---
title: Implementacja wzorca kontrolki TableItem dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: 4374666ba5e03720413614c63b00ba987f81f58f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447084"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a><span data-ttu-id="3daa2-102">Implementacja wzorca kontrolki TableItem dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="3daa2-102">Implementing the UI Automation TableItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="3daa2-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="3daa2-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="3daa2-104">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="3daa2-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="3daa2-105">W tym temacie przedstawiono wytyczne i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.ITableItemProvider>, w tym informacje o zdarzeniach i właściwościach.</span><span class="sxs-lookup"><span data-stu-id="3daa2-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableItemProvider>, including information about events and properties.</span></span> <span data-ttu-id="3daa2-106">Linki do dodatkowych odwołań znajdują się na końcu przeglądu.</span><span class="sxs-lookup"><span data-stu-id="3daa2-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="3daa2-107"><xref:System.Windows.Automation.TableItemPattern> wzorzec kontroli służy do obsługi kontrolek podrzędnych kontenerów, które implementują <xref:System.Windows.Automation.Provider.ITableProvider>.</span><span class="sxs-lookup"><span data-stu-id="3daa2-107">The <xref:System.Windows.Automation.TableItemPattern> control pattern is used to support child controls of containers that implement <xref:System.Windows.Automation.Provider.ITableProvider>.</span></span> <span data-ttu-id="3daa2-108">Dostęp do funkcji poszczególnych komórek jest zapewniany przez wymaganą współbieżną implementację <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span><span class="sxs-lookup"><span data-stu-id="3daa2-108">Access to individual cell functionality is provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span> <span data-ttu-id="3daa2-109">Ten wzorzec kontrolki jest analogiczny do <xref:System.Windows.Automation.Provider.IGridItemProvider> z rozróżnieniem, że każda kontrolka implementująca <xref:System.Windows.Automation.Provider.ITableItemProvider> musi programowo uwidocznić relację między daną komórką a informacjami o jego wierszu i kolumnie.</span><span class="sxs-lookup"><span data-stu-id="3daa2-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridItemProvider> with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableItemProvider> must programmatically expose the relationship between the individual cell and its row and column information.</span></span> <span data-ttu-id="3daa2-110">Aby zapoznać się z przykładami formantów implementujących ten wzorzec kontrolek, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="3daa2-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="3daa2-111">Wytyczne i konwencje dotyczące implementacji</span><span class="sxs-lookup"><span data-stu-id="3daa2-111">Implementation Guidelines and Conventions</span></span>  
  
- <span data-ttu-id="3daa2-112">Aby zapoznać się z pokrewnymi funkcjami elementów siatki, zobacz [implementowanie wzorca kontrolki GridItem automatyzacji interfejsu użytkownika](implementing-the-ui-automation-griditem-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="3daa2-112">For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](implementing-the-ui-automation-griditem-control-pattern.md).</span></span>  
  
<a name="Required_Members_for_ITableItemProvider"></a>   
## <a name="required-members-for-itableitemprovider"></a><span data-ttu-id="3daa2-113">Wymagane elementy członkowskie dla ITableItemProvider</span><span class="sxs-lookup"><span data-stu-id="3daa2-113">Required Members for ITableItemProvider</span></span>  
  
|<span data-ttu-id="3daa2-114">Wymagany element członkowski</span><span class="sxs-lookup"><span data-stu-id="3daa2-114">Required member</span></span>|<span data-ttu-id="3daa2-115">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="3daa2-115">Member type</span></span>|<span data-ttu-id="3daa2-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3daa2-116">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|<span data-ttu-id="3daa2-117">Metoda</span><span class="sxs-lookup"><span data-stu-id="3daa2-117">Method</span></span>|<span data-ttu-id="3daa2-118">Brak</span><span class="sxs-lookup"><span data-stu-id="3daa2-118">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|<span data-ttu-id="3daa2-119">Metoda</span><span class="sxs-lookup"><span data-stu-id="3daa2-119">Method</span></span>|<span data-ttu-id="3daa2-120">Brak</span><span class="sxs-lookup"><span data-stu-id="3daa2-120">None</span></span>|  
  
 <span data-ttu-id="3daa2-121">Ten wzorzec kontrolki nie ma skojarzonych właściwości ani zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="3daa2-121">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="3daa2-122">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="3daa2-122">Exceptions</span></span>  
 <span data-ttu-id="3daa2-123">Ten wzorzec kontrolki nie ma żadnych skojarzonych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="3daa2-123">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3daa2-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3daa2-124">See also</span></span>

- [<span data-ttu-id="3daa2-125">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="3daa2-125">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="3daa2-126">Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="3daa2-126">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="3daa2-127">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="3daa2-127">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="3daa2-128">Implementacja wzorca kontrolki tabeli automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="3daa2-128">Implementing the UI Automation Table Control Pattern</span></span>](implementing-the-ui-automation-table-control-pattern.md)
- [<span data-ttu-id="3daa2-129">Implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="3daa2-129">Implementing the UI Automation GridItem Control Pattern</span></span>](implementing-the-ui-automation-griditem-control-pattern.md)
- [<span data-ttu-id="3daa2-130">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="3daa2-130">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="3daa2-131">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="3daa2-131">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
