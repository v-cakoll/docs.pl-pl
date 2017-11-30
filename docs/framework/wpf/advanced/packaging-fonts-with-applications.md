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
ms.openlocfilehash: f60668f1bdac6607383b2ddf5c5ab1e41e31862b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="packaging-fonts-with-applications"></a><span data-ttu-id="4aabc-102">Pakowanie czcionek z aplikacjami</span><span class="sxs-lookup"><span data-stu-id="4aabc-102">Packaging Fonts with Applications</span></span>
<span data-ttu-id="4aabc-103">Ten temat zawiera przegląd zagadnień związanych z czcionkami pakietu z sieci [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4aabc-103">This topic provides an overview of how to package fonts with your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4aabc-104">Podobnie jak w przypadku większości typów oprogramowania, pliki czcionki są licencjonowane, a nie sprzedawane.</span><span class="sxs-lookup"><span data-stu-id="4aabc-104">As with most types of software, font files are licensed, rather than sold.</span></span> <span data-ttu-id="4aabc-105">Licencje, które określają sposób używanie czcionek różnią się dostawcy dostawcy, ale ogólnie większość licencji, w tym dotyczących czcionek [!INCLUDE[TLA#tla_ms#initcap](../../../../includes/tlasharptla-mssharpinitcap-md.md)] dostarcza z aplikacjami i [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], nie zezwalaj na czcionki, które mają zostać osadzone w aplikacji lub w inny sposób Ponowna dystrybucja.</span><span class="sxs-lookup"><span data-stu-id="4aabc-105">Licenses that govern the use of fonts vary from vendor to vendor but in general most licenses, including those covering the fonts [!INCLUDE[TLA#tla_ms#initcap](../../../../includes/tlasharptla-mssharpinitcap-md.md)] supplies with applications and [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], do not allow the fonts to be embedded within applications or otherwise redistributed.</span></span> <span data-ttu-id="4aabc-106">W związku z tym jako deweloper, który odpowiedzialność za zapewnienie, że masz wymagane prawa dla żadnej czcionki, który osadzić w aplikacji lub w inny sposób Ponowna dystrybucja.</span><span class="sxs-lookup"><span data-stu-id="4aabc-106">Therefore, as a developer it is your responsibility to ensure that you have the required license rights for any font you embed within an application or otherwise redistribute.</span></span>  
  

  
<a name="introduction_to_packaging_fonts"></a>   
## <a name="introduction-to-packaging-fonts"></a><span data-ttu-id="4aabc-107">Wprowadzenie do tworzenia pakietów czcionek</span><span class="sxs-lookup"><span data-stu-id="4aabc-107">Introduction to Packaging Fonts</span></span>  
 <span data-ttu-id="4aabc-108">Można łatwo spakować czcionki jako zasoby w sieci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, aby wyświetlić tekst interfejsu użytkownika i innych typów tekstu na podstawie zawartości.</span><span class="sxs-lookup"><span data-stu-id="4aabc-108">You can easily package fonts as resources within your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications to display user interface text and other types of text based content.</span></span> <span data-ttu-id="4aabc-109">Czcionki mogą być oddzielony od lub osadzone w aplikacji zestawu plików.</span><span class="sxs-lookup"><span data-stu-id="4aabc-109">The fonts can be separate from or embedded within the application's assembly files.</span></span> <span data-ttu-id="4aabc-110">Można również utworzyć w bibliotece tylko do zasobów czcionki aplikacji może odwoływać się.</span><span class="sxs-lookup"><span data-stu-id="4aabc-110">You can also create a resource-only font library, which your application can reference.</span></span>  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]<span data-ttu-id="4aabc-111">i [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] czcionki zawierać flagę typu fsType, wskazującą osadzanie licencjonowania czcionek praw czcionki.</span><span class="sxs-lookup"><span data-stu-id="4aabc-111"> and [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] fonts contain a type flag, fsType, that indicates font embedding licensing rights for the font.</span></span> <span data-ttu-id="4aabc-112">Jednak tego typu Flaga odwołuje się tylko do czcionki osadzone przechowywane w dokumencie — it nie odwołuje się do czcionki osadzone w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4aabc-112">However, this type flag only refers to embedded fonts stored in a document–it does not refer to fonts embedded in an application.</span></span> <span data-ttu-id="4aabc-113">Możesz pobrać osadzanie praw dla czcionki, tworząc czcionek <xref:System.Windows.Media.GlyphTypeface> obiektu i odwołanie się do jego <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="4aabc-113">You can retrieve the font embedding rights for a font by creating a <xref:System.Windows.Media.GlyphTypeface> object and referencing its <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> property.</span></span> <span data-ttu-id="4aabc-114">Zapoznaj się z sekcją "OS i 2 oraz Windows metryki" [specyfikacji OpenType](http://www.microsoft.com/typography/otspec/os2.htm) Aby uzyskać więcej informacji na temat flagi fsType.</span><span class="sxs-lookup"><span data-stu-id="4aabc-114">Refer to the "OS/2 and Windows Metrics" section of the [OpenType Specification](http://www.microsoft.com/typography/otspec/os2.htm) for more information on the fsType flag.</span></span>  
  
 <span data-ttu-id="4aabc-115">[Typography Microsoft](http://www.microsoft.com/typography/links/) witryna sieci Web zawiera informacje kontaktowe, które mogą pomóc w zlokalizować dostawcy określonej czcionki lub znaleźć dostawcy czcionki dla niestandardowych pracy.</span><span class="sxs-lookup"><span data-stu-id="4aabc-115">The [Microsoft Typography](http://www.microsoft.com/typography/links/) Web site includes contact information that can help you locate a particular font vendor or find a font vendor for custom work.</span></span>  
  
<a name="adding_fonts_as_content_items"></a>   
## <a name="adding-fonts-as-content-items"></a><span data-ttu-id="4aabc-116">Dodawanie czcionek jako elementy zawartości</span><span class="sxs-lookup"><span data-stu-id="4aabc-116">Adding Fonts as Content Items</span></span>  
 <span data-ttu-id="4aabc-117">Czcionki można dodać do aplikacji jako elementy zawartości projektu, które są oddzielne od plików zestawu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4aabc-117">You can add fonts to your application as project content items that are separate from the application's assembly files.</span></span> <span data-ttu-id="4aabc-118">Oznacza to, że elementy zawartości nie są osadzone jako zasoby w zestawie.</span><span class="sxs-lookup"><span data-stu-id="4aabc-118">This means that content items are not embedded as resources within an assembly.</span></span> <span data-ttu-id="4aabc-119">W poniższym przykładzie plik projektu przedstawia sposób definiowania elementów zawartości.</span><span class="sxs-lookup"><span data-stu-id="4aabc-119">The following project file example shows how to define content items.</span></span>  
  
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
  
 <span data-ttu-id="4aabc-120">Aby upewnić się, że aplikacja może używać czcionek w czasie wykonywania, czcionki musi być dostępny w katalogu wdrożenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4aabc-120">In order to ensure that the application can use the fonts at run time, the fonts must be accessible in the application's deployment directory.</span></span> <span data-ttu-id="4aabc-121">`<CopyToOutputDirectory>` Elementu w pliku projektu aplikacji pozwala czcionki mają być automatycznie kopiowane do katalogu wdrożenia aplikacji podczas procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4aabc-121">The `<CopyToOutputDirectory>` element in the application's project file allows you to automatically copy the fonts to the application deployment directory during the build process.</span></span> <span data-ttu-id="4aabc-122">W poniższym przykładzie plik projektu przedstawia sposób kopiowania czcionki do katalogu wdrażania.</span><span class="sxs-lookup"><span data-stu-id="4aabc-122">The following project file example shows how to copy fonts to the deployment directory.</span></span>  
  
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
  
 <span data-ttu-id="4aabc-123">Poniższy przykładowy kod przedstawia sposób odwołania czcionkę aplikacji jako element zawartości — przywoływany element zawartości musi być w tym samym katalogu co pliki zestawu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4aabc-123">The following code example shows how to reference the application's font as a content item—the referenced content item must be in the same directory as the application's assembly files.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>   
## <a name="adding-fonts-as-resource-items"></a><span data-ttu-id="4aabc-124">Dodawanie czcionek jako elementy zasobów</span><span class="sxs-lookup"><span data-stu-id="4aabc-124">Adding Fonts as Resource Items</span></span>  
 <span data-ttu-id="4aabc-125">Czcionki można dodać do aplikacji jako elementy zasobów projektu, które są osadzone w aplikacji zestawu plików.</span><span class="sxs-lookup"><span data-stu-id="4aabc-125">You can add fonts to your application as project resource items that are embedded within the application's assembly files.</span></span> <span data-ttu-id="4aabc-126">Przy użyciu osobnych podkatalogu dla zasobów pomaga organizować pliki projektu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4aabc-126">Using a separate subdirectory for resources helps to organize the application's project files.</span></span> <span data-ttu-id="4aabc-127">W poniższym przykładzie plik projektu przedstawia sposób definiowania czcionki jako elementy zasobów w oddzielnych podkatalogu.</span><span class="sxs-lookup"><span data-stu-id="4aabc-127">The following project file example shows how to define fonts as resource items in a separate subdirectory.</span></span>  
  
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
>  <span data-ttu-id="4aabc-128">Po dodaniu czcionki jako zasoby do aplikacji, upewnij się, czy ustawienie `<Resource>` elementu, a nie `<EmbeddedResource>` elementu w pliku projektu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4aabc-128">When you add fonts as resources to your application, make sure you are setting the `<Resource>` element, and not the `<EmbeddedResource>` element in your application's project file.</span></span> <span data-ttu-id="4aabc-129">`<EmbeddedResource>` Element dla akcji kompilacji nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="4aabc-129">The `<EmbeddedResource>` element for the build action is not supported.</span></span>  
  
 <span data-ttu-id="4aabc-130">W poniższym przykładzie znaczników pokazuje, jak odwołanie do zasobów czcionki aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4aabc-130">The following markup example shows how to reference the application's font resources.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a><span data-ttu-id="4aabc-131">Odwołania do elementów zasobu czcionki z kodu</span><span class="sxs-lookup"><span data-stu-id="4aabc-131">Referencing Font Resource Items from Code</span></span>  
 <span data-ttu-id="4aabc-132">Aby można było odwoływać się do czcionki zasobu elementów z kodu, musisz podać odwołanie zasobów czcionki z dwóch części: base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]; i odwołania do lokalizacji czcionki.</span><span class="sxs-lookup"><span data-stu-id="4aabc-132">In order to reference font resource items from code, you must supply a two-part font resource reference: the base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]; and the font location reference.</span></span> <span data-ttu-id="4aabc-133">Te wartości są używane jako parametry <xref:System.Windows.Media.FontFamily.%23ctor%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4aabc-133">These values are used as the parameters for the <xref:System.Windows.Media.FontFamily.%23ctor%2A> method.</span></span> <span data-ttu-id="4aabc-134">Poniższy przykład kodu pokazuje, jak odwołanie do zasobów czcionki aplikacji w podkatalogu projektu o nazwie `resources`.</span><span class="sxs-lookup"><span data-stu-id="4aabc-134">The following code example shows how to reference the application's font resources in the project subdirectory called `resources`.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 <span data-ttu-id="4aabc-135">Podstawowym [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] mogą obejmować podkatalogu aplikacji, gdzie znajduje się zasób czcionki.</span><span class="sxs-lookup"><span data-stu-id="4aabc-135">The base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] can include the application subdirectory where the font resource resides.</span></span> <span data-ttu-id="4aabc-136">W takim przypadku nie będzie trzeba określić katalog odwołania do lokalizacji czcionki, ale musi zawierać na początku "`./`", które określa zasoby czcionki jest w tym samym katalogu, określony przez podstawę [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4aabc-136">In this case, the font location reference would not need to specify a directory, but would have to include a leading "`./`", which indicates the font resource is in the same directory specified by the base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span></span> <span data-ttu-id="4aabc-137">Poniższy przykład kodu pokazuje alternatywny sposób odwołania do elementu zasobów czcionki — jest to odpowiednik w poprzednim przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="4aabc-137">The following code example shows an alternate way of referencing the font resource item—it is equivalent to the previous code example.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a><span data-ttu-id="4aabc-138">Odwołanie do czcionki z tym samym podkatalogu aplikacji</span><span class="sxs-lookup"><span data-stu-id="4aabc-138">Referencing Fonts from the Same Application Subdirectory</span></span>  
 <span data-ttu-id="4aabc-139">Pliki można umieścić zarówno aplikacji zawartości i zasobów w tym samym podkatalogu użytkownika projektu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4aabc-139">You can place both application content and resource files within the same user-defined subdirectory of your application project.</span></span> <span data-ttu-id="4aabc-140">W poniższym przykładzie plik projektu zawiera strony zawartości i zasoby czcionki zdefiniowane w tym samym podkatalogu.</span><span class="sxs-lookup"><span data-stu-id="4aabc-140">The following project file example shows a content page and font resources defined in the same subdirectory.</span></span>  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 <span data-ttu-id="4aabc-141">Ponieważ zawartość aplikacji i czcionki znajdują się w tym samym podkatalogu, odwołanie czcionki jest określana względem zawartości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4aabc-141">Since the application content and font are in the same subdirectory, the font reference is relative to the application content.</span></span> <span data-ttu-id="4aabc-142">Poniższe przykłady przedstawiają sposób odwołania zasobów czcionki aplikacji po czcionkę w tym samym katalogu co aplikacja.</span><span class="sxs-lookup"><span data-stu-id="4aabc-142">The following examples show how to reference the application's font resource when the font is in the same directory as the application.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a><span data-ttu-id="4aabc-143">Wyliczanie czcionek w aplikacji</span><span class="sxs-lookup"><span data-stu-id="4aabc-143">Enumerating Fonts in an Application</span></span>  
 <span data-ttu-id="4aabc-144">Aby wyliczyć czcionki jako zasób w aplikacji, użyj <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> lub <xref:System.Windows.Media.Fonts.GetTypefaces%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4aabc-144">To enumerate fonts as resource items in your application, use either the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> or <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method.</span></span> <span data-ttu-id="4aabc-145">Poniższy przykład przedstawia użycie <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> metodę, aby zwrócić zbiór <xref:System.Windows.Media.FontFamily> obiektów z lokalizacji, czcionki w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4aabc-145">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> method to return the collection of <xref:System.Windows.Media.FontFamily> objects from the application font location.</span></span> <span data-ttu-id="4aabc-146">W takim przypadku aplikacja zawiera podkatalog o nazwie "resources".</span><span class="sxs-lookup"><span data-stu-id="4aabc-146">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 <span data-ttu-id="4aabc-147">Poniższy przykład przedstawia użycie <xref:System.Windows.Media.Fonts.GetTypefaces%2A> metodę, aby zwrócić zbiór <xref:System.Windows.Media.Typeface> obiektów z lokalizacji, czcionki w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4aabc-147">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method to return the collection of <xref:System.Windows.Media.Typeface> objects from the application font location.</span></span> <span data-ttu-id="4aabc-148">W takim przypadku aplikacja zawiera podkatalog o nazwie "resources".</span><span class="sxs-lookup"><span data-stu-id="4aabc-148">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>   
## <a name="creating-a-font-resource-library"></a><span data-ttu-id="4aabc-149">Tworzenie biblioteki zasobów czcionki</span><span class="sxs-lookup"><span data-stu-id="4aabc-149">Creating a Font Resource Library</span></span>  
 <span data-ttu-id="4aabc-150">Można utworzyć tylko zasobów biblioteki, która zawiera tylko czcionki — żaden kod nie jest częścią tego typu projektu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="4aabc-150">You can create a resource-only library that contains only fonts—no code is part of this type of library project.</span></span> <span data-ttu-id="4aabc-151">Tworzenie biblioteki tylko do zasobu jest typowe technika oddzielenie zasobów z kodu aplikacji, który używa tych.</span><span class="sxs-lookup"><span data-stu-id="4aabc-151">Creating a resource-only library is a common technique for decoupling resources from the application code that uses them.</span></span> <span data-ttu-id="4aabc-152">Umożliwia to także zestaw biblioteki zostanie uwzględniona w wielu projektach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4aabc-152">This also allows the library assembly to be included with multiple application projects.</span></span> <span data-ttu-id="4aabc-153">W poniższym przykładzie plik projektu zawiera części klucza projektu biblioteki tylko do zasobów.</span><span class="sxs-lookup"><span data-stu-id="4aabc-153">The following project file example shows the key portions of a resource-only library project.</span></span>  
  
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
  
### <a name="referencing-a-font-in-a-resource-library"></a><span data-ttu-id="4aabc-154">Odwołanie do czcionki w bibliotece zasobów</span><span class="sxs-lookup"><span data-stu-id="4aabc-154">Referencing a Font in a Resource Library</span></span>  
 <span data-ttu-id="4aabc-155">Aby odwołać czcionki w bibliotece zasobów z poziomu aplikacji, musi prefiks odwołanie czcionki o nazwie zestawu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="4aabc-155">To reference a font in a resource library from your application, you must prefix the font reference with the name of the library assembly.</span></span> <span data-ttu-id="4aabc-156">W takim przypadku zestaw zasobów czcionki jest "FontLibrary".</span><span class="sxs-lookup"><span data-stu-id="4aabc-156">In this case, the font resource assembly is "FontLibrary".</span></span> <span data-ttu-id="4aabc-157">Rozdziel nazwy zestawu z odwołania w zestawie, użyj znaku ";".</span><span class="sxs-lookup"><span data-stu-id="4aabc-157">To separate the assembly name from the reference within the assembly, use a ';' character.</span></span> <span data-ttu-id="4aabc-158">Dodawanie — słowo kluczowe "Component" odwołanie do nazwy czcionki wykonuje pełne odwołanie do zasobu biblioteki czcionek.</span><span class="sxs-lookup"><span data-stu-id="4aabc-158">Adding the "Component" keyword followed by the reference to the font name completes the full reference to the font library's resource.</span></span> <span data-ttu-id="4aabc-159">Poniższy przykład kodu pokazuje, jak ma dotyczyć odwołanie czcionki w zestawie biblioteki zasobów.</span><span class="sxs-lookup"><span data-stu-id="4aabc-159">The following code example shows how to reference a font in a resource library assembly.</span></span>  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
>  <span data-ttu-id="4aabc-160">Ten zestaw SDK zawiera zestaw próbki [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionek, które można używać z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4aabc-160">This SDK contains a set of sample [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] fonts that you can use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span> <span data-ttu-id="4aabc-161">Czcionki są definiowane w bibliotece tylko do zasobów.</span><span class="sxs-lookup"><span data-stu-id="4aabc-161">The fonts are defined in a resource-only library.</span></span> <span data-ttu-id="4aabc-162">Aby uzyskać więcej informacji, zobacz [przykładowym pakiecie czcionek OpenType](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md).</span><span class="sxs-lookup"><span data-stu-id="4aabc-162">For more information, see [Sample OpenType Font Pack](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md).</span></span>  
  
<a name="limitations_on_font_usage"></a>   
## <a name="limitations-on-font-usage"></a><span data-ttu-id="4aabc-163">Ograniczenia dotyczące użycia czcionki</span><span class="sxs-lookup"><span data-stu-id="4aabc-163">Limitations on Font Usage</span></span>  
 <span data-ttu-id="4aabc-164">Poniższa lista zawiera kilka ograniczeń na tworzenie pakietów i używanie czcionek w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji:</span><span class="sxs-lookup"><span data-stu-id="4aabc-164">The following list describes several limitations on the packaging and use of fonts in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications:</span></span>  
  
-   <span data-ttu-id="4aabc-165">**Osadzanie bity uprawnienia czcionek:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie Sprawdź lub wymusić żadnej czcionki osadzanie bity uprawnienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4aabc-165">**Font embedding permission bits:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not check or enforce any font embedding permission bits.</span></span> <span data-ttu-id="4aabc-166">Zobacz [czcionki Introduction_to_Packing](#introduction_to_packaging_fonts) sekcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="4aabc-166">See the [Introduction_to_Packing Fonts](#introduction_to_packaging_fonts) section for more information.</span></span>  
  
-   <span data-ttu-id="4aabc-167">**Witryny pochodzenia czcionek:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje nie zezwalają na odwołanie czcionki do protokołu http lub ftp [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4aabc-167">**Site of origin fonts:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow a font reference to an http or ftp [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span></span>  
  
-   <span data-ttu-id="4aabc-168">**Bezwzględny identyfikator URI przy użyciu pakietu: notacji:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje nie pozwala na tworzenie <xref:System.Windows.Media.FontFamily> programowo przy użyciu "pakietu:" jako część bezwzględną [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] odwołanie do czcionki.</span><span class="sxs-lookup"><span data-stu-id="4aabc-168">**Absolute URI using the pack: notation:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow you to create a <xref:System.Windows.Media.FontFamily> object programmatically using "pack:" as part of the absolute [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] reference to a font.</span></span> <span data-ttu-id="4aabc-169">Na przykład `"pack://application:,,,/resources/#Pericles Light"` jest odwołaniem nieprawidłową czcionkę.</span><span class="sxs-lookup"><span data-stu-id="4aabc-169">For example, `"pack://application:,,,/resources/#Pericles Light"` is an invalid font reference.</span></span>  
  
-   <span data-ttu-id="4aabc-170">**Osadzanie czcionek automatycznego:** w czasie projektowania, nie jest obsługiwane podczas wyszukiwania użycia aplikacji czcionek i automatycznie osadzania czcionek w zasoby aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4aabc-170">**Automatic font embedding:** During design time, there is no support for searching an application's use of fonts and automatically embedding the fonts in the application's resources.</span></span>  
  
-   <span data-ttu-id="4aabc-171">**Podzbiory czcionki:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje nie obsługują tworzenia podzbiorów czcionki dla niestałych dokumenty.</span><span class="sxs-lookup"><span data-stu-id="4aabc-171">**Font subsets:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not support the creation of font subsets for non-fixed documents.</span></span>  
  
-   <span data-ttu-id="4aabc-172">W przypadkach, w przypadku nieprawidłowego odwołania, aplikacja przełączy się dostępna czcionka.</span><span class="sxs-lookup"><span data-stu-id="4aabc-172">In cases where there is an incorrect reference, the application falls back to using an available font.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4aabc-173">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4aabc-173">See Also</span></span>  
 <xref:System.Windows.Documents.Typography>  
 <xref:System.Windows.Media.FontFamily>  
 [<span data-ttu-id="4aabc-174">Typografii firmy Microsoft: Łączy, wiadomości i kontakty</span><span class="sxs-lookup"><span data-stu-id="4aabc-174">Microsoft Typography: Links, News, and Contacts</span></span>](http://www.microsoft.com/typography/links/)  
 [<span data-ttu-id="4aabc-175">Specyfikacja OpenType</span><span class="sxs-lookup"><span data-stu-id="4aabc-175">OpenType Specification</span></span>](http://www.microsoft.com/typography/otspec/)  
 [<span data-ttu-id="4aabc-176">Funkcje czcionek OpenType</span><span class="sxs-lookup"><span data-stu-id="4aabc-176">OpenType Font Features</span></span>](../../../../docs/framework/wpf/advanced/opentype-font-features.md)  
 [<span data-ttu-id="4aabc-177">Przykładowy pakiet czcionek OpenType</span><span class="sxs-lookup"><span data-stu-id="4aabc-177">Sample OpenType Font Pack</span></span>](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)
