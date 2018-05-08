---
title: Wzorce formantów automatyzacji interfejsu użytkownika — omówienie
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns
- UI Automation, control patterns
ms.assetid: cc229b33-234b-469b-ad60-f0254f32d45d
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 1b02618676a1162681c67d34a2c6f43def07893c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ui-automation-control-patterns-overview"></a>Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym omówieniu przedstawiono [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kontrolować wzorce. Wzorce formantu umożliwiają klasyfikowanie i udostępniać funkcje formantu niezależnie od typu formantu lub wygląd formantu.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] używa kontroli wzorców do reprezentowania zachowań wspólnych formantu. Na przykład użyć Invoke — wzorzec formantu dla formantów, które mogą być wywoływane (takie jak przyciski) i wzorca formantu przewijania dla formantów, które mają paski przewijania (np. pola listy, widoki list lub pól kombi). Ponieważ każdy — wzorzec formantu reprezentuje osobne funkcje, można je łączyć do opisania pełnego zestawu funkcji oferowanych przez określonego formantu.  
  
> [!NOTE]
>  Formanty agregacji — skompilowanej za pomocą formantów podrzędnych, które zapewniają [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] dla funkcji udostępnianych przez nadrzędny — powinien implementować wszystkich wzorców formantu zwykle skojarzone z każdym kontrolki podrzędnej. Z kolei tych samym wzorców formantu nie są wymagane do zaimplementowania przez formantów podrzędnych.  
  
<a name="uiautomation_control_pattern_includes"></a>   
## <a name="ui-automation-control-pattern-components"></a>Składniki — wzorzec formantu automatyzacji interfejsu użytkownika  
 Wzorce formantu obsługuje metod, właściwości, zdarzeń i relacje wymagane do zdefiniowania odrębny element funkcje dostępne w formancie.  
  
-   Relacja między elementu automatyzacji interfejsu użytkownika i jego nadrzędne, podrzędne i równorzędne opisuje strukturę elementu w obrębie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.  
  
-   Metody Zezwalaj klienci automatyzacji interfejsu użytkownika do manipulowania formantu.  
  
