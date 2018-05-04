---
title: Wnioskowanie tabel
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: b14cbc39b02136ac7f226faf2636a69ac072f529
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="inferring-tables"></a>Wnioskowanie tabel
Gdy wnioskowanie schematu dla <xref:System.Data.DataSet> z dokumentu XML ADO.NET najpierw określi, elementy XML, które reprezentują tabel. Następujące struktury XML powoduje tabelę dla **DataSet** schematu:  
  
-   Elementy z atrybutami  
  
-   Elementów z elementów podrzędnych  
  
-   Powtarzających się elementów  
  
## <a name="elements-with-attributes"></a>Elementy z atrybutami  
 Elementów, które mają atrybuty określone w nich spowodować wywnioskować tabel. Rozważmy na przykład następujący kod XML:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 Proces wnioskowania spowoduje utworzenie tabeli o nazwie "Element1."  
  
 **Zestaw danych:** DocumentElement  
  
 **Tabela:** Element1  
  
|attr1|Element1_Text|  
|-----------|--------------------|  
|Wartość1||  
|Wartość2|Tekst1|  
  
## <a name="elements-with-child-elements"></a>Elementów z elementów podrzędnych  
 Elementów, które mają wynik elementów podrzędnych w wywnioskować tabel. Rozważmy na przykład następujący kod XML:  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 Proces wnioskowania spowoduje utworzenie tabeli o nazwie "Element1."  
  
 **Zestaw danych:** DocumentElement  
  
 **Tabela:** Element1  
  
|ChildElement1|  
|-------------------|  
|Tekst1|  
  
 Dokument lub kluczu głównym elementu wynik tabeli wykrywany, jeśli ma ona atrybuty i elementy podrzędne, które są wywnioskować jako kolumny. Jeśli element dokumentu nie atrybutów i nie elementy podrzędne, które będzie można wywnioskować jako kolumny, element jest wywnioskowany jako **zestawu danych**. Rozważmy na przykład następujący kod XML:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 Proces wnioskowania spowoduje utworzenie tabeli o nazwie "DocumentElement".  
  
 **Zestaw danych:** NewDataSet  
  
 **Tabela:** DocumentElement  
  
|Element1|Element2|  
|--------------|--------------|  
|Tekst1|Tekst2|  
  
 Możesz też wziąć pod uwagę następujące XML:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 W procesie wnioskowania **DataSet** o nazwie "DocumentElement", który zawiera tabeli o nazwie "Element1."  
  
 **Zestaw danych:** DocumentElement  
  
 **Tabela:** Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|Wartość1|Wartość2|  
  
## <a name="repeating-elements"></a>Powtarzające się elementy  
 Elementy, które Powtórz wynik w jednej tabeli wywnioskowany. Rozważmy na przykład następujący kod XML:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 Proces wnioskowania spowoduje utworzenie tabeli o nazwie "Element1."  
  
 **Zestaw danych:** DocumentElement  
  
 **Tabela:** Element1  
  
|Element1_Text|  
|--------------------|  
|Tekst1|  
|Tekst2|  
  
## <a name="see-also"></a>Zobacz też  
 [Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Ładowanie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Ładowanie informacji o schemacie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Używanie języka XML w elemencie DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
