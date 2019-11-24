---
title: Implementacja wzorca kontrolki ScrollItem dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
ms.openlocfilehash: 1e33a64e66bc084e8cc5f75ece2ac2a4d7ea85aa
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447140"
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a><span data-ttu-id="0e98d-102">Implementacja wzorca kontrolki ScrollItem dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="0e98d-102">Implementing the UI Automation ScrollItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="0e98d-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span><span class="sxs-lookup"><span data-stu-id="0e98d-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="0e98d-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="0e98d-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="0e98d-105">This topic introduces guidelines and conventions for implementing the <xref:System.Windows.Automation.Provider.IScrollItemProvider>, including information about properties, methods, and events.</span><span class="sxs-lookup"><span data-stu-id="0e98d-105">This topic introduces guidelines and conventions for implementing the <xref:System.Windows.Automation.Provider.IScrollItemProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="0e98d-106">Links to additional references are listed at the end of the topic.</span><span class="sxs-lookup"><span data-stu-id="0e98d-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="0e98d-107">The <xref:System.Windows.Automation.ScrollItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IScrollProvider>.</span><span class="sxs-lookup"><span data-stu-id="0e98d-107">The <xref:System.Windows.Automation.ScrollItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IScrollProvider>.</span></span> <span data-ttu-id="0e98d-108">This control pattern acts as a communication channel between a child control and its container to ensure that the container can change the currently visible content (or region) within its viewport to display the child control.</span><span class="sxs-lookup"><span data-stu-id="0e98d-108">This control pattern acts as a communication channel between a child control and its container to ensure that the container can change the currently visible content (or region) within its viewport to display the child control.</span></span> <span data-ttu-id="0e98d-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="0e98d-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="0e98d-110">Implementation Guidelines and Conventions</span><span class="sxs-lookup"><span data-stu-id="0e98d-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="0e98d-111">When implementing the Scroll Item control pattern, note the following guidelines and conventions:</span><span class="sxs-lookup"><span data-stu-id="0e98d-111">When implementing the Scroll Item control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="0e98d-112">Items contained within a Window or Canvas control are not required to implement the IScrollItemProvider interface.</span><span class="sxs-lookup"><span data-stu-id="0e98d-112">Items contained within a Window or Canvas control are not required to implement the IScrollItemProvider interface.</span></span> <span data-ttu-id="0e98d-113">As an alternative, however, they must expose a valid location for the <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.</span><span class="sxs-lookup"><span data-stu-id="0e98d-113">As an alternative, however, they must expose a valid location for the <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.</span></span> <span data-ttu-id="0e98d-114">This will allow a UI Automation client application to use the <xref:System.Windows.Automation.ScrollPattern> control pattern methods on the container to display the child item.</span><span class="sxs-lookup"><span data-stu-id="0e98d-114">This will allow a UI Automation client application to use the <xref:System.Windows.Automation.ScrollPattern> control pattern methods on the container to display the child item.</span></span>  
  
<a name="Required_Members_for_IScrollItemProvider"></a>   
## <a name="required-members-for-iscrollitemprovider"></a><span data-ttu-id="0e98d-115">Required Members for IScrollItemProvider</span><span class="sxs-lookup"><span data-stu-id="0e98d-115">Required Members for IScrollItemProvider</span></span>  
 <span data-ttu-id="0e98d-116">The following method is required for implementing the IScrollProvider interface.</span><span class="sxs-lookup"><span data-stu-id="0e98d-116">The following method is required for implementing the IScrollProvider interface.</span></span>  
  
|<span data-ttu-id="0e98d-117">Required members</span><span class="sxs-lookup"><span data-stu-id="0e98d-117">Required members</span></span>|<span data-ttu-id="0e98d-118">Member type</span><span class="sxs-lookup"><span data-stu-id="0e98d-118">Member type</span></span>|<span data-ttu-id="0e98d-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0e98d-119">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|<span data-ttu-id="0e98d-120">-   Method</span><span class="sxs-lookup"><span data-stu-id="0e98d-120">-   Method</span></span>|<span data-ttu-id="0e98d-121">Brak</span><span class="sxs-lookup"><span data-stu-id="0e98d-121">None</span></span>|  
  
 <span data-ttu-id="0e98d-122">This control pattern has no associated properties or events.</span><span class="sxs-lookup"><span data-stu-id="0e98d-122">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="0e98d-123">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="0e98d-123">Exceptions</span></span>  
 <span data-ttu-id="0e98d-124">Providers must throw the following exceptions.</span><span class="sxs-lookup"><span data-stu-id="0e98d-124">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="0e98d-125">Exception Type</span><span class="sxs-lookup"><span data-stu-id="0e98d-125">Exception Type</span></span>|<span data-ttu-id="0e98d-126">Warunek</span><span class="sxs-lookup"><span data-stu-id="0e98d-126">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<span data-ttu-id="0e98d-127">If an item cannot be scrolled into view:</span><span class="sxs-lookup"><span data-stu-id="0e98d-127">If an item cannot be scrolled into view:</span></span><br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="0e98d-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0e98d-128">See also</span></span>

- [<span data-ttu-id="0e98d-129">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="0e98d-129">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="0e98d-130">Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="0e98d-130">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="0e98d-131">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="0e98d-131">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="0e98d-132">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="0e98d-132">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="0e98d-133">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="0e98d-133">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
