import xml.etree.ElementTree as ET
import pandas as pd
import re
a=[]
n=[]


tree = ET.parse('file_name.xml')
root = tree.getroot()

#регулярное выражение рекомпилим для дальнейшего использования
regex= re.compile(r'^1.[0-9]{1,2}$')

#проходя нужный уровень, выбираем значения по регулярке, помещая в массив для дальнейшего рассчета
for child in root[1][0]:
    regex = re.compile(r'^1.[0-9]{1,2}$')
    rv = regex.match(child.attrib['НомПоПорРазд1'])
    if rv:
        a.append(child.attrib['НомПоПорРазд1'])
        n.append(int(child.attrib['ВелКредРискИтого']))
summa=sum(n)

#считаем HHI
col = ['col1', 'col2', 'col3', 'col4']
df = pd.DataFrame(index=a, columns=col)
df = df.fillna(0)
df['col1']=n
df['col2']=df['col1']/summa
df['col3']=df['col2']*100
df['col4']=pow(df['col3'], 2)
summa1=sum(df['col4'])
print(df)

print('HHI=', summa1)
