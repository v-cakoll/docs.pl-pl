---
title: Tworzenie zapytań drzew XML (C#)
ms.date: 07/20/2015
ms.assetid: 0913d81b-541a-4fd4-9cbf-7ec89fd817ea
ms.openlocfilehash: 71a3d8538d96a9a5c273188a1bbb920ad6fa2d37
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61680977"
---
# <a name="querying-xml-trees-c"></a><span data-ttu-id="2659e-102">Tworzenie zapytań drzew XML (C#)</span><span class="sxs-lookup"><span data-stu-id="2659e-102">Querying XML Trees (C#)</span></span>
<span data-ttu-id="2659e-103">Ta sekcja zawiera przykłady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="2659e-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="2659e-104">Aby uzyskać więcej informacji na temat pisania [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytań, zobacz [wprowadzenie do LINQ w C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="2659e-104">For more information about writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, see [Getting Started with LINQ in C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="2659e-105">Po mają uruchomiony drzewa XML, Pisanie zapytań jest najbardziej skutecznym sposobem, aby wyodrębnić dane z drzewa.</span><span class="sxs-lookup"><span data-stu-id="2659e-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="2659e-106">Ponadto wykonywanie zapytań w połączeniu z konstrukcja funkcjonalna umożliwia generowanie nowego dokumentu XML, który ma innego kształtu z oryginalnego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="2659e-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2659e-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="2659e-107">In This Section</span></span>  
  
|<span data-ttu-id="2659e-108">Temat</span><span class="sxs-lookup"><span data-stu-id="2659e-108">Topic</span></span>|<span data-ttu-id="2659e-109">Opis</span><span class="sxs-lookup"><span data-stu-id="2659e-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="2659e-110">Podstawowe zapytania (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2659e-110">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)|<span data-ttu-id="2659e-111">Zawiera przykłady typowych zapytań drzew XML.</span><span class="sxs-lookup"><span data-stu-id="2659e-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="2659e-112">Projekcje i przekształcenia (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2659e-112">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="2659e-113">Przykłady typowych projekcji z i przekształcanie drzew XML.</span><span class="sxs-lookup"><span data-stu-id="2659e-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="2659e-114">Zaawansowane techniki zapytań (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2659e-114">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="2659e-115">Zapewnia techniki tworzenia zapytań, które są przydatne w bardziej zaawansowanych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="2659e-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="2659e-116">LINQ to XML dla użytkowników metody XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="2659e-116">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)|<span data-ttu-id="2659e-117">Przedstawia informacje o liczbie wyrażenia XPath i ich [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] odpowiedniki.</span><span class="sxs-lookup"><span data-stu-id="2659e-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="2659e-118">Czyste Przekształcanie funkcjonalne kodu XML (C#)</span><span class="sxs-lookup"><span data-stu-id="2659e-118">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)|<span data-ttu-id="2659e-119">Przedstawia informacje o małej samouczek dotyczący Pisanie zapytań w stylu programowania funkcjonalnego.</span><span class="sxs-lookup"><span data-stu-id="2659e-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2659e-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2659e-120">See also</span></span>

- [<span data-ttu-id="2659e-121">Przewodnik programowania (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2659e-121">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
- [<span data-ttu-id="2659e-122">Wprowadzenie do korzystania z LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="2659e-122">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
