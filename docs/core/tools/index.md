---
title: Interfejs wiersza polecenia platformy .NET Core
titleSuffix: ''
description: Omówienie cli .NET Core i jego funkcji.
ms.date: 02/13/2020
ms.openlocfilehash: 45a40063f70a621e807abf5e01ceecb125aecd7c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399120"
---
# <a name="net-core-cli-overview"></a><span data-ttu-id="8e780-103">Omówienie procesora CLI programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="8e780-103">.NET Core CLI overview</span></span>

<span data-ttu-id="8e780-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.1 SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="8e780-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="8e780-105">Interfejs wiersza polecenia .NET Core (CLI) jest wieloplatformowym łańcuchem narzędzi do tworzenia, tworzenia, uruchamiania i publikowania aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8e780-105">The .NET Core command-line interface (CLI) is a cross-platform toolchain for developing, building, running, and publishing .NET Core applications.</span></span>

<span data-ttu-id="8e780-106">Wartość .NET Core CLI jest dołączona do [sdk .NET Core .](../sdk.md)</span><span class="sxs-lookup"><span data-stu-id="8e780-106">The .NET Core CLI is included with the [.NET Core SDK](../sdk.md).</span></span> <span data-ttu-id="8e780-107">Aby dowiedzieć się, jak zainstalować zestaw SDK .NET Core, zobacz [Instalowanie sdk .NET Core .](../install/sdk.md)</span><span class="sxs-lookup"><span data-stu-id="8e780-107">To learn how to install the .NET Core SDK, see [Install the .NET Core SDK](../install/sdk.md).</span></span>

## <a name="cli-commands"></a><span data-ttu-id="8e780-108">Polecenia wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="8e780-108">CLI commands</span></span>

<span data-ttu-id="8e780-109">Domyślnie instalowane są następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="8e780-109">The following commands are installed by default:</span></span>

### <a name="basic-commands"></a><span data-ttu-id="8e780-110">Podstawowe polecenia</span><span class="sxs-lookup"><span data-stu-id="8e780-110">Basic commands</span></span>

- [`new`](dotnet-new.md)
- [`restore`](dotnet-restore.md)
- [`build`](dotnet-build.md)
- [`publish`](dotnet-publish.md)
- [`run`](dotnet-run.md)
- [`test`](dotnet-test.md)
- [`vstest`](dotnet-vstest.md)
- [`pack`](dotnet-pack.md)
- [`migrate`](dotnet-migrate.md)
- [`clean`](dotnet-clean.md)
- [`sln`](dotnet-sln.md)
- [`help`](dotnet-help.md)
- [`store`](dotnet-store.md)

### <a name="project-modification-commands"></a><span data-ttu-id="8e780-111">Polecenia modyfikacji projektu</span><span class="sxs-lookup"><span data-stu-id="8e780-111">Project modification commands</span></span>

- [`add package`](dotnet-add-package.md)
- [`add reference`](dotnet-add-reference.md)
- [`remove package`](dotnet-remove-package.md)
- [`remove reference`](dotnet-remove-reference.md)
- [`list reference`](dotnet-list-reference.md)

### <a name="advanced-commands"></a><span data-ttu-id="8e780-112">Polecenia zaawansowane</span><span class="sxs-lookup"><span data-stu-id="8e780-112">Advanced commands</span></span>

- [`nuget delete`](dotnet-nuget-delete.md)
- [`nuget locals`](dotnet-nuget-locals.md)
- [`nuget push`](dotnet-nuget-push.md)
- [`msbuild`](dotnet-msbuild.md)
- [`dotnet install script`](dotnet-install-script.md)

### <a name="tool-management-commands"></a><span data-ttu-id="8e780-113">Polecenia zarządzania narzędziami</span><span class="sxs-lookup"><span data-stu-id="8e780-113">Tool management commands</span></span>

