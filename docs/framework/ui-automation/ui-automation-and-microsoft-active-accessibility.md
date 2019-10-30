---
title: Automatyzacja interfejsu użytkownika a Microsoft Active Accessibility
ms.date: 03/30/2017
helpviewer_keywords:
- Active Accessibility
- UI Automation, Active Accessibility compared to
- UI Automation, Microsoft Active Accessibility
- Active Accessibility, UI Automation compared to
ms.assetid: 87bee662-0a3e-4232-a421-20e7a5968321
ms.openlocfilehash: 99909f29e3228e7bc140ebdc888d4663bcbca0b5
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040532"
---
# <a name="ui-automation-and-microsoft-active-accessibility"></a>Automatyzacja interfejsu użytkownika a Microsoft Active Accessibility
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Usługa Microsoft Active Accessibility była wcześniejszym rozwiązaniem do udostępniania aplikacji. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] jest nowym modelem dostępności dla systemu Microsoft Windows i jest przeznaczony do zaspokajania potrzeb produktów technologii pomocniczych i zautomatyzowanych narzędzi do testowania. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] oferuje wiele ulepszeń w porównaniu z aktywną dostępnością.  
  
 W tym temacie przedstawiono główne funkcje [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] i wyjaśniono, jak te funkcje różnią się od aktywnego ułatwienia dostępu.  
  
<a name="Programming_Languages_compare"></a>   
## <a name="programming-languages"></a>Języki programowania  
< Active Accessibility jest oparta na Component Object Model (COM) z obsługą dwóch interfejsów i dlatego jest programowalna w języku C/C++, Microsoft Visual Basic 6,0 i językach skryptów. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] (w tym Biblioteka dostawcy po stronie klienta dla formantów standardowych) jest zapisywana w kodzie zarządzanym, a aplikacje klienta automatyzacji interfejsu użytkownika są najłatwiej zaprogramowane przy użyciu C# programu lub Visual Basic .NET. Dostawcy automatyzacji interfejsu użytkownika, które są implementacjami interfejsów, można pisać w kodzie zarządzanym lub wC++języku C/.  
  
<a name="Support_in_Windows_Presentation_Foundation_"></a>   
## <a name="support-in-windows-presentation-foundation"></a>Obsługa w Windows Presentation Foundation  
 Windows Presentation Foundation (WPF) to nowy model tworzenia interfejsów użytkownika. elementy [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] nie zawierają natywnej obsługi Active Accessibility; są jednak obsługiwane [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], które obejmują obsługę mostkowania dla aktywnych klientów. Tylko klienci zaawansowani do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mogą w pełni korzystać z funkcji ułatwień dostępu [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)], takich jak rozbudowana obsługa tekstu.  
  
<a name="Servers_and_Clients_compare"></a>   
## <a name="servers-and-clients"></a>Serwery i klienci  
 W obszarze Active Accessibility serwery i klienci komunikują się bezpośrednio, w dużym stopniu przez implementację `IAccessible`serwera.  
  
 W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]podstawowa usługa bazuje na serwerze (nazywanym dostawcą) i klientem. Usługa podstawowa wysyła wywołania do interfejsów implementowanych przez dostawców i udostępnia dodatkowe usługi, takie jak generowanie unikatowych identyfikatorów środowiska uruchomieniowego dla elementów. Aplikacje klienckie używają funkcji biblioteki do wywoływania usługi [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
 Dostawcy automatyzacji interfejsu użytkownika mogą dostarczać informacje do klientów usługi Active Accessibility, a serwery Active Accessibility mogą dostarczać informacje do aplikacji klienckich automatyzacji interfejsu użytkownika. Jednak ponieważ usługa Active Accessibility nie ujawnia tak dużej ilości informacji jak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], te dwa modele nie są w pełni zgodne.  
  
<a name="UI_Elements_compare"></a>   
## <a name="ui-elements"></a>Elementy interfejsu użytkownika  
 Usługa Active Accessibility prezentuje [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów jako interfejs `IAccessible` lub jako identyfikator podrzędny. Aby określić, czy odwołują się do tego samego elementu, trudno jest porównać dwa wskaźniki `IAccessible`.  
  
 W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]każdy element jest reprezentowany jako obiekt <xref:System.Windows.Automation.AutomationElement>. Porównanie odbywa się przy użyciu operatora równości lub metody <xref:System.Windows.Automation.AutomationElement.Equals%2A>, z których oba porównują unikatowe identyfikatory środowiska uruchomieniowego elementów.  
  
