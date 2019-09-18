---
title: Automatyzacja interfejsu użytkownika a Microsoft Active Accessibility
ms.date: 03/30/2017
helpviewer_keywords:
- Active Accessibility
- UI Automation, Active Accessibility compared to
- UI Automation, Microsoft Active Accessibility
- Active Accessibility, UI Automation compared to
ms.assetid: 87bee662-0a3e-4232-a421-20e7a5968321
ms.openlocfilehash: 63b00f8eb35fa58ea0257d5e996fc2c51a248040
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042584"
---
# <a name="ui-automation-and-microsoft-active-accessibility"></a>Automatyzacja interfejsu użytkownika a Microsoft Active Accessibility
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 Usługa Microsoft Active Accessibility była wcześniejszym rozwiązaniem do udostępniania aplikacji. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]jest nowym modelem dostępności dla [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] programu i jest przeznaczony do zaspokajania potrzeb produktów technologii pomocniczych i zautomatyzowanych narzędzi do testowania. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]oferuje wiele ulepszeń w porównaniu z aktywną dostępnością.  
  
 W tym temacie przedstawiono główne funkcje programu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] i wyjaśniono, jak te funkcje różnią się od aktywnego ułatwienia dostępu.  
  
<a name="Programming_Languages_compare"></a>   
## <a name="programming-languages"></a>Języki programowania  
< Active Accessibility jest oparta na Component Object Model (com) z obsługą dwóch interfejsów i dlatego jest programowalna w języku C/C++, [!INCLUDE[TLA#tla_vb6](../../../includes/tlasharptla-vb6-md.md)]i w językach skryptów. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)](w tym Biblioteka dostawcy po stronie klienta dla kontrolek standardowych) jest zapisywana w kodzie zarządzanym, a aplikacje klienta automatyzacji interfejsu użytkownika są najłatwiej zaprogramowane przy użyciu C# lub Visual Basic .NET. Dostawcy automatyzacji interfejsu użytkownika, które są implementacjami interfejsów, można pisać w kodzie zarządzanym lub wC++języku C/.  
  
<a name="Support_in_Windows_Presentation_Foundation_"></a>   
## <a name="support-in-windows-presentation-foundation"></a>Obsługa w Windows Presentation Foundation  
 Windows Presentation Foundation (WPF) to nowy model tworzenia interfejsów użytkownika. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]elementy nie zawierają natywnej obsługi Active Accessibility; jednak obsługują one obsługę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], która obejmuje obsługę mostkowania dla aktywnych klientów dostępności. Tylko klienci zaawansowani [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dla programu mogą w pełni korzystać z [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]funkcji ułatwień dostępu, takich jak rozbudowana obsługa tekstu.  
  
<a name="Servers_and_Clients_compare"></a>   
## <a name="servers-and-clients"></a>Serwery i klienci  
 W obszarze Active Accessibility serwery i klienci komunikują się bezpośrednio, w dużym stopniu przez implementację `IAccessible`serwera.  
  
 W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie podstawowa usługa bazuje na serwerze (nazywanym dostawcą) i klientem. Usługa podstawowa wysyła wywołania do interfejsów implementowanych przez dostawców i udostępnia dodatkowe usługi, takie jak generowanie unikatowych identyfikatorów środowiska uruchomieniowego dla elementów. Aplikacje klienckie używają funkcji biblioteki do wywoływania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] usługi.  
  
 Dostawcy automatyzacji interfejsu użytkownika mogą dostarczać informacje do klientów usługi Active Accessibility, a serwery Active Accessibility mogą dostarczać informacje do aplikacji klienckich automatyzacji interfejsu użytkownika. Jednak ponieważ usługa Active Accessibility nie ujawnia tak dużej ilości informacji, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]jak te dwa modele nie są w pełni zgodne.  
  
