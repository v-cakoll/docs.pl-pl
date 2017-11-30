---
title: "Porady: łączenie obiektów delegowanych (obiekty delegowane multiemisji) (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ddb4ecbbf456179e91aa0003c2dc5653f153411f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a><span data-ttu-id="28315-102">Porady: łączenie obiektów delegowanych (obiekty delegowane multiemisji) (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="28315-102">How to: Combine Delegates (Multicast Delegates)(C# Programming Guide)</span></span>
<span data-ttu-id="28315-103">W tym przykładzie pokazano, jak utworzyć obiekty delegowane multiemisji.</span><span class="sxs-lookup"><span data-stu-id="28315-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="28315-104">Właściwość przydatne [delegować](../../../csharp/language-reference/keywords/delegate.md) obiektów jest, że wiele obiektów można przypisać do wystąpienia jednego delegata za pomocą `+` operatora.</span><span class="sxs-lookup"><span data-stu-id="28315-104">A useful property of [delegate](../../../csharp/language-reference/keywords/delegate.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="28315-105">Delegat multiemisji znajduje się lista przydzielonych obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="28315-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="28315-106">Po wywołaniu multiemisji delegata wywołuje delegatów na liście w kolejności.</span><span class="sxs-lookup"><span data-stu-id="28315-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="28315-107">Można połączyć tylko delegatów tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="28315-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="28315-108">`-` Operator może służyć do usunięcia delegata składnika z multiemisji delegata.</span><span class="sxs-lookup"><span data-stu-id="28315-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28315-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="28315-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="28315-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28315-110">See Also</span></span>  
 <xref:System.MulticastDelegate>  
 [<span data-ttu-id="28315-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="28315-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="28315-112">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="28315-112">Events</span></span>](../../../csharp/programming-guide/events/index.md)
