---
title: 'Samouczek: Klasyfikowanie problemów z obsługą - wieloklasowej klasyfikacji'
description: Dowiedz się, jak używać strukturze ML.NET w scenariuszu wieloklasowej klasyfikacji można klasyfikować problemy usługi GitHub, aby przypisać je do danego obszaru.
ms.date: 05/16/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: d47522bef632de1aac890d4de384c1b2c16b7a50
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877342"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-ml-net"></a><span data-ttu-id="907f7-103">Samouczek: Klasyfikowanie problemów przy użyciu klasyfikacji wieloklasowej przy użyciu uczenia Maszynowego platformy .NET</span><span class="sxs-lookup"><span data-stu-id="907f7-103">Tutorial: Categorize support issues using multiclass classification with ML .NET</span></span>

<span data-ttu-id="907f7-104">Ten przykładowy samouczek przedstawia tworzenie klasyfikatora problem usługi GitHub do nauczenia modelu, która klasyfikuje i przewiduje etykieta obszar problemu w usłudze GitHub za pomocą używany aplikację konsoli .NET Core przy użyciu strukturze ML.NET C# w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="907f7-104">This sample tutorial illustrates using ML.NET to create a GitHub issue classifier to train a model that classifies and predicts the Area label for a GitHub issue via a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="907f7-105">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="907f7-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="907f7-106">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="907f7-106">Prepare your data</span></span>
> * <span data-ttu-id="907f7-107">Przekształcanie danych</span><span class="sxs-lookup"><span data-stu-id="907f7-107">Transform the data</span></span>
> * <span data-ttu-id="907f7-108">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="907f7-108">Train the model</span></span>
> * <span data-ttu-id="907f7-109">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="907f7-109">Evaluate the model</span></span>
> * <span data-ttu-id="907f7-110">Prognozowanie za pomocą uczonego modelu</span><span class="sxs-lookup"><span data-stu-id="907f7-110">Predict with the trained model</span></span>
> * <span data-ttu-id="907f7-111">Wdrażanie i przewidywanie załadować modelu</span><span class="sxs-lookup"><span data-stu-id="907f7-111">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="907f7-112">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="907f7-112">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="907f7-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="907f7-113">Prerequisites</span></span>

