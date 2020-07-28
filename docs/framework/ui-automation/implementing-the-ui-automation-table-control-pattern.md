---
title: Implementacja wzorca formantu tabeli automatyzacji interfejsu użytkownika
description: Zapoznaj się z wytycznymi i konwencjami w celu zaimplementowania wzorca kontrolki tabeli w automatyzacji interfejsu użytkownika. Znajomość wymaganych członków interfejsu ITableProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
ms.openlocfilehash: e88ddee04ba887daf1929d855526cd0d062f78d5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168235"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a><span data-ttu-id="0f1d6-104">Implementacja wzorca formantu tabeli automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="0f1d6-104">Implementing the UI Automation Table Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="0f1d6-105">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0f1d6-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="0f1d6-106">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="0f1d6-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="0f1d6-107">W tym temacie przedstawiono wskazówki i konwencje dotyczące wdrażania <xref:System.Windows.Automation.Provider.ITableProvider> , w tym informacje o właściwościach, metodach i zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="0f1d6-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="0f1d6-108">Linki do dodatkowych odwołań znajdują się na końcu przeglądu.</span><span class="sxs-lookup"><span data-stu-id="0f1d6-108">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="0f1d6-109"><xref:System.Windows.Automation.TablePattern>Wzorzec kontrolki służy do obsługi kontrolek, które działają jako kontenery dla kolekcji elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="0f1d6-109">The <xref:System.Windows.Automation.TablePattern> control pattern is used to support controls that act as containers for a collection of child elements.</span></span> <span data-ttu-id="0f1d6-110">Elementy podrzędne tego elementu muszą implementować <xref:System.Windows.Automation.Provider.ITableItemProvider> i być zorganizowane w dwuwymiarowej logicznej układzie współrzędnych, który może być przesunięty przez wiersz i kolumnę.</span><span class="sxs-lookup"><span data-stu-id="0f1d6-110">The children of this element must implement <xref:System.Windows.Automation.Provider.ITableItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span></span> <span data-ttu-id="0f1d6-111">Ten wzorzec kontrolki jest analogiczny do <xref:System.Windows.Automation.Provider.IGridProvider> , z rozróżnieniem, że jakakolwiek kontrolka implementująca <xref:System.Windows.Automation.Provider.ITableProvider> musi także uwidaczniać relację nagłówka kolumny i/lub wiersza dla każdego elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="0f1d6-111">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridProvider>, with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableProvider> must also expose a column and/or row header relationship for each child element.</span></span> <span data-ttu-id="0f1d6-112">Aby zapoznać się z przykładami formantów implementujących ten wzorzec kontrolek, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="0f1d6-112">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="0f1d6-113">Wytyczne i konwencje dotyczące implementacji</span><span class="sxs-lookup"><span data-stu-id="0f1d6-113">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="0f1d6-114">Podczas implementowania wzorca kontroli tabeli należy zwrócić uwagę na następujące wytyczne i konwencje:</span><span class="sxs-lookup"><span data-stu-id="0f1d6-114">When implementing the Table control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="0f1d6-115">Dostęp do zawartości poszczególnych komórek odbywa się za pomocą dwuwymiarowego układu współrzędnych lub tablicy udostępnionej przez wymaganą współbieżną implementację <xref:System.Windows.Automation.Provider.IGridProvider> .</span><span class="sxs-lookup"><span data-stu-id="0f1d6-115">Access to the content of individual cells is through a two-dimensional logical coordinate system or array provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span>  
  
- <span data-ttu-id="0f1d6-116">Nagłówek kolumny lub wiersza może być zawarty w obiekcie tabeli lub być osobnym obiektem nagłówkowym skojarzonym z obiektem tabeli.</span><span class="sxs-lookup"><span data-stu-id="0f1d6-116">A column or row header can be contained within a table object or be a separate header object that is associated with a table object.</span></span>  
  
- <span data-ttu-id="0f1d6-117">Nagłówki kolumn i wierszy mogą zawierać zarówno nagłówek podstawowy, jak i nagłówki pomocnicze.</span><span class="sxs-lookup"><span data-stu-id="0f1d6-117">Column and row headers may include both a primary header as well as any supporting headers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f1d6-118">Pojęcie to jest widoczne w arkuszu kalkulacyjnym programu Microsoft Excel, w którym użytkownik zdefiniował kolumnę "imię Name".</span><span class="sxs-lookup"><span data-stu-id="0f1d6-118">This concept becomes evident in a Microsoft Excel spreadsheet where a user has defined a "First name" column.</span></span> <span data-ttu-id="0f1d6-119">Ta kolumna ma teraz dwa nagłówki — nagłówek "First Name" zdefiniowany przez użytkownika i alfanumeryczne oznaczenie tej kolumny przypisanej przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="0f1d6-119">This column now has two headers—the "First name" header defined by the user and the alphanumeric designation for that column assigned by the application.</span></span>  
  
