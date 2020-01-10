---
title: Narzędzie do odinstalowywania
description: Omówienie narzędzia do odinstalowywania platformy .NET Core, narzędzia z przewodnikiem, które umożliwia kontrolowane czyszczenie zestawów SDK i środowiska uruchomieniowego platformy .NET Core.
author: sfoslund
ms.date: 01/06/2020
ms.openlocfilehash: 4944c983cbd02b456c3a09a1b03bc28ba6e458cc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714554"
---
# <a name="net-core-uninstall-tool"></a><span data-ttu-id="e89c3-103">Narzędzie do dezinstalacji platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="e89c3-103">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="e89c3-104">[Narzędzie do dezinstalacji programu .NET Core](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`) umożliwia usuwanie zestawów SDK i środowisk uruchomieniowych platformy .NET Core z systemu.</span><span class="sxs-lookup"><span data-stu-id="e89c3-104">The [.NET Core Uninstall Tool](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and Runtimes from a system.</span></span> <span data-ttu-id="e89c3-105">Dostępna jest kolekcja opcji, aby określić wersje, które mają zostać odinstalowane.</span><span class="sxs-lookup"><span data-stu-id="e89c3-105">A collection of options is available to specify which versions you want to uninstall.</span></span>

<span data-ttu-id="e89c3-106">Narzędzie obsługuje systemy Windows i macOS.</span><span class="sxs-lookup"><span data-stu-id="e89c3-106">The tool supports Windows and macOS.</span></span> <span data-ttu-id="e89c3-107">System Linux nie jest obecnie obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="e89c3-107">Linux is currently not supported.</span></span>

<span data-ttu-id="e89c3-108">W systemie Windows narzędzie może odinstalować tylko zestawy SDK i środowiska uruchomieniowe, które zostały zainstalowane przy użyciu jednego z następujących instalatorów:</span><span class="sxs-lookup"><span data-stu-id="e89c3-108">On Windows, the tool can only uninstall SDKs and Runtimes that were installed using one of the following installers:</span></span>

- <span data-ttu-id="e89c3-109">Zestaw .NET Core SDK i Instalator środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="e89c3-109">The .NET Core SDK and runtime installer.</span></span>
- <span data-ttu-id="e89c3-110">Instalator programu Visual Studio w wersji wcześniejszej niż program Visual Studio 2019 w wersji 16,3.</span><span class="sxs-lookup"><span data-stu-id="e89c3-110">The Visual Studio installer in versions earlier than Visual Studio 2019 version 16.3.</span></span>

<span data-ttu-id="e89c3-111">W systemie macOS narzędzie może odinstalować tylko zestawy SDK i środowiska uruchomieniowe znajdujące się w folderze */usr/local/share/dotnet* .</span><span class="sxs-lookup"><span data-stu-id="e89c3-111">On macOS, the tool can only uninstall SDKs and runtimes located in the */usr/local/share/dotnet* folder.</span></span>

<span data-ttu-id="e89c3-112">Ze względu na te ograniczenia narzędzie może nie być w stanie odinstalować wszystkich zestawów SDK i środowisk uruchomieniowych platformy .NET Core na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e89c3-112">Because of these limitations, the tool may not be able to uninstall all of the .NET Core SDKs and runtimes on your machine.</span></span> <span data-ttu-id="e89c3-113">Można użyć `dotnet --info` polecenia, aby znaleźć wszystkie zainstalowane zestawy SDK .NET Core i środowiska uruchomieniowe, w tym zestawy SDK i środowiska uruchomieniowe, których to narzędzie nie może usunąć.</span><span class="sxs-lookup"><span data-stu-id="e89c3-113">You can use the `dotnet --info` command to find all of the .NET Core SDKs and runtimes installed, including those SDKs and runtimes that this tool can't remove.</span></span> <span data-ttu-id="e89c3-114">Polecenie `dotnet-core-uninstall list` wyświetla listę zestawów SDK, które można odinstalować za pomocą narzędzia.</span><span class="sxs-lookup"><span data-stu-id="e89c3-114">The `dotnet-core-uninstall list` command displays which SDKs can be uninstalled with the tool.</span></span>

## <a name="install-the-tool"></a><span data-ttu-id="e89c3-115">Zainstaluj narzędzie</span><span class="sxs-lookup"><span data-stu-id="e89c3-115">Install the tool</span></span>

