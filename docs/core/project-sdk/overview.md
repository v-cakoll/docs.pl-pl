---
title: Omówienie sdk projektu .NET Core
description: Dowiedz się więcej o zestawach SDK projektu .NET Core.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: 32e14993326c6f17d6470249fe5a545180348631
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399176"
---
# <a name="net-core-project-sdks"></a><span data-ttu-id="75d72-103">Zestawy SDK projektu .NET Core</span><span class="sxs-lookup"><span data-stu-id="75d72-103">.NET Core project SDKs</span></span>

<span data-ttu-id="75d72-104">Projekty .NET Core są skojarzone z zestawem sdk (Software Development Kit).</span><span class="sxs-lookup"><span data-stu-id="75d72-104">.NET Core projects are associated with a software development kit (SDK).</span></span> <span data-ttu-id="75d72-105">Każdy zestaw SDK projektu jest [zestawem obiektów docelowych](/visualstudio/msbuild/msbuild-targets) MSBuild i skojarzonych [zadań,](/visualstudio/msbuild/msbuild-tasks) które są odpowiedzialne za kompilowanie, pakowanie i publikowanie kodu.</span><span class="sxs-lookup"><span data-stu-id="75d72-105">Each project SDK is a set of MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span>

## <a name="available-sdks"></a><span data-ttu-id="75d72-106">Dostępne zestawy SDK</span><span class="sxs-lookup"><span data-stu-id="75d72-106">Available SDKs</span></span>

<span data-ttu-id="75d72-107">Dla programu .NET Core dostępne są następujące zestawy SDK:</span><span class="sxs-lookup"><span data-stu-id="75d72-107">The following SDKs are available for .NET Core:</span></span>

| <span data-ttu-id="75d72-108">ID</span><span class="sxs-lookup"><span data-stu-id="75d72-108">ID</span></span> | <span data-ttu-id="75d72-109">Opis</span><span class="sxs-lookup"><span data-stu-id="75d72-109">Description</span></span> | <span data-ttu-id="75d72-110">Repo</span><span class="sxs-lookup"><span data-stu-id="75d72-110">Repo</span></span>|
| - | - | - |
| `Microsoft.NET.Sdk` | <span data-ttu-id="75d72-111">Zestaw SDK rdzenia .NET</span><span class="sxs-lookup"><span data-stu-id="75d72-111">The .NET Core SDK</span></span> | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | <span data-ttu-id="75d72-112">Zestaw [SDK sieci Web](/aspnet/core/razor-pages/web-sdk) .NET Core</span><span class="sxs-lookup"><span data-stu-id="75d72-112">The .NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk)</span></span> | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | <span data-ttu-id="75d72-113">Zestaw [SDK do golenia](/aspnet/core/razor-pages/sdk) .NET Core</span><span class="sxs-lookup"><span data-stu-id="75d72-113">The .NET Core [Razor SDK](/aspnet/core/razor-pages/sdk)</span></span> |
| `Microsoft.NET.Sdk.Worker` | <span data-ttu-id="75d72-114">Zestaw SDK usługi podstawowego procesu roboczego .NET</span><span class="sxs-lookup"><span data-stu-id="75d72-114">The .NET Core Worker Service SDK</span></span> |
| `Microsoft.NET.Sdk.WindowsDesktop` | <span data-ttu-id="75d72-115">Zestaw SDK winforms programu .NET Core i WPF</span><span class="sxs-lookup"><span data-stu-id="75d72-115">The .NET Core WinForms and WPF SDK</span></span> |

<span data-ttu-id="75d72-116">Zestaw SDK .NET Core jest podstawowym zestawem SDK dla programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="75d72-116">The .NET Core SDK is the base SDK for .NET Core.</span></span> <span data-ttu-id="75d72-117">Inne zestawy SDK odwołują się do sdk .NET Core, a projekty skojarzone z innymi zestawami SDK mają wszystkie dostępne właściwości sdk .NET Core.</span><span class="sxs-lookup"><span data-stu-id="75d72-117">The other SDKs reference the .NET Core SDK, and projects that are associated with the other SDKs have all the .NET Core SDK properties available to them.</span></span> <span data-ttu-id="75d72-118">Na przykład zestaw Web SDK zależy zarówno od sdk .NET Core, jak i zestaw SDK razor.</span><span class="sxs-lookup"><span data-stu-id="75d72-118">The Web SDK, for example, depends on both the .NET Core SDK and the Razor SDK.</span></span>

