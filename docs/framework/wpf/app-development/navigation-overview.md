---
title: Przegląd Nawigacja
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
ms.openlocfilehash: ee2f6050eeea6eec840156ed5dce9fb9b6172149
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796864"
---
# <a name="navigation-overview"></a>Przegląd Nawigacja

Windows Presentation Foundation (WPF) obsługuje nawigację w stylu przeglądarki, która może być używana w dwóch typach aplikacji: Aplikacje autonomiczne i [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]. Aby spakować zawartość na potrzeby nawigacji [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , <xref:System.Windows.Controls.Page> udostępnia klasę. Można przechodzić z jednego <xref:System.Windows.Controls.Page> do drugiego, <xref:System.Windows.Documents.Hyperlink>korzystając z, lub <xref:System.Windows.Navigation.NavigationService>programowo, przy użyciu. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]program używa dziennika do zapamiętania stron, które zostały przeodwiedzone i aby przejść z powrotem do nich.

<xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.Hyperlink> [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], <xref:System.Windows.Navigation.NavigationService>, i arkusz stanowi rdzeń pomocy technicznej dla nawigacji oferowanej przez program. To omówienie zawiera szczegółowe informacje o tych funkcjach przed zaawansowaną obsługą nawigacji, która [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] obejmuje nawigację do luźnych plików, plików HTML i obiektów.

