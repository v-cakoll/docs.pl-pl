---
title: Implementacja wzorca kontrolki TableItem dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: cdbfc8d24dce3b63801682528a49c13d89660935
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043176"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a><span data-ttu-id="99861-102">Implementacja wzorca kontrolki TableItem dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="99861-102">Implementing the UI Automation TableItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="99861-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="99861-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="99861-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="99861-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="99861-105">W tym temacie przedstawiono wskazówki i konwencje <xref:System.Windows.Automation.Provider.ITableItemProvider>dotyczące wdrażania, w tym informacje o zdarzeniach i właściwościach.</span><span class="sxs-lookup"><span data-stu-id="99861-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableItemProvider>, including information about events and properties.</span></span> <span data-ttu-id="99861-106">Linki do dodatkowych odwołań znajdują się na końcu przeglądu.</span><span class="sxs-lookup"><span data-stu-id="99861-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="99861-107">Wzorzec kontrolki służy do obsługi kontrolek podrzędnych kontenerów, które implementują <xref:System.Windows.Automation.Provider.ITableProvider>. <xref:System.Windows.Automation.TableItemPattern></span><span class="sxs-lookup"><span data-stu-id="99861-107">The <xref:System.Windows.Automation.TableItemPattern> control pattern is used to support child controls of containers that implement <xref:System.Windows.Automation.Provider.ITableProvider>.</span></span> <span data-ttu-id="99861-108">Dostęp do funkcji poszczególnych komórek jest zapewniany przez wymaganą współbieżną <xref:System.Windows.Automation.Provider.IGridItemProvider>implementację.</span><span class="sxs-lookup"><span data-stu-id="99861-108">Access to individual cell functionality is provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span> <span data-ttu-id="99861-109">Ten wzorzec kontrolki jest analogiczny do <xref:System.Windows.Automation.Provider.IGridItemProvider> rozróżnienia, że jakakolwiek kontrola implementująca <xref:System.Windows.Automation.Provider.ITableItemProvider> musi programowo uwidocznić relację między daną komórką a informacjami o jego wierszu i kolumnie.</span><span class="sxs-lookup"><span data-stu-id="99861-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridItemProvider> with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableItemProvider> must programmatically expose the relationship between the individual cell and its row and column information.</span></span> <span data-ttu-id="99861-110">Aby zapoznać się z przykładami formantów implementujących ten wzorzec kontrolek, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="99861-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="99861-111">Wytyczne i konwencje dotyczące implementacji</span><span class="sxs-lookup"><span data-stu-id="99861-111">Implementation Guidelines and Conventions</span></span>  
  
- <span data-ttu-id="99861-112">Aby zapoznać się z pokrewnymi funkcjami elementów siatki, zobacz [implementowanie wzorca kontrolki GridItem automatyzacji interfejsu użytkownika](implementing-the-ui-automation-griditem-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="99861-112">For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](implementing-the-ui-automation-griditem-control-pattern.md).</span></span>  
  
<a name="Required_Members_for_ITableItemProvider"></a>   
## <a name="required-members-for-itableitemprovider"></a><span data-ttu-id="99861-113">Wymagane elementy członkowskie dla ITableItemProvider</span><span class="sxs-lookup"><span data-stu-id="99861-113">Required Members for ITableItemProvider</span></span>  
  
|<span data-ttu-id="99861-114">Wymagany element członkowski</span><span class="sxs-lookup"><span data-stu-id="99861-114">Required member</span></span>|<span data-ttu-id="99861-115">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="99861-115">Member type</span></span>|<span data-ttu-id="99861-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="99861-116">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|<span data-ttu-id="99861-117">Metoda</span><span class="sxs-lookup"><span data-stu-id="99861-117">Method</span></span>|<span data-ttu-id="99861-118">Brak</span><span class="sxs-lookup"><span data-stu-id="99861-118">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|<span data-ttu-id="99861-119">Metoda</span><span class="sxs-lookup"><span data-stu-id="99861-119">Method</span></span>|<span data-ttu-id="99861-120">Brak</span><span class="sxs-lookup"><span data-stu-id="99861-120">None</span></span>|  
  
 <span data-ttu-id="99861-121">Ten wzorzec kontrolki nie ma skojarzonych właściwości ani zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="99861-121">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="99861-122">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="99861-122">Exceptions</span></span>  
 <span data-ttu-id="99861-123">Ten wzorzec kontrolki nie ma żadnych skojarzonych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="99861-123">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99861-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99861-124">See also</span></span>

- [<span data-ttu-id="99861-125">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="99861-125">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="99861-126">Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="99861-126">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="99861-127">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="99861-127">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="99861-128">Implementacja wzorca kontrolki tabeli automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="99861-128">Implementing the UI Automation Table Control Pattern</span></span>](implementing-the-ui-automation-table-control-pattern.md)
- [<span data-ttu-id="99861-129">Implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="99861-129">Implementing the UI Automation GridItem Control Pattern</span></span>](implementing-the-ui-automation-griditem-control-pattern.md)
- [<span data-ttu-id="99861-130">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="99861-130">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="99861-131">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="99861-131">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
