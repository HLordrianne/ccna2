@C1: 
Config t
vlan 20
name Accenture.com
Interface vlan 20
 desc Accenture.com
 no shut
 ip add 10.0.0.129 255.255.255.128
ip dhcp excluded-add 10.0.0.129 10.0.0.139
ip dhcp pool Accenture.com
 network 10.0.0.129 255.255.255.128
 default-router 10.0.0.129
 domain-name Accenture.com
Int e1/0
 no shut
 switchport mode access
 switch access vlan 20
@S1
config t
int e1/0
no shut
ip add dhcp
do bp

**********FOR CHEV****************************
@C1
Config t
vlan 21
name CHEVRON.com
Interface vlan 21
 desc CHEVRON.com
 no shut
 ip add 10.0.8.1 255.255.248.0
ip dhcp excluded-add 10.0.8.1 10.0.8.100
ip dhcp pool CHEVRON.com
 network 10.0.8.1 255.255.248.0
 default-router 10.0.8.1
 domain-name CHEVRON.com
@A1: 
Int e0/0
 no shut
 switchport mode access
 switch access vlan 21
 DO SH VLAN BRIEF
@P1
config t
int e0/0
no shut
ip add dhcp
do bp


**********FOR SHELL**********************
Config t
vlan 22
name SHELL.COM
Interface vlan 22
 desc SHELL.COM
 no shut
 ip add 10.0.16.1 255.255.240.0
ip dhcp excluded-add 10.0.16.1 10.0.16.100
ip dhcp pool SHELL.COM
 network 10.0.16.0 255.255.240.0
 default-router 10.0.16.1
 domain-name SHELL.COM
 do sh run | sec dhcp
@A2: 
Int e1/0
 no shut
 switchport mode access
 switch access vlan 22
 DO SH VLAN BRIEF
@P2
config t
int e1/0
no shut
ip add dhcp
do bp

**********FOR fuel save*********************
Config t
vlan 23
name FUELSAVE.COM
Interface vlan 22
 desc FUELSAVE.COM
 no shut
 ip add 10.0.2.0 255.255.254.0
ip dhcp excluded-add 10.0.2.0 10.0.2.101
ip dhcp pool FUELSAVE.COM
 network 10.0.2.0 255.255.254.0
 default-router 10.0.2.1
 domain-name FUELSAVE.COM
 do sh run | sec dhcp

@A2: 
config t
Int e1/0
 no shut
 switchport mode access
 switch access vlan 23
 DO SH VLAN BRIEF
@P2
config t
int e1/0
no shut
ip add dhcp
do bp
