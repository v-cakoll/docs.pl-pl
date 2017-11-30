---
title: "Obsługa automatyzacji interfejsu użytkownika dla typu formantu DataItem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, Data Item control type
- Data Item control type
- control types, Data Item
ms.assetid: 181708fd-2595-4c43-9abd-75811627d64c
caps.latest.revision: "36"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 937a75a229685f76816a123ad863f5a22f6043a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ui-automation-support-for-the-dataitem-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu DataItem
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera informacje na temat [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] obsługi dla typu formantu DataItem. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] typu formantu to zestaw warunków, które muszą spełniać formantu, aby można było używać <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> właściwości. Takie szczegółowe wytyczne dla [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wartości właściwości i wzorce formantu.  
  
 Wpis na liście kontaktów jest przykładem kontrolki elementu danych. Kontrolki elementu danych zawiera informacje, które są przydatne do użytkownika końcowego. Jest bardziej skomplikowane niż element prosta lista, ponieważ zawiera on bardziej rozbudowane informacje.  
  
 Następujące sekcje definiują wymaganych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury, właściwości, wzorców formantu i zdarzenia dla typu formantu DataItem drzewa. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Wymagania dotyczą wszystkich danych kontrolki elementu czy [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], lub [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Struktura drzewa automatyzacji interfejsu użytkownika wymagane  
 Poniższa tabela przedstawia kontroli i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolki drzewa, które odnoszą się do elementu danych i opisano, jakie mogą być zawarte w każdym widoku. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, zobacz [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Drzewo — widoku kontrolki|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Drzewo — Widok zawartości|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|Element danych<br /><br /> -Zmienia się (0 lub więcej; może odbywać się w hierarchii)|Element danych<br /><br /> -Zmienia się (0 lub więcej; może odbywać się w hierarchii)|  
  
 Element danych elementu w siatce danych może obsługiwać różnych obiektów, w tym kolejną warstwę elementy danych lub siatki określonych elementów, takich jak tekst, obrazy, lub formanty edycji. Jeśli element element danych ma rolę określonego obiektu, element powinien być udostępniany jako określonego typu; na przykład ListItem typ formantu elementu wybieranych danych w siatce.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Właściwości automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono właściwości, której wartość lub definicji jest szczególnie istotne kontrolki elementu danych. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|Właściwość|Wartość|Uwagi|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz uwagi.|Wartość tej właściwości musi być unikatowy w obrębie wszystkich kontrolek w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz uwagi.|Prostokąt peryferyjnych zawiera całą formantu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz uwagi.|Obsługiwane w przypadku prostokąt ograniczający. Jeśli nie każdy punkt w obrębie prostokątem jest aktywne i wykonywać specjalne testowanie trafień, zastąpienia i podaj elementu do kliknięcia.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Element danych|Ta wartość jest taka sama dla wszystkich platform interfejsu użytkownika.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Wartość true|Formant elementu danych musi być zawsze zawartości.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Wartość true|Formant elementu danych musi być zawsze formantu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Zobacz uwagi.|Formant może przyjmować fokus klawiatury, musi obsługiwać tej właściwości.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>|Zobacz uwagi.|Jeśli formant zawiera stan, który jest on aktualizowany dynamicznie, a następnie ta właściwość musi być obsługiwany, dzięki czemu ułatwianiem może odbierać aktualizacje po zmianie stanu elementu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Zobacz uwagi.|Jest to wartość ciągu, która przekazuje użytkownikowi końcowemu obiekt, który reprezentuje element. Przykłady są "Pliku multimedialnego" lub "Skontaktuj się z".|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Dane elementów formantów bez etykiety tekst statyczny.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"element danych"|Zlokalizowany ciąg odpowiadający DataItem — typ formantu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz uwagi.|Formant elementu danych zawsze zawiera element tekst podstawowy, który dotyczy użytkownika skojarzyć identyfikatorowi najbardziej semantycznego dla elementu.|  
  
<a name="_Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Wzorce formantów automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kontrolować wzorce wymagane obsługiwane przez wszystkie kontrolki elementu danych. Aby uzyskać więcej informacji na temat wzorców formantu, zobacz [Przegląd wzorców formantu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|— Wzorzec formantu|Obsługa|Uwagi|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Zależy od|Jeśli element danych może być rozwinięte lub zwinięte by pokazać lub ukryć informacje, musi być obsługiwany wzorzec Rozwiń Zwiń.|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Zależy od|Elementy danych będzie obsługiwać wzorzec elementu siatki, gdy zbiór elementów danych jest dostępna w kontenerze, który można nawigować od elementu do elementu.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Zależy od|Wszystkie elementy danych obsługuje możliwość być wyświetlony w wyniku przewijania z wzorcem element przewijania, gdy ich kontenera danych ma więcej elementów niż można zmieścić na ekranie.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Tak|Wszystkie elementy danych musi obsługiwać wzorzec SelectionItem sygnalizującego, kiedy element jest zaznaczony.|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Zależy od|Jeśli element danych znajduje się w obrębie typu formantu siatki danych będzie on obsługiwać tego wzorca.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Zależy od|Jeśli element danych zawiera stan, który może być ponownym za pośrednictwem.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Zależy od|Jeśli tekst podstawowy element danych można edytować wzorca wartości muszą być obsługiwane.|  
  
<a name="Working_with_Data_Items_in_Large_Lists"></a>   
## <a name="working-with-data-items-in-large-lists"></a>Praca z elementami danych w dużych list  
 Dużych list są często dane wirtualizacji w ramach [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] struktur w wydajności. Ze względu na to, klient automatyzacji interfejsu użytkownika nie może używać [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] funkcji zapytania scrape zawartość pełne drzewo w taki sam sposób jak może w kontenerach innych elementów. Klient powinien przewinąć element w widoku (lub rozwiń sterowania, aby pokazać wszystkie opcje cenne) przed uzyskiwania dostępu do pełny zestaw danych z elementu danych.  
  
 Podczas wywoływania metody `SetFocus` na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementu w elemencie danych [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)] przypadku zwróci pomyślnie i spowodować fokus ustawioną edycji w poddrzewie elementu danych.  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Zdarzeń automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wymagane obsługiwane przez wszystkie kontrolki elementu danych zdarzenia. Aby uzyskać więcej informacji o zdarzeniach, zobacz [Przegląd zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Zdarzenia|Obsługa|Uwagi|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>Zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Zależy od|Brak|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>Zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>Zdarzenie zmiany właściwości.|Zależy od|Brak|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>Zdarzenie zmiany właściwości.|Zależy od|Brak|  
  
<a name="Data_Item_Control_Type_Example"></a>   
## <a name="dataitem-control-type-example"></a>Przykład typu formantu DataItem  
 Na poniższym obrazie przedstawiono typu formantu DataItem w kontrolce widok listy o obsługę zaawansowanych informacji dla kolumn.  
  
 ![Graficzne formantu widoku listy z dwoma elementami danych](../../../docs/framework/ui-automation/media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 Formant i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, które odnoszą się do formantu elementu danych jest wyświetlony poniżej. Wzorce formantu dla każdego elementu automatyzacji są wyświetlane w nawiasach. Grupa "Contoso" jest również częścią siatki formantu siatki danych hosta.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Drzewo — widoku kontrolki|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Drzewo — Widok zawartości|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|-Grupy "Contoso" (tabela, siatki)<br />— DataItem "kont Receivable.doc" (TableItem, GridItem, SelectionItem dla, wywołanie)<br />-Image "Kont Receivable.doc"<br />-Edytuj "Name" (TableItem, GridItem, wartość "Kont Receivable.doc")<br />-Edytuj "Data modyfikacji" (wartość TableItem, GridItem, "2006-8-25 15:29:00")<br />-Edytuj "Rozmiar" (wartość GridItem, TableItem, "11.0 KB)<br />— DataItem "kont Payable.doc" (TableItem, GridItem, SelectionItem dla, wywołanie)<br />-   ...|-Grupy "Contoso" (tabela, siatki)<br />— DataItem "kont Receivable.doc" (TableItem, GridItem, SelectionItem dla, wywołanie)<br />-Image "Kont Receivable.doc"<br />-Edytuj "Name" (TableItem, GridItem, wartość "Kont Receivable.doc")<br />-Edytuj "Data modyfikacji" (wartość TableItem, GridItem, "2006-8-25 15:29:00")<br />-Edytuj "Rozmiar" (wartość GridItem, TableItem, "11.0 KB)<br />— DataItem "kont Payable.doc" (TableItem, GridItem, SelectionItem dla, wywołanie)<br />-   …|  
  
 Jeśli siatka reprezentuje listę elementów możliwych do wyboru, można udostępnić odpowiednie elementy interfejsu użytkownika z typu formantu ListItem zamiast typu formantu DataItem. W poprzednim przykładzie można zwiększyć elementy DataItem ("Kont Receivable.doc" i "Kont Payable.doc") w grupie ("Contoso") w przypadku wystawianego je jako typy formantu ListItem tego typu już obsługuje wzorca formantu SelectionItem dla.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Automation.ControlType.DataItem>  
 [Przegląd typów formantu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Przegląd automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-overview.md)
