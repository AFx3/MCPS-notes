- Wireless: communication over wireless link (hops,user devices, BS)
- Mobility: handling the mobile user who canges point of attachment to network, mobile phone operators provide connection service allowing you to move, identity, authentication (if id user € their registry), of course billing

### Cellular Network Architecture Components:

- ![fig.1](./Immagini/mobNetArch.png)
- MSC other features:
	- can hadle multiple cell
	- hidden frame 
	- manage the handoff
	- some as gateway to public telefone network
	- identity, auth, trace devices, billing, trace time user connection

## Evolution of mobile network technologies

- ![fig.2](./Immagini/evolutonMobileNet.png)

- 1G: 
	- 1st gen
	- communication over analog signals
	- frequency
	- multiplexing:
		- method by which multiple (analog or digital) signals are combined into one signal over a shared medium
	- no digital signal
- 2G:
	- GSM
	- voice communication
	- digital signals
	- text messaging (SMS success wasn't expected)
- 3G:
	- 1st revolution
	- data communication and anternet connection
	- high data rate
- 4G:
	- extension of 3G architecture
- 5G: 
	- 5G have (also in 4G really) software engineering principles (microservices, virtualisation, impact of data centers)
	- low latency

### Cellular netwoks: the first hop
- two techniques for sharing mobile to BS radio spectrum
-
1. **combined FDMA/TDMA**:
	- divide spectrum in frequency channels, divide each channel into time slots
	- informal:
		- each frequency band is divided in time slots
		- assign each intersection to a device

- ![fig.3](./Immagini/cellNet1stHopA.png)

1. **CDMA**: Code Division Multiple Access:
	- division by codes: sequences of bits
	- partitioning the code space
	- code is negotiated before by BS according to decision provided by functions of the architecture (multiple codes)
	- specific code for each node transmitting
- ![fig.4](./Immagini/cellNet1stHopB.png)
- Sendig station send d1 and d0, so Z= di * Cm is the output of the station
- Receiving station decode signal and reconstruct appling di
- simple situation, real scenario has multiple trnsmitters and 1 receiver
- since receiver knows code used from transmitting, is amble to reconstruct original signal
	- even if the sum of many singals send

### 2G(voice) network architecture

- ![fig.5](./Immagini/2gArchitecture.png)

- X : circut switching implementation
- Gateway MSC (Mobile Switching Center):
	- mediate communication mobile <-> public telefone network
- MSC (Mobile Switching Cenrer):
	- infos of authenticated user, subscribe
- BSC (Base Station Controller): 
	- decides on how resources of phisical medium are used/managed
	- control/manage different BS
	- infos about medium devices
- BSS (Base Station System):
	- set of BS
	- awared on wich code is used 
	- infos about medium device

### 3G (voice + data) Network architecture
- ![fig.6](./Immagini/3G.png)
- Not only voice, also implement connection to core network
- **infrastucture extension, change anything**
- GGSN (Gateway GPRS Support Node) and SGSN (Serving GPRS Support Node) are two core network nodes in 2G GSM and 3G UMTS networks that enable packet-switched mobile internet. GGSN and SGSN were added to GSM networks as part of the GPRS enhancement, and they are used by both GSM and 3G UMTS networks.**
- **Radio Network Controller**:
	- this shit is introduced: 
		- circuit switching **to handle datagram and voice**
- Gateway **SGSN**: 
	- router, cuz deling with packets
- Gateway **GGSN**:
	- gateway, last router near public internet
- Gateway MSC:
	- parallel branches