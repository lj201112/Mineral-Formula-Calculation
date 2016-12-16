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
本程序master.py以及main文件夹中的模块均使用python 2.7.11编写。程序使用了Numpy以及Pandas包。如果您需要使用本程序，请安装Numpy以及Pandas包。  
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
#####6.计算得出的原子数是以O原子数为基准的：  
+ 磁铁矿通式：AB2O4 ，计算结果以4个O为基准
+ 钛铁矿通式：ABO3，计算结果以3个O为基准
+ 橄榄石通式：R2[SiO4]，计算结果以4个O为基准
+ 辉石通式：XY[T2O6]，计算结果以6个O为基准
+ 长石通式：M[T4O8]，计算结果以8个O为基准
            
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
            
