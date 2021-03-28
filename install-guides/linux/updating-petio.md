---
description: >-
  We believe these instructions should be pretty OS agnostic, but if you notice
  any mistakes that need to be corrected, please reach out on Discord!
---

# Updating Petio

* Stop the Petio service.

  ```bash
  sudo systemctl stop petio
  ```

* Download the latest version of Petio.

  ```bash
  sudo wget https://petio.tv/releases/latest -O petio-latest.zip
  ```

* Extract to petio folder.

  ```bash
  sudo unzip petio-latest.zip -d /opt/Petio
  ```

* Start Petio service.

  ```bash
  sudo systemctl start petio
  ```

* Remove the file you downloaded so you are ready for a new update later on.

  ```bash
  sudo rm petio-latest.zip
  ```

