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
4.计算结束后，在Python文件夹下会出现test_calc.xls，该文件为计算结果。
![image](https://raw.githubusercontent.com/lj201112/Mineral-Formula-Calculation/master/img_folder/4.png)

##0x04数据结构及文件类型说明
由于矿物的EMPA数据成分可能会有小范围的交叉，因此没有做

            
            
            
            
