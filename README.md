# Mineral-Formula-Calculation
Minerals formula calculations program based on major elements analysis

Created on 2016/12/15  
Author: LiJie  
Email: lj201112@163.com  
License: GNU Lesser General Public License (LGPL)

##0x01 介绍
Mineral-Formula-Calculation是一个计算EMPA数据的程序。该程序的功能：

* 计算矿物的Fe3+含量
* 计算分子中每种元素的原子数  

程序在Python文件夹下，文档结构如下：  

Python:  
&ensp;&ensp;&ensp;&ensp;&ensp;|--master.py 运行的主程序  
&ensp;&ensp;&ensp;&ensp;&ensp;|--main 包含计算文件的主文件夹  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;|--Magnetite.py 磁铁矿计算文件  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;|--Olivine.py 橄榄石结算文件  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;|--Pyroxene.py 辉石计算文件  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;|--Feldspar.py 长石计算文件  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;|--Ilmenite.py 钛铁矿计算文件  
            
##0x02 依赖关系
本程序master.py以及main文件夹中的模块均使用python 2.7.11编写。程序使用了Numpy以及Pandas库。如果您需要使用本程序，请安装Numpy以及Pandas包。  
您可以安装Python集成开发环境[Anaconda](https://www.continuum.io/downloads),或者安装Python包管理工具[pip](https://pip.pypa.io/en/stable/installing/)。
如果安装pip，则可以使用如下命令安装Numpy以及Pandas：
```
pip install numpy 
pip install pandas
```

##0x03使用方法
1.下载Python文件夹，将要计算的数据文件（以test.xls为例）放在Python文件夹中。  
![image](https://raw.githubusercontent.com/lj201112/Mineral-Formula-Calculation/master/img_folder/3.png)  
2运行终端（Windows下为cmd），找到Python文件夹所在的目录，运行
```python
python master.py
```  
3.根据提示，输入数据文件名称（包括扩展名）test.xls，按“回车”键开始计算。当计算结束后，再按下“回车”结束程序。  
![image](https://raw.githubusercontent.com/lj201112/Mineral-Formula-Calculation/master/img_folder/1.png)  
4.计算结束后，在Python文件夹下会出现test_calc.xls，该文件为计算结果。  
![image](https://raw.githubusercontent.com/lj201112/Mineral-Formula-Calculation/master/img_folder/4.png)  

##0x04数据结构及文件类型说明
由于矿物的EMPA数据成分可能会有小范围的交叉，因此没有实现根据成分自动归类的功能。  
#####1.本程序中EMPA所测的元素：
+ 磁铁矿: **SiO2, TiO2, Al2O3, FeO, MnO,	MgO, CaO, NiO, Cr2O3, V2O3**
+ 橄榄石: **SiO2, TiO2, Al2O3, FeO, MnO, MgO, CaO, NiO, Cr2O3**
+ 辉石:&ensp;&ensp; **SiO2, TiO2, Al2O3, FeO, MnO, MgO, CaO, &ensp;&ensp;&ensp;&ensp;&ensp;Cr2O3, K2O, Na2O**
+ 长石:&ensp;&ensp; **SiO2, TiO2, Al2O3,	FeO, MnO, MgO, CaO,&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp; K2O, Na2O**
+ 钛铁矿: **SiO2, TiO2, Al2O3, FeO, MnO,	MgO, CaO, NiO, Cr2O3, V2O3**（与磁铁矿相同）  

#####若您所测的数据与以上不同，请在源代码里添加或删减相应的变量参数，以免计算错误或程序出错。

#####2.请使用Excel 97-2003格式(.xls)文件，".xlsx"格式会出错。
#####3.数据表如图所示：  
![image](https://raw.githubusercontent.com/lj201112/Mineral-Formula-Calculation/master/img_folder/2.png)  
#####将EMPA数据按照矿物种类整理到不同的工作表中。  
#####每一个工作簿包含多个工作表，每种矿物数据放在一个工作表里，工作表名称请按规则重命名(双引号中的字符)，否则无法计算：
+ 磁铁矿："mag"
+ 橄榄石："ol"
+ 辉石："py"
+ 长石："fd"
+ 钛铁矿："ilm"  

#####工作表前后顺序对计算没有影响。  
#####4.数据请按照数据表中格式，第一列为顺序排列的序号，第二列及之后是元素名称，倒数第二列为"Total"表示总量，最后一行为"Comment"为备注。
#####一个数据表只能第一行为标题，不可有多行标题或者在数据中穿插标题。
#####注意：除了第一列，余下各列标题请除去多余空格。  
#####5.计算结果表如下图：  
![image](https://raw.githubusercontent.com/lj201112/Mineral-Formula-Calculation/master/img_folder/5.png)   
#####"Comment"前半部分数据为校准Fe3+后的数据(橄榄石没有计算Fe3+)，后半部分为校准后的百分化数据所求得的单个分子中元素的原子数。
#####6.Fe3+计算方法采用的是电价差法，橄榄石没有校准Fe3+。部分成分由于数据原因计算结果可能会产生负值，此时将TFeO全部看做FeO处理，认为成分中不含Fe2O3。
#####7.计算得出的原子数是以O原子数为基准的：  
+ 磁铁矿通式：AB2O4 ，计算结果以4个O为基准
+ 钛铁矿通式：ABO3，计算结果以3个O为基准
+ 橄榄石通式：R2[SiO4]，计算结果以4个O为基准
+ 辉石通式：XY[T2O6]，计算结果以6个O为基准
+ 长石通式：M[T4O8]，计算结果以8个O为基准
#####8.橄榄石的Fo、辉石的Mg#以及长石的Or、Ab、An是由原始数据计算而来，并不是经过百分化后计算的原子数得到的。
            
##0x05计算方法及代码解释
####以磁铁矿计算为例：
1.查找并计算出分子的相对分子质量：  
```python
SiO2_M = 28.086 + 15.999 * 2
    Al2O3_M = 26.982 * 2 + 15.999 * 3
    TiO2_M = 47.867 + 15.999 * 2
    FeO_M = 55.845 + 15.999
    Fe2O3_M = 55.845 * 2 + 15.999 * 3
    MnO_M = 54.938 + 15.999
    MgO_M = 24.305 + 15.999
    CaO_M = 40.078 + 15.999
    Na2O_M = 22.990 * 2 + 15.999
    K2O_M = 39.098 * 2 + 15.999
    NiO_M = 58.693 + 15.999
    V2O3_M = 50.942 * 2 + 15.999 * 3
    Cr2O3_M = 51.996 * 2 + 15.999 * 3
```
2.读取每一行中元素的质量百分数(wt%)：  
```python
    SiO2_wt = data[u'SiO2']
    Al2O3_wt = data[u'Al2O3']
    TiO2_wt = data[u'TiO2']
    TFeO_wt = data[u'FeO']
    MnO_wt = data[u'MnO'] 
    MgO_wt = data[u'MgO']
    CaO_wt = data[u'CaO'] 
    NiO_wt = data[u'NiO'] 
    V2O3_wt = data[u'V2O3'] 
    Cr2O3_wt= data[u'Cr2O3']
```
3.质量百分数除以相对分子质量，得到100g分子中的摩尔数目：  
```python
	SiO2_n = SiO2_wt / SiO2_M
    Al2O3_n = Al2O3_wt / Al2O3_M
    TiO2_n = TiO2_wt / TiO2_M
    TFeO_n = TFeO_wt / FeO_M
    MnO_n = MnO_wt / MnO_M
    MgO_n = MgO_wt / MgO_M
    CaO_n = CaO_wt / CaO_M
    NiO_n = NiO_wt / NiO_M
    V2O3_n = V2O3_wt / V2O3_M
    Cr2O3_n = Cr2O3_wt / Cr2O3_M
```
4.根据摩尔数，计算分子中阳离子的数目，并求出阳离子数目总和sum_ca：  
```python  
	SiO2_n = SiO2_wt / SiO2_M
    Al2O3_n = Al2O3_wt / Al2O3_M
    TiO2_n = TiO2_wt / TiO2_M
    TFeO_n = TFeO_wt / FeO_M
    MnO_n = MnO_wt / MnO_M
    MgO_n = MgO_wt / MgO_M
    CaO_n = CaO_wt / CaO_M
    NiO_n = NiO_wt / NiO_M
    V2O3_n = V2O3_wt / V2O3_M
    Cr2O3_n = Cr2O3_wt / Cr2O3_M
	sum_ca = SiO2_ca + Al2O3_ca + TiO2_ca + TFeO_ca + MnO_ca + MgO_ca + CaO_ca + NiO_ca + V2O3_ca + Cr2O3_ca
```  
5.根据电价差法计算Fe2+/Fe3+，磁铁矿通式为AB2O4，计算以3(A+B2)为基准的阳离子系数:  
```python
    ca_ratio = sum_ca / 3
    SiO2_co = SiO2_ca / ca_ratio
    Al2O3_co= Al2O3_ca / ca_ratio
    TiO2_co = TiO2_ca / ca_ratio
    TFeO_co = TFeO_ca / ca_ratio
    MnO_co = MnO_ca / ca_ratio
    MgO_co = MgO_ca / ca_ratio
    CaO_co = CaO_ca / ca_ratio
    NiO_co = NiO_ca / ca_ratio
    V2O3_co = V2O3_ca / ca_ratio
    Cr2O3_co = Cr2O3_ca / ca_ratio
```
ca_ratio表示阳离子系数，阳离子数/阳离子系数得到单位分子中的阳离子数(XX_co)。  
6.根据单位分子中的阳离子数计算单位分子中的正电荷总数sum_el：
```python
    SiO2_el = SiO2_co * 4
    Al2O3_el = Al2O3_co * 3
    TiO2_el = TiO2_co * 4
    TFeO_el = TFeO_co * 2
    MnO_el = MnO_co * 2
    MgO_el = MgO_co * 2
    CaO_el = CaO_co * 2
    NiO_el = NiO_co * 2
    V2O3_el = V2O3_co * 3
    Cr2O3_el = Cr2O3_co * 3
    sum_el = SiO2_el + Al2O3_el + TiO2_el + TFeO_el + MnO_el + MgO_el + CaO_el + NiO_el + V2O3_el + Cr2O3_el
```
7.理想磁铁矿分子中，阴离子的负电荷数为2 * 4 = 8 个负电荷，多余的负电荷可以认为是缺失Fe2O3造成的。则单位分子中Fe3+的阳离子数目等于多余的负电荷数，据此算出FeO wt%，以及Fe2O3 wt%。
```python
    Fe2O3_co = 8 - sum_el
    FeO_co = TFeO_co - Fe2O3_co
    Fe2O3_wt = Fe2O3_co * ca_ratio * Fe2O3_M / 2
    FeO_wt = FeO_co * ca_ratio * FeO_M
```
8.剩余氧法计算Fe2+/Fe3+。计算得到阴离子数目以及阴离子总数：
```python
    SiO2_an = SiO2_n * 2
    Al2O3_an = Al2O3_n * 3
    TiO2_an = TiO2_n * 2
    TFeO_an = TFeO_n
    MnO_an = MnO_n
    MgO_an = MgO_n
    CaO_an = CaO_n
    NiO_an = NiO_n
    V2O3_an = V2O3_n * 3
    Cr2O3_an = Cr2O3_n * 3
    sum_an = SiO2_an + Al2O3_an + TiO2_an + TFeO_an + MnO_an + MgO_an + CaO_an + NiO_an + V2O3_an + Cr2O3_an
```
9.以4个O为基准，根据阴离子系数求出单位分子中阴离子数目：
```python
    an_ratio = sum_an / 4
    SiO2_co2 = SiO2_ca / an_ratio
    Al2O3_co2= Al2O3_ca / an_ratio
    TiO2_co2 = TiO2_ca / an_ratio
    Fe2O3_co2 = (Fe2O3_wt / Fe2O3_M) * 2 / an_ratio
    FeO_co2 = FeO_wt / FeO_M / an_ratio
    TFeO_co2 = TFeO_ca / an_ratio
    MnO_co2 = MnO_ca / an_ratio
    MgO_co2 = MgO_ca / an_ratio
    CaO_co2 = CaO_ca / an_ratio
    NiO_co2 = NiO_ca / an_ratio
    V2O3_co2 = V2O3_ca / an_ratio
    Cr2O3_co2 = Cr2O3_ca / an_ratio 
```  
10.在剩余氧法计算中，磁铁矿理论的阳离子数与阴离子数比为3:4，理论阴离子数目为阳离子数目 * 4 / 3，实际少的氧原子数目则为Fe2O3的数目。  
如果Fe2O3与FeO具有相同的Fe含量，则质量比Fe2O3:FeO = 0.9。根据以上算出校准Fe3+后的质量总和。
```python
    O_re = sum_ca * 4 / 3 - sum_an
    Fe2O3_wt2 = O_re * Fe2O3_M
    FeO_wt2 = TFeO_wt - 0.9 * Fe2O3_wt2
	sum_wt = SiO2_wt + TiO2_wt + Al2O3_wt + Fe2O3_wt + FeO_wt + MnO_wt + MgO_wt + CaO_wt + NiO_wt + V2O3_wt + Cr2O3_wt
```
11.根据校准Fe3+后的质量，百分化后计算出以4个O为基准的原子数目：
```python
	SiO2_co3 = SiO2_wt / sum_wt * 100 / SiO2_M * 1 / an_ratio
    Al2O3_co3= Al2O3_wt / sum_wt * 100 / Al2O3_M * 2 / an_ratio
    TiO2_co3 = TiO2_wt / sum_wt * 100 / TiO2_M * 1 / an_ratio
    Fe2O3_co3 = Fe2O3_wt / sum_wt * 100 / Fe2O3_M * 2 / an_ratio
    FeO_co3 = FeO_wt / sum_wt * 100 / FeO_M * 1 / an_ratio
    MnO_co3 = MnO_wt / sum_wt * 100 / MnO_M * 1 / an_ratio
    MgO_co3 = MgO_wt / sum_wt * 100 / MgO_M * 1 / an_ratio
    CaO_co3 = CaO_wt / sum_wt * 100 / MgO_M * 1 / an_ratio
    NiO_co3 = NiO_wt / sum_wt * 100 / MgO_M * 1 / an_ratio
    V2O3_co3 = V2O3_wt / sum_wt * 100 / V2O3_M * 2 / an_ratio
    Cr2O3_co3 = Cr2O3_wt / sum_wt * 100 / Cr2O3_M * 2 /an_ratio
```

##0x06结语
从14年6月开始接触自学python到现在，已有两年多的时间，没有受过系统的学习训练，很多东西依旧不懂，包括这个程序都是本人翻书、网上检索以及参考别人的代码探索着写的。  

因为研究的需要，不想用excel重复地粘贴复制，决定用python写一个计算EMPA数据的程序。一是可以大量处理数据，二是看着代码能回快速想起来数据的计算方法，第三则是想用python写个程序锻炼下。断断续续自学了那么久的python，还从来没正经写过程序，这个算是处女作了。熟悉了python，体会到了pandas的强大，学会了使用git。编写程序整个过程带来的影响远大于代码本身，使自己向着心中的小目标迈出了小小一步。

写这个程序，前期后后花了1周多的时间。算法实现倒不难，理清思路写起来还是很快的。麻烦的是用pandas.DataFrame，为了写这个程序第一次接触pandas，各种问题，各种Error，让人很绝望，一度曾想放弃；写代码花费了不少的时间，这个算法在excel已经有过很多了，问过自己好多次，写这个有没有意义，最后还是坚持完成了，实现了绝大部分自己想要的功能。

很多事情，只要去做，就会有意义。想法在脑海里回顾一千遍，不如付诸行动一次来的实在。亡羊而补牢，未为迟也。





            
