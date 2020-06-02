---
title: Pobieranie i modyfikowanie danych
description: W .NET Framework dostawcy danych w ADO.NET pełnią rolę mostka między aplikacją a źródłem danych, aby odczytywać i aktualizować dane.
ms.date: 03/30/2017
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.openlocfilehash: f916324dc829526a5e6b0078021b09786755f666
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286614"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a>Pobieranie i modyfikowanie danych ADO.NET
Podstawowa funkcja dowolnej aplikacji bazy danych nawiązuje połączenie ze źródłem danych i pobiera dane, które zawiera. .NET Framework dostawcy danych ADO.NET służy jako Most między aplikacją a źródłem danych, co umożliwia wykonywanie poleceń oraz pobieranie danych przy użyciu elementu **DataReader** lub **DataAdapter**. Kluczową funkcją dowolnej aplikacji bazy danych jest możliwość aktualizowania danych przechowywanych w bazie danych programu. W ADO.NET, aktualizowanie danych obejmuje użycie obiektów **DataAdapter** i i <xref:System.Data.DataSet> i **Command** może również wymagać korzystania z transakcji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Nawiązywanie połączenia ze źródłem danych](connecting-to-a-data-source.md)  
 Opisuje sposób nawiązywania połączenia ze źródłem danych i sposobu pracy ze zdarzeniami połączenia.  
  
 [Parametry połączenia](connection-strings.md)  
 Zawiera tematy opisujące różne aspekty używania parametrów połączenia, w tym słowa kluczowe parametrów połączenia, informacje zabezpieczające i przechowywania i pobierania.  
  
 [Buforowanie połączeń](connection-pooling.md)  
 Opisuje pule połączeń dla dostawców danych .NET Framework.  
  
 [Polecenia i parametry](commands-and-parameters.md)  
 Zawiera tematy opisujące sposób tworzenia poleceń i konstruktorów poleceń, konfigurowania parametrów oraz wykonywania poleceń w celu pobierania i modyfikowania danych.  
  
 [Elementy DataAdapter i DataReader](dataadapters-and-datareaders.md)  
 Zawiera tematy opisujące operacje odczytujące, dataadaptery, parametry, obsługa zdarzeń DataAdapter i wykonywanie operacji wsadowych.  
  
 [Transakcje i współbieżność](transactions-and-concurrency.md)  
 Zawiera tematy opisujące sposób wykonywania transakcji lokalnych, transakcji rozproszonych i pracy z optymistyczną współbieżnością.  
  
 [Pobieranie tożsamości lub wartości automatycznych numerów](retrieving-identity-or-autonumber-values.md)  
 Zawiera przykład mapowania wartości wygenerowanych dla kolumny **tożsamości** w tabeli SQL Server lub dla pola **AutoNumber** w tabeli programu Microsoft Access do kolumny wstawionego wiersza w tabeli. Omawia scalanie wartości tożsamości w `DataTable` .  
  
 [Pobieranie danych binarnych](retrieving-binary-data.md)  
 Opisuje sposób pobierania danych binarnych lub dużych struktur danych przy użyciu programu `CommandBehavior` .`SequentialAccess` Aby zmodyfikować zachowanie domyślne `DataReader` .  
  
 [Modyfikowanie danych za pomocą procedur składowanych](modifying-data-with-stored-procedures.md)  
 Opisuje, jak używać parametrów wejściowych procedury składowanej i parametrów wyjściowych, aby wstawić wiersz w bazie danych, zwracając nową wartość tożsamości.  
  
 [Pobieranie informacji o schemacie bazy danych](retrieving-database-schema-information.md)  
 Opisuje sposób uzyskiwania dostępnych baz danych lub wykazów, tabel i widoków w bazie danych, ograniczeń istniejących dla tabel oraz innych informacji o schemacie ze źródła danych.  
  
 [DbProviderFactories](dbproviderfactories.md)  
 Opisuje model fabryki dostawców i pokazuje, jak używać klas bazowych w `System.Data.Common` przestrzeni nazw.  
  
 [Śledzenie danych w ADO.NET](data-tracing.md)  
 Opisuje sposób, w jaki ADO.NET zapewnia wbudowaną funkcję śledzenia danych.  
  
 [Liczniki wydajności](performance-counters.md)  
 Opisuje liczniki wydajności dostępne dla `SqlClient` i `OracleClient` .  
  
 [Programowanie asynchroniczne](asynchronous-programming.md)  
 Opisuje obsługę ADO.NET w programowaniu asynchronicznym.  
  
 [Obsługa przesyłania strumieniowego SqlClient](sqlclient-streaming-support.md)  
 W tym artykule omówiono sposób pisania aplikacji, które przesyła strumieniowo dane z SQL Server bez całkowitego ładowania w pamięci.  
  
## <a name="see-also"></a>Zobacz także

- [Mapowanie typu danych w ADO.NET](data-type-mappings-in-ado-net.md)
- [Elementy DataSet, DataTable i DataView](./dataset-datatable-dataview/index.md)
- [Zabezpieczanie aplikacji ADO.NET](securing-ado-net-applications.md)
- [SQL Server i ADO.NET](./sql/index.md)
- [Omówienie ADO.NET](ado-net-overview.md)
