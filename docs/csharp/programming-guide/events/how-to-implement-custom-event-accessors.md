---
title: Jak zaimplementować niestandardowe metody dostępu do zdarzeń — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: 34e816799f472e8945962e334b9a90b2582e0393
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705356"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a><span data-ttu-id="f6874-102">Jak zaimplementować niestandardowe metody dostępu do zdarzeń (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="f6874-102">How to implement custom event accessors (C# Programming Guide)</span></span>
<span data-ttu-id="f6874-103">Zdarzenie jest specjalnym rodzajem delegata multiemisji, który może być wywoływany z klasy, w której jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="f6874-103">An event is a special kind of multicast delegate that can only be invoked from within the class that  it is declared in.</span></span> <span data-ttu-id="f6874-104">Kod klienta subskrybuje zdarzenie, podając odwołanie do metody, która powinna być wywoływana, gdy zdarzenie zostanie wyzwolone.</span><span class="sxs-lookup"><span data-stu-id="f6874-104">Client code subscribes to the event by providing a reference to a method that should be invoked when the event is fired.</span></span> <span data-ttu-id="f6874-105">Te metody są dodawane do listy wywołań delegata za pomocą metod dostępu do zdarzeń, które przypominają metody dostępu do właściwości, z tą różnicą, że dostęp do zdarzeń nazywa się `add` i `remove`.</span><span class="sxs-lookup"><span data-stu-id="f6874-105">These methods are added to the delegate's invocation list through event accessors, which resemble property accessors, except that event accessors are named `add` and `remove`.</span></span> <span data-ttu-id="f6874-106">W większości przypadków nie trzeba podawać niestandardowych metod dostępu do zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f6874-106">In most cases, you do not have to supply custom event accessors.</span></span> <span data-ttu-id="f6874-107">Gdy w kodzie nie są dostarczane żadne niestandardowe metody dostępu do zdarzeń, kompilator doda je automatycznie.</span><span class="sxs-lookup"><span data-stu-id="f6874-107">When no custom event accessors are supplied in your code, the compiler will add them automatically.</span></span> <span data-ttu-id="f6874-108">Jednak w niektórych przypadkach może być konieczne zapewnienie zachowania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="f6874-108">However, in some cases you may have to provide custom behavior.</span></span> <span data-ttu-id="f6874-109">W tym temacie pokazano, [jak zaimplementować zdarzenia interfejsu](./how-to-implement-interface-events.md).</span><span class="sxs-lookup"><span data-stu-id="f6874-109">One such case is shown in the topic [How to implement interface events](./how-to-implement-interface-events.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="f6874-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6874-110">Example</span></span>  
 <span data-ttu-id="f6874-111">Poniższy przykład przedstawia sposób implementacji niestandardowych metod dostępu do zdarzeń dodawania i usuwania.</span><span class="sxs-lookup"><span data-stu-id="f6874-111">The following example shows how to implement custom add and remove event accessors.</span></span> <span data-ttu-id="f6874-112">Chociaż można zastąpić dowolny kod wewnątrz metod dostępu, Zalecamy zablokowanie zdarzenia przed dodaniem lub usunięciem nowej metody obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f6874-112">Although you can substitute any code inside the accessors, we recommend that you lock the event before you add or remove a new event handler method.</span></span>  
  
[!code-csharp[IDrawingObject.OnDraw](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a><span data-ttu-id="f6874-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6874-113">See also</span></span>

- [<span data-ttu-id="f6874-114">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f6874-114">Events</span></span>](./index.md)
- [<span data-ttu-id="f6874-115">event</span><span class="sxs-lookup"><span data-stu-id="f6874-115">event</span></span>](../../language-reference/keywords/event.md)
