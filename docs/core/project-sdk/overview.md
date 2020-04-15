---
title: Omówienie zestawie SDK projektu .NET Core
description: Dowiedz się więcej o sdkach projektu .NET Core.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: d0ac01dca31dffea482745126e00c34b1da20774
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389667"
---
# <a name="net-core-project-sdks"></a><span data-ttu-id="24454-103">SDK projektu .NET Core</span><span class="sxs-lookup"><span data-stu-id="24454-103">.NET Core project SDKs</span></span>

<span data-ttu-id="24454-104">Projekty .NET Core są skojarzone z zestawem do tworzenia oprogramowania (SDK).</span><span class="sxs-lookup"><span data-stu-id="24454-104">.NET Core projects are associated with a software development kit (SDK).</span></span> <span data-ttu-id="24454-105">Każdy *zestaw SDK projektu* jest zestawem obiektów [docelowych](/visualstudio/msbuild/msbuild-targets) MSBuild i [skojarzonych zadań,](/visualstudio/msbuild/msbuild-tasks) które są odpowiedzialne za kompilowanie, pakowanie i publikowanie kodu.</span><span class="sxs-lookup"><span data-stu-id="24454-105">Each *project SDK* is a set of MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span> <span data-ttu-id="24454-106">Projekt, który odwołuje się do sdk projektu jest czasami określany jako *projekt w stylu SDK*.</span><span class="sxs-lookup"><span data-stu-id="24454-106">A project that references a project SDK is sometimes referred to as an *SDK-style project*.</span></span>

## <a name="available-sdks"></a><span data-ttu-id="24454-107">Dostępne sdk</span><span class="sxs-lookup"><span data-stu-id="24454-107">Available SDKs</span></span>

<span data-ttu-id="24454-108">Dla platformy .NET Core dostępne są następujące skomuniky SDK:</span><span class="sxs-lookup"><span data-stu-id="24454-108">The following SDKs are available for .NET Core:</span></span>

| <span data-ttu-id="24454-109">ID</span><span class="sxs-lookup"><span data-stu-id="24454-109">ID</span></span> | <span data-ttu-id="24454-110">Opis</span><span class="sxs-lookup"><span data-stu-id="24454-110">Description</span></span> | <span data-ttu-id="24454-111">Repo</span><span class="sxs-lookup"><span data-stu-id="24454-111">Repo</span></span>|
| - | - | - |
| `Microsoft.NET.Sdk` | <span data-ttu-id="24454-112">Podstawowy sdk .NET</span><span class="sxs-lookup"><span data-stu-id="24454-112">The .NET Core SDK</span></span> | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | <span data-ttu-id="24454-113">Podstawowy identyfikator [SDK sieci Web](/aspnet/core/razor-pages/web-sdk) .NET</span><span class="sxs-lookup"><span data-stu-id="24454-113">The .NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk)</span></span> | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | <span data-ttu-id="24454-114">SDK [do golenia](/aspnet/core/razor-pages/sdk) .NET Core</span><span class="sxs-lookup"><span data-stu-id="24454-114">The .NET Core [Razor SDK](/aspnet/core/razor-pages/sdk)</span></span> |
| `Microsoft.NET.Sdk.Worker` | <span data-ttu-id="24454-115">Podstawowy plik SDK usługi pracownika .NET</span><span class="sxs-lookup"><span data-stu-id="24454-115">The .NET Core Worker Service SDK</span></span> |
| `Microsoft.NET.Sdk.WindowsDesktop` | <span data-ttu-id="24454-116">.NET Core WinForms i WPF SDK</span><span class="sxs-lookup"><span data-stu-id="24454-116">The .NET Core WinForms and WPF SDK</span></span> |

<span data-ttu-id="24454-117">Core SDK .NET jest podstawowym SDK dla .NET Core.</span><span class="sxs-lookup"><span data-stu-id="24454-117">The .NET Core SDK is the base SDK for .NET Core.</span></span> <span data-ttu-id="24454-118">Inne sdks odwołać .NET Core SDK i projekty, które są skojarzone z innymi SDK mają wszystkie właściwości .NET Core SDK dostępne dla nich.</span><span class="sxs-lookup"><span data-stu-id="24454-118">The other SDKs reference the .NET Core SDK, and projects that are associated with the other SDKs have all the .NET Core SDK properties available to them.</span></span> <span data-ttu-id="24454-119">Na przykład składnik SDK sieci Web zależy zarówno od sdk .NET Core, jak i SDK razor.</span><span class="sxs-lookup"><span data-stu-id="24454-119">The Web SDK, for example, depends on both the .NET Core SDK and the Razor SDK.</span></span>

