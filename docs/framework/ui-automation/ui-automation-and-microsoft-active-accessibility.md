---
title: Automatyzacja interfejsu użytkownika a Microsoft Active Accessibility
ms.date: 03/30/2017
helpviewer_keywords:
- Active Accessibility
- UI Automation, Active Accessibility compared to
- UI Automation, Microsoft Active Accessibility
- Active Accessibility, UI Automation compared to
ms.assetid: 87bee662-0a3e-4232-a421-20e7a5968321
ms.openlocfilehash: 9a84c344ffabdaaa9d0aed68b05b7a4449776789
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179980"
---
# <a name="ui-automation-and-microsoft-active-accessibility"></a>Automatyzacja interfejsu użytkownika a Microsoft Active Accessibility
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Microsoft Active Accessibility był wcześniejszym rozwiązaniem do tworzenia aplikacji dostępnych. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]jest nowym modelem ułatwień dostępu dla systemu Microsoft Windows i ma na celu zaspokojenie potrzeb produktów technologii wspomagających i zautomatyzowanych narzędzi testowych. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]oferuje wiele ulepszeń w stosunku do aktywnej dostępności.  
  
 Ten temat zawiera główne [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] funkcje i wyjaśnia, jak te funkcje różnią się od aktywnych ułatwień dostępu.  
  
<a name="Programming_Languages_compare"></a>
## <a name="programming-languages"></a>Języki programowania  
<Active Accessibility jest oparty na modelu com (Component Object Model) z obsługą dwóch interfejsów i dlatego można go programować w językach C/C++, Microsoft Visual Basic 6.0 i językach skryptów. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)](w tym biblioteki dostawcy po stronie klienta dla standardowych formantów) jest zapisywany w kodzie zarządzanym, a aplikacje klienckie automatyzacji interfejsu użytkownika są najłatwiej programowane przy użyciu języka C# lub Visual Basic .NET. Dostawcy automatyzacji interfejsu użytkownika, które są implementacjami interfejsu, mogą być zapisywane w kodzie zarządzanym lub w języku C/C++.  
  
<a name="Support_in_Windows_Presentation_Foundation_"></a>
## <a name="support-in-windows-presentation-foundation"></a>Pomoc techniczna w programie Windows Presentation Foundation  
 Windows Presentation Foundation (WPF) to nowy model do tworzenia interfejsów użytkownika. WPF elementy nie zawierają natywnej obsługi active accessibility; jednak obsługują [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], co obejmuje obsługę pomostową dla klientów Active Accessibility. Tylko klienci napisane specjalnie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dla można w pełni korzystać z funkcji ułatwień dostępu WPF, takich jak rozbudowany obsługi tekstu.  
  
<a name="Servers_and_Clients_compare"></a>
## <a name="servers-and-clients"></a>Serwery i klienci  
 W aktywnej dostępności serwery i klienci komunikują się `IAccessible`bezpośrednio, głównie poprzez implementację serwera .  
  
 W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], podstawowa usługa leży między serwerem (nazywanym dostawcą) a klientem. Usługa podstawowa wywołuje interfejsy implementowane przez dostawców i zapewnia dodatkowe usługi, takie jak generowanie unikatowych identyfikatorów środowiska uruchomieniowego dla elementów. Aplikacje klienckie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] używają funkcji biblioteki do wywoływania usługi.  
  
 Dostawcy automatyzacji interfejsu użytkownika mogą dostarczać informacje klientom aktywnych ułatwień dostępu, a serwery aktywnych ułatwień dostępu mogą dostarczać informacje aplikacjom klienckim automatyzacji interfejsu użytkownika. Jednak ponieważ funkcja Active Accessibility nie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]udostępnia tyle informacji, ile , oba modele nie są w pełni zgodne.  
  
<a name="UI_Elements_compare"></a>
## <a name="ui-elements"></a>Elementy interfejsu użytkownika  
 Active Accessibility [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] przedstawia elementy jako `IAccessible` interfejs lub jako identyfikator podrzędny. Trudno jest porównać `IAccessible` dwa wskaźniki, aby ustalić, czy odnoszą się one do tego samego elementu.  
  
 W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], każdy element jest <xref:System.Windows.Automation.AutomationElement> reprezentowany jako obiekt. Porównanie odbywa się przy użyciu <xref:System.Windows.Automation.AutomationElement.Equals%2A> operatora równości lub metody, z których oba porównują unikatowe identyfikatory środowiska uruchomieniowego elementów.  
  
