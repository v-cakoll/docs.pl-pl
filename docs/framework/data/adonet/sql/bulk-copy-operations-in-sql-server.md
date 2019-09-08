---
title: Operacje kopiowania masowego w programie SQL Server
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: ae97bcdd6776d573cf9e523133c2c00a42c273bb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782525"
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
 [Konfiguracja przykładu kopiowania zbiorczego](bulk-copy-example-setup.md)  
 Opisuje tabele używane w przykładowych kopiach zbiorczych i udostępnia skrypty SQL do tworzenia tabel w bazie danych AdventureWorks.  
  
 [Pojedyncze operacje kopiowania zbiorczego](single-bulk-copy-operations.md)  
 Opisuje, jak wykonać pojedynczą zbiorczą kopię danych w wystąpieniu SQL Server przy użyciu <xref:System.Data.SqlClient.SqlBulkCopy> klasy i jak wykonać operację kopiowania zbiorczego za pomocą instrukcji języka Transact-SQL <xref:System.Data.SqlClient.SqlCommand> i klasy.  
  
 [Wiele operacji kopiowania zbiorczego](multiple-bulk-copy-operations.md)  
 Opisuje sposób wykonywania wielu operacji zbiorczych kopiowania danych do wystąpienia SQL Server przy użyciu <xref:System.Data.SqlClient.SqlBulkCopy> klasy.  
  
 [Transakcja i operacje kopiowania zbiorczego](transaction-and-bulk-copy-operations.md)  
 Opisuje sposób wykonywania operacji kopiowania zbiorczego w ramach transakcji, w tym metody zatwierdzania lub wycofywania transakcji.  
  
## <a name="see-also"></a>Zobacz także

- [SQL Server i ADO.NET](index.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
