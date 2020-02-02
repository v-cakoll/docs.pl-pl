---
title: Interfejs wiersza polecenia platformy .NET Core
titleSuffix: ''
description: Przegląd interfejs wiersza polecenia platformy .NET Core i jego funkcji.
ms.date: 08/14/2017
ms.openlocfilehash: b0a8e0dd8cf77bb6f7567c27e9972f62515ec0f2
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920483"
---
# <a name="net-core-cli-overview"></a><span data-ttu-id="279f3-103">Przegląd interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="279f3-103">.NET Core CLI overview</span></span>

<span data-ttu-id="279f3-104">Interfejs wiersza polecenia (CLI) platformy .NET Core to Międzyplatformowy łańcucha narzędzi służący do tworzenia, kompilowania, uruchamiania i publikowania aplikacji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="279f3-104">The .NET Core command-line interface (CLI) is a cross-platform toolchain for developing, building, running, and publishing .NET Core applications.</span></span>

<span data-ttu-id="279f3-105">Interfejs wiersza polecenia platformy .NET Core jest dołączona do [zestaw .NET Core SDK](../sdk.md).</span><span class="sxs-lookup"><span data-stu-id="279f3-105">The .NET Core CLI is included with the [.NET Core SDK](../sdk.md).</span></span> <span data-ttu-id="279f3-106">Aby dowiedzieć się, jak zainstalować zestaw .NET Core SDK, zobacz [Install the zestaw .NET Core SDK](../install/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="279f3-106">To learn how to install the .NET Core SDK, see [Install the .NET Core SDK](../install/sdk.md).</span></span>

## <a name="cli-commands"></a><span data-ttu-id="279f3-107">Poleceń interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="279f3-107">CLI commands</span></span>

<span data-ttu-id="279f3-108">Następujące polecenia są instalowane domyślnie:</span><span class="sxs-lookup"><span data-stu-id="279f3-108">The following commands are installed by default:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="279f3-109">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="279f3-109">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="279f3-110">**Polecenia podstawowe**</span><span class="sxs-lookup"><span data-stu-id="279f3-110">**Basic commands**</span></span>

- [<span data-ttu-id="279f3-111">new</span><span class="sxs-lookup"><span data-stu-id="279f3-111">new</span></span>](dotnet-new.md)
- [<span data-ttu-id="279f3-112">restore</span><span class="sxs-lookup"><span data-stu-id="279f3-112">restore</span></span>](dotnet-restore.md)
- [<span data-ttu-id="279f3-113">utworzenia</span><span class="sxs-lookup"><span data-stu-id="279f3-113">build</span></span>](dotnet-build.md)
- [<span data-ttu-id="279f3-114">publish</span><span class="sxs-lookup"><span data-stu-id="279f3-114">publish</span></span>](dotnet-publish.md)
- [<span data-ttu-id="279f3-115">run</span><span class="sxs-lookup"><span data-stu-id="279f3-115">run</span></span>](dotnet-run.md)
- [<span data-ttu-id="279f3-116">badan</span><span class="sxs-lookup"><span data-stu-id="279f3-116">test</span></span>](dotnet-test.md)
- [<span data-ttu-id="279f3-117">VSTest</span><span class="sxs-lookup"><span data-stu-id="279f3-117">vstest</span></span>](dotnet-vstest.md)
- [<span data-ttu-id="279f3-118">pakiet</span><span class="sxs-lookup"><span data-stu-id="279f3-118">pack</span></span>](dotnet-pack.md)
- [<span data-ttu-id="279f3-119">dokonać</span><span class="sxs-lookup"><span data-stu-id="279f3-119">migrate</span></span>](dotnet-migrate.md)
- [<span data-ttu-id="279f3-120">czyst</span><span class="sxs-lookup"><span data-stu-id="279f3-120">clean</span></span>](dotnet-clean.md)
- [<span data-ttu-id="279f3-121">sln</span><span class="sxs-lookup"><span data-stu-id="279f3-121">sln</span></span>](dotnet-sln.md)
- [<span data-ttu-id="279f3-122">Pomoc</span><span class="sxs-lookup"><span data-stu-id="279f3-122">help</span></span>](dotnet-help.md)
- [<span data-ttu-id="279f3-123">zachować</span><span class="sxs-lookup"><span data-stu-id="279f3-123">store</span></span>](dotnet-store.md)

<span data-ttu-id="279f3-124">**Polecenia modyfikacji projektu**</span><span class="sxs-lookup"><span data-stu-id="279f3-124">**Project modification commands**</span></span>

- [<span data-ttu-id="279f3-125">Dodaj pakiet</span><span class="sxs-lookup"><span data-stu-id="279f3-125">add package</span></span>](dotnet-add-package.md)
- [<span data-ttu-id="279f3-126">Dodaj odwołanie</span><span class="sxs-lookup"><span data-stu-id="279f3-126">add reference</span></span>](dotnet-add-reference.md)
- [<span data-ttu-id="279f3-127">Usuń pakiet</span><span class="sxs-lookup"><span data-stu-id="279f3-127">remove package</span></span>](dotnet-remove-package.md)
- [<span data-ttu-id="279f3-128">Usuń odwołanie</span><span class="sxs-lookup"><span data-stu-id="279f3-128">remove reference</span></span>](dotnet-remove-reference.md)
- [<span data-ttu-id="279f3-129">odwołanie do listy</span><span class="sxs-lookup"><span data-stu-id="279f3-129">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="279f3-130">**Polecenia Zaawansowane**</span><span class="sxs-lookup"><span data-stu-id="279f3-130">**Advanced commands**</span></span>

- [<span data-ttu-id="279f3-131">Usuwanie NuGet</span><span class="sxs-lookup"><span data-stu-id="279f3-131">nuget delete</span></span>](dotnet-nuget-delete.md)
- [<span data-ttu-id="279f3-132">Ustawienia regionalne NuGet</span><span class="sxs-lookup"><span data-stu-id="279f3-132">nuget locals</span></span>](dotnet-nuget-locals.md)
- [<span data-ttu-id="279f3-133">wypychanie NuGet</span><span class="sxs-lookup"><span data-stu-id="279f3-133">nuget push</span></span>](dotnet-nuget-push.md)
- [<span data-ttu-id="279f3-134">msbuild</span><span class="sxs-lookup"><span data-stu-id="279f3-134">msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="279f3-135">skrypt instalacji dotnet</span><span class="sxs-lookup"><span data-stu-id="279f3-135">dotnet install script</span></span>](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="279f3-136">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="279f3-136">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="279f3-137">**Polecenia podstawowe**</span><span class="sxs-lookup"><span data-stu-id="279f3-137">**Basic commands**</span></span>

- [<span data-ttu-id="279f3-138">new</span><span class="sxs-lookup"><span data-stu-id="279f3-138">new</span></span>](dotnet-new.md)
- [<span data-ttu-id="279f3-139">restore</span><span class="sxs-lookup"><span data-stu-id="279f3-139">restore</span></span>](dotnet-restore.md)
- [<span data-ttu-id="279f3-140">utworzenia</span><span class="sxs-lookup"><span data-stu-id="279f3-140">build</span></span>](dotnet-build.md)
- [<span data-ttu-id="279f3-141">publish</span><span class="sxs-lookup"><span data-stu-id="279f3-141">publish</span></span>](dotnet-publish.md)
- [<span data-ttu-id="279f3-142">run</span><span class="sxs-lookup"><span data-stu-id="279f3-142">run</span></span>](dotnet-run.md)
- [<span data-ttu-id="279f3-143">badan</span><span class="sxs-lookup"><span data-stu-id="279f3-143">test</span></span>](dotnet-test.md)
- [<span data-ttu-id="279f3-144">VSTest</span><span class="sxs-lookup"><span data-stu-id="279f3-144">vstest</span></span>](dotnet-vstest.md)
- [<span data-ttu-id="279f3-145">pakiet</span><span class="sxs-lookup"><span data-stu-id="279f3-145">pack</span></span>](dotnet-pack.md)
- [<span data-ttu-id="279f3-146">dokonać</span><span class="sxs-lookup"><span data-stu-id="279f3-146">migrate</span></span>](dotnet-migrate.md)
- [<span data-ttu-id="279f3-147">czyst</span><span class="sxs-lookup"><span data-stu-id="279f3-147">clean</span></span>](dotnet-clean.md)
- [<span data-ttu-id="279f3-148">sln</span><span class="sxs-lookup"><span data-stu-id="279f3-148">sln</span></span>](dotnet-sln.md)

<span data-ttu-id="279f3-149">**Polecenia modyfikacji projektu**</span><span class="sxs-lookup"><span data-stu-id="279f3-149">**Project modification commands**</span></span>

- [<span data-ttu-id="279f3-150">Dodaj pakiet</span><span class="sxs-lookup"><span data-stu-id="279f3-150">add package</span></span>](dotnet-add-package.md)
- [<span data-ttu-id="279f3-151">Dodaj odwołanie</span><span class="sxs-lookup"><span data-stu-id="279f3-151">add reference</span></span>](dotnet-add-reference.md)
- [<span data-ttu-id="279f3-152">Usuń pakiet</span><span class="sxs-lookup"><span data-stu-id="279f3-152">remove package</span></span>](dotnet-remove-package.md)
- [<span data-ttu-id="279f3-153">Usuń odwołanie</span><span class="sxs-lookup"><span data-stu-id="279f3-153">remove reference</span></span>](dotnet-remove-reference.md)
- [<span data-ttu-id="279f3-154">odwołanie do listy</span><span class="sxs-lookup"><span data-stu-id="279f3-154">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="279f3-155">**Polecenia Zaawansowane**</span><span class="sxs-lookup"><span data-stu-id="279f3-155">**Advanced commands**</span></span>

- [<span data-ttu-id="279f3-156">Usuwanie NuGet</span><span class="sxs-lookup"><span data-stu-id="279f3-156">nuget delete</span></span>](dotnet-nuget-delete.md)
- [<span data-ttu-id="279f3-157">Ustawienia regionalne NuGet</span><span class="sxs-lookup"><span data-stu-id="279f3-157">nuget locals</span></span>](dotnet-nuget-locals.md)
- [<span data-ttu-id="279f3-158">wypychanie NuGet</span><span class="sxs-lookup"><span data-stu-id="279f3-158">nuget push</span></span>](dotnet-nuget-push.md)
- [<span data-ttu-id="279f3-159">msbuild</span><span class="sxs-lookup"><span data-stu-id="279f3-159">msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="279f3-160">skrypt instalacji dotnet</span><span class="sxs-lookup"><span data-stu-id="279f3-160">dotnet install script</span></span>](dotnet-install-script.md)

---

<span data-ttu-id="279f3-161">Interfejs wiersza polecenia przyjmuje model rozszerzalności, który pozwala określić dodatkowe narzędzia dla projektów.</span><span class="sxs-lookup"><span data-stu-id="279f3-161">The CLI adopts an extensibility model that allows you to specify additional tools for your projects.</span></span> <span data-ttu-id="279f3-162">Aby uzyskać więcej informacji, zobacz temat dotyczący [modelu rozszerzalności interfejs wiersza polecenia platformy .NET Core](extensibility.md) .</span><span class="sxs-lookup"><span data-stu-id="279f3-162">For more information, see the [.NET Core CLI extensibility model](extensibility.md) topic.</span></span>

## <a name="command-structure"></a><span data-ttu-id="279f3-163">Struktura poleceń</span><span class="sxs-lookup"><span data-stu-id="279f3-163">Command structure</span></span>

<span data-ttu-id="279f3-164">Struktura poleceń interfejsu wiersza polecenia składa się ze [sterownika ("dotnet")](#driver), [polecenia](#command)oraz możliwych [argumentów](#arguments) i [opcji](#options)polecenia.</span><span class="sxs-lookup"><span data-stu-id="279f3-164">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="279f3-165">Ten wzorzec jest widoczny w większości operacji interfejsu wiersza polecenia, takich jak tworzenie nowej aplikacji konsolowej i uruchamianie jej z poziomu wiersza poleceń, ponieważ następujące polecenia pokazują, że są wykonywane z katalogu o nazwie *my_app*:</span><span class="sxs-lookup"><span data-stu-id="279f3-165">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="279f3-166">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="279f3-166">.NET Core 2.x</span></span>](#tab/netcore2x)

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="279f3-167">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="279f3-167">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

---

### <a name="driver"></a><span data-ttu-id="279f3-168">Sterownik</span><span class="sxs-lookup"><span data-stu-id="279f3-168">Driver</span></span>

<span data-ttu-id="279f3-169">Sterownik nosi nazwę [dotnet](dotnet.md) i ma dwie obowiązki, uruchamiają [aplikację zależną od platformy](../deploying/index.md) lub wykonując polecenie.</span><span class="sxs-lookup"><span data-stu-id="279f3-169">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span> 

<span data-ttu-id="279f3-170">Aby uruchomić aplikację zależną od platformy, należy określić aplikację po sterowniku, na przykład `dotnet /path/to/my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="279f3-170">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="279f3-171">Podczas wykonywania polecenia z folderu, w którym znajduje się biblioteka DLL aplikacji, wystarczy wykonać `dotnet my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="279f3-171">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="279f3-172">Jeśli chcesz użyć określonej wersji środowiska uruchomieniowego platformy .NET Core, użyj opcji `--fx-version <VERSION>` (zobacz informacje dotyczące [polecenia dotnet](dotnet.md) ).</span><span class="sxs-lookup"><span data-stu-id="279f3-172">If you want to use a specific version of the .NET Core Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="279f3-173">Gdy podasz polecenie do sterownika, `dotnet.exe` uruchamia proces wykonywania polecenia interfejsu CLI.</span><span class="sxs-lookup"><span data-stu-id="279f3-173">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="279f3-174">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="279f3-174">For example:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="279f3-175">Najpierw sterownik Określa wersję zestawu SDK do użycia.</span><span class="sxs-lookup"><span data-stu-id="279f3-175">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="279f3-176">Jeśli nie ma pliku ["Global. JSON"](global-json.md), używana jest Najnowsza wersja zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="279f3-176">If there is no ['global.json'](global-json.md), the latest version of the SDK available is used.</span></span> <span data-ttu-id="279f3-177">Może to być wersja zapoznawcza lub stabilna, w zależności od tego, co jest najnowsze na komputerze.</span><span class="sxs-lookup"><span data-stu-id="279f3-177">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="279f3-178">Po ustaleniu wersji zestawu SDK wykonuje polecenie.</span><span class="sxs-lookup"><span data-stu-id="279f3-178">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="279f3-179">Polecenie</span><span class="sxs-lookup"><span data-stu-id="279f3-179">Command</span></span>

<span data-ttu-id="279f3-180">Polecenie wykonuje akcję.</span><span class="sxs-lookup"><span data-stu-id="279f3-180">The command performs an action.</span></span> <span data-ttu-id="279f3-181">Na przykład `dotnet build` kompiluje kod.</span><span class="sxs-lookup"><span data-stu-id="279f3-181">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="279f3-182">`dotnet publish` publikuje kod.</span><span class="sxs-lookup"><span data-stu-id="279f3-182">`dotnet publish` publishes code.</span></span> <span data-ttu-id="279f3-183">Polecenia są implementowane jako Aplikacja konsolowa przy użyciu konwencji `dotnet {command}`.</span><span class="sxs-lookup"><span data-stu-id="279f3-183">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="279f3-184">Argumenty</span><span class="sxs-lookup"><span data-stu-id="279f3-184">Arguments</span></span>

<span data-ttu-id="279f3-185">Argumenty przekazywane do wiersza polecenia są argumentami wywoływanego polecenia.</span><span class="sxs-lookup"><span data-stu-id="279f3-185">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="279f3-186">Na przykład podczas wykonywania `dotnet publish my_app.csproj`argument `my_app.csproj` wskazuje projekt do opublikowania i jest przesyłany do polecenia `publish`.</span><span class="sxs-lookup"><span data-stu-id="279f3-186">For example when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="279f3-187">Opcje</span><span class="sxs-lookup"><span data-stu-id="279f3-187">Options</span></span>

<span data-ttu-id="279f3-188">Opcje, które są przekazywane w wierszu polecenia są opcje wywoływanego polecenia.</span><span class="sxs-lookup"><span data-stu-id="279f3-188">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="279f3-189">Na przykład podczas wykonywania `dotnet publish --output /build_output`opcja `--output` i jej wartość są przesyłane do polecenia `publish`.</span><span class="sxs-lookup"><span data-stu-id="279f3-189">For example when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="migration-from-projectjson"></a><span data-ttu-id="279f3-190">Migracja z pliku Project. JSON</span><span class="sxs-lookup"><span data-stu-id="279f3-190">Migration from project.json</span></span>

<span data-ttu-id="279f3-191">Jeśli użyto narzędzi w wersji zapoznawczej 2 do tworzenia projektów opartych na pliku *Project. JSON*, zapoznaj się z tematem Migrowanie środowiska [dotnet](dotnet-migrate.md) , aby uzyskać informacje na temat migrowania projektu do programu MSBuild/ *. csproj* do użytku z narzędziami Release.</span><span class="sxs-lookup"><span data-stu-id="279f3-191">If you used Preview 2 tooling to produce *project.json*-based projects, consult the [dotnet migrate](dotnet-migrate.md) topic for information on migrating your project to MSBuild/*.csproj* for use with release tooling.</span></span> <span data-ttu-id="279f3-192">W przypadku projektów .NET Core utworzonych przed udostępnieniem narzędzi wersji zapoznawczej 2 należy ręcznie zaktualizować projekt zgodnie ze wskazówkami zawartymi w sekcji [Migrowanie z środowiska DNX do interfejs wiersza polecenia platformy .NET Core (Project. JSON)](../migration/from-dnx.md) , a następnie użyć `dotnet migrate` lub bezpośrednio uaktualnić projekty.</span><span class="sxs-lookup"><span data-stu-id="279f3-192">For .NET Core projects created prior to the release of Preview 2 tooling, either manually update the project following the guidance in [Migrating from DNX to .NET Core CLI (project.json)](../migration/from-dnx.md) and then use `dotnet migrate` or directly upgrade your projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="279f3-193">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="279f3-193">See also</span></span>

- [<span data-ttu-id="279f3-194">repozytorium usługi dotnet/zestawu SDK usługi GitHub</span><span class="sxs-lookup"><span data-stu-id="279f3-194">dotnet/sdk GitHub repository</span></span>](https://github.com/dotnet/sdk/)
- [<span data-ttu-id="279f3-195">Przewodnik instalacji programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="279f3-195">.NET Core installation guide</span></span>](https://aka.ms/dotnetcoregs)
