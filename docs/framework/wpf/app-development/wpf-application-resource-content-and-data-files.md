---
title: Zasoby aplikacji, zawartość i pliki danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF application [WPF], files
- loose resources [WPF]
- content files [WPF]
- Site of Origin files [WPF]
- resource files [WPF]
- remote files [WPF]
- embedded resources [WPF]
- files [WPF]
- referencing application files [WPF]
- application development [WPF], files
- application management [WPF]
ms.assetid: 7ad2943b-3961-41d3-8fc6-1582d43f5d99
ms.openlocfilehash: f17898972eeef66447060db32bae5fae377b710e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186201"
---
# <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="b3b54-102">Zasoby aplikacji WPF, zawartość, pliki danych</span><span class="sxs-lookup"><span data-stu-id="b3b54-102">WPF Application Resource, Content, and Data Files</span></span>
<span data-ttu-id="b3b54-103">Aplikacje systemu Microsoft Windows często zależą od plików [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]zawierających dane niewykonalne, takie jak obrazy, wideo i audio.</span><span class="sxs-lookup"><span data-stu-id="b3b54-103">Microsoft Windows applications often depend on files that contain non-executable data, such as [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], images, video, and audio.</span></span> <span data-ttu-id="b3b54-104">Windows Presentation Foundation (WPF) oferuje specjalną obsługę konfigurowania, identyfikowania i używania tego typu plików danych, które są nazywane plikami danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b3b54-104">Windows Presentation Foundation (WPF) offers special support for configuring, identifying, and using these types of data files, which are called application data files.</span></span> <span data-ttu-id="b3b54-105">Ta obsługa koncentruje się wokół określonego zestawu typów plików danych aplikacji, w tym:</span><span class="sxs-lookup"><span data-stu-id="b3b54-105">This support revolves around a specific set of application data file types, including:</span></span>  
  
- <span data-ttu-id="b3b54-106">**Pliki zasobów:** Pliki danych, które są kompilowane do zestawu WPF wykonywalnego lub biblioteki.</span><span class="sxs-lookup"><span data-stu-id="b3b54-106">**Resource Files**: Data files that are compiled into either an executable or library WPF assembly.</span></span>  
  
- <span data-ttu-id="b3b54-107">**Pliki zawartości**: Autonomiczne pliki danych, które mają jawne skojarzenie z wykonywalnym zestawem WPF.</span><span class="sxs-lookup"><span data-stu-id="b3b54-107">**Content Files**: Standalone data files that have an explicit association with an executable WPF assembly.</span></span>  
  
- <span data-ttu-id="b3b54-108">**Site of Origin Files**: Autonomiczne pliki danych, które nie mają skojarzenia z wykonywalnym zestawem WPF.</span><span class="sxs-lookup"><span data-stu-id="b3b54-108">**Site of Origin Files**: Standalone data files that have no association with an executable WPF assembly.</span></span>  
  
 <span data-ttu-id="b3b54-109">Jednym z ważnych rozróżnienia między tymi trzema typami plików jest to, że pliki zasobów i pliki zawartości są znane w czasie kompilacji; zgromadzenie ma wyraźną wiedzę na ich temat.</span><span class="sxs-lookup"><span data-stu-id="b3b54-109">One important distinction to make between these three types of files is that resource files and content files are known at build time; an assembly has explicit knowledge of them.</span></span> <span data-ttu-id="b3b54-110">W przypadku plików lokacji pochodzenia zestaw może jednak nie mieć żadnej wiedzy o nich lub niejawnej wiedzy za pośrednictwem odwołania do identyfikatora URI (URI) jednolitego pakietu; w przypadku tego ostatniego nie ma gwarancji, że plik miejsca pochodzenia, do którego istnieje, o których mowa w rzeczywistości.</span><span class="sxs-lookup"><span data-stu-id="b3b54-110">For site of origin files, however, an assembly may have no knowledge of them at all, or implicit knowledge through a pack uniform resource identifier (URI) reference; the case of the latter, there is no guarantee that the referenced site of origin file actually exists.</span></span>  
  
 <span data-ttu-id="b3b54-111">Aby odwołać się do plików danych aplikacji, Program Windows Presentation Foundation (WPF) używa schematu URI (Pack uniform resource identifier), który jest szczegółowo opisany w [pakietach URI w WPF](pack-uris-in-wpf.md)).</span><span class="sxs-lookup"><span data-stu-id="b3b54-111">To reference application data files, Windows Presentation Foundation (WPF) uses the Pack uniform resource identifier (URI) Scheme, which is described in detail in [Pack URIs in WPF](pack-uris-in-wpf.md)).</span></span>  
  
 <span data-ttu-id="b3b54-112">W tym temacie opisano sposób konfigurowania i używania plików danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b3b54-112">This topic describes how to configure and use application data files.</span></span>  

