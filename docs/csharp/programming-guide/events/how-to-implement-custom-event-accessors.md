---
title: 'Porady: implementowanie niestandardowych metod dostępu zdarzeń (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: 759a7a4518a371449723a23669816bbc0fbc0dee
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581249"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a><span data-ttu-id="326f3-102">Porady: implementowanie niestandardowych metod dostępu zdarzeń (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="326f3-102">How to: Implement Custom Event Accessors (C# Programming Guide)</span></span>
<span data-ttu-id="326f3-103">Zdarzenie jest specjalnym rodzajem multiemisji delegat, który można wywołać tylko z w ramach klasy, która jest zadeklarowana w.</span><span class="sxs-lookup"><span data-stu-id="326f3-103">An event is a special kind of multicast delegate that can only be invoked from within the class that  it is declared in.</span></span> <span data-ttu-id="326f3-104">Kod klienta subskrybuje zdarzenie, podając odwołanie do metody, które powinny być używane, gdy zdarzenie jest uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="326f3-104">Client code subscribes to the event by providing a reference to a method that should be invoked when the event is fired.</span></span> <span data-ttu-id="326f3-105">Te metody są dodawane do listy wywołań obiektu delegowanego przy użyciu metod dostępu zdarzeń, która jest podobna do metody dostępu właściwości, z tą różnicą, że metody dostępu zdarzeń są nazywane `add` i `remove`.</span><span class="sxs-lookup"><span data-stu-id="326f3-105">These methods are added to the delegate's invocation list through event accessors, which resemble property accessors, except that event accessors are named `add` and `remove`.</span></span> <span data-ttu-id="326f3-106">W większości przypadków nie trzeba podać niestandardowych metod dostępu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="326f3-106">In most cases, you do not have to supply custom event accessors.</span></span> <span data-ttu-id="326f3-107">Gdy nie niestandardowych metod dostępu zdarzeń są podane w kodzie, kompilator będzie dodać je automatycznie.</span><span class="sxs-lookup"><span data-stu-id="326f3-107">When no custom event accessors are supplied in your code, the compiler will add them automatically.</span></span> <span data-ttu-id="326f3-108">Jednak w niektórych przypadkach może trzeba będzie podać niestandardowe zachowanie.</span><span class="sxs-lookup"><span data-stu-id="326f3-108">However, in some cases you may have to provide custom behavior.</span></span> <span data-ttu-id="326f3-109">Takiej sytuacji jest wyświetlana w temacie [porady: Implementowanie zdarzenia interfejsu](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).</span><span class="sxs-lookup"><span data-stu-id="326f3-109">One such case is shown in the topic [How to:  Implement Interface Events](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="326f3-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="326f3-110">Example</span></span>  
 <span data-ttu-id="326f3-111">Poniższy przykład pokazuje, jak implementować niestandardowe zdarzenie dostępu add i remove.</span><span class="sxs-lookup"><span data-stu-id="326f3-111">The following example shows how to implement custom add and remove event accessors.</span></span> <span data-ttu-id="326f3-112">Chociaż może zastąpić dowolny kod wewnątrz metody dostępu, zaleca się blokowanie zdarzeń, aby dodać lub usunąć nowej metody obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="326f3-112">Although you can substitute any code inside the accessors, we recommend that you lock the event before you add or remove a new event handler method.</span></span>  
  
[!code-csharp[IDrawingObject.OnDraw](codesnippet/CSharp/how-to-implement-interface-events_1.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a><span data-ttu-id="326f3-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="326f3-113">See Also</span></span>

- [<span data-ttu-id="326f3-114">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="326f3-114">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
- [<span data-ttu-id="326f3-115">event</span><span class="sxs-lookup"><span data-stu-id="326f3-115">event</span></span>](../../../csharp/language-reference/keywords/event.md)