---
title: Wdrażanie modelu w ASP.NET Core Web API
description: Obsługiwanie modelu uczenia maszynowego w usłudze ML.NET tonacji Analysis za pośrednictwem Internetu przy użyciu interfejsu Web API ASP.NET Core
ms.date: 08/20/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: e1dcc719738a2beb3e63463245d4721c5298cf85
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666661"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a><span data-ttu-id="da2c3-103">Wdrażanie modelu w ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="da2c3-103">Deploy a model in an ASP.NET Core Web API</span></span>

<span data-ttu-id="da2c3-104">Dowiedz się, jak obsłużyć wstępnie szkolony model uczenia maszynowego ML.NET w sieci Web przy użyciu ASP.NET Core internetowego interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="da2c3-104">Learn how to serve a pre-trained ML.NET machine learning model on the web using an ASP.NET Core Web API.</span></span> <span data-ttu-id="da2c3-105">Obsługa modelu przez internetowy interfejs API umożliwia prognozowanie za pośrednictwem standardowych metod HTTP.</span><span class="sxs-lookup"><span data-stu-id="da2c3-105">Serving a model over a web API enables predictions via standard HTTP methods.</span></span>

> [!NOTE]
> <span data-ttu-id="da2c3-106">`PredictionEnginePool`rozszerzenie usługi jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="da2c3-106">`PredictionEnginePool` service extension is currently in preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="da2c3-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="da2c3-107">Prerequisites</span></span>

