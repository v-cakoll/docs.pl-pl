---
title: Zasoby aplikacji, zawartość i pliki danych
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
ms.openlocfilehash: f17898972eeef66447060db32bae5fae377b710e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186201"
---
# <a name="wpf-application-resource-content-and-data-files"></a>Zasoby aplikacji WPF, zawartość, pliki danych
Aplikacje systemu Microsoft Windows często zależą od plików [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]zawierających dane niewykonalne, takie jak obrazy, wideo i audio. Windows Presentation Foundation (WPF) oferuje specjalną obsługę konfigurowania, identyfikowania i używania tego typu plików danych, które są nazywane plikami danych aplikacji. Ta obsługa koncentruje się wokół określonego zestawu typów plików danych aplikacji, w tym:  
  
- **Pliki zasobów:** Pliki danych, które są kompilowane do zestawu WPF wykonywalnego lub biblioteki.  
  
- **Pliki zawartości**: Autonomiczne pliki danych, które mają jawne skojarzenie z wykonywalnym zestawem WPF.  
  
- **Site of Origin Files**: Autonomiczne pliki danych, które nie mają skojarzenia z wykonywalnym zestawem WPF.  
  
 Jednym z ważnych rozróżnienia między tymi trzema typami plików jest to, że pliki zasobów i pliki zawartości są znane w czasie kompilacji; zgromadzenie ma wyraźną wiedzę na ich temat. W przypadku plików lokacji pochodzenia zestaw może jednak nie mieć żadnej wiedzy o nich lub niejawnej wiedzy za pośrednictwem odwołania do identyfikatora URI (URI) jednolitego pakietu; w przypadku tego ostatniego nie ma gwarancji, że plik miejsca pochodzenia, do którego istnieje, o których mowa w rzeczywistości.  
  
 Aby odwołać się do plików danych aplikacji, Program Windows Presentation Foundation (WPF) używa schematu URI (Pack uniform resource identifier), który jest szczegółowo opisany w [pakietach URI w WPF](pack-uris-in-wpf.md)).  
  
 W tym temacie opisano sposób konfigurowania i używania plików danych aplikacji.  

<a name="Resource_Files"></a>
## <a name="resource-files"></a>Pliki zasobów  
 Jeśli plik danych aplikacji musi być zawsze dostępny dla aplikacji, jedynym sposobem zagwarantowania dostępności jest skompilowanie go do głównego zestawu wykonywalnego aplikacji lub jednego z jej zestawów, do których istnieje odwołanie. Ten typ pliku danych aplikacji jest znany jako *plik zasobów*.  
  
 Pliki zasobów należy używać, gdy:  
  
- Nie trzeba aktualizować zawartości pliku zasobów po jego skompilowaniu do zestawu.  
  
- Chcesz uprościć złożoność dystrybucji aplikacji, zmniejszając liczbę zależności plików.  
  
- Plik danych aplikacji musi być zlokalizowany (zobacz [Omówienie globalizacji i lokalizacji WPF).](../advanced/wpf-globalization-and-localization-overview.md)  
  
> [!NOTE]
> Pliki zasobów opisane w tej sekcji różnią się od plików zasobów opisanych w [zasobach XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md) i różnią się od osadzonych lub połączonych zasobów opisanych w [sekcji Zarządzanie zasobami aplikacji (.NET).](/visualstudio/ide/managing-application-resources-dotnet)  
  
### <a name="configuring-resource-files"></a>Konfigurowanie plików zasobów  
 W WPF WPF plik zasobów jest plikiem, który jest zawarty w projekcie `Resource` aparatu kompilacji firmy Microsoft (MSBuild) jako element.  
  
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
> W programie Visual Studio plik zasobu można utworzyć, dodając `Build Action` `Resource`plik do projektu i ustawiając go na .  
  
 Po zbudowaniu projektu MSBuild kompiluje zasób do zestawu.  
  
