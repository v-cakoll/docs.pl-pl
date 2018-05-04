---
title: Wnioskowanie kolumn
ms.date: 03/30/2017
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
ms.openlocfilehash: da98bcbc4537e08a6f8565b36f8b84b476efd027
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="inferring-columns"></a>Wnioskowanie kolumn
Po ADO.NET stwierdził z dokumentu XML które elementy do wywnioskowania jako tabele dla <xref:System.Data.DataSet>, następnie wnioskuje kolumn dla tych tabel. ADO.NET 2.0 wprowadzono nowy aparat wnioskowania schematu, którego wnioskuje typ silnie typizowane dane dla każdego **simpleType** elementu. W poprzednich wersjach, dane typu wywnioskowane **simpleType** był zawsze **element xsd: String**.  
  
## <a name="migration-and-backward-compatibility"></a>Migracji i zgodności z poprzednimi wersjami  
 **ReadXml** metoda przyjmuje argument typu **InferSchema**. Ten argument można określić zachowanie wnioskowania zgodność z poprzednimi wersjami. Dostępne wartości **InferSchema** wyliczenie przedstawiono w poniższej tabeli.  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 Zapewnia zgodność z poprzednimi wersjami przez zawsze wnioskowanie typu prostego jako <xref:System.String>.  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 Wnioskuje typ silnie typizowane dane. Zgłasza wyjątek, jeśli jest używana z <xref:System.Data.DataTable>.  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 Ignoruje wszystkie wbudowanego schematu i odczytuje dane do istniejącego <xref:System.Data.DataSet> schematu.  
  
## <a name="attributes"></a>Atrybuty  
 Zgodnie z definicją w [wnioskowanie tabel](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md), będzie można wywnioskować elementu z atrybutami jako tabelę. Atrybuty elementu następnie będzie można wywnioskować jako kolumny w tabeli. **ColumnMapping** będzie mieć ustawioną właściwość kolumn **MappingType.Attribute**, aby upewnić się, że nazwy kolumn zostanie zapisany jako atrybuty Jeśli schemat nie są zapisywane do pliku XML. Wartości atrybutów są przechowywane w wiersza w tabeli. Rozważmy na przykład następujący kod XML:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 Proces wnioskowania spowoduje utworzenie tabeli o nazwie **Element1** z dwiema kolumnami, **attr1** i **attr2**. **ColumnMapping** właściwości obie kolumny zostanie ustawiona do **MappingType.Attribute**.  
  
 **Zestaw danych:** DocumentElement  
  
 **Tabela:** Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|Wartość1|Wartość2|  
  
## <a name="elements-without-attributes-or-child-elements"></a>Elementy bez atrybuty i elementy podrzędne  
 Jeśli element nie ma elementów podrzędnych ani atrybutów, będzie można wywnioskować jako kolumna. **ColumnMapping** będzie mieć ustawioną właściwość kolumny **MappingType.Element**. Tekst dla elementy podrzędne są przechowywane w wiersza w tabeli. Rozważmy na przykład następujący kod XML:  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 Proces wnioskowania spowoduje utworzenie tabeli o nazwie **Element1** z dwiema kolumnami, **ChildElement1** i **ChildElement2**. **ColumnMapping** właściwości obie kolumny zostanie ustawiona do **MappingType.Element**.  
  
 **Zestaw danych:** DocumentElement  
  
 **Tabela:** Element1  
  
|ChildElement1|ChildElement2|  
|-------------------|-------------------|  
|Tekst1|Tekst2|  
  
## <a name="see-also"></a>Zobacz też  
 [Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Ładowanie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Ładowanie informacji o schemacie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Używanie języka XML w elemencie DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