<span data-ttu-id="e89c3-116">Narzędzie do odinstalowywania platformy .NET Core można pobrać z repozytorium usługi GitHub [/CLI-Lab](https://github.com/dotnet/cli-lab/releases) w ramach programu dotnet.</span><span class="sxs-lookup"><span data-stu-id="e89c3-116">You can download the .NET Core Uninstall Tool from the [dotnet/cli-lab](https://github.com/dotnet/cli-lab/releases) GitHub repository.</span></span>

> [!NOTE]
> <span data-ttu-id="e89c3-117">Narzędzie wymaga podniesienia uprawnień, aby odinstalować zestawy SDK i środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e89c3-117">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="e89c3-118">W związku z tym należy ją zainstalować w katalogu chronionym przed zapisem, takim jak *C:\Program Files* w systemie Windows lub */usr/local/bin* na macOS.</span><span class="sxs-lookup"><span data-stu-id="e89c3-118">Therefore, it should be installed in a write-protected directory such as *C:\Program Files* on Windows or */usr/local/bin* on macOS.</span></span> <span data-ttu-id="e89c3-119">Zobacz również [podwyższony poziom dostępu dla poleceń dotnet](../tools/elevated-access.md).</span><span class="sxs-lookup"><span data-stu-id="e89c3-119">See also [Elevated access for dotnet commands](../tools/elevated-access.md).</span></span> <span data-ttu-id="e89c3-120">Szczegółowe instrukcje dotyczące instalacji są dostępne na [stronie wydań usługi GitHub](https://github.com/dotnet/cli-lab/releases).</span><span class="sxs-lookup"><span data-stu-id="e89c3-120">Detailed installation instructions are available on the [GitHub Releases page](https://github.com/dotnet/cli-lab/releases).</span></span>

## <a name="run-the-tool"></a><span data-ttu-id="e89c3-121">Uruchamianie narzędzia</span><span class="sxs-lookup"><span data-stu-id="e89c3-121">Run the tool</span></span>

<span data-ttu-id="e89c3-122">W poniższych krokach przedstawiono zalecane podejście do uruchamiania narzędzia do odinstalowywania:</span><span class="sxs-lookup"><span data-stu-id="e89c3-122">The following steps show the recommended approach for running the uninstall tool:</span></span>

- [<span data-ttu-id="e89c3-123">Krok 1. wyświetlanie zainstalowanych zestawów SDK i środowisk uruchomieniowych platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="e89c3-123">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>](#step-1---display-installed-net-core-sdks-and-runtimes)
- [<span data-ttu-id="e89c3-124">Krok 2 — wykonywanie suchego przebiegu</span><span class="sxs-lookup"><span data-stu-id="e89c3-124">Step 2 - Do a dry run</span></span>](#step-2---do-a-dry-run)
- [<span data-ttu-id="e89c3-125">Krok 3 — Odinstalowywanie zestawów SDK i środowisk uruchomieniowych platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="e89c3-125">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>](#step-3---uninstall-net-core-sdks-and-runtimes)
- [<span data-ttu-id="e89c3-126">Krok 4. Usuwanie folderu rezerwowego NuGet (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="e89c3-126">Step 4 - Delete the NuGet fallback folder (optional)</span></span>](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a><span data-ttu-id="e89c3-127">Krok 1. wyświetlanie zainstalowanych zestawów SDK i środowisk uruchomieniowych platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="e89c3-127">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>

<span data-ttu-id="e89c3-128">`dotnet-core-uninstall list` polecenie wyświetla listę zainstalowanych zestawów SDK .NET Core i środowiska uruchomieniowe, które można usunąć za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="e89c3-128">The `dotnet-core-uninstall list` command lists the installed .NET Core SDKs and runtimes that can be removed with this tool.</span></span> <span data-ttu-id="e89c3-129">Niektóre zestawy SDK i środowiska uruchomieniowe mogą być wymagane przez program Visual Studio i są wyświetlane z zawarto adnotacją dlaczego nie zaleca się ich odinstalowywania.</span><span class="sxs-lookup"><span data-stu-id="e89c3-129">Some SDKs and runtimes may be required by Visual Studio and they're displayed with a note of why it isn't recommended to uninstall them.</span></span>

<span data-ttu-id="e89c3-130">**dotnet-Core — lista dezinstalacji**</span><span class="sxs-lookup"><span data-stu-id="e89c3-130">**dotnet-core-uninstall list**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="e89c3-131">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="e89c3-131">Synopsis</span></span>

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a><span data-ttu-id="e89c3-132">Opcje</span><span class="sxs-lookup"><span data-stu-id="e89c3-132">Options</span></span>

## <a name="windowstabwindows"></a>[<span data-ttu-id="e89c3-133">Windows</span><span class="sxs-lookup"><span data-stu-id="e89c3-133">Windows</span></span>](#tab/windows)

* **`--aspnet-runtime`**

  <span data-ttu-id="e89c3-134">Wyświetla wszystkie ASP.NET Core środowiska uruchomieniowe, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="e89c3-134">Lists all the ASP.NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="e89c3-135">Wyświetla listę wszystkich pakietów środowiska uruchomieniowego środowiska .NET Core i hostingu, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="e89c3-135">Lists all the .NET Core runtime and hosting bundles that can be uninstalled with this tool.</span></span>

* **`--runtime`**

  <span data-ttu-id="e89c3-136">Wyświetla wszystkie środowiska uruchomieniowe platformy .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="e89c3-136">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="e89c3-137">Wyświetla listę wszystkich zestawów SDK platformy .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="e89c3-137">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="e89c3-138">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="e89c3-138">Sets the verbosity level.</span></span> <span data-ttu-id="e89c3-139">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="e89c3-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="e89c3-140">Wartość domyślna to `normal`.</span><span class="sxs-lookup"><span data-stu-id="e89c3-140">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="e89c3-141">Wyświetla listę wszystkich zestawów SDK i środowisk uruchomieniowych x64 .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="e89c3-141">Lists all x64 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

* **`--x86`**

  <span data-ttu-id="e89c3-142">Wyświetla listę wszystkich zestawów SDK i środowisk uruchomieniowych x86 .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="e89c3-142">Lists all x86 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

## <a name="macostabmacos"></a>[<span data-ttu-id="e89c3-143">macOS</span><span class="sxs-lookup"><span data-stu-id="e89c3-143">macOS</span></span>](#tab/macos)

* **`--runtime`**

  <span data-ttu-id="e89c3-144">Wyświetla wszystkie środowiska uruchomieniowe platformy .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="e89c3-144">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="e89c3-145">Wyświetla listę wszystkich zestawów SDK platformy .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="e89c3-145">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="e89c3-146">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="e89c3-146">Sets the verbosity level.</span></span> <span data-ttu-id="e89c3-147">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="e89c3-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="e89c3-148">Wartość domyślna to `normal`.</span><span class="sxs-lookup"><span data-stu-id="e89c3-148">The default value is `normal`.</span></span>
  
---

#### <a name="examples"></a><span data-ttu-id="e89c3-149">Przykłady</span><span class="sxs-lookup"><span data-stu-id="e89c3-149">Examples</span></span>

* <span data-ttu-id="e89c3-150">Wyświetl listę wszystkich zestawów SDK platformy .NET Core i środowiska uruchomieniowe, które można usunąć za pomocą tego narzędzia:</span><span class="sxs-lookup"><span data-stu-id="e89c3-150">List all .NET Core SDKs and runtimes that can be removed with this tool:</span></span>

  ```console
  dotnet-core-uninstall list
  ```

* <span data-ttu-id="e89c3-151">Wyświetl listę wszystkich zestawów SDK i środowisk uruchomieniowych x64 .NET Core:</span><span class="sxs-lookup"><span data-stu-id="e89c3-151">List all x64 .NET Core SDKs and runtimes:</span></span>

  ```console
  dotnet-core-uninstall list --x64
  ```

* <span data-ttu-id="e89c3-152">Wyświetl listę wszystkich zestawów SDK dla platformy .NET Core:</span><span class="sxs-lookup"><span data-stu-id="e89c3-152">List all x86 .NET Core SDKs:</span></span>

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a><span data-ttu-id="e89c3-153">Krok 2 — wykonywanie suchego przebiegu</span><span class="sxs-lookup"><span data-stu-id="e89c3-153">Step 2 - Do a dry run</span></span>

<span data-ttu-id="e89c3-154">Polecenia `dotnet-core-uninstall dry-run` i `dotnet-core-uninstall whatif` wyświetlają zestawy .NET Core i środowiska uruchomieniowe, które zostaną usunięte na podstawie opcji dostępnych bez konieczności odinstalowania.</span><span class="sxs-lookup"><span data-stu-id="e89c3-154">The `dotnet-core-uninstall dry-run` and `dotnet-core-uninstall whatif` commands display the .NET Core SDKs and runtimes that will be removed based on the options provided without performing the uninstall.</span></span> <span data-ttu-id="e89c3-155">Te polecenia są synonimami.</span><span class="sxs-lookup"><span data-stu-id="e89c3-155">These commands are synonyms.</span></span>

<span data-ttu-id="e89c3-156">**dotnet-Core — Odinstalowywanie suchego i dotnet-Core-Uninstall whatIf**</span><span class="sxs-lookup"><span data-stu-id="e89c3-156">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="e89c3-157">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="e89c3-157">Synopsis</span></span>

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="e89c3-158">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e89c3-158">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="e89c3-159">Określona wersja do odinstalowania.</span><span class="sxs-lookup"><span data-stu-id="e89c3-159">The specified version to uninstall.</span></span> <span data-ttu-id="e89c3-160">Można wyświetlić kilka kolejnych wersji, rozdzielonych spacjami.</span><span class="sxs-lookup"><span data-stu-id="e89c3-160">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="e89c3-161">Pliki odpowiedzi są również obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="e89c3-161">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="e89c3-162">Pliki odpowiedzi są alternatywą do umieszczania wszystkich wersji w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="e89c3-162">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="e89c3-163">Są one plikami tekstowymi, zazwyczaj przy użyciu rozszerzenia \*. rsp, a każda wersja jest wymieniona w osobnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="e89c3-163">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="e89c3-164">Aby określić plik odpowiedzi dla argumentu `VERSION`, użyj znaku \@ bezpośrednio po nazwie pliku odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="e89c3-164">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="e89c3-165">Opcje</span><span class="sxs-lookup"><span data-stu-id="e89c3-165">Options</span></span>

## <a name="windowstabwindows"></a>[<span data-ttu-id="e89c3-166">Windows</span><span class="sxs-lookup"><span data-stu-id="e89c3-166">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="e89c3-167">Usuwa wszystkie zestawy SDK i środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e89c3-167">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="e89c3-168">Usuwa tylko zestawy SDK i środowiska uruchomieniowe platformy .NET Core z wersją mniejszą niż określona wersja.</span><span class="sxs-lookup"><span data-stu-id="e89c3-168">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="e89c3-169">Określona wersja jest zainstalowana.</span><span class="sxs-lookup"><span data-stu-id="e89c3-169">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="e89c3-170">Usuwa wszystkie zestawy SDK i środowiska uruchomieniowe platformy .NET Core, z wyjątkiem określonych wersji.</span><span class="sxs-lookup"><span data-stu-id="e89c3-170">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="e89c3-171">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core, z wyjątkiem jednej najwyższej wersji.</span><span class="sxs-lookup"><span data-stu-id="e89c3-171">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="e89c3-172">Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe zastąpione nowszymi poprawkami.</span><span class="sxs-lookup"><span data-stu-id="e89c3-172">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="e89c3-173">Ta opcja chroni plik Global. JSON.</span><span class="sxs-lookup"><span data-stu-id="e89c3-173">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="e89c3-174">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core oznaczone jako wersje zapoznawcze.</span><span class="sxs-lookup"><span data-stu-id="e89c3-174">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="e89c3-175">Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe oznaczone jako wersje zapoznawcze z wyjątkiem tego, który jest najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="e89c3-175">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="e89c3-176">Usuwa tylko ASP.NET Core środowiska uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="e89c3-176">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="e89c3-177">Usuwa środowisko uruchomieniowe programu .NET Core i tylko pakiety hostingu.</span><span class="sxs-lookup"><span data-stu-id="e89c3-177">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="e89c3-178">Usuwa zestawy .NET Core i środowiska uruchomieniowe zgodne z określoną wersją `major.minor`.</span><span class="sxs-lookup"><span data-stu-id="e89c3-178">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="e89c3-179">Usuwa tylko środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e89c3-179">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="e89c3-180">Usuwa tylko zestawy SDK platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e89c3-180">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="e89c3-181">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="e89c3-181">Sets the verbosity level.</span></span> <span data-ttu-id="e89c3-182">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="e89c3-182">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="e89c3-183">Wartość domyślna to `normal`.</span><span class="sxs-lookup"><span data-stu-id="e89c3-183">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="e89c3-184">Należy używać z `--sdk`, `--runtime`i `--aspnet-runtime` do usuwania zestawów SDK x64 lub środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="e89c3-184">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="e89c3-185">Aby można było usunąć zestawy SDK lub środowiska uruchomieniowe x86, należy użyć programu z `--sdk`, `--runtime`i `--aspnet-runtime`.</span><span class="sxs-lookup"><span data-stu-id="e89c3-185">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="e89c3-186">**`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e89c3-186">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="e89c3-187">Uwagi:</span><span class="sxs-lookup"><span data-stu-id="e89c3-187">Notes:</span></span>

1. <span data-ttu-id="e89c3-188">Wymagany jest dokładnie jeden z `--sdk`, `--runtime`, `--aspnet-runtime`i `--hosting-bundle`.</span><span class="sxs-lookup"><span data-stu-id="e89c3-188">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="e89c3-189">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`i `[<VERSION>...]` są na wyłączność.</span><span class="sxs-lookup"><span data-stu-id="e89c3-189">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="e89c3-190">Jeśli nie określono `--x64` lub `--x86`, zostaną usunięte oba wersje x64 i x86.</span><span class="sxs-lookup"><span data-stu-id="e89c3-190">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macostabmacos"></a>[<span data-ttu-id="e89c3-191">macOS</span><span class="sxs-lookup"><span data-stu-id="e89c3-191">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="e89c3-192">Usuwa wszystkie zestawy SDK i środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e89c3-192">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="e89c3-193">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core poniżej określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="e89c3-193">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="e89c3-194">Określona wersja pozostanie.</span><span class="sxs-lookup"><span data-stu-id="e89c3-194">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="e89c3-195">Usuwa zestawy .NET Core i środowiska uruchomieniowe, z wyjątkiem określonych wersji.</span><span class="sxs-lookup"><span data-stu-id="e89c3-195">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="e89c3-196">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core, z wyjątkiem jednej najwyższej wersji.</span><span class="sxs-lookup"><span data-stu-id="e89c3-196">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="e89c3-197">Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe zastąpione nowszymi poprawkami.</span><span class="sxs-lookup"><span data-stu-id="e89c3-197">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="e89c3-198">Ta opcja chroni plik Global. JSON.</span><span class="sxs-lookup"><span data-stu-id="e89c3-198">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="e89c3-199">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core oznaczone jako wersje zapoznawcze.</span><span class="sxs-lookup"><span data-stu-id="e89c3-199">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="e89c3-200">Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe oznaczone jako wersje zapoznawcze z wyjątkiem tego, który jest najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="e89c3-200">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="e89c3-201">Usuwa zestawy .NET Core i środowiska uruchomieniowe zgodne z określoną wersją `major.minor`.</span><span class="sxs-lookup"><span data-stu-id="e89c3-201">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="e89c3-202">Usuwa tylko środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e89c3-202">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="e89c3-203">Usuwa tylko zestawy SDK platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e89c3-203">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="e89c3-204">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="e89c3-204">Sets the verbosity level.</span></span> <span data-ttu-id="e89c3-205">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="e89c3-205">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="e89c3-206">Wartość domyślna to `normal`.</span><span class="sxs-lookup"><span data-stu-id="e89c3-206">The default value is `normal`.</span></span>
  
* <span data-ttu-id="e89c3-207">**`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio lub zestawy SDK.</span><span class="sxs-lookup"><span data-stu-id="e89c3-207">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="e89c3-208">Uwagi:</span><span class="sxs-lookup"><span data-stu-id="e89c3-208">Notes:</span></span>

1. <span data-ttu-id="e89c3-209">Wymagany jest dokładnie jeden z `--sdk` i `--runtime`.</span><span class="sxs-lookup"><span data-stu-id="e89c3-209">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="e89c3-210">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`i `[<VERSION>...]` są na wyłączność.</span><span class="sxs-lookup"><span data-stu-id="e89c3-210">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="e89c3-211">Przykłady</span><span class="sxs-lookup"><span data-stu-id="e89c3-211">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="e89c3-212">Domyślnie zestawy SDK platformy .NET Core i środowiska uruchomieniowe, które mogą być wymagane przez program Visual Studio lub inne zestawy SDK, nie są uwzględniane w danych wyjściowych `dotnet-core-uninstall dry-run`.</span><span class="sxs-lookup"><span data-stu-id="e89c3-212">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are not included in `dotnet-core-uninstall dry-run` output.</span></span> <span data-ttu-id="e89c3-213">W poniższych przykładach niektóre z określonych zestawów SDK i środowiska uruchomieniowe mogą nie zostać uwzględnione w danych wyjściowych, w zależności od stanu komputera.</span><span class="sxs-lookup"><span data-stu-id="e89c3-213">In the following examples, some of the specified SDKs and runtimes may not be included in the output, depending on the state of the machine.</span></span> <span data-ttu-id="e89c3-214">Aby uwzględnić wszystkie zestawy SDK i środowiska uruchomieniowe, należy je jawnie wystawić jako argumenty lub użyć opcji `--force`.</span><span class="sxs-lookup"><span data-stu-id="e89c3-214">To include all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="e89c3-215">Suchy przebieg usuwania wszystkich środowisk uruchomieniowych platformy .NET Core, które zostały zastąpione nowszymi poprawkami:</span><span class="sxs-lookup"><span data-stu-id="e89c3-215">Dry run of removing all .NET Core runtimes that have been superseded by higher patches:</span></span>

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* <span data-ttu-id="e89c3-216">Suche uruchomienie usuwania wszystkich zestawów SDK platformy .NET Core poniżej wersji `2.2.301`:</span><span class="sxs-lookup"><span data-stu-id="e89c3-216">Dry run of removing all .NET Core SDKs below the version `2.2.301`:</span></span>

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a><span data-ttu-id="e89c3-217">Krok 3 — Odinstalowywanie zestawów SDK i środowisk uruchomieniowych platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="e89c3-217">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>

<span data-ttu-id="e89c3-218">`dotnet-core-uninstall remove` Odinstalowuje zestawy SDK i środowiska uruchomieniowe platformy .NET Core, które są określone przez kolekcję opcji.</span><span class="sxs-lookup"><span data-stu-id="e89c3-218">`dotnet-core-uninstall remove` uninstalls .NET Core SDKs and Runtimes that are specified by a collection of options.</span></span> <span data-ttu-id="e89c3-219">Narzędzia nie można użyć do odinstalowania zestawów SDK i środowiska uruchomieniowego w wersji 5,0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="e89c3-219">The tool can't be used to uninstall SDKs and Runtimes with version 5.0 or above.</span></span>

<span data-ttu-id="e89c3-220">Ponieważ to narzędzie ma szkodliwe zachowanie, **zdecydowanie** zaleca się wykonanie suchego uruchomienia przed uruchomieniem polecenia Usuń.</span><span class="sxs-lookup"><span data-stu-id="e89c3-220">Since this tool has a destructive behavior, it's **highly** recommended that you do a dry run before running the remove command.</span></span> <span data-ttu-id="e89c3-221">W przypadku przebiegu suchego zostanie wyświetlona zawartość zestawów SDK i środowiska uruchomieniowe platformy .NET Core po użyciu polecenia `remove`.</span><span class="sxs-lookup"><span data-stu-id="e89c3-221">The dry run will show you what .NET Core SDKs and runtimes will be removed when you use the `remove` command.</span></span> <span data-ttu-id="e89c3-222">Zapoznaj się z tematem [czy należy usunąć wersję?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version) , aby dowiedzieć się, które zestawy SDK i środowiska uruchomieniowe są bezpieczne do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="e89c3-222">Refer to [Should I remove a version?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version) to learn which SDKs and runtimes are safe to remove.</span></span>

> [!CAUTION]
> <span data-ttu-id="e89c3-223">Należy pamiętać o następujących zastrzeżeniach:</span><span class="sxs-lookup"><span data-stu-id="e89c3-223">Keep in mind the following caveats:</span></span>
>
>- <span data-ttu-id="e89c3-224">To narzędzie umożliwia odinstalowanie wersji zestaw .NET Core SDK, które są wymagane przez pliki `global.json` na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e89c3-224">This tool can uninstall versions of the .NET Core SDK that are required by `global.json` files on your machine.</span></span> <span data-ttu-id="e89c3-225">Zestawy SDK platformy .NET Core można ponownie zainstalować ze strony [pobierania programu .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="e89c3-225">You can reinstall .NET Core SDKs from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="e89c3-226">To narzędzie umożliwia odinstalowanie wersji środowiska uruchomieniowego programu .NET Core, które są wymagane przez aplikacje zależne od platformy.</span><span class="sxs-lookup"><span data-stu-id="e89c3-226">This tool can uninstall versions of the .NET Core runtime that are required by framework dependent applications on your machine.</span></span> <span data-ttu-id="e89c3-227">Środowiska uruchomieniowe platformy .NET Core można ponownie zainstalować ze strony [pobierania programu .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="e89c3-227">You can reinstall .NET Core runtimes from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="e89c3-228">To narzędzie umożliwia odinstalowanie wersji zestaw .NET Core SDK i środowiska uruchomieniowego, na których bazuje program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e89c3-228">This tool can uninstall versions of the .NET Core SDK and runtime that Visual Studio relies on.</span></span> <span data-ttu-id="e89c3-229">W przypadku przerwania instalacji programu Visual Studio Uruchom polecenie "Napraw" w Instalatorze programu Visual Studio, aby powrócić do stanu roboczego.</span><span class="sxs-lookup"><span data-stu-id="e89c3-229">If you break your Visual Studio installation, run "Repair" in the Visual Studio installer to get back to a working state.</span></span>

<span data-ttu-id="e89c3-230">Domyślnie wszystkie polecenia zachowują zestawy .NET Core i środowiska uruchomieniowe, które mogą być wymagane przez program Visual Studio lub inne zestawy SDK.</span><span class="sxs-lookup"><span data-stu-id="e89c3-230">By default, all commands keep the .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs.</span></span> <span data-ttu-id="e89c3-231">Te zestawy SDK i środowiska uruchomieniowe mogą zostać odinstalowane przez wymienienie ich jawnie jako argumenty lub przy użyciu opcji `--force`.</span><span class="sxs-lookup"><span data-stu-id="e89c3-231">These SDKs and runtimes can be uninstalled by listing them explicitly as arguments or by using the `--force` option.</span></span>

<span data-ttu-id="e89c3-232">Narzędzie wymaga podniesienia uprawnień, aby odinstalować zestawy SDK i środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e89c3-232">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="e89c3-233">Uruchom narzędzie w wierszu polecenia administratora w systemie Windows i z `sudo` na macOS.</span><span class="sxs-lookup"><span data-stu-id="e89c3-233">Run the tool in an Administrator command prompt on Windows and with `sudo` on macOS.</span></span> <span data-ttu-id="e89c3-234">Polecenia `dry-run` i `whatif` nie wymagają podniesienia uprawnień.</span><span class="sxs-lookup"><span data-stu-id="e89c3-234">The `dry-run` and `whatif` commands don't require elevation.</span></span>

<span data-ttu-id="e89c3-235">**dotnet-Core — usuwanie odinstalowania**</span><span class="sxs-lookup"><span data-stu-id="e89c3-235">**dotnet-core-uninstall remove**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="e89c3-236">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="e89c3-236">Synopsis</span></span>

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="e89c3-237">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e89c3-237">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="e89c3-238">Określona wersja do odinstalowania.</span><span class="sxs-lookup"><span data-stu-id="e89c3-238">The specified version to uninstall.</span></span> <span data-ttu-id="e89c3-239">Można wyświetlić kilka kolejnych wersji, rozdzielonych spacjami.</span><span class="sxs-lookup"><span data-stu-id="e89c3-239">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="e89c3-240">Pliki odpowiedzi są również obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="e89c3-240">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="e89c3-241">Pliki odpowiedzi są alternatywą do umieszczania wszystkich wersji w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="e89c3-241">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="e89c3-242">Są one plikami tekstowymi, zazwyczaj przy użyciu rozszerzenia \*. rsp, a każda wersja jest wymieniona w osobnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="e89c3-242">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="e89c3-243">Aby określić plik odpowiedzi dla argumentu `VERSION`, użyj znaku \@ bezpośrednio po nazwie pliku odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="e89c3-243">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="e89c3-244">Opcje</span><span class="sxs-lookup"><span data-stu-id="e89c3-244">Options</span></span>

## <a name="windowstabwindows"></a>[<span data-ttu-id="e89c3-245">Windows</span><span class="sxs-lookup"><span data-stu-id="e89c3-245">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="e89c3-246">Usuwa wszystkie zestawy SDK i środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e89c3-246">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="e89c3-247">Usuwa tylko zestawy SDK i środowiska uruchomieniowe platformy .NET Core z wersją mniejszą niż określona wersja.</span><span class="sxs-lookup"><span data-stu-id="e89c3-247">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="e89c3-248">Określona wersja jest zainstalowana.</span><span class="sxs-lookup"><span data-stu-id="e89c3-248">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="e89c3-249">Usuwa wszystkie zestawy SDK i środowiska uruchomieniowe platformy .NET Core, z wyjątkiem określonych wersji.</span><span class="sxs-lookup"><span data-stu-id="e89c3-249">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="e89c3-250">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core, z wyjątkiem jednej najwyższej wersji.</span><span class="sxs-lookup"><span data-stu-id="e89c3-250">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="e89c3-251">Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe zastąpione nowszymi poprawkami.</span><span class="sxs-lookup"><span data-stu-id="e89c3-251">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="e89c3-252">Ta opcja chroni plik Global. JSON.</span><span class="sxs-lookup"><span data-stu-id="e89c3-252">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="e89c3-253">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core oznaczone jako wersje zapoznawcze.</span><span class="sxs-lookup"><span data-stu-id="e89c3-253">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="e89c3-254">Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe oznaczone jako wersje zapoznawcze z wyjątkiem tego, który jest najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="e89c3-254">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="e89c3-255">Usuwa tylko ASP.NET Core środowiska uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="e89c3-255">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="e89c3-256">Usuwa środowisko uruchomieniowe programu .NET Core i tylko pakiety hostingu.</span><span class="sxs-lookup"><span data-stu-id="e89c3-256">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="e89c3-257">Usuwa zestawy .NET Core i środowiska uruchomieniowe zgodne z określoną wersją `major.minor`.</span><span class="sxs-lookup"><span data-stu-id="e89c3-257">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="e89c3-258">Usuwa tylko środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e89c3-258">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="e89c3-259">Usuwa tylko zestawy SDK platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e89c3-259">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="e89c3-260">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="e89c3-260">Sets the verbosity level.</span></span> <span data-ttu-id="e89c3-261">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="e89c3-261">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="e89c3-262">Wartość domyślna to `normal`.</span><span class="sxs-lookup"><span data-stu-id="e89c3-262">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="e89c3-263">Należy używać z `--sdk`, `--runtime`i `--aspnet-runtime` do usuwania zestawów SDK x64 lub środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="e89c3-263">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="e89c3-264">Aby można było usunąć zestawy SDK lub środowiska uruchomieniowe x86, należy użyć programu z `--sdk`, `--runtime`i `--aspnet-runtime`.</span><span class="sxs-lookup"><span data-stu-id="e89c3-264">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="e89c3-265">**`-y, --yes`** Wykonuje polecenie bez potwierdzenia typu "tak" lub "nie".</span><span class="sxs-lookup"><span data-stu-id="e89c3-265">**`-y, --yes`** Executes the command without requiring a yes or no confirmation.</span></span>

* <span data-ttu-id="e89c3-266">**`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e89c3-266">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="e89c3-267">Uwagi:</span><span class="sxs-lookup"><span data-stu-id="e89c3-267">Notes:</span></span>

1. <span data-ttu-id="e89c3-268">Wymagany jest dokładnie jeden z `--sdk`, `--runtime`, `--aspnet-runtime`i `--hosting-bundle`.</span><span class="sxs-lookup"><span data-stu-id="e89c3-268">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="e89c3-269">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`i `[<VERSION>...]` są na wyłączność.</span><span class="sxs-lookup"><span data-stu-id="e89c3-269">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="e89c3-270">Jeśli nie określono `--x64` lub `--x86`, zostaną usunięte oba wersje x64 i x86.</span><span class="sxs-lookup"><span data-stu-id="e89c3-270">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macostabmacos"></a>[<span data-ttu-id="e89c3-271">macOS</span><span class="sxs-lookup"><span data-stu-id="e89c3-271">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="e89c3-272">Usuwa wszystkie zestawy SDK i środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e89c3-272">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="e89c3-273">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core poniżej określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="e89c3-273">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="e89c3-274">Określona wersja pozostanie.</span><span class="sxs-lookup"><span data-stu-id="e89c3-274">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="e89c3-275">Usuwa zestawy .NET Core i środowiska uruchomieniowe, z wyjątkiem określonych wersji.</span><span class="sxs-lookup"><span data-stu-id="e89c3-275">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="e89c3-276">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core, z wyjątkiem jednej najwyższej wersji.</span><span class="sxs-lookup"><span data-stu-id="e89c3-276">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="e89c3-277">Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe zastąpione nowszymi poprawkami.</span><span class="sxs-lookup"><span data-stu-id="e89c3-277">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="e89c3-278">Ta opcja chroni plik Global. JSON.</span><span class="sxs-lookup"><span data-stu-id="e89c3-278">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="e89c3-279">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core oznaczone jako wersje zapoznawcze.</span><span class="sxs-lookup"><span data-stu-id="e89c3-279">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="e89c3-280">Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe oznaczone jako wersje zapoznawcze z wyjątkiem tego, który jest najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="e89c3-280">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="e89c3-281">Usuwa zestawy .NET Core i środowiska uruchomieniowe zgodne z określoną wersją `major.minor`.</span><span class="sxs-lookup"><span data-stu-id="e89c3-281">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="e89c3-282">Usuwa tylko środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e89c3-282">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="e89c3-283">Usuwa tylko zestawy SDK platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e89c3-283">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="e89c3-284">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="e89c3-284">Sets the verbosity level.</span></span> <span data-ttu-id="e89c3-285">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="e89c3-285">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="e89c3-286">Wartość domyślna to `normal`.</span><span class="sxs-lookup"><span data-stu-id="e89c3-286">The default value is `normal`.</span></span>

* <span data-ttu-id="e89c3-287">**`-y, --yes`** Wykonuje polecenie bez potwierdzenia Y/N.</span><span class="sxs-lookup"><span data-stu-id="e89c3-287">**`-y, --yes`** Executes the command without requiring Y/N confirmation.</span></span>
  
* <span data-ttu-id="e89c3-288">**`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio lub zestawy SDK.</span><span class="sxs-lookup"><span data-stu-id="e89c3-288">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="e89c3-289">Uwagi:</span><span class="sxs-lookup"><span data-stu-id="e89c3-289">Notes:</span></span>

1. <span data-ttu-id="e89c3-290">Wymagany jest dokładnie jeden z `--sdk` i `--runtime`.</span><span class="sxs-lookup"><span data-stu-id="e89c3-290">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="e89c3-291">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`i `[<VERSION>...]` są na wyłączność.</span><span class="sxs-lookup"><span data-stu-id="e89c3-291">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="e89c3-292">Przykłady</span><span class="sxs-lookup"><span data-stu-id="e89c3-292">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="e89c3-293">Domyślnie są przechowywane zestawy SDK i środowiska uruchomieniowe platformy .NET Core, które mogą być wymagane przez program Visual Studio lub inne zestawy SDK.</span><span class="sxs-lookup"><span data-stu-id="e89c3-293">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are kept.</span></span> <span data-ttu-id="e89c3-294">W poniższych przykładach niektóre z określonych zestawów SDK i środowiska uruchomieniowe mogą pozostać w zależności od stanu komputera.</span><span class="sxs-lookup"><span data-stu-id="e89c3-294">In the following examples, some of the specified SDKs and runtimes may remain, depending on the state of the machine.</span></span> <span data-ttu-id="e89c3-295">Aby usunąć wszystkie zestawy SDK i środowiska uruchomieniowe, należy je jawnie wystawić jako argumenty lub użyć opcji `--force`.</span><span class="sxs-lookup"><span data-stu-id="e89c3-295">To remove all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="e89c3-296">Usuń wszystkie środowiska uruchomieniowe platformy .NET Core, z wyjątkiem wersji `3.0.0-preview6-27804-01` bez konieczności potwierdzania Y/N:</span><span class="sxs-lookup"><span data-stu-id="e89c3-296">Remove all .NET Core runtimes except the version `3.0.0-preview6-27804-01` without requiring Y/N confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* <span data-ttu-id="e89c3-297">Usuń wszystkie zestawy SDK platformy .NET Core 1,1 bez konieczności potwierdzania Y/n:</span><span class="sxs-lookup"><span data-stu-id="e89c3-297">Remove all .NET Core 1.1 SDKs without requiring Y/n confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* <span data-ttu-id="e89c3-298">Usuń zestaw .NET Core 1.1.11 SDK bez danych wyjściowych konsoli:</span><span class="sxs-lookup"><span data-stu-id="e89c3-298">Remove the .NET Core 1.1.11 SDK with no console output:</span></span>

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* <span data-ttu-id="e89c3-299">Usuń wszystkie zestawy SDK platformy .NET Core, które można bezpiecznie usunąć za pomocą tego narzędzia:</span><span class="sxs-lookup"><span data-stu-id="e89c3-299">Remove all .NET Core SDKs that can safely be removed by this tool:</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* <span data-ttu-id="e89c3-300">Usuń wszystkie zestawy SDK platformy .NET Core, które mogą zostać usunięte przez to narzędzie, w tym zestawy SDK, które mogą być wymagane przez program Visual Studio (niezalecane):</span><span class="sxs-lookup"><span data-stu-id="e89c3-300">Remove all .NET Core SDKs that can be removed by this tool, including those SDKs that may be required by Visual Studio (not recommended):</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* <span data-ttu-id="e89c3-301">Usuń wszystkie zestawy SDK platformy .NET Core, które są określone w pliku odpowiedzi `versions.rsp`</span><span class="sxs-lookup"><span data-stu-id="e89c3-301">Remove all .NET Core SDKs that are specified in the response file `versions.rsp`</span></span>

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  <span data-ttu-id="e89c3-302">Zawartość *wersji. rsp* jest następująca:</span><span class="sxs-lookup"><span data-stu-id="e89c3-302">The content of *versions.rsp* is as follows:</span></span>
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a><span data-ttu-id="e89c3-303">Krok 4. Usuwanie folderu rezerwowego NuGet (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="e89c3-303">Step 4 - Delete the NuGet fallback folder (optional)</span></span>

<span data-ttu-id="e89c3-304">W niektórych przypadkach nie jest już potrzebne `NuGetFallbackFolder` i może zostać usunięta.</span><span class="sxs-lookup"><span data-stu-id="e89c3-304">In some cases, you no longer need the `NuGetFallbackFolder` and may wish to delete it.</span></span> <span data-ttu-id="e89c3-305">Aby uzyskać więcej informacji na temat usuwania tego folderu, zobacz [usuwanie NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span><span class="sxs-lookup"><span data-stu-id="e89c3-305">For more information about deleting this folder, see [Remove the NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span></span>

## <a name="uninstall-the-tool"></a><span data-ttu-id="e89c3-306">Odinstalowywanie narzędzia</span><span class="sxs-lookup"><span data-stu-id="e89c3-306">Uninstall the tool</span></span>

## <a name="windowstabwindows"></a>[<span data-ttu-id="e89c3-307">Windows</span><span class="sxs-lookup"><span data-stu-id="e89c3-307">Windows</span></span>](#tab/windows)

1. <span data-ttu-id="e89c3-308">Otwórz aplet **Dodaj lub usuń programy**.</span><span class="sxs-lookup"><span data-stu-id="e89c3-308">Open **Add or Remove Programs**.</span></span>
2. <span data-ttu-id="e89c3-309">Wyszukaj `Microsoft .NET Core SDK Uninstall Tool`.</span><span class="sxs-lookup"><span data-stu-id="e89c3-309">Search for `Microsoft .NET Core SDK Uninstall Tool`.</span></span>
3. <span data-ttu-id="e89c3-310">Wybierz pozycję **Odinstaluj**.</span><span class="sxs-lookup"><span data-stu-id="e89c3-310">Select **Uninstall**.</span></span>

## <a name="macostabmacos"></a>[<span data-ttu-id="e89c3-311">macOS</span><span class="sxs-lookup"><span data-stu-id="e89c3-311">macOS</span></span>](#tab/macos)

<span data-ttu-id="e89c3-312">Usuń pobrany plik *dotnet-Core-Uninstall. tar. gz* z katalogu, w którym został zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="e89c3-312">Delete the downloaded *dotnet-core-uninstall.tar.gz* file from the directory where it was installed.</span></span> <span data-ttu-id="e89c3-313">Jeśli zawartość tego pliku została rozpakowany do innego katalogu, pamiętaj, aby usunąć tę zawartość.</span><span class="sxs-lookup"><span data-stu-id="e89c3-313">If you unzipped the contents of this file into another directory, be sure to delete that content as well.</span></span>

---
