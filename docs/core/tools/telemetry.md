---
title: Dane telemetryczne zestawu SDK programu .NET core
description: Poznaj funkcje telemetryczne zestawu .NET Core SDK, które zbierają informacje o użyciu dla analizy, które dane są zbierane i jak go wyłączyć.
author: richlander
ms.date: 06/20/2018
ms.custom: seodec18
ms.openlocfilehash: 82410863c81faa95edfb120c95ec6bc186ed1328
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64751678"
---
# <a name="net-core-sdk-telemetry"></a><span data-ttu-id="12d67-103">Dane telemetryczne zestawu SDK programu .NET core</span><span class="sxs-lookup"><span data-stu-id="12d67-103">.NET Core SDK telemetry</span></span>

<span data-ttu-id="12d67-104">[Zestawu .NET Core SDK](index.md) obejmuje [funkcji telemetrii](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry) które zbiera informacje o użyciu.</span><span class="sxs-lookup"><span data-stu-id="12d67-104">The [.NET Core SDK](index.md) includes a [telemetry feature](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry) that collects usage information.</span></span> <span data-ttu-id="12d67-105">Należy pamiętać, że zespół .NET wiedział, jak te narzędzia są używane, dzięki czemu można poprawić.</span><span class="sxs-lookup"><span data-stu-id="12d67-105">It's important that the .NET Team understands how the tools are used so they can be improved.</span></span> <span data-ttu-id="12d67-106">Aby uzyskać więcej informacji, zobacz [poznane z platformy .NET Core SDK Telemetrii](https://devblogs.microsoft.com/dotnet/what-weve-learned-from-net-core-sdk-telemetry/).</span><span class="sxs-lookup"><span data-stu-id="12d67-106">For more information, see [What we've learned from .NET Core SDK Telemetry](https://devblogs.microsoft.com/dotnet/what-weve-learned-from-net-core-sdk-telemetry/).</span></span>

<span data-ttu-id="12d67-107">Zebrane dane są anonimowe i opublikowane w zagregowanej formie do użycia przez firmę Microsoft i społeczności w ramach [licencji Creative Commons: uznanie autorstwa License](https://creativecommons.org/licenses/by/4.0/).</span><span class="sxs-lookup"><span data-stu-id="12d67-107">The collected data is anonymous and published in an aggregated form for use by both Microsoft and the community under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span>

## <a name="scope"></a><span data-ttu-id="12d67-108">Scope</span><span class="sxs-lookup"><span data-stu-id="12d67-108">Scope</span></span>

<span data-ttu-id="12d67-109">`dotnet` Polecenie służy do uruchamiania aplikacji i interfejsu wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="12d67-109">The `dotnet` command is used to launch both apps and the .NET Core CLI.</span></span> <span data-ttu-id="12d67-110">`dotnet` Samo polecenie nie zbiera dane telemetryczne.</span><span class="sxs-lookup"><span data-stu-id="12d67-110">The `dotnet` command itself doesn't collect telemetry.</span></span> <span data-ttu-id="12d67-111">Polecenia interfejsu wiersza polecenia platformy .NET Core są uruchamiane przez `dotnet` polecenia zbieranie danych telemetrycznych.</span><span class="sxs-lookup"><span data-stu-id="12d67-111">The .NET Core CLI commands run by the `dotnet` command collect the telemetry.</span></span>

<span data-ttu-id="12d67-112">Dane telemetryczne *nie włączono* przy użyciu `dotnet` polecenia, za pomocą polecenia, nie dołączonych:</span><span class="sxs-lookup"><span data-stu-id="12d67-112">Telemetry *isn't enabled* when using the `dotnet` command itself, with no command attached:</span></span>

- `dotnet`
- `dotnet [path-to-app]`

<span data-ttu-id="12d67-113">Dane telemetryczne *włączono* przy użyciu [poleceń interfejsu wiersza polecenia platformy .NET Core](index.md), takich jak:</span><span class="sxs-lookup"><span data-stu-id="12d67-113">Telemetry *is enabled* when using the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`

## <a name="how-to-opt-out"></a><span data-ttu-id="12d67-114">Jak zrezygnować</span><span class="sxs-lookup"><span data-stu-id="12d67-114">How to opt out</span></span>

<span data-ttu-id="12d67-115">Funkcja danych telemetrycznych zestawu SDK programu .NET Core jest włączona domyślnie.</span><span class="sxs-lookup"><span data-stu-id="12d67-115">The .NET Core SDK telemetry feature is enabled by default.</span></span> <span data-ttu-id="12d67-116">Zrezygnować z funkcji danych telemetrycznych przez ustawienie `DOTNET_CLI_TELEMETRY_OPTOUT` zmiennej środowiskowej, aby `1` lub `true`.</span><span class="sxs-lookup"><span data-stu-id="12d67-116">Opt out of the telemetry feature by setting the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

## <a name="data-points"></a><span data-ttu-id="12d67-117">Punkty danych</span><span class="sxs-lookup"><span data-stu-id="12d67-117">Data points</span></span>

<span data-ttu-id="12d67-118">Ta funkcja zbiera następujące dane:</span><span class="sxs-lookup"><span data-stu-id="12d67-118">The feature collects the following data:</span></span>

- <span data-ttu-id="12d67-119">Sygnatura czasowa wywołania&#8224;</span><span class="sxs-lookup"><span data-stu-id="12d67-119">Timestamp of invocation&#8224;</span></span>
- <span data-ttu-id="12d67-120">Polecenie wywoływane (na przykład "build")&#8224;</span><span class="sxs-lookup"><span data-stu-id="12d67-120">Command invoked (for example, "build")&#8224;</span></span>
- <span data-ttu-id="12d67-121">Trzy octet adres IP używany do określenia lokalizacji geograficznej&#8224;</span><span class="sxs-lookup"><span data-stu-id="12d67-121">Three octet IP address used to determine geographical location&#8224;</span></span>
- <span data-ttu-id="12d67-122">`ExitCode` polecenia</span><span class="sxs-lookup"><span data-stu-id="12d67-122">`ExitCode` of the command</span></span>
- <span data-ttu-id="12d67-123">Narzędzie Test runner (dla projektów testowych)</span><span class="sxs-lookup"><span data-stu-id="12d67-123">Test runner (for test projects)</span></span>
- <span data-ttu-id="12d67-124">Wersja systemu operacyjnego i&#8224;</span><span class="sxs-lookup"><span data-stu-id="12d67-124">Operating system and version&#8224;</span></span>
- <span data-ttu-id="12d67-125">Czy identyfikatory środowiska uruchomieniowego znajdują się w węźle środowiska uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="12d67-125">Whether runtime IDs are present in the runtimes node</span></span>
- <span data-ttu-id="12d67-126">Wersja zestawu .NET core SDK&#8224;</span><span class="sxs-lookup"><span data-stu-id="12d67-126">.NET Core SDK version&#8224;</span></span>

<span data-ttu-id="12d67-127">&#8224;Ta metryka jest publikowany.</span><span class="sxs-lookup"><span data-stu-id="12d67-127">&#8224;This metric is published.</span></span>

<span data-ttu-id="12d67-128">Począwszy od programu .NET Core 2.0 SDK nowe punkty danych są zbierane:</span><span class="sxs-lookup"><span data-stu-id="12d67-128">Starting with .NET Core 2.0 SDK, new data points are collected:</span></span>

- <span data-ttu-id="12d67-129">`dotnet` polecenie Opcje i argumenty: tylko znane opcje i argumenty są zbierane (nie dowolne ciągi).</span><span class="sxs-lookup"><span data-stu-id="12d67-129">`dotnet` command arguments and options: only known arguments and options are collected (not arbitrary strings).</span></span>
- <span data-ttu-id="12d67-130">Czy zestaw SDK jest uruchomiona w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="12d67-130">Whether the SDK is running in a container.</span></span>
- <span data-ttu-id="12d67-131">Platformy docelowe.</span><span class="sxs-lookup"><span data-stu-id="12d67-131">Target frameworks.</span></span>
- <span data-ttu-id="12d67-132">Mieszana adres MAC: kryptograficznie (SHA256) anonimowe i unikatowy identyfikator dla maszyny.</span><span class="sxs-lookup"><span data-stu-id="12d67-132">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> <span data-ttu-id="12d67-133">Ta metryka nie jest opublikowana.</span><span class="sxs-lookup"><span data-stu-id="12d67-133">This metric isn't published.</span></span>
- <span data-ttu-id="12d67-134">Skrótu bieżącego katalogu roboczego.</span><span class="sxs-lookup"><span data-stu-id="12d67-134">Hashed current working directory.</span></span>

<span data-ttu-id="12d67-135">Ta funkcja nie zbiera danych osobowych, takich jak nazwy użytkowników lub adresy e-mail.</span><span class="sxs-lookup"><span data-stu-id="12d67-135">The feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="12d67-136">Go nie skanowanie Twojego kodu, a nie wyodrębnić poufnych danych na poziomie projektu, takie jak nazwa repozytorium i autora.</span><span class="sxs-lookup"><span data-stu-id="12d67-136">It doesn't scan your code and doesn't extract sensitive project-level data, such as name, repo, or author.</span></span> <span data-ttu-id="12d67-137">Dane są przesyłane w bezpieczny sposób do serwerów firmy Microsoft przy użyciu [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technologii, przechowywane w obszarze ograniczony dostęp i opublikowane w ramach rygorystyczne kontrole zabezpieczeń z bezpiecznym [usługi Azure Storage](https://azure.microsoft.com/services/storage/) systemów.</span><span class="sxs-lookup"><span data-stu-id="12d67-137">The data is sent securely to Microsoft servers using [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="12d67-138">Zespół .NET chce wiedzieć, jak te narzędzia są używane, a jeśli działają poprawnie, nie co w przypadku tworzenia za pomocą narzędzi.</span><span class="sxs-lookup"><span data-stu-id="12d67-138">The .NET team wants to know how the tools are used and if they're working well, not what you're building with the tools.</span></span> <span data-ttu-id="12d67-139">Jeśli podejrzewasz, że zbiera dane telemetryczne poufne dane, lub że dane są insecurely lub niewłaściwie obsługiwane, Prześlij zgłoszenie do [interfejsu wiersza poleceniadotnet/](https://github.com/dotnet/cli/issues) repozytorium na potrzeby badania.</span><span class="sxs-lookup"><span data-stu-id="12d67-139">If you suspect that the telemetry is collecting sensitive data or that the data is being insecurely or inappropriately handled, file an issue in the [dotnet/cli](https://github.com/dotnet/cli/issues) repository for investigation.</span></span>

## <a name="published-data"></a><span data-ttu-id="12d67-140">Opublikowane dane</span><span class="sxs-lookup"><span data-stu-id="12d67-140">Published data</span></span>

<span data-ttu-id="12d67-141">Dane publikowane jest dostępny co kwartał i znajduje się w [danych użycia programu .NET Core SDK](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span><span class="sxs-lookup"><span data-stu-id="12d67-141">Published data is available quarterly and are listed at [.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span></span> <span data-ttu-id="12d67-142">Dostępne są następujące kolumny w pliku danych:</span><span class="sxs-lookup"><span data-stu-id="12d67-142">The columns of a data file are:</span></span>

- <span data-ttu-id="12d67-143">Znacznik czasu</span><span class="sxs-lookup"><span data-stu-id="12d67-143">Timestamp</span></span>
- <span data-ttu-id="12d67-144">Occurrences&#8224;</span><span class="sxs-lookup"><span data-stu-id="12d67-144">Occurrences&#8224;</span></span>
- <span data-ttu-id="12d67-145">Polecenie</span><span class="sxs-lookup"><span data-stu-id="12d67-145">Command</span></span>
- <span data-ttu-id="12d67-146">Geography&#8225;</span><span class="sxs-lookup"><span data-stu-id="12d67-146">Geography&#8225;</span></span>
- <span data-ttu-id="12d67-147">Rodzina systemów operacyjnych</span><span class="sxs-lookup"><span data-stu-id="12d67-147">OSFamily</span></span>
- <span data-ttu-id="12d67-148">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="12d67-148">RuntimeID</span></span>
- <span data-ttu-id="12d67-149">OSVersion</span><span class="sxs-lookup"><span data-stu-id="12d67-149">OSVersion</span></span>
- <span data-ttu-id="12d67-150">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="12d67-150">SDKVersion</span></span>

<span data-ttu-id="12d67-151">&#8224;*Wystąpień* kolumnie jest wyświetlana łączna liczba użycia tego polecenia dla tego wiersza metryk tego samego dnia.</span><span class="sxs-lookup"><span data-stu-id="12d67-151">&#8224;The *Occurrences* column displays the aggregate count of that command's use for that row's metrics that day.</span></span>

<span data-ttu-id="12d67-152">&#8225;Zazwyczaj *Geografia* kolumnie jest wyświetlana nazwa kraju.</span><span class="sxs-lookup"><span data-stu-id="12d67-152">&#8225;Typically, the *Geography* column displays the name of a country.</span></span> <span data-ttu-id="12d67-153">W niektórych przypadkach kontynent z Antarktyda pojawia się w tej kolumnie, albo z powodu pracowników naukowo-badawczych przy użyciu platformy .NET Core w Antarktyda lub nieprawidłowej lokalizacji danych.</span><span class="sxs-lookup"><span data-stu-id="12d67-153">In some cases, the continent of Antarctica appears in this column, either due to researchers using .NET Core in Antarctica or incorrect location data.</span></span>

### <a name="example"></a><span data-ttu-id="12d67-154">Przykład</span><span class="sxs-lookup"><span data-stu-id="12d67-154">Example</span></span>

| <span data-ttu-id="12d67-155">Znacznik czasu</span><span class="sxs-lookup"><span data-stu-id="12d67-155">Timestamp</span></span>      | <span data-ttu-id="12d67-156">Wystąpienia</span><span class="sxs-lookup"><span data-stu-id="12d67-156">Occurrences</span></span> | <span data-ttu-id="12d67-157">Polecenie</span><span class="sxs-lookup"><span data-stu-id="12d67-157">Command</span></span> | <span data-ttu-id="12d67-158">Lokalizacja geograficzna</span><span class="sxs-lookup"><span data-stu-id="12d67-158">Geography</span></span> | <span data-ttu-id="12d67-159">Rodzina systemów operacyjnych</span><span class="sxs-lookup"><span data-stu-id="12d67-159">OSFamily</span></span> | <span data-ttu-id="12d67-160">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="12d67-160">RuntimeID</span></span>     | <span data-ttu-id="12d67-161">OSVersion</span><span class="sxs-lookup"><span data-stu-id="12d67-161">OSVersion</span></span> | <span data-ttu-id="12d67-162">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="12d67-162">SDKVersion</span></span> |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| <span data-ttu-id="12d67-163">4/16/2017 0:00</span><span class="sxs-lookup"><span data-stu-id="12d67-163">4/16/2017 0:00</span></span> | <span data-ttu-id="12d67-164">8</span><span class="sxs-lookup"><span data-stu-id="12d67-164">8</span></span>           | <span data-ttu-id="12d67-165">Uruchom</span><span class="sxs-lookup"><span data-stu-id="12d67-165">run</span></span>     | <span data-ttu-id="12d67-166">Uganda</span><span class="sxs-lookup"><span data-stu-id="12d67-166">Uganda</span></span>    | <span data-ttu-id="12d67-167">Darwin</span><span class="sxs-lookup"><span data-stu-id="12d67-167">Darwin</span></span>   | <span data-ttu-id="12d67-168">osx.10.12-x64</span><span class="sxs-lookup"><span data-stu-id="12d67-168">osx.10.12-x64</span></span> | <span data-ttu-id="12d67-169">10.12</span><span class="sxs-lookup"><span data-stu-id="12d67-169">10.12</span></span>     | <span data-ttu-id="12d67-170">1.0.1</span><span class="sxs-lookup"><span data-stu-id="12d67-170">1.0.1</span></span>      |

### <a name="datasets"></a><span data-ttu-id="12d67-171">Zestawy danych</span><span class="sxs-lookup"><span data-stu-id="12d67-171">Datasets</span></span>

- [<span data-ttu-id="12d67-172">2016 - K3</span><span class="sxs-lookup"><span data-stu-id="12d67-172">2016 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)
- [<span data-ttu-id="12d67-173">2016 - KWARTAŁ 4</span><span class="sxs-lookup"><span data-stu-id="12d67-173">2016 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)
- [<span data-ttu-id="12d67-174">2017 - 1.</span><span class="sxs-lookup"><span data-stu-id="12d67-174">2017 - Q1</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)
- [<span data-ttu-id="12d67-175">2017 - Q2</span><span class="sxs-lookup"><span data-stu-id="12d67-175">2017 - Q2</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)
- [<span data-ttu-id="12d67-176">2017 - K3</span><span class="sxs-lookup"><span data-stu-id="12d67-176">2017 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q3.tsv)
- [<span data-ttu-id="12d67-177">2017 - KWARTAŁ 4</span><span class="sxs-lookup"><span data-stu-id="12d67-177">2017 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q4.tsv)

<span data-ttu-id="12d67-178">Dodatkowe zestawy danych są ogłaszane przy użyciu standardowego formatu adresu URL.</span><span class="sxs-lookup"><span data-stu-id="12d67-178">Additional datasets are posted using a standard URL format.</span></span> <span data-ttu-id="12d67-179">Zastąp `<YEAR>` rokiem i Zastąp `<QUARTER>` z kwartał roku (Użyj `1`, `2`, `3`, lub `4`).</span><span class="sxs-lookup"><span data-stu-id="12d67-179">Replace `<YEAR>` with the year and replace `<QUARTER>` with the quarter of the year (use `1`, `2`, `3`, or `4`).</span></span> <span data-ttu-id="12d67-180">Pliki znajdują się w wartości rozdzielane znakami tabulacji (*TSV*) format.</span><span class="sxs-lookup"><span data-stu-id="12d67-180">The files are in tab-separated values (*TSV*) format.</span></span>

`https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv`

## <a name="license"></a><span data-ttu-id="12d67-181">Licencja</span><span class="sxs-lookup"><span data-stu-id="12d67-181">License</span></span>

<span data-ttu-id="12d67-182">Dystrybucja programu Microsoft .NET Core jest licencjonowany za pomocą [postanowienia licencyjne dotyczące oprogramowania firmy Microsoft: Mirosoft .NET Library](https://aka.ms/dotnet-core-eula).</span><span class="sxs-lookup"><span data-stu-id="12d67-182">The Microsoft distribution of .NET Core is licensed with the [Microsoft Software License Terms: Mirosoft .NET Library](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="12d67-183">Aby uzyskać szczegółowe informacje dotyczące zbierania i przetwarzania danych zobacz sekcję zatytułowaną "Dane".</span><span class="sxs-lookup"><span data-stu-id="12d67-183">For details on data collection and processing, see the section entitled "Data."</span></span>

<span data-ttu-id="12d67-184">[Pakiety .NET NuGet](https://www.nuget.org/profiles/dotnetframework) użyć tego samego licencji, ale nie włączysz danych telemetrycznych (zobacz [zakres](#scope)).</span><span class="sxs-lookup"><span data-stu-id="12d67-184">[.NET NuGet packages](https://www.nuget.org/profiles/dotnetframework) use the same license but don't enable telemetry (see [Scope](#scope)).</span></span>

## <a name="disclosure"></a><span data-ttu-id="12d67-185">Ujawnienie</span><span class="sxs-lookup"><span data-stu-id="12d67-185">Disclosure</span></span>

<span data-ttu-id="12d67-186">.NET Core SDK zawiera następujący tekst, przy pierwszym uruchomieniu jednego z [poleceń interfejsu wiersza polecenia platformy .NET Core](index.md) (na przykład `dotnet restore`).</span><span class="sxs-lookup"><span data-stu-id="12d67-186">The .NET Core SDK displays the following text when you first run one of the [.NET Core CLI commands](index.md) (for example, `dotnet restore`).</span></span> <span data-ttu-id="12d67-187">Tekst może się nieco różnić w zależności od wersji zestawu SDK jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="12d67-187">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="12d67-188">To środowisko "najpierw uruchom" to, jak firma Microsoft przekaże Ci o zbieraniu danych.</span><span class="sxs-lookup"><span data-stu-id="12d67-188">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

```console
Welcome to .NET Core!
---------------------
Learn more about .NET Core: https://aka.ms/dotnet-docs
Use 'dotnet --help' to see available commands or visit: https://aka.ms/dotnet-cli-docs

Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience.
The data is anonymous and doesn't include command-line arguments.
The data is collected by Microsoft and shared with the community.
You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

## <a name="see-also"></a><span data-ttu-id="12d67-189">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="12d67-189">See also</span></span>

- [<span data-ttu-id="12d67-190">Czego się nauczyliśmy z platformy .NET Core SDK Telemetrii</span><span class="sxs-lookup"><span data-stu-id="12d67-190">What we've learned from .NET Core SDK Telemetry</span></span>](https://devblogs.microsoft.com/dotnet/what-weve-learned-from-net-core-sdk-telemetry/)
- [<span data-ttu-id="12d67-191">Źródło odwołania danych telemetrycznych (repozytorium dotnet/cli)</span><span class="sxs-lookup"><span data-stu-id="12d67-191">Telemetry reference source (dotnet/cli repo)</span></span>](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)
- [<span data-ttu-id="12d67-192">Dane użycia zestawu SDK programu .NET core</span><span class="sxs-lookup"><span data-stu-id="12d67-192">.NET Core SDK Usage Data</span></span>](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)
