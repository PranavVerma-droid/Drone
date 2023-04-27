# Drone-Project
🌎 This is a <b>Hobby Drone</b> made by <b>[PranavVerma-droid](https://web.craftingrealm.tk)</b>. 🌎 <br><br>
=> <b>P.S. This is a Hobby Drone, and it doesn't fly for very long (Approx. 5 Minutes) and it cannot take any more load</b>.

Here is what I did to Get it to fly: <br>
1. I Made a Custom PCB and Ordered it with [PCBWay](https://www.pcbway.com) (The File for that is Private - Sorry!)
2. I took out a old Li-ion Battery from a Old Electronics Car.
3. I Ordered a IR Remote Controller and a IR Receiver.
4. I Re-used the Batterry charger that came with the Car.

MultiWii Config Can be Found [Here](https://github.com/PranavVerma-droid/Drone-Project/blob/main/Code%20(MultiWii)/MultiWiiConf/MultiWiiConf.pde).
```
public void evaluateCommand(byte cmd, int dataSize) {
  int i;
  int icmd = (int)(cmd&0xFF);
  switch(icmd) {
    case MSP_IDENT:
        version = read8();
        multiType = read8();
        read8(); // MSP version
        multiCapability = read32();// capability
        if ((multiCapability&1)>0) {buttonRXbind = controlP5.addButton("bRXbind",1,10,yGraph+205-10,55,10); buttonRXbind.setColorBackground(blue_);buttonRXbind.setLabel("RX Bind");}
        if ((multiCapability&4)>0) controlP5.addTab("Motors").show();
        if ((multiCapability&8)>0) flaps=true;
        if (!GraphicsInited)  create_ServoGraphics();
       break;

    case MSP_STATUS:
        cycleTime = read16();
        i2cError = read16();
        present = read16();
        mode = read32();
        if ((present&1) >0) {buttonAcc.setColorBackground(green_);} else {buttonAcc.setColorBackground(red_);tACC_ROLL.setState(false); tACC_PITCH.setState(false); tACC_Z.setState(false);}
        if ((present&2) >0) {buttonBaro.setColorBackground(green_);} else {buttonBaro.setColorBackground(red_); tBARO.setState(false); }
        if ((present&4) >0) {buttonMag.setColorBackground(green_); Mag_=true;} else {buttonMag.setColorBackground(red_); tMAGX.setState(false); tMAGY.setState(false); tMAGZ.setState(false);}
        if ((present&8) >0) {buttonGPS.setColorBackground(green_);} else {buttonGPS.setColorBackground(red_); tHEAD.setState(false);}
        if ((present&16)>0) {buttonSonar.setColorBackground(green_);} else {buttonSonar.setColorBackground(red_);}

        for(i=0;i<CHECKBOXITEMS;i++) {if ((mode&(1<<i))>0) buttonCheckbox[i].setColorBackground(green_); else buttonCheckbox[i].setColorBackground(red_);}
        confSetting.setValue(read8());
        confSetting.setColorBackground(green_);
        break;
``` 
<br>

Other Documentation:
1. I used the <b>ATTINY212</b> on the Main PCB.
2. The IR and Remote are Generic.

Images Documentation:
<video controls>
  <source src="[movie.mp](https://github.com/PranavVerma-droid/Drone-Project/blob/main/Images-and-Videos/Drone-Flying-1.mp4)4" type="video/mp4">
</video>


