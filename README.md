# Домашнее задание к занятию  «Защита хоста»
### Задание 1

1. Установите **eCryptfs**.
2. Добавьте пользователя cryptouser.
3. Зашифруйте домашний каталог пользователя с помощью eCryptfs.

sudo apt-get install ecryptfs-utils

sudo add cryptouser

sudo adduser cryptouser

sudo ecryptfs-migrate-home -u ska

![1](https://github.com/BOSe1337/host/blob/main/1.JPG)


### Задание 2

1. Установите поддержку **LUKS**.
2. Создайте небольшой раздел, например, 100 Мб.
3. Зашифруйте созданный раздел с помощью LUKS.

![2](https://github.com/BOSe1337/host/blob/main/2.JPG)

![3](https://github.com/BOSe1337/host/blob/main/3.JPG)

![4](https://github.com/BOSe1337/host/blob/main/4.JPG)

![5](https://github.com/BOSe1337/host/blob/main/5.JPG)

lsblk

sudo dd if=/dev/urandom of=/root/secret.key bs=1024 count=2

sudo chmod 0400 /root/secret.key

sudo apt-get install cryptsetup

cryptsetup luksFormat /dev/sdb /root/secret.key

sudo cryptsetup luksFormat /dev/sdb /root/secret.key

sudo cryptsetup luksAddKey /dev/sdb /root/secret.key --key-file=/root/secret.key

sudo cryptsetup luksOpen /dev/sdb secret --key-file=/root/secret.key

sudo cryptsetup resize secret

sudo nano /root/secret.key

sudo cryptsetup resize secret

lsblk

mkfs.ext4 /dev/mapper/secret

cryptsetup -v status secret

lsblk

cryptsetup luksDump /dev/sdb

sudo mkdir -p /secret

sudo chmod 755 /secret

mount /dev/mapper/secret /secret

df -h

lsblk
