---
title: Wnioskowanie tabel
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 38709f91e01c7f85d9e8482bdd49bc0892121f09
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43528175"
---
# <a name="inferring-tables"></a>Wnioskowanie tabel
Podczas wnioskowania schematu dla <xref:System.Data.DataSet> z dokumentu XML ADO.NET najpierw określi, elementy XML, które reprezentują tabele. Następujące struktury XML wynik w tabeli **DataSet** schematu:  
  
-   Elementy z atrybutami  
  
-   Elementy z elementami podrzędnymi  
  
-   Powtarzalne elementy  
  
## <a name="elements-with-attributes"></a>Elementy z atrybutami  
 Elementy, które mają atrybuty określone w nich spowodować wywnioskować tabel. Na przykład rozważmy następujący kod XML:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 Procesu wnioskowania tworzy tabelę o nazwie "Element1."  
  
 **Zestaw danych:** elementu DocumentElement  
  
 **Tabela:** Element1  
  
|attr1|Element1_Text|  
|-----------|--------------------|  
|Wartość1||  
|Wartość2|TEXT1|  
  
## <a name="elements-with-child-elements"></a>Elementy z elementami podrzędnymi  
 Elementy, które mają wynik elementy podrzędne w wywnioskować tabel. Na przykład rozważmy następujący kod XML:  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 Procesu wnioskowania tworzy tabelę o nazwie "Element1."  
  
 **Zestaw danych:** elementu DocumentElement  
  
 **Tabela:** Element1  
  
|ChildElement1|  
|-------------------|  
|TEXT1|  
  
 Dokumentu lub katalogu głównego, element wynik tabeli wykrywany, jeśli ma on atrybutów lub elementów podrzędnych, które są wnioskowane jako kolumny. Jeśli element dokumentu ma żadnych atrybutów i nie elementy podrzędne, które będzie można wywnioskować jako kolumny, element jest wnioskowany jako **zestawu danych**. Na przykład rozważmy następujący kod XML:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 Procesu wnioskowania tworzy tabelę o nazwie "elementu DocumentElement".  
  
 **Zestaw danych:** NewDataSet  
  
 **Tabela:** elementu DocumentElement  
  
|element1|element2|  
|--------------|--------------|  
|TEXT1|Tekst2|  
  
 Można również rozważyć następujący kod XML:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 Tworzy procesu wnioskowania **DataSet** o nazwie elementu "DocumentElement", który zawiera tabelę o nazwie "Element1."  
  
 **Zestaw danych:** elementu DocumentElement  
  
 **Tabela:** Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|Wartość1|Wartość2|  
  
## <a name="repeating-elements"></a>Powtarzalne elementy  
 Elementy, które Powtórz wynik w jednej tabeli wykrywany. Na przykład rozważmy następujący kod XML:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 Procesu wnioskowania tworzy tabelę o nazwie "Element1."  
  
 **Zestaw danych:** elementu DocumentElement  
  
 **Tabela:** Element1  
  
|Element1_Text|  
|--------------------|  
|TEXT1|  
|Tekst2|  
  
## <a name="see-also"></a>Zobacz też  
 [Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Ładowanie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Ładowanie informacji o schemacie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Używanie języka XML w elemencie DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
