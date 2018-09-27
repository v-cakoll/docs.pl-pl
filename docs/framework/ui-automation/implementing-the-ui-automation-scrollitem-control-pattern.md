---
title: Implementacja wzorca formantu ScrollItem dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 4c3dfc6eb42fef0c3464b49f7513425038d9091b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2018
ms.locfileid: "47400676"
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a><span data-ttu-id="fb53c-102">Implementacja wzorca kontrolki ScrollItem dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="fb53c-102">Implementing the UI Automation ScrollItem Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="fb53c-103">Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="fb53c-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="fb53c-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="fb53c-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="fb53c-105">W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IScrollItemProvider>, wraz z informacjami dotyczącymi właściwości, metody i zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="fb53c-105">This topic introduces guidelines and conventions for implementing the <xref:System.Windows.Automation.Provider.IScrollItemProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="fb53c-106">Łącza do dodatkowe informacje są wyświetlane na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="fb53c-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="fb53c-107"><xref:System.Windows.Automation.ScrollItemPattern> — Wzorzec kontrolki jest używana do obsługi formantów podrzędnych poszczególnych kontenerów, które implementują <xref:System.Windows.Automation.Provider.IScrollProvider>.</span><span class="sxs-lookup"><span data-stu-id="fb53c-107">The <xref:System.Windows.Automation.ScrollItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IScrollProvider>.</span></span> <span data-ttu-id="fb53c-108">Ten wzorzec kontroli działa jako kanał komunikacyjny między kontrolki podrzędnej i jego kontener, aby upewnić się czy kontenera można zmienić zawartość aktualnie widoczne (lub regionie) w ramach jego okienka ekranu, aby wyświetlić kontrolki podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="fb53c-108">This control pattern acts as a communication channel between a child control and its container to ensure that the container can change the currently visible content (or region) within its viewport to display the child control.</span></span> <span data-ttu-id="fb53c-109">Przykłady formantów, które implementują wzorzec tej kontrolki, zobacz [kontroli wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="fb53c-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="fb53c-110">Wytyczne dotyczące implementacji i konwencje</span><span class="sxs-lookup"><span data-stu-id="fb53c-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="fb53c-111">Jeśli implementacja wzorca kontrolki przewijania elementu, należy zwrócić uwagę następujących wytycznych i konwencje:</span><span class="sxs-lookup"><span data-stu-id="fb53c-111">When implementing the Scroll Item control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="fb53c-112">Elementy zawarte w formancie okna lub obszaru roboczego nie są wymagane do zaimplementowania interfejsu IScrollItemProvider.</span><span class="sxs-lookup"><span data-stu-id="fb53c-112">Items contained within a Window or Canvas control are not required to implement the IScrollItemProvider interface.</span></span> <span data-ttu-id="fb53c-113">Jako alternatywę, jednak należy eksponowanie prawidłową lokalizację <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.</span><span class="sxs-lookup"><span data-stu-id="fb53c-113">As an alternative, however, they must expose a valid location for the <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.</span></span> <span data-ttu-id="fb53c-114">Pozwoli to aplikacji klienckiej automatyzacji interfejsu użytkownika użyć <xref:System.Windows.Automation.ScrollPattern> kontrolować metody wzorca w kontenerze, aby wyświetlić element podrzędny.</span><span class="sxs-lookup"><span data-stu-id="fb53c-114">This will allow a UI Automation client application to use the <xref:System.Windows.Automation.ScrollPattern> control pattern methods on the container to display the child item.</span></span>  
  
<a name="Required_Members_for_IScrollItemProvider"></a>   
## <a name="required-members-for-iscrollitemprovider"></a><span data-ttu-id="fb53c-115">Wymagane elementy IScrollItemProvider</span><span class="sxs-lookup"><span data-stu-id="fb53c-115">Required Members for IScrollItemProvider</span></span>  
 <span data-ttu-id="fb53c-116">Poniższa metoda jest wymagany dla implementującej interfejs IScrollProvider.</span><span class="sxs-lookup"><span data-stu-id="fb53c-116">The following method is required for implementing the IScrollProvider interface.</span></span>  
  
|<span data-ttu-id="fb53c-117">Wymagane elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="fb53c-117">Required members</span></span>|<span data-ttu-id="fb53c-118">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="fb53c-118">Member type</span></span>|<span data-ttu-id="fb53c-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fb53c-119">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|<span data-ttu-id="fb53c-120">— Metoda</span><span class="sxs-lookup"><span data-stu-id="fb53c-120">-   Method</span></span>|<span data-ttu-id="fb53c-121">Brak</span><span class="sxs-lookup"><span data-stu-id="fb53c-121">None</span></span>|  
  
 <span data-ttu-id="fb53c-122">Ten wzorzec kontrolka nie ma skojarzonych z nimi właściwości lub zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="fb53c-122">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="fb53c-123">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="fb53c-123">Exceptions</span></span>  
 <span data-ttu-id="fb53c-124">Dostawcy należy zgłaszać następujące wyjątki.</span><span class="sxs-lookup"><span data-stu-id="fb53c-124">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="fb53c-125">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="fb53c-125">Exception Type</span></span>|<span data-ttu-id="fb53c-126">Warunek</span><span class="sxs-lookup"><span data-stu-id="fb53c-126">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<span data-ttu-id="fb53c-127">Jeśli element nie może być przewijane w widoku:</span><span class="sxs-lookup"><span data-stu-id="fb53c-127">If an item cannot be scrolled into view:</span></span><br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="fb53c-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fb53c-128">See Also</span></span>  
 [<span data-ttu-id="fb53c-129">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="fb53c-129">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="fb53c-130">Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="fb53c-130">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="fb53c-131">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="fb53c-131">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="fb53c-132">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="fb53c-132">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="fb53c-133">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="fb53c-133">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
