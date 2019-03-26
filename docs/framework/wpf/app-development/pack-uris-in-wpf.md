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
ms.openlocfilehash: e84f586e621aa54d7e8a8f62e605ec3016cfb757
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411281"
---
# <a name="pack-uris-in-wpf"></a>Pakuj URI w WPF
W konsoli Windows Presentation Foundation (WPF) [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] są używane do identyfikowania i ładowanie plików na wiele sposobów, w tym następujące:  
  
-   Określanie [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] do wyświetlenia po pierwszym uruchomieniu aplikacji.  
  
-   Ładowanie obrazów.  
  
-   Przejdź do strony.  
  
-   Ładowanie plików danych innego niż plik wykonywalny.  
  
 Ponadto [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] może służyć do identyfikowania i ładowanie plików z różnych miejsc, w tym następujące czynności:  
  
-   Bieżący zestaw.  
  
-   Przywoływanego zestawu.  
  
-   Lokalizacja względem zestawu.  
  
-   Witryna aplikacji pochodzenia.  
  
 Aby zapewnić spójny mechanizm identyfikacji i ładowania tych typów plików z tych lokalizacji [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] korzysta z możliwości rozszerzania usługi *pakowanie schematu URI*. Ten temat zawiera omówienie schematu, opisano, jak utworzyć pakiet [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] dla różnych scenariuszy, w tym artykule omówiono bezwzględnym i względnym [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] i [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] rozdzielczości, przed wyświetleniem sposób użycia pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] z obu znaczników i kod.  
  
  
<a name="The_Pack_URI_Scheme"></a>   
## <a name="the-pack-uri-scheme"></a>Pakowanie schematu URI  
 Ten pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schematu jest używany przez [otwarte konwencje pakietów](https://go.microsoft.com/fwlink/?LinkID=71255) specyfikacji (OPC) w tym artykule opisano model do organizowania i identyfikowanie zawartości. Kluczowe elementy modelu są pakiety i części, gdzie *pakietu* to logiczny kontener przeznaczony dla jednego lub więcej logicznej *części*. Na poniższym rysunku przedstawiono tę koncepcję.  
  
 ![Diagram pakietu i części](./media/pack-uris-in-wpf/wpf-package-parts-diagram.png)  
  
 Aby zidentyfikować elementy, specyfikacji OPC wykorzystuje rozszerzalności RFC 2396 (identyfikatory URI (Uniform Resource): Ogólna składnia) do definiowania pakietowi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schematu.  
  
 Schemat, który jest określony przez [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jest definiowany przez jej prefiks; http, ftp i plik znajdują się znanych przykładów. Ten pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schemat używa "pakiet" jako jego schemat i zawiera dwa składniki: urzędu i ścieżkę. Poniżej przedstawiono formatu pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 pakiet: / /*urząd*/*ścieżki*
  
 *Urząd* Określa typ pakietu, który element jest zawarty w, podczas gdy *ścieżki* Określa lokalizację części w ramach pakietu.  
  
 Poniższy rysunek przedstawia tę koncepcję:  
  
 ![Relacja między pakietu, uprawnienia i ścieżki](./media/pack-uris-in-wpf/wpf-relationship-diagram.png)  
  
 Pakiety i części są analogiczne do aplikacji i plików, w której aplikacja (pakiet) może zawierać jeden lub więcej plików (części), w tym:  
  
-   Pliki zasobów, które są kompilowane do zestawu lokalnego.  
  
-   Pliki zasobów, które są kompilowane do przywoływanego zestawu.  
  
-   Pliki zasobów, które są kompilowane do zestawu odwołującego się.  
  
-   Pliki zawartości.  
  
-   Witryna pochodzenia plików.  
  
 Aby uzyskiwać dostęp do tych typów plików, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] obsługuje dwa urzędy: aplikacja: / / / oraz siteoforigin: / / /. Aplikacja: / / / Urząd identyfikuje pliki danych aplikacji, które są znane w czasie kompilacji, w tym pliki zasobów i zawartości. Siteoforigin: / / / Urząd identyfikuje witrynę pochodzenia plików. Zakres każdego uprawnień jest wyświetlany na poniższej ilustracji.  
  
 ![Schemat identyfikatora URI pakietu](./media/pack-uris-in-wpf/wpf-pack-uri-scheme.png)  
  
> [!NOTE]
>  Składnik wystawcy pod pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jest osadzony [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , wskazuje pakietu i muszą być zgodne z RFC 2396. Ponadto muszą zostać zastąpione przez znak "," znakiem "/", a zastrzeżone znaki, takie jak "%" i "?" musi być poprzedzone znakiem zmiany znaczenia. Zobacz OPC, aby uzyskać szczegółowe informacje.  
  
 W poniższych sekcjach opisano sposób tworzenia pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] za pomocą tych dwóch urzędów w połączeniu z odpowiednich ścieżek do identyfikacji zasobu, zawartość i witryna pochodzenia plików.  
  
<a name="Resource_File_Pack_URIs___Local_Assembly"></a>   
## <a name="resource-file-pack-uris"></a>Identyfikatory URI pakietu plików zasobów  
 Pliki zasobów są skonfigurowane jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Resource` elementy i są kompilowane do zestawów. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] obsługuje konstrukcji pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] który może służyć do identyfikowania plików zasobów, które są kompilowane do zestawu lokalnego lub skompilowany w zestawie, do którego odwołuje się z lokalnym zestawu.  
  
<a name="Local_Assembly_Resource_File"></a>   
### <a name="local-assembly-resource-file"></a>Plik zasobów zestawu lokalnego  
 Ten pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] zasobu pliku, który jest kompilowany do zestawu lokalnego używa następujących urzędu i ścieżki:  
  
-   **Urząd**: aplikacja: / / /.  
  
-   **Ścieżka**: Nazwa pliku zasobów, w tym ścieżki względem katalogu głównego folderu projektu zestawu lokalnego.  
  
 W poniższym przykładzie pokazano pakietowi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku zasobu, który znajduje się w katalogu głównym folderu projektu zestawu lokalnego.  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 W poniższym przykładzie pokazano pakietowi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku zasobu, który znajduje się w podfolderze folderu projektu zestawu lokalnego.  
  
 `pack://application:,,,/Subfolder/ResourceFile.xaml`  
  
<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>   
### <a name="referenced-assembly-resource-file"></a>Plik zasobów zestawu odwołania  
 Ten pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] zasobu pliku, który jest skompilowany w zestawie odwołania używa następujących urzędu i ścieżki:  
  
