---
title: Rozwiązywanie problemów z korzystaniem z narzędzia .NET Core
description: Poznaj typowe problemy podczas uruchamiania narzędzi .NET Core i możliwych rozwiązań.
author: kdollard
ms.date: 02/14/2020
ms.openlocfilehash: ed6243f802c4d3ce56a742916a1a28676e3cd876
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146453"
---
# <a name="troubleshoot-net-core-tool-usage-issues"></a><span data-ttu-id="6eeb7-103">Rozwiązywanie problemów z korzystaniem z narzędzia .NET Core</span><span class="sxs-lookup"><span data-stu-id="6eeb7-103">Troubleshoot .NET Core tool usage issues</span></span>

<span data-ttu-id="6eeb7-104">Możesz napotkać problemy podczas próby zainstalowania lub uruchomienia narzędzia .NET Core, które może być narzędziem globalnym lub lokalnym.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-104">You might come across issues when trying to install or run a .NET Core tool, which can be a global tool or a local tool.</span></span> <span data-ttu-id="6eeb7-105">W tym artykule opisano typowe przyczyny główne i niektóre możliwe rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-105">This article describes the common root causes and some possible solutions.</span></span>

## <a name="installed-net-core-tool-fails-to-run"></a><span data-ttu-id="6eeb7-106">Nie można uruchomić narzędzia Installed .NET Core</span><span class="sxs-lookup"><span data-stu-id="6eeb7-106">Installed .NET Core tool fails to run</span></span>

<span data-ttu-id="6eeb7-107">Gdy narzędzie .NET Core nie działa, najprawdopodobniej napotkałeś jeden z następujących problemów:</span><span class="sxs-lookup"><span data-stu-id="6eeb7-107">When a .NET Core tool fails to run, most likely you ran into one of the following issues:</span></span>

* <span data-ttu-id="6eeb7-108">Nie znaleziono pliku wykonywalnego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-108">The executable file for the tool wasn't found.</span></span>
* <span data-ttu-id="6eeb7-109">Nie znaleziono poprawnej wersji programu uruchomieniowego .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-109">The correct version of the .NET Core runtime wasn't found.</span></span>

### <a name="executable-file-not-found"></a><span data-ttu-id="6eeb7-110">Nie znaleziono pliku wykonywalnego</span><span class="sxs-lookup"><span data-stu-id="6eeb7-110">Executable file not found</span></span>

<span data-ttu-id="6eeb7-111">Jeśli plik wykonywalny nie zostanie znaleziony, zostanie wyświetlony komunikat podobny do następującego:</span><span class="sxs-lookup"><span data-stu-id="6eeb7-111">If the executable file isn't found, you'll see a message similar to the following:</span></span>

```console
Could not execute because the specified command or file was not found.
Possible reasons for this include:
  * You misspelled a built-in dotnet command.
  * You intended to execute a .NET Core program, but dotnet-xyz does not exist.
  * You intended to run a global tool, but a dotnet-prefixed executable with this name could not be found on the PATH.
```

<span data-ttu-id="6eeb7-112">Nazwa pliku wykonywalnego określa sposób wywoływania narzędzia.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-112">The name of the executable determines how you invoke the tool.</span></span> <span data-ttu-id="6eeb7-113">W poniższej tabeli opisano format:</span><span class="sxs-lookup"><span data-stu-id="6eeb7-113">The following table describes the format:</span></span>

| <span data-ttu-id="6eeb7-114">Format nazwy wykonywalnej</span><span class="sxs-lookup"><span data-stu-id="6eeb7-114">Executable name format</span></span>  | <span data-ttu-id="6eeb7-115">Format wywołania</span><span class="sxs-lookup"><span data-stu-id="6eeb7-115">Invocation format</span></span>   |
|-------------------------|---------------------|
| `dotnet-<toolName>.exe` | `dotnet <toolName>` |
| `<toolName>.exe`        | `<toolName>`        |

