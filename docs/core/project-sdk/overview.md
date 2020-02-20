---
title: Omówienie zestawu SDK programu .NET Core
description: Dowiedz się więcej o zestawach SDK projektu .NET Core.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: b1b839f81b1b4a8d20dbb34d3d2fc000c64acb8a
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453805"
---
# <a name="net-core-project-sdks"></a><span data-ttu-id="f61fb-103">Zestawy SDK projektu .NET Core</span><span class="sxs-lookup"><span data-stu-id="f61fb-103">.NET Core project SDKs</span></span>

<span data-ttu-id="f61fb-104">Projekty .NET Core są skojarzone z zestawem SDK (Software Development Kit).</span><span class="sxs-lookup"><span data-stu-id="f61fb-104">.NET Core projects are associated with a software development kit (SDK).</span></span> <span data-ttu-id="f61fb-105">Każdy zestaw SDK projektu to zestaw [obiektów docelowych](/visualstudio/msbuild/msbuild-targets) programu MSBuild i skojarzonych [zadań](/visualstudio/msbuild/msbuild-tasks) , które są odpowiedzialne za kompilowanie, pakowanie i publikowanie kodu.</span><span class="sxs-lookup"><span data-stu-id="f61fb-105">Each project SDK is a set of MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span>

## <a name="available-sdks"></a><span data-ttu-id="f61fb-106">Dostępne zestawy SDK</span><span class="sxs-lookup"><span data-stu-id="f61fb-106">Available SDKs</span></span>

<span data-ttu-id="f61fb-107">Dostępne są następujące zestawy SDK dla platformy .NET Core:</span><span class="sxs-lookup"><span data-stu-id="f61fb-107">The following SDKs are available for .NET Core:</span></span>

| <span data-ttu-id="f61fb-108">ID</span><span class="sxs-lookup"><span data-stu-id="f61fb-108">ID</span></span> | <span data-ttu-id="f61fb-109">Opis</span><span class="sxs-lookup"><span data-stu-id="f61fb-109">Description</span></span> | <span data-ttu-id="f61fb-110">Repo</span><span class="sxs-lookup"><span data-stu-id="f61fb-110">Repo</span></span>|
| - | - | - |
| `Microsoft.NET.Sdk` | <span data-ttu-id="f61fb-111">Zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="f61fb-111">The .NET Core SDK</span></span> | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | <span data-ttu-id="f61fb-112">[Zestaw SDK sieci Web](/aspnet/core/razor-pages/web-sdk) platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="f61fb-112">The .NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk)</span></span> | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | <span data-ttu-id="f61fb-113">[Zestaw SDK](/aspnet/core/razor-pages/sdk) programu .NET Core Razor</span><span class="sxs-lookup"><span data-stu-id="f61fb-113">The .NET Core [Razor SDK](/aspnet/core/razor-pages/sdk)</span></span> |
| `Microsoft.NET.Sdk.Worker` | <span data-ttu-id="f61fb-114">Zestaw SDK usługi procesu roboczego platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="f61fb-114">The .NET Core Worker Service SDK</span></span> |
| `Microsoft.NET.Sdk.WindowsDesktop` | <span data-ttu-id="f61fb-115">Podstawowe WinForms i zestaw WPF SDK platformy .NET</span><span class="sxs-lookup"><span data-stu-id="f61fb-115">The .NET Core WinForms and WPF SDK</span></span> |

<span data-ttu-id="f61fb-116">Zestaw .NET Core SDK jest podstawowym zestawem SDK dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f61fb-116">The .NET Core SDK is the base SDK for .NET Core.</span></span> <span data-ttu-id="f61fb-117">Inne zestawy SDK odwołują się do zestaw .NET Core SDK i projekty, które są skojarzone z innymi zestawami SDK, mają dostępne wszystkie właściwości zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="f61fb-117">The other SDKs reference the .NET Core SDK, and projects that are associated with the other SDKs have all the .NET Core SDK properties available to them.</span></span> <span data-ttu-id="f61fb-118">Zestaw SDK sieci Web, na przykład, zależy od zestaw .NET Core SDK i zestawu Razor SDK.</span><span class="sxs-lookup"><span data-stu-id="f61fb-118">The Web SDK, for example, depends on both the .NET Core SDK and the Razor SDK.</span></span>

