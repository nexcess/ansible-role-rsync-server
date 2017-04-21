Rsync Server
============

Setup rsync as a server.


Role Variables
--------------

Defaults: `defaults/main.yml`

- `rsync_server_timeout`: Timeout for connections, default `300` seconds
- `rsync_server_max_connections`: Maximum number of connections, default `10`
- `rsync_server_shares`: A list of dictionaries of shares with fields:
  - `name`: The published name of the share, required
  - `path`: Filesystem path of the share, required
  - `comment`: Description of the share, default is the same as `name`
  - `readonly`: Whether the share is read-only, default `True`
  - `uid`: User name or ID when access the share, default `nobody`
  - `gid`: Group name or ID when access the share, default `nobody`
  - `excludes`: A list of exclusions, default `['lost+found', '.*']`
  - `hostsallow`: A list of allowed hosts, default `['1.2.3.4', '2.3.4.0/24']`
  - `hostsdeny`: A list of denied hosts, default `['1.2.3.4', '2.3.4.0/24']`


Log rotation:
- `rsync_server_logrotate_interval`: Rotate log files at this interval, default `weeky`
- `rsync_server_logrotate_backlog_size`: Number of backlog files to keep, default `52`


Example Playbook
----------------

    - hosts: localhost
      roles:
      - role: rsync-server
        rsync_server_shares:
        - name: dataset-1
          comment: Public datasets
          path: /data/1


Author Information
------------------

ome-devel@lists.openmicroscopy.org.uk
