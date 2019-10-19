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
ms.openlocfilehash: 59c72d9ae12a014a8c47cb3b2852b337b173446c
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72580620"
---
# <a name="pack-uris-in-wpf"></a>Pakuj URI w WPF

W Windows Presentation Foundation (WPF) identyfikatory Uniform Resource Identifier (URI) służą do identyfikowania i ładowania plików na wiele sposobów, w tym:

- Określanie [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], który ma być wyświetlany podczas pierwszego uruchomienia aplikacji.

- Ładowanie obrazów.

- Przechodzenie do stron.

- Ładowanie niewykonywalnych plików danych.

Ponadto identyfikatory URI mogą służyć do identyfikowania i ładowania plików z różnych lokalizacji, w tym następujących:

- Bieżący zestaw.

- Przywoływany zestaw.

- Lokalizacja względem zestawu.

- Lokacja źródłowa aplikacji.

Aby zapewnić spójny mechanizm do identyfikowania i ładowania tych typów plików z tych lokalizacji, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wykorzystuje rozszerzalność *schematu identyfikatora URI pakietu*. Ten temat zawiera omówienie schematu, w którym opisano sposób konstruowania identyfikatorów URI pakietów dla różnych scenariuszy, omówiono bezwzględne i względne identyfikatory URI oraz rozpoznawanie identyfikatorów URI, przed pokazywaniem sposobu używania identyfikatorów URI pakietów z znaczników i kodu.

<a name="The_Pack_URI_Scheme"></a>

## <a name="the-pack-uri-scheme"></a>Schemat identyfikatora URI pakietu

