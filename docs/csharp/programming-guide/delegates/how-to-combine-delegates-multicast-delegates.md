---
title: 'Instrukcje: Łączenie delegatów (delegatów multiemisji C# ) — Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: d9430021e6a9b438822f1a6dc201f64adf4fdb0f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590663"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a><span data-ttu-id="0d210-102">Instrukcje: Łączenie obiektów delegowanych (obiekty delegowane multiemisji) (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="0d210-102">How to: Combine Delegates (Multicast Delegates)(C# Programming Guide)</span></span>
<span data-ttu-id="0d210-103">W tym przykładzie pokazano, jak utworzyć delegatów multiemisji.</span><span class="sxs-lookup"><span data-stu-id="0d210-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="0d210-104">Przydatna właściwość obiektów [delegatów](../../language-reference/keywords/delegate.md) polega na tym, że wiele obiektów może być przypisanych do jednego wystąpienia delegata przy użyciu `+` operatora.</span><span class="sxs-lookup"><span data-stu-id="0d210-104">A useful property of [delegate](../../language-reference/keywords/delegate.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="0d210-105">Delegat multiemisji zawiera listę przypisanych delegatów.</span><span class="sxs-lookup"><span data-stu-id="0d210-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="0d210-106">Gdy obiekt delegowany multiemisji jest wywoływany, wywołuje delegatów z listy w kolejności.</span><span class="sxs-lookup"><span data-stu-id="0d210-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="0d210-107">Łączyć można tylko Delegaty tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="0d210-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="0d210-108">`-` Operatora można użyć do usunięcia delegata składnika z delegata multiemisji.</span><span class="sxs-lookup"><span data-stu-id="0d210-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d210-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="0d210-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="0d210-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d210-110">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="0d210-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0d210-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0d210-112">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="0d210-112">Events</span></span>](../events/index.md)
