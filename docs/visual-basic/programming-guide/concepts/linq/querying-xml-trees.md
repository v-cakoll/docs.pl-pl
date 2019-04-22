---
title: Tworzenie zapytań drzew XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 2e35c1ab-08c8-4378-9ca8-8ff344756eda
ms.openlocfilehash: 0d3855a562ce5ec43b28fba21b2ab4db0583a2d3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839629"
---
# <a name="querying-xml-trees-visual-basic"></a><span data-ttu-id="7b92c-102">Tworzenie zapytań drzew XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b92c-102">Querying XML Trees (Visual Basic)</span></span>
<span data-ttu-id="7b92c-103">Ta sekcja zawiera przykłady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="7b92c-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="7b92c-104">Aby uzyskać więcej informacji na temat pisania [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytań, zobacz [wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="7b92c-104">For more information about writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, see [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="7b92c-105">Po mają uruchomiony drzewa XML, Pisanie zapytań jest najbardziej skutecznym sposobem, aby wyodrębnić dane z drzewa.</span><span class="sxs-lookup"><span data-stu-id="7b92c-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="7b92c-106">Ponadto wykonywanie zapytań w połączeniu z konstrukcja funkcjonalna umożliwia generowanie nowego dokumentu XML, który ma innego kształtu z oryginalnego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="7b92c-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7b92c-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="7b92c-107">In This Section</span></span>  
  
|<span data-ttu-id="7b92c-108">Temat</span><span class="sxs-lookup"><span data-stu-id="7b92c-108">Topic</span></span>|<span data-ttu-id="7b92c-109">Opis</span><span class="sxs-lookup"><span data-stu-id="7b92c-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="7b92c-110">Podstawowe zapytania (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b92c-110">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)|<span data-ttu-id="7b92c-111">Zawiera przykłady typowych zapytań drzew XML.</span><span class="sxs-lookup"><span data-stu-id="7b92c-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="7b92c-112">Projekcje i przekształcenia (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b92c-112">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="7b92c-113">Przykłady typowych projekcji z i przekształcanie drzew XML.</span><span class="sxs-lookup"><span data-stu-id="7b92c-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="7b92c-114">Zaawansowane techniki zapytań (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b92c-114">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="7b92c-115">Zapewnia techniki tworzenia zapytań, które są przydatne w bardziej zaawansowanych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="7b92c-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="7b92c-116">LINQ to XML dla użytkowników metody XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b92c-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)|<span data-ttu-id="7b92c-117">Przedstawia informacje o liczbie wyrażenia XPath i ich [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] odpowiedniki.</span><span class="sxs-lookup"><span data-stu-id="7b92c-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="7b92c-118">Czyste Przekształcanie funkcjonalne kodu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b92c-118">Pure Functional Transformations of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)|<span data-ttu-id="7b92c-119">Przedstawia informacje o małej samouczek dotyczący Pisanie zapytań w stylu programowania funkcjonalnego.</span><span class="sxs-lookup"><span data-stu-id="7b92c-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7b92c-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7b92c-120">See also</span></span>

- [<span data-ttu-id="7b92c-121">Przewodnik programowania (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b92c-121">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
- [<span data-ttu-id="7b92c-122">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7b92c-122">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
