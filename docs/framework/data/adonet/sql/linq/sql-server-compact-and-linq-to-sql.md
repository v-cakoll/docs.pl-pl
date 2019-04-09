---
title: SQL Server Compact i LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: db3f7aef082d965dc27b69f5a966ff038c0ffac0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145720"
---
# <a name="sql-server-compact-and-linq-to-sql"></a>SQL Server Compact i LINQ to SQL
SQL Server Compact to domyślna baza danych zainstalowana za pomocą programu Visual Studio. Aby uzyskać więcej informacji, zobacz [przy użyciu programu SQL Server Compact (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).  
  
 W tym temacie opisano podstawowe różnice w użycia, konfiguracji, zestawy funkcji i zakres [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pomocy technicznej.  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a>Właściwości programu SQL Server Compact w odniesieniu do programu LINQ to SQL  
 Domyślnie programu SQL Server Compact są zainstalowane dla wszystkich wersji programu Visual Studio i w związku z tym jest dostępny na komputerze deweloperskim do użytku z programem [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Ale wdrożenia aplikacji, która używa programu SQL Server Compact i [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] różni się od tego dla aplikacji programu SQL Server. SQL Server Compact nie jest częścią programu .NET Framework i w związku z tym musi być pakowane razem z aplikacją lub pobrane oddzielnie z witryny Microsoft.  
  
 Należy zwrócić uwagę następujących właściwości:  
  
-   SQL Server Compact jest spakowany jako bibliotekę DLL, która może zostać użyty dla plików bazy danych (z rozszerzeniem sdf) bezpośrednio.  
  
-   SQL Server Compact działa w tym samym procesie co aplikacja kliencka. Wydajność komunikacji przy użyciu programu SQL Server Compact, dlatego może być znacznie wyższa niż podczas komunikowania się z programem SQL Server. Z drugiej strony SQL Server Compact wymagają współdziałanie między kodem zarządzanym i niezarządzanym jego towarzyszącej kosztów.  
  
-   Rozmiar programu SQL Server Compact biblioteki DLL jest mały. Ta funkcja zmniejsza rozmiar cała aplikacja.  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Środowiska uruchomieniowego i narzędzie wiersza polecenia SQLMetal obsługi programu SQL Server Compact.  
  
-   [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Nie obsługuje programu SQL Server Compact.  
  
## <a name="feature-set"></a>Zestaw funkcji  
 SQL Server Compact zestaw funkcji jest znacznie prostsze niż zestaw funkcji programu SQL Server w następujący sposób, który może mieć wpływ na [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji:  
  
-   SQL Server Compact nie obsługuje procedur przechowywanych lub widoków.  
  
-   SQL Server Compact obsługuje tylko podzbiór typów danych i funkcji SQL.  
  
-   SQL Server Compact obsługuje tylko podzbiór konstrukcji SQL.  
  
-   SQL Server Compact zawiera tylko minimalne optymalizatora. Istnieje możliwość, że niektóre zapytania może upłynąć limit czasu.  
  
-   SQL Server Compact nie obsługuje częściowej relacji zaufania.  
  
## <a name="see-also"></a>Zobacz także

- [Tematy pomocy](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
