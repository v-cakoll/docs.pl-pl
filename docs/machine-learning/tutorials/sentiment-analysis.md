---
title: Użyj strukturze ML.NET w scenariuszu klasyfikacji binarnej analizy tonacji
description: Dowiedz się, jak używać strukturze ML.NET w scenariuszu klasyfikacji binarnej zrozumienie, jak na potrzeby prognozowania tonacji podjąć odpowiednie działania.
ms.date: 02/15/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: d6d5cae107e25000add5c8430a35131a79696bc2
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092764"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a><span data-ttu-id="ffa9e-103">Samouczek: Użyj strukturze ML.NET w scenariuszu klasyfikacji binarnej analizy tonacji</span><span class="sxs-lookup"><span data-stu-id="ffa9e-103">Tutorial: Use ML.NET in a sentiment analysis binary classification scenario</span></span>

> [!NOTE]
> <span data-ttu-id="ffa9e-104">W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="ffa9e-105">Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="ffa9e-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="ffa9e-106">Ten przykładowy samouczek przedstawia tworzenie klasyfikatora tonacji za pomocą aplikacji konsoli .NET Core przy użyciu języka C# w programie Visual Studio 2017 przy użyciu strukturze ML.NET.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-106">This sample tutorial illustrates using ML.NET to create a sentiment classifier via a .NET Core console application using C# in Visual Studio 2017.</span></span>

<span data-ttu-id="ffa9e-107">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="ffa9e-108">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="ffa9e-108">Understand the problem</span></span>
> * <span data-ttu-id="ffa9e-109">Wybieranie algorytmu uczenia maszynowego odpowiednie</span><span class="sxs-lookup"><span data-stu-id="ffa9e-109">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="ffa9e-110">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="ffa9e-110">Prepare your data</span></span>
> * <span data-ttu-id="ffa9e-111">Przekształcanie danych</span><span class="sxs-lookup"><span data-stu-id="ffa9e-111">Transform the data</span></span>
> * <span data-ttu-id="ffa9e-112">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="ffa9e-112">Train the model</span></span>
> * <span data-ttu-id="ffa9e-113">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="ffa9e-113">Evaluate the model</span></span>
> * <span data-ttu-id="ffa9e-114">Prognozowanie za pomocą uczonego modelu</span><span class="sxs-lookup"><span data-stu-id="ffa9e-114">Predict with the trained model</span></span>
> * <span data-ttu-id="ffa9e-115">Wdrażanie i przewidywanie załadować modelu</span><span class="sxs-lookup"><span data-stu-id="ffa9e-115">Deploy and Predict with a loaded model</span></span>

## <a name="sentiment-analysis-sample-overview"></a><span data-ttu-id="ffa9e-116">Omówienie przykładowych analizy tonacji</span><span class="sxs-lookup"><span data-stu-id="ffa9e-116">Sentiment analysis sample overview</span></span>

<span data-ttu-id="ffa9e-117">Próbka jest aplikacją konsoli, która używa strukturze ML.NET do nauczenia modelu, która klasyfikuje i przewiduje wskaźniki nastrojów klientów, jak dodatnie lub ujemne.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-117">The sample is a console app that uses ML.NET to train a model that classifies and predicts sentiment as either positive or negative.</span></span> <span data-ttu-id="ffa9e-118">Oblicza model z drugiego zestawu danych do analizy jakości dostawców.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-118">It also evaluates the model with a second dataset for quality analysis.</span></span> <span data-ttu-id="ffa9e-119">Zestawy danych wskaźniki nastrojów klientów są od projektu WikiDetox.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-119">The sentiment datasets are from the WikiDetox project.</span></span>

<span data-ttu-id="ffa9e-120">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-120">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ffa9e-121">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="ffa9e-121">Prerequisites</span></span>

