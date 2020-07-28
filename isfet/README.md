# ISFET

## MOSFET 基本原理

- 空乏型MOSFET

1. P型基底鑲入兩塊N型區，分別為Source以及Drain
2. 在這兩極之間以參雜成N型的通道區相連接
3. N型通道區的上層覆蓋了一層氧化層(二氧化矽(SiO2))
4. 閘極(Gate)是用金屬極片蓋在氧化層上面做成

## ISFET基本原理

- 由 Bergveld Piet於1970年提出

  他發現將一般MOSFET 的金屬閘極去除後，再將其浸入溶液時，元件之通道電流會隨H+濃度不同而變化，稱其為離子場效電晶體(ISFET)。

- **優勢**

  - 輸入阻抗高
  - 輸出阻抗低
  - 響應時間快
  - 低價位
  - 適合用於Biosensor

### 工作原理

由於pH-ISFET工作時感測膜區域直接浸泡於溶液中。與待測溶液相接觸的感測膜是離子感測元件將化學量轉換成電學量的關鍵。對溶液中離子活度的響應機制是根據吸附鍵結模型(Site-binding model)，電解質與感測膜之介面處會形成界面勢(Surface potential)，該界面勢隨電解質溶液的離子活度而改變，並對ISFET的通道電流起調制作用，進而引起汲源電流的變化，此即為氫離子感測場效應電晶體的基本工作原理。


- pH-ISFET基本公式

$$
 \begin{array}{l}
\mathrm{I}_{\mathrm{DS}}=\mathrm{g}_{\mathrm{m}}\left[2\left(\mathrm{V}_{\mathrm{GS}}-\mathrm{V}_{\mathrm{T}}\right) \mathrm{V}_{\mathrm{DS}}-\mathrm{V}_{\mathrm{DS}}^{2}\right] \quad  \\
\mathrm{V}_{\mathrm{T}}(\mathrm{ISFET})=\mathrm{V}_{\mathrm{T}}(\mathrm{MOSFET})-\frac{\Phi_{\mathrm{M}}}{\mathrm{q}}+\mathrm{E}_{\mathrm{Ref}}+\chi^{\mathrm{Sol}}-\psi_{0} \\
\Psi_{\mathrm{o}}=\mathrm{E}_{\mathrm{o}}+\frac{2.303 \mathrm{RT}}{\mathrm{F}} \log \mathrm{a}_{\mathrm{H}^{+}}=\mathrm{E}_{\mathrm{o}}-\frac{2.303 \mathrm{RT}}{\mathrm{F}} \mathrm{pH} \\
\mathrm{I}_{\mathrm{DS}}=\mathrm{g}_{\mathrm{m}}\left[2\left(\mathrm{V}_{\mathrm{GS}}-\frac{2.303 \mathrm{RT}}{\mathrm{F}} \mathrm{pH}-\mathrm{V}_{\mathrm{T}}^{*}\right) \mathrm{V}_{\mathrm{DS}}-\mathrm{V}_{\mathrm{DS}}^{2}\right]
\end{array}
$$

- 吸附鍵結模型(Site-binding model)
  - Yates提出用於解釋pH-ISFET響應原理
  - 在感測膜表面存在著羥基(Si-OH, Al-OH, Ta-OH)
    - ISFET感測膜的種類
      - Ta2O5
      - Al3N4
      - Si3N4
  - 在感測膜浸在電解質溶液時，界面處會發生以下化學反應

$$
 \begin{array}{l}
M-O H \Leftrightarrow M O^{-}+H^{+} \\
M-O H+H^{+} \Leftrightarrow M O H_{2}^{+}
\end{array}
$$

- 總體來說就是藉由感測膜感應出一個表面電位，並藉由導線將表面電位傳至後方MOSFET的閘極端，改變起始電壓(Threshold Voltage,Vth)
- pH值愈高，VT愈大，I-V曲線將往右移動

$$Sensitivity=\frac{|△ψ0|}{|△pH|}=\frac{|△Vthreshold|}{|△pH|}=\frac{|△Vgs|}{|△pH|}$$

由上述式子可以得知，感測器的表面電位、元件起始電壓、閘極源極之間的電壓(Vgs)皆會酸鹼度改變。
很多論文提到的感測度(Sensitivity)指的是Vth隨著pH的變化量而改變，如下圖所示，起始電壓(Vth)會隨著會隨著pH值升高而上升，而根據上面的公式，Ids會變小。

