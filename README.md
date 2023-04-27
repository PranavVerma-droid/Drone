# Drone-Project
🌎 This is a <b>Hobby Drone</b> made by <b>[PranavVerma-droid](https://web.craftingrealm.tk)</b>. 🌎 <br><br>
=> <b>P.S. This is a Hobby Drone, and it doesn't fly for very long (Approx. 5 Minutes) and it cannot take any more load</b>. <br>
=> This Drone has been build <b>UNDER 7$ (USD) </b>!!.

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


https://user-images.githubusercontent.com/73458565/234993466-746cd578-5364-4113-ba4c-764257cefc78.mp4


![photo_2023-04-28_02-16-19](https://user-images.githubusercontent.com/73458565/234993839-4af88486-3edb-49e8-bf2a-3814396a040c.jpg)
![photo_2023-04-28_02-16-23](https://user-images.githubusercontent.com/73458565/234993873-0c5ed616-3405-45a8-bc78-573b746fda76.jpg)


![photo_2023-04-28_02-16-16](https://user-images.githubusercontent.com/73458565/234993894-efb5d054-9d78-48df-863c-bd55b61027a5.jpg)


![photo_2023-04-28_02-16-13](https://user-images.githubusercontent.com/73458565/234993913-75b55853-cb26-4a9e-9ea1-725cd80db2f7.jpg)


![photo_2023-04-28_02-16-09](https://user-images.githubusercontent.com/73458565/234993930-060bda87-c356-4a70-b17a-4a2e63a2d6a2.jpg)



![photo_2023-04-28_02-16-05](https://user-images.githubusercontent.com/73458565/234993948-54ff1e37-8174-420e-b317-090fee10fc53.jpg)

![photo_2023-04-28_02-16-02](https://user-images.githubusercontent.com/73458565/234993974-050c96a1-9b7f-4055-8671-9c6e85cde447.jpg)


![photo_2023-04-28_02-15-59](https://user-images.githubusercontent.com/73458565/234993991-fb42b6d2-8fa4-434a-b8bc-9f91b1e84188.jpg)



![photo_2023-04-28_02-15-54](https://user-images.githubusercontent.com/73458565/234994032-c9b0e338-5337-452e-b92f-88c10fc8702f.jpg)

![photo_2023-04-28_02-15-47](https://user-images.githubusercontent.com/73458565/234994048-81a56402-5237-404e-ac1d-832e5dd324f2.jpg)


<b>This Code has been [Licensed](LICENSE).
