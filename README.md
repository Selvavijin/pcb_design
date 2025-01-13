# pcb_design

The tunnels or holes are covered by copper.

![image](https://github.com/user-attachments/assets/7452480f-1d8b-4480-8b77-3c37dc4c845f)

LUT means gates. 1 LUT means 1 gate(AND, OR, etc). This has 5K LUTs

![image](https://github.com/user-attachments/assets/5adbd60c-45b2-4883-a213-28d3a48d9527)

Here we are going to learn about making production ready shields for specific applications for our projects.

![image](https://github.com/user-attachments/assets/3d177cbe-b08f-4557-9706-d45fcd431ae0)

KiCAD is the open source tool and the other two are commertial tools. But the workflow of all the three are similar.

![image](https://github.com/user-attachments/assets/f1219506-07a1-4bdf-869c-27a4a58da053)

This is the application that we are going to focus on. We need to use this with an FPGA and create a shield for it. Let us see how

![image](https://github.com/user-attachments/assets/dd09ac4c-a659-41fa-9946-7a513d7b971c)

Creating a new project in KICad will create two files. One is .kicad_sch file and the other is .kicad_pcb.

![image](https://github.com/user-attachments/assets/0590de25-b1e2-49a5-881b-cb10261f4560)

Initially we will look into the schmatic file

![image](https://github.com/user-attachments/assets/5ad4cb71-00a2-4846-b95e-a412827e1067)

We can goto the 'place' option at the top or click 'a' to open the symbol library which has the collection of symbols.

![image](https://github.com/user-attachments/assets/b030ffc8-c8b9-4fdc-b5f2-7b9ac58086e6)

The below shown is the very simple design. 'w' is used for wiring purpose.

![image](https://github.com/user-attachments/assets/99125600-6a48-47b0-a39c-9a092ab563f6)

Now, let us move to the actual design.
We can goto 'https://github.com/yathAg/VSDSquadron_FM_Workshop' and download the required libraries. Then we have to necessoryly save the library in the same folder as our project. We have 3 folders inside the library file. Symbole - it has a .bak(back up) file and a symbol file. To add this in kicad, goto preferences->manage symbol libraries->project specific libraries and select the file.

![image](https://github.com/user-attachments/assets/e9973eb8-1eba-4844-a83e-b4c0eeb5268c)

![image](https://github.com/user-attachments/assets/9e1157e2-e75a-43de-b60b-93e70e7a9660)

Then we will search for Gyroscope(ICM 4267) which is required for our project. This is also not available in the symbols. So, we go to 'snapeda' and search for 'icm 4267' and download and use it as we did for the previous symbol.

![image](https://github.com/user-attachments/assets/943b9578-976f-4a68-9b46-9a32146e2a85)

![image](https://github.com/user-attachments/assets/7c7e5332-792d-46a9-bd40-f3e1bd55ad2f)

For any design, the reference manual is the datasheet of the device so, we will download it from the website 'https://invensense.tdk.com/products/motion-tracking/6-axis/icm-42670-p/'. For schmatic capture, there are two important characteristics, one is the pin description. So, fromm the datasheet, it is observed that there are two communication protocols used I3C and SPI interface. In this workshop, SPI part is focussed.

![image](https://github.com/user-attachments/assets/5ce3321f-1241-4d13-a69e-ee8ecd0cdc68)

By looking into the pin configuration, we do the connections. RESV is reserved and no connection, so we press 'q' and give the cross symbol. When we connect the entire circuits with the wires, it will too crowded. So, to avoid that problem, we are using labels eg: AP_CS.

![image](https://github.com/user-attachments/assets/18038cc5-8f9c-4ead-b8e0-8fcfbb2469a6)

To check whether they are connected using label we can use the highlighter. Which are the pins are highlighted while clicking in a pin, they are connected to each other.

![image](https://github.com/user-attachments/assets/190b4611-9c3b-4fb1-bb60-32ef18b9b723)

Then we have to add Decoupling capacitors as shown in the datasheet to make sure that the circuit works correctly.

![image](https://github.com/user-attachments/assets/6e43779a-74b2-4f79-b33b-ddb246941399)

![image](https://github.com/user-attachments/assets/be40a475-0927-4d3a-a77c-a1a7ad8153a4)

Then we have to give connectins to the 4 pin header. The main thing we have to make sure is the power requirements is met. The power supply on the VSD Squadron FM does not used to power up the shield. So, we need to use external power supply. The common thing that is used is an LDO which can be found from the website'mouser.com' and search for LDO and apply filters like '1 output' and '-3.3v' output voltage and we will have multiple options. We can search ams1117-3.3 in google and enter into the website 'digikey' and find the datasheet.

![image](https://github.com/user-attachments/assets/f6ffd96d-08a7-4282-ab96-92c90f26b714)

This component is commonly available and we can find it in the symbols itself. The one end is connected to the 5V of the VSD Squadron and the other end is connected to 3.3V and the third end is connected to gnd. Also we connect capacitors by referring into the data sheet.

![image](https://github.com/user-attachments/assets/61b424c8-0590-4684-93b6-4bd099694180)

Then we give title by double clicking in the bottom. Then we partition the circuits using a line. This is the schmetic.

![image](https://github.com/user-attachments/assets/5f1128b5-0d60-447a-9467-250e84350f12)

Then we are going to do ERC rule check. Inspect->Electrical rule checker->run erc.

![image](https://github.com/user-attachments/assets/deade9c5-cdfc-48f9-87e2-b56c58904e02)

Here we can ignore the 2 errors, because we are going to connect the supply directly from VSDSquadron. However, if we need to remove those errors, we can connect the pins to the power flags as shown below.

![image](https://github.com/user-attachments/assets/bca8da25-5412-4688-9c69-0b7987f20aaf)

Then we have to assign footprints. click on assign footprints. Here there is no footprints assigned for the capacitors. But the footprints are assigned for the next two devices but it can't be found and the last one has footprint in kicad itself.

![image](https://github.com/user-attachments/assets/2f9164a3-464a-476e-874f-5b65760b2158)

So, we need to know, how to set footprints for the capacitors by going to the reference document in 'https://github.com/yathAg/VSDSquadron_FM_Workshop'. We select the below footprint for all the capacitors.

![image](https://github.com/user-attachments/assets/d01eeaef-80a5-46ae-a7af-34d9e5da3f18)

To select the footprint for the ICM kit, we need to goto the datasheet and refer. Here, pitch is the interconnect between two pins. Here it is 'e' and is set to 0.5.

![image](https://github.com/user-attachments/assets/981fea82-e6be-4d54-956a-f2eb10186944)

![image](https://github.com/user-attachments/assets/5c6a912e-3ba8-4ed2-ac34-83ef76c26306)

From the below picture, we get that we have to search 'LGA' for the footprint, so we double click the schematic and select the required footprint.

![image](https://github.com/user-attachments/assets/460579a7-20c0-4114-a05c-df61335980c7)

Then we also add the footprint for the VSDSquadron from the local directory and now the footprints are assigned for everything.

![image](https://github.com/user-attachments/assets/0d727253-c34e-48b5-8d3d-f5c400e62a53)


