---
title: Elementy DataAdapter i DataReaders
ms.date: 03/30/2017
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
ms.openlocfilehash: 6e711b11ef9a3eca53806b825f1e721169ab662d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516780"
---
# <a name="dataadapters-and-datareaders"></a>Elementy DataAdapter i DataReaders
Możesz użyć ADO.NET **DataReader** można pobrać tylko do odczytu, tylko do przodu strumienia danych z bazy danych. Wyniki są zwracane jako zapytanie wykonuje i są przechowywane w buforze sieci na komputerze klienckim, dopóki ich zażądać przy użyciu **odczytu** metody **DataReader**. Za pomocą **DataReader** może zwiększyć wydajność aplikacji, zarówno przez pobranie danych, jak tylko będzie dostępny, a (domyślnie) przechowywanie tylko jeden wiersz jednocześnie w pamięci, co zmniejsza obciążenie systemu.  
  
 A <xref:System.Data.Common.DataAdapter> służy do pobierania danych ze źródła danych i wypełnianie tabel w ramach <xref:System.Data.DataSet>. `DataAdapter` Rozwiązuje również zmiany wprowadzone do `DataSet` wstecz do źródła danych. `DataAdapter` Używa `Connection` obiekt dostawcy danych .NET Framework, aby nawiązać połączenie źródła danych i używa `Command` obiektów, aby pobrać dane i rozwiązać zmian w źródle danych.  
  
 Każdy dostawca danych .NET Framework, dołączone do programu .NET Framework ma <xref:System.Data.Common.DbDataReader> i <xref:System.Data.Common.DbDataAdapter> obiektu: obejmuje .NET Framework Data Provider for OLE DB <xref:System.Data.OleDb.OleDbDataReader> i <xref:System.Data.OleDb.OleDbDataAdapter> obiektu, dla programu .NET Framework Data Provider for SQL Server obejmuje <xref:System.Data.SqlClient.SqlDataReader> i <xref:System.Data.SqlClient.SqlDataAdapter> obiektu .NET Framework Data Provider for ODBC obejmuje <xref:System.Data.Odbc.OdbcDataReader> i <xref:System.Data.Odbc.OdbcDataAdapter> obiektu i .NET Framework Data Provider for Oracle obejmuje <xref:System.Data.OracleClient.OracleDataReader> i <xref:System.Data.OracleClient.OracleDataAdapter> obiektu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Pobieranie danych przy użyciu elementu DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)  
 W tym artykule opisano ADO.NET **DataReader** obiektu i jak z niej korzystać, aby zwrócić strumień, który wyników ze źródła danych.  
  
 [Wypełnianie zestawu danych z elementu DataAdapter](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 Zawiera opis sposobu wypełniania `DataSet` z tabel, kolumn i wierszy przy użyciu `DataAdapter`.  
  
 [Parametry elementu DataAdapter](../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 Opisuje sposób używania parametrów za pomocą właściwości polecenia `DataAdapter` jak zamapować zawartość kolumny w tym `DataSet` do parametru polecenia.  
  
 [Dodawanie istniejących ograniczeń do zestawu danych](../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 W tym artykule opisano sposób dodawania istniejące ograniczenia `DataSet`.  
  
 [Element DataAdapter DataTable i mapowania elementu DataColumn](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)  
 W tym artykule opisano sposób konfigurowania `DataTableMappings` i `ColumnMappings` dla `DataAdapter`.  
  
 [Stronicowanie za pośrednictwem wyniku zapytania](../../../../docs/framework/data/adonet/paging-through-a-query-result.md)  
 Przykład wyświetlania wyników zapytania jako strony danych.  
  
 [Aktualizowanie źródeł danych za pomocą elementów DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 Opisuje sposób używania `DataAdapter` rozpoznać zmian w `DataSet` w bazie danych.  
  
 [Obsługa zdarzeń elementu DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 W tym artykule opisano `DataAdapter` zdarzenia i sposobu ich używania.  
  
 [Wykonywanie operacji wsadowych za pomocą elementów DataAdapters](../../../../docs/framework/data/adonet/performing-batch-operations-using-dataadapters.md)  
 W tym artykule opisano zwiększanie wydajności aplikacji dzięki zmniejszeniu liczby rund do programu SQL Server podczas stosowania aktualizacji z `DataSet`.  
  
## <a name="see-also"></a>Zobacz też  
 [Nawiązywanie połączenia ze źródłem danych](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [Polecenia i parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Transakcje i współbieżność](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [Elementy DataSet, DataTable i DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
