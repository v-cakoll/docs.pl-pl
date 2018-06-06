---
title: Narzędzia globalne .NET core
description: Omówienie narzędzia globalne .NET Core i dostępne dla nich polecenia interfejsu wiersza polecenia platformy .NET Core.
author: KathleenDollard
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 077ffd53f1ba2988c80a637aaa109a66139736b0
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34697095"
---
# <a name="net-core-global-tools-overview"></a><span data-ttu-id="35466-103">Omówienie narzędzia globalne .NET core</span><span class="sxs-lookup"><span data-stu-id="35466-103">.NET Core Global Tools overview</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

<span data-ttu-id="35466-104">Narzędzie globalne .NET Core to specjalne pakietu NuGet, który zawiera aplikację konsoli.</span><span class="sxs-lookup"><span data-stu-id="35466-104">A .NET Core Global Tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="35466-105">Narzędzie globalne można zainstalować na komputerze w domyślnej lokalizacji, która jest zawarta w zmiennej środowiskowej PATH lub w lokalizacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="35466-105">A Global Tool can be installed on your machine on a default location that is included in the PATH environment variable or on a custom location.</span></span>

<span data-ttu-id="35466-106">Jeśli chcesz użyć narzędzia globalne .NET Core:</span><span class="sxs-lookup"><span data-stu-id="35466-106">If you want to use a .NET Core Global Tool:</span></span>

* <span data-ttu-id="35466-107">Informacje o narzędziu (zazwyczaj witryny sieci Web lub stronie GitHub).</span><span class="sxs-lookup"><span data-stu-id="35466-107">Find information about the tool (usually a website or GitHub page).</span></span>
* <span data-ttu-id="35466-108">Sprawdź autora i statystyki w domu dla źródła danych (zazwyczaj NuGet.org).</span><span class="sxs-lookup"><span data-stu-id="35466-108">Check the author and statistics in the home for the feed (usually NuGet.org).</span></span>
* <span data-ttu-id="35466-109">Zainstaluj narzędzie.</span><span class="sxs-lookup"><span data-stu-id="35466-109">Install the tool.</span></span>
* <span data-ttu-id="35466-110">Wywołuje narzędzie.</span><span class="sxs-lookup"><span data-stu-id="35466-110">Call the tool.</span></span>
* <span data-ttu-id="35466-111">Zaktualizuj narzędzia.</span><span class="sxs-lookup"><span data-stu-id="35466-111">Update the tool.</span></span>
* <span data-ttu-id="35466-112">Odinstaluj narzędzie.</span><span class="sxs-lookup"><span data-stu-id="35466-112">Uninstall the tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="35466-113">Narzędzia globalne .NET core pojawiają się na ścieżce i uruchom w trybie pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="35466-113">.NET Core Global Tools appear on your path and run in full trust.</span></span> <span data-ttu-id="35466-114">Nie należy instalować narzędzia globalne .NET Core, chyba że zaufania do autora.</span><span class="sxs-lookup"><span data-stu-id="35466-114">Do not install .NET Core Global Tools unless you trust the author.</span></span>

## <a name="find-a-net-core-global-tool"></a><span data-ttu-id="35466-115">Znajdowanie narzędzia globalne .NET Core</span><span class="sxs-lookup"><span data-stu-id="35466-115">Find a .NET Core Global Tool</span></span>

<span data-ttu-id="35466-116">Obecnie nie ma funkcji wyszukiwania globalnego narzędzia w .NET Core interfejsu wiersza polecenia (CLI).</span><span class="sxs-lookup"><span data-stu-id="35466-116">Currently, there isn't a Global Tool search feature in the .NET Core Command-line Interface (CLI).</span></span>

