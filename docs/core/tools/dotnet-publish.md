---
title: polecenie - .NET Core interfejsu wiersza polecenia Opublikuj DotNet
description: Polecenie Publikuj dotnet publikuje projektu platformy .NET Core w katalogu.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 38224aa8472f99df107e523667e18892384a20b0
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696663"
---
# <a name="dotnet-publish"></a><span data-ttu-id="153a0-103">Publikowanie DotNet</span><span class="sxs-lookup"><span data-stu-id="153a0-103">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="153a0-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="153a0-104">Name</span></span>

<span data-ttu-id="153a0-105">`dotnet publish` -Pakietów aplikacji i jego zależności do folderu wdrożenia z systemem hostingu.</span><span class="sxs-lookup"><span data-stu-id="153a0-105">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="153a0-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="153a0-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="153a0-107">Oprogramowanie .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="153a0-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="153a0-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="153a0-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="153a0-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="153a0-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="153a0-110">Opis</span><span class="sxs-lookup"><span data-stu-id="153a0-110">Description</span></span>

<span data-ttu-id="153a0-111">`dotnet publish` kompiluje aplikacji odczytuje za pośrednictwem jego zależności, określona w pliku projektu i publikuje Wynikowy zestaw plików w katalogu.</span><span class="sxs-lookup"><span data-stu-id="153a0-111">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="153a0-112">Dane wyjściowe zawierają następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="153a0-112">The output includes the following assets:</span></span>

* <span data-ttu-id="153a0-113">Kod języka (IL) w zestawie z pośredniego *dll* rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="153a0-113">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
* <span data-ttu-id="153a0-114">*. deps.json* pliku, który zawiera wszystkie zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="153a0-114">*.deps.json* file that includes all of the dependencies of the project.</span></span>
* <span data-ttu-id="153a0-115">*. runtime.config.json* pliku, który określa udostępnionego środowisko uruchomieniowe, które oczekuje aplikacji, a także innych opcji konfiguracji dla środowiska uruchomieniowego (na przykład typ kolekcji pamięci).</span><span class="sxs-lookup"><span data-stu-id="153a0-115">*.runtime.config.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
* <span data-ttu-id="153a0-116">Zależności aplikacji, które są kopiowane z pamięci podręcznej NuGet w folderze wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="153a0-116">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="153a0-117">`dotnet publish` Danych wyjściowych polecenia jest gotowy do wdrożenia do obsługi systemu (na przykład serwer, PC, Mac, laptop) do wykonania.</span><span class="sxs-lookup"><span data-stu-id="153a0-117">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="153a0-118">Jest jedynym sposobem wspieranych do przygotowania aplikacji do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="153a0-118">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="153a0-119">W zależności od typu wdrożenia, który określa projekt system obsługujący może lub nie może być .NET Core współużytkowany środowiska uruchomieniowego na nim zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="153a0-119">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="153a0-120">Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="153a0-120">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="153a0-121">Do struktury katalogu opublikowanej aplikacji, zobacz [struktury katalogów](/aspnet/core/hosting/directory-structure).</span><span class="sxs-lookup"><span data-stu-id="153a0-121">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="153a0-122">Argumenty</span><span class="sxs-lookup"><span data-stu-id="153a0-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="153a0-123">Projekt do opublikowania.</span><span class="sxs-lookup"><span data-stu-id="153a0-123">The project to publish.</span></span> <span data-ttu-id="153a0-124">Jeśli nie zostanie określony, domyślnie do bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="153a0-124">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="153a0-125">Opcje</span><span class="sxs-lookup"><span data-stu-id="153a0-125">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="153a0-126">Oprogramowanie .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="153a0-126">.NET Core 2.1</span></span>](#tab/netcore21)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="153a0-127">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="153a0-127">Defines the build configuration.</span></span> <span data-ttu-id="153a0-128">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="153a0-128">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="153a0-129">Publikowanie aplikacji dla określonego [platformy docelowej](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="153a0-129">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="153a0-130">Należy określić w pliku projektu platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="153a0-130">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="153a0-131">Wymusza wszystkie zależności, które można rozwiązać, nawet jeśli ostatniego przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="153a0-131">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="153a0-132">Określenie ta flaga jest taka sama jak usuwanie *project.assets.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="153a0-132">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="153a0-133">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="153a0-133">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="153a0-134">Określa jeden lub kilka [target manifestów](../deploying/runtime-store.md) na potrzeby trim zestaw pakietów opublikowane z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="153a0-134">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="153a0-135">Plik manifestu jest częścią dane wyjściowe [ `dotnet store` polecenia](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="153a0-135">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="153a0-136">Aby określić wiele manifestów, Dodaj `--manifest` opcji dla każdego manifestu.</span><span class="sxs-lookup"><span data-stu-id="153a0-136">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="153a0-137">Ta opcja jest dostępna, począwszy od zestawu SDK programu .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="153a0-137">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-build`

