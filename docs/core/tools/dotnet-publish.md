---
title: polecenia — interfejs wiersza polecenia platformy .NET Core publikowania DotNet
description: Polecenia publikowania dotnet publikuje projekt .NET Core w katalogu.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: a60777d613573076f41fba3e5ed610b236884063
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43511427"
---
# <a name="dotnet-publish"></a><span data-ttu-id="d7580-103">Publikowanie DotNet</span><span class="sxs-lookup"><span data-stu-id="d7580-103">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="d7580-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="d7580-104">Name</span></span>

<span data-ttu-id="d7580-105">`dotnet publish` -Pakietów aplikacji oraz jego zależności w folderze w celu wdrożenia systemu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="d7580-105">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d7580-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="d7580-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="d7580-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="d7580-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="d7580-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="d7580-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d7580-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d7580-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="d7580-110">Opis</span><span class="sxs-lookup"><span data-stu-id="d7580-110">Description</span></span>

<span data-ttu-id="d7580-111">`dotnet publish` kompiluje aplikację, czyta za pośrednictwem jego zależności, które określono w pliku projektu i publikuje Wynikowy zestaw plików w katalogu.</span><span class="sxs-lookup"><span data-stu-id="d7580-111">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="d7580-112">Dane wyjściowe obejmują następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="d7580-112">The output includes the following assets:</span></span>

