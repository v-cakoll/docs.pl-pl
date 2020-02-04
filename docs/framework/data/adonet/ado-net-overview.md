---
title: Omówienie
ms.date: 03/30/2017
ms.assetid: ee3bc1d8-11db-4be4-89eb-c708cf04117d
ms.openlocfilehash: d5dc9cf7081c6876118914a0b95853a5a7ca5e57
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980343"
---
# <a name="adonet-overview"></a>Omówienie ADO.NET
ADO.NET zapewnia spójny dostęp do źródeł danych, takich jak SQL Server i XML, oraz źródeł danych udostępnianych za pośrednictwem OLE DB i ODBC. Aplikacje dla użytkowników korzystających z udostępniania danych mogą łączyć się z tymi źródłami danych przy użyciu programu ADO.NET, a także pobierać, obsługiwać i aktualizować zawarte w nich dane.  
  
 ADO.NET oddziela dostęp do danych z manipulowania danymi do odrębnych składników, które mogą być używane osobno lub wspólnie. ADO.NET zawiera .NET Framework dostawców danych do łączenia się z bazą danych, wykonywania poleceń i pobierania wyników. Wyniki są przetwarzane bezpośrednio, umieszczane w obiekcie ADO.NET <xref:System.Data.DataSet>, aby można było je uwidocznić dla użytkownika w trybie ad hoc, w połączeniu z danymi z wielu źródeł lub przekazywać między warstwami. Obiekt `DataSet` może być również używany niezależnie od dostawcy danych .NET Framework do zarządzania danymi lokalnymi w aplikacji lub źródłem z pliku XML.  
  
 Klasy ADO.NET są dostępne w pliku System. Data. dll i są zintegrowane z klasami XML znalezionymi w pliku System. XML. dll. W przypadku przykładowego kodu, który nawiązuje połączenie z bazą danych, pobiera z niej dane, a następnie wyświetla je w oknie konsoli, zobacz [przykłady kodu ADO.NET](ado-net-code-examples.md).  
  
 Funkcja ADO.NET zapewnia deweloperom, którzy piszą kod zarządzany podobny do funkcji udostępnianych przez deweloperów modelu COM (Component Object Model), przez ActiveX Data Objects (ADO). Zalecamy używanie ADO.NET, a nie ADO, do uzyskiwania dostępu do danych w aplikacjach .NET.  
  
 ADO.NET zapewnia najbardziej bezpośrednią metodę dostępu do danych w .NET Framework. W przypadku abstrakcji wyższego poziomu, która umożliwia aplikacjom współdziałanie z modelem koncepcyjnym, a nie z modelem magazynu bazowego, zobacz [ADO.NET Entity Framework](./ef/index.md).  
  
 **Privacy Statement**: The System.Data.dll, System.Data.Design.dll, System.Data.OracleClient.dll, System.Data.SqlXml.dll, System.Data.Linq.dll, System.Data.SqlServerCe.dll, and System.Data.DataSetExtensions.dll assemblies do not distinguish between a user's private data and non-private data.  Te zestawy nie zbierają, nie przechowują ani nie transportuje prywatnych danych użytkownika. Jednak aplikacje innych firm mogą zbierać, przechowywać i transportować prywatne dane użytkownika przy użyciu tych zestawów.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Architektura ADO.NET](ado-net-architecture.md)  
 Zawiera omówienie architektury i składników ADO.NET.  
  
 [Opcje technologii ADO.NET i wskazówki](ado-net-technology-options-and-guidelines.md)  
 Opisuje produkty i technologie dołączone do platformy danych jednostki.  
  
 [LINQ i ADO.NET](linq-and-ado-net.md)  
 Opisuje, jak program Language-Integrated Query (LINQ) jest zaimplementowany w programie ADO.NET i zawiera łącza do odpowiednich tematów.  
  
 [Dostawcy danych .NET Framework](data-providers.md)  
 Zawiera omówienie projektowania dostawcy danych .NET Framework i .NET Framework dostawców danych, które są dołączone do ADO.NET.  
  
 [Zestawy danych ADO.NET](ado-net-datasets.md)  
 Zawiera omówienie projektowania i składników `DataSet`.  
  
 [Wykonywanie równoczesne w ADO.NET](side-by-side-execution.md)  
 Omawia różnice w wersjach ADO.NET i ich wpływ na wykonywanie równoczesne i zgodność aplikacji.  
  
 [Przykłady kodu ADO.NET](ado-net-code-examples.md)  
 Udostępnia przykłady kodu, które pobierają dane przy użyciu dostawców danych ADO.NET.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Nowości w programie ADO.NET](whats-new.md)  
 Wprowadza funkcje, które są nowe w ADO.NET.  
  
 [Zabezpieczanie aplikacji ADO.NET](securing-ado-net-applications.md)  
 Zawiera opis bezpiecznych praktyk kodowania w przypadku korzystania z ADO.NET.  
  
 [Mapowanie typu danych w ADO.NET](data-type-mappings-in-ado-net.md)  
 Opisuje mapowania typu danych między .NET Framework typami danych i .NET Framework dostawcami danych.  
  
 [Pobieranie i modyfikowanie danych ADO.NET](retrieving-and-modifying-data.md)  
 Opisuje sposób nawiązywania połączenia ze źródłem danych, pobierania danych i modyfikowania danych. Obejmuje to `DataReaders` i `DataAdapters`.  
  
## <a name="see-also"></a>Zobacz także

- [ADO.NET](index.md)
- [Uzyskiwanie dostępu do danych w programie Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio)
