---
title: Co to jest nowa w programie .NET Core 2.1
description: Więcej informacji na temat nowych funkcji .NET Core 2.1.
author: rpetrusha
ms.author: ronpet
ms.date: 06/06/2018
ms.openlocfilehash: 241ac0195e5edcd17ac67ea7ea0fac159af97414
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34826935"
---
# <a name="whats-new-in-net-core-21"></a><span data-ttu-id="bcbd6-103">Co to jest nowa w programie .NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="bcbd6-103">What's new in .NET Core 2.1</span></span>

<span data-ttu-id="bcbd6-104">.NET core 2.1 zawiera nowych funkcji i rozszerzeń w następujących obszarach:</span><span class="sxs-lookup"><span data-stu-id="bcbd6-104">.NET Core 2.1 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="bcbd6-105">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="bcbd6-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="bcbd6-106">Przenoszenia do przodu</span><span class="sxs-lookup"><span data-stu-id="bcbd6-106">Roll forward</span></span>](#roll-forward)
- [<span data-ttu-id="bcbd6-107">Wdrażanie</span><span class="sxs-lookup"><span data-stu-id="bcbd6-107">Deployment</span></span>](#deployment)
- [<span data-ttu-id="bcbd6-108">Pakiet zgodności systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bcbd6-108">Windows Compatibility Pack</span></span>](#windows-compatibility-pack)
- [<span data-ttu-id="bcbd6-109">Ulepszenia kompilacji JIT</span><span class="sxs-lookup"><span data-stu-id="bcbd6-109">JIT compilation improvements</span></span>](#jit-compiler-improvements)
- [<span data-ttu-id="bcbd6-110">Zmiany interfejsu API</span><span class="sxs-lookup"><span data-stu-id="bcbd6-110">API changes</span></span>](#api-changes)

## <a name="tooling"></a><span data-ttu-id="bcbd6-111">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="bcbd6-111">Tooling</span></span>

<span data-ttu-id="bcbd6-112">.NET Core 2.1 zestaw SDK (v 2.1.300), narzędzi dołączonego .NET Core 2.1 zawiera następujące zmiany i udoskonalenia:</span><span class="sxs-lookup"><span data-stu-id="bcbd6-112">The .NET Core 2.1 SDK (v 2.1.300), the tooling included with .NET Core 2.1, includes the following changes and enhancements:</span></span>

### <a name="build-performance-improvements"></a><span data-ttu-id="bcbd6-113">Ulepszenia wydajności kompilacji</span><span class="sxs-lookup"><span data-stu-id="bcbd6-113">Build performance improvements</span></span>

<span data-ttu-id="bcbd6-114">Głównym celem .NET Core 2.1 jest poprawy wydajności w czasie kompilacji, szczególnie dla kompilacji przyrostowej.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-114">A major focus of .NET Core 2.1 is improving build-time performance, particularly for incremental builds.</span></span> <span data-ttu-id="bcbd6-115">Te ulepszenia wydajności dotyczą zarówno kompilacji z wiersza polecenia przy użyciu `dotnet build` i kompilacji w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-115">These performance improvements apply to both command-line builds using `dotnet build` and to builds in Visual Studio.</span></span> <span data-ttu-id="bcbd6-116">Niektóre poszczególnych obszarach poprawy obejmują:</span><span class="sxs-lookup"><span data-stu-id="bcbd6-116">Some individual areas of improvement include:</span></span>

- <span data-ttu-id="bcbd6-117">Rozpoznanie zasobów pakietu rozpoznawanie tylko zasoby używane przez kompilację, a nie wszystkie zasoby.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-117">For package asset resolution, resolving only assets used by a build rather than all assets.</span></span>

- <span data-ttu-id="bcbd6-118">Buforowanie odwołania do zestawów.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-118">Caching of assembly references.</span></span>

- <span data-ttu-id="bcbd6-119">Użyj zestawu SDK długotrwałe kompilacji z serwerów, które są procesów obejmujących przez poszczególne `dotnet build` wywołań.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-119">Use of long-running SDK build servers, which are processes that span across individual `dotnet build` invocations.</span></span> <span data-ttu-id="bcbd6-120">One wyeliminować potrzebę kompilacji JIT duże bloki kodu zawsze `dotnet build` jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-120">They eliminate the need to JIT-compile large blocks of code every time `dotnet build` is run.</span></span> <span data-ttu-id="bcbd6-121">Tworzenie serwera, które mogą być automatycznie zakończone procesy przy użyciu następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="bcbd6-121">Build server processes can be automatically terminated with the following command:</span></span>

   ```console
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a><span data-ttu-id="bcbd6-122">Nowe polecenia interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="bcbd6-122">New CLI commands</span></span>

<span data-ttu-id="bcbd6-123">Liczba narzędzia, które były dostępne tylko na projekt na podstawie przy użyciu [ `DotnetCliToolReference` ](../tools/extensibility.md) są teraz dostępne jako część zestawu SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-123">A number of tools that were available only on a per project basis using [`DotnetCliToolReference`](../tools/extensibility.md) are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="bcbd6-124">Narzędzia te obejmują:</span><span class="sxs-lookup"><span data-stu-id="bcbd6-124">These tools include:</span></span>

- <span data-ttu-id="bcbd6-125">`dotnet watch` Zawiera obserwatora systemu plików, który oczekuje na plik, aby zmienić przed wykonaniem wyznaczonych zestaw poleceń.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-125">`dotnet watch` provides a file system watcher that waits for a file to change before executing a designated set of commands.</span></span> <span data-ttu-id="bcbd6-126">Na przykład następujące polecenie automatycznie odtwarza bieżącego projektu i generuje pełne dane wyjściowe przy każdej zmianie plik w tym:</span><span class="sxs-lookup"><span data-stu-id="bcbd6-126">For example, the following command automatically rebuilds the current project and generates verbose output whenever a file in it changes:</span></span>

   ```console
   dotnet watch -- --verbose build
   ```
  
   <span data-ttu-id="bcbd6-127">Uwaga `--` opcję poprzedzającą `--verbose` opcji.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-127">Note the `--` option that precedes the `--verbose` option.</span></span> <span data-ttu-id="bcbd6-128">Go rozgranicza opcje przekazane bezpośrednio do `dotnet watch` polecenie argumenty, które są przekazywane do elementu podrzędnego `dotnet` procesu.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-128">It delimits the options passed directly to the `dotnet watch` command from the arguments that are passed to the child `dotnet` process.</span></span> <span data-ttu-id="bcbd6-129">Bez tego `--verbose` opcja ma zastosowanie do `dotnet watch` nie polecenia `dotnet build` polecenia.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-129">Without it, the `--verbose` option applies to the `dotnet watch` command, not the `dotnet build` command.</span></span>
  
   <span data-ttu-id="bcbd6-130">Aby uzyskać więcej informacji, zobacz [opracowanie platformy ASP.NET Core aplikacji przy użyciu czujki dotnet](/aspnet/core/tutorials/dotnet-watch)</span><span class="sxs-lookup"><span data-stu-id="bcbd6-130">For more information, see [Develop ASP.NET Core apps using dotnet watch](/aspnet/core/tutorials/dotnet-watch)</span></span>

- <span data-ttu-id="bcbd6-131">`dotnet dev-certs` generuje i zarządza certyfikaty używane podczas tworzenia aplikacji platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-131">`dotnet dev-certs` generates and manages certificates used during development in ASP.NET Core applications.</span></span>

- <span data-ttu-id="bcbd6-132">`dotnet user-secrets` zarządza kluczy tajnych w magazynie tajny użytkownika w aplikacjach ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-132">`dotnet user-secrets` manages the secrets in a user secret store in ASP.NET Core applications.</span></span>

- <span data-ttu-id="bcbd6-133">`dotnet sql-cache` tworzy tabelę i indeksy w bazie danych programu Microsoft SQL Server używanego do buforowania rozproszonego.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-133">`dotnet sql-cache` creates a table and indexes in a Microsoft SQL Server database to be used for distributed caching.</span></span>

- <span data-ttu-id="bcbd6-134">`dotnet ef` to narzędzie do zarządzania bazami danych, <xref:Microsoft.EntityFrameworkCore.DbContext> obiektów i migracje w aplikacjach Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-134">`dotnet ef` is a tool for managing databases, <xref:Microsoft.EntityFrameworkCore.DbContext> objects, and migrations in Entity Framework Core applications.</span></span> <span data-ttu-id="bcbd6-135">Aby uzyskać więcej informacji, zobacz [narzędzia wiersza polecenia platformy .NET Core EF](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="bcbd6-135">For more information, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

### <a name="global-tools"></a><span data-ttu-id="bcbd6-136">Narzędzia globalne</span><span class="sxs-lookup"><span data-stu-id="bcbd6-136">Global Tools</span></span>

<span data-ttu-id="bcbd6-137">.NET core 2.1 obsługuje *globalne narzędzia* — to znaczy niestandardowe narzędzia dostępne globalnie z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-137">.NET Core 2.1 supports *Global Tools* -- that is, custom tools that are available globally from the command line.</span></span> <span data-ttu-id="bcbd6-138">Modelu rozszerzalności w poprzednich wersjach programu .NET Core udostępnione niestandardowego narzędzia na podstawie projektu na tylko przy użyciu [ `DotnetCliToolReference` ](../tools/extensibility.md#consuming-per-project-tools).</span><span class="sxs-lookup"><span data-stu-id="bcbd6-138">The extensibility model in previous versions of .NET Core made custom tools available on a per project basis only by using [`DotnetCliToolReference`](../tools/extensibility.md#consuming-per-project-tools).</span></span>

<span data-ttu-id="bcbd6-139">Aby zainstalować narzędzie globalne, należy użyć [instalacji narzędzi dotnet](..\tools\dotnet-tool-install.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-139">To install a Global Tool, you use the [dotnet tool install](..\tools\dotnet-tool-install.md) command.</span></span> <span data-ttu-id="bcbd6-140">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="bcbd6-140">For example:</span></span>

```console
dotnet tool install -g dotnetsay
```

<span data-ttu-id="bcbd6-141">Po zakończeniu instalacji można uruchomić narzędzie z wiersza polecenia, określając nazwę narzędzia.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-141">Once installed, the tool can be run from the command line by specifying the tool name.</span></span> <span data-ttu-id="bcbd6-142">Aby uzyskać więcej informacji, zobacz [Omówienie narzędzia globalne .NET Core](../tools/global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="bcbd6-142">For more information, see [.NET Core Global Tools overview](../tools/global-tools.md).</span></span>

### <a name="tool-management-with-the-dotnet-tool-command"></a><span data-ttu-id="bcbd6-143">Narzędzie do zarządzania za pomocą `dotnet tool` polecenia</span><span class="sxs-lookup"><span data-stu-id="bcbd6-143">Tool management with the `dotnet tool` command</span></span>

<span data-ttu-id="bcbd6-144">W .NET Core SDK 2.1 (v 2.1.300), użyj wszystkich operacji narzędzia `dotnet tool` polecenia.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-144">In .NET Core SDK 2.1 (v 2.1.300), all tools operations use the `dotnet tool` command.</span></span> <span data-ttu-id="bcbd6-145">Dostępne są następujące opcje:</span><span class="sxs-lookup"><span data-stu-id="bcbd6-145">The following options are available:</span></span>

- <span data-ttu-id="bcbd6-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) Aby zainstalować narzędzie.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) to install a tool.</span></span>

- <span data-ttu-id="bcbd6-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) Aby odinstalować i ponownie zainstalować narzędzie, które skutecznie aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) to uninstall and reinstall a tool, which effectively updates it.</span></span>

- <span data-ttu-id="bcbd6-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) Aby wyświetlić listę aktualnie zainstalowane narzędzia.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) to list currently installed tools.</span></span>

- <span data-ttu-id="bcbd6-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) Aby odinstalować narzędzia aktualnie zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) to uninstall currently installed tools.</span></span>

## <a name="roll-forward"></a><span data-ttu-id="bcbd6-150">Przenoszenia do przodu</span><span class="sxs-lookup"><span data-stu-id="bcbd6-150">Roll forward</span></span>

<span data-ttu-id="bcbd6-151">Wszystkie aplikacje .NET Core automatycznemu .NET 2.0 Core przekazywane dalej do najnowszej wersji *wersja pomocnicza* zainstalowanego w systemie.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-151">All .NET Core applications starting with the .NET Core 2.0 automatically roll forward to the latest *minor version* installed on a system.</span></span> 

<span data-ttu-id="bcbd6-152">Zaczynając .NET Core 2.0, jeśli wersja platformy .NET Core, że aplikacja została skompilowana przy nie jest obecny w czasie wykonywania, aplikacja automatycznie jest uruchamiana dla zainstalowana najnowsza wersja *wersja pomocnicza* programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-152">Starting with .NET Core 2.0, if the version of .NET Core that an application was built with is not present at runtime, the application automatically runs against the latest installed *minor version* of .NET Core.</span></span> <span data-ttu-id="bcbd6-153">Innymi słowy Jeśli aplikacja jest wbudowana .NET Core 2.0 z i .NET Core 2.0 nie jest dostępny w systemie hosta, ale .NET Core 2.1, aplikacja zostanie uruchomiona przy użyciu zestawu .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-153">In other words, if an application is built with .NET Core 2.0, and .NET Core 2.0 is not present on the host system but .NET Core 2.1 is, the application runs with .NET Core 2.1.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bcbd6-154">To zachowanie przewijaniem do nie ma zastosowania do podglądu wersjach.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-154">This roll-forward behavior doesn't apply to preview releases.</span></span> <span data-ttu-id="bcbd6-155">Nie ma zastosowania główne wersje.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-155">Nor does it apply to major releases.</span></span> <span data-ttu-id="bcbd6-156">Na przykład aplikacji .NET Core 1.0 nie są przekazywane dalej do .NET Core w wersji 2.0 lub .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-156">For example, a .NET Core 1.0 application wouldn't roll forward to .NET Core 2.0 or .NET Core 2.1.</span></span>

<span data-ttu-id="bcbd6-157">Można również wyłączyć zbiorczego wersja pomocnicza w jednym z trzech sposobów:</span><span class="sxs-lookup"><span data-stu-id="bcbd6-157">You can also disable minor version roll forward in any of three ways:</span></span>

- <span data-ttu-id="bcbd6-158">Ustaw `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` zmiennej środowiskowej na wartość 0.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-158">Set the `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` environment variable to 0.</span></span>

- <span data-ttu-id="bcbd6-159">Dodaj następujący wiersz do pliku runtimeconfig.json:</span><span class="sxs-lookup"><span data-stu-id="bcbd6-159">Add the following line to the runtimeconfig.json file:</span></span>

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- <span data-ttu-id="bcbd6-160">Korzystając z [narzędzi interfejsu wiersza polecenia platformy .NET Core](../tools/index.md), obejmują takie jak następująca opcja za pomocą polecenia .NET Core `run`:</span><span class="sxs-lookup"><span data-stu-id="bcbd6-160">When using [.NET Core CLI tools](../tools/index.md), include the following option with a .NET Core command such as `run`:</span></span>

   ```console
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

## <a name="deployment"></a><span data-ttu-id="bcbd6-161">wdrażania</span><span class="sxs-lookup"><span data-stu-id="bcbd6-161">Deployment</span></span>

### <a name="self-contained-application-servicing"></a><span data-ttu-id="bcbd6-162">Obsługa aplikację autonomiczną</span><span class="sxs-lookup"><span data-stu-id="bcbd6-162">Self-contained application servicing</span></span>

<span data-ttu-id="bcbd6-163">`dotnet publish` teraz publikuje niezależne aplikacji za pomocą wersji środowiska uruchomieniowego obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-163">`dotnet publish` now publishes self-contained applications with a serviced runtime version.</span></span> <span data-ttu-id="bcbd6-164">Gdy opublikujesz aplikację autonomiczną z .NET Core SDK 2.1 (v 2.1.300), aplikacja zawiera najnowszą wersję środowiska uruchomieniowego obsługiwanych znane przez ten zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-164">When you publish a self-contained application with the .NET Core 2.1 SDK (v 2.1.300), your application includes the latest serviced runtime version known by that SDK.</span></span> <span data-ttu-id="bcbd6-165">Podczas uaktualniania do najnowszej wersji zestawu SDK, będzie publikować przy użyciu najnowszej wersji środowiska uruchomieniowego .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-165">When you upgrade to the latest SDK, you’ll publish with the latest .NET Core runtime version.</span></span> <span data-ttu-id="bcbd6-166">Dotyczy to dla środowisk uruchomieniowych .NET Core 1.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-166">This applies for .NET Core 1.0 runtimes and later.</span></span>

<span data-ttu-id="bcbd6-167">Publikowanie niezależne zależy od wersji środowiska uruchomieniowego na NuGet.org. Nie trzeba mieć serwisowanego środowiska uruchomieniowego na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-167">Self-contained publishing relies on runtime versions on NuGet.org. You do not need to have the serviced runtime on your machine.</span></span>

<span data-ttu-id="bcbd6-168">Przy użyciu zestawu .NET Core 2.0 SDK, niezależne aplikacje są publikowane ze środowiskiem uruchomieniowym platformy .NET Core 2.0.0, chyba że określono inną wersję za pomocą `RuntimeFrameworkVersion` właściwości.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-168">Using the .NET Core 2.0 SDK, self-contained applications are published with the .NET Core 2.0.0 runtime unless a different version is specified via the `RuntimeFrameworkVersion` property.</span></span> <span data-ttu-id="bcbd6-169">Z to nowe zachowanie już nie musisz ustawić tę właściwość, aby wybrać wyższą wersję środowiska uruchomieniowego dla swojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-169">With this new behavior, you’ll no longer need to set this property to select a higher runtime version for a self-contained application.</span></span> <span data-ttu-id="bcbd6-170">Najłatwiejszy idąc dalej jest zawsze publikowanie za pomocą .NET Core-SDK 2.1 (v 2.1.300).</span><span class="sxs-lookup"><span data-stu-id="bcbd6-170">The easiest approach going forward is to always publish with .NET Core 2.1 SDK (v 2.1.300).</span></span>

## <a name="windows-compatibility-pack"></a><span data-ttu-id="bcbd6-171">Pakiet zgodności systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bcbd6-171">Windows Compatibility Pack</span></span>

<span data-ttu-id="bcbd6-172">Jeśli port istniejącego kodu z programu .NET Framework do platformy .NET Core, możesz użyć [pakiet zgodności systemu Windows](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="bcbd6-172">When you port existing code from the .NET Framework to .NET Core, you can use the [Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span> <span data-ttu-id="bcbd6-173">Zapewnia dostęp do 20 000 API więcej niż jest dostępne w .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-173">It provides access to 20,000 more APIs than are available in .NET Core.</span></span> <span data-ttu-id="bcbd6-174">Te interfejsy API obejmują typy w <xref:System.Drawing?displayProperty="nameWithType"> przestrzeni nazw, <xref:System.Diagnostics.EventLog> klasy, usługi WMI, liczniki wydajności, usług systemu Windows i typy rejestru systemu Windows i elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-174">These APIs include types in the <xref:System.Drawing?displayProperty="nameWithType"> namespace, the <xref:System.Diagnostics.EventLog> class, WMI, Performance Counters, Windows Services, and the Windows registry types and members.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="bcbd6-175">Ulepszenia kompilatora JIT</span><span class="sxs-lookup"><span data-stu-id="bcbd6-175">JIT compiler improvements</span></span>

<span data-ttu-id="bcbd6-176">Oprogramowanie .NET core zawiera nową technologią kompilatora JIT o nazwie *kompilacji do warstwy* (znanej także jako *adaptacyjną optymalizacji*) która może znacznie poprawić wydajność.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-176">.NET Core incorporates a new JIT compiler technology called *tiered compilation* (also known as *adaptive optimization*) that can significantly improve performance.</span></span> <span data-ttu-id="bcbd6-177">Kompilacja warstwowego jest ustawienie opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-177">Tiered compilation is an opt-in setting.</span></span>

<span data-ttu-id="bcbd6-178">Co ważne zadania wykonywane przez kompilator JIT optymalizuje wykonanie kodu.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-178">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="bcbd6-179">Jednak w przypadku ścieżek kodu rzadko używanych kompilator może poświęcić więcej czasu na Optymalizacja kodu niż środowiska uruchomieniowego spędza uruchamiania zoptymalizowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-179">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends running unoptimized code.</span></span> <span data-ttu-id="bcbd6-180">Kompilacja warstwowych wprowadza dwóch etapach w kompilacji JIT:</span><span class="sxs-lookup"><span data-stu-id="bcbd6-180">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="bcbd6-181">A **najpierw warstwy**, które generuje kod tak szybko jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-181">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="bcbd6-182">A **Druga warstwa**, który generuje zoptymalizowanego kodu dla tych metod, które są często wykonywane.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-182">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="bcbd6-183">Druga warstwa kompilacji jest wykonywane równolegle na potrzeby zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-183">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="bcbd6-184">Można włączyć do warstwowego kompilacji na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-184">You can opt into tiered compilation in either of two ways.</span></span>

- <span data-ttu-id="bcbd6-185">Aby używać warstwowych kompilacji we wszystkich projektach, które zestaw SDK programu .NET Core 2.1, ustaw zmienną środowiskową następujące:</span><span class="sxs-lookup"><span data-stu-id="bcbd6-185">To use tiered compilation in all projects that use the .NET Core 2.1 SDK, set the following environment variable:</span></span>

  ```console
  COMPlus_TieredCompilation="1"
  ```

- <span data-ttu-id="bcbd6-186">Aby używać warstwowych kompilacji na podstawie na projekt, Dodaj `<TieredCompilation>` właściwości `<PropertyGroup>` sekcji pliku projektu MSBuild, jak przedstawiono na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="bcbd6-186">To use tiered compilation on a per-project basis, add the `<TieredCompilation>` property to the `<PropertyGroup>` section of the MSBuild project file, as the following example shows:</span></span>

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a><span data-ttu-id="bcbd6-187">Zmiany interfejsu API</span><span class="sxs-lookup"><span data-stu-id="bcbd6-187">API changes</span></span>

### <a name="spant-and-memoryt"></a><span data-ttu-id="bcbd6-188">`Span<T>` I `Memory<T>`</span><span class="sxs-lookup"><span data-stu-id="bcbd6-188">`Span<T>` and `Memory<T>`</span></span>

<span data-ttu-id="bcbd6-189">.NET core 2.1 zawiera niektóre nowe typy, które sprawiają, że praca z tablicami i innych rodzajów wydajniejsza pamięci.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-189">.NET Core 2.1 includes some new types that make working with arrays and other types of memory much more efficient.</span></span> <span data-ttu-id="bcbd6-190">Nowe typy:</span><span class="sxs-lookup"><span data-stu-id="bcbd6-190">The new types include:</span></span>

- <span data-ttu-id="bcbd6-191"><xref:System.Span%601?displayProperty=nameWithType> i <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-191"><xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="bcbd6-192"><xref:System.Memory%601?displayProperty=nameWithType> i <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-192"><xref:System.Memory%601?displayProperty=nameWithType> and <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="bcbd6-193">Bez tych typów przy przekazywaniu tych elementów jako część tablicy lub sekcji bufora pamięci należy utworzyć kopię część danych przed przekazaniem go do metody.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-193">Without these types, when passing such items as a portion of an array or a section of a memory buffer, you have to make a copy of some portion of the data before passing it to a method.</span></span> <span data-ttu-id="bcbd6-194">Te typy zapewniają wirtualny widok tych danych, która eliminuje potrzebę alokacji dodatkowej pamięci i operacje kopiowania.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-194">These types provide a virtual view of that data that eliminates the need for the additional memory allocation and copy operations.</span></span>

<span data-ttu-id="bcbd6-195">W poniższym przykładzie użyto <xref:System.Span%601> wystąpienia w celu zapewnienia przeglądu wirtualny 10 elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-195">The following example uses a <xref:System.Span%601> instance to provide a virtual view of 10 elements of an array.</span></span>

[!CODE-csharp[Span\<T>](~/samples/core/whats-new/whats-new-in-21/cs/program.cs)]

### <a name="brotli-compression"></a><span data-ttu-id="bcbd6-196">Kompresja Brotli</span><span class="sxs-lookup"><span data-stu-id="bcbd6-196">Brotli compression</span></span>

<span data-ttu-id="bcbd6-197">.NET core 2.1 dodaje obsługę Brotli kompresji i dekompresji.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-197">.NET Core 2.1 adds support for Brotli compression and decompression.</span></span> <span data-ttu-id="bcbd6-198">Brotli to algorytm kompresji bezstratny ogólnego przeznaczenia, który jest zdefiniowany w [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) i są obsługiwane w większości przeglądarek sieci web i serwerów głównych sieci web.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-198">Brotli is a general-purpose lossless compression algorithm that is defined in [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) and is supported by most web browsers and major web servers.</span></span> <span data-ttu-id="bcbd6-199">Można użyć podstawie strumienia <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> klasy lub wysokiej wydajności na podstawie zakresu <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> i <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-199">You can use the stream-based <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> class or the high-performance span-based <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> and <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> classes.</span></span> <span data-ttu-id="bcbd6-200">Poniższy przykład przedstawia kompresji z <xref:System.IO.Compression.BrotliStream> klasy:</span><span class="sxs-lookup"><span data-stu-id="bcbd6-200">The following example illustrates compression with the <xref:System.IO.Compression.BrotliStream> class:</span></span>

[!CODE-csharp[Brotli compression](~/samples/core/whats-new/whats-new-in-21/cs/brotli.cs#1)]

<span data-ttu-id="bcbd6-201"><xref:System.IO.Compression.BrotliStream> Zachowanie jest takie samo, jak <xref:System.IO.Compression.DeflateStream> i <xref:System.IO.Compression.GZipStream>, która ułatwia przekonwertować kod, który wywołuje te interfejsy API do <xref:System.IO.Compression.BrotliStream>.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-201">The <xref:System.IO.Compression.BrotliStream> behavior is the same as <xref:System.IO.Compression.DeflateStream> and <xref:System.IO.Compression.GZipStream>, which makes it easy to convert code that calls these APIs to <xref:System.IO.Compression.BrotliStream>.</span></span>

### <a name="new-cryptography-apis-and-cryptography-improvements"></a><span data-ttu-id="bcbd6-202">Kryptografia nowych interfejsów API i ulepszenia kryptografii</span><span class="sxs-lookup"><span data-stu-id="bcbd6-202">New cryptography APIs and cryptography improvements</span></span>

<span data-ttu-id="bcbd6-203">.NET core 2.1 zawiera wiele ulepszeń usługi cryptography API:</span><span class="sxs-lookup"><span data-stu-id="bcbd6-203">.NET Core 2.1 includes numerous enhancements to the cryptography APIs:</span></span>

- <span data-ttu-id="bcbd6-204"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> jest niedostępny w pakiecie System.Security.Cryptography.Pkcs.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-204"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> is available in the System.Security.Cryptography.Pkcs package.</span></span> <span data-ttu-id="bcbd6-205">Implementacja jest taka sama jak <xref:System.Security.Cryptography.Pkcs.SignedCms> klasa w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-205">The implementation is the same as the <xref:System.Security.Cryptography.Pkcs.SignedCms> class in the .NET Framework.</span></span>

- <span data-ttu-id="bcbd6-206">Nowe przeciążeń <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> i <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> metody akceptuje identyfikator algorytmu wyznaczania wartości skrótu, aby umożliwić wywołującym można pobrać wartości odcisku palca certyfikatu przy użyciu algorytmy innych niż SHA-1.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-206">New overloads of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> and <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> methods accept a hash algorithm identifier to enable callers to get certificate thumbprint values using algorithms other than SHA-1.</span></span>

- <span data-ttu-id="bcbd6-207">Nowe <xref:System.Span%601>— oparte na kryptografii interfejsy API są dostępne do tworzenia skrótu HMAC, kryptograficzne Generowanie liczby losowej podpisu asymetrycznego generowania, przetwarzania podpisu asymetrycznego i szyfrowania RSA.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-207">New <xref:System.Span%601>-based cryptography APIs are available for hashing, HMAC, cryptographic random number generation, asymmetric signature generation, asymmetric signature processing, and RSA encryption.</span></span>

- <span data-ttu-id="bcbd6-208">Wydajność <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> ulepszono o około 15% przy użyciu <xref:System.Span%601>— na podstawie implementacji.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-208">The performance of <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> has improved by about 15% by using a <xref:System.Span%601>-based implementation.</span></span>

- <span data-ttu-id="bcbd6-209">Nowe <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> klasa zawiera dwa nowe metody:</span><span class="sxs-lookup"><span data-stu-id="bcbd6-209">The new <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> class includes two new methods:</span></span>

  - <span data-ttu-id="bcbd6-210"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> Trwa stałej ilości czasu zwracanego przez dowolnego dwóch parametrów wejściowych taką samą długość, dzięki czemu nadaje się do użytku w kryptograficznych weryfikacji, aby uniknąć Współtworzenie chronometrażu informacji kanału po stronie.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-210"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> takes a fixed amount of time to return for any two inputs of the same length, which makes it suitable for use in cryptographic verification to avoid contributing to timing side-channel information.</span></span>

  - <span data-ttu-id="bcbd6-211"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> to nie może zostać zoptymalizowana procedura czyszczenia pamięci.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-211"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> is a memory-clearing routine that cannot be optimized.</span></span>

- <span data-ttu-id="bcbd6-212">Statycznych <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=fullName> wypełnienia metody <xref:System.Span%601> losowych wartości.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-212">The static <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=fullName> method fills a <xref:System.Span%601> with random values.</span></span>

- <span data-ttu-id="bcbd6-213"><xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> Jest teraz obsługiwana w systemie Linux i maxOS.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-213">The <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> is now supported on Linux and maxOS.</span></span>

- <span data-ttu-id="bcbd6-214">Diffie-Hellman krzywej eliptycznej (ECDH) jest teraz dostępna w <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> klasy rodziny.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-214">Elliptic-Curve Diffie-Hellman (ECDH) is now available in the <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> class family.</span></span> <span data-ttu-id="bcbd6-215">Powierzchnia jest taka sama, jak w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-215">The surface area is the same as in the .NET Framework.</span></span>

- <span data-ttu-id="bcbd6-216">Zwrócone przez wystąpienie <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> można zaszyfrować lub odszyfrować z OAEP przy użyciu skrótu SHA-2, oraz generowanie lub sprawdzają poprawność podpisów przy użyciu RSA-PSS.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-216">The instance returned by <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> can encrypt or decrypt with OAEP using a SHA-2 digest, as well as generate or validate signatures using RSA-PSS.</span></span>

### <a name="sockets-improvements"></a><span data-ttu-id="bcbd6-217">Ulepszenia gniazda</span><span class="sxs-lookup"><span data-stu-id="bcbd6-217">Sockets improvements</span></span>

<span data-ttu-id="bcbd6-218">Oprogramowanie .NET core zawiera nowy typ, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>i ponownie zapisane <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, które stanowią podstawę sieci wyższego poziomu interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-218">.NET Core includes a new type, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, and a rewritten <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, that form the basis of higher-level networking APIs.</span></span>  <span data-ttu-id="bcbd6-219"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, na przykład jest podstawą <xref:System.Net.Http.HttpClient> implementacji.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-219"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, for example, is the basis of the <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="bcbd6-220">W poprzednich wersjach programu .NET Core API wyższego poziomu były oparte na natywnych implementacji sieci.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-220">In previous versions of .NET Core, higher-level APIs were based on native networking implementations.</span></span>

<span data-ttu-id="bcbd6-221">Implementacja sockets wprowadzone w programie .NET Core 2.1 zawiera następujące korzyści:</span><span class="sxs-lookup"><span data-stu-id="bcbd6-221">The sockets implementation introduced in .NET Core 2.1 has a number of advantages:</span></span>

- <span data-ttu-id="bcbd6-222">Poprawa wydajności znaczących w porównaniu z poprzedniej implementacji.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-222">A significant performance improvement when compared with the previous implementation.</span></span>

- <span data-ttu-id="bcbd6-223">Eliminacja zależności platformy, które upraszcza wdrażania i obsługi.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-223">Elimination of platform dependencies, which simplifies deployment and servicing.</span></span>

- <span data-ttu-id="bcbd6-224">Zachowanie spójności na wszystkich platformach .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-224">Consistent behavior across all .NET Core platforms.</span></span>

<span data-ttu-id="bcbd6-225"><xref:System.Net.Http.SocketsHttpHandler> jest domyślna implementacja .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-225"><xref:System.Net.Http.SocketsHttpHandler> is the default implementation in .NET Core 2.1.</span></span> <span data-ttu-id="bcbd6-226">Jednak należy skonfigurować aplikację do używania starszej <xref:System.Net.Http.HttpClientHandler> klasy przez wywołanie metody <xref:System.AppContext.SetSwitch%2A?displayProperty="nameWithType"> metody:</span><span class="sxs-lookup"><span data-stu-id="bcbd6-226">However, you can configure your application to use the older <xref:System.Net.Http.HttpClientHandler> class by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty="nameWithType"> method:</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.useSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.useSocketsHttpHandler", False)
```

<span data-ttu-id="bcbd6-227">Można również użyć środowiska zmiennej, aby zrezygnować z używania gniazda implementacje na podstawie <xref:System.Net.Http.SocketsHttpHandler>.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-227">You can also use an environment variable to opt out of using sockets implementations based on <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="bcbd6-228">Aby to zrobić, ustaw `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` albo `false` lub równa 0.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-228">To do this, set the `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` to either `false` or 0.</span></span>

<span data-ttu-id="bcbd6-229">W systemie Windows, można używać <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, która zależy od implementacji native lub <xref:System.Net.Http.SocketsHttpHandler> klasy przez przekazanie wystąpienia klasy do <xref:System.Net.Http.HttpClient> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-229">On Windows, you can also choose to use <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, which relies on a native implementation, or the <xref:System.Net.Http.SocketsHttpHandler> class by passing an instance of the class to the <xref:System.Net.Http.HttpClient> constructor.</span></span>

<span data-ttu-id="bcbd6-230">W systemie Linux i macOS, można skonfigurować tylko <xref:System.Net.Http.HttpClient> na podstawie każdego procesu.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-230">On Linux and macOS, you can only configure <xref:System.Net.Http.HttpClient> on a per-process basis.</span></span> <span data-ttu-id="bcbd6-231">W systemie Linux należy wdrożyć [libcurl](https://curl.haxx.se/libcurl/) Jeśli chcesz używać starego <xref:System.Net.Http.HttpClient> implementacji.</span><span class="sxs-lookup"><span data-stu-id="bcbd6-231">On Linux, you need to deploy [libcurl](https://curl.haxx.se/libcurl/) if you want to use the old <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="bcbd6-232">(Jest instalowana z programem .NET Core 2.0.)</span><span class="sxs-lookup"><span data-stu-id="bcbd6-232">(It is installed with .NET Core 2.0.)</span></span>

## <a name="see-also"></a><span data-ttu-id="bcbd6-233">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bcbd6-233">See also</span></span>

[<span data-ttu-id="bcbd6-234">Co nowego w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="bcbd6-234">What's new in .NET Core</span></span>](index.md)  
[<span data-ttu-id="bcbd6-235">Nowe funkcje w programie EF Core 2.1</span><span class="sxs-lookup"><span data-stu-id="bcbd6-235">New features in EF Core 2.1</span></span>](/ef/core/what-is-new/ef-core-2.1)  
[<span data-ttu-id="bcbd6-236">What's new in ASP.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="bcbd6-236">What's new in ASP.NET Core 2.1</span></span>](/aspnet/core/aspnetcore-2.1)
