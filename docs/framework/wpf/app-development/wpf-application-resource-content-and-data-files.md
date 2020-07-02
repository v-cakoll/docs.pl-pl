---
title: Zasób aplikacji, zawartość i pliki danych
description: Dowiedz się więcej o specjalnej obsłudze dotyczącej konfigurowania, identyfikowania i używania plików danych aplikacji w programie Windows Presentation Foundation (WPF).
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
ms.openlocfilehash: 324b3eb922f0fd1d1d9ad00105a06a7fbdb8effd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622864"
---
# <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="a010c-103">Zasoby aplikacji WPF, zawartość, pliki danych</span><span class="sxs-lookup"><span data-stu-id="a010c-103">WPF Application Resource, Content, and Data Files</span></span>
<span data-ttu-id="a010c-104">Aplikacje Microsoft Windows często zależą od plików, które zawierają dane niewykonywalne, takie jak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] obrazy, wideo i dźwięk.</span><span class="sxs-lookup"><span data-stu-id="a010c-104">Microsoft Windows applications often depend on files that contain non-executable data, such as [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], images, video, and audio.</span></span> <span data-ttu-id="a010c-105">Windows Presentation Foundation (WPF) oferuje specjalną obsługę konfigurowania, identyfikowania i korzystania z tych typów plików danych, które są nazywane plikami danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a010c-105">Windows Presentation Foundation (WPF) offers special support for configuring, identifying, and using these types of data files, which are called application data files.</span></span> <span data-ttu-id="a010c-106">Ta obsługa dotyczy określonego zestawu typów plików danych aplikacji, w tym:</span><span class="sxs-lookup"><span data-stu-id="a010c-106">This support revolves around a specific set of application data file types, including:</span></span>  
  
- <span data-ttu-id="a010c-107">**Pliki zasobów**: pliki danych, które są kompilowane do pliku wykonywalnego lub zestawu WPF Library.</span><span class="sxs-lookup"><span data-stu-id="a010c-107">**Resource Files**: Data files that are compiled into either an executable or library WPF assembly.</span></span>  
  
- <span data-ttu-id="a010c-108">**Pliki zawartości**: autonomiczne pliki danych z jawnym skojarzeniem z wykonywalnym zestawem WPF.</span><span class="sxs-lookup"><span data-stu-id="a010c-108">**Content Files**: Standalone data files that have an explicit association with an executable WPF assembly.</span></span>  
  
- <span data-ttu-id="a010c-109">**Lokacja plików pochodzenia**: autonomiczne pliki danych, które nie mają skojarzenia z wykonywalnym zestawem WPF.</span><span class="sxs-lookup"><span data-stu-id="a010c-109">**Site of Origin Files**: Standalone data files that have no association with an executable WPF assembly.</span></span>  
  
 <span data-ttu-id="a010c-110">Jednym z ważnych różnic między tymi trzema typami plików jest to, że pliki zasobów i zawartości są znane w czasie kompilacji; zestaw ma jawną wiedzę o nich.</span><span class="sxs-lookup"><span data-stu-id="a010c-110">One important distinction to make between these three types of files is that resource files and content files are known at build time; an assembly has explicit knowledge of them.</span></span> <span data-ttu-id="a010c-111">Jednak w przypadku lokacji z plikami pochodzenia zestaw może nie mieć w ogóle informacji o nich ani niejawnej wiedzy za pomocą odwołania URI (Uniform Resource Identifier). w przypadku tej ostatniej nie ma gwarancji, że w rzeczywistości istnieje przywoływana lokacja pliku pierwotnego.</span><span class="sxs-lookup"><span data-stu-id="a010c-111">For site of origin files, however, an assembly may have no knowledge of them at all, or implicit knowledge through a pack uniform resource identifier (URI) reference; the case of the latter, there is no guarantee that the referenced site of origin file actually exists.</span></span>  
  
 <span data-ttu-id="a010c-112">Aby odwoływać się do plików danych aplikacji, Windows Presentation Foundation (WPF) używa schematu identyfikatora URI (Uniform Resource Identifier), który jest szczegółowo opisany w artykule [identyfikatory URI pakietu w WPF](pack-uris-in-wpf.md)).</span><span class="sxs-lookup"><span data-stu-id="a010c-112">To reference application data files, Windows Presentation Foundation (WPF) uses the Pack uniform resource identifier (URI) Scheme, which is described in detail in [Pack URIs in WPF](pack-uris-in-wpf.md)).</span></span>  
  
 <span data-ttu-id="a010c-113">W tym temacie opisano sposób konfigurowania plików danych aplikacji i korzystania z nich.</span><span class="sxs-lookup"><span data-stu-id="a010c-113">This topic describes how to configure and use application data files.</span></span>  

