# GPS_Spoofing
This is a proof of concept that transmits a GPS signalling using the location of 31 satellites and a TXCO PCB attached to a HackRF One. I also had to use a 30DB- attenuator to concentrate the signal so the car doesn't get overfaced with GPS signals. I managed to make the car think it's following a route around Doncaster using its own internal GPS or Phone running on Ubuntu Linux or Windows


## Team Members

|   Name              |    Username     |
|---------------------|-----------------|
| Owen Ball           |   Ballo-02      |

## Repositories/Tools that need to be downloaded
 - gps-sdr-sim
https://github.com/osqzss/gps-sdr-sim
 - SatGen 3 
https://www.labsat.co.uk/index.php/en/customer-area/software-firmware

## Brdc file location for up to date satellite positions
1.	Create an account on ‘https://cddis.nasa.gov’ 
2.	Download the latest brdc from ‘https://cddis.nasa.gov/archive/gnss/data/daily/’ -examples from ‘https://cddis.nasa.gov/archive/gnss/data/daily/2023/brdc/’ ‘brdc0320.23n.gz’
3.	Extract the file

##Hardware Uused
- HackRf One
https://greatscottgadgets.com/hackrf/one/ 
-30Db Attenuator

More Information Files- https://github.com/osqzss/gps-sdr-sim/tree/master/extclk
-Note- Only solder one capacitor on or else won’t work
![image](https://user-images.githubusercontent.com/42391940/223706023-1920e63b-da5d-4a88-a93f-af5f07462ab4.png)

## Installing Attenuator
30db connected via male SMA HackRF and female output to cable connected to either antenna or hardwired to rig 
## Installation
### Installation for Windows 
#### Installing Gps-sdr-sim
1.	Download Gps-sdr-sim from https://github.com/osqzss/gps-sdr-sim
2.	Unzip the contents 
3.	Start Visual Studio.
4.	Create an empty project for a console application.
5.	On the Solution Explorer at right, add "gpssim.c" and "getopt.c" to the Souce Files folder.
6.	Select "Release" in Solution Configurations drop-down list.
7.	Build the solution.

#### Installing SatGen 3
1.	Install SatGen 3 from - ‘https://www.labsat.co.uk/index.php/en/customer-area/software-firmware’
#### Installing HackRf One Drivers
1.	Install PothosSDR from - https://downloads.myriadrf.org/builds/PothosSDR/
Getting the brdc file for satellite positions 

1.	Create an account on ‘https://cddis.nasa.gov’ 
2.	Download the latest brdc from ‘https://cddis.nasa.gov/archive/gnss/data/daily/’ 
-examples from ‘https://cddis.nasa.gov/archive/gnss/data/daily/2023/brdc/’ ‘brdc0320.23n.gz’
3.	Extract the file

### Installation for Linux 
#### Installing Gps-sdr-sim
1.	Install prerequisites – 
2.	sudo apt install gnuradio libhackrf0 hackrf libhackrf-dev
3.	sudo make

# How to use with example (Aston Martin)
### Added Batch files for easy shortcuts
Compile_Speed.bat - Compiles the 'speed.txt' file to create a readable moving route in the .bin file 
Simulate_GPS.bat - Simulates the GPS co-ordinates in the compiled .bin file
### Create your own location
Getting the brdc file for satellite positions 
Note- Old brdc files can be used but please be aware of the date and time changing/inccorect
1.	Create an account on ‘https://cddis.nasa.gov’ 
2.	Download the latest brdc from ‘https://cddis.nasa.gov/archive/gnss/data/daily/’ 
-examples from ‘https://cddis.nasa.gov/archive/gnss/data/daily/2023/brdc/’ ‘brdc0320.23n.gz’
3.	Extract the file

### Create static location
Longitude - 40.812800
Latitude - -60.005900

1.	Sudo ./gps-sdr-sim -b 8 -e YOUR_BRDC_FILE_HERE -l 40.812800,-60.005900,100

### Create moving target
Triumphv3 – set route for the GPS to follow
1.	Go to SatGen 3
2.	Sudo gps-sdr-sim -b 8 -e brdc3540.14n -g triumphv3.txt

## Perform GPS simulation using an Aston Martin Rig
Notes for windows users:
  •	Don’t need sudo
  •	Whatever the project name was when compiled use that instead of ‘gps-sdr-sim’

1.	Sudo gps-sdr-sim -b 8 -e brdc0320.23n -g output.txt
![image](https://user-images.githubusercontent.com/42391940/223706492-f0d2b3e4-d72b-4381-9eae-c474b3178057.png)


2.	sudo hackrf_transfer -t gpssim.bin -f 1575420000 -s 2600000 -a 1 -x 0
![image](https://user-images.githubusercontent.com/42391940/223706578-4a39ba78-da7f-42a0-b373-39167043c7bd.png)
2.	Windows gives a slightly different result.

## SatGen 3
1.	Click Draw Route
2.	Select pins on where you want the route to go
![image](https://user-images.githubusercontent.com/42391940/223706909-92067734-b962-4288-8579-5920fc92b492.png)
3.	Click User defined
4.	Click save file
5.	Make sure the file is saved as .txt and looks something similar below with the values in. You can also adjust speed by pressing the speed button and changing

![image](https://user-images.githubusercontent.com/42391940/223706951-17f44c2c-b5af-4cbe-b368-926f21555840.png)


## License

Distributed under the GPL-3.0 License. See `LICENSE` for more information.
