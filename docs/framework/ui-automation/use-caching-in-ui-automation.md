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
ms.openlocfilehash: dd7506d388ba215f671ee3c7c4bae09baf4cc2b3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71040309"
---
# <a name="use-caching-in-ui-automation"></a><span data-ttu-id="f255e-102">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="f255e-102">Use Caching in UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="f255e-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f255e-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f255e-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f255e-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="f255e-105">W tej sekcji pokazano, jak zaimplementować buforowanie <xref:System.Windows.Automation.AutomationElement> właściwości i wzorców kontrolek.</span><span class="sxs-lookup"><span data-stu-id="f255e-105">This section shows how to implement caching of <xref:System.Windows.Automation.AutomationElement> properties and control patterns.</span></span>  
  
### <a name="activate-a-cache-request"></a><span data-ttu-id="f255e-106">Aktywuj żądanie pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="f255e-106">Activate a Cache Request</span></span>  
  
1. <span data-ttu-id="f255e-107">Utwórz <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="f255e-107">Create a <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="f255e-108">Określ właściwości i wzorce do buforowania przy użyciu <xref:System.Windows.Automation.CacheRequest.Add%2A>programu.</span><span class="sxs-lookup"><span data-stu-id="f255e-108">Specify properties and patterns to cache by using <xref:System.Windows.Automation.CacheRequest.Add%2A>.</span></span>  
  
3. <span data-ttu-id="f255e-109">Określ zakres buforowania przez ustawienie <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f255e-109">Specify the scope of caching by setting the <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> property.</span></span>  
  
4. <span data-ttu-id="f255e-110">Określ widok poddrzewa przez ustawienie <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f255e-110">Specify the view of the subtree by setting the <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> property.</span></span>  
  
5. <span data-ttu-id="f255e-111">Ustaw właściwość na <xref:System.Windows.Automation.AutomationElementMode.None> , jeśli chcesz zwiększyć wydajność, nie pobierając pełnych odwołań do obiektów. <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A></span><span class="sxs-lookup"><span data-stu-id="f255e-111">Set the <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> property to <xref:System.Windows.Automation.AutomationElementMode.None> if you wish to increase efficiency by not retrieving a full reference to objects.</span></span> <span data-ttu-id="f255e-112">(Spowoduje to niemożliwe pobranie bieżących wartości z tych obiektów).</span><span class="sxs-lookup"><span data-stu-id="f255e-112">(This will make it impossible to retrieve current values from those objects.)</span></span>  
  
