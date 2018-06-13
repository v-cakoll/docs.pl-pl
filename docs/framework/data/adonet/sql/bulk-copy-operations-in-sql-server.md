---
title: Operacje kopiowania masowego w programie SQL Server
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: 87373f55181742a243c60bc4b471334535d88ff7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360429"
---
# <a name="bulk-copy-operations-in-sql-server"></a>Operacje kopiowania masowego w programie SQL Server
Microsoft SQL Server zawiera popularne narzędzia wiersza polecenia o nazwie **bcp** dla szybko zbiorcze kopiowania dużych plików do tabel lub widoków w bazach danych programu SQL Server. <xref:System.Data.SqlClient.SqlBulkCopy> Klasa umożliwia pisanie kodu zarządzanego rozwiązań w zakresie podobnych możliwościach. Istnieją inne sposoby, aby załadować dane do tabeli programu SQL Server (na przykład instrukcji INSERT), ale <xref:System.Data.SqlClient.SqlBulkCopy> oferuje wydajności znaczących korzyści nad nimi.  
  
 <xref:System.Data.SqlClient.SqlBulkCopy> Klasa może być używana do zapisu danych tylko do tabel programu SQL Server. Jednak źródła danych nie jest ograniczony do programu SQL Server; wszystkie źródła danych może służyć, jak długo dane mogą być ładowane do <xref:System.Data.DataTable> wystąpienia lub odczytu z <xref:System.Data.IDataReader> wystąpienia.  
  
 Przy użyciu <xref:System.Data.SqlClient.SqlBulkCopy> klasy, można wykonać:  
  
-   Pojedynczy kopiowania masowego  
  
-   Wiele operacji kopiowania zbiorczego  
  
-   Operacja kopiowania zbiorczego w ramach transakcji  
  
> [!NOTE]
>  Korzystając z .NET Framework w wersji 1.1 lub starszy (który nie obsługuje <xref:System.Data.SqlClient.SqlBulkCopy> klasy), może zostać uruchomiony program SQL Server Transact-SQL **BULK INSERT** instrukcji przy użyciu <xref:System.Data.SqlClient.SqlCommand> obiektu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Konfiguracja przykładu kopiowania zbiorczego](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)  
 Opisuje tabele przykłady kopiowania zbiorczego i zapewnia skrypty SQL do tworzenia tabel w bazie danych AdventureWorks.  
  
 [Pojedyncze operacje kopiowania zbiorczego](../../../../../docs/framework/data/adonet/sql/single-bulk-copy-operations.md)  
 Opis sposobu wykonywania pojedynczego zbiorczego kopię danych do wystąpienia programu SQL Server przy użyciu <xref:System.Data.SqlClient.SqlBulkCopy> klasy i wykonać kopiowania masowego za pomocą instrukcji języka Transact-SQL i <xref:System.Data.SqlClient.SqlCommand> klasy.  
  
 [Wiele operacji kopiowania zbiorczego](../../../../../docs/framework/data/adonet/sql/multiple-bulk-copy-operations.md)  
 Zawiera opis sposobu wykonania wielu operacji kopiowania zbiorczego danych do wystąpienia programu SQL Server przy użyciu <xref:System.Data.SqlClient.SqlBulkCopy> klasy.  
  
 [Transakcja i operacje kopiowania zbiorczego](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)  
 Opisuje sposób wykonywania operacji kopiowania zbiorczego w ramach transakcji, w tym sposobu zatwierdzania lub wycofywania transakcji.  
  
## <a name="see-also"></a>Zobacz też  
 [SQL Server i ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
