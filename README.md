# PortaOne Billing Event monitor-in-the-middle

## Purpose

Intended to provide comfort view of event flow between PortOne billing and external handlers.

The component allows to create REST andpoint, accepting all the events from billing, 
and then passing it to real handler, storing the request and the answer in a round-robin buffer.

*Not properly tested, use at your own risk! This may create an extra  security risks as it has no any authentification*

## Installation
In the Composer storage. Just add proper require section:

    "require": {
        "pavlyuts/portabilling-eventmonitor": "*"
    }

## Dependencies
- rmccue/requests: ^1.7

## Use
You need to create HTTP endpoint to call with web-server and PHP configured. Then, create a code to handle events:

    <?php
    
    require '../vendor/autoload.php';

    $cc = new Portabillig\EventMonitor('https://myrealeventhandler.domain', '/var/poertaevents/', 2000);

Then, test to ensure it pass any call to your real event handling enpoint and point your billing system to the monitor URL.

Going to the same URL with plain no-args GET request will show event browser interface.

That's all!

## PortaOne documentation
Please, refer to PortaOne documentation and go to the training before use of this package.
- [External system provisioning framework (ESPF) docs](https://www.portaone.com/docs/PortaSwitch_Interfaces.pdf#page=45)
- [ESPF event list and passed values](https://www.portaone.com/docs/PortaSwitch_Interfaces.pdf#page=55)
- [Provisioning Application Reference Guide](https://www.portaone.com/docs/Provisioning_Application_Guide.pdf)
- [ESPF configuration handbook](https://www.portaone.com/handbook/index.htm#t=External_System_Provisioning%2FESPF_Configuration%2FESPF_Configuration.htm)
- [Administrator guide](https://www.portaone.com/docs/PortaBilling_Admin_Guide.pdf)

