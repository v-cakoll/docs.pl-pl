---
title: "Automatyzacja interfejsu użytkownika a Microsoft Active Accessibility"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Active Accessibility
- UI Automation, Active Accessibility compared to
- UI Automation, Microsoft Active Accessibility
- Active Accessibility, UI Automation compared to
ms.assetid: 87bee662-0a3e-4232-a421-20e7a5968321
caps.latest.revision: "24"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: b826bff9f16dcd564e9b5bd91aab8b2170db6ce3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-and-microsoft-active-accessibility"></a>Automatyzacja interfejsu użytkownika a Microsoft Active Accessibility
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)]został wcześniej rozwiązania na udostępnienie aplikacji. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]jest to nowy model ułatwień dostępu dla [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] automatycznego narzędzia do testowania i jest przeznaczona do zaspokoić potrzeby produktów technologii pomocniczej. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]oferuje wiele ulepszeń w stosunku do [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)].  
  
 Ten temat zawiera główne funkcje [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] oraz wyjaśniono, jak te funkcje różnią się od [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)].  
  
<a name="Programming_Languages_compare"></a>   
## <a name="programming-languages"></a>Języki programowania  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]jest oparta na [!INCLUDE[TLA#tla_com](../../../includes/tlasharptla-com-md.md)] z obsługą podwójne interfejsy i dlatego program w języku C/C++ [!INCLUDE[TLA#tla_vb6](../../../includes/tlasharptla-vb6-md.md)]i języki skryptów. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)](łącznie z biblioteki dostawcy po stronie klienta dla formantów standardowych) są zapisywane w kodzie zarządzanym i aplikacje klienckie automatyzacji interfejsu użytkownika są łatwo zaprogramowany przy użyciu [!INCLUDE[TLA#tla_vcshrp](../../../includes/tlasharptla-vcshrp-md.md)] lub [!INCLUDE[TLA#tla_visualbnet](../../../includes/tlasharptla-visualbnet-md.md)]. Dostawców automatyzacji interfejsu użytkownika, które są implementacje interfejsu, mogą być zapisywane w kodzie zarządzanym lub w języku C/C++.  
  
<a name="Support_in_Windows_Presentation_Foundation_"></a>   
## <a name="support-in-windows-presentation-foundation"></a>Obsługa w systemie Windows Presentation Foundation  
 [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)]jest to nowy model do tworzenia interfejsów użytkownika. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]elementy nie zawierają macierzystą obsługę [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], jednak obsługuje [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], która obejmuje obsługę mostkowania [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] klientów. Tylko klienci napisane specjalnie dla [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mogą w pełni korzystać z funkcji ułatwień dostępu [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)], takie jak obsługa zaawansowanej tekstu.  
  
<a name="Servers_and_Clients_compare"></a>   
## <a name="servers-and-clients"></a>Serwery i klientów  
 W [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], serwery i klienci komunikują się bezpośrednio, przede wszystkim przez wdrożenie serwera `IAccessible`.  
  
 W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], usługi podstawowej znajduje się między serwerem (nazywane dostawcę) a klientem. Podstawowa usługa wykonywania wywołań do interfejsów implementowanych przez dostawców i udostępnia dodatkowe usługi, takie jak generowanie identyfikatorów unikatowy środowiska uruchomieniowego dla elementów. Aplikacje klienckie umożliwia wywołanie funkcji biblioteki [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] usługi.  
  
 Dostawcy automatyzacji interfejsu użytkownika może dostarczyć informacji do [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] klientów i [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] serwerów może dostarczyć informacji dla aplikacji klienckich automatyzacji interfejsu użytkownika. Jednak ponieważ [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] nie ujawnia jak najwięcej informacji [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], dwa modele nie są w pełni zgodne.  
  
<a name="UI_Elements_compare"></a>   
## <a name="ui-elements"></a>Elementy interfejsu użytkownika  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]przedstawia informacje o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów albo jako `IAccessible` interfejsu lub jako identyfikatora podrzędnego. Jest trudne do porównania dwóch `IAccessible` wskaźniki do określenia, czy odnoszą się do tego samego elementu.  
  
 W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], każdy element jest reprezentowany jako <xref:System.Windows.Automation.AutomationElement> obiektu. Porównanie wykonuje się za pomocą operatora równości lub <xref:System.Windows.Automation.AutomationElement.Equals%2A> metody, które porównania identyfikatory unikatowy środowiska uruchomieniowego elementów.  
  
