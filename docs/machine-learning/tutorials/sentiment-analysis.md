---
title: Użyj strukturze ML.NET w scenariuszu klasyfikacji binarnej analizy tonacji
description: Dowiedz się, jak używać strukturze ML.NET w scenariuszu klasyfikacji binarnej zrozumienie, jak na potrzeby prognozowania tonacji podjąć odpowiednie działania.
ms.date: 06/04/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 57ade448f5773bee3474cb46bec8ad33e3afbee3
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2018
ms.locfileid: "43000391"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a><span data-ttu-id="ec830-103">Samouczek: Używanie strukturze ML.NET w scenariuszu klasyfikacji binarnej analizy tonacji</span><span class="sxs-lookup"><span data-stu-id="ec830-103">Tutorial: Use ML.NET in a sentiment analysis binary classification scenario</span></span>

> [!NOTE]
> <span data-ttu-id="ec830-104">W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="ec830-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="ec830-105">Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="ec830-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="ec830-106">Ten przykładowy samouczek przedstawia tworzenie klasyfikatora tonacji za pomocą aplikacji konsoli .NET Core przy użyciu języka C# w programie Visual Studio 2017 przy użyciu strukturze ML.NET.</span><span class="sxs-lookup"><span data-stu-id="ec830-106">This sample tutorial illustrates using ML.NET to create a sentiment classifier via a .NET Core console application using C# in Visual Studio 2017.</span></span>

<span data-ttu-id="ec830-107">W tym samouczku dowiesz się, jak:</span><span class="sxs-lookup"><span data-stu-id="ec830-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="ec830-108">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="ec830-108">Understand the problem</span></span>
> * <span data-ttu-id="ec830-109">Wybierz zadanie uczenia odpowiedniej maszyny</span><span class="sxs-lookup"><span data-stu-id="ec830-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="ec830-110">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="ec830-110">Prepare your data</span></span>
> * <span data-ttu-id="ec830-111">Tworzenie potoku uczenia</span><span class="sxs-lookup"><span data-stu-id="ec830-111">Create the learning pipeline</span></span>
> * <span data-ttu-id="ec830-112">Ładowanie klasyfikatora</span><span class="sxs-lookup"><span data-stu-id="ec830-112">Load a classifier</span></span>
> * <span data-ttu-id="ec830-113">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="ec830-113">Train the model</span></span>
> * <span data-ttu-id="ec830-114">Ocena modelu za pomocą innego zestawu danych</span><span class="sxs-lookup"><span data-stu-id="ec830-114">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="ec830-115">Przewidywanie wyników danych testów przy użyciu modelu</span><span class="sxs-lookup"><span data-stu-id="ec830-115">Predict the test data outcomes with the model</span></span>

## <a name="sentiment-analysis-sample-overview"></a><span data-ttu-id="ec830-116">Omówienie przykładowych analizy tonacji</span><span class="sxs-lookup"><span data-stu-id="ec830-116">Sentiment analysis sample overview</span></span>

<span data-ttu-id="ec830-117">Próbka jest aplikacją konsoli, która używa strukturze ML.NET do nauczenia modelu, która klasyfikuje i przewiduje wskaźniki nastrojów klientów, jak dodatnie lub ujemne.</span><span class="sxs-lookup"><span data-stu-id="ec830-117">The sample is a console app that uses ML.NET to train a model that classifies and predicts sentiment as either positive or negative.</span></span> <span data-ttu-id="ec830-118">Oblicza model z drugiego zestawu danych do analizy jakości dostawców.</span><span class="sxs-lookup"><span data-stu-id="ec830-118">It also evaluates the model with a second dataset for quality analysis.</span></span> <span data-ttu-id="ec830-119">Zestawy danych wskaźniki nastrojów klientów są od projektu WikiDetox.</span><span class="sxs-lookup"><span data-stu-id="ec830-119">The sentiment datasets are from the WikiDetox project.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ec830-120">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="ec830-120">Prerequisites</span></span>

