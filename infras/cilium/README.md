# cilium

[cilium helm](https://github.com/cilium/cilium/tree/main/install/kubernetes/cilium)

## frr.conf (FRR)

```frr
router bgp 65000
  bgp router-id 172.16.0.254
  bgp bestpath as-path multipath-relax
  timers bgp 3 9

  ! K8S 노드
  neighbor K8S-PEERS peer-group
  neighbor K8S-PEERS remote-as 64512
  neighbor K8S-PEERS send-community both
  neighbor K8S-PEERS route-map RM-IN-LB in
  neighbor K8S-PEERS route-map RM-OUT-NONE out
  bgp listen range 172.16.0.0/24 peer-group K8S-PEERS


  ! LAN 이웃 (내부 코어)
  neighbor 172.16.0.1 peer-group LAN-PEERS
  neighbor LAN-PEERS remote-as 64510
  neighbor LAN-PEERS send-community both
  neighbor LAN-PEERS route-map RM-OUT-LAN out

  address-family ipv4 unicast
    maximum-paths 8
  exit-address-family

! VIP 허용 대역
ip prefix-list PL-LB-V4 seq 10 permit 172.16.100.240/30 le 32

! 커뮤니티 분리
ip community-list standard GW-EXT permit 65000:100
ip community-list standard GW-INT permit 65000:200

! K8S에서 들어오는 경로 수용 (커뮤니티 기반 가중치/정책)
route-map RM-IN-LB permit 10
  match ip address prefix-list PL-LB-V4
  match community GW-EXT
  set weight 300
!
route-map RM-IN-LB permit 20
  match ip address prefix-list PL-LB-V4
  match community GW-INT
  set weight 200
!
route-map RM-IN-LB permit 100
  match ip address prefix-list PL-LB-V4

! K8S로 역광고는 없음
route-map RM-OUT-NONE permit 10

! WAN 으로는 external 만 내보냄
route-map RM-OUT-ISP permit 10
  match ip address prefix-list PL-LB-V4
  match community GW-EXT
!
route-map RM-OUT-ISP deny 100

! LAN으로는 internal 만 내보냄
route-map RM-OUT-LAN permit 10
  match ip address prefix-list PL-LB-V4
  match community GW-INT
!
```
