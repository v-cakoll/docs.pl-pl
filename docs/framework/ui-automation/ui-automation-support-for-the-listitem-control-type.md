---
title: "Obsługa automatyzacji interfejsu użytkownika dla typu formantu ListItem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control types, List
- List Item control type
- UI Automation, List Item control type
ms.assetid: 34f533bf-fc14-4e78-8fee-fb7107345fab
caps.latest.revision: "24"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: e97ea937fe62f05992eb23c928b36a7acb230f37
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ui-automation-support-for-the-listitem-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ListItem
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsługę <xref:System.Windows.Automation.ControlType.ListItem> kontroli typem. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typu formantu to zestaw warunków, które muszą spełniać formantu, aby można było używać <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> właściwości. Takie szczegółowe wytyczne dla [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wartości właściwości i wzorce formantu.  
  
 Kontrolki elementu listy są przykładem formantów, które implementują ListItem — typ formantu.  
  
 Następujące sekcje definiują wymaganych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury, właściwości, wzorców formantu i zdarzenia dla typu formantu ListItem drzewa. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Wymagania dotyczą wszystkich kontrolek listy, czy [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], lub [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Struktura drzewa automatyzacji interfejsu użytkownika wymagane  
 Poniższa tabela przedstawia kontroli i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolki drzewa, które odnoszą się do elementu listy, a w tym artykule opisano, jakie mogą być zawarte w każdym widoku. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, zobacz [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Kontrolki widoku|Widok zawartości|  
|------------------|------------------|  
|Element listy<br /><br /> -Obrazu (0 lub więcej)<br />-Tekst (0 lub więcej)<br />-Edytuj (0 lub więcej)|Element listy|  
  
 Elementy podrzędne kontrolki elementu listy, widok zawartości z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa zawsze musi mieć wartość "0". Jeśli struktura formantu jest taka, że inne elementy znajdują się poniżej elementu listy, a następnie należy wykonać, wymagania dotyczące [Obsługa automatyzacji interfejsu użytkownika dla typu formantu TreeItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md) kontroli typem.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Właściwości automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, której wartość lub definicji jest szczególnie istotne kontrolki elementu listy. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Właściwość|Wartość|Uwagi|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz uwagi.|Wartość tej właściwości musi być unikatowy w obrębie wszystkich kontrolek w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz uwagi.|Ta wartość tej właściwości powinna zawierać obszaru obrazu i tekstu treści elementu listy.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zależy od|Jeśli formant listy ma kliknięcia (punkt, który można kliknąć, aby spowodować, że na liście, aby przyjąć fokus) tego punktu, muszą być widoczne za pośrednictwem tej właściwości. Jeśli formant listy jest całkowicie objęte elementy podrzędne listy zgłosi <xref:System.Windows.Automation.NoClickablePointException> wskaż, klient musi poprosić element wewnątrz kontrolki listy dla elementu do kliknięcia.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz uwagi.|Wartość właściwości nazwy kontrolki elementu listy pochodzi z zawartość tekstu elementu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Zobacz uwagi.|Jeśli brak jest etykiety tekst statyczny tej właściwości musi ujawniać odwołanie do tego formantu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Element listy|Ta wartość jest taka sama dla wszystkich platform interfejsu użytkownika.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"element listy"|Zlokalizowany ciąg odpowiadający ListItem — typ formantu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Wartość true|Formant listy zawsze znajduje się w widoku zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Wartość true|Formant listy zawsze znajduje się w widoku kontrolki [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Wartość true|Jeśli kontener może akceptować wejście klawiatury wartość tej właściwości powinien mieć wartość PRAWDA.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|""|Tekst pomocy dla kontrolek listy należy wyjaśnić, dlaczego użytkownik jest pytany o dokonanie wyboru z listy opcji, która zwykle jest tego samego typu informacji przedstawionych w etykietce narzędzia. Na przykład "Wybierz element, aby ustawić rozdzielczość ekranu dla monitora."|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Zależy od|Ta właściwość powinna być udostępniane dla kontrolki elementu listy, które są reprezentujący obiekt. Te kontrolki elementu listy ma zazwyczaj ikony skojarzone z formantu, który użytkownicy mogą skojarzyć z obiektu źródłowego.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Zależy od|Ta właściwość musi zwracać wartość określa, czy element listy jest aktualnie wyświetlony w wyniku przewijania w ramach kontenera nadrzędnego, który implementuje Scroll — wzorzec formantu.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Wzorce formantów automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolować wzorce wymagane do obsługi przez kontrolki elementu listy. Aby uzyskać więcej informacji na wzorce formantów, zobacz [Przegląd wzorców formantu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|— Wzorzec formantu|Obsługa|Uwagi|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Tak|Kontrolki elementu listy musi implementować wzorzec tego formantu. Dzięki temu listy elementów kontroli w celu przedstawienia po jej wybraniu.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Zależy od|Jeśli element listy znajduje się w kontenerze, który jest przewijany tego wzorca formantu musi być implementowana.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Zależy od|Jeśli element listy jest dostępne do kontroli i akcji nie przeprowadza zmiana stanu zaznaczenia tego wzorca formantu musi być implementowana.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Zależy od|Jeśli element może operować, aby pokazać lub ukryć informacje tego wzorca formantu musi być implementowana.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Zależy od|Jeśli element można edytować tego wzorca formantu musi być implementowana. Zmiany kontrolki elementu listy mogą spowodować zmiany wartości <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>, i <xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>.|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Zależy od|Jeśli element do elementu przestrzennego nawigacji jest obsługiwana w kontenerze listy i kontenerze są rozmieszczone w wiersze i kolumny elementu siatki — wzorzec kontrolki musi być implementowana.|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Zależy od|Jeśli element ma polecenie, które można wykonywać na nim, niezależnie od wyboru, następnie tego wzorca musi być implementowana. Jest to zazwyczaj akcję skojarzoną z dwukrotnie kontrolki elementu listy. Przykłady czy uruchamiania dokumentu z [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)], lub odtwarzanie plików muzycznych [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)].|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Zdarzeń automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia wymagane obsługiwane przez wszystkie kontrolki elementu listy. Aby uzyskać więcej informacji dotyczących zdarzeń, zobacz [Przegląd zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Zdarzenia|Obsługa|Uwagi|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Zależy od|Brak|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>Zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>Zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>Zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>Zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagane|Brak|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Automation.ControlType.ListItem>  
 [Przegląd typów formantu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Przegląd automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-overview.md)
