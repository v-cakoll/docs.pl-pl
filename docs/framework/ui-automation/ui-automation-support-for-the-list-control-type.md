---
title: Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu lista
ms.date: 03/30/2017
helpviewer_keywords:
- control types, List
- List control type
- UI Automation, List control type
ms.assetid: 0e959fcb-50f2-413b-948d-7167d279bc11
ms.openlocfilehash: 2926e06cfbe065ad8a5bccdb7ebaf16596721def
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179707"
---
# <a name="ui-automation-support-for-the-list-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu lista
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Ten temat zawiera [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informacje dotyczące obsługi typu formantu Lista. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ formantu jest zestawem warunków, które <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> formant musi spełniać w celu użycia właściwości. Warunki obejmują szczegółowe [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wytyczne dotyczące [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa, wartości właściwości i wzorców kontroli.  
  
 Typ formantu Lista umożliwia organizowanie płaskiej grupy lub grup elementów i umożliwia użytkownikowi wybranie jednego lub kilku z tych elementów. Typ formantu Lista ma luźne ograniczenie dotyczące typów elementów podrzędnych, które mogą zawierać. Dzięki temu dostawcy automatyzacji interfejsu użytkownika do obsługi dobrze znanego elementu dla kontenerów wyboru.  
  
 Wymagania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] w poniższych sekcjach mają zastosowanie do wszystkich formantów, które implementują typ formantu Lista, czy [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Win32 lub Windows Forms. Formanty kontenera listy są przykładem formantów, które implementują typ formantu Lista.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Wymagana struktura drzewa automatyzacji interfejsu użytkownika  
 W poniższej tabeli przedstawiono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dwa widoki drzewa, które odnoszą się do formantów listy i opisano, co może być zawarte w każdym widoku. Widok formantu zawiera tylko elementy, które są formantami, a widok zawartości usuwa zbędne informacje z drzewa. Na przykład formant tekstowy używany do oznaczania pola `ComboBox NameProperty`kombi będzie naświetlony jako . Ponieważ formant tekstu jest już narażony w ten sposób za pośrednictwem widoku formantu, nie jest konieczne, aby był dwukrotnie narażony; w związku z tym jest usuwany z widoku zawartości. Aby uzyskać więcej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informacji na temat drzewa, zobacz [Omówienie drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md).  
  
|Widok sterowania|Widok zawartości|  
|------------------|------------------|  
|Zawiera elementy, które odpowiadają formantom.|Usuwa zbędne informacje z drzewa, dzięki czemu technologie pomocnicze działają z najmniejszym zestawem istotnych informacji dla użytkownika końcowego.|  
|List<br /><br /> - DataItem (0 lub więcej)<br />- ListItem (0 lub więcej)<br />- Grupa (0 lub więcej)<br />- Pasek przewijania (0, 1 lub 2)|List<br /><br /> - DataItem (0 lub więcej)<br />- ListItem (0 lub więcej)<br />- Grupa (0 lub więcej)|  
  
 Widok formantu formantu implementujego typ formantu Lista (na przykład kontrolka listy) składa się z:  
  
- Zero lub więcej elementów w formancie listy (elementy mogą być oparte na typach kontroli elementu listy lub elementu danych).
  
- Zero lub więcej formantów grupy w formancie listy.
  
- Kontrolki paska przewijania zero, jeden lub dwa.
  
Widok zawartości formantu implementujnego typu formantu Lista (na przykład formantu listy) składa się z:  
  
- Zero lub więcej elementów w formancie listy (elementy mogą być oparte na typach kontroli elementu listy lub elementu danych).
  
- Zero lub więcej grup w formancie listy.

Formant listy nie może zawierać elementów, które mają relację hierarchiczną inną niż zgrupowanie. Jeśli elementy mają elementy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podrzędne w drzewie, a następnie kontener listy powinny być oparte na tree typu formantu.  
  
 Elementy do wyboru w formancie listy będą dostępne [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] z elementami podrzędnymi w drzewie formantu listy. Wszystkie elementy w formancie listy muszą należeć do tej samej grupy wyboru. Wybieralne elementy na liście powinny być udostępniane jako ListItem (zamiast DataItem) typy kontroli.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Wymagane właściwości automatyzacji interfejsu użytkownika  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono właściwości, których wartość lub definicja jest szczególnie istotne dla formantów listy. Aby uzyskać [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] więcej informacji na temat właściwości, zobacz [Właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Właściwość|Wartość|Uwagi|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz notatki.|Wartość tej właściwości musi być unikatowa we wszystkich formantów w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz notatki.|Najbardziej zewnętrzny prostokąt, który zawiera cały formant.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz notatki.|Jeśli formant listy ma klikalny punkt (punkt, który można kliknąć, aby spowodować, że lista ma fokus), a następnie ten punkt musi być narażony za pośrednictwem tej właściwości.<br /><br /> Jeśli wartość `IsOffScreen` właściwości jest true, <xref:System.Windows.Automation.NoClickablePointException> a następnie zostanie podniesiona.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Zobacz notatki.|Jeśli formant może odbierać fokus klawiatury, musi obsługiwać tę właściwość.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz notatki.|Wartość właściwości Name formantu listy powinna przekazać kategorię opcji, o które użytkownik jest proszony o wybranie. Ta właściwość zazwyczaj pobiera swoją nazwę od statycznej etykiety tekstowej. Jeśli nie ma etykiety tekstowej statycznej, deweloper aplikacji musi udostępnić wartość właściwości Name.<br /><br /> Tylko ten czas ta właściwość nie jest wymagana dla formantów listy jest, jeśli formant jest używany w poddrzewie innego formantu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Zobacz notatki.|Jeśli istnieje etykieta tekstu statycznego, ta właściwość musi ujawnić odwołanie do tego formantu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|List|Ta wartość jest taka sama dla wszystkich struktur interfejsu użytkownika.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"lista"|Zlokalizowany ciąg odpowiadający typowi formantu Lista.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Formant listy jest zawsze uwzględniony w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] widoku zawartości drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Formant listy jest zawsze uwzględniony w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] widoku formantu drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|True|Jeśli kontener może akceptować dane wejściowe klawiatury, wartość tej właściwości powinna być true.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Zobacz notatki.|Tekst pomocy dla formantów listy powinien wyjaśniać, dlaczego użytkownik jest proszony o dokonanie wyboru z listy opcji. Na przykład "Zaznaczenie elementu z tej listy ustawi rozdzielczość wyświetlania monitora".|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns-and-properties"></a>Wymagane wzorce i właściwości automatyzacji interfejsu użytkownika  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono wzorce kontroli wymagane do obsługi przez formanty listy. Aby uzyskać więcej informacji na temat wzorców sterowania, zobacz [Omówienie wzorców sterowania automatyzacją interfejsu użytkownika](ui-automation-control-patterns-overview.md).  
  
|Właściwość Forsowania szyku/szyku|Wsparcie/wartość|Uwagi|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Wymagany|Wszystkie formanty, które obsługują `ISelectionProvider` typ formantu Lista należy zaimplementować, gdy stan wyboru jest utrzymywany między elementami zawartymi w formancie. Jeśli elementy w kontenerze nie są wybierane, należy użyć typu formantu Grupa.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Zależy|Formanty listy nie zawsze wymagają wybrania elementu.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Zależy|Formanty listy mogą być kontenerami pojedynczych lub wielokrotnych.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Zależy|Zaimplementuj ten wzorzec formantu, jeśli elementy w kontenerze są przewijane.|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Zależy|Zaimplementuj ten wzorzec, gdy nawigacja siatki musi być dostępna dla elementu po elemencie.|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Zależy|Zaimplementuj ten wzorzec formantu, jeśli formant może obsługiwać wiele widoków elementów w kontenerze.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Nigdy|`ITableProvider`nigdy nie jest obsługiwany dla typu formantu Lista. Jeśli formant powinien obsługiwać ten wzorzec formantu, formant powinien być oparty na typie formantu siatki danych.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Wymagane zdarzenia automatyzacji interfejsu użytkownika  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono zdarzenia, które muszą być obsługiwane przez wszystkie formanty listy. Aby uzyskać więcej informacji na temat zdarzeń, zobacz [Omówienie zdarzeń automatyzacji interfejsu użytkownika](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Zdarzenie|Wsparcie/wartość|Uwagi|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Zależy|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Zależy|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagany|Brak|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Automation.ControlType.List>
- [Typy kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-types-overview.md)
- [Przegląd automatyzacji interfejsu użytkownika](ui-automation-overview.md)
