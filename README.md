bt setup
===

program various bluetooth boards

### bluetooth hardware

#### HC-05

Set up as master, first connection to bt slave

```
AT+ORGL
AT+ROLE=1
AT+PSWD=0000 #optional
AT+INIT
AT+PAIR=[csv-device-id],[connect-ttl]
AT+BIND=[csv-device-id]
AT+LINK=[csv-device-id]
```

- after entering AT mode the led will flash slowly
- after calling init the led will flash rapidly
- after the pairing is successful the flashing will slow down
- after linking the led will flash 2x and pause, repeating

#### manual reconnect

After pairing once, all that is needed is

```
AT+LINK=[csv-device-id]
```

#### auto-connect

By default after binding the device it will connect automatically once restarted.

Using the connection mode command you can change auto-connect preference switch between requiring a bound device or just connecting to any available device.

### device ids

Device ids are generated from the mac address and 

- `00:19:01:49:32:33` becomes `0019,01,493233`
- `00:19:01:45:A1:30` becomes `0019,01,45A130`

### passwords

Some devices have a password requirement and some do not.

If pairing will not complete try password of `0000` or `1234` if no other password is known.

### other commands

- `AT+RMAAD` remove authenticated devices
- `AT+STATE` query the status of device
- `AT+CMODE` `0`, default, connect to only the bound device.  `1` will allow connection to any device.
- `AR+UART`  modify the serial connection properties (baud rate, parity, stop bits)

### reference

- https://arduino.stackexchange.com/a/22403
