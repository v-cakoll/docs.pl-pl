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
ms.openlocfilehash: b326d623da49cf02b95be8a22a75b3ea3d199e27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="navigation-overview"></a>Przegląd Nawigacja
Windows Presentation Foundation (WPF) obsługuje nawigacji stylu przeglądarki, które mogą być używane w dwóch typów aplikacji: aplikacje autonomiczne i [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]. Zawartość pakietu do nawigacji [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zapewnia <xref:System.Windows.Controls.Page> klasy. Można przejść z jednej <xref:System.Windows.Controls.Page> do innego deklaratywnie, za pomocą <xref:System.Windows.Documents.Hyperlink>, lub programowo, za pomocą <xref:System.Windows.Navigation.NavigationService>. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] korzysta z dziennika do zapamiętania stron, które zostały przesłane z i do przejdź z powrotem do ich.  
  
 <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Navigation.NavigationService>, i dziennika stanowią podstawową Obsługa nawigacji oferowane przez [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. To omówienie Eksploruje te funkcje szczegółowo przed obejmujące obsługi zaawansowanych nawigacji, który obejmuje nawigacji można utracić [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pliki, [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] plików i obiektów.  
  
> [!NOTE]
>  W tym temacie termin "przeglądarki" odnosi się tylko do przeglądarek, które mogą zawierać [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji, które obecnie [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] i Firefox. W przypadku, gdy określone [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] funkcje są obsługiwane tylko przez przeglądarki, wersja przeglądarki jest określone.  
   
     
## <a name="navigation-in-wpf-applications"></a>Nawigacja w aplikacjach WPF  
 Ten temat zawiera omówienie funkcji klucza nawigacji w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Te funkcje są dostępne dla obu aplikacji autonomicznej i [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], mimo że w tym temacie przedstawiono ich w kontekście [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].  
  
> [!NOTE]
>  W tym temacie nie opisano, jak tworzyć i wdrażać [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], zobacz [przeglądu aplikacje przeglądarki XAML w WPF](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md).  
  
 W tej sekcji opisano i przedstawiono następujące aspekty nawigacji:  
  
-   [Implementacja strony](#CreatingAXAMLPage)  
  
-   [Konfigurowanie strony początkowej](#Configuring_a_Start_Page)  
  
-   [Konfigurowanie tytuł, szerokość i wysokość okno hosta](#ConfiguringAXAMLPage)  
  
-   [Nawigacja hiperłącza](#NavigatingBetweenXAMLPages)  
  
-   [Fragment nawigacji](#FragmentNavigation)  
  
-   [Usługa nawigacji](#NavigationService)  
  
-   [Programowe nawigacji w usłudze nawigacji](#Programmatic_Navigation_with_the_Navigation_Service)  
  
-   [Okres istnienia nawigacji](#Navigation_Lifetime)  
  
-   [Pamiętaj o tym, nawigacja z użyciem arkusza](#NavigationHistory)  
  
-   [Okres istnienia strony i dziennika](#PageLifetime)  
  
-   [Zachowywanie stanu zawartości z historii nawigacji](#RetainingContentStateWithNavigationHistory)  
  
-   [Pliki cookie](#Cookies)  
  
-   [Nawigacja w strukturze](#Structured_Navigation)  
  
<a name="CreatingAXAMLPage"></a>   
### <a name="implementing-a-page"></a>Implementacja strony  
 W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], można przejść do kilku typów zawartości, które obejmują obiektami środowiska .NET Framework, niestandardowe obiekty, wartości wyliczenia, kontrolek użytkownika [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki, i [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] plików. Jednak przekonasz się, że najbardziej typowe i wygodny sposób zawartość pakietu jest przy użyciu <xref:System.Windows.Controls.Page>. Ponadto <xref:System.Windows.Controls.Page> implementuje funkcje specyficzne dla nawigacji do nich specjalistyczne i uproszczenia programowanie.  
  
 Przy użyciu <xref:System.Windows.Controls.Page>, deklaratywnego można zaimplementować stronę można nawigować [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przy użyciu znaczników podobnie do następującej zawartości.  
  
 [!code-xaml[NavigationOverviewSnippets#Page1XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page1.xaml#page1xaml)]  
  
 A <xref:System.Windows.Controls.Page> zaimplementowanym w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ma znacznika `Page` jako jego elementu głównego i wymaga [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] deklaracji przestrzeni nazw. `Page` Element zawiera zawartość, która ma być nawigacji do i wyświetlania. Dodawanie zawartości przez ustawienie `Page.Content` elementu właściwości, jak pokazano w poniższych znaczników.  
  
 [!code-xaml[NavigationOverviewSnippets#Page2XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page2.xaml#page2xaml)]  
  
 `Page.Content` może zawierać tylko jeden element podrzędny; w powyższym przykładzie zawartość jest jeden ciąg "Hello, strony!" W praktyce, jako element podrzędny zwykle użyje formant układu (zobacz [układu](../../../../docs/framework/wpf/advanced/layout.md)) do przechowywania i redagowanie zawartości.  
  
 Elementy podrzędne `Page` elementu są traktowane jako zawartość <xref:System.Windows.Controls.Page> i w związku z tym nie trzeba używać jawnych `Page.Content` deklaracji. Następujący kod jest odpowiednikiem deklaratywne do poprzedniego przykładu.  
  
 [!code-xaml[NavigationOverviewSnippets#Page3XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page3.xaml#page3xaml)]  
  
 W takim przypadku `Page.Content` jest ustawiany automatycznie z elementami podrzędnymi elementu `Page` elementu. Aby uzyskać więcej informacji, zobacz [modelu zawartości WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md).  
  
 Tylko do znaczników <xref:System.Windows.Controls.Page> przydaje się do wyświetlania zawartości. Jednak <xref:System.Windows.Controls.Page> można także formanty wyświetlania, które zezwala użytkownikom na interakcję ze stroną, i może odpowiadać do interakcji z użytkownikiem, obsługiwanie zdarzeń i wywoływanie logiki aplikacji. Interaktywnej <xref:System.Windows.Controls.Page> jest zaimplementowana przy użyciu kombinacji znaczników i kodem, jak pokazano w poniższym przykładzie.  
  
 [!code-xaml[XBAPAppDefSnippets#HomePageMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml#homepagemarkup)]  
  
 [!code-csharp[XBAPAppDefSnippets#HomePageCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml.cs#homepagecodebehind)]
 [!code-vb[XBAPAppDefSnippets#HomePageCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/HomePage.xaml.vb#homepagecodebehind)]  
  
 Aby umożliwić pliku znaczników i plik CodeBehind współdziałają ze sobą, następująca konfiguracja jest wymagana:  
  
-   W znaczniku `Page` musi zawierać element `x:Class` atrybutu. Gdy aplikacja utworzeniu istnienie `x:Class` w znaczniku pliku powoduje, że [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] do utworzenia `partial` klasą pochodzącą z <xref:System.Windows.Controls.Page> i ma przypisaną nazwę określonego przez `x:Class` atrybutu. Wymaga to dodanie [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] deklaracji przestrzeni nazw dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schematu ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ). Wygenerowany `partial` klasa implementuje `InitializeComponent`, nazywany do rejestrowania zdarzeń i ustaw właściwości, które są wykonywane w znaczniku.  
  
-   W kodem, musi być klasa `partial` klasa o takiej samej nazwie, która jest określona przez `x:Class` atrybutu w kodzie znaczników oraz jego musi pochodzić od <xref:System.Windows.Controls.Page>. Dzięki temu plik CodeBehind ma być skojarzone z `partial` klasy, która jest generowane dla pliku znaczników, podczas tworzenia aplikacji (zobacz [kompilowania aplikacji WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)).  
  
-   W kodem <xref:System.Windows.Controls.Page> klasa musi implementować konstruktora, który wywołuje `InitializeComponent` metody. `InitializeComponent` jest implementowany przez kod znaczników na wygenerowany plik `partial` klasę, aby rejestrować zdarzenia i ustawić właściwości, które są zdefiniowane w znaczniku.  
  
> [!NOTE]
>  Po dodaniu nowego <xref:System.Windows.Controls.Page> na Twój projekt używający [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], <xref:System.Windows.Controls.Page> jest implementowane za pomocą zarówno znaczników i kodem, i zawiera niezbędną konfigurację, aby utworzyć skojarzenie między plikami znaczników i kodu powiązanego jako opisane poniżej.  
  
 Po utworzeniu <xref:System.Windows.Controls.Page>, można przejść do niego. Aby określić pierwszy <xref:System.Windows.Controls.Page> czy aplikacji powoduje przejście do, należy skonfigurować początek <xref:System.Windows.Controls.Page>.  
  
<a name="Configuring_a_Start_Page"></a>   
### <a name="configuring-a-start-page"></a>Konfigurowanie strony początkowej  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] wymaga pewnego infrastruktury aplikacji, które ma być obsługiwana w przeglądarce. W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], <xref:System.Windows.Application> klasy jest częścią definicji aplikacji, który określa infrastruktury wymaganej aplikacji (zobacz [omówienie zarządzania aplikacji](../../../../docs/framework/wpf/app-development/application-management-overview.md)).  
  
 Definicja aplikacji jest zwykle zaimplementowany przy użyciu zarówno znaczników i kodu powiązanego z pliku znaczników, skonfigurowany jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `ApplicationDefinition` elementu. Poniżej znajduje się definicja aplikacji dla [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].  
  
 [!code-xaml[XBAPAppDefSnippets#XBAPApplicationDefinitionMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]  
  
 [!code-csharp[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml.cs#xbapapplicationdefinitioncodebehind)]
 [!code-vb[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/Application.xaml.vb#xbapapplicationdefinitioncodebehind)]  
  
 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Umożliwia określenie początkową definicję aplikacji <xref:System.Windows.Controls.Page>, która jest <xref:System.Windows.Controls.Page> który jest automatycznie załadowany Jeśli [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] jest uruchamiana. Możesz to zrobić przez ustawienie <xref:System.Windows.Application.StartupUri%2A> właściwości o [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] dla żądaną <xref:System.Windows.Controls.Page>.  
  
> [!NOTE]
>  W większości przypadków <xref:System.Windows.Controls.Page> jest skompilowany w lub wdrożyć przy użyciu aplikacji. W takich przypadkach [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , które identyfikują <xref:System.Windows.Controls.Page> jest pakietem [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], która jest [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] zgodne ze *pakietu* schematu. Pakiet [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] omówiono w [identyfikatorów URI pakietu na platformie WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md). Można także przechodzić do zawartości przy użyciu protokołu http, który został omówiony poniżej.  
  
 Można ustawić <xref:System.Windows.Application.StartupUri%2A> deklaratywnie w znacznikach, jak pokazano w poniższym przykładzie.  
  
 [!code-xaml[NavigationOverviewSnippets#XBAPApplicationDefinitionMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]  
  
 W tym przykładzie `StartupUri` ustawiono atrybut z pakietem względną [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] identyfikującym HomePage.xaml. Gdy [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] jest uruchomiona, HomePage.xaml automatycznie przejście i wyświetlić. Wskazuje na poniższej ilustracji przedstawiono [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] który został uruchomiony z serwera sieci Web.  
  
 ![Strona XBAP](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure9.png "NavigationOverviewFigure9")  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat opracowywania i wdrażania [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], zobacz [przeglądu aplikacje przeglądarki XAML w WPF](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md) i [wdrażanie aplikacji WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md).  
  
<a name="ConfiguringAXAMLPage"></a>   
### <a name="configuring-the-host-windows-title-width-and-height"></a>Konfigurowanie tytuł, szerokość i wysokość okno hosta  
 Jedyną operacją, można zauważyć z powyższej ilustracji jest tytuł przeglądarki i panelu kartę [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Oprócz trwa długo, tytuł nie jest atrakcyjne ani informacji. Z tego powodu <xref:System.Windows.Controls.Page> oferuje sposób można zmienić tytuł przez ustawienie <xref:System.Windows.Controls.Page.WindowTitle%2A> właściwości. Ponadto można skonfigurować szerokość i wysokość okna przeglądarki przez ustawienie <xref:System.Windows.Controls.Page.WindowWidth%2A> i <xref:System.Windows.Controls.Page.WindowHeight%2A>odpowiednio.  
  
 <xref:System.Windows.Controls.Page.WindowTitle%2A>, <xref:System.Windows.Controls.Page.WindowWidth%2A>, i <xref:System.Windows.Controls.Page.WindowHeight%2A> można ustawić deklaratywnie w znacznikach, jak pokazano w poniższym przykładzie.  
  
 [!code-xaml[NavigationOverviewSnippets#HomePageMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/HomePage.xaml#homepagemarkup)]  
  
 Wynik jest wyświetlany na poniższej ilustracji.  
  
 ![Tytuł okna, wysokość i szerokość](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure2.png "NavigationOverviewFigure2")  
  
<a name="NavigatingBetweenXAMLPages"></a>   
### <a name="hyperlink-navigation"></a>Nawigacja hiperłącza  
 Typowe [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] obejmuje kilka stron. Najprostszym sposobem, aby przejść z jednej strony do innej jest użycie <xref:System.Windows.Documents.Hyperlink>. Można dodać deklaratywnie <xref:System.Windows.Documents.Hyperlink> do <xref:System.Windows.Controls.Page> przy użyciu `Hyperlink` element, który jest wyświetlany w następujących znaczników.  
  
 [!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]  
  
 A `Hyperlink` element ma następujące wymagania:  
  
-   Ten pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] z <xref:System.Windows.Controls.Page> można przejść do, zgodnie z określonym `NavigateUri` atrybutu.  
  
-   Zawartości, czy użytkownik może kliknąć zainicjować nawigacji, takie jak tekst i obrazy (zawartości, która `Hyperlink` elementu mogą zawierać, zobacz <xref:System.Windows.Documents.Hyperlink>).  
  
 Poniższy rysunek pokazuje [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] z <xref:System.Windows.Controls.Page> mający <xref:System.Windows.Documents.Hyperlink>.  
  
 ![Strona z hiperłączem](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure3.png "NavigationOverviewFigure3")  
  
 Jak można oczekiwać, klikając pozycję <xref:System.Windows.Documents.Hyperlink> powoduje, że [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] można przejść do <xref:System.Windows.Controls.Page> identyfikowane przez `NavigateUri` atrybutu. Ponadto [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] dodaje wpis dla poprzedniej <xref:System.Windows.Controls.Page> do listy ostatnich stron w [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]. Przedstawiono na poniższej ilustracji.  
  
 ![Przyciski Wstecz i dalej](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure4.png "NavigationOverviewFigure4")  
  
 Oprócz obsługi nawigacji z jednego <xref:System.Windows.Controls.Page> do innego, <xref:System.Windows.Documents.Hyperlink> również obsługuje fragmentu nawigacji.  
  
<a name="FragmentNavigation"></a>   
### <a name="fragment-navigation"></a>Fragment nawigacji  
 *Fragmentu nawigacji* jest nawigacji do fragmentu zawartości albo bieżącego <xref:System.Windows.Controls.Page> lub innym <xref:System.Windows.Controls.Page>. W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], fragmentu zawartości znajduje się odpowiednia zawartość, który jest zawarty w nazwanego elementu. Nazwany element to element, który ma jego `Name` atrybut. Następujący kod przedstawia nazwane `TextBlock` element, który zawiera fragmentu zawartości.  
  
 [!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup1)]  
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup2)]  
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup3)]  
  
 Aby uzyskać <xref:System.Windows.Documents.Hyperlink> do nawigacji do fragmentu zawartości `NavigateUri` atrybutu musi zawierać następujące:  
  
-   [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] z <xref:System.Windows.Controls.Page> z fragmentu zawartości, aby przejść do.  
  
-   Znak "#".  
  
-   Nazwa elementu na <xref:System.Windows.Controls.Page> zawierający fragmentu zawartości.  
  
 Fragment [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] ma następujący format.  
  
 *PageURI* `#` *ElementName*  
  
 Poniżej przedstawiono przykład `Hyperlink` skonfigurowanego do nawigacji do fragmentu zawartości.  
  
 [!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml1)]  
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml2)]  
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml3)]  
  
> [!NOTE]
>  W tej sekcji opisano Domyślna implementacja nawigacji fragmentu w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] można też wdrożyć własny schemat nawigacji fragmentu, co w części wymaga obsługi <xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType> zdarzeń.  
  
> [!IMPORTANT]
>  Można przejść do fragmentów w utracić [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stron (tylko kod znaczników [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki z `Page` jako element główny) tylko wtedy, gdy strony można przeglądać za pośrednictwem [!INCLUDE[TLA2#tla_http](../../../../includes/tla2sharptla-http-md.md)].  
>   
>  Jednak utracić [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony można przejść do jego własnej fragmenty.  
  
<a name="NavigationService"></a>   
### <a name="navigation-service"></a>Usługa nawigacji  
 Gdy <xref:System.Windows.Documents.Hyperlink> pozwala użytkownikowi na zainicjowanie nawigacji do określonego <xref:System.Windows.Controls.Page>, zadanie lokalizowania i pobierania strony jest wykonywane przez <xref:System.Windows.Navigation.NavigationService> klasy. Zasadniczo <xref:System.Windows.Navigation.NavigationService> pozwala, aby przetworzyć żądanie nawigacji w imieniu kodu klienta, takich jak <xref:System.Windows.Documents.Hyperlink>. Ponadto <xref:System.Windows.Navigation.NavigationService> zapewnia obsługę wyższego poziomu śledzenia i wpływania na żądania nawigacji.  
  
 Gdy <xref:System.Windows.Documents.Hyperlink> zostanie kliknięty [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wywołania <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> Aby znaleźć i pobrać <xref:System.Windows.Controls.Page> na określony pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Pobrany <xref:System.Windows.Controls.Page> jest konwertowana na drzewa obiektów, których główny obiekt jest wystąpieniem pobrany <xref:System.Windows.Controls.Page>. Odwołanie do elementu głównego <xref:System.Windows.Controls.Page> obiekt jest przechowywany w <xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType> właściwości. Pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] zawartość, która została przejście jest przechowywane w <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> właściwości, podczas <xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType> przechowuje pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] ostatniej strony, który został przejście.  
  
> [!NOTE]
>  Istnieje możliwość [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji ma więcej niż jedno aktywne <xref:System.Windows.Navigation.NavigationService>. Aby uzyskać więcej informacji, zobacz [hostów nawigacji](#Navigation_Hosts) dalszej części tego tematu.  
  
<a name="Programmatic_Navigation_with_the_Navigation_Service"></a>   
### <a name="programmatic-navigation-with-the-navigation-service"></a>Programowe nawigacji w usłudze nawigacji  
 Nie trzeba wiedzieć o <xref:System.Windows.Navigation.NavigationService> Jeśli nawigacji jest wdrażane za pomocą znacznika w deklaratywnie <xref:System.Windows.Documents.Hyperlink>, ponieważ <xref:System.Windows.Documents.Hyperlink> używa <xref:System.Windows.Navigation.NavigationService> w Twoim imieniu. Oznacza to, że, tak długo, jak bezpośrednie lub pośrednie nadrzędnego z <xref:System.Windows.Documents.Hyperlink> jest hostem nawigacji (zobacz [hostów nawigacji](#Navigation_Hosts)), <xref:System.Windows.Documents.Hyperlink> będzie mógł odnaleźć i korzystanie z usługi nawigacji hosta nawigacji do przetworzenia żądania nawigacji.  
  
 Jednakże, istnieją sytuacje, gdy musisz użyć <xref:System.Windows.Navigation.NavigationService> bezpośrednio, takie jak:  
  
-   Gdy są potrzebne do utworzenia wystąpienia <xref:System.Windows.Controls.Page> przy użyciu konstruktora z systemem innym niż domyślny.  
  
-   Aby ustawić właściwości <xref:System.Windows.Controls.Page> zanim przejdziesz do niego.  
  
-   Gdy <xref:System.Windows.Controls.Page> że potrzebuje do nastąpi przejście, tylko można określić w czasie wykonywania.  
  
 W takich sytuacjach należy napisać kod, aby programowo zainicjować nawigacji przez wywołanie metody <xref:System.Windows.Navigation.NavigationService.Navigate%2A> metody <xref:System.Windows.Navigation.NavigationService> obiektu. Która wymaga odwołania do <xref:System.Windows.Navigation.NavigationService>.  
  
#### <a name="getting-a-reference-to-the-navigationservice"></a>Odwołanie do NavigationService pobierania  
 Przyczyn, które są objęte [hostów nawigacji](#Navigation_Hosts) sekcji [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji może mieć więcej niż jeden <xref:System.Windows.Navigation.NavigationService>. Oznacza to, że kod musi mieć możliwość znalezienia <xref:System.Windows.Navigation.NavigationService>, który jest zwykle <xref:System.Windows.Navigation.NavigationService> przejście bieżącego <xref:System.Windows.Controls.Page>. Można pobrać odwołania do <xref:System.Windows.Navigation.NavigationService> przez wywołanie metody `static` <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A?displayProperty=nameWithType> metody. Aby uzyskać <xref:System.Windows.Navigation.NavigationService> przejście określonego <xref:System.Windows.Controls.Page>, Przekaż odwołanie do <xref:System.Windows.Controls.Page> jako argument <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A> — metoda. Poniższy kod przedstawia sposób uzyskiwania <xref:System.Windows.Navigation.NavigationService> dla bieżącego <xref:System.Windows.Controls.Page>.  
  
 [!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPage.xaml.vb#getnscodebehind2)]  
  
 Jako skrót do znajdowania <xref:System.Windows.Navigation.NavigationService> dla <xref:System.Windows.Controls.Page>, <xref:System.Windows.Controls.Page> implementuje <xref:System.Windows.Controls.Page.NavigationService%2A> właściwości. Przedstawiono to w poniższym przykładzie.  
  
 [!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPageShortCut.xaml.vb#getnsshortcutcodebehind2)]  
  
> [!NOTE]
>  A <xref:System.Windows.Controls.Page> tylko można pobrać odwołania do jego <xref:System.Windows.Navigation.NavigationService> podczas <xref:System.Windows.Controls.Page> zgłasza <xref:System.Windows.FrameworkElement.Loaded> zdarzeń.  
  
#### <a name="programmatic-navigation-to-a-page-object"></a>Programowe nawigacji do obiektu strony  
 Poniższy przykład przedstawia użycie <xref:System.Windows.Navigation.NavigationService> programowo przejdź do <xref:System.Windows.Controls.Page>. Programowe nawigacji jest wymagana, ponieważ <xref:System.Windows.Controls.Page> czyli trwa przejście może tylko można wdrożyć przy użyciu jednego konstruktora innych niż domyślne. <xref:System.Windows.Controls.Page> Pomocą konstruktora domyślnego nie jest wyświetlany w następujących znaczników i kodu.  
  
 [!code-xaml[NavigationOverviewSnippets#PageWithNonDefaultConstructorXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml#pagewithnondefaultconstructorxaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml.cs#pagewithnondefaultconstructorcodebehind)]
 [!code-vb[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithNonDefaultConstructor.xaml.vb#pagewithnondefaultconstructorcodebehind)]  
  
 <xref:System.Windows.Controls.Page> Która przechodzi do <xref:System.Windows.Controls.Page> pomocą konstruktora domyślnego nie jest wyświetlany w następujących znaczników i kodu.  
  
 [!code-xaml[NavigationOverviewSnippets#NSNavigationPageXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml#nsnavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml.cs#nsnavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSNavigationPage.xaml.vb#nsnavigationpagecodebehind)]  
  
 Gdy <xref:System.Windows.Documents.Hyperlink> na tym <xref:System.Windows.Controls.Page> jest kliknięciu nawigacji jest inicjowane przez utworzenie wystąpienia <xref:System.Windows.Controls.Page> można przejść do za pomocą konstruktora domyślnego z systemem innym niż i wywoływania <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> — metoda. <xref:System.Windows.Navigation.NavigationService.Navigate%2A> przyjmuje odwołanie do obiektu, który <xref:System.Windows.Navigation.NavigationService> spowoduje przejście do, zamiast pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
#### <a name="programmatic-navigation-with-a-pack-uri"></a>Programowe nawigacja z użyciem identyfikatora URI pakietu  
 Jeśli chcesz utworzyć pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] programowo (jeśli można określić tylko ten pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] w czasie wykonywania, na przykład), można użyć <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> metody. Przedstawiono to w poniższym przykładzie.  
  
 [!code-xaml[NavigationOverviewSnippets#NSUriNavigationPageXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml#nsurinavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml.cs#nsurinavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSUriNavigationPage.xaml.vb#nsurinavigationpagecodebehind)]  
  
#### <a name="refreshing-the-current-page"></a>Odświeżanie na bieżącej stronie  
 A <xref:System.Windows.Controls.Page> nie jest pobierana, jeśli ma ona tego samego pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jak pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] przechowywaną w <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> właściwości. Aby wymusić [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ponownie pobrać bieżącą stronę, można wywołać <xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType> metody, jak pokazano w poniższym przykładzie.  
  
 [!code-xaml[NavigationOverviewSnippets#NSRefreshNavigationPageXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml#nsrefreshnavigationpagexaml1)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind1)]
 [!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind2)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind2)]  
  
<a name="Navigation_Lifetime"></a>   
### <a name="navigation-lifetime"></a>Okres istnienia nawigacji  
 Istnieje wiele sposobów, aby zainicjować nawigacji, w tym samouczku. Po zainicjowaniu nawigacji, a podczas nawigacji jest w toku, można śledzić i wpływ nawigacji przy użyciu następujących zdarzeń, które są implementowane przez <xref:System.Windows.Navigation.NavigationService>:  
  
-   <xref:System.Windows.Navigation.NavigationService.Navigating>. Występuje, gdy wymagany jest nowy nawigacji. Może służyć do anulowania nawigacji.  
  
-   <xref:System.Windows.Navigation.NavigationService.NavigationProgress>. Występuje okresowo podczas pobierania i udostępnia informacje o postępie nawigacji.  
  
-   <xref:System.Windows.Navigation.NavigationService.Navigated>. Występuje, gdy strony zostało znajduje się i pobrane.  
  
-   <xref:System.Windows.Navigation.NavigationService.NavigationStopped>. Występuje po zatrzymaniu nawigacji (wywołując <xref:System.Windows.Navigation.NavigationService.StopLoading%2A>), lub gdy wymagane jest nowe nawigacji w trakcie bieżącego nawigacji.  
  
-   <xref:System.Windows.Navigation.NavigationService.NavigationFailed>. Występuje, gdy występuje błąd podczas nawigowania do żądanej zawartości.  
  
-   <xref:System.Windows.Navigation.NavigationService.LoadCompleted>. Występuje, gdy zawartość, która została przejście jest załadowany i przeanalizować i rozpoczęciu renderowania.  
  
-   <xref:System.Windows.Navigation.NavigationService.FragmentNavigation>. Występuje po rozpoczęciu nawigacji do fragmentu zawartości, która się w stanie:  
  
    -   Natychmiast Jeśli żądanego fragmentu znajduje się w bieżącej zawartości.  
  
    -   Po zawartości źródłowej został załadowany, jeśli żądanego fragmentu znajduje się w innej zawartości.  
  
 Zdarzenia nawigacji są wywoływane w kolejności, które przedstawiono w poniższym rysunku.  
  
 ![Schemat blokowy nawigacji strony](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure11.png "NavigationOverviewFigure11")  
  
 Ogólnie rzecz biorąc <xref:System.Windows.Controls.Page> nie ma danych dotyczących tych zdarzeń. Jest bardziej prawdopodobne, że dotyczy ich aplikacji i z tego względu te zdarzenia są również zgłoszone przez <xref:System.Windows.Application> klasy:  
  
-   <xref:System.Windows.Application.Navigating?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.NavigationProgress?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.Navigated?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.NavigationFailed?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.NavigationStopped?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.LoadCompleted?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.FragmentNavigation?displayProperty=nameWithType>  
  
 Za każdym razem, gdy <xref:System.Windows.Navigation.NavigationService> zgłasza zdarzenie, <xref:System.Windows.Application> klasy wywołuje odpowiednie zdarzenie. <xref:System.Windows.Controls.Frame> i <xref:System.Windows.Navigation.NavigationWindow> oferują tego samego zdarzenia do wykrywania nawigacji w odpowiednich zakresach.  
  
 W niektórych przypadkach <xref:System.Windows.Controls.Page> mogą być zainteresowane tych zdarzeń. Na przykład <xref:System.Windows.Controls.Page> może obsłużyć <xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType> zdarzenia w celu określenia, czy anulować nawigacji od samego. Przedstawiono to w poniższym przykładzie.  
  
 [!code-xaml[NavigationOverviewSnippets#CancelNavigationPageXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml#cancelnavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml.cs#cancelnavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/CancelNavigationPage.xaml.vb#cancelnavigationpagecodebehind)]  
  
 Jeśli można zarejestrować obsługi zdarzenia nawigacji, z <xref:System.Windows.Controls.Page>, tak jak w poprzednim przykładzie, należy wyrejestrować program obsługi zdarzeń. Jeśli użytkownik nie może być efekty uboczne względem jak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pamięta nawigacji <xref:System.Windows.Controls.Page> nawigacji za pomocą dziennika.  
  
<a name="NavigationHistory"></a>   
### <a name="remembering-navigation-with-the-journal"></a>Pamiętaj o tym, nawigacja z użyciem arkusza  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] używa dwóch stosy do zapamiętania stron, które zostały przesłane z: stosie przechodzenia wstecz i do przodu stosu. Po przejściu od bieżącej <xref:System.Windows.Controls.Page> na nowy <xref:System.Windows.Controls.Page> lub do przodu do istniejącej <xref:System.Windows.Controls.Page>, bieżący <xref:System.Windows.Controls.Page> jest dodawany do *stosie przechodzenia wstecz*. Po przejściu od bieżącej <xref:System.Windows.Controls.Page> do poprzedniego <xref:System.Windows.Controls.Page>, bieżący <xref:System.Windows.Controls.Page> jest dodawany do *stosie forward*. Stosie przechodzenia wstecz, stosie forward i funkcji do zarządzania nimi, zbiorczo są określane jako dziennika. Każdy element w stosie przechodzenia wstecz i do przodu stosu jest wystąpienie <xref:System.Windows.Navigation.JournalEntry> klasy, a jest określany jako *wpis dziennika*.  
  
#### <a name="navigating-the-journal-from-internet-explorer"></a>Nawigacja do dziennika w programie Internet Explorer  
 Koncepcyjnie, arkusz działa tak samo jak robi **ponownie** i **do przodu** przycisków w [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] czy. Zostały one przedstawione na poniższej ilustracji.  
  
 ![Przyciski Wstecz i dalej](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure4.png "NavigationOverviewFigure4")  
  
 Aby uzyskać [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] obsługiwane przez [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] integruje dziennika nawigacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]. Dzięki temu użytkownicy mogą przejść stron w [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] za pomocą **ponownie**, **do przodu**, i **ostatnie strony** przycisków w [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]. Dziennik nie został zintegrowany ze [!INCLUDE[TLA2#tla_ie6](../../../../includes/tla2sharptla-ie6-md.md)] w taki sam sposób dla [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)] lub Internet Explorer 8. Zamiast tego [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] renderuje nawigacji substitute [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
> [!IMPORTANT]
>  W [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], gdy użytkownik przechodzi od i do [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], tylko wpisy dziennika dla stron, które nie zostały zachowane aktywności są przechowywane w dzienniku. Omówienie na przechowywanie stron aktywności, zobacz [okres istnienia strony i dziennika](#PageLifetime) dalszej części tego tematu.  
  
 Domyślnie tekst dla każdego <xref:System.Windows.Controls.Page> wyświetlonym w **ostatnie strony** lista [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] jest [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla <xref:System.Windows.Controls.Page>. W wielu przypadkach nie jest to szczególnie przydatne dla użytkownika. Na szczęście może zmieniać tekst przy użyciu jednej z następujących opcji:  
  
1.  Dołączony `JournalEntry.Name` wartość atrybutu.  
  
2.  `Page.Title` Wartość atrybutu.  
  
3.  `Page.WindowTitle` Wartość atrybutu i [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla bieżącego <xref:System.Windows.Controls.Page>.  
  
4.  [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Dla bieżącego <xref:System.Windows.Controls.Page>. (Domyślnie)  
  
 Kolejność, w którym są wyświetlane opcje odpowiada kolejność pierwszeństwa tekstu. Na przykład jeśli `JournalEntry.Name` jest ustawiona, inne wartości są ignorowane.  
  
 W poniższym przykładzie użyto `Page.Title` atrybutu, aby zmienić tekst wyświetlany dla wpisu dziennika.  
  
 [!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup1)]  
[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup2)]  
  
 [!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind1)]
 [!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind2)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind2)]  
  
#### <a name="navigating-the-journal-using-wpf"></a>Nawigowanie po dziennika przy użyciu programu WPF  
 Mimo że może przejść użytkownik dziennika przy użyciu **ponownie**, **do przodu**, i **ostatnie strony** w [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], można także przechodzić dziennika przy użyciu zarówno deklaracyjne i programowych mechanizmów udostępnianych przez [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Jedną z przyczyn w tym celu jest zapewnienie niestandardowych nawigacji [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] na swoich stronach.  
  
 Deklaratywnie można dodać obsługę nawigacji dziennika przy użyciu poleceń nawigacji udostępniane przez <xref:System.Windows.Input.NavigationCommands>. W poniższym przykładzie pokazano sposób użycia `BrowseBack` polecenie nawigacji.  
  
 [!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml1)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml2)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml3)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml4)]  
  
 Dziennik można przejść programowo przy użyciu jednej z następujących członków <xref:System.Windows.Navigation.NavigationService> klasy:  
  
-   <xref:System.Windows.Navigation.NavigationService.GoBack%2A>  
  
-   <xref:System.Windows.Navigation.NavigationService.GoForward%2A>  
  
-   <xref:System.Windows.Navigation.NavigationService.CanGoBack%2A>  
  
-   <xref:System.Windows.Navigation.NavigationService.CanGoForward%2A>  
  
 Ten dziennik może również manipulować programowo, zgodnie z opisem w [oporowe stan zawartości z historią nawigacji](#RetainingContentStateWithNavigationHistory) dalszej części tego tematu.  
  
<a name="PageLifetime"></a>   
### <a name="page-lifetime-and-the-journal"></a>Okres istnienia strony i dziennika  
 Należy wziąć pod uwagę [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] z kilka stron, które zawierają bogatej zawartości, w tym grafiki, animacji i nośnika. Zużycie pamięci dla stron, takich jak te może być dość duży, zwłaszcza w wypadku wideo i audio nośniki są używane. Biorąc pod uwagę, że dziennik "pamięta" stron, które zostały nawigować do, na przykład [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] może wymagać dużych i zauważalne ilość pamięci.  
  
 Z tego powodu domyślne zachowanie dziennika jest przechowywanie <xref:System.Windows.Controls.Page> metadanych w każdego wpisu dziennika zamiast odwołania do <xref:System.Windows.Controls.Page> obiektu. Jeśli przejście jest wpis dziennika, jego <xref:System.Windows.Controls.Page> metadanych jest używany do utworzenia nowego wystąpienia określonego <xref:System.Windows.Controls.Page>. W konsekwencji każdego <xref:System.Windows.Controls.Page> jest przejście, który ma czas istnienia, które przedstawiono w poniższym rysunku.  
  
 ![Okres istnienia strony](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure10.PNG "NavigationOverviewFigure10")  
  
 Mimo że za pomocą rejestrowanie domyślne zachowanie można zapisać na zużycie pamięci, może być obniżona wydajność renderowania na stronie; reinstantiating <xref:System.Windows.Controls.Page> może być czas intensywnie, zwłaszcza w przypadku, gdy ma ona wiele zawartości. Jeśli chcesz zachować <xref:System.Windows.Controls.Page> wystąpienia w dzienniku, można narysować na dwie metody w ten sposób. Najpierw należy programowo można przejść do <xref:System.Windows.Controls.Page> obiektu przez wywołanie metody <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> metody.  
  
 Po drugie, można określić, że [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zachować wystąpienia <xref:System.Windows.Controls.Page> w dzienniku przez ustawienie <xref:System.Windows.Controls.Page.KeepAlive%2A> właściwości `true` (wartość domyślna to `false`). Jak pokazano w poniższym przykładzie, można ustawić <xref:System.Windows.Controls.Page.KeepAlive%2A> deklaratywnie w znacznikach.  
  
 [!code-xaml[NavigationOverviewSnippets#KeepAlivePageXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/KeepAlivePage.xaml#keepalivepagexaml)]  
  
 Okres istnienia <xref:System.Windows.Controls.Page> czyli życiu niewielkim stopniu różni się od, który nie jest. Po raz pierwszy <xref:System.Windows.Controls.Page> który jest przechowywany aktywności jest przejście do, zostanie on uruchomiony tak jak <xref:System.Windows.Controls.Page> który nie jest przechowywane aktywności. Jednakże ponieważ wystąpienie <xref:System.Windows.Controls.Page> są przechowywane w dzienniku, zostanie on nigdy uruchomiony ponownie dla tak długo, jak pozostaje w dzienniku. W związku z tym jeśli <xref:System.Windows.Controls.Page> ma logiki inicjacji, który musi być wywoływany zawsze <xref:System.Windows.Controls.Page> jest przejście, użytkownik powinien Przenieś go z konstruktora do obsługi dla <xref:System.Windows.FrameworkElement.Loaded> zdarzeń. Jak pokazano na poniższej ilustracji, <xref:System.Windows.FrameworkElement.Loaded> i <xref:System.Windows.FrameworkElement.Unloaded> zdarzenia są nadal podnoszone, zawsze <xref:System.Windows.Controls.Page> jest przejście do i z, odpowiednio.  
  
 ![Kiedy są wywoływane zdarzeń ładowania i zwalniania](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure17.png "NavigationOverviewFigure17")  
  
 Gdy <xref:System.Windows.Controls.Page> jest nie utrzymywane, nie należy przeprowadzać jednej z następujących pozycji:  
  
-   Przechowywanie odwołanie lub dowolną część.  
  
-   Zarejestruj procedury obsługi zdarzeń z zdarzenia, które nie zostały zaimplementowane przez nią.  
  
 Każda z tych czynności spowoduje utworzenie odwołań force <xref:System.Windows.Controls.Page> ma zostać zachowana w pamięci, nawet po usunięciu z dziennika.  
  
 Ogólnie rzecz biorąc, należy preferować domyślnie <xref:System.Windows.Controls.Page> zachowanie nie zachowuje <xref:System.Windows.Controls.Page> aktywności. Jednak ma wpływ na stan opisanymi w następnej sekcji.  
  
<a name="RetainingContentStateWithNavigationHistory"></a>   
### <a name="retaining-content-state-with-navigation-history"></a>Zachowywanie stanu zawartości z historii nawigacji  
 Jeśli <xref:System.Windows.Controls.Page> nie pozostaje aktywne, i ma formantów, które zbierają dane od użytkownika, co się dzieje z danych, jeśli użytkownik przechodzi od i do <xref:System.Windows.Controls.Page>? Z punktu widzenia środowiska użytkownika użytkownik oczekiwać poprzednio wprowadzone dane. Niestety ponieważ nowe wystąpienie klasy <xref:System.Windows.Controls.Page> jest tworzony za każdym nawigacji formanty reinstantiated są zbierane dane, a dane zostaną utracone.  
  
 Na szczęście dzienniku zapewnia obsługę zapamiętywanie danych między <xref:System.Windows.Controls.Page> nawigacji, włącznie z danymi formantu. W szczególności wpisu dziennika dla każdego <xref:System.Windows.Controls.Page> działa jako tymczasowy kontenera skojarzonych z nim <xref:System.Windows.Controls.Page> stanu. Poniższe kroki wchodzą w skład jak ta obsługa jest używany podczas <xref:System.Windows.Controls.Page> jest przejście od:  
  
1.  Wpis dla bieżącego <xref:System.Windows.Controls.Page> zostanie dodany do dziennika.  
  
2.  Stan <xref:System.Windows.Controls.Page> jest przechowywany z wpisu dziennika dla tej strony, która jest dodawana do tyłu stosu.  
  
3.  Nowe <xref:System.Windows.Controls.Page> jest przejście.  
  
 Po stronie <xref:System.Windows.Controls.Page> jest przejście do, za pomocą dziennika, następujące kroki miejsce:  
  
1.  <xref:System.Windows.Controls.Page> (Wpis dziennika top w stosie przechodzenia wstecz) zostanie uruchomiony.  
  
2.  <xref:System.Windows.Controls.Page> Są odświeżane o stanie, które były przechowywane dla wpis dziennika <xref:System.Windows.Controls.Page>.  
  
3.  <xref:System.Windows.Controls.Page> Jest przejście wstecz.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] automatycznie wykorzystuje tę obsługę stosowania następujących formantów na <xref:System.Windows.Controls.Page>:  
  
-   <xref:System.Windows.Controls.CheckBox>  
  
-   <xref:System.Windows.Controls.ComboBox>  
  
-   <xref:System.Windows.Controls.Expander>  
  
-   <xref:System.Windows.Controls.Frame>  
  
-   <xref:System.Windows.Controls.ListBox>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.ProgressBar>  
  
-   <xref:System.Windows.Controls.RadioButton>  
  
-   <xref:System.Windows.Controls.Slider>  
  
-   <xref:System.Windows.Controls.TabControl>  
  
-   <xref:System.Windows.Controls.TabItem>  
  
-   <xref:System.Windows.Controls.TextBox>  
  
 Jeśli <xref:System.Windows.Controls.Page> używa tych kontrolki, dane wprowadzane w nich jest zapamiętanych między <xref:System.Windows.Controls.Page> nawigacji, jak pokazano w **ulubiony kolor** <xref:System.Windows.Controls.ListBox> na poniższej ilustracji.  
  
 ![Strona z formantami, które należy pamiętać, stan](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure13.png "NavigationOverviewFigure13")  
  
 Gdy <xref:System.Windows.Controls.Page> ma formantów innych niż wymienione w powyższej listy, lub jeśli stan jest przechowywany w niestandardowych obiektów, należy napisać kod, aby spowodować dziennika do zapamiętania stanu między <xref:System.Windows.Controls.Page> nawigacji.  
  
 Jeśli musisz pamiętać mała sztuk stanu między <xref:System.Windows.Controls.Page> nawigacji, można użyć właściwości zależności (zobacz <xref:System.Windows.DependencyProperty>) skonfigurowanych z <xref:System.Windows.FrameworkPropertyMetadata.Journal%2A?displayProperty=nameWithType> flagi metadanych.  
  
 Jeśli stan który Twojej <xref:System.Windows.Controls.Page> trzeba pamiętać tego składa się z wielu fragmentów danych, może być mniejsza ilość kodu znacznym Hermetyzowanie swój stan w jednej klasy i zaimplementować <xref:System.Windows.Navigation.IProvideCustomContentState> interfejsu.  
  
 Jeśli musisz nawigowania w zależności od różnych stanów jedną <xref:System.Windows.Controls.Page>, bez konieczności z <xref:System.Windows.Controls.Page> , można użyć <xref:System.Windows.Navigation.IProvideCustomContentState> i <xref:System.Windows.Navigation.NavigationService.AddBackEntry%2A?displayProperty=nameWithType>.  
  
<a name="Cookies"></a>   
### <a name="cookies"></a>Pliki cookie  
 Inny jak robi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacje mogą być przechowywane dane z plików cookie, które tworzone są aktualizowane i usunąć za pomocą <xref:System.Windows.Application.SetCookie%2A> i <xref:System.Windows.Application.GetCookie%2A> metody. Pliki cookie, które można tworzyć w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] są tego samego pliki cookie to innych typów aplikacji sieci Web użyj; pliki cookie są dowolnego fragmentów danych, które są przechowywane przez aplikację na komputerze klienckim podczas lub między sesjami aplikacji. Dane pliku cookie mają zwykle postać pary nazwa/wartość w następującym formacie.  
  
 *Nazwa* `=` *wartości*  
  
 Gdy dane są przekazywane do <xref:System.Windows.Application.SetCookie%2A>, wraz z <xref:System.Uri> lokalizacji, dla którego można ustawić plik cookie, plik cookie jest tworzony w pamięci i jest on dostępny tylko na czas trwania bieżącej sesji aplikacji. Ten typ pliku cookie jest określany jako *pliku cookie sesji*.  
  
 Do przechowywania pliku cookie sesji aplikacji, datę wygaśnięcia, należy dodać do pliku cookie w następującym formacie.  
  
 *NAZWA* `=` *WARTOŚCI* `; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`  
  
 Plik cookie z datą wygaśnięcia znajduje się w bieżącym [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] instalacji folderu tymczasowych plików internetowych, dopóki nie wygasa plik cookie. Taki plik cookie jest nazywany *trwały plik cookie* ponieważ istnieje między sesjami aplikacji.  
  
 Pobrać zarówno sesji i trwałe pliki cookie przez wywołanie metody <xref:System.Windows.Application.GetCookie%2A> jest metoda <xref:System.Uri> lokalizacji, w której plik cookie został ustawiony z <xref:System.Windows.Application.SetCookie%2A> metody.  
  
 Oto niektóre sposoby, które pliki cookie są obsługiwane w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]:  
  
-   [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Aplikacje autonomiczne i [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] zarówno tworzyć i zarządzać plików cookie.  
  
-   Pliki cookie, które są tworzone przez [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] jest możliwy za pomocą przeglądarki.  
  
-   [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] w tej samej domenie można tworzyć i udostępniać pliki cookie.  
  
-   [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] i [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] stron z tej samej domeny może tworzyć i udostępniać pliki cookie.  
  
-   Pliki cookie są wysyłane podczas [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] i utracić [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stron tworzą żądania sieci Web.  
  
-   Zarówno najwyższego poziomu [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] i [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] hostowanych w ramek IFRAME mogą uzyskiwać dostęp do plików cookie.  
  
-   Obsługa plików cookie w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jest taka sama dla wszystkich obsługiwanych przeglądarkach.  
  
-   W [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], P3P zasad, które dotyczą plików cookie jest honorowane przez [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], szczególnie w odniesieniu do firmy oraz innych firm [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
<a name="Structured_Navigation"></a>   
### <a name="structured-navigation"></a>Nawigacja w strukturze  
 Jeśli potrzebujesz do przekazywania danych z jednego <xref:System.Windows.Controls.Page> do innego, należy przekazać dane jako argumenty do z systemem innym niż domyślny konstruktor obiektu <xref:System.Windows.Controls.Page>. Należy pamiętać, że jeśli używasz tej metody, należy pozostawić <xref:System.Windows.Controls.Page> aktywności; Jeśli nie, przy następnym przejdź do <xref:System.Windows.Controls.Page>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] reinstantiates <xref:System.Windows.Controls.Page> za pomocą konstruktora domyślnego.  
  
 Alternatywnie Twojej <xref:System.Windows.Controls.Page> można zaimplementować właściwości, które są konfigurowane przy użyciu danych, który musi zostać przekazany. Rzeczy oczywisty, jednakże, gdy <xref:System.Windows.Controls.Page> należy przekazać dane z powrotem do <xref:System.Windows.Controls.Page> przejście, które do niego. Problem jest, że nawigacji nie obsługuje natywnie mechanizmy dla zagwarantowania, że <xref:System.Windows.Controls.Page> będą zwracane po jest kierowana z. Zasadniczo nawigacji nie obsługuje semantyki wywołanie/powrotu. Aby rozwiązać ten problem, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zapewnia <xref:System.Windows.Navigation.PageFunction%601> klasy, która służy do zapewnienia, że <xref:System.Windows.Controls.Page> jest zwracana do w sposób strukturalnych i przewidywalne. Aby uzyskać więcej informacji, zobacz [strukturalnych omówienie nawigacji](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md).  
  
<a name="The_NavigationWindow_Class"></a>   
## <a name="the-navigationwindow-class"></a>Klasa NavigationWindow  
 W tym punkcie przedstawiono gamy usług nawigacji, które najprawdopodobniej będzie używać do tworzenia aplikacji z zawartością, można nawigować. Te usługi zostały omówione w kontekście [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], chociaż nie są ograniczone do [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Nowoczesnych systemów operacyjnych i aplikacji systemu Windows skorzystaj z przeglądania nowoczesnych użytkowników włączenie nawigacji w stylu przeglądarki do aplikacji autonomicznej. Typowe przykłady obejmują:  
  
-   **Word tezaurusa**: Przejdź do opcji programu word.  
  
-   **Plik Explorer**: przeglądanie plików i folderów.  
  
-   **Kreatorzy**: podziału złożonym zadaniem na wiele stron, które można nawigować między. Przykładem jest Kreatora składników systemu Windows, która obsługuje dodawanie i usuwanie funkcji systemu Windows.  
  
 Aby dołączyć nawigacji w stylu przeglądarki do aplikacji autonomicznej, można użyć <xref:System.Windows.Navigation.NavigationWindow> klasy. <xref:System.Windows.Navigation.NavigationWindow> pochodną <xref:System.Windows.Window> i rozszerza on o tej samej obsługę nawigacji który [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] Podaj. Można użyć <xref:System.Windows.Navigation.NavigationWindow> jako głównego okna aplikacji autonomiczny lub jako okien podrzędnych, takich jak okno dialogowe.  
  
 Aby zaimplementować <xref:System.Windows.Navigation.NavigationWindow>, podobnie jak w przypadku większości klas najwyższego poziomu w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] (<xref:System.Windows.Window>, <xref:System.Windows.Controls.Page>i tak dalej), użycie kombinacji znaczników i związane z kodem. Przedstawiono to w poniższym przykładzie.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#NavigationWindowMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml#navigationwindowmarkup)]  
  
 [!code-csharp[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml.cs#navigationwindowcodebehind)]
 [!code-vb[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/MainWindow.xaml.vb#navigationwindowcodebehind)]  
  
 Ten kod tworzy <xref:System.Windows.Navigation.NavigationWindow> który automatycznie przechodzi do <xref:System.Windows.Controls.Page> (HomePage.xaml) podczas <xref:System.Windows.Navigation.NavigationWindow> jest otwarty. Jeśli <xref:System.Windows.Navigation.NavigationWindow> okna głównego aplikacji, można użyć `StartupUri` atrybutu, aby go uruchomić. Przedstawiono to w następujących znaczników.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchNavWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/App.xaml#applaunchnavwindow)]  
  
 Poniższy rysunek pokazuje <xref:System.Windows.Navigation.NavigationWindow> jako aplikacja autonomiczna w głównym oknie.  
  
 ![Okno główne](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure18.png "NavigationOverviewFigure18")  
  
 Z rysunku, można stwierdzić, że <xref:System.Windows.Navigation.NavigationWindow> ma tytuł, nawet jeśli nie została ustawiona <xref:System.Windows.Navigation.NavigationWindow> wykonania kodu z poprzedniego przykładu. Zamiast tego tytułu ustawić przy użyciu <xref:System.Windows.Controls.Page.WindowTitle%2A> właściwości, które przedstawiono w poniższym kodzie.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup1)]  
[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup2)]  
  
 Ustawienie <xref:System.Windows.Controls.Page.WindowWidth%2A> i <xref:System.Windows.Controls.Page.WindowHeight%2A> właściwości wpływa także na <xref:System.Windows.Navigation.NavigationWindow>.  
  
 Zazwyczaj należy zaimplementować własne <xref:System.Windows.Navigation.NavigationWindow> Aby dostosować zachowanie lub jego wyglądu. Jeśli nie zrobisz, możesz użyć skrótu. Jeśli określisz pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] z <xref:System.Windows.Controls.Page> jako <xref:System.Windows.Application.StartupUri%2A> w aplikacji autonomicznej, <xref:System.Windows.Application> automatycznie tworzy <xref:System.Windows.Navigation.NavigationWindow> hosta <xref:System.Windows.Controls.Page>. Następujący kod przedstawia sposób je włączyć.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/AnotherApp.xaml#applaunchpage)]  
  
 Jeśli chcesz, aby okna dodatkowej aplikacji, takich jak okno dialogowe, można <xref:System.Windows.Navigation.NavigationWindow>, można użyć kodu w poniższym przykładzie, aby go otworzyć.  
  
 [!code-csharp[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/DialogOwnerWindow.xaml.cs#createnwdialogbox)]
 [!code-vb[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/DialogOwnerWindow.xaml.vb#createnwdialogbox)]  
  
 Na poniższej ilustracji przedstawiono wynik.  
  
 ![Okno dialogowe](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure19.png "NavigationOverviewFigure19")  
  
 Jak widać, <xref:System.Windows.Navigation.NavigationWindow> Wyświetla [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]— styl **ponownie** i **do przodu** przycisków, aby umożliwić użytkownikom przechodzenie do dziennika. Przyciski te zapewniają tego samego środowiska użytkownika, jak pokazano na poniższej ilustracji.  
  
 ![Przyciski w oknie nawigacji Wstecz i dalej](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure20.png "NavigationOverviewFigure20")  
  
 Strony zapewnić własne dziennika Obsługa nawigacji i interfejsu użytkownika, można ukryć **ponownie** i **do przodu** przyciski wyświetlane na <xref:System.Windows.Navigation.NavigationWindow> przez ustawienie wartości <xref:System.Windows.Navigation.NavigationWindow.ShowsNavigationUI%2A> właściwości `false`.  
  
 Alternatywnie można korzystać z obsługi dostosowania w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zastąpić [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z <xref:System.Windows.Navigation.NavigationWindow> samej siebie.  
  
<a name="Frame_in_Standalone_Applications"></a>   
## <a name="the-frame-class"></a>Klasa ramki  
 Zarówno przeglądarki i <xref:System.Windows.Navigation.NavigationWindow> są tej zawartości można nawigować hosta systemu windows. W niektórych przypadkach aplikacje mają zawartość, która nie musi być obsługiwany przez całe okno. Jednak takie zawartość udostępniana wewnątrz innej zawartości. Można wstawić zawartości można nawigować do innej zawartości przy użyciu <xref:System.Windows.Controls.Frame> klasy. <xref:System.Windows.Controls.Frame> zapewnia obsługę tego samego jako <xref:System.Windows.Navigation.NavigationWindow> i [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
 Poniższy przykład przedstawia sposób dodawania <xref:System.Windows.Controls.Frame> do <xref:System.Windows.Controls.Page> deklaratywnie przy użyciu `Frame` elementu.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml3)]  
  
 Ustawia tego znacznika `Source` atrybutu `Frame` element z pakietem [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla <xref:System.Windows.Controls.Page> który <xref:System.Windows.Controls.Frame> początkowo powinien przejść do. Poniższy rysunek pokazuje [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] z <xref:System.Windows.Controls.Page> mający <xref:System.Windows.Controls.Frame> który nawigację między kilka stron.  
  
 ![Ramka nawigację między wieloma stronami](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure5.png "NavigationOverviewFigure5")  
  
 Tylko nie trzeba używać <xref:System.Windows.Controls.Frame> wewnątrz treści <xref:System.Windows.Controls.Page>. Jest również częściej <xref:System.Windows.Controls.Frame> wewnątrz treści <xref:System.Windows.Window>.  
  
 Domyślnie <xref:System.Windows.Controls.Frame> swój własny dziennik używa tylko w przypadku braku innym arkuszu. Jeśli <xref:System.Windows.Controls.Frame> jest częścią zawartość, która znajduje się wewnątrz albo <xref:System.Windows.Navigation.NavigationWindow> lub [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], <xref:System.Windows.Controls.Frame> korzysta z dziennika, który należy do <xref:System.Windows.Navigation.NavigationWindow> lub [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Czasami jednak <xref:System.Windows.Controls.Frame> może być konieczne odpowiedzialny za swój własny dziennik. Jedną z przyczyn w tym celu jest umożliwienie dziennika nawigację w ramach stron, które są obsługiwane przez <xref:System.Windows.Controls.Frame>. Jest to zilustrowane w poniższym rysunku.  
  
 ![Diagram ramek i stron](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure7.png "NavigationOverviewFigure7")  
  
 W takim przypadku można skonfigurować <xref:System.Windows.Controls.Frame> do użycia przez ustawienie swój własny dziennik <xref:System.Windows.Controls.Frame.JournalOwnership%2A> właściwość <xref:System.Windows.Controls.Frame> do <xref:System.Windows.Navigation.JournalOwnership.OwnsJournal>. Przedstawiono to w następujących znaczników.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml3)]  
  
 Na poniższym rysunku przedstawiono efekt poruszanie się w obrębie <xref:System.Windows.Controls.Frame> używającą swój własny dziennik.  
  
 ![Ramki, który używa swój własny dziennik](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure8.png "NavigationOverviewFigure8")  
  
 Należy zauważyć, że wpisy dziennika są wyświetlane w obszarze nawigacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w <xref:System.Windows.Controls.Frame>, a nie przez [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)].  
  
> [!NOTE]
>  Jeśli <xref:System.Windows.Controls.Frame> jest częścią zawartość, która jest obsługiwana w <xref:System.Windows.Window>, <xref:System.Windows.Controls.Frame> używany osobny dziennik, a w rezultacie wyświetla jego własnej nawigacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Jeśli użytkowników wymaga <xref:System.Windows.Controls.Frame> zapewnienie swój własny dziennik bez wyświetlania nawigacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], można ukryć nawigacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] przez ustawienie <xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A> do <xref:System.Windows.Visibility.Hidden>. Przedstawiono to w następujących znaczników.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml3)]  
  
<a name="Navigation_Hosts"></a>   
## <a name="navigation-hosts"></a>Hosty nawigacji  
 <xref:System.Windows.Controls.Frame> i <xref:System.Windows.Navigation.NavigationWindow> są klasy, które są określane jako hosty nawigacji. A *hosta nawigacji* jest klasą, który można przejść do wyświetlania zawartości. Aby to zrobić, każdy host nawigacji używa własnego <xref:System.Windows.Navigation.NavigationService> i dziennika. Na poniższej ilustracji przedstawiono podstawowe konstrukcji hosta nawigacji.  
  
 ![Diagramy nawigatora](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure15.png "NavigationOverviewFigure15")  
  
 Zasadniczo dzięki temu <xref:System.Windows.Navigation.NavigationWindow> i <xref:System.Windows.Controls.Frame> zapewnienie takie same nawigacji obsługuje który [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] miejsce, jeśli jest przeprowadzana w przeglądarce.  
  
 Oprócz funkcji <xref:System.Windows.Navigation.NavigationService> i dziennika, hosty nawigacji wykonania tych samych elementów członkowskich który <xref:System.Windows.Navigation.NavigationService> implementuje. Jest to zilustrowane w poniższym rysunku.  
  
 ![Dziennik w ramce i NavigationWindow](../../../../docs/framework/wpf/app-development/media/naivgationoverviewfigure24.png "NaivgationOverviewFigure24")  
  
 Dzięki temu program nawigacji pomocy technicznej bezpośrednio przed nimi. Może to rozważyć, jeśli należy zapewnić niestandardowe nawigacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dla <xref:System.Windows.Controls.Frame> jest hostowana w <xref:System.Windows.Window>. Ponadto obu typów implementować członków dodatkowych, związanych z nawigacji, w tym `BackStack` (<xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType>) i `ForwardStack` (<xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType>), umożliwiają wyliczyć wpisów dziennika w tle na stosie i odpowiednio przesyła stosu.  
  
 Jak wspomniano wcześniej, więcej niż jeden arkusz może istnieć w aplikacji. Następujący rysunek przedstawia przykład, gdy jest to możliwe.  
  
 ![Wiele dzienników w jednej aplikacji](../../../../docs/framework/wpf/app-development/media/naivgationoverviewfigure25.png "NaivgationOverviewFigure25")  
  
<a name="Navigating_to_Content_Other_than_Pages"></a>   
## <a name="navigating-to-content-other-than-xaml-pages"></a>Przechodzenie do zawartości innego niż strony XAML  
 W tym temacie <xref:System.Windows.Controls.Page> i dodatkiem Service pack [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] zostały już użyte do zaprezentowania różnych możliwości nawigacji [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Jednak <xref:System.Windows.Controls.Page> oznacza to skompilowany w aplikacji nie jest tylko typ zawartości, która może zostać przesłane do i dodatkiem Service pack [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] nie są jedynym sposobem, aby zidentyfikować zawartości.  
  
 Ponieważ w tej sekcji przedstawiono, można także przejść do utracić [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki, [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] plików i obiektów.  
  
<a name="Navigating_to_Loose_XAML_Files"></a>   
### <a name="navigating-to-loose-xaml-files"></a>Nawigacja do plików XAML utracić  
 Luźne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plik jest plikiem o następującej charakterystyce:  
  
-   Zawiera tylko [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (Brak kodu).  
  
-   Ma deklarację odpowiedni obszar nazw.  
  
-   Ma rozszerzenie nazwy pliku .xaml.  
  
 Rozważmy na przykład następująca zawartość, która jest przechowywana jako utracić [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku Person.xaml.  
  
 [!code-xaml[NavigationOverviewSnippets#LooseXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Person.xaml#loosexaml)]  
  
 Dwukrotne kliknięcie pliku przeglądarki zostanie otwarty i przechodzi do i wyświetla zawartość. Przedstawiono na poniższej ilustracji.  
  
 ![Wyświetlanie zawartości w pliku Person.XAML](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure21.png "NavigationOverviewFigure21")  
  
 Można wyświetlić utracić [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku z następujących czynności:  
  
-   Witryna sieci Web na komputerze lokalnym, intranetu lub Internetu.  
  
-   A [!INCLUDE[TLA#tla_unc](../../../../includes/tlasharptla-unc-md.md)] udziału plików.  
  
-   Dysk lokalny.  
  
 Luźne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plik można dodać do ulubionych w przeglądarce lub strona główna.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat publikowania i uruchamianie luźne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony, zobacz [wdrażanie aplikacji WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md).  
  
 Jednym z ograniczeń względem utracić [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest, że może zawierać tylko zawartości, którą można bezpiecznie uruchomić w częściowej relacji zaufania. Na przykład `Window` nie może być elementem głównym utracić [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku. Aby uzyskać więcej informacji, zobacz [WPF częściowego zaufania zabezpieczeń](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
<a name="Navigating_to_HTML_Files_Using_Frame"></a>   
### <a name="navigating-to-html-files-by-using-frame"></a>Nawigacja do plików HTML za pomocą ramki  
 Zgodnie z oczekiwaniami może można także przejść do [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]. Należy podać po prostu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] używającą schemat http. Na przykład następująca [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pokazuje <xref:System.Windows.Controls.Frame> która przechodzi do [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] strony.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHtmlNavMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHTMLNavPage.xaml#framehtmlnavmarkup)]  
  
 Nawigowanie do [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] wymaga specjalnych uprawnień. Na przykład nie można nawigować z [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] działa w częściowej relacji zaufania izolowanym strefy Internet. Aby uzyskać więcej informacji, zobacz [WPF częściowego zaufania zabezpieczeń](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
<a name="Navigating_to_HTML_Files_Using_WebBrowser"></a>   
### <a name="navigating-to-html-files-by-using-the-webbrowser-control"></a>Nawigacja do plików HTML za pomocą formantu WebBrowser  
 <xref:System.Windows.Controls.WebBrowser> Sterowanie obsługuje [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] hosting dokumentu, nawigacji i skrypt/zarządzanego kodu współdziałania. Aby uzyskać szczegółowe informacje dotyczące <xref:System.Windows.Controls.WebBrowser> sterowania, zobacz <xref:System.Windows.Controls.WebBrowser>.  
  
 Podobnie jak <xref:System.Windows.Controls.Frame>, nawigacyjnego do [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] przy użyciu <xref:System.Windows.Controls.WebBrowser> wymaga specjalnych uprawnień. Na przykład z częściowym zaufaniem aplikacji, można przejść tylko z [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] znajduje się w witrynie pochodzenia. Aby uzyskać więcej informacji, zobacz [WPF częściowego zaufania zabezpieczeń](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
<a name="Navigating_to_Objects"></a>   
### <a name="navigating-to-custom-objects"></a>Nawigowanie do niestandardowych obiektów  
 Jeśli dane są przechowywane jako obiektów niestandardowych, jeden sposób wyświetlania tych danych jest utworzenie <xref:System.Windows.Controls.Page> z zawartością, która jest powiązana z tych obiektów (zobacz [omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md)). Jeśli nie ma potrzeby tworzenia całej strony tak, aby wyświetlić obiekty obciążenie, można przejść bezpośrednio do nich zamiast tego.  
  
 Należy wziąć pod uwagę `Person` klasy, która jest zaimplementowana w poniższym kodzie.  
  
 [!code-csharp[NavigateToObjectSnippets#PersonClassCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/Person.cs#personclasscode)]
 [!code-vb[NavigateToObjectSnippets#PersonClassCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/Person.vb#personclasscode)]  
  
 Aby przejść do niego, należy wywołać <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A?displayProperty=nameWithType> metody, jak pokazano w następującym kodem.  
  
 [!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject1)]  
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject2)]  
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject3)]  
  
 [!code-csharp[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml.cs#pagethatnavstoobjectcodebehind)]
 [!code-vb[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/HomePage.xaml.vb#pagethatnavstoobjectcodebehind)]  
  
 Na poniższej ilustracji przedstawiono wynik.  
  
 ![Strona umożliwiająca przejście do klasy](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure22.png "NavigationOverviewFigure22")  
  
 Z tego rysunku widać, że przydatne nie będą wyświetlane żadne. W rzeczywistości wartość, która jest wyświetlana jest wartość zwracaną `ToString` metodę **osoby** obiektu; domyślnie jest to jedyny wartość [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] można używać do reprezentacji obiektu. Można zastąpić `ToString` metody do zwracania informacji bardziej zrozumiałe, mimo że będzie on nadal mieć tylko wartość ciągu. Co można użyć metody, która korzysta z funkcji prezentacji z [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jest użycie szablonu danych. Można wdrożyć szablon danych który [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] można skojarzyć z obiektu określonego typu. Poniższy kod przedstawia szablonu danych dla `Person` obiektu.  
  
 [!code-xaml[NavigateToObjectSnippets#DataTemplateMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/App.xaml#datatemplatemarkup)]  
  
 W tym miejscu szablonu danych jest skojarzony z `Person` typu przy użyciu `x:Type` — rozszerzenie znaczników w `DataType` atrybutu. Następnie wiąże szablonu danych `TextBlock` elementy (zobacz <xref:System.Windows.Controls.TextBlock>) do właściwości `Person` klasy. Na poniższej ilustracji przedstawiono wygląd zaktualizowane `Person` obiektu.  
  
 ![Przechodzenie do klasy zawierającej szablon danych](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure23.png "NavigationOverviewFigure23")  
  
 Zaletą tej metody jest spójności uzyskać dzięki możliwości ponowne użycie szablonu danych, aby wyświetlić obiekty spójnie dowolne miejsce w aplikacji.  
  
 Aby uzyskać więcej informacji w szablonach danych, zobacz [omówienie tworzenia szablonów danych](../../../../docs/framework/wpf/data/data-templating-overview.md).  
  
<a name="Security"></a>   
## <a name="security"></a>Zabezpieczenia  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Obsługa nawigacji umożliwia [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] nastąpi przejście przez Internet, a zezwala na zawartość innych firm hosta aplikacji. Do ochrony zarówno aplikacji, jak i użytkowników ze szkodliwych zachowanie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zawiera szereg funkcji zabezpieczeń, które zostały omówione w [zabezpieczeń](../../../../docs/framework/wpf/security-wpf.md) i [WPF częściowego zaufania zabezpieczeń](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Application.SetCookie%2A>  
 <xref:System.Windows.Application.GetCookie%2A>  
 [Zarządzanie aplikacjami — omówienie](../../../../docs/framework/wpf/app-development/application-management-overview.md)  
 [Pakowanie URI w WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)  
 [Strukturyzowana nawigacja — omówienie](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md)  
 [Topologia nawigacji — omówienie](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/app-development/navigation-how-to-topics.md)  
 [Wdrażanie aplikacji WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)
