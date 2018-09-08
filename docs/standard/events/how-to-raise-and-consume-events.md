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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa933e0fc589d0dbfec741e9db7fb11222cfdf38
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44193227"
---
# <a name="how-to-raise-and-consume-events"></a><span data-ttu-id="cfea7-102">Porady: wywoływanie zdarzeń i korzystanie z nich</span><span class="sxs-lookup"><span data-stu-id="cfea7-102">How to: Raise and Consume Events</span></span>
<span data-ttu-id="cfea7-103">Przykłady w tym temacie pokazują sposób pracy ze zdarzeniami.</span><span class="sxs-lookup"><span data-stu-id="cfea7-103">The examples in this topic show how to work with events.</span></span> <span data-ttu-id="cfea7-104">Obejmują one przykłady <xref:System.EventHandler> delegować, <xref:System.EventHandler%601> delegatów oraz niestandardową klasę delegatów, aby zilustrować wydarzenia z i bez danych.</span><span class="sxs-lookup"><span data-stu-id="cfea7-104">They include examples of the <xref:System.EventHandler> delegate, the <xref:System.EventHandler%601> delegate, and a custom delegate, to illustrate events with and without data.</span></span>  
  
 <span data-ttu-id="cfea7-105">W przykładach wykorzystano Koncepcje opisane w [zdarzenia](../../../docs/standard/events/index.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="cfea7-105">The examples use concepts described in the [Events](../../../docs/standard/events/index.md) article.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfea7-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="cfea7-106">Example</span></span>  
 <span data-ttu-id="cfea7-107">Pierwszy przykład pokazuje jak podnieść i zużyć zdarzenie, które nie zawiera danych.</span><span class="sxs-lookup"><span data-stu-id="cfea7-107">The first example shows how to raise and consume an event that doesn't have data.</span></span> <span data-ttu-id="cfea7-108">Zawiera klasę o nazwie `Counter` która posiada zdarzenie o nazwie `ThresholdReached`.</span><span class="sxs-lookup"><span data-stu-id="cfea7-108">It contains a class named `Counter` that has an event named `ThresholdReached`.</span></span> <span data-ttu-id="cfea7-109">To zdarzenie jest wywoływane, gdy wartość licznika jest równa lub przekracza wartość progową.</span><span class="sxs-lookup"><span data-stu-id="cfea7-109">This event is raised when a counter value equals or exceeds a threshold value.</span></span> <span data-ttu-id="cfea7-110"><xref:System.EventHandler> Delegat jest skojarzony ze zdarzeniem, ponieważ podano żadnych dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cfea7-110">The <xref:System.EventHandler> delegate is associated with the event, because no event data is provided.</span></span>  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="cfea7-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="cfea7-111">Example</span></span>  
 <span data-ttu-id="cfea7-112">Następny przykład pokazuje jak podnieść i zużyć zdarzenie, które zawierają dane.</span><span class="sxs-lookup"><span data-stu-id="cfea7-112">The next example shows how to raise and consume an event that provides data.</span></span> <span data-ttu-id="cfea7-113"><xref:System.EventHandler%601> Delegat jest skojarzony ze zdarzeniem i znajduje się wystąpienie obiektu danych zdarzenia niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="cfea7-113">The <xref:System.EventHandler%601> delegate is associated with the event, and an instance of a custom event data object is provided.</span></span>  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="cfea7-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="cfea7-114">Example</span></span>  
 <span data-ttu-id="cfea7-115">Następny przykład pokazuje, jak zadeklarować obiektu delegowany dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cfea7-115">The next example shows how to declare a delegate for an event.</span></span> <span data-ttu-id="cfea7-116">Pełnomocnik ma nazwę `ThresholdReachedEventHandler`.</span><span class="sxs-lookup"><span data-stu-id="cfea7-116">The delegate is named `ThresholdReachedEventHandler`.</span></span> <span data-ttu-id="cfea7-117">Jest to po prostu ilustracja.</span><span class="sxs-lookup"><span data-stu-id="cfea7-117">This is just an illustration.</span></span> <span data-ttu-id="cfea7-118">Zazwyczaj trzeba zadeklarować obiektu delegowany dla zdarzenia, ponieważ można użyć <xref:System.EventHandler> lub <xref:System.EventHandler%601> delegować.</span><span class="sxs-lookup"><span data-stu-id="cfea7-118">Typically, you do not have to declare a delegate for an event, because you can use either the <xref:System.EventHandler> or the <xref:System.EventHandler%601> delegate.</span></span> <span data-ttu-id="cfea7-119">Należy zadeklarować delegata tylko w rzadkich scenariuszach, takich jak staje się dostępny dla starszego kodu, który nie może używać elementów Generic swojej klasy.</span><span class="sxs-lookup"><span data-stu-id="cfea7-119">You should declare a delegate only in rare scenarios, such as making your class available to legacy code that cannot use generics.</span></span>  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="cfea7-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cfea7-120">See also</span></span>

- [<span data-ttu-id="cfea7-121">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cfea7-121">Events</span></span>](../../../docs/standard/events/index.md)
