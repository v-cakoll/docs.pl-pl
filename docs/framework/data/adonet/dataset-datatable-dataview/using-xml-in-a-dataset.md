---
title: "Za pomocą języka XML w zestawie danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35138159-e199-49ec-baf7-1ec6777e171e
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 28c1668dcb9678b65db62c0040adcd116221b92e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-xml-in-a-dataset"></a>Za pomocą języka XML w zestawie danych
Z ADO.NET możesz wpisać <xref:System.Data.DataSet> ze strumienia XML lub dokumentu. Strumień XML lub dokument można użyć do dostarczenia <xref:System.Data.DataSet> danych, informacje o schemacie lub obu. Informacje podane w strumieniu XML lub dokument można połączyć z istniejących danych i informacji o schemacie znajduje się już w <xref:System.Data.DataSet>.  
  
 ADO.NET umożliwia również tworzenie reprezentację XML <xref:System.Data.DataSet>, z lub bez jego schemat, aby przetransportować <xref:System.Data.DataSet> przez HTTP do użycia przez inną platformie włączone XML lub aplikacji. W reprezentacji XML <xref:System.Data.DataSet>, dane są zapisywane w pliku XML i schemat, jeśli jest dołączony wbudowany w reprezentacji, jest zapisywany przy użyciu języka definicji schematu XML (XSD). XML i schematu XML zapewniają wygodną format przesyłania zawartości <xref:System.Data.DataSet> do i z klientów zdalnych.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 Zawiera szczegółowe informacje na format XML używany do odczytu i zapisu zawartości w formacie DiffGram <xref:System.Data.DataSet>.  
  
 [Podczas ładowania zestawu danych z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 W tym artykule omówiono różne opcje, które należy uwzględnić podczas ładowania zawartości <xref:System.Data.DataSet> z dokumentu XML.  
  
 [Zapisywanie zawartości zestawu danych jako dane XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 W tym artykule omówiono sposób generowania zawartości <xref:System.Data.DataSet> jako dane XML i można użyć różnych opcji formatu XML.  
  
 [Ładowanie informacji o schemacie zestawu danych z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 W tym artykule omówiono <xref:System.Data.DataSet> metody używane do ładowania schematu <xref:System.Data.DataSet> z pliku XML.  
  
 [Zapisywanie informacji o schemacie zestawu danych jako XSD](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-schema-information-as-xsd.md)  
 W tym artykule omówiono zastosowania schematu XML i sposób generowania z <xref:System.Data.DataSet>.  
  
 [Zestaw danych i dokumentu XmlDataDocument synchronizacji](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)  
 Zawiera omówienie możliwości dostępnych w programie .NET Framework synchronicznego dostępu do widoków relacyjnych i hierarchicznych jednego zestawu danych, a pokazano, jak utworzyć synchroniczne relacji między <xref:System.Data.DataSet> i <xref:System.Xml.XmlDataDocument>.  
  
 [DataRelations zagnieżdżenia](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 W tym artykule omówiono znaczenie zagnieżdżonych <xref:System.Data.DataRelation> obiektów po reprezentujący zawartość <xref:System.Data.DataSet> danych XML oraz sposób ich tworzenia.  
  
 [Wyprowadzanie relacyjne struktury zestawu danych z schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Opisuje relacyjne struktury lub schematu z <xref:System.Data.DataSet> która jest tworzona na podstawie schematu XML.  
  
 [Wnioskowanie struktury zestawu danych relacyjnych z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 Opisuje wynikowy relacyjne struktury lub schematu z <xref:System.Data.DataSet> utworzonego podczas wywnioskować na podstawie elementów XML.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [ADO.NET — omówienie](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 W tym artykule opisano ADO.NET architektury i składników i sposobu ich używania dostęp do istniejących źródeł danych oraz do zarządzania danymi w aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Zbiory danych, DataTables i DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
