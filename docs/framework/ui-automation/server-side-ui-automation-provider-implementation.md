---
title: Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera
ms.date: 03/30/2017
helpviewer_keywords:
- server-side UI Automation provider implementation
- UI Automation, server-side provider implementation
- provider implementation, UI Automation
ms.assetid: 6acc6d08-bd67-4e2e-915c-9c1d34eb86fe
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: d8a6d604e78e1568714d5b574594af752abe221e
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56305510"
---
# <a name="server-side-ui-automation-provider-implementation"></a>Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tej sekcji opisano, jak do implementowania dostawcy automatyzacji interfejsu użytkownika po stronie serwera dla formantu niestandardowego.  
  
 Implementacja dla elementów Windows Presentation Foundation (WPF) i innych niż-[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] elementów (takich jak zaprojektowana z myślą o [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]) różni się. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] elementy zapewnia pomoc techniczną dla [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] przez klasę pochodną <xref:System.Windows.Automation.Peers.AutomationPeer>. Non -[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] elementy zapewniają pomoc techniczną za pomocą implementacji interfejsów dostawcy.  
  
<a name="Security_Considerations"></a>   
## <a name="security-considerations"></a>Zagadnienia dotyczące zabezpieczeń  
 Powinien być zapisywany dostawcy, dzięki czemu mogą one działać w środowisku częściowego zaufania. Ponieważ UIAutomationClient.dll nie jest skonfigurowany do uruchamiania w częściowej relacji zaufania, kod dostawcy nie może odwoływać się tego zestawu. Jeśli tak jest, dzięki czemu kod może uruchamiać w środowisku pełnego zaufania, ale następnie nie działać w środowisku częściowego zaufania.  
  
 W szczególności należy używać pola z klas w UIAutomationClient.dll, takich jak te w <xref:System.Windows.Automation.AutomationElement>. Zamiast tego należy użyć równoważne pola z klas w UIAutomationTypes.dll, takich jak <xref:System.Windows.Automation.AutomationElementIdentifiers>.  
  
<a name="Provider_Implementation_by_WPF_Elements"></a>   
## <a name="provider-implementation-by-windows-presentation-foundation-elements"></a>Implementacja dostawcy przez elementy programu Windows Presentation Foundation  
 Aby uzyskać więcej informacji na ten temat, zobacz [automatyzacji interfejsu użytkownika formantu niestandardowego WPF](../../../docs/framework/wpf/controls/ui-automation-of-a-wpf-custom-control.md).  
  
<a name="Provider_Implementation_by_non_WPF_Elements"></a>   
## <a name="provider-implementation-by-non-wpf-elements"></a>Implementacja dostawcy przez elementy innego niż WPF  
 Niestandardowe kontrolki, które nie są częścią [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] framework, ale są zapisywane w kodzie zarządzanym (w większości przypadków są to [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] formantów), zapewnia pomoc techniczną dla [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] poprzez implementację interfejsów. Każdy element musi implementować co najmniej jeden z interfejsów wymienionych w pierwszej tabeli w następnej sekcji. Ponadto jeśli element obsługuje jeden lub więcej wzorców kontrolek, musi implementować odpowiedni interfejs dla każdego — wzorzec kontrolki.  
  
 Twoje [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] projekt dostawcy musi odwoływać się do następujących zestawów:  
  
-   UIAutomationProviders.dll  
  
-   UIAutomationTypes.dll  
  
-   WindowsBase.dll  
  
  
<a name="Provider_Interfaces"></a>   
### <a name="provider-interfaces"></a>Interfejsy dostawcy  
 Każdy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dostawca musi implementować jeden z następujących interfejsów.  
  
|Interface|Opis|  
|---------------|-----------------|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderSimple>|Oferuje funkcję dla prostych formantem obsługiwanym w oknie, takie jak obsługa wzorców kontrolki i właściwości.|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderFragment>|Dziedziczy <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>. Dodaje funkcjonalność dotyczącą elementu w kontrolce złożone, w tym nawigacji w obrębie fragmentu, ustawienie fokusu i zwraca prostokąt otaczający element.|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>|Dziedziczy <xref:System.Windows.Automation.Provider.IRawElementProviderFragment>. Dodaje funkcjonalność dotyczącą elementu głównego w kontrolce złożonych tym lokalizowania elementu podrzędnego na określonych współrzędnych i ustawiania stanu koncentracji uwagi dla całego formantu.|  
  
 Następujące interfejsy zapewniają dodatkowe funkcje, ale nie są wymagane do zaimplementowania.  
  
