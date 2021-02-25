# linux学习笔记
## 第二章主机规划与磁盘分区
### 磁盘分区
1. MBR(Master Boot Record):主要开机记录区，可以安装开机管理程序的地方，
2. 分区表（partition table）:记录整个磁盘分区状态，磁盘分区是由分区表记录，并不是物理分区（注：MBR分区表）
![磁盘分区表的作用示意图](_v_images/20210124112521947_31221.png =541x)
    >主要分区（Primary)
    >延伸分区（Extended）：可以分多个区块，分出来的区块成为逻辑分区
    >逻辑分区（logical partition）

3. GPT(GUID partition table)
    逻辑区块位址（Logical Block Address, LBA），一个扇区大小大概512Bytes或4K
    ![](_v_images/20210124224811959_12322.png =316x)
    
4. UEFI（Unifed Extensible Firmware Interface）：统一可延伸固件界面