---
title: Wdrażanie modelu w ASP.NET podstawowego interfejsu API sieci Web
description: Obsługiwać ML.NET model uczenia maszynowego analizy tonacji przez Internet za pomocą ASP.NET Core Web API
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: b6801b7de5a17257be706f77a7a67aa87df96524
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79398931"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a><span data-ttu-id="4ab1e-103">Wdrażanie modelu w ASP.NET podstawowego interfejsu API sieci Web</span><span class="sxs-lookup"><span data-stu-id="4ab1e-103">Deploy a model in an ASP.NET Core Web API</span></span>

<span data-ttu-id="4ab1e-104">Dowiedz się, jak obsługiwać wstępnie przeszkolony ML.NET model uczenia maszynowego w sieci Web przy użyciu interfejsu ASP.NET Core Web API.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-104">Learn how to serve a pre-trained ML.NET machine learning model on the web using an ASP.NET Core Web API.</span></span> <span data-ttu-id="4ab1e-105">Obsługujących modelu za pośrednictwem interfejsu API sieci web umożliwia prognozowania za pośrednictwem standardowych metod HTTP.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-105">Serving a model over a web API enables predictions via standard HTTP methods.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4ab1e-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="4ab1e-106">Prerequisites</span></span>

- <span data-ttu-id="4ab1e-107">[Visual Studio 2017 w wersji 15.6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem ".NET Core programistorna wieloplatformowa".</span><span class="sxs-lookup"><span data-stu-id="4ab1e-107">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- <span data-ttu-id="4ab1e-108">Powershell.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-108">Powershell.</span></span>
- <span data-ttu-id="4ab1e-109">Wstępnie przeszkolony model.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-109">Pre-trained model.</span></span> <span data-ttu-id="4ab1e-110">Użyj [samouczka ML.NET analiza nastrojów,](../tutorials/sentiment-analysis.md) aby zbudować własny model lub pobrać ten [wstępnie przeszkolony model uczenia maszynowego analizy tonacji](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="4ab1e-110">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-aspnet-core-web-api-project"></a><span data-ttu-id="4ab1e-111">Tworzenie ASP.NET projektu podstawowego interfejsu API sieci Web</span><span class="sxs-lookup"><span data-stu-id="4ab1e-111">Create ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="4ab1e-112">Otwórz program Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-112">Open Visual Studio 2017.</span></span> <span data-ttu-id="4ab1e-113">Z paska menu wybierz **pozycję Plik > Nowy projekt >.**</span><span class="sxs-lookup"><span data-stu-id="4ab1e-113">Select **File > New > Project** from the menu bar.</span></span> <span data-ttu-id="4ab1e-114">W oknie dialogowym Nowy projekt wybierz węzeł **Visual C#,** po którym następuje węzeł **sieci Web.**</span><span class="sxs-lookup"><span data-stu-id="4ab1e-114">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="4ab1e-115">Następnie wybierz szablon projektu **ASP.NET Core Web Application.**</span><span class="sxs-lookup"><span data-stu-id="4ab1e-115">Then select the **ASP.NET Core Web Application** project template.</span></span> <span data-ttu-id="4ab1e-116">W polu tekstowym **Nazwa** wpisz "SentimentAnalysisWebAPI", a następnie wybierz przycisk **OK.**</span><span class="sxs-lookup"><span data-stu-id="4ab1e-116">In the **Name** text box, type "SentimentAnalysisWebAPI" and then select the **OK** button.</span></span>

1. <span data-ttu-id="4ab1e-117">W oknie, w które wyświetlane są różne typy projektów ASP.NET podstawowych, wybierz **interfejs API** i wybierz przycisk **OK.**</span><span class="sxs-lookup"><span data-stu-id="4ab1e-117">In the window that displays the different types of ASP.NET Core Projects, select **API** and the select the **OK** button.</span></span>

1. <span data-ttu-id="4ab1e-118">Utwórz katalog o nazwie *MLModels* w projekcie, aby zapisać wstępnie utworzone pliki modelu uczenia maszynowego:</span><span class="sxs-lookup"><span data-stu-id="4ab1e-118">Create a directory named *MLModels* in your project to save your pre-built machine learning model files:</span></span>

    <span data-ttu-id="4ab1e-119">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie Dodaj > nowy folder.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-119">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="4ab1e-120">Wpisz "MLModels" i naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-120">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="4ab1e-121">Zainstaluj **pakiet Microsoft.ML NuGet:**</span><span class="sxs-lookup"><span data-stu-id="4ab1e-121">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="4ab1e-122">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **polecenie Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-122">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="4ab1e-123">Wybierz "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj **Microsoft.ML**, wybierz ten pakiet na liście i wybierz przycisk Zainstaluj.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-123">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="4ab1e-124">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym Akceptacja licencji, jeśli zgadzasz się z warunkami licencyjnymi dla wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-124">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="4ab1e-125">Zainstaluj **pakiet Microsoft.Extensions.ML Nuget:**</span><span class="sxs-lookup"><span data-stu-id="4ab1e-125">Install the **Microsoft.Extensions.ML Nuget Package**:</span></span>

    <span data-ttu-id="4ab1e-126">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **polecenie Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-126">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="4ab1e-127">Wybierz "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj **Microsoft.Extensions.ML**, wybierz ten pakiet na liście i wybierz przycisk Zainstaluj.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-127">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="4ab1e-128">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym Akceptacja licencji, jeśli zgadzasz się z warunkami licencyjnymi dla wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-128">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="add-model-to-aspnet-core-web-api-project"></a><span data-ttu-id="4ab1e-129">Dodawanie modelu do ASP.NET projektu interfejsu API podstawowej sieci Web</span><span class="sxs-lookup"><span data-stu-id="4ab1e-129">Add model to ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="4ab1e-130">Kopiowanie wstępnie utworzonego modelu do katalogu *MLModels*</span><span class="sxs-lookup"><span data-stu-id="4ab1e-130">Copy your pre-built model to the *MLModels* directory</span></span>
1. <span data-ttu-id="4ab1e-131">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy plik zip modelu i wybierz polecenie Właściwości.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-131">In Solution Explorer, right-click the model zip file and select Properties.</span></span> <span data-ttu-id="4ab1e-132">W obszarze Zaawansowane zmień wartość Kopiuj do katalogu wyjściowego, aby kopiować, jeśli nowsza.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-132">Under Advanced, change the value of Copy to Output Directory to Copy if newer.</span></span>

## <a name="create-data-models"></a><span data-ttu-id="4ab1e-133">Tworzenie modeli danych</span><span class="sxs-lookup"><span data-stu-id="4ab1e-133">Create data models</span></span>

<span data-ttu-id="4ab1e-134">Należy utworzyć niektóre klasy dla danych wejściowych i prognoz.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-134">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="4ab1e-135">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="4ab1e-135">Add a new class to your project:</span></span>

1. <span data-ttu-id="4ab1e-136">Utwórz katalog o nazwie *DataModels* w projekcie, aby zapisać modele danych:</span><span class="sxs-lookup"><span data-stu-id="4ab1e-136">Create a directory named *DataModels* in your project to save your data models:</span></span>

    <span data-ttu-id="4ab1e-137">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie Dodaj > nowy folder.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-137">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="4ab1e-138">Wpisz "DataModels" i naciśnij klawisz **Enter**.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-138">Type "DataModels" and hit **Enter**.</span></span>

2. <span data-ttu-id="4ab1e-139">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy katalog *DataModels,* a następnie wybierz polecenie Dodaj > nowy element.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-139">In Solution Explorer, right-click the *DataModels* directory, and then select Add > New Item.</span></span>
3. <span data-ttu-id="4ab1e-140">W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-140">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="4ab1e-141">Następnie wybierz przycisk **Dodaj.**</span><span class="sxs-lookup"><span data-stu-id="4ab1e-141">Then, select the **Add** button.</span></span> <span data-ttu-id="4ab1e-142">Plik *SentimentData.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-142">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="4ab1e-143">Dodaj następującą instrukcję za pomocą do górnej części *SentimentData.cs:*</span><span class="sxs-lookup"><span data-stu-id="4ab1e-143">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="4ab1e-144">Usuń istniejącą definicję klasy i dodaj następujący kod do **pliku SentimentData.cs:**</span><span class="sxs-lookup"><span data-stu-id="4ab1e-144">Remove the existing class definition and add the following code to the **SentimentData.cs** file:</span></span>

    ```csharp
    public class SentimentData
    {
        [LoadColumn(0)]
        public string SentimentText;

        [LoadColumn(1)]
        [ColumnName("Label")]
        public bool Sentiment;
    }
    ```

4. <span data-ttu-id="4ab1e-145">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy katalog *DataModels,* a następnie wybierz polecenie **Dodaj > nowy element**.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-145">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="4ab1e-146">W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-146">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="4ab1e-147">Następnie wybierz przycisk Dodaj.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-147">Then, select the Add button.</span></span> <span data-ttu-id="4ab1e-148">Plik *SentimentPrediction.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-148">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="4ab1e-149">Dodaj następującą instrukcję używającą *SentimentPrediction.cs:*</span><span class="sxs-lookup"><span data-stu-id="4ab1e-149">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="4ab1e-150">Usuń istniejącą definicję klasy i dodaj następujący kod do *SentimentPrediction.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="4ab1e-150">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="4ab1e-151">`SentimentPrediction`dziedziczy `SentimentData`z .</span><span class="sxs-lookup"><span data-stu-id="4ab1e-151">`SentimentPrediction` inherits from `SentimentData`.</span></span> <span data-ttu-id="4ab1e-152">Ułatwia to wyświetlanie oryginalnych danych `SentimentText` we właściwości wraz z danymi wyjściowymi generowanymi przez model.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-152">This makes it easier to see the original data in the `SentimentText` property along with the output generated by the model.</span></span>

## <a name="register-predictionenginepool-for-use-in-the-application"></a><span data-ttu-id="4ab1e-153">Zarejestruj PredictionEnginePool do użycia w aplikacji</span><span class="sxs-lookup"><span data-stu-id="4ab1e-153">Register PredictionEnginePool for use in the application</span></span>

<span data-ttu-id="4ab1e-154">Aby utworzyć pojedynczą prognozę, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)musisz utworzyć plik .</span><span class="sxs-lookup"><span data-stu-id="4ab1e-154">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="4ab1e-155">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny dla nici.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-155">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="4ab1e-156">Ponadto należy utworzyć wystąpienie wszędzie tam, gdzie jest to potrzebne w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-156">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="4ab1e-157">Wraz ze wzrostem aplikacji ten proces może stać się niewykonalny.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-157">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="4ab1e-158">Aby zwiększyć wydajność i bezpieczeństwo wątków, należy `PredictionEnginePool` użyć kombinacji [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) iniekcji zależności i usługi, która tworzy obiektów [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do użycia w całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-158">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

