---
title: Narzędzia programu .NET core interfejsu wiersza polecenia (CLI)
description: Przegląd funkcji i narzędzi .NET Core interfejsu wiersza polecenia (CLI).
ms.date: 08/14/2017
ms.custom: seodec18
ms.openlocfilehash: e174867ce06e573fc85579183df0196d8276fb37
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826317"
---
# <a name="net-core-command-line-interface-cli-tools"></a><span data-ttu-id="840fc-103">Narzędzia interfejsu wiersza polecenia (CLI) platformy .NET core</span><span class="sxs-lookup"><span data-stu-id="840fc-103">.NET Core command-line interface (CLI) tools</span></span>

<span data-ttu-id="840fc-104">Interfejsu wiersza polecenia (CLI) platformy .NET Core to nowe łańcucha narzędzi i platform do tworzenia aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="840fc-104">The .NET Core command-line interface (CLI) is a new cross-platform toolchain for developing .NET applications.</span></span> <span data-ttu-id="840fc-105">Interfejs wiersza polecenia jest podstawę, na które narzędzia wyższego poziomu, takie jak umieścić zintegrowanych środowisk projektowych (IDE), edytory i koordynatorów kompilacji.</span><span class="sxs-lookup"><span data-stu-id="840fc-105">The CLI is a foundation upon which higher-level tools, such as Integrated Development Environments (IDEs), editors, and build orchestrators, can rest.</span></span>

## <a name="installation"></a><span data-ttu-id="840fc-106">Instalacja</span><span class="sxs-lookup"><span data-stu-id="840fc-106">Installation</span></span>

<span data-ttu-id="840fc-107">Użyj natywnych instalatorów lub za pomocą skryptów powłoki instalacji:</span><span class="sxs-lookup"><span data-stu-id="840fc-107">Either use the native installers or use the installation shell scripts:</span></span>

