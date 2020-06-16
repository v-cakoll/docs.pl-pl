---
title: 'Porady: wywoływanie zdarzeń i korzystanie z nich'
description: Zgłoś & zużywać zdarzenia w programie .NET. Zobacz przykłady, które używają delegata EventHandler, <TEventArgs> delegata EventHandler, & delegata niestandardowego.
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
ms.openlocfilehash: 4054e1a26c3392870af994a6eceafae92176a332
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769278"
---
# <a name="how-to-raise-and-consume-events"></a><span data-ttu-id="aa592-104">Porady: wywoływanie zdarzeń i korzystanie z nich</span><span class="sxs-lookup"><span data-stu-id="aa592-104">How to: Raise and Consume Events</span></span>
<span data-ttu-id="aa592-105">Przykłady w tym temacie przedstawiają sposób pracy ze zdarzeniami.</span><span class="sxs-lookup"><span data-stu-id="aa592-105">The examples in this topic show how to work with events.</span></span> <span data-ttu-id="aa592-106">Obejmują one przykłady <xref:System.EventHandler> delegata, <xref:System.EventHandler%601> delegata i delegata niestandardowego, które ilustrują zdarzenia z i bez danych.</span><span class="sxs-lookup"><span data-stu-id="aa592-106">They include examples of the <xref:System.EventHandler> delegate, the <xref:System.EventHandler%601> delegate, and a custom delegate, to illustrate events with and without data.</span></span>  
  
 <span data-ttu-id="aa592-107">Przykłady wykorzystują Koncepcje opisane w artykule [zdarzenia](index.md) .</span><span class="sxs-lookup"><span data-stu-id="aa592-107">The examples use concepts described in the [Events](index.md) article.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa592-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa592-108">Example</span></span>  
 <span data-ttu-id="aa592-109">Pierwszy przykład pokazuje, jak podnieść i zużyć zdarzenie, które nie ma danych.</span><span class="sxs-lookup"><span data-stu-id="aa592-109">The first example shows how to raise and consume an event that doesn't have data.</span></span> <span data-ttu-id="aa592-110">Zawiera klasę o nazwie `Counter` , która ma zdarzenie o nazwie `ThresholdReached` .</span><span class="sxs-lookup"><span data-stu-id="aa592-110">It contains a class named `Counter` that has an event named `ThresholdReached`.</span></span> <span data-ttu-id="aa592-111">To zdarzenie jest zgłaszane, gdy wartość licznika jest równa lub przekracza wartość progową.</span><span class="sxs-lookup"><span data-stu-id="aa592-111">This event is raised when a counter value equals or exceeds a threshold value.</span></span> <span data-ttu-id="aa592-112"><xref:System.EventHandler>Delegat jest skojarzony ze zdarzeniem, ponieważ nie podano danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="aa592-112">The <xref:System.EventHandler> delegate is associated with the event, because no event data is provided.</span></span>  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="aa592-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa592-113">Example</span></span>  
 <span data-ttu-id="aa592-114">W następnym przykładzie pokazano, jak podnieść i zużyć zdarzenie, które dostarcza dane.</span><span class="sxs-lookup"><span data-stu-id="aa592-114">The next example shows how to raise and consume an event that provides data.</span></span> <span data-ttu-id="aa592-115"><xref:System.EventHandler%601>Delegat jest skojarzony ze zdarzeniem, a wystąpienie obiektu danych zdarzenia niestandardowego jest dostarczone.</span><span class="sxs-lookup"><span data-stu-id="aa592-115">The <xref:System.EventHandler%601> delegate is associated with the event, and an instance of a custom event data object is provided.</span></span>  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="aa592-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa592-116">Example</span></span>  
 <span data-ttu-id="aa592-117">W następnym przykładzie pokazano, jak zadeklarować delegata dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="aa592-117">The next example shows how to declare a delegate for an event.</span></span> <span data-ttu-id="aa592-118">Delegat ma nazwę `ThresholdReachedEventHandler` .</span><span class="sxs-lookup"><span data-stu-id="aa592-118">The delegate is named `ThresholdReachedEventHandler`.</span></span> <span data-ttu-id="aa592-119">Jest to tylko ilustracja.</span><span class="sxs-lookup"><span data-stu-id="aa592-119">This is just an illustration.</span></span> <span data-ttu-id="aa592-120">Zazwyczaj nie trzeba deklarować delegatów dla zdarzenia, ponieważ można użyć albo <xref:System.EventHandler> <xref:System.EventHandler%601> delegata.</span><span class="sxs-lookup"><span data-stu-id="aa592-120">Typically, you do not have to declare a delegate for an event, because you can use either the <xref:System.EventHandler> or the <xref:System.EventHandler%601> delegate.</span></span> <span data-ttu-id="aa592-121">Delegata należy zadeklarować tylko w rzadkich scenariuszach, takich jak udostępnienie klasy dla starszego kodu, który nie może używać typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="aa592-121">You should declare a delegate only in rare scenarios, such as making your class available to legacy code that cannot use generics.</span></span>  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="aa592-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aa592-122">See also</span></span>

- [<span data-ttu-id="aa592-123">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="aa592-123">Events</span></span>](index.md)
