---
title: Narzędzia globalnej platformy .NET core
description: Omówienie narzędzia globalnej platformy .NET Core i dostępne dla nich polecenia interfejsu wiersza polecenia platformy .NET Core.
author: KathleenDollard
ms.date: 05/29/2018
ms.custom: seodec18
ms.openlocfilehash: 3bbf1e7953482dc07f05570443cf640a9fab6258
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61647755"
---
# <a name="net-core-global-tools-overview"></a><span data-ttu-id="1c167-103">Omówienie narzędzia globalnej platformy .NET core</span><span class="sxs-lookup"><span data-stu-id="1c167-103">.NET Core Global Tools overview</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

<span data-ttu-id="1c167-104">.NET Core globalnego narzędzie to specjalne pakietu NuGet, który zawiera aplikację konsolową w języku.</span><span class="sxs-lookup"><span data-stu-id="1c167-104">A .NET Core Global Tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="1c167-105">Narzędzie globalne można zainstalować na komputerze w domyślnej lokalizacji, która jest dostępna w zmiennej środowiskowej PATH lub w lokalizacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="1c167-105">A Global Tool can be installed on your machine on a default location that is included in the PATH environment variable or on a custom location.</span></span>

<span data-ttu-id="1c167-106">Jeśli chcesz użyć narzędzia globalnego .NET Core:</span><span class="sxs-lookup"><span data-stu-id="1c167-106">If you want to use a .NET Core Global Tool:</span></span>

* <span data-ttu-id="1c167-107">Zawiera informacje o narzędziu (zazwyczaj witryny sieci Web lub w witrynie github).</span><span class="sxs-lookup"><span data-stu-id="1c167-107">Find information about the tool (usually a website or GitHub page).</span></span>
* <span data-ttu-id="1c167-108">Sprawdź, autora i statystyki w miejsce, w którym dla źródła danych (zwykle NuGet.org).</span><span class="sxs-lookup"><span data-stu-id="1c167-108">Check the author and statistics in the home for the feed (usually NuGet.org).</span></span>
* <span data-ttu-id="1c167-109">Zainstaluj narzędzie.</span><span class="sxs-lookup"><span data-stu-id="1c167-109">Install the tool.</span></span>
* <span data-ttu-id="1c167-110">Wywołuje narzędzie.</span><span class="sxs-lookup"><span data-stu-id="1c167-110">Call the tool.</span></span>
* <span data-ttu-id="1c167-111">Zaktualizuj narzędzie.</span><span class="sxs-lookup"><span data-stu-id="1c167-111">Update the tool.</span></span>
* <span data-ttu-id="1c167-112">Odinstaluj narzędzie.</span><span class="sxs-lookup"><span data-stu-id="1c167-112">Uninstall the tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1c167-113">Narzędzia globalnej platformy .NET core są wyświetlane w zmiennej path i uruchamiać w trybie pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="1c167-113">.NET Core Global Tools appear on your path and run in full trust.</span></span> <span data-ttu-id="1c167-114">Nie należy instalować narzędzia globalnej platformy .NET Core, chyba że zaufania do autora.</span><span class="sxs-lookup"><span data-stu-id="1c167-114">Do not install .NET Core Global Tools unless you trust the author.</span></span>

## <a name="find-a-net-core-global-tool"></a><span data-ttu-id="1c167-115">Znajdź narzędzie globalne podstawowych platformy .NET</span><span class="sxs-lookup"><span data-stu-id="1c167-115">Find a .NET Core Global Tool</span></span>

<span data-ttu-id="1c167-116">Obecnie nie ma funkcji wyszukiwania globalnego narzędzia w konsoli .NET Core interfejsu wiersza polecenia (CLI).</span><span class="sxs-lookup"><span data-stu-id="1c167-116">Currently, there isn't a Global Tool search feature in the .NET Core Command-line Interface (CLI).</span></span>

