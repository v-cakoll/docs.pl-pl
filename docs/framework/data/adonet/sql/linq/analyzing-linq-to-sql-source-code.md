---
title: "Analizowanie danych LINQ do SQL kodu źródłowego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0e1677d8e30b083efe99f916b28672ddb6c3dd99
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="analyzing-linq-to-sql-source-code"></a>Analizowanie danych LINQ do SQL kodu źródłowego
Za pomocą poniższych kroków, można utworzyć [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] źródła kodu z przykładowej bazy danych Northwind. Możesz porównać elementy modelu obiektów z elementami bazy danych, aby lepiej widoczne jak różne elementy są zamapowane.  
  
> [!NOTE]
>  Deweloperzy przy użyciu [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] można użyć [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] do tworzenia tego kodu.  
  
1.  Jeśli w bazie danych Northwind nie jest już ma na komputerze deweloperskim, można pobrać bezpłatnie. Aby uzyskać więcej informacji, zobacz [pobieranie przykładowe bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
2.  Użyj narzędzia wiersza polecenia SqlMetal, aby wygenerować plik źródłowy języka Visual Basic lub C#. Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md). Wpisz następujące polecenia w wierszu polecenia, można wygenerować Visual Basic i C# plików źródłowych, które zawierają procedury składowane i funkcje:  
  
    -   `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    -   `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
