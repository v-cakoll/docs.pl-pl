---
title: Wdrażanie modelu w usłudze Azure Functions
description: Obsługa modelu uczenia maszynowego analizy ML.NET tonacji do przewidywania przez Internet przy użyciu funkcji platformy Azure
ms.date: 02/21/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 2f340805200a14e0e145ffe1bf20f8059df63555
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608052"
---
# <a name="deploy-a-model-to-azure-functions"></a><span data-ttu-id="70269-103">Wdrażanie modelu w usłudze Azure Functions</span><span class="sxs-lookup"><span data-stu-id="70269-103">Deploy a model to Azure Functions</span></span>

<span data-ttu-id="70269-104">Dowiedz się, jak wdrożyć wstępnie przeszkolony model uczenia maszynowego ML.NET dla prognoz za pośrednictwem protokołu HTTP za pośrednictwem środowiska bezserwerowego usługi Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="70269-104">Learn how to deploy a pre-trained ML.NET machine learning model for predictions over HTTP through an Azure Functions serverless environment.</span></span>

> [!NOTE]
> <span data-ttu-id="70269-105">W tym przykładzie uruchamia `PredictionEnginePool` wersję zapoznawczą usługi.</span><span class="sxs-lookup"><span data-stu-id="70269-105">This sample runs a preview version of the `PredictionEnginePool` service.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="70269-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="70269-106">Prerequisites</span></span>

