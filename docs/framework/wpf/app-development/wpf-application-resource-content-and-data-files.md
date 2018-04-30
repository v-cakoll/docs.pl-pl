---
title: Zasoby aplikacji WPF, zawartość, pliki danych
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 25
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bcf0a725b7b3467a50a9f51850709dd972da217d
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="wpf-application-resource-content-and-data-files"></a>Zasoby aplikacji WPF, zawartość, pliki danych
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] aplikacje często są zależne od plików, które zawierają dane inne niż wykonywalne, takich jak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], obrazy, wideo i audio. Windows Presentation Foundation (WPF) oferuje obsługę specjalne Konfigurowanie, identyfikowanie i używanie tych typów plików danych, które są nazywane pliki danych aplikacji. Ta obsługa dotyczy tego określonego zestawu danych typów plików aplikacji, w tym:  
  
-   **Pliki zasobów**: pliki danych, które są łączone w plik wykonywalny lub biblioteka [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zestawu.  
  
-   **Pliki zawartości**: autonomiczny pliki danych, których jawne skojarzenia z plikiem wykonywalnym [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zestawu.  
  
-   **Witryny pochodzenia plików**: autonomiczny pliki danych, które nie mają związku z pliku wykonywalnego [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zestawu.  
  
 Jedną istotną różnicę między te trzy typy plików, aby jest plików zasobów i pliki zawartości są znane w czasie kompilacji. zestaw ma jawne o nich wiedział. Dla witryny pochodzenia plików, jednak zestaw może nie mieć nie będzie o nich wiedział w, lub niejawne informacji na temat za pomocą pakietu [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] odwołanie; w przypadku, nie ma żadnej gwarancji, do którego istnieje odwołanie witryny pochodzenia pliku faktycznie istnieje.  
  
 Aby odwołać pliki danych aplikacji, Windows Presentation Foundation (WPF) korzysta z pakietu [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] schemat, który opisano szczegółowo w [identyfikatorów URI pakietu na platformie WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)).  
  
 W tym temacie opisano sposób konfigurowania i używanie plików danych aplikacji.  
  
  
<a name="Resource_Files"></a>   
## <a name="resource-files"></a>Pliki zasobów  
 Jeśli plik danych aplikacji musi być zawsze dostępny dla aplikacji, jedynym sposobem zagwarantowania dostępności jest go skompilować aplikacji główny zestaw pliku wykonywalnego lub jeden z jego zestawów występujących w odwołaniach. Ten typ pliku danych aplikacji jest nazywany *pliku zasobu*.  
  
 Należy używać zasobów plików, gdy:  
  
-   Nie trzeba zaktualizować zawartość pliku zasobu jest skompilowany w zestawie.  
  
-   Celem jest uproszczenie złożoności dystrybucji aplikacji dzięki zmniejszeniu liczby zależnościach plików.  
  
-   Plik danych aplikacji musi być Lokalizowalny (zobacz [omówienie lokalizacja i globalizacja WPF](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)).  
  
> [!NOTE]
>  Pliki zasobów, opisane w tej sekcji są inne niż pliki zasobów opisanego w [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md) i inne niż opisane w zasoby osadzone lub połączone [zarządzanie zasobami aplikacji (.NET) ](http://msdn.microsoft.com/library/f2582734-8ada-4baa-8a7c-e2ef943ddf7e).  
  
### <a name="configuring-resource-files"></a>Konfigurowanie pliki zasobów  
 W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], plik zasobów jest plikiem, który znajduje się w [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] projektu jako `Resource` elementu.  
  
```xml  
<Project "xmlns=http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Resource Include="ResourceFile.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  W [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], Utwórz plik zasobów przez dodanie pliku do projektu i ustawienie jej `Build Action` do `Resource`.  
  
 Po utworzeniu projektu [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] kompiluje zasobu w zestawie.  
  
### <a name="using-resource-files"></a>Przy użyciu plików zasobów  
 Aby załadować plik zasobów, należy wywołać <xref:System.Windows.Application.GetResourceStream%2A> metody <xref:System.Windows.Application> klasy, przekazując pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] identyfikującym rozszerzenie pliku żądanego zasobu. <xref:System.Windows.Application.GetResourceStream%2A> Zwraca <xref:System.Windows.Resources.StreamResourceInfo> obiektu, który przedstawia plik zasobu jako <xref:System.IO.Stream> oraz opis jego typ zawartości.  
  
 Na przykład poniższy kod przedstawia sposób użycia <xref:System.Windows.Application.GetResourceStream%2A> załadować <xref:System.Windows.Controls.Page> zasobów plików i ustaw go jako zawartość <xref:System.Windows.Controls.Frame> (`pageFrame`):  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 Podczas wywoływania <xref:System.Windows.Application.GetResourceStream%2A> zapewnia dostęp do <xref:System.IO.Stream>, należy wykonać konwertowana na typ właściwości na będzie mieć ustawienie go przy użyciu dodatkowej pracy. Zamiast tego można pozwolić [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zajmie się otwieranie i konwertowanie <xref:System.IO.Stream> przez załadowanie pliku zasobu bezpośrednio do właściwości typu przy użyciu kodu.  
  
 Poniższy przykład przedstawia sposób załadować <xref:System.Windows.Controls.Page> bezpośrednio do <xref:System.Windows.Controls.Frame> (`pageFrame`) przy użyciu kodu.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 Poniższy przykład jest kod znaczników równoważne poprzedniego przykładu.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a>Pliki kodu aplikacji jako pliki zasobów  
 Zestaw specjalnego [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] plików kodu aplikacji można odwoływać się przy użyciu pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], w tym systemu windows, stron przepływu dokumentów i słownikach zasobów. Na przykład można ustawić <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> właściwości z pakietem [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odwołujący się okna lub strony, który chcesz załadować podczas uruchamiania aplikacji.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 Można wykonać podczas [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plik znajduje się w [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] projektu jako `Page` elementu.  
  
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
>  W [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], możesz dodać nową <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>, lub <xref:System.Windows.ResourceDictionary> z projektem, `Build Action` dla znacznika pliku domyślnie zostanie ustawiona `Page`.  
  
 Jeśli projekt o `Page` elementów jest kompilowana, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementów jest konwertowana na format binarny i skompilowany w zestawie skojarzone. W rezultacie tych plików może służyć w taki sam sposób jak pliki typowych zasobów.  
  
> [!NOTE]
>  Jeśli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest skonfigurowany jako `Resource` element i nie ma pliku CodeBehind, nieprzetworzonego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest kompilowany do zestawu, a nie binarną wersję nieprzetworzonego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
<a name="Content_Files"></a>   
## <a name="content-files"></a>Pliki zawartości  
 A *zawartości pliku* jest rozpowszechniany jako plik utracić obok pliku wykonywalnego zestawu. Mimo że nie są one kompilowane do zestawu, zestawy są kompilowane przy użyciu metadanych, które określa skojarzenie z każdego pliku zawartości.  
  
 Pliki zawartości należy używać, gdy aplikacja wymaga określonych pliki danych aplikacji, które mają być może zaktualizować bez konieczności ponownego kompilowania zestawu, który wykorzystuje je.  
  
### <a name="configuring-content-files"></a>Konfigurowanie plików zawartości  
 Aby dodać zawartość pliku do projektu, pliku danych aplikacji musi być uwzględniona jako `Content` elementu. Ponadto, ponieważ plik zawartości nie jest kompilowany bezpośrednio do zestawu, należy ustawić [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `CopyToOutputDirectory` elementu metadanych, aby określić, że plik zawartości jest kopiowany do lokalizacji, która jest względem skompilowany zestaw. Jeśli chcesz zasobu, który ma zostać skopiowany do folderu wyjściowego kompilacji zawsze skompilowano projekt, należy ustawić `CopyToOutputDirectory` elementu metadanych z `Always` wartości. W przeciwnym razie można zapewnić, że tylko najnowszą wersję zasobu został skopiowany do folderu wyjściowego kompilacji za pomocą `PreserveNewest` wartości.  
  
 Poniższy kod przedstawia plik, który jest skonfigurowany jako zawartości pliku, który jest kopiowany do kompilacji danych wyjściowych, że folder tylko wtedy, gdy nowa wersja zasobu została dodana do projektu.  
  
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
>  W [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], Utwórz plik zawartości przez dodanie pliku do projektu i ustawienie jej `Build Action` do `Content`i ustaw jej `Copy to Output Directory` do `Copy always` (taki sam jak `Always`) i `Copy if newer` (taki sam jak `PreserveNewest`).  
  
 Po utworzeniu projektu <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atrybutu jest skompilowany w metadanych zestawu dla każdego pliku zawartości.  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 Wartość <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> oznacza ścieżkę do pliku zawartości względem położenia w projekcie. Na przykład, jeśli plik zawartości został znajduje się w podfolderze projektu, dodatkowe informacje o ścieżce może zostać włączone do <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> wartości.  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> Wartość jest również wartość ścieżki do zawartości pliku w folderze wyjściowym kompilacji.  
  
### <a name="using-content-files"></a>Przy użyciu plików zawartości  
 Aby załadować plik zawartości, należy wywołać <xref:System.Windows.Application.GetContentStream%2A> metody <xref:System.Windows.Application> klasy, przekazując pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] żądanego pliku zawartości, które identyfikują. <xref:System.Windows.Application.GetContentStream%2A> Zwraca <xref:System.Windows.Resources.StreamResourceInfo> obiektu, który udostępnia zawartość pliku jako <xref:System.IO.Stream> oraz opis jego typ zawartości.  
  
 Na przykład poniższy kod przedstawia sposób użycia <xref:System.Windows.Application.GetContentStream%2A> załadować <xref:System.Windows.Controls.Page> zawartości pliku i ustaw go jako zawartość <xref:System.Windows.Controls.Frame> (`pageFrame`).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 Podczas wywoływania <xref:System.Windows.Application.GetContentStream%2A> zapewnia dostęp do <xref:System.IO.Stream>, należy wykonać konwertowana na typ właściwości na będzie mieć ustawienie go przy użyciu dodatkowej pracy. Zamiast tego można pozwolić [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zajmie się otwieranie i konwertowanie <xref:System.IO.Stream> przez załadowanie pliku zasobu bezpośrednio do właściwości typu przy użyciu kodu.  
  
 Poniższy przykład przedstawia sposób załadować <xref:System.Windows.Controls.Page> bezpośrednio do <xref:System.Windows.Controls.Frame> (`pageFrame`) przy użyciu kodu.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 Poniższy przykład jest kod znaczników równoważne poprzedniego przykładu.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>   
## <a name="site-of-origin-files"></a>Witryny pochodzenia plików  
 Pliki zasobów mieć jawnej relacji z zestawów, które zostaną rozproszone obok, zgodnie z definicją w <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>. Jednak istnieją razy, gdy można nawiązać albo niejawne lub nieistniejącą relację w zestawu pliku danych aplikacji, łącznie z:  
  
-   Plik nie istnieje, gdy w czasie kompilacji.  
  
-   Nie wiadomo, które pliki z zestawu będzie wymagało do czasu wykonywania.  
  
-   Chcesz była możliwa aktualizacja plików bez konieczności ponownego kompilowania zestawu, który skojarzonych z nimi.  
  
-   Aplikacja używa plików dużej ilości danych, takich jak audio i wideo, i chcesz tylko użytkownicy, aby je pobrać, jeśli.  
  
 Istnieje możliwość załadowania tych typów plików przy użyciu tradycyjnych [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] systemów, takich jak schematy file:/// i http://.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 Schematy file:/// i http:// wymaga jednak aplikacji jest w pełni zaufany. Jeśli aplikacja jest [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] który został uruchomiony w Internecie lub intranecie, a żądania tylko zestaw uprawnień, które są dozwolone dla aplikacje uruchamiane w tych lokalizacjach, pliki utracić można ładować tylko z lokacji (punkt początkowy aplikacji Uruchom lokalizacji). Takie pliki są nazywane *witryny pochodzenia* plików.  
  
 Witryny pochodzenia pliki są tylko opcję aplikacje częściowo zaufane, chociaż są nie tylko aplikacje częściowo zaufane. W pełni zaufane aplikacje mogą nadal musi załadować pliki danych aplikacji, które nie wiedzą o w czasie kompilacji. Podczas w pełni zaufane aplikacje mogą używać file:///, prawdopodobne jest, że pliki danych aplikacji zostanie zainstalowany w tym samym folderze, lub podfolder o zestawie aplikacji. W takim przypadku przy użyciu lokacji odwołujące się do źródła jest łatwiejsze niż przy użyciu file:///, ponieważ przy użyciu file:/// wymaga się pełną ścieżkę pliku.  
  
> [!NOTE]
>  Witryny pochodzenia nie są buforowane pliki z [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] na komputerze klienckim, gdy pliki zawartości znajdują się. W rezultacie tylko są one pobierane na żądanie, w szczególności. Jeśli [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] aplikacja ma duże pliki multimedialne, konfigurując je jako witryny pochodzenia plików oznacza uruchamiania aplikacji początkowej jest znacznie szybsze i pliki tylko zostaną pobrane na żądanie.  
  
### <a name="configuring-site-of-origin-files"></a>Konfigurowanie witryny pochodzenia plików  
 W przypadku witryny pochodzenia plików nie istnieje lub jest nieznany w czasie kompilacji, należy użyć tradycyjnego wdrażania mechanizmów zapewniających wymagane pliki są dostępne w czasie wykonywania, w tym za pomocą `XCopy` wiersza polecenia programu lub [!INCLUDE[TLA#tla_wininstall](../../../../includes/tlasharptla-wininstall-md.md)].  
  
 Jeśli znasz w czasie kompilacji plików, które będą znajdować się w witrynie pochodzenia, takich jak, ale mimo to chcesz uniknąć jawne zależności, możesz dodać tych plików na [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] projektu jako `None` elementu. Zgodnie z plików zawartości, należy ustawić [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `CopyToOutputDirectory` atrybutu, aby określić, że witryny pochodzenia pliku jest kopiowany do lokalizacji, która jest względem skompilowany zestaw, określając albo `Always` wartość lub `PreserveNewest` wartość.  
  
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
>  W [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], tworzenia witryny pochodzenia pliku przez dodanie pliku do projektu i ustawienie jej `Build Action` do `None`.  
  
 Po utworzeniu projektu [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] kopiuje określone pliki do folderu wyjściowego kompilacji.  
  
### <a name="using-site-of-origin-files"></a>Za pomocą witryny pochodzenia plików  
 Aby załadować witryny pochodzenia pliku, należy wywołać <xref:System.Windows.Application.GetRemoteStream%2A> metody <xref:System.Windows.Application> klasy, przekazując pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] identyfikującym żądanej witryny pochodzenia pliku. <xref:System.Windows.Application.GetRemoteStream%2A> Zwraca <xref:System.Windows.Resources.StreamResourceInfo> obiektu, który udostępnia witryny pochodzenia pliku jako <xref:System.IO.Stream> oraz opis jego typ zawartości.  
  
 Na przykład poniższy kod przedstawia sposób użycia <xref:System.Windows.Application.GetRemoteStream%2A> załadować <xref:System.Windows.Controls.Page> witryny pochodzenia pliku i ustaw go jako zawartość <xref:System.Windows.Controls.Frame> (`pageFrame`).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 Podczas wywoływania <xref:System.Windows.Application.GetRemoteStream%2A> zapewnia dostęp do <xref:System.IO.Stream>, należy wykonać konwertowana na typ właściwości na będzie mieć ustawienie go przy użyciu dodatkowej pracy. Zamiast tego można pozwolić [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zajmie się otwieranie i konwertowanie <xref:System.IO.Stream> przez załadowanie pliku zasobu bezpośrednio do właściwości typu przy użyciu kodu.  
  
 Poniższy przykład przedstawia sposób załadować <xref:System.Windows.Controls.Page> bezpośrednio do <xref:System.Windows.Controls.Frame> (`pageFrame`) przy użyciu kodu.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 Poniższy przykład jest kod znaczników równoważne poprzedniego przykładu.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>   
## <a name="rebuilding-after-changing-build-type"></a>Ponowne kompilowanie po zmianie typu kompilacji  
 Po zmianie typu kompilacji pliku danych aplikacji, należy przebudować całej aplikacji, aby upewnić się, że te zmiany zostaną zastosowane. Jeśli tylko skompilowania aplikacji, zmiany nie zostaną zastosowane.  
  
## <a name="see-also"></a>Zobacz też  
 [Pakowanie URI w WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)
