---
title: Polecenia i parametry
ms.date: 03/30/2017
ms.assetid: b623f810-d871-49a5-b0f5-078cc3c34db6
ms.openlocfilehash: 0f90e45a9679e76a38621f6e3ae19de0e7591098
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612798"
---
# <a name="commands-and-parameters"></a>Polecenia i parametry
Po ustanowieniu połączenia ze źródłem danych, można wykonać polecenia i zwracania wyników z źródła danych przy użyciu <xref:System.Data.Common.DbCommand> obiektu. Można utworzyć polecenia przy użyciu jednego z konstruktorów polecenia dla dostawcy danych .NET Framework, którą pracujesz. Konstruktory może potrwać Argumenty opcjonalne, takie jak instrukcję SQL do wykonania w źródle danych <xref:System.Data.Common.DbConnection> obiektu lub <xref:System.Data.Common.DbTransaction> obiektu. Tych obiektów można również skonfigurować jako właściwości polecenia. Możesz również utworzyć polecenia dla danego połączenia za pomocą <xref:System.Data.Common.DbConnection.CreateCommand%2A> metody `DbConnection` obiektu. Można skonfigurować instrukcji SQL, wykonywane przez polecenie, używając <xref:System.Data.Common.DbCommand.CommandText%2A> właściwości.  
  
 Każdy dostawca danych .NET Framework, dołączone do programu .NET Framework ma `Command` obiektu. .NET Framework Data Provider for OLE DB zawiera <xref:System.Data.OleDb.OleDbCommand> obiektu .NET Framework Data Provider for SQL Server zawiera <xref:System.Data.SqlClient.SqlCommand> obiektu .NET Framework Data Provider for ODBC obejmuje <xref:System.Data.Odbc.OdbcCommand> obiektu i .NET Framework Data Provider Pro Oracle obejmuje <xref:System.Data.OracleClient.OracleCommand> obiektu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wykonywanie polecenia](../../../../docs/framework/data/adonet/executing-a-command.md)  
 W tym artykule opisano ADO.NET `Command` obiektu i jak go używać do wykonywania zapytań i poleceń względem źródła danych.  
  
 [Konfigurowanie parametrów i typów danych parametrów](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 W tym artykule opisano pracę z `Command` parametrów, w tym kierunku, typów danych i składnia parametru.  
  
 [Generowanie poleceń za pomocą CommandBuilders](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md)  
 Opisuje sposób używania polecenia Konstruktorzy można automatycznie wygenerować polecenia INSERT, UPDATE i DELETE dla `DataAdapter` zawierający polecenie SELECT pojedynczej tabeli.  
  
 [Uzyskiwanie pojedynczej wartości z bazy danych](../../../../docs/framework/data/adonet/obtaining-a-single-value-from-a-database.md)  
 Opisuje sposób używania `ExecuteScalar` metody `Command` obiekt do zwrotu pojedynczej wartości z zapytania do bazy danych.  
  
 [Używanie poleceń do modyfikacji danych](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 W tym artykule opisano sposób użycia dostawcy danych można wykonać przechowywanych procedur lub danych instrukcje języka definicji (DDL).  
  
## <a name="see-also"></a>Zobacz także
- [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [Elementy DataSet, DataTable i DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [Nawiązywanie połączenia ze źródłem danych](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
