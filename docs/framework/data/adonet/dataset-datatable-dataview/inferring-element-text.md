---
title: Wnioskowanie tekstu elementu
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: d457985bfbec924748d1a418e318609b6837b9d2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745171"
---
# <a name="inferring-element-text"></a>Wnioskowanie tekstu elementu
Jeśli element zawiera tekst, a nie ma żadnych elementów podrzędnych, aby był wywnioskowany, ponieważ tabele takie jak (elementy przy użyciu atrybutów) lub powtarzalne elementy nową kolumnę o nazwie **TableName_Text** zostaną dodane do tabeli, która jest wnioskowany dla elementu. Tekst zawarty w elemencie zostaną dodane do wiersza w tabeli i przechowywane w nowej kolumnie. **ColumnMapping** właściwości nowej kolumny, która będzie równa **MappingType.SimpleContent**.  
  
 Na przykład rozważmy następujący kod XML.  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 Procesu wnioskowania będzie utworzyć tabelę o nazwie **Element1** zawierającą dwie kolumny: **attr1** i **Element1_Text**. **ColumnMapping** właściwość **attr1** kolumna zostanie ustawiona **MappingType.Attribute**. **ColumnMapping** właściwość **Element1_Text** kolumna zostanie ustawiona **MappingType.SimpleContent**.  
  
 **Zestaw danych:** Elementu DocumentElement  
  
 **Tabela:** element1  
  
|attr1|Element1_Text|  
|-----------|--------------------|  
|value1|TEXT1|  
  
 Jeśli element zawiera tekst, ale ma również elementy podrzędne, które zawierają tekst, nie można dodać kolumny do tabeli do przechowywania tekstu zawarte w elemencie. Tekst zawarty w elemencie będą ignorowane, gdy tekst w elementy podrzędne są objęte wiersza w tabeli. Na przykład rozważmy następujący kod XML.  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 Procesu wnioskowania będzie utworzyć tabelę o nazwie **Element1** z jedną kolumną o nazwie **ChildElement1**. Tekst dla **ChildElement1** element zostaną uwzględnione w wiersza w tabeli. Inne teksty zostaną zignorowane. **ColumnMapping** właściwość **ChildElement1** kolumna zostanie ustawiona **MappingType.Element**.  
  
 **Zestaw danych:** Elementu DocumentElement  
  
 **Tabela:** element1  
  
|ChildElement1|  
|-------------------|  
|Tekst2|  
  
## <a name="see-also"></a>Zobacz także
- [Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [Ładowanie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [Ładowanie informacji o schemacie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [Używanie języka XML w elemencie DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
