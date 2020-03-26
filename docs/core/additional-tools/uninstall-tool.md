---
title: Narzędzie do odinstalowywania
description: Omówienie narzędzia do odinstalowywania rdzenia .NET, narzędzia z przewodnikiem, które umożliwia kontrolowane oczyszczanie zestawów SDK i środowiskach uruchomieniowych .NET Core.
author: sfoslund
ms.date: 01/06/2020
ms.openlocfilehash: 816aef6ab8bc0e51bb8befb14fde60513d4fadfc
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507324"
---
# <a name="net-core-uninstall-tool"></a><span data-ttu-id="685b6-103">Narzędzie do dezinstalacji platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="685b6-103">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="685b6-104">[Narzędzie .NET Core Uninstall Tool](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) umożliwia usunięcie zestawów SDK i runtimes .NET Core z systemu.</span><span class="sxs-lookup"><span data-stu-id="685b6-104">The [.NET Core Uninstall Tool](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and Runtimes from a system.</span></span> <span data-ttu-id="685b6-105">Dostępna jest kolekcja opcji określających, które wersje chcesz odinstalować.</span><span class="sxs-lookup"><span data-stu-id="685b6-105">A collection of options is available to specify which versions you want to uninstall.</span></span>

<span data-ttu-id="685b6-106">Narzędzie obsługuje systemy Windows i macOS.</span><span class="sxs-lookup"><span data-stu-id="685b6-106">The tool supports Windows and macOS.</span></span> <span data-ttu-id="685b6-107">Linux nie jest obecnie obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="685b6-107">Linux is currently not supported.</span></span>

<span data-ttu-id="685b6-108">W systemie Windows narzędzie może odinstalować tylko zestawy SDK i środowiska wykonawcze zainstalowane przy użyciu jednego z następujących instalatorów:</span><span class="sxs-lookup"><span data-stu-id="685b6-108">On Windows, the tool can only uninstall SDKs and Runtimes that were installed using one of the following installers:</span></span>

- <span data-ttu-id="685b6-109">Instalator .NET Core SDK i runtime.</span><span class="sxs-lookup"><span data-stu-id="685b6-109">The .NET Core SDK and runtime installer.</span></span>
- <span data-ttu-id="685b6-110">Instalator programu Visual Studio w wersjach wcześniejszych niż Visual Studio 2019 w wersji 16.3.</span><span class="sxs-lookup"><span data-stu-id="685b6-110">The Visual Studio installer in versions earlier than Visual Studio 2019 version 16.3.</span></span>

<span data-ttu-id="685b6-111">W systemie macOS narzędzie może odinstalowywać tylko zestawy SDK i środowiska wykonawcze znajdujące się w folderze */usr/local/share/dotnet.*</span><span class="sxs-lookup"><span data-stu-id="685b6-111">On macOS, the tool can only uninstall SDKs and runtimes located in the */usr/local/share/dotnet* folder.</span></span>

<span data-ttu-id="685b6-112">Z powodu tych ograniczeń narzędzie może nie być w stanie odinstalować wszystkich zestawów SDK core platformy .NET i środowiskach uruchomieniowych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="685b6-112">Because of these limitations, the tool may not be able to uninstall all of the .NET Core SDKs and runtimes on your machine.</span></span> <span data-ttu-id="685b6-113">Za pomocą `dotnet --info` polecenia można znaleźć wszystkie zestawy SDK rdzenia .NET i zainstalowane środowiska wykonawcze, w tym zestawy SDK i środowiska wykonawcze, których to narzędzie nie może usunąć.</span><span class="sxs-lookup"><span data-stu-id="685b6-113">You can use the `dotnet --info` command to find all of the .NET Core SDKs and runtimes installed, including those SDKs and runtimes that this tool can't remove.</span></span> <span data-ttu-id="685b6-114">Polecenie `dotnet-core-uninstall list` wyświetla, które zestawy SDK można odinstalować za pomocą narzędzia.</span><span class="sxs-lookup"><span data-stu-id="685b6-114">The `dotnet-core-uninstall list` command displays which SDKs can be uninstalled with the tool.</span></span>

## <a name="install-the-tool"></a><span data-ttu-id="685b6-115">Zainstaluj narzędzie</span><span class="sxs-lookup"><span data-stu-id="685b6-115">Install the tool</span></span>

