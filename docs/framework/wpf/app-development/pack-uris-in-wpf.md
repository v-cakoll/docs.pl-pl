---
title: Pakuj URI w WPF
ms.date: 03/30/2017
helpviewer_keywords:
- pack URI scheme [WPF]
- loading embedded resources [WPF]
- URIs (Uniform Resource Identifiers)
- Uniform Resource Identifiers (URIs)
- loading non-resource files
- application management [WPF]
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
ms.openlocfilehash: ad928fb223ce22c65bb86a78c7d4cd006651a2d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950756"
---
# <a name="pack-uris-in-wpf"></a>Pakuj URI w WPF

W Windows Presentation Foundation (WPF) [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] służy do identyfikowania i ładowania plików na wiele sposobów, w tym:

- Określenie elementu [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] do wyświetlenia podczas pierwszego uruchomienia aplikacji.

- Ładowanie obrazów.

- Przechodzenie do stron.

- Ładowanie niewykonywalnych plików danych.

Ponadto program [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] może służyć do identyfikowania i ładowania plików z różnych lokalizacji, w tym następujących:

- Bieżący zestaw.

- Przywoływany zestaw.

- Lokalizacja względem zestawu.

- Lokacja źródłowa aplikacji.

Aby zapewnić spójny mechanizm do identyfikowania i ładowania tych typów plików z tych lokalizacji, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wykorzystuje rozszerzalność *schematu identyfikatora URI pakietu*. Ten temat zawiera omówienie schematu, a także informacje na [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] temat tworzenia pakietu dla różnych scenariuszy, omawiania absolutnej i względnej [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] i rozpoznawania [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] i kod.

<a name="The_Pack_URI_Scheme"></a>

## <a name="the-pack-uri-scheme"></a>Schemat identyfikatora URI pakietu

Schemat pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jest używany przez specyfikację [Open](https://go.microsoft.com/fwlink/?LinkID=71255) Pack Conventions (OPC), która opisuje model służący do organizowania i identyfikowania zawartości. Kluczowymi elementami tego modelu są pakiety i części, w przypadku których *pakiet* jest kontenerem logicznym dla co najmniej jednej *części*logicznej. Poniższy rysunek ilustruje tę koncepcję.

![Diagram pakietu i części](./media/pack-uris-in-wpf/wpf-package-parts-diagram.png)

Aby zidentyfikować części, Specyfikacja OPC korzysta z rozszerzalności RFC 2396 (Uniform Resource Identifiers (URI): Składnia ogólna) do definiowania schematu pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] .

Schemat, który jest określony przez [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , jest definiowany za pomocą jego prefiksu, protokołu HTTP, FTP i pliku są dobrze znane przykłady. Schemat pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] używa pakietu "Pack" jako schematu i zawiera dwa składniki: Authority i Path. Poniżej przedstawiono format pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].

*ścieżka* *urzędu*/Pack://

*Urząd* określa typ pakietu, w którym znajduje się część, a *ścieżka* określa lokalizację części w ramach pakietu.

Pojęcie to jest zilustrowane na poniższej ilustracji:

![Relacja między pakietem, Urzędem i ścieżką](./media/pack-uris-in-wpf/wpf-relationship-diagram.png)

Pakiety i części są analogiczne do aplikacji i plików, w których aplikacja (pakiet) może zawierać jeden lub więcej plików (części), w tym:

- Pliki zasobów, które są kompilowane do zestawu lokalnego.

- Pliki zasobów, które są kompilowane do zestawu, do którego się odwołuje.

- Pliki zasobów, które są kompilowane do zestawu, do którego się odwołuje.

- Pliki zawartości.

- Lokacja plików pochodzenia.

