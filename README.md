# Jetson-Orin-Nano-2025

NVME ssd(sk-hynix p41, 500gb 제품 사용)에 os를 설치하여 Orin-Nano Booting 시도

1. SDK 설치해서 우분투에서 리커버리 모드로 연결하여 시도 -> 실패
2. SD카드 이미저를 NVME에 Flash 후, 부트로더 수정하여 성공

# 마운트 폴더 생성
sudo mkdir -p /mnt/jetson

# SSD 파티션 마운트 (lsblk로 실제 장치명 확인)
sudo mount /dev/nvme0n1p1 /mnt/jetson

sudo vi /mnt/jetson/boot/extlinux/extlinux.conf

화살표 키로 APPEND root=/dev/mmcblk0p1 rw rootwait 줄로 이동

i 키 → 편집 모드 진입 (화면 아래에 -- INSERT -- 표시)

/dev/mmcblk0p1 부분을 /dev/nvme0n1p1로 수정

APPEND root=/dev/nvme0n1p1 rw rootwait
