---
title: Przegląd właściwości automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, properties
- properties, UI Automation
ms.assetid: a6c31d7b-b33e-49b3-b5c1-31a345f9b7c8
ms.openlocfilehash: 8a44fd89017002ae51d9b15a22bac97668d0ff90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179869"
---
# <a name="ui-automation-properties-overview"></a><span data-ttu-id="4cce0-102">Przegląd właściwości automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="4cce0-102">UI Automation Properties Overview</span></span>
> [!NOTE]
> <span data-ttu-id="4cce0-103">Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="4cce0-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="4cce0-104">Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="4cce0-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="4cce0-105">Dostawcy automatyzacji interfejsu użytkownika [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] uwidaczniają właściwości elementów.</span><span class="sxs-lookup"><span data-stu-id="4cce0-105">UI Automation providers expose properties on [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements.</span></span> <span data-ttu-id="4cce0-106">Te właściwości umożliwiają aplikacjom klienckim automatyzacji interfejsu [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]użytkownika odnajdowanie informacji o elementach , szczególnie formantów, w tym danych statycznych i dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="4cce0-106">These properties enable UI Automation client applications to discover information about pieces of the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], especially controls, including both static and dynamic data.</span></span>  
  
 <span data-ttu-id="4cce0-107">Ta sekcja zawiera szeroki [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] przegląd właściwości.</span><span class="sxs-lookup"><span data-stu-id="4cce0-107">This section gives a broad overview of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] properties.</span></span> <span data-ttu-id="4cce0-108">Bardziej szczegółowe informacje podano w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="4cce0-108">More specific information is given in the following topics:</span></span>  
  
- [<span data-ttu-id="4cce0-109">Właściwości automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="4cce0-109">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)  
  
- [<span data-ttu-id="4cce0-110">Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera</span><span class="sxs-lookup"><span data-stu-id="4cce0-110">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)  
  
<a name="Property_Identifiers"></a>
## <a name="property-identifiers"></a><span data-ttu-id="4cce0-111">Identyfikatory właściwości</span><span class="sxs-lookup"><span data-stu-id="4cce0-111">Property Identifiers</span></span>  
 <span data-ttu-id="4cce0-112">Każda właściwość jest identyfikowana za pomocą liczby i nazwy.</span><span class="sxs-lookup"><span data-stu-id="4cce0-112">Every property is identified by a number and a name.</span></span> <span data-ttu-id="4cce0-113">Nazwy właściwości są używane tylko do debugowania i diagnozowania.</span><span class="sxs-lookup"><span data-stu-id="4cce0-113">The names of properties are used only for debugging and diagnosis.</span></span> <span data-ttu-id="4cce0-114">Dostawcy używają identyfikatorów numerycznych do identyfikowania przychodzących żądań właściwości.</span><span class="sxs-lookup"><span data-stu-id="4cce0-114">Providers use the numeric IDs to identify incoming property requests.</span></span> <span data-ttu-id="4cce0-115">Aplikacje klienckie <xref:System.Windows.Automation.AutomationProperty>używają jednak tylko , który hermetyzuje liczbę i nazwę, do identyfikowania właściwości, które chcą pobrać.</span><span class="sxs-lookup"><span data-stu-id="4cce0-115">Client applications, however, only use <xref:System.Windows.Automation.AutomationProperty>, which encapsulates the number and name, to identify properties they wish to retrieve.</span></span>  
  
 <span data-ttu-id="4cce0-116"><xref:System.Windows.Automation.AutomationProperty>obiekty reprezentujące określone właściwości są dostępne jako pola w różnych klasach.</span><span class="sxs-lookup"><span data-stu-id="4cce0-116"><xref:System.Windows.Automation.AutomationProperty> objects representing particular properties are available as fields in various classes.</span></span> <span data-ttu-id="4cce0-117">Ze względów bezpieczeństwa dostawcy automatyzacji interfejsu użytkownika uzyskują te obiekty z oddzielnego zestawu klas, które są zawarte w Uiautomationtypes.dll.</span><span class="sxs-lookup"><span data-stu-id="4cce0-117">For security reasons, UI Automation providers obtain these objects from a separate set of classes that are contained in Uiautomationtypes.dll.</span></span>  
  
 <span data-ttu-id="4cce0-118">W poniższej tabeli kategoryzuje właściwości <xref:System.Windows.Automation.AutomationProperty>według klas, które zawierają identyfikatory.</span><span class="sxs-lookup"><span data-stu-id="4cce0-118">The following table categorizes properties by the classes that contain the <xref:System.Windows.Automation.AutomationProperty>IDs.</span></span>  
  
