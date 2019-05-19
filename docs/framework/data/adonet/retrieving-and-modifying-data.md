---
title: Pobieranie i modyfikowanie danych ADO.NET
ms.date: 03/30/2017
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.openlocfilehash: a5ac8fbd2a53d2670471c1ef5e59508f582ed944
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881432"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a>Pobieranie i modyfikowanie danych ADO.NET
Podstawową funkcją dowolnej aplikacji bazy danych jest łączenie ze źródłem danych i pobierania danych, które zawiera. Dostawcy danych .NET Framework ADO.NET, które służą jako Most między aplikacją a źródłem danych, co umożliwia wykonywanie poleceń również, aby pobierać dane przy użyciu **DataReader** lub **DataAdapter** . Funkcja klucza aplikacji bazy danych jest możliwość aktualizowania danych, która jest przechowywana w bazie danych. W ADO.NET, aktualizowanie danych polega na użyciu **DataAdapter** i <xref:System.Data.DataSet>, i **polecenia** obiektów; i może również obejmować za pomocą transakcji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Nawiązywanie połączenia ze źródłem danych](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 W tym artykule opisano, jak nawiązać połączenie ze źródłem danych oraz sposób pracy ze zdarzeniami połączenia.  
  
 [Parametry połączeń](../../../../docs/framework/data/adonet/connection-strings.md)  
 Zawiera tematy, zawierająca opis różnych aspektów przy użyciu parametrów połączenia, w tym słowa kluczowe z parametrów połączenia, informacje o zabezpieczeniach i przechowywanie i pobieranie ich.  
  
 [Pula połączeń](../../../../docs/framework/data/adonet/connection-pooling.md)  
 W tym artykule opisano tworzenie puli połączeń dla dostawcy danych .NET Framework.  
  
 [Polecenia i parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 Zawiera tematy, opisujący sposób tworzenia poleceń i polecenia konstruktorów, konfigurowania parametrów i sposób wykonywania polecenia, aby pobrać i zmodyfikować dane.  
  
 [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 Zawiera tematy opisujące DataReaders, elementów DataAdapters, parametry, obsługa zdarzeń elementu DataAdapter i wykonywanie operacji wsadowych.  
  
 [Transakcje i współbieżność](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 Zawiera tematów opisujących sposób wykonywania transakcji lokalnych transakcje rozproszone i pracować z optymistycznej współbieżności.  
  
 [Pobieranie tożsamości lub wartości automatycznych numerów](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 Stanowi przykład mapowania wartości wygenerowany **tożsamości** kolumny w tabeli programu SQL Server lub **automatycznie numerowane** pola w tabeli programu Microsoft Access z kolumną wstawionego wiersza w tabeli. W tym artykule omówiono scalania wartości tożsamości w `DataTable`.  
  
 [Pobieranie danych binarnych](../../../../docs/framework/data/adonet/retrieving-binary-data.md)  
 W tym artykule opisano sposób pobierania danych binarnych lub struktur dużych ilości danych za pomocą `CommandBehavior`.`SequentialAccess` Aby zmodyfikować domyślne zachowanie `DataReader`.  
  
 [Modyfikowanie danych za pomocą procedur składowanych](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 W tym artykule opisano, jak użyć procedury składowanej parametrów wejściowych i wyjściowych parametrami, aby wstawić wierszy w bazie danych, zwraca nową wartość tożsamości.  
  
 [Pobieranie informacji o schemacie bazy danych](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 W tym artykule opisano sposób uzyskiwania dostępnych baz danych lub katalogi, tabele i widoki bazy danych, ograniczenia występujące dla tabel i innych informacji o schemacie źródła danych.  
  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 W tym artykule opisano model fabryki dostawcy i pokazuje sposób użycia klasy bazowe w `System.Data.Common` przestrzeni nazw.  
  
 [Śledzenie danych w ADO.NET](../../../../docs/framework/data/adonet/data-tracing.md)  
 W tym artykule opisano, jak ADO.NET, zapewnia funkcja śledzenia danych wbudowane.  
  
 [Liczniki wydajności](../../../../docs/framework/data/adonet/performance-counters.md)  
 W tym artykule opisano dostępne dla liczników wydajności `SqlClient` i `OracleClient`.  
  
 [Programowanie asynchroniczne](../../../../docs/framework/data/adonet/asynchronous-programming.md)  
 W tym artykule opisano ADO.NET obsługę programowania asynchronicznego.  
  
 [Obsługa przesyłania strumieniowego SqlClient](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md)  
 W tym artykule omówiono sposób pisania aplikacji strumienia danych z programu SQL Server bez konieczności jego w pełni załadowany do pamięci.  
  
## <a name="see-also"></a>Zobacz także

- [Mapowanie typu danych w ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)
- [Elementy DataSet, DataTable i DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [Zabezpieczanie aplikacji ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [SQL Server i ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
