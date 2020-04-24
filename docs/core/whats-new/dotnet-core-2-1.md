---
title: Co nowego w programie .NET Core 2.1
description: Dowiedz się więcej o nowych funkcjach znalezionych w .NET Core 2.1.
dev_langs:
- csharp
- vb
ms.date: 10/10/2018
ms.openlocfilehash: 78d9a6490c0479d9c21e01d0bcba41294d674a5c
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644381"
---
# <a name="whats-new-in-net-core-21"></a><span data-ttu-id="e23a0-103">Co nowego w programie .NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="e23a0-103">What's new in .NET Core 2.1</span></span>

<span data-ttu-id="e23a0-104">Program .NET Core 2.1 zawiera ulepszenia i nowe funkcje w następujących obszarach:</span><span class="sxs-lookup"><span data-stu-id="e23a0-104">.NET Core 2.1 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="e23a0-105">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="e23a0-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="e23a0-106">Przewiń do przodu</span><span class="sxs-lookup"><span data-stu-id="e23a0-106">Roll forward</span></span>](#roll-forward)
- [<span data-ttu-id="e23a0-107">Wdrożenie</span><span class="sxs-lookup"><span data-stu-id="e23a0-107">Deployment</span></span>](#deployment)
- [<span data-ttu-id="e23a0-108">Pakiet zgodności systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e23a0-108">Windows Compatibility Pack</span></span>](#windows-compatibility-pack)
- [<span data-ttu-id="e23a0-109">Ulepszenia kompilacji JIT</span><span class="sxs-lookup"><span data-stu-id="e23a0-109">JIT compilation improvements</span></span>](#jit-compiler-improvements)
- [<span data-ttu-id="e23a0-110">Zmiany api</span><span class="sxs-lookup"><span data-stu-id="e23a0-110">API changes</span></span>](#api-changes)

## <a name="tooling"></a><span data-ttu-id="e23a0-111">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="e23a0-111">Tooling</span></span>

<span data-ttu-id="e23a0-112">Zestaw .NET Core 2.1 SDK (v 2.1.300), oprzyrządowanie dołączone do programu .NET Core 2.1, zawiera następujące zmiany i ulepszenia:</span><span class="sxs-lookup"><span data-stu-id="e23a0-112">The .NET Core 2.1 SDK (v 2.1.300), the tooling included with .NET Core 2.1, includes the following changes and enhancements:</span></span>

### <a name="build-performance-improvements"></a><span data-ttu-id="e23a0-113">Twórz ulepszenia wydajności</span><span class="sxs-lookup"><span data-stu-id="e23a0-113">Build performance improvements</span></span>

<span data-ttu-id="e23a0-114">Głównym celem platformy .NET Core 2.1 jest poprawa wydajności w czasie kompilacji, szczególnie w przypadku kompilacji przyrostowych.</span><span class="sxs-lookup"><span data-stu-id="e23a0-114">A major focus of .NET Core 2.1 is improving build-time performance, particularly for incremental builds.</span></span> <span data-ttu-id="e23a0-115">Te ulepszenia wydajności dotyczą zarówno kompilacji `dotnet build` wiersza polecenia przy użyciu i kompilacji w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e23a0-115">These performance improvements apply to both command-line builds using `dotnet build` and to builds in Visual Studio.</span></span> <span data-ttu-id="e23a0-116">Niektóre poszczególne obszary poprawy obejmują:</span><span class="sxs-lookup"><span data-stu-id="e23a0-116">Some individual areas of improvement include:</span></span>

- <span data-ttu-id="e23a0-117">W przypadku rozpoznawania zasobów pakietu rozpoznawanie tylko zasobów używanych przez kompilację, a nie wszystkie zasoby.</span><span class="sxs-lookup"><span data-stu-id="e23a0-117">For package asset resolution, resolving only assets used by a build rather than all assets.</span></span>

- <span data-ttu-id="e23a0-118">Buforowanie odniesień do złożenia.</span><span class="sxs-lookup"><span data-stu-id="e23a0-118">Caching of assembly references.</span></span>

- <span data-ttu-id="e23a0-119">Korzystanie z długotrwałych serwerów kompilacji SDK, `dotnet build` które są procesami, które obejmują poszczególne wywołania.</span><span class="sxs-lookup"><span data-stu-id="e23a0-119">Use of long-running SDK build servers, which are processes that span across individual `dotnet build` invocations.</span></span> <span data-ttu-id="e23a0-120">Eliminują one konieczność JIT-kompilować duże `dotnet build` bloki kodu za każdym razem jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="e23a0-120">They eliminate the need to JIT-compile large blocks of code every time `dotnet build` is run.</span></span> <span data-ttu-id="e23a0-121">Procesy serwera kompilacji można automatycznie zakończyć za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="e23a0-121">Build server processes can be automatically terminated with the following command:</span></span>

   ```dotnetcli
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a><span data-ttu-id="e23a0-122">Nowe polecenia interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="e23a0-122">New CLI commands</span></span>

<span data-ttu-id="e23a0-123">Wiele narzędzi, które były dostępne tylko na `DotnetCliToolReference` podstawie projektu przy użyciu są teraz dostępne jako część .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="e23a0-123">A number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="e23a0-124">Do tych narzędzi należą:</span><span class="sxs-lookup"><span data-stu-id="e23a0-124">These tools include:</span></span>

- <span data-ttu-id="e23a0-125">`dotnet watch`udostępnia obserwatora systemu plików, który czeka na zmianę pliku przed wykonaniem wyznaczonego zestawu poleceń.</span><span class="sxs-lookup"><span data-stu-id="e23a0-125">`dotnet watch` provides a file system watcher that waits for a file to change before executing a designated set of commands.</span></span> <span data-ttu-id="e23a0-126">Na przykład następujące polecenie automatycznie odbudowuje bieżący projekt i generuje pełne dane wyjściowe za każdym razem, gdy zmienia się w nim plik:</span><span class="sxs-lookup"><span data-stu-id="e23a0-126">For example, the following command automatically rebuilds the current project and generates verbose output whenever a file in it changes:</span></span>

   ```dotnetcli
   dotnet watch -- --verbose build
   ```

   <span data-ttu-id="e23a0-127">Zwróć `--` uwagę na opcję `--verbose` poprzedzającą tę opcję.</span><span class="sxs-lookup"><span data-stu-id="e23a0-127">Note the `--` option that precedes the `--verbose` option.</span></span> <span data-ttu-id="e23a0-128">Rozgranicza opcje przekazywane bezpośrednio `dotnet watch` do polecenia z argumentów, `dotnet` które są przekazywane do procesu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="e23a0-128">It delimits the options passed directly to the `dotnet watch` command from the arguments that are passed to the child `dotnet` process.</span></span> <span data-ttu-id="e23a0-129">Bez niego `--verbose` opcja ma zastosowanie `dotnet watch` do polecenia, a nie do `dotnet build` polecenia.</span><span class="sxs-lookup"><span data-stu-id="e23a0-129">Without it, the `--verbose` option applies to the `dotnet watch` command, not the `dotnet build` command.</span></span>
  
   <span data-ttu-id="e23a0-130">Aby uzyskać więcej informacji, zobacz [Tworzenie aplikacji ASP.NET Core przy użyciu zegarka dotnet](/aspnet/core/tutorials/dotnet-watch).</span><span class="sxs-lookup"><span data-stu-id="e23a0-130">For more information, see [Develop ASP.NET Core apps using dotnet watch](/aspnet/core/tutorials/dotnet-watch).</span></span>

- <span data-ttu-id="e23a0-131">`dotnet dev-certs`generuje certyfikaty używane podczas tworzenia w aplikacjach ASP.NET Core i zarządza nimi.</span><span class="sxs-lookup"><span data-stu-id="e23a0-131">`dotnet dev-certs` generates and manages certificates used during development in ASP.NET Core applications.</span></span>

- <span data-ttu-id="e23a0-132">`dotnet user-secrets`zarządza wpisami tajnymi w tajnym magazynie użytkownika w aplikacjach ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e23a0-132">`dotnet user-secrets` manages the secrets in a user secret store in ASP.NET Core applications.</span></span>

- <span data-ttu-id="e23a0-133">`dotnet sql-cache`tworzy tabelę i indeksy w bazie danych programu Microsoft SQL Server, które mają być używane do buforowania rozproszonego.</span><span class="sxs-lookup"><span data-stu-id="e23a0-133">`dotnet sql-cache` creates a table and indexes in a Microsoft SQL Server database to be used for distributed caching.</span></span>

- <span data-ttu-id="e23a0-134">`dotnet ef`jest narzędziem do zarządzania bazami danych, <xref:Microsoft.EntityFrameworkCore.DbContext> obiektami i migracjami w aplikacjach Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="e23a0-134">`dotnet ef` is a tool for managing databases, <xref:Microsoft.EntityFrameworkCore.DbContext> objects, and migrations in Entity Framework Core applications.</span></span> <span data-ttu-id="e23a0-135">Aby uzyskać więcej informacji, zobacz [Narzędzia wiersza polecenia EF Core .NET](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="e23a0-135">For more information, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

### <a name="global-tools"></a><span data-ttu-id="e23a0-136">Narzędzia globalne</span><span class="sxs-lookup"><span data-stu-id="e23a0-136">Global Tools</span></span>

<span data-ttu-id="e23a0-137">Program .NET Core 2.1 obsługuje *narzędzia globalne* — czyli narzędzia niestandardowe, które są dostępne globalnie z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="e23a0-137">.NET Core 2.1 supports *Global Tools* -- that is, custom tools that are available globally from the command line.</span></span> <span data-ttu-id="e23a0-138">Model rozszerzalności w poprzednich wersjach programu .NET Core udostępnił narzędzia niestandardowe dostępne dla projektu tylko za pomocą programu `DotnetCliToolReference`.</span><span class="sxs-lookup"><span data-stu-id="e23a0-138">The extensibility model in previous versions of .NET Core made custom tools available on a per project basis only by using `DotnetCliToolReference`.</span></span>

<span data-ttu-id="e23a0-139">Aby zainstalować narzędzie globalne, należy użyć polecenia [instalacji narzędzia dotnet.](../tools/dotnet-tool-install.md)</span><span class="sxs-lookup"><span data-stu-id="e23a0-139">To install a Global Tool, you use the [dotnet tool install](../tools/dotnet-tool-install.md) command.</span></span> <span data-ttu-id="e23a0-140">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e23a0-140">For example:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="e23a0-141">Po zainstalowaniu narzędzie można uruchomić z wiersza polecenia, określając nazwę narzędzia.</span><span class="sxs-lookup"><span data-stu-id="e23a0-141">Once installed, the tool can be run from the command line by specifying the tool name.</span></span> <span data-ttu-id="e23a0-142">Aby uzyskać więcej informacji, zobacz [omówienie .NET Core Global Tools](../tools/global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="e23a0-142">For more information, see [.NET Core Global Tools overview](../tools/global-tools.md).</span></span>

### <a name="tool-management-with-the-dotnet-tool-command"></a><span data-ttu-id="e23a0-143">Zarządzanie narzędziami `dotnet tool` za pomocą polecenia</span><span class="sxs-lookup"><span data-stu-id="e23a0-143">Tool management with the `dotnet tool` command</span></span>

<span data-ttu-id="e23a0-144">W pliku .NET Core 2.1 SDK `dotnet tool` wszystkie operacje narzędzi używają tego polecenia.</span><span class="sxs-lookup"><span data-stu-id="e23a0-144">In .NET Core 2.1 SDK, all tools operations use the `dotnet tool` command.</span></span> <span data-ttu-id="e23a0-145">Dostępne są następujące opcje:</span><span class="sxs-lookup"><span data-stu-id="e23a0-145">The following options are available:</span></span>

- <span data-ttu-id="e23a0-146">[`dotnet tool install`](../tools/dotnet-tool-install.md), aby zainstalować narzędzie.</span><span class="sxs-lookup"><span data-stu-id="e23a0-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) to install a tool.</span></span>

- <span data-ttu-id="e23a0-147">[`dotnet tool update`](../tools/dotnet-tool-update.md), aby odinstalować i ponownie zainstalować narzędzie, które skutecznie je aktualizuje.</span><span class="sxs-lookup"><span data-stu-id="e23a0-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) to uninstall and reinstall a tool, which effectively updates it.</span></span>

- <span data-ttu-id="e23a0-148">[`dotnet tool list`](../tools/dotnet-tool-list.md), aby wyświetlić listę aktualnie zainstalowanych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="e23a0-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) to list currently installed tools.</span></span>

- <span data-ttu-id="e23a0-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md), aby odinstalować aktualnie zainstalowane narzędzia.</span><span class="sxs-lookup"><span data-stu-id="e23a0-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) to uninstall currently installed tools.</span></span>

## <a name="roll-forward"></a><span data-ttu-id="e23a0-150">Przewiń do przodu</span><span class="sxs-lookup"><span data-stu-id="e23a0-150">Roll forward</span></span>

<span data-ttu-id="e23a0-151">Wszystkie aplikacje .NET Core, począwszy od platformy .NET Core 2.0, automatycznie przewijają się do *najnowszej wersji pomocniczej zainstalowanej* w systemie.</span><span class="sxs-lookup"><span data-stu-id="e23a0-151">All .NET Core applications starting with .NET Core 2.0 automatically roll forward to the latest *minor version* installed on a system.</span></span>

<span data-ttu-id="e23a0-152">Począwszy od .NET Core 2.0, jeśli wersja .NET Core, z którą została zbudowana aplikacja, nie jest obecna w czasie wykonywania, aplikacja automatycznie uruchamia się z *najnowszą zainstalowaną wersją pomocniczą* programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e23a0-152">Starting with .NET Core 2.0, if the version of .NET Core that an application was built with is not present at runtime, the application automatically runs against the latest installed *minor version* of .NET Core.</span></span> <span data-ttu-id="e23a0-153">Innymi słowy, jeśli aplikacja jest zbudowana z .NET Core 2.0, a .NET Core 2.0 nie jest obecny w systemie hosta, ale .NET Core 2.1 jest, aplikacja działa z .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="e23a0-153">In other words, if an application is built with .NET Core 2.0, and .NET Core 2.0 is not present on the host system but .NET Core 2.1 is, the application runs with .NET Core 2.1.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e23a0-154">To zachowanie do przodu nie ma zastosowania do wersji zapoznawczych.</span><span class="sxs-lookup"><span data-stu-id="e23a0-154">This roll-forward behavior doesn't apply to preview releases.</span></span> <span data-ttu-id="e23a0-155">Domyślnie nie dotyczy również głównych wersji, ale można to zmienić za pomocą poniższych ustawień.</span><span class="sxs-lookup"><span data-stu-id="e23a0-155">By default, it also doesn't apply to major releases, but this can be changed with the settings below.</span></span>

<span data-ttu-id="e23a0-156">Można zmodyfikować to zachowanie, zmieniając ustawienie roll-forward na żadnej udostępnionej struktury kandydata.</span><span class="sxs-lookup"><span data-stu-id="e23a0-156">You can modify this behavior by changing the setting for the roll-forward on no candidate shared framework.</span></span> <span data-ttu-id="e23a0-157">Dostępne ustawienia to:</span><span class="sxs-lookup"><span data-stu-id="e23a0-157">The available settings are:</span></span>

- <span data-ttu-id="e23a0-158">`0`- wyłączyć zachowanie przewijania do przodu wersji pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="e23a0-158">`0` - disable minor version roll-forward behavior.</span></span> <span data-ttu-id="e23a0-159">Przy tym ustawieniu aplikacja zbudowana dla platformy .NET Core 2.0.0 zostanie przesuń do przodu do .NET Core 2.0.1, ale nie do .NET Core 2.2.0 lub .NET Core 3.0.0.</span><span class="sxs-lookup"><span data-stu-id="e23a0-159">With this setting, an application built for .NET Core 2.0.0 will roll forward to .NET Core 2.0.1, but not to .NET Core 2.2.0 or .NET Core 3.0.0.</span></span>
- <span data-ttu-id="e23a0-160">`1`- włączyć zachowanie przewijania wersji pomocniczej do przodu.</span><span class="sxs-lookup"><span data-stu-id="e23a0-160">`1` - enable minor version roll-forward behavior.</span></span> <span data-ttu-id="e23a0-161">Jest to wartość domyślna dla tego ustawienia.</span><span class="sxs-lookup"><span data-stu-id="e23a0-161">This is the default value for the setting.</span></span> <span data-ttu-id="e23a0-162">Przy tym ustawieniu aplikacja zbudowana dla platformy .NET Core 2.0.0 zostanie przesuń do przodu do .NET Core 2.0.1 lub .NET Core 2.2.0, w zależności od tego, który z nich jest zainstalowany, ale nie będzie przekierowywać do przodu do .NET Core 3.0.0.</span><span class="sxs-lookup"><span data-stu-id="e23a0-162">With this setting, an application built for .NET Core 2.0.0 will roll forward to either .NET Core 2.0.1 or .NET Core 2.2.0, depending on which one is installed, but it will not roll forward to .NET Core 3.0.0.</span></span>
- <span data-ttu-id="e23a0-163">`2`- włączyć drobne i główne zachowanie roll-forward wersji.</span><span class="sxs-lookup"><span data-stu-id="e23a0-163">`2` - enable minor and major version roll-forward behavior.</span></span> <span data-ttu-id="e23a0-164">Jeśli zestaw, nawet różne wersje główne są brane pod uwagę, więc aplikacja zbudowana dla .NET Core 2.0.0 zostanie przewijana do przodu do .NET Core 3.0.0.</span><span class="sxs-lookup"><span data-stu-id="e23a0-164">If set, even different major versions are considered, so an application built for .NET Core 2.0.0 will roll forward to .NET Core 3.0.0.</span></span>

<span data-ttu-id="e23a0-165">To ustawienie można zmodyfikować na dowolny z trzech sposobów:</span><span class="sxs-lookup"><span data-stu-id="e23a0-165">You can modify this setting in any of three ways:</span></span>

- <span data-ttu-id="e23a0-166">Ustaw `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` zmienną środowiskową na żądaną wartość.</span><span class="sxs-lookup"><span data-stu-id="e23a0-166">Set the `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` environment variable to the desired value.</span></span>

- <span data-ttu-id="e23a0-167">Dodaj następujący wiersz o żądanej wartości do pliku *.runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="e23a0-167">Add the following line with the desired value to the *.runtimeconfig.json* file:</span></span>

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- <span data-ttu-id="e23a0-168">W przypadku korzystania z interfejsu [wiersza polecenia .NET Core](../tools/index.md)należy dodać `run`następującą opcję z żądaną wartością do polecenia .NET Core, taką jak:</span><span class="sxs-lookup"><span data-stu-id="e23a0-168">When using the [.NET Core CLI](../tools/index.md), add the following option with the desired value to a .NET Core command such as `run`:</span></span>

   ```dotnetcli
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

<span data-ttu-id="e23a0-169">Roll do przodu wersji poprawki jest niezależna od tego ustawienia i odbywa się po zastosowaniu dowolnego potencjalnego rzutu wersji pomocniczej lub głównej do przodu.</span><span class="sxs-lookup"><span data-stu-id="e23a0-169">Patch version roll forward is independent of this setting and is done after any potential minor or major version roll forward is applied.</span></span>

## <a name="deployment"></a><span data-ttu-id="e23a0-170">Wdrożenie</span><span class="sxs-lookup"><span data-stu-id="e23a0-170">Deployment</span></span>

### <a name="self-contained-application-servicing"></a><span data-ttu-id="e23a0-171">Samodzielne serwisowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="e23a0-171">Self-contained application servicing</span></span>

<span data-ttu-id="e23a0-172">`dotnet publish`teraz publikuje samodzielne aplikacje z wersją serviced runtime.</span><span class="sxs-lookup"><span data-stu-id="e23a0-172">`dotnet publish` now publishes self-contained applications with a serviced runtime version.</span></span> <span data-ttu-id="e23a0-173">Podczas publikowania aplikacji niezależnej z .NET Core 2.1 SDK (v 2.1.300), aplikacja zawiera najnowszą wersję środowiska uruchomieniowego usługi znane przez ten zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="e23a0-173">When you publish a self-contained application with the .NET Core 2.1 SDK (v 2.1.300), your application includes the latest serviced runtime version known by that SDK.</span></span> <span data-ttu-id="e23a0-174">Po uaktualnieniu do najnowszego sdk, można opublikować z najnowszą wersją środowiska uruchomieniowego .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e23a0-174">When you upgrade to the latest SDK, you'll publish with the latest .NET Core runtime version.</span></span> <span data-ttu-id="e23a0-175">Dotyczy to środowiska uruchomień .NET Core 1.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="e23a0-175">This applies for .NET Core 1.0 runtimes and later.</span></span>

<span data-ttu-id="e23a0-176">Samodzielne publikowanie opiera się na wersjach środowiska wykonawczego na NuGet.org. Nie trzeba mieć serviced runtime na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e23a0-176">Self-contained publishing relies on runtime versions on NuGet.org. You do not need to have the serviced runtime on your machine.</span></span>

<span data-ttu-id="e23a0-177">Za pomocą .NET Core 2.0 SDK, samodzielne aplikacje są publikowane w czasie wykonywania .NET Core 2.0.0, chyba że inna wersja jest określona za pośrednictwem `RuntimeFrameworkVersion` właściwości.</span><span class="sxs-lookup"><span data-stu-id="e23a0-177">Using the .NET Core 2.0 SDK, self-contained applications are published with the .NET Core 2.0.0 runtime unless a different version is specified via the `RuntimeFrameworkVersion` property.</span></span> <span data-ttu-id="e23a0-178">Dzięki temu nowemu zachowaniu nie trzeba już ustawiać tej właściwości, aby wybrać wyższą wersję środowiska uruchomieniowego dla aplikacji niezależnej.</span><span class="sxs-lookup"><span data-stu-id="e23a0-178">With this new behavior, you'll no longer need to set this property to select a higher runtime version for a self-contained application.</span></span> <span data-ttu-id="e23a0-179">Najprostszym podejściem w przyszłości jest zawsze publikować za pomocą .NET Core 2.1 SDK (v 2.1.300).</span><span class="sxs-lookup"><span data-stu-id="e23a0-179">The easiest approach going forward is to always publish with .NET Core 2.1 SDK (v 2.1.300).</span></span>

<span data-ttu-id="e23a0-180">Aby uzyskać więcej informacji, zobacz [Samodzielne wdrożenie uruchomieniowe rolki do przodu](../deploying/runtime-patch-selection.md).</span><span class="sxs-lookup"><span data-stu-id="e23a0-180">For more information, see [Self-contained deployment runtime roll forward](../deploying/runtime-patch-selection.md).</span></span>
## <a name="windows-compatibility-pack"></a><span data-ttu-id="e23a0-181">Pakiet zgodności systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e23a0-181">Windows Compatibility Pack</span></span>

<span data-ttu-id="e23a0-182">Po przekadaniu istniejącego kodu z programu .NET Framework do programu .NET Core można użyć [pakietu zgodności systemu Windows](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="e23a0-182">When you port existing code from the .NET Framework to .NET Core, you can use the [Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span> <span data-ttu-id="e23a0-183">Zapewnia dostęp do 20 000 więcej interfejsów API niż są dostępne w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e23a0-183">It provides access to 20,000 more APIs than are available in .NET Core.</span></span> <span data-ttu-id="e23a0-184">Te interfejsy API obejmują <xref:System.Drawing?displayProperty=nameWithType> typy <xref:System.Diagnostics.EventLog> w obszarze nazw, klasy, WMI, liczniki wydajności, usługi systemu Windows i typy rejestru systemu Windows i członków.</span><span class="sxs-lookup"><span data-stu-id="e23a0-184">These APIs include types in the <xref:System.Drawing?displayProperty=nameWithType> namespace, the <xref:System.Diagnostics.EventLog> class, WMI, Performance Counters, Windows Services, and the Windows registry types and members.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="e23a0-185">Ulepszenia kompilatora JIT</span><span class="sxs-lookup"><span data-stu-id="e23a0-185">JIT compiler improvements</span></span>

<span data-ttu-id="e23a0-186">.NET Core zawiera nową technologię kompilatora JIT o nazwie *kompilacji warstwowej* (znany również jako *optymalizacji adaptacyjnej),* które mogą znacznie zwiększyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="e23a0-186">.NET Core incorporates a new JIT compiler technology called *tiered compilation* (also known as *adaptive optimization*) that can significantly improve performance.</span></span> <span data-ttu-id="e23a0-187">Kompilacja warstwowa jest ustawieniem opt-in.</span><span class="sxs-lookup"><span data-stu-id="e23a0-187">Tiered compilation is an opt-in setting.</span></span>

<span data-ttu-id="e23a0-188">Jednym z ważnych zadań wykonywanych przez kompilator JIT jest optymalizacja wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="e23a0-188">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="e23a0-189">W przypadku mało używanych ścieżek kodu kompilator może jednak poświęcić więcej czasu na optymalizację kodu niż środowisko wykonawcze spędza uruchamianie nieoptymalizowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="e23a0-189">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends running unoptimized code.</span></span> <span data-ttu-id="e23a0-190">Kompilacja warstwowa wprowadza dwa etapy kompilacji JIT:</span><span class="sxs-lookup"><span data-stu-id="e23a0-190">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="e23a0-191">**Pierwsza warstwa**, która generuje kod tak szybko, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="e23a0-191">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="e23a0-192">**Druga warstwa**, która generuje zoptymalizowany kod dla tych metod, które są wykonywane często.</span><span class="sxs-lookup"><span data-stu-id="e23a0-192">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="e23a0-193">Druga warstwa kompilacji jest wykonywana równolegle w celu zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="e23a0-193">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="e23a0-194">Możesz zdecydować się na kompilację warstwową na jeden z dwóch sposobów.</span><span class="sxs-lookup"><span data-stu-id="e23a0-194">You can opt into tiered compilation in either of two ways.</span></span>

- <span data-ttu-id="e23a0-195">Aby użyć kompilacji warstwowej we wszystkich projektach korzystających z zestawu .NET Core 2.1 SDK, należy ustawić następującą zmienną środowiskową:</span><span class="sxs-lookup"><span data-stu-id="e23a0-195">To use tiered compilation in all projects that use the .NET Core 2.1 SDK, set the following environment variable:</span></span>

  ```console
  COMPlus_TieredCompilation="1"
  ```

- <span data-ttu-id="e23a0-196">Aby użyć kompilacji warstwowej na podstawie projektu, `<TieredCompilation>` dodaj `<PropertyGroup>` właściwość do sekcji pliku projektu MSBuild, zgodnie z poniższym przykładem:</span><span class="sxs-lookup"><span data-stu-id="e23a0-196">To use tiered compilation on a per-project basis, add the `<TieredCompilation>` property to the `<PropertyGroup>` section of the MSBuild project file, as the following example shows:</span></span>

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a><span data-ttu-id="e23a0-197">Zmiany api</span><span class="sxs-lookup"><span data-stu-id="e23a0-197">API changes</span></span>

### <a name="spant-and-memoryt"></a><span data-ttu-id="e23a0-198">`Span<T>` i `Memory<T>`</span><span class="sxs-lookup"><span data-stu-id="e23a0-198">`Span<T>` and `Memory<T>`</span></span>

<span data-ttu-id="e23a0-199">.NET Core 2.1 zawiera kilka nowych typów, które sprawiają, że praca z macierzami i innymi typami pamięci jest znacznie bardziej wydajna.</span><span class="sxs-lookup"><span data-stu-id="e23a0-199">.NET Core 2.1 includes some new types that make working with arrays and other types of memory much more efficient.</span></span> <span data-ttu-id="e23a0-200">Nowe typy obejmują:</span><span class="sxs-lookup"><span data-stu-id="e23a0-200">The new types include:</span></span>

- <span data-ttu-id="e23a0-201"><xref:System.Span%601?displayProperty=nameWithType>i <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e23a0-201"><xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="e23a0-202"><xref:System.Memory%601?displayProperty=nameWithType>i <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e23a0-202"><xref:System.Memory%601?displayProperty=nameWithType> and <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="e23a0-203">Bez tych typów podczas przekazywania takich elementów, jak część tablicy lub sekcji buforu pamięci, należy wykonać kopię niektórych części danych przed przekazaniem go do metody.</span><span class="sxs-lookup"><span data-stu-id="e23a0-203">Without these types, when passing such items as a portion of an array or a section of a memory buffer, you have to make a copy of some portion of the data before passing it to a method.</span></span> <span data-ttu-id="e23a0-204">Te typy zapewniają wirtualny widok tych danych, który eliminuje potrzebę dodatkowej alokacji pamięci i operacji kopiowania.</span><span class="sxs-lookup"><span data-stu-id="e23a0-204">These types provide a virtual view of that data that eliminates the need for the additional memory allocation and copy operations.</span></span>

<span data-ttu-id="e23a0-205">W poniższym <xref:System.Span%601> przykładzie <xref:System.Memory%601> użyto i wystąpienie, aby zapewnić widok wirtualny 10 elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="e23a0-205">The following example uses a <xref:System.Span%601> and <xref:System.Memory%601> instance to provide a virtual view of 10 elements of an array.</span></span>

[!code-csharp[Span\<T>](~/samples/snippets/core/whats-new/whats-new-in-21/csharp/program.cs)]

[!code-vb[Memory\<T>](~/samples/snippets/core/whats-new/whats-new-in-21/vb/program.vb)]

### <a name="brotli-compression"></a><span data-ttu-id="e23a0-206">Kompresja Brotli</span><span class="sxs-lookup"><span data-stu-id="e23a0-206">Brotli compression</span></span>

<span data-ttu-id="e23a0-207">.NET Core 2.1 dodaje obsługę kompresji i dekompresji Brotli.</span><span class="sxs-lookup"><span data-stu-id="e23a0-207">.NET Core 2.1 adds support for Brotli compression and decompression.</span></span> <span data-ttu-id="e23a0-208">Brotli to uniwersalny algorytm kompresji bezstratnych, który jest zdefiniowany w [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) i jest obsługiwany przez większość przeglądarek internetowych i głównych serwerów internetowych.</span><span class="sxs-lookup"><span data-stu-id="e23a0-208">Brotli is a general-purpose lossless compression algorithm that is defined in [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) and is supported by most web browsers and major web servers.</span></span> <span data-ttu-id="e23a0-209">Można użyć klasy opartej na <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> strumieniu lub <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> klasy <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> oparte na rozpiętości o wysokiej wydajności.</span><span class="sxs-lookup"><span data-stu-id="e23a0-209">You can use the stream-based <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> class or the high-performance span-based <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> and <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> classes.</span></span> <span data-ttu-id="e23a0-210">Poniższy przykład ilustruje <xref:System.IO.Compression.BrotliStream> kompresję z klasą:</span><span class="sxs-lookup"><span data-stu-id="e23a0-210">The following example illustrates compression with the <xref:System.IO.Compression.BrotliStream> class:</span></span>

[!code-csharp[Brotli compression](~/samples/snippets/core/whats-new/whats-new-in-21/csharp/brotli.cs#1)]

[!code-vb[Brotli compression](~/samples/snippets/core/whats-new/whats-new-in-21/vb/brotli.vb#1)]

<span data-ttu-id="e23a0-211">Zachowanie <xref:System.IO.Compression.BrotliStream> jest takie <xref:System.IO.Compression.DeflateStream> samo <xref:System.IO.Compression.GZipStream>jak i , co ułatwia konwersję kodu, który wywołuje te interfejsy API do <xref:System.IO.Compression.BrotliStream>.</span><span class="sxs-lookup"><span data-stu-id="e23a0-211">The <xref:System.IO.Compression.BrotliStream> behavior is the same as <xref:System.IO.Compression.DeflateStream> and <xref:System.IO.Compression.GZipStream>, which makes it easy to convert code that calls these APIs to <xref:System.IO.Compression.BrotliStream>.</span></span>

### <a name="new-cryptography-apis-and-cryptography-improvements"></a><span data-ttu-id="e23a0-212">Nowe interfejsy API kryptografii i ulepszenia kryptografii</span><span class="sxs-lookup"><span data-stu-id="e23a0-212">New cryptography APIs and cryptography improvements</span></span>

<span data-ttu-id="e23a0-213">Program .NET Core 2.1 zawiera liczne ulepszenia interfejsów API kryptografii:</span><span class="sxs-lookup"><span data-stu-id="e23a0-213">.NET Core 2.1 includes numerous enhancements to the cryptography APIs:</span></span>

- <span data-ttu-id="e23a0-214"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType>jest dostępny w pakiecie System.Security.Cryptography.Pkcs.</span><span class="sxs-lookup"><span data-stu-id="e23a0-214"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> is available in the System.Security.Cryptography.Pkcs package.</span></span> <span data-ttu-id="e23a0-215">Implementacja jest taka <xref:System.Security.Cryptography.Pkcs.SignedCms> sama jak klasa w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e23a0-215">The implementation is the same as the <xref:System.Security.Cryptography.Pkcs.SignedCms> class in the .NET Framework.</span></span>

- <span data-ttu-id="e23a0-216">Nowe przeciążenia <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> i <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> metody akceptują identyfikator algorytmu mieszania, aby umożliwić wywołującym uzyskanie wartości odcisku palca certyfikatu przy użyciu algorytmów innych niż SHA-1.</span><span class="sxs-lookup"><span data-stu-id="e23a0-216">New overloads of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> and <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> methods accept a hash algorithm identifier to enable callers to get certificate thumbprint values using algorithms other than SHA-1.</span></span>

- <span data-ttu-id="e23a0-217">Nowe <xref:System.Span%601>interfejsy API kryptografii opartej na kryptografii są dostępne do mieszania, HMAC, generowania liczb losowych kryptograficznych, generowania asymetrycznego podpisu, asymetrycznego przetwarzania podpisu i szyfrowania RSA.</span><span class="sxs-lookup"><span data-stu-id="e23a0-217">New <xref:System.Span%601>-based cryptography APIs are available for hashing, HMAC, cryptographic random number generation, asymmetric signature generation, asymmetric signature processing, and RSA encryption.</span></span>

- <span data-ttu-id="e23a0-218">Wydajność poprawiła <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> się o około 15% przy użyciu implementacji opartej <xref:System.Span%601>na</span><span class="sxs-lookup"><span data-stu-id="e23a0-218">The performance of <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> has improved by about 15% by using a <xref:System.Span%601>-based implementation.</span></span>

- <span data-ttu-id="e23a0-219">Nowa <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> klasa zawiera dwie nowe metody:</span><span class="sxs-lookup"><span data-stu-id="e23a0-219">The new <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> class includes two new methods:</span></span>

  - <span data-ttu-id="e23a0-220"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A>zajmuje ustaloną ilość czasu, aby powrócić do dwóch wejść o tej samej długości, co sprawia, że nadaje się do wykorzystania w weryfikacji kryptograficznej, aby uniknąć przyczyniania się do czasu informacji kanału bocznego.</span><span class="sxs-lookup"><span data-stu-id="e23a0-220"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> takes a fixed amount of time to return for any two inputs of the same length, which makes it suitable for use in cryptographic verification to avoid contributing to timing side-channel information.</span></span>

  - <span data-ttu-id="e23a0-221"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A>jest procedurą czyszczenia pamięci, których nie można zoptymalizować.</span><span class="sxs-lookup"><span data-stu-id="e23a0-221"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> is a memory-clearing routine that cannot be optimized.</span></span>

- <span data-ttu-id="e23a0-222">Metoda statyczna <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> wypełnia <xref:System.Span%601> wartości losowe.</span><span class="sxs-lookup"><span data-stu-id="e23a0-222">The static <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> method fills a <xref:System.Span%601> with random values.</span></span>

- <span data-ttu-id="e23a0-223">Jest <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> teraz obsługiwany w systemach Linux i macOS.</span><span class="sxs-lookup"><span data-stu-id="e23a0-223">The <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> is now supported on Linux and macOS.</span></span>

- <span data-ttu-id="e23a0-224">Elliptic-Curve Diffie-Hellman (ECDH) jest <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> teraz dostępny w rodzinie klas.</span><span class="sxs-lookup"><span data-stu-id="e23a0-224">Elliptic-Curve Diffie-Hellman (ECDH) is now available in the <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> class family.</span></span> <span data-ttu-id="e23a0-225">Powierzchnia jest taka sama jak w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e23a0-225">The surface area is the same as in the .NET Framework.</span></span>

- <span data-ttu-id="e23a0-226">Wystąpienie zwracane przez <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> można szyfrować lub odszyfrowywać za pomocą OAEP przy użyciu skrótu SHA-2, a także generować lub weryfikować podpisy przy użyciu RSA-PSS.</span><span class="sxs-lookup"><span data-stu-id="e23a0-226">The instance returned by <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> can encrypt or decrypt with OAEP using a SHA-2 digest, as well as generate or validate signatures using RSA-PSS.</span></span>

### <a name="sockets-improvements"></a><span data-ttu-id="e23a0-227">Ulepszenia gniazd</span><span class="sxs-lookup"><span data-stu-id="e23a0-227">Sockets improvements</span></span>

<span data-ttu-id="e23a0-228">Program .NET Core zawiera <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>nowy typ <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>i przepisany plik, który stanowi podstawę interfejsów API sieciowego wyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="e23a0-228">.NET Core includes a new type, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, and a rewritten <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, that form the basis of higher-level networking APIs.</span></span>  <span data-ttu-id="e23a0-229"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, na przykład, jest <xref:System.Net.Http.HttpClient> podstawą realizacji.</span><span class="sxs-lookup"><span data-stu-id="e23a0-229"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, for example, is the basis of the <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="e23a0-230">W poprzednich wersjach programu .NET Core interfejsy API wyższego poziomu były oparte na implementacjach sieci natywnych.</span><span class="sxs-lookup"><span data-stu-id="e23a0-230">In previous versions of .NET Core, higher-level APIs were based on native networking implementations.</span></span>

<span data-ttu-id="e23a0-231">Implementacja gniazd wprowadzona w .NET Core 2.1 ma wiele zalet:</span><span class="sxs-lookup"><span data-stu-id="e23a0-231">The sockets implementation introduced in .NET Core 2.1 has a number of advantages:</span></span>

- <span data-ttu-id="e23a0-232">Znaczna poprawa wydajności w porównaniu z poprzednią implementacją.</span><span class="sxs-lookup"><span data-stu-id="e23a0-232">A significant performance improvement when compared with the previous implementation.</span></span>

- <span data-ttu-id="e23a0-233">Eliminacja zależności platformy, co upraszcza wdrażanie i obsługę.</span><span class="sxs-lookup"><span data-stu-id="e23a0-233">Elimination of platform dependencies, which simplifies deployment and servicing.</span></span>

- <span data-ttu-id="e23a0-234">Spójne zachowanie na wszystkich platformach .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e23a0-234">Consistent behavior across all .NET Core platforms.</span></span>

<span data-ttu-id="e23a0-235"><xref:System.Net.Http.SocketsHttpHandler>jest domyślną implementacją w .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="e23a0-235"><xref:System.Net.Http.SocketsHttpHandler> is the default implementation in .NET Core 2.1.</span></span> <span data-ttu-id="e23a0-236">Można jednak skonfigurować aplikację do używania <xref:System.Net.Http.HttpClientHandler> starszej <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> klasy, wywołując metodę:</span><span class="sxs-lookup"><span data-stu-id="e23a0-236">However, you can configure your application to use the older <xref:System.Net.Http.HttpClientHandler> class by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method:</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", False)
```

<span data-ttu-id="e23a0-237">Można również użyć zmiennej środowiskowej, aby zrezygnować z <xref:System.Net.Http.SocketsHttpHandler>używania implementacji gniazd opartych na .</span><span class="sxs-lookup"><span data-stu-id="e23a0-237">You can also use an environment variable to opt out of using sockets implementations based on <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="e23a0-238">Aby to zrobić, `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` ustaw `false` na jedną lub 0.</span><span class="sxs-lookup"><span data-stu-id="e23a0-238">To do this, set the `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` to either `false` or 0.</span></span>

<span data-ttu-id="e23a0-239">W systemie Windows można również <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>wybrać użycie , który opiera <xref:System.Net.Http.SocketsHttpHandler> się na implementacji macierzystej <xref:System.Net.Http.HttpClient> lub klasy, przekazując wystąpienie klasy do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="e23a0-239">On Windows, you can also choose to use <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, which relies on a native implementation, or the <xref:System.Net.Http.SocketsHttpHandler> class by passing an instance of the class to the <xref:System.Net.Http.HttpClient> constructor.</span></span>

<span data-ttu-id="e23a0-240">W systemach Linux i macOS <xref:System.Net.Http.HttpClient> można konfigurować tylko na podstawie procesu.</span><span class="sxs-lookup"><span data-stu-id="e23a0-240">On Linux and macOS, you can only configure <xref:System.Net.Http.HttpClient> on a per-process basis.</span></span> <span data-ttu-id="e23a0-241">W systemie Linux należy wdrożyć [libcurl,](https://curl.haxx.se/libcurl/) jeśli <xref:System.Net.Http.HttpClient> chcesz użyć starej implementacji.</span><span class="sxs-lookup"><span data-stu-id="e23a0-241">On Linux, you need to deploy [libcurl](https://curl.haxx.se/libcurl/) if you want to use the old <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="e23a0-242">(Jest zainstalowany z .NET Core 2.0.)</span><span class="sxs-lookup"><span data-stu-id="e23a0-242">(It is installed with .NET Core 2.0.)</span></span>

### <a name="breaking-changes"></a><span data-ttu-id="e23a0-243">Fundamentalne zmiany</span><span class="sxs-lookup"><span data-stu-id="e23a0-243">Breaking changes</span></span>

<span data-ttu-id="e23a0-244">Aby uzyskać informacje na temat zmiany podziału, zobacz [Przerywanie zmian migracji z wersji 2.0 do 2.1](../compatibility/2.0-2.1.md).</span><span class="sxs-lookup"><span data-stu-id="e23a0-244">For information about breaking changes, see [Breaking changes for migration from version 2.0 to 2.1](../compatibility/2.0-2.1.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e23a0-245">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e23a0-245">See also</span></span>

- [<span data-ttu-id="e23a0-246">Co nowego w programie .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="e23a0-246">What's new in .NET Core 3.1</span></span>](dotnet-core-3-1.md)
- [<span data-ttu-id="e23a0-247">Nowe funkcje w EF Core 2.1</span><span class="sxs-lookup"><span data-stu-id="e23a0-247">New features in EF Core 2.1</span></span>](/ef/core/what-is-new/ef-core-2.1)
- [<span data-ttu-id="e23a0-248">Co nowego w ASP.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="e23a0-248">What's new in ASP.NET Core 2.1</span></span>](/aspnet/core/aspnetcore-2.1)
