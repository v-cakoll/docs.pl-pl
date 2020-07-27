---
title: Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu edycja
description: Uzyskaj informacje na temat obsługi automatyzacji interfejsu użytkownika dla kontrolek typu Edycja. Poznaj wymaganą strukturę drzewa, właściwości, wzorce formantów i zdarzenia.
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Edit
- Edit control type
- UI Automation, Edit control type
ms.assetid: 6db9d231-c0a0-4e17-910e-ac80357f774f
ms.openlocfilehash: 6c404786d58cfcb4cc7dabd982eea33694b7cd0b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167941"
---
# <a name="ui-automation-support-for-the-edit-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu edycja

> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).

Ten temat zawiera informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsłudze typu kontrolki edycji. W programie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Typ kontrolki jest zestawem warunków, które formant musi spełniać, aby można było użyć <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> właściwości. Warunki obejmują określone wytyczne dotyczące [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wartości właściwości i wzorców formantów.

Edytowanie formantów umożliwia użytkownikowi wyświetlanie i edytowanie prostej linii tekstu bez obsługi formatowania sformatowanego.

W poniższych sekcjach opisano wymaganą [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strukturę drzewa, właściwości, wzorce formantów i zdarzenia dla typu kontrolki edycji. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Wymagania dotyczą wszystkich kontrolek edycji, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] systemu Win32 lub Windows Forms.

<a name="Required_UI_Automation_Tree_Structure"></a>

## <a name="required-ui-automation-tree-structure"></a>Wymagana struktura drzewa automatyzacji interfejsu użytkownika

W poniższej tabeli przedstawiono widok kontrolki i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, które odnoszą się do kontrolek edycji i opisano, co może być zawarte w poszczególnych widokach. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, zobacz [Omówienie drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md).

|Widok kontrolki|Widok zawartości|
|------------------|------------------|
|Edytuj|Edytuj|

Kontrolki implementujące typ kontrolki edycji zawsze będą mieć zero pasków przewijania w widoku kontrolki [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, ponieważ jest to formant jednowierszowy. Pojedynczy wiersz tekstu może być zawijany w niektórych scenariuszach układu. Typ kontrolki edycji jest najlepiej dostosowany do przechowywania małych ilości tekstu, który można edytować lub wybrać.

<a name="Required_UI_Automation_Properties"></a>

## <a name="required-ui-automation-properties"></a>Wymagane właściwości automatyzacji interfejsu użytkownika

Poniższa tabela zawiera listę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, których wartość lub definicja jest szczególnie istotna dla kontrolek edycji. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md).

|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Wartość|Wartość|Uwagi|
|------------------------------------------------------------------------------------|-----------|-----------|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz uwagi.|Wartość tej właściwości musi być unikatowa dla wszystkich kontrolek w aplikacji.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz uwagi.|Najbardziej zewnętrzny prostokąt, który zawiera cały formant.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz uwagi.|Kontrolka edycji musi mieć punkt kliknięcia, który daje fokus wprowadzania do edycji części kontrolki, gdy użytkownik kliknie tam mysz.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Zobacz uwagi.|Jeśli formant może odbierać fokus klawiatury, musi obsługiwać tę właściwość.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz uwagi.|Nazwa kontrolki edycji jest zazwyczaj generowana na podstawie statycznej etykiety tekstowej. Jeśli nie istnieje etykieta tekstu statycznego, wartość właściwości `Name` musi być przypisana przez dewelopera aplikacji. `Name`Właściwość nigdy nie powinna zawierać zawartości tekstowej kontrolki edycji.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Zobacz uwagi.|Jeśli istnieje etykieta tekstu statycznego skojarzona z kontrolką, ta właściwość musi uwidaczniać odwołanie do tej kontrolki. Jeśli formant tekstu jest podskładnikiem innej kontrolki, nie będzie miał `LabeledBy` ustawionej właściwości.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Edytuj|Ta wartość jest taka sama dla wszystkich [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] platform.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|edytowania|Zlokalizowany ciąg odpowiadający typowi kontrolki Edit.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Prawda|Kontrolka edycji jest zawsze uwzględniona w widoku zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Prawda|Kontrolka edycji jest zawsze uwzględniona w widoku kontrolki [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsPasswordProperty>|Zobacz uwagi.|Musi mieć ustawioną wartość true w kontrolkach edycji, które zawierają hasła. Jeśli kontrolka edycji zawiera zawartość hasła, ta właściwość może być używana przez czytnik ekranu, aby określić, czy naciśnięcia klawiszy mają być odczytywane podczas ich pisania.|

<a name="Required_UI_Automation_Control_Patterns"></a>

## <a name="required-ui-automation-control-patterns-and-properties"></a>Wymagane wzorce i właściwości formantów automatyzacji interfejsu użytkownika

W poniższej tabeli wymieniono wzorce kontrolki wymagane do obsługi przez wszystkie kontrolki edycji. Aby uzyskać więcej informacji na temat wzorców kontrolek, zobacz [Omówienie wzorców kontrolek automatyzacji interfejsu użytkownika](ui-automation-control-patterns-overview.md).

|Właściwość wzorca kontrolki/wzorca kontrolki|Obsługa/wartość|Uwagi|
|-----------------------------------------------|--------------------|-----------|
|<xref:System.Windows.Automation.Provider.ITextProvider>|Zależy od|Kontrolki edycji powinny obsługiwać wzorzec kontrolki tekstu, ponieważ szczegółowe informacje tekstowe powinny być zawsze dostępne dla klientów.|
|<xref:System.Windows.Automation.Provider.IValueProvider>|Zależy od|Wszystkie kontrolki edycji, które pobierają ciąg, muszą ujawniać wzorzec wartości.|
|<xref:System.Windows.Automation.Provider.IValueProvider.IsReadOnly%2A>|Zobacz uwagi.|Ta właściwość musi być ustawiona tak, aby wskazywała, czy formant może mieć ustawioną wartość programowo, czy jest edytowalny przez użytkownika.|
|<xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>|Zobacz uwagi.|Ta właściwość zwróci zawartość tekstową kontrolki edycji. Jeśli `IsPasswordProperty` jest ustawiona na `true` , ta właściwość musi podnieść żądanie, `InvalidOperationException` gdy jest to wymagane.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Zależy od|Wszystkie kontrolki edycji przyjmujące zakres liczbowy muszą ujawniać wzorzec kontroli wartości zakresu.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Minimum%2A>|Zobacz uwagi.|Ta właściwość musi być najmniejszą wartością, na którą można ustawić zawartość kontrolki edycji.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Maximum%2A>|Zobacz uwagi.|Ta właściwość musi być największą wartością, na którą można ustawić zawartość kontrolki edycji.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.SmallChange%2A>|Zobacz uwagi.|Ta właściwość musi wskazywać liczbę miejsc dziesiętnych, do których można ustawić wartość. Jeśli Edycja przyjmuje tylko liczby całkowite, `SmallChangeProperty` musi mieć wartość 1. Jeśli Edycja Pobiera zakres od 1,0 do 2,0, to `SmallChangeProperty` musi być 0,1. Jeśli kontrolka edycji Pobiera zakres od 1,00 do 2,00, to `SmallChangeProperty` musi być 0,001.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.LargeChange%2A>|`Null`|Ta właściwość nie musi być uwidoczniona w kontrolce edycji.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Value%2A>|Zobacz uwagi.|Ta właściwość będzie wskazywać zawartość liczbową kontrolki edycji. Jeśli bardziej precyzyjna wartość jest ustawiana przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klienta w zakresach określonych we `Minimum` `Maximum` właściwościach i, Właściwość Value będzie automatycznie zaokrąglana do najbliższej zaakceptowanej wartości.|

<a name="Required_UI_Automation_Events"></a>

## <a name="required-ui-automation-events"></a>Wymagane zdarzenia automatyzacji interfejsu użytkownika

Poniższa tabela zawiera listę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzeń wymaganych do obsługi przez wszystkie kontrolki edycji. Aby uzyskać więcej informacji na temat zdarzeń, zobacz [Omówienie zdarzeń automatyzacji interfejsu użytkownika](ui-automation-events-overview.md).

|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Wydarzen|Pomoc techniczna|Uwagi|
|---------------------------------------------------------------------------------|-------------|-----------|
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Wymagane|Brak|
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent>|Wymagane|Brak|
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent>|Wymagane|Brak|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>zdarzenie zmiany właściwości.|Wymagane|Brak|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>zdarzenie zmiany właściwości.|Wymagane|Brak|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>zdarzenie zmiany właściwości.|Wymagane|Brak|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>zdarzenie zmiany właściwości.|Wymagane|Brak|
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>zdarzenie zmiany właściwości.|Zależy od|Brak|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>zdarzenie zmiany właściwości.|Nigdy|Brak|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>zdarzenie zmiany właściwości.|Nigdy|Brak|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>zdarzenie zmiany właściwości.|Nigdy|Brak|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>zdarzenie zmiany właściwości.|Nigdy|Brak|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>zdarzenie zmiany właściwości.|Nigdy|Brak|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>zdarzenie zmiany właściwości.|Nigdy|Brak|
|<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty>zdarzenie zmiany właściwości.|Zależy od|Jeśli formant obsługuje wzorzec kontroli wartości zakresu, musi obsługiwać to zdarzenie.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagane|Brak|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagane|Brak|

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Automation.ControlType.Edit>
- [Typy formantów automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-types-overview.md)
- [Przegląd automatyzacji interfejsu użytkownika](ui-automation-overview.md)
