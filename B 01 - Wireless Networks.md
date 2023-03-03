### Why wireless networks?
- need cables in computer to 
	- communicate: strasfer data between nodes
	- provide power: between devices
- Cyber-physical systems embed computers in physical objects 
	- they're everywere: free placement, mobility, exposed to the wild -> go wireless (can't wire everything)
	- hence: wireless to replace cable in communications and batteries to replace cables in power supply

### Wireless networks
- network of **hosts** connected by **wireless links**
	- **hosts**: end-system devices that runs apps
		- mobile (often, but not necessary)
		- battery-powered (typycally)
- 2 modes of operaiotions
	1. **infrastructure**: BS(base stations) || wired access points
	2. **ad hoc networking**: no centralised coordinatiors (that coordinate shared medium), links connected wired
- **elements of wireless network**
	- ![fig.1](./Immagini/elementsWirelessNet.png) 
	- **wireless hosts**: 
		- run applicatins
		- stationary (fixed location), wireless not always mean mobility || mobile
		- devices want to communicate to internet -> traverse internet
		- are connected wireless to BS
	- **base stations**:
		- cover geographic areas
		- all communications to devices travese BS
		- manage resource of phisical medium
		- connected to a wired network
		- *relay*: responsible to send packets between wired ntwrk and wireless hosts (in its area)
		- e.g.:acess points(in wi-fi)/cell towers (in mobile phone)...
		- problem to solve for acess poibts: new accesses, coordinatin medium, oving devices
	- **wireless links**:
		- connect mobile to base stations
		- *Multiple Aceess Protocol* to coordinates *link access*
		- various *data rates*, *trasmission range*
	- **infrastructure mode** (network infrastructure):
		- BS connects mobiles into wired network
		- problem: nodes can move between BSs -> exchainging **control message**: connection doesn't terminate -> **change of responibility**
			- devices can move between BS of different/same **providers**: 
				- they provide authentication, billing
	- **intracell communication**: two hosts (end devices) communicates inside  the same BS's area
	- **intercell communication**: two hosts communicates through differente BS's areas

### wireless network taxonomity

- ![Fig.2](./Immagini/wirelessNetTaxonomity.png)

