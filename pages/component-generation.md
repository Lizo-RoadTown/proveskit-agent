---
layout: article
title: Component Generation
permalink: /component-generation/
key: page-component-generation
---

# F'Prime Component Generation

The Component Generator agent creates F'Prime components from natural language specifications.

---

## How It Works

### Input: Natural Language Requirements

**Example 1: Simple sensor**
> "Temperature sensor component that reads ADC every 10 seconds and reports telemetry."

**Example 2: Complex payload controller**
> "Payload controller with commands to power on/off subsystems, telemetry for voltage/current monitoring, events for fault detection, and parameters for configurable thresholds."

**Example 3: Data handler**
> "Data buffer component that receives packets from radio, stores in ring buffer, and forwards to ground station on request. Include command to flush buffer and event when buffer fills."

### Output: Complete Component Package

For each component, the agent generates:

1. **`.fpp` component definition**
2. **C++ implementation scaffold**
3. **Unit test framework**
4. **Component documentation**

---

## Component Elements

### Ports

**Auto-generated based on requirements:**

```fpp
active component PayloadController {
  # Async command port (auto-generated)
  async command port cmdIn

  # Telemetry output (auto-generated)
  telemetry port tlmOut

  # Event output (auto-generated)
  event port eventOut

  # Custom ports (from requirements)
  output port powerControl: PowerControl
  async input port dataIn: SerialData
}
```

**Agent identifies:**
- Required standard ports (command, telemetry, event)
- Custom ports from functional requirements
- Port direction (input/output)
- Port synchronicity (sync/async)

### Commands

**Extracted from requirement verbs:**

> "Commands to power on/off subsystems"

**Generates:**

```fpp
async command PowerOn(
  subsystem: U8 @< Subsystem ID (0-7)
) opcode 0x10

async command PowerOff(
  subsystem: U8 @< Subsystem ID (0-7)
) opcode 0x11
```

**Agent determines:**
- Command parameters and types
- Descriptions and annotations
- Synchronicity (async for most commands)
- Opcode assignment

### Telemetry

**Identified from monitoring requirements:**

> "Telemetry for voltage/current monitoring"

**Generates:**

```fpp
telemetry Voltage: F32 \
  format "{.2f} V" \
  update on change

telemetry Current: F32 \
  format "{.2f} A" \
  update on change

telemetry PowerStatus: U8 \
  format "{} (0=Off, 1=On)" \
  update always
```

**Agent specifies:**
- Channel types
- Formatting strings
- Update policies
- Units and ranges

### Events

**Derived from state changes and faults:**

> "Events for fault detection"

**Generates:**

```fpp
event VoltageOutOfRange(
  voltage: F32 @< Measured voltage
  threshold: F32 @< Expected threshold
) severity warning high \
  format "Voltage {.2f}V exceeds threshold {.2f}V"

event PowerSystemFault(
  subsystem: U8 @< Failed subsystem ID
  errorCode: U32 @< Fault code
) severity fatal \
  format "Subsystem {} fault: 0x{x}"
```

**Agent determines:**
- Event parameters
- Severity levels
- Format strings
- When events should fire

### Parameters

**Extracted from configuration needs:**

> "Parameters for configurable thresholds"

**Generates:**

```fpp
param VoltageMin: F32 \
  default 3.0 \
  id 0x100

param VoltageMax: F32 \
  default 5.0 \
  id 0x101

param SamplingPeriod: U32 \
  default 10 \
  id 0x102
```

---

## C++ Implementation

### Generated Scaffold

**TempSensor.cpp:**

```cpp
#include "TempSensor.hpp"

namespace Components {

  // Constructor
  TempSensor::TempSensor(const char* name) :
    TempSensorComponentBase(name)
  {
  }

  // Initialize
  void TempSensor::init(NATIVE_INT_TYPE instance)
  {
    TempSensorComponentBase::init(instance);
  }

  // Command handlers
  void TempSensor::ReadTemperature_cmdHandler(
    FwOpcodeType opCode,
    U32 cmdSeq
  )
  {
    // TODO: Implement temperature reading
    // 1. Read from ADC
    // 2. Convert to temperature
    // 3. Emit telemetry
    // 4. Check thresholds
    // 5. Send command response

    this->cmdResponse_out(opCode, cmdSeq, Fw::CmdResponse::OK);
  }

  // TODO: Implement other handlers
}
```

**Agent provides:**
- Proper inheritance from auto-generated base
- Handler signatures matching FPP
- TODO comments with implementation guidance
- Command response patterns

### Thread Safety

For **active components**, agent includes:

```cpp
// Thread-safe telemetry update
void TempSensor::updateTelemetry(F32 temp)
{
  this->lock();
  this->tlmWrite_Temperature(temp);
  this->unlock();
}
```

For **passive components**, no locking needed.

---

## Unit Tests

