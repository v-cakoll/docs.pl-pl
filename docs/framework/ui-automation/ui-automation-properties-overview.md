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
# <a name="ui-automation-properties-overview"></a>Przegląd właściwości automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Dostawcy automatyzacji interfejsu użytkownika [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] uwidaczniają właściwości elementów. Te właściwości umożliwiają aplikacjom klienckim automatyzacji interfejsu [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]użytkownika odnajdowanie informacji o elementach , szczególnie formantów, w tym danych statycznych i dynamicznych.  
  
 Ta sekcja zawiera szeroki [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] przegląd właściwości. Bardziej szczegółowe informacje podano w następujących tematach:  
  
- [Właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md)  
  
- [Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera](server-side-ui-automation-provider-implementation.md)  
  
<a name="Property_Identifiers"></a>
## <a name="property-identifiers"></a>Identyfikatory właściwości  
 Każda właściwość jest identyfikowana za pomocą liczby i nazwy. Nazwy właściwości są używane tylko do debugowania i diagnozowania. Dostawcy używają identyfikatorów numerycznych do identyfikowania przychodzących żądań właściwości. Aplikacje klienckie <xref:System.Windows.Automation.AutomationProperty>używają jednak tylko , który hermetyzuje liczbę i nazwę, do identyfikowania właściwości, które chcą pobrać.  
  
 <xref:System.Windows.Automation.AutomationProperty>obiekty reprezentujące określone właściwości są dostępne jako pola w różnych klasach. Ze względów bezpieczeństwa dostawcy automatyzacji interfejsu użytkownika uzyskują te obiekty z oddzielnego zestawu klas, które są zawarte w Uiautomationtypes.dll.  
  
 W poniższej tabeli kategoryzuje właściwości <xref:System.Windows.Automation.AutomationProperty>według klas, które zawierają identyfikatory.  
  
|Rodzaje właściwości|Klienci otrzymują identyfikatory od|Dostawcy otrzymują identyfikatory od|  
|-------------------------|--------------------------|----------------------------|  
|Właściwości wspólne dla wszystkich elementów (patrz poniższe tabele)|<xref:System.Windows.Automation.AutomationElement>|<xref:System.Windows.Automation.AutomationElementIdentifiers>|  
|Położenie okna dokowania|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.DockPatternIdentifiers>|  
|Stan elementu, który można rozwinąć i zwinąć|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers>|  
|Właściwości elementu w siatce|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.GridItemPatternIdentifiers>|  
|Właściwości siatki|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.GridPatternIdentifiers>|  
|Bieżący i obsługiwany widok elementu, który ma wiele widoków|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers>|  
|Właściwości elementu, który przesuwa się nad zakresem wartości, takich jak suwak|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.RangeValuePatternIdentifiers>|  
|Właściwości okna przewijania|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.ScrollPatternIdentifiers>|  
|Stan i kontener elementu, który można wybrać, tak jak na liście|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers>|  
|Właściwości formantu zawierającego elementy zaznaczenia|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.SelectionPatternIdentifiers>|  
|Nagłówki kolumn i wierszy elementu w tabeli|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.TableItemPatternIdentifiers>|  
|Nagłówki kolumn i wierszy oraz orientacja tabeli|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.TablePatternIdentifiers>|  
|Stan kontrolki przełączania|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.TogglePatternIdentifiers>|  
|Możliwości elementu, który można przenosić, obracać lub zmieniać ich nazwy|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.TransformPatternIdentifiers>|  
|Zdolność do wyceny i odczytu/zapisu elementu o wartości|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.ValuePatternIdentifiers>|  
|Możliwości i stan okna|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.WindowPatternIdentifiers>|  
  
<a name="Properties_by_Category"></a>
## <a name="properties-by-category"></a>Właściwości według kategorii  
 W poniższych tabelach kategoryzują właściwości, <xref:System.Windows.Automation.AutomationElement> których <xref:System.Windows.Automation.AutomationElementIdentifiers>identyfikatory znajdują się w pliku . Te właściwości są wspólne dla wszystkich formantów. Wszystkie z nich, z których kilka mogą być statyczne w okresie istnienia aplikacji dostawcy; najbardziej dynamiczne właściwości są skojarzone z wzorców kontroli.  
  
 Kolumna **Dostęp do właściwości** zawiera listę innych programów dostępu dla każdej właściwości, oprócz <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> i <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>. Aby uzyskać więcej informacji na temat uzyskiwania właściwości w aplikacji klienckiej, zobacz [Właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md).  
  
