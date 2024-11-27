# Cisco Packet Tracer Commands Summary:

## Lab2: Basic Router Configuration:

**Command line modes:**
- User EXEC mode: is the default when u open
- Priviliged EXEC mode: `enable`
- Global configuration mode: `configure terminal`

    1. Interface mode: Used to configure the device’s interface/port
    2. Line mode: Used to configure the device’s access lines
    3. Router mode: Used to configure the routing information

**Configuring router's interfaces can be done in different ways:**
- GUI of the router
- CLI directly on the router
- Through an end-device using Console Cable connected to the router

    ```c
    // Console port: is the port used to directly access the router and configure (manage) it, so we have to authenticate the access of this port.
    Router(config)# line console 0
    Router(config-line)# password yourpassword
    Router(config-line)# login
    ```
- Through an end-device using remote access control
    ```c
    // Virtual Teletype (VTY) port: is the port used to remotely access the router and configure (manage) it, so we have to authenticate the access of this port.
    Router(config)# line vty 0 4
    Router(config-line)# password yourpassword
    Router(config-line)# login
    ```
    ```c
    // to access it, open the command prompt on any end-device and do the following command
    telnel ip-address-of-router
    ```

**Basic commands line:**
1. Configuring a router Host Name:
    ```
    Router(config)# hostname NES413
    ```

2. Login banners: A login banner is a message that is displayed at login.
    ```
    Router(config)# banner motd #your statment#
    ```

3. Prevent the translation of incorrectly entered commands as though they
were hostnames.
    ```
    Router(config)# no ip domain-lookup
    ```

4. Configuring router passwords: Passwords restrict access to routers. The following two commands can be used to establish authentication
before accessing **privileged EXEC mode**:

    - Enable Password: set a password to the privileged mode. The password is displayed as clear text in the router’s configuration file.
        ```
        Router(config)# enable password yourpassword
        ```

    - Enable Secret: encrypted secret password to privileged mode. The password is displayed as encrypted text in the router’s configuration file.
        ```
        Router(config)# enable secret yourpassword
        ```

5. The service password-encryption global configuration command to prevent passwords from displaying as plain text in the configuration file.
    ```
    Router(config)# service password-encryption
    ````

6. Configuring Ethernet interfaces:
    ```
    Router(config)#interface type-and-number
    Router(config-if)# description descriptive-text
    Router(config-if)#ip address ipaddress subnetmask
    Router(config-if)#no shutdown
    ```

7. To verify the IPv4 addresses for all interfaces:
    ```
    Router# show ip interface brief
    ```

8. To show the routing table of the router use the following command in the privileged EXEC mode:
    ```
    Router# show ip route
    ```

**A Cisco network device contains two configuration files:**
1) The running configuration file (RAM).
2) The startup configuration file (NVRAM).

```c
// To save the current configuration of the router to the startup configuration file
Router# copy running-config startup-config

// To show the overall configurations that you make
Router# show running-config

// If you need to restore the previous configurations
Router# reload

// if the undesired changes were saved to the startup-config file, it may be necessary to clear all the configurations 
Router# erase stratup-config
Router# reload
```

## Lab3: Static Routing:

1) To configure static routes with a **next-hop IP address** or **exit interface** specified:
    ```
    Router(config)# ip route network-address subnet-mask next-hop-address
    ```
    ```
    Router(config)# ip route network-address subnet-mask exit-interface
    ```

2) To configure a default static route with a **next-hop IP address** or **exit interface** specified:
    ```
    Router(config)# ip route 0.0.0.0 0.0.0.0 next-hop-address
    ```
    ```
    Router(config)# ip route 0.0.0.0 0.0.0.0 exit-interface
    ```