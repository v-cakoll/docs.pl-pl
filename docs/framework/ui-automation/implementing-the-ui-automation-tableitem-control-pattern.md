---
title: Implementacja wzorca kontrolki TableItem dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: f35b491c31e8725eac0025dfd6815079d0ea9b79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180074"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a><span data-ttu-id="df702-102">Implementacja wzorca kontrolki TableItem dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="df702-102">Implementing the UI Automation TableItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="df702-103">Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="df702-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="df702-104">Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="df702-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="df702-105">W tym temacie przedstawiono wytyczne <xref:System.Windows.Automation.Provider.ITableItemProvider>i konwencje dotyczące implementacji, w tym informacje o zdarzeniach i właściwościach.</span><span class="sxs-lookup"><span data-stu-id="df702-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableItemProvider>, including information about events and properties.</span></span> <span data-ttu-id="df702-106">Łącza do dodatkowych odwołań są wyświetlane na końcu przeglądu.</span><span class="sxs-lookup"><span data-stu-id="df702-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="df702-107">Wzorzec <xref:System.Windows.Automation.TableItemPattern> kontroli służy do obsługi formantu podrzędnego kontenerów, które implementują <xref:System.Windows.Automation.Provider.ITableProvider>.</span><span class="sxs-lookup"><span data-stu-id="df702-107">The <xref:System.Windows.Automation.TableItemPattern> control pattern is used to support child controls of containers that implement <xref:System.Windows.Automation.Provider.ITableProvider>.</span></span> <span data-ttu-id="df702-108">Dostęp do poszczególnych funkcji komórek zapewnia wymagana jednoczesna <xref:System.Windows.Automation.Provider.IGridItemProvider>implementacja programu .</span><span class="sxs-lookup"><span data-stu-id="df702-108">Access to individual cell functionality is provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span> <span data-ttu-id="df702-109">Ten wzorzec formantu jest analogiczne <xref:System.Windows.Automation.Provider.IGridItemProvider> <xref:System.Windows.Automation.Provider.ITableItemProvider> do rozróżnienia, że wszelkie formanty implementacji musi programowo uwidaczniać relację między poszczególnych komórek i jej wiersza i kolumny informacji.</span><span class="sxs-lookup"><span data-stu-id="df702-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridItemProvider> with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableItemProvider> must programmatically expose the relationship between the individual cell and its row and column information.</span></span> <span data-ttu-id="df702-110">Aby zapoznać się z przykładami formantów implementuujnych tego wzorca sterowania, zobacz [Mapowanie wzorców sterowania dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="df702-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="df702-111">Wytyczne i konwencje dotyczące wdrażania</span><span class="sxs-lookup"><span data-stu-id="df702-111">Implementation Guidelines and Conventions</span></span>  
  
- <span data-ttu-id="df702-112">Aby zapoznać się z funkcją elementów siatki pokrewne, zobacz [Implementowanie wzorca sterowania interfejsem użytkownika automatyzacji](implementing-the-ui-automation-griditem-control-pattern.md)interfejsu użytkownika .</span><span class="sxs-lookup"><span data-stu-id="df702-112">For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](implementing-the-ui-automation-griditem-control-pattern.md).</span></span>  
  
<a name="Required_Members_for_ITableItemProvider"></a>
## <a name="required-members-for-itableitemprovider"></a><span data-ttu-id="df702-113">Wymagane elementy członkowskie dla ITableItemProvider</span><span class="sxs-lookup"><span data-stu-id="df702-113">Required Members for ITableItemProvider</span></span>  
  
|<span data-ttu-id="df702-114">Wymagany element członkowski</span><span class="sxs-lookup"><span data-stu-id="df702-114">Required member</span></span>|<span data-ttu-id="df702-115">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="df702-115">Member type</span></span>|<span data-ttu-id="df702-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="df702-116">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|<span data-ttu-id="df702-117">Metoda</span><span class="sxs-lookup"><span data-stu-id="df702-117">Method</span></span>|<span data-ttu-id="df702-118">Brak</span><span class="sxs-lookup"><span data-stu-id="df702-118">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|<span data-ttu-id="df702-119">Metoda</span><span class="sxs-lookup"><span data-stu-id="df702-119">Method</span></span>|<span data-ttu-id="df702-120">Brak</span><span class="sxs-lookup"><span data-stu-id="df702-120">None</span></span>|  
  
 <span data-ttu-id="df702-121">Ten wzorzec formantu nie ma skojarzonych właściwości lub zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="df702-121">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="df702-122">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="df702-122">Exceptions</span></span>  
 <span data-ttu-id="df702-123">Ten wzorzec formantu nie ma skojarzonych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="df702-123">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df702-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="df702-124">See also</span></span>

- [<span data-ttu-id="df702-125">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="df702-125">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="df702-126">Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="df702-126">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="df702-127">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="df702-127">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="df702-128">Implementacja wzorca kontrolki tabeli automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="df702-128">Implementing the UI Automation Table Control Pattern</span></span>](implementing-the-ui-automation-table-control-pattern.md)
- [<span data-ttu-id="df702-129">Implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="df702-129">Implementing the UI Automation GridItem Control Pattern</span></span>](implementing-the-ui-automation-griditem-control-pattern.md)
- [<span data-ttu-id="df702-130">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="df702-130">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="df702-131">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="df702-131">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
