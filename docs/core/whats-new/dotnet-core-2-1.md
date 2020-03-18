---
title: Co nowego w programie .NET Core 2.1
description: Dowiedz się więcej o nowych funkcjach, które można znaleźć w .NET Core 2.1.
dev_langs:
- csharp
- vb
ms.date: 10/10/2018
ms.openlocfilehash: 54ace52fc6a8f4614c1f762b65453979bcb92c7a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398868"
---
# <a name="whats-new-in-net-core-21"></a><span data-ttu-id="8f8c7-103">Co nowego w programie .NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="8f8c7-103">What's new in .NET Core 2.1</span></span>

<span data-ttu-id="8f8c7-104">.NET Core 2.1 zawiera ulepszenia i nowe funkcje w następujących obszarach:</span><span class="sxs-lookup"><span data-stu-id="8f8c7-104">.NET Core 2.1 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="8f8c7-105">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="8f8c7-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="8f8c7-106">Przewiń do przodu</span><span class="sxs-lookup"><span data-stu-id="8f8c7-106">Roll forward</span></span>](#roll-forward)
- [<span data-ttu-id="8f8c7-107">Wdrożenie</span><span class="sxs-lookup"><span data-stu-id="8f8c7-107">Deployment</span></span>](#deployment)
- [<span data-ttu-id="8f8c7-108">Pakiet zgodności systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8f8c7-108">Windows Compatibility Pack</span></span>](#windows-compatibility-pack)
- [<span data-ttu-id="8f8c7-109">Ulepszenia kompilacji JIT</span><span class="sxs-lookup"><span data-stu-id="8f8c7-109">JIT compilation improvements</span></span>](#jit-compiler-improvements)
- [<span data-ttu-id="8f8c7-110">Zmiany interfejsu API</span><span class="sxs-lookup"><span data-stu-id="8f8c7-110">API changes</span></span>](#api-changes)

## <a name="tooling"></a><span data-ttu-id="8f8c7-111">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="8f8c7-111">Tooling</span></span>

<span data-ttu-id="8f8c7-112">Zestaw SDK .NET Core 2.1 (v 2.1.300), oprzyrządowanie dołączone do .NET Core 2.1, zawiera następujące zmiany i ulepszenia:</span><span class="sxs-lookup"><span data-stu-id="8f8c7-112">The .NET Core 2.1 SDK (v 2.1.300), the tooling included with .NET Core 2.1, includes the following changes and enhancements:</span></span>

### <a name="build-performance-improvements"></a><span data-ttu-id="8f8c7-113">Tworzenie ulepszeń wydajności</span><span class="sxs-lookup"><span data-stu-id="8f8c7-113">Build performance improvements</span></span>

<span data-ttu-id="8f8c7-114">Głównym celem .NET Core 2.1 jest poprawa wydajności w czasie kompilacji, szczególnie w przypadku kompilacji przyrostowych.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-114">A major focus of .NET Core 2.1 is improving build-time performance, particularly for incremental builds.</span></span> <span data-ttu-id="8f8c7-115">Te ulepszenia wydajności dotyczą zarówno kompilacji `dotnet build` wiersza polecenia przy użyciu i do kompilacji w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-115">These performance improvements apply to both command-line builds using `dotnet build` and to builds in Visual Studio.</span></span> <span data-ttu-id="8f8c7-116">Niektóre poszczególne obszary poprawy obejmują:</span><span class="sxs-lookup"><span data-stu-id="8f8c7-116">Some individual areas of improvement include:</span></span>

- <span data-ttu-id="8f8c7-117">W przypadku rozpoznawania zasobów pakietu rozpoznawanie tylko zasobów używanych przez kompilację, a nie wszystkie zasoby.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-117">For package asset resolution, resolving only assets used by a build rather than all assets.</span></span>

- <span data-ttu-id="8f8c7-118">Buforowanie odwołań do zestawu.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-118">Caching of assembly references.</span></span>

- <span data-ttu-id="8f8c7-119">Korzystanie z długotrwałych serwerów kompilacji SDK, które `dotnet build` są procesami, które obejmują poszczególne wywołania.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-119">Use of long-running SDK build servers, which are processes that span across individual `dotnet build` invocations.</span></span> <span data-ttu-id="8f8c7-120">Eliminują one konieczność JIT-kompilacji `dotnet build` dużych bloków kodu za każdym razem jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-120">They eliminate the need to JIT-compile large blocks of code every time `dotnet build` is run.</span></span> <span data-ttu-id="8f8c7-121">Procesy serwera kompilacji można automatycznie zakończyć za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="8f8c7-121">Build server processes can be automatically terminated with the following command:</span></span>

   ```dotnetcli
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a><span data-ttu-id="8f8c7-122">Nowe polecenia wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="8f8c7-122">New CLI commands</span></span>

<span data-ttu-id="8f8c7-123">Wiele narzędzi, które były dostępne tylko na `DotnetCliToolReference` podstawie projektu przy użyciu są teraz dostępne jako część .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-123">A number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="8f8c7-124">Do tych narzędzi należą:</span><span class="sxs-lookup"><span data-stu-id="8f8c7-124">These tools include:</span></span>

- <span data-ttu-id="8f8c7-125">`dotnet watch`udostępnia obserwatora systemu plików, który czeka na zmianę pliku przed wykonaniem wyznaczonego zestawu poleceń.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-125">`dotnet watch` provides a file system watcher that waits for a file to change before executing a designated set of commands.</span></span> <span data-ttu-id="8f8c7-126">Na przykład następujące polecenie automatycznie odbudowuje bieżący projekt i generuje pełne dane wyjściowe, gdy zmienia się plik:</span><span class="sxs-lookup"><span data-stu-id="8f8c7-126">For example, the following command automatically rebuilds the current project and generates verbose output whenever a file in it changes:</span></span>

   ```dotnetcli
   dotnet watch -- --verbose build
   ```

   <span data-ttu-id="8f8c7-127">Zwróć `--` uwagę na `--verbose` opcję poprzedzanącą tę opcję.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-127">Note the `--` option that precedes the `--verbose` option.</span></span> <span data-ttu-id="8f8c7-128">To rozgranicza opcje przekazywane `dotnet watch` bezpośrednio do polecenia z argumentów, które są przekazywane do procesu podrzędne. `dotnet`</span><span class="sxs-lookup"><span data-stu-id="8f8c7-128">It delimits the options passed directly to the `dotnet watch` command from the arguments that are passed to the child `dotnet` process.</span></span> <span data-ttu-id="8f8c7-129">Bez niego `--verbose` opcja ma zastosowanie `dotnet watch` do polecenia, a `dotnet build` nie polecenia.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-129">Without it, the `--verbose` option applies to the `dotnet watch` command, not the `dotnet build` command.</span></span>
  
   <span data-ttu-id="8f8c7-130">Aby uzyskać więcej informacji, zobacz [Opracowywanie aplikacji ASP.NET Core przy użyciu zegarka dotnet](/aspnet/core/tutorials/dotnet-watch).</span><span class="sxs-lookup"><span data-stu-id="8f8c7-130">For more information, see [Develop ASP.NET Core apps using dotnet watch](/aspnet/core/tutorials/dotnet-watch).</span></span>

- <span data-ttu-id="8f8c7-131">`dotnet dev-certs`generuje certyfikaty używane podczas opracowywania w ASP.NET podstawowych aplikacji i zarządza nimi.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-131">`dotnet dev-certs` generates and manages certificates used during development in ASP.NET Core applications.</span></span>

- <span data-ttu-id="8f8c7-132">`dotnet user-secrets`zarządza kluczami tajnymi w tajnym magazynie użytkownika w ASP.NET aplikacji Core.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-132">`dotnet user-secrets` manages the secrets in a user secret store in ASP.NET Core applications.</span></span>

- <span data-ttu-id="8f8c7-133">`dotnet sql-cache`tworzy tabelę i indeksy w bazie danych programu Microsoft SQL Server, która ma być używana do buforowania rozproszonego.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-133">`dotnet sql-cache` creates a table and indexes in a Microsoft SQL Server database to be used for distributed caching.</span></span>

- <span data-ttu-id="8f8c7-134">`dotnet ef`jest narzędziem do zarządzania <xref:Microsoft.EntityFrameworkCore.DbContext> bazami danych, obiektami i migracjami w podstawowych aplikacjach entity framework.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-134">`dotnet ef` is a tool for managing databases, <xref:Microsoft.EntityFrameworkCore.DbContext> objects, and migrations in Entity Framework Core applications.</span></span> <span data-ttu-id="8f8c7-135">Aby uzyskać więcej informacji, zobacz [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="8f8c7-135">For more information, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

### <a name="global-tools"></a><span data-ttu-id="8f8c7-136">Narzędzia globalne</span><span class="sxs-lookup"><span data-stu-id="8f8c7-136">Global Tools</span></span>

<span data-ttu-id="8f8c7-137">.NET Core 2.1 obsługuje *narzędzia globalne* — czyli niestandardowe narzędzia, które są dostępne globalnie z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-137">.NET Core 2.1 supports *Global Tools* -- that is, custom tools that are available globally from the command line.</span></span> <span data-ttu-id="8f8c7-138">Model rozszerzalności w poprzednich wersjach programu .NET Core udostępnił niestandardowe narzędzia `DotnetCliToolReference`na podstawie poprzecznych projektów tylko przy użyciu .</span><span class="sxs-lookup"><span data-stu-id="8f8c7-138">The extensibility model in previous versions of .NET Core made custom tools available on a per project basis only by using `DotnetCliToolReference`.</span></span>

<span data-ttu-id="8f8c7-139">Aby zainstalować narzędzie globalne, należy użyć polecenia [instalowania narzędzia dotnet.](../tools/dotnet-tool-install.md)</span><span class="sxs-lookup"><span data-stu-id="8f8c7-139">To install a Global Tool, you use the [dotnet tool install](../tools/dotnet-tool-install.md) command.</span></span> <span data-ttu-id="8f8c7-140">Przykład:</span><span class="sxs-lookup"><span data-stu-id="8f8c7-140">For example:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="8f8c7-141">Po zainstalowaniu narzędzie można uruchomić z wiersza polecenia, określając nazwę narzędzia.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-141">Once installed, the tool can be run from the command line by specifying the tool name.</span></span> <span data-ttu-id="8f8c7-142">Aby uzyskać więcej informacji, zobacz [omówienie .NET Core Global Tools](../tools/global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="8f8c7-142">For more information, see [.NET Core Global Tools overview](../tools/global-tools.md).</span></span>

### <a name="tool-management-with-the-dotnet-tool-command"></a><span data-ttu-id="8f8c7-143">Zarządzanie narzędziami `dotnet tool` za pomocą polecenia</span><span class="sxs-lookup"><span data-stu-id="8f8c7-143">Tool management with the `dotnet tool` command</span></span>

<span data-ttu-id="8f8c7-144">W sdk .NET Core 2.1 wszystkie `dotnet tool` operacje narzędzi używają polecenia.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-144">In .NET Core 2.1 SDK, all tools operations use the `dotnet tool` command.</span></span> <span data-ttu-id="8f8c7-145">Dostępne są następujące opcje:</span><span class="sxs-lookup"><span data-stu-id="8f8c7-145">The following options are available:</span></span>

- <span data-ttu-id="8f8c7-146">[`dotnet tool install`](../tools/dotnet-tool-install.md), aby zainstalować narzędzie.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) to install a tool.</span></span>

- <span data-ttu-id="8f8c7-147">[`dotnet tool update`](../tools/dotnet-tool-update.md), aby odinstalować i ponownie zainstalować narzędzie, które skutecznie je aktualizuje.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) to uninstall and reinstall a tool, which effectively updates it.</span></span>

- <span data-ttu-id="8f8c7-148">[`dotnet tool list`](../tools/dotnet-tool-list.md), aby wyświetlić listę aktualnie zainstalowanych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) to list currently installed tools.</span></span>

- <span data-ttu-id="8f8c7-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md), aby odinstalować aktualnie zainstalowane narzędzia.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) to uninstall currently installed tools.</span></span>

## <a name="roll-forward"></a><span data-ttu-id="8f8c7-150">Przewiń do przodu</span><span class="sxs-lookup"><span data-stu-id="8f8c7-150">Roll forward</span></span>

<span data-ttu-id="8f8c7-151">Wszystkie aplikacje .NET Core, począwszy od .NET Core 2.0, są automatycznie przerzucane do najnowszej *wersji pomocniczej* zainstalowanej w systemie.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-151">All .NET Core applications starting with .NET Core 2.0 automatically roll forward to the latest *minor version* installed on a system.</span></span>

<span data-ttu-id="8f8c7-152">Począwszy od .NET Core 2.0, jeśli wersja programu .NET Core, w której została zbudowana aplikacja, nie jest obecna w czasie wykonywania, aplikacja jest automatycznie uruchamiana względem najnowszej zainstalowanej *wersji pomocniczej* programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-152">Starting with .NET Core 2.0, if the version of .NET Core that an application was built with is not present at runtime, the application automatically runs against the latest installed *minor version* of .NET Core.</span></span> <span data-ttu-id="8f8c7-153">Innymi słowy, jeśli aplikacja jest zbudowana z .NET Core 2.0, a .NET Core 2.0 nie jest obecny w systemie hosta, ale .NET Core 2.1 jest, aplikacja jest uruchamiana z .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-153">In other words, if an application is built with .NET Core 2.0, and .NET Core 2.0 is not present on the host system but .NET Core 2.1 is, the application runs with .NET Core 2.1.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8f8c7-154">To zachowanie roll-forward nie ma zastosowania do wersji zapoznawczych.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-154">This roll-forward behavior doesn't apply to preview releases.</span></span> <span data-ttu-id="8f8c7-155">Domyślnie nie ma zastosowania do głównych wersji, ale można to zmienić za pomocą poniższych ustawień.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-155">By default, it also doesn't apply to major releases, but this can be changed with the settings below.</span></span>

<span data-ttu-id="8f8c7-156">To zachowanie można zmodyfikować, zmieniając ustawienie roll-forward na nie kandydata udostępnionej struktury.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-156">You can modify this behavior by changing the setting for the roll-forward on no candidate shared framework.</span></span> <span data-ttu-id="8f8c7-157">Dostępne ustawienia to:</span><span class="sxs-lookup"><span data-stu-id="8f8c7-157">The available settings are:</span></span>

- <span data-ttu-id="8f8c7-158">`0`- wyłącz zachowanie wersji pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-158">`0` - disable minor version roll-forward behavior.</span></span> <span data-ttu-id="8f8c7-159">Dzięki temu ustawieniu aplikacja stworzona dla .NET Core 2.0.0 zostanie przewiona do pliku .NET Core 2.0.1, ale nie do .NET Core 2.2.0 lub .NET Core 3.0.0.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-159">With this setting, an application built for .NET Core 2.0.0 will roll forward to .NET Core 2.0.1, but not to .NET Core 2.2.0 or .NET Core 3.0.0.</span></span>
- <span data-ttu-id="8f8c7-160">`1`- włączyć zachowanie wersji pomocniczej roll-forward.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-160">`1` - enable minor version roll-forward behavior.</span></span> <span data-ttu-id="8f8c7-161">Jest to wartość domyślna dla ustawienia.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-161">This is the default value for the setting.</span></span> <span data-ttu-id="8f8c7-162">Dzięki temu ustawieniu aplikacja stworzona dla .NET Core 2.0.0 będzie przerzucać dalej do .NET Core 2.0.1 lub .NET Core 2.2.0, w zależności od tego, który z nich jest zainstalowany, ale nie będzie przerzucać dalej do .NET Core 3.0.0.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-162">With this setting, an application built for .NET Core 2.0.0 will roll forward to either .NET Core 2.0.1 or .NET Core 2.2.0, depending on which one is installed, but it will not roll forward to .NET Core 3.0.0.</span></span>
- <span data-ttu-id="8f8c7-163">`2`- włączyć zachowanie roll-forward wersji pomocniczej i głównej.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-163">`2` - enable minor and major version roll-forward behavior.</span></span> <span data-ttu-id="8f8c7-164">Jeśli zestaw, nawet różne wersje główne są brane pod uwagę, więc aplikacja zbudowana dla .NET Core 2.0.0 będzie przewijać do przodu do .NET Core 3.0.0.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-164">If set, even different major versions are considered, so an application built for .NET Core 2.0.0 will roll forward to .NET Core 3.0.0.</span></span>

<span data-ttu-id="8f8c7-165">To ustawienie można zmodyfikować na trzy sposoby:</span><span class="sxs-lookup"><span data-stu-id="8f8c7-165">You can modify this setting in any of three ways:</span></span>

- <span data-ttu-id="8f8c7-166">Ustaw `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` zmienną środowiskową na żądaną wartość.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-166">Set the `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` environment variable to the desired value.</span></span>

- <span data-ttu-id="8f8c7-167">Dodaj następujący wiersz z żądaną wartością do pliku *.runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="8f8c7-167">Add the following line with the desired value to the *.runtimeconfig.json* file:</span></span>

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- <span data-ttu-id="8f8c7-168">W przypadku korzystania z [polecenia CLI .NET Core](../tools/index.md)dodaj następującą opcję `run`z żądaną wartością do polecenia .NET Core, takiego jak:</span><span class="sxs-lookup"><span data-stu-id="8f8c7-168">When using the [.NET Core CLI](../tools/index.md), add the following option with the desired value to a .NET Core command such as `run`:</span></span>

   ```dotnetcli
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

<span data-ttu-id="8f8c7-169">Patch version roll forward jest niezależna od tego ustawienia i odbywa się po zastosowaniu potencjalnego zastosowania rzutu do przodu wersji pomocniczej lub głównej.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-169">Patch version roll forward is independent of this setting and is done after any potential minor or major version roll forward is applied.</span></span>

## <a name="deployment"></a><span data-ttu-id="8f8c7-170">Wdrożenie</span><span class="sxs-lookup"><span data-stu-id="8f8c7-170">Deployment</span></span>

### <a name="self-contained-application-servicing"></a><span data-ttu-id="8f8c7-171">Samodzielna obsługa aplikacji</span><span class="sxs-lookup"><span data-stu-id="8f8c7-171">Self-contained application servicing</span></span>

<span data-ttu-id="8f8c7-172">`dotnet publish`teraz publikuje niezależne aplikacje z wersją usługi runtime.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-172">`dotnet publish` now publishes self-contained applications with a serviced runtime version.</span></span> <span data-ttu-id="8f8c7-173">Podczas publikowania niezależnej aplikacji z .NET Core 2.1 SDK (v 2.1.300), aplikacja zawiera najnowszą wersję usługi uruchomieniowej znany przez ten zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-173">When you publish a self-contained application with the .NET Core 2.1 SDK (v 2.1.300), your application includes the latest serviced runtime version known by that SDK.</span></span> <span data-ttu-id="8f8c7-174">Po uaktualnieniu do najnowszego sdk, zostanie opublikowany z najnowszą wersją programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-174">When you upgrade to the latest SDK, you'll publish with the latest .NET Core runtime version.</span></span> <span data-ttu-id="8f8c7-175">Dotyczy to .NET Core 1.0 w czasie i nowszych.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-175">This applies for .NET Core 1.0 runtimes and later.</span></span>

<span data-ttu-id="8f8c7-176">Niezależne publikowanie opiera się na wersjach czasu wykonywania na NuGet.org. Nie trzeba mieć serviced runtime na komputerze.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-176">Self-contained publishing relies on runtime versions on NuGet.org. You do not need to have the serviced runtime on your machine.</span></span>

<span data-ttu-id="8f8c7-177">Przy użyciu .NET Core 2.0 SDK, niezależne aplikacje są publikowane w czasie wykonywania .NET Core 2.0.0, chyba że inna wersja jest określona za pośrednictwem `RuntimeFrameworkVersion` właściwości.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-177">Using the .NET Core 2.0 SDK, self-contained applications are published with the .NET Core 2.0.0 runtime unless a different version is specified via the `RuntimeFrameworkVersion` property.</span></span> <span data-ttu-id="8f8c7-178">Dzięki temu nowemu zachowaniu nie trzeba już ustawiać tej właściwości, aby wybrać wyższą wersję czasu wykonywania dla niezależnej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-178">With this new behavior, you'll no longer need to set this property to select a higher runtime version for a self-contained application.</span></span> <span data-ttu-id="8f8c7-179">Najprostszym podejściem w przyszłości jest zawsze publikowanie za pomocą .NET Core 2.1 SDK (v 2.1.300).</span><span class="sxs-lookup"><span data-stu-id="8f8c7-179">The easiest approach going forward is to always publish with .NET Core 2.1 SDK (v 2.1.300).</span></span>

<span data-ttu-id="8f8c7-180">Aby uzyskać więcej informacji, zobacz Samodzielne wdrażanie [runtime roll forward](../deploying/runtime-patch-selection.md).</span><span class="sxs-lookup"><span data-stu-id="8f8c7-180">For more information, see [Self-contained deployment runtime roll forward](../deploying/runtime-patch-selection.md).</span></span>
## <a name="windows-compatibility-pack"></a><span data-ttu-id="8f8c7-181">Pakiet zgodności systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8f8c7-181">Windows Compatibility Pack</span></span>

<span data-ttu-id="8f8c7-182">Podczas przenoszenia istniejącego kodu z platformy .NET Framework do programu .NET Core można użyć [pakietu zgodności systemu Windows](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="8f8c7-182">When you port existing code from the .NET Framework to .NET Core, you can use the [Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span> <span data-ttu-id="8f8c7-183">Zapewnia dostęp do 20 000 więcej interfejsów API niż są dostępne w .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-183">It provides access to 20,000 more APIs than are available in .NET Core.</span></span> <span data-ttu-id="8f8c7-184">Te interfejsy API <xref:System.Drawing?displayProperty=nameWithType> obejmują typy <xref:System.Diagnostics.EventLog> w obszarze nazw, klasie, WMI, licznikach wydajności, usługach systemu Windows oraz typach i członkach rejestru systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-184">These APIs include types in the <xref:System.Drawing?displayProperty=nameWithType> namespace, the <xref:System.Diagnostics.EventLog> class, WMI, Performance Counters, Windows Services, and the Windows registry types and members.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="8f8c7-185">Ulepszenia kompilatora JIT</span><span class="sxs-lookup"><span data-stu-id="8f8c7-185">JIT compiler improvements</span></span>

<span data-ttu-id="8f8c7-186">.NET Core zawiera nową technologię kompilatora JIT o nazwie *kompilacja warstwowa* (znana również jako *optymalizacja adaptacyjna),* która może znacznie zwiększyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-186">.NET Core incorporates a new JIT compiler technology called *tiered compilation* (also known as *adaptive optimization*) that can significantly improve performance.</span></span> <span data-ttu-id="8f8c7-187">Kompilacja warstwowa jest ustawieniem opt-in.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-187">Tiered compilation is an opt-in setting.</span></span>

<span data-ttu-id="8f8c7-188">Jednym z ważnych zadań wykonywanych przez kompilator JIT jest optymalizacja wykonania kodu.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-188">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="8f8c7-189">W przypadku mało używanych ścieżek kodu kompilator może poświęcić więcej czasu na optymalizację kodu niż czas wykonywania spędza uruchomiony niezoptymalizowany kod.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-189">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends running unoptimized code.</span></span> <span data-ttu-id="8f8c7-190">Kompilacja warstwowa wprowadza dwa etapy kompilacji JIT:</span><span class="sxs-lookup"><span data-stu-id="8f8c7-190">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="8f8c7-191">**Pierwsza warstwa**, która generuje kod tak szybko, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-191">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="8f8c7-192">**Druga warstwa**, która generuje zoptymalizowany kod dla tych metod, które są często wykonywane.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-192">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="8f8c7-193">Druga warstwa kompilacji jest wykonywana równolegle w celu zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-193">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="8f8c7-194">Możesz zdecydować się na kompilację warstwową na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-194">You can opt into tiered compilation in either of two ways.</span></span>

- <span data-ttu-id="8f8c7-195">Aby użyć kompilacji warstwowej we wszystkich projektach korzystających z zestawu SDK .NET Core 2.1, ustaw następującą zmienną środowiskową:</span><span class="sxs-lookup"><span data-stu-id="8f8c7-195">To use tiered compilation in all projects that use the .NET Core 2.1 SDK, set the following environment variable:</span></span>

  ```console
  COMPlus_TieredCompilation="1"
  ```

- <span data-ttu-id="8f8c7-196">Aby użyć kompilacji warstwowej dla połów dla pojęć projektu, dodaj `<TieredCompilation>` właściwość do `<PropertyGroup>` sekcji pliku projektu MSBuild, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="8f8c7-196">To use tiered compilation on a per-project basis, add the `<TieredCompilation>` property to the `<PropertyGroup>` section of the MSBuild project file, as the following example shows:</span></span>

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a><span data-ttu-id="8f8c7-197">Zmiany interfejsu API</span><span class="sxs-lookup"><span data-stu-id="8f8c7-197">API changes</span></span>

### <a name="spant-and-memoryt"></a><span data-ttu-id="8f8c7-198">`Span<T>` i `Memory<T>`</span><span class="sxs-lookup"><span data-stu-id="8f8c7-198">`Span<T>` and `Memory<T>`</span></span>

<span data-ttu-id="8f8c7-199">.NET Core 2.1 zawiera kilka nowych typów, które sprawiają, że praca z tablicami i innymi typami pamięci jest znacznie bardziej wydajna.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-199">.NET Core 2.1 includes some new types that make working with arrays and other types of memory much more efficient.</span></span> <span data-ttu-id="8f8c7-200">Nowe typy obejmują:</span><span class="sxs-lookup"><span data-stu-id="8f8c7-200">The new types include:</span></span>

- <span data-ttu-id="8f8c7-201"><xref:System.Span%601?displayProperty=nameWithType>i <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-201"><xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="8f8c7-202"><xref:System.Memory%601?displayProperty=nameWithType>i <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-202"><xref:System.Memory%601?displayProperty=nameWithType> and <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="8f8c7-203">Bez tych typów podczas przekazywania takich elementów jako część tablicy lub sekcji buforu pamięci, należy wykonać kopię niektórych części danych przed przekazaniem go do metody.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-203">Without these types, when passing such items as a portion of an array or a section of a memory buffer, you have to make a copy of some portion of the data before passing it to a method.</span></span> <span data-ttu-id="8f8c7-204">Te typy zapewniają wirtualny widok tych danych, który eliminuje potrzebę dodatkowych operacji alokacji i kopiowania pamięci.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-204">These types provide a virtual view of that data that eliminates the need for the additional memory allocation and copy operations.</span></span>

<span data-ttu-id="8f8c7-205">W poniższym <xref:System.Span%601> przykładzie <xref:System.Memory%601> użyto wystąpienia i wystąpienie, aby zapewnić widok wirtualny 10 elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-205">The following example uses a <xref:System.Span%601> and <xref:System.Memory%601> instance to provide a virtual view of 10 elements of an array.</span></span>

[!code-csharp[Span\<T>](~/samples/snippets/core/whats-new/whats-new-in-21/csharp/program.cs)]

[!code-vb[Memory\<T>](~/samples/snippets/core/whats-new/whats-new-in-21/vb/program.vb)]

### <a name="brotli-compression"></a><span data-ttu-id="8f8c7-206">Kompresja Brotli</span><span class="sxs-lookup"><span data-stu-id="8f8c7-206">Brotli compression</span></span>

<span data-ttu-id="8f8c7-207">.NET Core 2.1 dodaje obsługę kompresji i dekompresji Brotli.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-207">.NET Core 2.1 adds support for Brotli compression and decompression.</span></span> <span data-ttu-id="8f8c7-208">Brotli jest uniwersalnym algorytmem kompresji bezstratnej, który jest zdefiniowany w [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) i jest obsługiwany przez większość przeglądarek internetowych i głównych serwerów internetowych.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-208">Brotli is a general-purpose lossless compression algorithm that is defined in [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) and is supported by most web browsers and major web servers.</span></span> <span data-ttu-id="8f8c7-209">Można użyć klasy opartej <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> na strumieniu lub wysokiej <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> wydajności <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> span oparte i klas.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-209">You can use the stream-based <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> class or the high-performance span-based <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> and <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> classes.</span></span> <span data-ttu-id="8f8c7-210">W poniższym przykładzie przedstawiono <xref:System.IO.Compression.BrotliStream> kompresji z klasą:</span><span class="sxs-lookup"><span data-stu-id="8f8c7-210">The following example illustrates compression with the <xref:System.IO.Compression.BrotliStream> class:</span></span>

[!code-csharp[Brotli compression](~/samples/snippets/core/whats-new/whats-new-in-21/csharp/brotli.cs#1)]

[!code-vb[Brotli compression](~/samples/snippets/core/whats-new/whats-new-in-21/vb/brotli.vb#1)]

<span data-ttu-id="8f8c7-211">Zachowanie <xref:System.IO.Compression.BrotliStream> jest takie <xref:System.IO.Compression.DeflateStream> samo <xref:System.IO.Compression.GZipStream>jak i , co ułatwia konwertowanie <xref:System.IO.Compression.BrotliStream>kodu, który wywołuje te interfejsy API do .</span><span class="sxs-lookup"><span data-stu-id="8f8c7-211">The <xref:System.IO.Compression.BrotliStream> behavior is the same as <xref:System.IO.Compression.DeflateStream> and <xref:System.IO.Compression.GZipStream>, which makes it easy to convert code that calls these APIs to <xref:System.IO.Compression.BrotliStream>.</span></span>

### <a name="new-cryptography-apis-and-cryptography-improvements"></a><span data-ttu-id="8f8c7-212">Nowe interfejsy API kryptografii i ulepszenia kryptografii</span><span class="sxs-lookup"><span data-stu-id="8f8c7-212">New cryptography APIs and cryptography improvements</span></span>

<span data-ttu-id="8f8c7-213">.NET Core 2.1 zawiera wiele ulepszeń interfejsów API kryptografii:</span><span class="sxs-lookup"><span data-stu-id="8f8c7-213">.NET Core 2.1 includes numerous enhancements to the cryptography APIs:</span></span>

- <span data-ttu-id="8f8c7-214"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType>jest dostępny w pakiecie System.Security.Cryptography.Pkcs.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-214"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> is available in the System.Security.Cryptography.Pkcs package.</span></span> <span data-ttu-id="8f8c7-215">Implementacja jest taka <xref:System.Security.Cryptography.Pkcs.SignedCms> sama jak klasy w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-215">The implementation is the same as the <xref:System.Security.Cryptography.Pkcs.SignedCms> class in the .NET Framework.</span></span>

- <span data-ttu-id="8f8c7-216">Nowe przeciążenia <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> i metody akceptują identyfikator algorytmu mieszania, aby umożliwić wywołującym uzyskanie wartości odcisku palca certyfikatu przy użyciu algorytmów innych niż SHA-1.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-216">New overloads of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> and <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> methods accept a hash algorithm identifier to enable callers to get certificate thumbprint values using algorithms other than SHA-1.</span></span>

- <span data-ttu-id="8f8c7-217">Nowe <xref:System.Span%601>interfejsy API kryptografii są dostępne do mieszania, HMAC, kryptograficznego generowania liczb losowych, asymetrycznego generowania podpisów, asymetrycznego przetwarzania podpisów i szyfrowania RSA.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-217">New <xref:System.Span%601>-based cryptography APIs are available for hashing, HMAC, cryptographic random number generation, asymmetric signature generation, asymmetric signature processing, and RSA encryption.</span></span>

- <span data-ttu-id="8f8c7-218">Wydajność <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> poprawiła się o około 15% <xref:System.Span%601>przy użyciu implementacji opartej na.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-218">The performance of <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> has improved by about 15% by using a <xref:System.Span%601>-based implementation.</span></span>

- <span data-ttu-id="8f8c7-219">Nowa <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> klasa zawiera dwie nowe metody:</span><span class="sxs-lookup"><span data-stu-id="8f8c7-219">The new <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> class includes two new methods:</span></span>

  - <span data-ttu-id="8f8c7-220"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A>zajmuje stałą ilość czasu, aby powrócić do dwóch wejść o tej samej długości, co sprawia, że nadaje się do wykorzystania w weryfikacji kryptograficznej, aby uniknąć przyczyniania się do informacji o czasie kanału bocznego.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-220"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> takes a fixed amount of time to return for any two inputs of the same length, which makes it suitable for use in cryptographic verification to avoid contributing to timing side-channel information.</span></span>

  - <span data-ttu-id="8f8c7-221"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A>jest procedurą oczyszczania pamięci, która nie może być zoptymalizowana.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-221"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> is a memory-clearing routine that cannot be optimized.</span></span>

- <span data-ttu-id="8f8c7-222">Metoda <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> statyczna wypełnia <xref:System.Span%601> wartość losową.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-222">The static <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> method fills a <xref:System.Span%601> with random values.</span></span>

- <span data-ttu-id="8f8c7-223">Jest <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> teraz obsługiwany na Linuksie i macOS.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-223">The <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> is now supported on Linux and macOS.</span></span>

- <span data-ttu-id="8f8c7-224">Elliptic-Curve Diffie-Hellman (ECDH) jest <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> teraz dostępny w rodzinie klas.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-224">Elliptic-Curve Diffie-Hellman (ECDH) is now available in the <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> class family.</span></span> <span data-ttu-id="8f8c7-225">Powierzchnia jest taka sama jak w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-225">The surface area is the same as in the .NET Framework.</span></span>

- <span data-ttu-id="8f8c7-226">Wystąpienie zwracane <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> przez można zaszyfrować lub odszyfrować za pomocą OAEP przy użyciu sha-2 digest, a także generować lub weryfikować podpisy przy użyciu RSA-PSS.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-226">The instance returned by <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> can encrypt or decrypt with OAEP using a SHA-2 digest, as well as generate or validate signatures using RSA-PSS.</span></span>

### <a name="sockets-improvements"></a><span data-ttu-id="8f8c7-227">Ulepszenia gniazd</span><span class="sxs-lookup"><span data-stu-id="8f8c7-227">Sockets improvements</span></span>

<span data-ttu-id="8f8c7-228">.NET Core zawiera nowy <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>typ i <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>przepisane , które stanowią podstawę interfejsów API sieci owego wyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-228">.NET Core includes a new type, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, and a rewritten <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, that form the basis of higher-level networking APIs.</span></span>  <span data-ttu-id="8f8c7-229"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, na przykład, jest <xref:System.Net.Http.HttpClient> podstawą realizacji.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-229"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, for example, is the basis of the <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="8f8c7-230">W poprzednich wersjach programu .NET Core interfejsy API wyższego poziomu były oparte na implementacjach sieci natywnych.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-230">In previous versions of .NET Core, higher-level APIs were based on native networking implementations.</span></span>

<span data-ttu-id="8f8c7-231">Implementacja gniazd wprowadzona w .NET Core 2.1 ma wiele zalet:</span><span class="sxs-lookup"><span data-stu-id="8f8c7-231">The sockets implementation introduced in .NET Core 2.1 has a number of advantages:</span></span>

- <span data-ttu-id="8f8c7-232">Znaczna poprawa wydajności w porównaniu z poprzednią implementacją.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-232">A significant performance improvement when compared with the previous implementation.</span></span>

- <span data-ttu-id="8f8c7-233">Eliminacja zależności platformy, co upraszcza wdrażanie i obsługę.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-233">Elimination of platform dependencies, which simplifies deployment and servicing.</span></span>

- <span data-ttu-id="8f8c7-234">Spójne zachowanie na wszystkich platformach .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-234">Consistent behavior across all .NET Core platforms.</span></span>

<span data-ttu-id="8f8c7-235"><xref:System.Net.Http.SocketsHttpHandler>jest domyślną implementacją w .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-235"><xref:System.Net.Http.SocketsHttpHandler> is the default implementation in .NET Core 2.1.</span></span> <span data-ttu-id="8f8c7-236">Można jednak skonfigurować aplikację do używania <xref:System.Net.Http.HttpClientHandler> starszej <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> klasy, wywołując metodę:</span><span class="sxs-lookup"><span data-stu-id="8f8c7-236">However, you can configure your application to use the older <xref:System.Net.Http.HttpClientHandler> class by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method:</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", False)
```

<span data-ttu-id="8f8c7-237">Można również użyć zmiennej środowiskowej, aby zrezygnować <xref:System.Net.Http.SocketsHttpHandler>z używania implementacji gniazd na podstawie .</span><span class="sxs-lookup"><span data-stu-id="8f8c7-237">You can also use an environment variable to opt out of using sockets implementations based on <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="8f8c7-238">Aby to zrobić, `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` ustaw `false` jeden lub 0.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-238">To do this, set the `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` to either `false` or 0.</span></span>

<span data-ttu-id="8f8c7-239">W systemie Windows można również <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>użyć , który opiera się <xref:System.Net.Http.SocketsHttpHandler> na implementacji macierzystej lub <xref:System.Net.Http.HttpClient> klasy, przekazując wystąpienie klasy do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-239">On Windows, you can also choose to use <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, which relies on a native implementation, or the <xref:System.Net.Http.SocketsHttpHandler> class by passing an instance of the class to the <xref:System.Net.Http.HttpClient> constructor.</span></span>

<span data-ttu-id="8f8c7-240">W systemach Linux i macOS można konfigurować <xref:System.Net.Http.HttpClient> tylko na podstawie procesu.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-240">On Linux and macOS, you can only configure <xref:System.Net.Http.HttpClient> on a per-process basis.</span></span> <span data-ttu-id="8f8c7-241">W systemie Linux musisz wdrożyć [libcurl,](https://curl.haxx.se/libcurl/) jeśli <xref:System.Net.Http.HttpClient> chcesz użyć starej implementacji.</span><span class="sxs-lookup"><span data-stu-id="8f8c7-241">On Linux, you need to deploy [libcurl](https://curl.haxx.se/libcurl/) if you want to use the old <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="8f8c7-242">(Jest on zainstalowany z .NET Core 2.0.)</span><span class="sxs-lookup"><span data-stu-id="8f8c7-242">(It is installed with .NET Core 2.0.)</span></span>

### <a name="breaking-changes"></a><span data-ttu-id="8f8c7-243">Zmiany powodujące niezgodność</span><span class="sxs-lookup"><span data-stu-id="8f8c7-243">Breaking changes</span></span>

<span data-ttu-id="8f8c7-244">Aby uzyskać informacje o zmianach dotyczących łamania, zobacz [Łamanie zmian migracji z wersji 2.0 do 2.1](../compatibility/2.0-2.1.md).</span><span class="sxs-lookup"><span data-stu-id="8f8c7-244">For information about breaking changes, see [Breaking changes for migration from version 2.0 to 2.1](../compatibility/2.0-2.1.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8f8c7-245">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8f8c7-245">See also</span></span>

- [<span data-ttu-id="8f8c7-246">Co nowego w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="8f8c7-246">What's new in .NET Core</span></span>](index.md)
- [<span data-ttu-id="8f8c7-247">Nowe funkcje ef core 2.1</span><span class="sxs-lookup"><span data-stu-id="8f8c7-247">New features in EF Core 2.1</span></span>](/ef/core/what-is-new/ef-core-2.1)
- [<span data-ttu-id="8f8c7-248">Co nowego w ASP.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="8f8c7-248">What's new in ASP.NET Core 2.1</span></span>](/aspnet/core/aspnetcore-2.1)
