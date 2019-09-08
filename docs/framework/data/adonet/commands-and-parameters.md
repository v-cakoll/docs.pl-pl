---
title: Polecenia i parametry
ms.date: 03/30/2017
ms.assetid: b623f810-d871-49a5-b0f5-078cc3c34db6
ms.openlocfilehash: 1d0c3adb56e5ff44b5c5e065ac040f25584a1946
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784955"
---
# <a name="commands-and-parameters"></a>Polecenia i parametry
Po ustanowieniu połączenia ze źródłem danych można wykonać polecenia i zwrócić wyniki ze źródła danych za pomocą <xref:System.Data.Common.DbCommand> obiektu. Można utworzyć polecenie przy użyciu jednego z konstruktorów poleceń dla dostawcy danych .NET Framework, z którym pracujesz. Konstruktory mogą przyjmować opcjonalne argumenty, takie jak instrukcja SQL do wykonania w źródle danych, <xref:System.Data.Common.DbConnection> obiekcie <xref:System.Data.Common.DbTransaction> lub obiekcie. Można również skonfigurować te obiekty jako właściwości polecenia. Możesz również utworzyć polecenie dla określonego połączenia przy użyciu <xref:System.Data.Common.DbConnection.CreateCommand%2A> metody `DbConnection` obiektu. Instrukcję SQL wykonywaną przez polecenie można skonfigurować przy użyciu <xref:System.Data.Common.DbCommand.CommandText%2A> właściwości.  
  
 Każdy dostawca danych .NET Framework dołączony do .NET Framework ma `Command` obiekt. Dostawca danych .NET Framework dla OLE DB zawiera <xref:System.Data.OleDb.OleDbCommand> obiekt, .NET Framework dostawca danych dla SQL Server <xref:System.Data.SqlClient.SqlCommand> zawiera obiekt, .NET Framework dostawca danych dla ODBC zawiera <xref:System.Data.Odbc.OdbcCommand> obiekt i .NET Framework Dostawca danych dla programu Oracle zawiera <xref:System.Data.OracleClient.OracleCommand> obiekt.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wykonywanie polecenia](executing-a-command.md)  
 Opisuje obiekt ADO.NET `Command` i sposób jego użycia do wykonywania zapytań i poleceń względem źródła danych.  
  
 [Konfigurowanie parametrów i typów danych parametrów](configuring-parameters-and-parameter-data-types.md)  
 Opisuje pracę z `Command` parametrami, w tym kierunek, typy danych i składnią parametrów.  
  
 [Generowanie poleceń za pomocą CommandBuilders](generating-commands-with-commandbuilders.md)  
 Opisuje, jak używać konstruktorów poleceń do automatycznego generowania poleceń INSERT, Update i DELETE dla elementu `DataAdapter` , który ma polecenie Select z jedną tabelą.  
  
 [Uzyskiwanie pojedynczej wartości z bazy danych](obtaining-a-single-value-from-a-database.md)  
 Opisuje sposób użycia `ExecuteScalar` metody `Command` obiektu do zwrócenia pojedynczej wartości z zapytania bazy danych.  
  
 [Używanie poleceń do modyfikacji danych](using-commands-to-modify-data.md)  
 Opisuje sposób użycia dostawcy danych w celu wykonania procedur składowanych lub instrukcji języka definicji danych (DDL).  
  
## <a name="see-also"></a>Zobacz także

- [Elementy DataAdapter i DataReaders](dataadapters-and-datareaders.md)
- [Elementy DataSet, DataTable i DataView](./dataset-datatable-dataview/index.md)
- [Nawiązywanie połączenia ze źródłem danych](connecting-to-a-data-source.md)
- [Omówienie ADO.NET](ado-net-overview.md)
