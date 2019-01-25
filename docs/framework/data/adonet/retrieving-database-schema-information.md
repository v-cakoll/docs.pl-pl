---
title: Pobieranie informacji o schemacie bazy danych
ms.date: 03/30/2017
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
ms.openlocfilehash: 8a076ca792ee1b4b2194b778c51fefbd0bb19bd5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494031"
---
# <a name="retrieving-database-schema-information"></a>Pobieranie informacji o schemacie bazy danych
Uzyskiwanie informacji o schemacie bazy danych odbywa się z procesem odnajdywania schematu. Wykrywanie schematu umożliwia aplikacjom żądanie czy zarządzanego dostawcy Znajdź i zwrócone informacje na temat schematu bazy danych, nazywane również *metadanych*, z określoną bazą danych. Elementy schematu innej bazy danych, takie jak tabele, kolumny i procedur składowanych są udostępniane za pośrednictwem kolekcje schematów. Każda kolekcja schemat zawiera szereg informacji o schemacie specyficzne dla używanego dostawcy.  
  
 Każda implementacja zarządzanego dostawcy .NET Framework **GetSchema** method in Class metoda **połączenia** klasy i informacji o schemacie, który jest zwracany z **GetSchema**metody jest dostarczany w formie <xref:System.Data.DataTable>. **GetSchema** metodą jest przeciążona metoda, która zapewnia następujące parametry opcjonalne określanie kolekcji schematów, aby powrócić i ograniczając ilość zwracanych informacji.  
  
 Podaj dostawcy danych .NET Framework dla OLE DB i ODBC, Oracle oraz SqlClient **GetSchemaTable** metodę, która zwraca DataTable opisujące kolumny metadanych **DataReader**.  
  
 .NET Framework Data Provider for OLE DB udostępnia również informacje o schemacie przy użyciu <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> metody <xref:System.Data.OleDb.OleDbConnection> obiektu. Jako argumenty **Element GetOleDbSchemaTable** przyjmuje <xref:System.Data.OleDb.OleDbSchemaGuid> określający informacji o schemacie, aby powrócić i Tablica ograniczeń na te zwracane kolumny. **Element GetOleDbSchemaTable** zwraca <xref:System.Data.DataTable> wypełniony informacjami żądany schemat.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [GetSchema i kolekcje schematów](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 W tym artykule opisano **GetSchema** metody i jak może służyć do pobierania i ograniczyć informacji o schemacie bazy danych.  
  
 Ograniczenia schematu  
 W tym artykule opisano ograniczenia schematu, które mogą być używane z **GetSchema**.  
  
 [Typowe kolekcje schematów](../../../../docs/framework/data/adonet/common-schema-collections.md)  
 W tym artykule opisano, wszystkie Typowe kolekcje schematów obsługiwane przez wszystkich dostawców zarządzanych w programie .NET Framework.  
  
 [Kolekcje schematów programu SQL Server](../../../../docs/framework/data/adonet/sql-server-schema-collections.md)  
 W tym artykule opisano kolekcji schematów, obsługiwany przez dostawcę .NET Framework dla programu SQL Server.  
  
 [Kolekcje schematów Oracle](../../../../docs/framework/data/adonet/oracle-schema-collections.md)  
 W tym artykule opisano kolekcji schematów, obsługiwany przez dostawcę .NET Framework dla programu Oracle.  
  
 [Kolekcje schematów ODBC](../../../../docs/framework/data/adonet/odbc-schema-collections.md)  
 Opisuje kolekcje schematów dla sterowników ODBC.  
  
 [Kolekcje schematów OLE DB](../../../../docs/framework/data/adonet/ole-db-schema-collections.md)  
 Opisuje kolekcje schematów dla dostawcy OLE DB.  
  
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
  
## <a name="see-also"></a>Zobacz także
- [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
