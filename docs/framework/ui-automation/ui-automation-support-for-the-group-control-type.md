---
title: Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu grupa
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Group control type
- Group control type
- control types, Group
ms.assetid: 18e01bab-01f8-4567-b867-88dce9c4a435
ms.openlocfilehash: 3044461d6d8cd157c06c48f236e1c13005774d00
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179747"
---
# <a name="ui-automation-support-for-the-group-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu grupa
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Ten temat zawiera [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informacje na temat obsługi typu formantu Grupa. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ formantu jest zestawem warunków, które <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> formant musi spełniać w celu użycia właściwości. Warunki obejmują szczegółowe [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wytyczne dotyczące [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa, wartości właściwości i [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wzorców kontroli.  
  
 Formant grupy reprezentuje węzeł w hierarchii. Typ formantu Grupa tworzy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] separację w drzewie, więc elementy, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] które są zgrupowane razem mają logiczny podział w drzewie.  
  
 Poniższe sekcje definiują wymaganą [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strukturę drzewa, właściwości, wzorce kontroli i zdarzenia dla typu formantu Grupa. Wymagania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dotyczą wszystkich formantów [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]grupy, niezależnie od tego, czy , Win32 lub Windows Forms.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Wymagana struktura drzewa automatyzacji interfejsu użytkownika  
 W poniższej tabeli przedstawiono widok formantu i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, który odnosi się do formantów grupy i opisuje, co może być zawarte w każdym widoku. Aby uzyskać więcej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informacji na temat drzewa, zobacz [Omówienie drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md).  
  
|Widok sterowania|Widok zawartości|  
|------------------|------------------|  
|Grupa<br /><br /> - 0 lub wiele elementów sterujących|Grupa<br /><br /> - 0 lub wiele elementów sterujących|  
  
 Zazwyczaj formanty grupy będą miały [obsługę automatyzacji interfejsu użytkownika dla typu kontroli zawartości listy,](ui-automation-support-for-the-listitem-control-type.md) [obsługę automatyzacji interfejsu](ui-automation-support-for-the-treeitem-control-type.md)użytkownika dla typu kontroli interfejsu użytkownika lub [obsługę automatyzacji interfejsu użytkownika dla](ui-automation-support-for-the-dataitem-control-type.md) typów typów typów kontroli interfejsu użytkownika znalezionych pod nimi w poddrzewie. Ponieważ "Group" jest kontenerem rodzajowym, jest możliwe dla dowolnego typu formantu, aby być pod group kontroli w drzewie.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Wymagane właściwości automatyzacji interfejsu użytkownika  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono właściwości, których wartość lub definicja jest szczególnie istotne dla formantów grupy. Aby uzyskać [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] więcej informacji o właściwościach, zobacz [Właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Właściwość|Wartość|Uwagi|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz notatki.|Wartość tej właściwości musi być unikatowa we wszystkich formantów w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz notatki.|Najbardziej zewnętrzny prostokąt, który zawiera cały formant.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz notatki.|Obsługiwane, jeśli istnieje prostokąt ograniczający. Jeśli nie każdy punkt w prostokątze ograniczającym jest klikalny i wykonujesz specjalistyczne testowanie trafień, a następnie zastądaj i podaj klikalny punkt.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Zobacz notatki.|Jeśli formant może odbierać fokus klawiatury, musi obsługiwać tę właściwość.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz notatki.|Formant grupy zazwyczaj pobiera swoją nazwę od tekstu, który etykiety formantu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Zobacz notatki.|Formanty grupy są zazwyczaj samookadowanie. W takich `null` przypadkach wróć tutaj. Jeśli istnieje statyczna etykieta tekstowa dla grupy, to, że musi być zwrócony jako wartość LabeledBy właściwości.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Grupa|Ta wartość jest taka sama dla wszystkich struktur interfejsu użytkownika.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"grupa"|Zlokalizowany ciąg odpowiadający typowi formantu Grupa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Formant grupy jest zawsze uwzględniony w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] widoku zawartości drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Grupa kalendarza jest zawsze uwzględniona w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] widoku kontrolnym drzewa.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Wymagane wzorce sterowania automatyzacją interfejsu użytkownika  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono wzorce kontroli wymagane do obsługi dla typu formantu Grupa. Aby uzyskać więcej informacji na temat wzorców sterowania, zobacz [Omówienie wzorców sterowania automatyzacją interfejsu użytkownika](ui-automation-control-patterns-overview.md).  
  
|Wzór sterowania|Pomoc techniczna|Uwagi|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Zależy|Formanty grupy, które mogą być używane do pokazywalania lub ukrywania informacji, muszą obsługiwać wzorzec Rozwijanie zwijania.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Wymagane zdarzenia automatyzacji interfejsu użytkownika  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono zdarzenia, które muszą być obsługiwane przez wszystkie formanty grupy. Aby uzyskać więcej informacji o zdarzeniach, zobacz [Omówienie zdarzeń automatyzacji interfejsu użytkownika](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Zdarzenie|Pomoc techniczna|Uwagi|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Brak|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagany|Brak|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Automation.ControlType.Group>
- [Typy kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-types-overview.md)
- [Przegląd automatyzacji interfejsu użytkownika](ui-automation-overview.md)
