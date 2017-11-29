---
title: Ograniczenia (XSD) schematu XML mapowania do ograniczenia zestawu danych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9ac8e64c02d96450d41233cfbe65e1db839df9e7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
 [Ograniczenia unikalne schematu XML (XSD) mapy do ograniczenia zestawu danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Zawiera opis elementów schematu XML używany do tworzenia ograniczenia unique w **zestawu danych**.  
  
 [Mapowanie klucz ograniczenia schematu XML (XSD) do ograniczenia zestawu danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Zawiera opis elementów schematu XML używany do tworzenia ograniczeń klucza (ograniczenia unique, której wartości null nie są dozwolone) w **zestawu danych**.  
  
 [Mapa keyref ograniczeń schematu XML (XSD) do ograniczenia zestawu danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Zawiera opis elementów schematu XML używany do tworzenia keyref ograniczeń (klucz obcy) **zestawu danych**.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Wyprowadzanie relacyjne struktury zestawu danych z schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Opisuje relacyjne struktury lub schematu z **DataSet** która jest tworzona na podstawie schematu XSD.  
  
 [Generowanie relacji zestawu danych na podstawie schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 Zawiera opis elementów schematu XML używany do tworzenia relacji między kolumnami tabeli w **zestawu danych**.  
  
## <a name="see-also"></a>Zobacz też  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
