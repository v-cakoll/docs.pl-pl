---
title: Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu SplitButton
ms.date: 03/30/2017
helpviewer_keywords:
- Split Button control type
- control types, Split Button
- UI Automation, Split Button control type
ms.assetid: 14b05ccf-bcd8-4045-9bae-f7679cd98711
ms.openlocfilehash: 0c133704dda03f722aa1231b1eaf15e714082789
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206957"
---
# <a name="ui-automation-support-for-the-splitbutton-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu SplitButton
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pomocy technicznej dla kontrolek typu SplitButton. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ formantu to zestaw warunków, które kontrolki muszą spełnić, aby można było używać <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> właściwości. Warunki obejmują konkretne wskazówki dotyczące [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wartości właściwości i wzorce kontrolki.  
  
 Kontrolka przycisku podziału dają możliwość wykonywania akcji na kontrolki, a następnie rozwiń węzeł formantu, aby wyświetlić listę innych możliwych działań, które mogą być wykonywane.  
  
 Poniższe sekcje definiują wymagane [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa struktury, właściwości, wzorców kontrolek i zdarzeń dla kontrolek typu SplitButton. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Wymagania mają zastosowanie do wszystkich podziału tego, czy formanty przycisków [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], lub [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Struktura drzewa automatyzacji interfejsu użytkownika wymagane  
 Poniższa tabela przedstawia kontroli i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewo, które odnoszą się do kontrolek przycisku podziału, a w tym artykule opisano, jakie mogą być zawarte w każdym widoku. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, zobacz [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Formant widoku|Widok zawartości|  
|------------------|------------------|  
|SplitButton<br /><br /> <ul><li>Obraz (0 lub 1)</li><li>Tekst (0 lub 1)</li><li>Przycisk (1 lub 2)<br /><br /> <ul><li>Menu (0 lub 1; pojawia się jako element podrzędny przycisku, który obsługuje expandcollapse dla wzorca)</li><li>Element MenuItem (od 1 do wielu)</li></ul></li></ul>|SplitButton<br /><br /> — Element MenuItem (od 1 do wielu)|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Właściwości automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, których wartość lub definicji jest szczególnie istotne podzielić formanty przycisków. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Właściwość|Wartość|Uwagi|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz uwagi.|Wartość tej właściwości musi być unikatowa wśród wszystkich kontrolek w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz uwagi.|Najbardziej zewnętrznej prostokąt, który zawiera całą kontrolkę.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz uwagi.|Obsługiwane w przypadku prostokąt otaczający. W przeciwnym razie każdy punkt, w ramach prostokąt otaczający jest możesz klikać i wykonywać specjalne testowania trafień, zastąpić i zapewnienia elementu do kliknięcia.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Zobacz uwagi.|Formant może otrzymywać fokus klawiatury, musi obsługiwać tę właściwość.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|"Wróć"|Kontrolka przycisku podziału nazwa jest wyświetlana na przycisku.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Null|Kontrolki przycisku podziału nie ma etykiety tekst statyczny.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|SplitButton|Ta wartość jest taka sama dla wszystkich platform tworzenia interfejsu użytkownika.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"podziału button"|Zlokalizowany ciąg odpowiadający typowi kontrolki SplitButton.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Zobacz uwagi.|Tekst pomocy można wskazać wynik aktywacji przycisk podziału, zwykle jest to ten sam typ informacje znajdujące się za pośrednictwem etykietka narzędzia.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Prawda|Kontrolka przycisku podziału zawiera informacje dla użytkownika końcowego.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Prawda|Kontrolka przycisku podziału jest widoczna dla użytkownika końcowego.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Wzorce kontrolek automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolować wzorców, trzeba być obsługiwana przez kontrolki przycisku podziału. Aby uzyskać więcej informacji na temat wzorców kontrolek, zobacz [Przegląd wzorców kontrolki automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|— Wzorzec kontrolki|Pomoc techniczna|Uwagi|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Wymagane|Podziel przyciski zawsze mieć skojarzone z Wywołaj akcję domyślną.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Wymagane|Przyciski dzielone zawsze mieć możliwość zwiększania listy opcji.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Właściwości zdarzeń automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia wymagane są obsługiwane przez wszystkie kontrolki przycisku podziału. Aby uzyskać więcej informacji na temat zdarzeń, zobacz [Przegląd zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Zdarzenie|Pomoc techniczna|Uwagi|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagane|Brak|  
  
<a name="Split_Button_Control_Example"></a>   
## <a name="splitbutton-control-example"></a>Kontrolka SplitButton przykład  
 Na poniższym obrazie przedstawiono typ formantu SplitButton formantu siatki danych.  
  
 ![Split button](../../../docs/framework/ui-automation/media/uiauto-splitbutton-detailed.gif "uiauto_splitbutton_detailed")  
  
 Kontrolki i zawartości widok drzewa automatyzacji interfejsu użytkownika, które odnoszą się do kontrolki przycisku grid i podział danych jest wyświetlana poniżej. Wzorce kontrolki dla każdego elementu automatyzacji są wyświetlane w nawiasach.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Drzewo — widoku kontrolnym|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Drzewo — Widok zawartości|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|<ul><li>Przycisk podziału "Name" (expandcollapse dla wywołania)</li><li>Przycisk "Więcej opcji" (Wywołaj)<br /><br /> <ul><li>Menu</li><li>Element MenuItem</li><li>…</li></ul></li></ul>|<ul><li>Przycisk podziału "Name" (expandcollapse dla wywołania)</li><li>Przycisk "Więcej opcji" (Wywołaj)<br /><br /> <ul><li>Menu</li><li>Element MenuItem</li><li>…</li></ul></li></ul>|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Automation.ControlType.SplitButton>
- [Typy formantów automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)
- [Przegląd automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-overview.md)