<a name="Resource_Files"></a>
## <a name="resource-files"></a><span data-ttu-id="a010c-114">Pliki zasobów</span><span class="sxs-lookup"><span data-stu-id="a010c-114">Resource Files</span></span>  
 <span data-ttu-id="a010c-115">Jeśli plik danych aplikacji musi być zawsze dostępny dla aplikacji, jedynym sposobem na zagwarantowanie dostępności jest skompilowanie go do głównego zestawu wykonywalnego aplikacji lub jednego z zestawów, do których się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="a010c-115">If an application data file must always be available to an application, the only way to guarantee availability is to compile it into an application's main executable assembly or one of its referenced assemblies.</span></span> <span data-ttu-id="a010c-116">Ten typ pliku danych aplikacji jest znany jako *plik zasobów*.</span><span class="sxs-lookup"><span data-stu-id="a010c-116">This type of application data file is known as a *resource file*.</span></span>  
  
 <span data-ttu-id="a010c-117">Plików zasobów należy używać w programie:</span><span class="sxs-lookup"><span data-stu-id="a010c-117">You should use resource files when:</span></span>  
  
- <span data-ttu-id="a010c-118">Nie trzeba aktualizować zawartości pliku zasobów po skompilowaniu jej do zestawu.</span><span class="sxs-lookup"><span data-stu-id="a010c-118">You don't need to update the resource file's content after it is compiled into an assembly.</span></span>  
  
- <span data-ttu-id="a010c-119">Chcesz uprościć złożoność dystrybucji aplikacji, zmniejszając liczbę zależności między plikami.</span><span class="sxs-lookup"><span data-stu-id="a010c-119">You want to simplify application distribution complexity by reducing the number of file dependencies.</span></span>  
  