|Interface|Opis|  
|---------------|-----------------|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderAdviseEvents>|Umożliwia dostawcy do śledzenia żądań dla zdarzeń.|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride>|Umożliwia zmianę położenia okienkowych elementów w obrębie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa fragmentu.|  
  
 Wszystkie interfejsy w <xref:System.Windows.Automation.Provider> przestrzeni nazw służą do obsługi wzorzec kontroli.  
  
<a name="Requirements_for_Non_WPF_Providers"></a>   
### <a name="requirements-for-non-wpf-providers"></a>Wymagania dotyczące dostawców innych niż WPF  
 W celu komunikowania się z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], kontrolki, należy zaimplementować następujące główne obszary funkcji:  
  
|Funkcja|Implementacja|  
|-------------------|--------------------|  
|Udostępnianie dostawcy do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|W odpowiedzi na wiadomość WM_GETOBJECT wysyłany do okna kontrolki, zwraca obiekt, który implementuje <xref:System.Windows.Automation.Provider.IRawElementProviderSimple> (lub interfejs pochodny). Dla fragmentów musi to być dostawcy dla głównego fragmentu.|  
|Podaj wartości właściwości|Implementowanie <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPropertyValue%2A> świadczenia lub wartości zastępcze.|  
|Włącz klienta wchodzić w interakcje z kontrolką|Implementować interfejsy, które obsługują wzorce kontrolki, takie jak <xref:System.Windows.Automation.Provider.IInvokeProvider>. Zwróć tych dostawców wzorca w danej implementacji <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A>.|  
|Wywoływanie zdarzeń|Wywołanie jednej z metod statycznych <xref:System.Windows.Automation.Provider.AutomationInteropProvider> aby wywołać zdarzenie, które klient może nasłuchiwać.|  
|Włączanie nawigacji i koncentrujących się w obrębie fragmentu|Implementowanie <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> dla każdego elementu w obrębie fragmentu. (Nie jest konieczny dla elementów, które nie należą do fragmentu.)|  
|Włącz ukierunkowywanie i lokalizację elementu podrzędnego w fragmentu|Implementowanie <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>. (Nie jest konieczny dla elementów, które są nie fragmentu katalogów głównych.)|  
  
<a name="Property_Values_in_Non_WPF_Providers"></a>   
### <a name="property-values-in-non-wpf-providers"></a>Wartości właściwości w dostawcy innego niż WPF  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dostawców w przypadku kontrolek niestandardowych musi obsługiwać niektórych właściwości, których można użyć systemu automatyzacji, a także aplikacji klienckich. Dla elementów, które są hostowane w systemie windows (parametrów hWnd) [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] można pobrać niektórych właściwości z domyślnego dostawcę okna, ale musisz uzyskać inne od dostawcy niestandardowego.  
  
 Dostawców dla formantów HWND na podstawie zazwyczaj trzeba podać następujące właściwości (identyfikowanych na podstawie wartości pól):  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.ProcessIdProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.ClassNameProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.HasKeyboardFocusProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.IsPasswordProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.RuntimeIdProperty>  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElementIdentifiers.RuntimeIdProperty> Prosty element lub fragment hostowanych w oknie głównym są uzyskiwane z okna; jednak podać własne identyfikatory fragmentu elementy poniżej katalogu głównego (na przykład elementy listy w polu listy). Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.GetRuntimeId%2A>.  
>   
>  <xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty> Ma zostać zwrócony dla dostawców hostowanych w [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] kontroli. Domyślny dostawca okno może być w tym przypadku nie można pobrać poprawną wartość.  
>   
>  <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> Zwykle jest dostarczana przez dostawcę hosta. Na przykład, jeśli formant niestandardowy jest tworzony na podstawie <xref:System.Windows.Forms.Control>, nazwa pochodzi od `Text` właściwości formantu.  
  
 Przykładowy kod, zobacz [właściwości od dostawcy automatyzacji interfejsu użytkownika zwrot](../../../docs/framework/ui-automation/return-properties-from-a-ui-automation-provider.md).  
  