![Vth versus pH](https://user-images.githubusercontent.com/67454551/87219852-63c8ce00-c391-11ea-9159-a25ec532d689.png)

### 響應時間

如下圖所示，ISFET得感測度會隨時間變化

![drifting](https://user-images.githubusercontent.com/67454551/87219949-37618180-c392-11ea-98e0-43de1b2ee0d4.png)


### 量測系統

- C-V

  目前先不討論C-V量測系統，先著重於I-V量測系統

- I-V

  - IDS-VGS

  ![Ids versus Vgs](https://user-images.githubusercontent.com/67454551/87220003-f4ec7480-c392-11ea-9875-fd0c7dfcf454.png)


    下面曲線與X軸交點為Vth由圖可以得知當pH質越大，元件所需的Threshold Voltage就越大，因此VGS也更高

- IDS-VDS

  ![Ids versus Vds](https://user-images.githubusercontent.com/67454551/87220019-1b121480-c393-11ea-8ac1-cbdebe90ac1f.png)


### ISFET的缺點

- 時漂與遲滯量測系統

  - 遲滯現象

  > 所謂遲滯，指當溶液之pH 值突然改變後，又再次回至原來的pH值
  > 時，元件之輸出電壓會與原先pH值未改變前之輸出電壓有所不同，即量測順序為pHx→pHy→pHx→pHz→pHx的情況下，其前後兩次pHx所測量的輸出值不相同，此電壓輸出之差值即為遲滯。

  > H+和OH-離子的大小不同，H+離子擴散的速率高於OH-離子，故於酸性溶液中遲滯量較小，而鹼性溶液中遲滯量較大，造成遲滯曲線的不對稱。

  - 溫度效應

    可以分為下列幾種:

    - 參考電極之溫度效
      應

         ![drfting by temperature](https://user-images.githubusercontent.com/67454551/87220045-409f1e00-c393-11ea-9089-11260b0a9932.png)


        - 待測液之溫度效應

        - 臨界電壓之溫度效應

        - 表面電位之溫度效應

    - 照光響應
        -

- 酸鹼讀出電路與量測系統

### Performance

- Stability and reproducibility

  ![stability](https://user-images.githubusercontent.com/67454551/87220072-86f47d00-c393-11ea-933c-aeceb9266b7a.png)


- Response time (R)

  ![response time](https://user-images.githubusercontent.com/67454551/87220075-8d82f480-c393-11ea-9879-4464ce47690d.png)

- Drifting effect

  ![Vgs versus time](https://user-images.githubusercontent.com/67454551/87220076-9247a880-c393-11ea-9950-c007651e652b.png)

## Dual Gate ISFET

 **2015 IEEE**
[High performance dual-gate ISFET with non-ideal effect reduction schemes in a SOI-CMOS bioelectrical SoC](https://ieeexplore.ieee.org/document/7409792 "Title").
This device possesses two gates:

- **Fluidic gate (FG)**: Biased via a reference electrode in solution.

- **Standard polysilicon gate (PG)** : Standard gate of MOSFET.


> DGFET can be approximately modeled as two FETs connected in parallel.

### Operation mode

- single-gate (SG) operation

  - Only fluidic gate transistor is turned on to generate pH dependent
    current with a **constant drain-to-source voltage** **(VDS = 0.2 V).**

  - Vpg is set **0V** and Vfg is sweeping through **0 to 2V**

    ![Vfg sweeping](https://user-images.githubusercontent.com/67454551/87668247-5e5af180-c79e-11ea-99c9-d3462adf2663.png 'width=378')


- PG mode

  - Vpg is set **0.5 V** and Vpg is sweeping through **-0.2 to 1.5 V**

  - Optimal Vpg=0.5V (less drifting) when Vfg is set grounded.

  ![Vfg sweeping](https://user-images.githubusercontent.com/67454551/87669011-ca8a2500-c79f-11ea-9493-4c244fece83d.png 'width=378')

### Sensitivity

- According to the **VTH difference derived from the IDS-VFG
  data**, this device has a near-Nernst pH sensitivity of 53.3 mV/pH with linearity of $R^{2} = 0.994$ .

## Shortage of ISFET

- Time drift
- Hysteresis effect
- Severe flicker noise [(1)](https://www.sciencedirect.com/science/article/pii/S0925400509007059)

## Different Structure of ISFET


### Extended-gate

- Half of **transconductance efficiency (gm/ID) due to capacitive division**
- threshold voltage (VTH) mismatch due to trapped charges on the sensing membrane



### Sensitivity

- According to the **VTH difference derived from the IDS-VFG
  data**, this device has a near-Nernst pH sensitivity of 53.3
  mV/pH with linearity of R^2 = 0.994.


### Advantage

- Hello?
