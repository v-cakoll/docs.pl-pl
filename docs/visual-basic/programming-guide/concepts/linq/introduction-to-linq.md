---
title: Wprowadzenie do LINQ (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c6339c12-9b2d-433e-961c-0d2b7f0091c2
ms.openlocfilehash: 95c1d99604ba9f87e34b5bb423d42bf97c0cd29e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648795"
---
# <a name="introduction-to-linq-visual-basic"></a><span data-ttu-id="8bdd5-102">Wprowadzenie do LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bdd5-102">Introduction to LINQ (Visual Basic)</span></span>
<span data-ttu-id="8bdd5-103">Language-Integrated Query (LINQ) jest innowacje wprowadzone w programie .NET Framework w wersji 3.5 tego mostków lukę między obiektami w świecie, a światem danych.</span><span class="sxs-lookup"><span data-stu-id="8bdd5-103">Language-Integrated Query (LINQ) is an innovation introduced in the .NET Framework version 3.5 that bridges the gap between the world of objects and the world of data.</span></span>  
  
 <span data-ttu-id="8bdd5-104">Tradycyjne zapytania dotyczące danych są wyrażane jako zwykłe ciągi bez typu sprawdzania w kompilacji czasu lub obsługę funkcji IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="8bdd5-104">Traditionally, queries against data are expressed as simple strings without type checking at compile time or IntelliSense support.</span></span> <span data-ttu-id="8bdd5-105">Ponadto konieczne będzie uczenia się języka zapytań różne dla każdego typu źródła danych: Bazy danych SQL, dokumentów XML, różnych usług sieci Web i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="8bdd5-105">Furthermore, you have to learn a different query language for each type of data source: SQL databases, XML documents, various Web services, and so on.</span></span> <span data-ttu-id="8bdd5-106">LINQ sprawia, że *zapytania* staje się konstrukcją języka w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8bdd5-106">LINQ makes a *query* a first-class language construct in Visual Basic.</span></span> <span data-ttu-id="8bdd5-107">Możesz pisać zapytania dotyczące kolekcje silnie typizowanych obiektów przy użyciu dobrze znanych operatory i słowa kluczowe języka.</span><span class="sxs-lookup"><span data-stu-id="8bdd5-107">You write queries against strongly typed collections of objects by using language keywords and familiar operators.</span></span>  
  
 <span data-ttu-id="8bdd5-108">Możesz pisać zapytania LINQ w Visual Basic dla programu SQL Server baz danych, XML dokumenty, zestawami danych ADO.NET i kolekcji obiektów, która obsługuje <xref:System.Collections.IEnumerable> lub ogólny <xref:System.Collections.Generic.IEnumerable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="8bdd5-108">You can write LINQ queries in Visual Basic for SQL Server databases, XML documents, ADO.NET Datasets, and any collection of objects that supports <xref:System.Collections.IEnumerable> or the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="8bdd5-109">LINQ jest również obsługiwane przez strony trzecie dla wielu usług sieci Web oraz inne implementacje bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8bdd5-109">LINQ support is also provided by third parties for many Web services and other database implementations.</span></span>  
  
 <span data-ttu-id="8bdd5-110">W nowych projektach, lub obok zapytania non-LINQ w istniejących projektów, można użyć zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="8bdd5-110">You can use LINQ queries in new projects, or alongside non-LINQ queries in existing projects.</span></span> <span data-ttu-id="8bdd5-111">Jedynym wymaganiem jest, że projekt przeznaczony dla .NET Framework 3.5 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="8bdd5-111">The only requirement is that the project target .NET Framework 3.5 or later.</span></span>  
  
 <span data-ttu-id="8bdd5-112">Na poniższej ilustracji w programie Visual Studio pokazuje zapytanie LINQ z częściowo ukończone w bazie danych programu SQL Server w językach C# i Visual Basic z obsługą funkcji IntelliSense i kontrola typów w pełnej.</span><span class="sxs-lookup"><span data-stu-id="8bdd5-112">The following illustration from Visual Studio shows a partially-completed LINQ query against a SQL Server database in both C# and Visual Basic with full type checking and IntelliSense support.</span></span>  
  
 ![Diagram tego shwos zapytanie LINQ, za pomocą funkcji Intellisense.](./media/introduction-to-linq/linq-query-intellisense.png)  
  
## <a name="next-steps"></a><span data-ttu-id="8bdd5-114">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="8bdd5-114">Next Steps</span></span>  
 <span data-ttu-id="8bdd5-115">Aby dowiedzieć się więcej na temat LINQ, należy rozpocząć od staje się poznać niektóre podstawowe pojęcia związane z sekcji wprowadzenie [wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md), a następnie zapoznaj się z dokumentacją dla technologii LINQ, w którym są Czy chcesz:</span><span class="sxs-lookup"><span data-stu-id="8bdd5-115">To learn more details about LINQ, start by becoming familiar with some basic concepts in the Getting Started section [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md), and then read the documentation for the LINQ technology in which you are interested:</span></span>  
  
- <span data-ttu-id="8bdd5-116">Bazy danych programu SQL Server: [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="8bdd5-116">SQL Server databases: [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)</span></span>  
  
- <span data-ttu-id="8bdd5-117">Dokumenty XML: [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="8bdd5-117">XML documents: [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)</span></span>  
  
- <span data-ttu-id="8bdd5-118">ADO.NET Datasets: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span><span class="sxs-lookup"><span data-stu-id="8bdd5-118">ADO.NET Datasets: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span></span>  
  
- <span data-ttu-id="8bdd5-119">Kolekcje .NET, plików, parametry i tak dalej: [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)</span><span class="sxs-lookup"><span data-stu-id="8bdd5-119">.NET collections, files, strings and so on: [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bdd5-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8bdd5-120">See also</span></span>

- [<span data-ttu-id="8bdd5-121">Zapytanie o języku zintegrowanym (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bdd5-121">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/index.md)
