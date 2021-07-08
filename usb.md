[TOC]



# watch lsusb
Bus 001 Device 024: ID 0acd:4650 ID Tech Composite device

/dev/ttyACM1


# Power and data roles
|     | Power   | Data    |        |
|-----|---------|---------|--------|
| DFP | Source  | Send    | Host   |
| UFP | Sink    | Receive | Device |
|     | DRD     | DRP     |        |


| Female              | Male       |  Result       |
|---------------------|------------|---------------|
| Adapter (Source + ?)| X          |               |
| PC (Source + Send)  | X                 |               |
| X                   | Android           |               |
