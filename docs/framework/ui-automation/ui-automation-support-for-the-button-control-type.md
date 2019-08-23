---
title: Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu przycisk
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Button
- UI Automation, Button control type
- Button control type
ms.assetid: 057c983a-da83-4c50-86c7-26fe381076a6
ms.openlocfilehash: 01cdae7446464acc890c85b505c217170adcc90d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914217"
---
# <a name="ui-automation-support-for-the-button-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu przycisk
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 Ten temat zawiera informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pomocy technicznej dla kontrolek typu Button. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie typ kontrolki jest zestawem warunków, które formant musi spełniać, aby można było <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> użyć właściwości. Warunki obejmują określone wytyczne dotyczące [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wartości właściwości, wzorców formantów i [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzeń.  
  
 Przycisk to obiekt, z którym użytkownik współdziała, aby wykonać akcję taką jak przyciski **OK** i **Anuluj** w oknie dialogowym. Formant Button jest prostą kontrolką do uwidocznienia, ponieważ mapuje do jednego polecenia, które użytkownik chce wykonać.  
  
 W poniższych sekcjach opisano wymaganą [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strukturę drzewa, właściwości, wzorce formantów i zdarzenia dla typu formantu Button. Wymagania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stosują się do wszystkich kontrolek przycisku [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]niezależnie od [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]tego, czy.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Wymagana struktura drzewa automatyzacji interfejsu użytkownika  
 W poniższej tabeli przedstawiono widok kontrolki i widok [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zawartości drzewa, które odnoszą się do kontrolek przycisków i opisano, co może być zawarte w poszczególnych widokach. Aby uzyskać więcej informacji na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] temat drzewa, zobacz [Omówienie drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Widok kontrolki|Widok zawartości|  
|------------------|------------------|  
|Przycisk<br /><br /> -Image (0 lub więcej)<br />-Tekst (0 lub więcej)|Przycisk|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Wymagane właściwości automatyzacji interfejsu użytkownika  
 Poniższa tabela zawiera listę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, których wartość lub definicja jest szczególnie istotna dla formantów implementujących typ formantu Button (na przykład kontrolki przycisku). Aby uzyskać więcej informacji [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] na temat właściwości, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Wartość|Wartość|Uwagi|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>|Zobacz uwagi.|Kontrolka Button zazwyczaj musi obsługiwać klawisz akceleratora, aby umożliwić użytkownikowi końcowemu wykonywanie akcji, którą reprezentuje szybko z klawiatury.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz uwagi.|Wartość tej właściwości musi być unikatowa dla wszystkich kontrolek w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz uwagi.|Najbardziej zewnętrzny prostokąt, który zawiera cały formant.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz uwagi.|Obsługiwane, jeśli istnieje prostokąt ograniczający. Jeśli nie każdy punkt wewnątrz prostokąta ograniczenia jest klikany, a będziesz wykonywał wyspecjalizowane Testy trafień, a następnie przesłonić i udostępnić punkt kliknięcia.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Przycisk|Ta wartość jest taka sama dla wszystkich platform interfejsu użytkownika.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Zobacz uwagi.|Tekst pomocy może wskazywać końcowy wynik aktywowania przycisku. Jest to zazwyczaj ten sam typ informacji przedstawiony za pomocą etykietki narzędzia.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Prawda|Formant Button musi zawsze mieć wartość Content.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Prawda|Kontrolka przycisku musi być zawsze kontrolką.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Zobacz uwagi.|Jeśli formant może odbierać fokus klawiatury, musi obsługiwać tę właściwość.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Kontrolki przycisków są samodzielne etykietami według ich zawartości.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|przycisk|Zlokalizowany ciąg odpowiadający typowi kontrolce Button.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz uwagi.|Nazwa kontrolki przycisku jest tekstem, który jest używany do etykietowania. Za każdym razem, gdy obraz jest używany do etykietowania przycisku, tekst alternatywny musi być podany dla właściwości Nazwa przycisku.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Wymagane wzorce kontrolek automatyzacji interfejsu użytkownika  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wzorce kontrolki wymagane do obsługi przez wszystkie kontrolki przycisków. Aby uzyskać więcej informacji na temat wzorców kontroli, zobacz [Wzorce formantów automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Wzorzec kontrolki|Pomoc techniczna|Uwagi|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Zobacz uwagi.|Wszystkie przyciski powinny obsługiwać wzorzec kontrolki Invoke lub formant przełącznika. Wywołanie jest obsługiwane, gdy przycisk wykonuje polecenie na żądanie użytkownika. To polecenie mapuje do pojedynczej operacji, takiej jak wycinanie, kopiowanie, wklejanie lub usuwanie.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Zobacz uwagi.|Wszystkie przyciski powinny obsługiwać wzorzec kontrolki Invoke lub formant przełącznika. Przełącznik jest obsługiwany, jeśli przycisk może być przetworzony przez serię maksymalnie trzech stanów. Zwykle jest to widoczne jako przełącznik włączenia/wyłączenia dla określonych funkcji.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Zobacz uwagi.|Gdy przycisk jest hostowany jako element podrzędny przycisku podziału, przycisk podrzędny może obsługiwać wzorzec ExpandCollapse dla zamiast wzorca Invoke lub przełącznika. Wzorzec ExpandCollapse dla może służyć do otwierania lub zamykania menu lub innej struktury podrzędnej skojarzonej z elementem Button.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Wymagane zdarzenia automatyzacji interfejsu użytkownika  
 Poniższa tabela zawiera listę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzeń wymaganych do obsługi przez wszystkie kontrolki przycisków. Aby uzyskać więcej informacji na temat zdarzeń, zobacz [Omówienie zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Wydarzen|Pomoc techniczna|Uwagi|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Zależy od|Jeśli kontrolka obsługuje wzorzec kontrolki Invoke, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>zdarzenie zmiany właściwości.|Zależy od|Jeśli formant obsługuje wzorzec kontrolki Przełącz, musi obsługiwać to zdarzenie.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Automation.ControlType.Button>
- [Typy kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)
- [Przegląd automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-overview.md)
