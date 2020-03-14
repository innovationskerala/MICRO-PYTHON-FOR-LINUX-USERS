# Micro Python tutorial For Linux users

MicroPython is a tiny open source Python interpretor that runs on small embedded development boards


## Let's Get Started

1. Open terminal & Install ESP tool by using the command:
    `sudo pip install esptool`

2. Erase the already flashed firmware in the esp8266 board:
    `sudo esptool.py --port /dev/ttyUSB0 erase_flash`
    Make sure to put correct port.

3. Download the latest micropython firmware from the [website](https://micropython.org/downloadhttps://micropython.org/download)

4. Go to the folder where the download bin file of the firmware located, open terminal there then type

    `esptool.py --port /dev/ttyUSB0 --baud 460800 write_flash --flash_size=detect 0 esp8266-20170108-v1.8.7.bin`

    * For some boards with a particular FlashROM configuration.
    (e.g. some variants of a NodeMCU board)
    You may need to use the following command to deploy the firmware (note the `-fm dio` option):

        `esptool.py --port /dev/ttyUSB0 --baud 460800 write_flash --flash_size=detect -fm dio 0 esp8266-20170108-v1.8.7.bin`

    * You need to change `esp8266-20170108-v1.8.7.bin` as the name of the downloaded file name

5. Connect to esp8266 serially  using
    `sudo picocom /dev/ttyUSB0 -b115200`
    If you face any error FATAL: cannot open /dev/ttyUSB0: Permission denied like this plz type :
    `sudo chmod 666 /dev/ttyUSB0`


6. If  you get connected to the board then type

    ```python
    import esp
    esp.check_fw()
    ```

    If it return True then the firmware is ok

7. Now onwards you can run your python codes in
your microcontroller just hello world in python.

    ```python
    print("Hello World")
    ```

    Output:
    `Hello World`
