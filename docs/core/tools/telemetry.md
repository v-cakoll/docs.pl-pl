---
title: Dane telemetryczne zestawu SDK programu .NET core
description: Poznaj funkcje telemetryczne zestawu .NET Core SDK, które zbierają informacje o użyciu dla analizy, które dane są zbierane i jak go wyłączyć.
author: richlander
ms.date: 06/20/2018
ms.custom: seodec18
ms.openlocfilehash: 8b0b546d70eab837c2e075f839990870ae9ea6b1
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168848"
---
# <a name="net-core-sdk-telemetry"></a><span data-ttu-id="c5d38-103">Dane telemetryczne zestawu SDK programu .NET core</span><span class="sxs-lookup"><span data-stu-id="c5d38-103">.NET Core SDK telemetry</span></span>

<span data-ttu-id="c5d38-104">[Zestawu .NET Core SDK](index.md) obejmuje [funkcji telemetrii](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry) które zbiera informacje o użyciu.</span><span class="sxs-lookup"><span data-stu-id="c5d38-104">The [.NET Core SDK](index.md) includes a [telemetry feature](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry) that collects usage information.</span></span> <span data-ttu-id="c5d38-105">Należy pamiętać, że zespół .NET wiedział, jak te narzędzia są używane, dzięki czemu można poprawić.</span><span class="sxs-lookup"><span data-stu-id="c5d38-105">It's important that the .NET Team understands how the tools are used so they can be improved.</span></span> <span data-ttu-id="c5d38-106">Aby uzyskać więcej informacji, zobacz [poznane z platformy .NET Core SDK Telemetrii](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).</span><span class="sxs-lookup"><span data-stu-id="c5d38-106">For more information, see [What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).</span></span>

