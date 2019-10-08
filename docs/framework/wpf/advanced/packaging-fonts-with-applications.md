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
ms.openlocfilehash: 18a8037b6b4433a4a83860eae205174f3036d6e8
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005014"
---
# <a name="packaging-fonts-with-applications"></a>Pakowanie czcionek z aplikacjami
Ten temat zawiera omówienie tworzenia pakietów czcionek z aplikacją [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
> [!NOTE]
> Podobnie jak w przypadku większości typów oprogramowania, pliki czcionek są licencjonowane, a nie sprzedawane. Licencje, które regulują korzystanie z czcionek, różnią się od dostawcy do dostawcy, ale ogólnie w większości licencji, łącznie z tymi, które obejmują czcionki firmy Microsoft w aplikacjach i Windows, nie umożliwiają osadzania czcionek w aplikacjach ani redystrybucji. W związku z tym deweloper jest odpowiedzialny za zapewnienie, że masz wymagane prawa do licencji dla dowolnej czcionki osadzonej w aplikacji lub w inny sposób.  

<a name="introduction_to_packaging_fonts"></a>   
## <a name="introduction-to-packaging-fonts"></a>Wprowadzenie do tworzenia pakietów czcionek  
 Możesz łatwo spakować czcionki jako zasoby w aplikacjach [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], aby wyświetlić tekst interfejsu użytkownika i inne typy zawartości na podstawie tekstu. Czcionki mogą być oddzielone od lub osadzone w plikach zestawu aplikacji. Można również utworzyć bibliotekę czcionek tylko do zasobów, do której aplikacja może się odwoływać.  
  
 Czcionki OpenType i® TrueType zawierają flagę typu fsType, która wskazuje prawa licencjonowania osadzania czcionek dla czcionki. Jednak ta flaga typu odnosi się tylko do czcionek osadzonych przechowywanych w dokumencie — nie odnosi się do czcionek osadzonych w aplikacji. Możesz pobrać prawa osadzania czcionek dla czcionki, tworząc obiekt <xref:System.Windows.Media.GlyphTypeface> i przywołując Właściwość <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A>. Zapoznaj się z sekcją "system operacyjny/2 i metryki systemu Windows" [specyfikacji OpenType](https://www.microsoft.com/typography/otspec/os2.htm) , aby uzyskać więcej informacji na temat flagi fsType.  
  
 Witryna sieci Web [Microsoft Typografia](https://docs.microsoft.com/typography/) zawiera informacje kontaktowe, które mogą pomóc w znalezieniu konkretnego dostawcy czcionki lub znalezieniu dostawcy czcionki dla pracy niestandardowej.  
  
<a name="adding_fonts_as_content_items"></a>   
## <a name="adding-fonts-as-content-items"></a>Dodawanie czcionek jako elementów zawartości  
 Możesz dodać czcionki do aplikacji jako elementy zawartości projektu, które są niezależne od plików zestawu aplikacji. Oznacza to, że elementy zawartości nie są osadzone jako zasoby w ramach zestawu. Poniższy przykład pliku projektu przedstawia sposób definiowania elementów zawartości.  
  
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
  
 W celu zapewnienia, że aplikacja może używać czcionek w czasie wykonywania, czcionki muszą być dostępne w katalogu wdrożenia aplikacji. Element `<CopyToOutputDirectory>` w pliku projektu aplikacji pozwala automatycznie skopiować czcionki do katalogu wdrożenia aplikacji podczas procesu kompilacji. Poniższy przykład pliku projektu pokazuje, jak skopiować czcionki do katalogu wdrożenia.  
  
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
  
 Poniższy przykład kodu pokazuje, jak odwołać się do czcionki aplikacji jako element zawartości — element zawartości, do którego istnieje odwołanie, musi znajdować się w tym samym katalogu, co pliki zestawu aplikacji.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>   
## <a name="adding-fonts-as-resource-items"></a>Dodawanie czcionek jako elementów zasobów  
 Możesz dodać czcionki do aplikacji jako elementy zasobów projektu, które są osadzone w plikach zestawu aplikacji. Użycie oddzielnego podkatalogu dla zasobów ułatwia organizowanie plików projektu aplikacji. Poniższy przykład pliku projektu pokazuje, jak definiować czcionki jako elementy zasobów w osobnym podkatalogu.  
  
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
> Gdy dodajesz czcionki jako zasoby do aplikacji, upewnij się, że ustawiasz element `<Resource>`, a nie element `<EmbeddedResource>` w pliku projektu aplikacji. Element `<EmbeddedResource>` dla akcji kompilacji nie jest obsługiwany.  
  
 Poniższy przykład znacznika pokazuje, jak odwoływać się do zasobów czcionki aplikacji.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a>Odwoływanie się do elementów zasobów czcionki z kodu  
 Aby można było odwoływać się do elementów zasobów czcionki z kodu, należy podać dwa częściowe odwołanie do zasobu czcionki: Base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]; i informacje o lokalizacji czcionki. Te wartości są używane jako parametry metody <xref:System.Windows.Media.FontFamily.%23ctor%2A>. Poniższy przykład kodu pokazuje, jak odwoływać się do zasobów czcionki aplikacji w podkatalogu projektu o nazwie `resources`.  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 Podstawowy [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] może zawierać podkatalog aplikacji, w którym znajduje się zasób czcionki. W takim przypadku odwołanie do lokalizacji czcionki nie musi określać katalogu, ale musi zawierać wiodącą "`./`", co oznacza, że zasób czcionki znajduje się w tym samym katalogu określonym przez @no__t podstawowy-1. Poniższy przykład kodu pokazuje alternatywny sposób odwoływania się do elementu zasobu czcionki — jest to odpowiednik poprzedniego przykładu kodu.  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a>Odwoływanie się do czcionek z tego samego podkatalogu aplikacji  
 Zawartość aplikacji i pliki zasobów można umieścić w tym samym podkatalogu zdefiniowanym przez użytkownika projektu aplikacji. Poniższy przykład pliku projektu przedstawia stronę zawartości i zasoby czcionek zdefiniowane w tym samym podkatalogu.  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 Ponieważ zawartość i czcionka aplikacji znajdują się w tym samym podkatalogu, odwołanie do czcionki jest powiązane z zawartością aplikacji. W poniższych przykładach pokazano, jak odwoływać się do zasobu czcionki aplikacji, gdy czcionka znajduje się w tym samym katalogu, w którym znajduje się aplikacja.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a>Wyliczanie czcionek w aplikacji  
 Aby wyliczyć czcionki jako elementy zasobów w aplikacji, należy użyć metody <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> lub <xref:System.Windows.Media.Fonts.GetTypefaces%2A>. Poniższy przykład pokazuje, jak używać metody <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> w celu zwrócenia kolekcji obiektów <xref:System.Windows.Media.FontFamily> z lokalizacji czcionki aplikacji. W takim przypadku aplikacja zawiera podkatalog o nazwie "Resources" (zasoby).  
  
 [!code-csharp[FontSnippets#FontsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 Poniższy przykład pokazuje, jak używać metody <xref:System.Windows.Media.Fonts.GetTypefaces%2A> w celu zwrócenia kolekcji obiektów <xref:System.Windows.Media.Typeface> z lokalizacji czcionki aplikacji. W takim przypadku aplikacja zawiera podkatalog o nazwie "Resources" (zasoby).  
  
 [!code-csharp[FontSnippets#FontsSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>   
## <a name="creating-a-font-resource-library"></a>Tworzenie biblioteki zasobów czcionek  
 Można utworzyć bibliotekę tylko do zasobów, która zawiera tylko czcionki — żaden kod nie jest częścią tego typu projektu biblioteki. Tworzenie biblioteki zawierającej tylko zasoby jest powszechną techniką oddzielania zasobów od kodu aplikacji, który z nich korzysta. Pozwala to również na uwzględnienie zestawu biblioteki w wielu projektach aplikacji. Poniższy przykład pliku projektu przedstawia kluczowe fragmenty projektu biblioteki zawierającej tylko zasoby.  
  
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
 Aby odwołać się do czcionki w bibliotece zasobów z aplikacji, należy prefiksować odwołanie do czcionki z nazwą zestawu biblioteki. W takim przypadku zestaw zasobów czcionki to "FontLibrary". Aby oddzielić nazwę zestawu od odwołania w zestawie, użyj znaku ";". Dodanie słowa kluczowego "Component", po którym następuje odwołanie do nazwy czcionki, uzupełnia pełne odwołanie do zasobu biblioteki czcionek. Poniższy przykład kodu pokazuje, jak odwoływać się do czcionki w zestawie biblioteki zasobów.  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
> Ten zestaw SDK zawiera zestaw przykładowych czcionek OpenType, których można używać z aplikacjami [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Czcionki są zdefiniowane w bibliotece tylko do zasobów. Aby uzyskać więcej informacji, zobacz [przykładowy pakiet czcionek OpenType](sample-opentype-font-pack.md).  
  
<a name="limitations_on_font_usage"></a>   
## <a name="limitations-on-font-usage"></a>Ograniczenia dotyczące użycia czcionek  
 Na poniższej liście opisano niektóre ograniczenia dotyczące pakowania i używania czcionek w aplikacjach [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
- **Bity uprawnień osadzania czcionek:** aplikacje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie sprawdzają ani nie wymuszają żadnych bitów uprawnień osadzania czcionek. Aby uzyskać więcej informacji, zobacz sekcję [Introduction_to_Packing Fonts (czcionki](#introduction_to_packaging_fonts) ).  
  
- **Lokacja czcionek pochodzenia:** aplikacje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie zezwalają na odwołanie do czcionki w przypadku protokołu HTTP lub FTP [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].  
  
- **Bezwzględny identyfikator URI przy użyciu pakietu: w przypadku** aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie można utworzyć obiektu <xref:System.Windows.Media.FontFamily> programowo przy użyciu "Pack:" jako części bezwzględnego odwołania [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] do czcionki. Na przykład `"pack://application:,,,/resources/#Pericles Light"` jest nieprawidłowym odwołaniem do czcionki.  
  
- **Automatyczne Osadzanie czcionek:** W czasie projektowania nie ma obsługi wyszukiwania czcionek używanych przez aplikację i automatycznego osadzania czcionek w zasobach aplikacji.  
  
- **Podzestawy czcionek:** aplikacje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie obsługują tworzenia podzestawów czcionek dla nieustalonych dokumentów.  
  
- W przypadkach, gdy występuje nieprawidłowe odwołanie, aplikacja powraca do korzystania z dostępnej czcionki.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- [Typografia firmy Microsoft: linki, wiadomości i kontakty](https://docs.microsoft.com/typography/)
- [Specyfikacja OpenType](https://www.microsoft.com/typography/otspec/)
- [Funkcje czcionki OpenType](opentype-font-features.md)
- [Przykład pakietu czcionek OpenType](sample-opentype-font-pack.md)
