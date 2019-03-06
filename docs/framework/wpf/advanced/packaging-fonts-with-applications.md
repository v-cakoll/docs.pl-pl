---
title: Pakowanie czcionek z aplikacjami
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], packaging fonts with
- fonts [WPF], packaging with applications
- typography [WPF], packaging fonts with applications
- packaging fonts with applications [WPF]
ms.assetid: db15ee48-4d24-49f5-8b9d-a64460865286
ms.openlocfilehash: e66841fe72281bf0562b2ce50925a5c3a6bb9b54
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378880"
---
# <a name="packaging-fonts-with-applications"></a>Pakowanie czcionek z aplikacjami
Ten temat zawiera omówienie sposobów z czcionkami pakietu przy użyciu usługi [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji.  
  
> [!NOTE]
>  Podobnie jak w przypadku większości typów oprogramowania, pliki czcionek są licencjonowane, a nie sprzedawana. Licencje, określające sposób użytkowania czcionki różnią się w dostawcy dostawcy, ale ogólnie większość licencji, w tym dotyczących czcionek [!INCLUDE[TLA#tla_ms#initcap](../../../../includes/tlasharptla-mssharpinitcap-md.md)] dostarcza z aplikacjami i [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], nie zezwalają na czcionki, aby być osadzony w aplikacji lub w inny sposób Ponowna dystrybucja. W związku z tym jak Deweloper, który jest odpowiedzialny za zapewnienie, że masz prawa wymaganą licencję dla dowolnego czcionki, którą można osadzić w aplikacji lub w inny sposób Ponowna dystrybucja.  
  

  
<a name="introduction_to_packaging_fonts"></a>   
## <a name="introduction-to-packaging-fonts"></a>Wprowadzenie do pakowanie czcionek  
 Można łatwo spakować czcionki jako zasoby w ramach Twojej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, aby wyświetlić tekst interfejsu użytkownika i innych rodzajów tekst na podstawie zawartości. Czcionki może być niezależnie od lub osadzonego w ramach plików zestawu aplikacji. Można również utworzyć w bibliotece tylko do zasobów czcionki mogą odwoływać się do aplikacji.  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] i [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] czcionki zawiera flagę typu fsType, wskazującą czcionki osadzania Licencjonowanie prawa do czcionki. Jednak tego typu, Flaga odwołuje się tylko do osadzonych czcionek, przechowywane w dokumencie — it nie odwołuje się czcionki osadzone w aplikacji. Możesz pobrać osadzanie praw do czcionki, tworząc czcionek <xref:System.Windows.Media.GlyphTypeface> obiektu i odwołanie się do jego <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> właściwości. Zapoznaj się z sekcją "system operacyjny/2 i Windows metryki" [specyfikacji OpenType](https://www.microsoft.com/typography/otspec/os2.htm) więcej informacji na temat flagi fsType.  
  
 [Typography Microsoft](https://docs.microsoft.com/typography/) witryny sieci Web zawiera informacje kontaktowe, które mogą pomóc w zlokalizować dostawcy określonej czcionki lub Znajdź dostawcę czcionki niestandardowe pracy.  
  
<a name="adding_fonts_as_content_items"></a>   
## <a name="adding-fonts-as-content-items"></a>Dodawanie czcionki jako elementy zawartości  
 Możesz dodać czcionki do aplikacji jako elementy zawartości projektu, które są niezależne od plików zestawu aplikacji. Oznacza to, że elementy zawartości nie są osadzane jako zasoby w zestawie. W poniższym przykładzie plik projektu pokazuje jak zdefiniować elementy zawartości.  
  
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
  
 Aby zapewnić, że aplikacja może używać czcionek w czasie wykonywania, czcionki musi być dostępny w katalogu wdrożenia aplikacji. `<CopyToOutputDirectory>` Elementu w pliku projektu aplikacji pozwala automatycznie skopiować je do katalogu wdrożenia aplikacji podczas procesu kompilacji. W poniższym przykładzie plik projektu pokazano, jak można skopiować czcionki do katalogu wdrażania.  
  
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
  
 Poniższy przykład kodu pokazuje, jak odwoływać się do aplikacji czcionki jako element zawartości — przywoływany element zawartości musi być w tym samym katalogu co pliki zestawu aplikacji.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>   
## <a name="adding-fonts-as-resource-items"></a>Dodawanie czcionki jako element zasobu  
 Możesz dodać czcionki do aplikacji jako elementy zasobów projektu, które są osadzone w ramach plików zestawu aplikacji. Przy użyciu oddzielnych podkatalogu dla zasobów pomaga organizować pliki projektu aplikacji. W poniższym przykładzie plik projektu pokazuje jak zdefiniować czcionki jako zasób w oddzielnym podkatalogu.  
  
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
  
 W poniższym przykładzie znaczników pokazano, jak odwołanie do zasobów czcionki w aplikacji.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a>Odwoływanie się do elementów zasobu czcionek z kodu  
 Aby można było odwoływać się do elementów zasobu czcionek z kodu, należy podać odwołanie do zasobu legalną dwuczęściową czcionki: Podstawa [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]; i odwołanie do lokalizacji czcionki. Te wartości są używane jako parametry <xref:System.Windows.Media.FontFamily.%23ctor%2A> metody. Poniższy przykład kodu pokazuje, jak odwoływać się do aplikacji czcionki zasobów w podkatalogu projektu o nazwie `resources`.  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 Podstawa [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] mogą obejmować podkatalogu aplikacji, w którym znajduje się zasób czcionki. W tym przypadku nie będzie trzeba określić katalog czcionek odwołanie do lokalizacji, ale musi zawierać znaku "`./`", które określa zasoby czcionki znajduje się w tym samym katalogu, określony przez podstawę [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]. Poniższy przykład kodu pokazuje alternatywny sposób odwołuje się do elementu zasobu czcionek — jest to równoważne w poprzednim przykładzie kodu.  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a>Odwoływanie się do czcionki z tym samym podkatalogu aplikacji  
 Pliki można umieścić zarówno aplikacji zawartości i zasobów w ramach tego samego użytkownika podkatalogu projektu aplikacji. W poniższym przykładzie plik projektu zawiera strony zawartości i zasobów czcionki, zdefiniowane w tym samym podkatalogu.  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 Ponieważ zawartość aplikacji i czcionki znajdują się w tym samym podkatalogu, odwołanie czcionka jest względem zawartości aplikacji. Poniższe przykłady pokazują jak odwoływać się do zasobu czcionek aplikacji po czcionkę w tym samym katalogu co aplikacja.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a>Wyliczanie czcionek w aplikacji  
 Aby wyliczyć czcionki jako zasób w aplikacji, należy użyć <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> lub <xref:System.Windows.Media.Fonts.GetTypefaces%2A> metody. Poniższy przykład pokazuje, jak używać <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> metodę, aby zwrócić zbiór <xref:System.Windows.Media.FontFamily> obiektów z lokalizacji czcionki w aplikacji. W takim przypadku aplikacja zawiera podkatalog o nazwie "zasoby".  
  
 [!code-csharp[FontSnippets#FontsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 Poniższy przykład pokazuje, jak używać <xref:System.Windows.Media.Fonts.GetTypefaces%2A> metodę, aby zwrócić zbiór <xref:System.Windows.Media.Typeface> obiektów z lokalizacji czcionki w aplikacji. W takim przypadku aplikacja zawiera podkatalog o nazwie "zasoby".  
  
 [!code-csharp[FontSnippets#FontsSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>   
## <a name="creating-a-font-resource-library"></a>Tworzenie biblioteki zasobów czcionki  
 Można utworzyć bibliotekę tylko do zasobów, która zawiera tylko czcionki — żaden kod nie jest częścią tego typu projektu biblioteki. Tworzenie biblioteki tylko do zasobów jest typową techniką dla oddzielenie zasobów z kodu aplikacji, który używa tych. Dzięki temu również zestawu biblioteki do uwzględnienia w wielu projektach aplikacji. W poniższym przykładzie plik projektu zawiera kluczowych części projektu biblioteki tylko do zasobów.  
  
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
  
### <a name="referencing-a-font-in-a-resource-library"></a>Odwoływanie się do czcionki w bibliotece zasobów  
 Aby odwołać czcionki w bibliotece zasobów z aplikacji, musi prefiks odwołanie czcionki o nazwie zestawu biblioteki. W tym przypadku zestaw zasobów czcionki jest "FontLibrary". Aby rozdzielić nazwy zestawu z odwołania w zestawie, użyj znaku ";". Dodawanie słowa kluczowego "Component" odwołanie do nazwy czcionki kończy pełny odwołanie do zasobu biblioteki czcionki. Poniższy przykład kodu pokazuje jak odwoływać się do czcionki w zestawie zasobów biblioteki.  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
>  Ten zestaw SDK zawiera zestaw przykładowych [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionek, które można używać z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji. Czcionki są zdefiniowane w bibliotece tylko do zasobów. Aby uzyskać więcej informacji, zobacz [przykład pakietu czcionek OpenType](sample-opentype-font-pack.md).  
  
<a name="limitations_on_font_usage"></a>   
## <a name="limitations-on-font-usage"></a>Ograniczenia dotyczące użycia czcionki  
 Na poniższej liście opisano również kilka ograniczeń na tworzenie pakietów i używanie czcionek w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji:  
  
-   **Osadzanie bity uprawnień czcionek:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji sprawdź lub nie wymuszają żadnych osadzanie bity uprawnień czcionek. Zobacz [czcionki Introduction_to_Packing](#introduction_to_packaging_fonts) sekcji, aby uzyskać więcej informacji.  
  
-   **Witryna pochodzenia czcionki:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje nie zezwalają na odwołanie czcionki do protokołu http lub ftp [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].  
  
-   **Bezwzględny identyfikator URI przy użyciu pakietu: notacji:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje nie pozwalają na tworzenie <xref:System.Windows.Media.FontFamily> programowo przy użyciu "pakietu:" jako część bezwzględną [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] odwołań do czcionki. Na przykład `"pack://application:,,,/resources/#Pericles Light"` jest odwołaniem nieprawidłowa czcionka.  
  
-   **Osadzanie czcionki automatyczne:** W czasie projektowania nie jest obsługiwane podczas wyszukiwania aplikacji używanie czcionek i automatycznie osadzania czcionek w aplikacji zasobów.  
  
-   **Czcionka podzbiory:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje nie obsługują tworzenia podzestawy czcionki-fixed dokumentów.  
  
-   W przypadkach, w przypadku nieprawidłowego odwołania, aplikacja powróci przy użyciu dostępnej czcionki.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- [Typografia firmy Microsoft: Łączy, wiadomości i kontakty](https://docs.microsoft.com/typography/)
- [Specyfikacja OpenType](https://www.microsoft.com/typography/otspec/)
- [Funkcje czcionki OpenType](opentype-font-features.md)
- [Przykład pakietu czcionek OpenType](sample-opentype-font-pack.md)
