## Storage

> 참고 (By. 홍)
>
> 현재 쿠버네티스 클러스터 규모와 운영 복잡도를 고려했을 때, 별도의 CSI를 추가하기보다는 k3s 기본 제공 local-path 스토리지를 사용하는 것이 가장 적절해보임.<br/>
> 따라서, 별도의 CSI 추가 없이 기본 local-path 에서 `Retain` 정책만 추가하여 사용.<br/>
>
> 필요 시, 아래의 CSI 드라이버들을 대상으로 PoC를 진행한 뒤 도입 여부를 검토 예정

- [Proxmox CSI](https://github.com/sergelogvinov/proxmox-csi-plugin)
- [OpenEBS CSI](https://github.com/openebs/openebs)
- [LongHorn CSI](https://github.com/longhorn/longhorn)

Proxmox CSI 같은 경우, 리포지토리 자체 스타수가 좀 적고 reddit에서 프로덕션 사용사례에 대한 언급이 댓글은 봤지만, 구체적인 구성 방법이나 운영 사례에 대한 레퍼런스를 찾지 못함.