<span data-ttu-id="1c167-117">Narzędzia programu .NET Core globalnej można znaleźć na [NuGet](https://www.nuget.org).</span><span class="sxs-lookup"><span data-stu-id="1c167-117">You can find .NET Core Global Tools on [NuGet](https://www.nuget.org).</span></span> <span data-ttu-id="1c167-118">Jednak NuGet jeszcze nie dopuszcza do wyszukiwania w szczególności narzędzia globalnej platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1c167-118">However, NuGet doesn't yet allow you to search specifically for .NET Core Global Tools.</span></span>

<span data-ttu-id="1c167-119">Można również znaleźć zaleceń dotyczących narzędzi do wpisów w blogu lub w [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="1c167-119">You may also find tool recommendations in blog posts or in the [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub repository.</span></span>

<span data-ttu-id="1c167-120">Widać również kod źródłowy dla globalnych narzędzi utworzonych przez zespół programu ASP.NET w [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="1c167-120">You can also see the source code for the Global Tools created by the ASP.NET team at the [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub repository.</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="1c167-121">Sprawdź, autora i statystyk</span><span class="sxs-lookup"><span data-stu-id="1c167-121">Check the author and statistics</span></span>

<span data-ttu-id="1c167-122">Ponieważ narzędzia globalnej platformy .NET Core uruchamianie w trybie pełnego zaufania i zwykle są zainstalowane w zmiennej path, może być bardzo wydajne.</span><span class="sxs-lookup"><span data-stu-id="1c167-122">Since .NET Core Global Tools run in full trust and are generally installed on your path, they can be very powerful.</span></span> <span data-ttu-id="1c167-123">Nie można pobrać narzędzia od osób, którym nie ufasz.</span><span class="sxs-lookup"><span data-stu-id="1c167-123">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="1c167-124">Jeśli narzędzie jest obsługiwana dla narzędzia NuGet, możesz sprawdzić autora i statystyki, wyszukując narzędzie.</span><span class="sxs-lookup"><span data-stu-id="1c167-124">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="1c167-125">Zainstaluj narzędzie globalne</span><span class="sxs-lookup"><span data-stu-id="1c167-125">Install a Global Tool</span></span>

<span data-ttu-id="1c167-126">Aby zainstalować narzędzie globalne, należy użyć [instalacji narzędzi dotnet](dotnet-tool-install.md) polecenia interfejsu wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1c167-126">To install a Global Tool, you use the [dotnet tool install](dotnet-tool-install.md) .NET Core CLI command.</span></span> <span data-ttu-id="1c167-127">Poniższy przykład pokazuje, jak zainstalować narzędzie do globalnego w lokalizacji domyślnej:</span><span class="sxs-lookup"><span data-stu-id="1c167-127">The following example shows how to install a Global Tool in the default location:</span></span>

```console
dotnet tool install -g dotnetsay
```

<span data-ttu-id="1c167-128">Jeśli nie można zainstalować narzędzia, komunikaty o błędach są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="1c167-128">If the tool can't be installed, error messages are displayed.</span></span> <span data-ttu-id="1c167-129">Sprawdź, że źródła danych, które miały są sprawdzane.</span><span class="sxs-lookup"><span data-stu-id="1c167-129">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="1c167-130">Jeśli próbujesz zainstalować wersję wstępną lub określoną wersję narzędzia, można określić numeru wersji w następującym formacie:</span><span class="sxs-lookup"><span data-stu-id="1c167-130">If you're trying to install a pre-release version or a specific version of the tool, you can specify the version number using the following format:</span></span>

```console
dotnet tool install -g <package-name> --version <version-number>
```

<span data-ttu-id="1c167-131">Jeśli instalacja zakończy się pomyślnie, zostanie wyświetlony komunikat przedstawiający polecenia używane do wywoływania narzędzia i wersją zainstalowaną, podobny do poniższego przykładu:</span><span class="sxs-lookup"><span data-stu-id="1c167-131">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

<span data-ttu-id="1c167-132">Globalne narzędzia można zainstalować w domyślnym katalogu lub w określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="1c167-132">Global Tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="1c167-133">Domyślne katalogi są następujące:</span><span class="sxs-lookup"><span data-stu-id="1c167-133">The default directories are:</span></span>

| <span data-ttu-id="1c167-134">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="1c167-134">OS</span></span>          | <span data-ttu-id="1c167-135">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="1c167-135">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="1c167-136">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="1c167-136">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="1c167-137">Windows</span><span class="sxs-lookup"><span data-stu-id="1c167-137">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="1c167-138">Te lokalizacje są dodawane do ścieżki użytkownika podczas pierwszego uruchomienia zestaw SDK, więc globalnego narzędzia są zainstalowane, może być wywoływana bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="1c167-138">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="1c167-139">Należy zauważyć, że globalne narzędzia specyficzne dla użytkownika, nie machine globalnego.</span><span class="sxs-lookup"><span data-stu-id="1c167-139">Note that the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="1c167-140">Są specyficzne dla użytkownika oznacza, że nie można zainstalować narzędzie globalne, która jest dostępna dla wszystkich użytkowników komputera.</span><span class="sxs-lookup"><span data-stu-id="1c167-140">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="1c167-141">Narzędzie jest dostępne tylko dla każdego profilu użytkownika którym zostało zainstalowane narzędzie.</span><span class="sxs-lookup"><span data-stu-id="1c167-141">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="1c167-142">Można również zainstalować narzędzia globalnej w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="1c167-142">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="1c167-143">Podczas instalowania w określonym katalogu, użytkownik musi upewnić się polecenie jest dostępne, umieszczając tego katalogu w ścieżce, wywołując polecenie z katalogu, który został określony, lub podczas wywoływania narzędzia z w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="1c167-143">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="1c167-144">W tym przypadku interfejsu wiersza polecenia platformy .NET Core nie powoduje dodania tej lokalizacji automatycznie do zmiennej środowiskowej PATH.</span><span class="sxs-lookup"><span data-stu-id="1c167-144">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="use-the-tool"></a><span data-ttu-id="1c167-145">Za pomocą narzędzia</span><span class="sxs-lookup"><span data-stu-id="1c167-145">Use the tool</span></span>

<span data-ttu-id="1c167-146">Po zainstalowaniu narzędzia można wywoływać ją za pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="1c167-146">Once the tool is installed, you can call it by using its command.</span></span> <span data-ttu-id="1c167-147">Należy zauważyć, że polecenie nie może być taka sama jak nazwa pakietu.</span><span class="sxs-lookup"><span data-stu-id="1c167-147">Note that the command may not be the same as the package name.</span></span>

<span data-ttu-id="1c167-148">Jeśli polecenie jest `dotnetsay`, należy wywołać za pomocą:</span><span class="sxs-lookup"><span data-stu-id="1c167-148">If the command is `dotnetsay`, you call it with:</span></span>

```console
dotnetsay
```

<span data-ttu-id="1c167-149">Jeśli autor narzędzie potrzebowała narzędzie, które pojawią się w kontekście `dotnet` wierszu one napisał ją w taki sposób, nadaj mu `dotnet <command>`, takich jak:</span><span class="sxs-lookup"><span data-stu-id="1c167-149">If the tool author wanted the tool to appear in the context of the `dotnet` prompt, they may have written it in a way that you call it as `dotnet <command>`, such as:</span></span>

```console
dotnet doc
```

<span data-ttu-id="1c167-150">Możesz znaleźć, jakie narzędzia są objęte zainstalowanego pakietu narzędzie globalne, wyświetlając listę zainstalowanych pakietów przy użyciu [lista narzędzi dotnet](dotnet-tool-list.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="1c167-150">You can find which tools are included in an installed Global Tool package by listing the installed packages using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

<span data-ttu-id="1c167-151">Można także wyszukać instrukcje użycia w witrynie sieci Web narzędzia lub wpisując jedno z następujących poleceń:</span><span class="sxs-lookup"><span data-stu-id="1c167-151">You can also look for usage instructions at the tool's website or by typing one of the following commands:</span></span>

```console
<command> --help
dotnet <command> --help
```

### <a name="what-could-go-wrong"></a><span data-ttu-id="1c167-152">Co można pójdzie nie tak</span><span class="sxs-lookup"><span data-stu-id="1c167-152">What could go wrong</span></span>

<span data-ttu-id="1c167-153">Narzędzia globalne są [zależny od struktury aplikacji](../deploying/index.md#framework-dependent-deployments-fdd), co oznacza, że opierają się na środowisko uruchomieniowe platformy .NET Core zainstalowana na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="1c167-153">Global Tools are [framework-dependent applications](../deploying/index.md#framework-dependent-deployments-fdd), which means they rely on a .NET Core runtime installed on your machine.</span></span> <span data-ttu-id="1c167-154">Oczekiwany czas działania nie zostanie znaleziony, należy wykonać normalnego reguły przodu środowisko uruchomieniowe platformy .NET Core takich jak:</span><span class="sxs-lookup"><span data-stu-id="1c167-154">If the expected runtime is not found, they follow normal .NET Core runtime roll-forward rules such as:</span></span>

* <span data-ttu-id="1c167-155">Aplikacja przenosi do przodu do najwyższej wersji poprawki określonej wersji głównych i pomocniczych.</span><span class="sxs-lookup"><span data-stu-id="1c167-155">An application rolls forward to the highest patch release of the specified major and minor version.</span></span>
* <span data-ttu-id="1c167-156">Jeśli nie ma żadnych pasujących aparatu plików wykonywalnych dopasowania główne i pomocniczy numer wersji, dalej wyższa wersja pomocnicza jest używany.</span><span class="sxs-lookup"><span data-stu-id="1c167-156">If there is no matching runtime with a matching major and minor version number, the next higher minor version is used.</span></span>
* <span data-ttu-id="1c167-157">Przenoszenia do przodu nie zachodzi między wersji zapoznawczych środowiska uruchomieniowego lub wersji zapoznawczych i wersji.</span><span class="sxs-lookup"><span data-stu-id="1c167-157">Roll forward doesn't occur between preview versions of the runtime or between preview versions and release versions.</span></span> <span data-ttu-id="1c167-158">W związku z tym, globalne narzędzia utworzone za pomocą wersji zapoznawczych musi być odbudować i ponowne opublikowanie przez autora i ponownej instalacji.</span><span class="sxs-lookup"><span data-stu-id="1c167-158">Thus, Global Tools created using preview versions must be rebuilt and republished by the author and reinstalled.</span></span>
* <span data-ttu-id="1c167-159">Dodatkowe problemy dotyczące za pomocą narzędzi globalnego utworzone w .NET Core 2.1 w wersji zapoznawczej 1.</span><span class="sxs-lookup"><span data-stu-id="1c167-159">Additional issues can occur with Global Tools created in .NET Core 2.1 Preview 1.</span></span> <span data-ttu-id="1c167-160">Aby uzyskać więcej informacji, zobacz [.NET Core 2.1 w wersji zapoznawczej 2 — znane problemy](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="1c167-160">For more information, see [.NET Core 2.1 Preview 2 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).</span></span>

<span data-ttu-id="1c167-161">Jeśli aplikacja nie może znaleźć odpowiedniego środowiska uruchomieniowego, uruchomienie nie powiedzie się i zgłasza błąd.</span><span class="sxs-lookup"><span data-stu-id="1c167-161">If an application cannot find an appropriate runtime, it fails to run and reports an error.</span></span>

<span data-ttu-id="1c167-162">Inny problem, który może się zdarzyć, to narzędzie globalne, który został utworzony w starszej wersji zapoznawczej może nie działać z Twojego aktualnie zainstalowanego środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1c167-162">Another issue that might happen is that a Global Tool that was created during an earlier preview may not run with your currently installed .NET Core runtimes.</span></span> <span data-ttu-id="1c167-163">Możesz zobaczyć, które środowiska uruchomieniowe są zainstalowane na komputerze przy użyciu następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="1c167-163">You can see which runtimes are installed on your machine using the following command:</span></span>

```console
dotnet --list-runtimes
```

<span data-ttu-id="1c167-164">Skontaktuj się z autorem narzędzie globalne i czy można ponownie skompilować i ponownie opublikować ich pakiet narzędzi do narzędzia NuGet ze zaktualizowanym numerem wersji.</span><span class="sxs-lookup"><span data-stu-id="1c167-164">Contact the author of the Global Tool and see if they can recompile and republish their tool package to NuGet with an updated version number.</span></span> <span data-ttu-id="1c167-165">Po zaktualizowaniu one pakietów dla narzędzia NuGet, należy zaktualizować kopii.</span><span class="sxs-lookup"><span data-stu-id="1c167-165">Once they have updated the package on NuGet, you can update your copy.</span></span>

<span data-ttu-id="1c167-166">Interfejs wiersza polecenia platformy .NET Core próbuje dodać domyślne lokalizacje do zmiennej środowiskowej PATH na pierwszego użycia.</span><span class="sxs-lookup"><span data-stu-id="1c167-166">The .NET Core CLI tries to add the default locations to the PATH environment variable on its first usage.</span></span> <span data-ttu-id="1c167-167">Jednak istnieje kilka scenariuszy, w których lokalizacja może nie można dodać do ścieżki automatycznie, takich jak:</span><span class="sxs-lookup"><span data-stu-id="1c167-167">However, there are a couple of scenarios where the location might not be added to PATH automatically, such as:</span></span>

* <span data-ttu-id="1c167-168">Jeśli ustawiono `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="1c167-168">If you've set the `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` environment variable.</span></span>
* <span data-ttu-id="1c167-169">W systemie macOS, jeśli została zainstalowana przy użyciu zestawu .NET Core SDK *. tar.gz* plików i nie *.pkg*.</span><span class="sxs-lookup"><span data-stu-id="1c167-169">On macOS, if you've installed the .NET Core SDK using *.tar.gz* files and not *.pkg*.</span></span>
* <span data-ttu-id="1c167-170">W systemie Linux należy edytować plik środowiska powłoki, aby skonfigurować ŚCIEŻKĘ.</span><span class="sxs-lookup"><span data-stu-id="1c167-170">On Linux, you need to edit the shell environment file to configure the PATH.</span></span>

## <a name="other-cli-commands"></a><span data-ttu-id="1c167-171">Inne polecenia interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="1c167-171">Other CLI commands</span></span>

<span data-ttu-id="1c167-172">.NET Core SDK zawiera innych poleceń, które obsługują narzędzia globalnej platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1c167-172">The .NET Core SDK contains other commands that support .NET Core Global Tools.</span></span> <span data-ttu-id="1c167-173">Użyć dowolnej z `dotnet tool` poleceń przy użyciu jednego z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="1c167-173">Use any of the `dotnet tool` commands with one of the following options:</span></span>

* <span data-ttu-id="1c167-174">`--global` lub `-g` Określa, że polecenie jest zastosowanie do całej użytkownika narzędzia globalnej.</span><span class="sxs-lookup"><span data-stu-id="1c167-174">`--global` or `-g` specifies that the command is applicable to user-wide Global Tools.</span></span>
* <span data-ttu-id="1c167-175">`--tool-path` Określa niestandardową lokalizację dla narzędzia globalnej.</span><span class="sxs-lookup"><span data-stu-id="1c167-175">`--tool-path` specifies a custom location for Global Tools.</span></span>

<span data-ttu-id="1c167-176">Aby dowiedzieć się, jakie polecenia są dostępne dla narzędzia globalnej:</span><span class="sxs-lookup"><span data-stu-id="1c167-176">To find out which commands are available for Global Tools:</span></span>

```console
dotnet tool --help
```

<span data-ttu-id="1c167-177">Aktualizowanie narzędzie globalne obejmuje odinstalowanie i ponowne zainstalowanie go za pomocą najnowszej stabilnej wersji.</span><span class="sxs-lookup"><span data-stu-id="1c167-177">Updating a Global Tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="1c167-178">Aby zaktualizować narzędzie globalne, użyj [aktualizacji narzędzi dotnet](dotnet-tool-update.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="1c167-178">To update a Global Tool, use the [dotnet tool update](dotnet-tool-update.md) command:</span></span>

```console
dotnet tool update -g <packagename>
```

<span data-ttu-id="1c167-179">Usuń narzędzie globalne przy użyciu [narzędzia dotnet odinstalowania](dotnet-tool-uninstall.md):</span><span class="sxs-lookup"><span data-stu-id="1c167-179">Remove a Global Tool using the [dotnet tool uninstall](dotnet-tool-uninstall.md):</span></span>

```console
dotnet tool uninstall -g <packagename>
```

<span data-ttu-id="1c167-180">Aby wyświetlić wszystkie narzędzia globalnej aktualnie jest zainstalowana na komputerze, wraz z ich wersji i poleceń, użyj [lista narzędzi dotnet](dotnet-tool-list.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="1c167-180">To display all of the Global Tools currently installed on the machine, along with their version and commands, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```console
dotnet tool list -g
```