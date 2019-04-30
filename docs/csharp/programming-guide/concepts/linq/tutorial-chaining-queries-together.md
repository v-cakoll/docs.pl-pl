---
title: 'Samouczek: Łączenie łańcuchowe zapytań (C#)'
ms.date: 07/20/2015
ms.assetid: 44f54444-c4c5-4c23-9d19-986b957b8eda
ms.openlocfilehash: 3beed32aa276f218a80267748e74707941957e53
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61711996"
---
# <a name="tutorial-chaining-queries-together-c"></a><span data-ttu-id="bdac3-102">Samouczek: Łączenie łańcuchowe zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="bdac3-102">Tutorial: Chaining Queries Together (C#)</span></span>
<span data-ttu-id="bdac3-103">W tym samouczku przedstawiono przetwarzania modelu podczas tworzenia łańcucha zapytania ze sobą.</span><span class="sxs-lookup"><span data-stu-id="bdac3-103">This tutorial illustrates the processing model when you chain queries together.</span></span> <span data-ttu-id="bdac3-104">Łączenie łańcuchowe zapytań jest kluczowym elementem pisania przekształceń funkcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="bdac3-104">Chaining queries together is a key part of writing functional transformations.</span></span> <span data-ttu-id="bdac3-105">Należy zrozumieć, dokładnie tak jak łańcuchowe zapytań pracy.</span><span class="sxs-lookup"><span data-stu-id="bdac3-105">It is important to understand exactly how chained queries work.</span></span>  
  
 <span data-ttu-id="bdac3-106">Zapytania, które przetwarzają dokumentów Office Open XML Użyj tej techniki w szerokim zakresie.</span><span class="sxs-lookup"><span data-stu-id="bdac3-106">The queries that process Office Open XML documents use this technique extensively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bdac3-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="bdac3-107">In This Section</span></span>  
  
|<span data-ttu-id="bdac3-108">Temat</span><span class="sxs-lookup"><span data-stu-id="bdac3-108">Topic</span></span>|<span data-ttu-id="bdac3-109">Opis</span><span class="sxs-lookup"><span data-stu-id="bdac3-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="bdac3-110">Wykonanie odroczone i obliczanie z opóźnieniem w LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="bdac3-110">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)|<span data-ttu-id="bdac3-111">Opis pojęć dotyczących wykonanie odroczone i obliczanie z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="bdac3-111">Describes the concepts of deferred execution and lazy evaluation.</span></span>|  
|[<span data-ttu-id="bdac3-112">Przykład wykonania odroczonego (C#)</span><span class="sxs-lookup"><span data-stu-id="bdac3-112">Deferred Execution Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-example.md)|<span data-ttu-id="bdac3-113">Przykład wykonania odroczonego.</span><span class="sxs-lookup"><span data-stu-id="bdac3-113">Provides an example of deferred execution.</span></span>|  
|[<span data-ttu-id="bdac3-114">Przykład łączenia łańcuchowego zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="bdac3-114">Chaining Queries Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)|<span data-ttu-id="bdac3-115">Pokazuje, jak odroczonego wykonania działa, gdy Łączenie łańcuchowe zapytań.</span><span class="sxs-lookup"><span data-stu-id="bdac3-115">Shows how deferred execution works when chaining queries together.</span></span>|  
|[<span data-ttu-id="bdac3-116">Materializacja pośrednia (C#)</span><span class="sxs-lookup"><span data-stu-id="bdac3-116">Intermediate Materialization (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)|<span data-ttu-id="bdac3-117">Identyfikuje i przedstawia semantykę materializacja pośrednia.</span><span class="sxs-lookup"><span data-stu-id="bdac3-117">Identifies and illustrates the semantics of intermediate materialization.</span></span>|  
|[<span data-ttu-id="bdac3-118">Łańcucha standardowych operatorów zapytań razem (C#)</span><span class="sxs-lookup"><span data-stu-id="bdac3-118">Chaining Standard Query Operators Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)|<span data-ttu-id="bdac3-119">W tym artykule opisano semantykę standardowych operatorów zapytań z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="bdac3-119">Describes the lazy semantics of the standard query operators.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bdac3-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bdac3-120">See also</span></span>

- [<span data-ttu-id="bdac3-121">Czyste Przekształcanie funkcjonalne kodu XML (C#)</span><span class="sxs-lookup"><span data-stu-id="bdac3-121">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)
