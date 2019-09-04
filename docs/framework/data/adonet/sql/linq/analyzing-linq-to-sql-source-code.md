---
title: Analizowanie kodu źródłowego LINQ to SQL
ms.date: 03/30/2017
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
ms.openlocfilehash: dda19800a9aea0d644740c5378f6d5065181993e
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248080"
---
# <a name="analyzing-linq-to-sql-source-code"></a><span data-ttu-id="287e6-102">Analizowanie kodu źródłowego LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="287e6-102">Analyzing LINQ to SQL Source Code</span></span>
<span data-ttu-id="287e6-103">Wykonując poniższe kroki, można utworzyć [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kod źródłowy z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="287e6-103">By using the following steps, you can produce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] source code from the Northwind sample database.</span></span> <span data-ttu-id="287e6-104">Można porównać elementy modelu obiektów z elementami bazy danych, aby lepiej zobaczyć, jak są mapowane różne elementy.</span><span class="sxs-lookup"><span data-stu-id="287e6-104">You can compare elements of the object model with elements of the database to better see how different items are mapped.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="287e6-105">Deweloperzy korzystający z programu Visual Studio mogą używać projektanta O/R do tworzenia tego kodu.</span><span class="sxs-lookup"><span data-stu-id="287e6-105">Developers using Visual Studio can use the O/R Designer to produce this code.</span></span>  
  
1. <span data-ttu-id="287e6-106">Jeśli nie masz jeszcze przykładowej bazy danych Northwind na komputerze deweloperskim, możesz pobrać bezpłatnie.</span><span class="sxs-lookup"><span data-stu-id="287e6-106">If you do not already have the Northwind sample database on your development computer, you can download it free of charge.</span></span> <span data-ttu-id="287e6-107">Aby uzyskać więcej informacji, zobacz [Pobieranie przykładowych baz danych](downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="287e6-107">For more information, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span>  
  
2. <span data-ttu-id="287e6-108">Użyj narzędzia wiersza polecenia SqlMetal, aby wygenerować Visual Basic lub C# plik źródłowy.</span><span class="sxs-lookup"><span data-stu-id="287e6-108">Use the SqlMetal command-line tool to generate a Visual Basic or C# source file.</span></span> <span data-ttu-id="287e6-109">Aby uzyskać więcej informacji, zobacz [SQLMetal. exe (Narzędzie generowania kodu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="287e6-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span> <span data-ttu-id="287e6-110">Wpisując następujące polecenia w wierszu polecenia, można generować Visual Basic i C# pliki źródłowe, które zawierają procedury składowane i funkcje:</span><span class="sxs-lookup"><span data-stu-id="287e6-110">By typing the following commands at a command prompt, you can generate Visual Basic and C# source files that include stored procedures and functions:</span></span>  
  
    - `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    - `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a><span data-ttu-id="287e6-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="287e6-111">See also</span></span>

- [<span data-ttu-id="287e6-112">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="287e6-112">Reference</span></span>](reference.md)
- [<span data-ttu-id="287e6-113">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="287e6-113">Background Information</span></span>](background-information.md)