<a name="Tree_Views_and_Navigation_compare"></a>   
## <a name="tree-views-and-navigation"></a>Widok drzewa i nawigacji  
 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] Elementy na ekranie są widoczne w strukturze drzewa z pulpitem jako katalogu głównego, aplikacji systemu windows jako bezpośrednie elementy podrzędne i elementów w obrębie aplikacji jako dodatkowe elementy podrzędne.  
  
 W [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], wiele elementów automatyzacji, które nie mają znaczenia dla użytkowników końcowych są widoczne w drzewie. Aplikacje klienckie trzeba przyjrzeć się wszystkie elementy, aby określić, które są istotne.  
  
 Automatyzacja interfejsu użytkownika klienta aplikacji, zobacz [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] za pośrednictwem widoku filtrowanego. Widok zawiera tylko elementy odsetek: te, które zapewniają informacji do użytkownika lub Włącz interakcji. Wstępnie zdefiniowane widoki tylko elementy kontroli i tylko elementy zawartości są dostępne; Ponadto aplikacje można zdefiniować widoków niestandardowych. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]upraszcza proces opisujące [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] do użytkownika oraz użytkownika interakcji z aplikacją.  
  
 Nawigacji między elementami w [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], albo przestrzennych (na przykład przechodzenia do elementu, który znajduje się w lewo na ekranie), logiczne (na przykład przechodzenia do następnego elementu menu lub następnego elementu w kolejności tabulacji w oknie dialogowym) lub hierarchicznych (dla przykład przenoszenia pierwszego elementu podrzędnego w kontenerze lub podrzędnych do elementu nadrzędnego). Hierarchiczna nawigacji jest złożona faktem, że elementy podrzędne nie są zawsze obiektów implementujących `IAccessible`.  
  
 W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], wszystkie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy są <xref:System.Windows.Automation.AutomationElement> obiektów, które obsługują te same funkcje podstawowe. (Z punktu widzenia dostawcy są obiektów implementujących interfejs odziedziczone <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>.) Nawigacja jest głównie hierarchiczna: z obiektów nadrzędnych do podrzędnych i jeden element równorzędny do następnego. (Nawigacji między równorzędnymi ma element logicznych, ponieważ może on być zgodny kolejności tabulacji.) Można przejść z dowolnego punktu początkowego, przy użyciu dowolnego filtrowane widoku drzewa, <xref:System.Windows.Automation.TreeWalker> klasy. Można także przechodzić do konkretnego obiektów podrzędnych ani elementów podrzędnych za pomocą <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> i <xref:System.Windows.Automation.AutomationElement.FindAll%2A>, na przykład jest bardzo proste pobrać wszystkie elementy w oknie dialogowym obsługujących wzorzec określonego formantu.  
  
 Nawigacja w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jest lepsze niż w [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]. Niektóre elementy, takie jak listy rozwijane i wyświetlanie okien wyskakujących pojawiają się dwukrotnie w [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] drzewa i nawigacji z nich mogą mieć nieoczekiwane wyniki. Faktycznie nie można prawidłowo zaimplementować [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] dla formantu paska pomocniczego. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Umożliwia reparenting i położenia, dzięki czemu elementu można umieścić dowolne miejsce w drzewie niezależnie od hierarchii powodowanego przez prawo własności do systemu windows.  
  
<a name="Roles_and_Control_Types"></a>   
## <a name="roles-and-control-types"></a>Role i typy formantów  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]używa `accRole` właściwości (`IAccessible::get_actRole`) można pobrać opis roli elementu w [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], na przykład ROLE_SYSTEM_SLIDER lub ROLE_SYSTEM_MENUITEM. Rola elementu jest głównym clue do jego dostępnych funkcji. Interakcji z formantem jest realizowane za pośrednictwem metody stałej, takich jak `IAccessible::accSelect` i `IAccessible::accDoDefaultAction`. Interakcja między aplikacji klienckiej i [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] wynosi co można zrobić za pomocą `IAccessible`.  
  
 Z kolei [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] przede wszystkim oddziela typu formantu elementu (opisanego przez <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> właściwości) z jego funkcjonalność. Funkcja jest określana przez wzorce kontrolki, które są obsługiwane przez dostawcę za pośrednictwem jego implementacji interfejsów specjalne. Wzorce formantu można łączyć do opisania pełnego zestawu funkcji oferowanych przez określonego [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementu. Niektórzy dostawcy są wymagane do obsługi wzorcu określonego formantu. na przykład pole wyboru dla dostawcy musi obsługiwać Toggle — wzorzec formantu. Inni dostawcy są wymagane do obsługi co najmniej jeden zestaw wzorców formantu; na przykład przycisk musi obsługiwać przełącznika lub Invoke. Nadal nie wzorców formantu innych obsługiwać wszystkich; na przykład okienko, którego nie można przenieść, zmiany rozmiaru ani zadokowane nie ma żadnych wzorców formantu.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]obsługuje formantów niestandardowych, które są identyfikowane przez <xref:System.Windows.Automation.ControlType.Custom> właściwości i można opisać za pomocą <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> właściwości.  
  
 W poniższej tabeli przedstawiono mapowanie [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] ról [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolowanie typów.  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]Rola|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Typ formantu|  