<a name="Resource_Files"></a>
## <a name="resource-files"></a><span data-ttu-id="b3b54-113">Pliki zasobów</span><span class="sxs-lookup"><span data-stu-id="b3b54-113">Resource Files</span></span>  
 <span data-ttu-id="b3b54-114">Jeśli plik danych aplikacji musi być zawsze dostępny dla aplikacji, jedynym sposobem zagwarantowania dostępności jest skompilowanie go do głównego zestawu wykonywalnego aplikacji lub jednego z jej zestawów, do których istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="b3b54-114">If an application data file must always be available to an application, the only way to guarantee availability is to compile it into an application's main executable assembly or one of its referenced assemblies.</span></span> <span data-ttu-id="b3b54-115">Ten typ pliku danych aplikacji jest znany jako *plik zasobów*.</span><span class="sxs-lookup"><span data-stu-id="b3b54-115">This type of application data file is known as a *resource file*.</span></span>  
  
 <span data-ttu-id="b3b54-116">Pliki zasobów należy używać, gdy:</span><span class="sxs-lookup"><span data-stu-id="b3b54-116">You should use resource files when:</span></span>  
  
- <span data-ttu-id="b3b54-117">Nie trzeba aktualizować zawartości pliku zasobów po jego skompilowaniu do zestawu.</span><span class="sxs-lookup"><span data-stu-id="b3b54-117">You don't need to update the resource file's content after it is compiled into an assembly.</span></span>  
  
- <span data-ttu-id="b3b54-118">Chcesz uprościć złożoność dystrybucji aplikacji, zmniejszając liczbę zależności plików.</span><span class="sxs-lookup"><span data-stu-id="b3b54-118">You want to simplify application distribution complexity by reducing the number of file dependencies.</span></span>  
  