- <span data-ttu-id="70269-107">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowsze lub Visual Studio 2017 w wersji 15.6 lub nowszej z zainstalowanymi obciążeniami ".NET Core cross-platform development" i "Azure development".</span><span class="sxs-lookup"><span data-stu-id="70269-107">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" and "Azure development" workloads installed.</span></span>
- [<span data-ttu-id="70269-108">Narzędzia funkcji platformy Azure</span><span class="sxs-lookup"><span data-stu-id="70269-108">Azure Functions Tools</span></span>](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- <span data-ttu-id="70269-109">PowerShell</span><span class="sxs-lookup"><span data-stu-id="70269-109">Powershell</span></span>
- <span data-ttu-id="70269-110">Wstępnie przeszkolony model.</span><span class="sxs-lookup"><span data-stu-id="70269-110">Pre-trained model.</span></span> <span data-ttu-id="70269-111">Użyj [samouczka analizy ML.NET,](../tutorials/sentiment-analysis.md) aby zbudować własny model lub pobrać ten [wstępnie przeszkolony model uczenia maszynowego analizy tonacji](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="70269-111">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="azure-functions-sample-overview"></a><span data-ttu-id="70269-112">Omówienie przykładu usługi Azure Functions</span><span class="sxs-lookup"><span data-stu-id="70269-112">Azure Functions sample overview</span></span>

<span data-ttu-id="70269-113">Ten przykład jest **C# HTTP Trigger Azure Functions aplikacji,** która używa wstępnie przeszkolony model klasyfikacji binarnej do kategoryzowania tonacji tekstu jako dodatnie lub negatywne.</span><span class="sxs-lookup"><span data-stu-id="70269-113">This sample is a **C# HTTP Trigger Azure Functions application** that uses a pretrained binary classification model to categorize the sentiment of text as positive or negative.</span></span> <span data-ttu-id="70269-114">Usługa Azure Functions zapewnia łatwy sposób uruchamiania małych fragmentów kodu na dużą skalę w zarządzanym środowisku bezserwerowym w chmurze.</span><span class="sxs-lookup"><span data-stu-id="70269-114">Azure Functions provides an easy way to run small pieces of code at scale on a managed serverless environment in the cloud.</span></span> <span data-ttu-id="70269-115">Kod dla tego przykładu można znaleźć na repozytorium [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="70269-115">The code for this sample can be found on the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) repository on GitHub.</span></span>

## <a name="create-azure-functions-project"></a><span data-ttu-id="70269-116">Tworzenie projektu usługi Azure Functions</span><span class="sxs-lookup"><span data-stu-id="70269-116">Create Azure Functions project</span></span>

1. <span data-ttu-id="70269-117">Otwórz program Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="70269-117">Open Visual Studio 2017.</span></span> <span data-ttu-id="70269-118">Z paska menu **wybierz pozycję Plik** > **nowy** > **projekt.**</span><span class="sxs-lookup"><span data-stu-id="70269-118">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="70269-119">W oknie dialogowym **Nowy projekt** wybierz węzeł **Visual C#,** po którym następuje węzeł **Chmura.**</span><span class="sxs-lookup"><span data-stu-id="70269-119">In the **New Project** dialog, select the **Visual C#** node followed by the **Cloud** node.</span></span> <span data-ttu-id="70269-120">Następnie wybierz szablon projektu **usługi Azure Functions.**</span><span class="sxs-lookup"><span data-stu-id="70269-120">Then select the **Azure Functions** project template.</span></span> <span data-ttu-id="70269-121">W polu tekstowym **Nazwa** wpisz "SentimentAnalysisFunctionsApp", a następnie wybierz przycisk **OK.**</span><span class="sxs-lookup"><span data-stu-id="70269-121">In the **Name** text box, type "SentimentAnalysisFunctionsApp" and then select the **OK** button.</span></span>
1. <span data-ttu-id="70269-122">W oknie dialogowym **Nowy projekt** otwórz okno rozwijane nad opcjami projektu i wybierz pozycję Usługi Azure Functions w **wersji 2 (.NET Core).**</span><span class="sxs-lookup"><span data-stu-id="70269-122">In the **New Project** dialog, open the dropdown above the project options and select **Azure Functions v2 (.NET Core)**.</span></span> <span data-ttu-id="70269-123">Następnie wybierz projekt **wyzwalacza Http,** a następnie wybierz przycisk **OK.**</span><span class="sxs-lookup"><span data-stu-id="70269-123">Then, select the **Http trigger** project and then select the **OK** button.</span></span>
1. <span data-ttu-id="70269-124">Utwórz katalog o nazwie *MLModelki* w projekcie, aby zapisać model:</span><span class="sxs-lookup"><span data-stu-id="70269-124">Create a directory named *MLModels* in your project to save your model:</span></span>

    <span data-ttu-id="70269-125">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Dodaj** > **nowy folder**.</span><span class="sxs-lookup"><span data-stu-id="70269-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="70269-126">Wpisz "MLModel" i naciśnij enter.</span><span class="sxs-lookup"><span data-stu-id="70269-126">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="70269-127">Zainstaluj **Microsoft.ML NuGet Package** w wersji **1.3.1:**</span><span class="sxs-lookup"><span data-stu-id="70269-127">Install the **Microsoft.ML NuGet Package** version **1.3.1**:</span></span>

    <span data-ttu-id="70269-128">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="70269-128">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="70269-129">Wybierz "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj **Microsoft.ML**, wybierz ten pakiet na liście i wybierz przycisk **Zainstaluj.**</span><span class="sxs-lookup"><span data-stu-id="70269-129">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="70269-130">Wybierz przycisk **OK** w oknie **dialogowym Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="70269-130">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="70269-131">Zainstaluj **pakiet Microsoft.Azure.Functions.Extensions NuGet:**</span><span class="sxs-lookup"><span data-stu-id="70269-131">Install the **Microsoft.Azure.Functions.Extensions NuGet Package**:</span></span>

    <span data-ttu-id="70269-132">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="70269-132">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="70269-133">Wybierz "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj pozycję **Microsoft.Azure.Functions.Extensions**, wybierz ten pakiet na liście i wybierz przycisk **Zainstaluj.**</span><span class="sxs-lookup"><span data-stu-id="70269-133">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Azure.Functions.Extensions**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="70269-134">Wybierz przycisk **OK** w oknie **dialogowym Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="70269-134">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="70269-135">Zainstaluj **Microsoft.Extensions.ML NuGet Package** w wersji **0.15.1:**</span><span class="sxs-lookup"><span data-stu-id="70269-135">Install the **Microsoft.Extensions.ML NuGet Package** version **0.15.1**:</span></span>

    <span data-ttu-id="70269-136">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="70269-136">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="70269-137">Wybierz "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj **Microsoft.Extensions.ML**, wybierz ten pakiet na liście i wybierz przycisk **Zainstaluj.**</span><span class="sxs-lookup"><span data-stu-id="70269-137">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="70269-138">Wybierz przycisk **OK** w oknie **dialogowym Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="70269-138">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="70269-139">Zainstaluj pakiet **Microsoft.NET.Sdk.Functions NuGet w** wersji **1.0.31:**</span><span class="sxs-lookup"><span data-stu-id="70269-139">Install the **Microsoft.NET.Sdk.Functions NuGet Package** version **1.0.31**:</span></span>

    <span data-ttu-id="70269-140">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="70269-140">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="70269-141">Wybierz opcję "nuget.org" jako źródło pakietu, wybierz kartę Zainstalowane, wyszukaj pozycję **Microsoft.NET.Sdk.Functions**, wybierz ten pakiet na liście, wybierz **pozycję 1.0.31** z listy rozwijanej Wersja i wybierz przycisk **Aktualizuj.**</span><span class="sxs-lookup"><span data-stu-id="70269-141">Choose "nuget.org" as the Package source, select the Installed tab, search for **Microsoft.NET.Sdk.Functions**, select that package in the list, select **1.0.31** from the Version dropdown, and select the **Update** button.</span></span> <span data-ttu-id="70269-142">Wybierz przycisk **OK** w oknie **dialogowym Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="70269-142">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="add-pre-trained-model-to-project"></a><span data-ttu-id="70269-143">Dodawanie wstępnie przeszkolonego modelu do projektu</span><span class="sxs-lookup"><span data-stu-id="70269-143">Add pre-trained model to project</span></span>

1. <span data-ttu-id="70269-144">Skopiuj wstępnie utworzony model do folderu *MLModels.*</span><span class="sxs-lookup"><span data-stu-id="70269-144">Copy your pre-built model to the *MLModels* folder.</span></span>
1. <span data-ttu-id="70269-145">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy wstępnie utworzony plik modelu i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="70269-145">In Solution Explorer, right-click your pre-built model file and select **Properties**.</span></span> <span data-ttu-id="70269-146">W obszarze **Zaawansowane**zmień wartość **kopiuj na Katalog wyjściowy** na **Kopiuj, jeśli jest nowszy**.</span><span class="sxs-lookup"><span data-stu-id="70269-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="create-azure-function-to-analyze-sentiment"></a><span data-ttu-id="70269-147">Tworzenie funkcji platformy Azure w celu analizowania tonacji</span><span class="sxs-lookup"><span data-stu-id="70269-147">Create Azure Function to analyze sentiment</span></span>

<span data-ttu-id="70269-148">Utwórz klasę do przewidywania tonacji.</span><span class="sxs-lookup"><span data-stu-id="70269-148">Create a class to predict sentiment.</span></span> <span data-ttu-id="70269-149">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="70269-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="70269-150">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="70269-150">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="70269-151">W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Funkcja platformy **Azure** i zmień pole **Nazwa** na *AnalyzeSentiment.cs*.</span><span class="sxs-lookup"><span data-stu-id="70269-151">In the **Add New Item** dialog box, select **Azure Function** and change the **Name** field to *AnalyzeSentiment.cs*.</span></span> <span data-ttu-id="70269-152">Następnie wybierz przycisk **Dodaj.**</span><span class="sxs-lookup"><span data-stu-id="70269-152">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="70269-153">W oknie dialogowym **Nowa funkcja platformy Azure** wybierz pozycję **Wyzwalacz http**.</span><span class="sxs-lookup"><span data-stu-id="70269-153">In the **New Azure Function** dialog box, select **Http Trigger**.</span></span> <span data-ttu-id="70269-154">Następnie wybierz przycisk **OK.**</span><span class="sxs-lookup"><span data-stu-id="70269-154">Then, select the **OK** button.</span></span>

    <span data-ttu-id="70269-155">Plik *AnalyzeSentiment.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="70269-155">The *AnalyzeSentiment.cs* file opens in the code editor.</span></span> <span data-ttu-id="70269-156">Dodaj następującą `using` instrukcję do górnej części *AnalyzeSentiment.cs:*</span><span class="sxs-lookup"><span data-stu-id="70269-156">Add the following `using` statement to the top of *AnalyzeSentiment.cs*:</span></span>

    [!code-csharp [AnalyzeUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L1-L11)]

    <span data-ttu-id="70269-157">Domyślnie klasą `AnalyzeSentiment` `static`jest .</span><span class="sxs-lookup"><span data-stu-id="70269-157">By default, the `AnalyzeSentiment` class is `static`.</span></span> <span data-ttu-id="70269-158">Pamiętaj, aby `static` usunąć słowo kluczowe z definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="70269-158">Make sure to remove the `static` keyword from the class definition.</span></span>

    ```csharp
    public class AnalyzeSentiment
    {

    }
    ```

## <a name="create-data-models"></a><span data-ttu-id="70269-159">Tworzenie modeli danych</span><span class="sxs-lookup"><span data-stu-id="70269-159">Create data models</span></span>

<span data-ttu-id="70269-160">Należy utworzyć niektóre klasy dla danych wejściowych i prognoz.</span><span class="sxs-lookup"><span data-stu-id="70269-160">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="70269-161">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="70269-161">Add a new class to your project:</span></span>

1. <span data-ttu-id="70269-162">Utwórz katalog o nazwie *DataModels* w projekcie, aby zapisać modele danych: W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Dodaj > nowy folder**.</span><span class="sxs-lookup"><span data-stu-id="70269-162">Create a directory named *DataModels* in your project to save your data models: In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="70269-163">Wpisz "DataModels" i naciśnij enter.</span><span class="sxs-lookup"><span data-stu-id="70269-163">Type "DataModels" and hit Enter.</span></span>
2. <span data-ttu-id="70269-164">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy katalog *DataModels,* a następnie wybierz polecenie **Dodaj > Nowy element**.</span><span class="sxs-lookup"><span data-stu-id="70269-164">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
3. <span data-ttu-id="70269-165">W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="70269-165">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="70269-166">Następnie wybierz przycisk **Dodaj.**</span><span class="sxs-lookup"><span data-stu-id="70269-166">Then, select the **Add** button.</span></span>

    <span data-ttu-id="70269-167">Plik *SentimentData.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="70269-167">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="70269-168">Dodaj następującą instrukcję za pomocą do górnej części *SentimentData.cs:*</span><span class="sxs-lookup"><span data-stu-id="70269-168">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp [SentimentDataUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L1)]

    <span data-ttu-id="70269-169">Usuń istniejącą definicję klasy i dodaj następujący kod do pliku *SentimentData.cs:*</span><span class="sxs-lookup"><span data-stu-id="70269-169">Remove the existing class definition and add the following code to the *SentimentData.cs* file:</span></span>

    [!code-csharp [SentimentData](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L5-L13)]

4. <span data-ttu-id="70269-170">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy katalog *DataModels,* a następnie wybierz polecenie **Dodaj > Nowy element**.</span><span class="sxs-lookup"><span data-stu-id="70269-170">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="70269-171">W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="70269-171">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="70269-172">Następnie wybierz przycisk **Dodaj.**</span><span class="sxs-lookup"><span data-stu-id="70269-172">Then, select the **Add** button.</span></span> <span data-ttu-id="70269-173">Plik *SentimentPrediction.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="70269-173">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="70269-174">Dodaj następującą instrukcję za pomocą do górnej części *SentimentPrediction.cs:*</span><span class="sxs-lookup"><span data-stu-id="70269-174">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    [!code-csharp [SentimentPredictionUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L1)]

    <span data-ttu-id="70269-175">Usuń istniejącą definicję klasy i dodaj następujący kod do pliku *SentimentPrediction.cs:*</span><span class="sxs-lookup"><span data-stu-id="70269-175">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    [!code-csharp [SentimentPrediction](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L5-L14)]

    <span data-ttu-id="70269-176">`SentimentPrediction`dziedziczy, `SentimentData` z którego zapewnia dostęp `SentimentText` do oryginalnych danych we właściwości, jak również dane wyjściowe generowane przez model.</span><span class="sxs-lookup"><span data-stu-id="70269-176">`SentimentPrediction` inherits from `SentimentData` which provides access to the original data in the `SentimentText` property as well as the output generated by the model.</span></span>

## <a name="register-predictionenginepool-service"></a><span data-ttu-id="70269-177">Zarejestruj usługę PredictionEnginePool</span><span class="sxs-lookup"><span data-stu-id="70269-177">Register PredictionEnginePool service</span></span>

<span data-ttu-id="70269-178">Aby dokonać pojedynczego przewidywania, należy [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)utworzyć plik .</span><span class="sxs-lookup"><span data-stu-id="70269-178">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="70269-179">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny dla wątków.</span><span class="sxs-lookup"><span data-stu-id="70269-179">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="70269-180">Ponadto należy utworzyć wystąpienie go wszędzie tam, gdzie jest to potrzebne w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70269-180">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="70269-181">W miarę rozwoju aplikacji proces ten może stać się nie do opanowania.</span><span class="sxs-lookup"><span data-stu-id="70269-181">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="70269-182">Aby zwiększyć wydajność i bezpieczeństwo wątków, należy `PredictionEnginePool` użyć kombinacji iniekcji zależności i usługi, która tworzy [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) obiekty [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do użycia w całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70269-182">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

<span data-ttu-id="70269-183">Poniższe łącze zawiera więcej informacji, jeśli chcesz dowiedzieć się więcej o [iniekcji zależności](https://en.wikipedia.org/wiki/Dependency_injection).</span><span class="sxs-lookup"><span data-stu-id="70269-183">The following link provides more information if you want to learn more about [dependency injection](https://en.wikipedia.org/wiki/Dependency_injection).</span></span>

1. <span data-ttu-id="70269-184">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="70269-184">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="70269-185">W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *Startup.cs*.</span><span class="sxs-lookup"><span data-stu-id="70269-185">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *Startup.cs*.</span></span> <span data-ttu-id="70269-186">Następnie wybierz przycisk **Dodaj.**</span><span class="sxs-lookup"><span data-stu-id="70269-186">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="70269-187">Dodaj następujące instrukcje do górnej części *Startup.cs:*</span><span class="sxs-lookup"><span data-stu-id="70269-187">Add the following using statements to the top of *Startup.cs*:</span></span>

    [!code-csharp [StartupUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L1-L6)]

1. <span data-ttu-id="70269-188">Usuń istniejący kod poniżej using instrukcji i dodać następujący kod:</span><span class="sxs-lookup"><span data-stu-id="70269-188">Remove the existing code below the using statements and add the following code:</span></span>

    ```csharp
    [assembly: FunctionsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        public class Startup : FunctionsStartup
        {

        }
    }
    ```

1. <span data-ttu-id="70269-189">Zdefiniuj zmienne do przechowywania środowiska, w którym działa aplikacja, oraz ścieżki pliku, w której znajduje się model wewnątrz `Startup` klasy</span><span class="sxs-lookup"><span data-stu-id="70269-189">Define variables to store the environment the app is running in and the file path where the model is located inside the `Startup` class</span></span>

    [!code-csharp [DefineStartupVars](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L13-L14)]

1. <span data-ttu-id="70269-190">Poniżej utwórz konstruktora, aby `_environment` `_modelPath` ustawić wartości i zmienne.</span><span class="sxs-lookup"><span data-stu-id="70269-190">Below that, create a constructor to set the values of the `_environment` and `_modelPath` variables.</span></span> <span data-ttu-id="70269-191">Gdy aplikacja jest uruchomiona lokalnie, domyślnym środowiskiem jest *Programistyczne*.</span><span class="sxs-lookup"><span data-stu-id="70269-191">When the application is running locally, the default environment is *Development*.</span></span>

    [!code-csharp [StartupCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L16-L29)]

1. <span data-ttu-id="70269-192">Następnie dodaj nową metodę `Configure` wywoływaną `PredictionEnginePool` do rejestrowania usługi poniżej konstruktora.</span><span class="sxs-lookup"><span data-stu-id="70269-192">Then, add a new method called `Configure` to register the `PredictionEnginePool` service below the constructor.</span></span>

    [!code-csharp [ConfigureServices](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L31-L35)]

<span data-ttu-id="70269-193">Na wysokim poziomie ten kod inicjuje obiekty i usługi automatycznie do późniejszego użycia, gdy jest to wymagane przez aplikację, zamiast ręcznie to zrobić.</span><span class="sxs-lookup"><span data-stu-id="70269-193">At a high level, this code initializes the objects and services automatically for later use when requested by the application instead of having to manually do it.</span></span>

<span data-ttu-id="70269-194">Modele uczenia maszynowego nie są statyczne.</span><span class="sxs-lookup"><span data-stu-id="70269-194">Machine learning models are not static.</span></span> <span data-ttu-id="70269-195">W miarę udostępniania nowych danych szkoleniowych model jest ponownie przeszkolony i ponownie rozmieszczony.</span><span class="sxs-lookup"><span data-stu-id="70269-195">As new training data becomes available, the model is retrained and redeployed.</span></span> <span data-ttu-id="70269-196">Jednym ze sposobów, aby uzyskać najnowszą wersję modelu do aplikacji jest ponowne wdrożenie całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70269-196">One way to get the latest version of the model into your application is to redeploy the entire application.</span></span> <span data-ttu-id="70269-197">Powoduje to jednak wprowadzenie przestojów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70269-197">However, this introduces application downtime.</span></span> <span data-ttu-id="70269-198">Usługa `PredictionEnginePool` zapewnia mechanizm do ponownego ładowania zaktualizowanego modelu bez przejmowania aplikacji w dół.</span><span class="sxs-lookup"><span data-stu-id="70269-198">The `PredictionEnginePool` service provides a mechanism to reload an updated model without taking your application down.</span></span>

<span data-ttu-id="70269-199">Ustaw `watchForChanges` parametr `true`na , `PredictionEnginePool` a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) rozpoczyna się, który nasłuchuje powiadomień o zmianie systemu plików i wywołuje zdarzenia, gdy nastąpi zmiana w pliku.</span><span class="sxs-lookup"><span data-stu-id="70269-199">Set the `watchForChanges` parameter to `true`, and the `PredictionEnginePool` starts a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) that listens to the file system change notifications and raises events when there is a change to the file.</span></span> <span data-ttu-id="70269-200">Monituje o `PredictionEnginePool` automatyczne ponowne załadowanie modelu.</span><span class="sxs-lookup"><span data-stu-id="70269-200">This prompts the `PredictionEnginePool` to automatically reload the model.</span></span>

