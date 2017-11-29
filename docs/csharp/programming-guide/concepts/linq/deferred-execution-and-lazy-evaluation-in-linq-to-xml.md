---
title: "Wykonanie odroczone i obliczanie leniwe w składniku LINQ to XML (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 8683d1b4-b7ec-407b-be12-906ebe958a09
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 847d8f830c26f54521664accc4bf569f822f255a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-c"></a><span data-ttu-id="1441f-102">Wykonanie odroczone i obliczanie leniwe w składniku LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="1441f-102">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>
<span data-ttu-id="1441f-103">Operacje zapytań i osi są często stosowane do użycia odroczonego wykonania.</span><span class="sxs-lookup"><span data-stu-id="1441f-103">Query and axis operations are often implemented to use deferred execution.</span></span> <span data-ttu-id="1441f-104">W tym temacie opisano wymagania i zalety wykonanie odroczone oraz pewne zagadnienia implementacji.</span><span class="sxs-lookup"><span data-stu-id="1441f-104">This topic explains the requirements and advantages of deferred execution, and some implementation considerations.</span></span>  
  
## <a name="deferred-execution"></a><span data-ttu-id="1441f-105">Wykonanie odroczone</span><span class="sxs-lookup"><span data-stu-id="1441f-105">Deferred Execution</span></span>  
 <span data-ttu-id="1441f-106">Odroczone wykonywania oznacza, że obliczania wyrażenia jest opóźnione aż do jego *zrealizowane* faktycznie wymagana jest wartość.</span><span class="sxs-lookup"><span data-stu-id="1441f-106">Deferred execution means that the evaluation of an expression is delayed until its *realized* value is actually required.</span></span> <span data-ttu-id="1441f-107">Wykonanie odroczone może znacznie poprawić wydajność podczas modyfikowania kolekcji dużej ilości danych, szczególnie w programach, które zawierają ciąg kwerendy łańcuchowych lub manipulacji.</span><span class="sxs-lookup"><span data-stu-id="1441f-107">Deferred execution can greatly improve performance when you have to manipulate large data collections, especially in programs that contain a series of chained queries or manipulations.</span></span> <span data-ttu-id="1441f-108">W najlepszym przypadku wykonanie odroczone umożliwia tylko jednego iteracji za pomocą kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="1441f-108">In the best case, deferred execution enables only a single iteration through the source collection.</span></span>  
  
 <span data-ttu-id="1441f-109">Technologie LINQ umożliwiają zwiększone użycie odroczonego wykonania w przypadku członków podstawowych <xref:System.Linq?displayProperty=nameWithType> klas i metod rozszerzenia w różnych przestrzeniach nazw LINQ, takich jak <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1441f-109">The LINQ technologies make extensive use of deferred execution in both the members of core <xref:System.Linq?displayProperty=nameWithType> classes and in the extension methods in the various LINQ namespaces, such as <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="1441f-110">Wykonanie odroczone jest obsługiwane bezpośrednio w języku C#, przez [yield](../../../../csharp/language-reference/keywords/yield.md) — słowo kluczowe (w postaci `yield-return` instrukcji) używanego w ramach blokiem iteratora.</span><span class="sxs-lookup"><span data-stu-id="1441f-110">Deferred execution is supported directly in the C# language by the [yield](../../../../csharp/language-reference/keywords/yield.md) keyword (in the form of the `yield-return` statement) when used within an iterator block.</span></span> <span data-ttu-id="1441f-111">Takie iteratora musi zwracać kolekcję typu <xref:System.Collections.IEnumerator> lub <xref:System.Collections.Generic.IEnumerator%601> (lub typu pochodnego).</span><span class="sxs-lookup"><span data-stu-id="1441f-111">Such an iterator must return a collection of type <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> (or a derived type).</span></span>  
  
