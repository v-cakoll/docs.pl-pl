---
title: Trwa pobieranie i modyfikowanie danych ADO.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 4ea157cd52bf92dace924baaa40f5b1bba6f13a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="retrieving-and-modifying-data-in-adonet"></a>Trwa pobieranie i modyfikowanie danych ADO.NET
Podstawową funkcją dowolnej aplikacji bazy danych jest połączenie ze źródłem danych i pobierania danych, które zawiera. Dostawcy danych .NET Framework ADO.NET służyć jako mostka między aplikacją a źródłem danych, co umożliwia wykonanie polecenia oraz do pobierania danych przy użyciu **DataReader** lub **element DataAdapter** . Funkcji klucza dowolnej aplikacji bazy danych jest możliwość aktualizacji są przechowywane w bazie danych. W ADO.NET, aktualizowanie danych polega na użyciu **element DataAdapter** i <xref:System.Data.DataSet>, i **polecenia** obiektów; i może również obejmować przy użyciu transakcji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Nawiązywanie połączenia ze źródłem danych](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 Opisuje sposób nawiązania połączenia ze źródłem danych oraz sposób pracy z zdarzeń połączenia.  
  
 [Parametry połączeń](../../../../docs/framework/data/adonet/connection-strings.md)  
 Zawiera tematy zawierająca opis różnych aspektów przy użyciu parametrów połączenia, w tym słowa kluczowe z parametrów połączenia, informacje zabezpieczające i przechowywania i pobierania ich.  
  
 [Pula połączeń](../../../../docs/framework/data/adonet/connection-pooling.md)  
 W tym artykule opisano tworzenie puli połączeń dla dostawcy danych .NET Framework.  
  
 [Polecenia i parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 Zawiera tematów opisujących sposób tworzenia poleceń i polecenia konstruktorów, skonfiguruj parametry i sposobu wykonania polecenia, aby pobrać i zmodyfikować danych.  
  
 [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 Zawiera tematy opisujące DataReaders, obiektów DataAdapter, parametry, obsługa zdarzeń element DataAdapter i wykonywanie operacji wsadowych.  
  
 [Transakcje i współbieżność](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 Zawiera tematy opisujące jak wykonywać transakcje lokalne transakcje rozproszone i pracować z optymistycznej współbieżności.  
  
 [Pobieranie tożsamości lub wartości automatycznych numerów](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 Przykład mapowania wartości wygenerowany dla **tożsamości** kolumny w [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] tabeli lub **automatycznie numerowane** pola w tabeli programu Microsoft Access z kolumną zawierającą wstawionego wiersza w tabeli. W tym artykule omówiono scalania wartości tożsamości w `DataTable`.  
  
 [Pobieranie danych binarnych](../../../../docs/framework/data/adonet/retrieving-binary-data.md)  
 Opisuje sposób pobrać dane binarne lub struktury dużej ilości danych przy użyciu `CommandBehavior`.`SequentialAccess` Aby zmodyfikować domyślne zachowanie `DataReader`.  
  
 [Modyfikowanie danych za pomocą procedur składowanych](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 Opisuje sposób użyj procedury składowanej parametry wejściowe i wyjściowe parametry, aby wstawić nowy wiersz w bazie danych, zwraca nową wartość tożsamości.  
  
 [Pobieranie informacji o schemacie bazy danych](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 W tym artykule opisano sposób uzyskiwania dostępnych baz danych lub katalogami, tabele i widoki w bazie danych ograniczenia występujące dla tabel i innych informacji o schemacie źródła danych.  
  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 W tym artykule opisano model fabryki dostawcy i przedstawiono sposób użycia klasy podstawowe w `System.Data.Common` przestrzeni nazw.  
  
 [Śledzenie danych w ADO.NET](../../../../docs/framework/data/adonet/data-tracing.md)  
 W tym artykule opisano, jak ADO.NET udostępnia dane wbudowana funkcja śledzenia.  
  
 [Liczniki wydajności](../../../../docs/framework/data/adonet/performance-counters.md)  
 Zawiera opis dostępnych dla liczników wydajności `SqlClient` i `OracleClient`.  
  
 [Programowanie asynchroniczne](../../../../docs/framework/data/adonet/asynchronous-programming.md)  
 W tym artykule opisano [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] obsługę programowania asynchronicznego.  
  
 [Obsługa przesyłania strumieniowego SqlClient](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md)  
 W tym artykule omówiono sposób pisania aplikacji, które strumienia danych z [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] bez konieczności jej pełni załadowanych do pamięci.  
  
## <a name="see-also"></a>Zobacz też  
 [Mapowanie typu danych w ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [Elementy DataSet, DataTable i DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Zabezpieczanie aplikacji ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server i ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
