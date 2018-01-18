---
title: Danych programu SQL Server typy i ADO.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b8ecdffc8e2dc9795a3bc9623c5e0127e068cc4f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="sql-server-data-types-and-adonet"></a>Danych programu SQL Server typy i ADO.NET
SQL Server i programu .NET Framework są oparte na systemach innego typu, które mogą spowodować utratę danych. Aby zachować spójność danych, .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) udostępnia metody typizowane metody dostępu do pracy z danymi programu SQL Server. Korzystając z wyliczeń w <xref:System.Data.SqlDbType> klas, aby określić <xref:System.Data.SqlClient.SqlParameter> typów danych.  
  
 Aby uzyskać więcej informacji oraz tabelę, która opisuje dane typu mapowań między typy danych .NET Framework i programu SQL Server, zobacz [mapowanie typu danych serwera SQL](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md).  
  
 SQL Server 2008 wprowadzono nowe typy danych, które są przeznaczone do potrzeb firmy do pracy z datą i godziną, struktury, częściową strukturą i bez struktury danych. Te opisano w dokumentacji SQL Server 2008 — książki Online.  
  
 Typy danych programu SQL Server, które są dostępne do użycia w aplikacji zależy od wersji programu SQL Server, którego używasz. Aby uzyskać więcej informacji zobacz odpowiednich wersji programu SQL Server — książki Online w poniższej tabeli.  
  
 **SQL Server — książki Online**  
  
1.  [Typy danych (aparat bazy danych)](http://go.microsoft.com/fwlink/?LinkID=107468)  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Właściwość SqlTypes i zestaw danych](../../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md)  
 W tym artykule opisano obsługę typu `SqlTypes` w `DataSet`.  
  
 [Obsługa wartości Null](../../../../../docs/framework/data/adonet/sql/handling-null-values.md)  
 Pokazuje, jak pracować z wartości null i przechowywanymi na trzy logiczne.  
  
 [Porównywanie identyfikatora GUID i wartości uniqueidentifier](../../../../../docs/framework/data/adonet/sql/comparing-guid-and-uniqueidentifier-values.md)  
 Pokazuje, jak pracować z wartości identyfikatora GUID i unikatowy identyfikator programu SQL Server i programu .NET Framework.  
  
 [Dane daty i godziny](../../../../../docs/framework/data/adonet/sql/date-and-time-data.md)  
 Opis sposobu użycia nowego Data i godzina typy danych wprowadzonych w programie SQL Server 2008.  
  
 [Duże UDT](../../../../../docs/framework/data/adonet/sql/large-udts.md)  
 Pokazuje, jak można pobrać danych z dużą wartość UDTs wprowadzone w programie SQL Server 2008.  
  
 [Dane XML w programie SQL Server](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 Opisuje sposób pracy z danymi XML pobrane z programu SQL Server.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Data.DataSet>  
 W tym artykule opisano `DataSet` klasy i wszystkich jego elementów członkowskich.  
  
 <xref:System.Data.SqlTypes>  
 W tym artykule opisano `SqlTypes` przestrzeni nazw i wszystkich jego elementów członkowskich.  
  
 <xref:System.Data.SqlDbType>  
 W tym artykule opisano `SqlDbType` wyliczenie i wszystkich jego elementów członkowskich.  
  
 <xref:System.Data.DbType>  
 W tym artykule opisano `DbType` wyliczenie i wszystkich jego elementów członkowskich.  
  
## <a name="see-also"></a>Zobacz też  
 [Mapowanie typu danych serwera SQL](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [Konfigurowanie parametrów i typów danych parametrów](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [Parametry o wartościach tabelowych](../../../../../docs/framework/data/adonet/sql/table-valued-parameters.md)  
 [Dane binarne i dużej wartości w programie SQL Server](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
