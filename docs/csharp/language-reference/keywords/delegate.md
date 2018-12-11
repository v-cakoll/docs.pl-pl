---
title: Delegowanie — C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- delegate_CSharpKeyword
- delegate
- CS0123
helpviewer_keywords:
- delegate keyword [C#]
- function pointers [C#]
ms.assetid: 0bb8cb6d-2f87-47c7-9d1f-d65c1cd01e9f
ms.openlocfilehash: cbc81f8a9db3b2f637f9c6faabc8b533d2965b0d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241947"
---
# <a name="delegate-c-reference"></a><span data-ttu-id="425f0-102">delegate (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="425f0-102">delegate (C# Reference)</span></span>

<span data-ttu-id="425f0-103">Deklaracja typu delegata jest podobny do podpisu metody.</span><span class="sxs-lookup"><span data-stu-id="425f0-103">The declaration of a delegate type is similar to a method signature.</span></span> <span data-ttu-id="425f0-104">Ma wartość zwracaną i dowolną liczbę parametrów, dowolnego typu:</span><span class="sxs-lookup"><span data-stu-id="425f0-104">It has a return value and any number of parameters of any type:</span></span>

```csharp
public delegate void TestDelegate(string message);
public delegate int TestDelegate(MyType m, long num);
```

<span data-ttu-id="425f0-105">Element `delegate` jest typem referencyjnym, który może służyć do hermetyzacji nazwane lub metodę anonimową.</span><span class="sxs-lookup"><span data-stu-id="425f0-105">A `delegate` is a reference type that can be used to encapsulate a named or an anonymous method.</span></span> <span data-ttu-id="425f0-106">Delegaty są podobne do wskaźników funkcji języka C++; Jednak obiekty delegowane są bezpieczne i bezpieczny typowo.</span><span class="sxs-lookup"><span data-stu-id="425f0-106">Delegates are similar to function pointers in C++; however, delegates are type-safe and secure.</span></span> <span data-ttu-id="425f0-107">W przypadku aplikacji delegatów, zobacz [delegatów](../../../csharp/programming-guide/delegates/index.md) i [delegatów ogólnych](../../../csharp/programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="425f0-107">For applications of delegates, see [Delegates](../../../csharp/programming-guide/delegates/index.md) and [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="425f0-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="425f0-108">Remarks</span></span>

<span data-ttu-id="425f0-109">Obiekty delegowane są podstawą [zdarzenia](../../../csharp/programming-guide/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="425f0-109">Delegates are the basis for [Events](../../../csharp/programming-guide/events/index.md).</span></span>

<span data-ttu-id="425f0-110">Pełnomocnik może być utworzone przez skojarzenie przy użyciu metody nazwane i anonimowe.</span><span class="sxs-lookup"><span data-stu-id="425f0-110">A delegate can be instantiated by associating it either with a named or anonymous method.</span></span> <span data-ttu-id="425f0-111">Aby uzyskać więcej informacji, zobacz [metody o nazwie](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) i [anonimowymi](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="425f0-111">For more information, see [Named Methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) and [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>

<span data-ttu-id="425f0-112">Za pomocą metody lub wyrażenia lambda zgodne zwracany typ i parametry wejściowe, można utworzyć wystąpienia obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="425f0-112">The delegate must be instantiated with a method or lambda expression that has a compatible return type and input parameters.</span></span> <span data-ttu-id="425f0-113">Aby uzyskać więcej informacji na temat stopień odchylenia, jaki jest dozwolony w podpisie metody, zobacz [wariancje w Delegatach](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="425f0-113">For more information on the degree of variance that is allowed in the method signature, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span> <span data-ttu-id="425f0-114">Do użytku z metod anonimowych delegat i kodu, które ma zostać skojarzony z nim są zadeklarowane jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="425f0-114">For use with anonymous methods, the delegate and the code to be associated with it are declared together.</span></span> <span data-ttu-id="425f0-115">Obie metody tworzenia wystąpienia obiektów delegowanych zostały omówione w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="425f0-115">Both ways of instantiating delegates are discussed in this section.</span></span>

## <a name="example"></a><span data-ttu-id="425f0-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="425f0-116">Example</span></span>

[!code-csharp[csrefKeywordsTypes#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="425f0-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="425f0-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="425f0-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="425f0-118">See also</span></span>

- [<span data-ttu-id="425f0-119">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="425f0-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="425f0-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="425f0-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="425f0-121">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="425f0-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="425f0-122">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="425f0-122">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
- [<span data-ttu-id="425f0-123">Delegaty</span><span class="sxs-lookup"><span data-stu-id="425f0-123">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
- [<span data-ttu-id="425f0-124">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="425f0-124">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
- [<span data-ttu-id="425f0-125">Delegaci z metodami nazwanymi lub anonimowymi</span><span class="sxs-lookup"><span data-stu-id="425f0-125">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
- [<span data-ttu-id="425f0-126">Metody anonimowe</span><span class="sxs-lookup"><span data-stu-id="425f0-126">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
