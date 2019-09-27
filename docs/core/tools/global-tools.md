---
title: Narzędzia globalne platformy .NET Core
description: Omówienie narzędzi globalnych platformy .NET Core i dostępnych dla nich poleceń interfejs wiersza polecenia platformy .NET Core.
author: KathleenDollard
ms.date: 05/29/2018
ms.custom: seodec18
ms.openlocfilehash: 40a0aabcf523e8dac9a3ad226064bbb3c1b3ce5b
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332022"
---
# <a name="net-core-global-tools-overview"></a><span data-ttu-id="53d94-103">Globalne narzędzia platformy .NET Core — Omówienie</span><span class="sxs-lookup"><span data-stu-id="53d94-103">.NET Core Global Tools overview</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

<span data-ttu-id="53d94-104">Narzędzie globalne platformy .NET Core jest specjalnym pakietem NuGet, który zawiera aplikację konsolową.</span><span class="sxs-lookup"><span data-stu-id="53d94-104">A .NET Core Global Tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="53d94-105">Narzędzie globalne można zainstalować na komputerze w lokalizacji domyślnej, która jest uwzględniona w zmiennej środowiskowej PATH lub w lokalizacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="53d94-105">A Global Tool can be installed on your machine on a default location that is included in the PATH environment variable or on a custom location.</span></span>

<span data-ttu-id="53d94-106">Jeśli chcesz użyć globalnego narzędzia platformy .NET Core:</span><span class="sxs-lookup"><span data-stu-id="53d94-106">If you want to use a .NET Core Global Tool:</span></span>

* <span data-ttu-id="53d94-107">Znajdź informacje o narzędziu (zazwyczaj witryna sieci Web lub GitHub).</span><span class="sxs-lookup"><span data-stu-id="53d94-107">Find information about the tool (usually a website or GitHub page).</span></span>
* <span data-ttu-id="53d94-108">Sprawdź autora i statystyki na stronie głównej kanału informacyjnego (zwykle NuGet.org).</span><span class="sxs-lookup"><span data-stu-id="53d94-108">Check the author and statistics in the home for the feed (usually NuGet.org).</span></span>
* <span data-ttu-id="53d94-109">Zainstaluj narzędzie.</span><span class="sxs-lookup"><span data-stu-id="53d94-109">Install the tool.</span></span>
* <span data-ttu-id="53d94-110">Wywoływanie narzędzia.</span><span class="sxs-lookup"><span data-stu-id="53d94-110">Call the tool.</span></span>
* <span data-ttu-id="53d94-111">Zaktualizuj narzędzie.</span><span class="sxs-lookup"><span data-stu-id="53d94-111">Update the tool.</span></span>
* <span data-ttu-id="53d94-112">Odinstaluj narzędzie.</span><span class="sxs-lookup"><span data-stu-id="53d94-112">Uninstall the tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="53d94-113">Narzędzia globalne platformy .NET Core są wyświetlane na ścieżce i działają w trybie pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="53d94-113">.NET Core Global Tools appear on your path and run in full trust.</span></span> <span data-ttu-id="53d94-114">Nie instaluj podstawowych narzędzi platformy .NET Core, chyba że ufasz autorowi.</span><span class="sxs-lookup"><span data-stu-id="53d94-114">Do not install .NET Core Global Tools unless you trust the author.</span></span>

## <a name="find-a-net-core-global-tool"></a><span data-ttu-id="53d94-115">Znajdź narzędzie globalne platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="53d94-115">Find a .NET Core Global Tool</span></span>

<span data-ttu-id="53d94-116">Obecnie nie istnieje funkcja globalnego wyszukiwania narzędzi w interfejsie wiersza polecenia (CLI) platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="53d94-116">Currently, there isn't a Global Tool search feature in the .NET Core Command-line Interface (CLI).</span></span>

