---
title: Wdrażanie modelu w usłudze Azure Functions
description: Obsłużymy model uczenia maszynowego ML.NET tonacji Analysis na potrzeby przewidywania przez Internet przy użyciu Azure Functions
ms.date: 09/12/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 4f805c638df9e60160c27fa08995ce393e59d007
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774527"
---
# <a name="deploy-a-model-to-azure-functions"></a><span data-ttu-id="0978e-103">Wdrażanie modelu w usłudze Azure Functions</span><span class="sxs-lookup"><span data-stu-id="0978e-103">Deploy a model to Azure Functions</span></span>

<span data-ttu-id="0978e-104">Dowiedz się, jak wdrożyć wstępnie szkolony model uczenia maszynowego ML.NET na potrzeby prognozowania za pośrednictwem protokołu HTTP za pośrednictwem środowiska bezserwerowego Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="0978e-104">Learn how to deploy a pre-trained ML.NET machine learning model for predictions over HTTP through an Azure Functions serverless environment.</span></span>

> [!NOTE]
> <span data-ttu-id="0978e-105">rozszerzenie usługi `PredictionEnginePool` jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="0978e-105">`PredictionEnginePool` service extension is currently in preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0978e-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="0978e-106">Prerequisites</span></span>

- <span data-ttu-id="0978e-107">[Program Visual Studio 2017 w wersji 15,6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowaną funkcją "Programowanie dla wielu platform w środowisku .NET Core" i "Programowanie na platformie Azure".</span><span class="sxs-lookup"><span data-stu-id="0978e-107">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload and "Azure development" installed.</span></span>
- <span data-ttu-id="0978e-108">Microsoft. NET. Sdk. Functions pakiet NuGet w wersji 1.0.28 +.</span><span class="sxs-lookup"><span data-stu-id="0978e-108">Microsoft.NET.Sdk.Functions NuGet Package version 1.0.28+.</span></span>
- [<span data-ttu-id="0978e-109">Narzędzia Azure Functions</span><span class="sxs-lookup"><span data-stu-id="0978e-109">Azure Functions Tools</span></span>](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- <span data-ttu-id="0978e-110">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="0978e-110">Powershell</span></span>
- <span data-ttu-id="0978e-111">Model wstępnie szkolony.</span><span class="sxs-lookup"><span data-stu-id="0978e-111">Pre-trained model.</span></span> <span data-ttu-id="0978e-112">Użyj [samouczka analiza tonacji ml.NET](../tutorials/sentiment-analysis.md) , aby skompilować własny model lub pobrać ten [wstępnie szkolony model uczenia maszynowego analizy tonacji](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="0978e-112">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-azure-functions-project"></a><span data-ttu-id="0978e-113">Utwórz projekt Azure Functions</span><span class="sxs-lookup"><span data-stu-id="0978e-113">Create Azure Functions project</span></span>

1. <span data-ttu-id="0978e-114">Otwórz program Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="0978e-114">Open Visual Studio 2017.</span></span> <span data-ttu-id="0978e-115">Wybierz pozycję **plik** > **Nowy** > **projekt** na pasku menu.</span><span class="sxs-lookup"><span data-stu-id="0978e-115">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="0978e-116">W oknie dialogowym **Nowy projekt** wybierz węzeł **wizualizacji C#**  , a następnie węzeł **chmury** .</span><span class="sxs-lookup"><span data-stu-id="0978e-116">In the **New Project** dialog, select the **Visual C#** node followed by the **Cloud** node.</span></span> <span data-ttu-id="0978e-117">Następnie wybierz szablon projektu **Azure Functions** .</span><span class="sxs-lookup"><span data-stu-id="0978e-117">Then select the **Azure Functions** project template.</span></span> <span data-ttu-id="0978e-118">W polu tekstowym **Nazwa** wpisz "SentimentAnalysisFunctionsApp", a następnie wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="0978e-118">In the **Name** text box, type "SentimentAnalysisFunctionsApp" and then select the **OK** button.</span></span>
1. <span data-ttu-id="0978e-119">W oknie dialogowym **Nowy projekt** Otwórz listę rozwijaną nad opcjami projektu i wybierz pozycję **Azure Functions v2 (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="0978e-119">In the **New Project** dialog, open the dropdown above the project options and select **Azure Functions v2 (.NET Core)**.</span></span> <span data-ttu-id="0978e-120">Następnie wybierz projekt **wyzwalacza http** , a następnie wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="0978e-120">Then, select the **Http trigger** project and then select the **OK** button.</span></span>
1. <span data-ttu-id="0978e-121">Utwórz katalog o nazwie *MLModels* w projekcie, aby zapisać model:</span><span class="sxs-lookup"><span data-stu-id="0978e-121">Create a directory named *MLModels* in your project to save your model:</span></span>

    <span data-ttu-id="0978e-122">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **dodaj** **Nowy folder** > .</span><span class="sxs-lookup"><span data-stu-id="0978e-122">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="0978e-123">Wpisz "MLModels" i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="0978e-123">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="0978e-124">Zainstaluj **pakiet NuGet Microsoft.ml**:</span><span class="sxs-lookup"><span data-stu-id="0978e-124">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="0978e-125">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="0978e-125">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="0978e-126">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, Wyszukaj pozycję **Microsoft.ml**, wybierz ten pakiet z listy, a następnie wybierz przycisk **Instaluj** .</span><span class="sxs-lookup"><span data-stu-id="0978e-126">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="0978e-127">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="0978e-127">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="0978e-128">Zainstaluj **pakiet NuGet Microsoft. Azure. Functions. Extensions**:</span><span class="sxs-lookup"><span data-stu-id="0978e-128">Install the **Microsoft.Azure.Functions.Extensions NuGet Package**:</span></span>

    <span data-ttu-id="0978e-129">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="0978e-129">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="0978e-130">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, Wyszukaj pozycję **Microsoft. Azure. Functions. Extensions**, wybierz ten pakiet z listy, a następnie wybierz przycisk **Instaluj** .</span><span class="sxs-lookup"><span data-stu-id="0978e-130">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Azure.Functions.Extensions**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="0978e-131">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="0978e-131">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="0978e-132">Zainstaluj **pakiet NuGet Microsoft.Extensions.ml**:</span><span class="sxs-lookup"><span data-stu-id="0978e-132">Install the **Microsoft.Extensions.ML NuGet Package**:</span></span>

    <span data-ttu-id="0978e-133">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="0978e-133">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="0978e-134">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, Wyszukaj pozycję **Microsoft.Extensions.ml**, wybierz ten pakiet z listy, a następnie wybierz przycisk **Instaluj** .</span><span class="sxs-lookup"><span data-stu-id="0978e-134">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="0978e-135">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="0978e-135">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="0978e-136">Zaktualizuj **pakiet NuGet Microsoft. NET. Sdk. Functions** do wersji 1.0.28 +:</span><span class="sxs-lookup"><span data-stu-id="0978e-136">Update the **Microsoft.NET.Sdk.Functions NuGet Package** to version 1.0.28+:</span></span>

    <span data-ttu-id="0978e-137">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="0978e-137">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="0978e-138">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę zainstalowane, Wyszukaj pozycję **Microsoft. NET. Sdk. Functions**, zaznacz ten pakiet na liście, wybierz pozycję 1.0.28 lub nowszy z listy rozwijanej wersja i wybierz przycisk **Aktualizuj** .</span><span class="sxs-lookup"><span data-stu-id="0978e-138">Choose "nuget.org" as the Package source, select the Installed tab, search for **Microsoft.NET.Sdk.Functions**, select that package in the list, select 1.0.28 or later from the Version dropdown, and select the **Update** button.</span></span> <span data-ttu-id="0978e-139">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="0978e-139">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="add-pre-trained-model-to-project"></a><span data-ttu-id="0978e-140">Dodaj wstępnie szkolony model do projektu</span><span class="sxs-lookup"><span data-stu-id="0978e-140">Add pre-trained model to project</span></span>

1. <span data-ttu-id="0978e-141">Skopiuj wstępnie utworzony model do folderu *MLModels* .</span><span class="sxs-lookup"><span data-stu-id="0978e-141">Copy your pre-built model to the *MLModels* folder.</span></span>
1. <span data-ttu-id="0978e-142">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy wstępnie utworzony plik modelu i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="0978e-142">In Solution Explorer, right-click your pre-built model file and select **Properties**.</span></span> <span data-ttu-id="0978e-143">W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="0978e-143">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="create-azure-function-to-analyze-sentiment"></a><span data-ttu-id="0978e-144">Utwórz funkcję platformy Azure, aby analizować tonacji</span><span class="sxs-lookup"><span data-stu-id="0978e-144">Create Azure Function to analyze sentiment</span></span>

<span data-ttu-id="0978e-145">Utwórz klasę do przewidywania tonacji.</span><span class="sxs-lookup"><span data-stu-id="0978e-145">Create a class to predict sentiment.</span></span> <span data-ttu-id="0978e-146">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="0978e-146">Add a new class to your project:</span></span>

1. <span data-ttu-id="0978e-147">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz pozycję **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="0978e-147">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="0978e-148">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Funkcja platformy Azure** i zmień wartość pola **Nazwa** na *AnalyzeSentiment.cs*.</span><span class="sxs-lookup"><span data-stu-id="0978e-148">In the **Add New Item** dialog box, select **Azure Function** and change the **Name** field to *AnalyzeSentiment.cs*.</span></span> <span data-ttu-id="0978e-149">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="0978e-149">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="0978e-150">W oknie dialogowym **Nowa funkcja platformy Azure** wybierz pozycję **wyzwalacz http**.</span><span class="sxs-lookup"><span data-stu-id="0978e-150">In the **New Azure Function** dialog box, select **Http Trigger**.</span></span> <span data-ttu-id="0978e-151">Następnie wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="0978e-151">Then, select the **OK** button.</span></span>

    <span data-ttu-id="0978e-152">Plik *AnalyzeSentiment.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="0978e-152">The *AnalyzeSentiment.cs* file opens in the code editor.</span></span> <span data-ttu-id="0978e-153">Dodaj następującą instrukcję `using` na początku *AnalyzeSentiment.cs*:</span><span class="sxs-lookup"><span data-stu-id="0978e-153">Add the following `using` statement to the top of *AnalyzeSentiment.cs*:</span></span>

    [!code-csharp [AnalyzeUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L1-L11)]

    <span data-ttu-id="0978e-154">Domyślnie Klasa `AnalyzeSentiment` jest `static`.</span><span class="sxs-lookup"><span data-stu-id="0978e-154">By default, the `AnalyzeSentiment` class is `static`.</span></span> <span data-ttu-id="0978e-155">Upewnij się, że usunięto słowo kluczowe `static` z definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="0978e-155">Make sure to remove the `static` keyword from the class definition.</span></span>

    ```csharp
    public class AnalyzeSentiment
    {

    }
    ```

## <a name="create-data-models"></a><span data-ttu-id="0978e-156">Tworzenie modeli danych</span><span class="sxs-lookup"><span data-stu-id="0978e-156">Create data models</span></span>

<span data-ttu-id="0978e-157">Należy utworzyć klasy dla danych wejściowych i prognoz.</span><span class="sxs-lookup"><span data-stu-id="0978e-157">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="0978e-158">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="0978e-158">Add a new class to your project:</span></span>

1. <span data-ttu-id="0978e-159">Utwórz katalog o nazwie *Datamodels* w projekcie, aby zapisać modele danych: w Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj > nowy folder**.</span><span class="sxs-lookup"><span data-stu-id="0978e-159">Create a directory named *DataModels* in your project to save your data models: In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="0978e-160">Wpisz "datamodels" i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="0978e-160">Type "DataModels" and hit Enter.</span></span>
2. <span data-ttu-id="0978e-161">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy katalog *Datamodels* , a następnie wybierz pozycję **Dodaj > nowy element**.</span><span class="sxs-lookup"><span data-stu-id="0978e-161">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
3. <span data-ttu-id="0978e-162">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="0978e-162">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="0978e-163">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="0978e-163">Then, select the **Add** button.</span></span>

    <span data-ttu-id="0978e-164">Plik *SentimentData.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="0978e-164">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="0978e-165">Dodaj następującą instrukcję using na początku *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="0978e-165">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp [SentimentDataUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L1)]

    <span data-ttu-id="0978e-166">Usuń istniejącą definicję klasy i Dodaj następujący kod do pliku *SentimentData.cs* :</span><span class="sxs-lookup"><span data-stu-id="0978e-166">Remove the existing class definition and add the following code to the *SentimentData.cs* file:</span></span>

    [!code-csharp [SentimentData](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L5-L13)]

4. <span data-ttu-id="0978e-167">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy katalog *Datamodels* , a następnie wybierz pozycję **Dodaj > nowy element**.</span><span class="sxs-lookup"><span data-stu-id="0978e-167">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="0978e-168">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="0978e-168">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="0978e-169">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="0978e-169">Then, select the **Add** button.</span></span> <span data-ttu-id="0978e-170">Plik *SentimentPrediction.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="0978e-170">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="0978e-171">Dodaj następującą instrukcję using na początku *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="0978e-171">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    [!code-csharp [SentimentPredictionUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L1)]

    <span data-ttu-id="0978e-172">Usuń istniejącą definicję klasy i Dodaj następujący kod do pliku *SentimentPrediction.cs* :</span><span class="sxs-lookup"><span data-stu-id="0978e-172">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    [!code-csharp [SentimentPrediction](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L5-L14)]

    <span data-ttu-id="0978e-173">`SentimentPrediction` dziedziczy po `SentimentData`, który zapewnia dostęp do oryginalnych danych we właściwości `SentimentText`, a także dane wyjściowe generowane przez model.</span><span class="sxs-lookup"><span data-stu-id="0978e-173">`SentimentPrediction` inherits from `SentimentData` which provides access to the original data in the `SentimentText` property as well as the output generated by the model.</span></span>

## <a name="register-predictionenginepool-service"></a><span data-ttu-id="0978e-174">Zarejestruj usługę PredictionEnginePool</span><span class="sxs-lookup"><span data-stu-id="0978e-174">Register PredictionEnginePool service</span></span>

<span data-ttu-id="0978e-175">Aby wykonać pojedyncze prognozowanie, należy utworzyć [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="0978e-175">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="0978e-176">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nie jest bezpieczny wątkowo.</span><span class="sxs-lookup"><span data-stu-id="0978e-176">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="0978e-177">Ponadto należy utworzyć wystąpienie go wszędzie tam, gdzie jest to potrzebne w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0978e-177">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="0978e-178">Gdy aplikacja zostanie powiększona, ten proces może być niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="0978e-178">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="0978e-179">Aby zwiększyć wydajność i bezpieczeństwo wątków, użyj kombinacji iniekcji zależności i usługi `PredictionEnginePool`, która tworzy [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) obiektów do użycia w całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0978e-179">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

<span data-ttu-id="0978e-180">Poniższy link zawiera więcej informacji, jeśli chcesz dowiedzieć się więcej o [iniekcji zależności](https://en.wikipedia.org/wiki/Dependency_injection).</span><span class="sxs-lookup"><span data-stu-id="0978e-180">The following link provides more information if you want to learn more about [dependency injection](https://en.wikipedia.org/wiki/Dependency_injection).</span></span>

1. <span data-ttu-id="0978e-181">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz pozycję **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="0978e-181">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="0978e-182">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *Startup.cs*.</span><span class="sxs-lookup"><span data-stu-id="0978e-182">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *Startup.cs*.</span></span> <span data-ttu-id="0978e-183">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="0978e-183">Then, select the **Add** button.</span></span>

    <span data-ttu-id="0978e-184">Plik *Startup.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="0978e-184">The *Startup.cs* file opens in the code editor.</span></span> <span data-ttu-id="0978e-185">Dodaj następującą instrukcję using na początku *Startup.cs*:</span><span class="sxs-lookup"><span data-stu-id="0978e-185">Add the following using statement to the top of *Startup.cs*:</span></span>

    ```csharp
    using Microsoft.Azure.Functions.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    <span data-ttu-id="0978e-186">Usuń istniejący kod poniżej instrukcji using i Dodaj następujący kod do pliku *Startup.cs* :</span><span class="sxs-lookup"><span data-stu-id="0978e-186">Remove the existing code below the using statements and add the following code to the *Startup.cs* file:</span></span>

    ```csharp
    [assembly: FunctionsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        public class Startup : FunctionsStartup
        {
            public override void Configure(IFunctionsHostBuilder builder)
            {
                builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
                    .FromFile(modelName: "SentimentAnalysisModel", filePath:"MLModels/sentiment_model.zip", watchForChanges: true);
            }
        }
    }
    ```

<span data-ttu-id="0978e-187">Na wysokim poziomie ten kod inicjuje automatycznie obiekty i usługi do późniejszego użycia, gdy żądanie jest wymagane przez aplikację, a nie trzeba jej wykonać ręcznie.</span><span class="sxs-lookup"><span data-stu-id="0978e-187">At a high level, this code initializes the objects and services automatically for later use when requested by the application instead of having to manually do it.</span></span>

<span data-ttu-id="0978e-188">Modele uczenia maszynowego nie są statyczne.</span><span class="sxs-lookup"><span data-stu-id="0978e-188">Machine learning models are not static.</span></span> <span data-ttu-id="0978e-189">Po udostępnieniu nowych danych szkoleniowych model zostanie ponownie przeszkolony i wdrożony ponownie.</span><span class="sxs-lookup"><span data-stu-id="0978e-189">As new training data becomes available, the model is retrained and redeployed.</span></span> <span data-ttu-id="0978e-190">Jednym ze sposobów uzyskania najnowszej wersji modelu do aplikacji jest ponowne wdrożenie całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0978e-190">One way to get the latest version of the model into your application is to redeploy the entire application.</span></span> <span data-ttu-id="0978e-191">Powoduje to jednak wprowadzenie przestojów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0978e-191">However, this introduces application downtime.</span></span> <span data-ttu-id="0978e-192">Usługa `PredictionEnginePool` udostępnia mechanizm ponownego ładowania zaktualizowanego modelu bez konieczności podłączania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0978e-192">The `PredictionEnginePool` service provides a mechanism to reload an updated model without taking your application down.</span></span>

<span data-ttu-id="0978e-193">Ustaw parametr `watchForChanges` na `true`, a `PredictionEnginePool` uruchamia [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) , który nasłuchuje powiadomień o zmianie systemu plików i zgłasza zdarzenia w przypadku zmiany pliku.</span><span class="sxs-lookup"><span data-stu-id="0978e-193">Set the `watchForChanges` parameter to `true`, and the `PredictionEnginePool` starts a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) that listens to the file system change notifications and raises events when there is a change to the file.</span></span> <span data-ttu-id="0978e-194">Spowoduje to wypróbowanie `PredictionEnginePool` w celu automatycznego ponownego załadowania modelu.</span><span class="sxs-lookup"><span data-stu-id="0978e-194">This prompts the `PredictionEnginePool` to automatically reload the model.</span></span>

<span data-ttu-id="0978e-195">Model jest identyfikowany przez parametr `modelName`, dzięki czemu można ponownie załadować więcej niż jeden model dla aplikacji po zmianie.</span><span class="sxs-lookup"><span data-stu-id="0978e-195">The model is identified by the `modelName` parameter so that more than one model per application can be reloaded upon change.</span></span>

> [!TIP]
> <span data-ttu-id="0978e-196">Alternatywnie można użyć metody `FromUri` podczas pracy z modelami przechowywanymi zdalnie.</span><span class="sxs-lookup"><span data-stu-id="0978e-196">Alternatively, you can use the `FromUri` method when working with models stored remotely.</span></span> <span data-ttu-id="0978e-197">Zamiast oglądać zdarzenia ze zmienionymi plikami, `FromUri` sonduje lokalizację zdalną pod kątem zmian.</span><span class="sxs-lookup"><span data-stu-id="0978e-197">Rather than watching for file changed events, `FromUri` polls the remote location for changes.</span></span> <span data-ttu-id="0978e-198">Interwał sondowania jest wartością domyślną 5 minut.</span><span class="sxs-lookup"><span data-stu-id="0978e-198">The polling interval defaults to 5 minutes.</span></span> <span data-ttu-id="0978e-199">Interwał sondowania można zwiększyć lub zmniejszyć w zależności od wymagań aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0978e-199">You can increase or decrease the polling interval based on your application's requirements.</span></span> <span data-ttu-id="0978e-200">W poniższym przykładzie kodu `PredictionEnginePool` sonduje model przechowywany w określonym identyfikatorze URI co minutę.</span><span class="sxs-lookup"><span data-stu-id="0978e-200">In the code sample below, the `PredictionEnginePool` polls the model stored at the specified URI every minute.</span></span>
>
>```csharp
>builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="load-the-model-into-the-function"></a><span data-ttu-id="0978e-201">Załaduj model do funkcji</span><span class="sxs-lookup"><span data-stu-id="0978e-201">Load the model into the function</span></span>

<span data-ttu-id="0978e-202">Wstaw następujący kod wewnątrz klasy *AnalyzeSentiment* :</span><span class="sxs-lookup"><span data-stu-id="0978e-202">Insert the following code inside the *AnalyzeSentiment* class:</span></span>

[!code-csharp [AnalyzeCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L18-L24)]

<span data-ttu-id="0978e-203">Ten kod przypisuje `PredictionEnginePool` przez przekazanie go do konstruktora funkcji, który uzyskuje się za pośrednictwem iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="0978e-203">This code assigns the `PredictionEnginePool` by passing it to the function's constructor which you get via dependency injection.</span></span>

## <a name="use-the-model-to-make-predictions"></a><span data-ttu-id="0978e-204">Tworzenie prognoz przy użyciu modelu</span><span class="sxs-lookup"><span data-stu-id="0978e-204">Use the model to make predictions</span></span>

<span data-ttu-id="0978e-205">Zastąp istniejącą implementację metody *Run* w klasie *AnalyzeSentiment* następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="0978e-205">Replace the existing implementation of *Run* method in *AnalyzeSentiment* class with the following code:</span></span>

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
    SentimentPrediction prediction = _predictionEnginePool.Predict(modelName: "SentimentAnalysisModel", example: data);

    //Convert prediction to string
    string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

    //Return Prediction
    return (ActionResult)new OkObjectResult(sentiment);
}
```

<span data-ttu-id="0978e-206">Gdy metoda `Run` jest wykonywana, dane przychodzące z żądania HTTP są deserializowane i używane jako dane wejściowe dla `PredictionEnginePool`.</span><span class="sxs-lookup"><span data-stu-id="0978e-206">When the `Run` method executes, the incoming data from the HTTP request is deserialized and used as input for the `PredictionEnginePool`.</span></span> <span data-ttu-id="0978e-207">Metoda `Predict` jest następnie wywoływana w celu przeprowadzenia prognoz przy użyciu `SentimentAnalysisModel` zarejestrowanego w klasie `Startup` i zwraca wyniki z powrotem do użytkownika, jeśli się to powiedzie.</span><span class="sxs-lookup"><span data-stu-id="0978e-207">The `Predict` method is then called to make predictions using the `SentimentAnalysisModel` registered in the `Startup` class and returns the results back to the user if successful.</span></span>

## <a name="test-locally"></a><span data-ttu-id="0978e-208">Testuj lokalnie</span><span class="sxs-lookup"><span data-stu-id="0978e-208">Test locally</span></span>

<span data-ttu-id="0978e-209">Teraz, gdy wszystko jest skonfigurowane, czas na przetestowanie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="0978e-209">Now that everything is set up, it's time to test the application:</span></span>

1. <span data-ttu-id="0978e-210">Uruchom aplikację</span><span class="sxs-lookup"><span data-stu-id="0978e-210">Run the application</span></span>
1. <span data-ttu-id="0978e-211">Otwórz program PowerShell i wprowadź kod w wierszu, w którym PORT jest portem, na którym działa aplikacja.</span><span class="sxs-lookup"><span data-stu-id="0978e-211">Open PowerShell and enter the code into the prompt where PORT is the port your application is running on.</span></span> <span data-ttu-id="0978e-212">Zazwyczaj port jest 7071.</span><span class="sxs-lookup"><span data-stu-id="0978e-212">Typically the port is 7071.</span></span>

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="0978e-213">Jeśli to się powiedzie, dane wyjściowe powinny wyglądać podobnie do poniższego tekstu:</span><span class="sxs-lookup"><span data-stu-id="0978e-213">If successful, the output should look similar to the text below:</span></span>

    ```powershell
    Negative
    ```

<span data-ttu-id="0978e-214">Nabycia!</span><span class="sxs-lookup"><span data-stu-id="0978e-214">Congratulations!</span></span> <span data-ttu-id="0978e-215">Udało Ci się pomyślnie obsłużyć model, aby przekonywać prognoz przez Internet przy użyciu funkcji platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="0978e-215">You have successfully served your model to make predictions over the internet using an Azure Function.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0978e-216">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="0978e-216">Next Steps</span></span>

- [<span data-ttu-id="0978e-217">Wdrażanie na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="0978e-217">Deploy to Azure</span></span>](/azure/azure-functions/functions-develop-vs#publish-to-azure)
