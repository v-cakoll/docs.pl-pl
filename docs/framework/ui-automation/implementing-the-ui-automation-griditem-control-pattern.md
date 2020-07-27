---
title: Implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika
description: Znajomość wytycznych i konwencji dotyczących implementacji wzorca kontrolki GridItemPattern dla elementów siatki w automatyzacji interfejsu użytkownika. Zobacz wymagane elementy członkowskie dla IGridItemProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: e0a0c616f3f0cf9bc091e4fbb496d71ab8550bd3
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165824"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="8e5af-104">Implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="8e5af-104">Implementing the UI Automation GridItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="8e5af-105">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8e5af-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8e5af-106">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="8e5af-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="8e5af-107">W tym temacie przedstawiono wskazówki i konwencje dotyczące wdrażania <xref:System.Windows.Automation.Provider.IGridItemProvider> , w tym informacje o właściwościach.</span><span class="sxs-lookup"><span data-stu-id="8e5af-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="8e5af-108">Linki do dodatkowych odwołań znajdują się na końcu przeglądu.</span><span class="sxs-lookup"><span data-stu-id="8e5af-108">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="8e5af-109"><xref:System.Windows.Automation.GridItemPattern>Wzorzec kontrolki służy do obsługi poszczególnych kontrolek podrzędnych kontenerów, które implementują <xref:System.Windows.Automation.Provider.IGridProvider> .</span><span class="sxs-lookup"><span data-stu-id="8e5af-109">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="8e5af-110">Aby zapoznać się z przykładami formantów implementujących ten wzorzec kontrolek, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="8e5af-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="8e5af-111">Wytyczne i konwencje dotyczące implementacji</span><span class="sxs-lookup"><span data-stu-id="8e5af-111">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="8e5af-112">Podczas wdrażania należy <xref:System.Windows.Automation.Provider.IGridProvider> zwrócić uwagę na następujące wytyczne i konwencje:</span><span class="sxs-lookup"><span data-stu-id="8e5af-112">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="8e5af-113">Współrzędne siatki są równe zero, a lewa górna komórka ma współrzędne (0, 0).</span><span class="sxs-lookup"><span data-stu-id="8e5af-113">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="8e5af-114">Scalone komórki będą raportować ich <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> i <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> właściwości w oparciu o ich źródłową komórkę zakotwiczenia, zgodnie z definicją dostawcy automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8e5af-114">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="8e5af-115">Zwykle jest to pierwszy wiersz lub kolumna najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="8e5af-115">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
- <span data-ttu-id="8e5af-116"><xref:System.Windows.Automation.Provider.IGridItemProvider>nie zapewnia aktywnego manipulowania siatką, taką jak scalanie lub dzielenie komórek.</span><span class="sxs-lookup"><span data-stu-id="8e5af-116"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
- <span data-ttu-id="8e5af-117">Kontrolki implementujące <xref:System.Windows.Automation.Provider.IGridItemProvider> zwykle mogą być przenoszone (oznacza to, że klient automatyzacji interfejsu użytkownika można przenieść do sąsiednich kontrolek) przy użyciu klawiatury.</span><span class="sxs-lookup"><span data-stu-id="8e5af-117">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>
## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="8e5af-118">Wymagane elementy członkowskie dla IGridItemProvider</span><span class="sxs-lookup"><span data-stu-id="8e5af-118">Required Members for IGridItemProvider</span></span>  
 <span data-ttu-id="8e5af-119">Następujące właściwości i metody są wymagane do zaimplementowania <xref:System.Windows.Automation.Provider.IGridItemProvider> .</span><span class="sxs-lookup"><span data-stu-id="8e5af-119">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="8e5af-120">Wymagane elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8e5af-120">Required members</span></span>|<span data-ttu-id="8e5af-121">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="8e5af-121">Member type</span></span>|<span data-ttu-id="8e5af-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8e5af-122">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="8e5af-123">Właściwość</span><span class="sxs-lookup"><span data-stu-id="8e5af-123">Property</span></span>|<span data-ttu-id="8e5af-124">Brak</span><span class="sxs-lookup"><span data-stu-id="8e5af-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="8e5af-125">Właściwość</span><span class="sxs-lookup"><span data-stu-id="8e5af-125">Property</span></span>|<span data-ttu-id="8e5af-126">Brak</span><span class="sxs-lookup"><span data-stu-id="8e5af-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="8e5af-127">Właściwość</span><span class="sxs-lookup"><span data-stu-id="8e5af-127">Property</span></span>|<span data-ttu-id="8e5af-128">Brak</span><span class="sxs-lookup"><span data-stu-id="8e5af-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="8e5af-129">Właściwość</span><span class="sxs-lookup"><span data-stu-id="8e5af-129">Property</span></span>|<span data-ttu-id="8e5af-130">Brak</span><span class="sxs-lookup"><span data-stu-id="8e5af-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="8e5af-131">Właściwość</span><span class="sxs-lookup"><span data-stu-id="8e5af-131">Property</span></span>|<span data-ttu-id="8e5af-132">Brak</span><span class="sxs-lookup"><span data-stu-id="8e5af-132">None</span></span>|  
  
 <span data-ttu-id="8e5af-133">Ten wzorzec kontroli nie ma skojarzonych metod lub zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8e5af-133">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="8e5af-134">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="8e5af-134">Exceptions</span></span>  
 <span data-ttu-id="8e5af-135">Ten wzorzec kontrolki nie ma żadnych skojarzonych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="8e5af-135">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e5af-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e5af-136">See also</span></span>

- [<span data-ttu-id="8e5af-137">Wzorce formantów automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="8e5af-137">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="8e5af-138">Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="8e5af-138">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="8e5af-139">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="8e5af-139">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="8e5af-140">Implementacja wzorca kontrolki siatki automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="8e5af-140">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="8e5af-141">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="8e5af-141">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="8e5af-142">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="8e5af-142">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
