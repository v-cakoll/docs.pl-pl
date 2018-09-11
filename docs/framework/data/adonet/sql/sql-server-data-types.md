---
title: SQL Server Data typów i ADO.NET
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: 878bbe41f259f1e50cd0a41669c7a352e78bc0f1
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44272491"
---
# <a name="sql-server-data-types-and-adonet"></a>SQL Server Data typów i ADO.NET
Program SQL Server i .NET Framework są oparte na różnych typów systemów, które może spowodować utratę danych. Aby zachować spójność danych, dla programu .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) udostępnia metody typizowane metody dostępu do pracy z danymi programu SQL Server. Można używać wyliczenia w <xref:System.Data.SqlDbType> klasy, aby określić <xref:System.Data.SqlClient.SqlParameter> typów danych.  
  
 Więcej informacji i tabelę, która, które zawiera opis danych typu mapowania między typy danych .NET Framework i programu SQL Server, zobacz [mapowanie typu danych serwera SQL](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md).  
  
 Program SQL Server 2008 wprowadzono nowe typy danych, które są przeznaczone do zaspokojenia potrzeb biznesowych do pracy z daty i godziny, ze strukturą, częściową strukturą i bez struktury danych. Te opisano w dokumentacji programu SQL Server 2008 — książki Online.  
  
 Typy danych programu SQL Server, które są dostępne do użycia w aplikacji zależy od wersji programu SQL Server, którego używasz. Aby uzyskać więcej informacji zobacz odpowiedniej wersji programu SQL Server — książki Online, w poniższej tabeli.  
  
 **SQL Server — książki Online**  
  
1.  [Typy danych (aparat bazy danych)](https://go.microsoft.com/fwlink/?LinkID=107468)  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Właściwość SqlTypes i zestaw danych](../../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md)  
 W tym artykule opisano obsługę typu `SqlTypes` w `DataSet`.  
  
 [Obsługa wartości Null](../../../../../docs/framework/data/adonet/sql/handling-null-values.md)  
 Pokazuje, jak pracować z przechowywanymi w trzech logiki i wartości null.  
  
 [Porównywanie identyfikatora GUID i wartości uniqueidentifier](../../../../../docs/framework/data/adonet/sql/comparing-guid-and-uniqueidentifier-values.md)  
 Pokazuje, jak pracować z wartości identyfikatora GUID i unikatowy identyfikator programu SQL Server i .NET Framework.  
  
 [Dane daty i godziny](../../../../../docs/framework/data/adonet/sql/date-and-time-data.md)  
 W tym artykule opisano, jak używać nowych typów daty i godziny dane wprowadzone w programie SQL Server 2008.  
  
 [Duże UDT](../../../../../docs/framework/data/adonet/sql/large-udts.md)  
 Pokazuje, jak można pobrać danych z dużą wartość typów zdefiniowanych przez użytkownika, wprowadzone w programie SQL Server 2008.  
  
 [Dane XML w programie SQL Server](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 W tym artykule opisano sposób pracy z danymi XML, pobierane z programu SQL Server.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Data.DataSet>  
 W tym artykule opisano `DataSet` klasy i wszystkich jego składowych.  
  
 <xref:System.Data.SqlTypes>  
 W tym artykule opisano `SqlTypes` przestrzeni nazw i wszystkich jego składowych.  
  
 <xref:System.Data.SqlDbType>  
 W tym artykule opisano `SqlDbType` wyliczenia i wszyscy jej członkowie.  
  
 <xref:System.Data.DbType>  
 W tym artykule opisano `DbType` wyliczenia i wszyscy jej członkowie.  
  
## <a name="see-also"></a>Zobacz też  
 [Mapowanie typu danych serwera SQL](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [Konfigurowanie parametrów i typów danych parametrów](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [Parametry o wartościach tabelowych](../../../../../docs/framework/data/adonet/sql/table-valued-parameters.md)  
 [Dane binarne i dużej wartości w programie SQL Server](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
