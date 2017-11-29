---
title: "Czysty funkcjonalności transformacji XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e19b74a-7773-4b58-b110-953ffd364c55
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 01ad228d91037de1585d1e66292fddb80c785ada
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="pure-functional-transformations-of-xml-visual-basic"></a><span data-ttu-id="eea7e-102">Czysty funkcjonalności transformacji XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eea7e-102">Pure Functional Transformations of XML (Visual Basic)</span></span>
<span data-ttu-id="eea7e-103">Ta sekcja zawiera samouczek funkcjonalności transformacji XML.</span><span class="sxs-lookup"><span data-stu-id="eea7e-103">This section provides a functional transformation tutorial for XML.</span></span> <span data-ttu-id="eea7e-104">Dotyczy to również wyjaśnienia o pojęciach i konstrukcji językowych, że rozumiesz musi używać funkcjonalności przekształcenia i przykłady użycia funkcjonalności przekształceń do manipulowania dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="eea7e-104">This includes explanations of the main concepts and language constructs that you must understand to use functional transformations, and examples of using functional transformations to manipulate an XML document.</span></span> <span data-ttu-id="eea7e-105">W tym samouczku zapewnia LINQ do XML przykłady kodu, jednak wszystkie podstawowe pojęcia mają zastosowanie również do innych technologii LINQ.</span><span class="sxs-lookup"><span data-stu-id="eea7e-105">Although this tutorial provides LINQ to XML code examples, all of the underlying concepts also apply to other LINQ technologies.</span></span>  
  
 <span data-ttu-id="eea7e-106">[Samouczek: manipulowanie zawartości w dokumencie schemat WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) samouczek zawiera szereg przykładów, każdy opierając się na poprzedni.</span><span class="sxs-lookup"><span data-stu-id="eea7e-106">The [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial provides a series of examples, each building on the previous one.</span></span> <span data-ttu-id="eea7e-107">Następujące przykłady przedstawiają czysty funkcjonalności transformational podejścia manipulowanie XML.</span><span class="sxs-lookup"><span data-stu-id="eea7e-107">These examples demonstrate the pure functional transformational approach to manipulating XML.</span></span>  
  
 <span data-ttu-id="eea7e-108">Ten samouczek zakłada praktyczną znajomość języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="eea7e-108">This tutorial assumes a working knowledge of Visual Basic.</span></span> <span data-ttu-id="eea7e-109">Nie podano szczegółowe semantykę konstrukcji językowych w tym samouczku, ale podano linki dokumentację języka, zależnie od potrzeb.</span><span class="sxs-lookup"><span data-stu-id="eea7e-109">Detailed semantics of the language constructs are not provided in this tutorial, but links are provided to the language documentation as appropriate.</span></span>  
  
 <span data-ttu-id="eea7e-110">W praktyce koncepcji nauki podstawowego komputera i XML, łącznie z przestrzeni nazw XML, również zakłada, że.</span><span class="sxs-lookup"><span data-stu-id="eea7e-110">A working knowledge of basic computer science concepts and XML, including XML namespaces, is also assumed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eea7e-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="eea7e-111">In This Section</span></span>  
  
|<span data-ttu-id="eea7e-112">Temat</span><span class="sxs-lookup"><span data-stu-id="eea7e-112">Topic</span></span>|<span data-ttu-id="eea7e-113">Opis</span><span class="sxs-lookup"><span data-stu-id="eea7e-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="eea7e-114">Wprowadzenie do przekształcenia funkcjonalności czysty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eea7e-114">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)|<span data-ttu-id="eea7e-115">Zawiera opis przekształcenia funkcjonalności i definiuje istotne terminologii.</span><span class="sxs-lookup"><span data-stu-id="eea7e-115">Describes functional transformations and defines the relevant terminology.</span></span>|  
|[<span data-ttu-id="eea7e-116">Samouczek: Odroczonego wykonania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eea7e-116">Tutorial: Deferred Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)|<span data-ttu-id="eea7e-117">Opisuje obliczanie leniwe i wykonanie odroczone szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="eea7e-117">Describes lazy evaluation and deferred execution in detail.</span></span>|  
|[<span data-ttu-id="eea7e-118">Samouczek: Manipulowanie zawartości w dokumencie schemat WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eea7e-118">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)|<span data-ttu-id="eea7e-119">Samouczek przedstawiający transformację funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="eea7e-119">A tutorial that demonstrates a functional transformation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eea7e-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eea7e-120">See Also</span></span>  
 [<span data-ttu-id="eea7e-121">Wykonywanie zapytania drzewa XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eea7e-121">Querying XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)
