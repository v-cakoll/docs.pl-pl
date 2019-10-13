---
title: Przegląd nawigacji
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
ms.openlocfilehash: 874bc0b1b0ac38210569632dc3d21ed727ae26e4
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291644"
---
# <a name="navigation-overview"></a>Przegląd nawigacji

Windows Presentation Foundation (WPF) obsługuje nawigację w stylu przeglądarki, która może być używana w dwóch typach aplikacji: Aplikacje autonomiczne i [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]. Aby spakować zawartość na potrzeby nawigacji, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] udostępnia klasę <xref:System.Windows.Controls.Page>. Można przechodzić z jednego <xref:System.Windows.Controls.Page> do innego deklaratywnego, przy użyciu <xref:System.Windows.Documents.Hyperlink> lub programowo przy użyciu <xref:System.Windows.Navigation.NavigationService>. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] używa dziennika do zapamiętania stron, które zostały przechodzące z i aby przejść z powrotem do nich.

<xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Navigation.NavigationService>, a dziennik stanowi rdzeń obsługi nawigacji oferowany przez [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. To omówienie zawiera szczegółowe informacje o tych funkcjach przed zaawansowaną obsługą nawigacji, która obejmuje nawigację do luźnych plików [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], plików HTML i obiektów.

> [!NOTE]
> W tym temacie termin "Browser" dotyczy tylko przeglądarek, które mogą hostować aplikacje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], które obecnie obejmują programy Microsoft Internet Explorer i Firefox. W przypadku, gdy konkretne funkcje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] są obsługiwane tylko przez określoną przeglądarkę, wersja przeglądarki jest nazywana.

## <a name="navigation-in-wpf-applications"></a>Nawigacja w aplikacjach WPF

Ten temat zawiera omówienie możliwości nawigacji kluczy w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Te funkcje są dostępne zarówno dla aplikacji autonomicznych, jak i [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], chociaż w tym temacie przedstawiono je w kontekście [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].

