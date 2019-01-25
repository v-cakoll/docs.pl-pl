---
title: Analizowanie danych LINQ to SQL kod źródłowy
ms.date: 03/30/2017
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
ms.openlocfilehash: 4b1d2d2c54ae99a65f60c96b6330e3f94db6beb5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696857"
---
# <a name="analyzing-linq-to-sql-source-code"></a><span data-ttu-id="8353d-102">Analizowanie danych LINQ to SQL kod źródłowy</span><span class="sxs-lookup"><span data-stu-id="8353d-102">Analyzing LINQ to SQL Source Code</span></span>
<span data-ttu-id="8353d-103">Za pomocą poniższej procedury, można wygenerować [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] źródła kodu z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="8353d-103">By using the following steps, you can produce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] source code from the Northwind sample database.</span></span> <span data-ttu-id="8353d-104">Można porównać elementów modelu obiektów z elementami bazy danych, aby lepiej widzieć jak inne elementy są zamapowane.</span><span class="sxs-lookup"><span data-stu-id="8353d-104">You can compare elements of the object model with elements of the database to better see how different items are mapped.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8353d-105">Za pomocą programu Visual Studio deweloperzy mogą używać [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] do tworzenia tego kodu.</span><span class="sxs-lookup"><span data-stu-id="8353d-105">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] to produce this code.</span></span>  
  
1.  <span data-ttu-id="8353d-106">Jeśli nie masz już przykładowej bazy danych Northwind na komputerze deweloperskim, możesz ją pobrać bezpłatnie.</span><span class="sxs-lookup"><span data-stu-id="8353d-106">If you do not already have the Northwind sample database on your development computer, you can download it free of charge.</span></span> <span data-ttu-id="8353d-107">Aby uzyskać więcej informacji, zobacz [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="8353d-107">For more information, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
2.  <span data-ttu-id="8353d-108">Generowanie języka Visual Basic za pomocą narzędzia wiersza polecenia SqlMetal lub C# pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="8353d-108">Use the SqlMetal command-line tool to generate a Visual Basic or C# source file.</span></span> <span data-ttu-id="8353d-109">Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="8353d-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span> <span data-ttu-id="8353d-110">Wpisując następujące polecenia w wierszu polecenia, można wygenerować kodu języka Visual Basic i C# pliki źródłowe, które obejmują procedury składowane i funkcje:</span><span class="sxs-lookup"><span data-stu-id="8353d-110">By typing the following commands at a command prompt, you can generate Visual Basic and C# source files that include stored procedures and functions:</span></span>  
  
    -   `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    -   `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a><span data-ttu-id="8353d-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8353d-111">See also</span></span>
- [<span data-ttu-id="8353d-112">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="8353d-112">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [<span data-ttu-id="8353d-113">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="8353d-113">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