### <a name="using-resource-files"></a>Korzystanie z plików zasobów  
 Aby załadować plik zasobu, <xref:System.Windows.Application.GetResourceStream%2A> można <xref:System.Windows.Application> wywołać metodę klasy, przekazując identyfikator URI pakietu, który identyfikuje żądany plik zasobu. <xref:System.Windows.Application.GetResourceStream%2A>zwraca <xref:System.Windows.Resources.StreamResourceInfo> obiekt, który udostępnia plik zasobu jako <xref:System.IO.Stream> i opisuje jego typ zawartości.  
  
 Na przykład poniższy kod pokazuje, <xref:System.Windows.Application.GetResourceStream%2A> jak <xref:System.Windows.Controls.Page> użyć do załadowania pliku zasobu i ustawić go jako zawartość <xref:System.Windows.Controls.Frame> (`pageFrame`):  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 Podczas <xref:System.Windows.Application.GetResourceStream%2A> wywoływania daje <xref:System.IO.Stream>dostęp do , trzeba wykonać dodatkową pracę konwersji go do typu właściwości, które będą jej ustawienie. Zamiast tego można pozwolić WPF zadbać o <xref:System.IO.Stream> otwieranie i konwertowanie przez ładowanie pliku zasobów bezpośrednio do właściwości typu przy użyciu kodu.  
  
 W poniższym <xref:System.Windows.Controls.Page> przykładzie pokazano, jak <xref:System.Windows.Controls.Frame> `pageFrame`załadować bezpośrednio do ( ) przy użyciu kodu.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 Poniższy przykład jest odpowiednik znaczników z poprzedniego przykładu.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a>Pliki kodu aplikacji jako pliki zasobów  
 Specjalny zestaw plików kodu aplikacji WPF można odwoływać się za pomocą URI pakietu, w tym okna, strony, dokumenty przepływu i słowniki zasobów. Na przykład można ustawić <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> właściwość z identyfikatorem URI pakietu, który odwołuje się do okna lub strony, które chcesz załadować po uruchomieniu aplikacji.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 Można to zrobić, gdy plik XAML jest zawarty w projekcie `Page` MSBuild jako element.  
  
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
> W programie Visual Studio <xref:System.Windows.Window>dodasz <xref:System.Windows.Controls.Page> <xref:System.Windows.Documents.FlowDocument>nowe <xref:System.Windows.ResourceDictionary> , <xref:System.Windows.Navigation.NavigationWindow>, , `Build Action` lub do projektu, `Page`dla pliku znaczników domyślnie .  
  
 Podczas kompilacji `Page` projektu z elementami [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementy są konwertowane na format binarny i kompilowane do skojarzonego zestawu. W związku z tym pliki te mogą być używane w taki sam sposób jak typowe pliki zasobów.  
  
> [!NOTE]
> Jeśli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plik jest skonfigurowany `Resource` jako element i nie ma pliku zawierającego kod, plik raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest kompilowany [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]do zestawu, a nie w wersji binarnej pliku raw .  
  
<a name="Content_Files"></a>
## <a name="content-files"></a>Pliki zawartości  
 *Plik zawartości* jest rozprowadzany jako luźny plik obok zestawu wykonywalnego. Chociaż nie są one kompilowane do zestawu, zestawy są kompilowane z metadanymi, które ustanawia skojarzenia z każdego pliku zawartości.  
  
 Pliki zawartości należy używać, gdy aplikacja wymaga określonego zestawu plików danych aplikacji, które mają być w stanie zaktualizować bez ponownego komppilowania zestawu, który zużywa je.  
  
### <a name="configuring-content-files"></a>Konfigurowanie plików zawartości  
 Aby dodać plik zawartości do projektu, plik danych aplikacji `Content` musi być dołączony jako element. Ponadto ponieważ plik zawartości nie jest kompilowany bezpośrednio do zestawu, należy ustawić `CopyToOutputDirectory` element metadanych MSBuild, aby określić, że plik zawartości jest kopiowany do lokalizacji, która jest względem zestawu wbudowanego. Jeśli chcesz, aby zasób był kopiowany do folderu wyjściowego `CopyToOutputDirectory` kompilacji za `Always` każdym razem, gdy projekt jest zbudowany, należy ustawić element metadanych z wartością. W przeciwnym razie można upewnić się, że tylko najnowsza wersja zasobu jest kopiowana do folderu wyjściowego kompilacji `PreserveNewest` przy użyciu wartości.  
  
 Poniżej przedstawiono plik, który jest skonfigurowany jako plik zawartości, który jest kopiowany do folderu wyjściowego kompilacji tylko wtedy, gdy nowa wersja zasobu jest dodawany do projektu.  
  
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
> W programie Visual Studio plik zawartości jest tworzę, `Build Action` dodając `Content`plik do `Copy to Output Directory` `Copy always` projektu i `Always`ustawiając go na , i ustawiając go na (tak samo jak ) i `Copy if newer` (tak samo jak `PreserveNewest`).  
  
 Po zbudowaniu projektu <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atrybut jest kompilowany do metadanych zestawu dla każdego pliku zawartości.  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 Wartość oznacza <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> ścieżkę do pliku zawartości w stosunku do jego pozycji w projekcie. Na przykład jeśli plik zawartości znajdował się w podfolderze projektu, dodatkowe <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> informacje o ścieżce zostaną włączone do wartości.  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 Wartość <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> jest również wartością ścieżki do pliku zawartości w folderze wyjściowym kompilacji.  
  
### <a name="using-content-files"></a>Korzystanie z plików zawartości  
 Aby załadować plik zawartości, <xref:System.Windows.Application.GetContentStream%2A> można wywołać metodę <xref:System.Windows.Application> klasy, przekazując pakiet URI, który identyfikuje żądany plik zawartości. <xref:System.Windows.Application.GetContentStream%2A>zwraca <xref:System.Windows.Resources.StreamResourceInfo> obiekt, który udostępnia plik zawartości <xref:System.IO.Stream> jako i opisuje jego typ zawartości.  
  
 Na przykład poniższy kod pokazuje, <xref:System.Windows.Application.GetContentStream%2A> jak <xref:System.Windows.Controls.Page> użyć do załadowania pliku zawartości <xref:System.Windows.Controls.Frame> `pageFrame`i ustawić go jako zawartość ( ).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 Podczas <xref:System.Windows.Application.GetContentStream%2A> wywoływania daje <xref:System.IO.Stream>dostęp do , trzeba wykonać dodatkową pracę konwersji go do typu właściwości, które będą jej ustawienie. Zamiast tego można pozwolić WPF zadbać o <xref:System.IO.Stream> otwieranie i konwertowanie przez ładowanie pliku zasobów bezpośrednio do właściwości typu przy użyciu kodu.  
  
 W poniższym <xref:System.Windows.Controls.Page> przykładzie pokazano, jak <xref:System.Windows.Controls.Frame> `pageFrame`załadować bezpośrednio do ( ) przy użyciu kodu.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 Poniższy przykład jest odpowiednik znaczników z poprzedniego przykładu.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>
## <a name="site-of-origin-files"></a>Pliki witryny pochodzenia  
 Pliki zasobów mają jawną relację z zestawami, które są <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>dystrybuowane obok, zgodnie z definicją . Ale są chwile, kiedy można ustanowić niejawną lub nieistniejącą relację między zestawem a plikiem danych aplikacji, w tym gdy:  
  
- Plik nie istnieje w czasie kompilacji.  
  
- Nie wiesz, jakie pliki będzie wymagać zestawu do czasu wykonywania.  
  
- Chcesz mieć możliwość aktualizowania plików bez ponownego komppilowania zestawu, z którego są skojarzone.  
  
- Aplikacja używa dużych plików danych, takich jak audio i wideo, i chcesz, aby użytkownicy mogli je pobrać tylko wtedy, gdy zechcą.  
  
 Istnieje możliwość ładowania tego typu plików przy użyciu tradycyjnych schematów URI, takich jak schematy file:/// i http://.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 Jednak schematy file:/// i http:// wymagają pełnego zaufania aplikacji. Jeśli aplikacja jest aplikacją przeglądarki XAML (XBAP), która została uruchomiona z Internetu lub intranetu i żąda tylko zestawu uprawnień, które są dozwolone dla aplikacji uruchomionych z tych lokalizacji, luźne pliki można załadować tylko z miejsca pochodzenia aplikacji (miejsce uruchomienia). Takie pliki są znane jako *pliki witryny pochodzenia.*  
  
 Pliki lokacji pochodzenia są jedyną opcją dla aplikacji częściowego zaufania, chociaż nie są ograniczone do aplikacji częściowego zaufania. Pełne zaufanie aplikacji może nadal trzeba załadować pliki danych aplikacji, które nie wiedzą o w czasie kompilacji; podczas gdy aplikacje pełnego zaufania mogą używać file:///, jest prawdopodobne, że pliki danych aplikacji zostaną zainstalowane w tym samym folderze, w którym lub podfolderze zestawu aplikacji. W takim przypadku korzystanie z odwołów do witryny pochodzenia jest łatwiejsze niż używanie file:///, ponieważ użycie file:/// wymaga wypracowywania pełnej ścieżki pliku.  
  
> [!NOTE]
> Pliki witryny pochodzenia nie są buforowane za pomocą aplikacji przeglądarki XAML (XBAP) na komputerze klienckim, podczas gdy pliki zawartości są. W związku z tym są one pobierane tylko wtedy, gdy jest to wyraźnie wymagane. Jeśli aplikacja przeglądarki XAML (XBAP) ma duże pliki multimedialne, skonfigurowanie ich jako plików lokacji pochodzenia oznacza, że początkowe uruchomienie aplikacji jest znacznie szybsze, a pliki są pobierane tylko na żądanie.  
  
### <a name="configuring-site-of-origin-files"></a>Konfigurowanie plików witryny pochodzenia  
 Jeśli pliki witryny pochodzenia nie istnieją lub są nieznane w czasie kompilacji, należy użyć tradycyjnych mechanizmów wdrażania w celu `XCopy` zapewnienia, że wymagane pliki są dostępne w czasie wykonywania, w tym przy użyciu programu wiersza polecenia lub Instalatora Microsoft Windows.  
  
 Jeśli wiesz, w czasie kompilacji pliki, które mają być zlokalizowane w witrynie pochodzenia, ale nadal chcesz uniknąć jawnej zależności, `None` można dodać te pliki do projektu MSBuild jako element. Podobnie jak w plikach zawartości, należy `CopyToOutputDirectory` ustawić atrybut MSBuild, aby określić, że plik lokacji pochodzenia jest kopiowany `Always` do lokalizacji, która jest względem zestawu wbudowanego, określając wartość lub `PreserveNewest` wartość.  
  
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
> W programie Visual Studio plik witryny pochodzenia można utworzyć, dodając `Build Action` `None`plik do projektu i ustawiając go na .  
  
 Po utworzeniu projektu MSBuild kopiuje określone pliki do folderu wyjściowego kompilacji.  
  
### <a name="using-site-of-origin-files"></a>Korzystanie z plików witryny pochodzenia  
 Aby załadować plik witryny pochodzenia, <xref:System.Windows.Application.GetRemoteStream%2A> można <xref:System.Windows.Application> wywołać metodę klasy, przekazując pakiet URI, który identyfikuje żądaną witrynę pliku pochodzenia. <xref:System.Windows.Application.GetRemoteStream%2A>zwraca <xref:System.Windows.Resources.StreamResourceInfo> obiekt, który udostępnia plik witryny <xref:System.IO.Stream> pochodzenia jako i opisuje jego typ zawartości.  
  
 Na przykład poniższy kod pokazuje, <xref:System.Windows.Application.GetRemoteStream%2A> jak <xref:System.Windows.Controls.Page> użyć do załadowania pliku witryny <xref:System.Windows.Controls.Frame> pochodzenia`pageFrame`i ustawić go jako zawartość ( ).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 Podczas <xref:System.Windows.Application.GetRemoteStream%2A> wywoływania daje <xref:System.IO.Stream>dostęp do , trzeba wykonać dodatkową pracę konwersji go do typu właściwości, które będą jej ustawienie. Zamiast tego można pozwolić WPF zadbać o <xref:System.IO.Stream> otwieranie i konwertowanie przez ładowanie pliku zasobów bezpośrednio do właściwości typu przy użyciu kodu.  
  
 W poniższym <xref:System.Windows.Controls.Page> przykładzie pokazano, jak <xref:System.Windows.Controls.Frame> `pageFrame`załadować bezpośrednio do ( ) przy użyciu kodu.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 Poniższy przykład jest odpowiednik znaczników z poprzedniego przykładu.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>
## <a name="rebuilding-after-changing-build-type"></a>Przebudowa po zmianie typu kompilacji  
 Po zmianie typu kompilacji pliku danych aplikacji, należy odbudować całą aplikację, aby upewnić się, że te zmiany są stosowane. Jeśli tylko utworzyć aplikację, zmiany nie są stosowane.  
  
## <a name="see-also"></a>Zobacz też

- [Pakuj URI w WPF](pack-uris-in-wpf.md)
