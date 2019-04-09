---
title: Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: a1690e99aeaeb7ed9c85fd28697ae22d34bb2018
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115651"
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet
Język definicji schematu XML (XSD) umożliwia ograniczenie zezwalające na można określić elementów i atrybutów, które definiuje. Podczas mapowania schematu XML na schemat relacyjny w <xref:System.Data.DataSet>, ograniczenia schematu XML są mapowane na odpowiednie ograniczenia relacyjnych tabel i kolumn w obrębie **zestawu danych**.  
  
 W tej sekcji omówiono mapowanie następujące ograniczenia schematu XML:  
  
-   Ograniczenie unikatowości określony za pomocą **unikatowy** elementu.  
  
-   Ograniczenie klucza określony za pomocą **klucz** elementu.  
  
-   Ograniczenie keyref określony za pomocą **keyref** elementu.  
  
 Za pomocą ograniczenia na element lub atrybut, można określić pewne ograniczenia na podstawie wartości elementu w żadnym wystąpieniu klasy dokumentu. Na przykład: ograniczenie klucza w **CustomerID** element podrzędny elementu **klienta** elementu w schemacie wskazuje, że wartości **CustomerID** musi mieć element podrzędny Unikatowy w żadnym wystąpieniu dokumentów i wartości null są niedozwolone.  
  
 Ograniczenia można również określić między elementów i atrybutów w dokumencie, aby możliwe było nawiązanie relacji w obrębie dokumentu. Ograniczenia klucza i keyref są używane w schemacie określanie ograniczeń w dokumencie skutkuje relację między dokumentu elementów i atrybutów.  
  
 Proces mapowania konwertuje te ograniczenia schematu na odpowiednie ograniczenia w tabelach, utworzone w ramach **zestawu danych**.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Mapowanie ograniczeń unique schematu XML (XSD) na ograniczenia elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Opisano elementy schematu XML, używany do tworzenia unikatowych ograniczeń w **zestawu danych**.  
  
 [Mapowanie ograniczeń key schematu XML (XSD) na ograniczenia elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Opisano elementy schematu XML użyty do utworzenia ograniczenia klucza (ograniczenia unikatowe, której wartości null są niedozwolone) **zestawu danych**.  
  
 [Mapowanie ograniczeń keyref schematu XML (XSD) na ograniczenia elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Opisano elementy schematu XML użyty do utworzenia keyref ograniczenia (z kluczem obcym) w **zestawu danych**.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 W tym artykule opisano relacyjnej struktury lub schematu z **DataSet** , jest tworzona na podstawie schematu XSD.  
  
 [Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 Opisano elementy schematu XML, używany do tworzenia relacji między kolumnami tabeli w **zestawu danych**.  
  
## <a name="see-also"></a>Zobacz także

- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
