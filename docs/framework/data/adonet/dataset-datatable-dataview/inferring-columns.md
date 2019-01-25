---
title: Wnioskowanie kolumn
ms.date: 03/30/2017
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
ms.openlocfilehash: f3edd09b1fb8169e8f609514de38b3c37574079b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655234"
---
# <a name="inferring-columns"></a>Wnioskowanie kolumn
Po ADO.NET stwierdził z dokumentu XML które elementy, które działają jako tabele <xref:System.Data.DataSet>, następnie wnioskuje kolumn dla tych tabel. ADO.NET w wersji 2.0 wprowadzono nowy aparat wnioskowania schematu, który wnioskuje typ silnie typizowanych danych dla każdego **simpleType** elementu. W poprzednich wersjach, typ danych wnioskowanym **simpleType** element był to zawsze ciąg **element xsd: String**.  
  
## <a name="migration-and-backward-compatibility"></a>Migracja i zgodności z poprzednimi wersjami  
 **ReadXml** metoda przyjmuje argument typu **InferSchema**. Tego argumentu można określić zachowanie wnioskowania zgodność z poprzednimi wersjami. Dostępne wartości dla **InferSchema** wyliczenia są wyświetlane w poniższej tabeli.  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 Zapewnia zgodność z poprzednimi wersjami, zawsze wnioskowanie typu prostego jako <xref:System.String>.  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 Wnioskuje typ silnie typizowanych danych. Zgłasza wyjątek, jeśli używana z <xref:System.Data.DataTable>.  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 Ignoruje wszelkie wbudowanego schematu i odczytuje dane z istniejącymi <xref:System.Data.DataSet> schematu.  
  
## <a name="attributes"></a>Atrybuty  
 Zgodnie z definicją w [wnioskowanie tabel](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md), elementu z atrybutami zostanie wywnioskowany, jako tabelę. Atrybuty tego elementu następnie będzie można wywnioskować jako kolumny w tabeli. **ColumnMapping** właściwość kolumn zostanie ustawiona **MappingType.Attribute**, aby upewnić się, że nazwy kolumn zostanie zapisany jako atrybuty Jeśli schemat nie są zapisywane do pliku XML. Wartości atrybutów są przechowywane w wiersza w tabeli. Na przykład rozważmy następujący kod XML:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 Procesu wnioskowania będzie utworzyć tabelę o nazwie **Element1** z dwiema kolumnami **attr1** i **attr2**. **ColumnMapping** właściwość obie kolumny jest równa **MappingType.Attribute**.  
  
 **Zestaw danych:** Elementu DocumentElement  
  
 **Tabela:** element1  
  
|attr1|attr2|  
|-----------|-----------|  
|value1|value2|  
  
## <a name="elements-without-attributes-or-child-elements"></a>Elementy bez atrybutów lub elementów podrzędnych  
 Jeśli element nie ma elementów podrzędnych lub atrybuty, będzie można wywnioskować jako kolumny. **ColumnMapping** właściwości kolumny jest równa **MappingType.Element**. Tekst dla elementów podrzędnych są przechowywane w wiersza w tabeli. Na przykład rozważmy następujący kod XML:  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 Procesu wnioskowania będzie utworzyć tabelę o nazwie **Element1** z dwiema kolumnami **ChildElement1** i **ChildElement2**. **ColumnMapping** właściwość obie kolumny jest równa **MappingType.Element**.  
  
 **Zestaw danych:** Elementu DocumentElement  
  
 **Tabela:** element1  
  
|ChildElement1|ChildElement2|  
|-------------------|-------------------|  
|TEXT1|Tekst2|  
  
## <a name="see-also"></a>Zobacz także
- [Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [Ładowanie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [Ładowanie informacji o schemacie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [Używanie języka XML w elemencie DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