<span data-ttu-id="75d72-119">Można również autora własnego sdk, które mogą być dystrybuowane za pośrednictwem NuGet.</span><span class="sxs-lookup"><span data-stu-id="75d72-119">You can also author your own SDK that can be distributed via NuGet.</span></span>

## <a name="project-files"></a><span data-ttu-id="75d72-120">Pliki projektu</span><span class="sxs-lookup"><span data-stu-id="75d72-120">Project files</span></span>

<span data-ttu-id="75d72-121">Projekty .NET Core są oparte na formacie [MSBuild.](/visualstudio/msbuild/msbuild)</span><span class="sxs-lookup"><span data-stu-id="75d72-121">.NET Core projects are based on the [MSBuild](/visualstudio/msbuild/msbuild) format.</span></span> <span data-ttu-id="75d72-122">Pliki projektu, które mają rozszerzenia, takie jak *.csproj* dla projektów C# i *.fsproj* dla projektów F#, są w formacie XML.</span><span class="sxs-lookup"><span data-stu-id="75d72-122">Project files, which have extensions like *.csproj* for C# projects and *.fsproj* for F# projects, are in XML format.</span></span> <span data-ttu-id="75d72-123">Elementem głównym pliku projektu MSBuild jest [element projektu.](/visualstudio/msbuild/project-element-msbuild)</span><span class="sxs-lookup"><span data-stu-id="75d72-123">The root element of an MSBuild project file is the [Project](/visualstudio/msbuild/project-element-msbuild) element.</span></span> <span data-ttu-id="75d72-124">Element `Project` ma opcjonalny `Sdk` atrybut, który określa, który zestaw SDK (i wersja) do użycia.</span><span class="sxs-lookup"><span data-stu-id="75d72-124">The `Project` element has an optional `Sdk` attribute that specifies which SDK (and version) to use.</span></span> <span data-ttu-id="75d72-125">Aby użyć narzędzi .NET Core i utworzyć `Sdk` kod, ustaw atrybut na jeden z identyfikatorów w tabeli [Dostępne zestawy SDK.](#available-sdks)</span><span class="sxs-lookup"><span data-stu-id="75d72-125">To use the .NET Core tools and build your code, set the `Sdk` attribute to one of the IDs in the [Available SDKs](#available-sdks) table.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

<span data-ttu-id="75d72-126">Aby określić zestaw SDK, który pochodzi z NuGet, dołącz wersję na końcu nazwy lub określ nazwę i wersję w pliku *global.json.*</span><span class="sxs-lookup"><span data-stu-id="75d72-126">To specify an SDK that comes from NuGet, include the version at the end of the name, or specify the name and version in the *global.json* file.</span></span>

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

