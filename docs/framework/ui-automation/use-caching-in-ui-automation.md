---
title: Używanie buforowania w automatyzacji interfejsu użytkownika
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- caching, UI Automation
- UI Automation, caching
ms.assetid: ec722dff-6009-4279-b86a-e18d3fa94ebf
caps.latest.revision: 14
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 2f559153190e4acb3b67acf75954260b31906c0d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="use-caching-in-ui-automation"></a><span data-ttu-id="9ea0d-102">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="9ea0d-102">Use Caching in UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="9ea0d-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9ea0d-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="9ea0d-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="9ea0d-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="9ea0d-105">W tej sekcji przedstawiono sposób wykonania buforowanie <xref:System.Windows.Automation.AutomationElement> wzorce właściwości i kontroli.</span><span class="sxs-lookup"><span data-stu-id="9ea0d-105">This section shows how to implement caching of <xref:System.Windows.Automation.AutomationElement> properties and control patterns.</span></span>  
  
### <a name="activate-a-cache-request"></a><span data-ttu-id="9ea0d-106">Aktywuj żądania pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="9ea0d-106">Activate a Cache Request</span></span>  
  
1.  <span data-ttu-id="9ea0d-107">Utwórz <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="9ea0d-107">Create a <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2.  <span data-ttu-id="9ea0d-108">Określ właściwości i wzorce do pamięci podręcznej przy użyciu <xref:System.Windows.Automation.CacheRequest.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="9ea0d-108">Specify properties and patterns to cache by using <xref:System.Windows.Automation.CacheRequest.Add%2A>.</span></span>  
  
3.  <span data-ttu-id="9ea0d-109">Określ zakres buforowania przez ustawienie <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="9ea0d-109">Specify the scope of caching by setting the <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> property.</span></span>  
  
4.  <span data-ttu-id="9ea0d-110">Określ widok poddrzewo, ustawiając <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="9ea0d-110">Specify the view of the subtree by setting the <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> property.</span></span>  
  
5.  <span data-ttu-id="9ea0d-111">Ustaw <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> właściwości <xref:System.Windows.Automation.AutomationElementMode.None> Jeśli chcesz zwiększyć wydajność nie przywracając pełną odwołania do obiektów.</span><span class="sxs-lookup"><span data-stu-id="9ea0d-111">Set the <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> property to <xref:System.Windows.Automation.AutomationElementMode.None> if you wish to increase efficiency by not retrieving a full reference to objects.</span></span> <span data-ttu-id="9ea0d-112">(Będzie go można pobrać bieżących wartości z tych obiektów.)</span><span class="sxs-lookup"><span data-stu-id="9ea0d-112">(This will make it impossible to retrieve current values from those objects.)</span></span>  
  
