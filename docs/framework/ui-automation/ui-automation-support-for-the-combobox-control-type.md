---
title: Obsługa automatyzacji interfejsu użytkownika dla typu formantu ComboBox
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Combo Box
- UI Automation, Combo Box control type
- ComboBox controls
ms.assetid: bb321126-4770-41da-983a-67b7b89d45dd
ms.openlocfilehash: 2b1629adcc9e23294daa0512070089cc72ab5810
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179790"
---
# <a name="ui-automation-support-for-the-combobox-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla typu formantu ComboBox
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Ten temat zawiera [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informacje dotyczące obsługi typu formantu ComboBox. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ formantu jest zestawem warunków, które <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> formant musi spełniać w celu użycia właściwości. Warunki obejmują szczegółowe [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wytyczne dotyczące [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa, wartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, wzorców kontroli i zdarzeń.  
  
 Pole kombi to pole listy połączone z formantem statycznym lub formantem edycji, które wyświetla aktualnie zaznaczony element w części pola listy pola kombi. Część pola listy formantu jest wyświetlana przez cały czas lub pojawia się tylko wtedy, gdy użytkownik wybierze strzałkę rozwijaną (która jest przyciskiem) obok formantu. Jeśli pole zaznaczenia jest formantem edycji, użytkownik może wprowadzić informacje, których nie ma na liście; w przeciwnym razie użytkownik może wybrać tylko elementy na liście.  
  
 Poniższe sekcje definiują wymaganą [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strukturę drzewa, właściwości, wzorce kontroli i zdarzenia dla typu formantu ComboBox. Wymagania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dotyczą wszystkich formantów pola [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]kombi, niezależnie od tego, czy , Win32 lub Windows Forms.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Wymagana struktura drzewa automatyzacji interfejsu użytkownika  
 W poniższej tabeli przedstawiono widok formantu i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, który odnosi się do formantów pola kombi i opisuje, co może być zawarte w każdym widoku. Aby uzyskać więcej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informacji na temat drzewa, zobacz [Omówienie drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md).  
  
|Widok sterowania|Widok zawartości|  
|------------------|------------------|  
|ComboBox<br /><br /> - Edycja (0 lub 1)<br />- Lista (1)<br />- Pozycja listy (podrzędny listy; 0 do wielu)<br />- Przycisk (1)|ComboBox<br /><br /> - Pozycja listy (0 do wielu)|  
  
 Formant edycji w widoku kontrolnym pola kombi jest konieczny tylko wtedy, gdy pole kombi może być edytowane w celu podjęcia dowolnych danych wejściowych, tak jak w przypadku pola kombi w oknie dialogowym Uruchom.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Wymagane właściwości automatyzacji interfejsu użytkownika  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono właściwości, których wartość lub definicja jest szczególnie istotne dla formantów pola kombi. Aby uzyskać [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] więcej informacji o właściwościach, zobacz [Właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Właściwość|Wartość|Uwagi|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz notatki.|Wartość tej właściwości musi być unikatowa we wszystkich formantów w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz notatki.|Najbardziej zewnętrzny prostokąt, który zawiera cały formant.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz notatki.|Obsługiwane, jeśli istnieje prostokąt ograniczający. Jeśli nie każdy punkt w prostokątze ograniczającym jest klikalny i wykonujesz specjalistyczne testowanie trafień, a następnie zastądaj i podaj klikalny punkt.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ComboBox|Ta wartość jest taka [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] sama dla wszystkich struktur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Zobacz notatki.|Tekst pomocy dla formantów pola kombi powinien wyjaśniać, dlaczego użytkownik jest proszony o wybranie opcji z pola kombi. Tekst jest podobny do informacji prezentowanych za pośrednictwem etykietki narzędzia. Na przykład "Wybierz element, aby ustawić rozdzielczość ekranu monitora."|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Kontrolki pola kombi są zawsze uwzględniane w widoku zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Kontrolki pola kombi są zawsze uwzględniane w widoku kontrolnym [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|True|Kontrolki pola kombi uwidaczniają zestaw elementów z kontenera zaznaczenia. Formant pola kombi może odbierać fokus klawiatury, chociaż gdy klient automatyzacji interfejsu użytkownika ustawia fokus na polu kombi, wszystkie elementy w poddrzewie pola kombi mogą otrzymać fokus.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Zobacz notatki.|Formanty pola kombi zazwyczaj mają statyczną etykietę tekstową, do którego odwołuje się ta właściwość.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"pole kombi"|Zlokalizowany ciąg odpowiadający typowi formantu ComboBox.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz notatki.|Formant pola kombi zazwyczaj pobiera swoją nazwę od statycznego formantu tekstu.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Wymagane wzorce sterowania automatyzacją interfejsu użytkownika  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono wzorce kontroli wymagane do obsługi przez wszystkie formanty pola kombi. Aby uzyskać więcej informacji na temat wzorców sterowania, zobacz [Omówienie wzorców sterowania automatyzacją interfejsu użytkownika](ui-automation-control-patterns-overview.md).  
  
|Wzór sterowania|Pomoc techniczna|Uwagi|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Tak|Formant pola kombi musi zawsze zawierać przycisk rozwijany, aby być polem kombi.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Tak|Wyświetla bieżące zaznaczenie w polu kombi. Ta obsługa jest delegowana do pola listy pod polem kombi.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Zależy|Jeśli pole kombi ma możliwość podejmowania dowolnych wartości tekstowych, wzorzec wartość musi być obsługiwany. Ten wzorzec umożliwia programowe ustawianie zawartości ciągu pola kombi. Jeśli wzorzec wartość nie jest obsługiwany, oznacza to, że użytkownik musi dokonać wyboru z elementów listy w poddrzemieniu pola kombi.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Nigdy|Wzorzec przewijania nigdy nie jest obsługiwany bezpośrednio w polu kombi. Jest on obsługiwany, jeśli pole listy zawarte w polu kombi można przewijać. Może być obsługiwana tylko wtedy, gdy pole listy jest widoczne na ekranie.|  
  
<a name="Required_Events"></a>
## <a name="required-events"></a>Wymagane zdarzenia  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono zdarzenia, które mają być obsługiwane przez wszystkie kontrolki pola kombi. Aby uzyskać więcej informacji na temat zdarzeń, zobacz [Omówienie zdarzeń automatyzacji interfejsu użytkownika](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Zdarzenie|Pomoc techniczna|Uwagi|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagany|Brak|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Jeśli formant obsługuje wzorzec value, musi obsługiwać to zdarzenie.|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Automation.ControlType.ComboBox>
- [Typy kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-types-overview.md)
- [Przegląd automatyzacji interfejsu użytkownika](ui-automation-overview.md)
