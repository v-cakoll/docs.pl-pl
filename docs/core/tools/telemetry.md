---
title: Dane telemetryczne zestawu SDK programu .NET core
description: Odkryj funkcje telemetrii .NET Core SDK, które zbierają informacje o użyciu do analizy, które dane są zbierane i jak go wyłączyć.
author: richlander
ms.author: mairaw
ms.date: 06/20/2018
ms.openlocfilehash: f60a1eaa7b869676dfbb67529e7878ca9b9ca34a
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314880"
---
# <a name="net-core-sdk-telemetry"></a><span data-ttu-id="1f9f8-103">Dane telemetryczne zestawu SDK programu .NET core</span><span class="sxs-lookup"><span data-stu-id="1f9f8-103">.NET Core SDK telemetry</span></span>

<span data-ttu-id="1f9f8-104">[.NET Core SDK](index.md) obejmuje [funkcji telemetrii](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry) która zbiera informacje o użyciu.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-104">The [.NET Core SDK](index.md) includes a [telemetry feature](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry) that collects usage information.</span></span> <span data-ttu-id="1f9f8-105">Jest ważne, czy .NET Team rozumie używania narzędzi, można poprawić.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-105">It's important that the .NET Team understands how the tools are used so they can be improved.</span></span> <span data-ttu-id="1f9f8-106">Aby uzyskać więcej informacji, zobacz [co zostały dowiedzieliśmy się z .NET Core SDK Telemetrii](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).</span><span class="sxs-lookup"><span data-stu-id="1f9f8-106">For more information, see [What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).</span></span>