<a name="UI_Elements_compare"></a>   
## <a name="ui-elements"></a>Elementy interfejsu użytkownika  
 Usługa Active Accessibility [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prezentuje elementy `IAccessible` jako interfejs lub jako identyfikator podrzędny. Aby określić, czy odwołują `IAccessible` się do tego samego elementu, trudno jest porównać dwa wskaźniki.  
  
 W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie każdy element jest reprezentowany <xref:System.Windows.Automation.AutomationElement> jako obiekt. Porównanie odbywa się przy użyciu operatora równości lub <xref:System.Windows.Automation.AutomationElement.Equals%2A> metody, z których oba porównują unikatowe identyfikatory środowiska uruchomieniowego elementów.  
  
<a name="Tree_Views_and_Navigation_compare"></a>   
## <a name="tree-views-and-navigation"></a>Widoki i nawigacja drzewa  
 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] Elementy na ekranie mogą być widoczne jako struktura drzewa z pulpitem jako element główny, okna aplikacji jako bezpośrednie elementy podrzędne i elementy w aplikacjach jako dalsze elementy podrzędne.  
  
 W przypadku aktywnego ułatwienia dostępu wiele elementów automatyzacji, które nie są przeznaczone dla użytkowników końcowych, jest uwidocznione w drzewie. Aplikacje klienckie muszą przyjrzeć się wszystkim elementom, aby określić, które mają znaczenie.  
  
 Aplikacje klienckie automatyzacji interfejsu użytkownika Zobacz [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] widok przefiltrowany. Widok zawiera tylko interesujące elementy: te, które dają informacje użytkownikowi lub umożliwiają interakcję. Dostępne są wstępnie zdefiniowane widoki tylko elementów formantów i tylko elementy zawartości. Ponadto aplikacje mogą definiować widoki niestandardowe. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]upraszcza zadanie opisywania [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] dla użytkownika i pomagając użytkownikowi korzystać z aplikacji.  
  
 Nawigowanie między elementami, w aktywnej dostępności, jest przestrzenne (na przykład przenoszone do elementu, który znajduje się w lewej części ekranu), logiczne (na przykład przechodzenie do następnego elementu menu lub następny element w kolejności tabulacji w oknie dialogowym) lub hierarchiczny ( na przykład przeniesienie pierwszego elementu podrzędnego w kontenerze lub z elementu podrzędnego do jego elementu nadrzędnego. Nawigacja hierarchiczna jest skomplikowana przez fakt, że elementy podrzędne nie zawsze są obiektami `IAccessible`, które implementują.  
  
 W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie wszystkie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy są <xref:System.Windows.Automation.AutomationElement> obiektami, które obsługują te same funkcje podstawowe. (Z punktu widzenia dostawcy są obiektami, które implementują interfejs Dziedziczony z <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>.) Nawigacja jest głównie hierarchiczna: od elementów nadrzędnych do elementów podrzędnych i od jednego elementu równorzędnego do następnego. (Nawigacja między elementami równorzędnymi ma element logiczny, ponieważ może być zgodna z kolejnością tabulacji). Korzystając <xref:System.Windows.Automation.TreeWalker> z klasy, można nawigować od dowolnego punktu początkowego przy użyciu dowolnego przefiltrowanego widoku drzewa. Można również przechodzić do określonych elementów podrzędnych lub obiektów podrzędnych przy <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> użyciu <xref:System.Windows.Automation.AutomationElement.FindAll%2A>i; na przykład bardzo łatwo można pobrać wszystkie elementy w oknie dialogowym, które obsługują określony wzorzec kontrolki.  
  
 Nawigacja w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programie jest bardziej spójna niż w przypadku aktywnego ułatwienia dostępu. Niektóre elementy, takie jak listy rozwijane i wyskakujące okienka, pojawiają się dwukrotnie w aktywnym drzewie dostępności i nawigacja z nich może mieć nieoczekiwane wyniki. W rzeczywistości nie można poprawnie zaimplementować aktywnej dostępności dla formantu paska pomocniczego. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]umożliwia zmienianie elementów nadrzędnych i zmiana położenia, dzięki czemu element można umieścić w dowolnym miejscu drzewa, pomimo że hierarchia nałożona przez własność systemu Windows.  
  
