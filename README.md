# VM to use as a jumphost/portal into Lab environment

This repo will contain the build instructions for a VM that will act as a jumphost to the rest of the RHHI lab environment. For a quick deployment the VM will be exported as an OVA and stored on a separate storage server (in this case, a Synology DS918+) to allow for quick imports into newly deployed labs.

The intent is to have a locked down VM for external users to be able to access, so long as their user exists within the IdM database. Access will be through either:
- SSH key access (stored in the IdM database)
- Browser-based noVNC session to have access to the desktop

We're going to start with Fedora 30 WS as the initial distro used, but will eventually move this to a RHEL deployment with a security profile applied (USGCB would be my personal preference).


## General Steps

- Import Fedora WS ISO into RHHI
- New VM: Small, ovirtmgmt network, name = portal, check HA box, create disk 50GB
  - /boot           1024  MiB
  - /var            6144  MiB
  - /var/log        6144  MiB
  - /var/log/audit  2048  MiB
  - /tmp            2048  MiB
  - /root           12288 MiB
  - /home           20480 MiB
  - swap            1024  MiB
- Run Once: boot option attach ISO, change boot order, check box rollback config
-
