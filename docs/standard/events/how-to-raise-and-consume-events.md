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
ms.openlocfilehash: 4d0b24b8a6f1b914745d819b90b973752e32447c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279961"
---
# <a name="how-to-raise-and-consume-events"></a><span data-ttu-id="9f951-102">Porady: wywoływanie zdarzeń i korzystanie z nich</span><span class="sxs-lookup"><span data-stu-id="9f951-102">How to: Raise and Consume Events</span></span>
<span data-ttu-id="9f951-103">Przykłady w tym temacie przedstawiają sposób pracy ze zdarzeniami.</span><span class="sxs-lookup"><span data-stu-id="9f951-103">The examples in this topic show how to work with events.</span></span> <span data-ttu-id="9f951-104">Obejmują one przykłady <xref:System.EventHandler> delegata, <xref:System.EventHandler%601> delegata i delegata niestandardowego, które ilustrują zdarzenia z i bez danych.</span><span class="sxs-lookup"><span data-stu-id="9f951-104">They include examples of the <xref:System.EventHandler> delegate, the <xref:System.EventHandler%601> delegate, and a custom delegate, to illustrate events with and without data.</span></span>  
  
 <span data-ttu-id="9f951-105">Przykłady wykorzystują Koncepcje opisane w artykule [zdarzenia](index.md) .</span><span class="sxs-lookup"><span data-stu-id="9f951-105">The examples use concepts described in the [Events](index.md) article.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f951-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="9f951-106">Example</span></span>  
 <span data-ttu-id="9f951-107">Pierwszy przykład pokazuje, jak podnieść i zużyć zdarzenie, które nie ma danych.</span><span class="sxs-lookup"><span data-stu-id="9f951-107">The first example shows how to raise and consume an event that doesn't have data.</span></span> <span data-ttu-id="9f951-108">Zawiera klasę o nazwie `Counter` , która ma zdarzenie o nazwie `ThresholdReached` .</span><span class="sxs-lookup"><span data-stu-id="9f951-108">It contains a class named `Counter` that has an event named `ThresholdReached`.</span></span> <span data-ttu-id="9f951-109">To zdarzenie jest zgłaszane, gdy wartość licznika jest równa lub przekracza wartość progową.</span><span class="sxs-lookup"><span data-stu-id="9f951-109">This event is raised when a counter value equals or exceeds a threshold value.</span></span> <span data-ttu-id="9f951-110"><xref:System.EventHandler>Delegat jest skojarzony ze zdarzeniem, ponieważ nie podano danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="9f951-110">The <xref:System.EventHandler> delegate is associated with the event, because no event data is provided.</span></span>  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="9f951-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="9f951-111">Example</span></span>  
 <span data-ttu-id="9f951-112">W następnym przykładzie pokazano, jak podnieść i zużyć zdarzenie, które dostarcza dane.</span><span class="sxs-lookup"><span data-stu-id="9f951-112">The next example shows how to raise and consume an event that provides data.</span></span> <span data-ttu-id="9f951-113"><xref:System.EventHandler%601>Delegat jest skojarzony ze zdarzeniem, a wystąpienie obiektu danych zdarzenia niestandardowego jest dostarczone.</span><span class="sxs-lookup"><span data-stu-id="9f951-113">The <xref:System.EventHandler%601> delegate is associated with the event, and an instance of a custom event data object is provided.</span></span>  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="9f951-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="9f951-114">Example</span></span>  
 <span data-ttu-id="9f951-115">W następnym przykładzie pokazano, jak zadeklarować delegata dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="9f951-115">The next example shows how to declare a delegate for an event.</span></span> <span data-ttu-id="9f951-116">Delegat ma nazwę `ThresholdReachedEventHandler` .</span><span class="sxs-lookup"><span data-stu-id="9f951-116">The delegate is named `ThresholdReachedEventHandler`.</span></span> <span data-ttu-id="9f951-117">Jest to tylko ilustracja.</span><span class="sxs-lookup"><span data-stu-id="9f951-117">This is just an illustration.</span></span> <span data-ttu-id="9f951-118">Zazwyczaj nie trzeba deklarować delegatów dla zdarzenia, ponieważ można użyć albo <xref:System.EventHandler> <xref:System.EventHandler%601> delegata.</span><span class="sxs-lookup"><span data-stu-id="9f951-118">Typically, you do not have to declare a delegate for an event, because you can use either the <xref:System.EventHandler> or the <xref:System.EventHandler%601> delegate.</span></span> <span data-ttu-id="9f951-119">Delegata należy zadeklarować tylko w rzadkich scenariuszach, takich jak udostępnienie klasy dla starszego kodu, który nie może używać typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="9f951-119">You should declare a delegate only in rare scenarios, such as making your class available to legacy code that cannot use generics.</span></span>  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="9f951-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9f951-120">See also</span></span>

- [<span data-ttu-id="9f951-121">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="9f951-121">Events</span></span>](index.md)
