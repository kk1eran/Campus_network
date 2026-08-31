# Campus Network
Network design and architecture for a school campus.

continues documentation by date

PHASE 1

Firs thing to do is the physical cabling. Assign roles to each devices
Connections

NOC Systems - 
  SW6 - switch for that network
  SW6 -> (Fa0/1 - switch port) -> IP phone -> (PC port - F/0) -> PC18
  SW6 -> (Fa0/2 - Fa0) -> PC17

LAB ROOM
  SW6 - switch for that network
  SW6 -> (Fa0/1 - Fa0) -> PC12
  SW6 -> (Fa0/2 - Fa0) -> PC13
  SW6 -> (Fa0/3 - Fa0) -> PC14
  SW6 -> (Fa0/4 - Fa0) -> PC15
  SW6 -> (Fa0/5 - Fa0) -> PC16

IS Office
  SW3 -> (Fa0/1 - switch port) -> IP phone -> (PC port - Fa0) -> PC9
  SW3 -> (Fa0/2 - Fa0) -> PC10
  SW3 -> (Fa0/3 - Fa0) -> PC11
  SW3 -> (Fa0/4 - Port 0) -> Access Point

LOBBY
  SW5 -> (Fa0/1 - Port 0) -> Access Point -> Cellphones or Laptop

CS Office
  SW2 -> (Fa0/1 - switch port) -> IP phone 2 -> (PC port - Fa0) -> PC6
  SW2 -> (Fa0/2 - Fa0) -> PC7
  SW2 -> (Fa0/3 - Fa0) -> PC8
  SW2 -> (Fa0/4 - Port 0) -> Access Point 2

IT Office
  SW2 -> (Fa0/1 - switch port) -> IP phone 2 -> (PC port - Fa0) -> PC6
  SW2 -> (Fa0/2 - Fa0) -> PC4
  SW2 -> (Fa0/3 - Fa0) -> PC3
  SW2 -> (Fa0/4 - Port 0) -> Access Point 1

  SERVER ROOM
    SW0 -> (Fa0/1 - Fa0) -> Server0
    SW0 -> (Fa0/2 - Fa0) -> Server1

MLS0
switches connected to MLS0

  SW0 -> (Fa0/3 - Fa0/1) -> MLS0
  SW1 -> (Fa0/5 - Fa0/2) -> MLS0
  SW2 -> (Fa0/5 - Fa0/3) -> MLS0
  SW5 -> (Fa0/2 - Fa0/4) -> MLS0
routers
  Router0 -> (Gig0/0/0 - G0/1) -> MLS0

MLS0 <-> (G0/2 - G0/2) <-> MLS1

MLS1
switches connected to MLS1
  SW6 -> (Fa0/3 - Fa0/1) -> MLS1
  SW4 -> (Fa0/6 - Fa0/2) -> MLS1
  SW3 -> (Fa0/5 - Fa0/3) -> MLS1
routers
  Router1 -> (Gig0/0/0 - G0/1) -> MLS1

31/08/2026

AP4
  Smartphone -> (wireless connection) -> Access Point 4
  Laptop -> (wireless connection) -> Access Point 4

No shutdown Router0 and Router1 interface
  interface g0/0/0
  no shutdown

initial switch configuration 
vlan configuration 
PC IP addressing
  
PHASE 2
trunking a

Switch Configuration
Also applied vlan name

  SW0 (Server)
    interface Fa0/3
    switchport mode trunk
    switchport trunk native vlan 99
    switchport trunk allowed vlan 10, 60, 99
    no shutdown
    exit
    vlan 10
    name MANAGEMENT
    vlan 60
    name Server
    vlan 99
    name Native
    
  SW1 (IT)
    interface Fa0/5
    switchport mode trunk
    switchport trunk native vlan 99
    switchport trunk allowed vlan 10,50,80,99
    no shutdown
    exit
    vlan 10
    name MANAGEMENT
    vlan 50
    name IT_Office
    vlan 80
    name VOICE
    vlan 99
    name Native

  SW2 (CS)
    interface Fa0/5
    switchport mode trunk
    switchport trunk native vlan 99
    switchport trunk allowed vlan 10,30,80,99
    no shutdown
    exit
    vlan 10
    name MANAGEMENT
    vlan 50
    name IT_Office
    vlan 80
    name VOICE
    vlan 99
    name Native

  SW5 (Lobby)
    interface Fa0/2
    switchport mode trunk
    switchport trunk native vlan 99
    switchport trunk allowed vlan 10,20,99
    no shutdown
    exit
    vlan 10
    name MANAGEMENT
    vlan 20
    name Student
    vlan 99
    name Native

  SW6 (NOC)
    interface Fa0/3
    switchport mode trunk
    switchport trunk native vlan 99
    switchport trunk allowed vlan 10,70,80,99
    no shutdown
    exit
    vlan 10
    name MANAGEMENT
    vlan 70
    name NOC_System
    vlan 80
    name VOICE
    vlan 99
    name Native

  SW4 (Lobby)
    interface Fa0/5
    switchport mode trunk
    switchport trunk native vlan 99
    switchport trunk allowed vlan 10,20,99
    no shutdown
    exit
    vlan 10
    name MANAGEMENT
    vlan 20
    name Student
    vlan 99
    name Native

  SW3 (IS)
    interface Fa0/5
    switchport mode trunk
    switchport trunk native vlan 99
    switchport trunk allowed vlan 10,70,80,99
    no shutdown
    exit
    vlan 10
    name MANAGEMENT
    vlan 40
    name IS_Office
    vlan 80
    name VOICE
    vlan 99
    name Native

switch trunking is done next is MLS configuration.
  
  
    
    
      
  
  
  

  
  
  
