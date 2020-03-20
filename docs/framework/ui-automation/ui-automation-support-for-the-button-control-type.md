---
title: Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu przycisk
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Button
- UI Automation, Button control type
- Button control type
ms.assetid: 057c983a-da83-4c50-86c7-26fe381076a6
ms.openlocfilehash: e98e027559be8c3e8ccdb4ac4369c09fd13805e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179845"
---
# <a name="ui-automation-support-for-the-button-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu przycisk
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Ten temat zawiera [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informacje dotyczące obsługi typu formantu Przycisk. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ formantu jest zestawem warunków, które <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> formant musi spełniać w celu użycia właściwości. Warunki obejmują szczegółowe [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wytyczne dotyczące [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa, wartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, wzorców kontroli i zdarzeń.  
  
 Przycisk jest obiektem, z który użytkownik wchodzi w interakcję w celu wykonania akcji, takiej jak przyciski **OK** i **Anuluj** w oknie dialogowym. Formant przycisku jest prosty formant do udostępnienia, ponieważ mapuje do jednego polecenia, które użytkownik chce wykonać.  
  
 Poniższe sekcje definiują wymaganą [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strukturę drzewa, właściwości, wzorce kontroli i zdarzenia dla typu formantu Button. Wymagania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dotyczą wszystkich formantów [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]przycisków, niezależnie od tego, czy , Win32 lub Windows Forms.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Wymagana struktura drzewa automatyzacji interfejsu użytkownika  
 W poniższej tabeli przedstawiono widok formantu i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, który odnosi się do formantów przycisków i opisuje, co może być zawarte w każdym widoku. Aby uzyskać więcej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informacji na temat drzewa, zobacz [Omówienie drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md).  
  
|Widok sterowania|Widok zawartości|  
|------------------|------------------|  
|Button<br /><br /> - Obraz (0 lub więcej)<br />- Tekst (0 lub więcej)|Button|  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Wymagane właściwości automatyzacji interfejsu użytkownika  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono właściwości, których wartość lub definicja jest szczególnie istotne dla formantów, które implementują button typu formantu (takich jak formanty przycisku). Aby uzyskać [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] więcej informacji o właściwościach, zobacz [Właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Właściwość|Wartość|Uwagi|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>|Zobacz notatki.|Button Formant zazwyczaj musi obsługiwać klawisz akceleratora, aby umożliwić użytkownikowi końcowemu wykonanie akcji, które reprezentuje szybko z klawiatury.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz notatki.|Wartość tej właściwości musi być unikatowa we wszystkich formantów w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz notatki.|Najbardziej zewnętrzny prostokąt, który zawiera cały formant.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz notatki.|Obsługiwane, jeśli istnieje prostokąt ograniczający. Jeśli nie każdy punkt w prostokątze ograniczającym jest klikalny i wykonujesz specjalistyczne testowanie trafień, a następnie zastądaj i podaj klikalny punkt.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Button|Ta wartość jest taka sama dla wszystkich struktur interfejsu użytkownika.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Zobacz notatki.|Tekst pomocy może wskazywać, jaki będzie efekt końcowy aktywacji przycisku. Zazwyczaj jest to ten sam typ informacji prezentowanych za pośrednictwem etykietki narzędzia.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Button Formant musi być zawsze zadowolony.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Button Formant musi być zawsze formantem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Zobacz notatki.|Jeśli formant może odbierać fokus klawiatury, musi obsługiwać tę właściwość.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Formanty przycisków są etykietowane przez ich zawartość.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"przycisk"|Zlokalizowany ciąg odpowiadający typowi formantu Button.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz notatki.|Nazwa formantu przycisku jest tekstem używanym do etykietowania. Za każdym razem, gdy obraz jest używany do etykietowania przycisku, tekst alternatywny musi być dostarczony dla właściwości Nazwa przycisku.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Wymagane wzorce sterowania automatyzacją interfejsu użytkownika  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono wzorce kontroli wymagane do obsługi przez wszystkie formanty przycisków. Aby uzyskać więcej informacji na temat wzorców sterowania, zobacz [Omówienie wzorców sterowania automatyzacją interfejsu użytkownika](ui-automation-control-patterns-overview.md).  
  
|Wzór sterowania|Pomoc techniczna|Uwagi|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Zobacz notatki.|Wszystkie przyciski powinny obsługiwać invoke wzorzec formantu lub wzorzec sterowania przełącz. Invoke jest obsługiwany, gdy przycisk wykonuje polecenie na żądanie użytkownika. To polecenie jest mapowana na pojedynczą operację, taką jak Wytnij, Kopiuj, Wklej lub Usuń.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Zobacz notatki.|Wszystkie przyciski powinny obsługiwać invoke wzorzec formantu lub wzorzec sterowania przełącz. Przełącznik jest obsługiwany, jeśli przycisk może być przełączane przez serię maksymalnie trzech stanów. Zazwyczaj jest to postrzegane jako przełącznik włączania / wyłączania dla określonych funkcji.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Zobacz notatki.|Gdy przycisk jest obsługiwany jako dziecko przycisku podziału, przycisk podrzędny może obsługiwać rozwiń wzorzec Rozwijajklucza zamiast wzorca Invoke lub Toggle. Rozwiń szyk może służyć do otwierania lub zamykania menu lub innej podstruktury skojarzonej z elementem przycisku.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Wymagane zdarzenia automatyzacji interfejsu użytkownika  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono zdarzenia, które muszą być obsługiwane przez wszystkie formanty przycisków. Aby uzyskać więcej informacji na temat zdarzeń, zobacz [Omówienie zdarzeń automatyzacji interfejsu użytkownika](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Zdarzenie|Pomoc techniczna|Uwagi|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagany|Brak|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Zależy|Jeśli formant obsługuje invoke wzorzec formantu, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Jeśli formant obsługuje wzorzec formantu Przełącz, musi obsługiwać to zdarzenie.|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Automation.ControlType.Button>
- [Typy kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-types-overview.md)
- [Przegląd automatyzacji interfejsu użytkownika](ui-automation-overview.md)
