---
title: "Czysty funkcjonalności transformacji XML (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 97e8e582-eb3d-4756-bbfb-0899eb688ae4
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 32259e0b75d8c098663b589f33e2f36344fb15cc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="pure-functional-transformations-of-xml-c"></a><span data-ttu-id="ff793-102">Czysty funkcjonalności transformacji XML (C#)</span><span class="sxs-lookup"><span data-stu-id="ff793-102">Pure Functional Transformations of XML (C#)</span></span>
<span data-ttu-id="ff793-103">Ta sekcja zawiera samouczek funkcjonalności transformacji XML.</span><span class="sxs-lookup"><span data-stu-id="ff793-103">This section provides a functional transformation tutorial for XML.</span></span> <span data-ttu-id="ff793-104">Dotyczy to również wyjaśnienia o pojęciach i konstrukcji językowych, że rozumiesz musi używać funkcjonalności przekształcenia i przykłady użycia funkcjonalności przekształceń do manipulowania dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="ff793-104">This includes explanations of the main concepts and language constructs that you must understand to use functional transformations, and examples of using functional transformations to manipulate an XML document.</span></span> <span data-ttu-id="ff793-105">W tym samouczku zapewnia LINQ do XML przykłady kodu, jednak wszystkie podstawowe pojęcia mają zastosowanie również do innych technologii LINQ.</span><span class="sxs-lookup"><span data-stu-id="ff793-105">Although this tutorial provides LINQ to XML code examples, all of the underlying concepts also apply to other LINQ technologies.</span></span>  
  
 <span data-ttu-id="ff793-106">[Samouczek: manipulowanie zawartości w dokumencie schemat WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) samouczek zawiera szereg przykładów, każdy opierając się na poprzedni.</span><span class="sxs-lookup"><span data-stu-id="ff793-106">The [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial provides a series of examples, each building on the previous one.</span></span> <span data-ttu-id="ff793-107">Następujące przykłady przedstawiają czysty funkcjonalności transformational podejścia manipulowanie XML.</span><span class="sxs-lookup"><span data-stu-id="ff793-107">These examples demonstrate the pure functional transformational approach to manipulating XML.</span></span>  
  
 <span data-ttu-id="ff793-108">Ten samouczek zakłada praktyczną znajomość języka C#.</span><span class="sxs-lookup"><span data-stu-id="ff793-108">This tutorial assumes a working knowledge of C#.</span></span> <span data-ttu-id="ff793-109">Nie podano szczegółowe semantykę konstrukcji językowych w tym samouczku, ale podano linki dokumentację języka, zależnie od potrzeb.</span><span class="sxs-lookup"><span data-stu-id="ff793-109">Detailed semantics of the language constructs are not provided in this tutorial, but links are provided to the language documentation as appropriate.</span></span>  
  
 <span data-ttu-id="ff793-110">W praktyce koncepcji nauki podstawowego komputera i XML, łącznie z przestrzeni nazw XML, również zakłada, że.</span><span class="sxs-lookup"><span data-stu-id="ff793-110">A working knowledge of basic computer science concepts and XML, including XML namespaces, is also assumed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ff793-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ff793-111">In This Section</span></span>  
  
|<span data-ttu-id="ff793-112">Temat</span><span class="sxs-lookup"><span data-stu-id="ff793-112">Topic</span></span>|<span data-ttu-id="ff793-113">Opis</span><span class="sxs-lookup"><span data-stu-id="ff793-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="ff793-114">Wprowadzenie do przekształcenia funkcjonalności Pure (C#)</span><span class="sxs-lookup"><span data-stu-id="ff793-114">Introduction to Pure Functional Transformations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)|<span data-ttu-id="ff793-115">Zawiera opis przekształcenia funkcjonalności i definiuje istotne terminologii.</span><span class="sxs-lookup"><span data-stu-id="ff793-115">Describes functional transformations and defines the relevant terminology.</span></span>|  
|[<span data-ttu-id="ff793-116">Samouczek: Tworzenie łańcuchów zapytań razem (C#)</span><span class="sxs-lookup"><span data-stu-id="ff793-116">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)|<span data-ttu-id="ff793-117">Opisuje obliczanie leniwe i wykonanie odroczone szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="ff793-117">Describes lazy evaluation and deferred execution in detail.</span></span>|  
|[<span data-ttu-id="ff793-118">Samouczek: Manipulowanie zawartości w dokumencie schemat WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="ff793-118">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)|<span data-ttu-id="ff793-119">Samouczek przedstawiający transformację funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="ff793-119">A tutorial that demonstrates a functional transformation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ff793-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ff793-120">See Also</span></span>  
 [<span data-ttu-id="ff793-121">Zapytanie drzewa XML (C#)</span><span class="sxs-lookup"><span data-stu-id="ff793-121">Querying XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)
