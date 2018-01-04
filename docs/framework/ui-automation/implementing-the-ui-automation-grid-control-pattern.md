---
title: "Implementacja wzorca formantu siatki automatyzacji interfejsu użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
caps.latest.revision: "27"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4667cd149940310e2422686b9e9fdf6e7e99ca9e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a><span data-ttu-id="ed31e-102">Implementacja wzorca kontrolki siatki automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="ed31e-102">Implementing the UI Automation Grid Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="ed31e-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ed31e-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="ed31e-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="ed31e-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="ed31e-105">W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IGridProvider>, wraz z informacjami dotyczącymi właściwości, metod i zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ed31e-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="ed31e-106">Łącza do dodatkowe informacje są wyświetlane na końcu przeglądu.</span><span class="sxs-lookup"><span data-stu-id="ed31e-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="ed31e-107"><xref:System.Windows.Automation.GridPattern> — Wzorzec formantu jest używana do obsługi formantów, które działają jak kontenery kolekcję elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="ed31e-107">The <xref:System.Windows.Automation.GridPattern> control pattern is used to support controls that act as containers for a collection of child elements.</span></span> <span data-ttu-id="ed31e-108">Elementy podrzędne tego elementu musi implementować <xref:System.Windows.Automation.Provider.IGridItemProvider> i zorganizowane dwuwymiarowa logicznego układu współrzędnych, który można przekształcić według wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="ed31e-108">The children of this element must implement <xref:System.Windows.Automation.Provider.IGridItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span></span> <span data-ttu-id="ed31e-109">Przykłady formantów, które implementują wzorzec tego formantu można znaleźć [formantu wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="ed31e-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="ed31e-110">Implementacja — wskazówki i konwencje</span><span class="sxs-lookup"><span data-stu-id="ed31e-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="ed31e-111">Gdy implementacja wzorca formantu siatki, należy zwrócić uwagę następujące wskazówki i konwencje:</span><span class="sxs-lookup"><span data-stu-id="ed31e-111">When implementing the Grid control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="ed31e-112">Współrzędne siatki są liczony od zera o konieczności współrzędne (0, 0) u góry z lewej (lub górna prawa komórka w zależności od ustawień regionalnych).</span><span class="sxs-lookup"><span data-stu-id="ed31e-112">Grid coordinates are zero-based with the upper left (or upper right cell depending on locale) having coordinates (0, 0).</span></span>  
  
-   <span data-ttu-id="ed31e-113">Jeśli komórka jest pusta, nadal musi zostać zwrócona elementu automatyzacji interfejsu użytkownika w celu zapewnienia obsługi <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> właściwości dla komórki.</span><span class="sxs-lookup"><span data-stu-id="ed31e-113">If a cell is empty, a UI Automation element must still be returned in order to support the <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> property for that cell.</span></span> <span data-ttu-id="ed31e-114">Jest to możliwe, gdy układ elementów podrzędnych siatki jest podobna do tablicy niewyrównane (zobacz poniższy przykład).</span><span class="sxs-lookup"><span data-stu-id="ed31e-114">This is possible when the layout of child elements in the grid is similar to a ragged array (see example below).</span></span>  
  
 <span data-ttu-id="ed31e-115">![Widok Eksploratora Windows z niewyrównanym układem. ] (../../../docs/framework/ui-automation/media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")</span><span class="sxs-lookup"><span data-stu-id="ed31e-115">![Windows Explorer view showing ragged layout.](../../../docs/framework/ui-automation/media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")</span></span>  
<span data-ttu-id="ed31e-116">Przykład formantu siatki o pustym współrzędnych</span><span class="sxs-lookup"><span data-stu-id="ed31e-116">Example of a Grid Control with Empty Coordinates</span></span>  
  
-   <span data-ttu-id="ed31e-117">Siatkę z pojedynczego elementu jest nadal wymagane do zaimplementowania <xref:System.Windows.Automation.Provider.IGridProvider> Jeśli logicznie jest uważany za siatki.</span><span class="sxs-lookup"><span data-stu-id="ed31e-117">A grid with a single item is still required to implement <xref:System.Windows.Automation.Provider.IGridProvider> if it is logically considered to be a grid.</span></span> <span data-ttu-id="ed31e-118">Liczba elementów podrzędnych siatki jest bez znaczenia.</span><span class="sxs-lookup"><span data-stu-id="ed31e-118">The number of child items in the grid is immaterial.</span></span>  
  
-   <span data-ttu-id="ed31e-119">Ukryte wiersze i kolumny, w zależności od implementacji dostawcy mogą być ładowane w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, a w związku z tym zostaną odzwierciedlone w <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> i <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ed31e-119">Hidden rows and columns, depending on the provider implementation, may be loaded in the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree and therefore will be reflected in the <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> and <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> properties.</span></span> <span data-ttu-id="ed31e-120">Jeśli ukryte wiersze i kolumny nie zostały jeszcze zostały załadowane, ich nie powinno być liczone.</span><span class="sxs-lookup"><span data-stu-id="ed31e-120">If the hidden rows and columns have not yet been loaded, they should not be counted.</span></span>  
  
-   <span data-ttu-id="ed31e-121"><xref:System.Windows.Automation.Provider.IGridProvider>nie obsługuje aktywnego manipulowania siatki; <xref:System.Windows.Automation.Provider.ITransformProvider> musi zostać wdrożona, aby włączyć tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="ed31e-121"><xref:System.Windows.Automation.Provider.IGridProvider> does not enable active manipulation of a grid; <xref:System.Windows.Automation.Provider.ITransformProvider> must be implemented to enable this functionality.</span></span>  
  
-   <span data-ttu-id="ed31e-122">Użyj <xref:System.Windows.Automation.StructureChangedEventHandler> do nasłuchiwania zmian strukturalnych lub układ do siatki, takich jak komórki, które zostały dodane, usunięte lub scalone.</span><span class="sxs-lookup"><span data-stu-id="ed31e-122">Use a <xref:System.Windows.Automation.StructureChangedEventHandler> to listen for structural or layout changes to the grid such as cells that have been added, removed, or merged.</span></span>  
  
-   <span data-ttu-id="ed31e-123">Użyj <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> do śledzenia przechodzenie przez elementy lub komórki siatki.</span><span class="sxs-lookup"><span data-stu-id="ed31e-123">Use a <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> to track traversal through the items or cells of a grid.</span></span>  
  
<a name="Required_Members_for_IGridProvider"></a>   
## <a name="required-members-for-igridprovider"></a><span data-ttu-id="ed31e-124">Wymagane elementy IGridProvider</span><span class="sxs-lookup"><span data-stu-id="ed31e-124">Required Members for IGridProvider</span></span>  
 <span data-ttu-id="ed31e-125">Poniższe właściwości i metody są wymagane do implementowania interfejsu IGridProvider.</span><span class="sxs-lookup"><span data-stu-id="ed31e-125">The following properties and methods are required for implementing the IGridProvider interface.</span></span>  
  
|<span data-ttu-id="ed31e-126">Wymagane elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ed31e-126">Required members</span></span>|<span data-ttu-id="ed31e-127">Typ</span><span class="sxs-lookup"><span data-stu-id="ed31e-127">Type</span></span>|<span data-ttu-id="ed31e-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ed31e-128">Notes</span></span>|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>|<span data-ttu-id="ed31e-129">Właściwość</span><span class="sxs-lookup"><span data-stu-id="ed31e-129">Property</span></span>|<span data-ttu-id="ed31e-130">Brak</span><span class="sxs-lookup"><span data-stu-id="ed31e-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>|<span data-ttu-id="ed31e-131">Właściwość</span><span class="sxs-lookup"><span data-stu-id="ed31e-131">Property</span></span>|<span data-ttu-id="ed31e-132">Brak</span><span class="sxs-lookup"><span data-stu-id="ed31e-132">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A>|<span data-ttu-id="ed31e-133">Metoda</span><span class="sxs-lookup"><span data-stu-id="ed31e-133">Method</span></span>|<span data-ttu-id="ed31e-134">Brak</span><span class="sxs-lookup"><span data-stu-id="ed31e-134">None</span></span>|  
  
 <span data-ttu-id="ed31e-135">Wzorzec ten formant nie ma żadnych zdarzeń skojarzone.</span><span class="sxs-lookup"><span data-stu-id="ed31e-135">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="ed31e-136">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="ed31e-136">Exceptions</span></span>  
 <span data-ttu-id="ed31e-137">Dostawców należy zgłosić następujące wyjątki.</span><span class="sxs-lookup"><span data-stu-id="ed31e-137">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="ed31e-138">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="ed31e-138">Exception type</span></span>|<span data-ttu-id="ed31e-139">Warunek</span><span class="sxs-lookup"><span data-stu-id="ed31e-139">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> <span data-ttu-id="ed31e-140">— Jeśli Współrzędna żądanego wiersza jest większy niż <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> lub Współrzędna kolumny jest większa niż <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>.</span><span class="sxs-lookup"><span data-stu-id="ed31e-140">-   If the requested row coordinate is larger than the <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> or the column coordinate is larger than the <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>.</span></span>|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> <span data-ttu-id="ed31e-141">— Jeśli żądany wiersz lub kolumnę współrzędnych jest mniejsza od zera.</span><span class="sxs-lookup"><span data-stu-id="ed31e-141">-   If either of the requested row or column coordinates is less than zero.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ed31e-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ed31e-142">See Also</span></span>  
 [<span data-ttu-id="ed31e-143">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="ed31e-143">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="ed31e-144">Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="ed31e-144">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="ed31e-145">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="ed31e-145">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="ed31e-146">Implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="ed31e-146">Implementing the UI Automation GridItem Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)  
 [<span data-ttu-id="ed31e-147">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="ed31e-147">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="ed31e-148">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="ed31e-148">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