<a name="Tree_Views_and_Navigation_compare"></a>
## <a name="tree-views-and-navigation"></a>Widoki drzewa i nawigacja  
 Elementy [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] na ekranie mogą być postrzegane jako struktura drzewa z pulpitu jako katalog główny, okna aplikacji jako bezpośrednie elementy podrzędne i elementy w aplikacjach jako dalsze elementy podrzędne.  
  
 W active accessibility wiele elementów automatyzacji, które są nieistotne dla użytkowników końcowych są widoczne w drzewie. Aplikacje klienckie muszą przyjrzeć się wszystkim elementom, aby określić, które są znaczące.  
  
 Aplikacje klienckie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] automatyzacji interfejsu użytkownika są wyświetlane za pośrednictwem filtrowanego widoku. Widok zawiera tylko elementy zainteresowania: te, które przekazują informacje użytkownikowi lub umożliwiają interakcję. Wstępnie zdefiniowane widoki tylko elementy sterujące i tylko elementy zawartości są dostępne; ponadto aplikacje mogą definiować widoki niestandardowe. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]upraszcza zadanie opisywania [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] użytkownika i pomagania użytkownikowi w interakcji z aplikacją.  
  
 Nawigacja między elementami w obszarze Dostępność aktywna jest przestrzenna (na przykład przejście do elementu, który leży po lewej stronie ekranu), logiczna (na przykład przejście do następnego elementu menu lub następny element w kolejności tabulacji w oknie dialogowym) lub hierarchiczna ( na przykład przeniesienie pierwszego dziecka w kontenerze lub z podrzędnego do jego rodzica). Hierarchiczna nawigacja jest skomplikowana przez fakt, że `IAccessible`elementy podrzędne nie zawsze są obiektami, które implementują .  
  
 W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] wszystkie <xref:System.Windows.Automation.AutomationElement> elementy są obiektami obsługującymi tę samą podstawową funkcjonalność. (Z punktu widzenia dostawcy są to obiekty, które implementują interfejs odziedziczony po <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>.) Nawigacja jest głównie hierarchiczna: od rodziców do dzieci i od jednego rodzeństwa do drugiego. (Nawigacja między rodzeństwem ma element logiczny, ponieważ może być zgodna z kolejnością tabulacji). Można nawigować z dowolnego punktu początkowego, przy użyciu dowolnego <xref:System.Windows.Automation.TreeWalker> filtrowanego widoku drzewa, przy użyciu klasy. Można również przejść do określonych elementów <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> <xref:System.Windows.Automation.AutomationElement.FindAll%2A>podrzędnych lub podrzędnych za pomocą i ; na przykład jest bardzo łatwe do pobrania wszystkie elementy w oknie dialogowym, które obsługują określony wzorzec formantu.  
  
 Nawigacja [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jest bardziej spójna niż w aktywnej dostępności. Niektóre elementy, takie jak listy rozwijane i okna podręczne są wyświetlane dwukrotnie w drzewie Aktywne ułatwienia dostępu, a nawigacja z nich może mieć nieoczekiwane wyniki. W rzeczywistości jest niemożliwe do prawidłowego zaimplementowania active accessibility dla kontroli prętów zbrojeniowych. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]umożliwia ponowne najmówienie i zmianę położenia, dzięki czemu element może być umieszczony w dowolnym miejscu w drzewie, pomimo hierarchii nałożonej przez własność okien.  
  
