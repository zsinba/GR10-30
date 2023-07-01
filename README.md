# 硬件
DFRobot_GR10_30

<img src="https://ws.dfrobot.com.cn/FrzFPDP8UrYb7dNnC81NvKhHux4q"/>

## 文档 
https://wiki.dfrobot.com.cn/_SKU_SEN0543_Fermion_GR10_30_Gesture_Sensor#target_10
## 购买链接
略

#特点
* 最远识别距离30cm<p> 
* 可识别12种手势<p>
* 识别阈值参数可配置<p>
* 支持UART、I2C通讯<p>

# 技术规格
* 供电电压：3.3V~5V <p>
* 工作电流：10<mA<p>
* I2C地址：0x73<p>
* 波特率：9600<p>
* 最远识别距离：30cm<p>
* 工作温度范围：0℃~70℃<p>
* 工作湿度范围：5%RH~85%RH<p>
* 产品尺寸：20.5*23.5mm<p>
# 开发环境
Windows 11， Golang （20230701）

# 运行效果
```
starting
[2023-07-01 14:45:31.026] PAG悬停
[2023-07-01 14:45:33.140] PAG向下
[2023-07-01 14:45:34.569] PAG向上
[2023-07-01 14:45:35.775] PAG向左
[2023-07-01 14:45:37.070] PAG向右
[2023-07-01 14:45:38.292] PAG向左
[2023-07-01 14:45:39.281] PAG向右
[2023-07-01 14:45:40.250] PAG向左
[2023-07-01 14:45:41.082] PAG向右
[2023-07-01 14:45:42.025] PAG向左
[2023-07-01 14:45:42.685] PAG向右
```
# 协议
Modbus-rtu

# 设备地址
HEX: 0x73
<p>
DEC: 115

# 使用到的寄存器
0x0018 复位寄存器，开始的时候先复位
<p>
0x0007 输出寄存器，读这个就可以

# 对应位和手势的关系，见代码
```azure
const (
	PAGUp PAGRegister = 1 << iota // PAG向上
	PAGDown                       // PAG向下
	PAGLeft                       // PAG向左
	PAGRight                      // PAG向右
	PAGForward                    // PAG向前
	PAGBackward                   // PAG向后
	PAGClockwise                  // PAG顺时针旋转
	PAGCounterclockwise           // PAG逆时针旋转
	PAGWave                       // PAG挥手
	PAGHover                      // PAG悬停
	PAGUnknown                    // PAG未知
	PAGObjectAppearDisappear      // PAG目标出现/消失（保留）
	PAGHLModeChange               // PAG高低模式切换（保留）
	PAGProximity                  // PAG接近（保留）
	PAGClockwiseContinuous        // PAG顺时针连续旋转
	PAGCounterclockwiseContinuous // PAG逆时针连续旋转
)

func (r PAGRegister) Has(flag PAGRegister) bool {
	return r&flag != 0
}

```

