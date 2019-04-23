---
title: Przegląd właściwości automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, properties
- properties, UI Automation
ms.assetid: a6c31d7b-b33e-49b3-b5c1-31a345f9b7c8
ms.openlocfilehash: 9028f9f99ee22dd480d817bc8aa94c7113a15c9d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223007"
---
# <a name="ui-automation-properties-overview"></a>Przegląd właściwości automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Dostawcy automatyzacji interfejsu użytkownika udostępnianie właściwości na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elementów. Właściwości te umożliwiają aplikacjom klienta automatyzacji interfejsu użytkownika do odnajdywania informacji na temat rodzajów [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], szczególnie kontroluje obiekt, włącznie z danymi statyczne i dynamiczne.  
  
 W tej sekcji przedstawiono ogólne omówienie [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] właściwości. Więcej informacji znajduje się w następujących tematach:  
  
-   [Właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)  
  
-   [Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)  
  
<a name="Property_Identifiers"></a>   
## <a name="property-identifiers"></a>Identyfikatory właściwości  
 Dla każdej właściwości jest identyfikowany przez numer i nazwę. Nazwy właściwości są używane tylko w przypadku debugowania i diagnostyki. Dostawcy używają numeryczne [!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)] do identyfikowania żądań przychodzących właściwości. Aplikacje klienckie, jednak używać tylko <xref:System.Windows.Automation.AutomationProperty>, która hermetyzuje numeru i nazwy, aby zidentyfikować właściwości chcesz pobrać.  
  
 <xref:System.Windows.Automation.AutomationProperty> obiektów reprezentujących szczególne właściwości są dostępne jako pola w różnych klas. Ze względów bezpieczeństwa dostawcy automatyzacji interfejsu użytkownika, należy uzyskać te obiekty z oddzielny zestaw klas, które są zawarte w Uiautomationtypes.dll.  
  
 Poniższa tabela kategoryzuje właściwości według klasy, które zawierają <xref:System.Windows.Automation.AutomationProperty> [!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)].  
  
|Typy właściwości|Identyfikatory z pobierania przez klientów|Dostawców pobrać identyfikatorów z|  
|-------------------------|--------------------------|----------------------------|  
|Właściwości wspólne dla wszystkich elementów (zobacz poniższy tabel)|<xref:System.Windows.Automation.AutomationElement>|<xref:System.Windows.Automation.AutomationElementIdentifiers>|  
|Położenie okna dokującego.|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.DockPatternIdentifiers>|  
|Stan elementu, który można rozwijać i zwijać|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers>|  
|Właściwości elementu w siatce|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.GridItemPatternIdentifiers>|  
|Właściwości siatki|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.GridPatternIdentifiers>|  
|Wyświetl bieżące i obsługiwane elementu, który ma wiele widoków|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers>|  
|Właściwości elementu, który przechodzi przez zakres wartości, takich jak suwaka|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.RangeValuePatternIdentifiers>|  
|Właściwości okna przewijania|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.ScrollPatternIdentifiers>|  
|Stan i kontener elementu, który można wybrać, jak w list|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers>|  
|Właściwości kontrolki, która zawiera elementy zaznaczenia|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.SelectionPatternIdentifiers>|  
|Nagłówki kolumn i wierszy elementu w tabeli|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.TableItemPatternIdentifiers>|  
|Nagłówki kolumn i wierszy i orientację w tabeli.|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.TablePatternIdentifiers>|  
|Stan formantu przełączania|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.TogglePatternIdentifiers>|  
|Możliwości element, który można przenieść, obracać lub zmiany rozmiaru|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.TransformPatternIdentifiers>|  
|Możliwości odczytu/zapisu i wartość elementu, który ma wartość|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.ValuePatternIdentifiers>|  
|Możliwości i stan okna|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.WindowPatternIdentifiers>|  
  
<a name="Properties_by_Category"></a>   
## <a name="properties-by-category"></a>Właściwości według kategorii  
 Poniższe tabele kategoryzowanie właściwości którego [!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)] znajdują się w <xref:System.Windows.Automation.AutomationElement> i <xref:System.Windows.Automation.AutomationElementIdentifiers>. Te właściwości są wspólne dla wszystkich kontrolek. Wszystkie z wyjątkiem kilku z nich mogą zostać statycznych w okresie istnienia aplikacji dostawcy; właściwości dynamiczne najczęściej są skojarzone z wzorców kontrolek.  
  
 **Dostęp do właściwości** kolumna zawiera inne metody dostępu dla każdej właściwości w uzupełnieniu do <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> i <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>. Aby uzyskać więcej informacji na temat pobierania właściwości w aplikacji klienckiej, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