<a name="Roles_and_Control_Types"></a>
## <a name="roles-and-control-types"></a>Role i typy kontroli  
 Active Accessibility używa `accRole` właściwości`IAccessible::get_actRole`( ) do pobierania opisu roli [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]elementu w , takich jak ROLE_SYSTEM_SLIDER lub ROLE_SYSTEM_MENUITEM. Rola elementu jest główną wskazówką do jego dostępnej funkcjonalności. Interakcja z formantem odbywa się `IAccessible::accSelect` `IAccessible::accDoDefaultAction`przy użyciu stałych metod, takich jak i . Interakcja między aplikacją [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] kliencką a `IAccessible`aplikacją jest ograniczona do tego, co można zrobić za pośrednictwem .  
  
 W przeciwieństwie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] do dużej mierze oddziela typ formantu elementu <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> (opisane przez właściwość) z jego oczekiwanej funkcjonalności. Funkcjonalność jest określana przez wzorce kontroli, które są obsługiwane przez dostawcę za pośrednictwem jego implementacji interfejsów specjalistycznych. Wzorce kontroli można połączyć, aby opisać pełny zestaw [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] funkcji obsługiwanych przez określony element. Niektórzy dostawcy są zobowiązani do obsługi określonego wzorca kontroli; na przykład dostawca pola wyboru musi obsługiwać wzorzec sterowania przełącznikiem. Inni dostawcy są zobowiązani do obsługi jednego lub więcej zestaw wzorów kontroli; na przykład przycisk musi obsługiwać przełącznik lub invoke. Jeszcze inni nie obsługują wzorców kontroli w ogóle; na przykład okienko, którego nie można przenieść, zwymiarować ani zadokować, nie ma żadnych wzorców sterowania.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]obsługuje formanty niestandardowe, <xref:System.Windows.Automation.ControlType.Custom> które są identyfikowane <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> przez właściwość i mogą być opisane przez właściwość.  
  
 W poniższej tabeli przedstawiono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mapowanie ról aktywnej dostępności do typów kontroli.  
  
|Rola Aktywne ułatwień dostępu|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]typ sterowania|  
|----------------------------------------------------------------------|----------------------------------------------------------------------------------------|  
|ROLE_SYSTEM_PUSHBUTTON|Button|  
|ROLE_SYSTEM_CLIENT|Kalendarz|  
|ROLE_SYSTEM_CHECKBUTTON|Pole wyboru|  
|ROLE_SYSTEM_COMBOBOX|Pole kombi|  
|ROLE_SYSTEM_CLIENT|Niestandardowy|  
|ROLE_SYSTEM_LIST|Siatka danych|  
|ROLE_SYSTEM_LISTITEM|Element danych|  
|ROLE_SYSTEM_DOCUMENT|Dokument|  
|ROLE_SYSTEM_TEXT|Edytuj|  
|ROLE_SYSTEM_GROUPING|Grupa|  
|ROLE_SYSTEM_LIST|Nagłówek|  
|ROLE_SYSTEM_COLUMNHEADER|Element nagłówka|  
|ROLE_SYSTEM_LINK|Hyperlink|  
|ROLE_SYSTEM_GRAPHIC|Image (Obraz)|  
|ROLE_SYSTEM_LIST|List|  
|ROLE_SYSTEM_LISTITEM|Element listy|  
|ROLE_SYSTEM_MENUPOPUP|Menu|  
|ROLE_SYSTEM_MENUBAR|Pasek menu|  
|ROLE_SYSTEM_MENUITEM|Pozycja menu|  
|ROLE_SYSTEM_PANE|Pane|  
|ROLE_SYSTEM_PROGRESSBAR|Pasek postępu|  
|ROLE_SYSTEM_RADIOBUTTON|Przycisk radiowy|  
|ROLE_SYSTEM_SCROLLBAR|Pasek przewijania|  
|ROLE_SYSTEM_SEPARATOR|Separator|  
|ROLE_SYSTEM_SLIDER|Suwak|  
|ROLE_SYSTEM_SPINBUTTON|pokrętło|  
|ROLE_SYSTEM_SPLITBUTTON|Przycisk Podziału|  
|ROLE_SYSTEM_STATUSBAR|Pasek stanu|  
|ROLE_SYSTEM_PAGETABLIST|Tab|  
|ROLE_SYSTEM_PAGETAB|Element karty|  
|ROLE_SYSTEM_TABLE|Tabela|  
|ROLE_SYSTEM_STATICTEXT|Tekst|  
|ROLE_SYSTEM_INDICATOR|Thumb|  
|ROLE_SYSTEM_TITLEBAR|Pasek tytułu|  
|ROLE_SYSTEM_TOOLBAR|Pasek narzędzi|  
|ROLE_SYSTEM_TOOLTIP|ToolTip|  
|ROLE_SYSTEM_OUTLINE|Drzewo|  
|ROLE_SYSTEM_OUTLINEITEM|Element drzewa|  
|ROLE_SYSTEM_WINDOW|Okno|  
  
 Aby uzyskać więcej informacji na temat różnych typów formantów, zobacz [Typy kontroli automatyzacji interfejsu użytkownika](ui-automation-control-types.md).  
  