<span data-ttu-id="f61fb-119">Możesz również utworzyć własny zestaw SDK, który może być dystrybuowany za pośrednictwem programu NuGet.</span><span class="sxs-lookup"><span data-stu-id="f61fb-119">You can also author your own SDK that can be distributed via NuGet.</span></span>

## <a name="project-files"></a><span data-ttu-id="f61fb-120">Pliki projektu</span><span class="sxs-lookup"><span data-stu-id="f61fb-120">Project files</span></span>

<span data-ttu-id="f61fb-121">Projekty .NET Core są oparte na formacie programu [MSBuild](/visualstudio/msbuild/msbuild) .</span><span class="sxs-lookup"><span data-stu-id="f61fb-121">.NET Core projects are based on the [MSBuild](/visualstudio/msbuild/msbuild) format.</span></span> <span data-ttu-id="f61fb-122">Pliki projektu, które mają rozszerzenia, takie jak *. csproj* dla C# projektów i *. fsproj* dla F# projektów, są w formacie XML.</span><span class="sxs-lookup"><span data-stu-id="f61fb-122">Project files, which have extensions like *.csproj* for C# projects and *.fsproj* for F# projects, are in XML format.</span></span> <span data-ttu-id="f61fb-123">Głównym elementem pliku projektu MSBuild jest element [projektu](/msbuild/project-element-msbuild) .</span><span class="sxs-lookup"><span data-stu-id="f61fb-123">The root element of an MSBuild project file is the [Project](/msbuild/project-element-msbuild) element.</span></span> <span data-ttu-id="f61fb-124">Element `Project` ma opcjonalny atrybut `Sdk`, który określa zestaw SDK (i wersję), który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="f61fb-124">The `Project` element has an optional `Sdk` attribute that specifies which SDK (and version) to use.</span></span> <span data-ttu-id="f61fb-125">Aby użyć narzędzi .NET Core i skompilować swój kod, ustaw atrybut `Sdk` na jeden z identyfikatorów w tabeli [dostępnych zestawów SDK](#available-sdks) .</span><span class="sxs-lookup"><span data-stu-id="f61fb-125">To use the .NET Core tools and build your code, set the `Sdk` attribute to one of the IDs in the [Available SDKs](#available-sdks) table.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

<span data-ttu-id="f61fb-126">Aby określić zestaw SDK pochodzący z programu NuGet, należy dołączyć wersję na końcu nazwy lub określić nazwę i wersję w pliku *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="f61fb-126">To specify an SDK that comes from NuGet, include the version at the end of the name, or specify the name and version in the *global.json* file.</span></span>

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