<span data-ttu-id="1f9f8-107">Zebrane dane są anonimowe i opublikowane w zagregowanej formie do użycia przez firmę Microsoft i społecznością w obszarze [Creative Commons autorstwa licencji](https://creativecommons.org/licenses/by/4.0/).</span><span class="sxs-lookup"><span data-stu-id="1f9f8-107">The collected data is anonymous and published in an aggregated form for use by both Microsoft and the community under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span>

## <a name="scope"></a><span data-ttu-id="1f9f8-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="1f9f8-108">Scope</span></span>

<span data-ttu-id="1f9f8-109">`dotnet` Polecenia jest używane do uruchomienia aplikacjach i interfejsu wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-109">The `dotnet` command is used to launch both apps and the .NET Core CLI.</span></span> <span data-ttu-id="1f9f8-110">`dotnet` Samo polecenie nie zbierać dane telemetryczne.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-110">The `dotnet` command itself doesn't collect telemetry.</span></span> <span data-ttu-id="1f9f8-111">Uruchom polecenia interfejsu wiersza polecenia platformy .NET Core przez `dotnet` polecenia zbieranie danych telemetrycznych.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-111">The .NET Core CLI commands run by the `dotnet` command collect the telemetry.</span></span>

<span data-ttu-id="1f9f8-112">Dane telemetryczne *nie włączono* przy użyciu `dotnet` poleceń, za pomocą polecenia, nie dołączonych:</span><span class="sxs-lookup"><span data-stu-id="1f9f8-112">Telemetry *isn't enabled* when using the `dotnet` command itself, with no command attached:</span></span>

- `dotnet`
- `dotnet [path-to-app]`

<span data-ttu-id="1f9f8-113">Dane telemetryczne *włączono* przy użyciu [polecenia interfejsu wiersza polecenia platformy .NET Core](index.md), takich jak:</span><span class="sxs-lookup"><span data-stu-id="1f9f8-113">Telemetry *is enabled* when using the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`

## <a name="how-to-opt-out"></a><span data-ttu-id="1f9f8-114">Jak wykluczyć</span><span class="sxs-lookup"><span data-stu-id="1f9f8-114">How to opt out</span></span>

<span data-ttu-id="1f9f8-115">Funkcja telemetrii .NET Core SDK jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-115">The .NET Core SDK telemetry feature is enabled by default.</span></span> <span data-ttu-id="1f9f8-116">Opcja rezygnacji z funkcją telemetrii przez ustawienie `DOTNET_CLI_TELEMETRY_OPTOUT` zmienną środowiskową `1` lub `true`.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-116">Opt out of the telemetry feature by setting the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

## <a name="data-points"></a><span data-ttu-id="1f9f8-117">Punkty danych</span><span class="sxs-lookup"><span data-stu-id="1f9f8-117">Data points</span></span>

<span data-ttu-id="1f9f8-118">Funkcja zbiera następujące dane:</span><span class="sxs-lookup"><span data-stu-id="1f9f8-118">The feature collects the following data:</span></span>

- <span data-ttu-id="1f9f8-119">Sygnatura czasowa wywołania&#8224;</span><span class="sxs-lookup"><span data-stu-id="1f9f8-119">Timestamp of invocation&#8224;</span></span>
- <span data-ttu-id="1f9f8-120">Polecenie wywoływane (na przykład "kompilacji")&#8224;</span><span class="sxs-lookup"><span data-stu-id="1f9f8-120">Command invoked (for example, "build")&#8224;</span></span>
- <span data-ttu-id="1f9f8-121">Adres IP trzy octet umożliwia określenie lokalizacji geograficznych&#8224;</span><span class="sxs-lookup"><span data-stu-id="1f9f8-121">Three octet IP address used to determine geographical location&#8224;</span></span>
- <span data-ttu-id="1f9f8-122">`ExitCode` polecenie</span><span class="sxs-lookup"><span data-stu-id="1f9f8-122">`ExitCode` of the command</span></span>
- <span data-ttu-id="1f9f8-123">Test runner (do projekty testowe)</span><span class="sxs-lookup"><span data-stu-id="1f9f8-123">Test runner (for test projects)</span></span>
- <span data-ttu-id="1f9f8-124">Wersja systemu operacyjnego i&#8224;</span><span class="sxs-lookup"><span data-stu-id="1f9f8-124">Operating system and version&#8224;</span></span>
- <span data-ttu-id="1f9f8-125">Określa, czy znajdują się w węźle środowisk uruchomieniowych identyfikatorów środowiska wykonawczego</span><span class="sxs-lookup"><span data-stu-id="1f9f8-125">Whether runtime IDs are present in the runtimes node</span></span>
- <span data-ttu-id="1f9f8-126">Wersja zestawu SDK programu .NET core&#8224;</span><span class="sxs-lookup"><span data-stu-id="1f9f8-126">.NET Core SDK version&#8224;</span></span>

<span data-ttu-id="1f9f8-127">&#8224;Ta metryka jest opublikowana.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-127">&#8224;This metric is published.</span></span>

<span data-ttu-id="1f9f8-128">Począwszy od programu .NET Core SDK 2.0, nowe punkty danych są zbierane:</span><span class="sxs-lookup"><span data-stu-id="1f9f8-128">Starting with .NET Core SDK 2.0, new data points are collected:</span></span>

- <span data-ttu-id="1f9f8-129">`dotnet` polecenie Opcje i argumenty: tylko znane opcje i argumenty są zbierane (nie dowolne ciągi).</span><span class="sxs-lookup"><span data-stu-id="1f9f8-129">`dotnet` command arguments and options: only known arguments and options are collected (not arbitrary strings).</span></span>
- <span data-ttu-id="1f9f8-130">Określa, czy zestaw SDK jest uruchomiona w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-130">Whether the SDK is running in a container.</span></span>
- <span data-ttu-id="1f9f8-131">Docelowych platform.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-131">Target frameworks.</span></span>
- <span data-ttu-id="1f9f8-132">Wartość skrótu adresów MAC: kryptograficznie (SHA256) anonimowych, jak i unikatowy identyfikator dla maszyny.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-132">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> <span data-ttu-id="1f9f8-133">Ten pomiar nie jest opublikowana.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-133">This metric isn't published.</span></span>
- <span data-ttu-id="1f9f8-134">Skrótu bieżącego katalogu roboczego.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-134">Hashed current working directory.</span></span>

<span data-ttu-id="1f9f8-135">Funkcja nie zbieraj danych osobowych, takich jak nazwy użytkowników lub adresy e-mail.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-135">The feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="1f9f8-136">Nie skanuje kodu, a nie wyodrębnić poufnych danych na poziomie projektu, takie jak nazwa, repozytorium lub autora.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-136">It doesn't scan your code and doesn't extract sensitive project-level data, such as name, repo, or author.</span></span> <span data-ttu-id="1f9f8-137">Danych są bezpiecznie wysyłane do serwerów firmy Microsoft przy użyciu [usługi Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technologii, przechowywany w ograniczonym dostępem i publikowane w obszarze opcji ograniczeniami zabezpieczeń z bezpiecznego [usługi Azure Storage](https://azure.microsoft.com/services/storage/) systemów.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-137">The data is sent securely to Microsoft servers using [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="1f9f8-138">Zespół .NET chce dowiedzieć się, jak są używane narzędzia i jeśli działają poprawnie, nie co tworzysz przy użyciu narzędzi.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-138">The .NET team wants to know how the tools are used and if they're working well, not what you're building with the tools.</span></span> <span data-ttu-id="1f9f8-139">Jeśli podejrzewasz zbiera dane telemetryczne danych poufnych lub że dane są nimi lub niewłaściwie obsługi plików problemu w [dotnet/cli](https://github.com/dotnet/cli/issues) repozytorium, aby umożliwić zbadanie problemu.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-139">If you suspect that the telemetry is collecting sensitive data or that the data is being insecurely or inappropriately handled, file an issue in the [dotnet/cli](https://github.com/dotnet/cli/issues) repository for investigation.</span></span>

## <a name="published-data"></a><span data-ttu-id="1f9f8-140">Opublikowane dane</span><span class="sxs-lookup"><span data-stu-id="1f9f8-140">Published data</span></span>

<span data-ttu-id="1f9f8-141">Dane publikowane jest dostępna co kwartał i znajduje się w [dane użycia zestawu SDK programu .NET Core](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span><span class="sxs-lookup"><span data-stu-id="1f9f8-141">Published data is available quarterly and are listed at [.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span></span> <span data-ttu-id="1f9f8-142">Kolumn w pliku danych są:</span><span class="sxs-lookup"><span data-stu-id="1f9f8-142">The columns of a data file are:</span></span>

- <span data-ttu-id="1f9f8-143">Znacznik czasu</span><span class="sxs-lookup"><span data-stu-id="1f9f8-143">Timestamp</span></span>
- <span data-ttu-id="1f9f8-144">Occurrences&#8224;</span><span class="sxs-lookup"><span data-stu-id="1f9f8-144">Occurrences&#8224;</span></span>
- <span data-ttu-id="1f9f8-145">Polecenie</span><span class="sxs-lookup"><span data-stu-id="1f9f8-145">Command</span></span>
- <span data-ttu-id="1f9f8-146">Geography&#8225;</span><span class="sxs-lookup"><span data-stu-id="1f9f8-146">Geography&#8225;</span></span>
- <span data-ttu-id="1f9f8-147">Rodzina systemów operacyjnych</span><span class="sxs-lookup"><span data-stu-id="1f9f8-147">OSFamily</span></span>
- <span data-ttu-id="1f9f8-148">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="1f9f8-148">RuntimeID</span></span>
- <span data-ttu-id="1f9f8-149">OSVersion</span><span class="sxs-lookup"><span data-stu-id="1f9f8-149">OSVersion</span></span>
- <span data-ttu-id="1f9f8-150">Wersjazestawusdk</span><span class="sxs-lookup"><span data-stu-id="1f9f8-150">SDKVersion</span></span>

<span data-ttu-id="1f9f8-151">&#8224;*Wystąpień* kolumny Wyświetla łączna liczba Użyj tego polecenia dla tego wiersza metryki danego dnia.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-151">&#8224;The *Occurrences* column displays the aggregate count of that command's use for that row's metrics that day.</span></span>

<span data-ttu-id="1f9f8-152">&#8225;Zazwyczaj *geograficzne* kolumnie jest wyświetlana nazwa kraju.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-152">&#8225;Typically, the *Geography* column displays the name of a country.</span></span> <span data-ttu-id="1f9f8-153">W niektórych przypadkach kontynencie z Antarktyka pojawia się w tej kolumnie, albo z powodu pracowników naukowo-badawczych przy użyciu platformy .NET Core Antarktyka lub nieprawidłowej lokalizacji dane.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-153">In some cases, the continent of Antarctica appears in this column, either due to researchers using .NET Core in Antarctica or incorrect location data.</span></span>

### <a name="example"></a><span data-ttu-id="1f9f8-154">Przykład</span><span class="sxs-lookup"><span data-stu-id="1f9f8-154">Example</span></span>

| <span data-ttu-id="1f9f8-155">Znacznik czasu</span><span class="sxs-lookup"><span data-stu-id="1f9f8-155">Timestamp</span></span>      | <span data-ttu-id="1f9f8-156">Wystąpienia</span><span class="sxs-lookup"><span data-stu-id="1f9f8-156">Occurrences</span></span> | <span data-ttu-id="1f9f8-157">Polecenie</span><span class="sxs-lookup"><span data-stu-id="1f9f8-157">Command</span></span> | <span data-ttu-id="1f9f8-158">Lokalizacja geograficzna</span><span class="sxs-lookup"><span data-stu-id="1f9f8-158">Geography</span></span> | <span data-ttu-id="1f9f8-159">Rodzina systemów operacyjnych</span><span class="sxs-lookup"><span data-stu-id="1f9f8-159">OSFamily</span></span> | <span data-ttu-id="1f9f8-160">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="1f9f8-160">RuntimeID</span></span>     | <span data-ttu-id="1f9f8-161">OSVersion</span><span class="sxs-lookup"><span data-stu-id="1f9f8-161">OSVersion</span></span> | <span data-ttu-id="1f9f8-162">Wersjazestawusdk</span><span class="sxs-lookup"><span data-stu-id="1f9f8-162">SDKVersion</span></span> |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| <span data-ttu-id="1f9f8-163">4/16/2017 0:00</span><span class="sxs-lookup"><span data-stu-id="1f9f8-163">4/16/2017 0:00</span></span> | <span data-ttu-id="1f9f8-164">8</span><span class="sxs-lookup"><span data-stu-id="1f9f8-164">8</span></span>           | <span data-ttu-id="1f9f8-165">Uruchom</span><span class="sxs-lookup"><span data-stu-id="1f9f8-165">run</span></span>     | <span data-ttu-id="1f9f8-166">Ugandy</span><span class="sxs-lookup"><span data-stu-id="1f9f8-166">Uganda</span></span>    | <span data-ttu-id="1f9f8-167">Darwin</span><span class="sxs-lookup"><span data-stu-id="1f9f8-167">Darwin</span></span>   | <span data-ttu-id="1f9f8-168">osx.10.12-x64</span><span class="sxs-lookup"><span data-stu-id="1f9f8-168">osx.10.12-x64</span></span> | <span data-ttu-id="1f9f8-169">10.12</span><span class="sxs-lookup"><span data-stu-id="1f9f8-169">10.12</span></span>     | <span data-ttu-id="1f9f8-170">1.0.1</span><span class="sxs-lookup"><span data-stu-id="1f9f8-170">1.0.1</span></span>      |

### <a name="datasets"></a><span data-ttu-id="1f9f8-171">Zestawy danych</span><span class="sxs-lookup"><span data-stu-id="1f9f8-171">Datasets</span></span>

[<span data-ttu-id="1f9f8-172">2016 - K3</span><span class="sxs-lookup"><span data-stu-id="1f9f8-172">2016 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)  
[<span data-ttu-id="1f9f8-173">2016 - KWARTAŁ 4</span><span class="sxs-lookup"><span data-stu-id="1f9f8-173">2016 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)  
[<span data-ttu-id="1f9f8-174">2017 - 1.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-174">2017 - Q1</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)  
[<span data-ttu-id="1f9f8-175">2017 - K2</span><span class="sxs-lookup"><span data-stu-id="1f9f8-175">2017 - Q2</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)  
[<span data-ttu-id="1f9f8-176">2017 - K3</span><span class="sxs-lookup"><span data-stu-id="1f9f8-176">2017 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q3.tsv)  
[<span data-ttu-id="1f9f8-177">2017 - KWARTAŁ 4</span><span class="sxs-lookup"><span data-stu-id="1f9f8-177">2017 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q4.tsv)  

<span data-ttu-id="1f9f8-178">Dodatkowe zestawy danych są publikowane, przy użyciu standardowego formatu adresu URL.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-178">Additional datasets are posted using a standard URL format.</span></span> <span data-ttu-id="1f9f8-179">Zastąp `<YEAR>` roku i Zastąp `<QUARTER>` z kwartału roku (Użyj `1`, `2`, `3`, lub `4`).</span><span class="sxs-lookup"><span data-stu-id="1f9f8-179">Replace `<YEAR>` with the year and replace `<QUARTER>` with the quarter of the year (use `1`, `2`, `3`, or `4`).</span></span> <span data-ttu-id="1f9f8-180">Pliki znajdują się w wartości tabulatorami (*TSV*) format.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-180">The files are in tab-separated values (*TSV*) format.</span></span>

`https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv`

## <a name="license"></a><span data-ttu-id="1f9f8-181">Licencji</span><span class="sxs-lookup"><span data-stu-id="1f9f8-181">License</span></span>

<span data-ttu-id="1f9f8-182">Rozkład Microsoft .NET Core jest licencjonowana z [MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula).</span><span class="sxs-lookup"><span data-stu-id="1f9f8-182">The Microsoft distribution of .NET Core is licensed with the [MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="1f9f8-183">Ta licencja zawiera sekcja "Dane" Aby włączyć telemetrii (pokazana poniżej).</span><span class="sxs-lookup"><span data-stu-id="1f9f8-183">This license includes the "DATA" section to enable telemetry (shown below).</span></span>

<span data-ttu-id="1f9f8-184">[Pakietów NuGet programu .NET](https://www.nuget.org/profiles/dotnetframework) użyć tego samego licencji, ale nie włączysz telemetrii (zobacz [zakres](#scope)).</span><span class="sxs-lookup"><span data-stu-id="1f9f8-184">[.NET NuGet packages](https://www.nuget.org/profiles/dotnetframework) use the same license but don't enable telemetry (see [Scope](#scope)).</span></span>

> 2. <span data-ttu-id="1f9f8-185">DATA.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-185">DATA.</span></span> <span data-ttu-id="1f9f8-186">Oprogramowanie może zbierać informacje o Tobie i korzystanie z oprogramowania i wysyłać do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-186">The software may collect information about you and your use of the software, and send that to Microsoft.</span></span> <span data-ttu-id="1f9f8-187">Firma Microsoft może używać tych informacji do poprawy naszych produktów i usług.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-187">Microsoft may use this information to improve our products and services.</span></span> <span data-ttu-id="1f9f8-188">Możesz dowiedzieć się więcej o zbieraniu danych i użyć w dokumentacji pomocy i poufności informacji w http://go.microsoft.com/fwlink/?LinkId=528096.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-188">You can learn more about data collection and use in the help documentation and the privacy statement at http://go.microsoft.com/fwlink/?LinkId=528096.</span></span> <span data-ttu-id="1f9f8-189">Korzystanie z oprogramowania działa jako Twojej zgody na nich.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-189">Your use of the software operates as your consent to these practices.</span></span>

## <a name="disclosure"></a><span data-ttu-id="1f9f8-190">Ujawnienie</span><span class="sxs-lookup"><span data-stu-id="1f9f8-190">Disclosure</span></span>

<span data-ttu-id="1f9f8-191">.NET Core SDK zawiera następujący tekst przy pierwszym uruchomieniu jednego z [polecenia interfejsu wiersza polecenia platformy .NET Core](index.md) (na przykład `dotnet restore`).</span><span class="sxs-lookup"><span data-stu-id="1f9f8-191">The .NET Core SDK displays the following text when you first run one of the [.NET Core CLI commands](index.md) (for example, `dotnet restore`).</span></span> <span data-ttu-id="1f9f8-192">Tekst może się nieco różnić w zależności od wersji zestawu SDK jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-192">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="1f9f8-193">To środowisko "najpierw uruchom" jest jak Microsoft powiadomi użytkownika o zbierania danych.</span><span class="sxs-lookup"><span data-stu-id="1f9f8-193">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1f9f8-194">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f9f8-194">See also</span></span>

[<span data-ttu-id="1f9f8-195">Co zostało dowiedzieliśmy się z .NET Core SDK Telemetrii</span><span class="sxs-lookup"><span data-stu-id="1f9f8-195">What we've learned from .NET Core SDK Telemetry</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/)  
[<span data-ttu-id="1f9f8-196">Dane telemetryczne źródła odniesienia (repozytorium dotnet/cli)</span><span class="sxs-lookup"><span data-stu-id="1f9f8-196">Telemetry reference source (dotnet/cli repo)</span></span>](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)  
[<span data-ttu-id="1f9f8-197">Dane użycia zestawu SDK programu .NET core</span><span class="sxs-lookup"><span data-stu-id="1f9f8-197">.NET Core SDK Usage Data</span></span>](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)  
