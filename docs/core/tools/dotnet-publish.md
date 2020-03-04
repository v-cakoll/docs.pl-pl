---
title: polecenie dotnet publish
description: Dotnet publish polecenie publikuje projekt .NET Core lub rozwiązanie w katalogu.
ms.date: 02/24/2020
ms.openlocfilehash: cf41ee09244faad03feb8ccda19135b8c7780106
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157002"
---
# <a name="dotnet-publish"></a><span data-ttu-id="a91d7-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="a91d7-103">dotnet publish</span></span>

<span data-ttu-id="a91d7-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="a91d7-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="a91d7-105">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="a91d7-105">Name</span></span>

<span data-ttu-id="a91d7-106">`dotnet publish` — publikuje aplikację wraz z jej zależnościami w folderze do wdrożenia w systemie hostingu.</span><span class="sxs-lookup"><span data-stu-id="a91d7-106">`dotnet publish` - Publishes the application and its dependencies to a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a91d7-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="a91d7-107">Synopsis</span></span>

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration] 
    [-f|--framework] [--force] [--interactive] [--manifest]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [--self-contained]
    [--no-self-contained] [-v|--verbosity] [--version-suffix]

dotnet publish [-h|--help]
```

## <a name="description"></a><span data-ttu-id="a91d7-108">Opis</span><span class="sxs-lookup"><span data-stu-id="a91d7-108">Description</span></span>

<span data-ttu-id="a91d7-109">`dotnet publish` kompiluje aplikację, odczytuje ją z zależności określonych w pliku projektu i publikuje zestaw plików w katalogu.</span><span class="sxs-lookup"><span data-stu-id="a91d7-109">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="a91d7-110">Dane wyjściowe obejmują następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="a91d7-110">The output includes the following assets:</span></span>

- <span data-ttu-id="a91d7-111">Kod języka pośredniego (IL) w zestawie z rozszerzeniem *dll* .</span><span class="sxs-lookup"><span data-stu-id="a91d7-111">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="a91d7-112">Plik *. deps. JSON* , który zawiera wszystkie zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="a91d7-112">A *.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="a91d7-113">Plik *. runtimeconfig. JSON* , który określa udostępnione środowisko uruchomieniowe oczekiwane przez aplikację, a także inne opcje konfiguracji środowiska uruchomieniowego (na przykład typ wyrzucania elementów bezużytecznych).</span><span class="sxs-lookup"><span data-stu-id="a91d7-113">A *.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="a91d7-114">Zależności aplikacji, które są kopiowane z pamięci podręcznej NuGet do folderu danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="a91d7-114">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="a91d7-115">Dane wyjściowe polecenia `dotnet publish` są gotowe do wdrożenia w systemie hostingu (na przykład serwer, komputer, Mac, laptop) do wykonania.</span><span class="sxs-lookup"><span data-stu-id="a91d7-115">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="a91d7-116">Jest to jedyna oficjalnie obsługiwana metoda przygotowania aplikacji do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="a91d7-116">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="a91d7-117">W zależności od typu wdrożenia, który jest określany przez projekt, system hostingu może lub nie ma zainstalowanego udostępnionego środowiska uruchomieniowego platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a91d7-117">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span>

## <a name="arguments"></a><span data-ttu-id="a91d7-118">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a91d7-118">Arguments</span></span>

- **`PROJECT|SOLUTION`**

  <span data-ttu-id="a91d7-119">Projekt lub rozwiązanie do opublikowania.</span><span class="sxs-lookup"><span data-stu-id="a91d7-119">The project or solution to publish.</span></span>
  
  * <span data-ttu-id="a91d7-120">`PROJECT` jest ścieżką i nazwą pliku projektu [C#](csproj.md), F#lub Visual Basic lub ścieżką do katalogu, który zawiera plik projektu C#, F#lub Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a91d7-120">`PROJECT` is the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="a91d7-121">Jeśli katalog nie jest określony, domyślnie jest bieżącym katalogiem.</span><span class="sxs-lookup"><span data-stu-id="a91d7-121">If the directory is not specified, it defaults to the current directory.</span></span>

  * <span data-ttu-id="a91d7-122">`SOLUTION` jest ścieżką i nazwą pliku rozwiązania (rozszerzeniem*sln* ) lub ścieżką do katalogu zawierającego plik rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="a91d7-122">`SOLUTION` is the path and filename of a solution file (*.sln* extension), or the path to a directory that contains a solution file.</span></span> <span data-ttu-id="a91d7-123">Jeśli katalog nie jest określony, domyślnie jest bieżącym katalogiem.</span><span class="sxs-lookup"><span data-stu-id="a91d7-123">If the directory is not specified, it defaults to the current directory.</span></span> <span data-ttu-id="a91d7-124">**Dostępne począwszy od zestawu SDK platformy .NET Core 3,0.**</span><span class="sxs-lookup"><span data-stu-id="a91d7-124">**Available starting with .NET Core 3.0 SDK.**</span></span> 

## <a name="options"></a><span data-ttu-id="a91d7-125">Opcje</span><span class="sxs-lookup"><span data-stu-id="a91d7-125">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="a91d7-126">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a91d7-126">Defines the build configuration.</span></span> <span data-ttu-id="a91d7-127">Wartość domyślna dla większości projektów jest `Debug`, ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.</span><span class="sxs-lookup"><span data-stu-id="a91d7-127">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="a91d7-128">Publikuje aplikację dla określonej [platformy docelowej](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="a91d7-128">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="a91d7-129">Należy określić platformę docelową w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="a91d7-129">You must specify the target framework in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="a91d7-130">Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a91d7-130">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="a91d7-131">Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="a91d7-131">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="a91d7-132">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="a91d7-132">Prints out a short help for the command.</span></span>

- <span data-ttu-id="a91d7-133">**`--interactive`** **dostępne począwszy od zestawu SDK platformy .NET Core 3,0.**</span><span class="sxs-lookup"><span data-stu-id="a91d7-133">**`--interactive`** **Available starting with .NET Core 3.0 SDK.**</span></span>

  <span data-ttu-id="a91d7-134">Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję.</span><span class="sxs-lookup"><span data-stu-id="a91d7-134">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="a91d7-135">Na przykład, aby ukończyć uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="a91d7-135">For example, to complete authentication.</span></span> 

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="a91d7-136">Określa jeden lub kilka [docelowych manifestów](../deploying/runtime-store.md) , które mają być używane do przycinania zestawu pakietów opublikowanych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a91d7-136">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="a91d7-137">Plik manifestu jest częścią danych wyjściowych [polecenia`dotnet store`](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="a91d7-137">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="a91d7-138">Aby określić wiele manifestów, Dodaj opcję `--manifest` dla każdego manifestu.</span><span class="sxs-lookup"><span data-stu-id="a91d7-138">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span>

- **`--no-build`**

  <span data-ttu-id="a91d7-139">Nie kompiluje projektu przed opublikowaniem.</span><span class="sxs-lookup"><span data-stu-id="a91d7-139">Doesn't build the project before publishing.</span></span> <span data-ttu-id="a91d7-140">Niejawnie ustawia również flagę `--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="a91d7-140">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="a91d7-141">Ignoruje odwołania projektu do projektu i przywraca tylko projekt główny.</span><span class="sxs-lookup"><span data-stu-id="a91d7-141">Ignores project-to-project references and only restores the root project.</span></span>

