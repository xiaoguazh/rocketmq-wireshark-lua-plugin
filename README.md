# 1 Brief

This is improved version base on [arthur-zhang](https://github.com/arthur-zhang)/**[rocketmq-wireshark-lua-plugin](https://github.com/arthur-zhang/rocketmq-wireshark-lua-plugin)**

Major improvements:

- Support TCP reassembly

- Support parsing when pull message body has multi-records

- Replace json.lua with rxi's json.lua

- Add "msg_encoder" variable for handling Chinese chars, default setting is ENC_UTF_8

- Add Tree Fields : total_length, header_length, header, body to ease the inspection

- Add screenshots

- Fix the parsing errors  renaming code: var and methods

# 2 Usage

```
1)Exact and copy "rocketmq-plugin" folder to wireshark installtion folder

    e.g.,
        C:\Program Files\Wireshark\rocketmq-plugin

2)Open any text editor app and edit init.lua
    Note: for windows, the text editor requires to be "Run as Adminitrator"

    The init.lua is located in wireshark installtion folder, e.g.,
        C:\Program Files\Wireshark\init.lua

    Add below line to the end of init.lua, and save

        dofile(DATA_DIR.."rocketmq-plugin" .. package.config:sub(1,1) .. "rocketmq.lua")

3)Open wireshark and load a rocket_mq packet
```

# 3 Customization

## 3.1 Customize MQ_PORTS

In case you changed the default Rocket MQ ports to something different, please update **MQ_PORTS **in rocketmq.lua.

```
local MQ_PORTS = { 9876, 10911, 20111 }
```

## 3.2 Customize Encoding

In case your need other encoding than UTF-8, please update **msg_encoder** in rocketmq.lua.

See init.lua for more supported encoding list, e.g.,ENC_GB18030 = 80 for Chinese.

```
local msg_encoder = ENC_UTF_8
```

# 4 Version History

| Version | Date        | Author   | Note           |
|:-------:| ----------- | -------- | -------------- |
| 0.1     | 2021-Aug-20 | xiaoguaz | First delivery |
