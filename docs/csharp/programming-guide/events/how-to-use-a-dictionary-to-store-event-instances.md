---
title: 'Instrukcje: Użycie słownika do wystąpień zdarzeń Store - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
ms.openlocfilehash: 819c81aed3a6f09a20e51285058dcc77749dd33a
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245145"
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a><span data-ttu-id="24b1f-102">Instrukcje: Użycie słownika do wystąpień zdarzeń Store (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="24b1f-102">How to: Use a Dictionary to Store Event Instances (C# Programming Guide)</span></span>
<span data-ttu-id="24b1f-103">Jednym z zastosowań `accessor-declarations` na przykład uwidocznić wiele zdarzeń, bez przydzielania pola dla każdego zdarzenia, ale zamiast tego przy użyciu słownika do przechowywania wystąpień zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="24b1f-103">One use for `accessor-declarations` is to expose many events without allocating a field for each event, but instead using a Dictionary to store the event instances.</span></span> <span data-ttu-id="24b1f-104">Jest to przydatne tylko wtedy, jeśli masz wiele zdarzeń, ale możesz spodziewać się, że większość zdarzeń nie będzie zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="24b1f-104">This is only useful if you have many events, but you expect most of the events will not be implemented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24b1f-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="24b1f-105">Example</span></span>  
 [!code-csharp[csProgGuideEvents#9](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-use-a-dictionary-to-store-event-instances_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="24b1f-106">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24b1f-106">See Also</span></span>

- [<span data-ttu-id="24b1f-107">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="24b1f-107">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="24b1f-108">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="24b1f-108">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
- [<span data-ttu-id="24b1f-109">Delegaty</span><span class="sxs-lookup"><span data-stu-id="24b1f-109">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
