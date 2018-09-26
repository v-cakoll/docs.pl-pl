---
title: Implementacja wzorca formantu TableItem dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: e5d5e82c5c2cfc48c98559bd6ce14519bdfaa522
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47085921"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a><span data-ttu-id="5e2d2-102">Implementacja wzorca kontrolki TableItem dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="5e2d2-102">Implementing the UI Automation TableItem Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="5e2d2-103">Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5e2d2-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="5e2d2-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="5e2d2-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="5e2d2-105">W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.ITableItemProvider>, wraz z informacjami dotyczącymi zdarzeń i właściwości.</span><span class="sxs-lookup"><span data-stu-id="5e2d2-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableItemProvider>, including information about events and properties.</span></span> <span data-ttu-id="5e2d2-106">Łącza do dodatkowe informacje są wyświetlane na końcu przeglądu.</span><span class="sxs-lookup"><span data-stu-id="5e2d2-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="5e2d2-107"><xref:System.Windows.Automation.TableItemPattern> — Wzorzec kontrolki jest używana do obsługi formantów podrzędnych kontenerów, które implementują <xref:System.Windows.Automation.Provider.ITableProvider>.</span><span class="sxs-lookup"><span data-stu-id="5e2d2-107">The <xref:System.Windows.Automation.TableItemPattern> control pattern is used to support child controls of containers that implement <xref:System.Windows.Automation.Provider.ITableProvider>.</span></span> <span data-ttu-id="5e2d2-108">Dostęp do funkcji pojedyncze komórki jest zapewniany przez wymagane wykonania współbieżnych <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span><span class="sxs-lookup"><span data-stu-id="5e2d2-108">Access to individual cell functionality is provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span> <span data-ttu-id="5e2d2-109">Ten wzorzec kontroli jest odpowiednikiem <xref:System.Windows.Automation.Provider.IGridItemProvider> z rozróżnienie, że kontrolnych Implementowanie <xref:System.Windows.Automation.Provider.ITableItemProvider> programowo musi ujawniać relacji między pojedyncze komórki i jego informacje wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="5e2d2-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridItemProvider> with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableItemProvider> must programmatically expose the relationship between the individual cell and its row and column information.</span></span> <span data-ttu-id="5e2d2-110">Przykłady formantów, które implementują wzorzec tej kontrolki, zobacz [kontroli wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="5e2d2-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="5e2d2-111">Wytyczne dotyczące implementacji i konwencje</span><span class="sxs-lookup"><span data-stu-id="5e2d2-111">Implementation Guidelines and Conventions</span></span>  
  
-   <span data-ttu-id="5e2d2-112">Dla funkcji elementów powiązanych siatki, zobacz [implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="5e2d2-112">For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md).</span></span>  
  
<a name="Required_Members_for_ITableItemProvider"></a>   
## <a name="required-members-for-itableitemprovider"></a><span data-ttu-id="5e2d2-113">Wymagane elementy ITableItemProvider</span><span class="sxs-lookup"><span data-stu-id="5e2d2-113">Required Members for ITableItemProvider</span></span>  
  
|<span data-ttu-id="5e2d2-114">Wymagany</span><span class="sxs-lookup"><span data-stu-id="5e2d2-114">Required member</span></span>|<span data-ttu-id="5e2d2-115">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="5e2d2-115">Member type</span></span>|<span data-ttu-id="5e2d2-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5e2d2-116">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|<span data-ttu-id="5e2d2-117">Metoda</span><span class="sxs-lookup"><span data-stu-id="5e2d2-117">Method</span></span>|<span data-ttu-id="5e2d2-118">Brak</span><span class="sxs-lookup"><span data-stu-id="5e2d2-118">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|<span data-ttu-id="5e2d2-119">Metoda</span><span class="sxs-lookup"><span data-stu-id="5e2d2-119">Method</span></span>|<span data-ttu-id="5e2d2-120">Brak</span><span class="sxs-lookup"><span data-stu-id="5e2d2-120">None</span></span>|  
  
 <span data-ttu-id="5e2d2-121">Ten wzorzec kontrolka nie ma skojarzonych z nimi właściwości lub zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="5e2d2-121">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="5e2d2-122">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="5e2d2-122">Exceptions</span></span>  
 <span data-ttu-id="5e2d2-123">Ten wzorzec kontroli ma skojarzone generują żadnych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="5e2d2-123">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e2d2-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e2d2-124">See Also</span></span>  
 [<span data-ttu-id="5e2d2-125">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="5e2d2-125">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="5e2d2-126">Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="5e2d2-126">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="5e2d2-127">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="5e2d2-127">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="5e2d2-128">Implementacja wzorca kontrolki tabeli automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="5e2d2-128">Implementing the UI Automation Table Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-table-control-pattern.md)  
 [<span data-ttu-id="5e2d2-129">Implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="5e2d2-129">Implementing the UI Automation GridItem Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)  
 [<span data-ttu-id="5e2d2-130">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="5e2d2-130">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="5e2d2-131">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="5e2d2-131">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
