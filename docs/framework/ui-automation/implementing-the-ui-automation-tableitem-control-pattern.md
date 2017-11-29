---
title: "Implementacja wzorca formantu TableItem dla automatyzacji interfejsu użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
caps.latest.revision: "14"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 5861ab24627f9b78cd20f97fcdb1b1b3d681991a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a><span data-ttu-id="c72ce-102">Implementacja wzorca kontrolki TableItem dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="c72ce-102">Implementing the UI Automation TableItem Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="c72ce-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c72ce-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="c72ce-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="c72ce-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="c72ce-105">W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.ITableItemProvider>, wraz z informacjami dotyczącymi zdarzeń i właściwości.</span><span class="sxs-lookup"><span data-stu-id="c72ce-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableItemProvider>, including information about events and properties.</span></span> <span data-ttu-id="c72ce-106">Łącza do dodatkowe informacje są wyświetlane na końcu przeglądu.</span><span class="sxs-lookup"><span data-stu-id="c72ce-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="c72ce-107"><xref:System.Windows.Automation.TableItemPattern> — Wzorzec formantu jest używana do obsługi formantów podrzędnych kontenerów, które implementują <xref:System.Windows.Automation.Provider.ITableProvider>.</span><span class="sxs-lookup"><span data-stu-id="c72ce-107">The <xref:System.Windows.Automation.TableItemPattern> control pattern is used to support child controls of containers that implement <xref:System.Windows.Automation.Provider.ITableProvider>.</span></span> <span data-ttu-id="c72ce-108">Dostęp do pojedynczych komórek funkcji jest zapewniany przez wymagane wdrożenia równoczesnych <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span><span class="sxs-lookup"><span data-stu-id="c72ce-108">Access to individual cell functionality is provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span> <span data-ttu-id="c72ce-109">Ten wzorzec kontroli jest odpowiednikiem <xref:System.Windows.Automation.Provider.IGridItemProvider> z rozróżnienie żadnego kontroli wykonania <xref:System.Windows.Automation.Provider.ITableItemProvider> programowo musi ujawniać relacji między pojedynczych komórek i jego informacje o wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="c72ce-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridItemProvider> with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableItemProvider> must programmatically expose the relationship between the individual cell and its row and column information.</span></span> <span data-ttu-id="c72ce-110">Przykłady formantów, które implementują wzorzec tego formantu można znaleźć [formantu wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="c72ce-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="c72ce-111">Implementacja — wskazówki i konwencje</span><span class="sxs-lookup"><span data-stu-id="c72ce-111">Implementation Guidelines and Conventions</span></span>  
  
-   <span data-ttu-id="c72ce-112">Dla funkcji elementów pokrewnych siatki, zobacz [implementacja wzorca formantu GridItem dla automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="c72ce-112">For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md).</span></span>  
  
<a name="Required_Members_for_ITableItemProvider"></a>   
## <a name="required-members-for-itableitemprovider"></a><span data-ttu-id="c72ce-113">Wymagane elementy ITableItemProvider</span><span class="sxs-lookup"><span data-stu-id="c72ce-113">Required Members for ITableItemProvider</span></span>  
  
|<span data-ttu-id="c72ce-114">Wymagany element członkowski</span><span class="sxs-lookup"><span data-stu-id="c72ce-114">Required member</span></span>|<span data-ttu-id="c72ce-115">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="c72ce-115">Member type</span></span>|<span data-ttu-id="c72ce-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c72ce-116">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|<span data-ttu-id="c72ce-117">Metoda</span><span class="sxs-lookup"><span data-stu-id="c72ce-117">Method</span></span>|<span data-ttu-id="c72ce-118">Brak</span><span class="sxs-lookup"><span data-stu-id="c72ce-118">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|<span data-ttu-id="c72ce-119">Metoda</span><span class="sxs-lookup"><span data-stu-id="c72ce-119">Method</span></span>|<span data-ttu-id="c72ce-120">Brak</span><span class="sxs-lookup"><span data-stu-id="c72ce-120">None</span></span>|  
  
 <span data-ttu-id="c72ce-121">Ten wzorzec formantu nie ma skojarzonych z nimi właściwości ani zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c72ce-121">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="c72ce-122">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="c72ce-122">Exceptions</span></span>  
 <span data-ttu-id="c72ce-123">Ten wzorzec formantu ma bez wyjątków skojarzone.</span><span class="sxs-lookup"><span data-stu-id="c72ce-123">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c72ce-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c72ce-124">See Also</span></span>  
 [<span data-ttu-id="c72ce-125">Przegląd wzorców formantu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="c72ce-125">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="c72ce-126">Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="c72ce-126">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="c72ce-127">Wzorce formantów automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="c72ce-127">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="c72ce-128">Implementacja wzorca formantu tabeli automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="c72ce-128">Implementing the UI Automation Table Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-table-control-pattern.md)  
 [<span data-ttu-id="c72ce-129">Implementacja wzorca formantu GridItem dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="c72ce-129">Implementing the UI Automation GridItem Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)  
 [<span data-ttu-id="c72ce-130">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="c72ce-130">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="c72ce-131">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="c72ce-131">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
