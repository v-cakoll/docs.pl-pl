---
title: Co nowego w programie .NET Core 2.1
description: Dowiedz się więcej o nowych funkcjach dostępnych w programie .NET Core 2,1.
dev_langs:
- csharp
- vb
ms.date: 10/10/2018
ms.openlocfilehash: 2397bf999ba97fe0c011de180e05be4177894365
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239888"
---
# <a name="whats-new-in-net-core-21"></a><span data-ttu-id="cd93c-103">Co nowego w programie .NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="cd93c-103">What's new in .NET Core 2.1</span></span>

<span data-ttu-id="cd93c-104">Program .NET Core 2,1 zawiera ulepszenia i nowe funkcje w następujących obszarach:</span><span class="sxs-lookup"><span data-stu-id="cd93c-104">.NET Core 2.1 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="cd93c-105">Narzędzi</span><span class="sxs-lookup"><span data-stu-id="cd93c-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="cd93c-106">Przewinięcie do przodu</span><span class="sxs-lookup"><span data-stu-id="cd93c-106">Roll forward</span></span>](#roll-forward)
- [<span data-ttu-id="cd93c-107">Wdrożenie</span><span class="sxs-lookup"><span data-stu-id="cd93c-107">Deployment</span></span>](#deployment)
- [<span data-ttu-id="cd93c-108">Pakiet zgodności systemu Windows</span><span class="sxs-lookup"><span data-stu-id="cd93c-108">Windows Compatibility Pack</span></span>](#windows-compatibility-pack)
- [<span data-ttu-id="cd93c-109">Ulepszenia kompilacji JIT</span><span class="sxs-lookup"><span data-stu-id="cd93c-109">JIT compilation improvements</span></span>](#jit-compiler-improvements)
- [<span data-ttu-id="cd93c-110">Zmiany interfejsu API</span><span class="sxs-lookup"><span data-stu-id="cd93c-110">API changes</span></span>](#api-changes)

## <a name="tooling"></a><span data-ttu-id="cd93c-111">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="cd93c-111">Tooling</span></span>

<span data-ttu-id="cd93c-112">Zestaw .NET Core 2,1 SDK (v 2.1.300), narzędzia dołączone do programu .NET Core 2,1, obejmują następujące zmiany i ulepszenia:</span><span class="sxs-lookup"><span data-stu-id="cd93c-112">The .NET Core 2.1 SDK (v 2.1.300), the tooling included with .NET Core 2.1, includes the following changes and enhancements:</span></span>

### <a name="build-performance-improvements"></a><span data-ttu-id="cd93c-113">Ulepszenia wydajności kompilacji</span><span class="sxs-lookup"><span data-stu-id="cd93c-113">Build performance improvements</span></span>

<span data-ttu-id="cd93c-114">Głównym fokusem platformy .NET Core 2,1 jest poprawa wydajności czasu kompilacji, szczególnie w przypadku kompilacji przyrostowych.</span><span class="sxs-lookup"><span data-stu-id="cd93c-114">A major focus of .NET Core 2.1 is improving build-time performance, particularly for incremental builds.</span></span> <span data-ttu-id="cd93c-115">Te ulepszenia wydajności dotyczą zarówno `dotnet build` kompilacji wiersza polecenia, jak i kompilacji w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cd93c-115">These performance improvements apply to both command-line builds using `dotnet build` and to builds in Visual Studio.</span></span> <span data-ttu-id="cd93c-116">Niektóre indywidualne obszary poprawy obejmują:</span><span class="sxs-lookup"><span data-stu-id="cd93c-116">Some individual areas of improvement include:</span></span>

- <span data-ttu-id="cd93c-117">W przypadku rozpoznawania zasobów pakietu, rozpoznawania tylko zasobów używanych przez kompilację, a nie wszystkich zasobów.</span><span class="sxs-lookup"><span data-stu-id="cd93c-117">For package asset resolution, resolving only assets used by a build rather than all assets.</span></span>

- <span data-ttu-id="cd93c-118">Buforowanie odwołań do zestawów.</span><span class="sxs-lookup"><span data-stu-id="cd93c-118">Caching of assembly references.</span></span>

- <span data-ttu-id="cd93c-119">Korzystanie z długotrwałych serwerów kompilacji zestawu SDK, które są procesami, które rozciągają się na poszczególne wywołania `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="cd93c-119">Use of long-running SDK build servers, which are processes that span across individual `dotnet build` invocations.</span></span> <span data-ttu-id="cd93c-120">Eliminują one konieczność kompilowania dużych bloków kodu przy każdym uruchomieniu `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="cd93c-120">They eliminate the need to JIT-compile large blocks of code every time `dotnet build` is run.</span></span> <span data-ttu-id="cd93c-121">Procesy serwera kompilacji można automatycznie kończyć przy użyciu następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="cd93c-121">Build server processes can be automatically terminated with the following command:</span></span>

   ```dotnetcli
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a><span data-ttu-id="cd93c-122">Polecenia nowej infrastruktury CLI</span><span class="sxs-lookup"><span data-stu-id="cd93c-122">New CLI commands</span></span>

<span data-ttu-id="cd93c-123">Kilka narzędzi, które były dostępne tylko dla poszczególnych projektów, przy użyciu [`DotnetCliToolReference`](../tools/extensibility.md) są teraz dostępne jako część zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="cd93c-123">A number of tools that were available only on a per project basis using [`DotnetCliToolReference`](../tools/extensibility.md) are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="cd93c-124">Do tych narzędzi należą:</span><span class="sxs-lookup"><span data-stu-id="cd93c-124">These tools include:</span></span>

- <span data-ttu-id="cd93c-125">`dotnet watch` udostępnia obserwatora systemu plików, który czeka na zmianę pliku przed wykonaniem określonego zestawu poleceń.</span><span class="sxs-lookup"><span data-stu-id="cd93c-125">`dotnet watch` provides a file system watcher that waits for a file to change before executing a designated set of commands.</span></span> <span data-ttu-id="cd93c-126">Na przykład następujące polecenie automatycznie ponownie kompiluje bieżący projekt i generuje pełne dane wyjściowe za każdym razem, gdy plik zostanie zmieniony:</span><span class="sxs-lookup"><span data-stu-id="cd93c-126">For example, the following command automatically rebuilds the current project and generates verbose output whenever a file in it changes:</span></span>

   ```dotnetcli
   dotnet watch -- --verbose build
   ```

   <span data-ttu-id="cd93c-127">Zwróć uwagę na `--` opcji, która poprzedza opcję `--verbose`.</span><span class="sxs-lookup"><span data-stu-id="cd93c-127">Note the `--` option that precedes the `--verbose` option.</span></span> <span data-ttu-id="cd93c-128">Ogranicza opcje przekazane bezpośrednio do `dotnet watch` polecenia z argumentów, które są przekazane do podrzędnego procesu `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="cd93c-128">It delimits the options passed directly to the `dotnet watch` command from the arguments that are passed to the child `dotnet` process.</span></span> <span data-ttu-id="cd93c-129">Bez niej opcja `--verbose` ma zastosowanie do polecenia `dotnet watch`, a nie polecenia `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="cd93c-129">Without it, the `--verbose` option applies to the `dotnet watch` command, not the `dotnet build` command.</span></span>
  
   <span data-ttu-id="cd93c-130">Aby uzyskać więcej informacji, zobacz [opracowywanie aplikacji ASP.NET Core przy użyciu czujki dotnet](/aspnet/core/tutorials/dotnet-watch).</span><span class="sxs-lookup"><span data-stu-id="cd93c-130">For more information, see [Develop ASP.NET Core apps using dotnet watch](/aspnet/core/tutorials/dotnet-watch).</span></span>

- <span data-ttu-id="cd93c-131">`dotnet dev-certs` generuje i zarządza certyfikatami używanymi podczas opracowywania aplikacji ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="cd93c-131">`dotnet dev-certs` generates and manages certificates used during development in ASP.NET Core applications.</span></span>

- <span data-ttu-id="cd93c-132">`dotnet user-secrets` zarządza wpisami tajnymi w magazynie kluczy tajnych użytkownika w aplikacjach ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="cd93c-132">`dotnet user-secrets` manages the secrets in a user secret store in ASP.NET Core applications.</span></span>

- <span data-ttu-id="cd93c-133">`dotnet sql-cache` tworzy tabelę i indeksy w bazie danych Microsoft SQL Server, które mają być używane na potrzeby rozproszonej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="cd93c-133">`dotnet sql-cache` creates a table and indexes in a Microsoft SQL Server database to be used for distributed caching.</span></span>

- <span data-ttu-id="cd93c-134">`dotnet ef` to narzędzie do zarządzania bazami danych, obiektami <xref:Microsoft.EntityFrameworkCore.DbContext> i migracjami w aplikacjach Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="cd93c-134">`dotnet ef` is a tool for managing databases, <xref:Microsoft.EntityFrameworkCore.DbContext> objects, and migrations in Entity Framework Core applications.</span></span> <span data-ttu-id="cd93c-135">Aby uzyskać więcej informacji, zobacz [EF Core narzędzia wiersza polecenia programu .NET](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="cd93c-135">For more information, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

### <a name="global-tools"></a><span data-ttu-id="cd93c-136">Narzędzia globalne</span><span class="sxs-lookup"><span data-stu-id="cd93c-136">Global Tools</span></span>

<span data-ttu-id="cd93c-137">Program .NET Core 2,1 obsługuje *Narzędzia globalne* — czyli narzędzia niestandardowe, które są dostępne globalnie w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="cd93c-137">.NET Core 2.1 supports *Global Tools* -- that is, custom tools that are available globally from the command line.</span></span> <span data-ttu-id="cd93c-138">Model rozszerzalności we wcześniejszych wersjach programu .NET Core wykonał niestandardowe narzędzia dostępne na podstawie projektu tylko przy użyciu [`DotnetCliToolReference`](../tools/extensibility.md#consuming-per-project-tools).</span><span class="sxs-lookup"><span data-stu-id="cd93c-138">The extensibility model in previous versions of .NET Core made custom tools available on a per project basis only by using [`DotnetCliToolReference`](../tools/extensibility.md#consuming-per-project-tools).</span></span>

<span data-ttu-id="cd93c-139">Aby zainstalować narzędzie globalne, należy użyć polecenia [Narzędzia dotnet Install](../tools/dotnet-tool-install.md) .</span><span class="sxs-lookup"><span data-stu-id="cd93c-139">To install a Global Tool, you use the [dotnet tool install](../tools/dotnet-tool-install.md) command.</span></span> <span data-ttu-id="cd93c-140">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="cd93c-140">For example:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="cd93c-141">Po zainstalowaniu narzędzie można uruchomić z wiersza polecenia, określając nazwę narzędzia.</span><span class="sxs-lookup"><span data-stu-id="cd93c-141">Once installed, the tool can be run from the command line by specifying the tool name.</span></span> <span data-ttu-id="cd93c-142">Aby uzyskać więcej informacji, zobacz [Omówienie narzędzi globalnych platformy .NET Core](../tools/global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="cd93c-142">For more information, see [.NET Core Global Tools overview](../tools/global-tools.md).</span></span>

### <a name="tool-management-with-the-dotnet-tool-command"></a><span data-ttu-id="cd93c-143">Zarządzanie narzędziem za pomocą polecenia `dotnet tool`</span><span class="sxs-lookup"><span data-stu-id="cd93c-143">Tool management with the `dotnet tool` command</span></span>

<span data-ttu-id="cd93c-144">W zestawie SDK platformy .NET Core 2,1 wszystkie operacje narzędzi używają `dotnet tool` polecenie.</span><span class="sxs-lookup"><span data-stu-id="cd93c-144">In .NET Core 2.1 SDK, all tools operations use the `dotnet tool` command.</span></span> <span data-ttu-id="cd93c-145">Dostępne są następujące opcje:</span><span class="sxs-lookup"><span data-stu-id="cd93c-145">The following options are available:</span></span>

- <span data-ttu-id="cd93c-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) zainstalować narzędzie.</span><span class="sxs-lookup"><span data-stu-id="cd93c-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) to install a tool.</span></span>

- <span data-ttu-id="cd93c-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) odinstalować i ponownie zainstalować narzędzie, które efektywnie go aktualizuje.</span><span class="sxs-lookup"><span data-stu-id="cd93c-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) to uninstall and reinstall a tool, which effectively updates it.</span></span>

- <span data-ttu-id="cd93c-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) , aby wyświetlić listę aktualnie zainstalowanych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="cd93c-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) to list currently installed tools.</span></span>

- <span data-ttu-id="cd93c-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) odinstalować aktualnie zainstalowane narzędzia.</span><span class="sxs-lookup"><span data-stu-id="cd93c-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) to uninstall currently installed tools.</span></span>

## <a name="roll-forward"></a><span data-ttu-id="cd93c-150">Przewinięcie do przodu</span><span class="sxs-lookup"><span data-stu-id="cd93c-150">Roll forward</span></span>

<span data-ttu-id="cd93c-151">Wszystkie aplikacje .NET Core, począwszy od platformy .NET Core 2,0, automatycznie przekazują do najnowszej *wersji pomocniczej* zainstalowanej w systemie.</span><span class="sxs-lookup"><span data-stu-id="cd93c-151">All .NET Core applications starting with .NET Core 2.0 automatically roll forward to the latest *minor version* installed on a system.</span></span>

<span data-ttu-id="cd93c-152">Począwszy od platformy .NET Core 2,0, jeśli wersja platformy .NET Core, z którą została skompilowana aplikacja, nie jest obecna w czasie wykonywania, aplikacja jest uruchamiana automatycznie względem najnowszej zainstalowanej *pomocniczej wersji* platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cd93c-152">Starting with .NET Core 2.0, if the version of .NET Core that an application was built with is not present at runtime, the application automatically runs against the latest installed *minor version* of .NET Core.</span></span> <span data-ttu-id="cd93c-153">Innymi słowy, jeśli aplikacja jest skompilowana przy użyciu platformy .NET Core 2,0, a program .NET Core 2,0 nie jest obecny w systemie hosta, ale .NET Core 2,1 to, aplikacja działa z platformą .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="cd93c-153">In other words, if an application is built with .NET Core 2.0, and .NET Core 2.0 is not present on the host system but .NET Core 2.1 is, the application runs with .NET Core 2.1.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cd93c-154">To zachowanie z przekazaniem do przodu nie ma zastosowania do wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="cd93c-154">This roll-forward behavior doesn't apply to preview releases.</span></span> <span data-ttu-id="cd93c-155">Domyślnie nie dotyczy to również wersji głównych, ale można to zmienić przy użyciu poniższych ustawień.</span><span class="sxs-lookup"><span data-stu-id="cd93c-155">By default, it also doesn't apply to major releases, but this can be changed with the settings below.</span></span>

<span data-ttu-id="cd93c-156">To zachowanie można zmienić, zmieniając ustawienie dla opcji przechodzenie do przodu w przypadku braku kandydata udostępnionego platformy.</span><span class="sxs-lookup"><span data-stu-id="cd93c-156">You can modify this behavior by changing the setting for the roll-forward on no candidate shared framework.</span></span> <span data-ttu-id="cd93c-157">Dostępne są następujące ustawienia:</span><span class="sxs-lookup"><span data-stu-id="cd93c-157">The available settings are:</span></span>

- <span data-ttu-id="cd93c-158">`0` — Wyłącz zachowanie przekazujące wersje pomocnicze.</span><span class="sxs-lookup"><span data-stu-id="cd93c-158">`0` - disable minor version roll-forward behavior.</span></span> <span data-ttu-id="cd93c-159">W przypadku tego ustawienia aplikacja skompilowana dla programu .NET Core 2.0.0 będzie przeniesiona do wersji .NET Core 2.0.1, ale nie do platformy .NET Core 2.2.0 lub .NET Core 3.0.0.</span><span class="sxs-lookup"><span data-stu-id="cd93c-159">With this setting, an application built for .NET Core 2.0.0 will roll forward to .NET Core 2.0.1, but not to .NET Core 2.2.0 or .NET Core 3.0.0.</span></span>
- <span data-ttu-id="cd93c-160">`1` — Włącz zachowanie przekazujące wersje pomocnicze.</span><span class="sxs-lookup"><span data-stu-id="cd93c-160">`1` - enable minor version roll-forward behavior.</span></span> <span data-ttu-id="cd93c-161">Jest to wartość domyślna dla tego ustawienia.</span><span class="sxs-lookup"><span data-stu-id="cd93c-161">This is the default value for the setting.</span></span> <span data-ttu-id="cd93c-162">W przypadku tego ustawienia aplikacja skompilowana dla programu .NET Core 2.0.0 będzie przeniesiona do programu .NET Core 2.0.1 lub .NET Core 2.2.0, w zależności od tego, który z nich jest zainstalowany, ale nie zostanie przesunięty do programu .NET Core 3.0.0.</span><span class="sxs-lookup"><span data-stu-id="cd93c-162">With this setting, an application built for .NET Core 2.0.0 will roll forward to either .NET Core 2.0.1 or .NET Core 2.2.0, depending on which one is installed, but it will not roll forward to .NET Core 3.0.0.</span></span>
- <span data-ttu-id="cd93c-163">`2` — Włącz proste i główne zachowanie podczas przekazywania wersji.</span><span class="sxs-lookup"><span data-stu-id="cd93c-163">`2` - enable minor and major version roll-forward behavior.</span></span> <span data-ttu-id="cd93c-164">Jeśli ta wartość jest ustawiona, są uwzględniane różne wersje główne, więc aplikacja skompilowana dla platformy .NET Core 2.0.0 przejdzie do usługi .NET Core 3.0.0.</span><span class="sxs-lookup"><span data-stu-id="cd93c-164">If set, even different major versions are considered, so an application built for .NET Core 2.0.0 will roll forward to .NET Core 3.0.0.</span></span>

<span data-ttu-id="cd93c-165">To ustawienie można zmienić na jeden z trzech sposobów:</span><span class="sxs-lookup"><span data-stu-id="cd93c-165">You can modify this setting in any of three ways:</span></span>

- <span data-ttu-id="cd93c-166">Ustaw żądaną wartość zmiennej środowiskowej `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`.</span><span class="sxs-lookup"><span data-stu-id="cd93c-166">Set the `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` environment variable to the desired value.</span></span>

- <span data-ttu-id="cd93c-167">Dodaj następujący wiersz z odpowiednią wartością do pliku *. runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="cd93c-167">Add the following line with the desired value to the *.runtimeconfig.json* file:</span></span>

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- <span data-ttu-id="cd93c-168">Korzystając z [interfejs wiersza polecenia platformy .NET Core](../tools/index.md), Dodaj następującą opcję z odpowiednią wartością do polecenia programu .NET Core, np. `run`:</span><span class="sxs-lookup"><span data-stu-id="cd93c-168">When using the [.NET Core CLI](../tools/index.md), add the following option with the desired value to a .NET Core command such as `run`:</span></span>

   ```dotnetcli
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

<span data-ttu-id="cd93c-169">Wersja poprawki do przodu jest niezależna od tego ustawienia i jest wykonywana po zastosowaniu dowolnych dodatkowych lub głównych wersji do przodu.</span><span class="sxs-lookup"><span data-stu-id="cd93c-169">Patch version roll forward is independent of this setting and is done after any potential minor or major version roll forward is applied.</span></span>

## <a name="deployment"></a><span data-ttu-id="cd93c-170">Wdrożenie</span><span class="sxs-lookup"><span data-stu-id="cd93c-170">Deployment</span></span>

### <a name="self-contained-application-servicing"></a><span data-ttu-id="cd93c-171">Obsługa aplikacji samodzielnych</span><span class="sxs-lookup"><span data-stu-id="cd93c-171">Self-contained application servicing</span></span>

<span data-ttu-id="cd93c-172">`dotnet publish` teraz publikuje aplikacje samodzielne przy użyciu wersji środowiska uruchomieniowego z obsługą usługi.</span><span class="sxs-lookup"><span data-stu-id="cd93c-172">`dotnet publish` now publishes self-contained applications with a serviced runtime version.</span></span> <span data-ttu-id="cd93c-173">Po opublikowaniu aplikacji samodzielnej przy użyciu zestawu .NET Core 2,1 SDK (v 2.1.300) aplikacja zawiera najnowszą wersję środowiska uruchomieniowego, znaną przez ten zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="cd93c-173">When you publish a self-contained application with the .NET Core 2.1 SDK (v 2.1.300), your application includes the latest serviced runtime version known by that SDK.</span></span> <span data-ttu-id="cd93c-174">Po uaktualnieniu do najnowszego zestawu SDK opublikujesz go przy użyciu najnowszej wersji środowiska uruchomieniowego platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cd93c-174">When you upgrade to the latest SDK, you’ll publish with the latest .NET Core runtime version.</span></span> <span data-ttu-id="cd93c-175">Dotyczy to środowiska uruchomieniowego .NET Core 1,0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="cd93c-175">This applies for .NET Core 1.0 runtimes and later.</span></span>

<span data-ttu-id="cd93c-176">Samodzielny publikowanie jest zależne od wersji środowiska uruchomieniowego w systemie NuGet.org. Na maszynie nie trzeba mieć obsługiwanego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="cd93c-176">Self-contained publishing relies on runtime versions on NuGet.org. You do not need to have the serviced runtime on your machine.</span></span>

<span data-ttu-id="cd93c-177">Przy użyciu zestawu SDK platformy .NET Core 2,0 aplikacje samodzielne są publikowane przy użyciu środowiska uruchomieniowego 2.0.0 platformy .NET Core, chyba że inna wersja została określona za pośrednictwem właściwości `RuntimeFrameworkVersion`.</span><span class="sxs-lookup"><span data-stu-id="cd93c-177">Using the .NET Core 2.0 SDK, self-contained applications are published with the .NET Core 2.0.0 runtime unless a different version is specified via the `RuntimeFrameworkVersion` property.</span></span> <span data-ttu-id="cd93c-178">W przypadku tego nowego zachowania nie trzeba już ustawiać tej właściwości, aby wybrać nowszą wersję środowiska uruchomieniowego dla aplikacji samodzielnej.</span><span class="sxs-lookup"><span data-stu-id="cd93c-178">With this new behavior, you’ll no longer need to set this property to select a higher runtime version for a self-contained application.</span></span> <span data-ttu-id="cd93c-179">Najprostszym podejściem do przodu jest zawsze Publikowanie przy użyciu zestawu SDK platformy .NET Core 2,1 (v 2.1.300).</span><span class="sxs-lookup"><span data-stu-id="cd93c-179">The easiest approach going forward is to always publish with .NET Core 2.1 SDK (v 2.1.300).</span></span>

<span data-ttu-id="cd93c-180">Aby uzyskać więcej informacji, zobacz [samodzielne wdrożenie środowiska uruchomieniowego wdrożenia](../deploying/runtime-patch-selection.md).</span><span class="sxs-lookup"><span data-stu-id="cd93c-180">For more information, see [Self-contained deployment runtime roll forward](../deploying/runtime-patch-selection.md).</span></span>
## <a name="windows-compatibility-pack"></a><span data-ttu-id="cd93c-181">Pakiet zgodności systemu Windows</span><span class="sxs-lookup"><span data-stu-id="cd93c-181">Windows Compatibility Pack</span></span>

<span data-ttu-id="cd93c-182">Podczas przenoszenia istniejącego kodu z .NET Framework do programu .NET Core można użyć [pakietu zgodności systemu Windows](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="cd93c-182">When you port existing code from the .NET Framework to .NET Core, you can use the [Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span> <span data-ttu-id="cd93c-183">Zapewnia dostęp do 20 000 więcej interfejsów API, niż są dostępne w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cd93c-183">It provides access to 20,000 more APIs than are available in .NET Core.</span></span> <span data-ttu-id="cd93c-184">Te interfejsy API obejmują typy w przestrzeni nazw <xref:System.Drawing?displayProperty=nameWithType>, klasy <xref:System.Diagnostics.EventLog>, WMI, liczniki wydajności, usługi systemu Windows oraz typy i składowe rejestru systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="cd93c-184">These APIs include types in the <xref:System.Drawing?displayProperty=nameWithType> namespace, the <xref:System.Diagnostics.EventLog> class, WMI, Performance Counters, Windows Services, and the Windows registry types and members.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="cd93c-185">Udoskonalenia kompilatora JIT</span><span class="sxs-lookup"><span data-stu-id="cd93c-185">JIT compiler improvements</span></span>

<span data-ttu-id="cd93c-186">Platforma .NET Core obejmuje nową technologię kompilatora JIT o nazwie *kompilacja warstwowa* (znana również jako *Optymalizacja adaptacyjna*), która może znacząco poprawić wydajność.</span><span class="sxs-lookup"><span data-stu-id="cd93c-186">.NET Core incorporates a new JIT compiler technology called *tiered compilation* (also known as *adaptive optimization*) that can significantly improve performance.</span></span> <span data-ttu-id="cd93c-187">Kompilacja warstwowa jest ustawieniem zgody.</span><span class="sxs-lookup"><span data-stu-id="cd93c-187">Tiered compilation is an opt-in setting.</span></span>

<span data-ttu-id="cd93c-188">Jednym z ważnych zadań wykonywanych przez kompilator JIT jest optymalizacja wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="cd93c-188">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="cd93c-189">Jednak w przypadku niewielkich ścieżek kodu kompilator może poświęcać więcej czasu na optymalizację kodu niż środowisko uruchomieniowe spędza na uruchamianiu niezoptymalizowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="cd93c-189">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends running unoptimized code.</span></span> <span data-ttu-id="cd93c-190">Kompilacja warstwowa wprowadza dwa etapy kompilacji JIT:</span><span class="sxs-lookup"><span data-stu-id="cd93c-190">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="cd93c-191">**Pierwsza warstwa**, która generuje kod tak szybko, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="cd93c-191">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="cd93c-192">**Druga warstwa**, która generuje zoptymalizowany kod dla tych metod, które są wykonywane często.</span><span class="sxs-lookup"><span data-stu-id="cd93c-192">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="cd93c-193">Druga warstwa kompilacji jest wykonywana równolegle w celu zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="cd93c-193">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="cd93c-194">Możesz zdecydować się na kompilację warstwową na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="cd93c-194">You can opt into tiered compilation in either of two ways.</span></span>

- <span data-ttu-id="cd93c-195">Aby użyć kompilacji warstwowej we wszystkich projektach, które używają zestawu SDK platformy .NET Core 2,1, ustaw następujące zmienne środowiskowe:</span><span class="sxs-lookup"><span data-stu-id="cd93c-195">To use tiered compilation in all projects that use the .NET Core 2.1 SDK, set the following environment variable:</span></span>

  ```console
  COMPlus_TieredCompilation="1"
  ```

- <span data-ttu-id="cd93c-196">Aby użyć kompilacji warstwowej dla każdego projektu, Dodaj właściwość `<TieredCompilation>` do sekcji `<PropertyGroup>` pliku projektu MSBuild, jak pokazano na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="cd93c-196">To use tiered compilation on a per-project basis, add the `<TieredCompilation>` property to the `<PropertyGroup>` section of the MSBuild project file, as the following example shows:</span></span>

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a><span data-ttu-id="cd93c-197">Zmiany interfejsu API</span><span class="sxs-lookup"><span data-stu-id="cd93c-197">API changes</span></span>

### <a name="spant-and-memoryt"></a><span data-ttu-id="cd93c-198">`Span<T>` i `Memory<T>`</span><span class="sxs-lookup"><span data-stu-id="cd93c-198">`Span<T>` and `Memory<T>`</span></span>

<span data-ttu-id="cd93c-199">Platforma .NET Core 2,1 zawiera nowe typy, które ułatwiają pracę z tablicami i innymi typami pamięci.</span><span class="sxs-lookup"><span data-stu-id="cd93c-199">.NET Core 2.1 includes some new types that make working with arrays and other types of memory much more efficient.</span></span> <span data-ttu-id="cd93c-200">Nowe typy obejmują:</span><span class="sxs-lookup"><span data-stu-id="cd93c-200">The new types include:</span></span>

- <span data-ttu-id="cd93c-201"><xref:System.Span%601?displayProperty=nameWithType> i <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cd93c-201"><xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="cd93c-202"><xref:System.Memory%601?displayProperty=nameWithType> i <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cd93c-202"><xref:System.Memory%601?displayProperty=nameWithType> and <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="cd93c-203">Bez tych typów, podczas przekazywania takich elementów jako części tablicy lub sekcji buforu pamięci należy wykonać kopię części danych przed przekazaniem jej do metody.</span><span class="sxs-lookup"><span data-stu-id="cd93c-203">Without these types, when passing such items as a portion of an array or a section of a memory buffer, you have to make a copy of some portion of the data before passing it to a method.</span></span> <span data-ttu-id="cd93c-204">Te typy zapewniają wirtualny widok tych danych, który eliminuje konieczność dodatkowej alokacji pamięci i operacji kopiowania.</span><span class="sxs-lookup"><span data-stu-id="cd93c-204">These types provide a virtual view of that data that eliminates the need for the additional memory allocation and copy operations.</span></span>

<span data-ttu-id="cd93c-205">Poniższy przykład używa wystąpienia <xref:System.Span%601> i <xref:System.Memory%601>, aby zapewnić wirtualny widok 10 elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="cd93c-205">The following example uses a <xref:System.Span%601> and <xref:System.Memory%601> instance to provide a virtual view of 10 elements of an array.</span></span>

[!code-csharp[Span\<T>](~/samples/snippets/core/whats-new/whats-new-in-21/csharp/program.cs)]

[!code-vb[Memory\<T>](~/samples/snippets/core/whats-new/whats-new-in-21/vb/program.vb)]

### <a name="brotli-compression"></a><span data-ttu-id="cd93c-206">Kompresja Brotli</span><span class="sxs-lookup"><span data-stu-id="cd93c-206">Brotli compression</span></span>

<span data-ttu-id="cd93c-207">Program .NET Core 2,1 dodaje obsługę kompresji i dekompresji Brotli.</span><span class="sxs-lookup"><span data-stu-id="cd93c-207">.NET Core 2.1 adds support for Brotli compression and decompression.</span></span> <span data-ttu-id="cd93c-208">Brotli to algorytm kompresji bezstratnego ogólnego przeznaczenia, który jest zdefiniowany w [dokumencie RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) i jest obsługiwany przez większość przeglądarek sieci Web i głównych serwerów sieci Web.</span><span class="sxs-lookup"><span data-stu-id="cd93c-208">Brotli is a general-purpose lossless compression algorithm that is defined in [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) and is supported by most web browsers and major web servers.</span></span> <span data-ttu-id="cd93c-209">Można użyć klasy <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> opartej na strumieniach lub <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> i klas <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> opartych na procesorze o wysokiej wydajności.</span><span class="sxs-lookup"><span data-stu-id="cd93c-209">You can use the stream-based <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> class or the high-performance span-based <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> and <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> classes.</span></span> <span data-ttu-id="cd93c-210">Poniższy przykład ilustruje kompresję z klasą <xref:System.IO.Compression.BrotliStream>:</span><span class="sxs-lookup"><span data-stu-id="cd93c-210">The following example illustrates compression with the <xref:System.IO.Compression.BrotliStream> class:</span></span>

[!code-csharp[Brotli compression](~/samples/snippets/core/whats-new/whats-new-in-21/csharp/brotli.cs#1)]

[!code-vb[Brotli compression](~/samples/snippets/core/whats-new/whats-new-in-21/vb/brotli.vb#1)]

<span data-ttu-id="cd93c-211">Zachowanie <xref:System.IO.Compression.BrotliStream> jest takie samo jak <xref:System.IO.Compression.DeflateStream> i <xref:System.IO.Compression.GZipStream>, co ułatwia konwertowanie kodu, który wywołuje te interfejsy API do <xref:System.IO.Compression.BrotliStream>.</span><span class="sxs-lookup"><span data-stu-id="cd93c-211">The <xref:System.IO.Compression.BrotliStream> behavior is the same as <xref:System.IO.Compression.DeflateStream> and <xref:System.IO.Compression.GZipStream>, which makes it easy to convert code that calls these APIs to <xref:System.IO.Compression.BrotliStream>.</span></span>

### <a name="new-cryptography-apis-and-cryptography-improvements"></a><span data-ttu-id="cd93c-212">Nowe ulepszone interfejsy API kryptografii i kryptografii</span><span class="sxs-lookup"><span data-stu-id="cd93c-212">New cryptography APIs and cryptography improvements</span></span>

<span data-ttu-id="cd93c-213">Program .NET Core 2,1 zawiera liczne ulepszenia interfejsów API kryptografii:</span><span class="sxs-lookup"><span data-stu-id="cd93c-213">.NET Core 2.1 includes numerous enhancements to the cryptography APIs:</span></span>

- <span data-ttu-id="cd93c-214"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> jest dostępna w pakiecie System. Security. Cryptography. PKCS.</span><span class="sxs-lookup"><span data-stu-id="cd93c-214"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> is available in the System.Security.Cryptography.Pkcs package.</span></span> <span data-ttu-id="cd93c-215">Implementacja jest taka sama jak Klasa <xref:System.Security.Cryptography.Pkcs.SignedCms> w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cd93c-215">The implementation is the same as the <xref:System.Security.Cryptography.Pkcs.SignedCms> class in the .NET Framework.</span></span>

- <span data-ttu-id="cd93c-216">Nowe przeciążenia metod <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> i <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> akceptują identyfikator algorytmu wyznaczania wartości skrótu, aby umożliwić wywołującym pobieranie wartości odcisków palca certyfikatu przy użyciu algorytmów innych niż SHA-1.</span><span class="sxs-lookup"><span data-stu-id="cd93c-216">New overloads of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> and <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> methods accept a hash algorithm identifier to enable callers to get certificate thumbprint values using algorithms other than SHA-1.</span></span>

- <span data-ttu-id="cd93c-217">Dostępne są nowe interfejsy API kryptografii opartej na <xref:System.Span%601>ach, takie jak mieszanie, HMAC, generowanie losowe, Kryptografia, generowanie sygnatur asymetryczne, przetwarzanie sygnatur asymetryczne i szyfrowanie RSA.</span><span class="sxs-lookup"><span data-stu-id="cd93c-217">New <xref:System.Span%601>-based cryptography APIs are available for hashing, HMAC, cryptographic random number generation, asymmetric signature generation, asymmetric signature processing, and RSA encryption.</span></span>

- <span data-ttu-id="cd93c-218">Wydajność <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> została ulepszona o około 15% przy użyciu implementacji opartej na <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="cd93c-218">The performance of <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> has improved by about 15% by using a <xref:System.Span%601>-based implementation.</span></span>

- <span data-ttu-id="cd93c-219">Nowa Klasa <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> obejmuje dwie nowe metody:</span><span class="sxs-lookup"><span data-stu-id="cd93c-219">The new <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> class includes two new methods:</span></span>

  - <span data-ttu-id="cd93c-220"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> pobiera stałą ilość czasu, aby zwrócić w przypadku wszystkich dwóch danych wejściowych o tej samej długości, co sprawia, że jest to odpowiednie do użycia w weryfikacji kryptograficznej, aby uniknąć współtworzenia informacji w kanale bocznym.</span><span class="sxs-lookup"><span data-stu-id="cd93c-220"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> takes a fixed amount of time to return for any two inputs of the same length, which makes it suitable for use in cryptographic verification to avoid contributing to timing side-channel information.</span></span>

  - <span data-ttu-id="cd93c-221"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> to procedura czyszczenia pamięci, której nie można zoptymalizować.</span><span class="sxs-lookup"><span data-stu-id="cd93c-221"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> is a memory-clearing routine that cannot be optimized.</span></span>

- <span data-ttu-id="cd93c-222">Metoda static <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> wypełnia <xref:System.Span%601> losowo wartościami.</span><span class="sxs-lookup"><span data-stu-id="cd93c-222">The static <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> method fills a <xref:System.Span%601> with random values.</span></span>

- <span data-ttu-id="cd93c-223"><xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> jest teraz obsługiwana w systemach Linux i macOS.</span><span class="sxs-lookup"><span data-stu-id="cd93c-223">The <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> is now supported on Linux and macOS.</span></span>

- <span data-ttu-id="cd93c-224">Krzywa eliptyczna — Diffie-Hellmana (ECDH) jest teraz dostępna w rodzinie klas <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cd93c-224">Elliptic-Curve Diffie-Hellman (ECDH) is now available in the <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> class family.</span></span> <span data-ttu-id="cd93c-225">Powierzchnia obszaru jest taka sama jak w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cd93c-225">The surface area is the same as in the .NET Framework.</span></span>

- <span data-ttu-id="cd93c-226">Wystąpienie zwrócone przez <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> może szyfrować lub odszyfrowywać za pomocą OAEP przy użyciu skrótu SHA-2, a także generować lub weryfikować podpisy przy użyciu RSA-PSS.</span><span class="sxs-lookup"><span data-stu-id="cd93c-226">The instance returned by <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> can encrypt or decrypt with OAEP using a SHA-2 digest, as well as generate or validate signatures using RSA-PSS.</span></span>

### <a name="sockets-improvements"></a><span data-ttu-id="cd93c-227">Ulepszenia gniazd</span><span class="sxs-lookup"><span data-stu-id="cd93c-227">Sockets improvements</span></span>

<span data-ttu-id="cd93c-228">Platforma .NET Core zawiera nowy typ, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>i ponownie zapisany <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, który stanowi podstawę interfejsów API sieci wyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="cd93c-228">.NET Core includes a new type, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, and a rewritten <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, that form the basis of higher-level networking APIs.</span></span>  <span data-ttu-id="cd93c-229"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, na przykład, jest podstawą implementacji <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="cd93c-229"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, for example, is the basis of the <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="cd93c-230">W poprzednich wersjach programu .NET Core interfejsy API wyższego poziomu były oparte na natywnych implementacjach sieci.</span><span class="sxs-lookup"><span data-stu-id="cd93c-230">In previous versions of .NET Core, higher-level APIs were based on native networking implementations.</span></span>

<span data-ttu-id="cd93c-231">Implementacja Sockets wprowadzona w programie .NET Core 2,1 ma wiele zalet:</span><span class="sxs-lookup"><span data-stu-id="cd93c-231">The sockets implementation introduced in .NET Core 2.1 has a number of advantages:</span></span>

- <span data-ttu-id="cd93c-232">Znaczący wzrost wydajności w porównaniu z poprzednią implementacją.</span><span class="sxs-lookup"><span data-stu-id="cd93c-232">A significant performance improvement when compared with the previous implementation.</span></span>

- <span data-ttu-id="cd93c-233">Wyeliminowanie zależności platformy, co upraszcza wdrażanie i obsługę.</span><span class="sxs-lookup"><span data-stu-id="cd93c-233">Elimination of platform dependencies, which simplifies deployment and servicing.</span></span>

- <span data-ttu-id="cd93c-234">Spójne zachowanie na wszystkich platformach .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cd93c-234">Consistent behavior across all .NET Core platforms.</span></span>

<span data-ttu-id="cd93c-235"><xref:System.Net.Http.SocketsHttpHandler> to domyślna implementacja programu .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="cd93c-235"><xref:System.Net.Http.SocketsHttpHandler> is the default implementation in .NET Core 2.1.</span></span> <span data-ttu-id="cd93c-236">Można jednak skonfigurować aplikację tak, aby używała starszej klasy <xref:System.Net.Http.HttpClientHandler>, wywołując metodę <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="cd93c-236">However, you can configure your application to use the older <xref:System.Net.Http.HttpClientHandler> class by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method:</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", False)
```

<span data-ttu-id="cd93c-237">Można również użyć zmiennej środowiskowej, aby zrezygnować z użycia implementacji Sockets na podstawie <xref:System.Net.Http.SocketsHttpHandler>.</span><span class="sxs-lookup"><span data-stu-id="cd93c-237">You can also use an environment variable to opt out of using sockets implementations based on <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="cd93c-238">W tym celu ustaw wartość `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` na `false` lub 0.</span><span class="sxs-lookup"><span data-stu-id="cd93c-238">To do this, set the `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` to either `false` or 0.</span></span>

<span data-ttu-id="cd93c-239">W systemie Windows można również użyć <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, który opiera się na implementacji natywnej lub klasy <xref:System.Net.Http.SocketsHttpHandler> przez przekazanie wystąpienia klasy do konstruktora <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="cd93c-239">On Windows, you can also choose to use <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, which relies on a native implementation, or the <xref:System.Net.Http.SocketsHttpHandler> class by passing an instance of the class to the <xref:System.Net.Http.HttpClient> constructor.</span></span>

<span data-ttu-id="cd93c-240">W systemie Linux i macOS można skonfigurować tylko <xref:System.Net.Http.HttpClient> dla poszczególnych procesów.</span><span class="sxs-lookup"><span data-stu-id="cd93c-240">On Linux and macOS, you can only configure <xref:System.Net.Http.HttpClient> on a per-process basis.</span></span> <span data-ttu-id="cd93c-241">W systemie Linux należy wdrożyć [libcurl](https://curl.haxx.se/libcurl/) , jeśli chcesz użyć starej implementacji <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="cd93c-241">On Linux, you need to deploy [libcurl](https://curl.haxx.se/libcurl/) if you want to use the old <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="cd93c-242">(Jest instalowany z platformą .NET Core 2,0).</span><span class="sxs-lookup"><span data-stu-id="cd93c-242">(It is installed with .NET Core 2.0.)</span></span>

### <a name="breaking-changes"></a><span data-ttu-id="cd93c-243">Zmiany powodujące niezgodność</span><span class="sxs-lookup"><span data-stu-id="cd93c-243">Breaking changes</span></span>

<span data-ttu-id="cd93c-244">Aby uzyskać informacje o istotnych zmianach, zobacz istotne [zmiany dotyczące migracji z wersji 2,0 do 2,1](../compatibility/2.0-2.1.md).</span><span class="sxs-lookup"><span data-stu-id="cd93c-244">For information about breaking changes, see [Breaking changes for migration from version 2.0 to 2.1](../compatibility/2.0-2.1.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cd93c-245">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd93c-245">See also</span></span>

- [<span data-ttu-id="cd93c-246">Co nowego w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="cd93c-246">What's new in .NET Core</span></span>](index.md)
- [<span data-ttu-id="cd93c-247">Nowe funkcje w EF Core 2,1</span><span class="sxs-lookup"><span data-stu-id="cd93c-247">New features in EF Core 2.1</span></span>](/ef/core/what-is-new/ef-core-2.1)
- [<span data-ttu-id="cd93c-248">Co nowego w ASP.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="cd93c-248">What's new in ASP.NET Core 2.1</span></span>](/aspnet/core/aspnetcore-2.1)
