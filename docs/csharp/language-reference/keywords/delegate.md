---
title: "delegate (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- delegate_CSharpKeyword
- delegate
- CS0123
helpviewer_keywords:
- delegate keyword [C#]
- function pointers [C#]
ms.assetid: 0bb8cb6d-2f87-47c7-9d1f-d65c1cd01e9f
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 179e89cea0e683b72e57536d4e4d86b019493aed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="delegate-c-reference"></a><span data-ttu-id="e2ef2-102">delegate (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="e2ef2-102">delegate (C# Reference)</span></span>
<span data-ttu-id="e2ef2-103">Deklaracja typu delegowanego jest podobny do sygnatury metody.</span><span class="sxs-lookup"><span data-stu-id="e2ef2-103">The declaration of a delegate type is similar to a method signature.</span></span> <span data-ttu-id="e2ef2-104">Ma wartość zwracaną i dowolną liczbę parametrów dowolnego typu:</span><span class="sxs-lookup"><span data-stu-id="e2ef2-104">It has a return value and any number of parameters of any type:</span></span>  
  
```  
public delegate void TestDelegate(string message);  
public delegate int TestDelegate(MyType m, long num);  
```  
  
 <span data-ttu-id="e2ef2-105">A `delegate` jest typem referencyjnym, który może służyć Hermetyzowanie nazwane ani metoda anonimowa.</span><span class="sxs-lookup"><span data-stu-id="e2ef2-105">A `delegate` is a reference type that can be used to encapsulate a named or an anonymous method.</span></span> <span data-ttu-id="e2ef2-106">Obiekty delegowane są podobne do wskaźników funkcji w języku C++; jednak delegatów są bezpieczne i bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="e2ef2-106">Delegates are similar to function pointers in C++; however, delegates are type-safe and secure.</span></span> <span data-ttu-id="e2ef2-107">W przypadku aplikacji o delegatów, zobacz [delegatów](../../../csharp/programming-guide/delegates/index.md) i [delegatów](../../../csharp/programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="e2ef2-107">For applications of delegates, see [Delegates](../../../csharp/programming-guide/delegates/index.md) and [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2ef2-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e2ef2-108">Remarks</span></span>  
 <span data-ttu-id="e2ef2-109">Obiekty delegowane stanowią podstawę dla [zdarzenia](../../../csharp/programming-guide/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="e2ef2-109">Delegates are the basis for [Events](../../../csharp/programming-guide/events/index.md).</span></span>  
  
 <span data-ttu-id="e2ef2-110">Delegat można wdrożyć przez skojarzenie za pomocą metody nazwane i anonimowe.</span><span class="sxs-lookup"><span data-stu-id="e2ef2-110">A delegate can be instantiated by associating it either with a named or anonymous method.</span></span> <span data-ttu-id="e2ef2-111">Aby uzyskać więcej informacji, zobacz [metody o nazwie](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) i [metod anonimowych](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="e2ef2-111">For more information, see [Named Methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) and [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>  
  
 <span data-ttu-id="e2ef2-112">Obiekt delegowany musi być utworzone za pomocą wyrażenia metody lub lambda ma niezgodny typ zwracany i parametrów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="e2ef2-112">The delegate must be instantiated with a method or lambda expression that has a compatible return type and input parameters.</span></span> <span data-ttu-id="e2ef2-113">Aby uzyskać więcej informacji na stopień wariancję, jaki jest dozwolony w podpisie metody, zobacz [wariancji w Delegatach](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="e2ef2-113">For more information on the degree of variance that is allowed in the method signature, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span> <span data-ttu-id="e2ef2-114">Do użytku z metod anonimowych delegat i kodu ma zostać skojarzony z nim są zadeklarowane jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="e2ef2-114">For use with anonymous methods, the delegate and the code to be associated with it are declared together.</span></span> <span data-ttu-id="e2ef2-115">W tej sekcji omówiono obu kierunkach, tworzenie wystąpień obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="e2ef2-115">Both ways of instantiating delegates are discussed in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2ef2-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="e2ef2-116">Example</span></span>  
 [!code-csharp[csrefKeywordsTypes#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/delegate_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="e2ef2-117">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="e2ef2-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e2ef2-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e2ef2-118">See Also</span></span>  
 [<span data-ttu-id="e2ef2-119">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="e2ef2-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e2ef2-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e2ef2-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e2ef2-121">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="e2ef2-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="e2ef2-122">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="e2ef2-122">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="e2ef2-123">Obiekty delegowane</span><span class="sxs-lookup"><span data-stu-id="e2ef2-123">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="e2ef2-124">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="e2ef2-124">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="e2ef2-125">Obiekty delegowane z nazwanego vs. Metody anonimowe</span><span class="sxs-lookup"><span data-stu-id="e2ef2-125">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
 [<span data-ttu-id="e2ef2-126">Metody anonimowe</span><span class="sxs-lookup"><span data-stu-id="e2ef2-126">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
