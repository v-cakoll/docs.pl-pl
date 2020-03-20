---
title: Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ScrollBar
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Scroll Bar control type
- control types, Scroll Bar
- Scroll Bar control type
ms.assetid: 329891d7-b609-49e6-920a-09ea8a627d07
ms.openlocfilehash: 88a606369103e989b41ecf3569d54247cf3f83fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179617"
---
# <a name="ui-automation-support-for-the-scrollbar-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ScrollBar
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Ten temat zawiera [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informacje na temat obsługi typu formantu ScrollBar. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ formantu jest zestawem warunków, które <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> formant musi spełniać w celu użycia właściwości. Warunki obejmują szczegółowe [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wytyczne dotyczące [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa, wartości właściwości i wzorców kontroli.  
  
 Kontrolki paska przewijania umożliwiają użytkownikowi przewijanie zawartości w kontenerze okna lub elementu. Formant składa się z zestawu przycisków i kontrolki kciuka.  
  
 Poniższe sekcje definiują wymaganą [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strukturę drzewa, właściwości, wzorce kontroli i zdarzenia dla typu formantu ScrollBar. Wymagania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dotyczą wszystkich formantów [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]listy, niezależnie od tego, czy , Win32 lub Windows Forms.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Wymagana struktura drzewa automatyzacji interfejsu użytkownika  
 W poniższej tabeli przedstawiono widok formantu i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, który odnosi się do formantów paska przewijania i opisuje, co może być zawarte w każdym widoku. Aby uzyskać więcej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informacji na temat drzewa, zobacz [Omówienie drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md).  
  
|Widok sterowania|Widok zawartości|  
|------------------|------------------|  
|ScrollBar<br /><br /> - Przycisk (2 lub 4)<br />- Kciuk (0 lub 1)|Nie dotyczy. Formant paska przewijania nie zawiera zawartości.|  
  
 Formant paska przewijania zawsze ma od trzech do pięciu śmiga dzieci. Ponieważ poddrzewo ma więcej niż jeden kontrolka przycisku, należy ustawić określoną <xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty> wartość dla każdego elementu, aby były wykrywalne dla narzędzi automatyzacji testów.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Wymagane właściwości automatyzacji interfejsu użytkownika  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono właściwości, których wartość lub definicja jest szczególnie istotne dla formantów paska przewijania. Należy zauważyć, że kontrolka paska przewijania nigdy nie ma zawartości; jego funkcjonalność jest narażona za pośrednictwem wzorca kontroli przewijania, który jest obsługiwany w kontenerze przewijanym.  
  
 Aby uzyskać [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] więcej informacji o właściwościach, zobacz [Właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Właściwość|Wartość|Uwagi|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz notatki.|Wartość tej właściwości musi być unikatowa we wszystkich formantów w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz notatki.|Najbardziej zewnętrzny prostokąt, który zawiera cały formant.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Zobacz notatki.|Jeśli formant może odbierać fokus klawiatury, musi obsługiwać tę właściwość.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|`Null`|Formant paska przewijania nie `NameProperty` ma elementów zawartości i nie jest wymagane do ustawienia.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Nie jest to liczba.|Formant paska przewijania nie ma klikalnych punktów.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Paski przewijania nie mają etykiet.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ScrollBar|Ta wartość jest taka sama dla wszystkich struktur. Paski przewijania, które działają jako suwaki, muszą używać typu formantu Slider.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"pasek przewijania"|Zlokalizowany ciąg, który odpowiada typowi formantu Button.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|False|Formant paska przewijania nigdy nie jest elementem zawartości. Jeśli pasek przewijania jest formantem autonomicznym, musi on spełniać typ formantu Slider i zwracać `ControlType.Slider` dla `ControlType` właściwości.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Pasek przewijania musi być zawsze formantem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.OrientationProperty>|True|Formant paska przewijania musi zawsze ujawniać jego orientację poziomą lub pionową.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Wymagane wzorce sterowania automatyzacją interfejsu użytkownika  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono wzorce formantów, które muszą być obsługiwane przez kontrolki paska przewijania. Aby uzyskać więcej informacji na temat wzorców sterowania, zobacz [Omówienie wzorców sterowania automatyzacją interfejsu użytkownika](ui-automation-control-patterns-overview.md). Należy zauważyć, że gdy pasek przewijania jest używany jako formant tylko do manipulowania myszą, nie obsługuje wzorców sterowania. Jeśli jest używany jako formant suwaka w aplikacji, musi być nadany slider typu formantu.  
  
|Wzór sterowania|Pomoc techniczna|Uwagi|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Nigdy|Wzorzec kontroli przewijania nigdy nie jest bezpośrednio obsługiwany na pasku przewijania.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Zależy|Ta funkcja jest wymagana do obsługi tylko wtedy, gdy wzorzec kontroli przewijania nie jest obsługiwany w kontenerze, który ma pasek przewijania.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Wymagane zdarzenia automatyzacji interfejsu użytkownika  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono zdarzenia, które mają być obsługiwane przez wszystkie kontrolki paska przewijania. Aby uzyskać więcej informacji na temat zdarzeń, zobacz [Omówienie zdarzeń automatyzacji interfejsu użytkownika](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Zdarzenie|Wsparcie/wartość|Uwagi|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>zdarzenie, które uległo zmianie właściwości.|Nigdy|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>zdarzenie, które uległo zmianie właściwości.|Nigdy|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>zdarzenie, które uległo zmianie właściwości.|Nigdy|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>zdarzenie, które uległo zmianie właściwości.|Nigdy|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>zdarzenie, które uległo zmianie właściwości.|Nigdy|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>zdarzenie, które uległo zmianie właściwości.|Nigdy|Brak|  
|<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagany|Brak|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Automation.ControlType.ScrollBar>
- [Typy kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-types-overview.md)
- [Przegląd automatyzacji interfejsu użytkownika](ui-automation-overview.md)
