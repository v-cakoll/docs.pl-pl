---
title: "Narzędzia programu .NET core interfejsu wiersza polecenia (CLI)"
description: "Przegląd funkcji i narzędzi .NET Core interfejsu wiersza polecenia (CLI)."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 0f43f569cdb8b9e4be68b61ba7b5cc4686fdb871
ms.sourcegitcommit: 9bee08539b1886c9d57fa3d5bd8a58dfdd7cad94
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2017
---
# <a name="net-core-command-line-interface-cli-tools"></a><span data-ttu-id="d8611-103">Oprogramowanie .NET core narzędzi interfejsu wiersza polecenia (CLI)</span><span class="sxs-lookup"><span data-stu-id="d8611-103">.NET Core command-line interface (CLI) tools</span></span>

<span data-ttu-id="d8611-104">Oprogramowanie .NET Core interfejsu wiersza polecenia (CLI) jest nowy łańcuch między platformami narzędzi do tworzenia aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="d8611-104">The .NET Core command-line interface (CLI) is a new cross-platform toolchain for developing .NET applications.</span></span> <span data-ttu-id="d8611-105">Interfejsu wiersza polecenia jest foundation na narzędzia wyższego poziomu, takie jak zintegrowane środowisk deweloperskich (IDE), edytory i orchestrators kompilacji można rest.</span><span class="sxs-lookup"><span data-stu-id="d8611-105">The CLI is a foundation upon which higher-level tools, such as Integrated Development Environments (IDEs), editors, and build orchestrators, can rest.</span></span>

## <a name="installation"></a><span data-ttu-id="d8611-106">Instalacja</span><span class="sxs-lookup"><span data-stu-id="d8611-106">Installation</span></span>

<span data-ttu-id="d8611-107">Użyj natywnego instalatorów lub korzystać ze skryptów powłoki instalacji:</span><span class="sxs-lookup"><span data-stu-id="d8611-107">Either use the native installers or use the installation shell scripts:</span></span>

