---
title: Przegląd Nawigacja
description: Dowiedz się więcej o obsłudze nawigacyjnej w stylu przeglądarki używanym w aplikacjach autonomicznych i aplikacjach przeglądarki XAML w Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- loose XAML files [WPF]
- windows [WPF]
- Start page [WPF]
- HTML files [WPF]
- structured navigation [WPF]
- fragment navigation [WPF]
- URIs (Uniform Resource Identifiers)
- custom objects [WPF]
- Uniform Resource Identifiers (URIs)
- pages [WPF]
- frames [WPF]
- navigation hosts [WPF]
- journals [WPF]
- lifetimes [WPF]
- retaining content state [WPF]
- content state [WPF]
- programmatic navigation [WPF]
- hyperlinks [WPF]
ms.assetid: 86ad2143-606a-4e34-bf7e-51a2594248b8
ms.openlocfilehash: 2aac1b3a38b6240bfba1b90983fd9cbd18b31b6f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621707"
---
# <a name="navigation-overview"></a>Przegląd Nawigacja

Windows Presentation Foundation (WPF) obsługuje nawigację w stylu przeglądarki, która może być używana w dwóch typach aplikacji: Aplikacje autonomiczne i aplikacje przeglądarki XAML (XBAP). Aby spakować zawartość dla nawigacji, WPF udostępnia <xref:System.Windows.Controls.Page> klasę. Można przechodzić z jednego <xref:System.Windows.Controls.Page> do drugiego, korzystając z <xref:System.Windows.Documents.Hyperlink> , lub programowo, przy użyciu <xref:System.Windows.Navigation.NavigationService> . WPF używa dziennika do zapamiętania stron, które zostały przestawione i aby przejść z powrotem do nich.

<xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.Hyperlink> , <xref:System.Windows.Navigation.NavigationService> , i arkusz stanowi rdzeń wsparcia nawigacji oferowanego przez WPF. To omówienie zawiera szczegółowe informacje o tych funkcjach przed zaawansowaną obsługą nawigacji, która obejmuje nawigację do luźnych [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] plików, plików HTML i obiektów.

> [!NOTE]
> W tym temacie termin "Browser" dotyczy tylko przeglądarek, które mogą hostować aplikacje WPF, które obecnie obejmują programy Microsoft Internet Explorer i Firefox. W przypadku, gdy konkretne funkcje WPF są obsługiwane tylko przez określoną przeglądarkę, wersja przeglądarki jest nazywana.

## <a name="navigation-in-wpf-applications"></a>Nawigacja w aplikacjach WPF

Ten temat zawiera omówienie możliwości nawigacji kluczy w WPF. Te funkcje są dostępne zarówno dla aplikacji autonomicznych, jak i XBAP, chociaż w tym temacie przedstawiono je w kontekście programu XBAP.

> [!NOTE]
> W tym temacie omówiono sposób kompilowania i wdrażania aplikacji XBAP. Aby uzyskać więcej informacji na temat aplikacji XBAP, zobacz [Omówienie platformy WPF XAML przeglądarki](wpf-xaml-browser-applications-overview.md).

W tej części opisano i przedstawiono następujące aspekty nawigacji:

