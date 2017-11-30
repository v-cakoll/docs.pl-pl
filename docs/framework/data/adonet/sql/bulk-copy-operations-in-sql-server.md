---
title: Operacje kopiowania masowego w programie SQL Server
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 31da2fbc7dca4c0c2c077991ddec39e8979b08b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Instalator przykład kopiowania zbiorczego](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)  
 Opisuje tabele przykłady kopiowania zbiorczego i zapewnia skrypty SQL do tworzenia tabel w bazie danych AdventureWorks.  
  
 [Operacje kopiowania masowego pojedynczego](../../../../../docs/framework/data/adonet/sql/single-bulk-copy-operations.md)  
 Opis sposobu wykonywania pojedynczego zbiorczego kopię danych do wystąpienia programu SQL Server przy użyciu <xref:System.Data.SqlClient.SqlBulkCopy> klasy i wykonać kopiowania masowego za pomocą instrukcji języka Transact-SQL i <xref:System.Data.SqlClient.SqlCommand> klasy.  
  
 [Wiele operacji kopiowania zbiorczego](../../../../../docs/framework/data/adonet/sql/multiple-bulk-copy-operations.md)  
 Zawiera opis sposobu wykonania wielu operacji kopiowania zbiorczego danych do wystąpienia programu SQL Server przy użyciu <xref:System.Data.SqlClient.SqlBulkCopy> klasy.  
  
 [Transakcja i operacje kopiowania masowego](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)  
 Opisuje sposób wykonywania operacji kopiowania zbiorczego w ramach transakcji, w tym sposobu zatwierdzania lub wycofywania transakcji.  
  
## <a name="see-also"></a>Zobacz też  
 [SQL Server i ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