<a name="Tree_Views_and_Navigation_compare"></a>   
## <a name="tree-views-and-navigation"></a>Widoki i nawigacja drzewa  
 Elementy [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] na ekranie mogą być widoczne jako struktura drzewa z pulpitem jako element główny, okna aplikacji jako bezpośrednie elementy podrzędne oraz elementy w aplikacjach jako dalsze elementy podrzędne.  
  
 W przypadku aktywnego ułatwienia dostępu wiele elementów automatyzacji, które nie są przeznaczone dla użytkowników końcowych, jest uwidocznione w drzewie. Aplikacje klienckie muszą przyjrzeć się wszystkim elementom, aby określić, które mają znaczenie.  
  
 Aplikacje klienckie automatyzacji interfejsu użytkownika zobaczą [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] w widoku filtrowanym. Widok zawiera tylko interesujące elementy: te, które dają informacje użytkownikowi lub umożliwiają interakcję. Dostępne są wstępnie zdefiniowane widoki tylko elementów formantów i tylko elementy zawartości. Ponadto aplikacje mogą definiować widoki niestandardowe. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] upraszcza zadanie opisujące [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] użytkownikowi i pomagając użytkownikowi korzystać z aplikacji.  
  
 Nawigowanie między elementami, w aktywnej dostępności, jest przestrzenne (na przykład przenoszone do elementu, który znajduje się w lewej części ekranu), logiczne (na przykład przechodzenie do następnego elementu menu lub następny element w kolejności tabulacji w oknie dialogowym) lub hierarchiczny ( na przykład przeniesienie pierwszego elementu podrzędnego w kontenerze lub z elementu podrzędnego do jego elementu nadrzędnego. Nawigacja hierarchiczna jest skomplikowana przez fakt, że elementy podrzędne nie zawsze są obiektami implementującymi `IAccessible`.  
  
 W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]wszystkie elementy [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] są <xref:System.Windows.Automation.AutomationElement> obiektów, które obsługują te same funkcje podstawowe. (Z punktu widzenia dostawcy są obiektami, które implementują interfejs Dziedziczony z <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>). Nawigacja jest głównie hierarchiczna: od elementów nadrzędnych do elementów podrzędnych i od jednego elementu równorzędnego do następnego. (Nawigacja między elementami równorzędnymi ma element logiczny, ponieważ może być zgodna z kolejnością tabulacji). Korzystając z klasy <xref:System.Windows.Automation.TreeWalker>, można przechodzić z dowolnego punktu początkowego przy użyciu dowolnego przefiltrowanego widoku drzewa. Możesz również przejść do określonych elementów podrzędnych lub obiektów podrzędnych przy użyciu <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> i <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; na przykład bardzo łatwo można pobrać wszystkie elementy w oknie dialogowym, które obsługują określony wzorzec kontrolki.  
  
 Nawigacja w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jest bardziej spójna niż w przypadku aktywnych ułatwień dostępu. Niektóre elementy, takie jak listy rozwijane i wyskakujące okienka, pojawiają się dwukrotnie w aktywnym drzewie dostępności i nawigacja z nich może mieć nieoczekiwane wyniki. W rzeczywistości nie można poprawnie zaimplementować aktywnej dostępności dla formantu paska pomocniczego. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] umożliwia zmiany elementów nadrzędnych i rozmieszczenia, dzięki czemu element można umieścić w dowolnym miejscu drzewa, pomimo że hierarchia nałożona przez własność systemu Windows.  
  
<a name="Roles_and_Control_Types"></a>   
## <a name="roles-and-control-types"></a>Role i typy kontrolek  
 Funkcja Active Accessibility używa właściwości `accRole` (`IAccessible::get_actRole`) do pobierania opisu roli elementu w [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], takiej jak ROLE_SYSTEM_SLIDER lub ROLE_SYSTEM_MENUITEM. Rola elementu jest główną wskazówki dla dostępnych funkcji. Interakcja z kontrolką uzyskuje się za pomocą metod stałych, takich jak `IAccessible::accSelect` i `IAccessible::accDoDefaultAction`. Interakcja między aplikacją kliencką a [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] jest ograniczona do tego, co można zrobić za pomocą `IAccessible`.  
  
 W przeciwieństwie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] w dużym stopniu oddziela typ formantu elementu (opisany przez właściwość <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A>) od jego oczekiwanej funkcjonalności. Funkcja jest określana przez Wzorce formantów, które są obsługiwane przez dostawcę przez jego implementację wyspecjalizowanych interfejsów. Wzorce formantów można łączyć, aby opisać pełny zestaw funkcji obsługiwanych przez konkretny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementu. Niektórzy dostawcy są zobowiązani do obsługi określonego wzorca kontroli; na przykład, dostawca pola wyboru musi obsługiwać wzorzec kontrolki przełącznika. Inni dostawcy są zobowiązani do obsługi co najmniej jednego zestawu wzorców kontrolek. na przykład przycisk musi obsługiwać przełącznik lub Invoke. Jeszcze inne nie obsługują wzorców kontroli. na przykład okienko, które nie może zostać przeniesione, zmieniono rozmiar lub zadokowane nie ma żadnych wzorców kontrolek.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsługuje niestandardowe kontrolki, które są identyfikowane przez właściwość <xref:System.Windows.Automation.ControlType.Custom> i mogą być opisane przez właściwość <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty>.  
  
 W poniższej tabeli przedstawiono mapowanie aktywnych ról dostępności do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] typów kontroli.  
  