Schemat URI pakietu jest używany przez specyfikację [Open Pack Conventions](https://go.microsoft.com/fwlink/?LinkID=71255) (OPC), która opisuje model organizowania i identyfikowania zawartości. Kluczowymi elementami tego modelu są pakiety i części, w przypadku których *pakiet* jest kontenerem logicznym dla co najmniej jednej *części*logicznej. Poniższy rysunek ilustruje tę koncepcję.

![Diagram pakietu i części](./media/pack-uris-in-wpf/wpf-package-parts-diagram.png)

Aby zidentyfikować części, Specyfikacja OPC korzysta z rozszerzalności RFC 2396 (Uniform Resource Identifiers (URI): Generic Syntax), aby zdefiniować schemat identyfikatora URI pakietu.

Schemat, który jest określony za pomocą identyfikatora URI, jest definiowany za pomocą jego prefiksu; protokoły HTTP, FTP i File są dobrze znane przykłady. Schemat URI pakietu używa pakietu "Pack" jako schematu i zawiera dwa składniki: Authority i Path. Poniżej przedstawiono format identyfikatora URI pakietu.

*ścieżka* /*urzędu* Pack://

*Urząd* określa typ pakietu, w którym znajduje się część, a *ścieżka* określa lokalizację części w ramach pakietu.

Pojęcie to jest zilustrowane na poniższej ilustracji:

![Relacja między pakietem, Urzędem i ścieżką](./media/pack-uris-in-wpf/wpf-relationship-diagram.png)

Pakiety i części są analogiczne do aplikacji i plików, w których aplikacja (pakiet) może zawierać jeden lub więcej plików (części), w tym:

- Pliki zasobów, które są kompilowane do zestawu lokalnego.

- Pliki zasobów, które są kompilowane do zestawu, do którego się odwołuje.

- Pliki zasobów, które są kompilowane do zestawu, do którego się odwołuje.

- Pliki zawartości.

- Lokacja plików pochodzenia.

Aby uzyskać dostęp do tych typów plików, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] obsługuje dwa urzędy: application:///i siteoforigin:///. Urząd application:///identyfikuje pliki danych aplikacji, które są znane w czasie kompilacji, w tym pliki zasobów i zawartości. Urząd siteoforigin:///określa lokację plików pochodzenia. Zakres każdego urzędu pokazano na poniższej ilustracji.

![Diagram URI pakietu](./media/pack-uris-in-wpf/wpf-pack-uri-scheme.png)

> [!NOTE]
> Składnik urzędu URI pakietu jest osadzonym identyfikatorem URI, który wskazuje na pakiet i musi być zgodny ze specyfikacją RFC 2396. Ponadto znak "/" musi zostać zastąpiony znakiem "," i znakami zastrzeżonymi, takimi jak "%" i "?", należy zmienić wartość ucieczki. Zobacz OPC, aby uzyskać szczegółowe informacje.

W poniższych sekcjach opisano sposób tworzenia identyfikatorów URI pakietów przy użyciu tych dwóch urzędów w połączeniu z odpowiednimi ścieżkami do identyfikowania zasobów, zawartości i lokacji plików pochodzenia.

<a name="Resource_File_Pack_URIs___Local_Assembly"></a>

## <a name="resource-file-pack-uris"></a>Identyfikatory URI pakietu plików zasobów

Pliki zasobów są konfigurowane jako elementy `Resource` MSBuild i są kompilowane do zestawów. WPF obsługuje konstruowanie identyfikatorów URI pakietów, których można użyć do identyfikowania plików zasobów, które są kompilowane do zestawu lokalnego lub kompilowane do zestawu, do którego odwołuje się zestaw lokalny.

<a name="Local_Assembly_Resource_File"></a>

### <a name="local-assembly-resource-file"></a>Plik zasobu zestawu lokalnego

Identyfikator URI pakietu dla pliku zasobu, który jest kompilowany do zestawu lokalnego, używa następującego urzędu i ścieżki:

- **Urząd**: Application:///.

- **Path**: nazwa pliku zasobów, łącznie z jego ścieżką, względem katalogu głównego projektu zestawu lokalnego.

Poniższy przykład pokazuje identyfikator URI pakietu dla pliku zasobów [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], który znajduje się w folderze głównym folderu projektu zestawu lokalnego.

`pack://application:,,,/ResourceFile.xaml`

Poniższy przykład pokazuje identyfikator URI pakietu dla pliku zasobów [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], który znajduje się w podfolderze folderu projektu zestawu lokalnego.

`pack://application:,,,/Subfolder/ResourceFile.xaml`

<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>

### <a name="referenced-assembly-resource-file"></a>Przywoływany plik zasobu zestawu

Identyfikator URI pakietu dla pliku zasobu, który jest kompilowany do zestawu, do którego istnieje odwołanie, używa następującego urzędu i ścieżki:

- **Urząd**: Application:///.

- **Ścieżka**: nazwa pliku zasobów, który jest kompilowany do zestawu, do którego się odwołuje. Ścieżka musi być zgodna z następującym formatem:

  *AssemblyShortName*{ *; Wersja*] { *; PublicKey*]; składnik/*ścieżka*

  - **AssemblyShortName**: krótka nazwa przywoływanego zestawu.

  - **; Wersja** [opcjonalna]: wersja przywoływanego zestawu zawierającego plik zasobów. Ta wartość jest używana w przypadku załadowania co najmniej dwóch przywoływanych zestawów o tej samej krótkiej nazwie.

  - **; PublicKey** [opcjonalnie]: klucz publiczny, który został użyty do podpisania przywoływanego zestawu. Ta wartość jest używana w przypadku załadowania co najmniej dwóch przywoływanych zestawów o tej samej krótkiej nazwie.

  - **; składnik**: określa, że zestaw, do którego odwołuje się odwołanie, jest przywoływany z zestawu lokalnego.

  - **/Path**: nazwa pliku zasobów, łącznie z jego ścieżką, względem katalogu głównego folderu projektu zestawu, do którego się odwołuje.

Poniższy przykład pokazuje identyfikator URI pakietu dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku zasobów, który znajduje się w katalogu głównym folderu projektu zestawu, do którego się odwołuje.

`pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`

Poniższy przykład pokazuje identyfikator URI pakietu dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku zasobów, który znajduje się w podfolderze folderu projektu zestawu, do którego się odwołuje.

`pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`

W poniższym przykładzie przedstawiono identyfikator URI pakietu dla pliku zasobów [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], który znajduje się w folderze głównym, do którego odwołuje się folder projektu zestawu o określonej wersji.

`pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`

Należy zauważyć, że składnia identyfikatora URI pakietu dla przywoływanych plików zasobów zestawu może być używana tylko z urzędem application:///. Na przykład następujące elementy nie są obsługiwane w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].

`pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`

<a name="Content_File_Pack_URIs"></a>

## <a name="content-file-pack-uris"></a>Identyfikatory URI pakietu plików zawartości

Identyfikator URI pakietu dla pliku zawartości używa następującego urzędu i ścieżki:

- **Urząd**: Application:///.

- **Path**: nazwa pliku zawartości, włącznie z ścieżką względną do lokalizacji systemu plików głównego zestawu plików wykonywalnych aplikacji.

W poniższym przykładzie przedstawiono identyfikator URI pakietu dla pliku zawartości [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znajdującego się w tym samym folderze, w którym znajduje się zestaw wykonywalny.

`pack://application:,,,/ContentFile.xaml`

Poniższy przykład pokazuje identyfikator URI pakietu dla pliku zawartości [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znajdującego się w podfolderze odnoszącym się do zestawu wykonywalnego aplikacji.

`pack://application:,,,/Subfolder/ContentFile.xaml`

> [!NOTE]
> Nie można przejść do plików zawartości HTML. Schemat identyfikatora URI obsługuje tylko nawigację do plików HTML, które znajdują się w lokalizacji źródłowej.

<a name="The_siteoforigin_____Authority"></a>

## <a name="site-of-origin-pack-uris"></a>Witryna identyfikatorów URI pakietu pochodzenia

Identyfikator URI pakietu dla witryny pliku pochodzenia używa następującego urzędu i ścieżki:

- **Urząd**: siteoforigin:///.

- **Path**: Nazwa lokacji pliku pierwotnego, łącznie z ścieżką względną do lokalizacji, z której został uruchomiony zestaw wykonywalny.

Poniższy przykład pokazuje identyfikator URI pakietu dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lokacji pliku pierwotnego, przechowywane w lokalizacji, z której jest uruchamiany zestaw wykonywalny.

`pack://siteoforigin:,,,/SiteOfOriginFile.xaml`

Poniższy przykład pokazuje identyfikator URI pakietu dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lokacji pliku pierwotnego, przechowywane w podfolderze, który jest względny do lokalizacji, z której jest uruchamiany zestaw wykonywalny aplikacji.

`pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`

<a name="Page_Files"></a>

## <a name="page-files"></a>Pliki stronicowania

Pliki XAML, które są skonfigurowane jako elementy `Page` MSBuild, są kompilowane do zestawów w taki sam sposób jak pliki zasobów. W związku z tym elementy `Page` MSBuild można zidentyfikować przy użyciu identyfikatorów URI pakietów dla plików zasobów.

Typy plików [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], które są powszechnie skonfigurowane jako elementy programu MSBuild `Page`, mają jeden z następujących elementów jako ich element główny:

- <xref:System.Windows.Window?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Page?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>

- <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>

- <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>

- <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>

<a name="Absolute_vs_Relative_Pack_URIs"></a>

## <a name="absolute-vs-relative-pack-uris"></a>Bezwzględne a względne identyfikatory URI pakietu

W pełni kwalifikowany identyfikator URI pakietu obejmuje schemat, Urząd i ścieżkę, a także jest traktowany jako bezwzględny identyfikator URI pakietu. Jako uproszczenie dla deweloperów, elementy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zwykle umożliwiają ustawienie odpowiednich atrybutów z względnym identyfikatorem URI, który zawiera tylko ścieżkę.

Rozważmy na przykład następujący bezwzględny identyfikator URI pakietu dla pliku zasobu w zestawie lokalnym.

`pack://application:,,,/ResourceFile.xaml`

Względny identyfikator URI pakietu, który odwołuje się do tego pliku zasobów, będzie następujący.

`/ResourceFile.xaml`

> [!NOTE]
> Ze względu na to, że lokacja plików pochodzenia nie jest skojarzona z zestawami, można odwoływać się tylko do bezwzględnych identyfikatorów URI pakietów.

Domyślnie względny identyfikator URI pakietu jest traktowany względem lokalizacji znacznika lub kodu, który zawiera odwołanie. Jeśli jest używany wiodący ukośnik odwrotny, odwołanie względnego identyfikatora URI jest uznawane za odnoszące się do katalogu głównego aplikacji. Rozważmy na przykład następującą strukturę projektu.

`App.xaml`

`Page2.xaml`

`\SubFolder`

`+ Page1.xaml`

`+ Page2.xaml`

Jeśli Strona1. XAML zawiera identyfikator URI, który odwołuje się do *elementu głównego*\SubFolder\Page2.XAML, odwołanie może korzystać z następującego względnego identyfikatora URI pakietu.

`Page2.xaml`

Jeśli Strona1. XAML zawiera identyfikator URI, który odwołuje się do *elementu głównego*\Page2.XAML, odwołanie może korzystać z następującego względnego identyfikatora URI pakietu.

`/Page2.xaml`

<a name="Pack_URI_Resolution"></a>

## <a name="pack-uri-resolution"></a>Rozpoznawanie identyfikatora URI pakietu

Format identyfikatorów URI pakietów umożliwia wyszukanie tego samego identyfikatora URI pakietów dla różnych typów plików. Rozważmy na przykład następujący bezwzględny identyfikator URI pakietu.

`pack://application:,,,/ResourceOrContentFile.xaml`

Ten bezwzględny identyfikator URI pakietu może odwoływać się do pliku zasobów w lokalnym zestawie lub pliku zawartości. Ta sama wartość dotyczy poniższego względnego identyfikatora URI.

`/ResourceOrContentFile.xaml`

Aby określić typ pliku, do którego odwołuje się identyfikator URI pakietu, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozpoznaje identyfikatory URI dla plików zasobów w lokalnych zestawach i plikach zawartości przy użyciu następujących algorytmów heurystycznych:

1. Sondowanie metadanych zestawu dla <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atrybutu, który jest zgodny z identyfikatorem URI pakietu.

2. Jeśli zostanie znaleziony atrybut <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>, ścieżka identyfikatora URI pakietu odwołuje się do pliku zawartości.

3. Jeśli atrybut <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> nie zostanie znaleziony, sonduje pliki zasobów zestawu, które są kompilowane do zestawu lokalnego.

4. Jeśli zostanie znaleziony plik zasobów zgodny ze ścieżką identyfikatora URI pakietu, ścieżka identyfikatora URI pakietu odwołuje się do pliku zasobów.

5. Jeśli zasób nie zostanie znaleziony, wewnętrznie utworzony <xref:System.Uri> jest nieprawidłowy.

Rozpoznawanie identyfikatorów URI nie ma zastosowania w przypadku identyfikatorów URI, które odwołują się do następujących:

- Pliki zawartości w przywoływanych zestawach: te typy plików nie są obsługiwane przez [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].

- Osadzone pliki w przywoływanych zestawach: identyfikatory URI, które identyfikują je są unikatowe, ponieważ zawierają zarówno nazwę przywoływanego zestawu, jak i sufiks `;component`.

- Lokacja plików pochodzenia: identyfikatory URI, które identyfikują są unikatowe, ponieważ są jedynymi plikami, które mogą być identyfikowane przez identyfikatory URI pakietów, które zawierają siteoforigin:///Urząd.

Jednym z elementów uproszczenia, jakie jest rozpoznawanie identyfikatorów URI pakietu, jest to, że kod może być nieco niezależny od lokalizacji plików zasobów i zawartości. Jeśli na przykład plik zasobów w lokalnym zestawie, który zostanie ponownie skonfigurowany jako plik zawartości, identyfikator URI pakietu dla zasobu pozostaje taki sam, jak kod używający identyfikatora URI pakietu.

<a name="Programming_with_Pack_URIs"></a>

## <a name="programming-with-pack-uris"></a>Programowanie przy użyciu identyfikatorów URI pakietów

Wiele klas [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] implementuje właściwości, które można ustawić za pomocą identyfikatorów URI pakietów, takich jak:

- <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>

Te właściwości można ustawić zarówno przy użyciu znacznika, jak i kodu. W tej sekcji przedstawiono podstawowe konstrukcje obu programów, a następnie przedstawiono przykłady typowych scenariuszy.

<a name="Using_Pack_URIs_in_Markup"></a>

### <a name="using-pack-uris-in-markup"></a>Używanie identyfikatorów URI pakietów w znacznikach

Identyfikator URI pakietu jest określony w znaczniku przez ustawienie elementu atrybutu z identyfikatorem URI pakietu. Na przykład:

`<element attribute="pack://application:,,,/File.xaml" />`

Tabela 1 ilustruje różne identyfikatory URI bezwzględnych pakietów, które można określić w znacznikach.

Tabela 1: bezwzględne identyfikatory URI pakietu w znaczniku

|Plik|Bezwzględny identyfikator URI pakietu|
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

Tabela 2 ilustruje różne względne identyfikatory URI pakietów, które można określić w znacznikach.

Tabela 2: względne identyfikatory URI pakietu w znaczniku

|Plik|Względny identyfikator URI pakietu|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|Plik zasobów w lokalnym zestawie|`"/ResourceFile.xaml"`|
|Plik zasobów w podfolderze zestawu lokalnego|`"/Subfolder/ResourceFile.xaml"`|
|Plik zasobów w przywoływanym zestawie|`"/ReferencedAssembly;component/ResourceFile.xaml"`|
|Plik zasobów w podfolderze zestawu, do którego się odwołuje|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|Plik zawartości|`"/ContentFile.xaml"`|
|Plik zawartości w podfolderze|`"/Subfolder/ContentFile.xaml"`|

<a name="Using_Pack_URIs_in_Code"></a>

### <a name="using-pack-uris-in-code"></a>Używanie identyfikatorów URI pakietów w kodzie

Należy określić identyfikator URI pakietu w kodzie, tworząc wystąpienie klasy <xref:System.Uri> i przekazując identyfikator URI pakietu jako parametr do konstruktora. Jest to zaprezentowane w poniższym przykładzie.

```csharp
Uri uri = new Uri("pack://application:,,,/File.xaml");
```

Domyślnie Klasa <xref:System.Uri> traktuje identyfikatory URI pakietu jako bezwzględne. W związku z tym wyjątek jest zgłaszany, gdy wystąpienie klasy <xref:System.Uri> jest tworzone z względnym identyfikatorem URI.

```csharp
Uri uri = new Uri("/File.xaml");
```

Na szczęście <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> przeciążenie konstruktora klasy <xref:System.Uri> akceptuje parametr typu <xref:System.UriKind>, aby określić, czy identyfikator URI pakietu jest bezwzględny, czy względny.

```csharp
// Absolute URI (default)
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);
// Relative URI
Uri relativeUri = new Uri("/File.xaml",
                        UriKind.Relative);
```

Należy określić tylko <xref:System.UriKind.Absolute> lub <xref:System.UriKind.Relative>, gdy masz pewność, że podany identyfikator URI pakietu to jeden lub drugi. Jeśli nie znasz typu używanego identyfikatora URI, na przykład gdy użytkownik wprowadzi identyfikator URI pakietu w czasie wykonywania, zamiast tego użyj <xref:System.UriKind.RelativeOrAbsolute>.

```csharp
// Relative or Absolute URI provided by user via a text box
TextBox userProvidedUriTextBox = new TextBox();
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);
```

Tabela 3 ilustruje różne względne identyfikatory URI pakietów, które można określić w kodzie przy użyciu <xref:System.Uri?displayProperty=nameWithType>.

Tabela 3: bezwzględne identyfikatory URI pakietu w kodzie

|Plik|Bezwzględny identyfikator URI pakietu|
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

W tabeli 4 przedstawiono różne względne identyfikatory URI pakietów, które można określić w kodzie przy użyciu <xref:System.Uri?displayProperty=nameWithType>.

Tabela 4: względne identyfikatory URI pakietu w kodzie

|Plik|Względny identyfikator URI pakietu|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|Plik zasobu — zestaw lokalny|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|
|Plik zasobów w podfolderze — zestaw lokalny|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|Przywoływany zestaw plików zasobów|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|
|Plik zasobów w zestawie podfolderów, do którego się odwołuje|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|Plik zawartości|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|
|Plik zawartości w podfolderze|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|

<a name="Common_Pack_URI_Scenarios"></a>

### <a name="common-pack-uri-scenarios"></a>Scenariusze typowych identyfikatorów URI pakietu

W powyższych sekcjach omówiono sposób tworzenia identyfikatorów URI pakietów w celu identyfikowania zasobów, zawartości i lokacji plików pochodzenia. W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] te konstrukcje są używane na różne sposoby, a poniższe sekcje obejmują kilka typowych zastosowań.

<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>

#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a>Określanie interfejsu użytkownika do wyświetlania podczas uruchamiania aplikacji

<xref:System.Windows.Application.StartupUri%2A> określa pierwszy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], który ma być wyświetlany podczas uruchamiania aplikacji [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. W przypadku aplikacji autonomicznych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] może być oknem, jak pokazano w poniższym przykładzie.

[!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]

Aplikacje autonomiczne i [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] mogą również określać stronę jako początkowy interfejs użytkownika, jak pokazano w poniższym przykładzie.

[!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]

Jeśli aplikacja jest aplikacją autonomiczną, a strona jest określona za pomocą <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] otwiera <xref:System.Windows.Navigation.NavigationWindow> do hostowania strony. W przypadku [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] strona jest wyświetlana w przeglądarce hosta.

