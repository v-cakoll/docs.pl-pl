---
title: What's new in .NET Core 2.1
description: Dowiedz się więcej o nowych funkcjach w programie .NET Core 2.1.
dev_langs:
- csharp
- vb
author: rpetrusha
ms.author: ronpet
ms.date: 10/10/2018
ms.openlocfilehash: 7d8c89793f26ab07917e71832d5f3511d9b1aa5a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127553"
---
# <a name="whats-new-in-net-core-21"></a><span data-ttu-id="90a15-103">What's new in .NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="90a15-103">What's new in .NET Core 2.1</span></span>

<span data-ttu-id="90a15-104">.NET core 2.1 zawiera ulepszenia i nowe funkcje w następujących obszarach:</span><span class="sxs-lookup"><span data-stu-id="90a15-104">.NET Core 2.1 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="90a15-105">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="90a15-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="90a15-106">Przenoszenia do przodu</span><span class="sxs-lookup"><span data-stu-id="90a15-106">Roll forward</span></span>](#roll-forward)
- [<span data-ttu-id="90a15-107">Wdrażanie</span><span class="sxs-lookup"><span data-stu-id="90a15-107">Deployment</span></span>](#deployment)
- [<span data-ttu-id="90a15-108">Windows Compatibility Pack</span><span class="sxs-lookup"><span data-stu-id="90a15-108">Windows Compatibility Pack</span></span>](#windows-compatibility-pack)
- [<span data-ttu-id="90a15-109">Ulepszenia kompilacji JIT</span><span class="sxs-lookup"><span data-stu-id="90a15-109">JIT compilation improvements</span></span>](#jit-compiler-improvements)
- [<span data-ttu-id="90a15-110">Zmiany interfejsu API</span><span class="sxs-lookup"><span data-stu-id="90a15-110">API changes</span></span>](#api-changes)

## <a name="tooling"></a><span data-ttu-id="90a15-111">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="90a15-111">Tooling</span></span>

<span data-ttu-id="90a15-112">.NET Core 2.1 SDK (v 2.1.300), narzędzia dostępne przy użyciu platformy .NET Core 2.1, obejmuje następujące zmiany i udoskonalenia:</span><span class="sxs-lookup"><span data-stu-id="90a15-112">The .NET Core 2.1 SDK (v 2.1.300), the tooling included with .NET Core 2.1, includes the following changes and enhancements:</span></span>

### <a name="build-performance-improvements"></a><span data-ttu-id="90a15-113">Ulepszenia wydajności kompilacji</span><span class="sxs-lookup"><span data-stu-id="90a15-113">Build performance improvements</span></span>

<span data-ttu-id="90a15-114">W centrum uwagi platformy .NET Core 2.1 jest poprawę wydajności w czasie kompilacji, szczególnie w przypadku kompilacji przyrostowych.</span><span class="sxs-lookup"><span data-stu-id="90a15-114">A major focus of .NET Core 2.1 is improving build-time performance, particularly for incremental builds.</span></span> <span data-ttu-id="90a15-115">Te ulepszenia wydajności dotyczą zarówno kompilacji z wiersza polecenia przy użyciu `dotnet build` i kompilacji w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="90a15-115">These performance improvements apply to both command-line builds using `dotnet build` and to builds in Visual Studio.</span></span> <span data-ttu-id="90a15-116">Niektóre poszczególne obszary ulepszeń należą:</span><span class="sxs-lookup"><span data-stu-id="90a15-116">Some individual areas of improvement include:</span></span>

- <span data-ttu-id="90a15-117">Rozpoznawanie zawartości pakietu rozpoznawanie tylko zasoby używane przez kompilację, a nie wszystkie zasoby.</span><span class="sxs-lookup"><span data-stu-id="90a15-117">For package asset resolution, resolving only assets used by a build rather than all assets.</span></span>

- <span data-ttu-id="90a15-118">Buforowanie odwołania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="90a15-118">Caching of assembly references.</span></span>

- <span data-ttu-id="90a15-119">Użyj zestawu SDK długotrwałych kompilacji serwerów, które są procesy, które rozciągają się na poszczególnych `dotnet build` wywołania.</span><span class="sxs-lookup"><span data-stu-id="90a15-119">Use of long-running SDK build servers, which are processes that span across individual `dotnet build` invocations.</span></span> <span data-ttu-id="90a15-120">One wyeliminować potrzebę dużych bloków kodu, skompilować wg JIT zawsze `dotnet build` jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="90a15-120">They eliminate the need to JIT-compile large blocks of code every time `dotnet build` is run.</span></span> <span data-ttu-id="90a15-121">Tworzenie serwera, które mogą być automatycznie zakończone procesy za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="90a15-121">Build server processes can be automatically terminated with the following command:</span></span>

   ```console
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a><span data-ttu-id="90a15-122">Nowe polecenia interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="90a15-122">New CLI commands</span></span>

<span data-ttu-id="90a15-123">Wiele narzędzi, które były dostępne tylko na podstawę projektu przy użyciu [ `DotnetCliToolReference` ](../tools/extensibility.md) są teraz dostępne jako część zestawu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="90a15-123">A number of tools that were available only on a per project basis using [`DotnetCliToolReference`](../tools/extensibility.md) are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="90a15-124">Do tych narzędzi należą:</span><span class="sxs-lookup"><span data-stu-id="90a15-124">These tools include:</span></span>

- <span data-ttu-id="90a15-125">`dotnet watch` Zawiera obserwatora systemu plików, który oczekuje na plik, aby zmienić przed wykonaniem wyznaczonym zestaw poleceń.</span><span class="sxs-lookup"><span data-stu-id="90a15-125">`dotnet watch` provides a file system watcher that waits for a file to change before executing a designated set of commands.</span></span> <span data-ttu-id="90a15-126">Na przykład następujące polecenie automatycznie odtwarza bieżącego projektu i generuje pełne dane wyjściowe przy każdym zmian w plikach w nim:</span><span class="sxs-lookup"><span data-stu-id="90a15-126">For example, the following command automatically rebuilds the current project and generates verbose output whenever a file in it changes:</span></span>

   ```console
   dotnet watch -- --verbose build
   ```

   <span data-ttu-id="90a15-127">Uwaga `--` opcję poprzedzającą `--verbose` opcji.</span><span class="sxs-lookup"><span data-stu-id="90a15-127">Note the `--` option that precedes the `--verbose` option.</span></span> <span data-ttu-id="90a15-128">Jego rozgranicza opcje przekazane bezpośrednio do `dotnet watch` polecenia na podstawie argumentów, które są przekazywane do elementu podrzędnego `dotnet` procesu.</span><span class="sxs-lookup"><span data-stu-id="90a15-128">It delimits the options passed directly to the `dotnet watch` command from the arguments that are passed to the child `dotnet` process.</span></span> <span data-ttu-id="90a15-129">Bez tego `--verbose` opcja ma zastosowanie do `dotnet watch` nie polecenia `dotnet build` polecenia.</span><span class="sxs-lookup"><span data-stu-id="90a15-129">Without it, the `--verbose` option applies to the `dotnet watch` command, not the `dotnet build` command.</span></span>
  
   <span data-ttu-id="90a15-130">Aby uzyskać więcej informacji, zobacz [aplikacji opracowywanie platformy ASP.NET Core przy użyciu Obejrzyj dotnet](/aspnet/core/tutorials/dotnet-watch)</span><span class="sxs-lookup"><span data-stu-id="90a15-130">For more information, see [Develop ASP.NET Core apps using dotnet watch](/aspnet/core/tutorials/dotnet-watch)</span></span>

- <span data-ttu-id="90a15-131">`dotnet dev-certs` generuje klucze i zarządza certyfikatami używanymi podczas tworzenia aplikacji platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="90a15-131">`dotnet dev-certs` generates and manages certificates used during development in ASP.NET Core applications.</span></span>

- <span data-ttu-id="90a15-132">`dotnet user-secrets` zarządza wpisów tajnych w magazynie wpisu tajnego użytkownika w aplikacji platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="90a15-132">`dotnet user-secrets` manages the secrets in a user secret store in ASP.NET Core applications.</span></span>

- <span data-ttu-id="90a15-133">`dotnet sql-cache` tworzy tabelę i indeksy w bazie danych programu Microsoft SQL Server do użytku z rozproszonego buforowania.</span><span class="sxs-lookup"><span data-stu-id="90a15-133">`dotnet sql-cache` creates a table and indexes in a Microsoft SQL Server database to be used for distributed caching.</span></span>

- <span data-ttu-id="90a15-134">`dotnet ef` to narzędzie do zarządzania bazami danych, <xref:Microsoft.EntityFrameworkCore.DbContext> obiektów i migracje platformy Entity Framework Core aplikacji.</span><span class="sxs-lookup"><span data-stu-id="90a15-134">`dotnet ef` is a tool for managing databases, <xref:Microsoft.EntityFrameworkCore.DbContext> objects, and migrations in Entity Framework Core applications.</span></span> <span data-ttu-id="90a15-135">Aby uzyskać więcej informacji, zobacz [narzędzia wiersza polecenia platformy .NET Core EF](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="90a15-135">For more information, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

### <a name="global-tools"></a><span data-ttu-id="90a15-136">Narzędzia globalne</span><span class="sxs-lookup"><span data-stu-id="90a15-136">Global Tools</span></span>

<span data-ttu-id="90a15-137">Obsługuje platformy .NET core 2.1 *globalnego narzędzia* — czyli narzędzia niestandardowe, które są dostępne globalnie w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="90a15-137">.NET Core 2.1 supports *Global Tools* -- that is, custom tools that are available globally from the command line.</span></span> <span data-ttu-id="90a15-138">Model rozszerzalności w poprzednich wersjach programu .NET Core udostępnione narzędzia niestandardowe na podstawie projektu tylko przy użyciu [ `DotnetCliToolReference` ](../tools/extensibility.md#consuming-per-project-tools).</span><span class="sxs-lookup"><span data-stu-id="90a15-138">The extensibility model in previous versions of .NET Core made custom tools available on a per project basis only by using [`DotnetCliToolReference`](../tools/extensibility.md#consuming-per-project-tools).</span></span>

<span data-ttu-id="90a15-139">Aby zainstalować narzędzie globalne, należy użyć [instalacji narzędzi dotnet](../tools/dotnet-tool-install.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="90a15-139">To install a Global Tool, you use the [dotnet tool install](../tools/dotnet-tool-install.md) command.</span></span> <span data-ttu-id="90a15-140">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="90a15-140">For example:</span></span>

```console
dotnet tool install -g dotnetsay
```

<span data-ttu-id="90a15-141">Po zakończeniu instalacji można uruchomić narzędzie z wiersza polecenia, określając nazwę narzędzia.</span><span class="sxs-lookup"><span data-stu-id="90a15-141">Once installed, the tool can be run from the command line by specifying the tool name.</span></span> <span data-ttu-id="90a15-142">Aby uzyskać więcej informacji, zobacz [Omówienie narzędzia globalnej platformy .NET Core](../tools/global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="90a15-142">For more information, see [.NET Core Global Tools overview](../tools/global-tools.md).</span></span>

### <a name="tool-management-with-the-dotnet-tool-command"></a><span data-ttu-id="90a15-143">Narzędzie do zarządzania za pomocą `dotnet tool` polecenia</span><span class="sxs-lookup"><span data-stu-id="90a15-143">Tool management with the `dotnet tool` command</span></span>

<span data-ttu-id="90a15-144">W .NET Core 2.1 SDK, użyj wszystkie operacje narzędzia `dotnet tool` polecenia.</span><span class="sxs-lookup"><span data-stu-id="90a15-144">In .NET Core 2.1 SDK, all tools operations use the `dotnet tool` command.</span></span> <span data-ttu-id="90a15-145">Dostępne są następujące opcje:</span><span class="sxs-lookup"><span data-stu-id="90a15-145">The following options are available:</span></span>

- <span data-ttu-id="90a15-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) Aby zainstalować narzędzie.</span><span class="sxs-lookup"><span data-stu-id="90a15-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) to install a tool.</span></span>

- <span data-ttu-id="90a15-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) Aby odinstalować i ponownie zainstaluj narzędzie, które skutecznie aktualizuje.</span><span class="sxs-lookup"><span data-stu-id="90a15-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) to uninstall and reinstall a tool, which effectively updates it.</span></span>

- <span data-ttu-id="90a15-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) Aby wyświetlić listę aktualnie zainstalowanych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="90a15-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) to list currently installed tools.</span></span>

- <span data-ttu-id="90a15-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) Aby odinstalować aktualnie zainstalowanego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="90a15-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) to uninstall currently installed tools.</span></span>

## <a name="roll-forward"></a><span data-ttu-id="90a15-150">Przenoszenia do przodu</span><span class="sxs-lookup"><span data-stu-id="90a15-150">Roll forward</span></span>

<span data-ttu-id="90a15-151">Wszystkie aplikacje platformy .NET Core, począwszy od programu .NET Core 2.0 automatycznie uaktualniane do najnowszej wersji *wersja pomocnicza* zainstalowanego w systemie.</span><span class="sxs-lookup"><span data-stu-id="90a15-151">All .NET Core applications starting with the .NET Core 2.0 automatically roll forward to the latest *minor version* installed on a system.</span></span>

<span data-ttu-id="90a15-152">Uruchamianie przy użyciu platformy .NET Core 2.0, jeśli wersja programu .NET Core, która została zbudowana aplikacja nie jest obecny w czasie wykonywania, aplikacja automatycznie uruchamiana najnowszej zainstalowanej *wersja pomocnicza* programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="90a15-152">Starting with .NET Core 2.0, if the version of .NET Core that an application was built with is not present at runtime, the application automatically runs against the latest installed *minor version* of .NET Core.</span></span> <span data-ttu-id="90a15-153">Innymi słowy Jeśli aplikacja jest oparte na platformie .NET Core 2.0 i .NET Core 2.0 nie jest dostępny w systemie hosta, ale jest platformy .NET Core 2.1, aplikacja zostanie uruchomiona przy użyciu platformy .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="90a15-153">In other words, if an application is built with .NET Core 2.0, and .NET Core 2.0 is not present on the host system but .NET Core 2.1 is, the application runs with .NET Core 2.1.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="90a15-154">To zachowanie przodu nie ma zastosowania do wersji w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="90a15-154">This roll-forward behavior doesn't apply to preview releases.</span></span> <span data-ttu-id="90a15-155">Nie ma zastosowania do wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="90a15-155">Nor does it apply to major releases.</span></span> <span data-ttu-id="90a15-156">Na przykład aplikacji platformy .NET Core 1.0 w takich sytuacjach przydałaby uaktualniane do platformy .NET Core 2.0 lub platformy .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="90a15-156">For example, a .NET Core 1.0 application wouldn't roll forward to .NET Core 2.0 or .NET Core 2.1.</span></span>

<span data-ttu-id="90a15-157">Można również wyłączyć roll wersję pomocniczą na jeden z trzech sposobów:</span><span class="sxs-lookup"><span data-stu-id="90a15-157">You can also disable minor version roll forward in any of three ways:</span></span>

- <span data-ttu-id="90a15-158">Ustaw `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` zmiennej środowiskowej na wartość 0.</span><span class="sxs-lookup"><span data-stu-id="90a15-158">Set the `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` environment variable to 0.</span></span>

- <span data-ttu-id="90a15-159">Dodaj następujący wiersz do pliku runtimeconfig.json:</span><span class="sxs-lookup"><span data-stu-id="90a15-159">Add the following line to the runtimeconfig.json file:</span></span>

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- <span data-ttu-id="90a15-160">Korzystając z [narzędzi interfejsu wiersza polecenia platformy .NET Core](../tools/index.md), obejmują będzie następująca opcja za pomocą polecenia .NET Core, takie jak `run`:</span><span class="sxs-lookup"><span data-stu-id="90a15-160">When using [.NET Core CLI tools](../tools/index.md), include the following option with a .NET Core command such as `run`:</span></span>

   ```console
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

## <a name="deployment"></a><span data-ttu-id="90a15-161">wdrażania</span><span class="sxs-lookup"><span data-stu-id="90a15-161">Deployment</span></span>

### <a name="self-contained-application-servicing"></a><span data-ttu-id="90a15-162">Aplikacja samodzielna obsługi</span><span class="sxs-lookup"><span data-stu-id="90a15-162">Self-contained application servicing</span></span>

<span data-ttu-id="90a15-163">`dotnet publish` teraz publikowanie niezależna aplikacji przy użyciu wersji środowiska uruchomieniowego obsługiwanych.</span><span class="sxs-lookup"><span data-stu-id="90a15-163">`dotnet publish` now publishes self-contained applications with a serviced runtime version.</span></span> <span data-ttu-id="90a15-164">Podczas publikowania niezależna aplikacji przy użyciu zestawu .NET Core 2.1 SDK (v 2.1.300), aplikacja zawiera najnowszą wersję środowiska uruchomieniowego obsługiwanych znane przez ten zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="90a15-164">When you publish a self-contained application with the .NET Core 2.1 SDK (v 2.1.300), your application includes the latest serviced runtime version known by that SDK.</span></span> <span data-ttu-id="90a15-165">Podczas uaktualniania na najnowszy zestaw SDK będzie publikowania za pomocą najnowszej wersji środowiska uruchomieniowego .NET Core.</span><span class="sxs-lookup"><span data-stu-id="90a15-165">When you upgrade to the latest SDK, you’ll publish with the latest .NET Core runtime version.</span></span> <span data-ttu-id="90a15-166">Dotyczy to dla środowisk uruchomieniowych platformy .NET Core 1.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="90a15-166">This applies for .NET Core 1.0 runtimes and later.</span></span>

<span data-ttu-id="90a15-167">Publikowanie niezależne opiera się na wersje środowiska uruchomieniowego w witrynie NuGet.org. Nie trzeba mieć obsługiwane środowiska uruchomieniowego na komputerze.</span><span class="sxs-lookup"><span data-stu-id="90a15-167">Self-contained publishing relies on runtime versions on NuGet.org. You do not need to have the serviced runtime on your machine.</span></span>

<span data-ttu-id="90a15-168">Przy użyciu zestawu .NET Core 2.0 SDK, samodzielne aplikacje są publikowane w środowisku uruchomieniowym .NET Core 2.0.0 chyba że inna wersja jest określona za pomocą `RuntimeFrameworkVersion` właściwości.</span><span class="sxs-lookup"><span data-stu-id="90a15-168">Using the .NET Core 2.0 SDK, self-contained applications are published with the .NET Core 2.0.0 runtime unless a different version is specified via the `RuntimeFrameworkVersion` property.</span></span> <span data-ttu-id="90a15-169">Za pomocą to nowe zachowanie nie jest już należy ustawić tę właściwość, aby wybrać wyższą wersję środowiska uruchomieniowego niezależna aplikacji.</span><span class="sxs-lookup"><span data-stu-id="90a15-169">With this new behavior, you’ll no longer need to set this property to select a higher runtime version for a self-contained application.</span></span> <span data-ttu-id="90a15-170">To najłatwiejsza metoda przechodzenia do przodu jest zawsze publikowanie przy użyciu zestawu SDK platformy .NET Core 2.1 (v 2.1.300).</span><span class="sxs-lookup"><span data-stu-id="90a15-170">The easiest approach going forward is to always publish with .NET Core 2.1 SDK (v 2.1.300).</span></span>

<span data-ttu-id="90a15-171">Aby uzyskać więcej informacji, zobacz [niezależna deploymnet środowiska uruchomieniowego przenoszenia do przodu](../deploying/runtime-patch-selection.md).</span><span class="sxs-lookup"><span data-stu-id="90a15-171">For more information, see [Self-contained deploymnet runtime roll forward](../deploying/runtime-patch-selection.md).</span></span>
## <a name="windows-compatibility-pack"></a><span data-ttu-id="90a15-172">Windows Compatibility Pack</span><span class="sxs-lookup"><span data-stu-id="90a15-172">Windows Compatibility Pack</span></span>

<span data-ttu-id="90a15-173">Jeśli przeniesiesz istniejący kod z programu .NET Framework i .NET Core, możesz użyć [systemie Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="90a15-173">When you port existing code from the .NET Framework to .NET Core, you can use the [Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span> <span data-ttu-id="90a15-174">Zapewnia dostęp do 20 000 więcej interfejsów API, niż jest dostępnych w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="90a15-174">It provides access to 20,000 more APIs than are available in .NET Core.</span></span> <span data-ttu-id="90a15-175">Te interfejsy API i obejmuje dodatkowe typy w <xref:System.Drawing?displayProperty=nameWithType> przestrzeni nazw, <xref:System.Diagnostics.EventLog> klasy, usługi WMI, liczniki wydajności, usług Windows i Windows rejestru typów i członków.</span><span class="sxs-lookup"><span data-stu-id="90a15-175">These APIs include types in the <xref:System.Drawing?displayProperty=nameWithType> namespace, the <xref:System.Diagnostics.EventLog> class, WMI, Performance Counters, Windows Services, and the Windows registry types and members.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="90a15-176">Ulepszenia kompilatora JIT</span><span class="sxs-lookup"><span data-stu-id="90a15-176">JIT compiler improvements</span></span>

<span data-ttu-id="90a15-177">.NET core zawiera nową technologię kompilatora JIT, o nazwie *warstwowego kompilacji* (znany także jako *adaptacyjne optymalizacji*), może znacznie poprawić wydajność.</span><span class="sxs-lookup"><span data-stu-id="90a15-177">.NET Core incorporates a new JIT compiler technology called *tiered compilation* (also known as *adaptive optimization*) that can significantly improve performance.</span></span> <span data-ttu-id="90a15-178">Warstwowe kompilacja jest ustawienie zgłoszenie zgody na uczestnictwo.</span><span class="sxs-lookup"><span data-stu-id="90a15-178">Tiered compilation is an opt-in setting.</span></span>

<span data-ttu-id="90a15-179">Jedną z ważnych zadania wykonywane przez kompilator JIT jest zoptymalizowanie wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="90a15-179">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="90a15-180">Jednak dla ścieżek kodu rzadko używanych kompilator może poświęcić więcej czasu na optymalizację kodu niż środowisko uruchomieniowe spędzony przez uruchamianie kodu w sposób niezoptymalizowany.</span><span class="sxs-lookup"><span data-stu-id="90a15-180">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends running unoptimized code.</span></span> <span data-ttu-id="90a15-181">Kompilacja warstwowego wprowadzono dwa etapów w ramach kompilacji JIT:</span><span class="sxs-lookup"><span data-stu-id="90a15-181">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="90a15-182">A **najpierw warstwy**, która generuje kod tak szybko, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="90a15-182">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="90a15-183">A **Druga warstwa**, która generuje zoptymalizowanego kodu dla tych metod, które są często wykonywane.</span><span class="sxs-lookup"><span data-stu-id="90a15-183">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="90a15-184">Druga warstwa kompilacji odbywa się w sposób równoległy, aby uzyskać lepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="90a15-184">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="90a15-185">Możesz zdecydować się na warstwowy kompilacji na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="90a15-185">You can opt into tiered compilation in either of two ways.</span></span>

- <span data-ttu-id="90a15-186">Aby używać warstwowego kompilacji w projektach korzystających z zestawu SDK programu .NET Core 2.1, Ustaw następującą zmienną środowiskową:</span><span class="sxs-lookup"><span data-stu-id="90a15-186">To use tiered compilation in all projects that use the .NET Core 2.1 SDK, set the following environment variable:</span></span>

  ```console
  COMPlus_TieredCompilation="1"
  ```

- <span data-ttu-id="90a15-187">Aby użyć kompilacji warstwowego na poszczególnych projektów, należy dodać `<TieredCompilation>` właściwość `<PropertyGroup>` części pliku projektu MSBuild, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="90a15-187">To use tiered compilation on a per-project basis, add the `<TieredCompilation>` property to the `<PropertyGroup>` section of the MSBuild project file, as the following example shows:</span></span>

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a><span data-ttu-id="90a15-188">Zmiany interfejsu API</span><span class="sxs-lookup"><span data-stu-id="90a15-188">API changes</span></span>

### <a name="spant-and-memoryt"></a><span data-ttu-id="90a15-189">`Span<T>` i `Memory<T>`</span><span class="sxs-lookup"><span data-stu-id="90a15-189">`Span<T>` and `Memory<T>`</span></span>

<span data-ttu-id="90a15-190">.NET core 2.1 zawiera kilka nowych typów, które sprawiają, że praca z tablicami i inne rodzaje pamięci znacznie bardziej efektywne.</span><span class="sxs-lookup"><span data-stu-id="90a15-190">.NET Core 2.1 includes some new types that make working with arrays and other types of memory much more efficient.</span></span> <span data-ttu-id="90a15-191">Nowe typy obejmują:</span><span class="sxs-lookup"><span data-stu-id="90a15-191">The new types include:</span></span>

- <span data-ttu-id="90a15-192"><xref:System.Span%601?displayProperty=nameWithType> i <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="90a15-192"><xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="90a15-193"><xref:System.Memory%601?displayProperty=nameWithType> i <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="90a15-193"><xref:System.Memory%601?displayProperty=nameWithType> and <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="90a15-194">Bez tych typów przy przekazywaniu takie elementy jako część tablicy lub sekcji bufora pamięci należy utworzyć kopię część danych przed przekazaniem go do metody.</span><span class="sxs-lookup"><span data-stu-id="90a15-194">Without these types, when passing such items as a portion of an array or a section of a memory buffer, you have to make a copy of some portion of the data before passing it to a method.</span></span> <span data-ttu-id="90a15-195">Te typy zapewniają wirtualny widok tych danych, która eliminuje potrzebę stosowania alokacji więcej pamięci i operacji kopiowania.</span><span class="sxs-lookup"><span data-stu-id="90a15-195">These types provide a virtual view of that data that eliminates the need for the additional memory allocation and copy operations.</span></span>

<span data-ttu-id="90a15-196">W poniższym przykładzie użyto <xref:System.Span%601> i <xref:System.Memory%601> wystąpienia, aby przedstawić widok wirtualny 10 elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="90a15-196">The following example uses a <xref:System.Span%601> and <xref:System.Memory%601> instance to provide a virtual view of 10 elements of an array.</span></span>

[!CODE-csharp[Span\<T>](~/samples/core/whats-new/whats-new-in-21/cs/program.cs)]

[!CODE-vb[Memory\<T>](~/samples/core/whats-new/whats-new-in-21/vb/program.vb)]

### <a name="brotli-compression"></a><span data-ttu-id="90a15-197">Kompresja Brotli</span><span class="sxs-lookup"><span data-stu-id="90a15-197">Brotli compression</span></span>

<span data-ttu-id="90a15-198">.NET core 2.1 dodaje obsługę Brotli kompresji i dekompresji.</span><span class="sxs-lookup"><span data-stu-id="90a15-198">.NET Core 2.1 adds support for Brotli compression and decompression.</span></span> <span data-ttu-id="90a15-199">Brotli to algorytm kompresji bezstratne ogólnego przeznaczenia, który jest zdefiniowany w [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) i są obsługiwane w większości przeglądarek sieci web i serwery główne sieci web.</span><span class="sxs-lookup"><span data-stu-id="90a15-199">Brotli is a general-purpose lossless compression algorithm that is defined in [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) and is supported by most web browsers and major web servers.</span></span> <span data-ttu-id="90a15-200">Można użyć, na podstawie strumienia <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> klasy lub o wysokiej wydajności na podstawie zakresu <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> i <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="90a15-200">You can use the stream-based <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> class or the high-performance span-based <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> and <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> classes.</span></span> <span data-ttu-id="90a15-201">W poniższym przykładzie pokazano metody kompresji <xref:System.IO.Compression.BrotliStream> klasy:</span><span class="sxs-lookup"><span data-stu-id="90a15-201">The following example illustrates compression with the <xref:System.IO.Compression.BrotliStream> class:</span></span>

[!CODE-csharp[Brotli compression](~/samples/core/whats-new/whats-new-in-21/cs/brotli.cs#1)]

<span data-ttu-id="90a15-202"><xref:System.IO.Compression.BrotliStream> Zachowanie jest taka sama jak <xref:System.IO.Compression.DeflateStream> i <xref:System.IO.Compression.GZipStream>, który można łatwo przekonwertować kodu, który wywołuje te interfejsy API do <xref:System.IO.Compression.BrotliStream>.</span><span class="sxs-lookup"><span data-stu-id="90a15-202">The <xref:System.IO.Compression.BrotliStream> behavior is the same as <xref:System.IO.Compression.DeflateStream> and <xref:System.IO.Compression.GZipStream>, which makes it easy to convert code that calls these APIs to <xref:System.IO.Compression.BrotliStream>.</span></span>

### <a name="new-cryptography-apis-and-cryptography-improvements"></a><span data-ttu-id="90a15-203">Nowe elementy interfejsu API kryptografii i ulepszenia kryptografii</span><span class="sxs-lookup"><span data-stu-id="90a15-203">New cryptography APIs and cryptography improvements</span></span>

<span data-ttu-id="90a15-204">.NET core 2.1 zawiera wiele udoskonaleń cryptography API:</span><span class="sxs-lookup"><span data-stu-id="90a15-204">.NET Core 2.1 includes numerous enhancements to the cryptography APIs:</span></span>

- <span data-ttu-id="90a15-205"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> jest dostępna w pakiecie System.Security.Cryptography.Pkcs.</span><span class="sxs-lookup"><span data-stu-id="90a15-205"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> is available in the System.Security.Cryptography.Pkcs package.</span></span> <span data-ttu-id="90a15-206">Implementacja jest taka sama jak <xref:System.Security.Cryptography.Pkcs.SignedCms> klasy w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="90a15-206">The implementation is the same as the <xref:System.Security.Cryptography.Pkcs.SignedCms> class in the .NET Framework.</span></span>

- <span data-ttu-id="90a15-207">Nowe przeciążenia <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> i <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> metody akceptuje identyfikator algorytmu wyznaczania wartości skrótu, umożliwiając metodom wywołującym można pobrać wartości odcisku palca certyfikatu, przy użyciu algorytmów niż SHA-1.</span><span class="sxs-lookup"><span data-stu-id="90a15-207">New overloads of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> and <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> methods accept a hash algorithm identifier to enable callers to get certificate thumbprint values using algorithms other than SHA-1.</span></span>

- <span data-ttu-id="90a15-208">Nowe <xref:System.Span%601>— oparte na kryptografii interfejsy API są dostępne do tworzenia skrótu HMAC, kryptograficzne Generowanie liczby losowej, asymetryczne generowania, przetwarzania asymetrycznego podpisu i szyfrowania RSA.</span><span class="sxs-lookup"><span data-stu-id="90a15-208">New <xref:System.Span%601>-based cryptography APIs are available for hashing, HMAC, cryptographic random number generation, asymmetric signature generation, asymmetric signature processing, and RSA encryption.</span></span>

- <span data-ttu-id="90a15-209">Wydajność <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> ulepszono o około 15%, za pomocą <xref:System.Span%601>— na podstawie implementacji.</span><span class="sxs-lookup"><span data-stu-id="90a15-209">The performance of <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> has improved by about 15% by using a <xref:System.Span%601>-based implementation.</span></span>

- <span data-ttu-id="90a15-210">Nowy <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> klasa zawiera dwie nowe metody:</span><span class="sxs-lookup"><span data-stu-id="90a15-210">The new <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> class includes two new methods:</span></span>

  - <span data-ttu-id="90a15-211"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> ma ustaloną ilość czasu, aby powrócić do dowolnego dwóch danych wejściowych o takiej samej długości, która sprawia, że nadaje się do użytku w kryptograficznych weryfikacji, aby uniknąć, przyczyniając się do czasu informacji kanału po stronie.</span><span class="sxs-lookup"><span data-stu-id="90a15-211"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> takes a fixed amount of time to return for any two inputs of the same length, which makes it suitable for use in cryptographic verification to avoid contributing to timing side-channel information.</span></span>

  - <span data-ttu-id="90a15-212"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> to nie można zoptymalizować procedura czyszczenia pamięci.</span><span class="sxs-lookup"><span data-stu-id="90a15-212"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> is a memory-clearing routine that cannot be optimized.</span></span>

- <span data-ttu-id="90a15-213">Statyczne <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> wypełnienia metoda <xref:System.Span%601> przy użyciu wartości losowych.</span><span class="sxs-lookup"><span data-stu-id="90a15-213">The static <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> method fills a <xref:System.Span%601> with random values.</span></span>

- <span data-ttu-id="90a15-214"><xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> Jest teraz obsługiwana w systemie Linux i maxOS.</span><span class="sxs-lookup"><span data-stu-id="90a15-214">The <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> is now supported on Linux and maxOS.</span></span>

- <span data-ttu-id="90a15-215">Grupa Diffie'ego-Hellmana krzywej eliptycznej (ECDH) jest teraz dostępna w <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> klasy rodziny.</span><span class="sxs-lookup"><span data-stu-id="90a15-215">Elliptic-Curve Diffie-Hellman (ECDH) is now available in the <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> class family.</span></span> <span data-ttu-id="90a15-216">Obszar powierzchni jest taka sama, jak w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="90a15-216">The surface area is the same as in the .NET Framework.</span></span>

- <span data-ttu-id="90a15-217">Wystąpienie zwrócone przez <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> zaszyfrować lub odszyfrować za pomocą OAEP przy użyciu skrótu SHA-2, a także Generowanie lub zweryfikować podpisu RSA-PSS przy użyciu usługi.</span><span class="sxs-lookup"><span data-stu-id="90a15-217">The instance returned by <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> can encrypt or decrypt with OAEP using a SHA-2 digest, as well as generate or validate signatures using RSA-PSS.</span></span>

### <a name="sockets-improvements"></a><span data-ttu-id="90a15-218">Ulepszenia gniazda</span><span class="sxs-lookup"><span data-stu-id="90a15-218">Sockets improvements</span></span>

<span data-ttu-id="90a15-219">.NET core zawiera nowy typ <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>oraz nowych <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, które stanowią podstawę sieci wyższego poziomu interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="90a15-219">.NET Core includes a new type, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, and a rewritten <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, that form the basis of higher-level networking APIs.</span></span>  <span data-ttu-id="90a15-220"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, na przykład, będącą podstawą <xref:System.Net.Http.HttpClient> implementacji.</span><span class="sxs-lookup"><span data-stu-id="90a15-220"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, for example, is the basis of the <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="90a15-221">W poprzednich wersjach programu .NET Core API wyższego poziomu znajdowały się na implementacji sieci.</span><span class="sxs-lookup"><span data-stu-id="90a15-221">In previous versions of .NET Core, higher-level APIs were based on native networking implementations.</span></span>

<span data-ttu-id="90a15-222">Implementacja gniazda, wprowadzone w programie .NET Core 2.1 ma szereg zalet:</span><span class="sxs-lookup"><span data-stu-id="90a15-222">The sockets implementation introduced in .NET Core 2.1 has a number of advantages:</span></span>

- <span data-ttu-id="90a15-223">Poprawa istotnie poprawiającą wydajność w porównaniu z poprzednim wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="90a15-223">A significant performance improvement when compared with the previous implementation.</span></span>

- <span data-ttu-id="90a15-224">Eliminacja zależności platformy, która upraszcza wdrażanie i obsługę.</span><span class="sxs-lookup"><span data-stu-id="90a15-224">Elimination of platform dependencies, which simplifies deployment and servicing.</span></span>

- <span data-ttu-id="90a15-225">Spójne zachowanie na wszystkich platformach .NET Core.</span><span class="sxs-lookup"><span data-stu-id="90a15-225">Consistent behavior across all .NET Core platforms.</span></span>

<span data-ttu-id="90a15-226"><xref:System.Net.Http.SocketsHttpHandler> jest implementacją domyślną w programie .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="90a15-226"><xref:System.Net.Http.SocketsHttpHandler> is the default implementation in .NET Core 2.1.</span></span> <span data-ttu-id="90a15-227">Jednak należy skonfigurować aplikację do starszej wersji <xref:System.Net.Http.HttpClientHandler> klasy przez wywołanie metody <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> metody:</span><span class="sxs-lookup"><span data-stu-id="90a15-227">However, you can configure your application to use the older <xref:System.Net.Http.HttpClientHandler> class by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method:</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", False)
```

<span data-ttu-id="90a15-228">Możesz również użyć środowiska zmiennej, aby zrezygnować z przy użyciu gniazd implementacji na podstawie <xref:System.Net.Http.SocketsHttpHandler>.</span><span class="sxs-lookup"><span data-stu-id="90a15-228">You can also use an environment variable to opt out of using sockets implementations based on <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="90a15-229">Aby to zrobić, należy ustawić `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` do jednej `false` lub równa 0.</span><span class="sxs-lookup"><span data-stu-id="90a15-229">To do this, set the `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` to either `false` or 0.</span></span>

<span data-ttu-id="90a15-230">W Windows, możesz również używać <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, która opiera się na natywnych implementacji lub <xref:System.Net.Http.SocketsHttpHandler> klasy przez przekazanie wystąpienia klasy do <xref:System.Net.Http.HttpClient> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="90a15-230">On Windows, you can also choose to use <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, which relies on a native implementation, or the <xref:System.Net.Http.SocketsHttpHandler> class by passing an instance of the class to the <xref:System.Net.Http.HttpClient> constructor.</span></span>

<span data-ttu-id="90a15-231">W systemie Linux i macOS, można skonfigurować tylko <xref:System.Net.Http.HttpClient> na zasadzie na proces.</span><span class="sxs-lookup"><span data-stu-id="90a15-231">On Linux and macOS, you can only configure <xref:System.Net.Http.HttpClient> on a per-process basis.</span></span> <span data-ttu-id="90a15-232">W systemie Linux, należy wdrożyć [libcurl](https://curl.haxx.se/libcurl/) Jeśli chcesz używać starego <xref:System.Net.Http.HttpClient> implementacji.</span><span class="sxs-lookup"><span data-stu-id="90a15-232">On Linux, you need to deploy [libcurl](https://curl.haxx.se/libcurl/) if you want to use the old <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="90a15-233">(Jest instalowany przy użyciu platformy .NET Core 2.0.)</span><span class="sxs-lookup"><span data-stu-id="90a15-233">(It is installed with .NET Core 2.0.)</span></span>

## <a name="see-also"></a><span data-ttu-id="90a15-234">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90a15-234">See also</span></span>

* [<span data-ttu-id="90a15-235">Co nowego w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="90a15-235">What's new in .NET Core</span></span>](index.md)  
* [<span data-ttu-id="90a15-236">Nowe funkcje programu EF Core 2.1</span><span class="sxs-lookup"><span data-stu-id="90a15-236">New features in EF Core 2.1</span></span>](/ef/core/what-is-new/ef-core-2.1)  
* [<span data-ttu-id="90a15-237">What's new in platformy ASP.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="90a15-237">What's new in ASP.NET Core 2.1</span></span>](/aspnet/core/aspnetcore-2.1)