<span data-ttu-id="4ab1e-159">Poniższy link zawiera więcej informacji, jeśli chcesz dowiedzieć się więcej o [wstrzykiwaniu zależności w ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span><span class="sxs-lookup"><span data-stu-id="4ab1e-159">The following link provides more information if you want to learn more about [dependency injection in ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span></span>

1. <span data-ttu-id="4ab1e-160">Otwórz *klasę Startup.cs* i dodaj następującą instrukcję za pomocą do góry pliku:</span><span class="sxs-lookup"><span data-stu-id="4ab1e-160">Open the *Startup.cs* class and add the following using statement to the top of the file:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. <span data-ttu-id="4ab1e-161">Dodaj następujący kod do *metody ConfigureServices:*</span><span class="sxs-lookup"><span data-stu-id="4ab1e-161">Add the following code to the *ConfigureServices* method:</span></span>

    ```csharp
    services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
        .FromFile(modelName: "SentimentAnalysisModel", filePath:"MLModels/sentiment_model.zip", watchForChanges: true);
    ```

<span data-ttu-id="4ab1e-162">Na wysokim poziomie ten kod inicjaalizuje obiekty i usługi automatycznie do późniejszego użycia, gdy jest to wymagane przez aplikację, zamiast ręcznie to zrobić.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-162">At a high level, this code initializes the objects and services automatically for later use when requested by the application instead of having to manually do it.</span></span>

<span data-ttu-id="4ab1e-163">Modele uczenia maszynowego nie są statyczne.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-163">Machine learning models are not static.</span></span> <span data-ttu-id="4ab1e-164">W miarę udostępniania nowych danych szkoleniowych model jest ponownie trenowany i ponownie wdrożony.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-164">As new training data becomes available, the model is retrained and redeployed.</span></span> <span data-ttu-id="4ab1e-165">Jednym ze sposobów, aby uzyskać najnowszą wersję modelu do aplikacji jest ponowne wdrożenie całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-165">One way to get the latest version of the model into your application is to redeploy the entire application.</span></span> <span data-ttu-id="4ab1e-166">Jednak wprowadza to przestojów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-166">However, this introduces application downtime.</span></span> <span data-ttu-id="4ab1e-167">Usługa `PredictionEnginePool` zapewnia mechanizm, aby ponownie załadować zaktualizowany model bez usuwania aplikacji w dół.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-167">The `PredictionEnginePool` service provides a mechanism to reload an updated model without taking your application down.</span></span>

<span data-ttu-id="4ab1e-168">Ustaw `watchForChanges` parametr `true`na , `PredictionEnginePool` a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) rozpoczyna a, który nasłuchuje powiadomień o zmianie systemu plików i wywołuje zdarzenia, gdy nastąpi zmiana pliku.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-168">Set the `watchForChanges` parameter to `true`, and the `PredictionEnginePool` starts a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) that listens to the file system change notifications and raises events when there is a change to the file.</span></span> <span data-ttu-id="4ab1e-169">Spowoduje to `PredictionEnginePool` wyświetlenie monitu o automatyczne ponowne załadowanie modelu.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-169">This prompts the `PredictionEnginePool` to automatically reload the model.</span></span>

<span data-ttu-id="4ab1e-170">Model jest identyfikowany `modelName` przez parametr, dzięki czemu więcej niż jeden model na aplikację można ponownie załadować po zmianie.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-170">The model is identified by the `modelName` parameter so that more than one model per application can be reloaded upon change.</span></span>

> [!TIP]
> <span data-ttu-id="4ab1e-171">Alternatywnie można użyć `FromUri` tej metody podczas pracy z modelami przechowywanymi zdalnie.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-171">Alternatively, you can use the `FromUri` method when working with models stored remotely.</span></span> <span data-ttu-id="4ab1e-172">Zamiast oglądać zdarzenia zmienione `FromUri` pliki, sonduje lokalizację zdalną pod kątem zmian.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-172">Rather than watching for file changed events, `FromUri` polls the remote location for changes.</span></span> <span data-ttu-id="4ab1e-173">Interwał sondowania domyślnie wynosi 5 minut.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-173">The polling interval defaults to 5 minutes.</span></span> <span data-ttu-id="4ab1e-174">Interwał sondowania można zwiększyć lub zmniejszyć na podstawie wymagań aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-174">You can increase or decrease the polling interval based on your application's requirements.</span></span> <span data-ttu-id="4ab1e-175">W poniższym przykładzie `PredictionEnginePool` kodu sonduje model przechowywany przy określonym identyfikatorze URI co minutę.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-175">In the code sample below, the `PredictionEnginePool` polls the model stored at the specified URI every minute.</span></span>
>
>```csharp
>services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="create-predict-controller"></a><span data-ttu-id="4ab1e-176">Tworzenie kontrolera Predict</span><span class="sxs-lookup"><span data-stu-id="4ab1e-176">Create Predict controller</span></span>

<span data-ttu-id="4ab1e-177">Aby przetworzyć przychodzące żądania HTTP, utwórz kontroler.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-177">To process your incoming HTTP requests, create a controller.</span></span>

1. <span data-ttu-id="4ab1e-178">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy katalog *Kontrolery,* a następnie wybierz polecenie **Dodaj > kontrolera**.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-178">In Solution Explorer, right-click the *Controllers* directory, and then select **Add > Controller**.</span></span>
1. <span data-ttu-id="4ab1e-179">W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Kontroler interfejsu **API Pusty** i wybierz pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-179">In the **Add New Item** dialog box, select **API Controller Empty** and select **Add**.</span></span>
1. <span data-ttu-id="4ab1e-180">W wierszu polecenia zmień pole **Nazwa kontrolera** na *PredictController.cs*.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-180">In the prompt change the **Controller Name** field to *PredictController.cs*.</span></span> <span data-ttu-id="4ab1e-181">Następnie wybierz przycisk Dodaj.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-181">Then, select the Add button.</span></span> <span data-ttu-id="4ab1e-182">Plik *PredictController.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-182">The *PredictController.cs* file opens in the code editor.</span></span> <span data-ttu-id="4ab1e-183">Dodaj następującą instrukcję używającą *PredictController.cs:*</span><span class="sxs-lookup"><span data-stu-id="4ab1e-183">Add the following using statement to the top of *PredictController.cs*:</span></span>

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    <span data-ttu-id="4ab1e-184">Usuń istniejącą definicję klasy i dodaj następujący kod do *pliku PredictController.cs:*</span><span class="sxs-lookup"><span data-stu-id="4ab1e-184">Remove the existing class definition and add the following code to the *PredictController.cs* file:</span></span>

    ```csharp
    public class PredictController : ControllerBase
    {
        private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

        public PredictController(PredictionEnginePool<SentimentData,SentimentPrediction> predictionEnginePool)
        {
            _predictionEnginePool = predictionEnginePool;
        }

        [HttpPost]
        public ActionResult<string> Post([FromBody] SentimentData input)
        {
            if(!ModelState.IsValid)
            {
                return BadRequest();
            }

            SentimentPrediction prediction = _predictionEnginePool.Predict(modelName: "SentimentAnalysisModel", example: input);

            string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

            return Ok(sentiment);
        }
    }
    ```

<span data-ttu-id="4ab1e-185">Ten kod przypisuje `PredictionEnginePool` przez przekazanie go do konstruktora kontrolera, które można uzyskać za pomocą iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-185">This code assigns the `PredictionEnginePool` by passing it to the controller's constructor which you get via dependency injection.</span></span> <span data-ttu-id="4ab1e-186">Następnie metoda `Predict` kontrolera `Post` używa `PredictionEnginePool` do prognozowania `SentimentAnalysisModel` przy użyciu `Startup` zarejestrowanych w klasie i zwraca wyniki z powrotem do użytkownika, jeśli się powiedzie.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-186">Then, the `Predict` controller's `Post` method uses the `PredictionEnginePool` to make predictions using the `SentimentAnalysisModel` registered in the `Startup` class and returns the results back to the user if successful.</span></span>

## <a name="test-web-api-locally"></a><span data-ttu-id="4ab1e-187">Testowanie internetowego interfejsu API lokalnie</span><span class="sxs-lookup"><span data-stu-id="4ab1e-187">Test web API locally</span></span>

<span data-ttu-id="4ab1e-188">Po skonfigurowaniu wszystkiego nadszedł czas, aby przetestować aplikację.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-188">Once everything is set up, it's time to test the application.</span></span>

1. <span data-ttu-id="4ab1e-189">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-189">Run the application.</span></span>
1. <span data-ttu-id="4ab1e-190">Otwórz program PowerShell i wprowadź następujący kod, w którym port jest portem, na którym nasłuchuje aplikacja.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-190">Open Powershell and enter the following code where PORT is the port your application is listening on.</span></span>

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{SentimentText="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="4ab1e-191">Jeśli się powiedzie, dane wyjściowe powinny wyglądać podobnie do poniższego tekstu:</span><span class="sxs-lookup"><span data-stu-id="4ab1e-191">If successful, the output should look similar to the text below:</span></span>

    ```powershell
    Negative
    ```

<span data-ttu-id="4ab1e-192">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="4ab1e-192">Congratulations!</span></span> <span data-ttu-id="4ab1e-193">Pomyślnie służył eś modelowi do tworzenia prognoz przez Internet przy użyciu interfejsu ASP.NET Core Web API.</span><span class="sxs-lookup"><span data-stu-id="4ab1e-193">You have successfully served your model to make predictions over the internet using an ASP.NET Core Web API.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4ab1e-194">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="4ab1e-194">Next Steps</span></span>

- [<span data-ttu-id="4ab1e-195">Wdrażanie na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="4ab1e-195">Deploy to Azure</span></span>](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs#deploy-the-app-to-azure)