Aby uzyskać dostęp do tych typów plików [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , program obsługuje dwa urzędy: Application:///i siteoforigin:///. Urząd application:///identyfikuje pliki danych aplikacji, które są znane w czasie kompilacji, w tym pliki zasobów i zawartości. Urząd siteoforigin:///określa lokację plików pochodzenia. Zakres każdego urzędu pokazano na poniższej ilustracji.

![Diagram URI pakietu](./media/pack-uris-in-wpf/wpf-pack-uri-scheme.png)

> [!NOTE]
> Składnik urzędu pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jest osadzony [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , który wskazuje na pakiet i musi być zgodny ze specyfikacją RFC 2396. Ponadto znak "/" musi zostać zastąpiony znakiem "," i znakami zastrzeżonymi, takimi jak "%" i "?", należy zmienić wartość ucieczki. Zobacz OPC, aby uzyskać szczegółowe informacje.

W poniższych sekcjach opisano sposób tworzenia pakietów [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] przy użyciu tych dwóch urzędów w połączeniu z odpowiednimi ścieżkami służącymi do identyfikowania zasobów, zawartości i lokacji plików pochodzenia.

<a name="Resource_File_Pack_URIs___Local_Assembly"></a>

## <a name="resource-file-pack-uris"></a>Identyfikatory URI pakietu plików zasobów

Pliki zasobów są konfigurowane jako elementy `Resource` programu MSBuild i są kompilowane do zestawów. WPF obsługuje konstruowanie identyfikatorów URI pakietów, których można użyć do identyfikowania plików zasobów, które są kompilowane do zestawu lokalnego lub kompilowane do zestawu, do którego odwołuje się zestaw lokalny.

<a name="Local_Assembly_Resource_File"></a>

### <a name="local-assembly-resource-file"></a>Plik zasobu zestawu lokalnego

Pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla pliku zasobów, który jest kompilowany do zestawu lokalnego, używa następującego urzędu i ścieżki:

- **Urząd**: Application:///.

- **Ścieżka**: Nazwa pliku zasobów, łącznie z jego ścieżką, względem katalogu głównego lokalnego folderu projektu zestawu.

W poniższym przykładzie przedstawiono pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dla pliku zasobu, który znajduje się w folderze głównym folderu projektu zestawu lokalnego.

`pack://application:,,,/ResourceFile.xaml`

Poniższy przykład pokazuje pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dla pliku zasobu, który znajduje się w podfolderze folderu projektu zestawu lokalnego.

`pack://application:,,,/Subfolder/ResourceFile.xaml`

<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>

### <a name="referenced-assembly-resource-file"></a>Przywoływany plik zasobu zestawu

Pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla pliku zasobów, który jest kompilowany do zestawu, do którego istnieje odwołanie, używa następującego urzędu i ścieżki:

- **Urząd**: Application:///.

- **Ścieżka**: Nazwa pliku zasobów, który jest kompilowany do przywoływanego zestawu. Ścieżka musi być zgodna z następującym formatem:

  *AssemblyShortName* { *; Wersja*] { *; PublicKey*]; składnik/*ścieżka*

  - **AssemblyShortName**: krótka nazwa przywoływanego zestawu.

  - **; Wersja** [opcjonalna]: wersja przywoływanego zestawu zawierającego plik zasobów. Ta wartość jest używana w przypadku załadowania co najmniej dwóch przywoływanych zestawów o tej samej krótkiej nazwie.

  - **; PublicKey** [opcjonalnie]: klucz publiczny, który został użyty do podpisania przywoływanego zestawu. Ta wartość jest używana w przypadku załadowania co najmniej dwóch przywoływanych zestawów o tej samej krótkiej nazwie.

  - **; składnik**: określa, że zestaw, do którego odwołuje się odwołanie, jest przywoływany z zestawu lokalnego.

  - **/Path**: nazwa pliku zasobów, łącznie z jego ścieżką, względem katalogu głównego folderu projektu zestawu, do którego się odwołuje.

Poniższy przykład pokazuje pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dla pliku zasobu, który znajduje się w katalogu głównym folderu projektu zestawu, do którego się odwołuje.

`pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`

Poniższy przykład pokazuje pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dla pliku zasobu, który znajduje się w podfolderze folderu projektu zestawu, do którego się odwołuje.

`pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`

W poniższym przykładzie przedstawiono pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dla pliku zasobu, który znajduje się w folderze głównym odwołania do folderu projektu zestawu specyficznego dla wersji.

`pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`

Należy zauważyć, że [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] składnia pakietu dla plików zasobów zestawu, do których istnieją odwołania, może być używana tylko z urzędem Application:///. Na przykład następujące elementy nie są obsługiwane w programie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].

`pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`

<a name="Content_File_Pack_URIs"></a>

## <a name="content-file-pack-uris"></a>Identyfikatory URI pakietu plików zawartości

Pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla pliku zawartości używa następującego urzędu i ścieżki:

- **Urząd**: Application:///.

- **Ścieżka**: Nazwa pliku zawartości, łącznie z ścieżką względną do lokalizacji systemu plików głównego zestawu plików wykonywalnych aplikacji.

Poniższy przykład pokazuje pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dla pliku zawartości znajdującego się w tym samym folderze co zestaw wykonywalny.

`pack://application:,,,/ContentFile.xaml`

Poniższy przykład pokazuje pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dla pliku zawartości znajdujący się w podfolderze, który jest względny dla zestawu wykonywalnego aplikacji.

`pack://application:,,,/Subfolder/ContentFile.xaml`

> [!NOTE]
> Nie można przejść do plików zawartości HTML. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Schemat obsługuje tylko nawigację do plików HTML, które znajdują się w lokalizacji źródłowej.

<a name="The_siteoforigin_____Authority"></a>

## <a name="site-of-origin-pack-uris"></a>Witryna identyfikatorów URI pakietu pochodzenia

Pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla lokacji z plikiem pochodzenia używa następującego urzędu i ścieżki:

- **Urząd**: siteoforigin:///.

- **Ścieżka**: Nazwa witryny pliku pierwotnego, w tym jej ścieżka względem lokalizacji, z której został uruchomiony zestaw wykonywalny.

W poniższym przykładzie przedstawiono pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dla lokacji pliku pierwotnego, przechowywany w lokalizacji, z której jest uruchamiany zestaw wykonywalny.

`pack://siteoforigin:,,,/SiteOfOriginFile.xaml`

W poniższym przykładzie przedstawiono pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dla lokacji pliku pierwotnego, przechowywane w podfolderze odnoszący się do lokalizacji, z której jest uruchamiany zestaw wykonywalny aplikacji.

`pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`

<a name="Page_Files"></a>

## <a name="page-files"></a>Pliki stronicowania

Pliki XAML, które są skonfigurowane jako `Page` elementy programu MSBuild, są kompilowane do zestawów w taki sam sposób jak pliki zasobów. W związku z tym `Page` elementy MSBuild można zidentyfikować przy użyciu identyfikatorów URI pakietów dla plików zasobów.

Typy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plików, które są powszechnie skonfigurowane jako elementy programu`Page` MSBuild, mają jeden z następujących elementów jako ich element główny:

- <xref:System.Windows.Window?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Page?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>

- <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>

- <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>

- <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>

<a name="Absolute_vs_Relative_Pack_URIs"></a>

## <a name="absolute-vs-relative-pack-uris"></a>Bezwzględne a Względne identyfikatory URI pakietów

W pełni kwalifikowany pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] obejmuje schemat, Urząd i ścieżkę, a także jest traktowany jako [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]bezwzględny. Jako uproszczenie dla deweloperów, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementy zwykle umożliwiają ustawienie odpowiednich atrybutów z pakietem [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]względnym, który zawiera tylko ścieżkę.

Rozważmy na przykład następujący bezwzględny [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pakiet dla pliku zasobu w lokalnym zestawie.

`pack://application:,,,/ResourceFile.xaml`

Pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] względny, który odwołuje się do tego pliku zasobów, będzie następujący.

`/ResourceFile.xaml`

> [!NOTE]
> Ze względu na to, że lokacja plików pochodzenia nie jest skojarzona z zestawami, można [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]odwoływać się tylko do bezwzględnego pakietu.

Domyślnie pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] względny jest traktowany względem lokalizacji znacznika lub kodu, który zawiera odwołanie. Jeśli jest używany [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] wiodący ukośnik odwrotny, jest on traktowany jako odwołanie względne do katalogu głównego aplikacji. Rozważmy na przykład następującą strukturę projektu.