|<span data-ttu-id="4cce0-119">Rodzaje właściwości</span><span class="sxs-lookup"><span data-stu-id="4cce0-119">Kinds of properties</span></span>|<span data-ttu-id="4cce0-120">Klienci otrzymują identyfikatory od</span><span class="sxs-lookup"><span data-stu-id="4cce0-120">Clients get IDs from</span></span>|<span data-ttu-id="4cce0-121">Dostawcy otrzymują identyfikatory od</span><span class="sxs-lookup"><span data-stu-id="4cce0-121">Providers get IDs from</span></span>|  
|-------------------------|--------------------------|----------------------------|  
|<span data-ttu-id="4cce0-122">Właściwości wspólne dla wszystkich elementów (patrz poniższe tabele)</span><span class="sxs-lookup"><span data-stu-id="4cce0-122">Properties common to all elements (see following tables)</span></span>|<xref:System.Windows.Automation.AutomationElement>|<xref:System.Windows.Automation.AutomationElementIdentifiers>|  
|<span data-ttu-id="4cce0-123">Położenie okna dokowania</span><span class="sxs-lookup"><span data-stu-id="4cce0-123">Position of a docking window</span></span>|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.DockPatternIdentifiers>|  
|<span data-ttu-id="4cce0-124">Stan elementu, który można rozwinąć i zwinąć</span><span class="sxs-lookup"><span data-stu-id="4cce0-124">State of an element that can expand and collapse</span></span>|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers>|  
|<span data-ttu-id="4cce0-125">Właściwości elementu w siatce</span><span class="sxs-lookup"><span data-stu-id="4cce0-125">Properties of an item in a grid</span></span>|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.GridItemPatternIdentifiers>|  
|<span data-ttu-id="4cce0-126">Właściwości siatki</span><span class="sxs-lookup"><span data-stu-id="4cce0-126">Properties of a grid</span></span>|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.GridPatternIdentifiers>|  
|<span data-ttu-id="4cce0-127">Bieżący i obsługiwany widok elementu, który ma wiele widoków</span><span class="sxs-lookup"><span data-stu-id="4cce0-127">Current and supported view of an element that has multiple views</span></span>|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers>|  
|<span data-ttu-id="4cce0-128">Właściwości elementu, który przesuwa się nad zakresem wartości, takich jak suwak</span><span class="sxs-lookup"><span data-stu-id="4cce0-128">Properties of an element that moves over a range of values, such as a slider</span></span>|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.RangeValuePatternIdentifiers>|  
|<span data-ttu-id="4cce0-129">Właściwości okna przewijania</span><span class="sxs-lookup"><span data-stu-id="4cce0-129">Properties of a scrolling window</span></span>|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.ScrollPatternIdentifiers>|  
|<span data-ttu-id="4cce0-130">Stan i kontener elementu, który można wybrać, tak jak na liście</span><span class="sxs-lookup"><span data-stu-id="4cce0-130">Status and container of an item that can be selected, as in a list</span></span>|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers>|  
|<span data-ttu-id="4cce0-131">Właściwości formantu zawierającego elementy zaznaczenia</span><span class="sxs-lookup"><span data-stu-id="4cce0-131">Properties of a control that contains selection items</span></span>|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.SelectionPatternIdentifiers>|  
|<span data-ttu-id="4cce0-132">Nagłówki kolumn i wierszy elementu w tabeli</span><span class="sxs-lookup"><span data-stu-id="4cce0-132">Column and row headers of an item in a table</span></span>|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.TableItemPatternIdentifiers>|  
|<span data-ttu-id="4cce0-133">Nagłówki kolumn i wierszy oraz orientacja tabeli</span><span class="sxs-lookup"><span data-stu-id="4cce0-133">Column and row headers, and orientation, of a table</span></span>|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.TablePatternIdentifiers>|  
|<span data-ttu-id="4cce0-134">Stan kontrolki przełączania</span><span class="sxs-lookup"><span data-stu-id="4cce0-134">State of a toggle control</span></span>|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.TogglePatternIdentifiers>|  
|<span data-ttu-id="4cce0-135">Możliwości elementu, który można przenosić, obracać lub zmieniać ich nazwy</span><span class="sxs-lookup"><span data-stu-id="4cce0-135">Capabilities of an element that can be moved, rotated, or resized</span></span>|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.TransformPatternIdentifiers>|  
|<span data-ttu-id="4cce0-136">Zdolność do wyceny i odczytu/zapisu elementu o wartości</span><span class="sxs-lookup"><span data-stu-id="4cce0-136">Value and read/write capabilities of an element that has a value</span></span>|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.ValuePatternIdentifiers>|  
|<span data-ttu-id="4cce0-137">Możliwości i stan okna</span><span class="sxs-lookup"><span data-stu-id="4cce0-137">Capabilities and state of a window</span></span>|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.WindowPatternIdentifiers>|  
  