-   **Urząd**: aplikacja: / / /.  
  
-   **Ścieżka**: Nazwa pliku zasobu, który jest kompilowany do przywoływanego zestawu. Ścieżka musi być zgodna z następującym formatem:  
  
     *AssemblyShortName*{*; Wersja*] {*; PublicKey*]; składnik /*ścieżki*  
  
    -   **AssemblyShortName**: krótka nazwa dla przywoływanego zestawu.  
  
    -   **; Wersja** [Opcjonalna]: wersja przywoływanego zestawu, który zawiera plik zasobów. To jest używany, gdy co najmniej dwóch zestawach o tej samej krótkiej nazwie są ładowane.  
  
    -   **; PublicKey** [Opcjonalna]: klucz publiczny, który został użyty do podpisania przywoływanego zestawu. To jest używany, gdy co najmniej dwóch zestawach o tej samej krótkiej nazwie są ładowane.  
  
    -   **; składnik**: Określa, że z lokalnego zestawu odwołuje się do zestawu są określone.  
  
    -   **/ Ścieżka**: Nazwa pliku zasobów, w tym ścieżki względem katalogu głównego folderu projektu przywoływanego zestawu.  
  
 W poniższym przykładzie pokazano pakietowi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku zasobu, który znajduje się w katalogu głównym folderu projektu przywoływanego zestawu.  
  
 `pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`  
  
 W poniższym przykładzie pokazano pakietowi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku zasobu, który znajduje się w podfolderze folderu projektu przywoływanego zestawu.  
  
 `pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`  
  
 W poniższym przykładzie pokazano pakietowi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku zasobu, który znajduje się w folderze głównym folderu projektu zestawu odwołania, specyficzny dla wersji.  
  
 `pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`  
  
 Należy pamiętać, że pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] tylko w przypadku aplikacji można używać składni dla plików zasobów przywoływany zestaw: / / / urzędu. Na przykład, że nie jest obsługiwana w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
 `pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`  
  
