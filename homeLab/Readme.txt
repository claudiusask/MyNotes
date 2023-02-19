Appart from this normal config script, we should add DHCP & DNS sevrice for the interfaces we require DHCP or DNS. For example:
  -     DHCP:
  - set service dhcp-server shared-network-name LANeth1 subnet 10.0.10.0/24 range 0 start 10.0.10.50      # start of ip address to assign
  - set service dhcp-server shared-network-name LANeth1 subnet 10.0.10.0/24 range 0 stop 10.0.10.200      # stop of ip address to assign
  - ##        Anything before 10.0.10.50 and anything after 10.0.10.200 we can use for static assignment.
  - set service dhcp-server shared-network-name LANeth1 subnet 10.0.10.0/24 name-server 10.0.10.254       # DNS from this subnet address will go to this name-server.
  - set service dhcp-server shared-network-name LANeth1 subnet 10.0.10.0/24 default-router 10.0.10.254    # configure default router for all addresses of this subnet.
  
  
  -     DNS:
  - set service dns forwarding domain home.lab server 192.168..X.X(DNS-Server-ip)      # anyone in LAN asking for server.home.lab will be served by this DNS server.
  - set service dns forwarding name-server 1.1.1.1      # Anything that is not home.lab will go to this DNS server, we can add multiple DNS-Servers.
  - set service dns forwarding listen-address 10.10.10.254     # Only this subnet-gateway can ask for DNS queries - possible to add multiple.
  - set service dns forwarding allow-from 10.10.10.0/24        # only this subnet is allowed - possible to add multiple.
  
  
  - Keep system name-server to the Bind9 server which is my main DNS in the infrastructure. 
