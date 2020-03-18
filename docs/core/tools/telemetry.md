---
title: Dane telemetryczne sdk.NET Core
description: Odkryj funkcje telemetrii SDK .NET Core, które zbierają informacje o użyciu do analizy, jakie dane są zbierane i jak je wyłączyć.
author: KathleenDollard
ms.date: 08/27/2019
ms.openlocfilehash: 9d5d7ff09ade89712f2fbbe35224851bb1c28b4c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156689"
---
# <a name="net-core-sdk-telemetry"></a><span data-ttu-id="6e91e-103">Dane telemetryczne sdk.NET Core</span><span class="sxs-lookup"><span data-stu-id="6e91e-103">.NET Core SDK telemetry</span></span>

<span data-ttu-id="6e91e-104">Zestaw [SDK .NET Core](index.md) zawiera funkcję telemetrii, która zbiera dane użycia i informacje o wyjątkach po awarii procesora CLI.NET Core SDK includes a telemetry feature that collects usage data and exception information when the .NET Core CLI crashes.</span><span class="sxs-lookup"><span data-stu-id="6e91e-104">The [.NET Core SDK](index.md) includes a telemetry feature that collects usage data and exception information when the .NET Core CLI crashes.</span></span> <span data-ttu-id="6e91e-105">.NET Core CLI pochodzi z .NET Core SDK i jest zestaw zleceń, które umożliwiają tworzenie, testowanie i publikowanie aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6e91e-105">The .NET Core CLI comes with the .NET Core SDK and is the set of verbs that enable you to build, test, and publish your .NET Core apps.</span></span> <span data-ttu-id="6e91e-106">Ważne jest, aby zespół .NET rozumiał, jak narzędzia są używane, dzięki czemu można je ulepszyć.</span><span class="sxs-lookup"><span data-stu-id="6e91e-106">It's important that the .NET team understands how the tools are used so they can be improved.</span></span> <span data-ttu-id="6e91e-107">Informacje o niepowodzeniach pomagają zespołowi rozwiązywać problemy i naprawiać błędy.</span><span class="sxs-lookup"><span data-stu-id="6e91e-107">Information on failures helps the team resolve problems and fix bugs.</span></span>

