---
title: Narzędzie do odinstalowywania
description: Omówienie narzędzia do odinstalowywania platformy .NET Core, narzędzia z przewodnikiem, które umożliwia kontrolowane czyszczenie zestawów SDK i środowiska uruchomieniowego platformy .NET Core.
author: sfoslund
ms.date: 01/06/2020
ms.openlocfilehash: 45cf0841391d02636770e98666e2897d2598fab4
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595718"
---
# <a name="net-core-uninstall-tool"></a><span data-ttu-id="d995a-103">Narzędzie do dezinstalacji platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="d995a-103">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="d995a-104">[Narzędzie do dezinstalacji programu .NET Core](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) umożliwia usuwanie zestawów SDK i środowisk uruchomieniowych platformy .NET Core z systemu.</span><span class="sxs-lookup"><span data-stu-id="d995a-104">The [.NET Core Uninstall Tool](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and Runtimes from a system.</span></span> <span data-ttu-id="d995a-105">Dostępna jest kolekcja opcji, aby określić wersje, które mają zostać odinstalowane.</span><span class="sxs-lookup"><span data-stu-id="d995a-105">A collection of options is available to specify which versions you want to uninstall.</span></span>

<span data-ttu-id="d995a-106">Narzędzie obsługuje systemy Windows i macOS.</span><span class="sxs-lookup"><span data-stu-id="d995a-106">The tool supports Windows and macOS.</span></span> <span data-ttu-id="d995a-107">System Linux nie jest obecnie obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="d995a-107">Linux is currently not supported.</span></span>

<span data-ttu-id="d995a-108">W systemie Windows narzędzie może odinstalować tylko zestawy SDK i środowiska uruchomieniowe, które zostały zainstalowane przy użyciu jednego z następujących instalatorów:</span><span class="sxs-lookup"><span data-stu-id="d995a-108">On Windows, the tool can only uninstall SDKs and Runtimes that were installed using one of the following installers:</span></span>

- <span data-ttu-id="d995a-109">Zestaw .NET Core SDK i Instalator środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="d995a-109">The .NET Core SDK and runtime installer.</span></span>
- <span data-ttu-id="d995a-110">Instalator programu Visual Studio w wersji wcześniejszej niż program Visual Studio 2019 w wersji 16,3.</span><span class="sxs-lookup"><span data-stu-id="d995a-110">The Visual Studio installer in versions earlier than Visual Studio 2019 version 16.3.</span></span>

<span data-ttu-id="d995a-111">W systemie macOS narzędzie może odinstalować tylko zestawy SDK i środowiska uruchomieniowe znajdujące się w folderze */usr/local/share/dotnet* .</span><span class="sxs-lookup"><span data-stu-id="d995a-111">On macOS, the tool can only uninstall SDKs and runtimes located in the */usr/local/share/dotnet* folder.</span></span>

<span data-ttu-id="d995a-112">Ze względu na te ograniczenia narzędzie może nie być w stanie odinstalować wszystkich zestawów SDK i środowisk uruchomieniowych platformy .NET Core na komputerze.</span><span class="sxs-lookup"><span data-stu-id="d995a-112">Because of these limitations, the tool may not be able to uninstall all of the .NET Core SDKs and runtimes on your machine.</span></span> <span data-ttu-id="d995a-113">Możesz użyć `dotnet --info` polecenia, aby znaleźć wszystkie zainstalowane zestawy SDK .NET Core i środowiska uruchomieniowe, w tym zestawy SDK i środowiska uruchomieniowe, których to narzędzie nie może usunąć.</span><span class="sxs-lookup"><span data-stu-id="d995a-113">You can use the `dotnet --info` command to find all of the .NET Core SDKs and runtimes installed, including those SDKs and runtimes that this tool can't remove.</span></span> <span data-ttu-id="d995a-114">`dotnet-core-uninstall list` Polecenie wyświetla listę zestawów SDK, które można odinstalować za pomocą narzędzia.</span><span class="sxs-lookup"><span data-stu-id="d995a-114">The `dotnet-core-uninstall list` command displays which SDKs can be uninstalled with the tool.</span></span>

## <a name="install-the-tool"></a><span data-ttu-id="d995a-115">Zainstaluj narzędzie</span><span class="sxs-lookup"><span data-stu-id="d995a-115">Install the tool</span></span>

