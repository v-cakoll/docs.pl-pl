---
title: Narzędzie Odinstalowywanie
description: Omówienie narzędzia .NET Core Uninstall Tool, narzędzia z przewodnikiem, które umożliwia kontrolowane oczyszczanie zestawów SDK i runtimes .NET Core.
author: sfoslund
ms.date: 01/06/2020
ms.openlocfilehash: bd20cba133cbb754dcca48e48b76a391a9efacba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847084"
---
# <a name="net-core-uninstall-tool"></a><span data-ttu-id="09750-103">Narzędzie do dezinstalacji platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="09750-103">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="09750-104">[Narzędzie .NET Core Uninstall Tool](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) umożliwia usunięcie sdk i uruchamiania programu .NET Core z systemu.</span><span class="sxs-lookup"><span data-stu-id="09750-104">The [.NET Core Uninstall Tool](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and Runtimes from a system.</span></span> <span data-ttu-id="09750-105">Dostępna jest kolekcja opcji określających wersje, które mają zostać odinstalowane.</span><span class="sxs-lookup"><span data-stu-id="09750-105">A collection of options is available to specify which versions you want to uninstall.</span></span>

<span data-ttu-id="09750-106">Narzędzie obsługuje systemy Windows i macOS.</span><span class="sxs-lookup"><span data-stu-id="09750-106">The tool supports Windows and macOS.</span></span> <span data-ttu-id="09750-107">Linux nie jest obecnie obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="09750-107">Linux is currently not supported.</span></span>

<span data-ttu-id="09750-108">W systemie Windows narzędzie może odinstalować tylko zestawy SDK i środowiska uruchomieniowe zainstalowane przy użyciu jednego z następujących instalatorów:</span><span class="sxs-lookup"><span data-stu-id="09750-108">On Windows, the tool can only uninstall SDKs and Runtimes that were installed using one of the following installers:</span></span>

- <span data-ttu-id="09750-109">Zestaw SDK .NET Core i instalator w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="09750-109">The .NET Core SDK and runtime installer.</span></span>
- <span data-ttu-id="09750-110">Instalator programu Visual Studio w wersjach wcześniejszych niż Visual Studio 2019 w wersji 16.3.</span><span class="sxs-lookup"><span data-stu-id="09750-110">The Visual Studio installer in versions earlier than Visual Studio 2019 version 16.3.</span></span>

<span data-ttu-id="09750-111">W systemie macOS narzędzie może odinstalować tylko zestawy SDK i programy uruchomieniowe znajdujące się w folderze */usr/local/share/dotnet.*</span><span class="sxs-lookup"><span data-stu-id="09750-111">On macOS, the tool can only uninstall SDKs and runtimes located in the */usr/local/share/dotnet* folder.</span></span>

<span data-ttu-id="09750-112">Z powodu tych ograniczeń narzędzie może nie być w stanie odinstalować wszystkich zestawów SDK i kręgów .NET Core na komputerze.</span><span class="sxs-lookup"><span data-stu-id="09750-112">Because of these limitations, the tool may not be able to uninstall all of the .NET Core SDKs and runtimes on your machine.</span></span> <span data-ttu-id="09750-113">Za pomocą `dotnet --info` polecenia można znaleźć wszystkie zainstalowane zestawy SDK i programy runi .NET Core, w tym zestawy SDK i programy wykonywania, których nie można usunąć w tym narzędziu.</span><span class="sxs-lookup"><span data-stu-id="09750-113">You can use the `dotnet --info` command to find all of the .NET Core SDKs and runtimes installed, including those SDKs and runtimes that this tool can't remove.</span></span> <span data-ttu-id="09750-114">Polecenie `dotnet-core-uninstall list` wyświetla, które zestawy SDK można odinstalować za pomocą narzędzia.</span><span class="sxs-lookup"><span data-stu-id="09750-114">The `dotnet-core-uninstall list` command displays which SDKs can be uninstalled with the tool.</span></span>

## <a name="install-the-tool"></a><span data-ttu-id="09750-115">Zainstaluj narzędzie</span><span class="sxs-lookup"><span data-stu-id="09750-115">Install the tool</span></span>

