---
title: Narzędzie do odinstalowywania
description: Omówienie narzędzia do odinstalowywania platformy .NET Core, narzędzia z przewodnikiem, które umożliwia kontrolowane czyszczenie zestawów SDK i środowiska uruchomieniowego platformy .NET Core.
author: sfoslund
ms.date: 05/27/2020
ms.openlocfilehash: 4e70fd3438b582bd5a0d6a52d7e58ed5e07f8811
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446909"
---
# <a name="net-core-uninstall-tool"></a><span data-ttu-id="07904-103">Narzędzie do dezinstalacji platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="07904-103">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="07904-104">[Narzędzie do dezinstalacji programu .NET Core](https://aka.ms/dotnet-core-uninstall-tool) ( `dotnet-core-uninstall` ) umożliwia usuwanie zestawów SDK i środowisk uruchomieniowych platformy .NET Core z systemu.</span><span class="sxs-lookup"><span data-stu-id="07904-104">The [.NET Core Uninstall Tool](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and Runtimes from a system.</span></span> <span data-ttu-id="07904-105">Dostępna jest kolekcja opcji, aby określić wersje, które mają zostać odinstalowane.</span><span class="sxs-lookup"><span data-stu-id="07904-105">A collection of options is available to specify which versions you want to uninstall.</span></span>

<span data-ttu-id="07904-106">Narzędzie obsługuje systemy Windows i macOS.</span><span class="sxs-lookup"><span data-stu-id="07904-106">The tool supports Windows and macOS.</span></span> <span data-ttu-id="07904-107">System Linux nie jest obecnie obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="07904-107">Linux is currently not supported.</span></span>

<span data-ttu-id="07904-108">W systemie Windows narzędzie może odinstalować tylko zestawy SDK i środowiska uruchomieniowe, które zostały zainstalowane przy użyciu jednego z następujących instalatorów:</span><span class="sxs-lookup"><span data-stu-id="07904-108">On Windows, the tool can only uninstall SDKs and Runtimes that were installed using one of the following installers:</span></span>

- <span data-ttu-id="07904-109">Zestaw .NET Core SDK i Instalator środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="07904-109">The .NET Core SDK and runtime installer.</span></span>
- <span data-ttu-id="07904-110">Instalator programu Visual Studio w wersji wcześniejszej niż program Visual Studio 2019 w wersji 16,3.</span><span class="sxs-lookup"><span data-stu-id="07904-110">The Visual Studio installer in versions earlier than Visual Studio 2019 version 16.3.</span></span>

<span data-ttu-id="07904-111">W systemie macOS narzędzie może odinstalować tylko zestawy SDK i środowiska uruchomieniowe znajdujące się w folderze */usr/local/share/dotnet* .</span><span class="sxs-lookup"><span data-stu-id="07904-111">On macOS, the tool can only uninstall SDKs and runtimes located in the */usr/local/share/dotnet* folder.</span></span>

<span data-ttu-id="07904-112">Ze względu na te ograniczenia narzędzie może nie być w stanie odinstalować wszystkich zestawów SDK i środowisk uruchomieniowych platformy .NET Core na komputerze.</span><span class="sxs-lookup"><span data-stu-id="07904-112">Because of these limitations, the tool may not be able to uninstall all of the .NET Core SDKs and runtimes on your machine.</span></span> <span data-ttu-id="07904-113">Możesz użyć polecenia, `dotnet --info` Aby znaleźć wszystkie zainstalowane zestawy SDK .NET Core i środowiska uruchomieniowe, w tym zestawy SDK i środowiska uruchomieniowe, których to narzędzie nie może usunąć.</span><span class="sxs-lookup"><span data-stu-id="07904-113">You can use the `dotnet --info` command to find all of the .NET Core SDKs and runtimes installed, including those SDKs and runtimes that this tool can't remove.</span></span> <span data-ttu-id="07904-114">`dotnet-core-uninstall list`Polecenie wyświetla listę zestawów SDK, które można odinstalować za pomocą narzędzia.</span><span class="sxs-lookup"><span data-stu-id="07904-114">The `dotnet-core-uninstall list` command displays which SDKs can be uninstalled with the tool.</span></span>

## <a name="install-the-tool"></a><span data-ttu-id="07904-115">Zainstaluj narzędzie</span><span class="sxs-lookup"><span data-stu-id="07904-115">Install the tool</span></span>