|Rola Active Accessibility|Typ formantu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
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
 W obszarze Active Accessibility elementy obsługują wspólny zestaw właściwości, a niektóre właściwości (takie jak `accState`) muszą opisywać różne elementy, w zależności od roli elementu. Serwery muszą implementować wszystkie metody `IAccessible`, które zwracają właściwość, nawet te, które nie są istotne dla elementu.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] definiuje wiele innych właściwości, z których niektóre odpowiadają stanom w aktywnym ułatwieniach dostępu. Niektóre są wspólne dla wszystkich elementów, ale inne są specyficzne dla typów kontroli i wzorców kontrolek. Właściwości są rozróżniane przez unikatowe identyfikatory i większość właściwości można pobrać przy użyciu jednej metody, <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> lub <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>. Wiele właściwości można również łatwo pobrać z <xref:System.Windows.Automation.AutomationElement.Current%2A> i <xref:System.Windows.Automation.AutomationElement.Cached%2A> metod dostępu do właściwości.  
  
 Dostawca automatyzacji interfejsu użytkownika nie musi implementować nieistotnych właściwości, ale może po prostu zwrócić wartość `null` dla wszystkich właściwości, które nie są obsługiwane. Ponadto usługa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Core może uzyskać pewne właściwości od domyślnego dostawcy okien i są one połączyć z właściwościami jawnie implementowanymi przez dostawcę.  
  
 Ponadto, aby obsłużyć wiele innych właściwości, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zapewnia lepszą wydajność dzięki umożliwieniu pobierania wielu właściwości przy użyciu jednego połączenia obejmującego wiele procesów.  
  
 W poniższej tabeli przedstawiono zgodność między właściwościami w dwóch modelach.  
  
|Metoda dostępu do właściwości aktywnego ułatwienia dostępu|Identyfikator właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Uwagi|  
|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|-------------|  
|`get_accKeyboardShortcut`|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty> lub <xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|`AccessKeyProperty` ma pierwszeństwo, jeśli oba są obecne.|  
|`get_accName`|<xref:System.Windows.Automation.AutomationElement.NameProperty>||  
|`get_accRole`|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|Zapoznaj się z poprzednią tabelą, aby uzyskać mapowanie ról na typy kontrolek.|  
|`get_accValue`|<xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>|Prawidłowe tylko dla typów formantów, które obsługują ValuePattern lub RangeValuePattern. Wartości RangeValue dla są znormalizowane do 0-100, aby były spójne z zachowaniem technologii MSAA. Elementy wartości używają ciągu.|  
|`get_accHelp`|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>||  
|`accLocation`|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>||  
|`get_accDescription`|Nieobsługiwane w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|`accDescription` nie miała jasnej specyfikacji w obrębie technologii MSAA, co spowodowało, że dostawcy umieszczają różne fragmenty informacji w tej właściwości.|  
|`get_accHelpTopic`|Nieobsługiwane w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]||  
  
 W poniższej tabeli przedstawiono, które właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] odpowiadają stałym stanom dostępności.  
  
