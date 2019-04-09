---
title: Integracja aparatu plików wykonywalnych języka wspólnego z programem SQL Server
ms.date: 03/30/2017
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
ms.openlocfilehash: d87f2b89583747b80ef103f419bd9bd2e3b1e0da
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089838"
---
# <a name="sql-server-common-language-runtime-integration"></a>Integracja aparatu plików wykonywalnych języka wspólnego z programem SQL Server
SQL Server 2005 wprowadzono integrację składnika wspólnego języka wspólnego (CLR) programu .NET Framework dla programu Microsoft Windows. Oznacza to, że można napisać procedury składowane, wyzwalacze, typy zdefiniowane przez użytkownika, funkcje zdefiniowane przez użytkownika, agregacje zdefiniowane przez użytkownika i przesyłania strumieniowego funkcji z wartościami przechowywanymi w tabeli przy użyciu dowolnego języka .NET Framework, w tym programu Microsoft Visual Basic .NET i Microsoft Visual C#. <xref:Microsoft.SqlServer.Server> Przestrzeń nazw zawiera zestaw nowych interfejsów programowania aplikacji (API), aby kod zarządzany może wchodzić w interakcje ze środowiskiem programu Microsoft SQL Server.  
  
 W tej sekcji opisano, funkcji i zachowań, które są specyficzne dla integrację środowiska uruchomieniowego (języka wspólnego CLR) języka wspólnego programu SQL Server i programu SQL Server w trakcie określonego rozszerzenia do zestawu ADO.NET.  
  
 Ta sekcja ma zapewnić tylko wystarczających informacji, aby rozpocząć programowanie z użyciem integracji środowiska CLR programu SQL Server i nie jest przeznaczona do wyczerpująca. Aby uzyskać szczegółowe informacje Zobacz wersję programu SQL Server — książki Online dla wersji programu SQL Server, którego używasz.  
  
 **SQL Server Books Online**  
  
1.  [Koncepcje programowania integracji wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR)](https://go.microsoft.com/fwlink/?LinkId=115240)  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wprowadzenie do integracji środowiska CLR programu SQL Server](../../../../../docs/framework/data/adonet/sql/introduction-to-sql-server-clr-integration.md)  
 Wprowadzenie do integracji środowiska CLR programu SQL Server. Zawiera łącza do dodatkowych tematów.  
  
 [Zdefiniowane przez użytkownika funkcje CLR](../../../../../docs/framework/data/adonet/sql/clr-user-defined-functions.md)  
 W tym artykule opisano sposób wdrażania i używać różnych typów funkcji CLR: wartościami przechowywanymi w tabeli, skalarną i zdefiniowanych przez użytkownika funkcji agregujących.  
  
 [Zdefiniowane przez użytkownika typy CLR](../../../../../docs/framework/data/adonet/sql/clr-user-defined-types.md)  
 Opisuje sposób wdrożenia i używania typy CLR zdefiniowane przez użytkownika. Zawiera łącza do dodatkowych tematów.  
  
 [Procedury składowane CLR](../../../../../docs/framework/data/adonet/sql/clr-stored-procedures.md)  
 W tym artykule opisano, jak implementować oraz procedury składowane CLR. Zawiera łącza do dodatkowych tematów.  
  
 [Wyzwalacze CLR](../../../../../docs/framework/data/adonet/sql/clr-triggers.md)  
 Opisuje sposób wdrożenia i używania wyzwalacze CLR. Zawiera łącza do dodatkowych tematów.  
  
 [Połączenie kontekstu](../../../../../docs/framework/data/adonet/sql/the-context-connection.md)  
 W tym artykule opisano połączenia kontekstu.  
  
 [Zachowanie w procesie specyficzne dla serwera SQL ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-in-process-specific-behavior-of-adonet.md)  
 Opisuje rozszerzenia określone w procesie programu SQL Server, ADO.NET i połączenia kontekstu. Zawiera łącza do dodatkowych tematów.  
  
## <a name="see-also"></a>Zobacz także

- [SQL Server i ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
