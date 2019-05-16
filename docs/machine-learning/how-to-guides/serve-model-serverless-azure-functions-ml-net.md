---
title: Wdrażanie modelu w usłudze Azure Functions
description: Obsługiwać model analizy tonacji strukturze ML.NET uczenia maszynowego do przewidywania w Internecie przy użyciu usługi Azure Functions
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 9e62d8826227aed07451387cc733d27094327f99
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645096"
---
# <a name="deploy-a-model-to-azure-functions"></a><span data-ttu-id="112ed-103">Wdrażanie modelu w usłudze Azure Functions</span><span class="sxs-lookup"><span data-stu-id="112ed-103">Deploy a model to Azure Functions</span></span>

<span data-ttu-id="112ed-104">Dowiedz się, jak wdrożyć wstępnie przeszkolonych strukturze ML.NET usługi machine learning model do przewidywania za pośrednictwem protokołu HTTP za pośrednictwem środowiska bez użycia serwera usługi Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="112ed-104">Learn how to deploy a pre-trained ML.NET machine learning model for predictions over HTTP through an Azure Functions serverless environment.</span></span>

> [!NOTE]
> <span data-ttu-id="112ed-105">`PredictionEnginePool` rozszerzenie usługi jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="112ed-105">`PredictionEnginePool` service extension is currently in preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="112ed-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="112ed-106">Prerequisites</span></span>

