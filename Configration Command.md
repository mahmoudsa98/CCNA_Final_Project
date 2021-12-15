# CCNA_Final_Project
Configration Command
<<<<<<<<<<<<<<<<<<< <<<<<<<<<<<<<<<<<<< <<<<<<<<<<<<<<<<<<<  <><> <> <><> >>>>>>>>>>>>>>>>>>> >>>>>>>>>>>>>>>>>>> >>>>>>>>>>>>>>>>>>> 
                                             MAHMOUD SAFWAT MAHAMED ESMAT KHATER
<<<<<<<<<<<<<<<<<<< <<<<<<<<<<<<<<<<<<< <<<<<<<<<<<<<<<<<<< START >>>>>>>>>>>>>>>>>>> >>>>>>>>>>>>>>>>>>> >>>>>>>>>>>>>>>>>>>

<<<<<<<<<<<<<<<<<<< <<<<<<<<<<<<<<<<<<< <<<<<<<<<<<<<<<<<<< LEFT >>>>>>>>>>>>>>>>>>> >>>>>>>>>>>>>>>>>>> >>>>>>>>>>>>>>>>>>>

                                                          < < SW1 > >
Switch>en

Switch#conf t

Switch(config)#hostname SW1

SW1(config)#vtp mode server 

SW1(config)#vtp domain ccna

SW1(config)#vtp password cisco

SW1(config)#int range f0/1-4

SW1(config-if-range)#switchport mode trunk 
SW1(config-if-range)#switchport nonegotiate
SW1(config-if-range)#switchport trunk native vlan 99  
SW1(config-if-range)#exit
SW1(config)#vlan 10
SW1(config-vlan)#name to_lan_10
SW1(config-vlan)#vlan 20
SW1(config-vlan)#name to_lan_20
SW1(config-vlan)#vlan 30
SW1(config-vlan)#name to_lan_30
SW1(config-vlan)#exit
SW1(config)#spanning-tree vlan 20 root primary 

                                                          < < SW2 > >
Switch>en
Switch#conf t
SW2(config)#hostname SW2 
SW2(config)#int range f0/3, f0/14, f0/23
SW2(config-if-range)#switchport mode access 
SW2(config-if-range)#switchport port-security maximum 5
SW2(config-if-range)#switchport port-security mac-address sticky 
SW2(config-if-range)#switchport port-security violation restrict 
SW2(config-if-range)#switchport port-security aging time 1440
SW2(config-if-range)#spanning-tree bpduguard enable 
SW2(config-if-range)#spanning-tree portfast
SW2(config-if-range)#exit
SW2(config)#vtp mode client 
SW2(config)#vtp domain ccna
SW2(config)#vtp password cisco
SW2(config)#int range f0/2,f0/4
SW2(config-if-range)#switchport mode trunk
SW2(config-if-range)#switchport nonegotiate  
SW2(config-if-range)#switchport trunk native vlan 99  
SW2(config-if-range)#exit
SW2(config)#spanning-tree vlan 20 root primary 
SW2(config)#int f0/3
SW2(config-if)#switchport access vlan 10
SW2(config-if)#int f0/14
SW2(config-if)#switchport access vlan 20
SW2(config-if)#int f0/23
SW2(config-if)#switchport access vlan 30

                                                           < < SW3 > >
Switch>en 
Switch#conf t
Switch(config)#hostname SW3
SW3(config)#int range f0/2, f0/15, f0/23
SW3(config-if-range)#switchport mode access 
SW3(config-if-range)#switchport port-security maximum 5
SW3(config-if-range)#switchport port-security mac-address sticky 
SW3(config-if-range)#switchport port-security violation restrict 
SW3(config-if-range)#switchport port-security aging time 1440
SW3(config-if-range)#spanning-tree bpduguard enable 
SW3(config-if-range)#spanning-tree portfast 
SW3(config-if-range)#exit
SW3(config)#vtp mode client 
SW3(config)#vtp domain ccna
SW3(config)#vtp password cisco
SW3(config)#int range f0/3, f0/4
SW3(config-if-range)#switchport mode trunk 
SW3(config-if-range)#switchport nonegotiate 
SW3(config-if-range)#switchport trunk native vlan 99  
SW3(config-if-range)#exit
SW3(config)#spanning-tree vlan 20 root primary 
SW3(config)#int f0/2
SW3(config-if)#switchport access vlan 10
SW3(config-if)#int f0/15
SW3(config-if)#switchport access vlan 20
SW3(config-if)#int f0/23
SW3(config-if)#switchport access vlan 30
 
                                                         < < Router 1 > >
