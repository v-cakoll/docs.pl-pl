---
title: Pakuj URI w WPF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pack URI scheme [WPF]
- loading embedded resources [WPF]
- URIs (Uniform Resource Identifiers)
- Uniform Resource Identifiers (URIs)
- loading non-resource files
- application management [WPF]
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 05e13b8fc899b5cc6addb6d41db826f39b7528f0
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="pack-uris-in-wpf"></a>Pakuj URI w WPF
W [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)], [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] są używane do identyfikowania i ładować pliki na wiele sposobów, w tym następujące:  
  
-   Określanie [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] do wyświetlenia po pierwszym uruchamiania aplikacji.  
  
-   Podczas ładowania obrazów.  
  
-   Przechodzenie do strony.  
  
-   Ładowanie plików danych z systemem innym niż plik wykonywalny.  
  
 Ponadto [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] może służyć do identyfikowania i ładowanie plików z różnych lokalizacji, w tym następujące:  
  
-   Bieżący zestaw.  
  
-   Przywoływanego zestawu.  
  
-   Lokalizacja względem zestawu.  
  
-   Aplikacji witryny pochodzenia.  
  
 Aby zapewnić spójny mechanizm identyfikacji i ładowania tych typów plików w tych lokalizacjach [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] korzysta z rozszerzeń z *schemat identyfikatora URI pack*. Ten temat zawiera omówienie systemu, opisano sposób tworzenia pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] dla różnych scenariuszy, w tym artykule omówiono bezwzględnym i względnym [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] i [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] rozpoznawania przed pokazaniem jak używać dodatkiem Service pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] z obu znaczników i kod.  
  
  
<a name="The_Pack_URI_Scheme"></a>   
## <a name="the-pack-uri-scheme"></a>Schemat identyfikatora URI Pack  
 Ten pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schemat jest używany przez [otwartych Konwencji pakietów](http://go.microsoft.com/fwlink/?LinkID=71255) specyfikacji (pakietów OPC) opisano model organizowanie i identyfikacji zawartości. Kluczowe elementy modelu są pakiety i części, których *pakietu* jest kontenerem logicznym dla jednego lub więcej logicznej *części*. Poniższa ilustracja przedstawia tę koncepcję.  
  
 ![Diagram pakietu i części](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure1.PNG "WPFPackURISchemeFigure1")  
  
 Aby zidentyfikować elementy, specyfikacja OPC wykorzystuje funkcjonalność RFC 2396 (identyfikatory URI (Uniform Resource): ogólna składnia) do definiowania pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schematu.  
  
 Schemat, który jest określony przez [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jest definiowana za pomocą jego prefiks; http, ftp i plik znajdują się przykłady dobrze znanego. Ten pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schemat używa "pakiet" jego schemat i zawiera dwa składniki: urzędu i ścieżkę. Poniżej przedstawiono format pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 dodatkiem Service Pack: / /*urzędu*/*ścieżki*
  
 *Urzędu* Określa typ pakietu, który części jest zawarty w, podczas gdy *ścieżki* Określa lokalizację, w części w ramach pakietu.  
  
 Następujący rysunek przedstawia tę koncepcję:  
  
 ![Relacja między pakietem, uprawnienia i ścieżka](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure2.PNG "WPFPackURISchemeFigure2")  
  
 Pakiety i części są analogiczne do aplikacji i plików, w której aplikacja (pakiet) może zawierać jeden lub więcej plików (składniki), w tym:  
  
-   Pliki zasobów, które są kompilowane do zestawu lokalnego.  
  
-   Pliki zasobów, które są kompilowane do przywoływanego zestawu.  
  
-   Pliki zasobów, które są łączone w odwołaniem do zestawu.  
  
-   Pliki zawartości.  
  
-   Witryny pochodzenia plików.  
  
 Aby dostęp do tych typów plików, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] obsługuje dwa urzędy: aplikacji: / / / oraz siteoforigin: / / /. Aplikacja: / / / urzędu identyfikuje pliki danych aplikacji, które są znane w czasie kompilacji, w tym pliki zasobów i zawartości. Siteoforigin: lokalizacje urzędu identyfikuje witryny pochodzenia plików. Na poniższej ilustracji przedstawiono zakres każdego uprawnień.  
  
 ![Schemat identyfikatora URI Pack](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure4.png "WPFPackURISchemeFigure4")  
  
> [!NOTE]
>  Składnik urzędu pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jest osadzony [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] punktów do pakietu i musi być zgodna z RFC 2396. Ponadto muszą zostać zastąpione znakiem "," znak "/", a zastrzeżone znaki, takie jak "%" i "?" muszą być zmienione znaczenie. Zobacz OPC, aby uzyskać szczegółowe informacje.  
  
 W poniższych sekcjach opisano sposób tworzenia pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] przy użyciu tych dwóch urzędów w połączeniu z odpowiednich ścieżek do identyfikacji zasobu, zawartość i witryny pochodzenia plików.  
  