- <span data-ttu-id="a010c-120">Plik danych aplikacji musi być Lokalizowalny (zobacz [Omówienie globalizacji i lokalizacji platformy WPF](../advanced/wpf-globalization-and-localization-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="a010c-120">Your application data file needs to be localizable (see [WPF Globalization and Localization Overview](../advanced/wpf-globalization-and-localization-overview.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a010c-121">Pliki zasobów opisane w tej sekcji są inne niż pliki zasobów opisane w obszarze [zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md) i różne od osadzonych lub połączonych zasobów opisanych w temacie [Zarządzanie zasobami aplikacji (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="a010c-121">The resource files described in this section are different than the resource files described in [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) and different than the embedded or linked resources described in [Manage Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
### <a name="configuring-resource-files"></a><span data-ttu-id="a010c-122">Konfigurowanie plików zasobów</span><span class="sxs-lookup"><span data-stu-id="a010c-122">Configuring Resource Files</span></span>  
 <span data-ttu-id="a010c-123">W WPF, plik zasobów jest plikiem, który jest zawarty w projekcie Microsoft Build Engine (MSBuild) jako `Resource` element.</span><span class="sxs-lookup"><span data-stu-id="a010c-123">In WPF, a resource file is a file that is included in an Microsoft build engine (MSBuild) project as a `Resource` item.</span></span>  
  
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
> <span data-ttu-id="a010c-124">W programie Visual Studio tworzysz plik zasobów przez dodanie pliku do projektu i ustawienie jego `Build Action` na `Resource` .</span><span class="sxs-lookup"><span data-stu-id="a010c-124">In Visual Studio, you create a resource file by adding a file to a project and setting its `Build Action` to `Resource`.</span></span>  
  
 <span data-ttu-id="a010c-125">Po skompilowaniu projektu MSBuild kompiluje zasób do zestawu.</span><span class="sxs-lookup"><span data-stu-id="a010c-125">When the project is built, MSBuild compiles the resource into the assembly.</span></span>  
  
### <a name="using-resource-files"></a><span data-ttu-id="a010c-126">Korzystanie z plików zasobów</span><span class="sxs-lookup"><span data-stu-id="a010c-126">Using Resource Files</span></span>  
 <span data-ttu-id="a010c-127">Aby załadować plik zasobów, można wywołać <xref:System.Windows.Application.GetResourceStream%2A> metodę <xref:System.Windows.Application> klasy, przekazując identyfikator URI pakietu, który identyfikuje żądany plik zasobów.</span><span class="sxs-lookup"><span data-stu-id="a010c-127">To load a resource file, you can call the <xref:System.Windows.Application.GetResourceStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired resource file.</span></span> <span data-ttu-id="a010c-128"><xref:System.Windows.Application.GetResourceStream%2A>zwraca <xref:System.Windows.Resources.StreamResourceInfo> obiekt, który udostępnia plik zasobu jako <xref:System.IO.Stream> i opisuje jego typ zawartości.</span><span class="sxs-lookup"><span data-stu-id="a010c-128"><xref:System.Windows.Application.GetResourceStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the resource file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="a010c-129">Na przykład poniższy kod pokazuje, jak użyć <xref:System.Windows.Application.GetResourceStream%2A> do załadowania <xref:System.Windows.Controls.Page> pliku zasobów i ustawienia go jako zawartości <xref:System.Windows.Controls.Frame> ( `pageFrame` ):</span><span class="sxs-lookup"><span data-stu-id="a010c-129">As an example, the following code shows how to use <xref:System.Windows.Application.GetResourceStream%2A> to load a <xref:System.Windows.Controls.Page> resource file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`):</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 <span data-ttu-id="a010c-130">Podczas gdy wywoływanie <xref:System.Windows.Application.GetResourceStream%2A> daje dostęp do <xref:System.IO.Stream> , należy wykonać dodatkową ilość pracy, aby przekonwertować ją na typ właściwości, z którą zostanie ona ustawiona.</span><span class="sxs-lookup"><span data-stu-id="a010c-130">While calling <xref:System.Windows.Application.GetResourceStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="a010c-131">Zamiast tego można zezwolić platformie WPF na otwieranie i konwertowanie <xref:System.IO.Stream> przez załadowanie pliku zasobów bezpośrednio do właściwości typu za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="a010c-131">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="a010c-132">Poniższy przykład pokazuje, jak załadować element <xref:System.Windows.Controls.Page> bezpośrednio do <xref:System.Windows.Controls.Frame> ( `pageFrame` ) za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="a010c-132">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 <span data-ttu-id="a010c-133">Poniższy przykład jest odpowiednikiem znaczników z poprzedniego przykładu.</span><span class="sxs-lookup"><span data-stu-id="a010c-133">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a><span data-ttu-id="a010c-134">Pliki kodu aplikacji jako pliki zasobów</span><span class="sxs-lookup"><span data-stu-id="a010c-134">Application Code Files as Resource Files</span></span>  
 <span data-ttu-id="a010c-135">Do specjalnego zestawu plików kodu aplikacji WPF można odwoływać się za pomocą identyfikatorów URI pakietów, takich jak Windows, strony, dokumenty przepływu i słowniki zasobów.</span><span class="sxs-lookup"><span data-stu-id="a010c-135">A special set of WPF application code files can be referenced using pack URIs, including windows, pages, flow documents, and resource dictionaries.</span></span> <span data-ttu-id="a010c-136">Na przykład można ustawić <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> Właściwość z identyfikatorem URI pakietu, który odwołuje się do okna lub strony, które chcesz załadować podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a010c-136">For example, you can set the <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> property with a pack URI that references the window or page that you would like to load when an application starts.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 <span data-ttu-id="a010c-137">Można to zrobić, gdy plik XAML jest zawarty w projekcie MSBuild jako `Page` element.</span><span class="sxs-lookup"><span data-stu-id="a010c-137">You can do this when a XAML file is included in an MSBuild project as a `Page` item.</span></span>  
  
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
> <span data-ttu-id="a010c-138">W programie Visual Studio można dodać nowy <xref:System.Windows.Window> , <xref:System.Windows.Navigation.NavigationWindow> ,, <xref:System.Windows.Controls.Page> <xref:System.Windows.Documents.FlowDocument> lub <xref:System.Windows.ResourceDictionary> do projektu, `Build Action` dla którego plik znaczników będzie domyślnie `Page` .</span><span class="sxs-lookup"><span data-stu-id="a010c-138">In Visual Studio, you add a new <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>, or <xref:System.Windows.ResourceDictionary> to a project, the `Build Action` for the markup file will default to `Page`.</span></span>  
  
 <span data-ttu-id="a010c-139">Po `Page` skompilowaniu projektu z elementami elementy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] są konwertowane na format binarny i kompilowane w skojarzonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="a010c-139">When a project with `Page` items is compiled, the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] items are converted to binary format and compiled into the associated assembly.</span></span> <span data-ttu-id="a010c-140">W związku z tym te pliki mogą być używane w taki sam sposób jak w przypadku typowych plików zasobów.</span><span class="sxs-lookup"><span data-stu-id="a010c-140">Consequently, these files can be used in the same way as typical resource files.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a010c-141">Jeśli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plik jest skonfigurowany jako `Resource` element i nie ma pliku związanego z kodem, pierwotny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest kompilowany do zestawu, a nie do wersji binarnej RAW [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a010c-141">If a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is configured as a `Resource` item, and does not have a code-behind file, the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is compiled into an assembly rather than a binary version of the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
<a name="Content_Files"></a>
## <a name="content-files"></a><span data-ttu-id="a010c-142">Pliki zawartości</span><span class="sxs-lookup"><span data-stu-id="a010c-142">Content Files</span></span>  
 <span data-ttu-id="a010c-143">*Plik zawartości* jest dystrybuowany jako luźny plik obok zestawu wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="a010c-143">A *content file* is distributed as a loose file alongside an executable assembly.</span></span> <span data-ttu-id="a010c-144">Chociaż nie są one kompilowane do zestawu, zestawy są kompilowane za pomocą metadanych, które tworzą skojarzenie z każdym plikiem zawartości.</span><span class="sxs-lookup"><span data-stu-id="a010c-144">Although they are not compiled into an assembly, assemblies are compiled with metadata that establishes an association with each content file.</span></span>  
  
 <span data-ttu-id="a010c-145">Plików zawartości należy używać, gdy aplikacja wymaga określonego zestawu plików danych aplikacji, które mają być w stanie aktualizować bez ponownego kompilowania zestawu, który go używa.</span><span class="sxs-lookup"><span data-stu-id="a010c-145">You should use content files when your application requires a specific set of application data files that you want to be able to update without recompiling the assembly that consumes them.</span></span>  
  
### <a name="configuring-content-files"></a><span data-ttu-id="a010c-146">Konfigurowanie plików zawartości</span><span class="sxs-lookup"><span data-stu-id="a010c-146">Configuring Content Files</span></span>  
 <span data-ttu-id="a010c-147">Aby dodać plik zawartości do projektu, plik danych aplikacji musi być dołączony jako `Content` element.</span><span class="sxs-lookup"><span data-stu-id="a010c-147">To add a content file to a project, an application data file must be included as a `Content` item.</span></span> <span data-ttu-id="a010c-148">Ponadto, ponieważ plik zawartości nie jest kompilowany bezpośrednio do zestawu, należy ustawić `CopyToOutputDirectory` element metadanych MSBuild, aby określić, że plik zawartości jest kopiowany do lokalizacji względnej dla skompilowanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="a010c-148">Furthermore, because a content file is not compiled directly into the assembly, you need to set the MSBuild `CopyToOutputDirectory` metadata element to specify that the content file is copied to a location that is relative to the built assembly.</span></span> <span data-ttu-id="a010c-149">Jeśli zasób ma być kopiowany do folderu danych wyjściowych kompilacji przy każdym skompilowaniu projektu, należy ustawić `CopyToOutputDirectory` element metadanych z `Always` wartością.</span><span class="sxs-lookup"><span data-stu-id="a010c-149">If you want the resource to be copied to the build output folder every time a project is built, you set the `CopyToOutputDirectory` metadata element with the `Always` value.</span></span> <span data-ttu-id="a010c-150">W przeciwnym razie można upewnić się, że tylko Najnowsza wersja zasobu jest kopiowana do folderu danych wyjściowych kompilacji przy użyciu `PreserveNewest` wartości.</span><span class="sxs-lookup"><span data-stu-id="a010c-150">Otherwise, you can ensure that only the newest version of the resource is copied to the build output folder by using the `PreserveNewest` value.</span></span>  
  
 <span data-ttu-id="a010c-151">Poniżej przedstawiono plik skonfigurowany jako plik zawartości, który jest kopiowany do folderu danych wyjściowych kompilacji tylko wtedy, gdy nowa wersja zasobu zostanie dodana do projektu.</span><span class="sxs-lookup"><span data-stu-id="a010c-151">The following shows a file that is configured as a content file which is copied to the build output folder only when a new version of the resource is added to the project.</span></span>  
  
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
> <span data-ttu-id="a010c-152">W programie Visual Studio tworzysz plik zawartości przez dodanie pliku do projektu i ustawienie jego `Build Action` na `Content` , a następnie ustaw jego wartość (tak `Copy to Output Directory` `Copy always` jak `Always` ) i `Copy if newer` (analogicznie jak `PreserveNewest` ).</span><span class="sxs-lookup"><span data-stu-id="a010c-152">In Visual Studio, you create a content file by adding a file to a project and setting its `Build Action` to `Content`, and set its `Copy to Output Directory` to `Copy always` (same as `Always`) and `Copy if newer` (same as `PreserveNewest`).</span></span>  
  
 <span data-ttu-id="a010c-153">Po skompilowaniu projektu <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atrybut jest kompilowany do metadanych zestawu dla każdego pliku zawartości.</span><span class="sxs-lookup"><span data-stu-id="a010c-153">When the project is built, an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is compiled into the metadata of the assembly for each content file.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 <span data-ttu-id="a010c-154">Wartość <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> wskazuje ścieżkę do pliku zawartości względem jego położenia w projekcie.</span><span class="sxs-lookup"><span data-stu-id="a010c-154">The value of the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implies the path to the content file relative to its position in the project.</span></span> <span data-ttu-id="a010c-155">Na przykład, jeśli plik zawartości znajduje się w podfolderze projektu, dodatkowe informacje o ścieżce zostaną włączone do <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> wartości.</span><span class="sxs-lookup"><span data-stu-id="a010c-155">For example, if a content file was located in a project subfolder, the additional path information would be incorporated into the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <span data-ttu-id="a010c-156"><xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>Wartość jest również wartością ścieżki do pliku zawartości w folderze danych wyjściowych kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a010c-156">The <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value is also the value of the path to the content file in the build output folder.</span></span>  
  
### <a name="using-content-files"></a><span data-ttu-id="a010c-157">Korzystanie z plików zawartości</span><span class="sxs-lookup"><span data-stu-id="a010c-157">Using Content Files</span></span>  
 <span data-ttu-id="a010c-158">Aby załadować plik zawartości, można wywołać <xref:System.Windows.Application.GetContentStream%2A> metodę <xref:System.Windows.Application> klasy, przekazując identyfikator URI pakietu, który identyfikuje żądany plik zawartości.</span><span class="sxs-lookup"><span data-stu-id="a010c-158">To load a content file, you can call the <xref:System.Windows.Application.GetContentStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired content file.</span></span> <span data-ttu-id="a010c-159"><xref:System.Windows.Application.GetContentStream%2A>zwraca <xref:System.Windows.Resources.StreamResourceInfo> obiekt, który udostępnia plik zawartości jako <xref:System.IO.Stream> i opisuje jego typ zawartości.</span><span class="sxs-lookup"><span data-stu-id="a010c-159"><xref:System.Windows.Application.GetContentStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the content file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="a010c-160">Na przykład poniższy kod pokazuje, jak użyć <xref:System.Windows.Application.GetContentStream%2A> do załadowania <xref:System.Windows.Controls.Page> pliku zawartości i ustawienia go jako zawartości <xref:System.Windows.Controls.Frame> ( `pageFrame` ).</span><span class="sxs-lookup"><span data-stu-id="a010c-160">As an example, the following code shows how to use <xref:System.Windows.Application.GetContentStream%2A> to load a <xref:System.Windows.Controls.Page> content file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 <span data-ttu-id="a010c-161">Podczas gdy wywoływanie <xref:System.Windows.Application.GetContentStream%2A> daje dostęp do <xref:System.IO.Stream> , należy wykonać dodatkową ilość pracy, aby przekonwertować ją na typ właściwości, z którą zostanie ona ustawiona.</span><span class="sxs-lookup"><span data-stu-id="a010c-161">While calling <xref:System.Windows.Application.GetContentStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="a010c-162">Zamiast tego można zezwolić platformie WPF na otwieranie i konwertowanie <xref:System.IO.Stream> przez załadowanie pliku zasobów bezpośrednio do właściwości typu za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="a010c-162">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="a010c-163">Poniższy przykład pokazuje, jak załadować element <xref:System.Windows.Controls.Page> bezpośrednio do <xref:System.Windows.Controls.Frame> ( `pageFrame` ) za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="a010c-163">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 <span data-ttu-id="a010c-164">Poniższy przykład jest odpowiednikiem znaczników z poprzedniego przykładu.</span><span class="sxs-lookup"><span data-stu-id="a010c-164">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>
## <a name="site-of-origin-files"></a><span data-ttu-id="a010c-165">Lokacja plików pochodzenia</span><span class="sxs-lookup"><span data-stu-id="a010c-165">Site of Origin Files</span></span>  
 <span data-ttu-id="a010c-166">Pliki zasobów mają jawną relację z zestawami, które są dystrybuowane razem, zgodnie z definicją przez <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> .</span><span class="sxs-lookup"><span data-stu-id="a010c-166">Resource files have an explicit relationship with the assemblies that they are distributed alongside, as defined by the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>.</span></span> <span data-ttu-id="a010c-167">Ale istnieją przypadki, w których można określić niejawną lub nieistniejącą relację między zestawem a plikiem danych aplikacji, w tym:</span><span class="sxs-lookup"><span data-stu-id="a010c-167">But, there are times when you may want to establish either an implicit or non-existent relationship between an assembly and an application data file, including when:</span></span>  
  
- <span data-ttu-id="a010c-168">Plik nie istnieje w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a010c-168">A file doesn't exist at compile time.</span></span>  
  
- <span data-ttu-id="a010c-169">Nie wiesz, jakie pliki będą wymagane przez zestaw do czasu wykonania.</span><span class="sxs-lookup"><span data-stu-id="a010c-169">You don't know what files your assembly will require until run time.</span></span>  
  
- <span data-ttu-id="a010c-170">Chcesz mieć możliwość aktualizowania plików bez ponownego kompilowania zestawu, z którym są skojarzone.</span><span class="sxs-lookup"><span data-stu-id="a010c-170">You want to be able to update files without recompiling the assembly that they are associated with.</span></span>  
  
- <span data-ttu-id="a010c-171">Aplikacja używa dużych plików danych, takich jak audio i wideo, i chcesz, aby użytkownicy mogli je pobrać, jeśli zdecydują się na to.</span><span class="sxs-lookup"><span data-stu-id="a010c-171">Your application uses large data files, such as audio and video, and you only want users to download them if they choose to.</span></span>  
  
 <span data-ttu-id="a010c-172">Istnieje możliwość załadowania tych typów plików przy użyciu tradycyjnych schematów URI, takich jak `file:///` `http://` schematy i.</span><span class="sxs-lookup"><span data-stu-id="a010c-172">It is possible to load these types of files by using traditional URI schemes, such as the `file:///` and `http://` schemes.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 <span data-ttu-id="a010c-173">Jednak `file:///` `http://` schematy i wymagają, aby aplikacja miała pełne zaufanie.</span><span class="sxs-lookup"><span data-stu-id="a010c-173">However, the `file:///` and `http://` schemes require your application to have full trust.</span></span> <span data-ttu-id="a010c-174">Jeśli aplikacja jest aplikacją przeglądarki XAML (XBAP), która została uruchomiona z Internetu lub intranetu, i żąda tylko zestawu uprawnień dozwolonych dla aplikacji uruchomionych z tych lokalizacji, luźne pliki mogą być ładowane tylko z lokacji źródłowej (lokalizacja uruchamiania) aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a010c-174">If your application is a XAML browser application (XBAP) that was launched from the Internet or intranet, and it requests only the set of permissions that are allowed for applications launched from those locations, loose files can only be loaded from the application's site of origin (launch location).</span></span> <span data-ttu-id="a010c-175">Takie pliki są znane jako *lokacja plików pochodzenia* .</span><span class="sxs-lookup"><span data-stu-id="a010c-175">Such files are known as *site of origin* files.</span></span>  
  
 <span data-ttu-id="a010c-176">Lokacja plików pochodzenia jest jedyną opcją dla aplikacji częściowo zaufanych, chociaż nie są ograniczone do aplikacji częściowo zaufanych.</span><span class="sxs-lookup"><span data-stu-id="a010c-176">Site of origin files are the only option for partial trust applications, although are not limited to partial trust applications.</span></span> <span data-ttu-id="a010c-177">Aplikacje z pełnym zaufaniem mogą nadal potrzebować załadowania plików danych aplikacji, które nie są znane w czasie kompilacji; gdy aplikacje z pełnym zaufaniem mogą korzystać z file:///, prawdopodobnie pliki danych aplikacji zostaną zainstalowane w tym samym folderze co lub w podfolderze zestawu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a010c-177">Full trust applications may still need to load application data files that they do not know about at build time; while full trust applications could use file:///, it is likely that the application data files will be installed in the same folder as, or a subfolder of, the application assembly.</span></span> <span data-ttu-id="a010c-178">W takim przypadku użycie funkcji odwołującej się do lokalizacji jest łatwiejsze niż używanie file:///, ponieważ użycie file:///wymaga wykonania pełnej ścieżki do pliku.</span><span class="sxs-lookup"><span data-stu-id="a010c-178">In this case, using site of origin referencing is easier than using file:///, because using file:/// requires you to work out the full path the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a010c-179">Lokacja plików pochodzenia nie jest buforowana przez aplikację przeglądarki XAML (XBAP) na komputerze klienckim, natomiast pliki zawartości to.</span><span class="sxs-lookup"><span data-stu-id="a010c-179">Site of origin files are not cached with an XAML browser application (XBAP) on a client machine, while content files are.</span></span> <span data-ttu-id="a010c-180">W związku z tym są pobierane tylko wtedy, gdy jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="a010c-180">Consequently, they are only downloaded when specifically requested.</span></span> <span data-ttu-id="a010c-181">Jeśli aplikacja przeglądarki XAML (XBAP) ma duże pliki multimedialne, skonfigurowanie ich jako lokacji plików pochodzenia oznacza, że początkowe uruchomienie aplikacji jest znacznie szybsze i pliki są pobierane na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a010c-181">If an XAML browser application (XBAP) application has large media files, configuring them as site of origin files means the initial application launch is much faster, and the files are only downloaded on demand.</span></span>  
  
### <a name="configuring-site-of-origin-files"></a><span data-ttu-id="a010c-182">Konfigurowanie lokacji plików pochodzenia</span><span class="sxs-lookup"><span data-stu-id="a010c-182">Configuring Site of Origin Files</span></span>  
 <span data-ttu-id="a010c-183">Jeśli witryna plików pochodzenia jest nieistniejąca lub nieznana w czasie kompilacji, należy użyć tradycyjnych mechanizmów wdrażania, aby upewnić się, że wymagane pliki są dostępne w czasie wykonywania, w tym przy użyciu `XCopy` programu wiersza polecenia lub Instalator Windows Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a010c-183">If your site of origin files are non-existent or unknown at compile time, you need to use traditional deployment mechanisms for ensuring the required files are available at run time, including using either the `XCopy` command-line program or the Microsoft Windows Installer.</span></span>  
  
 <span data-ttu-id="a010c-184">Jeśli wiesz, jak w czasie kompilacji pliki, które mają znajdować się w lokacji pochodzenia, ale nadal chcesz uniknąć jawnej zależności, możesz dodać te pliki do projektu MSBuild jako `None` element.</span><span class="sxs-lookup"><span data-stu-id="a010c-184">If you do know at compile time the files that you would like to be located at the site of origin, but still want to avoid an explicit dependency, you can add those files to an MSBuild project as `None` item.</span></span> <span data-ttu-id="a010c-185">Podobnie jak w przypadku plików zawartości, należy ustawić atrybut MSBuild, `CopyToOutputDirectory` Aby określić, że lokacja pliku pochodzenia jest kopiowana do lokalizacji względnej dla skompilowanego zestawu, określając `Always` wartość lub `PreserveNewest` wartość.</span><span class="sxs-lookup"><span data-stu-id="a010c-185">As with content files, you need to set the MSBuild `CopyToOutputDirectory` attribute to specify that the site of origin file is copied to a location that is relative to the built assembly, by specifying either the `Always` value or the `PreserveNewest` value.</span></span>  
  
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
> <span data-ttu-id="a010c-186">W programie Visual Studio utworzysz lokację pliku pierwotnego, dodając plik do projektu i ustawiając go `Build Action` na `None` .</span><span class="sxs-lookup"><span data-stu-id="a010c-186">In Visual Studio, you create a site of origin file by adding a file to a project and setting its `Build Action` to `None`.</span></span>  
  
 <span data-ttu-id="a010c-187">Po skompilowaniu projektu, MSBuild kopiuje określone pliki do folderu danych wyjściowych kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a010c-187">When the project is built, MSBuild copies the specified files to the build output folder.</span></span>  
  
### <a name="using-site-of-origin-files"></a><span data-ttu-id="a010c-188">Korzystanie z lokalizacji plików pochodzenia</span><span class="sxs-lookup"><span data-stu-id="a010c-188">Using Site of Origin Files</span></span>  
 <span data-ttu-id="a010c-189">Aby załadować lokację pliku pierwotnego, można wywołać <xref:System.Windows.Application.GetRemoteStream%2A> metodę <xref:System.Windows.Application> klasy, przekazując identyfikator URI pakietu, który identyfikuje żądaną lokację pliku pierwotnego.</span><span class="sxs-lookup"><span data-stu-id="a010c-189">To load a site of origin file, you can call the <xref:System.Windows.Application.GetRemoteStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired site of origin file.</span></span> <span data-ttu-id="a010c-190"><xref:System.Windows.Application.GetRemoteStream%2A>zwraca <xref:System.Windows.Resources.StreamResourceInfo> obiekt, który uwidacznia lokację pliku pierwotnego jako <xref:System.IO.Stream> i opisuje jego typ zawartości.</span><span class="sxs-lookup"><span data-stu-id="a010c-190"><xref:System.Windows.Application.GetRemoteStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the site of origin file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="a010c-191">Na przykład poniższy kod pokazuje, jak użyć <xref:System.Windows.Application.GetRemoteStream%2A> do załadowania <xref:System.Windows.Controls.Page> lokacji pliku źródłowego i ustawienia jej jako zawartości <xref:System.Windows.Controls.Frame> ( `pageFrame` ).</span><span class="sxs-lookup"><span data-stu-id="a010c-191">As an example, the following code shows how to use <xref:System.Windows.Application.GetRemoteStream%2A> to load a <xref:System.Windows.Controls.Page> site of origin file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 <span data-ttu-id="a010c-192">Podczas gdy wywoływanie <xref:System.Windows.Application.GetRemoteStream%2A> daje dostęp do <xref:System.IO.Stream> , należy wykonać dodatkową ilość pracy, aby przekonwertować ją na typ właściwości, z którą zostanie ona ustawiona.</span><span class="sxs-lookup"><span data-stu-id="a010c-192">While calling <xref:System.Windows.Application.GetRemoteStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="a010c-193">Zamiast tego można zezwolić platformie WPF na otwieranie i konwertowanie <xref:System.IO.Stream> przez załadowanie pliku zasobów bezpośrednio do właściwości typu za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="a010c-193">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="a010c-194">Poniższy przykład pokazuje, jak załadować element <xref:System.Windows.Controls.Page> bezpośrednio do <xref:System.Windows.Controls.Frame> ( `pageFrame` ) za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="a010c-194">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 <span data-ttu-id="a010c-195">Poniższy przykład jest odpowiednikiem znaczników z poprzedniego przykładu.</span><span class="sxs-lookup"><span data-stu-id="a010c-195">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>
## <a name="rebuilding-after-changing-build-type"></a><span data-ttu-id="a010c-196">Ponowne kompilowanie po zmianie typu kompilacji</span><span class="sxs-lookup"><span data-stu-id="a010c-196">Rebuilding After Changing Build Type</span></span>  
 <span data-ttu-id="a010c-197">Po zmianie typu kompilacji pliku danych aplikacji należy ponownie skompilować całą aplikację, aby upewnić się, że te zmiany są stosowane.</span><span class="sxs-lookup"><span data-stu-id="a010c-197">After you change the build type of an application data file, you need to rebuild the entire application to ensure those changes are applied.</span></span> <span data-ttu-id="a010c-198">Jeśli aplikacja zostanie utworzona tylko, zmiany nie są stosowane.</span><span class="sxs-lookup"><span data-stu-id="a010c-198">If you only build the application, the changes are not applied.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a010c-199">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a010c-199">See also</span></span>

- [<span data-ttu-id="a010c-200">Pakuj URI w WPF</span><span class="sxs-lookup"><span data-stu-id="a010c-200">Pack URIs in WPF</span></span>](pack-uris-in-wpf.md)
