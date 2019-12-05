---
title: Używanie buforowania w automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- caching, UI Automation
- UI Automation, caching
ms.assetid: ec722dff-6009-4279-b86a-e18d3fa94ebf
ms.openlocfilehash: 679192b611a423e095ee9acc956d247364940edf
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800794"
---
# <a name="use-caching-in-ui-automation"></a><span data-ttu-id="2a02e-102">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="2a02e-102">Use Caching in UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="2a02e-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="2a02e-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="2a02e-104">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="2a02e-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="2a02e-105">W tej sekcji pokazano, jak zaimplementować buforowanie właściwości <xref:System.Windows.Automation.AutomationElement> i wzorców kontrolek.</span><span class="sxs-lookup"><span data-stu-id="2a02e-105">This section shows how to implement caching of <xref:System.Windows.Automation.AutomationElement> properties and control patterns.</span></span>  
  
### <a name="activate-a-cache-request"></a><span data-ttu-id="2a02e-106">Aktywuj żądanie pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="2a02e-106">Activate a Cache Request</span></span>  
  
1. <span data-ttu-id="2a02e-107">Utwórz <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="2a02e-107">Create a <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="2a02e-108">Określ właściwości i wzorce do buforowania przy użyciu <xref:System.Windows.Automation.CacheRequest.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="2a02e-108">Specify properties and patterns to cache by using <xref:System.Windows.Automation.CacheRequest.Add%2A>.</span></span>  
  
3. <span data-ttu-id="2a02e-109">Określ zakres buforowania, ustawiając właściwość <xref:System.Windows.Automation.CacheRequest.TreeScope%2A>.</span><span class="sxs-lookup"><span data-stu-id="2a02e-109">Specify the scope of caching by setting the <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> property.</span></span>  
  
4. <span data-ttu-id="2a02e-110">Określ widok poddrzewa, ustawiając właściwość <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A>.</span><span class="sxs-lookup"><span data-stu-id="2a02e-110">Specify the view of the subtree by setting the <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> property.</span></span>  
  
5. <span data-ttu-id="2a02e-111">Ustaw właściwość <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> na <xref:System.Windows.Automation.AutomationElementMode.None>, jeśli chcesz zwiększyć wydajność, nie pobierając pełnych odwołań do obiektów.</span><span class="sxs-lookup"><span data-stu-id="2a02e-111">Set the <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> property to <xref:System.Windows.Automation.AutomationElementMode.None> if you wish to increase efficiency by not retrieving a full reference to objects.</span></span> <span data-ttu-id="2a02e-112">(Spowoduje to niemożliwe pobranie bieżących wartości z tych obiektów).</span><span class="sxs-lookup"><span data-stu-id="2a02e-112">(This will make it impossible to retrieve current values from those objects.)</span></span>  
  
