---
title: Wnioskowanie relacji
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: 9833966fa5a16bef70a6ae2b9ca618fde0e05fbb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759039"
---
# <a name="inferring-relationships"></a>Wnioskowanie relacji
Jeśli element, który jest wywnioskowany jako tabela ma element podrzędny, która jest również wykryta jako tabelę, <xref:System.Data.DataRelation> zostanie utworzona między dwiema tabelami. Nową kolumnę o nazwie **ParentTableName_Id** zostaną dodane do tabeli utworzony dla elementu nadrzędnego oraz tabela utworzona dla elementu podrzędnego. **ColumnMapping** zostanie ustawiona właściwość tej kolumny tożsamości do **MappingType.Hidden**. Kolumna będzie zwiększanie automatycznie klucz podstawowy dla tabeli nadrzędnej i będzie służyć do **DataRelation** między dwiema tabelami. Typ danych kolumny tożsamości dodano będzie **System.Int32**, w odróżnieniu od typu danych wszystkie inne wnioskowany kolumny, która jest **System.String**. A <xref:System.Data.ForeignKeyConstraint> z **DeleteRule** = **Cascade** zostanie utworzony również w tabelach nadrzędne i podrzędne za pomocą nowej kolumny.  
  
 Rozważmy na przykład następujący kod XML:  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 Proces wnioskowania spowoduje utworzenie dwóch tabel: **Element1** i **ChildElement1**.  
  
 **Element1** tabela będzie mieć dwie kolumny: **Element1_Id** i **ChildElement2**. **ColumnMapping** właściwość **Element1_Id** kolumny zostanie ustawiona do **MappingType.Hidden**. **ColumnMapping** właściwość **ChildElement2** kolumny zostanie ustawiona do **MappingType.Element**. **Element1_Id** kolumny zostanie ustawione jako klucz podstawowy **Element1** tabeli.  
  
 **ChildElement1** tabela będzie miała trzy kolumny: **attr1**, **attr2** i **Element1_Id**. **ColumnMapping** właściwość **attr1** i **attr2** kolumn zostanie ustawiona do **MappingType.Attribute**. **ColumnMapping** właściwość **Element1_Id** kolumny zostanie ustawiona do **MappingType.Hidden**.  
  
 A **DataRelation** i **ForeignKeyConstraint** zostanie utworzona z użyciem **Element1_Id** kolumny z obu tabel.  
  
 **Zestaw danych:** DocumentElement  
  
 **Tabela:** Element1  
  
|Element1_Id|ChildElement2|  
|------------------|-------------------|  
|0|Tekst2|  
  
 **Tabela:** ChildElement1  
  
|attr1|attr2|Element1_Id|  
|-----------|-----------|------------------|  
|Wartość1|Wartość2|0|  
  
 **DataRelation:** Element1_ChildElement1  
  
 **ParentTable:** Element1  
  
 **ParentColumn:** Element1_Id  
  
 **ChildTable:** ChildElement1  
  
 **ChildColumn:** Element1_Id  
  
 **Zagnieżdżone:** wartość True  
  
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
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
