# ASUSWRT-DSM
ASUSWRT DSM for QRadar

# ASUSWRT Firmware Changes (ASUS Merlin Firmware)
This is a work in progress DSM that is being created for IBM QRadar CE. I'm slowly building the regex logic to parse the various functions of the ASUSWRT firmware to add as a log source. This is my first attempt at a custom DSM and it will be slowly improved overtime as I learn more. 

The router will need the following settings changed when creating the new log source:

    Firewall:
      Logged packets Type: Both
    System Log:
      Remote Log Server: IP of QRCE
      Default message log level: Emergency
      Log only messages more urgent than: alert
    Administration:
      System:
        Enable SSH: LAN only
        Enable JFFS custom scripts and configs: Yes

  Once the settings have been changed in ASUSWRT then the config file (dnsmasq.conf.add) will need to be created in the directory: /jffs/configs/.

  This will forward DNS queries to QRCE under the ASUSWRT DSM.

# QRCE Changes
A new DSM will need to be created called (ASUSWRT) using the DSM editor under the admin settings window. Once the new DSM is created the overrides contained in the folder (DSM Overrides) will need to be configured. This should be as simple as coping and pasting the saved regex and capture fields.

Additionally, under the Event Mappings tab when creating the custom DSM custom event mappings will need to be created for each event type. The custom mappings that I have created so far are under the file (Event Mappings). They have the field names with the required text for the events to mapped to the custom QIDs.


# TODO/WIP
Finish DNS Parsing
VPN Support (OPENVPN)
ASUSWRT Custom logs?
