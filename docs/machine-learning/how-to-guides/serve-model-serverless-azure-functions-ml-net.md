---
title: Wdrażanie modelu strukturze ML.NET do usługi Azure Functions
description: Obsługiwać model analizy tonacji strukturze ML.NET uczenia maszynowego do przewidywania w Internecie przy użyciu usługi Azure Functions
ms.date: 03/08/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 4681b37da64097dd8e537b4c956917277ecff96b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59330639"
---
# <a name="how-to-use-mlnet-model-in-azure-functions"></a><span data-ttu-id="b76ea-103">Instrukcje: Model w strukturze ML.NET użycie w usłudze Azure Functions</span><span class="sxs-lookup"><span data-stu-id="b76ea-103">How-To: Use ML.NET Model in Azure Functions</span></span>

<span data-ttu-id="b76ea-104">Niniejszy instruktaż pokazuje, jak poszczególne prognozy wprowadzone w środowisku bez użycia serwera, takich jak Azure Functions za pomocą wstępnie skompilowanych model uczenia maszynowego strukturze ML.NET za pośrednictwem Internetu.</span><span class="sxs-lookup"><span data-stu-id="b76ea-104">This how-to shows how individual predictions can be made using a pre-built ML.NET machine learning model through the internet in a serverless environment such as Azure Functions.</span></span>

