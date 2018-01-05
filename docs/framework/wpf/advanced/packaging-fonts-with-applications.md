---
title: Pakowanie czcionek z aplikacjami
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], packaging fonts with
- fonts [WPF], packaging with applications
- typography [WPF], packaging fonts with applications
- packaging fonts with applications [WPF]
ms.assetid: db15ee48-4d24-49f5-8b9d-a64460865286
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d3860aff69b0e4e7a3dc624898cc6b1daa0dd092
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="packaging-fonts-with-applications"></a>Pakowanie czcionek z aplikacjami
Ten temat zawiera przegląd zagadnień związanych z czcionkami pakietu z sieci [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji.  
  
> [!NOTE]
>  Podobnie jak w przypadku większości typów oprogramowania, pliki czcionki są licencjonowane, a nie sprzedawane. Licencje, które określają sposób używanie czcionek różnią się dostawcy dostawcy, ale ogólnie większość licencji, w tym dotyczących czcionek [!INCLUDE[TLA#tla_ms#initcap](../../../../includes/tlasharptla-mssharpinitcap-md.md)] dostarcza z aplikacjami i [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], nie zezwalaj na czcionki, które mają zostać osadzone w aplikacji lub w inny sposób Ponowna dystrybucja. W związku z tym jako deweloper, który odpowiedzialność za zapewnienie, że masz wymagane prawa dla żadnej czcionki, który osadzić w aplikacji lub w inny sposób Ponowna dystrybucja.  
  

  
<a name="introduction_to_packaging_fonts"></a>   
## <a name="introduction-to-packaging-fonts"></a>Wprowadzenie do tworzenia pakietów czcionek  
 Można łatwo spakować czcionki jako zasoby w sieci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, aby wyświetlić tekst interfejsu użytkownika i innych typów tekstu na podstawie zawartości. Czcionki mogą być oddzielony od lub osadzone w aplikacji zestawu plików. Można również utworzyć w bibliotece tylko do zasobów czcionki aplikacji może odwoływać się.  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]i [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] czcionki zawierać flagę typu fsType, wskazującą osadzanie licencjonowania czcionek praw czcionki. Jednak tego typu Flaga odwołuje się tylko do czcionki osadzone przechowywane w dokumencie — it nie odwołuje się do czcionki osadzone w aplikacji. Możesz pobrać osadzanie praw dla czcionki, tworząc czcionek <xref:System.Windows.Media.GlyphTypeface> obiektu i odwołanie się do jego <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> właściwości. Zapoznaj się z sekcją "OS i 2 oraz Windows metryki" [specyfikacji OpenType](http://www.microsoft.com/typography/otspec/os2.htm) Aby uzyskać więcej informacji na temat flagi fsType.  
  
 [Typography Microsoft](http://www.microsoft.com/typography/links/) witryna sieci Web zawiera informacje kontaktowe, które mogą pomóc w zlokalizować dostawcy określonej czcionki lub znaleźć dostawcy czcionki dla niestandardowych pracy.  
  
<a name="adding_fonts_as_content_items"></a>   
## <a name="adding-fonts-as-content-items"></a>Dodawanie czcionek jako elementy zawartości  
 Czcionki można dodać do aplikacji jako elementy zawartości projektu, które są oddzielne od plików zestawu aplikacji. Oznacza to, że elementy zawartości nie są osadzone jako zasoby w zestawie. W poniższym przykładzie plik projektu przedstawia sposób definiowania elementów zawartości.  
  
```xml  
<Project DefaultTargets="Build"  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Content Include="Peric.ttf" />  
    <Content Include="Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
 Aby upewnić się, że aplikacja może używać czcionek w czasie wykonywania, czcionki musi być dostępny w katalogu wdrożenia aplikacji. `<CopyToOutputDirectory>` Elementu w pliku projektu aplikacji pozwala czcionki mają być automatycznie kopiowane do katalogu wdrożenia aplikacji podczas procesu kompilacji. W poniższym przykładzie plik projektu przedstawia sposób kopiowania czcionki do katalogu wdrażania.  
  
```xml  
<ItemGroup>  
  <Content Include="Peric.ttf">  
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
  </Content>  
  <Content Include="Pericl.ttf">  
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
  </Content>  
</ItemGroup>  
```  
  
 Poniższy przykładowy kod przedstawia sposób odwołania czcionkę aplikacji jako element zawartości — przywoływany element zawartości musi być w tym samym katalogu co pliki zestawu aplikacji.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>   
## <a name="adding-fonts-as-resource-items"></a>Dodawanie czcionek jako elementy zasobów  
 Czcionki można dodać do aplikacji jako elementy zasobów projektu, które są osadzone w aplikacji zestawu plików. Przy użyciu osobnych podkatalogu dla zasobów pomaga organizować pliki projektu aplikacji. W poniższym przykładzie plik projektu przedstawia sposób definiowania czcionki jako elementy zasobów w oddzielnych podkatalogu.  
  
```xml  
<Project DefaultTargets="Build"  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Resource Include="resources\Peric.ttf" />  
    <Resource Include="resources\Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
> [!NOTE]
>  Po dodaniu czcionki jako zasoby do aplikacji, upewnij się, czy ustawienie `<Resource>` elementu, a nie `<EmbeddedResource>` elementu w pliku projektu aplikacji. `<EmbeddedResource>` Element dla akcji kompilacji nie jest obsługiwany.  
  
 W poniższym przykładzie znaczników pokazuje, jak odwołanie do zasobów czcionki aplikacji.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a>Odwołania do elementów zasobu czcionki z kodu  
 Aby można było odwoływać się do czcionki zasobu elementów z kodu, musisz podać odwołanie zasobów czcionki z dwóch części: base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]; i odwołania do lokalizacji czcionki. Te wartości są używane jako parametry <xref:System.Windows.Media.FontFamily.%23ctor%2A> metody. Poniższy przykład kodu pokazuje, jak odwołanie do zasobów czcionki aplikacji w podkatalogu projektu o nazwie `resources`.  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 Podstawowym [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] mogą obejmować podkatalogu aplikacji, gdzie znajduje się zasób czcionki. W takim przypadku nie będzie trzeba określić katalog odwołania do lokalizacji czcionki, ale musi zawierać na początku "`./`", które określa zasoby czcionki jest w tym samym katalogu, określony przez podstawę [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]. Poniższy przykład kodu pokazuje alternatywny sposób odwołania do elementu zasobów czcionki — jest to odpowiednik w poprzednim przykładzie kodu.  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a>Odwołanie do czcionki z tym samym podkatalogu aplikacji  
 Pliki można umieścić zarówno aplikacji zawartości i zasobów w tym samym podkatalogu użytkownika projektu aplikacji. W poniższym przykładzie plik projektu zawiera strony zawartości i zasoby czcionki zdefiniowane w tym samym podkatalogu.  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 Ponieważ zawartość aplikacji i czcionki znajdują się w tym samym podkatalogu, odwołanie czcionki jest określana względem zawartości aplikacji. Poniższe przykłady przedstawiają sposób odwołania zasobów czcionki aplikacji po czcionkę w tym samym katalogu co aplikacja.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a>Wyliczanie czcionek w aplikacji  
 Aby wyliczyć czcionki jako zasób w aplikacji, użyj <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> lub <xref:System.Windows.Media.Fonts.GetTypefaces%2A> metody. Poniższy przykład przedstawia użycie <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> metodę, aby zwrócić zbiór <xref:System.Windows.Media.FontFamily> obiektów z lokalizacji, czcionki w aplikacji. W takim przypadku aplikacja zawiera podkatalog o nazwie "resources".  
  
 [!code-csharp[FontSnippets#FontsSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 Poniższy przykład przedstawia użycie <xref:System.Windows.Media.Fonts.GetTypefaces%2A> metodę, aby zwrócić zbiór <xref:System.Windows.Media.Typeface> obiektów z lokalizacji, czcionki w aplikacji. W takim przypadku aplikacja zawiera podkatalog o nazwie "resources".  
  
 [!code-csharp[FontSnippets#FontsSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>   
## <a name="creating-a-font-resource-library"></a>Tworzenie biblioteki zasobów czcionki  
 Można utworzyć tylko zasobów biblioteki, która zawiera tylko czcionki — żaden kod nie jest częścią tego typu projektu biblioteki. Tworzenie biblioteki tylko do zasobu jest typowe technika oddzielenie zasobów z kodu aplikacji, który używa tych. Umożliwia to także zestaw biblioteki zostanie uwzględniona w wielu projektach aplikacji. W poniższym przykładzie plik projektu zawiera części klucza projektu biblioteki tylko do zasobów.  
  
```xml  
<PropertyGroup>  
  <AssemblyName>FontLibrary</AssemblyName>  
  <OutputType>library</OutputType>  
  ...  
</PropertyGroup>  
...  
<ItemGroup>  
  <Resource Include="Kooten.ttf" />  
  <Resource Include="Pesca.ttf" />  
</ItemGroup  
```  
  
### <a name="referencing-a-font-in-a-resource-library"></a>Odwołanie do czcionki w bibliotece zasobów  
 Aby odwołać czcionki w bibliotece zasobów z poziomu aplikacji, musi prefiks odwołanie czcionki o nazwie zestawu biblioteki. W takim przypadku zestaw zasobów czcionki jest "FontLibrary". Rozdziel nazwy zestawu z odwołania w zestawie, użyj znaku ";". Dodawanie — słowo kluczowe "Component" odwołanie do nazwy czcionki wykonuje pełne odwołanie do zasobu biblioteki czcionek. Poniższy przykład kodu pokazuje, jak ma dotyczyć odwołanie czcionki w zestawie biblioteki zasobów.  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
>  Ten zestaw SDK zawiera zestaw próbki [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionek, które można używać z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji. Czcionki są definiowane w bibliotece tylko do zasobów. Aby uzyskać więcej informacji, zobacz [przykładowym pakiecie czcionek OpenType](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md).  
  
<a name="limitations_on_font_usage"></a>   
## <a name="limitations-on-font-usage"></a>Ograniczenia dotyczące użycia czcionki  
 Poniższa lista zawiera kilka ograniczeń na tworzenie pakietów i używanie czcionek w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji:  
  
-   **Osadzanie bity uprawnienia czcionek:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie Sprawdź lub wymusić żadnej czcionki osadzanie bity uprawnienia aplikacji. Zobacz [czcionki Introduction_to_Packing](#introduction_to_packaging_fonts) sekcji, aby uzyskać więcej informacji.  
  
-   **Witryny pochodzenia czcionek:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje nie zezwalają na odwołanie czcionki do protokołu http lub ftp [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].  
  
-   **Bezwzględny identyfikator URI przy użyciu pakietu: notacji:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje nie pozwala na tworzenie <xref:System.Windows.Media.FontFamily> programowo przy użyciu "pakietu:" jako część bezwzględną [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] odwołanie do czcionki. Na przykład `"pack://application:,,,/resources/#Pericles Light"` jest odwołaniem nieprawidłową czcionkę.  
  
-   **Osadzanie czcionek automatycznego:** w czasie projektowania, nie jest obsługiwane podczas wyszukiwania użycia aplikacji czcionek i automatycznie osadzania czcionek w zasoby aplikacji.  
  
-   **Podzbiory czcionki:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje nie obsługują tworzenia podzbiorów czcionki dla niestałych dokumenty.  
  
-   W przypadkach, w przypadku nieprawidłowego odwołania, aplikacja przełączy się dostępna czcionka.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Documents.Typography>  
 <xref:System.Windows.Media.FontFamily>  
 [Typografii firmy Microsoft: Łączy, wiadomości i kontakty](http://www.microsoft.com/typography/links/)  
 [Specyfikacja OpenType](http://www.microsoft.com/typography/otspec/)  
 [Funkcje czcionki OpenType](../../../../docs/framework/wpf/advanced/opentype-font-features.md)  
 [Przykład pakietu czcionek OpenType](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)
