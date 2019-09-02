---
title: Używanie języka XML w elemencie DataSet
ms.date: 03/30/2017
ms.assetid: 35138159-e199-49ec-baf7-1ec6777e171e
ms.openlocfilehash: ba68f0fbe84a9877596ddfefd56f71a5889cf8de
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203144"
---
# <a name="using-xml-in-a-dataset"></a>Używanie języka XML w elemencie DataSet
Za pomocą ADO.NET można wypełniać <xref:System.Data.DataSet> z poziomu strumienia lub dokumentu XML. Możesz użyć strumienia XML lub dokumentu, aby dostarczyć <xref:System.Data.DataSet> dane, informacje o schemacie lub oba te elementy. Informacje dostarczone ze strumienia lub dokumentu XML mogą być łączone z istniejącymi danymi lub informacjami o schemacie, które <xref:System.Data.DataSet>już znajdują się w.  
  
 ADO.NET umożliwia również tworzenie reprezentacji <xref:System.Data.DataSet>XML, z lub bez jej schematu, w celu przetransportowania protokołu HTTP w celu użycia przez inną aplikację lub platformę z <xref:System.Data.DataSet> obsługą kodu XML. W reprezentacji <xref:System.Data.DataSet>XML, dane są zapisywane w języku XML i schemacie, jeśli są zawarte w tekście w reprezentacji, są zapisywane przy użyciu języka definicji schematu XML (XSD). Schemat XML i XML zapewniają wygodny format do przesyłania zawartości <xref:System.Data.DataSet> do i z klientów zdalnych.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Elementy DiffGram](diffgrams.md)  
 Zawiera szczegóły w formacie DiffGram, format XML używany do odczytywania i zapisywania zawartości <xref:System.Data.DataSet>.  
  
 [Ładowanie elementu DataSet z pliku XML](loading-a-dataset-from-xml.md)  
 Omawia różne opcje, które należy wziąć pod uwagę podczas ładowania <xref:System.Data.DataSet> zawartości z dokumentu XML.  
  
 [Zapisywanie zawartości elementu DataSet jako danych XML](writing-dataset-contents-as-xml-data.md)  
 W tym artykule omówiono sposób generowania zawartości <xref:System.Data.DataSet> jako dane XML i różne opcje formatu XML, których można użyć.  
  
 [Ładowanie informacji o schemacie elementu DataSet z pliku XML](loading-dataset-schema-information-from-xml.md)  
 Omawia metody używane do ładowania schematu <xref:System.Data.DataSet> z pliku XML. <xref:System.Data.DataSet>  
  
 [Zapisywanie informacji o schemacie elementu DataSet jako pliku XSD](writing-dataset-schema-information-as-xsd.md)  
 W tym artykule omówiono sposób użycia schematu XML i sposób generowania go z <xref:System.Data.DataSet>.  
  
 [Synchronizacja elementów DataSet i XmlDataDocument](dataset-and-xmldatadocument-synchronization.md)  
 Omawia możliwości dostępne w .NET Framework synchronicznego dostępu do zarówno widoków relacyjnych, jak i hierarchicznych jednego zestawu danych, a następnie pokazuje, jak utworzyć relację synchroniczną między <xref:System.Data.DataSet> <xref:System.Xml.XmlDataDocument>i.  
  
 [Zagnieżdżanie elementów DataRelation](nesting-datarelations.md)  
 Omawia znaczenie zagnieżdżonych <xref:System.Data.DataRelation> obiektów podczas reprezentowania zawartości <xref:System.Data.DataSet> jako dane XML i zawiera opis sposobu ich tworzenia.  
  
 [Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Opisuje strukturę relacyjną lub schemat, <xref:System.Data.DataSet> który został utworzony na podstawie schematu XML.  
  
 [Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML](inferring-dataset-relational-structure-from-xml.md)  
 Opisuje powstałą strukturę relacyjną lub schemat, <xref:System.Data.DataSet> który jest tworzony podczas wywnioskowanych z elementów XML.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Omówienie ADO.NET](../ado-net-overview.md)  
 Opisuje architekturę i składniki ADO.NET oraz sposób ich używania do uzyskiwania dostępu do istniejących źródeł danych oraz zarządzania danymi aplikacji.  
  
## <a name="see-also"></a>Zobacz także

- [Elementy DataSet, DataTable i DataView](index.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
