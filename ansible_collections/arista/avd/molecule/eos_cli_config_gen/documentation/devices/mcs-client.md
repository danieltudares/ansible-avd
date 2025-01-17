# mcs-client
# Table of Contents

- [Management](#management)
  - [Management Interfaces](#management-interfaces)
- [Monitoring](#monitoring)
  - [MCS client Summary](#mcs-client-summary)

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

# Monitoring

## MCS client Summary

MCS client is enabled

| Secondary CVX cluster | Server Hosts | Enabled |
| --------------------- | ------------ | ------- |
| default | 10.90.224.188, 10.90.224.189, leaf2.atd.lab | True |

### MCS client configuration

```eos
!
mcs client
   no shutdown
   !
   cvx secondary default
      no shutdown
      server host 10.90.224.188
      server host 10.90.224.189
      server host leaf2.atd.lab
```
