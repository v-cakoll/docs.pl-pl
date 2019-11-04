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
ms.openlocfilehash: a31dc2c5431c8201607462e8bdef4b8bae0fb41d
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460913"
---
# <a name="wpf-application-resource-content-and-data-files"></a>Zasoby aplikacji WPF, zawartość, pliki danych
Aplikacje Microsoft Windows często zależą od plików, które zawierają dane niewykonywalne, takie jak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], obrazy, wideo i dźwięk. Windows Presentation Foundation (WPF) oferuje specjalną obsługę konfigurowania, identyfikowania i korzystania z tych typów plików danych, które są nazywane plikami danych aplikacji. Ta obsługa dotyczy określonego zestawu typów plików danych aplikacji, w tym:  
  
- **Pliki zasobów**: pliki danych, które są kompilowane do pliku wykonywalnego lub biblioteki [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zestawu.  
  
- **Pliki zawartości**: autonomiczne pliki danych z jawnym skojarzeniem z wykonywalnym zestawem [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
- **Lokacja plików początkowych**: autonomiczne pliki danych, które nie mają skojarzenia z wykonywalnym zestawem [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
 Jednym z ważnych różnic między tymi trzema typami plików jest to, że pliki zasobów i zawartości są znane w czasie kompilacji; zestaw ma jawną wiedzę o nich. Jednak w przypadku lokacji z plikami pochodzenia zestaw może nie mieć w ogóle informacji o nich ani niejawnej wiedzy za pomocą odwołania URI (Uniform Resource Identifier). w przypadku tej ostatniej nie ma gwarancji, że w rzeczywistości istnieje przywoływana lokacja pliku pierwotnego.  
  
 Aby odwoływać się do plików danych aplikacji, Windows Presentation Foundation (WPF) używa schematu identyfikatora URI (Uniform Resource Identifier), który jest szczegółowo opisany w artykule [identyfikatory URI pakietu w WPF](pack-uris-in-wpf.md)).  
  
 W tym temacie opisano sposób konfigurowania plików danych aplikacji i korzystania z nich.  

<a name="Resource_Files"></a>   
## <a name="resource-files"></a>Pliki zasobów  
 Jeśli plik danych aplikacji musi być zawsze dostępny dla aplikacji, jedynym sposobem na zagwarantowanie dostępności jest skompilowanie go do głównego zestawu wykonywalnego aplikacji lub jednego z zestawów, do których się odwołuje. Ten typ pliku danych aplikacji jest znany jako *plik zasobów*.  
  
 Plików zasobów należy używać w programie:  
  
- Nie trzeba aktualizować zawartości pliku zasobów po skompilowaniu jej do zestawu.  
  
- Chcesz uprościć złożoność dystrybucji aplikacji, zmniejszając liczbę zależności między plikami.  
  
- Plik danych aplikacji musi być Lokalizowalny (zobacz [Omówienie globalizacji i lokalizacji platformy WPF](../advanced/wpf-globalization-and-localization-overview.md)).  
  
> [!NOTE]
> Pliki zasobów opisane w tej sekcji są inne niż pliki zasobów opisane w obszarze [zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md) i różne od osadzonych lub połączonych zasobów opisanych w temacie [Zarządzanie zasobami aplikacji (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  
  
### <a name="configuring-resource-files"></a>Konfigurowanie plików zasobów  
 W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], plik zasobów jest plikiem, który jest zawarty w projekcie Microsoft Build Engine (MSBuild) jako element `Resource`.  
  
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
> W programie Visual Studio tworzysz plik zasobów, dodając plik do projektu i ustawiając jego `Build Action`, aby `Resource`.  
  
 Po skompilowaniu projektu MSBuild kompiluje zasób do zestawu.  
  
### <a name="using-resource-files"></a>Korzystanie z plików zasobów  
 Aby załadować plik zasobów, można wywołać metodę <xref:System.Windows.Application.GetResourceStream%2A> klasy <xref:System.Windows.Application>, przekazując identyfikator URI pakietu, który identyfikuje żądany plik zasobów. <xref:System.Windows.Application.GetResourceStream%2A> zwraca obiekt <xref:System.Windows.Resources.StreamResourceInfo>, który udostępnia plik zasobów jako <xref:System.IO.Stream> i opisuje jego typ zawartości.  
  
 Na przykład poniższy kod ilustruje sposób użycia <xref:System.Windows.Application.GetResourceStream%2A> do załadowania <xref:System.Windows.Controls.Page> pliku zasobów i ustawienia go jako zawartości <xref:System.Windows.Controls.Frame> (`pageFrame`):  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 Podczas wywoływania <xref:System.Windows.Application.GetResourceStream%2A> zapewnia dostęp do <xref:System.IO.Stream>, należy wykonać dodatkową ilość pracy, aby przekonwertować ją na typ właściwości, za pomocą której zostanie on ustawiony. Zamiast tego można zezwolić [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] na otwieranie i konwertowanie <xref:System.IO.Stream> przez załadowanie pliku zasobów bezpośrednio do właściwości typu za pomocą kodu.  
  
 Poniższy przykład pokazuje, jak załadować <xref:System.Windows.Controls.Page> bezpośrednio do <xref:System.Windows.Controls.Frame> (`pageFrame`) przy użyciu kodu.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 Poniższy przykład jest odpowiednikiem znaczników z poprzedniego przykładu.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a>Pliki kodu aplikacji jako pliki zasobów  
 Do specjalnego zestawu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] plików kodu aplikacji można odwoływać się za pomocą identyfikatorów URI pakietów, takich jak Windows, strony, dokumenty przepływu i słowniki zasobów. Na przykład można ustawić właściwość <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> z identyfikatorem URI pakietu, który odwołuje się do okna lub strony, które chcesz załadować podczas uruchamiania aplikacji.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 Można to zrobić, gdy plik XAML zostanie uwzględniony w projekcie MSBuild jako element `Page`.  
  
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
> W programie Visual Studio dodano nowe <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>lub <xref:System.Windows.ResourceDictionary> do projektu, `Build Action` do pliku znaczników zostanie domyślnie `Page`.  
  
 Po skompilowaniu projektu z `Page` elementy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementy są konwertowane na format binarny i kompilowane w skojarzonym zestawie. W związku z tym te pliki mogą być używane w taki sam sposób jak w przypadku typowych plików zasobów.  
  
> [!NOTE]
> Jeśli plik [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest skonfigurowany jako element `Resource` i nie ma pliku związanego z kodem, nieprzetworzony [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest kompilowany do zestawu, a nie jako wersja binarna nieprzetworzonej [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
<a name="Content_Files"></a>   
## <a name="content-files"></a>Pliki zawartości  
 *Plik zawartości* jest dystrybuowany jako luźny plik obok zestawu wykonywalnego. Chociaż nie są one kompilowane do zestawu, zestawy są kompilowane za pomocą metadanych, które tworzą skojarzenie z każdym plikiem zawartości.  
  
 Plików zawartości należy używać, gdy aplikacja wymaga określonego zestawu plików danych aplikacji, które mają być w stanie aktualizować bez ponownego kompilowania zestawu, który go używa.  
  
### <a name="configuring-content-files"></a>Konfigurowanie plików zawartości  
 Aby dodać plik zawartości do projektu, plik danych aplikacji musi być dołączony jako element `Content`. Ponadto, ponieważ plik zawartości nie jest kompilowany bezpośrednio do zestawu, należy ustawić element metadanych `CopyToOutputDirectory` MSBuild, aby określić, że plik zawartości jest kopiowany do lokalizacji względnej dla skompilowanego zestawu. Jeśli zasób ma być kopiowany do folderu danych wyjściowych kompilacji przy każdym skompilowaniu projektu, należy ustawić `CopyToOutputDirectory` element metadanych z wartością `Always`. W przeciwnym razie można upewnić się, że tylko Najnowsza wersja zasobu jest kopiowana do folderu danych wyjściowych kompilacji przy użyciu wartości `PreserveNewest`.  
  
 Poniżej przedstawiono plik skonfigurowany jako plik zawartości, który jest kopiowany do folderu danych wyjściowych kompilacji tylko wtedy, gdy nowa wersja zasobu zostanie dodana do projektu.  
  
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
> W programie Visual Studio można utworzyć plik zawartości przez dodanie pliku do projektu i ustawienie jego `Build Action` na `Content`i ustawić `Copy to Output Directory` na `Copy always` (analogicznie jak `Always`) i `Copy if newer` (analogicznie jak `PreserveNewest`).  
  
 Podczas kompilowania projektu, <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atrybut jest kompilowany do metadanych zestawu dla każdego pliku zawartości.  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 Wartość <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> oznacza ścieżkę do pliku zawartości względem jego położenia w projekcie. Na przykład, jeśli plik zawartości znajduje się w podfolderze projektu, dodatkowe informacje o ścieżce zostaną włączone do wartości <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>.  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 Wartość <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> jest również wartością ścieżki do pliku zawartości w folderze danych wyjściowych kompilacji.  
  
### <a name="using-content-files"></a>Korzystanie z plików zawartości  
 Aby załadować plik zawartości, można wywołać metodę <xref:System.Windows.Application.GetContentStream%2A> klasy <xref:System.Windows.Application>, przekazując identyfikator URI pakietu, który identyfikuje żądany plik zawartości. <xref:System.Windows.Application.GetContentStream%2A> zwraca obiekt <xref:System.Windows.Resources.StreamResourceInfo>, który uwidacznia plik zawartości jako <xref:System.IO.Stream> i opisuje jego typ zawartości.  
  
 Na przykład poniższy kod ilustruje sposób użycia <xref:System.Windows.Application.GetContentStream%2A> do załadowania <xref:System.Windows.Controls.Page> pliku zawartości i ustawienia go jako zawartości <xref:System.Windows.Controls.Frame> (`pageFrame`).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 Podczas wywoływania <xref:System.Windows.Application.GetContentStream%2A> zapewnia dostęp do <xref:System.IO.Stream>, należy wykonać dodatkową ilość pracy, aby przekonwertować ją na typ właściwości, za pomocą której zostanie on ustawiony. Zamiast tego można zezwolić [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] na otwieranie i konwertowanie <xref:System.IO.Stream> przez załadowanie pliku zasobów bezpośrednio do właściwości typu za pomocą kodu.  
  
 Poniższy przykład pokazuje, jak załadować <xref:System.Windows.Controls.Page> bezpośrednio do <xref:System.Windows.Controls.Frame> (`pageFrame`) przy użyciu kodu.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 Poniższy przykład jest odpowiednikiem znaczników z poprzedniego przykładu.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>   
## <a name="site-of-origin-files"></a>Lokacja plików pochodzenia  
 Pliki zasobów mają jawną relację z zestawami, które są dystrybuowane razem, zgodnie z definicją <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>. Ale istnieją przypadki, w których można określić niejawną lub nieistniejącą relację między zestawem a plikiem danych aplikacji, w tym:  
  
- Plik nie istnieje w czasie kompilacji.  
  
- Nie wiesz, jakie pliki będą wymagane przez zestaw do czasu wykonania.  
  
- Chcesz mieć możliwość aktualizowania plików bez ponownego kompilowania zestawu, z którym są skojarzone.  
  
- Aplikacja używa dużych plików danych, takich jak audio i wideo, i chcesz, aby użytkownicy mogli je pobrać, jeśli zdecydują się na to.  
  
 Istnieje możliwość załadowania tych typów plików przy użyciu tradycyjnych schematów URI, takich jak schematy file:///i http://.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 Jednak schematy file:///i http://wymagają, aby aplikacja miała pełne zaufanie. Jeśli aplikacja jest aplikacją przeglądarki XAML (XBAP), która została uruchomiona z Internetu lub intranetu, i żąda tylko zestawu uprawnień, które są dozwolone dla aplikacji uruchomionych z tych lokalizacji, luźne pliki można ładować tylko z Lokacja źródłowa aplikacji (lokalizacja uruchamiania). Takie pliki są znane jako *lokacja plików pochodzenia* .  
  
 Lokacja plików pochodzenia jest jedyną opcją dla aplikacji częściowo zaufanych, chociaż nie są ograniczone do aplikacji częściowo zaufanych. Aplikacje z pełnym zaufaniem mogą nadal potrzebować załadowania plików danych aplikacji, które nie są znane w czasie kompilacji; gdy aplikacje z pełnym zaufaniem mogą korzystać z file:///, prawdopodobnie pliki danych aplikacji zostaną zainstalowane w tym samym folderze co lub w podfolderze zestawu aplikacji. W takim przypadku użycie funkcji odwołującej się do lokalizacji jest łatwiejsze niż używanie file:///, ponieważ użycie file:///wymaga wykonania pełnej ścieżki do pliku.  
  
> [!NOTE]
> Lokacja plików pochodzenia nie jest buforowana przez aplikację przeglądarki XAML (XBAP) na komputerze klienckim, natomiast pliki zawartości to. W związku z tym są pobierane tylko wtedy, gdy jest to wymagane. Jeśli aplikacja przeglądarki XAML (XBAP) ma duże pliki multimedialne, skonfigurowanie ich jako lokacji plików pochodzenia oznacza, że początkowe uruchomienie aplikacji jest znacznie szybsze i pliki są pobierane na żądanie.  
  
### <a name="configuring-site-of-origin-files"></a>Konfigurowanie lokacji plików pochodzenia  
 Jeśli witryna plików pochodzenia jest nieistniejąca lub nieznana w czasie kompilacji, należy użyć tradycyjnych mechanizmów wdrażania, aby upewnić się, że wymagane pliki są dostępne w czasie wykonywania, w tym przy użyciu narzędzia wiersza polecenia `XCopy` lub systemu Microsoft Windows Instalatora.  
  
 Jeśli wiesz, jak w czasie kompilacji pliki, które mają znajdować się w lokacji pochodzenia, ale nadal chcesz uniknąć jawnej zależności, możesz dodać te pliki do projektu MSBuild jako element `None`. Podobnie jak w przypadku plików zawartości, należy ustawić atrybut `CopyToOutputDirectory` MSBuild, aby określić, że lokacja pliku pochodzenia jest kopiowana do lokalizacji, która jest względna w stosunku do skompilowanego zestawu, przez określenie wartości `Always` lub wartości `PreserveNewest`.  
  
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
> W programie Visual Studio możesz utworzyć lokację pliku pierwotnego, dodając plik do projektu i ustawiając jego `Build Action`, aby `None`.  
  
 Po skompilowaniu projektu, MSBuild kopiuje określone pliki do folderu danych wyjściowych kompilacji.  
  
### <a name="using-site-of-origin-files"></a>Korzystanie z lokalizacji plików pochodzenia  
 Aby załadować lokację pliku pierwotnego, można wywołać metodę <xref:System.Windows.Application.GetRemoteStream%2A> klasy <xref:System.Windows.Application>, przekazując identyfikator URI pakietu, który identyfikuje żądaną lokację pliku pierwotnego. <xref:System.Windows.Application.GetRemoteStream%2A> zwraca obiekt <xref:System.Windows.Resources.StreamResourceInfo>, który uwidacznia lokację pliku źródłowego jako <xref:System.IO.Stream> i opisuje jego typ zawartości.  
  
 Na przykład poniższy kod ilustruje sposób użycia <xref:System.Windows.Application.GetRemoteStream%2A> do załadowania lokacji <xref:System.Windows.Controls.Page> pliku pierwotnego i ustawienia jej jako zawartości <xref:System.Windows.Controls.Frame> (`pageFrame`).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 Podczas wywoływania <xref:System.Windows.Application.GetRemoteStream%2A> zapewnia dostęp do <xref:System.IO.Stream>, należy wykonać dodatkową ilość pracy, aby przekonwertować ją na typ właściwości, za pomocą której zostanie on ustawiony. Zamiast tego można zezwolić [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] na otwieranie i konwertowanie <xref:System.IO.Stream> przez załadowanie pliku zasobów bezpośrednio do właściwości typu za pomocą kodu.  
  
 Poniższy przykład pokazuje, jak załadować <xref:System.Windows.Controls.Page> bezpośrednio do <xref:System.Windows.Controls.Frame> (`pageFrame`) przy użyciu kodu.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 Poniższy przykład jest odpowiednikiem znaczników z poprzedniego przykładu.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>   
## <a name="rebuilding-after-changing-build-type"></a>Ponowne kompilowanie po zmianie typu kompilacji  
 Po zmianie typu kompilacji pliku danych aplikacji należy ponownie skompilować całą aplikację, aby upewnić się, że te zmiany są stosowane. Jeśli aplikacja zostanie utworzona tylko, zmiany nie są stosowane.  
  
## <a name="see-also"></a>Zobacz także

- [Pakowanie URI w WPF](pack-uris-in-wpf.md)
