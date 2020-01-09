---
title: Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera
ms.date: 03/30/2017
helpviewer_keywords:
- server-side UI Automation provider implementation
- UI Automation, server-side provider implementation
- provider implementation, UI Automation
ms.assetid: 6acc6d08-bd67-4e2e-915c-9c1d34eb86fe
ms.openlocfilehash: 25f22d5e8caacc69643f6d79e109ebaa94159d80
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75632319"
---
# <a name="server-side-ui-automation-provider-implementation"></a>Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera

> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).

W tej sekcji opisano sposób implementacji dostawcy automatyzacji interfejsu użytkownika po stronie serwera dla kontrolki niestandardowej.

Implementacja elementów Windows Presentation Foundation (WPF) i elementów innych niż WPF (takich jak te zaprojektowane dla [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]) różni się zasadniczo. Elementy WPF zapewniają obsługę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] za pośrednictwem klasy pochodnej z <xref:System.Windows.Automation.Peers.AutomationPeer>. Elementy inne niż WPF zapewniają obsługę za pomocą implementacji interfejsów dostawcy.

<a name="Security_Considerations"></a>

## <a name="security-considerations"></a>Zagadnienia dotyczące zabezpieczeń

Należy napisać dostawców, aby mogły one działać w środowisku częściowego zaufania. Ponieważ UIAutomationClient. dll nie jest skonfigurowany do uruchamiania w ramach częściowej relacji zaufania, kod dostawcy nie powinien odwoływać się do tego zestawu. W takim przypadku kod może działać w środowisku z pełnym zaufaniem, ale kończy się niepowodzeniem w środowisku częściowego zaufania.

W szczególności nie należy używać pól z klas w UIAutomationClient. dll, takich jak te w <xref:System.Windows.Automation.AutomationElement>. Zamiast tego należy użyć odpowiednich pól z klas w UIAutomationTypes. dll, takich jak <xref:System.Windows.Automation.AutomationElementIdentifiers>.

<a name="Provider_Implementation_by_WPF_Elements"></a>

## <a name="provider-implementation-by-windows-presentation-foundation-elements"></a>Implementacja dostawcy przez Windows Presentation Foundation elementy

Aby uzyskać więcej informacji na temat tego tematu, zobacz [Automatyzacja interfejsu użytkownika dla kontrolki NIESTANDARDOWEJ WPF](../wpf/controls/ui-automation-of-a-wpf-custom-control.md).

<a name="Provider_Implementation_by_non_WPF_Elements"></a>

## <a name="provider-implementation-by-non-wpf-elements"></a>Implementacja dostawcy przez elementy inne niż WPF

Niestandardowe kontrolki, które nie są częścią platformy WPF Framework, ale są zapisywane w kodzie zarządzanym (najczęściej są to [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] kontrolki), zapewniają obsługę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] przez implementację interfejsów. Każdy element musi implementować co najmniej jeden interfejs wymieniony w pierwszej tabeli w następnej sekcji. Ponadto, jeśli element obsługuje jeden lub więcej wzorców kontrolek, musi zaimplementować odpowiedni interfejs dla każdego wzorca kontroli.

Projekt dostawcy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] musi odwoływać się do następujących zestawów:

- UIAutomationProviders.dll

- UIAutomationTypes.dll

- WindowsBase.dll

<a name="Provider_Interfaces"></a>

### <a name="provider-interfaces"></a>Interfejsy dostawcy

Każdy dostawca [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] musi zaimplementować jeden z następujących interfejsów.

|Interfejs|Opis|
|---------------|-----------------|
|<xref:System.Windows.Automation.Provider.IRawElementProviderSimple>|Oferuje funkcje prostej kontrolki hostowanej w oknie, w tym obsługę wzorców i właściwości formantów.|
|<xref:System.Windows.Automation.Provider.IRawElementProviderFragment>|Dziedziczy po <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>. Dodaje funkcje dla elementu w kontrolce złożonej, w tym nawigację w obrębie fragmentu, ustawienie fokusu i zwrócenie obwiedni elementu.|
|<xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>|Dziedziczy po <xref:System.Windows.Automation.Provider.IRawElementProviderFragment>. Dodaje funkcje dla elementu głównego w kontrolce złożonej, w tym lokalizowanie elementu podrzędnego w określonych współrzędnych i Ustawianie stanu fokusu dla całej kontrolki.|

Poniższe interfejsy oferują dodane funkcje, ale nie są wymagane do wdrożenia.

