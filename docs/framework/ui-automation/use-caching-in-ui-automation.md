---
title: Używanie buforowania w automatyzacji interfejsu użytkownika
description: Zobacz jak używać buforowania w automatyzacji interfejsu użytkownika. Zapoznaj się z instrukcjami dotyczącymi aktywacji żądania pamięci podręcznej, buforowania właściwości AutomationElement i uzyskiwania buforowanych wzorców.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- caching, UI Automation
- UI Automation, caching
ms.assetid: ec722dff-6009-4279-b86a-e18d3fa94ebf
ms.openlocfilehash: 8dff9db77e39dc66a16b6a7b395c76a3c768d48e
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924490"
---
# <a name="use-caching-in-ui-automation"></a><span data-ttu-id="bc2da-104">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="bc2da-104">Use Caching in UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="bc2da-105">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="bc2da-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="bc2da-106">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="bc2da-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="bc2da-107">W tej sekcji pokazano, jak zaimplementować buforowanie <xref:System.Windows.Automation.AutomationElement> właściwości i wzorców kontrolek.</span><span class="sxs-lookup"><span data-stu-id="bc2da-107">This section shows how to implement caching of <xref:System.Windows.Automation.AutomationElement> properties and control patterns.</span></span>  
  
### <a name="activate-a-cache-request"></a><span data-ttu-id="bc2da-108">Aktywuj żądanie pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="bc2da-108">Activate a Cache Request</span></span>  
  
1. <span data-ttu-id="bc2da-109">Utwórz <xref:System.Windows.Automation.CacheRequest> .</span><span class="sxs-lookup"><span data-stu-id="bc2da-109">Create a <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="bc2da-110">Określ właściwości i wzorce do buforowania przy użyciu programu <xref:System.Windows.Automation.CacheRequest.Add%2A> .</span><span class="sxs-lookup"><span data-stu-id="bc2da-110">Specify properties and patterns to cache by using <xref:System.Windows.Automation.CacheRequest.Add%2A>.</span></span>  
  
3. <span data-ttu-id="bc2da-111">Określ zakres buforowania przez ustawienie <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="bc2da-111">Specify the scope of caching by setting the <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> property.</span></span>  
  
4. <span data-ttu-id="bc2da-112">Określ widok poddrzewa przez ustawienie <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="bc2da-112">Specify the view of the subtree by setting the <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> property.</span></span>  
  
5. <span data-ttu-id="bc2da-113">Ustaw <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> Właściwość na, <xref:System.Windows.Automation.AutomationElementMode.None> Jeśli chcesz zwiększyć wydajność, nie pobierając pełnych odwołań do obiektów.</span><span class="sxs-lookup"><span data-stu-id="bc2da-113">Set the <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> property to <xref:System.Windows.Automation.AutomationElementMode.None> if you wish to increase efficiency by not retrieving a full reference to objects.</span></span> <span data-ttu-id="bc2da-114">(Spowoduje to niemożliwe pobranie bieżących wartości z tych obiektów).</span><span class="sxs-lookup"><span data-stu-id="bc2da-114">(This will make it impossible to retrieve current values from those objects.)</span></span>  
  
