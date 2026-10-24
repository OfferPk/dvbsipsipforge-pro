# DVBSIPSIPForge Pro (v1.0.0)

### DVB-SI (ETSI EN 300 468), MPEG-2 PSI & ATSC PSIP (A/65) Metadata Studio

---

## Overview

**DVBSIPSIPForge Pro** is a broadcast engineering utility and command-line tool built for digital television multiplex operators, terrestrial DVB-T2 network providers, satellite uplink engineers, and headend equipment developers. It provides bit-accurate table synthesis, section dissection, MPEG-2 CRC-32 verification, and 10-point normative compliance auditing across:

- **ETSI EN 300 468**: Specification for Service Information (SI) in DVB Systems  
- **ISO/IEC 13818-1**: MPEG-2 Transport Stream Program Specific Information (PSI)  
- **ETSI TR 101 211**: DVB-SI Implementation Guidelines & Carousel Timing  
- **ATSC A/65**: Program and System Information Protocol (PSIP)

---

## Key Capabilities

1. **Multiplex Table Synthesizer**:  
   - Generates Program Association Tables (PAT: `0x00`, PID `0x0000`).  
   - Generates Service Description Tables (SDT: `0x42`, PID `0x0011`) with embedded `service_descriptor` (tag `0x48`).  
   - Computes normative MPEG-2 CRC-32 checksums (`0x04C11DB7`).  
2. **Binary Section Dissector**:  
   - Dissects arbitrary MPEG-2 PSI / DVB-SI hexadecimal byte streams.  
   - Validates section length boundaries and CRC-32 integrity.  
3. **EPG & Channel Lineup Inspector**:  
   - Visualizes channel names, providers, service IDs, and running status.  
4. **10-Point Normative Compliance Auditor**:  
   - Automated checks for table IDs, CRC polynomials, section length limits, ONID/TSID allocation, and carousel repetition budgets.  
5. **Standalone Python CLI (`dvb-cli.py`)**:  
   - Headless table generation and packet inspection for automated broadcast playout CI/CD pipelines.

---

## Getting Started

### Web Studio

Open `source-code/index.html` in any web browser. Runs 100% locally with zero external network dependencies.

### Command-Line Interface

\# Generate PAT table

python3 build/dvb-cli.py pat \--tsid 1 \--prog 101 \--pmt 0x0100

\# Generate SDT table

python3 build/dvb-cli.py sdt \--tsid 1 \--onid 8442 \--sid 101 \--provider "BBC" \--name "BBC ONE HD"

\# Decode section hex

python3 build/dvb-cli.py decode "42f0260001c1000020fa..."

### Automated Testing

python3 test\_dvb.py