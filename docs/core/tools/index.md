---
title: Interfejs wiersza polecenia platformy .NET Core
titleSuffix: ''
description: Przegląd interfejs wiersza polecenia platformy .NET Core i jego funkcji.
ms.date: 02/13/2020
ms.openlocfilehash: f92151c85b4816fef1859e84ad94945445db1854
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2020
ms.locfileid: "86415971"
---
# <a name="net-core-cli-overview"></a><span data-ttu-id="0054d-103">Omówienie interfejsu wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="0054d-103">.NET Core CLI overview</span></span>

<span data-ttu-id="0054d-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="0054d-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="0054d-105">Interfejs wiersza polecenia (CLI) platformy .NET Core to Międzyplatformowy łańcucha narzędzi służący do tworzenia, kompilowania, uruchamiania i publikowania aplikacji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0054d-105">The .NET Core command-line interface (CLI) is a cross-platform toolchain for developing, building, running, and publishing .NET Core applications.</span></span>

<span data-ttu-id="0054d-106">Interfejs wiersza polecenia platformy .NET Core jest dołączona do [zestaw .NET Core SDK](../sdk.md).</span><span class="sxs-lookup"><span data-stu-id="0054d-106">The .NET Core CLI is included with the [.NET Core SDK](../sdk.md).</span></span> <span data-ttu-id="0054d-107">Aby dowiedzieć się, jak zainstalować zestaw .NET Core SDK, zobacz [Instalowanie programu .NET Core](../install/windows.md).</span><span class="sxs-lookup"><span data-stu-id="0054d-107">To learn how to install the .NET Core SDK, see [Install .NET Core](../install/windows.md).</span></span>

## <a name="cli-commands"></a><span data-ttu-id="0054d-108">Polecenia interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="0054d-108">CLI commands</span></span>

<span data-ttu-id="0054d-109">Następujące polecenia są instalowane domyślnie:</span><span class="sxs-lookup"><span data-stu-id="0054d-109">The following commands are installed by default:</span></span>

### <a name="basic-commands"></a><span data-ttu-id="0054d-110">Polecenia podstawowe</span><span class="sxs-lookup"><span data-stu-id="0054d-110">Basic commands</span></span>

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

### <a name="project-modification-commands"></a><span data-ttu-id="0054d-111">Polecenia modyfikacji projektu</span><span class="sxs-lookup"><span data-stu-id="0054d-111">Project modification commands</span></span>

- [`add package`](dotnet-add-package.md)
- [`add reference`](dotnet-add-reference.md)
- [`remove package`](dotnet-remove-package.md)
- [`remove reference`](dotnet-remove-reference.md)
- [`list reference`](dotnet-list-reference.md)

### <a name="advanced-commands"></a><span data-ttu-id="0054d-112">Polecenia Zaawansowane</span><span class="sxs-lookup"><span data-stu-id="0054d-112">Advanced commands</span></span>

- [`nuget delete`](dotnet-nuget-delete.md)
- [`nuget locals`](dotnet-nuget-locals.md)
- [`nuget push`](dotnet-nuget-push.md)
- [`msbuild`](dotnet-msbuild.md)
- [`dotnet install script`](dotnet-install-script.md)

### <a name="tool-management-commands"></a><span data-ttu-id="0054d-113">Polecenia zarządzania narzędziami</span><span class="sxs-lookup"><span data-stu-id="0054d-113">Tool management commands</span></span>

