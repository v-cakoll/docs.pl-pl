---
title: 'Instrukcje: Łączenie obiektów delegowanych (obiekty delegowane multiemisji)- C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: 426b9f91d3e3328522ec5c7ab043d5074ececc43
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61711023"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a><span data-ttu-id="079e6-102">Instrukcje: Łączenie obiektów delegowanych (obiekty delegowane multiemisji) (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="079e6-102">How to: Combine Delegates (Multicast Delegates)(C# Programming Guide)</span></span>
<span data-ttu-id="079e6-103">W tym przykładzie pokazano, jak utworzyć obiekty delegowane multiemisji.</span><span class="sxs-lookup"><span data-stu-id="079e6-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="079e6-104">Przydatne właściwość [delegować](../../../csharp/language-reference/keywords/delegate.md) obiektów jest, że wiele obiektów można przypisać do wystąpienia jednego delegata za pomocą `+` operatora.</span><span class="sxs-lookup"><span data-stu-id="079e6-104">A useful property of [delegate](../../../csharp/language-reference/keywords/delegate.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="079e6-105">Delegat multiemisji zawiera listę przypisanych delegatów.</span><span class="sxs-lookup"><span data-stu-id="079e6-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="079e6-106">Po wywołaniu delegata multiemisji wywołuje delegatów na liście w kolejności.</span><span class="sxs-lookup"><span data-stu-id="079e6-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="079e6-107">Można łączyć tylko obiektów delegowanych z tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="079e6-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="079e6-108">`-` Operator może służyć do usuwania delegata składnika delegatów multiemisji.</span><span class="sxs-lookup"><span data-stu-id="079e6-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="079e6-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="079e6-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="079e6-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="079e6-110">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="079e6-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="079e6-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="079e6-112">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="079e6-112">Events</span></span>](../../../csharp/programming-guide/events/index.md)
