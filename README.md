Ducati Scrambler CAN Bus
------------------------

What we know:
* Throttle position
* Clutch switch
* Neutral indicator
* RPM
* Kill switch
* Odometer

We might know:
* Battery Voltage

We don't know:
* Speed
* Temperature
* ABS status
* Sidestand switch
* Gear (might not be possible)

Unlikey:
* Trip meters (could be based off the odometer)
* Indicators
* Brakes

## Messages

The CAN bus messages are in the format `ZZZ AA BB CC DD EE FF GG HH` where `ZZZ` is the message ID.

### 081

Byte | Description
:---:|-------------
AA   | Throttle position between 00 - C8 in increments of 2. Also clutch switch where +1 is the switch being activated.
BB   |
CC   |
DD   |
EE   | Unknown, default C8
FF   |
GG   |
HH   |

### 100

Byte | Description
:---:|-------------
AA   | Neutral where 00 is neutral and E0 is not neutral
BB   | Changed with RPM, though unknown
CC   | Unknown, default 0A
DD   | RPM
EE   | RPM
FF   | Unknown, default 04
GG   |
HH   | Kill switch where 00 is off (killed) and 01 is on (run)

### 022

Byte | Description
:---:|-------------
AA   |
BB   |
CC   |
DD   |
EE   |
FF   | Toggles between 0 and 1 rapidly
GG   | Fast incrementing number
HH   | Fast incrementing number

### 201

Byte | Description
:---:|-------------
AA   |
BB   |
CC   |
DD   |
EE   |
FF   |
GG   |
HH   | Possibly battery voltage (7D = 125 = 12.5)

### 240

Byte | Description
:---:|-------------
AA   | Slow incrementing number
BB   |
CC   |
DD   |
EE   |
FF   |
GG   |
HH   |

### 300

Byte | Description
:---:|-------------
AA   |
BB   |
CC   | Odometer (unconfirmed)
DD   | Odometer (unconfirmed)
EE   | Odometer
FF   | Odometer
GG   | Seemingly random changing number
HH   |