6. <span data-ttu-id="2a02e-113">Aktywuj żądanie przy użyciu <xref:System.Windows.Automation.CacheRequest.Activate%2A> w bloku `using` (`Using` w programie Microsoft Visual Basic .NET).</span><span class="sxs-lookup"><span data-stu-id="2a02e-113">Activate the request by using <xref:System.Windows.Automation.CacheRequest.Activate%2A> within a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
 <span data-ttu-id="2a02e-114">Po uzyskaniu <xref:System.Windows.Automation.AutomationElement> obiektów lub zasubskrybowaniu zdarzeń należy dezaktywować żądanie przy użyciu <xref:System.Windows.Automation.CacheRequest.Pop%2A> (jeśli <xref:System.Windows.Automation.CacheRequest.Push%2A> była użyta) lub przez pozbywanie obiektu utworzonego przez <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span><span class="sxs-lookup"><span data-stu-id="2a02e-114">After obtaining <xref:System.Windows.Automation.AutomationElement> objects or subscribing to events, deactivate the request by using <xref:System.Windows.Automation.CacheRequest.Pop%2A> (if <xref:System.Windows.Automation.CacheRequest.Push%2A> was used) or by disposing the object created by <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span> <span data-ttu-id="2a02e-115">(Użyj <xref:System.Windows.Automation.CacheRequest.Activate%2A> w bloku `using` (`Using` w Microsoft Visual Basic .NET).</span><span class="sxs-lookup"><span data-stu-id="2a02e-115">(Use <xref:System.Windows.Automation.CacheRequest.Activate%2A> in a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
### <a name="cache-automationelement-properties"></a><span data-ttu-id="2a02e-116">Właściwości automatyzacji</span><span class="sxs-lookup"><span data-stu-id="2a02e-116">Cache AutomationElement Properties</span></span>  
  
1. <span data-ttu-id="2a02e-117">Gdy <xref:System.Windows.Automation.CacheRequest> jest aktywny, uzyskaj <xref:System.Windows.Automation.AutomationElement> obiektów przy użyciu <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> lub <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; lub uzyskaj <xref:System.Windows.Automation.AutomationElement> jako źródło zdarzenia, które zostało zarejestrowane dla momentu, gdy <xref:System.Windows.Automation.CacheRequest> był aktywny.</span><span class="sxs-lookup"><span data-stu-id="2a02e-117">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="2a02e-118">(Możesz również utworzyć pamięć podręczną, przekazując <xref:System.Windows.Automation.CacheRequest> do GetUpdatedCache lub jednej z metod <xref:System.Windows.Automation.TreeWalker>).</span><span class="sxs-lookup"><span data-stu-id="2a02e-118">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="2a02e-119">Użyj <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> lub Pobierz właściwość z właściwości <xref:System.Windows.Automation.AutomationElement.Cached%2A> <xref:System.Windows.Automation.AutomationElement>.</span><span class="sxs-lookup"><span data-stu-id="2a02e-119">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> or retrieve a property from the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property of the <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
### <a name="obtain-cached-patterns-and-their-properties"></a><span data-ttu-id="2a02e-120">Uzyskiwanie buforowanych wzorców i ich właściwości</span><span class="sxs-lookup"><span data-stu-id="2a02e-120">Obtain Cached Patterns and Their Properties</span></span>  
  
1. <span data-ttu-id="2a02e-121">Gdy <xref:System.Windows.Automation.CacheRequest> jest aktywny, uzyskaj <xref:System.Windows.Automation.AutomationElement> obiektów przy użyciu <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> lub <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; lub uzyskaj <xref:System.Windows.Automation.AutomationElement> jako źródło zdarzenia, które zostało zarejestrowane dla momentu, gdy <xref:System.Windows.Automation.CacheRequest> był aktywny.</span><span class="sxs-lookup"><span data-stu-id="2a02e-121">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="2a02e-122">(Możesz również utworzyć pamięć podręczną, przekazując <xref:System.Windows.Automation.CacheRequest> do GetUpdatedCache lub jednej z metod <xref:System.Windows.Automation.TreeWalker>).</span><span class="sxs-lookup"><span data-stu-id="2a02e-122">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="2a02e-123">Użyj <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> lub <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> do pobrania buforowanego wzorca.</span><span class="sxs-lookup"><span data-stu-id="2a02e-123">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> to retrieve a cached pattern.</span></span>  
  
3. <span data-ttu-id="2a02e-124">Pobiera wartości właściwości z właściwości `Cached` wzorca kontrolki.</span><span class="sxs-lookup"><span data-stu-id="2a02e-124">Retrieve property values from the `Cached` property of the control pattern.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a02e-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="2a02e-125">Example</span></span>  
 <span data-ttu-id="2a02e-126">Poniższy przykład kodu przedstawia różne aspekty buforowania przy użyciu <xref:System.Windows.Automation.CacheRequest.Activate%2A> do uaktywnienia <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="2a02e-126">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Activate%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a><span data-ttu-id="2a02e-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="2a02e-127">Example</span></span>  
 <span data-ttu-id="2a02e-128">Poniższy przykład kodu przedstawia różne aspekty buforowania przy użyciu <xref:System.Windows.Automation.CacheRequest.Push%2A> do uaktywnienia <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="2a02e-128">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Push%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span> <span data-ttu-id="2a02e-129">W przypadku zamiaru zagnieżdżenia żądań pamięci podręcznej warto używać <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span><span class="sxs-lookup"><span data-stu-id="2a02e-129">Except when you wish to nest cache requests, it is preferable to use <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a><span data-ttu-id="2a02e-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a02e-130">See also</span></span>

- [<span data-ttu-id="2a02e-131">Buforowanie w klientach automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="2a02e-131">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