|Interfejs|Opis|
|---------------|-----------------|
|<xref:System.Windows.Automation.Provider.IRawElementProviderAdviseEvents>|Umożliwia dostawcy śledzenie żądań zdarzeń.|
|<xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride>|Umożliwia zmianę położenia elementów opartych na oknach w drzewie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] fragmentu.|

Wszystkie inne interfejsy w przestrzeni nazw <xref:System.Windows.Automation.Provider> są przeznaczone do obsługi wzorców kontrolek.

<a name="Requirements_for_Non_WPF_Providers"></a>

### <a name="requirements-for-non-wpf-providers"></a>Wymagania dla dostawców nienależących do platformy WPF

Aby można było komunikować się z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], formant musi implementować następujące główne obszary funkcjonalności:

|Funkcja|Implementacja|
|-------------------|--------------------|
|Uwidacznianie dostawcy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|W odpowiedzi na WM_GETOBJECT komunikat wysyłany do okna sterowania zwracają obiekt implementujący <xref:System.Windows.Automation.Provider.IRawElementProviderSimple> (lub interfejs pochodny). Dla fragmentów, musi to być dostawca dla katalogu głównego fragmentów.|
|Podaj wartości właściwości|Zaimplementuj <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPropertyValue%2A>, aby podać lub zastąpić wartości.|
|Zezwalaj klientowi na współpracującie z kontrolką|Implementuj interfejsy obsługujące wzorce kontrolki, takie jak <xref:System.Windows.Automation.Provider.IInvokeProvider>. Zwróć tych dostawców wzorców w implementacji <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A>.|
|Zgłoś zdarzenia|Wywołaj jedną z metod statycznych <xref:System.Windows.Automation.Provider.AutomationInteropProvider>, aby zgłosić zdarzenie, dla którego klient może nasłuchiwać.|
|Włączanie nawigacji i skoncentrowanie się na fragmentach|Zaimplementuj <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> dla każdego elementu w fragmencie. (Niepotrzebne dla elementów, które nie są częścią fragmentu).|
|Włącz skoncentrowanie i lokalizację elementu podrzędnego w fragmencie|Zaimplementuj <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>. (Niepotrzebne dla elementów, które nie mają fragmentów głównych).|

<a name="Property_Values_in_Non_WPF_Providers"></a>

### <a name="property-values-in-non-wpf-providers"></a>Wartości właściwości w dostawcach spoza WPF

dostawcy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dla formantów niestandardowych muszą obsługiwać pewne właściwości, które mogą być używane przez system automatyzacji, a także przez aplikacje klienckie. W przypadku elementów, które są hostowane w systemie Windows (HWND), [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] może pobrać niektóre właściwości z domyślnego dostawcy okien, ale muszą uzyskać innych od dostawcy niestandardowego.

Dostawcy formantów opartych na HWND nie muszą zazwyczaj podawać następujących właściwości (identyfikowanych przez wartości pól):

- <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>

- <xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>

- <xref:System.Windows.Automation.AutomationElementIdentifiers.ProcessIdProperty>

- <xref:System.Windows.Automation.AutomationElementIdentifiers.ClassNameProperty>

- <xref:System.Windows.Automation.AutomationElementIdentifiers.HasKeyboardFocusProperty>

- <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>

- <xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>

- <xref:System.Windows.Automation.AutomationElementIdentifiers.IsPasswordProperty>

- <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>

- <xref:System.Windows.Automation.AutomationElementIdentifiers.RuntimeIdProperty>

> [!NOTE]
> W oknie zostanie uzyskana <xref:System.Windows.Automation.AutomationElementIdentifiers.RuntimeIdProperty> prostego elementu lub głównego fragmentu hostowanego w oknie; jednak elementy fragmentów poniżej elementu głównego (takie jak elementy listy w polu listy) muszą podawać własne identyfikatory. Aby uzyskać więcej informacji, zobacz temat <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.GetRuntimeId%2A>.
>
> <xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty> powinna zostać zwrócona dla dostawców hostowanych w kontrolce [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]. W takim przypadku domyślny dostawca okna może nie być w stanie pobrać poprawnej wartości.
>
> <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> jest zwykle dostarczany przez dostawcę hosta. Na przykład, Jeśli kontrolka niestandardowa jest pochodną <xref:System.Windows.Forms.Control>, nazwa pochodzi od właściwości `Text` formantu.

Na przykład kod, zobacz [zwracają właściwości z dostawcy automatyzacji interfejsu użytkownika](return-properties-from-a-ui-automation-provider.md).

<a name="Events_in_Non_WPF_Providers"></a>

### <a name="events-in-non-wpf-providers"></a>Zdarzenia w dostawcach innych niż WPF

