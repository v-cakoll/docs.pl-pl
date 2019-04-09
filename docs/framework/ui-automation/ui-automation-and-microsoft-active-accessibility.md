---
title: Automatyzacja interfejsu użytkownika a Microsoft Active Accessibility
ms.date: 03/30/2017
helpviewer_keywords:
- Active Accessibility
- UI Automation, Active Accessibility compared to
- UI Automation, Microsoft Active Accessibility
- Active Accessibility, UI Automation compared to
ms.assetid: 87bee662-0a3e-4232-a421-20e7a5968321
ms.openlocfilehash: 29a6b897115c5f2f3ae8d7e4ec708be59dc0d85b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115339"
---
# <a name="ui-automation-and-microsoft-active-accessibility"></a>Automatyzacja interfejsu użytkownika a Microsoft Active Accessibility
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)] była wcześniej umożliwiająca ułatwianie dostępu do aplikacji. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] jest to nowy model ułatwień dostępu dla [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] i ma na celu spełniać potrzeby produktów technologii pomocniczej i automatyczne narzędzia do testowania. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] oferuje wiele udoskonaleń [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)].  
  
 W tym temacie zawarto główne funkcje [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] oraz wyjaśniono, jak te funkcje różni się od [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)].  
  
<a name="Programming_Languages_compare"></a>   
## <a name="programming-languages"></a>Języki programowania  
<[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] opiera się na [!INCLUDE[TLA#tla_com](../../../includes/tlasharptla-com-md.md)] dzięki obsłudze podwójne interfejsy i dlatego program w języku C/C++ [!INCLUDE[TLA#tla_vb6](../../../includes/tlasharptla-vb6-md.md)]i w językach skryptów. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] (w tym biblioteki dostawcy po stronie klienta dla standardowych kontrolek) są zapisywane w kodzie zarządzanym i aplikacje klienckie automatyzacji interfejsu użytkownika są najłatwiej zaprogramowane przy użyciu języka C# lub Visual Basic .NET. Dostawców automatyzacji interfejsu użytkownika, które są implementacji interfejsów, można pisać w kodzie zarządzanym lub w języku C/C++.  
  
<a name="Support_in_Windows_Presentation_Foundation_"></a>   
## <a name="support-in-windows-presentation-foundation"></a>Obsługa w oprogramowaniu Windows Presentation Foundation  
 Windows Presentation Foundation (WPF) to nowy model do tworzenia interfejsów użytkownika. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] elementy nie zawierają natywną obsługę [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]; jednak obsługują [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], która obejmuje obsługę mostkowania [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] klientów. Tylko klienci napisanych specjalnie dla [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mogą w pełni korzystać z funkcji ułatwień dostępu [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)], takie jak zaawansowana obsługa tekstu.  
  
<a name="Servers_and_Clients_compare"></a>   
## <a name="servers-and-clients"></a>Serwery i klienci  
 W [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], serwery i klienci komunikują się bezpośrednio, głównie za pośrednictwem implementacji serwera `IAccessible`.  
  
 W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], podstawowej usługi znajdujące się między serwerem (nazywane dostawcę) a klientem. Podstawowa usługa wykonywania wywołań do interfejsy implementowane przez dostawców i zapewnia dodatkowe usługi, takie jak generowanie identyfikatorów unikatowy środowiska uruchomieniowego dla elementów. Aplikacje klienckie korzystają z funkcji biblioteki do wywołania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] usługi.  
  
 Dostawcy automatyzacji interfejsu użytkownika może dostarczyć informacji do [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] klientów i [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] serwerów może dostarczyć informacji aplikacjom klienckim automatyzacji interfejsu użytkownika. Jednak ponieważ [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] nie ujawnia jak najwięcej informacji [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], dwa modele nie są w pełni zgodne.  
  
<a name="UI_Elements_compare"></a>   
## <a name="ui-elements"></a>Elementy interfejsu użytkownika  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] przedstawia informacje o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów albo jako `IAccessible` interfejsu lub jako identyfikator podrzędnego. Jest trudne do porównywania dwóch `IAccessible` wskaźników, aby określić, jeśli odnoszą się do tego samego elementu.  
  
 W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], każdy element jest reprezentowany jako <xref:System.Windows.Automation.AutomationElement> obiektu. Porównanie odbywa się za pomocą operatora równości lub <xref:System.Windows.Automation.AutomationElement.Equals%2A> metody, które porównanie identyfikatorów runtime unikatowych elementów.  
  
