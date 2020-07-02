---
title: Omówienie zestawu SDK programu .NET Core
titleSuffix: ''
description: Dowiedz się więcej o zestawach SDK projektu .NET Core.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: 9db62ab7774e3dd71412fa346d78ae0c62a2f81f
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803044"
---
# <a name="net-core-project-sdks"></a><span data-ttu-id="c3877-103">Zestawy SDK projektu .NET Core</span><span class="sxs-lookup"><span data-stu-id="c3877-103">.NET Core project SDKs</span></span>

<span data-ttu-id="c3877-104">Projekty .NET Core są skojarzone z zestawem SDK (Software Development Kit).</span><span class="sxs-lookup"><span data-stu-id="c3877-104">.NET Core projects are associated with a software development kit (SDK).</span></span> <span data-ttu-id="c3877-105">Każdy *zestaw SDK projektu* to zestaw [obiektów docelowych](/visualstudio/msbuild/msbuild-targets) programu MSBuild i skojarzonych [zadań](/visualstudio/msbuild/msbuild-tasks) , które są odpowiedzialne za kompilowanie, pakowanie i publikowanie kodu.</span><span class="sxs-lookup"><span data-stu-id="c3877-105">Each *project SDK* is a set of MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span> <span data-ttu-id="c3877-106">Projekt, który odwołuje się do zestawu SDK projektu, jest czasami określany jako *projekt w stylu zestawu SDK*.</span><span class="sxs-lookup"><span data-stu-id="c3877-106">A project that references a project SDK is sometimes referred to as an *SDK-style project*.</span></span>

## <a name="available-sdks"></a><span data-ttu-id="c3877-107">Dostępne zestawy SDK</span><span class="sxs-lookup"><span data-stu-id="c3877-107">Available SDKs</span></span>

<span data-ttu-id="c3877-108">Dostępne są następujące zestawy SDK dla platformy .NET Core:</span><span class="sxs-lookup"><span data-stu-id="c3877-108">The following SDKs are available for .NET Core:</span></span>