<a name="Navigating_to_a_Page"></a>

#### <a name="navigating-to-a-page"></a>Przechodzenie do strony

Poniższy przykład pokazuje, jak przejść do strony.

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

Aby uzyskać więcej informacji na temat różnych sposobów nawigowania w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], zobacz [Omówienie nawigacji](navigation-overview.md).

<a name="Specifying_a_Window_Icon"></a>

#### <a name="specifying-a-window-icon"></a>Określanie ikony okna

Poniższy przykład pokazuje, jak używać identyfikatora URI, aby określić ikonę okna.

[!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]

Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Window.Icon%2A>.

<a name="Loading_Image__Audio__and_Video_Files"></a>

#### <a name="loading-image-audio-and-video-files"></a>Ładowanie plików obrazów, audio i wideo

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umożliwia aplikacjom korzystanie z różnych typów nośników, które można zidentyfikować i załadować przy użyciu identyfikatorów URI pakietów, jak pokazano w poniższych przykładach.

[!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]

[!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]

[!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]

Aby uzyskać więcej informacji na temat pracy z zawartością multimedialną, zobacz [grafika i multimedia](../graphics-multimedia/index.md).

<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>

#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a>Ładowanie słownika zasobów z lokacji źródłowej

Słowniki zasobów (<xref:System.Windows.ResourceDictionary>) mogą służyć do obsługi motywów aplikacji. Jednym ze sposobów tworzenia motywów i zarządzania nimi jest utworzenie wielu motywów jako słowników zasobów, które znajdują się w lokacji źródłowej aplikacji. Dzięki temu można dodawać i aktualizować motywy bez ponownego kompilowania i wdrażania aplikacji. Te słowniki zasobów można identyfikować i ładować przy użyciu identyfikatorów URI pakietów, które przedstawiono w poniższym przykładzie.

[!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]

Aby zapoznać się z omówieniem tematów w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], zobacz [Style i tworzenia szablonów](../controls/styling-and-templating.md).

## <a name="see-also"></a>Zobacz także

- [Zasoby aplikacji WPF, zawartość i pliki danych](wpf-application-resource-content-and-data-files.md)
