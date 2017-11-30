---
title: Wykonywanie zapytania drzewa XML (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e35c1ab-08c8-4378-9ca8-8ff344756eda
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1516cdc58effaa3e738210b948b43d7ed170890a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="querying-xml-trees-visual-basic"></a><span data-ttu-id="0ca6b-102">Wykonywanie zapytania drzewa XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ca6b-102">Querying XML Trees (Visual Basic)</span></span>
<span data-ttu-id="0ca6b-103">Ta sekcja zawiera przykłady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="0ca6b-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="0ca6b-104">Aby uzyskać więcej informacji na temat pisania [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytań, zobacz [wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="0ca6b-104">For more information about writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, see [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="0ca6b-105">Po ma uruchomiony drzewo XML, Pisanie zapytań jest najbardziej efektywny sposób wyodrębnić dane z drzewa.</span><span class="sxs-lookup"><span data-stu-id="0ca6b-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="0ca6b-106">Ponadto zapytań w połączeniu z funkcjonalności konstrukcji umożliwia generowanie nowego dokumentu XML, który ma inny kształt z oryginalnego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="0ca6b-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0ca6b-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="0ca6b-107">In This Section</span></span>  
  
|<span data-ttu-id="0ca6b-108">Temat</span><span class="sxs-lookup"><span data-stu-id="0ca6b-108">Topic</span></span>|<span data-ttu-id="0ca6b-109">Opis</span><span class="sxs-lookup"><span data-stu-id="0ca6b-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="0ca6b-110">Podstawowe zapytania (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ca6b-110">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)|<span data-ttu-id="0ca6b-111">Przykłady typowych kwerendy drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="0ca6b-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="0ca6b-112">Projekcje i przekształcenia (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ca6b-112">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="0ca6b-113">Przykłady typowych projekcji z i Przekształcanie XML drzewa.</span><span class="sxs-lookup"><span data-stu-id="0ca6b-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="0ca6b-114">Zaawansowane techniki zapytania (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ca6b-114">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="0ca6b-115">Udostępnia technik tworzenia zapytań, które są przydatne w bardziej zaawansowanych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="0ca6b-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="0ca6b-116">LINQ do XML dla wyrażenia XPath użytkowników (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ca6b-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)|<span data-ttu-id="0ca6b-117">Przedstawia liczbę wyrażenia XPath i ich [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] odpowiedniki.</span><span class="sxs-lookup"><span data-stu-id="0ca6b-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="0ca6b-118">Czysty funkcjonalności transformacji XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ca6b-118">Pure Functional Transformations of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)|<span data-ttu-id="0ca6b-119">Przedstawia informacje o małych samouczek dotyczący Pisanie zapytań w stylu programowanie funkcjonalne.</span><span class="sxs-lookup"><span data-stu-id="0ca6b-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0ca6b-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0ca6b-120">See Also</span></span>  
 [<span data-ttu-id="0ca6b-121">Przewodnik programowania w języku (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ca6b-121">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)  
 [<span data-ttu-id="0ca6b-122">Wprowadzenie do korzystania z LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0ca6b-122">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
