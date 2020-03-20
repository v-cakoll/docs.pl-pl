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
ms.openlocfilehash: cef2ae26ec4fccd25ca193ba7d441969f36b25a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187091"
---
# <a name="packaging-fonts-with-applications"></a>Pakowanie czcionek z aplikacjami
W tym temacie przedstawiono omówienie sposobu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pakowania czcionek z aplikacją.  
  
> [!NOTE]
> Podobnie jak w przypadku większości typów oprogramowania, pliki czcionek są licencjonowane, a nie sprzedawane. Licencje regulujące korzystanie z czcionek różnią się w zależności od dostawcy, ale ogólnie większość licencji, w tym tych obejmujących czcionki, które firma Microsoft dostarcza aplikacjom i systemowi Windows, nie zezwala na osadzanie czcionek w aplikacjach lub w inny sposób rozpowszechnianie. W związku z tym jako deweloper jest odpowiedzialny za zapewnienie, że masz wymagane prawa licencyjne dla każdej czcionki osadzasz w aplikacji lub w inny sposób redystrybuować.  

<a name="introduction_to_packaging_fonts"></a>
## <a name="introduction-to-packaging-fonts"></a>Wprowadzenie do czcionek opakowaniowych  
 Czcionki można łatwo spakować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jako zasoby w aplikacjach, aby wyświetlić tekst interfejsu użytkownika i inne typy zawartości tekstowej. Czcionki mogą być oddzielone od plików złożenia aplikacji lub osadzone w niej. Można również utworzyć bibliotekę czcionek tylko do zasobów, do której aplikacja może się odwoływać.  
  
 Czcionki OpenType i TrueType® zawierają flagę typu fsType, która wskazuje prawa do osadzania czcionek dla czcionki. Jednak ta flaga typu odnosi się tylko do czcionek osadzonych przechowywanych w dokumencie — nie odnosi się do czcionek osadzonych w aplikacji. Można pobrać prawa osadzania czcionki dla czcionki, tworząc <xref:System.Windows.Media.GlyphTypeface> <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> obiekt i odwołując się do jego właściwości. Więcej informacji na temat flagi fsType można znaleźć w sekcji "OS/2 i Metryki systemu Windows" [w specyfikacji OpenType.](https://www.microsoft.com/typography/otspec/os2.htm)  
  
 Witryna [microsoft typografia](https://docs.microsoft.com/typography/) w sieci Web zawiera informacje kontaktowe, które mogą pomóc w zlokalizowaniu określonego dostawcy czcionki lub znalezieniu dostawcy czcionek do pracy niestandardowej.  
  
<a name="adding_fonts_as_content_items"></a>
## <a name="adding-fonts-as-content-items"></a>Dodawanie czcionek jako elementów zawartości  
 Czcionki można dodawać do aplikacji jako elementy zawartości projektu, które są niezależne od plików zestawu aplikacji. Oznacza to, że elementy zawartości nie są osadzone jako zasoby w zestawie. W poniższym przykładzie pliku projektu pokazano, jak zdefiniować elementy zawartości.  
  
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
  
 Aby upewnić się, że aplikacja może używać czcionek w czasie wykonywania, czcionki muszą być dostępne w katalogu wdrażania aplikacji. Element `<CopyToOutputDirectory>` w pliku projektu aplikacji umożliwia automatyczne kopiowanie czcionek do katalogu wdrażania aplikacji podczas procesu kompilacji. W poniższym przykładzie pliku projektu pokazano, jak skopiować czcionki do katalogu wdrażania.  
  
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
  
 Poniższy przykład kodu pokazuje, jak odwoływać się do czcionki aplikacji jako elementu zawartości — element zawartości, do którego istnieje odwołanie, musi znajdować się w tym samym katalogu co pliki zestawu aplikacji.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>
## <a name="adding-fonts-as-resource-items"></a>Dodawanie czcionek jako elementów zasobów  
 Czcionki można dodawać do aplikacji jako elementy zasobów projektu, które są osadzone w plikach zestawu aplikacji. Użycie oddzielnego podkatalogu dla zasobów pomaga uporządkować pliki projektu aplikacji. W poniższym przykładzie pliku projektu pokazano, jak zdefiniować czcionki jako elementy zasobów w oddzielnym podkatalogu.  
  
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
> Podczas dodawania czcionek jako zasobów do aplikacji, `<Resource>` upewnij się, `<EmbeddedResource>` że są ustawienia elementu, a nie element w pliku projektu aplikacji. Element `<EmbeddedResource>` akcji kompilacji nie jest obsługiwany.  
  
 W poniższym przykładzie znaczników pokazano, jak odwoływać się do zasobów czcionek aplikacji.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a>Odwoływanie się do elementów zasobów czcionek z kodu  
 Aby odwoływać się do elementów zasobów czcionki z kodu, należy podać dwuczęściowe odwołanie do zasobu czcionki: podstawowy jednolity identyfikator zasobu (URI); i odwołanie do lokalizacji czcionki. Wartości te są używane jako <xref:System.Windows.Media.FontFamily.%23ctor%2A> parametry metody. Poniższy przykład kodu pokazuje, jak odwoływać się do zasobów `resources`czcionek aplikacji w podkatalogu projektu o nazwie .  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 Podstawowy jednolity identyfikator zasobu (URI) może zawierać podkatalog aplikacji, w którym znajduje się zasób czcionki. W takim przypadku odwołanie do lokalizacji czcionki nie musi określać katalogu,`./`ale musiałoby zawierać wiodący " ", który wskazuje, że zasób czcionki znajduje się w tym samym katalogu określonym przez podstawowy identyfikator jednolitego zasobu (URI). Poniższy przykład kodu pokazuje alternatywny sposób odwoływania się do elementu zasobu czcionki — jest odpowiednikiem poprzedniego przykładu kodu.  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a>Odwoływanie się do czcionek z tego samego podkatalogu aplikacji  
 Zawartość aplikacji i pliki zasobów można umieścić w tym samym podkatalogu zdefiniowanym przez użytkownika projektu aplikacji. W poniższym przykładzie pliku projektu przedstawiono stronę zawartości i zasoby czcionek zdefiniowane w tym samym podkatalogu.  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 Ponieważ zawartość aplikacji i czcionka znajdują się w tym samym podkatalogu, odwołanie do czcionki jest względem zawartości aplikacji. Poniższe przykłady pokazują, jak odwoływać się do zasobu czcionki aplikacji, gdy czcionka znajduje się w tym samym katalogu co aplikacja.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a>Wyliczanie czcionek w aplikacji  
 Aby wyliczyć czcionki jako elementy zasobów w <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> aplikacji, należy użyć metody lub. <xref:System.Windows.Media.Fonts.GetTypefaces%2A> W poniższym przykładzie <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> pokazano, jak użyć <xref:System.Windows.Media.FontFamily> metody do zwrócenia kolekcji obiektów z lokalizacji czcionki aplikacji. W takim przypadku aplikacja zawiera podkatalog o nazwie "zasoby".  
  
 [!code-csharp[FontSnippets#FontsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 W poniższym przykładzie <xref:System.Windows.Media.Fonts.GetTypefaces%2A> pokazano, jak użyć <xref:System.Windows.Media.Typeface> metody do zwrócenia kolekcji obiektów z lokalizacji czcionki aplikacji. W takim przypadku aplikacja zawiera podkatalog o nazwie "zasoby".  
  
 [!code-csharp[FontSnippets#FontsSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>
## <a name="creating-a-font-resource-library"></a>Tworzenie biblioteki zasobów czcionek  
 Można utworzyć bibliotekę tylko do zasobów, która zawiera tylko czcionki — żaden kod nie jest częścią tego typu projektu biblioteki. Tworzenie biblioteki tylko do zasobów jest powszechną techniką oddzielenia zasobów od kodu aplikacji, który ich używa. Umożliwia to również zestaw biblioteki, które mają być dołączone do wielu projektów aplikacji. W poniższym przykładzie pliku projektu przedstawiono kluczowe części projektu biblioteki tylko do zasobów.  
  
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
 Aby odwołać się do czcionki w bibliotece zasobów z aplikacji, należy prefiks odwołania czcionki z nazwą zestawu biblioteki. W takim przypadku zestaw zasobów czcionki jest "FontLibrary". Aby oddzielić nazwę zestawu od odwołania w zestawie, należy użyć znaku ';'. Dodanie słowa kluczowego "Składnik", po którym następuje odwołanie do nazwy czcionki, kończy pełne odniesienie do zasobu biblioteki czcionek. W poniższym przykładzie kodu pokazano, jak odwoływać się do czcionki w zestawie biblioteki zasobów.  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
> Ten zestaw SDK zawiera zestaw przykładowych czcionek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] OpenType, których można używać z aplikacjami. Czcionki są definiowane w bibliotece tylko do zasobów. Aby uzyskać więcej informacji, zobacz [Przykładowy pakiet czcionek OpenType](sample-opentype-font-pack.md).  
  
<a name="limitations_on_font_usage"></a>
## <a name="limitations-on-font-usage"></a>Ograniczenia dotyczące użycia czcionek  
 Na poniższej liście opisano kilka ograniczeń dotyczących [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pakowania i używania czcionek w aplikacjach:  
  
- **Bity uprawnień osadzania czcionek:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje nie sprawdzają ani nie wymuszają żadnych bitów uprawnień do osadzania czcionek. Aby uzyskać więcej informacji, zobacz sekcję [Introduction_to_Packing Czcionki.](#introduction_to_packaging_fonts)  
  
- **Czcionki witryny pochodzenia:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje nie zezwalają na odwoływanie się do czcionek do identyfikatora jednolitego zasobu http lub ftp (URI).  
  
- **Bezwzględny identyfikator URI przy użyciu pakietu: notacja:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje nie umożliwiają tworzenia <xref:System.Windows.Media.FontFamily> obiektu programowo przy użyciu "pack:" jako części bezwzględnego jednolitego identyfikatora zasobu (URI) odwołania do czcionki. Na przykład `"pack://application:,,,/resources/#Pericles Light"` jest nieprawidłowym odwołaniem do czcionki.  
  
- **Automatyczne osadzanie czcionek:** W czasie projektowania nie ma obsługi wyszukiwania aplikacji przy użyciu czcionek i automatycznego osadzania czcionek w zasobach aplikacji.  
  
- **Podzbiory czcionek:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje nie obsługują tworzenia podzbiorów czcionek dla dokumentów niezwiązanych.  
  
- W przypadkach, gdy istnieje niepoprawne odwołanie, aplikacja powraca do przy użyciu dostępnej czcionki.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- [Typografia firmy Microsoft: łącza, wiadomości i kontakty](https://docs.microsoft.com/typography/)
- [Specyfikacja OpenType](https://www.microsoft.com/typography/otspec/)
- [Funkcje czcionki OpenType](opentype-font-features.md)
- [Przykład pakietu czcionek OpenType](sample-opentype-font-pack.md)
