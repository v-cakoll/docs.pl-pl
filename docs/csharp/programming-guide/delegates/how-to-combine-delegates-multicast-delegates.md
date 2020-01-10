---
title: Jak łączyć delegatów (delegatów multiemisji) C# — Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: 7b5b9ba5c9bf70983fac9f869836b4c8c5449eca
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705382"
---
# <a name="how-to-combine-delegates-multicast-delegates-c-programming-guide"></a><span data-ttu-id="bbfbd-102">Łączenie obiektów delegowanych (obiekty delegowane multiemisji) (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="bbfbd-102">How to combine delegates (Multicast Delegates) (C# Programming Guide)</span></span>
<span data-ttu-id="bbfbd-103">W tym przykładzie pokazano, jak utworzyć delegatów multiemisji.</span><span class="sxs-lookup"><span data-stu-id="bbfbd-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="bbfbd-104">Przydatna właściwość obiektów [delegatów](../../language-reference/builtin-types/reference-types.md) polega na tym, że wiele obiektów może być przypisanych do jednego wystąpienia delegata przy użyciu operatora `+`.</span><span class="sxs-lookup"><span data-stu-id="bbfbd-104">A useful property of [delegate](../../language-reference/builtin-types/reference-types.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="bbfbd-105">Delegat multiemisji zawiera listę przypisanych delegatów.</span><span class="sxs-lookup"><span data-stu-id="bbfbd-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="bbfbd-106">Gdy obiekt delegowany multiemisji jest wywoływany, wywołuje delegatów z listy w kolejności.</span><span class="sxs-lookup"><span data-stu-id="bbfbd-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="bbfbd-107">Łączyć można tylko Delegaty tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="bbfbd-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="bbfbd-108">Operatora `-` można użyć do usunięcia delegata składnika z delegata multiemisji.</span><span class="sxs-lookup"><span data-stu-id="bbfbd-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbfbd-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="bbfbd-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="bbfbd-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bbfbd-110">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="bbfbd-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="bbfbd-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="bbfbd-112">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="bbfbd-112">Events</span></span>](../events/index.md)
