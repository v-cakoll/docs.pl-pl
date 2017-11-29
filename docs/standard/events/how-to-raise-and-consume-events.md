---
title: "Porady: wywoływanie zdarzeń i korzystanie z nich"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], raising
- raising events
- events [.NET Framework], samples
ms.assetid: 42afade7-3a02-4f2e-868b-95845f302f8f
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d052c865a554977ce5c8b0a347337d9d9b92fc57
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-raise-and-consume-events"></a><span data-ttu-id="5ff3b-102">Porady: wywoływanie zdarzeń i korzystanie z nich</span><span class="sxs-lookup"><span data-stu-id="5ff3b-102">How to: Raise and Consume Events</span></span>
<span data-ttu-id="5ff3b-103">Przykłady w tym temacie przedstawiają sposób pracy ze zdarzeniami.</span><span class="sxs-lookup"><span data-stu-id="5ff3b-103">The examples in this topic show how to work with events.</span></span> <span data-ttu-id="5ff3b-104">Obejmują one przykłady <xref:System.EventHandler> delegować, <xref:System.EventHandler%601> delegata i niestandardowych delegata, aby zilustrować zdarzenia z włączonymi i wyłączonymi danych.</span><span class="sxs-lookup"><span data-stu-id="5ff3b-104">They include examples of the <xref:System.EventHandler> delegate, the <xref:System.EventHandler%601> delegate, and a custom delegate, to illustrate events with and without data.</span></span>  
  
 <span data-ttu-id="5ff3b-105">W przykładach użyto pojęcia opisane w [zdarzenia](../../../docs/standard/events/index.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="5ff3b-105">The examples use concepts described in the [Events](../../../docs/standard/events/index.md) article.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ff3b-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="5ff3b-106">Example</span></span>  
 <span data-ttu-id="5ff3b-107">W pierwszym przykładzie przedstawiono sposób pozyskiwania i zużywać zdarzenie, które nie ma danych.</span><span class="sxs-lookup"><span data-stu-id="5ff3b-107">The first example shows how to raise and consume an event that doesn't have data.</span></span> <span data-ttu-id="5ff3b-108">Zawiera klasy o nazwie `Counter` ma zdarzenia o nazwie `ThresholdReached`.</span><span class="sxs-lookup"><span data-stu-id="5ff3b-108">It contains a class named `Counter` that has an event named `ThresholdReached`.</span></span> <span data-ttu-id="5ff3b-109">To zdarzenie jest wywoływane, gdy wartość licznika jest równa lub większa niż wartość progu.</span><span class="sxs-lookup"><span data-stu-id="5ff3b-109">This event is raised when a counter value equals or exceeds a threshold value.</span></span> <span data-ttu-id="5ff3b-110"><xref:System.EventHandler> Delegat jest skojarzone ze zdarzeniem, ponieważ nie jest podany żadnych danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="5ff3b-110">The <xref:System.EventHandler> delegate is associated with the event, because no event data is provided.</span></span>  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="5ff3b-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="5ff3b-111">Example</span></span>  
 <span data-ttu-id="5ff3b-112">Kolejnym przykładzie pokazano, jak pozyskiwania i zużywać zdarzenie, które zawierają dane.</span><span class="sxs-lookup"><span data-stu-id="5ff3b-112">The next example shows how to raise and consume an event that provides data.</span></span> <span data-ttu-id="5ff3b-113"><xref:System.EventHandler%601> Delegat jest skojarzone ze zdarzeniem oraz podano wystąpienia obiektu danych niestandardowych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5ff3b-113">The <xref:System.EventHandler%601> delegate is associated with the event, and an instance of a custom event data object is provided.</span></span>  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="5ff3b-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="5ff3b-114">Example</span></span>  
 <span data-ttu-id="5ff3b-115">Kolejnym przykładzie pokazano, jak można zadeklarować obiektu delegowanego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="5ff3b-115">The next example shows how to declare a delegate for an event.</span></span> <span data-ttu-id="5ff3b-116">Delegat nosi nazwę `ThresholdReachedEventHandler`.</span><span class="sxs-lookup"><span data-stu-id="5ff3b-116">The delegate is named `ThresholdReachedEventHandler`.</span></span> <span data-ttu-id="5ff3b-117">Jest to po prostu zapoznać się z ilustracją.</span><span class="sxs-lookup"><span data-stu-id="5ff3b-117">This is just an illustration.</span></span> <span data-ttu-id="5ff3b-118">Zazwyczaj nie trzeba zadeklarować delegata zdarzenia, ponieważ można użyć <xref:System.EventHandler> lub <xref:System.EventHandler%601> delegowanie.</span><span class="sxs-lookup"><span data-stu-id="5ff3b-118">Typically, you do not have to declare a delegate for an event, because you can use either the <xref:System.EventHandler> or the <xref:System.EventHandler%601> delegate.</span></span> <span data-ttu-id="5ff3b-119">Powinien deklarować delegata tylko w rzadkich scenariusze, takie jak udostępnianie klasy starszego kodu, który nie można używać typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="5ff3b-119">You should declare a delegate only in rare scenarios, such as making your class available to legacy code that cannot use generics.</span></span>  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="5ff3b-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5ff3b-120">See Also</span></span>  
 [<span data-ttu-id="5ff3b-121">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="5ff3b-121">Events</span></span>](../../../docs/standard/events/index.md)
