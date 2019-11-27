---
title: Implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: 832a53e072afc5533f2eeb7feb0cc326771cf23d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435254"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="5c8fa-102">Implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="5c8fa-102">Implementing the UI Automation GridItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="5c8fa-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="5c8fa-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="5c8fa-104">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="5c8fa-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="5c8fa-105">W tym temacie przedstawiono wytyczne i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IGridItemProvider>, w tym informacje o właściwościach.</span><span class="sxs-lookup"><span data-stu-id="5c8fa-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="5c8fa-106">Linki do dodatkowych odwołań znajdują się na końcu przeglądu.</span><span class="sxs-lookup"><span data-stu-id="5c8fa-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="5c8fa-107"><xref:System.Windows.Automation.GridItemPattern> wzorzec kontroli służy do obsługi poszczególnych formantów podrzędnych kontenerów, które implementują <xref:System.Windows.Automation.Provider.IGridProvider>.</span><span class="sxs-lookup"><span data-stu-id="5c8fa-107">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="5c8fa-108">Aby zapoznać się z przykładami formantów implementujących ten wzorzec kontrolek, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="5c8fa-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="5c8fa-109">Wytyczne i konwencje dotyczące implementacji</span><span class="sxs-lookup"><span data-stu-id="5c8fa-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="5c8fa-110">Podczas wdrażania <xref:System.Windows.Automation.Provider.IGridProvider>należy zwrócić uwagę na następujące wytyczne i konwencje:</span><span class="sxs-lookup"><span data-stu-id="5c8fa-110">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="5c8fa-111">Współrzędne siatki są równe zero, a lewa górna komórka ma współrzędne (0, 0).</span><span class="sxs-lookup"><span data-stu-id="5c8fa-111">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="5c8fa-112">Scalone komórki będą raportować <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> i <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> właściwości na podstawie ich źródłowej komórki zakotwiczenia zdefiniowanej przez dostawcę automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5c8fa-112">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="5c8fa-113">Zwykle jest to pierwszy wiersz lub kolumna najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="5c8fa-113">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
- <span data-ttu-id="5c8fa-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> nie zapewnia aktywnego manipulowania siatką, taką jak scalanie lub dzielenie komórek.</span><span class="sxs-lookup"><span data-stu-id="5c8fa-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
- <span data-ttu-id="5c8fa-115">Kontrolki implementujące <xref:System.Windows.Automation.Provider.IGridItemProvider> mogą być zwykle przenoszone (oznacza to, że klient automatyzacji interfejsu użytkownika można przenieść do sąsiednich kontrolek) przy użyciu klawiatury.</span><span class="sxs-lookup"><span data-stu-id="5c8fa-115">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="5c8fa-116">Wymagane elementy członkowskie dla IGridItemProvider</span><span class="sxs-lookup"><span data-stu-id="5c8fa-116">Required Members for IGridItemProvider</span></span>  
 <span data-ttu-id="5c8fa-117">Do zaimplementowania <xref:System.Windows.Automation.Provider.IGridItemProvider>są wymagane następujące właściwości i metody.</span><span class="sxs-lookup"><span data-stu-id="5c8fa-117">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="5c8fa-118">Wymagane elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="5c8fa-118">Required members</span></span>|<span data-ttu-id="5c8fa-119">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="5c8fa-119">Member type</span></span>|<span data-ttu-id="5c8fa-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5c8fa-120">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="5c8fa-121">Właściwość</span><span class="sxs-lookup"><span data-stu-id="5c8fa-121">Property</span></span>|<span data-ttu-id="5c8fa-122">Brak</span><span class="sxs-lookup"><span data-stu-id="5c8fa-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="5c8fa-123">Właściwość</span><span class="sxs-lookup"><span data-stu-id="5c8fa-123">Property</span></span>|<span data-ttu-id="5c8fa-124">Brak</span><span class="sxs-lookup"><span data-stu-id="5c8fa-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="5c8fa-125">Właściwość</span><span class="sxs-lookup"><span data-stu-id="5c8fa-125">Property</span></span>|<span data-ttu-id="5c8fa-126">Brak</span><span class="sxs-lookup"><span data-stu-id="5c8fa-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="5c8fa-127">Właściwość</span><span class="sxs-lookup"><span data-stu-id="5c8fa-127">Property</span></span>|<span data-ttu-id="5c8fa-128">Brak</span><span class="sxs-lookup"><span data-stu-id="5c8fa-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="5c8fa-129">Właściwość</span><span class="sxs-lookup"><span data-stu-id="5c8fa-129">Property</span></span>|<span data-ttu-id="5c8fa-130">Brak</span><span class="sxs-lookup"><span data-stu-id="5c8fa-130">None</span></span>|  
  
 <span data-ttu-id="5c8fa-131">Ten wzorzec kontroli nie ma skojarzonych metod lub zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5c8fa-131">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="5c8fa-132">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="5c8fa-132">Exceptions</span></span>  
 <span data-ttu-id="5c8fa-133">Ten wzorzec kontrolki nie ma żadnych skojarzonych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="5c8fa-133">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c8fa-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5c8fa-134">See also</span></span>

- [<span data-ttu-id="5c8fa-135">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="5c8fa-135">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="5c8fa-136">Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="5c8fa-136">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="5c8fa-137">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="5c8fa-137">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="5c8fa-138">Implementacja wzorca kontrolki siatki automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="5c8fa-138">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="5c8fa-139">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="5c8fa-139">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="5c8fa-140">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="5c8fa-140">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
