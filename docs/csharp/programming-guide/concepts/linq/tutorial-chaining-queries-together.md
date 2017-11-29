---
title: "Samouczek: Tworzenie łańcuchów zapytań razem (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 44f54444-c4c5-4c23-9d19-986b957b8eda
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 08196f4780e566cc05e36b6cfe78caad3e9c96a1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="tutorial-chaining-queries-together-c"></a><span data-ttu-id="2ff3b-102">Samouczek: Tworzenie łańcuchów zapytań razem (C#)</span><span class="sxs-lookup"><span data-stu-id="2ff3b-102">Tutorial: Chaining Queries Together (C#)</span></span>
<span data-ttu-id="2ff3b-103">W tym samouczku przedstawiono przetwarzania modelu, gdy łańcuch zapytania.</span><span class="sxs-lookup"><span data-stu-id="2ff3b-103">This tutorial illustrates the processing model when you chain queries together.</span></span> <span data-ttu-id="2ff3b-104">Łańcucha zapytań razem jest kluczowym elementem zapisywania funkcjonalności przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="2ff3b-104">Chaining queries together is a key part of writing functional transformations.</span></span> <span data-ttu-id="2ff3b-105">Należy zrozumieć, dokładnie tak jak łańcuchowa pracy zapytania.</span><span class="sxs-lookup"><span data-stu-id="2ff3b-105">It is important to understand exactly how chained queries work.</span></span>  
  
 <span data-ttu-id="2ff3b-106">Zapytania, które przetwarzają dokumenty pakietu Office Open XML często użyć tej metody.</span><span class="sxs-lookup"><span data-stu-id="2ff3b-106">The queries that process Office Open XML documents use this technique extensively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2ff3b-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="2ff3b-107">In This Section</span></span>  
  
|<span data-ttu-id="2ff3b-108">Temat</span><span class="sxs-lookup"><span data-stu-id="2ff3b-108">Topic</span></span>|<span data-ttu-id="2ff3b-109">Opis</span><span class="sxs-lookup"><span data-stu-id="2ff3b-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="2ff3b-110">Wykonanie odroczone i obliczanie leniwe w składniku LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="2ff3b-110">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)|<span data-ttu-id="2ff3b-111">Opis pojęć dotyczących odroczonego wykonania i obliczanie leniwe.</span><span class="sxs-lookup"><span data-stu-id="2ff3b-111">Describes the concepts of deferred execution and lazy evaluation.</span></span>|  
|[<span data-ttu-id="2ff3b-112">Wykonanie odroczone przykład (C#)</span><span class="sxs-lookup"><span data-stu-id="2ff3b-112">Deferred Execution Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-example.md)|<span data-ttu-id="2ff3b-113">Przykład odroczonego wykonania.</span><span class="sxs-lookup"><span data-stu-id="2ff3b-113">Provides an example of deferred execution.</span></span>|  
|[<span data-ttu-id="2ff3b-114">Tworzenie łańcuchów przykład kwerendy (C#)</span><span class="sxs-lookup"><span data-stu-id="2ff3b-114">Chaining Queries Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)|<span data-ttu-id="2ff3b-115">Pokazuje sposób odroczonego wykonania działa, gdy łańcucha zapytania ze sobą.</span><span class="sxs-lookup"><span data-stu-id="2ff3b-115">Shows how deferred execution works when chaining queries together.</span></span>|  
|[<span data-ttu-id="2ff3b-116">Pośredni Materialization (C#)</span><span class="sxs-lookup"><span data-stu-id="2ff3b-116">Intermediate Materialization (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)|<span data-ttu-id="2ff3b-117">Identyfikuje i przedstawia semantykę materialization pośrednich.</span><span class="sxs-lookup"><span data-stu-id="2ff3b-117">Identifies and illustrates the semantics of intermediate materialization.</span></span>|  
|[<span data-ttu-id="2ff3b-118">CBC standardowych operatorów zapytań razem (C#)</span><span class="sxs-lookup"><span data-stu-id="2ff3b-118">Chaining Standard Query Operators Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)|<span data-ttu-id="2ff3b-119">W tym artykule opisano opóźnieniem semantyki standardowych operatorów zapytań.</span><span class="sxs-lookup"><span data-stu-id="2ff3b-119">Describes the lazy semantics of the standard query operators.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2ff3b-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ff3b-120">See Also</span></span>  
 [<span data-ttu-id="2ff3b-121">Czysty funkcjonalności transformacji XML (C#)</span><span class="sxs-lookup"><span data-stu-id="2ff3b-121">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)
