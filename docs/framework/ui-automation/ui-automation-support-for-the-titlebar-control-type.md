---
title: Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu TitleBar
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Title Bar
- Title Bar control type
- UI Automation, Title Bar control type
ms.assetid: 3b7a4e13-0305-45d5-bc33-1f4133c50782
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 6ca737fc4c935fa8808e091ea425b8bd1415165b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33410432"
---
# <a name="ui-automation-support-for-the-titlebar-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu TitleBar
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsługi dla typu formantu TitleBar. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typu formantu to zestaw warunków, które muszą spełniać formantu, aby można było używać <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> właściwości. Takie szczegółowe wytyczne dla [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wartości właściwości i wzorce formantu.  
  
 Formanty paska tytułu reprezentują tytuły lub paski podpisu w oknie.  
  
 Następujące sekcje definiują wymaganych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury, właściwości, wzorców formantu i zdarzenia dla typu formantu TitleBar drzewa. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Wymagania dotyczą wszystkich kontrolek paska tytułu, czy [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], lub [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Struktura drzewa automatyzacji interfejsu użytkownika wymagane  
 Poniższa tabela przedstawia kontroli i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, które dotyczą paska tytułu steruje i opisano, jakie mogą być zawarte w każdym widoku. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, zobacz [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Kontrolki widoku|Widok zawartości|  
|------------------|------------------|  
|Pasek tytułu<br /><br /> -Menu (0 lub 1)<br />-Button (0 lub więcej)|Nie dotyczy. (formantu paska tytułu nie ma zawartości).|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Właściwości automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, której wartość lub definicji jest szczególnie istotne formanty pasek tytułu. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Właściwość|Wartość|Uwagi|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz uwagi.|Wartość tej właściwości musi być unikatowy w obrębie wszystkich kontrolek w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz uwagi.|Prostokąt ograniczający paska tytułu musi obejmować wszystkie formanty zawarte w nim.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz uwagi.|Obsługiwane w przypadku prostokąt ograniczający. Jeśli nie każdy punkt w obrębie prostokątem jest aktywne i wykonywać specjalne testowanie trafień, zastąpienia i podaj elementu do kliknięcia.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|False|Paski tytułu nigdy nie ma fokus klawiatury.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|""|Na pasku tytułu nie jest zawartości; jego informacji tekstowych jest narażony na okno nadrzędne.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Zobacz uwagi.|Formantu paska tytułu zwykle nie ma etykiety.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Pasek tytułu|Ta wartość jest taka sama dla wszystkich platform interfejsu użytkownika.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"pasek tytułu"|Zlokalizowany ciąg odpowiadający TitleBar — typ formantu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|False|Formantu paska tytułu nigdy nie jest zawartości.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Formantu paska tytułu zawsze musi być formantem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Zależy od|Ten formant zwróci wartość, w zależności od tego, czy pasek tytułu jest wyświetlany na ekranie.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|""|Nie jest konieczne do udostępnienia tekst pomocy.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>|""|Paski tytułu nigdy klawiszy skrótów.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>|""|Formantu paska tytułu nie ma klucza dostępu.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Wzorce formantów automatyzacji interfejsu użytkownika wymagane  
 TitleBar — typ formantu nie jest wymagany do obsługi dowolnej wzorce formantu. Działanie jest dostępne za pośrednictwem wzorca kontrolki okna w formancie okna.  
  
## <a name="required-ui-automation-events"></a>Zdarzeń automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia wymagane obsługiwane przez wszystkie formanty paska tytułu. Aby uzyskać więcej informacji o zdarzeniach, zobacz [Przegląd zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Zdarzenia|Obsługa|Uwagi|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> Zdarzenie zmiany właściwości.|Nigdy nie|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Nigdy nie|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagane|Brak|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Automation.ControlType.TitleBar>  
 [Typy kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Przegląd automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-overview.md)