<span data-ttu-id="24454-120">Można również tworzyć własne SDK, które mogą być dystrybuowane za pośrednictwem NuGet.</span><span class="sxs-lookup"><span data-stu-id="24454-120">You can also author your own SDK that can be distributed via NuGet.</span></span>

## <a name="project-files"></a><span data-ttu-id="24454-121">Pliki projektu</span><span class="sxs-lookup"><span data-stu-id="24454-121">Project files</span></span>

<span data-ttu-id="24454-122">Projekty .NET Core są oparte na formacie [MSBuild.](/visualstudio/msbuild/msbuild)</span><span class="sxs-lookup"><span data-stu-id="24454-122">.NET Core projects are based on the [MSBuild](/visualstudio/msbuild/msbuild) format.</span></span> <span data-ttu-id="24454-123">Pliki projektu, które mają rozszerzenia, takie jak *.csproj* dla projektów C# i *.fsproj* dla projektów F#, są w formacie XML.</span><span class="sxs-lookup"><span data-stu-id="24454-123">Project files, which have extensions like *.csproj* for C# projects and *.fsproj* for F# projects, are in XML format.</span></span> <span data-ttu-id="24454-124">Głównym elementem pliku projektu MSBuild jest [element projektu.](/visualstudio/msbuild/project-element-msbuild)</span><span class="sxs-lookup"><span data-stu-id="24454-124">The root element of an MSBuild project file is the [Project](/visualstudio/msbuild/project-element-msbuild) element.</span></span> <span data-ttu-id="24454-125">Element `Project` ma opcjonalny `Sdk` atrybut, który określa, który zestaw SDK (i wersja) do użycia.</span><span class="sxs-lookup"><span data-stu-id="24454-125">The `Project` element has an optional `Sdk` attribute that specifies which SDK (and version) to use.</span></span> <span data-ttu-id="24454-126">Aby użyć narzędzi .NET Core i utworzyć `Sdk` kod, ustaw atrybut na jeden z identyfikatorów w tabeli [Dostępne zestawy SDK.](#available-sdks)</span><span class="sxs-lookup"><span data-stu-id="24454-126">To use the .NET Core tools and build your code, set the `Sdk` attribute to one of the IDs in the [Available SDKs](#available-sdks) table.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

<span data-ttu-id="24454-127">Aby określić SDK, który pochodzi z NuGet, dołącz wersję na końcu nazwy lub określ nazwę i wersję w pliku *global.json.*</span><span class="sxs-lookup"><span data-stu-id="24454-127">To specify an SDK that comes from NuGet, include the version at the end of the name, or specify the name and version in the *global.json* file.</span></span>

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