- <span data-ttu-id="b3b54-119">Plik danych aplikacji musi być zlokalizowany (zobacz [Omówienie globalizacji i lokalizacji WPF).](../advanced/wpf-globalization-and-localization-overview.md)</span><span class="sxs-lookup"><span data-stu-id="b3b54-119">Your application data file needs to be localizable (see [WPF Globalization and Localization Overview](../advanced/wpf-globalization-and-localization-overview.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3b54-120">Pliki zasobów opisane w tej sekcji różnią się od plików zasobów opisanych w [zasobach XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md) i różnią się od osadzonych lub połączonych zasobów opisanych w [sekcji Zarządzanie zasobami aplikacji (.NET).](/visualstudio/ide/managing-application-resources-dotnet)</span><span class="sxs-lookup"><span data-stu-id="b3b54-120">The resource files described in this section are different than the resource files described in [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) and different than the embedded or linked resources described in [Manage Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
### <a name="configuring-resource-files"></a><span data-ttu-id="b3b54-121">Konfigurowanie plików zasobów</span><span class="sxs-lookup"><span data-stu-id="b3b54-121">Configuring Resource Files</span></span>  
 <span data-ttu-id="b3b54-122">W WPF WPF plik zasobów jest plikiem, który jest zawarty w projekcie `Resource` aparatu kompilacji firmy Microsoft (MSBuild) jako element.</span><span class="sxs-lookup"><span data-stu-id="b3b54-122">In WPF, a resource file is a file that is included in an Microsoft build engine (MSBuild) project as a `Resource` item.</span></span>  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Resource Include="ResourceFile.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
> <span data-ttu-id="b3b54-123">W programie Visual Studio plik zasobu można utworzyć, dodając `Build Action` `Resource`plik do projektu i ustawiając go na .</span><span class="sxs-lookup"><span data-stu-id="b3b54-123">In Visual Studio, you create a resource file by adding a file to a project and setting its `Build Action` to `Resource`.</span></span>  
  
 <span data-ttu-id="b3b54-124">Po zbudowaniu projektu MSBuild kompiluje zasób do zestawu.</span><span class="sxs-lookup"><span data-stu-id="b3b54-124">When the project is built, MSBuild compiles the resource into the assembly.</span></span>  
  
### <a name="using-resource-files"></a><span data-ttu-id="b3b54-125">Korzystanie z plików zasobów</span><span class="sxs-lookup"><span data-stu-id="b3b54-125">Using Resource Files</span></span>  
 <span data-ttu-id="b3b54-126">Aby załadować plik zasobu, <xref:System.Windows.Application.GetResourceStream%2A> można <xref:System.Windows.Application> wywołać metodę klasy, przekazując identyfikator URI pakietu, który identyfikuje żądany plik zasobu.</span><span class="sxs-lookup"><span data-stu-id="b3b54-126">To load a resource file, you can call the <xref:System.Windows.Application.GetResourceStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired resource file.</span></span> <span data-ttu-id="b3b54-127"><xref:System.Windows.Application.GetResourceStream%2A>zwraca <xref:System.Windows.Resources.StreamResourceInfo> obiekt, który udostępnia plik zasobu jako <xref:System.IO.Stream> i opisuje jego typ zawartości.</span><span class="sxs-lookup"><span data-stu-id="b3b54-127"><xref:System.Windows.Application.GetResourceStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the resource file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="b3b54-128">Na przykład poniższy kod pokazuje, <xref:System.Windows.Application.GetResourceStream%2A> jak <xref:System.Windows.Controls.Page> użyć do załadowania pliku zasobu i ustawić go jako zawartość <xref:System.Windows.Controls.Frame> (`pageFrame`):</span><span class="sxs-lookup"><span data-stu-id="b3b54-128">As an example, the following code shows how to use <xref:System.Windows.Application.GetResourceStream%2A> to load a <xref:System.Windows.Controls.Page> resource file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`):</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 <span data-ttu-id="b3b54-129">Podczas <xref:System.Windows.Application.GetResourceStream%2A> wywoływania daje <xref:System.IO.Stream>dostęp do , trzeba wykonać dodatkową pracę konwersji go do typu właściwości, które będą jej ustawienie.</span><span class="sxs-lookup"><span data-stu-id="b3b54-129">While calling <xref:System.Windows.Application.GetResourceStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="b3b54-130">Zamiast tego można pozwolić WPF zadbać o <xref:System.IO.Stream> otwieranie i konwertowanie przez ładowanie pliku zasobów bezpośrednio do właściwości typu przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="b3b54-130">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="b3b54-131">W poniższym <xref:System.Windows.Controls.Page> przykładzie pokazano, jak <xref:System.Windows.Controls.Frame> `pageFrame`załadować bezpośrednio do ( ) przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="b3b54-131">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 <span data-ttu-id="b3b54-132">Poniższy przykład jest odpowiednik znaczników z poprzedniego przykładu.</span><span class="sxs-lookup"><span data-stu-id="b3b54-132">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a><span data-ttu-id="b3b54-133">Pliki kodu aplikacji jako pliki zasobów</span><span class="sxs-lookup"><span data-stu-id="b3b54-133">Application Code Files as Resource Files</span></span>  
 <span data-ttu-id="b3b54-134">Specjalny zestaw plików kodu aplikacji WPF można odwoływać się za pomocą URI pakietu, w tym okna, strony, dokumenty przepływu i słowniki zasobów.</span><span class="sxs-lookup"><span data-stu-id="b3b54-134">A special set of WPF application code files can be referenced using pack URIs, including windows, pages, flow documents, and resource dictionaries.</span></span> <span data-ttu-id="b3b54-135">Na przykład można ustawić <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> właściwość z identyfikatorem URI pakietu, który odwołuje się do okna lub strony, które chcesz załadować po uruchomieniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b3b54-135">For example, you can set the <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> property with a pack URI that references the window or page that you would like to load when an application starts.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 <span data-ttu-id="b3b54-136">Można to zrobić, gdy plik XAML jest zawarty w projekcie `Page` MSBuild jako element.</span><span class="sxs-lookup"><span data-stu-id="b3b54-136">You can do this when a XAML file is included in an MSBuild project as a `Page` item.</span></span>  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Page Include="MainWindow.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
> <span data-ttu-id="b3b54-137">W programie Visual Studio <xref:System.Windows.Window>dodasz <xref:System.Windows.Controls.Page> <xref:System.Windows.Documents.FlowDocument>nowe <xref:System.Windows.ResourceDictionary> , <xref:System.Windows.Navigation.NavigationWindow>, , `Build Action` lub do projektu, `Page`dla pliku znaczników domyślnie .</span><span class="sxs-lookup"><span data-stu-id="b3b54-137">In Visual Studio, you add a new <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>, or <xref:System.Windows.ResourceDictionary> to a project, the `Build Action` for the markup file will default to `Page`.</span></span>  
  
 <span data-ttu-id="b3b54-138">Podczas kompilacji `Page` projektu z elementami [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementy są konwertowane na format binarny i kompilowane do skojarzonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="b3b54-138">When a project with `Page` items is compiled, the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] items are converted to binary format and compiled into the associated assembly.</span></span> <span data-ttu-id="b3b54-139">W związku z tym pliki te mogą być używane w taki sam sposób jak typowe pliki zasobów.</span><span class="sxs-lookup"><span data-stu-id="b3b54-139">Consequently, these files can be used in the same way as typical resource files.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3b54-140">Jeśli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plik jest skonfigurowany `Resource` jako element i nie ma pliku zawierającego kod, plik raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest kompilowany [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]do zestawu, a nie w wersji binarnej pliku raw .</span><span class="sxs-lookup"><span data-stu-id="b3b54-140">If a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is configured as a `Resource` item, and does not have a code-behind file, the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is compiled into an assembly rather than a binary version of the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
<a name="Content_Files"></a>
## <a name="content-files"></a><span data-ttu-id="b3b54-141">Pliki zawartości</span><span class="sxs-lookup"><span data-stu-id="b3b54-141">Content Files</span></span>  
 <span data-ttu-id="b3b54-142">*Plik zawartości* jest rozprowadzany jako luźny plik obok zestawu wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="b3b54-142">A *content file* is distributed as a loose file alongside an executable assembly.</span></span> <span data-ttu-id="b3b54-143">Chociaż nie są one kompilowane do zestawu, zestawy są kompilowane z metadanymi, które ustanawia skojarzenia z każdego pliku zawartości.</span><span class="sxs-lookup"><span data-stu-id="b3b54-143">Although they are not compiled into an assembly, assemblies are compiled with metadata that establishes an association with each content file.</span></span>  
  
 <span data-ttu-id="b3b54-144">Pliki zawartości należy używać, gdy aplikacja wymaga określonego zestawu plików danych aplikacji, które mają być w stanie zaktualizować bez ponownego komppilowania zestawu, który zużywa je.</span><span class="sxs-lookup"><span data-stu-id="b3b54-144">You should use content files when your application requires a specific set of application data files that you want to be able to update without recompiling the assembly that consumes them.</span></span>  
  
### <a name="configuring-content-files"></a><span data-ttu-id="b3b54-145">Konfigurowanie plików zawartości</span><span class="sxs-lookup"><span data-stu-id="b3b54-145">Configuring Content Files</span></span>  
 <span data-ttu-id="b3b54-146">Aby dodać plik zawartości do projektu, plik danych aplikacji `Content` musi być dołączony jako element.</span><span class="sxs-lookup"><span data-stu-id="b3b54-146">To add a content file to a project, an application data file must be included as a `Content` item.</span></span> <span data-ttu-id="b3b54-147">Ponadto ponieważ plik zawartości nie jest kompilowany bezpośrednio do zestawu, należy ustawić `CopyToOutputDirectory` element metadanych MSBuild, aby określić, że plik zawartości jest kopiowany do lokalizacji, która jest względem zestawu wbudowanego.</span><span class="sxs-lookup"><span data-stu-id="b3b54-147">Furthermore, because a content file is not compiled directly into the assembly, you need to set the MSBuild `CopyToOutputDirectory` metadata element to specify that the content file is copied to a location that is relative to the built assembly.</span></span> <span data-ttu-id="b3b54-148">Jeśli chcesz, aby zasób był kopiowany do folderu wyjściowego `CopyToOutputDirectory` kompilacji za `Always` każdym razem, gdy projekt jest zbudowany, należy ustawić element metadanych z wartością.</span><span class="sxs-lookup"><span data-stu-id="b3b54-148">If you want the resource to be copied to the build output folder every time a project is built, you set the `CopyToOutputDirectory` metadata element with the `Always` value.</span></span> <span data-ttu-id="b3b54-149">W przeciwnym razie można upewnić się, że tylko najnowsza wersja zasobu jest kopiowana do folderu wyjściowego kompilacji `PreserveNewest` przy użyciu wartości.</span><span class="sxs-lookup"><span data-stu-id="b3b54-149">Otherwise, you can ensure that only the newest version of the resource is copied to the build output folder by using the `PreserveNewest` value.</span></span>  
  
 <span data-ttu-id="b3b54-150">Poniżej przedstawiono plik, który jest skonfigurowany jako plik zawartości, który jest kopiowany do folderu wyjściowego kompilacji tylko wtedy, gdy nowa wersja zasobu jest dodawany do projektu.</span><span class="sxs-lookup"><span data-stu-id="b3b54-150">The following shows a file that is configured as a content file which is copied to the build output folder only when a new version of the resource is added to the project.</span></span>  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Content Include="ContentFile.xaml">  
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
    </Content>  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
> <span data-ttu-id="b3b54-151">W programie Visual Studio plik zawartości jest tworzę, `Build Action` dodając `Content`plik do `Copy to Output Directory` `Copy always` projektu i `Always`ustawiając go na , i ustawiając go na (tak samo jak ) i `Copy if newer` (tak samo jak `PreserveNewest`).</span><span class="sxs-lookup"><span data-stu-id="b3b54-151">In Visual Studio, you create a content file by adding a file to a project and setting its `Build Action` to `Content`, and set its `Copy to Output Directory` to `Copy always` (same as `Always`) and `Copy if newer` (same as `PreserveNewest`).</span></span>  
  
 <span data-ttu-id="b3b54-152">Po zbudowaniu projektu <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atrybut jest kompilowany do metadanych zestawu dla każdego pliku zawartości.</span><span class="sxs-lookup"><span data-stu-id="b3b54-152">When the project is built, an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is compiled into the metadata of the assembly for each content file.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 <span data-ttu-id="b3b54-153">Wartość oznacza <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> ścieżkę do pliku zawartości w stosunku do jego pozycji w projekcie.</span><span class="sxs-lookup"><span data-stu-id="b3b54-153">The value of the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implies the path to the content file relative to its position in the project.</span></span> <span data-ttu-id="b3b54-154">Na przykład jeśli plik zawartości znajdował się w podfolderze projektu, dodatkowe <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> informacje o ścieżce zostaną włączone do wartości.</span><span class="sxs-lookup"><span data-stu-id="b3b54-154">For example, if a content file was located in a project subfolder, the additional path information would be incorporated into the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <span data-ttu-id="b3b54-155">Wartość <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> jest również wartością ścieżki do pliku zawartości w folderze wyjściowym kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b3b54-155">The <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value is also the value of the path to the content file in the build output folder.</span></span>  
  
### <a name="using-content-files"></a><span data-ttu-id="b3b54-156">Korzystanie z plików zawartości</span><span class="sxs-lookup"><span data-stu-id="b3b54-156">Using Content Files</span></span>  
 <span data-ttu-id="b3b54-157">Aby załadować plik zawartości, <xref:System.Windows.Application.GetContentStream%2A> można wywołać metodę <xref:System.Windows.Application> klasy, przekazując pakiet URI, który identyfikuje żądany plik zawartości.</span><span class="sxs-lookup"><span data-stu-id="b3b54-157">To load a content file, you can call the <xref:System.Windows.Application.GetContentStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired content file.</span></span> <span data-ttu-id="b3b54-158"><xref:System.Windows.Application.GetContentStream%2A>zwraca <xref:System.Windows.Resources.StreamResourceInfo> obiekt, który udostępnia plik zawartości <xref:System.IO.Stream> jako i opisuje jego typ zawartości.</span><span class="sxs-lookup"><span data-stu-id="b3b54-158"><xref:System.Windows.Application.GetContentStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the content file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="b3b54-159">Na przykład poniższy kod pokazuje, <xref:System.Windows.Application.GetContentStream%2A> jak <xref:System.Windows.Controls.Page> użyć do załadowania pliku zawartości <xref:System.Windows.Controls.Frame> `pageFrame`i ustawić go jako zawartość ( ).</span><span class="sxs-lookup"><span data-stu-id="b3b54-159">As an example, the following code shows how to use <xref:System.Windows.Application.GetContentStream%2A> to load a <xref:System.Windows.Controls.Page> content file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 <span data-ttu-id="b3b54-160">Podczas <xref:System.Windows.Application.GetContentStream%2A> wywoływania daje <xref:System.IO.Stream>dostęp do , trzeba wykonać dodatkową pracę konwersji go do typu właściwości, które będą jej ustawienie.</span><span class="sxs-lookup"><span data-stu-id="b3b54-160">While calling <xref:System.Windows.Application.GetContentStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="b3b54-161">Zamiast tego można pozwolić WPF zadbać o <xref:System.IO.Stream> otwieranie i konwertowanie przez ładowanie pliku zasobów bezpośrednio do właściwości typu przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="b3b54-161">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="b3b54-162">W poniższym <xref:System.Windows.Controls.Page> przykładzie pokazano, jak <xref:System.Windows.Controls.Frame> `pageFrame`załadować bezpośrednio do ( ) przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="b3b54-162">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 <span data-ttu-id="b3b54-163">Poniższy przykład jest odpowiednik znaczników z poprzedniego przykładu.</span><span class="sxs-lookup"><span data-stu-id="b3b54-163">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>
## <a name="site-of-origin-files"></a><span data-ttu-id="b3b54-164">Pliki witryny pochodzenia</span><span class="sxs-lookup"><span data-stu-id="b3b54-164">Site of Origin Files</span></span>  
 <span data-ttu-id="b3b54-165">Pliki zasobów mają jawną relację z zestawami, które są <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>dystrybuowane obok, zgodnie z definicją .</span><span class="sxs-lookup"><span data-stu-id="b3b54-165">Resource files have an explicit relationship with the assemblies that they are distributed alongside, as defined by the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>.</span></span> <span data-ttu-id="b3b54-166">Ale są chwile, kiedy można ustanowić niejawną lub nieistniejącą relację między zestawem a plikiem danych aplikacji, w tym gdy:</span><span class="sxs-lookup"><span data-stu-id="b3b54-166">But, there are times when you may want to establish either an implicit or non-existent relationship between an assembly and an application data file, including when:</span></span>  
  
- <span data-ttu-id="b3b54-167">Plik nie istnieje w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b3b54-167">A file doesn't exist at compile time.</span></span>  
  
- <span data-ttu-id="b3b54-168">Nie wiesz, jakie pliki będzie wymagać zestawu do czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b3b54-168">You don't know what files your assembly will require until run time.</span></span>  
  
- <span data-ttu-id="b3b54-169">Chcesz mieć możliwość aktualizowania plików bez ponownego komppilowania zestawu, z którego są skojarzone.</span><span class="sxs-lookup"><span data-stu-id="b3b54-169">You want to be able to update files without recompiling the assembly that they are associated with.</span></span>  
  
- <span data-ttu-id="b3b54-170">Aplikacja używa dużych plików danych, takich jak audio i wideo, i chcesz, aby użytkownicy mogli je pobrać tylko wtedy, gdy zechcą.</span><span class="sxs-lookup"><span data-stu-id="b3b54-170">Your application uses large data files, such as audio and video, and you only want users to download them if they choose to.</span></span>  
  
 <span data-ttu-id="b3b54-171">Istnieje możliwość ładowania tego typu plików przy użyciu tradycyjnych schematów URI, takich jak schematy file:/// i http://.</span><span class="sxs-lookup"><span data-stu-id="b3b54-171">It is possible to load these types of files by using traditional URI schemes, such as the file:/// and http:// schemes.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 <span data-ttu-id="b3b54-172">Jednak schematy file:/// i http:// wymagają pełnego zaufania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b3b54-172">However, the file:/// and http:// schemes require your application to have full trust.</span></span> <span data-ttu-id="b3b54-173">Jeśli aplikacja jest aplikacją przeglądarki XAML (XBAP), która została uruchomiona z Internetu lub intranetu i żąda tylko zestawu uprawnień, które są dozwolone dla aplikacji uruchomionych z tych lokalizacji, luźne pliki można załadować tylko z miejsca pochodzenia aplikacji (miejsce uruchomienia).</span><span class="sxs-lookup"><span data-stu-id="b3b54-173">If your application is a XAML browser application (XBAP) that was launched from the Internet or intranet, and it requests only the set of permissions that are allowed for applications launched from those locations, loose files can only be loaded from the application's site of origin (launch location).</span></span> <span data-ttu-id="b3b54-174">Takie pliki są znane jako *pliki witryny pochodzenia.*</span><span class="sxs-lookup"><span data-stu-id="b3b54-174">Such files are known as *site of origin* files.</span></span>  
  
 <span data-ttu-id="b3b54-175">Pliki lokacji pochodzenia są jedyną opcją dla aplikacji częściowego zaufania, chociaż nie są ograniczone do aplikacji częściowego zaufania.</span><span class="sxs-lookup"><span data-stu-id="b3b54-175">Site of origin files are the only option for partial trust applications, although are not limited to partial trust applications.</span></span> <span data-ttu-id="b3b54-176">Pełne zaufanie aplikacji może nadal trzeba załadować pliki danych aplikacji, które nie wiedzą o w czasie kompilacji; podczas gdy aplikacje pełnego zaufania mogą używać file:///, jest prawdopodobne, że pliki danych aplikacji zostaną zainstalowane w tym samym folderze, w którym lub podfolderze zestawu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b3b54-176">Full trust applications may still need to load application data files that they do not know about at build time; while full trust applications could use file:///, it is likely that the application data files will be installed in the same folder as, or a subfolder of, the application assembly.</span></span> <span data-ttu-id="b3b54-177">W takim przypadku korzystanie z odwołów do witryny pochodzenia jest łatwiejsze niż używanie file:///, ponieważ użycie file:/// wymaga wypracowywania pełnej ścieżki pliku.</span><span class="sxs-lookup"><span data-stu-id="b3b54-177">In this case, using site of origin referencing is easier than using file:///, because using file:/// requires you to work out the full path the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3b54-178">Pliki witryny pochodzenia nie są buforowane za pomocą aplikacji przeglądarki XAML (XBAP) na komputerze klienckim, podczas gdy pliki zawartości są.</span><span class="sxs-lookup"><span data-stu-id="b3b54-178">Site of origin files are not cached with an XAML browser application (XBAP) on a client machine, while content files are.</span></span> <span data-ttu-id="b3b54-179">W związku z tym są one pobierane tylko wtedy, gdy jest to wyraźnie wymagane.</span><span class="sxs-lookup"><span data-stu-id="b3b54-179">Consequently, they are only downloaded when specifically requested.</span></span> <span data-ttu-id="b3b54-180">Jeśli aplikacja przeglądarki XAML (XBAP) ma duże pliki multimedialne, skonfigurowanie ich jako plików lokacji pochodzenia oznacza, że początkowe uruchomienie aplikacji jest znacznie szybsze, a pliki są pobierane tylko na żądanie.</span><span class="sxs-lookup"><span data-stu-id="b3b54-180">If an XAML browser application (XBAP) application has large media files, configuring them as site of origin files means the initial application launch is much faster, and the files are only downloaded on demand.</span></span>  
  
### <a name="configuring-site-of-origin-files"></a><span data-ttu-id="b3b54-181">Konfigurowanie plików witryny pochodzenia</span><span class="sxs-lookup"><span data-stu-id="b3b54-181">Configuring Site of Origin Files</span></span>  
 <span data-ttu-id="b3b54-182">Jeśli pliki witryny pochodzenia nie istnieją lub są nieznane w czasie kompilacji, należy użyć tradycyjnych mechanizmów wdrażania w celu `XCopy` zapewnienia, że wymagane pliki są dostępne w czasie wykonywania, w tym przy użyciu programu wiersza polecenia lub Instalatora Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="b3b54-182">If your site of origin files are non-existent or unknown at compile time, you need to use traditional deployment mechanisms for ensuring the required files are available at run time, including using either the `XCopy` command-line program or the Microsoft Windows Installer.</span></span>  
  
 <span data-ttu-id="b3b54-183">Jeśli wiesz, w czasie kompilacji pliki, które mają być zlokalizowane w witrynie pochodzenia, ale nadal chcesz uniknąć jawnej zależności, `None` można dodać te pliki do projektu MSBuild jako element.</span><span class="sxs-lookup"><span data-stu-id="b3b54-183">If you do know at compile time the files that you would like to be located at the site of origin, but still want to avoid an explicit dependency, you can add those files to an MSBuild project as `None` item.</span></span> <span data-ttu-id="b3b54-184">Podobnie jak w plikach zawartości, należy `CopyToOutputDirectory` ustawić atrybut MSBuild, aby określić, że plik lokacji pochodzenia jest kopiowany `Always` do lokalizacji, która jest względem zestawu wbudowanego, określając wartość lub `PreserveNewest` wartość.</span><span class="sxs-lookup"><span data-stu-id="b3b54-184">As with content files, you need to set the MSBuild `CopyToOutputDirectory` attribute to specify that the site of origin file is copied to a location that is relative to the built assembly, by specifying either the `Always` value or the `PreserveNewest` value.</span></span>  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <None Include="PageSiteOfOriginFile.xaml">  
    <CopyToOutputDirectory>Always</CopyToOutputDirectory>  
  </None>  
  ...  
</Project>  
```  
  
> [!NOTE]
> <span data-ttu-id="b3b54-185">W programie Visual Studio plik witryny pochodzenia można utworzyć, dodając `Build Action` `None`plik do projektu i ustawiając go na .</span><span class="sxs-lookup"><span data-stu-id="b3b54-185">In Visual Studio, you create a site of origin file by adding a file to a project and setting its `Build Action` to `None`.</span></span>  
  
 <span data-ttu-id="b3b54-186">Po utworzeniu projektu MSBuild kopiuje określone pliki do folderu wyjściowego kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b3b54-186">When the project is built, MSBuild copies the specified files to the build output folder.</span></span>  
  
### <a name="using-site-of-origin-files"></a><span data-ttu-id="b3b54-187">Korzystanie z plików witryny pochodzenia</span><span class="sxs-lookup"><span data-stu-id="b3b54-187">Using Site of Origin Files</span></span>  
 <span data-ttu-id="b3b54-188">Aby załadować plik witryny pochodzenia, <xref:System.Windows.Application.GetRemoteStream%2A> można <xref:System.Windows.Application> wywołać metodę klasy, przekazując pakiet URI, który identyfikuje żądaną witrynę pliku pochodzenia.</span><span class="sxs-lookup"><span data-stu-id="b3b54-188">To load a site of origin file, you can call the <xref:System.Windows.Application.GetRemoteStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired site of origin file.</span></span> <span data-ttu-id="b3b54-189"><xref:System.Windows.Application.GetRemoteStream%2A>zwraca <xref:System.Windows.Resources.StreamResourceInfo> obiekt, który udostępnia plik witryny <xref:System.IO.Stream> pochodzenia jako i opisuje jego typ zawartości.</span><span class="sxs-lookup"><span data-stu-id="b3b54-189"><xref:System.Windows.Application.GetRemoteStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the site of origin file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="b3b54-190">Na przykład poniższy kod pokazuje, <xref:System.Windows.Application.GetRemoteStream%2A> jak <xref:System.Windows.Controls.Page> użyć do załadowania pliku witryny <xref:System.Windows.Controls.Frame> pochodzenia`pageFrame`i ustawić go jako zawartość ( ).</span><span class="sxs-lookup"><span data-stu-id="b3b54-190">As an example, the following code shows how to use <xref:System.Windows.Application.GetRemoteStream%2A> to load a <xref:System.Windows.Controls.Page> site of origin file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 <span data-ttu-id="b3b54-191">Podczas <xref:System.Windows.Application.GetRemoteStream%2A> wywoływania daje <xref:System.IO.Stream>dostęp do , trzeba wykonać dodatkową pracę konwersji go do typu właściwości, które będą jej ustawienie.</span><span class="sxs-lookup"><span data-stu-id="b3b54-191">While calling <xref:System.Windows.Application.GetRemoteStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="b3b54-192">Zamiast tego można pozwolić WPF zadbać o <xref:System.IO.Stream> otwieranie i konwertowanie przez ładowanie pliku zasobów bezpośrednio do właściwości typu przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="b3b54-192">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="b3b54-193">W poniższym <xref:System.Windows.Controls.Page> przykładzie pokazano, jak <xref:System.Windows.Controls.Frame> `pageFrame`załadować bezpośrednio do ( ) przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="b3b54-193">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 <span data-ttu-id="b3b54-194">Poniższy przykład jest odpowiednik znaczników z poprzedniego przykładu.</span><span class="sxs-lookup"><span data-stu-id="b3b54-194">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>
## <a name="rebuilding-after-changing-build-type"></a><span data-ttu-id="b3b54-195">Przebudowa po zmianie typu kompilacji</span><span class="sxs-lookup"><span data-stu-id="b3b54-195">Rebuilding After Changing Build Type</span></span>  
 <span data-ttu-id="b3b54-196">Po zmianie typu kompilacji pliku danych aplikacji, należy odbudować całą aplikację, aby upewnić się, że te zmiany są stosowane.</span><span class="sxs-lookup"><span data-stu-id="b3b54-196">After you change the build type of an application data file, you need to rebuild the entire application to ensure those changes are applied.</span></span> <span data-ttu-id="b3b54-197">Jeśli tylko utworzyć aplikację, zmiany nie są stosowane.</span><span class="sxs-lookup"><span data-stu-id="b3b54-197">If you only build the application, the changes are not applied.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3b54-198">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b3b54-198">See also</span></span>

- [<span data-ttu-id="b3b54-199">Pakuj URI w WPF</span><span class="sxs-lookup"><span data-stu-id="b3b54-199">Pack URIs in WPF</span></span>](pack-uris-in-wpf.md)