* <span data-ttu-id="d8611-108">Natywnego pliki instalacyjne są używane przede wszystkim na komputerach deweloperów i natywnego za każdym obsługiwane platformy Zainstaluj mechanizm, na przykład DEB pakietów na funkcji MSI lub Ubuntu pakietów w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="d8611-108">The native installers are primarily used on developer's machines and use each supported platform's native install mechanism, for instance, DEB packages on Ubuntu or MSI bundles on Windows.</span></span> <span data-ttu-id="d8611-109">Te pliki instalacyjne zainstalować i skonfigurować środowisko do użycia przez dewelopera, ale wymagają uprawnień administratora na komputerze.</span><span class="sxs-lookup"><span data-stu-id="d8611-109">These installers install and configure the environment for immediate use by the developer but require administrative privileges on the machine.</span></span> <span data-ttu-id="d8611-110">Można wyświetlić w instrukcjach dotyczących instalacji w [Przewodnik instalacji platformy .NET Core](https://aka.ms/dotnetcoregs).</span><span class="sxs-lookup"><span data-stu-id="d8611-110">You can view the installation instructions in the [.NET Core installation guide](https://aka.ms/dotnetcoregs).</span></span>
* <span data-ttu-id="d8611-111">Skryptów powłoki są używane przede wszystkim dotyczące konfigurowania serwery kompilacji lub gdy chcesz zainstalować narzędzia bez uprawnień administracyjnych.</span><span class="sxs-lookup"><span data-stu-id="d8611-111">Shell scripts are primarily used for setting up build servers or when you wish to install the tools without administrative privileges.</span></span> <span data-ttu-id="d8611-112">Zainstaluj skrypty wymagania wstępne nie należy instalować na komputerze, który należy zainstalować ręcznie.</span><span class="sxs-lookup"><span data-stu-id="d8611-112">Install scripts don't install prerequisites on the machine, which must be installed manually.</span></span> <span data-ttu-id="d8611-113">Aby uzyskać więcej informacji, zobacz [zainstalować temat referencyjny skryptu](dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="d8611-113">For more information, see the [install script reference topic](dotnet-install-script.md).</span></span> <span data-ttu-id="d8611-114">Aby uzyskać informacje na temat Konfigurowanie interfejsu wiersza polecenia na serwerze kompilacji ciągłej integracji (CI), zobacz [przy użyciu programu .NET Core SDK i narzędzia w ciągłej integracji (CI)](using-ci-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="d8611-114">For information on how to set up CLI on your continuous integration (CI) build server, see [Using .NET Core SDK and tools in Continuous Integration (CI)](using-ci-with-cli.md).</span></span>

<span data-ttu-id="d8611-115">Domyślnie interfejsu wiersza polecenia instalacji w sposób side-by-side (SxS) tak wielu wersji narzędzi interfejsu wiersza polecenia mogą współistnieć na jednym komputerze.</span><span class="sxs-lookup"><span data-stu-id="d8611-115">By default, the CLI installs in a side-by-side (SxS) manner, so multiple versions of the CLI tools can coexist on a single machine.</span></span> <span data-ttu-id="d8611-116">Określanie, która wersja jest używana na komputerze, którym zainstalowano kilka wersji to co omówiono bardziej szczegółowo w [sterownika](#driver) sekcji.</span><span class="sxs-lookup"><span data-stu-id="d8611-116">Determining which version is used on a machine where multiple versions are installed is explained in more detail in the [Driver](#driver) section.</span></span>

## <a name="cli-commands"></a><span data-ttu-id="d8611-117">Polecenia interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="d8611-117">CLI commands</span></span>

<span data-ttu-id="d8611-118">Domyślnie instalowane są następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="d8611-118">The following commands are installed by default:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d8611-119">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="d8611-119">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="d8611-120">**Podstawowe polecenia**</span><span class="sxs-lookup"><span data-stu-id="d8611-120">**Basic commands**</span></span>

* [<span data-ttu-id="d8611-121">new</span><span class="sxs-lookup"><span data-stu-id="d8611-121">new</span></span>](dotnet-new.md)
* [<span data-ttu-id="d8611-122">Przywracanie</span><span class="sxs-lookup"><span data-stu-id="d8611-122">restore</span></span>](dotnet-restore.md)
* [<span data-ttu-id="d8611-123">kompilacji</span><span class="sxs-lookup"><span data-stu-id="d8611-123">build</span></span>](dotnet-build.md)
* [<span data-ttu-id="d8611-124">Publikowanie</span><span class="sxs-lookup"><span data-stu-id="d8611-124">publish</span></span>](dotnet-publish.md)
* [<span data-ttu-id="d8611-125">Uruchom</span><span class="sxs-lookup"><span data-stu-id="d8611-125">run</span></span>](dotnet-run.md)
* [<span data-ttu-id="d8611-126">Test</span><span class="sxs-lookup"><span data-stu-id="d8611-126">test</span></span>](dotnet-test.md)
* [<span data-ttu-id="d8611-127">vstest</span><span class="sxs-lookup"><span data-stu-id="d8611-127">vstest</span></span>](dotnet-vstest.md)
* [<span data-ttu-id="d8611-128">pakiet</span><span class="sxs-lookup"><span data-stu-id="d8611-128">pack</span></span>](dotnet-pack.md)
* [<span data-ttu-id="d8611-129">Migracja</span><span class="sxs-lookup"><span data-stu-id="d8611-129">migrate</span></span>](dotnet-migrate.md)
* [<span data-ttu-id="d8611-130">czyszczenie</span><span class="sxs-lookup"><span data-stu-id="d8611-130">clean</span></span>](dotnet-clean.md)
* [<span data-ttu-id="d8611-131">SLN</span><span class="sxs-lookup"><span data-stu-id="d8611-131">sln</span></span>](dotnet-sln.md)
* [<span data-ttu-id="d8611-132">Pomoc</span><span class="sxs-lookup"><span data-stu-id="d8611-132">help</span></span>](dotnet-help.md)
* [<span data-ttu-id="d8611-133">Magazyn</span><span class="sxs-lookup"><span data-stu-id="d8611-133">store</span></span>](dotnet-store.md)

<span data-ttu-id="d8611-134">**Polecenia modyfikacji projektu**</span><span class="sxs-lookup"><span data-stu-id="d8611-134">**Project modification commands**</span></span>

* [<span data-ttu-id="d8611-135">Dodaj pakiet</span><span class="sxs-lookup"><span data-stu-id="d8611-135">add package</span></span>](dotnet-add-package.md)
* [<span data-ttu-id="d8611-136">Dodaj odwołanie</span><span class="sxs-lookup"><span data-stu-id="d8611-136">add reference</span></span>](dotnet-add-reference.md)
* [<span data-ttu-id="d8611-137">Usunięcie pakietu</span><span class="sxs-lookup"><span data-stu-id="d8611-137">remove package</span></span>](dotnet-remove-package.md)
* [<span data-ttu-id="d8611-138">Usuwanie odwołań</span><span class="sxs-lookup"><span data-stu-id="d8611-138">remove reference</span></span>](dotnet-remove-reference.md)
* [<span data-ttu-id="d8611-139">Odwołanie do listy</span><span class="sxs-lookup"><span data-stu-id="d8611-139">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="d8611-140">**Zaawansowane poleceń**</span><span class="sxs-lookup"><span data-stu-id="d8611-140">**Advanced commands**</span></span>

* [<span data-ttu-id="d8611-141">Usuń nuget</span><span class="sxs-lookup"><span data-stu-id="d8611-141">nuget delete</span></span>](dotnet-nuget-delete.md)
* [<span data-ttu-id="d8611-142">Zmienne lokalne nuget</span><span class="sxs-lookup"><span data-stu-id="d8611-142">nuget locals</span></span>](dotnet-nuget-locals.md)
* [<span data-ttu-id="d8611-143">wypychania nuget</span><span class="sxs-lookup"><span data-stu-id="d8611-143">nuget push</span></span>](dotnet-nuget-push.md)
* [<span data-ttu-id="d8611-144">MSBUILD</span><span class="sxs-lookup"><span data-stu-id="d8611-144">msbuild</span></span>](dotnet-msbuild.md)
* [<span data-ttu-id="d8611-145">skrypt instalacji DotNet</span><span class="sxs-lookup"><span data-stu-id="d8611-145">dotnet install script</span></span>](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d8611-146">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="d8611-146">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="d8611-147">**Podstawowe polecenia**</span><span class="sxs-lookup"><span data-stu-id="d8611-147">**Basic commands**</span></span>

* [<span data-ttu-id="d8611-148">new</span><span class="sxs-lookup"><span data-stu-id="d8611-148">new</span></span>](dotnet-new.md)
* [<span data-ttu-id="d8611-149">Przywracanie</span><span class="sxs-lookup"><span data-stu-id="d8611-149">restore</span></span>](dotnet-restore.md)
* [<span data-ttu-id="d8611-150">kompilacji</span><span class="sxs-lookup"><span data-stu-id="d8611-150">build</span></span>](dotnet-build.md)
* [<span data-ttu-id="d8611-151">Publikowanie</span><span class="sxs-lookup"><span data-stu-id="d8611-151">publish</span></span>](dotnet-publish.md)
* [<span data-ttu-id="d8611-152">Uruchom</span><span class="sxs-lookup"><span data-stu-id="d8611-152">run</span></span>](dotnet-run.md)
* [<span data-ttu-id="d8611-153">Test</span><span class="sxs-lookup"><span data-stu-id="d8611-153">test</span></span>](dotnet-test.md)
* [<span data-ttu-id="d8611-154">vstest</span><span class="sxs-lookup"><span data-stu-id="d8611-154">vstest</span></span>](dotnet-vstest.md)
* [<span data-ttu-id="d8611-155">pakiet</span><span class="sxs-lookup"><span data-stu-id="d8611-155">pack</span></span>](dotnet-pack.md)
* [<span data-ttu-id="d8611-156">Migracja</span><span class="sxs-lookup"><span data-stu-id="d8611-156">migrate</span></span>](dotnet-migrate.md)
* [<span data-ttu-id="d8611-157">czyszczenie</span><span class="sxs-lookup"><span data-stu-id="d8611-157">clean</span></span>](dotnet-clean.md)
* [<span data-ttu-id="d8611-158">SLN</span><span class="sxs-lookup"><span data-stu-id="d8611-158">sln</span></span>](dotnet-sln.md)

<span data-ttu-id="d8611-159">**Polecenia modyfikacji projektu**</span><span class="sxs-lookup"><span data-stu-id="d8611-159">**Project modification commands**</span></span>

* [<span data-ttu-id="d8611-160">Dodaj pakiet</span><span class="sxs-lookup"><span data-stu-id="d8611-160">add package</span></span>](dotnet-add-package.md)
* [<span data-ttu-id="d8611-161">Dodaj odwołanie</span><span class="sxs-lookup"><span data-stu-id="d8611-161">add reference</span></span>](dotnet-add-reference.md)
* [<span data-ttu-id="d8611-162">Usunięcie pakietu</span><span class="sxs-lookup"><span data-stu-id="d8611-162">remove package</span></span>](dotnet-remove-package.md)
* [<span data-ttu-id="d8611-163">Usuwanie odwołań</span><span class="sxs-lookup"><span data-stu-id="d8611-163">remove reference</span></span>](dotnet-remove-reference.md)
* [<span data-ttu-id="d8611-164">Odwołanie do listy</span><span class="sxs-lookup"><span data-stu-id="d8611-164">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="d8611-165">**Zaawansowane poleceń**</span><span class="sxs-lookup"><span data-stu-id="d8611-165">**Advanced commands**</span></span>

* [<span data-ttu-id="d8611-166">Usuń nuget</span><span class="sxs-lookup"><span data-stu-id="d8611-166">nuget delete</span></span>](dotnet-nuget-delete.md)
* [<span data-ttu-id="d8611-167">Zmienne lokalne nuget</span><span class="sxs-lookup"><span data-stu-id="d8611-167">nuget locals</span></span>](dotnet-nuget-locals.md)
* [<span data-ttu-id="d8611-168">wypychania nuget</span><span class="sxs-lookup"><span data-stu-id="d8611-168">nuget push</span></span>](dotnet-nuget-push.md)
* [<span data-ttu-id="d8611-169">MSBUILD</span><span class="sxs-lookup"><span data-stu-id="d8611-169">msbuild</span></span>](dotnet-msbuild.md)
* [<span data-ttu-id="d8611-170">skrypt instalacji DotNet</span><span class="sxs-lookup"><span data-stu-id="d8611-170">dotnet install script</span></span>](dotnet-install-script.md)

---

<span data-ttu-id="d8611-171">Interfejsu wiersza polecenia przyjmuje modelu rozszerzalności, która pozwala na określenie dodatkowych narzędzi dla projektów.</span><span class="sxs-lookup"><span data-stu-id="d8611-171">The CLI adopts an extensibility model that allows you to specify additional tools for your projects.</span></span> <span data-ttu-id="d8611-172">Aby uzyskać więcej informacji, zobacz [modelu rozszerzalności interfejsu wiersza polecenia platformy .NET Core](extensibility.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="d8611-172">For more information, see the [.NET Core CLI extensibility model](extensibility.md) topic.</span></span>

## <a name="command-structure"></a><span data-ttu-id="d8611-173">Polecenie — struktura</span><span class="sxs-lookup"><span data-stu-id="d8611-173">Command structure</span></span>

<span data-ttu-id="d8611-174">Struktura polecenia interfejsu wiersza polecenia składa się z [sterownika ("dotnet")](#driver), [polecenia (lub "zlecenie")](#command-verb)oraz prawdopodobnie poleceń [argumenty](#arguments) i [opcje](#options).</span><span class="sxs-lookup"><span data-stu-id="d8611-174">CLI command structure consists of the [the driver ("dotnet")](#driver), [the command (or "verb")](#command-verb), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="d8611-175">Zobacz tego wzorca w większości operacji interfejsu wiersza polecenia, takie jak tworzenie nowej aplikacji konsoli i uruchomiony z wiersza polecenia jako następujące polecenia, Pokaż podczas wykonywania z katalogu o nazwie *moja_aplikacja*:</span><span class="sxs-lookup"><span data-stu-id="d8611-175">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d8611-176">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="d8611-176">.NET Core 2.x</span></span>](#tab/netcore2x)

```console
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d8611-177">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="d8611-177">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```


---

### <a name="driver"></a><span data-ttu-id="d8611-178">Sterownik</span><span class="sxs-lookup"><span data-stu-id="d8611-178">Driver</span></span>

<span data-ttu-id="d8611-179">O nazwie sterownik [dotnet](dotnet.md) i ma dwa obowiązki, każda uruchomiona [aplikacji zależnych od framework](../deploying/index.md) lub wykonywania polecenia.</span><span class="sxs-lookup"><span data-stu-id="d8611-179">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span> <span data-ttu-id="d8611-180">Tylko `dotnet` jest używana bez jest polecenie, gdy jest używany do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d8611-180">The only time `dotnet` is used without a command is when it's used to start an application.</span></span>

<span data-ttu-id="d8611-181">Uruchamianie aplikacji zależnych od framework, należy określić aplikację po sterowników, na przykład `dotnet /path/to/my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="d8611-181">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="d8611-182">Podczas wykonywania polecenia z folderu, w którym znajduje się aplikacji DLL, po prostu wykonać `dotnet my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="d8611-182">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span>

<span data-ttu-id="d8611-183">Jeśli podasz polecenia do sterownika, `dotnet.exe` rozpoczyna się proces wykonywania polecenia interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="d8611-183">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="d8611-184">Po pierwsze sterownika Określa wersję zestawu SDK do użycia.</span><span class="sxs-lookup"><span data-stu-id="d8611-184">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="d8611-185">Jeśli wersja nie jest określona w opcji polecenia, sterownik używa najnowszej dostępnej wersji.</span><span class="sxs-lookup"><span data-stu-id="d8611-185">If the version isn't specified in the command options, the driver uses the latest version available.</span></span> <span data-ttu-id="d8611-186">Aby określić wersję niż najnowszej zainstalowanej wersji, użyj `--fx-version <VERSION>` opcji (zobacz [polecenia dotnet](dotnet.md) odwołania).</span><span class="sxs-lookup"><span data-stu-id="d8611-186">To specify a version other than the latest installed version, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span> <span data-ttu-id="d8611-187">Po określeniu zestawu SDK w wersji sterownika wykonuje polecenie.</span><span class="sxs-lookup"><span data-stu-id="d8611-187">Once the SDK version is determined, the driver executes the command.</span></span>

### <a name="command-verb"></a><span data-ttu-id="d8611-188">Polecenie ("zlecenie")</span><span class="sxs-lookup"><span data-stu-id="d8611-188">Command ("verb")</span></span>

<span data-ttu-id="d8611-189">Polecenie (lub "zlecenie") jest po prostu polecenie, które wykonuje akcję.</span><span class="sxs-lookup"><span data-stu-id="d8611-189">The command (or "verb") is simply a command that performs an action.</span></span> <span data-ttu-id="d8611-190">Na przykład `dotnet build` kompilacji kodu.</span><span class="sxs-lookup"><span data-stu-id="d8611-190">For example, `dotnet build` builds your code.</span></span> <span data-ttu-id="d8611-191">`dotnet publish`publikuje kodu.</span><span class="sxs-lookup"><span data-stu-id="d8611-191">`dotnet publish` publishes your code.</span></span> <span data-ttu-id="d8611-192">Polecenia są zaimplementowane jako aplikacji konsoli przy użyciu `dotnet {verb}` Konwencji.</span><span class="sxs-lookup"><span data-stu-id="d8611-192">The commands are implemented as a console application using a `dotnet {verb}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="d8611-193">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d8611-193">Arguments</span></span>

<span data-ttu-id="d8611-194">Argumenty przekazywane w wierszu polecenia są argumenty polecenia wywoływane.</span><span class="sxs-lookup"><span data-stu-id="d8611-194">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="d8611-195">Na przykład podczas wykonywania `dotnet publish my_app.csproj`, `my_app.csproj` argument wskazuje projektu do publikowania i jest przekazywana do `publish` polecenia.</span><span class="sxs-lookup"><span data-stu-id="d8611-195">For example when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="d8611-196">Opcje</span><span class="sxs-lookup"><span data-stu-id="d8611-196">Options</span></span>

<span data-ttu-id="d8611-197">Opcje do polecenia wywoływane są opcje przebiegu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="d8611-197">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="d8611-198">Na przykład podczas wykonywania `dotnet publish --output /build_output`, `--output` opcji i jej wartość są przekazywane do `publish` polecenia.</span><span class="sxs-lookup"><span data-stu-id="d8611-198">For example when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span> 

## <a name="migration-from-projectjson"></a><span data-ttu-id="d8611-199">Migracja z pliku project.json</span><span class="sxs-lookup"><span data-stu-id="d8611-199">Migration from project.json</span></span>

<span data-ttu-id="d8611-200">Jeśli używana wersja zapoznawcza 2 narzędzi do tworzenia *project.json*— na podstawie projektów, zapoznaj się [migracji dotnet](dotnet-migrate.md) tematu zawiera informacje na temat migracji projektu do MSBuild /*.csproj*do użytku z wersji narzędzi.</span><span class="sxs-lookup"><span data-stu-id="d8611-200">If you used Preview 2 tooling to produce *project.json*-based projects, consult the [dotnet migrate](dotnet-migrate.md) topic for information on migrating your project to MSBuild/*.csproj* for use with release tooling.</span></span> <span data-ttu-id="d8611-201">Dla platformy .NET Core projektów utworzonych przed wydaniem narzędzi Preview 2 ręcznie zaktualizować projektu, postępując zgodnie ze wskazówkami w [migracji ze środowiska DNX .NET Core interfejsu wiersza polecenia (project.json)](../migration/from-dnx.md) , a następnie użyj `dotnet migrate` lub bezpośrednio uaktualnienia projekty.</span><span class="sxs-lookup"><span data-stu-id="d8611-201">For .NET Core projects created prior to the release of Preview 2 tooling, either manually update the project following the guidance in [Migrating from DNX to .NET Core CLI (project.json)](../migration/from-dnx.md) and then use `dotnet migrate` or directly upgrade your projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8611-202">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d8611-202">See also</span></span>

 [<span data-ttu-id="d8611-203">DotNet/CLI repozytorium GitHub</span><span class="sxs-lookup"><span data-stu-id="d8611-203">dotnet/CLI GitHub Repository</span></span>](https://github.com/dotnet/cli/)  
 [<span data-ttu-id="d8611-204">Przewodnik instalacji platformy .NET core</span><span class="sxs-lookup"><span data-stu-id="d8611-204">.NET Core installation guide</span></span>](https://aka.ms/dotnetcoregs)  