<a name="Roles_and_Control_Types"></a>   
## <a name="roles-and-control-types"></a>Role i typy kontrolek  
 Funkcja Active Accessibility używa `accRole` właściwości (`IAccessible::get_actRole`) do pobierania opisu roli [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]elementu w, takiej jak ROLE_SYSTEM_SLIDER lub ROLE_SYSTEM_MENUITEM. Rola elementu jest główną wskazówki dla dostępnych funkcji. Interakcja z kontrolką uzyskuje się za pomocą metod stałych `IAccessible::accSelect` , `IAccessible::accDoDefaultAction`takich jak i. Interakcja między aplikacją kliencką a programem [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] jest ograniczona do tego, co można zrobić `IAccessible`za pomocą programu.  
  
 W przeciwieństwie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , w dużym stopniu oddziela typ formantu elementu (opisany <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> przez właściwość) od jego oczekiwanej funkcjonalności. Funkcja jest określana przez Wzorce formantów, które są obsługiwane przez dostawcę przez jego implementację wyspecjalizowanych interfejsów. Wzorce formantów można łączyć w celu opisania pełnego zestawu funkcji obsługiwanych przez określony [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] element. Niektórzy dostawcy są zobowiązani do obsługi określonego wzorca kontroli; na przykład, dostawca pola wyboru musi obsługiwać wzorzec kontrolki przełącznika. Inni dostawcy są zobowiązani do obsługi co najmniej jednego zestawu wzorców kontrolek. na przykład przycisk musi obsługiwać przełącznik lub Invoke. Jeszcze inne nie obsługują wzorców kontroli. na przykład okienko, które nie może zostać przeniesione, zmieniono rozmiar lub zadokowane nie ma żadnych wzorców kontrolek.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]obsługuje niestandardowe kontrolki, które są identyfikowane <xref:System.Windows.Automation.ControlType.Custom> przez właściwość i mogą być opisane <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> przez właściwość.  
  
 W poniższej tabeli przedstawiono mapowanie aktywnych ról dostępności na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] typy kontroli.  
  
|Rola Active Accessibility|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Typ formantu|  
|----------------------------------------------------------------------|----------------------------------------------------------------------------------------|  
|ROLE_SYSTEM_PUSHBUTTON|Przycisk|  
|ROLE_SYSTEM_CLIENT|Kalendarz|  
|ROLE_SYSTEM_CHECKBUTTON|Pole wyboru|  
|ROLE_SYSTEM_COMBOBOX|Pole kombi|  
|ROLE_SYSTEM_CLIENT|Celnej|  
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
  
 Aby uzyskać więcej informacji na temat różnych typów formantów, zobacz [typy formantów automatyzacji interfejsu użytkownika](ui-automation-control-types.md).  
  
<a name="States_and_Properties"></a>   
## <a name="states-and-properties"></a>Stany i właściwości  
 W obszarze Active Accessibility elementy obsługują wspólny zestaw właściwości, a niektóre właściwości (takie jak `accState`) muszą opisywać różne elementy, w zależności od roli elementu. Serwery muszą implementować wszystkie metody `IAccessible` , które zwracają właściwość, nawet te, które nie są istotne dla elementu.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]definiuje wiele innych właściwości, z których niektóre odpowiadają stanom w aktywnym ułatwieniach dostępu. Niektóre są wspólne dla wszystkich elementów, ale inne są specyficzne dla typów kontroli i wzorców kontrolek. Właściwości są rozróżniane przez unikatowe identyfikatory i większość właściwości można pobrać przy użyciu pojedynczej metody <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> lub. <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> Wiele właściwości można również łatwo pobrać z <xref:System.Windows.Automation.AutomationElement.Current%2A> metod dostępu i <xref:System.Windows.Automation.AutomationElement.Cached%2A> właściwości.  
  
 Dostawca automatyzacji interfejsu użytkownika nie musi implementować nieistotnych właściwości, ale może po prostu zwrócić `null` wartość dla wszystkich właściwości, które nie są obsługiwane. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ponadto podstawowa usługa może uzyskać pewne właściwości od domyślnego dostawcy okien i są one połączyć z właściwościami jawnie implementowanymi przez dostawcę.  
  
 Jak również obsługa wielu innych właściwości, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zapewnia lepszą wydajność dzięki umożliwieniu pobierania wielu właściwości przy użyciu jednego połączenia obejmującego wiele procesów.  
  
 W poniższej tabeli przedstawiono zgodność między właściwościami w dwóch modelach.  
  