### Test Framework

**TempSensorTest.cpp:**

```cpp
#include "TempSensorTester.hpp"

TEST(TempSensorTest, NominalReading) {
  Components::TempSensorTester tester;
  tester.connectPorts();

  // Send ReadTemperature command
  tester.sendCmd_ReadTemperature(0, 0);
  tester.component.doDispatch();

  // Verify command response
  ASSERT_CMD_RESPONSE(0, TempSensor::OPCODE_READTEMPERATURE, 0,
                      Fw::CmdResponse::OK);

  // Verify telemetry emitted
  ASSERT_TLM_SIZE(1);
  ASSERT_TLM_Temperature_SIZE(1);
}

TEST(TempSensorTest, ThresholdAlert) {
  // TODO: Test temperature threshold event
}

TEST(TempSensorTest, InvalidCommand) {
  // TODO: Test error handling
}
```

**Agent generates:**
- Test fixture setup
- Port connections
- Nominal case tests
- TODO markers for additional tests

---

## Component Types

### Active Components

**When to use:**
- Has its own thread
- Processes async commands
- Runs periodic tasks

**Agent generates:**
- Async command handlers
- Message queue configuration
- Thread management

**Example:**
```fpp
active component TelemetryManager {
  async command port cmdIn
  # Agent adds thread config
}
```

### Passive Components

**When to use:**
- Called by other components
- No independent thread
- Pure functions/state

**Agent generates:**
- Sync handlers only
- No threading code

**Example:**
```fpp
passive component CRC32 {
  sync input port dataIn: SerialData
  # No threading needed
}
```

### Queued Components

**When to use:**
- Needs message queue
- No dedicated thread
- Driven by active component

**Agent identifies need from requirements.**

---

## Advanced Features

### State Machines

**Requirement:**
> "Component cycles through IDLE → ARMED → ACTIVE states with commands to transition."

**Agent generates:**
- Enum for states
- State variable in component
- Commands that trigger transitions
- Events on state changes
- State checking in handlers

### Data Buffers

**Requirement:**
> "Ring buffer for storing up to 100 data packets."

**Agent includes:**
- Buffer data structure
- Overflow handling
- Clear/flush commands
- Buffer status telemetry

### Timers

**Requirement:**
> "Sample temperature every 5 seconds."

**Agent adds:**
- Timer port connection
- Timer registration in init
- Timer expiry handler
- Configurable period parameter

---

## Validation

### Agent Self-Check

Before returning generated component:

1. **FPP syntax check** — Run `fpp-check`
2. **Port consistency** — Verify all ports connected in impl
3. **Handler completeness** — All commands/ports have handlers
4. **Documentation** — All elements have descriptions

### User Review Checklist

After receiving generated component:

- [ ] Requirements match generated interfaces
- [ ] Command parameters make sense
- [ ] Telemetry covers all states
- [ ] Events have appropriate severity
- [ ] TODO comments are clear
- [ ] Tests cover key scenarios

---

## Limitations

**Agent cannot:**
- Implement hardware-specific code (BSP, drivers)
- Design complex algorithms (must provide pseudocode)
- Determine optimal thread allocation
- Validate flight safety requirements

**Agent helps with:**
- Boilerplate F'Prime code
- Interface definitions
- Documentation structure
- Test scaffolding

**Human must:**
- Review all generated code
- Implement business logic
- Validate against requirements
- Perform integration testing

---

## Examples

### Example 1: GPS Receiver

**Input:**
> "GPS receiver component that reads NMEA sentences over UART, parses position data, emits telemetry for lat/lon/altitude, and raises event when fix is lost."

**Generated:**
- `GpsReceiver.fpp` with UART port, telemetry channels, events
- C++ with NMEA parsing TODO
- Tests for valid/invalid sentences
- ICD with telemetry table

### Example 2: Attitude Controller

**Input:**
> "Attitude determination component that reads gyro/magnetometer, estimates orientation quaternion, provides telemetry for Euler angles, has parameter for filter gain."

**Generated:**
- `AttitudeDetermination.fpp` with sensor ports, quaternion telemetry, parameters
- C++ with filter algorithm TODO
- Tests for sensor data processing
- Documentation for interface

### Example 3: File Downlink Manager

**Input:**
> "File manager that receives file chunks, assembles complete file, writes to filesystem, and responds with checksum. Include commands for start/cancel transfer."

**Generated:**
- `FileDownlink.fpp` with data port, commands, file I/O events
- C++ with file assembly logic TODO
- Tests for chunk ordering and errors
- Documentation for transfer protocol

---

## Next Steps

- Try generating your first component: [For Developers →](/proveskit-agent/developers/)
- Understand the technical details: [Architecture →](/proveskit-agent/technical/)
- See documentation capabilities: [Documentation Support →](/proveskit-agent/documentation/)
