---
title: Zbieranie danych telemetrycznych przez interfejs wiersza polecenia w strukturze ML.NET
description: Dowiedz się więcej o funkcje telemetrii strukturze ML.NET interfejsu wiersza polecenia, które zbierają użycia informacje do analizy danych, które są zbierane i jak go wyłączyć. Ponadto Znajdź łącza do umowy licencyjnej .NET i informacje o zgodności z GDPR firmy Microsoft.
ms.topic: conceptual
ms.date: 05/05/2019
ms.custom: ''
ms.openlocfilehash: 94c66267dfeec4b70ba4dd1fc47518eb0e01509a
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053575"
---
# <a name="telemetry-collection-by-the-mlnet-cli"></a><span data-ttu-id="2ddbe-104">Zbieranie danych telemetrycznych przez interfejs wiersza polecenia strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="2ddbe-104">Telemetry collection by the ML.NET CLI</span></span>

<span data-ttu-id="2ddbe-105">[Interfejsu wiersza polecenia w strukturze ML.NET](http://aka.ms/mlnet-cli) obejmuje funkcję dane telemetryczne, które zbiera anonimowe dane użycia zagregowanych do użycia przez firmę Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2ddbe-105">The [ML.NET CLI](http://aka.ms/mlnet-cli) includes a telemetry feature that collects anonymous usage data that is aggregated for use by Microsoft.</span></span>

## <a name="how-microsoft-uses-the-data"></a><span data-ttu-id="2ddbe-106">Jak firma Microsoft używa danych</span><span class="sxs-lookup"><span data-stu-id="2ddbe-106">How Microsoft uses the data</span></span>

<span data-ttu-id="2ddbe-107">Zespół pracujący nad produktem używa danych telemetrycznych interfejsu wiersza polecenia w strukturze ML.NET pomagające zrozumieć, jak poprawić narzędzia.</span><span class="sxs-lookup"><span data-stu-id="2ddbe-107">The product team uses ML.NET CLI telemetry data to help understand how to improve the tools.</span></span> <span data-ttu-id="2ddbe-108">Na przykład użycie klientów rzadko określonej usługi machine learning zadania, zespół pracujący nad produktem bada dlaczego i używa ustalenia, aby określić priorytety rozwój funkcji.</span><span class="sxs-lookup"><span data-stu-id="2ddbe-108">For example, if customers infrequently use a particular machine learning task, the product team investigates why and uses findings to prioritize feature development.</span></span> <span data-ttu-id="2ddbe-109">Interfejs wiersza polecenia w strukturze ML.NET telemetrii pomaga również debugowanie problemów, takich jak awarie i anomalii kodu.</span><span class="sxs-lookup"><span data-stu-id="2ddbe-109">ML.NET CLI telemetry also helps with debugging of issues such as crashes and code anomalies.</span></span> 

<span data-ttu-id="2ddbe-110">Gdy zespół pracujący nad produktem ocenia te szczegółowe informacje, wiemy również, że nie każdy chce wysyłać te dane.</span><span class="sxs-lookup"><span data-stu-id="2ddbe-110">While the product team appreciates this insight, we also know that not everyone wants to send this data.</span></span> [<span data-ttu-id="2ddbe-111">Dowiedz się, jak wyłączyć telemetrię.</span><span class="sxs-lookup"><span data-stu-id="2ddbe-111">Find out how to disable telemetry.</span></span>](#opt-out-of-data-collection)

## <a name="scope"></a><span data-ttu-id="2ddbe-112">Scope</span><span class="sxs-lookup"><span data-stu-id="2ddbe-112">Scope</span></span>

<span data-ttu-id="2ddbe-113">`mlnet` Polecenie uruchamia strukturze ML.NET interfejsu wiersza polecenia, ale samo polecenie nie zbiera dane telemetryczne.</span><span class="sxs-lookup"><span data-stu-id="2ddbe-113">The `mlnet` command launches the ML.NET CLI, but the command itself doesn't collect telemetry.</span></span>

<span data-ttu-id="2ddbe-114">Dane telemetryczne *nie włączono* po uruchomieniu `mlnet` polecenia żadne inne polecenie dołączone.</span><span class="sxs-lookup"><span data-stu-id="2ddbe-114">Telemetry *isn't enabled* when you run the `mlnet` command with no other command attached.</span></span> <span data-ttu-id="2ddbe-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="2ddbe-115">For example:</span></span>

- `mlnet`
- `mlnet --help`

<span data-ttu-id="2ddbe-116">Dane telemetryczne *włączono* po uruchomieniu [polecenia interfejsu wiersza polecenia w strukturze ML.NET](../reference/ml-net-cli-reference.md), takich jak `mlnet auto-train`.</span><span class="sxs-lookup"><span data-stu-id="2ddbe-116">Telemetry *is enabled* when you run an [ML.NET CLI command](../reference/ml-net-cli-reference.md), such as `mlnet auto-train`.</span></span>

## <a name="opt-out-of-data-collection"></a><span data-ttu-id="2ddbe-117">Zrezygnować ze zbierania danych</span><span class="sxs-lookup"><span data-stu-id="2ddbe-117">Opt out of data collection</span></span>

<span data-ttu-id="2ddbe-118">Funkcja telemetrii interfejsu wiersza polecenia w strukturze ML.NET jest włączona domyślnie.</span><span class="sxs-lookup"><span data-stu-id="2ddbe-118">The ML.NET CLI telemetry feature is enabled by default.</span></span>

<span data-ttu-id="2ddbe-119">Zrezygnować z funkcji danych telemetrycznych przez ustawienie `DOTNET_CLI_TELEMETRY_OPTOUT` zmiennej środowiskowej, aby `1` lub `true`.</span><span class="sxs-lookup"><span data-stu-id="2ddbe-119">Opt out of the telemetry feature by setting the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span> <span data-ttu-id="2ddbe-120">Ta zmienna środowiskowa globalnie stosuje się do narzędzia wiersza polecenia platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="2ddbe-120">This environment variable applies globally to the .NET CLI tool.</span></span>

## <a name="data-points-collected"></a><span data-ttu-id="2ddbe-121">Zebranych punktów danych</span><span class="sxs-lookup"><span data-stu-id="2ddbe-121">Data points collected</span></span>

<span data-ttu-id="2ddbe-122">Ta funkcja zbiera następujące dane:</span><span class="sxs-lookup"><span data-stu-id="2ddbe-122">The feature collects the following data:</span></span>

- <span data-ttu-id="2ddbe-123">Jakie polecenia została wywołana, takich jak `auto-train`</span><span class="sxs-lookup"><span data-stu-id="2ddbe-123">What command was invoked, such as `auto-train`</span></span>
- <span data-ttu-id="2ddbe-124">Nazwy parametrów wiersza polecenia używane (czyli "Nazwa zestawu danych, nazwę kolumny etykiety, zadania uczenia maszynowego, ścieżkę wyjściową, max eksploracji w czasie, poziom szczegółowości")</span><span class="sxs-lookup"><span data-stu-id="2ddbe-124">Command-line parameter names used (i.e. "dataset-name, label-column-name, ml-task, output-path, max-exploration-time, verbosity")</span></span>
- <span data-ttu-id="2ddbe-125">Mieszana adres MAC: kryptograficznie (SHA256) anonimowe i unikatowy identyfikator dla maszyny</span><span class="sxs-lookup"><span data-stu-id="2ddbe-125">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine</span></span>
- <span data-ttu-id="2ddbe-126">Sygnatura czasowa wywołania</span><span class="sxs-lookup"><span data-stu-id="2ddbe-126">Timestamp of an invocation</span></span>
- <span data-ttu-id="2ddbe-127">Trzy octet adres IP (nie pełnemu) używane tylko w celu określenia lokalizacji geograficznej</span><span class="sxs-lookup"><span data-stu-id="2ddbe-127">Three octet IP address (not full IP address) used only to determine geographical location</span></span>
- <span data-ttu-id="2ddbe-128">Nazwy wszystkich argumentów/parametry używane.</span><span class="sxs-lookup"><span data-stu-id="2ddbe-128">Name of all arguments/parameters used.</span></span> <span data-ttu-id="2ddbe-129">Nie odbiorcy wartości, takich jak ciągi</span><span class="sxs-lookup"><span data-stu-id="2ddbe-129">Not the customer's values, such as strings</span></span>
- <span data-ttu-id="2ddbe-130">Nazwa zestawu danych w formie skrótu pliku</span><span class="sxs-lookup"><span data-stu-id="2ddbe-130">Hashed dataset filename</span></span>
- <span data-ttu-id="2ddbe-131">Przedział rozmiaru pliku zestawu danych</span><span class="sxs-lookup"><span data-stu-id="2ddbe-131">Dataset file-size bucket</span></span>
- <span data-ttu-id="2ddbe-132">Wersja systemu operacyjnego i</span><span class="sxs-lookup"><span data-stu-id="2ddbe-132">Operating system and version</span></span>
- <span data-ttu-id="2ddbe-133">Wartość parametru--zadań: Podzielone wartości, takich jak `regression`, `binary-classification`, i `multiclass-classification`</span><span class="sxs-lookup"><span data-stu-id="2ddbe-133">Value of --task parameter: Categorical values, such as `regression`, `binary-classification`, and `multiclass-classification`</span></span>
- <span data-ttu-id="2ddbe-134">Wersja interfejsu wiersza polecenia w strukturze ML.NET (tj. 0.3.27703.4)</span><span class="sxs-lookup"><span data-stu-id="2ddbe-134">ML.NET CLI version (i.e. 0.3.27703.4)</span></span>

<span data-ttu-id="2ddbe-135">Dane są przesyłane w bezpieczny sposób do serwerów firmy Microsoft przy użyciu [usługi Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technologii, przechowywane w obszarze ograniczony dostęp i używane w ramach rygorystyczne kontrole zabezpieczeń z bezpiecznym [usługi Azure Storage](https://azure.microsoft.com/services/storage/) systemów.</span><span class="sxs-lookup"><span data-stu-id="2ddbe-135">The data is sent securely to Microsoft servers using [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and used under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

### <a name="data-points-not-collected"></a><span data-ttu-id="2ddbe-136">Nie zebrano punktów danych</span><span class="sxs-lookup"><span data-stu-id="2ddbe-136">Data points not collected</span></span>
<span data-ttu-id="2ddbe-137">Funkcja telemetrii *nie* zbierania:</span><span class="sxs-lookup"><span data-stu-id="2ddbe-137">The telemetry feature *doesn't* collect:</span></span>
- <span data-ttu-id="2ddbe-138">dane osobowe, takich jak nazwy użytkowników</span><span class="sxs-lookup"><span data-stu-id="2ddbe-138">personal data, such as usernames</span></span>
- <span data-ttu-id="2ddbe-139">nazwy plików zestawu danych</span><span class="sxs-lookup"><span data-stu-id="2ddbe-139">dataset filenames</span></span>
- <span data-ttu-id="2ddbe-140">dane z plików zestawu danych</span><span class="sxs-lookup"><span data-stu-id="2ddbe-140">data from dataset files</span></span>

<span data-ttu-id="2ddbe-141">Jeśli podejrzewasz, że zbiera dane telemetryczne interfejsu wiersza polecenia w strukturze ML.NET poufne dane, lub że dane są insecurely lub niewłaściwie obsługiwane, Prześlij zgłoszenie do [strukturze ML.NET](https://github.com/dotnet/machinelearning) repozytorium na potrzeby badania.</span><span class="sxs-lookup"><span data-stu-id="2ddbe-141">If you suspect that the ML.NET CLI telemetry is collecting sensitive data or that the data is being insecurely or inappropriately handled, file an issue in the [ML.NET](https://github.com/dotnet/machinelearning) repository for investigation.</span></span>

## <a name="license"></a><span data-ttu-id="2ddbe-142">Licencja</span><span class="sxs-lookup"><span data-stu-id="2ddbe-142">License</span></span>

<span data-ttu-id="2ddbe-143">Dystrybucja Microsoft interfejsu wiersza polecenia w strukturze ML.NET ma licencję za pomocą [postanowienia licencyjne dotyczące oprogramowania firmy Microsoft: Microsoft .NET Library](https://aka.ms/dotnet-core-eula).</span><span class="sxs-lookup"><span data-stu-id="2ddbe-143">The Microsoft distribution of ML.NET CLI is licensed with the [Microsoft Software License Terms: Microsoft .NET Library](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="2ddbe-144">Aby uzyskać szczegółowe informacje dotyczące zbierania i przetwarzania danych zobacz sekcję zatytułowaną "Dane".</span><span class="sxs-lookup"><span data-stu-id="2ddbe-144">For details on data collection and processing, see the section entitled "Data."</span></span>

## <a name="disclosure"></a><span data-ttu-id="2ddbe-145">Ujawnienie</span><span class="sxs-lookup"><span data-stu-id="2ddbe-145">Disclosure</span></span>

<span data-ttu-id="2ddbe-146">Przy pierwszym uruchomieniu [polecenia interfejsu wiersza polecenia w strukturze ML.NET](../reference/ml-net-cli-reference.md) takich jak `mlnet auto-train`, narzędzia interfejsu wiersza polecenia w strukturze ML.NET Wyświetla tekst ujawnienie, który informuje, jak zrezygnować z danych telemetrycznych.</span><span class="sxs-lookup"><span data-stu-id="2ddbe-146">When you first run a [ML.NET CLI command](../reference/ml-net-cli-reference.md) such as `mlnet auto-train`, the ML.NET CLI tool displays disclosure text that tells you how to opt out of telemetry.</span></span> <span data-ttu-id="2ddbe-147">Tekst może się nieco różnić w zależności od wersji korzystasz z interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="2ddbe-147">Text may vary slightly depending on the version of the CLI you're running.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ddbe-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ddbe-148">See also</span></span>
- [<span data-ttu-id="2ddbe-149">Dokumentacja interfejsu wiersza polecenia w strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="2ddbe-149">ML.NET CLI reference</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="2ddbe-150">Postanowienia licencyjne dotyczące oprogramowania firmy Microsoft: Microsoft .NET Library</span><span class="sxs-lookup"><span data-stu-id="2ddbe-150">Microsoft Software License Terms: Microsoft .NET Library</span></span>](https://aka.ms/dotnet-core-eula)
- [<span data-ttu-id="2ddbe-151">Ochrona prywatności w firmie Microsoft</span><span class="sxs-lookup"><span data-stu-id="2ddbe-151">Privacy at Microsoft</span></span>](https://www.microsoft.com/trustcenter/privacy/)
- [<span data-ttu-id="2ddbe-152">Poufności informacji firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="2ddbe-152">Microsoft Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
