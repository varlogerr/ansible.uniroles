Run nexus3 in docker container.

Image documentation: https://hub.docker.com/r/sonatype/nexus3

Usage
```
# ...
  roles:
  - role: dockered/nexus-run
    dockered_nexus_container_name: mynexus # optional. defaults to "{{xfacts.system.ansible_managed_prefix}}-nexus"
    dockered_nexus_version: 3.14.0 # optional. defaults to 3.15.2
    dockered_nexus_restart_policy: unless-stopped # optional. defaults to "always"
    dockered_nexus_network_mode: bridge # optional. defaults to "host"
    dockered_nexus_host_data_dir: /my-nexus/data/dir # optional
    dockered_nexus_ports: # optional. defaults to []. can be used with bridge network mode
    - "8081:8081"
    - "8082:8082"
# ...
```
