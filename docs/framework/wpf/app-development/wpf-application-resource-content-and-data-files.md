---
title: Zasoby aplikacji WPF, zawartość, pliki danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF application [WPF], files
- loose resources [WPF]
- content files [WPF]
- Site of Origin files [WPF]
- resource files [WPF]
- remote files [WPF]
- embedded resources [WPF]
- files [WPF]
- referencing application files [WPF]
- application development [WPF], files
- application management [WPF]
ms.assetid: 7ad2943b-3961-41d3-8fc6-1582d43f5d99
ms.openlocfilehash: 2c48788507eed40e8240491dbd5064ad6c293c9f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651933"
---
# <a name="wpf-application-resource-content-and-data-files"></a>Zasoby aplikacji WPF, zawartość, pliki danych
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] aplikacje często są zależne od plików, które zawierają dane niewykonywalne, takich jak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], obrazy, wideo i audio. Windows Presentation Foundation (WPF) oferuje specjalne obsługę konfigurowania, identyfikowania i stosowania tych typów plików danych, które są wywoływane, pliki danych aplikacji. Ta obsługa dotyczy tego określonego zestawu typów plików danych aplikacji, w tym:  
  
- **Pliki zasobów**: Pliki danych, które są kompilowane w plik wykonywalny lub biblioteka [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zestawu.  
  
- **Pliki zawartości**: Autonomiczne pliki danych, których jawne skojarzenia z plikiem wykonywalnym [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zestawu.  
  
- **Witryna pochodzenia plików**: Autonomiczne pliki danych, które nie są skojarzone z plikiem wykonywalnym [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zestawu.  
  
 Jedną istotną różnicę się między tymi trzema typami plików jest, że pliki zasobów i pliki zawartości są określane w czasie kompilacji; zestaw ma jawne będzie o nich wiedział. Dla witryny pochodzenia plików, zespół może jednak zawierać nie znajomości na wszystkich lub niejawne informacji na temat za pomocą pakietu [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] odwołanie; w przypadku, nie ma żadnej gwarancji lokacji przywoływany plik pierwotny faktycznie istnieje.  
  
 Aby odwołać się do plików danych aplikacji Windows Presentation Foundation (WPF) korzysta z pakietu [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] schemat, który jest szczegółowo opisane w [pakiet URI w WPF](pack-uris-in-wpf.md)).  
  
 W tym temacie opisano sposób konfigurowania i korzystania z plików danych aplikacji.  

<a name="Resource_Files"></a>   
## <a name="resource-files"></a>Pliki zasobów  
 Jeśli plik danych aplikacji musi być zawsze dostępny do aplikacji, jedynym sposobem zagwarantowania dostępności dotyczy wkompilować ją w głównym zestawie pliku wykonywalnego aplikacji lub jednej z jego przywoływanych zestawach. Ten typ pliku danych aplikacji jest znany jako *pliku zasobów*.  
  
 Skorzystaj z zasobów plików, gdy:  
  
- Nie potrzebujesz zaktualizować zawartość pliku zasobów, jest skompilowany w zestawie.  
  
- Celem jest uproszczenie złożoności dystrybucji aplikacji dzięki zmniejszeniu liczby zależnościach plików.  
  
- Musi być możliwy do zlokalizowania pliku danych aplikacji (zobacz [Przegląd lokalizacja i globalizacja WPF](../advanced/wpf-globalization-and-localization-overview.md)).  
  
> [!NOTE]
>  Pliki zasobów, opisane w tej sekcji są inne niż pliki zasobów opisano w [zasoby XAML](../advanced/xaml-resources.md) i różni się od zasobów osadzony lub połączony opisanych w [zasobów zarządzania aplikacji (.NET) ](/visualstudio/ide/managing-application-resources-dotnet).  
  
### <a name="configuring-resource-files"></a>Konfigurowanie plików zasobów  
 W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], plik zasobów jest plikiem, który znajduje się w [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] projektu jako `Resource` elementu.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Resource Include="ResourceFile.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  W [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], Utwórz plik zasobów przez dodanie pliku do projektu i ustawienie jej `Build Action` do `Resource`.  
  
 Podczas kompilowania projektu [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] kompiluje zasobu w zestawie.  
  
### <a name="using-resource-files"></a>Korzystanie z plików zasobów  
 Aby załadować plik zasobów, można wywołać <xref:System.Windows.Application.GetResourceStream%2A> metody <xref:System.Windows.Application> klasy, przekazując pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] określający plik żądanego zasobu. <xref:System.Windows.Application.GetResourceStream%2A> Zwraca <xref:System.Windows.Resources.StreamResourceInfo> obiektu, który uwidacznia plik zasobu jako <xref:System.IO.Stream> oraz opis typu zawartości.  
  
 Na przykład poniższy kod przedstawia sposób użycia <xref:System.Windows.Application.GetResourceStream%2A> załadować <xref:System.Windows.Controls.Page> zasobów plików i ustaw go jako zawartość <xref:System.Windows.Controls.Frame> (`pageFrame`):  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 Podczas wywoływania <xref:System.Windows.Application.GetResourceStream%2A> zapewnia dostęp do <xref:System.IO.Stream>, należy wykonać podczas konwertowania go do typu właściwości, który można będzie się ustawieniem dla niego przy użyciu dodatkowej pracy. Zamiast tego można pozwolić [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] powinien zachować ostrożność, otwierania i konwertowania <xref:System.IO.Stream> , ładując plik zasobów bezpośrednio do właściwości typu przy użyciu kodu.  
  
 Poniższy przykład przedstawia sposób ładowania <xref:System.Windows.Controls.Page> bezpośrednio do <xref:System.Windows.Controls.Frame> (`pageFrame`) przy użyciu kodu.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 Poniższy przykład jest równoważny z poprzednim przykładzie.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a>Pliki kodu aplikacji jako pliki zasobów  
 Zestaw specjalny [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] plików kodu aplikacji można się odwoływać przy użyciu pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], w tym windows, strony, dokumenty przepływu i słowniki zasobów. Na przykład można ustawić <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> właściwości z pakietem [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odwołujący się okna lub strony, który chcesz załadować podczas uruchamiania aplikacji.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 Można zrobić podczas [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plik jest uwzględniony w [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] projektu jako `Page` elementu.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Page Include="MainWindow.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  W [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], możesz dodać nową <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>, lub <xref:System.Windows.ResourceDictionary> do projektu, `Build Action` dla kodu znaczników pliku będą domyślnie `Page`.  
  
 Gdy projekt z `Page` elementów jest kompilowany, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementów jest konwertowana na format binarny i kompilowane do zestawu skojarzone. W związku z tym pliki te może służyć w taki sam sposób, jak pliki typowych zasobów.  
  
> [!NOTE]
>  Jeśli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest skonfigurowany jako `Resource` elementu i nie ma pliku CodeBehind, nieprzetworzoną [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest kompilowany do zestawu, zamiast binarną wersję nieprzetworzonych [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
<a name="Content_Files"></a>   
## <a name="content-files"></a>Pliki zawartości  
 A *zawartości pliku* jest rozpowszechniany jako plik luźne wraz z zestawu pliku wykonywalnego. Mimo że nie są kompilowane do zestawu, zestawy są kompilowane przy użyciu metadanych, który ustanawia skojarzenie z każdego pliku zawartości.  
  
 Należy używać plików zawartości, jeśli aplikacja wymaga określonego zestawu plików danych aplikacji, które można zaktualizować bez konieczności ponownego kompilowania zestawu, który je wykorzystuje.  
  
### <a name="configuring-content-files"></a>Konfigurowanie plików zawartości  
 Aby dodać zawartość pliku do projektu, może być dołączony jako pliku danych aplikacji `Content` elementu. Ponadto, ponieważ plik zawartości nie jest kompilowana bezpośrednio do zestawu, należy ustawić [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `CopyToOutputDirectory` elementu metadanych, aby określić, że plik zawartości jest kopiowany do lokalizacji, która jest określana względem skompilowany zestaw. Jeśli chcesz, aby zasób był kopiowany do folderu wyjściowego kompilacji każdym razem, gdy projekt jest kompilowany, możesz ustawić `CopyToOutputDirectory` elementu metadanych z `Always` wartości. W przeciwnym razie należy zapewnić, że tylko najnowszą wersję zasobu jest kopiowany do folderu danych wyjściowych kompilacji za pomocą `PreserveNewest` wartości.  
  
 Poniżej przedstawiono plik, który jest skonfigurowany jako wyjścia w zawartości pliku, który jest kopiowany do kompilacji folderu tylko wtedy, gdy nowa wersja zasobu jest dodawany do projektu.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Content Include="ContentFile.xaml">  
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
    </Content>  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  W [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], utworzyć plik zawartości przez dodanie pliku do projektu i ustawienie jej `Build Action` do `Content`i ustaw jego `Copy to Output Directory` do `Copy always` (taka sama jak `Always`) i `Copy if newer` (taka sama jak `PreserveNewest`).  
  
 Podczas kompilowania projektu <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atrybutu jest skompilowany w metadanych zestawu dla każdego pliku zawartości.  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 Wartość <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> oznacza ścieżkę do pliku zawartości względem jego pozycja w projekcie. Na przykład, jeżeli plik zawartości znajdują się w podfolderze projektu, dodatkowe informacje o ścieżce czy należy włączyć do <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> wartości.  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> Wartość jest również wartość ścieżki do zawartości pliku w folderze danych wyjściowych kompilacji.  
  
### <a name="using-content-files"></a>Przy użyciu plików zawartości  
 Aby załadować plik zawartości, można wywołać <xref:System.Windows.Application.GetContentStream%2A> metody <xref:System.Windows.Application> klasy, przekazując pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] określający żądany plik zawartości. <xref:System.Windows.Application.GetContentStream%2A> Zwraca <xref:System.Windows.Resources.StreamResourceInfo> obiektu, który udostępnia zawartość pliku jako <xref:System.IO.Stream> oraz opis typu zawartości.  
  
 Na przykład poniższy kod przedstawia sposób użycia <xref:System.Windows.Application.GetContentStream%2A> załadować <xref:System.Windows.Controls.Page> zawartości pliku i ustawić go jako zawartość <xref:System.Windows.Controls.Frame> (`pageFrame`).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 Podczas wywoływania <xref:System.Windows.Application.GetContentStream%2A> zapewnia dostęp do <xref:System.IO.Stream>, należy wykonać podczas konwertowania go do typu właściwości, który można będzie się ustawieniem dla niego przy użyciu dodatkowej pracy. Zamiast tego można pozwolić [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] powinien zachować ostrożność, otwierania i konwertowania <xref:System.IO.Stream> , ładując plik zasobów bezpośrednio do właściwości typu przy użyciu kodu.  
  
 Poniższy przykład przedstawia sposób ładowania <xref:System.Windows.Controls.Page> bezpośrednio do <xref:System.Windows.Controls.Frame> (`pageFrame`) przy użyciu kodu.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 Poniższy przykład jest równoważny z poprzednim przykładzie.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>   
## <a name="site-of-origin-files"></a>Witryna pochodzenia plików  
 Pliki zasobów ma wyraźnej relacji z zestawów, które zostaną rozproszone obok, zgodnie z definicją <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>. Jednak istnieją konieczny może nawiązać albo niejawne lub nieistniejącą relację między zestawu i pliku danych aplikacji, w tym przypadku:  
  
- Plik nie istnieje w czasie kompilacji.  
  
- Nie wiadomo, jakie pliki zestawu będzie wymagało do czasu wykonywania.  
  
- Chcesz być w stanie zaktualizować pliki bez konieczności ponownego kompilowania zestawu, który jest skojarzony.  
  
- Twoja aplikacja używa dużej ilości danych plików, takich jak audio i wideo, i chcesz tylko użytkowników, aby je pobrać, jeśli zdecydują się na.  
  
 Istnieje możliwość ładowania tych typów plików przy użyciu tradycyjnych [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] systemów, takich jak schematy file:/// i http://.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 Jednak schematy file:/// i http:// wymaga pełnego zaufania aplikacji. Jeśli aplikacja jest [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] , została uruchomiona z Internet lub intranet i żąda ona tylko zestaw uprawnień, które są dozwolone w przypadku aplikacje uruchamiane w tych lokalizacjach, pliki nie będzie można ładować tylko z lokacji (punkt początkowy aplikacji Uruchom lokalizacji). Takie pliki są nazywane *witrynę pochodzenia* plików.  
  
 Witryna pochodzenia plików są jedyną opcją dla aplikacji częściowej relacji zaufania, mimo że to nie ogranicza się do aplikacji częściowej relacji zaufania. W pełni zaufane aplikacje nadal może być konieczne załadować pliki danych aplikacji, które nie wiedzą o w czasie kompilacji. Chociaż w pełni zaufane aplikacje mogą używać file:///, jest prawdopodobne, że pliki danych aplikacji zostanie zainstalowany w tym samym folderze lub podfolderze o zestawie aplikacji. W takim przypadku przy użyciu lokacji odwołuje się do źródła jest łatwiejsze niż przy użyciu file:///, ponieważ przy użyciu file:/// wymaga pozwolimy na opracowanie pełnej ścieżki pliku.  
  
> [!NOTE]
>  Witryna pochodzenia, które nie są buforowane pliki za pomocą [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] na komputerze klienckim, gdy pliki zawartości znajdują się. W związku z tym ich są pobierane tylko wtedy, gdy wyraźnie wymagane. Jeśli [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] aplikacja ma duże pliki multimedialne, konfigurując je zgodnie z witryny pochodzenia plików oznacza, że uruchomienie początkowym aplikacji jest znacznie szybszy i pliki są pobierane tylko wtedy na żądanie.  
  
### <a name="configuring-site-of-origin-files"></a>Konfigurowanie witryny pochodzenia plików  
 W przypadku witryny pochodzenia plików nie istnieje lub jest nieznany w czasie kompilacji, należy użyć wdrażania tradycyjnych mechanizmów zapewniających wymagane pliki są dostępne w czasie wykonywania, w tym za pomocą `XCopy` wiersza polecenia programu lub [!INCLUDE[TLA#tla_wininstall](../../../../includes/tlasharptla-wininstall-md.md)].  
  
 Jeśli wiesz, w czasie kompilacji plików, które będą znajdować się w witrynie źródła, takich jak, ale mimo to chcesz uniknąć jawne zależności, można dodać te pliki [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] projektu jako `None` elementu. Jak w przypadku plików zawartości, należy ustawić [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `CopyToOutputDirectory` atrybutu, aby określić, czy witryna pochodzenia pliku jest kopiowany do lokalizacji, która jest określana względem skompilowany zestaw, określając opcję `Always` wartość lub `PreserveNewest` wartość.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <None Include="PageSiteOfOriginFile.xaml">  
    <CopyToOutputDirectory>Always</CopyToOutputDirectory>  
  </None>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  W [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], utworzyć witrynę pochodzenia pliku, dodając plik do projektu i ustawienie jej `Build Action` do `None`.  
  
 Podczas kompilowania projektu [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] kopiuje określone pliki do folderu wyjściowego kompilacji.  
  
### <a name="using-site-of-origin-files"></a>Przy użyciu witryny pochodzenia plików  
 Aby załadować witryny pochodzenia pliku, można wywołać <xref:System.Windows.Application.GetRemoteStream%2A> metody <xref:System.Windows.Application> klasy, przekazując w pakiecie [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] określający żądanej witryny pliku pierwotnego. <xref:System.Windows.Application.GetRemoteStream%2A> Zwraca <xref:System.Windows.Resources.StreamResourceInfo> obiektu, który przedstawia witrynę pochodzenia pliku jako <xref:System.IO.Stream> oraz opis typu zawartości.  
  
 Na przykład poniższy kod przedstawia sposób użycia <xref:System.Windows.Application.GetRemoteStream%2A> załadować <xref:System.Windows.Controls.Page> witrynę pochodzenia pliku i ustawić go jako zawartość <xref:System.Windows.Controls.Frame> (`pageFrame`).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 Podczas wywoływania <xref:System.Windows.Application.GetRemoteStream%2A> zapewnia dostęp do <xref:System.IO.Stream>, należy wykonać podczas konwertowania go do typu właściwości, który można będzie się ustawieniem dla niego przy użyciu dodatkowej pracy. Zamiast tego można pozwolić [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] powinien zachować ostrożność, otwierania i konwertowania <xref:System.IO.Stream> , ładując plik zasobów bezpośrednio do właściwości typu przy użyciu kodu.  
  
 Poniższy przykład przedstawia sposób ładowania <xref:System.Windows.Controls.Page> bezpośrednio do <xref:System.Windows.Controls.Frame> (`pageFrame`) przy użyciu kodu.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 Poniższy przykład jest równoważny z poprzednim przykładzie.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>   
## <a name="rebuilding-after-changing-build-type"></a>Ponowne tworzenie po zmianie typu kompilacji  
 Po zmianie typu kompilacji pliku danych aplikacji, należy ponownie skompilować całej aplikacji, aby upewnić się, że te zmiany zostaną zastosowane. Jeśli tworzysz tylko aplikacji, zmiany nie są stosowane.  
  
## <a name="see-also"></a>Zobacz także

- [Pakowanie URI w WPF](pack-uris-in-wpf.md)
