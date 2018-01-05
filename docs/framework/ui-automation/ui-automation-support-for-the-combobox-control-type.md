---
title: "Obsługa automatyzacji interfejsu użytkownika dla typu formantu ComboBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control types, Combo Box
- UI Automation, Combo Box control type
- ComboBox controls
ms.assetid: bb321126-4770-41da-983a-67b7b89d45dd
caps.latest.revision: "23"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: fb6729dbafff1b943cd698d9fac4ab5e0bae5a9b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-support-for-the-combobox-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ComboBox
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsługi dla typu formantu ComboBox. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typu formantu to zestaw warunków, które muszą spełniać formantu, aby można było używać <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> właściwości. Takie szczegółowe wytyczne dla [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wartości właściwości, wzorce formantu i [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia.  
  
 Pola kombi jest pole listy, w połączeniu z statyczną kontrolkę lub formant edycji, który wyświetla aktualnie zaznaczonego elementu w polu listy pola kombi. Pole listy części kontrolki jest wyświetlany przez cały czas lub jest wyświetlany tylko po wybraniu przez użytkownika (czyli przycisku) strzałkę listy rozwijanej obok kontrolki. Jeśli pole wyboru jest formant edycyjny, użytkownik może wprowadzić informacje, które nie jest na liście; w przeciwnym razie użytkownik może wybrać elementy na liście.  
  
 Następujące sekcje definiują wymaganych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa struktury, właściwości wzorców formantu i zdarzenia dla typu formantu ComboBox. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Wymagania dotyczą wszystkich formantów pól kombi, czy [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], lub [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Struktura drzewa automatyzacji interfejsu użytkownika wymagane  
 Poniższa tabela przedstawia kontroli i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, które odnoszą się do pola kombi steruje i opisano, jakie mogą być zawarte w każdym widoku. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, zobacz [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Kontrolki widoku|Widok zawartości|  
|------------------|------------------|  
|ComboBox<br /><br /> -Edytuj (0 lub 1)<br />-List (1)<br />-Listy elementów (podrzędnym listy; 0 do wielu)<br />-Button (1)|ComboBox<br /><br /> -Element list (od 0 do-wielu)|  
  
 Formant edycji w widoku kontrolki pola kombi jest konieczne tylko wtedy, gdy pole kombi mogą być edytowane podjęcie żadnych danych, tak jak w przypadku pola kombi, w oknie dialogowym Uruchamianie.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Właściwości automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, której wartość lub definicji jest szczególnie istotne kombi polu kontrolki. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Właściwość|Wartość|Uwagi|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz uwagi.|Wartość tej właściwości musi być unikatowy w obrębie wszystkich kontrolek w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz uwagi.|Prostokąt peryferyjnych zawiera całą formantu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz uwagi.|Obsługiwane w przypadku prostokąt ograniczający. Jeśli nie każdy punkt w obrębie prostokątem jest aktywne i wykonywać specjalne testowanie trafień, zastąpienia i podaj elementu do kliknięcia.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ComboBox|Ta wartość jest taka sama dla wszystkich [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] struktury.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Zobacz uwagi.|Tekst pomocy dla formantów pól kombi należy wyjaśnić, dlaczego użytkownik jest pytany można wybrać opcję z pola kombi. Tekst jest podobne do informacji przedstawionych w etykietce narzędzia. Na przykład "Wybierz element, aby ustawić rozdzielczości monitora."|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Wartość true|Formanty pola kombi zawsze znajdują się w widoku zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Wartość true|Formanty pola kombi zawsze znajdują się w widoku kontrolki [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Wartość true|Formanty pola kombi ujawnia zestaw elementów z kontener wyboru. Kontrolki pola kombi mogą odbierać fokus klawiatury, chociaż podczas automatyzacji interfejsu użytkownika klienta Ustawia priorytet dla pola kombi, wszystkie elementy w poddrzewie pole kombi może przyjmować fokus.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Zobacz uwagi.|Formanty pola kombi zwykle mają etykiety tekst statyczny, który odwołuje się do tej właściwości.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"pole kombi"|Zlokalizowany ciąg odpowiadający typu formantu ComboBox.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz uwagi.|Kontrolki pola kombi zazwyczaj otrzymuje zarejestrowaną nazwę z formantu tekst statyczny.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Wzorce formantów automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolować wzorce wymagane obsługiwane przez wszystkie formanty pola kombi. Aby uzyskać więcej informacji na wzorce formantów, zobacz [Przegląd wzorców formantu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|— Wzorzec formantu|Obsługa|Uwagi|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Tak|Kontrolki pola kombi musi zawsze zawierać przycisku rozwijanego, aby mogła być pola kombi.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Tak|Wyświetla bieżące zaznaczenie w polu kombi. Ta obsługa jest delegowane do pola listy poniżej pola kombi.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Zależy od|Jeśli pole kombi ma możliwość korzystania z wartości tekstowe dowolnego, wzorca wartości muszą być obsługiwane. Ten wzorzec umożliwia programowane Ustawianie zawartości ciągu pola kombi. Jeśli wzorzec wartość nie jest obsługiwana, oznacza to, że użytkownik musi dokonać wyboru z listy elementów w poddrzewie pola kombi.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Nigdy nie|Scroll — wzorzec nigdy nie jest obsługiwana w polu kombi bezpośrednio. Jeśli pole listy zawartych w polu kombi mogą być przewijane jest obsługiwane. Może być obsługiwana, tylko gdy pole listy ma widocznego na ekranie.|  
  
<a name="Required_Events"></a>   
## <a name="required-events"></a>Wymagane zdarzenia  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia wymagane obsługiwane przez wszystkie formanty pola kombi. Aby uzyskać więcej informacji dotyczących zdarzeń, zobacz [Przegląd zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Zdarzenia|Obsługa|Uwagi|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>Zdarzenie zmiany właściwości.|Zależy od|Jeśli formant obsługuje wzorca wartości, musi obsługiwać tego zdarzenia.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Automation.ControlType.ComboBox>  
 [Typy kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Przegląd automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-overview.md)