6. <span data-ttu-id="f255e-113">Aktywuj żądanie przy użyciu <xref:System.Windows.Automation.CacheRequest.Activate%2A> `using` bloku (`Using` w programie Microsoft Visual Basic .NET).</span><span class="sxs-lookup"><span data-stu-id="f255e-113">Activate the request by using <xref:System.Windows.Automation.CacheRequest.Activate%2A> within a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
 <span data-ttu-id="f255e-114">Po uzyskaniu <xref:System.Windows.Automation.AutomationElement> obiektów lub zasubskrybowaniu zdarzeń, Dezaktywuj żądanie przy <xref:System.Windows.Automation.CacheRequest.Pop%2A> użyciu ( <xref:System.Windows.Automation.CacheRequest.Push%2A> jeśli zostało użyte) lub przez odtworzenie obiektu utworzonego <xref:System.Windows.Automation.CacheRequest.Activate%2A>przez.</span><span class="sxs-lookup"><span data-stu-id="f255e-114">After obtaining <xref:System.Windows.Automation.AutomationElement> objects or subscribing to events, deactivate the request by using <xref:System.Windows.Automation.CacheRequest.Pop%2A> (if <xref:System.Windows.Automation.CacheRequest.Push%2A> was used) or by disposing the object created by <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span> <span data-ttu-id="f255e-115">(Użyj <xref:System.Windows.Automation.CacheRequest.Activate%2A> `using` w bloku (`Using` w programie Microsoft Visual Basic .NET).</span><span class="sxs-lookup"><span data-stu-id="f255e-115">(Use <xref:System.Windows.Automation.CacheRequest.Activate%2A> in a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
### <a name="cache-automationelement-properties"></a><span data-ttu-id="f255e-116">Właściwości automatyzacji</span><span class="sxs-lookup"><span data-stu-id="f255e-116">Cache AutomationElement Properties</span></span>  
  
1. <span data-ttu-id="f255e-117"><xref:System.Windows.Automation.AutomationElement.FindAll%2A> <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> <xref:System.Windows.Automation.CacheRequest> Gdy jest aktywny, należy uzyskać <xref:System.Windows.Automation.AutomationElement> obiekty za pomocą lub; albo uzyskać <xref:System.Windows.Automation.AutomationElement> jako źródło zdarzenia, które zostało zarejestrowane, gdy był aktywny. <xref:System.Windows.Automation.CacheRequest></span><span class="sxs-lookup"><span data-stu-id="f255e-117">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="f255e-118">(Możesz również utworzyć pamięć podręczną, przechodząc <xref:System.Windows.Automation.CacheRequest> do GetUpdatedCache lub jednej <xref:System.Windows.Automation.TreeWalker> z metod).</span><span class="sxs-lookup"><span data-stu-id="f255e-118">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="f255e-119">Użyj <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> lub Pobierz Właściwość <xref:System.Windows.Automation.AutomationElement.Cached%2A> z właściwości <xref:System.Windows.Automation.AutomationElement>.</span><span class="sxs-lookup"><span data-stu-id="f255e-119">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> or retrieve a property from the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property of the <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
### <a name="obtain-cached-patterns-and-their-properties"></a><span data-ttu-id="f255e-120">Uzyskiwanie buforowanych wzorców i ich właściwości</span><span class="sxs-lookup"><span data-stu-id="f255e-120">Obtain Cached Patterns and Their Properties</span></span>  
  
1. <span data-ttu-id="f255e-121"><xref:System.Windows.Automation.AutomationElement.FindAll%2A> <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> <xref:System.Windows.Automation.CacheRequest> Gdy jest aktywny, należy uzyskać <xref:System.Windows.Automation.AutomationElement> obiekty za pomocą lub; albo uzyskać <xref:System.Windows.Automation.AutomationElement> jako źródło zdarzenia, które zostało zarejestrowane, gdy był aktywny. <xref:System.Windows.Automation.CacheRequest></span><span class="sxs-lookup"><span data-stu-id="f255e-121">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="f255e-122">(Możesz również utworzyć pamięć podręczną, przechodząc <xref:System.Windows.Automation.CacheRequest> do GetUpdatedCache lub jednej <xref:System.Windows.Automation.TreeWalker> z metod).</span><span class="sxs-lookup"><span data-stu-id="f255e-122">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="f255e-123">Użyj <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> lub<xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> , aby pobrać buforowany wzorzec.</span><span class="sxs-lookup"><span data-stu-id="f255e-123">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> to retrieve a cached pattern.</span></span>  
  
3. <span data-ttu-id="f255e-124">Pobiera wartości właściwości z `Cached` właściwości wzorca kontrolki.</span><span class="sxs-lookup"><span data-stu-id="f255e-124">Retrieve property values from the `Cached` property of the control pattern.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f255e-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="f255e-125">Example</span></span>  
 <span data-ttu-id="f255e-126">Poniższy przykład kodu przedstawia różne aspekty buforowania przy użyciu narzędzia <xref:System.Windows.Automation.CacheRequest.Activate%2A> do <xref:System.Windows.Automation.CacheRequest>aktywacji.</span><span class="sxs-lookup"><span data-stu-id="f255e-126">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Activate%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a><span data-ttu-id="f255e-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="f255e-127">Example</span></span>  
 <span data-ttu-id="f255e-128">Poniższy przykład kodu przedstawia różne aspekty buforowania przy użyciu narzędzia <xref:System.Windows.Automation.CacheRequest.Push%2A> do <xref:System.Windows.Automation.CacheRequest>aktywacji.</span><span class="sxs-lookup"><span data-stu-id="f255e-128">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Push%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span> <span data-ttu-id="f255e-129">W przypadku zamiaru zagnieżdżenia żądań pamięci podręcznej najlepiej jest używać <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span><span class="sxs-lookup"><span data-stu-id="f255e-129">Except when you wish to nest cache requests, it is preferable to use <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a><span data-ttu-id="f255e-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f255e-130">See also</span></span>

- [<span data-ttu-id="f255e-131">Buforowanie w klientach automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="f255e-131">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
