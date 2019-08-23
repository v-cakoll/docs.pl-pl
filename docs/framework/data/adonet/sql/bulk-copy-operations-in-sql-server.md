---
title: Operacje kopiowania masowego w programie SQL Server
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: efa13eb1633fce3b59040ef8da79dba0f6ea81d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918061"
---
# <a name="bulk-copy-operations-in-sql-server"></a>Operacje kopiowania masowego w programie SQL Server
Microsoft SQL Server obejmuje popularne narzędzie wiersza polecenia o nazwie **BCP** , aby szybko skopiować duże pliki do tabel lub widoków w bazach danych SQL Server. <xref:System.Data.SqlClient.SqlBulkCopy> Klasa umożliwia pisanie rozwiązań kodu zarządzanego, które zapewniają podobną funkcjonalność. Istnieją inne sposoby ładowania danych do tabeli SQL Server (na przykład instrukcje INSERT), ale <xref:System.Data.SqlClient.SqlBulkCopy> oferują one znaczącą wydajność.  
  
 <xref:System.Data.SqlClient.SqlBulkCopy> Klasa może służyć do zapisywania danych tylko w tabelach SQL Server. Ale źródło danych nie jest ograniczone do SQL Server; można użyć dowolnego źródła danych, o ile dane mogą zostać załadowane do <xref:System.Data.DataTable> wystąpienia lub odczytane <xref:System.Data.IDataReader> za pomocą wystąpienia.  
  
 Korzystając z <xref:System.Data.SqlClient.SqlBulkCopy> klasy, można wykonać następujące polecenie:  
  
- Pojedyncza operacja kopiowania zbiorczego  
  
- Wiele operacji kopiowania zbiorczego  
  
- Operacja kopiowania zbiorczego w ramach transakcji  
  
> [!NOTE]
> W przypadku używania .NET Framework w wersji 1,1 lub starszej (która nie <xref:System.Data.SqlClient.SqlBulkCopy> obsługuje klasy) można wykonać SQL Server instrukcji języka Transact-SQL **BULK INSERT** przy użyciu <xref:System.Data.SqlClient.SqlCommand> obiektu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Konfiguracja przykładu kopiowania zbiorczego](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)  
 Opisuje tabele używane w przykładowych kopiach zbiorczych i udostępnia skrypty SQL do tworzenia tabel w bazie danych AdventureWorks.  
  
 [Pojedyncze operacje kopiowania zbiorczego](../../../../../docs/framework/data/adonet/sql/single-bulk-copy-operations.md)  
 Opisuje, jak wykonać pojedynczą zbiorczą kopię danych w wystąpieniu SQL Server przy użyciu <xref:System.Data.SqlClient.SqlBulkCopy> klasy i jak wykonać operację kopiowania zbiorczego za pomocą instrukcji języka Transact-SQL <xref:System.Data.SqlClient.SqlCommand> i klasy.  
  
 [Wiele operacji kopiowania zbiorczego](../../../../../docs/framework/data/adonet/sql/multiple-bulk-copy-operations.md)  
 Opisuje sposób wykonywania wielu operacji zbiorczych kopiowania danych do wystąpienia SQL Server przy użyciu <xref:System.Data.SqlClient.SqlBulkCopy> klasy.  
  
 [Transakcja i operacje kopiowania zbiorczego](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)  
 Opisuje sposób wykonywania operacji kopiowania zbiorczego w ramach transakcji, w tym metody zatwierdzania lub wycofywania transakcji.  
  
## <a name="see-also"></a>Zobacz także

- [SQL Server i ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
