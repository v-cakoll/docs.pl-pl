---
title: Ograniczenia (XSD) schematu XML mapowania do ograniczenia zestawu danych
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: 0a23e7a7ab6456125559ffd8fa19ffa5eba9335d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760989"
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a>Ograniczenia (XSD) schematu XML mapowania do ograniczenia zestawu danych
Język definicji schematu XML (XSD) umożliwia ograniczenia określonych elementów i atrybutów, który definiuje. Podczas mapowania schematu XML na schemat relacyjny w <xref:System.Data.DataSet>, ograniczenia schematu XML są mapowane na odpowiednich ograniczeń relacyjnych tabel i kolumn w **zestawu danych**.  
  
 W tej sekcji omówiono mapowanie schematu XML następujące ograniczenia:  
  
-   Ograniczenie unikatowości określona za pomocą **unikatowy** elementu.  
  
-   Ograniczenie klucza, określić przy użyciu **klucza** elementu.  
  
-   Ograniczenie keyref określona za pomocą **keyref** elementu.  
  
 Za pomocą ograniczenia na element lub atrybut, określeniu pewne ograniczenia w wartości elementu w żadnym wystąpieniu klasy dokumentu. Na przykład, ograniczenie klucza na **CustomerID** elementem podrzędnym **klienta** elementu w schemacie wskazuje, że wartości **CustomerID** musi być elementem podrzędnym Unikatowy w żadnym wystąpieniu dokumentów i wartości null są niedozwolone.  
  
 Ograniczenia można również określić między elementów i atrybutów w dokumencie, aby ustanowić relację, w tym dokumencie. Ograniczeń key i keyref są używane w schemacie można określić ograniczeń, w tym dokumencie, co w relacji między elementami dokumentu i atrybutów.  
  
 Proces mapowania konwertuje tych warunków ograniczających schematu na odpowiednie ograniczenia w tabelach utworzone w ramach **zestawu danych**.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Mapowanie ograniczeń unique schematu XML (XSD) na ograniczenia elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Zawiera opis elementów schematu XML używany do tworzenia ograniczenia unique w **zestawu danych**.  
  
 [Mapowanie ograniczeń key schematu XML (XSD) na ograniczenia elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Zawiera opis elementów schematu XML używany do tworzenia ograniczeń klucza (ograniczenia unique, której wartości null nie są dozwolone) w **zestawu danych**.  
  
 [Mapowanie ograniczeń keyref schematu XML (XSD) na ograniczenia elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Zawiera opis elementów schematu XML używany do tworzenia keyref ograniczeń (klucz obcy) **zestawu danych**.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Opisuje relacyjne struktury lub schematu z **DataSet** która jest tworzona na podstawie schematu XSD.  
  
 [Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 Zawiera opis elementów schematu XML używany do tworzenia relacji między kolumnami tabeli w **zestawu danych**.  
  
## <a name="see-also"></a>Zobacz też  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