- [Implementowanie strony](#CreatingAXAMLPage)

- [Konfigurowanie strony początkowej](#Configuring_a_Start_Page)

- [Konfigurowanie tytułu, szerokości i wysokości okna hosta](#ConfiguringAXAMLPage)

- [Nawigacja hiperlinków](#NavigatingBetweenXAMLPages)

- [Nawigacja fragmentów](#FragmentNavigation)

- [Usługa nawigacji](#NavigationService)

- [Nawigacja programowa przy użyciu usługi nawigacji](#Programmatic_Navigation_with_the_Navigation_Service)

- [Okres istnienia nawigacji](#Navigation_Lifetime)

- [Zapamiętywanie nawigacji przy użyciu dziennika](#NavigationHistory)

- [Okres istnienia strony i dziennik](#PageLifetime)

- [Zachowywanie stanu zawartości przy użyciu historii nawigacji](#RetainingContentStateWithNavigationHistory)

- [Plik cookie](#Cookies)

- [Nawigacja strukturalna](#Structured_Navigation)

<a name="CreatingAXAMLPage"></a>

### <a name="implementing-a-page"></a>Implementowanie strony

W programie WPF można przechodzić do kilku typów zawartości, które obejmują .NET Framework obiektów, obiektów niestandardowych, wartości wyliczenia, kontrolek użytkownika, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plików i plików HTML. Należy jednak się przekonać, że najpopularniejszym i wygodnym sposobem spakowania zawartości jest użycie <xref:System.Windows.Controls.Page> . Ponadto <xref:System.Windows.Controls.Page> wdraża funkcje specyficzne dla nawigacji, aby zwiększyć ich wygląd i uprościć programowanie.

Korzystając z programu <xref:System.Windows.Controls.Page> , można deklaratywnie zaimplementować stronę nawigacji [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zawartości przy użyciu oznaczeń takich jak następujące.

[!code-xaml[NavigationOverviewSnippets#Page1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page1.xaml#page1xaml)]

Obiekt <xref:System.Windows.Controls.Page> , który jest zaimplementowany w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczniku, ma `Page` jako element główny i wymaga deklaracji przestrzeni nazw XML WPF. `Page`Element zawiera zawartość, do której chcesz przejść i wyświetlić. Zawartość można dodać `Page.Content` , ustawiając element właściwości, jak pokazano w poniższej tabeli.

[!code-xaml[NavigationOverviewSnippets#Page2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page2.xaml#page2xaml)]

`Page.Content`może zawierać tylko jeden element podrzędny; w poprzednim przykładzie zawartość jest pojedynczym ciągiem "Hello, Page!" W tym przypadku zwykle jest używana kontrolka układu jako element podrzędny (zobacz [Układ](../advanced/layout.md)), aby zawierać i redagować zawartość.

Elementy podrzędne `Page` elementu są uważane za zawartość a <xref:System.Windows.Controls.Page> i, w związku z tym, nie trzeba używać jawnej `Page.Content` deklaracji. Następujący znacznik jest deklaratywną równoważną z poprzednim przykładem.

[!code-xaml[NavigationOverviewSnippets#Page3XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page3.xaml#page3xaml)]

W tym przypadku `Page.Content` jest automatycznie ustawiany z elementami podrzędnymi `Page` elementu. Aby uzyskać więcej informacji, zobacz artykuł [model zawartości WPF](../controls/wpf-content-model.md).

Tylko znaczników <xref:System.Windows.Controls.Page> jest przydatne do wyświetlania zawartości. <xref:System.Windows.Controls.Page>Można jednak również wyświetlić kontrolki, które umożliwiają użytkownikom interakcję ze stroną i mogą reagować na interakcję użytkownika przez obsługę zdarzeń i wywoływanie logiki aplikacji. Interaktywny <xref:System.Windows.Controls.Page> jest implementowany przy użyciu kombinacji znaczników i kodu, jak pokazano w poniższym przykładzie.

[!code-xaml[XBAPAppDefSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml#homepagemarkup)]

[!code-csharp[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml.cs#homepagecodebehind)]
[!code-vb[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/HomePage.xaml.vb#homepagecodebehind)]

Aby umożliwić współdziałanie pliku znaczników i pliku związanego z kodem, wymagana jest następująca konfiguracja:

- W znaczniku `Page` element musi zawierać `x:Class` atrybut. Po skompilowaniu aplikacji istnienie `x:Class` w pliku znaczników powoduje, że program Microsoft Build Engine (MSBuild) tworzy `partial` klasę, która pochodzi od <xref:System.Windows.Controls.Page> i ma nazwę, która jest określona przez `x:Class` atrybut. Wymaga to dodania deklaracji przestrzeni nazw XML dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schematu ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ). Wygenerowana `partial` Klasa implementuje `InitializeComponent` , która jest wywoływana, aby zarejestrować zdarzenia i ustawić właściwości zaimplementowane w znaczniku.

- W kodzie, Klasa musi być `partial` klasą o tej samej nazwie, która jest określona przez `x:Class` atrybut w znaczniku i musi pochodzić od <xref:System.Windows.Controls.Page> . Pozwala to skojarzyć plik związany z kodem z `partial` klasą wygenerowaną dla pliku znaczników podczas kompilowania aplikacji (zobacz [Kompilowanie aplikacji WPF](building-a-wpf-application-wpf.md)).

- W kodzie, <xref:System.Windows.Controls.Page> Klasa musi implementować konstruktora, który wywołuje `InitializeComponent` metodę. `InitializeComponent`jest implementowana przez wygenerowaną klasę pliku znaczników `partial` do rejestrowania zdarzeń i ustawiania właściwości, które są zdefiniowane w znaczniku.

> [!NOTE]
> Po dodaniu nowego elementu <xref:System.Windows.Controls.Page> do projektu przy użyciu programu Visual Studio, <xref:System.Windows.Controls.Page> jest zaimplementowany przy użyciu znaczników i kodu, i zawiera konfigurację niezbędną do utworzenia skojarzenia między plikami znaczników i kodu, zgodnie z opisem w tym miejscu.

Gdy masz, możesz <xref:System.Windows.Controls.Page> przejść do tego elementu. Aby określić pierwszy, <xref:System.Windows.Controls.Page> do którego aplikacji nawiguje, należy skonfigurować przycisk Uruchom <xref:System.Windows.Controls.Page> .

<a name="Configuring_a_Start_Page"></a>

### <a name="configuring-a-start-page"></a>Konfigurowanie strony początkowej

Aplikacje XBAP wymagają, aby pewna ilość infrastruktury aplikacji była hostowana w przeglądarce. W WPF <xref:System.Windows.Application> Klasa jest częścią definicji aplikacji, która ustanawia wymaganą infrastrukturę aplikacji (zobacz [Omówienie zarządzania aplikacjami](application-management-overview.md)).

Definicja aplikacji jest zwykle implementowana przy użyciu znaczników i kodu, z plikiem znaczników skonfigurowanym jako `ApplicationDefinition` element MSBuild. Poniżej znajduje się definicja aplikacji dla programu XBAP.

[!code-xaml[XBAPAppDefSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

[!code-csharp[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml.cs#xbapapplicationdefinitioncodebehind)]
[!code-vb[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/Application.xaml.vb#xbapapplicationdefinitioncodebehind)]

Aplikacja XBAP może używać jej definicji aplikacji do określenia uruchomienia <xref:System.Windows.Controls.Page> , który jest <xref:System.Windows.Controls.Page> automatycznie ładowany podczas uruchamiania aplikacji XBAP. W tym celu należy ustawić <xref:System.Windows.Application.StartupUri%2A> Właściwość z identyfikatorem URI (Uniform Resource Identifier) <xref:System.Windows.Controls.Page> .

> [!NOTE]
> W większości przypadków <xref:System.Windows.Controls.Page> jest to skompilowane lub wdrożone w aplikacji. W takich przypadkach identyfikator URI, który identyfikuje a, <xref:System.Windows.Controls.Page> jest identyfikatorem URI pakietu, który jest identyfikatorem URI, który jest zgodny ze schematem *pakietu* . Identyfikatory URI pakietów są bardziej omówione w identyfikatorach [URI pakietów w WPF](pack-uris-in-wpf.md). Możesz również przejść do zawartości przy użyciu schematu http, który został omówiony poniżej.

Można ustawić <xref:System.Windows.Application.StartupUri%2A> deklaratywnie w znacznikach, jak pokazano w poniższym przykładzie.

[!code-xaml[NavigationOverviewSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

W tym przykładzie `StartupUri` atrybut jest ustawiony z względnym identyfikatorem URI, który identyfikuje stronę główna. XAML. Gdy program XBAP zostanie uruchomiony, Strona główna. XAML jest automatycznie przechodzenia do i wyświetlana. Jest to pokazane na poniższym rysunku, który pokazuje aplikację XBAP uruchomioną z serwera sieci Web.

![Strona XBAP](./media/navigation-overview/xbap-launched-from-a-web-server.png "Spowoduje to wyświetlenie aplikacji XBAP uruchomionej z serwera sieci Web.")

> [!NOTE]
> Aby uzyskać więcej informacji na temat opracowywania i wdrażania aplikacji XBAP, zobacz [Omówienie aplikacji przeglądarek XAML w języku WPF](wpf-xaml-browser-applications-overview.md) i [wdrażanie programu WPF](deploying-a-wpf-application-wpf.md).

<a name="ConfiguringAXAMLPage"></a>

### <a name="configuring-the-host-windows-title-width-and-height"></a>Konfigurowanie tytułu, szerokości i wysokości okna hosta

Jednym z nich może być zauważono od poprzedniego rysunku, że tytuł przeglądarki i panelu karty jest identyfikatorem URI dla aplikacji XBAP. Poza tym, tytuł nie jest atrakcyjny ani informacyjny. Z tego powodu <xref:System.Windows.Controls.Page> oferuje sposób zmiany tytułu przez ustawienie <xref:System.Windows.Controls.Page.WindowTitle%2A> właściwości. Ponadto można skonfigurować szerokość i wysokość okna przeglądarki przez ustawienie <xref:System.Windows.Controls.Page.WindowWidth%2A> i <xref:System.Windows.Controls.Page.WindowHeight%2A> , odpowiednio.

<xref:System.Windows.Controls.Page.WindowTitle%2A>, <xref:System.Windows.Controls.Page.WindowWidth%2A> i <xref:System.Windows.Controls.Page.WindowHeight%2A> można ustawić deklaratywnie w znacznikach, jak pokazano w poniższym przykładzie.

[!code-xaml[NavigationOverviewSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/HomePage.xaml#homepagemarkup)]

Wyniki są pokazane na poniższym rysunku.

![Tytuł okna, wysokość, Szerokość](./media/navigation-overview/window-title-width-height.png "Spowoduje to wyświetlenie tytułu, wysokości i szerokości okna, które można skonfigurować.")

<a name="NavigatingBetweenXAMLPages"></a>

### <a name="hyperlink-navigation"></a>Nawigacja hiperlinków

Typowy obiekt XBAP zawiera kilka stron. Najprostszym sposobem przejścia z jednej strony do innej jest użycie <xref:System.Windows.Documents.Hyperlink> . Można deklaratywnie dodać <xref:System.Windows.Documents.Hyperlink> do a za <xref:System.Windows.Controls.Page> pomocą `Hyperlink` elementu, który jest pokazywany w poniższej tabeli.

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

`Hyperlink`Element wymaga następujących elementów:

- Identyfikator URI pakietu <xref:System.Windows.Controls.Page> do przechodzenia do, określony przez `NavigateUri` atrybut.

- Zawartość, którą użytkownik może kliknąć, aby zainicjować nawigację, na przykład tekst i obrazy (dla zawartości, którą `Hyperlink` może zawierać element, zobacz <xref:System.Windows.Documents.Hyperlink> ).

Na poniższej ilustracji przedstawiono aplikację XBAP z systemem <xref:System.Windows.Controls.Page> , który ma <xref:System.Windows.Documents.Hyperlink> .

![Strona z hiperłączem](./media/navigation-overview/xbap-with-a-page-with-a-hyperlink.png "Spowoduje to wyświetlenie aplikacji XBAP ze stroną z hiperłączem.")

Zgodnie z oczekiwaniami, kliknięcie powoduje, <xref:System.Windows.Documents.Hyperlink> że aplikacje XBAP przejdą do elementu <xref:System.Windows.Controls.Page> , który jest identyfikowany przez `NavigateUri` atrybut. Ponadto XBAP dodaje wpis dla poprzedniego elementu <xref:System.Windows.Controls.Page> do listy ostatnich stron w programie Internet Explorer. Jest to pokazane na poniższej ilustracji.

![Przyciski Wstecz i dalej](./media/navigation-overview/back-and-forward-navigation.png "Przejdź do przycisków Wstecz i do przodu.")

Również obsługa nawigacji z jednego <xref:System.Windows.Controls.Page> do drugiego, który <xref:System.Windows.Documents.Hyperlink> obsługuje nawigację fragmentów.

<a name="FragmentNavigation"></a>

### <a name="fragment-navigation"></a>Nawigacja fragmentów

*Nawigacja fragmentów* to Nawigacja do fragmentu zawartości w bieżącej <xref:System.Windows.Controls.Page> lub innej <xref:System.Windows.Controls.Page> . W WPF fragment zawartości to zawartość, która jest zawarta w nazwanym elemencie. Nazwany element to element, który ma `Name` ustawiony atrybut. Poniższe znaczniki pokazują nazwany `TextBlock` element, który zawiera fragment zawartości.

[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup2)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup3)]

Aby <xref:System.Windows.Documents.Hyperlink> można było przejść do fragmentu zawartości, `NavigateUri` atrybut musi zawierać następujące elementy:

- Identyfikator URI elementu <xref:System.Windows.Controls.Page> z fragmentem zawartości, do którego chcesz przejść.

- Znak "#".

- Nazwa elementu w elemencie <xref:System.Windows.Controls.Page> , który zawiera fragment zawartości.

Identyfikator URI fragmentu ma następujący format.

*PageURI* `#` *ElementName*

Poniżej przedstawiono przykład `Hyperlink` , który jest skonfigurowany do przechodzenia do fragmentu zawartości.

[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml1)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml2)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml3)]

> [!NOTE]
> W tej sekcji opisano domyślną implementację nawigacji fragmentów w programie WPF. WPF umożliwia również wdrożenie własnego schematu nawigacji fragmentu, który w części wymaga obsługi <xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType> zdarzenia.

> [!IMPORTANT]
> Można przechodzić do fragmentów na luźnych [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stronach (pliki tylko do znaczników [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] `Page` jako element główny) tylko wtedy, gdy strony można przeglądać za pośrednictwem protokołu HTTP.
>
> Jednak luźna [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strona może przechodzić do własnych fragmentów.

<a name="NavigationService"></a>

### <a name="navigation-service"></a>Usługa nawigacji

<xref:System.Windows.Documents.Hyperlink>Pozwala użytkownikowi na zainicjowanie nawigacji do konkretnej <xref:System.Windows.Controls.Page> , pracy lokalizowania i pobierania strony jest wykonywana przez <xref:System.Windows.Navigation.NavigationService> klasę. Zasadniczo <xref:System.Windows.Navigation.NavigationService> zapewnia możliwość przetwarzania żądania nawigacji w imieniu kodu klienta, takiego jak <xref:System.Windows.Documents.Hyperlink> . Ponadto <xref:System.Windows.Navigation.NavigationService> implementuje obsługę wyższego poziomu na potrzeby śledzenia i wpływania na żądanie nawigacji.

Gdy <xref:System.Windows.Documents.Hyperlink> jest kliknięty, program WPF wywołuje, <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> Aby zlokalizować i pobrać <xref:System.Windows.Controls.Page> przy użyciu określonego identyfikatora URI pakietu. Pobrane <xref:System.Windows.Controls.Page> zostało przekonwertowane na drzewo obiektów, których obiektem głównym jest wystąpienie pobrane <xref:System.Windows.Controls.Page> . Odwołanie do <xref:System.Windows.Controls.Page> obiektu głównego jest przechowywane we <xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType> właściwości. Identyfikator URI pakietu dla zawartości, do której został przeszedł, jest przechowywany we <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> właściwości, podczas gdy <xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType> przechowuje identyfikator URI pakietu dla ostatniej strony, do której przeszedł.

> [!NOTE]
> Istnieje możliwość, że aplikacja WPF ma więcej niż jeden obecnie aktywny <xref:System.Windows.Navigation.NavigationService> . Aby uzyskać więcej informacji, zobacz [hosty nawigacji](#Navigation_Hosts) w dalszej części tego tematu.

<a name="Programmatic_Navigation_with_the_Navigation_Service"></a>

### <a name="programmatic-navigation-with-the-navigation-service"></a>Nawigacja programowa przy użyciu usługi nawigacji

Nie musisz wiedzieć o tym <xref:System.Windows.Navigation.NavigationService> , czy nawigacja jest implementowana w znakach przy użyciu <xref:System.Windows.Documents.Hyperlink> , ponieważ <xref:System.Windows.Documents.Hyperlink> używa w <xref:System.Windows.Navigation.NavigationService> Twoim imieniu. Oznacza to, że pod warunkiem, że bezpośredni lub pośredni element nadrzędny obiektu <xref:System.Windows.Documents.Hyperlink> jest hostem nawigacyjnym (zobacz [hosty nawigacji](#Navigation_Hosts)), <xref:System.Windows.Documents.Hyperlink> będzie w stanie znaleźć i użyć usługi nawigacji hosta nawigacji, aby przetworzyć żądanie nawigacji.

Istnieją jednak sytuacje, w których należy bezpośrednio korzystać z <xref:System.Windows.Navigation.NavigationService> programu, w tym następujące:

- Gdy konieczne jest utworzenie wystąpienia <xref:System.Windows.Controls.Page> przy użyciu konstruktora bez parametrów.

- Gdy musisz ustawić właściwości <xref:System.Windows.Controls.Page> przed przechodzeniem do niego.

- Gdy to <xref:System.Windows.Controls.Page> , do którego należy przejść, można określić tylko w czasie wykonywania.

W takich sytuacjach należy napisać kod, aby programowo zainicjować nawigację przez wywołanie <xref:System.Windows.Navigation.NavigationService.Navigate%2A> metody <xref:System.Windows.Navigation.NavigationService> obiektu. Wymagające pobrania odwołania do <xref:System.Windows.Navigation.NavigationService> .

#### <a name="getting-a-reference-to-the-navigationservice"></a>Pobieranie odwołania do NavigationService

Ze względu na to, które są omówione w sekcji [hosty nawigacji](#Navigation_Hosts) , aplikacja WPF może mieć więcej niż jeden element <xref:System.Windows.Navigation.NavigationService> . Oznacza to, że kod wymaga metody znalezienia a <xref:System.Windows.Navigation.NavigationService> , która zwykle <xref:System.Windows.Navigation.NavigationService> przeszedł do bieżącego <xref:System.Windows.Controls.Page> . Możesz uzyskać odwołanie do a <xref:System.Windows.Navigation.NavigationService> przez wywołanie `static` <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A?displayProperty=nameWithType> metody. Aby uzyskać ten, <xref:System.Windows.Navigation.NavigationService> który przeszedł do określonego <xref:System.Windows.Controls.Page> , przekazujesz odwołanie do obiektu <xref:System.Windows.Controls.Page> jako argument <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A> metody. Poniższy kod pokazuje, jak uzyskać <xref:System.Windows.Navigation.NavigationService> dla bieżącego <xref:System.Windows.Controls.Page> .

[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPage.xaml.vb#getnscodebehind2)]

Jako skrót do znajdowania <xref:System.Windows.Navigation.NavigationService> dla a <xref:System.Windows.Controls.Page> , <xref:System.Windows.Controls.Page> implementuje <xref:System.Windows.Controls.Page.NavigationService%2A> Właściwość. Pokazano to w poniższym przykładzie.

[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPageShortCut.xaml.vb#getnsshortcutcodebehind2)]

> [!NOTE]
> Element a <xref:System.Windows.Controls.Page> może uzyskać odwołanie do niego tylko <xref:System.Windows.Navigation.NavigationService> wtedy <xref:System.Windows.Controls.Page> , gdy wywołuje <xref:System.Windows.FrameworkElement.Loaded> zdarzenie.

#### <a name="programmatic-navigation-to-a-page-object"></a>Programistyczne nawigowanie do obiektu strony

Poniższy przykład pokazuje, jak używać <xref:System.Windows.Navigation.NavigationService> do programistycznego nawigowania do <xref:System.Windows.Controls.Page> . Nawigacja programowa jest wymagana, ponieważ element <xref:System.Windows.Controls.Page> , do którego jest przeznaczony do przechodzenia, można utworzyć wystąpienie tylko przy użyciu jednego konstruktora bez parametrów. <xref:System.Windows.Controls.Page>Za pomocą konstruktora bez parametrów jest pokazywany w następujących znakach i kodzie.

[!code-xaml[NavigationOverviewSnippets#PageWithNonDefaultConstructorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml#pagewithnondefaultconstructorxaml)]

[!code-csharp[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml.cs#pagewithnondefaultconstructorcodebehind)]
[!code-vb[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithNonDefaultConstructor.xaml.vb#pagewithnondefaultconstructorcodebehind)]

<xref:System.Windows.Controls.Page>Powoduje to przejście do obiektu <xref:System.Windows.Controls.Page> z konstruktorem bez parametrów, który jest wyświetlany w następujących znakach i kodzie.

[!code-xaml[NavigationOverviewSnippets#NSNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml#nsnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml.cs#nsnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSNavigationPage.xaml.vb#nsnavigationpagecodebehind)]

Po <xref:System.Windows.Documents.Hyperlink> kliknięciu na tej stronie <xref:System.Windows.Controls.Page> Nawigacja jest inicjowana przez utworzenie wystąpienia elementu, <xref:System.Windows.Controls.Page> Aby przejść do użycia konstruktora bez parametrów i wywołania <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> metody. <xref:System.Windows.Navigation.NavigationService.Navigate%2A>akceptuje odwołanie do obiektu, <xref:System.Windows.Navigation.NavigationService> do którego będzie nawigować, a nie URI pakietu.

#### <a name="programmatic-navigation-with-a-pack-uri"></a>Nawigacja programowa przy użyciu identyfikatora URI pakietu

Jeśli konieczne jest programistyczne konstruowanie identyfikatora URI pakietu (Jeśli na przykład można określić tylko identyfikator URI pakietu w czasie wykonywania), można użyć <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> metody. Pokazano to w poniższym przykładzie.

[!code-xaml[NavigationOverviewSnippets#NSUriNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml#nsurinavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml.cs#nsurinavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSUriNavigationPage.xaml.vb#nsurinavigationpagecodebehind)]

#### <a name="refreshing-the-current-page"></a>Odświeżanie bieżącej strony

<xref:System.Windows.Controls.Page>Nie jest pobierana, jeśli ma ten sam identyfikator URI pakietu, co identyfikator URI pakietu, który jest przechowywany we <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> właściwości. Aby wymusić ponowne pobranie bieżącej strony przez program WPF, można wywołać <xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType> metodę, jak pokazano w poniższym przykładzie.

[!code-xaml[NavigationOverviewSnippets#NSRefreshNavigationPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml#nsrefreshnavigationpagexaml1)]

[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind1)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind2)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind2)]

<a name="Navigation_Lifetime"></a>

### <a name="navigation-lifetime"></a>Okres istnienia nawigacji

Istnieje wiele sposobów na zainicjowanie nawigacji, jak widać. Po zainicjowaniu nawigacji, gdy nawigacja jest w toku, można śledzić i wpływać na nawigację przy użyciu następujących zdarzeń, które są implementowane przez <xref:System.Windows.Navigation.NavigationService> :

- <xref:System.Windows.Navigation.NavigationService.Navigating>. Występuje po zażądaniu nowej nawigacji. Może służyć do anulowania nawigacji.

- <xref:System.Windows.Navigation.NavigationService.NavigationProgress>. Występuje okresowo podczas pobierania, aby zapewnić informacje o postępie nawigacji.

- <xref:System.Windows.Navigation.NavigationService.Navigated>. Występuje, gdy strona została umieszczona i pobrana.

- <xref:System.Windows.Navigation.NavigationService.NavigationStopped>. Występuje, gdy Nawigacja zostanie zatrzymana (przez wywołanie <xref:System.Windows.Navigation.NavigationService.StopLoading%2A> ) lub gdy żąda się nowej nawigacji, gdy trwa bieżące nawigowanie.

- <xref:System.Windows.Navigation.NavigationService.NavigationFailed>. Występuje, gdy wystąpi błąd podczas przechodzenia do wymaganej zawartości.

- <xref:System.Windows.Navigation.NavigationService.LoadCompleted>. Występuje, gdy zawartość, do której została przetworzona, została załadowana i przeanalizowana, i rozpoczęto renderowanie.

- <xref:System.Windows.Navigation.NavigationService.FragmentNavigation>. Występuje po rozpoczęciu nawigacji do fragmentu zawartości, co następuje:

  - Natychmiast, jeśli żądany fragment znajduje się w bieżącej zawartości.

  - Po załadowaniu zawartości źródłowej, jeśli żądany fragment znajduje się w innej zawartości.

Zdarzenia nawigacji są zgłaszane w kolejności zilustrowanej na poniższej ilustracji.

![Wykres przepływu nawigacji na stronie](./media/navigation-overview/order-of-navigation-events.png "Wykres przepływu zdarzeń nawigacji na stronie")

Ogólnie rzecz biorąc, <xref:System.Windows.Controls.Page> nie dotyczy tych zdarzeń. Jest to bardziej możliwe, że aplikacja jest objęta nimi, a z tego powodu te zdarzenia są również zgłaszane przez <xref:System.Windows.Application> klasę:

- <xref:System.Windows.Application.Navigating?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationProgress?displayProperty=nameWithType>

- <xref:System.Windows.Application.Navigated?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationFailed?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationStopped?displayProperty=nameWithType>

- <xref:System.Windows.Application.LoadCompleted?displayProperty=nameWithType>

- <xref:System.Windows.Application.FragmentNavigation?displayProperty=nameWithType>

Za każdym razem <xref:System.Windows.Navigation.NavigationService> , gdy wywołuje zdarzenie, <xref:System.Windows.Application> Klasa wywołuje odpowiednie zdarzenie. <xref:System.Windows.Controls.Frame>i <xref:System.Windows.Navigation.NavigationWindow> oferują te same zdarzenia w celu wykrywania nawigacji w obrębie odpowiednich zakresów.

W niektórych przypadkach <xref:System.Windows.Controls.Page> może zainteresować te zdarzenia. Na przykład <xref:System.Windows.Controls.Page> może obsłużyć <xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType> zdarzenie, aby określić, czy anulować nawigację od samego siebie. Pokazano to w poniższym przykładzie.

[!code-xaml[NavigationOverviewSnippets#CancelNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml#cancelnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml.cs#cancelnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/CancelNavigationPage.xaml.vb#cancelnavigationpagecodebehind)]

Jeśli zarejestrowano procedurę obsługi ze zdarzeniem nawigacji z <xref:System.Windows.Controls.Page> , jak w poprzednim przykładzie, należy również wyrejestrować procedurę obsługi zdarzeń. Jeśli tego nie zrobisz, mogą wystąpić skutki uboczne w odniesieniu do tego, jak nawigacja WPF zapamiętuje <xref:System.Windows.Controls.Page> nawigację przy użyciu dziennika.

<a name="NavigationHistory"></a>

### <a name="remembering-navigation-with-the-journal"></a>Zapamiętywanie nawigacji przy użyciu dziennika

WPF używa dwóch stosów do zapamiętania stron, z których pochodzą: stos zaplecza i stos do przodu. Po przejściu z bieżącego <xref:System.Windows.Controls.Page> do nowego lub do <xref:System.Windows.Controls.Page> istniejącego elementu <xref:System.Windows.Controls.Page> , bieżąca <xref:System.Windows.Controls.Page> jest dodawana do *stosu back*. Po przejściu z bieżącego z <xref:System.Windows.Controls.Page> powrotem do poprzedniego <xref:System.Windows.Controls.Page> , bieżąca wartość <xref:System.Windows.Controls.Page> jest dodawana do *stosu do przodu*. Stos zaplecza, stos przesyłania dalej i funkcje do zarządzania nimi są określane zbiorczo jako dziennik. Każdy element w stosie zaplecza i stos do przodu jest wystąpieniem <xref:System.Windows.Navigation.JournalEntry> klasy i jest określany jako *wpis w dzienniku*.

#### <a name="navigating-the-journal-from-internet-explorer"></a>Nawigowanie po dzienniku z programu Internet Explorer

Koncepcyjnie dziennik działa tak samo, jak przyciski **Wstecz** i **dalej** w programie Internet Explorer. Są one pokazane na poniższej ilustracji.

![Przyciski Wstecz i dalej](./media/navigation-overview/back-and-forward-navigation.png "Przejdź do przycisków Wstecz i do przodu.")

W przypadku aplikacji XBAP hostowanych przez program Internet Explorer WPF integruje się z arkuszem nawigacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] programu Internet Explorer. Dzięki temu użytkownicy mogą nawigować do stron w aplikacji XBAP przy użyciu przycisków **Wstecz**, **do przodu**i **ostatnich stron** w programie Internet Explorer.

> [!IMPORTANT]
> W programie Internet Explorer, gdy użytkownik nawiguje z powrotem do aplikacji XBAP, tylko wpisy dziennika dla stron, które nie były aktywne, są przechowywane w dzienniku. Aby poznać dyskusję na temat utrzymywania stron, zobacz [okres istnienia strony i dziennik](#PageLifetime) w dalszej części tego tematu.

Domyślnie tekst dla każdego elementu <xref:System.Windows.Controls.Page> , który pojawia się na liście **ostatnich stron** programu Internet Explorer jest identyfikatorem URI dla <xref:System.Windows.Controls.Page> . W wielu przypadkach nie jest to szczególnie istotne dla użytkownika. Na szczęście można zmienić tekst przy użyciu jednej z następujących opcji:

1. Dołączona `JournalEntry.Name` wartość atrybutu.

2. `Page.Title`Wartość atrybutu.

3. `Page.WindowTitle`Wartość atrybutu i identyfikator URI dla bieżącego <xref:System.Windows.Controls.Page> .

4. Identyfikator URI dla bieżącego <xref:System.Windows.Controls.Page> . (Domyślnie)

Kolejność, w jakiej są wyświetlane opcje, jest zgodna z kolejnością pierwszeństwa podczas wyszukiwania tekstu. Na przykład, jeśli `JournalEntry.Name` jest ustawiona, inne wartości są ignorowane.

Poniższy przykład używa atrybutu, `Page.Title` Aby zmienić tekst wyświetlany dla wpisu dziennika.

[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup2)]

[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind1)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind2)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind2)]

#### <a name="navigating-the-journal-using-wpf"></a>Nawigowanie po arkuszu przy użyciu WPF

Mimo że użytkownik może nawigować po arkuszu przy użyciu stron z **tyłu**, **do przodu**i **ostatnich** w programie Internet Explorer, można także nawigować po dzienniku przy użyciu mechanizmów deklaratywnych i programistycznych zapewnianych przez WPF. Jednym z powodów, aby to zrobić, jest udostępnienie na stronach niestandardowych interfejsów użytkownika nawigacyjnych.

Obsługę nawigacji w dzienniku można deklaratywnie dodać przy użyciu poleceń nawigacyjnych uwidocznionych przez program <xref:System.Windows.Input.NavigationCommands> . Poniższy przykład ilustruje sposób użycia `BrowseBack` polecenia nawigacji.

[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml1)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml2)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml3)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML4](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml4)]

Można programistycznie nawigować po arkuszu przy użyciu jednego z następujących elementów członkowskich <xref:System.Windows.Navigation.NavigationService> klasy:

- <xref:System.Windows.Navigation.NavigationService.GoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.GoForward%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoForward%2A>

Dziennik może być również manipulowany programowo, zgodnie z opisem w sekcji [zachowywanie stanu zawartości przy użyciu historii nawigacji](#RetainingContentStateWithNavigationHistory) w dalszej części tego tematu.

<a name="PageLifetime"></a>

### <a name="page-lifetime-and-the-journal"></a>Okres istnienia strony i dziennik

Rozważ użycie aplikacji XBAP z kilkoma stronami zawierającymi zawartość rozbudowaną, w tym grafiki, animacje i multimedia. Użycie pamięci dla stron takich jak takie może być bardzo duże, szczególnie w przypadku używania nośnika wideo i audio. Mając na względzie, że strony, do których przeprowadzili przechodzenie do stron, takie aplikacje XBAP mogą szybko wykorzystać znaczną i zauważalną ilość pamięci.

Z tego powodu domyślne zachowanie dziennika polega na zarejestrowaniu <xref:System.Windows.Controls.Page> metadanych w każdym wpisie dziennika, a nie w odwołaniu do <xref:System.Windows.Controls.Page> obiektu. Po przejściu do wpisu dziennika, jego <xref:System.Windows.Controls.Page> metadane są używane do tworzenia nowego wystąpienia określonego <xref:System.Windows.Controls.Page> . W związku z tym każdy, <xref:System.Windows.Controls.Page> który jest przestawiony, ma okres istnienia opisany na poniższej ilustracji.

![Okres istnienia strony](./media/navigation-overview/navigated-page-lifetime.png "Pokazuje okres istnienia strony.")

Chociaż korzystanie z domyślnego zachowania rejestrowania może zaoszczędzić przy zużyciu pamięci, wydajność renderowania na stronie może ulec zmniejszeniu. <xref:System.Windows.Controls.Page>ponowne wystąpienie może być czasochłonne, szczególnie jeśli ma dużą zawartość. Jeśli musisz zachować <xref:System.Windows.Controls.Page> wystąpienie w dzienniku, możesz narysować na dwie techniki. Najpierw można programistycznie nawigować do <xref:System.Windows.Controls.Page> obiektu przez wywołanie <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> metody.

Następnie można określić, że WPF zachowuje wystąpienie <xref:System.Windows.Controls.Page> w dzienniku, ustawiając <xref:System.Windows.Controls.Page.KeepAlive%2A> Właściwość na `true` (wartość domyślna to `false` ). Jak pokazano w poniższym przykładzie, można ustawić <xref:System.Windows.Controls.Page.KeepAlive%2A> deklaratywnie w znaczniku.

[!code-xaml[NavigationOverviewSnippets#KeepAlivePageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/KeepAlivePage.xaml#keepalivepagexaml)]

Okres istnienia aktywności jest bardzo <xref:System.Windows.Controls.Page> odmienny niż ten, który nie jest. Podczas pierwszego okresu <xref:System.Windows.Controls.Page> utrzymywania aktywności jest przechodzenie do, jest tworzone w taki sam sposób, jak to <xref:System.Windows.Controls.Page> , które nie jest aktywne. Jednak ponieważ wystąpienie <xref:System.Windows.Controls.Page> jest przechowywane w dzienniku, nigdy nie jest tworzone ponownie dla tak długo, jak pozostało w dzienniku. W związku z tym, jeśli <xref:System.Windows.Controls.Page> istnieje logika inicjalizacji, która musi być wywoływana za każdym razem <xref:System.Windows.Controls.Page> , gdy jest przenoszona do, należy przenieść ją z konstruktora do procedury obsługi <xref:System.Windows.FrameworkElement.Loaded> zdarzenia. Jak pokazano na poniższej ilustracji, <xref:System.Windows.FrameworkElement.Loaded> <xref:System.Windows.FrameworkElement.Unloaded> zdarzenia i nadal są wywoływane każdorazowo po <xref:System.Windows.Controls.Page> przejściu do i z, odpowiednio.

![Po podniesieniu ładowanych i niezaładowanych zdarzeń](./media/navigation-overview/loaded-and-unloaded-events.png "Załadowane i niezaładowane zdarzenia są wywoływane, gdy strona jest przenoszona do i z.")

Gdy <xref:System.Windows.Controls.Page> program nie jest aktywny, nie należy wykonywać żadnej z następujących czynności:

- Zapisz odwołanie do niego lub jego część.

- Zarejestruj procedury obsługi zdarzeń ze zdarzeniami, które nie zostały zaimplementowane przez ten program.

Wykonanie jednej z tych opcji spowoduje utworzenie odwołań, które wymuszają <xref:System.Windows.Controls.Page> zachowywanie w pamięci, nawet po jej usunięciu z dziennika.

Ogólnie rzecz biorąc, należy preferować domyślne zachowanie nieutrzymywania <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page> aktywności. Ma to jednak konsekwencje stanu omówione w następnej sekcji.

<a name="RetainingContentStateWithNavigationHistory"></a>

### <a name="retaining-content-state-with-navigation-history"></a>Zachowywanie stanu zawartości przy użyciu historii nawigacji

Jeśli element <xref:System.Windows.Controls.Page> nie jest aktywny i ma kontrolki, które zbierają dane od użytkownika, co się dzieje z danymi, gdy użytkownik nawiguje z powrotem od i do tyłu <xref:System.Windows.Controls.Page> ? W perspektywie środowiska użytkownika użytkownik powinien oczekiwać, że dane wprowadzone wcześniej. Niestety, ze względu na to, że nowe wystąpienie programu <xref:System.Windows.Controls.Page> jest tworzone przy użyciu poszczególnych nawigacji, formanty, w których zbierane są dane, są usuwane, a dane są tracone.

Na szczęście dziennik zapewnia obsługę zapamiętywania danych między <xref:System.Windows.Controls.Page> nawigacjami, w tym danych kontrolnych. W odniesieniu do każdego wpisu dziennika dla każdego <xref:System.Windows.Controls.Page> z nich pełni rolę kontenera tymczasowego dla skojarzonego <xref:System.Windows.Controls.Page> stanu. Poniższe kroki przedstawiają sposób użycia tej pomocy <xref:System.Windows.Controls.Page> w przypadku przejścia z:

1. Wpis dla bieżącego <xref:System.Windows.Controls.Page> zostanie dodany do dziennika.

2. Stan <xref:System.Windows.Controls.Page> jest przechowywany w pozycji dziennika dla tej strony, która jest dodawana do stosu back.

3. <xref:System.Windows.Controls.Page>Nastąpi przejście do nowego.

Po <xref:System.Windows.Controls.Page> przejściu do strony z powrotem do programu przy użyciu dziennika należy wykonać następujące czynności:

1. <xref:System.Windows.Controls.Page>Zostanie utworzone wystąpienie (górny wpis dziennika na stosie zaplecza).

2. <xref:System.Windows.Controls.Page>Jest odświeżany ze stanem, który został zapisany w pozycji dziennika dla <xref:System.Windows.Controls.Page> .

3. <xref:System.Windows.Controls.Page>Jest on przechodzenia z powrotem do.

WPF automatycznie używa tej obsługi, gdy są używane następujące kontrolki <xref:System.Windows.Controls.Page> :

- <xref:System.Windows.Controls.CheckBox>

- <xref:System.Windows.Controls.ComboBox>

- <xref:System.Windows.Controls.Expander>

- <xref:System.Windows.Controls.Frame>

- <xref:System.Windows.Controls.ListBox>

- <xref:System.Windows.Controls.ListBoxItem>

- <xref:System.Windows.Controls.MenuItem>

- <xref:System.Windows.Controls.ProgressBar>

- <xref:System.Windows.Controls.RadioButton>

- <xref:System.Windows.Controls.Slider>

- <xref:System.Windows.Controls.TabControl>

- <xref:System.Windows.Controls.TabItem>

- <xref:System.Windows.Controls.TextBox>

Jeśli <xref:System.Windows.Controls.Page> program używa tych kontrolek, dane wprowadzone do nich są zapamiętywane przez <xref:System.Windows.Controls.Page> nawigację, jak pokazano na poniższym rysunku **kolorze ulubionym** <xref:System.Windows.Controls.ListBox> .

![Strona z kontrolkami, które zapamiętają stan](./media/navigation-overview/data-remembered-across-page-navigations.png "Wprowadzone dane są zapamiętywane między nawigacjami stron.")

Gdy <xref:System.Windows.Controls.Page> ma kontrolki inne niż te znajdujące się na poprzedniej liście lub gdy stan jest przechowywany w obiektach niestandardowych, należy napisać kod, aby spowodować, że dziennik zostanie zapamiętany dla <xref:System.Windows.Controls.Page> nawigacji.

Jeśli musisz zapamiętać małe fragmenty stanu między <xref:System.Windows.Controls.Page> nawigacjami, możesz użyć właściwości zależności (zobacz <xref:System.Windows.DependencyProperty> ), które są skonfigurowane z <xref:System.Windows.FrameworkPropertyMetadata.Journal%2A?displayProperty=nameWithType> flagą metadanych.

Jeśli stan, który należy <xref:System.Windows.Controls.Page> pamiętać między nawigacjami, składa się z wielu fragmentów danych, może być mniej dużo czasochłonne, aby hermetyzować stan w jednej klasie i zaimplementować <xref:System.Windows.Navigation.IProvideCustomContentState> interfejs.

Jeśli chcesz nawigować przez różne stany jednego <xref:System.Windows.Controls.Page> , bez przechodzenia do <xref:System.Windows.Controls.Page> samego siebie, możesz użyć <xref:System.Windows.Navigation.IProvideCustomContentState> i <xref:System.Windows.Navigation.NavigationService.AddBackEntry%2A?displayProperty=nameWithType> .

<a name="Cookies"></a>

### <a name="cookies"></a>Pliki cookie

Innym sposobem, w jaki aplikacje WPF mogą przechowywać dane, są pliki cookie, które są tworzone, aktualizowane i usuwane przy <xref:System.Windows.Application.SetCookie%2A> użyciu <xref:System.Windows.Application.GetCookie%2A> metod i. Pliki cookie, które można tworzyć w WPF, są tymi samymi plikami cookie, które są używane przez inne typy aplikacji sieci Web; pliki cookie to dowolne fragmenty danych przechowywane przez aplikację na komputerze klienckim w trakcie lub między sesjami aplikacji. Dane plików cookie zazwyczaj przyjmuje postać pary nazwa/wartość w następującym formacie.

*Nazwa* `=` *Wartość*

Gdy dane są przesyłane do programu <xref:System.Windows.Application.SetCookie%2A> , wraz z <xref:System.Uri> lokalizacją, w której ma zostać ustawiony plik cookie, plik cookie jest tworzony w pamięci i jest dostępny tylko w czasie trwania bieżącej sesji aplikacji. Ten typ pliku cookie jest określany jako *plik cookie sesji*.

Aby przechowywać plik cookie między sesjami aplikacji, należy dodać do pliku cookie datę wygaśnięcia, używając następującego formatu.

*Nazwa* `=` *Wartość*`; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`

Plik cookie z datą wygaśnięcia jest przechowywany w folderze tymczasowych plików internetowych instalacji systemu Windows do momentu wygaśnięcia pliku cookie. Taki plik cookie jest znany jako *trwały plik cookie* , ponieważ utrzymuje się między sesjami aplikacji.

Można pobrać zarówno sesję, jak i trwałe pliki cookie <xref:System.Windows.Application.GetCookie%2A> , wywołując metodę, przekazując lokalizację, w <xref:System.Uri> której ustawiono plik cookie przy użyciu <xref:System.Windows.Application.SetCookie%2A> metody.

Poniżej przedstawiono niektóre sposoby obsługi plików cookie w programie WPF:

- Aplikacje autonomiczne WPF i XBAP mogą tworzyć pliki cookie i zarządzać nimi.

- Dostęp do plików cookie tworzonych przez aplikację XBAP można uzyskać z przeglądarki.

- Aplikacje XBAP z tej samej domeny mogą tworzyć i udostępniać pliki cookie.

- Aplikacje XBAP i strony HTML z tej samej domeny mogą tworzyć i udostępniać pliki cookie.

- Pliki cookie są wysyłane, gdy aplikacje XBAP i luźne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony tworzą żądania sieci Web.

- Zarówno aplikacje XBAP najwyższego poziomu, jak i aplikacje XBAP hostowane w elemencie IFRAME, mogą uzyskiwać dostęp do plików cookie.

- Obsługa plików cookie w programie WPF jest taka sama dla wszystkich obsługiwanych przeglądarek.

- W programie Internet Explorer Zasady P3P, które odnoszą się do plików cookie, są honorowane przez WPF, szczególnie w odniesieniu do aplikacji firmy Microsoft i innych firm.

<a name="Structured_Navigation"></a>

### <a name="structured-navigation"></a>Nawigacja strukturalna

Jeśli musisz przekazać dane z jednego <xref:System.Windows.Controls.Page> do drugiego, możesz przekazać dane jako argumenty do konstruktora bez parametrów <xref:System.Windows.Controls.Page> . Należy pamiętać, że w przypadku korzystania z tej techniki należy zachować <xref:System.Windows.Controls.Page> aktywność; Jeśli nie, przy następnym przejściu do elementu <xref:System.Windows.Controls.Page> , WPF ponownie tworzy wystąpienie przy <xref:System.Windows.Controls.Page> użyciu konstruktora bez parametrów.

Alternatywnie, <xref:System.Windows.Controls.Page> można zaimplementować właściwości, które są ustawione z danymi, które muszą zostać przesłane. Jednak rzeczy stają się trudne, gdy konieczne jest <xref:System.Windows.Controls.Page> przekazanie danych z powrotem do tego, który przeszedł <xref:System.Windows.Controls.Page> do niego. Problem polega na tym, że nawigacja nie wspiera natywnie mechanizmów do zagwarantowania, że <xref:System.Windows.Controls.Page> po przejściu z usługi zostanie zwrócona wartość. Zasadniczo nawigacja nie obsługuje semantyki wywołania/powrotu. Aby rozwiązać ten problem, WPF udostępnia <xref:System.Windows.Navigation.PageFunction%601> klasę, której można użyć, aby upewnić się, że element <xref:System.Windows.Controls.Page> jest zwracany do wartości w sposób przewidywalny i uporządkowany. Aby uzyskać więcej informacji, zobacz [Omówienie nawigacji strukturalnej](structured-navigation-overview.md).

<a name="The_NavigationWindow_Class"></a>

## <a name="the-navigationwindow-class"></a>Klasa NavigationWindow

Do tego momentu zobaczysz gamę usług nawigacyjnych, których najprawdopodobniej używasz do kompilowania aplikacji z nawigacją. Te usługi zostały omówione w kontekście aplikacji XBAP, chociaż nie są ograniczone do aplikacji XBAP. Nowoczesne systemy operacyjne i aplikacje systemu Windows wykorzystują korzystanie z przeglądarki nowoczesnych użytkowników w celu uwzględnienia nawigacji w stylu przeglądarki w aplikacjach autonomicznych. Typowe przykłady obejmują:

- **Tezaurus słów**: nawigowanie po wyborach w programie Word.

- **Eksplorator plików**: nawigowanie po plikach i folderach.

- **Kreatorzy**: dzielenie złożonego zadania na wiele stron, które mogą być przechodzenie między. Przykładem jest Kreator składników systemu Windows, który obsługuje dodawanie i usuwanie funkcji systemu Windows.

Aby włączyć nawigację w stylu przeglądarki do aplikacji autonomicznych, można użyć <xref:System.Windows.Navigation.NavigationWindow> klasy. <xref:System.Windows.Navigation.NavigationWindow>pochodzi z <xref:System.Windows.Window> i rozszerza je o te same wsparcie dla nawigacji, które zapewnia program XBAP. Możesz użyć <xref:System.Windows.Navigation.NavigationWindow> jako głównego okna aplikacji autonomicznej lub jako okna pomocniczego, takiego jak okno dialogowe.

Aby zaimplementować <xref:System.Windows.Navigation.NavigationWindow> , jak w przypadku większości klas najwyższego poziomu w WPF ( <xref:System.Windows.Window> , <xref:System.Windows.Controls.Page> , i tak dalej), należy użyć kombinacji znaczników i kodu. Pokazano to w poniższym przykładzie.

[!code-xaml[IntroToNavNavigationWindowSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml#navigationwindowmarkup)]

[!code-csharp[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml.cs#navigationwindowcodebehind)]
[!code-vb[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/MainWindow.xaml.vb#navigationwindowcodebehind)]

Ten kod tworzy <xref:System.Windows.Navigation.NavigationWindow> automatycznie nawigację do pliku <xref:System.Windows.Controls.Page> (Strona główna. XAML) po <xref:System.Windows.Navigation.NavigationWindow> otwarciu. Jeśli <xref:System.Windows.Navigation.NavigationWindow> jest głównym oknem aplikacji, można użyć `StartupUri` atrybutu, aby go uruchomić. Jest to pokazane w poniższej tabeli.

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchNavWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/App.xaml#applaunchnavwindow)]

Na poniższej ilustracji przedstawiono <xref:System.Windows.Navigation.NavigationWindow> Główne okno aplikacji autonomicznej.

![Okno główne](./media/navigation-overview/navigation-window-as-main-window.png "Okno nawigacji jako okno główne")

Na rysunku widać, że <xref:System.Windows.Navigation.NavigationWindow> ma tytuł, mimo że nie został on ustawiony w <xref:System.Windows.Navigation.NavigationWindow> kodzie implementacji z poprzedniego przykładu. Zamiast tego, tytuł jest ustawiany przy użyciu <xref:System.Windows.Controls.Page.WindowTitle%2A> właściwości, która jest pokazana w poniższym kodzie.

[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup1)]
[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup2)]

Ustawienie <xref:System.Windows.Controls.Page.WindowWidth%2A> właściwości i <xref:System.Windows.Controls.Page.WindowHeight%2A> ma także wpływ na <xref:System.Windows.Navigation.NavigationWindow> .

Zwykle należy wdrożyć własne, <xref:System.Windows.Navigation.NavigationWindow> gdy trzeba dostosować jego zachowanie lub jego wygląd. Jeśli nie wykonasz żadnego z tych czynności, możesz użyć skrótu. W przypadku określenia identyfikatora URI pakietu <xref:System.Windows.Controls.Page> jako <xref:System.Windows.Application.StartupUri%2A> w aplikacji autonomicznej program <xref:System.Windows.Application> automatycznie tworzy na <xref:System.Windows.Navigation.NavigationWindow> potrzeby hostowania <xref:System.Windows.Controls.Page> . Poniższe znaczniki pokazują, jak włączyć tę funkcję.

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchPage](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/AnotherApp.xaml#applaunchpage)]

Jeśli chcesz, aby okno aplikacji dodatkowej, takie jak okno dialogowe <xref:System.Windows.Navigation.NavigationWindow> , było, możesz użyć kodu w poniższym przykładzie, aby go otworzyć.

[!code-csharp[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/DialogOwnerWindow.xaml.cs#createnwdialogbox)]
[!code-vb[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/DialogOwnerWindow.xaml.vb#createnwdialogbox)]

Na poniższej ilustracji przedstawiono wynik.

![Okno dialogowe](./media/navigation-overview/navigation-window-as-dialog-box.png "Okno nawigacyjne jako okno dialogowe")

Jak widać, <xref:System.Windows.Navigation.NavigationWindow> Wyświetla przyciski **Wstecz** i **do przodu** w stylu programu Internet Explorer, które umożliwiają użytkownikom nawigowanie po arkuszu. Te przyciski zapewniają takie samo środowisko użytkownika, jak pokazano na poniższej ilustracji.

![Przyciski Wstecz i dalej w NavigationWindow](./media/navigation-overview/back-and-forward-buttons-in-navigation-window.png "Przyciski Wstecz i dalej w oknie nawigacji")

Jeśli strony zapewniają własną obsługę nawigacji w dzienniku i interfejs użytkownika, można ukryć przyciski **Wstecz** i **do przodu** wyświetlane przez <xref:System.Windows.Navigation.NavigationWindow> ustawienie wartości <xref:System.Windows.Navigation.NavigationWindow.ShowsNavigationUI%2A> właściwości na `false` .

Alternatywnie możesz użyć obsługi dostosowywania w WPF, aby zastąpić [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Navigation.NavigationWindow> siebie.

<a name="Frame_in_Standalone_Applications"></a>

## <a name="the-frame-class"></a>Klasa Frame

Przeglądarka i <xref:System.Windows.Navigation.NavigationWindow> system Windows obsługujący zawartość nawigacji. W niektórych przypadkach aplikacje mają zawartość, która nie musi być hostowana przez całe okno. Zamiast tego taka zawartość jest hostowana w innej zawartości. Możesz wstawić zawartość nawigacji do innej zawartości przy użyciu <xref:System.Windows.Controls.Frame> klasy. <xref:System.Windows.Controls.Frame>zapewnia taką samą obsługę jak <xref:System.Windows.Navigation.NavigationWindow> i aplikacje XBAP.

Poniższy przykład pokazuje, jak dodać a <xref:System.Windows.Controls.Frame> do <xref:System.Windows.Controls.Page> deklaratywnie przy użyciu `Frame` elementu.

[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml3)]

Ten znacznik ustawia `Source` atrybut `Frame` elementu z pakietem URI <xref:System.Windows.Controls.Page> , dla którego <xref:System.Windows.Controls.Frame> należy najpierw przejść do. Na poniższej ilustracji przedstawiono wystąpienie aplikacji XBAP z systemem, który <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Frame> przechodzi między kilka stron.

![Ramka, która przeszła między wieloma stronami](./media/navigation-overview/frame-navigation-between-multiple-pages.png "Spowoduje to wyświetlenie nawigacji między wieloma stronami.")

Nie musisz używać tylko <xref:System.Windows.Controls.Frame> wewnątrz zawartości <xref:System.Windows.Controls.Page> . Jest również często hostować <xref:System.Windows.Controls.Frame> wewnątrz zawartości <xref:System.Windows.Window> .

Domyślnie program <xref:System.Windows.Controls.Frame> używa tylko własnego dziennika w przypadku braku innego dziennika. Jeśli <xref:System.Windows.Controls.Frame> jest częścią zawartości, która jest hostowana wewnątrz <xref:System.Windows.Navigation.NavigationWindow> lub XBAP, <xref:System.Windows.Controls.Frame> używa dziennika, który należy do obiektu <xref:System.Windows.Navigation.NavigationWindow> lub XBAP. Czasami jednak <xref:System.Windows.Controls.Frame> może być odpowiedzialny za własny dziennik. Jedną z przyczyn tego problemu jest umożliwienie nawigowania w dziennikach na stronach, które są hostowane przez <xref:System.Windows.Controls.Frame> . Jest to zilustrowane na poniższej ilustracji.

![Diagram ramek i stron](./media/navigation-overview/journal-navigation-within-pages-hosted-by-a-frame.png "Spowoduje to wyświetlenie nawigacji w dzienniku na stronach hostowanych przez ramkę.")

W takim przypadku można skonfigurować <xref:System.Windows.Controls.Frame> do korzystania z własnego dziennika przez ustawienie <xref:System.Windows.Controls.Frame.JournalOwnership%2A> właściwości <xref:System.Windows.Controls.Frame> na <xref:System.Windows.Navigation.JournalOwnership.OwnsJournal> . Jest to pokazane w poniższej tabeli.

[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml3)]

Na poniższej ilustracji przedstawiono efekt nawigowania w obrębie <xref:System.Windows.Controls.Frame> , który używa własnego dziennika.

![Ramka, która używa własnego dziennika](./media/navigation-overview/frame-uses-its-own-journal.png "Przedstawia efekt nawigowania w obrębie ramki korzystającej z własnego dziennika.")

Należy zauważyć, że wpisy dziennika są wyświetlane przez nawigację [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w programie <xref:System.Windows.Controls.Frame> , a nie w programie Internet Explorer.

> [!NOTE]
> Jeśli element <xref:System.Windows.Controls.Frame> jest częścią zawartości, która jest hostowana w usłudze <xref:System.Windows.Window> , <xref:System.Windows.Controls.Frame> używa własnego dziennika i w związku z tym wyświetla własną nawigację [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] .

Jeśli środowisko użytkownika wymaga <xref:System.Windows.Controls.Frame> , aby zapewnić własny dziennik bez wyświetlania nawigacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , można ukryć nawigację, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ustawiając polecenie <xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A> na <xref:System.Windows.Visibility.Hidden> . Jest to pokazane w poniższej tabeli.

[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml3)]

<a name="Navigation_Hosts"></a>

## <a name="navigation-hosts"></a>Hosty nawigacji

<xref:System.Windows.Controls.Frame>i <xref:System.Windows.Navigation.NavigationWindow> są klasami, które są znane jako hosty nawigacji. *Host nawigacyjny* jest klasą, która może nawigować do zawartości i wyświetlać ją. W tym celu każdy host nawigacji używa własnych <xref:System.Windows.Navigation.NavigationService> i dzienników. Podstawowa konstrukcja hosta nawigacji jest pokazana na poniższej ilustracji.

![Diagramy nawigatora](./media/navigation-overview/navigation-host-construction.png "Podstawowa konstrukcja hosta nawigacji")

Zasadniczo umożliwia to <xref:System.Windows.Navigation.NavigationWindow> i <xref:System.Windows.Controls.Frame> zapewnia taką samą obsługę nawigacji, jaką środowisko XBAP zapewnia, gdy jest hostowana w przeglądarce.

Oprócz używania <xref:System.Windows.Navigation.NavigationService> i dziennika, hosty nawigacji implementują te same składowe, które <xref:System.Windows.Navigation.NavigationService> implementują. Jest to zilustrowane na poniższej ilustracji.

![Dziennik w ramce i w NavigationWindow](./media/navigation-overview/navigation-window-and-frame.png "Okno nawigacji i ramka")

Pozwala to na bezpośrednie przechodzenie do pomocy technicznej dotyczącej nawigacji. Można to wziąć pod uwagę, jeśli trzeba zapewnić niestandardową nawigację [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dla programu <xref:System.Windows.Controls.Frame> , która jest hostowana w <xref:System.Windows.Window> . Ponadto oba typy implementują dodatkowe elementy członkowskie powiązane z nawigacją, `BackStack` w tym ( <xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType> , <xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType> ) i `ForwardStack` ( <xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType> , <xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType> ), które umożliwiają Wyliczenie wpisów dziennika w stosie zaplecza i w stosie progresywnym.

Jak wspomniano wcześniej, w aplikacji może istnieć więcej niż jeden dziennik. Na poniższej ilustracji przedstawiono przykład, w którym może się to zdarzyć.

![Wiele dzienników w jednej aplikacji](./media/navigation-overview/multiple-journals-in-one-application.png "Jest to przykład dla więcej niż jednego dziennika w aplikacji.")

<a name="Navigating_to_Content_Other_than_Pages"></a>

## <a name="navigating-to-content-other-than-xaml-pages"></a>Przechodzenie do zawartości innej niż strony XAML

W tym temacie <xref:System.Windows.Controls.Page> i zostały użyte pakiety XBAP do zademonstrowania różnych możliwości nawigacyjnych platformy WPF. Jednak, <xref:System.Windows.Controls.Page> który jest kompilowany do aplikacji nie jest jedynym typem zawartości, do której można przejść, a pakiet XBAP nie jest jedynym sposobem identyfikacji zawartości.

Jak widać w tej sekcji, można także nawigować do luźnych [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plików, plików HTML i obiektów.

<a name="Navigating_to_Loose_XAML_Files"></a>

### <a name="navigating-to-loose-xaml-files"></a>Przechodzenie do luźnych plików XAML

Plik luźny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest plikiem o następujących cechach:

- Zawiera tylko [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (oznacza to, że nie jest to kod).

- Ma odpowiednią deklarację przestrzeni nazw.

- Ma rozszerzenie nazwy pliku. XAML.

Rozważmy na przykład następującą zawartość, która jest przechowywana jako luźny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plik, Person. XAML.

[!code-xaml[NavigationOverviewSnippets#LooseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Person.xaml#loosexaml)]

Po dwukrotnym kliknięciu pliku zostanie otwarta przeglądarka i zostanie wyświetlona zawartość. Jest to pokazane na poniższej ilustracji.

![Wyświetlanie zawartości w pliku Person. XAML](./media/navigation-overview/contents-of-person-xaml-file.png "Wyświetla zawartość pliku Person. XAML.")

Można wyświetlić luźny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plik z następujących:

- Witryna sieci Web na komputerze lokalnym, w intranecie lub w Internecie.

- Udział plików Universal Naming Convention (UNC).

- Dysk lokalny.

Luźny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plik można dodać do ulubionych przeglądarki lub jako stronę główną przeglądarki.

> [!NOTE]
> Aby uzyskać więcej informacji na temat publikowania i uruchamiania luźnych [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stron, zobacz [wdrażanie aplikacji WPF](deploying-a-wpf-application-wpf.md).

Ograniczenie odnoszące się do swobodnego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] polega na tym, że można hostować tylko zawartość, która jest bezpieczna do uruchamiania w częściowej relacji zaufania. Na przykład `Window` nie może być elementem głównym luźnego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku. Aby uzyskać więcej informacji, zobacz temat informacje o [zabezpieczeniach częściowej relacji zaufania WPF](../wpf-partial-trust-security.md).

<a name="Navigating_to_HTML_Files_Using_Frame"></a>

### <a name="navigating-to-html-files-by-using-frame"></a>Nawigowanie do plików HTML przy użyciu ramki

Jak można się spodziewać, możesz również przejść do kodu HTML. Wystarczy podać identyfikator URI, który używa schematu protokołu HTTP. Na przykład poniżej przedstawiono, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Controls.Frame> który przechodzi do strony html.

[!code-xaml[NavigationOverviewSnippets#FrameHtmlNavMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHTMLNavPage.xaml#framehtmlnavmarkup)]

Przechodzenie do HTML wymaga specjalnych uprawnień. Na przykład nie można nawigować po platformie XBAP działającej w piaskownicy zabezpieczeń strefa Internet częściowo Ufaj. Aby uzyskać więcej informacji, zobacz temat informacje o [zabezpieczeniach częściowej relacji zaufania WPF](../wpf-partial-trust-security.md).

<a name="Navigating_to_HTML_Files_Using_WebBrowser"></a>

### <a name="navigating-to-html-files-by-using-the-webbrowser-control"></a>Nawigowanie do plików HTML przy użyciu kontrolki WebBrowser

<xref:System.Windows.Controls.WebBrowser>Kontrolka obsługuje obsługę dokumentów HTML, nawigację i skrypt/współdziałanie kodu zarządzanego. Aby uzyskać szczegółowe informacje na temat <xref:System.Windows.Controls.WebBrowser> kontrolki, zobacz <xref:System.Windows.Controls.WebBrowser> .

Podobnie jak <xref:System.Windows.Controls.Frame> w przypadku nawigowania do języka HTML przy użyciu programu <xref:System.Windows.Controls.WebBrowser> wymagane są specjalne uprawnienia. Na przykład w aplikacji częściowo zaufanej można nawigować tylko do kodu HTML znajdującego się w lokalizacji źródłowej. Aby uzyskać więcej informacji, zobacz temat informacje o [zabezpieczeniach częściowej relacji zaufania WPF](../wpf-partial-trust-security.md).

<a name="Navigating_to_Objects"></a>

### <a name="navigating-to-custom-objects"></a>Nawigowanie do obiektów niestandardowych

Jeśli masz dane przechowywane jako obiekty niestandardowe, jednym ze sposobów wyświetlania tych danych jest utworzenie <xref:System.Windows.Controls.Page> zawartości z zawartością powiązaną z tymi obiektami (zobacz temat [powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)). Jeśli nie potrzebujesz nakładu na tworzenie całej strony tylko w celu wyświetlenia obiektów, możesz przejść bezpośrednio do nich.

Rozważmy `Person` klasę, która jest zaimplementowana w poniższym kodzie.

[!code-csharp[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/Person.cs#personclasscode)]
[!code-vb[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/Person.vb#personclasscode)]

Aby przejść do niego, należy wywołać <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A?displayProperty=nameWithType> metodę, jak pokazano w poniższym kodzie.

[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject1)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject2)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject3)]

[!code-csharp[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml.cs#pagethatnavstoobjectcodebehind)]
[!code-vb[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/HomePage.xaml.vb#pagethatnavstoobjectcodebehind)]

Na poniższej ilustracji przedstawiono wynik.

![Strona, która nawiguje do klasy](./media/navigation-overview/page-navigates-to-an-object.png "Jest to przykład strony, która nawiguje do obiektu.")

Na tym rysunku widać, że nie są wyświetlane żadne przydatne elementy. W rzeczywistości wyświetlana wartość jest wartością zwracaną `ToString` metody dla obiektu **osoby** ; domyślnie jest to jedyna wartość, która może być używana przez WPF do reprezentowania obiektu. Można zastąpić `ToString` metodę, aby zwrócić bardziej zrozumiałe informacje, chociaż nadal będzie to wartość ciągu. Jedną z technik, z których można skorzystać, wykorzystującą funkcje prezentacji WPF, jest użycie szablonu danych. Można zaimplementować szablon danych, który WPF może skojarzyć z obiektem określonego typu. Poniższy kod przedstawia szablon danych dla `Person` obiektu.

[!code-xaml[NavigateToObjectSnippets#DataTemplateMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/App.xaml#datatemplatemarkup)]

W tym miejscu szablon danych jest skojarzony z `Person` typem przy użyciu `x:Type` rozszerzenia znaczników w `DataType` atrybucie. Szablon danych następnie tworzy powiązania `TextBlock` elementów (zobacz <xref:System.Windows.Controls.TextBlock> ) z właściwościami `Person` klasy. Na poniższej ilustracji przedstawiono zaktualizowany wygląd `Person` obiektu.

![Przechodzenie do klasy, która ma szablon danych](./media/navigation-overview/navigating-to-a-class.png "Przechodzenie do klasy, która ma szablon danych.")

Zaletą tej techniki jest spójność, którą uzyskuje się dzięki możliwości ponownego użycia szablonu danych w celu spójnego wyświetlania obiektów w dowolnym miejscu w aplikacji.

Aby uzyskać więcej informacji na temat szablonów danych, zobacz [tworzenia szablonów danych — omówienie](../data/data-templating-overview.md).

<a name="Security"></a>

## <a name="security"></a>Zabezpieczenia

Obsługa nawigacji WPF umożliwia przechodzenie przez aplikacje XBAP do Internetu i umożliwia aplikacjom obsługiwanie zawartości innej firmy. Aby zapewnić ochronę zarówno aplikacji, jak i użytkowników przed szkodliwym zachowaniem, WPF oferuje różne [funkcje zabezpieczeń omówione w](../security-wpf.md) zabezpieczeniach i [częściowej relacji zaufania WPF](../wpf-partial-trust-security.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Application.SetCookie%2A>
- <xref:System.Windows.Application.GetCookie%2A>
- [Przegląd Zarządzanie aplikacjami](application-management-overview.md)
- [Pakuj URI w WPF](pack-uris-in-wpf.md)
- [Przegląd Strukturyzowana nawigacja](structured-navigation-overview.md)
- [Przegląd Topologia nawigacji](navigation-topologies-overview.md)
- [— Tematy porad](navigation-how-to-topics.md)
- [Wdrażanie aplikacji WPF](deploying-a-wpf-application-wpf.md)
