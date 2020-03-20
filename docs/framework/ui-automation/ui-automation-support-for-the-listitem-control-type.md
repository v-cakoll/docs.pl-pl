---
title: Obsługa automatyzacji interfejsu użytkownika dla typu formantu ListItem
ms.date: 03/30/2017
helpviewer_keywords:
- control types, List
- List Item control type
- UI Automation, List Item control type
ms.assetid: 34f533bf-fc14-4e78-8fee-fb7107345fab
ms.openlocfilehash: 245f9030897d54a2f1c95d5ce6369b67d23cb319
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179699"
---
# <a name="ui-automation-support-for-the-listitem-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla typu formantu ListItem
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Ten temat zawiera [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informacje <xref:System.Windows.Automation.ControlType.ListItem> na temat obsługi typu formantu. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ formantu jest zestawem warunków, które <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> formant musi spełniać w celu użycia właściwości. Warunki obejmują szczegółowe [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wytyczne dotyczące [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa, wartości właściwości i wzorców kontroli.  
  
 Formanty elementu listy są przykładem formantów, które implementują typ formantu ListItem.  
  
 Poniższe sekcje definiują wymaganą [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strukturę drzewa, właściwości, wzorce kontroli i zdarzenia dla typu formantu ListItem. Wymagania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dotyczą wszystkich formantów [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]listy, niezależnie od tego, czy , Win32 lub Windows Forms.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Wymagana struktura drzewa automatyzacji interfejsu użytkownika  
 W poniższej tabeli przedstawiono widok formantu i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, który odnosi się do formantów elementu listy i opisuje, co może być zawarte w każdym widoku. Aby uzyskać więcej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informacji na temat drzewa, zobacz [Omówienie drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md).  
  
|Widok sterowania|Widok zawartości|  
|------------------|------------------|  
|Listitem<br /><br /> - Obraz (0 lub więcej)<br />- Tekst (0 lub więcej)<br />- Edycja (0 lub więcej)|Listitem|  
  
 Element podrzędny formantu elementu listy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] w widoku zawartości drzewa musi być zawsze "0". Jeśli struktura formantu jest taka, że inne elementy są zawarte pod elementem listy, należy wykonać wymagania [dotyczące obsługi automatyzacji interfejsu użytkownika dla typu](ui-automation-support-for-the-treeitem-control-type.md) formantu typu kontroli interfejsu użytkownika.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Wymagane właściwości automatyzacji interfejsu użytkownika  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono właściwości, których wartość lub definicja jest szczególnie istotne dla formantów elementu listy. Aby uzyskać [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] więcej informacji na temat właściwości, zobacz [Właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Właściwość|Wartość|Uwagi|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz notatki.|Wartość tej właściwości musi być unikatowa we wszystkich formantów w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz notatki.|Ta wartość tej właściwości powinna zawierać obszar obrazu i zawartość tekstu elementu listy.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zależy|Jeśli formant listy ma klikalny punkt (punkt, który można kliknąć, aby spowodować, że lista ma fokus), a następnie ten punkt musi być narażony za pośrednictwem tej właściwości. Jeśli formant listy jest całkowicie objęte elementami <xref:System.Windows.Automation.NoClickablePointException> listy podrzędnej zostanie ono podnieść a, aby wskazać, że klient musi poprosić element wewnątrz formantu listy o klikalny punkt.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz notatki.|Wartość właściwości nazwa formantu elementu listy pochodzi z zawartości tekstowej elementu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Zobacz notatki.|Jeśli istnieje etykieta tekstu statycznego, ta właściwość musi ujawnić odwołanie do tego formantu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Listitem|Ta wartość jest taka sama dla wszystkich struktur interfejsu użytkownika.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"pozycja listy"|Zlokalizowany ciąg odpowiadający typowi formantu ListItem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Formant listy jest zawsze uwzględniony w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] widoku zawartości drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Formant listy jest zawsze uwzględniony w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] widoku formantu drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|True|Jeśli kontener może akceptować dane wejściowe klawiatury, wartość tej właściwości powinna być true.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|""|Tekst pomocy dla formantów listy powinien wyjaśniać, dlaczego użytkownik jest proszony o dokonanie wyboru z listy opcji, która jest zazwyczaj tego samego typu informacji prezentowanych za pośrednictwem etykietki narzędzia. Na przykład "Wybierz element, aby ustawić rozdzielczość ekranu dla monitora."|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Zależy|Ta właściwość powinna być widoczna dla formantów elementu listy, które reprezentują podstawowy obiekt. Te formanty elementu listy zazwyczaj mają ikonę skojarzoną z formantem, który użytkownicy kojarzą z obiektem źródłowym.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Zależy|Ta właściwość musi zwracać wartość, czy element listy jest obecnie przewijany do widoku w kontenerze nadrzędnym, który implementuje wzorzec kontroli przewijania.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Wymagane wzorce sterowania automatyzacją interfejsu użytkownika  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono wzorce kontroli wymagane do obsługi przez formanty elementu listy. Aby uzyskać więcej informacji na temat wzorców sterowania, zobacz [Omówienie wzorców sterowania automatyzacją interfejsu użytkownika](ui-automation-control-patterns-overview.md).  
  
|Wzór sterowania|Pomoc techniczna|Uwagi|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Tak|Formant elementu listy musi implementować ten wzorzec formantu. Dzięki temu elementy listy formantów do przekazywania, gdy są one zaznaczone.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Zależy|Jeśli element listy znajduje się w kontenerze, który można przewinąć, ten wzorzec formantu musi zostać zaimplementowany.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Zależy|Jeśli element listy jest sprawdzalny, a akcja nie wykonuje zmiany stanu zaznaczenia, należy zaimplementować ten wzorzec formantu.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Zależy|Jeśli element może być manipulowane, aby pokazać lub ukryć informacje, a następnie ten wzorzec kontroli musi być zaimplementowana.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Zależy|Jeśli element może być edytowany, to ten wzorzec formantu musi zostać zaimplementowany. Zmiany w formancie elementu listy spowodują zmiany wartości <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>i . <xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Zależy|Jeśli element do elementu nawigacji przestrzennej jest obsługiwany w kontenerze listy i kontener jest umieszczony w wierszach i kolumnach, a następnie wzorzec kontroli elementu siatki muszą być zaimplementowane.|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Zależy|Jeśli element ma polecenie, które można wykonać na nim, oddzielić od zaznaczenia, a następnie ten wzorzec musi być zaimplementowana. Zazwyczaj jest to akcja skojarzona z dwukrotnym kliknięciem formantu elementu listy. Przykładem może być uruchomienie dokumentu z Eksploratora Microsoft Windows lub odgrywania pliku muzycznego w programie Microsoft Windows Media Player.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Wymagane zdarzenia automatyzacji interfejsu użytkownika  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono zdarzenia, które mają być obsługiwane przez wszystkie formanty elementu listy. Aby uzyskać więcej informacji na temat zdarzeń, zobacz [Omówienie zdarzeń automatyzacji interfejsu użytkownika](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Zdarzenie|Pomoc techniczna|Uwagi|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Zależy|Brak|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Wymagany|Brak|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Wymagany|Brak|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Brak|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Brak|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Brak|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>zdarzenie, które uległo zmianie właściwości.|Zależy|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagany|Brak|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Automation.ControlType.ListItem>
- [Typy kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-types-overview.md)
- [Przegląd automatyzacji interfejsu użytkownika](ui-automation-overview.md)
