# router-bfd
# Table of Contents

- [Management](#management)
  - [Management Interfaces](#management-interfaces)
- [BFD](#bfd)
  - [Router BFD](#router-bfd)

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

# BFD

## Router BFD

### Router BFD Singlehop Summary

| Interval | Minimum RX | Multiplier |
| -------- | ---------- | ---------- |
| 900 | 900 | 50 |

### Router BFD Multihop Summary

| Interval | Minimum RX | Multiplier |
| -------- | ---------- | ---------- |
| 300 | 300 | 3 |

### Router BFD SBFD Summary

| Initiator Interval | Initiator Multiplier | Reflector Minimum RX | Reflector Local-Discriminator |
| ------------------ | -------------------- | -------------------- | ----------------------------- |
| 500 | 3 | 600 | 155.1.3.1 |

### Router BFD Device Configuration

```eos
!
router bfd
   interval 900 min-rx 900 multiplier 50 default
   multihop interval 300 min-rx 300 multiplier 3
   !
   sbfd
      local-interface Loopback0 ipv4 ipv6
      initiator interval 500 multiplier 3
      reflector min-rx 600
      reflector local-discriminator 155.1.3.1
```
