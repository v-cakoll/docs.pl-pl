---
title: Implementacja wzorca kontrolki TableItem dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: 44b14c65a5a86b4e56697904b9b013b4daa84479
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110433"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a><span data-ttu-id="99186-102">Implementacja wzorca kontrolki TableItem dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="99186-102">Implementing the UI Automation TableItem Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="99186-103">Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="99186-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="99186-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="99186-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="99186-105">W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.ITableItemProvider>, wraz z informacjami dotyczącymi zdarzeń i właściwości.</span><span class="sxs-lookup"><span data-stu-id="99186-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableItemProvider>, including information about events and properties.</span></span> <span data-ttu-id="99186-106">Łącza do dodatkowe informacje są wyświetlane na końcu przeglądu.</span><span class="sxs-lookup"><span data-stu-id="99186-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="99186-107"><xref:System.Windows.Automation.TableItemPattern> — Wzorzec kontrolki jest używana do obsługi formantów podrzędnych kontenerów, które implementują <xref:System.Windows.Automation.Provider.ITableProvider>.</span><span class="sxs-lookup"><span data-stu-id="99186-107">The <xref:System.Windows.Automation.TableItemPattern> control pattern is used to support child controls of containers that implement <xref:System.Windows.Automation.Provider.ITableProvider>.</span></span> <span data-ttu-id="99186-108">Dostęp do funkcji pojedyncze komórki jest zapewniany przez wymagane wykonania współbieżnych <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span><span class="sxs-lookup"><span data-stu-id="99186-108">Access to individual cell functionality is provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span> <span data-ttu-id="99186-109">Ten wzorzec kontroli jest odpowiednikiem <xref:System.Windows.Automation.Provider.IGridItemProvider> z rozróżnienie, że kontrolnych Implementowanie <xref:System.Windows.Automation.Provider.ITableItemProvider> programowo musi ujawniać relacji między pojedyncze komórki i jego informacje wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="99186-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridItemProvider> with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableItemProvider> must programmatically expose the relationship between the individual cell and its row and column information.</span></span> <span data-ttu-id="99186-110">Przykłady formantów, które implementują wzorzec tej kontrolki, zobacz [kontroli wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="99186-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="99186-111">Wytyczne dotyczące implementacji i konwencje</span><span class="sxs-lookup"><span data-stu-id="99186-111">Implementation Guidelines and Conventions</span></span>  
  
-   <span data-ttu-id="99186-112">Dla funkcji elementów powiązanych siatki, zobacz [implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="99186-112">For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md).</span></span>  
  
<a name="Required_Members_for_ITableItemProvider"></a>   
## <a name="required-members-for-itableitemprovider"></a><span data-ttu-id="99186-113">Wymagane elementy ITableItemProvider</span><span class="sxs-lookup"><span data-stu-id="99186-113">Required Members for ITableItemProvider</span></span>  
  
|<span data-ttu-id="99186-114">Wymagany</span><span class="sxs-lookup"><span data-stu-id="99186-114">Required member</span></span>|<span data-ttu-id="99186-115">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="99186-115">Member type</span></span>|<span data-ttu-id="99186-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="99186-116">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|<span data-ttu-id="99186-117">Metoda</span><span class="sxs-lookup"><span data-stu-id="99186-117">Method</span></span>|<span data-ttu-id="99186-118">Brak</span><span class="sxs-lookup"><span data-stu-id="99186-118">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|<span data-ttu-id="99186-119">Metoda</span><span class="sxs-lookup"><span data-stu-id="99186-119">Method</span></span>|<span data-ttu-id="99186-120">Brak</span><span class="sxs-lookup"><span data-stu-id="99186-120">None</span></span>|  
  
 <span data-ttu-id="99186-121">Ten wzorzec kontrolka nie ma skojarzonych z nimi właściwości lub zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="99186-121">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="99186-122">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="99186-122">Exceptions</span></span>  
 <span data-ttu-id="99186-123">Ten wzorzec kontroli ma skojarzone generują żadnych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="99186-123">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99186-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99186-124">See also</span></span>

- [<span data-ttu-id="99186-125">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="99186-125">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="99186-126">Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="99186-126">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="99186-127">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="99186-127">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="99186-128">Implementacja wzorca kontrolki tabeli automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="99186-128">Implementing the UI Automation Table Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-table-control-pattern.md)
- [<span data-ttu-id="99186-129">Implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="99186-129">Implementing the UI Automation GridItem Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)
- [<span data-ttu-id="99186-130">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="99186-130">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="99186-131">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="99186-131">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