<a name="Resource_File_Pack_URIs___Local_Assembly"></a>   
## <a name="resource-file-pack-uris"></a>Identyfikatory URI pakietu plików zasobów  
 Pliki zasobów są skonfigurowane jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Resource` elementów i są kompilowane do zestawów. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]obsługuje konstrukcji pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] można zidentyfikować pliki zasobów, które są kompilowane do zestawu lokalnego lub skompilowany w zestawie, do którego odwołuje się z lokalnym zestawu.  
  
<a name="Local_Assembly_Resource_File"></a>   
### <a name="local-assembly-resource-file"></a>Plik zasobów zestawu lokalnego  
 Ten pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] zasobu pliku, który jest kompilowany do zestawu lokalnego używa następujących urzędu i ścieżki:  
  
-   **Urząd**: aplikacji: / / /.  
  
-   **Ścieżka**: Nazwa pliku zasobu, wraz ze ścieżką względem katalogu głównego folderu projektu zestawu lokalnego.  
  
 W poniższym przykładzie przedstawiono pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku zasobu, który znajduje się w katalogu głównym folderu projektu zestawu lokalnego.  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 W poniższym przykładzie przedstawiono pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku zasobu, który znajduje się w podfolderze folderu projektu zestawu lokalnego.  
  
 `pack://application:,,,/Subfolder/ResourceFile.xaml`  
  
<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>   
### <a name="referenced-assembly-resource-file"></a>Plik zasobu przywoływanego zestawu  
 Ten pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] zasobu pliku, który ma zostać skompilowany w zestawie używa następujących urzędu i ścieżki:  
  
-   **Urząd**: aplikacji: / / /.  
  
-   **Ścieżka**: Nazwa pliku zasobu, który jest kompilowany do przywoływanego zestawu. Ścieżka musi być zgodna z następującym formacie:  
  
     *AssemblyShortName*{*; Wersja*] {*; PublicKey*]; component /*ścieżki*  
  
    -   **AssemblyShortName**: krótka nazwa dla przywoływanego zestawu.  
  
    -   **; Wersja** (opcjonalne): wersja przywoływanego zestawu, który zawiera plik zasobu. Służy to, gdy co najmniej dwa zestawy występujące w odwołaniach o tej samej krótkiej nazwie zostały załadowane.  
  
    -   **; PublicKey** [opcjonalnie]: klucz publiczny, który został użyty do podpisania przywoływanego zestawu. Służy to, gdy co najmniej dwa zestawy występujące w odwołaniach o tej samej krótkiej nazwie zostały załadowane.  
  
    -   **; składnika**: Określa, czy z lokalnego zestawu odwołuje się do zestawu następuje odwołanie.  
  
    -   **/ Ścieżki**: Nazwa pliku zasobu, wraz ze ścieżką względem katalogu głównego folderu projektu przywoływanego zestawu.  
  
 W poniższym przykładzie przedstawiono pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku zasobu, który znajduje się w katalogu głównym folderu projektu przywoływanego zestawu.  
  
 `pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`  
  
 W poniższym przykładzie przedstawiono pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku zasobu, który znajduje się w podfolderze folderu projektu przywoływanego zestawu.  
  
 `pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`  
  
 W poniższym przykładzie przedstawiono pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku zasobu, który znajduje się w folderze głównym folderu projektu zestaw do którego istnieje odwołanie, określonej wersji.  
  
 `pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`  
  
 Należy pamiętać, że pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] składnię przywoływanego zestawu plików zasobów mogą być używane tylko z aplikacji: / / / urzędu. Na przykład następujące nie jest obsługiwany w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
 `pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`  
  