<span data-ttu-id="53d94-117">Narzędzia platformy .NET Core można znaleźć na platformie [NuGet](https://www.nuget.org).</span><span class="sxs-lookup"><span data-stu-id="53d94-117">You can find .NET Core Global Tools on [NuGet](https://www.nuget.org).</span></span> <span data-ttu-id="53d94-118">Jednak pakiet NuGet nie zezwala jeszcze na wyszukiwanie dla narzędzi globalnych platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="53d94-118">However, NuGet doesn't yet allow you to search specifically for .NET Core Global Tools.</span></span>

<span data-ttu-id="53d94-119">Zalecenia dotyczące narzędzi można także znaleźć w wpisach w blogu lub w repozytorium GitHub [natemcmaster/dotnet-Tools](https://github.com/natemcmaster/dotnet-tools) .</span><span class="sxs-lookup"><span data-stu-id="53d94-119">You may also find tool recommendations in blog posts or in the [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub repository.</span></span>

<span data-ttu-id="53d94-120">Możesz również wyświetlić kod źródłowy narzędzi globalnych utworzonych przez zespół ASP.NET w repozytorium GitHub [/DotNetTools](https://github.com/aspnet/DotNetTools/) .</span><span class="sxs-lookup"><span data-stu-id="53d94-120">You can also see the source code for the Global Tools created by the ASP.NET team at the [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub repository.</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="53d94-121">Sprawdź autora i statystyki</span><span class="sxs-lookup"><span data-stu-id="53d94-121">Check the author and statistics</span></span>

<span data-ttu-id="53d94-122">Ponieważ globalne narzędzia platformy .NET Core działają w pełni zaufane i są zwykle instalowane na ścieżce, mogą być bardzo wydajne.</span><span class="sxs-lookup"><span data-stu-id="53d94-122">Since .NET Core Global Tools run in full trust and are generally installed on your path, they can be very powerful.</span></span> <span data-ttu-id="53d94-123">Nie pobieraj narzędzi z osób, które nie są zaufane.</span><span class="sxs-lookup"><span data-stu-id="53d94-123">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="53d94-124">Jeśli narzędzie jest hostowane w usłudze NuGet, można sprawdzić autora i statystyk, wyszukując narzędzie.</span><span class="sxs-lookup"><span data-stu-id="53d94-124">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="53d94-125">Instalowanie narzędzia globalnego</span><span class="sxs-lookup"><span data-stu-id="53d94-125">Install a Global Tool</span></span>

<span data-ttu-id="53d94-126">Aby zainstalować narzędzie globalne, należy użyć [Narzędzia dotnet zainstaluj](dotnet-tool-install.md) interfejs wiersza polecenia platformy .NET Core polecenie.</span><span class="sxs-lookup"><span data-stu-id="53d94-126">To install a Global Tool, you use the [dotnet tool install](dotnet-tool-install.md) .NET Core CLI command.</span></span> <span data-ttu-id="53d94-127">Poniższy przykład pokazuje, jak zainstalować narzędzie globalne w lokalizacji domyślnej:</span><span class="sxs-lookup"><span data-stu-id="53d94-127">The following example shows how to install a Global Tool in the default location:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="53d94-128">Jeśli nie można zainstalować narzędzia, zostaną wyświetlone komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="53d94-128">If the tool can't be installed, error messages are displayed.</span></span> <span data-ttu-id="53d94-129">Sprawdź, czy wybrane źródła danych są sprawdzane.</span><span class="sxs-lookup"><span data-stu-id="53d94-129">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="53d94-130">Jeśli próbujesz zainstalować wersję wstępną lub określoną wersję narzędzia, możesz określić numer wersji w następującym formacie:</span><span class="sxs-lookup"><span data-stu-id="53d94-130">If you're trying to install a pre-release version or a specific version of the tool, you can specify the version number using the following format:</span></span>

```dotnetcli
dotnet tool install -g <package-name> --version <version-number>
```

<span data-ttu-id="53d94-131">Jeśli instalacja zakończy się pomyślnie, zostanie wyświetlony komunikat z poleceniem, które służy do wywoływania narzędzia i zainstalowanej wersji, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="53d94-131">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

<span data-ttu-id="53d94-132">Narzędzia globalne można zainstalować w katalogu domyślnym lub w określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="53d94-132">Global Tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="53d94-133">Domyślne katalogi są następujące:</span><span class="sxs-lookup"><span data-stu-id="53d94-133">The default directories are:</span></span>

| <span data-ttu-id="53d94-134">OS</span><span class="sxs-lookup"><span data-stu-id="53d94-134">OS</span></span>          | <span data-ttu-id="53d94-135">Path</span><span class="sxs-lookup"><span data-stu-id="53d94-135">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="53d94-136">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="53d94-136">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="53d94-137">Windows</span><span class="sxs-lookup"><span data-stu-id="53d94-137">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="53d94-138">Te lokalizacje są dodawane do ścieżki użytkownika podczas pierwszego uruchomienia zestawu SDK, dzięki czemu globalne narzędzia mogą być wywoływane bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="53d94-138">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="53d94-139">Należy pamiętać, że globalne narzędzia to specyficzne dla użytkownika, a nie globalne maszyny.</span><span class="sxs-lookup"><span data-stu-id="53d94-139">Note that the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="53d94-140">Specyficzne dla użytkownika oznacza, że nie można zainstalować narzędzia globalnego, które jest dostępne dla wszystkich użytkowników komputera.</span><span class="sxs-lookup"><span data-stu-id="53d94-140">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="53d94-141">Narzędzie jest dostępne tylko dla każdego profilu użytkownika, w którym zainstalowano narzędzie.</span><span class="sxs-lookup"><span data-stu-id="53d94-141">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="53d94-142">Narzędzia globalne można także zainstalować w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="53d94-142">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="53d94-143">Po zainstalowaniu w określonym katalogu użytkownik musi upewnić się, że polecenie jest dostępne, dołączając ten katalog w ścieżce, wywołując polecenie z określonym katalogiem lub wywołując narzędzie z w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="53d94-143">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="53d94-144">W takim przypadku interfejs wiersza polecenia platformy .NET Core nie dodaje automatycznie tej lokalizacji do zmiennej środowiskowej PATH.</span><span class="sxs-lookup"><span data-stu-id="53d94-144">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="use-the-tool"></a><span data-ttu-id="53d94-145">Korzystanie z narzędzia</span><span class="sxs-lookup"><span data-stu-id="53d94-145">Use the tool</span></span>

<span data-ttu-id="53d94-146">Po zainstalowaniu narzędzia można wywołać je za pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="53d94-146">Once the tool is installed, you can call it by using its command.</span></span> <span data-ttu-id="53d94-147">Należy pamiętać, że polecenie nie może być takie samo jak nazwa pakietu.</span><span class="sxs-lookup"><span data-stu-id="53d94-147">Note that the command may not be the same as the package name.</span></span>

<span data-ttu-id="53d94-148">Jeśli polecenie jest `dotnetsay`, należy je wywołać z:</span><span class="sxs-lookup"><span data-stu-id="53d94-148">If the command is `dotnetsay`, you call it with:</span></span>

```console
dotnetsay
```

<span data-ttu-id="53d94-149">Jeśli narzędzie ma być wyświetlane w kontekście `dotnet` monitu, może napisać je w taki sposób, aby była wywoływana `dotnet <command>`w taki sposób, jak:</span><span class="sxs-lookup"><span data-stu-id="53d94-149">If the tool author wanted the tool to appear in the context of the `dotnet` prompt, they may have written it in a way that you call it as `dotnet <command>`, such as:</span></span>

```dotnetcli
dotnet doc
```

<span data-ttu-id="53d94-150">Aby znaleźć narzędzia dołączone do zainstalowanego pakietu narzędzi globalnych, należy wyświetlić listę zainstalowanych pakietów przy użyciu polecenia programu [dotnet](dotnet-tool-list.md) .</span><span class="sxs-lookup"><span data-stu-id="53d94-150">You can find which tools are included in an installed Global Tool package by listing the installed packages using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

<span data-ttu-id="53d94-151">Możesz również wyszukać instrukcje dotyczące użycia w witrynie sieci Web narzędzia lub wpisując jedno z następujących poleceń:</span><span class="sxs-lookup"><span data-stu-id="53d94-151">You can also look for usage instructions at the tool's website or by typing one of the following commands:</span></span>

```console
<command> --help
dotnet <command> --help
```

## <a name="other-cli-commands"></a><span data-ttu-id="53d94-152">Inne polecenia interfejsu CLI</span><span class="sxs-lookup"><span data-stu-id="53d94-152">Other CLI commands</span></span>

<span data-ttu-id="53d94-153">Zestaw .NET Core SDK zawiera inne polecenia, które obsługują narzędzia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="53d94-153">The .NET Core SDK contains other commands that support .NET Core Global Tools.</span></span> <span data-ttu-id="53d94-154">Użyj dowolnego `dotnet tool` polecenia z jedną z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="53d94-154">Use any of the `dotnet tool` commands with one of the following options:</span></span>

* <span data-ttu-id="53d94-155">`--global`lub `-g` określa, że polecenie ma zastosowanie do narzędzi globalnych na poziomie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="53d94-155">`--global` or `-g` specifies that the command is applicable to user-wide Global Tools.</span></span>
* <span data-ttu-id="53d94-156">`--tool-path`Określa niestandardową lokalizację dla narzędzi globalnych.</span><span class="sxs-lookup"><span data-stu-id="53d94-156">`--tool-path` specifies a custom location for Global Tools.</span></span>

<span data-ttu-id="53d94-157">Aby dowiedzieć się, które polecenia są dostępne dla narzędzi globalnych:</span><span class="sxs-lookup"><span data-stu-id="53d94-157">To find out which commands are available for Global Tools:</span></span>

```dotnetcli
dotnet tool --help
```

<span data-ttu-id="53d94-158">Aktualizacja narzędzia globalnego polega na odinstalowaniu i ponownym zainstalowaniu programu z najnowszą stabilną wersją.</span><span class="sxs-lookup"><span data-stu-id="53d94-158">Updating a Global Tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="53d94-159">Aby zaktualizować narzędzie globalne, użyj polecenia [aktualizacji narzędzia dotnet](dotnet-tool-update.md) :</span><span class="sxs-lookup"><span data-stu-id="53d94-159">To update a Global Tool, use the [dotnet tool update](dotnet-tool-update.md) command:</span></span>

```dotnetcli
dotnet tool update -g <packagename>
```

<span data-ttu-id="53d94-160">Usuń narzędzie globalne przy użyciu [Narzędzia dotnet Uninstall](dotnet-tool-uninstall.md):</span><span class="sxs-lookup"><span data-stu-id="53d94-160">Remove a Global Tool using the [dotnet tool uninstall](dotnet-tool-uninstall.md):</span></span>

```dotnetcli
dotnet tool uninstall -g <packagename>
```

<span data-ttu-id="53d94-161">Aby wyświetlić wszystkie narzędzia globalne aktualnie zainstalowane na komputerze wraz z ich wersjami i poleceniami, użyj polecenia z [listy narzędzi dotnet](dotnet-tool-list.md) :</span><span class="sxs-lookup"><span data-stu-id="53d94-161">To display all of the Global Tools currently installed on the machine, along with their version and commands, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```dotnetcli
dotnet tool list -g
```

## <a name="see-also"></a><span data-ttu-id="53d94-162">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="53d94-162">See also</span></span>

* [<span data-ttu-id="53d94-163">Rozwiązywanie problemów z użyciem narzędzia .NET Core</span><span class="sxs-lookup"><span data-stu-id="53d94-163">Troubleshoot .NET Core tool usage issues</span></span>](troubleshoot-usage-issues.md)
