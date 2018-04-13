---
title: Obsługa automatyzacji interfejsu użytkownika dla typu formantu DataGrid
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Data Grid control type
- control types, Data Grid
- UI Automation, Data Grid control type
ms.assetid: a3db4a3f-feb5-4e5f-9b42-aae7fa816e8a
caps.latest.revision: ''
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 3eb60004f4ffad0b62b10cf1e3ff5f28a3bf3fef
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
---
# <a name="ui-automation-support-for-the-datagrid-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu DataGrid
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera informacje na temat [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] obsługi dla typu formantu DataGrid. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typu formantu to zestaw warunków, które muszą spełniać formantu, aby można było używać `ControlType` właściwości. Takie szczegółowe wytyczne dla [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wartości właściwości i wzorce formantu.  
  
 DataGrid — typ formantu pozwala łatwo pracować z elementami zawierającymi metadane reprezentowany w kolumnach. Formanty siatki danych ma wiersze elementów i kolumny informacji na temat tych elementów. Kontrolki widoku listy w Eksplorator systemu Microsoft Vista to przykład obsługującego typu formantu DataGrid.  
  
 Następujące sekcje definiują wymaganych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa struktury, właściwości wzorców formantu i zdarzenia dla typu formantu DataGrid. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Wymagania dotyczą wszystkich danych formanty siatki czy [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], lub [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Struktura drzewa automatyzacji interfejsu użytkownika wymagane  
 Poniższa tabela przedstawia kontroli i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, które dotyczą siatki danych kontrolki i opisano, jakie mogą być zawarte w każdym widoku. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, zobacz [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Drzewo — widoku kontrolki|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Drzewo — Widok zawartości|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|DataGrid<br /><br /> <ul><li>Nagłówek (0, 1 lub 2)<br /><br /> <ul><li>HeaderItem (liczba wierszy lub kolumn)</li></ul></li><li>Element danych (0 lub więcej; może odbywać się w hierarchii)</li></ul>|DataGrid<br /><br /> — DataItem (0 lub więcej; może odbywać się w hierarchii)|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Właściwości automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono właściwości, której wartość lub definicji jest szczególnie istotne, aby formanty siatki danych. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|Właściwość|Wartość|Uwagi|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz uwagi.|Wartość tej właściwości musi być unikatowy w obrębie wszystkich kontrolek w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz uwagi.|Prostokąt peryferyjnych zawiera całą formantu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz uwagi.|Obsługiwane w przypadku prostokąt ograniczający. Jeśli nie każdy punkt w obrębie prostokątem jest aktywne i wykonywać specjalne testowanie trafień, zastąpienia i podaj elementu do kliknięcia.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|DataGrid|Ta wartość jest taka sama dla wszystkich platform interfejsu użytkownika.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Wartość tej właściwości musi być zawsze wartość True. To oznacza, że formantu siatki danych zawsze musi być w widoku zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Wartość tej właściwości musi być zawsze wartość True. To oznacza, że formantu siatki danych zawsze musi być w widoku kontrolki [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Zobacz uwagi.|Formant może przyjmować fokus klawiatury, musi obsługiwać tej właściwości.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Zobacz uwagi.|Jeśli brak jest etykiety tekst statyczny tej właściwości musi ujawniać odwołanie do tego formantu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"siatka danych"|Zlokalizowany ciąg odpowiadający typu formantu DataGrid.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz uwagi.|Formantu siatki danych zwykle pobiera wartość jego `Name` właściwości z etykiety tekst statyczny. Jeśli nie jest etykietą tekst statyczny Deweloper aplikacji należy przypisać wartość do `Name` właściwości. Wartość `Name` właściwości nigdy nie może być zawartość tekstową kontrolki edycji.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Wzorce formantów automatyzacji interfejsu użytkownika wymagane  
 Poniższa tabela zawiera listę wzorców formantu wymagane obsługiwane przez wszystkie formanty siatki danych. Aby uzyskać więcej informacji na temat wzorców formantu, zobacz [Przegląd wzorców formantu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|— Wzorzec formantu|Obsługa|Uwagi|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Tak|Samej kontrolce siatki danych zawsze obsługuje Grid — wzorzec formantu, ponieważ elementy którego nie zawiera metadanych, które jest określone w siatce.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Zależy od|Możliwość przewijania siatki danych zależy od zawartości i czy są obecne paski przewijania.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Zależy od|Możliwość wybrania Siatka danych zależy od zawartości.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Tak|Formantu siatki danych zawsze ma nagłówek w jego poddrzewa, więc wzorca formantu tabeli muszą być obsługiwane.|  
  
 Elementy danych w kontenerach siatki danych będzie obsługiwać co najmniej:  
  
-   SelectionItem — wzorzec formantu (jeśli siatka danych jest możliwy)  
  
-   Przewiń — wzorzec formantu (jeśli siatka danych przewijanego)  
  
-   Grid — wzorzec formantu  
  
-   TableItem — Wzorzec kontrolki  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Zdarzeń automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wymagane obsługiwane przez wszystkie formanty siatki danych zdarzenia. Aby uzyskać więcej informacji o zdarzeniach, zobacz [Przegląd zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Zdarzenia|Obsługa|Uwagi|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Zależy od|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty> Zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> Zdarzenie zmiany właściwości.|Zależy od|Jeśli formant obsługuje wzorca przewijania, musi obsługiwać tego zdarzenia.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> Zdarzenie zmiany właściwości.|Zależy od|Jeśli formant obsługuje wzorca przewijania, musi obsługiwać tego zdarzenia.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> Zdarzenie zmiany właściwości.|Zależy od|Jeśli formant obsługuje wzorca przewijania, musi obsługiwać tego zdarzenia.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> Zdarzenie zmiany właściwości.|Zależy od|Jeśli formant obsługuje wzorca przewijania, musi obsługiwać tego zdarzenia.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> Zdarzenie zmiany właściwości.|Zależy od|Jeśli formant obsługuje wzorca przewijania, musi obsługiwać tego zdarzenia.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> Zdarzenie zmiany właściwości.|Zależy od|Jeśli formant obsługuje wzorca przewijania, musi obsługiwać tego zdarzenia.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Wymagane|Brak|  
  
<a name="List_View_Control_Example"></a>   
## <a name="date-grid-control-type-example"></a>Przykład typu formantu siatki daty  
 Na poniższym obrazie przedstawiono formant ListView, który implementuje typu formantu DataGrid.  
  
 ![Graficzne formantu widoku listy z dwoma elementami danych](../../../docs/framework/ui-automation/media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 Formant i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, które odnoszą się do formantu widoku listy jest wyświetlony poniżej. Wzorce formantu dla każdego elementu automatyzacji są wyświetlane w nawiasach.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Drzewo — widoku kontrolki|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Drzewo — Widok zawartości|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|<ul><li>DataGrid (Wybór tabeli, siatki)</li><li>nagłówek<br /><br /> <ul><li>HeaderItem "Name" (wywołanie)</li><li>HeaderItem "Data modyfikacji" (wywołanie)</li><li>HeaderItem "Rozmiar" (wywołanie)</li></ul></li><li>Grupa "Contoso" (TableItem, GridItem, SelectionItem dla, tabeli *, siatki\*)<br /><br /> <ul><li>DataItem "kont Receivable.doc" (SelectionItem dla, wywołaj TableItem\*, GridItem\*)</li><li>DataItem "kont Payable.doc" (SelectionItem dla, wywołaj TableItem\*, GridItem\*)</li></ul></li></ul>|<ul><li>DataGrid (Wybór tabeli, siatki)</li><li>Grupa "Contoso" (TableItem, GridItem, SelectionItem dla, tabeli *, siatki\*)<br /><br /> <ul><li>DataItem "kont Receivable.doc" (SelectionItem dla, wywołaj TableItem\*, GridItem\*)</li><li>DataItem "kont Payable.doc" (SelectionItem dla, wywołaj TableItem\*, GridItem\*)</li></ul></li></ul>|  
  
 * W poprzednim przykładzie DataGrid, który zawiera wiele poziomów kontrolki. Formant grupy ("Contoso") zawiera dwa formanty DataItem ("Kont Receivable.doc" i "Kont Payable.doc"). Para DataGrid/GridItem jest niezależna od pary na innym poziomie. Formanty elementu danych w grupie można uwidocznić również jako typu formantu ListItem, umożliwiając im przedstawiane więcej obiektów wyraźnie jako możliwy, a nie jako proste danych elementów. W tym przykładzie nie zawiera elementy podrzędne elementy zgrupowanych danych.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Automation.ControlType.DataGrid>  
 [Typy kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Przegląd automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-overview.md)
