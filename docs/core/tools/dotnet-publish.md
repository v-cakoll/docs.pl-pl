---
title: polecenia publikowania DotNet
description: Polecenia publikowania dotnet publikuje projekt .NET Core w katalogu.
ms.date: 05/29/2018
ms.openlocfilehash: 24490bd0fbfca65692d7025b5ed2aea659c35473
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61648688"
---
# <a name="dotnet-publish"></a><span data-ttu-id="d7ebe-103">Publikowanie DotNet</span><span class="sxs-lookup"><span data-stu-id="d7ebe-103">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="d7ebe-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="d7ebe-104">Name</span></span>

<span data-ttu-id="d7ebe-105">`dotnet publish` -Pakietów aplikacji oraz jego zależności w folderze w celu wdrożenia systemu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-105">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d7ebe-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="d7ebe-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="d7ebe-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="d7ebe-107">.NET Core 2.1</span></span>](#tab/netcore21)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="d7ebe-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="d7ebe-108">.NET Core 2.0</span></span>](#tab/netcore20)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d7ebe-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d7ebe-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="d7ebe-110">Opis</span><span class="sxs-lookup"><span data-stu-id="d7ebe-110">Description</span></span>

<span data-ttu-id="d7ebe-111">`dotnet publish` kompiluje aplikację, czyta za pośrednictwem jego zależności, które określono w pliku projektu i publikuje Wynikowy zestaw plików w katalogu.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-111">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="d7ebe-112">Dane wyjściowe obejmują następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="d7ebe-112">The output includes the following assets:</span></span>

* <span data-ttu-id="d7ebe-113">Pośredni Language (IL) kod w zestawie przy użyciu *dll* rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-113">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
* <span data-ttu-id="d7ebe-114">*. deps.json* pliku, który zawiera wszystkie zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-114">*.deps.json* file that includes all of the dependencies of the project.</span></span>
* <span data-ttu-id="d7ebe-115">*. runtime.config.json* pliku, który określa udostępnionego środowiska uruchomieniowego, która oczekuje aplikacji, a także inne opcje konfiguracji środowiska uruchomieniowego (na przykład typ kolekcji wyrzucania elementów).</span><span class="sxs-lookup"><span data-stu-id="d7ebe-115">*.runtime.config.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
* <span data-ttu-id="d7ebe-116">Zależności aplikacji, które są kopiowane z pamięcią podręczną programu NuGet do folderu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-116">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="d7ebe-117">`dotnet publish` Danych wyjściowych polecenia jest gotowa do wdrożenia systemu macierzystego (na przykład na serwerze, PC, Mac, laptop) do wykonania.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-117">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="d7ebe-118">Jest oficjalnie obsługiwana jedynie do przygotowania aplikacji do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-118">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="d7ebe-119">W zależności od typu wdrożenia, który określa projektu systemu macierzystego może być lub może nie mieć platformy .NET Core udostępnionego środowiska uruchomieniowego na nim zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-119">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="d7ebe-120">Aby uzyskać więcej informacji, zobacz [wdrożenie aplikacji programu .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="d7ebe-120">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="d7ebe-121">Struktura katalogów opublikowanej aplikacji, można zobaczyć [strukturę katalogów](/aspnet/core/hosting/directory-structure).</span><span class="sxs-lookup"><span data-stu-id="d7ebe-121">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="d7ebe-122">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d7ebe-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="d7ebe-123">Projekt do opublikowania.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-123">The project to publish.</span></span> <span data-ttu-id="d7ebe-124">Ścieżka i nazwa pliku jest [ C# ](csproj.md), F#, lub plik projektu języka Visual Basic lub ścieżkę do katalogu, który zawiera C#, F#, lub plik projektu języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-124">It's either the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="d7ebe-125">Jeśli nie zostanie określony, jego wartość domyślna w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-125">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="d7ebe-126">Opcje</span><span class="sxs-lookup"><span data-stu-id="d7ebe-126">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="d7ebe-127">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="d7ebe-127">.NET Core 2.1</span></span>](#tab/netcore21)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="d7ebe-128">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-128">Defines the build configuration.</span></span> <span data-ttu-id="d7ebe-129">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-129">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="d7ebe-130">Publikuje aplikację w określonym [platformę docelową](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="d7ebe-130">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="d7ebe-131">W pliku projektu, należy określić platformę docelową.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-131">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="d7ebe-132">Wymusza wszystkie zależności rozwiązany, nawet wtedy, gdy ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="d7ebe-133">Określanie ta flaga jest taka sama jak usuwanie *project.assets.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="d7ebe-134">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-134">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="d7ebe-135">Określa jeden lub kilka [docelowe manifesty](../deploying/runtime-store.md) na potrzeby trim zbiór pakiety opublikowane przy użyciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-135">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="d7ebe-136">Plik manifestu jest częścią danych wyjściowych [ `dotnet store` polecenia](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="d7ebe-136">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="d7ebe-137">Aby określić wiele manifestów, Dodaj `--manifest` opcji dla każdego manifestu.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-137">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="d7ebe-138">Ta opcja jest dostępna, począwszy od programu .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-138">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-build`

<span data-ttu-id="d7ebe-139">Nie da się skompilować projektu przed opublikowaniem.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-139">Doesn't build the project before publishing.</span></span> <span data-ttu-id="d7ebe-140">Ustawia również niejawnie `--no-restore` flagi.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-140">It also implicitly sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="d7ebe-141">Ignoruje odwołania projekt projekt i przywraca jedynie projektu głównego.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-141">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="d7ebe-142">Przy uruchamianiu polecenia niejawne przywracania nie jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-142">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="d7ebe-143">Określa ścieżkę do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-143">Specifies the path for the output directory.</span></span> <span data-ttu-id="d7ebe-144">Jeśli nie zostanie określony, jego wartość domyślna to *./bin/[configuration]/[framework]/publish/* wdrożenia zależny od struktury lub *./bin/[configuration]/[framework]/[runtime]/publish/* dla niezależne wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-144">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="d7ebe-145">Jeśli ścieżka jest względna, katalog wyjściowy, generowany jest względem lokalizacji pliku projektu, aby bieżący katalog roboczy nie.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-145">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="d7ebe-146">Publikuje środowisko uruchomieniowe platformy .NET Core za pomocą aplikacji, dzięki czemu środowisko uruchomieniowe nie muszą być zainstalowane na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-146">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="d7ebe-147">Jeśli określono identyfikator środowiska uruchomieniowego, jego wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-147">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="d7ebe-148">Aby uzyskać więcej informacji na temat różne typy wdrożenia, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="d7ebe-148">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="d7ebe-149">Publikuje aplikację dla danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-149">Publishes the application for a given runtime.</span></span> <span data-ttu-id="d7ebe-150">To jest używany podczas tworzenia [niezależna wdrożenia (— SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="d7ebe-150">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="d7ebe-151">Aby uzyskać listę identyfikatorów środowisk uruchomieniowych (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="d7ebe-151">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="d7ebe-152">Domyślnie nie jest publikowanie [zależny od struktury wdrożenia (stacje)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="d7ebe-152">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d7ebe-153">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d7ebe-154">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="d7ebe-155">Określa sufiks wersji zastąpić gwiazdka (`*`) w polu wersja pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-155">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="d7ebe-156">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="d7ebe-156">.NET Core 2.0</span></span>](#tab/netcore20)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="d7ebe-157">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-157">Defines the build configuration.</span></span> <span data-ttu-id="d7ebe-158">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-158">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="d7ebe-159">Publikuje aplikację w określonym [platformę docelową](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="d7ebe-159">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="d7ebe-160">W pliku projektu, należy określić platformę docelową.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-160">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="d7ebe-161">Wymusza wszystkie zależności rozwiązany, nawet wtedy, gdy ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-161">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="d7ebe-162">Określanie ta flaga jest taka sama jak usuwanie *project.assets.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-162">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="d7ebe-163">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-163">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="d7ebe-164">Określa jeden lub kilka [docelowe manifesty](../deploying/runtime-store.md) na potrzeby trim zbiór pakiety opublikowane przy użyciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-164">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="d7ebe-165">Plik manifestu jest częścią danych wyjściowych [ `dotnet store` polecenia](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="d7ebe-165">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="d7ebe-166">Aby określić wiele manifestów, Dodaj `--manifest` opcji dla każdego manifestu.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-166">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="d7ebe-167">Ta opcja jest dostępna, począwszy od programu .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-167">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="d7ebe-168">Ignoruje odwołania projekt projekt i przywraca jedynie projektu głównego.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-168">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="d7ebe-169">Przy uruchamianiu polecenia niejawne przywracania nie jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-169">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="d7ebe-170">Określa ścieżkę do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-170">Specifies the path for the output directory.</span></span> <span data-ttu-id="d7ebe-171">Jeśli nie zostanie określony, jego wartość domyślna to *./bin/[configuration]/[framework]/publish/* wdrożenia zależny od struktury lub *./bin/[configuration]/[framework]/[runtime]/publish/* dla niezależne wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-171">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="d7ebe-172">Jeśli ścieżka jest względna, katalog wyjściowy, generowany jest względem lokalizacji pliku projektu, aby bieżący katalog roboczy nie.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-172">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="d7ebe-173">Publikuje środowisko uruchomieniowe platformy .NET Core za pomocą aplikacji, dzięki czemu środowisko uruchomieniowe nie muszą być zainstalowane na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-173">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="d7ebe-174">Jeśli określono identyfikator środowiska uruchomieniowego, jego wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-174">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="d7ebe-175">Aby uzyskać więcej informacji na temat różne typy wdrożenia, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="d7ebe-175">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="d7ebe-176">Publikuje aplikację dla danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-176">Publishes the application for a given runtime.</span></span> <span data-ttu-id="d7ebe-177">To jest używany podczas tworzenia [niezależna wdrożenia (— SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="d7ebe-177">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="d7ebe-178">Aby uzyskać listę identyfikatorów środowisk uruchomieniowych (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="d7ebe-178">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="d7ebe-179">Domyślnie nie jest publikowanie [zależny od struktury wdrożenia (stacje)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="d7ebe-179">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d7ebe-180">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-180">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d7ebe-181">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-181">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="d7ebe-182">Określa sufiks wersji zastąpić gwiazdka (`*`) w polu wersja pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-182">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d7ebe-183">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d7ebe-183">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="d7ebe-184">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-184">Defines the build configuration.</span></span> <span data-ttu-id="d7ebe-185">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-185">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="d7ebe-186">Publikuje aplikację w określonym [platformę docelową](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="d7ebe-186">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="d7ebe-187">W pliku projektu, należy określić platformę docelową.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-187">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="d7ebe-188">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-188">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="d7ebe-189">Określa jeden lub kilka [docelowe manifesty](../deploying/runtime-store.md) na potrzeby trim zbiór pakiety opublikowane przy użyciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-189">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="d7ebe-190">Plik manifestu jest częścią danych wyjściowych [ `dotnet store` polecenia](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="d7ebe-190">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="d7ebe-191">Aby określić wiele manifestów, Dodaj `--manifest` opcji dla każdego manifestu.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-191">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="d7ebe-192">Ta opcja jest dostępna, począwszy od programu .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-192">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="d7ebe-193">Określa ścieżkę do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-193">Specifies the path for the output directory.</span></span> <span data-ttu-id="d7ebe-194">Jeśli nie zostanie określony, jego wartość domyślna to *./bin/[configuration]/[framework]/publish/* wdrożenia zależny od struktury lub *./bin/[configuration]/[framework]/[runtime]/publish/* dla niezależne wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-194">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="d7ebe-195">Jeśli ścieżka jest względna, katalog wyjściowy, generowany jest względem lokalizacji pliku projektu, aby bieżący katalog roboczy nie.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-195">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="d7ebe-196">Publikuje aplikację dla danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-196">Publishes the application for a given runtime.</span></span> <span data-ttu-id="d7ebe-197">To jest używany podczas tworzenia [niezależna wdrożenia (— SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="d7ebe-197">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="d7ebe-198">Aby uzyskać listę identyfikatorów środowisk uruchomieniowych (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="d7ebe-198">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="d7ebe-199">Domyślnie nie jest publikowanie [zależny od struktury wdrożenia (stacje)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="d7ebe-199">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d7ebe-200">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-200">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d7ebe-201">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-201">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="d7ebe-202">Określa sufiks wersji zastąpić gwiazdka (`*`) w polu wersja pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="d7ebe-202">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="d7ebe-203">Przykłady</span><span class="sxs-lookup"><span data-stu-id="d7ebe-203">Examples</span></span>

<span data-ttu-id="d7ebe-204">Opublikuj projekt w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="d7ebe-204">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="d7ebe-205">Publikowanie aplikacji przy użyciu pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="d7ebe-205">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`

<span data-ttu-id="d7ebe-206">Opublikuj projekt w bieżącym katalogu przy użyciu `netcoreapp1.1` framework:</span><span class="sxs-lookup"><span data-stu-id="d7ebe-206">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`

<span data-ttu-id="d7ebe-207">Publikowanie bieżącej aplikacji przy użyciu `netcoreapp1.1` struktura i środowisko uruchomieniowe dla `OS X 10.10` (musi zawierać ten identyfikatorów RID w pliku projektu).</span><span class="sxs-lookup"><span data-stu-id="d7ebe-207">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

<span data-ttu-id="d7ebe-208">Publikowanie bieżącej aplikacji, ale nie zostaną przywrócone do projektu (P2P) odwołań, po prostu projekt główny podczas operacji przywracania (.NET Core SDK 2.0 i nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="d7ebe-208">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet publish --no-dependencies`

## <a name="see-also"></a><span data-ttu-id="d7ebe-209">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d7ebe-209">See also</span></span>

- [<span data-ttu-id="d7ebe-210">Platformy docelowe</span><span class="sxs-lookup"><span data-stu-id="d7ebe-210">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="d7ebe-211">Katalog identyfikatora środowiska uruchomieniowego (RID)</span><span class="sxs-lookup"><span data-stu-id="d7ebe-211">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