<span data-ttu-id="09750-116">Możesz pobrać narzędzie .NET Core Uninstall Tool [z tego miejsca](https://aka.ms/dotnet-core-uninstall-tool) i znaleźć kod źródłowy w repozytorium Github [dotnet/cli-lab.](https://github.com/dotnet/cli-lab)</span><span class="sxs-lookup"><span data-stu-id="09750-116">You can download the .NET Core Uninstall Tool from [here](https://aka.ms/dotnet-core-uninstall-tool) and find the source code at the [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub repository.</span></span>

> [!NOTE]
> <span data-ttu-id="09750-117">Narzędzie wymaga podniesienia uprawnień, aby odinstalować sdk .NET Core i kręgowych.</span><span class="sxs-lookup"><span data-stu-id="09750-117">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="09750-118">W związku z tym powinien być zainstalowany w katalogu chronionym przed zapisem, takim jak *C:\Program Files* w systemie Windows lub */usr/local/bin* w systemie macOS.</span><span class="sxs-lookup"><span data-stu-id="09750-118">Therefore, it should be installed in a write-protected directory such as *C:\Program Files* on Windows or */usr/local/bin* on macOS.</span></span> <span data-ttu-id="09750-119">Zobacz też [Podwyższony dostęp do poleceń dotnet](../tools/elevated-access.md).</span><span class="sxs-lookup"><span data-stu-id="09750-119">See also [Elevated access for dotnet commands](../tools/elevated-access.md).</span></span> <span data-ttu-id="09750-120">Aby uzyskać więcej informacji, zobacz [szczegółowe instrukcje instalacji](https://aka.ms/dotnet-core-uninstall-tool).</span><span class="sxs-lookup"><span data-stu-id="09750-120">For more information, see the [detailed installation instructions](https://aka.ms/dotnet-core-uninstall-tool).</span></span>

## <a name="run-the-tool"></a><span data-ttu-id="09750-121">Uruchamianie narzędzia</span><span class="sxs-lookup"><span data-stu-id="09750-121">Run the tool</span></span>

<span data-ttu-id="09750-122">W poniższych krokach przedstawiono zalecane podejście do uruchamiania narzędzia do odinstalowywania:</span><span class="sxs-lookup"><span data-stu-id="09750-122">The following steps show the recommended approach for running the uninstall tool:</span></span>

- [<span data-ttu-id="09750-123">Krok 1 — Wyświetlanie zainstalowanych zestawów SDK i runi .NET Core</span><span class="sxs-lookup"><span data-stu-id="09750-123">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>](#step-1---display-installed-net-core-sdks-and-runtimes)
- [<span data-ttu-id="09750-124">Krok 2 - Wykonaj suchy bieg</span><span class="sxs-lookup"><span data-stu-id="09750-124">Step 2 - Do a dry run</span></span>](#step-2---do-a-dry-run)
- [<span data-ttu-id="09750-125">Krok 3 — odinstalowywanie zestawów SDK i runi programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="09750-125">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>](#step-3---uninstall-net-core-sdks-and-runtimes)
- [<span data-ttu-id="09750-126">Krok 4 - Usuwanie folderu rezerwowego NuGet (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="09750-126">Step 4 - Delete the NuGet fallback folder (optional)</span></span>](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a><span data-ttu-id="09750-127">Krok 1 — Wyświetlanie zainstalowanych zestawów SDK i runi .NET Core</span><span class="sxs-lookup"><span data-stu-id="09750-127">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>

<span data-ttu-id="09750-128">Polecenie `dotnet-core-uninstall list` zawiera listę zainstalowanych zestawów SDK i uruchomień .NET Core, które można usunąć za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="09750-128">The `dotnet-core-uninstall list` command lists the installed .NET Core SDKs and runtimes that can be removed with this tool.</span></span> <span data-ttu-id="09750-129">Niektóre zestawy SDK i krępy mogą być wymagane przez program Visual Studio i są wyświetlane z notatką, dlaczego nie zaleca się ich odinstalowywania.</span><span class="sxs-lookup"><span data-stu-id="09750-129">Some SDKs and runtimes may be required by Visual Studio and they're displayed with a note of why it isn't recommended to uninstall them.</span></span>

<span data-ttu-id="09750-130">**lista dotnet-core-deinstall**</span><span class="sxs-lookup"><span data-stu-id="09750-130">**dotnet-core-uninstall list**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="09750-131">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="09750-131">Synopsis</span></span>

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a><span data-ttu-id="09750-132">Opcje</span><span class="sxs-lookup"><span data-stu-id="09750-132">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="09750-133">Windows</span><span class="sxs-lookup"><span data-stu-id="09750-133">Windows</span></span>](#tab/windows)

* **`--aspnet-runtime`**

  <span data-ttu-id="09750-134">Wyświetla listę wszystkich ASP.NET podstawowych uruchomień, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="09750-134">Lists all the ASP.NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="09750-135">Wyświetla listę wszystkich pakietów runowych i hostingowych .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="09750-135">Lists all the .NET Core runtime and hosting bundles that can be uninstalled with this tool.</span></span>

* **`--runtime`**

  <span data-ttu-id="09750-136">Wyświetla listę wszystkich uruchomień programu .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="09750-136">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="09750-137">Wyświetla listę wszystkich zestawów SDK .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="09750-137">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="09750-138">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="09750-138">Sets the verbosity level.</span></span> <span data-ttu-id="09750-139">Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i .</span><span class="sxs-lookup"><span data-stu-id="09750-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="09750-140">Wartością domyślną jest `normal`.</span><span class="sxs-lookup"><span data-stu-id="09750-140">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="09750-141">Wyświetla listę wszystkich zestawów SDK i zestawów RUN x64 .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="09750-141">Lists all x64 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

* **`--x86`**

  <span data-ttu-id="09750-142">Wyświetla listę wszystkich zestawów SDK i zestawów RUN x86 .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="09750-142">Lists all x86 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

## <a name="macos"></a>[<span data-ttu-id="09750-143">Macos</span><span class="sxs-lookup"><span data-stu-id="09750-143">macOS</span></span>](#tab/macos)

* **`--runtime`**

  <span data-ttu-id="09750-144">Wyświetla listę wszystkich uruchomień programu .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="09750-144">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="09750-145">Wyświetla listę wszystkich zestawów SDK .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="09750-145">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="09750-146">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="09750-146">Sets the verbosity level.</span></span> <span data-ttu-id="09750-147">Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i .</span><span class="sxs-lookup"><span data-stu-id="09750-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="09750-148">Wartością domyślną jest `normal`.</span><span class="sxs-lookup"><span data-stu-id="09750-148">The default value is `normal`.</span></span>
  
---

#### <a name="examples"></a><span data-ttu-id="09750-149">Przykłady</span><span class="sxs-lookup"><span data-stu-id="09750-149">Examples</span></span>

* <span data-ttu-id="09750-150">Lista wszystkich zestawów SDK i runi .NET Core, które można usunąć za pomocą tego narzędzia:</span><span class="sxs-lookup"><span data-stu-id="09750-150">List all .NET Core SDKs and runtimes that can be removed with this tool:</span></span>

  ```console
  dotnet-core-uninstall list
  ```

* <span data-ttu-id="09750-151">Lista wszystkich zestawów SDK i uruchomień x64 .NET Core:</span><span class="sxs-lookup"><span data-stu-id="09750-151">List all x64 .NET Core SDKs and runtimes:</span></span>

  ```console
  dotnet-core-uninstall list --x64
  ```

* <span data-ttu-id="09750-152">Lista wszystkich zestawów SDK x86 .NET Core:</span><span class="sxs-lookup"><span data-stu-id="09750-152">List all x86 .NET Core SDKs:</span></span>

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a><span data-ttu-id="09750-153">Krok 2 - Wykonaj suchy bieg</span><span class="sxs-lookup"><span data-stu-id="09750-153">Step 2 - Do a dry run</span></span>

<span data-ttu-id="09750-154">Polecenia `dotnet-core-uninstall dry-run` `dotnet-core-uninstall whatif` i wyświetlają zestawy SDK .NET Core i programy uruchomieniowe, które zostaną usunięte na podstawie dostępnych opcji bez odinstalowywania.</span><span class="sxs-lookup"><span data-stu-id="09750-154">The `dotnet-core-uninstall dry-run` and `dotnet-core-uninstall whatif` commands display the .NET Core SDKs and runtimes that will be removed based on the options provided without performing the uninstall.</span></span> <span data-ttu-id="09750-155">Polecenia te są synonimami.</span><span class="sxs-lookup"><span data-stu-id="09750-155">These commands are synonyms.</span></span>

<span data-ttu-id="09750-156">**dotnet-core-odinstalować suche uruchamianie i dotnet-core-odinstalować whatif**</span><span class="sxs-lookup"><span data-stu-id="09750-156">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="09750-157">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="09750-157">Synopsis</span></span>

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="09750-158">Argumenty</span><span class="sxs-lookup"><span data-stu-id="09750-158">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="09750-159">Określona wersja do odinstalowania.</span><span class="sxs-lookup"><span data-stu-id="09750-159">The specified version to uninstall.</span></span> <span data-ttu-id="09750-160">Można wyświetlić kilka wersji jeden po drugim, oddzielone spacjami.</span><span class="sxs-lookup"><span data-stu-id="09750-160">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="09750-161">Pliki odpowiedzi są również obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="09750-161">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="09750-162">Pliki odpowiedzi są alternatywą dla umieszczenia wszystkich wersji w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="09750-162">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="09750-163">Są to pliki tekstowe, zazwyczaj \*z rozszerzeniem .rsp, a każda wersja jest wyświetlana w osobnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="09750-163">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="09750-164">Aby określić plik odpowiedzi `VERSION` dla argumentu, użyj \@ znaku, po którym natychmiast następuje nazwa pliku odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="09750-164">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="09750-165">Opcje</span><span class="sxs-lookup"><span data-stu-id="09750-165">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="09750-166">Windows</span><span class="sxs-lookup"><span data-stu-id="09750-166">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="09750-167">Usuwa wszystkie zestawy SDK i programy wykonywania programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="09750-167">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="09750-168">Usuwa tylko zestawy SDK i programy wykonywania .NET Core z wersją mniejszą niż określona wersja.</span><span class="sxs-lookup"><span data-stu-id="09750-168">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="09750-169">Określona wersja pozostaje zainstalowana.</span><span class="sxs-lookup"><span data-stu-id="09750-169">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="09750-170">Usuwa wszystkie zestawy SDK i programy wykonywania programu .NET Core, z wyjątkiem określonych wersji.</span><span class="sxs-lookup"><span data-stu-id="09750-170">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="09750-171">Usuwa zestawy SDK i programy wykonywania .NET Core, z wyjątkiem jednej najwyższej wersji.</span><span class="sxs-lookup"><span data-stu-id="09750-171">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="09750-172">Usuwa zestawy SDK .NET Core i uruchamiane przez wyższe poprawki.</span><span class="sxs-lookup"><span data-stu-id="09750-172">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="09750-173">Ta opcja chroni global.json.</span><span class="sxs-lookup"><span data-stu-id="09750-173">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="09750-174">Usuwa zestawy SDK .NET Core i uruchamiane jako podglądy.</span><span class="sxs-lookup"><span data-stu-id="09750-174">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="09750-175">Usuwa zestawy SDK .NET Core i uruchamiane jako podglądy z wyjątkiem jednego najwyższego podglądu.</span><span class="sxs-lookup"><span data-stu-id="09750-175">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="09750-176">Usuwa tylko ASP.NET core.Removes ASP.NET Core runtimes only.</span><span class="sxs-lookup"><span data-stu-id="09750-176">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="09750-177">Usuwa tylko pakiety uruchomieniowe programu .NET Core i hosting.</span><span class="sxs-lookup"><span data-stu-id="09750-177">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="09750-178">Usuwa zestawy SDK .NET Core i uruchamiane, które są zgodne z określoną `major.minor` wersją.</span><span class="sxs-lookup"><span data-stu-id="09750-178">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="09750-179">Usuwa tylko uruchamianie programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="09750-179">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="09750-180">Usuwa tylko zestawy SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="09750-180">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="09750-181">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="09750-181">Sets the verbosity level.</span></span> <span data-ttu-id="09750-182">Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i .</span><span class="sxs-lookup"><span data-stu-id="09750-182">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="09750-183">Wartością domyślną jest `normal`.</span><span class="sxs-lookup"><span data-stu-id="09750-183">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="09750-184">Musi być `--sdk`używany `--runtime`z `--aspnet-runtime` , , i usunąć x64 SDK sdk lub kręgów.</span><span class="sxs-lookup"><span data-stu-id="09750-184">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="09750-185">Musi być `--sdk`używany `--runtime`z `--aspnet-runtime` , , i usunąć x86 SDK sdk lub kręgów.</span><span class="sxs-lookup"><span data-stu-id="09750-185">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="09750-186">**`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="09750-186">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="09750-187">Uwagi:</span><span class="sxs-lookup"><span data-stu-id="09750-187">Notes:</span></span>

1. <span data-ttu-id="09750-188">Dokładnie jeden `--sdk` `--runtime`z `--aspnet-runtime`, `--hosting-bundle` , i jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="09750-188">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="09750-189">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , i są wyłączne.</span><span class="sxs-lookup"><span data-stu-id="09750-189">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="09750-190">Jeśli `--x64` `--x86` lub nie są określone, a następnie x64 i x86 zostaną usunięte.</span><span class="sxs-lookup"><span data-stu-id="09750-190">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="09750-191">Macos</span><span class="sxs-lookup"><span data-stu-id="09750-191">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="09750-192">Usuwa wszystkie zestawy SDK i programy wykonywania programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="09750-192">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="09750-193">Usuwa zestawy SDK i programy wykonywania .NET Core poniżej określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="09750-193">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="09750-194">Określona wersja pozostanie.</span><span class="sxs-lookup"><span data-stu-id="09750-194">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="09750-195">Usuwa zestawy SDK i programy wykonywania .NET Core, z wyjątkiem określonych wersji.</span><span class="sxs-lookup"><span data-stu-id="09750-195">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="09750-196">Usuwa zestawy SDK i programy wykonywania .NET Core, z wyjątkiem jednej najwyższej wersji.</span><span class="sxs-lookup"><span data-stu-id="09750-196">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="09750-197">Usuwa zestawy SDK .NET Core i uruchamiane przez wyższe poprawki.</span><span class="sxs-lookup"><span data-stu-id="09750-197">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="09750-198">Ta opcja chroni global.json.</span><span class="sxs-lookup"><span data-stu-id="09750-198">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="09750-199">Usuwa zestawy SDK .NET Core i uruchamiane jako podglądy.</span><span class="sxs-lookup"><span data-stu-id="09750-199">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="09750-200">Usuwa zestawy SDK .NET Core i uruchamiane jako podglądy z wyjątkiem jednego najwyższego podglądu.</span><span class="sxs-lookup"><span data-stu-id="09750-200">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="09750-201">Usuwa zestawy SDK .NET Core i uruchamiane, które są zgodne z określoną `major.minor` wersją.</span><span class="sxs-lookup"><span data-stu-id="09750-201">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="09750-202">Usuwa tylko uruchamianie programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="09750-202">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="09750-203">Usuwa tylko zestawy SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="09750-203">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="09750-204">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="09750-204">Sets the verbosity level.</span></span> <span data-ttu-id="09750-205">Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i .</span><span class="sxs-lookup"><span data-stu-id="09750-205">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="09750-206">Wartością domyślną jest `normal`.</span><span class="sxs-lookup"><span data-stu-id="09750-206">The default value is `normal`.</span></span>
  
* <span data-ttu-id="09750-207">**`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio lub SDK.</span><span class="sxs-lookup"><span data-stu-id="09750-207">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="09750-208">Uwagi:</span><span class="sxs-lookup"><span data-stu-id="09750-208">Notes:</span></span>

1. <span data-ttu-id="09750-209">Dokładnie jeden `--sdk` `--runtime` z i jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="09750-209">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="09750-210">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , i są wyłączne.</span><span class="sxs-lookup"><span data-stu-id="09750-210">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="09750-211">Przykłady</span><span class="sxs-lookup"><span data-stu-id="09750-211">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="09750-212">Domyślnie zestawy SDK .NET Core i uruchamianie, które mogą być wymagane przez `dotnet-core-uninstall dry-run` program Visual Studio lub inne zestawy SDK, nie są uwzględniane w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="09750-212">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are not included in `dotnet-core-uninstall dry-run` output.</span></span> <span data-ttu-id="09750-213">W poniższych przykładach niektóre z określonych zestawów SDK i runtimes nie mogą być uwzględnione w danych wyjściowych, w zależności od stanu komputera.</span><span class="sxs-lookup"><span data-stu-id="09750-213">In the following examples, some of the specified SDKs and runtimes may not be included in the output, depending on the state of the machine.</span></span> <span data-ttu-id="09750-214">Aby uwzględnić wszystkie zestawy SDK i czas wykonywania, `--force` należy wyświetlić je jawnie jako argumenty lub użyć tej opcji.</span><span class="sxs-lookup"><span data-stu-id="09750-214">To include all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="09750-215">Suchy przebieg usuwania wszystkich środowiska uruchomieniowego .NET Core, które zostały zastąpione przez wyższe poprawki:</span><span class="sxs-lookup"><span data-stu-id="09750-215">Dry run of removing all .NET Core runtimes that have been superseded by higher patches:</span></span>

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* <span data-ttu-id="09750-216">Suchy przebieg usuwania wszystkich zestawów SDK .NET Core poniżej wersji: `2.2.301`</span><span class="sxs-lookup"><span data-stu-id="09750-216">Dry run of removing all .NET Core SDKs below the version `2.2.301`:</span></span>

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a><span data-ttu-id="09750-217">Krok 3 — odinstalowywanie zestawów SDK i runi programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="09750-217">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>

<span data-ttu-id="09750-218">`dotnet-core-uninstall remove`odinstalowuje zestawy SDK .NET Core i runtimes, które są określone przez zbiór opcji.</span><span class="sxs-lookup"><span data-stu-id="09750-218">`dotnet-core-uninstall remove` uninstalls .NET Core SDKs and Runtimes that are specified by a collection of options.</span></span> <span data-ttu-id="09750-219">Nie można użyć narzędzia do odinstalowywania zestawów SDK i uruchomień w wersji 5.0 lub wyższej.</span><span class="sxs-lookup"><span data-stu-id="09750-219">The tool can't be used to uninstall SDKs and Runtimes with version 5.0 or above.</span></span>

<span data-ttu-id="09750-220">Ponieważ to narzędzie ma destrukcyjne zachowanie, **zdecydowanie** zaleca się wykonanie biegu na sucho przed uruchomieniem polecenia usuwania.</span><span class="sxs-lookup"><span data-stu-id="09750-220">Since this tool has a destructive behavior, it's **highly** recommended that you do a dry run before running the remove command.</span></span> <span data-ttu-id="09750-221">Uruchamianie na sucho pokaże, jakie zestawy SDK i środowiska `remove` uruchomieniowe .NET Core zostaną usunięte podczas korzystania z polecenia.</span><span class="sxs-lookup"><span data-stu-id="09750-221">The dry run will show you what .NET Core SDKs and runtimes will be removed when you use the `remove` command.</span></span> <span data-ttu-id="09750-222">Odnoszą się do [Czy należy usunąć wersję?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version)</span><span class="sxs-lookup"><span data-stu-id="09750-222">Refer to [Should I remove a version?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version) to learn which SDKs and runtimes are safe to remove.</span></span>

> [!CAUTION]
> <span data-ttu-id="09750-223">Należy pamiętać o następujących zastrzeżeniach:</span><span class="sxs-lookup"><span data-stu-id="09750-223">Keep in mind the following caveats:</span></span>
>
>- <span data-ttu-id="09750-224">To narzędzie może odinstalować wersje zestawu SDK `global.json` .NET Core, które są wymagane przez pliki na komputerze.</span><span class="sxs-lookup"><span data-stu-id="09750-224">This tool can uninstall versions of the .NET Core SDK that are required by `global.json` files on your machine.</span></span> <span data-ttu-id="09750-225">Zestawy SDK programu .NET Core można ponownie zainstalować na stronie [Pobierz program .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)</span><span class="sxs-lookup"><span data-stu-id="09750-225">You can reinstall .NET Core SDKs from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="09750-226">To narzędzie można odinstalować wersje programu .NET Core, które są wymagane przez aplikacje zależne od struktury na komputerze.</span><span class="sxs-lookup"><span data-stu-id="09750-226">This tool can uninstall versions of the .NET Core runtime that are required by framework dependent applications on your machine.</span></span> <span data-ttu-id="09750-227">Czas wykonywania programu .NET Core można ponownie zainstalować na stronie [Pobieranie programu .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)</span><span class="sxs-lookup"><span data-stu-id="09750-227">You can reinstall .NET Core runtimes from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="09750-228">To narzędzie można odinstalować wersje zestawu SDK .NET Core i w czasie wykonywania, na których opiera się program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="09750-228">This tool can uninstall versions of the .NET Core SDK and runtime that Visual Studio relies on.</span></span> <span data-ttu-id="09750-229">Jeśli przerwiesz instalację programu Visual Studio, uruchom "Naprawę" w instalatorze programu Visual Studio, aby powrócić do stanu roboczego.</span><span class="sxs-lookup"><span data-stu-id="09750-229">If you break your Visual Studio installation, run "Repair" in the Visual Studio installer to get back to a working state.</span></span>

<span data-ttu-id="09750-230">Domyślnie wszystkie polecenia zachowują zestawy SDK i kręgowych .NET Core, które mogą być wymagane przez program Visual Studio lub inne zestawy SDK.</span><span class="sxs-lookup"><span data-stu-id="09750-230">By default, all commands keep the .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs.</span></span> <span data-ttu-id="09750-231">Te zestawy SDK i krępy można odinstalować, `--force` wymieniając je jawnie jako argumenty lub za pomocą tej opcji.</span><span class="sxs-lookup"><span data-stu-id="09750-231">These SDKs and runtimes can be uninstalled by listing them explicitly as arguments or by using the `--force` option.</span></span>

<span data-ttu-id="09750-232">Narzędzie wymaga podniesienia uprawnień, aby odinstalować sdk .NET Core i kręgowych.</span><span class="sxs-lookup"><span data-stu-id="09750-232">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="09750-233">Uruchom narzędzie w wierszu polecenia Administrator `sudo` w systemie Windows i w systemie macOS.</span><span class="sxs-lookup"><span data-stu-id="09750-233">Run the tool in an Administrator command prompt on Windows and with `sudo` on macOS.</span></span> <span data-ttu-id="09750-234">Polecenia `dry-run` `whatif` i nie wymagają podniesienia wysokości.</span><span class="sxs-lookup"><span data-stu-id="09750-234">The `dry-run` and `whatif` commands don't require elevation.</span></span>

<span data-ttu-id="09750-235">**usuwanie dotnet-core-deinstall**</span><span class="sxs-lookup"><span data-stu-id="09750-235">**dotnet-core-uninstall remove**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="09750-236">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="09750-236">Synopsis</span></span>

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="09750-237">Argumenty</span><span class="sxs-lookup"><span data-stu-id="09750-237">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="09750-238">Określona wersja do odinstalowania.</span><span class="sxs-lookup"><span data-stu-id="09750-238">The specified version to uninstall.</span></span> <span data-ttu-id="09750-239">Można wyświetlić kilka wersji jeden po drugim, oddzielone spacjami.</span><span class="sxs-lookup"><span data-stu-id="09750-239">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="09750-240">Pliki odpowiedzi są również obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="09750-240">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="09750-241">Pliki odpowiedzi są alternatywą dla umieszczenia wszystkich wersji w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="09750-241">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="09750-242">Są to pliki tekstowe, zazwyczaj \*z rozszerzeniem .rsp, a każda wersja jest wyświetlana w osobnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="09750-242">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="09750-243">Aby określić plik odpowiedzi `VERSION` dla argumentu, użyj \@ znaku, po którym natychmiast następuje nazwa pliku odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="09750-243">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="09750-244">Opcje</span><span class="sxs-lookup"><span data-stu-id="09750-244">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="09750-245">Windows</span><span class="sxs-lookup"><span data-stu-id="09750-245">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="09750-246">Usuwa wszystkie zestawy SDK i programy wykonywania programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="09750-246">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="09750-247">Usuwa tylko zestawy SDK i programy wykonywania .NET Core z wersją mniejszą niż określona wersja.</span><span class="sxs-lookup"><span data-stu-id="09750-247">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="09750-248">Określona wersja pozostaje zainstalowana.</span><span class="sxs-lookup"><span data-stu-id="09750-248">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="09750-249">Usuwa wszystkie zestawy SDK i programy wykonywania programu .NET Core, z wyjątkiem określonych wersji.</span><span class="sxs-lookup"><span data-stu-id="09750-249">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="09750-250">Usuwa zestawy SDK i programy wykonywania .NET Core, z wyjątkiem jednej najwyższej wersji.</span><span class="sxs-lookup"><span data-stu-id="09750-250">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="09750-251">Usuwa zestawy SDK .NET Core i uruchamiane przez wyższe poprawki.</span><span class="sxs-lookup"><span data-stu-id="09750-251">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="09750-252">Ta opcja chroni global.json.</span><span class="sxs-lookup"><span data-stu-id="09750-252">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="09750-253">Usuwa zestawy SDK .NET Core i uruchamiane jako podglądy.</span><span class="sxs-lookup"><span data-stu-id="09750-253">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="09750-254">Usuwa zestawy SDK .NET Core i uruchamiane jako podglądy z wyjątkiem jednego najwyższego podglądu.</span><span class="sxs-lookup"><span data-stu-id="09750-254">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="09750-255">Usuwa tylko ASP.NET core.Removes ASP.NET Core runtimes only.</span><span class="sxs-lookup"><span data-stu-id="09750-255">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="09750-256">Usuwa tylko pakiety uruchomieniowe programu .NET Core i hosting.</span><span class="sxs-lookup"><span data-stu-id="09750-256">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="09750-257">Usuwa zestawy SDK .NET Core i uruchamiane, które są zgodne z określoną `major.minor` wersją.</span><span class="sxs-lookup"><span data-stu-id="09750-257">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="09750-258">Usuwa tylko uruchamianie programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="09750-258">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="09750-259">Usuwa tylko zestawy SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="09750-259">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="09750-260">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="09750-260">Sets the verbosity level.</span></span> <span data-ttu-id="09750-261">Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i .</span><span class="sxs-lookup"><span data-stu-id="09750-261">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="09750-262">Wartością domyślną jest `normal`.</span><span class="sxs-lookup"><span data-stu-id="09750-262">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="09750-263">Musi być `--sdk`używany `--runtime`z `--aspnet-runtime` , , i usunąć x64 SDK sdk lub kręgów.</span><span class="sxs-lookup"><span data-stu-id="09750-263">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="09750-264">Musi być `--sdk`używany `--runtime`z `--aspnet-runtime` , , i usunąć x86 SDK sdk lub kręgów.</span><span class="sxs-lookup"><span data-stu-id="09750-264">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="09750-265">**`-y, --yes`** Wykonuje polecenie bez konieczności potwierdzenia tak lub nie.</span><span class="sxs-lookup"><span data-stu-id="09750-265">**`-y, --yes`** Executes the command without requiring a yes or no confirmation.</span></span>

* <span data-ttu-id="09750-266">**`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="09750-266">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="09750-267">Uwagi:</span><span class="sxs-lookup"><span data-stu-id="09750-267">Notes:</span></span>

1. <span data-ttu-id="09750-268">Dokładnie jeden `--sdk` `--runtime`z `--aspnet-runtime`, `--hosting-bundle` , i jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="09750-268">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="09750-269">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , i są wyłączne.</span><span class="sxs-lookup"><span data-stu-id="09750-269">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="09750-270">Jeśli `--x64` `--x86` lub nie są określone, a następnie x64 i x86 zostaną usunięte.</span><span class="sxs-lookup"><span data-stu-id="09750-270">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="09750-271">Macos</span><span class="sxs-lookup"><span data-stu-id="09750-271">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="09750-272">Usuwa wszystkie zestawy SDK i programy wykonywania programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="09750-272">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="09750-273">Usuwa zestawy SDK i programy wykonywania .NET Core poniżej określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="09750-273">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="09750-274">Określona wersja pozostanie.</span><span class="sxs-lookup"><span data-stu-id="09750-274">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="09750-275">Usuwa zestawy SDK i programy wykonywania .NET Core, z wyjątkiem określonych wersji.</span><span class="sxs-lookup"><span data-stu-id="09750-275">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="09750-276">Usuwa zestawy SDK i programy wykonywania .NET Core, z wyjątkiem jednej najwyższej wersji.</span><span class="sxs-lookup"><span data-stu-id="09750-276">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="09750-277">Usuwa zestawy SDK .NET Core i uruchamiane przez wyższe poprawki.</span><span class="sxs-lookup"><span data-stu-id="09750-277">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="09750-278">Ta opcja chroni global.json.</span><span class="sxs-lookup"><span data-stu-id="09750-278">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="09750-279">Usuwa zestawy SDK .NET Core i uruchamiane jako podglądy.</span><span class="sxs-lookup"><span data-stu-id="09750-279">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="09750-280">Usuwa zestawy SDK .NET Core i uruchamiane jako podglądy z wyjątkiem jednego najwyższego podglądu.</span><span class="sxs-lookup"><span data-stu-id="09750-280">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="09750-281">Usuwa zestawy SDK .NET Core i uruchamiane, które są zgodne z określoną `major.minor` wersją.</span><span class="sxs-lookup"><span data-stu-id="09750-281">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="09750-282">Usuwa tylko uruchamianie programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="09750-282">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="09750-283">Usuwa tylko zestawy SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="09750-283">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="09750-284">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="09750-284">Sets the verbosity level.</span></span> <span data-ttu-id="09750-285">Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i .</span><span class="sxs-lookup"><span data-stu-id="09750-285">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="09750-286">Wartością domyślną jest `normal`.</span><span class="sxs-lookup"><span data-stu-id="09750-286">The default value is `normal`.</span></span>

* <span data-ttu-id="09750-287">**`-y, --yes`** Wykonuje polecenie bez konieczności potwierdzenia Y/N.</span><span class="sxs-lookup"><span data-stu-id="09750-287">**`-y, --yes`** Executes the command without requiring Y/N confirmation.</span></span>
  
* <span data-ttu-id="09750-288">**`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio lub SDK.</span><span class="sxs-lookup"><span data-stu-id="09750-288">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="09750-289">Uwagi:</span><span class="sxs-lookup"><span data-stu-id="09750-289">Notes:</span></span>

1. <span data-ttu-id="09750-290">Dokładnie jeden `--sdk` `--runtime` z i jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="09750-290">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="09750-291">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , i są wyłączne.</span><span class="sxs-lookup"><span data-stu-id="09750-291">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="09750-292">Przykłady</span><span class="sxs-lookup"><span data-stu-id="09750-292">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="09750-293">Domyślnie zestawy SDK .NET Core i uruchamianie, które mogą być wymagane przez program Visual Studio lub inne zestawy SDK są przechowywane.</span><span class="sxs-lookup"><span data-stu-id="09750-293">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are kept.</span></span> <span data-ttu-id="09750-294">W poniższych przykładach niektóre z określonych zestawów SDK i runtimes może pozostać, w zależności od stanu komputera.</span><span class="sxs-lookup"><span data-stu-id="09750-294">In the following examples, some of the specified SDKs and runtimes may remain, depending on the state of the machine.</span></span> <span data-ttu-id="09750-295">Aby usunąć wszystkie zestawy SDK i czas wykonywania, `--force` należy wyświetlić je jawnie jako argumenty lub użyć tej opcji.</span><span class="sxs-lookup"><span data-stu-id="09750-295">To remove all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="09750-296">Usuń wszystkie uruchomienia programu .NET `3.0.0-preview6-27804-01` Core z wyjątkiem wersji bez konieczności potwierdzenia przez Wartość Y/N:</span><span class="sxs-lookup"><span data-stu-id="09750-296">Remove all .NET Core runtimes except the version `3.0.0-preview6-27804-01` without requiring Y/N confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* <span data-ttu-id="09750-297">Usuń wszystkie zestawy SDK .NET Core 1.1 bez konieczności potwierdzenia przez wartość Y/n:</span><span class="sxs-lookup"><span data-stu-id="09750-297">Remove all .NET Core 1.1 SDKs without requiring Y/n confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* <span data-ttu-id="09750-298">Usuń zestaw SDK .NET Core 1.1.11 bez wyjścia konsoli:</span><span class="sxs-lookup"><span data-stu-id="09750-298">Remove the .NET Core 1.1.11 SDK with no console output:</span></span>

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* <span data-ttu-id="09750-299">Usuń wszystkie zestawy SDK .NET Core, które można bezpiecznie usunąć za pomocą tego narzędzia:</span><span class="sxs-lookup"><span data-stu-id="09750-299">Remove all .NET Core SDKs that can safely be removed by this tool:</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* <span data-ttu-id="09750-300">Usuń wszystkie zestawy SDK .NET Core, które mogą zostać usunięte przez to narzędzie, w tym zestawy SDK, które mogą być wymagane przez program Visual Studio (nie zalecane):</span><span class="sxs-lookup"><span data-stu-id="09750-300">Remove all .NET Core SDKs that can be removed by this tool, including those SDKs that may be required by Visual Studio (not recommended):</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* <span data-ttu-id="09750-301">Usuwanie wszystkich zestawów SDK programu .NET Core określonych w pliku odpowiedzi`versions.rsp`</span><span class="sxs-lookup"><span data-stu-id="09750-301">Remove all .NET Core SDKs that are specified in the response file `versions.rsp`</span></span>

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  <span data-ttu-id="09750-302">Zawartość *versions.rsp* jest następująca:</span><span class="sxs-lookup"><span data-stu-id="09750-302">The content of *versions.rsp* is as follows:</span></span>
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a><span data-ttu-id="09750-303">Krok 4 - Usuwanie folderu rezerwowego NuGet (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="09750-303">Step 4 - Delete the NuGet fallback folder (optional)</span></span>

<span data-ttu-id="09750-304">W niektórych przypadkach nie potrzebujesz `NuGetFallbackFolder` już i możesz chcieć go usunąć.</span><span class="sxs-lookup"><span data-stu-id="09750-304">In some cases, you no longer need the `NuGetFallbackFolder` and may wish to delete it.</span></span> <span data-ttu-id="09750-305">Aby uzyskać więcej informacji na temat usuwania tego folderu, zobacz [Usuwanie NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span><span class="sxs-lookup"><span data-stu-id="09750-305">For more information about deleting this folder, see [Remove the NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span></span>

## <a name="uninstall-the-tool"></a><span data-ttu-id="09750-306">Odinstaluj narzędzie</span><span class="sxs-lookup"><span data-stu-id="09750-306">Uninstall the tool</span></span>

## <a name="windows"></a>[<span data-ttu-id="09750-307">Windows</span><span class="sxs-lookup"><span data-stu-id="09750-307">Windows</span></span>](#tab/windows)

1. <span data-ttu-id="09750-308">Otwórz **pozycję Dodaj lub usuń programy**.</span><span class="sxs-lookup"><span data-stu-id="09750-308">Open **Add or Remove Programs**.</span></span>
2. <span data-ttu-id="09750-309">Wyszukaj `Microsoft .NET Core SDK Uninstall Tool`.</span><span class="sxs-lookup"><span data-stu-id="09750-309">Search for `Microsoft .NET Core SDK Uninstall Tool`.</span></span>
3. <span data-ttu-id="09750-310">Wybierz **pozycję Odinstaluj**.</span><span class="sxs-lookup"><span data-stu-id="09750-310">Select **Uninstall**.</span></span>

## <a name="macos"></a>[<span data-ttu-id="09750-311">Macos</span><span class="sxs-lookup"><span data-stu-id="09750-311">macOS</span></span>](#tab/macos)

<span data-ttu-id="09750-312">Usuń pobrany plik *dotnet-core-uninstall.tar.gz* z katalogu, w którym został zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="09750-312">Delete the downloaded *dotnet-core-uninstall.tar.gz* file from the directory where it was installed.</span></span> <span data-ttu-id="09750-313">Jeśli zawartość tego pliku zostanie rozpakowana do innego katalogu, należy również usunąć tę zawartość.</span><span class="sxs-lookup"><span data-stu-id="09750-313">If you unzipped the contents of this file into another directory, be sure to delete that content as well.</span></span>

---