### Wireless links (chatateristics) vs wired links
- electromagnetic waves in the air (tonight, oh  lord, I can feel it comin' in the air tonigh, Phil Collins)
- **decresed signal strenght**: 
	- problem
	- signal decreases with lenght
	- radio signal attenuates as it propagates thru matter
		- obstacols can block electromagnetic waves
- **interference with other sources**: 
	- standardized wireless network frequency shared by other devices (e.g.: 2,4Ghz)
	- microwaves ownes, mobile phones, engince, appliances may *interference as well
	- receivers detect the sum of signal in the environment 
- **multipath propagation***: 
	- radio signal (electro waves )reflect on objects or ground, arriving at destination at different times

### Wireless tools
- **SNR**: signal to noise ratio -> evaluate *quality of the signal*
	- SNR = (*signal power*/*noise power)*
		- id est(meaningful input/meaningless or unwanted input(power of background noise)) such that 0 < SNR < +infinty, (watt or dBm)
		- SRN in dB (10th part of bel (B symbol): 10 dB=1B, logaritmic unit ratio over two homogeneous quantities) = 20 * log(signal/noise)
	- larger is SNR -> easier is to esxtract signal form noise (cool thing)
- **BER**: Bit Error Rate: probability taht a trasmitted bit is received in error at the reciver
- **SNR** vs **BER** tradeoff: how implicit is information in electro waves
	- given a phisical layer: increase power -> increase SNR(quality of the signal) -> decrease BER (send bits -> electro waves to the medium)
- **given SNR**: choose a physucal layer that meets BER requirement, **giving highest throughput**
- **SNR** may chainge with *mobility*:
	- dynamically adapt physical layer (modulation tecnique)
	- ![Fig.3](./Immagini/SNRvsBER.png)
	- also *signal attenuation* or *obstacles* **limit transmission range** 

### Wireless network challenges
1. **Limited knoweledge**: 
	- a node detect a situation, but not all communications
	- a terminal cannot hear all the other
	- hidden/exposed terminal problem
2. **Mobility/failure of terminals**:
	- terminals move (join/exit) in the range of different BS
	- terminals move away from each other
1. **Limited terminals**:
	- battery life, memory, processing, trasmission range
2. **Privacy**:
	- eavesdropping of ongoin communications

### Wireless network required mechanism
1. **Access** to a shared wireless channel
	- CSMA/CD (Carrier Sense Multiple Accesses with Collision Detection) multi access protocol CANNOT be used.
1. **Hand-off** ("goin' away")(network with infrastructure):
	- moving terminal into range of different BS
2. **Routing** (multi-hop ad hoc networks)
	- finding a path form **source** to **destination** in multi-hops networks
	- deling with arbitrary changes in neighborhood

### Wireless networks protocol stack
- | bits | frames | packets | segments | data |
- ![Fig.4](./Immagini/wirelessStack.png) 

### Recap: MAC protocol for wired networks
- a single channel availble for **all** the communications
- **all** stations can transmit and send on the channel
- if frames are sent simoultanesly on the channel 
	- -> resulting signal is **garbled** (**a collision occurs***)
- CSMA, CSMA/CD, ALHOA, slotted ALOHA

### CSMA 
- Carrier Sense Multiple Accesses 
- when a station has a frame to send -> listen to the channel to see if anyone else is trasmitting
- if channel is busy -> station waits untill it becomes idle
- when channel il idle -> station stransmits the frame
- if a collision occurs -> station waits a random amount of time and repeats
- 
- ![Fig.5](Immagini/csmaCD.png) 

### CSMA/CD
- a station aborts its trasmission as soon as it detects a collision
	- if two stations sense channel idle at the same time and start transmitting
		- -> stations quickly abort the frame as soon as collision is detected
- wudely used in LANs in MAC sub-layer
- IEEE 802.3
- **T** is the time required to reach the farthest station
- it takes minimum RTT (# time between sending/reciving the signal) (2 * T) to detect collision

### Binary Exponential Backoff
- defines time that station has to wait for trasmitting again a frame
- algorithm:
- time after a collision is divided in **contention slots**:
	- lenght of a contention slot is equal to the worst case round propagation time (2T if T time to reach farthest station)
- after 1st collision:
	- each station waits 0 or 1 slot before trying again (success or collision)
- after collision **i**:
	- choose x at random in (0, 2^**i** -1) -> exp:more collision, more time, may increase exponentially
- after 10 collisions:
	- choose x at random in a frozen interva (0..1023)
- after 16 collisions:
	- failure is reported back to upper levels

### Why MAC doesn't work on wireless
- station transmit and send if there is another communication in channel -> multiple antennas
- ![Fig.6](./Immagini/macWireless.png)

### Hidden terminal problem
- two or more stations which are out of the range of each other transmit simultaneously to a comme recipient

- ![Fig.7](./Immagini/hidden1.png)
- ![fig.8](./Immagini/hidden2.png)


### Exposed terminal problem
- a trasmitting station is prevent from sending frames due to interference with another transmitting station
- ![Fig.8](./Immagini/exposed1.png)
- - ![Fig.9](./Immagini/exposed2.png)

- so:
 ![FIg.10](./Immagini/recap.png)

### MACA protocol
- Multiple Accesses with Collision Avoidance:
	- stimulate the receiver into trasmittig to it a short frame first by sender 
		- RTS: Request To Send, includes length of the longer frame
	- if the station receiver wants to recive the message, replies with another frame
		- CTS: Clear To Send short frame with data lenght copied from RTS frame
	- then transmit a (long data frame)
	-  stations hearing the short frame **refrain from transmitting** during the transmission of the subsequent data frame
- collision:
- ![FIg.11](./Immagini/MACAcollision.png)
	- the two messages collinde: **no CTS generated** 
	- C and B uses ***Binary exponential backoff*** (same as ethernet) to retry RTS

### MACAW: MACA for Wireless network

- ![Fig.12](./Immagini/MACAW.png) 

### IEEE 802.11

- IEEE 802.11 (Legacy mode, 1st version)
	- relased in '97, clarified in '99
	- rarely used today -> evolving in a/b/g/n (theese most used today)
	- **data rate**: started with 1.2 Mbps *data rate* implemented via:
		- infrared signals (IR)
	- **radio frequencies** in the 2.4 Ghz band (Industral Scientific Medical Freq.)
	- many **degrees** of freedom:
	- **interoperability** among different productos was challenging
	- became popular with version 802.11b

- IEEE 802.11**a**
	- '99
	- **operating (radio) frequency**: 5 Ghz band
	- **throughput**(typ): 23 Mbps 
	- **data rate**(max): 54 Mbps
		- - lot of difference, exploit max transmission capacity of technologies
- IEEE 802.11.**b**
	- '99
	- **operating (radio) frequency**: 2,4 Ghz band (ISM band)
		- problem: in some environments (domestic) interference (microwave owens, cordless tel)
	- **throughput** (typ): 4.3 Mbps (<A)
	- **data rate** (max): 11 Mbps
- IEEE 802.11**g**
	- 2003
	- **operating (radio) frequency**: 2,4 Ghz band (SM)
	- **throughput**(typ): 19 Mbps and more (>B)
	- **data rate**(max): 54 Mbps
- IEEE 802.11**n**
	- 2009
	- **operating (radio) frequency**: 2,4 Ghz  and 5 Ghz band 
	- **throughput**(typ): 74 Mbps and more (>G)
	- **data rate**(max): 248 Mbps
	- supports MIMO tecnhologies:
		- a node can use multiple antennas at the transmitter/reciver
- Wi-Fi 5 - IEEE 802.11**ac**
	- 2013
	- **operating (radio) frequency**: 2,4 Ghz  and 5 Ghz band
	- **data rate** (max):
		- at **5 Ghz**: 1.3 Gbps
		- at **2.4 Ghz**: 450 Gbps
- Wi-Fi 6 IEEE 802.11**ax**
	- 2019
	- **data rate**: reaches up 10 Gbps
	- improvements
		- power consumption and security
		-
- IEEE 802.11 Wireless LAN
- ![Fig.13](./Immagini/wirelessLAN.png) 
- 802.11 **af-ah**:
	- sendind data for measurement
	- **low frequency** -> **higher range** (higher coverage)
		- cool for IoT: sensor in fields need coverage
- 802.11 stack
	- all theese protocols are at L2 (phiscal, frame shit)
		- differen releases -> different implementations
		- MAC and logically controls
		- 
### 802.11 Architecture
- a group of stations (AP) has **coordination funcition** 
	- to transmit data send/rec
- AC can be used in between nodes/other AC (link)/group of stations via fixed infrastructure
	- if using AP, a station communicates with another 
		- challenging all traffic thru a centralised AP
- may or not use a BS
- supports **ad hoc** network (no infrastructure):
	- a group of stations that are under the direct control of a single channel coordination function, without the aid of an infrastructure network
	- no centralised role of AP
	- distributed aming nodes belong ad hoc network
- a station can communicate directly with another without channelling all trafic thu AP
- spectrum diveded into channels at different frequencies
	- -> range of frequency divided in # of channels (usually 11)
	- -> AP admin choose frequency for AP
	- -> AP communicate thru channel using that frequency with the device
	- interference possible: channal can be the same as that choose by neighboring AP
- a node join to a network must associate with AP
	- scans channels
	- listen for beacon frames
		- containing SSID(net name) && (BSSID) MAC of the AP
		- host selects AP to associate with
		- they can perform auth
		- typically they run DHCP to get IO address in P's subnet

### Scanning
- host want to join the network
	- must discober infos abot AC to join to the network

- **passive scanning** 
	- ![Fig.14](./Immagini/passiveScanning.png)
		1. beacon frames sent from APs
			- AC periodically sends beacon frames
		2. association **request** frame sent:
			- H1 to select AC (based on BSSID)
			- choosing the AP according higher signal strength (depends on vendor implementation really)
		3. association **response** frame sent from AP to H1
- **active scanning**
	- ![Fig.15](./Immagini/activeScanning.png)
		- a node arrives in network -> send beacon -> want the reply to an AP
		1. Probe **request** frame broadcast from H1
		2. probe **response** frames sent from APs
		3. **association request** frame sent:
			- H1 to selected AP
		4. **Association response** frame sent:
			1. from selected AP to H1
		- *association request* and *association response* nedeed cuz can have multiple AP, but not aware if AP resplies
### MAC Sublayer

- ![Fig.16](./Immagini/macSublayer.png)
	- DCF: Distributed Coordination Function, here implements MACA -> distributed access to shared medium
		- completey decentred
		- thought for best effort asynchronous traffic
		- **must be implemented by all stations**
	- ![Fig.17](./Immagini/dcf.png)
	- Carrier sensing is performed at two levels:
		- *phisical CS*: 
			- informal: before trasmission if another station is transmitting -> detect incoming signal -> if channel is free -> transmit 
			- formal: 
				- checking the frequency to determine wheteher the medium is in use or not
				- phisical carrier sense to detect incoming signal
				- detects any activity in the channel due to other sources
		- *virtual CS*:
			- performed sending duration information in the headr of an RTS, CTS and data frame
			- keep channel virtually bused up to the end of frame transmission
			- a channel is marked busy if either the physical or the virtual CS indicate busy
		- a channel is marked busy if either the physical or the virtual CS indicate busy
	- always about coordinatin function:
		- priority access to the medium is controlle thru the use of **interframe space** (IFS) time interval: min time need to wait to send new frame (time between 2 frames)
			- formal IFS: mandatory periods of idle time on the transmission medium
		- Three IFS specified by stamdard (always talking about IEEE 802.11)
			1. Short IFS (SIFS)
			2. Point Coordination Function IFS (PIFS)
			3. Distributed Coordination Function (DIFS)
			- SIFS < PIFS < DIFS
			- stations only require to wait SIFS have the higher priority:
				- node with highet priority wait less the others with smaller one

	- PCF: Point Coordination Function: access medium between nodes to organise communication service
		- contention free
		- uses BS to control all activity in its cell
		- though for delay-sensitive traffic
		- AP pools station for transmissions
		- based on DCF
	- **DCF || PCF can be active at same time in same cell**

- MANCA ULTIMA SLIDE