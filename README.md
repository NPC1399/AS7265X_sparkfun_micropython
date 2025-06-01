# AS7265X MicroPython Driver

This is a MicroPython driver for the AS7265X 18-channel spectral sensor.

## Usage Example

```python
from machine import I2C
from AS7265X import AS7265X

# Initialize I2C (example for ESP32)
i2c = I2C(0, scl=Pin(22), sda=Pin(21))

# Initialize the sensor
sensor = AS7265X(i2c)

# Take a measurement
sensor.take_measurements()

# Get calibrated values
a_cal = sensor.get_calibrated_A()
b_cal = sensor.get_calibrated_B()
# ... and so on for all 18 channels

print(f"Calibrated A: {a_cal}")
print(f"Calibrated B: {b_cal}")
```

## API

The driver provides the following methods:

* `__init__(self, i2c, **kwargs)`: Initializes the sensor.
* `virtual_read_register(self, virtual_address)`: Reads a virtual register.
* `virtual_write_register(self, virtual_address, value)`: Writes to a virtual register.
* `get_devicetype(self)`: Gets the device type.
* `get_hardware_version(self)`: Gets the hardware version.
* `get_major_firmware_version(self)`: Gets the major firmware version.
* `get_patch_firmware_version(self)`: Gets the patch firmware version.
* `get_build_firmware_version(self)`: Gets the build firmware version.
* `take_measurements(self)`: Takes measurements for all channels.
* `take_measurements_with_bulb(self)`: Turns on all bulbs, takes measurements, then turns off bulbs.
* `get_G(self)`, `get_H(self)`, ..., `get_F(self)`: Get raw values for each channel.
* `get_calibrated_A(self)`, `get_calibrated_B(self)`, ..., `get_calibrated_F(self)`: Get calibrated values for each channel.
* `set_measurement_mode(self, mode)`: Sets the measurement mode.
* `set_gain(self, gain)`: Sets the gain.
* `set_integration_cycles(self, cyclevalue)`: Sets the integration cycle amount.
* `enable_interrupt(self)`: Enables the interrupt.
* `disable_interrupt(self)`: Disables the interrupt.
* `data_available(self)`: Checks if data is available.
* `clear_data_available(self)`: Clears the data available flag.
* `enable_bulb(self, device)`: Enables the bulb on a given device.
* `disable_bulb(self, device)`: Disables the bulb on a given device.
* `set_bulb_current(self, current, device)`: Sets the current limit of the bulb/LED.
* `select_device(self, device)`: Selects the device (master or slave).
* `enable_indicator(self)`: Enables the onboard indicator LED.
* `disable_indicator(self)`: Disables the onboard indicator LED.
* `set_indicator_current(self, current)`: Sets the current limit of the onboard LED.
* `get_temperature(self, devicenumber)`: Gets the temperature of a given device.
* `get_temperature_average(self)`: Gets the average temperature of all sensors.
* `soft_reset(self)`: Performs a soft reset.
* `get_value(self, RorC)`: Gets all raw or calibrated values based on the argument.

Please refer to the source code and the AS7265X datasheet for more details on each method and the sensor's functionality.