|Metoda dostępu do właściwości aktywnego ułatwienia dostępu|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Identyfikator właściwości|Uwagi|  
|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|-------------|  
|`get_accKeyboardShortcut`|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty> lub <xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|`AccessKeyProperty`ma pierwszeństwo, jeśli oba są obecne.|  
|`get_accName`|<xref:System.Windows.Automation.AutomationElement.NameProperty>||  
|`get_accRole`|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|Zapoznaj się z poprzednią tabelą, aby uzyskać mapowanie ról na typy kontrolek.|  
|`get_accValue`|<xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>|Prawidłowe tylko dla typów formantów, które obsługują ValuePattern lub RangeValuePattern. Wartości RangeValue dla są znormalizowane do 0-100, aby były spójne z zachowaniem technologii MSAA. Elementy wartości używają ciągu.|  
|`get_accHelp`|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>||  
|`accLocation`|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>||  
|`get_accDescription`|Nieobsługiwane w[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|`accDescription`nie miała jasnej specyfikacji w ramach technologii MSAA, co spowodowało, że dostawcy umieszczają różne fragmenty informacji w tej właściwości.|  
|`get_accHelpTopic`|Nieobsługiwane w[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]||  
  
 W poniższej tabeli przedstawiono właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , które odpowiadają stałym stanom dostępności.  
  
|Stan aktywnego ułatwienia dostępu|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]wartość|Czy wyzwalać zmianę stanu?|  
|-----------------------------------------------------------------------|------------------------------------------------------------------------------------|----------------------------|  
|STATE_SYSTEM_CHECKED|Dla pola wyboru,<xref:System.Windows.Automation.TogglePattern.ToggleStateProperty><br /><br /> Dla przycisku radiowego<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|T|  
|STATE_SYSTEM_COLLAPSED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Collapsed>|T|  
|STATE_SYSTEM_EXPANDED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Expanded>oraz<xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>|T|  
|STATE_SYSTEM_FOCUSABLE|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|N|  
|STATE_SYSTEM_FOCUSED|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|N|  
|STATE_SYSTEM_HASPOPUP|<xref:System.Windows.Automation.ExpandCollapsePattern>dla elementów menu|N|  
|STATE_SYSTEM_INVISIBLE|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>= Prawda i <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A> przyczyny<xref:System.Windows.Automation.NoClickablePointException>|N|  
|STATE_SYSTEM_LINKED|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> =<br /><br /> <xref:System.Windows.Automation.ControlType.Hyperlink>|N|  
|STATE_SYSTEM_MIXED|<xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> = <xref:System.Windows.Automation.ToggleState.Indeterminate>|N|  
|STATE_SYSTEM_MOVEABLE|<xref:System.Windows.Automation.TransformPattern.CanMoveProperty>|N|  
|STATE_SYSTEM_MUTLISELECTABLE|<xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>|N|  
|STATE_SYSTEM_OFFSCREEN|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>= Prawda|N|  
|STATE_SYSTEM_PROTECTED|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|N|  
|STATE_SYSTEM_READONLY|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty?displayProperty=nameWithType> i <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty?displayProperty=nameWithType>|N|  
|STATE_SYSTEM_SELECTABLE|<xref:System.Windows.Automation.SelectionItemPattern>jest obsługiwana|N|  
|STATE_SYSTEM_SELECTED|<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|N|  
|STATE_SYSTEM_SIZEABLE|<xref:System.Windows.Automation.TransformPattern.TransformPatternInformation.CanResize%2A>|N|  
|STATE_SYSTEM_UNAVAILABLE|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|T|  
  
 Następujące stany nie zostały zaimplementowane przez większość aktywnych serwerów kontroli dostępności lub nie mają odpowiednika w programie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
