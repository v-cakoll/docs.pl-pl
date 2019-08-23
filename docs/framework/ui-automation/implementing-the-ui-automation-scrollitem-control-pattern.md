---
title: Implementacja wzorca kontrolki ScrollItem dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
ms.openlocfilehash: 4883184d75a21efbc08947008baddf31346d7951
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935753"
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a><span data-ttu-id="3bddd-102">Implementacja wzorca kontrolki ScrollItem dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="3bddd-102">Implementing the UI Automation ScrollItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="3bddd-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3bddd-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="3bddd-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3bddd-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="3bddd-105">W tym temacie przedstawiono wytyczne i konwencje dotyczące <xref:System.Windows.Automation.Provider.IScrollItemProvider>wdrażania, w tym informacje o właściwościach, metodach i zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="3bddd-105">This topic introduces guidelines and conventions for implementing the <xref:System.Windows.Automation.Provider.IScrollItemProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="3bddd-106">Linki do dodatkowych odwołań znajdują się na końcu tematu.</span><span class="sxs-lookup"><span data-stu-id="3bddd-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="3bddd-107">Wzorzec kontrolki służy do obsługi poszczególnych kontrolek podrzędnych kontenerów, które implementują <xref:System.Windows.Automation.Provider.IScrollProvider>. <xref:System.Windows.Automation.ScrollItemPattern></span><span class="sxs-lookup"><span data-stu-id="3bddd-107">The <xref:System.Windows.Automation.ScrollItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IScrollProvider>.</span></span> <span data-ttu-id="3bddd-108">Ten wzorzec kontroli działa jako kanał komunikacyjny między kontrolką podrzędną a jej kontenerem, aby upewnić się, że kontener może zmienić aktualnie widoczną zawartość (lub region) w okienku ekranu, aby wyświetlić formant podrzędny.</span><span class="sxs-lookup"><span data-stu-id="3bddd-108">This control pattern acts as a communication channel between a child control and its container to ensure that the container can change the currently visible content (or region) within its viewport to display the child control.</span></span> <span data-ttu-id="3bddd-109">Aby zapoznać się z przykładami formantów implementujących ten wzorzec kontrolek, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="3bddd-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="3bddd-110">Wytyczne i konwencje dotyczące implementacji</span><span class="sxs-lookup"><span data-stu-id="3bddd-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="3bddd-111">Podczas implementowania wzorca kontrolki elementu Scroll należy zwrócić uwagę na następujące wytyczne i konwencje:</span><span class="sxs-lookup"><span data-stu-id="3bddd-111">When implementing the Scroll Item control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="3bddd-112">Elementy zawarte w kontrolce okna lub kanwy nie są wymagane do zaimplementowania interfejsu IScrollItemProvider.</span><span class="sxs-lookup"><span data-stu-id="3bddd-112">Items contained within a Window or Canvas control are not required to implement the IScrollItemProvider interface.</span></span> <span data-ttu-id="3bddd-113">Alternatywnie jednak muszą uwidocznić prawidłową lokalizację dla <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.</span><span class="sxs-lookup"><span data-stu-id="3bddd-113">As an alternative, however, they must expose a valid location for the <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.</span></span> <span data-ttu-id="3bddd-114">Umożliwi to aplikacji klienta automatyzacji interfejsu użytkownika użycie <xref:System.Windows.Automation.ScrollPattern> metod wzorca kontroli w kontenerze w celu wyświetlenia elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="3bddd-114">This will allow a UI Automation client application to use the <xref:System.Windows.Automation.ScrollPattern> control pattern methods on the container to display the child item.</span></span>  
  
<a name="Required_Members_for_IScrollItemProvider"></a>   
## <a name="required-members-for-iscrollitemprovider"></a><span data-ttu-id="3bddd-115">Wymagane elementy członkowskie dla IScrollItemProvider</span><span class="sxs-lookup"><span data-stu-id="3bddd-115">Required Members for IScrollItemProvider</span></span>  
 <span data-ttu-id="3bddd-116">Następująca metoda jest wymagana do zaimplementowania interfejsu IScrollProvider.</span><span class="sxs-lookup"><span data-stu-id="3bddd-116">The following method is required for implementing the IScrollProvider interface.</span></span>  
  
|<span data-ttu-id="3bddd-117">Wymagane elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3bddd-117">Required members</span></span>|<span data-ttu-id="3bddd-118">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="3bddd-118">Member type</span></span>|<span data-ttu-id="3bddd-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3bddd-119">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|<span data-ttu-id="3bddd-120">-Metoda</span><span class="sxs-lookup"><span data-stu-id="3bddd-120">-   Method</span></span>|<span data-ttu-id="3bddd-121">Brak</span><span class="sxs-lookup"><span data-stu-id="3bddd-121">None</span></span>|  
  
 <span data-ttu-id="3bddd-122">Ten wzorzec kontrolki nie ma skojarzonych właściwości ani zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="3bddd-122">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="3bddd-123">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="3bddd-123">Exceptions</span></span>  
 <span data-ttu-id="3bddd-124">Dostawcy muszą zgłosić następujące wyjątki.</span><span class="sxs-lookup"><span data-stu-id="3bddd-124">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="3bddd-125">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="3bddd-125">Exception Type</span></span>|<span data-ttu-id="3bddd-126">Warunek</span><span class="sxs-lookup"><span data-stu-id="3bddd-126">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<span data-ttu-id="3bddd-127">Jeśli elementu nie można przewijać do widoku:</span><span class="sxs-lookup"><span data-stu-id="3bddd-127">If an item cannot be scrolled into view:</span></span><br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="3bddd-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3bddd-128">See also</span></span>

- [<span data-ttu-id="3bddd-129">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="3bddd-129">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="3bddd-130">Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="3bddd-130">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="3bddd-131">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="3bddd-131">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="3bddd-132">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="3bddd-132">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="3bddd-133">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="3bddd-133">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