`App.xaml`

`Page2.xaml`

`\SubFolder`

`+ Page1.xaml`

`+ Page2.xaml`

Jeśli Strona1. XAML zawiera [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odwołanie do *elementu głównego*\SubFolder\Page2.XAML, można użyć następującego powiązanego pakietu. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]

`Page2.xaml`

Jeśli Strona1. XAML zawiera [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odwołanie do *elementu głównego*\Page2.XAML, można użyć następującego powiązanego pakietu. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]

`/Page2.xaml`

<a name="Pack_URI_Resolution"></a>

## <a name="pack-uri-resolution"></a>Rozpoznawanie identyfikatora URI pakietu

Format pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] umożliwia wyszukanie tego samego pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] dla różnych typów plików. Rozważmy na przykład następujący bezwzględny [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]pakiet.

`pack://application:,,,/ResourceOrContentFile.xaml`

Ten bezwzględny pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] może odwoływać się do pliku zasobów w zestawie lokalnym lub w pliku zawartości. Ta sama wartość dotyczy następujących względnych [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].

`/ResourceOrContentFile.xaml`

Aby określić typ pliku, do którego odwołuje się pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , program [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] usuwa [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pliki zasobów w lokalnych zestawach i plikach zawartości przy użyciu następujących algorytmów heurystycznych:

1. Sondowanie metadanych zestawu dla <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atrybutu, który jest zgodny z pakietem. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]