* <span data-ttu-id="6eeb7-116">Narzędzia globalne</span><span class="sxs-lookup"><span data-stu-id="6eeb7-116">Global tools</span></span>

  <span data-ttu-id="6eeb7-117">Narzędzia globalne można instalować w katalogu domyślnym lub w określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-117">Global tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="6eeb7-118">Katalogi domyślne to:</span><span class="sxs-lookup"><span data-stu-id="6eeb7-118">The default directories are:</span></span>

  | <span data-ttu-id="6eeb7-119">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="6eeb7-119">OS</span></span>          | <span data-ttu-id="6eeb7-120">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="6eeb7-120">Path</span></span>                          |
  |-------------|-------------------------------|
  | <span data-ttu-id="6eeb7-121">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="6eeb7-121">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
  | <span data-ttu-id="6eeb7-122">Windows</span><span class="sxs-lookup"><span data-stu-id="6eeb7-122">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

  <span data-ttu-id="6eeb7-123">Jeśli próbujesz uruchomić narzędzie globalne, sprawdź, czy zmienna `PATH` środowiskowa na komputerze zawiera ścieżkę, w której zainstalowano narzędzie globalne i czy plik wykonywalny znajduje się w tej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-123">If you're trying to run a global tool, check that the `PATH` environment variable on your machine contains the path where you installed the global tool and that the executable is in that path.</span></span>

  <span data-ttu-id="6eeb7-124">Polecenie CLI programu .NET Core próbuje dodać domyślną lokalizację do zmiennej środowiskowej PATH przy pierwszym użyciu.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-124">The .NET Core CLI tries to add the default location to the PATH environment variable on its first usage.</span></span> <span data-ttu-id="6eeb7-125">Istnieją jednak pewne scenariusze, w których lokalizacja może nie zostać automatycznie dodana do PATH:</span><span class="sxs-lookup"><span data-stu-id="6eeb7-125">However, there are some scenarios where the location might not be added to PATH automatically:</span></span>

  * <span data-ttu-id="6eeb7-126">Jeśli używasz systemu Linux i zainstalowano sdk .NET Core przy użyciu plików *.tar.gz,* a nie apt-get lub rpm.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-126">If you're using Linux and you've installed the .NET Core SDK using *.tar.gz* files and not apt-get or rpm.</span></span>
  * <span data-ttu-id="6eeb7-127">Jeśli używasz systemu macOS 10.15 "Catalina" lub nowsze wersje.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-127">If you're using macOS 10.15 "Catalina" or later versions.</span></span>
  * <span data-ttu-id="6eeb7-128">Jeśli używasz systemu macOS 10.14 "Mojave" lub wcześniejszych wersji, a pakiet SDK .NET Core został zainstalowany przy użyciu plików *.tar.gz,* a nie *.pkg*.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-128">If you're using macOS 10.14 "Mojave" or earlier versions, and you've installed the .NET Core SDK using *.tar.gz* files and not *.pkg*.</span></span>
  * <span data-ttu-id="6eeb7-129">Jeśli zainstalowano zestaw SDK .NET Core 3.0 i `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` ustawiono zmienną środowiskową na `false`.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-129">If you've installed the .NET Core 3.0 SDK and you've set the `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` environment variable to `false`.</span></span>
  * <span data-ttu-id="6eeb7-130">Jeśli zainstalowano zestaw SDK programu .NET Core 2.2 lub wcześniejsze `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` wersje, ustawiono zmienną środowiskową na `true`.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-130">If you've installed .NET Core 2.2 SDK or earlier versions, and you've set the `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` environment variable to `true`.</span></span>

  <span data-ttu-id="6eeb7-131">W tych scenariuszach lub jeśli `--tool-path` określono `PATH` opcję, zmienna środowiskowa na komputerze nie zawiera automatycznie ścieżki, w której zainstalowano narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-131">In these scenarios or if you specified the `--tool-path` option, the `PATH` environment variable on your machine doesn't automatically contain the path where you installed the global tool.</span></span> <span data-ttu-id="6eeb7-132">W takim przypadku dołącz lokalizację narzędzia `$HOME/.dotnet/tools`(na `PATH` przykład) do zmiennej środowiskowej przy użyciu dowolnej metody, jaką zapewnia powłoka do aktualizowania zmiennych środowiskowych.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-132">In that case, append the tool location (for example, `$HOME/.dotnet/tools`) to the `PATH` environment variable by using whatever method your shell provides for updating environment variables.</span></span> <span data-ttu-id="6eeb7-133">Aby uzyskać więcej informacji, zobacz [narzędzia .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="6eeb7-133">For more information, see [.NET Core tools](global-tools.md).</span></span>

* <span data-ttu-id="6eeb7-134">Narzędzia lokalne</span><span class="sxs-lookup"><span data-stu-id="6eeb7-134">Local tools</span></span>

  <span data-ttu-id="6eeb7-135">Jeśli próbujesz uruchomić narzędzie lokalne, sprawdź, czy w bieżącym katalogu lub dowolnych katalogach nadrzędnych znajduje się plik manifestu o nazwie *dotnet-tools.json.*</span><span class="sxs-lookup"><span data-stu-id="6eeb7-135">If you're trying to run a local tool, verify that there's a manifest file called *dotnet-tools.json* in the current directory or any of its parent directories.</span></span> <span data-ttu-id="6eeb7-136">Ten plik może również działać w folderze o nazwie *.config* w dowolnym miejscu w hierarchii folderów projektu, a nie w folderze głównym.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-136">This file can also live under a folder named *.config* anywhere in the project folder hierarchy, instead of the root folder.</span></span> <span data-ttu-id="6eeb7-137">Jeśli *istnieje dotnet-tools.json,* otwórz go i sprawdź, czy narzędzie, które próbujesz uruchomić.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-137">If *dotnet-tools.json* exists, open it and check for the tool you're trying to run.</span></span> <span data-ttu-id="6eeb7-138">Jeśli plik nie zawiera wpisu `"isRoot": true`dla , a następnie również sprawdzić dalej hierarchii plików dla dodatkowych plików manifestu narzędzia.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-138">If the file doesn't contain an entry for `"isRoot": true`, then also check further up the file hierarchy for additional tool manifest files.</span></span>

  <span data-ttu-id="6eeb7-139">Jeśli próbujesz uruchomić narzędzie .NET Core, które zostało zainstalowane z określoną ścieżką, musisz uwzględnić tę ścieżkę podczas korzystania z narzędzia.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-139">If you're trying to run a .NET Core tool that was installed with a specified path, you need to include that path when using the tool.</span></span> <span data-ttu-id="6eeb7-140">Przykładem użycia narzędzia zainstalowanego ścieżką narzędzia jest:</span><span class="sxs-lookup"><span data-stu-id="6eeb7-140">An example of using a tool-path installed tool is:</span></span>

  ```console
  ..\<toolDirectory>\dotnet-<toolName>
  ```

### <a name="runtime-not-found"></a><span data-ttu-id="6eeb7-141">Nie znaleziono czasu wykonywania</span><span class="sxs-lookup"><span data-stu-id="6eeb7-141">Runtime not found</span></span>

<span data-ttu-id="6eeb7-142">Narzędzia .NET Core są [aplikacjami zależnymi od struktury,](../deploying/index.md#publish-runtime-dependent)co oznacza, że opierają się na czasie uruchomieniowym .NET Core zainstalowanym na komputerze.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-142">.NET Core tools are [framework-dependent applications](../deploying/index.md#publish-runtime-dependent), which means they rely on a .NET Core runtime installed on your machine.</span></span> <span data-ttu-id="6eeb7-143">Jeśli oczekiwany czas wykonywania nie zostanie znaleziony, są one zgodne z normalnymi regułami realizacji programu .NET Core, takimi jak:</span><span class="sxs-lookup"><span data-stu-id="6eeb7-143">If the expected runtime isn't found, they follow normal .NET Core runtime roll-forward rules such as:</span></span>

* <span data-ttu-id="6eeb7-144">Aplikacja jest przerzucana do najwyższej wersji poprawki określonej wersji głównej i pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-144">An application rolls forward to the highest patch release of the specified major and minor version.</span></span>
* <span data-ttu-id="6eeb7-145">Jeśli nie ma pasującego czasu uruchomieniowego z pasującym numerem wersji głównej i pomocniczej, używana jest następna wyższa wersja pomocnicza.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-145">If there's no matching runtime with a matching major and minor version number, the next higher minor version is used.</span></span>
* <span data-ttu-id="6eeb7-146">Roll forward nie występuje między wersjami podglądu w czasie wykonywania lub między wersjami w wersji zapoznawczej i wersjami wersji.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-146">Roll forward doesn't occur between preview versions of the runtime or between preview versions and release versions.</span></span> <span data-ttu-id="6eeb7-147">Tak, .NET Core narzędzia utworzone przy użyciu wersji podglądu muszą być przebudowane i ponownie opublikowane przez autora i ponownie zainstalować.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-147">So, .NET Core tools created using preview versions must be rebuilt and republished by the author and reinstalled.</span></span>

<span data-ttu-id="6eeb7-148">Roll-forward nie nastąpi domyślnie w dwóch typowych scenariuszach:</span><span class="sxs-lookup"><span data-stu-id="6eeb7-148">Roll-forward won't occur by default in two common scenarios:</span></span>

* <span data-ttu-id="6eeb7-149">Dostępne są tylko niższe wersje programu runtime.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-149">Only lower versions of the runtime are available.</span></span> <span data-ttu-id="6eeb7-150">Roll-forward wybiera tylko nowsze wersje czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-150">Roll-forward only selects later versions of the runtime.</span></span>
* <span data-ttu-id="6eeb7-151">Dostępne są tylko wyższe wersje główne programu runtime.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-151">Only higher major versions of the runtime are available.</span></span> <span data-ttu-id="6eeb7-152">Roll-forward nie przekracza granic głównych wersji.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-152">Roll-forward doesn't cross major version boundaries.</span></span>

<span data-ttu-id="6eeb7-153">Jeśli aplikacja nie może znaleźć odpowiedniego czasu uruchomienia, nie można uruchomić i zgłasza błąd.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-153">If an application can't find an appropriate runtime, it fails to run and reports an error.</span></span>

<span data-ttu-id="6eeb7-154">Możesz dowiedzieć się, które programy uruchomieniowe programu .NET Core są zainstalowane na komputerze za pomocą jednego z następujących poleceń:</span><span class="sxs-lookup"><span data-stu-id="6eeb7-154">You can find out which .NET Core runtimes are installed on your machine using one of the following commands:</span></span>

```dotnetcli
dotnet --list-runtimes
dotnet --info
```

<span data-ttu-id="6eeb7-155">Jeśli uważasz, że narzędzie powinno obsługiwać aktualnie zainstalowaną wersję wykonywania, możesz skontaktować się z autorem narzędzia i sprawdzić, czy można zaktualizować numer wersji lub wiele celów.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-155">If you think the tool should support the runtime version you currently have installed, you can contact the tool author and see if they can update the version number or multi-target.</span></span> <span data-ttu-id="6eeb7-156">Po ponownym skompilowaniu i ponownym opublikowaniu pakietu narzędzi do NuGet ze zaktualizowanym numerem wersji można zaktualizować kopię.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-156">Once they've recompiled and republished their tool package to NuGet with an updated version number, you can update your copy.</span></span> <span data-ttu-id="6eeb7-157">Chociaż tak się nie dzieje, najszybszym rozwiązaniem dla Ciebie jest zainstalowanie wersji czasu wykonywania, która będzie działać z narzędziem, które próbujesz uruchomić.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-157">While that doesn't happen, the quickest solution for you is to install a version of the runtime that would work with the tool you're trying to run.</span></span> <span data-ttu-id="6eeb7-158">Aby pobrać określoną wersję programu .NET Core, odwiedź [stronę pobierania .NET Core](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="6eeb7-158">To download a specific .NET Core runtime version, visit the [.NET Core download page](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="6eeb7-159">Jeśli instalujesz zestaw SDK .NET Core w lokalizacji niedomyślnej, należy ustawić zmienną środowiskową `DOTNET_ROOT` na katalog zawierający `dotnet` plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-159">If you install the .NET Core SDK to a non-default location, you need to set the environment variable `DOTNET_ROOT` to the directory that contains the `dotnet` executable.</span></span>

## <a name="net-core-tool-installation-fails"></a><span data-ttu-id="6eeb7-160">Instalacja narzędzia .NET Core nie powiodła się</span><span class="sxs-lookup"><span data-stu-id="6eeb7-160">.NET Core tool installation fails</span></span>

<span data-ttu-id="6eeb7-161">Istnieje wiele przyczyn, dla których instalacja narzędzia globalnego lub lokalnego .NET Core może zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-161">There are a number of reasons the installation of a .NET Core global or local tool may fail.</span></span> <span data-ttu-id="6eeb7-162">Gdy instalacja narzędzia nie powiedzie się, zostanie wyświetlony komunikat podobny do następującego:</span><span class="sxs-lookup"><span data-stu-id="6eeb7-162">When the tool installation fails, you'll see a message similar to the following one:</span></span>

```console
Tool '{0}' failed to install. This failure may have been caused by:

* You are attempting to install a preview release and did not use the --version option to specify the version.
* A package by this name was found, but it was not a .NET Core tool.
* The required NuGet feed cannot be accessed, perhaps because of an Internet connection problem.
* You mistyped the name of the tool.

For more reasons, including package naming enforcement, visit https://aka.ms/failure-installing-tool
```

<span data-ttu-id="6eeb7-163">Aby ułatwić diagnozowanie tych błędów, komunikaty NuGet są wyświetlane bezpośrednio do użytkownika, wraz z poprzednim komunikatem.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-163">To help diagnose these failures, NuGet messages are shown directly to the user, along with the previous message.</span></span> <span data-ttu-id="6eeb7-164">Komunikat NuGet może pomóc w zidentyfikowaniu problemu.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-164">The NuGet message may help you identify the problem.</span></span>

### <a name="package-naming-enforcement"></a><span data-ttu-id="6eeb7-165">Wymuszanie nazewnictwa pakietów</span><span class="sxs-lookup"><span data-stu-id="6eeb7-165">Package naming enforcement</span></span>

<span data-ttu-id="6eeb7-166">Firma Microsoft zmieniła swoje wytyczne dotyczące identyfikatora pakietu dla narzędzi, co spowodowało, że wiele narzędzi nie zostało znalezionych z przewidywaną nazwą.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-166">Microsoft has changed its guidance on the Package ID for tools, resulting in a number of tools not being found with the predicted name.</span></span> <span data-ttu-id="6eeb7-167">Nowe wskazówki są takie, że wszystkie narzędzia firmy Microsoft są poprzedzone "Microsoft".</span><span class="sxs-lookup"><span data-stu-id="6eeb7-167">The new guidance is that all Microsoft tools be prefixed with "Microsoft."</span></span> <span data-ttu-id="6eeb7-168">Ten prefiks jest zarezerwowany i może być używany tylko dla pakietów podpisanych certyfikatem autoryzowanym przez firmę Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-168">This prefix is reserved and can only be used for packages signed with a Microsoft authorized certificate.</span></span>

<span data-ttu-id="6eeb7-169">Podczas przejścia niektóre narzędzia firmy Microsoft będą miały starą formę identyfikatora pakietu, podczas gdy inne będą miały nowy formularz:</span><span class="sxs-lookup"><span data-stu-id="6eeb7-169">During the transition, some Microsoft tools will have the old form of the package ID, while others will have the new form:</span></span>

```dotnetcli
dotnet tool install -g Microsoft.<toolName>
dotnet tool install -g <toolName>
```

<span data-ttu-id="6eeb7-170">W miarę aktualizowania identyfikatorów pakietów należy zmienić nowy identyfikator pakietu, aby otrzymywać najnowsze aktualizacje.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-170">As package IDs are updated, you'll need to change to the new package ID to get the latest updates.</span></span> <span data-ttu-id="6eeb7-171">Pakiety z uproszczoną nazwą narzędzia zostaną przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-171">Packages with the simplified tool name will be deprecated.</span></span>

### <a name="preview-releases"></a><span data-ttu-id="6eeb7-172">Wersje podglądu</span><span class="sxs-lookup"><span data-stu-id="6eeb7-172">Preview releases</span></span>

* <span data-ttu-id="6eeb7-173">Próbujesz zainstalować wersję zawersji zapoznawczej `--version` i nie używasz opcji, aby określić wersję.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-173">You're attempting to install a preview release and didn't use the `--version` option to specify the version.</span></span>

<span data-ttu-id="6eeb7-174">Narzędzia .NET Core, które są w wersji zapoznawczej, muszą być określone z częścią nazwy, aby wskazać, że są one w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-174">.NET Core tools that are in preview must be specified with a portion of the name to indicate that they are in preview.</span></span> <span data-ttu-id="6eeb7-175">Nie musisz dołączać całego podglądu.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-175">You don't need to include the entire preview.</span></span> <span data-ttu-id="6eeb7-176">Zakładając, że numery wersji są w oczekiwanym formacie, można użyć czegoś takiego jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="6eeb7-176">Assuming the version numbers are in the expected format, you can use something like the following example:</span></span>

```dotnetcli
dotnet tool install -g --version 1.1.0-pre <toolName>
```

### <a name="package-isnt-a-net-core-tool"></a><span data-ttu-id="6eeb7-177">Pakiet nie jest narzędziem .NET Core</span><span class="sxs-lookup"><span data-stu-id="6eeb7-177">Package isn't a .NET Core tool</span></span>

* <span data-ttu-id="6eeb7-178">Znaleziono pakiet NuGet o tej nazwie, ale nie było to narzędzie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-178">A NuGet package by this name was found, but it wasn't a .NET Core tool.</span></span>

<span data-ttu-id="6eeb7-179">Jeśli spróbujesz zainstalować pakiet NuGet, który jest zwykłym pakietem NuGet, a nie narzędziem .NET Core, zobaczysz błąd podobny do następującego:</span><span class="sxs-lookup"><span data-stu-id="6eeb7-179">If you try to install a NuGet package that is a regular NuGet package and not a .NET Core tool, you'll see an error similar to the following:</span></span>

> <span data-ttu-id="6eeb7-180">NU1212: Nieprawidłowa kombinacja `<ToolName>`pakietu projektowego dla .</span><span class="sxs-lookup"><span data-stu-id="6eeb7-180">NU1212: Invalid project-package combination for `<ToolName>`.</span></span> <span data-ttu-id="6eeb7-181">Styl projektu DotnetToolReference może zawierać tylko odwołania do typu DotnetTool.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-181">DotnetToolReference project style can only contain references of the DotnetTool type.</span></span>

### <a name="nuget-feed-cant-be-accessed"></a><span data-ttu-id="6eeb7-182">Nie można uzyskać dostępu do kanału NuGet</span><span class="sxs-lookup"><span data-stu-id="6eeb7-182">NuGet feed can't be accessed</span></span>

* <span data-ttu-id="6eeb7-183">Wymagany kanał nuget nie jest dostępny, być może z powodu problemu z połączeniem internetowym.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-183">The required NuGet feed can't be accessed, perhaps because of an Internet connection problem.</span></span>

<span data-ttu-id="6eeb7-184">Instalacja narzędzia wymaga dostępu do źródła danych NuGet, który zawiera pakiet narzędzi.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-184">Tool installation requires access to the NuGet feed that contains the tool package.</span></span> <span data-ttu-id="6eeb7-185">Nie powiedzie się, jeśli kanał nie jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-185">It fails if the feed isn't available.</span></span> <span data-ttu-id="6eeb7-186">Można zmieniać kanały `nuget.config`informacyjne za `nuget.config` pomocą, żądać określonego `--add-source` pliku lub określać dodatkowe źródła danych za pomocą przełącznika.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-186">You can alter feeds with `nuget.config`, request a specific `nuget.config` file, or specify additional feeds with the `--add-source` switch.</span></span> <span data-ttu-id="6eeb7-187">Domyślnie NuGet zgłasza błąd dla dowolnego źródła danych, który nie może się połączyć.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-187">By default, NuGet throws an error for any feed that can't connect.</span></span> <span data-ttu-id="6eeb7-188">Flaga `--ignore-failed-sources` może pominąć te nieosiągalne źródła.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-188">The flag `--ignore-failed-sources` can skip these non-reachable sources.</span></span>

### <a name="package-id-incorrect"></a><span data-ttu-id="6eeb7-189">Identyfikator pakietu niepoprawny</span><span class="sxs-lookup"><span data-stu-id="6eeb7-189">Package ID incorrect</span></span>

* <span data-ttu-id="6eeb7-190">Nazwa narzędzia została błędnie wpisana.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-190">You mistyped the name of the tool.</span></span>

<span data-ttu-id="6eeb7-191">Częstą przyczyną niepowodzenia jest to, że nazwa narzędzia nie jest poprawna.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-191">A common reason for failure is that the tool name isn't correct.</span></span> <span data-ttu-id="6eeb7-192">Może się to zdarzyć z powodu mistyping, lub dlatego, że narzędzie zostało przeniesione lub przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-192">This can happen because of mistyping, or because the tool has moved or been deprecated.</span></span> <span data-ttu-id="6eeb7-193">W przypadku narzędzi na NuGet.org jednym ze sposobów upewnienia się, że nazwa jest poprawna, jest wyszukanie narzędzia w NuGet.org i skopiowanie polecenia instalacji.</span><span class="sxs-lookup"><span data-stu-id="6eeb7-193">For tools on NuGet.org, one way to ensure you have the name correct is to search for the tool at NuGet.org and copy the installation command.</span></span>

## <a name="see-also"></a><span data-ttu-id="6eeb7-194">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6eeb7-194">See also</span></span>

* [<span data-ttu-id="6eeb7-195">Narzędzia .NET Core</span><span class="sxs-lookup"><span data-stu-id="6eeb7-195">.NET Core tools</span></span>](global-tools.md)
