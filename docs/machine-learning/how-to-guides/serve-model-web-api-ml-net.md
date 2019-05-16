---
title: Wdrażanie modelu w interfejsie API sieci Web platformy ASP.NET Core
description: Obsługiwać model uczenia maszynowego analizy tonacji strukturze ML.NET w Internecie przy użyciu interfejsu API sieci Web programu ASP.NET Core
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: f8b8f74f752aeb243d4a2987929bd28ddc5f7d5a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641083"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a><span data-ttu-id="ea4fd-103">Wdrażanie modelu w interfejsie API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ea4fd-103">Deploy a model in an ASP.NET Core Web API</span></span>

<span data-ttu-id="ea4fd-104">Dowiedz się, jak obsługiwać wstępnie przeszkolonych strukturze ML.NET modelu uczenia maszynowego w sieci web przy użyciu interfejsu API sieci Web programu ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-104">Learn how to serve a pre-trained ML.NET machine learning model on the web using an ASP.NET Core Web API.</span></span> <span data-ttu-id="ea4fd-105">Obsługuje model za pośrednictwem interfejsu API sieci web umożliwia prognozy przy użyciu standardowych metod HTTP.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-105">Serving a model over a web API enables predictions via standard HTTP methods.</span></span>

> [!NOTE]
> <span data-ttu-id="ea4fd-106">`PredictionEnginePool` rozszerzenie usługi jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-106">`PredictionEnginePool` service extension is currently in preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ea4fd-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="ea4fd-107">Prerequisites</span></span>

