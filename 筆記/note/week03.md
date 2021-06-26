# 第三週筆記

## 遺傳演算法

* 遺傳演算法是是計算數學中用於解決最佳化的搜尋演算法，是進化演算法的一種。進化演算法最初是借鑑了進化生物學中的一些現象而發展起來的，這些現象包括遺傳、突變、自然選擇以及雜交等等。

### 原理
* 由於在選擇用於繁殖下一代的個體時，是根據個體對環境的適應度而決定其繁殖量的，故而有時也稱為非均勻再生(differential reproduction)。 這是在選中用於繁殖下一代的個體中，對兩個不同的個體的相同位置的基因進行交換，從而產生新的個體。

### 程式執行
```
#keyGa.py
from geneticAlgorithm import GeneticAlgorithm
import random

class KeyGA(GeneticAlgorithm):
    def __init__(self, key):
        super().__init__()
        self.key = key

    def randomChromosome(self): # 隨機產生一個染色體 (一個 16 位元的 01 字串)
        bits=[]
        for _ in range(len(self.key)):
            bit = str(random.randint(0,1))
            bits.append(bit)
        return ''.join(bits)
  
    def calcFitness(self, c): # 分數是和 key 一致的位元個數
        fitness=0
        for i in range(len(self.key)):
            fitness += 1 if c[i]==self.key[i] else 0
        return fitness
  
    def crossover(self, c1, c2):
        cutIdx = random.randint(0, len(c1)-1)
        head   = c1[0:cutIdx]
        tail   = c2[cutIdx:]
        return head + tail
    
    def mutate(self, chromosome): # 突變運算
        i=random.randint(0, len(chromosome)-1) # 選擇突變點
        cMutate = chromosome[0:i]+random.choice(['0','1'])+chromosome[i+1:] # 在突變點上隨機選取 0 或 1
        return cMutate # 傳回突變後的染色體

# 執行遺傳演算法，企圖找到 key，最多執行一百代，每代族群都是一百人
kga = KeyGA("1010101010101010")
kga.run(100, 20)
```
## 加密技術的範例
### 凱撒密碼 -- 字母位移法
* 凱撒密碼 (Caesar cipher) 是一種最簡單且最廣為人知的加密技術。凱撒密碼是一種替換加密技術，明文中的所有字母都在字母表上向後（或向前）按照一個固定數目進行偏移後被替換成密文。例如，當偏移量是3的時候，所有的字母A將被替換成D，B變成E，以此類推。這個加密方法是以羅馬共和時期凱撒的名字命名的，據稱當年凱撒曾用此方法與其將軍們進行聯繫。

### 互斥或密碼
* XOR 是是密碼學中一種簡單的加密演算法。
* 對於其本身來說，如果使用不斷重複的金鑰，利用頻率分析就可以破解這種簡單的互斥或密碼。如果訊息的內容被猜出或知道，金鑰就會泄露。互斥或密碼值得使用的原因主要是其易於實現，而且計算成本小。簡單重複互斥或加密有時用於不需要特別安全的情況下來隱藏資訊。