<a name="Content_File_Pack_URIs"></a>   
## <a name="content-file-pack-uris"></a>Identyfikatory URI pakietu zawartości pliku  
 Ten pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla następujących urzędu i ścieżka pliku zawartości:  
  
-   **Urząd**: aplikacja: / / /.  
  
-   **Ścieżka**: Nazwa pliku zawartości, wraz ze ścieżką względną lokalizacji systemu plików w głównym zestawie pliku wykonywalnego aplikacji.  
  
 W poniższym przykładzie pokazano pakietowi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zawartości pliku, znajdującego się w tym samym folderze co zestawu pliku wykonywalnego.  
  
 `pack://application:,,,/ContentFile.xaml`  
  
 W poniższym przykładzie pokazano pakietowi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zawartości pliku, znajdującego się w podfolderze, która jest określana względem zestawu pliku wykonywalnego aplikacji.  
  
 `pack://application:,,,/Subfolder/ContentFile.xaml`  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] pliki zawartości nie nastąpi przejście. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Nawigacji obsługuje tylko schemat [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] pliki, które znajdują się w miejscu pochodzenia.  
  
<a name="The_siteoforigin_____Authority"></a>   
## <a name="site-of-origin-pack-uris"></a>Witryna pochodzenia identyfikatory URI z dodatkiem Service Pack  
 Ten pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] witryny pochodzenia plik używa następujących urzędu i ścieżki:  
  
-   **Urząd**: siteoforigin: / / /.  
  
-   **Ścieżka**: Nazwa witryny pochodzenia pliku, w tym jego ścieżka względem lokalizacji, z której został uruchomiony zestawu pliku wykonywalnego.  
  
 W poniższym przykładzie pokazano pakietowi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] witryny pochodzenia pliku przechowywanego w lokalizacji, z którego uruchomiono zestawu pliku wykonywalnego.  
  
 `pack://siteoforigin:,,,/SiteOfOriginFile.xaml`  
  
 W poniższym przykładzie pokazano pakietowi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] witryny pochodzenia pliku przechowywanego w podfolderze, które jest powiązane z lokalizacją, z którego uruchomiono zestawu pliku wykonywalnego aplikacji.  
  
 `pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`  
  