<span data-ttu-id="c5d38-107">Zebrane dane są anonimowe i opublikowane w zagregowanej formie do użycia przez firmę Microsoft i społeczności w ramach [licencji Creative Commons: uznanie autorstwa License](https://creativecommons.org/licenses/by/4.0/).</span><span class="sxs-lookup"><span data-stu-id="c5d38-107">The collected data is anonymous and published in an aggregated form for use by both Microsoft and the community under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span>

## <a name="scope"></a><span data-ttu-id="c5d38-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="c5d38-108">Scope</span></span>

<span data-ttu-id="c5d38-109">`dotnet` Polecenie służy do uruchamiania aplikacji i interfejsu wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c5d38-109">The `dotnet` command is used to launch both apps and the .NET Core CLI.</span></span> <span data-ttu-id="c5d38-110">`dotnet` Samo polecenie nie zbiera dane telemetryczne.</span><span class="sxs-lookup"><span data-stu-id="c5d38-110">The `dotnet` command itself doesn't collect telemetry.</span></span> <span data-ttu-id="c5d38-111">Polecenia interfejsu wiersza polecenia platformy .NET Core są uruchamiane przez `dotnet` polecenia zbieranie danych telemetrycznych.</span><span class="sxs-lookup"><span data-stu-id="c5d38-111">The .NET Core CLI commands run by the `dotnet` command collect the telemetry.</span></span>

<span data-ttu-id="c5d38-112">Dane telemetryczne *nie włączono* przy użyciu `dotnet` polecenia, za pomocą polecenia, nie dołączonych:</span><span class="sxs-lookup"><span data-stu-id="c5d38-112">Telemetry *isn't enabled* when using the `dotnet` command itself, with no command attached:</span></span>

- `dotnet`
- `dotnet [path-to-app]`

<span data-ttu-id="c5d38-113">Dane telemetryczne *włączono* przy użyciu [poleceń interfejsu wiersza polecenia platformy .NET Core](index.md), takich jak:</span><span class="sxs-lookup"><span data-stu-id="c5d38-113">Telemetry *is enabled* when using the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`

## <a name="how-to-opt-out"></a><span data-ttu-id="c5d38-114">Jak zrezygnować</span><span class="sxs-lookup"><span data-stu-id="c5d38-114">How to opt out</span></span>

<span data-ttu-id="c5d38-115">Funkcja danych telemetrycznych zestawu SDK programu .NET Core jest włączona domyślnie.</span><span class="sxs-lookup"><span data-stu-id="c5d38-115">The .NET Core SDK telemetry feature is enabled by default.</span></span> <span data-ttu-id="c5d38-116">Zrezygnować z funkcji danych telemetrycznych przez ustawienie `DOTNET_CLI_TELEMETRY_OPTOUT` zmiennej środowiskowej, aby `1` lub `true`.</span><span class="sxs-lookup"><span data-stu-id="c5d38-116">Opt out of the telemetry feature by setting the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

## <a name="data-points"></a><span data-ttu-id="c5d38-117">Punkty danych</span><span class="sxs-lookup"><span data-stu-id="c5d38-117">Data points</span></span>

<span data-ttu-id="c5d38-118">Ta funkcja zbiera następujące dane:</span><span class="sxs-lookup"><span data-stu-id="c5d38-118">The feature collects the following data:</span></span>

- <span data-ttu-id="c5d38-119">Sygnatura czasowa wywołania&#8224;</span><span class="sxs-lookup"><span data-stu-id="c5d38-119">Timestamp of invocation&#8224;</span></span>
- <span data-ttu-id="c5d38-120">Polecenie wywoływane (na przykład "build")&#8224;</span><span class="sxs-lookup"><span data-stu-id="c5d38-120">Command invoked (for example, "build")&#8224;</span></span>
- <span data-ttu-id="c5d38-121">Trzy octet adres IP używany do określenia lokalizacji geograficznej&#8224;</span><span class="sxs-lookup"><span data-stu-id="c5d38-121">Three octet IP address used to determine geographical location&#8224;</span></span>
- <span data-ttu-id="c5d38-122">`ExitCode` polecenia</span><span class="sxs-lookup"><span data-stu-id="c5d38-122">`ExitCode` of the command</span></span>
- <span data-ttu-id="c5d38-123">Narzędzie Test runner (dla projektów testowych)</span><span class="sxs-lookup"><span data-stu-id="c5d38-123">Test runner (for test projects)</span></span>
- <span data-ttu-id="c5d38-124">Wersja systemu operacyjnego i&#8224;</span><span class="sxs-lookup"><span data-stu-id="c5d38-124">Operating system and version&#8224;</span></span>
- <span data-ttu-id="c5d38-125">Czy identyfikatory środowiska uruchomieniowego znajdują się w węźle środowiska uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="c5d38-125">Whether runtime IDs are present in the runtimes node</span></span>
- <span data-ttu-id="c5d38-126">Wersja zestawu .NET core SDK&#8224;</span><span class="sxs-lookup"><span data-stu-id="c5d38-126">.NET Core SDK version&#8224;</span></span>

<span data-ttu-id="c5d38-127">&#8224;Ta metryka jest publikowany.</span><span class="sxs-lookup"><span data-stu-id="c5d38-127">&#8224;This metric is published.</span></span>

<span data-ttu-id="c5d38-128">Począwszy od programu .NET Core 2.0 SDK nowe punkty danych są zbierane:</span><span class="sxs-lookup"><span data-stu-id="c5d38-128">Starting with .NET Core 2.0 SDK, new data points are collected:</span></span>

- <span data-ttu-id="c5d38-129">`dotnet` polecenie Opcje i argumenty: tylko znane opcje i argumenty są zbierane (nie dowolne ciągi).</span><span class="sxs-lookup"><span data-stu-id="c5d38-129">`dotnet` command arguments and options: only known arguments and options are collected (not arbitrary strings).</span></span>
- <span data-ttu-id="c5d38-130">Czy zestaw SDK jest uruchomiona w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="c5d38-130">Whether the SDK is running in a container.</span></span>
- <span data-ttu-id="c5d38-131">Platformy docelowe.</span><span class="sxs-lookup"><span data-stu-id="c5d38-131">Target frameworks.</span></span>
- <span data-ttu-id="c5d38-132">Mieszana adres MAC: kryptograficznie (SHA256) anonimowe i unikatowy identyfikator dla maszyny.</span><span class="sxs-lookup"><span data-stu-id="c5d38-132">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> <span data-ttu-id="c5d38-133">Ta metryka nie jest opublikowana.</span><span class="sxs-lookup"><span data-stu-id="c5d38-133">This metric isn't published.</span></span>
- <span data-ttu-id="c5d38-134">Skrótu bieżącego katalogu roboczego.</span><span class="sxs-lookup"><span data-stu-id="c5d38-134">Hashed current working directory.</span></span>

<span data-ttu-id="c5d38-135">Ta funkcja nie zbiera danych osobowych, takich jak nazwy użytkowników lub adresy e-mail.</span><span class="sxs-lookup"><span data-stu-id="c5d38-135">The feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="c5d38-136">Go nie skanowanie Twojego kodu, a nie wyodrębnić poufnych danych na poziomie projektu, takie jak nazwa repozytorium i autora.</span><span class="sxs-lookup"><span data-stu-id="c5d38-136">It doesn't scan your code and doesn't extract sensitive project-level data, such as name, repo, or author.</span></span> <span data-ttu-id="c5d38-137">Dane są przesyłane w bezpieczny sposób do serwerów firmy Microsoft przy użyciu [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technologii, przechowywane w obszarze ograniczony dostęp i opublikowane w ramach rygorystyczne kontrole zabezpieczeń z bezpiecznym [usługi Azure Storage](https://azure.microsoft.com/services/storage/) systemów.</span><span class="sxs-lookup"><span data-stu-id="c5d38-137">The data is sent securely to Microsoft servers using [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="c5d38-138">Zespół .NET chce wiedzieć, jak te narzędzia są używane, a jeśli działają poprawnie, nie co w przypadku tworzenia za pomocą narzędzi.</span><span class="sxs-lookup"><span data-stu-id="c5d38-138">The .NET team wants to know how the tools are used and if they're working well, not what you're building with the tools.</span></span> <span data-ttu-id="c5d38-139">Jeśli podejrzewasz, że zbiera dane telemetryczne poufne dane, lub że dane są insecurely lub niewłaściwie obsługiwane, Prześlij zgłoszenie do [interfejsu wiersza poleceniadotnet/](https://github.com/dotnet/cli/issues) repozytorium na potrzeby badania.</span><span class="sxs-lookup"><span data-stu-id="c5d38-139">If you suspect that the telemetry is collecting sensitive data or that the data is being insecurely or inappropriately handled, file an issue in the [dotnet/cli](https://github.com/dotnet/cli/issues) repository for investigation.</span></span>

## <a name="published-data"></a><span data-ttu-id="c5d38-140">Opublikowane dane</span><span class="sxs-lookup"><span data-stu-id="c5d38-140">Published data</span></span>

<span data-ttu-id="c5d38-141">Dane publikowane jest dostępny co kwartał i znajduje się w [danych użycia programu .NET Core SDK](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span><span class="sxs-lookup"><span data-stu-id="c5d38-141">Published data is available quarterly and are listed at [.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span></span> <span data-ttu-id="c5d38-142">Dostępne są następujące kolumny w pliku danych:</span><span class="sxs-lookup"><span data-stu-id="c5d38-142">The columns of a data file are:</span></span>

- <span data-ttu-id="c5d38-143">Znacznik czasu</span><span class="sxs-lookup"><span data-stu-id="c5d38-143">Timestamp</span></span>
- <span data-ttu-id="c5d38-144">Occurrences&#8224;</span><span class="sxs-lookup"><span data-stu-id="c5d38-144">Occurrences&#8224;</span></span>
- <span data-ttu-id="c5d38-145">Polecenie</span><span class="sxs-lookup"><span data-stu-id="c5d38-145">Command</span></span>
- <span data-ttu-id="c5d38-146">Geography&#8225;</span><span class="sxs-lookup"><span data-stu-id="c5d38-146">Geography&#8225;</span></span>
- <span data-ttu-id="c5d38-147">Rodzina systemów operacyjnych</span><span class="sxs-lookup"><span data-stu-id="c5d38-147">OSFamily</span></span>
- <span data-ttu-id="c5d38-148">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="c5d38-148">RuntimeID</span></span>
- <span data-ttu-id="c5d38-149">OSVersion</span><span class="sxs-lookup"><span data-stu-id="c5d38-149">OSVersion</span></span>
- <span data-ttu-id="c5d38-150">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="c5d38-150">SDKVersion</span></span>

<span data-ttu-id="c5d38-151">&#8224;*Wystąpień* kolumnie jest wyświetlana łączna liczba użycia tego polecenia dla tego wiersza metryk tego samego dnia.</span><span class="sxs-lookup"><span data-stu-id="c5d38-151">&#8224;The *Occurrences* column displays the aggregate count of that command's use for that row's metrics that day.</span></span>

<span data-ttu-id="c5d38-152">&#8225;Zazwyczaj *Geografia* kolumnie jest wyświetlana nazwa kraju.</span><span class="sxs-lookup"><span data-stu-id="c5d38-152">&#8225;Typically, the *Geography* column displays the name of a country.</span></span> <span data-ttu-id="c5d38-153">W niektórych przypadkach kontynent z Antarktyda pojawia się w tej kolumnie, albo z powodu pracowników naukowo-badawczych przy użyciu platformy .NET Core w Antarktyda lub nieprawidłowej lokalizacji danych.</span><span class="sxs-lookup"><span data-stu-id="c5d38-153">In some cases, the continent of Antarctica appears in this column, either due to researchers using .NET Core in Antarctica or incorrect location data.</span></span>

### <a name="example"></a><span data-ttu-id="c5d38-154">Przykład</span><span class="sxs-lookup"><span data-stu-id="c5d38-154">Example</span></span>

| <span data-ttu-id="c5d38-155">Znacznik czasu</span><span class="sxs-lookup"><span data-stu-id="c5d38-155">Timestamp</span></span>      | <span data-ttu-id="c5d38-156">Wystąpienia</span><span class="sxs-lookup"><span data-stu-id="c5d38-156">Occurrences</span></span> | <span data-ttu-id="c5d38-157">Polecenie</span><span class="sxs-lookup"><span data-stu-id="c5d38-157">Command</span></span> | <span data-ttu-id="c5d38-158">Lokalizacja geograficzna</span><span class="sxs-lookup"><span data-stu-id="c5d38-158">Geography</span></span> | <span data-ttu-id="c5d38-159">Rodzina systemów operacyjnych</span><span class="sxs-lookup"><span data-stu-id="c5d38-159">OSFamily</span></span> | <span data-ttu-id="c5d38-160">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="c5d38-160">RuntimeID</span></span>     | <span data-ttu-id="c5d38-161">OSVersion</span><span class="sxs-lookup"><span data-stu-id="c5d38-161">OSVersion</span></span> | <span data-ttu-id="c5d38-162">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="c5d38-162">SDKVersion</span></span> |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| <span data-ttu-id="c5d38-163">4/16/2017 0:00</span><span class="sxs-lookup"><span data-stu-id="c5d38-163">4/16/2017 0:00</span></span> | <span data-ttu-id="c5d38-164">8</span><span class="sxs-lookup"><span data-stu-id="c5d38-164">8</span></span>           | <span data-ttu-id="c5d38-165">Uruchom</span><span class="sxs-lookup"><span data-stu-id="c5d38-165">run</span></span>     | <span data-ttu-id="c5d38-166">Ugandyjski</span><span class="sxs-lookup"><span data-stu-id="c5d38-166">Uganda</span></span>    | <span data-ttu-id="c5d38-167">Darwin</span><span class="sxs-lookup"><span data-stu-id="c5d38-167">Darwin</span></span>   | <span data-ttu-id="c5d38-168">osx.10.12-x64</span><span class="sxs-lookup"><span data-stu-id="c5d38-168">osx.10.12-x64</span></span> | <span data-ttu-id="c5d38-169">10.12</span><span class="sxs-lookup"><span data-stu-id="c5d38-169">10.12</span></span>     | <span data-ttu-id="c5d38-170">1.0.1</span><span class="sxs-lookup"><span data-stu-id="c5d38-170">1.0.1</span></span>      |

### <a name="datasets"></a><span data-ttu-id="c5d38-171">Zestawy danych</span><span class="sxs-lookup"><span data-stu-id="c5d38-171">Datasets</span></span>

[<span data-ttu-id="c5d38-172">2016 - K3</span><span class="sxs-lookup"><span data-stu-id="c5d38-172">2016 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)  
[<span data-ttu-id="c5d38-173">2016 - KWARTAŁ 4</span><span class="sxs-lookup"><span data-stu-id="c5d38-173">2016 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)  
[<span data-ttu-id="c5d38-174">2017 - 1.</span><span class="sxs-lookup"><span data-stu-id="c5d38-174">2017 - Q1</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)  
[<span data-ttu-id="c5d38-175">2017 - Q2</span><span class="sxs-lookup"><span data-stu-id="c5d38-175">2017 - Q2</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)  
[<span data-ttu-id="c5d38-176">2017 - K3</span><span class="sxs-lookup"><span data-stu-id="c5d38-176">2017 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q3.tsv)  
[<span data-ttu-id="c5d38-177">2017 - KWARTAŁ 4</span><span class="sxs-lookup"><span data-stu-id="c5d38-177">2017 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q4.tsv)  

<span data-ttu-id="c5d38-178">Dodatkowe zestawy danych są ogłaszane przy użyciu standardowego formatu adresu URL.</span><span class="sxs-lookup"><span data-stu-id="c5d38-178">Additional datasets are posted using a standard URL format.</span></span> <span data-ttu-id="c5d38-179">Zastąp `<YEAR>` rokiem i Zastąp `<QUARTER>` z kwartał roku (Użyj `1`, `2`, `3`, lub `4`).</span><span class="sxs-lookup"><span data-stu-id="c5d38-179">Replace `<YEAR>` with the year and replace `<QUARTER>` with the quarter of the year (use `1`, `2`, `3`, or `4`).</span></span> <span data-ttu-id="c5d38-180">Pliki znajdują się w wartości rozdzielane znakami tabulacji (*TSV*) format.</span><span class="sxs-lookup"><span data-stu-id="c5d38-180">The files are in tab-separated values (*TSV*) format.</span></span>

`https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv`

## <a name="license"></a><span data-ttu-id="c5d38-181">Licencja</span><span class="sxs-lookup"><span data-stu-id="c5d38-181">License</span></span>

<span data-ttu-id="c5d38-182">Dystrybucja programu Microsoft .NET Core jest licencjonowany za pomocą [MICROSOFT .NET LIBRARY Umowa licencyjna EULA](https://aka.ms/dotnet-core-eula).</span><span class="sxs-lookup"><span data-stu-id="c5d38-182">The Microsoft distribution of .NET Core is licensed with the [MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="c5d38-183">Ta licencja obejmuje sekcji "Dane", aby włączyć telemetrię (pokazana poniżej).</span><span class="sxs-lookup"><span data-stu-id="c5d38-183">This license includes the "DATA" section to enable telemetry (shown below).</span></span>

<span data-ttu-id="c5d38-184">[Pakiety .NET NuGet](https://www.nuget.org/profiles/dotnetframework) użyć tego samego licencji, ale nie włączysz danych telemetrycznych (zobacz [zakres](#scope)).</span><span class="sxs-lookup"><span data-stu-id="c5d38-184">[.NET NuGet packages](https://www.nuget.org/profiles/dotnetframework) use the same license but don't enable telemetry (see [Scope](#scope)).</span></span>

> 2. <span data-ttu-id="c5d38-185">DATA.</span><span class="sxs-lookup"><span data-stu-id="c5d38-185">DATA.</span></span> <span data-ttu-id="c5d38-186">Oprogramowanie może zbierać informacje o Tobie i użytkowanie oprogramowania i wysyłać je do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c5d38-186">The software may collect information about you and your use of the software, and send that to Microsoft.</span></span> <span data-ttu-id="c5d38-187">Firma Microsoft może używać tych informacji w celu poprawy naszych produktów i usług.</span><span class="sxs-lookup"><span data-stu-id="c5d38-187">Microsoft may use this information to improve our products and services.</span></span> <span data-ttu-id="c5d38-188">Możesz dowiedzieć się więcej na temat zbierania danych i używać w dokumentacji pomocy i zasady zachowania poufności w <http://go.microsoft.com/fwlink/?LinkId=528096>.</span><span class="sxs-lookup"><span data-stu-id="c5d38-188">You can learn more about data collection and use in the help documentation and the privacy statement at <http://go.microsoft.com/fwlink/?LinkId=528096>.</span></span> <span data-ttu-id="c5d38-189">Korzystanie z oprogramowania oznacza Państwa zgodę na tych rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="c5d38-189">Your use of the software operates as your consent to these practices.</span></span>

## <a name="disclosure"></a><span data-ttu-id="c5d38-190">Ujawnienie</span><span class="sxs-lookup"><span data-stu-id="c5d38-190">Disclosure</span></span>

<span data-ttu-id="c5d38-191">.NET Core SDK zawiera następujący tekst, przy pierwszym uruchomieniu jednego z [poleceń interfejsu wiersza polecenia platformy .NET Core](index.md) (na przykład `dotnet restore`).</span><span class="sxs-lookup"><span data-stu-id="c5d38-191">The .NET Core SDK displays the following text when you first run one of the [.NET Core CLI commands](index.md) (for example, `dotnet restore`).</span></span> <span data-ttu-id="c5d38-192">Tekst może się nieco różnić w zależności od wersji zestawu SDK jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="c5d38-192">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="c5d38-193">To środowisko "najpierw uruchom" to, jak firma Microsoft przekaże Ci o zbieraniu danych.</span><span class="sxs-lookup"><span data-stu-id="c5d38-193">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c5d38-194">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5d38-194">See also</span></span>

- [<span data-ttu-id="c5d38-195">Czego się nauczyliśmy z platformy .NET Core SDK Telemetrii</span><span class="sxs-lookup"><span data-stu-id="c5d38-195">What we've learned from .NET Core SDK Telemetry</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/)
- [<span data-ttu-id="c5d38-196">Źródło odwołania danych telemetrycznych (repozytorium dotnet/cli)</span><span class="sxs-lookup"><span data-stu-id="c5d38-196">Telemetry reference source (dotnet/cli repo)</span></span>](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)
- [<span data-ttu-id="c5d38-197">Dane użycia zestawu SDK programu .NET core</span><span class="sxs-lookup"><span data-stu-id="c5d38-197">.NET Core SDK Usage Data</span></span>](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)
