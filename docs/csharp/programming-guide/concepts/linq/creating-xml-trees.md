---
title: Tworzenie drzewa XML (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: bccc3e0a-c08c-468e-9d30-e075670fdace
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 23b19593774b5a010b453e3fe755e21386afd015
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="creating-xml-trees-c"></a><span data-ttu-id="4792b-102">Tworzenie drzewa XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4792b-102">Creating XML Trees (C#)</span></span>
<span data-ttu-id="4792b-103">Jednym z najbardziej typowych zadań XML konstruuje drzewo XML.</span><span class="sxs-lookup"><span data-stu-id="4792b-103">One of the most common XML tasks is constructing an XML tree.</span></span> <span data-ttu-id="4792b-104">W tej sekcji opisano kilka sposobów, aby je utworzyć.</span><span class="sxs-lookup"><span data-stu-id="4792b-104">This section describes several ways to create them.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4792b-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="4792b-105">In This Section</span></span>  
  
|<span data-ttu-id="4792b-106">Temat</span><span class="sxs-lookup"><span data-stu-id="4792b-106">Topic</span></span>|<span data-ttu-id="4792b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4792b-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="4792b-108">Konstrukcja funkcjonalności (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4792b-108">Functional Construction (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md)|<span data-ttu-id="4792b-109">Zawiera omówienie konstrukcji funkcjonalności w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4792b-109">Provides an overview of functional construction in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="4792b-110">Konstrukcja funkcjonalności umożliwia utworzenie całości lub części drzewa XML w jednej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4792b-110">Functional construction enables you to create all or part of your XML tree in a single statement.</span></span> <span data-ttu-id="4792b-111">Również w tym temacie pokazano, jak osadzić zapytania podczas konstruowania drzewo XML.</span><span class="sxs-lookup"><span data-stu-id="4792b-111">This topic also shows how to embed queries when constructing an XML tree.</span></span>|  
|[<span data-ttu-id="4792b-112">Tworzenie XML drzewa w języku C# (LINQ do XML)</span><span class="sxs-lookup"><span data-stu-id="4792b-112">Creating XML Trees in C# (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md)|<span data-ttu-id="4792b-113">Przedstawia sposób tworzenia drzewa w języku C#.</span><span class="sxs-lookup"><span data-stu-id="4792b-113">Shows how to create trees in C#.</span></span>|  
|[<span data-ttu-id="4792b-114">Vs w klonowania. Dołączanie (C#)</span><span class="sxs-lookup"><span data-stu-id="4792b-114">Cloning vs. Attaching (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/cloning-vs-attaching.md)|<span data-ttu-id="4792b-115">Pokazano różnicę między dodawania węzłów z istniejącego drzewa XML (węzły są klonowane i następnie dodany) i węzły z elementu nadrzędnego (są one po prostu dołączone).</span><span class="sxs-lookup"><span data-stu-id="4792b-115">Demonstrates the difference between adding nodes from an existing XML tree (nodes are cloned and then added) and adding nodes with no parent (they are simply attached).</span></span>|  
|[<span data-ttu-id="4792b-116">Analiza kodu XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4792b-116">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)|<span data-ttu-id="4792b-117">Pokazano, jak dokonać analizy pliku XML z różnych źródeł.</span><span class="sxs-lookup"><span data-stu-id="4792b-117">Shows how to parse XML from a variety of sources.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="4792b-118">stanowi warstwę nad <xref:System.Xml.XmlReader>, które są wykorzystywane do analizy kodu XML.</span><span class="sxs-lookup"><span data-stu-id="4792b-118"> is layered on top of <xref:System.Xml.XmlReader>, which is used to parse the XML.</span></span>|  
|[<span data-ttu-id="4792b-119">Porady: wypełnianie drzewo XML z XmlWriter (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4792b-119">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml.md)|<span data-ttu-id="4792b-120">Pokazuje, jak można wypełnić drzewo XML przy użyciu <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="4792b-120">Shows how to populate an XML tree by using an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="4792b-121">Porady: Sprawdzanie poprawności za pomocą schematu XSD (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4792b-121">How to: Validate Using XSD (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md)|<span data-ttu-id="4792b-122">Pokazuje, jak można sprawdzić poprawności drzewa XML za pomocą schematu XSD.</span><span class="sxs-lookup"><span data-stu-id="4792b-122">Shows how to validate an XML tree using XSD.</span></span>|  
|[<span data-ttu-id="4792b-123">Nieprawidłowa zawartość klasy XElement i obiektów klasy XDocument</span><span class="sxs-lookup"><span data-stu-id="4792b-123">Valid Content of XElement and XDocument Objects</span></span>](../../../../csharp/programming-guide/concepts/linq/valid-content-of-xelement-and-xdocument-objects3.md)|<span data-ttu-id="4792b-124">W tym artykule opisano nieprawidłowe argumenty, które mogą zostać przekazane do konstruktorów i metody, które są używane do dodawania zawartości do elementów i dokumentów.</span><span class="sxs-lookup"><span data-stu-id="4792b-124">Describes the valid arguments that can be passed to the constructors and methods that are used to add content to elements and documents.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4792b-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4792b-125">See Also</span></span>  
 [<span data-ttu-id="4792b-126">Przewodnik programowania w języku (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4792b-126">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
