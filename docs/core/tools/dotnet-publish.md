---
title: polecenia publikowania DotNet
description: Polecenia publikowania dotnet publikuje projekt .NET Core w katalogu.
ms.date: 05/29/2018
ms.openlocfilehash: 40ce31073ee3f6f94e110f3a4e1eeda0c7b2e48d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559319"
---
# <a name="dotnet-publish"></a><span data-ttu-id="70ec8-103">Publikowanie DotNet</span><span class="sxs-lookup"><span data-stu-id="70ec8-103">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="70ec8-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="70ec8-104">Name</span></span>

<span data-ttu-id="70ec8-105">`dotnet publish` -Pakietów aplikacji oraz jego zależności w folderze w celu wdrożenia systemu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="70ec8-105">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="70ec8-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="70ec8-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="70ec8-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="70ec8-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="70ec8-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="70ec8-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="70ec8-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="70ec8-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="70ec8-110">Opis</span><span class="sxs-lookup"><span data-stu-id="70ec8-110">Description</span></span>

<span data-ttu-id="70ec8-111">`dotnet publish` kompiluje aplikację, czyta za pośrednictwem jego zależności, które określono w pliku projektu i publikuje Wynikowy zestaw plików w katalogu.</span><span class="sxs-lookup"><span data-stu-id="70ec8-111">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="70ec8-112">Dane wyjściowe obejmują następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="70ec8-112">The output includes the following assets:</span></span>