<a name="Page_Files"></a>   
## <a name="page-files"></a>Pliki stronicowania  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki, które są skonfigurowane jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` elementy są kompilowane do zestawów w taki sam sposób, jak pliki zasobów. W związku z tym [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` elementy mogą być identyfikowane za pomocą pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] plików zasobów.  
  
 Typy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki, które zwykle są skonfigurowane jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` elementy mają jedną z następujących jako ich elementu głównego:  
  
-   <xref:System.Windows.Window?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Page?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>  
  
-   <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>  
  
<a name="Absolute_vs_Relative_Pack_URIs"></a>   
## <a name="absolute-vs-relative-pack-uris"></a>Bezwzględny programu vs. Pakiet względne identyfikatory URI  
 Pełny pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] zawiera schemat, uprawnienia i ścieżki, i jest uznawany za pakietu bezwzględne [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Jako uproszczenia dla deweloperów [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementy zazwyczaj pozwoli odpowiednich atrybutów z pakietem względną [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], która obejmuje tylko ścieżki.  
  
 Na przykład rozważmy następujący pakiet bezwzględne [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla pliku zasobu w zestawie lokalnego.  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 Względna pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odwołujący się do tego zasobu pliku, rachunek będzie następujący.  
  
 `/ResourceFile.xaml`  
  
> [!NOTE]
>  Ponieważ witryna pochodzenia pliki nie są skojarzone z zestawami, ich tylko można się odwoływać przy użyciu pakietu bezwzględne [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)].  
  
 Domyślnie pakiet względną [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] uznaje się względem lokalizacji pliku znaczników i kodu, który zawiera odwołanie. Jeśli używany jest wiodący ukośnik odwrotny, jednak względny pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odwołanie jest wtedy uważany za względem katalogu głównego aplikacji. Na przykład rozważmy następującą strukturę projektu.  
  
 `App.xaml`  
  
 `Page2.xaml`  
  
 `\SubFolder`  
  
 `+ Page1.xaml`  
  
 `+ Page2.xaml`  
  
 Jeśli zawiera Page1.xaml [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odwołujący się *głównego*\SubFolder\Page2.xaml, odwołania można użyć następujących pakiet względną [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 `Page2.xaml`  
  
 Jeśli zawiera Page1.xaml [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odwołujący się *głównego*\Page2.xaml, odwołania można użyć następujących pakiet względną [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 `/Page2.xaml`  
  
<a name="Pack_URI_Resolution"></a>   
## <a name="pack-uri-resolution"></a>Rozpoznawania identyfikatora URI pakietu  
 Format pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] umożliwia pakiet [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] dla różnych typów plików, które wyglądają tak samo. Na przykład rozważmy następujący pakiet bezwzględne [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 `pack://application:,,,/ResourceOrContentFile.xaml`  
  
 Ten pakiet bezwzględne [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] mogłoby się odwoływać do pliku zasobów w zestawie lokalnych lub zawartości pliku. To samo dotyczy następujących względny [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 `/ResourceOrContentFile.xaml`  
  
 Aby określić typ pliku, który pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odwołuje się do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jest rozpoznawana jako [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] dla plików zasobów w lokalnych zestawów i plików zawartości przy użyciu następujących algorytmów heurystycznych:  
  
1.  Metadane zestawu dla sondy <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atrybut, który odpowiada pakietowi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
2.  Jeśli <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atrybut zostanie znaleziony, ścieżki pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odwołuje się do zawartości pliku.  
  
3.  Jeśli <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atrybut nie zostanie znaleziony, pliki zasobów zestawu, które są kompilowane do zestawu lokalnego sondowania.  
  
4.  Jeśli plik zasobu, który odpowiada ścieżce pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] zostanie znaleziony, ścieżki pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odwołuje się do pliku zasobów.  
  
5.  Jeśli zasób nie zostanie znaleziony, utworzone wewnętrznie <xref:System.Uri> jest nieprawidłowy.  
  
 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] rozwiązania nie dotyczy [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] odwołujące się do następujących:  
  
-   Zawartość plików w przywoływanych zestawów: następujące typy plików nie są obsługiwane przez [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
-   Osadzone pliki w przywoływanych zestawach: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] które identyfikują są unikatowe, ponieważ obejmują one nazwę przywoływanego zestawu i `;component` sufiks.  
  
-   Witryna pochodzenia plików: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] które identyfikują są unikatowe, ponieważ są one tylko pliki, które można zidentyfikowane przez pakiet [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] zawierających siteoforigin: / / / urzędu.  
  
 Uproszczenie jednego, który pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] rozpoznawania umożliwia, jest dla kodu w pewnym stopniu niezależnie od lokalizacji plików zasobów i zawartości. Na przykład, jeśli masz plik zasobów w zestawie lokalnego, który jest konfigurowana ponownie do pliku zawartości pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla zasobu pozostają takie same, jak kod, który używa pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
<a name="Programming_with_Pack_URIs"></a>   
## <a name="programming-with-pack-uris"></a>Programowanie za pomocą identyfikatorów URI pakietu  
 Wiele [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] klasy implementuje właściwości, które można skonfigurować z dodatkiem Service pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], w tym:  
  
-   <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>  
  
 Te właściwości można ustawić zarówno z kodu znaczników i kodu. W tej sekcji przedstawiono podstawowe konstrukcje dla obu i następnie przedstawiono przykłady typowych scenariuszy.  
  
<a name="Using_Pack_URIs_in_Markup"></a>   
### <a name="using-pack-uris-in-markup"></a>Za pomocą identyfikatorów URI pakietu w znacznikach  
 Pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jest określona w znaczniku, ustawiając element atrybutu przy użyciu pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Na przykład:  
  
 `<element attribute="pack://application:,,,/File.xaml" />`  
  
 Tabela 1 przedstawiono różne bezwzględna pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , można określić w znacznikach.  
  
 Tabela 1: Identyfikatory URI bezwzględna pakietu, w znacznikach  
  
