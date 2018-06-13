---
title: Obsługa automatyzacji interfejsu użytkownika dla formantów typu kalendarz
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Calendar control type
- Calendar control type
- control types, Calendar
ms.assetid: e91a7393-a7f9-4838-a1a6-857438b24bc9
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 752ac4cfddd5ca8c8b42d05e1a452cd0ef60ee36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409521"
---
# <a name="ui-automation-support-for-the-calendar-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu kalendarz
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsługę formantów typu kalendarz. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typu formantu to zestaw warunków, które muszą spełniać formantu, aby można było używać <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> właściwości. Takie szczegółowe wytyczne dla [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wartości właściwości, wzorce formantu i [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia.  
  
 Formanty kalendarza umożliwia łatwe Sprawdź datę i wybierz inne daty.  
  
 Następujące sekcje definiują wymaganych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury, właściwości, wzorce formantów i zdarzeń dla formantów typu kalendarz drzewa. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Wymagania dotyczą wszystkich kontrolek kalendarza, czy [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], lub [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Struktura drzewa automatyzacji interfejsu użytkownika wymagane  
 Poniższa tabela przedstawia kontroli i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, które odnoszą się do formantów kalendarza i w tym artykule opisano, jakie mogą być zawarte w każdym widoku. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, zobacz [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Kontrolki widoku|Widok zawartości|  
|------------------|------------------|  
|Kalendarz<br /><br /> <ul><li>DataGrid<br /><br /> <ul><li>Nagłówek (0 lub 1)</li><li>HeaderItem (0 lub 7; ilość zależy od tego, ile dni są wyświetlane w kolumnach)</li><li>ListItem (ilość zależy od liczby dni są wyświetlane)</li><li>Przycisk (0 lub 2; dla widoku kalendarza stronicowanie)</li></ul></li></ul>|Kalendarz<br /><br /> — ListItem (ilość zależy od liczby dni są wyświetlane)|  
  
 Formanty kalendarza ma być reprezentowane w wielu różnych formularzy w interfejsie użytkownika. Tylko formanty w widoku kontrolki z gwarantowane [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa są Siatka danych nagłówka, elementu nagłówka i kontrolki elementu listy.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Właściwości automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, której wartość lub definicji jest szczególnie istotne w formantach kalendarza. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Właściwość|Wartość|Uwagi|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz uwagi.|Wartość tej właściwości musi być unikatowy w obrębie wszystkich kontrolek w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz uwagi.|Prostokąt peryferyjnych zawiera całą formantu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz uwagi.|Obsługiwane w przypadku prostokąt ograniczający. Jeśli nie każdy punkt w obrębie prostokątem jest aktywne i wykonywać specjalne testowanie trafień, zastąpienia i podaj elementu do kliknięcia.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Kalendarz|Ta wartość jest taka sama dla wszystkich [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] struktury.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Formant kalendarza zawsze znajduje się w widoku zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Formant kalendarza zawsze znajduje się w widoku kontrolki [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Zobacz uwagi.|Formant może przyjmować fokus klawiatury, musi obsługiwać tej właściwości.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Zobacz uwagi.|Etykieta kontrolki dokumentu. Zazwyczaj jest używane tytuł dokumentu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"Kalendarz"|Zlokalizowany ciąg odpowiadający formantów typu kalendarz.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz uwagi.|Formant kalendarza zazwyczaj otrzymuje zarejestrowaną nazwę od bieżącej daty.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Wzorce formantów automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolować wzorce wymagane obsługiwane przez wszystkie formanty kalendarza. Aby uzyskać więcej informacji na wzorce formantów, zobacz [Przegląd wzorców formantu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Właściwość wzorzec/wzorzec formantu|Obsługa|Uwagi|  
|---------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Tak|Ponieważ dni miesiąca są elementy, które mogą zostać przesłane od formant kalendarza zawsze obsługuje wzorca siatki.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Zależy od|Formanty kalendarza większość obsługuje Przerzucanie widoku za pomocą stron. Scroll — wzorzec jest zalecane, aby zapewnić obsługę stronicowania nawigacji.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Zależy od|Formanty kalendarza większości zachować konkretny dzień, miesiąc lub rok jako zaznaczenia elementu podrzędnego. Niektóre kalendarze są wielokrotnego wyboru, a inne tylko pojedynczego wyboru.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Tak|Formant kalendarza zawsze ma nagłówek w jego poddrzewo dni tygodnia, dlatego wzorca tabeli muszą być obsługiwane.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Nie|Value — wzorzec formantu nie jest konieczne w formantach kalendarza, ponieważ nie można ustawić wartości bezpośrednio w formancie. Jeśli określonej daty jest skojarzony z formantem, informacje należy podawać przez Selection — wzorzec formantu.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Zdarzeń automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia wymagane obsługiwane przez wszystkie formanty kalendarza. Aby uzyskać więcej informacji o zdarzeniach, zobacz [Przegląd zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Zdarzenia|Obsługa|Uwagi|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty> Zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> Zdarzenie zmiany właściwości.|Zależy od|Jeśli formant obsługuje wzorca formantu przewijania, musi obsługiwać tego zdarzenia.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> Zdarzenie zmiany właściwości.|Zależy od|Jeśli formant obsługuje wzorca formantu przewijania, musi obsługiwać tego zdarzenia.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> Zdarzenie zmiany właściwości.|Zależy od|Jeśli formant obsługuje wzorca formantu przewijania, musi obsługiwać tego zdarzenia.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> Zdarzenie zmiany właściwości.|Zależy od|Jeśli formant obsługuje wzorca formantu przewijania, musi obsługiwać tego zdarzenia.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> Zdarzenie zmiany właściwości.|Zależy od|Jeśli formant obsługuje wzorca formantu przewijania, musi obsługiwać tego zdarzenia.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> Zdarzenie zmiany właściwości.|Zależy od|Jeśli formant obsługuje wzorca formantu przewijania, musi obsługiwać tego zdarzenia.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Wymagane|Brak|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Automation.ControlType.Calendar>  
 [Typy kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Przegląd automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-overview.md)
