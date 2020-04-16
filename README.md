# Fog_Beetle
Wind tunnel operation and data analysis:


The files uploaded here are to operate and analyze the data acquired from a wind tunnel described in "surface morphology enhances deposition efficiency in biomimetic, wind-driven fog collection" (Link).

1. WindTunnel.ino:
  
This Arduino code is used to control the operation of the fan, nebulizers and the loadcell. The data reported are respectively:
  
  1) The raw number read from the loadcell
  2) Whether fog is actuated or not (1,0)
  3) The power percentage that defines the speed of the fan (PWM)
  4) The cycle number
  

2. DataAcquisition.py:

Python code to save data reported by the Arduino (using pySerial: https://pyserial.readthedocs.io/en/latest/shortintro.html) 
  
  
3. Example.txt:

  An example file saved by DataAcquisition.py. 
  
    2019-02-02 23:05:38,9878,0,40,0,
    Date Time, loadcell reading, fog flag, power percentage of the fan, cycle number,
    

4. DataAnalysis.py:

Python code to calculate the accumulation rate of fog droplets from the data above. The code first reads the data from the text file, then separates the cycles using reshape function.  Next it averages the data over every 5 seconds to eliminate the high frequency noises and converts the value to grams. The linear fit of each cycle is calculated and the printed values are the impaction rates. 
  

5. W.xlsx:

This excel file reports the mass of water directed toward the projected area of each target used in this study per second. By dividing the accumulation rate by the rate of water headed toward the projected area of the target one can calculate the deposition efficiency. 
  
    
    
    
6. WaterLevel&TemperatureControl.ino

A pressure sensor (MPXV7002DP) was connected to the bottom of the fog chamber that reads the pressure continuously. It compares the pressure read to the average of the first 20 readings. If the pressure is lower than 1mm of water it actuates a solenoid valve until it reaches the average value. Simultaneously, temperature, relative humidity and atmospheric pressure are recorded using a BME280.
