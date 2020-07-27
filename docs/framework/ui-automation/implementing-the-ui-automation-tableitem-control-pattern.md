---
title: Implementacja wzorca kontrolki TableItem dla automatyzacji interfejsu użytkownika
description: Zapoznaj się z wytycznymi i konwencjami, aby zaimplementować wzorzec kontrolki TableItem w automatyzacji interfejsu użytkownika. Znajomość wymaganych członków interfejsu ITableItemProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: 3d6d31fe0e041fbba147df14d290a775188755f2
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163527"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a><span data-ttu-id="cbae5-104">Implementacja wzorca kontrolki TableItem dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="cbae5-104">Implementing the UI Automation TableItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="cbae5-105">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="cbae5-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="cbae5-106">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="cbae5-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="cbae5-107">W tym temacie przedstawiono wskazówki i konwencje dotyczące wdrażania <xref:System.Windows.Automation.Provider.ITableItemProvider> , w tym informacje o zdarzeniach i właściwościach.</span><span class="sxs-lookup"><span data-stu-id="cbae5-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableItemProvider>, including information about events and properties.</span></span> <span data-ttu-id="cbae5-108">Linki do dodatkowych odwołań znajdują się na końcu przeglądu.</span><span class="sxs-lookup"><span data-stu-id="cbae5-108">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="cbae5-109"><xref:System.Windows.Automation.TableItemPattern>Wzorzec kontrolki służy do obsługi kontrolek podrzędnych kontenerów, które implementują <xref:System.Windows.Automation.Provider.ITableProvider> .</span><span class="sxs-lookup"><span data-stu-id="cbae5-109">The <xref:System.Windows.Automation.TableItemPattern> control pattern is used to support child controls of containers that implement <xref:System.Windows.Automation.Provider.ITableProvider>.</span></span> <span data-ttu-id="cbae5-110">Dostęp do funkcji poszczególnych komórek jest zapewniany przez wymaganą współbieżną implementację <xref:System.Windows.Automation.Provider.IGridItemProvider> .</span><span class="sxs-lookup"><span data-stu-id="cbae5-110">Access to individual cell functionality is provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span> <span data-ttu-id="cbae5-111">Ten wzorzec kontrolki jest analogiczny do <xref:System.Windows.Automation.Provider.IGridItemProvider> rozróżnienia, że jakakolwiek kontrola implementująca <xref:System.Windows.Automation.Provider.ITableItemProvider> musi programowo uwidocznić relację między daną komórką a informacjami o jego wierszu i kolumnie.</span><span class="sxs-lookup"><span data-stu-id="cbae5-111">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridItemProvider> with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableItemProvider> must programmatically expose the relationship between the individual cell and its row and column information.</span></span> <span data-ttu-id="cbae5-112">Aby zapoznać się z przykładami formantów implementujących ten wzorzec kontrolek, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="cbae5-112">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="cbae5-113">Wytyczne i konwencje dotyczące implementacji</span><span class="sxs-lookup"><span data-stu-id="cbae5-113">Implementation Guidelines and Conventions</span></span>  
  
- <span data-ttu-id="cbae5-114">Aby zapoznać się z pokrewnymi funkcjami elementów siatki, zobacz [implementowanie wzorca kontrolki GridItem automatyzacji interfejsu użytkownika](implementing-the-ui-automation-griditem-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="cbae5-114">For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](implementing-the-ui-automation-griditem-control-pattern.md).</span></span>  
  
<a name="Required_Members_for_ITableItemProvider"></a>
## <a name="required-members-for-itableitemprovider"></a><span data-ttu-id="cbae5-115">Wymagane elementy członkowskie dla ITableItemProvider</span><span class="sxs-lookup"><span data-stu-id="cbae5-115">Required Members for ITableItemProvider</span></span>  
  
|<span data-ttu-id="cbae5-116">Wymagany element członkowski</span><span class="sxs-lookup"><span data-stu-id="cbae5-116">Required member</span></span>|<span data-ttu-id="cbae5-117">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="cbae5-117">Member type</span></span>|<span data-ttu-id="cbae5-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cbae5-118">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|<span data-ttu-id="cbae5-119">Metoda</span><span class="sxs-lookup"><span data-stu-id="cbae5-119">Method</span></span>|<span data-ttu-id="cbae5-120">Brak</span><span class="sxs-lookup"><span data-stu-id="cbae5-120">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|<span data-ttu-id="cbae5-121">Metoda</span><span class="sxs-lookup"><span data-stu-id="cbae5-121">Method</span></span>|<span data-ttu-id="cbae5-122">Brak</span><span class="sxs-lookup"><span data-stu-id="cbae5-122">None</span></span>|  
  
 <span data-ttu-id="cbae5-123">Ten wzorzec kontrolki nie ma skojarzonych właściwości ani zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="cbae5-123">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="cbae5-124">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="cbae5-124">Exceptions</span></span>  
 <span data-ttu-id="cbae5-125">Ten wzorzec kontrolki nie ma żadnych skojarzonych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="cbae5-125">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbae5-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cbae5-126">See also</span></span>

- [<span data-ttu-id="cbae5-127">Wzorce formantów automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="cbae5-127">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="cbae5-128">Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="cbae5-128">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="cbae5-129">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="cbae5-129">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="cbae5-130">Implementacja wzorca formantu tabeli automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="cbae5-130">Implementing the UI Automation Table Control Pattern</span></span>](implementing-the-ui-automation-table-control-pattern.md)
- [<span data-ttu-id="cbae5-131">Implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="cbae5-131">Implementing the UI Automation GridItem Control Pattern</span></span>](implementing-the-ui-automation-griditem-control-pattern.md)
- [<span data-ttu-id="cbae5-132">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="cbae5-132">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="cbae5-133">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="cbae5-133">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
