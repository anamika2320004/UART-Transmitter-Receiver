# UART Transmitter/Receiver in Verilog

## Description
This project implements a UART (Universal Asynchronous Receiver/Transmitter) in Verilog, demonstrating serial communication using **shift registers** and **finite state machines (FSMs)**.

**Key Learning Outcomes:**
- Understanding serial communication (UART protocol)
- Designing FSM-based modules
- Using shift registers for transmitting and receiving data
- Implementing baud rate timing for realistic UART operation

---

## Files
| File Name     | Description                                  |
|---------------|----------------------------------------------|
| `uart_tx.v`   | UART Transmitter module,  UART Receiver module, Testbench for UART transmitter and receiver  |
---

## Simulation Setup (EDA Playground)
1. Open [EDA Playground](https://www.edaplayground.com/).  
2. Create separate files for transmitter, receiver, and testbench.  
3. Select **Language: Verilog** and **Simulator: Icarus Verilog**.  
4. Run the simulation.  

- **Waveform:** Optional — enable waveform view to see serial bit transitions.
- **Clock:** 1 MHz  
- **UART Baud Rate:** 9600  

---

## Console Output Example

| Time (ns) | TX Serial | RX Data | RX Done |
|------------|-----------|---------|---------|
| 0          | x         | xx      | x       |
| 1000       | 1         | xx      | 0       |
| 6000       | 0         | xx      | 0       |
| 110000     | 1         | xx      | 0       |
| 214000     | 0         | xx      | 0       |
| 318000     | 1         | xx      | 0       |
| 422000     | 0         | xx      | 0       |
| 630000     | 1         | xx      | 0       |
| 734000     | 0         | xx      | 0       |
| 838000     | 1         | xx      | 0       |
| 995000     | 1         | A5      | 1       |
| 996000     | 1         | A5      | 0       |

> Notes:  
> - `TX Serial` shows the serial bit being transmitted.  
> - `RX Data` shows the byte received by the UART receiver.  
> - `RX Done` is a pulse signal indicating the reception of a full byte.  

---

## How It Works
1. **UART Transmitter**:  
   - Converts parallel 8-bit data into serial data.
   - Uses FSM to manage **IDLE, START, DATA, and STOP** states.
   - Each bit is transmitted over multiple clock cycles according to **baud rate timing**.

2. **UART Receiver**:  
   - Detects start bit, samples incoming bits in the middle of each bit period.
   - Uses FSM to reconstruct the 8-bit data from serial input.
   - Raises `RX_DONE` when a full byte is received.

---

## Learning Outcomes
- Design and simulate UART communication in Verilog.  
- Understand how baud rate affects transmission timing.  
- Observe serial-to-parallel and parallel-to-serial conversion.  

---

## References
- [UART Protocol Overview](https://en.wikipedia.org/wiki/Universal_asynchronous_receiver/transmitter)  
- Verilog shift register and FSM tutorials  
