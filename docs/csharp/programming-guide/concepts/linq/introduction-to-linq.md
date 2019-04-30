---
title: Wprowadzenie do LINQ (C#)
ms.date: 07/20/2015
ms.assetid: 54874feb-55e5-4ca8-a9d6-1c1127fd7fb1
ms.openlocfilehash: ea17de41bbbc03158179f207aa0bc9fc9cceb863
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667541"
---
# <a name="introduction-to-linq-c"></a><span data-ttu-id="aac8a-102">Wprowadzenie do LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="aac8a-102">Introduction to LINQ (C#)</span></span>
<span data-ttu-id="aac8a-103">Language-Integrated Query (LINQ) jest innowacje wprowadzone w programie .NET Framework w wersji 3.5 tego mostków lukę między obiektami w świecie, a światem danych.</span><span class="sxs-lookup"><span data-stu-id="aac8a-103">Language-Integrated Query (LINQ) is an innovation introduced in the .NET Framework version 3.5 that bridges the gap between the world of objects and the world of data.</span></span>  
  
 <span data-ttu-id="aac8a-104">Tradycyjne zapytania dotyczące danych są wyrażane jako zwykłe ciągi bez typu sprawdzania w kompilacji czasu lub obsługę funkcji IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="aac8a-104">Traditionally, queries against data are expressed as simple strings without type checking at compile time or IntelliSense support.</span></span> <span data-ttu-id="aac8a-105">Ponadto konieczne będzie uczenia się języka zapytań różne dla każdego typu źródła danych: Bazy danych SQL, dokumentów XML, różnych usług sieci Web i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="aac8a-105">Furthermore, you have to learn a different query language for each type of data source: SQL databases, XML documents, various Web services, and so on.</span></span> <span data-ttu-id="aac8a-106">LINQ sprawia, że *zapytania* staje się konstrukcją języka w języku C#.</span><span class="sxs-lookup"><span data-stu-id="aac8a-106">LINQ makes a *query* a first-class language construct in C#.</span></span> <span data-ttu-id="aac8a-107">Możesz pisać zapytania dotyczące kolekcje silnie typizowanych obiektów przy użyciu dobrze znanych operatory i słowa kluczowe języka.</span><span class="sxs-lookup"><span data-stu-id="aac8a-107">You write queries against strongly typed collections of objects by using language keywords and familiar operators.</span></span>  
  
 <span data-ttu-id="aac8a-108">Możesz pisać zapytania LINQ w C# dla programu SQL Server baz danych, XML dokumenty, zestawami danych ADO.NET i kolekcji obiektów, która obsługuje <xref:System.Collections.IEnumerable> lub ogólny <xref:System.Collections.Generic.IEnumerable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="aac8a-108">You can write LINQ queries in C# for SQL Server databases, XML documents, ADO.NET Datasets, and any collection of objects that supports <xref:System.Collections.IEnumerable> or the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="aac8a-109">LINQ jest również obsługiwane przez strony trzecie dla wielu usług sieci Web oraz inne implementacje bazy danych.</span><span class="sxs-lookup"><span data-stu-id="aac8a-109">LINQ support is also provided by third parties for many Web services and other database implementations.</span></span>  
  
 <span data-ttu-id="aac8a-110">W nowych projektach, lub obok zapytania non-LINQ w istniejących projektów, można użyć zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="aac8a-110">You can use LINQ queries in new projects, or alongside non-LINQ queries in existing projects.</span></span> <span data-ttu-id="aac8a-111">Jedynym wymaganiem jest, że projekt przeznaczony dla .NET Framework 3.5 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="aac8a-111">The only requirement is that the project target .NET Framework 3.5 or later.</span></span>  
  
 <span data-ttu-id="aac8a-112">Na poniższej ilustracji w programie Visual Studio pokazuje zapytanie LINQ z częściowo ukończone w bazie danych programu SQL Server w obu C# i Visual Basic z pełną sprawdzenie i obsługę funkcji IntelliSense:</span><span class="sxs-lookup"><span data-stu-id="aac8a-112">The following illustration from Visual Studio shows a partially-completed LINQ query against a SQL Server database in both C# and Visual Basic with full type checking and IntelliSense support:</span></span>  
  
 ![Diagram, który pokazuje zapytanie LINQ, za pomocą funkcji Intellisense.](./media/introduction-to-linq/linq-query-intellisense.png)  
  
## <a name="next-steps"></a><span data-ttu-id="aac8a-114">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="aac8a-114">Next Steps</span></span>  
 <span data-ttu-id="aac8a-115">Aby dowiedzieć się więcej na temat LINQ, należy rozpocząć od staje się poznać niektóre podstawowe pojęcia związane z sekcji wprowadzenie [wprowadzenie do LINQ w C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md), a następnie zapoznaj się z dokumentacją dla technologii LINQ, w którym interesuje Cię:</span><span class="sxs-lookup"><span data-stu-id="aac8a-115">To learn more details about LINQ, start by becoming familiar with some basic concepts in the Getting Started section [Getting Started with LINQ in C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md), and then read the documentation for the LINQ technology in which you are interested:</span></span>  
  
- <span data-ttu-id="aac8a-116">Bazy danych programu SQL Server: [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="aac8a-116">SQL Server databases: [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)</span></span>  
  
- <span data-ttu-id="aac8a-117">Dokumenty XML: [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="aac8a-117">XML documents: [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)</span></span>  
  
- <span data-ttu-id="aac8a-118">ADO.NET Datasets: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span><span class="sxs-lookup"><span data-stu-id="aac8a-118">ADO.NET Datasets: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span></span>  
  
- <span data-ttu-id="aac8a-119">Kolekcje .NET, plików, parametry i tak dalej: [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)</span><span class="sxs-lookup"><span data-stu-id="aac8a-119">.NET collections, files, strings and so on: [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aac8a-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aac8a-120">See also</span></span>

- [<span data-ttu-id="aac8a-121">Zapytanie o języku zintegrowanym (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="aac8a-121">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)