|----------------------------------------------------------------------|----------------------------------------------------------------------------------------|  
|ROLE_SYSTEM_PUSHBUTTON|Przycisk|  
|ROLE_SYSTEM_CLIENT|Kalendarz|  
|ROLE_SYSTEM_CHECKBUTTON|Pole wyboru|  
|ROLE_SYSTEM_COMBOBOX|Pola kombi|  
|ROLE_SYSTEM_CLIENT|Niestandardowe|  
|ROLE_SYSTEM_LIST|Siatki danych|  
|ROLE_SYSTEM_LISTITEM|Element danych|  
|ROLE_SYSTEM_DOCUMENT|dokument|  
|ROLE_SYSTEM_TEXT|Edytowanie|  
|ROLE_SYSTEM_GROUPING|Grupa|  
|ROLE_SYSTEM_LIST|nagłówek|  
|ROLE_SYSTEM_COLUMNHEADER|Element nagłówka|  
|ROLE_SYSTEM_LINK|Hyperlink|  
|ROLE_SYSTEM_GRAPHIC|Obraz|  
|ROLE_SYSTEM_LIST|Lista|  
|ROLE_SYSTEM_LISTITEM|element listy|  
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
  
 Aby uzyskać więcej informacji na temat typów inny formant, zobacz [typy formantów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-types.md).  
  
<a name="States_and_Properties"></a>   
## <a name="states-and-properties"></a>Stany i właściwości  
 W [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], elementy obsługują wspólny zbiór właściwości, a niektóre właściwości (takie jak `accState`) musi opisywać bardzo różnych rzeczy, w zależności od roli elementu. Serwery muszą implementować wszystkie metody `IAccessible` , które zwracają właściwości, nawet te, które nie są odpowiednie do elementu.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]definiuje wiele innych właściwości, niektóre z nich odpowiadają stanów w [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]. Niektóre są wspólne dla wszystkich elementów, ale inne są specyficzne dla typów kontroli i wzorce formantu. Właściwości można rozróżnić za unikatowych identyfikatorów i większość właściwości można pobrać za pomocą pojedynczej metody <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> lub <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>. Wiele właściwości są również łatwe pobieranie z <xref:System.Windows.Automation.AutomationElement.Current%2A> i <xref:System.Windows.Automation.AutomationElement.Cached%2A> metod dostępu do właściwości.  
  
 Dostawca automatyzacji interfejsu użytkownika nie ma implementacji właściwości nie ma znaczenia, ale po prostu przywrócić `null` wartość właściwości nie obsługuje. Ponadto [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] usługi podstawowej i można uzyskać niektórych właściwości pochodzących od domyślnego dostawcy okna, są one połączone z właściwościami jawnie implementowana przez dostawcę.  
  
 Oprócz obsługi wiele innych właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dostaw lepsza wydajność, zezwalając na wiele właściwości, które mają zostać pobrane z wywołaniem jednym między procesami.  
  
 W poniższej tabeli przedstawiono związek między właściwości w obu modeli.  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]metody dostępu właściwości|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Identyfikator właściwości|Uwagi|  
|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|-------------|  
|`get_accKeyboardShortcut`|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty>lub<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|`AccessKeyProperty`ma pierwszeństwo, jeśli oba parametry są obecne.|  
|`get_accName`|<xref:System.Windows.Automation.AutomationElement.NameProperty>||  
|`get_accRole`|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|Zobacz w poprzedniej tabeli mapowania ról do kontroli typów.|  
|`get_accValue`|<xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>|Dotyczy tylko typy formantów, które obsługują klasy ValuePattern lub klasy RangeValuePattern. RangeValue dla wartości są znormalizowane do 0-100, aby były spójne z zachowaniem metody MSAA. Wartość elementów, użyj ciągu.|  
|`get_accHelp`|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>||  
|`accLocation`|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>||  
|`get_accDescription`|Nieobsługiwane w[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|`accDescription`nie miał wyczyść specyfikacji w MSAA, co spowodowało dostawców umieszczenie różnych rodzajów informacji w tej właściwości.|  
|`get_accHelpTopic`|Nieobsługiwane w[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]||  
  
 W poniższej tabeli przedstawiono którego [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] odpowiada właściwości [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] stanu stałe.  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]Stan|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Właściwość|Zmiana stanu wyzwalaczy?|  
