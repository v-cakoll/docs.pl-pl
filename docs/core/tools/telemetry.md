---
title: Dane telemetryczne zestaw .NET Core SDK
description: Odkryj zestaw .NET Core SDK funkcje telemetrii, które zbierają informacje o użyciu analizy, zbierane dane i jak je wyłączyć.
author: KathleenDollard
ms.date: 08/27/2019
ms.openlocfilehash: 0917dae23588ccd1809252aaf484c397e84561c7
ms.sourcegitcommit: 67cf756b033c6173a1bbd1cbd5aef1fccac99e34
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2020
ms.locfileid: "86226572"
---
# <a name="net-core-sdk-telemetry"></a><span data-ttu-id="ea0fc-103">Dane telemetryczne zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="ea0fc-103">.NET Core SDK telemetry</span></span>

<span data-ttu-id="ea0fc-104">[Zestaw .NET Core SDK](index.md) zawiera funkcję telemetrii, która zbiera dane dotyczące użycia i informacje o wyjątkach, gdy interfejs wiersza polecenia platformy .NET Core awarie.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-104">The [.NET Core SDK](index.md) includes a telemetry feature that collects usage data and exception information when the .NET Core CLI crashes.</span></span> <span data-ttu-id="ea0fc-105">Interfejs wiersza polecenia platformy .NET Core zawiera zestaw .NET Core SDK i jest zestawem zleceń, które umożliwiają kompilowanie, testowanie i publikowanie aplikacji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-105">The .NET Core CLI comes with the .NET Core SDK and is the set of verbs that enable you to build, test, and publish your .NET Core apps.</span></span> <span data-ttu-id="ea0fc-106">Ważne jest, aby zespół .NET wiedział, w jaki sposób narzędzia są używane, aby można je było ulepszyć.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-106">It's important that the .NET team understands how the tools are used so they can be improved.</span></span> <span data-ttu-id="ea0fc-107">Informacje o błędach ułatwiają zespołowi Rozwiązywanie problemów i rozwiązywanie usterek.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-107">Information on failures helps the team resolve problems and fix bugs.</span></span>

