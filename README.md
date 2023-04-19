This VS2017 solution provides Windows 10 plugins for the [MetaWear C# SDK](https://github.com/mbientlab/MetaWear-SDK-CSharp), 
providing Win10 specific Bluetooth and file I/O operations.  You can use this plugin for both UWP and .NET console appluations.  

The Win10 machine must be on the Fall Creator's Update or later.

# Install
Use the Package Manager console to install the [MetaWear.CSharp.Win10](https://www.nuget.org/packages/MetaWear.CSharp.Win10/) package 
in addition to the ``MetaWear.CSharp`` package.  

```bat
PM> Install-Package MetaWear.CSharp
PM> Install-Package MetaWear.CSharp.Win10
```

# Usage
First, retrieve the [BluetoothLEDevice](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.bluetoothledevice) object 
corresponding to the desired BLE device, then call ``GetMetaWearBoard`` to retrieve an ``IMetaWearBoard`` object for your device.

```csharp
public async IMetaWearBoard macAddrToIMetaWearBoard(ulong mac) {
    var device = await BluetoothLEDevice.FromBluetoothAddressAsync(mac);
    return MbientLab.MetaWear.Win10.Application.GetMetaWearBoard(device);
}
```

After retrieving your ``IMetaWearBoard`` object, you can use the SDK features, as outlined in the SDK [developers' guide](https://mbientlab.com/csdocs/1/metawearboard.html).

