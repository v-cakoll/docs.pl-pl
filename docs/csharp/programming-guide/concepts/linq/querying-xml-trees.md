---
title: Zapytanie drzewa XML (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 0913d81b-541a-4fd4-9cbf-7ec89fd817ea
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 66028510b57981879412a1c2a161652adde340bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="querying-xml-trees-c"></a><span data-ttu-id="8fc64-102">Zapytanie drzewa XML (C#)</span><span class="sxs-lookup"><span data-stu-id="8fc64-102">Querying XML Trees (C#)</span></span>
<span data-ttu-id="8fc64-103">Ta sekcja zawiera przykłady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="8fc64-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="8fc64-104">Aby uzyskać więcej informacji na temat pisania [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytań, zobacz [wprowadzenie do LINQ w C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="8fc64-104">For more information about writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, see [Getting Started with LINQ in C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="8fc64-105">Po ma uruchomiony drzewo XML, Pisanie zapytań jest najbardziej efektywny sposób wyodrębnić dane z drzewa.</span><span class="sxs-lookup"><span data-stu-id="8fc64-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="8fc64-106">Ponadto zapytań w połączeniu z funkcjonalności konstrukcji umożliwia generowanie nowego dokumentu XML, który ma inny kształt z oryginalnego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="8fc64-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8fc64-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="8fc64-107">In This Section</span></span>  
  
|<span data-ttu-id="8fc64-108">Temat</span><span class="sxs-lookup"><span data-stu-id="8fc64-108">Topic</span></span>|<span data-ttu-id="8fc64-109">Opis</span><span class="sxs-lookup"><span data-stu-id="8fc64-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="8fc64-110">Podstawowe zapytania (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8fc64-110">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)|<span data-ttu-id="8fc64-111">Przykłady typowych kwerendy drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="8fc64-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="8fc64-112">Projekcje i przekształcenia (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8fc64-112">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="8fc64-113">Przykłady typowych projekcji z i Przekształcanie XML drzewa.</span><span class="sxs-lookup"><span data-stu-id="8fc64-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="8fc64-114">Zaawansowane techniki zapytania (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8fc64-114">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="8fc64-115">Udostępnia technik tworzenia zapytań, które są przydatne w bardziej zaawansowanych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="8fc64-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="8fc64-116">LINQ do XML dla użytkowników XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="8fc64-116">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)|<span data-ttu-id="8fc64-117">Przedstawia liczbę wyrażenia XPath i ich [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] odpowiedniki.</span><span class="sxs-lookup"><span data-stu-id="8fc64-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="8fc64-118">Czysty funkcjonalności transformacji XML (C#)</span><span class="sxs-lookup"><span data-stu-id="8fc64-118">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)|<span data-ttu-id="8fc64-119">Przedstawia informacje o małych samouczek dotyczący Pisanie zapytań w stylu programowanie funkcjonalne.</span><span class="sxs-lookup"><span data-stu-id="8fc64-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8fc64-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8fc64-120">See Also</span></span>  
 [<span data-ttu-id="8fc64-121">Przewodnik programowania w języku (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8fc64-121">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)  
 [<span data-ttu-id="8fc64-122">Wprowadzenie do korzystania z LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="8fc64-122">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