|-----------------------------------------------------------------------|------------------------------------------------------------------------------------|----------------------------|  
|STATE_SYSTEM_CHECKED|Dla pola wyboru<xref:System.Windows.Automation.TogglePattern.ToggleStateProperty><br /><br /> Dla przycisku radiowego<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|T|  
|STATE_SYSTEM_COLLAPSED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Collapsed>|T|  
|STATE_SYSTEM_EXPANDED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Expanded>lub<xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>|T|  
|STATE_SYSTEM_FOCUSABLE|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|N|  
|STATE_SYSTEM_FOCUSED|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|N|  
|STATE_SYSTEM_HASPOPUP|<xref:System.Windows.Automation.ExpandCollapsePattern>dla elementów menu|N|  
|STATE_SYSTEM_INVISIBLE|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>= True i <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A> powoduje, że<xref:System.Windows.Automation.NoClickablePointException>|N|  
|STATE_SYSTEM_LINKED|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> =<br /><br /> <xref:System.Windows.Automation.ControlType.Hyperlink>|N|  
|STATE_SYSTEM_MIXED|<xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> = <xref:System.Windows.Automation.ToggleState.Indeterminate>|N|  
|STATE_SYSTEM_MOVEABLE|<xref:System.Windows.Automation.TransformPattern.CanMoveProperty>|N|  
|STATE_SYSTEM_MUTLISELECTABLE|<xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>|N|  
|STATE_SYSTEM_OFFSCREEN|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>= PRAWDA|N|  
|STATE_SYSTEM_PROTECTED|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|N|  
|STATE_SYSTEM_READONLY|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty?displayProperty=nameWithType>i<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty?displayProperty=nameWithType>|N|  
|STATE_SYSTEM_SELECTABLE|<xref:System.Windows.Automation.SelectionItemPattern>jest obsługiwana|N|  
|STATE_SYSTEM_SELECTED|<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|N|  
|STATE_SYSTEM_SIZEABLE|<xref:System.Windows.Automation.TransformPattern.TransformPatternInformation.CanResize%2A>|N|  
|STATE_SYSTEM_UNAVAILABLE|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|T|  
  
 Następujące stany albo nie zostały zaimplementowane przez większość [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] sterować serwerami lub nie mają odpowiednika w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]Stan|Uwagi|  