Router>en
Router#conf t
Router(config)#hostname Router_1
Router_1(config)#int g0/1
Router_1(config-if)#no shutdown 
Router_1(config-if)#standby version 2
Router_1(config-if)#exit
Router_1(config)#int g0/1.10
Router_1(config-subif)#encapsulation dot1Q 10
Router_1(config-subif)#ip address 192.168.10.1 255.255.255.0
Router_1(config-subif)#standby 10 ip 192.168.10.254
Router_1(config-subif)#standby 10 priority 150
Router_1(config-subif)#standby 10 preempt
Router_1(config-subif)#ip ospf 10 area 0
Router_1(config-subif)#exit
Router_1(config)#int g0/1.20
Router_1(config-subif)#encapsulation dot1Q 20
Router_1(config-subif)#ip address 192.168.20.1 255.255.255.0
Router_1(config-subif)#standby 20 ip 192.168.20.254
Router_1(config-subif)#standby 20 priority 150
Router_1(config-subif)#standby 20 preempt
Router_1(config-subif)#ip ospf 10 area 0
Router_1(config-subif)#exit
Router_1(config-subif)#int g0/1.30
Router_1(config-subif)#encapsulation dot1Q 30
Router_1(config-subif)#ip address 192.168.30.1 255.255.255.0
Router_1(config-subif)#standby 30 ip 192.168.30.254
Router_1(config-subif)#standby 30 preempt
Router_1(config-subif)#ip ospf 10 area 0
Router_1(config-subif)#exit
Router_1(config)#int g0/0
Router_1(config-if)#ip address 10.1.1.1 255.255.255.252
Router_1(config-if)#no shutdown 
Router_1(config-if)#ip ospf 10 area 0
Router_1(config-if)#ip ospf network point-to-point
Router_1(config-if)#exit
Router_1(config)#router ospf 10 
Router_1(config-router)#passive-interface g0/1.10
Router_1(config-router)#passive-interface g0/1.20
Router_1(config-router)#passive-interface g0/1.30
Router_1(config-router)#exit
ctrl + z
Router_1#
Router_1#copy running-config tftp
Address or name of remote host []? 192.168.80.253
Destination filename [Router_1-confg]? 
Router_1#dir flash
Router_1#copy flash: tftp
Source filename []? c2900-universalk9-mz.SPA.151-4.M4.bin
Address or name of remote host []? 192.168.80.253
Destination filename [c2900-universalk9-mz.SPA.151-4.M4.bin]? R1_Mahmoud_Safwat_c2900-universalk9-mz.SPA.151-4.M4.bin

                                                           < < Router 2 > >