<a name="Events_in_Non_WPF_Providers"></a>   
### <a name="events-in-non-wpf-providers"></a>Zdarzenia w WPF innych dostawców  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dostawców powinny wywoływać zdarzenia, aby powiadomić klienta aplikacje o zmianach w stan interfejsu użytkownika. Następujące metody umożliwiają wywoływanie zdarzeń.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseAutomationEvent%2A>|Wywołuje różne wydarzeń, takich jak zdarzenia wyzwolone przez wzorce kontrolki.|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseAutomationPropertyChangedEvent%2A>|Zgłasza zdarzenie, gdy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości została zmieniona.|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseStructureChangedEvent%2A>|Zgłasza zdarzenie, gdy struktury [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa został zmieniony; na przykład poprzez usunięcie lub dodanie elementu.|  
  
 Zdarzenie ma na celu powiadomić klienta czegoś protokole [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], czy działanie jest wyzwalane przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sam system. Na przykład, zdarzenie, które są identyfikowane za pomocą <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent> powinien być wywoływany, gdy kontrolka jest wywoływana za pośrednictwem danych wejściowych użytkownika bezpośrednich lub za pośrednictwem wywołania aplikacji klienta <xref:System.Windows.Automation.InvokePattern.Invoke%2A>.  
  
 Aby zoptymalizować wydajność, Dostawca można selektywnie wywoływanie zdarzeń lub Zgłoś Brak zdarzeń na wszystkich, jeśli żadna aplikacja klienta nie jest zarejestrowany do ich odbierania. Następujące metody są używane do optymalizacji.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A>|Ta właściwość statyczna Określa, czy wszystkie aplikacje klienckie subskrybowany przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia.|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderAdviseEvents>|Implementacja dostawcy tego interfejsu w folderze głównym fragmentu umożliwia zalecana, gdy klienci rejestrować i wyrejestrowywać programy obsługi zdarzeń dla zdarzenia na fragment.|  
  
<a name="Non_WPF_Provider_Navigation"></a>   
### <a name="non-wpf-provider-navigation"></a>Nawigacja dostawcy innego niż WPF  
 Dostawców na potrzeby proste formanty, takie jak niestandardowy przycisk hostowanych w oknie (HWND) nie ma potrzeby obsługi nawigacji w obrębie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa. Nawigacja do i z elementem jest obsługiwany przez domyślnego dostawcę dla okna hosta, które określono w implementacji <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>. Podczas implementowania dostawcy dla złożonych kontrolek niestandardowych, jednak musi obsługiwać nawigacji między węzeł główny fragmentu i jego obiektów podrzędnych oraz między węzłami tego samego poziomu.  
  
> [!NOTE]
>  Elementy fragmentu innym niż katalog główny musi zwracać `null` odwoływać się z <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>, ponieważ nie są one bezpośrednio hostowane w oknie, a nie domyślny dostawca może obsługiwać nawigacji do i z nich.  
  
 Struktura fragmentu zależy od implementacji <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A>. Dla każdego kierunku z każdego fragmentu, możliwe, ta metoda zwraca obiekt dostawcy dla elementu w tym kierunku. Jeśli nie ma żadnego elementu, w tym kierunku, metoda zwraca `null` odwołania.  
  
 Główny fragmentu obsługuje nawigacji tylko do elementów podrzędnych. Na przykład pole listy zwraca pierwszy element na liście po kierunek <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild>i ostatniego elementu, który ma kierunek <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>. Główny fragment nie obsługuje Nawigacja do elementu nadrzędnego lub elementów równorzędnych; jest to obsługiwane przez dostawcę okna hosta.  
  
 Elementy fragmentu, które nie są głównymi musi obsługiwać nawigacji do elementu nadrzędnego, a także do wszystkich elementów równorzędnych i elementy podrzędne, które mają.  
  
<a name="Non_WPF_Provider_Reparenting"></a>   
### <a name="non-wpf-provider-reparenting"></a>Dostawca nie WPF zmiana elementu nadrzędnego  
 Wyskakujące okienka są faktycznie najwyższego poziomu systemu windows, a więc domyślnie są wyświetlane w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa jako elementy podrzędne pulpitu. W wielu przypadkach jednak wyskakujące okienka są logicznie dzieci niektóre inne kontrolki. Na przykład listy rozwijanej pola kombi są logicznie podrzędne pola kombi. Podobnie okno podręczne menu logicznie jest elementem podrzędnym elementu menu. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zapewnia obsługę nadrzędne wyskakującego okienka, aby były wyświetlane jako elementy podrzędne formant.  
  
 Aby zmienić elementu nadrzędnego okno podręczne:  
  
1.  Tworzenie dostawcy dla tego okna. Wymaga to, że klasy okna podręcznego jest znana z wyprzedzeniem.  
  