<span data-ttu-id="f61fb-127">Innym sposobem określenia zestawu SDK jest element najwyższego poziomu [zestawu SDK](/visualstudio/msbuild/sdk-element-msbuild) :</span><span class="sxs-lookup"><span data-stu-id="f61fb-127">Another way to specify the SDK is with the top-level [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span></span>

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

<span data-ttu-id="f61fb-128">Odwołujące się do zestawu SDK w jednym z tych sposobów znacznie upraszczają pliki projektu dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f61fb-128">Referencing an SDK in one of these ways greatly simplifies project files for .NET Core.</span></span> <span data-ttu-id="f61fb-129">Podczas oceniania projektu, MSBuild dodaje niejawne Importy dla `Sdk.props` w górnej części pliku projektu i `Sdk.targets` na dole.</span><span class="sxs-lookup"><span data-stu-id="f61fb-129">While evaluating the project, MSBuild adds implicit imports for `Sdk.props` at the top of the project file and `Sdk.targets` at the bottom.</span></span>

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
> <span data-ttu-id="f61fb-130">Na komputerze z systemem Windows pliki *SDK. props* i *SDK. targets* znajdują się w folderze *%ProgramFiles%\dotnet\sdk\\[wersja] \Sdks\Microsoft.NET.Sdk\Sdk* .</span><span class="sxs-lookup"><span data-stu-id="f61fb-130">On a Windows machine, the *Sdk.props* and *Sdk.targets* files can be found in the *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk* folder.</span></span>

### <a name="preprocess-the-project-file"></a><span data-ttu-id="f61fb-131">Wstępnie przetwórz plik projektu</span><span class="sxs-lookup"><span data-stu-id="f61fb-131">Preprocess the project file</span></span>

<span data-ttu-id="f61fb-132">Można zobaczyć w pełni rozwinięty projekt, gdy program MSBuild widzi go po zestawie SDK i jego obiektach docelowych za pomocą polecenia `dotnet msbuild -preprocess`.</span><span class="sxs-lookup"><span data-stu-id="f61fb-132">You can see the fully expanded project as MSBuild sees it after the SDK and its targets are included by using the `dotnet msbuild -preprocess` command.</span></span> <span data-ttu-id="f61fb-133">Przełącznik [preprocesora](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) polecenia [`dotnet msbuild`](../tools/dotnet-msbuild.md) pokazuje, które pliki są importowane, ich źródła i ich wkłady do kompilacji bez faktycznego kompilowania projektu.</span><span class="sxs-lookup"><span data-stu-id="f61fb-133">The [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) switch of the [`dotnet msbuild`](../tools/dotnet-msbuild.md) command shows which files are imported, their sources, and their contributions to the build without actually building the project.</span></span>

<span data-ttu-id="f61fb-134">Jeśli projekt ma wiele platform docelowych, należy skoncentrować wyniki polecenia tylko dla jednej struktury, określając ją jako właściwość programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="f61fb-134">If the project has multiple target frameworks, focus the results of the command on only one framework by specifying it as an MSBuild property.</span></span> <span data-ttu-id="f61fb-135">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="f61fb-135">For example:</span></span>

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a><span data-ttu-id="f61fb-136">Domyślna kompilacja obejmuje</span><span class="sxs-lookup"><span data-stu-id="f61fb-136">Default compilation includes</span></span>

<span data-ttu-id="f61fb-137">Wartość domyślna obejmuje i wyklucza elementy kompilowania oraz osadzone zasoby są zdefiniowane w zestawie SDK.</span><span class="sxs-lookup"><span data-stu-id="f61fb-137">The default includes and excludes for compile items and embedded resources are defined in the SDK.</span></span> <span data-ttu-id="f61fb-138">W przeciwieństwie do projektów .NET Framework nie należących do zestawu SDK, nie trzeba określać tych elementów w pliku projektu, ponieważ ustawienia domyślne obejmują najczęściej spotykane przypadki użycia.</span><span class="sxs-lookup"><span data-stu-id="f61fb-138">Unlike non-SDK .NET Framework projects, you don't need to specify these items in your project file, because the defaults cover most common use cases.</span></span> <span data-ttu-id="f61fb-139">Prowadzi to do mniejszych plików projektu, które są łatwiejsze do zrozumienia, a także do edycji, w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="f61fb-139">This leads to smaller project files that are easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="f61fb-140">W poniższej tabeli przedstawiono, który element i które [elementy globalne](https://en.wikipedia.org/wiki/Glob_(programming)) są uwzględnione i wykluczone w zestaw .NET Core SDK:</span><span class="sxs-lookup"><span data-stu-id="f61fb-140">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET Core SDK:</span></span>

| <span data-ttu-id="f61fb-141">Element</span><span class="sxs-lookup"><span data-stu-id="f61fb-141">Element</span></span>           | <span data-ttu-id="f61fb-142">Uwzględnij globalizowania</span><span class="sxs-lookup"><span data-stu-id="f61fb-142">Include glob</span></span>                              | <span data-ttu-id="f61fb-143">Wyklucz globalizowania</span><span class="sxs-lookup"><span data-stu-id="f61fb-143">Exclude glob</span></span>                                                  | <span data-ttu-id="f61fb-144">Usuń globalizowania</span><span class="sxs-lookup"><span data-stu-id="f61fb-144">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| <span data-ttu-id="f61fb-145">Kompilacji</span><span class="sxs-lookup"><span data-stu-id="f61fb-145">Compile</span></span>           | <span data-ttu-id="f61fb-146">\*\*/\*. cs (lub inne rozszerzenia językowe)</span><span class="sxs-lookup"><span data-stu-id="f61fb-146">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="f61fb-147">\*\*/\*. User;  \*\*/\*.\*proj;  \*\*/\*. sln;  \*\*/\*. VSSSCC</span><span class="sxs-lookup"><span data-stu-id="f61fb-147">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="f61fb-148">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="f61fb-148">N/A</span></span>                      |
| <span data-ttu-id="f61fb-149">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="f61fb-149">EmbeddedResource</span></span>  | <span data-ttu-id="f61fb-150">\*\*/\*. resx</span><span class="sxs-lookup"><span data-stu-id="f61fb-150">\*\*/\*.resx</span></span>                              | <span data-ttu-id="f61fb-151">\*\*/\*. User; \*\*/\*.\*proj; \*\*/\*. sln; \*\*/\*. VSSSCC</span><span class="sxs-lookup"><span data-stu-id="f61fb-151">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="f61fb-152">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="f61fb-152">N/A</span></span>                      |
| <span data-ttu-id="f61fb-153">None</span><span class="sxs-lookup"><span data-stu-id="f61fb-153">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="f61fb-154">\*\*/\*. User; \*\*/\*.\*proj; \*\*/\*. sln; \*\*/\*. VSSSCC</span><span class="sxs-lookup"><span data-stu-id="f61fb-154">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="f61fb-155">\*\*/\*. cs; \*\*/\*. resx</span><span class="sxs-lookup"><span data-stu-id="f61fb-155">\*\*/\*.cs; \*\*/\*.resx</span></span> |

> [!NOTE]
> <span data-ttu-id="f61fb-156">Foldery `./bin` i `./obj`, które są reprezentowane przez `$(BaseOutputPath)` i `$(BaseIntermediateOutputPath)` właściwości programu MSBuild, są domyślnie wyłączone z elementy globalne.</span><span class="sxs-lookup"><span data-stu-id="f61fb-156">The `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, are excluded from the globs by default.</span></span> <span data-ttu-id="f61fb-157">Wykluczenia są reprezentowane przez właściwość `$(DefaultItemExcludes)`.</span><span class="sxs-lookup"><span data-stu-id="f61fb-157">Excludes are represented by the property `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="f61fb-158">Jeśli jawnie zdefiniujesz te elementy w pliku projektu, może wystąpić następujący błąd:</span><span class="sxs-lookup"><span data-stu-id="f61fb-158">If you explicitly define these items in your project file, you're likely to get the following error:</span></span>

<span data-ttu-id="f61fb-159">**Uwzględniono zduplikowane elementy kompilacji. Zestaw SDK platformy .NET domyślnie zawiera elementy kompilacji z katalogu projektu. Możesz usunąć te elementy z pliku projektu lub ustawić właściwość "EnableDefaultCompileItems" na wartość "false", jeśli chcesz jawnie uwzględnić je w pliku projektu.**</span><span class="sxs-lookup"><span data-stu-id="f61fb-159">**Duplicate Compile items were included. The .NET SDK includes Compile items from your project directory by default. You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.**</span></span>

<span data-ttu-id="f61fb-160">Aby rozwiązać ten problem, Usuń jawne `Compile` elementy, które pasują do niejawnych wymienionych w poprzedniej tabeli, lub ustaw właściwość `EnableDefaultCompileItems` na `false`, która wyłącza niejawne dołączanie:</span><span class="sxs-lookup"><span data-stu-id="f61fb-160">To resolve the error, either remove the explicit `Compile` items that match the implicit ones listed on the previous table, or set the `EnableDefaultCompileItems` property to `false`, which disables implicit inclusion:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="f61fb-161">Jeśli chcesz określić, na przykład niektóre pliki do opublikowania w aplikacji, nadal możesz używać znanych mechanizmów programu MSBuild dla tego, na przykład, elementu `Content`.</span><span class="sxs-lookup"><span data-stu-id="f61fb-161">If you want to specify, for example, some files to get published with your app, you can still use the known MSBuild mechanisms for that, for example, the `Content` element.</span></span>

<span data-ttu-id="f61fb-162">`EnableDefaultCompileItems` wyłącza tylko `Compile` elementy globalne, ale nie wpływa na inne elementy globalne, takie jak niejawne `None` globalizowania, które również dotyczą elementów \*. cs.</span><span class="sxs-lookup"><span data-stu-id="f61fb-162">`EnableDefaultCompileItems` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob that also applies to \*.cs items.</span></span> <span data-ttu-id="f61fb-163">Z tego powodu Eksplorator rozwiązań w programie Visual Studio pokazuje elementy \*. cs jako część projektu, zawarte jako elementy `None`.</span><span class="sxs-lookup"><span data-stu-id="f61fb-163">Because of that, Solution Explorer in Visual Studio shows \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="f61fb-164">Aby wyłączyć niejawną `None` globalizowania, ustaw `EnableDefaultNoneItems` na `false`:</span><span class="sxs-lookup"><span data-stu-id="f61fb-164">To disable the implicit `None` glob, set `EnableDefaultNoneItems` to `false`:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="f61fb-165">Aby wyłączyć *wszystkie* niejawne elementy globalne, ustaw właściwość `EnableDefaultItems` na `false`:</span><span class="sxs-lookup"><span data-stu-id="f61fb-165">To disable *all* implicit globs, set the `EnableDefaultItems` property to `false`:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="customize-the-build"></a><span data-ttu-id="f61fb-166">Dostosuj kompilację</span><span class="sxs-lookup"><span data-stu-id="f61fb-166">Customize the build</span></span>

<span data-ttu-id="f61fb-167">Istnieją różne sposoby [dostosowywania kompilacji](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="f61fb-167">There are various ways to [customize a build](/visualstudio/msbuild/customize-your-build).</span></span> <span data-ttu-id="f61fb-168">Możesz chcieć przesłonić Właściwość przez przekazanie jej jako argumentu do polecenia [MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) lub [dotnet](../tools/index.md) .</span><span class="sxs-lookup"><span data-stu-id="f61fb-168">You may want to override a property by passing it as an argument to an [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) or [dotnet](../tools/index.md) command.</span></span> <span data-ttu-id="f61fb-169">Możesz również dodać właściwość do pliku projektu lub do pliku *Directory. Build. props* .</span><span class="sxs-lookup"><span data-stu-id="f61fb-169">You can also add the property to the project file or to a *Directory.Build.props* file.</span></span> <span data-ttu-id="f61fb-170">Aby uzyskać listę przydatnych właściwości projektów .NET Core, zobacz [Właściwości programu MSBuild dla projektów zestaw .NET Core SDK](msbuild-props.md).</span><span class="sxs-lookup"><span data-stu-id="f61fb-170">For a list of useful properties for .NET Core projects, see [MSBuild properties for .NET Core SDK projects](msbuild-props.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f61fb-171">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f61fb-171">See also</span></span>

- [<span data-ttu-id="f61fb-172">Zainstaluj program .NET Core</span><span class="sxs-lookup"><span data-stu-id="f61fb-172">Install .NET Core</span></span>](../install/index.md)
- [<span data-ttu-id="f61fb-173">Jak używać zestawów SDK projektu MSBuild</span><span class="sxs-lookup"><span data-stu-id="f61fb-173">How to use MSBuild project SDKs</span></span>](/visualstudio/msbuild/how-to-use-project-sdk)