<span data-ttu-id="07904-116">W [tym miejscu](https://aka.ms/dotnet-core-uninstall-tool) możesz pobrać narzędzie do odinstalowywania platformy .NET Core i znaleźć kod źródłowy w repozytorium GitHub [/CLI-Lab](https://github.com/dotnet/cli-lab) .</span><span class="sxs-lookup"><span data-stu-id="07904-116">You can download the .NET Core Uninstall Tool from [here](https://aka.ms/dotnet-core-uninstall-tool) and find the source code at the [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub repository.</span></span>

> [!NOTE]
> <span data-ttu-id="07904-117">Narzędzie wymaga podniesienia uprawnień, aby odinstalować zestawy SDK i środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="07904-117">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="07904-118">W związku z tym należy ją zainstalować w katalogu chronionym przed zapisem, takim jak *C:\Program Files* w systemie Windows lub */usr/local/bin* na macOS.</span><span class="sxs-lookup"><span data-stu-id="07904-118">Therefore, it should be installed in a write-protected directory such as *C:\Program Files* on Windows or */usr/local/bin* on macOS.</span></span> <span data-ttu-id="07904-119">Zobacz również [podwyższony poziom dostępu dla poleceń dotnet](../tools/elevated-access.md).</span><span class="sxs-lookup"><span data-stu-id="07904-119">See also [Elevated access for dotnet commands](../tools/elevated-access.md).</span></span> <span data-ttu-id="07904-120">Aby uzyskać więcej informacji, zobacz [szczegółowe instrukcje dotyczące instalacji](https://aka.ms/dotnet-core-uninstall-tool).</span><span class="sxs-lookup"><span data-stu-id="07904-120">For more information, see the [detailed installation instructions](https://aka.ms/dotnet-core-uninstall-tool).</span></span>

## <a name="run-the-tool"></a><span data-ttu-id="07904-121">Uruchamianie narzędzia</span><span class="sxs-lookup"><span data-stu-id="07904-121">Run the tool</span></span>

<span data-ttu-id="07904-122">W poniższych krokach przedstawiono zalecane podejście do uruchamiania narzędzia do odinstalowywania:</span><span class="sxs-lookup"><span data-stu-id="07904-122">The following steps show the recommended approach for running the uninstall tool:</span></span>

- [<span data-ttu-id="07904-123">Krok 1. wyświetlanie zainstalowanych zestawów SDK i środowisk uruchomieniowych platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="07904-123">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>](#step-1---display-installed-net-core-sdks-and-runtimes)
- [<span data-ttu-id="07904-124">Krok 2 — wykonywanie suchego przebiegu</span><span class="sxs-lookup"><span data-stu-id="07904-124">Step 2 - Do a dry run</span></span>](#step-2---do-a-dry-run)
- [<span data-ttu-id="07904-125">Krok 3 — Odinstalowywanie zestawów SDK i środowisk uruchomieniowych platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="07904-125">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>](#step-3---uninstall-net-core-sdks-and-runtimes)
- [<span data-ttu-id="07904-126">Krok 4. Usuwanie folderu rezerwowego NuGet (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="07904-126">Step 4 - Delete the NuGet fallback folder (optional)</span></span>](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a><span data-ttu-id="07904-127">Krok 1. wyświetlanie zainstalowanych zestawów SDK i środowisk uruchomieniowych platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="07904-127">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>

<span data-ttu-id="07904-128">`dotnet-core-uninstall list`Polecenie wyświetla listę zainstalowanych zestawów SDK .NET Core i środowiska uruchomieniowe, które można usunąć za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="07904-128">The `dotnet-core-uninstall list` command lists the installed .NET Core SDKs and runtimes that can be removed with this tool.</span></span> <span data-ttu-id="07904-129">Niektóre zestawy SDK i środowiska uruchomieniowe mogą być wymagane przez program Visual Studio i są wyświetlane z zawarto adnotacją dlaczego nie zaleca się ich odinstalowywania.</span><span class="sxs-lookup"><span data-stu-id="07904-129">Some SDKs and runtimes may be required by Visual Studio and they're displayed with a note of why it isn't recommended to uninstall them.</span></span>

> [!NOTE]
> <span data-ttu-id="07904-130">Dane wyjściowe `dotnet-core-uninstall list` polecenia nie będą zgodne z listą zainstalowanych wersji w danych wyjściowych `dotnet --info` w większości przypadków.</span><span class="sxs-lookup"><span data-stu-id="07904-130">The output of the `dotnet-core-uninstall list` command will not match the list of installed versions in the output of `dotnet --info` in most cases.</span></span> <span data-ttu-id="07904-131">W przypadku tego narzędzia nie będą wyświetlane wersje zainstalowane przez pliki zip ani zarządzane przez program Visual Studio (dowolna wersja zainstalowana z programem Visual Studio 2019 16,3 lub nowszym).</span><span class="sxs-lookup"><span data-stu-id="07904-131">Specifically, this tool will not display versions installed by zip files or managed by Visual Studio (any version installed with Visual Studio 2019 16.3 or later).</span></span> <span data-ttu-id="07904-132">Jednym ze sposobów sprawdzenia, czy wersja jest zarządzana przez program Visual Studio, jest wyświetlenie jej w programie `Add or Remove Programs` , gdzie wersje zarządzane programu Visual Studio są oznaczone jako takie w nazwach wyświetlanych.</span><span class="sxs-lookup"><span data-stu-id="07904-132">One way to check if a version is managed by Visual Studio is to view it in `Add or Remove Programs`, where Visual Studio managed versions are marked as such in their display names.</span></span>

<span data-ttu-id="07904-133">**dotnet-Core — lista dezinstalacji**</span><span class="sxs-lookup"><span data-stu-id="07904-133">**dotnet-core-uninstall list**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="07904-134">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="07904-134">Synopsis</span></span>

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a><span data-ttu-id="07904-135">Opcje</span><span class="sxs-lookup"><span data-stu-id="07904-135">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="07904-136">Windows</span><span class="sxs-lookup"><span data-stu-id="07904-136">Windows</span></span>](#tab/windows)

* **`--aspnet-runtime`**

  <span data-ttu-id="07904-137">Wyświetla wszystkie ASP.NET Core środowiska uruchomieniowe, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="07904-137">Lists all the ASP.NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="07904-138">Wyświetla listę wszystkich pakietów hostingu platformy .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="07904-138">Lists all the .NET Core hosting bundles that can be uninstalled with this tool.</span></span>

* **`--runtime`**

  <span data-ttu-id="07904-139">Wyświetla wszystkie środowiska uruchomieniowe platformy .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="07904-139">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="07904-140">Wyświetla listę wszystkich zestawów SDK platformy .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="07904-140">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="07904-141">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="07904-141">Sets the verbosity level.</span></span> <span data-ttu-id="07904-142">Dozwolone wartości to `q[uiet]` , `m[inimal]` , `n[ormal]` , `d[etailed]` i `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="07904-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="07904-143">Wartość domyślna to `normal`.</span><span class="sxs-lookup"><span data-stu-id="07904-143">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="07904-144">Wyświetla listę wszystkich zestawów SDK i środowisk uruchomieniowych x64 .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="07904-144">Lists all x64 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

* **`--x86`**

  <span data-ttu-id="07904-145">Wyświetla listę wszystkich zestawów SDK i środowisk uruchomieniowych x86 .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="07904-145">Lists all x86 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

## <a name="macos"></a>[<span data-ttu-id="07904-146">macOS</span><span class="sxs-lookup"><span data-stu-id="07904-146">macOS</span></span>](#tab/macos)

* **`--runtime`**

  <span data-ttu-id="07904-147">Wyświetla wszystkie środowiska uruchomieniowe platformy .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="07904-147">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="07904-148">Wyświetla listę wszystkich zestawów SDK platformy .NET Core, które można odinstalować za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="07904-148">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="07904-149">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="07904-149">Sets the verbosity level.</span></span> <span data-ttu-id="07904-150">Dozwolone wartości to `q[uiet]` , `m[inimal]` , `n[ormal]` , `d[etailed]` i `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="07904-150">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="07904-151">Wartość domyślna to `normal`.</span><span class="sxs-lookup"><span data-stu-id="07904-151">The default value is `normal`.</span></span>
  
---

#### <a name="examples"></a><span data-ttu-id="07904-152">Przykłady</span><span class="sxs-lookup"><span data-stu-id="07904-152">Examples</span></span>

* <span data-ttu-id="07904-153">Wyświetl listę wszystkich zestawów SDK platformy .NET Core i środowiska uruchomieniowe, które można usunąć za pomocą tego narzędzia:</span><span class="sxs-lookup"><span data-stu-id="07904-153">List all .NET Core SDKs and runtimes that can be removed with this tool:</span></span>

  ```console
  dotnet-core-uninstall list
  ```

* <span data-ttu-id="07904-154">Wyświetl listę wszystkich zestawów SDK i środowisk uruchomieniowych x64 .NET Core:</span><span class="sxs-lookup"><span data-stu-id="07904-154">List all x64 .NET Core SDKs and runtimes:</span></span>

  ```console
  dotnet-core-uninstall list --x64
  ```

* <span data-ttu-id="07904-155">Wyświetl listę wszystkich zestawów SDK dla platformy .NET Core:</span><span class="sxs-lookup"><span data-stu-id="07904-155">List all x86 .NET Core SDKs:</span></span>

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a><span data-ttu-id="07904-156">Krok 2 — wykonywanie suchego przebiegu</span><span class="sxs-lookup"><span data-stu-id="07904-156">Step 2 - Do a dry run</span></span>

<span data-ttu-id="07904-157">`dotnet-core-uninstall dry-run`Polecenia i `dotnet-core-uninstall whatif` wyświetlają .NET Core zestawy SDK i środowiska uruchomieniowe, które zostaną usunięte na podstawie opcji dostępnych bez konieczności odinstalowania.</span><span class="sxs-lookup"><span data-stu-id="07904-157">The `dotnet-core-uninstall dry-run` and `dotnet-core-uninstall whatif` commands display the .NET Core SDKs and runtimes that will be removed based on the options provided without performing the uninstall.</span></span> <span data-ttu-id="07904-158">Te polecenia są synonimami.</span><span class="sxs-lookup"><span data-stu-id="07904-158">These commands are synonyms.</span></span>

<span data-ttu-id="07904-159">**dotnet-Core — Odinstalowywanie suchego i dotnet-Core-Uninstall whatIf**</span><span class="sxs-lookup"><span data-stu-id="07904-159">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="07904-160">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="07904-160">Synopsis</span></span>

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="07904-161">Argumenty</span><span class="sxs-lookup"><span data-stu-id="07904-161">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="07904-162">Określona wersja do odinstalowania.</span><span class="sxs-lookup"><span data-stu-id="07904-162">The specified version to uninstall.</span></span> <span data-ttu-id="07904-163">Można wyświetlić kilka kolejnych wersji, rozdzielonych spacjami.</span><span class="sxs-lookup"><span data-stu-id="07904-163">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="07904-164">Pliki odpowiedzi są również obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="07904-164">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="07904-165">Pliki odpowiedzi są alternatywą do umieszczania wszystkich wersji w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="07904-165">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="07904-166">Są one plikami tekstowymi, zazwyczaj z \* rozszerzeniem. rsp, a każda wersja jest wymieniona w osobnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="07904-166">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="07904-167">Aby określić plik odpowiedzi dla `VERSION` argumentu, użyj \@ znaku bezpośrednio po nazwie pliku odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="07904-167">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="07904-168">Opcje</span><span class="sxs-lookup"><span data-stu-id="07904-168">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="07904-169">Windows</span><span class="sxs-lookup"><span data-stu-id="07904-169">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="07904-170">Usuwa wszystkie zestawy SDK i środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="07904-170">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="07904-171">Usuwa tylko zestawy SDK i środowiska uruchomieniowe platformy .NET Core z wersją mniejszą niż określona wersja.</span><span class="sxs-lookup"><span data-stu-id="07904-171">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="07904-172">Określona wersja jest zainstalowana.</span><span class="sxs-lookup"><span data-stu-id="07904-172">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="07904-173">Usuwa wszystkie zestawy SDK i środowiska uruchomieniowe platformy .NET Core, z wyjątkiem określonych wersji.</span><span class="sxs-lookup"><span data-stu-id="07904-173">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="07904-174">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core, z wyjątkiem jednej najwyższej wersji.</span><span class="sxs-lookup"><span data-stu-id="07904-174">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="07904-175">Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe zastąpione nowszymi poprawkami.</span><span class="sxs-lookup"><span data-stu-id="07904-175">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="07904-176">Ta opcja chroni plik Global. JSON.</span><span class="sxs-lookup"><span data-stu-id="07904-176">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="07904-177">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core oznaczone jako wersje zapoznawcze.</span><span class="sxs-lookup"><span data-stu-id="07904-177">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="07904-178">Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe oznaczone jako wersje zapoznawcze z wyjątkiem tego, który jest najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="07904-178">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="07904-179">Usuwa tylko ASP.NET Core środowiska uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="07904-179">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="07904-180">Usuwa środowisko uruchomieniowe programu .NET Core i tylko pakiety hostingu.</span><span class="sxs-lookup"><span data-stu-id="07904-180">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="07904-181">Usuwa zestawy .NET Core i środowiska uruchomieniowe, które pasują do określonej `major.minor` wersji.</span><span class="sxs-lookup"><span data-stu-id="07904-181">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="07904-182">Usuwa tylko środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="07904-182">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="07904-183">Usuwa tylko zestawy SDK platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="07904-183">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="07904-184">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="07904-184">Sets the verbosity level.</span></span> <span data-ttu-id="07904-185">Dozwolone wartości to `q[uiet]` , `m[inimal]` , `n[ormal]` , `d[etailed]` i `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="07904-185">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="07904-186">Wartość domyślna to `normal`.</span><span class="sxs-lookup"><span data-stu-id="07904-186">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="07904-187">Musi być używana z `--sdk` , `--runtime` , i `--aspnet-runtime` do usuwania zestawów SDK x64 lub środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="07904-187">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="07904-188">Musi być używana z `--sdk` , `--runtime` , i `--aspnet-runtime` do usuwania zestawów SDK x86 lub środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="07904-188">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="07904-189">**`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="07904-189">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="07904-190">Uwagi:</span><span class="sxs-lookup"><span data-stu-id="07904-190">Notes:</span></span>

1. <span data-ttu-id="07904-191">Dokładnie jeden z `--sdk` , `--runtime` , `--aspnet-runtime` , i `--hosting-bundle` jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="07904-191">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="07904-192">`--all`,,,,,,, `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` `--all-previews-but-latest` `--major-minor` i `[<VERSION>...]` są wyłączne.</span><span class="sxs-lookup"><span data-stu-id="07904-192">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="07904-193">Jeśli `--x64` lub `--x86` nie zostanie określony, zostaną usunięte oba wersje x64 i x86.</span><span class="sxs-lookup"><span data-stu-id="07904-193">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="07904-194">macOS</span><span class="sxs-lookup"><span data-stu-id="07904-194">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="07904-195">Usuwa wszystkie zestawy SDK i środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="07904-195">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="07904-196">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core poniżej określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="07904-196">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="07904-197">Określona wersja pozostanie.</span><span class="sxs-lookup"><span data-stu-id="07904-197">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="07904-198">Usuwa zestawy .NET Core i środowiska uruchomieniowe, z wyjątkiem określonych wersji.</span><span class="sxs-lookup"><span data-stu-id="07904-198">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="07904-199">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core, z wyjątkiem jednej najwyższej wersji.</span><span class="sxs-lookup"><span data-stu-id="07904-199">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="07904-200">Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe zastąpione nowszymi poprawkami.</span><span class="sxs-lookup"><span data-stu-id="07904-200">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="07904-201">Ta opcja chroni plik Global. JSON.</span><span class="sxs-lookup"><span data-stu-id="07904-201">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="07904-202">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core oznaczone jako wersje zapoznawcze.</span><span class="sxs-lookup"><span data-stu-id="07904-202">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="07904-203">Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe oznaczone jako wersje zapoznawcze z wyjątkiem tego, który jest najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="07904-203">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="07904-204">Usuwa zestawy .NET Core i środowiska uruchomieniowe, które pasują do określonej `major.minor` wersji.</span><span class="sxs-lookup"><span data-stu-id="07904-204">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="07904-205">Usuwa tylko środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="07904-205">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="07904-206">Usuwa tylko zestawy SDK platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="07904-206">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="07904-207">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="07904-207">Sets the verbosity level.</span></span> <span data-ttu-id="07904-208">Dozwolone wartości to `q[uiet]` , `m[inimal]` , `n[ormal]` , `d[etailed]` i `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="07904-208">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="07904-209">Wartość domyślna to `normal`.</span><span class="sxs-lookup"><span data-stu-id="07904-209">The default value is `normal`.</span></span>
  
* <span data-ttu-id="07904-210">**`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio lub zestawy SDK.</span><span class="sxs-lookup"><span data-stu-id="07904-210">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="07904-211">Uwagi:</span><span class="sxs-lookup"><span data-stu-id="07904-211">Notes:</span></span>

1. <span data-ttu-id="07904-212">Dokładnie jeden z `--sdk` i `--runtime` jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="07904-212">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="07904-213">`--all`,,,,,,, `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` `--all-previews-but-latest` `--major-minor` i `[<VERSION>...]` są wyłączne.</span><span class="sxs-lookup"><span data-stu-id="07904-213">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="07904-214">Przykłady</span><span class="sxs-lookup"><span data-stu-id="07904-214">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="07904-215">Domyślnie zestawy SDK platformy .NET Core i środowiska uruchomieniowe, które mogą być wymagane przez program Visual Studio lub inne zestawy SDK, nie są uwzględniane w `dotnet-core-uninstall dry-run` danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="07904-215">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are not included in `dotnet-core-uninstall dry-run` output.</span></span> <span data-ttu-id="07904-216">W poniższych przykładach niektóre z określonych zestawów SDK i środowiska uruchomieniowe mogą nie zostać uwzględnione w danych wyjściowych, w zależności od stanu komputera.</span><span class="sxs-lookup"><span data-stu-id="07904-216">In the following examples, some of the specified SDKs and runtimes may not be included in the output, depending on the state of the machine.</span></span> <span data-ttu-id="07904-217">Aby uwzględnić wszystkie zestawy SDK i środowiska uruchomieniowe, należy je jawnie wystawić jako argumenty lub użyć `--force` opcji.</span><span class="sxs-lookup"><span data-stu-id="07904-217">To include all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="07904-218">Suchy przebieg usuwania wszystkich środowisk uruchomieniowych platformy .NET Core, które zostały zastąpione nowszymi poprawkami:</span><span class="sxs-lookup"><span data-stu-id="07904-218">Dry run of removing all .NET Core runtimes that have been superseded by higher patches:</span></span>

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* <span data-ttu-id="07904-219">Suchy przebieg usuwania wszystkich zestawów .NET Core SDK poniżej wersji `2.2.301` :</span><span class="sxs-lookup"><span data-stu-id="07904-219">Dry run of removing all .NET Core SDKs below the version `2.2.301`:</span></span>

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a><span data-ttu-id="07904-220">Krok 3 — Odinstalowywanie zestawów SDK i środowisk uruchomieniowych platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="07904-220">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>

<span data-ttu-id="07904-221">`dotnet-core-uninstall remove`Odinstalowuje zestawy SDK platformy .NET Core i środowiska uruchomieniowe, które są określone przez kolekcję opcji.</span><span class="sxs-lookup"><span data-stu-id="07904-221">`dotnet-core-uninstall remove` uninstalls .NET Core SDKs and Runtimes that are specified by a collection of options.</span></span> <span data-ttu-id="07904-222">Narzędzia nie można użyć do odinstalowania zestawów SDK i środowiska uruchomieniowego w wersji 5,0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="07904-222">The tool can't be used to uninstall SDKs and Runtimes with version 5.0 or above.</span></span>

<span data-ttu-id="07904-223">Ponieważ to narzędzie ma szkodliwe zachowanie, **zdecydowanie** zaleca się wykonanie suchego uruchomienia przed uruchomieniem polecenia Usuń.</span><span class="sxs-lookup"><span data-stu-id="07904-223">Since this tool has a destructive behavior, it's **highly** recommended that you do a dry run before running the remove command.</span></span> <span data-ttu-id="07904-224">W przypadku uruchamiania w trybie suchym zostanie wyświetlone, które zestawy SDK i środowiska uruchomieniowe platformy .NET Core zostaną usunięte przy użyciu `remove` polecenia.</span><span class="sxs-lookup"><span data-stu-id="07904-224">The dry run will show you what .NET Core SDKs and runtimes will be removed when you use the `remove` command.</span></span> <span data-ttu-id="07904-225">Zapoznaj się z tematem [czy należy usunąć wersję?](../install/remove-runtime-sdk-versions.md#should-i-remove-a-version) , aby dowiedzieć się, które zestawy SDK i środowiska uruchomieniowe są bezpieczne do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="07904-225">Refer to [Should I remove a version?](../install/remove-runtime-sdk-versions.md#should-i-remove-a-version) to learn which SDKs and runtimes are safe to remove.</span></span>

> [!CAUTION]
> <span data-ttu-id="07904-226">Należy pamiętać o następujących zastrzeżeniach:</span><span class="sxs-lookup"><span data-stu-id="07904-226">Keep in mind the following caveats:</span></span>
>
>- <span data-ttu-id="07904-227">To narzędzie umożliwia odinstalowanie wersji zestaw .NET Core SDK, które są wymagane przez `global.json` pliki na komputerze.</span><span class="sxs-lookup"><span data-stu-id="07904-227">This tool can uninstall versions of the .NET Core SDK that are required by `global.json` files on your machine.</span></span> <span data-ttu-id="07904-228">Zestawy SDK platformy .NET Core można ponownie zainstalować ze strony [pobierania programu .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="07904-228">You can reinstall .NET Core SDKs from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="07904-229">To narzędzie umożliwia odinstalowanie wersji środowiska uruchomieniowego programu .NET Core, które są wymagane przez aplikacje zależne od platformy.</span><span class="sxs-lookup"><span data-stu-id="07904-229">This tool can uninstall versions of the .NET Core runtime that are required by framework dependent applications on your machine.</span></span> <span data-ttu-id="07904-230">Środowiska uruchomieniowe platformy .NET Core można ponownie zainstalować ze strony [pobierania programu .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="07904-230">You can reinstall .NET Core runtimes from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="07904-231">To narzędzie umożliwia odinstalowanie wersji zestaw .NET Core SDK i środowiska uruchomieniowego, na których bazuje program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="07904-231">This tool can uninstall versions of the .NET Core SDK and runtime that Visual Studio relies on.</span></span> <span data-ttu-id="07904-232">W przypadku przerwania instalacji programu Visual Studio Uruchom polecenie "Napraw" w Instalatorze programu Visual Studio, aby powrócić do stanu roboczego.</span><span class="sxs-lookup"><span data-stu-id="07904-232">If you break your Visual Studio installation, run "Repair" in the Visual Studio installer to get back to a working state.</span></span>

<span data-ttu-id="07904-233">Domyślnie wszystkie polecenia zachowują zestawy .NET Core i środowiska uruchomieniowe, które mogą być wymagane przez program Visual Studio lub inne zestawy SDK.</span><span class="sxs-lookup"><span data-stu-id="07904-233">By default, all commands keep the .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs.</span></span> <span data-ttu-id="07904-234">Te zestawy SDK i środowiska uruchomieniowe mogą zostać odinstalowane przez wymienienie ich jawnie jako argumenty lub przy użyciu `--force` opcji.</span><span class="sxs-lookup"><span data-stu-id="07904-234">These SDKs and runtimes can be uninstalled by listing them explicitly as arguments or by using the `--force` option.</span></span>

<span data-ttu-id="07904-235">Narzędzie wymaga podniesienia uprawnień, aby odinstalować zestawy SDK i środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="07904-235">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="07904-236">Uruchom narzędzie w wierszu polecenia administratora w systemie Windows i w systemie `sudo` macOS.</span><span class="sxs-lookup"><span data-stu-id="07904-236">Run the tool in an Administrator command prompt on Windows and with `sudo` on macOS.</span></span> <span data-ttu-id="07904-237">`dry-run`Polecenia i `whatif` nie wymagają podniesienia uprawnień.</span><span class="sxs-lookup"><span data-stu-id="07904-237">The `dry-run` and `whatif` commands don't require elevation.</span></span>

<span data-ttu-id="07904-238">**dotnet-Core — usuwanie odinstalowania**</span><span class="sxs-lookup"><span data-stu-id="07904-238">**dotnet-core-uninstall remove**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="07904-239">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="07904-239">Synopsis</span></span>

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="07904-240">Argumenty</span><span class="sxs-lookup"><span data-stu-id="07904-240">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="07904-241">Określona wersja do odinstalowania.</span><span class="sxs-lookup"><span data-stu-id="07904-241">The specified version to uninstall.</span></span> <span data-ttu-id="07904-242">Można wyświetlić kilka kolejnych wersji, rozdzielonych spacjami.</span><span class="sxs-lookup"><span data-stu-id="07904-242">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="07904-243">Pliki odpowiedzi są również obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="07904-243">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="07904-244">Pliki odpowiedzi są alternatywą do umieszczania wszystkich wersji w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="07904-244">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="07904-245">Są one plikami tekstowymi, zazwyczaj z \* rozszerzeniem. rsp, a każda wersja jest wymieniona w osobnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="07904-245">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="07904-246">Aby określić plik odpowiedzi dla `VERSION` argumentu, użyj \@ znaku bezpośrednio po nazwie pliku odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="07904-246">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="07904-247">Opcje</span><span class="sxs-lookup"><span data-stu-id="07904-247">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="07904-248">Windows</span><span class="sxs-lookup"><span data-stu-id="07904-248">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="07904-249">Usuwa wszystkie zestawy SDK i środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="07904-249">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="07904-250">Usuwa tylko zestawy SDK i środowiska uruchomieniowe platformy .NET Core z wersją mniejszą niż określona wersja.</span><span class="sxs-lookup"><span data-stu-id="07904-250">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="07904-251">Określona wersja jest zainstalowana.</span><span class="sxs-lookup"><span data-stu-id="07904-251">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="07904-252">Usuwa wszystkie zestawy SDK i środowiska uruchomieniowe platformy .NET Core, z wyjątkiem określonych wersji.</span><span class="sxs-lookup"><span data-stu-id="07904-252">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="07904-253">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core, z wyjątkiem jednej najwyższej wersji.</span><span class="sxs-lookup"><span data-stu-id="07904-253">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="07904-254">Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe zastąpione nowszymi poprawkami.</span><span class="sxs-lookup"><span data-stu-id="07904-254">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="07904-255">Ta opcja chroni plik Global. JSON.</span><span class="sxs-lookup"><span data-stu-id="07904-255">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="07904-256">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core oznaczone jako wersje zapoznawcze.</span><span class="sxs-lookup"><span data-stu-id="07904-256">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="07904-257">Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe oznaczone jako wersje zapoznawcze z wyjątkiem tego, który jest najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="07904-257">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="07904-258">Usuwa tylko ASP.NET Core środowiska uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="07904-258">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="07904-259">Usuwa tylko zbiory hostingu platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="07904-259">Removes .NET Core hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="07904-260">Usuwa zestawy .NET Core i środowiska uruchomieniowe, które pasują do określonej `major.minor` wersji.</span><span class="sxs-lookup"><span data-stu-id="07904-260">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="07904-261">Usuwa tylko środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="07904-261">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="07904-262">Usuwa tylko zestawy SDK platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="07904-262">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="07904-263">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="07904-263">Sets the verbosity level.</span></span> <span data-ttu-id="07904-264">Dozwolone wartości to `q[uiet]` , `m[inimal]` , `n[ormal]` , `d[etailed]` i `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="07904-264">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="07904-265">Wartość domyślna to `normal`.</span><span class="sxs-lookup"><span data-stu-id="07904-265">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="07904-266">Musi być używana z `--sdk` , `--runtime` , i `--aspnet-runtime` do usuwania zestawów SDK x64 lub środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="07904-266">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="07904-267">Musi być używana z `--sdk` , `--runtime` , i `--aspnet-runtime` do usuwania zestawów SDK x86 lub środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="07904-267">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="07904-268">**`-y, --yes`** Wykonuje polecenie bez potwierdzenia typu "tak" lub "nie".</span><span class="sxs-lookup"><span data-stu-id="07904-268">**`-y, --yes`** Executes the command without requiring a yes or no confirmation.</span></span>

* <span data-ttu-id="07904-269">**`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="07904-269">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="07904-270">Uwagi:</span><span class="sxs-lookup"><span data-stu-id="07904-270">Notes:</span></span>

1. <span data-ttu-id="07904-271">Dokładnie jeden z `--sdk` , `--runtime` , `--aspnet-runtime` , i `--hosting-bundle` jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="07904-271">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="07904-272">`--all`,,,,,,, `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` `--all-previews-but-latest` `--major-minor` i `[<VERSION>...]` są wyłączne.</span><span class="sxs-lookup"><span data-stu-id="07904-272">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="07904-273">Jeśli `--x64` lub `--x86` nie zostanie określony, zostaną usunięte oba wersje x64 i x86.</span><span class="sxs-lookup"><span data-stu-id="07904-273">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="07904-274">macOS</span><span class="sxs-lookup"><span data-stu-id="07904-274">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="07904-275">Usuwa wszystkie zestawy SDK i środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="07904-275">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="07904-276">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core poniżej określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="07904-276">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="07904-277">Określona wersja pozostanie.</span><span class="sxs-lookup"><span data-stu-id="07904-277">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="07904-278">Usuwa zestawy .NET Core i środowiska uruchomieniowe, z wyjątkiem określonych wersji.</span><span class="sxs-lookup"><span data-stu-id="07904-278">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="07904-279">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core, z wyjątkiem jednej najwyższej wersji.</span><span class="sxs-lookup"><span data-stu-id="07904-279">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="07904-280">Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe zastąpione nowszymi poprawkami.</span><span class="sxs-lookup"><span data-stu-id="07904-280">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="07904-281">Ta opcja chroni plik Global. JSON.</span><span class="sxs-lookup"><span data-stu-id="07904-281">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="07904-282">Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core oznaczone jako wersje zapoznawcze.</span><span class="sxs-lookup"><span data-stu-id="07904-282">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="07904-283">Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe oznaczone jako wersje zapoznawcze z wyjątkiem tego, który jest najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="07904-283">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="07904-284">Usuwa zestawy .NET Core i środowiska uruchomieniowe, które pasują do określonej `major.minor` wersji.</span><span class="sxs-lookup"><span data-stu-id="07904-284">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="07904-285">Usuwa tylko środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="07904-285">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="07904-286">Usuwa tylko zestawy SDK platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="07904-286">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="07904-287">Ustawia poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="07904-287">Sets the verbosity level.</span></span> <span data-ttu-id="07904-288">Dozwolone wartości to `q[uiet]` , `m[inimal]` , `n[ormal]` , `d[etailed]` i `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="07904-288">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="07904-289">Wartość domyślna to `normal`.</span><span class="sxs-lookup"><span data-stu-id="07904-289">The default value is `normal`.</span></span>

* <span data-ttu-id="07904-290">**`-y, --yes`** Wykonuje polecenie bez potwierdzenia Y/N.</span><span class="sxs-lookup"><span data-stu-id="07904-290">**`-y, --yes`** Executes the command without requiring Y/N confirmation.</span></span>
  
* <span data-ttu-id="07904-291">**`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio lub zestawy SDK.</span><span class="sxs-lookup"><span data-stu-id="07904-291">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="07904-292">Uwagi:</span><span class="sxs-lookup"><span data-stu-id="07904-292">Notes:</span></span>

1. <span data-ttu-id="07904-293">Dokładnie jeden z `--sdk` i `--runtime` jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="07904-293">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="07904-294">`--all`,,,,,,, `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` `--all-previews-but-latest` `--major-minor` i `[<VERSION>...]` są wyłączne.</span><span class="sxs-lookup"><span data-stu-id="07904-294">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="07904-295">Przykłady</span><span class="sxs-lookup"><span data-stu-id="07904-295">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="07904-296">Domyślnie są przechowywane zestawy SDK i środowiska uruchomieniowe platformy .NET Core, które mogą być wymagane przez program Visual Studio lub inne zestawy SDK.</span><span class="sxs-lookup"><span data-stu-id="07904-296">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are kept.</span></span> <span data-ttu-id="07904-297">W poniższych przykładach niektóre z określonych zestawów SDK i środowiska uruchomieniowe mogą pozostać w zależności od stanu komputera.</span><span class="sxs-lookup"><span data-stu-id="07904-297">In the following examples, some of the specified SDKs and runtimes may remain, depending on the state of the machine.</span></span> <span data-ttu-id="07904-298">Aby usunąć wszystkie zestawy SDK i środowiska uruchomieniowe, należy je jawnie wystawić jako argumenty lub użyć `--force` opcji.</span><span class="sxs-lookup"><span data-stu-id="07904-298">To remove all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="07904-299">Usuń wszystkie środowiska uruchomieniowe platformy .NET Core z wyjątkiem wersji, która `3.0.0-preview6-27804-01` nie wymaga potwierdzenia Y/N:</span><span class="sxs-lookup"><span data-stu-id="07904-299">Remove all .NET Core runtimes except the version `3.0.0-preview6-27804-01` without requiring Y/N confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* <span data-ttu-id="07904-300">Usuń wszystkie zestawy SDK platformy .NET Core 1,1 bez konieczności potwierdzania Y/n:</span><span class="sxs-lookup"><span data-stu-id="07904-300">Remove all .NET Core 1.1 SDKs without requiring Y/n confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* <span data-ttu-id="07904-301">Usuń zestaw .NET Core 1.1.11 SDK bez danych wyjściowych konsoli:</span><span class="sxs-lookup"><span data-stu-id="07904-301">Remove the .NET Core 1.1.11 SDK with no console output:</span></span>

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* <span data-ttu-id="07904-302">Usuń wszystkie zestawy SDK platformy .NET Core, które można bezpiecznie usunąć za pomocą tego narzędzia:</span><span class="sxs-lookup"><span data-stu-id="07904-302">Remove all .NET Core SDKs that can safely be removed by this tool:</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* <span data-ttu-id="07904-303">Usuń wszystkie zestawy SDK platformy .NET Core, które mogą zostać usunięte przez to narzędzie, w tym zestawy SDK, które mogą być wymagane przez program Visual Studio (niezalecane):</span><span class="sxs-lookup"><span data-stu-id="07904-303">Remove all .NET Core SDKs that can be removed by this tool, including those SDKs that may be required by Visual Studio (not recommended):</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* <span data-ttu-id="07904-304">Usuń wszystkie zestawy SDK platformy .NET Core, które są określone w pliku odpowiedzi`versions.rsp`</span><span class="sxs-lookup"><span data-stu-id="07904-304">Remove all .NET Core SDKs that are specified in the response file `versions.rsp`</span></span>

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  <span data-ttu-id="07904-305">Zawartość *wersji. rsp* jest następująca:</span><span class="sxs-lookup"><span data-stu-id="07904-305">The content of *versions.rsp* is as follows:</span></span>
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a><span data-ttu-id="07904-306">Krok 4. Usuwanie folderu rezerwowego NuGet (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="07904-306">Step 4 - Delete the NuGet fallback folder (optional)</span></span>

<span data-ttu-id="07904-307">W niektórych przypadkach nie jest już potrzebna `NuGetFallbackFolder` i może chcieć ją usunąć.</span><span class="sxs-lookup"><span data-stu-id="07904-307">In some cases, you no longer need the `NuGetFallbackFolder` and may wish to delete it.</span></span> <span data-ttu-id="07904-308">Aby uzyskać więcej informacji na temat usuwania tego folderu, zobacz [usuwanie NuGetFallbackFolder](../install/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span><span class="sxs-lookup"><span data-stu-id="07904-308">For more information about deleting this folder, see [Remove the NuGetFallbackFolder](../install/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span></span>

## <a name="uninstall-the-tool"></a><span data-ttu-id="07904-309">Odinstalowywanie narzędzia</span><span class="sxs-lookup"><span data-stu-id="07904-309">Uninstall the tool</span></span>

## <a name="windows"></a>[<span data-ttu-id="07904-310">Windows</span><span class="sxs-lookup"><span data-stu-id="07904-310">Windows</span></span>](#tab/windows)

1. <span data-ttu-id="07904-311">Otwórz aplet **Dodaj lub usuń programy**.</span><span class="sxs-lookup"><span data-stu-id="07904-311">Open **Add or Remove Programs**.</span></span>
2. <span data-ttu-id="07904-312">Wyszukaj ciąg `Microsoft .NET Core SDK Uninstall Tool`.</span><span class="sxs-lookup"><span data-stu-id="07904-312">Search for `Microsoft .NET Core SDK Uninstall Tool`.</span></span>
3. <span data-ttu-id="07904-313">Wybierz pozycję **Odinstaluj**.</span><span class="sxs-lookup"><span data-stu-id="07904-313">Select **Uninstall**.</span></span>

## <a name="macos"></a>[<span data-ttu-id="07904-314">macOS</span><span class="sxs-lookup"><span data-stu-id="07904-314">macOS</span></span>](#tab/macos)

<span data-ttu-id="07904-315">Usuń pobrany plik *dotnet-Core-Uninstall. tar. gz* z katalogu, w którym został zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="07904-315">Delete the downloaded *dotnet-core-uninstall.tar.gz* file from the directory where it was installed.</span></span> <span data-ttu-id="07904-316">Jeśli zawartość tego pliku została rozpakowany do innego katalogu, pamiętaj, aby usunąć tę zawartość.</span><span class="sxs-lookup"><span data-stu-id="07904-316">If you unzipped the contents of this file into another directory, be sure to delete that content as well.</span></span>

---
