---
title: Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu SplitButton
ms.date: 03/30/2017
helpviewer_keywords:
- Split Button control type
- control types, Split Button
- UI Automation, Split Button control type
ms.assetid: 14b05ccf-bcd8-4045-9bae-f7679cd98711
ms.openlocfilehash: b3b8346ca77110b811ee0b226bfa2b4cbf2e18db
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71041101"
---
# <a name="ui-automation-support-for-the-splitbutton-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu SplitButton
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 Ten temat zawiera informacje na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] temat obsługi typu formantu SplitButton. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie typ kontrolki jest zestawem warunków, które formant musi spełniać, aby można było <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> użyć właściwości. Warunki obejmują określone wytyczne dotyczące [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wartości właściwości i wzorców formantów.  
  
 Kontrolka przycisku podziału umożliwia wykonywanie akcji na formancie i rozszerzanie kontrolki, aby wyświetlić listę innych możliwych akcji, które można wykonać.  
  
 W poniższych sekcjach opisano wymaganą [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strukturę drzewa, właściwości, wzorce formantów i zdarzenia dla typu formantu SplitButton. Wymagania stosują się do wszystkich kontrolek przycisku podziału [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]bez względu na to, [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]czy. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]  
  
## <a name="required-ui-automation-tree-structure"></a>Wymagana struktura drzewa automatyzacji interfejsu użytkownika  
 W poniższej tabeli przedstawiono widok kontrolki i widok [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zawartości drzewa, które odnoszą się do podzielonych kontrolek przycisków i opisano, co może być zawarte w poszczególnych widokach. Aby uzyskać więcej informacji na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] temat drzewa, zobacz [Omówienie drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md).  
  
|Widok kontrolki|Widok zawartości|  
|------------------|------------------|  
|SplitButton<br /><br /> <ul><li>Obraz (0 lub 1)</li><li>Tekst (0 lub 1)</li><li>Przycisk (1 lub 2)<br /><br /> <ul><li>Menu (0 lub 1; pojawia się jako element podrzędny przycisku, który obsługuje wzorzec ExpandCollapse dla)</li><li>MenuItem (od 1 do wielu)</li></ul></li></ul>|SplitButton<br /><br /> -MenuItem (od 1 do wielu)|  
  
## <a name="required-ui-automation-properties"></a>Wymagane właściwości automatyzacji interfejsu użytkownika  
 Poniższa tabela zawiera listę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, których wartość lub definicja jest szczególnie istotna dla kontrolek przycisku podziału. Aby uzyskać więcej informacji [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] na temat właściwości, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Wartość|Wartość|Uwagi|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz uwagi.|Wartość tej właściwości musi być unikatowa dla wszystkich kontrolek w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz uwagi.|Najbardziej zewnętrzny prostokąt, który zawiera cały formant.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz uwagi.|Obsługiwane, jeśli istnieje prostokąt ograniczający. Jeśli nie każdy punkt wewnątrz prostokąta ograniczenia jest klikany, a będziesz wykonywał wyspecjalizowane Testy trafień, a następnie przesłonić i udostępnić punkt kliknięcia.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Zobacz uwagi.|Jeśli formant może odbierać fokus klawiatury, musi obsługiwać tę właściwość.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Wrocie|Nazwa kontrolki przycisku podziału jest wyświetlana na przycisku.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Null|Kontrolki przycisku podziału nie mają statycznej etykiety tekstowej.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|SplitButton|Ta wartość jest taka sama dla wszystkich platform interfejsu użytkownika.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"przycisk podziału"|Zlokalizowany ciąg odpowiadający typowi kontrolce SplitButton.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Zobacz uwagi.|Tekst pomocy może wskazywać wynik aktywowania przycisku podziału, który jest zazwyczaj tym samym typem informacji prezentowanym za pomocą etykietki narzędzia.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Prawda|Kontrolka przycisku podziału zawiera informacje dla użytkownika końcowego.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Prawda|Kontrolka przycisku podziału jest widoczna dla użytkownika końcowego.|  
  
## <a name="required-ui-automation-control-patterns"></a>Wymagane wzorce kontrolek automatyzacji interfejsu użytkownika  
 Poniższa tabela zawiera listę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wzorców formantów wymaganych do obsługi przez podzielone kontrolki przycisku. Aby uzyskać więcej informacji na temat wzorców kontrolek, zobacz [Omówienie wzorców kontrolek automatyzacji interfejsu użytkownika](ui-automation-control-patterns-overview.md).  
  
|Wzorzec kontrolki|Pomoc techniczna|Uwagi|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Wymagane|Przyciski podziału zawsze mają domyślną akcję skojarzoną z wywołaniem Invoke.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Wymagane|Przyciski Split zawsze mają możliwość rozwinięcia listy opcji.|  
  
## <a name="required-ui-automation-events"></a>Wymagane zdarzenia automatyzacji interfejsu użytkownika  
 Poniższa tabela zawiera listę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzeń wymaganych do obsługi przez wszystkie kontrolki przycisku podziału. Aby uzyskać więcej informacji na temat zdarzeń, zobacz [Omówienie zdarzeń automatyzacji interfejsu użytkownika](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Wydarzen|Pomoc techniczna|Uwagi|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagane|Brak|  
  
## <a name="splitbutton-control-example"></a>Przykład kontrolki SplitButton  
 Na poniższej ilustracji przedstawiono typ formantu SplitButton w kontrolce siatka danych.  
  
 ![Przycisk podziału](./media/uiauto-splitbutton-detailed.gif "uiauto_splitbutton_detailed")  
  
 Poniżej jest wyświetlany widok kontrolki i widok zawartości drzewa automatyzacji interfejsu użytkownika, które dotyczą kontrolki siatka danych i przycisk podziału. Wzorce kontrolki dla każdego elementu automatyzacji są wyświetlane w nawiasach.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Widok kontrolki drzewa|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Drzewo — widok zawartości|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|<ul><li>SplitButton "name" (Invoke, ExpandCollapse dla)</li><li>Przycisk "więcej opcji" (Invoke)<br /><br /> <ul><li>Menu</li><li>MenuItem</li><li>…</li></ul></li></ul>|<ul><li>SplitButton "name" (Invoke, ExpandCollapse dla)</li><li>Przycisk "więcej opcji" (Invoke)<br /><br /> <ul><li>Menu</li><li>MenuItem</li><li>…</li></ul></li></ul>|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Automation.ControlType.SplitButton>
- [Typy kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-types-overview.md)
- [Przegląd automatyzacji interfejsu użytkownika](ui-automation-overview.md)
