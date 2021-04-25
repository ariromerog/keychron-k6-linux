# Keychron K6 Linux Fixes

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

 
  
  
 
