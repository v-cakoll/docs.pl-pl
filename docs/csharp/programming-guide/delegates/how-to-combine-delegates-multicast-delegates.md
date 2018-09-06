---
title: 'Porady: łączenie obiektów delegowanych (obiekty delegowane multiemisji) (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: e3cc3f9082bd86004a7821b64c01253408c07641
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43883181"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a><span data-ttu-id="575ea-102">Porady: łączenie obiektów delegowanych (obiekty delegowane multiemisji) (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="575ea-102">How to: Combine Delegates (Multicast Delegates)(C# Programming Guide)</span></span>
<span data-ttu-id="575ea-103">W tym przykładzie pokazano, jak utworzyć obiekty delegowane multiemisji.</span><span class="sxs-lookup"><span data-stu-id="575ea-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="575ea-104">Przydatne właściwość [delegować](../../../csharp/language-reference/keywords/delegate.md) obiektów jest, że wiele obiektów można przypisać do wystąpienia jednego delegata za pomocą `+` operatora.</span><span class="sxs-lookup"><span data-stu-id="575ea-104">A useful property of [delegate](../../../csharp/language-reference/keywords/delegate.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="575ea-105">Delegat multiemisji zawiera listę przypisanych delegatów.</span><span class="sxs-lookup"><span data-stu-id="575ea-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="575ea-106">Po wywołaniu delegata multiemisji wywołuje delegatów na liście w kolejności.</span><span class="sxs-lookup"><span data-stu-id="575ea-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="575ea-107">Można łączyć tylko obiektów delegowanych z tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="575ea-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="575ea-108">`-` Operator może służyć do usuwania delegata składnika delegatów multiemisji.</span><span class="sxs-lookup"><span data-stu-id="575ea-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="575ea-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="575ea-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="575ea-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="575ea-110">See Also</span></span>

- <xref:System.MulticastDelegate>  
- [<span data-ttu-id="575ea-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="575ea-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="575ea-112">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="575ea-112">Events</span></span>](../../../csharp/programming-guide/events/index.md)