- <span data-ttu-id="a91d7-142">**`--nologo`** **dostępne począwszy od zestawu SDK platformy .NET Core 3,0.**</span><span class="sxs-lookup"><span data-stu-id="a91d7-142">**`--nologo`** **Available starting with .NET Core 3.0 SDK.**</span></span>

  <span data-ttu-id="a91d7-143">Nie wyświetla transparentu początkowego ani komunikatu o prawach autorskich.</span><span class="sxs-lookup"><span data-stu-id="a91d7-143">Doesn't display the startup banner or the copyright message.</span></span> 

- **`--no-restore`**

  <span data-ttu-id="a91d7-144">Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.</span><span class="sxs-lookup"><span data-stu-id="a91d7-144">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="a91d7-145">Określa ścieżkę do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="a91d7-145">Specifies the path for the output directory.</span></span> <span data-ttu-id="a91d7-146">Jeśli nie zostanie określony, domyślna wartość to *./bin/[Configuration]/[Framework]/Publish/* dla plików wykonywalnych zależnych od środowiska uruchomieniowego i międzyplatformowych plików binarnych.</span><span class="sxs-lookup"><span data-stu-id="a91d7-146">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a runtime-dependent executable and cross-platform binaries.</span></span> <span data-ttu-id="a91d7-147">Wartość domyślna to *./bin/[Konfiguracja]/[Framework]/[Runtime]/Publish/* dla samodzielnego pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="a91d7-147">It defaults to *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained executable.</span></span>

  <span data-ttu-id="a91d7-148">Jeśli ścieżka jest względna, wygenerowany katalog wyjściowy jest względem lokalizacji pliku projektu, a nie do bieżącego katalogu roboczego.</span><span class="sxs-lookup"><span data-stu-id="a91d7-148">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

- **`--self-contained [true|false]`**

  <span data-ttu-id="a91d7-149">Publikuje środowisko uruchomieniowe platformy .NET Core przy użyciu aplikacji, aby nie trzeba było instalować środowiska uruchomieniowego na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="a91d7-149">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="a91d7-150">Wartość domyślna to `true`, jeśli określono identyfikator środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="a91d7-150">Default is `true` if a runtime identifier is specified.</span></span> <span data-ttu-id="a91d7-151">Aby uzyskać więcej informacji, zobacz Aplikacje [.NET Core](../deploying/index.md) i publikowanie aplikacji [platformy .net core za pomocą interfejs wiersza polecenia platformy .NET Core](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="a91d7-151">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- <span data-ttu-id="a91d7-152">**`--no-self-contained`** **dostępne począwszy od zestawu SDK platformy .NET Core 3,0.**</span><span class="sxs-lookup"><span data-stu-id="a91d7-152">**`--no-self-contained`**  **Available starting with .NET Core 3.0 SDK.**</span></span>

  <span data-ttu-id="a91d7-153">Równoważne `--self-contained false`.</span><span class="sxs-lookup"><span data-stu-id="a91d7-153">Equivalent to `--self-contained false`.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="a91d7-154">Publikuje aplikację dla danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="a91d7-154">Publishes the application for a given runtime.</span></span> <span data-ttu-id="a91d7-155">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="a91d7-155">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="a91d7-156">Aby uzyskać więcej informacji, zobacz Aplikacje [.NET Core](../deploying/index.md) i publikowanie aplikacji [platformy .net core za pomocą interfejs wiersza polecenia platformy .NET Core](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="a91d7-156">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="a91d7-157">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="a91d7-157">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a91d7-158">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a91d7-158">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="a91d7-159">Definiuje sufiks wersji, aby zastąpić gwiazdkę (`*`) w polu wersja pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="a91d7-159">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

## <a name="examples"></a><span data-ttu-id="a91d7-160">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a91d7-160">Examples</span></span>

- <span data-ttu-id="a91d7-161">Utwórz [Międzyplatformowy plik binarny zależny od środowiska uruchomieniowego](../deploying/index.md#produce-a-cross-platform-binary) dla projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="a91d7-161">Create a [runtime-dependent cross-platform binary](../deploying/index.md#produce-a-cross-platform-binary) for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet publish
  ```

  <span data-ttu-id="a91d7-162">Począwszy od zestawu SDK platformy .NET Core 3,0, w tym przykładzie tworzony jest również [plik wykonywalny zależny od środowiska uruchomieniowego](../deploying/index.md#publish-runtime-dependent) dla bieżącej platformy.</span><span class="sxs-lookup"><span data-stu-id="a91d7-162">Starting with .NET Core 3.0 SDK, this example also creates a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the current platform.</span></span>

- <span data-ttu-id="a91d7-163">Utwórz [własny plik wykonywalny](../deploying/index.md#publish-self-contained) dla projektu w bieżącym katalogu dla określonego środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="a91d7-163">Create a [self-contained executable](../deploying/index.md#publish-self-contained) for the project in the current directory, for a specific runtime:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  <span data-ttu-id="a91d7-164">Identyfikator RID musi znajdować się w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="a91d7-164">The RID must be in the project file.</span></span>

- <span data-ttu-id="a91d7-165">Utwórz [plik wykonywalny zależny od środowiska uruchomieniowego](../deploying/index.md#publish-runtime-dependent) dla projektu w bieżącym katalogu dla określonej platformy:</span><span class="sxs-lookup"><span data-stu-id="a91d7-165">Create a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the project in the current directory, for a specific platform:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  <span data-ttu-id="a91d7-166">Identyfikator RID musi znajdować się w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="a91d7-166">The RID must be in the project file.</span></span> <span data-ttu-id="a91d7-167">Ten przykład dotyczy zestawu .NET Core 3,0 SDK i nowszych wersji.</span><span class="sxs-lookup"><span data-stu-id="a91d7-167">This example applies to .NET Core 3.0 SDK and later versions.</span></span>

- <span data-ttu-id="a91d7-168">Opublikuj projekt w bieżącym katalogu dla określonego środowiska uruchomieniowego i platformy docelowej:</span><span class="sxs-lookup"><span data-stu-id="a91d7-168">Publish the project in the current directory, for a specific runtime and target framework:</span></span>

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- <span data-ttu-id="a91d7-169">Publikuj określony plik projektu:</span><span class="sxs-lookup"><span data-stu-id="a91d7-169">Publish the specified project file:</span></span>

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="a91d7-170">Opublikuj bieżącą aplikację, ale nie przywracaj odwołań z projektu do projektu (P2P), tylko projekt główny podczas operacji przywracania:</span><span class="sxs-lookup"><span data-stu-id="a91d7-170">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation:</span></span>

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a><span data-ttu-id="a91d7-171">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a91d7-171">See also</span></span>

- [<span data-ttu-id="a91d7-172">Omówienie publikowania aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="a91d7-172">.NET Core application publishing overview</span></span>](../deploying/index.md)
- [<span data-ttu-id="a91d7-173">Publikowanie aplikacji platformy .NET Core za pomocą interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="a91d7-173">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="a91d7-174">Platformy docelowe</span><span class="sxs-lookup"><span data-stu-id="a91d7-174">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="a91d7-175">Wykaz identyfikatorów środowiska uruchomieniowego (RID)</span><span class="sxs-lookup"><span data-stu-id="a91d7-175">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- <span data-ttu-id="a91d7-176">[Praca z MacOS Catalina Notarization](../install/macos-notarization-issues.md) Aby uzyskać więcej informacji, zobacz następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="a91d7-176">[Working with macOS Catalina Notarization](../install/macos-notarization-issues.md) For more information, see he following resources:</span></span>
- [<span data-ttu-id="a91d7-177">Struktura katalogów opublikowanej aplikacji</span><span class="sxs-lookup"><span data-stu-id="a91d7-177">Directory structure of a published application</span></span>](/aspnet/core/hosting/directory-structure)
