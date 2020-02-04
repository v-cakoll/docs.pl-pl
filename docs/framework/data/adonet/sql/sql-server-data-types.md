---
title: Typy danych programu SQL Server i ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: 9baffc7a439c851ead7ec0e12899adf418174e22
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2020
ms.locfileid: "76979862"
---
# <a name="sql-server-data-types-and-adonet"></a>Typy danych programu SQL Server i ADO.NET
SQL Server i .NET Framework są oparte na różnych systemach typu, co może spowodować utratę danych. Aby zachować integralność danych, Dostawca danych .NET Framework dla SQL Server (<xref:System.Data.SqlClient>) zapewnia metody dostępu typu Type do pracy z SQL Server danymi. Możesz użyć wyliczeń z klas <xref:System.Data.SqlDbType>, aby określić <xref:System.Data.SqlClient.SqlParameter> typy danych.  
  
 Aby uzyskać więcej informacji i tabelę opisującą mapowanie typu danych między SQL Server i .NET Framework typy danych, zobacz [SQL Server mapowania typów danych](../sql-server-data-type-mappings.md).  
  
 SQL Server 2008 wprowadza nowe typy danych, które są przeznaczone do zaspokajania potrzeb firmy, do pracy z danymi o dacie i godzinie, ze strukturą, częściową strukturą i bez struktury. Są one udokumentowane w SQL Server 2008 książki online.  
  
 SQL Server typy danych, które są dostępne do użycia w aplikacji, zależą od używanej wersji programu SQL Server. Aby uzyskać więcej informacji, zobacz odpowiednią wersję dokumentacji SQL Server Books Online w poniższej tabeli.  
  
 **Książka SQL Server online**  
  
1. [Typy danych (aparat bazy danych)](https://go.microsoft.com/fwlink/?LinkID=107468)  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Właściwość SqlTypes i zestaw danych](sqltypes-and-the-dataset.md)  
 Opisuje obsługę typu `SqlTypes` w `DataSet`.  
  
 [Obsługa wartości Null](handling-null-values.md)  
 Pokazuje, jak korzystać z wartości null i logiki z trzema wartościami.  
  
 [Porównywanie identyfikatora GUID i wartości uniqueidentifier](comparing-guid-and-uniqueidentifier-values.md)  
 Demonstruje sposób pracy z identyfikatorami GUID i unikatowymi wartościami w SQL Server i .NET Framework.  
  
 [Dane daty i godziny](date-and-time-data.md)  
 Opisuje sposób korzystania z nowych typów danych daty i godziny wprowadzonych w SQL Server 2008.  
  
 [Duże UDT](large-udts.md)  
 Demonstruje sposób pobierania danych z UDTs dużej wartości wprowadzonych w SQL Server 2008.  
  
 [Dane XML w programie SQL Server](xml-data-in-sql-server.md)  
 Opisuje sposób pracy z danymi XML pobranymi z SQL Server.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Data.DataSet>  
 Opisuje klasę `DataSet` i wszystkich jej elementów członkowskich.  
  
 <xref:System.Data.SqlTypes>  
 Zawiera opis przestrzeni nazw `SqlTypes` i wszystkich jej elementów członkowskich.  
  
 <xref:System.Data.SqlDbType>  
 Opisuje Wyliczenie `SqlDbType` i wszystkie jego elementy członkowskie.  
  
 <xref:System.Data.DbType>  
 Opisuje Wyliczenie `DbType` i wszystkie jego elementy członkowskie.  
  
## <a name="see-also"></a>Zobacz także

- [Mapowanie typu danych serwera SQL](../sql-server-data-type-mappings.md)
- [Konfigurowanie parametrów i typów danych parametrów](../configuring-parameters-and-parameter-data-types.md)
- [Parametry o wartościach tabelowych](table-valued-parameters.md)
- [Dane binarne i dużej wartości w programie SQL Server](sql-server-binary-and-large-value-data.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
