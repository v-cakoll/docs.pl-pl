---
title: Wdrażanie modelu w usłudze Azure Functions
description: Obsłużymy model uczenia maszynowego ML.NET tonacji Analysis na potrzeby przewidywania przez Internet przy użyciu Azure Functions
ms.date: 10/31/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: bd08982e96f39a9685ddabc090ac3bc5c7855022
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424348"
---
# <a name="deploy-a-model-to-azure-functions"></a><span data-ttu-id="08f02-103">Wdrażanie modelu w usłudze Azure Functions</span><span class="sxs-lookup"><span data-stu-id="08f02-103">Deploy a model to Azure Functions</span></span>

<span data-ttu-id="08f02-104">Dowiedz się, jak wdrożyć wstępnie szkolony model uczenia maszynowego ML.NET na potrzeby prognozowania za pośrednictwem protokołu HTTP za pośrednictwem środowiska bezserwerowego Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="08f02-104">Learn how to deploy a pre-trained ML.NET machine learning model for predictions over HTTP through an Azure Functions serverless environment.</span></span>

> [!NOTE]
> <span data-ttu-id="08f02-105">rozszerzenie usługi `PredictionEnginePool` jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="08f02-105">`PredictionEnginePool` service extension is currently in preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="08f02-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="08f02-106">Prerequisites</span></span>