|Stan aktywnego ułatwienia dostępu|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Właściwość|Czy wyzwalać zmianę stanu?|  
|-----------------------------------------------------------------------|------------------------------------------------------------------------------------|----------------------------|  
|STATE_SYSTEM_CHECKED|Dla pola wyboru, <xref:System.Windows.Automation.TogglePattern.ToggleStateProperty><br /><br /> Dla przycisku radiowego, <xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|T|  
|STATE_SYSTEM_COLLAPSED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Collapsed>|T|  
|STATE_SYSTEM_EXPANDED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Expanded> lub <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>|T|  
|STATE_SYSTEM_FOCUSABLE|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|N|  
|STATE_SYSTEM_FOCUSED|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|N|  
|STATE_SYSTEM_HASPOPUP|<xref:System.Windows.Automation.ExpandCollapsePattern> elementów menu|N|  
|STATE_SYSTEM_INVISIBLE|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> = true i <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A> powoduje <xref:System.Windows.Automation.NoClickablePointException>|N|  
|STATE_SYSTEM_LINKED|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> =<br /><br /> <xref:System.Windows.Automation.ControlType.Hyperlink>|N|  
|STATE_SYSTEM_MIXED|<xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> = <xref:System.Windows.Automation.ToggleState.Indeterminate>|N|  
|STATE_SYSTEM_MOVEABLE|<xref:System.Windows.Automation.TransformPattern.CanMoveProperty>|N|  
|STATE_SYSTEM_MUTLISELECTABLE|<xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>|N|  
|STATE_SYSTEM_OFFSCREEN|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> = true|N|  
|STATE_SYSTEM_PROTECTED|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|N|  
|STATE_SYSTEM_READONLY|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty?displayProperty=nameWithType> i <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty?displayProperty=nameWithType>|N|  
|STATE_SYSTEM_SELECTABLE|<xref:System.Windows.Automation.SelectionItemPattern> jest obsługiwana|N|  
|STATE_SYSTEM_SELECTED|<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|N|  
|STATE_SYSTEM_SIZEABLE|<xref:System.Windows.Automation.TransformPattern.TransformPatternInformation.CanResize%2A>|N|  
|STATE_SYSTEM_UNAVAILABLE|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|T|  
  
 Następujące stany nie zostały zaimplementowane przez większość aktywnych serwerów kontroli dostępności lub nie mają odpowiednika w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
|Stan aktywnego ułatwienia dostępu|Uwagi|  
|-----------------------------------------------------------------------|-------------|  
|STATE_SYSTEM_BUSY|Niedostępne w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_DEFAULT|Niedostępne w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ANIMATED|Niedostępne w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_EXTSELECTABLE|Nieszeroko zaimplementowane przez aktywne serwery ułatwień dostępu|  
|STATE_SYSTEM_MARQUEED|Nieszeroko zaimplementowane przez aktywne serwery ułatwień dostępu|  
|STATE_SYSTEM_SELFVOICING|Nieszeroko zaimplementowane przez aktywne serwery ułatwień dostępu|  
|STATE_SYSTEM_TRAVERSED|Niedostępne w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ALERT_HIGH|Nieszeroko zaimplementowane przez aktywne serwery ułatwień dostępu|  
|STATE_SYSTEM_ALERT_MEDIUM|Nieszeroko zaimplementowane przez aktywne serwery ułatwień dostępu|  
|STATE_SYSTEM_ALERT_LOW|Nieszeroko zaimplementowane przez aktywne serwery ułatwień dostępu|  
|STATE_SYSTEM_FLOATING|Nieszeroko zaimplementowane przez aktywne serwery ułatwień dostępu|  
|STATE_SYSTEM_HOTTRACKED|Niedostępne w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_PRESSED|Niedostępne w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
  
 Aby uzyskać pełną listę identyfikatorów właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Omówienie właściwości automatyzacji interfejsu użytkownika](ui-automation-properties-overview.md).  
  
<a name="uiautomation_events_compare"></a>   
## <a name="events"></a>Zdarzenia  
 Mechanizm zdarzeń w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], w przeciwieństwie do usługi Active Accessibility, nie polega na routingu zdarzeń systemu Windows (który jest ściśle powiązany z uchwytami okna) i nie wymaga od aplikacji klienckiej konfigurowania punktów zaczepienia. Subskrypcje zdarzeń można dostrajać nie tylko do określonych zdarzeń, ale do określonych części drzewa. Dostawcy mogą również dostrajać swój wzrost zdarzeń przez śledzenie zdarzeń, dla których nasłuchuje.  
  
 Łatwiejsze jest również, aby klienci pobierali elementy, które zgłaszają zdarzenia, ponieważ są one przesyłane bezpośrednio do wywołania zwrotnego zdarzenia. Właściwości elementu są automatycznie pobierane w przypadku, gdy żądanie pamięci podręcznej było aktywne, gdy klient zasubskrybuje zdarzenie.  
  
 W poniższej tabeli przedstawiono zgodność aktywnych WinEvents [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] i zdarzeń związanych z dostępnością.  
  