> [!NOTE]
> W tym temacie omówiono sposób kompilowania i wdrażania [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Aby uzyskać więcej informacji na [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], zobacz [Omówienie aplikacji przeglądarki XAML języka WPF](wpf-xaml-browser-applications-overview.md).

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

- [Cookie](#Cookies)

- [Nawigacja strukturalna](#Structured_Navigation)

<a name="CreatingAXAMLPage"></a>

### <a name="implementing-a-page"></a>Implementowanie strony

W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] można przechodzić do kilku typów zawartości, które obejmują .NET Framework obiektów, obiektów niestandardowych, wartości wyliczenia, kontrolek użytkownika, plików [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i plików HTML. Można jednak wiedzieć, że najpopularniejszy i wygodny sposób pakowania zawartości jest przy użyciu <xref:System.Windows.Controls.Page>. Ponadto <xref:System.Windows.Controls.Page> implementuje funkcje dotyczące nawigacji, aby zwiększyć ich wygląd i uprościć programowanie.

Za pomocą <xref:System.Windows.Controls.Page> można deklaratywnie zaimplementować stronę nawigacji dla zawartości [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przy użyciu oznaczeń takich jak następujące.

[!code-xaml[NavigationOverviewSnippets#Page1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page1.xaml#page1xaml)]

@No__t-0, który jest implementowany w znacznikach [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ma `Page` jako element główny, i wymaga deklaracji przestrzeni nazw [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] @ no__t-4. Element `Page` zawiera zawartość, do której chcesz przejść i wyświetlić. Aby dodać zawartość, należy ustawić `Page.Content` elementu właściwości, jak pokazano w poniższej tabeli.

[!code-xaml[NavigationOverviewSnippets#Page2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page2.xaml#page2xaml)]

`Page.Content` może zawierać tylko jeden element podrzędny; w poprzednim przykładzie zawartość jest pojedynczym ciągiem "Hello, Page!" W tym przypadku zwykle jest używana kontrolka układu jako element podrzędny (zobacz [Układ](../advanced/layout.md)), aby zawierać i redagować zawartość.

Elementy podrzędne elementu `Page` są uważane za zawartość <xref:System.Windows.Controls.Page> i w związku z tym nie trzeba używać jawnej deklaracji `Page.Content`. Następujący znacznik jest deklaratywną równoważną z poprzednim przykładem.

[!code-xaml[NavigationOverviewSnippets#Page3XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page3.xaml#page3xaml)]

W takim przypadku `Page.Content` jest automatycznie ustawiana z elementami podrzędnymi elementu `Page`. Aby uzyskać więcej informacji, zobacz artykuł [model zawartości WPF](../controls/wpf-content-model.md).

@No__t tylko znaczników-0 jest przydatne do wyświetlania zawartości. Jednak <xref:System.Windows.Controls.Page> może również wyświetlać kontrolki, które umożliwiają użytkownikom interakcję ze stroną i mogą reagować na interakcję użytkownika przez obsługę zdarzeń i wywoływanie logiki aplikacji. Interaktywna <xref:System.Windows.Controls.Page> jest implementowana przy użyciu kombinacji znaczników i kodu, jak pokazano w poniższym przykładzie.

[!code-xaml[XBAPAppDefSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml#homepagemarkup)]

[!code-csharp[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml.cs#homepagecodebehind)]
[!code-vb[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/HomePage.xaml.vb#homepagecodebehind)]

Aby umożliwić współdziałanie pliku znaczników i pliku związanego z kodem, wymagana jest następująca konfiguracja:

- W znaczniku element `Page` musi zawierać atrybut `x:Class`. Po skompilowaniu aplikacji, istnienie `x:Class` w pliku znaczników powoduje utworzenie klasy `partial`, która pochodzi z <xref:System.Windows.Controls.Page> i ma nazwę określoną przez atrybut `x:Class`. Wymaga to dodania deklaracji przestrzeni nazw [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dla schematu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`). Wygenerowana Klasa `partial` implementuje `InitializeComponent`, który jest wywoływany, aby zarejestrować zdarzenia i ustawić właściwości zaimplementowane w znaczniku.

- W kodzie, Klasa musi być klasą `partial` o tej samej nazwie, która jest określona przez atrybut `x:Class` w znaczniku i musi pochodzić od <xref:System.Windows.Controls.Page>. Pozwala to skojarzyć plik związany z kodem z klasą `partial`, która jest generowana dla pliku znaczników podczas kompilowania aplikacji (zobacz [Kompilowanie aplikacji WPF](building-a-wpf-application-wpf.md)).

- W kodzie, Klasa <xref:System.Windows.Controls.Page> musi implementować konstruktora, który wywołuje metodę `InitializeComponent`. `InitializeComponent` jest implementowana przez wygenerowaną przez plik znaczników `partial` klasę, aby zarejestrować zdarzenia i ustawić właściwości zdefiniowane w znaczniku.

> [!NOTE]
> Po dodaniu nowego <xref:System.Windows.Controls.Page> do projektu przy użyciu [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], <xref:System.Windows.Controls.Page> jest implementowana przy użyciu zarówno znaczników, jak i kodu, i zawiera konfigurację niezbędną do utworzenia skojarzenia między plikami znaczników i kodu, zgodnie z opisem w tym miejscu.

Gdy masz <xref:System.Windows.Controls.Page>, możesz przejść do tego elementu. Aby określić pierwszy <xref:System.Windows.Controls.Page>, do którego prowadzi aplikacja, należy skonfigurować Start <xref:System.Windows.Controls.Page>.

<a name="Configuring_a_Start_Page"></a>

### <a name="configuring-a-start-page"></a>Konfigurowanie strony początkowej

[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] wymaga, aby pewna ilość infrastruktury aplikacji była hostowana w przeglądarce. W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Klasa <xref:System.Windows.Application> jest częścią definicji aplikacji, która ustanawia wymaganą infrastrukturę aplikacji (zobacz [Omówienie zarządzania aplikacjami](application-management-overview.md)).

Definicja aplikacji jest zwykle implementowana przy użyciu znaczników i kodu, z plikiem znaczników skonfigurowanym jako element MSBuild @ no__t-0. Poniżej znajduje się definicja aplikacji dla [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].

[!code-xaml[XBAPAppDefSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

[!code-csharp[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml.cs#xbapapplicationdefinitioncodebehind)]
[!code-vb[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/Application.xaml.vb#xbapapplicationdefinitioncodebehind)]

@No__t-0 może użyć swojej definicji aplikacji, aby określić początkową <xref:System.Windows.Controls.Page>, czyli <xref:System.Windows.Controls.Page>, która jest automatycznie ładowana podczas uruchamiania [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. W tym celu należy ustawić właściwość <xref:System.Windows.Application.StartupUri%2A> z [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] dla żądanego <xref:System.Windows.Controls.Page>.

> [!NOTE]
> W większości przypadków <xref:System.Windows.Controls.Page> jest kompilowane lub wdrażany przy użyciu aplikacji. W takich przypadkach [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], które identyfikują <xref:System.Windows.Controls.Page> to pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], który jest [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], który jest zgodny ze schematem *pakietu* . Pakiet [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] został dokładniej omówiony w identyfikatorach [URI pakietów w WPF](pack-uris-in-wpf.md). Możesz również przejść do zawartości przy użyciu schematu http, który został omówiony poniżej.

Można ustawić <xref:System.Windows.Application.StartupUri%2A> deklaratywnie w znacznikach, jak pokazano w poniższym przykładzie.

[!code-xaml[NavigationOverviewSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

W tym przykładzie atrybut `StartupUri` jest ustawiony z pakietem względnym [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], który identyfikuje stronę główna. XAML. Gdy [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] jest uruchomiona, Strona główna. XAML jest automatycznie przechodzenia do i wyświetlana. Jest to pokazane na poniższym rysunku, który pokazuje [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], który został uruchomiony z serwera sieci Web.

![Strona aplikacji XBAP](./media/navigation-overview/xbap-launched-from-a-web-server.png "pokazuje, że aplikacje XBAP są uruchamiane z serwera sieci Web.")

> [!NOTE]
> Aby uzyskać więcej informacji na temat opracowywania i wdrażania [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], zobacz [Omówienie aplikacji w przeglądarce WPF XAML](wpf-xaml-browser-applications-overview.md) i [wdrażanie aplikacji WPF](deploying-a-wpf-application-wpf.md).

<a name="ConfiguringAXAMLPage"></a>

### <a name="configuring-the-host-windows-title-width-and-height"></a>Konfigurowanie tytułu, szerokości i wysokości okna hosta

Jednym z nich może być zauważono od poprzedniego rysunku, że tytuł przeglądarki i panelu karty jest [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Poza tym, tytuł nie jest atrakcyjny ani informacyjny. Z tego powodu <xref:System.Windows.Controls.Page> oferuje sposób zmiany tytułu przez ustawienie właściwości <xref:System.Windows.Controls.Page.WindowTitle%2A>. Ponadto można skonfigurować szerokość i wysokość okna przeglądarki, ustawiając odpowiednio <xref:System.Windows.Controls.Page.WindowWidth%2A> i <xref:System.Windows.Controls.Page.WindowHeight%2A>.

<xref:System.Windows.Controls.Page.WindowTitle%2A>, <xref:System.Windows.Controls.Page.WindowWidth%2A> i <xref:System.Windows.Controls.Page.WindowHeight%2A> można ustawić deklaratywnie w znaczniku, jak pokazano w poniższym przykładzie.

[!code-xaml[NavigationOverviewSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/HomePage.xaml#homepagemarkup)]

Wyniki są pokazane na poniższym rysunku.

![Tytuł okna, Wysokość i szerokość —](./media/navigation-overview/window-title-width-height.png "Wyświetla tytuł, Wysokość i szerokość okna, które można skonfigurować.")

<a name="NavigatingBetweenXAMLPages"></a>

### <a name="hyperlink-navigation"></a>Nawigacja hiperlinków

Typowy [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] zawiera kilka stron. Najprostszym sposobem przejścia z jednej strony do innej jest użycie <xref:System.Windows.Documents.Hyperlink>. Można deklaratywnie dodać <xref:System.Windows.Documents.Hyperlink> do <xref:System.Windows.Controls.Page> przy użyciu elementu `Hyperlink`, który jest przedstawiony w poniższym znaczniku.

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

Element `Hyperlink` wymaga następujących elementów:

- Pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] z <xref:System.Windows.Controls.Page> do przechodzenia do, określony przez atrybut `NavigateUri`.

- Zawartość, którą użytkownik może kliknąć, aby zainicjować nawigację, na przykład tekst i obrazy (dla zawartości, którą może zawierać element `Hyperlink`, patrz <xref:System.Windows.Documents.Hyperlink>).

Na poniższej ilustracji przedstawiono [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] z <xref:System.Windows.Controls.Page>, który ma <xref:System.Windows.Documents.Hyperlink>.

![Strona z hiperłączem](./media/navigation-overview/xbap-with-a-page-with-a-hyperlink.png "przedstawia element XBAP ze stroną z hiperłączem.")

Zgodnie z oczekiwaniami, kliknięcie <xref:System.Windows.Documents.Hyperlink> powoduje, że [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], aby przejść do <xref:System.Windows.Controls.Page>, który jest identyfikowany przez atrybut `NavigateUri`. Ponadto [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] dodaje wpis dla poprzedniego <xref:System.Windows.Controls.Page> do listy ostatnich stron w programie Internet Explorer. Jest to pokazane na poniższej ilustracji.

![Przyciski Wstecz i dalej](./media/navigation-overview/back-and-forward-navigation.png "przejdą do przycisków Wstecz i do przodu.")

Ponadto obsługa nawigacji z jednego <xref:System.Windows.Controls.Page> do innego, <xref:System.Windows.Documents.Hyperlink> obsługuje również nawigację fragmentów.

<a name="FragmentNavigation"></a>

### <a name="fragment-navigation"></a>Nawigacja fragmentów

*Nawigacja fragmentów* to Nawigacja do fragmentu zawartości w bieżącym <xref:System.Windows.Controls.Page> lub innej <xref:System.Windows.Controls.Page>. W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fragment zawartości to zawartość, która jest zawarta w nazwanym elemencie. Nazwany element to element, który ma ustawiony atrybut `Name`. Poniższe znaczniki pokazują nazwany element `TextBlock`, który zawiera fragment zawartości.

[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup2)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup3)]

Aby <xref:System.Windows.Documents.Hyperlink> w celu przejścia do fragmentu zawartości, atrybut `NavigateUri` musi zawierać następujące elementy:

- @No__t-0 z <xref:System.Windows.Controls.Page> z fragmentem zawartości, do którego chcesz przejść.

- Znak "#".

- Nazwa elementu w <xref:System.Windows.Controls.Page>, który zawiera fragment zawartości.

Fragment [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] ma następujący format.

*PageURI* `#` *ElementName*

Poniżej przedstawiono przykład `Hyperlink`, który jest skonfigurowany do przechodzenia do fragmentu zawartości.

[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml1)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml2)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml3)]

> [!NOTE]
> W tej sekcji opisano domyślną implementację nawigacji fragmentów w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umożliwia również wdrożenie własnego schematu nawigacji fragmentu, który w części wymaga obsługi zdarzenia <xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType>.

> [!IMPORTANT]
> Można przechodzić do fragmentów na luźno [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stron (pliki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] z `Page` jako element główny) tylko wtedy, gdy strony mogą być przeglądane za pośrednictwem protokołu HTTP.
>
> Jednak swobodna Strona [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] może przechodzić do własnych fragmentów.

<a name="NavigationService"></a>

### <a name="navigation-service"></a>Usługa nawigacji

Chociaż <xref:System.Windows.Documents.Hyperlink> umożliwia użytkownikowi zainicjowanie nawigacji do określonego <xref:System.Windows.Controls.Page>, pracy lokalizowania i pobierania strony jest wykonywana przez klasę <xref:System.Windows.Navigation.NavigationService>. Zasadniczo <xref:System.Windows.Navigation.NavigationService> umożliwia przetworzenie żądania nawigacji w imieniu kodu klienta, takiego jak <xref:System.Windows.Documents.Hyperlink>. Ponadto <xref:System.Windows.Navigation.NavigationService> implementuje obsługę wyższego poziomu na potrzeby śledzenia i wpływania na żądanie nawigacji.

Po kliknięciu <xref:System.Windows.Documents.Hyperlink> wywołania [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> Aby zlokalizować i pobrać <xref:System.Windows.Controls.Page> w określonym pakiecie [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Pobrany <xref:System.Windows.Controls.Page> jest konwertowany na drzewo obiektów, których obiekt główny jest wystąpieniem pobranego <xref:System.Windows.Controls.Page>. Odwołanie do obiektu głównego <xref:System.Windows.Controls.Page> jest przechowywane we właściwości <xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType>. Pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla zawartości, do której została przeszukana, jest przechowywany we właściwości <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType>, podczas gdy <xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType> przechowuje pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla ostatniej strony, do której przeszedł.

> [!NOTE]
> Aplikacja [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] może mieć więcej niż jedną obecnie aktywną <xref:System.Windows.Navigation.NavigationService>. Aby uzyskać więcej informacji, zobacz [hosty nawigacji](#Navigation_Hosts) w dalszej części tego tematu.

<a name="Programmatic_Navigation_with_the_Navigation_Service"></a>

### <a name="programmatic-navigation-with-the-navigation-service"></a>Nawigacja programowa przy użyciu usługi nawigacji

Nie musisz wiedzieć o <xref:System.Windows.Navigation.NavigationService>, jeśli nawigacja jest implementowana w znacznikach przy użyciu <xref:System.Windows.Documents.Hyperlink>, ponieważ <xref:System.Windows.Documents.Hyperlink> w Twoim imieniu używa <xref:System.Windows.Navigation.NavigationService>. Oznacza to, że w przypadku bezpośredniego lub pośredniego rodzica <xref:System.Windows.Documents.Hyperlink> jest hostem nawigacyjnym (zobacz [hosty nawigacji](#Navigation_Hosts)), <xref:System.Windows.Documents.Hyperlink> będzie w stanie znaleźć i użyć usługi nawigacji hosta nawigacji, aby przetworzyć żądanie nawigacji.

Istnieją jednak sytuacje, w których należy bezpośrednio używać <xref:System.Windows.Navigation.NavigationService>, w tym:

- Gdy trzeba utworzyć wystąpienie <xref:System.Windows.Controls.Page> przy użyciu konstruktora bez parametrów.

- Jeśli musisz ustawić właściwości <xref:System.Windows.Controls.Page> przed przejściem do niego.

- Gdy <xref:System.Windows.Controls.Page>, do którego należy przejść, można określić tylko w czasie wykonywania.

W takich sytuacjach należy napisać kod, aby programowo zainicjować nawigację, wywołując metodę <xref:System.Windows.Navigation.NavigationService.Navigate%2A> obiektu <xref:System.Windows.Navigation.NavigationService>. Wymagające pobrania odwołania do <xref:System.Windows.Navigation.NavigationService>.

#### <a name="getting-a-reference-to-the-navigationservice"></a>Pobieranie odwołania do NavigationService

Ze względu na to, które są omówione w sekcji [hosty nawigacji](#Navigation_Hosts) , aplikacja [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] może mieć więcej niż jeden <xref:System.Windows.Navigation.NavigationService>. Oznacza to, że kod wymaga metody znalezienia <xref:System.Windows.Navigation.NavigationService>, która jest zazwyczaj <xref:System.Windows.Navigation.NavigationService>, który przeszedł do bieżącego <xref:System.Windows.Controls.Page>. Możesz uzyskać odwołanie do <xref:System.Windows.Navigation.NavigationService>, wywołując metodę `static` @ no__t-2. Aby uzyskać <xref:System.Windows.Navigation.NavigationService>, które przechodzą do określonego <xref:System.Windows.Controls.Page>, należy przekazać odwołanie do <xref:System.Windows.Controls.Page> jako argumentu metody <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A>. Poniższy kod pokazuje, jak uzyskać <xref:System.Windows.Navigation.NavigationService> dla bieżącego <xref:System.Windows.Controls.Page>.

[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPage.xaml.vb#getnscodebehind2)]

Jako skrót do wyszukiwania <xref:System.Windows.Navigation.NavigationService> dla <xref:System.Windows.Controls.Page>, <xref:System.Windows.Controls.Page> implementuje Właściwość <xref:System.Windows.Controls.Page.NavigationService%2A>. Pokazano to w poniższym przykładzie.

[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPageShortCut.xaml.vb#getnsshortcutcodebehind2)]

> [!NOTE]
> @No__t-0 może uzyskać odwołanie do <xref:System.Windows.Navigation.NavigationService>, gdy <xref:System.Windows.Controls.Page> zgłasza zdarzenie <xref:System.Windows.FrameworkElement.Loaded>.

#### <a name="programmatic-navigation-to-a-page-object"></a>Programistyczne nawigowanie do obiektu strony

Poniższy przykład pokazuje, jak używać <xref:System.Windows.Navigation.NavigationService> do programistycznego nawigowania do <xref:System.Windows.Controls.Page>. Nawigacja programowa jest wymagana, ponieważ do <xref:System.Windows.Controls.Page>, do których prowadzi proces, można utworzyć wystąpienie tylko przy użyciu jednego konstruktora bez parametrów. @No__t-0 z konstruktorem bez parametrów jest pokazana w poniższym znaczniku i kodzie.

[!code-xaml[NavigationOverviewSnippets#PageWithNonDefaultConstructorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml#pagewithnondefaultconstructorxaml)]

[!code-csharp[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml.cs#pagewithnondefaultconstructorcodebehind)]
[!code-vb[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithNonDefaultConstructor.xaml.vb#pagewithnondefaultconstructorcodebehind)]

@No__t-0, który nawiguje do <xref:System.Windows.Controls.Page> z konstruktorem bez parametrów, jest pokazany w następujących znacznikach i kodzie.

[!code-xaml[NavigationOverviewSnippets#NSNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml#nsnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml.cs#nsnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSNavigationPage.xaml.vb#nsnavigationpagecodebehind)]

Gdy zostanie kliknięta wartość <xref:System.Windows.Documents.Hyperlink> w tym <xref:System.Windows.Controls.Page>, Nawigacja zostanie zainicjowana przez utworzenie wystąpienia <xref:System.Windows.Controls.Page>, aby przejść do użycia konstruktora bez parametrów i wywołania metody <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType>. <xref:System.Windows.Navigation.NavigationService.Navigate%2A> akceptuje odwołanie do obiektu, do którego zostanie przejściu <xref:System.Windows.Navigation.NavigationService>, a nie z pakietem [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].

#### <a name="programmatic-navigation-with-a-pack-uri"></a>Nawigacja programowa przy użyciu identyfikatora URI pakietu

Jeśli konieczne jest skonstruowanie pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] programowo (jeśli można określić tylko pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] w czasie wykonywania, na przykład), można użyć metody <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType>. Pokazano to w poniższym przykładzie.

[!code-xaml[NavigationOverviewSnippets#NSUriNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml#nsurinavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml.cs#nsurinavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSUriNavigationPage.xaml.vb#nsurinavigationpagecodebehind)]

#### <a name="refreshing-the-current-page"></a>Odświeżanie bieżącej strony

Nie pobrano <xref:System.Windows.Controls.Page>, jeśli ma ten sam pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jako pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], który jest przechowywany we właściwości <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType>. Aby wymusić ponowne pobranie bieżącej strony przez [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], można wywołać metodę <xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType>, jak pokazano w poniższym przykładzie.

[!code-xaml[NavigationOverviewSnippets#NSRefreshNavigationPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml#nsrefreshnavigationpagexaml1)]

[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind1)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind2)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind2)]

<a name="Navigation_Lifetime"></a>

### <a name="navigation-lifetime"></a>Okres istnienia nawigacji

Istnieje wiele sposobów na zainicjowanie nawigacji, jak widać. Po zainicjowaniu nawigacji, gdy nawigacja jest w toku, można śledzić i wpływać na nawigację przy użyciu następujących zdarzeń, które są implementowane przez <xref:System.Windows.Navigation.NavigationService>:

- <xref:System.Windows.Navigation.NavigationService.Navigating>. Występuje po zażądaniu nowej nawigacji. Może służyć do anulowania nawigacji.

- <xref:System.Windows.Navigation.NavigationService.NavigationProgress>. Występuje okresowo podczas pobierania, aby zapewnić informacje o postępie nawigacji.

- <xref:System.Windows.Navigation.NavigationService.Navigated>. Występuje, gdy strona została umieszczona i pobrana.

- <xref:System.Windows.Navigation.NavigationService.NavigationStopped>. Występuje, gdy Nawigacja zostanie zatrzymana (wywołując <xref:System.Windows.Navigation.NavigationService.StopLoading%2A>) lub gdy zostanie zażądana Nowa Nawigacja, gdy bieżąca nawigacja jest w toku.

- <xref:System.Windows.Navigation.NavigationService.NavigationFailed>. Występuje, gdy wystąpi błąd podczas przechodzenia do wymaganej zawartości.

- <xref:System.Windows.Navigation.NavigationService.LoadCompleted>. Występuje, gdy zawartość, do której została przetworzona, została załadowana i przeanalizowana, i rozpoczęto renderowanie.

- <xref:System.Windows.Navigation.NavigationService.FragmentNavigation>. Występuje po rozpoczęciu nawigacji do fragmentu zawartości, co następuje:

  - Natychmiast, jeśli żądany fragment znajduje się w bieżącej zawartości.

  - Po załadowaniu zawartości źródłowej, jeśli żądany fragment znajduje się w innej zawartości.

Zdarzenia nawigacji są zgłaszane w kolejności zilustrowanej na poniższej ilustracji.

![](./media/navigation-overview/order-of-navigation-events.png "Wykres przepływu zdarzeń nawigacji") na stronie wykresu nawigacji na stronie

Ogólnie rzecz biorąc, <xref:System.Windows.Controls.Page> nie dotyczy tych zdarzeń. Jest to bardziej możliwe, że aplikacja jest objęta nimi, a z tego powodu zdarzenia te są również zgłaszane przez klasę <xref:System.Windows.Application>:

- <xref:System.Windows.Application.Navigating?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationProgress?displayProperty=nameWithType>

- <xref:System.Windows.Application.Navigated?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationFailed?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationStopped?displayProperty=nameWithType>

- <xref:System.Windows.Application.LoadCompleted?displayProperty=nameWithType>

- <xref:System.Windows.Application.FragmentNavigation?displayProperty=nameWithType>

Za każdym razem, gdy <xref:System.Windows.Navigation.NavigationService> wywołuje zdarzenie, Klasa <xref:System.Windows.Application> wywołuje odpowiednie zdarzenie. <xref:System.Windows.Controls.Frame> i <xref:System.Windows.Navigation.NavigationWindow> oferują te same zdarzenia w celu wykrywania nawigacji w obrębie odpowiednich zakresów.

W niektórych przypadkach <xref:System.Windows.Controls.Page> może zainteresować te zdarzenia. Na przykład <xref:System.Windows.Controls.Page> może obsłużyć zdarzenie <xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType>, aby określić, czy anulować nawigację od samego siebie. Pokazano to w poniższym przykładzie.

[!code-xaml[NavigationOverviewSnippets#CancelNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml#cancelnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml.cs#cancelnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/CancelNavigationPage.xaml.vb#cancelnavigationpagecodebehind)]

Jeśli procedura obsługi zostanie zarejestrowana z użyciem zdarzenia nawigacji z <xref:System.Windows.Controls.Page>, jak w powyższym przykładzie, należy również wyrejestrować procedurę obsługi zdarzeń. Jeśli tego nie zrobisz, mogą wystąpić skutki uboczne w odniesieniu do sposobu, w jaki elementy nawigacyjne [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] odnoszą się do <xref:System.Windows.Controls.Page> nawigacji przy użyciu dziennika.

<a name="NavigationHistory"></a>

### <a name="remembering-navigation-with-the-journal"></a>Zapamiętywanie nawigacji przy użyciu dziennika

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] używa dwóch stosów do zapamiętania stron, z których pochodzą: stos zaplecza i stos do przodu. Podczas przechodzenia z bieżącego <xref:System.Windows.Controls.Page> do nowej <xref:System.Windows.Controls.Page> lub do istniejącej <xref:System.Windows.Controls.Page>, bieżący <xref:System.Windows.Controls.Page> zostanie dodany do *stosu zaplecza*. Po przejściu z bieżącego <xref:System.Windows.Controls.Page> z powrotem do poprzedniej <xref:System.Windows.Controls.Page>, bieżąca <xref:System.Windows.Controls.Page> zostanie dodana do *stosu przesyłania dalej*. Stos zaplecza, stos przesyłania dalej i funkcje do zarządzania nimi są określane zbiorczo jako dziennik. Każdy element w stosie zaplecza i stos do przodu jest wystąpieniem klasy <xref:System.Windows.Navigation.JournalEntry> i jest określany jako *wpis w dzienniku*.

#### <a name="navigating-the-journal-from-internet-explorer"></a>Nawigowanie po dzienniku z programu Internet Explorer

Koncepcyjnie dziennik działa tak samo, jak przyciski **Wstecz** i **dalej** w programie Internet Explorer. Są one pokazane na poniższej ilustracji.

![Przyciski Wstecz i dalej](./media/navigation-overview/back-and-forward-navigation.png "przejdą do przycisków Wstecz i do przodu.")

W przypadku [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] hostowanych przez program Internet Explorer [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] integruje dziennik w @no__t nawigacji-2 programu Internet Explorer. Dzięki temu użytkownicy mogą nawigować do stron w [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] przy użyciu przycisków **Wstecz**, **do przodu**i **ostatnich stron** w programie Internet Explorer.

> [!IMPORTANT]
> W programie Internet Explorer, gdy użytkownik nawiguje do i z powrotem do [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], tylko wpisy dziennika dla stron, które nie były aktywne, są zachowywane w dzienniku. Aby poznać dyskusję na temat utrzymywania stron, zobacz [okres istnienia strony i dziennik](#PageLifetime) w dalszej części tego tematu.

Domyślnie tekst dla każdego <xref:System.Windows.Controls.Page> pojawia się na liście **ostatnich stron** programu Internet Explorer to [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla <xref:System.Windows.Controls.Page>. W wielu przypadkach nie jest to szczególnie istotne dla użytkownika. Na szczęście można zmienić tekst przy użyciu jednej z następujących opcji:

1. Dołączona wartość atrybutu `JournalEntry.Name`.

2. Wartość atrybutu `Page.Title`.

3. Wartość atrybutu `Page.WindowTitle` i [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla bieżącego <xref:System.Windows.Controls.Page>.

4. @No__t-0 dla bieżącej <xref:System.Windows.Controls.Page>. Wartooć

Kolejność, w jakiej są wyświetlane opcje, jest zgodna z kolejnością pierwszeństwa podczas wyszukiwania tekstu. Na przykład jeśli ustawiono wartość `JournalEntry.Name`, pozostałe wartości zostaną zignorowane.

W poniższym przykładzie zastosowano atrybut `Page.Title`, aby zmienić tekst wyświetlany dla wpisu dziennika.

[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup2)]

[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind1)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind2)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind2)]

#### <a name="navigating-the-journal-using-wpf"></a>Nawigowanie po arkuszu przy użyciu WPF

Mimo że użytkownik może nawigować po arkuszu przy użyciu stron z **tyłu**, **do przodu**i **ostatnich** w programie Internet Explorer, można także nawigować po dzienniku przy użyciu mechanizmów deklaratywnych i programistycznych zapewnianych przez [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Jednym z powodów, aby to zrobić, jest udostępnienie na stronach niestandardowych interfejsów użytkownika nawigacyjnych.

Można deklaratywnie dodać obsługę nawigacji w dzienniku za pomocą poleceń nawigacyjnych uwidocznionych przez <xref:System.Windows.Input.NavigationCommands>. Poniższy przykład ilustruje sposób użycia polecenia nawigacji `BrowseBack`.

[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml1)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml2)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml3)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML4](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml4)]

Można programistycznie nawigować po arkuszu przy użyciu jednego z następujących elementów członkowskich klasy <xref:System.Windows.Navigation.NavigationService>:

- <xref:System.Windows.Navigation.NavigationService.GoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.GoForward%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoForward%2A>

Dziennik może być również manipulowany programowo, zgodnie z opisem w sekcji [zachowywanie stanu zawartości przy użyciu historii nawigacji](#RetainingContentStateWithNavigationHistory) w dalszej części tego tematu.

<a name="PageLifetime"></a>

### <a name="page-lifetime-and-the-journal"></a>Okres istnienia strony i dziennik

Weź pod uwagę [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] z kilkoma stronami zawierającymi zawartość rozbudowaną, w tym grafiki, animacje i multimedia. Użycie pamięci dla stron takich jak takie może być bardzo duże, szczególnie w przypadku używania nośnika wideo i audio. Mając na uwagę, że strony, do których odnoszą się przechodzenie, takie jak [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], mogą szybko wykorzystać znaczną i zauważalną ilość pamięci.

Z tego powodu domyślne zachowanie dziennika polega na przechowywaniu metadanych <xref:System.Windows.Controls.Page> w każdym wpisie dziennika, a nie w odniesieniu do obiektu <xref:System.Windows.Controls.Page>. Po przejściu do pozycji dziennika, jej metadane <xref:System.Windows.Controls.Page> są używane do tworzenia nowego wystąpienia określonego <xref:System.Windows.Controls.Page>. W związku z tym każdy przechodzący <xref:System.Windows.Controls.Page> ma okres istnienia, który jest przedstawiony na poniższej ilustracji.

![Okres istnienia strony](./media/navigation-overview/navigated-page-lifetime.png "pokazuje okres istnienia strony.")

Chociaż korzystanie z domyślnego zachowania rejestrowania może zaoszczędzić przy zużyciu pamięci, wydajność renderowania na stronie może ulec zmniejszeniu. ponowne wystąpienie <xref:System.Windows.Controls.Page> może być czasochłonne, szczególnie jeśli ma dużą zawartość. Jeśli musisz zachować wystąpienie <xref:System.Windows.Controls.Page> w dzienniku, możesz narysować na dwie techniki. Najpierw można programistycznie nawigować do obiektu <xref:System.Windows.Controls.Page>, wywołując metodę <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType>.

Następnie można określić, że [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zachować wystąpienie <xref:System.Windows.Controls.Page> w dzienniku przez ustawienie @no__t właściwości <xref:System.Windows.Controls.Page.KeepAlive%2A> (wartość domyślna to `false`). Jak pokazano w poniższym przykładzie, można ustawić <xref:System.Windows.Controls.Page.KeepAlive%2A> deklaratywnie w znaczniku.

[!code-xaml[NavigationOverviewSnippets#KeepAlivePageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/KeepAlivePage.xaml#keepalivepagexaml)]

Okres istnienia <xref:System.Windows.Controls.Page>, która jest utrzymywana, jest nieco inny niż taki, który nie jest. Przy pierwszym przejściu do <xref:System.Windows.Controls.Page>, do którego jest prowadzona aktywność, zostanie utworzona jego wystąpienie, tak jak <xref:System.Windows.Controls.Page>, które nie jest aktywne. Ponieważ jednak wystąpienie <xref:System.Windows.Controls.Page> jest zachowywane w dzienniku, nigdy nie jest ponownie tworzone, dopóki nie pozostanie w dzienniku. W związku z tym, jeśli <xref:System.Windows.Controls.Page> ma logikę inicjalizacji, która musi być wywoływana za każdym razem, gdy <xref:System.Windows.Controls.Page> jest przenoszona do, należy przenieść ją z konstruktora do procedury obsługi zdarzenia <xref:System.Windows.FrameworkElement.Loaded>. Jak pokazano na poniższej ilustracji, zdarzenia <xref:System.Windows.FrameworkElement.Loaded> i <xref:System.Windows.FrameworkElement.Unloaded> są nadal wywoływane za każdym razem, gdy <xref:System.Windows.Controls.Page> jest przenoszona do i z, odpowiednio.

Załadowane ![i niezaładowane zdarzenia są zgłaszane](./media/navigation-overview/loaded-and-unloaded-events.png ", a zdarzenia zwolnione są zgłaszane, gdy strona jest przenoszona do i z.")

Gdy <xref:System.Windows.Controls.Page> nie działa, należy wykonać jedną z następujących czynności:

- Zapisz odwołanie do niego lub jego część.

- Zarejestruj procedury obsługi zdarzeń ze zdarzeniami, które nie zostały zaimplementowane przez ten program.

Wykonanie dowolnej z tych opcji spowoduje utworzenie odwołań, które wymuszają <xref:System.Windows.Controls.Page> w pamięci, nawet po usunięciu z dziennika.

Ogólnie rzecz biorąc, należy preferować domyślne zachowanie <xref:System.Windows.Controls.Page> nieutrzymując <xref:System.Windows.Controls.Page> aktywności. Ma to jednak konsekwencje stanu omówione w następnej sekcji.

<a name="RetainingContentStateWithNavigationHistory"></a>

### <a name="retaining-content-state-with-navigation-history"></a>Zachowywanie stanu zawartości przy użyciu historii nawigacji

Jeśli <xref:System.Windows.Controls.Page> nie jest aktywna i ma kontrolki, które zbierają dane od użytkownika, co się dzieje z danymi, gdy użytkownik nawiguje z powrotem do <xref:System.Windows.Controls.Page>? W perspektywie środowiska użytkownika użytkownik powinien oczekiwać, że dane wprowadzone wcześniej. Niestety, ze względu na to, że nowe wystąpienie <xref:System.Windows.Controls.Page> jest tworzone przy użyciu każdej nawigacji, formanty, które zbierają dane, są usuwane, a dane zostaną utracone.

Na szczęście dziennik zapewnia obsługę zapamiętywania danych między nawigacjami <xref:System.Windows.Controls.Page>, w tym danymi kontroli. W każdym przypadku wpis dziennika dla każdego <xref:System.Windows.Controls.Page> pełni rolę kontenera tymczasowego dla skojarzonego stanu <xref:System.Windows.Controls.Page>. Poniższe kroki przedstawiają sposób użycia tej pomocy technicznej w przypadku przejścia do <xref:System.Windows.Controls.Page> z:

1. Wpis dla bieżącego <xref:System.Windows.Controls.Page> zostanie dodany do dziennika.

2. Stan <xref:System.Windows.Controls.Page> jest przechowywany w pozycji dziennika dla tej strony, która jest dodawana do stosu back.

3. Nowy <xref:System.Windows.Controls.Page> jest przechodzenia do.

Gdy strona <xref:System.Windows.Controls.Page> zostanie przeprowadzona z powrotem do, przy użyciu dziennika należy wykonać następujące czynności:

1. Zostanie utworzone wystąpienie <xref:System.Windows.Controls.Page> (górny wpis dziennika na stosie zaplecza).

2. @No__t-0 jest odświeżany stanem, który został zapisany w pozycji dziennika dla <xref:System.Windows.Controls.Page>.

3. @No__t-0 jest przechodzenia z powrotem do.

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] automatycznie korzysta z tej obsługi, gdy na <xref:System.Windows.Controls.Page> są używane następujące kontrolki:

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

Jeśli <xref:System.Windows.Controls.Page> używa tych kontrolek, dane wprowadzone do nich są zapamiętywane przez nawigację <xref:System.Windows.Controls.Page>, jak pokazano w **ulubionym kolorze**<xref:System.Windows.Controls.ListBox> na poniższej ilustracji.

![Strona z kontrolkami, które zapamiętali wprowadzone dane stanu,](./media/navigation-overview/data-remembered-across-page-navigations.png "jest zapamiętywana między nawigacjami stron.")

Gdy <xref:System.Windows.Controls.Page> zawiera kontrolki inne niż te znajdujące się na poprzedniej liście lub gdy stan jest przechowywany w obiektach niestandardowych, należy napisać kod, aby spowodować, że dziennik zostanie zapamiętany przez nawigację <xref:System.Windows.Controls.Page>.

Jeśli musisz zapamiętać małe fragmenty stanu między nawigacjami <xref:System.Windows.Controls.Page>, możesz użyć właściwości zależności (patrz <xref:System.Windows.DependencyProperty>) skonfigurowanych przy użyciu flagi metadanych <xref:System.Windows.FrameworkPropertyMetadata.Journal%2A?displayProperty=nameWithType>.

Jeśli stan, który <xref:System.Windows.Controls.Page> należy pamiętać między nawigacjami, składa się z wielu fragmentów danych, może się okazać, że mniej czasochłonny kod hermetyzuje swój stan w jednej klasie i implementuje interfejs <xref:System.Windows.Navigation.IProvideCustomContentState>.

Jeśli chcesz nawigować przez różne stany jednego <xref:System.Windows.Controls.Page>, bez przechodzenia do <xref:System.Windows.Controls.Page>, możesz użyć <xref:System.Windows.Navigation.IProvideCustomContentState> i <xref:System.Windows.Navigation.NavigationService.AddBackEntry%2A?displayProperty=nameWithType>.

<a name="Cookies"></a>

### <a name="cookies"></a>Cookie

Inny sposób, w jaki aplikacje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] mogą przechowywać dane, to pliki cookie, które są tworzone, aktualizowane i usuwane przy użyciu metod <xref:System.Windows.Application.SetCookie%2A> i <xref:System.Windows.Application.GetCookie%2A>. Pliki cookie, które można utworzyć w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] są tymi samymi plikami cookie, które są używane przez inne typy aplikacji sieci Web; pliki cookie to dowolne fragmenty danych przechowywane przez aplikację na komputerze klienckim w trakcie lub między sesjami aplikacji. Dane plików cookie zazwyczaj przyjmuje postać pary nazwa/wartość w następującym formacie.

*Nazwa* `=` *wartość*

Gdy dane są przesyłane do <xref:System.Windows.Application.SetCookie%2A>, wraz z <xref:System.Uri> lokalizacji, dla której ma zostać ustawiony plik cookie, plik cookie jest tworzony w pamięci i jest dostępny tylko w czasie trwania bieżącej sesji aplikacji. Ten typ pliku cookie jest określany jako *plik cookie sesji*.

Aby przechowywać plik cookie między sesjami aplikacji, należy dodać do pliku cookie datę wygaśnięcia, używając następującego formatu.

*Nazwa* `=` *wartość* `; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`

Plik cookie z datą wygaśnięcia jest przechowywany w folderze tymczasowych plików internetowych instalacji systemu Windows do momentu wygaśnięcia pliku cookie. Taki plik cookie jest znany jako *trwały plik cookie* , ponieważ utrzymuje się między sesjami aplikacji.

Można pobrać zarówno sesję, jak i trwałe pliki cookie, wywołując metodę <xref:System.Windows.Application.GetCookie%2A>, przekazując <xref:System.Uri> lokalizacji, w której ustawiono plik cookie przy użyciu metody <xref:System.Windows.Application.SetCookie%2A>.

Poniżej przedstawiono niektóre sposoby obsługi plików cookie w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]:

- Aplikacje autonomiczne [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] i [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] mogą tworzyć pliki cookie i zarządzać nimi.

- Dostęp do plików cookie utworzonych za pomocą [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] można uzyskać z przeglądarki.

- [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] z tej samej domeny może tworzyć i udostępniać pliki cookie.

- [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] i strony HTML z tej samej domeny mogą tworzyć i udostępniać pliki cookie.

- Pliki cookie są wysyłane, gdy [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] i luźne strony [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tworzą żądania sieci Web.

- Zarówno @no__t najwyższego poziomu-0 i [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] hostowane w elementach IFRAME mogą uzyskiwać dostęp do plików cookie.

- Obsługa plików cookie w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jest taka sama dla wszystkich obsługiwanych przeglądarek.

- W programie Internet Explorer Zasady P3P, które odnoszą się do plików cookie, są honorowane przez [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], szczególnie w odniesieniu do [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] stron trzecich.

<a name="Structured_Navigation"></a>

### <a name="structured-navigation"></a>Nawigacja strukturalna

Jeśli konieczne jest przekazanie danych z jednego <xref:System.Windows.Controls.Page> do innego, można przekazać dane jako argumenty do konstruktora bez parametrów <xref:System.Windows.Controls.Page>. Należy pamiętać, że w przypadku korzystania z tej techniki należy zachować <xref:System.Windows.Controls.Page> aktywności; w przeciwnym razie przy następnym przejściu do <xref:System.Windows.Controls.Page> [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ponownie tworzy wystąpienie <xref:System.Windows.Controls.Page> przy użyciu konstruktora bez parametrów.

Alternatywnie, <xref:System.Windows.Controls.Page> może zaimplementować właściwości, które są ustawione z danymi, które muszą zostać przesłane. Jednak rzeczy stają się trudne, gdy <xref:System.Windows.Controls.Page> musi przekazać dane z powrotem do <xref:System.Windows.Controls.Page>, które przeszedł do niego. Problem polega na tym, że nawigacja nie wspiera natywnie mechanizmów do zagwarantowania, że <xref:System.Windows.Controls.Page> zostanie zwrócona po przejściu z. Zasadniczo nawigacja nie obsługuje semantyki wywołania/powrotu. Aby rozwiązać ten problem, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zawiera klasę <xref:System.Windows.Navigation.PageFunction%601>, której można użyć, aby upewnić się, że <xref:System.Windows.Controls.Page> jest zwracany do przewidywalny i strukturalny sposób. Aby uzyskać więcej informacji, zobacz [Omówienie nawigacji strukturalnej](structured-navigation-overview.md).

<a name="The_NavigationWindow_Class"></a>

## <a name="the-navigationwindow-class"></a>Klasa NavigationWindow

Do tego momentu zobaczysz gamę usług nawigacyjnych, których najprawdopodobniej używasz do kompilowania aplikacji z nawigacją. Te usługi zostały omówione w kontekście [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], chociaż nie są ograniczone do [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Nowoczesne systemy operacyjne i aplikacje systemu Windows wykorzystują korzystanie z przeglądarki nowoczesnych użytkowników w celu uwzględnienia nawigacji w stylu przeglądarki w aplikacjach autonomicznych. Typowe przykłady obejmują:

- **Tezaurus słów**: nawigowanie po wyborach w programie Word.

- **Eksplorator plików**: nawigowanie po plikach i folderach.

- **Kreatorzy**: dzielenie złożonego zadania na wiele stron, które mogą być przechodzenie między. Przykładem jest Kreator składników systemu Windows, który obsługuje dodawanie i usuwanie funkcji systemu Windows.

Aby włączyć nawigację w stylu przeglądarki do aplikacji autonomicznych, można użyć klasy <xref:System.Windows.Navigation.NavigationWindow>. <xref:System.Windows.Navigation.NavigationWindow> pochodzi od <xref:System.Windows.Window> i rozszerza je o te same wsparcie dla nawigacji, którą zapewnia [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Możesz użyć <xref:System.Windows.Navigation.NavigationWindow> jako głównego okna aplikacji autonomicznej lub jako okna pomocniczego, takiego jak okno dialogowe.

Aby zaimplementować <xref:System.Windows.Navigation.NavigationWindow>, jak w przypadku większości klas najwyższego poziomu w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] (<xref:System.Windows.Window>, <xref:System.Windows.Controls.Page> itd.), należy użyć kombinacji znaczników i kodu. Pokazano to w poniższym przykładzie.

[!code-xaml[IntroToNavNavigationWindowSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml#navigationwindowmarkup)]

[!code-csharp[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml.cs#navigationwindowcodebehind)]
[!code-vb[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/MainWindow.xaml.vb#navigationwindowcodebehind)]

Ten kod tworzy <xref:System.Windows.Navigation.NavigationWindow>, która automatycznie przechodzi do <xref:System.Windows.Controls.Page> (Strona główna. XAML) podczas otwierania <xref:System.Windows.Navigation.NavigationWindow>. Jeśli <xref:System.Windows.Navigation.NavigationWindow> jest głównym oknem aplikacji, można użyć atrybutu `StartupUri`, aby go uruchomić. Jest to pokazane w poniższej tabeli.

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchNavWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/App.xaml#applaunchnavwindow)]

Na poniższej ilustracji przedstawiono <xref:System.Windows.Navigation.NavigationWindow> jako główne okno aplikacji autonomicznej.

Okno nawigacji ![okna głównego](./media/navigation-overview/navigation-window-as-main-window.png "jako okno główne")

Na rysunku widać, że <xref:System.Windows.Navigation.NavigationWindow> ma tytuł, nawet jeśli nie został on ustawiony w kodzie implementacji <xref:System.Windows.Navigation.NavigationWindow> z poprzedniego przykładu. Zamiast tego, tytuł jest ustawiany przy użyciu właściwości <xref:System.Windows.Controls.Page.WindowTitle%2A>, która jest pokazana w poniższym kodzie.

[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup1)]
[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup2)]

Ustawienie właściwości <xref:System.Windows.Controls.Page.WindowWidth%2A> i <xref:System.Windows.Controls.Page.WindowHeight%2A> ma także wpływ na <xref:System.Windows.Navigation.NavigationWindow>.

Zazwyczaj należy zaimplementować własne <xref:System.Windows.Navigation.NavigationWindow>, gdy trzeba dostosować zachowanie lub jego wygląd. Jeśli nie wykonasz żadnego z tych czynności, możesz użyć skrótu. Jeśli określisz pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] <xref:System.Windows.Controls.Page> jako <xref:System.Windows.Application.StartupUri%2A> w aplikacji autonomicznej, <xref:System.Windows.Application> automatycznie utworzy <xref:System.Windows.Navigation.NavigationWindow> do hostowania <xref:System.Windows.Controls.Page>. Poniższe znaczniki pokazują, jak włączyć tę funkcję.

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchPage](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/AnotherApp.xaml#applaunchpage)]

Jeśli chcesz, aby okno aplikacji dodatkowej, takie jak okno dialogowe, było <xref:System.Windows.Navigation.NavigationWindow>, możesz użyć kodu w poniższym przykładzie, aby go otworzyć.

[!code-csharp[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/DialogOwnerWindow.xaml.cs#createnwdialogbox)]
[!code-vb[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/DialogOwnerWindow.xaml.vb#createnwdialogbox)]

Na poniższej ilustracji przedstawiono wynik.

![](./media/navigation-overview/navigation-window-as-dialog-box.png "Okno nawigacji okna dialogowego jako okno dialogowe")

Jak widać, <xref:System.Windows.Navigation.NavigationWindow> Wyświetla przyciski wstecz i **do** **tyłu** w stylu programu Internet Explorer, które umożliwiają użytkownikom nawigowanie po arkuszu. Te przyciski zapewniają takie samo środowisko użytkownika, jak pokazano na poniższej ilustracji.

![Przyciski Wstecz i dalej na](./media/navigation-overview/back-and-forward-buttons-in-navigation-window.png "przyciskach NavigationWindow do tyłu i do przodu w oknie nawigacji")

Jeśli strony zapewniają własną obsługę nawigacji w dzienniku i interfejs użytkownika, można ukryć przyciski **Wstecz** i **do przodu** wyświetlane przez <xref:System.Windows.Navigation.NavigationWindow>, ustawiając wartość właściwości <xref:System.Windows.Navigation.NavigationWindow.ShowsNavigationUI%2A> na `false`.

Alternatywnie możesz użyć obsługi dostosowywania w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], aby zastąpić [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Navigation.NavigationWindow>.

<a name="Frame_in_Standalone_Applications"></a>

## <a name="the-frame-class"></a>Klasa Frame

Przeglądarka i <xref:System.Windows.Navigation.NavigationWindow> to Windows, który obsługuje nawigować po zawartości. W niektórych przypadkach aplikacje mają zawartość, która nie musi być hostowana przez całe okno. Zamiast tego taka zawartość jest hostowana w innej zawartości. Można wstawić zawartość nawigacji do innej zawartości przy użyciu klasy <xref:System.Windows.Controls.Frame>. <xref:System.Windows.Controls.Frame> zapewnia taką samą obsługę jak <xref:System.Windows.Navigation.NavigationWindow> i [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].

Poniższy przykład pokazuje, jak dodać <xref:System.Windows.Controls.Frame> do <xref:System.Windows.Controls.Page> deklaratywnie przy użyciu elementu `Frame`.

[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml3)]

Ten znacznik ustawia atrybut `Source` elementu `Frame` z pakietem [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla <xref:System.Windows.Controls.Page>, do którego ma nastąpić pierwotne przechodzenie <xref:System.Windows.Controls.Frame>. Na poniższej ilustracji przedstawiono [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] z <xref:System.Windows.Controls.Page>, który ma <xref:System.Windows.Controls.Frame>, które przeszły między kilka stron.

![Ramka, która przeszła między wieloma stronami](./media/navigation-overview/frame-navigation-between-multiple-pages.png ", pokazuje nawigację po klatce między wieloma stronami.")

Nie musisz używać <xref:System.Windows.Controls.Frame> wewnątrz zawartości <xref:System.Windows.Controls.Page>. Jest również często hostować <xref:System.Windows.Controls.Frame> wewnątrz zawartości <xref:System.Windows.Window>.

Domyślnie <xref:System.Windows.Controls.Frame> używa własnego dziennika w przypadku braku innego dziennika. Jeśli <xref:System.Windows.Controls.Frame> jest częścią zawartości hostowanej w <xref:System.Windows.Navigation.NavigationWindow> lub [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], <xref:System.Windows.Controls.Frame> używa dziennika, który należy do <xref:System.Windows.Navigation.NavigationWindow> lub [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Czasami chociaż <xref:System.Windows.Controls.Frame> może być odpowiedzialna za własny dziennik. Jedną z przyczyn tego problemu jest umożliwienie nawigowania w dziennikach na stronach, które są hostowane przez <xref:System.Windows.Controls.Frame>. Jest to zilustrowane na poniższej ilustracji.

![Diagram ramek i stron](./media/navigation-overview/journal-navigation-within-pages-hosted-by-a-frame.png "przedstawiający nawigację w ramach stron hostowanych przez ramkę.")

W takim przypadku można skonfigurować <xref:System.Windows.Controls.Frame>, aby użyć własnego dziennika, ustawiając właściwość <xref:System.Windows.Controls.Frame.JournalOwnership%2A> <xref:System.Windows.Controls.Frame> na <xref:System.Windows.Navigation.JournalOwnership.OwnsJournal>. Jest to pokazane w poniższej tabeli.

[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml3)]

Na poniższej ilustracji przedstawiono efekt nawigowania w obrębie <xref:System.Windows.Controls.Frame>, który używa własnego dziennika.

![Ramka, która używa własnego dziennika,](./media/navigation-overview/frame-uses-its-own-journal.png "pokazuje efekt nawigowania w obrębie ramki korzystającej z własnego dziennika.")

Należy zauważyć, że wpisy w dzienniku są wyświetlane przez nawigację [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w <xref:System.Windows.Controls.Frame>, a nie przez program Internet Explorer.

> [!NOTE]
> Jeśli <xref:System.Windows.Controls.Frame> jest częścią zawartości hostowanej w <xref:System.Windows.Window>, <xref:System.Windows.Controls.Frame> używa własnego dziennika i w związku z tym wyświetla własną nawigację [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].

Jeśli środowisko użytkownika wymaga <xref:System.Windows.Controls.Frame>, aby zapewnić własny dziennik bez wyświetlania @no__t nawigacyjnego-1, można ukryć nawigację [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], ustawiając <xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A> do <xref:System.Windows.Visibility.Hidden>. Jest to pokazane w poniższej tabeli.

[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml3)]

<a name="Navigation_Hosts"></a>

## <a name="navigation-hosts"></a>Hosty nawigacji

<xref:System.Windows.Controls.Frame> i <xref:System.Windows.Navigation.NavigationWindow> to klasy, które są znane jako hosty nawigacji. *Host nawigacyjny* jest klasą, która może nawigować do zawartości i wyświetlać ją. Aby to osiągnąć, każdy host nawigacji używa własnego <xref:System.Windows.Navigation.NavigationService> i dziennika. Podstawowa konstrukcja hosta nawigacji jest pokazana na poniższej ilustracji.

![Diagramy nawigatora](./media/navigation-overview/navigation-host-construction.png "podstawowa konstrukcja hosta nawigacji")

Zasadniczo pozwala to na <xref:System.Windows.Navigation.NavigationWindow> i <xref:System.Windows.Controls.Frame> w celu zapewnienia tej samej obsługi nawigacji, którą zapewnia [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], gdy jest ona hostowana w przeglądarce.

Oprócz korzystania z <xref:System.Windows.Navigation.NavigationService> i dziennika, hosty nawigacji implementują te same elementy członkowskie, których implementacje <xref:System.Windows.Navigation.NavigationService>. Jest to zilustrowane na poniższej ilustracji.

![Dziennik w ramce i w NavigationWindow](./media/navigation-overview/navigation-window-and-frame.png "oknie nawigacji i ramce")

Pozwala to na bezpośrednie przechodzenie do pomocy technicznej dotyczącej nawigacji. Można to wziąć pod uwagę, jeśli konieczne jest podanie niestandardowej nawigacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dla <xref:System.Windows.Controls.Frame>, który jest hostowany w <xref:System.Windows.Window>. Ponadto oba typy implementują dodatkowe elementy członkowskie powiązane z nawigacją, w tym `BackStack` (<xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType>) i `ForwardStack` (<xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType>), które umożliwiają Wyliczenie wpisów dziennika w stosie wstecznym i w stosie progresywnym.

Jak wspomniano wcześniej, w aplikacji może istnieć więcej niż jeden dziennik. Na poniższej ilustracji przedstawiono przykład, w którym może się to zdarzyć.

![Wiele dzienników w jednej aplikacji](./media/navigation-overview/multiple-journals-in-one-application.png "jest to przykład z więcej niż jednym dziennikiem w aplikacji.")

<a name="Navigating_to_Content_Other_than_Pages"></a>

## <a name="navigating-to-content-other-than-xaml-pages"></a>Przechodzenie do zawartości innej niż strony XAML

W tym temacie <xref:System.Windows.Controls.Page> i Pack [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] zostały użyte do zademonstrowania różnych możliwości nawigacyjnych [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Jednak <xref:System.Windows.Controls.Page>, który jest kompilowany do aplikacji nie jest jedynym typem zawartości, do której można przejść, a pakiet [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] nie jest jedynym sposobem identyfikacji zawartości.

Jak widać w tej sekcji, możesz również przejść do luźnych plików [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], plików HTML i obiektów.

<a name="Navigating_to_Loose_XAML_Files"></a>

### <a name="navigating-to-loose-xaml-files"></a>Przechodzenie do luźnych plików XAML

Luźny plik [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest plikiem o następujących cechach:

- Zawiera tylko [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (oznacza to, że nie jest to kod).

- Ma odpowiednią deklarację przestrzeni nazw.

- Ma rozszerzenie nazwy pliku. XAML.

Rozważmy na przykład następującą zawartość, która jest przechowywana jako luźny plik [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], Person. XAML.

[!code-xaml[NavigationOverviewSnippets#LooseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Person.xaml#loosexaml)]

Po dwukrotnym kliknięciu pliku zostanie otwarta przeglądarka i zostanie wyświetlona zawartość. Jest to pokazane na poniższej ilustracji.

![Wyświetlanie zawartości w pliku Person. XAML](./media/navigation-overview/contents-of-person-xaml-file.png "pokazuje zawartość pliku Person. XAML.")

Można wyświetlić luźny plik [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] z następujących:

- Witryna sieci Web na komputerze lokalnym, w intranecie lub w Internecie.

- Udział plików Universal Naming Convention (UNC).

- Dysk lokalny.

Luźny plik [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] można dodać do ulubionych przeglądarki lub jako stronę główną przeglądarki.

> [!NOTE]
> Aby uzyskać więcej informacji na temat publikowania i uruchamiania luźnych stron [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], zobacz [wdrażanie aplikacji WPF](deploying-a-wpf-application-wpf.md).

Ograniczenie odnoszące się do luźnych [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] oznacza, że można hostować tylko zawartość, która jest bezpieczna do uruchamiania w częściowej relacji zaufania. Na przykład `Window` nie może być elementem głównym luźnego pliku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Aby uzyskać więcej informacji, zobacz temat informacje o [zabezpieczeniach częściowej relacji zaufania WPF](../wpf-partial-trust-security.md).

<a name="Navigating_to_HTML_Files_Using_Frame"></a>

### <a name="navigating-to-html-files-by-using-frame"></a>Nawigowanie do plików HTML przy użyciu ramki

Jak można się spodziewać, możesz również przejść do kodu HTML. Wystarczy dostarczyć [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], który używa schematu http. Na przykład poniższy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pokazuje <xref:System.Windows.Controls.Frame>, który przechodzi do strony HTML.

[!code-xaml[NavigationOverviewSnippets#FrameHtmlNavMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHTMLNavPage.xaml#framehtmlnavmarkup)]

Przechodzenie do HTML wymaga specjalnych uprawnień. Na przykład nie można nawigować po [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], który jest uruchomiony w piaskownicy zabezpieczenia strefy internetowej częściowej relacji zaufania. Aby uzyskać więcej informacji, zobacz temat informacje o [zabezpieczeniach częściowej relacji zaufania WPF](../wpf-partial-trust-security.md).

<a name="Navigating_to_HTML_Files_Using_WebBrowser"></a>

### <a name="navigating-to-html-files-by-using-the-webbrowser-control"></a>Nawigowanie do plików HTML przy użyciu kontrolki WebBrowser

Kontrolka <xref:System.Windows.Controls.WebBrowser> obsługuje obsługę dokumentów HTML, nawigację i skrypt/współdziałanie kodu zarządzanego. Aby uzyskać szczegółowe informacje dotyczące kontroli <xref:System.Windows.Controls.WebBrowser>, zobacz <xref:System.Windows.Controls.WebBrowser>.

Podobnie jak <xref:System.Windows.Controls.Frame>, przechodzenie do kodu HTML przy użyciu <xref:System.Windows.Controls.WebBrowser> wymaga specjalnych uprawnień. Na przykład w aplikacji częściowo zaufanej można nawigować tylko do kodu HTML znajdującego się w lokalizacji źródłowej. Aby uzyskać więcej informacji, zobacz temat informacje o [zabezpieczeniach częściowej relacji zaufania WPF](../wpf-partial-trust-security.md).

<a name="Navigating_to_Objects"></a>

### <a name="navigating-to-custom-objects"></a>Nawigowanie do obiektów niestandardowych

Jeśli masz dane przechowywane jako obiekty niestandardowe, jednym ze sposobów wyświetlania tych danych jest utworzenie <xref:System.Windows.Controls.Page> z zawartością powiązaną z tymi obiektami (zobacz temat [powiązanie danych — omówienie](../data/data-binding-overview.md)). Jeśli nie potrzebujesz nakładu na tworzenie całej strony tylko w celu wyświetlenia obiektów, możesz przejść bezpośrednio do nich.

Rozważmy klasę `Person`, która jest zaimplementowana w poniższym kodzie.

[!code-csharp[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/Person.cs#personclasscode)]
[!code-vb[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/Person.vb#personclasscode)]

Aby przejść do niego, należy wywołać metodę <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A?displayProperty=nameWithType>, jak pokazano w poniższym kodzie.

[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject1)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject2)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject3)]

[!code-csharp[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml.cs#pagethatnavstoobjectcodebehind)]
[!code-vb[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/HomePage.xaml.vb#pagethatnavstoobjectcodebehind)]

Na poniższej ilustracji przedstawiono wynik.

![Strona, która nawiguje do klasy](./media/navigation-overview/page-navigates-to-an-object.png "jest przykładem strony, która nawiguje do obiektu.")

Na tym rysunku widać, że nie są wyświetlane żadne przydatne elementy. W rzeczywistości wyświetlana wartość jest wartością zwracaną metody `ToString` dla obiektu **osoby** ; Domyślnie jest to jedyna wartość, która może być używana przez [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] do reprezentowania obiektu. Można przesłonić metodę `ToString`, aby zwracała bardziej zrozumiałe informacje, choć będzie ona nadal tylko wartością ciągu. Jedną z technik, z których można skorzystać, wykorzystując możliwości prezentacji [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], jest użycie szablonu danych. Można zaimplementować szablon danych, który [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] może skojarzyć z obiektem określonego typu. Poniższy kod przedstawia szablon danych dla obiektu `Person`.

[!code-xaml[NavigateToObjectSnippets#DataTemplateMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/App.xaml#datatemplatemarkup)]

W tym miejscu szablon danych jest skojarzony z typem `Person` przy użyciu rozszerzenia znaczników `x:Type` w atrybucie `DataType`. Następnie szablon danych wiąże elementy `TextBlock` (patrz <xref:System.Windows.Controls.TextBlock>) z właściwościami klasy `Person`. Na poniższej ilustracji przedstawiono zaktualizowany wygląd obiektu `Person`.

![Przechodzenie do klasy, która ma szablon danych](./media/navigation-overview/navigating-to-a-class.png "przechodzenia do klasy, która ma szablon danych.")

Zaletą tej techniki jest spójność, którą uzyskuje się dzięki możliwości ponownego użycia szablonu danych w celu spójnego wyświetlania obiektów w dowolnym miejscu w aplikacji.

Aby uzyskać więcej informacji na temat szablonów danych, zobacz [tworzenia szablonów danych — omówienie](../data/data-templating-overview.md).

<a name="Security"></a>

## <a name="security"></a>Zabezpieczenia

Obsługa nawigacji [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umożliwia przechodzenie do [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] przez Internet i umożliwia aplikacjom obsługę zawartości innej firmy. Aby chronić aplikacje i użytkowników przed szkodliwym zachowaniem, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] oferuje różne funkcje zabezpieczeń omówione w temacie [zabezpieczenia](../security-wpf.md) i [częściowe zaufanie WPF](../wpf-partial-trust-security.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Application.SetCookie%2A>
- <xref:System.Windows.Application.GetCookie%2A>
- [Omówienie zarządzania aplikacjami](application-management-overview.md)
- [Identyfikatory URI pakietów w WPF](pack-uris-in-wpf.md)
- [Omówienie nawigacji strukturalnej](structured-navigation-overview.md)
- [Omówienie topologii nawigacji](navigation-topologies-overview.md)
- [Tematy porad](navigation-how-to-topics.md)
- [Wdrażanie aplikacji WPF](deploying-a-wpf-application-wpf.md)
