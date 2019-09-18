---
title: Przegląd właściwości automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, properties
- properties, UI Automation
ms.assetid: a6c31d7b-b33e-49b3-b5c1-31a345f9b7c8
ms.openlocfilehash: 59d65601a37c9aba63708748a82fd5e85261b75b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042144"
---
# <a name="ui-automation-properties-overview"></a><span data-ttu-id="75578-102">Przegląd właściwości automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="75578-102">UI Automation Properties Overview</span></span>
> [!NOTE]
> <span data-ttu-id="75578-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="75578-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="75578-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="75578-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="75578-105">Dostawcy automatyzacji interfejsu użytkownika uwidaczniają [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] właściwości w elementach.</span><span class="sxs-lookup"><span data-stu-id="75578-105">UI Automation providers expose properties on [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements.</span></span> <span data-ttu-id="75578-106">Te właściwości umożliwiają aplikacjom klienckim automatyzacji interfejsu użytkownika odnajdywanie informacji o fragmentach [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], zwłaszcza formantów, włącznie z danymi statycznymi i dynamicznymi.</span><span class="sxs-lookup"><span data-stu-id="75578-106">These properties enable UI Automation client applications to discover information about pieces of the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], especially controls, including both static and dynamic data.</span></span>  
  
 <span data-ttu-id="75578-107">Ta sekcja zawiera obszerne omówienie [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] właściwości.</span><span class="sxs-lookup"><span data-stu-id="75578-107">This section gives a broad overview of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] properties.</span></span> <span data-ttu-id="75578-108">Bardziej szczegółowe informacje znajdują się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="75578-108">More specific information is given in the following topics:</span></span>  
  
- [<span data-ttu-id="75578-109">Właściwości automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="75578-109">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)  
  
- [<span data-ttu-id="75578-110">Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera</span><span class="sxs-lookup"><span data-stu-id="75578-110">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)  
  
<a name="Property_Identifiers"></a>   
## <a name="property-identifiers"></a><span data-ttu-id="75578-111">Identyfikatory właściwości</span><span class="sxs-lookup"><span data-stu-id="75578-111">Property Identifiers</span></span>  
 <span data-ttu-id="75578-112">Każda właściwość jest identyfikowana przez liczbę i nazwę.</span><span class="sxs-lookup"><span data-stu-id="75578-112">Every property is identified by a number and a name.</span></span> <span data-ttu-id="75578-113">Nazwy właściwości są używane tylko do debugowania i diagnostyki.</span><span class="sxs-lookup"><span data-stu-id="75578-113">The names of properties are used only for debugging and diagnosis.</span></span> <span data-ttu-id="75578-114">Dostawcy używają identyfikatorów liczbowych do identyfikowania przychodzących żądań właściwości.</span><span class="sxs-lookup"><span data-stu-id="75578-114">Providers use the numeric IDs to identify incoming property requests.</span></span> <span data-ttu-id="75578-115">Jednak <xref:System.Windows.Automation.AutomationProperty>aplikacje klienckie, które hermetyzują liczbę i nazwę, identyfikują właściwości, które chcą pobrać.</span><span class="sxs-lookup"><span data-stu-id="75578-115">Client applications, however, only use <xref:System.Windows.Automation.AutomationProperty>, which encapsulates the number and name, to identify properties they wish to retrieve.</span></span>  
  
 <span data-ttu-id="75578-116"><xref:System.Windows.Automation.AutomationProperty>obiekty reprezentujące określone właściwości są dostępne jako pola w różnych klasach.</span><span class="sxs-lookup"><span data-stu-id="75578-116"><xref:System.Windows.Automation.AutomationProperty> objects representing particular properties are available as fields in various classes.</span></span> <span data-ttu-id="75578-117">Ze względów bezpieczeństwa dostawcy automatyzacji interfejsu użytkownika uzyskują te obiekty z oddzielnego zestawu klas, które są zawarte w UIAutomationTypes. dll.</span><span class="sxs-lookup"><span data-stu-id="75578-117">For security reasons, UI Automation providers obtain these objects from a separate set of classes that are contained in Uiautomationtypes.dll.</span></span>  
  
 <span data-ttu-id="75578-118">Poniższa tabela zawiera kategorie właściwości według klas, które zawierają <xref:System.Windows.Automation.AutomationProperty>identyfikatory.</span><span class="sxs-lookup"><span data-stu-id="75578-118">The following table categorizes properties by the classes that contain the <xref:System.Windows.Automation.AutomationProperty>IDs.</span></span>  
  
