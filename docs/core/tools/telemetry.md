---
title: "Dane telemetryczne narzędzi interfejsu wiersza polecenia programu .NET core"
description: "Odkryj funkcje telemetrii .NET Core narzędzia, które zbierają informacje o użyciu do analizy, które dane są zbierane i jak go wyłączyć."
keywords: Dane telemetryczne .NET i .NET core
author: richlander
ms.author: mairaw
ms.date: 08/04/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 480df976-7568-4df4-9d26-9911357b5a31
ms.workload: dotnetcore
ms.openlocfilehash: 66ad63f0b2a2f62f34f0784b236d242f1d92066a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="net-core-cli-tools-telemetry"></a><span data-ttu-id="5fd98-104">Dane telemetryczne narzędzi interfejsu wiersza polecenia programu .NET core</span><span class="sxs-lookup"><span data-stu-id="5fd98-104">.NET Core CLI Tools telemetry</span></span>

<span data-ttu-id="5fd98-105">[.NET Core SDK](index.md) obejmuje [funkcji telemetrii](https://github.com/dotnet/cli/pull/2145) która zbiera informacje o użyciu.</span><span class="sxs-lookup"><span data-stu-id="5fd98-105">The [.NET Core SDK](index.md) includes a [telemetry feature](https://github.com/dotnet/cli/pull/2145) that collects usage information.</span></span> <span data-ttu-id="5fd98-106">Koniecznie zespołu .NET rozumie, używania narzędzi, aby firma Microsoft może je poprawić.</span><span class="sxs-lookup"><span data-stu-id="5fd98-106">It's important that the .NET Team understands how the tools are used so that we can improve them.</span></span> <span data-ttu-id="5fd98-107">Aby uzyskać więcej informacji, zobacz [co zostały dowiedzieliśmy się z .NET Core SDK Telemetrii](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).</span><span class="sxs-lookup"><span data-stu-id="5fd98-107">For more information, see [What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).</span></span>

<span data-ttu-id="5fd98-108">Zebrane dane są anonimowe i opublikowane w zagregowanej formie do użycia przez firmę Microsoft i społecznością w obszarze [Creative Commons autorstwa licencji](https://creativecommons.org/licenses/by/4.0/).</span><span class="sxs-lookup"><span data-stu-id="5fd98-108">The collected data is anonymous and published in an aggregated form for use by both Microsoft and the community under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span> 

## <a name="scope"></a><span data-ttu-id="5fd98-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="5fd98-109">Scope</span></span>

<span data-ttu-id="5fd98-110">`dotnet` Polecenia jest używane do uruchomienia aplikacjach i interfejsu wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5fd98-110">The `dotnet` command is used to launch both apps and the .NET Core CLI.</span></span> <span data-ttu-id="5fd98-111">`dotnet` Samo polecenie nie zbierać dane telemetryczne.</span><span class="sxs-lookup"><span data-stu-id="5fd98-111">The `dotnet` command itself doesn't collect telemetry.</span></span> <span data-ttu-id="5fd98-112">Uruchom polecenia interfejsu wiersza polecenia platformy .NET Core przez `dotnet` polecenia zbieranie danych telemetrycznych.</span><span class="sxs-lookup"><span data-stu-id="5fd98-112">The .NET Core CLI commands run by the `dotnet` command collect the telemetry.</span></span>

<span data-ttu-id="5fd98-113">Dane telemetryczne *nie włączono* przy użyciu `dotnet` poleceń, za pomocą polecenia, nie dołączonych:</span><span class="sxs-lookup"><span data-stu-id="5fd98-113">Telemetry *isn't enabled* when using the `dotnet` command itself, with no command attached:</span></span>

- `dotnet`
- `dotnet [path-to-app]`

<span data-ttu-id="5fd98-114">Dane telemetryczne *włączono* przy użyciu [polecenia interfejsu wiersza polecenia platformy .NET Core](index.md), takich jak:</span><span class="sxs-lookup"><span data-stu-id="5fd98-114">Telemetry *is enabled* when using the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`


## <a name="behavior"></a><span data-ttu-id="5fd98-115">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="5fd98-115">Behavior</span></span>

<span data-ttu-id="5fd98-116">Funkcja telemetrii .NET Core interfejsu wiersza polecenia narzędzia jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="5fd98-116">The .NET Core CLI Tools telemetry feature is enabled by default.</span></span> <span data-ttu-id="5fd98-117">Wypisz funkcji telemetrii przez ustawienie `DOTNET_CLI_TELEMETRY_OPTOUT` zmienną środowiskową `1` lub `true`.</span><span class="sxs-lookup"><span data-stu-id="5fd98-117">Opt-out of the telemetry feature by setting the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

## <a name="data-points"></a><span data-ttu-id="5fd98-118">Punkty danych</span><span class="sxs-lookup"><span data-stu-id="5fd98-118">Data points</span></span>

<span data-ttu-id="5fd98-119">Funkcja zbiera następujące dane:</span><span class="sxs-lookup"><span data-stu-id="5fd98-119">The feature collects the following data:</span></span>

- <span data-ttu-id="5fd98-120">Sygnatura czasowa wywołania &#8224;</span><span class="sxs-lookup"><span data-stu-id="5fd98-120">Timestamp of invocation&#8224;</span></span>
- <span data-ttu-id="5fd98-121">Polecenie wywoływane (na przykład "kompilacji") &#8224;</span><span class="sxs-lookup"><span data-stu-id="5fd98-121">Command invoked (for example, "build")&#8224;</span></span>
- <span data-ttu-id="5fd98-122">Oktet trzy adres IP używany do określenia lokalizacji geograficznej &#8224;</span><span class="sxs-lookup"><span data-stu-id="5fd98-122">Three octet IP address used to determine geographical location&#8224;</span></span>
- <span data-ttu-id="5fd98-123">`ExitCode`polecenie</span><span class="sxs-lookup"><span data-stu-id="5fd98-123">`ExitCode` of the command</span></span>
- <span data-ttu-id="5fd98-124">Test runner (do projekty testowe)</span><span class="sxs-lookup"><span data-stu-id="5fd98-124">Test runner (for test projects)</span></span>
- <span data-ttu-id="5fd98-125">&#8224; systemu operacyjnego i wersji</span><span class="sxs-lookup"><span data-stu-id="5fd98-125">Operating system and version&#8224;</span></span>
- <span data-ttu-id="5fd98-126">Określa, czy znajdują się w węźle środowisk uruchomieniowych identyfikatorów środowiska wykonawczego</span><span class="sxs-lookup"><span data-stu-id="5fd98-126">Whether runtime IDs are present in the runtimes node</span></span>
- <span data-ttu-id="5fd98-127">Wersja zestawu SDK programu .NET core &#8224;</span><span class="sxs-lookup"><span data-stu-id="5fd98-127">.NET Core SDK version&#8224;</span></span>

<span data-ttu-id="5fd98-128">&#8224; Ta metryka jest opublikowana.</span><span class="sxs-lookup"><span data-stu-id="5fd98-128">&#8224;This metric is published.</span></span>

<span data-ttu-id="5fd98-129">Począwszy od programu .NET Core SDK 2.0, nowe punkty danych są zbierane:</span><span class="sxs-lookup"><span data-stu-id="5fd98-129">Starting with .NET Core SDK 2.0, new data points are collected:</span></span>

- <span data-ttu-id="5fd98-130">`dotnet`polecenie Opcje i argumenty: tylko znane opcje i argumenty są zbierane (nie dowolne ciągi).</span><span class="sxs-lookup"><span data-stu-id="5fd98-130">`dotnet` command arguments and options: only known arguments and options are collected (not arbitrary strings).</span></span>
- <span data-ttu-id="5fd98-131">Określa, czy zestaw SDK jest uruchomiona w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="5fd98-131">Whether the SDK is running in a container.</span></span>
- <span data-ttu-id="5fd98-132">Docelowych platform.</span><span class="sxs-lookup"><span data-stu-id="5fd98-132">Target frameworks.</span></span>
- <span data-ttu-id="5fd98-133">Wartość skrótu adresów MAC: kryptograficznie (SHA256) anonimowych, jak i unikatowy identyfikator dla maszyny.</span><span class="sxs-lookup"><span data-stu-id="5fd98-133">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> <span data-ttu-id="5fd98-134">Ta metryka nie został opublikowany.</span><span class="sxs-lookup"><span data-stu-id="5fd98-134">This metric is not published.</span></span>
- <span data-ttu-id="5fd98-135">Skrótu bieżącego katalogu roboczego.</span><span class="sxs-lookup"><span data-stu-id="5fd98-135">Hashed current working directory.</span></span>

<span data-ttu-id="5fd98-136">Funkcja nie zbieraj danych osobowych, takich jak nazwy użytkowników lub adresy e-mail.</span><span class="sxs-lookup"><span data-stu-id="5fd98-136">The feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="5fd98-137">Nie skanuje kodu, a nie wyodrębnić poufnych danych na poziomie projektu, takie jak nazwa, repozytorium lub autora.</span><span class="sxs-lookup"><span data-stu-id="5fd98-137">It doesn't scan your code and doesn't extract sensitive project-level data, such as name, repo, or author.</span></span> <span data-ttu-id="5fd98-138">Danych są bezpiecznie wysyłane do serwerów firmy Microsoft przy użyciu [usługi Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technologii, przechowywany w ograniczonym dostępem i publikowane w obszarze opcji ograniczeniami zabezpieczeń z bezpiecznego [usługi Azure Storage](https://azure.microsoft.com/services/storage/) systemów.</span><span class="sxs-lookup"><span data-stu-id="5fd98-138">The data is sent securely to Microsoft servers using [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="5fd98-139">Chcemy się dowiedzieć się, jak są używane narzędzia i jeśli działają poprawnie, nie co tworzysz przy użyciu narzędzi.</span><span class="sxs-lookup"><span data-stu-id="5fd98-139">We want to know how the tools are used and if they're working well, not what you're building with the tools.</span></span> <span data-ttu-id="5fd98-140">Jeśli podejrzewasz, że dane telemetryczne jest zbieranie danych poufnych lub że jesteśmy nimi lub niewłaściwie obsługi danych, [plików problemu w repozytorium dotnet/cli problemów](https://github.com/dotnet/cli/issues) aby umożliwić zbadanie problemu.</span><span class="sxs-lookup"><span data-stu-id="5fd98-140">If you suspect that the telemetry is collecting sensitive data or that we're insecurely or inappropriately handling data, [file an issue in the dotnet/cli repo issues](https://github.com/dotnet/cli/issues) for investigation.</span></span>

## <a name="published-data"></a><span data-ttu-id="5fd98-141">Opublikowane dane</span><span class="sxs-lookup"><span data-stu-id="5fd98-141">Published data</span></span>

<span data-ttu-id="5fd98-142">Dane publikowane jest dostępna co kwartał i znajduje się w [dane użycia zestawu SDK programu .NET Core](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span><span class="sxs-lookup"><span data-stu-id="5fd98-142">Published data is available quarterly and are listed at [.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span></span> <span data-ttu-id="5fd98-143">Kolumn w pliku danych są:</span><span class="sxs-lookup"><span data-stu-id="5fd98-143">The columns of a data file are:</span></span>
- <span data-ttu-id="5fd98-144">Znacznik czasu</span><span class="sxs-lookup"><span data-stu-id="5fd98-144">Timestamp</span></span>
- <span data-ttu-id="5fd98-145">Wystąpienia &#8224;</span><span class="sxs-lookup"><span data-stu-id="5fd98-145">Occurrences&#8224;</span></span>
- <span data-ttu-id="5fd98-146">Polecenie</span><span class="sxs-lookup"><span data-stu-id="5fd98-146">Command</span></span>
- <span data-ttu-id="5fd98-147">Lokalizacja geograficzna &#8225;</span><span class="sxs-lookup"><span data-stu-id="5fd98-147">Geography&#8225;</span></span>
- <span data-ttu-id="5fd98-148">Rodzina systemów operacyjnych</span><span class="sxs-lookup"><span data-stu-id="5fd98-148">OSFamily</span></span>
- <span data-ttu-id="5fd98-149">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="5fd98-149">RuntimeID</span></span>
- <span data-ttu-id="5fd98-150">OSVersion</span><span class="sxs-lookup"><span data-stu-id="5fd98-150">OSVersion</span></span>
- <span data-ttu-id="5fd98-151">Wersjazestawusdk</span><span class="sxs-lookup"><span data-stu-id="5fd98-151">SDKVersion</span></span>

<span data-ttu-id="5fd98-152">&#8224; *Wystąpień* kolumny Wyświetla łączna liczba Użyj tego polecenia dla tego wiersza metryki danego dnia.</span><span class="sxs-lookup"><span data-stu-id="5fd98-152">&#8224;The *Occurrences* column displays the aggregate count of that command's use for that row's metrics that day.</span></span> 

<span data-ttu-id="5fd98-153">&#8225; Zazwyczaj *geograficzne* kolumnie jest wyświetlana nazwa kraju.</span><span class="sxs-lookup"><span data-stu-id="5fd98-153">&#8225;Typically, the *Geography* column displays the name of a country.</span></span> <span data-ttu-id="5fd98-154">W niektórych przypadkach kontynencie z Antarktyka pojawia się w tej kolumnie, albo z powodu pracowników naukowo-badawczych przy użyciu platformy .NET Core Antarktyka lub nieprawidłowej lokalizacji dane.</span><span class="sxs-lookup"><span data-stu-id="5fd98-154">In some cases, the continent of Antarctica appears in this column, either due to researchers using .NET Core in Antarctica or incorrect location data.</span></span>

### <a name="example"></a><span data-ttu-id="5fd98-155">Przykład</span><span class="sxs-lookup"><span data-stu-id="5fd98-155">Example</span></span>

| <span data-ttu-id="5fd98-156">Znacznik czasu</span><span class="sxs-lookup"><span data-stu-id="5fd98-156">Timestamp</span></span>      | <span data-ttu-id="5fd98-157">Wystąpienia</span><span class="sxs-lookup"><span data-stu-id="5fd98-157">Occurrences</span></span> | <span data-ttu-id="5fd98-158">Polecenie</span><span class="sxs-lookup"><span data-stu-id="5fd98-158">Command</span></span> | <span data-ttu-id="5fd98-159">Lokalizacja geograficzna</span><span class="sxs-lookup"><span data-stu-id="5fd98-159">Geography</span></span> | <span data-ttu-id="5fd98-160">Rodzina systemów operacyjnych</span><span class="sxs-lookup"><span data-stu-id="5fd98-160">OSFamily</span></span> | <span data-ttu-id="5fd98-161">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="5fd98-161">RuntimeID</span></span>     | <span data-ttu-id="5fd98-162">OSVersion</span><span class="sxs-lookup"><span data-stu-id="5fd98-162">OSVersion</span></span> | <span data-ttu-id="5fd98-163">Wersjazestawusdk</span><span class="sxs-lookup"><span data-stu-id="5fd98-163">SDKVersion</span></span> |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| <span data-ttu-id="5fd98-164">4/16/2017 0:00</span><span class="sxs-lookup"><span data-stu-id="5fd98-164">4/16/2017 0:00</span></span> | <span data-ttu-id="5fd98-165">8</span><span class="sxs-lookup"><span data-stu-id="5fd98-165">8</span></span>           | <span data-ttu-id="5fd98-166">Uruchom</span><span class="sxs-lookup"><span data-stu-id="5fd98-166">run</span></span>     | <span data-ttu-id="5fd98-167">Ugandy</span><span class="sxs-lookup"><span data-stu-id="5fd98-167">Uganda</span></span>    | <span data-ttu-id="5fd98-168">Darwin</span><span class="sxs-lookup"><span data-stu-id="5fd98-168">Darwin</span></span>   | <span data-ttu-id="5fd98-169">OSX.10.12 x64</span><span class="sxs-lookup"><span data-stu-id="5fd98-169">osx.10.12-x64</span></span> | <span data-ttu-id="5fd98-170">10.12</span><span class="sxs-lookup"><span data-stu-id="5fd98-170">10.12</span></span>     | <span data-ttu-id="5fd98-171">1.0.1</span><span class="sxs-lookup"><span data-stu-id="5fd98-171">1.0.1</span></span>      |

### <a name="datasets"></a><span data-ttu-id="5fd98-172">Zestawy danych</span><span class="sxs-lookup"><span data-stu-id="5fd98-172">Datasets</span></span>

[<span data-ttu-id="5fd98-173">2016 - K3</span><span class="sxs-lookup"><span data-stu-id="5fd98-173">2016 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)  
[<span data-ttu-id="5fd98-174">2016 - KWARTAŁ 4</span><span class="sxs-lookup"><span data-stu-id="5fd98-174">2016 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)  
[<span data-ttu-id="5fd98-175">2017 - 1.</span><span class="sxs-lookup"><span data-stu-id="5fd98-175">2017 - Q1</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)  
[<span data-ttu-id="5fd98-176">2017 - K2</span><span class="sxs-lookup"><span data-stu-id="5fd98-176">2017 - Q2</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)

<span data-ttu-id="5fd98-177">Dodatkowe zestawy danych są publikowane, przy użyciu standardowego formatu adresu URL.</span><span class="sxs-lookup"><span data-stu-id="5fd98-177">Additional datasets are posted using a standard URL format.</span></span> <span data-ttu-id="5fd98-178">Zastąp `<YEAR>` roku i Zastąp `<QUARTER>` z kwartału roku (Użyj `1`, `2`, `3`, lub `4`).</span><span class="sxs-lookup"><span data-stu-id="5fd98-178">Replace `<YEAR>` with the year and replace `<QUARTER>` with the quarter of the year (use `1`, `2`, `3`, or `4`).</span></span> <span data-ttu-id="5fd98-179">Pliki znajdują się w wartości tabulatorami (*TSV*) format.</span><span class="sxs-lookup"><span data-stu-id="5fd98-179">The files are in tab-separated values (*TSV*) format.</span></span> 

```
https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv
```

## <a name="license"></a><span data-ttu-id="5fd98-180">Licencji</span><span class="sxs-lookup"><span data-stu-id="5fd98-180">License</span></span>

<span data-ttu-id="5fd98-181">Rozkład Microsoft .NET Core jest licencjonowana z [MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula).</span><span class="sxs-lookup"><span data-stu-id="5fd98-181">The Microsoft distribution of .NET Core is licensed with the [MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="5fd98-182">Ta licencja zawiera sekcja "Dane" Aby włączyć telemetrii (pokazana poniżej).</span><span class="sxs-lookup"><span data-stu-id="5fd98-182">This license includes the "DATA" section to enable telemetry (shown below).</span></span>

<span data-ttu-id="5fd98-183">[Pakietów NuGet programu .NET](https://www.nuget.org/profiles/dotnetframework) użyć tego samego licencji, ale nie włączysz telemetrii (zobacz [zakres](#scope)).</span><span class="sxs-lookup"><span data-stu-id="5fd98-183">[.NET NuGet packages](https://www.nuget.org/profiles/dotnetframework) use the same license but don't enable telemetry (see [Scope](#scope)).</span></span>

> 2. <span data-ttu-id="5fd98-184">DANE.</span><span class="sxs-lookup"><span data-stu-id="5fd98-184">DATA.</span></span> <span data-ttu-id="5fd98-185">Oprogramowanie może zbierać informacje o Tobie i korzystanie z oprogramowania i wysyłać do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5fd98-185">The software may collect information about you and your use of the software, and send that to Microsoft.</span></span> <span data-ttu-id="5fd98-186">Firma Microsoft może używać tych informacji do poprawy naszych produktów i usług.</span><span class="sxs-lookup"><span data-stu-id="5fd98-186">Microsoft may use this information to improve our products and services.</span></span> <span data-ttu-id="5fd98-187">Można dowiedzieć się więcej o zbieraniu danych i używać w dokumentacji pomocy i poufności informacji w http://go.microsoft.com/fwlink/?LinkId=528096.</span><span class="sxs-lookup"><span data-stu-id="5fd98-187">You can learn more about data collection and use in the help documentation and the privacy statement at http://go.microsoft.com/fwlink/?LinkId=528096.</span></span> <span data-ttu-id="5fd98-188">Korzystanie z oprogramowania działa jako Twojej zgody na nich.</span><span class="sxs-lookup"><span data-stu-id="5fd98-188">Your use of the software operates as your consent to these practices.</span></span>

## <a name="disclosure"></a><span data-ttu-id="5fd98-189">Ujawnienie</span><span class="sxs-lookup"><span data-stu-id="5fd98-189">Disclosure</span></span>

<span data-ttu-id="5fd98-190">Narzędzia .NET Core interfejsu wiersza polecenia, wyświetl następujący tekst przy pierwszym uruchomieniu polecenia (na przykład `dotnet restore`).</span><span class="sxs-lookup"><span data-stu-id="5fd98-190">The .NET Core CLI Tools display the following text when you first run one of the commands (for example, `dotnet restore`).</span></span> <span data-ttu-id="5fd98-191">Tekst może się nieco różnić w zależności od wersji zestawu SDK jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="5fd98-191">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="5fd98-192">To środowisko "najpierw uruchom" jest jak Microsoft powiadomi użytkownika o zbierania danych.</span><span class="sxs-lookup"><span data-stu-id="5fd98-192">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

```console
Welcome to .NET Core!
---------------------
Learn more about .NET Core @ https://aka.ms/dotnet-docs. Use dotnet --help to see available commands or go to https://aka.ms/dotnet-cli-docs.
 
Telemetry
--------------
The .NET Core tools collect usage data in order to improve your experience. The data is anonymous and does not include command-line arguments. The data is collected by Microsoft and shared with the community.
You can opt out of telemetry by setting a DOTNET_CLI_TELEMETRY_OPTOUT environment variable to 1 using your favorite shell.
You can read more about .NET Core tools telemetry @ https://aka.ms/dotnet-cli-telemetry.
```

## <a name="see-also"></a><span data-ttu-id="5fd98-193">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5fd98-193">See also</span></span>

[<span data-ttu-id="5fd98-194">Co zostało dowiedzieliśmy się z .NET Core SDK Telemetrii</span><span class="sxs-lookup"><span data-stu-id="5fd98-194">What we've learned from .NET Core SDK Telemetry</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/)  
<span data-ttu-id="5fd98-195">[Dane telemetryczne źródła odniesienia (repozytorium dotnet/cli; release/2.0.0 gałęzi)](https://github.com/dotnet/cli/blob/release/2.0.0/src/dotnet/Telemetry.cs) </span><span class="sxs-lookup"><span data-stu-id="5fd98-195">[Telemetry reference source (dotnet/cli repo; release/2.0.0 branch)](https://github.com/dotnet/cli/blob/release/2.0.0/src/dotnet/Telemetry.cs) </span></span>  
[<span data-ttu-id="5fd98-196">Dane użycia zestawu SDK programu .NET core</span><span class="sxs-lookup"><span data-stu-id="5fd98-196">.NET Core SDK Usage Data</span></span>](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)
