# Notes

## Ideas / key features

### Drivers

- Drivers could be stacked to higher-level functionnality

### Devices

- GPIB module
- Mini, micro, ultra modules with varying form factors
- Mixed signal testbench module (analog + digital)
- Digital stimulation + measurement card (for numerical systems)
- Use existing systems for the lower end modules (arduino boards, etc...). Already existing cards can be programmed by the user directly (trail version kind of)
- DAC card that would work with a time domain signal (from numpy)
- Devices can be uniquely adressed. Either via IP, serial number or other mean of identification
- Each device needs to be (very) easily findable. Either via command line utility to find all of the devices, a WPS-like system or a dynamic system that lights up the device in a list and an LED on the device.
- Easy datalogger module with convenient signal inputs. It should be very quick to implement with Python code.
  - Maybe have a simpler module that has all the interfaces built-in and a bigger one that has extension slots so that the user can build his datalogger
  - 


### Inter-device communication

- Devices can be time synchronized to share a common timebase
- (Unsure) A device X could store a command for device Y provided they are on the same network and send it whenever an event arises.

### Communication

- Protocol version is agreed upon by both parties (device and host) at startup.
- Each device works with one and only one protocol. The host is responsible of using the right protocol for the device it is currently talking with
- Each device provides information about itself to the host at the beginning of communication such as protocol version, description, hardware version, etc... 
- EtherCat could be a nice improvement but not for now. The system must first be tested with simpler protocols.

### Drivers

- Standard functions (inherited) to allow for cross-instrument testbenches. (A testbench could require *a voltmeter* of any kind and any voltmeter with a well-made driver would be suitable)
- A device is instanciated using the driver's constructor ``dev = Driver("identifier")``

### Commands

- Commands should be standardized as much as possible
- 
### Code

- The use of interpreters is still debatable. It looks nice and allows for easy selection of some protocols but its a bit complicated and might not suit the task perfectly
  - Only for C++ / slaves ?

### Other

- Pytest could be used to create testbenches
- Some I2C communication have a "repeated start" that can be tricky to implement (read right after write)
- Web server for each interface ? (or only the bigger ones)
- Syndesi CLI that MUST be extremely easy to use to :
  - Find devices
  - Try out easy stuff
  - Configure the devices if necessary