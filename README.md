### Universal_Shift_Register
The "Universal Shift Register" module is a digital circuit that performs various shifting operations on a binary data stream.
It can shift the data to the left or right, load a new input value, or hold the current value without any shift.
The module takes inputs such as clock (clk), reset (reset), input data (I), select signal (sel), and shift-in data (si).
It provides outputs for the shifted data (Q) and the shifted-out data (so).

Here's a breakdown of the module's functionality:

#Register Initialization:
The module uses a D flip-flop (Q_reg) to store the current output value.
On a positive edge of the clock (clk) and a positive edge of the reset signal (reset), the module resets the output value (Q_reg) to zero.

#Shifting Logic:
The module uses combinational logic to calculate the next value (Q_next) based on the select signal (sel), shift-in data (si), current output (Q_reg), and input data (I).
The select signal (sel) determines the type of shift operation to be performed:
2'b00 - No shift: The output remains unchanged.
2'b01 - Shift right: The output is shifted right by one position, and the most significant bit (MSB) is replaced with the input data (si[1]).
2'b10 - Shift left: The output is shifted left by one position, and the least significant bit (LSB) is replaced with the input data (si[0]).
2'b11 - Load input: The output is replaced with the input data (I).
Other select signal values result in no shift, and the output remains unchanged.
The calculated next value (Q_next) is stored in the register (Q_reg) on the next positive edge of the clock (clk).

#Output Assignment:
The final output (Q) is assigned to the current value stored in the register (Q_reg), representing the shifted or loaded data.
The shifted-out data (so) is assigned the value of the MSB (Q_reg[n-1]) and the LSB (Q_reg[0]),
representing the data that is shifted out of the register during the shifting operations.
By using this Universal Shift Register module, you can manipulate binary data streams by shifting, loading,
or holding values based on the control signals and input data provided.
It is a versatile circuit commonly used in digital systems for tasks such as data manipulation,
serial-to-parallel conversion, parallel-to-serial conversion, and various data processing operations.
