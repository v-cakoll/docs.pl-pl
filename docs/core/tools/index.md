---
title: Interfejs wiersza polecenia platformy .NET Core
titleSuffix: ''
description: Przegląd interfejs wiersza polecenia platformy .NET Core i jego funkcji.
ms.date: 02/13/2020
ms.openlocfilehash: 1078d68ddc088274fa14b0094a81765f7af69dad
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543317"
---
# <a name="net-core-cli-overview"></a><span data-ttu-id="ee5d3-103">Przegląd interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="ee5d3-103">.NET Core CLI overview</span></span>

<span data-ttu-id="ee5d3-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="ee5d3-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="ee5d3-105">Interfejs wiersza polecenia (CLI) platformy .NET Core to Międzyplatformowy łańcucha narzędzi służący do tworzenia, kompilowania, uruchamiania i publikowania aplikacji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ee5d3-105">The .NET Core command-line interface (CLI) is a cross-platform toolchain for developing, building, running, and publishing .NET Core applications.</span></span>

<span data-ttu-id="ee5d3-106">Interfejs wiersza polecenia platformy .NET Core jest dołączona do [zestaw .NET Core SDK](../sdk.md).</span><span class="sxs-lookup"><span data-stu-id="ee5d3-106">The .NET Core CLI is included with the [.NET Core SDK](../sdk.md).</span></span> <span data-ttu-id="ee5d3-107">Aby dowiedzieć się, jak zainstalować zestaw .NET Core SDK, zobacz [Install the zestaw .NET Core SDK](../install/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="ee5d3-107">To learn how to install the .NET Core SDK, see [Install the .NET Core SDK](../install/sdk.md).</span></span>

## <a name="cli-commands"></a><span data-ttu-id="ee5d3-108">Poleceń interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="ee5d3-108">CLI commands</span></span>

<span data-ttu-id="ee5d3-109">Następujące polecenia są instalowane domyślnie:</span><span class="sxs-lookup"><span data-stu-id="ee5d3-109">The following commands are installed by default:</span></span>

### <a name="basic-commands"></a><span data-ttu-id="ee5d3-110">Polecenia podstawowe</span><span class="sxs-lookup"><span data-stu-id="ee5d3-110">Basic commands</span></span>

- [<span data-ttu-id="ee5d3-111">new</span><span class="sxs-lookup"><span data-stu-id="ee5d3-111">new</span></span>](dotnet-new.md)
- [<span data-ttu-id="ee5d3-112">restore</span><span class="sxs-lookup"><span data-stu-id="ee5d3-112">restore</span></span>](dotnet-restore.md)
- [<span data-ttu-id="ee5d3-113">utworzenia</span><span class="sxs-lookup"><span data-stu-id="ee5d3-113">build</span></span>](dotnet-build.md)
- [<span data-ttu-id="ee5d3-114">publish</span><span class="sxs-lookup"><span data-stu-id="ee5d3-114">publish</span></span>](dotnet-publish.md)
- [<span data-ttu-id="ee5d3-115">wykonane</span><span class="sxs-lookup"><span data-stu-id="ee5d3-115">run</span></span>](dotnet-run.md)
- [<span data-ttu-id="ee5d3-116">badan</span><span class="sxs-lookup"><span data-stu-id="ee5d3-116">test</span></span>](dotnet-test.md)
- [<span data-ttu-id="ee5d3-117">VSTest</span><span class="sxs-lookup"><span data-stu-id="ee5d3-117">vstest</span></span>](dotnet-vstest.md)
- [<span data-ttu-id="ee5d3-118">pakiet</span><span class="sxs-lookup"><span data-stu-id="ee5d3-118">pack</span></span>](dotnet-pack.md)
- [<span data-ttu-id="ee5d3-119">migrowanie</span><span class="sxs-lookup"><span data-stu-id="ee5d3-119">migrate</span></span>](dotnet-migrate.md)
- [<span data-ttu-id="ee5d3-120">czyst</span><span class="sxs-lookup"><span data-stu-id="ee5d3-120">clean</span></span>](dotnet-clean.md)
- [<span data-ttu-id="ee5d3-121">sln</span><span class="sxs-lookup"><span data-stu-id="ee5d3-121">sln</span></span>](dotnet-sln.md)
- [<span data-ttu-id="ee5d3-122">Pomoc</span><span class="sxs-lookup"><span data-stu-id="ee5d3-122">help</span></span>](dotnet-help.md)
- [<span data-ttu-id="ee5d3-123">zachować</span><span class="sxs-lookup"><span data-stu-id="ee5d3-123">store</span></span>](dotnet-store.md)

### <a name="project-modification-commands"></a><span data-ttu-id="ee5d3-124">Polecenia modyfikacji projektu</span><span class="sxs-lookup"><span data-stu-id="ee5d3-124">Project modification commands</span></span>

- [<span data-ttu-id="ee5d3-125">Dodaj pakiet</span><span class="sxs-lookup"><span data-stu-id="ee5d3-125">add package</span></span>](dotnet-add-package.md)
- [<span data-ttu-id="ee5d3-126">Dodaj odwołanie</span><span class="sxs-lookup"><span data-stu-id="ee5d3-126">add reference</span></span>](dotnet-add-reference.md)
- [<span data-ttu-id="ee5d3-127">Usuń pakiet</span><span class="sxs-lookup"><span data-stu-id="ee5d3-127">remove package</span></span>](dotnet-remove-package.md)
- [<span data-ttu-id="ee5d3-128">Usuń odwołanie</span><span class="sxs-lookup"><span data-stu-id="ee5d3-128">remove reference</span></span>](dotnet-remove-reference.md)
- [<span data-ttu-id="ee5d3-129">odwołanie do listy</span><span class="sxs-lookup"><span data-stu-id="ee5d3-129">list reference</span></span>](dotnet-list-reference.md)

### <a name="advanced-commands"></a><span data-ttu-id="ee5d3-130">Polecenia Zaawansowane</span><span class="sxs-lookup"><span data-stu-id="ee5d3-130">Advanced commands</span></span>

- [<span data-ttu-id="ee5d3-131">Usuwanie NuGet</span><span class="sxs-lookup"><span data-stu-id="ee5d3-131">nuget delete</span></span>](dotnet-nuget-delete.md)
- [<span data-ttu-id="ee5d3-132">Ustawienia regionalne NuGet</span><span class="sxs-lookup"><span data-stu-id="ee5d3-132">nuget locals</span></span>](dotnet-nuget-locals.md)
- [<span data-ttu-id="ee5d3-133">wypychanie NuGet</span><span class="sxs-lookup"><span data-stu-id="ee5d3-133">nuget push</span></span>](dotnet-nuget-push.md)
- [<span data-ttu-id="ee5d3-134">MSBuild</span><span class="sxs-lookup"><span data-stu-id="ee5d3-134">msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="ee5d3-135">skrypt instalacji dotnet</span><span class="sxs-lookup"><span data-stu-id="ee5d3-135">dotnet install script</span></span>](dotnet-install-script.md)

### <a name="tool-management-commands"></a><span data-ttu-id="ee5d3-136">Polecenia zarządzania narzędziami</span><span class="sxs-lookup"><span data-stu-id="ee5d3-136">Tool management commands</span></span>

- [<span data-ttu-id="ee5d3-137">Instalacja narzędzia</span><span class="sxs-lookup"><span data-stu-id="ee5d3-137">tool install</span></span>](dotnet-tool-install.md)
- [<span data-ttu-id="ee5d3-138">Lista narzędzi</span><span class="sxs-lookup"><span data-stu-id="ee5d3-138">tool list</span></span>](dotnet-tool-list.md)
- [<span data-ttu-id="ee5d3-139">Aktualizacja narzędzia</span><span class="sxs-lookup"><span data-stu-id="ee5d3-139">tool update</span></span>](dotnet-tool-update.md)
- <span data-ttu-id="ee5d3-140">dostępne [przywracanie narzędzi](global-tools.md#install-a-local-tool) **rozpoczynające się od zestaw .NET Core SDK 3,0**</span><span class="sxs-lookup"><span data-stu-id="ee5d3-140">[tool restore](global-tools.md#install-a-local-tool) **Available starting with .NET Core SDK 3.0**</span></span>
- <span data-ttu-id="ee5d3-141">dostępne [uruchomienie narzędzia](global-tools.md#invoke-a-local-tool) **rozpoczynające się od zestaw .NET Core SDK 3,0**</span><span class="sxs-lookup"><span data-stu-id="ee5d3-141">[tool run](global-tools.md#invoke-a-local-tool) **Available starting with .NET Core SDK 3.0**</span></span>
- [<span data-ttu-id="ee5d3-142">Odinstalowywanie narzędzia</span><span class="sxs-lookup"><span data-stu-id="ee5d3-142">tool uninstall</span></span>](dotnet-tool-uninstall.md)

<span data-ttu-id="ee5d3-143">Narzędzia są aplikacjami konsolowymi, które są instalowane z pakietów NuGet i są wywoływane z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="ee5d3-143">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="ee5d3-144">Narzędzia można pisać samodzielnie lub instalować Narzędzia zapisane przez inne firmy.</span><span class="sxs-lookup"><span data-stu-id="ee5d3-144">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="ee5d3-145">Narzędzia są również nazywane narzędziami globalnymi, narzędziami ścieżki narzędzi i narzędziami lokalnymi.</span><span class="sxs-lookup"><span data-stu-id="ee5d3-145">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="ee5d3-146">Aby uzyskać więcej informacji, zobacz [Narzędzia platformy .NET Core — Omówienie](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="ee5d3-146">For more information, see [.NET Core tools overview](global-tools.md).</span></span>

## <a name="command-structure"></a><span data-ttu-id="ee5d3-147">Struktura poleceń</span><span class="sxs-lookup"><span data-stu-id="ee5d3-147">Command structure</span></span>

<span data-ttu-id="ee5d3-148">Struktura poleceń interfejsu wiersza polecenia składa się ze [sterownika ("dotnet")](#driver), [polecenia](#command)oraz możliwych [argumentów](#arguments) i [opcji](#options)polecenia.</span><span class="sxs-lookup"><span data-stu-id="ee5d3-148">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="ee5d3-149">Ten wzorzec jest widoczny w większości operacji interfejsu wiersza polecenia, takich jak tworzenie nowej aplikacji konsolowej i uruchamianie jej z poziomu wiersza poleceń, ponieważ następujące polecenia pokazują, że są wykonywane z katalogu o nazwie *my_app*:</span><span class="sxs-lookup"><span data-stu-id="ee5d3-149">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a><span data-ttu-id="ee5d3-150">Sterownik</span><span class="sxs-lookup"><span data-stu-id="ee5d3-150">Driver</span></span>

<span data-ttu-id="ee5d3-151">Sterownik nosi nazwę [dotnet](dotnet.md) i ma dwie obowiązki, uruchamiają [aplikację zależną od platformy](../deploying/index.md) lub wykonując polecenie.</span><span class="sxs-lookup"><span data-stu-id="ee5d3-151">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span> 

<span data-ttu-id="ee5d3-152">Aby uruchomić aplikację zależną od platformy, należy określić aplikację po sterowniku, na przykład `dotnet /path/to/my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="ee5d3-152">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="ee5d3-153">Podczas wykonywania polecenia z folderu, w którym znajduje się biblioteka DLL aplikacji, wystarczy wykonać `dotnet my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="ee5d3-153">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="ee5d3-154">Jeśli chcesz użyć określonej wersji środowiska uruchomieniowego platformy .NET Core, użyj opcji `--fx-version <VERSION>` (zobacz informacje dotyczące [polecenia dotnet](dotnet.md) ).</span><span class="sxs-lookup"><span data-stu-id="ee5d3-154">If you want to use a specific version of the .NET Core Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="ee5d3-155">Gdy podasz polecenie do sterownika, `dotnet.exe` uruchamia proces wykonywania polecenia interfejsu CLI.</span><span class="sxs-lookup"><span data-stu-id="ee5d3-155">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="ee5d3-156">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="ee5d3-156">For example:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="ee5d3-157">Najpierw sterownik Określa wersję zestawu SDK do użycia.</span><span class="sxs-lookup"><span data-stu-id="ee5d3-157">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="ee5d3-158">Jeśli nie ma pliku ["Global. JSON"](global-json.md), używana jest Najnowsza wersja zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="ee5d3-158">If there is no ['global.json'](global-json.md), the latest version of the SDK available is used.</span></span> <span data-ttu-id="ee5d3-159">Może to być wersja zapoznawcza lub stabilna, w zależności od tego, co jest najnowsze na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ee5d3-159">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="ee5d3-160">Po ustaleniu wersji zestawu SDK wykonuje polecenie.</span><span class="sxs-lookup"><span data-stu-id="ee5d3-160">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="ee5d3-161">Polecenie</span><span class="sxs-lookup"><span data-stu-id="ee5d3-161">Command</span></span>

<span data-ttu-id="ee5d3-162">Polecenie wykonuje akcję.</span><span class="sxs-lookup"><span data-stu-id="ee5d3-162">The command performs an action.</span></span> <span data-ttu-id="ee5d3-163">Na przykład `dotnet build` kompiluje kod.</span><span class="sxs-lookup"><span data-stu-id="ee5d3-163">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="ee5d3-164">`dotnet publish` publikuje kod.</span><span class="sxs-lookup"><span data-stu-id="ee5d3-164">`dotnet publish` publishes code.</span></span> <span data-ttu-id="ee5d3-165">Polecenia są implementowane jako Aplikacja konsolowa przy użyciu konwencji `dotnet {command}`.</span><span class="sxs-lookup"><span data-stu-id="ee5d3-165">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="ee5d3-166">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ee5d3-166">Arguments</span></span>

<span data-ttu-id="ee5d3-167">Argumenty przekazywane do wiersza polecenia są argumentami wywoływanego polecenia.</span><span class="sxs-lookup"><span data-stu-id="ee5d3-167">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="ee5d3-168">Na przykład podczas wykonywania `dotnet publish my_app.csproj`argument `my_app.csproj` wskazuje projekt do opublikowania i jest przesyłany do polecenia `publish`.</span><span class="sxs-lookup"><span data-stu-id="ee5d3-168">For example when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="ee5d3-169">Opcje</span><span class="sxs-lookup"><span data-stu-id="ee5d3-169">Options</span></span>

<span data-ttu-id="ee5d3-170">Opcje, które są przekazywane w wierszu polecenia są opcje wywoływanego polecenia.</span><span class="sxs-lookup"><span data-stu-id="ee5d3-170">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="ee5d3-171">Na przykład podczas wykonywania `dotnet publish --output /build_output`opcja `--output` i jej wartość są przesyłane do polecenia `publish`.</span><span class="sxs-lookup"><span data-stu-id="ee5d3-171">For example when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee5d3-172">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ee5d3-172">See also</span></span>

- [<span data-ttu-id="ee5d3-173">repozytorium usługi dotnet/zestawu SDK usługi GitHub</span><span class="sxs-lookup"><span data-stu-id="ee5d3-173">dotnet/sdk GitHub repository</span></span>](https://github.com/dotnet/sdk/)
- [<span data-ttu-id="ee5d3-174">Przewodnik instalacji programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="ee5d3-174">.NET Core installation guide</span></span>](../install/sdk.md)