|Plik|Bezwzględna pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|Plik zasobów — zestawu lokalnego|`"pack://application:,,,/ResourceFile.xaml"`|  
|Plik zasobów w podfolderze — zestawu lokalnego|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|  
|Plik zasobów - przywoływanego zestawu|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|  
|Plik zasobów w podfolderze przywoływanego zestawu|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|Plik zasobów w określonej wersji zestawu odwołania|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|  
|Plik zawartości|`"pack://application:,,,/ContentFile.xaml"`|  
|Plik zawartości w podfolderze|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|  
|Witryna pliku pierwotnego|`"pack://siteoforigin:,,,/SOOFile.xaml"`|  
|Witryna pochodzenia plik w podfolderze|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|  
  
 Tabela 2 ilustruje różne pakiet względną [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , można określić w znacznikach.  
  
 Tabela 2: Pakiet względne identyfikatory URI, w znacznikach  
  
|Plik|Względna pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|Plik zasobów w zestawie lokalne|`"/ResourceFile.xaml"`|  
|Plik zasobów w podfolderze zestawu lokalnego|`"/Subfolder/ResourceFile.xaml"`|  
|Plik zasobów w zestawie odwołania|`"/ReferencedAssembly;component/ResourceFile.xaml"`|  
|Plik zasobów w podfolderze przywoływanego zestawu|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|Plik zawartości|`"/ContentFile.xaml"`|  
|Plik zawartości w podfolderze|`"/Subfolder/ContentFile.xaml"`|  
  
<a name="Using_Pack_URIs_in_Code"></a>   
### <a name="using-pack-uris-in-code"></a>Za pomocą identyfikatorów URI pakietu w kodzie  
 Określ pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] w kodzie przez utworzenie wystąpienia <xref:System.Uri> klasy i przekazywania pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jako parametr do konstruktora. Jest to zaprezentowane w poniższym przykładzie.  
  
```csharp  
Uri uri = new Uri("pack://application:,,,/File.xaml");  
```  
  
 Domyślnie <xref:System.Uri> klasy uwzględnia pakiet [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , aby były absolutne. W związku z tym, zgłaszany jest wyjątek, jeśli wystąpienie <xref:System.Uri> klasa jest tworzona przy użyciu pakietu względną [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
```csharp  
Uri uri = new Uri("/File.xaml");  
```  
  
 Na szczęście <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> przeciążenia <xref:System.Uri> konstruktora klasy akceptuje parametr typu <xref:System.UriKind> pozwala określić, czy pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jest bezwzględny lub względny.  
  
```csharp  
// Absolute URI (default)  
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);  
// Relative URI  
Uri relativeUri = new Uri("/File.xaml",   
                        UriKind.Relative);  
```  
  
 Należy określić tylko <xref:System.UriKind.Absolute> lub <xref:System.UriKind.Relative> gdy masz pewność, że podany pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jest jednej z nich. Jeśli nie znasz typ pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , użycia, na przykład gdy użytkownik wprowadza pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] w czasie wykonywania, użyj <xref:System.UriKind.RelativeOrAbsolute> zamiast tego.  
  
```csharp  
// Relative or Absolute URI provided by user via a text box  
TextBox userProvidedUriTextBox = new TextBox();  
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);  
```  
  
 Tabela 3 ilustruje różne pakiet względną [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , można określić w kodzie za pomocą <xref:System.Uri?displayProperty=nameWithType>.  
  
 Tabela 3: Identyfikatory URI bezwzględna pakietu, w kodzie  
  
|Plik|Bezwzględna pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|Plik zasobów — zestawu lokalnego|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|  
|Plik zasobów w podfolderze — zestawu lokalnego|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|Plik zasobów - przywoływanego zestawu|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|  
|Plik zasobów w podfolderze przywoływanego zestawu|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|Plik zasobów w określonej wersji zestawu odwołania|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|  
|Plik zawartości|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|  
|Plik zawartości w podfolderze|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|  
|Witryna pliku pierwotnego|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|  
|Witryna pochodzenia plik w podfolderze|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|  
  
 Tabela 4 przedstawiono różne pakiet względną [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , można określić w kodzie za pomocą <xref:System.Uri?displayProperty=nameWithType>.  
  
 Tabela 4: Pakiet względne identyfikatory URI, w kodzie  
  
|Plik|Względna pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|Plik zasobów — zestawu lokalnego|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|  
|Plik zasobów w podfolderze — zestawu lokalnego|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|Plik zasobów - przywoływanego zestawu|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|  
|Plik zasobów w podfolderze - przywoływanego zestawu|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|Plik zawartości|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|  
|Plik zawartości w podfolderze|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|  
  
<a name="Common_Pack_URI_Scenarios"></a>   
### <a name="common-pack-uri-scenarios"></a>Typowe scenariusze identyfikatora URI pakietu  
 Poprzednich sekcji mają omówiono sposób tworzenia pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] do identyfikacji zasobu, zawartość i witryna pochodzenia plików. W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], te konstrukcje są używane w na różne sposoby, a w poniższych częściach omówiono kilka typowego użycia.  
  
<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>   
#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a>Określanie interfejsu użytkownika, aby pokazać podczas uruchamiania aplikacji  
 <xref:System.Windows.Application.StartupUri%2A> Określa pierwszy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aby pokazać, kiedy [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacja zostanie uruchomiona. W przypadku aplikacji autonomicznych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] może być to okno, jak pokazano w poniższym przykładzie.  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]  
  
 Aplikacje autonomiczne i [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] można również określić strony jako początkowej interfejsu użytkownika, jak pokazano w poniższym przykładzie.  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]  
  
 Jeśli aplikacja jest aplikacją, a strona jest określony za pomocą <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] otwiera <xref:System.Windows.Navigation.NavigationWindow> do obsługi strony. Aby uzyskać [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], strona jest wyświetlana w przeglądarce hosta.  
  
