---
title: Obsługa automatyzacji interfejsu użytkownika dla typu formantu DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- Data Grid control type
- control types, Data Grid
- UI Automation, Data Grid control type
ms.assetid: a3db4a3f-feb5-4e5f-9b42-aae7fa816e8a
ms.openlocfilehash: 9bf036271652f8056b79f4c5e389347cd09989e8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59161034"
---
# <a name="ui-automation-support-for-the-datagrid-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla typu formantu DataGrid
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera informacje na temat [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pomocy technicznej dla kontrolek typu DataGrid. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ formantu to zestaw warunków, które kontrolki muszą spełnić, aby można było używać `ControlType` właściwości. Warunki obejmują konkretne wskazówki dotyczące [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wartości właściwości i wzorce kontrolki.  
  
 Typ formantu DataGrid pozwala łatwo pracować z elementami, które zawierają metadane reprezentowany w kolumnach. Formanty siatki danych ma wiersze elementów i kolumny informacji na temat tych elementów. Kontrolka widoku listy w programie Microsoft Vista Explorer jest przykładowi, który obsługuje typ formantu DataGrid.  
  
 Poniższe sekcje definiują wymagane [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa struktury, właściwości, wzorców kontrolek i zdarzeń dla kontrolek typu DataGrid. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Wymagania mają zastosowanie do wszystkich danych formantach siatki czy [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], lub [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Struktura drzewa automatyzacji interfejsu użytkownika wymagane  
 Poniższa tabela przedstawia kontroli i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewo, które odnoszą się do siatki danych steruje i w tym artykule opisano, jakie mogą być zawarte w każdym widoku. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, zobacz [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Drzewo — widoku kontrolnym|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Drzewo — Widok zawartości|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|DataGrid<br /><br /> <ul><li>Nagłówek (0, 1 lub 2)<br /><br /> <ul><li>HeaderItem (liczba wierszy lub kolumn)</li></ul></li><li>Element danych (0 lub więcej; mogą być zorganizowane w hierarchii)</li></ul>|DataGrid<br /><br /> -DataItem (0 lub więcej; mogą być zorganizowane w hierarchii)|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Właściwości automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono właściwości, których wartość lub definicji jest szczególnie istotne w formantach siatki danych. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|Właściwość|Wartość|Uwagi|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz uwagi.|Wartość tej właściwości musi być unikatowa wśród wszystkich kontrolek w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz uwagi.|Najbardziej zewnętrznej prostokąt, który zawiera całą kontrolkę.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz uwagi.|Obsługiwane w przypadku prostokąt otaczający. W przeciwnym razie każdy punkt, w ramach prostokąt otaczający jest możesz klikać i wykonywać specjalne testowania trafień, zastąpić i zapewnienia elementu do kliknięcia.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|DataGrid|Ta wartość jest taka sama dla wszystkich platform tworzenia interfejsu użytkownika.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Prawda|Wartość tej właściwości musi zawsze mieć wartość True. Oznacza to, formant siatki danych musi być zawsze w widoku zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Prawda|Wartość tej właściwości musi zawsze mieć wartość True. Oznacza to, formant siatki danych musi być zawsze w widoku kontrolnym [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Zobacz uwagi.|Formant może otrzymywać fokus klawiatury, musi obsługiwać tę właściwość.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Zobacz uwagi.|Jeśli brak jest etykiety tekst statyczny tej właściwości należy ujawnić odwołanie do tego formantu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"siatki danych"|Zlokalizowany ciąg odpowiadający typowi Formant DataGrid.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz uwagi.|Formant siatki danych zazwyczaj pobiera wartość jego `Name` właściwość etykiety tekst statyczny. Jeśli nie jest etykietą tekst statyczny Deweloper aplikacji, należy przypisać wartość do `Name` właściwości. Wartość `Name` właściwość nigdy nie musi być zawartość tekstową kontrolki edycji.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Wzorce kontrolek automatyzacji interfejsu użytkownika wymagane  
 Poniższa tabela zawiera listę wzorców kontrolek, wymagane są obsługiwane przez wszystkie formanty siatki danych. Aby uzyskać więcej informacji na temat wzorców kontrolek, zobacz [Przegląd wzorców kontrolki automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|— Wzorzec kontrolki|Pomoc techniczna|Uwagi|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Yes|Sam formant siatki danych zawsze obsługuje wzorca kontrolki siatki, ponieważ elementy zawierała metadanych, który został rozmieszczony w siatce.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Zależy od|Możliwość przewiń w siatce danych, zależy od zawartości i tego, czy paski przewijania są obecne.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Zależy od|Możliwość wybrania siatki danych zależy od zawartości.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Tak|Formant siatki danych zawsze ma nagłówek w ramach jego poddrzewa, więc wzorca kontrolki tabeli muszą być obsługiwane.|  
  
 Elementy danych w ramach kontenerów siatki danych będzie obsługiwać minimum:  
  
-   SelectionItem — wzorzec kontrolki (jeśli siatki danych jest możliwy)  
  
-   Przewiń — wzorzec kontrolki (jeśli siatki danych przewijany)  
  
-   Grid — wzorzec kontrolki  
  
-   TableItem — Wzorzec kontrolki  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Właściwości zdarzeń automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia wymagane są obsługiwane przez wszystkie formanty siatki danych. Aby uzyskać więcej informacji o zdarzeniach zobacz [Przegląd zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Zdarzenie|Pomoc techniczna|Uwagi|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Zależy od|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty> Zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> Zdarzenie zmiany właściwości.|Zależy od|Jeśli są obsługiwane przez kontrolkę wzorca przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> Zdarzenie zmiany właściwości.|Zależy od|Jeśli są obsługiwane przez kontrolkę wzorca przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> Zdarzenie zmiany właściwości.|Zależy od|Jeśli są obsługiwane przez kontrolkę wzorca przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> Zdarzenie zmiany właściwości.|Zależy od|Jeśli są obsługiwane przez kontrolkę wzorca przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> Zdarzenie zmiany właściwości.|Zależy od|Jeśli są obsługiwane przez kontrolkę wzorca przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> Zdarzenie zmiany właściwości.|Zależy od|Jeśli są obsługiwane przez kontrolkę wzorca przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Wymagane|Brak|  
  
<a name="List_View_Control_Example"></a>   
## <a name="date-grid-control-type-example"></a>Przykład typu kontrolki Grid daty  
 Na poniższym obrazie przedstawiono kontrolka widoku listy, która implementuje typu formantu DataGrid.  
  
 ![Graficzne kontrolki widok listy z dwoma elementami danych](../../../docs/framework/ui-automation/media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 Kontrolki i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewo, które odnoszą się do kontrolki widoku listy jest wyświetlana poniżej. Wzorce kontrolki dla każdego elementu automatyzacji są wyświetlane w nawiasach.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Drzewo — widoku kontrolnym|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Drzewo — Widok zawartości|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|<ul><li>Siatka danych (tabeli siatki, wybór)</li><li>nagłówek<br /><br /> <ul><li>HeaderItem "Name" (wywołanie)</li><li>HeaderItem "Data modyfikacji" (wywołanie)</li><li>HeaderItem "Rozmiar" (wywołanie)</li></ul></li><li>Grupa "Contoso" (TableItem GridItem —, SelectionItem dla, tabeli *, siatki\*)<br /><br /> <ul><li>DataItem "kont Receivable.doc" (SelectionItem dla, wywołaj TableItem\*, GridItem —\*)</li><li>DataItem "kont Payable.doc" (SelectionItem dla, wywołaj TableItem\*, GridItem —\*)</li></ul></li></ul>|<ul><li>Siatka danych (tabeli siatki, wybór)</li><li>Grupa "Contoso" (TableItem GridItem —, SelectionItem dla, tabeli *, siatki\*)<br /><br /> <ul><li>DataItem "kont Receivable.doc" (SelectionItem dla, wywołaj TableItem\*, GridItem —\*)</li><li>DataItem "kont Payable.doc" (SelectionItem dla, wywołaj TableItem\*, GridItem —\*)</li></ul></li></ul>|  
  
 * Powyższy przykład pokazuje DataGrid, który zawiera wiele poziomów kontroli. Formant grupy ("Contoso") zawiera dwie kontrolki elementu danych ("Kont Receivable.doc" i "Kont Payable.doc"). Para DataGrid/GridItem — jest niezależna od pary na innym poziomie. Kontrolki elementu danych w grupie można również udostępniane, jako typ kontroli wyszczególnij umożliwiające im mają zostać wyświetlone więcej obiektów wyraźnie, jak można wybierać, a nie jako elementy danych proste. W tym przykładzie nie ma elementów podrzędnych elementów pogrupowanych danych.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Automation.ControlType.DataGrid>
- [Typy formantów automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)
- [Przegląd automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-overview.md)
