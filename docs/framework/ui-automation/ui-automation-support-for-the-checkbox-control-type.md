---
title: Obsługa automatyzacji interfejsu użytkownika dla typu formantu CheckBox
ms.date: 03/30/2017
helpviewer_keywords:
- CheckBox control type
- control types, CheckBox
- UI Automation, CheckBox control type
ms.assetid: 9c2a0e70-3a39-4ba9-96ea-a7fe531fae9f
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 35b99c8cdbeaf5ac5f1e4f86ba40f1ce2e242c79
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407320"
---
# <a name="ui-automation-support-for-the-checkbox-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu CheckBox
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera informacje na temat [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] obsługi dla typu formantu CheckBox. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typu formantu to zestaw warunków, które muszą spełniać formantu, aby można było używać <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> właściwości. Takie szczegółowe wytyczne dla [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wartości właściwości i wzorce formantu.  
  
 Pole wyboru jest obiekt służący do wskazywania stanu, które użytkownicy mogą pracować z przechodzić w tym stanie. Pola wyboru prezentować albo pliku binarnego za (tak/nie), (włączony/wyłączony) lub wyższego (włączony, wyłączony, nieokreślone) opcja dla użytkownika.  
  
 Następujące sekcje definiują wymaganych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury, właściwości, wzorców formantu i zdarzenia dla typu formantu CheckBox drzewa. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Wymagania dotyczą wszystkich formanty pól wyboru, czy [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], lub [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Struktura drzewa automatyzacji interfejsu użytkownika wymagane  
 Poniższa tabela przedstawia kontroli i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, który dotyczy formanty pól wyboru, a w tym artykule opisano, jakie mogą być zawarte w każdym widoku. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, zobacz [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Kontrolki widoku|Widok zawartości|  
|------------------|------------------|  
|CheckBox|CheckBox|  
  
> [!NOTE]
>  Pola wyboru nigdy nie mają elementów podrzędnych w zawartości widoku lub formantu. Jeśli formant muszą zawierać elementy podrzędne, oznacza to, że można użyć innego typu formantu.  
  
### <a name="required-ui-automation-properties"></a>Właściwości automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, której wartość lub definicji jest szczególnie istotne, aby formanty pól wyboru. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Właściwość|Wartość|Uwagi|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz uwagi.|Wartość tej właściwości musi być unikatowy w obrębie wszystkich kontrolek w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz uwagi.|Prostokąt peryferyjnych zawiera całą formantu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz uwagi.|Obsługiwane w przypadku prostokąt ograniczający. Jeśli nie każdy punkt w obrębie prostokątem jest aktywne i wykonywać specjalne testowanie trafień, zastąpienia i podaj elementu do kliknięcia.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|CheckBox|Ta wartość jest taka sama dla wszystkich platform interfejsu użytkownika.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Wartość tej właściwości musi być zawsze wartość True. Oznacza to, że kontrolka pola wyboru zawsze muszą być zawarte w widoku zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Wartość tej właściwości musi być zawsze wartość True. Oznacza to, że kontrolka pola wyboru zawsze muszą być zawarte w widoku kontrolki z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Zobacz uwagi.|Formant może przyjmować fokus klawiatury, musi obsługiwać tej właściwości.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Pola wyboru są własnym etykietach kontrolek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"pole wyboru"|Zlokalizowany ciąg odpowiadający CheckBox — typ formantu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz uwagi.|Wartość formantu pole wyboru `Name` właściwość jest tekst, który jest wyświetlany obok pola zachowuje swój stan przełącznika.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Wzorce formantów automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolować wzorce wymagane obsługiwane przez wszystkie formanty pól wyboru. Aby uzyskać więcej informacji na temat wzorców formantu, zobacz [Przegląd wzorców formantu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|— Wzorzec formantu|Obsługa|Uwagi|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Wymagane|Umożliwia pole wyboru, aby ponownym jego trybami wewnętrzny programowo.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Zdarzeń automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia wymagane obsługiwane przez wszystkie formanty pól wyboru. Aby uzyskać więcej informacji o zdarzeniach, zobacz [Przegląd zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Zdarzenia|Obsługa|Uwagi|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
  
<a name="Default_Action"></a>   
## <a name="default-action"></a>Akcja domyślna  
 Domyślne działanie pole wyboru jest spowodować przycisk radiowy, aby stać się fokus i Przełącz swojego bieżącego stanu. Jak wspomniano wcześniej, pola wyboru przedstawia dane binarne (tak/nie) (/ Wyłącz) decyzja użytkownika lub wyższego (włączony, wyłączony, nieokreślone). Jeśli pole wyboru jest binarny domyślne działanie powoduje, że stan "on" jako "off" lub stanu "off" jako "on". Pole wyboru stanu wyższego cykle akcji domyślnej trybami pole wyboru w tej samej kolejności tak, jakby użytkownik wysłał kolejnych kliknięcia myszą do formantu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Automation.ControlType.CheckBox>  
 [Typy kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Przegląd automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-overview.md)
