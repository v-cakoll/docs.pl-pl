---
title: Delegaty z nazwanymi lub. Metody anonimowe (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
ms.openlocfilehash: 6d7dcb3c7c6fa8f1d55237504c23cf468aa0e79d
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45678525"
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a><span data-ttu-id="68aaa-102">Delegaty z nazwanymi lub. Metody anonimowe (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="68aaa-102">Delegates with Named vs. Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="68aaa-103">A [delegować](../../../csharp/language-reference/keywords/delegate.md) mogą być skojarzone z metodę o nazwie.</span><span class="sxs-lookup"><span data-stu-id="68aaa-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) can be associated with a named method.</span></span> <span data-ttu-id="68aaa-104">Podczas tworzenia wystąpienia delegata za pomocą metodę o nazwie metoda jest przekazywana jako parametr, na przykład:</span><span class="sxs-lookup"><span data-stu-id="68aaa-104">When you instantiate a delegate by using a named method, the method is passed as a parameter, for example:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#1](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_1.cs)]  
  
 <span data-ttu-id="68aaa-105">Jest to, za pomocą innej metody o nazwie.</span><span class="sxs-lookup"><span data-stu-id="68aaa-105">This is called using a named method.</span></span> <span data-ttu-id="68aaa-106">Delegaty skonstruowany przy użyciu metodę o nazwie umożliwiająca Hermetyzowanie albo [statyczne](../../../csharp/language-reference/keywords/static.md) metodę lub metodę wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="68aaa-106">Delegates constructed with a named method can encapsulate either a [static](../../../csharp/language-reference/keywords/static.md) method or an instance method.</span></span> <span data-ttu-id="68aaa-107">Metody o nazwie są jedynym sposobem tworzenia wystąpienia delegata we wcześniejszych wersjach języka C#.</span><span class="sxs-lookup"><span data-stu-id="68aaa-107">Named methods are the only way to instantiate a delegate in earlier versions of C#.</span></span> <span data-ttu-id="68aaa-108">Jednak w sytuacji, w których utworzenie nowej metody jest niechciane obciążenie, C# umożliwia tworzenia wystąpienia delegata i natychmiast określić blok kodu, który przetworzy delegata, gdy jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="68aaa-108">However, in a situation where creating a new method is unwanted overhead, C# enables you to instantiate a delegate and immediately specify a code block that the delegate will process when it is called.</span></span> <span data-ttu-id="68aaa-109">Blok może zawierać wyrażenia lambda lub metodę anonimową.</span><span class="sxs-lookup"><span data-stu-id="68aaa-109">The block can contain either a lambda expression or an anonymous method.</span></span> <span data-ttu-id="68aaa-110">Aby uzyskać więcej informacji, zobacz [funkcjami anonimowymi](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="68aaa-110">For more information, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68aaa-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="68aaa-111">Remarks</span></span>  
 <span data-ttu-id="68aaa-112">Metoda, który jest przekazywany jako parametr delegata musi mieć taką samą sygnaturę jak deklaracja delegata.</span><span class="sxs-lookup"><span data-stu-id="68aaa-112">The method that you pass as a delegate parameter must have the same signature as the delegate declaration.</span></span>  
  
 <span data-ttu-id="68aaa-113">Wystąpienie delegata może hermetyzacji statycznych lub metodę wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="68aaa-113">A delegate instance may encapsulate either static or instance method.</span></span>  
  
 <span data-ttu-id="68aaa-114">Chociaż można używać delegata [się](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametru, nie zaleca się korzystanie z delegaty multiemisji zdarzeń ponieważ nie wie, delegata, która zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="68aaa-114">Although the delegate can use an [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter, we do not recommend its use with multicast event delegates because you cannot know which delegate will be called.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="68aaa-115">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="68aaa-115">Example 1</span></span>  
 <span data-ttu-id="68aaa-116">Oto prosty przykład deklarowanie i używanie delegata.</span><span class="sxs-lookup"><span data-stu-id="68aaa-116">The following is a simple example of declaring and using a delegate.</span></span> <span data-ttu-id="68aaa-117">Należy zauważyć, że oba delegata, `Del`i skojarzoną metodę `MultiplyNumbers`, mają taki sam podpis</span><span class="sxs-lookup"><span data-stu-id="68aaa-117">Notice that both the delegate, `Del`, and the associated method, `MultiplyNumbers`, have the same signature</span></span>  
  
 [!code-csharp[csProgGuideDelegates#2](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_2.cs)]  
  
## <a name="example-2"></a><span data-ttu-id="68aaa-118">Przykład 2</span><span class="sxs-lookup"><span data-stu-id="68aaa-118">Example 2</span></span>  
 <span data-ttu-id="68aaa-119">W poniższym przykładzie jednego delegata jest mapowany na statycznych i metod i zwraca szczegółowe informacje z każdego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="68aaa-119">In the following example, one delegate is mapped to both static and instance methods and returns specific information from each.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#3](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="68aaa-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="68aaa-120">See Also</span></span>

- [<span data-ttu-id="68aaa-121">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="68aaa-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="68aaa-122">Delegaci</span><span class="sxs-lookup"><span data-stu-id="68aaa-122">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
- [<span data-ttu-id="68aaa-123">Metody anonimowe</span><span class="sxs-lookup"><span data-stu-id="68aaa-123">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
- [<span data-ttu-id="68aaa-124">Porady: łączenie obiektów delegowanych (obiekty delegowane multiemisji)</span><span class="sxs-lookup"><span data-stu-id="68aaa-124">How to: Combine Delegates (Multicast Delegates)</span></span>](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
- [<span data-ttu-id="68aaa-125">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="68aaa-125">Events</span></span>](../../../csharp/programming-guide/events/index.md)
