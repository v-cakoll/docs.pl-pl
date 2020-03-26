---
title: Dane telemetryczne sdk .NET Core
description: Odnajduj funkcje telemetryczne .NET Core SDK, które zbierają informacje o użyciu do analizy, które dane są zbierane i jak je wyłączyć.
author: KathleenDollard
ms.date: 08/27/2019
ms.openlocfilehash: a79b791abc99331ff39f5e281ee0fdc62b258989
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507285"
---
# <a name="net-core-sdk-telemetry"></a><span data-ttu-id="82c4f-103">Dane telemetryczne sdk .NET Core</span><span class="sxs-lookup"><span data-stu-id="82c4f-103">.NET Core SDK telemetry</span></span>

<span data-ttu-id="82c4f-104">Zestaw [SDK rdzenia .NET](index.md) zawiera funkcję telemetryczną, która zbiera dane użycia i informacje o wyjątkach w przypadku awarii interfejsu wiersza polecenia .NET Core.</span><span class="sxs-lookup"><span data-stu-id="82c4f-104">The [.NET Core SDK](index.md) includes a telemetry feature that collects usage data and exception information when the .NET Core CLI crashes.</span></span> <span data-ttu-id="82c4f-105">Plik wiersza polecenia .NET Core jest dostarczany z zestawem .NET Core SDK i jest zestawem zleceń, które umożliwiają tworzenie, testowanie i publikowanie aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="82c4f-105">The .NET Core CLI comes with the .NET Core SDK and is the set of verbs that enable you to build, test, and publish your .NET Core apps.</span></span> <span data-ttu-id="82c4f-106">Ważne jest, aby zespół platformy .NET zrozumiał, jak narzędzia są używane, dzięki czemu można je ulepszyć.</span><span class="sxs-lookup"><span data-stu-id="82c4f-106">It's important that the .NET team understands how the tools are used so they can be improved.</span></span> <span data-ttu-id="82c4f-107">Informacje o błędach pomaga zespołowi rozwiązać problemy i naprawić błędy.</span><span class="sxs-lookup"><span data-stu-id="82c4f-107">Information on failures helps the team resolve problems and fix bugs.</span></span>

