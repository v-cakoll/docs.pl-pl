---
title: Obsługa automatyzacji interfejsu użytkownika dla formantów typu kalendarz
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Calendar control type
- Calendar control type
- control types, Calendar
ms.assetid: e91a7393-a7f9-4838-a1a6-857438b24bc9
ms.openlocfilehash: b9b7e999c20c97acd1da4d6afedbac9177996ebe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179829"
---
# <a name="ui-automation-support-for-the-calendar-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla formantów typu kalendarz
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Ten temat zawiera [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informacje dotyczące obsługi typu formantu Kalendarz. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ formantu jest zestawem warunków, które <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> formant musi spełniać w celu użycia właściwości. Warunki obejmują szczegółowe [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wytyczne dotyczące [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa, wartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, wzorców kontroli i zdarzeń.  
  
 Kontrolki kalendarza umożliwiają użytkownikowi łatwe określenie daty i wybranie innych dat.  
  
 Poniższe sekcje definiują wymaganą [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strukturę drzewa, właściwości, wzorce kontroli i zdarzenia dla typu formantu Kalendarz. Wymagania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dotyczą wszystkich formantów [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]kalendarza, niezależnie od tego, czy , Win32 lub Windows Forms.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Wymagana struktura drzewa automatyzacji interfejsu użytkownika  
 W poniższej tabeli przedstawiono widok formantu i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, który odnosi się do formantów kalendarza i opisuje, co może być zawarte w każdym widoku. Aby uzyskać więcej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informacji na temat drzewa, zobacz [Omówienie drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md).  
  
|Widok sterowania|Widok zawartości|  
|------------------|------------------|  
|Kalendarz<br /><br /> <ul><li>DataGrid<br /><br /> <ul><li>Nagłówek (0 lub 1)</li><li>Element nagłówka (0 lub 7; ilość zależy od tego, ile dni jest wyświetlanych w kolumnach)</li><li>ListItem (ilość zależy od liczby wyświetlanych dni)</li><li>Przycisk (0 lub 2; dla widoku kalendarza stronicowania)</li></ul></li></ul>|Kalendarz<br /><br /> - ListItem (ilość zależy od tego, ile dni są wyświetlane)|  
  
 Kontrolki kalendarza mogą być reprezentowane w wielu różnych formach w interfejsie użytkownika. Jedynymi gwarantowanymi formantami w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] widoku kontrolnym drzewa są siatki danych, nagłówka, elementu nagłówka i formantów elementu listy.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Wymagane właściwości automatyzacji interfejsu użytkownika  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono właściwości, których wartość lub definicja jest szczególnie istotne dla formantów kalendarza. Aby uzyskać [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] więcej informacji na temat właściwości, zobacz [Właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Właściwość|Wartość|Uwagi|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz notatki.|Wartość tej właściwości musi być unikatowa we wszystkich formantów w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz notatki.|Najbardziej zewnętrzny prostokąt, który zawiera cały formant.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz notatki.|Obsługiwane, jeśli istnieje prostokąt ograniczający. Jeśli nie każdy punkt w prostokątze ograniczającym jest klikalny i wykonujesz specjalistyczne testowanie trafień, a następnie zastądaj i podaj klikalny punkt.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Kalendarz|Ta wartość jest taka [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] sama dla wszystkich struktur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Formant kalendarza jest zawsze uwzględniony [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] w widoku zawartości drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Formant kalendarza jest zawsze uwzględniony [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] w widoku kontrolnym drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Zobacz notatki.|Jeśli formant może odbierać fokus klawiatury, musi obsługiwać tę właściwość.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Zobacz notatki.|Etykieta formantu dokumentu. Zazwyczaj używany jest tytuł dokumentu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"kalendarz"|Zlokalizowany ciąg odpowiadający typowi formantu Kalendarz.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz notatki.|Formant kalendarza zazwyczaj pobiera swoją nazwę od daty bieżącego dnia.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Wymagane wzorce sterowania automatyzacją interfejsu użytkownika  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono wzorce kontroli wymagane do obsługi przez wszystkie formanty kalendarza. Aby uzyskać więcej informacji na temat wzorców sterowania, zobacz [Omówienie wzorców sterowania automatyzacją interfejsu użytkownika](ui-automation-control-patterns-overview.md).  
  
|Właściwość Forsowania szyku/szyku|Pomoc techniczna|Uwagi|  
|---------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Tak|Formant kalendarza zawsze obsługuje Grid wzorzec, ponieważ dni w ciągu miesiąca są elementy, które mogą być nawigowane przestrzennie.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Zależy|Większość formantów kalendarza obsługuje przerzucanie widoku według strony. Wzorzec przewijania jest zalecane w celu obsługi nawigacji stronicowania.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Zależy|Większość formantów kalendarza zachowuje określony dzień, miesiąc lub rok jako wybór podelementu. Niektóre kalendarze można wybierać wielokrotnie, a inne tylko z jednym wyborem.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Tak|Formant kalendarza zawsze ma nagłówek w jego poddrzewie dla dni tygodnia, więc wzorzec tabeli musi być obsługiwany.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Nie|Wzorzec kontroli wartości nie jest konieczne dla formantów kalendarza, ponieważ nie można ustawić wartość bezpośrednio na formancie. Jeśli określona data jest skojarzona z formantem, informacje powinny być dostarczane przez wzorzec kontroli wyboru.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Wymagane zdarzenia automatyzacji interfejsu użytkownika  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono zdarzenia, które muszą być obsługiwane przez wszystkie formanty kalendarza. Aby uzyskać więcej informacji o zdarzeniach, zobacz [Omówienie zdarzeń automatyzacji interfejsu użytkownika](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Zdarzenie|Pomoc techniczna|Uwagi|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagany|Brak|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Jeśli formant obsługuje wzorzec kontroli przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Jeśli formant obsługuje wzorzec kontroli przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Jeśli formant obsługuje wzorzec kontroli przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Jeśli formant obsługuje wzorzec kontroli przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Jeśli formant obsługuje wzorzec kontroli przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Jeśli formant obsługuje wzorzec kontroli przewijania, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Wymagany|Brak|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Automation.ControlType.Calendar>
- [Typy kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-types-overview.md)
- [Przegląd automatyzacji interfejsu użytkownika](ui-automation-overview.md)
