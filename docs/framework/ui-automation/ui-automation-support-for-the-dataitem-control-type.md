---
title: Obsługa automatyzacji interfejsu użytkownika dla typu formantu DataItem
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Data Item control type
- Data Item control type
- control types, Data Item
ms.assetid: 181708fd-2595-4c43-9abd-75811627d64c
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: e055733a8f3d1ecb9c1fcea336bbe90ddd155731
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48032426"
---
# <a name="ui-automation-support-for-the-dataitem-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu DataItem
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera informacje na temat [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pomocy technicznej dla kontrolek typu DataItem. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] typu formantu to zestaw warunków, które kontrolki muszą spełnić, aby można było używać <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> właściwości. Warunki obejmują konkretne wskazówki dotyczące [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wartości właściwości i wzorce kontrolki.  
  
 Wpis na liście kontaktów jest przykładem kontrolki elementu danych. Kontrolki elementu danych zawiera informacje, który ma znaczenie dla użytkownika końcowego. Jest bardziej skomplikowane niż element prostej listy, ponieważ zawiera ona bogatsze informacje.  
  
 Poniższe sekcje definiują wymagane [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury, właściwości, wzorców kontrolek i zdarzeń dla kontrolek typu DataItem drzewa. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Wymagania mają zastosowanie do wszystkich danych kontrolki elementu czy [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], lub [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Struktura drzewa automatyzacji interfejsu użytkownika wymagane  
 Poniższa tabela przedstawia kontroli i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewo, które odnoszą się do elementu danych steruje i w tym artykule opisano, jakie mogą być zawarte w każdym widoku. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, zobacz [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Drzewo — widoku kontrolnym|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Drzewo — Widok zawartości|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|Element danych<br /><br /> -Różni się (0 lub więcej; mogą być zorganizowane w hierarchii)|Element danych<br /><br /> -Różni się (0 lub więcej; mogą być zorganizowane w hierarchii)|  
  
 Element elementu danych w siatce danych można hostować różnych obiektów, w tym kolejną warstwę elementy danych lub siatki określone elementy, takie jak tekst, obrazy lub edycji wzbogaconej. Jeśli element element danych ma rolę określonego obiektu, element powinny zostać ujawnione jako określonego typu; na przykład ListItem typ formantu elementu można wybierać danych w siatce.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Właściwości automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono właściwości, których wartość lub definicji jest szczególnie istotne kontrolki elementu danych. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|Właściwość|Wartość|Uwagi|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz uwagi.|Wartość tej właściwości musi być unikatowa wśród wszystkich kontrolek w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz uwagi.|Najbardziej zewnętrznej prostokąt, który zawiera całą kontrolkę.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz uwagi.|Obsługiwane w przypadku prostokąt otaczający. W przeciwnym razie każdy punkt, w ramach prostokąt otaczający jest możesz klikać i wykonywać specjalne testowania trafień, zastąpić i zapewnienia elementu do kliknięcia.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Element danych|Ta wartość jest taka sama dla wszystkich platform tworzenia interfejsu użytkownika.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Kontrolki elementu danych musi być zawsze zawartości.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Kontrolki elementu danych musi być zawsze formantu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Zobacz uwagi.|Formant może otrzymywać fokus klawiatury, musi obsługiwać tę właściwość.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>|Zobacz uwagi.|Jeśli kontrolka zawiera stan, która jest aktualizowana dynamicznie, a następnie ta właściwość musi być obsługiwana, dzięki czemu technologii pomocniczej, które mogą odbierać aktualizacje po zmianie stanu elementu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Zobacz uwagi.|Jest to wartość ciągu, który umożliwia przekazywanie danych do użytkownika końcowego obiektu źródłowego, który reprezentuje element. Przykładami są "Pliku multimedialnego" lub "Skontaktuj się z".|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Kontrolki elementu danych nie ma etykiety tekst statyczny.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"element danych"|Zlokalizowany ciąg odpowiadający typu formantu elementu danych.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz uwagi.|Kontrolki elementu danych jest zawsze zawiera element tekst podstawowy, który odnosi się do użytkownika skojarzyć jako najbardziej semantycznego identyfikatora dla elementu.|  
  
<a name="_Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Wzorce kontrolek automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kontrolować wzorców, wymagane są obsługiwane przez wszystkie kontrolki elementu danych. Aby uzyskać więcej informacji na temat wzorców kontrolek, zobacz [Przegląd wzorców kontrolki automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|— Wzorzec kontrolki|Obsługa|Uwagi|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Zależy od|Jeśli element danych można można rozwijać i zwijać by pokazać lub ukryć informacje, wzorzec Rozwiń Zwiń muszą być obsługiwane.|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Zależy od|Elementy danych będzie obsługiwać wzorzec elementu siatki, gdy kolekcja elementów danych jest dostępna w kontenerze, który może być przestrzennie nawigować pozycji na pozycję.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Zależy od|Wszystkie elementy danych obsługuje możliwość być przewijane w widoku przy użyciu wzorca element przewijania, gdy ich kontenera danych ma więcej elementów niż można zmieścić na ekranie.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Tak|Wszystkie elementy danych musi obsługiwać wzorzec SelectionItem sygnalizującego, kiedy element jest zaznaczony.|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Zależy od|Jeśli element danych znajduje się w obrębie typu formantu siatki danych będzie ona obsługiwać tego wzorca.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Zależy od|Jeśli element danych zawiera stan, który jest cyklom za pośrednictwem.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Zależy od|Jeśli tekst podstawowy element danych jest edytowalna wzorca wartości muszą być obsługiwane.|  
  
<a name="Working_with_Data_Items_in_Large_Lists"></a>   
## <a name="working-with-data-items-in-large-lists"></a>Praca z elementami danych w dużych listach  
 Duże listy są często danych zwirtualizowane w ramach [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] struktur ułatwiających wydajności. Z tego powodu nie można użyć klienta automatyzacji interfejsu użytkownika [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] funkcji zapytania scrape zawartość pełne drzewo w taki sam sposób, że jest to możliwe w innych kontenerach elementu. Klient powinien przewinąć element w widoku (lub rozwiń kontrolki aby pokazać wszystkie opcje cenne) przed uzyskaniem dostępu do pełnego zestawu danych z elementu danych.  
  
 Podczas wywoływania `SetFocus` na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element do elementu danych [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)] przypadek zwróci pomyślnie i spowodować, że fokus, należy ustawić na edycję w poddrzewie elementu danych.  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Właściwości zdarzeń automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia wymagane są obsługiwane przez wszystkie kontrolki elementu danych. Aby uzyskać więcej informacji o zdarzeniach zobacz [Przegląd zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Zdarzenia|Obsługa|Uwagi|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Zależy od|Brak|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty> Zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty> Zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> Zdarzenie zmiany właściwości.|Zależy od|Brak|  
  
<a name="Data_Item_Control_Type_Example"></a>   
## <a name="dataitem-control-type-example"></a>Przykład typu formantu elementu danych  
 Na poniższym obrazie przedstawiono typu formantu elementu danych w kontrolce widok listy z obsługą rozbudowane informacje dla kolumn.  
  
 ![Graficzne kontrolki widok listy z dwoma elementami danych](../../../docs/framework/ui-automation/media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 Kontrolki i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewo, które odnoszą się do kontrolki elementu danych jest wyświetlana poniżej. Wzorce kontrolki dla każdego elementu automatyzacji są wyświetlane w nawiasach. Grupa "Contoso" jest również częścią siatki kontrolki hosta w siatce danych.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Drzewo — widoku kontrolnym|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Drzewo — Widok zawartości|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|-Grupy "Contoso" (tabeli i siatki)<br />— DataItem "kont Receivable.doc" (TableItem, GridItem — SelectionItem dla, wywołaj)<br />-Image "Kont Receivable.doc"<br />-Edytować "Name" (TableItem, GridItem —, wartość "Kont Receivable.doc")<br />-Edytować "Data modyfikacji" (wartość TableItem, GridItem —, "8/25/2006 3:29 PM")<br />-Edytować "Rozmiar" (wartość GridItem —, TableItem, "11.0 KB)<br />— DataItem "kont Payable.doc" (TableItem, GridItem — SelectionItem dla, wywołaj)<br />-   ...|-Grupy "Contoso" (tabeli i siatki)<br />— DataItem "kont Receivable.doc" (TableItem, GridItem — SelectionItem dla, wywołaj)<br />-Image "Kont Receivable.doc"<br />-Edytować "Name" (TableItem, GridItem —, wartość "Kont Receivable.doc")<br />-Edytować "Data modyfikacji" (wartość TableItem, GridItem —, "8/25/2006 3:29 PM")<br />-Edytować "Rozmiar" (wartość GridItem —, TableItem, "11.0 KB)<br />— DataItem "kont Payable.doc" (TableItem, GridItem — SelectionItem dla, wywołaj)<br />-   …|  
  
 Jeśli siatki reprezentuje listę elementów możliwych do wybrania, odpowiednie elementy interfejsu użytkownika można ujawnić z typem kontroli wyszczególnij zamiast typu formantu elementu danych. W poprzednim przykładzie można zwiększyć, udostępnianie je jako typy kontroli wyszczególnij, ponieważ ten typ obsługuje już wzorca kontrolki SelectionItem dla elementów DataItem ("Kont Receivable.doc" i "Kont Payable.doc") w grupie ("Contoso").  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Automation.ControlType.DataItem>  
 [Typy kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Przegląd automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-overview.md)
