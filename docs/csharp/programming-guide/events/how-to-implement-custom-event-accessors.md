---
title: 'Instrukcje: Implementowanie niestandardowych metod dostępu do C# zdarzeń — Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: 4eaf8b4c3038d07d5b0fc021e21c7f1a2de85d74
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590523"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a><span data-ttu-id="c993f-102">Instrukcje: Implementowanie niestandardowych metod dostępu doC# zdarzeń (Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="c993f-102">How to: Implement Custom Event Accessors (C# Programming Guide)</span></span>
<span data-ttu-id="c993f-103">Zdarzenie jest specjalnym rodzajem delegata multiemisji, który może być wywoływany z klasy, w której jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="c993f-103">An event is a special kind of multicast delegate that can only be invoked from within the class that  it is declared in.</span></span> <span data-ttu-id="c993f-104">Kod klienta subskrybuje zdarzenie, podając odwołanie do metody, która powinna być wywoływana, gdy zdarzenie zostanie wyzwolone.</span><span class="sxs-lookup"><span data-stu-id="c993f-104">Client code subscribes to the event by providing a reference to a method that should be invoked when the event is fired.</span></span> <span data-ttu-id="c993f-105">Te metody są dodawane do listy wywołań delegata za pomocą metod dostępu do zdarzeń, które przypominają metody dostępu do właściwości, z tą różnicą, że `add` dostęp `remove`do zdarzeń jest nazwany i.</span><span class="sxs-lookup"><span data-stu-id="c993f-105">These methods are added to the delegate's invocation list through event accessors, which resemble property accessors, except that event accessors are named `add` and `remove`.</span></span> <span data-ttu-id="c993f-106">W większości przypadków nie trzeba podawać niestandardowych metod dostępu do zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c993f-106">In most cases, you do not have to supply custom event accessors.</span></span> <span data-ttu-id="c993f-107">Gdy w kodzie nie są dostarczane żadne niestandardowe metody dostępu do zdarzeń, kompilator doda je automatycznie.</span><span class="sxs-lookup"><span data-stu-id="c993f-107">When no custom event accessors are supplied in your code, the compiler will add them automatically.</span></span> <span data-ttu-id="c993f-108">Jednak w niektórych przypadkach może być konieczne zapewnienie zachowania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="c993f-108">However, in some cases you may have to provide custom behavior.</span></span> <span data-ttu-id="c993f-109">Jeden z takich przypadków przedstawiono w temacie [jak:  Implementuj zdarzenia](./how-to-implement-interface-events.md)interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c993f-109">One such case is shown in the topic [How to:  Implement Interface Events](./how-to-implement-interface-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c993f-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="c993f-110">Example</span></span>  
 <span data-ttu-id="c993f-111">Poniższy przykład przedstawia sposób implementacji niestandardowych metod dostępu do zdarzeń dodawania i usuwania.</span><span class="sxs-lookup"><span data-stu-id="c993f-111">The following example shows how to implement custom add and remove event accessors.</span></span> <span data-ttu-id="c993f-112">Chociaż można zastąpić dowolny kod wewnątrz metod dostępu, Zalecamy zablokowanie zdarzenia przed dodaniem lub usunięciem nowej metody obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c993f-112">Although you can substitute any code inside the accessors, we recommend that you lock the event before you add or remove a new event handler method.</span></span>  
  
[!code-csharp[IDrawingObject.OnDraw](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a><span data-ttu-id="c993f-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c993f-113">See also</span></span>

- [<span data-ttu-id="c993f-114">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c993f-114">Events</span></span>](./index.md)
- [<span data-ttu-id="c993f-115">event</span><span class="sxs-lookup"><span data-stu-id="c993f-115">event</span></span>](../../language-reference/keywords/event.md)