|Stan aktywnego ułatwienia dostępu|Uwagi|  
|-----------------------------------------------------------------------|-------------|  
|STATE_SYSTEM_BUSY|Niedostępne w[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_DEFAULT|Niedostępne w[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ANIMATED|Niedostępne w[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_EXTSELECTABLE|Nieszeroko zaimplementowane przez aktywne serwery ułatwień dostępu|  
|STATE_SYSTEM_MARQUEED|Nieszeroko zaimplementowane przez aktywne serwery ułatwień dostępu|  
|STATE_SYSTEM_SELFVOICING|Nieszeroko zaimplementowane przez aktywne serwery ułatwień dostępu|  
|STATE_SYSTEM_TRAVERSED|Niedostępne w[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ALERT_HIGH|Nieszeroko zaimplementowane przez aktywne serwery ułatwień dostępu|  
|STATE_SYSTEM_ALERT_MEDIUM|Nieszeroko zaimplementowane przez aktywne serwery ułatwień dostępu|  
|STATE_SYSTEM_ALERT_LOW|Nieszeroko zaimplementowane przez aktywne serwery ułatwień dostępu|  
|STATE_SYSTEM_FLOATING|Nieszeroko zaimplementowane przez aktywne serwery ułatwień dostępu|  
|STATE_SYSTEM_HOTTRACKED|Niedostępne w[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_PRESSED|Niedostępne w[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
  
 Aby uzyskać pełną listę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] identyfikatorów właściwości, zobacz [Omówienie właściwości automatyzacji interfejsu użytkownika](ui-automation-properties-overview.md).  
  
<a name="uiautomation_events_compare"></a>   
## <a name="events"></a>Zdarzenia  
 Mechanizm zdarzeń w programie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], w przeciwieństwie do usługi Active Accessibility, nie polega na routingu zdarzeń systemu Windows (który jest ściśle powiązany z uchwytami okna) i nie wymaga od aplikacji klienckiej konfigurowania punktów zaczepienia. Subskrypcje zdarzeń można dostrajać nie tylko do określonych zdarzeń, ale do określonych części drzewa. Dostawcy mogą również dostrajać swój wzrost zdarzeń przez śledzenie zdarzeń, dla których nasłuchuje.  
  
 Łatwiejsze jest również, aby klienci pobierali elementy, które zgłaszają zdarzenia, ponieważ są one przesyłane bezpośrednio do wywołania zwrotnego zdarzenia. Właściwości elementu są automatycznie pobierane w przypadku, gdy żądanie pamięci podręcznej było aktywne, gdy klient zasubskrybuje zdarzenie.  
  
 W poniższej tabeli przedstawiono zgodność aktywnych WinEvents i [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzeń związanych z dostępnością.  
  
|WinEvent|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Identyfikator zdarzenia|  
|--------------|--------------------------------------------------------------------------------------------|  
|EVENT_OBJECT_ACCELERATORCHANGE|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>Zmiana właściwości|  
|EVENT_OBJECT_CONTENTSCROLLED|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>lub <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> zmiana właściwości na skojarzonych paskach przewijania|  
|EVENT_OBJECT_CREATE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_DEFACTIONCHANGE|Brak równoważnej|  
|EVENT_OBJECT_DESCRIPTIONCHANGE|Brak dokładnego odpowiednika; być <xref:System.Windows.Automation.AutomationElement.HelpTextProperty> może <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> lub zmieniono Właściwość|  
|EVENT_OBJECT_DESTROY|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_FOCUS|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_OBJECT_HELPCHANGE|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>stąp|  
|EVENT_OBJECT_HIDE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_LOCATIONCHANGE|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>Zmiana właściwości|  
|EVENT_OBJECT_NAMECHANGE|<xref:System.Windows.Automation.AutomationElement.NameProperty>Zmiana właściwości|  
|EVENT_OBJECT_PARENTCHANGE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_REORDER|Niespójnie używane w usłudze Active Accessibility. W programie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]nie zdefiniowano bezpośrednio odpowiedniego zdarzenia.|  
|EVENT_OBJECT_SELECTION|<xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>|  
|EVENT_OBJECT_SELECTIONADD|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent>|  
|EVENT_OBJECT_SELECTIONREMOVE|<xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent>|  
|EVENT_OBJECT_SELECTIONWITHIN|Brak równoważnej|  
|EVENT_OBJECT_SHOW|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_STATECHANGE|Różne zdarzenia ze zmienionymi właściwościami|  
|EVENT_OBJECT_VALUECHANGE|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>i <xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType> zmienione|  
|EVENT_SYSTEM_ALERT|Brak równoważnej|  
|EVENT_SYSTEM_CAPTUREEND|Brak równoważnej|  
|EVENT_SYSTEM_CAPTURESTART|Brak równoważnej|  
|EVENT_SYSTEM_CONTEXTHELPEND|Brak równoważnej|  
|EVENT_SYSTEM_CONTEXTHELPSTART|Brak równoważnej|  
|EVENT_SYSTEM_DIALOGEND|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|  
|EVENT_SYSTEM_DIALOGSTART|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|  
|EVENT_SYSTEM_DRAGDROPEND|Brak równoważnej|  
|EVENT_SYSTEM_DRAGDROPSTART|Brak równoważnej|  
|EVENT_SYSTEM_FOREGROUND|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_SYSTEM_MENUEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT_SYSTEM_MENUPOPUPEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT_SYSTEM_MENUPOPUPSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT_SYSTEM_MENUSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT_SYSTEM_MINIMIZEEND|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>Zmiana właściwości|  
|EVENT_SYSTEM_MINIMIZESTART|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>Zmiana właściwości|  
|EVENT_SYSTEM_MOVESIZEEND|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>Zmiana właściwości|  
|EVENT_SYSTEM_MOVESIZESTART|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>Zmiana właściwości|  
|EVENT_SYSTEM_SCROLLINGEND|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>lub <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> zmiana właściwości|  
|EVENT_SYSTEM_SCROLLINGSTART|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>lub <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> zmiana właściwości|  
|EVENT_SYSTEM_SOUND|Brak równoważnej|  
|EVENT_SYSTEM_SWITCHEND|Brak równoważnej, ale <xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent> Zdarzenie sygnalizuje, że nowa aplikacja otrzymała fokus|  
|EVENT_SYSTEM_SWITCHSTART|Brak równoważnej|  
|Brak równoważnej|<xref:System.Windows.Automation.MultipleViewPattern.CurrentViewProperty>Zmiana właściwości|  
|Brak równoważnej|<xref:System.Windows.Automation.ScrollPattern.HorizontallyScrollableProperty>Zmiana właściwości|  
|Brak równoważnej|<xref:System.Windows.Automation.ScrollPattern.VerticallyScrollableProperty>Zmiana właściwości|  
|Brak równoważnej|<xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty>Zmiana właściwości|  
|Brak równoważnej|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>Zmiana właściwości|  
|Brak równoważnej|<xref:System.Windows.Automation.ScrollPattern.HorizontalViewSizeProperty>Zmiana właściwości|  
|Brak równoważnej|<xref:System.Windows.Automation.ScrollPattern.VerticalViewSizeProperty>Zmiana właściwości|  
|Brak równoważnej|<xref:System.Windows.Automation.TogglePattern.ToggleStateProperty>Zmiana właściwości|  
|Brak równoważnej|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>Zmiana właściwości|  
|Brak równoważnej|<xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent>wydarzen|  
|Brak równoważnej|<xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent>|  
  
<a name="Security_compare"></a>   
## <a name="security"></a>Zabezpieczenia  
 Niektóre `IAccessible` scenariusze dostosowania wymagają zawijania podstawowego `IAccessible` i wywoływania do niego. Ma to wpływ na bezpieczeństwo, ponieważ częściowo zaufany składnik nie powinien być pośrednikiem w ścieżce kodu.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Model eliminuje konieczność wywoływania przez dostawców do innego kodu dostawcy. Usługa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podstawowa wykonuje wszystkie wymagane agregacje.  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe założenia automatyzacji interfejsu użytkownika](index.md)
