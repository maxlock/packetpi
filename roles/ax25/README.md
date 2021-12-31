AX25
=========

This role configures the linux kernel ax25 applications.


Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

Whilst not dependant on any other roles, configuring systemd to start the provisioned daemons can be achieved by using the devoinc.systemd_service role as follows

```
- role: devoinc.systemd_service
  become: True
  systemd_service:

    kissattach:
      enabled: Yes
      exec_start: "/usr/sbin/kissattach /dev/tnc ax0"
      type: oneshot
      remain_after_exit: yes
      restart: "on-failure"
      requires: "socat.service"
      wanted_by: "multi-user.target"

    nrattach:
      enabled: Yes
      exec_start: "/usr/sbin/nrattach netrom"
      type: oneshot
      remain_after_exit: yes
      restart: "on-failure"
      requires: "kissattach.service"
      wanted_by: "multi-user.target"

    mheard:
      enabled: Yes
      exec_start: "/usr/sbin/mheardd"
      restart: "on-failure"
      requires: "kissattach.service"
      wanted_by: "multi-user.target"

    netrom:
      enabled: Yes
      exec_start: "/usr/sbin/netromd -i"
      type: oneshot
      remain_after_exit: yes
      restart: "on-failure"
      requires: "nrattach.service"
      wanted_by: "multi-user.target"

    ax25d:
      enabled: Yes
      exec_start: "/usr/sbin/ax25d -l"
      restart: "on-failure"
      requires: "kissattach.service"
      wanted_by: "multi-user.target"
```

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```
- hosts: servers
  roles:
  - role: ax25
    tags: [ax25]
    become: True
```

License
-------

GPL3

Author Information
------------------

Contact the author via github https://github.com/maxlock/packetpi
