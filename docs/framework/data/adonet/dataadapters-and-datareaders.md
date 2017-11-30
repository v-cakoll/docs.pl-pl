---
title: "Obiektów DataAdapter i DataReaders"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3e7a0af0b5fabdfacfcc825258242868b0fbb513
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="dataadapters-and-datareaders"></a>Obiektów DataAdapter i DataReaders
Można użyć ADO.NET **DataReader** do pobrania z bazy danych tylko do odczytu, tylko do przodu strumienia danych. Wyniki są zwracane jako zapytanie wykonuje i są przechowywane w buforze sieci na komputerze klienckim, dopóki ich zażądać przy użyciu **odczytu** metody **DataReader**. Przy użyciu **DataReader** może zwiększyć wydajność aplikacji, zarówno przez pobranie danych, jak jest dostępny i (domyślnie) przechowywania tylko jeden wiersz jednocześnie w pamięci, zmniejszając narzut systemu.  
  
 A <xref:System.Data.Common.DataAdapter> służy do pobierania danych ze źródła danych i wypełnić tabel w <xref:System.Data.DataSet>. `DataAdapter` Rozwiązuje również zmiany wprowadzone w `DataSet` do źródła danych. `DataAdapter` Używa `Connection` obiekt dostawcy danych .NET Framework do nawiązania połączenia źródła danych który używa `Command` obiektów można pobrać danych z i rozwiązać zmian w źródle danych.  
  
 Każdy dostawca danych programu .NET Framework uwzględnionych w programie .NET Framework ma <xref:System.Data.Common.DbDataReader> i <xref:System.Data.Common.DbDataAdapter> obiektu: .NET Framework Data Provider for OLE DB zawiera <xref:System.Data.OleDb.OleDbDataReader> i <xref:System.Data.OleDb.OleDbDataAdapter> obiektu dostawcy danych programu .NET Framework dla serwera SQL Serwer zawiera <xref:System.Data.SqlClient.SqlDataReader> i <xref:System.Data.SqlClient.SqlDataAdapter> obiekt dostawcy danych programu .NET Framework dla ODBC obejmuje <xref:System.Data.Odbc.OdbcDataReader> i <xref:System.Data.Odbc.OdbcDataAdapter> obiektu i .NET Framework Data Provider for Oracle obejmuje <xref:System.Data.OracleClient.OracleDataReader> i <xref:System.Data.OracleClient.OracleDataAdapter> obiektu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Podczas pobierania danych przy użyciu elementu DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)  
 W tym artykule opisano ADO.NET **DataReader** obiekt i jak z niego korzystać, aby zwrócić strumień wyniki ze źródła danych.  
  
 [Wypełnianie zestawu danych z element DataAdapter](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 Opisuje sposób wypełnienia `DataSet` z tabel, kolumn i wierszy za pomocą `DataAdapter`.  
  
 [Element DataAdapter parametrów](../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 Informacje dotyczące używania parametry z właściwościami polecenia `DataAdapter` sposób mapowania zawartości kolumny w tym `DataSet` do parametru polecenia.  
  
 [Dodawanie istniejących ograniczeń do zestawu danych](../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 Zawiera opis sposobu dodawania istniejącego ograniczeń do `DataSet`.  
  
 [Element DataAdapter DataTable i mapowania elementu DataColumn](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)  
 Zawiera opis sposobu konfigurowania `DataTableMappings` i `ColumnMappings` dla `DataAdapter`.  
  
 [Stronicowanie za pośrednictwem wyników z kwerendy](../../../../docs/framework/data/adonet/paging-through-a-query-result.md)  
 Przykład wyświetlania wyników zapytania jako strony danych.  
  
 [Aktualizowanie źródła danych za pomocą obiektów DataAdapter](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 Informacje dotyczące używania `DataAdapter` rozpoznać zmian w `DataSet` w bazie danych.  
  
 [Obsługa zdarzeń element DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 W tym artykule opisano `DataAdapter` zdarzenia i sposobu ich używania.  
  
 [Za pomocą obiektów DataAdapter operacji wsadowych.](../../../../docs/framework/data/adonet/performing-batch-operations-using-dataadapters.md)  
 Opisuje zwiększanie wydajności aplikacji dzięki zmniejszeniu liczby rund do serwera SQL podczas stosowania aktualizacji z `DataSet`.  
  
## <a name="see-also"></a>Zobacz też  
 [Połączenie ze źródłem danych](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [Poleceń i parametrów](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Transakcje i współbieżność](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [Zbiory danych, DataTables i DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
