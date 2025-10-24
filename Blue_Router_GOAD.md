### Notes for Blue_Router Setup to be used with Super-GOAD in Proxmox

## Interfaces
The Blue_Router is a pfsense that sits between CyberRange(GraySpace) and the Blue (SuperGOAD) space.

1. Download PFSense ISO
    - https://www.pfsense.org/download/
2. Setup the PFSense Proxmox VM
    - CPU: 2
    - RAM: 4096
    - Disk: 40GB
    - Network: This setup will depend on the environment... for my environment I have things broken into vnets. So I added 3 vnets with vlan tags as follows.
        - Dom1: bridge=\<VNETID>,firewall=1,tag=\<VLANID>
        - Dom2: bridge=\<VNETID>,firewall=1,tag=\<VLANID>
        - Dom3: bridge=\<VNETID>,firewall=1,tag=\<VLANID>

        Note: SuperGOAD has 3 domains so you will need to create three IP spaces for the 3 domains on your pfsense. I will mark these as Dom1, Dom2, and Dom3. AFTER adding these 3 vnets you will see that you have 4 NETWORK DEVICES on the pfsense. The 3 you created after and the 1 that was created when the vm was created.

        IMPORTANT! YOU NEED TO KEEP THE 1 DEFAULT NETWORK DEVICE TO GET ACCESS TO THE INTERNET IN THE SETUP. 
        