- <span data-ttu-id="0f1d6-120">Zobacz [Implementacja wzorca kontrolki siatki automatyzacji interfejsu użytkownika](implementing-the-ui-automation-grid-control-pattern.md) dla powiązanych funkcji siatki.</span><span class="sxs-lookup"><span data-stu-id="0f1d6-120">See [Implementing the UI Automation Grid Control Pattern](implementing-the-ui-automation-grid-control-pattern.md) for related grid functionality.</span></span>  
  
 <span data-ttu-id="0f1d6-121">![Tabela ze złożonymi elementami nagłówka.](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span><span class="sxs-lookup"><span data-stu-id="0f1d6-121">![Table with complex header items.](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span></span>  
<span data-ttu-id="0f1d6-122">Przykład tabeli z złożonymi nagłówkami kolumn</span><span class="sxs-lookup"><span data-stu-id="0f1d6-122">Example of a Table with Complex Column Headers</span></span>  
  
 <span data-ttu-id="0f1d6-123">![Tabela z niejednoznaczną właściwością RowOrColumnMajor.](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span><span class="sxs-lookup"><span data-stu-id="0f1d6-123">![Table with ambiguous RowOrColumnMajor property.](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span></span>  
<span data-ttu-id="0f1d6-124">Przykład tabeli z niejednoznaczną właściwością RowOrColumnMajor</span><span class="sxs-lookup"><span data-stu-id="0f1d6-124">Example of a Table with Ambiguous RowOrColumnMajor Property</span></span>  
  
<a name="Required_Members_for_ITableProvider"></a>
## <a name="required-members-for-itableprovider"></a><span data-ttu-id="0f1d6-125">Wymagane elementy członkowskie dla ITableProvider</span><span class="sxs-lookup"><span data-stu-id="0f1d6-125">Required Members for ITableProvider</span></span>  
 <span data-ttu-id="0f1d6-126">Dla interfejsu ITableProvider są wymagane następujące właściwości i metody.</span><span class="sxs-lookup"><span data-stu-id="0f1d6-126">The following properties and methods are required for the ITableProvider interface.</span></span>  
  
|<span data-ttu-id="0f1d6-127">Wymagane elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="0f1d6-127">Required members</span></span>|<span data-ttu-id="0f1d6-128">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="0f1d6-128">Member type</span></span>|<span data-ttu-id="0f1d6-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0f1d6-129">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|<span data-ttu-id="0f1d6-130">Właściwość</span><span class="sxs-lookup"><span data-stu-id="0f1d6-130">Property</span></span>|<span data-ttu-id="0f1d6-131">Brak</span><span class="sxs-lookup"><span data-stu-id="0f1d6-131">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|<span data-ttu-id="0f1d6-132">Metoda</span><span class="sxs-lookup"><span data-stu-id="0f1d6-132">Method</span></span>|<span data-ttu-id="0f1d6-133">Brak</span><span class="sxs-lookup"><span data-stu-id="0f1d6-133">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|<span data-ttu-id="0f1d6-134">Metoda</span><span class="sxs-lookup"><span data-stu-id="0f1d6-134">Method</span></span>|<span data-ttu-id="0f1d6-135">Brak</span><span class="sxs-lookup"><span data-stu-id="0f1d6-135">None</span></span>|  
  
 <span data-ttu-id="0f1d6-136">Ten wzorzec kontrolki nie ma skojarzonych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0f1d6-136">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="0f1d6-137">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="0f1d6-137">Exceptions</span></span>  
 <span data-ttu-id="0f1d6-138">Ten wzorzec kontrolki nie ma żadnych skojarzonych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="0f1d6-138">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f1d6-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f1d6-139">See also</span></span>

- [<span data-ttu-id="0f1d6-140">Wzorce formantów automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="0f1d6-140">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="0f1d6-141">Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="0f1d6-141">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="0f1d6-142">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="0f1d6-142">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="0f1d6-143">Implementacja wzorca kontrolki TableItem dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="0f1d6-143">Implementing the UI Automation TableItem Control Pattern</span></span>](implementing-the-ui-automation-tableitem-control-pattern.md)
- [<span data-ttu-id="0f1d6-144">Implementacja wzorca kontrolki siatki automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="0f1d6-144">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="0f1d6-145">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="0f1d6-145">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="0f1d6-146">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="0f1d6-146">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