|<span data-ttu-id="75578-119">Rodzaje właściwości</span><span class="sxs-lookup"><span data-stu-id="75578-119">Kinds of properties</span></span>|<span data-ttu-id="75578-120">Klienci otrzymują identyfikatory z</span><span class="sxs-lookup"><span data-stu-id="75578-120">Clients get IDs from</span></span>|<span data-ttu-id="75578-121">Dostawcy pobierają identyfikatory z</span><span class="sxs-lookup"><span data-stu-id="75578-121">Providers get IDs from</span></span>|  
|-------------------------|--------------------------|----------------------------|  
|<span data-ttu-id="75578-122">Właściwości wspólne dla wszystkich elementów (zobacz następujące tabele)</span><span class="sxs-lookup"><span data-stu-id="75578-122">Properties common to all elements (see following tables)</span></span>|<xref:System.Windows.Automation.AutomationElement>|<xref:System.Windows.Automation.AutomationElementIdentifiers>|  
|<span data-ttu-id="75578-123">Pozycja okna dokującego</span><span class="sxs-lookup"><span data-stu-id="75578-123">Position of a docking window</span></span>|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.DockPatternIdentifiers>|  
|<span data-ttu-id="75578-124">Stan elementu, który można rozwinąć i zwinąć</span><span class="sxs-lookup"><span data-stu-id="75578-124">State of an element that can expand and collapse</span></span>|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers>|  
|<span data-ttu-id="75578-125">Właściwości elementu w siatce</span><span class="sxs-lookup"><span data-stu-id="75578-125">Properties of an item in a grid</span></span>|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.GridItemPatternIdentifiers>|  
|<span data-ttu-id="75578-126">Właściwości siatki</span><span class="sxs-lookup"><span data-stu-id="75578-126">Properties of a grid</span></span>|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.GridPatternIdentifiers>|  
|<span data-ttu-id="75578-127">Bieżący i obsługiwany widok elementu, który ma wiele widoków</span><span class="sxs-lookup"><span data-stu-id="75578-127">Current and supported view of an element that has multiple views</span></span>|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers>|  
|<span data-ttu-id="75578-128">Właściwości elementu, który przenosi się na zakres wartości, na przykład suwak</span><span class="sxs-lookup"><span data-stu-id="75578-128">Properties of an element that moves over a range of values, such as a slider</span></span>|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.RangeValuePatternIdentifiers>|  
|<span data-ttu-id="75578-129">Właściwości okna przewijania</span><span class="sxs-lookup"><span data-stu-id="75578-129">Properties of a scrolling window</span></span>|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.ScrollPatternIdentifiers>|  
|<span data-ttu-id="75578-130">Stan i kontener elementu, który można wybrać, jak na liście</span><span class="sxs-lookup"><span data-stu-id="75578-130">Status and container of an item that can be selected, as in a list</span></span>|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers>|  
|<span data-ttu-id="75578-131">Właściwości kontrolki zawierającej elementy zaznaczenia</span><span class="sxs-lookup"><span data-stu-id="75578-131">Properties of a control that contains selection items</span></span>|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.SelectionPatternIdentifiers>|  
|<span data-ttu-id="75578-132">Nagłówki kolumn i wierszy elementu w tabeli</span><span class="sxs-lookup"><span data-stu-id="75578-132">Column and row headers of an item in a table</span></span>|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.TableItemPatternIdentifiers>|  
|<span data-ttu-id="75578-133">Nagłówki kolumn i wierszy oraz orientacja tabeli</span><span class="sxs-lookup"><span data-stu-id="75578-133">Column and row headers, and orientation, of a table</span></span>|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.TablePatternIdentifiers>|  
|<span data-ttu-id="75578-134">Stan kontrolki przełączania</span><span class="sxs-lookup"><span data-stu-id="75578-134">State of a toggle control</span></span>|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.TogglePatternIdentifiers>|  
|<span data-ttu-id="75578-135">Możliwości elementu, który można przenieść, obrócić lub zmienić jego rozmiar</span><span class="sxs-lookup"><span data-stu-id="75578-135">Capabilities of an element that can be moved, rotated, or resized</span></span>|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.TransformPatternIdentifiers>|  
|<span data-ttu-id="75578-136">Możliwości wartości i odczytu/zapisu elementu, który ma wartość</span><span class="sxs-lookup"><span data-stu-id="75578-136">Value and read/write capabilities of an element that has a value</span></span>|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.ValuePatternIdentifiers>|  
|<span data-ttu-id="75578-137">Możliwości i stan okna</span><span class="sxs-lookup"><span data-stu-id="75578-137">Capabilities and state of a window</span></span>|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.WindowPatternIdentifiers>|  
  