> [!NOTE]
> <span data-ttu-id="b76ea-105">W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="b76ea-105">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="b76ea-106">Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="b76ea-106">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="b76ea-107">Obecnie używasz w tym przykładzie porad i pokrewnych **strukturze ML.NET wersji 0.10**.</span><span class="sxs-lookup"><span data-stu-id="b76ea-107">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="b76ea-108">Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium dotnet/machinelearning github](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="b76ea-108">For more information, see the release notes at the [dotnet/machinelearning github repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b76ea-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="b76ea-109">Prerequisites</span></span>

- <span data-ttu-id="b76ea-110">[Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) za pomocą obciążenia "Programowanie dla wielu platform .NET Core" i "Programowanie na platformie Azure" zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="b76ea-110">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload and "Azure development" installed.</span></span> 
- [<span data-ttu-id="b76ea-111">Narzędzia usługi Azure Functions</span><span class="sxs-lookup"><span data-stu-id="b76ea-111">Azure Functions Tools</span></span>](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- <span data-ttu-id="b76ea-112">Program PowerShell</span><span class="sxs-lookup"><span data-stu-id="b76ea-112">Powershell</span></span>
- <span data-ttu-id="b76ea-113">Wstępnie uczonego modelu.</span><span class="sxs-lookup"><span data-stu-id="b76ea-113">Pre-trained model.</span></span> 
    - <span data-ttu-id="b76ea-114">Użyj [samouczek analizy tonacji w strukturze ML.NET](../tutorials/sentiment-analysis.md) do tworzenia własnego modelu.</span><span class="sxs-lookup"><span data-stu-id="b76ea-114">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model.</span></span>
    - <span data-ttu-id="b76ea-115">Pobierz ten [modelu uczenia maszynowego analizy tonacji wstępnie przeszkolonych](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="b76ea-115">Download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-azure-functions-project"></a><span data-ttu-id="b76ea-116">Tworzenie projektu usługi Azure Functions</span><span class="sxs-lookup"><span data-stu-id="b76ea-116">Create Azure Functions Project</span></span>

1. <span data-ttu-id="b76ea-117">Otwórz program Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="b76ea-117">Open Visual Studio 2017.</span></span> <span data-ttu-id="b76ea-118">Wybierz **pliku** > **New** > **projektu** z paska menu.</span><span class="sxs-lookup"><span data-stu-id="b76ea-118">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="b76ea-119">W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#**  węzła następuje **chmury** węzła.</span><span class="sxs-lookup"><span data-stu-id="b76ea-119">In the **New Project** dialog, select the **Visual C#** node followed by the **Cloud** node.</span></span> <span data-ttu-id="b76ea-120">Następnie wybierz pozycję **usługi Azure Functions** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="b76ea-120">Then select the **Azure Functions** project template.</span></span> <span data-ttu-id="b76ea-121">W **nazwa** pole tekstowe, wpisz "SentimentAnalysisFunctionsApp", a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="b76ea-121">In the **Name** text box, type "SentimentAnalysisFunctionsApp" and then select the **OK** button.</span></span>
1. <span data-ttu-id="b76ea-122">W **nowy projekt** okno dialogowe, Otwórz listę rozwijaną powyżej opcje projektu i wybierz **usługi Azure Functions w wersji 2 (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="b76ea-122">In the **New Project** dialog, open the dropdown above the project options and select **Azure Functions v2 (.NET Core)**.</span></span> <span data-ttu-id="b76ea-123">Następnie wybierz **wyzwalacza Http** projektu, a następnie wybierz pozycję **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="b76ea-123">Then, select the **Http trigger** project and then select the **OK** button.</span></span>
1. <span data-ttu-id="b76ea-124">Utwórz katalog o nazwie *MLModels* w projekcie, aby zapisać modelu:</span><span class="sxs-lookup"><span data-stu-id="b76ea-124">Create a directory named *MLModels* in your project to save your model:</span></span>

    <span data-ttu-id="b76ea-125">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nad projektem i wybierz **Dodaj** > **nowy Folder**.</span><span class="sxs-lookup"><span data-stu-id="b76ea-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="b76ea-126">Wpisz "MLModels", a następnie naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="b76ea-126">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="b76ea-127">Zainstaluj **pakietu NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="b76ea-127">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="b76ea-128">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="b76ea-128">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="b76ea-129">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="b76ea-129">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="b76ea-130">Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.</span><span class="sxs-lookup"><span data-stu-id="b76ea-130">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="add-pre-built-model-to-project"></a><span data-ttu-id="b76ea-131">Dodaj wstępnie utworzonych modeli do projektu</span><span class="sxs-lookup"><span data-stu-id="b76ea-131">Add Pre-built Model To Project</span></span>

1. <span data-ttu-id="b76ea-132">Skopiuj wstępnie skompilowanych model *MLModels* folderu.</span><span class="sxs-lookup"><span data-stu-id="b76ea-132">Copy your pre-built model to the *MLModels* folder.</span></span>
1. <span data-ttu-id="b76ea-133">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy plik wstępnie utworzonych modeli, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="b76ea-133">In Solution Explorer, right-click your pre-built model file and select **Properties**.</span></span> <span data-ttu-id="b76ea-134">W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="b76ea-134">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="create-function-to-analyze-sentiment"></a><span data-ttu-id="b76ea-135">Tworzenie funkcji do analizy tonacji</span><span class="sxs-lookup"><span data-stu-id="b76ea-135">Create Function to Analyze Sentiment</span></span>

<span data-ttu-id="b76ea-136">Utwórz klasę do prognozowania wskaźniki nastrojów klientów.</span><span class="sxs-lookup"><span data-stu-id="b76ea-136">Create a class to predict sentiment.</span></span> <span data-ttu-id="b76ea-137">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="b76ea-137">Add a new class to your project:</span></span>

1. <span data-ttu-id="b76ea-138">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="b76ea-138">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="b76ea-139">W **Dodaj nowy element** okno dialogowe, wybierz opcję **funkcji platformy Azure** i zmień **nazwa** pole *AnalyzeSentiment.cs*.</span><span class="sxs-lookup"><span data-stu-id="b76ea-139">In the **Add New Item** dialog box, select **Azure Function** and change the **Name** field to *AnalyzeSentiment.cs*.</span></span> <span data-ttu-id="b76ea-140">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="b76ea-140">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="b76ea-141">W **nowej funkcji platformy Azure** okno dialogowe, wybierz opcję **wyzwalacza Http**.</span><span class="sxs-lookup"><span data-stu-id="b76ea-141">In the **New Azure Function** dialog box, select **Http Trigger**.</span></span> <span data-ttu-id="b76ea-142">Następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="b76ea-142">Then, select the **OK** button.</span></span>

    <span data-ttu-id="b76ea-143">*AnalyzeSentiment.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="b76ea-143">The *AnalyzeSentiment.cs* file opens in the code editor.</span></span> <span data-ttu-id="b76ea-144">Dodaj następujący kod `using` instrukcji na górze *GitHubIssueData.cs*:</span><span class="sxs-lookup"><span data-stu-id="b76ea-144">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

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
using Microsoft.ML;
using Microsoft.ML.Core.Data;
using Microsoft.ML.Data;
using MLNETServerless.DataModels;
```

### <a name="create-data-models"></a><span data-ttu-id="b76ea-145">Tworzenie modeli danych</span><span class="sxs-lookup"><span data-stu-id="b76ea-145">Create Data Models</span></span>

<span data-ttu-id="b76ea-146">Musisz utworzyć niektóre klasy dla danych wejściowych i prognozy.</span><span class="sxs-lookup"><span data-stu-id="b76ea-146">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="b76ea-147">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="b76ea-147">Add a new class to your project:</span></span>

1. <span data-ttu-id="b76ea-148">Utwórz katalog o nazwie *DataModels* w projekcie, aby zapisać modeli danych: W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj > Nowy Folder**.</span><span class="sxs-lookup"><span data-stu-id="b76ea-148">Create a directory named *DataModels* in your project to save your data models: In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="b76ea-149">Wpisz "DataModels", a następnie naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="b76ea-149">Type "DataModels" and hit Enter.</span></span>
2. <span data-ttu-id="b76ea-150">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy *DataModels* katalogu, a następnie wybierz **Dodaj > Nowy element**.</span><span class="sxs-lookup"><span data-stu-id="b76ea-150">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
3. <span data-ttu-id="b76ea-151">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="b76ea-151">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="b76ea-152">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="b76ea-152">Then, select the **Add** button.</span></span> <span data-ttu-id="b76ea-153">*SentimentData.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="b76ea-153">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="b76ea-154">Dodaj następujące za pomocą instrukcji na górze *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="b76ea-154">Add the following using statement to the top of *SentimentData.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="b76ea-155">Usuń istniejącą definicję klasy i Dodaj następujący kod do pliku SentimentData.cs:</span><span class="sxs-lookup"><span data-stu-id="b76ea-155">Remove the existing class definition and add the following code to the SentimentData.cs file:</span></span>

```csharp
public class SentimentData
{
    [LoadColumn(0)]
    public bool Label { get; set; }
    [LoadColumn(1)]
    public string Text { get; set; }
}
```

4. <span data-ttu-id="b76ea-156">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy *DataModels* katalogu, a następnie wybierz **Dodaj > Nowy element**.</span><span class="sxs-lookup"><span data-stu-id="b76ea-156">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="b76ea-157">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="b76ea-157">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="b76ea-158">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="b76ea-158">Then, select the **Add** button.</span></span> <span data-ttu-id="b76ea-159">*SentimentPrediction.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="b76ea-159">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="b76ea-160">Dodaj następujące za pomocą instrukcji na górze *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="b76ea-160">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="b76ea-161">Usuń istniejącą definicję klasy i Dodaj następujący kod do *SentimentPrediction.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="b76ea-161">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

```csharp
public class SentimentPrediction
{
    [ColumnName("PredictedLabel")]
    public bool Prediction { get; set; }
}
```

### <a name="add-prediction-logic"></a><span data-ttu-id="b76ea-162">Dodawanie logiki prognoz</span><span class="sxs-lookup"><span data-stu-id="b76ea-162">Add Prediction Logic</span></span>

<span data-ttu-id="b76ea-163">Zastąp istniejącą implementację programu *Uruchom* method in Class metoda *AnalyzeSentiment* klasy z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="b76ea-163">Replace the existing implementation of *Run* method in *AnalyzeSentiment* class with the following code:</span></span>

```csharp
    public static async Task<IActionResult> Run(
        [HttpTrigger(AuthorizationLevel.Function,"post", Route = null)] HttpRequest req,
        ILogger log)
    {
        log.LogInformation("C# HTTP trigger function processed a request.");

        //Create Context
        MLContext mlContext = new MLContext();

        //Load Model
        using (var fs = File.OpenRead("MLModels/sentiment_model.zip"))
        {
            model = mlContext.Model.Load(fs);
        }

        //Parse HTTP Request Body
        string requestBody = await new StreamReader(req.Body).ReadToEndAsync();
        SentimentData data = JsonConvert.DeserializeObject<SentimentData>(requestBody);

        //Create Prediction Engine
        PredictionEngine<SentimentData, SentimentPrediction> predictionEngine = model.CreatePredictionEngine<SentimentData, SentimentPrediction>(mlContext);

        //Make Prediction
        SentimentPrediction prediction = predictionEngine.Predict(data);

        //Convert prediction to string
        string isToxic = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";

        //Return Prediction
        return (ActionResult)new OkObjectResult(isToxic);
    }
}
```

## <a name="test-locally"></a><span data-ttu-id="b76ea-164">Przetestować ją lokalnie</span><span class="sxs-lookup"><span data-stu-id="b76ea-164">Test Locally</span></span>

<span data-ttu-id="b76ea-165">Teraz, że wszystko zostało skonfigurowane, nadszedł czas na przetestowanie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="b76ea-165">Now that everything is set up, it's time to test the application:</span></span>

1. <span data-ttu-id="b76ea-166">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="b76ea-166">Run the application</span></span>
1. <span data-ttu-id="b76ea-167">Otwórz program PowerShell, a następnie wprowadź kod w wierszu polecenia, gdzie jest to port aplikacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="b76ea-167">Open PowerShell and enter the code into the prompt where PORT is the port your application is running on.</span></span> <span data-ttu-id="b76ea-168">Zazwyczaj port jest 7071.</span><span class="sxs-lookup"><span data-stu-id="b76ea-168">Typically the port is 7071.</span></span> 

```powershell
Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{Text="This is a very rude movie"} | ConvertTo-Json) -ContentType "application/json"
```

<span data-ttu-id="b76ea-169">Jeśli to się powiedzie, dane wyjściowe powinny wyglądać podobnie do poniższy tekst:</span><span class="sxs-lookup"><span data-stu-id="b76ea-169">If successful, the output should look similar to the text below:</span></span>

```powershell
Toxic
```

<span data-ttu-id="b76ea-170">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="b76ea-170">Congratulations!</span></span> <span data-ttu-id="b76ea-171">Zostały pomyślnie obsłużone model do przewidywania przyszłych zdarzeń za pośrednictwem Internetu przy użyciu funkcji platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="b76ea-171">You have successfully served your model to make predictions over the internet using an Azure Function.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b76ea-172">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="b76ea-172">Next Steps</span></span>

- [<span data-ttu-id="b76ea-173">Wdrażanie na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="b76ea-173">Deploy to Azure</span></span>](/azure/azure-functions/functions-develop-vs#publish-to-azure)