2.  Zaimplementuj wszystkie właściwości i wzorce w zwykły sposób tym okno podręczne, tak, jakby była kontroli samodzielną.  
  
3.  Implementowanie <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A> właściwości, tak że zwraca wartość uzyskana z <xref:System.Windows.Automation.Provider.AutomationInteropProvider.HostProviderFromHandle%2A>, gdzie parametr jest uchwyt okna podręcznego okna.  
  
4.  Implementowanie <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> dla tego okna i jego obiektu nadrzędnego, tak że nawigacja odbywa się prawidłowo z logiczną elementu nadrzędnego do podrzędnych logicznego oraz między elementami podrzędnymi tego samego poziomu.  
  
 Gdy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] napotka oknie podręcznym rozpoznaje nawigacji jest przesłaniana z domyślnego i nakłada się na oknie podręcznym po napotkaniu się jako element podrzędny pulpitu. Zamiast tego węzła tylko będzie dostępny za pośrednictwem tego fragmentu.  
  
 Zmiana elementu nadrzędnego nie jest odpowiednia w sytuacjach, w którym formant może obsługiwać oknem każdej klasy. Na przykład pasek pomocniczy umożliwia hostowanie dowolnego typu HWND w jego pasma. Obsługa tych przypadków [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsługuje alternatywnej formy relokacji HWND, zgodnie z opisem w następnej sekcji.  
  
<a name="Non_WPF_Provider_Repositioning"></a>   
### <a name="non-wpf-provider-repositioning"></a>Dostawca nie WPF zmiana położenia  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] fragmenty mogą zawierać dwóch lub więcej elementów, które każdy znajdują się w oknie (HWND). Ponieważ każdy HWND ma swój własny domyślnego dostawcę, który uwzględnia HWND, aby być obiektem podrzędnym obiektu zawierającego HWND, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa domyślnie pokaże parametrów hWnd we fragmencie jako elementy podrzędne okna nadrzędnego. W większości przypadków jest to pożądane zachowania, ale czasami może ona prowadzić do wprowadzenia w błąd, ponieważ jest niezgodna Struktura logiczna [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Dobrym przykładem jest formantem paska pomocniczego. Pasek pomocniczy zawiera przedziałami, które z kolei może zawierać kontrolkę na podstawie HWND, takie jak pasek narzędzi, pole edycji lub pola kombi. Domyślny dostawca okna dla paska pomocniczego HWND zobaczy kontroli poza pasmem parametrów hWnd jako elementy podrzędne oraz dostawcy paska pomocniczego widzi grup jako elementy podrzędne. Ponieważ dostawca HWND dostawcy paska pomocniczego współpracującą i łączenia ich elementy podrzędne, grup i kontrolę opartą na HWND są traktowane jako elementy podrzędne paska pomocniczego. Logicznie jednak tylko paski powinna zostać wyświetlona jako elementy podrzędne paska pomocniczego, a każdy dostawca poza pasmem powinny być połączone z domyślnego dostawcę HWND dla formantu, który zawiera.  
  
 Aby to osiągnąć, dostawcy głównego fragmentu dla paska pomocniczego ujawnia zestaw elementów podrzędnych reprezentujący pasma. Każdego pasma ma jednego dostawcę, który może narazić właściwości i wzorce. W jego implementacja obiektu <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>, dostawca poza pasmem zwraca domyślny dostawca okna dla kontrolki HWND, który uzyskuje się przez wywołanie metody <xref:System.Windows.Automation.Provider.AutomationInteropProvider.HostProviderFromHandle%2A>, przekazując uchwyt okna formantu. Na koniec implementuje dostawcy głównego fragmentu dla paska pomocniczego <xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride> interfejsu, a w jego implementacja obiektu <xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride.GetOverrideProviderForHwnd%2A> zwraca dostawcę odpowiednie poza pasmem dla formantu zawartego w określonym HWND.  
  
## <a name="see-also"></a>Zobacz także
- [Przegląd dostawców automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [Udostępnianie dostawcy automatyzacji interfejsu użytkownika po stronie serwera](../../../docs/framework/ui-automation/expose-a-server-side-ui-automation-provider.md)
- [Zwracanie właściwości od dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/return-properties-from-a-ui-automation-provider.md)
- [Wywoływanie zdarzeń od dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/raise-events-from-a-ui-automation-provider.md)
- [Włączanie nawigacji w dostawcy fragmentu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/enable-navigation-in-a-ui-automation-fragment-provider.md)
- [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
