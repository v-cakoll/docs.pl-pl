---
title: Zbieranie danych telemetrycznych przez ML.NET CLI
description: Dowiedz się więcej o ML.NET funkcji telemetrii wiersza wiersza, które zbierają informacje o użyciu do analizy, jakie dane są zbierane i jak je wyłączyć. Ponadto znajdź łącza do umowy licencyjnej .NET i informacje o zgodności z RODO firmy Microsoft.
ms.topic: conceptual
ms.date: 09/03/2019
ms.custom: mlnet-tooling
ms.openlocfilehash: 99e11acba343cc689c3219ca9316144fc62cd618
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78849747"
---
# <a name="telemetry-collection-by-the-mlnet-cli"></a><span data-ttu-id="5795d-104">Zbieranie danych telemetrycznych przez ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="5795d-104">Telemetry collection by the ML.NET CLI</span></span>

<span data-ttu-id="5795d-105">[ML.NET CLI](https://aka.ms/mlnet-cli) zawiera funkcję telemetrii, która zbiera anonimowe dane użycia, które są agregowane do użytku przez firmę Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5795d-105">The [ML.NET CLI](https://aka.ms/mlnet-cli) includes a telemetry feature that collects anonymous usage data that is aggregated for use by Microsoft.</span></span>

## <a name="how-microsoft-uses-the-data"></a><span data-ttu-id="5795d-106">Jak firma Microsoft wykorzystuje dane</span><span class="sxs-lookup"><span data-stu-id="5795d-106">How Microsoft uses the data</span></span>

<span data-ttu-id="5795d-107">Zespół produktu używa danych telemetrycznych ML.NET CLI, aby pomóc w zrozumieniu, jak ulepszyć narzędzia.</span><span class="sxs-lookup"><span data-stu-id="5795d-107">The product team uses ML.NET CLI telemetry data to help understand how to improve the tools.</span></span> <span data-ttu-id="5795d-108">Na przykład jeśli klienci rzadko używają określonego zadania uczenia maszynowego, zespół produktu bada, dlaczego i używa wyników do ustalania priorytetów tworzenia funkcji.</span><span class="sxs-lookup"><span data-stu-id="5795d-108">For example, if customers infrequently use a particular machine learning task, the product team investigates why and uses findings to prioritize feature development.</span></span> <span data-ttu-id="5795d-109">ML.NET telemetrii interfejsu i telewizji pomaga również w debugowaniu problemów, takich jak awarie i anomalie kodu.</span><span class="sxs-lookup"><span data-stu-id="5795d-109">ML.NET CLI telemetry also helps with debugging of issues such as crashes and code anomalies.</span></span>

<span data-ttu-id="5795d-110">Podczas gdy zespół produktów docenia tę wiedzę, wiemy również, że nie każdy chce wysłać te dane.</span><span class="sxs-lookup"><span data-stu-id="5795d-110">While the product team appreciates this insight, we also know that not everyone wants to send this data.</span></span> [<span data-ttu-id="5795d-111">Dowiedz się, jak wyłączyć telemetrię.</span><span class="sxs-lookup"><span data-stu-id="5795d-111">Find out how to disable telemetry.</span></span>](#opt-out-of-data-collection)

## <a name="scope"></a><span data-ttu-id="5795d-112">Zakres</span><span class="sxs-lookup"><span data-stu-id="5795d-112">Scope</span></span>

<span data-ttu-id="5795d-113">Polecenie `mlnet` uruchamia ML.NET CLI, ale samo polecenie nie zbiera danych telemetrycznych.</span><span class="sxs-lookup"><span data-stu-id="5795d-113">The `mlnet` command launches the ML.NET CLI, but the command itself doesn't collect telemetry.</span></span>

<span data-ttu-id="5795d-114">Telemetria *nie jest włączona* po uruchomieniu `mlnet` polecenia bez innego polecenia dołączone.</span><span class="sxs-lookup"><span data-stu-id="5795d-114">Telemetry *isn't enabled* when you run the `mlnet` command with no other command attached.</span></span> <span data-ttu-id="5795d-115">Przykład:</span><span class="sxs-lookup"><span data-stu-id="5795d-115">For example:</span></span>

- `mlnet`
- `mlnet --help`

<span data-ttu-id="5795d-116">Telemetria *jest włączona* po uruchomieniu [polecenia ML.NET wiersza polecenia ,](../reference/ml-net-cli-reference.md)na przykład . `mlnet auto-train`</span><span class="sxs-lookup"><span data-stu-id="5795d-116">Telemetry *is enabled* when you run an [ML.NET CLI command](../reference/ml-net-cli-reference.md), such as `mlnet auto-train`.</span></span>

## <a name="opt-out-of-data-collection"></a><span data-ttu-id="5795d-117">Rezygnacja z gromadzenia danych</span><span class="sxs-lookup"><span data-stu-id="5795d-117">Opt out of data collection</span></span>

<span data-ttu-id="5795d-118">Funkcja telemetrii ML.NET CLI jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="5795d-118">The ML.NET CLI telemetry feature is enabled by default.</span></span>

<span data-ttu-id="5795d-119">Zrezygnuj z `MLDOTNET_CLI_TELEMETRY_OPTOUT` funkcji telemetrii, ustawiając zmienną środowiskową na `1` lub `true`.</span><span class="sxs-lookup"><span data-stu-id="5795d-119">Opt out of the telemetry feature by setting the `MLDOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span> <span data-ttu-id="5795d-120">Ta zmienna środowiskowa ma zastosowanie globalnie do narzędzia ML.NET CLI.</span><span class="sxs-lookup"><span data-stu-id="5795d-120">This environment variable applies globally to the ML.NET CLI tool.</span></span>

## <a name="data-points-collected"></a><span data-ttu-id="5795d-121">Zebrane punkty danych</span><span class="sxs-lookup"><span data-stu-id="5795d-121">Data points collected</span></span>

<span data-ttu-id="5795d-122">Funkcja zbiera następujące dane:</span><span class="sxs-lookup"><span data-stu-id="5795d-122">The feature collects the following data:</span></span>

- <span data-ttu-id="5795d-123">Jakie polecenie zostało wywołane, takie jak`auto-train`</span><span class="sxs-lookup"><span data-stu-id="5795d-123">What command was invoked, such as `auto-train`</span></span>
- <span data-ttu-id="5795d-124">Używane nazwy parametrów wiersza polecenia (czyli "nazwa zestawu danych, nazwa kolumny etykiety, ml-task, ścieżka wyjścia, czas max-eksploracji, szczegółowość")</span><span class="sxs-lookup"><span data-stu-id="5795d-124">Command-line parameter names used (that is, "dataset-name, label-column-name, ml-task, output-path, max-exploration-time, verbosity")</span></span>
- <span data-ttu-id="5795d-125">Hashed adres MAC: kryptograficznie (SHA256) anonimowy i unikalny identyfikator dla komputera</span><span class="sxs-lookup"><span data-stu-id="5795d-125">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine</span></span>
- <span data-ttu-id="5795d-126">Sygnatura czasowa wywołania</span><span class="sxs-lookup"><span data-stu-id="5795d-126">Timestamp of an invocation</span></span>
- <span data-ttu-id="5795d-127">Trzy oktetowe adres IP (nie pełny adres IP) używane tylko do określania lokalizacji geograficznej</span><span class="sxs-lookup"><span data-stu-id="5795d-127">Three octet IP address (not full IP address) used only to determine geographical location</span></span>
- <span data-ttu-id="5795d-128">Nazwa wszystkich użytych argumentów/parametrów.</span><span class="sxs-lookup"><span data-stu-id="5795d-128">Name of all arguments/parameters used.</span></span> <span data-ttu-id="5795d-129">Nie wartości klienta, takie jak ciągi znaków</span><span class="sxs-lookup"><span data-stu-id="5795d-129">Not the customer's values, such as strings</span></span>
- <span data-ttu-id="5795d-130">Haszowane nazwy pliku zestawu danych</span><span class="sxs-lookup"><span data-stu-id="5795d-130">Hashed dataset filename</span></span>
- <span data-ttu-id="5795d-131">Zasobnik rozmiaru pliku zestawu danych</span><span class="sxs-lookup"><span data-stu-id="5795d-131">Dataset file-size bucket</span></span>
- <span data-ttu-id="5795d-132">System operacyjny i wersja</span><span class="sxs-lookup"><span data-stu-id="5795d-132">Operating system and version</span></span>
- <span data-ttu-id="5795d-133">Wartość parametru --task: Wartości kategorii, takie jak `regression`, `binary-classification`, i`multiclass-classification`</span><span class="sxs-lookup"><span data-stu-id="5795d-133">Value of --task parameter: Categorical values, such as `regression`, `binary-classification`, and `multiclass-classification`</span></span>
- <span data-ttu-id="5795d-134">ML.NET wersji CLI (czyli 0.3.27703.4)</span><span class="sxs-lookup"><span data-stu-id="5795d-134">ML.NET CLI version (that is, 0.3.27703.4)</span></span>

<span data-ttu-id="5795d-135">Dane są bezpiecznie wysyłane do serwerów firmy Microsoft przy użyciu technologii [usługi Azure Application Insights,](https://azure.microsoft.com/services/application-insights/) przechowywane w ramach ograniczonego dostępu i używane pod ścisłymi kontrolami zabezpieczeń z bezpiecznych systemów [usługi Azure Storage.](https://azure.microsoft.com/services/storage/)</span><span class="sxs-lookup"><span data-stu-id="5795d-135">The data is sent securely to Microsoft servers using [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and used under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

### <a name="data-points-not-collected"></a><span data-ttu-id="5795d-136">Punkty danych nie są zbierane</span><span class="sxs-lookup"><span data-stu-id="5795d-136">Data points not collected</span></span>

<span data-ttu-id="5795d-137">Funkcja telemetrii *nie* zbiera:</span><span class="sxs-lookup"><span data-stu-id="5795d-137">The telemetry feature *doesn't* collect:</span></span>

- <span data-ttu-id="5795d-138">danych osobowych, takich jak nazwy użytkowników</span><span class="sxs-lookup"><span data-stu-id="5795d-138">personal data, such as usernames</span></span>
- <span data-ttu-id="5795d-139">nazwy plików zestawu danych</span><span class="sxs-lookup"><span data-stu-id="5795d-139">dataset filenames</span></span>
- <span data-ttu-id="5795d-140">dane z plików zestawu danych</span><span class="sxs-lookup"><span data-stu-id="5795d-140">data from dataset files</span></span>

<span data-ttu-id="5795d-141">Jeśli podejrzewasz, że ML.NET telemetrii cli zbiera poufne dane lub że dane są niebezpiecznie lub niewłaściwie obsługiwane, zgłoś problem w repozytorium [ML.NET](https://github.com/dotnet/machinelearning) w celu zbadania.</span><span class="sxs-lookup"><span data-stu-id="5795d-141">If you suspect that the ML.NET CLI telemetry is collecting sensitive data or that the data is being insecurely or inappropriately handled, file an issue in the [ML.NET](https://github.com/dotnet/machinelearning) repository for investigation.</span></span>

## <a name="license"></a><span data-ttu-id="5795d-142">Licencja</span><span class="sxs-lookup"><span data-stu-id="5795d-142">License</span></span>

<span data-ttu-id="5795d-143">Dystrybucja ML.NET CLI firmy Microsoft jest licencjonowana z [postanowieniami licencyjnymi firmy Microsoft: Microsoft .NET Library](https://aka.ms/dotnet-core-eula).</span><span class="sxs-lookup"><span data-stu-id="5795d-143">The Microsoft distribution of ML.NET CLI is licensed with the [Microsoft Software License Terms: Microsoft .NET Library](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="5795d-144">Szczegółowe informacje na temat gromadzenia i przetwarzania danych można znaleźć w sekcji zatytułowanej "Dane".</span><span class="sxs-lookup"><span data-stu-id="5795d-144">For details on data collection and processing, see the section entitled "Data."</span></span>

## <a name="disclosure"></a><span data-ttu-id="5795d-145">Ujawnienie</span><span class="sxs-lookup"><span data-stu-id="5795d-145">Disclosure</span></span>

<span data-ttu-id="5795d-146">Po pierwszym uruchomieniu polecenia ML.NET `mlnet auto-train` [CLI,](../reference/ml-net-cli-reference.md) takie jak , narzędzie ML.NET CLI wyświetla tekst ujawnienia, który informuje, jak zrezygnować z telemetrii.</span><span class="sxs-lookup"><span data-stu-id="5795d-146">When you first run a [ML.NET CLI command](../reference/ml-net-cli-reference.md) such as `mlnet auto-train`, the ML.NET CLI tool displays disclosure text that tells you how to opt out of telemetry.</span></span> <span data-ttu-id="5795d-147">Tekst może się nieznacznie różnić w zależności od używanej wersji kaliów.</span><span class="sxs-lookup"><span data-stu-id="5795d-147">Text may vary slightly depending on the version of the CLI you're running.</span></span>

## <a name="see-also"></a><span data-ttu-id="5795d-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5795d-148">See also</span></span>

- [<span data-ttu-id="5795d-149">ML.NET odwołanie cli</span><span class="sxs-lookup"><span data-stu-id="5795d-149">ML.NET CLI reference</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="5795d-150">Postanowienia licencyjne dotyczące oprogramowania firmy Microsoft: Microsoft .NET Library</span><span class="sxs-lookup"><span data-stu-id="5795d-150">Microsoft Software License Terms: Microsoft .NET Library</span></span>](https://aka.ms/dotnet-core-eula)
- [<span data-ttu-id="5795d-151">Prywatność w firmie Microsoft</span><span class="sxs-lookup"><span data-stu-id="5795d-151">Privacy at Microsoft</span></span>](https://www.microsoft.com/trustcenter/privacy/)
- [<span data-ttu-id="5795d-152">Oświadczenie o ochronie prywatności w firmie Microsoft</span><span class="sxs-lookup"><span data-stu-id="5795d-152">Microsoft Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