<a name="Content_File_Pack_URIs"></a>   
## <a name="content-file-pack-uris"></a>Identyfikatory URI Pack pliku zawartości  
 Ten pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla pliku zawartości używa następujących urzędu i ścieżki:  
  
-   **Urząd**: aplikacji: / / /.  
  
-   **Ścieżka**: Nazwa zawartości pliku, wraz ze ścieżką względną wobec lokalizacji pliku systemu głównego pliku wykonywalnego zestawu aplikacji.  
  
 W poniższym przykładzie przedstawiono pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zawartości pliku, znajdującego się w tym samym folderze co zestawu pliku wykonywalnego.  
  
 `pack://application:,,,/ContentFile.xaml`  
  
 W poniższym przykładzie przedstawiono pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku zawartości, znajduje się w podfolderze, względem pliku wykonywalnego zestawu aplikacji.  
  
 `pack://application:,,,/Subfolder/ContentFile.xaml`  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]pliki zawartości nie może zostać przesłane do. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Schemat obsługuje tylko nawigacji do [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] pliki, które znajdują się w witrynie pochodzenia.  
  
<a name="The_siteoforigin_____Authority"></a>   
## <a name="site-of-origin-pack-uris"></a>Witryny pochodzenia URI pakietu  
 Ten pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla witryny pochodzenia pliku używa następujących urzędu i ścieżki:  
  
-   **Urząd**: siteoforigin: / / /.  
  
-   **Ścieżka**: Nazwa witryny pochodzenia pliku, wraz ze ścieżką względną wobec lokalizacji, z którego uruchomiono zestawu pliku wykonywalnego.  
  
 W poniższym przykładzie przedstawiono pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] witryny pochodzenia pliku, przechowywane w lokalizacji, z którego uruchomiono wykonywalnego zestawu.  
  
 `pack://siteoforigin:,,,/SiteOfOriginFile.xaml`  
  
 W poniższym przykładzie przedstawiono pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] witryny pochodzenia pliku, przechowywane w podfolderze względną wobec lokalizacji, w którym jest uruchamiana wykonywalnego zestawu aplikacji.  
  
 `pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`  
  
