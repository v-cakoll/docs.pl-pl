---
title: Wzorce formantów automatyzacji interfejsu użytkownika — omówienie
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns
- UI Automation, control patterns
ms.assetid: cc229b33-234b-469b-ad60-f0254f32d45d
ms.openlocfilehash: 6e2b5eaff3ee80434d5cdf39391273685da9faf0
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68434076"
---
# <a name="ui-automation-control-patterns-overview"></a>Wzorce formantów automatyzacji interfejsu użytkownika — omówienie
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 W tym omówieniu [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] przedstawiono wzorce kontroli. Wzorce kontrolek umożliwiają kategoryzowanie i Uwidacznianie funkcjonalności formantu niezależnie od typu formantu lub wyglądu kontrolki.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]używa wzorców formantów do reprezentowania typowych zachowań kontroli. Na przykład możesz użyć wzorca kontrolki Invoke dla formantów, które mogą być wywoływane (takie jak przyciski) i wzorca kontrolki przewijania dla formantów, które mają paski przewijania (takie jak pola listy, widoki listy lub pola kombi). Ze względu na to, że każdy wzorzec kontrolki reprezentuje osobną funkcję, można łączyć je w celu opisania pełnego zestawu funkcji obsługiwanych przez daną kontrolkę.  
  
> [!NOTE]
>  Formanty agregujące — skompilowane z kontrolkami podrzędnymi, które udostępniają [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] funkcje dla elementu nadrzędnego — powinny implementować wszystkie wzorce kontroli zwykle skojarzone z poszczególnymi kontrolkami podrzędnymi. Z kolei te same wzorce kontroli nie muszą być implementowane przez kontrolki podrzędne.  
  
<a name="uiautomation_control_pattern_includes"></a>   
## <a name="ui-automation-control-pattern-components"></a>Składniki wzorca kontrolki automatyzacji interfejsu użytkownika  
 Wzorce formantów obsługują metody, właściwości, zdarzenia i relacje, które są konieczne do zdefiniowania odrębnej funkcji dostępnej w formancie.  
  
- Relacja między elementem automatyzacji interfejsu użytkownika a jego elementem nadrzędnym, podrzędnym i równorzędnym opisuje strukturę elementu w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewie.  
  
- Metody umożliwiają klientom automatyzacji interfejsu użytkownika manipulowanie formantem.  
  
- Właściwości i zdarzenia zawierają informacje o funkcji wzorca kontroli, a także informacje o stanie formantu.  
  
 Wzorce kontrolne odnoszą się do [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] interfejsów, jak interfejsy odnoszą się do obiektów Component Object Model (com). W modelu COM można wysyłać zapytania do obiektu, aby zażądać obsługiwanych interfejsów, a następnie używać tych interfejsów do uzyskiwania dostępu do funkcji. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]systemie klienci automatyzacji interfejsu użytkownika mogą zadawać formant, który obsługuje, a następnie współdziałać z kontrolką przez właściwości, metody, zdarzenia i struktury uwidocznione przez obsługiwane wzorce kontroli. Na przykład dla wielowierszowego pola edycji są implementowane <xref:System.Windows.Automation.Provider.IScrollProvider>dostawcy automatyzacji interfejsu użytkownika. Gdy klient wie, że <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.ScrollPattern> obsługuje wzorzec kontrolki, może użyć właściwości, metod i zdarzeń uwidocznionych przez ten wzorzec kontrolki, aby manipulować formantem lub uzyskać dostęp do informacji o formancie.  
  
<a name="uiautomation_control_pattern_client_provider"></a>   
## <a name="ui-automation-providers-and-clients"></a>Dostawcy automatyzacji interfejsu użytkownika i klienci  
 Dostawcy automatyzacji interfejsu użytkownika implementują wzorce kontroli, aby uwidocznić odpowiednie zachowanie dla określonej funkcji obsługiwanej przez formant.  
  
 Klienci automatyzacji interfejsu użytkownika uzyskują dostęp do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metod i właściwości klas wzorców kontroli i używają ich do uzyskiwania [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]informacji na temat lub do [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]manipulowania. Te klasy wzorców formantów znajdują się w <xref:System.Windows.Automation> przestrzeni nazw (na <xref:System.Windows.Automation.InvokePattern> przykład i <xref:System.Windows.Automation.SelectionPattern>).  
  
 Klienci używają <xref:System.Windows.Automation.AutomationElement> metod (takich jak <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> lub <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType>) lub dostępu środowiska uruchomieniowego języka wspólnego [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] (CLR), aby uzyskać dostęp do właściwości wzorca. Każda Klasa wzorca kontroli ma element członkowski pola (na przykład <xref:System.Windows.Automation.InvokePattern.Pattern?displayProperty=nameWithType> lub <xref:System.Windows.Automation.SelectionPattern.Pattern?displayProperty=nameWithType>), który identyfikuje ten wzorzec kontrolki i może być przesłany jako parametr <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> do <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> lub do pobrania tego wzorca dla <xref:System.Windows.Automation.AutomationElement>.  
  
