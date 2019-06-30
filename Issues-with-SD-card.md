Since the newer versions of Android applications cannot arbitrarily write data to the SD card due to "increased security". The issue comes also from the fact that the app doesn't have control over what the `aria2` executable does. ([devgianlu/Aria2Android#19](https://github.com/devgianlu/Aria2Android/issues/19))

There's however a solution for rooted users which can use Magisk and an appropriate module (ExSDCard AccessEnable) to overcome this limitation. If you're having trouble, comment [here](https://github.com/devgianlu/Aria2App/issues/70).