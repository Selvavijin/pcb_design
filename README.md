# pcb_design

The tunnels or holes are covered by copper. There is a core present in the middle and the copper layers cover the core. We focus on 2 layer board. so, we have a core and 2 copper layers.

![image](https://github.com/user-attachments/assets/7452480f-1d8b-4480-8b77-3c37dc4c845f)

The gray colour represents the core and the two yellow layers represent copper layers. In KiCAD, front copper layer is red in colour and back copper layer is blue in colour.

![image](https://github.com/user-attachments/assets/02e7a43c-e88b-4e99-a0a6-0cb0c54a28ae)

![image](https://github.com/user-attachments/assets/9b140cc9-d577-4ceb-89db-c1d0f71ca554)

Silkscreen is used to add the important informations like adding the names or writing any text.

![image](https://github.com/user-attachments/assets/75a1101f-b6fa-444e-93d9-2c34f6ad543c)

![image](https://github.com/user-attachments/assets/a7ff19bb-b237-4fef-8ef8-f9f2b4e0a1a3)

![image](https://github.com/user-attachments/assets/e2b671ff-21d6-4296-aa4a-c4a67713af05)

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

![image](https://github.com/user-attachments/assets/9e0f2f1e-32fe-4109-9d25-ec1d9f5c246b)

As a designer, we have to make connections with minimum resistance.

![image](https://github.com/user-attachments/assets/f5419905-8a9b-456d-9cd7-c5d1d6f76d4a)

![image](https://github.com/user-attachments/assets/85eca368-d080-4b13-82fa-f4a909661dc8)

![image](https://github.com/user-attachments/assets/98c51d32-da5d-455b-bd00-52ba88912658)

![image](https://github.com/user-attachments/assets/f07e94bb-9dc6-4565-866a-39519f126caf)

![image](https://github.com/user-attachments/assets/f352f65f-e9e8-4e82-8fba-f8b0c6ecdab0)

In KiCAD we are making a small change for the 10 and 22um capacitor in footprint as a bigger size.

![image](https://github.com/user-attachments/assets/6a396416-f8cb-48bf-b14f-70d48cd7b8c1)

Once that is done, we can move to the PCB editor and the below window appears.

![image](https://github.com/user-attachments/assets/44950bc1-948b-4dc5-bd54-e3c39735e793)

To create a new project, goto File->Board setup. The user layers are not required now, so we disabled it.

![image](https://github.com/user-attachments/assets/87b4e175-398f-4d83-9c6f-d9f618755e4e)

Then moving to physical stackup, we are customizing the colours of layers and also we can customize the thickness and material.

![image](https://github.com/user-attachments/assets/27852020-02b4-4674-89c0-7cc4c1329871)

Moving to 'constraints'. If we do more designs, we can use the option 'import settings from another board'. Otherwise, manually we have to set it according to the manufacturer. Now we stick to 'JLCPCB' manufacturer. The detailed document can be found in the reference document. And the capabilities of JLCPCB can be found in 'https://jlcpcb.com/capabilities/pcb-capabilities'.

![image](https://github.com/user-attachments/assets/71903bb1-7ec6-45a8-b990-a9ac41879442)

![image](https://github.com/user-attachments/assets/e20972a7-82cb-4d96-9040-b5ddd5d08dce)

![image](https://github.com/user-attachments/assets/a8dc59a3-1165-4cbe-8498-0ee5408daa1d)

![image](https://github.com/user-attachments/assets/e2669f45-fa4c-4984-bade-a9254f1438a6)

Then we can move to 'pre-defined sizes'

![image](https://github.com/user-attachments/assets/4b9ccd20-0930-4533-b394-edfd4b2f97bc)

Now the entire setup is complete. 
Now we select the 50 mils.

![image](https://github.com/user-attachments/assets/8068762c-d6da-43bb-947b-503a27ebd7d9)

The three sets of capacitors that are together are called de-coupling capacitors and should be placed as close to the power pins as shown in the schematic.

![image](https://github.com/user-attachments/assets/4f29bffa-bc0e-4a0e-b7c4-901fa0780093)

Then we organize the silkscreen. Then we draw the board boundary. So, we select the edgecuts layer and draw boundary.

![image](https://github.com/user-attachments/assets/7bf1ad4f-4bed-45c9-b3f1-f61d240137d2)

Then we are going to make the copper zones. There are two layers top and bottom. On bottom, we are going to add a gnd zone.

![image](https://github.com/user-attachments/assets/4c1dd7c0-070f-4f2f-a9c8-932e4e2e3c0e)

![image](https://github.com/user-attachments/assets/1ff83922-751f-427f-84ff-20443fe6977f)

If we see down, we can see 25 unrouted nets and if we press 'b', it fills out the copper zone as shown below.

![image](https://github.com/user-attachments/assets/ec7d7880-5e96-4bed-aeaf-774648dac6aa)

Now, all the gnd are connected on the bottom layer and are remaining in the top layer. On the front layer, we are going to give 3.3v zone as we given for the gnd.

![image](https://github.com/user-attachments/assets/81fbb072-597e-478d-9f7a-089273e4b4fa)

When we press 'b' again, all the 3.3v are connected.

![image](https://github.com/user-attachments/assets/9e7176f1-8e8e-4eaf-9ead-682b149395e7)

But, it is missed in some places as shown below because of the minimum width and the clearance that we selected.

![image](https://github.com/user-attachments/assets/a8b0ffaf-5941-4b40-979d-4641980371d2)

If we reduce the clearance value, it will affect the circuit. So we are going to give connection using wires. 

![image](https://github.com/user-attachments/assets/6aafc1f6-778e-43eb-b7a8-8dd0a2c35a4b)

While we give connections, we face difficulty in routing as shown above. So, will change the pins in the schematic as shown below.

![image](https://github.com/user-attachments/assets/48ae6c45-bdae-4302-a908-2a863bd7a8f7)

![image](https://github.com/user-attachments/assets/7c4f9e15-a677-4799-807d-bf5c381c3442)

We can click 'v' for a via and use it.

![image](https://github.com/user-attachments/assets/d7861557-7e42-49b8-b7b3-697fae772841)

Then we do connect gnd signals by using the via.

![image](https://github.com/user-attachments/assets/5de3fa9e-7f59-4c1a-9f49-f0f55a02eb6e)

Then we do connect 5V signal using 20 mil trace.

![image](https://github.com/user-attachments/assets/952804f3-7169-41ff-b4e9-51a8b4c0a5d6)

In pin number 8 and 5, the connection is not done due to clearance. So we connect it with a place trace as shown below.

![image](https://github.com/user-attachments/assets/5794f4b4-416b-448e-8763-e335427df4e9)

Once these things are done, we click 'b' again.

![image](https://github.com/user-attachments/assets/97707291-5296-43f8-8fd3-d39815ca26ec)

Then we go to the 3d viewer and get an idea on how the PCB looks like.

![image](https://github.com/user-attachments/assets/f55bbc92-c742-40d8-9505-7826985e92d7)

![image](https://github.com/user-attachments/assets/93570122-864a-4ceb-b692-11f6039300a7)

There are more empty space and we can go to the silkscreen layer to add any texts. 

![image](https://github.com/user-attachments/assets/70a1f05e-e4a8-4445-afe3-9064d1f445e2)

We can add the texts in a fancier manner by clicking on the plugin and content manager->Kibuzzard on the home screen. 

![image](https://github.com/user-attachments/assets/23504def-97b0-4be4-b57d-f3fb31dc5af2)

Once that is done, we can go to preferences->action plugin.

![image](https://github.com/user-attachments/assets/70ce049a-a1a9-4844-9dca-33838df81724)

The next step is to run the DRC checker and we can exclude the error that are obtained. Because, we have checked them already.

![image](https://github.com/user-attachments/assets/02cf98b9-f37a-4f00-abd7-c4481344ff6c)
