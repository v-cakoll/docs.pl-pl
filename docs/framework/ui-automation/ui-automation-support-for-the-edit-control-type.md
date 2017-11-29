---
title: "Obsługa automatyzacji interfejsu użytkownika dla formantów typu edycja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control types, Edit
- Edit control type
- UI Automation, Edit control type
ms.assetid: 6db9d231-c0a0-4e17-910e-ac80357f774f
caps.latest.revision: "29"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 1ed9d3ce2f3283d7422ec7c1039ede75b1ed072c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ui-automation-support-for-the-edit-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu edycja
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsługę formantów typu Edycja. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typu formantu to zestaw warunków, które muszą spełniać formantu, aby można było używać <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> właściwości. Takie szczegółowe wytyczne dla [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wartości właściwości i wzorce formantu.  
  
 Formanty edycji włączyć użytkownika wyświetlić i edytować proste wiersza tekstu bez formatowanie pomocy technicznej.  
  
 Następujące sekcje definiują wymaganych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury, właściwości, wzorce formantów i zdarzeń dla formantów typu Edycja drzewa. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Wymagania dotyczą wszystkie formanty, edycji czy [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], lub [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Struktura drzewa automatyzacji interfejsu użytkownika wymagane  
 Poniższa tabela przedstawia kontroli i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, który dotyczy formanty edycji i w tym artykule opisano, jakie mogą być zawarte w każdym widoku. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, zobacz [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Kontrolki widoku|Widok zawartości|  
|------------------|------------------|  
|Edytowanie|Edytowanie|  
  
 Formanty, które implementują formantów typu Edycja zawsze będą mieć zerowej paski przewijania w widoku kontrolki [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, ponieważ jest on formantu jeden wiersz. W niektórych scenariuszach układu może zawijać się pojedynczy wiersz tekstu. Formantów typu Edycja najlepiej nadaje się do przechowywania niewielkich ilości można edytować lub wybranie tekstu.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Właściwości automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, której wartość lub definicji jest szczególnie istotne edytować kontrolki. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Właściwość|Wartość|Uwagi|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz uwagi.|Wartość tej właściwości musi być unikatowy w obrębie wszystkich kontrolek w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz uwagi.|Prostokąt peryferyjnych zawiera całą formantu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz uwagi.|Formant edycji musi mieć kliknięcia, zapewniająca fokus wprowadzania do edycji części kontrolki, gdy użytkownik kliknie przycisk myszy.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Zobacz uwagi.|Formant może przyjmować fokus klawiatury, musi obsługiwać tej właściwości.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz uwagi.|Nazwa kontrolki edycji zwykle jest generowana z etykiety tekst statyczny. Jeśli nie jest etykietą tekst statyczny, wartość właściwości `Name` musi być przypisany przez dewelopera aplikacji. `Name` Właściwość nigdy nie powinna zawierać zawartość tekstową kontrolki edycji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Zobacz uwagi.|Jeśli jest skojarzony z formantem etykiety tekst statyczny, ta właściwość musi ujawniać odwołanie do tego formantu. Jeśli tekst formantu jest podskładnik innego formantu, nie będzie miał `LabeledBy` zestawu właściwości.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Edytowanie|Ta wartość jest taka sama dla wszystkich [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] struktury.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"edit"|Zlokalizowany ciąg odpowiadający formantów typu Edycja.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Wartość true|Formant edycji zawsze znajduje się w widoku zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Wartość true|Formant edycji zawsze znajduje się w widoku kontrolki [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsPasswordProperty>|Zobacz uwagi.|Musi mieć ustawioną wartość PRAWDA na edytowanie kontrolek, które zawierają hasła. Jeśli formant edycyjny zawiera zawartość hasła następnie tej właściwości można czytników ekranu do określenia, czy naciśnięcia klawiszy należy przeczytać jako użytkownik wpisuje je.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns-and-properties"></a>Wymagane właściwości i wzorce formantów automatyzacji interfejsu użytkownika  
 W poniższej tabeli przedstawiono wymagane wzorce formantu obsługiwane przez wszystkie formanty edycji. Aby uzyskać więcej informacji na temat wzorców formantu, zobacz [Przegląd wzorców formantu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Właściwość wzorzec wzorzec/formantu|Obsługa i wartości|Uwagi|  
|-----------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITextProvider>|Zależy od|Formantów edycyjnych powinien obsługiwać wzorzec tekstu formantu, ponieważ szczegółowe informacje tekstowe powinna być zawsze dostępny dla klientów.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Zależy od|Wszystkie formanty edycji, które przyjmują ciąg musi ujawniać wzorca wartości.|  
|<xref:System.Windows.Automation.Provider.IValueProvider.IsReadOnly%2A>|Zobacz uwagi.|Ta właściwość musi mieć ustawioną wskazuje, czy formant może mieć wartości ustawić programowo lub można edytować przez użytkownika.|  
|<xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>|Zobacz uwagi.|Ta właściwość zwraca zawartość tekstową kontrolki edycji. Jeśli `IsPasswordProperty` ustawiono `true`, ta właściwość musi wygenerować `InvalidOpertaionException` na żądanie.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Zależy od|Wszystkie formanty edycji, które przyjmują zakresu numerycznego musi ujawniać wzorca formantu wartości zakresu.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Minimum%2A>|Zobacz uwagi.|Ta właściwość musi mieć zawartość formantu edycyjnego może być ustawiony na najmniejszą wartość.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Maximum%2A>|Zobacz uwagi.|Ta właściwość musi być największą wartość, która zawartość formantu edycyjnego może mieć wartości.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.SmallChange%2A>|Zobacz uwagi.|Ta właściwość musi wskazywać liczbę miejsc dziesiętnych, które mogą mieć ustawioną wartość. Jeśli Edycja przyjmuje tylko liczby całkowite, `SmallChangeProperty` musi mieć wartość 1. Jeśli Edycja przyjmuje zakres od 1.0 do 2.0, a następnie `SmallChangeProperty` musi być 0,1. Jeśli zakres z 1,00, 2,00 przyjmuje kontrolki edycji, a następnie `SmallChangeProperty` musi być 0,001.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.LargeChange%2A>|`Null`|Ta właściwość nie musi zostać udostępnione w formancie edycyjnym.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Value%2A>|Zobacz uwagi.|Ta właściwość wskazuje liczbowych zawartość kontrolki edycji. Gdy ustawiono bardziej dokładne wartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klienta w ramach zakresu określonego `Minimum` i `Maximum` właściwości, wartość właściwości zostanie automatycznie zaokrąglony do najbliższej wartości zaakceptowane.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Zdarzeń automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia wymagane do obsługi przez wszystkie formanty edycji. Aby uzyskać więcej informacji o zdarzeniach, zobacz [Przegląd zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Zdarzenia|Obsługa|Uwagi|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>Zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>Zdarzenie zmiany właściwości.|Nigdy nie|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>Zdarzenie zmiany właściwości.|Nigdy nie|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>Zdarzenie zmiany właściwości.|Nigdy nie|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>Zdarzenie zmiany właściwości.|Nigdy nie|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>Zdarzenie zmiany właściwości.|Nigdy nie|Brak|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>Zdarzenie zmiany właściwości.|Nigdy nie|Brak|  
|<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty>Zdarzenie zmiany właściwości.|Zależy od|Jeśli formant obsługuje wzorca formantu wartości zakresu, musi obsługiwać tego zdarzenia.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagane|Brak|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Automation.ControlType.Edit>  
 [Przegląd typów formantu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Przegląd automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-overview.md)