<span data-ttu-id="82c4f-108">Zebrane dane są anonimowe i publikowane łącznie na licencji [Creative Commons Attribution License.](https://creativecommons.org/licenses/by/4.0/)</span><span class="sxs-lookup"><span data-stu-id="82c4f-108">The collected data is anonymous and published in aggregate under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span>

## <a name="scope"></a><span data-ttu-id="82c4f-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="82c4f-109">Scope</span></span>

<span data-ttu-id="82c4f-110">`dotnet`ma dwie funkcje: uruchamianie aplikacji i wykonywanie poleceń INTERFEJSU WIERSZA polecenia.</span><span class="sxs-lookup"><span data-stu-id="82c4f-110">`dotnet` has two functions: to run apps, and to execute CLI commands.</span></span> <span data-ttu-id="82c4f-111">Telemetria nie jest `dotnet` *zbierana* podczas uruchamiania aplikacji w następującym formacie:</span><span class="sxs-lookup"><span data-stu-id="82c4f-111">Telemetry *isn't collected* when using `dotnet` to start an application in the following format:</span></span>

- `dotnet [path-to-app].dll`

<span data-ttu-id="82c4f-112">Dane telemetryczne *są zbierane* podczas korzystania z dowolnego [polecenia .NET Core CLI,](index.md)takich jak:</span><span class="sxs-lookup"><span data-stu-id="82c4f-112">Telemetry *is collected* when using any of the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet run`

## <a name="how-to-opt-out"></a><span data-ttu-id="82c4f-113">Jak zrezygnować</span><span class="sxs-lookup"><span data-stu-id="82c4f-113">How to opt out</span></span>

<span data-ttu-id="82c4f-114">Funkcja telemetrii .NET Core SDK jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="82c4f-114">The .NET Core SDK telemetry feature is enabled by default.</span></span> <span data-ttu-id="82c4f-115">Aby zrezygnować z funkcji telemetrii, `1` ustaw `true`zmienną środowiskową `DOTNET_CLI_TELEMETRY_OPTOUT` na lub .</span><span class="sxs-lookup"><span data-stu-id="82c4f-115">To opt out of the telemetry feature, set the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

<span data-ttu-id="82c4f-116">Pojedynczy wpis telemetryczny jest również wysyłany przez instalatora pakietu .NET Core SDK po pomyślnej instalacji.</span><span class="sxs-lookup"><span data-stu-id="82c4f-116">A single telemetry entry is also sent by the .NET Core SDK installer when a successful installation happens.</span></span> <span data-ttu-id="82c4f-117">Aby zrezygnować, przed `DOTNET_CLI_TELEMETRY_OPTOUT` zainstalowaniem zestawu .NET Core SDK należy ustawić zmienną środowiskową.</span><span class="sxs-lookup"><span data-stu-id="82c4f-117">To opt out, set the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable before you install the .NET Core SDK.</span></span>

## <a name="disclosure"></a><span data-ttu-id="82c4f-118">Ujawnienie</span><span class="sxs-lookup"><span data-stu-id="82c4f-118">Disclosure</span></span>

<span data-ttu-id="82c4f-119">Przy pierwszym uruchomieniu jednego z [poleceń .NET Core CLI](index.md) (na `dotnet build`przykład) w programie .NET Core SDK jest wyświetlany tekst podobny do następującego.</span><span class="sxs-lookup"><span data-stu-id="82c4f-119">The .NET Core SDK displays text similar to the following when you first run one of the [.NET Core CLI commands](index.md) (for example, `dotnet build`).</span></span> <span data-ttu-id="82c4f-120">Tekst może się nieznacznie różnić w zależności od wersji uruchomionego sdk.</span><span class="sxs-lookup"><span data-stu-id="82c4f-120">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="82c4f-121">To środowisko "pierwszego uruchomienia" to sposób, w jaki firma Microsoft powiadamia użytkownika o zbieraniu danych.</span><span class="sxs-lookup"><span data-stu-id="82c4f-121">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

```console
Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience. The data is anonymous. It is collected by Microsoft and shared with the community. You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

<span data-ttu-id="82c4f-122">Aby wyłączyć ten komunikat i wiadomość powitalną `DOTNET_NOLOGO` .NET `true`Core, ustaw zmienną środowiskową na .</span><span class="sxs-lookup"><span data-stu-id="82c4f-122">To disable this message and the .NET Core welcome message, set the `DOTNET_NOLOGO` environment variable to `true`.</span></span> <span data-ttu-id="82c4f-123">Należy zauważyć, że ta zmienna nie ma wpływu na rezygnację telemetryczną.</span><span class="sxs-lookup"><span data-stu-id="82c4f-123">Note that this variable has no effect on telemetry opt out.</span></span>

## <a name="data-points"></a><span data-ttu-id="82c4f-124">Punkty danych</span><span class="sxs-lookup"><span data-stu-id="82c4f-124">Data points</span></span>

<span data-ttu-id="82c4f-125">Funkcja telemetrii nie zbiera danych osobowych, takich jak nazwy użytkowników lub adresy e-mail.</span><span class="sxs-lookup"><span data-stu-id="82c4f-125">The telemetry feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="82c4f-126">Nie skanuje kodu i nie wyodrębnia danych na poziomie projektu, takich jak nazwa, repozytorium lub autor.</span><span class="sxs-lookup"><span data-stu-id="82c4f-126">It doesn't scan your code and doesn't extract project-level data, such as name, repository, or author.</span></span> <span data-ttu-id="82c4f-127">Dane są bezpiecznie wysyłane do serwerów firmy Microsoft przy użyciu technologii [Usługi Azure Monitor,](https://azure.microsoft.com/services/monitor/) przechowywane w ograniczonym dostępie i publikowane pod ścisłą kontrolą zabezpieczeń z bezpiecznych systemów [usługi Azure Storage.](https://azure.microsoft.com/services/storage/)</span><span class="sxs-lookup"><span data-stu-id="82c4f-127">The data is sent securely to Microsoft servers using [Azure Monitor](https://azure.microsoft.com/services/monitor/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="82c4f-128">Ochrona twojej prywatności jest dla nas ważna.</span><span class="sxs-lookup"><span data-stu-id="82c4f-128">Protecting your privacy is important to us.</span></span> <span data-ttu-id="82c4f-129">Jeśli podejrzewasz, że dane telemetryczne zbierają poufne dane lub dane są niezabezpieczone lub niewłaściwie obsługiwane, zgłębij problem w repozytorium [dotnet/cli](https://github.com/dotnet/cli/issues) lub wyślij wiadomość e-mail do [dotnet@microsoft.com](mailto:dotnet@microsoft.com) badania.</span><span class="sxs-lookup"><span data-stu-id="82c4f-129">If you suspect the telemetry is collecting sensitive data or the data is being insecurely or inappropriately handled, file an issue in the [dotnet/cli](https://github.com/dotnet/cli/issues) repository or send an email to [dotnet@microsoft.com](mailto:dotnet@microsoft.com) for investigation.</span></span>

<span data-ttu-id="82c4f-130">Funkcja telemetrii zbiera następujące dane:</span><span class="sxs-lookup"><span data-stu-id="82c4f-130">The telemetry feature collects the following data:</span></span>

| <span data-ttu-id="82c4f-131">Wersje SDK</span><span class="sxs-lookup"><span data-stu-id="82c4f-131">SDK versions</span></span> | <span data-ttu-id="82c4f-132">Dane</span><span class="sxs-lookup"><span data-stu-id="82c4f-132">Data</span></span> |
|--------------|------|
| <span data-ttu-id="82c4f-133">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="82c4f-133">All</span></span>          | <span data-ttu-id="82c4f-134">Sygnatura czasowa wywołania.</span><span class="sxs-lookup"><span data-stu-id="82c4f-134">Timestamp of invocation.</span></span> |
| <span data-ttu-id="82c4f-135">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="82c4f-135">All</span></span>          | <span data-ttu-id="82c4f-136">Polecenie wywoływane (na przykład "build"), haszowane począwszy od 2.1.</span><span class="sxs-lookup"><span data-stu-id="82c4f-136">Command invoked (for example, "build"), hashed starting in 2.1.</span></span> |
| <span data-ttu-id="82c4f-137">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="82c4f-137">All</span></span>          | <span data-ttu-id="82c4f-138">Trzy oktetowe adresy IP używane do określenia lokalizacji geograficznej.</span><span class="sxs-lookup"><span data-stu-id="82c4f-138">Three octet IP address used to determine the geographical location.</span></span> |
| <span data-ttu-id="82c4f-139">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="82c4f-139">All</span></span>          | <span data-ttu-id="82c4f-140">System operacyjny i wersja.</span><span class="sxs-lookup"><span data-stu-id="82c4f-140">Operating system and version.</span></span> |
| <span data-ttu-id="82c4f-141">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="82c4f-141">All</span></span>          | <span data-ttu-id="82c4f-142">Identyfikator środowiska uruchomieniowego (RID) jest uruchomiony na SDK.</span><span class="sxs-lookup"><span data-stu-id="82c4f-142">Runtime ID (RID) the SDK is running on.</span></span> |
| <span data-ttu-id="82c4f-143">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="82c4f-143">All</span></span>          | <span data-ttu-id="82c4f-144">.NET Core SDK w wersji.</span><span class="sxs-lookup"><span data-stu-id="82c4f-144">.NET Core SDK version.</span></span> |
| <span data-ttu-id="82c4f-145">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="82c4f-145">All</span></span>          | <span data-ttu-id="82c4f-146">Profil telemetrii: wartość opcjonalna używana tylko z jawną zgodą użytkownika i używana wewnętrznie w firmie Microsoft.</span><span class="sxs-lookup"><span data-stu-id="82c4f-146">Telemetry profile: an optional value only used with explicit user opt-in and used internally at Microsoft.</span></span> |
| <span data-ttu-id="82c4f-147">>=2,0</span><span class="sxs-lookup"><span data-stu-id="82c4f-147">>=2.0</span></span>        | <span data-ttu-id="82c4f-148">Argumenty i opcje polecenia: zbiera się kilka argumentów i opcji (nie dowolne ciągi).</span><span class="sxs-lookup"><span data-stu-id="82c4f-148">Command arguments and options: several arguments and options are collected (not arbitrary strings).</span></span> <span data-ttu-id="82c4f-149">Zobacz [zebrane opcje](#collected-options).</span><span class="sxs-lookup"><span data-stu-id="82c4f-149">See [collected options](#collected-options).</span></span> <span data-ttu-id="82c4f-150">Hashed po 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="82c4f-150">Hashed after 2.1.300.</span></span> |
| <span data-ttu-id="82c4f-151">>=2,0</span><span class="sxs-lookup"><span data-stu-id="82c4f-151">>=2.0</span></span>         | <span data-ttu-id="82c4f-152">Czy SDK jest uruchomiony w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="82c4f-152">Whether the SDK is running in a container.</span></span> |
| <span data-ttu-id="82c4f-153">>=2,0</span><span class="sxs-lookup"><span data-stu-id="82c4f-153">>=2.0</span></span>         | <span data-ttu-id="82c4f-154">Struktury docelowe (od `TargetFramework` zdarzenia), mieszane począwszy od 2.1.</span><span class="sxs-lookup"><span data-stu-id="82c4f-154">Target frameworks (from the `TargetFramework` event), hashed starting in 2.1.</span></span> |
| <span data-ttu-id="82c4f-155">>=2,0</span><span class="sxs-lookup"><span data-stu-id="82c4f-155">>=2.0</span></span>         | <span data-ttu-id="82c4f-156">Hashed Media Access Control (MAC) adres: kryptograficznie (SHA256) anonimowy i unikatowy identyfikator komputera.</span><span class="sxs-lookup"><span data-stu-id="82c4f-156">Hashed Media Access Control (MAC) address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> |
| <span data-ttu-id="82c4f-157">>=2,0</span><span class="sxs-lookup"><span data-stu-id="82c4f-157">>=2.0</span></span>         | <span data-ttu-id="82c4f-158">Haszem bieżący katalog roboczy.</span><span class="sxs-lookup"><span data-stu-id="82c4f-158">Hashed current working directory.</span></span> |
| <span data-ttu-id="82c4f-159">>=2,0</span><span class="sxs-lookup"><span data-stu-id="82c4f-159">>=2.0</span></span>         | <span data-ttu-id="82c4f-160">Zainstaluj raport sukcesu z haszem instalatora exe nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="82c4f-160">Install success report, with hashed installer exe filename.</span></span> |
| <span data-ttu-id="82c4f-161">>=2,1,300</span><span class="sxs-lookup"><span data-stu-id="82c4f-161">>=2.1.300</span></span>     | <span data-ttu-id="82c4f-162">Wersja jądra.</span><span class="sxs-lookup"><span data-stu-id="82c4f-162">Kernel version.</span></span> |
| <span data-ttu-id="82c4f-163">>=2,1,300</span><span class="sxs-lookup"><span data-stu-id="82c4f-163">>=2.1.300</span></span>     | <span data-ttu-id="82c4f-164">Libc release/version.</span><span class="sxs-lookup"><span data-stu-id="82c4f-164">Libc release/version.</span></span> |
| <span data-ttu-id="82c4f-165">>=3,0,100</span><span class="sxs-lookup"><span data-stu-id="82c4f-165">>=3.0.100</span></span>     | <span data-ttu-id="82c4f-166">Czy dane wyjściowe zostały przekierowane (true czy false).</span><span class="sxs-lookup"><span data-stu-id="82c4f-166">Whether the output was redirected (true or false).</span></span> |
| <span data-ttu-id="82c4f-167">>=3,0,100</span><span class="sxs-lookup"><span data-stu-id="82c4f-167">>=3.0.100</span></span>     | <span data-ttu-id="82c4f-168">W awarii interfejsu WIERSZA/SDK typu wyjątku i jego śledzenia stosu (tylko kod INTERFEJSU WIERSZA/SDKU jest zawarty w śledzenia stosu wysłane).</span><span class="sxs-lookup"><span data-stu-id="82c4f-168">On a CLI/SDK crash, the exception type and its stack trace (only CLI/SDK code is included in the stack trace sent).</span></span> <span data-ttu-id="82c4f-169">Aby uzyskać więcej informacji, zobacz [.NET Core CLI/SDK crash dane telemetryczne wyjątku zebrane](#net-core-clisdk-crash-exception-telemetry-collected).</span><span class="sxs-lookup"><span data-stu-id="82c4f-169">For more information, see [.NET Core CLI/SDK crash exception telemetry collected](#net-core-clisdk-crash-exception-telemetry-collected).</span></span> |

### <a name="collected-options"></a><span data-ttu-id="82c4f-170">Zebrane opcje</span><span class="sxs-lookup"><span data-stu-id="82c4f-170">Collected options</span></span>

<span data-ttu-id="82c4f-171">Niektóre polecenia wysyłają dodatkowe dane.</span><span class="sxs-lookup"><span data-stu-id="82c4f-171">Certain commands send additional data.</span></span> <span data-ttu-id="82c4f-172">Podzbiór poleceń wysyła pierwszy argument:</span><span class="sxs-lookup"><span data-stu-id="82c4f-172">A subset of commands sends the first argument:</span></span>

| <span data-ttu-id="82c4f-173">Polecenie</span><span class="sxs-lookup"><span data-stu-id="82c4f-173">Command</span></span>               | <span data-ttu-id="82c4f-174">Wysłane dane pierwszego argumentu</span><span class="sxs-lookup"><span data-stu-id="82c4f-174">First argument data sent</span></span>                |
|-----------------------|-----------------------------------------|
| `dotnet help <arg>`   | <span data-ttu-id="82c4f-175">Pomoc polecenia jest poszukiwany.</span><span class="sxs-lookup"><span data-stu-id="82c4f-175">The command help is being queried for.</span></span>  |
| `dotnet new <arg>`    | <span data-ttu-id="82c4f-176">Nazwa szablonu (skrót).</span><span class="sxs-lookup"><span data-stu-id="82c4f-176">The template name (hashed).</span></span>             |
| `dotnet add <arg>`    | <span data-ttu-id="82c4f-177">Słowo `package` lub `reference`.</span><span class="sxs-lookup"><span data-stu-id="82c4f-177">The word `package` or `reference`.</span></span>      |
| `dotnet remove <arg>` | <span data-ttu-id="82c4f-178">Słowo `package` lub `reference`.</span><span class="sxs-lookup"><span data-stu-id="82c4f-178">The word `package` or `reference`.</span></span>      |
| `dotnet list <arg>`   | <span data-ttu-id="82c4f-179">Słowo `package` lub `reference`.</span><span class="sxs-lookup"><span data-stu-id="82c4f-179">The word `package` or `reference`.</span></span>      |
| `dotnet sln <arg>`    | <span data-ttu-id="82c4f-180">Słowo `add`, `list`, `remove`lub .</span><span class="sxs-lookup"><span data-stu-id="82c4f-180">The word `add`, `list`, or `remove`.</span></span>    |
| `dotnet nuget <arg>`  | <span data-ttu-id="82c4f-181">Słowo `delete`, `locals`, `push`lub .</span><span class="sxs-lookup"><span data-stu-id="82c4f-181">The word `delete`, `locals`, or `push`.</span></span> |

<span data-ttu-id="82c4f-182">Podzbiór poleceń wysyła wybrane opcje, jeśli są używane, wraz z ich wartościami:</span><span class="sxs-lookup"><span data-stu-id="82c4f-182">A subset of commands sends selected options if they're used, along with their values:</span></span>

| <span data-ttu-id="82c4f-183">Opcja</span><span class="sxs-lookup"><span data-stu-id="82c4f-183">Option</span></span>                  | <span data-ttu-id="82c4f-184">Polecenia</span><span class="sxs-lookup"><span data-stu-id="82c4f-184">Commands</span></span>                                                                                       |
|-------------------------|------------------------------------------------------------------------------------------------|
| `--verbosity`           | <span data-ttu-id="82c4f-185">Wszystkie polecenia</span><span class="sxs-lookup"><span data-stu-id="82c4f-185">All commands</span></span>                                                                                   |
| `--language`            | `dotnet new`                                                                                   |
| `--configuration`       | <span data-ttu-id="82c4f-186">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="82c4f-186">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`</span></span>                  |
| `--framework`           | <span data-ttu-id="82c4f-187">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest`</span><span class="sxs-lookup"><span data-stu-id="82c4f-187">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest`</span></span> |
| `--runtime`             | <span data-ttu-id="82c4f-188">`dotnet build`,  `dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="82c4f-188">`dotnet build`,  `dotnet publish`</span></span>                                                              |
| `--platform`            | `dotnet vstest`                                                                                |
| `--logger`              | `dotnet vstest`                                                                                |
| `--sdk-package-version` | `dotnet migrate`                                                                               |

<span data-ttu-id="82c4f-189">Z `--verbosity` wyjątkiem `--sdk-package-version`i , wszystkie inne wartości są mieszane począwszy od .NET Core 2.1.100 SDK.</span><span class="sxs-lookup"><span data-stu-id="82c4f-189">Except for `--verbosity` and `--sdk-package-version`, all the other values are hashed starting with .NET Core 2.1.100 SDK.</span></span>

## <a name="net-core-clisdk-crash-exception-telemetry-collected"></a><span data-ttu-id="82c4f-190">Dane telemetryczne wyjątku awarii .NET Core CLI/SDK zebrane</span><span class="sxs-lookup"><span data-stu-id="82c4f-190">.NET Core CLI/SDK crash exception telemetry collected</span></span>

<span data-ttu-id="82c4f-191">Jeśli plik CLI/SDK .NET Core ulegnie awarii, zbiera nazwę wyjątku i śledzenia stosu kodu interfejsu wiersza polecenia/sdku.</span><span class="sxs-lookup"><span data-stu-id="82c4f-191">If the .NET Core CLI/SDK crashes, it collects the name of the exception and stack trace of the CLI/SDK code.</span></span> <span data-ttu-id="82c4f-192">Te informacje są zbierane w celu oceny problemów i poprawy jakości .NET Core SDK i CLI.</span><span class="sxs-lookup"><span data-stu-id="82c4f-192">This information is collected to assess problems and improve the quality of the .NET Core SDK and CLI.</span></span> <span data-ttu-id="82c4f-193">Ten artykuł zawiera informacje o gromadzonych przez nas danych.</span><span class="sxs-lookup"><span data-stu-id="82c4f-193">This article provides information about the data we collect.</span></span> <span data-ttu-id="82c4f-194">Zawiera również wskazówki dotyczące sposobu, w jaki użytkownicy budujący własną wersję sdk .NET Core mogą uniknąć niezamierzonego ujawnienia informacji osobistych lub poufnych.</span><span class="sxs-lookup"><span data-stu-id="82c4f-194">It also provides tips on how users building their own version of the .NET Core SDK can avoid inadvertent disclosure of personal or sensitive information.</span></span>

### <a name="types-of-collected-data"></a><span data-ttu-id="82c4f-195">Rodzaje gromadzonych danych</span><span class="sxs-lookup"><span data-stu-id="82c4f-195">Types of collected data</span></span>

<span data-ttu-id="82c4f-196">.NET Core CLI zbiera informacje tylko dla wyjątków interfejsu WIERSZA/SDK, a nie wyjątków w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="82c4f-196">.NET Core CLI collects information for CLI/SDK exceptions only, not exceptions in your application.</span></span> <span data-ttu-id="82c4f-197">Zebrane dane zawiera nazwę wyjątku i śledzenia stosu.</span><span class="sxs-lookup"><span data-stu-id="82c4f-197">The collected data contains the name of the exception and the stack trace.</span></span> <span data-ttu-id="82c4f-198">Ten ślad stosu jest z kodu CLI/SDK.</span><span class="sxs-lookup"><span data-stu-id="82c4f-198">This stack trace is of CLI/SDK code.</span></span>

<span data-ttu-id="82c4f-199">Poniższy przykład przedstawia rodzaj danych, które są zbierane:</span><span class="sxs-lookup"><span data-stu-id="82c4f-199">The following example shows the kind of data that is collected:</span></span>

```console
System.IO.IOException
at System.ConsolePal.WindowsConsoleStream.Write(Byte[] buffer, Int32 offset, Int32 count)
at System.IO.StreamWriter.Flush(Boolean flushStream, Boolean flushEncoder)
at System.IO.StreamWriter.Write(Char[] buffer)
at System.IO.TextWriter.WriteLine()
at System.IO.TextWriter.SyncTextWriter.WriteLine()
at Microsoft.DotNet.Cli.Utils.Reporter.WriteLine()
at Microsoft.DotNet.Tools.Run.RunCommand.EnsureProjectIsBuilt()
at Microsoft.DotNet.Tools.Run.RunCommand.Execute()
at Microsoft.DotNet.Tools.Run.RunCommand.Run(String[] args)
at Microsoft.DotNet.Cli.Program.ProcessArgs(String[] args, ITelemetry telemetryClient)
at Microsoft.DotNet.Cli.Program.Main(String[] args)
```

### <a name="avoid-inadvertent-disclosure-of-information"></a><span data-ttu-id="82c4f-200">Unikanie nieumyślnego ujawniania informacji</span><span class="sxs-lookup"><span data-stu-id="82c4f-200">Avoid inadvertent disclosure of information</span></span>

<span data-ttu-id="82c4f-201">Współautorzy programu .NET Core i inni, którzy uruchomili wersję sdk .NET Core, którą sami stworzyli, powinni rozważyć ścieżkę do ich kodu źródłowego SDK.</span><span class="sxs-lookup"><span data-stu-id="82c4f-201">.NET Core contributors and anyone else running a version of the .NET Core SDK that they built themselves should consider the path to their SDK source code.</span></span> <span data-ttu-id="82c4f-202">Jeśli wystąpi awaria podczas korzystania z .NET Core SDK, który jest kompilacją debugowania niestandardowego lub skonfigurowany z niestandardowymi plikami symboli kompilacji, ścieżka pliku źródłowego SDK z komputera kompilacji jest zbierana jako część śledzenia stosu i nie jest mieszana.</span><span class="sxs-lookup"><span data-stu-id="82c4f-202">If a crash occurs while using a .NET Core SDK that is a custom debug build or configured with custom build symbol files, the SDK source file path from the build machine is collected as part of the stack trace and isn't hashed.</span></span>

<span data-ttu-id="82c4f-203">Z tego powodu niestandardowe kompilacje sdk .NET Core nie powinny znajdować się w katalogach, których nazwy ścieżek ujawniają informacje osobiste lub poufne.</span><span class="sxs-lookup"><span data-stu-id="82c4f-203">Because of this, custom builds of the .NET Core SDK shouldn't be located in directories whose path names expose personal or sensitive information.</span></span>

## <a name="see-also"></a><span data-ttu-id="82c4f-204">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="82c4f-204">See also</span></span>

- [<span data-ttu-id="82c4f-205">.NET Core CLI Telemetry - Dane q2 2019</span><span class="sxs-lookup"><span data-stu-id="82c4f-205">.NET Core CLI Telemetry - 2019 Q2 Data</span></span>](https://dotnet.microsoft.com/platform/telemetry/dotnet-core-cli-2019q2)
- [<span data-ttu-id="82c4f-206">Źródło referencyjne telemetrii (repozytorium dotnet/cli)</span><span class="sxs-lookup"><span data-stu-id="82c4f-206">Telemetry reference source (dotnet/cli repository)</span></span>](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)