<a name="Tree_Views_and_Navigation_compare"></a>   
## <a name="tree-views-and-navigation"></a>Widoki drzewa i nawigacja  
 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] Elementów na ekranie może być traktowany jako struktury drzewa z pulpitem jako katalogu głównego, aplikacji systemu windows jako bezpośrednie elementy podrzędne i elementy w ramach aplikacji jako dalsze elementów podrzędnych.  
  
 W [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], wiele elementów automatyzacji, które są nieodpowiednie dla użytkowników końcowych są widoczne w drzewie. Aplikacje klienckie trzeba Przyjrzyj się wszystkie elementy, aby określić, które mają znaczenie.  
  
 Automatyzacja interfejsu użytkownika klienta aplikacje "widzą" [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] za pośrednictwem widoku filtrowanego znajdującego się. Widok zawiera tylko interesujące Cię elementy: te, które podają informacje dla użytkownika lub umożliwiają interakcję. Wstępnie zdefiniowanych widoków tylko elementy kontroli i tylko elementy zawartości są dostępne; Ponadto aplikacje mogą definiować niestandardowe widoki. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] upraszcza proces opisujące [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] dla użytkownika i ułatwienia dla użytkowników, interakcji z aplikacją.  
  
 Nawigacja między elementami, w [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], jest przestrzennego (na przykład przeniesienie do elementu, który znajduje się po lewej stronie, na ekranie), logiczne (na przykład przejście do następnego elementu menu lub następnego elementu w kolejności tabulacji w oknie dialogowym) lub hierarchiczny (dla przykład przenoszenia pierwszego elementu podrzędnego w kontenerze lub element podrzędny do elementu nadrzędnego). Nawigacja hierarchiczna jest skomplikowane faktem, że elementy podrzędne nie zawsze są obiekty, które implementują `IAccessible`.  
  
 W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], wszystkie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy są <xref:System.Windows.Automation.AutomationElement> obiekty, które obsługują te same funkcje podstawowe. (Z punktu widzenia dostawca są obiektami, które implementują interfejs odziedziczone <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>.) Nawigacja jest głównie hierarchicznych: z elementów nadrzędnych do elementów podrzędnych i jeden element równorzędny do następnego. (Nawigacja pomiędzy elementami równorzędnymi ma element logiczny, ponieważ może on być zgodny kolejność tabulacji). Możesz przejść z dowolnego punktu początkowego, przy użyciu dowolnego widoku filtrowanego znajdującego się w drzewie <xref:System.Windows.Automation.TreeWalker> klasy. Możesz także przejść do elementów podrzędnych danego lub elementy podrzędne przy użyciu <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> i <xref:System.Windows.Automation.AutomationElement.FindAll%2A>, na przykład jest bardzo proste pobrać wszystkie elementy w oknie dialogowym, które obsługują wzorzec określoną kontrolkę.  
  
 Nawigacja w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jest lepsze niż w [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]. Niektóre elementy, takie jak listy rozwijane i wyskakujących okienek pojawiają się dwukrotnie w [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] drzewa i nawigacji z nich mogą mieć nieoczekiwane wyniki. Nie jest możliwe faktycznie zaimplementowano poprawnie [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] kontrolki paska pomocniczego. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Włącza zmiana elementu nadrzędnego i zmiana położenia, dzięki czemu element można umieścić dowolne miejsce w drzewie, niezależnie od hierarchii nałożonych przez własności dla systemu windows.  
  
