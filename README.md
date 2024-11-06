# [`dimensionengineering` module](https://github.com/viam-modules/dimensionengineering)

This [dimensionengineering module](https://app.viam.com/module/viam/dimensionengineering) implements a dimensionengineering [sabertooth motor](https://www.active-robots.com/sabertooth-dual-5a-motor-driver.html?gad_source=1&gbraid=0AAAAAqSVQxV5lEXhnzCszz755bu4HbB_v&gclid=CjwKCAiAxKy5BhBbEiwAYiW--ycKzcP6fsVvoBrPQN0WM6p-T-tDBxYlkgXRtaYqTeXO21dLbPqsnhoCoikQAvD_BwE) using the [`rdk:component:motor` API](https://docs.viam.com/appendix/apis/components/motor/).

## Configure your sabertooth motor

> [!NOTE]
> Before configuring your motor, you must [create a machine](https://docs.viam.com/cloud/machines/#add-a-new-machine).

Navigate to the [**CONFIGURE** tab](https://docs.viam.com/configure/) of your [machine](https://docs.viam.com/fleet/machines/) in the [Viam app](https://app.viam.com/).
[Add motor / dimensionengineering:sabertooth to your machine](https://docs.viam.com/configure/#components).

On the new component panel, copy and paste the following attribute template into your motor's attributes field:

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
| `serial_path` | string | **Required** | The full filesystem path to the serial device, starting with <file>/dev/</file>. To find your serial device path, first connect the serial device to your machine, then:<ul><li>On Linux, run <code>ls /dev/serial/by-path/\*</code> to show connected serial devices, or look for your device in the output of <code>sudo dmesg \| grep tty</code>. Example: <code>"/dev/serial/by-path/usb-0:1.1:1.0"</code>.</li><li>On macOS, run <code>ls /dev/tty\* \| grep -i usb</code> to show connected USB serial devices, <code>ls /dev/tty\*</code> to browse all devices, or look for your device in the output of <code>sudo dmesg \| grep tty</code>. Example: <code>"/dev/ttyS0"</code>.</li></ul> |
| `address` | int | **Required** | Serial address of the controller. |
| `motor_channel` | int | **Required** | Channel the motor is connected to on the controller. |


## Example configuration

### `viam:dimensionengineering:sabertooth`
```json
  {
      "name": "<your-dimensionengineering-sabertooth-motor-name>",
      "model": "viam:dimensionengineering:sabertooth",
      "type": "motor",
      "namespace": "rdk",
      "attributes": {
        "serial_path": "/dev/serial/by-path/your_device",
        "serial_address": 127,
        "motor_channel": 1
      },
      "depends_on": []
  }
```

### Next Steps
- To test your motor, expand the **TEST** section of its configuration pane or go to the [**CONTROL** tab](https://docs.viam.com/fleet/control/).
- To write code against your motor, use one of the [available SDKs](https://docs.viam.com/sdks/).
- To view examples using a motor component, explore [these tutorials](https://docs.viam.com/tutorials/).