* <span data-ttu-id="907f7-114">[Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".</span><span class="sxs-lookup"><span data-stu-id="907f7-114">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="907f7-115">[Github generuje plik z wartościami oddzielonymi tabulatorami (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span><span class="sxs-lookup"><span data-stu-id="907f7-115">The [Github issues tab separated file (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span></span>
* <span data-ttu-id="907f7-116">[Problemy usługi Github test pliku z wartościami oddzielonymi tabulatorami (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span><span class="sxs-lookup"><span data-stu-id="907f7-116">The [Github issues test tab separated file (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="907f7-117">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="907f7-117">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="907f7-118">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="907f7-118">Create a project</span></span>

1. <span data-ttu-id="907f7-119">Otwórz program Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="907f7-119">Open Visual Studio 2017.</span></span> <span data-ttu-id="907f7-120">Wybierz **pliku** > **New** > **projektu** z paska menu.</span><span class="sxs-lookup"><span data-stu-id="907f7-120">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="907f7-121">W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła następuje **platformy .NET Core** węzła.</span><span class="sxs-lookup"><span data-stu-id="907f7-121">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="907f7-122">Następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="907f7-122">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="907f7-123">W **nazwa** pole tekstowe, wpisz "GitHubIssueClassification", a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="907f7-123">In the **Name** text box, type "GitHubIssueClassification" and then select the **OK** button.</span></span>

2. <span data-ttu-id="907f7-124">Utwórz katalog o nazwie *danych* w projekcie, aby zapisać pliki zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="907f7-124">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="907f7-125">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nad projektem i wybierz **Dodaj** > **nowy Folder**.</span><span class="sxs-lookup"><span data-stu-id="907f7-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="907f7-126">Wpisz "Dane", a następnie naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="907f7-126">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="907f7-127">Utwórz katalog o nazwie *modeli* w projekcie, aby zapisać modelu:</span><span class="sxs-lookup"><span data-stu-id="907f7-127">Create a directory named *Models* in your project to save your model:</span></span>

    <span data-ttu-id="907f7-128">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nad projektem i wybierz **Dodaj** > **nowy Folder**.</span><span class="sxs-lookup"><span data-stu-id="907f7-128">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="907f7-129">Wpisz "Modele", a następnie naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="907f7-129">Type "Models" and hit Enter.</span></span>

4. <span data-ttu-id="907f7-130">Zainstaluj **pakietu NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="907f7-130">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="907f7-131">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="907f7-131">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="907f7-132">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.ML**, wybierz opcję **v 1.0.0** pakietu na liście, a następnie wybierz pozycję **zainstalować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="907f7-132">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select the **v 1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="907f7-133">Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.</span><span class="sxs-lookup"><span data-stu-id="907f7-133">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="907f7-134">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="907f7-134">Prepare your data</span></span>

1. <span data-ttu-id="907f7-135">Pobierz [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) i [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) danych ustawia i zapisywanie ich *danych* wcześniej utworzony folder.</span><span class="sxs-lookup"><span data-stu-id="907f7-135">Download the [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) and the [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="907f7-136">Szkolenie modeli modelu uczenia maszynowego na pierwszego zestawu danych, a drugi może służyć do oceny, jak dokładna jest model.</span><span class="sxs-lookup"><span data-stu-id="907f7-136">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="907f7-137">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy każdy z \*pliki tsv i wybierz pozycję **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="907f7-137">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="907f7-138">W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="907f7-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="907f7-139">Tworzenie klas i definiowania ścieżek</span><span class="sxs-lookup"><span data-stu-id="907f7-139">Create classes and define paths</span></span>

<span data-ttu-id="907f7-140">Dodaj następujące dodatkowe `using` instrukcji na górze *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="907f7-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

<span data-ttu-id="907f7-141">Utwórz trzy pola globalnego na potrzeby przechowywania ścieżek do ostatnio pobrane pliki i zmiennych globalnych `MLContext`,`DataView`, i `PredictionEngine`:</span><span class="sxs-lookup"><span data-stu-id="907f7-141">Create three global fields to hold the paths to the recently downloaded files, and global variables for the `MLContext`,`DataView`, and `PredictionEngine`:</span></span>

* <span data-ttu-id="907f7-142">`_trainDataPath` zawiera ścieżkę do zestawu danych, używane do trenowania modelu.</span><span class="sxs-lookup"><span data-stu-id="907f7-142">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="907f7-143">`_testDataPath` zawiera ścieżkę do zestawu danych, używane do oceny modelu.</span><span class="sxs-lookup"><span data-stu-id="907f7-143">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="907f7-144">`_modelPath` ma ścieżkę, w którym jest zapisany trenowanego modelu.</span><span class="sxs-lookup"><span data-stu-id="907f7-144">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="907f7-145">`_mlContext` jest <xref:Microsoft.ML.MLContext> zapewniający przetwarzania kontekstu.</span><span class="sxs-lookup"><span data-stu-id="907f7-145">`_mlContext` is the <xref:Microsoft.ML.MLContext> that provides processing context.</span></span>
* <span data-ttu-id="907f7-146">`_trainingDataView` jest <xref:Microsoft.ML.IDataView> używani do przetwarzania zestaw danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="907f7-146">`_trainingDataView` is the <xref:Microsoft.ML.IDataView> used to process the training dataset.</span></span>
* <span data-ttu-id="907f7-147">`_predEngine` jest <xref:Microsoft.ML.PredictionEngine%602> używany dla pojedynczego prognozy.</span><span class="sxs-lookup"><span data-stu-id="907f7-147">`_predEngine` is the <xref:Microsoft.ML.PredictionEngine%602> used for single predictions.</span></span>

<span data-ttu-id="907f7-148">Dodaj następujący kod po prawej stronie wiersza powyżej `Main` metodę, aby określić ścieżki te i inne zmienne:</span><span class="sxs-lookup"><span data-stu-id="907f7-148">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="907f7-149">Utwórz niektóre klasy dla danych wejściowych i prognozy.</span><span class="sxs-lookup"><span data-stu-id="907f7-149">Create some classes for your input data and predictions.</span></span> <span data-ttu-id="907f7-150">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="907f7-150">Add a new class to your project:</span></span>

1. <span data-ttu-id="907f7-151">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="907f7-151">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="907f7-152">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *GitHubIssueData.cs*.</span><span class="sxs-lookup"><span data-stu-id="907f7-152">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *GitHubIssueData.cs*.</span></span> <span data-ttu-id="907f7-153">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="907f7-153">Then, select the **Add** button.</span></span>

    <span data-ttu-id="907f7-154">*GitHubIssueData.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="907f7-154">The *GitHubIssueData.cs* file opens in the code editor.</span></span> <span data-ttu-id="907f7-155">Dodaj następujący kod `using` instrukcji na górze *GitHubIssueData.cs*:</span><span class="sxs-lookup"><span data-stu-id="907f7-155">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

<span data-ttu-id="907f7-156">Usuń istniejącą definicję klasy i Dodaj następujący kod, który zawiera dwie klasy `GitHubIssue` i `IssuePrediction`, *GitHubIssueData.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="907f7-156">Remove the existing class definition and add the following code, which has two classes `GitHubIssue` and `IssuePrediction`, to the *GitHubIssueData.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

<span data-ttu-id="907f7-157">`label` Kolumna, która chcesz przewidzieć.</span><span class="sxs-lookup"><span data-stu-id="907f7-157">The `label` is the column you want to predict.</span></span> <span data-ttu-id="907f7-158">Wskazywanego przez nią `Features` to dane wejściowe, nadaj model do przewidywania etykiety.</span><span class="sxs-lookup"><span data-stu-id="907f7-158">The identified `Features` are the inputs you give the model to predict the Label.</span></span>

<span data-ttu-id="907f7-159">Użyj [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) do określania wskaźników kolumny źródłowe w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="907f7-159">Use the [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="907f7-160">`GitHubIssue` jest to klasa wejściowy zestaw danych i ma następujące <xref:System.String> pola:</span><span class="sxs-lookup"><span data-stu-id="907f7-160">`GitHubIssue` is the input dataset class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="907f7-161">Pierwsza kolumna `ID` (identyfikator problemu usługi GitHub)</span><span class="sxs-lookup"><span data-stu-id="907f7-161">the first column `ID` (GitHub Issue ID)</span></span>
* <span data-ttu-id="907f7-162">druga kolumna `Area` (prognozowane potrzeby szkolenia)</span><span class="sxs-lookup"><span data-stu-id="907f7-162">the second column `Area` (the prediction for training)</span></span>
* <span data-ttu-id="907f7-163">trzecia kolumna `Title` (tytuł problemu usługi GitHub) jest to pierwszy `feature` używane do prognozowania `Area`</span><span class="sxs-lookup"><span data-stu-id="907f7-163">the third column `Title` (GitHub issue title) is the first `feature` used for predicting the `Area`</span></span>
* <span data-ttu-id="907f7-164">Czwarta kolumna `Description` drugi `feature` używane do prognozowania `Area`</span><span class="sxs-lookup"><span data-stu-id="907f7-164">the fourth column  `Description` is the second `feature` used for predicting the `Area`</span></span>

<span data-ttu-id="907f7-165">`IssuePrediction` Klasa służy do prognozowania po wyszkoliła modelu.</span><span class="sxs-lookup"><span data-stu-id="907f7-165">`IssuePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="907f7-166">Ma on jeden `string` (`Area`) i `PredictedLabel` `ColumnName` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="907f7-166">It has a single `string` (`Area`) and a `PredictedLabel` `ColumnName` attribute.</span></span>  <span data-ttu-id="907f7-167">`PredictedLabel` Używany podczas prognoz i oceny.</span><span class="sxs-lookup"><span data-stu-id="907f7-167">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="907f7-168">W wersji ewaluacyjnej używane są dane szkoleniowe, przewidywane wartości i model danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="907f7-168">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="907f7-169">Wszystkie operacje strukturze ML.NET uruchomić w [MLContext](xref:Microsoft.ML.MLContext) klasy.</span><span class="sxs-lookup"><span data-stu-id="907f7-169">All ML.NET operations start in the [MLContext](xref:Microsoft.ML.MLContext) class.</span></span> <span data-ttu-id="907f7-170">Inicjowanie `mlContext` tworzy nowe środowisko strukturze ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="907f7-170">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="907f7-171">Przypomina, model `DBContext` w `Entity Framework`.</span><span class="sxs-lookup"><span data-stu-id="907f7-171">It's similar, conceptually, to `DBContext` in `Entity Framework`.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="907f7-172">Inicjowanie zmiennych w głównym oknie</span><span class="sxs-lookup"><span data-stu-id="907f7-172">Initialize variables in Main</span></span>

<span data-ttu-id="907f7-173">Inicjowanie `_mlContext` zmienna globalna o nowe wystąpienie klasy `MLContext` z Inicjator losowy (`seed: 0`) dla powtarzalnych/deterministyczne wyników w szkoleniach wielu.</span><span class="sxs-lookup"><span data-stu-id="907f7-173">Initialize the `_mlContext` global variable  with a new instance of `MLContext` with a random seed (`seed: 0`) for repeatable/deterministic results across multiple trainings.</span></span>  <span data-ttu-id="907f7-174">Zastąp `Console.WriteLine("Hello World!")` wiersz poniższym kodem w `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="907f7-174">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a><span data-ttu-id="907f7-175">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="907f7-175">Load the data</span></span>

<span data-ttu-id="907f7-176">Używa strukturze ML.NET [klasy IDataView](xref:Microsoft.ML.IDataView) jako dane tabelaryczne numeryczny lub tekst opisujący sposób elastyczne i wydajne.</span><span class="sxs-lookup"><span data-stu-id="907f7-176">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="907f7-177">`IDataView` można załadować albo pliki tekstowe lub w czasie rzeczywistym (na przykład SQL bazy danych lub pliki dziennika).</span><span class="sxs-lookup"><span data-stu-id="907f7-177">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span>

<span data-ttu-id="907f7-178">Aby zainicjować i załadować `_trainingDataView` zmienna globalna, aby mógł zostać użyty dla potoku, Dodaj następujący kod po `mlContext` inicjowania:</span><span class="sxs-lookup"><span data-stu-id="907f7-178">To initialize and load the `_trainingDataView` global variable in order to use it for the pipeline, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]

<span data-ttu-id="907f7-179">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczytuje w pliku.</span><span class="sxs-lookup"><span data-stu-id="907f7-179">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="907f7-180">Pobiera zmienne ścieżek danych i zwraca `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="907f7-180">It takes in the data path variables and returns an `IDataView`.</span></span>

<span data-ttu-id="907f7-181">Dodaj następujący kod jako następnego wiersza kodu w `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="907f7-181">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallProcessData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

<span data-ttu-id="907f7-182">`ProcessData` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="907f7-182">The `ProcessData` method executes the following tasks:</span></span>

* <span data-ttu-id="907f7-183">Wyodrębnia i przekształca dane.</span><span class="sxs-lookup"><span data-stu-id="907f7-183">Extracts and transforms the data.</span></span>
* <span data-ttu-id="907f7-184">Zwraca potoku przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="907f7-184">Returns the processing pipeline.</span></span>

<span data-ttu-id="907f7-185">Tworzenie `ProcessData` metody tuż za `Main` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="907f7-185">Create the `ProcessData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="907f7-186">Wyodrębnianie funkcji i przekształcania danych</span><span class="sxs-lookup"><span data-stu-id="907f7-186">Extract Features and transform the data</span></span>

<span data-ttu-id="907f7-187">Jak chcesz przewidzieć etykieta GitHub powierzchni `GitHubIssue`, użyj [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) metodę, aby przekształcić `Area` kolumny na typ liczbowy klucza `Label` kolumny (formacie akceptowanym przez algorytmy klasyfikacji ) i dodaj ją jako nowe kolumny zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="907f7-187">As you want to predict the Area GitHub label for a `GitHubIssue`, use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform the `Area` column into a numeric key type `Label` column (a format accepted by classification algorithms) and add it as a new dataset column:</span></span>

[!code-csharp[MapValueToKey](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

<span data-ttu-id="907f7-188">Następnie wywołaj `mlContext.Transforms.Text.FeaturizeText` która przekształca tekst (`Title` i `Description`) kolumny liczbowe wektor dla każdego o nazwie `TitleFeaturized` i `DescriptionFeaturized`.</span><span class="sxs-lookup"><span data-stu-id="907f7-188">Next, call `mlContext.Transforms.Text.FeaturizeText` which transforms the text (`Title` and `Description`) columns into a numeric vector for each called `TitleFeaturized` and `DescriptionFeaturized`.</span></span> <span data-ttu-id="907f7-189">Dołącz cechowania dla obu kolumn do potoku z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="907f7-189">Append the featurization for both columns to the pipeline with the following code:</span></span>

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

<span data-ttu-id="907f7-190">Ostatnim krokiem w przygotowaniu danych łączy wszystkie kolumny funkcji do **funkcji** przy użyciu kolumny [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) metody.</span><span class="sxs-lookup"><span data-stu-id="907f7-190">The last step in data preparation combines all of the feature columns into the **Features** column using the [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) method.</span></span> <span data-ttu-id="907f7-191">Domyślnie algorytmu uczenia przetwarza tylko funkcje z **funkcji** kolumny.</span><span class="sxs-lookup"><span data-stu-id="907f7-191">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="907f7-192">Dołącz to przekształcenie do potoku z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="907f7-192">Append this transformation to the pipeline with the following code:</span></span>

[!code-csharp[Concatenate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 <span data-ttu-id="907f7-193">Następnie dołącz <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> w pamięci podręcznej widoku danych, dzięki czemu podczas iteracji przez dane wielokrotnie przy użyciu pamięci podręcznej mogą uzyskać lepszą wydajność, zgodnie z poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="907f7-193">Next, append a <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> to cache the DataView so when you iterate over the data multiple times using the cache might get better performance, as with the following code:</span></span>

[!code-csharp[AppendCache](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

> [!WARNING]
> <span data-ttu-id="907f7-194">Użyj AppendCacheCheckpoint dla zestawów danych małe i średnie, aby zmniejszyć czas szkolenia.</span><span class="sxs-lookup"><span data-stu-id="907f7-194">Use AppendCacheCheckpoint for small/medium datasets to lower training time.</span></span> <span data-ttu-id="907f7-195">Nie używaj go (Usuń. AppendCacheCheckpoint()) podczas obsługi bardzo dużych zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="907f7-195">Do NOT use it (remove .AppendCacheCheckpoint()) when handling very large datasets.</span></span>

<span data-ttu-id="907f7-196">Zwróć potoku na końcu `ProcessData` metody.</span><span class="sxs-lookup"><span data-stu-id="907f7-196">Return the pipeline at the end of the `ProcessData` method.</span></span>

[!code-csharp[ReturnPipeline](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

<span data-ttu-id="907f7-197">W tym kroku obsługuje przetwarzania wstępnego cechowania.</span><span class="sxs-lookup"><span data-stu-id="907f7-197">This step handles preprocessing/featurization.</span></span> <span data-ttu-id="907f7-198">Za pomocą dodatkowych składników dostępnych w strukturze ML.NET umożliwiają lepsze wyniki za pomocą modelu.</span><span class="sxs-lookup"><span data-stu-id="907f7-198">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="build-and-train-the-model"></a><span data-ttu-id="907f7-199">Tworzenie i trenowanie modelu</span><span class="sxs-lookup"><span data-stu-id="907f7-199">Build and train the model</span></span>

<span data-ttu-id="907f7-200">Dodaj następujące wywołanie do `BuildAndTrainModel`metodę jako następnego wiersza kodu w `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="907f7-200">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="907f7-201">`BuildAndTrainModel` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="907f7-201">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="907f7-202">Tworzy klasę algorytm szkolenia.</span><span class="sxs-lookup"><span data-stu-id="907f7-202">Creates the training algorithm class.</span></span>
* <span data-ttu-id="907f7-203">Szkolenie modeli modelu.</span><span class="sxs-lookup"><span data-stu-id="907f7-203">Trains the model.</span></span>
* <span data-ttu-id="907f7-204">Prognozuje obszaru, w oparciu o dane szkoleniowe.</span><span class="sxs-lookup"><span data-stu-id="907f7-204">Predicts area based on training data.</span></span>
* <span data-ttu-id="907f7-205">Zwraca wartość modelu.</span><span class="sxs-lookup"><span data-stu-id="907f7-205">Returns the model.</span></span>

<span data-ttu-id="907f7-206">Tworzenie `BuildAndTrainModel` metody tuż za `Main` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="907f7-206">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a><span data-ttu-id="907f7-207">O zadaniu klasyfikacji</span><span class="sxs-lookup"><span data-stu-id="907f7-207">About the classification task</span></span>

<span data-ttu-id="907f7-208">Klasyfikacja jest zadanie uczenia maszynowego, które są używane dane do **określić** kategorii, typ lub klasa elementu lub wiersz danych i jest często jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="907f7-208">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data and is frequently one of the following types:</span></span>

* <span data-ttu-id="907f7-209">Plik binarny: A i B.</span><span class="sxs-lookup"><span data-stu-id="907f7-209">Binary: either A or B.</span></span>
* <span data-ttu-id="907f7-210">Kontra: wielu kategorii, które można przewidzieć przy użyciu pojedynczego modelu.</span><span class="sxs-lookup"><span data-stu-id="907f7-210">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="907f7-211">Tego rodzaju problem korzystanie z klasyfikacji kontra, uczenie algorytmu, ponieważ do prognozowania kategorii problemu może być jednym z wielu kategorii (kontra), a nie tylko dwóch (binarnych).</span><span class="sxs-lookup"><span data-stu-id="907f7-211">For this type of problem, use a Multiclass classification learning algorithm, since your issue category prediction can be one of multiple categories (multiclass) rather than just two (binary).</span></span>

<span data-ttu-id="907f7-212">Dołącz Algorytm uczenia maszynowego z definicjami przekształcania danych przez dodanie poniższego jako pierwszy wiersz kodu w `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="907f7-212">Append the machine learning algorithm to the data transformation definitions by adding the following as the first line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddTrainer](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

<span data-ttu-id="907f7-213">[SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) to algorytm klasyfikacji wieloklasowej szkolenia.</span><span class="sxs-lookup"><span data-stu-id="907f7-213">The [SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) is your multiclass classification training algorithm.</span></span> <span data-ttu-id="907f7-214">To jest dołączany do `pipeline` i akceptuje neural `Title` i `Description` (`Features`) i `Label` parametrów, aby dowiedzieć się więcej na podstawie historycznych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="907f7-214">This is appended to the `pipeline` and accepts the featurized `Title` and `Description` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="907f7-215">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="907f7-215">Train the model</span></span>

<span data-ttu-id="907f7-216">Dopasuj do modelu `splitTrainSet` danych i zwracają uczonego modelu przez dodanie poniższego jako następnego wiersza kodu w `BuildAndTrainModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="907f7-216">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

<span data-ttu-id="907f7-217">`Fit()`Metoda szkolenie modeli modelu przekształcania zestawu danych i stosując szkolenia.</span><span class="sxs-lookup"><span data-stu-id="907f7-217">The `Fit()`method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="907f7-218">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest wygoda interfejsu API, dzięki czemu można przekazać, a następnie wykonaj prognozowania w pojedynczym wystąpieniu danych.</span><span class="sxs-lookup"><span data-stu-id="907f7-218">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span> <span data-ttu-id="907f7-219">Dodaj to w następnym wierszu `BuildAndTrainModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="907f7-219">Add this as the next line in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[CreatePredictionEngine1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a><span data-ttu-id="907f7-220">Prognozowanie za pomocą uczonego modelu</span><span class="sxs-lookup"><span data-stu-id="907f7-220">Predict with the trained model</span></span>

<span data-ttu-id="907f7-221">Dodaj problem w usłudze GitHub do testowania uczonego modelu prognozowania w `Predict` metody przez utworzenie wystąpienia `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="907f7-221">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[CreateTestIssue1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

<span data-ttu-id="907f7-222">Użyj [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) funkcja sprawia, że prognoz na pojedynczy wiersz danych:</span><span class="sxs-lookup"><span data-stu-id="907f7-222">Use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a><span data-ttu-id="907f7-223">Przy użyciu modelu: przewidywanie wyników</span><span class="sxs-lookup"><span data-stu-id="907f7-223">Using the model: prediction results</span></span>

<span data-ttu-id="907f7-224">Wyświetlanie `GitHubIssue` i odpowiadających im `Area` etykiety prognozowania, aby można było udostępnić wyniki i podejmowanie odpowiednich działań na nich.</span><span class="sxs-lookup"><span data-stu-id="907f7-224">Display `GitHubIssue` and corresponding `Area` label prediction in order to share the results and act on them accordingly.</span></span>  <span data-ttu-id="907f7-225">Tworzenie ekranu wyników za pomocą następujących <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:</span><span class="sxs-lookup"><span data-stu-id="907f7-225">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="907f7-226">Zwraca czy model jest uczony na potrzeby oceny</span><span class="sxs-lookup"><span data-stu-id="907f7-226">Return the model trained to use for evaluation</span></span>

<span data-ttu-id="907f7-227">Zwraca model na końcu `BuildAndTrainModel` metody.</span><span class="sxs-lookup"><span data-stu-id="907f7-227">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a><span data-ttu-id="907f7-228">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="907f7-228">Evaluate the model</span></span>

<span data-ttu-id="907f7-229">Teraz, po utworzeniu i uczony model, należy ocenić ją z innego zestawu danych do zapewniania jakości i sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="907f7-229">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="907f7-230">W `Evaluate` metody, model utworzony w `BuildAndTrainModel` jest przekazywany do obliczenia.</span><span class="sxs-lookup"><span data-stu-id="907f7-230">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="907f7-231">Tworzenie `Evaluate` metody tuż za `BuildAndTrainModel`, jak w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="907f7-231">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate()
{

}
```

<span data-ttu-id="907f7-232">`Evaluate` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="907f7-232">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="907f7-233">Ładuje zestawy danych testowych.</span><span class="sxs-lookup"><span data-stu-id="907f7-233">Loads the test dataset.</span></span>
* <span data-ttu-id="907f7-234">Tworzy ewaluatora wieloklasowej.</span><span class="sxs-lookup"><span data-stu-id="907f7-234">Creates the multiclass evaluator.</span></span>
* <span data-ttu-id="907f7-235">Oblicza model oraz tworzenie metryk.</span><span class="sxs-lookup"><span data-stu-id="907f7-235">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="907f7-236">Przedstawia metryki.</span><span class="sxs-lookup"><span data-stu-id="907f7-236">Displays the metrics.</span></span>

<span data-ttu-id="907f7-237">Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `BuildAndTrainModel` wywołania metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="907f7-237">Add a call to the new method from the `Main` method, right under the `BuildAndTrainModel` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

<span data-ttu-id="907f7-238">Tak jak poprzednio w przypadku zestawu danych szkoleniowych, ładowanie zestawu danych testowych, dodając następujący kod do `Evaluate` metody:</span><span class="sxs-lookup"><span data-stu-id="907f7-238">As you did previously with the training dataset, load the test dataset by adding the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

<span data-ttu-id="907f7-239">[Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) metoda oblicza metryk jakości dla modelu przy użyciu określonego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="907f7-239">The [Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) method computes the quality metrics for the model using the specified dataset.</span></span> <span data-ttu-id="907f7-240">Zwraca <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> obiekt, który zawiera metryki ogólną obliczone przez ewaluatory klasyfikacji wieloklasowej.</span><span class="sxs-lookup"><span data-stu-id="907f7-240">It returns a <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> object that contains the overall metrics computed by multiclass classification evaluators.</span></span>
<span data-ttu-id="907f7-241">Aby wyświetlić metryki, aby określić jakość modelu, należy je uzyskać pierwszy.</span><span class="sxs-lookup"><span data-stu-id="907f7-241">To display the metrics to determine the quality of the model, you need to get them first.</span></span>
<span data-ttu-id="907f7-242">Zwróć uwagę na [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda uczenia maszynowego `_trainedModel` zmiennej globalnej ( [ITransformer](xref:Microsoft.ML.ITransformer)) do wprowadzania funkcji i zwracają prognozy.</span><span class="sxs-lookup"><span data-stu-id="907f7-242">Notice the use of the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method of the machine learning `_trainedModel` global variable (an [ITransformer](xref:Microsoft.ML.ITransformer)) to input the features and return predictions.</span></span> <span data-ttu-id="907f7-243">Dodaj następujący kod do `Evaluate` metodę jako następny wiersz:</span><span class="sxs-lookup"><span data-stu-id="907f7-243">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

<span data-ttu-id="907f7-244">Następujące metryki są oceniane pod kątem wieloklasowej klasyfikacji:</span><span class="sxs-lookup"><span data-stu-id="907f7-244">The following metrics are evaluated for multiclass classification:</span></span>

* <span data-ttu-id="907f7-245">Dokładność Micro - każdej pary przykładową klasę przyczynia się jednakowo do metryki dokładności.</span><span class="sxs-lookup"><span data-stu-id="907f7-245">Micro Accuracy - Every sample-class pair contributes equally to the accuracy metric.</span></span>  <span data-ttu-id="907f7-246">Chcesz, aby dokładność Micro być jak zbliżone do wartości 1, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="907f7-246">You want Micro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="907f7-247">Dokładność — makro — każda klasa przyczynia się jednakowo do metryki dokładności.</span><span class="sxs-lookup"><span data-stu-id="907f7-247">Macro Accuracy - Every class contributes equally to the accuracy metric.</span></span> <span data-ttu-id="907f7-248">Moduł klasy są podane weight równe jako większych klas.</span><span class="sxs-lookup"><span data-stu-id="907f7-248">Minority classes are given equal weight as the larger classes.</span></span> <span data-ttu-id="907f7-249">Chcesz, aby dokładność — makro sposób maksymalnie zbliżony 1, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="907f7-249">You want Macro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="907f7-250">Dziennik utraty — zobacz [utraty dziennika](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="907f7-250">Log-loss - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="907f7-251">Ma dziennik utraty sposób maksymalnie zbliżony zero, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="907f7-251">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="907f7-252">Zmniejszenie dziennika utraty — zakresy z [-inf, 100], gdzie 100 to doskonałe prognoz i 0 wskazuje średnią prognozy.</span><span class="sxs-lookup"><span data-stu-id="907f7-252">Log-loss reduction - Ranges from [-inf, 100], where 100 is perfect predictions and 0 indicates mean predictions.</span></span> <span data-ttu-id="907f7-253">Chcesz, aby zmniejszenie dziennika utraty sposób maksymalnie zbliżony zero, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="907f7-253">You want Log-loss reduction to be as close to zero as possible.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="907f7-254">Wyświetlanie metryki dotyczące weryfikacji modelu</span><span class="sxs-lookup"><span data-stu-id="907f7-254">Displaying the metrics for model validation</span></span>

<span data-ttu-id="907f7-255">Użyj poniższego kodu, aby wyświetlić metryki, udostępnianie wyników, a następnie działanie na nich:</span><span class="sxs-lookup"><span data-stu-id="907f7-255">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

## <a name="deploy-and-predict-with-a-model"></a><span data-ttu-id="907f7-256">Wdrażanie i prognozowanie za pomocą modelu</span><span class="sxs-lookup"><span data-stu-id="907f7-256">Deploy and Predict with a model</span></span>

<span data-ttu-id="907f7-257">Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `Evaluate` wywołania metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="907f7-257">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

<span data-ttu-id="907f7-258">Tworzenie `PredictIssue` metody tuż za `Evaluate` — metoda (i tuż przed `SaveModelAsFile` metoda), używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="907f7-258">Create the `PredictIssue` method, just after the `Evaluate` method (and just before the `SaveModelAsFile` method), using the following code:</span></span>

```csharp
private static void PredictIssue()
{

}
```

<span data-ttu-id="907f7-259">`PredictIssue` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="907f7-259">The `PredictIssue` method executes the following tasks:</span></span>

* <span data-ttu-id="907f7-260">Tworzy jeden problem danych testowych.</span><span class="sxs-lookup"><span data-stu-id="907f7-260">Creates a single issue of test data.</span></span>
* <span data-ttu-id="907f7-261">Prognozuje obszaru na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="907f7-261">Predicts Area based on test data.</span></span>
* <span data-ttu-id="907f7-262">Łączy w sobie testowanie, danych i prognoz dla raportowania.</span><span class="sxs-lookup"><span data-stu-id="907f7-262">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="907f7-263">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="907f7-263">Displays the predicted results.</span></span>

<span data-ttu-id="907f7-264">Dodaj problem w usłudze GitHub do testowania uczonego modelu prognozowania w `Predict` metody przez utworzenie wystąpienia `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="907f7-264">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[AddTestIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

<span data-ttu-id="907f7-265">Tak jak wcześniej, Utwórz `PredictionEngine` wystąpienia w następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="907f7-265">As you did previously, create a `PredictionEngine` instance with the following code:</span></span>

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]
  
<span data-ttu-id="907f7-266">Użyj `PredictionEngine` do prognozowania etykiety GitHub powierzchni, dodając następujący kod do `PredictIssue` metoda prognozowania:</span><span class="sxs-lookup"><span data-stu-id="907f7-266">Use the `PredictionEngine` to predict the Area GitHub label by adding the following code to the `PredictIssue` method for the prediction:</span></span>

[!code-csharp[PredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a><span data-ttu-id="907f7-267">Przy użyciu załadować modelu do prognozowania</span><span class="sxs-lookup"><span data-stu-id="907f7-267">Using the loaded model for prediction</span></span>

<span data-ttu-id="907f7-268">Wyświetlanie `Area` celu kategoryzowania problem i odpowiednie do nich działanie na nim.</span><span class="sxs-lookup"><span data-stu-id="907f7-268">Display `Area` in order to categorize the issue and act on it accordingly.</span></span> <span data-ttu-id="907f7-269">Tworzenie ekranu wyników za pomocą następujących <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:</span><span class="sxs-lookup"><span data-stu-id="907f7-269">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayResults](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a><span data-ttu-id="907f7-270">Wyniki</span><span class="sxs-lookup"><span data-stu-id="907f7-270">Results</span></span>

<span data-ttu-id="907f7-271">Wyniki powinny być podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="907f7-271">Your results should be similar to the following.</span></span> <span data-ttu-id="907f7-272">Ponieważ przetwarza potoku, wyświetla komunikaty.</span><span class="sxs-lookup"><span data-stu-id="907f7-272">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="907f7-273">Może zostać wyświetlony ostrzeżenia lub komunikaty przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="907f7-273">You may see warnings, or processing messages.</span></span> <span data-ttu-id="907f7-274">Te komunikaty zostały usunięte z następujących wyników dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="907f7-274">These messages have been removed from the following results for clarity.</span></span>

```console
=============== Single Prediction just-trained-model - Result: area-System.Net ===============
*************************************************************************************************************
*       Metrics for Multi-class Classification model - Test Data
*------------------------------------------------------------------------------------------------------------
*       MicroAccuracy:    0.738
*       MacroAccuracy:    0.668
*       LogLoss:          .919
*       LogLossReduction: .643
*************************************************************************************************************
=============== Single Prediction - Result: area-System.Data ===============
```

<span data-ttu-id="907f7-275">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="907f7-275">Congratulations!</span></span> <span data-ttu-id="907f7-276">Teraz został pomyślnie skompilowany usługi machine learning model do klasyfikowania i prognozowanie etykieta obszar problemu w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="907f7-276">You've now successfully built a machine learning model for classifying and predicting an Area label for a GitHub issue.</span></span> <span data-ttu-id="907f7-277">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="907f7-277">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="907f7-278">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="907f7-278">Next steps</span></span>

<span data-ttu-id="907f7-279">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="907f7-279">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="907f7-280">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="907f7-280">Prepare your data</span></span>
> * <span data-ttu-id="907f7-281">Przekształcanie danych</span><span class="sxs-lookup"><span data-stu-id="907f7-281">Transform the data</span></span>
> * <span data-ttu-id="907f7-282">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="907f7-282">Train the model</span></span>
> * <span data-ttu-id="907f7-283">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="907f7-283">Evaluate the model</span></span>
> * <span data-ttu-id="907f7-284">Prognozowanie za pomocą uczonego modelu</span><span class="sxs-lookup"><span data-stu-id="907f7-284">Predict with the trained model</span></span>
> * <span data-ttu-id="907f7-285">Wdrażanie i przewidywanie załadować modelu</span><span class="sxs-lookup"><span data-stu-id="907f7-285">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="907f7-286">Przejdź do następnego samouczka, aby dowiedzieć się więcej</span><span class="sxs-lookup"><span data-stu-id="907f7-286">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="907f7-287">Taxi Fare Predictor</span><span class="sxs-lookup"><span data-stu-id="907f7-287">Taxi Fare Predictor</span></span>](taxi-fare.md)