<a name="uiautomation_control_patterns_dynamic"></a>   
## <a name="dynamic-control-patterns"></a>Wzorce kontroli dynamicznej  
 Niektóre kontrolki nie zawsze obsługują ten sam zestaw wzorców kontrolek. Wzorce formantów są uważane za obsługiwane, gdy są dostępne dla klienta automatyzacji interfejsu użytkownika. Na przykład wielowierszowe pole edycji umożliwia przewijanie w pionie tylko wtedy, gdy zawiera więcej wierszy tekstu niż można je wyświetlić w obszarze widocznym. Przewijanie jest wyłączone po usunięciu wystarczającej ilości tekstu, aby przewijanie nie było już wymagane. Na potrzeby tego przykładu wzorzec kontrolki ScrollPattern jest dynamicznie obsługiwany w zależności od bieżącego stanu formantu (ilość tekstu w polu Edycja).  
  
<a name="Control_Pattern_Classes_and_Interfaces"></a>   
## <a name="control-pattern-classes-and-interfaces"></a>Klasy i interfejsy wzorca kontroli  
 W poniższej tabeli opisano [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wzorce kontrolek. W tabeli wymieniono również klasy używane przez klientów automatyzacji interfejsu użytkownika do uzyskiwania dostępu do wzorców formantów, a także interfejsy używane przez dostawców automatyzacji interfejsu użytkownika do ich implementacji.  
  
|Klasa wzorca kontrolki|Interfejs dostawcy|Opis|  
|---------------------------|------------------------|-----------------|  
|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.Provider.IDockProvider>|Używane dla kontrolek, które mogą być zadokowane w kontenerze dokowania. Na przykład paski narzędzi lub palety narzędzi.|  
|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Używany do kontrolek, które mogą być rozwinięte lub zwinięte. Na przykład elementy menu w aplikacji, takie jak menu **plik** .|  
|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.Provider.IGridProvider>|Używane dla formantów, które obsługują funkcje siatki, takie jak rozmiar i przechodzenie do określonej komórki. Na przykład widok dużych ikon w Eksploratorze Windows lub prostych tabelach bez nagłówków w programie [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)].|  
|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Używane dla formantów, które mają komórki w siatkach. Poszczególne komórki powinny obsługiwać wzorzec GridItem. Na przykład każda komórka w [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)] widoku szczegółowym.|  
|<xref:System.Windows.Automation.InvokePattern>|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Używany do kontrolek, które mogą być wywoływane, takich jak przycisk.|  
|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Używane dla kontrolek, które mogą przełączać się między wieloma reprezentacjami tego samego zestawu informacji, danych lub elementów podrzędnych. Na przykład kontrolka widok listy, w której dane są dostępne w widokach miniatury, kafelków, ikon, list lub szczegółów.|  
|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Używane dla kontrolek, które mają zakres wartości, które można zastosować do kontrolki. Na przykład, formant pokrętła zawierający lata może mieć zakres od 1900 do 2010, podczas gdy inny formant pokrętła przedstawiający miesiące będzie miał zakres od 1 do 12.|  
|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.Provider.IScrollProvider>|Używany do kontrolek, które można przewijać. Na przykład kontrolka, która ma paski przewijania, które są aktywne, gdy istnieje więcej informacji niż można wyświetlić w obszarze widocznym formantu.|  
|<xref:System.Windows.Automation.ScrollItemPattern>|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Używany do kontrolek, które mają pojedyncze elementy na liście, które są przewijane. Na przykład kontrolka listy, która ma poszczególne elementy na liście przewijania, taka jak kontrolka pola kombi.|  
|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Używany do zaznaczania elementów sterujących kontenera. Na przykład pola listy i pola kombi.|  
|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Używany do poszczególnych elementów w kontrolkach kontenera wyboru, takich jak pola listy i pola kombi.|  
|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.Provider.ITableProvider>|Używany do kontrolek, które mają siatkę, a także informacje nagłówka. Na przykład [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] arkusze.|  
|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Używane dla elementów w tabeli.|  
|<xref:System.Windows.Automation.TextPattern>|<xref:System.Windows.Automation.Provider.ITextProvider>|Służy do edycji formantów i dokumentów, które uwidaczniają informacje tekstowe.|  
|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.Provider.IToggleProvider>|Używane dla kontrolek, w których stan może być przełączany. Na przykład pola wyboru i elementy menu umożliwiające sprawdzanie.|  
|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.Provider.ITransformProvider>|Używany do kontrolek, które mogą być zmieniane, przenoszone i obracane. Typowe zastosowania wzorca kontrolki przekształcania znajdują się w projektantach, formularzach, edytorach graficznych i aplikacjach do rysowania.|  
|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.Provider.IValueProvider>|Umożliwia klientom pobieranie lub Ustawianie wartości w kontrolkach, które nie obsługują zakresu wartości. Na przykład wybór daty i godziny.|  
|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.Provider.IWindowProvider>|Udostępnia informacje specyficzne dla systemu Windows, podstawowe koncepcje [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] systemu operacyjnego. Przykłady formantów, które są Windows są oknami aplikacji najwyższego poziomu[!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)]( [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)],, i tak dalej) [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] , podrzędne okna i okna dialogowe.|  
  
## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Mapowanie wzorców kontrolek dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)
- [Przegląd automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-overview.md)
- [Właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)
- [Właściwości zdarzeń automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md)
