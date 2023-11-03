# FGPA

## 整体过程

```markdown
编写 Verilog (.v) 文件：

使用 Verilog 或其他支持的硬件描述语言编写您的 FPGA 设计代码。Verilog 文件描述了电路的行为和结构。
编写 Constraint (.cst) 文件：

编写约束文件，也称为约束条件文件。该文件描述了时序、引脚分配、时钟频率等约束条件，以确保设计在 FPGA 上正确运行。
综合：

使用综合工具，如 Yosys，将 Verilog 代码转换为逻辑网表。综合工具将分析和优化设计，并生成逻辑网表文件。
实现：

使用物理设计工具（例如 nextpnr, Vivado、Quartus Prime、iCEcube2 等），将逻辑网表映射到目标 FPGA 设备的物理资源上。该步骤包括布局（将逻辑元件放置在 FPGA 芯片上的位置）和布线（将逻辑元件之间的连线连接起来）。
生成 Bitstream 文件：

在实现步骤完成后，生成 FPGA 设备可识别的 Bitstream 文件。Bitstream 文件包含了将设计配置到 FPGA 芯片上所需的详细信息，例如逻辑元件的位置、连线信息和时钟设置。
配置 FPGA 开发板：

将生成的 Bitstream 文件加载到 FPGA 开发板上。这通常需要使用特定的软件工具或命令行工具，例如 Vivado Hardware Manager、Quartus Programmer 或 openFPGALoader。
```



## 工具

### yosys: 综合工具。
```markdown
>  1. 启动 Yosys：
>   - 在命令行中输入 `yosys` 命令来启动 Yosys 工具。
>
>  2. 导入设计文件：
> 
>    - 在 Yosys 提示符下，使用
>
>       
>
>      ```
>      read_verilog
>      ```
>
>       
>
>      命令导入设计文件：
>
>      复制
>
>      ```
>      yosys> read_verilog design.v
>      ```
>
> 3. 综合设计：
>
>    - 使用
>
>       
>
>      ```
>      synth
>      ```
>
>       
>
>      命令对设计进行综合：
>
>      复制
>
>      ```
>      yosys> synth <synthesis_command>
>      ```
>
>      ```
>      <synthesis_command>
>      ```
>
>       
>
>      表示您选择的综合命令。Yosys 支持不同的综合命令，如
>
>       
>
>      ```
>      synth_ice40
>      ```
>
>      （针对 Lattice iCE40 FPGA）或
>
>       
>
>      ```
>      synth_xilinx
>      ```
>
>      （针对 Xilinx FPGA）。您可以根据目标 FPGA 平台选择适当的综合命令。
>
> 4. 查看综合结果：
>
>    - 使用
>
>       
>
>      ```
>      show
>      ```
>
>       
>
>      命令查看综合后的设计：
>
>      复制
>
>      ```
>      yosys> show
>      ```
>
>      这将显示综合生成的逻辑网表。
>
> 5. 导出网表：
>
>    - 使用
>
>       
>
>      ```
>      write_verilog
>      ```
>
>       
>
>      命令将综合后的逻辑网表导出为 Verilog 文件：
>
>      复制
>
>      ```
>      yosys> write_verilog synthesized.v
>      ```
>
>      这将生成一个名为
>
>       
>
>      ```
>      synthesized.v
>      ```
>
>       
>
>      的文件，其中包含综合后的逻辑网表。
```

### nextpnr-gowin: 实现工具



### openFPGALoader: 烧录工具。





