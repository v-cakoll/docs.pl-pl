---
title: "Implementacja wzorca formantu dokowania automatyzacji interfejsu użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, dock
- dock control pattern
- UI Automation, dock control pattern
ms.assetid: ea3d2212-7c8e-4dd7-bf08-73141ca2d4fb
caps.latest.revision: "23"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 136d4ec56cf0c78aac03d1b3f44a18cd268d3bc9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a><span data-ttu-id="95a5b-102">Implementacja wzorca kontrolki dokowania automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="95a5b-102">Implementing the UI Automation Dock Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="95a5b-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="95a5b-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="95a5b-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="95a5b-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="95a5b-105">W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IDockProvider>, wraz z informacjami o właściwościach.</span><span class="sxs-lookup"><span data-stu-id="95a5b-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IDockProvider>, including information about properties.</span></span> <span data-ttu-id="95a5b-106">Łącza do dodatkowe informacje są wyświetlane na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="95a5b-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="95a5b-107"><xref:System.Windows.Automation.DockPattern> — Wzorzec formantu jest używany do udostępnienia właściwości dock formantu dokowania kontenera.</span><span class="sxs-lookup"><span data-stu-id="95a5b-107">The <xref:System.Windows.Automation.DockPattern> control pattern is used to expose the dock properties of a control within a docking container.</span></span> <span data-ttu-id="95a5b-108">Kontener dokowania jest formant, który pozwala na poziomie i w pionie, Rozmieść elementy podrzędne względem siebie.</span><span class="sxs-lookup"><span data-stu-id="95a5b-108">A docking container is a control that allows you to arrange child elements horizontally and vertically, relative to each other.</span></span> <span data-ttu-id="95a5b-109">Przykłady formantów, które implementują wzorzec tego formantu można znaleźć [formantu wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="95a5b-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
 <span data-ttu-id="95a5b-110">![Kontener dokowania z zadokowanych dwa działania podrzędne. ] (../../../docs/framework/ui-automation/media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")</span><span class="sxs-lookup"><span data-stu-id="95a5b-110">![Docking container with two docked children.](../../../docs/framework/ui-automation/media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")</span></span>  
<span data-ttu-id="95a5b-111">Dokowanie przykład z programu Visual Studio, gdy okno "Klasy widok" jest DockPosition.Right i w oknie "Lista błędów" jest DockPosition.Bottom</span><span class="sxs-lookup"><span data-stu-id="95a5b-111">Docking Example from Visual Studio Where "Class View" Window Is DockPosition.Right and "Error List" Window Is DockPosition.Bottom</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="95a5b-112">Implementacja — wskazówki i konwencje</span><span class="sxs-lookup"><span data-stu-id="95a5b-112">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="95a5b-113">Gdy implementacja wzorca formantu dokowania, należy zwrócić uwagę następujące wskazówki i konwencje:</span><span class="sxs-lookup"><span data-stu-id="95a5b-113">When implementing the Dock control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="95a5b-114"><xref:System.Windows.Automation.Provider.IDockProvider>nie ujawnia żadnych właściwości dokowania kontenera ani właściwości formantów, które są zadokowane sąsiadujące bieżącego formantu w kontenerze dokowania.</span><span class="sxs-lookup"><span data-stu-id="95a5b-114"><xref:System.Windows.Automation.Provider.IDockProvider> does not expose any properties of the docking container or any properties of controls that are docked adjacent to the current control within the docking container.</span></span>  
  
-   <span data-ttu-id="95a5b-115">Formanty są zadokowane względem siebie na podstawie ich bieżącego zamówienia z; wyższe ich kolejności umieszczania, dalej są umieszczane z określonej krawędzi dokowania kontenera.</span><span class="sxs-lookup"><span data-stu-id="95a5b-115">Controls are docked relative to each other based on their current z-order; the higher their z-order placement, the farther they are placed from the specified edge of the docking container.</span></span>  
  
-   <span data-ttu-id="95a5b-116">Jeśli rozmiaru kontenera dokowania żadnych zadokowanych formantów w kontenerze będzie można zmienić ich pozycji opróżnić do tej samej granicy, do której zostały pierwotnie zadokowane.</span><span class="sxs-lookup"><span data-stu-id="95a5b-116">If the docking container is resized, any docked controls within the container will be repositioned flush to the same edge to which they were originally docked.</span></span> <span data-ttu-id="95a5b-117">Formantów dokowanych również zmienić rozmiar do wypełnienia dowolnego miejsca w kontenerze według dokowania zachowanie ich <xref:System.Windows.Automation.DockPosition>.</span><span class="sxs-lookup"><span data-stu-id="95a5b-117">The docked controls will also resize to fill any space within the container according to the docking behavior of their <xref:System.Windows.Automation.DockPosition>.</span></span> <span data-ttu-id="95a5b-118">Na przykład jeśli <xref:System.Windows.Automation.DockPosition.Top> określono lewej i prawej stronie formantu zostanie rozwinięty w celu wypełnienia dowolnego dostępnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="95a5b-118">For example, if <xref:System.Windows.Automation.DockPosition.Top> is specified, the left and right sides of the control will expand to fill any available space.</span></span> <span data-ttu-id="95a5b-119">Jeśli <xref:System.Windows.Automation.DockPosition.Fill> jest określona, wszystkie cztery strony formantu zostanie rozwinięty w celu wypełnienia dowolnego dostępnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="95a5b-119">If <xref:System.Windows.Automation.DockPosition.Fill> is specified, all four sides of the control will expand to fill any available space.</span></span>  
  
-   <span data-ttu-id="95a5b-120">W systemie monitor wielu formantów powinien dock do lewej lub prawej strony bieżącego monitora.</span><span class="sxs-lookup"><span data-stu-id="95a5b-120">On a multi-monitor system, controls should dock to the left or right side of the current monitor.</span></span> <span data-ttu-id="95a5b-121">Jeśli nie jest to możliwe, powinny one zostało zadokowane do lewej monitora lewej lub prawej krawędzi monitor po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="95a5b-121">If that is not possible, they should dock to the left side of the leftmost monitor or the right side of the rightmost monitor.</span></span>  
  
<a name="Required_Members_for_IDockProvider"></a>   
## <a name="required-members-for-idockprovider"></a><span data-ttu-id="95a5b-122">Wymagane elementy IDockProvider</span><span class="sxs-lookup"><span data-stu-id="95a5b-122">Required Members for IDockProvider</span></span>  
 <span data-ttu-id="95a5b-123">Poniższe właściwości i metody są wymagane do implementowania interfejsu IDockProvider.</span><span class="sxs-lookup"><span data-stu-id="95a5b-123">The following properties and methods are required for implementing the IDockProvider interface.</span></span>  
  
|<span data-ttu-id="95a5b-124">Wymagane elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="95a5b-124">Required members</span></span>|<span data-ttu-id="95a5b-125">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="95a5b-125">Member type</span></span>|<span data-ttu-id="95a5b-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="95a5b-126">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider.DockPosition%2A>|<span data-ttu-id="95a5b-127">Właściwość</span><span class="sxs-lookup"><span data-stu-id="95a5b-127">Property</span></span>|<span data-ttu-id="95a5b-128">Brak</span><span class="sxs-lookup"><span data-stu-id="95a5b-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A>|<span data-ttu-id="95a5b-129">Metoda</span><span class="sxs-lookup"><span data-stu-id="95a5b-129">Method</span></span>|<span data-ttu-id="95a5b-130">Brak</span><span class="sxs-lookup"><span data-stu-id="95a5b-130">None</span></span>|  
  
 <span data-ttu-id="95a5b-131">Wzorzec ten formant nie ma żadnych zdarzeń skojarzone.</span><span class="sxs-lookup"><span data-stu-id="95a5b-131">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="95a5b-132">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="95a5b-132">Exceptions</span></span>  
 <span data-ttu-id="95a5b-133">Dostawców należy zgłosić następujące wyjątki.</span><span class="sxs-lookup"><span data-stu-id="95a5b-133">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="95a5b-134">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="95a5b-134">Exception type</span></span>|<span data-ttu-id="95a5b-135">Warunek</span><span class="sxs-lookup"><span data-stu-id="95a5b-135">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A><br /><br /> <span data-ttu-id="95a5b-136">— Gdy formantu nie jest w stanie wykonać styl dokowania żądanej.</span><span class="sxs-lookup"><span data-stu-id="95a5b-136">-   When a control is not able to execute the requested dock style.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="95a5b-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95a5b-137">See Also</span></span>  
 [<span data-ttu-id="95a5b-138">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="95a5b-138">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="95a5b-139">Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="95a5b-139">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="95a5b-140">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="95a5b-140">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="95a5b-141">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="95a5b-141">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="95a5b-142">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="95a5b-142">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
