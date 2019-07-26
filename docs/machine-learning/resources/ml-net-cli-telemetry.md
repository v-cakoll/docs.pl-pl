---
title: Zbieranie danych telemetrycznych za pomocą interfejsu wiersza polecenia ML.NET
description: Dowiedz się więcej o funkcjach telemetrycznych interfejsu wiersza polecenia ML.NET, które zbierają informacje o użyciu do analizy, zbierane dane i jak je wyłączyć. Znajdź także linki do umowy licencyjnej platformy .NET oraz informacje o zgodności z programem Microsoft Rodo.
ms.topic: conceptual
ms.date: 05/05/2019
ms.custom: ''
ms.openlocfilehash: eab1e37d7d0d47251c4f92422730b105cf2db265
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433793"
---
# <a name="telemetry-collection-by-the-mlnet-cli"></a><span data-ttu-id="e82bc-104">Zbieranie danych telemetrycznych za pomocą interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="e82bc-104">Telemetry collection by the ML.NET CLI</span></span>

<span data-ttu-id="e82bc-105">[Interfejs wiersza polecenia ml.NET](https://aka.ms/mlnet-cli) zawiera funkcję telemetrii, która zbiera anonimowe dane użycia, które są agregowane na użytek firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e82bc-105">The [ML.NET CLI](https://aka.ms/mlnet-cli) includes a telemetry feature that collects anonymous usage data that is aggregated for use by Microsoft.</span></span>

## <a name="how-microsoft-uses-the-data"></a><span data-ttu-id="e82bc-106">Jak firma Microsoft używa danych</span><span class="sxs-lookup"><span data-stu-id="e82bc-106">How Microsoft uses the data</span></span>

<span data-ttu-id="e82bc-107">Zespół produktu używa danych telemetrycznych interfejsu wiersza polecenia ML.NET, aby pomóc zrozumieć, jak ulepszyć narzędzia.</span><span class="sxs-lookup"><span data-stu-id="e82bc-107">The product team uses ML.NET CLI telemetry data to help understand how to improve the tools.</span></span> <span data-ttu-id="e82bc-108">Na przykład jeśli klienci rzadko wykorzystują określone zadanie uczenia maszynowego, zespół produktu bada dlaczego i korzysta z wyników, aby określić priorytety projektowania funkcji.</span><span class="sxs-lookup"><span data-stu-id="e82bc-108">For example, if customers infrequently use a particular machine learning task, the product team investigates why and uses findings to prioritize feature development.</span></span> <span data-ttu-id="e82bc-109">Dane telemetryczne interfejsu wiersza polecenia ML.NET pomagają również debugować problemy, takie jak awarie i anomalie w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e82bc-109">ML.NET CLI telemetry also helps with debugging of issues such as crashes and code anomalies.</span></span> 

<span data-ttu-id="e82bc-110">Gdy zespół produktu docenia ten wgląd, wie również, że nie wszyscy chcą wysyłać te dane.</span><span class="sxs-lookup"><span data-stu-id="e82bc-110">While the product team appreciates this insight, we also know that not everyone wants to send this data.</span></span> [<span data-ttu-id="e82bc-111">Dowiedz się, jak wyłączyć telemetrię.</span><span class="sxs-lookup"><span data-stu-id="e82bc-111">Find out how to disable telemetry.</span></span>](#opt-out-of-data-collection)

## <a name="scope"></a><span data-ttu-id="e82bc-112">Scope</span><span class="sxs-lookup"><span data-stu-id="e82bc-112">Scope</span></span>

<span data-ttu-id="e82bc-113">`mlnet` Polecenie uruchamia interfejs wiersza polecenia ml.NET, ale samo polecenie nie zbiera danych telemetrycznych.</span><span class="sxs-lookup"><span data-stu-id="e82bc-113">The `mlnet` command launches the ML.NET CLI, but the command itself doesn't collect telemetry.</span></span>

<span data-ttu-id="e82bc-114">Funkcja telemetrii *nie jest włączona* po uruchomieniu `mlnet` polecenia bez innego dołączonego polecenia.</span><span class="sxs-lookup"><span data-stu-id="e82bc-114">Telemetry *isn't enabled* when you run the `mlnet` command with no other command attached.</span></span> <span data-ttu-id="e82bc-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="e82bc-115">For example:</span></span>

- `mlnet`
- `mlnet --help`

<span data-ttu-id="e82bc-116">Funkcja telemetrii *jest włączona* po uruchomieniu [polecenia ml.NET CLI](../reference/ml-net-cli-reference.md), takiego `mlnet auto-train`jak.</span><span class="sxs-lookup"><span data-stu-id="e82bc-116">Telemetry *is enabled* when you run an [ML.NET CLI command](../reference/ml-net-cli-reference.md), such as `mlnet auto-train`.</span></span>

## <a name="opt-out-of-data-collection"></a><span data-ttu-id="e82bc-117">Rezygnacja z zbierania danych</span><span class="sxs-lookup"><span data-stu-id="e82bc-117">Opt out of data collection</span></span>

<span data-ttu-id="e82bc-118">Funkcja telemetrii interfejsu wiersza polecenia ML.NET jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="e82bc-118">The ML.NET CLI telemetry feature is enabled by default.</span></span>

<span data-ttu-id="e82bc-119">Rezygnacja z funkcji telemetrii przez ustawienie `DOTNET_CLI_TELEMETRY_OPTOUT` zmiennej środowiskowej `1` na `true`lub.</span><span class="sxs-lookup"><span data-stu-id="e82bc-119">Opt out of the telemetry feature by setting the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span> <span data-ttu-id="e82bc-120">Ta zmienna środowiskowa jest stosowana globalnie do narzędzia interfejsu wiersza polecenia platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="e82bc-120">This environment variable applies globally to the .NET CLI tool.</span></span>

## <a name="data-points-collected"></a><span data-ttu-id="e82bc-121">Zebrane punkty danych</span><span class="sxs-lookup"><span data-stu-id="e82bc-121">Data points collected</span></span>

<span data-ttu-id="e82bc-122">Funkcja zbiera następujące dane:</span><span class="sxs-lookup"><span data-stu-id="e82bc-122">The feature collects the following data:</span></span>

- <span data-ttu-id="e82bc-123">Jakie polecenie zostało wywołane, na przykład`auto-train`</span><span class="sxs-lookup"><span data-stu-id="e82bc-123">What command was invoked, such as `auto-train`</span></span>
- <span data-ttu-id="e82bc-124">Używane nazwy parametrów wiersza polecenia (tj. "DataSet-Name, Label-column-name, ml-Task, Output-Path, Max-Learning-Time, szczegółowości")</span><span class="sxs-lookup"><span data-stu-id="e82bc-124">Command-line parameter names used (i.e. "dataset-name, label-column-name, ml-task, output-path, max-exploration-time, verbosity")</span></span>
- <span data-ttu-id="e82bc-125">Skrótowy adres MAC: kryptograficzny (SHA256) anonimowy i unikatowy identyfikator dla komputera</span><span class="sxs-lookup"><span data-stu-id="e82bc-125">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine</span></span>
- <span data-ttu-id="e82bc-126">Sygnatura czasowa wywołania</span><span class="sxs-lookup"><span data-stu-id="e82bc-126">Timestamp of an invocation</span></span>
- <span data-ttu-id="e82bc-127">Trzy oktetowe adresy IP (nie pełny adres IP) używane tylko do określania lokalizacji geograficznej</span><span class="sxs-lookup"><span data-stu-id="e82bc-127">Three octet IP address (not full IP address) used only to determine geographical location</span></span>
- <span data-ttu-id="e82bc-128">Nazwa wszystkich używanych argumentów/parametrów.</span><span class="sxs-lookup"><span data-stu-id="e82bc-128">Name of all arguments/parameters used.</span></span> <span data-ttu-id="e82bc-129">Nie wartości klienta, takie jak ciągi</span><span class="sxs-lookup"><span data-stu-id="e82bc-129">Not the customer's values, such as strings</span></span>
- <span data-ttu-id="e82bc-130">Nazwa pliku zestawu danych skrótów</span><span class="sxs-lookup"><span data-stu-id="e82bc-130">Hashed dataset filename</span></span>
- <span data-ttu-id="e82bc-131">Zasobnik rozmiaru pliku zestawu danych</span><span class="sxs-lookup"><span data-stu-id="e82bc-131">Dataset file-size bucket</span></span>
- <span data-ttu-id="e82bc-132">System operacyjny i wersja</span><span class="sxs-lookup"><span data-stu-id="e82bc-132">Operating system and version</span></span>
- <span data-ttu-id="e82bc-133">Wartość--parametru zadania: Kategorii wartości, takie jak `regression`, `binary-classification`i`multiclass-classification`</span><span class="sxs-lookup"><span data-stu-id="e82bc-133">Value of --task parameter: Categorical values, such as `regression`, `binary-classification`, and `multiclass-classification`</span></span>
- <span data-ttu-id="e82bc-134">Wersja interfejsu wiersza polecenia ML.NET (np. 0.3.27703.4)</span><span class="sxs-lookup"><span data-stu-id="e82bc-134">ML.NET CLI version (i.e. 0.3.27703.4)</span></span>

<span data-ttu-id="e82bc-135">Dane są bezpiecznie przesyłane do serwerów firmy Microsoft przy użyciu technologii [Application Insights platformy Azure](https://azure.microsoft.com/services/application-insights/) , w ramach ograniczonego dostępu i stosowane w ramach ścisłej kontroli zabezpieczeń z bezpiecznych systemów [usługi Azure Storage](https://azure.microsoft.com/services/storage/) .</span><span class="sxs-lookup"><span data-stu-id="e82bc-135">The data is sent securely to Microsoft servers using [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and used under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

### <a name="data-points-not-collected"></a><span data-ttu-id="e82bc-136">Punkty danych nie są zbierane</span><span class="sxs-lookup"><span data-stu-id="e82bc-136">Data points not collected</span></span>
<span data-ttu-id="e82bc-137">Funkcja telemetrii *nie* zbiera:</span><span class="sxs-lookup"><span data-stu-id="e82bc-137">The telemetry feature *doesn't* collect:</span></span>
- <span data-ttu-id="e82bc-138">dane osobowe, takie jak nazwy użytkowników</span><span class="sxs-lookup"><span data-stu-id="e82bc-138">personal data, such as usernames</span></span>
- <span data-ttu-id="e82bc-139">nazwy plików DataSet</span><span class="sxs-lookup"><span data-stu-id="e82bc-139">dataset filenames</span></span>
- <span data-ttu-id="e82bc-140">dane z plików DataSet</span><span class="sxs-lookup"><span data-stu-id="e82bc-140">data from dataset files</span></span>

<span data-ttu-id="e82bc-141">Jeśli podejrzewasz, że Telemetria interfejsu wiersza polecenia ML.NET zbiera poufne dane lub że dane są w sposób niezabezpieczony lub niewłaściwie obsłużony, należy rozwiązać problem w repozytorium [ml.NET](https://github.com/dotnet/machinelearning) w celu zbadania.</span><span class="sxs-lookup"><span data-stu-id="e82bc-141">If you suspect that the ML.NET CLI telemetry is collecting sensitive data or that the data is being insecurely or inappropriately handled, file an issue in the [ML.NET](https://github.com/dotnet/machinelearning) repository for investigation.</span></span>

## <a name="license"></a><span data-ttu-id="e82bc-142">Licencja</span><span class="sxs-lookup"><span data-stu-id="e82bc-142">License</span></span>

<span data-ttu-id="e82bc-143">ML.NET interfejs wiersza polecenia firmy Microsoft do dystrybucji jest licencjonowany za pomocą [postanowień licencyjnych dotyczących oprogramowania firmy Microsoft: Biblioteka](https://aka.ms/dotnet-core-eula)Microsoft .NET.</span><span class="sxs-lookup"><span data-stu-id="e82bc-143">The Microsoft distribution of ML.NET CLI is licensed with the [Microsoft Software License Terms: Microsoft .NET Library](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="e82bc-144">Aby uzyskać szczegółowe informacje na temat zbierania i przetwarzania danych, zobacz sekcję zatytułowaną "dane".</span><span class="sxs-lookup"><span data-stu-id="e82bc-144">For details on data collection and processing, see the section entitled "Data."</span></span>

## <a name="disclosure"></a><span data-ttu-id="e82bc-145">Mogąc</span><span class="sxs-lookup"><span data-stu-id="e82bc-145">Disclosure</span></span>

<span data-ttu-id="e82bc-146">Gdy po raz pierwszy uruchomisz [polecenie interfejsu wiersza polecenia ml.NET](../reference/ml-net-cli-reference.md) , takie jak `mlnet auto-train`, narzędzie ml.NET CLI wyświetla tekst, który informuje, jak zrezygnować z telemetrii.</span><span class="sxs-lookup"><span data-stu-id="e82bc-146">When you first run a [ML.NET CLI command](../reference/ml-net-cli-reference.md) such as `mlnet auto-train`, the ML.NET CLI tool displays disclosure text that tells you how to opt out of telemetry.</span></span> <span data-ttu-id="e82bc-147">Tekst może się nieco różnić w zależności od używanej wersji interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="e82bc-147">Text may vary slightly depending on the version of the CLI you're running.</span></span>

## <a name="see-also"></a><span data-ttu-id="e82bc-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e82bc-148">See also</span></span>
- [<span data-ttu-id="e82bc-149">Dokumentacja interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="e82bc-149">ML.NET CLI reference</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="e82bc-150">Postanowienia licencyjne dotyczące oprogramowania firmy Microsoft: Biblioteka Microsoft .NET</span><span class="sxs-lookup"><span data-stu-id="e82bc-150">Microsoft Software License Terms: Microsoft .NET Library</span></span>](https://aka.ms/dotnet-core-eula)
- [<span data-ttu-id="e82bc-151">Prywatność w firmie Microsoft</span><span class="sxs-lookup"><span data-stu-id="e82bc-151">Privacy at Microsoft</span></span>](https://www.microsoft.com/trustcenter/privacy/)
- [<span data-ttu-id="e82bc-152">Zasady zachowania poufności informacji firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="e82bc-152">Microsoft Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