<a name="Properties_by_Category"></a>   
## <a name="properties-by-category"></a><span data-ttu-id="75578-138">Właściwości według kategorii</span><span class="sxs-lookup"><span data-stu-id="75578-138">Properties by Category</span></span>  
 <span data-ttu-id="75578-139">W poniższych tabelach wymieniono właściwości, których identyfikatory znajdują się <xref:System.Windows.Automation.AutomationElement> w <xref:System.Windows.Automation.AutomationElementIdentifiers>i.</span><span class="sxs-lookup"><span data-stu-id="75578-139">The following tables categorize the properties whose IDs are found in <xref:System.Windows.Automation.AutomationElement> and <xref:System.Windows.Automation.AutomationElementIdentifiers>.</span></span> <span data-ttu-id="75578-140">Te właściwości są wspólne dla wszystkich kontrolek.</span><span class="sxs-lookup"><span data-stu-id="75578-140">These properties are common to all controls.</span></span> <span data-ttu-id="75578-141">Wszystkie oprócz kilku z nich mogą być statyczne w okresie istnienia aplikacji dostawcy. Większość właściwości dynamicznych jest skojarzonych ze wzorcami kontrolek.</span><span class="sxs-lookup"><span data-stu-id="75578-141">All but a few of them are likely to be static over the lifetime of the provider application; most dynamic properties are associated with control patterns.</span></span>  
  
 <span data-ttu-id="75578-142">W kolumnie **dostęp do właściwości** są wyświetlane wszystkie inne metody dostępu dla każdej właściwości, a <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> także <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>do i.</span><span class="sxs-lookup"><span data-stu-id="75578-142">The **Property Access** column lists any other accessors for each property, in addition to <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> and <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>.</span></span> <span data-ttu-id="75578-143">Aby uzyskać więcej informacji na temat pobierania właściwości w aplikacji klienckiej, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md).</span><span class="sxs-lookup"><span data-stu-id="75578-143">For more information on getting properties in a client application, see [UI Automation Properties for Clients](ui-automation-properties-for-clients.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="75578-144">Aby uzyskać szczegółowe informacje na temat każdej właściwości, Użyj linku w kolumnie **dostęp do właściwości** .</span><span class="sxs-lookup"><span data-stu-id="75578-144">For specific information about each property, follow the link in the **Property Access** column.</span></span>  
  
### <a name="display-characteristics"></a><span data-ttu-id="75578-145">Właściwości wyświetlania</span><span class="sxs-lookup"><span data-stu-id="75578-145">Display Characteristics</span></span>  
  
|<span data-ttu-id="75578-146">Identyfikator właściwości</span><span class="sxs-lookup"><span data-stu-id="75578-146">Property identifier</span></span>|<span data-ttu-id="75578-147">Dostęp do właściwości</span><span class="sxs-lookup"><span data-stu-id="75578-147">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>|  
|<xref:System.Windows.Automation.AutomationElement.CultureProperty>|<span data-ttu-id="75578-148">n/d</span><span class="sxs-lookup"><span data-stu-id="75578-148">n/a</span></span>|  
|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsOffscreen%2A>|  
|<xref:System.Windows.Automation.AutomationElement.OrientationProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Orientation%2A>|  
  
### <a name="element-type"></a><span data-ttu-id="75578-149">{1&gt;Element Type&lt;1}</span><span class="sxs-lookup"><span data-stu-id="75578-149">Element Type</span></span>  
  
|<span data-ttu-id="75578-150">Identyfikator właściwości</span><span class="sxs-lookup"><span data-stu-id="75578-150">Property identifier</span></span>|<span data-ttu-id="75578-151">Dostęp do właściwości</span><span class="sxs-lookup"><span data-stu-id="75578-151">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsContentElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsControlElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LocalizedControlType%2A>|  
  
### <a name="identification"></a><span data-ttu-id="75578-152">Identyfikatora</span><span class="sxs-lookup"><span data-stu-id="75578-152">Identification</span></span>  
  
|<span data-ttu-id="75578-153">Identyfikator właściwości</span><span class="sxs-lookup"><span data-stu-id="75578-153">Property identifier</span></span>|<span data-ttu-id="75578-154">Dostęp do właściwości</span><span class="sxs-lookup"><span data-stu-id="75578-154">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClassNameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ClassName%2A>|  
|<xref:System.Windows.Automation.AutomationElement.FrameworkIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.FrameworkId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LabeledByProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LabeledBy%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ProcessIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ProcessId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.RuntimeIdProperty>|<xref:System.Windows.Automation.AutomationElement.GetRuntimeId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NativeWindowHandleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.NativeWindowHandle%2A>|  
  
### <a name="interaction"></a><span data-ttu-id="75578-155">Interakcji</span><span class="sxs-lookup"><span data-stu-id="75578-155">Interaction</span></span>  
  
|<span data-ttu-id="75578-156">Identyfikator właściwości</span><span class="sxs-lookup"><span data-stu-id="75578-156">Property identifier</span></span>|<span data-ttu-id="75578-157">Dostęp do właściwości</span><span class="sxs-lookup"><span data-stu-id="75578-157">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AcceleratorKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AccessKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>|<xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>|  
|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HasKeyboardFocus%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsEnabled%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsKeyboardFocusable%2A>|  
  
### <a name="support-for-patterns"></a><span data-ttu-id="75578-158">Obsługa wzorców</span><span class="sxs-lookup"><span data-stu-id="75578-158">Support for Patterns</span></span>  
  
|<span data-ttu-id="75578-159">Identyfikator właściwości</span><span class="sxs-lookup"><span data-stu-id="75578-159">Property identifier</span></span>|<span data-ttu-id="75578-160">Dostęp do właściwości</span><span class="sxs-lookup"><span data-stu-id="75578-160">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsDockPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsExpandCollapsePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsGridItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsGridPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsInvokePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsMultipleViewPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsRangeValuePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsScrollItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsScrollPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsSelectionItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsSelectionPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTableItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTablePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTogglePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTransformPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsValuePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsWindowPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
  
### <a name="miscellaneous"></a><span data-ttu-id="75578-161">Różne</span><span class="sxs-lookup"><span data-stu-id="75578-161">Miscellaneous</span></span>  
  
|<span data-ttu-id="75578-162">Identyfikator właściwości</span><span class="sxs-lookup"><span data-stu-id="75578-162">Property identifier</span></span>|<span data-ttu-id="75578-163">Dostęp do właściwości</span><span class="sxs-lookup"><span data-stu-id="75578-163">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsRequiredForFormProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsRequiredForForm%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsPassword%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemStatusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemStatus%2A>|  
  
<a name="Localization"></a>   
## <a name="localization"></a><span data-ttu-id="75578-164">Lokalizacja</span><span class="sxs-lookup"><span data-stu-id="75578-164">Localization</span></span>  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="75578-165">dostawcy powinni przedstawić następujące właściwości w języku systemu operacyjnego:</span><span class="sxs-lookup"><span data-stu-id="75578-165">providers should present the following properties in the language of the operating system:</span></span>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>  
  
<a name="Properties_and_Events"></a>   
## <a name="properties-and-events"></a><span data-ttu-id="75578-166">Właściwości i zdarzenia</span><span class="sxs-lookup"><span data-stu-id="75578-166">Properties and Events</span></span>  
 <span data-ttu-id="75578-167">Ściśle powiązane z właściwościami w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] to koncepcja zdarzeń zmieniających właściwości.</span><span class="sxs-lookup"><span data-stu-id="75578-167">Closely tied in with the properties in [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is the concept of property-changed events.</span></span> <span data-ttu-id="75578-168">W przypadku właściwości dynamicznych aplikacja kliencka musi wiedzieć, że wartość właściwości została zmieniona, dzięki czemu może ona aktualizować pamięć podręczną informacji lub reagować na nowe informacje w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="75578-168">For dynamic properties, the client application needs a way to know that a property value has changed, so that it can update its cache of information or react to the new information in some other way.</span></span>  
  
 <span data-ttu-id="75578-169">Dostawcy zgłaszają zdarzenia, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] gdy coś w zmianach.</span><span class="sxs-lookup"><span data-stu-id="75578-169">Providers raise events when something in the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] changes.</span></span> <span data-ttu-id="75578-170">Na przykład jeśli pole wyboru jest zaznaczone lub wyczyszczone, zdarzenie zmiany właściwości jest zgłaszane przez implementację wzorca przełączania przez dostawcę.</span><span class="sxs-lookup"><span data-stu-id="75578-170">For example, if a check box is selected or cleared, a property-changed event is raised by the provider's implementation of the Toggle pattern.</span></span> <span data-ttu-id="75578-171">Dostawcy mogą wybiórczo zgłaszać zdarzenia w zależności od tego, czy klienci oczekują na zdarzenia, czy nasłuchują określonych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="75578-171">Providers can raise events selectively, depending on whether any clients are listening for events, or listening for specific events.</span></span>  
  
 <span data-ttu-id="75578-172">Nie wszystkie zmiany właściwości powodują wystąpienie zdarzeń; jest to całkowicie do implementacji dostawcy automatyzacji interfejsu użytkownika dla elementu.</span><span class="sxs-lookup"><span data-stu-id="75578-172">Not all property changes raise events; that is entirely up to the implementation of the UI Automation provider for the element.</span></span> <span data-ttu-id="75578-173">Na przykład standardowy dostawca proxy dla pól listy nie zgłasza zdarzenia po <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> wprowadzeniu zmian.</span><span class="sxs-lookup"><span data-stu-id="75578-173">For example, the standard proxy providers for list boxes do not raise an event when the <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> changes.</span></span> <span data-ttu-id="75578-174">W takim przypadku aplikacja musi nasłuchiwać przez <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>.</span><span class="sxs-lookup"><span data-stu-id="75578-174">In this case, the application instead must listen for an <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>.</span></span>  
  
 <span data-ttu-id="75578-175">Klienci nasłuchują zdarzeń, subskrybując je.</span><span class="sxs-lookup"><span data-stu-id="75578-175">Clients listen for events by subscribing to them.</span></span> <span data-ttu-id="75578-176">Subskrybowanie zdarzeń oznacza utworzenie metod delegatów, które mogą obsłużyć zdarzenia, a następnie przekazanie metod do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] określonych zdarzeń, które będą rozpatrywane w tych metodach.</span><span class="sxs-lookup"><span data-stu-id="75578-176">Subscribing to events means creating delegate methods that can handle the events, and then passing the methods to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] along with the specific events that will be dealt with in those methods.</span></span> <span data-ttu-id="75578-177">W szczególności dla zdarzeń ze zmienionymi właściwościami klienci muszą <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="75578-177">For property-changed events in particular, clients must implement <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75578-178">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75578-178">See also</span></span>

- [<span data-ttu-id="75578-179">Buforowanie w klientach automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="75578-179">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
- [<span data-ttu-id="75578-180">Właściwości automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="75578-180">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)
- [<span data-ttu-id="75578-181">Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera</span><span class="sxs-lookup"><span data-stu-id="75578-181">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
- [<span data-ttu-id="75578-182">Znajdź element automatyzacji interfejsu użytkownika na podstawie warunku właściwości</span><span class="sxs-lookup"><span data-stu-id="75578-182">Find a UI Automation Element Based on a Property Condition</span></span>](find-a-ui-automation-element-based-on-a-property-condition.md)
- [<span data-ttu-id="75578-183">Zwracanie właściwości od dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="75578-183">Return Properties from a UI Automation Provider</span></span>](return-properties-from-a-ui-automation-provider.md)
- [<span data-ttu-id="75578-184">Wywoływanie zdarzeń od dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="75578-184">Raise Events from a UI Automation Provider</span></span>](raise-events-from-a-ui-automation-provider.md)
