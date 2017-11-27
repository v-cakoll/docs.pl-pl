---
title: "Wykonanie odroczone i obliczanie leniwe w składniku LINQ to XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31998eed-b95e-47fb-a865-9de1f337d1fb
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3a465c4448157505a42db57202298cb18e44a562
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-visual-basic"></a><span data-ttu-id="75b9a-102">Wykonanie odroczone i obliczanie leniwe w składniku LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75b9a-102">Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)</span></span>
<span data-ttu-id="75b9a-103">Operacje zapytań i osi są często stosowane do użycia odroczonego wykonania.</span><span class="sxs-lookup"><span data-stu-id="75b9a-103">Query and axis operations are often implemented to use deferred execution.</span></span> <span data-ttu-id="75b9a-104">W tym temacie opisano wymagania i zalety wykonanie odroczone oraz pewne zagadnienia implementacji.</span><span class="sxs-lookup"><span data-stu-id="75b9a-104">This topic explains the requirements and advantages of deferred execution, and some implementation considerations.</span></span>  
  
## <a name="deferred-execution"></a><span data-ttu-id="75b9a-105">Wykonanie odroczone</span><span class="sxs-lookup"><span data-stu-id="75b9a-105">Deferred Execution</span></span>  
 <span data-ttu-id="75b9a-106">Odroczone wykonywania oznacza, że obliczania wyrażenia jest opóźnione aż do jego *zrealizowane* faktycznie wymagana jest wartość.</span><span class="sxs-lookup"><span data-stu-id="75b9a-106">Deferred execution means that the evaluation of an expression is delayed until its *realized* value is actually required.</span></span> <span data-ttu-id="75b9a-107">Wykonanie odroczone może znacznie poprawić wydajność podczas modyfikowania kolekcji dużej ilości danych, szczególnie w programach, które zawierają ciąg kwerendy łańcuchowych lub manipulacji.</span><span class="sxs-lookup"><span data-stu-id="75b9a-107">Deferred execution can greatly improve performance when you have to manipulate large data collections, especially in programs that contain a series of chained queries or manipulations.</span></span> <span data-ttu-id="75b9a-108">W najlepszym przypadku wykonanie odroczone umożliwia tylko jednego iteracji za pomocą kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="75b9a-108">In the best case, deferred execution enables only a single iteration through the source collection.</span></span>  
  
 <span data-ttu-id="75b9a-109">Technologie LINQ umożliwiają zwiększone użycie odroczonego wykonania w przypadku członków podstawowych <xref:System.Linq?displayProperty=nameWithType> klas i metod rozszerzenia w różnych przestrzeniach nazw LINQ, takich jak <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="75b9a-109">The LINQ technologies make extensive use of deferred execution in both the members of core <xref:System.Linq?displayProperty=nameWithType> classes and in the extension methods in the various LINQ namespaces, such as <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="eager-vs-lazy-evaluation"></a><span data-ttu-id="75b9a-110">Wczesny vs. Obliczanie leniwe</span><span class="sxs-lookup"><span data-stu-id="75b9a-110">Eager vs. Lazy Evaluation</span></span>  
 <span data-ttu-id="75b9a-111">Podczas pisania metodę, która implementuje wykonanie odroczone należy zdecydować, czy należy zaimplementować metodę przy użyciu obliczanie leniwe lub wczesny oceny.</span><span class="sxs-lookup"><span data-stu-id="75b9a-111">When you write a method that implements deferred execution, you also have to decide whether to implement the method using lazy evaluation or eager evaluation.</span></span>  
  
-   <span data-ttu-id="75b9a-112">W *obliczanie leniwe*, pojedynczy element kolekcji źródłowej jest przetwarzany każde wywołanie iteratora.</span><span class="sxs-lookup"><span data-stu-id="75b9a-112">In *lazy evaluation*, a single element of the source collection is processed during each call to the iterator.</span></span> <span data-ttu-id="75b9a-113">To jest typowym sposobem, w którym Iteratory są implementowane.</span><span class="sxs-lookup"><span data-stu-id="75b9a-113">This is the typical way in which iterators are implemented.</span></span>  
  
-   <span data-ttu-id="75b9a-114">W *wczesny oceny*, pierwsze wywołanie w celu iteratora spowoduje całą kolekcję przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="75b9a-114">In *eager evaluation*, the first call to the iterator will result in the entire collection being processed.</span></span> <span data-ttu-id="75b9a-115">Mogą być także wymagane tymczasową kopię kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="75b9a-115">A temporary copy of the source collection might also be required.</span></span> <span data-ttu-id="75b9a-116">Na przykład <xref:System.Linq.Enumerable.OrderBy%2A> metoda ma sortowania całą kolekcję przed zwraca pierwszy element.</span><span class="sxs-lookup"><span data-stu-id="75b9a-116">For example, the <xref:System.Linq.Enumerable.OrderBy%2A> method has to sort the entire collection before it returns the first element.</span></span>  
  
 <span data-ttu-id="75b9a-117">Obliczanie leniwe zazwyczaj daje lepszą wydajność, ponieważ dystrybuuje większe obciążenie przetwarzania równomiernie w całej oceny kolekcji i minimalizuje dane tymczasowe.</span><span class="sxs-lookup"><span data-stu-id="75b9a-117">Lazy evaluation usually yields better performance because it distributes overhead processing evenly throughout the evaluation of the collection and minimizes the use of temporary data.</span></span> <span data-ttu-id="75b9a-118">Oczywiście dla niektórych operacji, nie ma żadnych innych opcji niż aby zmaterializowania pośrednich wyników.</span><span class="sxs-lookup"><span data-stu-id="75b9a-118">Of course, for some operations, there is no other option than to materialize intermediate results.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="75b9a-119">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="75b9a-119">Next Steps</span></span>  
 <span data-ttu-id="75b9a-120">Następnego tematu w tym samouczku przedstawiono odroczonego wykonania:</span><span class="sxs-lookup"><span data-stu-id="75b9a-120">The next topic in this tutorial illustrates deferred execution:</span></span>  
  
-   [<span data-ttu-id="75b9a-121">Wykonanie odroczone — przykład (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75b9a-121">Deferred Execution Example (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="75b9a-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="75b9a-122">See Also</span></span>  
 [<span data-ttu-id="75b9a-123">Samouczek: Odroczonego wykonania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75b9a-123">Tutorial: Deferred Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)  
 [<span data-ttu-id="75b9a-124">Pojęcia i terminologię (funkcjonalności przekształcania) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75b9a-124">Concepts and Terminology (Functional Transformation) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)  
 [<span data-ttu-id="75b9a-125">Operacje agregacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75b9a-125">Aggregation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)
