---
title: Pełnomocnicy z nazwanymi i anonimowymi metodami — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
ms.openlocfilehash: 1ec366999ca6457471b705fa83f06fcde4293f4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712380"
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a><span data-ttu-id="da0f8-102">Delegaty z metodami nazwanymi lub anonimowymi (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="da0f8-102">Delegates with Named vs. Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="da0f8-103">[Pełnomocnik](../../language-reference/builtin-types/reference-types.md) a może być skojarzony z nazwanego metody.</span><span class="sxs-lookup"><span data-stu-id="da0f8-103">A [delegate](../../language-reference/builtin-types/reference-types.md) can be associated with a named method.</span></span> <span data-ttu-id="da0f8-104">Podczas tworzenia wystąpienia delegata przy użyciu metody nazwane, metoda jest przekazywana jako parametr, na przykład:</span><span class="sxs-lookup"><span data-stu-id="da0f8-104">When you instantiate a delegate by using a named method, the method is passed as a parameter, for example:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#1)]  
  
 <span data-ttu-id="da0f8-105">Jest to wywoływane przy użyciu metody o nazwie.</span><span class="sxs-lookup"><span data-stu-id="da0f8-105">This is called using a named method.</span></span> <span data-ttu-id="da0f8-106">Delegaci skonstruowane z nazwanego metody może hermetyzować metodę [statyczną](../../language-reference/keywords/static.md) lub metody wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="da0f8-106">Delegates constructed with a named method can encapsulate either a [static](../../language-reference/keywords/static.md) method or an instance method.</span></span> <span data-ttu-id="da0f8-107">Nazwane metody są jedynym sposobem wystąpienia delegata we wcześniejszych wersjach języka C#.</span><span class="sxs-lookup"><span data-stu-id="da0f8-107">Named methods are the only way to instantiate a delegate in earlier versions of C#.</span></span> <span data-ttu-id="da0f8-108">Jednak w sytuacji, gdy tworzenie nowej metody jest niepożądane obciążenie, C# umożliwia utworzenie wystąpienia delegata i natychmiast określić blok kodu, który pełnomocnik będzie przetwarzać, gdy jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="da0f8-108">However, in a situation where creating a new method is unwanted overhead, C# enables you to instantiate a delegate and immediately specify a code block that the delegate will process when it is called.</span></span> <span data-ttu-id="da0f8-109">Blok może zawierać wyrażenie lambda lub metodę anonimową.</span><span class="sxs-lookup"><span data-stu-id="da0f8-109">The block can contain either a lambda expression or an anonymous method.</span></span> <span data-ttu-id="da0f8-110">Aby uzyskać więcej informacji, zobacz [Funkcje anonimowe](../statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="da0f8-110">For more information, see [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da0f8-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="da0f8-111">Remarks</span></span>  
 <span data-ttu-id="da0f8-112">Metoda, która jest przekazana jako parametr delegata musi mieć ten sam podpis jako deklaracja delegata.</span><span class="sxs-lookup"><span data-stu-id="da0f8-112">The method that you pass as a delegate parameter must have the same signature as the delegate declaration.</span></span>  
  
 <span data-ttu-id="da0f8-113">Wystąpienie delegata może hermetyzować metodę statyczną lub instancję.</span><span class="sxs-lookup"><span data-stu-id="da0f8-113">A delegate instance may encapsulate either static or instance method.</span></span>  
  
 <span data-ttu-id="da0f8-114">Mimo że pełnomocnik może użyć [out](../../language-reference/keywords/out-parameter-modifier.md) parametru, nie zaleca się jego użycia z delegatów zdarzeń multiemisji, ponieważ nie wiadomo, który delegat zostanie wywołany.</span><span class="sxs-lookup"><span data-stu-id="da0f8-114">Although the delegate can use an [out](../../language-reference/keywords/out-parameter-modifier.md) parameter, we do not recommend its use with multicast event delegates because you cannot know which delegate will be called.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="da0f8-115">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="da0f8-115">Example 1</span></span>  
 <span data-ttu-id="da0f8-116">Poniżej przedstawiono prosty przykład deklarowania i używania pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="da0f8-116">The following is a simple example of declaring and using a delegate.</span></span> <span data-ttu-id="da0f8-117">Należy zauważyć, że `Del`zarówno pełnomocnik, i `MultiplyNumbers`skojarzona metoda , mają ten sam podpis</span><span class="sxs-lookup"><span data-stu-id="da0f8-117">Notice that both the delegate, `Del`, and the associated method, `MultiplyNumbers`, have the same signature</span></span>  
  
 [!code-csharp[csProgGuideDelegates#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#2)]  
  
## <a name="example-2"></a><span data-ttu-id="da0f8-118">Przykład 2</span><span class="sxs-lookup"><span data-stu-id="da0f8-118">Example 2</span></span>  
 <span data-ttu-id="da0f8-119">W poniższym przykładzie jeden delegat jest mapowany na metody statyczne i wystąpienia i zwraca określone informacje z każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="da0f8-119">In the following example, one delegate is mapped to both static and instance methods and returns specific information from each.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="da0f8-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da0f8-120">See also</span></span>

- [<span data-ttu-id="da0f8-121">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="da0f8-121">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="da0f8-122">Delegaty</span><span class="sxs-lookup"><span data-stu-id="da0f8-122">Delegates</span></span>](./index.md)
- [<span data-ttu-id="da0f8-123">Jak połączyć delegatów (delegatów multiemisji)</span><span class="sxs-lookup"><span data-stu-id="da0f8-123">How to combine delegates (Multicast Delegates)</span></span>](./how-to-combine-delegates-multicast-delegates.md)
- [<span data-ttu-id="da0f8-124">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="da0f8-124">Events</span></span>](../events/index.md)
