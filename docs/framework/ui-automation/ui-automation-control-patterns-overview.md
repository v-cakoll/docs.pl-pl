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
ms.openlocfilehash: 73ac290c688436e7ce74e1baaf9f7dbbbecb66bf
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855608"
---
# <a name="ui-automation-control-patterns-overview"></a>Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym omówieniu przedstawiono [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kontrolować wzorców. Wzorce kontrolki umożliwiają klasyfikowanie i ujawniać funkcjonalność formantu niezależnie od typu formantu lub wygląd formantu.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zastosowań kontrolować wzorców do reprezentowania wspólnej kontroli zachowania. Na przykład użyć Invoke — wzorzec kontrolki dla formantów, które mogą być wywoływane (np. przyciski) i wzorca kontrolki przewijania dla formantów, które mają paski przewijania (takie jak pola listy, widoki list lub pól kombi). Ponieważ każdy — wzorzec kontrolki reprezentuje osobne funkcje, można je łączyć do opisania pełny zestaw funkcji oferowanych przez określonego formantu.  
  
> [!NOTE]
>  Agreguj kontrolek — utworzonych za pomocą formantów podrzędnych, które zapewniają [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] dla funkcji udostępnianych przez nadrzędne — powinny implementować wszystkie wzorce kontrolki, zwykle występujących w każdej kontrolki podrzędne. Z kolei tych tych samych wzorców kontrolek nie są wymagane do zaimplementowania przez formantów podrzędnych.  
  
<a name="uiautomation_control_pattern_includes"></a>   
## <a name="ui-automation-control-pattern-components"></a>Składniki wzorzec kontrolki automatyzacji interfejsu użytkownika  
 Wzorce kontrolki obsługuje metody, właściwości, zdarzeń i relacje niezbędnej do zdefiniowania dyskretnych część funkcji dostępnych w formancie.  
  
-   Relacja między elementu automatyzacji interfejsu użytkownika i jego nadrzędne, podrzędne i równorzędne opisujący strukturę elementu w obrębie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.  
  
-   Metody zezwolić klientom automatyzacji interfejsu użytkownika do manipulowania formantu.  
  