* <span data-ttu-id="70ec8-113">Pośredni Language (IL) kod w zestawie przy użyciu *dll* rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="70ec8-113">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
* <span data-ttu-id="70ec8-114">*. deps.json* pliku, który zawiera wszystkie zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="70ec8-114">*.deps.json* file that includes all of the dependencies of the project.</span></span>
* <span data-ttu-id="70ec8-115">*. runtime.config.json* pliku, który określa udostępnionego środowiska uruchomieniowego, która oczekuje aplikacji, a także inne opcje konfiguracji środowiska uruchomieniowego (na przykład typ kolekcji wyrzucania elementów).</span><span class="sxs-lookup"><span data-stu-id="70ec8-115">*.runtime.config.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
* <span data-ttu-id="70ec8-116">Zależności aplikacji, które są kopiowane z pamięcią podręczną programu NuGet do folderu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="70ec8-116">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="70ec8-117">`dotnet publish` Danych wyjściowych polecenia jest gotowa do wdrożenia systemu macierzystego (na przykład na serwerze, PC, Mac, laptop) do wykonania.</span><span class="sxs-lookup"><span data-stu-id="70ec8-117">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="70ec8-118">Jest oficjalnie obsługiwana jedynie do przygotowania aplikacji do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="70ec8-118">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="70ec8-119">W zależności od typu wdrożenia, który określa projektu systemu macierzystego może być lub może nie mieć platformy .NET Core udostępnionego środowiska uruchomieniowego na nim zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="70ec8-119">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="70ec8-120">Aby uzyskać więcej informacji, zobacz [wdrożenie aplikacji programu .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="70ec8-120">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="70ec8-121">Struktura katalogów opublikowanej aplikacji, można zobaczyć [strukturę katalogów](/aspnet/core/hosting/directory-structure).</span><span class="sxs-lookup"><span data-stu-id="70ec8-121">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="70ec8-122">Argumenty</span><span class="sxs-lookup"><span data-stu-id="70ec8-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="70ec8-123">Projekt do opublikowania.</span><span class="sxs-lookup"><span data-stu-id="70ec8-123">The project to publish.</span></span> <span data-ttu-id="70ec8-124">Ścieżka i nazwa pliku jest [ C# ](csproj.md), F#, lub plik projektu języka Visual Basic lub ścieżkę do katalogu, który zawiera C#, F#, lub plik projektu języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="70ec8-124">It's either the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="70ec8-125">Jeśli nie zostanie określony, jego wartość domyślna w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="70ec8-125">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="70ec8-126">Opcje</span><span class="sxs-lookup"><span data-stu-id="70ec8-126">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="70ec8-127">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="70ec8-127">.NET Core 2.1</span></span>](#tab/netcore21)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="70ec8-128">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="70ec8-128">Defines the build configuration.</span></span> <span data-ttu-id="70ec8-129">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="70ec8-129">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="70ec8-130">Publikuje aplikację w określonym [platformę docelową](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="70ec8-130">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="70ec8-131">W pliku projektu, należy określić platformę docelową.</span><span class="sxs-lookup"><span data-stu-id="70ec8-131">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="70ec8-132">Wymusza wszystkie zależności rozwiązany, nawet wtedy, gdy ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="70ec8-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="70ec8-133">Określanie ta flaga jest taka sama jak usuwanie *project.assets.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="70ec8-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="70ec8-134">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="70ec8-134">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="70ec8-135">Określa jeden lub kilka [docelowe manifesty](../deploying/runtime-store.md) na potrzeby trim zbiór pakiety opublikowane przy użyciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70ec8-135">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="70ec8-136">Plik manifestu jest częścią danych wyjściowych [ `dotnet store` polecenia](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="70ec8-136">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="70ec8-137">Aby określić wiele manifestów, Dodaj `--manifest` opcji dla każdego manifestu.</span><span class="sxs-lookup"><span data-stu-id="70ec8-137">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="70ec8-138">Ta opcja jest dostępna, począwszy od programu .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="70ec8-138">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-build`

<span data-ttu-id="70ec8-139">Nie da się skompilować projektu przed opublikowaniem.</span><span class="sxs-lookup"><span data-stu-id="70ec8-139">Doesn't build the project before publishing.</span></span> <span data-ttu-id="70ec8-140">Ustawia również niejawnie `--no-restore` flagi.</span><span class="sxs-lookup"><span data-stu-id="70ec8-140">It also implicitly sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="70ec8-141">Ignoruje odwołania projekt projekt i przywraca jedynie projektu głównego.</span><span class="sxs-lookup"><span data-stu-id="70ec8-141">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="70ec8-142">Przy uruchamianiu polecenia niejawne przywracania nie jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="70ec8-142">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="70ec8-143">Określa ścieżkę do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="70ec8-143">Specifies the path for the output directory.</span></span> <span data-ttu-id="70ec8-144">Jeśli nie zostanie określony, jego wartość domyślna to *./bin/[configuration]/[framework]/publish/* wdrożenia zależny od struktury lub *./bin/[configuration]/[framework]/[runtime]/publish/* dla niezależne wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="70ec8-144">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="70ec8-145">Jeśli ścieżka jest względna, katalog wyjściowy, generowany jest względem lokalizacji pliku projektu, aby bieżący katalog roboczy nie.</span><span class="sxs-lookup"><span data-stu-id="70ec8-145">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="70ec8-146">Publikuje środowisko uruchomieniowe platformy .NET Core za pomocą aplikacji, dzięki czemu środowisko uruchomieniowe nie muszą być zainstalowane na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="70ec8-146">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="70ec8-147">Jeśli określono identyfikator środowiska uruchomieniowego, jego wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="70ec8-147">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="70ec8-148">Aby uzyskać więcej informacji na temat różne typy wdrożenia, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="70ec8-148">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="70ec8-149">Publikuje aplikację dla danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="70ec8-149">Publishes the application for a given runtime.</span></span> <span data-ttu-id="70ec8-150">To jest używany podczas tworzenia [niezależna wdrożenia (— SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="70ec8-150">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="70ec8-151">Aby uzyskać listę identyfikatorów środowisk uruchomieniowych (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="70ec8-151">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="70ec8-152">Domyślnie nie jest publikowanie [zależny od struktury wdrożenia (stacje)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="70ec8-152">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="70ec8-153">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="70ec8-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="70ec8-154">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="70ec8-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="70ec8-155">Określa sufiks wersji zastąpić gwiazdka (`*`) w polu wersja pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="70ec8-155">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="70ec8-156">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="70ec8-156">.NET Core 2.0</span></span>](#tab/netcore20)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="70ec8-157">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="70ec8-157">Defines the build configuration.</span></span> <span data-ttu-id="70ec8-158">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="70ec8-158">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="70ec8-159">Publikuje aplikację w określonym [platformę docelową](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="70ec8-159">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="70ec8-160">W pliku projektu, należy określić platformę docelową.</span><span class="sxs-lookup"><span data-stu-id="70ec8-160">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="70ec8-161">Wymusza wszystkie zależności rozwiązany, nawet wtedy, gdy ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="70ec8-161">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="70ec8-162">Określanie ta flaga jest taka sama jak usuwanie *project.assets.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="70ec8-162">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="70ec8-163">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="70ec8-163">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="70ec8-164">Określa jeden lub kilka [docelowe manifesty](../deploying/runtime-store.md) na potrzeby trim zbiór pakiety opublikowane przy użyciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70ec8-164">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="70ec8-165">Plik manifestu jest częścią danych wyjściowych [ `dotnet store` polecenia](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="70ec8-165">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="70ec8-166">Aby określić wiele manifestów, Dodaj `--manifest` opcji dla każdego manifestu.</span><span class="sxs-lookup"><span data-stu-id="70ec8-166">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="70ec8-167">Ta opcja jest dostępna, począwszy od programu .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="70ec8-167">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="70ec8-168">Ignoruje odwołania projekt projekt i przywraca jedynie projektu głównego.</span><span class="sxs-lookup"><span data-stu-id="70ec8-168">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="70ec8-169">Przy uruchamianiu polecenia niejawne przywracania nie jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="70ec8-169">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="70ec8-170">Określa ścieżkę do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="70ec8-170">Specifies the path for the output directory.</span></span> <span data-ttu-id="70ec8-171">Jeśli nie zostanie określony, jego wartość domyślna to *./bin/[configuration]/[framework]/publish/* wdrożenia zależny od struktury lub *./bin/[configuration]/[framework]/[runtime]/publish/* dla niezależne wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="70ec8-171">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="70ec8-172">Jeśli ścieżka jest względna, katalog wyjściowy, generowany jest względem lokalizacji pliku projektu, aby bieżący katalog roboczy nie.</span><span class="sxs-lookup"><span data-stu-id="70ec8-172">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="70ec8-173">Publikuje środowisko uruchomieniowe platformy .NET Core za pomocą aplikacji, dzięki czemu środowisko uruchomieniowe nie muszą być zainstalowane na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="70ec8-173">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="70ec8-174">Jeśli określono identyfikator środowiska uruchomieniowego, jego wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="70ec8-174">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="70ec8-175">Aby uzyskać więcej informacji na temat różne typy wdrożenia, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="70ec8-175">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="70ec8-176">Publikuje aplikację dla danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="70ec8-176">Publishes the application for a given runtime.</span></span> <span data-ttu-id="70ec8-177">To jest używany podczas tworzenia [niezależna wdrożenia (— SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="70ec8-177">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="70ec8-178">Aby uzyskać listę identyfikatorów środowisk uruchomieniowych (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="70ec8-178">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="70ec8-179">Domyślnie nie jest publikowanie [zależny od struktury wdrożenia (stacje)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="70ec8-179">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="70ec8-180">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="70ec8-180">Sets the verbosity level of the command.</span></span> <span data-ttu-id="70ec8-181">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="70ec8-181">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="70ec8-182">Określa sufiks wersji zastąpić gwiazdka (`*`) w polu wersja pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="70ec8-182">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="70ec8-183">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="70ec8-183">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="70ec8-184">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="70ec8-184">Defines the build configuration.</span></span> <span data-ttu-id="70ec8-185">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="70ec8-185">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="70ec8-186">Publikuje aplikację w określonym [platformę docelową](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="70ec8-186">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="70ec8-187">W pliku projektu, należy określić platformę docelową.</span><span class="sxs-lookup"><span data-stu-id="70ec8-187">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="70ec8-188">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="70ec8-188">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="70ec8-189">Określa jeden lub kilka [docelowe manifesty](../deploying/runtime-store.md) na potrzeby trim zbiór pakiety opublikowane przy użyciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70ec8-189">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="70ec8-190">Plik manifestu jest częścią danych wyjściowych [ `dotnet store` polecenia](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="70ec8-190">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="70ec8-191">Aby określić wiele manifestów, Dodaj `--manifest` opcji dla każdego manifestu.</span><span class="sxs-lookup"><span data-stu-id="70ec8-191">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="70ec8-192">Ta opcja jest dostępna, począwszy od programu .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="70ec8-192">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="70ec8-193">Określa ścieżkę do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="70ec8-193">Specifies the path for the output directory.</span></span> <span data-ttu-id="70ec8-194">Jeśli nie zostanie określony, jego wartość domyślna to *./bin/[configuration]/[framework]/publish/* wdrożenia zależny od struktury lub *./bin/[configuration]/[framework]/[runtime]/publish/* dla niezależne wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="70ec8-194">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="70ec8-195">Jeśli ścieżka jest względna, katalog wyjściowy, generowany jest względem lokalizacji pliku projektu, aby bieżący katalog roboczy nie.</span><span class="sxs-lookup"><span data-stu-id="70ec8-195">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="70ec8-196">Publikuje aplikację dla danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="70ec8-196">Publishes the application for a given runtime.</span></span> <span data-ttu-id="70ec8-197">To jest używany podczas tworzenia [niezależna wdrożenia (— SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="70ec8-197">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="70ec8-198">Aby uzyskać listę identyfikatorów środowisk uruchomieniowych (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="70ec8-198">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="70ec8-199">Domyślnie nie jest publikowanie [zależny od struktury wdrożenia (stacje)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="70ec8-199">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="70ec8-200">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="70ec8-200">Sets the verbosity level of the command.</span></span> <span data-ttu-id="70ec8-201">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="70ec8-201">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="70ec8-202">Określa sufiks wersji zastąpić gwiazdka (`*`) w polu wersja pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="70ec8-202">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="70ec8-203">Przykłady</span><span class="sxs-lookup"><span data-stu-id="70ec8-203">Examples</span></span>

<span data-ttu-id="70ec8-204">Opublikuj projekt w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="70ec8-204">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="70ec8-205">Publikowanie aplikacji przy użyciu pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="70ec8-205">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`

<span data-ttu-id="70ec8-206">Opublikuj projekt w bieżącym katalogu przy użyciu `netcoreapp1.1` framework:</span><span class="sxs-lookup"><span data-stu-id="70ec8-206">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`

<span data-ttu-id="70ec8-207">Publikowanie bieżącej aplikacji przy użyciu `netcoreapp1.1` struktura i środowisko uruchomieniowe dla `OS X 10.10` (musi zawierać ten identyfikatorów RID w pliku projektu).</span><span class="sxs-lookup"><span data-stu-id="70ec8-207">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

<span data-ttu-id="70ec8-208">Publikowanie bieżącej aplikacji, ale nie zostaną przywrócone do projektu (P2P) odwołań, po prostu projekt główny podczas operacji przywracania (.NET Core SDK 2.0 i nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="70ec8-208">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet publish --no-dependencies`

## <a name="see-also"></a><span data-ttu-id="70ec8-209">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70ec8-209">See also</span></span>

- [<span data-ttu-id="70ec8-210">Platformy docelowe</span><span class="sxs-lookup"><span data-stu-id="70ec8-210">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="70ec8-211">Katalog identyfikatora środowiska uruchomieniowego (RID)</span><span class="sxs-lookup"><span data-stu-id="70ec8-211">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
