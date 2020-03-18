---
title: Jak połączyć delegatów (delegatów multiemisji) - C# Programming Guide
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: 7b5b9ba5c9bf70983fac9f869836b4c8c5449eca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705382"
---
# <a name="how-to-combine-delegates-multicast-delegates-c-programming-guide"></a><span data-ttu-id="2262e-102">Łączenie obiektów delegowanych (obiekty delegowane multiemisji) (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="2262e-102">How to combine delegates (Multicast Delegates) (C# Programming Guide)</span></span>
<span data-ttu-id="2262e-103">W tym przykładzie pokazano, jak utworzyć delegatów multiemisji.</span><span class="sxs-lookup"><span data-stu-id="2262e-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="2262e-104">Przydatną właściwością obiektów [delegowanych](../../language-reference/builtin-types/reference-types.md) jest, że wiele obiektów można przypisać `+` do jednego wystąpienia delegata za pomocą operatora.</span><span class="sxs-lookup"><span data-stu-id="2262e-104">A useful property of [delegate](../../language-reference/builtin-types/reference-types.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="2262e-105">Pełnomocnik multiemisji zawiera listę przydzielonych delegatów.</span><span class="sxs-lookup"><span data-stu-id="2262e-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="2262e-106">Gdy delegat multiemisji jest wywoływana, wywołuje delegatów na liście, w kolejności.</span><span class="sxs-lookup"><span data-stu-id="2262e-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="2262e-107">Można łączyć tylko delegatów tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="2262e-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="2262e-108">Operator `-` może służyć do usuwania delegata składnika z delegata multiemisji.</span><span class="sxs-lookup"><span data-stu-id="2262e-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2262e-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="2262e-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="2262e-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2262e-110">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="2262e-111">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="2262e-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2262e-112">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="2262e-112">Events</span></span>](../events/index.md)