-   Właściwości i zdarzenia zapewniają informacje o funkcjach wzorca kontrolki, a także informacje na temat stanu kontrolki.  
  
 Wzorce kontrolki odnoszą się do [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] jako interfejsy odnoszą się do [!INCLUDE[TLA#tla_com](../../../includes/tlasharptla-com-md.md)] obiektów. W [!INCLUDE[TLA2#tla_com](../../../includes/tla2sharptla-com-md.md)], można tworzyć zapytania obiektu zadać, co interfejsy obsługuje, a następnie użyć tych interfejsów do dostępu do funkcjonalności. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], klienci automatyzacji interfejsu użytkownika można zadawać kontrolki, które określają wzorców problemu obsługuje, a następnie współdziałał z formantu za pomocą właściwości, metod, zdarzeń i struktury udostępnianych przez wzorców kontrolek obsługiwanych. Na przykład dla pola wielowierszowe Edytowanie dostawcy automatyzacji interfejsu użytkownika wdrożenia <xref:System.Windows.Automation.Provider.IScrollProvider>. Gdy klient wie, który <xref:System.Windows.Automation.AutomationElement> obsługuje <xref:System.Windows.Automation.ScrollPattern> — wzorzec kontrolki, jego można użyć właściwości, metod i zdarzeń udostępnianych przez tego wzorca kontrolki do manipulowania kontrolki lub dostęp do informacji na temat kontroli.  
  
<a name="uiautomation_control_pattern_client_provider"></a>   
## <a name="ui-automation-providers-and-clients"></a>Dostawcy automatyzacji interfejsu użytkownika i klientów  
 Dostawcy automatyzacji interfejsu użytkownika implementują wzorców kontrolek, aby udostępnić odpowiednie zachowanie konkretne funkcje obsługiwane przez kontrolkę.  
  
 Klienci automatyzacji interfejsu użytkownika, dostęp do metod i właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontroli wzorzec klasy i ich używać, aby uzyskać informacje na [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], lub do manipulowania [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. W ramach tych zajęć wzorca kontrolki znajdują się w <xref:System.Windows.Automation> przestrzeni nazw (na przykład <xref:System.Windows.Automation.InvokePattern> i <xref:System.Windows.Automation.SelectionPattern>).  
  
 Klienci używają <xref:System.Windows.Automation.AutomationElement> metody (takie jak <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> lub <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType>) lub [!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)] metod dostępu w celu uzyskania dostępu do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości przy użyciu wzorca. Każda klasa wzorzec kontroli ma składową pola (na przykład <xref:System.Windows.Automation.InvokePattern.Pattern?displayProperty=nameWithType>"lub <xref:System.Windows.Automation.SelectionPattern.Pattern?displayProperty=nameWithType>) który identyfikuje ten — wzorzec kontrolki i może być przekazywany jako parametr do <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> lub <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> do pobrania tego wzorca dla <xref:System.Windows.Automation.AutomationElement>.  
  
<a name="uiautomation_control_patterns_dynamic"></a>   
## <a name="dynamic-control-patterns"></a>Wzorce kontrolek dynamicznych  
 Niektóre formanty nie zawsze obsługują ten sam zestaw wzorców kontrolek. Wzorce kontrolki są traktowane jako obsługiwane, gdy są one dostępne dla klientów automatyzacji interfejsu użytkownika. Na przykład wielowierszowe edytowanie umożliwia pole pionowe przewijanie tylko wtedy, gdy zawiera on więcej wierszy niż można wyświetlić w jej obszarze widoczne. Przewijanie jest wyłączone, po usunięciu tekstu jest za mało, aby przewijanie nie jest już wymagane. W tym przykładzie klasy ScrollPattern — wzorzec kontrolki dynamicznie jest obsługiwana w zależności od bieżącego stanu kontrolki (ilość tekstu znajduje się w polu edycji).  
  
<a name="Control_Pattern_Classes_and_Interfaces"></a>   
## <a name="control-pattern-classes-and-interfaces"></a>Kontrolka wzorzec klasy i interfejsy  
 W poniższej tabeli opisano [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolować wzorców. W tabeli wymieniono także klasy używane przez klientów automatyzacji interfejsu użytkownika do wzorców kontroli dostępu, a także interfejsy używane przez dostawców automatyzacji interfejsu użytkownika do ich wykonania.  
  
|Klasa wzorzec kontrolki|Interfejs dostawcy|Opis|  
|---------------------------|------------------------|-----------------|  
|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.Provider.IDockProvider>|Używane dla formantów, które może być zadokowane w kontenerze dokowania. Na przykład pasków narzędzi i palet narzędzia.|  
|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Używane dla formantów, które można rozwijać i zwijać. Na przykład, elementy menu w aplikacji, takich jak **pliku** menu.|  
|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.Provider.IGridProvider>|Używane dla formantów, które obsługują siatki funkcje, takie jak zmiany rozmiaru i przenoszenie do określonej komórki. Na przykład wyświetlanie dużych ikon w Eksploratorze Windows lub proste tabele bez nagłówków w [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)].|  
|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Używane dla formantów, które mają komórek siatki. Pojedyncze komórki powinien obsługiwać GridItem — wzorzec. Na przykład każdej komórki w [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)] szczegółów widoku.|  
|<xref:System.Windows.Automation.InvokePattern>|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Używane dla formantów, które mogą być wywoływane, takiej jak przycisk.|  
|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Używane dla formantów, które można przełączać się między wiele reprezentacji ten sam zestaw informacji, danych lub elementy podrzędne. Na przykład widoku listy kontroli, gdy dane są dostępne w miniatury, kafelka, ikona, lista lub widoków szczegółów.|  
|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Używane dla formantów, które mają zakres wartości, które mogą być stosowane do formantu. Pokrętło lat może na przykład mają szeroką gamę 1900-2010, a inna kontrolka pokrętła prezentowanie miesięcy będzie zakresu od 1 do 12.|  
|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.Provider.IScrollProvider>|Używane dla formantów, które można przewijać. Na przykład kontrolki zawierający paski przewijania, które są aktywne po więcej informacji, niż można wyświetlić w obszar wyświetlany formantu.|  
|<xref:System.Windows.Automation.ScrollItemPattern>|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Używane dla formantów, które mają poszczególne elementy na liście, który przewija. Na przykład lista formant, który zawiera poszczególne elementy na liście przewijania, takie jak formant pola kombi.|  
|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Używane dla kontrolki kontenera wyboru. Na przykład pola listy i pola kombi.|  
|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Używane dla poszczególnych elementów w kontrolkach kontenerze zaznaczenia, takie jak pola listy i pola kombi.|  
|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.Provider.ITableProvider>|Używane dla formantów, które mają siatki oraz informacje nagłówka. Na przykład [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] arkuszy.|  
|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Używane na potrzeby elementów w tabeli.|  
|<xref:System.Windows.Automation.TextPattern>|<xref:System.Windows.Automation.Provider.ITextProvider>|Używane dla formantów edycji i dokumenty, które udostępniają informacje tekstowe.|  
|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.Provider.IToggleProvider>|Używane dla formantów, gdzie może być ich stan. Na przykład pola wyboru i elementy dostępne do kontroli menu.|  
|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.Provider.ITransformProvider>|Używane dla formantów, które mogą być ze zmienionym rozmiarem, przenieść i obracać. Typowe zastosowania wzorca kontrolki przekształcania znajdują się w projektantach, formularze, edytory graficzne i aplikacji rysowania.|  
|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.Provider.IValueProvider>|Umożliwia klientom do pobierania lub ustawiania wartości kontrolek, które nie obsługują zakresu wartości. Na przykład wybór daty i godziny.|  
|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.Provider.IWindowProvider>|Udostępnia informacje specyficzne dla systemu windows, podstawową koncepcją do [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] systemu operacyjnego. Przykłady formantów, system Windows są najwyższego poziomu aplikacji systemu windows ([!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)], [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)]i tak dalej), [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] okien podrzędnych i okien dialogowych.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Mapowanie wzorców kontrolek dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)  
 [Przegląd automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-overview.md)  
 [Właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)  
 [Właściwości zdarzeń automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md)
