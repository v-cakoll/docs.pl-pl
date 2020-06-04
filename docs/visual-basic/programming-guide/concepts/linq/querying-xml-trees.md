---
title: Tworzenie zapytań dotyczących drzew XML
ms.date: 07/20/2015
ms.assetid: 2e35c1ab-08c8-4378-9ca8-8ff344756eda
ms.openlocfilehash: 22e3dd873e2be8381f3d8da8f7c4284d09e45543
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411873"
---
# <a name="querying-xml-trees-visual-basic"></a><span data-ttu-id="fe49f-102">Wykonywanie zapytania dotyczącego drzew XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe49f-102">Querying XML Trees (Visual Basic)</span></span>
<span data-ttu-id="fe49f-103">Ta sekcja zawiera przykłady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytań.</span><span class="sxs-lookup"><span data-stu-id="fe49f-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="fe49f-104">Aby uzyskać więcej informacji na temat pisania zapytań LINQ, zobacz [wprowadzenie with LINQ in Visual Basic](getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="fe49f-104">For more information about writing LINQ queries, see [Getting Started with LINQ in Visual Basic](getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="fe49f-105">Po utworzeniu wystąpienia drzewa XML, Pisanie zapytań jest najbardziej skutecznym sposobem wyodrębnienia danych z drzewa.</span><span class="sxs-lookup"><span data-stu-id="fe49f-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="fe49f-106">Ponadto zapytanie połączone z konstrukcją funkcjonalną umożliwia wygenerowanie nowego dokumentu XML, który ma inny kształt od oryginalnego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="fe49f-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fe49f-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="fe49f-107">In This Section</span></span>  
  
|<span data-ttu-id="fe49f-108">Temat</span><span class="sxs-lookup"><span data-stu-id="fe49f-108">Topic</span></span>|<span data-ttu-id="fe49f-109">Opis</span><span class="sxs-lookup"><span data-stu-id="fe49f-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="fe49f-110">Zapytania podstawowe (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe49f-110">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](basic-queries-linq-to-xml.md)|<span data-ttu-id="fe49f-111">Zawiera typowe przykłady tworzenia zapytań dotyczących drzew XML.</span><span class="sxs-lookup"><span data-stu-id="fe49f-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="fe49f-112">Projekcje i przekształcenia (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe49f-112">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="fe49f-113">Zawiera typowe przykłady projekcji i transformacji drzew XML.</span><span class="sxs-lookup"><span data-stu-id="fe49f-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="fe49f-114">Zaawansowane techniki zapytań (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe49f-114">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="fe49f-115">Zapewnia techniki zapytań, które są przydatne w bardziej zaawansowanych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="fe49f-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="fe49f-116">LINQ to XML dla użytkowników XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe49f-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)|<span data-ttu-id="fe49f-117">Przedstawia liczbę wyrażeń XPath i ich [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] odpowiedników.</span><span class="sxs-lookup"><span data-stu-id="fe49f-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="fe49f-118">Czystej funkcjonalne przekształcenia XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe49f-118">Pure Functional Transformations of XML (Visual Basic)</span></span>](pure-functional-transformations-of-xml.md)|<span data-ttu-id="fe49f-119">Prezentuje niewielki samouczek dotyczący pisania zapytań w stylu programowania funkcjonalnego.</span><span class="sxs-lookup"><span data-stu-id="fe49f-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fe49f-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe49f-120">See also</span></span>

- [<span data-ttu-id="fe49f-121">Przewodnik programowania (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe49f-121">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](programming-guide-linq-to-xml.md)
- [<span data-ttu-id="fe49f-122">Wprowadzenie do programu LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fe49f-122">Getting Started with LINQ in Visual Basic</span></span>](getting-started-with-linq.md)