Router>en
Router#conf t
Router(config)#hostname Router_2
Router_2(config)#int g0/0
Router_2(config-if)#no shutdown 
Router_2(config-if)#standby version 2
Router_2(config-if)#exit
Router_2(config)#int g0/0.10
Router_2(config-subif)#encapsulation dot1Q 10
Router_2(config-subif)#ip address 192.168.10.2 255.255.255.0
Router_2(config-subif)#standby 10 ip 192.168.10.254
Router_2(config-subif)#standby 10 preempt
Router_2(config-subif)#exit
Router_2(config)#int g0/0.20
Router_2(config-subif)#encapsulation dot1Q 20
Router_2(config-subif)#ip address 192.168.20.2 255.255.255.0
Router_2(config-subif)#standby 20 ip 192.168.20.254
Router_2(config-subif)#standby 20 preempt
Router_2(config-subif)#exit
Router_2(config-subif)#int g0/0.30
Router_2(config-subif)#encapsulation dot1Q 30
Router_2(config-subif)#ip address 192.168.30.2 255.255.255.0
Router_2(config-subif)#standby 30 ip 192.168.30.254
Router_2(config-subif)#standby 30 priority 150
Router_2(config-subif)#standby 30 preempt
Router_2(config-subif)#exit
Router_2(config)#int g0/1
Router_2(config-if)#ip address 10.2.2.1 255.255.255.252
Router_2(config-if)#no shutdown 
Router_2(config-if)#ip ospf 10 area 0
Router_2(config-if)#ip ospf network point-to-point 
Router_2(config-if)#exit
Router_2(config-if)#router ospf 10
Router_2(config-router)#passive-interface g0/0.10
Router_2(config-router)#passive-interface g0/0.20
Router_2(config-router)#passive-interface g0/0.30
Router_2(config-if)#exit
Router_2(config)#int g0/0.10
Router_2(config-subif)#ip ospf 10 area 0
Router_2(config-subif)#int g0/0.20
Router_2(config-subif)#ip ospf 10 area 0
Router_2(config-subif)#int g0/0.30
Router_2(config-subif)#ip ospf 10 area 0
ctrl + z
Router_2#
Router_2#copy running-config tftp
Address or name of remote host []? 192.168.80.253
Destination filename [Router_2-confg]? 
Router_2#dir flash
Router_2#copy flash: tftp
Source filename []? c2900-universalk9-mz.SPA.151-4.M4.bin
Address or name of remote host []? 192.168.80.253
Destination filename [c2900-universalk9-mz.SPA.151-4.M4.bin]? R2_Mahmoud_Safwat_c2900-universalk9-mz.SPA.151-4.M4.bin

<<PCs Configration>>
                     ip               mask            gateway
vlan 10 PCs
PC3              192.168.10.5          /24         192.168.10.254
PC6              192.168.10.6          /24         192.168.10.254
vlan 20 PCs
PC4              192.168.20.5          /24         192.168.20.254
PC7              192.168.20.6          /24         192.168.20.254
vlan 30 PCs
PC5              192.168.30.5          /24         192.168.30.254
PC8              192.168.30.6          /24         192.168.30.254

<<<<<<<<<<<<<<<<<<< <<<<<<<<<<<<<<<<<<< <<<<<<<<<<<<<<<<<<< MID >>>>>>>>>>>>>>>>>>> >>>>>>>>>>>>>>>>>>> >>>>>>>>>>>>>>>>>>>

                                                         < < MLS > >
Switch>en
Switch#conf t
Switch(config)#hostname MLS
MLS(config)#ip routing 
MLS(config)#int g1/0/1
MLS(config-if)#no switchport 
MLS(config-if)#ip address 10.1.1.2 255.255.255.252
MLS(config-if)#ip ospf 10 area 20
MLS(config-if)#ip ospf network point-to-point
MLS(config-if)#exit
MLS(config)#int g1/0/2
MLS(config-if)#no switchport 
MLS(config-if)#ip address 10.2.2.2 255.255.255.252
MLS(config-if)#ip ospf 10 area 20
MLS(config-if)#ip ospf network point-to-point
MLS(config-if)#exit
MLS(config)#int g1/0/3
MLS(config-if)#switchport trunk encapsulation dot1q 
MLS(config-if)#switchport mode trunk 
MLS(config-if)# exit
MLS(config)#int g1/0/4
MLS(config-if)#no switchport 
MLS(config-if)#ip address 10.3.3.2 255.255.255.252
MLS(config-if)#ip ospf 10 area 20
MLS(config-if)#ip ospf network point-to-point
MLS(config-if)#exit
MLS(config)#vlan 40
MLS(config-vlan)#vlan 50
MLS(config-vlan)#vlan 60
MLS(config-vlan)#exit
MLS(config)#int vlan 40
MLS(config-if)#ip address 172.16.0.97 255.255.255.240
MLS(config-if)#ip ospf 10 area 0
MLS(config-if)#exit
MLS(config)#int vlan 50
MLS(config-if)#ip address 172.16.0.1 255.255.255.192
MLS(config-if)#ip ospf 10 area 0
MLS(config-if)#int vlan 60
MLS(config-if)#no ip address 172.16.0.65 255.255.255.224
MLS(config-if)#ip ospf 10 area 0
MLS(config-if)#exit
MLS(config)#router ospf 10
MLS(config-router)#passive-interface vlan 40
MLS(config-router)#passive-interface vlan 50
MLS(config-router)#passive-interface vlan 60
MLS(config-router)#exit
MLS(config-if)#exit
MLS(config)#access-list 1 deny 192.168.10.0 0.0.0.255
MLS(config)#access-list 1 permit any 
MLS(config)#int vlan 50
MLS(config-if)#ip access-group 1 out
MLS(config-if)#exit
MLS(config)#ip access-list extended web-server
MLS(config-ext-nacl)#deny tcp 192.168.10.0 0.0.0.255 host 192.168.80.254 eq 80
MLS(config-ext-nacl)#deny tcp 192.168.20.0 0.0.0.255 host 192.168.80.254 eq 80
MLS(config-ext-nacl)#deny tcp 192.168.30.0 0.0.0.255 host 192.168.80.254 eq 80
MLS(config-ext-nacl)#deny tcp 172.16.0.0 0.0.0.63 host 192.168.80.254 eq 80
MLS(config-ext-nacl)#permit ip any any 
MLS(config-ext-nacl)#exit
MLS(config)#in g1/0/4
MLS(config-if)#ip access-group web-server out
ctrl + z
MLS#
MLS#copy running-config tftp
Address or name of remote host []? 192.168.80.253
Destination filename [MLS-confg]? 
MLS#dir flash
MLS#copy flash: tftp
Source filename []? c2900-universalk9-mz.SPA.151-4.M4.bin
Address or name of remote host []? 192.168.80.253
Destination filename [c2900-universalk9-mz.SPA.151-4.M4.bin]? MLS_Mahmoud_Safwat_c2900-universalk9-mz.SPA.151-4.M4.bin

                                                           < < SW4 > >
