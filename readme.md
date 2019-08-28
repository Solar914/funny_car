2019/7/15
    
    这是用于rt-thread举办的智能战车DIY活动的一个项目。
   
    目标是设计一个两轮平衡小车，完成基本功能，平衡和遥控。如果有时间会增加树莓派做物体跟踪。
    
    硬件搭建：采用大疆的m2006无刷电机搭配c610电调，采用6s航模锂电池供电（不加稳压模块），mcu选用stm32f407zgt6，imu模块选用gy-86，蓝牙hc-05作为遥控通信，选用us-100超声波模块用来避障。

    目前进度：
    1.已在正点原子探索者开发板上完成了：在rt-thread 4.0.0系统下，对两个电机的控制（基于can总线），读取gy-86的九轴数据（怀疑磁力计读数有问题，暂时姿态解算有问题），还有硬件定时器，软件定时器，LED控制等一下简单的功能。
    2.pcb已经完成mcu最小系统，lm2576-5、asm1117-3.3稳压部分，can芯片tja1050电路，的设计。
    3.电机支架和底板的机械图纸已设计好（同学帮忙设计的），已经送去加工了。

2019/8/28
    目前已基本完成要求功能，ps2遥控控制两轮平衡车较稳定的运行，具体如下：
        硬件上，24v转5v，5转3.3v稳压电路，stm32f407zgt6最小系统与外围接口电路，pcb做了两版才成功。
        软件上，完成了，姿态结算，数据滤波，串级pid 外环角度环，内环速度环，在线pid参数修改，串口配合山外调试助手在线看数据波形，ps2遥控控制等。

    还准备继续做的内容：1、减少一些全局变量的使用，用rtt的IPC来替代。
                      2、通过yaw角度或电机编码器，实现转向环 速度 的闭环控制。增加 前进 和 转向 的位置控制。（前面的都是速度控制）
                      3、增加树莓派做图像处理的一些工作。