<a name="States_and_Properties"></a>
## <a name="states-and-properties"></a>Stany i właściwości  
 W active accessibility elementy obsługują wspólny zestaw właściwości, a niektóre `accState`właściwości (takie jak) muszą opisywać bardzo różne rzeczy, w zależności od roli elementu. Serwery muszą implementować wszystkie metody tego `IAccessible` zwracać właściwości, nawet te, które nie są istotne dla elementu.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]definiuje wiele więcej właściwości, z których niektóre odpowiadają stanom w aktywnej dostępności. Niektóre są wspólne dla wszystkich elementów, ale inne są specyficzne dla typów kontroli i wzorców kontroli. Właściwości są wyróżniane przez unikatowe identyfikatory, a większość właściwości można <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> pobrać <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>za pomocą jednej metody lub . Wiele właściwości można również łatwo <xref:System.Windows.Automation.AutomationElement.Current%2A> pobrać <xref:System.Windows.Automation.AutomationElement.Cached%2A> z akcesorów i właściwości.  
  
 Dostawca automatyzacji interfejsu użytkownika nie musi implementować właściwości nieistotne, ale można po prostu zwrócić `null` wartość dla wszystkich właściwości, które nie obsługuje. Ponadto usługa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podstawowa może uzyskać niektóre właściwości od domyślnego dostawcy okna, a te są połączone z właściwościami jawnie zaimplementowanymi przez dostawcę.  
  
 Oprócz obsługi wielu innych właściwości, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dostarcza lepszą wydajność, umożliwiając wiele właściwości, które mają być pobierane za pomocą jednego wywołania między procesami.  
  
 W poniższej tabeli przedstawiono zgodność między właściwościami w dwóch modelach.  
  
|Akcesor właściwości Active Accessibility|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Identyfikator właściwości|Uwagi|  
|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|-------------|  
|`get_accKeyboardShortcut`|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty> lub <xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|`AccessKeyProperty`ma pierwszeństwo, jeśli oba są obecne.|  
|`get_accName`|<xref:System.Windows.Automation.AutomationElement.NameProperty>||  
|`get_accRole`|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|Zobacz poprzednią tabelę do mapowania ról do kontroli typów.|  
|`get_accValue`|<xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>|Jest prawidłowy tylko dla typów formantów obsługujących wartość ValuePattern lub RangeValuePattern. Wartości RangeValue są znormalizowane do 0-100, aby były zgodne z zachowaniem MSAA. Elementy wartości używają ciągu.|  
|`get_accHelp`|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>||  
|`accLocation`|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>||  
|`get_accDescription`|Nie jest obsługiwany w[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|`accDescription`nie miał jasnej specyfikacji w MSAA, co spowodowało, że dostawcy umieścili różne informacje w tej nieruchomości.|  
|`get_accHelpTopic`|Nie jest obsługiwany w[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]||  
  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli przedstawiono właściwości, które odpowiadają stałym stanu aktywnej dostępności.  
  
|Stan aktywnej ułatwień dostępu|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Właściwość|Wyzwala zmiany stanu?|  
|-----------------------------------------------------------------------|------------------------------------------------------------------------------------|----------------------------|  
|STATE_SYSTEM_CHECKED|W przypadku pola wyboru,<xref:System.Windows.Automation.TogglePattern.ToggleStateProperty><br /><br /> W przypadku przycisku radiowego<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|Tak|  
|STATE_SYSTEM_COLLAPSED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Collapsed>|Tak|  
|STATE_SYSTEM_EXPANDED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Expanded>Lub<xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>|Tak|  
|STATE_SYSTEM_FOCUSABLE|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|Nie|  
|STATE_SYSTEM_FOCUSED|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|Nie|  
|STATE_SYSTEM_HASPOPUP|<xref:System.Windows.Automation.ExpandCollapsePattern>dla elementów menu|Nie|  
|STATE_SYSTEM_INVISIBLE|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>= Prawda <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A> i przyczyny<xref:System.Windows.Automation.NoClickablePointException>|Nie|  
|STATE_SYSTEM_LINKED|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> =<br /><br /> <xref:System.Windows.Automation.ControlType.Hyperlink>|Nie|  
|STATE_SYSTEM_MIXED|<xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> = <xref:System.Windows.Automation.ToggleState.Indeterminate>|Nie|  
|STATE_SYSTEM_MOVEABLE|<xref:System.Windows.Automation.TransformPattern.CanMoveProperty>|Nie|  
|STATE_SYSTEM_MUTLISELECTABLE|<xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>|Nie|  
|STATE_SYSTEM_OFFSCREEN|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>= Prawda|Nie|  
|STATE_SYSTEM_PROTECTED|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|Nie|  
|STATE_SYSTEM_READONLY|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty?displayProperty=nameWithType> i <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty?displayProperty=nameWithType>|Nie|  
|STATE_SYSTEM_SELECTABLE|<xref:System.Windows.Automation.SelectionItemPattern>jest obsługiwany|Nie|  
|STATE_SYSTEM_SELECTED|<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|Nie|  
|STATE_SYSTEM_SIZEABLE|<xref:System.Windows.Automation.TransformPattern.TransformPatternInformation.CanResize%2A>|Nie|  
|STATE_SYSTEM_UNAVAILABLE|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|Tak|  
  
 Następujące stany nie zostały zaimplementowane przez większość aktywnych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]serwerów kontroli ułatwień dostępu lub nie mają odpowiednika w .  
  
