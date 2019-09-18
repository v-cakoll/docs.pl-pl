---
title: Obsługa automatyzacji interfejsu użytkownika dla typu formantu ListItem
ms.date: 03/30/2017
helpviewer_keywords:
- control types, List
- List Item control type
- UI Automation, List Item control type
ms.assetid: 34f533bf-fc14-4e78-8fee-fb7107345fab
ms.openlocfilehash: 18dcec2be6d9496c14dcc12c1d21b60967732db8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71041474"
---
# <a name="ui-automation-support-for-the-listitem-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla typu formantu ListItem
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 Ten temat zawiera informacje [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation.ControlType.ListItem> na temat obsługi typu formantu. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie typ kontrolki jest zestawem warunków, które formant musi spełniać, aby można było <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> użyć właściwości. Warunki obejmują określone wytyczne dotyczące [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wartości właściwości i wzorców formantów.  
  
 Kontrolki elementu listy są przykładem formantów, które implementują typ kontrolki ListItem.  
  
 W poniższych sekcjach opisano wymaganą [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strukturę drzewa, właściwości, wzorce formantów i zdarzenia dla typu formantu ListItem. Wymagania stosują się do wszystkich kontrolek listy [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]czy, [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]lub. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Wymagana struktura drzewa automatyzacji interfejsu użytkownika  
 W poniższej tabeli przedstawiono widok kontrolki i widok [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zawartości drzewa, które odnoszą się do kontrolek elementów listy, a także opisano, co może być zawarte w poszczególnych widokach. Aby uzyskać więcej informacji na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] temat drzewa, zobacz [drzewo automatyzacji interfejsu użytkownika — omówienie](ui-automation-tree-overview.md).  
  
|Widok kontrolki|Widok zawartości|  
|------------------|------------------|  
|ListItem<br /><br /> -Image (0 lub więcej)<br />-Tekst (0 lub więcej)<br />-Edytuj (0 lub więcej)|ListItem|  
  
 Elementy podrzędne formantu elementu listy w widoku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zawartości drzewa muszą mieć zawsze wartość "0". Jeśli struktura kontrolki jest taka, że inne elementy znajdują się poniżej elementu listy, należy postępować zgodnie z wymaganiami dotyczącymi [obsługi automatyzacji interfejsu użytkownika dla](ui-automation-support-for-the-treeitem-control-type.md) typu formantu TreeItem.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Wymagane właściwości automatyzacji interfejsu użytkownika  
 Poniższa tabela zawiera listę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, których wartość lub definicja jest szczególnie istotna dla formantów elementu listy. Aby uzyskać więcej informacji [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] na temat właściwości, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Wartość|Wartość|Uwagi|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz uwagi.|Wartość tej właściwości musi być unikatowa dla wszystkich kontrolek w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz uwagi.|Ta wartość tej właściwości powinna obejmować obszar obrazu i zawartości tekstowej elementu listy.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zależy od|Jeśli kontrolka listy ma punkt kliknięcia (punkt, który można kliknąć, aby spowodować, że lista zostanie skoncentrowana), ten punkt musi być uwidoczniony za pomocą tej właściwości. Jeśli formant listy jest całkowicie objęty elementami listy elementów podrzędnych, spowoduje to <xref:System.Windows.Automation.NoClickablePointException> wygenerowanie, aby wskazać, że klient musi zażądać elementu wewnątrz kontrolki listy dla punktu możliwego do kliknięcia.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz uwagi.|Wartość właściwości Nazwa kontrolki elementu listy pochodzi z zawartości tekstowej elementu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Zobacz uwagi.|Jeśli istnieje statyczna etykieta tekstowa, ta właściwość musi ujawniać odwołanie do tej kontrolki.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ListItem|Ta wartość jest taka sama dla wszystkich platform interfejsu użytkownika.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"element listy"|Zlokalizowany ciąg odpowiadający typowi kontrolce ListItem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Prawda|Kontrolka listy jest zawsze uwzględniona w widoku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zawartości drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Prawda|Kontrolka listy jest zawsze uwzględniona w widoku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolki drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Prawda|Jeśli kontener może przyjmować dane wejściowe z klawiatury, ta wartość właściwości powinna mieć wartość true.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|""|Tekst pomocy dla kontrolek listy powinien wyjaśnić, dlaczego użytkownik jest proszony o dokonanie wyboru z listy opcji, która jest zazwyczaj tym samym typem informacji prezentowanym za pośrednictwem etykietki narzędzia. Na przykład "Wybierz element, aby ustawić rozdzielczość ekranu dla monitora".|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Zależy od|Ta właściwość powinna być udostępniona dla kontrolek elementu listy, które reprezentują obiekt źródłowy. Te kontrolki elementów listy zazwyczaj mają ikonę skojarzoną z kontrolką, którą użytkownicy są skojarzeni z obiektem źródłowym.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Zależy od|Ta właściwość musi zwracać wartość, czy element listy jest obecnie przewijany do widoku w obrębie kontenera nadrzędnego, który implementuje wzorzec kontrolki przewijania.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Wymagane wzorce kontrolek automatyzacji interfejsu użytkownika  
 Poniższa tabela zawiera listę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wzorców formantów wymaganych do obsługi przez kontrolki elementu listy. Aby uzyskać więcej informacji na temat wzorców kontroli, zobacz [Wzorce formantów automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md).  
  
|Wzorzec kontrolki|Pomoc techniczna|Uwagi|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Tak|Formant elementu listy musi implementować ten wzorzec kontrolki. Pozwala to na przekazanie elementów listy, gdy są one zaznaczone.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Zależy od|Jeśli element listy znajduje się w kontenerze, który można przewijać, ten wzorzec kontrolki musi zostać zaimplementowany.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Zależy od|Jeśli element listy jest zaznaczony i akcja nie wykonuje zmiany stanu wyboru, ten wzorzec kontrolki musi zostać zaimplementowany.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Zależy od|Jeśli element można modyfikować w celu pokazywania lub ukrywania informacji, ten wzorzec kontrolki musi być zaimplementowany.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Zależy od|Jeśli element można edytować, ten wzorzec kontrolki musi być zaimplementowany. Zmiany w formancie elementu listy spowodują zmiany wartości elementów <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>i. <xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Zależy od|Jeśli funkcja nawigacji przestrzennej elementu do elementu jest obsługiwana w obrębie kontenera listy, a kontener jest układany w wiersze i kolumny, należy zaimplementować wzorzec kontrolki elementu siatki.|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Zależy od|Jeśli element zawiera polecenie, które można wykonać na nim, niezależnie od zaznaczenia, ten wzorzec musi być zaimplementowany. Jest to zazwyczaj akcja skojarzona z dwukrotnym kliknięciem kontrolki elementu listy. Przykładem może być uruchamianie dokumentu [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)]lub odtwarzanie pliku muzycznego w programie. [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)]|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Wymagane zdarzenia automatyzacji interfejsu użytkownika  
 Poniższa tabela zawiera listę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzeń wymaganych do obsługi przez wszystkie kontrolki elementu listy. Aby uzyskać więcej informacji na temat zdarzeń, zobacz [Omówienie zdarzeń automatyzacji interfejsu użytkownika](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Wydarzen|Pomoc techniczna|Uwagi|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Zależy od|Brak|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagane|Brak|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Automation.ControlType.ListItem>
- [Typy kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-types-overview.md)
- [Przegląd automatyzacji interfejsu użytkownika](ui-automation-overview.md)