<a name="Page_Files"></a>   
## <a name="page-files"></a>Pliki stronicowania  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]pliki, które są skonfigurowane jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` elementy są kompilowane do zestawów w taki sam sposób jak pliki zasobów. W rezultacie [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` elementy mogą zostać zidentyfikowane przy użyciu pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] plików zasobów.  
  
 Typy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki, które zwykle są skonfigurowane jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` elementy mają jeden z następujących jako ich elementu głównego:  
  
-   <xref:System.Windows.Window?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Page?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>  
  
-   <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>  
  
<a name="Absolute_vs_Relative_Pack_URIs"></a>   
## <a name="absolute-vs-relative-pack-uris"></a>Bezwzględny vs. Pakiet względne identyfikatory URI  
 Pełny pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] zawiera schemat, uprawnień i ścieżkę, i jest uznawany za bezwzględna pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Jako uproszczenia dla deweloperów [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementy umożliwiają zazwyczaj Ustaw odpowiednie atrybuty z pakietem względną [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], która obejmuje tylko ścieżki.  
  
 Rozważmy na przykład następujący pakiet bezwzględną [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla pliku zasobu w zestawie lokalnego.  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 Pakiet względną [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odwołujący się do tego zasobu pliku będą następujące.  
  
 `/ResourceFile.xaml`  
  
> [!NOTE]
>  Ponieważ witryny pochodzenia pliki nie są skojarzone z zestawów, one tylko można odwoływać się z pakietem bezwzględną [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)].  
  
 Domyślnie pakiet względną [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jest uznawany za względną wobec lokalizacji znaczników lub kod, który zawiera odwołanie. Jeśli używana jest wiodącego ukośnika, jednak względnej pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odwołanie jest uznawany za następnie względem katalogu głównego aplikacji. Na przykład należy wziąć pod uwagę następujące struktury projektu.  
  
 `App.xaml`  
  
 `Page2.xaml`  
  
 `\SubFolder`  
  
 `+ Page1.xaml`  
  
 `+ Page2.xaml`  
  
 Jeśli zawiera Page1.xaml [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , która odwołuje się *głównego*\SubFolder\Page2.xaml, odwołanie można użyć następujących pakietu względną [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 `Page2.xaml`  
  
 Jeśli zawiera Page1.xaml [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , która odwołuje się *głównego*\Page2.xaml, odwołanie można użyć następujących pakietu względną [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 `/Page2.xaml`  
  
<a name="Pack_URI_Resolution"></a>   
## <a name="pack-uri-resolution"></a>Rozpoznawania identyfikatora URI Pack  
 Format pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] sprawia, że istnieje możliwość, że pakiet [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] dla różnych typów plików do przeszukania takie same. Rozważmy na przykład następujący pakiet bezwzględną [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 `pack://application:,,,/ResourceOrContentFile.xaml`  
  
 Ten pakiet bezwzględną [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] można odwoływać się do pliku zasobu w zestawie lokalnego lub pliku zawartości. To samo dotyczy następujących względnej [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 `/ResourceOrContentFile.xaml`  
  
 Aby określić typ pliku pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odwołuje się do, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozpoznaje [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] dla plików zasobów lokalnych zestawów i plików zawartości przy użyciu następujących Algorytm heurystyczny:  
  
1.  Sonda metadanych zestawu <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atrybut, który odpowiada pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
2.  Jeśli <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atrybut zostanie znaleziony, ścieżka pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odwołuje się do pliku zawartości.  
  
3.  Jeśli <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> nie odnaleziono atrybutu, pliki zasobów zestawu, które są kompilowane do zestawu lokalnego sondowania.  
  
4.  Jeśli plik zasobów zgodna ze ścieżką pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] zostanie znaleziony, ścieżka pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odwołuje się do pliku zasobów.  
  
5.  Jeśli nie można odnaleźć zasobu, utworzone wewnętrznie <xref:System.Uri> jest nieprawidłowy.  
  
 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]rozdzielczość nie jest stosowany dla [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] odwołujące się do następujących:  
  
-   Zawartość plików w przywoływanych zestawach: następujące typy plików nie są obsługiwane przez [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
-   Osadzone pliki w przywoływanych zestawach: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] które identyfikują są unikatowe, ponieważ zawierają one nazwę zestawu, do którego istnieje odwołanie i `;component` sufiks.  
  
-   Witryny pochodzenia plików: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] które identyfikują są unikatowe, ponieważ są one tylko pliki, które mogą zostać zidentyfikowane przez pakiet [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] zawierających siteoforigin: / / / urzędu.  
  
 Uproszczenie jednego, czy pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] rozpoznawania umożliwia dla kodu nieco niezależnie od lokalizacji zasobów i zawartość plików jest. Na przykład, jeśli plik zasobu w zestawie lokalnego, który jest konfigurowane jako plik zawartości pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla zasobu jest taka sama, jak kod, który korzysta z pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
<a name="Programming_with_Pack_URIs"></a>   
## <a name="programming-with-pack-uris"></a>Programowanie za pomocą identyfikatorów URI pakietu  
 Wiele [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] klasy implementować właściwości, które można skonfigurować z dodatkiem Service pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], takie jak:  
  
-   <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>  
  
 Te właściwości można ustawić zarówno znaczników i kodu. W tej sekcji przedstawiono podstawowe konstrukcji dla obu, a następnie przedstawiono przykłady typowych scenariuszy.  
  
<a name="Using_Pack_URIs_in_Markup"></a>   
### <a name="using-pack-uris-in-markup"></a>W znaczniku przy użyciu identyfikatorów URI pakietu  
 Pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jest określony w znaczniku przez ustawienie elementu atrybutu przy użyciu pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Na przykład:  
  
 `<element attribute="pack://application:,,,/File.xaml" />`  
  
 Tabela 1 przedstawiono różne bezwzględna pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] wskazanym w znaczniku.  
  
 Tabela 1: Bezwzględna pakietu URI w znaczniku  
  