<span data-ttu-id="153a0-138">Nie Skompiluj projekt przed opublikowaniem.</span><span class="sxs-lookup"><span data-stu-id="153a0-138">Doesn't build the project before publishing.</span></span> <span data-ttu-id="153a0-139">Niejawne także ustawia `--no-restore` flagi.</span><span class="sxs-lookup"><span data-stu-id="153a0-139">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="153a0-140">Ignoruje odwołania projektu do projektu i przywraca tylko projektu głównego.</span><span class="sxs-lookup"><span data-stu-id="153a0-140">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="153a0-141">Podczas uruchamiania polecenia przywracania niejawne nie jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="153a0-141">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="153a0-142">Określa ścieżkę do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="153a0-142">Specifies the path for the output directory.</span></span> <span data-ttu-id="153a0-143">Jeśli nie zostanie określony, domyślnie *./bin/[configuration]/[framework]/publish/* wdrożenia zależne od framework lub *./bin/[configuration]/[framework]/[runtime]/publish/* dla Samodzielne wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="153a0-143">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="153a0-144">W przypadku względną ścieżkę do katalogu wyjściowego, generowane jest względną wobec lokalizacji pliku projektu, aby bieżący katalog roboczy nie.</span><span class="sxs-lookup"><span data-stu-id="153a0-144">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="153a0-145">Publikuje środowiska uruchomieniowego .NET Core z aplikacji, więc środowisko uruchomieniowe nie musi być zainstalowany na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="153a0-145">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="153a0-146">Jeśli określono identyfikator środowiska uruchomieniowego, jego wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="153a0-146">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="153a0-147">Aby uzyskać więcej informacji na temat różne typy wdrożenia, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="153a0-147">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="153a0-148">Publikowanie aplikacji dla danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="153a0-148">Publishes the application for a given runtime.</span></span> <span data-ttu-id="153a0-149">To jest używany podczas tworzenia [niezależne wdrożenia (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="153a0-149">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="153a0-150">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="153a0-150">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="153a0-151">Domyślnie nie jest publikowanie [wdrożenia framework zależne (stacje)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="153a0-151">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="153a0-152">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="153a0-152">Sets the verbosity level of the command.</span></span> <span data-ttu-id="153a0-153">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="153a0-153">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="153a0-154">Definiuje sufiksem wersji, aby zastąpić gwiazdka (`*`) w polu wersja pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="153a0-154">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="153a0-155">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="153a0-155">.NET Core 2.0</span></span>](#tab/netcore20)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="153a0-156">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="153a0-156">Defines the build configuration.</span></span> <span data-ttu-id="153a0-157">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="153a0-157">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="153a0-158">Publikowanie aplikacji dla określonego [platformy docelowej](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="153a0-158">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="153a0-159">Należy określić w pliku projektu platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="153a0-159">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="153a0-160">Wymusza wszystkie zależności, które można rozwiązać, nawet jeśli ostatniego przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="153a0-160">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="153a0-161">Określenie ta flaga jest taka sama jak usuwanie *project.assets.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="153a0-161">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="153a0-162">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="153a0-162">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="153a0-163">Określa jeden lub kilka [target manifestów](../deploying/runtime-store.md) na potrzeby trim zestaw pakietów opublikowane z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="153a0-163">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="153a0-164">Plik manifestu jest częścią dane wyjściowe [ `dotnet store` polecenia](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="153a0-164">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="153a0-165">Aby określić wiele manifestów, Dodaj `--manifest` opcji dla każdego manifestu.</span><span class="sxs-lookup"><span data-stu-id="153a0-165">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="153a0-166">Ta opcja jest dostępna, począwszy od zestawu SDK programu .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="153a0-166">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="153a0-167">Ignoruje odwołania projektu do projektu i przywraca tylko projektu głównego.</span><span class="sxs-lookup"><span data-stu-id="153a0-167">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="153a0-168">Podczas uruchamiania polecenia przywracania niejawne nie jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="153a0-168">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="153a0-169">Określa ścieżkę do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="153a0-169">Specifies the path for the output directory.</span></span> <span data-ttu-id="153a0-170">Jeśli nie zostanie określony, domyślnie *./bin/[configuration]/[framework]/publish/* wdrożenia zależne od framework lub *./bin/[configuration]/[framework]/[runtime]/publish/* dla Samodzielne wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="153a0-170">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="153a0-171">W przypadku względną ścieżkę do katalogu wyjściowego, generowane jest względną wobec lokalizacji pliku projektu, aby bieżący katalog roboczy nie.</span><span class="sxs-lookup"><span data-stu-id="153a0-171">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="153a0-172">Publikuje środowiska uruchomieniowego .NET Core z aplikacji, więc środowisko uruchomieniowe nie musi być zainstalowany na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="153a0-172">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="153a0-173">Jeśli określono identyfikator środowiska uruchomieniowego, jego wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="153a0-173">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="153a0-174">Aby uzyskać więcej informacji na temat różne typy wdrożenia, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="153a0-174">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="153a0-175">Publikowanie aplikacji dla danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="153a0-175">Publishes the application for a given runtime.</span></span> <span data-ttu-id="153a0-176">To jest używany podczas tworzenia [niezależne wdrożenia (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="153a0-176">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="153a0-177">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="153a0-177">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="153a0-178">Domyślnie nie jest publikowanie [wdrożenia framework zależne (stacje)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="153a0-178">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="153a0-179">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="153a0-179">Sets the verbosity level of the command.</span></span> <span data-ttu-id="153a0-180">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="153a0-180">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="153a0-181">Definiuje sufiksem wersji, aby zastąpić gwiazdka (`*`) w polu wersja pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="153a0-181">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="153a0-182">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="153a0-182">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="153a0-183">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="153a0-183">Defines the build configuration.</span></span> <span data-ttu-id="153a0-184">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="153a0-184">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="153a0-185">Publikowanie aplikacji dla określonego [platformy docelowej](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="153a0-185">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="153a0-186">Należy określić w pliku projektu platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="153a0-186">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="153a0-187">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="153a0-187">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="153a0-188">Określa jeden lub kilka [target manifestów](../deploying/runtime-store.md) na potrzeby trim zestaw pakietów opublikowane z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="153a0-188">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="153a0-189">Plik manifestu jest częścią dane wyjściowe [ `dotnet store` polecenia](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="153a0-189">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="153a0-190">Aby określić wiele manifestów, Dodaj `--manifest` opcji dla każdego manifestu.</span><span class="sxs-lookup"><span data-stu-id="153a0-190">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="153a0-191">Ta opcja jest dostępna, począwszy od zestawu SDK programu .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="153a0-191">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="153a0-192">Określa ścieżkę do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="153a0-192">Specifies the path for the output directory.</span></span> <span data-ttu-id="153a0-193">Jeśli nie zostanie określony, domyślnie *./bin/[configuration]/[framework]/publish/* wdrożenia zależne od framework lub *./bin/[configuration]/[framework]/[runtime]/publish/* dla Samodzielne wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="153a0-193">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="153a0-194">W przypadku względną ścieżkę do katalogu wyjściowego, generowane jest względną wobec lokalizacji pliku projektu, aby bieżący katalog roboczy nie.</span><span class="sxs-lookup"><span data-stu-id="153a0-194">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="153a0-195">Publikowanie aplikacji dla danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="153a0-195">Publishes the application for a given runtime.</span></span> <span data-ttu-id="153a0-196">To jest używany podczas tworzenia [niezależne wdrożenia (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="153a0-196">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="153a0-197">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="153a0-197">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="153a0-198">Domyślnie nie jest publikowanie [wdrożenia framework zależne (stacje)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="153a0-198">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="153a0-199">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="153a0-199">Sets the verbosity level of the command.</span></span> <span data-ttu-id="153a0-200">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="153a0-200">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="153a0-201">Definiuje sufiksem wersji, aby zastąpić gwiazdka (`*`) w polu wersja pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="153a0-201">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="153a0-202">Przykłady</span><span class="sxs-lookup"><span data-stu-id="153a0-202">Examples</span></span>