Switch>en
Switch#conf t
Switch(config)#hostname SW4
SW4(config)#vlan 40
SW4(config-vlan)#vlan 50
SW4(config-vlan)#vlan 60
SW4(config-vlan)#exit
SW4(config)#int f0/2
SW4(config-if)#switchport mode access 
SW4(config-if)#switchport access vlan 40
SW4(config-if)#exit
SW4(config)#int f0/13
SW4(config-if)#switchport mode access 
SW4(config-if)#switchport access vlan 50
SW4(config-if)#int f0/21
SW4(config-if)#switchport mode access 
SW4(config-if)#switchport access vlan 60
SW4(config-if)#exit
SW4(config)#int g0/1
SW4(config-if)#switchport mode trunk 

<<PCs Configration>>
                     ip               mask            gateway
vlan 40 PC
PC9              172.16.0.99           /28          172.16.0.97
vlan 50 PC
PC10             172.16.0.15           /24          172.16.0.1
vlan 60 PC
PC11             172.16.0.72           /24          172.16.0.65
 
>>>>>>>>>>>>>>>>>>> >>>>>>>>>>>>>>>>>>> >>>>>>>>>>>>>>>>>>> RIGHT >>>>>>>>>>>>>>>>>>> >>>>>>>>>>>>>>>>>>> >>>>>>>>>>>>>>>>>>>

                                                        < < Router 3 > >
