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
ms.openlocfilehash: 015eb38038f85621d027ef82118bf4133a45917a
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "45999393"
---
# <a name="ui-automation-support-for-the-list-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu lista
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pomocy technicznej dla kontrolek typu listy. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ formantu to zestaw warunków, które kontrolki muszą spełnić, aby można było używać <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> właściwości. Warunki obejmują konkretne wskazówki dotyczące [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wartości właściwości i wzorce kontrolki.  
  
 Kontrolek typu lista umożliwia organizowanie prostego grupy lub grup elementów i umożliwia użytkownikowi wybranie co najmniej jeden z tych elementów. Kontrolek typu lista ma ograniczenie luźne jakie typy elementów podrzędnych może zawierać. Dzięki temu dostawcy automatyzacji interfejsu użytkownika do obsługi dobrze znanego elementu dla kontenerów zaznaczenia.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Wymagania w poniższych sekcjach mają zastosowanie do wszystkich formantów, które implementują kontrolek typu List, czy [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], lub [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]. Kontrole kontenerów listy służą jako przykład kontrolek, które implementują typ kontrolki listy.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Struktura drzewa automatyzacji interfejsu użytkownika wymagane  
 Poniższa tabela przedstawia dwa widoki [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontroluje drzewo, które odnoszą się do listy, a w tym artykule opisano, jakie mogą być zawarte w każdym widoku. Widok kontrolki zawiera tylko te elementy, które są kontrolek, a widok zawartości usuwa nadmiarowe informacje z drzewa. Na przykład, kontrolki tekstu używany do etykiety pola kombi zostaną ujawnione jako `ComboBox NameProperty`. Ponieważ kontrolki tekstu jest już widoczna w ten sposób za pośrednictwem widoku formantu, który nie jest konieczne jest widoczne dwa razy; w związku z tym spowoduje jego usunięcie z widok zawartości. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, zobacz [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Formant widoku|Widok zawartości|  
|------------------|------------------|  
|Zawiera elementy, które odnoszą się do kontrolek.|Usuwa nadmiarowe informacje z drzewa, technologiami pomocniczymi pracować z najmniejszego zbioru istotnych informacji do użytkownika końcowego.|  
|Lista<br /><br /> -DataItem (0 lub więcej)<br />— ListItem (0 lub więcej)<br />-Group (0 lub więcej)<br />-Paska przewijania (0, 1 lub 2)|Lista<br /><br /> -DataItem (0 lub więcej)<br />— ListItem (0 lub więcej)<br />-Group (0 lub więcej)|  
  
 Widok kontrolki dla formantu, który implementuje typ kontrolki listy (na przykład kontrolka w postaci listy) składa się z:  
  
-   Zero lub więcej elementów w ramach kontrolki listy (elementy mogą być oparte na typy kontrolek elementu listy lub element danych)  
  
-   Zero lub więcej kontrolek grupy w ramach kontrolki listy  
  
-   Zero, jeden znak lub formanty paska przewijania w dwóch  
  
-  
  
 Widok zawartości formantu, który implementuje typ kontrolki listy (na przykład kontrolka w postaci listy) składa się z:  
  
-   Zero lub więcej elementów w ramach kontrolki listy (elementy mogą być oparte na typy kontrolek elementu listy lub element danych)  
  
-   Zero lub więcej grup w ramach kontrolki listy  
  
 Kontrolka listy nie może mieć elementy, które mają hierarchicznych relacji innej niż są zgrupowane razem. Jeśli elementy podrzędne [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, a następnie wyświetlenie listy kontenerów powinna być oparta na Tree — typ kontrolki.  
  
 Elementy dostępne do wyboru w kontrolce listy będzie dostępny z poziomu obiektów podrzędnych w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa kontrolki listy. Wszystkie elementy w kontrolce listy musi należeć do tej samej grupie zaznaczenia. Elementy dostępne do wyboru na liście powinny zostać ujawnione jako typy kontroli wyszczególnij (zamiast elementu danych).  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Właściwości automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, których wartość lub definicji jest szczególnie istotne w kontrolkach listy. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Właściwość|Wartość|Uwagi|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz uwagi.|Wartość tej właściwości musi być unikatowa wśród wszystkich kontrolek w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz uwagi.|Najbardziej zewnętrznej prostokąt, który zawiera całą kontrolkę.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz uwagi.|Jeśli kontrolka listy ma kliknięcia (punkt, który można kliknąć, aby spowodować, że na liście, aby przyjąć fokus), ten punkt, muszą być widoczne za pośrednictwem tej właściwości.<br /><br /> Jeśli wartość `IsOffScreen` właściwość ma wartość true, a następnie <xref:System.Windows.Automation.NoClickablePointException> zostanie wygenerowany.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Zobacz uwagi.|Formant może otrzymywać fokus klawiatury, musi obsługiwać tę właściwość.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz uwagi.|Wartość formantu listy właściwości Name należy przekazać kategoria opcji, które użytkownik jest pytany, aby dokonać wyboru spośród. Ta właściwość zazwyczaj pobiera jego nazwę od etykiety tekst statyczny. Jeśli nie jest etykietą tekst statyczny Deweloper aplikacji musi ujawnić wartości dla właściwości nazwy.<br /><br /> Jedyną sytuacją, w których ta właściwość nie jest wymagana dla kontrolek listy jest, jeśli formant jest używany w poddrzewie innej kontrolki.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Zobacz uwagi.|Jeśli brak jest etykiety tekst statyczny tej właściwości należy ujawnić odwołanie do tego formantu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Lista|Ta wartość jest taka sama dla wszystkich platform tworzenia interfejsu użytkownika.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"list"|Zlokalizowany ciąg odpowiadający typowi kontrolki listy.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Kontrolka listy zawsze znajduje się w widoku zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Kontrolka listy zawsze znajduje się w widoku kontrolnym [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|True|Jeśli kontener może akceptować dane wejściowe z klawiatury wartość tej właściwości powinna być prawdziwe.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Zobacz uwagi.|Tekst pomocy dla kontrolek listy należy wyjaśnić, dlaczego użytkownik zażądano dokonania wyboru z listy opcji. Na przykład "Wybór elementu z tej listy ustawi rozdzielczość ekranu dla monitora."|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns-and-properties"></a>Wymagane właściwości i wzorce kontrolek automatyzacji interfejsu użytkownika  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolować wzorców, trzeba być obsługiwana przez kontrolki listy. Aby uzyskać więcej informacji na temat wzorców kontrolek, zobacz [Przegląd wzorców kontrolki automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Właściwości wzorzec/wzorzec kontrolki|Obsługa/wartość|Uwagi|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Wymagane|Wszystkie formanty, które obsługują kontrolek typu Lista musi implementować `ISelectionProvider` gdy stan zaznaczenia jest zachowywane między elementy zawarte w formancie. Jeśli nie można wybierać elementów w kontenerze, należy użyć kontrolek typu Group.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Zależy od|Kontrolki listy nie zawsze wymagają wybrania elementu.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Zależy od|Kontrolki listy może być kontenerów pojedynczego lub wielokrotnego wyboru.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Zależy od|Implementacja tego wzorca kontrolki, jeśli przewijany elementów w kontenerze.|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Zależy od|Implementacja tego wzorca, gdy nawigacyjne siatki muszą być dostępne na podstawie elementu.|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Zależy od|Implementacja tego wzorca kontrolki, jeśli formant może obsługiwać wiele widoków, elementów w kontenerze.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|nigdy nie|`ITableProvider` nigdy nie jest obsługiwana dla kontrolek typu List. Jeśli formant powinien obsługiwać tego wzorca formantu, formant powinna być oparta na typ formantu siatki danych.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Właściwości zdarzeń automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia wymagane są obsługiwane przez wszystkie kontrolki listy. Aby uzyskać więcej informacji na temat zdarzeń, zobacz [Przegląd zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Zdarzenia|Obsługa/wartość|Uwagi|  
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
