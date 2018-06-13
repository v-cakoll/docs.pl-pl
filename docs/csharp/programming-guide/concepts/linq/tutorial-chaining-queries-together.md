---
title: 'Samouczek: Tworzenie łańcuchów zapytań razem (C#)'
ms.date: 07/20/2015
ms.assetid: 44f54444-c4c5-4c23-9d19-986b957b8eda
ms.openlocfilehash: 8411d8577c192e2aa1a43bea47644fe6bdc09e88
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323713"
---
# <a name="tutorial-chaining-queries-together-c"></a><span data-ttu-id="d6cbf-102">Samouczek: Tworzenie łańcuchów zapytań razem (C#)</span><span class="sxs-lookup"><span data-stu-id="d6cbf-102">Tutorial: Chaining Queries Together (C#)</span></span>
<span data-ttu-id="d6cbf-103">W tym samouczku przedstawiono przetwarzania modelu, gdy łańcuch zapytania.</span><span class="sxs-lookup"><span data-stu-id="d6cbf-103">This tutorial illustrates the processing model when you chain queries together.</span></span> <span data-ttu-id="d6cbf-104">Łańcucha zapytań razem jest kluczowym elementem zapisywania funkcjonalności przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="d6cbf-104">Chaining queries together is a key part of writing functional transformations.</span></span> <span data-ttu-id="d6cbf-105">Należy zrozumieć, dokładnie tak jak łańcuchowa pracy zapytania.</span><span class="sxs-lookup"><span data-stu-id="d6cbf-105">It is important to understand exactly how chained queries work.</span></span>  
  
 <span data-ttu-id="d6cbf-106">Zapytania, które przetwarzają dokumenty pakietu Office Open XML często użyć tej metody.</span><span class="sxs-lookup"><span data-stu-id="d6cbf-106">The queries that process Office Open XML documents use this technique extensively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d6cbf-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d6cbf-107">In This Section</span></span>  
  
|<span data-ttu-id="d6cbf-108">Temat</span><span class="sxs-lookup"><span data-stu-id="d6cbf-108">Topic</span></span>|<span data-ttu-id="d6cbf-109">Opis</span><span class="sxs-lookup"><span data-stu-id="d6cbf-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d6cbf-110">Wykonanie odroczone i obliczanie leniwe w składniku LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d6cbf-110">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)|<span data-ttu-id="d6cbf-111">Opis pojęć dotyczących odroczonego wykonania i obliczanie leniwe.</span><span class="sxs-lookup"><span data-stu-id="d6cbf-111">Describes the concepts of deferred execution and lazy evaluation.</span></span>|  
|[<span data-ttu-id="d6cbf-112">Wykonanie odroczone przykład (C#)</span><span class="sxs-lookup"><span data-stu-id="d6cbf-112">Deferred Execution Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-example.md)|<span data-ttu-id="d6cbf-113">Przykład odroczonego wykonania.</span><span class="sxs-lookup"><span data-stu-id="d6cbf-113">Provides an example of deferred execution.</span></span>|  
|[<span data-ttu-id="d6cbf-114">Tworzenie łańcuchów przykład kwerendy (C#)</span><span class="sxs-lookup"><span data-stu-id="d6cbf-114">Chaining Queries Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)|<span data-ttu-id="d6cbf-115">Pokazuje sposób odroczonego wykonania działa, gdy łańcucha zapytania ze sobą.</span><span class="sxs-lookup"><span data-stu-id="d6cbf-115">Shows how deferred execution works when chaining queries together.</span></span>|  
|[<span data-ttu-id="d6cbf-116">Pośredni Materialization (C#)</span><span class="sxs-lookup"><span data-stu-id="d6cbf-116">Intermediate Materialization (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)|<span data-ttu-id="d6cbf-117">Identyfikuje i przedstawia semantykę materialization pośrednich.</span><span class="sxs-lookup"><span data-stu-id="d6cbf-117">Identifies and illustrates the semantics of intermediate materialization.</span></span>|  
|[<span data-ttu-id="d6cbf-118">CBC standardowych operatorów zapytań razem (C#)</span><span class="sxs-lookup"><span data-stu-id="d6cbf-118">Chaining Standard Query Operators Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)|<span data-ttu-id="d6cbf-119">W tym artykule opisano opóźnieniem semantyki standardowych operatorów zapytań.</span><span class="sxs-lookup"><span data-stu-id="d6cbf-119">Describes the lazy semantics of the standard query operators.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d6cbf-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d6cbf-120">See Also</span></span>  
 [<span data-ttu-id="d6cbf-121">Czysty funkcjonalności transformacji XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d6cbf-121">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)
