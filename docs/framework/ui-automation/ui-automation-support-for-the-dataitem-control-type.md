---
title: Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu DataItem
description: Uzyskaj informacje na temat obsługi automatyzacji interfejsu użytkownika dla typu formantu elementu danych. Poznaj wymaganą strukturę drzewa, właściwości, wzorce formantów i zdarzenia.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Data Item control type
- Data Item control type
- control types, Data Item
ms.assetid: 181708fd-2595-4c43-9abd-75811627d64c
ms.openlocfilehash: c1b149e1033303e98bd150e62c6344b60eec1f93
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167983"
---
# <a name="ui-automation-support-for-the-dataitem-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu DataItem
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Ten temat zawiera informacje o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] obsłudze typu formantu elementu danych. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] typie formantu jest zestaw warunków, które formant musi spełniać, aby można było użyć <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> właściwości. Warunki obejmują określone wytyczne dotyczące [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wartości właściwości i wzorców formantów.  
  
 Wpis na liście kontaktów to przykład kontrolki elementu danych. Kontrolka elementu danych zawiera informacje, które są istotne dla użytkownika końcowego. Jest to bardziej skomplikowane niż prosta pozycja listy, ponieważ zawiera bogatsze informacje.  
  
 W poniższych sekcjach opisano wymaganą [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strukturę drzewa, właściwości, wzorce formantów i zdarzenia dla typu formantu elementu danych. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Wymagania dotyczą wszystkich kontrolek elementów danych, zarówno [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] systemu Win32, jak i Windows Forms.  
  
## <a name="required-ui-automation-tree-structure"></a>Wymagana struktura drzewa automatyzacji interfejsu użytkownika  
 W poniższej tabeli przedstawiono widok kontrolki i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, które odnoszą się do kontrolek elementów danych i opisano, co może być zawarte w poszczególnych widokach. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, zobacz [Omówienie drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Widok kontrolki drzewa|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Drzewo — widok zawartości|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|Elementu<br /><br /> — Różne (0 lub więcej; mogą być uporządkowane w hierarchii)|Elementu<br /><br /> — Różne (0 lub więcej; mogą być uporządkowane w hierarchii)|  
  
 Element element danych w siatce danych może obsługiwać wiele obiektów, w tym inną warstwę elementów danych lub konkretne elementy siatki, takie jak tekst, obrazy lub kontrolki edycji. Jeśli element danych ma określoną rolę obiektu, element powinien być uwidoczniony jako określony typ kontroli; na przykład typ kontrolki elementu listy dla elementów danych, które można wybrać w siatce.  
  
## <a name="required-ui-automation-properties"></a>Wymagane właściwości automatyzacji interfejsu użytkownika  
 Poniższa tabela zawiera listę właściwości, których wartość lub definicja jest szczególnie istotna dla kontrolek elementu danych. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md).  
  
|Właściwość|Wartość|Uwagi|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz uwagi.|Wartość tej właściwości musi być unikatowa dla wszystkich kontrolek w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz uwagi.|Najbardziej zewnętrzny prostokąt, który zawiera cały formant.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz uwagi.|Obsługiwane, jeśli istnieje prostokąt ograniczający. Jeśli nie każdy punkt wewnątrz prostokąta ograniczenia jest klikany, a będziesz wykonywał wyspecjalizowane Testy trafień, a następnie przesłonić i udostępnić punkt kliknięcia.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Elementu|Ta wartość jest taka sama dla wszystkich platform interfejsu użytkownika.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Prawda|Formant elementu danych musi zawsze mieć wartość Content.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Prawda|Formant elementu danych musi być zawsze kontrolką.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Zobacz uwagi.|Jeśli formant może odbierać fokus klawiatury, musi obsługiwać tę właściwość.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>|Zobacz uwagi.|Jeśli formant zawiera stan, który jest aktualizowany dynamicznie, ta właściwość musi być obsługiwana, aby technologia pomocnicza mogła otrzymywać aktualizacje po zmianie stanu elementu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Zobacz uwagi.|Jest to wartość ciągu, która przekazuje użytkownikowi końcowemu obiekt, który reprezentuje element. Przykłady to "plik multimedialny" lub "kontakt".|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Kontrolki elementów danych nie mają statycznej etykiety tekstowej.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"element danych"|Zlokalizowany ciąg odpowiadający typowi formantu elementu danych.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz uwagi.|Kontrolka element danych zawsze zawiera podstawowy element tekstowy, który odnosi się do tego, co użytkownik może skojarzyć jako największą semantykę dla elementu.|  
  
## <a name="required-ui-automation-control-patterns"></a>Wymagane wzorce kontrolek automatyzacji interfejsu użytkownika  
 Poniższa tabela zawiera listę [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] wzorców formantów wymaganych do obsługi przez wszystkie kontrolki elementów danych. Aby uzyskać więcej informacji na temat wzorców kontrolek, zobacz [Omówienie wzorców kontrolek automatyzacji interfejsu użytkownika](ui-automation-control-patterns-overview.md).  
  
|Wzorzec kontrolki|Pomoc techniczna|Uwagi|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Zależy od|Jeśli element danych może być rozwinięty lub zwinięty w celu pokazywania i ukrywania informacji, musi być obsługiwany wzorzec rozwijania zwijanie.|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Zależy od|Elementy danych będą obsługiwać wzorzec elementu siatki, gdy kolekcja elementów danych jest dostępna w obrębie kontenera, w którym można przechodzić do elementów.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Zależy od|Wszystkie elementy danych obsługują możliwość przewijania do widoku z wzorcem elementu przewijania, gdy ich kontener danych zawiera więcej elementów niż można zmieścić na ekranie.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Tak|Wszystkie elementy danych muszą obsługiwać wzorzec elementu zaznaczenia, aby wskazać, kiedy element jest zaznaczony.|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Zależy od|Jeśli element danych jest zawarty w typie kontrolki siatki danych, będzie obsługiwał ten wzorzec.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Zależy od|Jeśli element danych zawiera stan, który może być przetworzony przez.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Zależy od|Jeśli podstawowy tekst elementu danych jest edytowalny, wzorzec wartości musi być obsługiwany.|  
  
## <a name="working-with-data-items-in-large-lists"></a>Praca z elementami danych na dużych listach  
 Duże listy są często danymi zwirtualizowanymi w ramach [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] struktur, aby pomóc w wydajności. Z tego powodu klient automatyzacji interfejsu użytkownika nie może użyć [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] funkcji zapytania, aby wyrównać zawartość pełnego drzewa w taki sam sposób, jak w przypadku innych kontenerów elementów. Klient powinien przewinąć element do widoku (lub rozwinąć kontrolkę, aby wyświetlić wszystkie cenne opcje) przed uzyskaniem dostępu do pełnego zestawu informacji z elementu danych.  
  
 Gdy wywoływana jest `SetFocus` [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pozycja elementu danych, przypadek Eksploratora systemu Microsoft Windows zwróci powodzenie i spowoduje, że fokus zostanie ustawiony na edycję w poddrzewie elementu danych.  
  
## <a name="required-ui-automation-events"></a>Wymagane zdarzenia automatyzacji interfejsu użytkownika  
 Poniższa tabela zawiera listę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzeń wymaganych do obsługi przez wszystkie kontrolki elementów danych. Aby uzyskać więcej informacji na temat zdarzeń, zobacz [Omówienie zdarzeń automatyzacji interfejsu użytkownika](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Wydarzen|Pomoc techniczna|Uwagi|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Zależy od|Brak|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>zdarzenie zmiany właściwości.|Zależy od|Brak|  
  
## <a name="dataitem-control-type-example"></a>Przykład typu kontrolki danych  
 Na poniższej ilustracji przedstawiono typ formantu elementu danych w kontrolce widok listy z obsługą zaawansowanych informacji dla kolumn.  
  
 ![Ilustracja przedstawiająca kontrolkę widoku listy z dwoma elementami danych](./media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 Poniżej zostanie wyświetlony widok kontrolki i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, które odnoszą się do kontrolki elementu danych. Wzorce kontrolki dla każdego elementu automatyzacji są wyświetlane w nawiasach. Grupa "contoso" jest również częścią siatki kontrolki hosta siatki danych.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Widok kontrolki drzewa|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Drzewo — widok zawartości|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|-Group "contoso" (tabela, siatka)<br />-Element "Receivable.doc konta" (TableItem, GridItem, SelectionItem dla, Invoke)<br />-Image "konta Receivable.doc"<br />-Edytuj "name" (TableItem, GridItem, Value "Accounts Receivable.doc")<br />-Edytuj "Data modyfikacji" (TableItem, GridItem, wartość "8/25/2006 3:29 PM")<br />-Edit "size" (GridItem, TableItem, Value "11,0 KB)<br />-Element "Payable.doc konta" (TableItem, GridItem, SelectionItem dla, Invoke)<br />-   ...|-Group "contoso" (tabela, siatka)<br />-Element "Receivable.doc konta" (TableItem, GridItem, SelectionItem dla, Invoke)<br />-Image "konta Receivable.doc"<br />-Edytuj "name" (TableItem, GridItem, Value "Accounts Receivable.doc")<br />-Edytuj "Data modyfikacji" (TableItem, GridItem, wartość "8/25/2006 3:29 PM")<br />-Edit "size" (GridItem, TableItem, Value "11,0 KB)<br />-Element "Payable.doc konta" (TableItem, GridItem, SelectionItem dla, Invoke)<br />-   …|  
  
 Jeśli siatka reprezentuje listę elementów możliwej do wyboru, odpowiednie elementy interfejsu użytkownika mogą być uwidocznione przy użyciu typu kontrolki ListItem zamiast typu kontrolki danych. W poprzednim przykładzie elementy danych elementu danych ("Accounts Receivable.doc" i "Accounts Payable.doc") w grupie ("contoso") można ulepszyć przez udostępnienie ich jako typy kontrolek typu ListItem, ponieważ ten typ już obsługuje wzorzec formantu SelectionItem dla.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Automation.ControlType.DataItem>
- [Typy formantów automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-types-overview.md)
- [Przegląd automatyzacji interfejsu użytkownika](ui-automation-overview.md)
