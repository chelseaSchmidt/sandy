# sandy

## Hardware

- Raspberry Pi 4
- SKR Pico V1.0

## Setup

- Klipper: https://www.klipper3d.org/Installation.html

  - ssh into Raspberry Pi
  - `source env/bin/activate` to activate python virtual environment
  - Install Klipper on Raspberry Pi with KIAUH
  - Flash SKR Pico
    - These links were helpful for flashing:
      - https://github.com/bigtreetech/SKR-Pico/blob/master/Klipper/README.md
      - https://docs.vorondesign.com/build/software/skrPico_klipper.html
  - Configure Klipper; the `printer.cfg` config file needs to be added in the `~/printer_data/config/` directory, NOT `~/` like docs say
  - Run Klipper with `sudo service klipper start`
  - Check for errors with `cat ~/printer_data/logs/klippy.log`, resolve any, `sudo service klipper restart` after each config change

- OctoPrint: https://github.com/OctoPrint/OctoPrint

  - Install and start OctoPrint
  - Configure OctoPrint
    - https://www.klipper3d.org/OctoPrint.html
    - `<home_dir>/printer_data/comms/klippy.serial` needs to be added in OctoPrint "Additional serial ports" setting and then selected as the port. Don't use `~` in place of home dir
  - Select `<home_dir>/printer_data/comms/klippy.serial` as the port
  - Select 250000 as the baud rate
  - Hit "Connect"

## Startup

- Command line
  - `ssh <username>@raspberrypi.local` | ssh into Raspberry Pi
  - `source env/bin/activate` | Activate python virtual environment
  - `sudo service klipper status` | Verify Klipper service is running
  - `octoprint serve` | Start OctoPrint server
- Navigate to OctoPrint client at `http://<raspberry_pi_local_ip>:5000` and login
  - Example: `http://10.0.0.26:5000`

## Reference

- `nano ~/printer_data/config/printer.cfg` | Edit Klipper -> stepper motor config
- `cat ~/printer_data/logs/klippy.log` | View Klipper service logs (status command doesn't seem to report errors reliably)
- `sudo service klipper stop`
- `sudo service klipper restart`
- `sudo service klipper status`
