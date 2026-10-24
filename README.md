# Enterprise Network Topology & Configuration (Cisco Packet Tracer)

Ez a projekt egy komplex, többrétegű vállalati hálózati topológiát valósít meg Cisco Packet Tracer környezetben, dinamikus belső útválasztással, biztonságos menedzsment hálózattal, Wi-Fi integrációval és külső internetes kapcsolattal.

## 🌐 Hálózati Architektúra és Főbb Komponensek

* **Belső Dinamikus Útválasztás (OSPF):** A belső hálózati szegmensek (routerek: `R1`, `R2`, `R3`, `R4`) között az OSPF protokoll biztosítja az automatikus útvonal-felismerést, a topológia teljes konvergenciáját és a hatékony adatforgalmat.
* **R4 & S4:** Az `R4` router kezeli a `192.168.50.0/24`-es alhálózatot, amelyhez az `S4` switch, valamint helyi eszközök és munkaállomások kapcsolódnak.
* **Vezeték nélküli Hálózat (Wi-Fi):** Az `AccessPoint0` (`IRODA` SSID) biztosítja a mobileszközök (Laptop, Smartphone) vezeték nélküli csatlakozását a vállalati hálózathoz.
* **Menedzsment VLAN (VLAN 99):** Az `S1` switch menedzsment interfésze a `10.0.99.2`-es IP-címen érhető el, ami lehetővé teszi a biztonságos távoli felügyeletet az **ADMIN** laptopról.
* **Külső Kapcsolat (Internet / ISP):** Az `ISP` routeren keresztül egy statikus alapértelmezett útvonal (`0.0.0.0/0`) biztosítja a kijárást a külvilágot szimuláló **WEB** szerver felé (`192.168.100.115`).

## ⚙️ Főbb Hálózati Szolgáltatások

* **DHCP Szolgáltatás:** Automatikus IP-cím kiosztás a belső kliensek számára az `R1` Vlan10 és vlan20 felé, `R4` pedig `S4`-en keresztül access point felé.
* **VLAN & Switch Port Konfiguráció:** Szegmentált hálózati struktúra, aktív Trunk és Access portokkal.
* **Routing Policy:** 
  * Házon belül dinamikus **OSPF** routing.
  * A külvilág (ISP / WEB szerver) felé irányuló forgalomnál optimalizált statikus alapértelmezett útvonal.

## 🛠️ Ellenőrzési és Tesztelési Eredmények

* **OSPF konvergencia:** A routerek útvonaltábláiban (`show ip route`) minden alhálózat hibátlanul szerepel.
* **Külső elérés:** A belső kliensekről (pl. `PC1`, `PC7`) indított ping tesztek a külső WEB szerver felé 0%-os csomagveszteséggel futnak le.
* **Menedzsment:** Az ADMIN laptopról az S1 switch irányába (`ping 10.0.99.2`) sikeres, stabil távoli kapcsolat építhető ki.