|Plik|Bezwzględna pakietu[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|Plik zasobów — zestawu lokalnego|`"pack://application:,,,/ResourceFile.xaml"`|  
|Plik zasobów w podfolderze - zestawu lokalnego|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|  
|Plik zasobów - przywoływanego zestawu|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|  
|Plik zasobów w podfolderze przywoływanego zestawu|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|Plik zasobów w określonej wersji przywoływanego zestawu.|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|  
|Plik zawartości|`"pack://application:,,,/ContentFile.xaml"`|  
|Zawartość pliku w podfolderze|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|  
|Witryny pochodzenia pliku|`"pack://siteoforigin:,,,/SOOFile.xaml"`|  
|Witryny pochodzenia pliku w podfolderze|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|  
  
 Tabela 2 przedstawia różne pakiet względną [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] wskazanym w znaczniku.  
  
 Tabela 2: URI pakietu względne w znaczniku  
  
|Plik|Względne pakietu[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|Plik zasobów w zestawie lokalnego|`"/ResourceFile.xaml"`|  
|Plik zasobów w podfolderze zestawu lokalnego|`"/Subfolder/ResourceFile.xaml"`|  
|Plik zasobów w przywoływanego zestawu|`"/ReferencedAssembly;component/ResourceFile.xaml"`|  
|Plik zasobów w podfolderze przywoływanego zestawu|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|Plik zawartości|`"/ContentFile.xaml"`|  
|Zawartość pliku w podfolderze|`"/Subfolder/ContentFile.xaml"`|  
  
<a name="Using_Pack_URIs_in_Code"></a>   
### <a name="using-pack-uris-in-code"></a>Przy użyciu identyfikatorów URI pakietu w kodzie  
 Określ pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] w kodzie przez utworzenie wystąpienia <xref:System.Uri> klasy i przekazywanie pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jako parametr do konstruktora. Jest to zaprezentowane w poniższym przykładzie.  
  
```csharp  
Uri uri = new Uri("pack://application:,,,/File.xaml");  
```  
  
 Domyślnie <xref:System.Uri> klasy uwzględnia pakiet [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] być bezwzględny. W rezultacie zgłoszony wyjątek, gdy wystąpienie klasy <xref:System.Uri> klasy jest tworzony z pakietem względną [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
```csharp  
Uri uri = new Uri("/File.xaml");  
```  
  
 Na szczęście <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> przeciążenia z <xref:System.Uri> konstruktora klasy przyjmuje parametr typu <xref:System.UriKind> pozwala określić, czy pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jest bezwzględny lub względny.  
  
```csharp  
// Absolute URI (default)  
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);  
// Relative URI  
Uri relativeUri = new Uri("/File.xaml",   
                        UriKind.Relative);  
```  
  
 Należy określić tylko <xref:System.UriKind.Absolute> lub <xref:System.UriKind.Relative> gdy masz pewność, że podany pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jest jednego lub drugiego. Jeśli nie znasz typ pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] używany, np. gdy użytkownik wprowadza pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] w czasie wykonywania, użyj <xref:System.UriKind.RelativeOrAbsolute> zamiast tego.  
  
```csharp  
// Relative or Absolute URI provided by user via a text box  
TextBox userProvidedUriTextBox = new TextBox();  
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);  
```  
  
 Tabela 3 przedstawiono różne pakiet względną [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] określonego przez użytkownika w kodzie za pomocą <xref:System.Uri?displayProperty=nameWithType>.  
  
 Tabela 3: Bezwzględna pakietu URI w kodzie  
  
