---
title: Analizowanie kodu źródłowego LINQ to SQL
ms.date: 03/30/2017
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
ms.openlocfilehash: 35bc4988b8b9845ce6f45bab6849cd4b53a858ec
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592482"
---
# <a name="analyzing-linq-to-sql-source-code"></a><span data-ttu-id="31994-102">Analizowanie kodu źródłowego LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="31994-102">Analyzing LINQ to SQL Source Code</span></span>
<span data-ttu-id="31994-103">Za pomocą poniższej procedury, można wygenerować [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] źródła kodu z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="31994-103">By using the following steps, you can produce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] source code from the Northwind sample database.</span></span> <span data-ttu-id="31994-104">Można porównać elementów modelu obiektów z elementami bazy danych, aby lepiej widzieć jak inne elementy są zamapowane.</span><span class="sxs-lookup"><span data-stu-id="31994-104">You can compare elements of the object model with elements of the database to better see how different items are mapped.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="31994-105">Za pomocą programu Visual Studio deweloperzy mogą używać [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] do tworzenia tego kodu.</span><span class="sxs-lookup"><span data-stu-id="31994-105">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] to produce this code.</span></span>  
  
1. <span data-ttu-id="31994-106">Jeśli nie masz już przykładowej bazy danych Northwind na komputerze deweloperskim, możesz ją pobrać bezpłatnie.</span><span class="sxs-lookup"><span data-stu-id="31994-106">If you do not already have the Northwind sample database on your development computer, you can download it free of charge.</span></span> <span data-ttu-id="31994-107">Aby uzyskać więcej informacji, zobacz [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="31994-107">For more information, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
2. <span data-ttu-id="31994-108">Generowanie języka Visual Basic za pomocą narzędzia wiersza polecenia SqlMetal lub C# pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="31994-108">Use the SqlMetal command-line tool to generate a Visual Basic or C# source file.</span></span> <span data-ttu-id="31994-109">Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="31994-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span> <span data-ttu-id="31994-110">Wpisując następujące polecenia w wierszu polecenia, można wygenerować kodu języka Visual Basic i C# pliki źródłowe, które obejmują procedury składowane i funkcje:</span><span class="sxs-lookup"><span data-stu-id="31994-110">By typing the following commands at a command prompt, you can generate Visual Basic and C# source files that include stored procedures and functions:</span></span>  
  
    - `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    - `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a><span data-ttu-id="31994-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31994-111">See also</span></span>

- [<span data-ttu-id="31994-112">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="31994-112">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [<span data-ttu-id="31994-113">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="31994-113">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
