# base
# Table of Contents

- [Management](#management)
  - [Management Interfaces](#management-interfaces)
  - [Management SSH](#management-ssh)
  - [Management Console](#management-console)
  - [Management API HTTP](#management-api-http)
- [Management Security](#management-security)
  - [Management Security Summary](#management-security-summary)
  - [Management Security Configuration](#management-security-configuration)
- [EOS CLI](#eos-cli)

# Management

## Management Interfaces

### Management Interfaces Summary

#### IPv4

| Management Interface | description | Type | VRF | IP Address | Gateway |
| -------------------- | ----------- | ---- | --- | ---------- | ------- |
| Management1 | oob_management | oob | MGMT | 10.73.255.122/24 | 10.73.255.2 |

#### IPv6

| Management Interface | description | Type | VRF | IPv6 Address | IPv6 Gateway |
| -------------------- | ----------- | ---- | --- | ------------ | ------------ |
| Management1 | oob_management | oob | MGMT | - | - |

### Management Interfaces Device Configuration

```eos
!
interface Management1
   description oob_management
   vrf MGMT
   ip address 10.73.255.122/24
```

## Management SSH

### IPv4 ACL

| IPv4 ACL | VRF |
| -------- | --- |
| ACL-SSH | - |
| ACL-SSH-VRF | mgt |

### IPv6 ACL

| IPv6 ACL | VRF |
| -------- | --- |
| ACL-SSH6 | - |
| ACL-SSH-VRF6 | mgt |

 ### SSH timeout and management

| Idle Timeout | SSH Management |
| ------------ | -------------- |
| 15 | Enabled |

### Max number of SSH sessions limit and per-host limit

| Connection Limit | Max from a single Host |
| ---------------- | ---------------------- |
| - | 12 |

### Ciphers and algorithms

| Ciphers | Key-exchange methods | MAC algorithms | Hostkey server algorithms |
|---------|----------------------|----------------|---------------------------|
| default | default | default | default |

### VRFs

| VRF | Status |
| --- | ------ |
| mgt | Enabled |

### Management SSH Configuration

```eos
!
management ssh
   ip access-group ACL-SSH in
   ip access-group ACL-SSH-VRF vrf mgt in
   ipv6 access-group ACL-SSH6 in
   ipv6 access-group ACL-SSH-VRF6 vrf mgt in
   idle-timeout 15
   connection per-host 12
   no shutdown
   !
   vrf mgt
      no shutdown
```

## Management Console

### Management Console Timeout

Management Console Timeout is set to **300** minutes.

### Management Console Configuration

```eos
!
management console
   idle-timeout 300
```

## Management API HTTP

### Management API HTTP Summary

| HTTP | HTTPS | Default Services |
| ---- | ----- | ---------------- |
| True | True | - |

### Management API VRF Access

| VRF Name | IPv4 ACL | IPv6 ACL |
| -------- | -------- | -------- |
| mgt | ACL-API | - |

### Management API HTTP Configuration

```eos
!
management api http-commands
   protocol https
   protocol http
   no shutdown
   !
   vrf mgt
      no shutdown
      ip access-group ACL-API
```

# Management Security

## Management Security Summary

| Settings | Value |
| -------- | ----- |
| Common password encryption key | True |

## Management Security Configuration

```eos
!
management security
   password encryption-key common
```

# EOS CLI

```eos
!
interface Loopback1000
  description Interface created with eos_cli on device level

```
