---
title: 'Instrukcje: Łączenie obiektów delegowanych (obiekty delegowane multiemisji)- C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: 426b9f91d3e3328522ec5c7ab043d5074ececc43
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970116"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a><span data-ttu-id="24437-102">Instrukcje: Łączenie obiektów delegowanych (obiekty delegowane multiemisji) (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="24437-102">How to: Combine Delegates (Multicast Delegates)(C# Programming Guide)</span></span>
<span data-ttu-id="24437-103">W tym przykładzie pokazano, jak utworzyć obiekty delegowane multiemisji.</span><span class="sxs-lookup"><span data-stu-id="24437-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="24437-104">Przydatne właściwość [delegować](../../../csharp/language-reference/keywords/delegate.md) obiektów jest, że wiele obiektów można przypisać do wystąpienia jednego delegata za pomocą `+` operatora.</span><span class="sxs-lookup"><span data-stu-id="24437-104">A useful property of [delegate](../../../csharp/language-reference/keywords/delegate.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="24437-105">Delegat multiemisji zawiera listę przypisanych delegatów.</span><span class="sxs-lookup"><span data-stu-id="24437-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="24437-106">Po wywołaniu delegata multiemisji wywołuje delegatów na liście w kolejności.</span><span class="sxs-lookup"><span data-stu-id="24437-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="24437-107">Można łączyć tylko obiektów delegowanych z tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="24437-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="24437-108">`-` Operator może służyć do usuwania delegata składnika delegatów multiemisji.</span><span class="sxs-lookup"><span data-stu-id="24437-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24437-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="24437-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="24437-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24437-110">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="24437-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="24437-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="24437-112">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="24437-112">Events</span></span>](../../../csharp/programming-guide/events/index.md)
