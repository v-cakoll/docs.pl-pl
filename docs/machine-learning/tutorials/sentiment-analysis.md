---
title: Użyj strukturze ML.NET w scenariuszu klasyfikacji binarnej analizy tonacji
description: Dowiedz się, jak używać strukturze ML.NET w scenariuszu klasyfikacji binarnej zrozumienie, jak na potrzeby prognozowania tonacji podjąć odpowiednie działania.
ms.date: 03/07/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: a88ed38b76a230095f35304aa2b52af0a7c9c22d
ms.sourcegitcommit: 77854e8704b9689b73103d691db34d71c2bf1dad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2019
ms.locfileid: "58307944"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a><span data-ttu-id="9b696-103">Samouczek: Użyj strukturze ML.NET w scenariuszu klasyfikacji binarnej analizy tonacji</span><span class="sxs-lookup"><span data-stu-id="9b696-103">Tutorial: Use ML.NET in a sentiment analysis binary classification scenario</span></span>

<span data-ttu-id="9b696-104">Ten przykładowy samouczek przedstawia tworzenie klasyfikatora opinii do prognozowania dodatnie lub ujemne wskaźniki nastrojów klientów za pośrednictwem używany aplikację konsoli .NET Core przy użyciu strukturze ML.NET C# w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="9b696-104">This sample tutorial illustrates using ML.NET to create a sentiment classifier to predict either positive or negative sentiment via a .NET Core console application using C# in Visual Studio 2017.</span></span> <span data-ttu-id="9b696-105">W środowisku usługi machine learning tego rodzaju prognozowania nosi nazwę klasyfikacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="9b696-105">In the world of machine learning, this type of prediction is known as binary classification.</span></span>

> [!NOTE]
> <span data-ttu-id="9b696-106">W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="9b696-106">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="9b696-107">Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="9b696-107">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="9b696-108">Obecnie używasz tego samouczka, a powiązane próbki **strukturze ML.NET wersji 0,11**.</span><span class="sxs-lookup"><span data-stu-id="9b696-108">This tutorial and related sample are currently using **ML.NET version 0.11**.</span></span> <span data-ttu-id="9b696-109">Aby uzyskać więcej informacji, zobacz informacje o wersji w [dotnet/machinelearning repozytorium GitHub](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)</span><span class="sxs-lookup"><span data-stu-id="9b696-109">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)</span></span>

<span data-ttu-id="9b696-110">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="9b696-110">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="9b696-111">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="9b696-111">Understand the problem</span></span>
> * <span data-ttu-id="9b696-112">Wybieranie algorytmu uczenia maszynowego odpowiednie</span><span class="sxs-lookup"><span data-stu-id="9b696-112">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="9b696-113">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="9b696-113">Prepare your data</span></span>
> * <span data-ttu-id="9b696-114">Przekształcanie danych</span><span class="sxs-lookup"><span data-stu-id="9b696-114">Transform the data</span></span>
> * <span data-ttu-id="9b696-115">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="9b696-115">Train the model</span></span>
> * <span data-ttu-id="9b696-116">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="9b696-116">Evaluate the model</span></span>
> * <span data-ttu-id="9b696-117">Prognozowanie za pomocą uczonego modelu</span><span class="sxs-lookup"><span data-stu-id="9b696-117">Predict with the trained model</span></span>
> * <span data-ttu-id="9b696-118">Wdrażanie i przewidywanie załadować modelu</span><span class="sxs-lookup"><span data-stu-id="9b696-118">Deploy and Predict with a loaded model</span></span>

## <a name="sentiment-analysis-sample-overview"></a><span data-ttu-id="9b696-119">Omówienie przykładowych analizy tonacji</span><span class="sxs-lookup"><span data-stu-id="9b696-119">Sentiment analysis sample overview</span></span>

<span data-ttu-id="9b696-120">Próbka jest aplikacją konsoli, która używa strukturze ML.NET do nauczenia modelu, która klasyfikuje i przewiduje wskaźniki nastrojów klientów, jak dodatnie lub ujemne.</span><span class="sxs-lookup"><span data-stu-id="9b696-120">The sample is a console app that uses ML.NET to train a model that classifies and predicts sentiment as either positive or negative.</span></span> <span data-ttu-id="9b696-121">Zestaw danych tonacji Yelp pochodzi z uniwersytet kalifornijski-Irvine (UCI), która zostanie podzielona na szkolenie zestaw danych i zestawy danych testowych.</span><span class="sxs-lookup"><span data-stu-id="9b696-121">The Yelp sentiment dataset is from University of California, Irvine (UCI), which is split into a train dataset and a test dataset.</span></span> <span data-ttu-id="9b696-122">Przykład oblicza model z zestawu danych testowych do analizy jakości dostawców.</span><span class="sxs-lookup"><span data-stu-id="9b696-122">The sample evaluates the model with the test dataset for quality analysis.</span></span> 

<span data-ttu-id="9b696-123">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="9b696-123">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9b696-124">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="9b696-124">Prerequisites</span></span>