* <span data-ttu-id="840fc-108">Natywnych instalatorów są używane przede wszystkim na maszynach dewelopera i natywne za każdym obsługiwanych platform Zainstaluj mechanizm, na przykład DEB pakiety na pakiety MSI lub Ubuntu na Windows.</span><span class="sxs-lookup"><span data-stu-id="840fc-108">The native installers are primarily used on developer's machines and use each supported platform's native install mechanism, for instance, DEB packages on Ubuntu or MSI bundles on Windows.</span></span> <span data-ttu-id="840fc-109">Te pliki instalacyjne zainstalować i skonfigurować środowisko do użycia przez dewelopera, ale wymagają uprawnień administratora na komputerze.</span><span class="sxs-lookup"><span data-stu-id="840fc-109">These installers install and configure the environment for immediate use by the developer but require administrative privileges on the machine.</span></span> <span data-ttu-id="840fc-110">Możesz wyświetlić instrukcje dotyczące instalacji w [Przewodnik instalacji platformy .NET Core](https://aka.ms/dotnetcoregs).</span><span class="sxs-lookup"><span data-stu-id="840fc-110">You can view the installation instructions in the [.NET Core installation guide](https://aka.ms/dotnetcoregs).</span></span>
* <span data-ttu-id="840fc-111">Skrypty powłoki są głównie używane do konfigurowania serwerów kompilacji lub gdy chcesz zainstalować narzędzia bez uprawnień administracyjnych.</span><span class="sxs-lookup"><span data-stu-id="840fc-111">Shell scripts are primarily used for setting up build servers or when you wish to install the tools without administrative privileges.</span></span> <span data-ttu-id="840fc-112">Zainstaluj skrypty wymagań wstępnych nie należy instalować na komputerze, który musi zostać zainstalowany ręcznie.</span><span class="sxs-lookup"><span data-stu-id="840fc-112">Install scripts don't install prerequisites on the machine, which must be installed manually.</span></span> <span data-ttu-id="840fc-113">Aby uzyskać więcej informacji, zobacz [zainstalować temat referencyjny skryptu](dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="840fc-113">For more information, see the [install script reference topic](dotnet-install-script.md).</span></span> <span data-ttu-id="840fc-114">Aby uzyskać informacji na temat sposobu konfigurowania interfejsu wiersza polecenia na serwerze kompilacji ciągłej integracji (CI), zobacz [przy użyciu zestawu .NET Core SDK i narzędzia w ciągłej integracji (CI)](using-ci-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="840fc-114">For information on how to set up CLI on your continuous integration (CI) build server, see [Using .NET Core SDK and tools in Continuous Integration (CI)](using-ci-with-cli.md).</span></span>

<span data-ttu-id="840fc-115">Domyślnie interfejs wiersza polecenia instaluje w sposób side-by-side (SxS) tak wielu wersji narzędzi interfejsu wiersza polecenia mogą współistnieć na jednym komputerze.</span><span class="sxs-lookup"><span data-stu-id="840fc-115">By default, the CLI installs in a side-by-side (SxS) manner, so multiple versions of the CLI tools can coexist on a single machine.</span></span> <span data-ttu-id="840fc-116">Określenie, która wersja jest używana na komputerze, gdzie jest zainstalowanych wiele wersji zostało wyjaśnione bardziej szczegółowo w [sterownika](#driver) sekcji.</span><span class="sxs-lookup"><span data-stu-id="840fc-116">Determining which version is used on a machine where multiple versions are installed is explained in more detail in the [Driver](#driver) section.</span></span>

## <a name="cli-commands"></a><span data-ttu-id="840fc-117">Polecenia interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="840fc-117">CLI commands</span></span>

<span data-ttu-id="840fc-118">Następujące polecenia są instalowane domyślnie:</span><span class="sxs-lookup"><span data-stu-id="840fc-118">The following commands are installed by default:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="840fc-119">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="840fc-119">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="840fc-120">**Podstawowe polecenia**</span><span class="sxs-lookup"><span data-stu-id="840fc-120">**Basic commands**</span></span>

* [<span data-ttu-id="840fc-121">new</span><span class="sxs-lookup"><span data-stu-id="840fc-121">new</span></span>](dotnet-new.md)
* [<span data-ttu-id="840fc-122">restore</span><span class="sxs-lookup"><span data-stu-id="840fc-122">restore</span></span>](dotnet-restore.md)
* [<span data-ttu-id="840fc-123">Kompilacja</span><span class="sxs-lookup"><span data-stu-id="840fc-123">build</span></span>](dotnet-build.md)
* [<span data-ttu-id="840fc-124">publish</span><span class="sxs-lookup"><span data-stu-id="840fc-124">publish</span></span>](dotnet-publish.md)
* [<span data-ttu-id="840fc-125">run</span><span class="sxs-lookup"><span data-stu-id="840fc-125">run</span></span>](dotnet-run.md)
* [<span data-ttu-id="840fc-126">Test</span><span class="sxs-lookup"><span data-stu-id="840fc-126">test</span></span>](dotnet-test.md)
* [<span data-ttu-id="840fc-127">vstest</span><span class="sxs-lookup"><span data-stu-id="840fc-127">vstest</span></span>](dotnet-vstest.md)
* [<span data-ttu-id="840fc-128">pakiet</span><span class="sxs-lookup"><span data-stu-id="840fc-128">pack</span></span>](dotnet-pack.md)
* [<span data-ttu-id="840fc-129">Migracja</span><span class="sxs-lookup"><span data-stu-id="840fc-129">migrate</span></span>](dotnet-migrate.md)
* [<span data-ttu-id="840fc-130">czyszczenie</span><span class="sxs-lookup"><span data-stu-id="840fc-130">clean</span></span>](dotnet-clean.md)
* [<span data-ttu-id="840fc-131">sln</span><span class="sxs-lookup"><span data-stu-id="840fc-131">sln</span></span>](dotnet-sln.md)
* [<span data-ttu-id="840fc-132">Pomoc</span><span class="sxs-lookup"><span data-stu-id="840fc-132">help</span></span>](dotnet-help.md)
* [<span data-ttu-id="840fc-133">store</span><span class="sxs-lookup"><span data-stu-id="840fc-133">store</span></span>](dotnet-store.md)

<span data-ttu-id="840fc-134">**Polecenia modyfikacji projektu**</span><span class="sxs-lookup"><span data-stu-id="840fc-134">**Project modification commands**</span></span>

* [<span data-ttu-id="840fc-135">Dodaj pakiet</span><span class="sxs-lookup"><span data-stu-id="840fc-135">add package</span></span>](dotnet-add-package.md)
* [<span data-ttu-id="840fc-136">Dodawanie odwołania</span><span class="sxs-lookup"><span data-stu-id="840fc-136">add reference</span></span>](dotnet-add-reference.md)
* [<span data-ttu-id="840fc-137">Usuń pakiet</span><span class="sxs-lookup"><span data-stu-id="840fc-137">remove package</span></span>](dotnet-remove-package.md)
* [<span data-ttu-id="840fc-138">Usuwanie odwołań</span><span class="sxs-lookup"><span data-stu-id="840fc-138">remove reference</span></span>](dotnet-remove-reference.md)
* [<span data-ttu-id="840fc-139">Odwołanie do listy</span><span class="sxs-lookup"><span data-stu-id="840fc-139">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="840fc-140">**Zaawansowane polecenia**</span><span class="sxs-lookup"><span data-stu-id="840fc-140">**Advanced commands**</span></span>

* [<span data-ttu-id="840fc-141">Usuń nuget</span><span class="sxs-lookup"><span data-stu-id="840fc-141">nuget delete</span></span>](dotnet-nuget-delete.md)
* [<span data-ttu-id="840fc-142">Zmienne lokalne nuget</span><span class="sxs-lookup"><span data-stu-id="840fc-142">nuget locals</span></span>](dotnet-nuget-locals.md)
* [<span data-ttu-id="840fc-143">nuget wypychania</span><span class="sxs-lookup"><span data-stu-id="840fc-143">nuget push</span></span>](dotnet-nuget-push.md)
* [<span data-ttu-id="840fc-144">msbuild</span><span class="sxs-lookup"><span data-stu-id="840fc-144">msbuild</span></span>](dotnet-msbuild.md)
* [<span data-ttu-id="840fc-145">skrypt instalacji DotNet</span><span class="sxs-lookup"><span data-stu-id="840fc-145">dotnet install script</span></span>](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="840fc-146">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="840fc-146">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="840fc-147">**Podstawowe polecenia**</span><span class="sxs-lookup"><span data-stu-id="840fc-147">**Basic commands**</span></span>

* [<span data-ttu-id="840fc-148">new</span><span class="sxs-lookup"><span data-stu-id="840fc-148">new</span></span>](dotnet-new.md)
* [<span data-ttu-id="840fc-149">restore</span><span class="sxs-lookup"><span data-stu-id="840fc-149">restore</span></span>](dotnet-restore.md)
* [<span data-ttu-id="840fc-150">Kompilacja</span><span class="sxs-lookup"><span data-stu-id="840fc-150">build</span></span>](dotnet-build.md)
* [<span data-ttu-id="840fc-151">publish</span><span class="sxs-lookup"><span data-stu-id="840fc-151">publish</span></span>](dotnet-publish.md)
* [<span data-ttu-id="840fc-152">run</span><span class="sxs-lookup"><span data-stu-id="840fc-152">run</span></span>](dotnet-run.md)
* [<span data-ttu-id="840fc-153">Test</span><span class="sxs-lookup"><span data-stu-id="840fc-153">test</span></span>](dotnet-test.md)
* [<span data-ttu-id="840fc-154">vstest</span><span class="sxs-lookup"><span data-stu-id="840fc-154">vstest</span></span>](dotnet-vstest.md)
* [<span data-ttu-id="840fc-155">pakiet</span><span class="sxs-lookup"><span data-stu-id="840fc-155">pack</span></span>](dotnet-pack.md)
* [<span data-ttu-id="840fc-156">Migracja</span><span class="sxs-lookup"><span data-stu-id="840fc-156">migrate</span></span>](dotnet-migrate.md)
* [<span data-ttu-id="840fc-157">czyszczenie</span><span class="sxs-lookup"><span data-stu-id="840fc-157">clean</span></span>](dotnet-clean.md)
* [<span data-ttu-id="840fc-158">sln</span><span class="sxs-lookup"><span data-stu-id="840fc-158">sln</span></span>](dotnet-sln.md)

<span data-ttu-id="840fc-159">**Polecenia modyfikacji projektu**</span><span class="sxs-lookup"><span data-stu-id="840fc-159">**Project modification commands**</span></span>

* [<span data-ttu-id="840fc-160">Dodaj pakiet</span><span class="sxs-lookup"><span data-stu-id="840fc-160">add package</span></span>](dotnet-add-package.md)
* [<span data-ttu-id="840fc-161">Dodawanie odwołania</span><span class="sxs-lookup"><span data-stu-id="840fc-161">add reference</span></span>](dotnet-add-reference.md)
* [<span data-ttu-id="840fc-162">Usuń pakiet</span><span class="sxs-lookup"><span data-stu-id="840fc-162">remove package</span></span>](dotnet-remove-package.md)
* [<span data-ttu-id="840fc-163">Usuwanie odwołań</span><span class="sxs-lookup"><span data-stu-id="840fc-163">remove reference</span></span>](dotnet-remove-reference.md)
* [<span data-ttu-id="840fc-164">Odwołanie do listy</span><span class="sxs-lookup"><span data-stu-id="840fc-164">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="840fc-165">**Zaawansowane polecenia**</span><span class="sxs-lookup"><span data-stu-id="840fc-165">**Advanced commands**</span></span>

* [<span data-ttu-id="840fc-166">Usuń nuget</span><span class="sxs-lookup"><span data-stu-id="840fc-166">nuget delete</span></span>](dotnet-nuget-delete.md)
* [<span data-ttu-id="840fc-167">Zmienne lokalne nuget</span><span class="sxs-lookup"><span data-stu-id="840fc-167">nuget locals</span></span>](dotnet-nuget-locals.md)
* [<span data-ttu-id="840fc-168">nuget wypychania</span><span class="sxs-lookup"><span data-stu-id="840fc-168">nuget push</span></span>](dotnet-nuget-push.md)
* [<span data-ttu-id="840fc-169">msbuild</span><span class="sxs-lookup"><span data-stu-id="840fc-169">msbuild</span></span>](dotnet-msbuild.md)
* [<span data-ttu-id="840fc-170">skrypt instalacji DotNet</span><span class="sxs-lookup"><span data-stu-id="840fc-170">dotnet install script</span></span>](dotnet-install-script.md)

---

<span data-ttu-id="840fc-171">Interfejs wiersza polecenia przyjmuje model rozszerzeń, który umożliwia określenie dodatkowych narzędzi dla projektów.</span><span class="sxs-lookup"><span data-stu-id="840fc-171">The CLI adopts an extensibility model that allows you to specify additional tools for your projects.</span></span> <span data-ttu-id="840fc-172">Aby uzyskać więcej informacji, zobacz [modelu rozszerzeń interfejsu wiersza polecenia platformy .NET Core](extensibility.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="840fc-172">For more information, see the [.NET Core CLI extensibility model](extensibility.md) topic.</span></span>

## <a name="command-structure"></a><span data-ttu-id="840fc-173">Struktura polecenia</span><span class="sxs-lookup"><span data-stu-id="840fc-173">Command structure</span></span>

<span data-ttu-id="840fc-174">Struktura polecenia interfejsu wiersza polecenia składa się z [sterownika ("dotnet")](#driver), [polecenie (lub "verb")](#command-verb)i ewentualnie polecenia [argumenty](#arguments) i [opcje](#options).</span><span class="sxs-lookup"><span data-stu-id="840fc-174">CLI command structure consists of [the driver ("dotnet")](#driver), [the command (or "verb")](#command-verb), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="840fc-175">Zostanie wyświetlony ten wzorzec w przypadku większości operacji interfejsu wiersza polecenia, takie jak tworzenie nowej aplikacji konsoli i uruchamiając go z poziomu wiersza polecenia jako następujące polecenia, Pokaż podczas wykonywania z katalogu o nazwie *moja_aplikacja*:</span><span class="sxs-lookup"><span data-stu-id="840fc-175">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="840fc-176">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="840fc-176">.NET Core 2.x</span></span>](#tab/netcore2x)

```console
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="840fc-177">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="840fc-177">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

---

### <a name="driver"></a><span data-ttu-id="840fc-178">Sterownik</span><span class="sxs-lookup"><span data-stu-id="840fc-178">Driver</span></span>

<span data-ttu-id="840fc-179">Nosi nazwę sterownika [dotnet](dotnet.md) i ma dwa odpowiedzialności, albo uruchamianie [zależny od struktury aplikacji](../deploying/index.md) lub wykonywania polecenia.</span><span class="sxs-lookup"><span data-stu-id="840fc-179">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span> 

<span data-ttu-id="840fc-180">Uruchamianie aplikacji zależny od struktury, na przykład określić aplikację po sterownika, `dotnet /path/to/my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="840fc-180">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="840fc-181">Podczas wykonywania polecenia z folderu, w którym znajduje się biblioteki DLL z aplikacji, po prostu wykonaj `dotnet my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="840fc-181">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="840fc-182">Jeśli chcesz użyć określonej wersji środowiska uruchomieniowego programu .NET Core, użyj `--fx-version <VERSION>` opcji (zobacz [polecenia dotnet](dotnet.md) odwołania).</span><span class="sxs-lookup"><span data-stu-id="840fc-182">If you want to use a specific version of the .NET Core Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="840fc-183">Podczas dostarczania polecenia do sterownika, `dotnet.exe` rozpoczyna się proces wykonywania polecenia interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="840fc-183">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="840fc-184">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="840fc-184">For example:</span></span>

```bash
> dotnet build
```

<span data-ttu-id="840fc-185">Po pierwsze sterownik Określa wersję zestawu SDK do użycia.</span><span class="sxs-lookup"><span data-stu-id="840fc-185">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="840fc-186">Jeśli ma nie ["global.json"](global-json.md), służy najnowszą wersję zestawu SDK, które są dostępne.</span><span class="sxs-lookup"><span data-stu-id="840fc-186">If there is no ['global.json'](global-json.md), the latest version of the SDK available is used.</span></span> <span data-ttu-id="840fc-187">Może to być w wersji zapoznawczej albo stabilną wersję, w zależności od tego, co to jest najnowsze na komputerze.</span><span class="sxs-lookup"><span data-stu-id="840fc-187">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="840fc-188">Po określeniu wersji zestawu SDK wykonuje polecenie.</span><span class="sxs-lookup"><span data-stu-id="840fc-188">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command-verb"></a><span data-ttu-id="840fc-189">Polecenie ("verb")</span><span class="sxs-lookup"><span data-stu-id="840fc-189">Command ("verb")</span></span>

<span data-ttu-id="840fc-190">Polecenie (lub "verb") jest po prostu polecenie, które wykonują akcję.</span><span class="sxs-lookup"><span data-stu-id="840fc-190">The command (or "verb") is simply a command that performs an action.</span></span> <span data-ttu-id="840fc-191">Na przykład `dotnet build` kompiluje kod.</span><span class="sxs-lookup"><span data-stu-id="840fc-191">For example, `dotnet build` builds your code.</span></span> <span data-ttu-id="840fc-192">`dotnet publish` publikuje swój kod.</span><span class="sxs-lookup"><span data-stu-id="840fc-192">`dotnet publish` publishes your code.</span></span> <span data-ttu-id="840fc-193">Polecenia są implementowane jako aplikacji konsoli za pomocą `dotnet {verb}` Konwencji.</span><span class="sxs-lookup"><span data-stu-id="840fc-193">The commands are implemented as a console application using a `dotnet {verb}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="840fc-194">Argumenty</span><span class="sxs-lookup"><span data-stu-id="840fc-194">Arguments</span></span>

<span data-ttu-id="840fc-195">Argumenty, które należy przekazać w wierszu polecenia są argumenty polecenia wywoływane.</span><span class="sxs-lookup"><span data-stu-id="840fc-195">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="840fc-196">Na przykład podczas wykonywania `dotnet publish my_app.csproj`, `my_app.csproj` argument określa projekt do publikowania i jest przekazywany do `publish` polecenia.</span><span class="sxs-lookup"><span data-stu-id="840fc-196">For example when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="840fc-197">Opcje</span><span class="sxs-lookup"><span data-stu-id="840fc-197">Options</span></span>

<span data-ttu-id="840fc-198">Opcje, które należy przekazać w wierszu polecenia są opcje polecenia wywoływane.</span><span class="sxs-lookup"><span data-stu-id="840fc-198">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="840fc-199">Na przykład podczas wykonywania `dotnet publish --output /build_output`, `--output` opcję i jej wartość są przekazywane do `publish` polecenia.</span><span class="sxs-lookup"><span data-stu-id="840fc-199">For example when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="migration-from-projectjson"></a><span data-ttu-id="840fc-200">Migracja z pliku project.json</span><span class="sxs-lookup"><span data-stu-id="840fc-200">Migration from project.json</span></span>

<span data-ttu-id="840fc-201">Jeśli używasz narzędzia do tworzenia w wersji 2 *project.json*— na podstawie projektów, zapoznaj się z [migracji dotnet](dotnet-migrate.md) zawiera informacje na temat migracji projektu do programu MSBuild /*.csproj*do użytku z wersji narzędzia.</span><span class="sxs-lookup"><span data-stu-id="840fc-201">If you used Preview 2 tooling to produce *project.json*-based projects, consult the [dotnet migrate](dotnet-migrate.md) topic for information on migrating your project to MSBuild/*.csproj* for use with release tooling.</span></span> <span data-ttu-id="840fc-202">Dla platformy .NET Core projektów utworzonych przed wydaniem narzędzi w wersji 2, ręcznie zaktualizować projekt, postępując zgodnie ze wskazówkami w [migrowanie ze środowiska DNX, .NET Core interfejsu wiersza polecenia (project.json)](../migration/from-dnx.md) , a następnie użyj `dotnet migrate` lub bezpośrednio uaktualnienia Twoich projektów.</span><span class="sxs-lookup"><span data-stu-id="840fc-202">For .NET Core projects created prior to the release of Preview 2 tooling, either manually update the project following the guidance in [Migrating from DNX to .NET Core CLI (project.json)](../migration/from-dnx.md) and then use `dotnet migrate` or directly upgrade your projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="840fc-203">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="840fc-203">See also</span></span>

- [<span data-ttu-id="840fc-204">/ interfejsu wiersza polecenia DotNet repozytorium GitHub</span><span class="sxs-lookup"><span data-stu-id="840fc-204">dotnet/CLI GitHub Repository</span></span>](https://github.com/dotnet/cli/)
- [<span data-ttu-id="840fc-205">Przewodnik instalacji platformy .NET core</span><span class="sxs-lookup"><span data-stu-id="840fc-205">.NET Core installation guide</span></span>](https://aka.ms/dotnetcoregs)
