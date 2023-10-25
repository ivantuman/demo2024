
# demo2024
# №1
Сначала я рассчитываю  IP-адреса
# Таблица
|Имя устройства  |Интерфейс           |IPv4            |Маска/Префикс   |Шлюз            |
|  ------------- | -------------      | -------------  |  ------------- |  -------------       |
|ISP             |ens192              |10.12.29.10     |/24             |10.12.29.10         |
|                |ens224              |192.168.0.160   |/30             |                      |
|                |ens225              |192.168.0.164   |/30             |                      |
|HQ-R            |ens192              |192.168.0.159   |/30             |192.168.0.160       |
|                |ens224              |192.168.0.1     |/25             |                      |
|BR-R            |ens192              |192.168.0.163   |/30             |192.168.0.159        |
|                |ens224              |192.168.0.127   |/27             | 192.168.0.159                     |
|HQ-SRV          |ens192              |192.168.0.125   |/25             |192.168.0.1           |
|BR-SRV          |ens192              |192.168.0.156   |/27             |192.168.0.127       |

# Топология
![2023-10-25_13-57-07](https://github.com/IvanTumanov123/demo2024/assets/148867523/39edd56f-da00-4eac-a9a7-040a92ba4080)

Далее я захожу в файл конфигурации 
```
nano /etc/network/interfaces
```
И ввожу следующее:
```
auto ens192
iface ens192 inet static
address 10.12.29.10
netmask 255.255.255.0
gateway 10.12.29.254

auto ens224
iface ens224 inet static
address 192.168.0.160
netmask 255.255.255.252

auto ens225
iface ens225 inet static
address 192.168.0.164
netmask 255.255.255.252
```
Делаю всё так же и с другими виртуальными машинами
# №1.2
Сначала я устанавливаю пакеты FRR
```
apt-get install frr
```