-   Właściwości i zdarzenia Podaj informacje o funkcjach wzorca kontrolki, a także informacje o stanie formantu.  
  
 Wzorce formantu są powiązane z [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] jako interfejsy odnoszą się do [!INCLUDE[TLA#tla_com](../../../includes/tlasharptla-com-md.md)] obiektów. W [!INCLUDE[TLA2#tla_com](../../../includes/tla2sharptla-com-md.md)], można zbadać obiektu poproś co interfejsy obsługuje, a następnie użyć tych interfejsów do funkcji dostępu. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], klienci automatyzacji interfejsu użytkownika mogą poprosić formantu kontroli wzorce obsługuje, a następnie współdziałał z sterowanie za pośrednictwem właściwości, metody, zdarzeń i struktur udostępnianych przez wzorce obsługiwanych formantu. Na przykład w przypadku pola edycji wielowierszowy dostawców automatyzacji interfejsu użytkownika zaimplementować <xref:System.Windows.Automation.Provider.IScrollProvider>. Gdy klient wie, że <xref:System.Windows.Automation.AutomationElement> obsługuje <xref:System.Windows.Automation.ScrollPattern> — wzorzec formantu, można użyć właściwości, metod i zdarzeń udostępnianych przez tego wzorca kontrolki do manipulowania formant lub uzyskać dostępu do informacji na temat kontroli.  
  
<a name="uiautomation_control_pattern_client_provider"></a>   
## <a name="ui-automation-providers-and-clients"></a>Dostawcy automatyzacji interfejsu użytkownika i klientów  
 Dostawcy automatyzacji interfejsu użytkownika Implementowanie wzorców formantu do udostępnienia odpowiedniej zachowanie konkretne funkcje obsługiwane przez formant.  
  
 Klienci automatyzacji interfejsu użytkownika, dostęp do metody i właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontroli wzorzec klasy i ich używać, aby uzyskać informacje [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], lub do manipulowania [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Te klasy — wzorzec formantu znajdują się w <xref:System.Windows.Automation> przestrzeni nazw (na przykład <xref:System.Windows.Automation.InvokePattern> i <xref:System.Windows.Automation.SelectionPattern>).  
  
 Klienci używają <xref:System.Windows.Automation.AutomationElement> metod (takich jak <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> lub <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType>) lub [!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)] metod dostępu, aby uzyskać dostęp do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości wzorca. Każda klasa — wzorzec formantu ma członek pola (na przykład <xref:System.Windows.Automation.InvokePattern.Pattern?displayProperty=nameWithType>"lub <xref:System.Windows.Automation.SelectionPattern.Pattern?displayProperty=nameWithType>) identyfikuje tego wzorca formantu i mogą być przekazywane jako parametr <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> lub <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> do pobrania tego wzorca dla <xref:System.Windows.Automation.AutomationElement>.  
  
<a name="uiautomation_control_patterns_dynamic"></a>   
## <a name="dynamic-control-patterns"></a>Wzorce kontrolki dynamicznej  
 Niektóre formanty nie zawsze obsługują ten sam zestaw wzorców formantu. Wzorce formantu uwzględniane są obsługiwane, gdy są one dostępne dla klientów automatyzacji interfejsu użytkownika. Na przykład wielowierszowym formancie edytować pole umożliwia pionowe przewijanie tylko wtedy, gdy zawiera on więcej wierszy niż można wyświetlić w obszarze jej możliwych do wyświetlenia. Przewijanie jest wyłączone, po usunięciu tekstu jest za mało, aby przewijanie nie jest już wymagane. Na przykład klasy ScrollPattern — wzorzec formantu dynamicznie jest obsługiwana w zależności od bieżącego stanu kontroli (ilość tekstu znajduje się w polu edycji).  
  
<a name="Control_Pattern_Classes_and_Interfaces"></a>   
## <a name="control-pattern-classes-and-interfaces"></a>Formant wzorzec klasy i interfejsy  
 W poniższej tabeli opisano [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolować wzorce. Podano również używany przez klientów automatyzacji interfejsu użytkownika wzorce kontroli dostępu do klasy, jak również interfejsy używane przez dostawców automatyzacji interfejsu użytkownika do ich wdrażania.  
  
|Klasa — wzorzec formantu|Interfejs dostawcy|Opis|  
|---------------------------|------------------------|-----------------|  
|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.Provider.IDockProvider>|Używane dla formantów, które może być zadokowany w kontenerze dokowania. Na przykład paski narzędzi lub narzędzia palety.|  
|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Używane dla formantów, które mogą zostać rozwinięte lub zwinięte. Na przykład elementy menu w aplikacji, takich jak **pliku** menu.|  
|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.Provider.IGridProvider>|Używany dla formantów, które obsługują funkcje siatki, takie jak zmiany rozmiaru i przechodzenia do określonej komórki. Na przykład wyświetlić dużych ikon w Eksploratorze Windows lub prostego tabel bez nagłówków w [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)].|  
|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Używany dla formantów, które mają komórek w obrębie siatki. Pojedynczych komórek powinien obsługiwać GridItem — wzorzec. Na przykład każdej komórki w [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)] widoku szczegółów.|  
|<xref:System.Windows.Automation.InvokePattern>|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Używane dla formantów, które można wywołać, takie jak przycisk.|  
|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Używane dla formantów, które można przełączać się między wieloma reprezentacje ten sam zestaw informacji, danych lub elementów podrzędnych. Na przykład widok listy kontroli, których dane są dostępne w miniatur, kafelka, ikona, lista lub widoków szczegółów.|  
|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Używany dla formantów, które mają zakres wartości, które można zastosować do formantu. Na przykład pokrętło lat może być zakresu 1900-2010, podczas gdy inny formant pokrętła przedstawiający miesięcy byłyby zakresu od 1 do 12.|  
|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.Provider.IScrollProvider>|Używane dla formantów, które mogą być przewijane. Na przykład formantu mający paski przewijania, które są aktywne po więcej informacji, niż można wyświetlić w widocznym obszarze formantu.|  
|<xref:System.Windows.Automation.ScrollItemPattern>|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Używany dla formantów, które mają poszczególne elementy na liście przewijania. Na przykład formantu listy, który ma poszczególne elementy na liście przewijania, takich jak kontrolki pola kombi.|  
|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Używane dla formantów kontener zaznaczenia. Na przykład pola listy i pola kombi.|  
|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Używana dla poszczególnych elementów w formantach kontener zaznaczenia, takich jak pola listy i pola kombi.|  
|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.Provider.ITableProvider>|Używany do formantów, które mają siatka oraz informacje o nagłówku. Na przykład [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] arkuszy.|  
|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Używany do elementów w tabeli.|  
|<xref:System.Windows.Automation.TextPattern>|<xref:System.Windows.Automation.Provider.ITextProvider>|Używany w formantach edycji i dokumenty, które udostępniają informacje tekstowe.|  
|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.Provider.IToggleProvider>|Używane dla formantów, gdzie można przełączać stan. Na przykład pola wyboru i elementy dostępne do kontroli menu.|  
|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.Provider.ITransformProvider>|Używane dla formantów, które można zmieniać, przenieść i obracać. Typowe zastosowania wzorca kontrolki przekształcania znajdują się w projektantów, formularzy, edytory graficzne i rysowania aplikacji.|  
|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.Provider.IValueProvider>|Umożliwia klientom można pobrać lub ustawić wartości w formantach, które nie obsługują zakresu wartości. Na przykład wybór daty i godziny.|  
|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.Provider.IWindowProvider>|Przedstawia informacje specyficzne dla systemu windows, podstawowych koncepcji do [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] systemu operacyjnego. Przykłady formantów, które są systemu windows są najwyższego poziomu aplikacji systemu windows ([!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)], [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)]i tak dalej), [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] okno podrzędne i okien dialogowych.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Mapowanie wzorców kontrolek dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)  
 [Przegląd automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-overview.md)  
 [Właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)  
 [Właściwości zdarzeń automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md)
