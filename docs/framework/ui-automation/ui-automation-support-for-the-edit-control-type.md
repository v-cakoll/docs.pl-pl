---
title: Obsługa automatyzacji interfejsu użytkownika dla formantów typu edycja
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Edit
- Edit control type
- UI Automation, Edit control type
ms.assetid: 6db9d231-c0a0-4e17-910e-ac80357f774f
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 39804f7a525a45a4de37e7dded9ac4998280755f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44070631"
---
# <a name="ui-automation-support-for-the-edit-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu edycja
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsługi dla kontrolek typu Edycja. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ formantu to zestaw warunków, które kontrolki muszą spełnić, aby można było używać <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> właściwości. Warunki obejmują konkretne wskazówki dotyczące [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wartości właściwości i wzorce kontrolki.  
  
 Formantach edycji wzbogaconej umożliwić użytkownikowi wyświetlanie i edytowanie proste wiersz tekstu bez bogatego formatowania pomocy technicznej.  
  
 Poniższe sekcje definiują wymagane [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa struktury, właściwości, wzorców kontrolek i zdarzeń dla kontrolek typu Edycja. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Wymagania mają zastosowanie do wszystkich kontrolkach edycji wzbogaconej, czy [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], lub [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Struktura drzewa automatyzacji interfejsu użytkownika wymagane  
 Poniższa tabela przedstawia kontroli i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewo, które odnoszą się do edycji wzbogaconej, a w tym artykule opisano, jakie mogą być zawarte w każdym widoku. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, zobacz [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Formant widoku|Widok zawartości|  
|------------------|------------------|  
|Edytowanie|Edytowanie|  
  
 Formanty, które implementują kontrolek typu Edit będzie ono mieć zawsze zero pasków przewijania w widoku kontrolnym [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, ponieważ jest on kontroli jeden wiersz. Pojedynczy wiersz tekstu może opakować w niektórych scenariuszach układu. Kontrolek typu Edit najlepiej nadaje się do przechowywania niewielkich ilości tekstu atrybutu do edycji lub możliwy.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Właściwości automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, których wartość lub definicji jest szczególnie istotne edytować kontrolki. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Właściwość|Wartość|Uwagi|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz uwagi.|Wartość tej właściwości musi być unikatowa wśród wszystkich kontrolek w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz uwagi.|Najbardziej zewnętrznej prostokąt, który zawiera całą kontrolkę.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz uwagi.|Kontrolka edycji musi mieć kliknięcia, zapewniająca fokusu wprowadzania do Edytuj części kontrolki, gdy użytkownik kliknie myszą istnieje.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Zobacz uwagi.|Formant może otrzymywać fokus klawiatury, musi obsługiwać tę właściwość.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz uwagi.|Nazwa kontrolki edycji zwykle jest generowany z etykiety tekst statyczny. Jeśli nie jest statyczny tekst etykiety, wartość właściwości `Name` musi zostać przypisany przez dewelopera aplikacji. `Name` Właściwość nigdy nie powinna zawierać zawartość tekstową kontrolki edycji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Zobacz uwagi.|W przypadku etykietę statyczny tekst skojarzony z formantem, ta właściwość musi ujawniać odwołanie do tego formantu. Jeśli text control to podskładnika innej kontrolki, nie będziesz mieć `LabeledBy` zestawu właściwości.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Edytowanie|Ta wartość jest taka sama dla wszystkich [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] struktur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"edit"|Zlokalizowany ciąg odpowiadający typowi kontrolki edycji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Kontrolka edycji zawsze znajduje się w widoku zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Kontrolka edycji zawsze znajduje się w widoku kontrolnym [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsPasswordProperty>|Zobacz uwagi.|Musi być równa wartości true w formantach edycji wzbogaconej, zawierających hasła. Jeśli kontrolka edycji zawiera zawartość hasła następnie ta właściwość może służyć przez czytnik ekranu do określenia, czy naciśnięć klawiszy powinny być odczytywane jako użytkownik wpisze je.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns-and-properties"></a>Wymagane właściwości i wzorce kontrolek automatyzacji interfejsu użytkownika  
 W poniższej tabeli przedstawiono wzorców kontrolek wymagane są obsługiwane przez wszystkie edycji wzbogaconej. Aby uzyskać więcej informacji na temat wzorców kontrolek, zobacz [Przegląd wzorców kontrolki automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Właściwość wzorzec wzorzec/formantu|Obsługa/wartość|Uwagi|  
|-----------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITextProvider>|Zależy od|Formantach edycji wzbogaconej powinien obsługiwać wzorca kontrolki tekstu, ponieważ szczegółowe informacje tekstowe powinna zawsze być dostępna dla klientów.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Zależy od|Wszystkie kontrolki edycji, które przyjmują ciąg musi ujawniać wzorca wartości.|  
|<xref:System.Windows.Automation.Provider.IValueProvider.IsReadOnly%2A>|Zobacz uwagi.|Ta właściwość musi być równa wskazać, czy formant może mieć wartość programowo ustawić, czy można edytować przez użytkownika.|  
|<xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>|Zobacz uwagi.|Właściwość ta zwróci zawartość tekstową kontrolki edycji. Jeśli `IsPasswordProperty` ustawiono `true`, ta właściwość musi wygenerować `InvalidOpertaionException` żądanie.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Zależy od|Wszystkie kontrolki edycji, które przyjmują zakresu liczbowego musi ujawniać wzorca kontrolki wartości zakresu.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Minimum%2A>|Zobacz uwagi.|Ta właściwość musi być najmniejsza wartość, którą można ustawić zawartość kontrolki edycji.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Maximum%2A>|Zobacz uwagi.|Ta właściwość musi być największą wartość, która można ustawić zawartość kontrolki edycji.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.SmallChange%2A>|Zobacz uwagi.|Ta właściwość musi wskazać liczbę miejsc dziesiętnych, które może być równa wartości. Jeśli edytować tylko liczby całkowite, `SmallChangeProperty` musi mieć wartość 1. Jeśli edycja ma zakres od 1.0 do wersji 2.0, a następnie `SmallChangeProperty` musi być 0,1. Jeśli kontrolka edycji ma zakres od 1,00 do 2.00, a następnie `SmallChangeProperty` musi być 0,001.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.LargeChange%2A>|`Null`|Ta właściwość nie musi być odsłonięta na formant edycji.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Value%2A>|Zobacz uwagi.|Ta właściwość wskazuje liczbowych zawartość kontrolki edycji. Po ustawieniu wartości bardziej precyzyjne [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klienta zakresów określonych w `Minimum` i `Maximum` właściwości i wartości właściwości automatycznie zostanie zaokrąglona do najbliższej wartości akceptowane.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Właściwości zdarzeń automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia wymagane są obsługiwane przez wszystkie formanty edycji. Aby uzyskać więcej informacji o zdarzeniach zobacz [Przegląd zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Zdarzenia|Obsługa|Uwagi|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> Zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> Zdarzenie zmiany właściwości.|nigdy nie|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> Zdarzenie zmiany właściwości.|nigdy nie|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> Zdarzenie zmiany właściwości.|nigdy nie|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> Zdarzenie zmiany właściwości.|nigdy nie|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> Zdarzenie zmiany właściwości.|nigdy nie|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> Zdarzenie zmiany właściwości.|nigdy nie|Brak|  
|<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty> Zdarzenie zmiany właściwości.|Zależy od|Jeśli są obsługiwane przez kontrolkę wzorca kontrolki wartości zakresu, musi obsługiwać to zdarzenie.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagane|Brak|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Automation.ControlType.Edit>  
 [Typy kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Przegląd automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-overview.md)
