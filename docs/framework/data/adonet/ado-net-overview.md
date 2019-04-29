---
title: Omówienie ADO.NET
ms.date: 03/30/2017
ms.assetid: ee3bc1d8-11db-4be4-89eb-c708cf04117d
ms.openlocfilehash: 7ec3b5f4dd08a39f96ed28e6666fd4b00bced903
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607365"
---
# <a name="adonet-overview"></a>Omówienie ADO.NET
ADO.NET zapewnia spójny dostęp do źródeł danych, takie jak SQL Server i XML i źródła danych dostępne za pośrednictwem OLE DB i ODBC. Udostępnianie danych aplikacje komercyjne umożliwia ADO.NET nawiązać połączenie z tymi źródłami danych i pobierania, obsługiwać i zaktualizować dane, które zawierają.  
  
 Dostęp do danych w ADO.NET są oddzielone od manipulowanie danymi na osobne składniki, których można użyć pojedynczo lub w tandem. ADO.NET zawiera dostawcy danych .NET Framework do nawiązywania połączenia z bazą danych, wykonując polecenia i pobierania wyników. Te wyniki są albo przetwarzane bezpośrednio, umieszczone w ADO.NET <xref:System.Data.DataSet> obiektu w celu będzie widoczna dla użytkownika w sposób ad-hoc w połączeniu z danymi z wielu źródeł lub przekazywane między warstwami. `DataSet` Obiektu można również używać niezależnie od dostawcy danych .NET Framework do zarządzania danymi lokalne dla aplikacji lub skąd pochodzi z pliku XML.  
  
 Klasy ADO.NET znajdują się w System.Data.dll i są zintegrowane z usługą znalezione w System.Xml.dll klasy XML. Przykładowy kod, który nawiązuje połączenie z bazą danych, pobiera dane z niego, a następnie zostaną wyświetlone w oknie konsoli, zobacz [przykłady kodu ADO.NET](../../../../docs/framework/data/adonet/ado-net-code-examples.md).  
  
 ADO.NET oferuje funkcje dla deweloperów, którzy pisania kodu zarządzanego, które są podobne do funkcji dla deweloperów model (COM) obiektu składnika macierzystego ActiveX Data Objects (ADO). Zalecamy użycie programu ADO.NET, nie ADO do uzyskiwania dostępu do danych w aplikacjach .NET.  
  
 ADO.NET zapewnia najbardziej bezpośrednią metodę dostępu do danych w ramach programu .NET Framework. Na wyższym poziomie abstrakcji, który umożliwia aplikacjom pracować z modelu koncepcyjnego zamiast odpowiedni model magazynu, zobacz [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).  
  
 **Zasady zachowania poufności informacji**: Zestawy System.Data.dll, System.Data.Design.dll i System.Data.OracleClient.dll, System.Data.SqlXml.dll, System.Data.Linq.dll, System.Data.SqlServerCe.dll oraz System.Data.DataSetExtensions.dll nie dokonuje rozróżnienia między użytkownika -prywatne dane i dane prywatne.  Te zestawy nie zbierania, przechowywania lub transportu danych prywatnych dowolnego użytkownika. Jednak aplikacje innych firm mogą zbierać, przechowywania lub transportu przez użytkownika dane prywatne przy użyciu tych zestawów.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Architektura ADO.NET](../../../../docs/framework/data/adonet/ado-net-architecture.md)  
 Zawiera omówienie architektury i składników programu ADO.NET.  
  
 [Opcje technologii ADO.NET i wskazówki](../../../../docs/framework/data/adonet/ado-net-technology-options-and-guidelines.md)  
 Zawiera opis produktów i technologii zawartych z platformą danych jednostki.  
  
 [LINQ i ADO.NET](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 W tym artykule opisano, jak język Language-Integrated Query (LINQ) jest zaimplementowana w ADO.NET oraz linki do powiązanych tematów.  
  
 [Dostawcy danych .NET Framework](../../../../docs/framework/data/adonet/data-providers.md)  
 Zawiera omówienie projektu dostawcy danych .NET Framework, dostawcy danych .NET Framework, które znajdują się za pomocą narzędzia ADO.NET.  
  
 [Zestawy danych ADO.NET](../../../../docs/framework/data/adonet/ado-net-datasets.md)  
 Zawiera omówienie `DataSet` projektu i składników.  
  
 [Wykonywanie równoczesne w ADO.NET](../../../../docs/framework/data/adonet/side-by-side-execution.md)  
 W tym artykule omówiono różnice między wersjami programu ADO.NET i ich wpływ na zgodność aplikacji i wykonywanie side-by-side.  
  
 [Przykłady kodu ADO.NET](../../../../docs/framework/data/adonet/ado-net-code-examples.md)  
 Zawiera przykłady kodu, które pobierają dane przy użyciu dostawcy danych ADO.NET.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Nowości w programie ADO.NET](../../../../docs/framework/data/adonet/whats-new.md)  
 Zawiera funkcje, które są nowością w programie [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
 [Zabezpieczanie aplikacji ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 Opisuje bezpiecznego kodowania, gdy za pomocą platformy ADO.NET.  
  
 [Mapowanie typu danych w ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 Opisuje mapowanie typu danych między typami danych .NET Framework i dostawcy danych .NET Framework.  
  
 [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 W tym artykule opisano, jak połączyć się ze źródłem danych, pobieranie danych i modyfikować dane. Obejmuje to `DataReaders` i `DataAdapters`.  
  
## <a name="see-also"></a>Zobacz także

- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
- [Uzyskiwanie dostępu do danych w programie Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
