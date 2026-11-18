[Wi-Fi Optimization Lab](#hero) [Link budget](#physics) [Channels](#spectrum) [Coverage lab](#lab) [3D field](#terrain) [Beamforming](#beam) [Airtime](#airtime) [Playbook](#playbook)

Wireless Networking project

# Wi-Fi network optimization

Coverage, capacity and interference pull against each other. This lab lets you work each one by hand: tune a link budget, plan channels, place access points on a floor plan, and watch the signal field respond in 3D.

[Open the coverage lab](#lab) [Start with the physics](#physics)

**−67 dBm**Signal target for voice and video

**25 dB**SNR needed for high-order QAM

**3 channels**Non-overlapping in 2.4 GHz: 1, 6, 11

Part 1

## Link budget: where every dB goes

Received signal is transmit power plus antenna gain, minus path loss. Loss grows with frequency, distance and every wall in the way. The signal-to-noise ratio then picks the modulation (MCS), and the MCS sets the data rate.

Band

Channel width

Transmit power

Antenna gain

Distance

Path loss exponent n

Drywall walls

Concrete walls

Received signal

Noise floor

SNR

MCS

PHY rate, 1 stream

Link quality

RSSI = Ptx + Gant − \[ FSPL(1 m) + 10·n·log10(d) + ΣLwall \] FSPL(1 m) = 20·log10(fMHz) − 27.55\
Noise = −174 + 10·log10(BHz) + NF(7 dB)\
SNR = RSSI − Noise MCS = highest index whose SNR threshold is met

### Reading the result

Every 6 dB of extra loss halves the range. 5 GHz loses about 7 dB more than 2.4 GHz at 1 m and more per wall, which is why it needs more APs but rewards them with far more clean channels. Doubling channel width raises the noise floor by 3 dB, so wide channels need a stronger signal for the same MCS.

### Budget waterfall

Each bar adds or removes dB from the running total.

### Signal vs distance

All three bands with your settings.

2.4 GHz5 GHz6 GHz

Part 2

## Channel planning

Two APs on the same channel take turns, so they split airtime (co-channel interference). Two APs on partly overlapping channels cannot decode each other, so they talk over each other and corrupt frames (adjacent-channel interference). The second case is worse.

### 2.4 GHz spectrum

Pick a channel for each AP and see where their spectral masks collide.

### The channel width trade

Doubling width doubles peak rate but halves the number of clean channels and raises the noise floor 3 dB.

Non-overlapping channelsPeak rate per stream (Mbps)

Dense venues usually stay at 20 to 40 MHz so neighbouring APs can each get their own channel.

Part 3

## Floor-plan coverage lab

A 40 × 25 m office with drywall, glass, brick and concrete. Drag access points, change their channels and power, or let the optimizer search placements with simulated annealing. Coverage, SINR and co-channel conflicts update as you work.

ConcreteBrickDrywallGlass

Band

Show

Area at −67 dBm or better

Dead zones (below −80)

Median SINR

Avg PHY rate, 20 MHz

Co-channel conflicts (same-channel APs that hear each other above −82 dBm)

Model: log-distance path loss with n = 3, 3 dBi antennas, fixed per-wall attenuation per band, light deterministic shadowing, noise floor −94 dBm. Built for illustration, not as a site survey replacement.

Part 4

## The signal field in 3D

The same floor and the same APs from the lab, drawn as a height field. Peaks are strong signal and valleys are dead zones. The translucent plane sits at the service target, so everything above it is good enough for voice and video. Change the lab and this view follows.

Drag to orbit, scroll to zoom

Part 5

## Beamforming and MU-MIMO

An AP with several antennas can delay each one slightly so the waves add up toward a client and cancel elsewhere. Superimpose two sets of delays and the AP serves two clients at the same time (MU-MIMO), each with weak leakage toward the other.

Array gain

Beamwidth

Leakage toward client B

Clients served at once

Antenna elements

Element spacing

Client A angle

Client B angle

### Radiation pattern

Part 6

## Airtime and contention

Wi-Fi is half-duplex and shared. Before sending, each station waits a random backoff (CSMA/CA). As more stations compete, two pick the same slot more often and collide. Wi-Fi 6 OFDMA sidesteps part of this by letting the AP schedule several clients in one transmission.

### Collision probability vs stations

Bianchi model, fixed contention window, saturated stations.

Active stations

Contention window

Collision chance

Airtime efficiency

Per-station share

### Four small packets: OFDM vs OFDMA

Same four 300-byte frames. Legacy Wi-Fi sends them one after another, each paying full overhead. OFDMA splits the channel into resource units and sends them together.

OFDM total**900*µs***

OFDMA total**363*µs***

Speedup**2.5×**

Part 7

## The optimization playbook

Optimization is a loop, not a one-time setting. Measure, design for the hardest client, configure, prove it with a validation survey, then keep watching as the building and the clients change.

#### Survey

Walls, clients, apps and existing RF noise

#### Design

AP count from capacity, not just coverage

#### Configure

Channels, power, width, rates, roaming

#### Validate

Walk the floor: −67 dBm, 25 dB SNR

#### Monitor

Utilization under 50%, retries under 10%

2009

#### Wi-Fi 4

802.11n

- MIMO, up to 4 streams
- 40 MHz channels
- 600 Mbps peak

2013

#### Wi-Fi 5

802.11ac

- 80 and 160 MHz, 5 GHz only
- 256-QAM
- Downlink MU-MIMO

2019 / 2020

#### Wi-Fi 6 / 6E

802.11ax

- OFDMA and uplink MU-MIMO
- BSS coloring, target wake time
- 1024-QAM, 6 GHz band (6E)

2024

#### Wi-Fi 7

802.11be

- 320 MHz channels in 6 GHz
- 4096-QAM
- Multi-link operation (MLO)

IEEE Std 802.11ax-2021, High Efficiency WLAN.

IEEE Std 802.11be-2024, Extremely High Throughput.

G. Bianchi, "Performance analysis of the IEEE 802.11 distributed coordination function," IEEE JSAC, 2000.

T. S. Rappaport, Wireless Communications: Principles and Practice, 2nd ed.

ITU-R P.1238, Propagation data for indoor radio systems.

C. A. Balanis, Antenna Theory: Analysis and Design (array factor).

Wi-Fi Network Optimization Lab. Wireless Networking course project, Stevens Institute of Technology.Prepared by Noor