- [`tool install`](dotnet-tool-install.md)
- [`tool list`](dotnet-tool-list.md)
- [`tool update`](dotnet-tool-update.md)
- <span data-ttu-id="0054d-114">[`tool restore`](global-tools.md#install-a-local-tool)Dostępne od zestaw .NET Core SDK 3,0.</span><span class="sxs-lookup"><span data-stu-id="0054d-114">[`tool restore`](global-tools.md#install-a-local-tool) Available since .NET Core SDK 3.0.</span></span>
- <span data-ttu-id="0054d-115">[`tool run`](global-tools.md#invoke-a-local-tool)Dostępne od zestaw .NET Core SDK 3,0.</span><span class="sxs-lookup"><span data-stu-id="0054d-115">[`tool run`](global-tools.md#invoke-a-local-tool) Available since .NET Core SDK 3.0.</span></span>
- [`tool uninstall`](dotnet-tool-uninstall.md)

<span data-ttu-id="0054d-116">Narzędzia są aplikacjami konsolowymi, które są instalowane z pakietów NuGet i są wywoływane z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="0054d-116">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="0054d-117">Narzędzia można pisać samodzielnie lub instalować Narzędzia zapisane przez inne firmy.</span><span class="sxs-lookup"><span data-stu-id="0054d-117">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="0054d-118">Narzędzia są również nazywane narzędziami globalnymi, narzędziami ścieżki narzędzi i narzędziami lokalnymi.</span><span class="sxs-lookup"><span data-stu-id="0054d-118">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="0054d-119">Aby uzyskać więcej informacji, zobacz [Narzędzia platformy .NET Core — Omówienie](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="0054d-119">For more information, see [.NET Core tools overview](global-tools.md).</span></span>

## <a name="command-structure"></a><span data-ttu-id="0054d-120">Struktura poleceń</span><span class="sxs-lookup"><span data-stu-id="0054d-120">Command structure</span></span>

<span data-ttu-id="0054d-121">Struktura poleceń interfejsu wiersza polecenia składa się ze [sterownika ("dotnet")](#driver), [polecenia](#command)oraz możliwych [argumentów](#arguments) i [opcji](#options)polecenia.</span><span class="sxs-lookup"><span data-stu-id="0054d-121">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="0054d-122">Ten wzorzec jest widoczny w większości operacji interfejsu wiersza polecenia, takich jak tworzenie nowej aplikacji konsolowej i uruchamianie jej z poziomu wiersza poleceń, ponieważ następujące polecenia pokazują, że są wykonywane z katalogu o nazwie *my_app*:</span><span class="sxs-lookup"><span data-stu-id="0054d-122">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a><span data-ttu-id="0054d-123">Sterownik</span><span class="sxs-lookup"><span data-stu-id="0054d-123">Driver</span></span>

<span data-ttu-id="0054d-124">Sterownik nosi nazwę [dotnet](dotnet.md) i ma dwie obowiązki, uruchamiają [aplikację zależną od platformy](../deploying/index.md) lub wykonując polecenie.</span><span class="sxs-lookup"><span data-stu-id="0054d-124">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span>

<span data-ttu-id="0054d-125">Aby uruchomić aplikację zależną od platformy, należy określić aplikację po stronie sterownika, na przykład `dotnet /path/to/my_app.dll` .</span><span class="sxs-lookup"><span data-stu-id="0054d-125">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="0054d-126">Gdy wykonujesz polecenie z folderu, w którym znajduje się biblioteka DLL aplikacji, po prostu wykonaj `dotnet my_app.dll` .</span><span class="sxs-lookup"><span data-stu-id="0054d-126">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="0054d-127">Jeśli chcesz użyć określonej wersji środowiska uruchomieniowego platformy .NET Core, użyj `--fx-version <VERSION>` opcji (zobacz informacje dotyczące [polecenia dotnet](dotnet.md) ).</span><span class="sxs-lookup"><span data-stu-id="0054d-127">If you want to use a specific version of the .NET Core Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="0054d-128">Po podaniu polecenia do sterownika program `dotnet.exe` uruchamia proces wykonywania poleceń interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="0054d-128">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="0054d-129">Przykład:</span><span class="sxs-lookup"><span data-stu-id="0054d-129">For example:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="0054d-130">Najpierw sterownik Określa wersję zestawu SDK do użycia.</span><span class="sxs-lookup"><span data-stu-id="0054d-130">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="0054d-131">Jeśli nie ma [global.jsw](global-json.md) pliku, używana jest Najnowsza wersja zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="0054d-131">If there is no [global.json](global-json.md) file, the latest version of the SDK available is used.</span></span> <span data-ttu-id="0054d-132">Może to być wersja zapoznawcza lub stabilna, w zależności od tego, co jest najnowsze na komputerze.</span><span class="sxs-lookup"><span data-stu-id="0054d-132">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="0054d-133">Po ustaleniu wersji zestawu SDK wykonuje polecenie.</span><span class="sxs-lookup"><span data-stu-id="0054d-133">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="0054d-134">Polecenie</span><span class="sxs-lookup"><span data-stu-id="0054d-134">Command</span></span>

<span data-ttu-id="0054d-135">Polecenie wykonuje akcję.</span><span class="sxs-lookup"><span data-stu-id="0054d-135">The command performs an action.</span></span> <span data-ttu-id="0054d-136">Na przykład `dotnet build` kompiluje kod.</span><span class="sxs-lookup"><span data-stu-id="0054d-136">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="0054d-137">`dotnet publish`publikuje kod.</span><span class="sxs-lookup"><span data-stu-id="0054d-137">`dotnet publish` publishes code.</span></span> <span data-ttu-id="0054d-138">Polecenia są implementowane jako Aplikacja konsolowa przy użyciu `dotnet {command}` Konwencji.</span><span class="sxs-lookup"><span data-stu-id="0054d-138">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="0054d-139">Argumenty</span><span class="sxs-lookup"><span data-stu-id="0054d-139">Arguments</span></span>

<span data-ttu-id="0054d-140">Argumenty przekazywane do wiersza polecenia są argumentami wywoływanego polecenia.</span><span class="sxs-lookup"><span data-stu-id="0054d-140">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="0054d-141">Na przykład po wykonaniu `dotnet publish my_app.csproj` `my_app.csproj` argument wskazuje projekt do opublikowania i jest przesyłany do `publish` polecenia.</span><span class="sxs-lookup"><span data-stu-id="0054d-141">For example, when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="0054d-142">Opcje</span><span class="sxs-lookup"><span data-stu-id="0054d-142">Options</span></span>

<span data-ttu-id="0054d-143">Opcje, które są przekazywane w wierszu polecenia są opcje wywoływanego polecenia.</span><span class="sxs-lookup"><span data-stu-id="0054d-143">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="0054d-144">Na przykład po wykonaniu `dotnet publish --output /build_output` `--output` opcji i jej wartości są przesyłane do `publish` polecenia.</span><span class="sxs-lookup"><span data-stu-id="0054d-144">For example, when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="see-also"></a><span data-ttu-id="0054d-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0054d-145">See also</span></span>

- [<span data-ttu-id="0054d-146">repozytorium usługi dotnet/zestawu SDK usługi GitHub</span><span class="sxs-lookup"><span data-stu-id="0054d-146">dotnet/sdk GitHub repository</span></span>](https://github.com/dotnet/sdk/)
- [<span data-ttu-id="0054d-147">Przewodnik instalacji programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="0054d-147">.NET Core installation guide</span></span>](../install/windows.md)
