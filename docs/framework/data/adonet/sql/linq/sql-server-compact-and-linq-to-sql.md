---
title: SQL Server Compact i LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: b5a1a12018bd85cf313c1841e6b67ab2edf67b4a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792536"
---
# <a name="sql-server-compact-and-linq-to-sql"></a>SQL Server Compact i LINQ to SQL
SQL Server Compact jest domyślną bazą danych zainstalowaną z programem Visual Studio. Aby uzyskać więcej informacji, zobacz [używanie SQL Server Compact (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).  
  
 W tym temacie omówiono kluczowe różnice w zakresie użycia, konfiguracji, zestawów funkcji i zakresu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pomocy technicznej.  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a>Charakterystyka SQL Server Compact w odniesieniu do LINQ to SQL  
 Domyślnie program SQL Server Compact jest instalowany dla wszystkich wersji programu Visual Studio i dlatego jest dostępny na komputerze deweloperskim do użytku z programem [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Ale wdrożenie aplikacji, która używa SQL Server Compact i [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] różni się od tej dla aplikacji SQL Server. SQL Server Compact nie jest częścią .NET Framework i dlatego musi być spakowana z aplikacją lub pobierana oddzielnie z witryny firmy Microsoft.  
  
 Należy pamiętać o następujących cechach:  
  
- SQL Server Compact jest spakowany jako biblioteka DLL, która może być używana bezpośrednio dla plików bazy danych (rozszerzenie SDF).  
  
- SQL Server Compact uruchamiane w tym samym procesie co aplikacja kliencka. W związku z tym wydajność komunikacji z SQL Server Compactami może być znacznie wyższa niż komunikacja z SQL Server. Z drugiej strony, SQL Server Compact wymaga współdziałania między kodem zarządzanym i niezarządzanym z kosztami towarzyszącymi.  
  
- Rozmiar biblioteki DLL SQL Server Compact jest mały. Ta funkcja zmniejsza całkowity rozmiar aplikacji.  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Środowisko uruchomieniowe i narzędzie wiersza polecenia SQLMetal SQL Server Compact.  
  
- Object Relational Designer nie obsługuje SQL Server Compact.  
  
## <a name="feature-set"></a>Zestaw funkcji  
 Zestaw funkcji SQL Server Compact jest znacznie prostszy niż zestaw funkcji SQL Server w następujących sposobach, które mogą mieć wpływ na [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacje:  
  
- SQL Server Compact nie obsługuje procedur ani widoków składowanych.  
  
- SQL Server Compact obsługuje tylko podzbiór typów danych i funkcji SQL.  
  
- SQL Server Compact obsługuje tylko podzestaw konstrukcji SQL.  
  
- SQL Server Compact zapewnia tylko minimalny optymalizator. Istnieje możliwość, że niektóre zapytania mogą przekroczyć limit czasu.  
  
- SQL Server Compact nie obsługuje częściowej relacji zaufania.  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja](reference.md)
