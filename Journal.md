## 1.4.2026
### Time spent: 1h
i wanted to make a row of leds going from 1 to x and from x to 1 and going at varying speeds that the ics would dictate. My first step was to try and simulate the ics in a software of some sort, well i spent an hour trying to get multiple diffrent simulators working. I tried to do it in falstad which would actually be possible but way too much work, so i tried the next best thing i could think of, kicad spice simulation. I tried to look up spice models of the cd4020 and cd4017 but i wasnt succesfull. So i tried asking ai to give me the spice models and yet again nothing, i did a lot of debugging since kicad always spat a lot of errors at me, i didnt understand a single error, after an hour i gave up..

## 2.4.2026
### Time spent: 20 mins
I scrapped my old idea and started working on a completly new one.Firstly i looked up what the lm556 is and how i could use it, its basically 2 ne555s in one package, so i based my idea on 2 main frequencies. A crosshair of 8 (16 total) Leds + 4 leds in the corners, with frequencies as in the image. Since we have the main part i picked 2 cd4017 to drive the 16 leds i didnt have to research anything since i used it before. I will also most likely use a cd4020 for frequency C, and i will most likely change the frequencies(probably b and c so the cd4020 can handle tha math)  

<img src="./attachments/idea.jpg" alt="idea" width="400"/>  

> So far i have put the lm556 inside my kicad schematic, but its weird it is 2 symbols with either unit a or b markings. I also imported the cd4017 for both parts(a + b), and wired up the gnds and vccs, and outputs of both parts to their own cd4017  

## 2.4.2026 #2
### Time spent: 30 mins
I wired up the 2 cd4017s to the leds, and their reset and clk enable pins to GND. I connected the cathodes of the 16 leds to ground through a resistor(i will calculate the value later). I also added a cd4020 and another cd4017 to the schematic and wired the reset pins of both Ics to GND, and added a label for clock A and put the label to Lm556s part A and cd4020 clk so they are connected, i will need to do math to figure out the correct speed. Now a big thing i need to decide if i want the leds of the crosshair to go d1-d2........d8-d7-d6....  , or not. If i would choose the first option i would need to either lower the amount of leds to 6 so i could use the existing cd4017 or use an extra cd4017 but i dont think that would be efficient enough idk tho. That decision is for after i wake up since its a bit past midnight already.
<img src="./attachments/Schematic_v1.png" alt="idea" />  

## 6.4.2026
### Time spent: 1H 40 mins
From last time a lot changed i reworked the frequencies so frequencies ended up like this a = 2 Hz b = 4 Hz and c = a/8.  
> so c = 0.25Hz  

Than i used a NE555 calculator in astable configuration and calculated what resistors and capacitors i need for the frequencies a and b. I also decided that the 4 LEDs that are driven by frequency c will be blue so it has a nice contrast. Once i had my new version in mind i put all of the resistors in the config that the digikey calculator showed me. SO i added all of the polarised Caps and resistors according to my calculations. Wired it all up and i had my finished schematic.
<img src="./attachments/finalScheme.png" alt="final version of the scheme">

Now that i had my schematic came the harder part making the PCB. But first i had to pick the footprints, which i somewhat followed the guide and somewhat just picked what looked best and would work. After i selected all of my footprints i imported the components from the schematic and started doing the layout that will be simmilar to the sketch. So i positioned the LEDs in a cross with the 4 blue LEDs in the corners, then I placed the Ics in a way i thought would be the best for routing, then i moved the parts that were needed for the ics or leds to work/not burn up. Once that was done i started by routing on the front layer, i routed all signals and and ic outpust, pretty much anything that wasnt vcc or gnd, along the way i had to use a few vias and route some parts on the back layer. Once that was done i routed the VCC and GND on the back layer occasionally using the front.
#### Finished PCB  

<img src="./attachments/IcProject.png" alt="Finished PCB">  

> i dont have the 3d models since they take up a lot of space.