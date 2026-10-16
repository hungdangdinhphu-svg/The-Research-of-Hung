(16/10/2026 - DD/MM/YYYY)

# Hệ hình thức, IPR, Target, Cawpg, và phép biến đổi T

## 1. Định nghĩa

### 1.1. Hệ hình thức
Một hệ hình thức:
\[
J=(A,D,C)
\]
trong đó:
- $A$: tập tiên đề.
- $D$: tập định nghĩa.
- $C$: tập hệ quả.

Ký hiệu:

$$J_{i1}=(A_1,D_1,C_1),\quad \vert{}C_1\vert{}=n,\ \vert{}D_1\vert{}=n',\ \vert{}A_1\vert{}=n''.$$

$$J_{i2}=(A_2,D_2,C_2),\quad \vert{}C_2\vert{}=k,\ \vert{}D_2\vert{}=k',\ \vert{}A_2\vert{}=k''.$$

### 1.2. Information Processing Resources (IPR)
Cho $O$ là tập phép toán xử lý thông tin. Cho $R$ là tập ràng buộc tài nguyên. 

Khi đó: $$IPR=\{o\in O\mid R(o)\}.$$

### 1.3. Target
$$Target=(Reslt,Res_1,Res_2)$$

thỏa:

$$Res_1\vdash Reslt,\quad Res_2\vdash Reslt.$$

Target đạt được trong $J_{i1}$ nếu:

$$J_{i1}\vdash_{IPR} Res_1.$$

Target đạt được trong $J_{i2}$ nếu:

$$J_{i2}\vdash_{IPR} Res_2.$$



### 1.4. Reslt, Res_1, Res_2
Định nghĩa:

$$Th_{IPR}(J)=\{\varphi\mid J\vdash_{IPR}\varphi\}.$$

$Reslt$ là công thức thỏa:

$$Reslt\in Th_{IPR}(J)$$

với mọi hệ $J$ mà $J\vdash_{IPR} Reslt$.

$$Res_1\vdash Reslt,\quad Res_2\vdash Reslt.$$



### 1.5. Cawpg
$$Cawpg(J,Target,IPR)\iff C(J,Target,IPR)\neq\varnothing$$

trong đó $C(J,Target,IPR)$ là tập xung đột của bộ ba $(J,Target,IPR)$.

$$Feasible(J_{i1},Target,IPR)\iff J_{i1}\vdash_{IPR} Res_1.$$

$$Feasible(J_{i2},Target,IPR)\iff J_{i2}\vdash_{IPR} Res_2.$$

$$Cawpg(J,Target,IPR)\Rightarrow \neg Feasible(J,Target,IPR).$$



### 1.6. Phép biến đổi T
$$T:\mathcal{J}\times\mathcal{T}\times\mathcal{I}\to\mathcal{J}$$

$$T(J_{i1},Target,IPR)=J_{i2}.$$

Điều kiện:

$$Cawpg(J_{i1},Target,IPR),$$

$$\neg Feasible(J_{i1},Target,IPR),$$

$$\neg Cawpg(J_{i2},Target,IPR),$$

$$Feasible(J_{i2},Target,IPR),$$

$$J_{i2}\vdash_{IPR} Res_2,$$

$$Res_2\vdash Reslt.$$




## 2. Chi tiết

Cho $J_{i1}$ gồm $n$ hệ quả, $n'$ định nghĩa, $n''$ tiên đề.

Cho $J_{i2}$ gồm $k$ hệ quả, $k'$ định nghĩa, $k''$ tiên đề.

Yêu cầu $J_{i1}$ thỏa mãn $Target$ dưới $IPR$ để đạt $Res_1$:

$$Cawpg(J_{i1},Target,IPR),$$

$$\neg Feasible(J_{i1},Target,IPR).$$

Phép biến đổi:

$$T:(s_1,s_2,s_3)\mapsto J_{i2},$$

trong đó:

$$s_1=J_{i1},\quad s_2=Target,\quad s_3=IPR.$$

Yêu cầu $J_{i2}$ thỏa mãn $Target$ dưới $IPR$ để đạt $Res_2$:

$$\neg Cawpg(J_{i2},Target,IPR),$$

$$Feasible(J_{i2},Target,IPR).$$



## 3. Định lý

Nếu:

$$T(J_{i1},Target,IPR)=J_{i2},$$

$$Cawpg(J_{i1},Target,IPR),$$

$$\neg Feasible(J_{i1},Target,IPR),$$

$$\neg Cawpg(J_{i2},Target,IPR),$$

$$Feasible(J_{i2},Target,IPR),$$

$$J_{i2}\vdash_{IPR} Res_2,$$

$$Res_2\vdash Reslt,$$

thì:

$$Target\text{ đạt được trong }J_{i2},$$

$$Target\text{ không đạt được trong }J_{i1}.$$