<a name="Properties_by_Category"></a>
## <a name="properties-by-category"></a><span data-ttu-id="4cce0-138">Właściwości według kategorii</span><span class="sxs-lookup"><span data-stu-id="4cce0-138">Properties by Category</span></span>  
 <span data-ttu-id="4cce0-139">W poniższych tabelach kategoryzują właściwości, <xref:System.Windows.Automation.AutomationElement> których <xref:System.Windows.Automation.AutomationElementIdentifiers>identyfikatory znajdują się w pliku .</span><span class="sxs-lookup"><span data-stu-id="4cce0-139">The following tables categorize the properties whose IDs are found in <xref:System.Windows.Automation.AutomationElement> and <xref:System.Windows.Automation.AutomationElementIdentifiers>.</span></span> <span data-ttu-id="4cce0-140">Te właściwości są wspólne dla wszystkich formantów.</span><span class="sxs-lookup"><span data-stu-id="4cce0-140">These properties are common to all controls.</span></span> <span data-ttu-id="4cce0-141">Wszystkie z nich, z których kilka mogą być statyczne w okresie istnienia aplikacji dostawcy; najbardziej dynamiczne właściwości są skojarzone z wzorców kontroli.</span><span class="sxs-lookup"><span data-stu-id="4cce0-141">All but a few of them are likely to be static over the lifetime of the provider application; most dynamic properties are associated with control patterns.</span></span>  
  
 <span data-ttu-id="4cce0-142">Kolumna **Dostęp do właściwości** zawiera listę innych programów dostępu dla każdej właściwości, oprócz <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> i <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="4cce0-142">The **Property Access** column lists any other accessors for each property, in addition to <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> and <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>.</span></span> <span data-ttu-id="4cce0-143">Aby uzyskać więcej informacji na temat uzyskiwania właściwości w aplikacji klienckiej, zobacz [Właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md).</span><span class="sxs-lookup"><span data-stu-id="4cce0-143">For more information on getting properties in a client application, see [UI Automation Properties for Clients](ui-automation-properties-for-clients.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4cce0-144">Aby uzyskać szczegółowe informacje o każdej właściwości, kliknij łącze w kolumnie **Dostęp do właściwości.**</span><span class="sxs-lookup"><span data-stu-id="4cce0-144">For specific information about each property, follow the link in the **Property Access** column.</span></span>  
  
### <a name="display-characteristics"></a><span data-ttu-id="4cce0-145">Charakterystyka wyświetlacza</span><span class="sxs-lookup"><span data-stu-id="4cce0-145">Display Characteristics</span></span>  
  
|<span data-ttu-id="4cce0-146">Identyfikator właściwości</span><span class="sxs-lookup"><span data-stu-id="4cce0-146">Property identifier</span></span>|<span data-ttu-id="4cce0-147">Dostęp do nieruchomości</span><span class="sxs-lookup"><span data-stu-id="4cce0-147">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>|  
|<xref:System.Windows.Automation.AutomationElement.CultureProperty>|<span data-ttu-id="4cce0-148">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="4cce0-148">n/a</span></span>|  
|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsOffscreen%2A>|  
|<xref:System.Windows.Automation.AutomationElement.OrientationProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Orientation%2A>|  
  
### <a name="element-type"></a><span data-ttu-id="4cce0-149">Typ elementu</span><span class="sxs-lookup"><span data-stu-id="4cce0-149">Element Type</span></span>  
  
|<span data-ttu-id="4cce0-150">Identyfikator właściwości</span><span class="sxs-lookup"><span data-stu-id="4cce0-150">Property identifier</span></span>|<span data-ttu-id="4cce0-151">Dostęp do nieruchomości</span><span class="sxs-lookup"><span data-stu-id="4cce0-151">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsContentElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsControlElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LocalizedControlType%2A>|  
  
### <a name="identification"></a><span data-ttu-id="4cce0-152">Identyfikacja</span><span class="sxs-lookup"><span data-stu-id="4cce0-152">Identification</span></span>  
  
|<span data-ttu-id="4cce0-153">Identyfikator właściwości</span><span class="sxs-lookup"><span data-stu-id="4cce0-153">Property identifier</span></span>|<span data-ttu-id="4cce0-154">Dostęp do nieruchomości</span><span class="sxs-lookup"><span data-stu-id="4cce0-154">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClassNameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ClassName%2A>|  
|<xref:System.Windows.Automation.AutomationElement.FrameworkIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.FrameworkId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LabeledByProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LabeledBy%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ProcessIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ProcessId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.RuntimeIdProperty>|<xref:System.Windows.Automation.AutomationElement.GetRuntimeId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NativeWindowHandleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.NativeWindowHandle%2A>|  
  
### <a name="interaction"></a><span data-ttu-id="4cce0-155">Interakcja</span><span class="sxs-lookup"><span data-stu-id="4cce0-155">Interaction</span></span>  
  
|<span data-ttu-id="4cce0-156">Identyfikator właściwości</span><span class="sxs-lookup"><span data-stu-id="4cce0-156">Property identifier</span></span>|<span data-ttu-id="4cce0-157">Dostęp do nieruchomości</span><span class="sxs-lookup"><span data-stu-id="4cce0-157">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AcceleratorKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AccessKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>|<xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>|  
|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HasKeyboardFocus%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsEnabled%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsKeyboardFocusable%2A>|  
  
### <a name="support-for-patterns"></a><span data-ttu-id="4cce0-158">Obsługa wzorców</span><span class="sxs-lookup"><span data-stu-id="4cce0-158">Support for Patterns</span></span>  
  
|<span data-ttu-id="4cce0-159">Identyfikator właściwości</span><span class="sxs-lookup"><span data-stu-id="4cce0-159">Property identifier</span></span>|<span data-ttu-id="4cce0-160">Dostęp do nieruchomości</span><span class="sxs-lookup"><span data-stu-id="4cce0-160">Property access</span></span>|  
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
  
### <a name="miscellaneous"></a><span data-ttu-id="4cce0-161">Różne</span><span class="sxs-lookup"><span data-stu-id="4cce0-161">Miscellaneous</span></span>  
  
|<span data-ttu-id="4cce0-162">Identyfikator właściwości</span><span class="sxs-lookup"><span data-stu-id="4cce0-162">Property identifier</span></span>|<span data-ttu-id="4cce0-163">Dostęp do nieruchomości</span><span class="sxs-lookup"><span data-stu-id="4cce0-163">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsRequiredForFormProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsRequiredForForm%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsPassword%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemStatusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemStatus%2A>|  
  
<a name="Localization"></a>
## <a name="localization"></a><span data-ttu-id="4cce0-164">Lokalizacja</span><span class="sxs-lookup"><span data-stu-id="4cce0-164">Localization</span></span>  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="4cce0-165">dostawcy powinni przedstawić następujące właściwości w języku systemu operacyjnego:</span><span class="sxs-lookup"><span data-stu-id="4cce0-165">providers should present the following properties in the language of the operating system:</span></span>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>  
  
<a name="Properties_and_Events"></a>
## <a name="properties-and-events"></a><span data-ttu-id="4cce0-166">Właściwości i zdarzenia</span><span class="sxs-lookup"><span data-stu-id="4cce0-166">Properties and Events</span></span>  
 <span data-ttu-id="4cce0-167">Ściśle związany z właściwości w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jest pojęcie zdarzeń zmienionych właściwości.</span><span class="sxs-lookup"><span data-stu-id="4cce0-167">Closely tied in with the properties in [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is the concept of property-changed events.</span></span> <span data-ttu-id="4cce0-168">W przypadku właściwości dynamicznych aplikacja kliencka potrzebuje sposobu, aby wiedzieć, że wartość właściwości została zmieniona, dzięki czemu może zaktualizować swoją pamięć podręczną informacji lub reagować na nowe informacje w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="4cce0-168">For dynamic properties, the client application needs a way to know that a property value has changed, so that it can update its cache of information or react to the new information in some other way.</span></span>  
  
 <span data-ttu-id="4cce0-169">Dostawcy zgłaszają zdarzenia, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] gdy coś się zmienia.</span><span class="sxs-lookup"><span data-stu-id="4cce0-169">Providers raise events when something in the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] changes.</span></span> <span data-ttu-id="4cce0-170">Na przykład jeśli pole wyboru jest zaznaczone lub wyczyszczone, zdarzenie zmienione właściwości jest wywoływane przez implementację dostawcy wzorzec przełączania.</span><span class="sxs-lookup"><span data-stu-id="4cce0-170">For example, if a check box is selected or cleared, a property-changed event is raised by the provider's implementation of the Toggle pattern.</span></span> <span data-ttu-id="4cce0-171">Dostawcy mogą selektywnie podnosić zdarzenia, w zależności od tego, czy klienci nasłuchują zdarzeń, czy nasłuchują określonych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4cce0-171">Providers can raise events selectively, depending on whether any clients are listening for events, or listening for specific events.</span></span>  
  
 <span data-ttu-id="4cce0-172">Nie wszystkie zmiany właściwości podnieść zdarzenia; który jest całkowicie do implementacji dostawcy automatyzacji interfejsu użytkownika dla elementu.</span><span class="sxs-lookup"><span data-stu-id="4cce0-172">Not all property changes raise events; that is entirely up to the implementation of the UI Automation provider for the element.</span></span> <span data-ttu-id="4cce0-173">Na przykład dostawcy standardowego serwera proxy dla pól <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> listy nie zgłaszają zdarzenia, gdy zmiany.</span><span class="sxs-lookup"><span data-stu-id="4cce0-173">For example, the standard proxy providers for list boxes do not raise an event when the <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> changes.</span></span> <span data-ttu-id="4cce0-174">W takim przypadku aplikacja zamiast tego <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>musi nasłuchić .</span><span class="sxs-lookup"><span data-stu-id="4cce0-174">In this case, the application instead must listen for an <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>.</span></span>  
  
 <span data-ttu-id="4cce0-175">Klienci nasłuchują zdarzeń, subskrybując je.</span><span class="sxs-lookup"><span data-stu-id="4cce0-175">Clients listen for events by subscribing to them.</span></span> <span data-ttu-id="4cce0-176">Subskrybowanie zdarzeń oznacza tworzenie metod delegata, które mogą obsługiwać zdarzenia, a następnie przekazywanie metod [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wraz z określonymi zdarzeniami, które będą rozpatrywane w tych metodach.</span><span class="sxs-lookup"><span data-stu-id="4cce0-176">Subscribing to events means creating delegate methods that can handle the events, and then passing the methods to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] along with the specific events that will be dealt with in those methods.</span></span> <span data-ttu-id="4cce0-177">W szczególności w przypadku zdarzeń zmienionych właściwości klienci muszą zaimplementować <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="4cce0-177">For property-changed events in particular, clients must implement <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cce0-178">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4cce0-178">See also</span></span>

- [<span data-ttu-id="4cce0-179">Buforowanie w klientach automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="4cce0-179">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
- [<span data-ttu-id="4cce0-180">Właściwości automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="4cce0-180">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)
- [<span data-ttu-id="4cce0-181">Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera</span><span class="sxs-lookup"><span data-stu-id="4cce0-181">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
- [<span data-ttu-id="4cce0-182">Znajdź element automatyzacji interfejsu użytkownika na podstawie warunku właściwości</span><span class="sxs-lookup"><span data-stu-id="4cce0-182">Find a UI Automation Element Based on a Property Condition</span></span>](find-a-ui-automation-element-based-on-a-property-condition.md)
- [<span data-ttu-id="4cce0-183">Zwracanie właściwości od dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="4cce0-183">Return Properties from a UI Automation Provider</span></span>](return-properties-from-a-ui-automation-provider.md)
- [<span data-ttu-id="4cce0-184">Wywoływanie zdarzeń od dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="4cce0-184">Raise Events from a UI Automation Provider</span></span>](raise-events-from-a-ui-automation-provider.md)