> [!NOTE]
> Aby uzyskać szczegółowe informacje o każdej właściwości, kliknij łącze w kolumnie **Dostęp do właściwości.**  
  
### <a name="display-characteristics"></a>Charakterystyka wyświetlacza  
  
|Identyfikator właściwości|Dostęp do nieruchomości|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>|  
|<xref:System.Windows.Automation.AutomationElement.CultureProperty>|Nie dotyczy|  
|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsOffscreen%2A>|  
|<xref:System.Windows.Automation.AutomationElement.OrientationProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Orientation%2A>|  
  
### <a name="element-type"></a>Typ elementu  
  
|Identyfikator właściwości|Dostęp do nieruchomości|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsContentElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsControlElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LocalizedControlType%2A>|  
  
### <a name="identification"></a>Identyfikacja  
  
|Identyfikator właściwości|Dostęp do nieruchomości|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClassNameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ClassName%2A>|  
|<xref:System.Windows.Automation.AutomationElement.FrameworkIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.FrameworkId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LabeledByProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LabeledBy%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ProcessIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ProcessId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.RuntimeIdProperty>|<xref:System.Windows.Automation.AutomationElement.GetRuntimeId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NativeWindowHandleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.NativeWindowHandle%2A>|  
  
### <a name="interaction"></a>Interakcja  
  
|Identyfikator właściwości|Dostęp do nieruchomości|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AcceleratorKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AccessKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>|<xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>|  
|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HasKeyboardFocus%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsEnabled%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsKeyboardFocusable%2A>|  
  
### <a name="support-for-patterns"></a>Obsługa wzorców  
  
|Identyfikator właściwości|Dostęp do nieruchomości|  
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
  
|Identyfikator właściwości|Dostęp do nieruchomości|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsRequiredForFormProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsRequiredForForm%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsPassword%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemStatusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemStatus%2A>|  
  
<a name="Localization"></a>
## <a name="localization"></a>Lokalizacja  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]dostawcy powinni przedstawić następujące właściwości w języku systemu operacyjnego:  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>  
  
<a name="Properties_and_Events"></a>
## <a name="properties-and-events"></a>Właściwości i zdarzenia  
 Ściśle związany z właściwości w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jest pojęcie zdarzeń zmienionych właściwości. W przypadku właściwości dynamicznych aplikacja kliencka potrzebuje sposobu, aby wiedzieć, że wartość właściwości została zmieniona, dzięki czemu może zaktualizować swoją pamięć podręczną informacji lub reagować na nowe informacje w inny sposób.  
  
 Dostawcy zgłaszają zdarzenia, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] gdy coś się zmienia. Na przykład jeśli pole wyboru jest zaznaczone lub wyczyszczone, zdarzenie zmienione właściwości jest wywoływane przez implementację dostawcy wzorzec przełączania. Dostawcy mogą selektywnie podnosić zdarzenia, w zależności od tego, czy klienci nasłuchują zdarzeń, czy nasłuchują określonych zdarzeń.  
  
 Nie wszystkie zmiany właściwości podnieść zdarzenia; który jest całkowicie do implementacji dostawcy automatyzacji interfejsu użytkownika dla elementu. Na przykład dostawcy standardowego serwera proxy dla pól <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> listy nie zgłaszają zdarzenia, gdy zmiany. W takim przypadku aplikacja zamiast tego <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>musi nasłuchić .  
  
 Klienci nasłuchują zdarzeń, subskrybując je. Subskrybowanie zdarzeń oznacza tworzenie metod delegata, które mogą obsługiwać zdarzenia, a następnie przekazywanie metod [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wraz z określonymi zdarzeniami, które będą rozpatrywane w tych metodach. W szczególności w przypadku zdarzeń zmienionych właściwości klienci muszą zaimplementować <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>.  
  
## <a name="see-also"></a>Zobacz też

- [Buforowanie w klientach automatyzacji interfejsu użytkownika](caching-in-ui-automation-clients.md)
- [Właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md)
- [Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera](server-side-ui-automation-provider-implementation.md)
- [Znajdź element automatyzacji interfejsu użytkownika na podstawie warunku właściwości](find-a-ui-automation-element-based-on-a-property-condition.md)
- [Zwracanie właściwości od dostawcy automatyzacji interfejsu użytkownika](return-properties-from-a-ui-automation-provider.md)
- [Wywoływanie zdarzeń od dostawcy automatyzacji interfejsu użytkownika](raise-events-from-a-ui-automation-provider.md)
