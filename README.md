Smartmontools
=============

Smartmontools fork with signed temperature on some drive.

According to [ticket #42] [1], subzero temperature will not be supported in stock Smartmontools.
It is true that raw value are *vendor secret* and unfortunatly the lack of standardization within
S.M.A.R.T. attributes leads to this: all vendors have their own implementation.

While I totally agree with the idea that *if we do not know how to threat the value, don't guess
an interpretation.* On the other hand, there are cases where we know how to interprete the data
and those cases should not suffer from the lack of vendor's documentations.

  [1]: http://sourceforge.net/apps/trac/smartmontools/ticket/42 "Subzero temperature"