- <span data-ttu-id="08f02-107">[Program Visual Studio 2017 w wersji 15,6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowaną funkcją "Programowanie dla wielu platform w środowisku .NET Core" i "Programowanie na platformie Azure".</span><span class="sxs-lookup"><span data-stu-id="08f02-107">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload and "Azure development" installed.</span></span>
- [<span data-ttu-id="08f02-108">Narzędzia Azure Functions</span><span class="sxs-lookup"><span data-stu-id="08f02-108">Azure Functions Tools</span></span>](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- <span data-ttu-id="08f02-109">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="08f02-109">Powershell</span></span>
- <span data-ttu-id="08f02-110">Model wstępnie szkolony.</span><span class="sxs-lookup"><span data-stu-id="08f02-110">Pre-trained model.</span></span> <span data-ttu-id="08f02-111">Użyj [samouczka analiza tonacji ml.NET](../tutorials/sentiment-analysis.md) , aby skompilować własny model lub pobrać ten [wstępnie szkolony model uczenia maszynowego analizy tonacji](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="08f02-111">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="azure-functions-sample-overview"></a><span data-ttu-id="08f02-112">Przykład Azure Functions — Omówienie</span><span class="sxs-lookup"><span data-stu-id="08f02-112">Azure Functions sample overview</span></span>

<span data-ttu-id="08f02-113">Ten przykład jest  **C# wyzwalaczem http Azure Functions aplikacji** , która używa premieszczonego modelu klasyfikacji danych binarnych do kategoryzowania tonacji tekstu jako pozytywnego lub ujemnego.</span><span class="sxs-lookup"><span data-stu-id="08f02-113">This sample is a **C# HTTP Trigger Azure Functions application** that uses a pretrained binary classification model to categorize the sentiment of text as positive or negative.</span></span> <span data-ttu-id="08f02-114">Azure Functions zapewnia łatwy sposób uruchamiania małych fragmentów kodu na dużą skalę w zarządzanym środowisku bez serwera w chmurze.</span><span class="sxs-lookup"><span data-stu-id="08f02-114">Azure Functions provides an easy way to run small pieces of code at scale on a managed serverless environment in the cloud.</span></span> <span data-ttu-id="08f02-115">Kod dla tego przykładu można znaleźć w repozytorium [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="08f02-115">The code for this sample can be found on the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) repository on GitHub.</span></span>

## <a name="create-azure-functions-project"></a><span data-ttu-id="08f02-116">Utwórz projekt Azure Functions</span><span class="sxs-lookup"><span data-stu-id="08f02-116">Create Azure Functions project</span></span>

1. <span data-ttu-id="08f02-117">Otwórz program Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="08f02-117">Open Visual Studio 2017.</span></span> <span data-ttu-id="08f02-118">Wybierz pozycję **plik** > **Nowy** > **projekt** na pasku menu.</span><span class="sxs-lookup"><span data-stu-id="08f02-118">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="08f02-119">W oknie dialogowym **Nowy projekt** wybierz węzeł **wizualizacji C#**  , a następnie węzeł **chmury** .</span><span class="sxs-lookup"><span data-stu-id="08f02-119">In the **New Project** dialog, select the **Visual C#** node followed by the **Cloud** node.</span></span> <span data-ttu-id="08f02-120">Następnie wybierz szablon projektu **Azure Functions** .</span><span class="sxs-lookup"><span data-stu-id="08f02-120">Then select the **Azure Functions** project template.</span></span> <span data-ttu-id="08f02-121">W polu tekstowym **Nazwa** wpisz "SentimentAnalysisFunctionsApp", a następnie wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="08f02-121">In the **Name** text box, type "SentimentAnalysisFunctionsApp" and then select the **OK** button.</span></span>
1. <span data-ttu-id="08f02-122">W oknie dialogowym **Nowy projekt** Otwórz listę rozwijaną nad opcjami projektu i wybierz pozycję **Azure Functions v2 (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="08f02-122">In the **New Project** dialog, open the dropdown above the project options and select **Azure Functions v2 (.NET Core)**.</span></span> <span data-ttu-id="08f02-123">Następnie wybierz projekt **wyzwalacza http** , a następnie wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="08f02-123">Then, select the **Http trigger** project and then select the **OK** button.</span></span>
1. <span data-ttu-id="08f02-124">Utwórz katalog o nazwie *MLModels* w projekcie, aby zapisać model:</span><span class="sxs-lookup"><span data-stu-id="08f02-124">Create a directory named *MLModels* in your project to save your model:</span></span>

    <span data-ttu-id="08f02-125">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **dodaj** **Nowy folder** > .</span><span class="sxs-lookup"><span data-stu-id="08f02-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="08f02-126">Wpisz "MLModels" i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="08f02-126">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="08f02-127">Zainstaluj **pakiet NuGet Microsoft.ml** w wersji **1.3.1**:</span><span class="sxs-lookup"><span data-stu-id="08f02-127">Install the **Microsoft.ML NuGet Package** version **1.3.1**:</span></span>

    <span data-ttu-id="08f02-128">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="08f02-128">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="08f02-129">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, Wyszukaj pozycję **Microsoft.ml**, wybierz ten pakiet z listy, a następnie wybierz przycisk **Instaluj** .</span><span class="sxs-lookup"><span data-stu-id="08f02-129">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="08f02-130">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="08f02-130">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="08f02-131">Zainstaluj **pakiet NuGet Microsoft. Azure. Functions. Extensions**:</span><span class="sxs-lookup"><span data-stu-id="08f02-131">Install the **Microsoft.Azure.Functions.Extensions NuGet Package**:</span></span>

    <span data-ttu-id="08f02-132">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="08f02-132">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="08f02-133">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, Wyszukaj pozycję **Microsoft. Azure. Functions. Extensions**, wybierz ten pakiet z listy, a następnie wybierz przycisk **Instaluj** .</span><span class="sxs-lookup"><span data-stu-id="08f02-133">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Azure.Functions.Extensions**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="08f02-134">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="08f02-134">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="08f02-135">Zainstaluj **pakiet NuGet Microsoft.Extensions.ml** w wersji **1.3.1**:</span><span class="sxs-lookup"><span data-stu-id="08f02-135">Install the **Microsoft.Extensions.ML NuGet Package** version **1.3.1**:</span></span>

    <span data-ttu-id="08f02-136">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="08f02-136">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="08f02-137">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, Wyszukaj pozycję **Microsoft.Extensions.ml**, wybierz ten pakiet z listy, a następnie wybierz przycisk **Instaluj** .</span><span class="sxs-lookup"><span data-stu-id="08f02-137">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="08f02-138">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="08f02-138">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="08f02-139">Zainstaluj **pakiet NuGet Microsoft. NET. Sdk. Functions** w wersji 1.0.28 +:</span><span class="sxs-lookup"><span data-stu-id="08f02-139">Install the **Microsoft.NET.Sdk.Functions NuGet Package** version 1.0.28+:</span></span>

    <span data-ttu-id="08f02-140">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="08f02-140">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="08f02-141">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę zainstalowane, Wyszukaj pozycję **Microsoft. NET. Sdk. Functions**, zaznacz ten pakiet na liście, wybierz pozycję **1.0.28 lub nowszy** z listy rozwijanej wersja i wybierz przycisk **Aktualizuj** .</span><span class="sxs-lookup"><span data-stu-id="08f02-141">Choose "nuget.org" as the Package source, select the Installed tab, search for **Microsoft.NET.Sdk.Functions**, select that package in the list, select **1.0.28 or later** from the Version dropdown, and select the **Update** button.</span></span> <span data-ttu-id="08f02-142">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="08f02-142">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="add-pre-trained-model-to-project"></a><span data-ttu-id="08f02-143">Dodaj wstępnie szkolony model do projektu</span><span class="sxs-lookup"><span data-stu-id="08f02-143">Add pre-trained model to project</span></span>

1. <span data-ttu-id="08f02-144">Skopiuj wstępnie utworzony model do folderu *MLModels* .</span><span class="sxs-lookup"><span data-stu-id="08f02-144">Copy your pre-built model to the *MLModels* folder.</span></span>
1. <span data-ttu-id="08f02-145">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy wstępnie utworzony plik modelu i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="08f02-145">In Solution Explorer, right-click your pre-built model file and select **Properties**.</span></span> <span data-ttu-id="08f02-146">W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="08f02-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="create-azure-function-to-analyze-sentiment"></a><span data-ttu-id="08f02-147">Utwórz funkcję platformy Azure, aby analizować tonacji</span><span class="sxs-lookup"><span data-stu-id="08f02-147">Create Azure Function to analyze sentiment</span></span>

<span data-ttu-id="08f02-148">Utwórz klasę do przewidywania tonacji.</span><span class="sxs-lookup"><span data-stu-id="08f02-148">Create a class to predict sentiment.</span></span> <span data-ttu-id="08f02-149">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="08f02-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="08f02-150">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz pozycję **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="08f02-150">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="08f02-151">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Funkcja platformy Azure** i zmień wartość pola **Nazwa** na *AnalyzeSentiment.cs*.</span><span class="sxs-lookup"><span data-stu-id="08f02-151">In the **Add New Item** dialog box, select **Azure Function** and change the **Name** field to *AnalyzeSentiment.cs*.</span></span> <span data-ttu-id="08f02-152">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="08f02-152">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="08f02-153">W oknie dialogowym **Nowa funkcja platformy Azure** wybierz pozycję **wyzwalacz http**.</span><span class="sxs-lookup"><span data-stu-id="08f02-153">In the **New Azure Function** dialog box, select **Http Trigger**.</span></span> <span data-ttu-id="08f02-154">Następnie wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="08f02-154">Then, select the **OK** button.</span></span>

    <span data-ttu-id="08f02-155">Plik *AnalyzeSentiment.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="08f02-155">The *AnalyzeSentiment.cs* file opens in the code editor.</span></span> <span data-ttu-id="08f02-156">Dodaj następującą instrukcję `using` na początku *AnalyzeSentiment.cs*:</span><span class="sxs-lookup"><span data-stu-id="08f02-156">Add the following `using` statement to the top of *AnalyzeSentiment.cs*:</span></span>

    [!code-csharp [AnalyzeUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L1-L11)]

    <span data-ttu-id="08f02-157">Domyślnie Klasa `AnalyzeSentiment` jest `static`.</span><span class="sxs-lookup"><span data-stu-id="08f02-157">By default, the `AnalyzeSentiment` class is `static`.</span></span> <span data-ttu-id="08f02-158">Upewnij się, że usunięto słowo kluczowe `static` z definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="08f02-158">Make sure to remove the `static` keyword from the class definition.</span></span>

    ```csharp
    public class AnalyzeSentiment
    {

    }
    ```

## <a name="create-data-models"></a><span data-ttu-id="08f02-159">Tworzenie modeli danych</span><span class="sxs-lookup"><span data-stu-id="08f02-159">Create data models</span></span>

<span data-ttu-id="08f02-160">Należy utworzyć klasy dla danych wejściowych i prognoz.</span><span class="sxs-lookup"><span data-stu-id="08f02-160">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="08f02-161">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="08f02-161">Add a new class to your project:</span></span>

1. <span data-ttu-id="08f02-162">Utwórz katalog o nazwie *Datamodels* w projekcie, aby zapisać modele danych: w Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj > nowy folder**.</span><span class="sxs-lookup"><span data-stu-id="08f02-162">Create a directory named *DataModels* in your project to save your data models: In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="08f02-163">Wpisz "datamodels" i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="08f02-163">Type "DataModels" and hit Enter.</span></span>
2. <span data-ttu-id="08f02-164">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy katalog *Datamodels* , a następnie wybierz pozycję **Dodaj > nowy element**.</span><span class="sxs-lookup"><span data-stu-id="08f02-164">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
3. <span data-ttu-id="08f02-165">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="08f02-165">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="08f02-166">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="08f02-166">Then, select the **Add** button.</span></span>

    <span data-ttu-id="08f02-167">Plik *SentimentData.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="08f02-167">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="08f02-168">Dodaj następującą instrukcję using na początku *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="08f02-168">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp [SentimentDataUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L1)]

    <span data-ttu-id="08f02-169">Usuń istniejącą definicję klasy i Dodaj następujący kod do pliku *SentimentData.cs* :</span><span class="sxs-lookup"><span data-stu-id="08f02-169">Remove the existing class definition and add the following code to the *SentimentData.cs* file:</span></span>

    [!code-csharp [SentimentData](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L5-L13)]

4. <span data-ttu-id="08f02-170">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy katalog *Datamodels* , a następnie wybierz pozycję **Dodaj > nowy element**.</span><span class="sxs-lookup"><span data-stu-id="08f02-170">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="08f02-171">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="08f02-171">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="08f02-172">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="08f02-172">Then, select the **Add** button.</span></span> <span data-ttu-id="08f02-173">Plik *SentimentPrediction.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="08f02-173">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="08f02-174">Dodaj następującą instrukcję using na początku *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="08f02-174">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    [!code-csharp [SentimentPredictionUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L1)]

    <span data-ttu-id="08f02-175">Usuń istniejącą definicję klasy i Dodaj następujący kod do pliku *SentimentPrediction.cs* :</span><span class="sxs-lookup"><span data-stu-id="08f02-175">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    [!code-csharp [SentimentPrediction](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L5-L14)]

    <span data-ttu-id="08f02-176">`SentimentPrediction` dziedziczy po `SentimentData`, który zapewnia dostęp do oryginalnych danych we właściwości `SentimentText`, a także dane wyjściowe generowane przez model.</span><span class="sxs-lookup"><span data-stu-id="08f02-176">`SentimentPrediction` inherits from `SentimentData` which provides access to the original data in the `SentimentText` property as well as the output generated by the model.</span></span>

## <a name="register-predictionenginepool-service"></a><span data-ttu-id="08f02-177">Zarejestruj usługę PredictionEnginePool</span><span class="sxs-lookup"><span data-stu-id="08f02-177">Register PredictionEnginePool service</span></span>

<span data-ttu-id="08f02-178">Aby wykonać pojedyncze prognozowanie, należy utworzyć [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="08f02-178">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="08f02-179">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nie jest bezpieczny wątkowo.</span><span class="sxs-lookup"><span data-stu-id="08f02-179">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="08f02-180">Ponadto należy utworzyć wystąpienie go wszędzie tam, gdzie jest to potrzebne w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="08f02-180">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="08f02-181">Gdy aplikacja zostanie powiększona, ten proces może być niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="08f02-181">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="08f02-182">Aby zwiększyć wydajność i bezpieczeństwo wątków, użyj kombinacji iniekcji zależności i usługi `PredictionEnginePool`, która tworzy [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) obiektów do użycia w całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="08f02-182">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

<span data-ttu-id="08f02-183">Poniższy link zawiera więcej informacji, jeśli chcesz dowiedzieć się więcej o [iniekcji zależności](https://en.wikipedia.org/wiki/Dependency_injection).</span><span class="sxs-lookup"><span data-stu-id="08f02-183">The following link provides more information if you want to learn more about [dependency injection](https://en.wikipedia.org/wiki/Dependency_injection).</span></span>

1. <span data-ttu-id="08f02-184">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz pozycję **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="08f02-184">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="08f02-185">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *Startup.cs*.</span><span class="sxs-lookup"><span data-stu-id="08f02-185">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *Startup.cs*.</span></span> <span data-ttu-id="08f02-186">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="08f02-186">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="08f02-187">Dodaj następujące instrukcje using na początku *Startup.cs*:</span><span class="sxs-lookup"><span data-stu-id="08f02-187">Add the following using statements to the top of *Startup.cs*:</span></span>

    [!code-csharp [StartupUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L1-L6)]

1. <span data-ttu-id="08f02-188">Usuń istniejący kod poniżej instrukcji using i Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="08f02-188">Remove the existing code below the using statements and add the following code:</span></span>

    ```csharp
    [assembly: FunctionsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        public class Startup : FunctionsStartup
        {

        }
    }
    ```

1. <span data-ttu-id="08f02-189">Zdefiniuj zmienne do przechowywania środowiska, w którym jest uruchomiona aplikacja, oraz ścieżkę pliku, w której znajduje się model wewnątrz klasy `Startup`</span><span class="sxs-lookup"><span data-stu-id="08f02-189">Define variables to store the environment the app is running in and the file path where the model is located inside the `Startup` class</span></span>

    [!code-csharp [DefineStartupVars](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L13-L14)]

1. <span data-ttu-id="08f02-190">Poniżej Utwórz konstruktora, aby ustawić wartości zmiennych `_environment` i `_modelPath`.</span><span class="sxs-lookup"><span data-stu-id="08f02-190">Below that, create a constructor to set the values of the `_environment` and `_modelPath` variables.</span></span> <span data-ttu-id="08f02-191">Gdy aplikacja działa lokalnie, środowisko domyślne to *programowanie*.</span><span class="sxs-lookup"><span data-stu-id="08f02-191">When the application is running locally, the default environment is *Development*.</span></span>

    [!code-csharp [StartupCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L16-L29)]

1. <span data-ttu-id="08f02-192">Następnie Dodaj nową metodę o nazwie `Configure`, aby zarejestrować usługę `PredictionEnginePool` poniżej konstruktora.</span><span class="sxs-lookup"><span data-stu-id="08f02-192">Then, add a new method called `Configure` to register the `PredictionEnginePool` service below the constructor.</span></span>

    [!code-csharp [ConfigureServices](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L31-L35)]

<span data-ttu-id="08f02-193">Na wysokim poziomie ten kod inicjuje automatycznie obiekty i usługi do późniejszego użycia, gdy żądanie jest wymagane przez aplikację, a nie trzeba jej wykonać ręcznie.</span><span class="sxs-lookup"><span data-stu-id="08f02-193">At a high level, this code initializes the objects and services automatically for later use when requested by the application instead of having to manually do it.</span></span>

<span data-ttu-id="08f02-194">Modele uczenia maszynowego nie są statyczne.</span><span class="sxs-lookup"><span data-stu-id="08f02-194">Machine learning models are not static.</span></span> <span data-ttu-id="08f02-195">Po udostępnieniu nowych danych szkoleniowych model zostanie ponownie przeszkolony i wdrożony ponownie.</span><span class="sxs-lookup"><span data-stu-id="08f02-195">As new training data becomes available, the model is retrained and redeployed.</span></span> <span data-ttu-id="08f02-196">Jednym ze sposobów uzyskania najnowszej wersji modelu do aplikacji jest ponowne wdrożenie całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="08f02-196">One way to get the latest version of the model into your application is to redeploy the entire application.</span></span> <span data-ttu-id="08f02-197">Powoduje to jednak wprowadzenie przestojów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="08f02-197">However, this introduces application downtime.</span></span> <span data-ttu-id="08f02-198">Usługa `PredictionEnginePool` udostępnia mechanizm ponownego ładowania zaktualizowanego modelu bez konieczności podłączania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="08f02-198">The `PredictionEnginePool` service provides a mechanism to reload an updated model without taking your application down.</span></span>

<span data-ttu-id="08f02-199">Ustaw parametr `watchForChanges` na `true`, a `PredictionEnginePool` uruchamia [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) , który nasłuchuje powiadomień o zmianie systemu plików i zgłasza zdarzenia w przypadku zmiany pliku.</span><span class="sxs-lookup"><span data-stu-id="08f02-199">Set the `watchForChanges` parameter to `true`, and the `PredictionEnginePool` starts a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) that listens to the file system change notifications and raises events when there is a change to the file.</span></span> <span data-ttu-id="08f02-200">Spowoduje to wypróbowanie `PredictionEnginePool` w celu automatycznego ponownego załadowania modelu.</span><span class="sxs-lookup"><span data-stu-id="08f02-200">This prompts the `PredictionEnginePool` to automatically reload the model.</span></span>

<span data-ttu-id="08f02-201">Model jest identyfikowany przez parametr `modelName`, dzięki czemu można ponownie załadować więcej niż jeden model dla aplikacji po zmianie.</span><span class="sxs-lookup"><span data-stu-id="08f02-201">The model is identified by the `modelName` parameter so that more than one model per application can be reloaded upon change.</span></span>

> [!TIP]
> <span data-ttu-id="08f02-202">Alternatywnie można użyć metody `FromUri` podczas pracy z modelami przechowywanymi zdalnie.</span><span class="sxs-lookup"><span data-stu-id="08f02-202">Alternatively, you can use the `FromUri` method when working with models stored remotely.</span></span> <span data-ttu-id="08f02-203">Zamiast oglądać zdarzenia ze zmienionymi plikami, `FromUri` sonduje lokalizację zdalną pod kątem zmian.</span><span class="sxs-lookup"><span data-stu-id="08f02-203">Rather than watching for file changed events, `FromUri` polls the remote location for changes.</span></span> <span data-ttu-id="08f02-204">Interwał sondowania jest wartością domyślną 5 minut.</span><span class="sxs-lookup"><span data-stu-id="08f02-204">The polling interval defaults to 5 minutes.</span></span> <span data-ttu-id="08f02-205">Interwał sondowania można zwiększyć lub zmniejszyć w zależności od wymagań aplikacji.</span><span class="sxs-lookup"><span data-stu-id="08f02-205">You can increase or decrease the polling interval based on your application's requirements.</span></span> <span data-ttu-id="08f02-206">W poniższym przykładzie kodu `PredictionEnginePool` sonduje model przechowywany w określonym identyfikatorze URI co minutę.</span><span class="sxs-lookup"><span data-stu-id="08f02-206">In the code sample below, the `PredictionEnginePool` polls the model stored at the specified URI every minute.</span></span>
>
>```csharp
>builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="load-the-model-into-the-function"></a><span data-ttu-id="08f02-207">Załaduj model do funkcji</span><span class="sxs-lookup"><span data-stu-id="08f02-207">Load the model into the function</span></span>

<span data-ttu-id="08f02-208">Wstaw następujący kod wewnątrz klasy *AnalyzeSentiment* :</span><span class="sxs-lookup"><span data-stu-id="08f02-208">Insert the following code inside the *AnalyzeSentiment* class:</span></span>

[!code-csharp [AnalyzeCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L18-L24)]

<span data-ttu-id="08f02-209">Ten kod przypisuje `PredictionEnginePool` przez przekazanie go do konstruktora funkcji, który uzyskuje się za pośrednictwem iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="08f02-209">This code assigns the `PredictionEnginePool` by passing it to the function's constructor which you get via dependency injection.</span></span>

## <a name="use-the-model-to-make-predictions"></a><span data-ttu-id="08f02-210">Tworzenie prognoz przy użyciu modelu</span><span class="sxs-lookup"><span data-stu-id="08f02-210">Use the model to make predictions</span></span>

<span data-ttu-id="08f02-211">Zastąp istniejącą implementację metody *Run* w klasie *AnalyzeSentiment* następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="08f02-211">Replace the existing implementation of *Run* method in *AnalyzeSentiment* class with the following code:</span></span>

[!code-csharp [AnalyzeRunMethod](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L26-L45)]

<span data-ttu-id="08f02-212">Gdy metoda `Run` jest wykonywana, dane przychodzące z żądania HTTP są deserializowane i używane jako dane wejściowe dla `PredictionEnginePool`.</span><span class="sxs-lookup"><span data-stu-id="08f02-212">When the `Run` method executes, the incoming data from the HTTP request is deserialized and used as input for the `PredictionEnginePool`.</span></span> <span data-ttu-id="08f02-213">Metoda `Predict` jest następnie wywoływana w celu przeprowadzenia prognoz przy użyciu `SentimentAnalysisModel` zarejestrowanego w klasie `Startup` i zwraca wyniki z powrotem do użytkownika, jeśli się to powiedzie.</span><span class="sxs-lookup"><span data-stu-id="08f02-213">The `Predict` method is then called to make predictions using the `SentimentAnalysisModel` registered in the `Startup` class and returns the results back to the user if successful.</span></span>

## <a name="test-locally"></a><span data-ttu-id="08f02-214">Testuj lokalnie</span><span class="sxs-lookup"><span data-stu-id="08f02-214">Test locally</span></span>

<span data-ttu-id="08f02-215">Teraz, gdy wszystko jest skonfigurowane, czas na przetestowanie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="08f02-215">Now that everything is set up, it's time to test the application:</span></span>

1. <span data-ttu-id="08f02-216">Uruchom aplikację</span><span class="sxs-lookup"><span data-stu-id="08f02-216">Run the application</span></span>
1. <span data-ttu-id="08f02-217">Otwórz program PowerShell i wprowadź kod w wierszu, w którym PORT jest portem, na którym działa aplikacja.</span><span class="sxs-lookup"><span data-stu-id="08f02-217">Open PowerShell and enter the code into the prompt where PORT is the port your application is running on.</span></span> <span data-ttu-id="08f02-218">Zazwyczaj port jest 7071.</span><span class="sxs-lookup"><span data-stu-id="08f02-218">Typically the port is 7071.</span></span>

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="08f02-219">Jeśli to się powiedzie, dane wyjściowe powinny wyglądać podobnie do poniższego tekstu:</span><span class="sxs-lookup"><span data-stu-id="08f02-219">If successful, the output should look similar to the text below:</span></span>

    ```powershell
    Negative
    ```

<span data-ttu-id="08f02-220">Nabycia!</span><span class="sxs-lookup"><span data-stu-id="08f02-220">Congratulations!</span></span> <span data-ttu-id="08f02-221">Udało Ci się pomyślnie obsłużyć model, aby przekonywać prognoz przez Internet przy użyciu funkcji platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="08f02-221">You have successfully served your model to make predictions over the internet using an Azure Function.</span></span>

## <a name="next-steps"></a><span data-ttu-id="08f02-222">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="08f02-222">Next Steps</span></span>

- [<span data-ttu-id="08f02-223">Wdrażanie na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="08f02-223">Deploy to Azure</span></span>](/azure/azure-functions/functions-develop-vs#publish-to-azure)
