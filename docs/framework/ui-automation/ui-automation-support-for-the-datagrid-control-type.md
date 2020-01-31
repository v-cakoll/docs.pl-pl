---
title: Obsługa automatyzacji interfejsu użytkownika dla typu formantu DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- Data Grid control type
- control types, Data Grid
- UI Automation, Data Grid control type
ms.assetid: a3db4a3f-feb5-4e5f-9b42-aae7fa816e8a
ms.openlocfilehash: 1e127b4a2fdb51a151344f81e1451ecee6ca3a5a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789544"
---
# <a name="ui-automation-support-for-the-datagrid-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla typu formantu DataGrid
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Ten temat zawiera informacje na temat obsługi [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] dla typu formantu DataGrid. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]typ formantu to zestaw warunków, które formant musi spełniać, aby można było użyć właściwości `ControlType`. Warunki obejmują określone wytyczne dotyczące struktury drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], wartości właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] i wzorców formantów.  
  
 Typ formantu DataGrid umożliwia użytkownikowi łatwą współpracę z elementami zawierającymi metadane reprezentowane w kolumnach. Kontrolki siatki danych zawierają wiersze elementów i kolumn informacji o tych elementach. Kontrolka widoku listy w Eksploratorze systemu Microsoft Vista jest przykładem obsługującym typ formantu DataGrid.  
  
 Poniższe sekcje definiują wymaganą strukturę drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], właściwości, wzorce formantów i zdarzenia dla typu formantu DataGrid. Wymagania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dotyczą wszystkich formantów siatki danych, zarówno [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Win32, jak i Windows Forms.  
  
## <a name="required-ui-automation-tree-structure"></a>Wymagana struktura drzewa automatyzacji interfejsu użytkownika  
 W poniższej tabeli przedstawiono widok kontrolki i widok zawartości drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], które odnoszą się do kontrolek siatki danych i opisano, co może być zawarte w poszczególnych widokach. Aby uzyskać więcej informacji na temat drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Omówienie drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md).  
  
|Widok kontrolki drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Drzewo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] — widok zawartości|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|DataGrid<br /><br /> <ul><li>Nagłówek (0, 1 lub 2)<br /><br /> <ul><li>HeaderItem (liczba kolumn lub wierszy)</li></ul></li><li>Element typu (0 lub więcej; może być strukturalny w hierarchii)</li></ul>|DataGrid<br /><br /> -Element typu (0 lub więcej; może być strukturalny w hierarchii)|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Wymagane właściwości automatyzacji interfejsu użytkownika  
 Poniższa tabela zawiera listę właściwości, których wartość lub definicja jest szczególnie istotna dla kontrolek siatki danych. Aby uzyskać więcej informacji na temat właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md).  
  
|Właściwość|Wartość|Uwagi|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz uwagi.|Wartość tej właściwości musi być unikatowa dla wszystkich kontrolek w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz uwagi.|Najbardziej zewnętrzny prostokąt, który zawiera cały formant.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz uwagi.|Obsługiwane, jeśli istnieje prostokąt ograniczający. Jeśli nie każdy punkt wewnątrz prostokąta ograniczenia jest klikany, a będziesz wykonywał wyspecjalizowane Testy trafień, a następnie przesłonić i udostępnić punkt kliknięcia.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|DataGrid|Ta wartość jest taka sama dla wszystkich platform interfejsu użytkownika.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Prawda|Wartość tej właściwości musi zawsze mieć wartość true. Oznacza to, że kontrolka siatka danych musi zawsze znajdować się w widoku zawartości drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Prawda|Wartość tej właściwości musi zawsze mieć wartość true. Oznacza to, że kontrolka siatka danych musi zawsze znajdować się w widoku kontrolki drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Zobacz uwagi.|Jeśli formant może odbierać fokus klawiatury, musi obsługiwać tę właściwość.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Zobacz uwagi.|Jeśli istnieje statyczna etykieta tekstowa, ta właściwość musi ujawniać odwołanie do tej kontrolki.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"siatka danych"|Zlokalizowany ciąg odpowiadający typowi formantu DataGrid.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz uwagi.|Kontrolka siatka danych zazwyczaj pobiera wartość właściwości `Name` z statycznej etykiety tekstowej. Jeśli nie istnieje etykieta tekstu statycznego, Deweloper aplikacji musi przypisać wartość do właściwości `Name`. Wartość właściwości `Name` nie może być zawartością tekstową kontrolki edycji.|  
  
## <a name="required-ui-automation-control-patterns"></a>Wymagane wzorce kontrolek automatyzacji interfejsu użytkownika  
 Poniższa tabela zawiera listę wzorców formantów wymaganych do obsługi przez wszystkie kontrolki siatki danych. Aby uzyskać więcej informacji na temat wzorców kontrolek, zobacz [Omówienie wzorców kontrolek automatyzacji interfejsu użytkownika](ui-automation-control-patterns-overview.md).  
  
