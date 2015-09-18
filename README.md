libvirt
=======

[![Ansible Role](https://img.shields.io/ansible/role/5010.svg)](https://galaxy.ansible.com/list#/roles/5010)

Installs and configures libvirt

Requirements
------------

This role requires Ansible 1.4 or higher.

Role Variables
--------------

| Name                                      | Default                                                                                                                                                    | Description                                                                                                             |
|-------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| libvirt_libvirtd_listen_tls               | 1                                                                                                                                                          | Listen for secure TLS connections                                                                                       |
| libvirt_libvirtd_listen_tcp               | 0                                                                                                                                                          | Listen for unencrypted TCP connections                                                                                  |
| libvirt_libvirtd_tls_port                 | 0                                                                                                                                                          | Port for accepting secure TLS connections                                                                               |
| libvirt_libvirtd_tcp_port                 | 0                                                                                                                                                          | Port for accepting insecure TCP connections                                                                             |
| libvirt_libvirtd_listen_addr              | 0.0.0.0                                                                                                                                                    | Address to bind to                                                                                                      |
| libvirt_libvirtd_mdns_adv                 | 0                                                                                                                                                          | Enable mDNS advertisement of the libvirt service                                                                        |
| libvirt_libvirtd_mdns_name                | "Virtualization Host {{ ansible_hostname }}"                                                                                                               | mDNS advertisement name                                                                                                 |
| libvirt_lxc_log_with_libvirtd             | 0                                                                                                                                                          | Accumulate log messages from all lxc controllers along with libvirtd's log outputs                                      |
| libvirt_lxc_security_driver               | selinux                                                                                                                                                    | LXC security driver                                                                                                     |
| libvirt_lxc_security_default_confined     | 0                                                                                                                                                          | Are LXC guests confined or unconfined by default                                                                        |
| libvirt_lxc_security_require_confined     | 0                                                                                                                                                          | Enable or disable the creation of unconfined LXC guests                                                                 |
| libvirt_qemu_vnc_listen                   | 127.0.0.1                                                                                                                                                  | Address VNC will listen on                                                                                              |
| libvirt_qemu_vnc_tls                      | 0                                                                                                                                                          | Enable or disable use of TLS encryption on the VNC server                                                               |
| libvirt_qemu_vnc_tls_x509_cert_dir        | /etc/pki/libvirt-vnc                                                                                                                                       | The directory where VNC x509 certificates are located                                                                   |
| libvirt_qemu_vnc_tls_x509_verify          | 0                                                                                                                                                          | Enabling this option will reject any client who does not have a certificate signed by the CA                            |
| libvirt_qemu_vnc_password_enabled         | False                                                                                                                                                      | Enable or disable VNC password                                                                                          |
| libvirt_qemu_vnc_password                 | password                                                                                                                                                   | VNC password                                                                                                            |
| libvirt_qemu_vnc_sasl                     | 0                                                                                                                                                          | Enable or disable use of SASL encryption on the VNC server                                                              |
| libvirt_qemu_vnc_sasl_dir                 | /etc/sasl2                                                                                                                                                 | Location of VNC SASL configuration file                                                                                 |
| libvirt_qemu_vnc_allow_host_audio         | 0                                                                                                                                                          | Enabling this option will make libvirtd honor the QEMU_AUDIO_DRV environment variable when using VNC                    |
| libvirt_qemu_spice_listen                 | 127.0.0.1                                                                                                                                                  | Address SPICE will listen on                                                                                            |
| libvirt_qemu_spice_tls                    | 0                                                                                                                                                          | Enable or disable use of TLS encryption on the SPICE server                                                             |
| libvirt_qemu_spice_tls_x509_cert_dir      | /etc/pki/libvirt-spice                                                                                                                                     | The directory where SPICE x509 certificates are located                                                                 |
| libvirt_qemu_spice_password_enabled       | False                                                                                                                                                      | Enable or disable SPICE password                                                                                        |
| libvirt_qemu_spice_password               | password                                                                                                                                                   | SPICE password                                                                                                          |
| libvirt_qemu_spice_sasl                   | 0                                                                                                                                                          | Enable or disable use of SASL encryption on the SPICE server                                                            |
| libvirt_qemu_spice_sasl_dir               | /etc/sasl2                                                                                                                                                 | Location of SPICE SASL configuration file                                                                               |
| libvirt_qemu_nographics_allow_host_audio  | 0                                                                                                                                                          | When enabling this setting, libvirt will passthrough the QEMU_AUDIO_DRV environment variable when using nographics      |
| libvirt_qemu_remote_display_port_min      | 5900                                                                                                                                                       | VNC/SPICE minimum port                                                                                                  |
| libvirt_qemu_remote_display_port_max      | 65535                                                                                                                                                      | VNC/SPICE maximum port                                                                                                  |
| libvirt_qemu_remote_websocket_port_min    | 5700                                                                                                                                                       | VNC WebSocket minimum port                                                                                              |
| libvirt_qemu_remote_websocket_port_max    | 65535                                                                                                                                                      | VNC WebSocket maximum port                                                                                              |
| libvirt_qemu_security_driver              | selinux                                                                                                                                                    | QEMU security driver                                                                                                    |
| libvirt_qemu_security_default_confined    | 1                                                                                                                                                          | Are QEMU guests confined or unconfined by default                                                                       |
| libvirt_qemu_security_require_confined    | 0                                                                                                                                                          | Enable or disable the creation of unconfined QEMU guests                                                                |
| libvirt_qemu_user                         | root                                                                                                                                                       | The user for QEMU processes run by the system instance                                                                  |
| libvirt_qemu_group                        | root                                                                                                                                                       | The group for QEMU processes run by the system instance                                                                 |
| libvirt_qemu_dynamic_ownership            | 1                                                                                                                                                          | Whether libvirt should dynamically change file ownership to match the configured user/group                             |
| libvirt_qemu_cgroup_controllers           | [ "cpu", "devices", "memory", "blkio", "cpuset", "cpuacct" ]                                                                                               | List of cgroup controllers to make use of with QEMU guests                                                              |
| libvirt_qemu_cgroup_device_acl            | [ "/dev/null", "/dev/full", "/dev/zero", "/dev/random", "/dev/urandom", "/dev/ptmx", "/dev/kvm", "/dev/kqemu", "/dev/rtc", "/dev/hpet", "/dev/vfio/vfio" ] | List of devices allowed / required by all virtual machines                                                              |
| libvirt_qemu_save_image_format            | raw                                                                                                                                                        | Format used when saving an image                                                                                        |
| libvirt_qemu_dump_image_format            | raw                                                                                                                                                        | Format used when dumping an image                                                                                       |
| libvirt_qemu_snapshot_image_format        | raw                                                                                                                                                        | Format used when snapshoting an image                                                                                   |
| libvirt_qemu_auto_dump_path               | /var/lib/libvirt/qemu/dump                                                                                                                                 | Location of dump files                                                                                                  |
| libvirt_qemu_auto_dump_bypass_cache       | 0                                                                                                                                                          | Enable or disable the use of filesystem cache when writing the dump file                                                |
| libvirt_qemu_auto_start_bypass_cache      | 0                                                                                                                                                          | Enable or disable the use of filesystem cache when restoring any managed state file                                     |
| libvirt_qemu_hugetlbfs_mount_enabled      | False                                                                                                                                                      | Enable or disable guests from requesting huge page backing                                                              |
| libvirt_qemu_hugetlbfs_mount              | /dev/hugepages                                                                                                                                             | Location of memory backing files                                                                                        |
| libvirt_qemu_bridge_helper_enabled        | False                                                                                                                                                      | Enable or disable bridge helper                                                                                         |
| libvirt_qemu_bridge_helper                | /usr/libexec/qemu-bridge-helper                                                                                                                            | Path to the setuid helper for creating tap devices                                                                      |
| libvirt_qemu_clear_emulator_capabilities  | 1                                                                                                                                                          | If enabled, libvirt will drop all privileged capabilities of the QEMU/KVM emulator                                      |
| libvirt_qemu_set_process_name             | 0                                                                                                                                                          | If enabled, libvirt will have QEMU set its process name to "qemu:VM_NAME", where VM_NAME is the name of the VM          |
| libvirt_qemu_max_processes                | -1                                                                                                                                                         | If set to a positive integer, libvirt will use it to set the maximum number of processes that can be run by qemu user   |
| libvirt_qemu_max_files                    | -1                                                                                                                                                         | If set to a positive integer, libvirt will use it to set the maximum number of files that can be opened by qemu user    |
| libvirt_qemu_mac_filter                   | 0                                                                                                                                                          | Enable or disable MAC address based filtering on bridge ports                                                           |
| libvirt_qemu_relaxed_acs_check            | 0                                                                                                                                                          | Allow or disallow PCI devices below non-ACS switch to be assigned to guests                                             |
| libvirt_qemu_allow_disk_format_probing    | 0                                                                                                                                                          | If enabled, libvirt will probe disk images to attempt to identify their format, when not otherwise specified in the XML |
| libvirt_qemu_lock_manager_sanlock_enabled | False                                                                                                                                                      | Enable or disable 'Sanlock' project based locking of the file content                                                   |
| libvirt_qemu_max_queued                   | 0                                                                                                                                                          | Set limit of maximum APIs queued on one domain                                                                          |
| libvirt_qemu_keepalive_interval           | -1                                                                                                                                                         | Keepalive interval                                                                                                      |
| libvirt_qemu_keepalive_count              | 0                                                                                                                                                          | Keepalive count                                                                                                         |
| libvirt_qemu_seccomp_sandbox              | -1                                                                                                                                                         | Use seccomp syscall whitelisting in QEMU                                                                                |
| libvirt_qemu_migration_address            | 0.0.0.0                                                                                                                                                    | Incoming migrations listening address                                                                                   |
| libvirt_qemu_migration_port_min           | 49152                                                                                                                                                      | Incoming migrations minimum port                                                                                        |
| libvirt_qemu_migration_port_max           | 49215                                                                                                                                                      | Incoming migrations maximum port                                                                                        |

Dependencies
------------

None

Example Playbook
----------------

Install libvirt
```
- hosts: all
  roles:
    - { role: kbrebanov.libvirt }
```

Install libvirt and set VNC to listen on all addresses
```
- hosts: all
  roles:
    - { role: kbrebanov.libvirt, libvirt_qemu_vnc_listen: 0.0.0.0 }
```

License
-------

BSD

Author Information
------------------

Kevin Brebanov
