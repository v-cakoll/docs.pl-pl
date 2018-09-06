---
title: 'Porady: użycie słownika do przechowywania wystąpień zdarzeń (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
ms.openlocfilehash: c3a804ce1bf1f5ac8db47f0f0c1f37d1ca5f781b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43741721"
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a><span data-ttu-id="0333b-102">Porady: użycie słownika do przechowywania wystąpień zdarzeń (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="0333b-102">How to: Use a Dictionary to Store Event Instances (C# Programming Guide)</span></span>
<span data-ttu-id="0333b-103">Jednym z zastosowań `accessor-declarations` na przykład uwidocznić wiele zdarzeń, bez przydzielania pola dla każdego zdarzenia, ale zamiast tego przy użyciu słownika do przechowywania wystąpień zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0333b-103">One use for `accessor-declarations` is to expose many events without allocating a field for each event, but instead using a Dictionary to store the event instances.</span></span> <span data-ttu-id="0333b-104">Jest to przydatne tylko wtedy, jeśli masz wiele zdarzeń, ale możesz spodziewać się, że większość zdarzeń nie będzie zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="0333b-104">This is only useful if you have many events, but you expect most of the events will not be implemented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0333b-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="0333b-105">Example</span></span>  
 [!code-csharp[csProgGuideEvents#9](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-use-a-dictionary-to-store-event-instances_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="0333b-106">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0333b-106">See Also</span></span>

- [<span data-ttu-id="0333b-107">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0333b-107">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="0333b-108">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="0333b-108">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
- [<span data-ttu-id="0333b-109">Delegaci</span><span class="sxs-lookup"><span data-stu-id="0333b-109">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
