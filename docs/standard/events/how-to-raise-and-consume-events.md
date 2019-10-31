---
title: 'Porady: wywoływanie zdarzeń i korzystanie z nich'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], raising
- raising events
- events [.NET Framework], samples
ms.assetid: 42afade7-3a02-4f2e-868b-95845f302f8f
ms.openlocfilehash: 256b5ae9ac2145e339136985872dfa5423aca730
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131583"
---
# <a name="how-to-raise-and-consume-events"></a><span data-ttu-id="07755-102">Porady: wywoływanie zdarzeń i korzystanie z nich</span><span class="sxs-lookup"><span data-stu-id="07755-102">How to: Raise and Consume Events</span></span>
<span data-ttu-id="07755-103">Przykłady w tym temacie przedstawiają sposób pracy ze zdarzeniami.</span><span class="sxs-lookup"><span data-stu-id="07755-103">The examples in this topic show how to work with events.</span></span> <span data-ttu-id="07755-104">Obejmują one przykłady delegatów <xref:System.EventHandler>, delegatów <xref:System.EventHandler%601> i delegatów niestandardowych, aby zilustrować zdarzenia z danymi i bez nich.</span><span class="sxs-lookup"><span data-stu-id="07755-104">They include examples of the <xref:System.EventHandler> delegate, the <xref:System.EventHandler%601> delegate, and a custom delegate, to illustrate events with and without data.</span></span>  
  
 <span data-ttu-id="07755-105">Przykłady wykorzystują Koncepcje opisane w artykule [zdarzenia](../../../docs/standard/events/index.md) .</span><span class="sxs-lookup"><span data-stu-id="07755-105">The examples use concepts described in the [Events](../../../docs/standard/events/index.md) article.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07755-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="07755-106">Example</span></span>  
 <span data-ttu-id="07755-107">Pierwszy przykład pokazuje, jak podnieść i zużyć zdarzenie, które nie ma danych.</span><span class="sxs-lookup"><span data-stu-id="07755-107">The first example shows how to raise and consume an event that doesn't have data.</span></span> <span data-ttu-id="07755-108">Zawiera klasę o nazwie `Counter`, która ma zdarzenie o nazwie `ThresholdReached`.</span><span class="sxs-lookup"><span data-stu-id="07755-108">It contains a class named `Counter` that has an event named `ThresholdReached`.</span></span> <span data-ttu-id="07755-109">To zdarzenie jest zgłaszane, gdy wartość licznika jest równa lub przekracza wartość progową.</span><span class="sxs-lookup"><span data-stu-id="07755-109">This event is raised when a counter value equals or exceeds a threshold value.</span></span> <span data-ttu-id="07755-110">Delegat <xref:System.EventHandler> jest skojarzony ze zdarzeniem, ponieważ nie podano danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="07755-110">The <xref:System.EventHandler> delegate is associated with the event, because no event data is provided.</span></span>  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="07755-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="07755-111">Example</span></span>  
 <span data-ttu-id="07755-112">W następnym przykładzie pokazano, jak podnieść i zużyć zdarzenie, które dostarcza dane.</span><span class="sxs-lookup"><span data-stu-id="07755-112">The next example shows how to raise and consume an event that provides data.</span></span> <span data-ttu-id="07755-113">Delegat <xref:System.EventHandler%601> jest skojarzony ze zdarzeniem, a wystąpienie obiektu danych zdarzenia niestandardowego jest dostarczone.</span><span class="sxs-lookup"><span data-stu-id="07755-113">The <xref:System.EventHandler%601> delegate is associated with the event, and an instance of a custom event data object is provided.</span></span>  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="07755-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="07755-114">Example</span></span>  
 <span data-ttu-id="07755-115">W następnym przykładzie pokazano, jak zadeklarować delegata dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="07755-115">The next example shows how to declare a delegate for an event.</span></span> <span data-ttu-id="07755-116">Delegat ma nazwę `ThresholdReachedEventHandler`.</span><span class="sxs-lookup"><span data-stu-id="07755-116">The delegate is named `ThresholdReachedEventHandler`.</span></span> <span data-ttu-id="07755-117">Jest to tylko ilustracja.</span><span class="sxs-lookup"><span data-stu-id="07755-117">This is just an illustration.</span></span> <span data-ttu-id="07755-118">Zazwyczaj nie trzeba deklarować delegatów dla zdarzenia, ponieważ można użyć <xref:System.EventHandler> lub delegata <xref:System.EventHandler%601>.</span><span class="sxs-lookup"><span data-stu-id="07755-118">Typically, you do not have to declare a delegate for an event, because you can use either the <xref:System.EventHandler> or the <xref:System.EventHandler%601> delegate.</span></span> <span data-ttu-id="07755-119">Delegata należy zadeklarować tylko w rzadkich scenariuszach, takich jak udostępnienie klasy dla starszego kodu, który nie może używać typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="07755-119">You should declare a delegate only in rare scenarios, such as making your class available to legacy code that cannot use generics.</span></span>  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="07755-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07755-120">See also</span></span>

- [<span data-ttu-id="07755-121">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="07755-121">Events</span></span>](../../../docs/standard/events/index.md)
