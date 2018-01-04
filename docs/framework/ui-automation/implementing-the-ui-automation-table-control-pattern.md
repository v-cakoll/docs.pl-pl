---
title: "Implementacja wzorca formantu tabeli automatyzacji interfejsu użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
caps.latest.revision: "19"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 1e0b3c09948b53363888ae133cd0c4d9f9ae8f05
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a><span data-ttu-id="90f0b-102">Implementacja wzorca kontrolki tabeli automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="90f0b-102">Implementing the UI Automation Table Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="90f0b-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="90f0b-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="90f0b-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="90f0b-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="90f0b-105">W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.ITableProvider>, wraz z informacjami dotyczącymi właściwości, metod i zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="90f0b-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="90f0b-106">Łącza do dodatkowe informacje są wyświetlane na końcu przeglądu.</span><span class="sxs-lookup"><span data-stu-id="90f0b-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="90f0b-107"><xref:System.Windows.Automation.TablePattern> — Wzorzec formantu jest używana do obsługi formantów, które działają jak kontenery kolekcję elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="90f0b-107">The <xref:System.Windows.Automation.TablePattern> control pattern is used to support controls that act as containers for a collection of child elements.</span></span> <span data-ttu-id="90f0b-108">Elementy podrzędne tego elementu musi implementować <xref:System.Windows.Automation.Provider.ITableItemProvider> i zorganizowane dwuwymiarowa logicznego układu współrzędnych, który można przekształcić według wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="90f0b-108">The children of this element must implement <xref:System.Windows.Automation.Provider.ITableItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span></span> <span data-ttu-id="90f0b-109">Ten wzorzec kontroli jest odpowiednikiem <xref:System.Windows.Automation.Provider.IGridProvider>, z rozróżnienie żadnego kontroli wykonania <xref:System.Windows.Automation.Provider.ITableProvider> również musi ujawniać relacji nagłówek kolumny i/lub wiersz dla każdego elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="90f0b-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridProvider>, with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableProvider> must also expose a column and/or row header relationship for each child element.</span></span> <span data-ttu-id="90f0b-110">Przykłady formantów, które implementują wzorzec tego formantu można znaleźć [formantu wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="90f0b-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="90f0b-111">Implementacja — wskazówki i konwencje</span><span class="sxs-lookup"><span data-stu-id="90f0b-111">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="90f0b-112">Gdy implementacja wzorca formantu tabeli, należy zwrócić uwagę następujące wskazówki i konwencje:</span><span class="sxs-lookup"><span data-stu-id="90f0b-112">When implementing the Table control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="90f0b-113">Dostęp do zawartości komórki jest za pośrednictwem dwuwymiarowa współrzędnych logicznych lub tablicy podał wymagane wdrożenia równoczesnych <xref:System.Windows.Automation.Provider.IGridProvider>.</span><span class="sxs-lookup"><span data-stu-id="90f0b-113">Access to the content of individual cells is through a two-dimensional logical coordinate system or array provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span>  
  
-   <span data-ttu-id="90f0b-114">Nagłówek kolumny lub wiersza mogą być zawarte w obiekcie tabeli lub być obiekt oddzielny nagłówek, który jest skojarzony z obiektem tabeli.</span><span class="sxs-lookup"><span data-stu-id="90f0b-114">A column or row header can be contained within a table object or be a separate header object that is associated with a table object.</span></span>  
  
-   <span data-ttu-id="90f0b-115">Nagłówki kolumn i wierszy może obejmować zarówno nagłówek podstawowy, jak i wszelkie nagłówki pomocniczych.</span><span class="sxs-lookup"><span data-stu-id="90f0b-115">Column and row headers may include both a primary header as well as any supporting headers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="90f0b-116">To pojęcie staje się widoczna w [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] arkusza kalkulacyjnego, w którym zdefiniowany przez użytkownika kolumny "Imię".</span><span class="sxs-lookup"><span data-stu-id="90f0b-116">This concept becomes evident in a [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] spreadsheet where a user has defined a "First name" column.</span></span> <span data-ttu-id="90f0b-117">Ta kolumna zawiera teraz dwa nagłówki — nagłówek "Imię" zdefiniowany przez użytkownika i oznaczenie alfanumeryczne dla tej kolumny przypisane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="90f0b-117">This column now has two headers—the "First name" header defined by the user and the alphanumeric designation for that column assigned by the application.</span></span>  
  
