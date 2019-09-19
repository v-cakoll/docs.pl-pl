---
title: Narzędzia globalne platformy .NET Core
description: Omówienie narzędzi globalnych platformy .NET Core i dostępnych dla nich poleceń interfejs wiersza polecenia platformy .NET Core.
author: KathleenDollard
ms.date: 05/29/2018
ms.custom: seodec18
ms.openlocfilehash: 01c1463ceddcd64e5bab05b95a5ae4a91b6da838
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117461"
---
# <a name="net-core-global-tools-overview"></a><span data-ttu-id="5d2ef-103">Globalne narzędzia platformy .NET Core — Omówienie</span><span class="sxs-lookup"><span data-stu-id="5d2ef-103">.NET Core Global Tools overview</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

<span data-ttu-id="5d2ef-104">Narzędzie globalne platformy .NET Core jest specjalnym pakietem NuGet, który zawiera aplikację konsolową.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-104">A .NET Core Global Tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="5d2ef-105">Narzędzie globalne można zainstalować na komputerze w lokalizacji domyślnej, która jest uwzględniona w zmiennej środowiskowej PATH lub w lokalizacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-105">A Global Tool can be installed on your machine on a default location that is included in the PATH environment variable or on a custom location.</span></span>

<span data-ttu-id="5d2ef-106">Jeśli chcesz użyć globalnego narzędzia platformy .NET Core:</span><span class="sxs-lookup"><span data-stu-id="5d2ef-106">If you want to use a .NET Core Global Tool:</span></span>

* <span data-ttu-id="5d2ef-107">Znajdź informacje o narzędziu (zazwyczaj witryna sieci Web lub GitHub).</span><span class="sxs-lookup"><span data-stu-id="5d2ef-107">Find information about the tool (usually a website or GitHub page).</span></span>
* <span data-ttu-id="5d2ef-108">Sprawdź autora i statystyki na stronie głównej kanału informacyjnego (zwykle NuGet.org).</span><span class="sxs-lookup"><span data-stu-id="5d2ef-108">Check the author and statistics in the home for the feed (usually NuGet.org).</span></span>
* <span data-ttu-id="5d2ef-109">Zainstaluj narzędzie.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-109">Install the tool.</span></span>
* <span data-ttu-id="5d2ef-110">Wywoływanie narzędzia.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-110">Call the tool.</span></span>
* <span data-ttu-id="5d2ef-111">Zaktualizuj narzędzie.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-111">Update the tool.</span></span>
* <span data-ttu-id="5d2ef-112">Odinstaluj narzędzie.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-112">Uninstall the tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5d2ef-113">Narzędzia globalne platformy .NET Core są wyświetlane na ścieżce i działają w trybie pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-113">.NET Core Global Tools appear on your path and run in full trust.</span></span> <span data-ttu-id="5d2ef-114">Nie instaluj podstawowych narzędzi platformy .NET Core, chyba że ufasz autorowi.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-114">Do not install .NET Core Global Tools unless you trust the author.</span></span>

## <a name="find-a-net-core-global-tool"></a><span data-ttu-id="5d2ef-115">Znajdź narzędzie globalne platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="5d2ef-115">Find a .NET Core Global Tool</span></span>

<span data-ttu-id="5d2ef-116">Obecnie nie istnieje funkcja globalnego wyszukiwania narzędzi w interfejsie wiersza polecenia (CLI) platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-116">Currently, there isn't a Global Tool search feature in the .NET Core Command-line Interface (CLI).</span></span>

