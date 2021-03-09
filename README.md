# sensors-asus-ec
This script provides sensor data for the ASUS Dark Hero through the ec_sys debug interface. This is intended as a workaround until proper kernel support is implemented. Enhancements/fixes are welcome.

## Requirements
- Python 3 with the `daemonize` module.
- The kernel module `ec_sys` must be loaded. 
- Root privileges to read the data. Script can be run as a daemon which then listens on a local port. From there a regular user can run and data will be read from the daemon.

## Usage
| Argument                  | Description                                                                              |
| -------------------       | -----------------------------------------------------------------------                  |
| `-h`                      | Help                                                                                     |
| `-d`                      | Run as daemon                                                                            |
| `-f`                      | If running daemon, run in foregroud                                                      |
| `-p`                      | Path to PID file, defaults to '/var/run/sensors-asus-ec.pid'                             |
| `-P`                      | Port to listen or connect. defauls to 2787                                               |


## Examples
```
$ sudo ./sensors-asus-ec.py -d
$ ./sensors-asus-ec.py
MOTHERBOARD_TEMP    : 35 °C
CHIPSET_TEMP        : 54 °C
CPU_TEMP            : 34 °C
T_SENSOR            : 27 °C
WATER_FLOW          : 162 RPM

$ nc 127.0.0.1 2787
{"MOTHERBOARD_TEMP": "35 \u00b0C", "CHIPSET_TEMP": "54 \u00b0C", "CPU_TEMP": "34 \u00b0C", "T_SENSOR": "27 \u00b0C", "WATER_FLOW": "164 RPM"}
```
