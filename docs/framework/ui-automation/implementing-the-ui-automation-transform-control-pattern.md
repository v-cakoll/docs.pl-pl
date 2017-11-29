---
title: "Implementacja wzorca formantu przekształcania automatyzacji interfejsu użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Transform
- Transform control pattern
- UI Automation, Transform control pattern
ms.assetid: 5f49d843-5845-4800-9d9c-56ce0d146844
caps.latest.revision: "14"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: df871c7f7214a6135db2493972dd76f41ce31aaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-transform-control-pattern"></a><span data-ttu-id="4b057-102">Implementacja wzorca kontrolki przekształcania automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="4b057-102">Implementing the UI Automation Transform Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="4b057-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4b057-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="4b057-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="4b057-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="4b057-105">W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.ITransformProvider>, wraz z informacjami dotyczącymi właściwości, metod i zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4b057-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITransformProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="4b057-106">Łącza do dodatkowe informacje są wyświetlane na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="4b057-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="4b057-107"><xref:System.Windows.Automation.TransformPattern> — Wzorzec formantu jest używana do obsługi formantów, które można przenieść, rozmiaru lub obracać dwuwymiarowa miejsce.</span><span class="sxs-lookup"><span data-stu-id="4b057-107">The <xref:System.Windows.Automation.TransformPattern> control pattern is used to support controls that can be moved, resized, or rotated within a two-dimensional space.</span></span> <span data-ttu-id="4b057-108">Przykłady formantów, które implementują wzorzec tego formantu można znaleźć [formantu wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="4b057-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="4b057-109">Implementacja — wskazówki i konwencje</span><span class="sxs-lookup"><span data-stu-id="4b057-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="4b057-110">Gdy implementacja wzorca kontrolki przekształcania, należy zwrócić uwagę następujące wskazówki i konwencje:</span><span class="sxs-lookup"><span data-stu-id="4b057-110">When implementing the Transform control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="4b057-111">Obsługa tego wzorca formantu nie jest ograniczona do obiektów na pulpicie.</span><span class="sxs-lookup"><span data-stu-id="4b057-111">Support for this control pattern is not limited to objects on the desktop.</span></span> <span data-ttu-id="4b057-112">Ten wzorzec formantu również musi obsługiwane przez element podrzędny obiektu kontenera, gdy elementy podrzędne można przenieść, zmiany rozmiaru lub obracać za darmo w granicach kontenera.</span><span class="sxs-lookup"><span data-stu-id="4b057-112">This control pattern must also be supported by the children of a container object if the children can be moved, resized, or rotated freely within the boundaries of the container.</span></span>  
  