<span data-ttu-id="153a0-203">Publikuj projekt w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="153a0-203">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="153a0-204">Publikowanie aplikacji przy użyciu pliku określonego projektu:</span><span class="sxs-lookup"><span data-stu-id="153a0-204">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`

<span data-ttu-id="153a0-205">Opublikować projekt w bieżącym katalogu, używając `netcoreapp1.1` framework:</span><span class="sxs-lookup"><span data-stu-id="153a0-205">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`

<span data-ttu-id="153a0-206">Publikowanie bieżącej aplikacji przy użyciu `netcoreapp1.1` framework i środowiska uruchomieniowego dla `OS X 10.10` (musi zawierać ten identyfikatorów RID w pliku projektu).</span><span class="sxs-lookup"><span data-stu-id="153a0-206">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

<span data-ttu-id="153a0-207">Publikowanie bieżącej aplikacji, ale nie należy przywracać projektu do projektu (P2P) odwołań, po prostu główny projekt podczas operacji przywracania (.NET Core SDK 2.0 i nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="153a0-207">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet publish --no-dependencies`

## <a name="see-also"></a><span data-ttu-id="153a0-208">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="153a0-208">See also</span></span>

* [<span data-ttu-id="153a0-209">Platformy docelowe</span><span class="sxs-lookup"><span data-stu-id="153a0-209">Target frameworks</span></span>](../../standard/frameworks.md)
* [<span data-ttu-id="153a0-210">Wykaz identyfikatora środowiska uruchomieniowego (RID)</span><span class="sxs-lookup"><span data-stu-id="153a0-210">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
