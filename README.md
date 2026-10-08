# OBD Key Programming Guide

## Purpose
This repository documents authorized automotive locksmith and diagnostics workflows for OBD-based key programming, immobilizer synchronization, and secure access procedures. This is meant for professional locksmiths, vehicle security technicians, and authorized repair workflows on vehicles they own or are legally authorized to service.

## Scope and Safety

- Intended for trained automotive professionals only.
- Work only on vehicles you own or are explicitly authorized to service.
- Follow manufacturer service documentation and approved tooling.
- Use 12V and 5V circuits with caution; shorting CAN/LIN or OBD wiring can damage modules.
- Never bypass security controls on vehicles outside your authorized scope.

## Tooling

- OEM or approved diagnostic scanner
- OBD-II adapter with stable CAN FD / ISO 9141 / KWP2000 support
- Battery maintainer or power supply capable of maintaining 12.5–13.5V
- Key programmer compatible with the target vehicle family
- Transponder / immobilizer recognition tools
- Multimeter and oscilloscope
- Vehicle-specific wiring diagram and service manual

## Safety notes

- Keep battery voltage above 12.5V during programming.
- Ensure ignition is in the correct state as required by the manufacturer.
- Do not connect unsupported wires to OBD or transponder circuits.
- Avoid using low-quality adapters that can create voltage drops or signal noise.
- Disconnect from the internet or IMEI/data services if the manufacturer requires a local-only programming environment.

## Automotive architecture basics

### 1. Immobilizer
The immobilizer prevents unauthorized engine start. It usually consists of:

- ECU / PCM
- BCM or body control unit
- transponder key / RFID signal
- communication bus: CAN, LIN, ISO, or proprietary bus

### 2. Key recognition
Most systems validate a key code against an authorized list stored in the ECU / BCM.

Typical sequence:

- key inserted or proximity signal detected
- transponder/remote ID transmitted
- ECU/BCM compares against stored key IDs
- engine start allowed only when matched

### 3. OBD programming path
Some vehicles allow programming or synchronization through the OBD port using manufacturer-approved sequences, often under:

- key learning / add key
- all keys lost
- immobilizer reset
- ECU synchronization

## Common legitimate procedures

### A. Add key via onboard procedure
Common when an existing working key is present.

Procedure outline:

1. Connect scanner to the OBD port.
2. Confirm battery voltage and ignition state.
3. Select the correct vehicle model and immobilizer menu.
4. Use the manufacturer-specific “Add Key” or “Key Learn” command.
5. Insert the new key as instructed by the tool.
6. Wait for status confirmation.
7. Confirm key recognition by testing ignition and lock functions.

### B. All keys lost
This is an advanced procedure and often requires dealer-level tools or secure manufacturer authorization.

Typical high-level workflow:

1. Verify vehicle and security type.
2. Confirm vehicle configuration and VIN.
3. Use manufacturer-specific equipment or secure programming credentials.
4. Perform key-code generation / synchronization.
5. Clear old key data if the process requires it.
6. Program replacement keys and confirm each one operates.

### C. Synchronization after module replacement
If a BCM, ECU, or steering lock module has been replaced, the system may need immobilizer pairing.

Process usually includes:

1. Vehicle identification and module coding.
2. Read/clear DTCs.
3. Enter immobilizer configuration menu.
4. Synchronize the key list with the control modules.
5. Verify communication between BCM and ECM.

## OBD connection and pin basics

- Pin 16: Battery supply (+12V)
- Pin 4 and 5: chassis and signal ground
- Pins 6 and 14: CAN high and low for many vehicles
- Protocol support depends on model year and manufacturer

Always use the vehicle service manual for the exact pinout because manufacturer layouts vary widely.

## Diagnostic workflow

### Step 1: Identify vehicle and system

Collect:

- VIN
- model year
- body type
- engine and transmission
- key type (mechanical, transponder, smart key, remote fob)
- immobilizer generation

### Step 2: Confirm battery and power quality

- Battery should be stable and fully charged.
- No voltage drop under load
- Use a maintained power source if required

### Step 3: Read fault codes

Look for:

- immobilizer errors
- key code mismatch
- BCM / ECM communication faults
- transponder errors
- steering lock faults

### Step 4: Check key state

- Mechanical wear
- transponder resonance or coding issues
- battery in remote fob
- key ID mismatch

### Step 5: Use manufacturer process

- Key registration
- remote pairing
- immobilizer learning
- module coding and calibration

### Step 6: Validate end-to-end

- Start engine
- lock/unlock functions
- panic mode / trunk release if present
- remote range and signal quality

## Example workflow template

```text
Vehicle: 2018 VW Golf
System: BCM + immobilizer
Tools: approved scanner, battery maintainer, key programmer
Sequence:
1. Verify VIN and key count.
2. Connect battery maintainer.
3. Read DTCs.
4. Check current key list in BCM.
5. Use authorized key programming function.
6. Add new key.
7. Re-synchronize with ECM.
8. Validate all keys start vehicle.
```

## Common documentation points for a locksmith job sheet

- VIN and registration
authorized locksmith or technician name
- reason for programming
- number of keys before and after
- scanner model / software version
- key part numbers and transponder IDs
- battery voltage during procedure
- any DTCs cleared or reproduced
- final validation result

## Threat model and legal considerations

- Unauthorized cloning or bypass is outside the scope of this guide.
- This repository does not provide methods for defeating manufacturer security or creating unauthorized keys.
- Use only approved OEM or professional tools and authenticated manufacturer procedures.
- Keep logs and proof of authorization for all key programming jobs.

## Recommended reading list

- Manufacturer-specific service manuals
- OEM key programming procedures
- approved locksmith training materials
- CAN / LIN / OBD protocol documentation from official service documentation

## Example tables

### Common OBD protocols

| Protocol | Typical usage | Notes |
| --- | --- | --- |
| ISO 9141-2 | older European vehicles | slower, low-speed serial |
| KWP2000 | many European vehicles | common for diagnostics |
| CAN | modern vehicles | widely used for ECUs and BCM |
| LIN | local modules | often in door modules and seat nodes |
| J1850 VPW / PWM | older GM/Ford applications | mostly legacy |

### Safe voltage guidance

| Condition | Voltage |
| --- | --- |
| Healthy battery resting | 12.6–12.8V |
| Charging | 13.5–14.5V |
| Programming minimum | 12.5V+ |
| Unsafe for sensitive programming | below 12.0V |

## Appendix: clean workflow checklist

- [ ] Confirm legal authorization and vehicle ownership
- [ ] Verify VIN and vehicle year/model
- [ ] Measure battery voltage
- [ ] Read current DTCs
- [ ] Confirm OEM tool compatibility
- [ ] Complete manufacturer sequence
- [ ] Validate all keys and remote functions
- [ ] Record service logs and final status

## Final note

This guide is a technical reference for professional, authorized vehicle security work. It does not provide unauthorized access or bypass techniques. Use each procedure exactly as manufacturer-approved.
