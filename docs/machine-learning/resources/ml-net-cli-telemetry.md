---
title: Zbieranie danych telemetrycznych przez interfejs wiersza polecenia w strukturze ML.NET
description: Dowiedz się więcej o funkcje telemetrii strukturze ML.NET interfejsu wiersza polecenia, które zbierają użycia informacje do analizy danych, które są zbierane i jak go wyłączyć. Ponadto Znajdź łącza do umowy licencyjnej .NET i informacje o zgodności z GDPR firmy Microsoft.
ms.topic: conceptual
ms.date: 05/05/2019
ms.custom: ''
ms.openlocfilehash: 49ebd6c9e1b77c85d891b8c9fb8cbd5c66b478a9
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65066158"
---
# <a name="telemetry-collection-by-the-mlnet-cli"></a><span data-ttu-id="cd632-104">Zbieranie danych telemetrycznych przez interfejs wiersza polecenia strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="cd632-104">Telemetry collection by the ML.NET CLI</span></span>

<span data-ttu-id="cd632-105">[Interfejsu wiersza polecenia w strukturze ML.NET](http://aka.ms/mlnet-cli) obejmuje funkcję dane telemetryczne, które zbiera anonimowe dane użycia zagregowanych do użycia przez firmę Microsoft.</span><span class="sxs-lookup"><span data-stu-id="cd632-105">The [ML.NET CLI](http://aka.ms/mlnet-cli) includes a telemetry feature that collects anonymous usage data that is aggregated for use by Microsoft.</span></span>

## <a name="how-microsoft-uses-the-data"></a><span data-ttu-id="cd632-106">Jak firma Microsoft używa danych</span><span class="sxs-lookup"><span data-stu-id="cd632-106">How Microsoft uses the data</span></span>

<span data-ttu-id="cd632-107">Zespół pracujący nad produktem używa danych telemetrycznych interfejsu wiersza polecenia w strukturze ML.NET pomagające zrozumieć, jak poprawić narzędzia.</span><span class="sxs-lookup"><span data-stu-id="cd632-107">The product team uses ML.NET CLI telemetry data to help understand how to improve the tools.</span></span> <span data-ttu-id="cd632-108">Na przykład użycie klientów rzadko określonej usługi machine learning zadania, zespół pracujący nad produktem bada dlaczego i używa ustalenia, aby określić priorytety rozwój funkcji.</span><span class="sxs-lookup"><span data-stu-id="cd632-108">For example, if customers infrequently use a particular machine learning task, the product team investigates why and uses findings to prioritize feature development.</span></span> <span data-ttu-id="cd632-109">Interfejs wiersza polecenia w strukturze ML.NET telemetrii pomaga również debugowanie problemów, takich jak awarie i anomalii kodu.</span><span class="sxs-lookup"><span data-stu-id="cd632-109">ML.NET CLI telemetry also helps with debugging of issues such as crashes and code anomalies.</span></span> 

<span data-ttu-id="cd632-110">Gdy zespół pracujący nad produktem ocenia te szczegółowe informacje, wiemy również, że nie każdy chce wysyłać te dane.</span><span class="sxs-lookup"><span data-stu-id="cd632-110">While the product team appreciates this insight, we also know that not everyone wants to send this data.</span></span> [<span data-ttu-id="cd632-111">Dowiedz się, jak wyłączyć telemetrię.</span><span class="sxs-lookup"><span data-stu-id="cd632-111">Find out how to disable telemetry.</span></span>](#opt-out-of-data-collection)

## <a name="scope"></a><span data-ttu-id="cd632-112">Scope</span><span class="sxs-lookup"><span data-stu-id="cd632-112">Scope</span></span>

<span data-ttu-id="cd632-113">`mlnet` Polecenie uruchamia strukturze ML.NET interfejsu wiersza polecenia, ale samo polecenie nie zbiera dane telemetryczne.</span><span class="sxs-lookup"><span data-stu-id="cd632-113">The `mlnet` command launches the ML.NET CLI, but the command itself doesn't collect telemetry.</span></span>

<span data-ttu-id="cd632-114">Dane telemetryczne *nie włączono* po uruchomieniu `mlnet` polecenia żadne inne polecenie dołączone.</span><span class="sxs-lookup"><span data-stu-id="cd632-114">Telemetry *isn't enabled* when you run the `mlnet` command with no other command attached.</span></span> <span data-ttu-id="cd632-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="cd632-115">For example:</span></span>

- `mlnet`
- `mlnet --help`

<span data-ttu-id="cd632-116">Dane telemetryczne *włączono* po uruchomieniu [polecenia interfejsu wiersza polecenia w strukturze ML.NET](../reference/ml-net-cli-reference.md), takich jak `mlnet auto-train`.</span><span class="sxs-lookup"><span data-stu-id="cd632-116">Telemetry *is enabled* when you run an [ML.NET CLI command](../reference/ml-net-cli-reference.md), such as `mlnet auto-train`.</span></span>

## <a name="opt-out-of-data-collection"></a><span data-ttu-id="cd632-117">Zrezygnować ze zbierania danych</span><span class="sxs-lookup"><span data-stu-id="cd632-117">Opt out of data collection</span></span>

<span data-ttu-id="cd632-118">Funkcja telemetrii interfejsu wiersza polecenia w strukturze ML.NET jest włączona domyślnie.</span><span class="sxs-lookup"><span data-stu-id="cd632-118">The ML.NET CLI telemetry feature is enabled by default.</span></span>

<span data-ttu-id="cd632-119">Zrezygnować z funkcji danych telemetrycznych przez ustawienie `DOTNET_CLI_TELEMETRY_OPTOUT` zmiennej środowiskowej, aby `1` lub `true`.</span><span class="sxs-lookup"><span data-stu-id="cd632-119">Opt out of the telemetry feature by setting the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span> <span data-ttu-id="cd632-120">Ta zmienna środowiskowa globalnie stosuje się do narzędzia wiersza polecenia platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="cd632-120">This environment variable applies globally to the .NET CLI tool.</span></span>

## <a name="data-points-collected"></a><span data-ttu-id="cd632-121">Zebranych punktów danych</span><span class="sxs-lookup"><span data-stu-id="cd632-121">Data points collected</span></span>

<span data-ttu-id="cd632-122">Ta funkcja zbiera następujące dane:</span><span class="sxs-lookup"><span data-stu-id="cd632-122">The feature collects the following data:</span></span>

- <span data-ttu-id="cd632-123">Polecenia, które są wywoływane, takich jak `auto-train`</span><span class="sxs-lookup"><span data-stu-id="cd632-123">Which commands are invoked, such as `auto-train`</span></span>
- <span data-ttu-id="cd632-124">Mieszana adres MAC: kryptograficznie (SHA256) anonimowe i unikatowy identyfikator dla maszyny</span><span class="sxs-lookup"><span data-stu-id="cd632-124">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine</span></span>
- <span data-ttu-id="cd632-125">Sygnatura czasowa wywołania</span><span class="sxs-lookup"><span data-stu-id="cd632-125">Timestamp of an invocation</span></span>
- <span data-ttu-id="cd632-126">Trzy octet adres IP używany tylko w celu określenia lokalizacji geograficznej</span><span class="sxs-lookup"><span data-stu-id="cd632-126">Three octet IP address used only to determine geographical location</span></span>
- <span data-ttu-id="cd632-127">Nazwy wszystkich argumentów/parametry używane.</span><span class="sxs-lookup"><span data-stu-id="cd632-127">Name of all arguments/parameters used.</span></span> <span data-ttu-id="cd632-128">Nie odbiorcy wartości, takich jak ciągi</span><span class="sxs-lookup"><span data-stu-id="cd632-128">Not the customer's values, such as strings</span></span>
- <span data-ttu-id="cd632-129">Wersja systemu operacyjnego i</span><span class="sxs-lookup"><span data-stu-id="cd632-129">Operating system and version</span></span>
- <span data-ttu-id="cd632-130">Wartość parametru--ml zadania: Podzielone wartości, takich jak `regression`, `binary-classification`, i `multiclass-classification`</span><span class="sxs-lookup"><span data-stu-id="cd632-130">Value of --ml-task parameter: Categorical values, such as `regression`, `binary-classification`, and `multiclass-classification`</span></span>
- <span data-ttu-id="cd632-131">[Skala logarytmiczna zaokrąglone](https://en.wikipedia.org/wiki/Rounding#Rounding_to_a_specified_power) rozmiar pliku zestawu danych (najbliższym potęgą liczby 2)</span><span class="sxs-lookup"><span data-stu-id="cd632-131">[Logarithmic rounded](https://en.wikipedia.org/wiki/Rounding#Rounding_to_a_specified_power) dataset file size (nearest power of 2)</span></span>
- <span data-ttu-id="cd632-132">`ExitCode` polecenia</span><span class="sxs-lookup"><span data-stu-id="cd632-132">`ExitCode` of the command</span></span>

<span data-ttu-id="cd632-133">Dane są przesyłane w bezpieczny sposób do serwerów firmy Microsoft przy użyciu [usługi Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technologii, przechowywane w obszarze ograniczony dostęp i używane w ramach rygorystyczne kontrole zabezpieczeń z bezpiecznym [usługi Azure Storage](https://azure.microsoft.com/services/storage/) systemów.</span><span class="sxs-lookup"><span data-stu-id="cd632-133">The data is sent securely to Microsoft servers using [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and used under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

### <a name="data-points-not-collected"></a><span data-ttu-id="cd632-134">Nie zebrano punktów danych</span><span class="sxs-lookup"><span data-stu-id="cd632-134">Data points not collected</span></span>
<span data-ttu-id="cd632-135">Funkcja telemetrii *nie* zbierania:</span><span class="sxs-lookup"><span data-stu-id="cd632-135">The telemetry feature *doesn't* collect:</span></span>
- <span data-ttu-id="cd632-136">dane osobowe, takich jak nazwy użytkowników</span><span class="sxs-lookup"><span data-stu-id="cd632-136">personal data, such as usernames</span></span>
- <span data-ttu-id="cd632-137">nazwy plików zestawu danych</span><span class="sxs-lookup"><span data-stu-id="cd632-137">dataset filenames</span></span>
- <span data-ttu-id="cd632-138">dane z plików zestawu danych</span><span class="sxs-lookup"><span data-stu-id="cd632-138">data from dataset files</span></span>

<span data-ttu-id="cd632-139">Jeśli podejrzewasz, że zbiera dane telemetryczne interfejsu wiersza polecenia w strukturze ML.NET poufne dane, lub że dane są insecurely lub niewłaściwie obsługiwane, Prześlij zgłoszenie do [strukturze ML.NET](https://github.com/dotnet/machinelearning) repozytorium na potrzeby badania.</span><span class="sxs-lookup"><span data-stu-id="cd632-139">If you suspect that the ML.NET CLI telemetry is collecting sensitive data or that the data is being insecurely or inappropriately handled, file an issue in the [ML.NET](https://github.com/dotnet/machinelearning) repository for investigation.</span></span>

## <a name="license"></a><span data-ttu-id="cd632-140">Licencja</span><span class="sxs-lookup"><span data-stu-id="cd632-140">License</span></span>

<span data-ttu-id="cd632-141">Dystrybucja Microsoft interfejsu wiersza polecenia w strukturze ML.NET ma licencję za pomocą [postanowienia licencyjne dotyczące oprogramowania firmy Microsoft: Microsoft .NET Library](https://aka.ms/dotnet-core-eula).</span><span class="sxs-lookup"><span data-stu-id="cd632-141">The Microsoft distribution of ML.NET CLI is licensed with the [Microsoft Software License Terms: Microsoft .NET Library](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="cd632-142">Aby uzyskać szczegółowe informacje dotyczące zbierania i przetwarzania danych zobacz sekcję zatytułowaną "Dane".</span><span class="sxs-lookup"><span data-stu-id="cd632-142">For details on data collection and processing, see the section entitled "Data."</span></span>

## <a name="disclosure"></a><span data-ttu-id="cd632-143">Ujawnienie</span><span class="sxs-lookup"><span data-stu-id="cd632-143">Disclosure</span></span>

<span data-ttu-id="cd632-144">Przy pierwszym uruchomieniu [polecenia interfejsu wiersza polecenia w strukturze ML.NET](../reference/ml-net-cli-reference.md) takich jak `mlnet auto-train`, narzędzia interfejsu wiersza polecenia w strukturze ML.NET Wyświetla tekst ujawnienie, który informuje, jak zrezygnować z danych telemetrycznych.</span><span class="sxs-lookup"><span data-stu-id="cd632-144">When you first run a [ML.NET CLI command](../reference/ml-net-cli-reference.md) such as `mlnet auto-train`, the ML.NET CLI tool displays disclosure text that tells you how to opt out of telemetry.</span></span> <span data-ttu-id="cd632-145">Tekst może się nieco różnić w zależności od wersji korzystasz z interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="cd632-145">Text may vary slightly depending on the version of the CLI you're running.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd632-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd632-146">See also</span></span>
- [<span data-ttu-id="cd632-147">Dokumentacja interfejsu wiersza polecenia w strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="cd632-147">ML.NET CLI reference</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="cd632-148">Postanowienia licencyjne dotyczące oprogramowania firmy Microsoft: Microsoft .NET Library</span><span class="sxs-lookup"><span data-stu-id="cd632-148">Microsoft Software License Terms: Microsoft .NET Library</span></span>](https://aka.ms/dotnet-core-eula)
- [<span data-ttu-id="cd632-149">Ochrona prywatności w firmie Microsoft</span><span class="sxs-lookup"><span data-stu-id="cd632-149">Privacy at Microsoft</span></span>](https://www.microsoft.com/en-us/trustcenter/privacy/)
- [<span data-ttu-id="cd632-150">Poufności informacji firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="cd632-150">Microsoft Privacy Statement</span></span>](https://privacy.microsoft.com/en-us/privacystatement)
