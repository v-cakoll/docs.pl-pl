---
title: Implementacja wzorca kontrolki ScrollItem dla automatyzacji interfejsu użytkownika
description: Zapoznaj się z wytycznymi i konwencjami dotyczącymi wdrażania wzorca kontroli ScrollItem dla w automatyzacji interfejsu użytkownika. Zobacz wymagane elementy członkowskie dla interfejsu IScrollItemProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
ms.openlocfilehash: a548eb25280d9a8feddc4633a1ba3e7dc022af36
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163570"
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a><span data-ttu-id="009b9-104">Implementacja wzorca kontrolki ScrollItem dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="009b9-104">Implementing the UI Automation ScrollItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="009b9-105">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="009b9-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="009b9-106">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="009b9-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="009b9-107">W tym temacie przedstawiono wytyczne i konwencje dotyczące wdrażania <xref:System.Windows.Automation.Provider.IScrollItemProvider> , w tym informacje o właściwościach, metodach i zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="009b9-107">This topic introduces guidelines and conventions for implementing the <xref:System.Windows.Automation.Provider.IScrollItemProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="009b9-108">Linki do dodatkowych odwołań znajdują się na końcu tematu.</span><span class="sxs-lookup"><span data-stu-id="009b9-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="009b9-109"><xref:System.Windows.Automation.ScrollItemPattern>Wzorzec kontrolki służy do obsługi poszczególnych kontrolek podrzędnych kontenerów, które implementują <xref:System.Windows.Automation.Provider.IScrollProvider> .</span><span class="sxs-lookup"><span data-stu-id="009b9-109">The <xref:System.Windows.Automation.ScrollItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IScrollProvider>.</span></span> <span data-ttu-id="009b9-110">Ten wzorzec kontroli działa jako kanał komunikacyjny między kontrolką podrzędną a jej kontenerem, aby upewnić się, że kontener może zmienić aktualnie widoczną zawartość (lub region) w okienku ekranu, aby wyświetlić formant podrzędny.</span><span class="sxs-lookup"><span data-stu-id="009b9-110">This control pattern acts as a communication channel between a child control and its container to ensure that the container can change the currently visible content (or region) within its viewport to display the child control.</span></span> <span data-ttu-id="009b9-111">Aby zapoznać się z przykładami formantów implementujących ten wzorzec kontrolek, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="009b9-111">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="009b9-112">Wytyczne i konwencje dotyczące implementacji</span><span class="sxs-lookup"><span data-stu-id="009b9-112">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="009b9-113">Podczas implementowania wzorca kontrolki elementu Scroll należy zwrócić uwagę na następujące wytyczne i konwencje:</span><span class="sxs-lookup"><span data-stu-id="009b9-113">When implementing the Scroll Item control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="009b9-114">Elementy zawarte w kontrolce okna lub kanwy nie są wymagane do zaimplementowania interfejsu IScrollItemProvider.</span><span class="sxs-lookup"><span data-stu-id="009b9-114">Items contained within a Window or Canvas control are not required to implement the IScrollItemProvider interface.</span></span> <span data-ttu-id="009b9-115">Alternatywnie jednak muszą uwidocznić prawidłową lokalizację dla <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> .</span><span class="sxs-lookup"><span data-stu-id="009b9-115">As an alternative, however, they must expose a valid location for the <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.</span></span> <span data-ttu-id="009b9-116">Umożliwi to aplikacji klienta automatyzacji interfejsu użytkownika użycie <xref:System.Windows.Automation.ScrollPattern> metod wzorca kontroli w kontenerze w celu wyświetlenia elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="009b9-116">This will allow a UI Automation client application to use the <xref:System.Windows.Automation.ScrollPattern> control pattern methods on the container to display the child item.</span></span>  
  
<a name="Required_Members_for_IScrollItemProvider"></a>
## <a name="required-members-for-iscrollitemprovider"></a><span data-ttu-id="009b9-117">Wymagane elementy członkowskie dla IScrollItemProvider</span><span class="sxs-lookup"><span data-stu-id="009b9-117">Required Members for IScrollItemProvider</span></span>  
 <span data-ttu-id="009b9-118">Następująca metoda jest wymagana do zaimplementowania interfejsu IScrollProvider.</span><span class="sxs-lookup"><span data-stu-id="009b9-118">The following method is required for implementing the IScrollProvider interface.</span></span>  
  
|<span data-ttu-id="009b9-119">Wymagane elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="009b9-119">Required members</span></span>|<span data-ttu-id="009b9-120">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="009b9-120">Member type</span></span>|<span data-ttu-id="009b9-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="009b9-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|<span data-ttu-id="009b9-122">-Metoda</span><span class="sxs-lookup"><span data-stu-id="009b9-122">-   Method</span></span>|<span data-ttu-id="009b9-123">Brak</span><span class="sxs-lookup"><span data-stu-id="009b9-123">None</span></span>|  
  
 <span data-ttu-id="009b9-124">Ten wzorzec kontrolki nie ma skojarzonych właściwości ani zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="009b9-124">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="009b9-125">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="009b9-125">Exceptions</span></span>  
 <span data-ttu-id="009b9-126">Dostawcy muszą zgłosić następujące wyjątki.</span><span class="sxs-lookup"><span data-stu-id="009b9-126">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="009b9-127">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="009b9-127">Exception Type</span></span>|<span data-ttu-id="009b9-128">Warunek</span><span class="sxs-lookup"><span data-stu-id="009b9-128">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<span data-ttu-id="009b9-129">Jeśli elementu nie można przewijać do widoku:</span><span class="sxs-lookup"><span data-stu-id="009b9-129">If an item cannot be scrolled into view:</span></span><br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="009b9-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="009b9-130">See also</span></span>

- [<span data-ttu-id="009b9-131">Wzorce formantów automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="009b9-131">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="009b9-132">Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="009b9-132">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="009b9-133">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="009b9-133">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="009b9-134">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="009b9-134">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="009b9-135">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="009b9-135">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
