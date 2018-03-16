`mced` is a very small daemon which monitors /dev/mcelog for machine check events, and then reports them to other applications.

Machine checks can indicate failing hardware, system overheats, bad DIMMs or other problems. Some MCEs are 'fatal' and can't generally be survived. Many, however are not fatal, and mced can help you detect and report them more accurately.


Notes:

* Kernels prior to 2.6.22 do not support poll() on /dev/mcelog.  In that
  case, the polling intervals of the kernel and of mced will limit the
  rate at which MCEs can be logged.  To get better resolution, decrease
  these intervals.

* Not every system tracks a "current boot number".  For those that do, the
  -b (--bootnum) option can be used.  Tracking a boot number can help to
  identify crashes that might be related to MCEs.

* mced does not try to decode MCEs.  If you want that, you should try
  Andi Kleen's mcelog tool (https://www.mcelog.org/) or the
  simple generic MCE decoder included in this package (mce_decode).

* The latest code for this project can be found at the github site:
  	https://github.com/thockin/mcedaemon
  The mced-devel mailing list is where development discussions and patches
  get sent:
  	http://groups.google.com/group/mced-devel

* mced supports sending events over D-Bus.  See the mced man page for
  details or the mce_listen code for specifics on how to receive and
  decode these events.  Building with D-Bus support requires development
  packages for glib, gobject, gtype, pcre, dbus and dbus-glib.

* If there is something you need out of mced, or if something is not
  working right, please contact me - thockin@hockin.org.