- <span data-ttu-id="112ed-107">[Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) za pomocą obciążenia "Programowanie dla wielu platform .NET Core" i "Programowanie na platformie Azure" zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="112ed-107">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload and "Azure development" installed.</span></span>
- [<span data-ttu-id="112ed-108">Narzędzia usługi Azure Functions</span><span class="sxs-lookup"><span data-stu-id="112ed-108">Azure Functions Tools</span></span>](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- <span data-ttu-id="112ed-109">Program PowerShell</span><span class="sxs-lookup"><span data-stu-id="112ed-109">Powershell</span></span>
- <span data-ttu-id="112ed-110">Wstępnie uczonego modelu.</span><span class="sxs-lookup"><span data-stu-id="112ed-110">Pre-trained model.</span></span> <span data-ttu-id="112ed-111">Użyj [samouczek analizy tonacji w strukturze ML.NET](../tutorials/sentiment-analysis.md) do stworzenia własnego modelu lub pobrać [modelu uczenia maszynowego analizy tonacji wstępnie przeszkolonych](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="112ed-111">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-azure-functions-project"></a><span data-ttu-id="112ed-112">Tworzenie projektu usługi Azure Functions</span><span class="sxs-lookup"><span data-stu-id="112ed-112">Create Azure Functions project</span></span>

1. <span data-ttu-id="112ed-113">Otwórz program Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="112ed-113">Open Visual Studio 2017.</span></span> <span data-ttu-id="112ed-114">Wybierz **pliku** > **New** > **projektu** z paska menu.</span><span class="sxs-lookup"><span data-stu-id="112ed-114">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="112ed-115">W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#**  węzła następuje **chmury** węzła.</span><span class="sxs-lookup"><span data-stu-id="112ed-115">In the **New Project** dialog, select the **Visual C#** node followed by the **Cloud** node.</span></span> <span data-ttu-id="112ed-116">Następnie wybierz pozycję **usługi Azure Functions** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="112ed-116">Then select the **Azure Functions** project template.</span></span> <span data-ttu-id="112ed-117">W **nazwa** pole tekstowe, wpisz "SentimentAnalysisFunctionsApp", a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="112ed-117">In the **Name** text box, type "SentimentAnalysisFunctionsApp" and then select the **OK** button.</span></span>
1. <span data-ttu-id="112ed-118">W **nowy projekt** okno dialogowe, Otwórz listę rozwijaną powyżej opcje projektu i wybierz **usługi Azure Functions w wersji 2 (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="112ed-118">In the **New Project** dialog, open the dropdown above the project options and select **Azure Functions v2 (.NET Core)**.</span></span> <span data-ttu-id="112ed-119">Następnie wybierz **wyzwalacza Http** projektu, a następnie wybierz pozycję **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="112ed-119">Then, select the **Http trigger** project and then select the **OK** button.</span></span>
1. <span data-ttu-id="112ed-120">Utwórz katalog o nazwie *MLModels* w projekcie, aby zapisać modelu:</span><span class="sxs-lookup"><span data-stu-id="112ed-120">Create a directory named *MLModels* in your project to save your model:</span></span>

    <span data-ttu-id="112ed-121">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nad projektem i wybierz **Dodaj** > **nowy Folder**.</span><span class="sxs-lookup"><span data-stu-id="112ed-121">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="112ed-122">Wpisz "MLModels", a następnie naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="112ed-122">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="112ed-123">Zainstaluj **pakietu NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="112ed-123">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="112ed-124">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="112ed-124">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="112ed-125">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="112ed-125">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="112ed-126">Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.</span><span class="sxs-lookup"><span data-stu-id="112ed-126">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="112ed-127">Zainstaluj **pakietu NuGet Microsoft.Extensions.ML**:</span><span class="sxs-lookup"><span data-stu-id="112ed-127">Install the **Microsoft.Extensions.ML NuGet Package**:</span></span>

    <span data-ttu-id="112ed-128">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="112ed-128">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="112ed-129">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.Extensions.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="112ed-129">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="112ed-130">Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.</span><span class="sxs-lookup"><span data-stu-id="112ed-130">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="add-pre-trained-model-to-project"></a><span data-ttu-id="112ed-131">Dodaj wstępnie uczonego modelu do projektu</span><span class="sxs-lookup"><span data-stu-id="112ed-131">Add pre-trained model to project</span></span>

1. <span data-ttu-id="112ed-132">Skopiuj wstępnie skompilowanych model *MLModels* folderu.</span><span class="sxs-lookup"><span data-stu-id="112ed-132">Copy your pre-built model to the *MLModels* folder.</span></span>
1. <span data-ttu-id="112ed-133">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy plik wstępnie utworzonych modeli, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="112ed-133">In Solution Explorer, right-click your pre-built model file and select **Properties**.</span></span> <span data-ttu-id="112ed-134">W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="112ed-134">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="create-azure-function-to-analyze-sentiment"></a><span data-ttu-id="112ed-135">Tworzenie funkcji platformy Azure analizować tonację</span><span class="sxs-lookup"><span data-stu-id="112ed-135">Create Azure Function to analyze sentiment</span></span>

<span data-ttu-id="112ed-136">Utwórz klasę do prognozowania wskaźniki nastrojów klientów.</span><span class="sxs-lookup"><span data-stu-id="112ed-136">Create a class to predict sentiment.</span></span> <span data-ttu-id="112ed-137">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="112ed-137">Add a new class to your project:</span></span>

1. <span data-ttu-id="112ed-138">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="112ed-138">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="112ed-139">W **Dodaj nowy element** okno dialogowe, wybierz opcję **funkcji platformy Azure** i zmień **nazwa** pole *AnalyzeSentiment.cs*.</span><span class="sxs-lookup"><span data-stu-id="112ed-139">In the **Add New Item** dialog box, select **Azure Function** and change the **Name** field to *AnalyzeSentiment.cs*.</span></span> <span data-ttu-id="112ed-140">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="112ed-140">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="112ed-141">W **nowej funkcji platformy Azure** okno dialogowe, wybierz opcję **wyzwalacza Http**.</span><span class="sxs-lookup"><span data-stu-id="112ed-141">In the **New Azure Function** dialog box, select **Http Trigger**.</span></span> <span data-ttu-id="112ed-142">Następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="112ed-142">Then, select the **OK** button.</span></span>

    <span data-ttu-id="112ed-143">*AnalyzeSentiment.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="112ed-143">The *AnalyzeSentiment.cs* file opens in the code editor.</span></span> <span data-ttu-id="112ed-144">Dodaj następujący kod `using` instrukcji na górze *AnalyzeSentiment.cs*:</span><span class="sxs-lookup"><span data-stu-id="112ed-144">Add the following `using` statement to the top of *AnalyzeSentiment.cs*:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Threading.Tasks;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Azure.WebJobs;
    using Microsoft.Azure.WebJobs.Extensions.Http;
    using Microsoft.AspNetCore.Http;
    using Microsoft.Extensions.Logging;
    using Newtonsoft.Json;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    <span data-ttu-id="112ed-145">Domyślnie `AnalyzeSentiment` klasa jest `static`.</span><span class="sxs-lookup"><span data-stu-id="112ed-145">By default, the `AnalyzeSentiment` class is `static`.</span></span> <span data-ttu-id="112ed-146">Upewnij się usunąć `static` — słowo kluczowe z poziomu definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="112ed-146">Make sure to remove the `static` keyword from the class definition.</span></span>

    ```csharp
    public class AnalyzeSentiment
    {
    
    }
    ```

## <a name="create-data-models"></a><span data-ttu-id="112ed-147">Tworzenie modeli danych</span><span class="sxs-lookup"><span data-stu-id="112ed-147">Create data models</span></span>

<span data-ttu-id="112ed-148">Musisz utworzyć niektóre klasy dla danych wejściowych i prognozy.</span><span class="sxs-lookup"><span data-stu-id="112ed-148">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="112ed-149">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="112ed-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="112ed-150">Utwórz katalog o nazwie *DataModels* w projekcie, aby zapisać modeli danych: W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj > Nowy Folder**.</span><span class="sxs-lookup"><span data-stu-id="112ed-150">Create a directory named *DataModels* in your project to save your data models: In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="112ed-151">Wpisz "DataModels", a następnie naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="112ed-151">Type "DataModels" and hit Enter.</span></span>
2. <span data-ttu-id="112ed-152">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy *DataModels* katalogu, a następnie wybierz **Dodaj > Nowy element**.</span><span class="sxs-lookup"><span data-stu-id="112ed-152">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
3. <span data-ttu-id="112ed-153">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="112ed-153">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="112ed-154">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="112ed-154">Then, select the **Add** button.</span></span> 

    <span data-ttu-id="112ed-155">*SentimentData.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="112ed-155">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="112ed-156">Dodaj następujące za pomocą instrukcji na górze *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="112ed-156">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="112ed-157">Usuń istniejącą definicję klasy i Dodaj następujący kod do *SentimentData.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="112ed-157">Remove the existing class definition and add the following code to the *SentimentData.cs* file:</span></span>
    
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

4. <span data-ttu-id="112ed-158">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy *DataModels* katalogu, a następnie wybierz **Dodaj > Nowy element**.</span><span class="sxs-lookup"><span data-stu-id="112ed-158">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="112ed-159">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="112ed-159">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="112ed-160">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="112ed-160">Then, select the **Add** button.</span></span> <span data-ttu-id="112ed-161">*SentimentPrediction.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="112ed-161">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="112ed-162">Dodaj następujące za pomocą instrukcji na górze *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="112ed-162">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="112ed-163">Usuń istniejącą definicję klasy i Dodaj następujący kod do *SentimentPrediction.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="112ed-163">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="112ed-164">`SentimentPrediction` dziedziczy `SentimentData` zapewniającą dostęp do oryginalnych danych przechowywanych w `SentimentText` właściwości, a także dane wyjściowe generowane przez model.</span><span class="sxs-lookup"><span data-stu-id="112ed-164">`SentimentPrediction` inherits from `SentimentData` which provides access to the original data in the `SentimentText` property as well as the output generated by the model.</span></span>

## <a name="register-predictionenginepool-service"></a><span data-ttu-id="112ed-165">Zarejestruj usługę PredictionEnginePool</span><span class="sxs-lookup"><span data-stu-id="112ed-165">Register PredictionEnginePool service</span></span>

<span data-ttu-id="112ed-166">Do pojedynczego prognozowania, należy użyć [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="112ed-166">To make a single prediction, use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="112ed-167">Aby można było używać [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602) w aplikacji należy go utworzyć, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="112ed-167">In order to use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) in your application you must create it when it's needed.</span></span> <span data-ttu-id="112ed-168">W takim przypadku najlepszym rozwiązaniem należy wziąć pod uwagę jest iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="112ed-168">In that case, a best practice to consider is dependency injection.</span></span>

<span data-ttu-id="112ed-169">Kliknięcie następującego łącza zawiera więcej informacji, jeśli chcesz dowiedzieć się więcej na temat [wstrzykiwanie zależności](https://en.wikipedia.org/wiki/Dependency_injection).</span><span class="sxs-lookup"><span data-stu-id="112ed-169">The following link provides more information if you want to learn about [dependency injection](https://en.wikipedia.org/wiki/Dependency_injection).</span></span>

1. <span data-ttu-id="112ed-170">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="112ed-170">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="112ed-171">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *Startup.cs*.</span><span class="sxs-lookup"><span data-stu-id="112ed-171">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *Startup.cs*.</span></span> <span data-ttu-id="112ed-172">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="112ed-172">Then, select the **Add** button.</span></span> 

    <span data-ttu-id="112ed-173">*Startup.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="112ed-173">The *Startup.cs* file opens in the code editor.</span></span> <span data-ttu-id="112ed-174">Dodaj następujące za pomocą instrukcji na górze *Startup.cs*:</span><span class="sxs-lookup"><span data-stu-id="112ed-174">Add the following using statement to the top of *Startup.cs*:</span></span>

    ```csharp
    using Microsoft.Azure.WebJobs;
    using Microsoft.Azure.WebJobs.Hosting;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    <span data-ttu-id="112ed-175">Usuń istniejący kod poniżej używając instrukcji i Dodaj następujący kod do *Startup.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="112ed-175">Remove the existing code below the using statements and add the following code to the *Startup.cs* file:</span></span>

    ```csharp
    [assembly: WebJobsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        class Startup : IWebJobsStartup
        {
            public void Configure(IWebJobsBuilder builder)
            {
                builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
                    .FromFile("MLModels/sentiment_model.zip");
            }
        }
    }
    ```

<span data-ttu-id="112ed-176">Na wysokim poziomie ten kod inicjalizuje obiektami i usługami, automatycznie, gdy jest to wymagane przez aplikację, nie trzeba to zrobić ręcznie.</span><span class="sxs-lookup"><span data-stu-id="112ed-176">At a high level, this code initializes the objects and services automatically when requested by the application instead of having to manually do it.</span></span>

> [!WARNING]
> <span data-ttu-id="112ed-177">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nie jest metodą o bezpiecznych wątkach.</span><span class="sxs-lookup"><span data-stu-id="112ed-177">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="112ed-178">Zwiększona wydajność i bezpieczeństwo wątków, użyj `PredictionEnginePool` usługa, która tworzy [ `ObjectPool` ](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) z `PredictionEngine` obiekty do użytku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="112ed-178">For improved performance and thread safety, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of `PredictionEngine` objects for application use.</span></span> 

## <a name="register-startup-as-an-azure-functions-extension"></a><span data-ttu-id="112ed-179">Rejestrowanie uruchamiania jako rozszerzenie usługi Azure Functions</span><span class="sxs-lookup"><span data-stu-id="112ed-179">Register Startup as an Azure Functions extension</span></span>

<span data-ttu-id="112ed-180">Aby można było używać `Startup` w aplikacji, należy zarejestrować go jako rozszerzenie usługi Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="112ed-180">In order to use `Startup` in your application, you need to register it as an Azure Functions extension.</span></span> <span data-ttu-id="112ed-181">Utwórz nowy plik o nazwie *extensions.json* w projekcie, jeśli już nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="112ed-181">Create a new file called *extensions.json* in your project if one does not already exist.</span></span>

1. <span data-ttu-id="112ed-182">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="112ed-182">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="112ed-183">W **nowy element** okno dialogowe, wybierz opcję **Visual C#**  węzła następuje **Web** węzła.</span><span class="sxs-lookup"><span data-stu-id="112ed-183">In the **New Item** dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="112ed-184">Następnie wybierz pozycję **plik Json** opcji.</span><span class="sxs-lookup"><span data-stu-id="112ed-184">Then select the **Json File** option.</span></span> <span data-ttu-id="112ed-185">W **nazwa** pole tekstowe, wpisz "extensions.json", a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="112ed-185">In the **Name** text box, type "extensions.json" and then select the **OK** button.</span></span>

    <span data-ttu-id="112ed-186">*Extensions.json* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="112ed-186">The *extensions.json* file opens in the code editor.</span></span> <span data-ttu-id="112ed-187">Dodaj następującą zawartość do *extensions.json*:</span><span class="sxs-lookup"><span data-stu-id="112ed-187">Add the following content to *extensions.json*:</span></span>
    
    ```json
    {
      "extensions": [
        {
          "name": "Startup",
          "typename": "SentimentAnalysisFunctionsApp.Startup, SentimentAnalysisFunctionsApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"
        }
      ]
    }
    ```

1. <span data-ttu-id="112ed-188">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy użytkownika *extensions.json* plik i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="112ed-188">In Solution Explorer, right-click your *extensions.json* file and select **Properties**.</span></span> <span data-ttu-id="112ed-189">W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="112ed-189">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="load-the-model-into-the-function"></a><span data-ttu-id="112ed-190">Ładowanie modelu do funkcji</span><span class="sxs-lookup"><span data-stu-id="112ed-190">Load the model into the function</span></span>

<span data-ttu-id="112ed-191">Wstaw następujący kod wewnątrz *AnalyzeSentiment* klasy:</span><span class="sxs-lookup"><span data-stu-id="112ed-191">Insert the following code inside the *AnalyzeSentiment* class:</span></span>

```csharp
private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

// AnalyzeSentiment class constructor
public AnalyzeSentiment(PredictionEnginePool<SentimentData, SentimentPrediction> predictionEnginePool)
{
    _predictionEnginePool = predictionEnginePool;
}
```

<span data-ttu-id="112ed-192">Ten kod przypisuje `PredictionEnginePool` przez przekazanie jej do funkcji konstruktora, który otrzymujesz za pomocą iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="112ed-192">This code assigns the `PredictionEnginePool` by passing it to the function's constructor which you get via dependency injection.</span></span>

## <a name="use-the-model-to-make-predictions"></a><span data-ttu-id="112ed-193">Użyj modelu do prognozowania</span><span class="sxs-lookup"><span data-stu-id="112ed-193">Use the model to make predictions</span></span>

<span data-ttu-id="112ed-194">Zastąp istniejącą implementację programu *Uruchom* method in Class metoda *AnalyzeSentiment* klasy z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="112ed-194">Replace the existing implementation of *Run* method in *AnalyzeSentiment* class with the following code:</span></span>

```csharp
[FunctionName("AnalyzeSentiment")]
public async Task<IActionResult> Run(
[HttpTrigger(AuthorizationLevel.Function, "post", Route = null)] HttpRequest req,
ILogger log)
{
    log.LogInformation("C# HTTP trigger function processed a request.");

    //Parse HTTP Request Body
    string requestBody = await new StreamReader(req.Body).ReadToEndAsync();
    SentimentData data = JsonConvert.DeserializeObject<SentimentData>(requestBody);
    
    //Make Prediction
    SentimentPrediction prediction = _predictionEnginePool.Predict(data);

    //Convert prediction to string
    string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

    //Return Prediction
    return (ActionResult)new OkObjectResult(sentiment);
}
```

<span data-ttu-id="112ed-195">Gdy `Run` metoda jest wykonywana, dane przychodzące z żądania HTTP jest przeprowadzona i używany jako dane wejściowe na potrzeby `PredictionEnginePool`.</span><span class="sxs-lookup"><span data-stu-id="112ed-195">When the `Run` method executes, the incoming data from the HTTP request is deserialized and used as input for the `PredictionEnginePool`.</span></span> <span data-ttu-id="112ed-196">`Predict` Wywoływana jest metoda następnie generują przewidywanie i zwracają wynik do użytkownika.</span><span class="sxs-lookup"><span data-stu-id="112ed-196">The `Predict` method is then called to generate a prediction and return the result to the user.</span></span> 

## <a name="test-locally"></a><span data-ttu-id="112ed-197">Przetestować ją lokalnie</span><span class="sxs-lookup"><span data-stu-id="112ed-197">Test locally</span></span>

<span data-ttu-id="112ed-198">Teraz, że wszystko zostało skonfigurowane, nadszedł czas na przetestowanie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="112ed-198">Now that everything is set up, it's time to test the application:</span></span>

1. <span data-ttu-id="112ed-199">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="112ed-199">Run the application</span></span>
1. <span data-ttu-id="112ed-200">Otwórz program PowerShell, a następnie wprowadź kod w wierszu polecenia, gdzie jest to port aplikacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="112ed-200">Open PowerShell and enter the code into the prompt where PORT is the port your application is running on.</span></span> <span data-ttu-id="112ed-201">Zazwyczaj port jest 7071.</span><span class="sxs-lookup"><span data-stu-id="112ed-201">Typically the port is 7071.</span></span>

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="112ed-202">Jeśli to się powiedzie, dane wyjściowe powinny wyglądać podobnie do poniższy tekst:</span><span class="sxs-lookup"><span data-stu-id="112ed-202">If successful, the output should look similar to the text below:</span></span>
    
    ```powershell
    Negative
    ```

<span data-ttu-id="112ed-203">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="112ed-203">Congratulations!</span></span> <span data-ttu-id="112ed-204">Zostały pomyślnie obsłużone model do przewidywania przyszłych zdarzeń za pośrednictwem Internetu przy użyciu funkcji platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="112ed-204">You have successfully served your model to make predictions over the internet using an Azure Function.</span></span>

## <a name="next-steps"></a><span data-ttu-id="112ed-205">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="112ed-205">Next Steps</span></span>

- [<span data-ttu-id="112ed-206">Wdrażanie na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="112ed-206">Deploy to Azure</span></span>](/azure/azure-functions/functions-develop-vs#publish-to-azure)