<span data-ttu-id="ea0fc-108">Zebrane dane są anonimowe i publikowane jako zagregowane w ramach [licencji Creative Commons Attribution](https://creativecommons.org/licenses/by/4.0/).</span><span class="sxs-lookup"><span data-stu-id="ea0fc-108">The collected data is anonymous and published in aggregate under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span>

## <a name="scope"></a><span data-ttu-id="ea0fc-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="ea0fc-109">Scope</span></span>

<span data-ttu-id="ea0fc-110">`dotnet`Program ma dwie funkcje: do uruchamiania aplikacji i wykonywania poleceń interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-110">`dotnet` has two functions: to run apps, and to execute CLI commands.</span></span> <span data-ttu-id="ea0fc-111">Dane telemetryczne *nie są zbierane* podczas korzystania `dotnet` z programu w celu uruchomienia aplikacji w następującym formacie:</span><span class="sxs-lookup"><span data-stu-id="ea0fc-111">Telemetry *isn't collected* when using `dotnet` to start an application in the following format:</span></span>

- `dotnet [path-to-app].dll`

<span data-ttu-id="ea0fc-112">Dane telemetryczne *są zbierane* przy użyciu dowolnego [polecenia interfejs wiersza polecenia platformy .NET Core](index.md), takich jak:</span><span class="sxs-lookup"><span data-stu-id="ea0fc-112">Telemetry *is collected* when using any of the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet run`

## <a name="how-to-opt-out"></a><span data-ttu-id="ea0fc-113">Jak zrezygnować</span><span class="sxs-lookup"><span data-stu-id="ea0fc-113">How to opt out</span></span>

<span data-ttu-id="ea0fc-114">Funkcja telemetrii zestaw .NET Core SDK jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-114">The .NET Core SDK telemetry feature is enabled by default.</span></span> <span data-ttu-id="ea0fc-115">Aby zrezygnować z funkcji telemetrii, należy ustawić `DOTNET_CLI_TELEMETRY_OPTOUT` zmienną środowiskową na `1` lub `true` .</span><span class="sxs-lookup"><span data-stu-id="ea0fc-115">To opt out of the telemetry feature, set the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

<span data-ttu-id="ea0fc-116">W przypadku pomyślnej instalacji wysyłany jest również pojedynczy wpis telemetrii przez Instalatora zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-116">A single telemetry entry is also sent by the .NET Core SDK installer when a successful installation happens.</span></span> <span data-ttu-id="ea0fc-117">Aby zrezygnować z programu, należy ustawić `DOTNET_CLI_TELEMETRY_OPTOUT` zmienną środowiskową przed zainstalowaniem zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-117">To opt out, set the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable before you install the .NET Core SDK.</span></span>

## <a name="disclosure"></a><span data-ttu-id="ea0fc-118">Mogąc</span><span class="sxs-lookup"><span data-stu-id="ea0fc-118">Disclosure</span></span>

<span data-ttu-id="ea0fc-119">Zestaw .NET Core SDK wyświetla tekst podobny do poniższego po pierwszym uruchomieniu jednego z [poleceń interfejs wiersza polecenia platformy .NET Core](index.md) (na przykład `dotnet build` ).</span><span class="sxs-lookup"><span data-stu-id="ea0fc-119">The .NET Core SDK displays text similar to the following when you first run one of the [.NET Core CLI commands](index.md) (for example, `dotnet build`).</span></span> <span data-ttu-id="ea0fc-120">Tekst może się nieco różnić w zależności od używanej wersji zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-120">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="ea0fc-121">To "pierwsze uruchomienie" polega na tym, jak firma Microsoft powiadamia użytkownika o zbieraniu danych.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-121">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

```console
Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience. The data is anonymous. It is collected by Microsoft and shared with the community. You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

<span data-ttu-id="ea0fc-122">Aby wyłączyć ten komunikat i komunikat powitalny platformy .NET Core, ustaw dla `DOTNET_NOLOGO` zmiennej środowiskowej wartość `true` .</span><span class="sxs-lookup"><span data-stu-id="ea0fc-122">To disable this message and the .NET Core welcome message, set the `DOTNET_NOLOGO` environment variable to `true`.</span></span> <span data-ttu-id="ea0fc-123">Należy zauważyć, że ta zmienna nie ma wpływu na rezygnację z telemetrii.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-123">Note that this variable has no effect on telemetry opt out.</span></span>

## <a name="data-points"></a><span data-ttu-id="ea0fc-124">Punkty danych</span><span class="sxs-lookup"><span data-stu-id="ea0fc-124">Data points</span></span>

<span data-ttu-id="ea0fc-125">Funkcja telemetrii nie zbiera danych osobowych, takich jak nazwy użytkowników lub adresy e-mail.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-125">The telemetry feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="ea0fc-126">Nie skanuje kodu i nie wyodrębnia danych na poziomie projektu, takich jak Name, Repository lub Author.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-126">It doesn't scan your code and doesn't extract project-level data, such as name, repository, or author.</span></span> <span data-ttu-id="ea0fc-127">Dane są bezpiecznie przesyłane do serwerów firmy Microsoft przy użyciu technologii [Azure monitor](https://azure.microsoft.com/services/monitor/) , w ramach ograniczonego dostępu, i publikowane w ramach ścisłych kontroli zabezpieczeń z bezpiecznych systemów [usługi Azure Storage](https://azure.microsoft.com/services/storage/) .</span><span class="sxs-lookup"><span data-stu-id="ea0fc-127">The data is sent securely to Microsoft servers using [Azure Monitor](https://azure.microsoft.com/services/monitor/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="ea0fc-128">Ochrona prywatności jest dla nas ważna.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-128">Protecting your privacy is important to us.</span></span> <span data-ttu-id="ea0fc-129">Jeśli podejrzewasz, że Telemetria zbiera dane poufne lub dane są w sposób niezabezpieczony lub niewłaściwie obsłużone, należy rozwiązać problem w repozytorium [dotnet/SDK](https://github.com/dotnet/sdk/issues) lub wysłać wiadomość e-mail do [dotnet@microsoft.com](mailto:dotnet@microsoft.com) badania.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-129">If you suspect the telemetry is collecting sensitive data or the data is being insecurely or inappropriately handled, file an issue in the [dotnet/sdk](https://github.com/dotnet/sdk/issues) repository or send an email to [dotnet@microsoft.com](mailto:dotnet@microsoft.com) for investigation.</span></span>

<span data-ttu-id="ea0fc-130">Funkcja telemetrii zbiera następujące dane:</span><span class="sxs-lookup"><span data-stu-id="ea0fc-130">The telemetry feature collects the following data:</span></span>

| <span data-ttu-id="ea0fc-131">Wersje zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="ea0fc-131">SDK versions</span></span> | <span data-ttu-id="ea0fc-132">Dane</span><span class="sxs-lookup"><span data-stu-id="ea0fc-132">Data</span></span> |
|--------------|------|
| <span data-ttu-id="ea0fc-133">Wszystko</span><span class="sxs-lookup"><span data-stu-id="ea0fc-133">All</span></span>          | <span data-ttu-id="ea0fc-134">Sygnatura czasowa wywołania.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-134">Timestamp of invocation.</span></span> |
| <span data-ttu-id="ea0fc-135">Wszystko</span><span class="sxs-lookup"><span data-stu-id="ea0fc-135">All</span></span>          | <span data-ttu-id="ea0fc-136">Wywołano polecenie (na przykład "Kompilacja"), wartość skrótu rozpoczynająca się w 2,1.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-136">Command invoked (for example, "build"), hashed starting in 2.1.</span></span> |
| <span data-ttu-id="ea0fc-137">Wszystko</span><span class="sxs-lookup"><span data-stu-id="ea0fc-137">All</span></span>          | <span data-ttu-id="ea0fc-138">Trzy adresy IP używane do określenia lokalizacji geograficznej.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-138">Three octet IP address used to determine the geographical location.</span></span> |
| <span data-ttu-id="ea0fc-139">Wszystko</span><span class="sxs-lookup"><span data-stu-id="ea0fc-139">All</span></span>          | <span data-ttu-id="ea0fc-140">System operacyjny i wersja.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-140">Operating system and version.</span></span> |
| <span data-ttu-id="ea0fc-141">Wszystko</span><span class="sxs-lookup"><span data-stu-id="ea0fc-141">All</span></span>          | <span data-ttu-id="ea0fc-142">Identyfikator środowiska uruchomieniowego (RID), na którym jest uruchomiony zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-142">Runtime ID (RID) the SDK is running on.</span></span> |
| <span data-ttu-id="ea0fc-143">Wszystko</span><span class="sxs-lookup"><span data-stu-id="ea0fc-143">All</span></span>          | <span data-ttu-id="ea0fc-144">Wersja zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-144">.NET Core SDK version.</span></span> |
| <span data-ttu-id="ea0fc-145">Wszystko</span><span class="sxs-lookup"><span data-stu-id="ea0fc-145">All</span></span>          | <span data-ttu-id="ea0fc-146">Profil telemetrii: opcjonalna wartość używana tylko z jawnym zapytaniem użytkownika i używana wewnętrznie w firmie Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-146">Telemetry profile: an optional value only used with explicit user opt-in and used internally at Microsoft.</span></span> |
| <span data-ttu-id="ea0fc-147">>= 2,0</span><span class="sxs-lookup"><span data-stu-id="ea0fc-147">>=2.0</span></span>        | <span data-ttu-id="ea0fc-148">Argumenty polecenia i opcje: zbierane są kilka argumentów i opcji (nie dowolnych ciągów).</span><span class="sxs-lookup"><span data-stu-id="ea0fc-148">Command arguments and options: several arguments and options are collected (not arbitrary strings).</span></span> <span data-ttu-id="ea0fc-149">Zobacz [zebrane opcje](#collected-options).</span><span class="sxs-lookup"><span data-stu-id="ea0fc-149">See [collected options](#collected-options).</span></span> <span data-ttu-id="ea0fc-150">Skrót po 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-150">Hashed after 2.1.300.</span></span> |
| <span data-ttu-id="ea0fc-151">>= 2,0</span><span class="sxs-lookup"><span data-stu-id="ea0fc-151">>=2.0</span></span>         | <span data-ttu-id="ea0fc-152">Czy zestaw SDK działa w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-152">Whether the SDK is running in a container.</span></span> |
| <span data-ttu-id="ea0fc-153">>= 2,0</span><span class="sxs-lookup"><span data-stu-id="ea0fc-153">>=2.0</span></span>         | <span data-ttu-id="ea0fc-154">Platformy docelowe (ze `TargetFramework` zdarzenia), które zostały zmieszane, począwszy od 2,1.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-154">Target frameworks (from the `TargetFramework` event), hashed starting in 2.1.</span></span> |
| <span data-ttu-id="ea0fc-155">>= 2,0</span><span class="sxs-lookup"><span data-stu-id="ea0fc-155">>=2.0</span></span>         | <span data-ttu-id="ea0fc-156">Adres MAC w postaci skrótu Access Control: kryptograficzny (SHA256) anonimowy i unikatowy identyfikator dla komputera.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-156">Hashed Media Access Control (MAC) address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> |
| <span data-ttu-id="ea0fc-157">>= 2,0</span><span class="sxs-lookup"><span data-stu-id="ea0fc-157">>=2.0</span></span>         | <span data-ttu-id="ea0fc-158">Skrót bieżącego katalogu roboczego.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-158">Hashed current working directory.</span></span> |
| <span data-ttu-id="ea0fc-159">>= 2,0</span><span class="sxs-lookup"><span data-stu-id="ea0fc-159">>=2.0</span></span>         | <span data-ttu-id="ea0fc-160">Zainstaluj Raport z sukcesem z nazwą pliku exe Instalatora.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-160">Install success report, with hashed installer exe filename.</span></span> |
| <span data-ttu-id="ea0fc-161">>= 2.1.300</span><span class="sxs-lookup"><span data-stu-id="ea0fc-161">>=2.1.300</span></span>     | <span data-ttu-id="ea0fc-162">Wersja jądra.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-162">Kernel version.</span></span> |
| <span data-ttu-id="ea0fc-163">>= 2.1.300</span><span class="sxs-lookup"><span data-stu-id="ea0fc-163">>=2.1.300</span></span>     | <span data-ttu-id="ea0fc-164">Libc wydanie/wersja.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-164">Libc release/version.</span></span> |
| <span data-ttu-id="ea0fc-165">>= 3.0.100</span><span class="sxs-lookup"><span data-stu-id="ea0fc-165">>=3.0.100</span></span>     | <span data-ttu-id="ea0fc-166">Czy dane wyjściowe zostały przekierowane (wartość true lub false).</span><span class="sxs-lookup"><span data-stu-id="ea0fc-166">Whether the output was redirected (true or false).</span></span> |
| <span data-ttu-id="ea0fc-167">>= 3.0.100</span><span class="sxs-lookup"><span data-stu-id="ea0fc-167">>=3.0.100</span></span>     | <span data-ttu-id="ea0fc-168">W przypadku awarii interfejsu wiersza polecenia/zestawu SDK typ wyjątku i jego ślad stosu (kod interfejsu wiersza polecenia/zestawu SDK jest dołączony do wysyłanego śladu stosu).</span><span class="sxs-lookup"><span data-stu-id="ea0fc-168">On a CLI/SDK crash, the exception type and its stack trace (only CLI/SDK code is included in the stack trace sent).</span></span> <span data-ttu-id="ea0fc-169">Aby uzyskać więcej informacji, zobacz dane [telemetryczne wyjątku awarii interfejs wiersza polecenia platformy .NET Core/SDK](#net-core-clisdk-crash-exception-telemetry-collected).</span><span class="sxs-lookup"><span data-stu-id="ea0fc-169">For more information, see [.NET Core CLI/SDK crash exception telemetry collected](#net-core-clisdk-crash-exception-telemetry-collected).</span></span> |

### <a name="collected-options"></a><span data-ttu-id="ea0fc-170">Zebrane opcje</span><span class="sxs-lookup"><span data-stu-id="ea0fc-170">Collected options</span></span>

<span data-ttu-id="ea0fc-171">Niektóre polecenia wysyłają dodatkowe dane.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-171">Certain commands send additional data.</span></span> <span data-ttu-id="ea0fc-172">Podzbiór poleceń wysyła pierwszy argument:</span><span class="sxs-lookup"><span data-stu-id="ea0fc-172">A subset of commands sends the first argument:</span></span>

| <span data-ttu-id="ea0fc-173">Polecenie</span><span class="sxs-lookup"><span data-stu-id="ea0fc-173">Command</span></span>               | <span data-ttu-id="ea0fc-174">Wysłane dane pierwszego argumentu</span><span class="sxs-lookup"><span data-stu-id="ea0fc-174">First argument data sent</span></span>                |
|-----------------------|-----------------------------------------|
| `dotnet help <arg>`   | <span data-ttu-id="ea0fc-175">Trwa kwerenda pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-175">The command help is being queried for.</span></span>  |
| `dotnet new <arg>`    | <span data-ttu-id="ea0fc-176">Nazwa szablonu (wartość skrótu).</span><span class="sxs-lookup"><span data-stu-id="ea0fc-176">The template name (hashed).</span></span>             |
| `dotnet add <arg>`    | <span data-ttu-id="ea0fc-177">Słowo `package` lub `reference` .</span><span class="sxs-lookup"><span data-stu-id="ea0fc-177">The word `package` or `reference`.</span></span>      |
| `dotnet remove <arg>` | <span data-ttu-id="ea0fc-178">Słowo `package` lub `reference` .</span><span class="sxs-lookup"><span data-stu-id="ea0fc-178">The word `package` or `reference`.</span></span>      |
| `dotnet list <arg>`   | <span data-ttu-id="ea0fc-179">Słowo `package` lub `reference` .</span><span class="sxs-lookup"><span data-stu-id="ea0fc-179">The word `package` or `reference`.</span></span>      |
| `dotnet sln <arg>`    | <span data-ttu-id="ea0fc-180">Słowo `add` , `list` , lub `remove` .</span><span class="sxs-lookup"><span data-stu-id="ea0fc-180">The word `add`, `list`, or `remove`.</span></span>    |
| `dotnet nuget <arg>`  | <span data-ttu-id="ea0fc-181">Słowo `delete` , `locals` , lub `push` .</span><span class="sxs-lookup"><span data-stu-id="ea0fc-181">The word `delete`, `locals`, or `push`.</span></span> |

<span data-ttu-id="ea0fc-182">Podzbiór poleceń wysyła wybrane opcje, jeśli są używane, wraz z ich wartościami:</span><span class="sxs-lookup"><span data-stu-id="ea0fc-182">A subset of commands sends selected options if they're used, along with their values:</span></span>

| <span data-ttu-id="ea0fc-183">Opcja</span><span class="sxs-lookup"><span data-stu-id="ea0fc-183">Option</span></span>                  | <span data-ttu-id="ea0fc-184">Polecenia</span><span class="sxs-lookup"><span data-stu-id="ea0fc-184">Commands</span></span>                                                                                       |
|-------------------------|------------------------------------------------------------------------------------------------|
| `--verbosity`           | <span data-ttu-id="ea0fc-185">Wszystkie polecenia</span><span class="sxs-lookup"><span data-stu-id="ea0fc-185">All commands</span></span>                                                                                   |
| `--language`            | `dotnet new`                                                                                   |
| `--configuration`       | <span data-ttu-id="ea0fc-186">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="ea0fc-186">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`</span></span>                  |
| `--framework`           | <span data-ttu-id="ea0fc-187">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest`</span><span class="sxs-lookup"><span data-stu-id="ea0fc-187">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest`</span></span> |
| `--runtime`             | <span data-ttu-id="ea0fc-188">`dotnet build`,  `dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="ea0fc-188">`dotnet build`,  `dotnet publish`</span></span>                                                              |
| `--platform`            | `dotnet vstest`                                                                                |
| `--logger`              | `dotnet vstest`                                                                                |
| `--sdk-package-version` | `dotnet migrate`                                                                               |

<span data-ttu-id="ea0fc-189">Z wyjątkiem `--verbosity` i `--sdk-package-version` , wszystkie inne wartości są zmieszane, począwszy od platformy .NET Core 2.1.100 SDK.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-189">Except for `--verbosity` and `--sdk-package-version`, all the other values are hashed starting with .NET Core 2.1.100 SDK.</span></span>

## <a name="net-core-clisdk-crash-exception-telemetry-collected"></a><span data-ttu-id="ea0fc-190">Zebrane dane telemetryczne wyjątku awarii interfejs wiersza polecenia platformy .NET Core/SDK</span><span class="sxs-lookup"><span data-stu-id="ea0fc-190">.NET Core CLI/SDK crash exception telemetry collected</span></span>

<span data-ttu-id="ea0fc-191">Jeśli wystąpi awaria interfejs wiersza polecenia platformy .NET Core/SDK, zbierane są informacje o nazwie i śladie stosu dla kodu CLI/SDK.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-191">If the .NET Core CLI/SDK crashes, it collects the name of the exception and stack trace of the CLI/SDK code.</span></span> <span data-ttu-id="ea0fc-192">Te informacje są zbierane w celu oceny problemów i poprawy jakości zestaw .NET Core SDK i interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-192">This information is collected to assess problems and improve the quality of the .NET Core SDK and CLI.</span></span> <span data-ttu-id="ea0fc-193">Ten artykuł zawiera informacje o zbieranych danych.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-193">This article provides information about the data we collect.</span></span> <span data-ttu-id="ea0fc-194">Zawiera również wskazówki dotyczące sposobu, w jaki użytkownicy tworzą własne wersje zestaw .NET Core SDK mogą uniknąć przypadkowego ujawnienia informacji osobistych lub poufnych.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-194">It also provides tips on how users building their own version of the .NET Core SDK can avoid inadvertent disclosure of personal or sensitive information.</span></span>

### <a name="types-of-collected-data"></a><span data-ttu-id="ea0fc-195">Typy zebranych danych</span><span class="sxs-lookup"><span data-stu-id="ea0fc-195">Types of collected data</span></span>

<span data-ttu-id="ea0fc-196">Interfejs wiersza polecenia platformy .NET Core zbiera informacje tylko dla wyjątków CLI/SDK, a nie wyjątków w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-196">.NET Core CLI collects information for CLI/SDK exceptions only, not exceptions in your application.</span></span> <span data-ttu-id="ea0fc-197">Zebrane dane zawierają nazwę wyjątku i ślad stosu.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-197">The collected data contains the name of the exception and the stack trace.</span></span> <span data-ttu-id="ea0fc-198">Ten ślad stosu jest kodem CLI/SDK.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-198">This stack trace is of CLI/SDK code.</span></span>

<span data-ttu-id="ea0fc-199">Poniższy przykład przedstawia rodzaj zbieranych danych:</span><span class="sxs-lookup"><span data-stu-id="ea0fc-199">The following example shows the kind of data that is collected:</span></span>

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

### <a name="avoid-inadvertent-disclosure-of-information"></a><span data-ttu-id="ea0fc-200">Unikaj przypadkowego ujawnienia informacji</span><span class="sxs-lookup"><span data-stu-id="ea0fc-200">Avoid inadvertent disclosure of information</span></span>

<span data-ttu-id="ea0fc-201">Współautorzy platformy .NET Core i inne osoby, na których jest uruchomiona wersja zestaw .NET Core SDK należy wziąć pod uwagę ścieżkę do kodu źródłowego zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-201">.NET Core contributors and anyone else running a version of the .NET Core SDK that they built themselves should consider the path to their SDK source code.</span></span> <span data-ttu-id="ea0fc-202">Jeśli wystąpi awaria podczas korzystania z zestaw .NET Core SDK, który jest kompilacją niestandardową lub skonfigurowaną za pomocą niestandardowych plików symboli kompilacji, ścieżka pliku źródłowego zestawu SDK z maszyny kompilacji jest zbierana jako część śladu stosu i nie ma wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-202">If a crash occurs while using a .NET Core SDK that is a custom debug build or configured with custom build symbol files, the SDK source file path from the build machine is collected as part of the stack trace and isn't hashed.</span></span>

<span data-ttu-id="ea0fc-203">Z tego powodu niestandardowe kompilacje zestaw .NET Core SDK nie powinny znajdować się w katalogach, których nazwy ścieżek ujawniają osobiste lub poufne informacje.</span><span class="sxs-lookup"><span data-stu-id="ea0fc-203">Because of this, custom builds of the .NET Core SDK shouldn't be located in directories whose path names expose personal or sensitive information.</span></span>

## <a name="see-also"></a><span data-ttu-id="ea0fc-204">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ea0fc-204">See also</span></span>

- [<span data-ttu-id="ea0fc-205">Dane telemetryczne interfejs wiersza polecenia platformy .NET Core-2019 Q2</span><span class="sxs-lookup"><span data-stu-id="ea0fc-205">.NET Core CLI Telemetry - 2019 Q2 Data</span></span>](https://dotnet.microsoft.com/platform/telemetry/dotnet-core-cli-2019q2)
- [<span data-ttu-id="ea0fc-206">Źródło odwołania telemetrii (repozytorium dotnet/SDK)</span><span class="sxs-lookup"><span data-stu-id="ea0fc-206">Telemetry reference source (dotnet/sdk repository)</span></span>](https://github.com/dotnet/sdk/tree/master/src/Cli/dotnet/Telemetry)