<span data-ttu-id="70269-201">Model jest identyfikowany `modelName` przez parametr, dzięki czemu więcej niż jeden model na aplikację można ponownie załadować po zmianie.</span><span class="sxs-lookup"><span data-stu-id="70269-201">The model is identified by the `modelName` parameter so that more than one model per application can be reloaded upon change.</span></span>

> [!TIP]
> <span data-ttu-id="70269-202">Alternatywnie można użyć `FromUri` metody podczas pracy z modelami przechowywanymi zdalnie.</span><span class="sxs-lookup"><span data-stu-id="70269-202">Alternatively, you can use the `FromUri` method when working with models stored remotely.</span></span> <span data-ttu-id="70269-203">Zamiast obserwować zdarzenia zmiany `FromUri` pliku, sonduje zdalną lokalizację pod kątem zmian.</span><span class="sxs-lookup"><span data-stu-id="70269-203">Rather than watching for file changed events, `FromUri` polls the remote location for changes.</span></span> <span data-ttu-id="70269-204">Domyślnie interwał sondowania wynosi 5 minut.</span><span class="sxs-lookup"><span data-stu-id="70269-204">The polling interval defaults to 5 minutes.</span></span> <span data-ttu-id="70269-205">Można zwiększyć lub zmniejszyć interwał sondowania na podstawie wymagań aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70269-205">You can increase or decrease the polling interval based on your application's requirements.</span></span> <span data-ttu-id="70269-206">W przykładzie kodu `PredictionEnginePool` poniżej sonduje model przechowywany w określonym identyfikatorze URI co minutę.</span><span class="sxs-lookup"><span data-stu-id="70269-206">In the code sample below, the `PredictionEnginePool` polls the model stored at the specified URI every minute.</span></span>
>
>```csharp
>builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="load-the-model-into-the-function"></a><span data-ttu-id="70269-207">Załaduj model do funkcji</span><span class="sxs-lookup"><span data-stu-id="70269-207">Load the model into the function</span></span>

<span data-ttu-id="70269-208">Wstaw następujący kod wewnątrz *analyzesentiment* klasy:</span><span class="sxs-lookup"><span data-stu-id="70269-208">Insert the following code inside the *AnalyzeSentiment* class:</span></span>

[!code-csharp [AnalyzeCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L18-L24)]

<span data-ttu-id="70269-209">Ten kod `PredictionEnginePool` przypisuje, przekazując go do konstruktora funkcji, które można uzyskać za pośrednictwem iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="70269-209">This code assigns the `PredictionEnginePool` by passing it to the function's constructor which you get via dependency injection.</span></span>

## <a name="use-the-model-to-make-predictions"></a><span data-ttu-id="70269-210">Użyj modelu, aby przewidywać</span><span class="sxs-lookup"><span data-stu-id="70269-210">Use the model to make predictions</span></span>

<span data-ttu-id="70269-211">Zastąp istniejącą implementację *Metody Uruchamianie* w *klasie AnalyzeSentiment* następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="70269-211">Replace the existing implementation of *Run* method in *AnalyzeSentiment* class with the following code:</span></span>

[!code-csharp [AnalyzeRunMethod](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L26-L45)]

<span data-ttu-id="70269-212">Podczas `Run` wykonywania metody, przychodzące dane z żądania HTTP jest deserialized `PredictionEnginePool`i używane jako dane wejściowe dla .</span><span class="sxs-lookup"><span data-stu-id="70269-212">When the `Run` method executes, the incoming data from the HTTP request is deserialized and used as input for the `PredictionEnginePool`.</span></span> <span data-ttu-id="70269-213">Metoda `Predict` jest następnie wywoływana do `SentimentAnalysisModel` prognoz przy `Startup` użyciu zarejestrowanych w klasie i zwraca wyniki z powrotem do użytkownika, jeśli zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="70269-213">The `Predict` method is then called to make predictions using the `SentimentAnalysisModel` registered in the `Startup` class and returns the results back to the user if successful.</span></span>

## <a name="test-locally"></a><span data-ttu-id="70269-214">Testowanie lokalnie</span><span class="sxs-lookup"><span data-stu-id="70269-214">Test locally</span></span>

<span data-ttu-id="70269-215">Teraz, gdy wszystko jest skonfigurowane, nadszedł czas, aby przetestować aplikację:</span><span class="sxs-lookup"><span data-stu-id="70269-215">Now that everything is set up, it's time to test the application:</span></span>

1. <span data-ttu-id="70269-216">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="70269-216">Run the application</span></span>
1. <span data-ttu-id="70269-217">Otwórz program PowerShell i wprowadź kod w wierszu polecenia, w którym port jest portem, na którym jest uruchomiona aplikacja.</span><span class="sxs-lookup"><span data-stu-id="70269-217">Open PowerShell and enter the code into the prompt where PORT is the port your application is running on.</span></span> <span data-ttu-id="70269-218">Zazwyczaj port jest 7071.</span><span class="sxs-lookup"><span data-stu-id="70269-218">Typically the port is 7071.</span></span>

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="70269-219">Jeśli się powiedzie, dane wyjściowe powinny wyglądać podobnie do poniższego tekstu:</span><span class="sxs-lookup"><span data-stu-id="70269-219">If successful, the output should look similar to the text below:</span></span>

    ```powershell
    Negative
    ```

<span data-ttu-id="70269-220">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="70269-220">Congratulations!</span></span> <span data-ttu-id="70269-221">Pomyślnie służył modelu do prognozowania za pośrednictwem Internetu przy użyciu funkcji platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="70269-221">You have successfully served your model to make predictions over the internet using an Azure Function.</span></span>

## <a name="next-steps"></a><span data-ttu-id="70269-222">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="70269-222">Next Steps</span></span>

- [<span data-ttu-id="70269-223">Wdrażanie na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="70269-223">Deploy to Azure</span></span>](/azure/azure-functions/functions-develop-vs#publish-to-azure)
