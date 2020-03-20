---
title: Obsługa automatyzacji interfejsu użytkownika dla typu formantu DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- Data Grid control type
- control types, Data Grid
- UI Automation, Data Grid control type
ms.assetid: a3db4a3f-feb5-4e5f-9b42-aae7fa816e8a
ms.openlocfilehash: 69532c9836876c25e9f31395213b1a89e0307dcd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179800"
---
# <a name="ui-automation-support-for-the-datagrid-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla typu formantu DataGrid
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Ten temat zawiera [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] informacje na temat obsługi typu formantu DataGrid. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ formantu jest zestawem warunków, które `ControlType` formant musi spełniać w celu użycia właściwości. Warunki obejmują szczegółowe [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wytyczne dotyczące [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa, wartości właściwości i wzorców kontroli.  
  
 Typ formantu DataGrid umożliwia użytkownikowi łatwe pracę z elementami, które zawierają metadane reprezentowane w kolumnach. Formanty siatki danych mają wiersze elementów i kolumny informacji o tych elementach. Formant widoku listy w Eksploratorze Microsoft Vista jest przykładem, który obsługuje typ formantu DataGrid.  
  
 Poniższe sekcje definiują wymaganą [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strukturę drzewa, właściwości, wzorce kontroli i zdarzenia dla typu formantu DataGrid. Wymagania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dotyczą wszystkich formantów siatki [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]danych, niezależnie od tego, czy , Win32 lub Windows Forms.  
  
## <a name="required-ui-automation-tree-structure"></a>Wymagana struktura drzewa automatyzacji interfejsu użytkownika  
 W poniższej tabeli przedstawiono widok formantu i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, który odnosi się do formantów siatki danych i opisuje, co może być zawarte w każdym widoku. Aby uzyskać więcej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informacji na temat drzewa, zobacz [Omówienie drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Drzewo — widok kontrolny|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Drzewo — widok zawartości|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|DataGrid<br /><br /> <ul><li>Nagłówek (0, 1 lub 2)<br /><br /> <ul><li>Element nagłówka (liczba kolumn lub wierszy)</li></ul></li><li>DataItem (0 lub więcej; może być skonstruowany w hierarchii)</li></ul>|DataGrid<br /><br /> - DataItem (0 lub więcej; może być zorganizowany w hierarchii)|  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Wymagane właściwości automatyzacji interfejsu użytkownika  
 W poniższej tabeli wymieniono właściwości, których wartość lub definicja jest szczególnie istotne dla formantów siatki danych. Aby uzyskać [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] więcej informacji na temat właściwości, zobacz [Właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md).  
  
|Właściwość|Wartość|Uwagi|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz notatki.|Wartość tej właściwości musi być unikatowa we wszystkich formantów w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz notatki.|Najbardziej zewnętrzny prostokąt, który zawiera cały formant.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz notatki.|Obsługiwane, jeśli istnieje prostokąt ograniczający. Jeśli nie każdy punkt w prostokątze ograniczającym jest klikalny i wykonujesz specjalistyczne testowanie trafień, a następnie zastądaj i podaj klikalny punkt.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|DataGrid|Ta wartość jest taka sama dla wszystkich struktur interfejsu użytkownika.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Wartość tej właściwości musi być zawsze True. Oznacza to, że formant siatki danych musi [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zawsze znajdować się w widoku zawartości drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Wartość tej właściwości musi być zawsze True. Oznacza to, że formant siatki danych musi [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zawsze znajdować się w widoku kontrolnym drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Zobacz notatki.|Jeśli formant może odbierać fokus klawiatury, musi obsługiwać tę właściwość.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Zobacz notatki.|Jeśli istnieje etykieta tekstu statycznego, ta właściwość musi ujawnić odwołanie do tego formantu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"siatka danych"|Zlokalizowany ciąg odpowiadający typowi formantu DataGrid.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz notatki.|Formant siatki danych zazwyczaj pobiera `Name` wartość dla jego właściwości ze statycznej etykiety tekstowej. Jeśli nie ma statycznej etykiety tekstowej, deweloper aplikacji `Name` musi przypisać wartość dla właściwości. Wartość `Name` właściwości nigdy nie może być zawartość tekstowa formantu edycji.|  
  
## <a name="required-ui-automation-control-patterns"></a>Wymagane wzorce sterowania automatyzacją interfejsu użytkownika  
 W poniższej tabeli wymieniono wzorce kontroli wymagane do obsługi przez wszystkie formanty siatki danych. Aby uzyskać więcej informacji na temat wzorców sterowania, zobacz [Omówienie wzorców sterowania automatyzacją interfejsu użytkownika](ui-automation-control-patterns-overview.md).  
  
|Wzór sterowania|Pomoc techniczna|Uwagi|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Tak|Formant siatki danych zawsze obsługuje wzorzec kontroli siatki, ponieważ elementy, które zawiera metadane, który jest rozmieszczona w siatce.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Zależy|Możliwość przewijania siatki danych zależy od zawartości i od tego, czy znajdują się paski przewijania.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Zależy|Możliwość wyboru siatki danych zależy od zawartości.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Tak|Formant siatki danych zawsze ma nagłówek w jego poddrzewie, więc wzorzec kontroli tabeli musi być obsługiwany.|  
  
 Elementy danych w kontenerach siatki danych będą obsługiwać co najmniej:  
  
- Wzorzec kontroli elementu zaznaczenia (jeśli siatka danych jest wybierana)  
  
- Przewiń wzorzec sterowania elementem (jeśli siatka danych jest przewijana)  
  
- Wzorzec formantu elementu siatki  
  
- TableItem — Wzorzec kontrolki  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Wymagane zdarzenia automatyzacji interfejsu użytkownika  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono zdarzenia, które mają być obsługiwane przez wszystkie formanty siatki danych. Aby uzyskać więcej informacji o zdarzeniach, zobacz [Omówienie zdarzeń automatyzacji interfejsu użytkownika](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Zdarzenie|Pomoc techniczna|Uwagi|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Zależy|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagany|Brak|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Jeśli formant obsługuje wzorzec przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Jeśli formant obsługuje wzorzec przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Jeśli formant obsługuje wzorzec przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Jeśli formant obsługuje wzorzec przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Jeśli formant obsługuje wzorzec przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Jeśli formant obsługuje wzorzec przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Wymagany|Brak|  
  
## <a name="date-grid-control-type-example"></a>Przykład typu formantu siatki daty  
 Na poniższej ilustracji przedstawiono formant widoku listy, który implementuje typ formantu DataGrid.  
  
 ![Grafika kontrolki widoku listy z dwoma elementami danych](./media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 Widok formantu i widok [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zawartości drzewa, który odnosi się do widoku listy kontroli jest wyświetlany poniżej. Wzorce sterowania dla każdego elementu automatyzacji są wyświetlane w nawiasach.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Drzewo — widok kontrolny|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Drzewo — widok zawartości|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|<ul><li>DataGrid (tabela, siatka, wybór)</li><li>Nagłówek<br /><br /> <ul><li>HeaderItem "Name" (Invoke)</li><li>HeaderItem "Data modyfikacji" (Invoke)</li><li>Nagłówek "Rozmiar" (Invoke)</li></ul></li><li>Grupa "Contoso" (TableItem, GridItem, SelectionItem,\*Table*, Grid )<br /><br /> <ul><li>DataItem "Rozrachunki z odbiorcami.doc" (SelectionItem, Invoke, TableItem\*, GridItem\*)</li><li>DataItem "Rozrachunki z dostawcami.doc" (SelectionItem, Invoke, TableItem\*, GridItem\*)</li></ul></li></ul>|<ul><li>DataGrid (tabela, siatka, wybór)</li><li>Grupa "Contoso" (TableItem, GridItem, SelectionItem,\*Table*, Grid )<br /><br /> <ul><li>DataItem "Rozrachunki z odbiorcami.doc" (SelectionItem, Invoke, TableItem\*, GridItem\*)</li><li>DataItem "Rozrachunki z dostawcami.doc" (SelectionItem, Invoke, TableItem\*, GridItem\*)</li></ul></li></ul>|  
  
 \*W poprzednim przykładzie pokazano DataGrid, który zawiera wiele poziomów formantów. Formant Grupy ("Contoso") zawiera dwa formanty DataItem ("Rozrachunki z odbiorcami.doc" i "Rozrachunki z dostawcami.doc"). Para DataGrid/GridItem jest niezależna od pary na innym poziomie. Formanty DataItem w ramach group mogą być również udostępniane jako typ formantu ListItem, dzięki czemu mają być prezentowane bardziej wyraźnie jako obiekty do wyboru, a nie jako proste elementy danych. W tym przykładzie nie obejmuje podelementów zgrupowanych elementów danych.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Automation.ControlType.DataGrid>
- [Typy kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-types-overview.md)
- [Przegląd automatyzacji interfejsu użytkownika](ui-automation-overview.md)
