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
# <a name="packaging-fonts-with-applications"></a><span data-ttu-id="f9a86-102">Pakowanie czcionek z aplikacjami</span><span class="sxs-lookup"><span data-stu-id="f9a86-102">Packaging Fonts with Applications</span></span>
<span data-ttu-id="f9a86-103">Ten temat zawiera omówienie sposobów z czcionkami pakietu przy użyciu usługi [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9a86-103">This topic provides an overview of how to package fonts with your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f9a86-104">Podobnie jak w przypadku większości typów oprogramowania, pliki czcionek są licencjonowane, a nie sprzedawana.</span><span class="sxs-lookup"><span data-stu-id="f9a86-104">As with most types of software, font files are licensed, rather than sold.</span></span> <span data-ttu-id="f9a86-105">Licencje, określające sposób użytkowania czcionki różnią się w dostawcy dostawcy, ale ogólnie większość licencji, w tym dotyczących czcionek [!INCLUDE[TLA#tla_ms#initcap](../../../../includes/tlasharptla-mssharpinitcap-md.md)] dostarcza z aplikacjami i [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], nie zezwalają na czcionki, aby być osadzony w aplikacji lub w inny sposób Ponowna dystrybucja.</span><span class="sxs-lookup"><span data-stu-id="f9a86-105">Licenses that govern the use of fonts vary from vendor to vendor but in general most licenses, including those covering the fonts [!INCLUDE[TLA#tla_ms#initcap](../../../../includes/tlasharptla-mssharpinitcap-md.md)] supplies with applications and [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], do not allow the fonts to be embedded within applications or otherwise redistributed.</span></span> <span data-ttu-id="f9a86-106">W związku z tym jak Deweloper, który jest odpowiedzialny za zapewnienie, że masz prawa wymaganą licencję dla dowolnego czcionki, którą można osadzić w aplikacji lub w inny sposób Ponowna dystrybucja.</span><span class="sxs-lookup"><span data-stu-id="f9a86-106">Therefore, as a developer it is your responsibility to ensure that you have the required license rights for any font you embed within an application or otherwise redistribute.</span></span>  
  

  
<a name="introduction_to_packaging_fonts"></a>   
## <a name="introduction-to-packaging-fonts"></a><span data-ttu-id="f9a86-107">Wprowadzenie do pakowanie czcionek</span><span class="sxs-lookup"><span data-stu-id="f9a86-107">Introduction to Packaging Fonts</span></span>  
 <span data-ttu-id="f9a86-108">Można łatwo spakować czcionki jako zasoby w ramach Twojej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, aby wyświetlić tekst interfejsu użytkownika i innych rodzajów tekst na podstawie zawartości.</span><span class="sxs-lookup"><span data-stu-id="f9a86-108">You can easily package fonts as resources within your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications to display user interface text and other types of text based content.</span></span> <span data-ttu-id="f9a86-109">Czcionki może być niezależnie od lub osadzonego w ramach plików zestawu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9a86-109">The fonts can be separate from or embedded within the application's assembly files.</span></span> <span data-ttu-id="f9a86-110">Można również utworzyć w bibliotece tylko do zasobów czcionki mogą odwoływać się do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9a86-110">You can also create a resource-only font library, which your application can reference.</span></span>  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] <span data-ttu-id="f9a86-111">i [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] czcionki zawiera flagę typu fsType, wskazującą czcionki osadzania Licencjonowanie prawa do czcionki.</span><span class="sxs-lookup"><span data-stu-id="f9a86-111">and [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] fonts contain a type flag, fsType, that indicates font embedding licensing rights for the font.</span></span> <span data-ttu-id="f9a86-112">Jednak tego typu, Flaga odwołuje się tylko do osadzonych czcionek, przechowywane w dokumencie — it nie odwołuje się czcionki osadzone w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9a86-112">However, this type flag only refers to embedded fonts stored in a document–it does not refer to fonts embedded in an application.</span></span> <span data-ttu-id="f9a86-113">Możesz pobrać osadzanie praw do czcionki, tworząc czcionek <xref:System.Windows.Media.GlyphTypeface> obiektu i odwołanie się do jego <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f9a86-113">You can retrieve the font embedding rights for a font by creating a <xref:System.Windows.Media.GlyphTypeface> object and referencing its <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> property.</span></span> <span data-ttu-id="f9a86-114">Zapoznaj się z sekcją "system operacyjny/2 i Windows metryki" [specyfikacji OpenType](https://www.microsoft.com/typography/otspec/os2.htm) więcej informacji na temat flagi fsType.</span><span class="sxs-lookup"><span data-stu-id="f9a86-114">Refer to the "OS/2 and Windows Metrics" section of the [OpenType Specification](https://www.microsoft.com/typography/otspec/os2.htm) for more information on the fsType flag.</span></span>  
  
 <span data-ttu-id="f9a86-115">[Typography Microsoft](https://docs.microsoft.com/typography/) witryny sieci Web zawiera informacje kontaktowe, które mogą pomóc w zlokalizować dostawcy określonej czcionki lub Znajdź dostawcę czcionki niestandardowe pracy.</span><span class="sxs-lookup"><span data-stu-id="f9a86-115">The [Microsoft Typography](https://docs.microsoft.com/typography/) Web site includes contact information that can help you locate a particular font vendor or find a font vendor for custom work.</span></span>  
  
<a name="adding_fonts_as_content_items"></a>   
## <a name="adding-fonts-as-content-items"></a><span data-ttu-id="f9a86-116">Dodawanie czcionki jako elementy zawartości</span><span class="sxs-lookup"><span data-stu-id="f9a86-116">Adding Fonts as Content Items</span></span>  
 <span data-ttu-id="f9a86-117">Możesz dodać czcionki do aplikacji jako elementy zawartości projektu, które są niezależne od plików zestawu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9a86-117">You can add fonts to your application as project content items that are separate from the application's assembly files.</span></span> <span data-ttu-id="f9a86-118">Oznacza to, że elementy zawartości nie są osadzane jako zasoby w zestawie.</span><span class="sxs-lookup"><span data-stu-id="f9a86-118">This means that content items are not embedded as resources within an assembly.</span></span> <span data-ttu-id="f9a86-119">W poniższym przykładzie plik projektu pokazuje jak zdefiniować elementy zawartości.</span><span class="sxs-lookup"><span data-stu-id="f9a86-119">The following project file example shows how to define content items.</span></span>  
  
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
  
 <span data-ttu-id="f9a86-120">Aby zapewnić, że aplikacja może używać czcionek w czasie wykonywania, czcionki musi być dostępny w katalogu wdrożenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9a86-120">In order to ensure that the application can use the fonts at run time, the fonts must be accessible in the application's deployment directory.</span></span> <span data-ttu-id="f9a86-121">`<CopyToOutputDirectory>` Elementu w pliku projektu aplikacji pozwala automatycznie skopiować je do katalogu wdrożenia aplikacji podczas procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f9a86-121">The `<CopyToOutputDirectory>` element in the application's project file allows you to automatically copy the fonts to the application deployment directory during the build process.</span></span> <span data-ttu-id="f9a86-122">W poniższym przykładzie plik projektu pokazano, jak można skopiować czcionki do katalogu wdrażania.</span><span class="sxs-lookup"><span data-stu-id="f9a86-122">The following project file example shows how to copy fonts to the deployment directory.</span></span>  
  
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
  
 <span data-ttu-id="f9a86-123">Poniższy przykład kodu pokazuje, jak odwoływać się do aplikacji czcionki jako element zawartości — przywoływany element zawartości musi być w tym samym katalogu co pliki zestawu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9a86-123">The following code example shows how to reference the application's font as a content item—the referenced content item must be in the same directory as the application's assembly files.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>   
## <a name="adding-fonts-as-resource-items"></a><span data-ttu-id="f9a86-124">Dodawanie czcionki jako element zasobu</span><span class="sxs-lookup"><span data-stu-id="f9a86-124">Adding Fonts as Resource Items</span></span>  
 <span data-ttu-id="f9a86-125">Możesz dodać czcionki do aplikacji jako elementy zasobów projektu, które są osadzone w ramach plików zestawu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9a86-125">You can add fonts to your application as project resource items that are embedded within the application's assembly files.</span></span> <span data-ttu-id="f9a86-126">Przy użyciu oddzielnych podkatalogu dla zasobów pomaga organizować pliki projektu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9a86-126">Using a separate subdirectory for resources helps to organize the application's project files.</span></span> <span data-ttu-id="f9a86-127">W poniższym przykładzie plik projektu pokazuje jak zdefiniować czcionki jako zasób w oddzielnym podkatalogu.</span><span class="sxs-lookup"><span data-stu-id="f9a86-127">The following project file example shows how to define fonts as resource items in a separate subdirectory.</span></span>  
  
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
>  <span data-ttu-id="f9a86-128">Po dodaniu czcionki jako zasoby do aplikacji, upewnij się, czy ustawienie `<Resource>` elementu, a nie `<EmbeddedResource>` elementu w pliku projektu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9a86-128">When you add fonts as resources to your application, make sure you are setting the `<Resource>` element, and not the `<EmbeddedResource>` element in your application's project file.</span></span> <span data-ttu-id="f9a86-129">`<EmbeddedResource>` Element dla akcji kompilacji nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="f9a86-129">The `<EmbeddedResource>` element for the build action is not supported.</span></span>  
  
 <span data-ttu-id="f9a86-130">W poniższym przykładzie znaczników pokazano, jak odwołanie do zasobów czcionki w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9a86-130">The following markup example shows how to reference the application's font resources.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a><span data-ttu-id="f9a86-131">Odwoływanie się do elementów zasobu czcionek z kodu</span><span class="sxs-lookup"><span data-stu-id="f9a86-131">Referencing Font Resource Items from Code</span></span>  
 <span data-ttu-id="f9a86-132">Aby można było odwoływać się do elementów zasobu czcionek z kodu, należy podać odwołanie do zasobu legalną dwuczęściową czcionki: Podstawa [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]; i odwołanie do lokalizacji czcionki.</span><span class="sxs-lookup"><span data-stu-id="f9a86-132">In order to reference font resource items from code, you must supply a two-part font resource reference: the base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]; and the font location reference.</span></span> <span data-ttu-id="f9a86-133">Te wartości są używane jako parametry <xref:System.Windows.Media.FontFamily.%23ctor%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f9a86-133">These values are used as the parameters for the <xref:System.Windows.Media.FontFamily.%23ctor%2A> method.</span></span> <span data-ttu-id="f9a86-134">Poniższy przykład kodu pokazuje, jak odwoływać się do aplikacji czcionki zasobów w podkatalogu projektu o nazwie `resources`.</span><span class="sxs-lookup"><span data-stu-id="f9a86-134">The following code example shows how to reference the application's font resources in the project subdirectory called `resources`.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 <span data-ttu-id="f9a86-135">Podstawa [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] mogą obejmować podkatalogu aplikacji, w którym znajduje się zasób czcionki.</span><span class="sxs-lookup"><span data-stu-id="f9a86-135">The base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] can include the application subdirectory where the font resource resides.</span></span> <span data-ttu-id="f9a86-136">W tym przypadku nie będzie trzeba określić katalog czcionek odwołanie do lokalizacji, ale musi zawierać znaku "`./`", które określa zasoby czcionki znajduje się w tym samym katalogu, określony przez podstawę [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f9a86-136">In this case, the font location reference would not need to specify a directory, but would have to include a leading "`./`", which indicates the font resource is in the same directory specified by the base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span></span> <span data-ttu-id="f9a86-137">Poniższy przykład kodu pokazuje alternatywny sposób odwołuje się do elementu zasobu czcionek — jest to równoważne w poprzednim przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="f9a86-137">The following code example shows an alternate way of referencing the font resource item—it is equivalent to the previous code example.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a><span data-ttu-id="f9a86-138">Odwoływanie się do czcionki z tym samym podkatalogu aplikacji</span><span class="sxs-lookup"><span data-stu-id="f9a86-138">Referencing Fonts from the Same Application Subdirectory</span></span>  
 <span data-ttu-id="f9a86-139">Pliki można umieścić zarówno aplikacji zawartości i zasobów w ramach tego samego użytkownika podkatalogu projektu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9a86-139">You can place both application content and resource files within the same user-defined subdirectory of your application project.</span></span> <span data-ttu-id="f9a86-140">W poniższym przykładzie plik projektu zawiera strony zawartości i zasobów czcionki, zdefiniowane w tym samym podkatalogu.</span><span class="sxs-lookup"><span data-stu-id="f9a86-140">The following project file example shows a content page and font resources defined in the same subdirectory.</span></span>  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 <span data-ttu-id="f9a86-141">Ponieważ zawartość aplikacji i czcionki znajdują się w tym samym podkatalogu, odwołanie czcionka jest względem zawartości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9a86-141">Since the application content and font are in the same subdirectory, the font reference is relative to the application content.</span></span> <span data-ttu-id="f9a86-142">Poniższe przykłady pokazują jak odwoływać się do zasobu czcionek aplikacji po czcionkę w tym samym katalogu co aplikacja.</span><span class="sxs-lookup"><span data-stu-id="f9a86-142">The following examples show how to reference the application's font resource when the font is in the same directory as the application.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a><span data-ttu-id="f9a86-143">Wyliczanie czcionek w aplikacji</span><span class="sxs-lookup"><span data-stu-id="f9a86-143">Enumerating Fonts in an Application</span></span>  
 <span data-ttu-id="f9a86-144">Aby wyliczyć czcionki jako zasób w aplikacji, należy użyć <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> lub <xref:System.Windows.Media.Fonts.GetTypefaces%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f9a86-144">To enumerate fonts as resource items in your application, use either the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> or <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method.</span></span> <span data-ttu-id="f9a86-145">Poniższy przykład pokazuje, jak używać <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> metodę, aby zwrócić zbiór <xref:System.Windows.Media.FontFamily> obiektów z lokalizacji czcionki w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9a86-145">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> method to return the collection of <xref:System.Windows.Media.FontFamily> objects from the application font location.</span></span> <span data-ttu-id="f9a86-146">W takim przypadku aplikacja zawiera podkatalog o nazwie "zasoby".</span><span class="sxs-lookup"><span data-stu-id="f9a86-146">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 <span data-ttu-id="f9a86-147">Poniższy przykład pokazuje, jak używać <xref:System.Windows.Media.Fonts.GetTypefaces%2A> metodę, aby zwrócić zbiór <xref:System.Windows.Media.Typeface> obiektów z lokalizacji czcionki w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9a86-147">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method to return the collection of <xref:System.Windows.Media.Typeface> objects from the application font location.</span></span> <span data-ttu-id="f9a86-148">W takim przypadku aplikacja zawiera podkatalog o nazwie "zasoby".</span><span class="sxs-lookup"><span data-stu-id="f9a86-148">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>   
## <a name="creating-a-font-resource-library"></a><span data-ttu-id="f9a86-149">Tworzenie biblioteki zasobów czcionki</span><span class="sxs-lookup"><span data-stu-id="f9a86-149">Creating a Font Resource Library</span></span>  
 <span data-ttu-id="f9a86-150">Można utworzyć bibliotekę tylko do zasobów, która zawiera tylko czcionki — żaden kod nie jest częścią tego typu projektu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="f9a86-150">You can create a resource-only library that contains only fonts—no code is part of this type of library project.</span></span> <span data-ttu-id="f9a86-151">Tworzenie biblioteki tylko do zasobów jest typową techniką dla oddzielenie zasobów z kodu aplikacji, który używa tych.</span><span class="sxs-lookup"><span data-stu-id="f9a86-151">Creating a resource-only library is a common technique for decoupling resources from the application code that uses them.</span></span> <span data-ttu-id="f9a86-152">Dzięki temu również zestawu biblioteki do uwzględnienia w wielu projektach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9a86-152">This also allows the library assembly to be included with multiple application projects.</span></span> <span data-ttu-id="f9a86-153">W poniższym przykładzie plik projektu zawiera kluczowych części projektu biblioteki tylko do zasobów.</span><span class="sxs-lookup"><span data-stu-id="f9a86-153">The following project file example shows the key portions of a resource-only library project.</span></span>  
  
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
  
### <a name="referencing-a-font-in-a-resource-library"></a><span data-ttu-id="f9a86-154">Odwoływanie się do czcionki w bibliotece zasobów</span><span class="sxs-lookup"><span data-stu-id="f9a86-154">Referencing a Font in a Resource Library</span></span>  
 <span data-ttu-id="f9a86-155">Aby odwołać czcionki w bibliotece zasobów z aplikacji, musi prefiks odwołanie czcionki o nazwie zestawu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="f9a86-155">To reference a font in a resource library from your application, you must prefix the font reference with the name of the library assembly.</span></span> <span data-ttu-id="f9a86-156">W tym przypadku zestaw zasobów czcionki jest "FontLibrary".</span><span class="sxs-lookup"><span data-stu-id="f9a86-156">In this case, the font resource assembly is "FontLibrary".</span></span> <span data-ttu-id="f9a86-157">Aby rozdzielić nazwy zestawu z odwołania w zestawie, użyj znaku ";".</span><span class="sxs-lookup"><span data-stu-id="f9a86-157">To separate the assembly name from the reference within the assembly, use a ';' character.</span></span> <span data-ttu-id="f9a86-158">Dodawanie słowa kluczowego "Component" odwołanie do nazwy czcionki kończy pełny odwołanie do zasobu biblioteki czcionki.</span><span class="sxs-lookup"><span data-stu-id="f9a86-158">Adding the "Component" keyword followed by the reference to the font name completes the full reference to the font library's resource.</span></span> <span data-ttu-id="f9a86-159">Poniższy przykład kodu pokazuje jak odwoływać się do czcionki w zestawie zasobów biblioteki.</span><span class="sxs-lookup"><span data-stu-id="f9a86-159">The following code example shows how to reference a font in a resource library assembly.</span></span>  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
>  <span data-ttu-id="f9a86-160">Ten zestaw SDK zawiera zestaw przykładowych [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionek, które można używać z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9a86-160">This SDK contains a set of sample [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] fonts that you can use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span> <span data-ttu-id="f9a86-161">Czcionki są zdefiniowane w bibliotece tylko do zasobów.</span><span class="sxs-lookup"><span data-stu-id="f9a86-161">The fonts are defined in a resource-only library.</span></span> <span data-ttu-id="f9a86-162">Aby uzyskać więcej informacji, zobacz [przykład pakietu czcionek OpenType](sample-opentype-font-pack.md).</span><span class="sxs-lookup"><span data-stu-id="f9a86-162">For more information, see [Sample OpenType Font Pack](sample-opentype-font-pack.md).</span></span>  
  
<a name="limitations_on_font_usage"></a>   
## <a name="limitations-on-font-usage"></a><span data-ttu-id="f9a86-163">Ograniczenia dotyczące użycia czcionki</span><span class="sxs-lookup"><span data-stu-id="f9a86-163">Limitations on Font Usage</span></span>  
 <span data-ttu-id="f9a86-164">Na poniższej liście opisano również kilka ograniczeń na tworzenie pakietów i używanie czcionek w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji:</span><span class="sxs-lookup"><span data-stu-id="f9a86-164">The following list describes several limitations on the packaging and use of fonts in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications:</span></span>  
  
-   <span data-ttu-id="f9a86-165">**Osadzanie bity uprawnień czcionek:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji sprawdź lub nie wymuszają żadnych osadzanie bity uprawnień czcionek.</span><span class="sxs-lookup"><span data-stu-id="f9a86-165">**Font embedding permission bits:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not check or enforce any font embedding permission bits.</span></span> <span data-ttu-id="f9a86-166">Zobacz [czcionki Introduction_to_Packing](#introduction_to_packaging_fonts) sekcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="f9a86-166">See the [Introduction_to_Packing Fonts](#introduction_to_packaging_fonts) section for more information.</span></span>  
  
-   <span data-ttu-id="f9a86-167">**Witryna pochodzenia czcionki:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje nie zezwalają na odwołanie czcionki do protokołu http lub ftp [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f9a86-167">**Site of origin fonts:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow a font reference to an http or ftp [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span></span>  
  
-   <span data-ttu-id="f9a86-168">**Bezwzględny identyfikator URI przy użyciu pakietu: notacji:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje nie pozwalają na tworzenie <xref:System.Windows.Media.FontFamily> programowo przy użyciu "pakietu:" jako część bezwzględną [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] odwołań do czcionki.</span><span class="sxs-lookup"><span data-stu-id="f9a86-168">**Absolute URI using the pack: notation:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow you to create a <xref:System.Windows.Media.FontFamily> object programmatically using "pack:" as part of the absolute [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] reference to a font.</span></span> <span data-ttu-id="f9a86-169">Na przykład `"pack://application:,,,/resources/#Pericles Light"` jest odwołaniem nieprawidłowa czcionka.</span><span class="sxs-lookup"><span data-stu-id="f9a86-169">For example, `"pack://application:,,,/resources/#Pericles Light"` is an invalid font reference.</span></span>  
  
-   <span data-ttu-id="f9a86-170">**Osadzanie czcionki automatyczne:** W czasie projektowania nie jest obsługiwane podczas wyszukiwania aplikacji używanie czcionek i automatycznie osadzania czcionek w aplikacji zasobów.</span><span class="sxs-lookup"><span data-stu-id="f9a86-170">**Automatic font embedding:** During design time, there is no support for searching an application's use of fonts and automatically embedding the fonts in the application's resources.</span></span>  
  
-   <span data-ttu-id="f9a86-171">**Czcionka podzbiory:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje nie obsługują tworzenia podzestawy czcionki-fixed dokumentów.</span><span class="sxs-lookup"><span data-stu-id="f9a86-171">**Font subsets:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not support the creation of font subsets for non-fixed documents.</span></span>  
  
-   <span data-ttu-id="f9a86-172">W przypadkach, w przypadku nieprawidłowego odwołania, aplikacja powróci przy użyciu dostępnej czcionki.</span><span class="sxs-lookup"><span data-stu-id="f9a86-172">In cases where there is an incorrect reference, the application falls back to using an available font.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9a86-173">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9a86-173">See also</span></span>
- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- [<span data-ttu-id="f9a86-174">Typografia firmy Microsoft: Łączy, wiadomości i kontakty</span><span class="sxs-lookup"><span data-stu-id="f9a86-174">Microsoft Typography: Links, News, and Contacts</span></span>](https://docs.microsoft.com/typography/)
- [<span data-ttu-id="f9a86-175">Specyfikacja OpenType</span><span class="sxs-lookup"><span data-stu-id="f9a86-175">OpenType Specification</span></span>](https://www.microsoft.com/typography/otspec/)
- [<span data-ttu-id="f9a86-176">Funkcje czcionki OpenType</span><span class="sxs-lookup"><span data-stu-id="f9a86-176">OpenType Font Features</span></span>](opentype-font-features.md)
- [<span data-ttu-id="f9a86-177">Przykład pakietu czcionek OpenType</span><span class="sxs-lookup"><span data-stu-id="f9a86-177">Sample OpenType Font Pack</span></span>](sample-opentype-font-pack.md)