<span data-ttu-id="d995a-116">W [tym miejscu](https://aka.ms/dotnet-core-uninstall-tool) możesz pobrać narzędzie do odinstalowywania platformy .NET Core i znaleźć kod źródłowy w repozytorium GitHub [/CLI-Lab](https://github.com/dotnet/cli-lab) .</span><span class="sxs-lookup"><span data-stu-id="d995a-116">You can download the .NET Core Uninstall Tool from [here](https://aka.ms/dotnet-core-uninstall-tool) and find the source code at the [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub repository.</span></span>

> [!NOTE]
> <span data-ttu-id="d995a-117">Narzędzie wymaga podniesienia uprawnień, aby odinstalować zestawy SDK i środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d995a-117">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="d995a-118">W związku z tym należy ją zainstalować w katalogu chronionym przed zapisem, takim jak *C:\Program Files* w systemie Windows lub */usr/local/bin* na macOS.</span><span class="sxs-lookup"><span data-stu-id="d995a-118">Therefore, it should be installed in a write-protected directory such as *C:\Program Files* on Windows or */usr/local/bin* on macOS.</span></span> <span data-ttu-id="d995a-119">Zobacz również [podwyższony poziom dostępu dla poleceń dotnet](../tools/elevated-access.md).</span><span class="sxs-lookup"><span data-stu-id="d995a-119">See also [Elevated access for dotnet commands](../tools/elevated-access.md).</span></span> <span data-ttu-id="d995a-120">Aby uzyskać więcej informacji, zobacz [szczegółowe instrukcje dotyczące instalacji](https://aka.ms/dotnet-core-uninstall-tool).</span><span class="sxs-lookup"><span data-stu-id="d995a-120">For more information, see the [detailed installation instructions](https://aka.ms/dotnet-core-uninstall-tool).</span></span>

## <a name="run-the-tool"></a><span data-ttu-id="d995a-121">Uruchamianie narzędzia</span><span class="sxs-lookup"><span data-stu-id="d995a-121">Run the tool</span></span>

<span data-ttu-id="d995a-122">W poniższych krokach przedstawiono zalecane podejście do uruchamiania narzędzia do odinstalowywania:</span><span class="sxs-lookup"><span data-stu-id="d995a-122">The following steps show the recommended approach for running the uninstall tool:</span></span>

- [<span data-ttu-id="d995a-123">Krok 1. wyświetlanie zainstalowanych zestawów SDK i środowisk uruchomieniowych platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="d995a-123">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>](#step-1---display-installed-net-core-sdks-and-runtimes)
- [<span data-ttu-id="d995a-124">Krok 2 — wykonywanie suchego przebiegu</span><span class="sxs-lookup"><span data-stu-id="d995a-124">Step 2 - Do a dry run</span></span>](#step-2---do-a-dry-run)
- [<span data-ttu-id="d995a-125">Krok 3 — Odinstalowywanie zestawów SDK i środowisk uruchomieniowych platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="d995a-125">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>](#step-3---uninstall-net-core-sdks-and-runtimes)
- [<span data-ttu-id="d995a-126">Krok 4. Usuwanie folderu rezerwowego NuGet (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="d995a-126">Step 4 - Delete the NuGet fallback folder (optional)</span></span>](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a><span data-ttu-id="d995a-127">Krok 1. wyświetlanie zainstalowanych zestawów SDK i środowisk uruchomieniowych platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="d995a-127">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>

<span data-ttu-id="d995a-128">`dotnet-core-uninstall list` Polecenie wyświetla listę zainstalowanych zestawów SDK .NET Core i środowiska uruchomieniowe, które można usunąć za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="d995a-128">The `dotnet-core-uninstall list` command lists the installed .NET Core SDKs and runtimes that can be removed with this tool.</span></span> <span data-ttu-id="d995a-129">Niektóre zestawy SDK i środowiska uruchomieniowe mogą być wymagane przez program Visual Studio i są wyświetlane z zawarto adnotacją dlaczego nie zaleca się ich odinstalowywania.</span><span class="sxs-lookup"><span data-stu-id="d995a-129">Some SDKs and runtimes may be required by Visual Studio and they're displayed with a note of why it isn't recommended to uninstall them.</span></span>

> [!NOTE]
> <span data-ttu-id="d995a-130">Dane wyjściowe `dotnet-core-uninstall list` polecenia nie będą zgodne z listą zainstalowanych wersji w danych wyjściowych `dotnet --info` w większości przypadków.</span><span class="sxs-lookup"><span data-stu-id="d995a-130">The output of the `dotnet-core-uninstall list` command will not match the list of installed versions in the output of `dotnet --info` in most cases.</span></span> <span data-ttu-id="d995a-131">W przypadku tego narzędzia nie będą wyświetlane wersje zainstalowane przez pliki zip ani zarządzane przez program Visual Studio (dowolna wersja zainstalowana z programem Visual Studio 2019 16,3 lub nowszym).</span><span class="sxs-lookup"><span data-stu-id="d995a-131">Specifically, this tool will not display versions installed by zip files or managed by Visual Studio (any version installed with Visual Studio 2019 16.3 or later).</span></span> <span data-ttu-id="d995a-132">Jednym ze sposobów sprawdzenia, czy wersja jest zarządzana przez program Visual Studio, jest wyświetlenie jej w programie `Add or Remove Programs`, gdzie wersje zarządzane programu Visual Studio są oznaczone jako takie w nazwach wyświetlanych.</span><span class="sxs-lookup"><span data-stu-id="d995a-132">One way to check if a version is managed by Visual Studio is to view it in `Add or Remove Programs`, where Visual Studio managed versions are marked as such in their display names.</span></span>

<span data-ttu-id="d995a-133">**dotnet-Core — lista dezinstalacji**</span><span class="sxs-lookup"><span data-stu-id="d995a-133">**dotnet-core-uninstall list**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="d995a-134">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="d995a-134">Synopsis</span></span>

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a><span data-ttu-id="d995a-135">Opcje</span><span class="sxs-lookup"><span data-stu-id="d995a-135">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="d995a-136">Windows</span><span class="sxs-lookup"><span data-stu-id="d995a-136">Windows</span></span>](#tab/windows)

* **`--aspnet-runtime`**

  <span data-ttu-id="d995a-137">Wyświetla wszystkie ASP.NET Core środowiska uruchomieniowe, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="d995a-137">Lists all the ASP.NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="d995a-138">Wyświetla listę wszystkich pakietów środowiska uruchomieniowego środowiska .NET Core i hostingu, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="d995a-138">Lists all the .NET Core runtime and hosting bundles that can be uninstalled with this tool.</span></span>

* **`--runtime`**

  <span data-ttu-id="d995a-139">Wyświetla wszystkie środowiska uruchomieniowe platformy .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="d995a-139">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="d995a-140">Wyświetla listę wszystkich zestawów SDK platformy .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="d995a-140">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="d995a-141">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="d995a-141">Sets the verbosity level.</span></span> <span data-ttu-id="d995a-142">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d995a-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d995a-143">Wartością domyślną jest `normal`.</span><span class="sxs-lookup"><span data-stu-id="d995a-143">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="d995a-144">Wyświetla listę wszystkich zestawów SDK i środowisk uruchomieniowych x64 .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="d995a-144">Lists all x64 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

* **`--x86`**

  <span data-ttu-id="d995a-145">Wyświetla listę wszystkich zestawów SDK i środowisk uruchomieniowych x86 .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="d995a-145">Lists all x86 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

## <a name="macos"></a>[<span data-ttu-id="d995a-146">macOS</span><span class="sxs-lookup"><span data-stu-id="d995a-146">macOS</span></span>](#tab/macos)

* **`--runtime`**

  <span data-ttu-id="d995a-147">Wyświetla wszystkie środowiska uruchomieniowe platformy .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="d995a-147">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="d995a-148">Wyświetla listę wszystkich zestawów SDK platformy .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="d995a-148">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="d995a-149">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="d995a-149">Sets the verbosity level.</span></span> <span data-ttu-id="d995a-150">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d995a-150">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d995a-151">Wartością domyślną jest `normal`.</span><span class="sxs-lookup"><span data-stu-id="d995a-151">The default value is `normal`.</span></span>
  
---

#### <a name="examples"></a><span data-ttu-id="d995a-152">Przykłady</span><span class="sxs-lookup"><span data-stu-id="d995a-152">Examples</span></span>

* <span data-ttu-id="d995a-153">Wyświetl listę wszystkich zestawów SDK platformy .NET Core i środowiska uruchomieniowe, które można usunąć za pomocą tego narzędzia:</span><span class="sxs-lookup"><span data-stu-id="d995a-153">List all .NET Core SDKs and runtimes that can be removed with this tool:</span></span>

  ```console
  dotnet-core-uninstall list
  ```

* <span data-ttu-id="d995a-154">Wyświetl listę wszystkich zestawów SDK i środowisk uruchomieniowych x64 .NET Core:</span><span class="sxs-lookup"><span data-stu-id="d995a-154">List all x64 .NET Core SDKs and runtimes:</span></span>

  ```console
  dotnet-core-uninstall list --x64
  ```

* <span data-ttu-id="d995a-155">Wyświetl listę wszystkich zestawów SDK dla platformy .NET Core:</span><span class="sxs-lookup"><span data-stu-id="d995a-155">List all x86 .NET Core SDKs:</span></span>

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a><span data-ttu-id="d995a-156">Krok 2 — wykonywanie suchego przebiegu</span><span class="sxs-lookup"><span data-stu-id="d995a-156">Step 2 - Do a dry run</span></span>

<span data-ttu-id="d995a-157">Polecenia `dotnet-core-uninstall dry-run` i `dotnet-core-uninstall whatif` wyświetlają .NET Core zestawy SDK i środowiska uruchomieniowe, które zostaną usunięte na podstawie opcji dostępnych bez konieczności odinstalowania.</span><span class="sxs-lookup"><span data-stu-id="d995a-157">The `dotnet-core-uninstall dry-run` and `dotnet-core-uninstall whatif` commands display the .NET Core SDKs and runtimes that will be removed based on the options provided without performing the uninstall.</span></span> <span data-ttu-id="d995a-158">Te polecenia są synonimami.</span><span class="sxs-lookup"><span data-stu-id="d995a-158">These commands are synonyms.</span></span>

<span data-ttu-id="d995a-159">**dotnet-Core — Odinstalowywanie suchego i dotnet-Core-Uninstall whatIf**</span><span class="sxs-lookup"><span data-stu-id="d995a-159">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="d995a-160">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="d995a-160">Synopsis</span></span>

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="d995a-161">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d995a-161">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="d995a-162">Określona wersja do odinstalowania.</span><span class="sxs-lookup"><span data-stu-id="d995a-162">The specified version to uninstall.</span></span> <span data-ttu-id="d995a-163">Można wyświetlić kilka kolejnych wersji, rozdzielonych spacjami.</span><span class="sxs-lookup"><span data-stu-id="d995a-163">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="d995a-164">Pliki odpowiedzi są również obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="d995a-164">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="d995a-165">Pliki odpowiedzi są alternatywą do umieszczania wszystkich wersji w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="d995a-165">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="d995a-166">Są one plikami tekstowymi, zazwyczaj z \*rozszerzeniem. rsp, a każda wersja jest wymieniona w osobnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="d995a-166">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="d995a-167">Aby określić plik odpowiedzi dla `VERSION` argumentu, użyj \@ znaku bezpośrednio po nazwie pliku odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="d995a-167">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="d995a-168">Opcje</span><span class="sxs-lookup"><span data-stu-id="d995a-168">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="d995a-169">Windows</span><span class="sxs-lookup"><span data-stu-id="d995a-169">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="d995a-170">Usuwa wszystkie zestawy SDK i środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d995a-170">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="d995a-171">Usuwa tylko zestawy SDK i środowiska uruchomieniowe platformy .NET Core z wersją mniejszą niż określona wersja.</span><span class="sxs-lookup"><span data-stu-id="d995a-171">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="d995a-172">Określona wersja jest zainstalowana.</span><span class="sxs-lookup"><span data-stu-id="d995a-172">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="d995a-173">Usuwa wszystkie zestawy SDK i środowiska uruchomieniowe platformy .NET Core, z wyjątkiem określonych wersji.</span><span class="sxs-lookup"><span data-stu-id="d995a-173">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="d995a-174">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core, z wyjątkiem jednej najwyższej wersji.</span><span class="sxs-lookup"><span data-stu-id="d995a-174">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="d995a-175">Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe zastąpione nowszymi poprawkami.</span><span class="sxs-lookup"><span data-stu-id="d995a-175">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="d995a-176">Ta opcja chroni plik Global. JSON.</span><span class="sxs-lookup"><span data-stu-id="d995a-176">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="d995a-177">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core oznaczone jako wersje zapoznawcze.</span><span class="sxs-lookup"><span data-stu-id="d995a-177">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="d995a-178">Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe oznaczone jako wersje zapoznawcze z wyjątkiem tego, który jest najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="d995a-178">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="d995a-179">Usuwa tylko ASP.NET Core środowiska uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="d995a-179">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="d995a-180">Usuwa środowisko uruchomieniowe programu .NET Core i tylko pakiety hostingu.</span><span class="sxs-lookup"><span data-stu-id="d995a-180">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="d995a-181">Usuwa zestawy .NET Core i środowiska uruchomieniowe, które pasują do określonej `major.minor` wersji.</span><span class="sxs-lookup"><span data-stu-id="d995a-181">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="d995a-182">Usuwa tylko środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d995a-182">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="d995a-183">Usuwa tylko zestawy SDK platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d995a-183">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="d995a-184">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="d995a-184">Sets the verbosity level.</span></span> <span data-ttu-id="d995a-185">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d995a-185">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d995a-186">Wartością domyślną jest `normal`.</span><span class="sxs-lookup"><span data-stu-id="d995a-186">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="d995a-187">Musi być używana z `--sdk`, `--runtime`, i `--aspnet-runtime` do usuwania zestawów SDK x64 lub środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="d995a-187">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="d995a-188">Musi być używana z `--sdk`, `--runtime`, i `--aspnet-runtime` do usuwania zestawów SDK x86 lub środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="d995a-188">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="d995a-189">**`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d995a-189">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="d995a-190">Uwagi:</span><span class="sxs-lookup"><span data-stu-id="d995a-190">Notes:</span></span>

1. <span data-ttu-id="d995a-191">Dokładnie jeden z `--sdk`, `--runtime`, `--aspnet-runtime`, i `--hosting-bundle` jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="d995a-191">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="d995a-192">`--all`, `--all-below`, `--all-but` `--major-minor` `[<VERSION>...]` ,,,,, i są wyłączne. `--all-but-latest` `--all-lower-patches` `--all-previews` `--all-previews-but-latest`</span><span class="sxs-lookup"><span data-stu-id="d995a-192">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="d995a-193">Jeśli `--x64` lub `--x86` nie zostanie określony, zostaną usunięte oba wersje x64 i x86.</span><span class="sxs-lookup"><span data-stu-id="d995a-193">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="d995a-194">macOS</span><span class="sxs-lookup"><span data-stu-id="d995a-194">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="d995a-195">Usuwa wszystkie zestawy SDK i środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d995a-195">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="d995a-196">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core poniżej określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="d995a-196">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="d995a-197">Określona wersja pozostanie.</span><span class="sxs-lookup"><span data-stu-id="d995a-197">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="d995a-198">Usuwa zestawy .NET Core i środowiska uruchomieniowe, z wyjątkiem określonych wersji.</span><span class="sxs-lookup"><span data-stu-id="d995a-198">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="d995a-199">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core, z wyjątkiem jednej najwyższej wersji.</span><span class="sxs-lookup"><span data-stu-id="d995a-199">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="d995a-200">Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe zastąpione nowszymi poprawkami.</span><span class="sxs-lookup"><span data-stu-id="d995a-200">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="d995a-201">Ta opcja chroni plik Global. JSON.</span><span class="sxs-lookup"><span data-stu-id="d995a-201">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="d995a-202">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core oznaczone jako wersje zapoznawcze.</span><span class="sxs-lookup"><span data-stu-id="d995a-202">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="d995a-203">Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe oznaczone jako wersje zapoznawcze z wyjątkiem tego, który jest najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="d995a-203">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="d995a-204">Usuwa zestawy .NET Core i środowiska uruchomieniowe, które pasują do określonej `major.minor` wersji.</span><span class="sxs-lookup"><span data-stu-id="d995a-204">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="d995a-205">Usuwa tylko środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d995a-205">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="d995a-206">Usuwa tylko zestawy SDK platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d995a-206">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="d995a-207">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="d995a-207">Sets the verbosity level.</span></span> <span data-ttu-id="d995a-208">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d995a-208">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d995a-209">Wartością domyślną jest `normal`.</span><span class="sxs-lookup"><span data-stu-id="d995a-209">The default value is `normal`.</span></span>
  
* <span data-ttu-id="d995a-210">**`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio lub zestawy SDK.</span><span class="sxs-lookup"><span data-stu-id="d995a-210">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="d995a-211">Uwagi:</span><span class="sxs-lookup"><span data-stu-id="d995a-211">Notes:</span></span>

1. <span data-ttu-id="d995a-212">Dokładnie jeden z `--sdk` i `--runtime` jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="d995a-212">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="d995a-213">`--all`, `--all-below`, `--all-but` `--major-minor` `[<VERSION>...]` ,,,,, i są wyłączne. `--all-but-latest` `--all-lower-patches` `--all-previews` `--all-previews-but-latest`</span><span class="sxs-lookup"><span data-stu-id="d995a-213">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="d995a-214">Przykłady</span><span class="sxs-lookup"><span data-stu-id="d995a-214">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="d995a-215">Domyślnie zestawy SDK platformy .NET Core i środowiska uruchomieniowe, które mogą być wymagane przez program Visual Studio lub inne zestawy SDK `dotnet-core-uninstall dry-run` , nie są uwzględniane w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="d995a-215">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are not included in `dotnet-core-uninstall dry-run` output.</span></span> <span data-ttu-id="d995a-216">W poniższych przykładach niektóre z określonych zestawów SDK i środowiska uruchomieniowe mogą nie zostać uwzględnione w danych wyjściowych, w zależności od stanu komputera.</span><span class="sxs-lookup"><span data-stu-id="d995a-216">In the following examples, some of the specified SDKs and runtimes may not be included in the output, depending on the state of the machine.</span></span> <span data-ttu-id="d995a-217">Aby uwzględnić wszystkie zestawy SDK i środowiska uruchomieniowe, należy je jawnie wystawić `--force` jako argumenty lub użyć opcji.</span><span class="sxs-lookup"><span data-stu-id="d995a-217">To include all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="d995a-218">Suchy przebieg usuwania wszystkich środowisk uruchomieniowych platformy .NET Core, które zostały zastąpione nowszymi poprawkami:</span><span class="sxs-lookup"><span data-stu-id="d995a-218">Dry run of removing all .NET Core runtimes that have been superseded by higher patches:</span></span>

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* <span data-ttu-id="d995a-219">Suchy przebieg usuwania wszystkich zestawów .NET Core SDK poniżej wersji `2.2.301`:</span><span class="sxs-lookup"><span data-stu-id="d995a-219">Dry run of removing all .NET Core SDKs below the version `2.2.301`:</span></span>

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a><span data-ttu-id="d995a-220">Krok 3 — Odinstalowywanie zestawów SDK i środowisk uruchomieniowych platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="d995a-220">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>

<span data-ttu-id="d995a-221">`dotnet-core-uninstall remove`Odinstalowuje zestawy SDK platformy .NET Core i środowiska uruchomieniowe, które są określone przez kolekcję opcji.</span><span class="sxs-lookup"><span data-stu-id="d995a-221">`dotnet-core-uninstall remove` uninstalls .NET Core SDKs and Runtimes that are specified by a collection of options.</span></span> <span data-ttu-id="d995a-222">Narzędzia nie można użyć do odinstalowania zestawów SDK i środowiska uruchomieniowego w wersji 5,0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="d995a-222">The tool can't be used to uninstall SDKs and Runtimes with version 5.0 or above.</span></span>

<span data-ttu-id="d995a-223">Ponieważ to narzędzie ma szkodliwe zachowanie, **zdecydowanie** zaleca się wykonanie suchego uruchomienia przed uruchomieniem polecenia Usuń.</span><span class="sxs-lookup"><span data-stu-id="d995a-223">Since this tool has a destructive behavior, it's **highly** recommended that you do a dry run before running the remove command.</span></span> <span data-ttu-id="d995a-224">W przypadku uruchamiania w trybie suchym zostanie wyświetlone, które zestawy SDK i środowiska uruchomieniowe platformy .NET Core `remove` zostaną usunięte przy użyciu polecenia.</span><span class="sxs-lookup"><span data-stu-id="d995a-224">The dry run will show you what .NET Core SDKs and runtimes will be removed when you use the `remove` command.</span></span> <span data-ttu-id="d995a-225">Zapoznaj się z tematem [czy należy usunąć wersję?](../install/remove-runtime-sdk-versions.md#should-i-remove-a-version) , aby dowiedzieć się, które zestawy SDK i środowiska uruchomieniowe są bezpieczne do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="d995a-225">Refer to [Should I remove a version?](../install/remove-runtime-sdk-versions.md#should-i-remove-a-version) to learn which SDKs and runtimes are safe to remove.</span></span>

> [!CAUTION]
> <span data-ttu-id="d995a-226">Należy pamiętać o następujących zastrzeżeniach:</span><span class="sxs-lookup"><span data-stu-id="d995a-226">Keep in mind the following caveats:</span></span>
>
>- <span data-ttu-id="d995a-227">To narzędzie umożliwia odinstalowanie wersji zestaw .NET Core SDK, które są wymagane przez `global.json` pliki na komputerze.</span><span class="sxs-lookup"><span data-stu-id="d995a-227">This tool can uninstall versions of the .NET Core SDK that are required by `global.json` files on your machine.</span></span> <span data-ttu-id="d995a-228">Zestawy SDK platformy .NET Core można ponownie zainstalować ze strony [pobierania programu .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="d995a-228">You can reinstall .NET Core SDKs from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="d995a-229">To narzędzie umożliwia odinstalowanie wersji środowiska uruchomieniowego programu .NET Core, które są wymagane przez aplikacje zależne od platformy.</span><span class="sxs-lookup"><span data-stu-id="d995a-229">This tool can uninstall versions of the .NET Core runtime that are required by framework dependent applications on your machine.</span></span> <span data-ttu-id="d995a-230">Środowiska uruchomieniowe platformy .NET Core można ponownie zainstalować ze strony [pobierania programu .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="d995a-230">You can reinstall .NET Core runtimes from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="d995a-231">To narzędzie umożliwia odinstalowanie wersji zestaw .NET Core SDK i środowiska uruchomieniowego, na których bazuje program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d995a-231">This tool can uninstall versions of the .NET Core SDK and runtime that Visual Studio relies on.</span></span> <span data-ttu-id="d995a-232">W przypadku przerwania instalacji programu Visual Studio Uruchom polecenie "Napraw" w Instalatorze programu Visual Studio, aby powrócić do stanu roboczego.</span><span class="sxs-lookup"><span data-stu-id="d995a-232">If you break your Visual Studio installation, run "Repair" in the Visual Studio installer to get back to a working state.</span></span>

<span data-ttu-id="d995a-233">Domyślnie wszystkie polecenia zachowują zestawy .NET Core i środowiska uruchomieniowe, które mogą być wymagane przez program Visual Studio lub inne zestawy SDK.</span><span class="sxs-lookup"><span data-stu-id="d995a-233">By default, all commands keep the .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs.</span></span> <span data-ttu-id="d995a-234">Te zestawy SDK i środowiska uruchomieniowe mogą zostać odinstalowane przez wymienienie ich jawnie jako `--force` argumenty lub przy użyciu opcji.</span><span class="sxs-lookup"><span data-stu-id="d995a-234">These SDKs and runtimes can be uninstalled by listing them explicitly as arguments or by using the `--force` option.</span></span>

<span data-ttu-id="d995a-235">Narzędzie wymaga podniesienia uprawnień, aby odinstalować zestawy SDK i środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d995a-235">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="d995a-236">Uruchom narzędzie w wierszu polecenia administratora w systemie Windows i `sudo` w systemie macOS.</span><span class="sxs-lookup"><span data-stu-id="d995a-236">Run the tool in an Administrator command prompt on Windows and with `sudo` on macOS.</span></span> <span data-ttu-id="d995a-237">Polecenia `dry-run` i `whatif` nie wymagają podniesienia uprawnień.</span><span class="sxs-lookup"><span data-stu-id="d995a-237">The `dry-run` and `whatif` commands don't require elevation.</span></span>

<span data-ttu-id="d995a-238">**dotnet-Core — usuwanie odinstalowania**</span><span class="sxs-lookup"><span data-stu-id="d995a-238">**dotnet-core-uninstall remove**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="d995a-239">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="d995a-239">Synopsis</span></span>

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="d995a-240">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d995a-240">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="d995a-241">Określona wersja do odinstalowania.</span><span class="sxs-lookup"><span data-stu-id="d995a-241">The specified version to uninstall.</span></span> <span data-ttu-id="d995a-242">Można wyświetlić kilka kolejnych wersji, rozdzielonych spacjami.</span><span class="sxs-lookup"><span data-stu-id="d995a-242">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="d995a-243">Pliki odpowiedzi są również obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="d995a-243">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="d995a-244">Pliki odpowiedzi są alternatywą do umieszczania wszystkich wersji w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="d995a-244">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="d995a-245">Są one plikami tekstowymi, zazwyczaj z \*rozszerzeniem. rsp, a każda wersja jest wymieniona w osobnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="d995a-245">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="d995a-246">Aby określić plik odpowiedzi dla `VERSION` argumentu, użyj \@ znaku bezpośrednio po nazwie pliku odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="d995a-246">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="d995a-247">Opcje</span><span class="sxs-lookup"><span data-stu-id="d995a-247">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="d995a-248">Windows</span><span class="sxs-lookup"><span data-stu-id="d995a-248">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="d995a-249">Usuwa wszystkie zestawy SDK i środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d995a-249">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="d995a-250">Usuwa tylko zestawy SDK i środowiska uruchomieniowe platformy .NET Core z wersją mniejszą niż określona wersja.</span><span class="sxs-lookup"><span data-stu-id="d995a-250">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="d995a-251">Określona wersja jest zainstalowana.</span><span class="sxs-lookup"><span data-stu-id="d995a-251">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="d995a-252">Usuwa wszystkie zestawy SDK i środowiska uruchomieniowe platformy .NET Core, z wyjątkiem określonych wersji.</span><span class="sxs-lookup"><span data-stu-id="d995a-252">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="d995a-253">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core, z wyjątkiem jednej najwyższej wersji.</span><span class="sxs-lookup"><span data-stu-id="d995a-253">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="d995a-254">Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe zastąpione nowszymi poprawkami.</span><span class="sxs-lookup"><span data-stu-id="d995a-254">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="d995a-255">Ta opcja chroni plik Global. JSON.</span><span class="sxs-lookup"><span data-stu-id="d995a-255">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="d995a-256">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core oznaczone jako wersje zapoznawcze.</span><span class="sxs-lookup"><span data-stu-id="d995a-256">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="d995a-257">Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe oznaczone jako wersje zapoznawcze z wyjątkiem tego, który jest najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="d995a-257">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="d995a-258">Usuwa tylko ASP.NET Core środowiska uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="d995a-258">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="d995a-259">Usuwa środowisko uruchomieniowe programu .NET Core i tylko pakiety hostingu.</span><span class="sxs-lookup"><span data-stu-id="d995a-259">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="d995a-260">Usuwa zestawy .NET Core i środowiska uruchomieniowe, które pasują do określonej `major.minor` wersji.</span><span class="sxs-lookup"><span data-stu-id="d995a-260">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="d995a-261">Usuwa tylko środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d995a-261">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="d995a-262">Usuwa tylko zestawy SDK platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d995a-262">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="d995a-263">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="d995a-263">Sets the verbosity level.</span></span> <span data-ttu-id="d995a-264">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d995a-264">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d995a-265">Wartością domyślną jest `normal`.</span><span class="sxs-lookup"><span data-stu-id="d995a-265">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="d995a-266">Musi być używana z `--sdk`, `--runtime`, i `--aspnet-runtime` do usuwania zestawów SDK x64 lub środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="d995a-266">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="d995a-267">Musi być używana z `--sdk`, `--runtime`, i `--aspnet-runtime` do usuwania zestawów SDK x86 lub środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="d995a-267">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="d995a-268">**`-y, --yes`** Wykonuje polecenie bez potwierdzenia typu "tak" lub "nie".</span><span class="sxs-lookup"><span data-stu-id="d995a-268">**`-y, --yes`** Executes the command without requiring a yes or no confirmation.</span></span>

* <span data-ttu-id="d995a-269">**`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d995a-269">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="d995a-270">Uwagi:</span><span class="sxs-lookup"><span data-stu-id="d995a-270">Notes:</span></span>

1. <span data-ttu-id="d995a-271">Dokładnie jeden z `--sdk`, `--runtime`, `--aspnet-runtime`, i `--hosting-bundle` jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="d995a-271">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="d995a-272">`--all`, `--all-below`, `--all-but` `--major-minor` `[<VERSION>...]` ,,,,, i są wyłączne. `--all-but-latest` `--all-lower-patches` `--all-previews` `--all-previews-but-latest`</span><span class="sxs-lookup"><span data-stu-id="d995a-272">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="d995a-273">Jeśli `--x64` lub `--x86` nie zostanie określony, zostaną usunięte oba wersje x64 i x86.</span><span class="sxs-lookup"><span data-stu-id="d995a-273">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="d995a-274">macOS</span><span class="sxs-lookup"><span data-stu-id="d995a-274">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="d995a-275">Usuwa wszystkie zestawy SDK i środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d995a-275">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="d995a-276">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core poniżej określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="d995a-276">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="d995a-277">Określona wersja pozostanie.</span><span class="sxs-lookup"><span data-stu-id="d995a-277">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="d995a-278">Usuwa zestawy .NET Core i środowiska uruchomieniowe, z wyjątkiem określonych wersji.</span><span class="sxs-lookup"><span data-stu-id="d995a-278">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="d995a-279">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core, z wyjątkiem jednej najwyższej wersji.</span><span class="sxs-lookup"><span data-stu-id="d995a-279">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="d995a-280">Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe zastąpione nowszymi poprawkami.</span><span class="sxs-lookup"><span data-stu-id="d995a-280">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="d995a-281">Ta opcja chroni plik Global. JSON.</span><span class="sxs-lookup"><span data-stu-id="d995a-281">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="d995a-282">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core oznaczone jako wersje zapoznawcze.</span><span class="sxs-lookup"><span data-stu-id="d995a-282">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="d995a-283">Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe oznaczone jako wersje zapoznawcze z wyjątkiem tego, który jest najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="d995a-283">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="d995a-284">Usuwa zestawy .NET Core i środowiska uruchomieniowe, które pasują do określonej `major.minor` wersji.</span><span class="sxs-lookup"><span data-stu-id="d995a-284">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="d995a-285">Usuwa tylko środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d995a-285">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="d995a-286">Usuwa tylko zestawy SDK platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d995a-286">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="d995a-287">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="d995a-287">Sets the verbosity level.</span></span> <span data-ttu-id="d995a-288">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d995a-288">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d995a-289">Wartością domyślną jest `normal`.</span><span class="sxs-lookup"><span data-stu-id="d995a-289">The default value is `normal`.</span></span>

* <span data-ttu-id="d995a-290">**`-y, --yes`** Wykonuje polecenie bez potwierdzenia Y/N.</span><span class="sxs-lookup"><span data-stu-id="d995a-290">**`-y, --yes`** Executes the command without requiring Y/N confirmation.</span></span>
  
* <span data-ttu-id="d995a-291">**`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio lub zestawy SDK.</span><span class="sxs-lookup"><span data-stu-id="d995a-291">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="d995a-292">Uwagi:</span><span class="sxs-lookup"><span data-stu-id="d995a-292">Notes:</span></span>

1. <span data-ttu-id="d995a-293">Dokładnie jeden z `--sdk` i `--runtime` jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="d995a-293">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="d995a-294">`--all`, `--all-below`, `--all-but` `--major-minor` `[<VERSION>...]` ,,,,, i są wyłączne. `--all-but-latest` `--all-lower-patches` `--all-previews` `--all-previews-but-latest`</span><span class="sxs-lookup"><span data-stu-id="d995a-294">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="d995a-295">Przykłady</span><span class="sxs-lookup"><span data-stu-id="d995a-295">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="d995a-296">Domyślnie są przechowywane zestawy SDK i środowiska uruchomieniowe platformy .NET Core, które mogą być wymagane przez program Visual Studio lub inne zestawy SDK.</span><span class="sxs-lookup"><span data-stu-id="d995a-296">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are kept.</span></span> <span data-ttu-id="d995a-297">W poniższych przykładach niektóre z określonych zestawów SDK i środowiska uruchomieniowe mogą pozostać w zależności od stanu komputera.</span><span class="sxs-lookup"><span data-stu-id="d995a-297">In the following examples, some of the specified SDKs and runtimes may remain, depending on the state of the machine.</span></span> <span data-ttu-id="d995a-298">Aby usunąć wszystkie zestawy SDK i środowiska uruchomieniowe, należy je jawnie wystawić `--force` jako argumenty lub użyć opcji.</span><span class="sxs-lookup"><span data-stu-id="d995a-298">To remove all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="d995a-299">Usuń wszystkie środowiska uruchomieniowe platformy .NET Core z `3.0.0-preview6-27804-01` wyjątkiem wersji, która nie wymaga potwierdzenia Y/N:</span><span class="sxs-lookup"><span data-stu-id="d995a-299">Remove all .NET Core runtimes except the version `3.0.0-preview6-27804-01` without requiring Y/N confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* <span data-ttu-id="d995a-300">Usuń wszystkie zestawy SDK platformy .NET Core 1,1 bez konieczności potwierdzania Y/n:</span><span class="sxs-lookup"><span data-stu-id="d995a-300">Remove all .NET Core 1.1 SDKs without requiring Y/n confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* <span data-ttu-id="d995a-301">Usuń zestaw .NET Core 1.1.11 SDK bez danych wyjściowych konsoli:</span><span class="sxs-lookup"><span data-stu-id="d995a-301">Remove the .NET Core 1.1.11 SDK with no console output:</span></span>

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* <span data-ttu-id="d995a-302">Usuń wszystkie zestawy SDK platformy .NET Core, które można bezpiecznie usunąć za pomocą tego narzędzia:</span><span class="sxs-lookup"><span data-stu-id="d995a-302">Remove all .NET Core SDKs that can safely be removed by this tool:</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* <span data-ttu-id="d995a-303">Usuń wszystkie zestawy SDK platformy .NET Core, które mogą zostać usunięte przez to narzędzie, w tym zestawy SDK, które mogą być wymagane przez program Visual Studio (niezalecane):</span><span class="sxs-lookup"><span data-stu-id="d995a-303">Remove all .NET Core SDKs that can be removed by this tool, including those SDKs that may be required by Visual Studio (not recommended):</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* <span data-ttu-id="d995a-304">Usuń wszystkie zestawy SDK platformy .NET Core, które są określone w pliku odpowiedzi`versions.rsp`</span><span class="sxs-lookup"><span data-stu-id="d995a-304">Remove all .NET Core SDKs that are specified in the response file `versions.rsp`</span></span>

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  <span data-ttu-id="d995a-305">Zawartość *wersji. rsp* jest następująca:</span><span class="sxs-lookup"><span data-stu-id="d995a-305">The content of *versions.rsp* is as follows:</span></span>
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a><span data-ttu-id="d995a-306">Krok 4. Usuwanie folderu rezerwowego NuGet (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="d995a-306">Step 4 - Delete the NuGet fallback folder (optional)</span></span>

<span data-ttu-id="d995a-307">W niektórych przypadkach nie jest już potrzebna `NuGetFallbackFolder` i może chcieć ją usunąć.</span><span class="sxs-lookup"><span data-stu-id="d995a-307">In some cases, you no longer need the `NuGetFallbackFolder` and may wish to delete it.</span></span> <span data-ttu-id="d995a-308">Aby uzyskać więcej informacji na temat usuwania tego folderu, zobacz [usuwanie NuGetFallbackFolder](../install/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span><span class="sxs-lookup"><span data-stu-id="d995a-308">For more information about deleting this folder, see [Remove the NuGetFallbackFolder](../install/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span></span>

## <a name="uninstall-the-tool"></a><span data-ttu-id="d995a-309">Odinstalowywanie narzędzia</span><span class="sxs-lookup"><span data-stu-id="d995a-309">Uninstall the tool</span></span>

## <a name="windows"></a>[<span data-ttu-id="d995a-310">Windows</span><span class="sxs-lookup"><span data-stu-id="d995a-310">Windows</span></span>](#tab/windows)

1. <span data-ttu-id="d995a-311">Otwórz aplet **Dodaj lub usuń programy**.</span><span class="sxs-lookup"><span data-stu-id="d995a-311">Open **Add or Remove Programs**.</span></span>
2. <span data-ttu-id="d995a-312">Wyszukaj `Microsoft .NET Core SDK Uninstall Tool`.</span><span class="sxs-lookup"><span data-stu-id="d995a-312">Search for `Microsoft .NET Core SDK Uninstall Tool`.</span></span>
3. <span data-ttu-id="d995a-313">Wybierz pozycję **Odinstaluj**.</span><span class="sxs-lookup"><span data-stu-id="d995a-313">Select **Uninstall**.</span></span>

## <a name="macos"></a>[<span data-ttu-id="d995a-314">macOS</span><span class="sxs-lookup"><span data-stu-id="d995a-314">macOS</span></span>](#tab/macos)

<span data-ttu-id="d995a-315">Usuń pobrany plik *dotnet-Core-Uninstall. tar. gz* z katalogu, w którym został zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="d995a-315">Delete the downloaded *dotnet-core-uninstall.tar.gz* file from the directory where it was installed.</span></span> <span data-ttu-id="d995a-316">Jeśli zawartość tego pliku została rozpakowany do innego katalogu, pamiętaj, aby usunąć tę zawartość.</span><span class="sxs-lookup"><span data-stu-id="d995a-316">If you unzipped the contents of this file into another directory, be sure to delete that content as well.</span></span>

---