-   <span data-ttu-id="4b057-113">Obiekt nie można przenosić, zmiany rozmiaru ani obracać lokalizacji ekranu wynikowy będzie można całkowicie poza współrzędne swojego kontenera i w związku z tym niedostępne do klawiatury lub myszy (na przykład w przypadku, gdy okno najwyższego poziomu zostanie przesunięty ekranem lub a obiekt podrzędny zostanie przeniesiona poza granice tego kontenera okienka ekranu).</span><span class="sxs-lookup"><span data-stu-id="4b057-113">An object cannot be moved, resized, or rotated such that its resulting screen location would be completely outside the coordinates of its container and therefore inaccessible to the keyboard or mouse (for example, when a top-level window is moved off-screen or a child object is moved outside the boundaries of the container's viewport).</span></span> <span data-ttu-id="4b057-114">W takich przypadkach obiekt znajduje się maksymalnie zbliżony współrzędne ekranu żądanego możliwie z góry lub lewej współrzędne zastąpiona w granicach kontenera.</span><span class="sxs-lookup"><span data-stu-id="4b057-114">In these cases, the object is placed as close to the requested screen coordinates as possible with the top or left coordinates overridden to be within the container boundaries.</span></span>  
  
-   <span data-ttu-id="4b057-115">Monitor wielu systemów Jeśli obiekt jest przenoszony, po zmianie rozmiaru lub obrócony całkowicie poza współrzędne ekranu pulpitu połączonych obiektu jest umieszczona na podstawowy monitor maksymalnie zbliżony żądanego współrzędne, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="4b057-115">For multi-monitor systems, if an object is moved, resized, or rotated completely outside the combined desktop screen coordinates, the object is placed on the primary monitor as close to the requested coordinates as possible.</span></span>  
  
-   <span data-ttu-id="4b057-116">Wszystkie parametry i wartości właściwości są niezależne od ustawień regionalnych i bezwzględne.</span><span class="sxs-lookup"><span data-stu-id="4b057-116">All parameters and property values are absolute and independent of locale.</span></span>  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-itransformprovider"></a><span data-ttu-id="4b057-117">Wymagane elementy ITransformProvider</span><span class="sxs-lookup"><span data-stu-id="4b057-117">Required Members for ITransformProvider</span></span>  
 <span data-ttu-id="4b057-118">Poniższe właściwości i metody są wymagane do wykonania <xref:System.Windows.Automation.Provider.ITransformProvider>.</span><span class="sxs-lookup"><span data-stu-id="4b057-118">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.ITransformProvider>.</span></span>  
  
|<span data-ttu-id="4b057-119">Wymagane elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="4b057-119">Required members</span></span>|<span data-ttu-id="4b057-120">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="4b057-120">Member type</span></span>|<span data-ttu-id="4b057-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4b057-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanMove%2A>|<span data-ttu-id="4b057-122">Właściwość</span><span class="sxs-lookup"><span data-stu-id="4b057-122">Property</span></span>|<span data-ttu-id="4b057-123">Brak</span><span class="sxs-lookup"><span data-stu-id="4b057-123">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanResize%2A>|<span data-ttu-id="4b057-124">Właściwość</span><span class="sxs-lookup"><span data-stu-id="4b057-124">Property</span></span>|<span data-ttu-id="4b057-125">Brak</span><span class="sxs-lookup"><span data-stu-id="4b057-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanRotate%2A>|<span data-ttu-id="4b057-126">Właściwość</span><span class="sxs-lookup"><span data-stu-id="4b057-126">Property</span></span>|<span data-ttu-id="4b057-127">Brak</span><span class="sxs-lookup"><span data-stu-id="4b057-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A>|<span data-ttu-id="4b057-128">Metoda</span><span class="sxs-lookup"><span data-stu-id="4b057-128">Method</span></span>|<span data-ttu-id="4b057-129">Brak</span><span class="sxs-lookup"><span data-stu-id="4b057-129">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A>|<span data-ttu-id="4b057-130">Metoda</span><span class="sxs-lookup"><span data-stu-id="4b057-130">Method</span></span>|<span data-ttu-id="4b057-131">Brak</span><span class="sxs-lookup"><span data-stu-id="4b057-131">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A>|<span data-ttu-id="4b057-132">Metoda</span><span class="sxs-lookup"><span data-stu-id="4b057-132">Method</span></span>|<span data-ttu-id="4b057-133">Brak</span><span class="sxs-lookup"><span data-stu-id="4b057-133">None</span></span>|  
  
 <span data-ttu-id="4b057-134">Wzorzec ten formant nie ma żadnych zdarzeń skojarzone.</span><span class="sxs-lookup"><span data-stu-id="4b057-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="4b057-135">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="4b057-135">Exceptions</span></span>  
 <span data-ttu-id="4b057-136">Dostawców należy zgłosić następujące wyjątki.</span><span class="sxs-lookup"><span data-stu-id="4b057-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="4b057-137">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="4b057-137">Exception Type</span></span>|<span data-ttu-id="4b057-138">Warunek</span><span class="sxs-lookup"><span data-stu-id="4b057-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A><br /><br /> <span data-ttu-id="4b057-139">-Jeśli <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> ma wartość false.</span><span class="sxs-lookup"><span data-stu-id="4b057-139">-   If the <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> is false.</span></span>|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A><br /><br /> <span data-ttu-id="4b057-140">-Jeśli <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> ma wartość false.</span><span class="sxs-lookup"><span data-stu-id="4b057-140">-   If the <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> is false.</span></span>|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A><br /><br /> <span data-ttu-id="4b057-141">-Jeśli <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> ma wartość false.</span><span class="sxs-lookup"><span data-stu-id="4b057-141">-   If the <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> is false.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4b057-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4b057-142">See Also</span></span>  
 [<span data-ttu-id="4b057-143">Przegląd wzorców formantu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="4b057-143">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="4b057-144">Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="4b057-144">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="4b057-145">Wzorce formantów automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="4b057-145">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="4b057-146">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="4b057-146">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="4b057-147">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="4b057-147">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
