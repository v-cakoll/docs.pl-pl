---
title: Obsługa automatyzacji interfejsu użytkownika dla typu formantu TreeItem
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Tree Item
- Tree Item control type
- UI Automation, Tree Item control type
ms.assetid: 229f341a-477f-434e-b877-4db9973068eb
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: ec2783e3841a74ddfbca0d719569242ba5e61224
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654987"
---
# <a name="ui-automation-support-for-the-treeitem-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu TreeItem
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pomocy technicznej dla kontrolek typu TreeItem. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ formantu to zestaw warunków, które kontrolki muszą spełnić, aby można było używać <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> właściwości. Warunki obejmują konkretne wskazówki dotyczące [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wartości właściwości i wzorce kontrolki.  
  
 Kontrolek typu TreeItem reprezentuje węzeł w kontenerze drzewa. Każdy węzeł może zawierać innych węzłów o nazwie węzłów podrzędnych. Węzły nadrzędne, albo przez węzły, które zawierają węzły podrzędne mogą być wyświetlane jako rozwinięta czy zwinięta.  
  
 Poniższe sekcje definiują wymagane [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury, właściwości, wzorców kontrolek i zdarzeń dla kontrolek typu TreeItem drzewa. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Wymagania mają zastosowanie do wszystkich formantów element drzewa, czy [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], lub [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Struktura drzewa automatyzacji interfejsu użytkownika wymagane  
 Poniższa tabela przedstawia kontroli i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewo, które odnoszą się do elementu w drzewie kontrolki, a w tym artykule opisano, jakie mogą być zawarte w poszczególnych widokach. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, zobacz [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Formant widoku|Widok zawartości|  
|------------------|------------------|  
|TreeItem<br /><br /> — Pole wyboru (0 lub 1)<br />-Image (0 lub 1)<br />— Przycisk (0 lub 1)<br />— TreeItem (0 lub więcej)|TreeItem<br /><br /> — TreeItem (0 lub więcej)|  
  
 Kontrolki elementu drzewa może mieć zero lub więcej podrzędnych elementów drzewa w widoku zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa. Jeśli kontrolka element drzewa funkcje poza co to jest widoczna w wzorców kontrolek wymienione poniżej, a następnie kontrolki powinna być oparta na danych — typ formantu.  
  
 Zwinięty drzewa elementów nie będą wyświetlane kontrolki widoku lub widok zawartości do momentu stają się rozwinięty i są widoczne (lub, może być przewijane w widoku).  
  
 Wyświetl formant może zawierać dodatkowe szczegóły dla formantu, w tym powiązanego obrazu lub przycisku. Na przykład element w widoku konspektu może zawierać obraz, a także przycisk, aby rozwinąć lub zwinąć konspektu. Te szczegóły obiektów nie pojawiają się w widoku zawartości, ponieważ informacje jest już reprezentowany przez nadrzędny element drzewa. Elementy drzewa, które jest przewijane mieściły się na ekranie pojawi się w kontroli i zawartość widoków [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, a powinien mieć <xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> ma wartość true.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Właściwości automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, których wartość lub definicji jest szczególnie istotne w kontrolkach listy. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Właściwość|Wartość|Uwagi|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz uwagi.|Wartość tej właściwości musi być unikatowa wśród wszystkich kontrolek w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz uwagi.|Najbardziej zewnętrznej prostokąt, który zawiera całą kontrolkę.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz uwagi.|Ta właściwość musi zwracać lokalizacji elementu, który spowoduje, że element, aby zmienić stan zaznaczenia lub stają się fokus.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|TreeItem|Ta wartość jest taka sama dla wszystkich platform tworzenia interfejsu użytkownika.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Prawda|Kontrolka listy zawsze znajduje się w widoku zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Prawda|Kontrolka listy zawsze znajduje się w widoku kontrolnym [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Zobacz uwagi.|Ta właściwość jest równa wskazują, kiedy kontrolki elementu drzewa jest przewijane mieściły się na ekranie.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Zobacz uwagi.|Formant może otrzymywać fokus klawiatury, musi obsługiwać tę właściwość.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Zobacz uwagi.|Jeśli elementu w drzewie używa ikonę wizualizacji wskazująca, że to obiekty określonego typu, ta właściwość musi być obsługiwana i wskazuje obiekt jest.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Drzewo elementów kontrolki są własnym etykietowania.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"element drzewa"|Zlokalizowany ciąg odpowiadający kontrolek typu TreeItem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz uwagi.|Ta właściwość udostępnia tekst wyświetlany dla każdego formantu elementu w drzewie.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Wzorce kontrolek automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolować wzorców, trzeba być obsługiwana przez kontrolki listy. Aby uzyskać więcej informacji na temat wzorców kontrolek, zobacz [Przegląd wzorców kontrolki automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Właściwości wzorzec/wzorzec kontrolki|Obsługa/wartość|Uwagi|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Zależy od|Implementacja tego wzorca kontrolki, jeśli element drzewa ma oddzielne polecenie informacje z możliwością działania.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Tak|Wszystkie elementy drzewa może można rozwijać i zwijać.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|Rozwinięte, zwinięty lub typu liść węzła|Drzewo elementów będzie węzły liści, gdy nie są one rozwinięta czy zwinięta.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Zależy od|Implementacja tego wzorca kontrolki, jeśli kontener drzewa obsługuje wzorca kontrolki przewijania.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Zależy od|Implementacja tego wzorca kontrolki, jeśli jest to możliwe zapewnienie aktywnego zaznaczenia, zachowywane po użytkownik powraca do kontenera drzewa.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider.SelectionContainer%2A>|Tak|Ta właściwość udostępni ten sam kontener dla wszystkich elementów w kontenerze.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Zależy od|Implementacja tego wzorca kontrolki, jeśli element drzewa ma skojarzone pole wyboru.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Właściwości zdarzeń automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia wymagane są obsługiwane przez wszystkie kontrolki elementu w drzewie. Aby uzyskać więcej informacji o zdarzeniach zobacz [Przegląd zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Zdarzenia|Obsługa|Uwagi|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty> Zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Zależy od|Brak|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty> Zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Zależy od|Brak|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Zależy od|Brak|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Zależy od|Brak|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty> Zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> Zdarzenie zmiany właściwości.|Zależy od|Brak|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Automation.ControlType.TreeItem>
- [Typy kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)
- [Przegląd automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-overview.md)
