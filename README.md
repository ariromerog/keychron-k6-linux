# Keychron K6 Linux Fixes

Recopilation of small fixes to really enjoy this cool little keyboard. Most of this is found from the Keyhcron Linux user group on facebook.

## How to enable Fn Keys

Out of the box, both the `fn1` and `fn2` modifiers only change to multimedia keys. Heres the fix:

- Set your keyboard to Windios/Android mode
- Set the options for the kernel module

        echo "s hid_apple fnmode=2" > /etc/modprobe.d/hid_apple.conf
        sudo update-initramfs -u
        reboot

## Fast bluetooth reconnect

Edit `/etc/bluetooth/main.conf`, uncomment the FastConnectable line and set it to true:
`FastConnectable = false`

## Missing special/latin characters

The keychron is missing the `~` and `՝` key, wich is pretty important for coding. In my case, I also need to be able to write some latin charcaters, such as ñ, á, etc. In order to get those working, what you need is enable and choose the "Compose Key", In Gnome is under the "keyboard and input" section in the "tweaks" application. 

You can see available key combinations here: https://help.ubuntu.com/community/GtkComposeTable

The complete list of available key combinations is in your  `/usr/share/X11/locale/en_US.UTF-8/Compose` file.

Then, you can edit your own `~/.XCompose` file and create your custom associations:

        # import the default Compose file for your locale
        include "%L"

        # Keychron K6 Fixes
        <Multi_key> <backslash> <backslash> : "`"
        <Multi_key> <minus> <n> : "ñ"
        <Multi_key> <minus> <N> : "Ñ"

You can find the key names that go between the `<>` characters using the `xev` tool.