<a name="Roles_and_Control_Types"></a>   
## <a name="roles-and-control-types"></a>Role i typy formantów  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] używa `accRole` właściwości (`IAccessible::get_actRole`) można pobrać opis roli elementu w [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], takich jak ROLE_SYSTEM_SLIDER lub ROLE_SYSTEM_MENUITEM. Rola elementu jest głównym sugeruje jej dostępnych funkcji. Interakcja z kontrolką odbywa się przy użyciu metody stałych, takich jak `IAccessible::accSelect` i `IAccessible::accDoDefaultAction`. Interakcja między aplikacji klienckiej i [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] wynosi co można zrobić za pomocą `IAccessible`.  
  
 Z kolei [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stopniu oddziela typu formantu elementu (opisanego przez <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> właściwość) z jego funkcjonalność. Funkcja jest określana przez wzorców kontrolki, które są obsługiwane przez dostawcę za pośrednictwem jego implementacja obiektu wyspecjalizowane interfejsy. Wzorce kontrolki można połączyć do opisania pełny zestaw funkcji oferowanych przez dany [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementu. Niektórzy dostawcy są wymagane na potrzeby obsługi wzorca określonego formantu; na przykład dostawca pole wyboru musi obsługiwać wzorca kontrolki przełącznika. Innych dostawców są wymagane do obsługi co najmniej jeden zestaw wzorców kontrolek; na przykład przycisk musi obsługiwać przełącznika lub Invoke. Nadal innych Obsługa nie wzorców kontrolek w ogóle; na przykład okienka w którym nie można przenieść, zmienić rozmiar ani zadokowane nie ma żadnych wzorców kontrolek.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsługuje niestandardowe formanty, które są identyfikowane za pomocą <xref:System.Windows.Automation.ControlType.Custom> właściwości i można opisać za pomocą <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> właściwości.  
  
 W poniższej tabeli przedstawiono mapowania [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] ról [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolować typów.  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] rola|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Typ formantu|  
|----------------------------------------------------------------------|----------------------------------------------------------------------------------------|  
|ROLE_SYSTEM_PUSHBUTTON|Przycisk|  
|ROLE_SYSTEM_CLIENT|Kalendarz|  
|ROLE_SYSTEM_CHECKBUTTON|Pole wyboru|  
|ROLE_SYSTEM_COMBOBOX|Pole kombi|  
|ROLE_SYSTEM_CLIENT|Niestandardowe|  
|ROLE_SYSTEM_LIST|Siatka danych|  
|ROLE_SYSTEM_LISTITEM|Element danych|  
|ROLE_SYSTEM_DOCUMENT|dokument|  
|ROLE_SYSTEM_TEXT|Edytowanie|  
|ROLE_SYSTEM_GROUPING|Grupa|  
|ROLE_SYSTEM_LIST|nagłówek|  
|ROLE_SYSTEM_COLUMNHEADER|Element nagłówka|  
|ROLE_SYSTEM_LINK|Hyperlink|  
|ROLE_SYSTEM_GRAPHIC|Obraz|  
|ROLE_SYSTEM_LIST|Lista|  
|ROLE_SYSTEM_LISTITEM|Element listy|  
|ROLE_SYSTEM_MENUPOPUP|Menu|  
|ROLE_SYSTEM_MENUBAR|Pasek menu|  
|ROLE_SYSTEM_MENUITEM|Element menu|  
|ROLE_SYSTEM_PANE|Pane|  
|ROLE_SYSTEM_PROGRESSBAR|Pasek postępu|  
|ROLE_SYSTEM_RADIOBUTTON|Przycisk radiowy|  
|ROLE_SYSTEM_SCROLLBAR|Pasek przewijania|  
|ROLE_SYSTEM_SEPARATOR|Separator|  
|ROLE_SYSTEM_SLIDER|Suwak|  
|ROLE_SYSTEM_SPINBUTTON|pokrętło|  
|ROLE_SYSTEM_SPLITBUTTON|Przycisk podziału|  
|ROLE_SYSTEM_STATUSBAR|Pasek stanu|  
|ROLE_SYSTEM_PAGETABLIST|Tab|  
|ROLE_SYSTEM_PAGETAB|Element karty|  
|ROLE_SYSTEM_TABLE|tabela|  
|ROLE_SYSTEM_STATICTEXT|Tekst|  
|ROLE_SYSTEM_INDICATOR|Thumb|  
|ROLE_SYSTEM_TITLEBAR|Pasek tytułu|  
|ROLE_SYSTEM_TOOLBAR|Pasek narzędzi|  
|ROLE_SYSTEM_TOOLTIP|ToolTip|  
|ROLE_SYSTEM_OUTLINE|Drzewo|  
|ROLE_SYSTEM_OUTLINEITEM|Element drzewa|  
|ROLE_SYSTEM_WINDOW|Okno|  
  
 Aby uzyskać więcej informacji na temat typów innej kontrolki zobacz [typy kontrolek automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-types.md).  
  
<a name="States_and_Properties"></a>   
## <a name="states-and-properties"></a>Stany i właściwości  
 W [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], elementy obsługi wspólny zbiór właściwości, a niektóre właściwości (takie jak `accState`) musi opisywać bardzo różnych rzeczy, w zależności od roli elementu. Serwery muszą implementować wszystkie metody `IAccessible` zwracanych właściwością, nawet te, które nie mają znaczenia dla elementu.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] definiuje wiele innych właściwości, niektóre z nich odpowiadają stanom w [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]. Niektóre są wspólne dla wszystkich elementów, ale inne są specyficzne dla typów formantów i wzorce kontrolki. Właściwości są rozróżniane na podstawie niepowtarzalnych identyfikatorów, a większość właściwości mogą być pobierane przy użyciu jednej metody <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> lub <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>. Wiele właściwości są również łatwe pobieranie z <xref:System.Windows.Automation.AutomationElement.Current%2A> i <xref:System.Windows.Automation.AutomationElement.Cached%2A> metod dostępu do właściwości.  
  
 Dostawcy automatyzacji interfejsu użytkownika, nie trzeba zaimplementować właściwości nie ma znaczenia, ale można po prostu zwrócenia `null` wartość właściwości nie obsługuje. Ponadto [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podstawowej usługi można uzyskać niektóre właściwości z domyślnego dostawcę okna i są one połączone z właściwościami, które jawnie implementowana przez dostawcę.  
  
 A także obsługuje wiele innych właściwości, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zapewnia większą wydajność, umożliwiając wiele właściwości, które mają zostać pobrane za pomocą wywołania jednego między procesami.  
  
 W poniższej tabeli przedstawiono związek między właściwościami w dwóch modeli.  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] Metoda dostępu do właściwości|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Identyfikator właściwości|Uwagi|  
|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|-------------|  
|`get_accKeyboardShortcut`|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty> lub <xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|`AccessKeyProperty` ma pierwszeństwo, jeśli obie są podane.|  
|`get_accName`|<xref:System.Windows.Automation.AutomationElement.NameProperty>||  
|`get_accRole`|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|Zob. Poprzednia tabela mapowania ról, aby typy kontrolek.|  
|`get_accValue`|<xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>|Prawidłowy tylko dla typów formantów, które obsługują klasy ValuePattern lub klasy RangeValuePattern. RangeValue dla wartości są znormalizowane zgodnie z 0-100, aby były zgodne z zachowaniem MSAA. Wartość elementów, użyj ciągu.|  
|`get_accHelp`|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>||  
|`accLocation`|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>||  
|`get_accDescription`|Nie są obsługiwane w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|`accDescription` nie ma wyczyść specyfikacji w ramach MSAA, co spowodowało umieszczenie różnych rodzajów informacji w tej właściwości dostawcy.|  
|`get_accHelpTopic`|Nie są obsługiwane w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]||  
  
 W poniższej tabeli przedstawiono, które [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości odpowiadają [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] stanu stałe.  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] state|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] property|Zmiana stanu wyzwalaczy?|  