* <span data-ttu-id="d7580-113">Pośredni Language (IL) kod w zestawie przy użyciu *dll* rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="d7580-113">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
* <span data-ttu-id="d7580-114">*. deps.json* pliku, który zawiera wszystkie zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="d7580-114">*.deps.json* file that includes all of the dependencies of the project.</span></span>
* <span data-ttu-id="d7580-115">*. runtime.config.json* pliku, który określa udostępnionego środowiska uruchomieniowego, która oczekuje aplikacji, a także inne opcje konfiguracji środowiska uruchomieniowego (na przykład typ kolekcji wyrzucania elementów).</span><span class="sxs-lookup"><span data-stu-id="d7580-115">*.runtime.config.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
* <span data-ttu-id="d7580-116">Zależności aplikacji, które są kopiowane z pamięcią podręczną programu NuGet do folderu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="d7580-116">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="d7580-117">`dotnet publish` Danych wyjściowych polecenia jest gotowa do wdrożenia systemu macierzystego (na przykład na serwerze, PC, Mac, laptop) do wykonania.</span><span class="sxs-lookup"><span data-stu-id="d7580-117">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="d7580-118">Jest oficjalnie obsługiwana jedynie do przygotowania aplikacji do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="d7580-118">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="d7580-119">W zależności od typu wdrożenia, który określa projektu systemu macierzystego może być lub może nie mieć platformy .NET Core udostępnionego środowiska uruchomieniowego na nim zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="d7580-119">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="d7580-120">Aby uzyskać więcej informacji, zobacz [wdrożenie aplikacji programu .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="d7580-120">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="d7580-121">Struktura katalogów opublikowanej aplikacji, można zobaczyć [strukturę katalogów](/aspnet/core/hosting/directory-structure).</span><span class="sxs-lookup"><span data-stu-id="d7580-121">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="d7580-122">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d7580-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="d7580-123">Projekt do opublikowania.</span><span class="sxs-lookup"><span data-stu-id="d7580-123">The project to publish.</span></span> <span data-ttu-id="d7580-124">Jeśli nie zostanie określony, jego wartość domyślna w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d7580-124">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="d7580-125">Opcje</span><span class="sxs-lookup"><span data-stu-id="d7580-125">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="d7580-126">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="d7580-126">.NET Core 2.1</span></span>](#tab/netcore21)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="d7580-127">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="d7580-127">Defines the build configuration.</span></span> <span data-ttu-id="d7580-128">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="d7580-128">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="d7580-129">Publikuje aplikację w określonym [platformę docelową](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="d7580-129">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="d7580-130">W pliku projektu, należy określić platformę docelową.</span><span class="sxs-lookup"><span data-stu-id="d7580-130">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="d7580-131">Wymusza wszystkie zależności rozwiązany, nawet wtedy, gdy ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d7580-131">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="d7580-132">Określanie ta flaga jest taka sama jak usuwanie *project.assets.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="d7580-132">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="d7580-133">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="d7580-133">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="d7580-134">Określa jeden lub kilka [docelowe manifesty](../deploying/runtime-store.md) na potrzeby trim zbiór pakiety opublikowane przy użyciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d7580-134">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="d7580-135">Plik manifestu jest częścią danych wyjściowych [ `dotnet store` polecenia](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="d7580-135">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="d7580-136">Aby określić wiele manifestów, Dodaj `--manifest` opcji dla każdego manifestu.</span><span class="sxs-lookup"><span data-stu-id="d7580-136">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="d7580-137">Ta opcja jest dostępna, począwszy od programu .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="d7580-137">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-build`

<span data-ttu-id="d7580-138">Nie da się skompilować projektu przed opublikowaniem.</span><span class="sxs-lookup"><span data-stu-id="d7580-138">Doesn't build the project before publishing.</span></span> <span data-ttu-id="d7580-139">Ustawia również niejawnie `--no-restore` flagi.</span><span class="sxs-lookup"><span data-stu-id="d7580-139">It also implicitly sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="d7580-140">Ignoruje odwołania projekt projekt i przywraca jedynie projektu głównego.</span><span class="sxs-lookup"><span data-stu-id="d7580-140">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="d7580-141">Przy uruchamianiu polecenia niejawne przywracania nie jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="d7580-141">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="d7580-142">Określa ścieżkę do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="d7580-142">Specifies the path for the output directory.</span></span> <span data-ttu-id="d7580-143">Jeśli nie zostanie określony, jego wartość domyślna to *./bin/[configuration]/[framework]/publish/* wdrożenia zależny od struktury lub *./bin/[configuration]/[framework]/[runtime]/publish/* dla niezależne wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="d7580-143">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="d7580-144">Jeśli ścieżka jest względna, katalog wyjściowy, generowany jest względem lokalizacji pliku projektu, aby bieżący katalog roboczy nie.</span><span class="sxs-lookup"><span data-stu-id="d7580-144">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="d7580-145">Publikuje środowisko uruchomieniowe platformy .NET Core za pomocą aplikacji, dzięki czemu środowisko uruchomieniowe nie muszą być zainstalowane na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="d7580-145">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="d7580-146">Jeśli określono identyfikator środowiska uruchomieniowego, jego wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="d7580-146">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="d7580-147">Aby uzyskać więcej informacji na temat różne typy wdrożenia, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="d7580-147">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="d7580-148">Publikuje aplikację dla danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="d7580-148">Publishes the application for a given runtime.</span></span> <span data-ttu-id="d7580-149">To jest używany podczas tworzenia [niezależna wdrożenia (— SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="d7580-149">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="d7580-150">Aby uzyskać listę identyfikatorów środowisk uruchomieniowych (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="d7580-150">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="d7580-151">Domyślnie nie jest publikowanie [zależny od struktury wdrożenia (stacje)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="d7580-151">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d7580-152">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="d7580-152">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d7580-153">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d7580-153">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="d7580-154">Określa sufiks wersji zastąpić gwiazdka (`*`) w polu wersja pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="d7580-154">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="d7580-155">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="d7580-155">.NET Core 2.0</span></span>](#tab/netcore20)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="d7580-156">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="d7580-156">Defines the build configuration.</span></span> <span data-ttu-id="d7580-157">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="d7580-157">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="d7580-158">Publikuje aplikację w określonym [platformę docelową](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="d7580-158">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="d7580-159">W pliku projektu, należy określić platformę docelową.</span><span class="sxs-lookup"><span data-stu-id="d7580-159">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="d7580-160">Wymusza wszystkie zależności rozwiązany, nawet wtedy, gdy ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d7580-160">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="d7580-161">Określanie ta flaga jest taka sama jak usuwanie *project.assets.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="d7580-161">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="d7580-162">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="d7580-162">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="d7580-163">Określa jeden lub kilka [docelowe manifesty](../deploying/runtime-store.md) na potrzeby trim zbiór pakiety opublikowane przy użyciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d7580-163">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="d7580-164">Plik manifestu jest częścią danych wyjściowych [ `dotnet store` polecenia](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="d7580-164">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="d7580-165">Aby określić wiele manifestów, Dodaj `--manifest` opcji dla każdego manifestu.</span><span class="sxs-lookup"><span data-stu-id="d7580-165">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="d7580-166">Ta opcja jest dostępna, począwszy od programu .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="d7580-166">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="d7580-167">Ignoruje odwołania projekt projekt i przywraca jedynie projektu głównego.</span><span class="sxs-lookup"><span data-stu-id="d7580-167">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="d7580-168">Przy uruchamianiu polecenia niejawne przywracania nie jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="d7580-168">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="d7580-169">Określa ścieżkę do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="d7580-169">Specifies the path for the output directory.</span></span> <span data-ttu-id="d7580-170">Jeśli nie zostanie określony, jego wartość domyślna to *./bin/[configuration]/[framework]/publish/* wdrożenia zależny od struktury lub *./bin/[configuration]/[framework]/[runtime]/publish/* dla niezależne wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="d7580-170">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="d7580-171">Jeśli ścieżka jest względna, katalog wyjściowy, generowany jest względem lokalizacji pliku projektu, aby bieżący katalog roboczy nie.</span><span class="sxs-lookup"><span data-stu-id="d7580-171">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="d7580-172">Publikuje środowisko uruchomieniowe platformy .NET Core za pomocą aplikacji, dzięki czemu środowisko uruchomieniowe nie muszą być zainstalowane na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="d7580-172">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="d7580-173">Jeśli określono identyfikator środowiska uruchomieniowego, jego wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="d7580-173">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="d7580-174">Aby uzyskać więcej informacji na temat różne typy wdrożenia, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="d7580-174">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="d7580-175">Publikuje aplikację dla danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="d7580-175">Publishes the application for a given runtime.</span></span> <span data-ttu-id="d7580-176">To jest używany podczas tworzenia [niezależna wdrożenia (— SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="d7580-176">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="d7580-177">Aby uzyskać listę identyfikatorów środowisk uruchomieniowych (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="d7580-177">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="d7580-178">Domyślnie nie jest publikowanie [zależny od struktury wdrożenia (stacje)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="d7580-178">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d7580-179">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="d7580-179">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d7580-180">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d7580-180">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="d7580-181">Określa sufiks wersji zastąpić gwiazdka (`*`) w polu wersja pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="d7580-181">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d7580-182">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d7580-182">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="d7580-183">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="d7580-183">Defines the build configuration.</span></span> <span data-ttu-id="d7580-184">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="d7580-184">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="d7580-185">Publikuje aplikację w określonym [platformę docelową](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="d7580-185">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="d7580-186">W pliku projektu, należy określić platformę docelową.</span><span class="sxs-lookup"><span data-stu-id="d7580-186">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="d7580-187">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="d7580-187">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="d7580-188">Określa jeden lub kilka [docelowe manifesty](../deploying/runtime-store.md) na potrzeby trim zbiór pakiety opublikowane przy użyciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d7580-188">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="d7580-189">Plik manifestu jest częścią danych wyjściowych [ `dotnet store` polecenia](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="d7580-189">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="d7580-190">Aby określić wiele manifestów, Dodaj `--manifest` opcji dla każdego manifestu.</span><span class="sxs-lookup"><span data-stu-id="d7580-190">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="d7580-191">Ta opcja jest dostępna, począwszy od programu .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="d7580-191">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="d7580-192">Określa ścieżkę do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="d7580-192">Specifies the path for the output directory.</span></span> <span data-ttu-id="d7580-193">Jeśli nie zostanie określony, jego wartość domyślna to *./bin/[configuration]/[framework]/publish/* wdrożenia zależny od struktury lub *./bin/[configuration]/[framework]/[runtime]/publish/* dla niezależne wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="d7580-193">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="d7580-194">Jeśli ścieżka jest względna, katalog wyjściowy, generowany jest względem lokalizacji pliku projektu, aby bieżący katalog roboczy nie.</span><span class="sxs-lookup"><span data-stu-id="d7580-194">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="d7580-195">Publikuje aplikację dla danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="d7580-195">Publishes the application for a given runtime.</span></span> <span data-ttu-id="d7580-196">To jest używany podczas tworzenia [niezależna wdrożenia (— SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="d7580-196">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="d7580-197">Aby uzyskać listę identyfikatorów środowisk uruchomieniowych (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="d7580-197">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="d7580-198">Domyślnie nie jest publikowanie [zależny od struktury wdrożenia (stacje)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="d7580-198">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d7580-199">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="d7580-199">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d7580-200">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d7580-200">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="d7580-201">Określa sufiks wersji zastąpić gwiazdka (`*`) w polu wersja pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="d7580-201">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="d7580-202">Przykłady</span><span class="sxs-lookup"><span data-stu-id="d7580-202">Examples</span></span>

<span data-ttu-id="d7580-203">Opublikuj projekt w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="d7580-203">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="d7580-204">Publikowanie aplikacji przy użyciu pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="d7580-204">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`

<span data-ttu-id="d7580-205">Opublikuj projekt w bieżącym katalogu przy użyciu `netcoreapp1.1` framework:</span><span class="sxs-lookup"><span data-stu-id="d7580-205">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`

<span data-ttu-id="d7580-206">Publikowanie bieżącej aplikacji przy użyciu `netcoreapp1.1` struktura i środowisko uruchomieniowe dla `OS X 10.10` (musi zawierać ten identyfikatorów RID w pliku projektu).</span><span class="sxs-lookup"><span data-stu-id="d7580-206">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

<span data-ttu-id="d7580-207">Publikowanie bieżącej aplikacji, ale nie zostaną przywrócone do projektu (P2P) odwołań, po prostu projekt główny podczas operacji przywracania (.NET Core SDK 2.0 i nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="d7580-207">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet publish --no-dependencies`

## <a name="see-also"></a><span data-ttu-id="d7580-208">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d7580-208">See also</span></span>

* [<span data-ttu-id="d7580-209">Platformy docelowe</span><span class="sxs-lookup"><span data-stu-id="d7580-209">Target frameworks</span></span>](../../standard/frameworks.md)
* [<span data-ttu-id="d7580-210">Katalog identyfikatora środowiska uruchomieniowego (RID)</span><span class="sxs-lookup"><span data-stu-id="d7580-210">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
