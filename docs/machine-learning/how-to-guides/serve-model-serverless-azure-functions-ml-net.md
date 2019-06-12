---
title: Wdrażanie modelu w usłudze Azure Functions
description: Obsługiwać model analizy tonacji strukturze ML.NET uczenia maszynowego do przewidywania w Internecie przy użyciu usługi Azure Functions
ms.date: 06/11/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 7df7a6f9fcc5a4702171e1aac4b6b67e0c343748
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025981"
---
# <a name="deploy-a-model-to-azure-functions"></a><span data-ttu-id="9e411-103">Wdrażanie modelu w usłudze Azure Functions</span><span class="sxs-lookup"><span data-stu-id="9e411-103">Deploy a model to Azure Functions</span></span>

<span data-ttu-id="9e411-104">Dowiedz się, jak wdrożyć wstępnie przeszkolonych strukturze ML.NET usługi machine learning model do przewidywania za pośrednictwem protokołu HTTP za pośrednictwem środowiska bez użycia serwera usługi Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="9e411-104">Learn how to deploy a pre-trained ML.NET machine learning model for predictions over HTTP through an Azure Functions serverless environment.</span></span>

> [!NOTE]
> <span data-ttu-id="9e411-105">`PredictionEnginePool` rozszerzenie usługi jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="9e411-105">`PredictionEnginePool` service extension is currently in preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9e411-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="9e411-106">Prerequisites</span></span>

