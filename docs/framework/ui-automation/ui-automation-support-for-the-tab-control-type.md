---
title: Obsługa automatyzacji interfejsu użytkownika dla formantów typu karta
ms.date: 03/30/2017
helpviewer_keywords:
- TabControl type
- UI Automation, Tab control type
- control types, Tab
ms.assetid: f8be2732-836d-4e4d-85e2-73aa39479bf4
ms.openlocfilehash: 3970cdde3d4c2c421867fe47c77d76f8483965da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179561"
---
# <a name="ui-automation-support-for-the-tab-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla formantów typu karta
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Ten temat zawiera [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informacje dotyczące obsługi typu formantu Tabulator. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ formantu jest zestawem warunków, które <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> formant musi spełniać w celu użycia właściwości. Warunki obejmują szczegółowe [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wytyczne dotyczące [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]drzewa, wartości właściwości i . wzorców sterowania.  
  
 Formant tabulacji jest analogiczny do dzielników w notesie lub etykiet w szafce plików. Za pomocą kontrolki karty aplikacja może zdefiniować wiele stron dla tego samego obszaru okna lub okna dialogowego.  
  
 Poniższe sekcje definiują wymaganą [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strukturę drzewa, właściwości, wzorce kontroli i zdarzenia dla typu formantu Tabulator. Wymagania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dotyczą wszystkich formantów [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]kart, niezależnie od tego, czy , Win32 lub Windows Forms.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Wymagana struktura drzewa automatyzacji interfejsu użytkownika  
 W poniższej tabeli przedstawiono widok formantu i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, który odnosi się do formantów kart i opisuje, co może być zawarte w każdym widoku. Aby uzyskać więcej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informacji na temat drzewa, zobacz [Omówienie drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md).  
  
|Widok sterowania|Widok zawartości|  
|------------------|------------------|  
|Tab<br /><br /> <ul><li>TabItem (1 lub więcej)</li><li>Pasek przewijania (0 lub 1)<br /><br /> <ul><li>Przycisk (0 lub 2)</li></ul></li></ul>|Tab<br /><br /> - TabItem (1 lub więcej)|  
  
 Kontrolki [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabulatorów mają elementy podrzędne oparte na typie formantu Element karty. Gdy elementy karty są zgrupowane (na przykład jak w aplikacjach pakietu Microsoft Office 2007) typ formantu Tabulator może również obsługiwać typy formantów Grupy dla zgrupowanych elementów karty, zgodnie z poniższą strukturą drzewa.  
  
|Widok sterowania|Widok zawartości|  
|------------------|------------------|  
|Tab<br /><br /> <ul><li>TabItem (1 lub więcej)</li><li>Grupa (0 lub więcej)<br /><br /> <ul><li>TabItem (0 lub więcej)</li></ul></li><li>Pasek przewijania (0 lub więcej)<br /><br /> <ul><li>Przycisk (0 lub 2)</li></ul></li></ul>|Tab<br /><br /> <ul><li>TabItem (1 lub więcej)</li><li>Grupa (0 lub więcej)<br /><br /> <ul><li>TabItem (0 lub więcej)</li></ul></li></ul>|  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Wymagane właściwości automatyzacji interfejsu użytkownika  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono właściwości, których wartość lub definicja jest szczególnie istotne dla typu formantu Tabulator. Aby uzyskać [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] więcej informacji na temat właściwości, zobacz [Właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Właściwość|Wartość|Uwagi|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz notatki.|Wartość tej właściwości musi być unikatowa we wszystkich formantów w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz notatki.|Najbardziej zewnętrzny prostokąt, który zawiera cały formant.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Zobacz notatki.|Jeśli formant może odbierać fokus klawiatury, musi obsługiwać tę właściwość.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz notatki.|Formant karty rzadko wymaga Name właściwości.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Nie|Formant karty nie ma klikalny punkt.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Zobacz notatki.|Formanty tabulatorów zazwyczaj mają statyczną etykietę tekstową, która jest widoczna za pośrednictwem tej właściwości.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Tab|Ta wartość jest taka sama dla wszystkich struktur interfejsu użytkownika.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"zakładka"|Zlokalizowany ciąg odpowiadający typowi formantu Tabulatora.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|True|Typ formantu Tabulatora musi mieć możliwość odbierania fokusu klawiatury. Zazwyczaj [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klient wywołuje SetFocus na kontrolce karty i jeden z jego elementów przekaże fokus klawiatury do kontrolki karty. Jest możliwe dla niektórych kontenerów kart, aby skupić się bez ustawiania fokusu do jednego z jego elementów.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Formant karty jest zawsze uwzględniony w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] widoku zawartości drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Formant karty jest zawsze uwzględniony w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] widoku kontrolnym drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.OrientationProperty>|Zobacz notatki.|Formant karty musi zawsze wskazywać, czy jest umieszczony poziomo czy pionowo.|  
  
<a name="Required_UI_Automation_Control_Patterns_and_Properties"></a>
## <a name="required-ui-automation-control-patterns-and-properties"></a>Wymagane wzorce i właściwości automatyzacji interfejsu użytkownika  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono wzorce kontroli wymagane do obsługi przez wszystkie kontrolki kart. Aby uzyskać więcej informacji na temat wzorców sterowania, zobacz [Omówienie wzorców sterowania automatyzacją interfejsu użytkownika](ui-automation-control-patterns-overview.md).  
  
|Właściwość Forsowania szyku/szyku|Wsparcie/wartość|Uwagi|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Tak|Wszystkie kontrolki kart muszą obsługiwać wzorzec zaznaczenia.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|True|Kontrolki tabulatorów zawsze wymagają wyboru.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|False|Kontrolki kart są zawsze kontenerami z pojedynczym wyborem.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Zależy|Wzorzec przewijania musi być obsługiwany w formancie karty ma widżety, które umożliwiają przewijanie zestawu elementów karty.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Wymagane zdarzenia automatyzacji interfejsu użytkownika  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono zdarzenia, które muszą być obsługiwane przez wszystkie kontrolki kart. Aby uzyskać więcej informacji na temat zdarzeń, zobacz [Omówienie zdarzeń automatyzacji interfejsu użytkownika](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Zdarzenie|Pomoc techniczna|Uwagi|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagany|Brak|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Automation.ControlType.Tab>
- [Typy kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-types-overview.md)
- [Przegląd automatyzacji interfejsu użytkownika](ui-automation-overview.md)