<span data-ttu-id="24454-128">Innym sposobem określenia SDK jest element [Sdk](/visualstudio/msbuild/sdk-element-msbuild) najwyższego poziomu:</span><span class="sxs-lookup"><span data-stu-id="24454-128">Another way to specify the SDK is with the top-level [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span></span>

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

<span data-ttu-id="24454-129">Odwoływanie się do sdk w jeden z tych sposobów znacznie upraszcza pliki projektu dla .NET Core.</span><span class="sxs-lookup"><span data-stu-id="24454-129">Referencing an SDK in one of these ways greatly simplifies project files for .NET Core.</span></span> <span data-ttu-id="24454-130">Podczas oceny projektu MSBuild dodaje niejawne importy w `Sdk.props` górnej `Sdk.targets` części pliku projektu i na dole.</span><span class="sxs-lookup"><span data-stu-id="24454-130">While evaluating the project, MSBuild adds implicit imports for `Sdk.props` at the top of the project file and `Sdk.targets` at the bottom.</span></span>

```xml
<Project>
  <!-- Implicit top import -->
  <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />
  ...
  <!-- Implicit bottom import -->
  <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>
```

> [!TIP]
> <span data-ttu-id="24454-131">Na komputerze z systemem Windows pliki *Sdk.props* i *Sdk.targets* można znaleźć w folderze *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk\Sdk* folder.</span><span class="sxs-lookup"><span data-stu-id="24454-131">On a Windows machine, the *Sdk.props* and *Sdk.targets* files can be found in the *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk* folder.</span></span>

### <a name="preprocess-the-project-file"></a><span data-ttu-id="24454-132">Wstępne przetwarzanie pliku projektu</span><span class="sxs-lookup"><span data-stu-id="24454-132">Preprocess the project file</span></span>

<span data-ttu-id="24454-133">Możesz zobaczyć w pełni rozwinięty projekt, jak MSBuild widzi go po SDK i jego cele są uwzględniane za pomocą `dotnet msbuild -preprocess` polecenia.</span><span class="sxs-lookup"><span data-stu-id="24454-133">You can see the fully expanded project as MSBuild sees it after the SDK and its targets are included by using the `dotnet msbuild -preprocess` command.</span></span> <span data-ttu-id="24454-134">Przełącznik [przetwarzania wstępnego](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) [`dotnet msbuild`](../tools/dotnet-msbuild.md) polecenia pokazuje, które pliki są importowane, ich źródła i ich wkład do kompilacji bez faktycznego budowania projektu.</span><span class="sxs-lookup"><span data-stu-id="24454-134">The [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) switch of the [`dotnet msbuild`](../tools/dotnet-msbuild.md) command shows which files are imported, their sources, and their contributions to the build without actually building the project.</span></span>

<span data-ttu-id="24454-135">Jeśli projekt ma wiele struktur docelowych, skoncentruj wyniki polecenia tylko na jednej platformie, określając ją jako właściwość MSBuild.</span><span class="sxs-lookup"><span data-stu-id="24454-135">If the project has multiple target frameworks, focus the results of the command on only one framework by specifying it as an MSBuild property.</span></span> <span data-ttu-id="24454-136">Przykład:</span><span class="sxs-lookup"><span data-stu-id="24454-136">For example:</span></span>

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a><span data-ttu-id="24454-137">Domyślna kompilacja obejmuje</span><span class="sxs-lookup"><span data-stu-id="24454-137">Default compilation includes</span></span>

<span data-ttu-id="24454-138">Domyślne obejmuje i wyklucza dla elementów kompilacji i osadzone zasoby są zdefiniowane w zestawie SDK.</span><span class="sxs-lookup"><span data-stu-id="24454-138">The default includes and excludes for compile items and embedded resources are defined in the SDK.</span></span> <span data-ttu-id="24454-139">W przeciwieństwie do projektów innych niż SDK .NET Framework, nie trzeba określać te elementy w pliku projektu, ponieważ domyślne obejmują najczęstsze przypadki użycia.</span><span class="sxs-lookup"><span data-stu-id="24454-139">Unlike non-SDK .NET Framework projects, you don't need to specify these items in your project file, because the defaults cover most common use cases.</span></span> <span data-ttu-id="24454-140">Prowadzi to do mniejszych plików projektu, które są łatwiejsze do zrozumienia, a także edytować ręcznie, w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="24454-140">This leads to smaller project files that are easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="24454-141">W poniższej tabeli przedstawiono, który element i które [globy](https://en.wikipedia.org/wiki/Glob_(programming)) są uwzględniane i wykluczane w zestawie .NET Core SDK:</span><span class="sxs-lookup"><span data-stu-id="24454-141">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET Core SDK:</span></span>

| <span data-ttu-id="24454-142">Element</span><span class="sxs-lookup"><span data-stu-id="24454-142">Element</span></span>           | <span data-ttu-id="24454-143">Uwzględnij glob</span><span class="sxs-lookup"><span data-stu-id="24454-143">Include glob</span></span>                              | <span data-ttu-id="24454-144">Wyklucz glob</span><span class="sxs-lookup"><span data-stu-id="24454-144">Exclude glob</span></span>                                                  | <span data-ttu-id="24454-145">Usuń glob</span><span class="sxs-lookup"><span data-stu-id="24454-145">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| <span data-ttu-id="24454-146">Skompilować</span><span class="sxs-lookup"><span data-stu-id="24454-146">Compile</span></span>           | <span data-ttu-id="24454-147">\*\*/\*.cs (lub inne rozszerzenia języka)</span><span class="sxs-lookup"><span data-stu-id="24454-147">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="24454-148">\*\*/\*.user;  \*\*/\*. \*proj ;  \* \* / \*  \* \* /.vssscc \*(vssscc)</span><span class="sxs-lookup"><span data-stu-id="24454-148">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="24454-149">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="24454-149">N/A</span></span>                      |
| <span data-ttu-id="24454-150">Zasoby wbudowaneSerekseźródło</span><span class="sxs-lookup"><span data-stu-id="24454-150">EmbeddedResource</span></span>  | <span data-ttu-id="24454-151">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="24454-151">\*\*/\*.resx</span></span>                              | <span data-ttu-id="24454-152">\*\*/\*.user; \*\*/\*. \*proj ; \* \* / \* \* \* /.vssscc \*(vssscc)</span><span class="sxs-lookup"><span data-stu-id="24454-152">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="24454-153">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="24454-153">N/A</span></span>                      |
| <span data-ttu-id="24454-154">Brak</span><span class="sxs-lookup"><span data-stu-id="24454-154">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="24454-155">\*\*/\*.user; \*\*/\*. \*proj ; \* \* / \* \* \* /.vssscc \*(vssscc)</span><span class="sxs-lookup"><span data-stu-id="24454-155">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="24454-156">\*\*/\*.cs ; \* \* /.resx \*(resx)</span><span class="sxs-lookup"><span data-stu-id="24454-156">\*\*/\*.cs; \*\*/\*.resx</span></span> |

> [!NOTE]
> <span data-ttu-id="24454-157">`./bin` Foldery `./obj` i foldery, które `$(BaseOutputPath)` są `$(BaseIntermediateOutputPath)` reprezentowane przez i MSBuild właściwości, są domyślnie wykluczone z globs.</span><span class="sxs-lookup"><span data-stu-id="24454-157">The `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, are excluded from the globs by default.</span></span> <span data-ttu-id="24454-158">Wykluczenia są reprezentowane `$(DefaultItemExcludes)`przez właściwość .</span><span class="sxs-lookup"><span data-stu-id="24454-158">Excludes are represented by the property `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="24454-159">Jeśli jawnie zdefiniujesz te elementy w pliku projektu, prawdopodobnie zostanie wyświetlony następujący błąd:</span><span class="sxs-lookup"><span data-stu-id="24454-159">If you explicitly define these items in your project file, you're likely to get the following error:</span></span>

<span data-ttu-id="24454-160">**Zduplikowane elementy kompilacji zostały uwzględnione. Zestaw SDK platformy .NET domyślnie zawiera elementy kompilacji z katalogu projektu. Można usunąć te elementy z pliku projektu lub ustawić właściwość "EnableDefaultCompileItems" na "false", jeśli chcesz jawnie dołączyć je do pliku projektu.**</span><span class="sxs-lookup"><span data-stu-id="24454-160">**Duplicate Compile items were included. The .NET SDK includes Compile items from your project directory by default. You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.**</span></span>

<span data-ttu-id="24454-161">Aby rozwiązać ten problem, usuń `Compile` jawne elementy, które pasują do niejawnych wymienionych w poprzedniej tabeli, lub ustaw `EnableDefaultCompileItems` właściwość na `false`, która wyłącza niejawne włączenie:</span><span class="sxs-lookup"><span data-stu-id="24454-161">To resolve the error, either remove the explicit `Compile` items that match the implicit ones listed on the previous table, or set the `EnableDefaultCompileItems` property to `false`, which disables implicit inclusion:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="24454-162">Jeśli chcesz określić, na przykład niektóre pliki, aby uzyskać opublikowane w aplikacji, nadal można użyć znanych mechanizmów MSBuild do tego, na przykład `Content` elementu.</span><span class="sxs-lookup"><span data-stu-id="24454-162">If you want to specify, for example, some files to get published with your app, you can still use the known MSBuild mechanisms for that, for example, the `Content` element.</span></span>

<span data-ttu-id="24454-163">`EnableDefaultCompileItems`tylko wyłącza `Compile` globs, ale nie wpływa na `None` inne globs, \*jak niejawne glob, który ma również zastosowanie do .cs elementów.</span><span class="sxs-lookup"><span data-stu-id="24454-163">`EnableDefaultCompileItems` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob that also applies to \*.cs items.</span></span> <span data-ttu-id="24454-164">Z tego powodu Eksplorator \*rozwiązań w programie Visual Studio pokazuje `None` elementy .cs jako część projektu, zawarte jako elementy.</span><span class="sxs-lookup"><span data-stu-id="24454-164">Because of that, Solution Explorer in Visual Studio shows \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="24454-165">Aby wyłączyć `None` niejawną `EnableDefaultNoneItems` `false`glob, należy ustawić na:</span><span class="sxs-lookup"><span data-stu-id="24454-165">To disable the implicit `None` glob, set `EnableDefaultNoneItems` to `false`:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="24454-166">Aby wyłączyć *wszystkie* niejawne `EnableDefaultItems` globy, ustaw właściwość na: `false`</span><span class="sxs-lookup"><span data-stu-id="24454-166">To disable *all* implicit globs, set the `EnableDefaultItems` property to `false`:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="customize-the-build"></a><span data-ttu-id="24454-167">Dostosowywanie kompilacji</span><span class="sxs-lookup"><span data-stu-id="24454-167">Customize the build</span></span>

<span data-ttu-id="24454-168">Istnieją różne sposoby [dostosowywania kompilacji.](/visualstudio/msbuild/customize-your-build)</span><span class="sxs-lookup"><span data-stu-id="24454-168">There are various ways to [customize a build](/visualstudio/msbuild/customize-your-build).</span></span> <span data-ttu-id="24454-169">Można zastąpić właściwość, przekazując ją jako argument do [polecenia msbuild](/visualstudio/msbuild/msbuild-command-line-reference) lub [dotnet.](../tools/index.md)</span><span class="sxs-lookup"><span data-stu-id="24454-169">You may want to override a property by passing it as an argument to an [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) or [dotnet](../tools/index.md) command.</span></span> <span data-ttu-id="24454-170">Można również dodać właściwość do pliku projektu lub do pliku *Directory.Build.props.*</span><span class="sxs-lookup"><span data-stu-id="24454-170">You can also add the property to the project file or to a *Directory.Build.props* file.</span></span> <span data-ttu-id="24454-171">Aby uzyskać listę przydatnych właściwości dla projektów .NET Core, zobacz [Właściwości MSBuild dla projektów .NET Core SDK](msbuild-props.md).</span><span class="sxs-lookup"><span data-stu-id="24454-171">For a list of useful properties for .NET Core projects, see [MSBuild properties for .NET Core SDK projects](msbuild-props.md).</span></span>

### <a name="custom-targets"></a><span data-ttu-id="24454-172">Cele niestandardowe</span><span class="sxs-lookup"><span data-stu-id="24454-172">Custom targets</span></span>

<span data-ttu-id="24454-173">.NET Podstawowe projekty można spakować niestandardowe obiekty docelowe MSBuild i właściwości do użycia przez projekty, które korzystają z pakietu.</span><span class="sxs-lookup"><span data-stu-id="24454-173">.NET Core projects can package custom MSBuild targets and properties for use by projects that consume the package.</span></span> <span data-ttu-id="24454-174">Użyj tego typu rozszerzalności, aby:</span><span class="sxs-lookup"><span data-stu-id="24454-174">Use this type of extensibility when you want to:</span></span>

- <span data-ttu-id="24454-175">Rozszerzanie procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="24454-175">Extend the build process.</span></span>
- <span data-ttu-id="24454-176">Dostęp do artefaktów procesu kompilacji, takich jak wygenerowane pliki.</span><span class="sxs-lookup"><span data-stu-id="24454-176">Access artifacts of the build process, such as generated files.</span></span>
- <span data-ttu-id="24454-177">Sprawdź konfigurację, w ramach której jest wywoływana kompilacja.</span><span class="sxs-lookup"><span data-stu-id="24454-177">Inspect the configuration under which the build is invoked.</span></span>

<span data-ttu-id="24454-178">Cele lub właściwości kompilacji niestandardowej można `<package_id>.targets` dodać, umieszczając pliki w formularzu lub `<package_id>.props` (na `Contoso.Utility.UsefulStuff.targets`przykład) w folderze *kompilacji* projektu.</span><span class="sxs-lookup"><span data-stu-id="24454-178">You add custom build targets or properties by placing files in the form `<package_id>.targets` or `<package_id>.props` (for example, `Contoso.Utility.UsefulStuff.targets`) in the *build* folder of the project.</span></span>

<span data-ttu-id="24454-179">Poniższy kod XML jest fragmentem kodu z pliku *csproj,* który instruuje [`dotnet pack`](../tools/dotnet-pack.md) polecenie, co spakować.</span><span class="sxs-lookup"><span data-stu-id="24454-179">The following XML is a snippet from a *.csproj* file that instructs the [`dotnet pack`](../tools/dotnet-pack.md) command what to package.</span></span> <span data-ttu-id="24454-180">Element `<ItemGroup Label="dotnet pack instructions">` umieszcza pliki obiektów docelowych w folderze *kompilacji* wewnątrz pakietu.</span><span class="sxs-lookup"><span data-stu-id="24454-180">The `<ItemGroup Label="dotnet pack instructions">` element places the targets files into the *build* folder inside the package.</span></span> <span data-ttu-id="24454-181">Element `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` umieszcza zestawy i pliki *.json* w folderze *kompilacji.*</span><span class="sxs-lookup"><span data-stu-id="24454-181">The `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` element places the assemblies and *.json* files into the *build* folder.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  ...
  <ItemGroup Label="dotnet pack instructions">
    <Content Include="build\*.targets">
      <Pack>true</Pack>
      <PackagePath>build\</PackagePath>
    </Content>
  </ItemGroup>
  <Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">
    <!-- Collect these items inside a target that runs after build but before packaging. -->
    <ItemGroup>
      <Content Include="$(OutputPath)\*.dll;$(OutputPath)\*.json">
        <Pack>true</Pack>
        <PackagePath>build\</PackagePath>
      </Content>
    </ItemGroup>
  </Target>
  ...
  
</Project>
```

<span data-ttu-id="24454-182">Aby korzystać z niestandardowego obiektu `PackageReference` docelowego w projekcie, dodaj element, który wskazuje pakiet i jego wersję.</span><span class="sxs-lookup"><span data-stu-id="24454-182">To consume a custom target in your project, add a `PackageReference` element that points to the package and its version.</span></span> <span data-ttu-id="24454-183">W przeciwieństwie do narzędzi pakiet niestandardowych obiektów docelowych znajduje się w zamknięciu zależności projektu zużywającego.</span><span class="sxs-lookup"><span data-stu-id="24454-183">Unlike the tools, the custom targets package is included in the consuming project's dependency closure.</span></span>

<span data-ttu-id="24454-184">Można skonfigurować sposób używania niestandardowego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="24454-184">You can configure how to use the custom target.</span></span> <span data-ttu-id="24454-185">Ponieważ jest to obiekt docelowy MSBuild, może zależeć od danego obiektu docelowego, uruchomić `dotnet msbuild -t:<target-name>` po innym miejscu docelowym lub być wywoływane ręcznie za pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="24454-185">Since it's an MSBuild target, it can depend on a given target, run after another target, or be manually invoked by using the `dotnet msbuild -t:<target-name>` command.</span></span> <span data-ttu-id="24454-186">Jednak aby zapewnić lepsze środowisko użytkownika, można połączyć narzędzia dla projektu i niestandardowe obiekty docelowe.</span><span class="sxs-lookup"><span data-stu-id="24454-186">However, to provide a better user experience, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="24454-187">W tym scenariuszu narzędzie na projekt akceptuje wszelkie parametry są potrzebne [`dotnet msbuild`](../tools/dotnet-msbuild.md) i przekłada się na wymagane wywołanie, które wykonuje obiekt docelowy.</span><span class="sxs-lookup"><span data-stu-id="24454-187">In this scenario, the per-project tool accepts whatever parameters are needed and translates that into the required [`dotnet msbuild`](../tools/dotnet-msbuild.md) invocation that executes the target.</span></span> <span data-ttu-id="24454-188">Możesz zobaczyć próbkę tego rodzaju synergii na [MVP Summit 2016 Hackathon](https://github.com/dotnet/MVPSummitHackathon2016) [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) próbki repozytorium w projekcie.</span><span class="sxs-lookup"><span data-stu-id="24454-188">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

## <a name="see-also"></a><span data-ttu-id="24454-189">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24454-189">See also</span></span>

- [<span data-ttu-id="24454-190">Instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="24454-190">Install .NET Core</span></span>](../install/index.md)
- [<span data-ttu-id="24454-191">Jak korzystać z sdk projektów MSBuild</span><span class="sxs-lookup"><span data-stu-id="24454-191">How to use MSBuild project SDKs</span></span>](/visualstudio/msbuild/how-to-use-project-sdk)
- [<span data-ttu-id="24454-192">Pakiet niestandardowe obiekty docelowe i rekwizyty MSBuild za pomocą nuget</span><span class="sxs-lookup"><span data-stu-id="24454-192">Package custom MSBuild targets and props with NuGet</span></span>](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