|WinEvent|Identyfikator zdarzenia [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|--------------|--------------------------------------------------------------------------------------------|  
|EVENT_OBJECT_ACCELERATORCHANGE|Zmiana właściwości <xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|  
|EVENT_OBJECT_CONTENTSCROLLED|Zmiana właściwości <xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> lub <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> na skojarzonych paskach przewijania|  
|EVENT_OBJECT_CREATE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_DEFACTIONCHANGE|Brak równoważnej|  
|EVENT_OBJECT_DESCRIPTIONCHANGE|Brak dokładnego odpowiednika; prawdopodobnie <xref:System.Windows.Automation.AutomationElement.HelpTextProperty> lub <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> zmiany właściwości|  
|EVENT_OBJECT_DESTROY|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_FOCUS|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_OBJECT_HELPCHANGE|Zmiana <xref:System.Windows.Automation.AutomationElement.HelpTextProperty>|  
|EVENT_OBJECT_HIDE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_LOCATIONCHANGE|Zmiana właściwości <xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|  
|EVENT_OBJECT_NAMECHANGE|Zmiana właściwości <xref:System.Windows.Automation.AutomationElement.NameProperty>|  
|EVENT_OBJECT_PARENTCHANGE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_REORDER|Niespójnie używane w usłudze Active Accessibility. Nie zdefiniowano bezpośrednio odpowiadającego zdarzenia w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|EVENT_OBJECT_SELECTION|<xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>|  
|EVENT_OBJECT_SELECTIONADD|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent>|  
|EVENT_OBJECT_SELECTIONREMOVE|<xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent>|  
|EVENT_OBJECT_SELECTIONWITHIN|Brak równoważnej|  
|EVENT_OBJECT_SHOW|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_STATECHANGE|Różne zdarzenia ze zmienionymi właściwościami|  
|EVENT_OBJECT_VALUECHANGE|Zmieniono <xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType> i <xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType>|  
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
|EVENT_SYSTEM_MINIMIZEEND|Zmiana właściwości <xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>|  
|EVENT_SYSTEM_MINIMIZESTART|Zmiana właściwości <xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>|  
|EVENT_SYSTEM_MOVESIZEEND|Zmiana właściwości <xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|  
|EVENT_SYSTEM_MOVESIZESTART|Zmiana właściwości <xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|  
|EVENT_SYSTEM_SCROLLINGEND|Zmiana właściwości <xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> lub <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty>|  
|EVENT_SYSTEM_SCROLLINGSTART|Zmiana właściwości <xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> lub <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty>|  
|EVENT_SYSTEM_SOUND|Brak równoważnej|  
|EVENT_SYSTEM_SWITCHEND|Brak równoważnej, ale zdarzenie <xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent> sygnalizuje, że nowa aplikacja otrzymała fokus|  
|EVENT_SYSTEM_SWITCHSTART|Brak równoważnej|  
|Brak równoważnej|Zmiana właściwości <xref:System.Windows.Automation.MultipleViewPattern.CurrentViewProperty>|  
|Brak równoważnej|Zmiana właściwości <xref:System.Windows.Automation.ScrollPattern.HorizontallyScrollableProperty>|  
|Brak równoważnej|Zmiana właściwości <xref:System.Windows.Automation.ScrollPattern.VerticallyScrollableProperty>|  
|Brak równoważnej|Zmiana właściwości <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty>|  
|Brak równoważnej|Zmiana właściwości <xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>|  
|Brak równoważnej|Zmiana właściwości <xref:System.Windows.Automation.ScrollPattern.HorizontalViewSizeProperty>|  
|Brak równoważnej|Zmiana właściwości <xref:System.Windows.Automation.ScrollPattern.VerticalViewSizeProperty>|  
|Brak równoważnej|Zmiana właściwości <xref:System.Windows.Automation.TogglePattern.ToggleStateProperty>|  
|Brak równoważnej|Zmiana właściwości <xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>|  
|Brak równoważnej|zdarzenie <xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent>|  
|Brak równoważnej|<xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent>|  
  
<a name="Security_compare"></a>   
## <a name="security"></a>Zabezpieczenia  
 Niektóre `IAccessible` scenariusze dostosowania wymagają zawijania `IAccessible` podstawowego i wywoływania do niego. Ma to wpływ na bezpieczeństwo, ponieważ częściowo zaufany składnik nie powinien być pośrednikiem w ścieżce kodu.  
  
 Model [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]u eliminuje konieczność wywoływania przez dostawców do innego kodu dostawcy. Usługa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Core wykonuje wszystkie wymagane agregacje.  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe założenia automatyzacji interfejsu użytkownika](index.md)