- <span data-ttu-id="da2c3-108">[Program Visual Studio 2017 15,6 lub nowszy](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="da2c3-108">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- <span data-ttu-id="da2c3-109">Narzędzia.</span><span class="sxs-lookup"><span data-stu-id="da2c3-109">Powershell.</span></span>
- <span data-ttu-id="da2c3-110">Model wstępnie szkolony.</span><span class="sxs-lookup"><span data-stu-id="da2c3-110">Pre-trained model.</span></span> <span data-ttu-id="da2c3-111">Użyj [samouczka analiza tonacji ml.NET](../tutorials/sentiment-analysis.md) , aby skompilować własny model lub pobrać ten [wstępnie szkolony model uczenia maszynowego analizy tonacji](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="da2c3-111">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-aspnet-core-web-api-project"></a><span data-ttu-id="da2c3-112">Tworzenie projektu interfejsu API sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="da2c3-112">Create ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="da2c3-113">Otwórz program Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="da2c3-113">Open Visual Studio 2017.</span></span> <span data-ttu-id="da2c3-114">Wybierz pozycję **plik > nowy > projekt** na pasku menu.</span><span class="sxs-lookup"><span data-stu-id="da2c3-114">Select **File > New > Project** from the menu bar.</span></span> <span data-ttu-id="da2c3-115">W oknie dialogowym Nowy projekt wybierz węzeł **wizualizacji C#**  , a następnie węzeł **sieci Web** .</span><span class="sxs-lookup"><span data-stu-id="da2c3-115">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="da2c3-116">Następnie wybierz szablon projektu **aplikacji sieci Web ASP.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="da2c3-116">Then select the **ASP.NET Core Web Application** project template.</span></span> <span data-ttu-id="da2c3-117">W polu tekstowym **Nazwa** wpisz "SentimentAnalysisWebAPI", a następnie wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="da2c3-117">In the **Name** text box, type "SentimentAnalysisWebAPI" and then select the **OK** button.</span></span>

1. <span data-ttu-id="da2c3-118">W oknie, w którym są wyświetlane różne typy projektów ASP.NET Core, wybierz pozycję **interfejs API** i wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="da2c3-118">In the window that displays the different types of ASP.NET Core Projects, select **API** and the select the **OK** button.</span></span>

1. <span data-ttu-id="da2c3-119">Utwórz katalog o nazwie *MLModels* w projekcie, aby zapisać wstępnie utworzone pliki modelu uczenia maszynowego:</span><span class="sxs-lookup"><span data-stu-id="da2c3-119">Create a directory named *MLModels* in your project to save your pre-built machine learning model files:</span></span>

    <span data-ttu-id="da2c3-120">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie Dodaj > nowy folder.</span><span class="sxs-lookup"><span data-stu-id="da2c3-120">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="da2c3-121">Wpisz "MLModels" i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="da2c3-121">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="da2c3-122">Zainstaluj **pakiet NuGet Microsoft.ml**:</span><span class="sxs-lookup"><span data-stu-id="da2c3-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="da2c3-123">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="da2c3-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="da2c3-124">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, Wyszukaj pozycję **Microsoft.ml**, wybierz ten pakiet z listy, a następnie wybierz przycisk Instaluj.</span><span class="sxs-lookup"><span data-stu-id="da2c3-124">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="da2c3-125">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie wybierz przycisk Akceptuję w oknie dialogowym akceptacji licencji, jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="da2c3-125">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="da2c3-126">Zainstaluj **pakiet Nuget Microsoft.Extensions.ml**:</span><span class="sxs-lookup"><span data-stu-id="da2c3-126">Install the **Microsoft.Extensions.ML Nuget Package**:</span></span>

    <span data-ttu-id="da2c3-127">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="da2c3-127">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="da2c3-128">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, Wyszukaj pozycję **Microsoft.Extensions.ml**, wybierz ten pakiet z listy, a następnie wybierz przycisk Instaluj.</span><span class="sxs-lookup"><span data-stu-id="da2c3-128">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="da2c3-129">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie wybierz przycisk Akceptuję w oknie dialogowym akceptacji licencji, jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="da2c3-129">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="add-model-to-aspnet-core-web-api-project"></a><span data-ttu-id="da2c3-130">Dodaj model do projektu interfejsu API sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="da2c3-130">Add model to ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="da2c3-131">Skopiuj wstępnie utworzony model do katalogu *MLModels*</span><span class="sxs-lookup"><span data-stu-id="da2c3-131">Copy your pre-built model to the *MLModels* directory</span></span>
1. <span data-ttu-id="da2c3-132">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy plik zip modelu i wybierz polecenie Właściwości.</span><span class="sxs-lookup"><span data-stu-id="da2c3-132">In Solution Explorer, right-click the model zip file and select Properties.</span></span> <span data-ttu-id="da2c3-133">W obszarze Zaawansowane Zmień wartość opcji Kopiuj do katalogu wyjściowego na Kopiuj, jeśli nowszy.</span><span class="sxs-lookup"><span data-stu-id="da2c3-133">Under Advanced, change the value of Copy to Output Directory to Copy if newer.</span></span>

## <a name="create-data-models"></a><span data-ttu-id="da2c3-134">Tworzenie modeli danych</span><span class="sxs-lookup"><span data-stu-id="da2c3-134">Create data models</span></span>

<span data-ttu-id="da2c3-135">Należy utworzyć klasy dla danych wejściowych i prognoz.</span><span class="sxs-lookup"><span data-stu-id="da2c3-135">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="da2c3-136">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="da2c3-136">Add a new class to your project:</span></span>

1. <span data-ttu-id="da2c3-137">Utwórz katalog o nazwie datamodels w projekcie, aby zapisać modele danych:</span><span class="sxs-lookup"><span data-stu-id="da2c3-137">Create a directory named *DataModels* in your project to save your data models:</span></span>

    <span data-ttu-id="da2c3-138">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie Dodaj > nowy folder.</span><span class="sxs-lookup"><span data-stu-id="da2c3-138">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="da2c3-139">Wpisz "datamodels" i naciśnij klawisz **Enter**.</span><span class="sxs-lookup"><span data-stu-id="da2c3-139">Type "DataModels" and hit **Enter**.</span></span>

2. <span data-ttu-id="da2c3-140">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy katalog datamodels, a następnie wybierz pozycję Dodaj > nowy element.</span><span class="sxs-lookup"><span data-stu-id="da2c3-140">In Solution Explorer, right-click the *DataModels* directory, and then select Add > New Item.</span></span>
3. <span data-ttu-id="da2c3-141">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="da2c3-141">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="da2c3-142">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="da2c3-142">Then, select the **Add** button.</span></span> <span data-ttu-id="da2c3-143">Plik *SentimentData.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="da2c3-143">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="da2c3-144">Dodaj następującą instrukcję using na początku *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="da2c3-144">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    <span data-ttu-id="da2c3-145">Usuń istniejącą definicję klasy i Dodaj następujący kod do pliku **SentimentData.cs** :</span><span class="sxs-lookup"><span data-stu-id="da2c3-145">Remove the existing class definition and add the following code to the **SentimentData.cs** file:</span></span>
    
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

4. <span data-ttu-id="da2c3-146">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy katalog datamodels, a następnie wybierz pozycję **Dodaj > nowy element**.</span><span class="sxs-lookup"><span data-stu-id="da2c3-146">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="da2c3-147">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="da2c3-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="da2c3-148">Następnie wybierz przycisk Dodaj.</span><span class="sxs-lookup"><span data-stu-id="da2c3-148">Then, select the Add button.</span></span> <span data-ttu-id="da2c3-149">Plik *SentimentPrediction.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="da2c3-149">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="da2c3-150">Dodaj następującą instrukcję using na początku *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="da2c3-150">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    <span data-ttu-id="da2c3-151">Usuń istniejącą definicję klasy i Dodaj następujący kod do pliku *SentimentPrediction.cs* :</span><span class="sxs-lookup"><span data-stu-id="da2c3-151">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>
    
    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="da2c3-152">`SentimentPrediction`dziedziczy z `SentimentData`.</span><span class="sxs-lookup"><span data-stu-id="da2c3-152">`SentimentPrediction` inherits from `SentimentData`.</span></span> <span data-ttu-id="da2c3-153">Dzięki temu można łatwiej zobaczyć oryginalne dane we `SentimentText` właściwości wraz z danymi wyjściowymi generowanymi przez model.</span><span class="sxs-lookup"><span data-stu-id="da2c3-153">This makes it easier to see the original data in the `SentimentText` property along with the output generated by the model.</span></span> 

## <a name="register-predictionenginepool-for-use-in-the-application"></a><span data-ttu-id="da2c3-154">Zarejestruj PredictionEnginePool do użycia w aplikacji</span><span class="sxs-lookup"><span data-stu-id="da2c3-154">Register PredictionEnginePool for use in the application</span></span>

<span data-ttu-id="da2c3-155">Aby wykonać pojedyncze prognozowanie, użyj [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="da2c3-155">To make a single prediction, use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="da2c3-156">Aby można było używać [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) w aplikacji, należy ją utworzyć w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="da2c3-156">In order to use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) in your application you must create it when it's needed.</span></span> <span data-ttu-id="da2c3-157">W takim przypadku najlepszym rozwiązaniem jest wstrzyknięcie zależności.</span><span class="sxs-lookup"><span data-stu-id="da2c3-157">In that case, a best practice to consider is dependency injection.</span></span>

<span data-ttu-id="da2c3-158">Poniższy link zawiera więcej informacji, aby dowiedzieć się więcej o [iniekcji zależności w ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span><span class="sxs-lookup"><span data-stu-id="da2c3-158">The following link provides more information if you want to learn about [dependency injection in ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span></span>

1. <span data-ttu-id="da2c3-159">Otwórz klasę *Startup.cs* i Dodaj następującą instrukcję using na początku pliku:</span><span class="sxs-lookup"><span data-stu-id="da2c3-159">Open the *Startup.cs* class and add the following using statement to the top of the file:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. <span data-ttu-id="da2c3-160">Dodaj następujący kod do metody *ConfigureServices* :</span><span class="sxs-lookup"><span data-stu-id="da2c3-160">Add the following code to the *ConfigureServices* method:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);
        services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
            .FromFile("MLModels/sentiment_model.zip");
    }
    ```

<span data-ttu-id="da2c3-161">Na wysokim poziomie ten kod inicjuje obiekty i usługi automatycznie, gdy jest to wymagane przez aplikację, a nie trzeba jej wykonać ręcznie.</span><span class="sxs-lookup"><span data-stu-id="da2c3-161">At a high level, this code initializes the objects and services automatically when requested by the application instead of having to manually do it.</span></span>

> [!WARNING]
> <span data-ttu-id="da2c3-162">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny wątkowo.</span><span class="sxs-lookup"><span data-stu-id="da2c3-162">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="da2c3-163">Aby zwiększyć wydajność i bezpieczeństwo wątków, użyj `PredictionEnginePool` usługi, która [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) tworzy `PredictionEngine` obiekty do użycia w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da2c3-163">For improved performance and thread safety, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of `PredictionEngine` objects for application use.</span></span> <span data-ttu-id="da2c3-164">Przeczytaj następujący wpis w blogu, aby dowiedzieć się więcej na temat [tworzenia i używania `PredictionEngine` pul obiektów w ASP.NET Core](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span><span class="sxs-lookup"><span data-stu-id="da2c3-164">Read the following blog post to learn more about [creating and using `PredictionEngine` object pools in ASP.NET Core](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span>  

## <a name="create-predict-controller"></a><span data-ttu-id="da2c3-165">Utwórz kontroler predykcyjny</span><span class="sxs-lookup"><span data-stu-id="da2c3-165">Create Predict controller</span></span>

<span data-ttu-id="da2c3-166">Aby przetwarzać przychodzące żądania HTTP, Utwórz kontroler.</span><span class="sxs-lookup"><span data-stu-id="da2c3-166">To process your incoming HTTP requests, create a controller.</span></span>

1. <span data-ttu-id="da2c3-167">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy katalog controllers, a następnie wybierz pozycję **Dodaj kontroler >** .</span><span class="sxs-lookup"><span data-stu-id="da2c3-167">In Solution Explorer, right-click the *Controllers* directory, and then select **Add > Controller**.</span></span>
1. <span data-ttu-id="da2c3-168">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **kontroler interfejsu API puste** i wybierz pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="da2c3-168">In the **Add New Item** dialog box, select **API Controller Empty** and select **Add**.</span></span>
1. <span data-ttu-id="da2c3-169">W oknie monitu Zmień **nazwę kontrolera** na *PredictController.cs*.</span><span class="sxs-lookup"><span data-stu-id="da2c3-169">In the prompt change the **Controller Name** field to *PredictController.cs*.</span></span> <span data-ttu-id="da2c3-170">Następnie wybierz przycisk Dodaj.</span><span class="sxs-lookup"><span data-stu-id="da2c3-170">Then, select the Add button.</span></span> <span data-ttu-id="da2c3-171">Plik *PredictController.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="da2c3-171">The *PredictController.cs* file opens in the code editor.</span></span> <span data-ttu-id="da2c3-172">Dodaj następującą instrukcję using na początku *PredictController.cs*:</span><span class="sxs-lookup"><span data-stu-id="da2c3-172">Add the following using statement to the top of *PredictController.cs*:</span></span>

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    <span data-ttu-id="da2c3-173">Usuń istniejącą definicję klasy i Dodaj następujący kod do pliku *PredictController.cs* :</span><span class="sxs-lookup"><span data-stu-id="da2c3-173">Remove the existing class definition and add the following code to the *PredictController.cs* file:</span></span>
    
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

<span data-ttu-id="da2c3-174">Ten kod przypisuje `PredictionEnginePool` przez przekazanie go do konstruktora kontrolera, który uzyskuje się za pośrednictwem iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="da2c3-174">This code assigns the `PredictionEnginePool` by passing it to the controller's constructor which you get via dependency injection.</span></span> <span data-ttu-id="da2c3-175">`Predict` Następnie Metoda`Post` kontrolera używa `PredictionEnginePool` do tworzenia prognoz i zwracania wyników z powrotem do użytkownika, jeśli to się powiedzie.</span><span class="sxs-lookup"><span data-stu-id="da2c3-175">Then, the `Predict` controller's `Post` method uses the `PredictionEnginePool` to make predictions and return the results back to the user if successful.</span></span>

## <a name="test-web-api-locally"></a><span data-ttu-id="da2c3-176">Testowanie lokalnego interfejsu API sieci Web</span><span class="sxs-lookup"><span data-stu-id="da2c3-176">Test web API locally</span></span>

<span data-ttu-id="da2c3-177">Po skonfigurowaniu wszystkiego czas na przetestowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da2c3-177">Once everything is set up, it's time to test the application.</span></span>

1. <span data-ttu-id="da2c3-178">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="da2c3-178">Run the application.</span></span>
1. <span data-ttu-id="da2c3-179">Otwórz program PowerShell i wprowadź następujący kod, gdzie PORT jest portem, na którym nasłuchuje aplikacja.</span><span class="sxs-lookup"><span data-stu-id="da2c3-179">Open Powershell and enter the following code where PORT is the port your application is listening on.</span></span>

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{SentimentText="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="da2c3-180">Jeśli to się powiedzie, dane wyjściowe powinny wyglądać podobnie do poniższego tekstu:</span><span class="sxs-lookup"><span data-stu-id="da2c3-180">If successful, the output should look similar to the text below:</span></span>
    
    ```powershell
    Negative
    ```

<span data-ttu-id="da2c3-181">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="da2c3-181">Congratulations!</span></span> <span data-ttu-id="da2c3-182">Udało Ci się pomyślnie obsłużyć model, aby przekonywać prognoz przez Internet przy użyciu ASP.NET Core internetowego interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="da2c3-182">You have successfully served your model to make predictions over the internet using an ASP.NET Core Web API.</span></span>

## <a name="next-steps"></a><span data-ttu-id="da2c3-183">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="da2c3-183">Next Steps</span></span>

- [<span data-ttu-id="da2c3-184">Wdrażanie na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="da2c3-184">Deploy to Azure</span></span>](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.1#deploy-the-app-to-azure)