2. Jeśli atrybut zostanie znaleziony, ścieżka do pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odnosi się do pliku zawartości. <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>

3. <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> Jeśli atrybut nie zostanie znaleziony, sonduje pliki zasobów zestawu, które są kompilowane do zestawu lokalnego.

4. Jeśli zostanie znaleziony plik zasobów zgodny ze ścieżką pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , ścieżka do pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odnosi się do pliku zasobów.

5. Jeśli zasób nie zostanie znaleziony, wewnętrznie utworzony <xref:System.Uri> jest nieprawidłowy.

[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]rozwiązanie nie ma zastosowania w [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] odniesieniu do następujących informacji:

- Pliki zawartości w przywoływanych zestawach: te typy plików nie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]są obsługiwane przez program.

- Osadzone pliki w przywoływanych [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] zestawach: identyfikują one są unikatowe `;component` , ponieważ obejmują zarówno nazwę przywoływanego zestawu, jak i sufiks.

- Lokacja plików pierwotnych [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] : określa, że są one unikatowe, ponieważ są to jedyne pliki, które mogą [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] być zidentyfikowane przez pakiet zawierający urząd siteoforigin:///.

Jednym z uproszczeń [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , które może rozpoznać pakiet, jest to, aby kod był nieco niezależny od lokalizacji plików zasobów i zawartości. Jeśli na przykład plik zasobów w lokalnym zestawie, który zostanie ponownie skonfigurowany jako plik zawartości, pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla zasobu pozostaje taki sam, jak kod, który używa pakietu. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]

<a name="Programming_with_Pack_URIs"></a>

## <a name="programming-with-pack-uris"></a>Programowanie przy użyciu identyfikatorów URI pakietów

Wiele [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] klas implementuje właściwości, które można ustawić za pomocą [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]pakietu, w tym:

- <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>

Te właściwości można ustawić zarówno przy użyciu znacznika, jak i kodu. W tej sekcji przedstawiono podstawowe konstrukcje obu programów, a następnie przedstawiono przykłady typowych scenariuszy.

<a name="Using_Pack_URIs_in_Markup"></a>

### <a name="using-pack-uris-in-markup"></a>Używanie identyfikatorów URI pakietów w znacznikach

Pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jest określony w znacznikach przez ustawienie elementu atrybutu z pakietem [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Przykład:

`<element attribute="pack://application:,,,/File.xaml" />`

Tabela 1 ilustruje różne bezwzględne [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pakiety, które można określić w znacznikach.

Tabela 1: Bezwzględne identyfikatory URI pakietów w znacznikach

|Plik|Bezwzględny pakiet[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|Plik zasobu — zestaw lokalny|`"pack://application:,,,/ResourceFile.xaml"`|
|Plik zasobów w podfolderze — zestaw lokalny|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|
|Przywoływany zestaw plików zasobów|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|
|Plik zasobów w podfolderze zestawu, do którego się odwołuje|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|Plik zasobów w przywoływanym zestawie|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|
|Plik zawartości|`"pack://application:,,,/ContentFile.xaml"`|
|Plik zawartości w podfolderze|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|
|Lokacja pliku źródłowego|`"pack://siteoforigin:,,,/SOOFile.xaml"`|
|Lokacja pliku źródłowego w podfolderze|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|

Tabela 2 ilustruje różne pakiety [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] względne, które można określić w znacznikach.

Tabela 2: Względne identyfikatory URI pakietu w znaczniku

|Plik|Pakiet względny[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|Plik zasobów w lokalnym zestawie|`"/ResourceFile.xaml"`|
|Plik zasobów w podfolderze zestawu lokalnego|`"/Subfolder/ResourceFile.xaml"`|
|Plik zasobów w przywoływanym zestawie|`"/ReferencedAssembly;component/ResourceFile.xaml"`|
|Plik zasobów w podfolderze zestawu, do którego się odwołuje|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|Plik zawartości|`"/ContentFile.xaml"`|
|Plik zawartości w podfolderze|`"/Subfolder/ContentFile.xaml"`|

<a name="Using_Pack_URIs_in_Code"></a>

### <a name="using-pack-uris-in-code"></a>Używanie identyfikatorów URI pakietów w kodzie

Należy określić pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] w kodzie, tworząc wystąpienie <xref:System.Uri> klasy i przekazując pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jako parametr do konstruktora. Jest to zaprezentowane w poniższym przykładzie.

```csharp
Uri uri = new Uri("pack://application:,,,/File.xaml");
```

Domyślnie <xref:System.Uri> Klasa traktuje pakiet [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] jako bezwzględny. W związku z tym wyjątek jest zgłaszany, gdy wystąpienie <xref:System.Uri> klasy jest tworzone z pakietem [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]względnym.

```csharp
Uri uri = new Uri("/File.xaml");
```

Na szczęście <xref:System.Uri> <xref:System.UriKind> przeciążenie konstruktora klasy akceptuje parametr typu, aby można było określić, czy pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jest bezwzględny, czy względny. <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29>

```csharp
// Absolute URI (default)
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);
// Relative URI
Uri relativeUri = new Uri("/File.xaml",
                        UriKind.Relative);
```

Należy określić tylko <xref:System.UriKind.Absolute> lub <xref:System.UriKind.Relative> wtedy, gdy masz pewność, że dostarczony pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] to jeden lub drugi. Jeśli nie znasz typu używanego pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , na przykład gdy użytkownik wprowadzi pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] w czasie wykonywania, użyj <xref:System.UriKind.RelativeOrAbsolute> zamiast tego.

```csharp
// Relative or Absolute URI provided by user via a text box
TextBox userProvidedUriTextBox = new TextBox();
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);
```

Tabela 3 ilustruje różne pakiety [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] względne, które można określić w kodzie przy użyciu. <xref:System.Uri?displayProperty=nameWithType>

Tabela 3: Bezwzględne identyfikatory URI pakietów w kodzie

|Plik|Bezwzględny pakiet[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|Plik zasobu — zestaw lokalny|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|
|Plik zasobów w podfolderze — zestaw lokalny|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|Przywoływany zestaw plików zasobów|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|
|Plik zasobów w podfolderze zestawu, do którego się odwołuje|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|Plik zasobów w przywoływanym zestawie|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|
|Plik zawartości|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|
|Plik zawartości w podfolderze|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|
|Lokacja pliku źródłowego|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|
|Lokacja pliku źródłowego w podfolderze|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|

W tabeli 4 przedstawiono różne powiązane pakiety [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , które można określić w kodzie przy <xref:System.Uri?displayProperty=nameWithType>użyciu.

Tabela 4: Względne identyfikatory URI pakietu w kodzie

|Plik|Pakiet względny[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|Plik zasobu — zestaw lokalny|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|
|Plik zasobów w podfolderze — zestaw lokalny|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|Przywoływany zestaw plików zasobów|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|
|Plik zasobów w zestawie podfolderów, do którego się odwołuje|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|Plik zawartości|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|
|Plik zawartości w podfolderze|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|

<a name="Common_Pack_URI_Scenarios"></a>

### <a name="common-pack-uri-scenarios"></a>Scenariusze typowych identyfikatorów URI pakietu

W poprzednich sekcjach omówiono sposób konstruowania pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] do identyfikowania zasobów, zawartości i lokalizacji plików pochodzenia. W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]programie te konstrukcje są używane na różne sposoby, a poniższe sekcje obejmują kilka typowych zastosowań.

<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>

#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a>Określanie interfejsu użytkownika do wyświetlania podczas uruchamiania aplikacji

<xref:System.Windows.Application.StartupUri%2A>Określa pierwszy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , który ma być wyświetlany [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , gdy aplikacja jest uruchamiana. W przypadku aplikacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] autonomicznych może to być okno, jak pokazano w poniższym przykładzie.

[!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]

Aplikacje autonomiczne [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] i mogą również określać stronę jako początkowy interfejs użytkownika, jak pokazano w poniższym przykładzie.

[!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]

Jeśli aplikacja jest aplikacją autonomiczną, a strona jest określona za pomocą <xref:System.Windows.Application.StartupUri%2A>programu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , program <xref:System.Windows.Navigation.NavigationWindow> otwiera na potrzeby hostowania strony. W [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]przypadku programu strona jest wyświetlana w przeglądarce hosta.

<a name="Navigating_to_a_Page"></a>

#### <a name="navigating-to-a-page"></a>Przechodzenie do strony

Poniższy przykład pokazuje, jak przejść do strony.

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

Aby uzyskać więcej informacji na temat różnych sposobów nawigowania [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]w programie, zobacz [Omówienie nawigacji](navigation-overview.md).

<a name="Specifying_a_Window_Icon"></a>

#### <a name="specifying-a-window-icon"></a>Określanie ikony okna

Poniższy przykład pokazuje, jak używać identyfikatora URI, aby określić ikonę okna.

[!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]

Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Window.Icon%2A>.

<a name="Loading_Image__Audio__and_Video_Files"></a>

#### <a name="loading-image-audio-and-video-files"></a>Ładowanie plików obrazów, audio i wideo

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]zezwala aplikacjom na korzystanie z różnych typów nośników, które mogą być zidentyfikowane i ładowane z pakietem [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], jak pokazano w poniższych przykładach.

[!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]

[!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]

[!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]

Aby uzyskać więcej informacji na temat pracy z zawartością multimedialną, zobacz [grafika i multimedia](../graphics-multimedia/index.md).

<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>

#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a>Ładowanie słownika zasobów z lokacji źródłowej

Słowniki zasobów<xref:System.Windows.ResourceDictionary>() mogą służyć do obsługi motywów aplikacji. Jednym ze sposobów tworzenia motywów i zarządzania nimi jest utworzenie wielu motywów jako słowników zasobów, które znajdują się w lokacji źródłowej aplikacji. Dzięki temu można dodawać i aktualizować motywy bez ponownego kompilowania i wdrażania aplikacji. Te słowniki zasobów można identyfikować i ładować przy [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]użyciu pakietu, który jest przedstawiony w poniższym przykładzie.

[!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]

Aby zapoznać się z omówieniem motywów w programie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], zobacz [Style i tworzenia szablonów](../controls/styling-and-templating.md).

## <a name="see-also"></a>Zobacz także

- [Zasoby aplikacji WPF, zawartość i pliki danych](wpf-application-resource-content-and-data-files.md)
