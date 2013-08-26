Smartmontools
=============

Smartmontools fork with signed temperature on some drive.

According to [ticket #42] [1], subzero temperature will not be supported in stock Smartmontools.
It is true that raw value are *vendor secret* and unfortunatly the lack of standardization within
S.M.A.R.T. attributes leads to this: all vendors have their own implementation.

While I totally agree with the idea that *if we do not know how to threat the value, don't guess
an interpretation.* On the other hand, there are cases where we know how to interprete the data
and those cases should not suffer from the lack of vendor's documentations.

As part of an embedded project that is required to run in a wide temperature range, smartmontools 
was modified to provide correct information on temperature.

*Daemon smartd has not been tested. You've been warned!*

*update-smart-drivedb.in is broken. Do not use it with this release.*

Ouput example (some lines were removed)

```
smartctl 6.2 (build date Aug 23 2013) [x86_64-linux-3.10.9-200.fc19.x86_64] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Kingston SSDNow with signed temperature. SandForce Driven SSDs
Device Model:     KINGSTON SE100S3200G
Serial Number:    50026B723107D243
LU WWN Device Id: 5 0026b7 23107d243
Firmware Version: 515ABBF0
User Capacity:    200 049 647 616 bytes [200 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS, ACS-2 T13/2015-D revision 3
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Fri Aug 23 13:12:02 2013 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

...

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x0033   120   120   050    Pre-fail  Always       -       0/0
...
194 Temperature_Celsius     0x0022   248   044   000    Old_age   Always       -       -8 (Min/Max -16/44)
...
242 Lifetime_Reads_GiB      0x0032   000   000   000    Old_age   Always       -       5
```

  [1]: http://sourceforge.net/apps/trac/smartmontools/ticket/42 "Subzero temperature"