> [!NOTE]
> W tym temacie termin "Browser" dotyczy tylko przeglądarek, które mogą hostować [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacje, które obecnie obejmują [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] i Firefox. W przypadku [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , gdy konkretne funkcje są obsługiwane tylko przez określoną przeglądarkę, wersja przeglądarki jest nazywana.

## <a name="navigation-in-wpf-applications"></a>Nawigacja w aplikacjach WPF

Ten temat zawiera omówienie możliwości nawigacji kluczy w programie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Te funkcje są dostępne zarówno dla aplikacji autonomicznych [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], jak i, chociaż w tym temacie przedstawiono je w [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]kontekście.

> [!NOTE]
> W tym temacie omówiono sposób kompilowania i wdrażania [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Aby uzyskać więcej informacji [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]na temat, zobacz temat [WPF XAML przeglądarki Applications Overview](wpf-xaml-browser-applications-overview.md).

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

W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]programie można przechodzić do kilku typów zawartości, które obejmują .NET Framework obiektów, obiektów niestandardowych, wartości wyliczenia, kontrolek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] użytkownika, plików i plików HTML. Należy jednak się przekonać, że najpopularniejszym i wygodnym sposobem spakowania zawartości jest użycie <xref:System.Windows.Controls.Page>. Ponadto wdraża <xref:System.Windows.Controls.Page> funkcje specyficzne dla nawigacji, aby zwiększyć ich wygląd i uprościć programowanie.

Korzystając <xref:System.Windows.Controls.Page>z programu, można deklaratywnie zaimplementować [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stronę nawigacji zawartości przy użyciu oznaczeń takich jak następujące.

[!code-xaml[NavigationOverviewSnippets#Page1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page1.xaml#page1xaml)]

Obiekt <xref:System.Windows.Controls.Page> , który jest zaimplementowany [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w znaczniku, ma `Page` jako element główny i [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wymaga [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] deklaracji przestrzeni nazw. `Page` Element zawiera zawartość, do której chcesz przejść i wyświetlić. Zawartość można dodać, ustawiając `Page.Content` element właściwości, jak pokazano w poniższej tabeli.

[!code-xaml[NavigationOverviewSnippets#Page2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page2.xaml#page2xaml)]

`Page.Content`może zawierać tylko jeden element podrzędny; w poprzednim przykładzie zawartość jest pojedynczym ciągiem "Hello, Page!" W tym przypadku zwykle jest używana kontrolka układu jako element podrzędny (zobacz [Układ](../advanced/layout.md)), aby zawierać i redagować zawartość.

Elementy `Page` podrzędne elementu są uważane za zawartość <xref:System.Windows.Controls.Page> a i, w związku z tym, nie trzeba używać jawnej `Page.Content` deklaracji. Następujący znacznik jest deklaratywną równoważną z poprzednim przykładem.

[!code-xaml[NavigationOverviewSnippets#Page3XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page3.xaml#page3xaml)]

W tym przypadku `Page.Content` jest automatycznie ustawiany z elementami `Page` podrzędnymi elementu. Aby uzyskać więcej informacji, zobacz artykuł [model zawartości WPF](../controls/wpf-content-model.md).

Tylko <xref:System.Windows.Controls.Page> znaczników jest przydatne do wyświetlania zawartości. <xref:System.Windows.Controls.Page> Można jednak również wyświetlić kontrolki, które umożliwiają użytkownikom interakcję ze stroną i mogą reagować na interakcję użytkownika przez obsługę zdarzeń i wywoływanie logiki aplikacji. Interaktywny <xref:System.Windows.Controls.Page> jest implementowany przy użyciu kombinacji znaczników i kodu, jak pokazano w poniższym przykładzie.

[!code-xaml[XBAPAppDefSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml#homepagemarkup)]

[!code-csharp[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml.cs#homepagecodebehind)]
[!code-vb[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/HomePage.xaml.vb#homepagecodebehind)]

Aby umożliwić współdziałanie pliku znaczników i pliku związanego z kodem, wymagana jest następująca konfiguracja:

- W znaczniku `Page` element musi `x:Class` zawierać atrybut. Po skompilowaniu aplikacji istnienie `x:Class` w pliku znaczników powoduje [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] utworzenie `partial` klasy, która pochodzi od <xref:System.Windows.Controls.Page> i ma nazwę, która jest określona przez `x:Class` atrybut. Wymaga to dodania [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] deklaracji przestrzeni nazw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dla schematu ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ). Wygenerowana `partial` Klasa implementuje `InitializeComponent`, która jest wywoływana, aby zarejestrować zdarzenia i ustawić właściwości zaimplementowane w znaczniku.

- W kodzie, Klasa musi być `partial` klasą o tej samej nazwie, która jest określona `x:Class` przez atrybut w znaczniku i musi pochodzić od <xref:System.Windows.Controls.Page>. Pozwala to skojarzyć plik związany z kodem z `partial` klasą wygenerowaną dla pliku znaczników podczas kompilowania aplikacji (zobacz Kompilowanie [aplikacji WPF](building-a-wpf-application-wpf.md)).

- W kodzie, <xref:System.Windows.Controls.Page> Klasa musi implementować konstruktora, który `InitializeComponent` wywołuje metodę. `InitializeComponent`jest implementowana przez wygenerowaną `partial` klasę pliku znaczników do rejestrowania zdarzeń i ustawiania właściwości, które są zdefiniowane w znaczniku.

> [!NOTE]
> Po dodaniu nowego <xref:System.Windows.Controls.Page> elementu do projektu za pomocą [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]programu, <xref:System.Windows.Controls.Page> jest zaimplementowany przy użyciu znaczników i kodu, i zawiera konfigurację niezbędną do utworzenia skojarzenia między plikami znaczników i kodu jako opisano tutaj.

Gdy masz, możesz <xref:System.Windows.Controls.Page>przejść do tego elementu. Aby określić pierwszy <xref:System.Windows.Controls.Page> , do którego aplikacji nawiguje, należy skonfigurować przycisk Uruchom <xref:System.Windows.Controls.Page>.

<a name="Configuring_a_Start_Page"></a>

### <a name="configuring-a-start-page"></a>Konfigurowanie strony początkowej

[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]Wymagaj, aby pewna ilość infrastruktury aplikacji była hostowana w przeglądarce. W programie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Klasajestczęścią definicji aplikacji, która ustanawia wymaganą infrastrukturę aplikacji (zobacz [Omówienie zarządzania aplikacjami).](application-management-overview.md) <xref:System.Windows.Application>

Definicja aplikacji jest zwykle implementowana przy użyciu znaczników i kodu, z plikiem znaczników skonfigurowanym jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `ApplicationDefinition` element. Poniżej znajduje się definicja aplikacji dla programu [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].

[!code-xaml[XBAPAppDefSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

[!code-csharp[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml.cs#xbapapplicationdefinitioncodebehind)]
[!code-vb[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/Application.xaml.vb#xbapapplicationdefinitioncodebehind)]

W celu określenia uruchomienia <xref:System.Windows.Controls.Page>, który jest ładowany automatycznie podczas [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] uruchamiania, <xref:System.Windows.Controls.Page> możeużyćjegodefinicjiaplikacji.[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] W tym <xref:System.Windows.Application.StartupUri%2A> [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] celu należy ustawić właściwość na wartość dla żądanej <xref:System.Windows.Controls.Page>.

> [!NOTE]
> W większości przypadków <xref:System.Windows.Controls.Page> jest to skompilowane lub wdrożone w aplikacji. W takich [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] przypadkach oznacza to, że <xref:System.Windows.Controls.Page> jest to [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], który jest zgodny ze schematem *pakietu* . Pakiet [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] został dokładniej omówiony w identyfikatorach [URI pakietów w WPF](pack-uris-in-wpf.md). Możesz również przejść do zawartości przy użyciu schematu http, który został omówiony poniżej.

Można ustawić <xref:System.Windows.Application.StartupUri%2A> deklaratywnie w znacznikach, jak pokazano w poniższym przykładzie.

[!code-xaml[NavigationOverviewSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

W tym przykładzie `StartupUri` atrybut jest ustawiony z pakietem [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] względnym, który identyfikuje stronę główna. XAML. Po uruchomieniu [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] programu Strona główna. XAML jest automatycznie przechodź do i wyświetlana. Jest to zademonstrowane na poniższym rysunku, który pokazuje [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] , że został uruchomiony z serwera sieci Web.

![Strona XBAP](./media/navigation-overview/xbap-launched-from-a-web-server.png "Spowoduje to wyświetlenie aplikacji XBAP uruchomionej z serwera sieci Web.")

> [!NOTE]
> Aby uzyskać więcej informacji na temat opracowywania i [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]wdrażania programu, zobacz [Omówienie aplikacji w przeglądarce WPF XAML](wpf-xaml-browser-applications-overview.md) i [wdrażanie aplikacji WPF](deploying-a-wpf-application-wpf.md).

<a name="ConfiguringAXAMLPage"></a>

### <a name="configuring-the-host-windows-title-width-and-height"></a>Konfigurowanie tytułu, szerokości i wysokości okna hosta

Jednym z nich może być zauważono od poprzedniego rysunku, że tytuł przeglądarki i panelu karty jest [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]dla. Poza tym, tytuł nie jest atrakcyjny ani informacyjny. Z tego powodu <xref:System.Windows.Controls.Page> oferuje sposób zmiany tytułu przez <xref:System.Windows.Controls.Page.WindowTitle%2A> ustawienie właściwości. Ponadto można skonfigurować szerokość i wysokość okna przeglądarki przez ustawienie <xref:System.Windows.Controls.Page.WindowWidth%2A> i <xref:System.Windows.Controls.Page.WindowHeight%2A>, odpowiednio.

<xref:System.Windows.Controls.Page.WindowTitle%2A>, <xref:System.Windows.Controls.Page.WindowWidth%2A> i<xref:System.Windows.Controls.Page.WindowHeight%2A> można ustawić deklaratywnie w znacznikach, jak pokazano w poniższym przykładzie.

[!code-xaml[NavigationOverviewSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/HomePage.xaml#homepagemarkup)]

Wyniki są pokazane na poniższym rysunku.

![Tytuł okna, wysokość, Szerokość](./media/navigation-overview/window-title-width-height.png "Spowoduje to wyświetlenie tytułu, wysokości i szerokości okna, które można skonfigurować.")

<a name="NavigatingBetweenXAMLPages"></a>

### <a name="hyperlink-navigation"></a>Nawigacja hiperlinków

Typowy [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] zawiera kilka stron. Najprostszym sposobem przejścia z jednej strony do innej jest użycie <xref:System.Windows.Documents.Hyperlink>. Można deklaratywnie dodać <xref:System.Windows.Documents.Hyperlink> do a <xref:System.Windows.Controls.Page> za pomocą `Hyperlink` elementu, który jest pokazywany w poniższej tabeli.

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

`Hyperlink` Element wymaga następujących elementów:

- Pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , do którego <xref:System.Windows.Controls.Page> zostanie przewidziana wartość określona przez `NavigateUri` atrybut.

- Zawartość, którą użytkownik może kliknąć, aby zainicjować nawigację, na przykład tekst i obrazy (dla zawartości, którą `Hyperlink` może zawierać element, zobacz <xref:System.Windows.Documents.Hyperlink>).

Na poniższej ilustracji przedstawiono obiekt [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] <xref:System.Windows.Controls.Page> z, który ma <xref:System.Windows.Documents.Hyperlink>.

![Strona z hiperłączem](./media/navigation-overview/xbap-with-a-page-with-a-hyperlink.png "Spowoduje to wyświetlenie aplikacji XBAP ze stroną z hiperłączem.")

Zgodnie <xref:System.Windows.Documents.Hyperlink> z oczekiwaniami, kliknięcie [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] powoduje przejście <xref:System.Windows.Controls.Page> do elementu, który jest identyfikowany przez `NavigateUri` atrybut. Ponadto dodaje wpis dla poprzedniego <xref:System.Windows.Controls.Page> elementu do listy ostatnich stron w [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]. [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Jest to pokazane na poniższej ilustracji.

![Przyciski Wstecz i dalej](./media/navigation-overview/back-and-forward-navigation.png "Przejdź do przycisków Wstecz i do przodu.")

Również obsługa nawigacji z jednego <xref:System.Windows.Controls.Page> do drugiego, <xref:System.Windows.Documents.Hyperlink> który obsługuje nawigację fragmentów.

<a name="FragmentNavigation"></a>

### <a name="fragment-navigation"></a>Nawigacja fragmentów

*Nawigacja fragmentów* to Nawigacja do fragmentu zawartości w bieżącej <xref:System.Windows.Controls.Page> lub innej. <xref:System.Windows.Controls.Page> W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]programie fragment zawartości to zawartość, która jest zawarta w nazwanym elemencie. Nazwany element to element, który ma `Name` ustawiony atrybut. Poniższe znaczniki pokazują nazwany `TextBlock` element, który zawiera fragment zawartości.

[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup2)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup3)]

Aby można było przejść do fragmentu zawartości `NavigateUri` , atrybut musi zawierać następujące elementy: <xref:System.Windows.Documents.Hyperlink>

- [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Elementuzelementemzfragmentemzawartości,<xref:System.Windows.Controls.Page> do którego chcesz przejść.

- A "#" character.

- Nazwa elementu w <xref:System.Windows.Controls.Page> elemencie, który zawiera fragment zawartości.

Fragment [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] ma następujący format.

*PageURI* `#` *ElementName*

Poniżej przedstawiono przykład `Hyperlink` , który jest skonfigurowany do przechodzenia do fragmentu zawartości.

[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml1)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml2)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml3)]

> [!NOTE]
> W tej sekcji opisano domyślną implementację nawigacji fragmentów w programie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]umożliwia również wdrożenie własnego schematu nawigacji fragmentu, który w części wymaga obsługi <xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType> zdarzenia.

> [!IMPORTANT]
> Można przechodzić do fragmentów na [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] luźnych stronach (pliki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] `Page` tylko do znaczników jako element główny) tylko wtedy, gdy strony można przeglądać za pośrednictwem protokołu HTTP.
>
> Jednak luźna [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strona może przechodzić do własnych fragmentów.

<a name="NavigationService"></a>

### <a name="navigation-service"></a>Usługa nawigacji

Pozwala użytkownikowi na zainicjowanie nawigacji do konkretnej <xref:System.Windows.Controls.Page>, pracy lokalizowania i pobierania <xref:System.Windows.Navigation.NavigationService> strony jest wykonywana przez klasę. <xref:System.Windows.Documents.Hyperlink> Zasadniczo zapewnia możliwość przetwarzania żądania nawigacji w imieniu kodu klienta, takiego <xref:System.Windows.Documents.Hyperlink>jak. <xref:System.Windows.Navigation.NavigationService> <xref:System.Windows.Navigation.NavigationService> Ponadto implementuje obsługę wyższego poziomu na potrzeby śledzenia i wpływania na żądanie nawigacji.

<xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Page> [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]Gdy zostanie kliknięty, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] program wywołuje wyszukiwanie i pobierze w określonym pakiecie. <xref:System.Windows.Documents.Hyperlink> Pobrane <xref:System.Windows.Controls.Page> zostało przekonwertowane na drzewo obiektów, których obiektem głównym jest wystąpienie pobrane <xref:System.Windows.Controls.Page>. Odwołanie do obiektu głównego <xref:System.Windows.Controls.Page> jest przechowywane <xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType> we właściwości. Pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla zawartości, do której został przeszedł, jest przechowywany <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> we właściwości, podczas gdy <xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType> program przechowuje pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla ostatniej strony, do której przeszedł.

> [!NOTE]
> Aplikacja może mieć więcej niż jedną aktywną <xref:System.Windows.Navigation.NavigationService>aplikację. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Aby uzyskać więcej informacji, zobacz [hosty nawigacji](#Navigation_Hosts) w dalszej części tego tematu.

<a name="Programmatic_Navigation_with_the_Navigation_Service"></a>

### <a name="programmatic-navigation-with-the-navigation-service"></a>Nawigacja programowa przy użyciu usługi nawigacji

Nie musisz wiedzieć <xref:System.Windows.Navigation.NavigationService> o tym, czy nawigacja jest implementowana w znakach przy użyciu <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.Hyperlink> ponieważ używa <xref:System.Windows.Navigation.NavigationService> w Twoim imieniu. Oznacza to, że pod warunkiem, że bezpośredni lub pośredni element nadrzędny obiektu <xref:System.Windows.Documents.Hyperlink> jest hostem nawigacyjnym (zobacz [hosty nawigacji](#Navigation_Hosts)), będzie w stanie znaleźć i użyć usługi nawigacji hosta nawigacji, <xref:System.Windows.Documents.Hyperlink> aby przetworzyć żądanie nawigacji.

Istnieją jednak sytuacje, w których należy bezpośrednio korzystać <xref:System.Windows.Navigation.NavigationService> z programu, w tym następujące:

- Gdy konieczne jest utworzenie wystąpienia <xref:System.Windows.Controls.Page> przy użyciu konstruktora bez parametrów.

- Gdy musisz ustawić właściwości <xref:System.Windows.Controls.Page> przed przechodzeniem do niego.

- Gdy to <xref:System.Windows.Controls.Page> , do którego należy przejść, można określić tylko w czasie wykonywania.

W takich sytuacjach należy napisać kod, aby programowo zainicjować nawigację przez wywołanie <xref:System.Windows.Navigation.NavigationService.Navigate%2A> metody <xref:System.Windows.Navigation.NavigationService> obiektu. Wymagające pobrania odwołania do <xref:System.Windows.Navigation.NavigationService>.

#### <a name="getting-a-reference-to-the-navigationservice"></a>Pobieranie odwołania do NavigationService

Przyczyny omówione w sekcji [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [hosty nawigacji](#Navigation_Hosts) mogą mieć więcej niż jedną <xref:System.Windows.Navigation.NavigationService>aplikację. Oznacza to, że kod wymaga metody znalezienia a <xref:System.Windows.Navigation.NavigationService>, która <xref:System.Windows.Navigation.NavigationService> zwykle przeszedł do bieżącego <xref:System.Windows.Controls.Page>. Możesz uzyskać odwołanie do a <xref:System.Windows.Navigation.NavigationService> przez `static` <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A?displayProperty=nameWithType> wywołanie metody. Aby uzyskać <xref:System.Windows.Navigation.NavigationService> ten, który przeszedł do określonego <xref:System.Windows.Controls.Page>, <xref:System.Windows.Controls.Page> przekazujesz odwołanie do obiektu jako argument <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A> metody. Poniższy kod pokazuje, <xref:System.Windows.Navigation.NavigationService> jak uzyskać dla bieżącego. <xref:System.Windows.Controls.Page>

[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPage.xaml.vb#getnscodebehind2)]

<xref:System.Windows.Navigation.NavigationService> Jako skrót do znajdowania dla a <xref:System.Windows.Controls.Page>, <xref:System.Windows.Controls.Page> implementuje <xref:System.Windows.Controls.Page.NavigationService%2A> właściwość. Pokazano to w poniższym przykładzie.

[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPageShortCut.xaml.vb#getnsshortcutcodebehind2)]

> [!NOTE]
> Element <xref:System.Windows.Controls.Page> a może uzyskać odwołanie do niego <xref:System.Windows.Navigation.NavigationService> tylko wtedy <xref:System.Windows.Controls.Page> , <xref:System.Windows.FrameworkElement.Loaded> gdy wywołuje zdarzenie.

#### <a name="programmatic-navigation-to-a-page-object"></a>Programistyczne nawigowanie do obiektu strony

Poniższy przykład pokazuje, <xref:System.Windows.Navigation.NavigationService> jak używać do programistycznego nawigowania <xref:System.Windows.Controls.Page>do. Nawigacja programowa jest wymagana, ponieważ <xref:System.Windows.Controls.Page> element, do którego jest przeznaczony do przechodzenia, można utworzyć wystąpienie tylko przy użyciu jednego konstruktora bez parametrów. <xref:System.Windows.Controls.Page> Za pomocą konstruktora bez parametrów jest pokazywany w następujących znakach i kodzie.

[!code-xaml[NavigationOverviewSnippets#PageWithNonDefaultConstructorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml#pagewithnondefaultconstructorxaml)]

[!code-csharp[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml.cs#pagewithnondefaultconstructorcodebehind)]
[!code-vb[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithNonDefaultConstructor.xaml.vb#pagewithnondefaultconstructorcodebehind)]

Powoduje to przejście do obiektu <xref:System.Windows.Controls.Page> zkonstruktorembezparametrów,któryjestwyświetlanywnastępującychznakach<xref:System.Windows.Controls.Page> i kodzie.

[!code-xaml[NavigationOverviewSnippets#NSNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml#nsnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml.cs#nsnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSNavigationPage.xaml.vb#nsnavigationpagecodebehind)]

Po kliknięciu <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page> na tej stronie nawigacja jest inicjowana przez utworzenie wystąpienia elementu, aby przejść do użycia konstruktora <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> bez parametrów i wywołania metody. <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Navigation.NavigationService.Navigate%2A>akceptuje odwołanie do obiektu, do którego <xref:System.Windows.Navigation.NavigationService> będzie nawigować, a nie do pakietu. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]

#### <a name="programmatic-navigation-with-a-pack-uri"></a>Nawigacja programowa przy użyciu identyfikatora URI pakietu

Jeśli konieczne jest skonstruowanie pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] programowo (gdy można określić tylko pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] w czasie wykonywania, na przykład) <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> , można użyć metody. Pokazano to w poniższym przykładzie.

[!code-xaml[NavigationOverviewSnippets#NSUriNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml#nsurinavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml.cs#nsurinavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSUriNavigationPage.xaml.vb#nsurinavigationpagecodebehind)]

#### <a name="refreshing-the-current-page"></a>Odświeżanie bieżącej strony

Program nie [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> jest pobierany, jeśli ma taki sam pakiet jak pakiet, który jest przechowywany we właściwości. <xref:System.Windows.Controls.Page> Aby wymusić [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ponowne pobranie bieżącej strony, można <xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType> wywołać metodę, jak pokazano w poniższym przykładzie.

[!code-xaml[NavigationOverviewSnippets#NSRefreshNavigationPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml#nsrefreshnavigationpagexaml1)]

[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind1)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind2)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind2)]

<a name="Navigation_Lifetime"></a>

### <a name="navigation-lifetime"></a>Okres istnienia nawigacji

Istnieje wiele sposobów na zainicjowanie nawigacji, jak widać. Po zainicjowaniu nawigacji, gdy nawigacja jest w toku, można śledzić i wpływać na nawigację przy użyciu następujących zdarzeń, które są <xref:System.Windows.Navigation.NavigationService>implementowane przez:

- <xref:System.Windows.Navigation.NavigationService.Navigating>. Występuje po zażądaniu nowej nawigacji. Może służyć do anulowania nawigacji.

- <xref:System.Windows.Navigation.NavigationService.NavigationProgress>. Występuje okresowo podczas pobierania, aby zapewnić informacje o postępie nawigacji.

- <xref:System.Windows.Navigation.NavigationService.Navigated>. Występuje, gdy strona została umieszczona i pobrana.

- <xref:System.Windows.Navigation.NavigationService.NavigationStopped>. Występuje, gdy Nawigacja zostanie zatrzymana (przez <xref:System.Windows.Navigation.NavigationService.StopLoading%2A>wywołanie) lub gdy żąda się nowej nawigacji, gdy trwa bieżące nawigowanie.

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

<xref:System.Windows.Navigation.NavigationService> Za<xref:System.Windows.Application> każdym razem, gdy wywołuje zdarzenie, Klasa wywołuje odpowiednie zdarzenie. <xref:System.Windows.Controls.Frame>i <xref:System.Windows.Navigation.NavigationWindow> oferują te same zdarzenia w celu wykrywania nawigacji w obrębie odpowiednich zakresów.

W niektórych przypadkach <xref:System.Windows.Controls.Page> może zainteresować te zdarzenia. Na przykład <xref:System.Windows.Controls.Page> może <xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType> obsłużyć zdarzenie, aby określić, czy anulować nawigację od samego siebie. Pokazano to w poniższym przykładzie.

[!code-xaml[NavigationOverviewSnippets#CancelNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml#cancelnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml.cs#cancelnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/CancelNavigationPage.xaml.vb#cancelnavigationpagecodebehind)]

Jeśli zarejestrowano procedurę obsługi ze zdarzeniem nawigacji z <xref:System.Windows.Controls.Page>, jak w poprzednim przykładzie, należy również wyrejestrować procedurę obsługi zdarzeń. Jeśli tego nie zrobisz, mogą wystąpić skutki uboczne w odniesieniu do sposobu <xref:System.Windows.Controls.Page> , w jaki [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] przechodzenie nawigacji przez nawigację przy użyciu dziennika.

<a name="NavigationHistory"></a>

### <a name="remembering-navigation-with-the-journal"></a>Zapamiętywanie nawigacji przy użyciu dziennika

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]używa dwóch stosów do zapamiętania stron, z których pochodzą: stos zaplecza i stos do przodu. Po przejściu <xref:System.Windows.Controls.Page> z bieżącego do nowego <xref:System.Windows.Controls.Page> lub do istniejącego <xref:System.Windows.Controls.Page>elementu, bieżąca <xref:System.Windows.Controls.Page> jest dodawana do *stosu back*. <xref:System.Windows.Controls.Page> Po przejściu z bieżącego z powrotem do poprzedniego <xref:System.Windows.Controls.Page>, bieżąca <xref:System.Windows.Controls.Page> wartość jest dodawana do stosu do *przodu*. Stos zaplecza, stos przesyłania dalej i funkcje do zarządzania nimi są określane zbiorczo jako dziennik. Każdy element w stosie zaplecza i stos do przodu jest wystąpieniem <xref:System.Windows.Navigation.JournalEntry> klasy i jest określany jako wpis w *dzienniku*.

#### <a name="navigating-the-journal-from-internet-explorer"></a>Nawigowanie po dzienniku z programu Internet Explorer

Koncepcyjnie dziennik działa tak samo, jak przyciski **Wstecz** i **dalej** w tym programie [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] . Są one pokazane na poniższej ilustracji.

![Przyciski Wstecz i dalej](./media/navigation-overview/back-and-forward-navigation.png "Przejdź do przycisków Wstecz i do przodu.")

W [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] przypadku programu hostowanego [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]przez [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] program[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]integruje dziennik z nawigacją. Pozwala to użytkownikom na [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] nawigowanie na stronach przy użyciu przycisków **Wstecz**, **do przodu**i **ostatnich stron** w programie [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]. Dziennik nie jest zintegrowany [!INCLUDE[TLA2#tla_ie6](../../../../includes/tla2sharptla-ie6-md.md)] w taki sam sposób, jak w przypadku programu [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)] lub Internet Explorer 8. Zamiast tego [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]renderuje zastępczą nawigację. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]

> [!IMPORTANT]
> W [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]programie, gdy użytkownik nawiguje [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]do i z powrotem do, tylko wpisy dziennika dla stron, które nie były aktywne, są zachowywane w dzienniku. Aby poznać dyskusję na temat utrzymywania stron, zobacz [okres istnienia strony i dziennik](#PageLifetime) w dalszej części tego tematu.

Domyślnie tekst dla <xref:System.Windows.Controls.Page> każdego, który pojawia się na [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] liście [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] **ostatnio używanych stron** , jest dla elementu. <xref:System.Windows.Controls.Page> W wielu przypadkach nie jest to szczególnie istotne dla użytkownika. Na szczęście można zmienić tekst przy użyciu jednej z następujących opcji:

1. Dołączona `JournalEntry.Name` wartość atrybutu.

2. Wartość `Page.Title` atrybutu.

3. Wartość atrybutu i dla bieżącego <xref:System.Windows.Controls.Page>. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] `Page.WindowTitle`

4. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Dla bieżącego<xref:System.Windows.Controls.Page>. (Domyślnie)

Kolejność, w jakiej są wyświetlane opcje, jest zgodna z kolejnością pierwszeństwa podczas wyszukiwania tekstu. Na przykład, jeśli `JournalEntry.Name` jest ustawiona, inne wartości są ignorowane.

Poniższy przykład używa `Page.Title` atrybutu, aby zmienić tekst wyświetlany dla wpisu dziennika.

[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup2)]

[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind1)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind2)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind2)]

#### <a name="navigating-the-journal-using-wpf"></a>Nawigowanie po arkuszu przy użyciu WPF

Mimo że użytkownik może nawigować po arkuszu przy użyciu stron z **tyłu**, **do przodu**i **ostatnich** w [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]programie, można także nawigować po dzienniku przy użyciu mechanizmów deklaratywnych i programistycznych [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]zapewnianych przez program. Jednym z powodów, aby to zrobić, jest zapewnienie [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] niestandardowej nawigacji na stronach.

Obsługę nawigacji w dzienniku można deklaratywnie dodać przy użyciu poleceń nawigacyjnych uwidocznionych <xref:System.Windows.Input.NavigationCommands>przez program. Poniższy przykład ilustruje sposób użycia `BrowseBack` polecenia nawigacji.

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

[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Weź pod uwagę kilka stron zawierających rozbudowaną zawartość, w tym grafiki, animacje i multimedia. Użycie pamięci dla stron takich jak takie może być bardzo duże, szczególnie w przypadku używania nośnika wideo i audio. Mając na względzie, że strony, do których przeprowadził przechodzenie, [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] mogą szybko korzystać z dużej i zauważalnej ilości pamięci.

Z tego powodu domyślne zachowanie dziennika polega na <xref:System.Windows.Controls.Page> zarejestrowaniu metadanych w każdym wpisie dziennika, a nie w odwołaniu <xref:System.Windows.Controls.Page> do obiektu. Po przejściu do wpisu dziennika, jego <xref:System.Windows.Controls.Page> metadane są używane do tworzenia nowego wystąpienia określonego. <xref:System.Windows.Controls.Page> W związku z tym każdy <xref:System.Windows.Controls.Page> , który jest przestawiony, ma okres istnienia opisany na poniższej ilustracji.

![Okres istnienia strony](./media/navigation-overview/navigated-page-lifetime.png "Pokazuje okres istnienia strony.")

Chociaż korzystanie z domyślnego zachowania rejestrowania może zaoszczędzić przy zużyciu pamięci, wydajność renderowania na stronie może ulec zmniejszeniu. ponowne wystąpienie <xref:System.Windows.Controls.Page> może być czasochłonne, szczególnie jeśli ma dużą zawartość. Jeśli musisz zachować <xref:System.Windows.Controls.Page> wystąpienie w dzienniku, możesz narysować na dwie techniki. Najpierw można programistycznie nawigować do <xref:System.Windows.Controls.Page> obiektu przez <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> wywołanie metody.

Następnie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] można określić, że zachować wystąpienie <xref:System.Windows.Controls.Page> obiektu w dzienniku przez ustawienie <xref:System.Windows.Controls.Page.KeepAlive%2A> właściwości na `true` (wartość domyślna to `false`). Jak pokazano w poniższym przykładzie, można ustawić <xref:System.Windows.Controls.Page.KeepAlive%2A> deklaratywnie w znaczniku.

[!code-xaml[NavigationOverviewSnippets#KeepAlivePageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/KeepAlivePage.xaml#keepalivepagexaml)]

Okres istnienia <xref:System.Windows.Controls.Page> aktywności jest bardzo odmienny niż ten, który nie jest. Podczas pierwszego okresu <xref:System.Windows.Controls.Page> utrzymywania aktywności jest przechodzenie do, jest tworzone w taki sam sposób, <xref:System.Windows.Controls.Page> jak to, które nie jest aktywne. Jednak ponieważ wystąpienie <xref:System.Windows.Controls.Page> jest przechowywane w dzienniku, nigdy nie jest tworzone ponownie dla tak długo, jak pozostało w dzienniku. W związku z tym, <xref:System.Windows.Controls.Page> Jeśli istnieje logika inicjalizacji, która musi być wywoływana <xref:System.Windows.Controls.Page> za każdym razem, gdy jest przenoszona do, należy przenieść ją z konstruktora <xref:System.Windows.FrameworkElement.Loaded> do procedury obsługi zdarzenia. Jak pokazano na poniższej ilustracji, <xref:System.Windows.FrameworkElement.Loaded> zdarzenia i <xref:System.Windows.FrameworkElement.Unloaded> <xref:System.Windows.Controls.Page> nadal są wywoływane każdorazowo po przejściu do i z, odpowiednio.

Po podniesieniu ![ładowanych i niezaładowanych zdarzeń](./media/navigation-overview/loaded-and-unloaded-events.png "Załadowane i niezaładowane zdarzenia są wywoływane, gdy strona jest przenoszona do i z.")

Gdy program nie jest aktywny, nie należy wykonywać żadnej z następujących czynności: <xref:System.Windows.Controls.Page>

- Zapisz odwołanie do niego lub jego część.

- Zarejestruj procedury obsługi zdarzeń ze zdarzeniami, które nie zostały zaimplementowane przez ten program.

Wykonanie jednej z tych opcji spowoduje utworzenie odwołań, które <xref:System.Windows.Controls.Page> wymuszają zachowywanie w pamięci, nawet po jej usunięciu z dziennika.

Ogólnie rzecz biorąc, należy preferować domyślne <xref:System.Windows.Controls.Page> zachowanie <xref:System.Windows.Controls.Page> nieutrzymywania aktywności. Ma to jednak konsekwencje stanu omówione w następnej sekcji.

<a name="RetainingContentStateWithNavigationHistory"></a>

### <a name="retaining-content-state-with-navigation-history"></a>Zachowywanie stanu zawartości przy użyciu historii nawigacji

Jeśli element <xref:System.Windows.Controls.Page> nie jest aktywny i ma kontrolki, które zbierają dane od użytkownika, co się dzieje z danymi, gdy użytkownik nawiguje z powrotem od i <xref:System.Windows.Controls.Page>do tyłu? W perspektywie środowiska użytkownika użytkownik powinien oczekiwać, że dane wprowadzone wcześniej. Niestety, ze względu na to, <xref:System.Windows.Controls.Page> że nowe wystąpienie programu jest tworzone przy użyciu poszczególnych nawigacji, formanty, w których zbierane są dane, są usuwane, a dane są tracone.

Na szczęście dziennik zapewnia obsługę zapamiętywania danych między <xref:System.Windows.Controls.Page> nawigacjami, w tym danych kontrolnych. W odniesieniu do każdego wpisu <xref:System.Windows.Controls.Page> dziennika dla każdego z nich pełni rolę kontenera <xref:System.Windows.Controls.Page> tymczasowego dla skojarzonego stanu. Poniższe kroki przedstawiają sposób użycia tej pomocy w przypadku <xref:System.Windows.Controls.Page> przejścia z:

1. Wpis dla bieżącego <xref:System.Windows.Controls.Page> zostanie dodany do dziennika.

2. Stan <xref:System.Windows.Controls.Page> jest przechowywany w pozycji dziennika dla tej strony, która jest dodawana do stosu back.

3. Nastąpi przejście do nowego <xref:System.Windows.Controls.Page> .

Po przejściu <xref:System.Windows.Controls.Page> do strony z powrotem do programu przy użyciu dziennika należy wykonać następujące czynności:

1. Zostanie utworzone wystąpienie (górny wpis dziennika na stosie zaplecza). <xref:System.Windows.Controls.Page>

2. Jest odświeżany ze stanem, który został zapisany w pozycji dziennika <xref:System.Windows.Controls.Page>dla. <xref:System.Windows.Controls.Page>

3. <xref:System.Windows.Controls.Page> Jest on przechodzenia z powrotem do.

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Program automatycznie używa tej obsługi, <xref:System.Windows.Controls.Page>gdy są używane następujące kontrolki:

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

Jeśli program <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.ListBox> używa tych kontrolek, dane wprowadzone do nich są zapamiętywane przez nawigację, jak pokazano na poniższym rysunku **kolorze ulubionym.** <xref:System.Windows.Controls.Page>

![Strona z kontrolkami, które zapamiętają stan](./media/navigation-overview/data-remembered-across-page-navigations.png "Wprowadzone dane są zapamiętywane między nawigacjami stron.")

Gdy ma kontrolki inne niż te znajdujące się na poprzedniej liście lub gdy stan jest przechowywany w obiektach niestandardowych, należy napisać kod, aby spowodować, że dziennik zostanie zapamiętany <xref:System.Windows.Controls.Page> dla nawigacji. <xref:System.Windows.Controls.Page>

Jeśli musisz zapamiętać małe fragmenty stanu między <xref:System.Windows.Controls.Page> nawigacjami, możesz użyć właściwości zależności (zobacz <xref:System.Windows.DependencyProperty>) <xref:System.Windows.FrameworkPropertyMetadata.Journal%2A?displayProperty=nameWithType> , które są skonfigurowane z flagą metadanych.

Jeśli stan, który <xref:System.Windows.Controls.Page> należy pamiętać między nawigacjami, składa się z wielu fragmentów danych, może być mniej dużo czasochłonne, aby hermetyzować stan w jednej klasie i <xref:System.Windows.Navigation.IProvideCustomContentState> zaimplementować interfejs.

Jeśli chcesz nawigować <xref:System.Windows.Controls.Page>przez różne stany jednego, bez przechodzenia <xref:System.Windows.Controls.Page> do samego siebie, możesz użyć <xref:System.Windows.Navigation.IProvideCustomContentState> i <xref:System.Windows.Navigation.NavigationService.AddBackEntry%2A?displayProperty=nameWithType>.

<a name="Cookies"></a>

### <a name="cookies"></a>Cookie

Innym sposobem [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] przechowywania danych przez aplikacje jest tworzenie, aktualizowanie i usuwanie plików cookie przy <xref:System.Windows.Application.SetCookie%2A> użyciu metod i <xref:System.Windows.Application.GetCookie%2A> . Pliki cookie, które można utworzyć w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] programie, są tymi samymi plikami cookie, które są używane przez inne typy aplikacji sieci Web; pliki cookie są dowolnymi danymi przechowywanymi przez aplikację na komputerze klienckim w trakcie lub między sesjami aplikacji. Dane plików cookie zazwyczaj przyjmuje postać pary nazwa/wartość w następującym formacie.

*Nazwa* `=` *Wartość*

Gdy dane są przesyłane do <xref:System.Windows.Application.SetCookie%2A>programu, wraz <xref:System.Uri> z lokalizacją, w której ma zostać ustawiony plik cookie, plik cookie jest tworzony w pamięci i jest dostępny tylko w czasie trwania bieżącej sesji aplikacji. Ten typ pliku cookie jest określany jako *plik cookie sesji*.

Aby przechowywać plik cookie między sesjami aplikacji, należy dodać do pliku cookie datę wygaśnięcia, używając następującego formatu.

*NAZWA* `=` *WARTOŚĆ*`; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`

Plik cookie z datą wygaśnięcia jest przechowywany w folderze tymczasowych plików [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] internetowych bieżącej instalacji do momentu wygaśnięcia pliku cookie. Taki plik cookie jest znany jako *trwały plik cookie* , ponieważ utrzymuje się między sesjami aplikacji.

Można pobrać zarówno sesję, jak i trwałe pliki cookie <xref:System.Windows.Application.GetCookie%2A> , wywołując metodę, <xref:System.Uri> przekazując lokalizację, w której ustawiono <xref:System.Windows.Application.SetCookie%2A> plik cookie przy użyciu metody.

Poniżej przedstawiono niektóre sposoby obsługi plików cookie w programie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]:

- [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Aplikacje autonomiczne [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] i mogą zarówno tworzyć pliki cookie, jak i nimi zarządzać.

- Pliki cookie, które są tworzone [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] za pomocą programu, są dostępne z przeglądarki.

- [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]w tej samej domenie można tworzyć i udostępniać pliki cookie.

- [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]a strony HTML z tej samej domeny mogą tworzyć i udostępniać pliki cookie.

- Pliki cookie są wysyłane, gdy [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] i luźne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony tworzą żądania sieci Web.

- Oba elementy najwyższego [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] poziomu [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] i hostowane w elemencie iframe mogą uzyskiwać dostęp do plików cookie.

- Obsługa plików cookie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] w programie jest taka sama dla wszystkich obsługiwanych przeglądarek.

- W [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]systemie Zasady P3P, które odnoszą się do plików cookie, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]są honorowane przez, szczególnie w odniesieniu do podmiotów [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]pierwszej strony i innych firm.

<a name="Structured_Navigation"></a>

### <a name="structured-navigation"></a>Nawigacja strukturalna

Jeśli musisz przekazać dane z jednego <xref:System.Windows.Controls.Page> do drugiego, możesz przekazać dane jako argumenty do konstruktora <xref:System.Windows.Controls.Page>bez parametrów. Należy pamiętać, że w <xref:System.Windows.Controls.Page> przypadku korzystania z tej techniki należy zachować aktywności; Jeśli nie, następnym razem <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page> , gdy przejdziesz do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , ponownie tworzy wystąpienie za pomocą konstruktora bez parametrów.

Alternatywnie, <xref:System.Windows.Controls.Page> można zaimplementować właściwości, które są ustawione z danymi, które muszą zostać przesłane. Jednak rzeczy stają się trudne, gdy konieczne jest <xref:System.Windows.Controls.Page> przekazanie danych z powrotem <xref:System.Windows.Controls.Page> do tego, który przeszedł do niego. Problem polega na tym, że nawigacja nie wspiera natywnie mechanizmów do zagwarantowania, że po przejściu z usługi zostanie zwrócona wartość <xref:System.Windows.Controls.Page> . Zasadniczo nawigacja nie obsługuje semantyki wywołania/powrotu. Aby rozwiązać ten problem, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] program <xref:System.Windows.Navigation.PageFunction%601> udostępnia klasę, której można użyć w celu zapewnienia, <xref:System.Windows.Controls.Page> że element jest zwracany do wartości w sposób przewidywalny i strukturalny. Aby uzyskać więcej informacji, zobacz [Omówienie nawigacji strukturalnej](structured-navigation-overview.md).

<a name="The_NavigationWindow_Class"></a>

## <a name="the-navigationwindow-class"></a>Klasa NavigationWindow

Do tego momentu zobaczysz gamę usług nawigacyjnych, których najprawdopodobniej używasz do kompilowania aplikacji z nawigacją. Te usługi zostały omówione w kontekście [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], chociaż nie są ograniczone do. [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] Nowoczesne systemy operacyjne i aplikacje systemu Windows wykorzystują korzystanie z przeglądarki nowoczesnych użytkowników w celu uwzględnienia nawigacji w stylu przeglądarki w aplikacjach autonomicznych. Typowe przykłady obejmują:

- **Tezaurus słów**: Nawigowanie po wyborach w programie Word.

- **Eksplorator plików**: Nawigowanie po plikach i folderach.

- **Kreatorzy**: Rozdzielenie złożonego zadania na wiele stron, które mogą być przechodzenie między. Przykładem jest Kreator składników systemu Windows, który obsługuje dodawanie i usuwanie funkcji systemu Windows.

Aby włączyć nawigację w stylu przeglądarki do aplikacji autonomicznych, można użyć <xref:System.Windows.Navigation.NavigationWindow> klasy. <xref:System.Windows.Navigation.NavigationWindow>pochodzi z <xref:System.Windows.Window> i rozszerza je o takie samo wsparcie dla nawigacji, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] która zapewnia. Możesz użyć <xref:System.Windows.Navigation.NavigationWindow> jako głównego okna aplikacji autonomicznej lub jako okna pomocniczego, takiego jak okno dialogowe.

Aby zaimplementować <xref:System.Windows.Navigation.NavigationWindow>, jak w przypadku większości klas najwyższego poziomu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] w<xref:System.Windows.Window>( <xref:System.Windows.Controls.Page>,, i tak dalej), należy użyć kombinacji znaczników i kodu. Pokazano to w poniższym przykładzie.

[!code-xaml[IntroToNavNavigationWindowSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml#navigationwindowmarkup)]

[!code-csharp[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml.cs#navigationwindowcodebehind)]
[!code-vb[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/MainWindow.xaml.vb#navigationwindowcodebehind)]

Ten kod tworzy <xref:System.Windows.Navigation.NavigationWindow> automatycznie nawigację do pliku <xref:System.Windows.Controls.Page> (Strona główna <xref:System.Windows.Navigation.NavigationWindow> . XAML) po otwarciu. Jeśli jest głównym oknem aplikacji, można `StartupUri` użyć atrybutu, aby go uruchomić. <xref:System.Windows.Navigation.NavigationWindow> Jest to pokazane w poniższej tabeli.

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchNavWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/App.xaml#applaunchnavwindow)]

Na poniższej ilustracji przedstawiono <xref:System.Windows.Navigation.NavigationWindow> główne okno aplikacji autonomicznej.

![Okno główne](./media/navigation-overview/navigation-window-as-main-window.png "Okno nawigacji jako okno główne")

Na rysunku widać, że <xref:System.Windows.Navigation.NavigationWindow> ma tytuł, mimo że nie został on ustawiony <xref:System.Windows.Navigation.NavigationWindow> w kodzie implementacji z poprzedniego przykładu. Zamiast tego, tytuł jest ustawiany przy użyciu <xref:System.Windows.Controls.Page.WindowTitle%2A> właściwości, która jest pokazana w poniższym kodzie.

[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup1)]
[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup2)]

Ustawienie właściwości <xref:System.Windows.Controls.Page.WindowHeight%2A> <xref:System.Windows.Navigation.NavigationWindow>i ma także wpływ na. <xref:System.Windows.Controls.Page.WindowWidth%2A>

Zwykle należy wdrożyć własne <xref:System.Windows.Navigation.NavigationWindow> , gdy trzeba dostosować jego zachowanie lub jego wygląd. Jeśli nie wykonasz żadnego z tych czynności, możesz użyć skrótu. Jeśli [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] określisz pakiet <xref:System.Windows.Controls.Page> programu <xref:System.Windows.Application.StartupUri%2A> <xref:System.Windows.Application> jako w<xref:System.Windows.Controls.Page>aplikacjiautonomicznej, program automatycznie tworzy dohostowania.<xref:System.Windows.Navigation.NavigationWindow> Poniższe znaczniki pokazują, jak włączyć tę funkcję.

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchPage](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/AnotherApp.xaml#applaunchpage)]

Jeśli chcesz <xref:System.Windows.Navigation.NavigationWindow>, aby okno aplikacji dodatkowej, takie jak okno dialogowe, było, możesz użyć kodu w poniższym przykładzie, aby go otworzyć.

[!code-csharp[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/DialogOwnerWindow.xaml.cs#createnwdialogbox)]
[!code-vb[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/DialogOwnerWindow.xaml.vb#createnwdialogbox)]

Na poniższej ilustracji przedstawiono wynik.

Okno ![dialogowe](./media/navigation-overview/navigation-window-as-dialog-box.png "Okno nawigacyjne jako okno dialogowe")

Jak widać, wyświetlane są <xref:System.Windows.Navigation.NavigationWindow> [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]przyciski do **tyłu** i **do przodu** , które umożliwiają użytkownikom nawigowanie po arkuszu. Te przyciski zapewniają takie samo środowisko użytkownika, jak pokazano na poniższej ilustracji.

![Przyciski Wstecz i dalej w NavigationWindow](./media/navigation-overview/back-and-forward-buttons-in-navigation-window.png "Przyciski Wstecz i dalej w oknie nawigacji")

Jeśli strony zapewniają własną obsługę nawigacji w dzienniku i interfejs użytkownika, można ukryć przyciski **Wstecz** i **do przodu** wyświetlane <xref:System.Windows.Navigation.NavigationWindow> przez ustawienie wartości <xref:System.Windows.Navigation.NavigationWindow.ShowsNavigationUI%2A> właściwości na `false`.

Alternatywnie możesz użyć obsługi dostosowywania w programie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , aby [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zastąpić <xref:System.Windows.Navigation.NavigationWindow> sam siebie.

<a name="Frame_in_Standalone_Applications"></a>

## <a name="the-frame-class"></a>Klasa Frame

Przeglądarka i <xref:System.Windows.Navigation.NavigationWindow> system Windows obsługujący zawartość nawigacji. W niektórych przypadkach aplikacje mają zawartość, która nie musi być hostowana przez całe okno. Zamiast tego taka zawartość jest hostowana w innej zawartości. Możesz wstawić zawartość nawigacji do innej zawartości przy użyciu <xref:System.Windows.Controls.Frame> klasy. <xref:System.Windows.Controls.Frame>zapewnia taką samą obsługę jak <xref:System.Windows.Navigation.NavigationWindow> i [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].

Poniższy przykład pokazuje, jak dodać a <xref:System.Windows.Controls.Frame> <xref:System.Windows.Controls.Page> do `Frame` deklaratywnie przy użyciu elementu.

[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml3)]

Ten `Source` znacznik ustawia atrybut [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] `Frame` elementu z<xref:System.Windows.Controls.Frame>pakietem , dla którego należy najpierw przejść do. <xref:System.Windows.Controls.Page> Na poniższej ilustracji przedstawiono obiekt [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] <xref:System.Windows.Controls.Page> z, który <xref:System.Windows.Controls.Frame> ma przechodzenie między kilka stron.

![Ramka, która przeszła między wieloma stronami](./media/navigation-overview/frame-navigation-between-multiple-pages.png "Spowoduje to wyświetlenie nawigacji między wieloma stronami.")

Nie musisz używać <xref:System.Windows.Controls.Frame> tylko wewnątrz zawartości <xref:System.Windows.Controls.Page>. Jest również często hostować <xref:System.Windows.Controls.Frame> wewnątrz zawartości. <xref:System.Windows.Window>

Domyślnie program <xref:System.Windows.Controls.Frame> używa tylko własnego dziennika w przypadku braku innego dziennika. <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Navigation.NavigationWindow> [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] <xref:System.Windows.Controls.Frame> [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]Jeśli jest częścią zawartości, która znajduje się wewnątrz lub, używa dziennika, który należy do lub. <xref:System.Windows.Controls.Frame> Czasami jednak <xref:System.Windows.Controls.Frame> może być odpowiedzialny za własny dziennik. Jedną z przyczyn tego problemu jest umożliwienie nawigowania w dziennikach na stronach, które są <xref:System.Windows.Controls.Frame>hostowane przez. Jest to zilustrowane na poniższej ilustracji.

![Diagram ramek i stron](./media/navigation-overview/journal-navigation-within-pages-hosted-by-a-frame.png "Spowoduje to wyświetlenie nawigacji w dzienniku na stronach hostowanych przez ramkę.")

W <xref:System.Windows.Controls.Frame> takim przypadku można skonfigurować do korzystania z własnego dziennika przez <xref:System.Windows.Controls.Frame.JournalOwnership%2A> ustawienie właściwości <xref:System.Windows.Controls.Frame> na <xref:System.Windows.Navigation.JournalOwnership.OwnsJournal>. Jest to pokazane w poniższej tabeli.

[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml3)]

Na poniższej ilustracji przedstawiono efekt nawigowania w obrębie <xref:System.Windows.Controls.Frame> , który używa własnego dziennika.

![Ramka, która używa własnego dziennika](./media/navigation-overview/frame-uses-its-own-journal.png "Przedstawia efekt nawigowania w obrębie ramki korzystającej z własnego dziennika.")

Należy zauważyć, że wpisy dziennika są wyświetlane przez nawigację [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Controls.Frame>w, a nie przez [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)].

> [!NOTE]
> Jeśli element <xref:System.Windows.Controls.Frame> jest częścią zawartości <xref:System.Windows.Window>, która jest hostowana w <xref:System.Windows.Controls.Frame> usłudze, używa własnego dziennika i w związku z tym wyświetla własną nawigację [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].

<xref:System.Windows.Controls.Frame> Jeśli środowisko użytkownika wymaga, aby zapewnić własny dziennik bez wyświetlania nawigacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], można ukryć nawigację [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , ustawiając <xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A> polecenie na <xref:System.Windows.Visibility.Hidden>. Jest to pokazane w poniższej tabeli.

[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml3)]

<a name="Navigation_Hosts"></a>

## <a name="navigation-hosts"></a>Hosty nawigacji

<xref:System.Windows.Controls.Frame>i <xref:System.Windows.Navigation.NavigationWindow> są klasami, które są znane jako hosty nawigacji. *Host nawigacyjny* jest klasą, która może nawigować do zawartości i wyświetlać ją. W tym celu każdy host nawigacji używa własnych <xref:System.Windows.Navigation.NavigationService> i dzienników. Podstawowa konstrukcja hosta nawigacji jest pokazana na poniższej ilustracji.

![Diagramy nawigatora](./media/navigation-overview/navigation-host-construction.png "Podstawowa konstrukcja hosta nawigacji")

Zasadniczo umożliwia <xref:System.Windows.Navigation.NavigationWindow> to i <xref:System.Windows.Controls.Frame> zapewnia taką [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] samą obsługę nawigacji, którą zapewnia, gdy jest ona hostowana w przeglądarce.

Oprócz używania <xref:System.Windows.Navigation.NavigationService> i dziennika, hosty nawigacji implementują te same składowe, które <xref:System.Windows.Navigation.NavigationService> implementują. Jest to zilustrowane na poniższej ilustracji.

![Dziennik w ramce i w NavigationWindow](./media/navigation-overview/navigation-window-and-frame.png "Okno nawigacji i ramka")

Pozwala to na bezpośrednie przechodzenie do pomocy technicznej dotyczącej nawigacji. Można to wziąć pod uwagę [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Window>, jeśli trzeba zapewnić niestandardową nawigację <xref:System.Windows.Controls.Frame> dla programu, która jest hostowana w. Ponadto oba typy implementują dodatkowe elementy członkowskie powiązane z nawigacją, `BackStack` w<xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType>tym <xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType>(, `ForwardStack` )<xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType>i <xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType>(,), które umożliwiają Wyliczenie wpisów dziennika w tylnej stosują odpowiednio stosy i progresywne stosu.

Jak wspomniano wcześniej, w aplikacji może istnieć więcej niż jeden dziennik. Na poniższej ilustracji przedstawiono przykład, w którym może się to zdarzyć.

![Wiele dzienników w jednej aplikacji](./media/navigation-overview/multiple-journals-in-one-application.png "Jest to przykład dla więcej niż jednego dziennika w aplikacji.")

<a name="Navigating_to_Content_Other_than_Pages"></a>

## <a name="navigating-to-content-other-than-xaml-pages"></a>Przechodzenie do zawartości innej niż strony XAML

W tym temacie, <xref:System.Windows.Controls.Page> a pakiet [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] został użyty do zademonstrowania różnych możliwości nawigacyjnych programu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Jednak, <xref:System.Windows.Controls.Page> który jest kompilowany do aplikacji nie jest jedynym typem zawartości, do której można przejść, a pakiet [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] nie jest jedynym sposobem identyfikacji zawartości.

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

- Udział [!INCLUDE[TLA#tla_unc](../../../../includes/tlasharptla-unc-md.md)] plików.

- Dysk lokalny.

Luźny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plik można dodać do ulubionych przeglądarki lub jako stronę główną przeglądarki.

> [!NOTE]
> Aby uzyskać więcej informacji na temat publikowania i [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uruchamiania luźnych stron, zobacz [wdrażanie aplikacji WPF](deploying-a-wpf-application-wpf.md).

Ograniczenie odnoszące się do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] swobodnego polega na tym, że można hostować tylko zawartość, która jest bezpieczna do uruchamiania w częściowej relacji zaufania. Na przykład `Window` nie może być elementem głównym luźnego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku. Aby uzyskać więcej informacji, zobacz temat informacje o [zabezpieczeniach częściowej relacji zaufania WPF](../wpf-partial-trust-security.md).

<a name="Navigating_to_HTML_Files_Using_Frame"></a>

### <a name="navigating-to-html-files-by-using-frame"></a>Nawigowanie do plików HTML przy użyciu ramki

Jak można się spodziewać, możesz również przejść do kodu HTML. Wystarczy dostarczyć [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , który używa schematu http. Na przykład poniżej [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Controls.Frame> przedstawiono, który przechodzi do strony html.

[!code-xaml[NavigationOverviewSnippets#FrameHtmlNavMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHTMLNavPage.xaml#framehtmlnavmarkup)]

Przechodzenie do HTML wymaga specjalnych uprawnień. Nie można na przykład nawigować z [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] obszaru izolowanego zabezpieczeń strefa Internet częściowo Ufaj. Aby uzyskać więcej informacji, zobacz temat informacje o [zabezpieczeniach częściowej relacji zaufania WPF](../wpf-partial-trust-security.md).

<a name="Navigating_to_HTML_Files_Using_WebBrowser"></a>

### <a name="navigating-to-html-files-by-using-the-webbrowser-control"></a>Nawigowanie do plików HTML przy użyciu kontrolki WebBrowser

<xref:System.Windows.Controls.WebBrowser> Kontrolka obsługuje obsługę dokumentów HTML, nawigację i skrypt/współdziałanie kodu zarządzanego. Aby uzyskać szczegółowe informacje na <xref:System.Windows.Controls.WebBrowser> temat kontrolki <xref:System.Windows.Controls.WebBrowser>, zobacz.

Podobnie <xref:System.Windows.Controls.Frame>jak w przypadku nawigowania do <xref:System.Windows.Controls.WebBrowser> języka HTML przy użyciu programu wymagane są specjalne uprawnienia. Na przykład w aplikacji częściowo zaufanej można nawigować tylko do kodu HTML znajdującego się w lokalizacji źródłowej. Aby uzyskać więcej informacji, zobacz temat informacje o [zabezpieczeniach częściowej relacji zaufania WPF](../wpf-partial-trust-security.md).

<a name="Navigating_to_Objects"></a>

### <a name="navigating-to-custom-objects"></a>Nawigowanie do obiektów niestandardowych

Jeśli masz dane przechowywane jako obiekty niestandardowe, jednym ze sposobów wyświetlania tych danych jest utworzenie <xref:System.Windows.Controls.Page> zawartości z zawartością powiązaną z tymi obiektami (zobacz temat [powiązanie danych — omówienie](../data/data-binding-overview.md)). Jeśli nie potrzebujesz nakładu na tworzenie całej strony tylko w celu wyświetlenia obiektów, możesz przejść bezpośrednio do nich.

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

Na tym rysunku widać, że nie są wyświetlane żadne przydatne elementy. W rzeczywistości wyświetlana wartość jest wartością `ToString` zwracaną metody dla obiektu **osoby** ; domyślnie jest to jedyna wartość, która [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] może być używana do reprezentowania obiektu. Można zastąpić `ToString` metodę, aby zwrócić bardziej zrozumiałe informacje, chociaż nadal będzie to wartość ciągu. Jedną z technik, z której można korzystać w celu korzystania z funkcji [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] prezentacji programu, jest użycie szablonu danych. Można zaimplementować szablon danych, który [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] może zostać skojarzony z obiektem określonego typu. Poniższy kod przedstawia szablon danych dla `Person` obiektu.

[!code-xaml[NavigateToObjectSnippets#DataTemplateMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/App.xaml#datatemplatemarkup)]

W tym miejscu szablon danych jest skojarzony z `Person` typem przy `x:Type` użyciu rozszerzenia znaczników w `DataType` atrybucie. Szablon danych następnie tworzy powiązania `TextBlock` elementów (zobacz <xref:System.Windows.Controls.TextBlock>) `Person` z właściwościami klasy. Na poniższej ilustracji przedstawiono zaktualizowany wygląd `Person` obiektu.

![Przechodzenie do klasy, która ma szablon danych](./media/navigation-overview/navigating-to-a-class.png "Przechodzenie do klasy, która ma szablon danych.")

Zaletą tej techniki jest spójność, którą uzyskuje się dzięki możliwości ponownego użycia szablonu danych w celu spójnego wyświetlania obiektów w dowolnym miejscu w aplikacji.

Aby uzyskać więcej informacji na temat szablonów danych, zobacz [tworzenia szablonów danych — omówienie](../data/data-templating-overview.md).

<a name="Security"></a>

## <a name="security"></a>Zabezpieczenia

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Obsługa nawigacji umożliwia [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] nawigowanie w Internecie i umożliwia aplikacjom obsługę zawartości innej firmy. Aby chronić aplikacje i użytkowników przed szkodliwym zachowaniem [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , program udostępnia różnorodne funkcje zabezpieczeń, które są omówione [](../security-wpf.md) w zabezpieczeniach i [częściowej relacji zaufania WPF](../wpf-partial-trust-security.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Application.SetCookie%2A>
- <xref:System.Windows.Application.GetCookie%2A>
- [Zarządzanie aplikacjami — omówienie](application-management-overview.md)
- [Pakowanie URI w WPF](pack-uris-in-wpf.md)
- [Strukturyzowana nawigacja — omówienie](structured-navigation-overview.md)
- [Topologia nawigacji — omówienie](navigation-topologies-overview.md)
- [Tematy z instrukcjami](navigation-how-to-topics.md)
- [Wdrażanie aplikacji WPF](deploying-a-wpf-application-wpf.md)
