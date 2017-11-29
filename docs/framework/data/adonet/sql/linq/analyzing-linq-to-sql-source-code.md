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
# <a name="analyzing-linq-to-sql-source-code"></a><span data-ttu-id="15a15-102">Analizowanie danych LINQ do SQL kodu źródłowego</span><span class="sxs-lookup"><span data-stu-id="15a15-102">Analyzing LINQ to SQL Source Code</span></span>
<span data-ttu-id="15a15-103">Za pomocą poniższych kroków, można utworzyć [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] źródła kodu z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="15a15-103">By using the following steps, you can produce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] source code from the Northwind sample database.</span></span> <span data-ttu-id="15a15-104">Możesz porównać elementy modelu obiektów z elementami bazy danych, aby lepiej widoczne jak różne elementy są zamapowane.</span><span class="sxs-lookup"><span data-stu-id="15a15-104">You can compare elements of the object model with elements of the database to better see how different items are mapped.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15a15-105">Deweloperzy przy użyciu [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] można użyć [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] do tworzenia tego kodu.</span><span class="sxs-lookup"><span data-stu-id="15a15-105">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can use the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] to produce this code.</span></span>  
  
1.  <span data-ttu-id="15a15-106">Jeśli w bazie danych Northwind nie jest już ma na komputerze deweloperskim, można pobrać bezpłatnie.</span><span class="sxs-lookup"><span data-stu-id="15a15-106">If you do not already have the Northwind sample database on your development computer, you can download it free of charge.</span></span> <span data-ttu-id="15a15-107">Aby uzyskać więcej informacji, zobacz [pobieranie przykładowe bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="15a15-107">For more information, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
2.  <span data-ttu-id="15a15-108">Użyj narzędzia wiersza polecenia SqlMetal, aby wygenerować plik źródłowy języka Visual Basic lub C#.</span><span class="sxs-lookup"><span data-stu-id="15a15-108">Use the SqlMetal command-line tool to generate a Visual Basic or C# source file.</span></span> <span data-ttu-id="15a15-109">Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="15a15-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span> <span data-ttu-id="15a15-110">Wpisz następujące polecenia w wierszu polecenia, można wygenerować Visual Basic i C# plików źródłowych, które zawierają procedury składowane i funkcje:</span><span class="sxs-lookup"><span data-stu-id="15a15-110">By typing the following commands at a command prompt, you can generate Visual Basic and C# source files that include stored procedures and functions:</span></span>  
  
    -   `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    -   `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a><span data-ttu-id="15a15-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15a15-111">See Also</span></span>  
 [<span data-ttu-id="15a15-112">Odwołanie</span><span class="sxs-lookup"><span data-stu-id="15a15-112">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 [<span data-ttu-id="15a15-113">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="15a15-113">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