| <span data-ttu-id="c3877-109">ID</span><span class="sxs-lookup"><span data-stu-id="c3877-109">ID</span></span> | <span data-ttu-id="c3877-110">Opis</span><span class="sxs-lookup"><span data-stu-id="c3877-110">Description</span></span> | <span data-ttu-id="c3877-111">Repozytorium</span><span class="sxs-lookup"><span data-stu-id="c3877-111">Repo</span></span>|
| - | - | - |
| `Microsoft.NET.Sdk` | <span data-ttu-id="c3877-112">Zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="c3877-112">The .NET Core SDK</span></span> | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Web` | <span data-ttu-id="c3877-113">[Zestaw SDK sieci Web](/aspnet/core/razor-pages/web-sdk) platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="c3877-113">The .NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk)</span></span> | <https://github.com/aspnet/websdk> |
| `Microsoft.NET.Sdk.Razor` | <span data-ttu-id="c3877-114">[Zestaw SDK](/aspnet/core/razor-pages/sdk) programu .NET Core Razor</span><span class="sxs-lookup"><span data-stu-id="c3877-114">The .NET Core [Razor SDK](/aspnet/core/razor-pages/sdk)</span></span> |
| `Microsoft.NET.Sdk.Worker` | <span data-ttu-id="c3877-115">Zestaw SDK usługi procesu roboczego platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="c3877-115">The .NET Core Worker Service SDK</span></span> |
| `Microsoft.NET.Sdk.WindowsDesktop` | <span data-ttu-id="c3877-116">Podstawowe WinForms i zestaw WPF SDK platformy .NET</span><span class="sxs-lookup"><span data-stu-id="c3877-116">The .NET Core WinForms and WPF SDK</span></span> |

<span data-ttu-id="c3877-117">Zestaw .NET Core SDK jest podstawowym zestawem SDK dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c3877-117">The .NET Core SDK is the base SDK for .NET Core.</span></span> <span data-ttu-id="c3877-118">Inne zestawy SDK odwołują się do zestaw .NET Core SDK i projekty, które są skojarzone z innymi zestawami SDK, mają dostępne wszystkie właściwości zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="c3877-118">The other SDKs reference the .NET Core SDK, and projects that are associated with the other SDKs have all the .NET Core SDK properties available to them.</span></span> <span data-ttu-id="c3877-119">Zestaw SDK sieci Web, na przykład, zależy od zestaw .NET Core SDK i zestawu Razor SDK.</span><span class="sxs-lookup"><span data-stu-id="c3877-119">The Web SDK, for example, depends on both the .NET Core SDK and the Razor SDK.</span></span>

<span data-ttu-id="c3877-120">Możesz również utworzyć własny zestaw SDK, który może być dystrybuowany za pośrednictwem programu NuGet.</span><span class="sxs-lookup"><span data-stu-id="c3877-120">You can also author your own SDK that can be distributed via NuGet.</span></span>

## <a name="project-files"></a><span data-ttu-id="c3877-121">Pliki projektu</span><span class="sxs-lookup"><span data-stu-id="c3877-121">Project files</span></span>

<span data-ttu-id="c3877-122">Projekty .NET Core są oparte na formacie programu [MSBuild](/visualstudio/msbuild/msbuild) .</span><span class="sxs-lookup"><span data-stu-id="c3877-122">.NET Core projects are based on the [MSBuild](/visualstudio/msbuild/msbuild) format.</span></span> <span data-ttu-id="c3877-123">Pliki projektu, które mają rozszerzenia, takie jak *. csproj* dla projektów C# i *. fsproj* dla projektów F #, są w formacie XML.</span><span class="sxs-lookup"><span data-stu-id="c3877-123">Project files, which have extensions like *.csproj* for C# projects and *.fsproj* for F# projects, are in XML format.</span></span> <span data-ttu-id="c3877-124">Głównym elementem pliku projektu MSBuild jest element [projektu](/visualstudio/msbuild/project-element-msbuild) .</span><span class="sxs-lookup"><span data-stu-id="c3877-124">The root element of an MSBuild project file is the [Project](/visualstudio/msbuild/project-element-msbuild) element.</span></span> <span data-ttu-id="c3877-125">`Project`Element ma opcjonalny `Sdk` atrybut, który określa zestaw SDK (i wersję) do użycia.</span><span class="sxs-lookup"><span data-stu-id="c3877-125">The `Project` element has an optional `Sdk` attribute that specifies which SDK (and version) to use.</span></span> <span data-ttu-id="c3877-126">Aby użyć narzędzi .NET Core i skompilować swój kod, należy ustawić `Sdk` atrybut na jeden z identyfikatorów w tabeli [dostępnych zestawów SDK](#available-sdks) .</span><span class="sxs-lookup"><span data-stu-id="c3877-126">To use the .NET Core tools and build your code, set the `Sdk` attribute to one of the IDs in the [Available SDKs](#available-sdks) table.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

<span data-ttu-id="c3877-127">Aby określić zestaw SDK pochodzący z programu NuGet, należy dołączyć wersję na końcu nazwy lub określić nazwę i wersję w *global.js* pliku.</span><span class="sxs-lookup"><span data-stu-id="c3877-127">To specify an SDK that comes from NuGet, include the version at the end of the name, or specify the name and version in the *global.json* file.</span></span>

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

<span data-ttu-id="c3877-128">Innym sposobem określenia zestawu SDK jest element najwyższego poziomu [zestawu SDK](/visualstudio/msbuild/sdk-element-msbuild) :</span><span class="sxs-lookup"><span data-stu-id="c3877-128">Another way to specify the SDK is with the top-level [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span></span>

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

<span data-ttu-id="c3877-129">Odwołujące się do zestawu SDK w jednym z tych sposobów znacznie upraszczają pliki projektu dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c3877-129">Referencing an SDK in one of these ways greatly simplifies project files for .NET Core.</span></span> <span data-ttu-id="c3877-130">Podczas oceniania projektu, MSBuild dodaje niejawne Importy w `Sdk.props` górnej części pliku projektu i `Sdk.targets` w dolnej części.</span><span class="sxs-lookup"><span data-stu-id="c3877-130">While evaluating the project, MSBuild adds implicit imports for `Sdk.props` at the top of the project file and `Sdk.targets` at the bottom.</span></span>

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
> <span data-ttu-id="c3877-131">Na komputerze z systemem Windows pliki *SDK. props* i *SDK. targets* można znaleźć w folderze *%ProgramFiles%\dotnet\sdk \\ [wersja] \Sdks\Microsoft.NET.Sdk\Sdk* .</span><span class="sxs-lookup"><span data-stu-id="c3877-131">On a Windows machine, the *Sdk.props* and *Sdk.targets* files can be found in the *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk* folder.</span></span>

### <a name="preprocess-the-project-file"></a><span data-ttu-id="c3877-132">Wstępnie przetwórz plik projektu</span><span class="sxs-lookup"><span data-stu-id="c3877-132">Preprocess the project file</span></span>

<span data-ttu-id="c3877-133">Można zobaczyć w pełni rozwinięty projekt, gdy program MSBuild widzi go po zestawie SDK i jego obiektach docelowych za pomocą `dotnet msbuild -preprocess` polecenia.</span><span class="sxs-lookup"><span data-stu-id="c3877-133">You can see the fully expanded project as MSBuild sees it after the SDK and its targets are included by using the `dotnet msbuild -preprocess` command.</span></span> <span data-ttu-id="c3877-134">Przełącznik [preprocesora](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) [`dotnet msbuild`](../tools/dotnet-msbuild.md) polecenia pokazuje, które pliki są importowane, ich źródła i ich wkłady do kompilacji bez faktycznego kompilowania projektu.</span><span class="sxs-lookup"><span data-stu-id="c3877-134">The [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) switch of the [`dotnet msbuild`](../tools/dotnet-msbuild.md) command shows which files are imported, their sources, and their contributions to the build without actually building the project.</span></span>

<span data-ttu-id="c3877-135">Jeśli projekt ma wiele platform docelowych, należy skoncentrować wyniki polecenia tylko dla jednej struktury, określając ją jako właściwość programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="c3877-135">If the project has multiple target frameworks, focus the results of the command on only one framework by specifying it as an MSBuild property.</span></span> <span data-ttu-id="c3877-136">Przykład:</span><span class="sxs-lookup"><span data-stu-id="c3877-136">For example:</span></span>

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a><span data-ttu-id="c3877-137">Domyślna kompilacja obejmuje</span><span class="sxs-lookup"><span data-stu-id="c3877-137">Default compilation includes</span></span>

<span data-ttu-id="c3877-138">Wartość domyślna to include i Exclude dla elementów kompilowania, zasobów osadzonych i `None` elementów zdefiniowanych w zestawie SDK.</span><span class="sxs-lookup"><span data-stu-id="c3877-138">The default includes and excludes for compile items, embedded resources, and `None` items are defined in the SDK.</span></span> <span data-ttu-id="c3877-139">W przeciwieństwie do projektów .NET Framework nie należących do zestawu SDK, nie trzeba określać tych elementów w pliku projektu, ponieważ ustawienia domyślne obejmują najczęściej spotykane przypadki użycia.</span><span class="sxs-lookup"><span data-stu-id="c3877-139">Unlike non-SDK .NET Framework projects, you don't need to specify these items in your project file, because the defaults cover most common use cases.</span></span> <span data-ttu-id="c3877-140">Sprawia to, że plik projektu jest mniejszy i łatwiejszy do zrozumienia i edycji, w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="c3877-140">This makes the project file smaller and easier to understand and edit by hand, if needed.</span></span>

<span data-ttu-id="c3877-141">W poniższej tabeli pokazano, które elementy i które [elementy globalne](https://en.wikipedia.org/wiki/Glob_(programming)) są uwzględnione i wykluczone w zestaw .NET Core SDK:</span><span class="sxs-lookup"><span data-stu-id="c3877-141">The following table shows which elements and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET Core SDK:</span></span>

| <span data-ttu-id="c3877-142">Element</span><span class="sxs-lookup"><span data-stu-id="c3877-142">Element</span></span>           | <span data-ttu-id="c3877-143">Uwzględnij globalizowania</span><span class="sxs-lookup"><span data-stu-id="c3877-143">Include glob</span></span>                              | <span data-ttu-id="c3877-144">Wyklucz globalizowania</span><span class="sxs-lookup"><span data-stu-id="c3877-144">Exclude glob</span></span>                                                  | <span data-ttu-id="c3877-145">Usuń globalizowania</span><span class="sxs-lookup"><span data-stu-id="c3877-145">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| <span data-ttu-id="c3877-146">Opracowania</span><span class="sxs-lookup"><span data-stu-id="c3877-146">Compile</span></span>           | <span data-ttu-id="c3877-147">\*\*/\*. cs (lub inne rozszerzenia językowe)</span><span class="sxs-lookup"><span data-stu-id="c3877-147">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="c3877-148">\*\*/\*Użytkownicy  \*\*/\*.\* proj  \*\*/\*. sln  \*\*/\*. vssscc</span><span class="sxs-lookup"><span data-stu-id="c3877-148">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="c3877-149">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="c3877-149">N/A</span></span>                      |
| <span data-ttu-id="c3877-150">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="c3877-150">EmbeddedResource</span></span>  | <span data-ttu-id="c3877-151">\*\*/\*. resx</span><span class="sxs-lookup"><span data-stu-id="c3877-151">\*\*/\*.resx</span></span>                              | <span data-ttu-id="c3877-152">\*\*/\*Użytkownicy \*\*/\*.\* proj \*\*/\*. sln \*\*/\*. vssscc</span><span class="sxs-lookup"><span data-stu-id="c3877-152">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="c3877-153">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="c3877-153">N/A</span></span>                      |
| <span data-ttu-id="c3877-154">Brak</span><span class="sxs-lookup"><span data-stu-id="c3877-154">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="c3877-155">\*\*/\*Użytkownicy \*\*/\*.\* proj \*\*/\*. sln \*\*/\*. vssscc</span><span class="sxs-lookup"><span data-stu-id="c3877-155">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="c3877-156">\*\*/\*Rejestr \*\*/\*. resx</span><span class="sxs-lookup"><span data-stu-id="c3877-156">\*\*/\*.cs; \*\*/\*.resx</span></span> |

> [!NOTE]
> <span data-ttu-id="c3877-157">`./bin`Foldery i `./obj` , które są reprezentowane przez `$(BaseOutputPath)` właściwości i programu `$(BaseIntermediateOutputPath)` MSBuild, są domyślnie wykluczone z elementy globalne.</span><span class="sxs-lookup"><span data-stu-id="c3877-157">The `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, are excluded from the globs by default.</span></span> <span data-ttu-id="c3877-158">Wykluczenia są reprezentowane przez właściwość `$(DefaultItemExcludes)` .</span><span class="sxs-lookup"><span data-stu-id="c3877-158">Excludes are represented by the property `$(DefaultItemExcludes)`.</span></span>