- <span data-ttu-id="9e411-107">[Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) za pomocą obciążenia "Programowanie dla wielu platform .NET Core" i "Programowanie na platformie Azure" zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="9e411-107">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload and "Azure development" installed.</span></span>
- <span data-ttu-id="9e411-108">1.0.28+ wersji pakietu NuGet Microsoft.NET.Sdk.Functions.</span><span class="sxs-lookup"><span data-stu-id="9e411-108">Microsoft.NET.Sdk.Functions NuGet Package version 1.0.28+.</span></span>
- [<span data-ttu-id="9e411-109">Narzędzia usługi Azure Functions</span><span class="sxs-lookup"><span data-stu-id="9e411-109">Azure Functions Tools</span></span>](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- <span data-ttu-id="9e411-110">Program PowerShell</span><span class="sxs-lookup"><span data-stu-id="9e411-110">Powershell</span></span>
- <span data-ttu-id="9e411-111">Wstępnie uczonego modelu.</span><span class="sxs-lookup"><span data-stu-id="9e411-111">Pre-trained model.</span></span> <span data-ttu-id="9e411-112">Użyj [samouczek analizy tonacji w strukturze ML.NET](../tutorials/sentiment-analysis.md) do stworzenia własnego modelu lub pobrać [modelu uczenia maszynowego analizy tonacji wstępnie przeszkolonych](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="9e411-112">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-azure-functions-project"></a><span data-ttu-id="9e411-113">Tworzenie projektu usługi Azure Functions</span><span class="sxs-lookup"><span data-stu-id="9e411-113">Create Azure Functions project</span></span>

1. <span data-ttu-id="9e411-114">Otwórz program Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="9e411-114">Open Visual Studio 2017.</span></span> <span data-ttu-id="9e411-115">Wybierz **pliku** > **New** > **projektu** z paska menu.</span><span class="sxs-lookup"><span data-stu-id="9e411-115">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="9e411-116">W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#**  węzła następuje **chmury** węzła.</span><span class="sxs-lookup"><span data-stu-id="9e411-116">In the **New Project** dialog, select the **Visual C#** node followed by the **Cloud** node.</span></span> <span data-ttu-id="9e411-117">Następnie wybierz pozycję **usługi Azure Functions** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="9e411-117">Then select the **Azure Functions** project template.</span></span> <span data-ttu-id="9e411-118">W **nazwa** pole tekstowe, wpisz "SentimentAnalysisFunctionsApp", a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9e411-118">In the **Name** text box, type "SentimentAnalysisFunctionsApp" and then select the **OK** button.</span></span>
1. <span data-ttu-id="9e411-119">W **nowy projekt** okno dialogowe, Otwórz listę rozwijaną powyżej opcje projektu i wybierz **usługi Azure Functions w wersji 2 (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="9e411-119">In the **New Project** dialog, open the dropdown above the project options and select **Azure Functions v2 (.NET Core)**.</span></span> <span data-ttu-id="9e411-120">Następnie wybierz **wyzwalacza Http** projektu, a następnie wybierz pozycję **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9e411-120">Then, select the **Http trigger** project and then select the **OK** button.</span></span>
1. <span data-ttu-id="9e411-121">Utwórz katalog o nazwie *MLModels* w projekcie, aby zapisać modelu:</span><span class="sxs-lookup"><span data-stu-id="9e411-121">Create a directory named *MLModels* in your project to save your model:</span></span>

    <span data-ttu-id="9e411-122">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nad projektem i wybierz **Dodaj** > **nowy Folder**.</span><span class="sxs-lookup"><span data-stu-id="9e411-122">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="9e411-123">Wpisz "MLModels", a następnie naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="9e411-123">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="9e411-124">Zainstaluj **pakietu NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="9e411-124">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="9e411-125">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="9e411-125">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="9e411-126">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9e411-126">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="9e411-127">Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.</span><span class="sxs-lookup"><span data-stu-id="9e411-127">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="9e411-128">Zainstaluj **pakietu NuGet Microsoft.Azure.Functions.Extensions**:</span><span class="sxs-lookup"><span data-stu-id="9e411-128">Install the **Microsoft.Azure.Functions.Extensions NuGet Package**:</span></span>

    <span data-ttu-id="9e411-129">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="9e411-129">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="9e411-130">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.Azure.Functions.Extensions**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9e411-130">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Azure.Functions.Extensions**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="9e411-131">Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.</span><span class="sxs-lookup"><span data-stu-id="9e411-131">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="9e411-132">Zainstaluj **pakietu NuGet Microsoft.Extensions.ML**:</span><span class="sxs-lookup"><span data-stu-id="9e411-132">Install the **Microsoft.Extensions.ML NuGet Package**:</span></span>

    <span data-ttu-id="9e411-133">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="9e411-133">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="9e411-134">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.Extensions.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9e411-134">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="9e411-135">Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.</span><span class="sxs-lookup"><span data-stu-id="9e411-135">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="9e411-136">Aktualizacja **pakietu NuGet Microsoft.NET.Sdk.Functions** do wersji 1.0.28:</span><span class="sxs-lookup"><span data-stu-id="9e411-136">Update the **Microsoft.NET.Sdk.Functions NuGet Package** to version 1.0.28:</span></span>

    <span data-ttu-id="9e411-137">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="9e411-137">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="9e411-138">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę zainstalowane, wyszukaj **Microsoft.NET.Sdk.Functions**, wybierz pakiet, na liście, wybierz 1.0.28 lub później z listy rozwijanej wersję i wybierz **aktualizacji**  przycisku.</span><span class="sxs-lookup"><span data-stu-id="9e411-138">Choose "nuget.org" as the Package source, select the Installed tab, search for **Microsoft.NET.Sdk.Functions**, select that package in the list, select 1.0.28 or later from the Version dropdown, and select the **Update** button.</span></span> <span data-ttu-id="9e411-139">Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.</span><span class="sxs-lookup"><span data-stu-id="9e411-139">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="add-pre-trained-model-to-project"></a><span data-ttu-id="9e411-140">Dodaj wstępnie uczonego modelu do projektu</span><span class="sxs-lookup"><span data-stu-id="9e411-140">Add pre-trained model to project</span></span>

1. <span data-ttu-id="9e411-141">Skopiuj wstępnie skompilowanych model *MLModels* folderu.</span><span class="sxs-lookup"><span data-stu-id="9e411-141">Copy your pre-built model to the *MLModels* folder.</span></span>
1. <span data-ttu-id="9e411-142">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy plik wstępnie utworzonych modeli, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="9e411-142">In Solution Explorer, right-click your pre-built model file and select **Properties**.</span></span> <span data-ttu-id="9e411-143">W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="9e411-143">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="create-azure-function-to-analyze-sentiment"></a><span data-ttu-id="9e411-144">Tworzenie funkcji platformy Azure analizować tonację</span><span class="sxs-lookup"><span data-stu-id="9e411-144">Create Azure Function to analyze sentiment</span></span>

<span data-ttu-id="9e411-145">Utwórz klasę do prognozowania wskaźniki nastrojów klientów.</span><span class="sxs-lookup"><span data-stu-id="9e411-145">Create a class to predict sentiment.</span></span> <span data-ttu-id="9e411-146">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="9e411-146">Add a new class to your project:</span></span>

1. <span data-ttu-id="9e411-147">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="9e411-147">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="9e411-148">W **Dodaj nowy element** okno dialogowe, wybierz opcję **funkcji platformy Azure** i zmień **nazwa** pole *AnalyzeSentiment.cs*.</span><span class="sxs-lookup"><span data-stu-id="9e411-148">In the **Add New Item** dialog box, select **Azure Function** and change the **Name** field to *AnalyzeSentiment.cs*.</span></span> <span data-ttu-id="9e411-149">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9e411-149">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="9e411-150">W **nowej funkcji platformy Azure** okno dialogowe, wybierz opcję **wyzwalacza Http**.</span><span class="sxs-lookup"><span data-stu-id="9e411-150">In the **New Azure Function** dialog box, select **Http Trigger**.</span></span> <span data-ttu-id="9e411-151">Następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9e411-151">Then, select the **OK** button.</span></span>

    <span data-ttu-id="9e411-152">*AnalyzeSentiment.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="9e411-152">The *AnalyzeSentiment.cs* file opens in the code editor.</span></span> <span data-ttu-id="9e411-153">Dodaj następujący kod `using` instrukcji na górze *AnalyzeSentiment.cs*:</span><span class="sxs-lookup"><span data-stu-id="9e411-153">Add the following `using` statement to the top of *AnalyzeSentiment.cs*:</span></span>

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

    <span data-ttu-id="9e411-154">Domyślnie `AnalyzeSentiment` klasa jest `static`.</span><span class="sxs-lookup"><span data-stu-id="9e411-154">By default, the `AnalyzeSentiment` class is `static`.</span></span> <span data-ttu-id="9e411-155">Upewnij się usunąć `static` — słowo kluczowe z poziomu definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="9e411-155">Make sure to remove the `static` keyword from the class definition.</span></span>

    ```csharp
    public class AnalyzeSentiment
    {
    
    }
    ```

## <a name="create-data-models"></a><span data-ttu-id="9e411-156">Tworzenie modeli danych</span><span class="sxs-lookup"><span data-stu-id="9e411-156">Create data models</span></span>

<span data-ttu-id="9e411-157">Musisz utworzyć niektóre klasy dla danych wejściowych i prognozy.</span><span class="sxs-lookup"><span data-stu-id="9e411-157">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="9e411-158">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="9e411-158">Add a new class to your project:</span></span>

1. <span data-ttu-id="9e411-159">Utwórz katalog o nazwie *DataModels* w projekcie, aby zapisać modeli danych: W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj > Nowy Folder**.</span><span class="sxs-lookup"><span data-stu-id="9e411-159">Create a directory named *DataModels* in your project to save your data models: In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="9e411-160">Wpisz "DataModels", a następnie naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="9e411-160">Type "DataModels" and hit Enter.</span></span>
2. <span data-ttu-id="9e411-161">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy *DataModels* katalogu, a następnie wybierz **Dodaj > Nowy element**.</span><span class="sxs-lookup"><span data-stu-id="9e411-161">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
3. <span data-ttu-id="9e411-162">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="9e411-162">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="9e411-163">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9e411-163">Then, select the **Add** button.</span></span> 

    <span data-ttu-id="9e411-164">*SentimentData.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="9e411-164">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="9e411-165">Dodaj następujące za pomocą instrukcji na górze *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="9e411-165">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="9e411-166">Usuń istniejącą definicję klasy i Dodaj następujący kod do *SentimentData.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="9e411-166">Remove the existing class definition and add the following code to the *SentimentData.cs* file:</span></span>
    
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

4. <span data-ttu-id="9e411-167">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy *DataModels* katalogu, a następnie wybierz **Dodaj > Nowy element**.</span><span class="sxs-lookup"><span data-stu-id="9e411-167">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="9e411-168">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="9e411-168">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="9e411-169">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9e411-169">Then, select the **Add** button.</span></span> <span data-ttu-id="9e411-170">*SentimentPrediction.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="9e411-170">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="9e411-171">Dodaj następujące za pomocą instrukcji na górze *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="9e411-171">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="9e411-172">Usuń istniejącą definicję klasy i Dodaj następujący kod do *SentimentPrediction.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="9e411-172">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="9e411-173">`SentimentPrediction` dziedziczy `SentimentData` zapewniającą dostęp do oryginalnych danych przechowywanych w `SentimentText` właściwości, a także dane wyjściowe generowane przez model.</span><span class="sxs-lookup"><span data-stu-id="9e411-173">`SentimentPrediction` inherits from `SentimentData` which provides access to the original data in the `SentimentText` property as well as the output generated by the model.</span></span>

## <a name="register-predictionenginepool-service"></a><span data-ttu-id="9e411-174">Zarejestruj usługę PredictionEnginePool</span><span class="sxs-lookup"><span data-stu-id="9e411-174">Register PredictionEnginePool service</span></span>

<span data-ttu-id="9e411-175">Do pojedynczego prognozowania, należy użyć [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="9e411-175">To make a single prediction, use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="9e411-176">Aby można było używać [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602) w aplikacji należy go utworzyć, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="9e411-176">In order to use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) in your application you must create it when it's needed.</span></span> <span data-ttu-id="9e411-177">W takim przypadku najlepszym rozwiązaniem należy wziąć pod uwagę jest iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="9e411-177">In that case, a best practice to consider is dependency injection.</span></span>

<span data-ttu-id="9e411-178">Kliknięcie następującego łącza zawiera więcej informacji, jeśli chcesz dowiedzieć się więcej na temat [wstrzykiwanie zależności](https://en.wikipedia.org/wiki/Dependency_injection).</span><span class="sxs-lookup"><span data-stu-id="9e411-178">The following link provides more information if you want to learn about [dependency injection](https://en.wikipedia.org/wiki/Dependency_injection).</span></span>

1. <span data-ttu-id="9e411-179">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="9e411-179">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="9e411-180">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *Startup.cs*.</span><span class="sxs-lookup"><span data-stu-id="9e411-180">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *Startup.cs*.</span></span> <span data-ttu-id="9e411-181">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9e411-181">Then, select the **Add** button.</span></span> 

    <span data-ttu-id="9e411-182">*Startup.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="9e411-182">The *Startup.cs* file opens in the code editor.</span></span> <span data-ttu-id="9e411-183">Dodaj następujące za pomocą instrukcji na górze *Startup.cs*:</span><span class="sxs-lookup"><span data-stu-id="9e411-183">Add the following using statement to the top of *Startup.cs*:</span></span>

    ```csharp
    using Microsoft.Azure.WebJobs;
    using Microsoft.Azure.WebJobs.Hosting;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    <span data-ttu-id="9e411-184">Usuń istniejący kod poniżej używając instrukcji i Dodaj następujący kod do *Startup.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="9e411-184">Remove the existing code below the using statements and add the following code to the *Startup.cs* file:</span></span>

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

<span data-ttu-id="9e411-185">Na wysokim poziomie ten kod inicjalizuje obiektami i usługami, automatycznie, gdy jest to wymagane przez aplikację, nie trzeba to zrobić ręcznie.</span><span class="sxs-lookup"><span data-stu-id="9e411-185">At a high level, this code initializes the objects and services automatically when requested by the application instead of having to manually do it.</span></span>

> [!WARNING]
> <span data-ttu-id="9e411-186">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nie jest metodą o bezpiecznych wątkach.</span><span class="sxs-lookup"><span data-stu-id="9e411-186">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="9e411-187">Zwiększona wydajność i bezpieczeństwo wątków, użyj `PredictionEnginePool` usługa, która tworzy [ `ObjectPool` ](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) z `PredictionEngine` obiekty do użytku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9e411-187">For improved performance and thread safety, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of `PredictionEngine` objects for application use.</span></span> 

## <a name="load-the-model-into-the-function"></a><span data-ttu-id="9e411-188">Ładowanie modelu do funkcji</span><span class="sxs-lookup"><span data-stu-id="9e411-188">Load the model into the function</span></span>

<span data-ttu-id="9e411-189">Wstaw następujący kod wewnątrz *AnalyzeSentiment* klasy:</span><span class="sxs-lookup"><span data-stu-id="9e411-189">Insert the following code inside the *AnalyzeSentiment* class:</span></span>

```csharp
private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

// AnalyzeSentiment class constructor
public AnalyzeSentiment(PredictionEnginePool<SentimentData, SentimentPrediction> predictionEnginePool)
{
    _predictionEnginePool = predictionEnginePool;
}
```

<span data-ttu-id="9e411-190">Ten kod przypisuje `PredictionEnginePool` przez przekazanie jej do funkcji konstruktora, który otrzymujesz za pomocą iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="9e411-190">This code assigns the `PredictionEnginePool` by passing it to the function's constructor which you get via dependency injection.</span></span>

## <a name="use-the-model-to-make-predictions"></a><span data-ttu-id="9e411-191">Użyj modelu do prognozowania</span><span class="sxs-lookup"><span data-stu-id="9e411-191">Use the model to make predictions</span></span>

<span data-ttu-id="9e411-192">Zastąp istniejącą implementację programu *Uruchom* method in Class metoda *AnalyzeSentiment* klasy z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="9e411-192">Replace the existing implementation of *Run* method in *AnalyzeSentiment* class with the following code:</span></span>

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

<span data-ttu-id="9e411-193">Gdy `Run` metoda jest wykonywana, dane przychodzące z żądania HTTP jest przeprowadzona i używany jako dane wejściowe na potrzeby `PredictionEnginePool`.</span><span class="sxs-lookup"><span data-stu-id="9e411-193">When the `Run` method executes, the incoming data from the HTTP request is deserialized and used as input for the `PredictionEnginePool`.</span></span> <span data-ttu-id="9e411-194">`Predict` Wywoływana jest metoda następnie generują przewidywanie i zwracają wynik do użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9e411-194">The `Predict` method is then called to generate a prediction and return the result to the user.</span></span> 

## <a name="test-locally"></a><span data-ttu-id="9e411-195">Przetestować ją lokalnie</span><span class="sxs-lookup"><span data-stu-id="9e411-195">Test locally</span></span>

<span data-ttu-id="9e411-196">Teraz, że wszystko zostało skonfigurowane, nadszedł czas na przetestowanie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="9e411-196">Now that everything is set up, it's time to test the application:</span></span>

1. <span data-ttu-id="9e411-197">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="9e411-197">Run the application</span></span>
1. <span data-ttu-id="9e411-198">Otwórz program PowerShell, a następnie wprowadź kod w wierszu polecenia, gdzie jest to port aplikacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="9e411-198">Open PowerShell and enter the code into the prompt where PORT is the port your application is running on.</span></span> <span data-ttu-id="9e411-199">Zazwyczaj port jest 7071.</span><span class="sxs-lookup"><span data-stu-id="9e411-199">Typically the port is 7071.</span></span>

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="9e411-200">Jeśli to się powiedzie, dane wyjściowe powinny wyglądać podobnie do poniższy tekst:</span><span class="sxs-lookup"><span data-stu-id="9e411-200">If successful, the output should look similar to the text below:</span></span>
    
    ```powershell
    Negative
    ```

<span data-ttu-id="9e411-201">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="9e411-201">Congratulations!</span></span> <span data-ttu-id="9e411-202">Zostały pomyślnie obsłużone model do przewidywania przyszłych zdarzeń za pośrednictwem Internetu przy użyciu funkcji platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="9e411-202">You have successfully served your model to make predictions over the internet using an Azure Function.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9e411-203">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="9e411-203">Next Steps</span></span>

- [<span data-ttu-id="9e411-204">Wdrażanie na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="9e411-204">Deploy to Azure</span></span>](/azure/azure-functions/functions-develop-vs#publish-to-azure)