## <a name="eager-vs-lazy-evaluation"></a><span data-ttu-id="1441f-112">Wczesny vs. Obliczanie leniwe</span><span class="sxs-lookup"><span data-stu-id="1441f-112">Eager vs. Lazy Evaluation</span></span>  
 <span data-ttu-id="1441f-113">Podczas pisania metodę, która implementuje wykonanie odroczone należy zdecydować, czy należy zaimplementować metodę przy użyciu obliczanie leniwe lub wczesny oceny.</span><span class="sxs-lookup"><span data-stu-id="1441f-113">When you write a method that implements deferred execution, you also have to decide whether to implement the method using lazy evaluation or eager evaluation.</span></span>  
  
-   <span data-ttu-id="1441f-114">W *obliczanie leniwe*, pojedynczy element kolekcji źródłowej jest przetwarzany każde wywołanie iteratora.</span><span class="sxs-lookup"><span data-stu-id="1441f-114">In *lazy evaluation*, a single element of the source collection is processed during each call to the iterator.</span></span> <span data-ttu-id="1441f-115">To jest typowym sposobem, w którym Iteratory są implementowane.</span><span class="sxs-lookup"><span data-stu-id="1441f-115">This is the typical way in which iterators are implemented.</span></span>  
  
-   <span data-ttu-id="1441f-116">W *wczesny oceny*, pierwsze wywołanie w celu iteratora spowoduje całą kolekcję przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="1441f-116">In *eager evaluation*, the first call to the iterator will result in the entire collection being processed.</span></span> <span data-ttu-id="1441f-117">Mogą być także wymagane tymczasową kopię kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="1441f-117">A temporary copy of the source collection might also be required.</span></span> <span data-ttu-id="1441f-118">Na przykład <xref:System.Linq.Enumerable.OrderBy%2A> metoda ma sortowania całą kolekcję przed zwraca pierwszy element.</span><span class="sxs-lookup"><span data-stu-id="1441f-118">For example, the <xref:System.Linq.Enumerable.OrderBy%2A> method has to sort the entire collection before it returns the first element.</span></span>  
  
 <span data-ttu-id="1441f-119">Obliczanie leniwe zazwyczaj daje lepszą wydajność, ponieważ dystrybuuje większe obciążenie przetwarzania równomiernie w całej oceny kolekcji i minimalizuje dane tymczasowe.</span><span class="sxs-lookup"><span data-stu-id="1441f-119">Lazy evaluation usually yields better performance because it distributes overhead processing evenly throughout the evaluation of the collection and minimizes the use of temporary data.</span></span> <span data-ttu-id="1441f-120">Oczywiście dla niektórych operacji, nie ma żadnych innych opcji niż aby zmaterializowania pośrednich wyników.</span><span class="sxs-lookup"><span data-stu-id="1441f-120">Of course, for some operations, there is no other option than to materialize intermediate results.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="1441f-121">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="1441f-121">Next Steps</span></span>  
 <span data-ttu-id="1441f-122">Następnego tematu w tym samouczku przedstawiono odroczonego wykonania:</span><span class="sxs-lookup"><span data-stu-id="1441f-122">The next topic in this tutorial illustrates deferred execution:</span></span>  
  
-   [<span data-ttu-id="1441f-123">Wykonanie odroczone przykład (C#)</span><span class="sxs-lookup"><span data-stu-id="1441f-123">Deferred Execution Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="1441f-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1441f-124">See Also</span></span>  
 [<span data-ttu-id="1441f-125">Samouczek: Tworzenie łańcuchów zapytań razem (C#)</span><span class="sxs-lookup"><span data-stu-id="1441f-125">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)  
 [<span data-ttu-id="1441f-126">Pojęcia i terminologię (funkcjonalności przekształcania) (C#)</span><span class="sxs-lookup"><span data-stu-id="1441f-126">Concepts and Terminology (Functional Transformation) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)  
 [<span data-ttu-id="1441f-127">Operacje agregacji (C#)</span><span class="sxs-lookup"><span data-stu-id="1441f-127">Aggregation Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/aggregation-operations.md)  
 [<span data-ttu-id="1441f-128">YIELD</span><span class="sxs-lookup"><span data-stu-id="1441f-128">yield</span></span>](../../../../csharp/language-reference/keywords/yield.md)
