---
title: Narzędzia interfejsu wiersza polecenia (CLI) platformy .NET Core
description: Omówienie narzędzi i funkcji interfejsu wiersza polecenia (CLI) platformy .NET Core.
ms.date: 08/14/2017
ms.openlocfilehash: b3bffb47ff973bd0da90e3f943e817756e563138
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714148"
---
# <a name="net-core-command-line-interface-cli-tools"></a><span data-ttu-id="02fac-103">Narzędzia interfejsu wiersza polecenia (CLI) platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="02fac-103">.NET Core command-line interface (CLI) tools</span></span>

<span data-ttu-id="02fac-104">Interfejs wiersza polecenia platformy .NET Core (CLI) to nowe Międzyplatformowe łańcucha narzędzi do tworzenia aplikacji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="02fac-104">The .NET Core command-line interface (CLI) is a new cross-platform toolchain for developing .NET applications.</span></span> <span data-ttu-id="02fac-105">Interfejs wiersza polecenia jest podstawą, na której można zawiesić narzędzia wyższego poziomu, takie jak zintegrowane środowiska deweloperskie (środowisk IDE), Edytory i koordynatorzy kompilacji.</span><span class="sxs-lookup"><span data-stu-id="02fac-105">The CLI is a foundation upon which higher-level tools, such as Integrated Development Environments (IDEs), editors, and build orchestrators, can rest.</span></span>

## <a name="installation"></a><span data-ttu-id="02fac-106">Instalacja programu</span><span class="sxs-lookup"><span data-stu-id="02fac-106">Installation</span></span>

<span data-ttu-id="02fac-107">Użyj natywnych instalatorów lub użyj skryptów powłoki instalacji:</span><span class="sxs-lookup"><span data-stu-id="02fac-107">Either use the native installers or use the installation shell scripts:</span></span>

