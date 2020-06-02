---
title: Operacje kopiowania masowego w programie SQL Server
description: Dowiedz się, jak używać klasy SqlBulkCopy do pisania rozwiązań kodu zarządzanego, które zbiorczo kopiują duże pliki do tabel lub widoków w bazach danych SQL Server.
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: 4f877836aa45efe162cce3c42cb5733f86deab2c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286523"
---
# <a name="bulk-copy-operations-in-sql-server"></a>Operacje kopiowania masowego w programie SQL Server
Microsoft SQL Server obejmuje popularne narzędzie wiersza polecenia o nazwie **BCP** , aby szybko skopiować duże pliki do tabel lub widoków w bazach danych SQL Server. <xref:System.Data.SqlClient.SqlBulkCopy>Klasa umożliwia pisanie rozwiązań kodu zarządzanego, które zapewniają podobną funkcjonalność. Istnieją inne sposoby ładowania danych do tabeli SQL Server (na przykład instrukcje INSERT), ale <xref:System.Data.SqlClient.SqlBulkCopy> oferują one znaczącą wydajność.  
  
 <xref:System.Data.SqlClient.SqlBulkCopy>Klasa może służyć do zapisywania danych tylko w tabelach SQL Server. Ale źródło danych nie jest ograniczone do SQL Server; można użyć dowolnego źródła danych, o ile dane mogą zostać załadowane do <xref:System.Data.DataTable> wystąpienia lub odczytane za pomocą <xref:System.Data.IDataReader> wystąpienia.  
  
 Korzystając z <xref:System.Data.SqlClient.SqlBulkCopy> klasy, można wykonać następujące polecenie:  
  
- Pojedyncza operacja kopiowania zbiorczego  
  
- Wiele operacji kopiowania zbiorczego  
  
- Operacja kopiowania zbiorczego w ramach transakcji  
  
> [!NOTE]
> W przypadku używania .NET Framework w wersji 1,1 lub starszej (która nie obsługuje <xref:System.Data.SqlClient.SqlBulkCopy> klasy) można wykonać SQL Server instrukcji języka Transact-SQL **BULK INSERT** przy użyciu <xref:System.Data.SqlClient.SqlCommand> obiektu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Konfiguracja przykładu kopiowania zbiorczego](bulk-copy-example-setup.md)  
 Opisuje tabele używane w przykładowych kopiach zbiorczych i udostępnia skrypty SQL do tworzenia tabel w bazie danych AdventureWorks.  
  
 [Pojedyncze operacje kopiowania zbiorczego](single-bulk-copy-operations.md)  
 Opisuje, jak wykonać pojedynczą zbiorczą kopię danych w wystąpieniu SQL Server przy użyciu <xref:System.Data.SqlClient.SqlBulkCopy> klasy i jak wykonać operację kopiowania zbiorczego za pomocą instrukcji języka Transact-SQL i <xref:System.Data.SqlClient.SqlCommand> klasy.  
  
 [Wiele operacji kopiowania zbiorczego](multiple-bulk-copy-operations.md)  
 Opisuje sposób wykonywania wielu operacji zbiorczych kopiowania danych do wystąpienia SQL Server przy użyciu <xref:System.Data.SqlClient.SqlBulkCopy> klasy.  
  
 [Transakcja i operacje kopiowania zbiorczego](transaction-and-bulk-copy-operations.md)  
 Opisuje sposób wykonywania operacji kopiowania zbiorczego w ramach transakcji, w tym metody zatwierdzania lub wycofywania transakcji.  
  
## <a name="see-also"></a>Zobacz także

- [SQL Server i ADO.NET](index.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
