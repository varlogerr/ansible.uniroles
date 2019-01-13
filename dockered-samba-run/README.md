Demo usage
```
# ...
  roles:
  - role: dockered-samba-run
    dockered_samba_host_port: 445 # optional. defaults to "445"
    dockered_samba_host_mount_dir: "{{ xfacts.user.homedir }}/Shares" # optional. defaults to "/"
    dockered_samba_container_name: samba # optional. defaults to "samba"
    dockered_samba_restart_policy: unless-stopped # optional. defaults to "unless-stopped"
    dockered_samba_groups: # optional. defaults to []
    - name: app1 # required
      gid: 1001 # optional
    - name: app2 # required
      gid: 1002 # optional
    dockered_samba_users: # optional. defaults to []
    - name: app1 # required
      uid: 1001 # optional
      group: app1 # optional
      groups: sam # optional
    - name: app2 # required
      uid: 1002 # optional
      group: app2 # optional
      groups: sam,app1 # optional
    dockered_samba_samba_users: # optional. defaults to []
    - name: app2 # required
      pass: qwerty # required
    dockered_samba_dirs: # optional. defaults to []
    - path: /data/Share1 # required
      owner: app1 # optional
      group: sam # optional
      mode: "0755" # optional
    - path: /data/Share2 # required
      owner: app2 # optional
      group: sam # optional
      mode: "0755" # optional
    dockered_samba_shares: # optional. defaults to []
    - |
      [pub]
        path = /data/Share1
        guest ok = yes
        force user = app1
        force group = sam
        create mask = 0664
        force create mode = 0664
        directory mask = 0775
        force directory mode = 0775
    - |
      [Homenet]
        path = /data/Share2
        valid users = @sam
        guest ok = no
        writable = yes
        browsable = yes
        guest ok = yes
        create mask = 0664
        force create mode = 0664
        directory mask = 0775
        force directory mode = 0775
# ...
```