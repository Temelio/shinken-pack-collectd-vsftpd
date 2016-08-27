# shinken-pack-collectd-vsftpd

## Description

This Shinken monitoring pack is used to manage vsftpd services with our
standard deployment of Collectd.

We request Collectd data using unixsock plugin and collectd-nagios script from
collecd-utils package.

This pack depends to shinken-pack-collectd-base to work

## Objects

### Templates

#### Host templates

* collectd-vsftpd: Manage all default thresholds and values for services

### Services

| Service name              | Description             | Value specification                            | DS        | Consolidation | Warning variable | Critical variable | Duplicate_foreach variable |
|---------------------------|-------------------------|------------------------------------------------|-----------|---------------|------------------|-------------------|----------------------------|
| VSFTPD - $KEY$ processes  | Check VSFTPD processes  | processes-$VALUE1$/ps_count                    | processes | none          | $VALUE2$         | $VALUE3$          | _vsftpd_processes         |
| VSFTPD - $KEY$            | Check listening ports   | tcpconns-$VALUE1$-local/tcp_connections-LISTEN | value     | none          | $VALUE2$         | $VALUE3$          | _vsftpd_listen            |

## Default values

    _vsftpd_processes   vsftpd $(vsftpd)$$(1:1)$$(1:1)$
    _vsftpd_listen      FTPS port $(990)$$(1:1)$$(1:1)$