6. <span data-ttu-id="bc2da-115">Aktywuj żądanie przy użyciu <xref:System.Windows.Automation.CacheRequest.Activate%2A> `using` bloku ( `Using` w programie Microsoft Visual Basic .NET).</span><span class="sxs-lookup"><span data-stu-id="bc2da-115">Activate the request by using <xref:System.Windows.Automation.CacheRequest.Activate%2A> within a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
 <span data-ttu-id="bc2da-116">Po uzyskaniu <xref:System.Windows.Automation.AutomationElement> obiektów lub zasubskrybowaniu zdarzeń, Dezaktywuj żądanie przy użyciu <xref:System.Windows.Automation.CacheRequest.Pop%2A> (Jeśli <xref:System.Windows.Automation.CacheRequest.Push%2A> zostało użyte) lub przez odtworzenie obiektu utworzonego przez <xref:System.Windows.Automation.CacheRequest.Activate%2A> .</span><span class="sxs-lookup"><span data-stu-id="bc2da-116">After obtaining <xref:System.Windows.Automation.AutomationElement> objects or subscribing to events, deactivate the request by using <xref:System.Windows.Automation.CacheRequest.Pop%2A> (if <xref:System.Windows.Automation.CacheRequest.Push%2A> was used) or by disposing the object created by <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span> <span data-ttu-id="bc2da-117">(Użyj <xref:System.Windows.Automation.CacheRequest.Activate%2A> w `using` bloku ( `Using` w programie Microsoft Visual Basic .NET).</span><span class="sxs-lookup"><span data-stu-id="bc2da-117">(Use <xref:System.Windows.Automation.CacheRequest.Activate%2A> in a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
### <a name="cache-automationelement-properties"></a><span data-ttu-id="bc2da-118">Właściwości automatyzacji</span><span class="sxs-lookup"><span data-stu-id="bc2da-118">Cache AutomationElement Properties</span></span>  
  
1. <span data-ttu-id="bc2da-119">Gdy <xref:System.Windows.Automation.CacheRequest> jest aktywny, należy uzyskać <xref:System.Windows.Automation.AutomationElement> obiekty za pomocą <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> lub <xref:System.Windows.Automation.AutomationElement.FindAll%2A> ; albo uzyskać <xref:System.Windows.Automation.AutomationElement> jako źródło zdarzenia, które zostało zarejestrowane, gdy <xref:System.Windows.Automation.CacheRequest> był aktywny.</span><span class="sxs-lookup"><span data-stu-id="bc2da-119">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="bc2da-120">(Możesz również utworzyć pamięć podręczną, przechodząc <xref:System.Windows.Automation.CacheRequest> do GetUpdatedCache lub jednej z <xref:System.Windows.Automation.TreeWalker> metod).</span><span class="sxs-lookup"><span data-stu-id="bc2da-120">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="bc2da-121">Użyj <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> lub Pobierz właściwość z <xref:System.Windows.Automation.AutomationElement.Cached%2A> właściwości <xref:System.Windows.Automation.AutomationElement> .</span><span class="sxs-lookup"><span data-stu-id="bc2da-121">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> or retrieve a property from the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property of the <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
### <a name="obtain-cached-patterns-and-their-properties"></a><span data-ttu-id="bc2da-122">Uzyskiwanie buforowanych wzorców i ich właściwości</span><span class="sxs-lookup"><span data-stu-id="bc2da-122">Obtain Cached Patterns and Their Properties</span></span>  
  
1. <span data-ttu-id="bc2da-123">Gdy <xref:System.Windows.Automation.CacheRequest> jest aktywny, należy uzyskać <xref:System.Windows.Automation.AutomationElement> obiekty za pomocą <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> lub <xref:System.Windows.Automation.AutomationElement.FindAll%2A> ; albo uzyskać <xref:System.Windows.Automation.AutomationElement> jako źródło zdarzenia, które zostało zarejestrowane, gdy <xref:System.Windows.Automation.CacheRequest> był aktywny.</span><span class="sxs-lookup"><span data-stu-id="bc2da-123">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="bc2da-124">(Możesz również utworzyć pamięć podręczną, przechodząc <xref:System.Windows.Automation.CacheRequest> do GetUpdatedCache lub jednej z <xref:System.Windows.Automation.TreeWalker> metod).</span><span class="sxs-lookup"><span data-stu-id="bc2da-124">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="bc2da-125">Użyj <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> lub, <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> Aby pobrać buforowany wzorzec.</span><span class="sxs-lookup"><span data-stu-id="bc2da-125">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> to retrieve a cached pattern.</span></span>  
  
3. <span data-ttu-id="bc2da-126">Pobiera wartości właściwości z `Cached` właściwości wzorca kontrolki.</span><span class="sxs-lookup"><span data-stu-id="bc2da-126">Retrieve property values from the `Cached` property of the control pattern.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc2da-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="bc2da-127">Example</span></span>  
 <span data-ttu-id="bc2da-128">Poniższy przykład kodu przedstawia różne aspekty buforowania przy użyciu narzędzia <xref:System.Windows.Automation.CacheRequest.Activate%2A> do aktywacji <xref:System.Windows.Automation.CacheRequest> .</span><span class="sxs-lookup"><span data-stu-id="bc2da-128">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Activate%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a><span data-ttu-id="bc2da-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="bc2da-129">Example</span></span>  
 <span data-ttu-id="bc2da-130">Poniższy przykład kodu przedstawia różne aspekty buforowania przy użyciu narzędzia <xref:System.Windows.Automation.CacheRequest.Push%2A> do aktywacji <xref:System.Windows.Automation.CacheRequest> .</span><span class="sxs-lookup"><span data-stu-id="bc2da-130">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Push%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span> <span data-ttu-id="bc2da-131">W przypadku zamiaru zagnieżdżenia żądań pamięci podręcznej najlepiej jest używać <xref:System.Windows.Automation.CacheRequest.Activate%2A> .</span><span class="sxs-lookup"><span data-stu-id="bc2da-131">Except when you wish to nest cache requests, it is preferable to use <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a><span data-ttu-id="bc2da-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc2da-132">See also</span></span>

- [<span data-ttu-id="bc2da-133">Buforowanie w klientach automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="bc2da-133">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