#### <a name="build-errors"></a><span data-ttu-id="c3877-159">Błędy kompilacji</span><span class="sxs-lookup"><span data-stu-id="c3877-159">Build errors</span></span>

<span data-ttu-id="c3877-160">Jeśli jawnie zdefiniujesz dowolny z tych elementów w pliku projektu, możesz uzyskać błąd kompilacji "NETSDK1022" podobny do poniższego:</span><span class="sxs-lookup"><span data-stu-id="c3877-160">If you explicitly define any of these items in your project file, you're likely to get a "NETSDK1022" build error similar to the following:</span></span>

  > <span data-ttu-id="c3877-161">Uwzględniono zduplikowane elementy "Kompiluj".</span><span class="sxs-lookup"><span data-stu-id="c3877-161">Duplicate 'Compile' items were included.</span></span> <span data-ttu-id="c3877-162">Zestaw SDK platformy .NET domyślnie zawiera elementy "Kompiluj" z katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="c3877-162">The .NET SDK includes 'Compile' items from your project directory by default.</span></span> <span data-ttu-id="c3877-163">Możesz usunąć te elementy z pliku projektu lub ustawić właściwość "EnableDefaultCompileItems" na wartość "false", jeśli chcesz jawnie uwzględnić je w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="c3877-163">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

  > <span data-ttu-id="c3877-164">Uwzględniono zduplikowane elementy "EmbeddedResource".</span><span class="sxs-lookup"><span data-stu-id="c3877-164">Duplicate 'EmbeddedResource' items were included.</span></span> <span data-ttu-id="c3877-165">Zestaw SDK platformy .NET domyślnie zawiera elementy "EmbeddedResource" z katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="c3877-165">The .NET SDK includes 'EmbeddedResource' items from your project directory by default.</span></span> <span data-ttu-id="c3877-166">Możesz usunąć te elementy z pliku projektu lub ustawić właściwość "EnableDefaultEmbeddedResourceItems" na wartość "false", jeśli chcesz jawnie uwzględnić je w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="c3877-166">You can either remove these items from your project file, or set the 'EnableDefaultEmbeddedResourceItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="c3877-167">Aby rozwiązać te błędy, wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="c3877-167">To resolve the errors, do one of the following:</span></span>