outer>en 
Router#conf t
Router(config)#hostname Router_3
Router_3(config)#int g0/1
Router_3(config-if)#ip address 10.3.3.1 255.255.255.252
Router_3(config-if)#no shutdown
Router_3(config-if)#ip ospf 10 area 20
Router_3(config-if)#ip ospf network point-to-point
Router_3(config-if)#exit
Router_3(config)#int g0/0
Router_3(config-if)#ip address 192.168.80.1 255.255.255.0
Router_3(config-if)#no shutdown 
Router_3(config-if)#exit
Router_3(config)#ip dhcp excluded-address 192.168.80.250 192.168.80.254 
Router_3(config)#ip dhcp pool LAN_1
Router_3(dhcp-config)#network 192.168.80.0 255.255.255.0
Router_3(dhcp-config)#default-router 192.168.80.1
Router_3(dhcp-config)#domain-name cisco.com
Router_3(dhcp-config)#dns-server 15.1.1.1
Router_3(dhcp-config)#exit
Router_3(config)#int g0/2
Router_3(config-if)#ip address dhcp 
Router_3(config-if)#no shutdown
Router_3(config-if)#ip ospf 10 area 20
Router_3(config-if)#exit
Router_3(config)#ip route 0.0.0.0 0.0.0.0 g0/2
Router_3(config)#router ospf 10
Router_3(config-router)#default-information originate
Router_3(config-router)#passive-interface g0/2
Router_3(config-router)#passive-interface g0/0
Router_3(config-router)#exit
Router_3(config)#int g0/1
Router_3(config-if)#ip ospf net
Router_3(config-if)#ip ospf network poi
Router_3(config-if)#ip ospf network point-to-point 
Router_3(config)#access-list 1 permit 192.168.0.0 0.0.255.255
Router_3(config)#access-list 1 permit 172.16.0.0 0.0.0.255
Router_3(config)#ip nat inside source list 1 interface g0/2
Router_3(config)#int g0/1
Router_3(config-if)#ip nat inside 
Router_3(config-if)#int g0/0
Router_3(config-if)#ip nat inside 
Router_3(config-if)#int g0/2
Router_3(config-if)#ip nat outside 
Router_3(config-if)#exit
Router_3(config)#ip domain-name nti.com
Router_3(config)#username admin privilege 15 secret cisco
Router_3(config)#crypto key generate rsa
            [512]: 1024
Router_3(config)#line vty 0 15
Router_3(config-line)#transport input ssh
Router_3(config-line)#login local 
Router_3(config)#ip access-list standard VTY
Router_3(config-std-nacl)#permit 172.16.0.99 0.0.0.15
Router_3(config-std-nacl)#exit
Router_3(config)#line vty 0 15 
Router_3(config-line)#access-class VTY in
ctrl + z
Router_3#
Router_3#copy running-config tftp
Address or name of remote host []? 192.168.80.253
Destination filename [Router_3-confg]? 
Router_3#dir flash
Router_3#copy flash: tftp
Source filename []? c2900-universalk9-mz.SPA.151-4.M4.bin
Address or name of remote host []? 192.168.80.253
Destination filename [c2900-universalk9-mz.SPA.151-4.M4.bin]? R3_Mahmoud_Safwat_c2900-universalk9-mz.SPA.151-4.M4.bin

                                                           < < SW5 > >
Switch>en
Switch#conf t
Switch(config)#hostname SW5
SW5(config)#int range f0/2-3
SW5(config-if-range)#channel-group  1 mode active 
SW5(config-if-range)#exit
SW5(config)#int f0/1
SW5(config-if)#switchport mode trunk 
Switch(config-if)#exit
SW5(config)#int port-channel 1
SW5(config-if)#switchport mode trunk 
Switch(config-if)#exit

                                                           < < SW6 > >
Switch>en             
Switch#conf t
Switch(config)#hostname SW6
SW6(config)#int range f0/2-3
SW6(config-if-range)#channel-group  1 mode active 
SW6(config-if-range)#exit
SW6(config)#int port-channel 1
SW6(config-if)#switchport mode trunk 
Switch(config-if)#exit

<<PCs Configration>> "DHCP"
>>>>>>>>>>>>>>>>>>> >>>>>>>>>>>>>>>>>>> >>>>>>>>>>>>>>>>>>> <> <> <> >>>>>>>>>>>>>>>>>>> >>>>>>>>>>>>>>>>>>> >>>>>>>>>>>>>>>>>>>



                                                         < < SHOW Used > >
show ip route
show ip ospf neighbor
show ip ospf interface
show ip int breif
show vlan
>>>>>>>>>>>>>>>>>>> >>>>>>>>>>>>>>>>>>> >>>>>>>>>>>>>>>>>>> END >>>>>>>>>>>>>>>>>>> >>>>>>>>>>>>>>>>>>> >>>>>>>>>>>>>>>>>>>

                                             MAHMOUD SAFWAT MAHAMED ESMAT KHATER
>>>>>>>>>>>>>>>>>>> >>>>>>>>>>>>>>>>>>> >>>>>>>>>>>>>>>>>>> <><> <> <><> >>>>>>>>>>>>>>>>>>> >>>>>>>>>>>>>>>>>>> >>>>>>>>>>>>>>>>>>>
