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
ms.openlocfilehash: b5ad2280c832b62e043a1f65f082d5475697c38c
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545357"
---
# <a name="packaging-fonts-with-applications"></a><span data-ttu-id="e9e3b-102">Pakowanie czcionek z aplikacjami</span><span class="sxs-lookup"><span data-stu-id="e9e3b-102">Packaging Fonts with Applications</span></span>
<span data-ttu-id="e9e3b-103">Ten temat zawiera omówienie sposobu tworzenia pakietów czcionek w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-103">This topic provides an overview of how to package fonts with your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9e3b-104">Podobnie jak w przypadku większości typów oprogramowania, pliki czcionek są licencjonowane, a nie sprzedawane.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-104">As with most types of software, font files are licensed, rather than sold.</span></span> <span data-ttu-id="e9e3b-105">Licencje, które regulują korzystanie z czcionek, różnią się od dostawcy do dostawcy, ale ogólnie w większości licencji, [!INCLUDE[TLA#tla_ms#initcap](../../../../includes/tlasharptla-mssharpinitcap-md.md)] w tym w odniesieniu do czcionek dostarczanych z aplikacjami i [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]nie zezwalają na Osadzanie czcionek w aplikacjach ani w inny sposób Ponowna dystrybucja.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-105">Licenses that govern the use of fonts vary from vendor to vendor but in general most licenses, including those covering the fonts [!INCLUDE[TLA#tla_ms#initcap](../../../../includes/tlasharptla-mssharpinitcap-md.md)] supplies with applications and [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], do not allow the fonts to be embedded within applications or otherwise redistributed.</span></span> <span data-ttu-id="e9e3b-106">W związku z tym deweloper jest odpowiedzialny za zapewnienie, że masz wymagane prawa do licencji dla dowolnej czcionki osadzonej w aplikacji lub w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-106">Therefore, as a developer it is your responsibility to ensure that you have the required license rights for any font you embed within an application or otherwise redistribute.</span></span>  

<a name="introduction_to_packaging_fonts"></a>   
## <a name="introduction-to-packaging-fonts"></a><span data-ttu-id="e9e3b-107">Wprowadzenie do tworzenia pakietów czcionek</span><span class="sxs-lookup"><span data-stu-id="e9e3b-107">Introduction to Packaging Fonts</span></span>  
 <span data-ttu-id="e9e3b-108">Możesz łatwo spakować czcionki jako zasoby w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacjach, aby wyświetlić tekst interfejsu użytkownika i inne typy zawartości na podstawie tekstu.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-108">You can easily package fonts as resources within your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications to display user interface text and other types of text based content.</span></span> <span data-ttu-id="e9e3b-109">Czcionki mogą być oddzielone od lub osadzone w plikach zestawu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-109">The fonts can be separate from or embedded within the application's assembly files.</span></span> <span data-ttu-id="e9e3b-110">Można również utworzyć bibliotekę czcionek tylko do zasobów, do której aplikacja może się odwoływać.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-110">You can also create a resource-only font library, which your application can reference.</span></span>  
  
 <span data-ttu-id="e9e3b-111">OpenType i [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] Fonts zawierają flagę typu fsType, która wskazuje prawa licencjonowania osadzania czcionek dla czcionki.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-111">OpenType and [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] fonts contain a type flag, fsType, that indicates font embedding licensing rights for the font.</span></span> <span data-ttu-id="e9e3b-112">Jednak ta flaga typu odnosi się tylko do czcionek osadzonych przechowywanych w dokumencie — nie odnosi się do czcionek osadzonych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-112">However, this type flag only refers to embedded fonts stored in a document–it does not refer to fonts embedded in an application.</span></span> <span data-ttu-id="e9e3b-113">Możesz pobrać prawa osadzania czcionek dla czcionki, tworząc <xref:System.Windows.Media.GlyphTypeface> obiekt i przywołując jego <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> właściwość.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-113">You can retrieve the font embedding rights for a font by creating a <xref:System.Windows.Media.GlyphTypeface> object and referencing its <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> property.</span></span> <span data-ttu-id="e9e3b-114">Zapoznaj się z sekcją "system operacyjny/2 i metryki systemu Windows" [specyfikacji OpenType](https://www.microsoft.com/typography/otspec/os2.htm) , aby uzyskać więcej informacji na temat flagi fsType.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-114">Refer to the "OS/2 and Windows Metrics" section of the [OpenType Specification](https://www.microsoft.com/typography/otspec/os2.htm) for more information on the fsType flag.</span></span>  
  
 <span data-ttu-id="e9e3b-115">Witryna sieci Web [Microsoft Typografia](https://docs.microsoft.com/typography/) zawiera informacje kontaktowe, które mogą pomóc w znalezieniu konkretnego dostawcy czcionki lub znalezieniu dostawcy czcionki dla pracy niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-115">The [Microsoft Typography](https://docs.microsoft.com/typography/) Web site includes contact information that can help you locate a particular font vendor or find a font vendor for custom work.</span></span>  
  
<a name="adding_fonts_as_content_items"></a>   
## <a name="adding-fonts-as-content-items"></a><span data-ttu-id="e9e3b-116">Dodawanie czcionek jako elementów zawartości</span><span class="sxs-lookup"><span data-stu-id="e9e3b-116">Adding Fonts as Content Items</span></span>  
 <span data-ttu-id="e9e3b-117">Możesz dodać czcionki do aplikacji jako elementy zawartości projektu, które są niezależne od plików zestawu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-117">You can add fonts to your application as project content items that are separate from the application's assembly files.</span></span> <span data-ttu-id="e9e3b-118">Oznacza to, że elementy zawartości nie są osadzone jako zasoby w ramach zestawu.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-118">This means that content items are not embedded as resources within an assembly.</span></span> <span data-ttu-id="e9e3b-119">Poniższy przykład pliku projektu przedstawia sposób definiowania elementów zawartości.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-119">The following project file example shows how to define content items.</span></span>  
  
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
  
 <span data-ttu-id="e9e3b-120">W celu zapewnienia, że aplikacja może używać czcionek w czasie wykonywania, czcionki muszą być dostępne w katalogu wdrożenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-120">In order to ensure that the application can use the fonts at run time, the fonts must be accessible in the application's deployment directory.</span></span> <span data-ttu-id="e9e3b-121">`<CopyToOutputDirectory>` Element w pliku projektu aplikacji pozwala automatycznie skopiować czcionki do katalogu wdrożenia aplikacji podczas procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-121">The `<CopyToOutputDirectory>` element in the application's project file allows you to automatically copy the fonts to the application deployment directory during the build process.</span></span> <span data-ttu-id="e9e3b-122">Poniższy przykład pliku projektu pokazuje, jak skopiować czcionki do katalogu wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-122">The following project file example shows how to copy fonts to the deployment directory.</span></span>  
  
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
  
 <span data-ttu-id="e9e3b-123">Poniższy przykład kodu pokazuje, jak odwołać się do czcionki aplikacji jako element zawartości — element zawartości, do którego istnieje odwołanie, musi znajdować się w tym samym katalogu, co pliki zestawu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-123">The following code example shows how to reference the application's font as a content item—the referenced content item must be in the same directory as the application's assembly files.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>   
## <a name="adding-fonts-as-resource-items"></a><span data-ttu-id="e9e3b-124">Dodawanie czcionek jako elementów zasobów</span><span class="sxs-lookup"><span data-stu-id="e9e3b-124">Adding Fonts as Resource Items</span></span>  
 <span data-ttu-id="e9e3b-125">Możesz dodać czcionki do aplikacji jako elementy zasobów projektu, które są osadzone w plikach zestawu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-125">You can add fonts to your application as project resource items that are embedded within the application's assembly files.</span></span> <span data-ttu-id="e9e3b-126">Użycie oddzielnego podkatalogu dla zasobów ułatwia organizowanie plików projektu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-126">Using a separate subdirectory for resources helps to organize the application's project files.</span></span> <span data-ttu-id="e9e3b-127">Poniższy przykład pliku projektu pokazuje, jak definiować czcionki jako elementy zasobów w osobnym podkatalogu.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-127">The following project file example shows how to define fonts as resource items in a separate subdirectory.</span></span>  
  
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
>  <span data-ttu-id="e9e3b-128">Gdy dodajesz czcionki jako zasoby do aplikacji, upewnij się, że ustawiasz `<Resource>` element, a `<EmbeddedResource>` nie element w pliku projektu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-128">When you add fonts as resources to your application, make sure you are setting the `<Resource>` element, and not the `<EmbeddedResource>` element in your application's project file.</span></span> <span data-ttu-id="e9e3b-129">`<EmbeddedResource>` Element dla akcji kompilacji nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-129">The `<EmbeddedResource>` element for the build action is not supported.</span></span>  
  
 <span data-ttu-id="e9e3b-130">Poniższy przykład znacznika pokazuje, jak odwoływać się do zasobów czcionki aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-130">The following markup example shows how to reference the application's font resources.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a><span data-ttu-id="e9e3b-131">Odwoływanie się do elementów zasobów czcionki z kodu</span><span class="sxs-lookup"><span data-stu-id="e9e3b-131">Referencing Font Resource Items from Code</span></span>  
 <span data-ttu-id="e9e3b-132">Aby odwoływać się do elementów zasobów czcionki z kodu, należy podać dwa częściowe odwołanie do zasobu czcionki: Base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]; i informacje o lokalizacji czcionki.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-132">In order to reference font resource items from code, you must supply a two-part font resource reference: the base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]; and the font location reference.</span></span> <span data-ttu-id="e9e3b-133">Te wartości są używane jako parametry dla <xref:System.Windows.Media.FontFamily.%23ctor%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-133">These values are used as the parameters for the <xref:System.Windows.Media.FontFamily.%23ctor%2A> method.</span></span> <span data-ttu-id="e9e3b-134">Poniższy przykład kodu pokazuje, jak odwoływać się do zasobów czcionki aplikacji w podkatalogu projektu o nazwie `resources`.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-134">The following code example shows how to reference the application's font resources in the project subdirectory called `resources`.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 <span data-ttu-id="e9e3b-135">Baza [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] może obejmować podkatalog aplikacji, w którym znajduje się zasób czcionki.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-135">The base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] can include the application subdirectory where the font resource resides.</span></span> <span data-ttu-id="e9e3b-136">W takim przypadku odwołanie do lokalizacji czcionki nie musi określać katalogu, ale musi zawierać wiodący znak "`./`", który wskazuje, że zasób czcionki znajduje się w tym samym katalogu określonym przez bazę. [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9e3b-136">In this case, the font location reference would not need to specify a directory, but would have to include a leading "`./`", which indicates the font resource is in the same directory specified by the base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span></span> <span data-ttu-id="e9e3b-137">Poniższy przykład kodu pokazuje alternatywny sposób odwoływania się do elementu zasobu czcionki — jest to odpowiednik poprzedniego przykładu kodu.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-137">The following code example shows an alternate way of referencing the font resource item—it is equivalent to the previous code example.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a><span data-ttu-id="e9e3b-138">Odwoływanie się do czcionek z tego samego podkatalogu aplikacji</span><span class="sxs-lookup"><span data-stu-id="e9e3b-138">Referencing Fonts from the Same Application Subdirectory</span></span>  
 <span data-ttu-id="e9e3b-139">Zawartość aplikacji i pliki zasobów można umieścić w tym samym podkatalogu zdefiniowanym przez użytkownika projektu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-139">You can place both application content and resource files within the same user-defined subdirectory of your application project.</span></span> <span data-ttu-id="e9e3b-140">Poniższy przykład pliku projektu przedstawia stronę zawartości i zasoby czcionek zdefiniowane w tym samym podkatalogu.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-140">The following project file example shows a content page and font resources defined in the same subdirectory.</span></span>  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 <span data-ttu-id="e9e3b-141">Ponieważ zawartość i czcionka aplikacji znajdują się w tym samym podkatalogu, odwołanie do czcionki jest powiązane z zawartością aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-141">Since the application content and font are in the same subdirectory, the font reference is relative to the application content.</span></span> <span data-ttu-id="e9e3b-142">W poniższych przykładach pokazano, jak odwoływać się do zasobu czcionki aplikacji, gdy czcionka znajduje się w tym samym katalogu, w którym znajduje się aplikacja.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-142">The following examples show how to reference the application's font resource when the font is in the same directory as the application.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a><span data-ttu-id="e9e3b-143">Wyliczanie czcionek w aplikacji</span><span class="sxs-lookup"><span data-stu-id="e9e3b-143">Enumerating Fonts in an Application</span></span>  
 <span data-ttu-id="e9e3b-144">Aby wyliczyć czcionki jako elementy zasobów w aplikacji, użyj <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> metody lub. <xref:System.Windows.Media.Fonts.GetTypefaces%2A></span><span class="sxs-lookup"><span data-stu-id="e9e3b-144">To enumerate fonts as resource items in your application, use either the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> or <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method.</span></span> <span data-ttu-id="e9e3b-145">Poniższy przykład pokazuje, <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> jak używać metody do zwracania <xref:System.Windows.Media.FontFamily> kolekcji obiektów z lokalizacji czcionki aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-145">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> method to return the collection of <xref:System.Windows.Media.FontFamily> objects from the application font location.</span></span> <span data-ttu-id="e9e3b-146">W takim przypadku aplikacja zawiera podkatalog o nazwie "Resources" (zasoby).</span><span class="sxs-lookup"><span data-stu-id="e9e3b-146">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 <span data-ttu-id="e9e3b-147">Poniższy przykład pokazuje, <xref:System.Windows.Media.Fonts.GetTypefaces%2A> jak używać metody do zwracania <xref:System.Windows.Media.Typeface> kolekcji obiektów z lokalizacji czcionki aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-147">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method to return the collection of <xref:System.Windows.Media.Typeface> objects from the application font location.</span></span> <span data-ttu-id="e9e3b-148">W takim przypadku aplikacja zawiera podkatalog o nazwie "Resources" (zasoby).</span><span class="sxs-lookup"><span data-stu-id="e9e3b-148">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>   
## <a name="creating-a-font-resource-library"></a><span data-ttu-id="e9e3b-149">Tworzenie biblioteki zasobów czcionek</span><span class="sxs-lookup"><span data-stu-id="e9e3b-149">Creating a Font Resource Library</span></span>  
 <span data-ttu-id="e9e3b-150">Można utworzyć bibliotekę tylko do zasobów, która zawiera tylko czcionki — żaden kod nie jest częścią tego typu projektu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-150">You can create a resource-only library that contains only fonts—no code is part of this type of library project.</span></span> <span data-ttu-id="e9e3b-151">Tworzenie biblioteki zawierającej tylko zasoby jest powszechną techniką oddzielania zasobów od kodu aplikacji, który z nich korzysta.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-151">Creating a resource-only library is a common technique for decoupling resources from the application code that uses them.</span></span> <span data-ttu-id="e9e3b-152">Pozwala to również na uwzględnienie zestawu biblioteki w wielu projektach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-152">This also allows the library assembly to be included with multiple application projects.</span></span> <span data-ttu-id="e9e3b-153">Poniższy przykład pliku projektu przedstawia kluczowe fragmenty projektu biblioteki zawierającej tylko zasoby.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-153">The following project file example shows the key portions of a resource-only library project.</span></span>  
  
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
  
### <a name="referencing-a-font-in-a-resource-library"></a><span data-ttu-id="e9e3b-154">Odwoływanie się do czcionki w bibliotece zasobów</span><span class="sxs-lookup"><span data-stu-id="e9e3b-154">Referencing a Font in a Resource Library</span></span>  
 <span data-ttu-id="e9e3b-155">Aby odwołać się do czcionki w bibliotece zasobów z aplikacji, należy prefiksować odwołanie do czcionki z nazwą zestawu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-155">To reference a font in a resource library from your application, you must prefix the font reference with the name of the library assembly.</span></span> <span data-ttu-id="e9e3b-156">W takim przypadku zestaw zasobów czcionki to "FontLibrary".</span><span class="sxs-lookup"><span data-stu-id="e9e3b-156">In this case, the font resource assembly is "FontLibrary".</span></span> <span data-ttu-id="e9e3b-157">Aby oddzielić nazwę zestawu od odwołania w zestawie, użyj znaku ";".</span><span class="sxs-lookup"><span data-stu-id="e9e3b-157">To separate the assembly name from the reference within the assembly, use a ';' character.</span></span> <span data-ttu-id="e9e3b-158">Dodanie słowa kluczowego "Component", po którym następuje odwołanie do nazwy czcionki, uzupełnia pełne odwołanie do zasobu biblioteki czcionek.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-158">Adding the "Component" keyword followed by the reference to the font name completes the full reference to the font library's resource.</span></span> <span data-ttu-id="e9e3b-159">Poniższy przykład kodu pokazuje, jak odwoływać się do czcionki w zestawie biblioteki zasobów.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-159">The following code example shows how to reference a font in a resource library assembly.</span></span>  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
>  <span data-ttu-id="e9e3b-160">Ten zestaw SDK zawiera zestaw przykładowych czcionek OpenType, których można używać z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-160">This SDK contains a set of sample OpenType fonts that you can use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span> <span data-ttu-id="e9e3b-161">Czcionki są zdefiniowane w bibliotece tylko do zasobów.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-161">The fonts are defined in a resource-only library.</span></span> <span data-ttu-id="e9e3b-162">Aby uzyskać więcej informacji, zobacz [przykładowy pakiet czcionek OpenType](sample-opentype-font-pack.md).</span><span class="sxs-lookup"><span data-stu-id="e9e3b-162">For more information, see [Sample OpenType Font Pack](sample-opentype-font-pack.md).</span></span>  
  
<a name="limitations_on_font_usage"></a>   
## <a name="limitations-on-font-usage"></a><span data-ttu-id="e9e3b-163">Ograniczenia dotyczące użycia czcionek</span><span class="sxs-lookup"><span data-stu-id="e9e3b-163">Limitations on Font Usage</span></span>  
 <span data-ttu-id="e9e3b-164">Na poniższej liście opisano niektóre ograniczenia dotyczące pakowania i używania czcionek w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacjach:</span><span class="sxs-lookup"><span data-stu-id="e9e3b-164">The following list describes several limitations on the packaging and use of fonts in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications:</span></span>  
  
- <span data-ttu-id="e9e3b-165">**Bity uprawnień osadzania czcionek:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje nie sprawdzają ani nie wymuszają żadnych bitów uprawnień osadzania czcionek.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-165">**Font embedding permission bits:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not check or enforce any font embedding permission bits.</span></span> <span data-ttu-id="e9e3b-166">Aby uzyskać więcej informacji, zobacz sekcję [Introduction_to_Packing Fonts (czcionki](#introduction_to_packaging_fonts) ).</span><span class="sxs-lookup"><span data-stu-id="e9e3b-166">See the [Introduction_to_Packing Fonts](#introduction_to_packaging_fonts) section for more information.</span></span>  
  
- <span data-ttu-id="e9e3b-167">**Witryna z czcionkami pochodzenia:** aplikacje nie zezwalają na odwołanie do czcionki do protokołu HTTP lub [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]FTP. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9e3b-167">**Site of origin fonts:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow a font reference to an http or ftp [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span></span>  
  
- <span data-ttu-id="e9e3b-168">**Bezwzględny identyfikator URI przy użyciu pakietu:** aplikacje nie umożliwiają programistycznego <xref:System.Windows.Media.FontFamily> tworzenia obiektu za pomocą "Pack:" jako części bezwzględnego [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] odwołania do czcionki. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9e3b-168">**Absolute URI using the pack: notation:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow you to create a <xref:System.Windows.Media.FontFamily> object programmatically using "pack:" as part of the absolute [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] reference to a font.</span></span> <span data-ttu-id="e9e3b-169">Na przykład `"pack://application:,,,/resources/#Pericles Light"` jest nieprawidłowym odwołaniem do czcionki.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-169">For example, `"pack://application:,,,/resources/#Pericles Light"` is an invalid font reference.</span></span>  
  
- <span data-ttu-id="e9e3b-170">**Automatyczne Osadzanie czcionek:** W czasie projektowania nie ma obsługi wyszukiwania czcionek używanych przez aplikację i automatycznego osadzania czcionek w zasobach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-170">**Automatic font embedding:** During design time, there is no support for searching an application's use of fonts and automatically embedding the fonts in the application's resources.</span></span>  
  
- <span data-ttu-id="e9e3b-171">**Podzestawy czcionek:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje nie obsługują tworzenia podzestawów czcionek dla nieustalonych dokumentów.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-171">**Font subsets:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not support the creation of font subsets for non-fixed documents.</span></span>  
  
- <span data-ttu-id="e9e3b-172">W przypadkach, gdy występuje nieprawidłowe odwołanie, aplikacja powraca do korzystania z dostępnej czcionki.</span><span class="sxs-lookup"><span data-stu-id="e9e3b-172">In cases where there is an incorrect reference, the application falls back to using an available font.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9e3b-173">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9e3b-173">See also</span></span>

- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- [<span data-ttu-id="e9e3b-174">Typografia firmy Microsoft: Linki, wiadomości i kontakty</span><span class="sxs-lookup"><span data-stu-id="e9e3b-174">Microsoft Typography: Links, News, and Contacts</span></span>](https://docs.microsoft.com/typography/)
- [<span data-ttu-id="e9e3b-175">Specyfikacja OpenType</span><span class="sxs-lookup"><span data-stu-id="e9e3b-175">OpenType Specification</span></span>](https://www.microsoft.com/typography/otspec/)
- [<span data-ttu-id="e9e3b-176">Funkcje czcionki OpenType</span><span class="sxs-lookup"><span data-stu-id="e9e3b-176">OpenType Font Features</span></span>](opentype-font-features.md)
- [<span data-ttu-id="e9e3b-177">Przykład pakietu czcionek OpenType</span><span class="sxs-lookup"><span data-stu-id="e9e3b-177">Sample OpenType Font Pack</span></span>](sample-opentype-font-pack.md)
