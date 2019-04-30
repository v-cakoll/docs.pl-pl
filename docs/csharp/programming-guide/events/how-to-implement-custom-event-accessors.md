---
title: 'Instrukcje: Implementowanie niestandardowych metod dostępu zdarzeń - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: 8cb6f6f22282ef72f040431e525f1129b46e8c26
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61711151"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a><span data-ttu-id="cfcc1-102">Instrukcje: Implementowanie niestandardowych metod dostępu zdarzeń (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="cfcc1-102">How to: Implement Custom Event Accessors (C# Programming Guide)</span></span>
<span data-ttu-id="cfcc1-103">Zdarzenie jest specjalnym rodzajem multiemisji delegat, który można wywołać tylko z w ramach klasy, która jest zadeklarowana w.</span><span class="sxs-lookup"><span data-stu-id="cfcc1-103">An event is a special kind of multicast delegate that can only be invoked from within the class that  it is declared in.</span></span> <span data-ttu-id="cfcc1-104">Kod klienta subskrybuje zdarzenie, podając odwołanie do metody, które powinny być używane, gdy zdarzenie jest uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="cfcc1-104">Client code subscribes to the event by providing a reference to a method that should be invoked when the event is fired.</span></span> <span data-ttu-id="cfcc1-105">Te metody są dodawane do listy wywołań obiektu delegowanego przy użyciu metod dostępu zdarzeń, która jest podobna do metody dostępu właściwości, z tą różnicą, że metody dostępu zdarzeń są nazywane `add` i `remove`.</span><span class="sxs-lookup"><span data-stu-id="cfcc1-105">These methods are added to the delegate's invocation list through event accessors, which resemble property accessors, except that event accessors are named `add` and `remove`.</span></span> <span data-ttu-id="cfcc1-106">W większości przypadków nie trzeba podać niestandardowych metod dostępu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="cfcc1-106">In most cases, you do not have to supply custom event accessors.</span></span> <span data-ttu-id="cfcc1-107">Gdy nie niestandardowych metod dostępu zdarzeń są podane w kodzie, kompilator będzie dodać je automatycznie.</span><span class="sxs-lookup"><span data-stu-id="cfcc1-107">When no custom event accessors are supplied in your code, the compiler will add them automatically.</span></span> <span data-ttu-id="cfcc1-108">Jednak w niektórych przypadkach może trzeba będzie podać niestandardowe zachowanie.</span><span class="sxs-lookup"><span data-stu-id="cfcc1-108">However, in some cases you may have to provide custom behavior.</span></span> <span data-ttu-id="cfcc1-109">Takiej sytuacji jest wyświetlana w temacie [jak:  Zdarzenia implementowania interfejsu](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).</span><span class="sxs-lookup"><span data-stu-id="cfcc1-109">One such case is shown in the topic [How to:  Implement Interface Events](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfcc1-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="cfcc1-110">Example</span></span>  
 <span data-ttu-id="cfcc1-111">Poniższy przykład pokazuje, jak implementować niestandardowe zdarzenie dostępu add i remove.</span><span class="sxs-lookup"><span data-stu-id="cfcc1-111">The following example shows how to implement custom add and remove event accessors.</span></span> <span data-ttu-id="cfcc1-112">Chociaż może zastąpić dowolny kod wewnątrz metody dostępu, zaleca się blokowanie zdarzeń, aby dodać lub usunąć nowej metody obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="cfcc1-112">Although you can substitute any code inside the accessors, we recommend that you lock the event before you add or remove a new event handler method.</span></span>  
  
[!code-csharp[IDrawingObject.OnDraw](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a><span data-ttu-id="cfcc1-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cfcc1-113">See also</span></span>

- [<span data-ttu-id="cfcc1-114">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cfcc1-114">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="cfcc1-115">event</span><span class="sxs-lookup"><span data-stu-id="cfcc1-115">event</span></span>](../../../csharp/language-reference/keywords/event.md)
