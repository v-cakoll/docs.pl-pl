---
title: polecenie dotnet publish
description: Dotnet publish polecenie publikuje projekt platformy .NET Core w katalogu.
ms.date: 05/29/2018
ms.openlocfilehash: 88dc53d6c45bc18f630d8a7137704e813ad4f0e3
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626076"
---
# <a name="dotnet-publish"></a><span data-ttu-id="db512-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="db512-103">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="db512-104">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="db512-104">Name</span></span>

<span data-ttu-id="db512-105">`dotnet publish` — pakiety aplikacji i jej zależności w folderze do wdrożenia w systemie hostingu.</span><span class="sxs-lookup"><span data-stu-id="db512-105">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="db512-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="db512-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21"></a>[<span data-ttu-id="db512-107">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="db512-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-20"></a>[<span data-ttu-id="db512-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="db512-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1x"></a>[<span data-ttu-id="db512-109">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="db512-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="db512-110">Opis</span><span class="sxs-lookup"><span data-stu-id="db512-110">Description</span></span>

<span data-ttu-id="db512-111">`dotnet publish` kompiluje aplikację, odczytuje ją z zależności określonych w pliku projektu i publikuje zestaw plików w katalogu.</span><span class="sxs-lookup"><span data-stu-id="db512-111">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="db512-112">Dane wyjściowe obejmują następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="db512-112">The output includes the following assets:</span></span>

- <span data-ttu-id="db512-113">Kod języka pośredniego (IL) w zestawie z rozszerzeniem *dll* .</span><span class="sxs-lookup"><span data-stu-id="db512-113">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="db512-114">plik *. deps. JSON* zawiera wszystkie zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="db512-114">*.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="db512-115">plik *. runtimeconfig. JSON* określa współużytkowany środowisko uruchomieniowe oczekiwane przez aplikację, a także inne opcje konfiguracji środowiska uruchomieniowego (na przykład typ wyrzucania elementów bezużytecznych).</span><span class="sxs-lookup"><span data-stu-id="db512-115">*.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="db512-116">Zależności aplikacji, które są kopiowane z pamięci podręcznej NuGet do folderu danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="db512-116">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="db512-117">Dane wyjściowe polecenia `dotnet publish` są gotowe do wdrożenia w systemie hostingu (na przykład serwer, komputer, Mac, laptop) do wykonania.</span><span class="sxs-lookup"><span data-stu-id="db512-117">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="db512-118">Jest to jedyna oficjalnie obsługiwana metoda przygotowania aplikacji do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="db512-118">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="db512-119">W zależności od typu wdrożenia, który jest określany przez projekt, system hostingu może lub nie ma zainstalowanego udostępnionego środowiska uruchomieniowego platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="db512-119">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="db512-120">Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="db512-120">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="db512-121">Aby uzyskać strukturę katalogów opublikowanej aplikacji, zobacz [Struktura katalogów](/aspnet/core/hosting/directory-structure).</span><span class="sxs-lookup"><span data-stu-id="db512-121">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="db512-122">Argumenty</span><span class="sxs-lookup"><span data-stu-id="db512-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="db512-123">Projekt do opublikowania.</span><span class="sxs-lookup"><span data-stu-id="db512-123">The project to publish.</span></span> <span data-ttu-id="db512-124">Jest to ścieżka i nazwa pliku [C#](csproj.md)projektu, F#, lub Visual Basic, lub ścieżka do katalogu, który zawiera plik projektu C#, F#lub Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="db512-124">It's either the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="db512-125">Jeśli nie zostanie określony, domyślnie jest bieżącym katalogiem.</span><span class="sxs-lookup"><span data-stu-id="db512-125">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="db512-126">Opcje</span><span class="sxs-lookup"><span data-stu-id="db512-126">Options</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="db512-127">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="db512-127">.NET Core 2.1</span></span>](#tab/netcore21)

`-c|--configuration <CONFIGURATION>`

<span data-ttu-id="db512-128">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="db512-128">Defines the build configuration.</span></span> <span data-ttu-id="db512-129">Wartość domyślna dla większości projektów jest `Debug`, ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.</span><span class="sxs-lookup"><span data-stu-id="db512-129">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="db512-130">Publikuje aplikację dla określonej [platformy docelowej](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="db512-130">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="db512-131">Należy określić platformę docelową w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="db512-131">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="db512-132">Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="db512-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="db512-133">Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="db512-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="db512-134">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="db512-134">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="db512-135">Określa jeden lub kilka [docelowych manifestów](../deploying/runtime-store.md) , które mają być używane do przycinania zestawu pakietów opublikowanych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="db512-135">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="db512-136">Plik manifestu jest częścią danych wyjściowych [polecenia`dotnet store`](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="db512-136">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="db512-137">Aby określić wiele manifestów, Dodaj opcję `--manifest` dla każdego manifestu.</span><span class="sxs-lookup"><span data-stu-id="db512-137">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="db512-138">Ta opcja jest dostępna począwszy od zestawu SDK platformy .NET Core 2,0.</span><span class="sxs-lookup"><span data-stu-id="db512-138">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-build`

<span data-ttu-id="db512-139">Nie kompiluje projektu przed opublikowaniem.</span><span class="sxs-lookup"><span data-stu-id="db512-139">Doesn't build the project before publishing.</span></span> <span data-ttu-id="db512-140">Niejawnie ustawia również flagę `--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="db512-140">It also implicitly sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="db512-141">Ignoruje odwołania projektu do projektu i przywraca tylko projekt główny.</span><span class="sxs-lookup"><span data-stu-id="db512-141">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="db512-142">Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.</span><span class="sxs-lookup"><span data-stu-id="db512-142">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="db512-143">Określa ścieżkę do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="db512-143">Specifies the path for the output directory.</span></span> <span data-ttu-id="db512-144">Jeśli nie zostanie określony, domyślna wartość to *./bin/[Configuration]/[Framework]/Publish/* dla wdrożenia zależnego od platformy lub *./bin/[Konfiguracja]/[Framework]/[środowisko uruchomieniowe]/Publish/* do wdrożenia samodzielnego.</span><span class="sxs-lookup"><span data-stu-id="db512-144">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="db512-145">Jeśli ścieżka jest względna, wygenerowany katalog wyjściowy jest względem lokalizacji pliku projektu, a nie do bieżącego katalogu roboczego.</span><span class="sxs-lookup"><span data-stu-id="db512-145">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="db512-146">Publikuje środowisko uruchomieniowe platformy .NET Core przy użyciu aplikacji, aby nie trzeba było instalować środowiska uruchomieniowego na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="db512-146">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="db512-147">Jeśli określono identyfikator środowiska uruchomieniowego, jego wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="db512-147">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="db512-148">Aby uzyskać więcej informacji na temat różnych typów wdrożeń, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="db512-148">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="db512-149">Publikuje aplikację dla danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="db512-149">Publishes the application for a given runtime.</span></span> <span data-ttu-id="db512-150">Jest on używany podczas tworzenia [własnego wdrożenia (SCD)](../deploying/index.md#publish-self-contained).</span><span class="sxs-lookup"><span data-stu-id="db512-150">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#publish-self-contained).</span></span> <span data-ttu-id="db512-151">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="db512-151">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="db512-152">Wartość domyślna to opublikowanie [wdrożenia zależnego od platformy (FDD)](../deploying/index.md#publish-runtime-dependent).</span><span class="sxs-lookup"><span data-stu-id="db512-152">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#publish-runtime-dependent).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="db512-153">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="db512-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="db512-154">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="db512-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="db512-155">Definiuje sufiks wersji, aby zastąpić gwiazdkę (`*`) w polu wersja pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="db512-155">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-20"></a>[<span data-ttu-id="db512-156">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="db512-156">.NET Core 2.0</span></span>](#tab/netcore20)

`-c|--configuration <CONFIGURATION>`

<span data-ttu-id="db512-157">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="db512-157">Defines the build configuration.</span></span> <span data-ttu-id="db512-158">Wartość domyślna dla większości projektów jest `Debug`, ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.</span><span class="sxs-lookup"><span data-stu-id="db512-158">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="db512-159">Publikuje aplikację dla określonej [platformy docelowej](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="db512-159">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="db512-160">Należy określić platformę docelową w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="db512-160">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="db512-161">Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="db512-161">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="db512-162">Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="db512-162">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="db512-163">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="db512-163">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="db512-164">Określa jeden lub kilka [docelowych manifestów](../deploying/runtime-store.md) , które mają być używane do przycinania zestawu pakietów opublikowanych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="db512-164">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="db512-165">Plik manifestu jest częścią danych wyjściowych [polecenia`dotnet store`](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="db512-165">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="db512-166">Aby określić wiele manifestów, Dodaj opcję `--manifest` dla każdego manifestu.</span><span class="sxs-lookup"><span data-stu-id="db512-166">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="db512-167">Ta opcja jest dostępna począwszy od zestawu SDK platformy .NET Core 2,0.</span><span class="sxs-lookup"><span data-stu-id="db512-167">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="db512-168">Ignoruje odwołania projektu do projektu i przywraca tylko projekt główny.</span><span class="sxs-lookup"><span data-stu-id="db512-168">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="db512-169">Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.</span><span class="sxs-lookup"><span data-stu-id="db512-169">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="db512-170">Określa ścieżkę do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="db512-170">Specifies the path for the output directory.</span></span> <span data-ttu-id="db512-171">Jeśli nie zostanie określony, domyślna wartość to *./bin/[Configuration]/[Framework]/Publish/* dla wdrożenia zależnego od platformy lub *./bin/[Konfiguracja]/[Framework]/[środowisko uruchomieniowe]/Publish/* do wdrożenia samodzielnego.</span><span class="sxs-lookup"><span data-stu-id="db512-171">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="db512-172">Jeśli ścieżka jest względna, wygenerowany katalog wyjściowy jest względem lokalizacji pliku projektu, a nie do bieżącego katalogu roboczego.</span><span class="sxs-lookup"><span data-stu-id="db512-172">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="db512-173">Publikuje środowisko uruchomieniowe platformy .NET Core przy użyciu aplikacji, aby nie trzeba było instalować środowiska uruchomieniowego na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="db512-173">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="db512-174">Jeśli określono identyfikator środowiska uruchomieniowego, jego wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="db512-174">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="db512-175">Aby uzyskać więcej informacji na temat różnych typów wdrożeń, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="db512-175">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="db512-176">Publikuje aplikację dla danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="db512-176">Publishes the application for a given runtime.</span></span> <span data-ttu-id="db512-177">Jest on używany podczas tworzenia [własnego wdrożenia (SCD)](../deploying/index.md#publish-self-contained).</span><span class="sxs-lookup"><span data-stu-id="db512-177">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#publish-self-contained).</span></span> <span data-ttu-id="db512-178">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="db512-178">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="db512-179">Wartość domyślna to opublikowanie [wdrożenia zależnego od platformy (FDD)](../deploying/index.md#publish-runtime-dependent).</span><span class="sxs-lookup"><span data-stu-id="db512-179">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#publish-runtime-dependent).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="db512-180">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="db512-180">Sets the verbosity level of the command.</span></span> <span data-ttu-id="db512-181">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="db512-181">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="db512-182">Definiuje sufiks wersji, aby zastąpić gwiazdkę (`*`) w polu wersja pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="db512-182">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1x"></a>[<span data-ttu-id="db512-183">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="db512-183">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration <CONFIGURATION>`

<span data-ttu-id="db512-184">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="db512-184">Defines the build configuration.</span></span> <span data-ttu-id="db512-185">Wartość domyślna dla większości projektów jest `Debug`, ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.</span><span class="sxs-lookup"><span data-stu-id="db512-185">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="db512-186">Publikuje aplikację dla określonej [platformy docelowej](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="db512-186">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="db512-187">Należy określić platformę docelową w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="db512-187">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="db512-188">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="db512-188">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="db512-189">Określa jeden lub kilka [docelowych manifestów](../deploying/runtime-store.md) , które mają być używane do przycinania zestawu pakietów opublikowanych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="db512-189">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="db512-190">Plik manifestu jest częścią danych wyjściowych [polecenia`dotnet store`](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="db512-190">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="db512-191">Aby określić wiele manifestów, Dodaj opcję `--manifest` dla każdego manifestu.</span><span class="sxs-lookup"><span data-stu-id="db512-191">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="db512-192">Ta opcja jest dostępna począwszy od zestawu SDK platformy .NET Core 2,0.</span><span class="sxs-lookup"><span data-stu-id="db512-192">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="db512-193">Określa ścieżkę do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="db512-193">Specifies the path for the output directory.</span></span> <span data-ttu-id="db512-194">Jeśli nie zostanie określony, domyślna wartość to *./bin/[Configuration]/[Framework]/Publish/* dla wdrożenia zależnego od platformy lub *./bin/[Konfiguracja]/[Framework]/[środowisko uruchomieniowe]/Publish/* do wdrożenia samodzielnego.</span><span class="sxs-lookup"><span data-stu-id="db512-194">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="db512-195">Jeśli ścieżka jest względna, wygenerowany katalog wyjściowy jest względem lokalizacji pliku projektu, a nie do bieżącego katalogu roboczego.</span><span class="sxs-lookup"><span data-stu-id="db512-195">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="db512-196">Publikuje aplikację dla danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="db512-196">Publishes the application for a given runtime.</span></span> <span data-ttu-id="db512-197">Jest on używany podczas tworzenia [własnego wdrożenia (SCD)](../deploying/index.md#publish-self-contained).</span><span class="sxs-lookup"><span data-stu-id="db512-197">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#publish-self-contained).</span></span> <span data-ttu-id="db512-198">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="db512-198">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="db512-199">Wartość domyślna to opublikowanie [wdrożenia zależnego od platformy (FDD)](../deploying/index.md#publish-runtime-dependent).</span><span class="sxs-lookup"><span data-stu-id="db512-199">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#publish-runtime-dependent).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="db512-200">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="db512-200">Sets the verbosity level of the command.</span></span> <span data-ttu-id="db512-201">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="db512-201">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="db512-202">Definiuje sufiks wersji, aby zastąpić gwiazdkę (`*`) w polu wersja pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="db512-202">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="db512-203">Przykłady</span><span class="sxs-lookup"><span data-stu-id="db512-203">Examples</span></span>

<span data-ttu-id="db512-204">Opublikuj projekt w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="db512-204">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="db512-205">Publikowanie aplikacji przy użyciu określonego pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="db512-205">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`

<span data-ttu-id="db512-206">Opublikuj projekt w bieżącym katalogu przy użyciu struktury `netcoreapp1.1`:</span><span class="sxs-lookup"><span data-stu-id="db512-206">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`

<span data-ttu-id="db512-207">Opublikuj bieżącą aplikację przy użyciu struktury `netcoreapp1.1` i środowiska uruchomieniowego dla `OS X 10.10` (należy wyświetlić listę tego identyfikatora RID w pliku projektu).</span><span class="sxs-lookup"><span data-stu-id="db512-207">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

<span data-ttu-id="db512-208">Opublikuj bieżącą aplikację, ale nie przywracaj odwołań z projektu do projektu (P2P), tylko projekt główny podczas operacji przywracania (zestaw .NET Core SDK 2,0 i nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="db512-208">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet publish --no-dependencies`

## <a name="see-also"></a><span data-ttu-id="db512-209">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db512-209">See also</span></span>

- [<span data-ttu-id="db512-210">Platformy docelowe</span><span class="sxs-lookup"><span data-stu-id="db512-210">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="db512-211">Wykaz identyfikatorów środowiska uruchomieniowego (RID)</span><span class="sxs-lookup"><span data-stu-id="db512-211">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
