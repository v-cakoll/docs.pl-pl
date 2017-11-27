---
title: Wnioskowanie tabel
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ae6f7827b7206544ff7547cc04f44b7cda34bef8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Wnioskowanie struktury zestawu danych relacyjnych z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Podczas ładowania zestawu danych z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Ładowanie informacji o schemacie zestawu danych z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Za pomocą języka XML w zestawie danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Zbiory danych, DataTables i DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
