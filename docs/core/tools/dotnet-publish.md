---
title: polecenie publikowania dotnet
description: Polecenie publikowania dotnet publikuje projekt lub rozwiązanie programu .NET Core w katalogu.
ms.date: 02/24/2020
ms.openlocfilehash: c34618409c9a539043c84c7e03daa8aa249d64f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146558"
---
# <a name="dotnet-publish"></a><span data-ttu-id="9c975-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="9c975-103">dotnet publish</span></span>

<span data-ttu-id="9c975-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.1 SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="9c975-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="9c975-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="9c975-105">Name</span></span>

<span data-ttu-id="9c975-106">`dotnet publish`- Publikuje aplikację i jej zależności do folderu do wdrożenia w systemie hostingowym.</span><span class="sxs-lookup"><span data-stu-id="9c975-106">`dotnet publish` - Publishes the application and its dependencies to a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9c975-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="9c975-107">Synopsis</span></span>

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration]
    [-f|--framework] [--force] [--interactive] [--manifest]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [--self-contained]
    [--no-self-contained] [-v|--verbosity] [--version-suffix]

dotnet publish [-h|--help]
```

## <a name="description"></a><span data-ttu-id="9c975-108">Opis</span><span class="sxs-lookup"><span data-stu-id="9c975-108">Description</span></span>

<span data-ttu-id="9c975-109">`dotnet publish`kompiluje aplikację, odczytuje jej zależności określone w pliku projektu i publikuje wynikowy zestaw plików do katalogu.</span><span class="sxs-lookup"><span data-stu-id="9c975-109">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="9c975-110">Dane wyjściowe obejmują następujące aktywa:</span><span class="sxs-lookup"><span data-stu-id="9c975-110">The output includes the following assets:</span></span>

- <span data-ttu-id="9c975-111">Kod języka pośredniego (IL) w zestawie z rozszerzeniem *dll.*</span><span class="sxs-lookup"><span data-stu-id="9c975-111">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="9c975-112">Plik *.deps.json,* który zawiera wszystkie zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="9c975-112">A *.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="9c975-113">Plik *.runtimeconfig.json,* który określa udostępniony czas wykonywania, który oczekuje aplikacji, a także inne opcje konfiguracji dla czasu wykonywania (na przykład typ wyrzucania elementów bezużytecznych).</span><span class="sxs-lookup"><span data-stu-id="9c975-113">A *.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="9c975-114">Zależności aplikacji, które są kopiowane z pamięci podręcznej NuGet do folderu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="9c975-114">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="9c975-115">Dane `dotnet publish` wyjściowe polecenia są gotowe do wdrożenia w systemie hostingowym (na przykład serwer, komputer PC, Mac, laptop) do wykonania.</span><span class="sxs-lookup"><span data-stu-id="9c975-115">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="9c975-116">Jest to jedyny oficjalnie obsługiwany sposób przygotowania aplikacji do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="9c975-116">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="9c975-117">W zależności od typu wdrożenia, który określa projekt, system hostingu może lub nie może mieć zainstalowanego udostępnionego programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9c975-117">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span>

## <a name="arguments"></a><span data-ttu-id="9c975-118">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9c975-118">Arguments</span></span>

- **`PROJECT|SOLUTION`**

  <span data-ttu-id="9c975-119">Projekt lub rozwiązanie do opublikowania.</span><span class="sxs-lookup"><span data-stu-id="9c975-119">The project or solution to publish.</span></span>
  
  * <span data-ttu-id="9c975-120">`PROJECT`to ścieżka i nazwa pliku pliku projektu [Języka C#,](csproj.md)F# lub Visual Basic lub ścieżka do katalogu zawierającego plik projektu Języka C#, F# lub Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9c975-120">`PROJECT` is the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="9c975-121">Jeśli katalog nie jest określony, domyślnie jest to bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="9c975-121">If the directory is not specified, it defaults to the current directory.</span></span>

  * <span data-ttu-id="9c975-122">`SOLUTION`to ścieżka i nazwa pliku pliku rozwiązania *(rozszerzenie sln)* lub ścieżka do katalogu zawierającego plik rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9c975-122">`SOLUTION` is the path and filename of a solution file (*.sln* extension), or the path to a directory that contains a solution file.</span></span> <span data-ttu-id="9c975-123">Jeśli katalog nie jest określony, domyślnie jest to bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="9c975-123">If the directory is not specified, it defaults to the current directory.</span></span> <span data-ttu-id="9c975-124">Dostępne od sdk .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="9c975-124">Available since .NET Core 3.0 SDK.</span></span>

## <a name="options"></a><span data-ttu-id="9c975-125">Opcje</span><span class="sxs-lookup"><span data-stu-id="9c975-125">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="9c975-126">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9c975-126">Defines the build configuration.</span></span> <span data-ttu-id="9c975-127">Wartość domyślna dla `Debug`większości projektów jest , ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.</span><span class="sxs-lookup"><span data-stu-id="9c975-127">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="9c975-128">Publikuje aplikację dla określonej [struktury docelowej](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="9c975-128">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="9c975-129">Należy określić platformę docelową w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="9c975-129">You must specify the target framework in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="9c975-130">Wymusza rozwiązywanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9c975-130">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="9c975-131">Określenie tej flagi jest takie samo jak usunięcie pliku *project.assets.json.*</span><span class="sxs-lookup"><span data-stu-id="9c975-131">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="9c975-132">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="9c975-132">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="9c975-133">Umożliwia zatrzymanie polecenia i oczekiwanie na wejście użytkownika lub akcję.</span><span class="sxs-lookup"><span data-stu-id="9c975-133">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="9c975-134">Na przykład, aby zakończyć uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="9c975-134">For example, to complete authentication.</span></span> <span data-ttu-id="9c975-135">Dostępne od sdk .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="9c975-135">Available since .NET Core 3.0 SDK.</span></span>

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="9c975-136">Określa jeden lub kilka [manifestów docelowych,](../deploying/runtime-store.md) które mają być używane do przycinania zestawu pakietów opublikowanych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9c975-136">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="9c975-137">Plik manifestu jest częścią danych [ `dotnet store` ](dotnet-store.md)wyjściowych polecenia .</span><span class="sxs-lookup"><span data-stu-id="9c975-137">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="9c975-138">Aby określić wiele manifestów, dodaj `--manifest` opcję dla każdego manifestu.</span><span class="sxs-lookup"><span data-stu-id="9c975-138">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span>

- **`--no-build`**

  <span data-ttu-id="9c975-139">Nie tworzy projektu przed opublikowaniem.</span><span class="sxs-lookup"><span data-stu-id="9c975-139">Doesn't build the project before publishing.</span></span> <span data-ttu-id="9c975-140">To również niejawnie ustawia `--no-restore` flagę.</span><span class="sxs-lookup"><span data-stu-id="9c975-140">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="9c975-141">Ignoruje odwołania projektu do projektu i przywraca tylko projekt główny.</span><span class="sxs-lookup"><span data-stu-id="9c975-141">Ignores project-to-project references and only restores the root project.</span></span>

- **`--nologo`**

  <span data-ttu-id="9c975-142">Nie wyświetla banera startowego ani wiadomości o prawach autorskich.</span><span class="sxs-lookup"><span data-stu-id="9c975-142">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="9c975-143">Dostępne od sdk .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="9c975-143">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="9c975-144">Nie wykonuje przywracania niejawnego podczas uruchamiania polecenia.</span><span class="sxs-lookup"><span data-stu-id="9c975-144">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="9c975-145">Określa ścieżkę katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="9c975-145">Specifies the path for the output directory.</span></span> <span data-ttu-id="9c975-146">Jeśli nie zostanie określony, domyślnie *./bin/[configuration]/[framework]/publish/* dla plików insynualnych zależnych od czasu wykonywania i plików binarnych między platformami.</span><span class="sxs-lookup"><span data-stu-id="9c975-146">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a runtime-dependent executable and cross-platform binaries.</span></span> <span data-ttu-id="9c975-147">Domyślnie *./bin/[configuration]/[framework]/[runtime]/publish/* dla samodzielnego pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="9c975-147">It defaults to *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained executable.</span></span>

  <span data-ttu-id="9c975-148">Jeśli ścieżka jest względna, wygenerowany katalog wyjściowy jest względem lokalizacji pliku projektu, a nie bieżącego katalogu roboczego.</span><span class="sxs-lookup"><span data-stu-id="9c975-148">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

- **`--self-contained [true|false]`**

  <span data-ttu-id="9c975-149">Publikuje program .NET Core w aplikacji, dzięki czemu czas wykonywania nie musi być zainstalowany na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="9c975-149">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="9c975-150">Domyślnie `true` jest, jeśli określono identyfikator czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9c975-150">Default is `true` if a runtime identifier is specified.</span></span> <span data-ttu-id="9c975-151">Aby uzyskać więcej informacji, zobacz [publikowanie](../deploying/index.md) i [publikowanie aplikacji .NET Core w aplikacji .NET Core za pomocą interfejsu wiersza wiersza wiersza wiersza wiersza .NET Core](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="9c975-151">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`--no-self-contained`**

  <span data-ttu-id="9c975-152">Odpowiednik `--self-contained false`.</span><span class="sxs-lookup"><span data-stu-id="9c975-152">Equivalent to `--self-contained false`.</span></span> <span data-ttu-id="9c975-153">Dostępne od sdk .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="9c975-153">Available since .NET Core 3.0 SDK.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="9c975-154">Publikuje aplikację dla danego czasu uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="9c975-154">Publishes the application for a given runtime.</span></span> <span data-ttu-id="9c975-155">Aby uzyskać listę identyfikatorów runtime (RID), zobacz [katalog RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="9c975-155">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="9c975-156">Aby uzyskać więcej informacji, zobacz [publikowanie](../deploying/index.md) i [publikowanie aplikacji .NET Core w aplikacji .NET Core za pomocą interfejsu wiersza wiersza wiersza wiersza wiersza .NET Core](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="9c975-156">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="9c975-157">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="9c975-157">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9c975-158">Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i .</span><span class="sxs-lookup"><span data-stu-id="9c975-158">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="9c975-159">Wartością `minimal`domyślną jest .</span><span class="sxs-lookup"><span data-stu-id="9c975-159">Default value is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="9c975-160">Definiuje sufiks wersji, aby zastąpić`*`gwiazdkę ( ) w polu wersji pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="9c975-160">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

## <a name="examples"></a><span data-ttu-id="9c975-161">Przykłady</span><span class="sxs-lookup"><span data-stu-id="9c975-161">Examples</span></span>

- <span data-ttu-id="9c975-162">Utwórz [plik binarny zależny między platformami](../deploying/index.md#produce-a-cross-platform-binary) dla projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="9c975-162">Create a [runtime-dependent cross-platform binary](../deploying/index.md#produce-a-cross-platform-binary) for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet publish
  ```

  <span data-ttu-id="9c975-163">Począwszy od .NET Core 3.0 SDK, w tym przykładzie tworzy również [plik wykonywalny zależny od czasu wykonywania](../deploying/index.md#publish-runtime-dependent) dla bieżącej platformy.</span><span class="sxs-lookup"><span data-stu-id="9c975-163">Starting with .NET Core 3.0 SDK, this example also creates a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the current platform.</span></span>

- <span data-ttu-id="9c975-164">Utwórz [samodzielny plik wykonywalny](../deploying/index.md#publish-self-contained) dla projektu w bieżącym katalogu dla określonego czasu wykonawczego:</span><span class="sxs-lookup"><span data-stu-id="9c975-164">Create a [self-contained executable](../deploying/index.md#publish-self-contained) for the project in the current directory, for a specific runtime:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  <span data-ttu-id="9c975-165">Rid musi znajdować się w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="9c975-165">The RID must be in the project file.</span></span>

- <span data-ttu-id="9c975-166">Utwórz [plik wykonywalny zależny od czasu wykonywania](../deploying/index.md#publish-runtime-dependent) dla projektu w bieżącym katalogu dla określonej platformy:</span><span class="sxs-lookup"><span data-stu-id="9c975-166">Create a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the project in the current directory, for a specific platform:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  <span data-ttu-id="9c975-167">Rid musi znajdować się w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="9c975-167">The RID must be in the project file.</span></span> <span data-ttu-id="9c975-168">W tym przykładzie dotyczy .NET Core 3.0 SDK i nowszych wersji.</span><span class="sxs-lookup"><span data-stu-id="9c975-168">This example applies to .NET Core 3.0 SDK and later versions.</span></span>

- <span data-ttu-id="9c975-169">Opublikuj projekt w bieżącym katalogu dla określonej struktury wykonywania i docelowej:</span><span class="sxs-lookup"><span data-stu-id="9c975-169">Publish the project in the current directory, for a specific runtime and target framework:</span></span>

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- <span data-ttu-id="9c975-170">Opublikuj określony plik projektu:</span><span class="sxs-lookup"><span data-stu-id="9c975-170">Publish the specified project file:</span></span>

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="9c975-171">Opublikuj bieżącą aplikację, ale nie przywracaj odwołań projektu do projektu (P2P), tylko projekt główny podczas operacji przywracania:</span><span class="sxs-lookup"><span data-stu-id="9c975-171">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation:</span></span>

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a><span data-ttu-id="9c975-172">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c975-172">See also</span></span>

- [<span data-ttu-id="9c975-173">Omówienie publikowania aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="9c975-173">.NET Core application publishing overview</span></span>](../deploying/index.md)
- [<span data-ttu-id="9c975-174">Publikowanie aplikacji .NET Core za pomocą wiersza wiersza wiersza wiersza wiersza .NET Core</span><span class="sxs-lookup"><span data-stu-id="9c975-174">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="9c975-175">Platformy docelowe</span><span class="sxs-lookup"><span data-stu-id="9c975-175">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="9c975-176">Katalog identyfikatora środowiska uruchomienigo (RID)</span><span class="sxs-lookup"><span data-stu-id="9c975-176">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- <span data-ttu-id="9c975-177">[Praca z systemem macOS Catalina Notariacja](../install/macos-notarization-issues.md) Aby uzyskać więcej informacji, zobacz on następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="9c975-177">[Working with macOS Catalina Notarization](../install/macos-notarization-issues.md) For more information, see he following resources:</span></span>
- [<span data-ttu-id="9c975-178">Struktura katalogów opublikowanej aplikacji</span><span class="sxs-lookup"><span data-stu-id="9c975-178">Directory structure of a published application</span></span>](/aspnet/core/hosting/directory-structure)
