---
title: Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu edycja
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Edit
- Edit control type
- UI Automation, Edit control type
ms.assetid: 6db9d231-c0a0-4e17-910e-ac80357f774f
ms.openlocfilehash: cdbb400d438231689fe35c4bff2bd2946b6bed80
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789504"
---
# <a name="ui-automation-support-for-the-edit-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu edycja

> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).

Ten temat zawiera informacje na temat obsługi [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] typu kontrolki edycji. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]typ formantu to zestaw warunków, które formant musi spełniać, aby można było użyć właściwości <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>. Warunki obejmują określone wytyczne dotyczące struktury drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], wartości właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] i wzorców formantów.

Edytowanie formantów umożliwia użytkownikowi wyświetlanie i edytowanie prostej linii tekstu bez obsługi formatowania sformatowanego.

Poniższe sekcje definiują wymaganą strukturę drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], właściwości, wzorce formantów i zdarzenia dla typu kontrolki Edycja. Wymagania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mają zastosowanie do wszystkich kontrolek edycji, czy [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Win32 czy Windows Forms.

<a name="Required_UI_Automation_Tree_Structure"></a>

## <a name="required-ui-automation-tree-structure"></a>Wymagana struktura drzewa automatyzacji interfejsu użytkownika

W poniższej tabeli przedstawiono widok kontrolki i widok zawartości drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], które odnoszą się do kontrolek edycji i opisano, co może być zawarte w poszczególnych widokach. Aby uzyskać więcej informacji na temat drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Omówienie drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md).

|Widok kontrolki|Widok zawartości|
|------------------|------------------|
|Edytowanie|Edytowanie|

Kontrolki implementujące typ kontrolki edycji zawsze będą mieć zero pasków przewijania w widoku kontrolki drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], ponieważ jest to formant jednowierszowy. Pojedynczy wiersz tekstu może być zawijany w niektórych scenariuszach układu. Typ kontrolki edycji jest najlepiej dostosowany do przechowywania małych ilości tekstu, który można edytować lub wybrać.

<a name="Required_UI_Automation_Properties"></a>

## <a name="required-ui-automation-properties"></a>Wymagane właściwości automatyzacji interfejsu użytkownika

W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, których wartość lub definicja jest szczególnie istotna dla kontrolek edycji. Aby uzyskać więcej informacji na temat właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md).

