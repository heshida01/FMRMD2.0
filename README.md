## [mrmd2.0.py](http://lab.malab.cn:5001/MRMD2.0/Home)
 
#### 1. Installation：
We recommend using [miniconda3.4.3](https://repo.anaconda.com/miniconda/)(or python3.6), support linux,windows.  


  ```
  pip3 install -r requirements.txt --ignore-installed
  ```  

  ##### note:
  If the installation of a Windows user's mine package fails, download the corresponding version of the WHL file from [here](https://www.lfd.uci.edu/~gohlke/pythonlibs/) to install it.
  
 #### 2. usage
 Some important parameters are given below. For more parameter Settings, please refer to the relevant documents of [iFeature](https://github.com/Superzchen/iFeature) and [pse-in-one2.0](https://github.com/banshanren/Pse-in-One-2.0) authors. The parameter name of this program is basically the same as the name of the original program.
#### iFeature
|参数|取值|
|:-|:-|  
|--Inputfile|文件名需指定标签，如0.example.fasta代表标签为0|    
|--FE_method_file|['iFeature.py','iFeaturePseKRAAC.py']|   

当type(使用iFeature.py)且取值['AAC', 'EAAC', 'CKSAAP', 'DPC', 'DDE', 'TPC', 'BINARY', 'GAAC', 'EGAAC', 'CKSAAGP', 'GDPC', 'GTPC', 'AAINDEX', 'ZSCALE', 'BLOSUM62', 'NMBroto', 'Moran', 'Geary', 'CTDC', 'CTDT', 'CTDD', 'CTriad', 'KSCTriad', 'SOCNumber', 'QSOrder', 'PAAC', 'APAAC']时进行数据处理的一些命令的样例：
```
python Fmrmd2.0.py --InputFiles 1.positive.txt 0.negative.txt --FE_method iFeature.py --type AAC   
python Fmrmd2.0.py --InputFiles 1.positive.txt 0.negative.txt --FE_method iFeature.py --type CKSAAP  
python Fmrmd2.0.py --InputFiles 1.pos.fasta 0.neg.fasta --FE_method iFeature.py --type CTDC   
python Fmrmd2.0.py --InputFiles 1.pos.fasta 0.neg.fasta --FE_method iFeature.py --type DPC  
python Fmrmd2.0.py --InputFiles 1.pos.fasta 0.neg.fasta --FE_method iFeature.py --type DDE  
```

当type(使用iFeaturePseKRAAC.py)且取值['type1', 'type2', 'type3A', 'type3B', 'type4', 'type5', 'type6A', 'type6B', 'type6C', 'type7', 'type8', 'type9', 'type10', 'type11', 'type12', 'type13', 'type14', 'type15','type16']时进行数据处理的命令的样例：

```
python FMRMD2.0.py  --InputFiles 1.sc.fasta 0.sc.fasta --FE_method_file iFeaturePseKRAAC.py --type type1 --subtype lambda-correlation --gap_lambda 2 --raactype 5
```
*****************************

#### Pse-in-One 2.0
|参数|说明|
|:-|:-|  
|--Inputfile|文件名需指定标签，如0.example.fasta代表标签为0|    
|--FE_method_file|取值['nac.py,acc.py,pse.py,sc.py]|   
--sequeceType|取值['DNA','RNA','Protein']  
--method|method参数较为复杂，下面以单独的表格给出：
***************************
|参数--method说明|取值|
|:-|:-|  
|使用nac.py,无需指定输入数据的类型|['kmer','mismatch','subsequence']|    
|使用acc.py，输入数据为蛋白质序列|['AC', 'CC', 'ACC']|   
使用acc.py，输入数据为RNA序列|['DAC', 'DCC', 'DACC', 'TAC', 'TCC', 'TACC', 'MAC', 'GAC', 'NMBAC']
|使用acc.py，输入数据为DNA序列|['AC', 'CC', 'ACC']|  
|使用pse.py，输入数据为蛋白质序列|['PC-PseAAC', 'PC-PseAAC-General', 'SC-PseAAC', 'SC-PseAAC-General']|   
使用pse.py，输入数据为RNA序列|['PC-PseDNC-General', 'SC-PseDNC-General']  
使用pse.py，输入数据为DNA序列| ['PseDNC', 'PseKNC', 'PC-PseDNC-General', 'SC-PseDNC-General', 'PC-PseTNC-General', 'SC-PseTNC-General']
使用sc.py，输入数据为RNA序列| ['Triplet','PseSSC','PscDPC']  

备注sc.py中蛋白质和DNA序列不能使用,并且格式比较特殊，数据格式可以参考experimental_data目录中提供的样例

****************************
使用Pse-in-One进行数据处理的一些命令的样例：
   ```
python Fmrmd2.0.py --InputFiles 1.example.txt 0.example.txt --FE_method_file nac.py --sequenceType RNA --method kmer --k 3  
python Fmrmd2.0.py --InputFiles 1.example.txt 0.example.txt --FE_method_file nac.py --sequenceType RNA --method Mismatch     
python Fmrmd2.0.py --InputFiles 1.example.txt 0.example.txt --FE_method_file nac.py --sequenceType RNA --method kmer --k 53   
python Fmrmd2.0.py --InputFiles 1.example.fasta 0.example.fasta --FE_method_file nac.py --sequenceType Protein --method kmer --k 3  
python Fmrmd2.0.py --InputFiles 1.example.fasta 0.example.fasta --FE_method_file acc.py --sequenceType Protein --method ACC  
python Fmrmd2.0.py --InputFiles 1.example.fasta 0.example.fasta --FE_method_file acc.py --sequenceType Protein --method AC  
python Fmrmd2.0.py --InputFiles 1.example.fasta 0.example.fasta --FE_method_file acc.py --sequenceType Protein --method CC 
python Fmrmd2.0.py --InputFiles 1.rna.fasta 0.rna.fasta --FE_method_file acc.py --sequenceType RNA --method DAC 
python Fmrmd2.0.py --InputFiles 1.rna.fasta 0.rna.fasta --FE_method_file acc.py --sequenceType RNA --method DACC  
python Fmrmd2.0.py --InputFiles 1.rna.fasta 0.rna.fasta --FE_method_file acc.py --sequenceType RNA --method MAC  
python Fmrmd2.0.py --InputFiles 1.rna.fasta 0.rna.fasta --FE_method_file acc.py --sequenceType RNA --method NMBAC  
python Fmrmd2.0.py --InputFiles 1.rna.fasta 0.rna.fasta --FE_method_file pse.py --sequenceType RNA --method PC-PseDNC-General  
   ```


If you have any questions.please contact me (heshida@tju.edu.cn)