* <span data-ttu-id="9b696-125">[Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".</span><span class="sxs-lookup"><span data-stu-id="9b696-125">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* [<span data-ttu-id="9b696-126">Plik zip zdania etykietą tonacji na zestaw danych</span><span class="sxs-lookup"><span data-stu-id="9b696-126">The UCI Sentiment Labeled Sentences dataset zip file</span></span>](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)

## <a name="machine-learning-workflow"></a><span data-ttu-id="9b696-127">Maszyny uczenie się przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9b696-127">Machine learning workflow</span></span>

<span data-ttu-id="9b696-128">W tym samouczku poniżej przepływu pracy, który umożliwia proces przenoszenia w sposób uporządkowany uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="9b696-128">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="9b696-129">Fazy przepływu pracy są następujące:</span><span class="sxs-lookup"><span data-stu-id="9b696-129">The workflow phases are as follows:</span></span>

1. <span data-ttu-id="9b696-130">**Omówienie problemu**</span><span class="sxs-lookup"><span data-stu-id="9b696-130">**Understand the problem**</span></span>
2. <span data-ttu-id="9b696-131">**Przygotowywanie danych**</span><span class="sxs-lookup"><span data-stu-id="9b696-131">**Prepare your data**</span></span>
   * <span data-ttu-id="9b696-132">**Ładowanie danych**</span><span class="sxs-lookup"><span data-stu-id="9b696-132">**Load the data**</span></span>
   * <span data-ttu-id="9b696-133">**Wyodrębnianie funkcji (przekształcania danych)**</span><span class="sxs-lookup"><span data-stu-id="9b696-133">**Extract features (Transform your data)**</span></span>
3. <span data-ttu-id="9b696-134">**Kompilowanie i szkolenie**</span><span class="sxs-lookup"><span data-stu-id="9b696-134">**Build and train**</span></span> 
   * <span data-ttu-id="9b696-135">**Uczenie modelu**</span><span class="sxs-lookup"><span data-stu-id="9b696-135">**Train the model**</span></span>
   * <span data-ttu-id="9b696-136">**Ocena modelu**</span><span class="sxs-lookup"><span data-stu-id="9b696-136">**Evaluate the model**</span></span>
4. <span data-ttu-id="9b696-137">**Wdrażanie modelu**</span><span class="sxs-lookup"><span data-stu-id="9b696-137">**Deploy Model**</span></span>
   * <span data-ttu-id="9b696-138">**Użyj modelu do prognozowania**</span><span class="sxs-lookup"><span data-stu-id="9b696-138">**Use the Model to predict**</span></span>

### <a name="understand-the-problem"></a><span data-ttu-id="9b696-139">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="9b696-139">Understand the problem</span></span>

<span data-ttu-id="9b696-140">Należy najpierw zrozumieć, dzięki czemu można podzielić je w dół do części obsługujące kompilowanie i uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="9b696-140">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="9b696-141">Potężne problem umożliwia prognozowanie i ocena wyników.</span><span class="sxs-lookup"><span data-stu-id="9b696-141">Breaking the problem down allows you to predict and evaluate the results.</span></span>

<span data-ttu-id="9b696-142">Ten problem, w tym samouczku jest zrozumienie, przychodzące tonacji komentarz witryny sieci Web podejmowanie odpowiednich działań.</span><span class="sxs-lookup"><span data-stu-id="9b696-142">The problem for this tutorial is to understand incoming website comment sentiment to take the appropriate action.</span></span>

<span data-ttu-id="9b696-143">Ten problem można podzielić do tonacji tekstu i wartości tonacji danych mają do nauczenia modelu, z, a wartości tonacji przewidywane, można obliczyć, a następnie za pomocą pod względem.</span><span class="sxs-lookup"><span data-stu-id="9b696-143">You can break down the problem to the sentiment text and sentiment value for the data you want to train the model with, and a predicted sentiment value that you can evaluate and then use operationally.</span></span>

<span data-ttu-id="9b696-144">Następnie należy **określić** tonacji, która ułatwia wybieranie zadań uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="9b696-144">You then need to **determine** the sentiment, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-algorithm"></a><span data-ttu-id="9b696-145">Wybieranie algorytmu uczenia maszynowego odpowiednie</span><span class="sxs-lookup"><span data-stu-id="9b696-145">Select the appropriate machine learning algorithm</span></span>

<span data-ttu-id="9b696-146">W rozwiązaniu tego problemu znasz następujące fakty:</span><span class="sxs-lookup"><span data-stu-id="9b696-146">With this problem, you know the following facts:</span></span>

<span data-ttu-id="9b696-147">Szkolenie danych: komentarze witryny sieci Web może być liczbą dodatnią (1) lub fałszywie ujemny (0) (**tonacji**).</span><span class="sxs-lookup"><span data-stu-id="9b696-147">Training data: website comments can be positive (1) or negative (0) (**sentiment**).</span></span>

<span data-ttu-id="9b696-148">Przewidywanie **tonacji** nowego komentarza witryny sieci Web, dodatnie lub ujemne, takie jak w następujących przykładach:</span><span class="sxs-lookup"><span data-stu-id="9b696-148">Predict the **sentiment** of a new website comment, either positive or negative, such as in the following examples:</span></span>

* <span data-ttu-id="9b696-149">Uwielbiam kelnerów w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="9b696-149">I love the wait staff here.</span></span> <span data-ttu-id="9b696-150">One dzieła.</span><span class="sxs-lookup"><span data-stu-id="9b696-150">They rock.</span></span>
* <span data-ttu-id="9b696-151">To miejsce ma najgorszy od początku.</span><span class="sxs-lookup"><span data-stu-id="9b696-151">This place has the worst soup.</span></span>

<span data-ttu-id="9b696-152">Algorytmu uczenia maszynowego klasyfikacji najlepiej nadaje się dla tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="9b696-152">The classification machine learning algorithm is best suited for this scenario.</span></span>

### <a name="about-the-classification-algorithm"></a><span data-ttu-id="9b696-153">Temat algorytm klasyfikacji</span><span class="sxs-lookup"><span data-stu-id="9b696-153">About the classification algorithm</span></span>

<span data-ttu-id="9b696-154">Klasyfikacja jest algorytm uczenia maszynowego, która korzysta z danych do **określić** kategorii, typ lub klasa elementu lub wiersza danych.</span><span class="sxs-lookup"><span data-stu-id="9b696-154">Classification is a machine learning algorithm that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="9b696-155">Na przykład można użyć klasyfikacji:</span><span class="sxs-lookup"><span data-stu-id="9b696-155">For example, you can use classification to:</span></span>

* <span data-ttu-id="9b696-156">Zidentyfikuj tonacji jako dodatnia lub ujemna.</span><span class="sxs-lookup"><span data-stu-id="9b696-156">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="9b696-157">Klasyfikowanie wiadomości e-mail jako spam, wiadomości-śmieci lub właściwej.</span><span class="sxs-lookup"><span data-stu-id="9b696-157">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="9b696-158">Ustal, czy pacjent laboratorium przykładowe dane stanowią cancerous.</span><span class="sxs-lookup"><span data-stu-id="9b696-158">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="9b696-159">Klienci na kategorie według ich tendencje do odpowiedzi na kampanię sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="9b696-159">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="9b696-160">Algorytmy klasyfikacji są często jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="9b696-160">Classification algorithms are frequently one of the following types:</span></span>

* <span data-ttu-id="9b696-161">Plik binarny: A i B.</span><span class="sxs-lookup"><span data-stu-id="9b696-161">Binary: either A or B.</span></span>
* <span data-ttu-id="9b696-162">Kontra: wielu kategorii, które można przewidzieć przy użyciu pojedynczego modelu.</span><span class="sxs-lookup"><span data-stu-id="9b696-162">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="9b696-163">Ponieważ komentarze witryny sieci Web muszą być klasyfikowane jako dodatnie lub ujemne, użycie algorytmu klasyfikacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="9b696-163">Because the website comments need to be classified as either positive or negative, you use the Binary Classification algorithm.</span></span> 

## <a name="create-a-console-application"></a><span data-ttu-id="9b696-164">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="9b696-164">Create a console application</span></span>

1. <span data-ttu-id="9b696-165">Otwórz program Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="9b696-165">Open Visual Studio 2017.</span></span> <span data-ttu-id="9b696-166">Wybierz **pliku** > **New** > **projektu** z paska menu.</span><span class="sxs-lookup"><span data-stu-id="9b696-166">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="9b696-167">W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła następuje **platformy .NET Core** węzła.</span><span class="sxs-lookup"><span data-stu-id="9b696-167">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="9b696-168">Następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="9b696-168">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="9b696-169">W **nazwa** pole tekstowe, wpisz "SentimentAnalysis", a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9b696-169">In the **Name** text box, type "SentimentAnalysis" and then select the **OK** button.</span></span>

2. <span data-ttu-id="9b696-170">Utwórz katalog o nazwie *danych* w projekcie, aby zapisać pliki zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="9b696-170">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="9b696-171">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nad projektem i wybierz **Dodaj** > **nowy Folder**.</span><span class="sxs-lookup"><span data-stu-id="9b696-171">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="9b696-172">Wpisz "Dane", a następnie naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="9b696-172">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="9b696-173">Zainstaluj **pakietu NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="9b696-173">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="9b696-174">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="9b696-174">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="9b696-175">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9b696-175">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="9b696-176">Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.</span><span class="sxs-lookup"><span data-stu-id="9b696-176">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="9b696-177">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="9b696-177">Prepare your data</span></span>

1. <span data-ttu-id="9b696-178">Pobierz [pliku zip zestawu danych na wskaźniki nastrojów klientów etykietą zdań (patrz cytaty poniżej)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)i Rozpakuj go.</span><span class="sxs-lookup"><span data-stu-id="9b696-178">Download [The UCI Sentiment Labeled Sentences dataset zip file (see citations in the following note)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="9b696-179">Kopiuj `yelp_labelled.txt` mezzanine do *danych* katalog został utworzony.</span><span class="sxs-lookup"><span data-stu-id="9b696-179">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

> [!NOTE]
> <span data-ttu-id="9b696-180">Zestawy danych, w tym samouczku są z "From grupy do poszczególnych etykiet korzystanie z funkcji głębokiego" Kotzias et.</span><span class="sxs-lookup"><span data-stu-id="9b696-180">The datasets this tutorial uses are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="9b696-181">Al.</span><span class="sxs-lookup"><span data-stu-id="9b696-181">al,.</span></span> <span data-ttu-id="9b696-182">KDD 2015 i hostowanej na Machine Learning repozytorium — Dua, D. i Karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="9b696-182">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="9b696-183">UCI usługi Machine Learning repozytorium [http://archive.ics.uci.edu/ml].</span><span class="sxs-lookup"><span data-stu-id="9b696-183">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="9b696-184">Irvine, CA: Uniwersytet kalifornijski School informacji i informatyki.</span><span class="sxs-lookup"><span data-stu-id="9b696-184">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

3. <span data-ttu-id="9b696-185">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy `yelp_labeled.txt` plik i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="9b696-185">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="9b696-186">W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="9b696-186">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="9b696-187">Tworzenie klas i definiowania ścieżek</span><span class="sxs-lookup"><span data-stu-id="9b696-187">Create classes and define paths</span></span>

<span data-ttu-id="9b696-188">Dodaj następujące dodatkowe `using` instrukcji na górze *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="9b696-188">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

<span data-ttu-id="9b696-189">Należy utworzyć dwa pola globalnego na potrzeby przechowywania ostatnio pobrane dataset ścieżkę pliku i ścieżka pliku zapisanego modelu:</span><span class="sxs-lookup"><span data-stu-id="9b696-189">You need to create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

* <span data-ttu-id="9b696-190">`_dataPath` zawiera ścieżkę do zestawu danych, używane do trenowania modelu.</span><span class="sxs-lookup"><span data-stu-id="9b696-190">`_dataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="9b696-191">`_modelPath` ma ścieżkę, w którym jest zapisany trenowanego modelu.</span><span class="sxs-lookup"><span data-stu-id="9b696-191">`_modelPath` has the path where the trained model is saved.</span></span>

<span data-ttu-id="9b696-192">Dodaj następujący kod po prawej stronie wiersza powyżej `Main` metodę, aby określić tych ścieżek:</span><span class="sxs-lookup"><span data-stu-id="9b696-192">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Declare global variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

<span data-ttu-id="9b696-193">Musisz utworzyć niektóre klasy dla danych wejściowych i prognozy.</span><span class="sxs-lookup"><span data-stu-id="9b696-193">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="9b696-194">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="9b696-194">Add a new class to your project:</span></span>

1. <span data-ttu-id="9b696-195">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="9b696-195">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="9b696-196">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="9b696-196">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="9b696-197">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9b696-197">Then, select the **Add** button.</span></span>

    <span data-ttu-id="9b696-198">*SentimentData.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="9b696-198">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="9b696-199">Dodaj następujący kod `using` instrukcji na górze *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="9b696-199">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

<span data-ttu-id="9b696-200">Usuń istniejącą definicję klasy i Dodaj następujący kod, który zawiera dwie klasy `SentimentData` i `SentimentPrediction`, *SentimentData.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="9b696-200">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

<span data-ttu-id="9b696-201">Klasa wejściowy zestaw danych `SentimentData`, ma `string` dla komentarza (`SentimentText`) i `bool` (`Sentiment`) z wartością dla tonacji dodatnia lub ujemna.</span><span class="sxs-lookup"><span data-stu-id="9b696-201">The input dataset class, `SentimentData`, has a `string` for the comment (`SentimentText`) and a `bool` (`Sentiment`) that has a value for sentiment of either positive or negative.</span></span> <span data-ttu-id="9b696-202">Oba pola mają <xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29> atrybuty dołączonych do nich.</span><span class="sxs-lookup"><span data-stu-id="9b696-202">Both fields have <xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29> attributes attached to them.</span></span> <span data-ttu-id="9b696-203">Ten atrybut wykonywania działań Opisuje kolejność każdego pola w pliku danych.</span><span class="sxs-lookup"><span data-stu-id="9b696-203">This attribute describes the order of each field in the data file.</span></span>  <span data-ttu-id="9b696-204">Ponadto `Sentiment` właściwość ma <xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A> do wyznaczenia jako `Label` pola.</span><span class="sxs-lookup"><span data-stu-id="9b696-204">In addition, the `Sentiment` property has a <xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A> to designate it as the `Label` field.</span></span> <span data-ttu-id="9b696-205">`SentimentPrediction` Klasa służy do prognozowania po wyszkoliła modelu.</span><span class="sxs-lookup"><span data-stu-id="9b696-205">`SentimentPrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="9b696-206">Ma ona pojedynczy atrybut typu wartość logiczna (`Sentiment`) i `PredictedLabel` `ColumnName` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="9b696-206">It has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="9b696-207">`Label` Umożliwia tworzenie i uczenie modelu, a także używane z Podziel się z zestawu danych testowych do ewaluacji modelu.</span><span class="sxs-lookup"><span data-stu-id="9b696-207">The `Label` is used to create and train the model, and it's also used with the split out test dataset to evaluate the model.</span></span> <span data-ttu-id="9b696-208">`PredictedLabel` Używany podczas prognoz i oceny.</span><span class="sxs-lookup"><span data-stu-id="9b696-208">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="9b696-209">W wersji ewaluacyjnej używane są dane szkoleniowe, przewidywane wartości i model danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="9b696-209">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="9b696-210">Podczas tworzenia modelu za pomocą platformy ML.NET rozpoczyna się od utworzenia <xref:Microsoft.ML.MLContext>.</span><span class="sxs-lookup"><span data-stu-id="9b696-210">When building a model with ML.NET you start by creating an <xref:Microsoft.ML.MLContext>.</span></span> <span data-ttu-id="9b696-211">`MLContext` można porównywać pod względem koncepcyjnym do korzystania z `DbContext` platformy Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="9b696-211">`MLContext` is comparable conceptually to using `DbContext` in Entity Framework.</span></span> <span data-ttu-id="9b696-212">Środowisko dostarcza kontekst dla zadania uczenia Maszynowego, który może służyć do wyjątku, śledzenie i rejestrowanie.</span><span class="sxs-lookup"><span data-stu-id="9b696-212">The environment provides a context for your ML job that can be used for exception tracking and logging.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="9b696-213">Inicjowanie zmiennych w głównym oknie</span><span class="sxs-lookup"><span data-stu-id="9b696-213">Initialize variables in Main</span></span>

<span data-ttu-id="9b696-214">Utwórz zmienną o nazwie `mlContext` i zainicjuj ją o nowe wystąpienie klasy `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="9b696-214">Create a variable called `mlContext` and initialize it with a new instance of `MLContext`.</span></span>  <span data-ttu-id="9b696-215">Zastąp `Console.WriteLine("Hello World!")` wiersz poniższym kodem w `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="9b696-215">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

<span data-ttu-id="9b696-216">Dodaj następujący kod jako następnego wiersza kodu w `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="9b696-216">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallLoadData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

<span data-ttu-id="9b696-217">`LoadData` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="9b696-217">The `LoadData` method executes the following tasks:</span></span>

* <span data-ttu-id="9b696-218">Służy do ładowania danych.</span><span class="sxs-lookup"><span data-stu-id="9b696-218">Loads the data.</span></span>
* <span data-ttu-id="9b696-219">Dzieli załadowanego zestawu danych na szkolenie i testowanie zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="9b696-219">Splits the loaded dataset into train and test datasets.</span></span>
* <span data-ttu-id="9b696-220">Zwraca podziału nauczenia i przetestowania zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="9b696-220">Returns the split train and test datasets.</span></span>

<span data-ttu-id="9b696-221">Tworzenie `LoadData` metody tuż za `Main` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="9b696-221">Create the `LoadData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static TrainCatalogBase.TrainTestData LoadData(MLContext mlContext)
{

}
```
## <a name="load-the-data"></a><span data-ttu-id="9b696-222">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="9b696-222">Load the data</span></span>

<span data-ttu-id="9b696-223">Ponieważ utworzone wcześniej `SentimentData` typ modelu danych jest zgodny schemat zestawu danych, inicjowanie, mapowanie i ładowanie na jeden wiersz kodu za pomocą zestawu danych można łączyć `MLContext.Data.LoadFromTextFile` otoki dla [metoda LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29).</span><span class="sxs-lookup"><span data-stu-id="9b696-223">Since your previously created `SentimentData` data model type matches the dataset schema, you can combine the initialization, mapping, and dataset loading into one line of code using the `MLContext.Data.LoadFromTextFile` wrapper for the [LoadFromTextFile method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29).</span></span> <span data-ttu-id="9b696-224">Zwraca <xref:Microsoft.Data.DataView.IDataView>.</span><span class="sxs-lookup"><span data-stu-id="9b696-224">It returns a <xref:Microsoft.Data.DataView.IDataView>.</span></span> 

 <span data-ttu-id="9b696-225">Jako dane wejściowe i wyjściowe `Transforms`, `DataView` jest typem potoku danych podstawowych porównywalne do `IEnumerable` dla `LINQ`.</span><span class="sxs-lookup"><span data-stu-id="9b696-225">As the input and output of `Transforms`, a `DataView` is the fundamental data pipeline type, comparable to `IEnumerable` for `LINQ`.</span></span>

<span data-ttu-id="9b696-226">W strukturze ML.NET dane są podobne do widoku SQL.</span><span class="sxs-lookup"><span data-stu-id="9b696-226">In ML.NET, data is similar to a SQL view.</span></span> <span data-ttu-id="9b696-227">Jest opóźnieniem ocenianą informatycznych i heterogenicznych.</span><span class="sxs-lookup"><span data-stu-id="9b696-227">It is lazily evaluated, schematized, and heterogenous.</span></span> <span data-ttu-id="9b696-228">Obiekt jest pierwszą częścią potoku i służy do ładowania danych.</span><span class="sxs-lookup"><span data-stu-id="9b696-228">The object is the first part of the pipeline, and loads the data.</span></span> <span data-ttu-id="9b696-229">W tym samouczku ładuje zestaw danych o komentarze i odpowiednie toksyczne lub inne niż toksyczne tonacji.</span><span class="sxs-lookup"><span data-stu-id="9b696-229">For this tutorial, it loads a dataset with comments and corresponding toxic or non toxic sentiment.</span></span> <span data-ttu-id="9b696-230">Służy do tworzenia modelu i szkoleń.</span><span class="sxs-lookup"><span data-stu-id="9b696-230">This is used to create the model, and train it.</span></span>

 <span data-ttu-id="9b696-231">Dodaj następujący kod jako pierwsza linia `LoadData` metody:</span><span class="sxs-lookup"><span data-stu-id="9b696-231">Add the following code as the first line of the `LoadData` method:</span></span>

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="9b696-232">Podziel zestaw danych dla modelu, szkolenia i testowania</span><span class="sxs-lookup"><span data-stu-id="9b696-232">Split the dataset for model training and testing</span></span>

<span data-ttu-id="9b696-233">Następnie należy zarówno zestaw danych szkoleniowych do nauczenia modelu, jak i zestawy danych testowych do ewaluacji modelu.</span><span class="sxs-lookup"><span data-stu-id="9b696-233">Next, you need both a training dataset to train the model and a test dataset to evaluate the model.</span></span> <span data-ttu-id="9b696-234">Użyj `MLContext.BinaryClassification.TrainTestSplit` który opakowuje <xref:Microsoft.ML.StaticPipe.TrainingStaticExtensions.TrainTestSplit%2A> Podziel załadowanego zestawu danych na szkolenie i testowanie zestawy danych i zwrócić wewnątrz <xref:Microsoft.ML.TrainCatalogBase.TrainTestData>.</span><span class="sxs-lookup"><span data-stu-id="9b696-234">Use the `MLContext.BinaryClassification.TrainTestSplit` which wraps <xref:Microsoft.ML.StaticPipe.TrainingStaticExtensions.TrainTestSplit%2A> to split the loaded dataset into train and test datasets and return them inside of a <xref:Microsoft.ML.TrainCatalogBase.TrainTestData>.</span></span> <span data-ttu-id="9b696-235">Zestaw testów przy użyciu część danych można określić `testFraction`parametru.</span><span class="sxs-lookup"><span data-stu-id="9b696-235">You can specify the fraction of data for the test set with the `testFraction`parameter.</span></span> <span data-ttu-id="9b696-236">Wartość domyślna wynosi 10%, ale w tym przypadku użyj 20% do użycia większej ilości danych do celów oceny.</span><span class="sxs-lookup"><span data-stu-id="9b696-236">The default is 10% but you use 20% in this case to use more data for the evaluation.</span></span>  

<span data-ttu-id="9b696-237">Aby podzielić dane załadowane do wymaganych zestawów danych, Dodaj następujący kod w następnym wierszu `LoadData` metody:</span><span class="sxs-lookup"><span data-stu-id="9b696-237">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData` method:</span></span>

[!code-csharp[SplitData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

<span data-ttu-id="9b696-238">Zwróć `splitDataView` na końcu `LoadData` metody:</span><span class="sxs-lookup"><span data-stu-id="9b696-238">Return the `splitDataView` at the end of the `LoadData` method:</span></span>

[!code-csharp[ReturnSplitData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="9b696-239">Tworzenie i trenowanie modelu</span><span class="sxs-lookup"><span data-stu-id="9b696-239">Build and train the model</span></span>

<span data-ttu-id="9b696-240">Dodaj następujące wywołanie do `BuildAndTrainModel`metodę jako następnego wiersza kodu w `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="9b696-240">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="9b696-241">`BuildAndTrainModel` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="9b696-241">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="9b696-242">Wyodrębnia i przekształca dane.</span><span class="sxs-lookup"><span data-stu-id="9b696-242">Extracts and transforms the data.</span></span>
* <span data-ttu-id="9b696-243">Szkolenie modeli modelu.</span><span class="sxs-lookup"><span data-stu-id="9b696-243">Trains the model.</span></span>
* <span data-ttu-id="9b696-244">Prognozuje tonacji na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="9b696-244">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="9b696-245">Zwraca wartość modelu.</span><span class="sxs-lookup"><span data-stu-id="9b696-245">Returns the model.</span></span>

<span data-ttu-id="9b696-246">Tworzenie `BuildAndTrainModel` metody tuż za `Main` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="9b696-246">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
{

}
```

<span data-ttu-id="9b696-247">Należy zauważyć, że dwa parametry są przekazywane do metody Train; `MLContext` kontekstu (`mlContext`), a `IDataView`dla zestawu danych szkoleniowych (`splitTrainSet`).</span><span class="sxs-lookup"><span data-stu-id="9b696-247">Notice that two parameters are passed into the Train method; a `MLContext` for the context (`mlContext`), and an `IDataView`for the training dataset (`splitTrainSet`).</span></span> 

## <a name="extract-and-transform-the-data"></a><span data-ttu-id="9b696-248">Wyodrębnianie i przekształcania danych</span><span class="sxs-lookup"><span data-stu-id="9b696-248">Extract and transform the data</span></span>

<span data-ttu-id="9b696-249">Wstępne przetwarzanie i czyszczenie danych są ważne zadania, które występują przed zestaw danych jest efektywnie używać uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="9b696-249">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="9b696-250">Nieprzetworzone dane są często hałas i zawodnych i może brakować wartości.</span><span class="sxs-lookup"><span data-stu-id="9b696-250">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="9b696-251">Korzystanie z danych bez tych zadań modelowania może spowodować wyświetlenie nieprawdziwych wyników.</span><span class="sxs-lookup"><span data-stu-id="9b696-251">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="9b696-252">UCZENIE MASZYNOWE. Potoki przekształcenie firmy NET tworzą zbiór niestandardowych przekształceń, które są stosowane do danych przed szkolenie i testowanie.</span><span class="sxs-lookup"><span data-stu-id="9b696-252">ML.NET's transform pipelines compose a custom set of transforms that are applied to your data before training or testing.</span></span> <span data-ttu-id="9b696-253">Przekształcenia głównym celem jest danych [cechowania](../resources/glossary.md#feature-engineering).</span><span class="sxs-lookup"><span data-stu-id="9b696-253">The transforms' primary purpose is data [featurization](../resources/glossary.md#feature-engineering).</span></span> <span data-ttu-id="9b696-254">Omówienie algorytmów uczenia maszynowego [neural](../resources/glossary.md#feature) dane, dzięki czemu następnym krokiem jest do przekształcania danych tekstowych do formatu, który rozpoznaje nasze algorytmy uczenia Maszynowego.</span><span class="sxs-lookup"><span data-stu-id="9b696-254">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, so the next step is to transform our textual data into a format that our ML algorithms recognize.</span></span> <span data-ttu-id="9b696-255">Ten format jest [liczbowych wektor](../resources/glossary.md#numerical-feature-vector).</span><span class="sxs-lookup"><span data-stu-id="9b696-255">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="9b696-256">Następnie wywołaj `mlContext.Transforms.Text.FeaturizeText` które featurizes kolumny tekstowej (`SentimentText`) o nazwie kolumny do wektora liczbowych `Features` używane przez algorytm uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="9b696-256">Next, call `mlContext.Transforms.Text.FeaturizeText` which featurizes the text column (`SentimentText`) column into a numeric vector called `Features` used by the machine learning algorithm.</span></span> <span data-ttu-id="9b696-257">To wywołanie otoką zwracające <xref:Microsoft.ML.Data.EstimatorChain%601> skutecznie się potoku.</span><span class="sxs-lookup"><span data-stu-id="9b696-257">This is a wrapper call that returns an <xref:Microsoft.ML.Data.EstimatorChain%601> that will effectively be a pipeline.</span></span> <span data-ttu-id="9b696-258">Nazwij to `pipeline` jako następnie dołączy trainer do `EstimatorChain`.</span><span class="sxs-lookup"><span data-stu-id="9b696-258">Name this `pipeline` as you will then append the trainer to the `EstimatorChain`.</span></span> <span data-ttu-id="9b696-259">Dodaj jako następnego wiersza kodu:</span><span class="sxs-lookup"><span data-stu-id="9b696-259">Add this as the next line of code:</span></span>

[!code-csharp[FeaturizeText](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

>[!WARNING]
> <span data-ttu-id="9b696-260">Wersja strukturze ML.NET 0.10 zmieniona kolejność parametrów transformacji.</span><span class="sxs-lookup"><span data-stu-id="9b696-260">ML.NET Version 0.10 changed the order of the Transform parameters.</span></span> <span data-ttu-id="9b696-261">To spowoduje nie Błąd limitu do czasu uruchomienia aplikacji i tworzenie modelu.</span><span class="sxs-lookup"><span data-stu-id="9b696-261">This will not error out until you run the application and build the model.</span></span> <span data-ttu-id="9b696-262">Użyj nazwy parametrów transformacji, jak pokazano w poprzednim fragmencie kodu.</span><span class="sxs-lookup"><span data-stu-id="9b696-262">Use the parameter names for Transforms as illustrated in the previous code snippet.</span></span>

<span data-ttu-id="9b696-263">Jest to krok przetwarzania wstępnego cechowania.</span><span class="sxs-lookup"><span data-stu-id="9b696-263">This is the preprocessing/featurization step.</span></span> <span data-ttu-id="9b696-264">Za pomocą dodatkowych składników dostępnych w strukturze ML.NET umożliwiają lepsze wyniki za pomocą modelu.</span><span class="sxs-lookup"><span data-stu-id="9b696-264">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="9b696-265">Wybieranie algorytmu uczenia</span><span class="sxs-lookup"><span data-stu-id="9b696-265">Choose a learning algorithm</span></span>

<span data-ttu-id="9b696-266">Aby dodać instruktora, należy wywołać `mlContext.BinaryClassification.Trainers.FastTree` metody otoki, która zwraca <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> obiektu.</span><span class="sxs-lookup"><span data-stu-id="9b696-266">To add the trainer, call the `mlContext.BinaryClassification.Trainers.FastTree` wrapper method which returns a <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> object.</span></span> <span data-ttu-id="9b696-267">Jest to uczeń drzewa decyzyjne, które będą używane w tym potoku.</span><span class="sxs-lookup"><span data-stu-id="9b696-267">This is a decision tree learner you'll use in this pipeline.</span></span> <span data-ttu-id="9b696-268">`FastTreeBinaryClassificationTrainer` Jest dołączany do `pipeline` i akceptuje neural `SentimentText` (`Features`) i `Label` parametrów, aby dowiedzieć się więcej na podstawie historycznych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="9b696-268">The `FastTreeBinaryClassificationTrainer` is appended to the `pipeline` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

<span data-ttu-id="9b696-269">Dodaj następujący kod do `BuildAndTrainModel` metody:</span><span class="sxs-lookup"><span data-stu-id="9b696-269">Add the following code to the `BuildAndTrainModel` method:</span></span>

[!code-csharp[FastTreeBinaryClassificationTrainer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a FastTreeBinaryClassificationTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="9b696-270">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="9b696-270">Train the model</span></span>

<span data-ttu-id="9b696-271">Uczenie modelu, <xref:Microsoft.ML.Data.TransformerChain%601>zgodnie z zestawu danych, który został załadowany i przekształcone.</span><span class="sxs-lookup"><span data-stu-id="9b696-271">You train the model, <xref:Microsoft.ML.Data.TransformerChain%601>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="9b696-272">Po zdefiniowaniu estymatora uczenie modelu przy użyciu <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> metoda przy jednoczesnym zapewnieniu dane szkoleniowe już załadowana.</span><span class="sxs-lookup"><span data-stu-id="9b696-272">Once the estimator has been defined, you train your model using the <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> method while providing the already loaded training data.</span></span> <span data-ttu-id="9b696-273">Spowoduje to zwrócenie modelu na potrzeby prognozy.</span><span class="sxs-lookup"><span data-stu-id="9b696-273">This returns a model to use for predictions.</span></span> <span data-ttu-id="9b696-274">`pipeline.Fit()` szkolenie modeli potoku i zwraca `Transformer` na podstawie `DataView` przekazany.</span><span class="sxs-lookup"><span data-stu-id="9b696-274">`pipeline.Fit()` trains the pipeline and returns a `Transformer` based on the `DataView` passed in.</span></span> <span data-ttu-id="9b696-275">Eksperyment nie jest wykonywane, dopóki `.Fit()` metoda przebiegów.</span><span class="sxs-lookup"><span data-stu-id="9b696-275">The experiment is not executed until the `.Fit()` method runs.</span></span>

<span data-ttu-id="9b696-276">Dodaj następujący kod do `BuildAndTrainModel` metody:</span><span class="sxs-lookup"><span data-stu-id="9b696-276">Add the following code to the `BuildAndTrainModel` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="9b696-277">Zapisz i wróć model jest uczony na potrzeby oceny</span><span class="sxs-lookup"><span data-stu-id="9b696-277">Save and Return the model trained to use for evaluation</span></span>

<span data-ttu-id="9b696-278">W tym momencie masz model typu <xref:Microsoft.ML.Data.TransformerChain%601> , można zintegrować wszystkich istniejących i nowych aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="9b696-278">At this point, you have a model of type <xref:Microsoft.ML.Data.TransformerChain%601> that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="9b696-279">Zwraca model na końcu `BuildAndTrainModel` metody.</span><span class="sxs-lookup"><span data-stu-id="9b696-279">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="9b696-280">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="9b696-280">Evaluate the model</span></span>

<span data-ttu-id="9b696-281">Teraz, po utworzeniu i uczony model, należy ocenić ją z innego zestawu danych do zapewniania jakości i sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="9b696-281">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="9b696-282">W `Evaluate` metody, model utworzony w `BuildAndTrainModel` jest przekazywany do obliczenia.</span><span class="sxs-lookup"><span data-stu-id="9b696-282">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="9b696-283">Tworzenie `Evaluate` metody tuż za `BuildAndTrainModel`, jak w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="9b696-283">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
{

}
```

<span data-ttu-id="9b696-284">`Evaluate` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="9b696-284">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="9b696-285">Ładuje zestawy danych testowych.</span><span class="sxs-lookup"><span data-stu-id="9b696-285">Loads the test dataset.</span></span>
* <span data-ttu-id="9b696-286">Tworzy ewaluatora binaryclassification.</span><span class="sxs-lookup"><span data-stu-id="9b696-286">Creates the binaryclassification evaluator.</span></span>
* <span data-ttu-id="9b696-287">Oblicza model i tworzy metryki.</span><span class="sxs-lookup"><span data-stu-id="9b696-287">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="9b696-288">Przedstawia metryki.</span><span class="sxs-lookup"><span data-stu-id="9b696-288">Displays the metrics.</span></span>

<span data-ttu-id="9b696-289">Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `Train` wywołania metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="9b696-289">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

<span data-ttu-id="9b696-290">Następnie użyjemy usługi machine learning `model` parametru (transformatora) i `splitTestSet` parametr wejściowy funkcji i zwracają prognozy.</span><span class="sxs-lookup"><span data-stu-id="9b696-290">Next, you'll use the machine learning `model` parameter (a transformer) and the `splitTestSet` parameter to input the features and return predictions.</span></span> <span data-ttu-id="9b696-291">Dodaj następujący kod do `Evaluate` metodę jako następny wiersz:</span><span class="sxs-lookup"><span data-stu-id="9b696-291">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

<span data-ttu-id="9b696-292">`mlContext.BinaryClassification.Evaluate` Metoda oblicza metryk jakości `PredictionModel` przy użyciu określonego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="9b696-292">The `mlContext.BinaryClassification.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="9b696-293">Zwraca <xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics> obiekt, który zawiera metryki ogólną obliczone przez ewaluatory klasyfikacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="9b696-293">It returns a <xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics> object that contains the overall metrics computed by binary classification evaluators.</span></span> <span data-ttu-id="9b696-294">Aby je wyświetlić, aby określić jakość modelu, należy pobrać pierwszy metryki.</span><span class="sxs-lookup"><span data-stu-id="9b696-294">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="9b696-295">Dodaj następujący kod w następnym wierszu `Evaluate` metody:</span><span class="sxs-lookup"><span data-stu-id="9b696-295">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="9b696-296">Wyświetlanie metryki dotyczące weryfikacji modelu</span><span class="sxs-lookup"><span data-stu-id="9b696-296">Displaying the metrics for model validation</span></span>

<span data-ttu-id="9b696-297">Użyj poniższego kodu, aby wyświetlić metryki, udostępnianie wyników, a następnie działanie na nich:</span><span class="sxs-lookup"><span data-stu-id="9b696-297">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

<span data-ttu-id="9b696-298">Aby zapisać swój model do pliku zip, przed zwróceniem, Dodaj następujący kod do wywoływania `SaveModelAsFile` metody w następnym wierszu `Evaluate`:</span><span class="sxs-lookup"><span data-stu-id="9b696-298">To save your model to a .zip file before returning, add the following code to call the `SaveModelAsFile` method as the next line in `Evaluate`:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallSaveModel "Save the model")]

## <a name="save-the-model-as-azip-file"></a><span data-ttu-id="9b696-299">Zapisz model jako plik a.zip</span><span class="sxs-lookup"><span data-stu-id="9b696-299">Save the model as a.zip file</span></span>

<span data-ttu-id="9b696-300">Tworzenie `SaveModelAsFile` metody tuż za `Evaluate` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="9b696-300">Create the `SaveModelAsFile` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="9b696-301">`SaveModelAsFile` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="9b696-301">The `SaveModelAsFile` method executes the following tasks:</span></span>

* <span data-ttu-id="9b696-302">Zapisuje modelu w postaci pliku zip.</span><span class="sxs-lookup"><span data-stu-id="9b696-302">Saves the model as a .zip file.</span></span>

<span data-ttu-id="9b696-303">Następnie utwórz metodę, aby zapisać modelu mogą być używane ponownie i używane w innych aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="9b696-303">Next, create a method to save the model so that it can be reused and consumed in other applications.</span></span> <span data-ttu-id="9b696-304">`ITransformer` Ma <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> metodę, która przyjmuje `_modelPath` globalne pola i <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="9b696-304">The `ITransformer` has a <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> method that takes in the `_modelPath` global field, and a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="9b696-305">Aby zapisać ten element jako plik zip, należy utworzyć `FileStream` bezpośrednio przed wywołaniem `SaveTo` metody.</span><span class="sxs-lookup"><span data-stu-id="9b696-305">To save this as a zip file, you'll create the `FileStream` immediately before calling the `SaveTo` method.</span></span> <span data-ttu-id="9b696-306">Dodaj następujący kod do `SaveModelAsFile` metodę jako następny wiersz:</span><span class="sxs-lookup"><span data-stu-id="9b696-306">Add the following code to the `SaveModelAsFile` method as the next line:</span></span>

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SaveModel "Add the SaveTo Method")]

<span data-ttu-id="9b696-307">Można również wyświetlić, którym został zapisany plik przy pisaniu komunikatu konsoli, za pomocą `_modelPath`, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="9b696-307">You could also display where the file was written by writing a console message with the `_modelPath`, using the following code:</span></span>

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="predict-the-test-data-outcome-with-the-saved-model"></a><span data-ttu-id="9b696-308">Wynik testu danych przy użyciu zapisanych modelu prognozowania</span><span class="sxs-lookup"><span data-stu-id="9b696-308">Predict the test data outcome with the saved model</span></span>

<span data-ttu-id="9b696-309">Tworzenie `UseModelWithSingleItem` metody tuż za `Evaluate` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="9b696-309">Create the `UseModelWithSingleItem` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="9b696-310">`UseModelWithSingleItem` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="9b696-310">The `UseModelWithSingleItem` method executes the following tasks:</span></span>

* <span data-ttu-id="9b696-311">Tworzy pojedynczy komentarz danych testowych.</span><span class="sxs-lookup"><span data-stu-id="9b696-311">Creates a single comment of test data.</span></span>
* <span data-ttu-id="9b696-312">Prognozuje tonacji na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="9b696-312">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="9b696-313">Łączy w sobie testowanie, danych i prognoz dla raportowania.</span><span class="sxs-lookup"><span data-stu-id="9b696-313">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="9b696-314">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="9b696-314">Displays the predicted results.</span></span>

<span data-ttu-id="9b696-315">Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `Evaluate` wywołania metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="9b696-315">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallUseModelWithSingleItem](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

<span data-ttu-id="9b696-316">Gdy `model` jest `transformer` który operuje na wiele wierszy danych, to bardzo typowy scenariusz w środowisku produkcyjnym jest na potrzeby prognoz na poszczególne przykłady.</span><span class="sxs-lookup"><span data-stu-id="9b696-316">While the `model` is a `transformer` that operates on many rows of data, a very common production scenario is a need for predictions on individual examples.</span></span> <span data-ttu-id="9b696-317"><xref:Microsoft.ML.PredictionEngine%602> Jest otoką, który jest zwracany z `CreatePredictionEngine` metody.</span><span class="sxs-lookup"><span data-stu-id="9b696-317">The <xref:Microsoft.ML.PredictionEngine%602> is a wrapper that is returned from the `CreatePredictionEngine` method.</span></span> <span data-ttu-id="9b696-318">Możemy dodać następujący kod, aby utworzyć `PredictionEngine` jako pierwszy wiersz w `Predict` metody:</span><span class="sxs-lookup"><span data-stu-id="9b696-318">Let's add the following code to create the `PredictionEngine` as the first line in the `Predict` Method:</span></span>

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]
  
<span data-ttu-id="9b696-319">Dodaj komentarz do testowania uczonego modelu prognozowania w `Predict` metody przez utworzenie wystąpienia `SentimentData`:</span><span class="sxs-lookup"><span data-stu-id="9b696-319">Add a comment to test the trained model's prediction in the `Predict` method by creating an instance of `SentimentData`:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

 <span data-ttu-id="9b696-320">Możesz go używać, aby przewidzieć dodatnie lub ujemne tonacji pojedyncze wystąpienie danych komentarz.</span><span class="sxs-lookup"><span data-stu-id="9b696-320">You can use that to predict the positive or negative sentiment of a single instance of the comment data.</span></span> <span data-ttu-id="9b696-321">Aby uzyskać prognozę, użyj <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> na danych.</span><span class="sxs-lookup"><span data-stu-id="9b696-321">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="9b696-322">Należy pamiętać, że dane wejściowe to ciąg, a model zawiera cechowania.</span><span class="sxs-lookup"><span data-stu-id="9b696-322">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="9b696-323">Potok jest zsynchronizowany podczas uczenia i przewidywania.</span><span class="sxs-lookup"><span data-stu-id="9b696-323">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="9b696-324">Nie trzeba napisać kod przetwarzania wstępnego cechowania specjalnie dla prognoz i zajmuje się tego samego interfejsu API i usługi batch jednorazowe prognozy.</span><span class="sxs-lookup"><span data-stu-id="9b696-324">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

### <a name="use-the-model-prediction"></a><span data-ttu-id="9b696-325">Użyj modelu: prognoz</span><span class="sxs-lookup"><span data-stu-id="9b696-325">Use the model: prediction</span></span>

<span data-ttu-id="9b696-326">Wyświetlanie `SentimentText` i odpowiednie przewidywania opinii w celu udostępniania wyników i odpowiednie do nich działanie na nich.</span><span class="sxs-lookup"><span data-stu-id="9b696-326">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="9b696-327">Jest to nazywane operacjonalizacji, jako część zasad operacyjnych przy użyciu zwracanych danych.</span><span class="sxs-lookup"><span data-stu-id="9b696-327">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="9b696-328">Tworzenie ekranu wyników za pomocą następujących <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:</span><span class="sxs-lookup"><span data-stu-id="9b696-328">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="deploy-and-predict-with-a-loaded-model"></a><span data-ttu-id="9b696-329">Wdrażanie i przewidywanie załadować modelu</span><span class="sxs-lookup"><span data-stu-id="9b696-329">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="9b696-330">Tworzenie `UseLoadedModelWithBatchItems` metody, tuż przed `SaveModelAsFile` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="9b696-330">Create the `UseLoadedModelWithBatchItems` method, just before the `SaveModelAsFile` method, using the following code:</span></span>

```csharp
public static void UseLoadedModelWithBatchItems(MLContext mlContext)
{

}
```

<span data-ttu-id="9b696-331">`UseLoadedModelWithBatchItems` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="9b696-331">The `UseLoadedModelWithBatchItems` method executes the following tasks:</span></span>

* <span data-ttu-id="9b696-332">Tworzy dane testowe usługi batch.</span><span class="sxs-lookup"><span data-stu-id="9b696-332">Creates batch test data.</span></span>
* <span data-ttu-id="9b696-333">Prognozuje tonacji na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="9b696-333">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="9b696-334">Łączy w sobie testowanie, danych i prognoz dla raportowania.</span><span class="sxs-lookup"><span data-stu-id="9b696-334">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="9b696-335">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="9b696-335">Displays the predicted results.</span></span>

<span data-ttu-id="9b696-336">Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `UseModelWithSingleItem` wywołania metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="9b696-336">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem` method call, using the following code:</span></span>

[!code-csharp[CallPredictModelLoaded](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseLoadedModelWithBatchItems "Call the CallUseLoadedModelWithBatchItems method")]

<span data-ttu-id="9b696-337">Dodaj niektóre komentarze, aby przetestować prognozy uczonego modelu w `UseLoadedModelWithBatchItems` metody:</span><span class="sxs-lookup"><span data-stu-id="9b696-337">Add some comments to test the trained model's predictions in the `UseLoadedModelWithBatchItems` method:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

<span data-ttu-id="9b696-338">Model obciążenia</span><span class="sxs-lookup"><span data-stu-id="9b696-338">Load the model</span></span>

[!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadModel "Load the model")]

<span data-ttu-id="9b696-339">Teraz, gdy model, możesz go używać, aby przewidzieć toksyczne lub inne niż toksyczne tonacji przy użyciu danych komentarz <xref:Microsoft.ML.ITransformer.Transform%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9b696-339">Now that you have a model, you can use that to predict the Toxic or Non Toxic sentiment of the comment data using the <xref:Microsoft.ML.ITransformer.Transform%2A> method.</span></span> <span data-ttu-id="9b696-340">Aby uzyskać prognozę, użyj `Predict` na nowych danych.</span><span class="sxs-lookup"><span data-stu-id="9b696-340">To get a prediction, use `Predict` on new data.</span></span> <span data-ttu-id="9b696-341">Należy pamiętać, że dane wejściowe to ciąg, a model zawiera cechowania.</span><span class="sxs-lookup"><span data-stu-id="9b696-341">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="9b696-342">Potok jest zsynchronizowany podczas uczenia i przewidywania.</span><span class="sxs-lookup"><span data-stu-id="9b696-342">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="9b696-343">Nie trzeba napisać kod przetwarzania wstępnego cechowania specjalnie dla prognoz i zajmuje się tego samego interfejsu API i usługi batch jednorazowe prognozy.</span><span class="sxs-lookup"><span data-stu-id="9b696-343">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span> <span data-ttu-id="9b696-344">Dodaj następujący kod do `UseLoadedModelWithBatchItems` metodę dla prognoz:</span><span class="sxs-lookup"><span data-stu-id="9b696-344">Add the following code to the `UseLoadedModelWithBatchItems` method for the predictions:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="use-the-loaded-model-for-prediction"></a><span data-ttu-id="9b696-345">Na użytek załadować modelu prognozowania</span><span class="sxs-lookup"><span data-stu-id="9b696-345">Use the loaded model for prediction</span></span>

<span data-ttu-id="9b696-346">Wyświetlanie `SentimentText` i odpowiednie przewidywania opinii w celu udostępniania wyników i odpowiednie do nich działanie na nich.</span><span class="sxs-lookup"><span data-stu-id="9b696-346">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="9b696-347">Jest to nazywane operacjonalizacji, jako część zasad operacyjnych przy użyciu zwracanych danych.</span><span class="sxs-lookup"><span data-stu-id="9b696-347">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="9b696-348">Utwórz nagłówek dla wyników za pomocą następujących <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:</span><span class="sxs-lookup"><span data-stu-id="9b696-348">Create a header for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="9b696-349">Przed wyświetleniem wyników, Połącz opinii i prognozowania ze sobą, aby zobaczyć, oryginalnym komentarzem z jego przewidywane wskaźniki nastrojów klientów.</span><span class="sxs-lookup"><span data-stu-id="9b696-349">Before displaying the predicted results, combine the sentiment and prediction together to see the original comment with its predicted sentiment.</span></span> <span data-ttu-id="9b696-350">Poniższy kod używa <xref:System.Linq.Enumerable.Zip%2A> metodę, aby to zrobić, obok więc Dodaj ten kod:</span><span class="sxs-lookup"><span data-stu-id="9b696-350">The following code uses the <xref:System.Linq.Enumerable.Zip%2A> method to make that happen, so add that code next:</span></span>

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#BuildSentimentPredictionPairs "Build the pairs of sentiment data and predictions")]

<span data-ttu-id="9b696-351">Teraz, gdy zostały połączone `SentimentText` i `Sentiment` do klasy, można wyświetlić wyniki za pomocą <xref:System.Console.WriteLine?displayProperty=nameWithType> metody:</span><span class="sxs-lookup"><span data-stu-id="9b696-351">Now that you've combined the `SentimentText` and `Sentiment` into a class, you can display the results using the <xref:System.Console.WriteLine?displayProperty=nameWithType> method:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

<span data-ttu-id="9b696-352">Ponieważ wywnioskować, że jest nową funkcją w C# 7.1 i wersją języka domyślnego projektu języka C# 7.0 nazwami elementów krotki, musisz zmienić wersję języka C# 7.1 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="9b696-352">Because inferred tuple element names are a new feature in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span>
<span data-ttu-id="9b696-353">Aby to zrobić, kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="9b696-353">To do that, right-click on the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="9b696-354">Wybierz **kompilacji** kartę, a następnie wybierz pozycję **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9b696-354">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="9b696-355">Z listy rozwijanej wybierz **języka C# 7.1** (lub nowsza wersja).</span><span class="sxs-lookup"><span data-stu-id="9b696-355">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="9b696-356">Wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="9b696-356">Select the **OK** button.</span></span>

## <a name="results"></a><span data-ttu-id="9b696-357">Wyniki</span><span class="sxs-lookup"><span data-stu-id="9b696-357">Results</span></span>

<span data-ttu-id="9b696-358">Wyniki powinny być podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="9b696-358">Your results should be similar to the following.</span></span> <span data-ttu-id="9b696-359">Ponieważ przetwarza potoku, wyświetla komunikaty.</span><span class="sxs-lookup"><span data-stu-id="9b696-359">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="9b696-360">Może zostać wyświetlony ostrzeżenia lub komunikaty przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="9b696-360">You may see warnings, or processing messages.</span></span> <span data-ttu-id="9b696-361">Te zostały usunięte z następujących wyników dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="9b696-361">These have been removed from the following results for clarity.</span></span>

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 79.14%
Auc: 86.27%
F1Score: 80.60%

=============== End of model evaluation ===============
The model is saved to C:\Tutorials\SentimentAnalysis\bin\Debug\netcoreapp2.1\Data\Model.zip

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This was a very bad steak | Prediction: Negative | Probability: 0.4641322
=============== End of Predictions ===============


=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This was a horrible meal | Prediction: Negative | Probability: 0.1391833
Sentiment: I love this spaghetti. | Prediction: Positive | Probability: 0.9819039
=============== End of predictions ===============

=============== End of process ===============
Press any key to continue . . .

```

<span data-ttu-id="9b696-362">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="9b696-362">Congratulations!</span></span> <span data-ttu-id="9b696-363">Model uczenia maszynowego dla klasyfikacji i prognozowanie tonacji wiadomości teraz zostały pomyślnie skompilowane.</span><span class="sxs-lookup"><span data-stu-id="9b696-363">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span> 

<span data-ttu-id="9b696-364">Tworzenie modeli pomyślne jest procesem iteracyjnym.</span><span class="sxs-lookup"><span data-stu-id="9b696-364">Building successful models is an iterative process.</span></span> <span data-ttu-id="9b696-365">Ten model jest początkowa niższa jakość samouczek używa małych zestawów danych na przeszkolenie szybkiego modelu.</span><span class="sxs-lookup"><span data-stu-id="9b696-365">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="9b696-366">Jeśli nie jesteś zadowolony z jakość modelu, możesz spróbować ją ulepszyć, zapewniając większych zestawów danych szkoleniowych lub wybierając szkolenia różnych algorytmów przy użyciu różnych funkcji hyper parametrów dla każdego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="9b696-366">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different hyper-parameters for each algorithm.</span></span>

<span data-ttu-id="9b696-367">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="9b696-367">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9b696-368">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="9b696-368">Next steps</span></span>

<span data-ttu-id="9b696-369">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="9b696-369">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="9b696-370">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="9b696-370">Understand the problem</span></span>
> * <span data-ttu-id="9b696-371">Wybieranie algorytmu uczenia maszynowego odpowiednie</span><span class="sxs-lookup"><span data-stu-id="9b696-371">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="9b696-372">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="9b696-372">Prepare your data</span></span>
> * <span data-ttu-id="9b696-373">Przekształcanie danych</span><span class="sxs-lookup"><span data-stu-id="9b696-373">Transform the data</span></span>
> * <span data-ttu-id="9b696-374">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="9b696-374">Train the model</span></span>
> * <span data-ttu-id="9b696-375">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="9b696-375">Evaluate the model</span></span>
> * <span data-ttu-id="9b696-376">Prognozowanie za pomocą uczonego modelu</span><span class="sxs-lookup"><span data-stu-id="9b696-376">Predict with the trained model</span></span>
> * <span data-ttu-id="9b696-377">Wdrażanie i przewidywanie załadować modelu</span><span class="sxs-lookup"><span data-stu-id="9b696-377">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="9b696-378">Przejdź do następnego samouczka, aby dowiedzieć się więcej</span><span class="sxs-lookup"><span data-stu-id="9b696-378">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="9b696-379">Klasyfikacja problemu</span><span class="sxs-lookup"><span data-stu-id="9b696-379">Issue Classification</span></span>](github-issue-classification.md)