<span data-ttu-id="75d72-127">Innym sposobem określenia sdk jest z najwyższego poziomu [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span><span class="sxs-lookup"><span data-stu-id="75d72-127">Another way to specify the SDK is with the top-level [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span></span>

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

<span data-ttu-id="75d72-128">Odwoływanie się do sdk w jeden z tych sposobów znacznie upraszcza pliki projektu dla .NET Core.</span><span class="sxs-lookup"><span data-stu-id="75d72-128">Referencing an SDK in one of these ways greatly simplifies project files for .NET Core.</span></span> <span data-ttu-id="75d72-129">Podczas oceny projektu, MSBuild dodaje niejawne importy w `Sdk.props` `Sdk.targets` górnej części pliku projektu i u dołu.</span><span class="sxs-lookup"><span data-stu-id="75d72-129">While evaluating the project, MSBuild adds implicit imports for `Sdk.props` at the top of the project file and `Sdk.targets` at the bottom.</span></span>

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
> <span data-ttu-id="75d72-130">Na komputerze z systemem Windows pliki *Sdk.props* i *Sdk.targets* można znaleźć w folderze *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk.Sdk.in.*</span><span class="sxs-lookup"><span data-stu-id="75d72-130">On a Windows machine, the *Sdk.props* and *Sdk.targets* files can be found in the *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk* folder.</span></span>

### <a name="preprocess-the-project-file"></a><span data-ttu-id="75d72-131">Wstępne przetwarzanie pliku projektu</span><span class="sxs-lookup"><span data-stu-id="75d72-131">Preprocess the project file</span></span>

<span data-ttu-id="75d72-132">Możesz zobaczyć w pełni rozwinięty projekt, jak MSBuild widzi go po sdk i jego cele są uwzględniane za pomocą `dotnet msbuild -preprocess` polecenia.</span><span class="sxs-lookup"><span data-stu-id="75d72-132">You can see the fully expanded project as MSBuild sees it after the SDK and its targets are included by using the `dotnet msbuild -preprocess` command.</span></span> <span data-ttu-id="75d72-133">Przełącznik [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) [`dotnet msbuild`](../tools/dotnet-msbuild.md) polecenia pokazuje, które pliki są importowane, ich źródła i ich wkład do kompilacji bez faktycznie tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="75d72-133">The [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) switch of the [`dotnet msbuild`](../tools/dotnet-msbuild.md) command shows which files are imported, their sources, and their contributions to the build without actually building the project.</span></span>

<span data-ttu-id="75d72-134">Jeśli projekt ma wiele struktur docelowych, skoncentruj wyniki polecenia tylko na jednej strukturze, określając go jako właściwość MSBuild.</span><span class="sxs-lookup"><span data-stu-id="75d72-134">If the project has multiple target frameworks, focus the results of the command on only one framework by specifying it as an MSBuild property.</span></span> <span data-ttu-id="75d72-135">Przykład:</span><span class="sxs-lookup"><span data-stu-id="75d72-135">For example:</span></span>

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a><span data-ttu-id="75d72-136">Domyślna kompilacja zawiera</span><span class="sxs-lookup"><span data-stu-id="75d72-136">Default compilation includes</span></span>

<span data-ttu-id="75d72-137">Domyślne zawiera i wyklucza dla elementów kompilacji i osadzonych zasobów są zdefiniowane w zestawie SDK.</span><span class="sxs-lookup"><span data-stu-id="75d72-137">The default includes and excludes for compile items and embedded resources are defined in the SDK.</span></span> <span data-ttu-id="75d72-138">W przeciwieństwie do projektów innych niż SDK .NET Framework, nie trzeba określać te elementy w pliku projektu, ponieważ wartości domyślne obejmują najbardziej typowych przypadków użycia.</span><span class="sxs-lookup"><span data-stu-id="75d72-138">Unlike non-SDK .NET Framework projects, you don't need to specify these items in your project file, because the defaults cover most common use cases.</span></span> <span data-ttu-id="75d72-139">Prowadzi to do mniejszych plików projektu, które są łatwiejsze do zrozumienia, a także edytować ręcznie, w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="75d72-139">This leads to smaller project files that are easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="75d72-140">W poniższej tabeli przedstawiono, który element i [które globy](https://en.wikipedia.org/wiki/Glob_(programming)) są uwzględniane i wykluczane w zestawie .NET Core SDK:</span><span class="sxs-lookup"><span data-stu-id="75d72-140">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET Core SDK:</span></span>

| <span data-ttu-id="75d72-141">Element</span><span class="sxs-lookup"><span data-stu-id="75d72-141">Element</span></span>           | <span data-ttu-id="75d72-142">Uwzględnij glob</span><span class="sxs-lookup"><span data-stu-id="75d72-142">Include glob</span></span>                              | <span data-ttu-id="75d72-143">Wykluczyć glob</span><span class="sxs-lookup"><span data-stu-id="75d72-143">Exclude glob</span></span>                                                  | <span data-ttu-id="75d72-144">Usuń glob</span><span class="sxs-lookup"><span data-stu-id="75d72-144">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| <span data-ttu-id="75d72-145">Skompilować</span><span class="sxs-lookup"><span data-stu-id="75d72-145">Compile</span></span>           | <span data-ttu-id="75d72-146">\*\*/\*.cs (lub rozszerzenia innych języków)</span><span class="sxs-lookup"><span data-stu-id="75d72-146">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="75d72-147">\*\*/\*.user;  \*\*/\*. \*proj;  \* \* / \*  \* \* /.vssscc \*(vssscc)</span><span class="sxs-lookup"><span data-stu-id="75d72-147">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="75d72-148">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="75d72-148">N/A</span></span>                      |
| <span data-ttu-id="75d72-149">Osadzony zasób</span><span class="sxs-lookup"><span data-stu-id="75d72-149">EmbeddedResource</span></span>  | <span data-ttu-id="75d72-150">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="75d72-150">\*\*/\*.resx</span></span>                              | <span data-ttu-id="75d72-151">\*\*/\*.user; \*\*/\*. \*proj; \* \* / \* \* \* /.vssscc \*(vssscc)</span><span class="sxs-lookup"><span data-stu-id="75d72-151">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="75d72-152">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="75d72-152">N/A</span></span>                      |
| <span data-ttu-id="75d72-153">Brak</span><span class="sxs-lookup"><span data-stu-id="75d72-153">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="75d72-154">\*\*/\*.user; \*\*/\*. \*proj; \* \* / \* \* \* /.vssscc \*(vssscc)</span><span class="sxs-lookup"><span data-stu-id="75d72-154">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="75d72-155">\*\*/\*.cs; \* \* /.resx \*(resx)</span><span class="sxs-lookup"><span data-stu-id="75d72-155">\*\*/\*.cs; \*\*/\*.resx</span></span> |

> [!NOTE]
> <span data-ttu-id="75d72-156">I `./bin` `./obj` foldery, które są reprezentowane `$(BaseOutputPath)` `$(BaseIntermediateOutputPath)` przez i MSBuild właściwości, są domyślnie wyłączone z globs.</span><span class="sxs-lookup"><span data-stu-id="75d72-156">The `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, are excluded from the globs by default.</span></span> <span data-ttu-id="75d72-157">Wykluczenia są reprezentowane przez `$(DefaultItemExcludes)`właściwość .</span><span class="sxs-lookup"><span data-stu-id="75d72-157">Excludes are represented by the property `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="75d72-158">Jeśli jawnie zdefiniujesz te elementy w pliku projektu, prawdopodobnie zostanie unikniesz następującego błędu:</span><span class="sxs-lookup"><span data-stu-id="75d72-158">If you explicitly define these items in your project file, you're likely to get the following error:</span></span>

<span data-ttu-id="75d72-159">**Zduplikowane elementy kompilacji zostały uwzględnione. Zestaw SDK .NET domyślnie zawiera elementy kompilacji z katalogu projektu. Można usunąć te elementy z pliku projektu lub ustawić właściwość "EnableDefaultCompileItems" na "false", jeśli chcesz jawnie uwzględnić je w pliku projektu.**</span><span class="sxs-lookup"><span data-stu-id="75d72-159">**Duplicate Compile items were included. The .NET SDK includes Compile items from your project directory by default. You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.**</span></span>

<span data-ttu-id="75d72-160">Aby rozwiązać ten błąd, `Compile` usuń jawne elementy, które pasują do niejawnych `EnableDefaultCompileItems` wymienionych `false`w poprzedniej tabeli, lub ustaw właściwość , która wyłącza niejawne włączenie:</span><span class="sxs-lookup"><span data-stu-id="75d72-160">To resolve the error, either remove the explicit `Compile` items that match the implicit ones listed on the previous table, or set the `EnableDefaultCompileItems` property to `false`, which disables implicit inclusion:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="75d72-161">Jeśli chcesz określić, na przykład, niektóre pliki, aby uzyskać opublikowane z aplikacją, nadal można użyć `Content` znanych mechanizmów MSBuild dla tego, na przykład element.</span><span class="sxs-lookup"><span data-stu-id="75d72-161">If you want to specify, for example, some files to get published with your app, you can still use the known MSBuild mechanisms for that, for example, the `Content` element.</span></span>

<span data-ttu-id="75d72-162">`EnableDefaultCompileItems`wyłącza tylko `Compile` globs, ale nie ma wpływu na `None` inne globs, \*jak niejawny glob, który odnosi się również do elementów .cs.</span><span class="sxs-lookup"><span data-stu-id="75d72-162">`EnableDefaultCompileItems` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob that also applies to \*.cs items.</span></span> <span data-ttu-id="75d72-163">Z tego powodu Eksplorator rozwiązań w programie Visual Studio pokazuje \*elementy .cs jako część projektu, uwzględnione jako `None` elementy.</span><span class="sxs-lookup"><span data-stu-id="75d72-163">Because of that, Solution Explorer in Visual Studio shows \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="75d72-164">Aby wyłączyć `None` niejawny glob, ustaw `EnableDefaultNoneItems` na `false`:</span><span class="sxs-lookup"><span data-stu-id="75d72-164">To disable the implicit `None` glob, set `EnableDefaultNoneItems` to `false`:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="75d72-165">Aby wyłączyć *wszystkie* niejawne `EnableDefaultItems` globs, należy ustawić właściwość na: `false`</span><span class="sxs-lookup"><span data-stu-id="75d72-165">To disable *all* implicit globs, set the `EnableDefaultItems` property to `false`:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="customize-the-build"></a><span data-ttu-id="75d72-166">Dostosowywanie kompilacji</span><span class="sxs-lookup"><span data-stu-id="75d72-166">Customize the build</span></span>

<span data-ttu-id="75d72-167">Istnieją różne sposoby [dostosowywania kompilacji.](/visualstudio/msbuild/customize-your-build)</span><span class="sxs-lookup"><span data-stu-id="75d72-167">There are various ways to [customize a build](/visualstudio/msbuild/customize-your-build).</span></span> <span data-ttu-id="75d72-168">Można zastąpić właściwość, przekazując ją jako argument do polecenia [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) lub [dotnet.](../tools/index.md)</span><span class="sxs-lookup"><span data-stu-id="75d72-168">You may want to override a property by passing it as an argument to an [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) or [dotnet](../tools/index.md) command.</span></span> <span data-ttu-id="75d72-169">Można również dodać właściwość do pliku projektu lub pliku *Directory.Build.props.*</span><span class="sxs-lookup"><span data-stu-id="75d72-169">You can also add the property to the project file or to a *Directory.Build.props* file.</span></span> <span data-ttu-id="75d72-170">Aby uzyskać listę przydatnych właściwości dla projektów programu .NET Core, zobacz [właściwości MSBuild dla projektów SDK .NET Core](msbuild-props.md).</span><span class="sxs-lookup"><span data-stu-id="75d72-170">For a list of useful properties for .NET Core projects, see [MSBuild properties for .NET Core SDK projects](msbuild-props.md).</span></span>

### <a name="custom-targets"></a><span data-ttu-id="75d72-171">Niestandardowe cele</span><span class="sxs-lookup"><span data-stu-id="75d72-171">Custom targets</span></span>

<span data-ttu-id="75d72-172">.NET Core projekty można spakować niestandardowe msbuild cele i właściwości do użytku przez projekty, które zużywają pakiet.</span><span class="sxs-lookup"><span data-stu-id="75d72-172">.NET Core projects can package custom MSBuild targets and properties for use by projects that consume the package.</span></span> <span data-ttu-id="75d72-173">Użyj tego typu rozszerzalności, jeśli chcesz:</span><span class="sxs-lookup"><span data-stu-id="75d72-173">Use this type of extensibility when you want to:</span></span>

- <span data-ttu-id="75d72-174">Rozszerz proces kompilacji.</span><span class="sxs-lookup"><span data-stu-id="75d72-174">Extend the build process.</span></span>
- <span data-ttu-id="75d72-175">Dostęp artefakty procesu kompilacji, takich jak wygenerowane pliki.</span><span class="sxs-lookup"><span data-stu-id="75d72-175">Access artifacts of the build process, such as generated files.</span></span>
- <span data-ttu-id="75d72-176">Sprawdź konfigurację, w której jest wywoływana kompilacja.</span><span class="sxs-lookup"><span data-stu-id="75d72-176">Inspect the configuration under which the build is invoked.</span></span>

<span data-ttu-id="75d72-177">Dodaj niestandardowe obiekty docelowe kompilacji lub właściwości, `<package_id>.props` umieszczając pliki `Contoso.Utility.UsefulStuff.targets`w formularzu `<package_id>.targets` lub (na przykład) w folderze *kompilacji* projektu.</span><span class="sxs-lookup"><span data-stu-id="75d72-177">You add custom build targets or properties by placing files in the form `<package_id>.targets` or `<package_id>.props` (for example, `Contoso.Utility.UsefulStuff.targets`) in the *build* folder of the project.</span></span>

<span data-ttu-id="75d72-178">Poniższy kod XML jest urywkiem pliku *csproj,* [`dotnet pack`](../tools/dotnet-pack.md) który instruuje polecenie, co spakować.</span><span class="sxs-lookup"><span data-stu-id="75d72-178">The following XML is a snippet from a *.csproj* file that instructs the [`dotnet pack`](../tools/dotnet-pack.md) command what to package.</span></span> <span data-ttu-id="75d72-179">Element `<ItemGroup Label="dotnet pack instructions">` umieszcza pliki docelowe w folderze *kompilacji* wewnątrz pakietu.</span><span class="sxs-lookup"><span data-stu-id="75d72-179">The `<ItemGroup Label="dotnet pack instructions">` element places the targets files into the *build* folder inside the package.</span></span> <span data-ttu-id="75d72-180">Element `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` umieszcza zestawy i pliki *json* w folderze *kompilacji.*</span><span class="sxs-lookup"><span data-stu-id="75d72-180">The `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` element places the assemblies and *.json* files into the *build* folder.</span></span>

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

<span data-ttu-id="75d72-181">Aby użyć niestandardowego obiektu docelowego `PackageReference` w projekcie, dodaj element, który wskazuje pakiet i jego wersję.</span><span class="sxs-lookup"><span data-stu-id="75d72-181">To consume a custom target in your project, add a `PackageReference` element that points to the package and its version.</span></span> <span data-ttu-id="75d72-182">W przeciwieństwie do narzędzi pakiet niestandardowych obiektów docelowych znajduje się w zamknięciu zależności zużywania projektu.</span><span class="sxs-lookup"><span data-stu-id="75d72-182">Unlike the tools, the custom targets package is included in the consuming project's dependency closure.</span></span>

<span data-ttu-id="75d72-183">Można skonfigurować sposób używania niestandardowego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="75d72-183">You can configure how to use the custom target.</span></span> <span data-ttu-id="75d72-184">Ponieważ jest to obiekt docelowy MSBuild, może zależeć od danego obiektu docelowego, uruchomić `dotnet msbuild -t:<target-name>` po innym miejscu docelowym lub być wywoływane ręcznie za pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="75d72-184">Since it's an MSBuild target, it can depend on a given target, run after another target, or be manually invoked by using the `dotnet msbuild -t:<target-name>` command.</span></span> <span data-ttu-id="75d72-185">Jednak aby zapewnić lepsze środowisko użytkownika, można połączyć narzędzia dla poszczególnych projektów i niestandardowe cele.</span><span class="sxs-lookup"><span data-stu-id="75d72-185">However, to provide a better user experience, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="75d72-186">W tym scenariuszu narzędzie dla projektu akceptuje wszystkie parametry są potrzebne i [`dotnet msbuild`](../tools/dotnet-msbuild.md) przekłada się na wymagane wywołanie, które wykonuje obiekt docelowy.</span><span class="sxs-lookup"><span data-stu-id="75d72-186">In this scenario, the per-project tool accepts whatever parameters are needed and translates that into the required [`dotnet msbuild`](../tools/dotnet-msbuild.md) invocation that executes the target.</span></span> <span data-ttu-id="75d72-187">Możesz zobaczyć próbkę tego rodzaju synergii na [MVP Summit 2016 Hackathon próbki](https://github.com/dotnet/MVPSummitHackathon2016) repo w [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) projekcie.</span><span class="sxs-lookup"><span data-stu-id="75d72-187">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

## <a name="see-also"></a><span data-ttu-id="75d72-188">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="75d72-188">See also</span></span>

- [<span data-ttu-id="75d72-189">Instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="75d72-189">Install .NET Core</span></span>](../install/index.md)
- [<span data-ttu-id="75d72-190">Jak korzystać z zestawów SDK projektu MSBuild</span><span class="sxs-lookup"><span data-stu-id="75d72-190">How to use MSBuild project SDKs</span></span>](/visualstudio/msbuild/how-to-use-project-sdk)
- [<span data-ttu-id="75d72-191">Pakiet niestandardowych celów MSBuild i rekwizyty z NuGet</span><span class="sxs-lookup"><span data-stu-id="75d72-191">Package custom MSBuild targets and props with NuGet</span></span>](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