<span data-ttu-id="685b6-116">Możesz pobrać narzędzie .NET Core Uninstall [Tool stąd](https://aka.ms/dotnet-core-uninstall-tool) i znaleźć kod źródłowy w repozytorium GitHub [dotnet/cli-lab.](https://github.com/dotnet/cli-lab)</span><span class="sxs-lookup"><span data-stu-id="685b6-116">You can download the .NET Core Uninstall Tool from [here](https://aka.ms/dotnet-core-uninstall-tool) and find the source code at the [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub repository.</span></span>

> [!NOTE]
> <span data-ttu-id="685b6-117">Narzędzie wymaga podniesienia uprawnień do odinstalowywania zestawów SDK core platformy .NET i środowiskach uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="685b6-117">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="685b6-118">W związku z tym powinien być zainstalowany w katalogu chronionym przed zapisem, takich jak *C:\Program Files* w systemie Windows lub */usr/local/bin* w systemie macOS.</span><span class="sxs-lookup"><span data-stu-id="685b6-118">Therefore, it should be installed in a write-protected directory such as *C:\Program Files* on Windows or */usr/local/bin* on macOS.</span></span> <span data-ttu-id="685b6-119">Zobacz też [Podwyższony dostęp do poleceń dotnet .](../tools/elevated-access.md)</span><span class="sxs-lookup"><span data-stu-id="685b6-119">See also [Elevated access for dotnet commands](../tools/elevated-access.md).</span></span> <span data-ttu-id="685b6-120">Aby uzyskać więcej informacji, zobacz [szczegółowe instrukcje instalacji](https://aka.ms/dotnet-core-uninstall-tool).</span><span class="sxs-lookup"><span data-stu-id="685b6-120">For more information, see the [detailed installation instructions](https://aka.ms/dotnet-core-uninstall-tool).</span></span>

## <a name="run-the-tool"></a><span data-ttu-id="685b6-121">Uruchamianie narzędzia</span><span class="sxs-lookup"><span data-stu-id="685b6-121">Run the tool</span></span>

<span data-ttu-id="685b6-122">W poniższych krokach przedstawiono zalecane podejście do uruchamiania narzędzia do odinstalowywania:</span><span class="sxs-lookup"><span data-stu-id="685b6-122">The following steps show the recommended approach for running the uninstall tool:</span></span>

- [<span data-ttu-id="685b6-123">Krok 1 - Wyświetlanie zainstalowanych pakietów SDK core .NET i środowiskach uruchomieniowych</span><span class="sxs-lookup"><span data-stu-id="685b6-123">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>](#step-1---display-installed-net-core-sdks-and-runtimes)
- [<span data-ttu-id="685b6-124">Krok 2 - Wykonaj suchą serię</span><span class="sxs-lookup"><span data-stu-id="685b6-124">Step 2 - Do a dry run</span></span>](#step-2---do-a-dry-run)
- [<span data-ttu-id="685b6-125">Krok 3 - Odinstalowywanie podstawowych pakietów SDK i runtimes .NET</span><span class="sxs-lookup"><span data-stu-id="685b6-125">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>](#step-3---uninstall-net-core-sdks-and-runtimes)
- [<span data-ttu-id="685b6-126">Krok 4 - Usuń folder rezerwowy NuGet (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="685b6-126">Step 4 - Delete the NuGet fallback folder (optional)</span></span>](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a><span data-ttu-id="685b6-127">Krok 1 - Wyświetlanie zainstalowanych pakietów SDK core .NET i środowiskach uruchomieniowych</span><span class="sxs-lookup"><span data-stu-id="685b6-127">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>

<span data-ttu-id="685b6-128">Polecenie `dotnet-core-uninstall list` zawiera listę zainstalowanych zestawów SDK rdzenia .NET i środowiskach uruchomieniowych, które można usunąć za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="685b6-128">The `dotnet-core-uninstall list` command lists the installed .NET Core SDKs and runtimes that can be removed with this tool.</span></span> <span data-ttu-id="685b6-129">Niektóre pakiety SDK i środowiska wykonawcze mogą być wymagane przez program Visual Studio i są wyświetlane z notatką, dlaczego nie jest zalecane, aby je odinstalować.</span><span class="sxs-lookup"><span data-stu-id="685b6-129">Some SDKs and runtimes may be required by Visual Studio and they're displayed with a note of why it isn't recommended to uninstall them.</span></span>

> [!NOTE]
> <span data-ttu-id="685b6-130">Dane wyjściowe `dotnet-core-uninstall list` polecenia nie będą zgodne z listą `dotnet --info` zainstalowanych wersji w danych wyjściowych w większości przypadków.</span><span class="sxs-lookup"><span data-stu-id="685b6-130">The output of the `dotnet-core-uninstall list` command will not match the list of installed versions in the output of `dotnet --info` in most cases.</span></span> <span data-ttu-id="685b6-131">W szczególności to narzędzie nie będzie wyświetlać wersje zainstalowane przez pliki zip lub zarządzane przez program Visual Studio (dowolna wersja zainstalowana z programem Visual Studio 2019 16.3 lub nowszym).</span><span class="sxs-lookup"><span data-stu-id="685b6-131">Specifically, this tool will not display versions installed by zip files or managed by Visual Studio (any version installed with Visual Studio 2019 16.3 or later).</span></span> <span data-ttu-id="685b6-132">Jednym ze sposobów sprawdzenia, czy wersja jest zarządzana `Add or Remove Programs`przez program Visual Studio, jest wyświetlenie jej w programie , gdzie wersje zarządzane programu Visual Studio są oznaczone jako takie w ich nazwach wyświetlanych.</span><span class="sxs-lookup"><span data-stu-id="685b6-132">One way to check if a version is managed by Visual Studio is to view it in `Add or Remove Programs`, where Visual Studio managed versions are marked as such in their display names.</span></span>

<span data-ttu-id="685b6-133">**lista dotnet-core-uninstall**</span><span class="sxs-lookup"><span data-stu-id="685b6-133">**dotnet-core-uninstall list**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="685b6-134">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="685b6-134">Synopsis</span></span>

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a><span data-ttu-id="685b6-135">Opcje</span><span class="sxs-lookup"><span data-stu-id="685b6-135">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="685b6-136">Windows</span><span class="sxs-lookup"><span data-stu-id="685b6-136">Windows</span></span>](#tab/windows)

* **`--aspnet-runtime`**

  <span data-ttu-id="685b6-137">Wyświetla listę wszystkich ASP.NET core runtimes, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="685b6-137">Lists all the ASP.NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="685b6-138">Wyświetla listę wszystkich pakietów uruchomieniowych i hostingowych .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="685b6-138">Lists all the .NET Core runtime and hosting bundles that can be uninstalled with this tool.</span></span>

* **`--runtime`**

  <span data-ttu-id="685b6-139">Wyświetla listę wszystkich przepływów .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="685b6-139">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="685b6-140">Wyświetla listę wszystkich zestawów SDK .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="685b6-140">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="685b6-141">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="685b6-141">Sets the verbosity level.</span></span> <span data-ttu-id="685b6-142">Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i .</span><span class="sxs-lookup"><span data-stu-id="685b6-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="685b6-143">Wartością domyślną jest `normal`.</span><span class="sxs-lookup"><span data-stu-id="685b6-143">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="685b6-144">Wyświetla listę wszystkich zestawów SDK rdzenia x64 .NET i środowiskach uruchomieniowych, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="685b6-144">Lists all x64 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

* **`--x86`**

  <span data-ttu-id="685b6-145">Wyświetla listę wszystkich zestawów SDK rdzenia x86 .NET i środowiskach uruchomieniowych, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="685b6-145">Lists all x86 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

## <a name="macos"></a>[<span data-ttu-id="685b6-146">Macos</span><span class="sxs-lookup"><span data-stu-id="685b6-146">macOS</span></span>](#tab/macos)

* **`--runtime`**

  <span data-ttu-id="685b6-147">Wyświetla listę wszystkich przepływów .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="685b6-147">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="685b6-148">Wyświetla listę wszystkich zestawów SDK .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="685b6-148">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="685b6-149">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="685b6-149">Sets the verbosity level.</span></span> <span data-ttu-id="685b6-150">Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i .</span><span class="sxs-lookup"><span data-stu-id="685b6-150">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="685b6-151">Wartością domyślną jest `normal`.</span><span class="sxs-lookup"><span data-stu-id="685b6-151">The default value is `normal`.</span></span>
  
---

#### <a name="examples"></a><span data-ttu-id="685b6-152">Przykłady</span><span class="sxs-lookup"><span data-stu-id="685b6-152">Examples</span></span>

* <span data-ttu-id="685b6-153">Wyświetl listę wszystkich zestawów SDK core platformy .NET i środowiskach uruchomieniowych, które można usunąć za pomocą tego narzędzia:</span><span class="sxs-lookup"><span data-stu-id="685b6-153">List all .NET Core SDKs and runtimes that can be removed with this tool:</span></span>

  ```console
  dotnet-core-uninstall list
  ```

* <span data-ttu-id="685b6-154">Wyświetl listę wszystkich podstawowych sdk x64 .NET i środowiskach uruchomieniowych:</span><span class="sxs-lookup"><span data-stu-id="685b6-154">List all x64 .NET Core SDKs and runtimes:</span></span>

  ```console
  dotnet-core-uninstall list --x64
  ```

* <span data-ttu-id="685b6-155">Wyświetl listę wszystkich podstawowych sdk x86 .NET:</span><span class="sxs-lookup"><span data-stu-id="685b6-155">List all x86 .NET Core SDKs:</span></span>

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a><span data-ttu-id="685b6-156">Krok 2 - Wykonaj suchą serię</span><span class="sxs-lookup"><span data-stu-id="685b6-156">Step 2 - Do a dry run</span></span>

<span data-ttu-id="685b6-157">Polecenia `dotnet-core-uninstall dry-run` `dotnet-core-uninstall whatif` i wyświetlają pakiety SDK rdzenia .NET i środowiska wykonawcze, które zostaną usunięte na podstawie dostępnych opcji bez odinstalowywania.</span><span class="sxs-lookup"><span data-stu-id="685b6-157">The `dotnet-core-uninstall dry-run` and `dotnet-core-uninstall whatif` commands display the .NET Core SDKs and runtimes that will be removed based on the options provided without performing the uninstall.</span></span> <span data-ttu-id="685b6-158">Polecenia te są synonimami.</span><span class="sxs-lookup"><span data-stu-id="685b6-158">These commands are synonyms.</span></span>

<span data-ttu-id="685b6-159">**dotnet-core-uninstall dry-run i dotnet-core-uninstall whatif**</span><span class="sxs-lookup"><span data-stu-id="685b6-159">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="685b6-160">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="685b6-160">Synopsis</span></span>

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="685b6-161">Argumenty</span><span class="sxs-lookup"><span data-stu-id="685b6-161">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="685b6-162">Określona wersja do odinstalowania.</span><span class="sxs-lookup"><span data-stu-id="685b6-162">The specified version to uninstall.</span></span> <span data-ttu-id="685b6-163">Można wyświetlić kilka wersji jeden po drugim, oddzielone spacjami.</span><span class="sxs-lookup"><span data-stu-id="685b6-163">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="685b6-164">Obsługiwane są również pliki odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="685b6-164">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="685b6-165">Pliki odpowiedzi są alternatywą dla umieszczania wszystkich wersji w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="685b6-165">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="685b6-166">Są to pliki tekstowe, \*zazwyczaj z rozszerzeniem .rsp, a każda wersja jest wyświetlana w osobnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="685b6-166">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="685b6-167">Aby określić plik `VERSION` odpowiedzi dla \@ argumentu, należy użyć znaku natychmiast po nazwie pliku odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="685b6-167">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="685b6-168">Opcje</span><span class="sxs-lookup"><span data-stu-id="685b6-168">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="685b6-169">Windows</span><span class="sxs-lookup"><span data-stu-id="685b6-169">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="685b6-170">Usuwa wszystkie podstawowe sdk .NET i środowiska wykonawcze.</span><span class="sxs-lookup"><span data-stu-id="685b6-170">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="685b6-171">Usuwa tylko .NET Core SDK i runtimes z wersją mniejszą niż określona wersja.</span><span class="sxs-lookup"><span data-stu-id="685b6-171">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="685b6-172">Określona wersja pozostaje zainstalowana.</span><span class="sxs-lookup"><span data-stu-id="685b6-172">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="685b6-173">Usuwa wszystkie.NET Core SDKs i runtimes, z wyjątkiem tych wersji określonych.</span><span class="sxs-lookup"><span data-stu-id="685b6-173">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="685b6-174">Usuwa .NET Core SDK i runtimes, z wyjątkiem jednej najwyższej wersji.</span><span class="sxs-lookup"><span data-stu-id="685b6-174">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="685b6-175">Usuwa .NET Core SDK i runtimes zastąpione przez wyższe poprawki.</span><span class="sxs-lookup"><span data-stu-id="685b6-175">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="685b6-176">Ta opcja chroni global.json.</span><span class="sxs-lookup"><span data-stu-id="685b6-176">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="685b6-177">Usuwa .NET Core SDK i środowiska wykonawcze oznaczone jako podglądy.</span><span class="sxs-lookup"><span data-stu-id="685b6-177">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="685b6-178">Usuwa .NET Core SDK i runtimes oznaczone jako podglądy z wyjątkiem jednego najwyższego podglądu.</span><span class="sxs-lookup"><span data-stu-id="685b6-178">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="685b6-179">Usuwa tylko ASP.NET podstawowe środowiska wykonawcze.</span><span class="sxs-lookup"><span data-stu-id="685b6-179">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="685b6-180">Usuwa tylko środowisko uruchomieniowe i pakiety hostingu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="685b6-180">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="685b6-181">Usuwa .NET Core SDKs i runtimes, które pasują do określonej `major.minor` wersji.</span><span class="sxs-lookup"><span data-stu-id="685b6-181">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="685b6-182">Usuwa tylko środowiska uruchomieniowe .NET Core.</span><span class="sxs-lookup"><span data-stu-id="685b6-182">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="685b6-183">Usuwa tylko podstawowe sdk .NET.</span><span class="sxs-lookup"><span data-stu-id="685b6-183">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="685b6-184">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="685b6-184">Sets the verbosity level.</span></span> <span data-ttu-id="685b6-185">Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i .</span><span class="sxs-lookup"><span data-stu-id="685b6-185">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="685b6-186">Wartością domyślną jest `normal`.</span><span class="sxs-lookup"><span data-stu-id="685b6-186">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="685b6-187">Musi być `--sdk`używany `--runtime`z `--aspnet-runtime` , i usunąć x64 SDK lub runtimes.</span><span class="sxs-lookup"><span data-stu-id="685b6-187">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="685b6-188">Musi być `--sdk`używany `--runtime`z `--aspnet-runtime` , i usunąć x86 SDK lub runtimes.</span><span class="sxs-lookup"><span data-stu-id="685b6-188">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="685b6-189">**`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="685b6-189">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="685b6-190">Uwagi:</span><span class="sxs-lookup"><span data-stu-id="685b6-190">Notes:</span></span>

1. <span data-ttu-id="685b6-191">Dokładnie jeden `--sdk`z `--runtime` `--aspnet-runtime`, `--hosting-bundle` , i jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="685b6-191">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="685b6-192">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , i są wyłączne.</span><span class="sxs-lookup"><span data-stu-id="685b6-192">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="685b6-193">Jeśli `--x64` `--x86` lub nie są określone, a następnie x64 i x86 zostaną usunięte.</span><span class="sxs-lookup"><span data-stu-id="685b6-193">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="685b6-194">Macos</span><span class="sxs-lookup"><span data-stu-id="685b6-194">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="685b6-195">Usuwa wszystkie podstawowe sdk .NET i środowiska wykonawcze.</span><span class="sxs-lookup"><span data-stu-id="685b6-195">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="685b6-196">Usuwa .NET Core SDK i środowiska wykonawcze poniżej określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="685b6-196">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="685b6-197">Określona wersja pozostanie.</span><span class="sxs-lookup"><span data-stu-id="685b6-197">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="685b6-198">Usuwa .NET Core SDKs i runtimes, z wyjątkiem tych wersji określonych.</span><span class="sxs-lookup"><span data-stu-id="685b6-198">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="685b6-199">Usuwa .NET Core SDK i runtimes, z wyjątkiem jednej najwyższej wersji.</span><span class="sxs-lookup"><span data-stu-id="685b6-199">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="685b6-200">Usuwa .NET Core SDK i runtimes zastąpione przez wyższe poprawki.</span><span class="sxs-lookup"><span data-stu-id="685b6-200">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="685b6-201">Ta opcja chroni global.json.</span><span class="sxs-lookup"><span data-stu-id="685b6-201">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="685b6-202">Usuwa .NET Core SDK i środowiska wykonawcze oznaczone jako podglądy.</span><span class="sxs-lookup"><span data-stu-id="685b6-202">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="685b6-203">Usuwa .NET Core SDK i runtimes oznaczone jako podglądy z wyjątkiem jednego najwyższego podglądu.</span><span class="sxs-lookup"><span data-stu-id="685b6-203">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="685b6-204">Usuwa .NET Core SDKs i runtimes, które pasują do określonej `major.minor` wersji.</span><span class="sxs-lookup"><span data-stu-id="685b6-204">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="685b6-205">Usuwa tylko środowiska uruchomieniowe .NET Core.</span><span class="sxs-lookup"><span data-stu-id="685b6-205">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="685b6-206">Usuwa tylko podstawowe sdk .NET.</span><span class="sxs-lookup"><span data-stu-id="685b6-206">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="685b6-207">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="685b6-207">Sets the verbosity level.</span></span> <span data-ttu-id="685b6-208">Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i .</span><span class="sxs-lookup"><span data-stu-id="685b6-208">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="685b6-209">Wartością domyślną jest `normal`.</span><span class="sxs-lookup"><span data-stu-id="685b6-209">The default value is `normal`.</span></span>
  
* <span data-ttu-id="685b6-210">**`--force`** Wymusza usunięcie wersji, które mogą być używane przez visual studio lub SDK.</span><span class="sxs-lookup"><span data-stu-id="685b6-210">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="685b6-211">Uwagi:</span><span class="sxs-lookup"><span data-stu-id="685b6-211">Notes:</span></span>

1. <span data-ttu-id="685b6-212">Dokładnie jeden `--sdk` z `--runtime` i jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="685b6-212">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="685b6-213">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , i są wyłączne.</span><span class="sxs-lookup"><span data-stu-id="685b6-213">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="685b6-214">Przykłady</span><span class="sxs-lookup"><span data-stu-id="685b6-214">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="685b6-215">Domyślnie.NET Core SDKs i runtimes, które mogą być wymagane przez visual studio `dotnet-core-uninstall dry-run` lub inne sdk nie są uwzględniane w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="685b6-215">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are not included in `dotnet-core-uninstall dry-run` output.</span></span> <span data-ttu-id="685b6-216">W poniższych przykładach niektóre z określonych sks i runtimes nie mogą być uwzględnione w danych wyjściowych, w zależności od stanu komputera.</span><span class="sxs-lookup"><span data-stu-id="685b6-216">In the following examples, some of the specified SDKs and runtimes may not be included in the output, depending on the state of the machine.</span></span> <span data-ttu-id="685b6-217">Aby uwzględnić wszystkie zestawy SDK i środowiska wykonawcze, `--force` wymień je jawnie jako argumenty lub użyj tej opcji.</span><span class="sxs-lookup"><span data-stu-id="685b6-217">To include all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="685b6-218">Dry run usuwania wszystkich .NET Core runtimes, które zostały zastąpione przez wyższe poprawki:</span><span class="sxs-lookup"><span data-stu-id="685b6-218">Dry run of removing all .NET Core runtimes that have been superseded by higher patches:</span></span>

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* <span data-ttu-id="685b6-219">Suchy bieg usuwania wszystkich .NET Core SDK poniżej wersji: `2.2.301`</span><span class="sxs-lookup"><span data-stu-id="685b6-219">Dry run of removing all .NET Core SDKs below the version `2.2.301`:</span></span>

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a><span data-ttu-id="685b6-220">Krok 3 - Odinstalowywanie podstawowych pakietów SDK i runtimes .NET</span><span class="sxs-lookup"><span data-stu-id="685b6-220">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>

<span data-ttu-id="685b6-221">`dotnet-core-uninstall remove`odinstalowuje pakiety .NET Core SDK i Runtimes, które są określone przez kolekcję opcji.</span><span class="sxs-lookup"><span data-stu-id="685b6-221">`dotnet-core-uninstall remove` uninstalls .NET Core SDKs and Runtimes that are specified by a collection of options.</span></span> <span data-ttu-id="685b6-222">Narzędzia nie można odinstalować zestawów SDK i Runtimes w wersji 5.0 lub wyższej.</span><span class="sxs-lookup"><span data-stu-id="685b6-222">The tool can't be used to uninstall SDKs and Runtimes with version 5.0 or above.</span></span>

<span data-ttu-id="685b6-223">Ponieważ to narzędzie ma destrukcyjne zachowanie, **zaleca** się wykonanie przebiegu na sucho przed uruchomieniem polecenia remove.</span><span class="sxs-lookup"><span data-stu-id="685b6-223">Since this tool has a destructive behavior, it's **highly** recommended that you do a dry run before running the remove command.</span></span> <span data-ttu-id="685b6-224">Dry run pokaże, co .NET Core SDKs i środowiska wykonawcze `remove` zostaną usunięte podczas korzystania z polecenia.</span><span class="sxs-lookup"><span data-stu-id="685b6-224">The dry run will show you what .NET Core SDKs and runtimes will be removed when you use the `remove` command.</span></span> <span data-ttu-id="685b6-225">Zapoznaj się z [należy usunąć wersję?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version)</span><span class="sxs-lookup"><span data-stu-id="685b6-225">Refer to [Should I remove a version?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version) to learn which SDKs and runtimes are safe to remove.</span></span>

> [!CAUTION]
> <span data-ttu-id="685b6-226">Należy pamiętać o następujących zastrzeżeniach:</span><span class="sxs-lookup"><span data-stu-id="685b6-226">Keep in mind the following caveats:</span></span>
>
>- <span data-ttu-id="685b6-227">To narzędzie może odinstalować wersje zestawu .NET Core `global.json` SDK, które są wymagane przez pliki na komputerze.</span><span class="sxs-lookup"><span data-stu-id="685b6-227">This tool can uninstall versions of the .NET Core SDK that are required by `global.json` files on your machine.</span></span> <span data-ttu-id="685b6-228">Można ponownie zainstalować pliki SDK .NET Core ze strony [Pobierz .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)</span><span class="sxs-lookup"><span data-stu-id="685b6-228">You can reinstall .NET Core SDKs from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="685b6-229">To narzędzie można odinstalować wersje środowiska uruchomieniowego .NET Core, które są wymagane przez aplikacje zależne od struktury na komputerze.</span><span class="sxs-lookup"><span data-stu-id="685b6-229">This tool can uninstall versions of the .NET Core runtime that are required by framework dependent applications on your machine.</span></span> <span data-ttu-id="685b6-230">Można ponownie zainstalować środowiska uruchomieniowe .NET Core ze strony [Pobierz .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)</span><span class="sxs-lookup"><span data-stu-id="685b6-230">You can reinstall .NET Core runtimes from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="685b6-231">To narzędzie może odinstalować wersje zestawu .NET Core SDK i środowiska wykonawczego, na których opiera się program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="685b6-231">This tool can uninstall versions of the .NET Core SDK and runtime that Visual Studio relies on.</span></span> <span data-ttu-id="685b6-232">Jeśli przerwać instalację programu Visual Studio, uruchom "Napraw" w instalatorze programu Visual Studio, aby wrócić do stanu roboczego.</span><span class="sxs-lookup"><span data-stu-id="685b6-232">If you break your Visual Studio installation, run "Repair" in the Visual Studio installer to get back to a working state.</span></span>

<span data-ttu-id="685b6-233">Domyślnie wszystkie polecenia zachowują .NET Core SDKs i runtimes, które mogą być wymagane przez visual studio lub innych SDK.</span><span class="sxs-lookup"><span data-stu-id="685b6-233">By default, all commands keep the .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs.</span></span> <span data-ttu-id="685b6-234">Te zestawy SDK i środowiska wykonawcze można odinstalować, wymieniając `--force` je jawnie jako argumenty lub używając tej opcji.</span><span class="sxs-lookup"><span data-stu-id="685b6-234">These SDKs and runtimes can be uninstalled by listing them explicitly as arguments or by using the `--force` option.</span></span>

<span data-ttu-id="685b6-235">Narzędzie wymaga podniesienia uprawnień do odinstalowywania zestawów SDK core platformy .NET i środowiskach uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="685b6-235">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="685b6-236">Uruchom narzędzie w wierszu polecenia Administrator `sudo` w systemie Windows i w systemie macOS.</span><span class="sxs-lookup"><span data-stu-id="685b6-236">Run the tool in an Administrator command prompt on Windows and with `sudo` on macOS.</span></span> <span data-ttu-id="685b6-237">Polecenia `dry-run` `whatif` i polecenia nie wymagają podniesienia uprawnień.</span><span class="sxs-lookup"><span data-stu-id="685b6-237">The `dry-run` and `whatif` commands don't require elevation.</span></span>

<span data-ttu-id="685b6-238">**dotnet-core-uninstall usunąć**</span><span class="sxs-lookup"><span data-stu-id="685b6-238">**dotnet-core-uninstall remove**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="685b6-239">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="685b6-239">Synopsis</span></span>

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="685b6-240">Argumenty</span><span class="sxs-lookup"><span data-stu-id="685b6-240">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="685b6-241">Określona wersja do odinstalowania.</span><span class="sxs-lookup"><span data-stu-id="685b6-241">The specified version to uninstall.</span></span> <span data-ttu-id="685b6-242">Można wyświetlić kilka wersji jeden po drugim, oddzielone spacjami.</span><span class="sxs-lookup"><span data-stu-id="685b6-242">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="685b6-243">Obsługiwane są również pliki odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="685b6-243">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="685b6-244">Pliki odpowiedzi są alternatywą dla umieszczania wszystkich wersji w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="685b6-244">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="685b6-245">Są to pliki tekstowe, \*zazwyczaj z rozszerzeniem .rsp, a każda wersja jest wyświetlana w osobnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="685b6-245">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="685b6-246">Aby określić plik `VERSION` odpowiedzi dla \@ argumentu, należy użyć znaku natychmiast po nazwie pliku odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="685b6-246">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="685b6-247">Opcje</span><span class="sxs-lookup"><span data-stu-id="685b6-247">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="685b6-248">Windows</span><span class="sxs-lookup"><span data-stu-id="685b6-248">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="685b6-249">Usuwa wszystkie podstawowe sdk .NET i środowiska wykonawcze.</span><span class="sxs-lookup"><span data-stu-id="685b6-249">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="685b6-250">Usuwa tylko .NET Core SDK i runtimes z wersją mniejszą niż określona wersja.</span><span class="sxs-lookup"><span data-stu-id="685b6-250">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="685b6-251">Określona wersja pozostaje zainstalowana.</span><span class="sxs-lookup"><span data-stu-id="685b6-251">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="685b6-252">Usuwa wszystkie.NET Core SDKs i runtimes, z wyjątkiem tych wersji określonych.</span><span class="sxs-lookup"><span data-stu-id="685b6-252">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="685b6-253">Usuwa .NET Core SDK i runtimes, z wyjątkiem jednej najwyższej wersji.</span><span class="sxs-lookup"><span data-stu-id="685b6-253">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="685b6-254">Usuwa .NET Core SDK i runtimes zastąpione przez wyższe poprawki.</span><span class="sxs-lookup"><span data-stu-id="685b6-254">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="685b6-255">Ta opcja chroni global.json.</span><span class="sxs-lookup"><span data-stu-id="685b6-255">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="685b6-256">Usuwa .NET Core SDK i środowiska wykonawcze oznaczone jako podglądy.</span><span class="sxs-lookup"><span data-stu-id="685b6-256">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="685b6-257">Usuwa .NET Core SDK i runtimes oznaczone jako podglądy z wyjątkiem jednego najwyższego podglądu.</span><span class="sxs-lookup"><span data-stu-id="685b6-257">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="685b6-258">Usuwa tylko ASP.NET podstawowe środowiska wykonawcze.</span><span class="sxs-lookup"><span data-stu-id="685b6-258">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="685b6-259">Usuwa tylko środowisko uruchomieniowe i pakiety hostingu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="685b6-259">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="685b6-260">Usuwa .NET Core SDKs i runtimes, które pasują do określonej `major.minor` wersji.</span><span class="sxs-lookup"><span data-stu-id="685b6-260">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="685b6-261">Usuwa tylko środowiska uruchomieniowe .NET Core.</span><span class="sxs-lookup"><span data-stu-id="685b6-261">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="685b6-262">Usuwa tylko podstawowe sdk .NET.</span><span class="sxs-lookup"><span data-stu-id="685b6-262">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="685b6-263">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="685b6-263">Sets the verbosity level.</span></span> <span data-ttu-id="685b6-264">Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i .</span><span class="sxs-lookup"><span data-stu-id="685b6-264">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="685b6-265">Wartością domyślną jest `normal`.</span><span class="sxs-lookup"><span data-stu-id="685b6-265">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="685b6-266">Musi być `--sdk`używany `--runtime`z `--aspnet-runtime` , i usunąć x64 SDK lub runtimes.</span><span class="sxs-lookup"><span data-stu-id="685b6-266">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="685b6-267">Musi być `--sdk`używany `--runtime`z `--aspnet-runtime` , i usunąć x86 SDK lub runtimes.</span><span class="sxs-lookup"><span data-stu-id="685b6-267">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="685b6-268">**`-y, --yes`** Wykonuje polecenie bez konieczności potwierdzenia tak lub nie.</span><span class="sxs-lookup"><span data-stu-id="685b6-268">**`-y, --yes`** Executes the command without requiring a yes or no confirmation.</span></span>

* <span data-ttu-id="685b6-269">**`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="685b6-269">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="685b6-270">Uwagi:</span><span class="sxs-lookup"><span data-stu-id="685b6-270">Notes:</span></span>

1. <span data-ttu-id="685b6-271">Dokładnie jeden `--sdk`z `--runtime` `--aspnet-runtime`, `--hosting-bundle` , i jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="685b6-271">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="685b6-272">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , i są wyłączne.</span><span class="sxs-lookup"><span data-stu-id="685b6-272">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="685b6-273">Jeśli `--x64` `--x86` lub nie są określone, a następnie x64 i x86 zostaną usunięte.</span><span class="sxs-lookup"><span data-stu-id="685b6-273">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="685b6-274">Macos</span><span class="sxs-lookup"><span data-stu-id="685b6-274">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="685b6-275">Usuwa wszystkie podstawowe sdk .NET i środowiska wykonawcze.</span><span class="sxs-lookup"><span data-stu-id="685b6-275">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="685b6-276">Usuwa .NET Core SDK i środowiska wykonawcze poniżej określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="685b6-276">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="685b6-277">Określona wersja pozostanie.</span><span class="sxs-lookup"><span data-stu-id="685b6-277">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="685b6-278">Usuwa .NET Core SDKs i runtimes, z wyjątkiem tych wersji określonych.</span><span class="sxs-lookup"><span data-stu-id="685b6-278">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="685b6-279">Usuwa .NET Core SDK i runtimes, z wyjątkiem jednej najwyższej wersji.</span><span class="sxs-lookup"><span data-stu-id="685b6-279">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="685b6-280">Usuwa .NET Core SDK i runtimes zastąpione przez wyższe poprawki.</span><span class="sxs-lookup"><span data-stu-id="685b6-280">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="685b6-281">Ta opcja chroni global.json.</span><span class="sxs-lookup"><span data-stu-id="685b6-281">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="685b6-282">Usuwa .NET Core SDK i środowiska wykonawcze oznaczone jako podglądy.</span><span class="sxs-lookup"><span data-stu-id="685b6-282">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="685b6-283">Usuwa .NET Core SDK i runtimes oznaczone jako podglądy z wyjątkiem jednego najwyższego podglądu.</span><span class="sxs-lookup"><span data-stu-id="685b6-283">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="685b6-284">Usuwa .NET Core SDKs i runtimes, które pasują do określonej `major.minor` wersji.</span><span class="sxs-lookup"><span data-stu-id="685b6-284">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="685b6-285">Usuwa tylko środowiska uruchomieniowe .NET Core.</span><span class="sxs-lookup"><span data-stu-id="685b6-285">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="685b6-286">Usuwa tylko podstawowe sdk .NET.</span><span class="sxs-lookup"><span data-stu-id="685b6-286">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="685b6-287">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="685b6-287">Sets the verbosity level.</span></span> <span data-ttu-id="685b6-288">Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i .</span><span class="sxs-lookup"><span data-stu-id="685b6-288">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="685b6-289">Wartością domyślną jest `normal`.</span><span class="sxs-lookup"><span data-stu-id="685b6-289">The default value is `normal`.</span></span>

* <span data-ttu-id="685b6-290">**`-y, --yes`** Wykonuje polecenie bez konieczności potwierdzania Y/N.</span><span class="sxs-lookup"><span data-stu-id="685b6-290">**`-y, --yes`** Executes the command without requiring Y/N confirmation.</span></span>
  
* <span data-ttu-id="685b6-291">**`--force`** Wymusza usunięcie wersji, które mogą być używane przez visual studio lub SDK.</span><span class="sxs-lookup"><span data-stu-id="685b6-291">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="685b6-292">Uwagi:</span><span class="sxs-lookup"><span data-stu-id="685b6-292">Notes:</span></span>

1. <span data-ttu-id="685b6-293">Dokładnie jeden `--sdk` z `--runtime` i jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="685b6-293">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="685b6-294">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , i są wyłączne.</span><span class="sxs-lookup"><span data-stu-id="685b6-294">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="685b6-295">Przykłady</span><span class="sxs-lookup"><span data-stu-id="685b6-295">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="685b6-296">Domyślnie.NET Core SDKs i runtimes, które mogą być wymagane przez visual studio lub inne SDK są przechowywane.</span><span class="sxs-lookup"><span data-stu-id="685b6-296">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are kept.</span></span> <span data-ttu-id="685b6-297">W poniższych przykładach niektóre z określonych sks i środowiska wykonawcze mogą pozostać, w zależności od stanu komputera.</span><span class="sxs-lookup"><span data-stu-id="685b6-297">In the following examples, some of the specified SDKs and runtimes may remain, depending on the state of the machine.</span></span> <span data-ttu-id="685b6-298">Aby usunąć wszystkie zestawy SDK i środowiska wykonawcze, należy `--force` wyświetlić je jawnie jako argumenty lub użyć tej opcji.</span><span class="sxs-lookup"><span data-stu-id="685b6-298">To remove all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="685b6-299">Usuń wszystkie środowiska uruchomieniowe .NET Core z wyjątkiem wersji `3.0.0-preview6-27804-01` bez konieczności potwierdzenia Y/N:</span><span class="sxs-lookup"><span data-stu-id="685b6-299">Remove all .NET Core runtimes except the version `3.0.0-preview6-27804-01` without requiring Y/N confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* <span data-ttu-id="685b6-300">Usuń wszystkie SDK .NET Core 1.1 bez konieczności potwierdzenia Y/n:</span><span class="sxs-lookup"><span data-stu-id="685b6-300">Remove all .NET Core 1.1 SDKs without requiring Y/n confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* <span data-ttu-id="685b6-301">Usuń sdk .NET Core 1.1.11 bez wyjścia konsoli:</span><span class="sxs-lookup"><span data-stu-id="685b6-301">Remove the .NET Core 1.1.11 SDK with no console output:</span></span>

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* <span data-ttu-id="685b6-302">Usuń wszystkie zestawy SDK .NET Core, które można bezpiecznie usunąć za pomocą tego narzędzia:</span><span class="sxs-lookup"><span data-stu-id="685b6-302">Remove all .NET Core SDKs that can safely be removed by this tool:</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* <span data-ttu-id="685b6-303">Usuń wszystkie zestawy SDK .NET Core, które mogą zostać usunięte przez to narzędzie, w tym zestawy SDK, które mogą być wymagane przez program Visual Studio (nie zalecane):</span><span class="sxs-lookup"><span data-stu-id="685b6-303">Remove all .NET Core SDKs that can be removed by this tool, including those SDKs that may be required by Visual Studio (not recommended):</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* <span data-ttu-id="685b6-304">Usuń wszystkie podstawowe pliki SDK .NET określone w pliku odpowiedzi`versions.rsp`</span><span class="sxs-lookup"><span data-stu-id="685b6-304">Remove all .NET Core SDKs that are specified in the response file `versions.rsp`</span></span>

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  <span data-ttu-id="685b6-305">Treść *versions.rsp* jest następująca:</span><span class="sxs-lookup"><span data-stu-id="685b6-305">The content of *versions.rsp* is as follows:</span></span>
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a><span data-ttu-id="685b6-306">Krok 4 - Usuń folder rezerwowy NuGet (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="685b6-306">Step 4 - Delete the NuGet fallback folder (optional)</span></span>

<span data-ttu-id="685b6-307">W niektórych przypadkach nie `NuGetFallbackFolder` trzeba już i może chcesz go usunąć.</span><span class="sxs-lookup"><span data-stu-id="685b6-307">In some cases, you no longer need the `NuGetFallbackFolder` and may wish to delete it.</span></span> <span data-ttu-id="685b6-308">Aby uzyskać więcej informacji na temat usuwania tego [folderu, zobacz Usuwanie pliku NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span><span class="sxs-lookup"><span data-stu-id="685b6-308">For more information about deleting this folder, see [Remove the NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span></span>

## <a name="uninstall-the-tool"></a><span data-ttu-id="685b6-309">Odinstaluj narzędzie</span><span class="sxs-lookup"><span data-stu-id="685b6-309">Uninstall the tool</span></span>

## <a name="windows"></a>[<span data-ttu-id="685b6-310">Windows</span><span class="sxs-lookup"><span data-stu-id="685b6-310">Windows</span></span>](#tab/windows)

1. <span data-ttu-id="685b6-311">Otwórz **pozycję Dodaj lub usuń programy**.</span><span class="sxs-lookup"><span data-stu-id="685b6-311">Open **Add or Remove Programs**.</span></span>
2. <span data-ttu-id="685b6-312">Wyszukaj `Microsoft .NET Core SDK Uninstall Tool`.</span><span class="sxs-lookup"><span data-stu-id="685b6-312">Search for `Microsoft .NET Core SDK Uninstall Tool`.</span></span>
3. <span data-ttu-id="685b6-313">Wybierz **pozycję Odinstaluj**.</span><span class="sxs-lookup"><span data-stu-id="685b6-313">Select **Uninstall**.</span></span>

## <a name="macos"></a>[<span data-ttu-id="685b6-314">Macos</span><span class="sxs-lookup"><span data-stu-id="685b6-314">macOS</span></span>](#tab/macos)

<span data-ttu-id="685b6-315">Usuń pobrany plik *dotnet-core-uninstall.tar.gz* z katalogu, w którym został zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="685b6-315">Delete the downloaded *dotnet-core-uninstall.tar.gz* file from the directory where it was installed.</span></span> <span data-ttu-id="685b6-316">Jeśli zawartość tego pliku została rozpakowana do innego katalogu, należy również usunąć tę zawartość.</span><span class="sxs-lookup"><span data-stu-id="685b6-316">If you unzipped the contents of this file into another directory, be sure to delete that content as well.</span></span>

---