- <span data-ttu-id="02fac-108">Natywne Instalatory są używane przede wszystkim na maszynach deweloperskich i używają natywnego mechanizmu instalacji na platformie, na przykład DEB pakiety w pakietach Ubuntu i MSI w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="02fac-108">The native installers are primarily used on developer's machines and use each supported platform's native install mechanism, for instance, DEB packages on Ubuntu or MSI bundles on Windows.</span></span> <span data-ttu-id="02fac-109">Te Instalatory instalują i konfigurują środowisko do natychmiastowego użytku przez dewelopera, ale wymagają uprawnień administracyjnych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="02fac-109">These installers install and configure the environment for immediate use by the developer but require administrative privileges on the machine.</span></span> <span data-ttu-id="02fac-110">Instrukcje dotyczące instalacji można wyświetlić w [podręczniku instalacji programu .NET Core](https://aka.ms/dotnetcoregs).</span><span class="sxs-lookup"><span data-stu-id="02fac-110">You can view the installation instructions in the [.NET Core installation guide](https://aka.ms/dotnetcoregs).</span></span>
- <span data-ttu-id="02fac-111">Skrypty powłoki są używane głównie do konfigurowania serwerów kompilacji lub do instalowania narzędzi bez uprawnień administracyjnych.</span><span class="sxs-lookup"><span data-stu-id="02fac-111">Shell scripts are primarily used for setting up build servers or when you wish to install the tools without administrative privileges.</span></span> <span data-ttu-id="02fac-112">Skrypty instalacji nie instalują wstępnie wymaganych składników na komputerze, które należy zainstalować ręcznie.</span><span class="sxs-lookup"><span data-stu-id="02fac-112">Install scripts don't install prerequisites on the machine, which must be installed manually.</span></span> <span data-ttu-id="02fac-113">Aby uzyskać więcej informacji, zobacz [temat informacje o skrypcie instalacji](dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="02fac-113">For more information, see the [install script reference topic](dotnet-install-script.md).</span></span> <span data-ttu-id="02fac-114">Aby uzyskać informacje na temat sposobu konfigurowania interfejsu wiersza polecenia na serwerze kompilacji ciągłej integracji (CI), zobacz [używanie zestaw .NET Core SDK i narzędzi w ciągłej integracji (ci)](using-ci-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="02fac-114">For information on how to set up CLI on your continuous integration (CI) build server, see [Using .NET Core SDK and tools in Continuous Integration (CI)](using-ci-with-cli.md).</span></span>

<span data-ttu-id="02fac-115">Domyślnie interfejs wiersza polecenia jest instalowany w sposób równoległy (SxS), dzięki czemu wiele wersji narzędzi interfejsu wiersza polecenia może współistnieć na jednej maszynie.</span><span class="sxs-lookup"><span data-stu-id="02fac-115">By default, the CLI installs in a side-by-side (SxS) manner, so multiple versions of the CLI tools can coexist on a single machine.</span></span> <span data-ttu-id="02fac-116">Określanie, która wersja jest używana na komputerze, na którym zainstalowano wiele wersji, wyjaśniono bardziej szczegółowo w sekcji [sterownika](#driver) .</span><span class="sxs-lookup"><span data-stu-id="02fac-116">Determining which version is used on a machine where multiple versions are installed is explained in more detail in the [Driver](#driver) section.</span></span>

## <a name="cli-commands"></a><span data-ttu-id="02fac-117">Poleceń interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="02fac-117">CLI commands</span></span>

<span data-ttu-id="02fac-118">Następujące polecenia są instalowane domyślnie:</span><span class="sxs-lookup"><span data-stu-id="02fac-118">The following commands are installed by default:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="02fac-119">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="02fac-119">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="02fac-120">**Polecenia podstawowe**</span><span class="sxs-lookup"><span data-stu-id="02fac-120">**Basic commands**</span></span>

- [<span data-ttu-id="02fac-121">new</span><span class="sxs-lookup"><span data-stu-id="02fac-121">new</span></span>](dotnet-new.md)
- [<span data-ttu-id="02fac-122">restore</span><span class="sxs-lookup"><span data-stu-id="02fac-122">restore</span></span>](dotnet-restore.md)
- [<span data-ttu-id="02fac-123">utworzenia</span><span class="sxs-lookup"><span data-stu-id="02fac-123">build</span></span>](dotnet-build.md)
- [<span data-ttu-id="02fac-124">publish</span><span class="sxs-lookup"><span data-stu-id="02fac-124">publish</span></span>](dotnet-publish.md)
- [<span data-ttu-id="02fac-125">run</span><span class="sxs-lookup"><span data-stu-id="02fac-125">run</span></span>](dotnet-run.md)
- [<span data-ttu-id="02fac-126">badan</span><span class="sxs-lookup"><span data-stu-id="02fac-126">test</span></span>](dotnet-test.md)
- [<span data-ttu-id="02fac-127">VSTest</span><span class="sxs-lookup"><span data-stu-id="02fac-127">vstest</span></span>](dotnet-vstest.md)
- [<span data-ttu-id="02fac-128">pakiet</span><span class="sxs-lookup"><span data-stu-id="02fac-128">pack</span></span>](dotnet-pack.md)
- [<span data-ttu-id="02fac-129">migrowanie</span><span class="sxs-lookup"><span data-stu-id="02fac-129">migrate</span></span>](dotnet-migrate.md)
- [<span data-ttu-id="02fac-130">czyst</span><span class="sxs-lookup"><span data-stu-id="02fac-130">clean</span></span>](dotnet-clean.md)
- [<span data-ttu-id="02fac-131">sln</span><span class="sxs-lookup"><span data-stu-id="02fac-131">sln</span></span>](dotnet-sln.md)
- [<span data-ttu-id="02fac-132">Pomoc</span><span class="sxs-lookup"><span data-stu-id="02fac-132">help</span></span>](dotnet-help.md)
- [<span data-ttu-id="02fac-133">zachować</span><span class="sxs-lookup"><span data-stu-id="02fac-133">store</span></span>](dotnet-store.md)

<span data-ttu-id="02fac-134">**Polecenia modyfikacji projektu**</span><span class="sxs-lookup"><span data-stu-id="02fac-134">**Project modification commands**</span></span>

- [<span data-ttu-id="02fac-135">Dodaj pakiet</span><span class="sxs-lookup"><span data-stu-id="02fac-135">add package</span></span>](dotnet-add-package.md)
- [<span data-ttu-id="02fac-136">Dodaj odwołanie</span><span class="sxs-lookup"><span data-stu-id="02fac-136">add reference</span></span>](dotnet-add-reference.md)
- [<span data-ttu-id="02fac-137">Usuń pakiet</span><span class="sxs-lookup"><span data-stu-id="02fac-137">remove package</span></span>](dotnet-remove-package.md)
- [<span data-ttu-id="02fac-138">Usuń odwołanie</span><span class="sxs-lookup"><span data-stu-id="02fac-138">remove reference</span></span>](dotnet-remove-reference.md)
- [<span data-ttu-id="02fac-139">odwołanie do listy</span><span class="sxs-lookup"><span data-stu-id="02fac-139">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="02fac-140">**Polecenia Zaawansowane**</span><span class="sxs-lookup"><span data-stu-id="02fac-140">**Advanced commands**</span></span>

- [<span data-ttu-id="02fac-141">Usuwanie NuGet</span><span class="sxs-lookup"><span data-stu-id="02fac-141">nuget delete</span></span>](dotnet-nuget-delete.md)
- [<span data-ttu-id="02fac-142">Ustawienia regionalne NuGet</span><span class="sxs-lookup"><span data-stu-id="02fac-142">nuget locals</span></span>](dotnet-nuget-locals.md)
- [<span data-ttu-id="02fac-143">wypychanie NuGet</span><span class="sxs-lookup"><span data-stu-id="02fac-143">nuget push</span></span>](dotnet-nuget-push.md)
- [<span data-ttu-id="02fac-144">msbuild</span><span class="sxs-lookup"><span data-stu-id="02fac-144">msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="02fac-145">skrypt instalacji dotnet</span><span class="sxs-lookup"><span data-stu-id="02fac-145">dotnet install script</span></span>](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="02fac-146">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="02fac-146">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="02fac-147">**Polecenia podstawowe**</span><span class="sxs-lookup"><span data-stu-id="02fac-147">**Basic commands**</span></span>

- [<span data-ttu-id="02fac-148">new</span><span class="sxs-lookup"><span data-stu-id="02fac-148">new</span></span>](dotnet-new.md)
- [<span data-ttu-id="02fac-149">restore</span><span class="sxs-lookup"><span data-stu-id="02fac-149">restore</span></span>](dotnet-restore.md)
- [<span data-ttu-id="02fac-150">utworzenia</span><span class="sxs-lookup"><span data-stu-id="02fac-150">build</span></span>](dotnet-build.md)
- [<span data-ttu-id="02fac-151">publish</span><span class="sxs-lookup"><span data-stu-id="02fac-151">publish</span></span>](dotnet-publish.md)
- [<span data-ttu-id="02fac-152">run</span><span class="sxs-lookup"><span data-stu-id="02fac-152">run</span></span>](dotnet-run.md)
- [<span data-ttu-id="02fac-153">badan</span><span class="sxs-lookup"><span data-stu-id="02fac-153">test</span></span>](dotnet-test.md)
- [<span data-ttu-id="02fac-154">VSTest</span><span class="sxs-lookup"><span data-stu-id="02fac-154">vstest</span></span>](dotnet-vstest.md)
- [<span data-ttu-id="02fac-155">pakiet</span><span class="sxs-lookup"><span data-stu-id="02fac-155">pack</span></span>](dotnet-pack.md)
- [<span data-ttu-id="02fac-156">migrowanie</span><span class="sxs-lookup"><span data-stu-id="02fac-156">migrate</span></span>](dotnet-migrate.md)
- [<span data-ttu-id="02fac-157">czyst</span><span class="sxs-lookup"><span data-stu-id="02fac-157">clean</span></span>](dotnet-clean.md)
- [<span data-ttu-id="02fac-158">sln</span><span class="sxs-lookup"><span data-stu-id="02fac-158">sln</span></span>](dotnet-sln.md)

<span data-ttu-id="02fac-159">**Polecenia modyfikacji projektu**</span><span class="sxs-lookup"><span data-stu-id="02fac-159">**Project modification commands**</span></span>

- [<span data-ttu-id="02fac-160">Dodaj pakiet</span><span class="sxs-lookup"><span data-stu-id="02fac-160">add package</span></span>](dotnet-add-package.md)
- [<span data-ttu-id="02fac-161">Dodaj odwołanie</span><span class="sxs-lookup"><span data-stu-id="02fac-161">add reference</span></span>](dotnet-add-reference.md)
- [<span data-ttu-id="02fac-162">Usuń pakiet</span><span class="sxs-lookup"><span data-stu-id="02fac-162">remove package</span></span>](dotnet-remove-package.md)
- [<span data-ttu-id="02fac-163">Usuń odwołanie</span><span class="sxs-lookup"><span data-stu-id="02fac-163">remove reference</span></span>](dotnet-remove-reference.md)
- [<span data-ttu-id="02fac-164">odwołanie do listy</span><span class="sxs-lookup"><span data-stu-id="02fac-164">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="02fac-165">**Polecenia Zaawansowane**</span><span class="sxs-lookup"><span data-stu-id="02fac-165">**Advanced commands**</span></span>

- [<span data-ttu-id="02fac-166">Usuwanie NuGet</span><span class="sxs-lookup"><span data-stu-id="02fac-166">nuget delete</span></span>](dotnet-nuget-delete.md)
- [<span data-ttu-id="02fac-167">Ustawienia regionalne NuGet</span><span class="sxs-lookup"><span data-stu-id="02fac-167">nuget locals</span></span>](dotnet-nuget-locals.md)
- [<span data-ttu-id="02fac-168">wypychanie NuGet</span><span class="sxs-lookup"><span data-stu-id="02fac-168">nuget push</span></span>](dotnet-nuget-push.md)
- [<span data-ttu-id="02fac-169">msbuild</span><span class="sxs-lookup"><span data-stu-id="02fac-169">msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="02fac-170">skrypt instalacji dotnet</span><span class="sxs-lookup"><span data-stu-id="02fac-170">dotnet install script</span></span>](dotnet-install-script.md)

---

<span data-ttu-id="02fac-171">Interfejs wiersza polecenia przyjmuje model rozszerzalności, który pozwala określić dodatkowe narzędzia dla projektów.</span><span class="sxs-lookup"><span data-stu-id="02fac-171">The CLI adopts an extensibility model that allows you to specify additional tools for your projects.</span></span> <span data-ttu-id="02fac-172">Aby uzyskać więcej informacji, zobacz temat dotyczący [modelu rozszerzalności interfejs wiersza polecenia platformy .NET Core](extensibility.md) .</span><span class="sxs-lookup"><span data-stu-id="02fac-172">For more information, see the [.NET Core CLI extensibility model](extensibility.md) topic.</span></span>

## <a name="command-structure"></a><span data-ttu-id="02fac-173">Struktura poleceń</span><span class="sxs-lookup"><span data-stu-id="02fac-173">Command structure</span></span>

<span data-ttu-id="02fac-174">Struktura poleceń interfejsu wiersza polecenia składa się ze [sterownika ("dotnet")](#driver), [polecenia](#command)oraz możliwych [argumentów](#arguments) i [opcji](#options)polecenia.</span><span class="sxs-lookup"><span data-stu-id="02fac-174">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="02fac-175">Ten wzorzec jest widoczny w większości operacji interfejsu wiersza polecenia, takich jak tworzenie nowej aplikacji konsolowej i uruchamianie jej z poziomu wiersza poleceń, ponieważ następujące polecenia pokazują, że są wykonywane z katalogu o nazwie *my_app*:</span><span class="sxs-lookup"><span data-stu-id="02fac-175">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="02fac-176">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="02fac-176">.NET Core 2.x</span></span>](#tab/netcore2x)

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="02fac-177">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="02fac-177">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

---

### <a name="driver"></a><span data-ttu-id="02fac-178">Sterownik</span><span class="sxs-lookup"><span data-stu-id="02fac-178">Driver</span></span>

<span data-ttu-id="02fac-179">Sterownik nosi nazwę [dotnet](dotnet.md) i ma dwie obowiązki, uruchamiają [aplikację zależną od platformy](../deploying/index.md) lub wykonując polecenie.</span><span class="sxs-lookup"><span data-stu-id="02fac-179">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span> 

<span data-ttu-id="02fac-180">Aby uruchomić aplikację zależną od platformy, należy określić aplikację po sterowniku, na przykład `dotnet /path/to/my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="02fac-180">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="02fac-181">Podczas wykonywania polecenia z folderu, w którym znajduje się biblioteka DLL aplikacji, wystarczy wykonać `dotnet my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="02fac-181">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="02fac-182">Jeśli chcesz użyć określonej wersji środowiska uruchomieniowego platformy .NET Core, użyj opcji `--fx-version <VERSION>` (zobacz informacje dotyczące [polecenia dotnet](dotnet.md) ).</span><span class="sxs-lookup"><span data-stu-id="02fac-182">If you want to use a specific version of the .NET Core Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="02fac-183">Gdy podasz polecenie do sterownika, `dotnet.exe` uruchamia proces wykonywania polecenia interfejsu CLI.</span><span class="sxs-lookup"><span data-stu-id="02fac-183">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="02fac-184">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="02fac-184">For example:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="02fac-185">Najpierw sterownik Określa wersję zestawu SDK do użycia.</span><span class="sxs-lookup"><span data-stu-id="02fac-185">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="02fac-186">Jeśli nie ma pliku ["Global. JSON"](global-json.md), używana jest Najnowsza wersja zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="02fac-186">If there is no ['global.json'](global-json.md), the latest version of the SDK available is used.</span></span> <span data-ttu-id="02fac-187">Może to być wersja zapoznawcza lub stabilna, w zależności od tego, co jest najnowsze na komputerze.</span><span class="sxs-lookup"><span data-stu-id="02fac-187">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="02fac-188">Po ustaleniu wersji zestawu SDK wykonuje polecenie.</span><span class="sxs-lookup"><span data-stu-id="02fac-188">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="02fac-189">Polecenie</span><span class="sxs-lookup"><span data-stu-id="02fac-189">Command</span></span>

<span data-ttu-id="02fac-190">Polecenie wykonuje akcję.</span><span class="sxs-lookup"><span data-stu-id="02fac-190">The command performs an action.</span></span> <span data-ttu-id="02fac-191">Na przykład `dotnet build` kompiluje kod.</span><span class="sxs-lookup"><span data-stu-id="02fac-191">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="02fac-192">`dotnet publish` publikuje kod.</span><span class="sxs-lookup"><span data-stu-id="02fac-192">`dotnet publish` publishes code.</span></span> <span data-ttu-id="02fac-193">Polecenia są implementowane jako Aplikacja konsolowa przy użyciu konwencji `dotnet {command}`.</span><span class="sxs-lookup"><span data-stu-id="02fac-193">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="02fac-194">Argumenty</span><span class="sxs-lookup"><span data-stu-id="02fac-194">Arguments</span></span>

<span data-ttu-id="02fac-195">Argumenty przekazywane do wiersza polecenia są argumentami wywoływanego polecenia.</span><span class="sxs-lookup"><span data-stu-id="02fac-195">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="02fac-196">Na przykład podczas wykonywania `dotnet publish my_app.csproj`argument `my_app.csproj` wskazuje projekt do opublikowania i jest przesyłany do polecenia `publish`.</span><span class="sxs-lookup"><span data-stu-id="02fac-196">For example when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="02fac-197">Opcje</span><span class="sxs-lookup"><span data-stu-id="02fac-197">Options</span></span>

<span data-ttu-id="02fac-198">Opcje, które są przekazywane w wierszu polecenia są opcje wywoływanego polecenia.</span><span class="sxs-lookup"><span data-stu-id="02fac-198">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="02fac-199">Na przykład podczas wykonywania `dotnet publish --output /build_output`opcja `--output` i jej wartość są przesyłane do polecenia `publish`.</span><span class="sxs-lookup"><span data-stu-id="02fac-199">For example when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="migration-from-projectjson"></a><span data-ttu-id="02fac-200">Migracja z pliku Project. JSON</span><span class="sxs-lookup"><span data-stu-id="02fac-200">Migration from project.json</span></span>

<span data-ttu-id="02fac-201">Jeśli użyto narzędzi w wersji zapoznawczej 2 do tworzenia projektów opartych na pliku *Project. JSON*, zapoznaj się z tematem Migrowanie środowiska [dotnet](dotnet-migrate.md) , aby uzyskać informacje na temat migrowania projektu do programu MSBuild/ *. csproj* do użytku z narzędziami Release.</span><span class="sxs-lookup"><span data-stu-id="02fac-201">If you used Preview 2 tooling to produce *project.json*-based projects, consult the [dotnet migrate](dotnet-migrate.md) topic for information on migrating your project to MSBuild/*.csproj* for use with release tooling.</span></span> <span data-ttu-id="02fac-202">W przypadku projektów .NET Core utworzonych przed udostępnieniem narzędzi wersji zapoznawczej 2 należy ręcznie zaktualizować projekt zgodnie ze wskazówkami zawartymi w sekcji [Migrowanie z środowiska DNX do interfejs wiersza polecenia platformy .NET Core (Project. JSON)](../migration/from-dnx.md) , a następnie użyć `dotnet migrate` lub bezpośrednio uaktualnić projekty.</span><span class="sxs-lookup"><span data-stu-id="02fac-202">For .NET Core projects created prior to the release of Preview 2 tooling, either manually update the project following the guidance in [Migrating from DNX to .NET Core CLI (project.json)](../migration/from-dnx.md) and then use `dotnet migrate` or directly upgrade your projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="02fac-203">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="02fac-203">See also</span></span>

- [<span data-ttu-id="02fac-204">Repozytorium dotnet/CLI usługi GitHub</span><span class="sxs-lookup"><span data-stu-id="02fac-204">dotnet/CLI GitHub Repository</span></span>](https://github.com/dotnet/cli/)
- [<span data-ttu-id="02fac-205">Przewodnik instalacji programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="02fac-205">.NET Core installation guide</span></span>](https://aka.ms/dotnetcoregs)