> [!NOTE]
>  Aby uzyskać szczegółowe informacje o każdej właściwości, kliknij link w **dostęp do właściwości** kolumny.  
  
### <a name="display-characteristics"></a>Display Characteristics  
  
|Identyfikator właściwości|Dostęp do właściwości|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>|  
|<xref:System.Windows.Automation.AutomationElement.CultureProperty>|n/d|  
|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsOffscreen%2A>|  
|<xref:System.Windows.Automation.AutomationElement.OrientationProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Orientation%2A>|  
  
### <a name="element-type"></a>{1&gt;Element Type&lt;1}  
  
|Identyfikator właściwości|Dostęp do właściwości|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsContentElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsControlElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LocalizedControlType%2A>|  
  
### <a name="identification"></a>Identyfikacja  
  
|Identyfikator właściwości|Dostęp do właściwości|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClassNameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ClassName%2A>|  
|<xref:System.Windows.Automation.AutomationElement.FrameworkIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.FrameworkId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LabeledByProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LabeledBy%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ProcessIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ProcessId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.RuntimeIdProperty>|<xref:System.Windows.Automation.AutomationElement.GetRuntimeId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NativeWindowHandleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.NativeWindowHandle%2A>|  
  
### <a name="interaction"></a>Interakcji  
  
|Identyfikator właściwości|Dostęp do właściwości|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AcceleratorKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AccessKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>|<xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>|  
|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HasKeyboardFocus%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsEnabled%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsKeyboardFocusable%2A>|  
  
### <a name="support-for-patterns"></a>Obsługa wzorców  
  
|Identyfikator właściwości|Dostęp do właściwości|  
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
  
### <a name="miscellaneous"></a>Różne  
  
|Identyfikator właściwości|Dostęp do właściwości|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsRequiredForFormProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsRequiredForForm%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsPassword%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemStatusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemStatus%2A>|  
  
<a name="Localization"></a>   
## <a name="localization"></a>Lokalizacja  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dostawcy powinni przedstawić potwierdzenie odpowiedniego następujące właściwości w języku systemu operacyjnego:  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>  
  
<a name="Properties_and_Events"></a>   
## <a name="properties-and-events"></a>Właściwości i zdarzenia  
 Ściśle powiązane za pomocą właściwości w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pojęcie zdarzenia zmiany właściwości. Dla właściwości dynamicznych aplikacja kliencka musi jakoś dowiedzieć się, że wartość właściwości została zmieniona, tak, aby go zaktualizować pamięci podręcznej informacji lub reagowanie na nowe informacje w inny sposób.  
  
 Dostawców wywoływać zdarzenia, gdy element [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] zmiany. Na przykład jeśli pole wyboru lub odznaczane, to zdarzenie zmiany właściwości jest wywoływane przez implementację dostawcy wzorca przełącznika. Dostawców może wywoływać zdarzenia selektywnie, w zależności od tego, czy wszyscy klienci są nasłuchiwanie zdarzeń lub nasłuchiwania dla określonych zdarzeń.  
  
 Nie wszystkie zmiany właściwości wywoływanie zdarzeń; która zależy od całkowicie implementacja dostawcy automatyzacji interfejsu użytkownika dla elementu. Na przykład dostawców standardowy serwer proxy dla pól listy nieznakowe inicjują zdarzenia podczas <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> zmiany. W takim przypadku aplikacji zamiast musi nasłuchiwać <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>.  
  
 Klienci nasłuchiwać zdarzeń, subskrybując je. Subskrybowanie zdarzeń oznacza, że tworzenie metod delegatów, które może obsłużyć zdarzenia, a następnie przekazywanie metody służące do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wraz z określonych zdarzeń, które zostanie omówione w tych metodach. Dla zdarzenia zmiany właściwości w szczególności, klienci muszą implementować <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>.  
  
## <a name="see-also"></a>Zobacz także

- [Buforowanie w klientach automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
- [Właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)
- [Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
- [Znajdź element automatyzacji interfejsu użytkownika na podstawie warunku właściwości](../../../docs/framework/ui-automation/find-a-ui-automation-element-based-on-a-property-condition.md)
- [Zwracanie właściwości od dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/return-properties-from-a-ui-automation-provider.md)
- [Wywoływanie zdarzeń od dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/raise-events-from-a-ui-automation-provider.md)
