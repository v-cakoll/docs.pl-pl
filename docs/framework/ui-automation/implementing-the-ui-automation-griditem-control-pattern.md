---
title: "Implementacja wzorca formantu GridItem dla automatyzacji interfejsu użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
caps.latest.revision: "15"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: daaffd02eaaf7fcb0e64dbcda4bd2ee155163f4f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="74a37-102">Implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="74a37-102">Implementing the UI Automation GridItem Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="74a37-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="74a37-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="74a37-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="74a37-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="74a37-105">W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IGridItemProvider>, wraz z informacjami o właściwościach.</span><span class="sxs-lookup"><span data-stu-id="74a37-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="74a37-106">Łącza do dodatkowe informacje są wyświetlane na końcu przeglądu.</span><span class="sxs-lookup"><span data-stu-id="74a37-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="74a37-107"><xref:System.Windows.Automation.GridItemPattern> — Wzorzec formantu jest używana do obsługi formantów podrzędnych poszczególnych kontenerów, które implementują <xref:System.Windows.Automation.Provider.IGridProvider>.</span><span class="sxs-lookup"><span data-stu-id="74a37-107">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="74a37-108">Przykłady formantów, które implementują wzorzec tego formantu można znaleźć [formantu wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="74a37-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="74a37-109">Implementacja — wskazówki i konwencje</span><span class="sxs-lookup"><span data-stu-id="74a37-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="74a37-110">Podczas implementowania <xref:System.Windows.Automation.Provider.IGridProvider>, należy zwrócić uwagę następujące wskazówki i konwencje:</span><span class="sxs-lookup"><span data-stu-id="74a37-110">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="74a37-111">Współrzędne siatki jest liczony od zera górna lewa komórka o współrzędne (0, 0).</span><span class="sxs-lookup"><span data-stu-id="74a37-111">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
-   <span data-ttu-id="74a37-112">Scalone komórki będzie zgłaszać ich <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> i <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> właściwości na podstawie ich podstawowej zakotwiczenia komórki zgodnie z definicją w dostawcy automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="74a37-112">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="74a37-113">Zazwyczaj będzie najwyższego poziomu i lewej strony wierszy lub kolumn.</span><span class="sxs-lookup"><span data-stu-id="74a37-113">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
-   <span data-ttu-id="74a37-114"><xref:System.Windows.Automation.Provider.IGridItemProvider>przewidują active manipulowania siatki, takie jak scalanie lub dzielenie komórek.</span><span class="sxs-lookup"><span data-stu-id="74a37-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
-   <span data-ttu-id="74a37-115">Określa, które implementują <xref:System.Windows.Automation.Provider.IGridItemProvider> zwykle można przekształcić (klient automatyzacji interfejsu użytkownika można przenieść do formantów sąsiadujące) za pomocą klawiatury.</span><span class="sxs-lookup"><span data-stu-id="74a37-115">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="74a37-116">Wymagane elementy IGridItemProvider</span><span class="sxs-lookup"><span data-stu-id="74a37-116">Required Members for IGridItemProvider</span></span>  
 <span data-ttu-id="74a37-117">Poniższe właściwości i metody są wymagane do wykonania <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span><span class="sxs-lookup"><span data-stu-id="74a37-117">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="74a37-118">Wymagane elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="74a37-118">Required members</span></span>|<span data-ttu-id="74a37-119">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="74a37-119">Member type</span></span>|<span data-ttu-id="74a37-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="74a37-120">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="74a37-121">Właściwość</span><span class="sxs-lookup"><span data-stu-id="74a37-121">Property</span></span>|<span data-ttu-id="74a37-122">Brak</span><span class="sxs-lookup"><span data-stu-id="74a37-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="74a37-123">Właściwość</span><span class="sxs-lookup"><span data-stu-id="74a37-123">Property</span></span>|<span data-ttu-id="74a37-124">Brak</span><span class="sxs-lookup"><span data-stu-id="74a37-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="74a37-125">Właściwość</span><span class="sxs-lookup"><span data-stu-id="74a37-125">Property</span></span>|<span data-ttu-id="74a37-126">Brak</span><span class="sxs-lookup"><span data-stu-id="74a37-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="74a37-127">Właściwość</span><span class="sxs-lookup"><span data-stu-id="74a37-127">Property</span></span>|<span data-ttu-id="74a37-128">Brak</span><span class="sxs-lookup"><span data-stu-id="74a37-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="74a37-129">Właściwość</span><span class="sxs-lookup"><span data-stu-id="74a37-129">Property</span></span>|<span data-ttu-id="74a37-130">Brak</span><span class="sxs-lookup"><span data-stu-id="74a37-130">None</span></span>|  
  
 <span data-ttu-id="74a37-131">Ten wzorzec formantu nie ma skojarzonych z nim metod ani zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="74a37-131">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="74a37-132">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="74a37-132">Exceptions</span></span>  
 <span data-ttu-id="74a37-133">Ten wzorzec formantu ma bez wyjątków skojarzone.</span><span class="sxs-lookup"><span data-stu-id="74a37-133">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74a37-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="74a37-134">See Also</span></span>  
 [<span data-ttu-id="74a37-135">Przegląd wzorców formantu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="74a37-135">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="74a37-136">Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="74a37-136">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="74a37-137">Wzorce formantów automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="74a37-137">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="74a37-138">Implementacja wzorca formantu siatki automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="74a37-138">Implementing the UI Automation Grid Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)  
 [<span data-ttu-id="74a37-139">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="74a37-139">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="74a37-140">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="74a37-140">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
