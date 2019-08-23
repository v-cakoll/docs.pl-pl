---
title: Analizowanie kodu źródłowego LINQ to SQL
ms.date: 03/30/2017
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
ms.openlocfilehash: 4b23e0df1ee762dd22d43cd1be050db70481db50
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964113"
---
# <a name="analyzing-linq-to-sql-source-code"></a><span data-ttu-id="bd72a-102">Analizowanie kodu źródłowego LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="bd72a-102">Analyzing LINQ to SQL Source Code</span></span>
<span data-ttu-id="bd72a-103">Wykonując poniższe kroki, można utworzyć [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kod źródłowy z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="bd72a-103">By using the following steps, you can produce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] source code from the Northwind sample database.</span></span> <span data-ttu-id="bd72a-104">Można porównać elementy modelu obiektów z elementami bazy danych, aby lepiej zobaczyć, jak są mapowane różne elementy.</span><span class="sxs-lookup"><span data-stu-id="bd72a-104">You can compare elements of the object model with elements of the database to better see how different items are mapped.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bd72a-105">Deweloperzy korzystający z programu Visual Studio mogą używać projektanta O/R do tworzenia tego kodu.</span><span class="sxs-lookup"><span data-stu-id="bd72a-105">Developers using Visual Studio can use the O/R Designer to produce this code.</span></span>  
  
1. <span data-ttu-id="bd72a-106">Jeśli nie masz jeszcze przykładowej bazy danych Northwind na komputerze deweloperskim, możesz pobrać bezpłatnie.</span><span class="sxs-lookup"><span data-stu-id="bd72a-106">If you do not already have the Northwind sample database on your development computer, you can download it free of charge.</span></span> <span data-ttu-id="bd72a-107">Aby uzyskać więcej informacji, zobacz [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="bd72a-107">For more information, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
2. <span data-ttu-id="bd72a-108">Użyj narzędzia wiersza polecenia SqlMetal, aby wygenerować Visual Basic lub C# plik źródłowy.</span><span class="sxs-lookup"><span data-stu-id="bd72a-108">Use the SqlMetal command-line tool to generate a Visual Basic or C# source file.</span></span> <span data-ttu-id="bd72a-109">Aby uzyskać więcej informacji, zobacz [SQLMetal. exe (Narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="bd72a-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span> <span data-ttu-id="bd72a-110">Wpisując następujące polecenia w wierszu polecenia, można generować Visual Basic i C# pliki źródłowe, które zawierają procedury składowane i funkcje:</span><span class="sxs-lookup"><span data-stu-id="bd72a-110">By typing the following commands at a command prompt, you can generate Visual Basic and C# source files that include stored procedures and functions:</span></span>  
  
    - `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    - `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a><span data-ttu-id="bd72a-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd72a-111">See also</span></span>

- [<span data-ttu-id="bd72a-112">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="bd72a-112">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [<span data-ttu-id="bd72a-113">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="bd72a-113">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