|-----------------------------------------------------------------------|------------------------------------------------------------------------------------|----------------------------|  
|STATE_SYSTEM_CHECKED|Dla pola wyboru <xref:System.Windows.Automation.TogglePattern.ToggleStateProperty><br /><br /> Dla przycisku radiowego <xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|T|  
|STATE_SYSTEM_COLLAPSED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Collapsed>|T|  
|STATE_SYSTEM_EXPANDED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Expanded> lub <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>|T|  
|STATE_SYSTEM_FOCUSABLE|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|N|  
|STATE_SYSTEM_FOCUSED|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|N|  
|STATE_SYSTEM_HASPOPUP|<xref:System.Windows.Automation.ExpandCollapsePattern> dla elementów menu|N|  
|STATE_SYSTEM_INVISIBLE|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> = True i <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A> powoduje, że <xref:System.Windows.Automation.NoClickablePointException>|N|  
|STATE_SYSTEM_LINKED|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> =<br /><br /> <xref:System.Windows.Automation.ControlType.Hyperlink>|N|  
|STATE_SYSTEM_MIXED|<xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> = <xref:System.Windows.Automation.ToggleState.Indeterminate>|N|  
|STATE_SYSTEM_MOVEABLE|<xref:System.Windows.Automation.TransformPattern.CanMoveProperty>|N|  
|STATE_SYSTEM_MUTLISELECTABLE|<xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>|N|  
|STATE_SYSTEM_OFFSCREEN|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> = PRAWDA|N|  
|STATE_SYSTEM_PROTECTED|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|N|  
|STATE_SYSTEM_READONLY|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty?displayProperty=nameWithType>|N|  
|STATE_SYSTEM_SELECTABLE|<xref:System.Windows.Automation.SelectionItemPattern> jest obsługiwany|N|  
|STATE_SYSTEM_SELECTED|<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|N|  
|STATE_SYSTEM_SIZEABLE|<xref:System.Windows.Automation.TransformPattern.TransformPatternInformation.CanResize%2A>|N|  
|STATE_SYSTEM_UNAVAILABLE|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|T|  
  
 Następujące stany, albo nie zostały wykonane przez większość [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] kontrolować serwerów lub nie mają odpowiednika w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] state|Uwagi|  