<span data-ttu-id="35466-117">Narzędzia globalne .NET Core można znaleźć na [NuGet](https://www.nuget.org).</span><span class="sxs-lookup"><span data-stu-id="35466-117">You can find .NET Core Global Tools on [NuGet](https://www.nuget.org).</span></span> <span data-ttu-id="35466-118">Jednak w NuGet wyszukiwania w szczególności .NET Core globalne narzędzi jeszcze nie zezwala.</span><span class="sxs-lookup"><span data-stu-id="35466-118">However, NuGet doesn't yet allow you to search specifically for .NET Core Global Tools.</span></span>

<span data-ttu-id="35466-119">Można również znaleźć zaleceniami w blogach lub w [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="35466-119">You may also find tool recommendations in blog posts or in the [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub repository.</span></span>

<span data-ttu-id="35466-120">Można również Zobacz kod źródłowy dla globalnych narzędzi utworzone przez zespół ASP.NET [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="35466-120">You can also see the source code for the Global Tools created by the ASP.NET team at the [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub repository.</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="35466-121">Sprawdź autora i statystyki</span><span class="sxs-lookup"><span data-stu-id="35466-121">Check the author and statistics</span></span>

<span data-ttu-id="35466-122">Ponieważ .NET Core globalne narzędzia uruchamiania w trybie pełnego zaufania i są zazwyczaj instalowana na ścieżce, mogą być bardzo zaawansowane.</span><span class="sxs-lookup"><span data-stu-id="35466-122">Since .NET Core Global Tools run in full trust and are generally installed on your path, they can be very powerful.</span></span> <span data-ttu-id="35466-123">Nie pobieraj narzędzia od osób, którym nie ufasz.</span><span class="sxs-lookup"><span data-stu-id="35466-123">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="35466-124">Narzędzie znajduje się na NuGet, wyszukując dla tego narzędzia można sprawdzić autorowi i statystyki.</span><span class="sxs-lookup"><span data-stu-id="35466-124">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="35466-125">Zainstaluj narzędzie globalne</span><span class="sxs-lookup"><span data-stu-id="35466-125">Install a Global Tool</span></span>

<span data-ttu-id="35466-126">Aby zainstalować narzędzie globalne, należy użyć [instalacji narzędzi dotnet](dotnet-tool-install.md) polecenia interfejsu wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="35466-126">To install a Global Tool, you use the [dotnet tool install](dotnet-tool-install.md) .NET Core CLI command.</span></span> <span data-ttu-id="35466-127">Poniższy przykład pokazuje, jak zainstalować narzędzie globalne w domyślnej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="35466-127">The following example shows how to install a Global Tool in the default location:</span></span>

```console
dotnet tool install -g dotnetsay
```

<span data-ttu-id="35466-128">Jeśli nie można zainstalować narzędzie, wyświetlane są komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="35466-128">If the tool can't be installed, error messages are displayed.</span></span> <span data-ttu-id="35466-129">Sprawdź, że źródła danych, które miały jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="35466-129">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="35466-130">Jeśli próbujesz zainstalować wersji wstępnej lub określoną wersję narzędzia, można określić numeru wersji w następującym formacie:</span><span class="sxs-lookup"><span data-stu-id="35466-130">If you're trying to install a pre-release version or a specific version of the tool, you can specify the version number using the following format:</span></span>

```console
dotnet tool install -g <package-name> --version <version-number>
```

<span data-ttu-id="35466-131">Jeśli instalacja zakończy się pomyślnie, zostanie wyświetlony komunikat przedstawiający polecenia używane do wywoływania narzędzia i wersją zainstalowaną, podobnie do poniższego przykładu:</span><span class="sxs-lookup"><span data-stu-id="35466-131">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

<span data-ttu-id="35466-132">Globalne narzędzia można zainstalować w domyślnym katalogiem lub w określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="35466-132">Global Tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="35466-133">Domyślne katalogi są:</span><span class="sxs-lookup"><span data-stu-id="35466-133">The default directories are:</span></span>

| <span data-ttu-id="35466-134">SYSTEM OPERACYJNY</span><span class="sxs-lookup"><span data-stu-id="35466-134">OS</span></span>          | <span data-ttu-id="35466-135">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="35466-135">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="35466-136">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="35466-136">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="35466-137">Windows</span><span class="sxs-lookup"><span data-stu-id="35466-137">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="35466-138">Lokalizacje te są dodawane do ścieżki użytkownika po pierwszym uruchomieniu zestawu SDK, więc globalne narzędzia są zainstalowane, można wywołać bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="35466-138">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="35466-139">Należy pamiętać, że globalne narzędzia są specyficzne dla użytkownika, nie urządzenia globalnego.</span><span class="sxs-lookup"><span data-stu-id="35466-139">Note that the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="35466-140">Trwa specyficzne dla użytkownika oznacza, że nie można zainstalować narzędzie globalne, które jest dostępna dla wszystkich użytkowników maszyny.</span><span class="sxs-lookup"><span data-stu-id="35466-140">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="35466-141">Narzędzie jest dostępna tylko dla każdego profilu użytkownika którym zostało zainstalowane narzędzie.</span><span class="sxs-lookup"><span data-stu-id="35466-141">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="35466-142">Globalne narzędzia można również zainstalować z określonego katalogu.</span><span class="sxs-lookup"><span data-stu-id="35466-142">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="35466-143">Podczas instalowania z określonego katalogu, użytkownik musi upewnić się, to polecenie jest dostępne, umieszczając ten katalog w ścieżce, przez wywołanie polecenia z określony katalog, lub narzędzie z określonego katalogu.</span><span class="sxs-lookup"><span data-stu-id="35466-143">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="35466-144">W takim przypadku .NET Core interfejsu wiersza polecenia nie automatycznie dodać tej lokalizacji, do zmiennej środowiskowej PATH.</span><span class="sxs-lookup"><span data-stu-id="35466-144">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="use-the-tool"></a><span data-ttu-id="35466-145">Użyj narzędzia</span><span class="sxs-lookup"><span data-stu-id="35466-145">Use the tool</span></span>

<span data-ttu-id="35466-146">Po zainstalowaniu narzędzia można wywołać ją przy użyciu polecenia.</span><span class="sxs-lookup"><span data-stu-id="35466-146">Once the tool is installed, you can call it by using its command.</span></span> <span data-ttu-id="35466-147">Należy pamiętać, że polecenie nie może być taka sama jak nazwa pakietu.</span><span class="sxs-lookup"><span data-stu-id="35466-147">Note that the command may not be the same as the package name.</span></span>

<span data-ttu-id="35466-148">Jeśli polecenie jest `dotnetsay`, za pomocą wywołania:</span><span class="sxs-lookup"><span data-stu-id="35466-148">If the command is `dotnetsay`, you call it with:</span></span>

```console
dotnetsay
```

<span data-ttu-id="35466-149">Jeśli narzędzie autora chciał narzędzia pojawią się w kontekście `dotnet` wierszu one może napisano go w sposób wywołać go jako `dotnet <command>`, takich jak:</span><span class="sxs-lookup"><span data-stu-id="35466-149">If the tool author wanted the tool to appear in the context of the `dotnet` prompt, they may have written it in a way that you call it as `dotnet <command>`, such as:</span></span>

```console
dotnet doc
```

<span data-ttu-id="35466-150">Można znaleźć narzędzia znajdują się w zainstalowanym pakietem narzędzie globalne przez wyświetlanie listy zainstalowanych pakietów przy użyciu [lista narzędzi dotnet](dotnet-tool-list.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="35466-150">You can find which tools are included in an installed Global Tool package by listing the installed packages using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

<span data-ttu-id="35466-151">Można także wyszukać instrukcje użycia w witrynie sieci Web narzędzia lub wpisując jedno z następujących poleceń:</span><span class="sxs-lookup"><span data-stu-id="35466-151">You can also look for usage instructions at the tool's website or by typing one of the following commands:</span></span>

```console
<command> --help
dotnet <command> --help
```

### <a name="what-could-go-wrong"></a><span data-ttu-id="35466-152">Co można udaje</span><span class="sxs-lookup"><span data-stu-id="35466-152">What could go wrong</span></span>

<span data-ttu-id="35466-153">Narzędzia globalnych są [aplikacje zależne od framework](../deploying/index.md#framework-dependent-deployments-fdd), co oznacza, że opierają się na podstawowego środowiska wykonawczego .NET zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="35466-153">Global Tools are [framework-dependent applications](../deploying/index.md#framework-dependent-deployments-fdd), which means they rely on a .NET Core runtime installed on your machine.</span></span> <span data-ttu-id="35466-154">Nie znaleziono oczekiwanego środowiska uruchomieniowego, należy wykonać normalnych reguł przewijaniem do środowiska wykonawczego platformy .NET Core takich jak:</span><span class="sxs-lookup"><span data-stu-id="35466-154">If the expected runtime is not found, they follow normal .NET Core runtime roll-forward rules such as:</span></span>

* <span data-ttu-id="35466-155">Aplikacja do przodu przedstawia do najwyższej wersji poprawki określonej wersji głównej i pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="35466-155">An application rolls forward to the highest patch release of the specified major and minor version.</span></span>
* <span data-ttu-id="35466-156">Jeśli nie ma żadnych zgodnego środowiska uruchomieniowego z odpowiadającym głównych i podrzędny numer wersji, używana jest dalej nowszej wersji pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="35466-156">If there is no matching runtime with a matching major and minor version number, the next higher minor version is used.</span></span>
* <span data-ttu-id="35466-157">Przenoszenia do przodu nie zachodzi między wersji zapoznawczych środowiska uruchomieniowego lub wersje Podgląd i wersje.</span><span class="sxs-lookup"><span data-stu-id="35466-157">Roll forward doesn't occur between preview versions of the runtime or between preview versions and release versions.</span></span> <span data-ttu-id="35466-158">W związku z tym globalnych narzędzi utworzone za pomocą wersji zapoznawczych musi można odbudować i ponownie opublikować przez autora i ponownej instalacji.</span><span class="sxs-lookup"><span data-stu-id="35466-158">Thus, Global Tools created using preview versions must be rebuilt and republished by the author and reinstalled.</span></span>
* <span data-ttu-id="35466-159">Dodatkowe problemy mogą wystąpić z globalnego narzędzia utworzone w .NET Core 2.1 Preview 1.</span><span class="sxs-lookup"><span data-stu-id="35466-159">Additional issues can occur with Global Tools created in .NET Core 2.1 Preview 1.</span></span> <span data-ttu-id="35466-160">Aby uzyskać więcej informacji, zobacz [.NET Core 2.1 Preview 2 znane problemy](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="35466-160">For more information, see [.NET Core 2.1 Preview 2 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).</span></span>

<span data-ttu-id="35466-161">Jeśli aplikacja nie może znaleźć odpowiedniego środowiska uruchomieniowego, kończy się niepowodzeniem i zgłosi błąd.</span><span class="sxs-lookup"><span data-stu-id="35466-161">If an application cannot find an appropriate runtime, it fails to run and reports an error.</span></span>

<span data-ttu-id="35466-162">Innego problemu, który może się zdarzyć, jest, że narzędzie globalne, który został utworzony w starszej wersji zapoznawczej może nie działać z Twojej aktualnie zainstalowanego środowiska uruchomieniowe .NET Core.</span><span class="sxs-lookup"><span data-stu-id="35466-162">Another issue that might happen is that a Global Tool that was created during an earlier preview may not run with your currently installed .NET Core runtimes.</span></span> <span data-ttu-id="35466-163">Możesz sprawdzić, które programy obsługi są zainstalowane na tym komputerze za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="35466-163">You can see which runtimes are installed on your machine using the following command:</span></span>

```console
dotnet --list-runtimes
```

<span data-ttu-id="35466-164">Skontaktuj się z autorem narzędzie globalne i czy można ponownie skompilować i ponownie opublikować ich pakietu Narzędzia do NuGet z liczbą zaktualizowanej wersji.</span><span class="sxs-lookup"><span data-stu-id="35466-164">Contact the author of the Global Tool and see if they can recompile and republish their tool package to NuGet with an updated version number.</span></span> <span data-ttu-id="35466-165">Po ich został zaktualizowany pakiet na NuGet, należy zaktualizować kopii.</span><span class="sxs-lookup"><span data-stu-id="35466-165">Once they have updated the package on NuGet, you can update your copy.</span></span>

<span data-ttu-id="35466-166">Interfejsu wiersza polecenia platformy .NET Core próbuje dodać domyślne lokalizacje do zmiennej środowiskowej ŚCIEŻKA na pierwszego użycia.</span><span class="sxs-lookup"><span data-stu-id="35466-166">The .NET Core CLI tries to add the default locations to the PATH environment variable on its first usage.</span></span> <span data-ttu-id="35466-167">Jednak istnieje kilka scenariuszy, w którym lokalizacja może nie można dodać do ścieżki automatycznie, takich jak:</span><span class="sxs-lookup"><span data-stu-id="35466-167">However, there are a couple of scenarios where the location might not be added to PATH automatically, such as:</span></span>

* <span data-ttu-id="35466-168">Jeśli ustawiono `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="35466-168">If you've set the `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` environment variable.</span></span>
* <span data-ttu-id="35466-169">Na macOS, jeśli został zainstalowany przy użyciu zestawu SDK programu .NET Core *. tar.gz* plików i nie *.pkg*.</span><span class="sxs-lookup"><span data-stu-id="35466-169">On macOS, if you've installed the .NET Core SDK using *.tar.gz* files and not *.pkg*.</span></span>
* <span data-ttu-id="35466-170">W systemie Linux należy edytować plik środowiska powłoki, aby skonfigurować ŚCIEŻKĘ.</span><span class="sxs-lookup"><span data-stu-id="35466-170">On Linux, you need to edit the shell environment file to configure the PATH.</span></span>

## <a name="other-cli-commands"></a><span data-ttu-id="35466-171">Inne polecenia interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="35466-171">Other CLI commands</span></span>

<span data-ttu-id="35466-172">.NET Core SDK zawiera inne polecenia, które obsługuje narzędzia globalne .NET Core.</span><span class="sxs-lookup"><span data-stu-id="35466-172">The .NET Core SDK contains other commands that support .NET Core Global Tools.</span></span> <span data-ttu-id="35466-173">Użyć dowolnego z `dotnet tool` poleceń z jedną z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="35466-173">Use any of the `dotnet tool` commands with one of the following options:</span></span>

* <span data-ttu-id="35466-174">`--global` lub `-g` Określa, że polecenia mające zastosowanie do całej użytkownika narzędzia globalnego.</span><span class="sxs-lookup"><span data-stu-id="35466-174">`--global` or `-g` specifies that the command is applicable to user-wide Global Tools.</span></span>
* <span data-ttu-id="35466-175">`--tool-path` Określa niestandardową lokalizację dla globalnych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="35466-175">`--tool-path` specifies a custom location for Global Tools.</span></span>

<span data-ttu-id="35466-176">Aby dowiedzieć się, jakie polecenia są dostępne dla narzędzia globalne:</span><span class="sxs-lookup"><span data-stu-id="35466-176">To find out which commands are available for Global Tools:</span></span>

```console
dotnet tool --help
```

<span data-ttu-id="35466-177">Aktualizowanie narzędzie globalne obejmuje odinstalowanie i ponowne zainstalowanie go przy użyciu najnowszej wersji stabilnej.</span><span class="sxs-lookup"><span data-stu-id="35466-177">Updating a Global Tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="35466-178">Aby zaktualizować narzędzie globalne, użyj [aktualizacji narzędzi dotnet](dotnet-tool-update.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="35466-178">To update a Global Tool, use the [dotnet tool update](dotnet-tool-update.md) command:</span></span>

```console
dotnet tool update -g <packagename>
```

<span data-ttu-id="35466-179">Usuń narzędzie globalne przy użyciu [narzędzia dotnet odinstalowania](dotnet-tool-uninstall.md):</span><span class="sxs-lookup"><span data-stu-id="35466-179">Remove a Global Tool using the [dotnet tool uninstall](dotnet-tool-uninstall.md):</span></span>

```console
dotnet tool uninstall -g <packagename>
```

<span data-ttu-id="35466-180">Aby wyświetlić wszystkie narzędzia globalne aktualnie zainstalowane na komputerze, wraz z ich wersji i poleceń, należy użyć [lista narzędzi dotnet](dotnet-tool-list.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="35466-180">To display all of the Global Tools currently installed on the machine, along with their version and commands, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```console
dotnet tool list -g
```