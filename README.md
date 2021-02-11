# Badgerloop Testing Framework
The home for all things related to the Badgerloop Testing Framework

## Table of Contents
- [Badgerloop Testing Framework](#badgerloop-testing-framework)
  - [Table of Contents](#table-of-contents)
  - [Hardware Emulation](#hardware-emulation)
    - [Hardware Emulation Board](#hardware-emulation-board)
      - [List of devices](#list-of-devices)
    - [Raspberry Pi Controller](#raspberry-pi-controller)
  - [Test Configurations](#test-configurations)
    - [Writing Tests](#writing-tests)
    - [Running Tests](#running-tests)
      - [Raspberry Pi Runner](#raspberry-pi-runner)
      - [Logging Server](#logging-server)
  - [Definitions](#definitions)


## Hardware Emulation
Hardware emulation is made up of two parts. A hardware emulation board being developed by the [Low Voltage Team](https://github.com/badgerloop-software/hardware) and a [Raspberry Pi](https://raspberrypi.org) controller board. The raspberry pi would recieve tests from [test configuration files](#test-configurations) and setup various devices to correspond to tests running on our boards.
### Hardware Emulation Board
The hardware emulation board is essentially a Raspberry Pi hat with access to an array of devices to test our state machine and drivers.

#### List of devices
- 2x [REF194GSZ](https://www.digikey.com/en/products/detail/analog-devices-inc/REF194GSZ-REEL7/995868) Analog to Digital Converter
- 2x [MAX525BCAP](https://www.digikey.com/en/products/detail/maxim-integrated/MAX525BCAP/948076) Digital to Analog Converter
- 1x I<sup>2</sup>C [MCP23017](https://www.microchip.com/wwwproducts/en/MCP23017)
- 1x [LT3092](https://www.analog.com/media/en/technical-documentation/data-sheets/lt3092.pdf) Current Source
### Raspberry Pi Controller
*Note that the Raspberry Pi Controller and Runner are the same board*
The Raspberry Pi will configue these pins as inputs and outputs and report their status to the [runner](#raspberry-pi-runner)
## Test Configurations
Tests will be setup by configuration file. After a developer has configured a test they will upload it to the [Raspberry Pi runner](#raspberry-pi-runner) where it will setup the [hardware emulation board](#hardware-emulation-board) and configure the MCU to run the tests.
### Writing Tests
TBD
### Running Tests
Running tests will consist of 3 parts. A hardware configuration, a corresponding GTest, and a log reporting server.


#### Raspberry Pi Runner
*Note that the Raspberry Pi Runner and Controller are the same board*
The Raspberry Pi will configure it's I/O pins in accordance with the [configuration file](#writing-tests) using it's own framework (probably PyTest). Once it's state machine is setup it will then configure the UUT to run it's corresponding test. Logs and results of both tests will be combined and uploaded to a logging server. 

#### Logging Server
TBD

## Definitions
UUT - Unit Under Test - The unit being tested