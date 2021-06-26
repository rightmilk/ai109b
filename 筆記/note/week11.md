# 第十一週筆記

## 科學計算函式庫
### matplotlib - 繪圖工具
* subplot(x,y,z) row_x乘column_y張圖中的第z張。
### numpy - 數學矩陣運算
* import numpy as np
* np.arange(x,y) 從起始值到上限值。
* np.add(x,y) 兩矩陣相加。
* .shape() 回傳矩陣為幾乘幾陣列 .shape=(x,y) 重設矩陣維度。
* np.linspace(x,y,z) 從x~y分成z個。
* 可直接使用 a+b a*b a>b 等。
* a[x:y:z] a變數中大於等於x，小於y,一次取z單位。
* np.random.randint(0,10,6) 0~10取6個。
* np.linalg.det(x)求出x矩陣之行列式
### scupy - numpy 的擴充版
* from scipy import linalg , linalg.solve(A,B),解出A,B矩陣的特徵向量  
### sympy - 符號運算
* x,y = symbols('x y') : 建立變數x y  
* diff(x,y) : 對x做y微分
* integrate(x,y,z) 對x做積分，範圍是y~z  
* factor(x) : x做因式分解  
* expand(x) : 將x乘開  
* simplify(x) : 如果x有同類項將其合併  
* solve(x) : 求解x  
* sympy.sqrt(x) :將x開根號
### 其他
* eval() : ()內塞ax+b的表達式 並回傳結果  
* exp() :　指數函數  

