---
title: Obsługa automatyzacji interfejsu użytkownika dla formantów typu kalendarz
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Calendar control type
- Calendar control type
- control types, Calendar
ms.assetid: e91a7393-a7f9-4838-a1a6-857438b24bc9
ms.openlocfilehash: 082325aede46501ade15fce60e6ef06e3d3ecf39
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914206"
---
# <a name="ui-automation-support-for-the-calendar-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla formantów typu kalendarz
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 Ten temat zawiera informacje na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] temat obsługi typu formantu kalendarza. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie typ kontrolki jest zestawem warunków, które formant musi spełniać, aby można było <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> użyć właściwości. Warunki obejmują określone wytyczne dotyczące [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wartości właściwości, wzorców formantów i [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzeń.  
  
 Formanty kalendarza pozwalają użytkownikowi łatwo określić datę i wybrać inne daty.  
  
 W poniższych sekcjach opisano wymaganą [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strukturę drzewa, właściwości, wzorce formantów i zdarzenia dla typu formantu kalendarza. Wymagania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dotyczą wszystkich formantów kalendarza, niezależnie od tego [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]czy, [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], czy.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Wymagana struktura drzewa automatyzacji interfejsu użytkownika  
 W poniższej tabeli przedstawiono widok kontrolki i widok [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zawartości drzewa, które odnoszą się do kontrolek kalendarz i opisano, co może być zawarte w poszczególnych widokach. Aby uzyskać więcej informacji na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] temat drzewa, zobacz [drzewo automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Widok kontrolki|Widok zawartości|  
|------------------|------------------|  
|Kalendarz<br /><br /> <ul><li>DataGrid<br /><br /> <ul><li>Nagłówek (0 lub 1)</li><li>HeaderItem (0 lub 7; ilość zależy od liczby dni wyświetlania w kolumnach)</li><li>Element ListItem (ilość zależy od liczby wyświetlanych dni)</li><li>Przycisk (0 lub 2; dla widoku kalendarza stronicowania)</li></ul></li></ul>|Kalendarz<br /><br /> -ListItem (ilość zależy od liczby wyświetlanych dni)|  
  
 Formanty kalendarza mogą być reprezentowane w wielu różnych formularzach w interfejsie użytkownika. Jedyne gwarantowane kontrolki, które mają być widoczne w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] widoku sterowania drzewa, to siatka danych, nagłówek, element nagłówka i kontrolki elementu listy.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Wymagane właściwości automatyzacji interfejsu użytkownika  
 Poniższa tabela zawiera listę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, których wartość lub definicja jest szczególnie istotna dla formantów kalendarza. Aby uzyskać więcej informacji [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] na temat właściwości, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Wartość|Wartość|Uwagi|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz uwagi.|Wartość tej właściwości musi być unikatowa dla wszystkich kontrolek w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz uwagi.|Najbardziej zewnętrzny prostokąt, który zawiera cały formant.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz uwagi.|Obsługiwane, jeśli istnieje prostokąt ograniczający. Jeśli nie każdy punkt wewnątrz prostokąta ograniczenia jest klikany, a będziesz wykonywał wyspecjalizowane Testy trafień, a następnie przesłonić i udostępnić punkt kliknięcia.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Kalendarz|Ta wartość jest taka sama dla wszystkich [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] platform.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Prawda|Kontrolka Calendar jest zawsze uwzględniona w widoku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zawartości drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Prawda|Kontrolka Calendar jest zawsze uwzględniona w widoku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolki drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Zobacz uwagi.|Jeśli formant może odbierać fokus klawiatury, musi obsługiwać tę właściwość.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Zobacz uwagi.|Etykieta kontrolki dokumentu. Zwykle jest używany tytuł dokumentu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|Kalendarz|Zlokalizowany ciąg odpowiadający typowi formantu kalendarza.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz uwagi.|Kontrolka Calendar zazwyczaj pobiera swoją nazwę z bieżącej daty dnia.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Wymagane wzorce kontrolek automatyzacji interfejsu użytkownika  
 Poniższa tabela zawiera listę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wzorców formantów wymaganych do obsługi przez wszystkie kontrolki kalendarza. Aby uzyskać więcej informacji na temat wzorców kontroli, zobacz [Wzorce formantów automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Wzorzec kontrolki/Właściwość wzorca|Pomoc techniczna|Uwagi|  
|---------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Tak|Kontrolka Calendar zawsze obsługuje wzorzec siatki, ponieważ dni w miesiącu to elementy, które mogą być przechodzące w przestrzenne.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Zależy od|Większość formantów kalendarza obsługuje przerzucanie stron widoku przez. Wzorzec przewijania jest zalecany w celu obsługi nawigacji stronicowania.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Zależy od|Większość formantów kalendarza zachowuje określony dzień, miesiąc lub rok jako zaznaczenie elementu podrzędnego. Niektóre kalendarze są wybierane do wyboru, a inne tylko pojedynczo.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Tak|Kontrolka Calendar zawsze ma nagłówek w jego poddrzewie na dni tygodnia, więc wzorzec tabeli musi być obsługiwany.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Nie|Wzorzec kontroli wartości nie jest wymagany w przypadku formantów kalendarza, ponieważ nie można ustawić wartości bezpośrednio w kontrolce. Jeśli określona data jest skojarzona z kontrolką, informacje powinny być dostarczone przez wzorzec kontrolki wyboru.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Wymagane zdarzenia automatyzacji interfejsu użytkownika  
 Poniższa tabela zawiera listę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzeń wymaganych do obsługi przez wszystkie formanty kalendarza. Aby uzyskać więcej informacji na temat zdarzeń, zobacz [Omówienie zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Wydarzen|Pomoc techniczna|Uwagi|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>zdarzenie zmiany właściwości.|Zależy od|Jeśli formant obsługuje wzorzec kontrolki przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>zdarzenie zmiany właściwości.|Zależy od|Jeśli formant obsługuje wzorzec kontrolki przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>zdarzenie zmiany właściwości.|Zależy od|Jeśli formant obsługuje wzorzec kontrolki przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>zdarzenie zmiany właściwości.|Zależy od|Jeśli formant obsługuje wzorzec kontrolki przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>zdarzenie zmiany właściwości.|Zależy od|Jeśli formant obsługuje wzorzec kontrolki przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>zdarzenie zmiany właściwości.|Zależy od|Jeśli formant obsługuje wzorzec kontrolki przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Wymagane|Brak|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Automation.ControlType.Calendar>
- [Typy kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)
- [Przegląd automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-overview.md)
