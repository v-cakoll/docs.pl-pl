---
title: Analizowanie kodu źródłowego LINQ to SQL
ms.date: 03/30/2017
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
ms.openlocfilehash: 1110e64d16a6c2790939cc695ecd67e37ec109e4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203291"
---
# <a name="analyzing-linq-to-sql-source-code"></a>Analizowanie kodu źródłowego LINQ to SQL
Za pomocą poniższej procedury, można wygenerować [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] źródła kodu z przykładowej bazy danych Northwind. Można porównać elementów modelu obiektów z elementami bazy danych, aby lepiej widzieć jak inne elementy są zamapowane.  
  
> [!NOTE]
>  Za pomocą programu Visual Studio deweloperzy mogą używać [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] do tworzenia tego kodu.  
  
1.  Jeśli nie masz już przykładowej bazy danych Northwind na komputerze deweloperskim, możesz ją pobrać bezpłatnie. Aby uzyskać więcej informacji, zobacz [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
2.  Generowanie języka Visual Basic za pomocą narzędzia wiersza polecenia SqlMetal lub C# pliku źródłowego. Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md). Wpisując następujące polecenia w wierszu polecenia, można wygenerować kodu języka Visual Basic i C# pliki źródłowe, które obejmują procedury składowane i funkcje:  
  
    -   `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    -   `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a>Zobacz także

- [Tematy pomocy](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
