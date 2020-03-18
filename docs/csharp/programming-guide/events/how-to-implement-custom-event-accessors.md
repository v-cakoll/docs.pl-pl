---
title: Jak zaimplementować niestandardowe akcesory zdarzeń - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: 34e816799f472e8945962e334b9a90b2582e0393
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705356"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a><span data-ttu-id="aea47-102">Jak zaimplementować niestandardowe akcesory zdarzeń (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="aea47-102">How to implement custom event accessors (C# Programming Guide)</span></span>
<span data-ttu-id="aea47-103">Zdarzenie jest specjalny rodzaj delegata multiemisji, które mogą być wywoływane tylko z wewnątrz klasy, która jest zadeklarowana w.</span><span class="sxs-lookup"><span data-stu-id="aea47-103">An event is a special kind of multicast delegate that can only be invoked from within the class that  it is declared in.</span></span> <span data-ttu-id="aea47-104">Kod klienta subskrybuje zdarzenie, podając odwołanie do metody, która powinna być wywoływana podczas odpalania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="aea47-104">Client code subscribes to the event by providing a reference to a method that should be invoked when the event is fired.</span></span> <span data-ttu-id="aea47-105">Metody te są dodawane do listy wywołania delegata za pośrednictwem akcesorów zdarzeń, które `add` przypominają `remove`akcesory właściwości, z tą różnicą, że akcesory zdarzeń są nazwane i .</span><span class="sxs-lookup"><span data-stu-id="aea47-105">These methods are added to the delegate's invocation list through event accessors, which resemble property accessors, except that event accessors are named `add` and `remove`.</span></span> <span data-ttu-id="aea47-106">W większości przypadków nie trzeba podać niestandardowych akcesorów zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="aea47-106">In most cases, you do not have to supply custom event accessors.</span></span> <span data-ttu-id="aea47-107">Jeśli w kodzie nie są dostarczane żadne niestandardowe akcesory zdarzeń, kompilator doda je automatycznie.</span><span class="sxs-lookup"><span data-stu-id="aea47-107">When no custom event accessors are supplied in your code, the compiler will add them automatically.</span></span> <span data-ttu-id="aea47-108">Jednak w niektórych przypadkach może być trzeba podać zachowanie niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="aea47-108">However, in some cases you may have to provide custom behavior.</span></span> <span data-ttu-id="aea47-109">Jeden taki przypadek jest pokazany w temacie [Jak zaimplementować zdarzenia interfejsu](./how-to-implement-interface-events.md).</span><span class="sxs-lookup"><span data-stu-id="aea47-109">One such case is shown in the topic [How to implement interface events](./how-to-implement-interface-events.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="aea47-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="aea47-110">Example</span></span>  
 <span data-ttu-id="aea47-111">W poniższym przykładzie pokazano, jak zaimplementować niestandardowe dodawanie i usuwanie akcesorów zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="aea47-111">The following example shows how to implement custom add and remove event accessors.</span></span> <span data-ttu-id="aea47-112">Mimo że można zastąpić dowolny kod wewnątrz akcesorów, zaleca się zablokowanie zdarzenia przed dodaniem lub usunięciem nowej metody obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="aea47-112">Although you can substitute any code inside the accessors, we recommend that you lock the event before you add or remove a new event handler method.</span></span>  
  
[!code-csharp[IDrawingObject.OnDraw](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a><span data-ttu-id="aea47-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aea47-113">See also</span></span>

- [<span data-ttu-id="aea47-114">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="aea47-114">Events</span></span>](./index.md)
- [<span data-ttu-id="aea47-115">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="aea47-115">event</span></span>](../../language-reference/keywords/event.md)
