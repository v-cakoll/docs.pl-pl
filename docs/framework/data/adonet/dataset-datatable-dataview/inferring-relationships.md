---
title: Wnioskowanie relacji
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: 7dc3fb0c6098d636e640aaf52b72a404c1486492
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44705706"
---
# <a name="inferring-relationships"></a>Wnioskowanie relacji
Jeśli element, który jest wnioskowany jako tabela ma element podrzędny, która została wywnioskowana, także jako tabelę, <xref:System.Data.DataRelation> zostaną utworzone między dwiema tabelami. Nową kolumnę o nazwie **ParentTableName_Id** zostaną dodane do tabeli, który został utworzony dla elementu nadrzędnego i tabelę utworzoną dla elementu podrzędnego. **ColumnMapping** właściwość ta kolumna identity jest równa **MappingType.Hidden**. Kolumna będzie zwiększenie automatycznie klucz podstawowy dla tabeli nadrzędnej i będą używane dla **DataRelation** między dwiema tabelami. Typ danych w kolumnie tożsamości dodano będzie **System.Int32**, inaczej niż w przypadku wszystkich pozostałych kolumn wywnioskowane na typ danych, który jest **System.String**. A <xref:System.Data.ForeignKeyConstraint> z **DeleteRule** = **Cascade** zostanie również utworzony przy użyciu nowej kolumny w tabelach nadrzędne i podrzędne.  
  
 Na przykład rozważmy następujący kod XML:  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 Procesu wnioskowania dadzą dwie tabele: **Element1** i **ChildElement1**.  
  
 **Element1** tabela będzie zawierać dwie kolumny: **Element1_Id** i **ChildElement2**. **ColumnMapping** właściwość **Element1_Id** kolumna zostanie ustawiona **MappingType.Hidden**. **ColumnMapping** właściwość **ChildElement2** kolumna zostanie ustawiona **MappingType.Element**. **Element1_Id** kolumny zostanie ustawiony jako klucz podstawowy **Element1** tabeli.  
  
 **ChildElement1** tabela ma trzy kolumny: **attr1**, **attr2** i **Element1_Id**. **ColumnMapping** właściwość **attr1** i **attr2** kolumny zostaną ustawione **MappingType.Attribute**. **ColumnMapping** właściwość **Element1_Id** kolumna zostanie ustawiona **MappingType.Hidden**.  
  
 A **DataRelation** i **ForeignKeyConstraint** zostanie utworzona z użyciem **Element1_Id** kolumny z obu tabel.  
  
 **Zestaw danych:** elementu DocumentElement  
  
 **Tabela:** Element1  
  
|Element1_Id|ChildElement2|  
|------------------|-------------------|  
|0|Tekst2|  
  
 **Tabela:** ChildElement1  
  
|attr1|attr2|Element1_Id|  
|-----------|-----------|------------------|  
|Wartość1|Wartość2|0|  
  
 **DataRelation —:** Element1_ChildElement1  
  
 **ParentTable:** Element1  
  
 **ParentColumn:** Element1_Id  
  
 **ChildTable:** ChildElement1  
  
 **ChildColumn:** Element1_Id  
  
 **Zagnieżdżone:** True  
  
 **ForeignKeyConstraint:** Element1_ChildElement1  
  
 **Kolumna:** Element1_Id  
  
 **ParentTable:** Element1  
  
 **ChildTable:** ChildElement1  
  
 **DeleteRule:** kaskadowo  
  
 **AcceptRejectRule:** None  
  
## <a name="see-also"></a>Zobacz też  
 [Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Ładowanie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Ładowanie informacji o schemacie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Zagnieżdżanie elementów DataRelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 [Używanie języka XML w elemencie DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
