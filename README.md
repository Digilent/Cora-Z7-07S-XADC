Cora Z7-07S XADC Demo
====================

Description
-----------

This project demonstrates how to use the Cora Z7-07S's ZYNQ FPGA's analog-to-digital core (referred to as the XADC) with a ZYNQ processor. Vivado is used to build the demo's hardware platform, and Xilinx SDK is used to program the bitstream onto the board and to build and deploy a C application.

To use this demo, the Cora Z7-07S must be connected to a computer over MicroUSB, which must be running a serial terminal. For more information on how to set up and use a serial terminal, such as Tera Term or PuTTY, refer to [this tutorial](https://reference.digilentinc.com/learn/programmable-logic/tutorials/tera-term).

A channel select index can be incremented by pressing button 0 and decremented by pressing button 1. The table below shows how the channel select index is used to select from the Cora's various analog inputs. RGB LED 0 is used to show the sign of the selected analog input. If the voltage reading is greater than 0.5 Volts, the RGB LED is green; if the voltage reading is less than -0.5 Volts, the RGB LED is red.

**Warning:** *Take care not to drive analog inputs below the Cora's ground or above 1.0V (for differential inputs) or above 3.3V (for single-ended inputs). Differential inputs operating in Bipolar mode provide negative readings when the negative input pin of the pair has a higher voltage than the positive, however, this does NOT imply that these inputs can safely be driven below the system ground.*

| Index     | Analog Input/s                           | 
| --------- | ---------------------------------------- |
| 0         | VP/VN Dedicated Differential Input       |
| 1         | Shield Header A6-A7 Differential Input   |
| 2         | Shield Header A8-A9 Differential Input   |
| 3         | Shield Header A10-A11 Differential Input |
| 4         | Shield Header A0 Single-Ended Input      |
| 5         | Shield Header A1 Single-Ended Input      |
| 6         | Shield Header A2 Single-Ended Input      |
| 7         | Shield Header A3 Single-Ended Input      |
| 8         | Shield Header A4 Single-Ended Input      |
| 9         | Shield Header A5 Single-Ended Input      |

Requirements
------------
* **Cora Z7-07S**: To purchase a Cora Z7-07S, see the [Digilent Store](https://store.digilentinc.com/cora-z7-zynq-7000-single-core-and-dual-core-options-for-arm-fpga-soc-development/).
* **Vivado and Vitis 2020.1 Installations**: [Installing Vivad, Vitis, and Digilent Board Files](https://reference.digilentinc.com/learn/programmable-logic/tutorials/2020.1/installation) guide.
* **MicroUSB Cable**
* **Wires and a Circuit to Measure**

Demo Setup
----------
**Note:** *Releases have not yet been created for either variant of this demo.*

**Note:** *Other releases may require other steps be taken to use them. Make sure to check the version of this README found in the commit associated with that release's tag for instructions.*

1. Download the most recent release ZIP archives from the repo's [releases page](https://github.com/Digilent/Cora-Z7-07S-XADC/releases). These files are called "Cora-Z7-07S-XADC-hw-2020.1-1.zip" and "Cora-Z7-07S-XADC-sw-2020.1-1.zip". The -hw- archive contains an exported XPR project file and associated sources for use with Vivado. The -sw- archive contains exported project files for use with Vitis. Both of these files contain the build products of the associated tool.
2. Extract the downloaded -hw- archive. (Do not extract the -sw- archive)
3. Open Vivado 2020.1.
3. Open the XPR project file, found at \<archive extracted location\>/hw/hw.xpr, included in the extracted hardware release in Vivado 2020.1.
4. No additional steps are required within Vivado. The project can be viewed, modified, and rebuilt, and a new platform can be exported, as desired.
5. Open Vitis 2020.1. Choose an empty folder as the *Workspace* to launch into.
6. With Vitis opened, click the **Import Project** button, under **PROJECT** in the welcome screen.
7. Choose *Vitis project exported zip file* as the Import type, then click **Next**.
8. **Browse** for the downloaded -sw- archive, and **Open** it.
9. Make sure that all boxes are checked in order to import each of the projects present in the archive will be imported, then click **Finish**.
10. Connect your test circuit to appropriate shield header analog inputs. Take note of the warning in the Description section, above.
11. Connect the Cora Z7 to your computer via the MicroUSB programming cable, make sure the power source select jumper is set to USB or WALL (depending on whether you are using an external supply), then power on the board by flipping the power switch to the ON position.
12. Open a serial terminal application (such as TeraTerm or PuTTY) and connect it to the Cora Z7's serial port, using a baud rate of 115200.
13. In the *Assistant* pane at the bottom left of the Vitis window, right click on the project marked `[System]`, and select **Run** -> **Launch Hardware**. When the demo is finished launching, messages will be able to be seen through the serial terminal, and the demo can be used as described in this document's *Description* section, above.

Next Steps
----------
This demo can be used as a basis for other projects by modifying the hardware platform in the Vivado project's block design or by modifying the application project.

Check out the Cora Z7-07S's [Resource Center](https://reference.digilentinc.com/reference/programmable-logic/cora-z7/start) to find more documentation, demos, and tutorials.

For technical support or questions, please post on the [Digilent Forum](forum.digilentinc.com).

Additional Notes
----------------
For more information on how this project is version controlled, refer to the READMEs found in this repository's hw/scripts and sw/src folders.