- [`tool install`](dotnet-tool-install.md)
- [`tool list`](dotnet-tool-list.md)
- [`tool update`](dotnet-tool-update.md)
- <span data-ttu-id="8e780-114">[`tool restore`](global-tools.md#install-a-local-tool)Dostępne od .NET Core SDK 3.0.</span><span class="sxs-lookup"><span data-stu-id="8e780-114">[`tool restore`](global-tools.md#install-a-local-tool) Available since .NET Core SDK 3.0.</span></span>
- <span data-ttu-id="8e780-115">[`tool run`](global-tools.md#invoke-a-local-tool)Dostępne od .NET Core SDK 3.0.</span><span class="sxs-lookup"><span data-stu-id="8e780-115">[`tool run`](global-tools.md#invoke-a-local-tool) Available since .NET Core SDK 3.0.</span></span>
- [`tool uninstall`](dotnet-tool-uninstall.md)

<span data-ttu-id="8e780-116">Narzędzia są aplikacje konsoli, które są instalowane z pakietów NuGet i są wywoływane z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="8e780-116">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="8e780-117">Możesz samodzielnie pisać narzędzia lub instalować narzędzia napisane przez osoby trzecie.</span><span class="sxs-lookup"><span data-stu-id="8e780-117">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="8e780-118">Narzędzia są również znane jako narzędzia globalne, narzędzia ścieżki narzędziowej i narzędzia lokalne.</span><span class="sxs-lookup"><span data-stu-id="8e780-118">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="8e780-119">Aby uzyskać więcej informacji, zobacz [omówienie narzędzi .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="8e780-119">For more information, see [.NET Core tools overview](global-tools.md).</span></span>

## <a name="command-structure"></a><span data-ttu-id="8e780-120">Struktura poleceń</span><span class="sxs-lookup"><span data-stu-id="8e780-120">Command structure</span></span>

<span data-ttu-id="8e780-121">Struktura polecenia CLI składa się ze [sterownika ("dotnet"),](#driver) [polecenia](#command)i ewentualnie [argumentów](#arguments) poleceń i [opcji](#options).</span><span class="sxs-lookup"><span data-stu-id="8e780-121">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="8e780-122">Ten wzorzec jest wyświetlana w większości operacji wiersza polecenia, takich jak tworzenie nowej aplikacji konsoli i uruchamianie jej z wiersza polecenia, zgodnie z poniższymi poleceniami, które są wyświetlane podczas wykonywania z katalogu o nazwie *my_app:*</span><span class="sxs-lookup"><span data-stu-id="8e780-122">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a><span data-ttu-id="8e780-123">Sterownik</span><span class="sxs-lookup"><span data-stu-id="8e780-123">Driver</span></span>

<span data-ttu-id="8e780-124">Sterownik nosi nazwę [dotnet](dotnet.md) i ma dwa obowiązki, uruchamiając [aplikację zależną od struktury](../deploying/index.md) lub wykonując polecenie.</span><span class="sxs-lookup"><span data-stu-id="8e780-124">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span>

<span data-ttu-id="8e780-125">Aby uruchomić aplikację zależną od struktury, określ aplikację `dotnet /path/to/my_app.dll`po sterowniku, na przykład .</span><span class="sxs-lookup"><span data-stu-id="8e780-125">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="8e780-126">Podczas wykonywania polecenia z folderu, w którym znajduje się `dotnet my_app.dll`dll aplikacji, wystarczy wykonać .</span><span class="sxs-lookup"><span data-stu-id="8e780-126">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="8e780-127">Jeśli chcesz użyć określonej wersji programu .NET Core Runtime, użyj `--fx-version <VERSION>` tej opcji (zobacz odwołanie do polecenia [dotnet).](dotnet.md)</span><span class="sxs-lookup"><span data-stu-id="8e780-127">If you want to use a specific version of the .NET Core Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="8e780-128">Po dostarczeniu polecenia `dotnet.exe` do sterownika uruchamia proces wykonywania polecenia WIERSZA.</span><span class="sxs-lookup"><span data-stu-id="8e780-128">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="8e780-129">Przykład:</span><span class="sxs-lookup"><span data-stu-id="8e780-129">For example:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="8e780-130">Po pierwsze, sterownik określa wersję sdk do użycia.</span><span class="sxs-lookup"><span data-stu-id="8e780-130">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="8e780-131">Jeśli nie ma pliku [global.json,](global-json.md) używana jest najnowsza dostępna wersja sdk.</span><span class="sxs-lookup"><span data-stu-id="8e780-131">If there is no [global.json](global-json.md) file, the latest version of the SDK available is used.</span></span> <span data-ttu-id="8e780-132">Może to być wersja zapoznawcza lub stabilna, w zależności od tego, co jest najnowsze na komputerze.</span><span class="sxs-lookup"><span data-stu-id="8e780-132">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="8e780-133">Po ustaleniu wersji sdk wykonuje polecenie.</span><span class="sxs-lookup"><span data-stu-id="8e780-133">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="8e780-134">Polecenie</span><span class="sxs-lookup"><span data-stu-id="8e780-134">Command</span></span>

<span data-ttu-id="8e780-135">Polecenie wykonuje akcję.</span><span class="sxs-lookup"><span data-stu-id="8e780-135">The command performs an action.</span></span> <span data-ttu-id="8e780-136">Na przykład `dotnet build` tworzy kod.</span><span class="sxs-lookup"><span data-stu-id="8e780-136">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="8e780-137">`dotnet publish`publikuje kod.</span><span class="sxs-lookup"><span data-stu-id="8e780-137">`dotnet publish` publishes code.</span></span> <span data-ttu-id="8e780-138">Polecenia są implementowane jako aplikacja konsoli `dotnet {command}` przy użyciu konwencji.</span><span class="sxs-lookup"><span data-stu-id="8e780-138">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="8e780-139">Argumenty</span><span class="sxs-lookup"><span data-stu-id="8e780-139">Arguments</span></span>

<span data-ttu-id="8e780-140">Argumenty, które przekazujesz w wierszu polecenia są argumentami do wywołanych polecenia.</span><span class="sxs-lookup"><span data-stu-id="8e780-140">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="8e780-141">Na przykład podczas `dotnet publish my_app.csproj`wykonywania `my_app.csproj` , argument wskazuje projekt do `publish` opublikowania i jest przekazywany do polecenia.</span><span class="sxs-lookup"><span data-stu-id="8e780-141">For example when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="8e780-142">Opcje</span><span class="sxs-lookup"><span data-stu-id="8e780-142">Options</span></span>

<span data-ttu-id="8e780-143">Opcje, które przekazujesz w wierszu polecenia, są opcjami wywołanych polecenia.</span><span class="sxs-lookup"><span data-stu-id="8e780-143">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="8e780-144">Na przykład podczas `dotnet publish --output /build_output`wykonywania, `--output` opcja i jej `publish` wartość są przekazywane do polecenia.</span><span class="sxs-lookup"><span data-stu-id="8e780-144">For example when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e780-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8e780-145">See also</span></span>

- [<span data-ttu-id="8e780-146">Repozytorium GitHub dotnet/sdk</span><span class="sxs-lookup"><span data-stu-id="8e780-146">dotnet/sdk GitHub repository</span></span>](https://github.com/dotnet/sdk/)
- [<span data-ttu-id="8e780-147">Przewodnik instalacji programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="8e780-147">.NET Core installation guide</span></span>](../install/sdk.md)