- <span data-ttu-id="c3877-168">Usuń jawne `Compile` , `EmbeddedResource` lub elementy, `None` które są zgodne z niejawnymi wymienionymi w poprzedniej tabeli.</span><span class="sxs-lookup"><span data-stu-id="c3877-168">Remove the explicit `Compile`, `EmbeddedResource`, or `None` items that match the implicit ones listed on the previous table.</span></span>

- <span data-ttu-id="c3877-169">Ustaw `EnableDefaultItems` Właściwość na `false` , aby wyłączyć wszystkie niejawne dołączenie do pliku:</span><span class="sxs-lookup"><span data-stu-id="c3877-169">Set the `EnableDefaultItems` property to `false` to disable all implicit file inclusion:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="c3877-170">Jeśli chcesz określić pliki do opublikowania w aplikacji, nadal możesz użyć znanych mechanizmów programu MSBuild dla tego elementu, na przykład `Content` .</span><span class="sxs-lookup"><span data-stu-id="c3877-170">If you want to specify files to be published with your app, you can still use the known MSBuild mechanisms for that, for example, the `Content` element.</span></span>

- <span data-ttu-id="c3877-171">Selektywnie Wyłącz tylko `Compile` , `EmbeddedResource` lub `None` elementy globalne, ustawiając `EnableDefaultCompileItems` Właściwość, `EnableDefaultEmbeddedResourceItems` , lub `EnableDefaultNoneItems` na `false` :</span><span class="sxs-lookup"><span data-stu-id="c3877-171">Selectively disable only `Compile`, `EmbeddedResource`, or `None` globs by setting the `EnableDefaultCompileItems`, `EnableDefaultEmbeddedResourceItems`, or `EnableDefaultNoneItems` property to `false`:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
    <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="c3877-172">Jeśli wyłączysz tylko `Compile` elementy globalne, Eksplorator rozwiązań w programie Visual Studio nadal pokazuje \* elementy CS jako część projektu, uwzględnione jako `None` elementy.</span><span class="sxs-lookup"><span data-stu-id="c3877-172">If you only disable `Compile` globs, Solution Explorer in Visual Studio still shows \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="c3877-173">Aby wyłączyć niejawną `None` globalizowania, ustaw `EnableDefaultNoneItems` ją na wartość `false` .</span><span class="sxs-lookup"><span data-stu-id="c3877-173">To disable the implicit `None` glob, set `EnableDefaultNoneItems` to `false` too.</span></span>