|Stan aktywnej ułatwień dostępu|Uwagi|  
|-----------------------------------------------------------------------|-------------|  
|STATE_SYSTEM_BUSY|Niedostępne w[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_DEFAULT|Niedostępne w[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ANIMATED|Niedostępne w[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_EXTSELECTABLE|Nie są szeroko implementowane przez serwery Active Accessibility|  
|STATE_SYSTEM_MARQUEED|Nie są szeroko implementowane przez serwery Active Accessibility|  
|STATE_SYSTEM_SELFVOICING|Nie są szeroko implementowane przez serwery Active Accessibility|  
|STATE_SYSTEM_TRAVERSED|Niedostępne w[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ALERT_HIGH|Nie są szeroko implementowane przez serwery Active Accessibility|  
|STATE_SYSTEM_ALERT_MEDIUM|Nie są szeroko implementowane przez serwery Active Accessibility|  
|STATE_SYSTEM_ALERT_LOW|Nie są szeroko implementowane przez serwery Active Accessibility|  
|STATE_SYSTEM_FLOATING|Nie są szeroko implementowane przez serwery Active Accessibility|  
|STATE_SYSTEM_HOTTRACKED|Niedostępne w[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_PRESSED|Niedostępne w[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
  
 Aby uzyskać pełną [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] listę identyfikatorów właściwości, zobacz [Omówienie właściwości automatyzacji interfejsu użytkownika](ui-automation-properties-overview.md).  
  
<a name="uiautomation_events_compare"></a>
## <a name="events"></a>Zdarzenia  
 Mechanizm zdarzeń [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]w , w przeciwieństwie do w active accessibility, nie opiera się na routingu zdarzeń systemu Windows (który jest ściśle związany z uchwytami okien) i nie wymaga aplikacji klienckiej do konfigurowania haków. Subskrypcje zdarzeń można dostosować nie tylko do określonych zdarzeń, ale do poszczególnych części drzewa. Dostawcy mogą również dostosować ich podnoszenie zdarzeń, śledząc, jakie zdarzenia są słuchane.  
  
 Jest również łatwiejsze dla klientów, aby pobrać elementy, które podnoszą zdarzenia, ponieważ są one przekazywane bezpośrednio do wywołania zwrotnego zdarzenia. Właściwości elementu są automatycznie zbierane z przedpremierem, jeśli żądanie pamięci podręcznej było aktywne, gdy klient subskrybował zdarzenie.  
  
 W poniższej tabeli przedstawiono zgodność aktywnych ułatwień dostępu WinEvents i [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzeń.  
  
|Okręg wyborczy WinEvent|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]identyfikator zdarzenia|  
|--------------|--------------------------------------------------------------------------------------------|  
|EVENT_OBJECT_ACCELERATORCHANGE|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>zmiana właściwości|  
|EVENT_OBJECT_CONTENTSCROLLED|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>lub <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> zmiana właściwości na skojarzonych paskach przewijania|  
|EVENT_OBJECT_CREATE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_DEFACTIONCHANGE|Brak odpowiednika|  
|EVENT_OBJECT_DESCRIPTIONCHANGE|Nie ma dokładnego odpowiednika; być <xref:System.Windows.Automation.AutomationElement.HelpTextProperty> <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> może lub zmiana własności|  
|EVENT_OBJECT_DESTROY|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_FOCUS|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_OBJECT_HELPCHANGE|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>Zmienić|  
|EVENT_OBJECT_HIDE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_LOCATIONCHANGE|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>zmiana właściwości|  
|EVENT_OBJECT_NAMECHANGE|<xref:System.Windows.Automation.AutomationElement.NameProperty>zmiana właściwości|  
|EVENT_OBJECT_PARENTCHANGE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_REORDER|Nie jest konsekwentnie używany w aktywnej dostępności. W pliku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|EVENT_OBJECT_SELECTION|<xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>|  
|EVENT_OBJECT_SELECTIONADD|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent>|  
|EVENT_OBJECT_SELECTIONREMOVE|<xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent>|  
|EVENT_OBJECT_SELECTIONWITHIN|Brak odpowiednika|  
|EVENT_OBJECT_SHOW|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_STATECHANGE|Różne zdarzenia zmieniane przez właściwości|  
|EVENT_OBJECT_VALUECHANGE|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>i <xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType> zmieniono|  
|EVENT_SYSTEM_ALERT|Brak odpowiednika|  
|EVENT_SYSTEM_CAPTUREEND|Brak odpowiednika|  
|EVENT_SYSTEM_CAPTURESTART|Brak odpowiednika|  
|EVENT_SYSTEM_CONTEXTHELPEND|Brak odpowiednika|  
|EVENT_SYSTEM_CONTEXTHELPSTART|Brak odpowiednika|  
|EVENT_SYSTEM_DIALOGEND|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|  
|EVENT_SYSTEM_DIALOGSTART|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|  
|EVENT_SYSTEM_DRAGDROPEND|Brak odpowiednika|  
|EVENT_SYSTEM_DRAGDROPSTART|Brak odpowiednika|  
|EVENT_SYSTEM_FOREGROUND|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_SYSTEM_MENUEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT_SYSTEM_MENUPOPUPEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT_SYSTEM_MENUPOPUPSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT_SYSTEM_MENUSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT_SYSTEM_MINIMIZEEND|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>zmiana właściwości|  
|EVENT_SYSTEM_MINIMIZESTART|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>zmiana właściwości|  
|EVENT_SYSTEM_MOVESIZEEND|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>zmiana właściwości|  
|EVENT_SYSTEM_MOVESIZESTART|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>zmiana właściwości|  
|EVENT_SYSTEM_SCROLLINGEND|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>lub <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> zmiana własności|  
|EVENT_SYSTEM_SCROLLINGSTART|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>lub <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> zmiana własności|  
|EVENT_SYSTEM_SOUND|Brak odpowiednika|  
|EVENT_SYSTEM_SWITCHEND|Nie ma odpowiednika, <xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent> ale zdarzenie sygnalizuje, że nowa aplikacja otrzymała fokus|  
|EVENT_SYSTEM_SWITCHSTART|Brak odpowiednika|  
|Brak odpowiednika|<xref:System.Windows.Automation.MultipleViewPattern.CurrentViewProperty>zmiana właściwości|  
|Brak odpowiednika|<xref:System.Windows.Automation.ScrollPattern.HorizontallyScrollableProperty>zmiana właściwości|  
|Brak odpowiednika|<xref:System.Windows.Automation.ScrollPattern.VerticallyScrollableProperty>zmiana właściwości|  
|Brak odpowiednika|<xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty>zmiana właściwości|  
|Brak odpowiednika|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>zmiana właściwości|  
|Brak odpowiednika|<xref:System.Windows.Automation.ScrollPattern.HorizontalViewSizeProperty>zmiana właściwości|  
|Brak odpowiednika|<xref:System.Windows.Automation.ScrollPattern.VerticalViewSizeProperty>zmiana właściwości|  
|Brak odpowiednika|<xref:System.Windows.Automation.TogglePattern.ToggleStateProperty>zmiana właściwości|  
|Brak odpowiednika|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>zmiana właściwości|  
|Brak odpowiednika|<xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent>Zdarzenie|  
|Brak odpowiednika|<xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent>|  
  
<a name="Security_compare"></a>
## <a name="security"></a>Zabezpieczenia  
 Niektóre `IAccessible` scenariusze dostosowywania wymagają `IAccessible` zawijania bazy i wywoływania do niej. Ma to wpływ na bezpieczeństwo, ponieważ częściowo zaufany składnik nie powinien być pośrednikiem w ścieżce kodu.  
  
 Model [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] usuwa potrzebę dostawców do wywołania za pośrednictwem innego kodu dostawcy. Usługa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podstawowa wykonuje wszystkie niezbędne agregacji.  
  
## <a name="see-also"></a>Zobacz też

- [Podstawowe założenia automatyzacji interfejsu użytkownika](index.md)