|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Właściwość|Wartość|Uwagi|
|------------------------------------------------------------------------------------|-----------|-----------|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz uwagi.|Wartość tej właściwości musi być unikatowa dla wszystkich kontrolek w aplikacji.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz uwagi.|Najbardziej zewnętrzny prostokąt, który zawiera cały formant.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz uwagi.|Kontrolka edycji musi mieć punkt kliknięcia, który daje fokus wprowadzania do edycji części kontrolki, gdy użytkownik kliknie tam mysz.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Zobacz uwagi.|Jeśli formant może odbierać fokus klawiatury, musi obsługiwać tę właściwość.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz uwagi.|Nazwa kontrolki edycji jest zazwyczaj generowana na podstawie statycznej etykiety tekstowej. Jeśli nie istnieje etykieta tekstu statycznego, wartość właściwości `Name` musi być przypisana przez dewelopera aplikacji. Właściwość `Name` nigdy nie powinna zawierać zawartości tekstowej kontrolki edycji.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Zobacz uwagi.|Jeśli istnieje etykieta tekstu statycznego skojarzona z kontrolką, ta właściwość musi uwidaczniać odwołanie do tej kontrolki. Jeśli formant tekstu jest podskładnikiem innej kontrolki, nie będzie miał ustawionej właściwości `LabeledBy`.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Edytowanie|Ta wartość jest taka sama dla wszystkich platform [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|edytowania|Zlokalizowany ciąg odpowiadający typowi kontrolki Edit.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Prawda|Kontrolka edycji jest zawsze uwzględniona w widoku zawartości drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Prawda|Kontrolka edycji jest zawsze uwzględniona w widoku kontrolki drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsPasswordProperty>|Zobacz uwagi.|Musi mieć ustawioną wartość true w kontrolkach edycji, które zawierają hasła. Jeśli kontrolka edycji zawiera zawartość hasła, ta właściwość może być używana przez czytnik ekranu, aby określić, czy naciśnięcia klawiszy mają być odczytywane podczas ich pisania.|

<a name="Required_UI_Automation_Control_Patterns"></a>

## <a name="required-ui-automation-control-patterns-and-properties"></a>Wymagane wzorce i właściwości formantów automatyzacji interfejsu użytkownika

W poniższej tabeli wymieniono wzorce kontrolki wymagane do obsługi przez wszystkie kontrolki edycji. Aby uzyskać więcej informacji na temat wzorców kontrolek, zobacz [Omówienie wzorców kontrolek automatyzacji interfejsu użytkownika](ui-automation-control-patterns-overview.md).

|Właściwość wzorca kontrolki/wzorca kontrolki|Obsługa/wartość|Uwagi|
|-----------------------------------------------|--------------------|-----------|
|<xref:System.Windows.Automation.Provider.ITextProvider>|Zależy od|Kontrolki edycji powinny obsługiwać wzorzec kontrolki tekstu, ponieważ szczegółowe informacje tekstowe powinny być zawsze dostępne dla klientów.|
|<xref:System.Windows.Automation.Provider.IValueProvider>|Zależy od|Wszystkie kontrolki edycji, które pobierają ciąg, muszą ujawniać wzorzec wartości.|
|<xref:System.Windows.Automation.Provider.IValueProvider.IsReadOnly%2A>|Zobacz uwagi.|Ta właściwość musi być ustawiona tak, aby wskazywała, czy formant może mieć ustawioną wartość programowo, czy jest edytowalny przez użytkownika.|
|<xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>|Zobacz uwagi.|Ta właściwość zwróci zawartość tekstową kontrolki edycji. Jeśli `IsPasswordProperty` jest ustawiona na `true`, ta właściwość musi podnieść `InvalidOperationException` na żądanie.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Zależy od|Wszystkie kontrolki edycji przyjmujące zakres liczbowy muszą ujawniać wzorzec kontroli wartości zakresu.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Minimum%2A>|Zobacz uwagi.|Ta właściwość musi być najmniejszą wartością, na którą można ustawić zawartość kontrolki edycji.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Maximum%2A>|Zobacz uwagi.|Ta właściwość musi być największą wartością, na którą można ustawić zawartość kontrolki edycji.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.SmallChange%2A>|Zobacz uwagi.|Ta właściwość musi wskazywać liczbę miejsc dziesiętnych, do których można ustawić wartość. Jeśli Edycja przyjmuje tylko liczby całkowite, `SmallChangeProperty` musi mieć wartość 1. Jeśli Edycja Pobiera zakres od 1,0 do 2,0, `SmallChangeProperty` musi być 0,1. Jeśli kontrolka edycji Pobiera zakres od 1,00 do 2,00, `SmallChangeProperty` musi być 0,001.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.LargeChange%2A>|`Null`|Ta właściwość nie musi być uwidoczniona w kontrolce edycji.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Value%2A>|Zobacz uwagi.|Ta właściwość będzie wskazywać zawartość liczbową kontrolki edycji. Gdy bardziej precyzyjna wartość jest ustawiana przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klienta w zakresach określonych we właściwościach `Minimum` i `Maximum`, Właściwość Value będzie automatycznie zaokrąglana do najbliższej zaakceptowanej wartości.|

<a name="Required_UI_Automation_Events"></a>

## <a name="required-ui-automation-events"></a>Wymagane zdarzenia automatyzacji interfejsu użytkownika

Poniższa tabela zawiera listę zdarzeń [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wymaganych do obsługi przez wszystkie kontrolki edycji. Aby uzyskać więcej informacji na temat zdarzeń, zobacz [Omówienie zdarzeń automatyzacji interfejsu użytkownika](ui-automation-events-overview.md).

|Zdarzenie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Obsługa|Uwagi|
|---------------------------------------------------------------------------------|-------------|-----------|
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Wymagane|Brak|
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent>|Wymagane|Brak|
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent>|Wymagane|Brak|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> zdarzenie zmiany właściwości.|Wymagane|Brak|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> zdarzenie zmiany właściwości.|Wymagane|Brak|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> zdarzenie zmiany właściwości.|Wymagane|Brak|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> zdarzenie zmiany właściwości.|Wymagane|Brak|
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> zdarzenie zmiany właściwości.|Zależy od|Brak|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> zdarzenie zmiany właściwości.|nigdy nie|Brak|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> zdarzenie zmiany właściwości.|nigdy nie|Brak|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> zdarzenie zmiany właściwości.|nigdy nie|Brak|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> zdarzenie zmiany właściwości.|nigdy nie|Brak|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> zdarzenie zmiany właściwości.|nigdy nie|Brak|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> zdarzenie zmiany właściwości.|nigdy nie|Brak|
|<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty> zdarzenie zmiany właściwości.|Zależy od|Jeśli formant obsługuje wzorzec kontroli wartości zakresu, musi obsługiwać to zdarzenie.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagane|Brak|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagane|Brak|

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Automation.ControlType.Edit>
- [Typy kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-types-overview.md)
- [Przegląd automatyzacji interfejsu użytkownika](ui-automation-overview.md)
