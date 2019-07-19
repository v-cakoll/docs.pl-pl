---
title: polecenie dotnet publish
description: Dotnet publish polecenie publikuje projekt platformy .NET Core w katalogu.
ms.date: 05/29/2018
ms.openlocfilehash: 8cefeae17e464e14abc54dce1feb414a72c44164
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331033"
---
# <a name="dotnet-publish"></a><span data-ttu-id="35d91-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="35d91-103">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="35d91-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="35d91-104">Name</span></span>

<span data-ttu-id="35d91-105">`dotnet publish`-Pakuje aplikację i jej zależności do folderu w celu wdrożenia w systemie hostingu.</span><span class="sxs-lookup"><span data-stu-id="35d91-105">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="35d91-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="35d91-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="35d91-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="35d91-107">.NET Core 2.1</span></span>](#tab/netcore21)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="35d91-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="35d91-108">.NET Core 2.0</span></span>](#tab/netcore20)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="35d91-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="35d91-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="35d91-110">Opis</span><span class="sxs-lookup"><span data-stu-id="35d91-110">Description</span></span>

<span data-ttu-id="35d91-111">`dotnet publish`kompiluje aplikację, odczytuje ją z zależności określonych w pliku projektu i publikuje zestaw plików w katalogu.</span><span class="sxs-lookup"><span data-stu-id="35d91-111">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="35d91-112">Dane wyjściowe obejmują następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="35d91-112">The output includes the following assets:</span></span>

* <span data-ttu-id="35d91-113">Kod języka pośredniego (IL) w zestawie z rozszerzeniem *dll* .</span><span class="sxs-lookup"><span data-stu-id="35d91-113">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
* <span data-ttu-id="35d91-114">plik *. deps. JSON* zawiera wszystkie zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="35d91-114">*.deps.json* file that includes all of the dependencies of the project.</span></span>
* <span data-ttu-id="35d91-115">plik *. runtimeconfig. JSON* określa współużytkowany środowisko uruchomieniowe oczekiwane przez aplikację, a także inne opcje konfiguracji środowiska uruchomieniowego (na przykład typ wyrzucania elementów bezużytecznych).</span><span class="sxs-lookup"><span data-stu-id="35d91-115">*.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
* <span data-ttu-id="35d91-116">Zależności aplikacji, które są kopiowane z pamięci podręcznej NuGet do folderu danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="35d91-116">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="35d91-117">Dane `dotnet publish` wyjściowe polecenia są gotowe do wdrożenia w systemie hostingu (na przykład na serwerze, komputerze, Mac, laptopie) do wykonania.</span><span class="sxs-lookup"><span data-stu-id="35d91-117">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="35d91-118">Jest to jedyna oficjalnie obsługiwana metoda przygotowania aplikacji do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="35d91-118">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="35d91-119">W zależności od typu wdrożenia, który jest określany przez projekt, system hostingu może lub nie ma zainstalowanego udostępnionego środowiska uruchomieniowego platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="35d91-119">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="35d91-120">Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="35d91-120">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="35d91-121">Aby uzyskać strukturę katalogów opublikowanej aplikacji, zobacz [Struktura katalogów](/aspnet/core/hosting/directory-structure).</span><span class="sxs-lookup"><span data-stu-id="35d91-121">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="35d91-122">Argumenty</span><span class="sxs-lookup"><span data-stu-id="35d91-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="35d91-123">Projekt do opublikowania.</span><span class="sxs-lookup"><span data-stu-id="35d91-123">The project to publish.</span></span> <span data-ttu-id="35d91-124">Jest to ścieżka i nazwa pliku [C#](csproj.md)projektu, F#, lub Visual Basic, lub ścieżka do katalogu, który zawiera plik projektu C#, F#lub Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="35d91-124">It's either the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="35d91-125">Jeśli nie zostanie określony, domyślnie jest bieżącym katalogiem.</span><span class="sxs-lookup"><span data-stu-id="35d91-125">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="35d91-126">Opcje</span><span class="sxs-lookup"><span data-stu-id="35d91-126">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="35d91-127">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="35d91-127">.NET Core 2.1</span></span>](#tab/netcore21)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="35d91-128">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="35d91-128">Defines the build configuration.</span></span> <span data-ttu-id="35d91-129">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="35d91-129">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="35d91-130">Publikuje aplikację dla określonej [platformy docelowej](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="35d91-130">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="35d91-131">Należy określić platformę docelową w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="35d91-131">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="35d91-132">Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="35d91-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="35d91-133">Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="35d91-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="35d91-134">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="35d91-134">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="35d91-135">Określa jeden lub kilka [docelowych manifestów](../deploying/runtime-store.md) , które mają być używane do przycinania zestawu pakietów opublikowanych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="35d91-135">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="35d91-136">Plik manifestu jest częścią danych wyjściowych [ `dotnet store` polecenia](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="35d91-136">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="35d91-137">Aby określić wiele manifestów, Dodaj `--manifest` opcję dla każdego manifestu.</span><span class="sxs-lookup"><span data-stu-id="35d91-137">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="35d91-138">Ta opcja jest dostępna począwszy od zestawu SDK platformy .NET Core 2,0.</span><span class="sxs-lookup"><span data-stu-id="35d91-138">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-build`

<span data-ttu-id="35d91-139">Nie kompiluje projektu przed opublikowaniem.</span><span class="sxs-lookup"><span data-stu-id="35d91-139">Doesn't build the project before publishing.</span></span> <span data-ttu-id="35d91-140">Również niejawnie ustawia `--no-restore` flagę.</span><span class="sxs-lookup"><span data-stu-id="35d91-140">It also implicitly sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="35d91-141">Ignoruje odwołania projektu do projektu i przywraca tylko projekt główny.</span><span class="sxs-lookup"><span data-stu-id="35d91-141">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="35d91-142">Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.</span><span class="sxs-lookup"><span data-stu-id="35d91-142">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="35d91-143">Określa ścieżkę do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="35d91-143">Specifies the path for the output directory.</span></span> <span data-ttu-id="35d91-144">Jeśli nie zostanie określony, domyślna wartość to *./bin/[Configuration]/[Framework]/Publish/* dla wdrożenia zależnego od platformy lub *./bin/[Konfiguracja]/[Framework]/[środowisko uruchomieniowe]/Publish/* do wdrożenia samodzielnego.</span><span class="sxs-lookup"><span data-stu-id="35d91-144">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="35d91-145">Jeśli ścieżka jest względna, wygenerowany katalog wyjściowy jest względem lokalizacji pliku projektu, a nie do bieżącego katalogu roboczego.</span><span class="sxs-lookup"><span data-stu-id="35d91-145">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="35d91-146">Publikuje środowisko uruchomieniowe platformy .NET Core przy użyciu aplikacji, aby nie trzeba było instalować środowiska uruchomieniowego na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="35d91-146">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="35d91-147">Jeśli określono identyfikator środowiska uruchomieniowego, jego wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="35d91-147">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="35d91-148">Aby uzyskać więcej informacji na temat różnych typów wdrożeń, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="35d91-148">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="35d91-149">Publikuje aplikację dla danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="35d91-149">Publishes the application for a given runtime.</span></span> <span data-ttu-id="35d91-150">Jest on używany podczas tworzenia [własnego wdrożenia (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="35d91-150">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="35d91-151">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="35d91-151">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="35d91-152">Wartość domyślna to opublikowanie [wdrożenia zależnego od platformy (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="35d91-152">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="35d91-153">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="35d91-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="35d91-154">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="35d91-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="35d91-155">Definiuje sufiks wersji, aby zastąpić gwiazdkę (`*`) w polu wersja pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="35d91-155">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="35d91-156">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="35d91-156">.NET Core 2.0</span></span>](#tab/netcore20)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="35d91-157">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="35d91-157">Defines the build configuration.</span></span> <span data-ttu-id="35d91-158">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="35d91-158">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="35d91-159">Publikuje aplikację dla określonej [platformy docelowej](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="35d91-159">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="35d91-160">Należy określić platformę docelową w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="35d91-160">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="35d91-161">Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="35d91-161">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="35d91-162">Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="35d91-162">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="35d91-163">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="35d91-163">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="35d91-164">Określa jeden lub kilka [docelowych manifestów](../deploying/runtime-store.md) , które mają być używane do przycinania zestawu pakietów opublikowanych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="35d91-164">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="35d91-165">Plik manifestu jest częścią danych wyjściowych [ `dotnet store` polecenia](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="35d91-165">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="35d91-166">Aby określić wiele manifestów, Dodaj `--manifest` opcję dla każdego manifestu.</span><span class="sxs-lookup"><span data-stu-id="35d91-166">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="35d91-167">Ta opcja jest dostępna począwszy od zestawu SDK platformy .NET Core 2,0.</span><span class="sxs-lookup"><span data-stu-id="35d91-167">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="35d91-168">Ignoruje odwołania projektu do projektu i przywraca tylko projekt główny.</span><span class="sxs-lookup"><span data-stu-id="35d91-168">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="35d91-169">Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.</span><span class="sxs-lookup"><span data-stu-id="35d91-169">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="35d91-170">Określa ścieżkę do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="35d91-170">Specifies the path for the output directory.</span></span> <span data-ttu-id="35d91-171">Jeśli nie zostanie określony, domyślna wartość to *./bin/[Configuration]/[Framework]/Publish/* dla wdrożenia zależnego od platformy lub *./bin/[Konfiguracja]/[Framework]/[środowisko uruchomieniowe]/Publish/* do wdrożenia samodzielnego.</span><span class="sxs-lookup"><span data-stu-id="35d91-171">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="35d91-172">Jeśli ścieżka jest względna, wygenerowany katalog wyjściowy jest względem lokalizacji pliku projektu, a nie do bieżącego katalogu roboczego.</span><span class="sxs-lookup"><span data-stu-id="35d91-172">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="35d91-173">Publikuje środowisko uruchomieniowe platformy .NET Core przy użyciu aplikacji, aby nie trzeba było instalować środowiska uruchomieniowego na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="35d91-173">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="35d91-174">Jeśli określono identyfikator środowiska uruchomieniowego, jego wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="35d91-174">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="35d91-175">Aby uzyskać więcej informacji na temat różnych typów wdrożeń, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="35d91-175">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="35d91-176">Publikuje aplikację dla danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="35d91-176">Publishes the application for a given runtime.</span></span> <span data-ttu-id="35d91-177">Jest on używany podczas tworzenia [własnego wdrożenia (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="35d91-177">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="35d91-178">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="35d91-178">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="35d91-179">Wartość domyślna to opublikowanie [wdrożenia zależnego od platformy (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="35d91-179">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="35d91-180">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="35d91-180">Sets the verbosity level of the command.</span></span> <span data-ttu-id="35d91-181">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="35d91-181">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="35d91-182">Definiuje sufiks wersji, aby zastąpić gwiazdkę (`*`) w polu wersja pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="35d91-182">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="35d91-183">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="35d91-183">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="35d91-184">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="35d91-184">Defines the build configuration.</span></span> <span data-ttu-id="35d91-185">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="35d91-185">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="35d91-186">Publikuje aplikację dla określonej [platformy docelowej](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="35d91-186">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="35d91-187">Należy określić platformę docelową w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="35d91-187">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="35d91-188">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="35d91-188">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="35d91-189">Określa jeden lub kilka [docelowych manifestów](../deploying/runtime-store.md) , które mają być używane do przycinania zestawu pakietów opublikowanych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="35d91-189">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="35d91-190">Plik manifestu jest częścią danych wyjściowych [ `dotnet store` polecenia](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="35d91-190">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="35d91-191">Aby określić wiele manifestów, Dodaj `--manifest` opcję dla każdego manifestu.</span><span class="sxs-lookup"><span data-stu-id="35d91-191">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="35d91-192">Ta opcja jest dostępna począwszy od zestawu SDK platformy .NET Core 2,0.</span><span class="sxs-lookup"><span data-stu-id="35d91-192">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="35d91-193">Określa ścieżkę do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="35d91-193">Specifies the path for the output directory.</span></span> <span data-ttu-id="35d91-194">Jeśli nie zostanie określony, domyślna wartość to *./bin/[Configuration]/[Framework]/Publish/* dla wdrożenia zależnego od platformy lub *./bin/[Konfiguracja]/[Framework]/[środowisko uruchomieniowe]/Publish/* do wdrożenia samodzielnego.</span><span class="sxs-lookup"><span data-stu-id="35d91-194">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="35d91-195">Jeśli ścieżka jest względna, wygenerowany katalog wyjściowy jest względem lokalizacji pliku projektu, a nie do bieżącego katalogu roboczego.</span><span class="sxs-lookup"><span data-stu-id="35d91-195">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="35d91-196">Publikuje aplikację dla danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="35d91-196">Publishes the application for a given runtime.</span></span> <span data-ttu-id="35d91-197">Jest on używany podczas tworzenia [własnego wdrożenia (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="35d91-197">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="35d91-198">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="35d91-198">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="35d91-199">Wartość domyślna to opublikowanie [wdrożenia zależnego od platformy (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="35d91-199">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="35d91-200">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="35d91-200">Sets the verbosity level of the command.</span></span> <span data-ttu-id="35d91-201">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="35d91-201">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="35d91-202">Definiuje sufiks wersji, aby zastąpić gwiazdkę (`*`) w polu wersja pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="35d91-202">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="35d91-203">Przykłady</span><span class="sxs-lookup"><span data-stu-id="35d91-203">Examples</span></span>

<span data-ttu-id="35d91-204">Opublikuj projekt w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="35d91-204">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="35d91-205">Publikowanie aplikacji przy użyciu określonego pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="35d91-205">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`

<span data-ttu-id="35d91-206">Opublikuj projekt w bieżącym katalogu przy użyciu `netcoreapp1.1` struktury:</span><span class="sxs-lookup"><span data-stu-id="35d91-206">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`

<span data-ttu-id="35d91-207">Opublikuj bieżącą aplikację przy użyciu `netcoreapp1.1` struktury i środowiska uruchomieniowego dla `OS X 10.10` (należy wyświetlić listę tego identyfikatora RID w pliku projektu).</span><span class="sxs-lookup"><span data-stu-id="35d91-207">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

<span data-ttu-id="35d91-208">Opublikuj bieżącą aplikację, ale nie przywracaj odwołań z projektu do projektu (P2P), tylko projekt główny podczas operacji przywracania (zestaw .NET Core SDK 2,0 i nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="35d91-208">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet publish --no-dependencies`

## <a name="see-also"></a><span data-ttu-id="35d91-209">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35d91-209">See also</span></span>

- [<span data-ttu-id="35d91-210">Platformy docelowe</span><span class="sxs-lookup"><span data-stu-id="35d91-210">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="35d91-211">Wykaz identyfikatorów środowiska uruchomieniowego (RID)</span><span class="sxs-lookup"><span data-stu-id="35d91-211">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