|Wzorzec kontrolki|Obsługa|Uwagi|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Tak|Kontrolka siatka danych zawsze obsługuje wzorzec kontrolki siatki, ponieważ elementy, które zawierają metadane, które są określone w siatce.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Zależy od|Możliwość przewijania siatki danych zależy od zawartości i od tego, czy paski przewijania są obecne.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Zależy od|Możliwość wyboru siatki danych zależy od zawartości.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Tak|Kontrolka siatka danych zawsze ma nagłówek w jego poddrzewie, aby wzorzec kontrolki tabela musi być obsługiwany.|  
  
 Elementy danych w kontenerach siatki danych będą obsługiwane co najmniej:  
  
- Wzorzec kontrolki elementu zaznaczenia (w przypadku wybrania siatki danych)  
  
- Scroll — wzorzec kontrolki (Jeśli siatka danych jest przewijana)  
  
- Wzorzec kontrolki elementu siatki  
  
- TableItem — Wzorzec kontrolki  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Wymagane zdarzenia automatyzacji interfejsu użytkownika  
 Poniższa tabela zawiera listę zdarzeń [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], które muszą być obsługiwane przez wszystkie kontrolki siatki danych. Aby uzyskać więcej informacji na temat zdarzeń, zobacz [Omówienie zdarzeń automatyzacji interfejsu użytkownika](ui-automation-events-overview.md).  
  
|Zdarzenie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Obsługa|Uwagi|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Zależy od|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty> zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> zdarzenie zmiany właściwości.|Zależy od|Jeśli formant obsługuje wzorzec przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> zdarzenie zmiany właściwości.|Zależy od|Jeśli formant obsługuje wzorzec przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> zdarzenie zmiany właściwości.|Zależy od|Jeśli formant obsługuje wzorzec przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> zdarzenie zmiany właściwości.|Zależy od|Jeśli formant obsługuje wzorzec przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> zdarzenie zmiany właściwości.|Zależy od|Jeśli formant obsługuje wzorzec przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> zdarzenie zmiany właściwości.|Zależy od|Jeśli formant obsługuje wzorzec przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Wymagane|Brak|  
  
## <a name="date-grid-control-type-example"></a>Przykład typu kontrolki siatki daty  
 Na poniższej ilustracji przedstawiono formant widoku listy, który implementuje typ formantu DataGrid.  
  
 ![Ilustracja przedstawiająca kontrolkę widoku listy z dwoma elementami danych](./media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 Poniżej zostanie wyświetlony widok kontrolki i widok zawartości drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], które odnoszą się do kontrolki widok listy. Wzorce kontrolki dla każdego elementu automatyzacji są wyświetlane w nawiasach.  
  
|Widok kontrolki drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Drzewo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] — widok zawartości|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|<ul><li>DataGrid (tabela, Siatka, wybór)</li><li>nagłówek<br /><br /> <ul><li>HeaderItem "name" (Invoke)</li><li>HeaderItem "Data modyfikacji" (Invoke)</li><li>HeaderItem "size" (Invoke)</li></ul></li><li>Grupa "contoso" (TableItem, GridItem, SelectionItem dla, tabela *, Siatka\*)<br /><br /> <ul><li>Element Ci "Accounts. doc" (SelectionItem dla, Invoke, TableItem\*, GridItem\*)</li><li>Element Ci "Accounts. doc" (SelectionItem dla, Invoke, TableItem\*, GridItem\*)</li></ul></li></ul>|<ul><li>DataGrid (tabela, Siatka, wybór)</li><li>Grupa "contoso" (TableItem, GridItem, SelectionItem dla, tabela *, Siatka\*)<br /><br /> <ul><li>Element Ci "Accounts. doc" (SelectionItem dla, Invoke, TableItem\*, GridItem\*)</li><li>Element Ci "Accounts. doc" (SelectionItem dla, Invoke, TableItem\*, GridItem\*)</li></ul></li></ul>|  
  
 \* w poprzednim przykładzie przedstawiono element DataGrid, który zawiera wiele poziomów kontrolek. Kontrolka Grupa ("contoso") zawiera dwie kontrolki elementu ("Accounts. doc" i "Accounts. doc"). Para DataGrid/GridItem jest niezależna od pary na innym poziomie. Kontrolki danych elementu danych w grupie mogą być również uwidocznione jako typ kontrolki typu "ListItem", co umożliwia ich wyraźne prezentowanie jako obiektów z możliwością wyboru, a nie jako proste elementy danych. Ten przykład nie obejmuje elementów podrzędnych zgrupowanych elementów danych.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Automation.ControlType.DataGrid>
- [Typy kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-types-overview.md)
- [Przegląd automatyzacji interfejsu użytkownika](ui-automation-overview.md)
