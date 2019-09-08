---
title: Elementy DataAdapter i DataReader
ms.date: 03/30/2017
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
ms.openlocfilehash: 20c6d514e70d2e4db451e0fff02e72688bf7d0ba
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786651"
---
# <a name="dataadapters-and-datareaders"></a>Elementy DataAdapter i DataReader
Za pomocą elementu **DataReader** ADO.NET można pobrać strumień danych tylko do odczytu z bazy danych. Wyniki są zwracane w miarę wykonywania zapytania i są przechowywane w buforze sieciowym na kliencie do momentu zażądania ich przy użyciu metody **Read** elementu **DataReader**. Użycie elementu **DataReader** może zwiększyć wydajność aplikacji, pobierając dane natychmiast po ich udostępnieniu i (domyślnie) przechowując tylko jeden wiersz jednocześnie w pamięci, zmniejszając obciążenie systemu.  
  
 A <xref:System.Data.Common.DataAdapter> służy do pobierania danych ze źródła danych i wypełniania tabel <xref:System.Data.DataSet>w. Rozwiązuje również zmiany wprowadzone w odwrocie do źródła danych. `DataSet` `DataAdapter` Używa obiektu dostawcy danych .NET Framework do nawiązywania połączenia ze źródłem danych i używa `Command` obiektów do pobierania danych ze i rozwiązywania zmian w źródle danych. `Connection` `DataAdapter`  
  
 Każdy dostawca danych .NET Framework <xref:System.Data.Common.DbDataReader> dołączony do .NET Framework ma <xref:System.Data.Common.DbDataAdapter> obiekt a i: .NET Framework <xref:System.Data.OleDb.OleDbDataReader> dostawca danych dla <xref:System.Data.OleDb.OleDbDataAdapter> OLE DB zawiera obiekt i .NET Framework dostawca danych dla SQL <xref:System.Data.SqlClient.SqlDataReader> Serwer zawiera <xref:System.Data.OracleClient.OracleDataReader> a <xref:System.Data.SqlClient.SqlDataAdapter> i obiekt, <xref:System.Data.Odbc.OdbcDataReader> dostawca danych .NET Framework dla <xref:System.Data.Odbc.OdbcDataAdapter> ODBC zawiera obiekt i, a dostawca danych .NET Framework dla programu Oracle zawiera a i <xref:System.Data.OracleClient.OracleDataAdapter> obiekt.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Pobieranie danych przy użyciu elementu DataReader](retrieving-data-using-a-datareader.md)  
 Opisuje obiekt ADO.NET **DataReader** i sposób użycia go do zwrócenia strumienia wyników ze źródła danych.  
  
 [Wypełnianie zestawu danych z elementu DataAdapter](populating-a-dataset-from-a-dataadapter.md)  
 Opisuje sposób wypełniania `DataSet` tabelami, kolumnami i wierszami przy `DataAdapter`użyciu.  
  
 [Parametry elementu DataAdapter](dataadapter-parameters.md)  
 Opisuje sposób używania parametrów z właściwościami `DataAdapter` polecenia, `DataSet` w tym sposób mapowania zawartości kolumny w parametr do parametru polecenia.  
  
 [Dodawanie istniejących ograniczeń do zestawu danych](adding-existing-constraints-to-a-dataset.md)  
 Opisuje sposób dodawania istniejących ograniczeń do `DataSet`.  
  
 [Element DataAdapter DataTable i mapowania elementu DataColumn](dataadapter-datatable-and-datacolumn-mappings.md)  
 Opisuje sposób konfigurowania `DataTableMappings` i `ColumnMappings` dla programu `DataAdapter`.  
  
 [Stronicowanie za pośrednictwem wyniku zapytania](paging-through-a-query-result.md)  
 Przedstawia przykład wyświetlania wyników zapytania jako stron danych.  
  
 [Aktualizowanie źródeł danych za pomocą elementów DataAdapters](updating-data-sources-with-dataadapters.md)  
 Opisuje, jak za pomocą `DataAdapter` programu rozpoznać zmiany `DataSet` z powrotem do bazy danych.  
  
 [Obsługa zdarzeń elementu DataAdapter](handling-dataadapter-events.md)  
 Zawiera `DataAdapter` opis zdarzeń i sposobu ich używania.  
  
 [Wykonywanie operacji wsadowych za pomocą elementów DataAdapters](performing-batch-operations-using-dataadapters.md)  
 Opisuje zwiększenie wydajności aplikacji przez zredukowanie liczby rund do SQL Server podczas stosowania aktualizacji z programu `DataSet`.  
  
## <a name="see-also"></a>Zobacz także

- [Nawiązywanie połączenia ze źródłem danych](connecting-to-a-data-source.md)
- [Polecenia i parametry](commands-and-parameters.md)
- [Transakcje i współbieżność](transactions-and-concurrency.md)
- [Elementy DataSet, DataTable i DataView](./dataset-datatable-dataview/index.md)
- [Omówienie ADO.NET](ado-net-overview.md)
