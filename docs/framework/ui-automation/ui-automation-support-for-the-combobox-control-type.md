---
title: Obsługa automatyzacji interfejsu użytkownika dla typu formantu ComboBox
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Combo Box
- UI Automation, Combo Box control type
- ComboBox controls
ms.assetid: bb321126-4770-41da-983a-67b7b89d45dd
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 25d27faeac2c60a50801b817185aa1d5196e506d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398563"
---
# <a name="ui-automation-support-for-the-combobox-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ComboBox
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pomocy technicznej dla kontrolek typu ComboBox. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ formantu to zestaw warunków, które kontrolki muszą spełnić, aby można było używać <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> właściwości. Warunki obejmują konkretne wskazówki dotyczące [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wartości właściwości, wzorców kontrolek i [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia.  
  
 Pole kombi jest polem listy w połączeniu ze statyczną kontrolkę lub kontrolkę edycji, która wyświetla aktualnie wybranego elementu w polu listy pola kombi. Pole listy części kontrolki jest wyświetlana przez cały czas lub tylko jest wyświetlany, gdy użytkownik wybierze strzałkę listy rozwijanej, (czyli przycisku) obok formantu. Jeśli pole wyboru jest formant edycji, użytkownik może wprowadzić informacje, które nie ma na liście; w przeciwnym razie użytkownik może wybrać elementy na liście.  
  
 Poniższe sekcje definiują wymagane [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa struktury, właściwości, wzorców kontrolek i zdarzeń dla kontrolek typu ComboBox. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Wymagania mają zastosowanie do wszystkich formantów pola kombi, czy [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], lub [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Struktura drzewa automatyzacji interfejsu użytkownika wymagane  
 Poniższa tabela przedstawia kontroli i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewo, które odnoszą się do pola kombi kontroluje i w tym artykule opisano, jakie mogą być zawarte w każdym widoku. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, zobacz [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Formant widoku|Widok zawartości|  
|------------------|------------------|  
|ComboBox<br /><br /> -Edycji (0 lub 1)<br />-List (1)<br />-Lista elementu (element podrzędny elementu listy; 0 do wielu)<br />— Przycisk (1)|ComboBox<br /><br /> -Element list (od 0 do wielu)|  
  
 Kontrolka edycji w widoku kontrolki pola kombi jest konieczne tylko wtedy, gdy pole kombi można edytować w celu używane żadne dane wejściowe, tak jak w przypadku pola kombi w oknie dialogowym Uruchamianie.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Właściwości automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, których wartość lub definicji jest szczególnie istotne, aby pole kombi pola kontrolki. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Właściwość|Wartość|Uwagi|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz uwagi.|Wartość tej właściwości musi być unikatowa wśród wszystkich kontrolek w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz uwagi.|Najbardziej zewnętrznej prostokąt, który zawiera całą kontrolkę.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz uwagi.|Obsługiwane w przypadku prostokąt otaczający. W przeciwnym razie każdy punkt, w ramach prostokąt otaczający jest możesz klikać i wykonywać specjalne testowania trafień, zastąpić i zapewnienia elementu do kliknięcia.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ComboBox|Ta wartość jest taka sama dla wszystkich [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] struktur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Zobacz uwagi.|Tekst pomocy dla formantów pola kombi powinien wyjaśnić, dlaczego użytkownik zażądano wybierz odpowiednią opcję z pola kombi. Tekst jest podobny do informacje znajdujące się za pośrednictwem etykietka narzędzia. Na przykład "Wybierz element, aby ustawić rozdzielczość ekranu monitora."|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Formanty pola kombi zawsze znajdują się w widoku zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Formanty pola kombi zawsze znajdują się w widoku kontrolnym [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|True|Formanty pola kombi uwidocznić zbiór elementów w kontenerze zaznaczenia. Kontrolka pola kombi mogą otrzymać fokus klawiatury, chociaż podczas automatyzacji interfejsu użytkownika klienta Ustawia fokus na pole kombi, wszystkie elementy w zainstalowanym poddrzewie pole kombi może zostać ustawiony fokus.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Zobacz uwagi.|Formanty pola kombi zazwyczaj mają etykietę statyczny tekst, który odwołuje się do tej właściwości.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"pole kombi"|Zlokalizowany ciąg odpowiadający typowi kontrolki ComboBox.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz uwagi.|Kontrolka pola kombi zazwyczaj pobiera jego nazwę w kontrolce tekst statyczny.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Wzorce kontrolek automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolować wzorców, wymagane są obsługiwane przez wszystkie kontrolki pola kombi. Aby uzyskać więcej informacji na temat wzorców kontrolek, zobacz [Przegląd wzorców kontrolki automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|— Wzorzec kontrolki|Obsługa|Uwagi|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Tak|Kontrolka pola kombi musi zawsze zawierać przycisk listy rozwijanej, aby pola kombi.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Tak|Wyświetla bieżące zaznaczenie w polu kombi. Ta funkcja jest delegowane do pola listy poniżej pola kombi.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Zależy od|Jeśli pole kombi ma możliwość korzystania z wartości dowolnego tekstu, wzorca wartości muszą być obsługiwane. Ten wzorzec umożliwia programowe Ustawianie zawartość ciągu w polu kombi. Jeśli wzorzec wartość nie jest obsługiwana, oznacza to, czy użytkownik musi dokonać wyboru z listy elementów w poddrzewie pola kombi.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|nigdy nie|Wzorzec przewijania nigdy nie jest obsługiwana w polu kombi bezpośrednio. Jest ona obsługiwana przewinięciu zawartych w polu kombi pola listy. Może być obsługiwany, tylko gdy pola listy jest widoczne na ekranie.|  
  
<a name="Required_Events"></a>   
## <a name="required-events"></a>Wymaganych zdarzeń  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia wymagane są obsługiwane przez wszystkie kontrolki pola kombi. Aby uzyskać więcej informacji na temat zdarzeń, zobacz [Przegląd zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Zdarzenia|Obsługa|Uwagi|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> Zdarzenie zmiany właściwości.|Zależy od|Jeśli są obsługiwane przez kontrolkę wzorca wartości, musi obsługiwać to zdarzenie.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Automation.ControlType.ComboBox>  
 [Typy kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Przegląd automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-overview.md)
