---
title: Obsługa automatyzacji interfejsu użytkownika dla typu formantu HeaderItem
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Header Item control type
- Header Item control type
- control types, Header Item
ms.assetid: 09ce1310-ee31-493c-a71e-010bafc42fcf
ms.openlocfilehash: 57faebde753f6c18d8b92b0e11f8ff17837393db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179776"
---
# <a name="ui-automation-support-for-the-headeritem-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla typu formantu HeaderItem
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Ten temat zawiera [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informacje na temat obsługi typu formantu HeaderItem. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ formantu jest zestawem warunków, które <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> formant musi spełniać w celu użycia właściwości. Warunki obejmują szczegółowe [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wytyczne dotyczące [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa, wartości właściwości i wzorców kontroli.  
  
 Typ formantu HeaderItem zawiera etykietę wizualną dla wiersza lub kolumny informacji.  
  
 Formanty elementu nagłówka są przykładami formantów implementuujnych typu formantu HeaderItem. Wymagania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] w poniższych sekcjach dotyczą wszystkich formantów nagłówka, niezależnie od tego, czy [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Win32 lub Windows Forms.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Wymagana struktura drzewa automatyzacji interfejsu użytkownika  
 W poniższej tabeli przedstawiono widok formantu i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, który odnosi się do formantów elementu nagłówka i opisuje, co może być zawarte w każdym widoku. Aby uzyskać więcej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informacji na temat drzewa, zobacz [Omówienie drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md).  
  
|Widok sterowania|Widok zawartości|  
|------------------|------------------|  
|Headeritem|Brak|  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Wymagane właściwości automatyzacji interfejsu użytkownika  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono właściwości, których wartość lub definicja jest szczególnie istotne dla formantów elementu nagłówka. Aby uzyskać [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] więcej informacji o właściwościach, zobacz [Właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Właściwość|Wartość|Uwagi|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz notatki.|Wartość tej właściwości musi być unikatowa we wszystkich formantów w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz notatki.|Najbardziej zewnętrzny prostokąt, który zawiera cały formant.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz notatki.|Obsługiwane, jeśli istnieje prostokąt ograniczający. Jeśli nie każdy punkt w prostokątze ograniczającym jest klikalny i wykonujesz specjalistyczne testowanie trafień, a następnie zastądaj i podaj klikalny punkt.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Zobacz notatki.|Jeśli formant może odbierać fokus klawiatury, musi obsługiwać tę właściwość.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz notatki.|Formant elementu nagłówka jest zawsze samookadowanie.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`.|Formanty elementu nagłówka nie mają etykiety statycznej.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Headeritem|Ta wartość jest taka [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] sama dla wszystkich struktur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"element nagłówka"|Zlokalizowany ciąg dla typu formantu HeaderItem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|False|Formant elementu nagłówka nie jest uwzględniony [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] w widoku zawartości drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Formant elementu nagłówka jest zawsze uwzględniony [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] w widoku kontrolnym drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>|Zobacz notatki.|Ta właściwość zawiera informacje o zamówieniach sortowania według elementu nagłówka.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Wymagane wzorce sterowania automatyzacją interfejsu użytkownika  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono wzorce kontroli wymagane do obsługi przez wszystkie formanty elementu nagłówka. Aby uzyskać więcej informacji na temat wzorców sterowania, zobacz [Omówienie wzorców sterowania automatyzacją interfejsu użytkownika](ui-automation-control-patterns-overview.md).  
  
|Wzór sterowania|Pomoc techniczna|Uwagi|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider>|Zależy|Zaimplementuj ten wzorzec formantu, jeśli formant elementu nagłówka można zwymiarować.|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Zależy|Zaimplementuj ten wzorzec formantu, jeśli można kliknąć formant elementu nagłówka, aby posortować dane.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Wymagane zdarzenia automatyzacji interfejsu użytkownika  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono zdarzenia, które mają być obsługiwane przez wszystkie formanty elementu nagłówka. Aby uzyskać więcej informacji na temat zdarzeń, zobacz [Omówienie zdarzeń automatyzacji interfejsu użytkownika](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Zdarzenie|Pomoc techniczna|Uwagi|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Zależy|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagany|Brak|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Automation.ControlType.HeaderItem>
- [Typy kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-types-overview.md)
- [Przegląd automatyzacji interfejsu użytkownika](ui-automation-overview.md)