<span data-ttu-id="6e91e-108">Zebrane dane są anonimowe i publikowane łącznie na licencji [Creative Commons Uznanie autorstwa.](https://creativecommons.org/licenses/by/4.0/)</span><span class="sxs-lookup"><span data-stu-id="6e91e-108">The collected data is anonymous and published in aggregate under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span>

## <a name="scope"></a><span data-ttu-id="6e91e-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="6e91e-109">Scope</span></span>

<span data-ttu-id="6e91e-110">`dotnet`ma dwie funkcje: uruchamianie aplikacji i wykonywanie poleceń wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="6e91e-110">`dotnet` has two functions: to run apps, and to execute CLI commands.</span></span> <span data-ttu-id="6e91e-111">Dane telemetryczne nie `dotnet` są *zbierane* podczas uruchamiania aplikacji w następującym formacie:</span><span class="sxs-lookup"><span data-stu-id="6e91e-111">Telemetry *isn't collected* when using `dotnet` to start an application in the following format:</span></span>

- `dotnet [path-to-app].dll`

<span data-ttu-id="6e91e-112">Dane telemetryczne *są zbierane* podczas korzystania z dowolnych [poleceń cli .NET Core,](index.md)takich jak:</span><span class="sxs-lookup"><span data-stu-id="6e91e-112">Telemetry *is collected* when using any of the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet run`

## <a name="how-to-opt-out"></a><span data-ttu-id="6e91e-113">Jak zrezygnować</span><span class="sxs-lookup"><span data-stu-id="6e91e-113">How to opt out</span></span>

<span data-ttu-id="6e91e-114">Funkcja telemetrii SDK .NET Core jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="6e91e-114">The .NET Core SDK telemetry feature is enabled by default.</span></span> <span data-ttu-id="6e91e-115">Aby zrezygnować z funkcji telemetrii, `1` `true`ustaw zmienną środowiskową `DOTNET_CLI_TELEMETRY_OPTOUT` na lub .</span><span class="sxs-lookup"><span data-stu-id="6e91e-115">To opt out of the telemetry feature, set the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

<span data-ttu-id="6e91e-116">Pojedynczy wpis telemetrii jest również wysyłany przez instalatora SDK .NET Core, gdy nastąpi pomyślna instalacja.</span><span class="sxs-lookup"><span data-stu-id="6e91e-116">A single telemetry entry is also sent by the .NET Core SDK installer when a successful installation happens.</span></span> <span data-ttu-id="6e91e-117">Aby zrezygnować, `DOTNET_CLI_TELEMETRY_OPTOUT` należy ustawić zmienną środowiskową przed zainstalowaniem zestawu SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6e91e-117">To opt out, set the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable before you install the .NET Core SDK.</span></span>

## <a name="disclosure"></a><span data-ttu-id="6e91e-118">Ujawnienie</span><span class="sxs-lookup"><span data-stu-id="6e91e-118">Disclosure</span></span>

<span data-ttu-id="6e91e-119">Zestaw SDK .NET Core wyświetla tekst podobny do następującego po pierwszym uruchomieniu jednego z `dotnet build` [poleceń cli .NET Core](index.md) (na przykład).</span><span class="sxs-lookup"><span data-stu-id="6e91e-119">The .NET Core SDK displays text similar to the following when you first run one of the [.NET Core CLI commands](index.md) (for example, `dotnet build`).</span></span> <span data-ttu-id="6e91e-120">Tekst może się nieznacznie różnić w zależności od używanej wersji programu SDK.</span><span class="sxs-lookup"><span data-stu-id="6e91e-120">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="6e91e-121">To środowisko "pierwszego uruchomienia" polega na tym, jak firma Microsoft powiadamia użytkownika o zbieraniu danych.</span><span class="sxs-lookup"><span data-stu-id="6e91e-121">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

```console
Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience. The data is anonymous. It is collected by Microsoft and shared with the community. You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

## <a name="data-points"></a><span data-ttu-id="6e91e-122">Punkty danych</span><span class="sxs-lookup"><span data-stu-id="6e91e-122">Data points</span></span>

<span data-ttu-id="6e91e-123">Funkcja telemetrii nie zbiera danych osobowych, takich jak nazwy użytkowników lub adresy e-mail.</span><span class="sxs-lookup"><span data-stu-id="6e91e-123">The telemetry feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="6e91e-124">Nie skanuje kodu i nie wyodrębnia danych na poziomie projektu, takich jak nazwa, repozytorium lub autor.</span><span class="sxs-lookup"><span data-stu-id="6e91e-124">It doesn't scan your code and doesn't extract project-level data, such as name, repository, or author.</span></span> <span data-ttu-id="6e91e-125">Dane są bezpiecznie wysyłane do serwerów firmy Microsoft przy użyciu technologii [usługi Azure Monitor,](https://azure.microsoft.com/services/monitor/) przechowywane w ramach ograniczonego dostępu i publikowane pod ścisłymi kontrolami zabezpieczeń z bezpiecznych systemów [usługi Azure Storage.](https://azure.microsoft.com/services/storage/)</span><span class="sxs-lookup"><span data-stu-id="6e91e-125">The data is sent securely to Microsoft servers using [Azure Monitor](https://azure.microsoft.com/services/monitor/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="6e91e-126">Ochrona prywatności jest dla nas ważna.</span><span class="sxs-lookup"><span data-stu-id="6e91e-126">Protecting your privacy is important to us.</span></span> <span data-ttu-id="6e91e-127">Jeśli podejrzewasz, że dane telemetryczne zbierają poufne dane lub dane są niebezpiecznie lub niewłaściwie obsługiwane, zgłoś problem w [dotnet@microsoft.com](mailto:dotnet@microsoft.com) repozytorium [dotnet/cli](https://github.com/dotnet/cli/issues) lub wyślij wiadomość e-mail do badania.</span><span class="sxs-lookup"><span data-stu-id="6e91e-127">If you suspect the telemetry is collecting sensitive data or the data is being insecurely or inappropriately handled, file an issue in the [dotnet/cli](https://github.com/dotnet/cli/issues) repository or send an email to [dotnet@microsoft.com](mailto:dotnet@microsoft.com) for investigation.</span></span>

<span data-ttu-id="6e91e-128">Funkcja telemetrii zbiera następujące dane:</span><span class="sxs-lookup"><span data-stu-id="6e91e-128">The telemetry feature collects the following data:</span></span>

| <span data-ttu-id="6e91e-129">Wersje SDK</span><span class="sxs-lookup"><span data-stu-id="6e91e-129">SDK versions</span></span> | <span data-ttu-id="6e91e-130">Dane</span><span class="sxs-lookup"><span data-stu-id="6e91e-130">Data</span></span> |
|--------------|------|
| <span data-ttu-id="6e91e-131">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="6e91e-131">All</span></span>          | <span data-ttu-id="6e91e-132">Sygnatura czasowa wywołania.</span><span class="sxs-lookup"><span data-stu-id="6e91e-132">Timestamp of invocation.</span></span> |
| <span data-ttu-id="6e91e-133">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="6e91e-133">All</span></span>          | <span data-ttu-id="6e91e-134">Polecenie wywoływane (na przykład "build"), haszowane począwszy od 2.1.</span><span class="sxs-lookup"><span data-stu-id="6e91e-134">Command invoked (for example, "build"), hashed starting in 2.1.</span></span> |
| <span data-ttu-id="6e91e-135">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="6e91e-135">All</span></span>          | <span data-ttu-id="6e91e-136">Trzy oktetowe adres IP używane do określenia lokalizacji geograficznej.</span><span class="sxs-lookup"><span data-stu-id="6e91e-136">Three octet IP address used to determine the geographical location.</span></span> |
| <span data-ttu-id="6e91e-137">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="6e91e-137">All</span></span>          | <span data-ttu-id="6e91e-138">System operacyjny i wersja.</span><span class="sxs-lookup"><span data-stu-id="6e91e-138">Operating system and version.</span></span> |
| <span data-ttu-id="6e91e-139">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="6e91e-139">All</span></span>          | <span data-ttu-id="6e91e-140">Identyfikator działania (RID) jest uruchomiony na sdk.</span><span class="sxs-lookup"><span data-stu-id="6e91e-140">Runtime ID (RID) the SDK is running on.</span></span> |
| <span data-ttu-id="6e91e-141">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="6e91e-141">All</span></span>          | <span data-ttu-id="6e91e-142">Wersja SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6e91e-142">.NET Core SDK version.</span></span> |
| <span data-ttu-id="6e91e-143">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="6e91e-143">All</span></span>          | <span data-ttu-id="6e91e-144">Profil telemetrii: wartość opcjonalna używana tylko z jawną zgodą użytkownika i używana wewnętrznie w firmie Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6e91e-144">Telemetry profile: an optional value only used with explicit user opt-in and used internally at Microsoft.</span></span> |
| <span data-ttu-id="6e91e-145">>=2,0</span><span class="sxs-lookup"><span data-stu-id="6e91e-145">>=2.0</span></span>        | <span data-ttu-id="6e91e-146">Argumenty i opcje polecenia: zbiera się kilka argumentów i opcji (nie dowolnych ciągów).</span><span class="sxs-lookup"><span data-stu-id="6e91e-146">Command arguments and options: several arguments and options are collected (not arbitrary strings).</span></span> <span data-ttu-id="6e91e-147">Zobacz [zebrane opcje](#collected-options).</span><span class="sxs-lookup"><span data-stu-id="6e91e-147">See [collected options](#collected-options).</span></span> <span data-ttu-id="6e91e-148">Hashed po 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="6e91e-148">Hashed after 2.1.300.</span></span> |
| <span data-ttu-id="6e91e-149">>=2,0</span><span class="sxs-lookup"><span data-stu-id="6e91e-149">>=2.0</span></span>         | <span data-ttu-id="6e91e-150">Czy zestaw SDK jest uruchomiony w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="6e91e-150">Whether the SDK is running in a container.</span></span> |
| <span data-ttu-id="6e91e-151">>=2,0</span><span class="sxs-lookup"><span data-stu-id="6e91e-151">>=2.0</span></span>         | <span data-ttu-id="6e91e-152">Platformdocelowych (ze `TargetFramework` zdarzenia), haszowane począwszy od 2.1.</span><span class="sxs-lookup"><span data-stu-id="6e91e-152">Target frameworks (from the `TargetFramework` event), hashed starting in 2.1.</span></span> |
| <span data-ttu-id="6e91e-153">>=2,0</span><span class="sxs-lookup"><span data-stu-id="6e91e-153">>=2.0</span></span>         | <span data-ttu-id="6e91e-154">Hashed Media Access Control (MAC) adres: kryptograficznie (SHA256) anonimowy i unikatowy identyfikator dla komputera.</span><span class="sxs-lookup"><span data-stu-id="6e91e-154">Hashed Media Access Control (MAC) address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> |
| <span data-ttu-id="6e91e-155">>=2,0</span><span class="sxs-lookup"><span data-stu-id="6e91e-155">>=2.0</span></span>         | <span data-ttu-id="6e91e-156">Hashed bieżącego katalogu roboczego.</span><span class="sxs-lookup"><span data-stu-id="6e91e-156">Hashed current working directory.</span></span> |
| <span data-ttu-id="6e91e-157">>=2,0</span><span class="sxs-lookup"><span data-stu-id="6e91e-157">>=2.0</span></span>         | <span data-ttu-id="6e91e-158">Zainstaluj raport o powodzej sukcesu, z haszowany instalator exe nazwa_</span><span class="sxs-lookup"><span data-stu-id="6e91e-158">Install success report, with hashed installer exe filename.</span></span> |
| <span data-ttu-id="6e91e-159">>= 2,1 300</span><span class="sxs-lookup"><span data-stu-id="6e91e-159">>=2.1.300</span></span>     | <span data-ttu-id="6e91e-160">Wersja jądra.</span><span class="sxs-lookup"><span data-stu-id="6e91e-160">Kernel version.</span></span> |
| <span data-ttu-id="6e91e-161">>= 2,1 300</span><span class="sxs-lookup"><span data-stu-id="6e91e-161">>=2.1.300</span></span>     | <span data-ttu-id="6e91e-162">Libc wydania/wersji.</span><span class="sxs-lookup"><span data-stu-id="6e91e-162">Libc release/version.</span></span> |
| <span data-ttu-id="6e91e-163">>= 3,0,100</span><span class="sxs-lookup"><span data-stu-id="6e91e-163">>=3.0.100</span></span>     | <span data-ttu-id="6e91e-164">Czy dane wyjściowe zostały przekierowane (prawda lub fałsz).</span><span class="sxs-lookup"><span data-stu-id="6e91e-164">Whether the output was redirected (true or false).</span></span> |
| <span data-ttu-id="6e91e-165">>= 3,0,100</span><span class="sxs-lookup"><span data-stu-id="6e91e-165">>=3.0.100</span></span>     | <span data-ttu-id="6e91e-166">W awarii cli/SDK typ wyjątku i jego śledzenia stosu (tylko kod CLI/SDK znajduje się w śledzenia stosu wysłane).</span><span class="sxs-lookup"><span data-stu-id="6e91e-166">On a CLI/SDK crash, the exception type and its stack trace (only CLI/SDK code is included in the stack trace sent).</span></span> <span data-ttu-id="6e91e-167">Aby uzyskać więcej informacji, zobacz [.NET Core CLI/SDK błąd wyjątek telemetrii zebranych](#net-core-clisdk-crash-exception-telemetry-collected).</span><span class="sxs-lookup"><span data-stu-id="6e91e-167">For more information, see [.NET Core CLI/SDK crash exception telemetry collected](#net-core-clisdk-crash-exception-telemetry-collected).</span></span> |

### <a name="collected-options"></a><span data-ttu-id="6e91e-168">Zebrane opcje</span><span class="sxs-lookup"><span data-stu-id="6e91e-168">Collected options</span></span>

<span data-ttu-id="6e91e-169">Niektóre polecenia wysyłają dodatkowe dane.</span><span class="sxs-lookup"><span data-stu-id="6e91e-169">Certain commands send additional data.</span></span> <span data-ttu-id="6e91e-170">Pierwszy argument wysyła podzbiór poleceń:</span><span class="sxs-lookup"><span data-stu-id="6e91e-170">A subset of commands sends the first argument:</span></span>

| <span data-ttu-id="6e91e-171">Polecenie</span><span class="sxs-lookup"><span data-stu-id="6e91e-171">Command</span></span>               | <span data-ttu-id="6e91e-172">Wysłane dane pierwszego argumentu</span><span class="sxs-lookup"><span data-stu-id="6e91e-172">First argument data sent</span></span>                |
|-----------------------|-----------------------------------------|
| `dotnet help <arg>`   | <span data-ttu-id="6e91e-173">Pomoc polecenia jest przeszukiwana.</span><span class="sxs-lookup"><span data-stu-id="6e91e-173">The command help is being queried for.</span></span>  |
| `dotnet new <arg>`    | <span data-ttu-id="6e91e-174">Nazwa szablonu (haszowane).</span><span class="sxs-lookup"><span data-stu-id="6e91e-174">The template name (hashed).</span></span>             |
| `dotnet add <arg>`    | <span data-ttu-id="6e91e-175">Słowo `package` lub `reference`.</span><span class="sxs-lookup"><span data-stu-id="6e91e-175">The word `package` or `reference`.</span></span>      |
| `dotnet remove <arg>` | <span data-ttu-id="6e91e-176">Słowo `package` lub `reference`.</span><span class="sxs-lookup"><span data-stu-id="6e91e-176">The word `package` or `reference`.</span></span>      |
| `dotnet list <arg>`   | <span data-ttu-id="6e91e-177">Słowo `package` lub `reference`.</span><span class="sxs-lookup"><span data-stu-id="6e91e-177">The word `package` or `reference`.</span></span>      |
| `dotnet sln <arg>`    | <span data-ttu-id="6e91e-178">Słowo `add`, `list`lub `remove`.</span><span class="sxs-lookup"><span data-stu-id="6e91e-178">The word `add`, `list`, or `remove`.</span></span>    |
| `dotnet nuget <arg>`  | <span data-ttu-id="6e91e-179">Słowo `delete`, `locals`lub `push`.</span><span class="sxs-lookup"><span data-stu-id="6e91e-179">The word `delete`, `locals`, or `push`.</span></span> |

<span data-ttu-id="6e91e-180">Podzbiór poleceń wysyła wybrane opcje, jeśli są używane, wraz z ich wartościami:</span><span class="sxs-lookup"><span data-stu-id="6e91e-180">A subset of commands sends selected options if they're used, along with their values:</span></span>

| <span data-ttu-id="6e91e-181">Opcja</span><span class="sxs-lookup"><span data-stu-id="6e91e-181">Option</span></span>                  | <span data-ttu-id="6e91e-182">Polecenia</span><span class="sxs-lookup"><span data-stu-id="6e91e-182">Commands</span></span>                                                                                       |
|-------------------------|------------------------------------------------------------------------------------------------|
| `--verbosity`           | <span data-ttu-id="6e91e-183">Wszystkie polecenia</span><span class="sxs-lookup"><span data-stu-id="6e91e-183">All commands</span></span>                                                                                   |
| `--language`            | `dotnet new`                                                                                   |
| `--configuration`       | <span data-ttu-id="6e91e-184">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="6e91e-184">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`</span></span>                  |
| `--framework`           | <span data-ttu-id="6e91e-185">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest`</span><span class="sxs-lookup"><span data-stu-id="6e91e-185">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest`</span></span> |
| `--runtime`             | <span data-ttu-id="6e91e-186">`dotnet build`,  `dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="6e91e-186">`dotnet build`,  `dotnet publish`</span></span>                                                              |
| `--platform`            | `dotnet vstest`                                                                                |
| `--logger`              | `dotnet vstest`                                                                                |
| `--sdk-package-version` | `dotnet migrate`                                                                               |

<span data-ttu-id="6e91e-187">Z `--verbosity` wyjątkiem `--sdk-package-version`i , wszystkie inne wartości są haszowane począwszy od .NET Core 2.1.100 SDK.</span><span class="sxs-lookup"><span data-stu-id="6e91e-187">Except for `--verbosity` and `--sdk-package-version`, all the other values are hashed starting with .NET Core 2.1.100 SDK.</span></span>

## <a name="net-core-clisdk-crash-exception-telemetry-collected"></a><span data-ttu-id="6e91e-188">Zebrane dane telemetryczne wyjątku awarii wiersza wiersza wiersza usługi .NET Core/SDK</span><span class="sxs-lookup"><span data-stu-id="6e91e-188">.NET Core CLI/SDK crash exception telemetry collected</span></span>

<span data-ttu-id="6e91e-189">Jeśli .NET Core CLI/SDK ulega awarii, zbiera nazwę wyjątku i śledzenia stosu kodu CLI/SDK.</span><span class="sxs-lookup"><span data-stu-id="6e91e-189">If the .NET Core CLI/SDK crashes, it collects the name of the exception and stack trace of the CLI/SDK code.</span></span> <span data-ttu-id="6e91e-190">Te informacje są zbierane w celu oceny problemów i poprawy jakości .NET Core SDK i CLI.</span><span class="sxs-lookup"><span data-stu-id="6e91e-190">This information is collected to assess problems and improve the quality of the .NET Core SDK and CLI.</span></span> <span data-ttu-id="6e91e-191">Ten artykuł zawiera informacje o gromadzonych przez nas danych.</span><span class="sxs-lookup"><span data-stu-id="6e91e-191">This article provides information about the data we collect.</span></span> <span data-ttu-id="6e91e-192">Zawiera również wskazówki dotyczące sposobu, w jaki użytkownicy budujący własną wersję sdk .NET Core mogą uniknąć nieumyślnego ujawnienia informacji osobistych lub poufnych.</span><span class="sxs-lookup"><span data-stu-id="6e91e-192">It also provides tips on how users building their own version of the .NET Core SDK can avoid inadvertent disclosure of personal or sensitive information.</span></span>

### <a name="types-of-collected-data"></a><span data-ttu-id="6e91e-193">Rodzaje zebranych danych</span><span class="sxs-lookup"><span data-stu-id="6e91e-193">Types of collected data</span></span>

<span data-ttu-id="6e91e-194">Interfejs cli programu .NET Core zbiera informacje tylko dla wyjątków cli/SDK, a nie wyjątki w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6e91e-194">.NET Core CLI collects information for CLI/SDK exceptions only, not exceptions in your application.</span></span> <span data-ttu-id="6e91e-195">Zebrane dane zawierają nazwę wyjątku i śledzenia stosu.</span><span class="sxs-lookup"><span data-stu-id="6e91e-195">The collected data contains the name of the exception and the stack trace.</span></span> <span data-ttu-id="6e91e-196">Ten ślad stosu jest kodem CLI/SDK.</span><span class="sxs-lookup"><span data-stu-id="6e91e-196">This stack trace is of CLI/SDK code.</span></span>

<span data-ttu-id="6e91e-197">W poniższym przykładzie przedstawiono rodzaj danych, które są zbierane:</span><span class="sxs-lookup"><span data-stu-id="6e91e-197">The following example shows the kind of data that is collected:</span></span>

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

### <a name="avoid-inadvertent-disclosure-of-information"></a><span data-ttu-id="6e91e-198">Unikanie nieumyślnego ujawnienia informacji</span><span class="sxs-lookup"><span data-stu-id="6e91e-198">Avoid inadvertent disclosure of information</span></span>

<span data-ttu-id="6e91e-199">Współautorzy programu .NET Core i każda inna osoba, która uruchamia wersję sdk .NET Core SDK, którą sami stworzyli, powinni rozważyć ścieżkę do kodu źródłowego sdk.</span><span class="sxs-lookup"><span data-stu-id="6e91e-199">.NET Core contributors and anyone else running a version of the .NET Core SDK that they built themselves should consider the path to their SDK source code.</span></span> <span data-ttu-id="6e91e-200">Jeśli wystąpi awaria podczas korzystania z .NET Core SDK, który jest niestandardową kompilacją debugowania lub skonfigurowany z niestandardowymi plikami symboli kompilacji, ścieżka pliku źródłowego sdk z komputera kompilacji jest zbierana jako część śledzenia stosu i nie jest haszowana.</span><span class="sxs-lookup"><span data-stu-id="6e91e-200">If a crash occurs while using a .NET Core SDK that is a custom debug build or configured with custom build symbol files, the SDK source file path from the build machine is collected as part of the stack trace and isn't hashed.</span></span>

<span data-ttu-id="6e91e-201">Z tego powodu niestandardowe kompilacje sdk .NET Core nie powinny znajdować się w katalogach, których nazwy ścieżek udostępniają informacje osobiste lub poufne.</span><span class="sxs-lookup"><span data-stu-id="6e91e-201">Because of this, custom builds of the .NET Core SDK shouldn't be located in directories whose path names expose personal or sensitive information.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e91e-202">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e91e-202">See also</span></span>

- [<span data-ttu-id="6e91e-203">.NET Core CLI Telemetria - Dane za II kwartał 2019</span><span class="sxs-lookup"><span data-stu-id="6e91e-203">.NET Core CLI Telemetry - 2019 Q2 Data</span></span>](https://dotnet.microsoft.com/platform/telemetry/dotnet-core-cli-2019q2)
- [<span data-ttu-id="6e91e-204">Źródło odwołania telemetrii (repozytorium dotnet/cli)</span><span class="sxs-lookup"><span data-stu-id="6e91e-204">Telemetry reference source (dotnet/cli repository)</span></span>](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)