|-----------------------------------------------------------------------|-------------|  
|STATE_SYSTEM_BUSY|Nie jest dostępna w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_DEFAULT|Nie jest dostępna w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ANIMATED|Nie jest dostępna w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_EXTSELECTABLE|Nie są powszechnie implementowany przez [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] serwerów|  
|STATE_SYSTEM_MARQUEED|Nie są powszechnie implementowany przez [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] serwerów|  
|STATE_SYSTEM_SELFVOICING|Nie są powszechnie implementowany przez [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] serwerów|  
|STATE_SYSTEM_TRAVERSED|Nie jest dostępna w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ALERT_HIGH|Nie są powszechnie implementowany przez [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] serwerów|  
|STATE_SYSTEM_ALERT_MEDIUM|Nie są powszechnie implementowany przez [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] serwerów|  
|STATE_SYSTEM_ALERT_LOW|Nie są powszechnie implementowany przez [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] serwerów|  
|STATE_SYSTEM_FLOATING|Nie są powszechnie implementowany przez [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] serwerów|  
|STATE_SYSTEM_HOTTRACKED|Nie jest dostępna w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_PRESSED|Nie jest dostępna w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
  
 Aby uzyskać pełną listę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] identyfikatory właściwości, zobacz [Przegląd właściwości automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
<a name="uiautomation_events_compare"></a>   
## <a name="events"></a>Zdarzenia  
 Mechanizm zdarzeń [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], inaczej niż w przypadku, że w [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], nie zależą od Windows zdarzenia, routing (który jest ściśle powiązany za pomocą uchwytów okien) i nie wymaga aplikacja kliencka, aby skonfigurować punkty zaczepienia. Subskrypcje zdarzeń może być dostosowaniu nie tylko do określonych zdarzeń, ale do określonej części drzewa. Dostawców można regulować ich wywoływanie zdarzeń przez śledzenie jakie zdarzenia są trwa posłuchaliśmy dla.  
  
 Jest również ułatwić klientom pobieranie elementów, które zgłosić zdarzenia, ponieważ są one przekazywane bezpośrednio do wywołania zwrotnego zdarzeń. Właściwości elementu są automatycznie pobieranych z wyprzedzeniem, jeśli żądanie pamięci podręcznej był aktywny w przypadku, gdy klient subskrybuje zdarzenie.  
  
 W poniższej tabeli przedstawiono zgodność [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] WinEvents i [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia.  
  
|WinEvent|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Identyfikator zdarzenia|  
|--------------|--------------------------------------------------------------------------------------------|  
|EVENT_OBJECT_ACCELERATORCHANGE|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty> Zmiana właściwości|  
|EVENT_OBJECT_CONTENTSCROLLED|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> lub <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> zmiana właściwości pasków przewijania skojarzone|  
|EVENT_OBJECT_CREATE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_DEFACTIONCHANGE|Odpowiednika|  
|EVENT_OBJECT_DESCRIPTIONCHANGE|Nie jest dokładnym odpowiednikiem; być może <xref:System.Windows.Automation.AutomationElement.HelpTextProperty> lub <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> zmiana właściwości|  
|EVENT_OBJECT_DESTROY|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_FOCUS|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_OBJECT_HELPCHANGE|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty> zmiana|  
|EVENT_OBJECT_HIDE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_LOCATIONCHANGE|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> Zmiana właściwości|  
|EVENT_OBJECT_NAMECHANGE|<xref:System.Windows.Automation.AutomationElement.NameProperty> Zmiana właściwości|  
|EVENT_OBJECT_PARENTCHANGE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_REORDER|Nie zawsze są używane w [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]. Nie bezpośrednio odpowiednie zdarzenie jest zdefiniowany w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|EVENT_OBJECT_SELECTION|<xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>|  
|EVENT_OBJECT_SELECTIONADD|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent>|  
|EVENT_OBJECT_SELECTIONREMOVE|<xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent>|  
|EVENT_OBJECT_SELECTIONWITHIN|Odpowiednika|  
|EVENT_OBJECT_SHOW|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_STATECHANGE|Różne zdarzenia zmiany właściwości|  
|EVENT_OBJECT_VALUECHANGE|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType> i <xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType> zmienione|  
|EVENT_SYSTEM_ALERT|Odpowiednika|  
|EVENT_SYSTEM_CAPTUREEND|Odpowiednika|  
|EVENT_SYSTEM_CAPTURESTART|Odpowiednika|  
|EVENT_SYSTEM_CONTEXTHELPEND|Odpowiednika|  
|EVENT_SYSTEM_CONTEXTHELPSTART|Odpowiednika|  
|EVENT_SYSTEM_DIALOGEND|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|  
|EVENT_SYSTEM_DIALOGSTART|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|  
|EVENT_SYSTEM_DRAGDROPEND|Odpowiednika|  
|EVENT_SYSTEM_DRAGDROPSTART|Odpowiednika|  
|EVENT_SYSTEM_FOREGROUND|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_SYSTEM_MENUEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT_SYSTEM_MENUPOPUPEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT_SYSTEM_MENUPOPUPSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT_SYSTEM_MENUSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT_SYSTEM_MINIMIZEEND|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty> Zmiana właściwości|  
|EVENT_SYSTEM_MINIMIZESTART|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty> Zmiana właściwości|  
|EVENT_SYSTEM_MOVESIZEEND|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> Zmiana właściwości|  
|EVENT_SYSTEM_MOVESIZESTART|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> Zmiana właściwości|  
|EVENT_SYSTEM_SCROLLINGEND|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> lub <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> zmiana właściwości|  
|EVENT_SYSTEM_SCROLLINGSTART|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> lub <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> zmiana właściwości|  
|EVENT_SYSTEM_SOUND|Odpowiednika|  
|EVENT_SYSTEM_SWITCHEND|Odpowiednika, ale <xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent> zdarzenie sygnalizuje, że nowa aplikacja otrzymała fokus|  
|EVENT_SYSTEM_SWITCHSTART|Odpowiednika|  
|Odpowiednika|<xref:System.Windows.Automation.MultipleViewPattern.CurrentViewProperty> Zmiana właściwości|  
|Odpowiednika|<xref:System.Windows.Automation.ScrollPattern.HorizontallyScrollableProperty> Zmiana właściwości|  
|Odpowiednika|<xref:System.Windows.Automation.ScrollPattern.VerticallyScrollableProperty> Zmiana właściwości|  
|Odpowiednika|<xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> Zmiana właściwości|  
|Odpowiednika|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> Zmiana właściwości|  
|Odpowiednika|<xref:System.Windows.Automation.ScrollPattern.HorizontalViewSizeProperty> Zmiana właściwości|  
|Odpowiednika|<xref:System.Windows.Automation.ScrollPattern.VerticalViewSizeProperty> Zmiana właściwości|  
|Odpowiednika|<xref:System.Windows.Automation.TogglePattern.ToggleStateProperty> Zmiana właściwości|  
|Odpowiednika|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty> Zmiana właściwości|  
|Odpowiednika|<xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent> zdarzenie|  
|Odpowiednika|<xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent>|  
  
<a name="Security_compare"></a>   
## <a name="security"></a>Zabezpieczenia  
 Niektóre `IAccessible` dostosowywania scenariusze wymagają zawijania podstawowej `IAccessible` i wywoływać metodę za pośrednictwem do niego. To ma skutki dla bezpieczeństwa, ponieważ częściowo zaufanych składników nie powinny być pośrednik w ścieżce kodu.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Modelu eliminuje potrzebę dostawcy mogą wykonywać wywołania za pośrednictwem innego dostawcy kodu. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Usługa core wykonuje wszystkie niezbędne agregacji.  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe założenia automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/index.md)
