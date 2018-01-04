---
title: "Poleceń i parametrów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b623f810-d871-49a5-b0f5-078cc3c34db6
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f28f4ed728ee429a691a0a19b3fc143ac0e832ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="commands-and-parameters"></a>Poleceń i parametrów
Po ustanowieniu połączenia ze źródłem danych, można wykonać polecenia i zwracają wyniki z źródła danych przy użyciu <xref:System.Data.Common.DbCommand> obiektu. Można utworzyć przy użyciu jednego z konstruktorów polecenia dla dostawcy danych .NET Framework, które użytkownik pracuje z polecenia. Konstruktory może zająć Argumenty opcjonalne, takie jak instrukcja SQL do wykonania w źródle danych <xref:System.Data.Common.DbConnection> obiekt, lub <xref:System.Data.Common.DbTransaction> obiektu. Można również skonfigurować te obiekty jako właściwości polecenia. Można również utworzyć polecenia dla konkretnego połączenia za pomocą <xref:System.Data.Common.DbConnection.CreateCommand%2A> metody `DbConnection` obiektu. Instrukcja SQL jest wykonywany przez polecenie można skonfigurować za pomocą <xref:System.Data.Common.DbCommand.CommandText%2A> właściwości.  
  
 Każdy dostawca danych programu .NET Framework uwzględnionych w programie .NET Framework ma `Command` obiektu. .NET Framework Data Provider for OLE DB zawiera <xref:System.Data.OleDb.OleDbCommand> obiekt dostawcy danych programu .NET Framework dla programu SQL Server zawiera <xref:System.Data.SqlClient.SqlCommand> obiekt dostawcy danych programu .NET Framework dla ODBC obejmuje <xref:System.Data.Odbc.OdbcCommand> obiektu i .NET Framework Dostawca danych dla Oracle zawiera <xref:System.Data.OracleClient.OracleCommand> obiektu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wykonywanie polecenia](../../../../docs/framework/data/adonet/executing-a-command.md)  
 W tym artykule opisano ADO.NET `Command` obiekt i jak z niego korzystać do wykonywania zapytań i poleceń względem źródła danych.  
  
 [Konfigurowanie parametrów i typów danych parametrów](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 Zawiera opis pracy z `Command` parametrów, w tym kierunku, typy danych i składnia parametru.  
  
 [Generowanie poleceń za pomocą CommandBuilders](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md)  
 Informacje dotyczące używania polecenia konstruktorów mają być automatycznie generowane polecenia INSERT, UPDATE i DELETE dla `DataAdapter` mający pojedynczej tabeli polecenia wyboru.  
  
 [Uzyskiwanie pojedynczej wartości z bazy danych](../../../../docs/framework/data/adonet/obtaining-a-single-value-from-a-database.md)  
 Informacje dotyczące używania `ExecuteScalar` metody `Command` obiektu do zwrócenia pojedynczej wartości z zapytania do bazy danych.  
  
 [Używanie poleceń do modyfikacji danych](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 Informacje dotyczące używania dostawcy danych można wykonać przechowywanych danych lub procedury instrukcje języka definicji (DDL).  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Elementy DataSet, DataTable i DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Nawiązywanie połączenia ze źródłem danych](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
