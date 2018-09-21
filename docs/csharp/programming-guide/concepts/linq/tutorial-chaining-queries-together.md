---
title: 'Samouczek: Tworzenie łańcuchów zapytań razem (C#)'
ms.date: 07/20/2015
ms.assetid: 44f54444-c4c5-4c23-9d19-986b957b8eda
ms.openlocfilehash: cab012a6ae618bd731c26bc1a002c144b84d2169
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46489933"
---
# <a name="tutorial-chaining-queries-together-c"></a><span data-ttu-id="dd543-102">Samouczek: Tworzenie łańcuchów zapytań razem (C#)</span><span class="sxs-lookup"><span data-stu-id="dd543-102">Tutorial: Chaining Queries Together (C#)</span></span>
<span data-ttu-id="dd543-103">W tym samouczku przedstawiono przetwarzania modelu podczas tworzenia łańcucha zapytania ze sobą.</span><span class="sxs-lookup"><span data-stu-id="dd543-103">This tutorial illustrates the processing model when you chain queries together.</span></span> <span data-ttu-id="dd543-104">Łączenie łańcuchowe zapytań jest kluczowym elementem pisania przekształceń funkcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="dd543-104">Chaining queries together is a key part of writing functional transformations.</span></span> <span data-ttu-id="dd543-105">Należy zrozumieć, dokładnie tak jak łańcuchowe zapytań pracy.</span><span class="sxs-lookup"><span data-stu-id="dd543-105">It is important to understand exactly how chained queries work.</span></span>  
  
 <span data-ttu-id="dd543-106">Zapytania, które przetwarzają dokumentów Office Open XML Użyj tej techniki w szerokim zakresie.</span><span class="sxs-lookup"><span data-stu-id="dd543-106">The queries that process Office Open XML documents use this technique extensively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dd543-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="dd543-107">In This Section</span></span>  
  
|<span data-ttu-id="dd543-108">Temat</span><span class="sxs-lookup"><span data-stu-id="dd543-108">Topic</span></span>|<span data-ttu-id="dd543-109">Opis</span><span class="sxs-lookup"><span data-stu-id="dd543-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="dd543-110">Wykonanie odroczone i obliczanie z opóźnieniem w LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="dd543-110">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)|<span data-ttu-id="dd543-111">Opis pojęć dotyczących wykonanie odroczone i obliczanie z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="dd543-111">Describes the concepts of deferred execution and lazy evaluation.</span></span>|  
|[<span data-ttu-id="dd543-112">Przykład wykonania odroczonego (C#)</span><span class="sxs-lookup"><span data-stu-id="dd543-112">Deferred Execution Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-example.md)|<span data-ttu-id="dd543-113">Przykład wykonania odroczonego.</span><span class="sxs-lookup"><span data-stu-id="dd543-113">Provides an example of deferred execution.</span></span>|  
|[<span data-ttu-id="dd543-114">Przykład łączenia łańcuchowego zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="dd543-114">Chaining Queries Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)|<span data-ttu-id="dd543-115">Pokazuje, jak odroczonego wykonania działa, gdy Łączenie łańcuchowe zapytań.</span><span class="sxs-lookup"><span data-stu-id="dd543-115">Shows how deferred execution works when chaining queries together.</span></span>|  
|[<span data-ttu-id="dd543-116">Materializacja pośrednia (C#)</span><span class="sxs-lookup"><span data-stu-id="dd543-116">Intermediate Materialization (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)|<span data-ttu-id="dd543-117">Identyfikuje i przedstawia semantykę materializacja pośrednia.</span><span class="sxs-lookup"><span data-stu-id="dd543-117">Identifies and illustrates the semantics of intermediate materialization.</span></span>|  
|[<span data-ttu-id="dd543-118">Łańcucha standardowych operatorów zapytań razem (C#)</span><span class="sxs-lookup"><span data-stu-id="dd543-118">Chaining Standard Query Operators Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)|<span data-ttu-id="dd543-119">W tym artykule opisano semantykę standardowych operatorów zapytań z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="dd543-119">Describes the lazy semantics of the standard query operators.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dd543-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dd543-120">See Also</span></span>

- [<span data-ttu-id="dd543-121">Czyste Przekształcanie funkcjonalne kodu XML (C#)</span><span class="sxs-lookup"><span data-stu-id="dd543-121">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)
