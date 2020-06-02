---
title: Elementy DataAdapter i DataReader
description: Dowiedz się więcej o ADO.NET elemencie DataReader, który pobiera dane z bazy danych i DataAdapter, która pobiera dane ze źródła danych i wypełnia zestaw danych.
ms.date: 03/30/2017
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
ms.openlocfilehash: 17463d65266baa53521bed9603c8abd96923277b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286976"
---
# <a name="dataadapters-and-datareaders"></a>Elementy DataAdapter i DataReader
Za pomocą elementu **DataReader** ADO.NET można pobrać strumień danych tylko do odczytu z bazy danych. Wyniki są zwracane w miarę wykonywania zapytania i są przechowywane w buforze sieciowym na kliencie do momentu zażądania ich przy użyciu metody **Read** elementu **DataReader**. Użycie elementu **DataReader** może zwiększyć wydajność aplikacji, pobierając dane natychmiast po ich udostępnieniu i (domyślnie) przechowując tylko jeden wiersz jednocześnie w pamięci, zmniejszając obciążenie systemu.  
  
 A służy <xref:System.Data.Common.DataAdapter> do pobierania danych ze źródła danych i wypełniania tabel w <xref:System.Data.DataSet> . `DataAdapter`Rozwiązuje również zmiany wprowadzone w `DataSet` odwrocie do źródła danych. `DataAdapter`Używa `Connection` obiektu dostawcy danych .NET Framework do nawiązywania połączenia ze źródłem danych i używa `Command` obiektów do pobierania danych ze i rozwiązywania zmian w źródle danych.  
  
 Każdy dostawca danych .NET Framework dołączony do .NET Framework ma <xref:System.Data.Common.DbDataReader> obiekt a i <xref:System.Data.Common.DbDataAdapter> obiektu: dostawca danych .NET Framework dla OLE DB zawiera i obiekt, .NET Framework Dostawca danych dla SQL Server zawiera a i obiekt <xref:System.Data.OleDb.OleDbDataReader> <xref:System.Data.OleDb.OleDbDataAdapter> <xref:System.Data.SqlClient.SqlDataReader> <xref:System.Data.SqlClient.SqlDataAdapter> , .NET Framework dostawca danych dla ODBC zawiera obiekt <xref:System.Data.Odbc.OdbcDataReader> i <xref:System.Data.Odbc.OdbcDataAdapter> , a .NET Framework dostawca danych dla programu Oracle zawiera <xref:System.Data.OracleClient.OracleDataReader> obiekt i <xref:System.Data.OracleClient.OracleDataAdapter> .  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Pobieranie danych przy użyciu elementu DataReader](retrieving-data-using-a-datareader.md)  
 Opisuje obiekt ADO.NET **DataReader** i sposób użycia go do zwrócenia strumienia wyników ze źródła danych.  
  
 [Wypełnianie zestawu danych z elementu DataAdapter](populating-a-dataset-from-a-dataadapter.md)  
 Opisuje sposób wypełniania `DataSet` tabelami, kolumnami i wierszami przy użyciu `DataAdapter` .  
  
 [Parametry elementu DataAdapter](dataadapter-parameters.md)  
 Opisuje sposób używania parametrów z właściwościami polecenia, `DataAdapter` w tym sposób mapowania zawartości kolumny w `DataSet` parametr do parametru polecenia.  
  
 [Dodawanie istniejących ograniczeń do zestawu danych](adding-existing-constraints-to-a-dataset.md)  
 Opisuje sposób dodawania istniejących ograniczeń do `DataSet` .  
  
 [Element DataAdapter DataTable i mapowania elementu DataColumn](dataadapter-datatable-and-datacolumn-mappings.md)  
 Opisuje sposób konfigurowania `DataTableMappings` i `ColumnMappings` dla programu `DataAdapter` .  
  
 [Stronicowanie za pośrednictwem wyniku zapytania](paging-through-a-query-result.md)  
 Przedstawia przykład wyświetlania wyników zapytania jako stron danych.  
  
 [Aktualizowanie źródeł danych za pomocą elementów DataAdapter](updating-data-sources-with-dataadapters.md)  
 Opisuje, jak za pomocą programu `DataAdapter` rozpoznać zmiany z `DataSet` powrotem do bazy danych.  
  
 [Obsługa zdarzeń elementu DataAdapter](handling-dataadapter-events.md)  
 Zawiera opis `DataAdapter` zdarzeń i sposobu ich używania.  
  
 [Wykonywanie operacji wsadowych za pomocą elementów DataAdapter](performing-batch-operations-using-dataadapters.md)  
 Opisuje zwiększenie wydajności aplikacji przez zredukowanie liczby rund do SQL Server podczas stosowania aktualizacji z programu `DataSet` .  
  
## <a name="see-also"></a>Zobacz także

- [Nawiązywanie połączenia ze źródłem danych](connecting-to-a-data-source.md)
- [Polecenia i parametry](commands-and-parameters.md)
- [Transakcje i współbieżność](transactions-and-concurrency.md)
- [Elementy DataSet, DataTable i DataView](./dataset-datatable-dataview/index.md)
- [Omówienie ADO.NET](ado-net-overview.md)
