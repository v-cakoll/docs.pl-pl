---
title: Delegaty z metodami nazwanymi i C# anonimowymi — Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
ms.openlocfilehash: 1ec366999ca6457471b705fa83f06fcde4293f4e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712380"
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a><span data-ttu-id="5ebed-102">Delegaty z metodami nazwanymi lub anonimowymi (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="5ebed-102">Delegates with Named vs. Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="5ebed-103">[Delegat](../../language-reference/builtin-types/reference-types.md) może być skojarzony z nazwaną metodą.</span><span class="sxs-lookup"><span data-stu-id="5ebed-103">A [delegate](../../language-reference/builtin-types/reference-types.md) can be associated with a named method.</span></span> <span data-ttu-id="5ebed-104">Podczas tworzenia wystąpienia delegata przy użyciu nazwanej metody Metoda jest przenoszona jako parametr, na przykład:</span><span class="sxs-lookup"><span data-stu-id="5ebed-104">When you instantiate a delegate by using a named method, the method is passed as a parameter, for example:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#1)]  
  
 <span data-ttu-id="5ebed-105">Ta metoda jest wywoływana przy użyciu nazwanej metody.</span><span class="sxs-lookup"><span data-stu-id="5ebed-105">This is called using a named method.</span></span> <span data-ttu-id="5ebed-106">Obiekty delegowane skonstruowane przy użyciu nazwanej metody mogą hermetyzować metodę [statyczną](../../language-reference/keywords/static.md) lub metodę wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="5ebed-106">Delegates constructed with a named method can encapsulate either a [static](../../language-reference/keywords/static.md) method or an instance method.</span></span> <span data-ttu-id="5ebed-107">Nazwane metody są jedynym sposobem tworzenia wystąpienia delegata we wcześniejszych wersjach programu C#.</span><span class="sxs-lookup"><span data-stu-id="5ebed-107">Named methods are the only way to instantiate a delegate in earlier versions of C#.</span></span> <span data-ttu-id="5ebed-108">Jednak w sytuacji, w której Tworzenie nowej metody jest niepożądane, C# umożliwia utworzenie wystąpienia delegata i natychmiastowe określenie bloku kodu, który obiekt delegowany będzie przetwarzany po wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="5ebed-108">However, in a situation where creating a new method is unwanted overhead, C# enables you to instantiate a delegate and immediately specify a code block that the delegate will process when it is called.</span></span> <span data-ttu-id="5ebed-109">Blok może zawierać wyrażenie lambda lub metodę anonimową.</span><span class="sxs-lookup"><span data-stu-id="5ebed-109">The block can contain either a lambda expression or an anonymous method.</span></span> <span data-ttu-id="5ebed-110">Aby uzyskać więcej informacji, zobacz [funkcje anonimowe](../statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="5ebed-110">For more information, see [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ebed-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5ebed-111">Remarks</span></span>  
 <span data-ttu-id="5ebed-112">Metoda, która jest przekazywany jako parametr delegata, musi mieć taką samą sygnaturę jak Deklaracja delegata.</span><span class="sxs-lookup"><span data-stu-id="5ebed-112">The method that you pass as a delegate parameter must have the same signature as the delegate declaration.</span></span>  
  
 <span data-ttu-id="5ebed-113">Wystąpienie delegata może hermetyzować wartość statyczną lub metodę wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="5ebed-113">A delegate instance may encapsulate either static or instance method.</span></span>  
  
 <span data-ttu-id="5ebed-114">Chociaż delegat może korzystać z parametru [out](../../language-reference/keywords/out-parameter-modifier.md) , nie zalecamy jej używania z delegatami zdarzeń multiemisji, ponieważ nie można wiedzieć, który delegat zostanie wywołany.</span><span class="sxs-lookup"><span data-stu-id="5ebed-114">Although the delegate can use an [out](../../language-reference/keywords/out-parameter-modifier.md) parameter, we do not recommend its use with multicast event delegates because you cannot know which delegate will be called.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="5ebed-115">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="5ebed-115">Example 1</span></span>  
 <span data-ttu-id="5ebed-116">Poniżej przedstawiono prosty przykład deklarowania i używania delegata.</span><span class="sxs-lookup"><span data-stu-id="5ebed-116">The following is a simple example of declaring and using a delegate.</span></span> <span data-ttu-id="5ebed-117">Zwróć uwagę, że zarówno delegat, `Del`, jak i Metoda skojarzona, `MultiplyNumbers`, mają tę samą sygnaturę</span><span class="sxs-lookup"><span data-stu-id="5ebed-117">Notice that both the delegate, `Del`, and the associated method, `MultiplyNumbers`, have the same signature</span></span>  
  
 [!code-csharp[csProgGuideDelegates#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#2)]  
  
## <a name="example-2"></a><span data-ttu-id="5ebed-118">Przykład 2</span><span class="sxs-lookup"><span data-stu-id="5ebed-118">Example 2</span></span>  
 <span data-ttu-id="5ebed-119">W poniższym przykładzie jeden delegat jest mapowany na metody static i instance i zwraca określone informacje z każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="5ebed-119">In the following example, one delegate is mapped to both static and instance methods and returns specific information from each.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="5ebed-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ebed-120">See also</span></span>

- [<span data-ttu-id="5ebed-121">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5ebed-121">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5ebed-122">Delegaci</span><span class="sxs-lookup"><span data-stu-id="5ebed-122">Delegates</span></span>](./index.md)
- [<span data-ttu-id="5ebed-123">Jak łączyć delegatów (delegatów multiemisji)</span><span class="sxs-lookup"><span data-stu-id="5ebed-123">How to combine delegates (Multicast Delegates)</span></span>](./how-to-combine-delegates-multicast-delegates.md)
- [<span data-ttu-id="5ebed-124">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="5ebed-124">Events</span></span>](../events/index.md)
