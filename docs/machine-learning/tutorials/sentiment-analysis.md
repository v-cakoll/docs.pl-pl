---
title: Użyj ML.NET w przypadku klasyfikacji binarnej analizy wskaźniki nastrojów klientów
description: Dowiedzieć się, jak za pomocą ML.NET w scenariuszu klasyfikacji binarnej można określić sposób użycia prognozowania wskaźniki nastrojów klientów podjęcie odpowiednich działań.
ms.date: 06/04/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 5194ec8b41304cc06848400607d5d76f288d42e6
ms.sourcegitcommit: 640cee8fc5d256cdd80e5b80240469feac10499e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2018
ms.locfileid: "36298282"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a><span data-ttu-id="dc651-103">Samouczek: Użyj ML.NET w przypadku klasyfikacji binarnej analizy wskaźniki nastrojów klientów</span><span class="sxs-lookup"><span data-stu-id="dc651-103">Tutorial: Use ML.NET in a sentiment analysis binary classification scenario</span></span>

> [!NOTE]
> <span data-ttu-id="dc651-104">W tym temacie odnosi się do ML.NET, który jest obecnie w wersji zapoznawczej, i materiały może być może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="dc651-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="dc651-105">Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="dc651-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="dc651-106">Ten samouczek przykładowy przedstawiono przy użyciu ML.NET utworzenie klasyfikatora programu wskaźniki nastrojów klientów za pomocą aplikacji konsoli .NET Core przy użyciu języka C# w programie Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="dc651-106">This sample tutorial illustrates using ML.NET to create a sentiment classifier via a .NET Core console application using C# in Visual Studio 2017.</span></span>

<span data-ttu-id="dc651-107">Z tego samouczka, dowiesz się, jak:</span><span class="sxs-lookup"><span data-stu-id="dc651-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="dc651-108">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="dc651-108">Understand the problem</span></span>
> * <span data-ttu-id="dc651-109">Wybierz zadanie learning odpowiednie maszyny</span><span class="sxs-lookup"><span data-stu-id="dc651-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="dc651-110">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="dc651-110">Prepare your data</span></span>
> * <span data-ttu-id="dc651-111">Tworzenie potoku learning</span><span class="sxs-lookup"><span data-stu-id="dc651-111">Create the learning pipeline</span></span>
> * <span data-ttu-id="dc651-112">Klasyfikator obciążenia</span><span class="sxs-lookup"><span data-stu-id="dc651-112">Load a classifier</span></span>
> * <span data-ttu-id="dc651-113">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="dc651-113">Train the model</span></span>
> * <span data-ttu-id="dc651-114">Ocena modelu z innego zestawu danych</span><span class="sxs-lookup"><span data-stu-id="dc651-114">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="dc651-115">Wyniki testu danych z modelu prognozowania</span><span class="sxs-lookup"><span data-stu-id="dc651-115">Predict the test data outcomes with the model</span></span>

## <a name="sentiment-analysis-sample-overview"></a><span data-ttu-id="dc651-116">Omówienie przykładowej analizy wskaźniki nastrojów klientów</span><span class="sxs-lookup"><span data-stu-id="dc651-116">Sentiment analysis sample overview</span></span>

<span data-ttu-id="dc651-117">Próbka jest aplikacji konsoli, która używa ML.NET do nauczenia modelu, który klasyfikowanych i prognozuje wskaźniki nastrojów klientów jako dodatnią lub ujemną.</span><span class="sxs-lookup"><span data-stu-id="dc651-117">The sample is a console app that uses ML.NET to train a model that classifies and predicts sentiment as either positive or negative.</span></span> <span data-ttu-id="dc651-118">Oblicza model z drugiego zestawu danych do analizy jakości.</span><span class="sxs-lookup"><span data-stu-id="dc651-118">It also evaluates the model with a second dataset for quality analysis.</span></span> <span data-ttu-id="dc651-119">Zestawy danych wskaźniki nastrojów klientów pochodzą z projektu WikiDetox.</span><span class="sxs-lookup"><span data-stu-id="dc651-119">The sentiment datasets are from the WikiDetox project.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dc651-120">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="dc651-120">Prerequisites</span></span>

