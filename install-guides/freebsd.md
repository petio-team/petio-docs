# FreeBSD

## MongoDB

placeholder

## Installing Petio

There is no package built for FreeBSD so the application will have to be built from source

#### Building from source

```
## Install dependencies
pkg install mongodb
pkg install npm
pkg install git (only if you want to use git to checkout the source)
npm install -g typescript

## Clone the repo and build the application
mkdir -p /usr/local/share/petio
cd /usr/local/share/petio
git clone -b dev https://github.com/petio-team/petio.git .
cd pkg/admin
npm install
npm run build
cd ../frontend
npm install
npm run build
cd ../api
npm install
npm run build
cd
mkdir -p /usr/local/petio
chown $petio_user:$petio_group /usr/local/petio
su -m $petio_user
setenv VIEWS_FOLDER /usr/local/share/petio/pkg/
setenv DATA_FOLDER /usr/local/petio

# Run the application
node /usr/local/share/petio/pkg/api/dist/main.js --host 0.0.0.0 --port 7777
```

#### Create a Petio service

rc.d script to run petio. It checks whether mongod is enabled and running, warns if not, and forcefully starts it if not running.

* Place this script in `/usr/local/etc/rc.d/petio`
* Give it execute permissions: `chmod +x /usr/local/etc/rc.d/petio`
* Configure it in `/etc/rc.conf`
  * sysrc petio\_enable="YES"
  * optionally set user: `sysrc petio_user="petio"`
  * optionally set group: `sysrc petio_group="petio"`
  * optionally set data directory: `sysrc petio_data_dir="/usr/local/petio"`

```
#!/bin/sh

# PROVIDE: petio
# REQUIRE: DAEMON mongod
# BEFORE: LOGIN
# KEYWORD: shutdown

. /etc/rc.subr

name=petio
rcvar=petio_enable

load_rc_config $name

: ${petio_enable:="NO"}
: ${petio_user:="petio"}
: ${petio_group:="petio"}
: ${petio_data_dir:="/usr/local/petio"}

export NODE_ENV=production
export APP_DIR=/usr/local/share/petio
export VIEWS_FOLDER=/usr/local/share/petio/pkg/
export DATA_FOLDER=${petio_data_dir}

pidfile="/var/run/${name}/${name}.pid"
start_precmd="petio_precmd"

procname="/usr/local/bin/node"
command="/usr/sbin/daemon"
command_args="-f -p ${pidfile} ${procname} --no-warnings /usr/local/share/petio/pkg/api/dist/main.js --host 0.0.0.0 --port 7777"

petio_precmd()
{
        if [ ! -d $(dirname ${pidfile}) ]; then
                install -d -o ${petio_user} -g ${petio_group} $(dirname ${pidfile})
        fi

        if [ ! -d ${petio_data_dir} ]; then
                install -d -o ${petio_user} -g ${petio_group} ${petio_data_dir}
        fi

        # make sure mongod is running
        if ! checkyesno mongod_enable && \
                ! /usr/local/etc/rc.d/mongod forcestatus 1>/dev/null 2>&1; then
                        echo "Make sure to enable and start mongod"
                        /usr/local/etc/rc.d/mongod forcestart || return 1
        fi
        return 0
}

run_rc_command "$1"
```

Once you've completed these steps, you can navigate to `http://<hostname>:7777` to start [configuring Petio](../configuration/first-time-setup.md).&#x20;
