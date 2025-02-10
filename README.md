# [`dimensionengineering` module](https://github.com/viam-modules/dimensionengineering)

This [dimensionengineering module](https://app.viam.com/module/viam/dimensionengineering) implements a dimensionengineering [sabertooth motor](https://www.active-robots.com/sabertooth-dual-5a-motor-driver.html?gad_source=1&gbraid=0AAAAAqSVQxV5lEXhnzCszz755bu4HbB_v&gclid=CjwKCAiAxKy5BhBbEiwAYiW--ycKzcP6fsVvoBrPQN0WM6p-T-tDBxYlkgXRtaYqTeXO21dLbPqsnhoCoikQAvD_BwE) using the [`rdk:component:motor` API](https://docs.viam.com/appendix/apis/components/motor/).

> [!NOTE]
> Before configuring your motor, you must [create a machine](https://docs.viam.com/cloud/machines/#add-a-new-machine).

Navigate to the [**CONFIGURE** tab](https://docs.viam.com/configure/) of your [machine](https://docs.viam.com/fleet/machines/) in the [Viam app](https://app.viam.com/).
[Add motor / dimensionengineering:sabertooth to your machine](https://docs.viam.com/configure/#components).

## Configure your sabertooth motor

To configure a sabertooth motor, you must configure the `serial_address`, `motor_channel`, and set the `serial_path` of the motor. To find your serial device path, first connect the serial device to your machine, then :

- On Linux, run `ls /dev/serial/by-path/` to show connected serial devices, or look for your device in the output of `sudo dmesg | grep tty`. Example: `"/dev/serial/by-path/usb-0:1.1:1.0"`.
- On macOS, run `ls /dev/tty* | grep -i usb` to show connected USB serial devices, `ls /dev/tty*` to browse all devices, or look for your device in the output of `sudo dmesg | grep tty`. Example: `"/dev/ttyS0"`.

```json
{
  "serial_path": "<serial-path-to-your-motor>",
  "serial_address": <int>,
  "motor_channel": <int>
}
```

### Attributes

The following attributes are available for `viam:dimensionengineering:sabertooth` motors:

| Attribute | Type | Required? | Description |
| --------- | ---- | --------- | ----------  |
| `serial_path` | string | **Required** | The full filesystem path to the serial device, starting with `/dev`. |
| `address` | int | **Required** | Serial address of the controller. |
| `motor_channel` | int | **Required** | Channel the motor is connected to on the controller. |

## Example configuration

### `viam:dimensionengineering:sabertooth`

```json
  {
    "serial_path": "/dev/serial/by-path/your_device",
    "serial_address": 127,
    "motor_channel": 1
  }
```

### Next Steps

- To test your motor, expand the **TEST** section of its configuration pane or go to the [**CONTROL** tab](https://docs.viam.com/fleet/control/).
- To write code against your motor, use one of the [available SDKs](https://docs.viam.com/sdks/).
- To view examples using a motor component, explore [these tutorials](https://docs.viam.com/tutorials/).
