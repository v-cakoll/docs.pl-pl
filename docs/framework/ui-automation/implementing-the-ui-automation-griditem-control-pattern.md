---
title: Implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: d561587e6bb98ba857b27ba89b4c1a45ba964ffd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180190"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="8f176-102">Implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="8f176-102">Implementing the UI Automation GridItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="8f176-103">Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="8f176-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8f176-104">Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="8f176-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="8f176-105">W tym temacie przedstawiono wytyczne <xref:System.Windows.Automation.Provider.IGridItemProvider>i konwencje dotyczące wdrażania, w tym informacje o właściwościach.</span><span class="sxs-lookup"><span data-stu-id="8f176-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="8f176-106">Łącza do dodatkowych odwołań są wyświetlane na końcu przeglądu.</span><span class="sxs-lookup"><span data-stu-id="8f176-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="8f176-107">Wzorzec <xref:System.Windows.Automation.GridItemPattern> kontroli służy do obsługi poszczególnych <xref:System.Windows.Automation.Provider.IGridProvider>formantów podrzędnych kontenerów, które implementują .</span><span class="sxs-lookup"><span data-stu-id="8f176-107">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="8f176-108">Aby zapoznać się z przykładami formantów implementuujnych tego wzorca sterowania, zobacz [Mapowanie wzorców sterowania dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="8f176-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="8f176-109">Wytyczne i konwencje dotyczące wdrażania</span><span class="sxs-lookup"><span data-stu-id="8f176-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="8f176-110">Podczas wdrażania <xref:System.Windows.Automation.Provider.IGridProvider>należy zwrócić uwagę na następujące wytyczne i konwencje:</span><span class="sxs-lookup"><span data-stu-id="8f176-110">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="8f176-111">Współrzędne siatki są oparte na wartości zerowej, a lewa górna komórka ma współrzędne (0, 0).</span><span class="sxs-lookup"><span data-stu-id="8f176-111">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="8f176-112">Scalone komórki <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> będą <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> raportować swoje i właściwości na podstawie ich podstawowej komórki kotwicy zdefiniowanej przez dostawcę automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8f176-112">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="8f176-113">Zazwyczaj będzie to najwyższy i najbardziej wysunięty do lewej wiersz lub kolumna.</span><span class="sxs-lookup"><span data-stu-id="8f176-113">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
- <span data-ttu-id="8f176-114"><xref:System.Windows.Automation.Provider.IGridItemProvider>nie przewiduje aktywnej manipulacji siatką, takiej jak scalanie lub dzielenie komórek.</span><span class="sxs-lookup"><span data-stu-id="8f176-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
- <span data-ttu-id="8f176-115">Formanty, które implementują <xref:System.Windows.Automation.Provider.IGridItemProvider> zazwyczaj mogą być przechodzione (czyli klient automatyzacji interfejsu użytkownika można przenieść do sąsiednich formantów) za pomocą klawiatury.</span><span class="sxs-lookup"><span data-stu-id="8f176-115">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>
## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="8f176-116">Wymagana liczba członków dla IGridItemProvider</span><span class="sxs-lookup"><span data-stu-id="8f176-116">Required Members for IGridItemProvider</span></span>  
 <span data-ttu-id="8f176-117">Następujące właściwości i metody są wymagane <xref:System.Windows.Automation.Provider.IGridItemProvider>do wdrożenia .</span><span class="sxs-lookup"><span data-stu-id="8f176-117">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="8f176-118">Wymagane elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8f176-118">Required members</span></span>|<span data-ttu-id="8f176-119">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="8f176-119">Member type</span></span>|<span data-ttu-id="8f176-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8f176-120">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="8f176-121">Właściwość</span><span class="sxs-lookup"><span data-stu-id="8f176-121">Property</span></span>|<span data-ttu-id="8f176-122">Brak</span><span class="sxs-lookup"><span data-stu-id="8f176-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="8f176-123">Właściwość</span><span class="sxs-lookup"><span data-stu-id="8f176-123">Property</span></span>|<span data-ttu-id="8f176-124">Brak</span><span class="sxs-lookup"><span data-stu-id="8f176-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="8f176-125">Właściwość</span><span class="sxs-lookup"><span data-stu-id="8f176-125">Property</span></span>|<span data-ttu-id="8f176-126">Brak</span><span class="sxs-lookup"><span data-stu-id="8f176-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="8f176-127">Właściwość</span><span class="sxs-lookup"><span data-stu-id="8f176-127">Property</span></span>|<span data-ttu-id="8f176-128">Brak</span><span class="sxs-lookup"><span data-stu-id="8f176-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="8f176-129">Właściwość</span><span class="sxs-lookup"><span data-stu-id="8f176-129">Property</span></span>|<span data-ttu-id="8f176-130">Brak</span><span class="sxs-lookup"><span data-stu-id="8f176-130">None</span></span>|  
  
 <span data-ttu-id="8f176-131">Ten wzorzec formantu nie ma skojarzonych metod ani zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8f176-131">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="8f176-132">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="8f176-132">Exceptions</span></span>  
 <span data-ttu-id="8f176-133">Ten wzorzec formantu nie ma skojarzonych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="8f176-133">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f176-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8f176-134">See also</span></span>

- [<span data-ttu-id="8f176-135">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="8f176-135">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="8f176-136">Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="8f176-136">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="8f176-137">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="8f176-137">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="8f176-138">Implementacja wzorca kontrolki siatki automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="8f176-138">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="8f176-139">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="8f176-139">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="8f176-140">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="8f176-140">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