<span data-ttu-id="5d2ef-117">Narzędzia platformy .NET Core można znaleźć na platformie [NuGet](https://www.nuget.org).</span><span class="sxs-lookup"><span data-stu-id="5d2ef-117">You can find .NET Core Global Tools on [NuGet](https://www.nuget.org).</span></span> <span data-ttu-id="5d2ef-118">Jednak pakiet NuGet nie zezwala jeszcze na wyszukiwanie dla narzędzi globalnych platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-118">However, NuGet doesn't yet allow you to search specifically for .NET Core Global Tools.</span></span>

<span data-ttu-id="5d2ef-119">Zalecenia dotyczące narzędzi można także znaleźć w wpisach w blogu lub w repozytorium GitHub [natemcmaster/dotnet-Tools](https://github.com/natemcmaster/dotnet-tools) .</span><span class="sxs-lookup"><span data-stu-id="5d2ef-119">You may also find tool recommendations in blog posts or in the [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub repository.</span></span>

<span data-ttu-id="5d2ef-120">Możesz również wyświetlić kod źródłowy narzędzi globalnych utworzonych przez zespół ASP.NET w repozytorium GitHub [/DotNetTools](https://github.com/aspnet/DotNetTools/) .</span><span class="sxs-lookup"><span data-stu-id="5d2ef-120">You can also see the source code for the Global Tools created by the ASP.NET team at the [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub repository.</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="5d2ef-121">Sprawdź autora i statystyki</span><span class="sxs-lookup"><span data-stu-id="5d2ef-121">Check the author and statistics</span></span>

<span data-ttu-id="5d2ef-122">Ponieważ globalne narzędzia platformy .NET Core działają w pełni zaufane i są zwykle instalowane na ścieżce, mogą być bardzo wydajne.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-122">Since .NET Core Global Tools run in full trust and are generally installed on your path, they can be very powerful.</span></span> <span data-ttu-id="5d2ef-123">Nie pobieraj narzędzi z osób, które nie są zaufane.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-123">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="5d2ef-124">Jeśli narzędzie jest hostowane w usłudze NuGet, można sprawdzić autora i statystyk, wyszukując narzędzie.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-124">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="5d2ef-125">Instalowanie narzędzia globalnego</span><span class="sxs-lookup"><span data-stu-id="5d2ef-125">Install a Global Tool</span></span>

<span data-ttu-id="5d2ef-126">Aby zainstalować narzędzie globalne, należy użyć [Narzędzia dotnet zainstaluj](dotnet-tool-install.md) interfejs wiersza polecenia platformy .NET Core polecenie.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-126">To install a Global Tool, you use the [dotnet tool install](dotnet-tool-install.md) .NET Core CLI command.</span></span> <span data-ttu-id="5d2ef-127">Poniższy przykład pokazuje, jak zainstalować narzędzie globalne w lokalizacji domyślnej:</span><span class="sxs-lookup"><span data-stu-id="5d2ef-127">The following example shows how to install a Global Tool in the default location:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="5d2ef-128">Jeśli nie można zainstalować narzędzia, zostaną wyświetlone komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-128">If the tool can't be installed, error messages are displayed.</span></span> <span data-ttu-id="5d2ef-129">Sprawdź, czy wybrane źródła danych są sprawdzane.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-129">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="5d2ef-130">Jeśli próbujesz zainstalować wersję wstępną lub określoną wersję narzędzia, możesz określić numer wersji w następującym formacie:</span><span class="sxs-lookup"><span data-stu-id="5d2ef-130">If you're trying to install a pre-release version or a specific version of the tool, you can specify the version number using the following format:</span></span>

```dotnetcli
dotnet tool install -g <package-name> --version <version-number>
```

<span data-ttu-id="5d2ef-131">Jeśli instalacja zakończy się pomyślnie, zostanie wyświetlony komunikat z poleceniem, które służy do wywoływania narzędzia i zainstalowanej wersji, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="5d2ef-131">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

<span data-ttu-id="5d2ef-132">Narzędzia globalne można zainstalować w katalogu domyślnym lub w określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-132">Global Tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="5d2ef-133">Domyślne katalogi są następujące:</span><span class="sxs-lookup"><span data-stu-id="5d2ef-133">The default directories are:</span></span>

| <span data-ttu-id="5d2ef-134">OS</span><span class="sxs-lookup"><span data-stu-id="5d2ef-134">OS</span></span>          | <span data-ttu-id="5d2ef-135">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="5d2ef-135">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="5d2ef-136">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="5d2ef-136">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="5d2ef-137">Windows</span><span class="sxs-lookup"><span data-stu-id="5d2ef-137">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="5d2ef-138">Te lokalizacje są dodawane do ścieżki użytkownika podczas pierwszego uruchomienia zestawu SDK, dzięki czemu globalne narzędzia mogą być wywoływane bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-138">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="5d2ef-139">Należy pamiętać, że globalne narzędzia to specyficzne dla użytkownika, a nie globalne maszyny.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-139">Note that the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="5d2ef-140">Specyficzne dla użytkownika oznacza, że nie można zainstalować narzędzia globalnego, które jest dostępne dla wszystkich użytkowników komputera.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-140">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="5d2ef-141">Narzędzie jest dostępne tylko dla każdego profilu użytkownika, w którym zainstalowano narzędzie.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-141">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="5d2ef-142">Narzędzia globalne można także zainstalować w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-142">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="5d2ef-143">Po zainstalowaniu w określonym katalogu użytkownik musi upewnić się, że polecenie jest dostępne, dołączając ten katalog w ścieżce, wywołując polecenie z określonym katalogiem lub wywołując narzędzie z w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-143">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="5d2ef-144">W takim przypadku interfejs wiersza polecenia platformy .NET Core nie dodaje automatycznie tej lokalizacji do zmiennej środowiskowej PATH.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-144">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="use-the-tool"></a><span data-ttu-id="5d2ef-145">Korzystanie z narzędzia</span><span class="sxs-lookup"><span data-stu-id="5d2ef-145">Use the tool</span></span>

<span data-ttu-id="5d2ef-146">Po zainstalowaniu narzędzia można wywołać je za pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-146">Once the tool is installed, you can call it by using its command.</span></span> <span data-ttu-id="5d2ef-147">Należy pamiętać, że polecenie nie może być takie samo jak nazwa pakietu.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-147">Note that the command may not be the same as the package name.</span></span>

<span data-ttu-id="5d2ef-148">Jeśli polecenie jest `dotnetsay`, należy je wywołać z:</span><span class="sxs-lookup"><span data-stu-id="5d2ef-148">If the command is `dotnetsay`, you call it with:</span></span>

```console
dotnetsay
```

<span data-ttu-id="5d2ef-149">Jeśli narzędzie ma być wyświetlane w kontekście `dotnet` monitu, może napisać je w taki sposób, aby była wywoływana `dotnet <command>`w taki sposób, jak:</span><span class="sxs-lookup"><span data-stu-id="5d2ef-149">If the tool author wanted the tool to appear in the context of the `dotnet` prompt, they may have written it in a way that you call it as `dotnet <command>`, such as:</span></span>

```dotnetcli
dotnet doc
```

<span data-ttu-id="5d2ef-150">Aby znaleźć narzędzia dołączone do zainstalowanego pakietu narzędzi globalnych, należy wyświetlić listę zainstalowanych pakietów przy użyciu polecenia programu [dotnet](dotnet-tool-list.md) .</span><span class="sxs-lookup"><span data-stu-id="5d2ef-150">You can find which tools are included in an installed Global Tool package by listing the installed packages using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

<span data-ttu-id="5d2ef-151">Możesz również wyszukać instrukcje dotyczące użycia w witrynie sieci Web narzędzia lub wpisując jedno z następujących poleceń:</span><span class="sxs-lookup"><span data-stu-id="5d2ef-151">You can also look for usage instructions at the tool's website or by typing one of the following commands:</span></span>

```console
<command> --help
dotnet <command> --help
```

### <a name="what-could-go-wrong"></a><span data-ttu-id="5d2ef-152">Co się stało</span><span class="sxs-lookup"><span data-stu-id="5d2ef-152">What could go wrong</span></span>

<span data-ttu-id="5d2ef-153">Narzędzia globalne są [aplikacjami zależnymi od platformy](../deploying/index.md#framework-dependent-deployments-fdd), co oznacza, że korzystają z środowiska uruchomieniowego .NET Core zainstalowanego na komputerze.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-153">Global Tools are [framework-dependent applications](../deploying/index.md#framework-dependent-deployments-fdd), which means they rely on a .NET Core runtime installed on your machine.</span></span> <span data-ttu-id="5d2ef-154">Jeśli nie odnaleziono oczekiwanego środowiska uruchomieniowego, są one zgodne z normalnymi regułami przetaczania w czasie wykonywania platformy .NET Core, takimi jak:</span><span class="sxs-lookup"><span data-stu-id="5d2ef-154">If the expected runtime is not found, they follow normal .NET Core runtime roll-forward rules such as:</span></span>

* <span data-ttu-id="5d2ef-155">Aplikacja przenosi do przodu do najwyższej wersji poprawki określonej głównej i pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-155">An application rolls forward to the highest patch release of the specified major and minor version.</span></span>
* <span data-ttu-id="5d2ef-156">Jeśli nie ma pasującego środowiska uruchomieniowego z odpowiadającym mu numerem wersji głównej i pomocniczej, używana jest kolejna wyższa wersja pomocnicza.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-156">If there is no matching runtime with a matching major and minor version number, the next higher minor version is used.</span></span>
* <span data-ttu-id="5d2ef-157">Przewinięcie do przodu nie występuje między wersjami w wersji zapoznawczej środowiska uruchomieniowego a wersjami zapoznawczymi i wersjami.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-157">Roll forward doesn't occur between preview versions of the runtime or between preview versions and release versions.</span></span> <span data-ttu-id="5d2ef-158">W tym celu narzędzia globalne utworzone przy użyciu wersji zapoznawczej muszą zostać odbudowane i ponownie opublikowane przez autora oraz ponowne zainstalowanie.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-158">Thus, Global Tools created using preview versions must be rebuilt and republished by the author and reinstalled.</span></span>
* <span data-ttu-id="5d2ef-159">Dodatkowe problemy mogą wystąpić w przypadku narzędzi globalnych utworzonych w programie .NET Core 2,1 w wersji zapoznawczej 1.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-159">Additional issues can occur with Global Tools created in .NET Core 2.1 Preview 1.</span></span> <span data-ttu-id="5d2ef-160">Aby uzyskać więcej informacji, zobacz temat [znane problemy w programie .NET Core 2,1 (wersja zapoznawcza 2](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md)).</span><span class="sxs-lookup"><span data-stu-id="5d2ef-160">For more information, see [.NET Core 2.1 Preview 2 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).</span></span>

<span data-ttu-id="5d2ef-161">Jeśli aplikacja nie może znaleźć odpowiedniego środowiska uruchomieniowego, jego uruchomienie nie powiedzie się i zgłosi błąd.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-161">If an application cannot find an appropriate runtime, it fails to run and reports an error.</span></span>

<span data-ttu-id="5d2ef-162">Innym problemem, który może się zdarzyć, jest to, że narzędzie globalne, które zostało utworzone podczas wcześniejszej wersji zapoznawczej, może nie działać z aktualnie zainstalowanymi środowiskami uruchomieniowymi platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-162">Another issue that might happen is that a Global Tool that was created during an earlier preview may not run with your currently installed .NET Core runtimes.</span></span> <span data-ttu-id="5d2ef-163">Możesz zobaczyć, które środowiska uruchomieniowe są zainstalowane na maszynie, za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="5d2ef-163">You can see which runtimes are installed on your machine using the following command:</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="5d2ef-164">Skontaktuj się z autorem narzędzia globalnego i sprawdź, czy można ponownie skompilować pakiet narzędzi do narzędzia NuGet przy użyciu zaktualizowanego numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-164">Contact the author of the Global Tool and see if they can recompile and republish their tool package to NuGet with an updated version number.</span></span> <span data-ttu-id="5d2ef-165">Po zaktualizowaniu pakietu w pakiecie NuGet możesz zaktualizować swoją kopię.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-165">Once they have updated the package on NuGet, you can update your copy.</span></span>

<span data-ttu-id="5d2ef-166">Interfejs wiersza polecenia platformy .NET Core próbuje dodać domyślne lokalizacje do zmiennej środowiskowej PATH przy pierwszym użyciu.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-166">The .NET Core CLI tries to add the default locations to the PATH environment variable on its first usage.</span></span> <span data-ttu-id="5d2ef-167">Istnieje jednak kilka scenariuszy, w których lokalizacja nie może być automatycznie dodawana do ścieżki, na przykład:</span><span class="sxs-lookup"><span data-stu-id="5d2ef-167">However, there are a couple of scenarios where the location might not be added to PATH automatically, such as:</span></span>

* <span data-ttu-id="5d2ef-168">W `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` przypadku ustawienia zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-168">If you've set the `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` environment variable.</span></span>
* <span data-ttu-id="5d2ef-169">W systemie macOS, jeśli zainstalowano zestaw .NET Core SDK przy użyciu plików *tar. gz* , a nie *. pkg*.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-169">On macOS, if you've installed the .NET Core SDK using *.tar.gz* files and not *.pkg*.</span></span>
* <span data-ttu-id="5d2ef-170">W systemie Linux należy edytować plik środowiska powłoki, aby skonfigurować ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-170">On Linux, you need to edit the shell environment file to configure the PATH.</span></span>

## <a name="other-cli-commands"></a><span data-ttu-id="5d2ef-171">Inne polecenia interfejsu CLI</span><span class="sxs-lookup"><span data-stu-id="5d2ef-171">Other CLI commands</span></span>

<span data-ttu-id="5d2ef-172">Zestaw .NET Core SDK zawiera inne polecenia, które obsługują narzędzia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-172">The .NET Core SDK contains other commands that support .NET Core Global Tools.</span></span> <span data-ttu-id="5d2ef-173">Użyj dowolnego `dotnet tool` polecenia z jedną z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="5d2ef-173">Use any of the `dotnet tool` commands with one of the following options:</span></span>

* <span data-ttu-id="5d2ef-174">`--global`lub `-g` określa, że polecenie ma zastosowanie do narzędzi globalnych na poziomie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-174">`--global` or `-g` specifies that the command is applicable to user-wide Global Tools.</span></span>
* <span data-ttu-id="5d2ef-175">`--tool-path`Określa niestandardową lokalizację dla narzędzi globalnych.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-175">`--tool-path` specifies a custom location for Global Tools.</span></span>

<span data-ttu-id="5d2ef-176">Aby dowiedzieć się, które polecenia są dostępne dla narzędzi globalnych:</span><span class="sxs-lookup"><span data-stu-id="5d2ef-176">To find out which commands are available for Global Tools:</span></span>

```dotnetcli
dotnet tool --help
```

<span data-ttu-id="5d2ef-177">Aktualizacja narzędzia globalnego polega na odinstalowaniu i ponownym zainstalowaniu programu z najnowszą stabilną wersją.</span><span class="sxs-lookup"><span data-stu-id="5d2ef-177">Updating a Global Tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="5d2ef-178">Aby zaktualizować narzędzie globalne, użyj polecenia [aktualizacji narzędzia dotnet](dotnet-tool-update.md) :</span><span class="sxs-lookup"><span data-stu-id="5d2ef-178">To update a Global Tool, use the [dotnet tool update](dotnet-tool-update.md) command:</span></span>

```dotnetcli
dotnet tool update -g <packagename>
```

<span data-ttu-id="5d2ef-179">Usuń narzędzie globalne przy użyciu [Narzędzia dotnet Uninstall](dotnet-tool-uninstall.md):</span><span class="sxs-lookup"><span data-stu-id="5d2ef-179">Remove a Global Tool using the [dotnet tool uninstall](dotnet-tool-uninstall.md):</span></span>

```dotnetcli
dotnet tool uninstall -g <packagename>
```

<span data-ttu-id="5d2ef-180">Aby wyświetlić wszystkie narzędzia globalne aktualnie zainstalowane na komputerze wraz z ich wersjami i poleceniami, użyj polecenia z [listy narzędzi dotnet](dotnet-tool-list.md) :</span><span class="sxs-lookup"><span data-stu-id="5d2ef-180">To display all of the Global Tools currently installed on the machine, along with their version and commands, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```dotnetcli
dotnet tool list -g
```
