## Radar detection

This is to implement 2D CFAR process of Radar detection. 
Radar_Target_Generation_and_Detection.m is the main function in matlab

**Radar** data is typically very sparse and in a limited range, however it can directly tell us how fast an object is moving in a certain direction. This ability makes radars a very pratical sensor for doing things like cruise control where its important to know how fast the car infront of you is traveling. Radar sensors are also very affordable and common now of days in newer cars.

### details

#### Implementation steps for the 2D CFAR process.

* Slide Window through the complete Range Doppler Map

* Set the training, guard cells and offset

* design a loop such that it slides the CUT across range doppler map by giving margins at the edges for Training and Guard Cells.

#### Selection of Training, Guard cells and offset.
* Training Cells, Tr = 12, Td = 8;
* Guard Cells,  Gr = 4; Gd = 4;
* Offset the threshold by SNR value in dB, offset=9.5;

#### Steps taken to suppress the non-thresholded cells at the edges.
 To sum convert the value from logarithmic to linear using db2pow function. Average the summed values for all of the training cells used. After averaging convert it back to logarithimic using pow2db. Further add the offset to it to determine the threshold. Next, compare the signal under CUT with this threshold. If the CUT level > threshold assign it a value of 1, else equate it to 0.
