# `webcam-srv`

*webcam-srv* helps to configure [MediaMTX](https://mediamtx.org/) to serve video streams from webcams.

## Requirements

* [MediaMTX](https://mediamtx.org/) server,
* *ffmpeg* utility.
* [go-task](https://github.com/go-task/task)

## Installation

* Clone repository:

  ```sh
  $ git clone https://github.com/RoEdAl/webcam-srv.git
  ```

* Install *webcam-srv*:

  ```sh
  $ cd webcam-srv
  $ sudo task install
  $ sudo reboot
  ```

* Obtain *VID* and *PID* of your webcam and add appropiate *udev* rule in `/usr/local/lib/udev/rules.d/80-v4l-ids.rules` file:

  ```udev
  ATTRS{idProduct}=="PPPP", ATTRS{idVendor}=="VVVV", SYMLINK+="v4l/newdev", TAG+="systemd", ENV{SYSTEMD_ALIAS}="/dev/v4l/newdev"
  ```

  This rule creates symlink of V4L2 device into `/dev/vl4` folder.

  ```sh
  $ ls -l /dev/v4l
  drwxr-xr-x 2 root root  80 Nov 24 10:41 by-id
  drwxr-xr-x 2 root root 120 Nov 24 10:41 by-path
  lrwxrwxrwx 1 root root   9 Nov 24 10:41 newdev -> ../video0
  ```

* Edit configuration file of *webcam-srv*:
  
    ````
    sudo nano /usr/local/etc/webcam-srv.yml
    ````

* Run *MediaMTX* server.

    ```sh
    $ sudo systemctl start mediamtx
    ```

## Configuration file

**TODO**
