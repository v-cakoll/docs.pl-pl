---
title: Interfejs wiersza polecenia platformy .NET Core
titleSuffix: ''
description: Omówienie interfejsu wiersza polecenia .NET Core i jego funkcji.
ms.date: 02/13/2020
ms.openlocfilehash: ac5988bacbef41326f2501a2cff6c3f5aa0be798
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80110844"
---
# <a name="net-core-cli-overview"></a><span data-ttu-id="c86ae-103">Omówienie interfejsu wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="c86ae-103">.NET Core CLI overview</span></span>

<span data-ttu-id="c86ae-104">**Ten artykuł dotyczy:** ✔️.NET Core 2.1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="c86ae-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="c86ae-105">Interfejs wiersza polecenia .NET Core (CLI) to wieloplatformowy toolchain do tworzenia, tworzenia, uruchamiania i publikowania aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c86ae-105">The .NET Core command-line interface (CLI) is a cross-platform toolchain for developing, building, running, and publishing .NET Core applications.</span></span>

<span data-ttu-id="c86ae-106">Plik .NET Core CLI jest dołączony do [interfejsu SDK .NET Core](../sdk.md).</span><span class="sxs-lookup"><span data-stu-id="c86ae-106">The .NET Core CLI is included with the [.NET Core SDK](../sdk.md).</span></span> <span data-ttu-id="c86ae-107">Aby dowiedzieć się, jak zainstalować pakiet .NET Core SDK, zobacz [Instalowanie pakietu .NET Core SDK](../install/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="c86ae-107">To learn how to install the .NET Core SDK, see [Install the .NET Core SDK](../install/sdk.md).</span></span>

## <a name="cli-commands"></a><span data-ttu-id="c86ae-108">Polecenia interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="c86ae-108">CLI commands</span></span>

<span data-ttu-id="c86ae-109">Następujące polecenia są instalowane domyślnie:</span><span class="sxs-lookup"><span data-stu-id="c86ae-109">The following commands are installed by default:</span></span>

### <a name="basic-commands"></a><span data-ttu-id="c86ae-110">Polecenia podstawowe</span><span class="sxs-lookup"><span data-stu-id="c86ae-110">Basic commands</span></span>

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

### <a name="project-modification-commands"></a><span data-ttu-id="c86ae-111">Polecenia modyfikacji projektu</span><span class="sxs-lookup"><span data-stu-id="c86ae-111">Project modification commands</span></span>

- [`add package`](dotnet-add-package.md)
- [`add reference`](dotnet-add-reference.md)
- [`remove package`](dotnet-remove-package.md)
- [`remove reference`](dotnet-remove-reference.md)
- [`list reference`](dotnet-list-reference.md)

### <a name="advanced-commands"></a><span data-ttu-id="c86ae-112">Zaawansowane polecenia</span><span class="sxs-lookup"><span data-stu-id="c86ae-112">Advanced commands</span></span>

- [`nuget delete`](dotnet-nuget-delete.md)
- [`nuget locals`](dotnet-nuget-locals.md)
- [`nuget push`](dotnet-nuget-push.md)
- [`msbuild`](dotnet-msbuild.md)
- [`dotnet install script`](dotnet-install-script.md)

### <a name="tool-management-commands"></a><span data-ttu-id="c86ae-113">Polecenia zarządzania narzędziami</span><span class="sxs-lookup"><span data-stu-id="c86ae-113">Tool management commands</span></span>

- [`tool install`](dotnet-tool-install.md)
- [`tool list`](dotnet-tool-list.md)
- [`tool update`](dotnet-tool-update.md)
- <span data-ttu-id="c86ae-114">[`tool restore`](global-tools.md#install-a-local-tool)Dostępne od .NET Core SDK 3.0.</span><span class="sxs-lookup"><span data-stu-id="c86ae-114">[`tool restore`](global-tools.md#install-a-local-tool) Available since .NET Core SDK 3.0.</span></span>
- <span data-ttu-id="c86ae-115">[`tool run`](global-tools.md#invoke-a-local-tool)Dostępne od .NET Core SDK 3.0.</span><span class="sxs-lookup"><span data-stu-id="c86ae-115">[`tool run`](global-tools.md#invoke-a-local-tool) Available since .NET Core SDK 3.0.</span></span>
- [`tool uninstall`](dotnet-tool-uninstall.md)

<span data-ttu-id="c86ae-116">Narzędzia są aplikacje konsoli, które są instalowane z pakietów NuGet i są wywoływane z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="c86ae-116">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="c86ae-117">Możesz samodzielnie napisać narzędzia lub zainstalować narzędzia napisane przez osoby trzecie.</span><span class="sxs-lookup"><span data-stu-id="c86ae-117">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="c86ae-118">Narzędzia są również nazywane narzędziami globalnymi, narzędziami ścieżki narzędzi i narzędziami lokalnymi.</span><span class="sxs-lookup"><span data-stu-id="c86ae-118">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="c86ae-119">Aby uzyskać więcej informacji, zobacz [omówienie narzędzi .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="c86ae-119">For more information, see [.NET Core tools overview](global-tools.md).</span></span>

## <a name="command-structure"></a><span data-ttu-id="c86ae-120">Struktura poleceń</span><span class="sxs-lookup"><span data-stu-id="c86ae-120">Command structure</span></span>

<span data-ttu-id="c86ae-121">Struktura poleceń interfejsu wiersza polecenia składa się ze [sterownika ("dotnet")](#driver), [polecenia](#command)i ewentualnie [argumentów](#arguments) i [opcji](#options)polecenia.</span><span class="sxs-lookup"><span data-stu-id="c86ae-121">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="c86ae-122">Ten wzorzec jest widoczny w większości operacji interfejsu wiersza polecenia, takich jak tworzenie nowej aplikacji konsoli i uruchamianie jej z wiersza polecenia, jak pokazują następujące polecenia podczas wykonywania z katalogu o nazwie *my_app:*</span><span class="sxs-lookup"><span data-stu-id="c86ae-122">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a><span data-ttu-id="c86ae-123">Sterownik</span><span class="sxs-lookup"><span data-stu-id="c86ae-123">Driver</span></span>

<span data-ttu-id="c86ae-124">Sterownik nosi nazwę [dotnet](dotnet.md) i ma dwa obowiązki, albo z uruchomionym [aplikacją zależną od struktury,](../deploying/index.md) albo wykonując polecenie.</span><span class="sxs-lookup"><span data-stu-id="c86ae-124">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span>

<span data-ttu-id="c86ae-125">Aby uruchomić aplikację zależną od struktury, określ aplikację `dotnet /path/to/my_app.dll`po sterowniku, na przykład .</span><span class="sxs-lookup"><span data-stu-id="c86ae-125">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="c86ae-126">Podczas wykonywania polecenia z folderu, w którym znajduje się biblioteka DLL aplikacji, wystarczy wykonać `dotnet my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="c86ae-126">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="c86ae-127">Jeśli chcesz użyć określonej wersji środowiska uruchomieniowego .NET Core, użyj `--fx-version <VERSION>` tej opcji (zobacz odwołanie do polecenia [dotnet).](dotnet.md)</span><span class="sxs-lookup"><span data-stu-id="c86ae-127">If you want to use a specific version of the .NET Core Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="c86ae-128">Po podaniu polecenia do `dotnet.exe` sterownika, rozpoczyna proces wykonywania polecenia interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="c86ae-128">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="c86ae-129">Przykład:</span><span class="sxs-lookup"><span data-stu-id="c86ae-129">For example:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="c86ae-130">Najpierw sterownik określa wersję sdk do użycia.</span><span class="sxs-lookup"><span data-stu-id="c86ae-130">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="c86ae-131">Jeśli nie ma pliku [global.json,](global-json.md) używana jest najnowsza wersja sdk.</span><span class="sxs-lookup"><span data-stu-id="c86ae-131">If there is no [global.json](global-json.md) file, the latest version of the SDK available is used.</span></span> <span data-ttu-id="c86ae-132">Może to być wersja zapoznawcza lub stabilna, w zależności od tego, co jest najnowsze na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c86ae-132">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="c86ae-133">Po określeniu wersji SDK wykonuje polecenie.</span><span class="sxs-lookup"><span data-stu-id="c86ae-133">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="c86ae-134">Polecenie</span><span class="sxs-lookup"><span data-stu-id="c86ae-134">Command</span></span>

<span data-ttu-id="c86ae-135">Polecenie wykonuje akcję.</span><span class="sxs-lookup"><span data-stu-id="c86ae-135">The command performs an action.</span></span> <span data-ttu-id="c86ae-136">Na przykład `dotnet build` tworzy kod.</span><span class="sxs-lookup"><span data-stu-id="c86ae-136">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="c86ae-137">`dotnet publish`publikuje kod.</span><span class="sxs-lookup"><span data-stu-id="c86ae-137">`dotnet publish` publishes code.</span></span> <span data-ttu-id="c86ae-138">Polecenia są implementowane jako aplikacja konsoli `dotnet {command}` przy użyciu konwencji.</span><span class="sxs-lookup"><span data-stu-id="c86ae-138">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="c86ae-139">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c86ae-139">Arguments</span></span>

<span data-ttu-id="c86ae-140">Argumenty przekazywane w wierszu polecenia są argumentami do wywoływanego polecenia.</span><span class="sxs-lookup"><span data-stu-id="c86ae-140">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="c86ae-141">Na przykład podczas `dotnet publish my_app.csproj`wykonywania `my_app.csproj` argument wskazuje projekt do opublikowania i `publish` jest przekazywany do polecenia.</span><span class="sxs-lookup"><span data-stu-id="c86ae-141">For example, when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="c86ae-142">Opcje</span><span class="sxs-lookup"><span data-stu-id="c86ae-142">Options</span></span>

<span data-ttu-id="c86ae-143">Opcje przekazywane w wierszu polecenia są opcjami wywoływanym poleceniem.</span><span class="sxs-lookup"><span data-stu-id="c86ae-143">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="c86ae-144">Na przykład podczas `dotnet publish --output /build_output`wykonywania `--output` , opcja i jej `publish` wartość są przekazywane do polecenia.</span><span class="sxs-lookup"><span data-stu-id="c86ae-144">For example, when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="see-also"></a><span data-ttu-id="c86ae-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c86ae-145">See also</span></span>

- [<span data-ttu-id="c86ae-146">repozytorium Dotnet/Sdk GitHub</span><span class="sxs-lookup"><span data-stu-id="c86ae-146">dotnet/sdk GitHub repository</span></span>](https://github.com/dotnet/sdk/)
- [<span data-ttu-id="c86ae-147">Przewodnik instalacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="c86ae-147">.NET Core installation guide</span></span>](../install/sdk.md)