6.  <span data-ttu-id="9ea0d-113">Aktywuj żądania przy użyciu <xref:System.Windows.Automation.CacheRequest.Activate%2A> w `using` bloku (`Using` w programie Microsoft Visual Basic .NET).</span><span class="sxs-lookup"><span data-stu-id="9ea0d-113">Activate the request by using <xref:System.Windows.Automation.CacheRequest.Activate%2A> within a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
 <span data-ttu-id="9ea0d-114">Po uzyskaniu <xref:System.Windows.Automation.AutomationElement> obiektów lub subskrybowanie zdarzeń, Dezaktywuj żądania przy użyciu <xref:System.Windows.Automation.CacheRequest.Pop%2A> (Jeśli <xref:System.Windows.Automation.CacheRequest.Push%2A> użyto) lub usuwanie obiektu utworzonego przez <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span><span class="sxs-lookup"><span data-stu-id="9ea0d-114">After obtaining <xref:System.Windows.Automation.AutomationElement> objects or subscribing to events, deactivate the request by using <xref:System.Windows.Automation.CacheRequest.Pop%2A> (if <xref:System.Windows.Automation.CacheRequest.Push%2A> was used) or by disposing the object created by <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span> <span data-ttu-id="9ea0d-115">(Użyj <xref:System.Windows.Automation.CacheRequest.Activate%2A> w `using` bloku (`Using` w programie Microsoft Visual Basic .NET).</span><span class="sxs-lookup"><span data-stu-id="9ea0d-115">(Use <xref:System.Windows.Automation.CacheRequest.Activate%2A> in a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
### <a name="cache-automationelement-properties"></a><span data-ttu-id="9ea0d-116">Właściwości Obiekt AutomationElement pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="9ea0d-116">Cache AutomationElement Properties</span></span>  
  
1.  <span data-ttu-id="9ea0d-117">Gdy <xref:System.Windows.Automation.CacheRequest> jest aktywny, uzyskać <xref:System.Windows.Automation.AutomationElement> obiektów przy użyciu <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> lub <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; lub uzyskać <xref:System.Windows.Automation.AutomationElement> jako źródło zdarzenia, który został zarejestrowany program <xref:System.Windows.Automation.CacheRequest> był aktywny.</span><span class="sxs-lookup"><span data-stu-id="9ea0d-117">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="9ea0d-118">(Można również utworzyć pamięci podręcznej przez przekazanie <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache lub jedną z <xref:System.Windows.Automation.TreeWalker> metody.)</span><span class="sxs-lookup"><span data-stu-id="9ea0d-118">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2.  <span data-ttu-id="9ea0d-119">Użyj <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> lub pobrać właściwości z <xref:System.Windows.Automation.AutomationElement.Cached%2A> właściwość <xref:System.Windows.Automation.AutomationElement>.</span><span class="sxs-lookup"><span data-stu-id="9ea0d-119">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> or retrieve a property from the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property of the <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
### <a name="obtain-cached-patterns-and-their-properties"></a><span data-ttu-id="9ea0d-120">Uzyskaj wzorce pamięci podręcznej i ich właściwości</span><span class="sxs-lookup"><span data-stu-id="9ea0d-120">Obtain Cached Patterns and Their Properties</span></span>  
  
1.  <span data-ttu-id="9ea0d-121">Gdy <xref:System.Windows.Automation.CacheRequest> jest aktywny, uzyskać <xref:System.Windows.Automation.AutomationElement> obiektów przy użyciu <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> lub <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; lub uzyskać <xref:System.Windows.Automation.AutomationElement> jako źródło zdarzenia, który został zarejestrowany program <xref:System.Windows.Automation.CacheRequest> był aktywny.</span><span class="sxs-lookup"><span data-stu-id="9ea0d-121">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="9ea0d-122">(Można również utworzyć pamięci podręcznej przez przekazanie <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache lub jedną z <xref:System.Windows.Automation.TreeWalker> metody.)</span><span class="sxs-lookup"><span data-stu-id="9ea0d-122">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2.  <span data-ttu-id="9ea0d-123">Użyj <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> lub <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> można pobrać wzorzec pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="9ea0d-123">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> to retrieve a cached pattern.</span></span>  
  
3.  <span data-ttu-id="9ea0d-124">Pobiera się wartości właściwości z `Cached` właściwości wzorca formantu.</span><span class="sxs-lookup"><span data-stu-id="9ea0d-124">Retrieve property values from the `Cached` property of the control pattern.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ea0d-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="9ea0d-125">Example</span></span>  
 <span data-ttu-id="9ea0d-126">Poniższy przykładowy kod przedstawia różne aspekty buforowania, za pomocą <xref:System.Windows.Automation.CacheRequest.Activate%2A> aktywować <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="9ea0d-126">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Activate%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a><span data-ttu-id="9ea0d-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="9ea0d-127">Example</span></span>  
 <span data-ttu-id="9ea0d-128">Poniższy przykładowy kod przedstawia różne aspekty buforowania, za pomocą <xref:System.Windows.Automation.CacheRequest.Push%2A> aktywować <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="9ea0d-128">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Push%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span> <span data-ttu-id="9ea0d-129">Z wyjątkiem, gdy chcesz zagnieździć żądań pamięci podręcznej, zaleca się używania <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span><span class="sxs-lookup"><span data-stu-id="9ea0d-129">Except when you wish to nest cache requests, it is preferable to use <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a><span data-ttu-id="9ea0d-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9ea0d-130">See Also</span></span>  
 [<span data-ttu-id="9ea0d-131">Buforowanie w klientach automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="9ea0d-131">Caching in UI Automation Clients</span></span>](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
