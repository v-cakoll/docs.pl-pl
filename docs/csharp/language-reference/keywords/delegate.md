---
title: delegate (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- delegate_CSharpKeyword
- delegate
- CS0123
helpviewer_keywords:
- delegate keyword [C#]
- function pointers [C#]
ms.assetid: 0bb8cb6d-2f87-47c7-9d1f-d65c1cd01e9f
ms.openlocfilehash: ba1cfdcc56b3d2301a07ffa4af793e7002da21bb
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948426"
---
# <a name="delegate-c-reference"></a><span data-ttu-id="a0d0c-102">delegate (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a0d0c-102">delegate (C# Reference)</span></span>

<span data-ttu-id="a0d0c-103">Deklaracja typu delegowanego jest podobny do sygnatury metody.</span><span class="sxs-lookup"><span data-stu-id="a0d0c-103">The declaration of a delegate type is similar to a method signature.</span></span> <span data-ttu-id="a0d0c-104">Ma wartość zwracaną i dowolną liczbę parametrów dowolnego typu:</span><span class="sxs-lookup"><span data-stu-id="a0d0c-104">It has a return value and any number of parameters of any type:</span></span>

```csharp
public delegate void TestDelegate(string message);
public delegate int TestDelegate(MyType m, long num);
```

<span data-ttu-id="a0d0c-105">A `delegate` jest typem referencyjnym, który może służyć Hermetyzowanie nazwane ani metoda anonimowa.</span><span class="sxs-lookup"><span data-stu-id="a0d0c-105">A `delegate` is a reference type that can be used to encapsulate a named or an anonymous method.</span></span> <span data-ttu-id="a0d0c-106">Obiekty delegowane są podobne do wskaźników funkcji w języku C++; jednak delegatów są bezpieczne i bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="a0d0c-106">Delegates are similar to function pointers in C++; however, delegates are type-safe and secure.</span></span> <span data-ttu-id="a0d0c-107">W przypadku aplikacji o delegatów, zobacz [delegatów](../../../csharp/programming-guide/delegates/index.md) i [delegatów](../../../csharp/programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="a0d0c-107">For applications of delegates, see [Delegates](../../../csharp/programming-guide/delegates/index.md) and [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="a0d0c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a0d0c-108">Remarks</span></span>

<span data-ttu-id="a0d0c-109">Obiekty delegowane stanowią podstawę dla [zdarzenia](../../../csharp/programming-guide/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="a0d0c-109">Delegates are the basis for [Events](../../../csharp/programming-guide/events/index.md).</span></span>

<span data-ttu-id="a0d0c-110">Delegat można wdrożyć przez skojarzenie za pomocą metody nazwane i anonimowe.</span><span class="sxs-lookup"><span data-stu-id="a0d0c-110">A delegate can be instantiated by associating it either with a named or anonymous method.</span></span> <span data-ttu-id="a0d0c-111">Aby uzyskać więcej informacji, zobacz [metody o nazwie](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) i [metod anonimowych](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="a0d0c-111">For more information, see [Named Methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) and [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>

<span data-ttu-id="a0d0c-112">Obiekt delegowany musi być utworzone za pomocą wyrażenia metody lub lambda ma niezgodny typ zwracany i parametrów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="a0d0c-112">The delegate must be instantiated with a method or lambda expression that has a compatible return type and input parameters.</span></span> <span data-ttu-id="a0d0c-113">Aby uzyskać więcej informacji na stopień wariancję, jaki jest dozwolony w podpisie metody, zobacz [wariancji w Delegatach](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="a0d0c-113">For more information on the degree of variance that is allowed in the method signature, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span> <span data-ttu-id="a0d0c-114">Do użytku z metod anonimowych delegat i kodu ma zostać skojarzony z nim są zadeklarowane jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="a0d0c-114">For use with anonymous methods, the delegate and the code to be associated with it are declared together.</span></span> <span data-ttu-id="a0d0c-115">W tej sekcji omówiono obu kierunkach, tworzenie wystąpień obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="a0d0c-115">Both ways of instantiating delegates are discussed in this section.</span></span>

## <a name="example"></a><span data-ttu-id="a0d0c-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0d0c-116">Example</span></span>

[!code-csharp[csrefKeywordsTypes#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="a0d0c-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a0d0c-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a0d0c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0d0c-118">See also</span></span>

[<span data-ttu-id="a0d0c-119">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a0d0c-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
[<span data-ttu-id="a0d0c-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a0d0c-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
[<span data-ttu-id="a0d0c-121">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="a0d0c-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
[<span data-ttu-id="a0d0c-122">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="a0d0c-122">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
[<span data-ttu-id="a0d0c-123">Delegaci</span><span class="sxs-lookup"><span data-stu-id="a0d0c-123">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
[<span data-ttu-id="a0d0c-124">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a0d0c-124">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
[<span data-ttu-id="a0d0c-125">Delegaci z metodami nazwanymi lub anonimowymi</span><span class="sxs-lookup"><span data-stu-id="a0d0c-125">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
[<span data-ttu-id="a0d0c-126">Metody anonimowe</span><span class="sxs-lookup"><span data-stu-id="a0d0c-126">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
