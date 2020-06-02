---
title: Polecenia i parametry
description: Dowiedz się, jak używać obiektów poleceń dla każdego dostawcy danych .NET Framework, aby uruchamiać polecenia i zwracać wyniki ze źródła danych.
ms.date: 03/30/2017
ms.assetid: b623f810-d871-49a5-b0f5-078cc3c34db6
ms.openlocfilehash: c0baec4d6c3984cb50178c3aa7f9ed3878055bb6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287145"
---
# <a name="commands-and-parameters"></a>Polecenia i parametry
Po ustanowieniu połączenia ze źródłem danych można wykonać polecenia i zwrócić wyniki ze źródła danych za pomocą <xref:System.Data.Common.DbCommand> obiektu. Można utworzyć polecenie przy użyciu jednego z konstruktorów poleceń dla dostawcy danych .NET Framework, z którym pracujesz. Konstruktory mogą przyjmować opcjonalne argumenty, takie jak instrukcja SQL do wykonania w źródle danych, <xref:System.Data.Common.DbConnection> obiekcie lub <xref:System.Data.Common.DbTransaction> obiekcie. Można również skonfigurować te obiekty jako właściwości polecenia. Możesz również utworzyć polecenie dla określonego połączenia przy użyciu <xref:System.Data.Common.DbConnection.CreateCommand%2A> metody `DbConnection` obiektu. Instrukcję SQL wykonywaną przez polecenie można skonfigurować przy użyciu <xref:System.Data.Common.DbCommand.CommandText%2A> właściwości.  
  
 Każdy dostawca danych .NET Framework dołączony do .NET Framework ma `Command` obiekt. Dostawca danych .NET Framework dla OLE DB zawiera obiekt <xref:System.Data.OleDb.OleDbCommand> , .NET Framework dostawca danych dla SQL Server zawiera obiekt <xref:System.Data.SqlClient.SqlCommand> , .NET Framework dostawca danych dla ODBC zawiera obiekt <xref:System.Data.Odbc.OdbcCommand> , a .NET Framework dostawca danych dla programu Oracle zawiera <xref:System.Data.OracleClient.OracleCommand> obiekt.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wykonywanie polecenia](executing-a-command.md)  
 Opisuje obiekt ADO.NET `Command` i sposób jego użycia do wykonywania zapytań i poleceń względem źródła danych.  
  
 [Konfigurowanie parametrów i typów danych parametrów](configuring-parameters-and-parameter-data-types.md)  
 Opisuje pracę z `Command` parametrami, w tym kierunek, typy danych i składnią parametrów.  
  
 [Generowanie poleceń za pomocą CommandBuilders](generating-commands-with-commandbuilders.md)  
 Opisuje, jak używać konstruktorów poleceń do automatycznego generowania poleceń INSERT, UPDATE i DELETE dla elementu `DataAdapter` , który ma polecenie Select z jedną tabelą.  
  
 [Uzyskiwanie pojedynczej wartości z bazy danych](obtaining-a-single-value-from-a-database.md)  
 Opisuje sposób użycia `ExecuteScalar` metody `Command` obiektu do zwrócenia pojedynczej wartości z zapytania bazy danych.  
  
 [Używanie poleceń do modyfikacji danych](using-commands-to-modify-data.md)  
 Opisuje sposób użycia dostawcy danych w celu wykonania procedur składowanych lub instrukcji języka definicji danych (DDL).  
  
## <a name="see-also"></a>Zobacz także

- [Elementy DataAdapter i DataReader](dataadapters-and-datareaders.md)
- [Elementy DataSet, DataTable i DataView](./dataset-datatable-dataview/index.md)
- [Nawiązywanie połączenia ze źródłem danych](connecting-to-a-data-source.md)
- [Omówienie ADO.NET](ado-net-overview.md)
