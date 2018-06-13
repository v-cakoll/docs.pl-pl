---
title: Analizowanie danych LINQ do SQL kodu źródłowego
ms.date: 03/30/2017
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
ms.openlocfilehash: 25c54fa67171b456b2eeb5c30f52d1e654fca995
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353757"
---
# <a name="analyzing-linq-to-sql-source-code"></a>Analizowanie danych LINQ do SQL kodu źródłowego
Za pomocą poniższych kroków, można utworzyć [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] źródła kodu z przykładowej bazy danych Northwind. Możesz porównać elementy modelu obiektów z elementami bazy danych, aby lepiej widoczne jak różne elementy są zamapowane.  
  
> [!NOTE]
>  Za pomocą programu Visual Studio deweloperzy mogą używać [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] do tworzenia tego kodu.  
  
1.  Jeśli w bazie danych Northwind nie jest już ma na komputerze deweloperskim, można pobrać bezpłatnie. Aby uzyskać więcej informacji, zobacz [pobieranie przykładowe bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
2.  Użyj narzędzia wiersza polecenia SqlMetal, aby wygenerować plik źródłowy języka Visual Basic lub C#. Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md). Wpisz następujące polecenia w wierszu polecenia, można wygenerować Visual Basic i C# plików źródłowych, które zawierają procedury składowane i funkcje:  
  
    -   `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    -   `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
