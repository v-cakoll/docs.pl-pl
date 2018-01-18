---
title: Pobieranie informacji o schemacie bazy danych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 09a0ec444801d1fe2caccf9e25a68e3c6ae8f5c2
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="retrieving-database-schema-information"></a>Pobieranie informacji o schemacie bazy danych
Uzyskiwanie informacji o schemacie z bazy danych odbywa się z procesem odnajdywania schematu. Odnajdywanie schematu umożliwia aplikacjom żądanie czy zarządzanego dostawcy znaleźć i zwraca informacje dotyczące schematu bazy danych, nazywane również *metadanych*, danego bazy danych. Elementów schematu innej bazy danych, takich jak tabele, kolumny i procedury składowane są udostępniane za pomocą kolekcji schematu. Każdej kolekcji schematu zawiera szereg informacji o schemacie specyficzne dla używanego dostawcy.  
  
 Każda implementacja zarządzanego dostawcy .NET Framework **GetSchema** metody w **połączenia** klasy i informacji o schemacie, która jest zwracana z **GetSchema**metody jest dostarczany w formie <xref:System.Data.DataTable>. **GetSchema** metody jest przeciążona metoda, która zapewnia następujące parametry opcjonalne określanie kolekcji schematów, aby wrócić i ograniczanie ilość zwracanych informacji.  
  
 Podaj dostawców danych .NET Framework dla OLE DB, ODBC, Oracle i SqlClient **GetSchemaTable** metodę, która zwraca DataTable opisujące metadane kolumny **DataReader**.  
  
 .NET Framework Data Provider for OLE DB przedstawia również informacje o schemacie przy użyciu <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> metody <xref:System.Data.OleDb.OleDbConnection> obiektu. Jako argumenty **Element GetOleDbSchemaTable** przyjmuje <xref:System.Data.OleDb.OleDbSchemaGuid> identyfikującym informacji o schemacie, aby wrócić i zwrócił tablicę ograniczeń dotyczących tych kolumn. **Element GetOleDbSchemaTable** zwraca <xref:System.Data.DataTable> wypełnione informacjami żądany schemat.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [GetSchema i kolekcje schematów](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 W tym artykule opisano **GetSchema** — metoda i jak może służyć do pobierania i ograniczanie informacji schematu z bazy danych.  
  
 Ograniczenia schematu  
 W tym artykule opisano ograniczenia schematu, które mogą być używane z **GetSchema**.  
  
 [Typowe kolekcje schematów](../../../../docs/framework/data/adonet/common-schema-collections.md)  
 Zawiera opis wszystkich typowych kolekcji schematu obsługiwane przez wszystkich dostawców zarządzane w programie .NET Framework.  
  
 [Kolekcje schematów programu SQL Server](../../../../docs/framework/data/adonet/sql-server-schema-collections.md)  
 Opis kolekcji schematów, obsługiwane przez dostawcę .NET Framework dla programu SQL Server.  
  
 [Kolekcje schematów Oracle](../../../../docs/framework/data/adonet/oracle-schema-collections.md)  
 Opis kolekcji schematów, obsługiwane przez dostawcę .NET Framework dla programu Oracle.  
  
 [Kolekcje schematów ODBC](../../../../docs/framework/data/adonet/odbc-schema-collections.md)  
 Opis kolekcji schematu dla sterowników ODBC.  
  
 [Kolekcje schematów OLE DB](../../../../docs/framework/data/adonet/ole-db-schema-collections.md)  
 Opis kolekcji schematu dla dostawcy OLE DB.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 W tym artykule opisano **GetSchema** metody <xref:System.Data.Common.DbConnection> klasy.  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 W tym artykule opisano **GetSchema** metody <xref:System.Data.Odbc.OdbcConnection> klasy.  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 W tym artykule opisano **GetSchema** metody <xref:System.Data.OleDb.OleDbConnection> klasy.  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 W tym artykule opisano **GetSchema** metody <xref:System.Data.OracleClient.OracleConnection> klasy.  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 W tym artykule opisano **GetSchema** metody <xref:System.Data.SqlClient.SqlConnection> klasy.  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 W tym artykule opisano **GetSchemaTable** metody <xref:System.Data.Common.DbDataReader> klasy.  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 W tym artykule opisano **GetSchemaTable** metody <xref:System.Data.Odbc.OdbcDataReader> klasy.  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 W tym artykule opisano **GetSchemaTable** metody <xref:System.Data.OleDb.OleDbDataReader> klasy.  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 W tym artykule opisano **GetSchemaTable** metody <xref:System.Data.OracleClient.OracleDataReader> klasy.  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 W tym artykule opisano **GetSchemaTable** metody <xref:System.Data.SqlClient.SqlDataReader> klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
