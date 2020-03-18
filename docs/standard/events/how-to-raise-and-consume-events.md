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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73131583"
---
# <a name="how-to-raise-and-consume-events"></a><span data-ttu-id="3553d-102">Porady: wywoływanie zdarzeń i korzystanie z nich</span><span class="sxs-lookup"><span data-stu-id="3553d-102">How to: Raise and Consume Events</span></span>
<span data-ttu-id="3553d-103">Przykłady w tym temacie pokazują, jak pracować ze zdarzeniami.</span><span class="sxs-lookup"><span data-stu-id="3553d-103">The examples in this topic show how to work with events.</span></span> <span data-ttu-id="3553d-104">Obejmują one przykłady <xref:System.EventHandler> pełnomocnika, <xref:System.EventHandler%601> delegata i delegata niestandardowego, aby zilustrować zdarzenia z danymi i bez nich.</span><span class="sxs-lookup"><span data-stu-id="3553d-104">They include examples of the <xref:System.EventHandler> delegate, the <xref:System.EventHandler%601> delegate, and a custom delegate, to illustrate events with and without data.</span></span>  
  
 <span data-ttu-id="3553d-105">W przykładach są używane pojęcia opisane w [artykule Zdarzenia.](../../../docs/standard/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="3553d-105">The examples use concepts described in the [Events](../../../docs/standard/events/index.md) article.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3553d-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="3553d-106">Example</span></span>  
 <span data-ttu-id="3553d-107">W pierwszym przykładzie pokazano, jak podnieść i zużywać zdarzenie, które nie ma danych.</span><span class="sxs-lookup"><span data-stu-id="3553d-107">The first example shows how to raise and consume an event that doesn't have data.</span></span> <span data-ttu-id="3553d-108">Zawiera klasę o `Counter` nazwie, która `ThresholdReached`ma zdarzenie o nazwie .</span><span class="sxs-lookup"><span data-stu-id="3553d-108">It contains a class named `Counter` that has an event named `ThresholdReached`.</span></span> <span data-ttu-id="3553d-109">To zdarzenie jest wywoływane, gdy wartość licznika jest równa lub przekracza wartość progową.</span><span class="sxs-lookup"><span data-stu-id="3553d-109">This event is raised when a counter value equals or exceeds a threshold value.</span></span> <span data-ttu-id="3553d-110">Pełnomocnik <xref:System.EventHandler> jest skojarzony ze zdarzeniem, ponieważ nie podano żadnych danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="3553d-110">The <xref:System.EventHandler> delegate is associated with the event, because no event data is provided.</span></span>  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="3553d-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="3553d-111">Example</span></span>  
 <span data-ttu-id="3553d-112">W następnym przykładzie pokazano, jak podnieść i zużywać zdarzenie, które zawiera dane.</span><span class="sxs-lookup"><span data-stu-id="3553d-112">The next example shows how to raise and consume an event that provides data.</span></span> <span data-ttu-id="3553d-113">Delegat <xref:System.EventHandler%601> jest skojarzony ze zdarzeniem i podano wystąpienie niestandardowego obiektu danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="3553d-113">The <xref:System.EventHandler%601> delegate is associated with the event, and an instance of a custom event data object is provided.</span></span>  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="3553d-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="3553d-114">Example</span></span>  
 <span data-ttu-id="3553d-115">W następnym przykładzie pokazano, jak zadeklarować pełnomocnika dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="3553d-115">The next example shows how to declare a delegate for an event.</span></span> <span data-ttu-id="3553d-116">Pełnomocnik ma nazwę `ThresholdReachedEventHandler`.</span><span class="sxs-lookup"><span data-stu-id="3553d-116">The delegate is named `ThresholdReachedEventHandler`.</span></span> <span data-ttu-id="3553d-117">To tylko ilustracja.</span><span class="sxs-lookup"><span data-stu-id="3553d-117">This is just an illustration.</span></span> <span data-ttu-id="3553d-118">Zazwyczaj nie trzeba zadeklarować pełnomocnika dla zdarzenia, ponieważ można użyć <xref:System.EventHandler> lub <xref:System.EventHandler%601> pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="3553d-118">Typically, you do not have to declare a delegate for an event, because you can use either the <xref:System.EventHandler> or the <xref:System.EventHandler%601> delegate.</span></span> <span data-ttu-id="3553d-119">Pełnomocnika należy zadeklarować tylko w rzadkich scenariuszach, takich jak udostępnianie klasy starszemu kodowi, który nie może używać typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="3553d-119">You should declare a delegate only in rare scenarios, such as making your class available to legacy code that cannot use generics.</span></span>  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="3553d-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3553d-120">See also</span></span>

- [<span data-ttu-id="3553d-121">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="3553d-121">Events</span></span>](../../../docs/standard/events/index.md)
