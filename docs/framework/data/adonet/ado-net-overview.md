---
title: "ADO.NET — omówienie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee3bc1d8-11db-4be4-89eb-c708cf04117d
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0857df4e4f7e12f78af6b91a76022bcaf94cc027
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="adonet-overview"></a>ADO.NET — omówienie
ADO.NET zapewnia spójny dostęp do źródeł danych, takich jak SQL Server i XML, a także do źródeł danych za pośrednictwem OLE DB i ODBC. Udostępnianie danych aplikacji użytkownika umożliwia ADO.NET połączenia z tych źródeł danych i pobrać, obsługi i aktualizować danych, które zawierają.  
  
 ADO.NET oddziela dostęp do danych z manipulowania danymi na osobne składniki, które mogą być używane pojedynczo lub w połączeniu. ADO.NET zawiera dostawcy danych .NET Framework dla połączenia z bazą danych, wykonywania poleceń i pobierania wyników. Wyniki są albo przetwarzane bezpośrednio, umieszczone w ADO.NET <xref:System.Data.DataSet> obiekt, aby zostać uwidoczniona dla użytkownika w sposób ad hoc, połączeniu z danymi z wielu źródeł lub przekazywane między warstwami. `DataSet` Obiektu można również użyć niezależnie od dostawcy danych .NET Framework do zarządzania dane lokalne aplikacji lub z XML.  
  
 Klasy ADO.NET znajdują się w System.Data.dll i są zintegrowane z klasami XML w System.Xml.dll. Aby uzyskać przykładowy kod, który nawiązuje połączenie z bazą danych, pobiera dane z niego, a następnie wyświetla dane w oknie konsoli, zobacz [przykłady kodu ADO.NET](../../../../docs/framework/data/adonet/ado-net-code-examples.md).  
  
 ADO.NET zapewnia funkcje dla deweloperów, którzy napisać kod zarządzany, które są podobne do funkcji dla deweloperów model (COM) obiektu składnik macierzysty przez obiektów ADO (ActiveX Data). Zalecane jest użycie ADO.NET, nie ADO do uzyskiwania dostępu do danych w aplikacjach .NET.  
  
 ADO.NET zapewnia najprostszą metodę dostępu do danych w programie .NET Framework. Na wyższym poziomie abstrakcji, który umożliwia aplikacjom obsługę model koncepcyjny zamiast odpowiedni model magazynu, zobacz [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).  
  
 **Privacy Statement**: The System.Data.dll, System.Data.Design.dll, System.Data.OracleClient.dll, System.Data.SqlXml.dll, System.Data.Linq.dll, System.Data.SqlServerCe.dll, and System.Data.DataSetExtensions.dll assemblies do not distinguish between a user's private data and non-private data.  Te zestawy nie zbierania, przechowywania lub transportu danych prywatnych dowolnego użytkownika. Jednak aplikacje innych firm mogą zbierać, przechowywania lub transportu prywatnych danych użytkownika za pomocą tych zestawów.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Architektura ADO.NET](../../../../docs/framework/data/adonet/ado-net-architecture.md)  
 Zawiera omówienie architektury i składników programu ADO.NET.  
  
 [Opcje technologii ADO.NET i wskazówki](../../../../docs/framework/data/adonet/ado-net-technology-options-and-guidelines.md)  
 Zawiera opis produktów i technologii zawartych w platformę danych jednostki.  
  
 [LINQ i ADO.NET](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 W tym artykule opisano, jak język Language-Integrated zapytania (LINQ) jest zaimplementowana w ADO.NET oraz linki do powiązanych tematów.  
  
 [Dostawcy danych .NET Framework](../../../../docs/framework/data/adonet/data-providers.md)  
 Omówienie projektowania dostawcy danych .NET Framework i dostawców danych .NET Framework, które są dołączone do ADO.NET.  
  
 [Zestawy danych ADO.NET](../../../../docs/framework/data/adonet/ado-net-datasets.md)  
 Zawiera omówienie `DataSet` projektowania i składniki.  
  
 [Wykonywanie równoczesne w ADO.NET](../../../../docs/framework/data/adonet/side-by-side-execution.md)  
 W tym artykule omówiono różnice w wersji ADO.NET i ich wpływ na wykonanie side-by-side oraz zgodności aplikacji.  
  
 [Przykłady kodu ADO.NET](../../../../docs/framework/data/adonet/ado-net-code-examples.md)  
 Zawiera przykłady kodu, które służą do pobierania danych przy użyciu dostawcy danych ADO.NET.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Nowości w programie ADO.NET](../../../../docs/framework/data/adonet/whats-new.md)  
 Zawiera funkcje, które są nowością w programie [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
 [Zabezpieczanie aplikacji ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 Opisuje bezpieczne praktyk kodowania, przy użyciu pakietu ADO.NET.  
  
 [Mapowanie typu danych w ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 Opisuje mapowanie typu danych między typami danych .NET Framework i dostawcy danych .NET Framework.  
  
 [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 Informacje dotyczące połączenia ze źródłem danych, pobieranie danych i modyfikowania danych. Obejmuje to `DataReaders` i `DataAdapters`.  
  
## <a name="see-also"></a>Zobacz też  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 [Uzyskiwanie dostępu do danych w programie Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