* <span data-ttu-id="dc651-121">[Visual Studio 2017 15,6 lub nowszym](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) z obciążeniem "Programowanie wieloplatformowych .NET Core" zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="dc651-121">[Visual Studio 2017 15.6 or later](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="dc651-122">[Wikipedia detox wiersz danych karta rozdzielonych plików (wikiPedia-detox-250-wiersza data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).</span><span class="sxs-lookup"><span data-stu-id="dc651-122">The [Wikipedia detox line data tab separated file (wikiPedia-detox-250-line-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span>
* <span data-ttu-id="dc651-123">[Karta testu linii detox Wikipedia rozdzielonych plików (wikipedia-detox-250-wiersza test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).</span><span class="sxs-lookup"><span data-stu-id="dc651-123">The [Wikipedia detox line test tab separated file (wikipedia-detox-250-line-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="dc651-124">Machine learning w przepływie pracy</span><span class="sxs-lookup"><span data-stu-id="dc651-124">Machine learning workflow</span></span>

<span data-ttu-id="dc651-125">W tym samouczku wykonuje przepływ pracy, który umożliwia procesu przenieść w sposób uporządkowany uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="dc651-125">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="dc651-126">Fazy przepływu pracy są następujące:</span><span class="sxs-lookup"><span data-stu-id="dc651-126">The workflow phases are as follows:</span></span>

1. <span data-ttu-id="dc651-127">**Zrozumieć**</span><span class="sxs-lookup"><span data-stu-id="dc651-127">**Understand the problem**</span></span>
2. <span data-ttu-id="dc651-128">**Pozyskiwanie danych**</span><span class="sxs-lookup"><span data-stu-id="dc651-128">**Ingest the data**</span></span>
3. <span data-ttu-id="dc651-129">**Przetwarzanie wstępne danych i inżynieria**</span><span class="sxs-lookup"><span data-stu-id="dc651-129">**Data preprocess and feature engineering**</span></span>
4. <span data-ttu-id="dc651-130">**Szkolenie i prognozowania modelu**</span><span class="sxs-lookup"><span data-stu-id="dc651-130">**Train and predict the model**</span></span>
5. <span data-ttu-id="dc651-131">**Ocena modelu**</span><span class="sxs-lookup"><span data-stu-id="dc651-131">**Evaluate the model**</span></span>
6. <span data-ttu-id="dc651-132">**Operationalization modelu**</span><span class="sxs-lookup"><span data-stu-id="dc651-132">**Model operationalization**</span></span>

### <a name="understand-the-problem"></a><span data-ttu-id="dc651-133">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="dc651-133">Understand the problem</span></span>

<span data-ttu-id="dc651-134">Należy najpierw zrozumieć, dlatego mogą być dzielone do części, które obsługują tworzenie i uczenie modelu.</span><span class="sxs-lookup"><span data-stu-id="dc651-134">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="dc651-135">Przerywanie problem w dół do prognozowania i ocena wyników.</span><span class="sxs-lookup"><span data-stu-id="dc651-135">Breaking the problem down you to predict and evaluate the results.</span></span>

<span data-ttu-id="dc651-136">Ten problem, w tym samouczku jest zrozumienie, przychodzących witryny sieci Web komentarz wskaźniki nastrojów klientów podjęcie odpowiednich działań.</span><span class="sxs-lookup"><span data-stu-id="dc651-136">The problem for this tutorial is to understand incoming website comment sentiment to take the appropriate action.</span></span>

<span data-ttu-id="dc651-137">Problem można podzielić tekstu wskaźniki nastrojów klientów i wskaźniki nastrojów klientów wartość żądane dane do uczenia modelu o i wartość przewidywane wskaźniki nastrojów klientów, które można ocenić i następnie użyć pod względem.</span><span class="sxs-lookup"><span data-stu-id="dc651-137">You can break down the problem to the sentiment text and sentiment value for the data you want to train the model with, and a predicted sentiment value that you can evaluate and then use operationally.</span></span>

<span data-ttu-id="dc651-138">Następnie należy **określić** wskaźniki nastrojów klientów, która ułatwia wybór zadania uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="dc651-138">You then need to **determine** the sentiment, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="dc651-139">Wybierz zadanie learning odpowiednie maszyny</span><span class="sxs-lookup"><span data-stu-id="dc651-139">Select the appropriate machine learning task</span></span>

<span data-ttu-id="dc651-140">Z tym problemem znasz następujące fakty:</span><span class="sxs-lookup"><span data-stu-id="dc651-140">With this problem, you know the following facts:</span></span>

<span data-ttu-id="dc651-141">Uczenie danych: komentarze witryny sieci Web może być liczbą dodatnią lub ujemną (**wskaźniki nastrojów klientów**).</span><span class="sxs-lookup"><span data-stu-id="dc651-141">Training data: website comments can be positive or negative (**sentiment**).</span></span>
<span data-ttu-id="dc651-142">Przewidywanie **wskaźniki nastrojów klientów** nowego komentarza witryny sieci Web, dodatnie lub ujemne, takich jak w poniższych przykładach:</span><span class="sxs-lookup"><span data-stu-id="dc651-142">Predict the **sentiment** of a new website comment, either positive or negative, such as in the following examples:</span></span>

* <span data-ttu-id="dc651-143">Unikaj umieszczania Dodawanie żadnego znaczenia do Wikipedia.</span><span class="sxs-lookup"><span data-stu-id="dc651-143">Please refrain from adding nonsense to Wikipedia.</span></span>
* <span data-ttu-id="dc651-144">Jest najlepsza i artykułu należy oznacza, że.</span><span class="sxs-lookup"><span data-stu-id="dc651-144">He is the best, and the article should say that.</span></span>

<span data-ttu-id="dc651-145">Zadanie klasyfikacji maszyny learning jest najbardziej odpowiednie dla tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="dc651-145">The classification machine learning task is best suited for this scenario.</span></span>

### <a name="about-the-classification-task"></a><span data-ttu-id="dc651-146">Zadania klasyfikacji</span><span class="sxs-lookup"><span data-stu-id="dc651-146">About the classification task</span></span>

<span data-ttu-id="dc651-147">Klasyfikacja jest zadanie uczenia maszynowego, które używa danych do **określić** kategorii, typu lub klasy elementu lub wiersza danych.</span><span class="sxs-lookup"><span data-stu-id="dc651-147">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="dc651-148">Na przykład można użyć klasyfikacji:</span><span class="sxs-lookup"><span data-stu-id="dc651-148">For example, you can use classification to:</span></span>

* <span data-ttu-id="dc651-149">Zidentyfikuj wskaźniki nastrojów klientów jako dodatnią lub ujemną.</span><span class="sxs-lookup"><span data-stu-id="dc651-149">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="dc651-150">Klasyfikowanie poczty e-mail jako wiadomości-śmieci, wiadomości-śmieci lub dobra.</span><span class="sxs-lookup"><span data-stu-id="dc651-150">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="dc651-151">Ustal, czy pacjenta laboratorium próbki jest cancerous.</span><span class="sxs-lookup"><span data-stu-id="dc651-151">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="dc651-152">Klasyfikowanie klientów przez ich większego ukierunkowania odpowiedzieć kampanii sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="dc651-152">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="dc651-153">Zadania klasyfikacji są często jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="dc651-153">Classification tasks are frequently one of the following types:</span></span>

* <span data-ttu-id="dc651-154">Dane binarne: A i B.</span><span class="sxs-lookup"><span data-stu-id="dc651-154">Binary: either A or B.</span></span>
* <span data-ttu-id="dc651-155">Multiklasa: wiele kategorii, które można przewidzieć przy użyciu pojedynczego modelu.</span><span class="sxs-lookup"><span data-stu-id="dc651-155">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="dc651-156">Tworzenie aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="dc651-156">Create a console application</span></span>

1. <span data-ttu-id="dc651-157">Otwórz program Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="dc651-157">Open Visual Studio 2017.</span></span> <span data-ttu-id="dc651-158">Wybierz **pliku** > **nowy** > **projektu** na pasku menu.</span><span class="sxs-lookup"><span data-stu-id="dc651-158">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="dc651-159">W *nowy projekt*\* okno dialogowe, wybierz opcję **Visual C#** węzła następuje **.NET Core** węzła.</span><span class="sxs-lookup"><span data-stu-id="dc651-159">In the *New Project*\* dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="dc651-160">Następnie wybierz **aplikacji konsoli (.NET Core)** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="dc651-160">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="dc651-161">W **nazwa** polu tekstowym, wpisz "SentimentAnalysis", a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="dc651-161">In the **Name** text box, type "SentimentAnalysis" and then select the **OK** button.</span></span>

2. <span data-ttu-id="dc651-162">Utwórz katalog o nazwie *danych* w projekcie, aby zapisać pliki zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="dc651-162">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="dc651-163">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj** > **nowy Folder**.</span><span class="sxs-lookup"><span data-stu-id="dc651-163">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="dc651-164">Wpisz "Dane" i naciśnij Enter.</span><span class="sxs-lookup"><span data-stu-id="dc651-164">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="dc651-165">Zainstaluj **pakietu NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="dc651-165">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="dc651-166">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="dc651-166">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="dc651-167">Wybierz polecenie "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj **Microsoft.ML**, wybierz z listy tego pakietu i wybierz **zainstalować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="dc651-167">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="dc651-168">Wybierz **OK** znajdującego się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdującego się na **akceptacji licencji** okna dialogowego jeśli użytkownik Akceptuję warunki licencji dla pakietów na liście.</span><span class="sxs-lookup"><span data-stu-id="dc651-168">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="dc651-169">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="dc651-169">Prepare your data</span></span>

1. <span data-ttu-id="dc651-170">Pobierz [WikiPedia detox-250-wiersza data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) i [wikipedia-detox-250-wiersza test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) danych ustawia i zapisywanie ich *danych* folder utworzony wcześniej.</span><span class="sxs-lookup"><span data-stu-id="dc651-170">Download the [WikiPedia detox-250-line-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) and the [wikipedia-detox-250-line-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="dc651-171">Modelu uczenia maszynowego przygotowuje pierwszego zestawu danych, a drugi może służyć do oceny, jak dokładny jest modelem.</span><span class="sxs-lookup"><span data-stu-id="dc651-171">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="dc651-172">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy każdy z \*.tsv pliki i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="dc651-172">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="dc651-173">W obszarze **zaawansowane**, zmień wartość **Kopiuj do katalogu wyjściowego** do **zawsze**.</span><span class="sxs-lookup"><span data-stu-id="dc651-173">Under **Advanced**, change the value of **Copy to Output Directory** to **Always**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="dc651-174">Tworzenie klas i zdefiniować ścieżki</span><span class="sxs-lookup"><span data-stu-id="dc651-174">Create classes and define paths</span></span>

<span data-ttu-id="dc651-175">Dodaj następujące dodatkowe `using` instrukcje na początku *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="dc651-175">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="dc651-176">Musisz utworzyć trzy zmienne globalne, aby mógł pomieścić ścieżka ostatnio pobranych plików:</span><span class="sxs-lookup"><span data-stu-id="dc651-176">You need to create three global variables to hold the path to the recently downloaded files:</span></span>

* <span data-ttu-id="dc651-177">`_dataPath` zawiera ścieżkę do zestawu danych używany do uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="dc651-177">`_dataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="dc651-178">`_testDataPath` zawiera ścieżkę do zestawu danych używane do oceny modelu.</span><span class="sxs-lookup"><span data-stu-id="dc651-178">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="dc651-179">`_modelPath` zawiera ścieżkę, w której jest zapisywany trenowanego modelu.</span><span class="sxs-lookup"><span data-stu-id="dc651-179">`_modelPath` has the path where the trained model is saved.</span></span>

<span data-ttu-id="dc651-180">Dodaj następujący kod do prawej wiersz powyżej `Main` metodę, aby określić ostatnio pobranych plików:</span><span class="sxs-lookup"><span data-stu-id="dc651-180">Add the following code to the line right above the `Main` method to specify the recently downloaded files:</span></span>

[!code-csharp[Declare file variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#2 "Declare variables to store data files")]

<span data-ttu-id="dc651-181">Musisz utworzyć niektórych klas dla danych wejściowych i prognoz.</span><span class="sxs-lookup"><span data-stu-id="dc651-181">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="dc651-182">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="dc651-182">Add a new class to your project:</span></span>

1. <span data-ttu-id="dc651-183">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="dc651-183">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="dc651-184">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmienić **nazwa** do *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="dc651-184">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="dc651-185">Następnie wybierz opcję **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="dc651-185">Then, select the **Add** button.</span></span>

    <span data-ttu-id="dc651-186">*SentimentData.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="dc651-186">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="dc651-187">Dodaj następujące `using` instrukcji na początku *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="dc651-187">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#1 "Add necessary usings")]

<span data-ttu-id="dc651-188">Usuń istniejącą definicję klasy i Dodaj następujący kod, który ma dwie klasy `SentimentData` i `SentimentPrediction`, do *SentimentData.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="dc651-188">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#2 "Declare data record types")]

<span data-ttu-id="dc651-189">`SentimentData` Klasa zestawu danych wejściowych i ma `float` (`Sentiment`) mający wartość wskaźniki nastrojów klientów dodatnie lub ujemne, a ciąg komentarza (`SentimentText`).</span><span class="sxs-lookup"><span data-stu-id="dc651-189">`SentimentData` is the input dataset class and has a `float` (`Sentiment`) that has a value for sentiment of either positive or negative, and a string for the comment (`SentimentText`).</span></span> <span data-ttu-id="dc651-190">Oba pola mają `Column` atrybuty dołączone do nich.</span><span class="sxs-lookup"><span data-stu-id="dc651-190">Both fields have `Column` attributes attached to them.</span></span> <span data-ttu-id="dc651-191">Ten atrybut Opisuje kolejność każdego pola w pliku danych, który jest `Label` pola.</span><span class="sxs-lookup"><span data-stu-id="dc651-191">This attribute describes the order of each field in the data file, and which is the `Label` field.</span></span> <span data-ttu-id="dc651-192">`SentimentPrediction` Klasa służy do prognozowania po zakończenia uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="dc651-192">`SentimentPrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="dc651-193">Składa się z jednego typu boolean (`Sentiment`) i `PredictedLabel` `ColumnName` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="dc651-193">It has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="dc651-194">`Label` Jest używany do tworzenia i nauczenia modelu, a także używane z drugiego zestawu danych do oceny modelu.</span><span class="sxs-lookup"><span data-stu-id="dc651-194">The `Label` is used to create and train the model, and it's also used with a second dataset to evaluate the model.</span></span> <span data-ttu-id="dc651-195">`PredictedLabel` Jest używany podczas prognozowania i oceny.</span><span class="sxs-lookup"><span data-stu-id="dc651-195">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="dc651-196">Do oceny są używane dane wejściowe dane szkoleniowe, przewidywane wartości i modelu.</span><span class="sxs-lookup"><span data-stu-id="dc651-196">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="dc651-197">W *Program.cs* Zmień `Main` podpis metody zastępując `void` z `async Task`, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="dc651-197">In the *Program.cs* file, change the `Main` method signature by replacing `void` with `async Task`, as in the following example:</span></span>

```csharp
static async Task Main(string[] args) 
{

}
```

<span data-ttu-id="dc651-198">Możesz dodać `async` do `Main` z <xref:System.Threading.Tasks.Task> typ zwracany, ponieważ są zapisywane modelu w pliku zip później, a program musi czekać, aż do zakończenia tego zadania zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="dc651-198">You add `async` to `Main` with a <xref:System.Threading.Tasks.Task> return type because you're saving the model to a zip file later, and the program needs to wait until that external task completes.</span></span>

> [!NOTE]
> <span data-ttu-id="dc651-199">*Async głównego* metoda pozwala na użycie `await` w Twojej `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="dc651-199">An *async main* method enables you to use `await` in your `Main` method.</span></span> <span data-ttu-id="dc651-200">Aby uzyskać więcej informacji, zobacz [async głównego](../../../docs/csharp/programming-guide/main-and-command-args/index.md) w Podręczniku programowania C#.</span><span class="sxs-lookup"><span data-stu-id="dc651-200">For more information, see the [async main](../../../docs/csharp/programming-guide/main-and-command-args/index.md) topic in the C# programming guide.</span></span>

<span data-ttu-id="dc651-201">Zastąp `Console.WriteLine("Hello World!")` wiersza w następującym kodem `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="dc651-201">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[Train](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#3 "Train your model")]

<span data-ttu-id="dc651-202">`Train` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="dc651-202">The `Train` method executes the following tasks:</span></span>

* <span data-ttu-id="dc651-203">Ładuje lub wysyła strumień danych.</span><span class="sxs-lookup"><span data-stu-id="dc651-203">Loads or ingests the data.</span></span>
* <span data-ttu-id="dc651-204">Przetwarza wstępnie i featurizes danych.</span><span class="sxs-lookup"><span data-stu-id="dc651-204">Preprocesses and featurizes the data.</span></span>
* <span data-ttu-id="dc651-205">Przygotowuje modelu.</span><span class="sxs-lookup"><span data-stu-id="dc651-205">Trains the model.</span></span>
* <span data-ttu-id="dc651-206">Prognozuje wskaźniki nastrojów klientów oparte na danych testowych.</span><span class="sxs-lookup"><span data-stu-id="dc651-206">Predicts sentiment based on test data.</span></span>

<span data-ttu-id="dc651-207">Utwórz `Train` metody tuż po `Main` metodę, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="dc651-207">Create the `Train` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static async Task<PredictionModel<SentimentData, SentimentPrediction>> Train()
{

}
```

## <a name="ingest-the-data"></a><span data-ttu-id="dc651-208">Pozyskiwanie danych</span><span class="sxs-lookup"><span data-stu-id="dc651-208">Ingest the data</span></span>

<span data-ttu-id="dc651-209">Inicjuje nowe wystąpienie klasy <xref:Microsoft.ML.LearningPipeline> zawierające ładowanie danych, przetwarzanie danych/featurization i modelu.</span><span class="sxs-lookup"><span data-stu-id="dc651-209">Initialize a new instance of <xref:Microsoft.ML.LearningPipeline> that will include the data loading, data processing/featurization, and model.</span></span> <span data-ttu-id="dc651-210">Dodaj następujący kod jako pierwszy wiersz `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="dc651-210">Add the following code as the first line of the `Train` method:</span></span>

[!code-csharp[LearningPipeline](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#5 "Create a learning pipeline")]

<span data-ttu-id="dc651-211"><xref:Microsoft.ML.Data.TextLoader> Obiektu jest pierwszą częścią potoku i ładuje dane szkoleniowe pliku.</span><span class="sxs-lookup"><span data-stu-id="dc651-211">The <xref:Microsoft.ML.Data.TextLoader> object is the first part of the pipeline, and loads the training file data.</span></span>

[!code-csharp[TextLoader](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#6 "Add a text loader to the pipeline")]

## <a name="data-preprocess-and-feature-engineering"></a><span data-ttu-id="dc651-212">Przetwarzanie wstępne danych i inżynieria</span><span class="sxs-lookup"><span data-stu-id="dc651-212">Data preprocess and feature engineering</span></span>

<span data-ttu-id="dc651-213">Przetwarzanie wstępne i czyszczenia danych są ważne zadania, które występuje, zanim będzie można skutecznie użyć zestawu danych do uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="dc651-213">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="dc651-214">Dane pierwotne jest często zakłócenia i zawodnych i może brakować wartości.</span><span class="sxs-lookup"><span data-stu-id="dc651-214">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="dc651-215">Przy użyciu danych bez tych zadań modelowania może wygenerować błędne wyniki.</span><span class="sxs-lookup"><span data-stu-id="dc651-215">Using data without these modeling tasks can produce misleading results.</span></span> <span data-ttu-id="dc651-216">ML. Potoki przekształcenia w sieci umożliwiają utworzenie niestandardowego zestawu transformacje, które są stosowane do danych przed szkolenia lub testowania.</span><span class="sxs-lookup"><span data-stu-id="dc651-216">ML.NET's transform pipelines allow you to compose a custom set of transforms that are applied to your data before training or testing.</span></span> <span data-ttu-id="dc651-217">Główny cel przekształcenia dotyczy featurization danych.</span><span class="sxs-lookup"><span data-stu-id="dc651-217">The transforms' primary purpose is for data featurization.</span></span> <span data-ttu-id="dc651-218">Potok przekształcenia korzyści jest to, że po definicji potoku przekształcania, zapisać potoku, aby zastosować go do testowania danych.</span><span class="sxs-lookup"><span data-stu-id="dc651-218">A transform pipeline's advantage is that after transform pipeline definition, save the pipeline to apply it to test data.</span></span>

<span data-ttu-id="dc651-219">Zastosuj <xref:Microsoft.ML.Transforms.TextFeaturizer> można przekonwertować `SentimentText` kolumny do [liczbowych wektor](../resources/glossary.md#numerical-feature-vector) o nazwie `Features` używane przez algorytm uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="dc651-219">Apply a <xref:Microsoft.ML.Transforms.TextFeaturizer> to convert the `SentimentText` column into a [numeric vector](../resources/glossary.md#numerical-feature-vector) called `Features` used by the machine learning algorithm.</span></span> <span data-ttu-id="dc651-220">Jest to krok przetwarzania wstępnego featurization.</span><span class="sxs-lookup"><span data-stu-id="dc651-220">This is the preprocessing/featurization step.</span></span> <span data-ttu-id="dc651-221">Przy użyciu dodatkowych składników dostępnych w ML.NET umożliwiają lepsze wyniki z modelu.</span><span class="sxs-lookup"><span data-stu-id="dc651-221">Using additional components available in ML.NET can enable better results with your model.</span></span> <span data-ttu-id="dc651-222">Dodaj `TextFeaturizer` do potoku jako następnym wierszu kodu:</span><span class="sxs-lookup"><span data-stu-id="dc651-222">Add `TextFeaturizer` to the pipeline as the next line of code:</span></span>

[!code-csharp[TextFeaturizer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#7 "Add a TextFeaturizer to the pipeline")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="dc651-223">Wybierz algorytm uczenia</span><span class="sxs-lookup"><span data-stu-id="dc651-223">Choose a learning algorithm</span></span>

<span data-ttu-id="dc651-224"><xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier> Obiekt jest uczeń drzewa decyzyjne, będzie używany w tym potoku.</span><span class="sxs-lookup"><span data-stu-id="dc651-224">The <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier> object is a decision tree learner you'll use in this pipeline.</span></span> <span data-ttu-id="dc651-225">Podobnie jak w kroku featurization wypróbować różne uczących dostępne w ML.NET i zmiany ich parametry prowadzi do różne wyniki.</span><span class="sxs-lookup"><span data-stu-id="dc651-225">Similar to the featurization step, trying out different learners available in ML.NET and changing their parameters leads to different results.</span></span> <span data-ttu-id="dc651-226">Dostrajanie, można ustawić [hyperparameters](../resources/glossary.md#hyperparameter) jak <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumTrees>, <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumLeaves>, i <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.MinDocumentsInLeafs>.</span><span class="sxs-lookup"><span data-stu-id="dc651-226">For tuning, you can set [hyperparameters](../resources/glossary.md#hyperparameter) like <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumTrees>, <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumLeaves>, and <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.MinDocumentsInLeafs>.</span></span> <span data-ttu-id="dc651-227">Te hyperparameters są ustawiane przed niczego wpływa na modelu i są specyficzne dla modelu.</span><span class="sxs-lookup"><span data-stu-id="dc651-227">These hyperparameters are set before anything affects the model and are model-specific.</span></span> <span data-ttu-id="dc651-228">Są używane do dostrajania drzewo decyzyjne dotyczące wydajności, więc większe wartości może niekorzystnie wpłynąć na wydajność.</span><span class="sxs-lookup"><span data-stu-id="dc651-228">They're used to tune the decision tree for performance, so larger values can negatively impact performance.</span></span>

<span data-ttu-id="dc651-229">Dodaj następujący kod do `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="dc651-229">Add the following code to the `Train` method:</span></span>

[!code-csharp[BinaryClassifier](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#8 "Add a fast binary tree classifier")]

## <a name="train-the-model"></a><span data-ttu-id="dc651-230">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="dc651-230">Train the model</span></span>

<span data-ttu-id="dc651-231">Nauczenia modelu, <xref:Microsoft.ML.PredictionModel%602>zgodnie zestawu danych, który został załadowany i przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="dc651-231">You train the model, <xref:Microsoft.ML.PredictionModel%602>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="dc651-232">`pipeline.Train<SentimentData, SentimentPrediction>()` przygotowuje potoku (ładuje dane, pociągu featurizer i uczeń).</span><span class="sxs-lookup"><span data-stu-id="dc651-232">`pipeline.Train<SentimentData, SentimentPrediction>()` trains the pipeline (loads the data, trains the featurizer and learner).</span></span> <span data-ttu-id="dc651-233">Eksperyment nie została wykonana, dopóki nie dzieje.</span><span class="sxs-lookup"><span data-stu-id="dc651-233">The experiment is not executed until this happens.</span></span>

<span data-ttu-id="dc651-234">Dodaj następujący kod do `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="dc651-234">Add the following code to the `Train` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#9 "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="dc651-235">Zapisz i wróć uczenia modelu do użycia na potrzeby oceny</span><span class="sxs-lookup"><span data-stu-id="dc651-235">Save and Return the model trained to use for evaluation</span></span>

<span data-ttu-id="dc651-236">W tym momencie masz modelu, który można zintegrować wszelkie istniejące lub nowe aplikacje .NET.</span><span class="sxs-lookup"><span data-stu-id="dc651-236">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="dc651-237">Aby zapisać modelu w pliku zip, przed zwróceniem, Dodaj następujący kod do następnego wiersza w `Train`:</span><span class="sxs-lookup"><span data-stu-id="dc651-237">To save your model to a .zip file before returning, add the following code to the next line in `Train`:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#10 "Save the model")]

<span data-ttu-id="dc651-238">Zwraca model na końcu `Train` metody.</span><span class="sxs-lookup"><span data-stu-id="dc651-238">Return the model at the end of the `Train` method.</span></span>

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#11 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="dc651-239">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="dc651-239">Evaluate the model</span></span>

<span data-ttu-id="dc651-240">Teraz, utworzeniu i nauczyć model, należy go obliczyć z innego zestawu danych dla jakości i sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="dc651-240">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="dc651-241">W `Evaluate` metoda, modelu, który został utworzony w `Train` jest przekazywany do obliczenia.</span><span class="sxs-lookup"><span data-stu-id="dc651-241">In the `Evaluate` method, the model created in `Train` is passed in to be evaluated.</span></span> <span data-ttu-id="dc651-242">Utwórz `Evaluate` metody tuż po `Train`, jak w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="dc651-242">Create the `Evaluate` method, just after `Train`, as in the following code:</span></span>

```csharp
public static void Evaluate(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

<span data-ttu-id="dc651-243">`Evaluate` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="dc651-243">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="dc651-244">Załadowanie zestawu danych testowych.</span><span class="sxs-lookup"><span data-stu-id="dc651-244">Loads the test dataset.</span></span>
* <span data-ttu-id="dc651-245">Tworzy ewaluatora binarnego.</span><span class="sxs-lookup"><span data-stu-id="dc651-245">Creates the binary evaluator.</span></span>
* <span data-ttu-id="dc651-246">Oblicza model oraz tworzenie metryk.</span><span class="sxs-lookup"><span data-stu-id="dc651-246">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="dc651-247">Przedstawia metryki.</span><span class="sxs-lookup"><span data-stu-id="dc651-247">Displays the metrics.</span></span>

<span data-ttu-id="dc651-248">Dodaj wywołanie do nowej metody z `Main` metoda, bezpośrednio pod `Train` wywołania metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="dc651-248">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#12 "Call the Evaluate method")]

<span data-ttu-id="dc651-249"><xref:Microsoft.ML.Data.TextLoader> Klasy ładuje nowego zestawu danych testowych z tego samego schematu.</span><span class="sxs-lookup"><span data-stu-id="dc651-249">The <xref:Microsoft.ML.Data.TextLoader> class loads the new test dataset with the same schema.</span></span> <span data-ttu-id="dc651-250">Należy ocenić modelu przy użyciu tego zestawu danych w celu sprawdzenia jakości.</span><span class="sxs-lookup"><span data-stu-id="dc651-250">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="dc651-251">Dodaj następujący kod do `Evaluate` metody:</span><span class="sxs-lookup"><span data-stu-id="dc651-251">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadText](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#13 "Load the test dataset")]

<span data-ttu-id="dc651-252"><xref:Microsoft.ML.Models.BinaryClassificationEvaluator> Obiektu oblicza metryki jakości `PredictionModel` przy użyciu określonego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="dc651-252">The <xref:Microsoft.ML.Models.BinaryClassificationEvaluator> object computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="dc651-253">Aby wyświetlić te metryki, Dodaj ewaluatora w następnym wierszu `Evaluate` metodę z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="dc651-253">To see those metrics, add the evaluator as the next line in the `Evaluate` method, with the following code:</span></span>

[!code-csharp[BinaryEvaluator](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#14 "Create the binary evaluator")]

<span data-ttu-id="dc651-254"><xref:Microsoft.ML.Models.BinaryClassificationMetrics> Zawiera ogólną metryki obliczone przez oceniających klasyfikacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="dc651-254">The <xref:Microsoft.ML.Models.BinaryClassificationMetrics> contains the overall metrics computed by binary classification evaluators.</span></span> <span data-ttu-id="dc651-255">Aby wyświetlić tych zasobów w celu określenia jakości modelu, należy uzyskać pierwszy metryki.</span><span class="sxs-lookup"><span data-stu-id="dc651-255">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="dc651-256">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="dc651-256">Add the following code:</span></span>

[!code-csharp[CreateMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#15 "Evaluate the model and create metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="dc651-257">Wyświetlanie metryki Weryfikacja modelu</span><span class="sxs-lookup"><span data-stu-id="dc651-257">Displaying the metrics for model validation</span></span>

<span data-ttu-id="dc651-258">Do wyświetlania metryk, udostępnić wyniki, a następnie działają na nich należy użyć poniższego kodu:</span><span class="sxs-lookup"><span data-stu-id="dc651-258">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#16 "Display selected metrics")]

## <a name="predict-the-test-data-outcomes-with-the-model"></a><span data-ttu-id="dc651-259">Wyniki testu danych z modelu prognozowania</span><span class="sxs-lookup"><span data-stu-id="dc651-259">Predict the test data outcomes with the model</span></span>

<span data-ttu-id="dc651-260">Utwórz `Predict` metody tuż po `Evaluate` metodę, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="dc651-260">Create the `Predict` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
public static void Predict(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

<span data-ttu-id="dc651-261">`Predict` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="dc651-261">The `Predict` method executes the following tasks:</span></span>

* <span data-ttu-id="dc651-262">Tworzy danych testowych.</span><span class="sxs-lookup"><span data-stu-id="dc651-262">Creates test data.</span></span>
* <span data-ttu-id="dc651-263">Prognozuje wskaźniki nastrojów klientów oparte na danych testowych.</span><span class="sxs-lookup"><span data-stu-id="dc651-263">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="dc651-264">Łączy testowania danych i prognoz dla raportowania.</span><span class="sxs-lookup"><span data-stu-id="dc651-264">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="dc651-265">Wyświetla wyniki przewidywane.</span><span class="sxs-lookup"><span data-stu-id="dc651-265">Displays the predicted results.</span></span>

<span data-ttu-id="dc651-266">Dodaj wywołanie do nowej metody z `Main` metoda, bezpośrednio pod `Evaluate` wywołania metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="dc651-266">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#17 "Call the Predict method")]

<span data-ttu-id="dc651-267">Dodaj niektóre komentarze do testowania prognoz uczonego modelu w `Predict` metody:</span><span class="sxs-lookup"><span data-stu-id="dc651-267">Add some comments to test the trained model's predictions in the `Predict` method:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#18 "Create test data for predictions")]

<span data-ttu-id="dc651-268">Teraz, gdy masz modelu należy go używać, aby przewidzieć dodatnie lub ujemne wskaźniki nastrojów klientów użycia danych komentarz <xref:Microsoft.ML.PredictionModel.Predict%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="dc651-268">Now that you have a model, you can use that to predict the positive or negative sentiment of the comment data using the <xref:Microsoft.ML.PredictionModel.Predict%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="dc651-269">Aby uzyskać prognozowania, należy użyć `Predict` na nowych danych.</span><span class="sxs-lookup"><span data-stu-id="dc651-269">To get a prediction, use `Predict` on new data.</span></span> <span data-ttu-id="dc651-270">Należy pamiętać, że danych wejściowych jest ciągiem i model zawiera featurization.</span><span class="sxs-lookup"><span data-stu-id="dc651-270">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="dc651-271">Potoku sieci jest w synchronizacji podczas uczenia i prognozowania.</span><span class="sxs-lookup"><span data-stu-id="dc651-271">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="dc651-272">Nie trzeba napisać kod przetwarzania wstępnego featurization specjalnie z myślą o prognoz i tego samego interfejsu API zajmuje się zarówno partii i jednorazowego prognoz.</span><span class="sxs-lookup"><span data-stu-id="dc651-272">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#19 "Create predictions of sentiments")]

### <a name="model-operationalization-prediction"></a><span data-ttu-id="dc651-273">Model operationalization: prognozowania</span><span class="sxs-lookup"><span data-stu-id="dc651-273">Model operationalization: prediction</span></span>

<span data-ttu-id="dc651-274">Wyświetl `SentimentText` oraz odpowiednie wskaźniki nastrojów klientów prognozowania celu mają wyniki i odpowiednio działają na nich.</span><span class="sxs-lookup"><span data-stu-id="dc651-274">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="dc651-275">Jest to operationalization używanie zwrócone dane jako części zasady operacyjne.</span><span class="sxs-lookup"><span data-stu-id="dc651-275">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="dc651-276">Utwórz nagłówek dla wyników z następującym <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:</span><span class="sxs-lookup"><span data-stu-id="dc651-276">Create a header for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#20 "Display prediction outputs")]

<span data-ttu-id="dc651-277">Przed wyświetleniem wyniki przewidywane, łączyć wskaźniki nastrojów klientów i prognozowanie ze sobą, aby wyświetlić oryginalne komentarz z jego przewidywane wskaźniki nastrojów klientów.</span><span class="sxs-lookup"><span data-stu-id="dc651-277">Before displaying the predicted results, combine the sentiment and prediction together to see the original comment with its predicted sentiment.</span></span> <span data-ttu-id="dc651-278">Poniższy kod używa <xref:System.Linq.Enumerable.Zip%2A> metodę, aby to zrobić, a więc Dodaj ten kod obok:</span><span class="sxs-lookup"><span data-stu-id="dc651-278">The following code uses the <xref:System.Linq.Enumerable.Zip%2A> method to make that happen, so add that code next:</span></span>

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#21 "Build the pairs of sentiment data and predictions")]

<span data-ttu-id="dc651-279">Teraz, po połączeniu `SentimentText` i `Sentiment` do klasy, można wyświetlić wyniki za pomocą <xref:System.Console.WriteLine?displayProperty=nameWithType> metody:</span><span class="sxs-lookup"><span data-stu-id="dc651-279">Now that you've combined the `SentimentText` and `Sentiment` into a class, you can display the results using the <xref:System.Console.WriteLine?displayProperty=nameWithType> method:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#22 "Display the predictions")]

<span data-ttu-id="dc651-280">Ponieważ wywnioskować nazwy elementu krotki to 7.0 C# jest nową funkcją w C# 7.1 i wersję językową domyślny projekt, musisz zmienić wersję języka C# 7.1 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="dc651-280">Because inferred tuple element names are a new feature in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span>
<span data-ttu-id="dc651-281">W tym celu kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="dc651-281">To do that, right-click on the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="dc651-282">Wybierz **kompilacji** i wybierz **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="dc651-282">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="dc651-283">Na liście rozwijanej wybierz **C# 7.1** (lub nowszej wersji).</span><span class="sxs-lookup"><span data-stu-id="dc651-283">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="dc651-284">Wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="dc651-284">Select the **OK** button.</span></span>

## <a name="results"></a><span data-ttu-id="dc651-285">Wyniki</span><span class="sxs-lookup"><span data-stu-id="dc651-285">Results</span></span>

<span data-ttu-id="dc651-286">Wyniki powinny być podobne do następującego.</span><span class="sxs-lookup"><span data-stu-id="dc651-286">Your results should be similar to the following.</span></span> <span data-ttu-id="dc651-287">Jak przetwarza potoku, wyświetla komunikaty.</span><span class="sxs-lookup"><span data-stu-id="dc651-287">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="dc651-288">Mogą pojawić się ostrzeżenia lub komunikaty przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="dc651-288">You may see warnings, or processing messages.</span></span> <span data-ttu-id="dc651-289">Te zostały usunięte z następującymi wynikami dla uzyskania przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="dc651-289">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="dc651-290">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="dc651-290">Congratulations!</span></span> <span data-ttu-id="dc651-291">Teraz został pomyślnie skompilowany modelu uczenia maszynowego, klasyfikowania i prognozowanie wiadomości wskaźniki nastrojów klientów.</span><span class="sxs-lookup"><span data-stu-id="dc651-291">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span> <span data-ttu-id="dc651-292">Kod źródłowy można znaleźć w tym samouczku w [dotnet/przykłady](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="dc651-292">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="dc651-293">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="dc651-293">Next steps</span></span>

<span data-ttu-id="dc651-294">W tym samouczku przedstawiono sposób:</span><span class="sxs-lookup"><span data-stu-id="dc651-294">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="dc651-295">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="dc651-295">Understand the problem</span></span>
> * <span data-ttu-id="dc651-296">Wybierz zadanie learning odpowiednie maszyny</span><span class="sxs-lookup"><span data-stu-id="dc651-296">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="dc651-297">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="dc651-297">Prepare your data</span></span>
> * <span data-ttu-id="dc651-298">Tworzenie potoku learning</span><span class="sxs-lookup"><span data-stu-id="dc651-298">Create the learning pipeline</span></span>
> * <span data-ttu-id="dc651-299">Klasyfikator obciążenia</span><span class="sxs-lookup"><span data-stu-id="dc651-299">Load a classifier</span></span>
> * <span data-ttu-id="dc651-300">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="dc651-300">Train the model</span></span>
> * <span data-ttu-id="dc651-301">Ocena modelu z innego zestawu danych</span><span class="sxs-lookup"><span data-stu-id="dc651-301">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="dc651-302">Wyniki testu danych z modelu prognozowania</span><span class="sxs-lookup"><span data-stu-id="dc651-302">Predict the test data outcomes with the model</span></span>

<span data-ttu-id="dc651-303">Przejdź do następnego samouczkiem, aby dowiedzieć się więcej</span><span class="sxs-lookup"><span data-stu-id="dc651-303">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="dc651-304">Prognoza taryfy taksówki</span><span class="sxs-lookup"><span data-stu-id="dc651-304">Taxi Fare Predictor</span></span>](taxi-fare.md)
