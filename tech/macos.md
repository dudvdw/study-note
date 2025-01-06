### quickKey

Mac 自带屏幕截图 Command + Shift + 5

Command + Tab 可让您快速浏览桌面上打开的每个应用程序窗口。

Command + H 快捷方式快速隐藏桌面上打开的任何窗口

Command + T 打开新的标签页

Command + 1/2/3/4 打开对应的的标签页

Command + ` 同一个 APP 多窗口之间切换 

Command + , 打开软件的偏好设置



### Diagnose system

``` shell
sudo sysdiagnose
```


### Shutdown Mac

Terminal: With a simple command we can easily set a timer. And not only to Shutdown but also Restart and even Sleep.
``` shell
sudo shutdown –[flag] +[time]
```
There are 3 flags for different tasks like:

-h is for Shutdown
-r is for Restart
-s is for Sleep

So let's schedule it to shutdown 60 mins later:
``` shell
sudo shutdown -h +60
```

or assumung the clock is 10:00 at the moment
``` shell
sudo shutdown -h 1100
```




### Generage md5 or sha256

``` bash
openssl md5 <filename>
```

``` bash
openssl sha256 <filename>
```

### Decode base64
``` bash
echo '<base64_string>' | base64 -d
openssl base64 -d <<< '<base64_string>'

base64 -d encoded_example.b64 > decoded_example.txt
```

### Encode base64
``` bash
echo '<string>' | base64 
openssl base64 -e <<< '<string>'

base64 example.txt > encoded_example.b64
```


- **To Encode `.txt` to Binary**:
  ```bash
  cat input.txt > output.bin
  ```

- **To Decode Binary to `.txt`**:
  ```bash
  cat output.bin > decoded.txt
  ```

- **To Encode `.txt` to Hexadecimal**:
  ```bash
  xxd -p input.txt > output.hex
  ```

- **To Decode Hexadecimal to `.txt`**:
  ```bash
  xxd -r -p output.hex > decoded.txt
  ```


### Shortcut key

1. Mac 自带屏幕截图 Command + Shift + 5

2. Command + Tab 可让您快速浏览桌面上打开的每个应用程序窗口。

3. Command + H 快捷方式快速隐藏桌面上打开的任何窗口

4. Command + T 打开新的标签页

5. Command + 1/2/3/4 打开对应的的标签页

6. Command + ` 同一个 APP 多窗口之间切换 

7. Command + , 打开软件的偏好设置


### Speaker maintenance

Double screws for the left speaker, only the lower bass unit is processed
3 screws for the right speaker, both high and low bass units are processed

### VMware Fusion 11
ZTVXW-VRAG9-D1WUR-XLQCT-VV5XX
G0ZQR-GRGYE-G1V8Z-AT9E0-6KNGV
RHZP8-V2QKE-Z1ZPQ-QFUET-Q7QZZ
7HYY8-Z8WWY-F1MAN-ECKNY-LUXYX
XKZYV-PK9CC-A1Y0X-K5HZL-Y65ZV
VJEM8-GUCPG-U1RJX-Z1Q9Z-QLGXT


