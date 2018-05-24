---
title: polecenie - .NET Core interfejsu wiersza polecenia Opublikuj DotNet
description: Polecenie Publikuj dotnet publikuje projektu platformy .NET Core w katalogu.
author: mairaw
ms.author: mairaw
ms.date: 03/10/2018
ms.openlocfilehash: 8509f1a721c0b4b4c05d68e0f98f9b856bcc5a8e
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="dotnet-publish"></a><span data-ttu-id="e6c59-103">Publikowanie DotNet</span><span class="sxs-lookup"><span data-stu-id="e6c59-103">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="e6c59-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="e6c59-104">Name</span></span>

<span data-ttu-id="e6c59-105">`dotnet publish` -Pakietów aplikacji i jego zależności do folderu wdrożenia z systemem hostingu.</span><span class="sxs-lookup"><span data-stu-id="e6c59-105">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e6c59-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="e6c59-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="e6c59-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="e6c59-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies] [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="e6c59-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="e6c59-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="e6c59-109">Opis</span><span class="sxs-lookup"><span data-stu-id="e6c59-109">Description</span></span>

<span data-ttu-id="e6c59-110">`dotnet publish` kompiluje aplikacji odczytuje za pośrednictwem jego zależności, określona w pliku projektu i publikuje Wynikowy zestaw plików w katalogu.</span><span class="sxs-lookup"><span data-stu-id="e6c59-110">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="e6c59-111">Dane wyjściowe będą zawierać następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="e6c59-111">The output will contain the following:</span></span>

* <span data-ttu-id="e6c59-112">Kod języka (IL) w zestawie z pośredniego *dll* rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="e6c59-112">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
* <span data-ttu-id="e6c59-113">*. deps.json* pliku, który zawiera wszystkie zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="e6c59-113">*.deps.json* file that contains all of the dependencies of the project.</span></span>
* <span data-ttu-id="e6c59-114">*. runtime.config.json* pliku, który określa udostępnionego środowisko uruchomieniowe, które oczekuje aplikacji, a także innych opcji konfiguracji dla środowiska uruchomieniowego (na przykład typ kolekcji pamięci).</span><span class="sxs-lookup"><span data-stu-id="e6c59-114">*.runtime.config.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
* <span data-ttu-id="e6c59-115">Zależności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e6c59-115">The application's dependencies.</span></span> <span data-ttu-id="e6c59-116">Te są kopiowane z pamięci podręcznej NuGet do folderu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="e6c59-116">These are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="e6c59-117">`dotnet publish` Danych wyjściowych polecenia jest gotowy do wdrożenia do obsługi systemu (na przykład serwer, PC, Mac, laptop) do wykonania i jest jedynym oficjalnie obsługiwana sposobu przygotowania aplikacji do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="e6c59-117">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution and is the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="e6c59-118">W zależności od typu wdrożenia, który określa projekt system obsługujący może lub nie może być .NET Core współużytkowany środowiska uruchomieniowego na nim zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="e6c59-118">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="e6c59-119">Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="e6c59-119">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="e6c59-120">Do struktury katalogu opublikowanej aplikacji, zobacz [struktury katalogów](/aspnet/core/hosting/directory-structure).</span><span class="sxs-lookup"><span data-stu-id="e6c59-120">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="e6c59-121">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e6c59-121">Arguments</span></span>

`PROJECT`

<span data-ttu-id="e6c59-122">Projekt do publikowania, domyślnie do bieżącego katalogu, jeśli nie zostanie określony.</span><span class="sxs-lookup"><span data-stu-id="e6c59-122">The project to publish, which defaults to the current directory if not specified.</span></span>

