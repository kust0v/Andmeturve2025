Praktikum 10

skript.sh sisu:

#!/bin/sh  
iptables -F  
iptables -X naabrid 2>/dev/null  
iptables -N naabrid  
iptables -A naabrid -j LOG --log-prefix "Kustov-NAABRID-ahel: "  
iptables -A naabrid -p icmp --icmp-type echo-request -j ACCEPT  
iptables -A naabrid -m state --state NEW -p tcp --dport 22 -j LOG --log-prefix "ssh yhendused: "  
iptables -A naabrid -m state --state NEW -p tcp --dport 22 -j ACCEPT  
iptables -A naabrid -m state --state NEW -p tcp --dport 80 -j ACCEPT  
iptables -A naabrid -m state --state NEW -p tcp --dport 443 -j ACCEPT  
iptables -A naabrid -m state --state NEW -p tcp --dport 25 -j ACCEPT  
iptables -A naabrid -j RETURN  
iptables -A INPUT -i lo -j ACCEPT  
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT  
iptables -A INPUT -s 172.20.10.6 -j naabrid  
iptables -A INPUT -j LOG --log-prefix "input-reject "  
iptables -A INPUT -j REJECT  

![Kuvatõmmis 2025-05-29 184710](https://github.com/user-attachments/assets/645dbea1-86ea-4325-923f-87557c62d678)

![Kuvatõmmis 2025-05-29 202246](https://github.com/user-attachments/assets/a4388e40-cd1f-47a9-b4b9-1d90a043a17d)

10-4 Portide skannimine IPv6 aadressi põhjal, DDoS rünnakud otse IPv6 seadme aadressile ja fragmentatsiooni rünnakud.  

10-5 Sest nad lähtuvad turvafilosoofiast, et vaikimisi ei tööta süsteemis ükski teenus, mis oleks kuulamas. See tähendab, et kui kasutaja ei ole ise midagi avanud, siis pole midagi, mida tulemüür peaks kaitsma  

10-6 Rünne nimega ND spoofing. Selle ründe käigus saadab ründaja võltsitud NDP teateid, et suunata ohvri võrguliiklus enda seadmesse. See võimaldab man-in-the-middle rünnakuid. Viide: https://en.wikipedia.org/wiki/Neighbor_Discovery_Protocol#Security_issues
