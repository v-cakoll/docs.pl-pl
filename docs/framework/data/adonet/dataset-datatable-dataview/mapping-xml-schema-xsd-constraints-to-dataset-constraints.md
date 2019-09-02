---
title: Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: b0082b534b8df10ac5277cf2f5aa5b2d2e40c11b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204622"
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet
Język definicji schematu XML (XSD) umożliwia określenie ograniczeń dla elementów i atrybutów, które definiuje. Podczas mapowania schematu XML na schemat relacyjny w programie <xref:System.Data.DataSet>ograniczenia schematu XML są mapowane na odpowiednie ograniczenia relacyjne dla tabel i kolumn w **zestawie danych**.  
  
 W tej sekcji omówiono mapowanie następujących ograniczeń schematu XML:  
  
- Ograniczenie unikatowości określone przy użyciu **unikatowego** elementu.  
  
- Ograniczenie klucza określone za pomocą elementu **Key** .  
  
- Ograniczenie keyref określone przy użyciu elementu **keyref** .  
  
 Przy użyciu ograniczenia dotyczącego elementu lub atrybutu należy określić pewne ograniczenia dotyczące wartości elementu w dowolnym wystąpieniu dokumentu. Na przykład ograniczenie klucza dla elementu podrzędnego **CustomerID** elementu **klienta** w schemacie wskazuje, że wartości elementu podrzędnego **CustomerID** muszą być unikatowe w każdym wystąpieniu dokumentu, a wartości null są niedozwolone.  
  
 Można również określić ograniczenia między elementami i atrybutami w dokumencie, aby określić relację w dokumencie. Ograniczenia Key i keyref są używane w schemacie, aby określić ograniczenia w dokumencie, co skutkuje relacją między elementami dokumentu a atrybutami.  
  
 Proces mapowania konwertuje te ograniczenia schematu na odpowiednie ograniczenia dotyczące tabel utworzonych w ramach **zestawu danych**.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Mapowanie ograniczeń unique schematu XML (XSD) na ograniczenia elementu DataSet](map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Opisuje elementy schematu XML używane do tworzenia unikatowych ograniczeń w **zestawie danych**.  
  
 [Mapowanie ograniczeń key schematu XML (XSD) na ograniczenia elementu DataSet](map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Opisuje elementy schematu XML używane do tworzenia ograniczeń klucza (unikatowych ograniczeń, w których wartości null są niedozwolone) w **zestawie danych**.  
  
 [Mapowanie ograniczeń keyref schematu XML (XSD) na ograniczenia elementu DataSet](map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Opisuje elementy schematu XML używane do tworzenia ograniczeń keyref (klucza obcego) w **zestawie danych**.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Opisuje strukturę relacyjną lub schemat **zestawu danych** , który jest tworzony na podstawie schematu XSD.  
  
 [Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)  
 Opisuje elementy schematu XML używane do tworzenia relacji między kolumnami tabeli w **zestawie danych**.  
  
## <a name="see-also"></a>Zobacz także

- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