|Plik|Bezwzględna pakietu[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|Plik zasobów — zestawu lokalnego|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|  
|Plik zasobów w podfolderze - zestawu lokalnego|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|Plik zasobów - przywoływanego zestawu|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|  
|Plik zasobów w podfolderze przywoływanego zestawu|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|Plik zasobów w określonej wersji przywoływanego zestawu.|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|  
|Plik zawartości|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|  
|Zawartość pliku w podfolderze|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|  
|Witryny pochodzenia pliku|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|  
|Witryny pochodzenia pliku w podfolderze|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|  
  
 Tabela 4 przedstawiono różne pakiet względną [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] określonego przez użytkownika za pomocą kodu <xref:System.Uri?displayProperty=nameWithType>.  
  
 Tabela 4: URI pakietu względne w kodzie  
  
|Plik|Względne pakietu[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|Plik zasobów — zestawu lokalnego|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|  
|Plik zasobów w podfolderze - zestawu lokalnego|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|Plik zasobów - przywoływanego zestawu|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|  
|Plik zasobów w podfolderze - przywoływanego zestawu|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|Plik zawartości|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|  
|Zawartość pliku w podfolderze|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|  
  
<a name="Common_Pack_URI_Scenarios"></a>   
### <a name="common-pack-uri-scenarios"></a>Typowe scenariusze identyfikatora URI Pack  
 Poprzednich sekcjach ma opisano sposób tworzenia pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] do identyfikacji zasobu, zawartość i witryny pochodzenia plików. W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]tych konstrukcji używanych w różny sposób i w poniższych częściach omówiono kilka typowych użycia.  
  
<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>   
#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a>Określanie interfejsu użytkownika do wyświetlenia w momencie uruchamiania aplikacji  
 <xref:System.Windows.Application.StartupUri%2A>Określa pierwszy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aby pokazać, kiedy [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacja jest uruchamiana. Dla aplikacji autonomicznych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] może być oknem, jak pokazano w poniższym przykładzie.  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]  
  
 Aplikacje autonomiczne i [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] można również określić stronę jako początkowa interfejsu użytkownika, jak pokazano w poniższym przykładzie.  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]  
  
 Jeśli aplikacja to aplikacja autonomiczna, a strona jest określany za pomocą <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] otwiera <xref:System.Windows.Navigation.NavigationWindow> do hostowania strony. Aby uzyskać [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], strona jest wyświetlana w przeglądarce hosta.  
  
<a name="Navigating_to_a_Page"></a>   
#### <a name="navigating-to-a-page"></a>Przechodzenie do strony  
 Poniższy przykład pokazuje, jak można przejść do strony.  
  
 [!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]  
  
 Aby uzyskać więcej informacji na różne sposoby, aby przejść w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], zobacz [omówienie nawigacji](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
<a name="Specifying_a_Window_Icon"></a>   
#### <a name="specifying-a-window-icon"></a>Określanie ikonę okna  
 Poniższy przykład przedstawia sposób korzystania z identyfikatora URI, aby określić ikonę okna.  
  
 [!code-xaml[WindowIconSnippets#WindowIconSetXAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Window.Icon%2A>.  
  
<a name="Loading_Image__Audio__and_Video_Files"></a>   
#### <a name="loading-image-audio-and-video-files"></a>Ładowanie plików wideo, Audio i obrazów  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Umożliwia aplikacjom na korzystanie z różnych typów, z których wszystkie zidentyfikowane i załadowany z dodatkiem Service pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], jak pokazano w poniższych przykładach.  
  
 [!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]  
  
 [!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]  
  
 [!code-xaml[ImageSample#ImagePackURIContent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]  
  
 Aby uzyskać więcej informacji na temat pracy z zawartości nośnika, zobacz [grafiki i Multimedia](../../../../docs/framework/wpf/graphics-multimedia/index.md).  
  
<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>   
#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a>Ładowanie słownika zasobów z witryny pochodzenia  
 Słowniki zasobów (<xref:System.Windows.ResourceDictionary>) może służyć do obsługi motywów aplikacji. Jednym ze sposobów tworzenia i zarządzania nimi kompozycji jest utworzenie wielu motywów jako słowniki zasobów, które znajdują się w witrynie pochodzenia aplikacji. Dzięki temu kompozycje do dodania i zaktualizować konieczności ponownego kompilowania ani ponownego wdrażania aplikacji. Te słowniki zasobów mogą zostać zidentyfikowane i ładowane przy użyciu pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], które przedstawiono w poniższym przykładzie.  
  
 [!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]  
  
 Omówienie motywów w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], zobacz [stylami i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zasób w aplikacji WPF, zawartość i plików danych](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