-   <span data-ttu-id="90f0b-118">Zobacz [implementacja wzorca formantu siatki automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md) siatki powiązanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="90f0b-118">See [Implementing the UI Automation Grid Control Pattern](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md) for related grid functionality.</span></span>  
  
 <span data-ttu-id="90f0b-119">![Tabela ze złożonymi elementami nagłówka. ] (../../../docs/framework/ui-automation/media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span><span class="sxs-lookup"><span data-stu-id="90f0b-119">![Table with complex header items.](../../../docs/framework/ui-automation/media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span></span>  
<span data-ttu-id="90f0b-120">Przykład tabeli z nagłówkami kolumn złożonych</span><span class="sxs-lookup"><span data-stu-id="90f0b-120">Example of a Table with Complex Column Headers</span></span>  
  
 <span data-ttu-id="90f0b-121">![Tabela z niejednoznaczną właściwością RowOrColumnMajor. ] (../../../docs/framework/ui-automation/media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span><span class="sxs-lookup"><span data-stu-id="90f0b-121">![Table with ambiguous RowOrColumnMajor property.](../../../docs/framework/ui-automation/media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span></span>  
<span data-ttu-id="90f0b-122">Przykład tabeli z niejednoznaczną właściwością RowOrColumnMajor</span><span class="sxs-lookup"><span data-stu-id="90f0b-122">Example of a Table with Ambiguous RowOrColumnMajor Property</span></span>  
  
<a name="Required_Members_for_ITableProvider"></a>   
## <a name="required-members-for-itableprovider"></a><span data-ttu-id="90f0b-123">Wymagane elementy ITableProvider</span><span class="sxs-lookup"><span data-stu-id="90f0b-123">Required Members for ITableProvider</span></span>  
 <span data-ttu-id="90f0b-124">Poniższe właściwości i metody są wymagane dla interfejsu ITableProvider.</span><span class="sxs-lookup"><span data-stu-id="90f0b-124">The following properties and methods are required for the ITableProvider interface.</span></span>  
  
|<span data-ttu-id="90f0b-125">Wymagane elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="90f0b-125">Required members</span></span>|<span data-ttu-id="90f0b-126">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="90f0b-126">Member type</span></span>|<span data-ttu-id="90f0b-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="90f0b-127">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|<span data-ttu-id="90f0b-128">Właściwość</span><span class="sxs-lookup"><span data-stu-id="90f0b-128">Property</span></span>|<span data-ttu-id="90f0b-129">Brak</span><span class="sxs-lookup"><span data-stu-id="90f0b-129">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|<span data-ttu-id="90f0b-130">Metoda</span><span class="sxs-lookup"><span data-stu-id="90f0b-130">Method</span></span>|<span data-ttu-id="90f0b-131">Brak</span><span class="sxs-lookup"><span data-stu-id="90f0b-131">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|<span data-ttu-id="90f0b-132">Metoda</span><span class="sxs-lookup"><span data-stu-id="90f0b-132">Method</span></span>|<span data-ttu-id="90f0b-133">Brak</span><span class="sxs-lookup"><span data-stu-id="90f0b-133">None</span></span>|  
  
 <span data-ttu-id="90f0b-134">Wzorzec ten formant nie ma żadnych zdarzeń skojarzone.</span><span class="sxs-lookup"><span data-stu-id="90f0b-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="90f0b-135">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="90f0b-135">Exceptions</span></span>  
 <span data-ttu-id="90f0b-136">Ten wzorzec formantu ma bez wyjątków skojarzone.</span><span class="sxs-lookup"><span data-stu-id="90f0b-136">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90f0b-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="90f0b-137">See Also</span></span>  
 [<span data-ttu-id="90f0b-138">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="90f0b-138">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="90f0b-139">Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="90f0b-139">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="90f0b-140">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="90f0b-140">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="90f0b-141">Implementacja wzorca kontrolki TableItem dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="90f0b-141">Implementing the UI Automation TableItem Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-tableitem-control-pattern.md)  
 [<span data-ttu-id="90f0b-142">Implementacja wzorca kontrolki siatki automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="90f0b-142">Implementing the UI Automation Grid Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)  
 [<span data-ttu-id="90f0b-143">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="90f0b-143">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="90f0b-144">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="90f0b-144">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