- <span data-ttu-id="ea4fd-108">[Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".</span><span class="sxs-lookup"><span data-stu-id="ea4fd-108">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- <span data-ttu-id="ea4fd-109">Program PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-109">Powershell.</span></span>
- <span data-ttu-id="ea4fd-110">Wstępnie uczonego modelu.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-110">Pre-trained model.</span></span> <span data-ttu-id="ea4fd-111">Użyj [samouczek analizy tonacji w strukturze ML.NET](../tutorials/sentiment-analysis.md) do stworzenia własnego modelu lub pobrać [modelu uczenia maszynowego analizy tonacji wstępnie przeszkolonych](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="ea4fd-111">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-aspnet-core-web-api-project"></a><span data-ttu-id="ea4fd-112">Utwórz projekt internetowego interfejsu API platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ea4fd-112">Create ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="ea4fd-113">Otwórz program Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-113">Open Visual Studio 2017.</span></span> <span data-ttu-id="ea4fd-114">Wybierz **Plik > Nowy > Projekt** z paska menu.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-114">Select **File > New > Project** from the menu bar.</span></span> <span data-ttu-id="ea4fd-115">W oknie dialogowym Nowy projekt, wybierz **Visual C#**  węzła następuje **Web** węzła.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-115">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="ea4fd-116">Następnie wybierz pozycję **aplikacji sieci Web programu ASP.NET Core** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-116">Then select the **ASP.NET Core Web Application** project template.</span></span> <span data-ttu-id="ea4fd-117">W **nazwa** pole tekstowe, wpisz "SentimentAnalysisWebAPI", a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-117">In the **Name** text box, type "SentimentAnalysisWebAPI" and then select the **OK** button.</span></span>

1. <span data-ttu-id="ea4fd-118">W oknie, które są wyświetlane różne typy projektów programu ASP.NET Core, wybierz **API** a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-118">In the window that displays the different types of ASP.NET Core Projects, select **API** and the select the **OK** button.</span></span>

1. <span data-ttu-id="ea4fd-119">Utwórz katalog o nazwie *MLModels* w projekcie do zapisywania maszyny wstępnie skompilowanych plików modeli uczenia:</span><span class="sxs-lookup"><span data-stu-id="ea4fd-119">Create a directory named *MLModels* in your project to save your pre-built machine learning model files:</span></span>

    <span data-ttu-id="ea4fd-120">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy nad projektem i wybierz polecenie Dodaj > Nowy Folder.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-120">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="ea4fd-121">Wpisz "MLModels", a następnie naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-121">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="ea4fd-122">Zainstaluj **pakietu NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="ea4fd-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="ea4fd-123">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="ea4fd-124">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i kliknij przycisk Zainstaluj.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-124">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="ea4fd-125">Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na okno dialogowe akceptacja licencji, jeśli akceptujesz postanowienia licencyjne pakiety wymienione.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-125">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="ea4fd-126">Zainstaluj **pakietu Nuget Microsoft.Extensions.ML**:</span><span class="sxs-lookup"><span data-stu-id="ea4fd-126">Install the **Microsoft.Extensions.ML Nuget Package**:</span></span>

    <span data-ttu-id="ea4fd-127">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-127">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="ea4fd-128">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.Extensions.ML**, a następnie wybierz pakiet z listy i kliknij przycisk Zainstaluj.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-128">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="ea4fd-129">Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na okno dialogowe akceptacja licencji, jeśli akceptujesz postanowienia licencyjne pakiety wymienione.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-129">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="add-model-to-aspnet-core-web-api-project"></a><span data-ttu-id="ea4fd-130">Dodawanie modelu do projektu internetowego interfejsu API platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ea4fd-130">Add model to ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="ea4fd-131">Skopiuj wstępnie skompilowanych model *MLModels* katalogu</span><span class="sxs-lookup"><span data-stu-id="ea4fd-131">Copy your pre-built model to the *MLModels* directory</span></span>
1. <span data-ttu-id="ea4fd-132">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy plik zip modelu i wybierz polecenie Właściwości.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-132">In Solution Explorer, right-click the model zip file and select Properties.</span></span> <span data-ttu-id="ea4fd-133">W obszarze Zaawansowane Zmień wartość kopii do katalogu wyjściowego do skopiowania, jeśli nowszy.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-133">Under Advanced, change the value of Copy to Output Directory to Copy if newer.</span></span>

## <a name="create-data-models"></a><span data-ttu-id="ea4fd-134">Tworzenie modeli danych</span><span class="sxs-lookup"><span data-stu-id="ea4fd-134">Create data models</span></span>

<span data-ttu-id="ea4fd-135">Musisz utworzyć niektóre klasy dla danych wejściowych i prognozy.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-135">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="ea4fd-136">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="ea4fd-136">Add a new class to your project:</span></span>

1. <span data-ttu-id="ea4fd-137">Utwórz katalog o nazwie *DataModels* w projekcie, aby zapisać modeli danych:</span><span class="sxs-lookup"><span data-stu-id="ea4fd-137">Create a directory named *DataModels* in your project to save your data models:</span></span>

    <span data-ttu-id="ea4fd-138">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy nad projektem i wybierz polecenie Dodaj > Nowy Folder.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-138">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="ea4fd-139">Wpisz "DataModels", a następnie kliknij przycisk **Enter**.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-139">Type "DataModels" and hit **Enter**.</span></span>

2. <span data-ttu-id="ea4fd-140">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy *DataModels* katalogu, a następnie wybierz pozycję Dodaj > Nowy element.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-140">In Solution Explorer, right-click the *DataModels* directory, and then select Add > New Item.</span></span>
3. <span data-ttu-id="ea4fd-141">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-141">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="ea4fd-142">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-142">Then, select the **Add** button.</span></span> <span data-ttu-id="ea4fd-143">*SentimentData.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-143">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="ea4fd-144">Dodaj następujące za pomocą instrukcji na górze *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="ea4fd-144">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    <span data-ttu-id="ea4fd-145">Usuń istniejącą definicję klasy i Dodaj następujący kod do **SentimentData.cs** pliku:</span><span class="sxs-lookup"><span data-stu-id="ea4fd-145">Remove the existing class definition and add the following code to the **SentimentData.cs** file:</span></span>
    
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

4. <span data-ttu-id="ea4fd-146">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy *DataModels* katalogu, a następnie wybierz **Dodaj > Nowy element**.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-146">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="ea4fd-147">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="ea4fd-148">Następnie wybierz przycisk Dodaj.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-148">Then, select the Add button.</span></span> <span data-ttu-id="ea4fd-149">*SentimentPrediction.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-149">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="ea4fd-150">Dodaj następujące za pomocą instrukcji na górze *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="ea4fd-150">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    <span data-ttu-id="ea4fd-151">Usuń istniejącą definicję klasy i Dodaj następujący kod do *SentimentPrediction.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="ea4fd-151">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>
    
    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="ea4fd-152">`SentimentPrediction` dziedziczy `SentimentData`.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-152">`SentimentPrediction` inherits from `SentimentData`.</span></span> <span data-ttu-id="ea4fd-153">Dzięki temu łatwiej zobaczyć oryginalne dane w `SentimentText` właściwości oraz dane wyjściowe generowane przez model.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-153">This makes it easier to see the original data in the `SentimentText` property along with the output generated by the model.</span></span> 

## <a name="register-predictionenginepool-for-use-in-the-application"></a><span data-ttu-id="ea4fd-154">Zarejestruj PredictionEnginePool do użycia w aplikacji</span><span class="sxs-lookup"><span data-stu-id="ea4fd-154">Register PredictionEnginePool for use in the application</span></span>

<span data-ttu-id="ea4fd-155">Do pojedynczego prognozowania, należy użyć [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="ea4fd-155">To make a single prediction, use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="ea4fd-156">Aby można było używać [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602) w aplikacji należy go utworzyć, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-156">In order to use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) in your application you must create it when it's needed.</span></span> <span data-ttu-id="ea4fd-157">W takim przypadku najlepszym rozwiązaniem należy wziąć pod uwagę jest iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-157">In that case, a best practice to consider is dependency injection.</span></span>

<span data-ttu-id="ea4fd-158">Kliknięcie następującego łącza zawiera więcej informacji, jeśli chcesz dowiedzieć się więcej na temat [wstrzykiwanie zależności w programie ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span><span class="sxs-lookup"><span data-stu-id="ea4fd-158">The following link provides more information if you want to learn about [dependency injection in ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span></span>

1. <span data-ttu-id="ea4fd-159">Otwórz *Startup.cs* klasę i dodaj następujące za pomocą instrukcji na górze pliku:</span><span class="sxs-lookup"><span data-stu-id="ea4fd-159">Open the *Startup.cs* class and add the following using statement to the top of the file:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. <span data-ttu-id="ea4fd-160">Dodaj następujący kod do *ConfigureServices* metody:</span><span class="sxs-lookup"><span data-stu-id="ea4fd-160">Add the following code to the *ConfigureServices* method:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);
        services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
            .FromFile("MLModels/sentiment_model.zip");
    }
    ```

<span data-ttu-id="ea4fd-161">Na wysokim poziomie ten kod inicjalizuje obiektami i usługami, automatycznie, gdy jest to wymagane przez aplikację, nie trzeba to zrobić ręcznie.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-161">At a high level, this code initializes the objects and services automatically when requested by the application instead of having to manually do it.</span></span>

> [!WARNING]
> <span data-ttu-id="ea4fd-162">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nie jest metodą o bezpiecznych wątkach.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-162">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="ea4fd-163">Zwiększona wydajność i bezpieczeństwo wątków, użyj `PredictionEnginePool` usługa, która tworzy [ `ObjectPool` ](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) z `PredictionEngine` obiekty do użytku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-163">For improved performance and thread safety, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of `PredictionEngine` objects for application use.</span></span> <span data-ttu-id="ea4fd-164">Przeczytaj następujący wpis w blogu, aby dowiedzieć się więcej o [tworzenia i używania `PredictionEngine` obiektu pul w programie ASP.NET Core](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span><span class="sxs-lookup"><span data-stu-id="ea4fd-164">Read the following blog post to learn more about [creating and using `PredictionEngine` object pools in ASP.NET Core](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span>  

## <a name="create-predict-controller"></a><span data-ttu-id="ea4fd-165">Tworzenie kontrolera Predict</span><span class="sxs-lookup"><span data-stu-id="ea4fd-165">Create Predict controller</span></span>

<span data-ttu-id="ea4fd-166">Do przetwarzania przychodzących żądań HTTP, należy utworzyć kontroler.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-166">To process your incoming HTTP requests, create a controller.</span></span>

1. <span data-ttu-id="ea4fd-167">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy *kontrolerów* katalogu, a następnie wybierz **Dodaj > kontrolera**.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-167">In Solution Explorer, right-click the *Controllers* directory, and then select **Add > Controller**.</span></span>
1. <span data-ttu-id="ea4fd-168">W **Dodaj nowy element** okno dialogowe, wybierz opcję **pusty Kontroler interfejsu API** i wybierz **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-168">In the **Add New Item** dialog box, select **API Controller Empty** and select **Add**.</span></span>
1. <span data-ttu-id="ea4fd-169">Zmiana monitu **nazwy kontrolera** pole *PredictController.cs*.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-169">In the prompt change the **Controller Name** field to *PredictController.cs*.</span></span> <span data-ttu-id="ea4fd-170">Następnie wybierz przycisk Dodaj.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-170">Then, select the Add button.</span></span> <span data-ttu-id="ea4fd-171">*PredictController.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-171">The *PredictController.cs* file opens in the code editor.</span></span> <span data-ttu-id="ea4fd-172">Dodaj następujące za pomocą instrukcji na górze *PredictController.cs*:</span><span class="sxs-lookup"><span data-stu-id="ea4fd-172">Add the following using statement to the top of *PredictController.cs*:</span></span>

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    <span data-ttu-id="ea4fd-173">Usuń istniejącą definicję klasy i Dodaj następujący kod do *PredictController.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="ea4fd-173">Remove the existing class definition and add the following code to the *PredictController.cs* file:</span></span>
    
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

            SentimentPrediction prediction = _predictionEnginePool.Predict(input);

            string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

            return Ok(sentiment);
        }
    }
    ```

<span data-ttu-id="ea4fd-174">Ten kod przypisuje `PredictionEnginePool` przez przekazanie jej do konstruktora kontrolera, którego można uzyskać za pomocą iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-174">This code assigns the `PredictionEnginePool` by passing it to the controller's constructor which you get via dependency injection.</span></span> <span data-ttu-id="ea4fd-175">Następnie `Predict` kontrolera `Post` metoda używa `PredictionEnginePool` do tworzenia prognoz i zwracają wyniki do użytkownika, jeśli to się powiedzie.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-175">Then, the `Predict` controller's `Post` method uses the `PredictionEnginePool` to make predictions and return the results back to the user if successful.</span></span>

## <a name="test-web-api-locally"></a><span data-ttu-id="ea4fd-176">Test internetowy interfejs API lokalnie</span><span class="sxs-lookup"><span data-stu-id="ea4fd-176">Test web API locally</span></span>

<span data-ttu-id="ea4fd-177">Po skonfigurowaniu jest wszystko, nadszedł czas na przetestowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-177">Once everything is set up, it's time to test the application.</span></span>

1. <span data-ttu-id="ea4fd-178">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-178">Run the application.</span></span>
1. <span data-ttu-id="ea4fd-179">Otwórz program Powershell, a następnie wprowadź poniższy kod, gdzie jest to port aplikacja nasłuchuje na.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-179">Open Powershell and enter the following code where PORT is the port your application is listening on.</span></span>

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{Text="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="ea4fd-180">Jeśli to się powiedzie, dane wyjściowe powinny wyglądać podobnie do poniższy tekst:</span><span class="sxs-lookup"><span data-stu-id="ea4fd-180">If successful, the output should look similar to the text below:</span></span>
    
    ```powershell
    Negative
    ```

<span data-ttu-id="ea4fd-181">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="ea4fd-181">Congratulations!</span></span> <span data-ttu-id="ea4fd-182">Zostały pomyślnie obsłużone model do przewidywania przyszłych zdarzeń za pośrednictwem Internetu przy użyciu interfejsu API sieci Web programu ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="ea4fd-182">You have successfully served your model to make predictions over the internet using an ASP.NET Core Web API.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ea4fd-183">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="ea4fd-183">Next Steps</span></span>

- [<span data-ttu-id="ea4fd-184">Wdrażanie na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="ea4fd-184">Deploy to Azure</span></span>](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.1#deploy-the-app-to-azure)
