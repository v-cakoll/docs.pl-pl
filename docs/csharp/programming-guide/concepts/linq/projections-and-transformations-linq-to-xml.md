---
title: "Projekcje i przekształcenia (LINQ do XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: bb0457ab-1823-47e6-9d2d-c93c958cc913
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 81172ebb440bc2737bbe3f1de0f1dd3cf6e086c4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="projections-and-transformations-linq-to-xml-c"></a><span data-ttu-id="aaaf3-102">Projekcje i przekształcenia (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="aaaf3-102">Projections and Transformations (LINQ to XML) (C#)</span></span>
<span data-ttu-id="aaaf3-103">Ta sekcja zawiera przykłady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] projekcje i przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="aaaf3-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] projections and transformations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aaaf3-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="aaaf3-104">In This Section</span></span>  
  
|<span data-ttu-id="aaaf3-105">Temat</span><span class="sxs-lookup"><span data-stu-id="aaaf3-105">Topic</span></span>|<span data-ttu-id="aaaf3-106">Opis</span><span class="sxs-lookup"><span data-stu-id="aaaf3-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="aaaf3-107">Porady: Praca z słowniki za pomocą LINQ do XML (C#)</span><span class="sxs-lookup"><span data-stu-id="aaaf3-107">How to: Work with Dictionaries Using LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-work-with-dictionaries-using-linq-to-xml.md)|<span data-ttu-id="aaaf3-108">Pokazuje do przekształcania słowniki do pliku XML oraz sposobu Przekształcanie XML do słownika.</span><span class="sxs-lookup"><span data-stu-id="aaaf3-108">Shows how to transform dictionaries to XML, and how to transform XML into dictionaries.</span></span>|  
|[<span data-ttu-id="aaaf3-109">Porady: Przekształcanie kształtu drzewo XML (C#)</span><span class="sxs-lookup"><span data-stu-id="aaaf3-109">How to: Transform the Shape of an XML Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-transform-the-shape-of-an-xml-tree.md)|<span data-ttu-id="aaaf3-110">Przedstawia sposób przekształcania kształtu dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="aaaf3-110">Shows how to transform the shape of an XML document.</span></span>|  
|[<span data-ttu-id="aaaf3-111">Porady: kontrolowanie typu projekcji (C#)</span><span class="sxs-lookup"><span data-stu-id="aaaf3-111">How to: Control the Type of a Projection (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-control-the-type-of-a-projection.md)|<span data-ttu-id="aaaf3-112">Pokazuje, jak kontrolować typ [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="aaaf3-112">Shows how to control the type of a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="aaaf3-113">Porady: projekt nowy typ (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="aaaf3-113">How to: Project a New Type (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-project-a-new-type-linq-to-xml.md)|<span data-ttu-id="aaaf3-114">Pokazuje, jak do kolekcji typu użytkownika z projektów [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="aaaf3-114">Shows how to project a collection of a user-defined type from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="aaaf3-115">Porady: projekt wykresu obiektów (C#)</span><span class="sxs-lookup"><span data-stu-id="aaaf3-115">How to: Project an Object Graph (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-project-an-object-graph.md)|<span data-ttu-id="aaaf3-116">Pokazuje, jak projektu bardziej złożonych wykres obiektu z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="aaaf3-116">Shows how to project a more complex object graph from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="aaaf3-117">Porady: projekt typu anonimowego (C#)</span><span class="sxs-lookup"><span data-stu-id="aaaf3-117">How to: Project an Anonymous Type (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-project-an-anonymous-type.md)|<span data-ttu-id="aaaf3-118">Pokazuje, jak kolekcji obiektów anonimowego z projektów [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="aaaf3-118">Shows how to project a collection of anonymous objects from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="aaaf3-119">Porady: generowanie pliki tekstowe z pliku XML (C#)</span><span class="sxs-lookup"><span data-stu-id="aaaf3-119">How to: Generate Text Files from XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-generate-text-files-from-xml.md)|<span data-ttu-id="aaaf3-120">Pokazuje, jak do przekształcania pliku XML do pliku tekstowego z systemem innym niż XML.</span><span class="sxs-lookup"><span data-stu-id="aaaf3-120">Shows how to transform an XML file to a non-XML text file.</span></span>|  
|[<span data-ttu-id="aaaf3-121">Porady: generowanie kodu XML z plików CSV (C#)</span><span class="sxs-lookup"><span data-stu-id="aaaf3-121">How to: Generate XML from CSV Files (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-generate-xml-from-csv-files.md)|<span data-ttu-id="aaaf3-122">Przedstawia sposób użycia [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] można przeanalizować pliku CSV i generowanie kodu XML z niego.</span><span class="sxs-lookup"><span data-stu-id="aaaf3-122">Shows how to use [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to parse a CSV file and generate XML from it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aaaf3-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aaaf3-123">See Also</span></span>  
 [<span data-ttu-id="aaaf3-124">Zapytanie drzewa XML (C#)</span><span class="sxs-lookup"><span data-stu-id="aaaf3-124">Querying XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)
