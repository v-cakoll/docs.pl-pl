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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 16c675491a378d72d82a252d79a73379f494893c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="sql-server-data-types-and-adonet"></a>Danych programu SQL Server typy i ADO.NET
SQL Server i programu .NET Framework są oparte na systemach innego typu, które mogą spowodować utratę danych. Aby zachować spójność danych, .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) udostępnia metody typizowane metody dostępu do pracy z danymi programu SQL Server. Korzystając z wyliczeń w <xref:System.Data.SqlDbType> klas, aby określić <xref:System.Data.SqlClient.SqlParameter> typów danych.  
  
 Aby uzyskać więcej informacji oraz tabelę, która opisuje dane typu mapowań między typy danych .NET Framework i programu SQL Server, zobacz [mapowanie typu danych serwera SQL](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md).  
  
 SQL Server 2008 wprowadzono nowe typy danych, które są przeznaczone do potrzeb firmy do pracy z datą i godziną, struktury, częściową strukturą i bez struktury danych. Te opisano w dokumentacji SQL Server 2008 — książki Online.  
  
 Typy danych programu SQL Server, które są dostępne do użycia w aplikacji zależy od wersji programu SQL Server, którego używasz. Aby uzyskać więcej informacji zobacz odpowiednich wersji programu SQL Server — książki Online w poniższej tabeli.  
  
 **SQL Server — książki Online**  
  
1.  [Typy danych (aparat bazy danych)](http://go.microsoft.com/fwlink/?LinkID=107468)  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Właściwości SqlTypes i zestawie danych](../../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md)  
 W tym artykule opisano obsługę typu `SqlTypes` w `DataSet`.  
  
 [Obsługa wartości Null](../../../../../docs/framework/data/adonet/sql/handling-null-values.md)  
 Pokazuje, jak pracować z wartości null i przechowywanymi na trzy logiczne.  
  
 [Porównanie identyfikator GUID i uniqueidentifier wartości](../../../../../docs/framework/data/adonet/sql/comparing-guid-and-uniqueidentifier-values.md)  
 Pokazuje, jak pracować z wartości identyfikatora GUID i unikatowy identyfikator programu SQL Server i programu .NET Framework.  
  
 [Daty i godziny](../../../../../docs/framework/data/adonet/sql/date-and-time-data.md)  
 Opis sposobu użycia nowego Data i godzina typy danych wprowadzonych w programie SQL Server 2008.  
  
 [Duże typów](../../../../../docs/framework/data/adonet/sql/large-udts.md)  
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
 [Parametry przechowywanymi w tabeli](../../../../../docs/framework/data/adonet/sql/table-valued-parameters.md)  
 [Dane binarne i duża wartość serwera SQL](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