<a name="Navigating_to_a_Page"></a>   
#### <a name="navigating-to-a-page"></a>Przejdź do strony  
 Poniższy przykład pokazuje, jak można przejść do strony.  
  
 [!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]  
  
 Aby uzyskać więcej informacji na temat różnych sposobów nawigacji w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], zobacz [Nawigacja — omówienie](navigation-overview.md).  
  
<a name="Specifying_a_Window_Icon"></a>   
#### <a name="specifying-a-window-icon"></a>Określanie ikonę okna  
 Poniższy przykład pokazuje sposób korzystania z identyfikatora URI, aby określić ikonę okna.  
  
 [!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Window.Icon%2A>.  
  
<a name="Loading_Image__Audio__and_Video_Files"></a>   
#### <a name="loading-image-audio-and-video-files"></a>Trwa ładowanie obrazu, dźwięku i wideo  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Umożliwia aplikacjom używanie różnych typów nośników, z których wszystkie zidentyfikowane i załadowany z dodatkiem Service pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], jak pokazano w poniższych przykładach.  
  
 [!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]  
  
 [!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]  
  
 [!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]  
  
 Aby uzyskać więcej informacji na temat pracy z zawartości multimedialnej, zobacz [grafika i Multimedia](../graphics-multimedia/index.md).  
  
<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>   
#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a>Trwa ładowanie słownika zasobów z witryny pochodzenia  
 Słowniki zasobów (<xref:System.Windows.ResourceDictionary>) może służyć do obsługi motywów aplikacji. Jednym ze sposobów tworzenia i zarządzania nimi motywy jest do utworzenia wielu motywów jako słowniki zasobów, znajdujących się w witrynie aplikacji pochodzenia. Dzięki temu motywy, aby być dodawane lub aktualizowane bez konieczności ponownego kompilowania i ponownego wdrażania aplikacji. Te słowniki zasobów można zidentyfikować i załadowany przy użyciu pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], która została przedstawiona w poniższym przykładzie.  
  
 [!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]  
  
 Aby uzyskać przegląd motywów w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], zobacz [Tworzenie szablonów i stylów](../controls/styling-and-templating.md).  
  
## <a name="see-also"></a>Zobacz także
- [Zasoby aplikacji WPF, zawartość i pliki danych](wpf-application-resource-content-and-data-files.md)