|-----------------------------------------------------------------------|-------------|  
|STATE_SYSTEM_BUSY|Nie jest dostępna w[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_DEFAULT|Nie jest dostępna w[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ANIMATED|Nie jest dostępna w[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_EXTSELECTABLE|Nie są powszechnie implementowany przez [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] serwerów|  
|STATE_SYSTEM_MARQUEED|Nie są powszechnie implementowany przez [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] serwerów|  
|STATE_SYSTEM_SELFVOICING|Nie są powszechnie implementowany przez [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] serwerów|  
|STATE_SYSTEM_TRAVERSED|Nie jest dostępna w[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ALERT_HIGH|Nie są powszechnie implementowany przez [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] serwerów|  
|STATE_SYSTEM_ALERT_MEDIUM|Nie są powszechnie implementowany przez [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] serwerów|  
|STATE_SYSTEM_ALERT_LOW|Nie są powszechnie implementowany przez [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] serwerów|  
|STATE_SYSTEM_FLOATING|Nie są powszechnie implementowany przez [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] serwerów|  
|STATE_SYSTEM_HOTTRACKED|Nie jest dostępna w[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_PRESSED|Nie jest dostępna w[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
  
 Aby uzyskać pełną listę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości identyfikatorów, zobacz [Przegląd właściwości automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
<a name="uiautomation_events_compare"></a>   
## <a name="events"></a>Zdarzenia  
 Mechanizm zdarzeń [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], w odróżnieniu od w [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], nie bazuje na routingu zdarzeń systemu Windows, (która jest ściśle związany się przy użyciu dojścia do okna) i nie wymaga aplikacji klienta, aby skonfigurować punkty zaczepienia. Subskrypcjami zdarzeń może być dopracowaniu nie tylko na określone zdarzenia, ale do określonej części drzewa. Dostawców można również dostosować ich wywoływanie zdarzeń przez śledzenie jakie zdarzenia są prowadzi nasłuch dla.  
  
 Jest również ułatwić klientom na pobieranie elementów, które uruchamiają zdarzenia, ponieważ są one przekazywane bezpośrednio do zdarzenia wywołania zwrotnego. Właściwości elementu są automatycznie prefetched, jeśli żądanie pamięci podręcznej był aktywny, gdy klient subskrybuje zdarzenia.  
  
 W poniższej tabeli przedstawiono zgodność [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] WinEvents i [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia.  
  
|WinEvent|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Identyfikator zdarzenia|  
|--------------|--------------------------------------------------------------------------------------------|  
|EVENT_OBJECT_ACCELERATORCHANGE|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>Zmiana właściwości|  
|EVENT_OBJECT_CONTENTSCROLLED|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>lub <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> zmiany właściwości na paski przewijania skojarzone|  
|EVENT_OBJECT_CREATE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_DEFACTIONCHANGE|Odpowiednika|  
|EVENT_OBJECT_DESCRIPTIONCHANGE|Nie jest dokładnym odpowiednikiem; być może <xref:System.Windows.Automation.AutomationElement.HelpTextProperty> lub <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> zmiany właściwości|  
|EVENT_OBJECT_DESTROY|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_FOCUS|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_OBJECT_HELPCHANGE|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>zmiany|  
|EVENT_OBJECT_HIDE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_LOCATIONCHANGE|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>Zmiana właściwości|  
|EVENT_OBJECT_NAMECHANGE|<xref:System.Windows.Automation.AutomationElement.NameProperty>Zmiana właściwości|  
|EVENT_OBJECT_PARENTCHANGE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_REORDER|Nie zawsze są używane w [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]. Nie bezpośrednio odpowiednie zdarzenie jest zdefiniowany w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|EVENT_OBJECT_SELECTION|<xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>|  
|EVENT_OBJECT_SELECTIONADD|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent>|  
|EVENT_OBJECT_SELECTIONREMOVE|<xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent>|  
|EVENT_OBJECT_SELECTIONWITHIN|Odpowiednika|  
|EVENT_OBJECT_SHOW|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_STATECHANGE|Różne zdarzenia zmiany właściwości|  
|EVENT_OBJECT_VALUECHANGE|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>i <xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType> zmienione|  
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
|EVENT_SYSTEM_MINIMIZEEND|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>Zmiana właściwości|  
|EVENT_SYSTEM_MINIMIZESTART|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>Zmiana właściwości|  
|EVENT_SYSTEM_MOVESIZEEND|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>Zmiana właściwości|  
|EVENT_SYSTEM_MOVESIZESTART|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>Zmiana właściwości|  
|EVENT_SYSTEM_SCROLLINGEND|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>lub <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> zmiany właściwości|  
|EVENT_SYSTEM_SCROLLINGSTART|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>lub <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> zmiany właściwości|  
|EVENT_SYSTEM_SOUND|Odpowiednika|  
|EVENT_SYSTEM_SWITCHEND|Odpowiednika, ale <xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent> zdarzenie sygnalizuje, że nowa aplikacja odebrał fokus|  
|EVENT_SYSTEM_SWITCHSTART|Odpowiednika|  
|Odpowiednika|<xref:System.Windows.Automation.MultipleViewPattern.CurrentViewProperty>Zmiana właściwości|  
|Odpowiednika|<xref:System.Windows.Automation.ScrollPattern.HorizontallyScrollableProperty>Zmiana właściwości|  
|Odpowiednika|<xref:System.Windows.Automation.ScrollPattern.VerticallyScrollableProperty>Zmiana właściwości|  
|Odpowiednika|<xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty>Zmiana właściwości|  
|Odpowiednika|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>Zmiana właściwości|  
|Odpowiednika|<xref:System.Windows.Automation.ScrollPattern.HorizontalViewSizeProperty>Zmiana właściwości|  
|Odpowiednika|<xref:System.Windows.Automation.ScrollPattern.VerticalViewSizeProperty>Zmiana właściwości|  
|Odpowiednika|<xref:System.Windows.Automation.TogglePattern.ToggleStateProperty>Zmiana właściwości|  
|Odpowiednika|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>Zmiana właściwości|  
|Odpowiednika|<xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent>zdarzenia|  
|Odpowiednika|<xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent>|  
  
<a name="Security_compare"></a>   
## <a name="security"></a>Zabezpieczenia  
 Niektóre `IAccessible` scenariusze dostosowywania wymagają zawijania podstawowej `IAccessible` i wywoływanie przez do niego. Ma to wpływ na bezpieczeństwo, ponieważ składnik częściowo zaufane nie powinien być pośrednik w ścieżce kodu.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Modelu eliminuje to potrzebę dostawców umożliwia wywołanie za pośrednictwem innego dostawcy kodu. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Core usługa ma wszystkie niezbędne agregacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe założenia automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/index.md)
