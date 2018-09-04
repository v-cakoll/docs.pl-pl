---
title: Za pomocą języka XML w zestawie danych
ms.date: 03/30/2017
ms.assetid: 35138159-e199-49ec-baf7-1ec6777e171e
ms.openlocfilehash: cbdc6135a819e2141426f432d163cd49a7b78ac4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43489880"
---
# <a name="using-xml-in-a-dataset"></a>Za pomocą języka XML w zestawie danych
Za pomocą narzędzia ADO.NET można wypełnić <xref:System.Data.DataSet> ze strumienia XML lub dokumentu. Można użyć strumień XML lub dokument Dostarcz je do <xref:System.Data.DataSet> danych, informacje o schemacie lub obu. Informacje dostarczone z strumień XML lub dokumentu może być łączone z istniejące dane lub informacje o schemacie już istnieje w <xref:System.Data.DataSet>.  
  
 ADO.NET umożliwia również tworzenie Reprezentacja XML <xref:System.Data.DataSet>, z lub bez jego schematu, aby przetransportować <xref:System.Data.DataSet> między HTTP do użycia przez inną aplikację lub włączone XML platformy. W Reprezentacja XML <xref:System.Data.DataSet>, dane są zapisywane w pliku XML i schematu, jeśli jest wbudowane w reprezentacji, są zapisywane przy użyciu języka definicji schematu XML (XSD). XML i schematu XML zapewniają wygodny format przesyłania zawartości <xref:System.Data.DataSet> do i z klientów zdalnych.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Elementy DiffGram](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 Zawiera szczegółowe informacje na format XML używany do odczytywania i zapisywania zawartości w formacie DiffGram <xref:System.Data.DataSet>.  
  
 [Ładowanie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 W tym artykule omówiono różne opcje, które należy uwzględnić podczas ładowania zawartości <xref:System.Data.DataSet> z dokumentu XML.  
  
 [Zapisywanie zawartości elementu DataSet jako danych XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 W tym artykule omówiono sposób generowania zawartość <xref:System.Data.DataSet> jako danych XML i można użyć różnych opcji format XML.  
  
 [Ładowanie informacji o schemacie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 W tym artykule omówiono <xref:System.Data.DataSet> metody używane do ładowania schematu <xref:System.Data.DataSet> z pliku XML.  
  
 [Zapisywanie informacji o schemacie elementu DataSet jako pliku XSD](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-schema-information-as-xsd.md)  
 W tym artykule omówiono używa schematu XML oraz sposób wygenerowany na podstawie <xref:System.Data.DataSet>.  
  
 [Synchronizacja elementów DataSet i XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)  
 W tym artykule omówiono możliwości dostępne w programie .NET Framework synchronicznego dostępu do jednego zestawu danych relacyjnych i hierarchicznych widoków i pokazuje, jak utworzyć synchroniczne relacji między <xref:System.Data.DataSet> i <xref:System.Xml.XmlDataDocument>.  
  
 [Zagnieżdżanie elementów DataRelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 W tym artykule omówiono znaczenie zagnieżdżonych <xref:System.Data.DataRelation> obiekty podczas reprezentujący zawartość <xref:System.Data.DataSet> jako dane XML oraz sposób ich tworzenia.  
  
 [Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 W tym artykule opisano relacyjnej struktury lub schematu z <xref:System.Data.DataSet> , jest tworzona na podstawie schematu XML.  
  
 [Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 W tym artykule opisano wynikowy relacyjnej struktury lub schematu z <xref:System.Data.DataSet> utworzonego podczas wywnioskować na podstawie elementów XML.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Omówienie ADO.NET](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 W tym artykule opisano ADO.NET architektura i składniki i sposób ich użycia, dostęp do istniejących źródeł danych oraz do zarządzania danymi w aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
