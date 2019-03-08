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
ms.openlocfilehash: 7636a7d9a100d0df95f7d5462672819624ba52a4
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679973"
---
# <a name="navigation-overview"></a>Przegląd Nawigacja
Windows Presentation Foundation (WPF) obsługuje nawigacji w stylu przeglądarki, który może służyć w dwóch rodzajów aplikacji: aplikacje autonomiczne i [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]. Do zawartości pakietów do nawigacji [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zapewnia <xref:System.Windows.Controls.Page> klasy. Możesz przejść z jednego <xref:System.Windows.Controls.Page> do innego deklaratywne, przy użyciu <xref:System.Windows.Documents.Hyperlink>, lub programowo, za pomocą <xref:System.Windows.Navigation.NavigationService>. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] używa dziennika, do zapamiętania stron, które przejście z i przejdź z powrotem do ich.  
  
 <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Navigation.NavigationService>, i dziennika na formularzu core obsługi nawigacji oferowany przez [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. W tym omówieniu przedstawiono te funkcje szczegółowo przed obejmujących obsługę zaawansowanych nawigacji, która obejmuje nawigacji luźne [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] plików [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] pliki i obiekty.  
  
> [!NOTE]
>  W tym temacie termin "Przeglądarka" odnosi się tylko do przeglądarki, które mogą hostować [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji, które obecnie dotyczy to [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] i Firefox. W przypadku, gdy określone [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] funkcje są obsługiwane tylko przez konkretnej przeglądarce, wersja przeglądarki jest określone.  
   
     
## <a name="navigation-in-wpf-applications"></a>Nawigacja w aplikacjach WPF  
 Ten temat zawiera omówienie możliwości nawigacji klucza [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Te możliwości są dostępne dla obu aplikacji autonomicznej i [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], chociaż w tym temacie przedstawiono je w kontekście [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].  
  
> [!NOTE]
>  W tym temacie nie omówiono sposób tworzenia i wdrażania [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], zobacz [WPF XAML Browser Applications Overview](wpf-xaml-browser-applications-overview.md).  
  
 W tej sekcji opisano i przedstawiono następujące aspekty nawigacji:  
  
-   [Implementowanie strony](#CreatingAXAMLPage)  
  
-   [Konfigurowanie strony początkowej](#Configuring_a_Start_Page)  
  
-   [Konfigurowanie tytuł, szerokość i wysokość okna hosta](#ConfiguringAXAMLPage)  
  
-   [Nawigacja hiperłącza](#NavigatingBetweenXAMLPages)  
  
-   [Nawigacja fragmentów](#FragmentNavigation)  
  
-   [Usługa nawigacji](#NavigationService)  
  
-   [Nawigacja programowa z usługą nawigacji](#Programmatic_Navigation_with_the_Navigation_Service)  
  
-   [Okres istnienia nawigacji](#Navigation_Lifetime)  
  
-   [Uzupełnij nawigacja z użyciem arkusza](#NavigationHistory)  
  
-   [Okres istnienia strony i dziennika](#PageLifetime)  
  
-   [Zachowanie stanu zawartości za pomocą historii nawigacji](#RetainingContentStateWithNavigationHistory)  
  
-   [Plik cookie](#Cookies)  
  
-   [Strukturyzowana Nawigacja](#Structured_Navigation)  
  
<a name="CreatingAXAMLPage"></a>   
### <a name="implementing-a-page"></a>Implementowanie strony  
 W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], możesz przejść do kilku typów zawartości, które zawierają obiekty .NET Framework, niestandardowych obiektów, wartości wyliczenia, kontrolki użytkownika [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plików, a [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] plików. Jednak przekonasz się, że najbardziej typowe i wygodny sposób zawartość pakietu jest za pomocą <xref:System.Windows.Controls.Page>. Ponadto <xref:System.Windows.Controls.Page> implementuje funkcje nawigacji określonych rozbudowywać ich wygląd i uprościć programowanie.  
  
 Za pomocą <xref:System.Windows.Controls.Page>, sposób deklaratywny można zaimplementować stronę można nawigować [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zawartości przy użyciu znaczników, podobnie do poniższego.  
  
 [!code-xaml[NavigationOverviewSnippets#Page1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page1.xaml#page1xaml)]  
  
 A <xref:System.Windows.Controls.Page> jest zaimplementowana w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ma znaczników `Page` jako element główny i wymaga [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] deklarację przestrzeni nazw. `Page` Elementu z zawartością, którą chcesz przejdź do, a następnie wyświetlić. Możesz dodać zawartość, ustawiając `Page.Content` element właściwości, jak pokazano w niej następujące znaczniki.  
  
 [!code-xaml[NavigationOverviewSnippets#Page2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page2.xaml#page2xaml)]  
  
 `Page.Content` może zawierać tylko jeden element podrzędny; w poprzednim przykładzie, zawartość jest pojedynczy ciąg "Hello, strony!" W praktyce, zazwyczaj używa się kontrolkę układu jako element podrzędny (zobacz [układ](../advanced/layout.md)) do przechowywania i redagowanie zawartości.  
  
 Elementy podrzędne `Page` elementu są uważane za zawartość <xref:System.Windows.Controls.Page> i w związku z tym, nie trzeba używać jawne `Page.Content` deklaracji. Następujące znaczniki odpowiada deklaratywne do poprzedniego przykładu.  
  
 [!code-xaml[NavigationOverviewSnippets#Page3XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page3.xaml#page3xaml)]  
  
 W tym przypadku `Page.Content` automatycznie została ustawiona za pomocą elementów podrzędnych `Page` elementu. Aby uzyskać więcej informacji, zobacz [Model zawartości WPF](../controls/wpf-content-model.md).  
  
 Tylko znaczniki <xref:System.Windows.Controls.Page> przydaje się do wyświetlania zawartości. Jednak <xref:System.Windows.Controls.Page> może również formanty wyświetlania, które umożliwiają użytkownikom na interakcję ze stroną i mogą odpowiadać na interakcję z użytkownikiem, obsługa zdarzeń i wywoływanie aplikacji logiki. Interakcyjna <xref:System.Windows.Controls.Page> jest implementowany przy użyciu kombinacji znaczników i kodu powiązanego, jak pokazano w poniższym przykładzie.  
  
 [!code-xaml[XBAPAppDefSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml#homepagemarkup)]  
  
 [!code-csharp[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml.cs#homepagecodebehind)]
 [!code-vb[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/HomePage.xaml.vb#homepagecodebehind)]  
  
 Aby umożliwić pliku znaczników i pliku związanego z kodem pracy zespołowej, następująca konfiguracja jest wymagana:  
  
-   W znaczniku `Page` element musi zawierać `x:Class` atrybutu. Podczas kompilowania aplikacji, istnienie `x:Class` w znaczniku pliku powoduje, że [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] utworzyć `partial` klasę pochodzącą od <xref:System.Windows.Controls.Page> i ma nazwę, która jest określona przez `x:Class` atrybutu. Wymaga to dodania [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] deklarację przestrzeni nazw dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schematu ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ). Wygenerowany `partial` klasy implementuje `InitializeComponent`, która jest wywoływana, aby rejestrować zdarzenia i ustawić właściwości, które są implementowane w znacznikach.  
  
-   Związane z kodem, klasy musi być `partial` klasy o takiej samej nazwie, który jest określony przez `x:Class` atrybutu w kodzie znaczników oraz jego musi pochodzić od klasy <xref:System.Windows.Controls.Page>. Dzięki temu pliku związanego z kodem, który ma zostać skojarzony z `partial` klasy, który jest generowany dla pliku znaczników Po skompilowaniu aplikację (zobacz [Kompilowanie aplikacji WPF](building-a-wpf-application-wpf.md)).  
  
-   W związanym z kodem <xref:System.Windows.Controls.Page> klasy należy zaimplementować konstruktora, który wywołuje `InitializeComponent` metody. `InitializeComponent` jest implementowana przez znaczniki użytkownika wygenerowany plik `partial` klasy, aby rejestrować zdarzenia i ustawić właściwości, które są zdefiniowane w znacznikach.  
  
> [!NOTE]
>  Po dodaniu nowego <xref:System.Windows.Controls.Page> do projektu przy użyciu [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], <xref:System.Windows.Controls.Page> jest implementowany przy użyciu znaczników i związane z kodem, i zawiera niezbędną konfigurację, aby utworzyć skojarzenie między plikami znaczników i związane z kodem jako opisane w tym miejscu.  
  
 Po utworzeniu <xref:System.Windows.Controls.Page>, możesz przejść do niego. Aby określić pierwszy <xref:System.Windows.Controls.Page> czy przechodzi do strony aplikacji, musisz skonfigurować początek <xref:System.Windows.Controls.Page>.  
  
<a name="Configuring_a_Start_Page"></a>   
### <a name="configuring-a-start-page"></a>Konfigurowanie strony początkowej  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] wymaga pewnego infrastruktury aplikacji będzie hostowana w przeglądarce. W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], <xref:System.Windows.Application> klasa jest częścią definicji aplikacji, która ustanawia infrastruktury wymaganej aplikacji (zobacz [Zarządzanie aplikacjami — omówienie](application-management-overview.md)).  
  
 Definicja aplikacji zwykle jest implementowany przy użyciu znaczników i kodu powiązanego z pliku znaczników, skonfigurowany jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `ApplicationDefinition` elementu. Poniżej przedstawiono definicji aplikacji dla [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].  
  
 [!code-xaml[XBAPAppDefSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]  
  
 [!code-csharp[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml.cs#xbapapplicationdefinitioncodebehind)]
 [!code-vb[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/Application.xaml.vb#xbapapplicationdefinitioncodebehind)]  
  
 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Użyć jego definicji aplikacji, aby określić rozpoczęcia <xref:System.Windows.Controls.Page>, czyli <xref:System.Windows.Controls.Page> , jest automatycznie ładowany, gdy [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] jest uruchamiany. Możesz to zrobić, ustawiając <xref:System.Windows.Application.StartupUri%2A> właściwość o [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] dla żądaną <xref:System.Windows.Controls.Page>.  
  
> [!NOTE]
>  W większości przypadków <xref:System.Windows.Controls.Page> jest skompilowany w lub wdrożony z aplikacją. W takich przypadkach [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] określający <xref:System.Windows.Controls.Page> jest dodatkiem [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], czyli [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , zgodne ze *pakiet* schematu. Pakiet [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] zostały omówione w dalszych [pakiet URI w WPF](pack-uris-in-wpf.md). Możesz także przejść do zawartości za pomocą schemat http, które omówiono poniżej.  
  
 Możesz ustawić <xref:System.Windows.Application.StartupUri%2A> deklaratywnie w znaczniku, jak pokazano w poniższym przykładzie.  
  
 [!code-xaml[NavigationOverviewSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]  
  
 W tym przykładzie `StartupUri` ustawiono atrybut z pakietem względną [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] określający HomePage.xaml. Gdy [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] jest uruchomiony, HomePage.xaml automatyczne przejście i wyświetlić. Wskazuje na poniższej ilustracji przedstawiono [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] który został uruchomiony z serwera sieci Web.  
  
 ![Strona XBAP](./media/navigation-overview/xbap-launched-from-a-web-server.png "pokazuje XBAP uruchomione z serwera sieci Web.")  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat tworzenia i wdrażania [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], zobacz [WPF XAML Browser Applications Overview](wpf-xaml-browser-applications-overview.md) i [wdrażanie aplikacji WPF](deploying-a-wpf-application-wpf.md).  
  
<a name="ConfiguringAXAMLPage"></a>   
### <a name="configuring-the-host-windows-title-width-and-height"></a>Konfigurowanie tytuł, szerokość i wysokość okna hosta  
 Jedno, być może zauważono w poprzednim rysunku jest tytuł zarówno w przeglądarce, jak i w panelu kartę [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Oprócz trwa długo, tytuł jest atrakcyjna ani zawierającego wiele użytecznych informacji. Z tego powodu <xref:System.Windows.Controls.Page> oferuje sposób zmienić tytuł przez ustawienie <xref:System.Windows.Controls.Page.WindowTitle%2A> właściwości. Ponadto można skonfigurować szerokość i wysokość okna przeglądarki, ustawiając <xref:System.Windows.Controls.Page.WindowWidth%2A> i <xref:System.Windows.Controls.Page.WindowHeight%2A>, odpowiednio.  
  
 <xref:System.Windows.Controls.Page.WindowTitle%2A>, <xref:System.Windows.Controls.Page.WindowWidth%2A>, i <xref:System.Windows.Controls.Page.WindowHeight%2A> można ustawić deklaratywnie w znaczniku, jak pokazano w poniższym przykładzie.  
  
 [!code-xaml[NavigationOverviewSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/HomePage.xaml#homepagemarkup)]  
  
 Wynik jest wyświetlany na poniższej ilustracji.  
  
 ![Tytuł okna, wysokość i szerokość](./media/navigation-overview/window-title-width-height.png "pokazuje tytuł okna, wysokość i szerokość można skonfigurować.")  
  
<a name="NavigatingBetweenXAMLPages"></a>   
### <a name="hyperlink-navigation"></a>Nawigacja hiperłącza  
 Typowa [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] obejmuje kilka stron. Najprostszym sposobem, aby przejść z jednej strony do innej jest użycie <xref:System.Windows.Documents.Hyperlink>. Można dodać deklaratywne <xref:System.Windows.Documents.Hyperlink> do <xref:System.Windows.Controls.Page> przy użyciu `Hyperlink` element, który jest wyświetlany w niej następujące znaczniki.  
  
 [!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]  
  
 A `Hyperlink` element wymaga następujących czynności:  
  
-   Ten pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] z <xref:System.Windows.Controls.Page> przejdź do, zgodnie z określonym `NavigateUri` atrybutu.  
  
-   Zawartości, czy użytkownik może kliknąć do zainicjowania nawigacji, takie jak tekst i obrazy (zawartości, która `Hyperlink` element może zawierać, zobacz <xref:System.Windows.Documents.Hyperlink>).  
  
 Poniższy rysunek przedstawia [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] z <xref:System.Windows.Controls.Page> zawierający <xref:System.Windows.Documents.Hyperlink>.  
  
 ![Strona z hiperłączem](./media/navigation-overview/xbap-with-a-page-with-a-hyperlink.png "pokazuje XBAP ze stroną z hiperłączem.")  
  
 Jak można oczekiwać, klikając <xref:System.Windows.Documents.Hyperlink> powoduje, że [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] można przejść do <xref:System.Windows.Controls.Page> identyfikowane przez `NavigateUri` atrybutu. Ponadto [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] dodaje wpis z poprzednich <xref:System.Windows.Controls.Page> do listy ostatnich stron w [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]. Jest to pokazane na poniższej ilustracji.  
  
 ![Przyciski Wstecz i dalej](./media/navigation-overview/back-and-forward-navigation.png "Nawiguj za pomocą przycisków do przodu i Wstecz.")  
  
 Oprócz obsługi nawigacji z jednego <xref:System.Windows.Controls.Page> do innego, <xref:System.Windows.Documents.Hyperlink> również obsługuje fragmentu nawigacji.  
  
<a name="FragmentNavigation"></a>   
### <a name="fragment-navigation"></a>Nawigacja fragmentów  
 *Fragment nawigacji* jest nawigacji do fragmentu zawartości albo bieżącego <xref:System.Windows.Controls.Page> lub inne <xref:System.Windows.Controls.Page>. W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], fragmentu zawartości jest zawartość, który jest zawarty w nazwanego elementu. Element nazwany jest element, który ma jej `Name` atrybut. Poniższy kod przedstawia nazwane `TextBlock` element, który zawiera fragmentu zawartości.  
  
 [!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup1)]  
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup2)]  
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup3)]  
  
 Aby uzyskać <xref:System.Windows.Documents.Hyperlink> do nawigacji do fragmentu zawartości `NavigateUri` atrybutu musi zawierać następujące czynności:  
  
-   [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] z <xref:System.Windows.Controls.Page> z fragmentu zawartości, aby przejść do.  
  
-   A "#" character.  
  
-   Nazwa elementu na <xref:System.Windows.Controls.Page> zawierający fragmentu zawartości.  
  
 Fragment [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] ma następujący format.  
  
 *PageURI* `#` *ElementName*  
  
 Poniżej pokazano przykład `Hyperlink` skonfigurowanego do nawigacji do fragmentu zawartości.  
  
 [!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml1)]  
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml2)]  
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml3)]  
  
> [!NOTE]
>  W tej sekcji opisano Domyślna implementacja nawigacji fragmentu w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Umożliwia także zaimplementować własny schemat nawigacji fragmentu, który w całości, wymaga obsługi <xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType> zdarzeń.  
  
> [!IMPORTANT]
>  Możesz przejść do fragmentów w luźne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stron (tylko znaczniki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki z `Page` jako element główny) tylko wtedy, gdy strony można przeglądać za pomocą [!INCLUDE[TLA2#tla_http](../../../../includes/tla2sharptla-http-md.md)].  
>   
>  Jednak nie będzie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony można przejść do jego własnej fragmentów.  
  
<a name="NavigationService"></a>   
### <a name="navigation-service"></a>Navigation Service  
 Gdy <xref:System.Windows.Documents.Hyperlink> zezwala użytkownikowi na zainicjowanie Nawigacja do konkretnej <xref:System.Windows.Controls.Page>, zadanie lokalizowania i pobierania strony jest wykonywane przez <xref:System.Windows.Navigation.NavigationService> klasy. Zasadniczo <xref:System.Windows.Navigation.NavigationService> zapewnia możliwość przetwarzania żądania nawigacji w imieniu kodu klienta, takich jak <xref:System.Windows.Documents.Hyperlink>. Ponadto <xref:System.Windows.Navigation.NavigationService> TFTP implementuje obsługę wyższego poziomu śledzenia i wywieranie wpływu na żądanie nawigacji.  
  
 Gdy <xref:System.Windows.Documents.Hyperlink> po kliknięciu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wywołania <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> Aby znaleźć i pobrać <xref:System.Windows.Controls.Page> w określonym pakiecie [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Pobrany <xref:System.Windows.Controls.Page> jest konwertowana na drzewie obiektów, których główny obiekt jest wystąpieniem pobrany <xref:System.Windows.Controls.Page>. Odwołanie do katalogu głównego <xref:System.Windows.Controls.Page> obiekt jest przechowywany w <xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType> właściwości. Ten pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla zawartości, która została przejście, są przechowywane w <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> właściwości podczas <xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType> przechowuje pakietowi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] ostatniej strony, który został przejście.  
  
> [!NOTE]
>  Możliwe jest [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji do więcej niż jednego aktywnego <xref:System.Windows.Navigation.NavigationService>. Aby uzyskać więcej informacji, zobacz [hosty nawigacji](#Navigation_Hosts) w dalszej części tego tematu.  
  
<a name="Programmatic_Navigation_with_the_Navigation_Service"></a>   
### <a name="programmatic-navigation-with-the-navigation-service"></a>Nawigacja programowa z usługą nawigacji  
 Nie musisz wiedzieć o <xref:System.Windows.Navigation.NavigationService> Jeśli nawigacji jest zaimplementowana w sposób deklaratywny przy użyciu znaczników <xref:System.Windows.Documents.Hyperlink>, ponieważ <xref:System.Windows.Documents.Hyperlink> używa <xref:System.Windows.Navigation.NavigationService> w Twoim imieniu. Oznacza to, że tak długo, jak bezpośrednie lub pośrednie nadrzędnego elementu <xref:System.Windows.Documents.Hyperlink> jest hostem nawigacji (zobacz [hosty nawigacji](#Navigation_Hosts)), <xref:System.Windows.Documents.Hyperlink> będą mogli odnaleźć i zacząć używać usługi nawigacji hosta nawigacji do przetworzenia żądania nawigacji.  
  
 Jednak istnieją sytuacje, gdy trzeba użyć <xref:System.Windows.Navigation.NavigationService> bezpośrednio, w tym następujące czynności:  
  
-   Gdy zachodzi potrzeba utworzenia wystąpienia <xref:System.Windows.Controls.Page> za pomocą konstruktora innych niż domyślne.  
  
-   Aby ustawić właściwości <xref:System.Windows.Controls.Page> zanim przejdziesz do niego.  
  
-   Gdy <xref:System.Windows.Controls.Page> że potrzebuje do nastąpi przejście, tylko można określić w czasie wykonywania.  
  
 W takich sytuacjach należy napisać kod, aby programowo zainicjować nawigacji, wywołując <xref:System.Windows.Navigation.NavigationService.Navigate%2A> metody <xref:System.Windows.Navigation.NavigationService> obiektu. Wymagającym pobieranie odwołania do <xref:System.Windows.Navigation.NavigationService>.  
  
#### <a name="getting-a-reference-to-the-navigationservice"></a>Pobieranie odwołania do NavigationService  
 Przyczyn, które zostały omówione w [hosty nawigacji](#Navigation_Hosts) sekcji [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacja może mieć więcej niż jedną <xref:System.Windows.Navigation.NavigationService>. Oznacza to, że kod musi mieć możliwość znalezienia <xref:System.Windows.Navigation.NavigationService>, co jest zazwyczaj <xref:System.Windows.Navigation.NavigationService> przejście bieżącego <xref:System.Windows.Controls.Page>. Możesz uzyskać odwołanie do <xref:System.Windows.Navigation.NavigationService> przez wywołanie metody `static` <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A?displayProperty=nameWithType> metody. Aby uzyskać <xref:System.Windows.Navigation.NavigationService> , przejście do określonego <xref:System.Windows.Controls.Page>, należy przekazać odwołanie do <xref:System.Windows.Controls.Page> jako argument <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A> metody. Poniższy kod ilustruje sposób pobrania <xref:System.Windows.Navigation.NavigationService> dla bieżącego <xref:System.Windows.Controls.Page>.  
  
 [!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPage.xaml.vb#getnscodebehind2)]  
  
 Jako skrót do wyszukiwania <xref:System.Windows.Navigation.NavigationService> dla <xref:System.Windows.Controls.Page>, <xref:System.Windows.Controls.Page> implementuje <xref:System.Windows.Controls.Page.NavigationService%2A> właściwości. Jest to pokazane w poniższym przykładzie.  
  
 [!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPageShortCut.xaml.vb#getnsshortcutcodebehind2)]  
  
> [!NOTE]
>  A <xref:System.Windows.Controls.Page> mogą uzyskać jedynie odwołanie do jego <xref:System.Windows.Navigation.NavigationService> podczas <xref:System.Windows.Controls.Page> zgłasza <xref:System.Windows.FrameworkElement.Loaded> zdarzeń.  
  
#### <a name="programmatic-navigation-to-a-page-object"></a>Nawigacja programowa do obiektu strony  
 Poniższy przykład pokazuje, jak używać <xref:System.Windows.Navigation.NavigationService> programowo przejdź do <xref:System.Windows.Controls.Page>. Nawigacja programowa jest wymagana, ponieważ <xref:System.Windows.Controls.Page> oznacza to przejście tak, aby tylko wystąpienia można tworzyć za pomocą konstruktora pojedynczy, innych niż domyślne. <xref:System.Windows.Controls.Page> Przy użyciu konstruktora domyślnego nie jest wyświetlany w następujących znaczników i kodu.  
  
 [!code-xaml[NavigationOverviewSnippets#PageWithNonDefaultConstructorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml#pagewithnondefaultconstructorxaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml.cs#pagewithnondefaultconstructorcodebehind)]
 [!code-vb[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithNonDefaultConstructor.xaml.vb#pagewithnondefaultconstructorcodebehind)]  
  
 <xref:System.Windows.Controls.Page> , Przechodzi do <xref:System.Windows.Controls.Page> przy użyciu konstruktora domyślnego nie jest wyświetlany w następujących znaczników i kodu.  
  
 [!code-xaml[NavigationOverviewSnippets#NSNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml#nsnavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml.cs#nsnavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSNavigationPage.xaml.vb#nsnavigationpagecodebehind)]  
  
 Gdy <xref:System.Windows.Documents.Hyperlink> na tym <xref:System.Windows.Controls.Page> jest kliknięciu nawigacji jest inicjowane przez utworzenie wystąpienia <xref:System.Windows.Controls.Page> można przejść do przy użyciu innego niż domyślny konstruktor i wywoływać metodę <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> metody. <xref:System.Windows.Navigation.NavigationService.Navigate%2A> akceptuje odwołanie do obiektu, który <xref:System.Windows.Navigation.NavigationService> spowoduje przejście do, a nie pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
#### <a name="programmatic-navigation-with-a-pack-uri"></a>Nawigacja programowa za pomocą identyfikatora URI pakietu  
 Jeśli musisz utworzyć pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] programowo (jeśli można określić tylko pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] w czasie wykonywania, na przykład), można użyć <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> metody. Jest to pokazane w poniższym przykładzie.  
  
 [!code-xaml[NavigationOverviewSnippets#NSUriNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml#nsurinavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml.cs#nsurinavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSUriNavigationPage.xaml.vb#nsurinavigationpagecodebehind)]  
  
#### <a name="refreshing-the-current-page"></a>Odświeżanie na bieżącej stronie  
 A <xref:System.Windows.Controls.Page> nie jest pobierana, jeśli ma ona tego samego pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] co pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] przechowywaną w <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> właściwości. Aby wymusić [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ponownie pobrać bieżącej strony, można wywołać <xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType> metodzie, jak pokazano w poniższym przykładzie.  
  
 [!code-xaml[NavigationOverviewSnippets#NSRefreshNavigationPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml#nsrefreshnavigationpagexaml1)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind1)]
 [!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind2)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind2)]  
  
<a name="Navigation_Lifetime"></a>   
### <a name="navigation-lifetime"></a>Okres istnienia nawigacji  
 Istnieje wiele sposobów, aby zainicjować nawigacji, w tym samouczku. Po zainicjowaniu nawigacji i nawigacji w trakcie, mogą śledzić i wpłynąć nawigacyjne przy użyciu następujących zdarzeń, które są implementowane przez <xref:System.Windows.Navigation.NavigationService>:  
  
-   <xref:System.Windows.Navigation.NavigationService.Navigating>. Występuje, gdy wymagane jest nową nawigację. Może służyć do anulowania nawigacji.  
  
-   <xref:System.Windows.Navigation.NavigationService.NavigationProgress>. Występuje okresowo podczas pobierania i udostępnia informacje o postępie nawigacji.  
  
-   <xref:System.Windows.Navigation.NavigationService.Navigated>. Występuje, gdy strona została znajduje się i pobrane.  
  
-   <xref:System.Windows.Navigation.NavigationService.NavigationStopped>. Występuje po zatrzymaniu nawigacji (przez wywołanie metody <xref:System.Windows.Navigation.NavigationService.StopLoading%2A>), lub gdy nowa Nawigacja zostanie zgłoszone, gdy bieżący nawigacji jest w toku.  
  
-   <xref:System.Windows.Navigation.NavigationService.NavigationFailed>. Występuje, gdy występuje błąd podczas nawigowania do żądanej zawartości.  
  
-   <xref:System.Windows.Navigation.NavigationService.LoadCompleted>. Występuje, gdy zawartość, która została przejście zostanie załadowany i przeanalizować i rozpoczął renderowania.  
  
-   <xref:System.Windows.Navigation.NavigationService.FragmentNavigation>. Występuje po rozpoczęciu nawigacji do fragmentu zawartości, która się dzieje:  
  
    -   Natychmiast Jeśli żądany fragment znajduje się w bieżącej zawartości.  
  
    -   Po źródło zawartości został załadowany, jeśli żądany fragment znajduje się w innej zawartości.  
  
 Zdarzenia nawigacji są wywoływane w kolejności to zilustrowane w poniższym rysunku.  
  
 ![Schemat blokowy nawigacji strony](./media/navigation-overview/order-of-navigation-events.png "schematu blokowego zdarzeń nawigacji strony")  
  
 Ogólnie rzecz biorąc <xref:System.Windows.Controls.Page> nie ma danych dotyczących tych zdarzeń. Jest bardziej prawdopodobne, że aplikacja jest rozpatrywany wraz z ich i z tego powodu te zdarzenia są również inicjowane przez <xref:System.Windows.Application> klasy:  
  
-   <xref:System.Windows.Application.Navigating?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.NavigationProgress?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.Navigated?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.NavigationFailed?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.NavigationStopped?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.LoadCompleted?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.FragmentNavigation?displayProperty=nameWithType>  
  
 Za każdym razem, gdy <xref:System.Windows.Navigation.NavigationService> wywołuje zdarzenie, <xref:System.Windows.Application> klasa wywołuje odpowiednie zdarzenie. <xref:System.Windows.Controls.Frame> i <xref:System.Windows.Navigation.NavigationWindow> oferuje te same zdarzenia do wykrywania nawigacji w odpowiednich zakresach.  
  
 W niektórych przypadkach <xref:System.Windows.Controls.Page> mogą być zainteresowane tych zdarzeń. Na przykład <xref:System.Windows.Controls.Page> może obsługiwać <xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType> zdarzenia w celu określenia, czy można anulować nawigacji od samego. Jest to pokazane w poniższym przykładzie.  
  
 [!code-xaml[NavigationOverviewSnippets#CancelNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml#cancelnavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml.cs#cancelnavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/CancelNavigationPage.xaml.vb#cancelnavigationpagecodebehind)]  
  
 Jeśli program obsługi można zarejestrować za pomocą zdarzenia nawigacji z <xref:System.Windows.Controls.Page>, podobnie jak poprzedni przykład, musisz wyrejestrować program obsługi zdarzeń. Jeśli nie, może być efekty uboczne w odniesieniu do jak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pamięta nawigacji <xref:System.Windows.Controls.Page> Nawigowanie przy użyciu arkusza.  
  
<a name="NavigationHistory"></a>   
### <a name="remembering-navigation-with-the-journal"></a>Uzupełnij nawigacja z użyciem arkusza  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] używa dwóch stosów do zapamiętania stron, które mają przejście z: stos Wstecz i do przodu stosu. Po przejściu z bieżącego <xref:System.Windows.Controls.Page> na nową <xref:System.Windows.Controls.Page> lub do przodu do istniejącego <xref:System.Windows.Controls.Page>, bieżący <xref:System.Windows.Controls.Page> jest dodawany do *stosu wstecz*. Po przejściu z bieżącego <xref:System.Windows.Controls.Page> do poprzedniego <xref:System.Windows.Controls.Page>, bieżący <xref:System.Windows.Controls.Page> jest dodawany do *stosu do przodu*. Stos Wstecz, do przodu stosu i funkcje w celu zarządzania nimi, są nazywane zbiorczo arkusza. Każdy element w stosie do przodu i Wstecz stosu jest wystąpieniem <xref:System.Windows.Navigation.JournalEntry> klasy i jest określany jako *pozycja dziennika*.  
  
#### <a name="navigating-the-journal-from-internet-explorer"></a>Przejdź do dziennika w programie Internet Explorer  
 Model ten dziennik działa tak samo sposób **ponownie** i **do przodu** przycisków w [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] zrobić. Są one wyświetlane na poniższej ilustracji.  
  
 ![Przyciski Wstecz i dalej](./media/navigation-overview/back-and-forward-navigation.png "Nawiguj za pomocą przycisków do przodu i Wstecz.")  
  
 Aby uzyskać [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] obsługiwane przez [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] integruje arkusza w nawigacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]. Dzięki temu użytkownicy mogą przejść do strony w [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] przy użyciu **ponownie**, **do przodu**, i **ostatnie strony** przycisków w [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]. Arkusz nie został zintegrowany ze [!INCLUDE[TLA2#tla_ie6](../../../../includes/tla2sharptla-ie6-md.md)] w taki sam sposób, jest on przeznaczony dla [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)] lub Internet Explorer 8. Zamiast tego [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] renderuje Nawigacja Zastąp [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
> [!IMPORTANT]
>  W [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], gdy użytkownik nawiguje opuszczenie i z powrotem do [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], tylko wpisy dziennika dla stron, które nie zostały zachowane aktywności są przechowywane w dzienniku. Omówienie na utrzymywaniu działającej strony jest aktywny, zobacz [okres istnienia strony i dziennika](#PageLifetime) w dalszej części tego tematu.  
  
 Domyślnie tekst dla każdego <xref:System.Windows.Controls.Page> wyświetlany w **ostatnie strony** listę [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] jest [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla <xref:System.Windows.Controls.Page>. W wielu przypadkach nie jest to szczególnie istotne dla użytkownika. Na szczęście możesz zmienić tekst przy użyciu jednej z następujących opcji:  
  
1.  Dołączony `JournalEntry.Name` wartość atrybutu.  
  
2.  `Page.Title` Wartość atrybutu.  
  
3.  `Page.WindowTitle` Wartość atrybutu i [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla bieżącego <xref:System.Windows.Controls.Page>.  
  
4.  [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Dla bieżącego <xref:System.Windows.Controls.Page>. (Domyślnie)  
  
 Kolejność, w którym te opcje wymieniono jest zgodna z kolejnością pierwszeństwo służące do znajdowania tekstu. Na przykład jeśli `JournalEntry.Name` jest ustawiony, inne wartości są ignorowane.  
  
 W poniższym przykładzie użyto `Page.Title` atrybutu, aby zmienić tekst, który pojawia się dla wpisu dziennika.  
  
 [!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup1)]  
[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup2)]  
  
 [!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind1)]
 [!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind2)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind2)]  
  
#### <a name="navigating-the-journal-using-wpf"></a>Przejdź do dziennika przy użyciu programu WPF  
 Mimo że można przejść użytkownik arkusza za pomocą **ponownie**, **do przodu**, i **ostatnie strony** w [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], możesz także przejść dziennika przy użyciu zarówno deklaracyjne i programowe udostępnionych przez nią mechanizmów [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Jednym z powodów w tym celu jest zapewnienie własnej nawigacji [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] na swoich stronach.  
  
 Obsługa nawigacji dziennika deklaratywne można dodać za pomocą polecenia nawigacji udostępniane przez <xref:System.Windows.Input.NavigationCommands>. Poniższy przykład pokazuje sposób użycia `BrowseBack` polecenie nawigacji.  
  
 [!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml1)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml2)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml3)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML4](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml4)]  
  
 Możesz programowo przejść dziennika przy użyciu jednej z następujących członków <xref:System.Windows.Navigation.NavigationService> klasy:  
  
-   <xref:System.Windows.Navigation.NavigationService.GoBack%2A>  
  
-   <xref:System.Windows.Navigation.NavigationService.GoForward%2A>  
  
-   <xref:System.Windows.Navigation.NavigationService.CanGoBack%2A>  
  
-   <xref:System.Windows.Navigation.NavigationService.CanGoForward%2A>  
  
 Ten dziennik również można modyfikować programowo, zgodnie z opisem w [oporowe stan zawartości z historią nawigacji](#RetainingContentStateWithNavigationHistory) w dalszej części tego tematu.  
  
<a name="PageLifetime"></a>   
### <a name="page-lifetime-and-the-journal"></a>Okres istnienia strony i dziennika  
 Należy wziąć pod uwagę [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] z kilku stron, które zawierają sformatowanej zawartości, łącznie z grafiki, animacji i media. Zużycie pamięci dla stron, takie jak te może być bardzo duże, szczególnie w przypadku, gdy wideo i audio nośniki są używane. Biorąc pod uwagę, że dziennik "pamięta" stron, które zostały nawigować do, na przykład [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] można szybko wykorzystać zauważalne i dużych ilości pamięci.  
  
 Z tego powodu domyślne zachowanie dziennika jest zapisanie <xref:System.Windows.Controls.Page> metadanych w każdego wpisu dziennika, a nie odwołaniem do <xref:System.Windows.Controls.Page> obiektu. Gdy wpis dziennika jest przejście do jego <xref:System.Windows.Controls.Page> metadane są używane do utworzenia nowego wystąpienia określonego <xref:System.Windows.Controls.Page>. W konsekwencji każdego <xref:System.Windows.Controls.Page> jest przejście, który ma czas istnienia, który jest zilustrowany przez poniższej ilustracji.  
  
 ![Okres istnienia strony](./media/navigation-overview/navigated-page-lifetime.png "pokazuje okres istnienia, gdy strona jest przejście.")  
  
 Mimo że przy użyciu domyślnego zachowania rejestrowania można zapisać na zużycie pamięci, może ulec zmniejszeniu wydajności renderowania na stronę; reinstantiating <xref:System.Windows.Controls.Page> może znacznie obciążać czasu, szczególnie w przypadku, gdy ma ona dużo zawartości. Jeśli chcesz zachować <xref:System.Windows.Controls.Page> wystąpienia w dzienniku, można narysować w dwie techniki, aby to zrobić. Po pierwsze, programowo można przejść do <xref:System.Windows.Controls.Page> obiektu przez wywołanie metody <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> metody.  
  
 Po drugie, można określić, że [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zachować wystąpienie <xref:System.Windows.Controls.Page> w dzienniku, ustawiając <xref:System.Windows.Controls.Page.KeepAlive%2A> właściwości `true` (wartość domyślna to `false`). Jak pokazano w poniższym przykładzie, można ustawić <xref:System.Windows.Controls.Page.KeepAlive%2A> deklaratywnie w znacznikach.  
  
 [!code-xaml[NavigationOverviewSnippets#KeepAlivePageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/KeepAlivePage.xaml#keepalivepagexaml)]  
  
 Okres istnienia <xref:System.Windows.Controls.Page> czyli życiu kliknięcia różni się od jednego, który nie jest. Po raz pierwszy <xref:System.Windows.Controls.Page> , są przechowywane aktywności jest przejście, zostanie uruchomiony, podobnie jak <xref:System.Windows.Controls.Page> który nie mieści się aktywny. Jednakże ponieważ wystąpienie <xref:System.Windows.Controls.Page> są przechowywane w dzienniku, nigdy nie konkretyzacji ponownie dla tak długo, jak długo pozostaje w dzienniku. W związku z tym jeśli <xref:System.Windows.Controls.Page> ma logiki inicjowania, należy wywołać, każdym razem, gdy <xref:System.Windows.Controls.Page> jest przejście, należy go przenieść z konstruktora — w tym do obsługi dla <xref:System.Windows.FrameworkElement.Loaded> zdarzeń. Jak pokazano na poniższej ilustracji <xref:System.Windows.FrameworkElement.Loaded> i <xref:System.Windows.FrameworkElement.Unloaded> nadal są generowane każdorazowo zdarzenia <xref:System.Windows.Controls.Page> jest kierowana do i z, odpowiednio.  
  
 ![Kiedy są generowane zdarzenia załadowany i nie załadowany](./media/navigation-overview/loaded-and-unloaded-events.png "załadowany i zdarzenia zwolnione są wywoływane, gdy strona jest kierowana do i z.")  
  
 Gdy <xref:System.Windows.Controls.Page> jest nie życiu, nie powinien wykonać następujące czynności:  
  
-   Store odwołanie do lub dowolnej jego części.  
  
-   Zarejestruj procedury obsługi zdarzeń za pomocą zdarzeń, które nie są implementowane przez nią.  
  
 Każda z tych czynności spowoduje utworzenie odwołania, które wymuszają <xref:System.Windows.Controls.Page> ma zostać zachowana w pamięci, nawet po, został usunięty z arkusza.  
  
 Ogólnie rzecz biorąc, preferowaną wartość domyślna <xref:System.Windows.Controls.Page> zachowanie nie <xref:System.Windows.Controls.Page> podtrzymywania połączenia. Ma to jednak wpływ stanu, które zostały omówione w następnej sekcji.  
  
<a name="RetainingContentStateWithNavigationHistory"></a>   
### <a name="retaining-content-state-with-navigation-history"></a>Zachowanie stanu zawartości za pomocą historii nawigacji  
 Jeśli <xref:System.Windows.Controls.Page> nie mieści się aktywny, i formanty, które zbierają dane od użytkownika, co się stanie z danymi, jeśli użytkownik przejdzie opuszczenie i z powrotem do <xref:System.Windows.Controls.Page>? Z punktu widzenia użytkownika środowisko użytkownika powinno pojawić się dane, które są wprowadzone wcześniej. Niestety ponieważ nowe wystąpienie klasy <xref:System.Windows.Controls.Page> jest tworzona przy użyciu każdego nawigacji, formanty, że reinstantiated są zbierane dane i dane zostaną utracone.  
  
 Na szczęście arkusza zapewnia obsługę zapamiętywanie danych między <xref:System.Windows.Controls.Page> dokonywania nawigacji, włącznie z danymi formantu. W szczególności wpisu dziennika dla każdego <xref:System.Windows.Controls.Page> działa jako kontener tymczasowego dla skojarzonego <xref:System.Windows.Controls.Page> stanu. Poniższe kroki opisują, jak ta funkcja jest używana podczas <xref:System.Windows.Controls.Page> jest przejście od:  
  
1.  Wpis dla bieżącego <xref:System.Windows.Controls.Page> jest dodawany do dziennika.  
  
2.  Stan <xref:System.Windows.Controls.Page> są przechowywane z wpisu dziennika dla tej strony, która jest dodawana do tyłu stosu.  
  
3.  Nowy <xref:System.Windows.Controls.Page> jest przejście.  
  
 Po stronie <xref:System.Windows.Controls.Page> jest przejście do, przy użyciu arkusza, poniższe kroki wykonane:  
  
1.  <xref:System.Windows.Controls.Page> Konkretyzacji (wpis dziennika najważniejsze na stosie wstecz).  
  
2.  <xref:System.Windows.Controls.Page> Jest odświeżane przy użyciu stanu, w którym została zapisana przy użyciu wpisu dziennika dla <xref:System.Windows.Controls.Page>.  
  
3.  <xref:System.Windows.Controls.Page> Jest kierowana do.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] automatycznie używa tej obsługi stosowania następujące elementy sterujące na <xref:System.Windows.Controls.Page>:  
  
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
  
 Jeśli <xref:System.Windows.Controls.Page> używa tych formantów, dane wprowadzone w nich zapamiętywane jest między <xref:System.Windows.Controls.Page> tego, jak pokazano w **ulubiony kolor** <xref:System.Windows.Controls.ListBox> na poniższej ilustracji.  
  
 ![Strona z kontrolkami, które należy pamiętać, stan](./media/navigation-overview/data-remembered-across-page-navigations.png "strony tego zapamiętywane jest wprowadzanych danych.")  
  
 Gdy <xref:System.Windows.Controls.Page> zawiera też kontrolki służące innym niż te na powyższej liście, lub gdy stan są przechowywane w obiektach niestandardowych, należy napisać kod, aby spowodować, że dziennik do zapamiętania stanu na <xref:System.Windows.Controls.Page> dokonywania nawigacji.  
  
 Jeśli musisz pamiętać małych fragmentów stanu na <xref:System.Windows.Controls.Page> tego, można użyć właściwości zależności (zobacz <xref:System.Windows.DependencyProperty>), są skonfigurowane przy użyciu <xref:System.Windows.FrameworkPropertyMetadata.Journal%2A?displayProperty=nameWithType> flagi metadanych.  
  
 Jeśli stan, Twoje <xref:System.Windows.Controls.Page> musi zapamiętać tego składa się z wielu fragmentów danych, może okazać się mniejszej ilości kodu intensywnie korzystających z hermetyzacji swój stan, w jedną klasę i zaimplementować <xref:System.Windows.Navigation.IProvideCustomContentState> interfejsu.  
  
 Jeśli trzeba przejść za pomocą różnych stanów pojedynczej <xref:System.Windows.Controls.Page>, bez przechodzenia z <xref:System.Windows.Controls.Page> , możesz użyć <xref:System.Windows.Navigation.IProvideCustomContentState> i <xref:System.Windows.Navigation.NavigationService.AddBackEntry%2A?displayProperty=nameWithType>.  
  
<a name="Cookies"></a>   
### <a name="cookies"></a>Pliki cookie  
 Inny sposób [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dane mogą być magazynowane w aplikacji jest za pomocą plików cookie, które są tworzone, aktualizować i usuwać za pomocą <xref:System.Windows.Application.SetCookie%2A> i <xref:System.Windows.Application.GetCookie%2A> metody. Pliki cookie, które można tworzyć w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tych samych plików cookie oznacza innych typów aplikacji sieci Web użyj; pliki cookie są dowolnych fragmentów danych, które są przechowywane przez aplikację na komputerze klienckim podczas lub między sesjami aplikacji. Dane pliku cookie ma zwykle postać pary nazwa/wartość w następującym formacie.  
  
 *Nazwa* `=` *wartość*  
  
 Gdy dane są przekazywane do <xref:System.Windows.Application.SetCookie%2A>, wraz z <xref:System.Uri> lokalizacji, dla którego plik cookie powinna być ustawiona, plik cookie jest tworzony w pamięci i jest on dostępny tylko na czas trwania bieżącej sesji aplikacji. Ten typ pliku cookie jest nazywany *pliku cookie sesji*.  
  
 Do przechowywania plików cookie między aplikacjami, datę wygaśnięcia, należy dodać do pliku cookie, w następującym formacie.  
  
 *NAZWA* `=` *WARTOŚĆ* `; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`  
  
 Plik cookie z datą wygaśnięcia znajduje się w bieżącym [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] katalogu Temporary Internet Files instalacji do momentu wygaśnięcia ważności pliku cookie. Taki plik cookie jest znany jako *trwały plik cookie* ponieważ utrzymuje się między sesjami aplikacji.  
  
 Pobieranie sesji i trwałe pliki cookie, wywołując <xref:System.Windows.Application.GetCookie%2A> jest metoda <xref:System.Uri> lokalizacji, w którym plik cookie została ustawiona za pomocą <xref:System.Windows.Application.SetCookie%2A> metody.  
  
 Poniżej przedstawiono kilka sposobów, które pliki cookie są obsługiwane w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]:  
  
-   [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Aplikacje autonomiczne i [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] zarówno tworzyć i zarządzać plików cookie.  
  
-   Pliki cookie, które są tworzone przez [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] jest możliwy za pomocą przeglądarki.  
  
-   [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] w tej samej domenie mogą tworzyć i udostępniać pliki cookie.  
  
-   [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] i [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] stron w tej samej domenie, można tworzyć i udostępniać pliki cookie.  
  
-   Pliki cookie są wysyłane po [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] i utracić wprowadzone [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stron wysyłać żądania sieci Web.  
  
-   Zarówno najwyższego poziomu [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] i [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] hostowane w ramek IFRAME mogą uzyskiwać dostęp do plików cookie.  
  
-   Obsługa plików cookie w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jest taka sama dla wszystkich obsługiwanych przeglądarek.  
  
-   W [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], P3P zasad, które odnoszą się do plików cookie jest uznawane za [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], szczególnie w odniesieniu do firmy Microsoft i innych firm [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
<a name="Structured_Navigation"></a>   
### <a name="structured-navigation"></a>Strukturyzowana Nawigacja  
 Jeśli musisz przekazać dane z jednego <xref:System.Windows.Controls.Page> do innego, dane można przekazać jako argumenty dla konstruktora innych niż domyślne <xref:System.Windows.Controls.Page>. Należy pamiętać, że jeśli używasz tej techniki, należy pozostawić <xref:System.Windows.Controls.Page> aktywności; Jeśli nie, przy następnym przejściu do sekcji <xref:System.Windows.Controls.Page>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ponownie tworzy wystąpienie <xref:System.Windows.Controls.Page> przy użyciu domyślnego konstruktora.  
  
 Alternatywnie Twoje <xref:System.Windows.Controls.Page> można zaimplementować właściwości, które są konfigurowane przy użyciu danych, które należy przekazać. Elementy stają się trudne, jednak, gdy <xref:System.Windows.Controls.Page> potrzebuje do przekazania danych z powrotem do <xref:System.Windows.Controls.Page> , przejście do niej. Problem polega na to, że nawigacji nie obsługuje natywnie mechanizmy do zagwarantowania, że <xref:System.Windows.Controls.Page> będą zwracane po jest kierowana z. Zasadniczo nawigacji nie obsługują semantyki wywołanie/powrotu. Aby rozwiązać ten problem, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zapewnia <xref:System.Windows.Navigation.PageFunction%601> klasę, która służy do upewnij się, że <xref:System.Windows.Controls.Page> zwracany jest w sposób przewidywalny i ze strukturą. Aby uzyskać więcej informacji, zobacz [ze strukturą Przegląd Nawigacja](structured-navigation-overview.md).  
  
<a name="The_NavigationWindow_Class"></a>   
## <a name="the-navigationwindow-class"></a>Navigationwindow — klasa  
 Do tej pory przedstawiono gamę usług nawigacji, które najprawdopodobniej służące do tworzenia aplikacji przy użyciu zawartości można nawigować. Usługi te zostały omówione w kontekście [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], chociaż nie są ograniczone do [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Nowoczesne systemy operacyjne i aplikacje Windows zalet przeglądania nowoczesnych użytkowników Włączanie nawigacji w stylu przeglądarki do aplikacji autonomicznej. Typowe przykłady obejmują:  
  
-   **Word tezaurusa**: Przejdź opcje programu word.  
  
-   **Folder Eksplorator plików**: Przeglądanie plików i folderów.  
  
-   **Kreatorzy**: Potężne skomplikowane zadanie na wiele stron, które można nawigować między. Kreator składników Windows, który obsługuje dodawanie i usuwanie funkcji Windows to na przykład.  
  
 Włączanie nawigacji w stylu przeglądarki do aplikacji autonomicznej, można użyć <xref:System.Windows.Navigation.NavigationWindow> klasy. <xref:System.Windows.Navigation.NavigationWindow> pochodzi od klasy <xref:System.Windows.Window> i rozszerza je przy użyciu tego samego obsługę nawigacji, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] zapewniają. Możesz użyć <xref:System.Windows.Navigation.NavigationWindow> jako głównego okna aplikacji autonomicznej lub okien podrzędnych, takich jak okno dialogowe.  
  
 Aby zaimplementować <xref:System.Windows.Navigation.NavigationWindow>, podobnie jak w przypadku większości klas najwyższego poziomu w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] (<xref:System.Windows.Window>, <xref:System.Windows.Controls.Page>i tak dalej), możesz użyć kombinacji znaczników i związane z kodem. Jest to pokazane w poniższym przykładzie.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml#navigationwindowmarkup)]  
  
 [!code-csharp[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml.cs#navigationwindowcodebehind)]
 [!code-vb[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/MainWindow.xaml.vb#navigationwindowcodebehind)]  
  
 Ten kod tworzy <xref:System.Windows.Navigation.NavigationWindow> , automatycznie przechodzi do <xref:System.Windows.Controls.Page> (HomePage.xaml) podczas <xref:System.Windows.Navigation.NavigationWindow> jest otwarty. Jeśli <xref:System.Windows.Navigation.NavigationWindow> okna głównego aplikacji, możesz użyć `StartupUri` atrybutu, aby go uruchomić. Jest to pokazane w niej następujące znaczniki.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchNavWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/App.xaml#applaunchnavwindow)]  
  
 Poniższy rysunek przedstawia <xref:System.Windows.Navigation.NavigationWindow> jako głównego okna aplikacji autonomicznej.  
  
 ![Okno główne](./media/navigation-overview/navigation-window-as-main-window.png "oknie nawigacji okna głównego")  
  
 Z rysunku, możesz zobaczyć, że <xref:System.Windows.Navigation.NavigationWindow> ma tytuł, nawet jeśli nie została ustawiona <xref:System.Windows.Navigation.NavigationWindow> kod implementacji z poprzedniego przykładu. Zamiast tego tytuł można ustawić przy użyciu <xref:System.Windows.Controls.Page.WindowTitle%2A> właściwość, która jest wyświetlana w poniższym kodzie.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup1)]  
[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup2)]  
  
 Ustawienie <xref:System.Windows.Controls.Page.WindowWidth%2A> i <xref:System.Windows.Controls.Page.WindowHeight%2A> właściwości wpływa również na <xref:System.Windows.Navigation.NavigationWindow>.  
  
 Zazwyczaj należy zaimplementować własny <xref:System.Windows.Navigation.NavigationWindow> kiedy trzeba będzie dostosować jego zachowanie lub jego wyglądu. Jeśli tego nie zrobisz, możesz użyć skrótu. Jeśli określisz pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] z <xref:System.Windows.Controls.Page> jako <xref:System.Windows.Application.StartupUri%2A> w aplikacji autonomicznej, <xref:System.Windows.Application> automatycznie tworzy <xref:System.Windows.Navigation.NavigationWindow> hosta <xref:System.Windows.Controls.Page>. Następujący kod pokazuje, jak włączyć tę opcję.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchPage](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/AnotherApp.xaml#applaunchpage)]  
  
 Jeśli chcesz, aby okno drugą aplikację, takich jak okno dialogowe, można <xref:System.Windows.Navigation.NavigationWindow>, w poniższym przykładzie można użyć kodu, aby go otworzyć.  
  
 [!code-csharp[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/DialogOwnerWindow.xaml.cs#createnwdialogbox)]
 [!code-vb[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/DialogOwnerWindow.xaml.vb#createnwdialogbox)]  
  
 Na poniższej ilustracji przedstawiono wyniki.  
  
 ![Okno dialogowe](./media/navigation-overview/navigation-window-as-dialog-box.png "oknie nawigacyjnym jako okno dialogowe")  
  
 Jak widać, <xref:System.Windows.Navigation.NavigationWindow> Wyświetla [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]— styl **ponownie** i **do przodu** przyciski, która pozwala użytkownikom na przechodzenie do dziennika. Przyciski te zapewniają tego samego środowiska użytkownika, jak pokazano na poniższej ilustracji.  
  
 ![Przyciski w oknie nawigacji Wstecz i dalej](./media/navigation-overview/back-and-forward-buttons-in-navigation-window.png "przyciski w oknie nawigacji Wstecz i dalej")  
  
 Jeśli strony udostępnia własne Obsługa nawigacji dziennika i interfejsu użytkownika, można ukryć **ponownie** i **do przodu** przyciski wyświetlane na <xref:System.Windows.Navigation.NavigationWindow> , ustawiając wartość <xref:System.Windows.Navigation.NavigationWindow.ShowsNavigationUI%2A> właściwości `false`.  
  
 Alternatywnie, można użyć obsługi dostosowywania w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zastąpić [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z <xref:System.Windows.Navigation.NavigationWindow> sam.  
  
<a name="Frame_in_Standalone_Applications"></a>   
## <a name="the-frame-class"></a>Frame — klasa  
 Zarówno przeglądarki i <xref:System.Windows.Navigation.NavigationWindow> są tę zawartość można nawigować hostów systemu windows. W niektórych przypadkach aplikacje mają zawartość, która nie musi być obsługiwany przez całe okno. Zamiast tego takiej zawartości znajdować się wewnątrz innej zawartości. Można wstawić zawartości można nawigować do innej zawartości przy użyciu <xref:System.Windows.Controls.Frame> klasy. <xref:System.Windows.Controls.Frame> zapewnia obsługę tych samych jako <xref:System.Windows.Navigation.NavigationWindow> i [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
 Poniższy przykład pokazuje, jak dodać <xref:System.Windows.Controls.Frame> do <xref:System.Windows.Controls.Page> deklaratywne, przy użyciu `Frame` elementu.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml3)]  
  
 Ustawia ten kod znaczników `Source` atrybutu `Frame` elementu z pakietem [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla <xref:System.Windows.Controls.Page> , <xref:System.Windows.Controls.Frame> początkowo należy przejść do. Poniższy rysunek przedstawia [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] z <xref:System.Windows.Controls.Page> zawierający <xref:System.Windows.Controls.Frame> , nawigację między kilka stron.  
  
 ![Ramkę, która ma nawigację między wieloma stronami](./media/navigation-overview/frame-navigation-between-multiple-pages.png "pokazuje nawigacji w ramce między wieloma stronami.")  
  
 Tylko nie trzeba stosować <xref:System.Windows.Controls.Frame> wewnątrz treści <xref:System.Windows.Controls.Page>. Jest również typowe do hostowania <xref:System.Windows.Controls.Frame> wewnątrz treści <xref:System.Windows.Window>.  
  
 Domyślnie <xref:System.Windows.Controls.Frame> używa tylko własnego dziennika w przypadku braku innego arkusza. Jeśli <xref:System.Windows.Controls.Frame> stanowi część zawartości, która znajduje się wewnątrz albo <xref:System.Windows.Navigation.NavigationWindow> lub [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], <xref:System.Windows.Controls.Frame> korzysta z dziennika, który należy do <xref:System.Windows.Navigation.NavigationWindow> lub [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Czasami jednak <xref:System.Windows.Controls.Frame> może być konieczne odpowiedzialne za własną dziennika. Jednym z powodów w tym celu jest umożliwienie dziennika nawigacji w obrębie strony które są hostowane przez <xref:System.Windows.Controls.Frame>. Jest to zilustrowane w poniższym rysunku.  
  
 ![Diagram ramek i stron](./media/navigation-overview/journal-navigation-within-pages-hosted-by-a-frame.png "pokazuje dziennika Nawigacja w stronach hostowanych przez ramkę.")  
  
 W takim przypadku można skonfigurować <xref:System.Windows.Controls.Frame> używać własnego dziennika przez ustawienie <xref:System.Windows.Controls.Frame.JournalOwnership%2A> właściwość <xref:System.Windows.Controls.Frame> do <xref:System.Windows.Navigation.JournalOwnership.OwnsJournal>. Jest to pokazane w niej następujące znaczniki.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml3)]  
  
 Na poniższym rysunku przedstawiono efekt poruszanie się w obrębie <xref:System.Windows.Controls.Frame> , który używa własnego dziennika.  
  
 ![Ramkę, która korzysta z własnego dziennika](./media/navigation-overview/frame-uses-its-own-journal.png "to pokazuje wpływ poruszanie się w obrębie ramki, który używa własnego dziennika.")  
  
 Należy zauważyć, że wpisy dziennika są wyświetlane przez nawigacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w <xref:System.Windows.Controls.Frame>, a nie przez [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)].  
  
> [!NOTE]
>  Jeśli <xref:System.Windows.Controls.Frame> stanowi część zawartości, która znajduje się w <xref:System.Windows.Window>, <xref:System.Windows.Controls.Frame> używany osobny dziennik i w związku z tym, wyświetla własną nawigacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Jeśli Twoje środowisko użytkownika wymaga <xref:System.Windows.Controls.Frame> zapewnienie własnego dziennika bez pokazywania nawigacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], można ukryć nawigacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , ustawiając <xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A> do <xref:System.Windows.Visibility.Hidden>. Jest to pokazane w niej następujące znaczniki.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml3)]  
  
<a name="Navigation_Hosts"></a>   
## <a name="navigation-hosts"></a>Hosty nawigacji  
 <xref:System.Windows.Controls.Frame> i <xref:System.Windows.Navigation.NavigationWindow> są klasami, które są znane jako hosty nawigacji. A *hosta nawigacji* to klasa, która może przejść do wyświetlania zawartości. Aby to osiągnąć, każdy host nawigacji używa własną <xref:System.Windows.Navigation.NavigationService> i dziennika. Budowa podstawowych hosta nawigacji jest wyświetlany na poniższej ilustracji.  
  
 ![Diagramy nawigatora](./media/navigation-overview/navigation-host-construction.png "podstawowe konstrukcji hosta nawigacji")  
  
 Zasadniczo to ustawienie zezwala <xref:System.Windows.Navigation.NavigationWindow> i <xref:System.Windows.Controls.Frame> zapewnienie takie same nawigacji jest to obsługiwane [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] miejsce w przypadku hostowania w przeglądarce.  
  
 Poza używaniem <xref:System.Windows.Navigation.NavigationService> i dziennika, hosty nawigacji zaimplementować te same elementy członkowskie, <xref:System.Windows.Navigation.NavigationService> implementuje. Jest to zilustrowane w poniższym rysunku.  
  
 ![Dziennika w ramce, a w oknie nawigacji](./media/navigation-overview/navigation-window-and-frame.png "oknie nawigacji i ramki")  
  
 Dzięki temu program nawigacji pomocy technicznej bezpośrednio przed nimi. Może to rozważyć, jeśli konieczne będzie podanie własnej nawigacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dla <xref:System.Windows.Controls.Frame> hostowaną w <xref:System.Windows.Window>. Ponadto, oba typy implementacji członków dodatkowych, związanych z nawigacją, w tym `BackStack` (<xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType>) i `ForwardStack` (<xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType>), co pozwala użytkownikowi na wyliczenie zapisów w tle stos i do przodu stosu, odpowiednio.  
  
 Jak wspomniano wcześniej, więcej niż jeden arkusz może znajdować się w obrębie aplikacji. Następujący rysunek przedstawia przykład, jeśli taka sytuacja może wystąpić.  
  
 ![Wiele dzienników w jednej aplikacji](./media/navigation-overview/multiple-journals-in-one-application.png "jest to przykład więcej niż jeden arkusz w aplikacji.")  
  
<a name="Navigating_to_Content_Other_than_Pages"></a>   
## <a name="navigating-to-content-other-than-xaml-pages"></a>Przechodzenie do zawartości innej niż stron XAML  
 W tym temacie <xref:System.Windows.Controls.Page> i dodatkiem Service pack [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] zostały użyte w celu pokazują różne możliwości nawigacji [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Jednak <xref:System.Windows.Controls.Page> oznacza to skompilowany w aplikacji nie jest jedynym typem zawartości, która może być przejście i dodatkiem Service pack [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] nie są jedynym sposobem identyfikacji zawartości.  
  
 Tak jak pokazano w tej sekcji, możesz także przejść do luźne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plików [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] pliki i obiekty.  
  
<a name="Navigating_to_Loose_XAML_Files"></a>   
### <a name="navigating-to-loose-xaml-files"></a>Przejdź do plików XAML luźne  
 Luźne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plik jest plikiem o następującej charakterystyce:  
  
-   Zawiera tylko [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (Brak kodu).  
  
-   Ma deklarację odpowiedniego obszaru nazw.  
  
-   Ma rozszerzenie nazwy pliku .xaml.  
  
 Na przykład rozważmy następującą zawartością, która jest przechowywana jako luźne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku Person.xaml.  
  
 [!code-xaml[NavigationOverviewSnippets#LooseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Person.xaml#loosexaml)]  
  
 Dwukrotne kliknięcie pliku przeglądarki otwiera i przechodzi do strony i wyświetla zawartość. Jest to pokazane na poniższej ilustracji.  
  
 ![Wyświetlanie zawartości w pliku Person.XAML](./media/navigation-overview/contents-of-person-xaml-file.png "pokazuje zawartość pliku Person.XAML.")  
  
 Możesz wyświetlić luźne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plików z następujących wartości:  
  
-   Witryna sieci Web na komputerze lokalnym, intranetu lub Internetu.  
  
-   A [!INCLUDE[TLA#tla_unc](../../../../includes/tlasharptla-unc-md.md)] udziału plików.  
  
-   Dysk lokalny.  
  
 Luźne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plik można dodać do ulubionych w przeglądarce lub strona główna.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat publikowania i uruchamianie luźne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony, zobacz [wdrażanie aplikacji WPF](deploying-a-wpf-application-wpf.md).  
  
 Jednym z ograniczeń w odniesieniu do luźne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest, że może obsługiwać tylko zawartość, która jest bezpieczne uruchamianie w częściowej relacji zaufania. Na przykład `Window` nie może być elementem głównym luźne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku. Aby uzyskać więcej informacji, zobacz [WPF częściowego zaufania zabezpieczeń](../wpf-partial-trust-security.md).  
  
<a name="Navigating_to_HTML_Files_Using_Frame"></a>   
### <a name="navigating-to-html-files-by-using-frame"></a>Nawigacja do plików HTML za pomocą ramki  
 Zgodnie z oczekiwaniami, możesz także przejść do [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]. Po prostu musisz podać [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] używającą schemat http. Na przykład następująca [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pokazuje <xref:System.Windows.Controls.Frame> , przechodzi do [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] strony.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHtmlNavMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHTMLNavPage.xaml#framehtmlnavmarkup)]  
  
 Przejdź do [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] wymaga specjalnych uprawnień. Na przykład, nie możesz przejść za pomocą [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] działa w izolowanym częściowej relacji zaufania strefie Internet. Aby uzyskać więcej informacji, zobacz [WPF częściowego zaufania zabezpieczeń](../wpf-partial-trust-security.md).  
  
<a name="Navigating_to_HTML_Files_Using_WebBrowser"></a>   
### <a name="navigating-to-html-files-by-using-the-webbrowser-control"></a>Przejdź do plików HTML za pomocą formantu WebBrowser  
 <xref:System.Windows.Controls.WebBrowser> Kontrolować obsługuje [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] hostingu dokumentu, nawigacji i skryptu/zarządzanego kodu współdziałania. Aby uzyskać szczegółowe informacje dotyczące <xref:System.Windows.Controls.WebBrowser> sterowania, zobacz <xref:System.Windows.Controls.WebBrowser>.  
  
 Podobnie jak <xref:System.Windows.Controls.Frame>, po do [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] przy użyciu <xref:System.Windows.Controls.WebBrowser> wymaga specjalnych uprawnień. Na przykład z poziomu aplikacji częściowego zaufania, można przejść wyłącznie [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] znajduje się w miejscu pochodzenia. Aby uzyskać więcej informacji, zobacz [WPF częściowego zaufania zabezpieczeń](../wpf-partial-trust-security.md).  
  
<a name="Navigating_to_Objects"></a>   
### <a name="navigating-to-custom-objects"></a>Przejdź do obiektów niestandardowych  
 Jeśli masz dane, które są przechowywane jako obiektów niestandardowych, jeden sposób wyświetlania tych danych jest utworzenie <xref:System.Windows.Controls.Page> z zawartością, która jest powiązana z tych obiektów (zobacz [Przegląd wiązanie danych](../data/data-binding-overview.md)). Jeśli nie potrzebujesz kłopotów z tworzeniem całej strony, aby wyświetlić obiekty, można przejść bezpośrednio do nich zamiast tego.  
  
 Należy wziąć pod uwagę `Person` klasę, która jest zaimplementowana w poniższym kodzie.  
  
 [!code-csharp[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/Person.cs#personclasscode)]
 [!code-vb[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/Person.vb#personclasscode)]  
  
 Aby przejść do niego, należy wywołać <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A?displayProperty=nameWithType> metody, jak pokazano w następującym kodem.  
  
 [!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject1)]  
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject2)]  
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject3)]  
  
 [!code-csharp[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml.cs#pagethatnavstoobjectcodebehind)]
 [!code-vb[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/HomePage.xaml.vb#pagethatnavstoobjectcodebehind)]  
  
 Na poniższej ilustracji przedstawiono wyniki.  
  
 ![Strona, prowadzącego do klasy](./media/navigation-overview/page-navigates-to-an-object.png "to przykład strony, który prowadzi do obiektu.")  
  
 Na podstawie tej wartości widać, że będą wyświetlane żadne informacje przydatne. W rzeczywistości wartość, która jest wyświetlana jest wartość zwracaną przez `ToString` metodę **osoby** obiektu; domyślnie jest to jedyny wartość, która [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] można używać do reprezentacji obiektu. Można zastąpić `ToString` metodę, aby zwrócić bardziej opisowe informacje, mimo że będzie on nadal składać się wyłącznie wartości typu string. Jedna z technik umożliwia wykorzystującego możliwości prezentacja [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jest użycie szablonu danych. Możesz wdrożyć szablon danych, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] można skojarzyć z obiektu określonego typu. Poniższy kod przedstawia szablon danych `Person` obiektu.  
  
 [!code-xaml[NavigateToObjectSnippets#DataTemplateMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/App.xaml#datatemplatemarkup)]  
  
 W tym miejscu szablonu danych jest skojarzona z `Person` typu przy użyciu `x:Type` — rozszerzenie znaczników w `DataType` atrybutu. Następnie tworzy powiązania szablonu danych `TextBlock` elementów (zobacz <xref:System.Windows.Controls.TextBlock>) do właściwości `Person` klasy. Na poniższej ilustracji przedstawiono zaktualizowany wygląd `Person` obiektu.  
  
 ![Przejdź do klasy, która ma szablon danych](./media/navigation-overview/navigating-to-a-class.png "przechodzenia do klasy, która ma szablon danych.")  
  
 Zaletą tej metody jest spójność zyskujesz dzięki możliwości ponowne użycie szablonu danych, aby wyświetlić obiekty spójnie wszędzie w aplikacji.  
  
 Aby uzyskać więcej informacji na temat szablonów danych, zobacz [Przegląd Szablonowanie danych](../data/data-templating-overview.md).  
  
<a name="Security"></a>   
## <a name="security"></a>Zabezpieczenia  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Obsługa nawigacji umożliwia [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] przejście przez Internet, a zezwala aplikacjom hostować zawartość innych firm. Do ochrony zarówno aplikacji, jak i użytkowników przed szkodliwym zachowanie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zawiera szereg funkcji zabezpieczeń, które zostały omówione w [zabezpieczeń](../security-wpf.md) i [WPF częściowego zaufania zabezpieczeń](../wpf-partial-trust-security.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Application.SetCookie%2A>
- <xref:System.Windows.Application.GetCookie%2A>
- [Zarządzanie aplikacjami — omówienie](application-management-overview.md)
- [Pakowanie URI w WPF](pack-uris-in-wpf.md)
- [Strukturyzowana nawigacja — omówienie](structured-navigation-overview.md)
- [Topologia nawigacji — omówienie](navigation-topologies-overview.md)
- [Tematy z instrukcjami](navigation-how-to-topics.md)
- [Wdrażanie aplikacji WPF](deploying-a-wpf-application-wpf.md)
