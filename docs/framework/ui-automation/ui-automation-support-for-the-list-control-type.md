---
title: Obsługa automatyzacji interfejsu użytkownika dla formantów typu lista
ms.date: 03/30/2017
helpviewer_keywords:
- control types, List
- List control type
- UI Automation, List control type
ms.assetid: 0e959fcb-50f2-413b-948d-7167d279bc11
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: f715f183642af6e98079171f41c0e76318052809
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ui-automation-support-for-the-list-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu lista
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsługę formantów typu Lista. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typu formantu to zestaw warunków, które muszą spełniać formantu, aby można było używać <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> właściwości. Takie szczegółowe wytyczne dla [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wartości właściwości i wzorce formantu.  
  
 List — typ formantu umożliwia organizowanie płaskiej grupy lub grup elementów i umożliwia użytkownikowi wybierz co najmniej jeden z tych elementów. List — typ formantu ma utracić ograniczeń na jakie rodzaje elementów podrzędnych może on zawierać. Dzięki temu dostawcy automatyzacji interfejsu użytkownika do obsługi dobrze znanego elementu kontenerów zaznaczenia.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Wymagania w poniższych sekcjach dotyczą wszystkich kontrolek, które określa, czy wdrożenia formantów typu Lista [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], lub [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]. Kontrole kontenerów listy są przykładem formantów, które implementują List — typ formantu.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Struktura drzewa automatyzacji interfejsu użytkownika wymagane  
 Poniższa tabela przedstawia dwa widoki [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, które odnoszą się do listy steruje i opisano, jakie mogą być zawarte w każdym widoku. Widok formant zawiera tylko elementy, które są formanty, a widok zawartości usuwa nadmiarowe informacje z drzewa. Na przykład kontrolki tekstu używany na etykiecie pola kombi mają być widoczne jako `ComboBox NameProperty`. Ponieważ kontrolkę tekstu już jest widoczna w ten sposób za pomocą formantu widoku nie jest konieczne jest widoczne dwa razy; w związku z tym zostanie ono usunięte z widoku zawartości. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, zobacz [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Kontrolki widoku|Widok zawartości|  
|------------------|------------------|  
|Zawiera elementy, które odpowiadają kontrolki.|Usuwa nadmiarowych z drzewa, tak by technologie pomocnicze pracować z najmniejszą zbiór przydatne informacje dla użytkownika końcowego.|  
|Lista<br /><br /> -DataItem (0 lub więcej)<br />— ListItem (0 lub więcej)<br />-Group (0 lub więcej)<br />-Pasek przewijania (0, 1 lub 2)|Lista<br /><br /> -DataItem (0 lub więcej)<br />— ListItem (0 lub więcej)<br />-Group (0 lub więcej)|  
  
 Widok kontroli dla formantu, który implementuje typu formantu listy (na przykład formant listy) obejmuje:  
  
-   Zero lub więcej elementów wewnątrz formantu listy (elementy mogą być oparte na typy formantów elementu listy lub element danych)  
  
-   Grupowanie formantów zero lub więcej w formancie listy  
  
-   Zero, co najmniej formanty paska przewijania dwóch  
  
-  
  
 Widok zawartości formantu, który implementuje typu formantu listy (na przykład formant listy) obejmuje:  
  
-   Zero lub więcej elementów wewnątrz formantu listy (elementy mogą być oparte na typy formantów elementu listy lub element danych)  
  
-   Zero lub więcej grup wewnątrz formantu listy  
  
 Formant listy nie może zawierać elementy, które mają hierarchiczną relację niż są grupowane. Jeśli elementy podrzędne [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, a następnie kontenera listy powinny być oparte na Tree — typ formantu.  
  
 Elementy dostępne do wyboru wewnątrz formantu listy będą dostępne z poziomu elementów podrzędnych w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa kontrolki listy. Wszystkie elementy wewnątrz formantu listy muszą należeć do tej samej grupy wyboru. Elementy dostępne do wyboru na liście powinny zostać ujawnione jako typy formantu ListItem (zamiast elementu danych).  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Właściwości automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, której wartość lub definicji jest szczególnie istotne kontrolki listy. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Właściwość|Wartość|Uwagi|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz uwagi.|Wartość tej właściwości musi być unikatowy w obrębie wszystkich kontrolek w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz uwagi.|Prostokąt peryferyjnych zawiera całą formantu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz uwagi.|Jeśli formant listy kliknięcia (punkt, który można kliknąć, aby spowodować, że na liście, aby przyjąć fokus), prowadzące musi być wystawiony za pomocą tej właściwości.<br /><br /> Jeśli wartość `IsOffScreen` właściwość ma wartość true, a następnie <xref:System.Windows.Automation.NoClickablePointException> zostanie wygenerowany.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Zobacz uwagi.|Formant może przyjmować fokus klawiatury, musi obsługiwać tej właściwości.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz uwagi.|Wartość właściwości nazwy formantu listy należy przekazać kategorii opcje, które użytkownik jest pytany, aby dokonać wyboru spośród. Ta właściwość zazwyczaj otrzymuje zarejestrowaną nazwę z etykiety tekst statyczny. Jeśli nie jest etykietą tekst statyczny Deweloper aplikacji musi ujawniać wartości dla właściwości Name.<br /><br /> Czas tylko ta właściwość nie jest wymagane dla kontrolek listy jest, jeśli formant jest używany w poddrzewie inny formant.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Zobacz uwagi.|Jeśli brak jest etykiety tekst statyczny tej właściwości musi ujawniać odwołanie do tego formantu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Lista|Ta wartość jest taka sama dla wszystkich platform interfejsu użytkownika.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"list"|Zlokalizowany ciąg odpowiadający List — typ formantu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Formant listy zawsze znajduje się w widoku zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Formant listy zawsze znajduje się w widoku kontrolki [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|True|Jeśli kontener może akceptować wejście klawiatury wartość tej właściwości powinien mieć wartość PRAWDA.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Zobacz uwagi.|Tekst pomocy dla kontrolek listy należy wyjaśnić, dlaczego użytkownik jest pytany o dokonanie wyboru z listy opcji. Na przykład "wyboru elementów z tej listy spowoduje ustawienie rozdzielczość ekranu dla monitora."|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns-and-properties"></a>Wymagane właściwości i wzorce formantów automatyzacji interfejsu użytkownika  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolować wzorce wymagane do obsługi przez kontrolki listy. Aby uzyskać więcej informacji na wzorce formantów, zobacz [Przegląd wzorców formantu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Właściwość wzorzec/wzorzec formantu|Obsługa i wartości|Uwagi|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Wymagane|Wszystkie formanty, które obsługują formantów typu Lista musi implementować `ISelectionProvider` gdy stan zaznaczenia jest zachowywane między elementy zawarte w formancie. Jeśli elementów w kontenerze nie są można wybierać, należy użyć formantów typu grupa.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Zależy od|Formanty listy nie zawsze wymagają wybrania elementu.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Zależy od|Formanty listy może być kontenery pojedynczego lub wielokrotnego wyboru.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Zależy od|Implementuje tego wzorca kontroli w przypadku elementów w kontenerze przewijanego.|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Zależy od|Wdrożenie tego wzorca podczas nawigacji siatki musi być dostępna na podstawie elementu.|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Zależy od|Wdrożenie tego wzorca formantu, jeśli formant może obsługiwać wiele widoków, elementów w kontenerze.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Nigdy nie|`ITableProvider` nigdy nie jest obsługiwana dla formantów typu Lista. Jeśli formant powinien obsługiwać tego wzorca formantu, kontrolki powinny być oparte na danych DataGrid — typ formantu.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Zdarzeń automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia wymagane obsługiwane przez wszystkie kontrolki listy. Aby uzyskać więcej informacji dotyczących zdarzeń, zobacz [Przegląd zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Zdarzenia|Obsługa i wartości|Uwagi|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Zależy od|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Zależy od|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty> Zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> Zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> Zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> Zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> Zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> Zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> Zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagane|Brak|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Automation.ControlType.List>  
 [Typy kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Przegląd automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-overview.md)
