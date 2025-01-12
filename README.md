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