* <span data-ttu-id="ec830-121">[Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".</span><span class="sxs-lookup"><span data-stu-id="ec830-121">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="ec830-122">[Wikipedia detox wiersza danych tabulacji pliku (wikiPedia-detox-250-linia data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).</span><span class="sxs-lookup"><span data-stu-id="ec830-122">The [Wikipedia detox line data tab separated file (wikiPedia-detox-250-line-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span>
* <span data-ttu-id="ec830-123">[Wikipedia detox wiersza testu tabulacji pliku (wikipedia-detox-250-linia test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).</span><span class="sxs-lookup"><span data-stu-id="ec830-123">The [Wikipedia detox line test tab separated file (wikipedia-detox-250-line-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="ec830-124">Maszyny uczenie się przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ec830-124">Machine learning workflow</span></span>

<span data-ttu-id="ec830-125">W tym samouczku poniżej przepływu pracy, który umożliwia proces przenoszenia w sposób uporządkowany uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="ec830-125">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="ec830-126">Fazy przepływu pracy są następujące:</span><span class="sxs-lookup"><span data-stu-id="ec830-126">The workflow phases are as follows:</span></span>

1. <span data-ttu-id="ec830-127">**Omówienie problemu**</span><span class="sxs-lookup"><span data-stu-id="ec830-127">**Understand the problem**</span></span>
2. <span data-ttu-id="ec830-128">**Pozyskiwanie danych**</span><span class="sxs-lookup"><span data-stu-id="ec830-128">**Ingest the data**</span></span>
3. <span data-ttu-id="ec830-129">**Wstępne przetwarzanie danych i inżynieria funkcji**</span><span class="sxs-lookup"><span data-stu-id="ec830-129">**Data preprocess and feature engineering**</span></span>
4. <span data-ttu-id="ec830-130">**Uczenia i przewidywania modelu**</span><span class="sxs-lookup"><span data-stu-id="ec830-130">**Train and predict the model**</span></span>
5. <span data-ttu-id="ec830-131">**Ocena modelu**</span><span class="sxs-lookup"><span data-stu-id="ec830-131">**Evaluate the model**</span></span>
6. <span data-ttu-id="ec830-132">**Operacjonalizacja modelu**</span><span class="sxs-lookup"><span data-stu-id="ec830-132">**Model operationalization**</span></span>

### <a name="understand-the-problem"></a><span data-ttu-id="ec830-133">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="ec830-133">Understand the problem</span></span>

<span data-ttu-id="ec830-134">Należy najpierw zrozumieć, dzięki czemu można podzielić je w dół do części obsługujące kompilowanie i uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="ec830-134">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="ec830-135">Przerywanie problem w dół do przewidywania i ocena wyników.</span><span class="sxs-lookup"><span data-stu-id="ec830-135">Breaking the problem down you to predict and evaluate the results.</span></span>

<span data-ttu-id="ec830-136">Ten problem, w tym samouczku jest zrozumienie, przychodzące tonacji komentarz witryny sieci Web podejmowanie odpowiednich działań.</span><span class="sxs-lookup"><span data-stu-id="ec830-136">The problem for this tutorial is to understand incoming website comment sentiment to take the appropriate action.</span></span>

<span data-ttu-id="ec830-137">Ten problem można podzielić do tonacji tekstu i wartości tonacji danych mają do nauczenia modelu, z, a wartości tonacji przewidywane, można obliczyć, a następnie za pomocą pod względem.</span><span class="sxs-lookup"><span data-stu-id="ec830-137">You can break down the problem to the sentiment text and sentiment value for the data you want to train the model with, and a predicted sentiment value that you can evaluate and then use operationally.</span></span>

<span data-ttu-id="ec830-138">Następnie należy **określić** tonacji, która ułatwia wybieranie zadań uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="ec830-138">You then need to **determine** the sentiment, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="ec830-139">Wybierz zadanie uczenia odpowiedniej maszyny</span><span class="sxs-lookup"><span data-stu-id="ec830-139">Select the appropriate machine learning task</span></span>

<span data-ttu-id="ec830-140">W rozwiązaniu tego problemu znasz następujące fakty:</span><span class="sxs-lookup"><span data-stu-id="ec830-140">With this problem, you know the following facts:</span></span>

<span data-ttu-id="ec830-141">Szkolenie danych: komentarze witryny sieci Web może być dodatnia lub ujemna (**tonacji**).</span><span class="sxs-lookup"><span data-stu-id="ec830-141">Training data: website comments can be positive or negative (**sentiment**).</span></span>
<span data-ttu-id="ec830-142">Przewidywanie **tonacji** nowego komentarza witryny sieci Web, dodatnie lub ujemne, takie jak w następujących przykładach:</span><span class="sxs-lookup"><span data-stu-id="ec830-142">Predict the **sentiment** of a new website comment, either positive or negative, such as in the following examples:</span></span>

* <span data-ttu-id="ec830-143">Punktowanych — Dodawanie żadnego znaczenia do Wikipedia.</span><span class="sxs-lookup"><span data-stu-id="ec830-143">Please refrain from adding nonsense to Wikipedia.</span></span>
* <span data-ttu-id="ec830-144">Jest on najlepsze, a artykuł powinien oznacza, że.</span><span class="sxs-lookup"><span data-stu-id="ec830-144">He is the best, and the article should say that.</span></span>

<span data-ttu-id="ec830-145">Zadania uczenia maszyny klasyfikacji najlepiej nadaje się dla tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="ec830-145">The classification machine learning task is best suited for this scenario.</span></span>

### <a name="about-the-classification-task"></a><span data-ttu-id="ec830-146">O zadaniu klasyfikacji</span><span class="sxs-lookup"><span data-stu-id="ec830-146">About the classification task</span></span>

<span data-ttu-id="ec830-147">Klasyfikacja jest zadanie uczenia maszynowego, które są używane dane do **określić** kategorii, typ lub klasa elementu lub wiersza danych.</span><span class="sxs-lookup"><span data-stu-id="ec830-147">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="ec830-148">Na przykład można użyć klasyfikacji:</span><span class="sxs-lookup"><span data-stu-id="ec830-148">For example, you can use classification to:</span></span>

* <span data-ttu-id="ec830-149">Zidentyfikuj tonacji jako dodatnia lub ujemna.</span><span class="sxs-lookup"><span data-stu-id="ec830-149">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="ec830-150">Klasyfikowanie wiadomości e-mail jako spam, wiadomości-śmieci lub właściwej.</span><span class="sxs-lookup"><span data-stu-id="ec830-150">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="ec830-151">Ustal, czy pacjent laboratorium przykładowe dane stanowią cancerous.</span><span class="sxs-lookup"><span data-stu-id="ec830-151">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="ec830-152">Klienci na kategorie według ich tendencje do odpowiedzi na kampanię sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="ec830-152">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="ec830-153">Klasyfikacja zadań są często jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="ec830-153">Classification tasks are frequently one of the following types:</span></span>

* <span data-ttu-id="ec830-154">Plik binarny: A i B.</span><span class="sxs-lookup"><span data-stu-id="ec830-154">Binary: either A or B.</span></span>
* <span data-ttu-id="ec830-155">Kontra: wielu kategorii, które można przewidzieć przy użyciu pojedynczego modelu.</span><span class="sxs-lookup"><span data-stu-id="ec830-155">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="ec830-156">Tworzenie aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="ec830-156">Create a console application</span></span>

1. <span data-ttu-id="ec830-157">Otwórz program Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="ec830-157">Open Visual Studio 2017.</span></span> <span data-ttu-id="ec830-158">Wybierz **pliku** > **New** > **projektu** z paska menu.</span><span class="sxs-lookup"><span data-stu-id="ec830-158">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="ec830-159">W *nowy projekt*\* okno dialogowe, wybierz opcję **Visual C#** węzła następuje **platformy .NET Core** węzła.</span><span class="sxs-lookup"><span data-stu-id="ec830-159">In the *New Project*\* dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="ec830-160">Następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="ec830-160">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="ec830-161">W **nazwa** pole tekstowe, wpisz "SentimentAnalysis", a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="ec830-161">In the **Name** text box, type "SentimentAnalysis" and then select the **OK** button.</span></span>

2. <span data-ttu-id="ec830-162">Utwórz katalog o nazwie *danych* w projekcie, aby zapisać pliki zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="ec830-162">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="ec830-163">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nad projektem i wybierz **Dodaj** > **nowy Folder**.</span><span class="sxs-lookup"><span data-stu-id="ec830-163">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="ec830-164">Wpisz "Dane", a następnie naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="ec830-164">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="ec830-165">Zainstaluj **pakietu NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="ec830-165">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="ec830-166">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="ec830-166">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="ec830-167">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="ec830-167">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="ec830-168">Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.</span><span class="sxs-lookup"><span data-stu-id="ec830-168">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="ec830-169">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="ec830-169">Prepare your data</span></span>

1. <span data-ttu-id="ec830-170">Pobierz [WikiPedia detox-250-linia data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) i [wikipedia-detox-250-linia test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) danych ustawia i zapisywanie ich *danych* wcześniej utworzony folder.</span><span class="sxs-lookup"><span data-stu-id="ec830-170">Download the [WikiPedia detox-250-line-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) and the [wikipedia-detox-250-line-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="ec830-171">Szkolenie modeli modelu uczenia maszynowego na pierwszego zestawu danych, a drugi może służyć do oceny, jak dokładna jest model.</span><span class="sxs-lookup"><span data-stu-id="ec830-171">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="ec830-172">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy każdy z \*pliki tsv i wybierz pozycję **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="ec830-172">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="ec830-173">W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="ec830-173">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="ec830-174">Tworzenie klas i definiowania ścieżek</span><span class="sxs-lookup"><span data-stu-id="ec830-174">Create classes and define paths</span></span>

<span data-ttu-id="ec830-175">Dodaj następujące dodatkowe `using` instrukcji na górze *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="ec830-175">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="ec830-176">Musisz utworzyć trzy pola globalnego na potrzeby przechowywania ścieżek do ostatnio pobrane pliki:</span><span class="sxs-lookup"><span data-stu-id="ec830-176">You need to create three global fields to hold the paths to the recently downloaded files:</span></span>

* <span data-ttu-id="ec830-177">`_dataPath` zawiera ścieżkę do zestawu danych, używane do trenowania modelu.</span><span class="sxs-lookup"><span data-stu-id="ec830-177">`_dataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="ec830-178">`_testDataPath` zawiera ścieżkę do zestawu danych, używane do oceny modelu.</span><span class="sxs-lookup"><span data-stu-id="ec830-178">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="ec830-179">`_modelPath` ma ścieżkę, w którym jest zapisany trenowanego modelu.</span><span class="sxs-lookup"><span data-stu-id="ec830-179">`_modelPath` has the path where the trained model is saved.</span></span>

<span data-ttu-id="ec830-180">Dodaj następujący kod po prawej stronie wiersza powyżej `Main` metodę, aby określić tych ścieżek:</span><span class="sxs-lookup"><span data-stu-id="ec830-180">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Declare file variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#2 "Declare variables to store data files")]

<span data-ttu-id="ec830-181">Musisz utworzyć niektóre klasy dla danych wejściowych i prognozy.</span><span class="sxs-lookup"><span data-stu-id="ec830-181">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="ec830-182">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="ec830-182">Add a new class to your project:</span></span>

1. <span data-ttu-id="ec830-183">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="ec830-183">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="ec830-184">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="ec830-184">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="ec830-185">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="ec830-185">Then, select the **Add** button.</span></span>

    <span data-ttu-id="ec830-186">*SentimentData.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="ec830-186">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="ec830-187">Dodaj następujący kod `using` instrukcji na górze *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="ec830-187">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#1 "Add necessary usings")]

<span data-ttu-id="ec830-188">Usuń istniejącą definicję klasy i Dodaj następujący kod, który zawiera dwie klasy `SentimentData` i `SentimentPrediction`, *SentimentData.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="ec830-188">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#2 "Declare data record types")]

<span data-ttu-id="ec830-189">`SentimentData` Klasa wejściowy zestaw danych i ma `float` (`Sentiment`) zawierający wartości tonacji dodatnie lub ujemne, a ciąg komentarza (`SentimentText`).</span><span class="sxs-lookup"><span data-stu-id="ec830-189">`SentimentData` is the input dataset class and has a `float` (`Sentiment`) that has a value for sentiment of either positive or negative, and a string for the comment (`SentimentText`).</span></span> <span data-ttu-id="ec830-190">Oba pola mają `Column` atrybuty dołączonych do nich.</span><span class="sxs-lookup"><span data-stu-id="ec830-190">Both fields have `Column` attributes attached to them.</span></span> <span data-ttu-id="ec830-191">Ten atrybut wykonywania działań Opisuje kolejność każdego pola w pliku danych, i które `Label` pola.</span><span class="sxs-lookup"><span data-stu-id="ec830-191">This attribute describes the order of each field in the data file, and which is the `Label` field.</span></span> <span data-ttu-id="ec830-192">`SentimentPrediction` Klasa służy do prognozowania po wyszkoliła modelu.</span><span class="sxs-lookup"><span data-stu-id="ec830-192">`SentimentPrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="ec830-193">Ma ona pojedynczy atrybut typu wartość logiczna (`Sentiment`) i `PredictedLabel` `ColumnName` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ec830-193">It has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="ec830-194">`Label` Umożliwia tworzenie i uczenie modelu, a także drugiego zestawu danych do ewaluacji modelu.</span><span class="sxs-lookup"><span data-stu-id="ec830-194">The `Label` is used to create and train the model, and it's also used with a second dataset to evaluate the model.</span></span> <span data-ttu-id="ec830-195">`PredictedLabel` Używany podczas prognoz i oceny.</span><span class="sxs-lookup"><span data-stu-id="ec830-195">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="ec830-196">W wersji ewaluacyjnej używane są dane szkoleniowe, przewidywane wartości i model danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="ec830-196">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="ec830-197">W *Program.cs* pliku, zmień `Main` podpis metody, zastępując `void` z `async Task`, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ec830-197">In the *Program.cs* file, change the `Main` method signature by replacing `void` with `async Task`, as in the following example:</span></span>

```csharp
static async Task Main(string[] args) 
{

}
```

<span data-ttu-id="ec830-198">Możesz dodać `async` do `Main` z <xref:System.Threading.Tasks.Task> typ zwracany, ponieważ model są zapisywane później do pliku zip, a program musi czekać, aż do zakończenia tego zadania zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="ec830-198">You add `async` to `Main` with a <xref:System.Threading.Tasks.Task> return type because you're saving the model to a zip file later, and the program needs to wait until that external task completes.</span></span>

> [!NOTE]
> <span data-ttu-id="ec830-199">*Asynchroniczna funkcja main* metoda umożliwia użycie `await` w swojej `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="ec830-199">An *async main* method enables you to use `await` in your `Main` method.</span></span> <span data-ttu-id="ec830-200">Aby uzyskać więcej informacji, zobacz [asynchroniczna funkcja main](../../../docs/csharp/programming-guide/main-and-command-args/index.md) w Podręczniku programowania C#.</span><span class="sxs-lookup"><span data-stu-id="ec830-200">For more information, see the [async main](../../../docs/csharp/programming-guide/main-and-command-args/index.md) topic in the C# programming guide.</span></span>

<span data-ttu-id="ec830-201">Zastąp `Console.WriteLine("Hello World!")` wiersz poniższym kodem w `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="ec830-201">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[Train](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#3 "Train your model")]

<span data-ttu-id="ec830-202">`Train` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="ec830-202">The `Train` method executes the following tasks:</span></span>

* <span data-ttu-id="ec830-203">Ładuje lub pozyskuje dane.</span><span class="sxs-lookup"><span data-stu-id="ec830-203">Loads or ingests the data.</span></span>
* <span data-ttu-id="ec830-204">Wstępnie przetwarza i featurizes danych.</span><span class="sxs-lookup"><span data-stu-id="ec830-204">Preprocesses and featurizes the data.</span></span>
* <span data-ttu-id="ec830-205">Szkolenie modeli modelu.</span><span class="sxs-lookup"><span data-stu-id="ec830-205">Trains the model.</span></span>
* <span data-ttu-id="ec830-206">Prognozuje tonacji na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="ec830-206">Predicts sentiment based on test data.</span></span>

<span data-ttu-id="ec830-207">Tworzenie `Train` metody tuż za `Main` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ec830-207">Create the `Train` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static async Task<PredictionModel<SentimentData, SentimentPrediction>> Train()
{

}
```

## <a name="ingest-the-data"></a><span data-ttu-id="ec830-208">Pozyskiwanie danych</span><span class="sxs-lookup"><span data-stu-id="ec830-208">Ingest the data</span></span>

<span data-ttu-id="ec830-209">Inicjuje nowe wystąpienie klasy <xref:Microsoft.ML.LearningPipeline> zawierające ładowania danych, przetwarzanie danych/cechowania i modelu.</span><span class="sxs-lookup"><span data-stu-id="ec830-209">Initialize a new instance of <xref:Microsoft.ML.LearningPipeline> that will include the data loading, data processing/featurization, and model.</span></span> <span data-ttu-id="ec830-210">Dodaj następujący kod jako pierwsza linia `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="ec830-210">Add the following code as the first line of the `Train` method:</span></span>

[!code-csharp[LearningPipeline](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#5 "Create a learning pipeline")]

<span data-ttu-id="ec830-211"><xref:Microsoft.ML.Data.TextLoader> Obiektu jest pierwszą częścią potoku i ładuje plik danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="ec830-211">The <xref:Microsoft.ML.Data.TextLoader> object is the first part of the pipeline, and loads the training file data.</span></span>

[!code-csharp[TextLoader](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#6 "Add a text loader to the pipeline")]

## <a name="data-preprocess-and-feature-engineering"></a><span data-ttu-id="ec830-212">Wstępne przetwarzanie danych i inżynieria funkcji</span><span class="sxs-lookup"><span data-stu-id="ec830-212">Data preprocess and feature engineering</span></span>

<span data-ttu-id="ec830-213">Wstępne przetwarzanie i czyszczenie danych są ważne zadania, które występują przed zestaw danych jest efektywnie używać uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="ec830-213">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="ec830-214">Nieprzetworzone dane są często hałas i zawodnych i może brakować wartości.</span><span class="sxs-lookup"><span data-stu-id="ec830-214">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="ec830-215">Korzystanie z danych bez tych zadań modelowania może spowodować wyświetlenie nieprawdziwych wyników.</span><span class="sxs-lookup"><span data-stu-id="ec830-215">Using data without these modeling tasks can produce misleading results.</span></span> <span data-ttu-id="ec830-216">UCZENIE MASZYNOWE. Potoki przekształcenie firmy NET umożliwiają tworzą zbiór niestandardowych przekształceń, które są stosowane do danych przed szkolenie i testowanie.</span><span class="sxs-lookup"><span data-stu-id="ec830-216">ML.NET's transform pipelines allow you to compose a custom set of transforms that are applied to your data before training or testing.</span></span> <span data-ttu-id="ec830-217">Przekształcenia głównym celem jest dla cechowania danych.</span><span class="sxs-lookup"><span data-stu-id="ec830-217">The transforms' primary purpose is for data featurization.</span></span> <span data-ttu-id="ec830-218">Potok przekształcania zaletą jest to, że po definicji potoku transformacji, Zapisz potoku, aby zastosować dane testowe.</span><span class="sxs-lookup"><span data-stu-id="ec830-218">A transform pipeline's advantage is that after transform pipeline definition, save the pipeline to apply it to test data.</span></span>

<span data-ttu-id="ec830-219">Zastosuj <xref:Microsoft.ML.Transforms.TextFeaturizer> można przekonwertować `SentimentText` kolumny na [liczbowych wektor](../resources/glossary.md#numerical-feature-vector) o nazwie `Features` używane przez algorytm uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="ec830-219">Apply a <xref:Microsoft.ML.Transforms.TextFeaturizer> to convert the `SentimentText` column into a [numeric vector](../resources/glossary.md#numerical-feature-vector) called `Features` used by the machine learning algorithm.</span></span> <span data-ttu-id="ec830-220">Jest to krok przetwarzania wstępnego cechowania.</span><span class="sxs-lookup"><span data-stu-id="ec830-220">This is the preprocessing/featurization step.</span></span> <span data-ttu-id="ec830-221">Za pomocą dodatkowych składników dostępnych w strukturze ML.NET umożliwiają lepsze wyniki za pomocą modelu.</span><span class="sxs-lookup"><span data-stu-id="ec830-221">Using additional components available in ML.NET can enable better results with your model.</span></span> <span data-ttu-id="ec830-222">Dodaj `TextFeaturizer` do potoku jako następnego wiersza kodu:</span><span class="sxs-lookup"><span data-stu-id="ec830-222">Add `TextFeaturizer` to the pipeline as the next line of code:</span></span>

[!code-csharp[TextFeaturizer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#7 "Add a TextFeaturizer to the pipeline")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="ec830-223">Wybieranie algorytmu uczenia</span><span class="sxs-lookup"><span data-stu-id="ec830-223">Choose a learning algorithm</span></span>

<span data-ttu-id="ec830-224"><xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier> Obiekt jest uczeń drzewa decyzyjne, zostanie użyty w tym potoku.</span><span class="sxs-lookup"><span data-stu-id="ec830-224">The <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier> object is a decision tree learner you'll use in this pipeline.</span></span> <span data-ttu-id="ec830-225">Podobnie jak w kroku cechowania wypróbowania różnych uczestników kursów, które są dostępne w strukturze ML.NET i zmienianie ich parametrów prowadzi do różne wyniki.</span><span class="sxs-lookup"><span data-stu-id="ec830-225">Similar to the featurization step, trying out different learners available in ML.NET and changing their parameters leads to different results.</span></span> <span data-ttu-id="ec830-226">W przypadku dostosowywania, można ustawić [hiperparametrów](../resources/glossary.md#hyperparameter) takich jak <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumTrees>, <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumLeaves>, i <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.MinDocumentsInLeafs>.</span><span class="sxs-lookup"><span data-stu-id="ec830-226">For tuning, you can set [hyperparameters](../resources/glossary.md#hyperparameter) like <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumTrees>, <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumLeaves>, and <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.MinDocumentsInLeafs>.</span></span> <span data-ttu-id="ec830-227">Te hiperparametrów są ustawiane przed wszystko wpływa na modelu i są specyficzne dla modelu.</span><span class="sxs-lookup"><span data-stu-id="ec830-227">These hyperparameters are set before anything affects the model and are model-specific.</span></span> <span data-ttu-id="ec830-228">Służą one do dostrojenia drzewa decyzyjnego dla wydajności, więc większe wartości może negatywnie wpłynąć na wydajność.</span><span class="sxs-lookup"><span data-stu-id="ec830-228">They're used to tune the decision tree for performance, so larger values can negatively impact performance.</span></span>

<span data-ttu-id="ec830-229">Dodaj następujący kod do `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="ec830-229">Add the following code to the `Train` method:</span></span>

[!code-csharp[BinaryClassifier](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#8 "Add a fast binary tree classifier")]

## <a name="train-the-model"></a><span data-ttu-id="ec830-230">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="ec830-230">Train the model</span></span>

<span data-ttu-id="ec830-231">Uczenie modelu, <xref:Microsoft.ML.PredictionModel%602>zgodnie z zestawu danych, który został załadowany i przekształcone.</span><span class="sxs-lookup"><span data-stu-id="ec830-231">You train the model, <xref:Microsoft.ML.PredictionModel%602>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="ec830-232">`pipeline.Train<SentimentData, SentimentPrediction>()` szkolenie modeli potoku (służy do ładowania danych, pociągów featurized i uczeń).</span><span class="sxs-lookup"><span data-stu-id="ec830-232">`pipeline.Train<SentimentData, SentimentPrediction>()` trains the pipeline (loads the data, trains the featurizer and learner).</span></span> <span data-ttu-id="ec830-233">Eksperyment nie jest wykonywane, dopóki nie dzieje.</span><span class="sxs-lookup"><span data-stu-id="ec830-233">The experiment is not executed until this happens.</span></span>

<span data-ttu-id="ec830-234">Dodaj następujący kod do `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="ec830-234">Add the following code to the `Train` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#9 "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="ec830-235">Zapisz i wróć model jest uczony na potrzeby oceny</span><span class="sxs-lookup"><span data-stu-id="ec830-235">Save and Return the model trained to use for evaluation</span></span>

<span data-ttu-id="ec830-236">W tym momencie masz modelu, który można zintegrować wszystkich istniejących i nowych aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="ec830-236">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="ec830-237">Aby zapisać swój model do pliku zip, przed zwróceniem, Dodaj następujący kod do następnego wiersza w `Train`:</span><span class="sxs-lookup"><span data-stu-id="ec830-237">To save your model to a .zip file before returning, add the following code to the next line in `Train`:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#10 "Save the model")]

<span data-ttu-id="ec830-238">Zwraca model na końcu `Train` metody.</span><span class="sxs-lookup"><span data-stu-id="ec830-238">Return the model at the end of the `Train` method.</span></span>

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#11 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="ec830-239">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="ec830-239">Evaluate the model</span></span>

<span data-ttu-id="ec830-240">Teraz, po utworzeniu i uczony model, należy ocenić ją z innego zestawu danych do zapewniania jakości i sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="ec830-240">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="ec830-241">W `Evaluate` metody, model utworzony w `Train` jest przekazywany do obliczenia.</span><span class="sxs-lookup"><span data-stu-id="ec830-241">In the `Evaluate` method, the model created in `Train` is passed in to be evaluated.</span></span> <span data-ttu-id="ec830-242">Tworzenie `Evaluate` metody tuż za `Train`, jak w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="ec830-242">Create the `Evaluate` method, just after `Train`, as in the following code:</span></span>

```csharp
public static void Evaluate(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

<span data-ttu-id="ec830-243">`Evaluate` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="ec830-243">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="ec830-244">Ładuje zestawy danych testowych.</span><span class="sxs-lookup"><span data-stu-id="ec830-244">Loads the test dataset.</span></span>
* <span data-ttu-id="ec830-245">Tworzy ewaluatora binarnego.</span><span class="sxs-lookup"><span data-stu-id="ec830-245">Creates the binary evaluator.</span></span>
* <span data-ttu-id="ec830-246">Oblicza model oraz tworzenie metryk.</span><span class="sxs-lookup"><span data-stu-id="ec830-246">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="ec830-247">Przedstawia metryki.</span><span class="sxs-lookup"><span data-stu-id="ec830-247">Displays the metrics.</span></span>

<span data-ttu-id="ec830-248">Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `Train` wywołania metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ec830-248">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#12 "Call the Evaluate method")]

<span data-ttu-id="ec830-249"><xref:Microsoft.ML.Data.TextLoader> Klasy ładuje nowego zestawu danych testowych za pomocą tego samego schematu.</span><span class="sxs-lookup"><span data-stu-id="ec830-249">The <xref:Microsoft.ML.Data.TextLoader> class loads the new test dataset with the same schema.</span></span> <span data-ttu-id="ec830-250">Możesz ocenić modelu przy użyciu tego zestawu danych w celu sprawdzenia jakości.</span><span class="sxs-lookup"><span data-stu-id="ec830-250">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="ec830-251">Dodaj następujący kod do `Evaluate` metody:</span><span class="sxs-lookup"><span data-stu-id="ec830-251">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadText](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#13 "Load the test dataset")]

<span data-ttu-id="ec830-252"><xref:Microsoft.ML.Models.BinaryClassificationEvaluator> Obiektu oblicza metryk jakości `PredictionModel` przy użyciu określonego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="ec830-252">The <xref:Microsoft.ML.Models.BinaryClassificationEvaluator> object computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="ec830-253">Aby wyświetlić te metryki, należy dodać ewaluatora w następnym wierszu `Evaluate` metoda następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="ec830-253">To see those metrics, add the evaluator as the next line in the `Evaluate` method, with the following code:</span></span>

[!code-csharp[BinaryEvaluator](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#14 "Create the binary evaluator")]

<span data-ttu-id="ec830-254"><xref:Microsoft.ML.Models.BinaryClassificationMetrics> Zawiera ogólne metryki obliczone przez ewaluatory klasyfikacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="ec830-254">The <xref:Microsoft.ML.Models.BinaryClassificationMetrics> contains the overall metrics computed by binary classification evaluators.</span></span> <span data-ttu-id="ec830-255">Aby je wyświetlić, aby określić jakość modelu, należy pobrać pierwszy metryki.</span><span class="sxs-lookup"><span data-stu-id="ec830-255">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="ec830-256">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="ec830-256">Add the following code:</span></span>

[!code-csharp[CreateMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#15 "Evaluate the model and create metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="ec830-257">Wyświetlanie metryki dotyczące weryfikacji modelu</span><span class="sxs-lookup"><span data-stu-id="ec830-257">Displaying the metrics for model validation</span></span>

<span data-ttu-id="ec830-258">Użyj poniższego kodu, aby wyświetlić metryki, udostępnianie wyników, a następnie działanie na nich:</span><span class="sxs-lookup"><span data-stu-id="ec830-258">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#16 "Display selected metrics")]

## <a name="predict-the-test-data-outcomes-with-the-model"></a><span data-ttu-id="ec830-259">Przewidywanie wyników danych testów przy użyciu modelu</span><span class="sxs-lookup"><span data-stu-id="ec830-259">Predict the test data outcomes with the model</span></span>

<span data-ttu-id="ec830-260">Tworzenie `Predict` metody tuż za `Evaluate` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ec830-260">Create the `Predict` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
public static void Predict(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

<span data-ttu-id="ec830-261">`Predict` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="ec830-261">The `Predict` method executes the following tasks:</span></span>

* <span data-ttu-id="ec830-262">Tworzy dane testowe.</span><span class="sxs-lookup"><span data-stu-id="ec830-262">Creates test data.</span></span>
* <span data-ttu-id="ec830-263">Prognozuje tonacji na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="ec830-263">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="ec830-264">Łączy w sobie testowanie, danych i prognoz dla raportowania.</span><span class="sxs-lookup"><span data-stu-id="ec830-264">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="ec830-265">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="ec830-265">Displays the predicted results.</span></span>

<span data-ttu-id="ec830-266">Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `Evaluate` wywołania metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ec830-266">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#17 "Call the Predict method")]

<span data-ttu-id="ec830-267">Dodaj niektóre komentarze, aby przetestować prognozy uczonego modelu w `Predict` metody:</span><span class="sxs-lookup"><span data-stu-id="ec830-267">Add some comments to test the trained model's predictions in the `Predict` method:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#18 "Create test data for predictions")]

<span data-ttu-id="ec830-268">Teraz, gdy model, możesz go używać, aby przewidzieć dodatnie lub ujemne tonacji przy użyciu danych komentarz <xref:Microsoft.ML.PredictionModel.Predict%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="ec830-268">Now that you have a model, you can use that to predict the positive or negative sentiment of the comment data using the <xref:Microsoft.ML.PredictionModel.Predict%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ec830-269">Aby uzyskać prognozę, użyj `Predict` na nowych danych.</span><span class="sxs-lookup"><span data-stu-id="ec830-269">To get a prediction, use `Predict` on new data.</span></span> <span data-ttu-id="ec830-270">Należy pamiętać, że dane wejściowe to ciąg, a model zawiera cechowania.</span><span class="sxs-lookup"><span data-stu-id="ec830-270">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="ec830-271">Potok jest zsynchronizowany podczas uczenia i przewidywania.</span><span class="sxs-lookup"><span data-stu-id="ec830-271">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="ec830-272">Nie trzeba napisać kod przetwarzania wstępnego cechowania specjalnie dla prognoz i zajmuje się tego samego interfejsu API i usługi batch jednorazowe prognozy.</span><span class="sxs-lookup"><span data-stu-id="ec830-272">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#19 "Create predictions of sentiments")]

### <a name="model-operationalization-prediction"></a><span data-ttu-id="ec830-273">Model operacjonalizacji: prognoz</span><span class="sxs-lookup"><span data-stu-id="ec830-273">Model operationalization: prediction</span></span>

<span data-ttu-id="ec830-274">Wyświetlanie `SentimentText` i odpowiednie przewidywania opinii w celu udostępniania wyników i odpowiednie do nich działanie na nich.</span><span class="sxs-lookup"><span data-stu-id="ec830-274">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="ec830-275">Jest to nazywane operacjonalizacji, jako część zasad operacyjnych przy użyciu zwracanych danych.</span><span class="sxs-lookup"><span data-stu-id="ec830-275">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="ec830-276">Utwórz nagłówek dla wyników za pomocą następujących <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:</span><span class="sxs-lookup"><span data-stu-id="ec830-276">Create a header for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#20 "Display prediction outputs")]

<span data-ttu-id="ec830-277">Przed wyświetleniem wyników, Połącz opinii i prognozowania ze sobą, aby zobaczyć, oryginalnym komentarzem z jego przewidywane wskaźniki nastrojów klientów.</span><span class="sxs-lookup"><span data-stu-id="ec830-277">Before displaying the predicted results, combine the sentiment and prediction together to see the original comment with its predicted sentiment.</span></span> <span data-ttu-id="ec830-278">Poniższy kod używa <xref:System.Linq.Enumerable.Zip%2A> metodę, aby to zrobić, obok więc Dodaj ten kod:</span><span class="sxs-lookup"><span data-stu-id="ec830-278">The following code uses the <xref:System.Linq.Enumerable.Zip%2A> method to make that happen, so add that code next:</span></span>

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#21 "Build the pairs of sentiment data and predictions")]

<span data-ttu-id="ec830-279">Teraz, gdy zostały połączone `SentimentText` i `Sentiment` do klasy, można wyświetlić wyniki za pomocą <xref:System.Console.WriteLine?displayProperty=nameWithType> metody:</span><span class="sxs-lookup"><span data-stu-id="ec830-279">Now that you've combined the `SentimentText` and `Sentiment` into a class, you can display the results using the <xref:System.Console.WriteLine?displayProperty=nameWithType> method:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#22 "Display the predictions")]

<span data-ttu-id="ec830-280">Ponieważ wywnioskować, że jest nową funkcją w C# 7.1 i wersją języka domyślnego projektu języka C# 7.0 nazwami elementów krotki, musisz zmienić wersję języka C# 7.1 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="ec830-280">Because inferred tuple element names are a new feature in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span>
<span data-ttu-id="ec830-281">Aby to zrobić, kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="ec830-281">To do that, right-click on the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="ec830-282">Wybierz **kompilacji** kartę, a następnie wybierz pozycję **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="ec830-282">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="ec830-283">Z listy rozwijanej wybierz **języka C# 7.1** (lub nowsza wersja).</span><span class="sxs-lookup"><span data-stu-id="ec830-283">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="ec830-284">Wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="ec830-284">Select the **OK** button.</span></span>

## <a name="results"></a><span data-ttu-id="ec830-285">wyniki</span><span class="sxs-lookup"><span data-stu-id="ec830-285">Results</span></span>

<span data-ttu-id="ec830-286">Wyniki powinny być podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="ec830-286">Your results should be similar to the following.</span></span> <span data-ttu-id="ec830-287">Ponieważ przetwarza potoku, wyświetla komunikaty.</span><span class="sxs-lookup"><span data-stu-id="ec830-287">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="ec830-288">Może zostać wyświetlony ostrzeżenia lub komunikaty przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="ec830-288">You may see warnings, or processing messages.</span></span> <span data-ttu-id="ec830-289">Te zostały usunięte z następujących wyników dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="ec830-289">These have been removed from the following results for clarity.</span></span>

```

PredictionModel quality metrics evaluation
------------------------------------------
Accuracy: 66.67%
Auc: 94.44%
F1Score: 75.00%

Sentiment Predictions
---------------------
Sentiment: Please refrain from adding nonsense to Wikipedia. | Prediction: Negative
Sentiment: He is the best, and the article should say that. | Prediction: Positive

```

<span data-ttu-id="ec830-290">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="ec830-290">Congratulations!</span></span> <span data-ttu-id="ec830-291">Model uczenia maszynowego dla klasyfikacji i prognozowanie tonacji wiadomości teraz zostały pomyślnie skompilowane.</span><span class="sxs-lookup"><span data-stu-id="ec830-291">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span> <span data-ttu-id="ec830-292">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="ec830-292">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ec830-293">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="ec830-293">Next steps</span></span>

<span data-ttu-id="ec830-294">W tym samouczku przedstawiono sposób:</span><span class="sxs-lookup"><span data-stu-id="ec830-294">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="ec830-295">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="ec830-295">Understand the problem</span></span>
> * <span data-ttu-id="ec830-296">Wybierz zadanie uczenia odpowiedniej maszyny</span><span class="sxs-lookup"><span data-stu-id="ec830-296">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="ec830-297">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="ec830-297">Prepare your data</span></span>
> * <span data-ttu-id="ec830-298">Tworzenie potoku uczenia</span><span class="sxs-lookup"><span data-stu-id="ec830-298">Create the learning pipeline</span></span>
> * <span data-ttu-id="ec830-299">Ładowanie klasyfikatora</span><span class="sxs-lookup"><span data-stu-id="ec830-299">Load a classifier</span></span>
> * <span data-ttu-id="ec830-300">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="ec830-300">Train the model</span></span>
> * <span data-ttu-id="ec830-301">Ocena modelu za pomocą innego zestawu danych</span><span class="sxs-lookup"><span data-stu-id="ec830-301">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="ec830-302">Przewidywanie wyników danych testów przy użyciu modelu</span><span class="sxs-lookup"><span data-stu-id="ec830-302">Predict the test data outcomes with the model</span></span>

<span data-ttu-id="ec830-303">Przejdź do następnego samouczka, aby dowiedzieć się więcej</span><span class="sxs-lookup"><span data-stu-id="ec830-303">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="ec830-304">Taksówek taryfy predykcyjne</span><span class="sxs-lookup"><span data-stu-id="ec830-304">Taxi Fare Predictor</span></span>](taxi-fare.md)