## <a name="customize-the-build"></a><span data-ttu-id="c3877-174">Dostosuj kompilację</span><span class="sxs-lookup"><span data-stu-id="c3877-174">Customize the build</span></span>

<span data-ttu-id="c3877-175">Istnieją różne sposoby [dostosowywania kompilacji](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="c3877-175">There are various ways to [customize a build](/visualstudio/msbuild/customize-your-build).</span></span> <span data-ttu-id="c3877-176">Możesz chcieć przesłonić Właściwość przez przekazanie jej jako argumentu do polecenia [MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) lub [dotnet](../tools/index.md) .</span><span class="sxs-lookup"><span data-stu-id="c3877-176">You may want to override a property by passing it as an argument to an [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) or [dotnet](../tools/index.md) command.</span></span> <span data-ttu-id="c3877-177">Możesz również dodać właściwość do pliku projektu lub do pliku *Directory. Build. props* .</span><span class="sxs-lookup"><span data-stu-id="c3877-177">You can also add the property to the project file or to a *Directory.Build.props* file.</span></span> <span data-ttu-id="c3877-178">Aby uzyskać listę przydatnych właściwości projektów .NET Core, zobacz [Dokumentacja programu MSBuild dla projektów zestaw .NET Core SDK](msbuild-props.md).</span><span class="sxs-lookup"><span data-stu-id="c3877-178">For a list of useful properties for .NET Core projects, see [MSBuild reference for .NET Core SDK projects](msbuild-props.md).</span></span>

### <a name="custom-targets"></a><span data-ttu-id="c3877-179">Niestandardowe elementy docelowe</span><span class="sxs-lookup"><span data-stu-id="c3877-179">Custom targets</span></span>

<span data-ttu-id="c3877-180">Projekty .NET Core mogą spakować niestandardowe cele programu MSBuild i właściwości do użycia przez projekty korzystające z pakietu.</span><span class="sxs-lookup"><span data-stu-id="c3877-180">.NET Core projects can package custom MSBuild targets and properties for use by projects that consume the package.</span></span> <span data-ttu-id="c3877-181">Użyj tego typu rozszerzalności, gdy chcesz:</span><span class="sxs-lookup"><span data-stu-id="c3877-181">Use this type of extensibility when you want to:</span></span>

- <span data-ttu-id="c3877-182">Rozwiń proces kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c3877-182">Extend the build process.</span></span>
- <span data-ttu-id="c3877-183">Dostęp do artefaktów procesu kompilacji, takich jak wygenerowane pliki.</span><span class="sxs-lookup"><span data-stu-id="c3877-183">Access artifacts of the build process, such as generated files.</span></span>
- <span data-ttu-id="c3877-184">Sprawdź konfigurację, pod którą jest wywoływana kompilacja.</span><span class="sxs-lookup"><span data-stu-id="c3877-184">Inspect the configuration under which the build is invoked.</span></span>

<span data-ttu-id="c3877-185">Dodawanie niestandardowych elementów docelowych kompilacji lub właściwości przez umieszczenie plików w formularzu `<package_id>.targets` lub `<package_id>.props` (na przykład `Contoso.Utility.UsefulStuff.targets` ) w folderze *Build* projektu.</span><span class="sxs-lookup"><span data-stu-id="c3877-185">You add custom build targets or properties by placing files in the form `<package_id>.targets` or `<package_id>.props` (for example, `Contoso.Utility.UsefulStuff.targets`) in the *build* folder of the project.</span></span>

<span data-ttu-id="c3877-186">Poniższy kod XML to fragment z pliku *. csproj* , który instruuje [`dotnet pack`](../tools/dotnet-pack.md) polecenie do pakowania.</span><span class="sxs-lookup"><span data-stu-id="c3877-186">The following XML is a snippet from a *.csproj* file that instructs the [`dotnet pack`](../tools/dotnet-pack.md) command what to package.</span></span> <span data-ttu-id="c3877-187">`<ItemGroup Label="dotnet pack instructions">`Element umieszcza pliki docelowe w folderze *kompilacji* wewnątrz pakietu.</span><span class="sxs-lookup"><span data-stu-id="c3877-187">The `<ItemGroup Label="dotnet pack instructions">` element places the targets files into the *build* folder inside the package.</span></span> <span data-ttu-id="c3877-188">`<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">`Element umieszcza zestawy i pliki *JSON* w folderze *Build* .</span><span class="sxs-lookup"><span data-stu-id="c3877-188">The `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` element places the assemblies and *.json* files into the *build* folder.</span></span>

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

<span data-ttu-id="c3877-189">Aby użyć niestandardowego obiektu docelowego w projekcie, Dodaj element wskazujący `PackageReference` pakiet i jego wersję.</span><span class="sxs-lookup"><span data-stu-id="c3877-189">To consume a custom target in your project, add a `PackageReference` element that points to the package and its version.</span></span> <span data-ttu-id="c3877-190">W przeciwieństwie do narzędzi, pakiet Custom targets jest uwzględniany w zamknięciu zależności projektu zużywanego.</span><span class="sxs-lookup"><span data-stu-id="c3877-190">Unlike the tools, the custom targets package is included in the consuming project's dependency closure.</span></span>

<span data-ttu-id="c3877-191">Można skonfigurować sposób używania niestandardowego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="c3877-191">You can configure how to use the custom target.</span></span> <span data-ttu-id="c3877-192">Ponieważ jest to element docelowy programu MSBuild, może on zależeć od danego elementu docelowego, działać po innym elemencie docelowym lub być wywoływana ręcznie przy użyciu `dotnet msbuild -t:<target-name>` polecenia.</span><span class="sxs-lookup"><span data-stu-id="c3877-192">Since it's an MSBuild target, it can depend on a given target, run after another target, or be manually invoked by using the `dotnet msbuild -t:<target-name>` command.</span></span> <span data-ttu-id="c3877-193">Aby jednak zapewnić lepsze środowisko użytkownika, można połączyć narzędzia dla poszczególnych projektów i niestandardowe elementy docelowe.</span><span class="sxs-lookup"><span data-stu-id="c3877-193">However, to provide a better user experience, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="c3877-194">W tym scenariuszu narzędzie dla projektu akceptuje wszelkie parametry, które są potrzebne, i tłumaczy je na wymagane [`dotnet msbuild`](../tools/dotnet-msbuild.md) wywołanie, które wykonuje miejsce docelowe.</span><span class="sxs-lookup"><span data-stu-id="c3877-194">In this scenario, the per-project tool accepts whatever parameters are needed and translates that into the required [`dotnet msbuild`](../tools/dotnet-msbuild.md) invocation that executes the target.</span></span> <span data-ttu-id="c3877-195">Możesz zobaczyć przykład tego rodzaju synergii w repozytorium [przykładów Hackathonych](https://github.com/dotnet/MVPSummitHackathon2016) w projekcie programu 2016 MVP [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) .</span><span class="sxs-lookup"><span data-stu-id="c3877-195">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

## <a name="see-also"></a><span data-ttu-id="c3877-196">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3877-196">See also</span></span>

- [<span data-ttu-id="c3877-197">Instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="c3877-197">Install .NET Core</span></span>](../install/index.yml)
- [<span data-ttu-id="c3877-198">Jak używać zestawów SDK projektu MSBuild</span><span class="sxs-lookup"><span data-stu-id="c3877-198">How to use MSBuild project SDKs</span></span>](/visualstudio/msbuild/how-to-use-project-sdk)
- [<span data-ttu-id="c3877-199">Pakowanie niestandardowych elementów docelowych programu MSBuild i ich właściwości przy użyciu narzędzia NuGet</span><span class="sxs-lookup"><span data-stu-id="c3877-199">Package custom MSBuild targets and props with NuGet</span></span>](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
