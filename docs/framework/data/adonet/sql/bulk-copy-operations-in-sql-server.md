---
title: Operacje kopiowania masowego w programie SQL Server
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: 16709d1bdc03c767d1e3aed808de220bf91e76ee
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43455669"
---
# <a name="bulk-copy-operations-in-sql-server"></a>Operacje kopiowania masowego w programie SQL Server
Microsoft SQL Server zawiera popularne narzędzia wiersza polecenia o nazwie **bcp** dla szybko zbiorcze kopiowanie dużych plików do tabel lub widoków w bazach danych programu SQL Server. <xref:System.Data.SqlClient.SqlBulkCopy> Klasy umożliwia pisanie kodu zarządzanego rozwiązania, które zapewniają podobne funkcje. Istnieją inne sposoby, aby załadować dane do tabeli programu SQL Server (na przykład instrukcji INSERT), ale <xref:System.Data.SqlClient.SqlBulkCopy> oferuje zalety istotnie poprawiającą wydajność, nad nimi.  
  
 <xref:System.Data.SqlClient.SqlBulkCopy> Klasa może być używana w celu zapisania danych tylko do tabel programu SQL Server. Jednak źródła danych nie jest ograniczony do programu SQL Server; Dowolne źródło danych może służyć, tak długo, jak długo dane mogą być ładowane do <xref:System.Data.DataTable> wystąpienia lub odczytu z <xref:System.Data.IDataReader> wystąpienia.  
  
 Za pomocą <xref:System.Data.SqlClient.SqlBulkCopy> klasy, można wykonać:  
  
-   Pojedynczej zbiorczej operacji kopiowania  
  
-   Wiele operacji kopiowania zbiorczego  
  
-   Operacji kopiowania zbiorczego, w ramach transakcji  
  
> [!NOTE]
>  Korzystając z .NET Framework w wersji 1.1 lub wcześniejszej (który nie obsługuje <xref:System.Data.SqlClient.SqlBulkCopy> klasy), SQL Server Transact-SQL można wykonywać **BULK INSERT** przy użyciu instrukcji <xref:System.Data.SqlClient.SqlCommand> obiektu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Konfiguracja przykładu kopiowania zbiorczego](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)  
 W tym artykule opisano z tabelami używanymi w przykładach kopiowania zbiorczego i zawiera skrypty SQL do tworzenia tabel w bazie AdventureWorks.  
  
 [Pojedyncze operacje kopiowania zbiorczego](../../../../../docs/framework/data/adonet/sql/single-bulk-copy-operations.md)  
 W tym artykule opisano sposób wykonywania pojedynczej zbiorczej kopię danych do wystąpienia programu SQL Server używa <xref:System.Data.SqlClient.SqlBulkCopy> klasy i sposobu wykonywania operacji kopiowania zbiorczego za pomocą instrukcji języka Transact-SQL i <xref:System.Data.SqlClient.SqlCommand> klasy.  
  
 [Wiele operacji kopiowania zbiorczego](../../../../../docs/framework/data/adonet/sql/multiple-bulk-copy-operations.md)  
 W tym artykule opisano sposób wykonywania wiele operacji kopiowania zbiorczego danych do wystąpienia programu SQL Server przy użyciu <xref:System.Data.SqlClient.SqlBulkCopy> klasy.  
  
 [Transakcja i operacje kopiowania zbiorczego](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)  
 W tym artykule opisano sposób wykonywania operacji kopiowania zbiorczego, w ramach transakcji, w tym sposobu zatwierdzania lub wycofywania transakcji.  
  
## <a name="see-also"></a>Zobacz też  
 [SQL Server i ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