dostawcy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] powinni zgłaszać zdarzenia w celu powiadomienia aplikacji klienckich o zmianach w stanie interfejsu użytkownika. Następujące metody są używane do wywoływania zdarzeń.

|Metoda|Opis|
|------------|-----------------|
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseAutomationEvent%2A>|Wywołuje różne zdarzenia, w tym zdarzenia wyzwalane przez wzorce kontrolek.|
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseAutomationPropertyChangedEvent%2A>|Wywołuje zdarzenie po zmianie właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseStructureChangedEvent%2A>|Podnosi zdarzenie po zmianie struktury drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]; na przykład przez usunięcie lub dodanie elementu.|

Celem zdarzenia jest powiadomienie klienta o jakimś miejscu w [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], niezależnie od tego, czy działanie jest wyzwalane przez sam system [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Na przykład zdarzenie identyfikowane przez <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent> powinno być wywoływane za każdym razem, gdy kontrolka jest wywoływana, przez bezpośrednie dane wejściowe użytkownika lub przez wywoływanie <xref:System.Windows.Automation.InvokePattern.Invoke%2A>przez aplikację kliencką.

Aby zoptymalizować wydajność, dostawca może wybiórczo zgłaszać zdarzenia lub nie zgłaszać żadnych zdarzeń, jeśli żadna aplikacja kliencka nie zostanie zarejestrowana. Następujące metody są używane do optymalizacji.

|Metoda|Opis|
|------------|-----------------|
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A>|Ta właściwość statyczna określa, czy wszystkie aplikacje klienckie subskrybują zdarzenia [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|
|<xref:System.Windows.Automation.Provider.IRawElementProviderAdviseEvents>|Implementacja tego interfejsu w ramach dostawcy w katalogu głównym fragmentów umożliwia jego doradzanie, gdy klienci rejestrują i wyrejestrowujeją programy obsługi zdarzeń dla zdarzeń w fragmencie.|

<a name="Non_WPF_Provider_Navigation"></a>

### <a name="non-wpf-provider-navigation"></a>Nawigacja dostawcy spoza WPF

Dostawcy formantów prostych, takich jak niestandardowy przycisk hostowany w oknie (HWND), nie muszą obsługiwać nawigowania w drzewie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Nawigacja do i z elementu jest obsługiwana przez domyślnego dostawcę okna hosta, który jest określony w implementacji <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>. W przypadku zaimplementowania dostawcy dla złożonej kontrolki niestandardowej, należy jednak obsługiwać nawigację między węzłem głównym fragmentu i jego elementami podrzędnymi oraz między węzłami elementów równorzędnych.

> [!NOTE]
> Elementy fragmentu innego niż główny muszą zwracać `null` odwołanie z <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>, ponieważ nie są one bezpośrednio hostowane w oknie, a żaden dostawca domyślny nie może obsługiwać nawigowania do i z nich.

Struktura fragmentu jest określana przez implementację <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A>. Dla każdego możliwego kierunku z każdego fragmentu ta metoda zwraca obiekt dostawcy dla elementu w tym kierunku. Jeśli w tym kierunku nie ma elementu, metoda zwraca odwołanie `null`.

Element główny fragmentu obsługuje nawigację tylko do elementów podrzędnych. Na przykład pole listy zwraca pierwszy element na liście, gdy kierunek jest <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild>, a ostatni element, gdy kierunek jest <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>. Element główny fragmentu nie obsługuje nawigacji do elementów nadrzędnych ani równorzędnych; jest to obsługiwane przez dostawcę okna hosta.

Elementy fragmentu, który nie jest elementem głównym, muszą obsługiwać nawigację do elementu nadrzędnego oraz do wszelkich elementów równorzędnych i ich elementów podrzędnych.

<a name="Non_WPF_Provider_Reparenting"></a>

### <a name="non-wpf-provider-reparenting"></a>Obiekt nadrzędny dostawcy spoza platformy WPF

Okna podręczne są w rzeczywistości oknami najwyższego poziomu, a więc domyślnie pojawiają się w drzewie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jako elementy podrzędne pulpitu. W wielu przypadkach okna podręczne są jednak logicznie elementami podrzędnymi innej kontrolki. Na przykład lista rozwijana pola kombi jest logicznie elementem podrzędnym pola kombi. Analogicznie, okno podręczne menu jest logicznie elementem podrzędnym menu. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zapewnia pomoc techniczną do ponownego nadrzędnych okien wyskakujących, tak aby były one elementami podrzędnymi powiązanej kontrolki.

Aby zmienić nadrzędny okna podręcznego:

1. Utwórz dostawcę dla okna podręcznego. Wymaga to, aby Klasa okna podręcznego była znana z góry.

2. Zaimplementuj wszystkie właściwości i wzorce w zwykły sposób dla tego okna podręcznego, tak jakby były one kontrolką we własnym zakresie.

3. Zaimplementuj Właściwość <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A> tak, aby zwracała wartość uzyskaną z <xref:System.Windows.Automation.Provider.AutomationInteropProvider.HostProviderFromHandle%2A>, gdzie parametr jest dojściem okna podręcznego.

4. Zaimplementuj <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> dla okna podręcznego i jego elementu nadrzędnego, aby Nawigacja była prawidłowo obsługiwana z logicznego elementu nadrzędnego do logicznych elementów podrzędnych i między równorzędnymi elementami podrzędnymi.

Gdy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pojawia się okno podręczne, rozpoznaje, że nawigacja jest zastępowana domyślnie, i pomija okno podręczne, gdy zostanie napotkane jako element podrzędny pulpitu. Zamiast tego węzeł będzie dostępny tylko za pomocą fragmentu.

Obiekt nadrzędny nie jest odpowiedni dla przypadków, gdy kontrolka może obsługiwać okno dowolnej klasy. Na przykład paska pomocniczego może hostować dowolny typ HWND w swoich pasmach. Aby obsłużyć te przypadki, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsługuje alternatywną formę relokacji elementu HWND, zgodnie z opisem w następnej sekcji.

<a name="Non_WPF_Provider_Repositioning"></a>

### <a name="non-wpf-provider-repositioning"></a>Zmiana położenia dostawcy spoza WPF

fragmenty [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mogą zawierać co najmniej dwa elementy, które są zawarte w oknie (HWND). Ponieważ każdy HWND ma własnego domyślnego dostawcę, który uważa, że właściwość HWND ma być elementem podrzędnym zawierającej HWND, drzewo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] domyślnie pokaże HWND w fragmencie jako elementy podrzędne okna nadrzędnego. W większości przypadków jest to pożądane zachowanie, ale czasami może prowadzić do pomyłki, ponieważ nie pasuje do struktury logicznej [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].

Dobrym przykładem jest formant paska pomocniczego. Paska pomocniczego zawiera pasma, z których każdy może z kolei zawierać kontrolkę opartą na elemencie HWND, taką jak pasek narzędzi, pole edycji lub pole kombi. Domyślny dostawca okna dla paska pomocniczego HWND widzi kontrolki przedziału jako elementy podrzędne, a dostawca paska pomocniczego widzi paski jako elementy podrzędne. Ze względu na to, że dostawca HWND i dostawca paska pomocniczego działają wspólnie i łącząc ich elementy podrzędne, zarówno te, jak i kontrolki oparte na elemencie HWND, są wyświetlane jako elementy podrzędne paska pomocniczego. Logicznie jednak tylko paski powinny być wyświetlane jako elementy podrzędne paska pomocniczego, a każdy dostawca pasm powinien być połączony z domyślnym dostawcą HWND dla kontrolki, która zawiera.

Aby to osiągnąć, główny dostawca fragmentów dla paska pomocniczego uwidacznia zestaw elementów podrzędnych reprezentujących pasma. Każda grupa ma jednego dostawcę, który może uwidaczniać właściwości i wzorce. W jego implementacji <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>dostawca pasma zwraca domyślnego dostawcę okna dla elementu HWND formantu, który uzyskuje, wywołując <xref:System.Windows.Automation.Provider.AutomationInteropProvider.HostProviderFromHandle%2A>, przekazując w uchwyt okna kontrolki. Na koniec główny dostawca fragmentów dla paska pomocniczego implementuje interfejs <xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride>, a w jego implementacji <xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride.GetOverrideProviderForHwnd%2A> zwraca odpowiedniego dostawcę pasma dla kontrolki zawartej w określonym elemencie HWND.

## <a name="see-also"></a>Zobacz także

- [Przegląd dostawców automatyzacji interfejsu użytkownika](ui-automation-providers-overview.md)
- [Udostępnianie dostawcy automatyzacji interfejsu użytkownika po stronie serwera](expose-a-server-side-ui-automation-provider.md)
- [Zwracanie właściwości od dostawcy automatyzacji interfejsu użytkownika](return-properties-from-a-ui-automation-provider.md)
- [Wywoływanie zdarzeń od dostawcy automatyzacji interfejsu użytkownika](raise-events-from-a-ui-automation-provider.md)
- [Włączanie nawigacji w dostawcy fragmentu automatyzacji interfejsu użytkownika](enable-navigation-in-a-ui-automation-fragment-provider.md)
- [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