## <a name="options"></a><span data-ttu-id="e6c59-123">Opcje</span><span class="sxs-lookup"><span data-stu-id="e6c59-123">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="e6c59-124">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="e6c59-124">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="e6c59-125">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e6c59-125">Defines the build configuration.</span></span> <span data-ttu-id="e6c59-126">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="e6c59-126">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="e6c59-127">Publikowanie aplikacji dla określonego [platformy docelowej](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e6c59-127">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="e6c59-128">Należy określić w pliku projektu platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="e6c59-128">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="e6c59-129">Wymusza wszystkie zależności, które można rozwiązać, nawet jeśli ostatniego przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e6c59-129">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="e6c59-130">Jest to równoważne usuwanie *project.assets.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="e6c59-130">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="e6c59-131">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="e6c59-131">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="e6c59-132">Określa jeden lub kilka [target manifestów](../deploying/runtime-store.md) na potrzeby trim zestaw pakietów opublikowane z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="e6c59-132">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="e6c59-133">Plik manifestu jest częścią dane wyjściowe [ `dotnet store` polecenia](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="e6c59-133">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="e6c59-134">Aby określić wiele manifestów, Dodaj `--manifest` opcji dla każdego manifestu.</span><span class="sxs-lookup"><span data-stu-id="e6c59-134">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="e6c59-135">Ta opcja jest dostępna, począwszy od zestawu SDK programu .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="e6c59-135">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="e6c59-136">Ignoruje odwołania projektu do projektu i przywraca tylko projektu głównego.</span><span class="sxs-lookup"><span data-stu-id="e6c59-136">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="e6c59-137">Nie wykonać przywracanie niejawne, podczas uruchamiania polecenia.</span><span class="sxs-lookup"><span data-stu-id="e6c59-137">Doesn't perform an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="e6c59-138">Określa ścieżkę do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="e6c59-138">Specifies the path for the output directory.</span></span> <span data-ttu-id="e6c59-139">Jeśli nie zostanie określony, domyślnie *./bin/[configuration]/[framework]/publish/* wdrożenia zależne od framework lub *./bin/[configuration]/[framework]/[runtime]/publish/* dla Samodzielne wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="e6c59-139">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="e6c59-140">W przypadku ścieżki względnej do katalogu wyjściowego, generowane jest względną wobec lokalizacji pliku projektu, aby bieżący katalog roboczy nie.</span><span class="sxs-lookup"><span data-stu-id="e6c59-140">If a relative path is provided, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="e6c59-141">Publikuje środowiska uruchomieniowego .NET Core z aplikacji, więc środowisko uruchomieniowe nie musi być zainstalowany na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="e6c59-141">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="e6c59-142">Jeśli określono identyfikator środowiska uruchomieniowego, jego wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="e6c59-142">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="e6c59-143">Aby uzyskać więcej informacji na temat różne typy wdrożenia, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="e6c59-143">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="e6c59-144">Publikowanie aplikacji dla danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="e6c59-144">Publishes the application for a given runtime.</span></span> <span data-ttu-id="e6c59-145">To jest używany podczas tworzenia [niezależne wdrożenia (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="e6c59-145">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="e6c59-146">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="e6c59-146">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="e6c59-147">Domyślnie nie jest publikowanie [wdrożenia framework zależne (stacje)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="e6c59-147">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="e6c59-148">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="e6c59-148">Sets the verbosity level of the command.</span></span> <span data-ttu-id="e6c59-149">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="e6c59-149">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="e6c59-150">Definiuje sufiksem wersji, aby zastąpić gwiazdka (`*`) w polu wersja pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="e6c59-150">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="e6c59-151">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="e6c59-151">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="e6c59-152">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e6c59-152">Defines the build configuration.</span></span> <span data-ttu-id="e6c59-153">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="e6c59-153">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="e6c59-154">Publikowanie aplikacji dla określonego [platformy docelowej](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e6c59-154">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="e6c59-155">Należy określić w pliku projektu platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="e6c59-155">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="e6c59-156">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="e6c59-156">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="e6c59-157">Określa jeden lub kilka [target manifestów](../deploying/runtime-store.md) na potrzeby trim zestaw pakietów opublikowane z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="e6c59-157">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="e6c59-158">Plik manifestu jest częścią dane wyjściowe [ `dotnet store` polecenia](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="e6c59-158">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="e6c59-159">Aby określić wiele manifestów, Dodaj `--manifest` opcji dla każdego manifestu.</span><span class="sxs-lookup"><span data-stu-id="e6c59-159">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="e6c59-160">Ta opcja jest dostępna, począwszy od zestawu SDK programu .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="e6c59-160">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="e6c59-161">Określa ścieżkę do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="e6c59-161">Specifies the path for the output directory.</span></span> <span data-ttu-id="e6c59-162">Jeśli nie zostanie określony, domyślnie *./bin/[configuration]/[framework]/publish/* wdrożenia zależne od framework lub *./bin/[configuration]/[framework]/[runtime]/publish/* dla Samodzielne wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="e6c59-162">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="e6c59-163">W przypadku ścieżki względnej do katalogu wyjściowego, generowane jest względną wobec lokalizacji pliku projektu, aby bieżący katalog roboczy nie.</span><span class="sxs-lookup"><span data-stu-id="e6c59-163">If a relative path is provided, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="e6c59-164">Publikowanie aplikacji dla danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="e6c59-164">Publishes the application for a given runtime.</span></span> <span data-ttu-id="e6c59-165">To jest używany podczas tworzenia [niezależne wdrożenia (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="e6c59-165">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="e6c59-166">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="e6c59-166">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="e6c59-167">Domyślnie nie jest publikowanie [wdrożenia framework zależne (stacje)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="e6c59-167">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="e6c59-168">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="e6c59-168">Sets the verbosity level of the command.</span></span> <span data-ttu-id="e6c59-169">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="e6c59-169">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="e6c59-170">Definiuje sufiksem wersji, aby zastąpić gwiazdka (`*`) w polu wersja pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="e6c59-170">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="e6c59-171">Przykłady</span><span class="sxs-lookup"><span data-stu-id="e6c59-171">Examples</span></span>

<span data-ttu-id="e6c59-172">Publikuj projekt w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="e6c59-172">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="e6c59-173">Publikowanie aplikacji przy użyciu pliku określonego projektu:</span><span class="sxs-lookup"><span data-stu-id="e6c59-173">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`

<span data-ttu-id="e6c59-174">Opublikować projekt w bieżącym katalogu, używając `netcoreapp1.1` framework:</span><span class="sxs-lookup"><span data-stu-id="e6c59-174">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`

<span data-ttu-id="e6c59-175">Publikowanie bieżącej aplikacji przy użyciu `netcoreapp1.1` framework i środowiska uruchomieniowego dla `OS X 10.10` (musi zawierać ten identyfikatorów RID w pliku projektu).</span><span class="sxs-lookup"><span data-stu-id="e6c59-175">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

<span data-ttu-id="e6c59-176">Publikowanie bieżącej aplikacji, ale nie należy przywracać projektu do projektu (P2P) odwołań, po prostu główny projekt podczas operacji przywracania (.NET Core SDK 2.0 i nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="e6c59-176">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet publish --no-dependencies`

## <a name="see-also"></a><span data-ttu-id="e6c59-177">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6c59-177">See also</span></span>

* [<span data-ttu-id="e6c59-178">Platformy docelowe</span><span class="sxs-lookup"><span data-stu-id="e6c59-178">Target frameworks</span></span>](../../standard/frameworks.md)
* [<span data-ttu-id="e6c59-179">Wykaz identyfikatora środowiska uruchomieniowego (RID)</span><span class="sxs-lookup"><span data-stu-id="e6c59-179">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