* <span data-ttu-id="ffa9e-122">[Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".</span><span class="sxs-lookup"><span data-stu-id="ffa9e-122">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="ffa9e-123">[Wikipedia detox wiersza danych tabulacji pliku (wikiPedia-detox-250-linia data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).</span><span class="sxs-lookup"><span data-stu-id="ffa9e-123">The [Wikipedia detox line data tab separated file (wikiPedia-detox-250-line-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span>
* <span data-ttu-id="ffa9e-124">[Wikipedia detox wiersza testu tabulacji pliku (wikipedia-detox-250-linia test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).</span><span class="sxs-lookup"><span data-stu-id="ffa9e-124">The [Wikipedia detox line test tab separated file (wikipedia-detox-250-line-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="ffa9e-125">Maszyny uczenie się przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ffa9e-125">Machine learning workflow</span></span>

<span data-ttu-id="ffa9e-126">W tym samouczku poniżej przepływu pracy, który umożliwia proces przenoszenia w sposób uporządkowany uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-126">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="ffa9e-127">Fazy przepływu pracy są następujące:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-127">The workflow phases are as follows:</span></span>

1. <span data-ttu-id="ffa9e-128">**Omówienie problemu**</span><span class="sxs-lookup"><span data-stu-id="ffa9e-128">**Understand the problem**</span></span>
2. <span data-ttu-id="ffa9e-129">**Przygotowywanie danych**</span><span class="sxs-lookup"><span data-stu-id="ffa9e-129">**Prepare your data**</span></span>
   * <span data-ttu-id="ffa9e-130">**Ładowanie danych**</span><span class="sxs-lookup"><span data-stu-id="ffa9e-130">**Load the data**</span></span>
   * <span data-ttu-id="ffa9e-131">**Wyodrębnianie funkcji (przekształcania danych)**</span><span class="sxs-lookup"><span data-stu-id="ffa9e-131">**Extract features (Transform your data)**</span></span>
3. <span data-ttu-id="ffa9e-132">**Kompilowanie i szkolenie**</span><span class="sxs-lookup"><span data-stu-id="ffa9e-132">**Build and train**</span></span> 
   * <span data-ttu-id="ffa9e-133">**Uczenie modelu**</span><span class="sxs-lookup"><span data-stu-id="ffa9e-133">**Train the model**</span></span>
   * <span data-ttu-id="ffa9e-134">**Ocena modelu**</span><span class="sxs-lookup"><span data-stu-id="ffa9e-134">**Evaluate the model**</span></span>
4. <span data-ttu-id="ffa9e-135">**Wdrażanie modelu**</span><span class="sxs-lookup"><span data-stu-id="ffa9e-135">**Deploy Model**</span></span>
   * <span data-ttu-id="ffa9e-136">**Użyj modelu do prognozowania**</span><span class="sxs-lookup"><span data-stu-id="ffa9e-136">**Use the Model to predict**</span></span>

### <a name="understand-the-problem"></a><span data-ttu-id="ffa9e-137">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="ffa9e-137">Understand the problem</span></span>

<span data-ttu-id="ffa9e-138">Należy najpierw zrozumieć, dzięki czemu można podzielić je w dół do części obsługujące kompilowanie i uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-138">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="ffa9e-139">Potężne problem umożliwia prognozowanie i ocena wyników.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-139">Breaking the problem down allows you to predict and evaluate the results.</span></span>

<span data-ttu-id="ffa9e-140">Ten problem, w tym samouczku jest zrozumienie, przychodzące tonacji komentarz witryny sieci Web podejmowanie odpowiednich działań.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-140">The problem for this tutorial is to understand incoming website comment sentiment to take the appropriate action.</span></span>

<span data-ttu-id="ffa9e-141">Ten problem można podzielić do tonacji tekstu i wartości tonacji danych mają do nauczenia modelu, z, a wartości tonacji przewidywane, można obliczyć, a następnie za pomocą pod względem.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-141">You can break down the problem to the sentiment text and sentiment value for the data you want to train the model with, and a predicted sentiment value that you can evaluate and then use operationally.</span></span>

<span data-ttu-id="ffa9e-142">Następnie należy **określić** tonacji, która ułatwia wybieranie zadań uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-142">You then need to **determine** the sentiment, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-algorithm"></a><span data-ttu-id="ffa9e-143">Wybieranie algorytmu uczenia maszynowego odpowiednie</span><span class="sxs-lookup"><span data-stu-id="ffa9e-143">Select the appropriate machine learning algorithm</span></span>

<span data-ttu-id="ffa9e-144">W rozwiązaniu tego problemu znasz następujące fakty:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-144">With this problem, you know the following facts:</span></span>

<span data-ttu-id="ffa9e-145">Szkolenie danych: komentarze witryny sieci Web może być toksyczne (1) czy nie toksyczne (0) (**tonacji**).</span><span class="sxs-lookup"><span data-stu-id="ffa9e-145">Training data: website comments can be toxic (1) or not toxic (0) (**sentiment**).</span></span>
<span data-ttu-id="ffa9e-146">Przewidywanie **tonacji** nowego komentarza witryny sieci Web, toksyczne lub nie toksyczne, takie jak w następujących przykładach:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-146">Predict the **sentiment** of a new website comment, either toxic or not toxic, such as in the following examples:</span></span>

* <span data-ttu-id="ffa9e-147">Punktowanych — Dodawanie żadnego znaczenia do Wikipedia.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-147">Please refrain from adding nonsense to Wikipedia.</span></span>
* <span data-ttu-id="ffa9e-148">Jest on najlepsze, a artykuł powinien oznacza, że.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-148">He is the best, and the article should say that.</span></span>

<span data-ttu-id="ffa9e-149">Algorytmu uczenia maszynowego klasyfikacji najlepiej nadaje się dla tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-149">The classification machine learning algorithm is best suited for this scenario.</span></span>

### <a name="about-the-classification-task"></a><span data-ttu-id="ffa9e-150">O zadaniu klasyfikacji</span><span class="sxs-lookup"><span data-stu-id="ffa9e-150">About the classification task</span></span>

<span data-ttu-id="ffa9e-151">Klasyfikacja jest algorytm uczenia maszynowego, która korzysta z danych do **określić** kategorii, typ lub klasa elementu lub wiersza danych.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-151">Classification is a machine learning algorithm that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="ffa9e-152">Na przykład można użyć klasyfikacji:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-152">For example, you can use classification to:</span></span>

* <span data-ttu-id="ffa9e-153">Zidentyfikuj tonacji jako dodatnia lub ujemna.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-153">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="ffa9e-154">Klasyfikowanie wiadomości e-mail jako spam, wiadomości-śmieci lub właściwej.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-154">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="ffa9e-155">Ustal, czy pacjent laboratorium przykładowe dane stanowią cancerous.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-155">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="ffa9e-156">Klienci na kategorie według ich tendencje do odpowiedzi na kampanię sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-156">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="ffa9e-157">Algorytmy klasyfikacji są często jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-157">Classification algorithms are frequently one of the following types:</span></span>

* <span data-ttu-id="ffa9e-158">Plik binarny: A i B.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-158">Binary: either A or B.</span></span>
* <span data-ttu-id="ffa9e-159">Kontra: wielu kategorii, które można przewidzieć przy użyciu pojedynczego modelu.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-159">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="ffa9e-160">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="ffa9e-160">Create a console application</span></span>

1. <span data-ttu-id="ffa9e-161">Otwórz program Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-161">Open Visual Studio 2017.</span></span> <span data-ttu-id="ffa9e-162">Wybierz **pliku** > **New** > **projektu** z paska menu.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-162">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="ffa9e-163">W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła następuje **platformy .NET Core** węzła.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-163">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="ffa9e-164">Następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-164">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="ffa9e-165">W **nazwa** pole tekstowe, wpisz "SentimentAnalysis", a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-165">In the **Name** text box, type "SentimentAnalysis" and then select the **OK** button.</span></span>

2. <span data-ttu-id="ffa9e-166">Utwórz katalog o nazwie *danych* w projekcie, aby zapisać pliki zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-166">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="ffa9e-167">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nad projektem i wybierz **Dodaj** > **nowy Folder**.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-167">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="ffa9e-168">Wpisz "Dane", a następnie naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-168">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="ffa9e-169">Zainstaluj **pakietu NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-169">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="ffa9e-170">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-170">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="ffa9e-171">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-171">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="ffa9e-172">Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-172">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="ffa9e-173">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="ffa9e-173">Prepare your data</span></span>

1. <span data-ttu-id="ffa9e-174">Pobierz [Wikipedia detox-250-linia data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) i [wikipedia-detox-250-linia test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) danych ustawia i zapisywanie ich *danych* wcześniej utworzony folder.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-174">Download the [Wikipedia detox-250-line-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) and the [wikipedia-detox-250-line-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="ffa9e-175">Szkolenie modeli modelu uczenia maszynowego na pierwszego zestawu danych, a drugi może służyć do oceny, jak dokładna jest model.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-175">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="ffa9e-176">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy każdy z \*pliki tsv i wybierz pozycję **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-176">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="ffa9e-177">W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-177">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="ffa9e-178">Tworzenie klas i definiowania ścieżek</span><span class="sxs-lookup"><span data-stu-id="ffa9e-178">Create classes and define paths</span></span>

<span data-ttu-id="ffa9e-179">Dodaj następujące dodatkowe `using` instrukcji na górze *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-179">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="ffa9e-180">Musisz utworzyć trzy pola globalnego na potrzeby przechowywania ścieżek do ostatnio pobrane pliki, a dla zmiennej globalnej `TextLoader`:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-180">You need to create three global fields to hold the paths to the recently downloaded files, and a global variable for the `TextLoader`:</span></span>

* <span data-ttu-id="ffa9e-181">`_trainDataPath` zawiera ścieżkę do zestawu danych, używane do trenowania modelu.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-181">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="ffa9e-182">`_testDataPath` zawiera ścieżkę do zestawu danych, używane do oceny modelu.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-182">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="ffa9e-183">`_modelPath` ma ścieżkę, w którym jest zapisany trenowanego modelu.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-183">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="ffa9e-184">`_textLoader` jest <xref:Microsoft.ML.Data.TextLoader> używany do ładowania i przekształcić zestawy danych.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-184">`_textLoader` is the <xref:Microsoft.ML.Data.TextLoader> used to load and transform the datasets.</span></span>

<span data-ttu-id="ffa9e-185">Dodaj następujący kod po prawej stronie wiersza powyżej `Main` metodę, aby określić tych ścieżek i `_textLoader` zmiennej:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-185">Add the following code to the line right above the `Main` method to specify those paths and the `_textLoader` variable:</span></span>

[!code-csharp[Declare global variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#2 "Declare global variables")]

<span data-ttu-id="ffa9e-186">Musisz utworzyć niektóre klasy dla danych wejściowych i prognozy.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-186">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="ffa9e-187">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-187">Add a new class to your project:</span></span>

1. <span data-ttu-id="ffa9e-188">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-188">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="ffa9e-189">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-189">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="ffa9e-190">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-190">Then, select the **Add** button.</span></span>

    <span data-ttu-id="ffa9e-191">*SentimentData.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-191">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="ffa9e-192">Dodaj następujący kod `using` instrukcji na górze *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-192">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#1 "Add necessary usings")]

<span data-ttu-id="ffa9e-193">Usuń istniejącą definicję klasy i Dodaj następujący kod, który zawiera dwie klasy `SentimentData` i `SentimentPrediction`, *SentimentData.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-193">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#2 "Declare data record types")]

<span data-ttu-id="ffa9e-194">`SentimentData` Klasa wejściowy zestaw danych i ma `float` (`Sentiment`) zawierający wartości tonacji dodatnie lub ujemne, a ciąg komentarza (`SentimentText`).</span><span class="sxs-lookup"><span data-stu-id="ffa9e-194">`SentimentData` is the input dataset class and has a `float` (`Sentiment`) that has a value for sentiment of either positive or negative, and a string for the comment (`SentimentText`).</span></span> <span data-ttu-id="ffa9e-195">Oba pola mają `Column` atrybuty dołączonych do nich.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-195">Both fields have `Column` attributes attached to them.</span></span> <span data-ttu-id="ffa9e-196">Ten atrybut wykonywania działań Opisuje kolejność każdego pola w pliku danych, i które `Label` pola.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-196">This attribute describes the order of each field in the data file, and which is the `Label` field.</span></span> <span data-ttu-id="ffa9e-197">`SentimentPrediction` Klasa służy do prognozowania po wyszkoliła modelu.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-197">`SentimentPrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="ffa9e-198">Ma ona pojedynczy atrybut typu wartość logiczna (`Sentiment`) i `PredictedLabel` `ColumnName` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-198">It has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="ffa9e-199">`Label` Umożliwia tworzenie i uczenie modelu, a także drugiego zestawu danych do ewaluacji modelu.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-199">The `Label` is used to create and train the model, and it's also used with a second dataset to evaluate the model.</span></span> <span data-ttu-id="ffa9e-200">`PredictedLabel` Używany podczas prognoz i oceny.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-200">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="ffa9e-201">W wersji ewaluacyjnej używane są dane szkoleniowe, przewidywane wartości i model danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-201">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="ffa9e-202">Podczas tworzenia modelu za pomocą platformy ML.NET rozpoczyna się od utworzenia `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-202">When building a model with ML.NET you start by creating an `MLContext`.</span></span> <span data-ttu-id="ffa9e-203">To jest porównywalna koncepcyjnie za pomocą `DbContext` platformy Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-203">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span> <span data-ttu-id="ffa9e-204">Środowisko dostarcza kontekst dla zadania uczenia Maszynowego, który może służyć do wyjątku, śledzenie i rejestrowanie.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-204">The environment provides a context for your ML job that can be used for exception tracking and logging.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="ffa9e-205">Inicjowanie zmiennych w głównym oknie</span><span class="sxs-lookup"><span data-stu-id="ffa9e-205">Initialize variables in Main</span></span>

<span data-ttu-id="ffa9e-206">Utwórz zmienną o nazwie `mlContext` i zainicjuj ją o nowe wystąpienie klasy `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-206">Create a variable called `mlContext` and initialize it with a new instance of `MLContext`.</span></span>  <span data-ttu-id="ffa9e-207">Zastąp `Console.WriteLine("Hello World!")` wiersz poniższym kodem w `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-207">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="ffa9e-208">Następnie do Instalatora w celu załadowania zainicjować danych `_textLoader` zmienna globalna, aby można było użyć go ponownie.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-208">Next, to setup for data loading initialize the `_textLoader` global variable in order to reuse it.</span></span>  <span data-ttu-id="ffa9e-209">Po utworzeniu `TextLoader` przy użyciu `MLContext.Data.CreateTextLoader`, są przekazywane w kontekście potrzebne i <xref:Microsoft.ML.Data.TextLoader.Arguments> klasy, która umożliwia dostosowanie.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-209">When you create a `TextLoader` using  `MLContext.Data.CreateTextLoader`, you pass in the context needed and the <xref:Microsoft.ML.Data.TextLoader.Arguments> class which enables customization.</span></span>

 <span data-ttu-id="ffa9e-210">Określ schemat danych, przekazując tablicę <xref:Microsoft.ML.Data.TextLoader.Column> obiektów modułu ładującego zawierająca wszystkie nazwy kolumn i ich typy.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-210">Specify the data schema by passing an array of <xref:Microsoft.ML.Data.TextLoader.Column> objects to the loader containing all the column names and their types.</span></span> <span data-ttu-id="ffa9e-211">Wcześniej zdefiniowany schemat danych podczas tworzenia naszej `SentimentData` klasy.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-211">You defined the data schema previously when you created our `SentimentData` class.</span></span> <span data-ttu-id="ffa9e-212">Dla naszych schematu jest pierwszą kolumnę (etykieta) <xref:System.Boolean> (Prognozowane) i druga kolumna (SentimentText) to funkcja typu/ciąg tekstowy używany do prognozowania tonacji.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-212">For our schema, the first column (Label) is a <xref:System.Boolean> (the prediction) and the second column (SentimentText) is the feature of type text/string used for predicting the sentiment.</span></span>
<span data-ttu-id="ffa9e-213">`TextLoader` Klasa zwraca w pełni zainicjowane <xref:Microsoft.ML.Data.TextLoader></span><span class="sxs-lookup"><span data-stu-id="ffa9e-213">The `TextLoader` class returns a fully initialized <xref:Microsoft.ML.Data.TextLoader></span></span>  

<span data-ttu-id="ffa9e-214">Aby zainicjować `_textLoader` zmienna globalna, aby można było użyć go ponownie w przypadku wymaganych zestawów danych, Dodaj następujący kod po `mlContext` inicjowania:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-214">To initialize the `_textLoader` global variable in order to reuse it for the needed datasets, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[initTextLoader](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#4 "Initialize the TextLoader")]

<span data-ttu-id="ffa9e-215">Dodaj następujący kod jako następnego wiersza kodu w `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-215">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[Train](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#5 "Train your model")]

<span data-ttu-id="ffa9e-216">`Train` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-216">The `Train` method executes the following tasks:</span></span>

* <span data-ttu-id="ffa9e-217">Służy do ładowania danych.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-217">Loads the data.</span></span>
* <span data-ttu-id="ffa9e-218">Wyodrębnia i przekształca dane.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-218">Extracts and transforms the data.</span></span>
* <span data-ttu-id="ffa9e-219">Szkolenie modeli modelu.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-219">Trains the model.</span></span>
* <span data-ttu-id="ffa9e-220">Prognozuje tonacji na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-220">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="ffa9e-221">Zwraca wartość modelu.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-221">Returns the model.</span></span>

<span data-ttu-id="ffa9e-222">Tworzenie `Train` metody tuż za `Main` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-222">Create the `Train` method, just after the `Main` method, using the following code:</span></span>

```csharp
 public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

<span data-ttu-id="ffa9e-223">Należy zauważyć, że dwa parametry są przekazywane do metody Train; `MLContext` kontekstu (`mlContext`), a <xref:System.String> dla ścieżki zestawu danych (`dataPath`).</span><span class="sxs-lookup"><span data-stu-id="ffa9e-223">Notice that two parameters are passed into the Train method; a `MLContext` for the context (`mlContext`), and a <xref:System.String> for the dataset path (`dataPath`).</span></span> <span data-ttu-id="ffa9e-224">Użytkownik chce użyć tej metody w więcej niż jeden raz celów szkoleniowych i testów.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-224">You're going to use this method more than once for training and testing.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="ffa9e-225">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="ffa9e-225">Load the data</span></span>

<span data-ttu-id="ffa9e-226">Będzie załadować dane przy użyciu `_textLoader` zmienna globalna z `dataPath` parametru.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-226">You'll load the data using the `_textLoader` global variable with the `dataPath` parameter.</span></span> <span data-ttu-id="ffa9e-227">Zwraca <xref:Microsoft.Data.DataView.IDataView>.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-227">It returns a <xref:Microsoft.Data.DataView.IDataView>.</span></span> <span data-ttu-id="ffa9e-228">Jako dane wejściowe i wyjściowe `Transforms`, `DataView` jest typem potoku danych podstawowych porównywalne do `IEnumerable` dla `LINQ`.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-228">As the input and output of `Transforms`, a `DataView` is the fundamental data pipeline type, comparable to `IEnumerable` for `LINQ`.</span></span>

<span data-ttu-id="ffa9e-229">W strukturze ML.NET dane są podobne do widoku SQL.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-229">In ML.NET, data is similar to a SQL view.</span></span> <span data-ttu-id="ffa9e-230">Jest opóźnieniem ocenianą informatycznych i heterogenicznych.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-230">It is lazily evaluated, schematized, and heterogenous.</span></span> <span data-ttu-id="ffa9e-231">Obiekt jest pierwszą częścią potoku i służy do ładowania danych.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-231">The object is the first part of the pipeline, and loads the data.</span></span> <span data-ttu-id="ffa9e-232">W tym samouczku ładuje zestaw danych o komentarze i odpowiednie toksyczne lub inne niż toksyczne tonacji.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-232">For this tutorial, it loads a dataset with comments and corresponding toxic or non toxic sentiment.</span></span> <span data-ttu-id="ffa9e-233">Służy do tworzenia modelu i szkoleń.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-233">This is used to create the model, and train it.</span></span>

 <span data-ttu-id="ffa9e-234">Dodaj następujący kod jako pierwsza linia `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-234">Add the following code as the first line of the `Train` method:</span></span>

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#6 "loading training dataset")]

## <a name="extract-and-transform-the-data"></a><span data-ttu-id="ffa9e-235">Wyodrębnianie i przekształcania danych</span><span class="sxs-lookup"><span data-stu-id="ffa9e-235">Extract and transform the data</span></span>

<span data-ttu-id="ffa9e-236">Wstępne przetwarzanie i czyszczenie danych są ważne zadania, które występują przed zestaw danych jest efektywnie używać uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-236">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="ffa9e-237">Nieprzetworzone dane są często hałas i zawodnych i może brakować wartości.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-237">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="ffa9e-238">Korzystanie z danych bez tych zadań modelowania może spowodować wyświetlenie nieprawdziwych wyników.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-238">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="ffa9e-239">UCZENIE MASZYNOWE. Potoki przekształcenie firmy NET tworzą zbiór niestandardowych przekształceń, które są stosowane do danych przed szkolenie i testowanie.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-239">ML.NET's transform pipelines compose a custom set of transforms that are applied to your data before training or testing.</span></span> <span data-ttu-id="ffa9e-240">Przekształcenia głównym celem jest danych [cechowania](../resources/glossary.md#feature-engineering).</span><span class="sxs-lookup"><span data-stu-id="ffa9e-240">The transforms' primary purpose is data [featurization](../resources/glossary.md#feature-engineering).</span></span> <span data-ttu-id="ffa9e-241">Omówienie algorytmów uczenia maszynowego [neural](../resources/glossary.md#feature) dane, dzięki czemu następnym krokiem jest do przekształcania danych tekstowych do formatu, który rozpoznaje nasze algorytmy uczenia Maszynowego.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-241">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, so the next step is to transform our textual data into a format that our ML algorithms recognize.</span></span> <span data-ttu-id="ffa9e-242">Ten format jest [liczbowych wektor](../resources/glossary.md#numerical-feature-vector).</span><span class="sxs-lookup"><span data-stu-id="ffa9e-242">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="ffa9e-243">Następnie wywołaj `mlContext.Transforms.Text.FeaturizeText` które featurizes kolumny tekstowej (`SentimentText`) o nazwie kolumny do wektora liczbowych `Features` używane przez algorytm uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-243">Next, call `mlContext.Transforms.Text.FeaturizeText` which featurizes the text column (`SentimentText`) column into a numeric vector called `Features` used by the machine learning algorithm.</span></span> <span data-ttu-id="ffa9e-244">To wywołanie otoką zwracające <xref:Microsoft.ML.Data.EstimatorChain%601> skutecznie się potoku.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-244">This is a wrapper call that returns an <xref:Microsoft.ML.Data.EstimatorChain%601> that will effectively be a pipeline.</span></span> <span data-ttu-id="ffa9e-245">Nazwij to `pipeline` jako następnie dołączy trainer do `EstimatorChain`.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-245">Name this `pipeline` as you will then append the trainer to the `EstimatorChain`.</span></span> <span data-ttu-id="ffa9e-246">Dodaj jako następnego wiersza kodu:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-246">Add this as the next line of code:</span></span>

[!code-csharp[TextFeaturizingEstimator](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#7 "Add a TextFeaturizingEstimator")]

<span data-ttu-id="ffa9e-247">Jest to krok przetwarzania wstępnego cechowania.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-247">This is the preprocessing/featurization step.</span></span> <span data-ttu-id="ffa9e-248">Za pomocą dodatkowych składników dostępnych w strukturze ML.NET umożliwiają lepsze wyniki za pomocą modelu.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-248">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="ffa9e-249">Wybieranie algorytmu uczenia</span><span class="sxs-lookup"><span data-stu-id="ffa9e-249">Choose a learning algorithm</span></span>

<span data-ttu-id="ffa9e-250">Aby dodać instruktora, należy wywołać `mlContext.Transforms.Text.FeaturizeText` metody otoki, która zwraca <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> obiektu.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-250">To add the trainer, call the `mlContext.Transforms.Text.FeaturizeText` wrapper method which returns a <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> object.</span></span> <span data-ttu-id="ffa9e-251">Jest to uczeń drzewa decyzyjne, które będą używane w tym potoku.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-251">This is a decision tree learner you'll use in this pipeline.</span></span> <span data-ttu-id="ffa9e-252">`FastTreeBinaryClassificationTrainer` Jest dołączany do `pipeline` i akceptuje neural `SentimentText` (`Features`) i `Label` parametrów, aby dowiedzieć się więcej na podstawie historycznych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-252">The `FastTreeBinaryClassificationTrainer` is appended to the `pipeline` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

<span data-ttu-id="ffa9e-253">Dodaj następujący kod do `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-253">Add the following code to the `Train` method:</span></span>

[!code-csharp[FastTreeBinaryClassificationTrainer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#8 "Add a FastTreeBinaryClassificationTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="ffa9e-254">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="ffa9e-254">Train the model</span></span>

<span data-ttu-id="ffa9e-255">Uczenie modelu, <xref:Microsoft.ML.Data.TransformerChain%601>zgodnie z zestawu danych, który został załadowany i przekształcone.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-255">You train the model, <xref:Microsoft.ML.Data.TransformerChain%601>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="ffa9e-256">Po zdefiniowaniu estymatora uczenie modelu przy użyciu <xref:Microsoft.ML.Data.EstimatorChain%601.Fit*> przy jednoczesnym zapewnieniu dane szkoleniowe już załadowana.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-256">Once the estimator has been defined, you train your model using the <xref:Microsoft.ML.Data.EstimatorChain%601.Fit*> while providing the already loaded training data.</span></span> <span data-ttu-id="ffa9e-257">Spowoduje to zwrócenie modelu na potrzeby prognozy.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-257">This returns a model to use for predictions.</span></span> <span data-ttu-id="ffa9e-258">`pipeline.Fit()` szkolenie modeli potoku i zwraca `Transformer` na podstawie `DataView` przekazany.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-258">`pipeline.Fit()` trains the pipeline and returns a `Transformer` based on the `DataView` passed in.</span></span> <span data-ttu-id="ffa9e-259">Eksperyment nie jest wykonywane, dopóki nie dzieje.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-259">The experiment is not executed until this happens.</span></span>

<span data-ttu-id="ffa9e-260">Dodaj następujący kod do `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-260">Add the following code to the `Train` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#9 "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="ffa9e-261">Zapisz i wróć model jest uczony na potrzeby oceny</span><span class="sxs-lookup"><span data-stu-id="ffa9e-261">Save and Return the model trained to use for evaluation</span></span>

<span data-ttu-id="ffa9e-262">W tym momencie masz model typu <xref:Microsoft.ML.Data.TransformerChain%601> , można zintegrować wszystkich istniejących i nowych aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-262">At this point, you have a model of type <xref:Microsoft.ML.Data.TransformerChain%601> that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="ffa9e-263">Zwraca model na końcu `Train` metody.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-263">Return the model at the end of the `Train` method.</span></span>

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#10 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="ffa9e-264">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="ffa9e-264">Evaluate the model</span></span>

<span data-ttu-id="ffa9e-265">Teraz, po utworzeniu i uczony model, należy ocenić ją z innego zestawu danych do zapewniania jakości i sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-265">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="ffa9e-266">W `Evaluate` metody, model utworzony w `Train` jest przekazywany do obliczenia.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-266">In the `Evaluate` method, the model created in `Train` is passed in to be evaluated.</span></span> <span data-ttu-id="ffa9e-267">Tworzenie `Evaluate` metody tuż za `Train`, jak w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-267">Create the `Evaluate` method, just after `Train`, as in the following code:</span></span>

```csharp
public static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="ffa9e-268">`Evaluate` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-268">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="ffa9e-269">Ładuje zestawy danych testowych.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-269">Loads the test dataset.</span></span>
* <span data-ttu-id="ffa9e-270">Tworzy ewaluatora binarnego.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-270">Creates the binary evaluator.</span></span>
* <span data-ttu-id="ffa9e-271">Oblicza model oraz tworzenie metryk.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-271">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="ffa9e-272">Przedstawia metryki.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-272">Displays the metrics.</span></span>

<span data-ttu-id="ffa9e-273">Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `Train` wywołania metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-273">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#11 "Call the Evaluate method")]

<span data-ttu-id="ffa9e-274">Będzie załadować zestawu danych testowych za pomocą wcześniej zainicjowane `_textLoader` zmienna globalna z `_testDataPath` globalne pole.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-274">You'll load the test dataset using the previously initialized  `_textLoader` global variable with the `_testDataPath` global field.</span></span> <span data-ttu-id="ffa9e-275">Możesz ocenić modelu przy użyciu tego zestawu danych w celu sprawdzenia jakości.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-275">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="ffa9e-276">Dodaj następujący kod do `Evaluate` metody:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-276">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#12 "Load the test dataset")]

<span data-ttu-id="ffa9e-277">Następnie użyjemy usługi machine learning `model` parametru (transformatora), aby dane wejściowe funkcji i zwracają prognozy.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-277">Next, you'll use the machine learning `model` parameter (a transformer) to input the features and return predictions.</span></span> <span data-ttu-id="ffa9e-278">Dodaj następujący kod do `Evaluate` metodę jako następny wiersz:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-278">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#13 "Predict using the Transformer")]

<span data-ttu-id="ffa9e-279">`BinaryClassificationContext.Evaluate` Metoda oblicza metryk jakości `PredictionModel` przy użyciu określonego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-279">The `BinaryClassificationContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="ffa9e-280">Zwraca `BinaryClassificationEvaluator.CalibratedResult` obiekt zawiera ogólne metryki obliczone przez ewaluatory klasyfikacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-280">It returns a `BinaryClassificationEvaluator.CalibratedResult` object contains the overall metrics computed by binary classification evaluators.</span></span> <span data-ttu-id="ffa9e-281">Aby je wyświetlić, aby określić jakość modelu, należy pobrać pierwszy metryki.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-281">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="ffa9e-282">Dodaj następujący kod w następnym wierszu `Evaluate` metody:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-282">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#14 "Compute Metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="ffa9e-283">Wyświetlanie metryki dotyczące weryfikacji modelu</span><span class="sxs-lookup"><span data-stu-id="ffa9e-283">Displaying the metrics for model validation</span></span>

<span data-ttu-id="ffa9e-284">Użyj poniższego kodu, aby wyświetlić metryki, udostępnianie wyników, a następnie działanie na nich:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-284">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#15 "Display selected metrics")]

<span data-ttu-id="ffa9e-285">Aby zapisać swój model do pliku zip, przed zwróceniem, Dodaj następujący kod do wywoływania `SaveModelAsFile` metody w następnym wierszu `Evaluate`:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-285">To save your model to a .zip file before returning, add the following code to call the `SaveModelAsFile` method as the next line in `Evaluate`:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#23 "Save the model")]

## <a name="save-the-model-as-azip-file"></a><span data-ttu-id="ffa9e-286">Zapisz model jako plik a.zip</span><span class="sxs-lookup"><span data-stu-id="ffa9e-286">Save the model as a.zip file</span></span>

<span data-ttu-id="ffa9e-287">Tworzenie `SaveModelAsFile` metody tuż za `Evaluate` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-287">Create the `SaveModelAsFile` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="ffa9e-288">`SaveModelAsFile` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-288">The `SaveModelAsFile` method executes the following tasks:</span></span>

* <span data-ttu-id="ffa9e-289">Zapisuje modelu w postaci pliku zip.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-289">Saves the model as a .zip file.</span></span>

<span data-ttu-id="ffa9e-290">Następnie utwórz metodę, aby zapisać modelu mogą być używane ponownie i używane w innych aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-290">Next, create a method to save the model so that it can be reused and consumed in other applications.</span></span> <span data-ttu-id="ffa9e-291">`ITransformer` Ma <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> metodę, która przyjmuje `_modelPath` globalne pola i <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-291">The `ITransformer` has a <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> method that takes in the `_modelPath` global field, and a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="ffa9e-292">Aby zapisać ten element jako plik zip, należy utworzyć `FileStream` bezpośrednio przed wywołaniem `SaveTo` metody.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-292">To save this as a zip file, you'll create the `FileStream` immediately before calling the `SaveTo` method.</span></span> <span data-ttu-id="ffa9e-293">Dodaj następujący kod do `SaveModelAsFile` metodę jako następny wiersz:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-293">Add the following code to the `SaveModelAsFile` method as the next line:</span></span>

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#24 "Add the SaveTo Method")]
<span data-ttu-id="ffa9e-294">Wdrażanie i przewidywanie załadować model, można również wyświetlić, którym został zapisany plik przy pisaniu komunikatu konsoli, za pomocą `_modelPath`, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-294">Deploy and Predict with a loaded model You could also display where the file was written by writing a console message with the `_modelPath`, using the following code:</span></span>

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="predict-the-test-data-outcome-with-the-saved-model"></a><span data-ttu-id="ffa9e-295">Wynik testu danych przy użyciu zapisanych modelu prognozowania</span><span class="sxs-lookup"><span data-stu-id="ffa9e-295">Predict the test data outcome with the saved model</span></span>

<span data-ttu-id="ffa9e-296">Tworzenie `Predict` metody tuż za `Evaluate` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-296">Create the `Predict` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void Predict(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="ffa9e-297">`Predict` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-297">The `Predict` method executes the following tasks:</span></span>

* <span data-ttu-id="ffa9e-298">Tworzy pojedynczy komentarz danych testowych.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-298">Creates a single comment of test data.</span></span>
* <span data-ttu-id="ffa9e-299">Prognozuje tonacji na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-299">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="ffa9e-300">Łączy w sobie testowanie, danych i prognoz dla raportowania.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-300">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="ffa9e-301">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-301">Displays the predicted results.</span></span>

<span data-ttu-id="ffa9e-302">Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `Evaluate` wywołania metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-302">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#16 "Call the Predict method")]

<span data-ttu-id="ffa9e-303">Gdy `model` jest `transformer` który operuje na wiele wierszy danych, to bardzo typowy scenariusz w środowisku produkcyjnym jest na potrzeby prognoz na poszczególne przykłady.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-303">While the `model` is a `transformer` that operates on many rows of data, a very common production scenario is a need for predictions on individual examples.</span></span> <span data-ttu-id="ffa9e-304"><xref:Microsoft.ML.PredictionEngine%602> Jest otoką, który jest zwracany z `CreatePredictionEngine` metody.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-304">The <xref:Microsoft.ML.PredictionEngine%602> is a wrapper that is returned from the `CreatePredictionEngine` method.</span></span> <span data-ttu-id="ffa9e-305">Możemy dodać następujący kod, aby utworzyć `PredictionEngine` jako pierwszy wiersz w `Predict` metody:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-305">Let's add the following code to create the `PredictionEngine` as the first line in the `Predict` Method:</span></span>

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#17 "Create the PredictionEngine")]
  
<span data-ttu-id="ffa9e-306">Dodaj komentarz do testowania uczonego modelu prognozowania w `Predict` metody przez utworzenie wystąpienia `SentimentData`:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-306">Add a comment to test the trained model's prediction in the `Predict` method by creating an instance of `SentimentData`:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#18 "Create test data for single prediction")]

 <span data-ttu-id="ffa9e-307">Możesz go używać, aby przewidzieć toksyczne lub inne niż toksyczne tonacji pojedyncze wystąpienie danych komentarz.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-307">You can use that to predict the Toxic or Non Toxic sentiment of a single instance of the comment data.</span></span> <span data-ttu-id="ffa9e-308">Aby uzyskać prognozę, użyj <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> na danych.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-308">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="ffa9e-309">Należy pamiętać, że dane wejściowe to ciąg, a model zawiera cechowania.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-309">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="ffa9e-310">Potok jest zsynchronizowany podczas uczenia i przewidywania.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-310">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="ffa9e-311">Nie trzeba napisać kod przetwarzania wstępnego cechowania specjalnie dla prognoz i zajmuje się tego samego interfejsu API i usługi batch jednorazowe prognozy.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-311">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#19 "Create a prediction of sentiment")]

### <a name="using-the-model-prediction"></a><span data-ttu-id="ffa9e-312">Przy użyciu modelu: prognoz</span><span class="sxs-lookup"><span data-stu-id="ffa9e-312">Using the model: prediction</span></span>

<span data-ttu-id="ffa9e-313">Wyświetlanie `SentimentText` i odpowiednie przewidywania opinii w celu udostępniania wyników i odpowiednie do nich działanie na nich.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-313">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="ffa9e-314">Jest to nazywane operacjonalizacji, jako część zasad operacyjnych przy użyciu zwracanych danych.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-314">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="ffa9e-315">Tworzenie ekranu wyników za pomocą następujących <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-315">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#20 "Display prediction output")]

## <a name="deploy-and-predict-with-a-loaded-model"></a><span data-ttu-id="ffa9e-316">Wdrażanie i przewidywanie załadować modelu</span><span class="sxs-lookup"><span data-stu-id="ffa9e-316">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="ffa9e-317">Tworzenie `PredictWithModelLoadedFromFile` metody, tuż przed `SaveModelAsFile` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-317">Create the `PredictWithModelLoadedFromFile` method, just before the `SaveModelAsFile` method, using the following code:</span></span>

```csharp
public static void PredictWithModelLoadedFromFile(MLContext mlContext)
{

}
```

<span data-ttu-id="ffa9e-318">`PredictWithModelLoadedFromFile` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-318">The `PredictWithModelLoadedFromFile` method executes the following tasks:</span></span>

* <span data-ttu-id="ffa9e-319">Tworzy dane testowe usługi batch.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-319">Creates batch test data.</span></span>
* <span data-ttu-id="ffa9e-320">Prognozuje tonacji na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-320">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="ffa9e-321">Łączy w sobie testowanie, danych i prognoz dla raportowania.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-321">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="ffa9e-322">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-322">Displays the predicted results.</span></span>

<span data-ttu-id="ffa9e-323">Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `Predict` wywołania metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-323">Add a call to the new method from the `Main` method, right under the `Predict` method call, using the following code:</span></span>

[!code-csharp[CallPredictModelLoaded](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#25 "Call the PredictWithModelLoadedFromFile method")]

<span data-ttu-id="ffa9e-324">Dodaj niektóre komentarze, aby przetestować prognozy uczonego modelu w `PredictWithModelLoadedFromFile` metody:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-324">Add some comments to test the trained model's predictions in the `PredictWithModelLoadedFromFile` method:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#26 "Create test data for predictions")]

<span data-ttu-id="ffa9e-325">Model obciążenia</span><span class="sxs-lookup"><span data-stu-id="ffa9e-325">Load the model</span></span>

[!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#27 "Load the model")]

<span data-ttu-id="ffa9e-326">Teraz, gdy model, możesz go używać, aby przewidzieć toksyczne lub inne niż toksyczne tonacji przy użyciu danych komentarz <xref:Microsoft.ML.Core.Data.ITransformer.Transform%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-326">Now that you have a model, you can use that to predict the Toxic or Non Toxic sentiment of the comment data using the <xref:Microsoft.ML.Core.Data.ITransformer.Transform%2A> method.</span></span> <span data-ttu-id="ffa9e-327">Aby uzyskać prognozę, użyj `Predict` na nowych danych.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-327">To get a prediction, use `Predict` on new data.</span></span> <span data-ttu-id="ffa9e-328">Należy pamiętać, że dane wejściowe to ciąg, a model zawiera cechowania.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-328">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="ffa9e-329">Potok jest zsynchronizowany podczas uczenia i przewidywania.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-329">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="ffa9e-330">Nie trzeba napisać kod przetwarzania wstępnego cechowania specjalnie dla prognoz i zajmuje się tego samego interfejsu API i usługi batch jednorazowe prognozy.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-330">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span> <span data-ttu-id="ffa9e-331">Dodaj następujący kod do `PredictWithModelLoadedFromFile` metodę dla prognoz:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-331">Add the following code to the `PredictWithModelLoadedFromFile` method for the predictions:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#28 "Create predictions of sentiments")]

### <a name="using-the-loaded-model-for-prediction"></a><span data-ttu-id="ffa9e-332">Przy użyciu załadować modelu do prognozowania</span><span class="sxs-lookup"><span data-stu-id="ffa9e-332">Using the loaded model for prediction</span></span>

<span data-ttu-id="ffa9e-333">Wyświetlanie `SentimentText` i odpowiednie przewidywania opinii w celu udostępniania wyników i odpowiednie do nich działanie na nich.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-333">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="ffa9e-334">Jest to nazywane operacjonalizacji, jako część zasad operacyjnych przy użyciu zwracanych danych.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-334">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="ffa9e-335">Utwórz nagłówek dla wyników za pomocą następujących <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-335">Create a header for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#29 "Display prediction outputs")]

<span data-ttu-id="ffa9e-336">Przed wyświetleniem wyników, Połącz opinii i prognozowania ze sobą, aby zobaczyć, oryginalnym komentarzem z jego przewidywane wskaźniki nastrojów klientów.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-336">Before displaying the predicted results, combine the sentiment and prediction together to see the original comment with its predicted sentiment.</span></span> <span data-ttu-id="ffa9e-337">Poniższy kod używa <xref:System.Linq.Enumerable.Zip%2A> metodę, aby to zrobić, obok więc Dodaj ten kod:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-337">The following code uses the <xref:System.Linq.Enumerable.Zip%2A> method to make that happen, so add that code next:</span></span>

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#30 "Build the pairs of sentiment data and predictions")]

<span data-ttu-id="ffa9e-338">Teraz, gdy zostały połączone `SentimentText` i `Sentiment` do klasy, można wyświetlić wyniki za pomocą <xref:System.Console.WriteLine?displayProperty=nameWithType> metody:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-338">Now that you've combined the `SentimentText` and `Sentiment` into a class, you can display the results using the <xref:System.Console.WriteLine?displayProperty=nameWithType> method:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#31 "Display the predictions")]

<span data-ttu-id="ffa9e-339">Ponieważ wywnioskować, że jest nową funkcją w C# 7.1 i wersją języka domyślnego projektu języka C# 7.0 nazwami elementów krotki, musisz zmienić wersję języka C# 7.1 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-339">Because inferred tuple element names are a new feature in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span>
<span data-ttu-id="ffa9e-340">Aby to zrobić, kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-340">To do that, right-click on the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="ffa9e-341">Wybierz **kompilacji** kartę, a następnie wybierz pozycję **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-341">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="ffa9e-342">Z listy rozwijanej wybierz **języka C# 7.1** (lub nowsza wersja).</span><span class="sxs-lookup"><span data-stu-id="ffa9e-342">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="ffa9e-343">Wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-343">Select the **OK** button.</span></span>

## <a name="results"></a><span data-ttu-id="ffa9e-344">Wyniki</span><span class="sxs-lookup"><span data-stu-id="ffa9e-344">Results</span></span>

<span data-ttu-id="ffa9e-345">Wyniki powinny być podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-345">Your results should be similar to the following.</span></span> <span data-ttu-id="ffa9e-346">Ponieważ przetwarza potoku, wyświetla komunikaty.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-346">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="ffa9e-347">Może zostać wyświetlony ostrzeżenia lub komunikaty przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-347">You may see warnings, or processing messages.</span></span> <span data-ttu-id="ffa9e-348">Te zostały usunięte z następujących wyników dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-348">These have been removed from the following results for clarity.</span></span>

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 94.44%
Auc: 98.77%
F1Score: 94.74%
=============== End of model evaluation ===============

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This is a very rude movie | Prediction: Toxic | Probability: 0.5297049
=============== End of Predictions ===============

=============== New iteration of Model ===============
=============== Create and Train the Model ===============
=============== End of training ===============


The model is saved to: C:\Tutorial\SentimentAnalysis\bin\Debug\netcoreapp2.1\Data\Model.zip

=============== Prediction Test of loaded model with a multiple sample ===============

Sentiment: This is a very rude movie | Prediction: Toxic | Probability: 0.4585565
Sentiment: I love this article. | Prediction: Not Toxic | Probability: 0.09454837

```

<span data-ttu-id="ffa9e-349">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="ffa9e-349">Congratulations!</span></span> <span data-ttu-id="ffa9e-350">Model uczenia maszynowego dla klasyfikacji i prognozowanie tonacji wiadomości teraz zostały pomyślnie skompilowane.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-350">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span> <span data-ttu-id="ffa9e-351">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="ffa9e-351">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ffa9e-352">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="ffa9e-352">Next steps</span></span>

<span data-ttu-id="ffa9e-353">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="ffa9e-353">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="ffa9e-354">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="ffa9e-354">Understand the problem</span></span>
> * <span data-ttu-id="ffa9e-355">Wybieranie algorytmu uczenia maszynowego odpowiednie</span><span class="sxs-lookup"><span data-stu-id="ffa9e-355">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="ffa9e-356">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="ffa9e-356">Prepare your data</span></span>
> * <span data-ttu-id="ffa9e-357">Przekształcanie danych</span><span class="sxs-lookup"><span data-stu-id="ffa9e-357">Transform the data</span></span>
> * <span data-ttu-id="ffa9e-358">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="ffa9e-358">Train the model</span></span>
> * <span data-ttu-id="ffa9e-359">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="ffa9e-359">Evaluate the model</span></span>
> * <span data-ttu-id="ffa9e-360">Prognozowanie za pomocą uczonego modelu</span><span class="sxs-lookup"><span data-stu-id="ffa9e-360">Predict with the trained model</span></span>
> * <span data-ttu-id="ffa9e-361">Wdrażanie i przewidywanie załadować modelu</span><span class="sxs-lookup"><span data-stu-id="ffa9e-361">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="ffa9e-362">Przejdź do następnego samouczka, aby dowiedzieć się więcej</span><span class="sxs-lookup"><span data-stu-id="ffa9e-362">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="ffa9e-363">Klasyfikacja problemu</span><span class="sxs-lookup"><span data-stu-id="ffa9e-363">Issue Classification</span></span>](github-issue-classification.md)
