---
title: 'Samouczek: Kategoryzowanie problemów z obsługą — klasyfikacja wieloklasowa'
description: Dowiedz się, jak używać ML.NET w scenariuszu klasyfikacji wieloklasowej do klasyfikowania problemów z usługiGitHub w celu przypisania ich do danego obszaru.
ms.date: 01/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 50980cd933054825bf21f955b0341dd8e66f3e62
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78239940"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-mlnet"></a><span data-ttu-id="64ca9-103">Samouczek: Kategoryzowanie problemów z obsługą przy użyciu klasyfikacji wieloklasowej z ML.NET</span><span class="sxs-lookup"><span data-stu-id="64ca9-103">Tutorial: Categorize support issues using multiclass classification with ML.NET</span></span>

<span data-ttu-id="64ca9-104">Ten przykładowy samouczek ilustruje użycie ML.NET do utworzenia klasyfikatora problemów usługi GitHub w celu nauczenia modelu, który klasyfikuje i przewiduje etykietę Obszar dla problemu z usługą GitHub za pośrednictwem aplikacji konsoli .NET Core przy użyciu języka C# w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="64ca9-104">This sample tutorial illustrates using ML.NET to create a GitHub issue classifier to train a model that classifies and predicts the Area label for a GitHub issue via a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="64ca9-105">Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="64ca9-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="64ca9-106">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="64ca9-106">Prepare your data</span></span>
> * <span data-ttu-id="64ca9-107">Przekształcanie danych</span><span class="sxs-lookup"><span data-stu-id="64ca9-107">Transform the data</span></span>
> * <span data-ttu-id="64ca9-108">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="64ca9-108">Train the model</span></span>
> * <span data-ttu-id="64ca9-109">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="64ca9-109">Evaluate the model</span></span>
> * <span data-ttu-id="64ca9-110">Przewidywanie z przeszkolony model</span><span class="sxs-lookup"><span data-stu-id="64ca9-110">Predict with the trained model</span></span>
> * <span data-ttu-id="64ca9-111">Wdrażanie i przewidywanie przy załadowanym modelu</span><span class="sxs-lookup"><span data-stu-id="64ca9-111">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="64ca9-112">Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification)</span><span class="sxs-lookup"><span data-stu-id="64ca9-112">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="64ca9-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="64ca9-113">Prerequisites</span></span>

* <span data-ttu-id="64ca9-114">[Visual Studio 2017 w wersji 15.6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem ".NET Core programistorna wieloplatformowa".</span><span class="sxs-lookup"><span data-stu-id="64ca9-114">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="64ca9-115">[Plik rozdzielony przez kartę Github (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span><span class="sxs-lookup"><span data-stu-id="64ca9-115">The [Github issues tab separated file (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span></span>
* <span data-ttu-id="64ca9-116">[Github problemy test karty oddzielone pliku (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span><span class="sxs-lookup"><span data-stu-id="64ca9-116">The [Github issues test tab separated file (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="64ca9-117">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="64ca9-117">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="64ca9-118">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="64ca9-118">Create a project</span></span>

1. <span data-ttu-id="64ca9-119">Otwórz program Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="64ca9-119">Open Visual Studio 2017.</span></span> <span data-ttu-id="64ca9-120">Wybierz **pozycję Plik** > **nowy** > **projekt** z paska menu.</span><span class="sxs-lookup"><span data-stu-id="64ca9-120">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="64ca9-121">W oknie dialogowym **Nowy projekt** wybierz węzeł **Visual C#,** po którym następuje węzeł **.NET Core.**</span><span class="sxs-lookup"><span data-stu-id="64ca9-121">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="64ca9-122">Następnie wybierz szablon projektu **aplikacji konsoli (.NET Core).**</span><span class="sxs-lookup"><span data-stu-id="64ca9-122">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="64ca9-123">W polu tekstowym **Nazwa** wpisz "GitHubIssueClassification", a następnie wybierz przycisk **OK.**</span><span class="sxs-lookup"><span data-stu-id="64ca9-123">In the **Name** text box, type "GitHubIssueClassification" and then select the **OK** button.</span></span>

2. <span data-ttu-id="64ca9-124">Utwórz katalog o nazwie *Dane* w projekcie, aby zapisać pliki zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="64ca9-124">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="64ca9-125">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj** > **nowy folder**.</span><span class="sxs-lookup"><span data-stu-id="64ca9-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="64ca9-126">Wpisz "Dane" i naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="64ca9-126">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="64ca9-127">Utwórz katalog o nazwie *Modele* w projekcie, aby zapisać model:</span><span class="sxs-lookup"><span data-stu-id="64ca9-127">Create a directory named *Models* in your project to save your model:</span></span>

    <span data-ttu-id="64ca9-128">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj** > **nowy folder**.</span><span class="sxs-lookup"><span data-stu-id="64ca9-128">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="64ca9-129">Wpisz "Modele" i naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="64ca9-129">Type "Models" and hit Enter.</span></span>

4. <span data-ttu-id="64ca9-130">Zainstaluj **pakiet Microsoft.ML NuGet:**</span><span class="sxs-lookup"><span data-stu-id="64ca9-130">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="64ca9-131">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **polecenie Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="64ca9-131">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="64ca9-132">Wybierz "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj **Microsoft.ML** i wybierz przycisk **Zainstaluj.**</span><span class="sxs-lookup"><span data-stu-id="64ca9-132">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="64ca9-133">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z warunkami licencyjnymi dla wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="64ca9-133">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="64ca9-134">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="64ca9-134">Prepare your data</span></span>

1. <span data-ttu-id="64ca9-135">Pobierz [zestawy danych issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) i [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) i zapisz je w folderze *Data* utworzonym wcześniej.</span><span class="sxs-lookup"><span data-stu-id="64ca9-135">Download the [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) and the [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="64ca9-136">Pierwszy zestaw danych szkoli model uczenia maszynowego, a drugi może służyć do oceny, jak dokładny jest model.</span><span class="sxs-lookup"><span data-stu-id="64ca9-136">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="64ca9-137">W Eksploratorze rozwiązań \*kliknij prawym przyciskiem myszy każdy z plików .tsv i wybierz **polecenie Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="64ca9-137">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="64ca9-138">W obszarze **Zaawansowane**zmień wartość **kopiuj do katalogu wyjściowego,** aby **skopiować, jeśli nowsza**.</span><span class="sxs-lookup"><span data-stu-id="64ca9-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="64ca9-139">Tworzenie klas i definiowanie ścieżek</span><span class="sxs-lookup"><span data-stu-id="64ca9-139">Create classes and define paths</span></span>

<span data-ttu-id="64ca9-140">Dodaj następujące `using` dodatkowe instrukcje do górnej części pliku *Program.cs:*</span><span class="sxs-lookup"><span data-stu-id="64ca9-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddUsings)]

<span data-ttu-id="64ca9-141">Utwórz trzy pola globalne, aby pomieścić ścieżki do ostatnio pobranych plików, oraz zmienne globalne dla `MLContext`,`DataView`i `PredictionEngine`:</span><span class="sxs-lookup"><span data-stu-id="64ca9-141">Create three global fields to hold the paths to the recently downloaded files, and global variables for the `MLContext`,`DataView`, and `PredictionEngine`:</span></span>

* <span data-ttu-id="64ca9-142">`_trainDataPath`ma ścieżkę do zestawu danych używanego do nauczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="64ca9-142">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="64ca9-143">`_testDataPath`ma ścieżkę do zestawu danych używanego do oceny modelu.</span><span class="sxs-lookup"><span data-stu-id="64ca9-143">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="64ca9-144">`_modelPath`ma ścieżkę, w której jest zapisywany trenowany model.</span><span class="sxs-lookup"><span data-stu-id="64ca9-144">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="64ca9-145">`_mlContext`<xref:Microsoft.ML.MLContext> jest, który zapewnia kontekst przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="64ca9-145">`_mlContext` is the <xref:Microsoft.ML.MLContext> that provides processing context.</span></span>
* <span data-ttu-id="64ca9-146">`_trainingDataView`jest <xref:Microsoft.ML.IDataView> używany do przetwarzania zestawu danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="64ca9-146">`_trainingDataView` is the <xref:Microsoft.ML.IDataView> used to process the training dataset.</span></span>
* <span data-ttu-id="64ca9-147">`_predEngine`jest <xref:Microsoft.ML.PredictionEngine%602> używany dla pojedynczych prognoz.</span><span class="sxs-lookup"><span data-stu-id="64ca9-147">`_predEngine` is the <xref:Microsoft.ML.PredictionEngine%602> used for single predictions.</span></span>

<span data-ttu-id="64ca9-148">Dodaj następujący kod do wiersza `Main` tuż nad metodą, aby określić te ścieżki i inne zmienne:</span><span class="sxs-lookup"><span data-stu-id="64ca9-148">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="64ca9-149">Utwórz niektóre klasy dla danych wejściowych i prognoz.</span><span class="sxs-lookup"><span data-stu-id="64ca9-149">Create some classes for your input data and predictions.</span></span> <span data-ttu-id="64ca9-150">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="64ca9-150">Add a new class to your project:</span></span>

1. <span data-ttu-id="64ca9-151">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="64ca9-151">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="64ca9-152">W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *GitHubIssueData.cs*.</span><span class="sxs-lookup"><span data-stu-id="64ca9-152">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *GitHubIssueData.cs*.</span></span> <span data-ttu-id="64ca9-153">Następnie wybierz przycisk **Dodaj.**</span><span class="sxs-lookup"><span data-stu-id="64ca9-153">Then, select the **Add** button.</span></span>

    <span data-ttu-id="64ca9-154">Plik *GitHubIssueData.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="64ca9-154">The *GitHubIssueData.cs* file opens in the code editor.</span></span> <span data-ttu-id="64ca9-155">Dodaj następującą `using` instrukcję do górnej części *GitHubIssueData.cs:*</span><span class="sxs-lookup"><span data-stu-id="64ca9-155">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/GitHubIssueData.cs#AddUsings)]

<span data-ttu-id="64ca9-156">Usuń istniejącą definicję klasy i dodaj następujący `GitHubIssue` `IssuePrediction`kod, który ma dwie klasy i , do *pliku GitHubIssueData.cs:*</span><span class="sxs-lookup"><span data-stu-id="64ca9-156">Remove the existing class definition and add the following code, which has two classes `GitHubIssue` and `IssuePrediction`, to the *GitHubIssueData.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/GitHubIssueData.cs#DeclareTypes)]

<span data-ttu-id="64ca9-157">Jest `label` to kolumna, którą chcesz przewidzieć.</span><span class="sxs-lookup"><span data-stu-id="64ca9-157">The `label` is the column you want to predict.</span></span> <span data-ttu-id="64ca9-158">Zidentyfikowane `Features` są dane wejściowe, które dajesz modelu do przewidywania Label.</span><span class="sxs-lookup"><span data-stu-id="64ca9-158">The identified `Features` are the inputs you give the model to predict the Label.</span></span>

<span data-ttu-id="64ca9-159">Użyj [LoadColumnAttribute,](xref:Microsoft.ML.Data.LoadColumnAttribute) aby określić indeksy kolumn źródłowych w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="64ca9-159">Use the [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="64ca9-160">`GitHubIssue`jest klasą wejściowego zestawu <xref:System.String> danych i ma następujące pola:</span><span class="sxs-lookup"><span data-stu-id="64ca9-160">`GitHubIssue` is the input dataset class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="64ca9-161">pierwsza kolumna `ID` (identyfikator problemu GitHub)</span><span class="sxs-lookup"><span data-stu-id="64ca9-161">the first column `ID` (GitHub Issue ID)</span></span>
* <span data-ttu-id="64ca9-162">druga kolumna `Area` (prognoza szkolenia)</span><span class="sxs-lookup"><span data-stu-id="64ca9-162">the second column `Area` (the prediction for training)</span></span>
* <span data-ttu-id="64ca9-163">w trzeciej `Title` kolumnie (tytuł wydania GitHub) jest pierwszą `feature` używaną do przewidywania`Area`</span><span class="sxs-lookup"><span data-stu-id="64ca9-163">the third column `Title` (GitHub issue title) is the first `feature` used for predicting the `Area`</span></span>
* <span data-ttu-id="64ca9-164">czwarta kolumna `Description` jest `feature` drugą używaną do przewidywania`Area`</span><span class="sxs-lookup"><span data-stu-id="64ca9-164">the fourth column  `Description` is the second `feature` used for predicting the `Area`</span></span>

<span data-ttu-id="64ca9-165">`IssuePrediction`jest klasą używaną do przewidywania po przeszkoloniu modelu.</span><span class="sxs-lookup"><span data-stu-id="64ca9-165">`IssuePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="64ca9-166">Ma jeden `string` (`Area`) `PredictedLabel` `ColumnName` i atrybut.</span><span class="sxs-lookup"><span data-stu-id="64ca9-166">It has a single `string` (`Area`) and a `PredictedLabel` `ColumnName` attribute.</span></span>  <span data-ttu-id="64ca9-167">Jest `PredictedLabel` używany podczas przewidywania i oceny.</span><span class="sxs-lookup"><span data-stu-id="64ca9-167">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="64ca9-168">Do oceny dane wejściowe z danymi treningowymi, przewidywane wartości i model są używane.</span><span class="sxs-lookup"><span data-stu-id="64ca9-168">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="64ca9-169">Wszystkie operacje ML.NET rozpoczynają się w klasie [MLContext.](xref:Microsoft.ML.MLContext)</span><span class="sxs-lookup"><span data-stu-id="64ca9-169">All ML.NET operations start in the [MLContext](xref:Microsoft.ML.MLContext) class.</span></span> <span data-ttu-id="64ca9-170">Inicjowanie `mlContext` tworzy nowe środowisko ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="64ca9-170">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="64ca9-171">Jest to podobne, koncepcyjnie, `DBContext` `Entity Framework`do w .</span><span class="sxs-lookup"><span data-stu-id="64ca9-171">It's similar, conceptually, to `DBContext` in `Entity Framework`.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="64ca9-172">Inicjowanie zmiennych w main</span><span class="sxs-lookup"><span data-stu-id="64ca9-172">Initialize variables in Main</span></span>

<span data-ttu-id="64ca9-173">Inicjuj zmienną `_mlContext` globalną `MLContext` z nowym`seed: 0`wystąpieniem z losowym materiałem siewnym ( ) dla powtarzalnych/deterministycznych wyników w wielu szkoleniach.</span><span class="sxs-lookup"><span data-stu-id="64ca9-173">Initialize the `_mlContext` global variable  with a new instance of `MLContext` with a random seed (`seed: 0`) for repeatable/deterministic results across multiple trainings.</span></span>  <span data-ttu-id="64ca9-174">Zastąp `Console.WriteLine("Hello World!")` wiersz następującym `Main` kodem w metodzie:</span><span class="sxs-lookup"><span data-stu-id="64ca9-174">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a><span data-ttu-id="64ca9-175">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="64ca9-175">Load the data</span></span>

<span data-ttu-id="64ca9-176">ML.NET używa [klasy IDataView](xref:Microsoft.ML.IDataView) jako elastycznego i wydajnego sposobu opisywania danych liczbowych lub tekstowych.</span><span class="sxs-lookup"><span data-stu-id="64ca9-176">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="64ca9-177">`IDataView`można ładować pliki tekstowe lub w czasie rzeczywistym (na przykład bazy danych SQL lub pliki dziennika).</span><span class="sxs-lookup"><span data-stu-id="64ca9-177">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span>

<span data-ttu-id="64ca9-178">Aby zainicjować i `_trainingDataView` załadować zmienną globalną, aby użyć jej w `mlContext` potoku, dodaj następujący kod po inicjalizacji:</span><span class="sxs-lookup"><span data-stu-id="64ca9-178">To initialize and load the `_trainingDataView` global variable in order to use it for the pipeline, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[LoadTrainData](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#LoadTrainData)]

<span data-ttu-id="64ca9-179">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczyty w pliku.</span><span class="sxs-lookup"><span data-stu-id="64ca9-179">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="64ca9-180">Przyjmuje zmienne ścieżki danych i `IDataView`zwraca .</span><span class="sxs-lookup"><span data-stu-id="64ca9-180">It takes in the data path variables and returns an `IDataView`.</span></span>

<span data-ttu-id="64ca9-181">Dodaj następujące jako następny wiersz kodu `Main` w metodzie:</span><span class="sxs-lookup"><span data-stu-id="64ca9-181">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallProcessData](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallProcessData)]

<span data-ttu-id="64ca9-182">Metoda `ProcessData` wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="64ca9-182">The `ProcessData` method executes the following tasks:</span></span>

* <span data-ttu-id="64ca9-183">Wyodrębnia i przekształca dane.</span><span class="sxs-lookup"><span data-stu-id="64ca9-183">Extracts and transforms the data.</span></span>
* <span data-ttu-id="64ca9-184">Zwraca potok przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="64ca9-184">Returns the processing pipeline.</span></span>

<span data-ttu-id="64ca9-185">Utwórz `ProcessData` metodę, tuż `Main` po tej metodzie, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="64ca9-185">Create the `ProcessData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="64ca9-186">Wyodrębnianie funkcji i przekształcanie danych</span><span class="sxs-lookup"><span data-stu-id="64ca9-186">Extract Features and transform the data</span></span>

<span data-ttu-id="64ca9-187">`GitHubIssue`Aby przewidzieć etykietę Area GitHub dla , użyj metody [MapValueToKey(),](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) aby przekształcić `Label` `Area` kolumnę w kolumnę typu klucza numerycznego (format akceptowany przez algorytmy klasyfikacji) i dodać ją jako nową kolumnę zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="64ca9-187">As you want to predict the Area GitHub label for a `GitHubIssue`, use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform the `Area` column into a numeric key type `Label` column (a format accepted by classification algorithms) and add it as a new dataset column:</span></span>

[!code-csharp[MapValueToKey](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#MapValueToKey)]

<span data-ttu-id="64ca9-188">`mlContext.Transforms.Text.FeaturizeText` Następnie wywołanie, które przekształca`Title` `Description`kolumny tekstowe ( i ) `TitleFeaturized` w `DescriptionFeaturized`wektor numeryczny dla każdego wywoływanego i .</span><span class="sxs-lookup"><span data-stu-id="64ca9-188">Next, call `mlContext.Transforms.Text.FeaturizeText` which transforms the text (`Title` and `Description`) columns into a numeric vector for each called `TitleFeaturized` and `DescriptionFeaturized`.</span></span> <span data-ttu-id="64ca9-189">Dołącz featurization dla obu kolumn do potoku z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="64ca9-189">Append the featurization for both columns to the pipeline with the following code:</span></span>

[!code-csharp[FeaturizeText](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#FeaturizeText)]

<span data-ttu-id="64ca9-190">Ostatni krok w przygotowaniu danych łączy wszystkie kolumny operacji w kolumnie **Funkcje** przy użyciu metody [Concatenate().](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A)</span><span class="sxs-lookup"><span data-stu-id="64ca9-190">The last step in data preparation combines all of the feature columns into the **Features** column using the [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) method.</span></span> <span data-ttu-id="64ca9-191">Domyślnie algorytm uczenia się przetwarza tylko funkcje z **kolumny Funkcje.**</span><span class="sxs-lookup"><span data-stu-id="64ca9-191">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="64ca9-192">Dołącz tę transformację do potoku za pomocą następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="64ca9-192">Append this transformation to the pipeline with the following code:</span></span>

[!code-csharp[Concatenate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Concatenate)]

 <span data-ttu-id="64ca9-193">Następnie dołącz a <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> do buforowania DataView tak po wielokrotnym itetensyjności danych przy użyciu pamięci podręcznej może uzyskać lepszą wydajność, jak w przypadku następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="64ca9-193">Next, append a <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> to cache the DataView so when you iterate over the data multiple times using the cache might get better performance, as with the following code:</span></span>

[!code-csharp[AppendCache](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AppendCache)]

> [!WARNING]
> <span data-ttu-id="64ca9-194">Użyj appendCacheCheckpoint dla małych/średnich zestawów danych, aby obniżyć czas szkolenia.</span><span class="sxs-lookup"><span data-stu-id="64ca9-194">Use AppendCacheCheckpoint for small/medium datasets to lower training time.</span></span> <span data-ttu-id="64ca9-195">NIE używaj go (usuń . AppendCacheCheckpoint()) podczas obsługi bardzo dużych zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="64ca9-195">Do NOT use it (remove .AppendCacheCheckpoint()) when handling very large datasets.</span></span>

<span data-ttu-id="64ca9-196">Zwraca potoku na końcu `ProcessData` metody.</span><span class="sxs-lookup"><span data-stu-id="64ca9-196">Return the pipeline at the end of the `ProcessData` method.</span></span>

[!code-csharp[ReturnPipeline](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#ReturnPipeline)]

<span data-ttu-id="64ca9-197">Ten krok obsługuje wstępne przetwarzanie/featurization.</span><span class="sxs-lookup"><span data-stu-id="64ca9-197">This step handles preprocessing/featurization.</span></span> <span data-ttu-id="64ca9-198">Korzystanie z dodatkowych składników dostępnych w ML.NET może umożliwić lepsze wyniki w modelu.</span><span class="sxs-lookup"><span data-stu-id="64ca9-198">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="build-and-train-the-model"></a><span data-ttu-id="64ca9-199">Zbuduj i wytrenuj model</span><span class="sxs-lookup"><span data-stu-id="64ca9-199">Build and train the model</span></span>

<span data-ttu-id="64ca9-200">Dodaj następujące wywołanie `BuildAndTrainModel`do metody jako następny `Main` wiersz kodu w metodzie:</span><span class="sxs-lookup"><span data-stu-id="64ca9-200">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="64ca9-201">Metoda `BuildAndTrainModel` wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="64ca9-201">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="64ca9-202">Tworzy klasy algorytmu szkolenia.</span><span class="sxs-lookup"><span data-stu-id="64ca9-202">Creates the training algorithm class.</span></span>
* <span data-ttu-id="64ca9-203">Trenuje model.</span><span class="sxs-lookup"><span data-stu-id="64ca9-203">Trains the model.</span></span>
* <span data-ttu-id="64ca9-204">Prognozuje obszar na podstawie danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="64ca9-204">Predicts area based on training data.</span></span>
* <span data-ttu-id="64ca9-205">Zwraca model.</span><span class="sxs-lookup"><span data-stu-id="64ca9-205">Returns the model.</span></span>

<span data-ttu-id="64ca9-206">Utwórz `BuildAndTrainModel` metodę, tuż `Main` po tej metodzie, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="64ca9-206">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a><span data-ttu-id="64ca9-207">Zadanie klasyfikacji – informacje</span><span class="sxs-lookup"><span data-stu-id="64ca9-207">About the classification task</span></span>

<span data-ttu-id="64ca9-208">Klasyfikacja jest zadaniem uczenia maszynowego, które używa danych do **określenia** kategorii, typu lub klasy elementu lub wiersza danych i często jest jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="64ca9-208">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data and is frequently one of the following types:</span></span>

* <span data-ttu-id="64ca9-209">Binarne: A lub B.</span><span class="sxs-lookup"><span data-stu-id="64ca9-209">Binary: either A or B.</span></span>
* <span data-ttu-id="64ca9-210">Wieloklasowa: wiele kategorii, które można przewidzieć przy użyciu jednego modelu.</span><span class="sxs-lookup"><span data-stu-id="64ca9-210">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="64ca9-211">Dla tego typu problemu należy użyć algorytmu uczenia się klasyfikacji wieloklasowej, ponieważ przewidywanie kategorii problemów może być jedną z wielu kategorii (wieloklasowych), a nie tylko dwie (binarne).</span><span class="sxs-lookup"><span data-stu-id="64ca9-211">For this type of problem, use a Multiclass classification learning algorithm, since your issue category prediction can be one of multiple categories (multiclass) rather than just two (binary).</span></span>

<span data-ttu-id="64ca9-212">Dołącz algorytm uczenia maszynowego do definicji transformacji danych, dodając następujące wierszy kodu w: `BuildAndTrainModel()`</span><span class="sxs-lookup"><span data-stu-id="64ca9-212">Append the machine learning algorithm to the data transformation definitions by adding the following as the first line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddTrainer](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddTrainer)]

<span data-ttu-id="64ca9-213">[SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) jest algorytm szkolenia klasyfikacji wieloklasowej.</span><span class="sxs-lookup"><span data-stu-id="64ca9-213">The [SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) is your multiclass classification training algorithm.</span></span> <span data-ttu-id="64ca9-214">Jest to dołączone `pipeline` do i akceptuje `Title` featurized i `Description` (`Features`) i parametry `Label` wejściowe, aby dowiedzieć się z danych historycznych.</span><span class="sxs-lookup"><span data-stu-id="64ca9-214">This is appended to the `pipeline` and accepts the featurized `Title` and `Description` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="64ca9-215">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="64ca9-215">Train the model</span></span>

<span data-ttu-id="64ca9-216">Dopasuj `splitTrainSet` model do danych i zwróć uczonego modelu, `BuildAndTrainModel()` dodając następujące wierszy kodu w metodzie:</span><span class="sxs-lookup"><span data-stu-id="64ca9-216">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#TrainModel)]

<span data-ttu-id="64ca9-217">Metoda `Fit()`szkoli model, przekształcając zestaw danych i stosując szkolenie.</span><span class="sxs-lookup"><span data-stu-id="64ca9-217">The `Fit()`method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="64ca9-218">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest interfejs emanujący interfejsu API wygody, który umożliwia przekazywanie, a następnie wykonywanie przewidywanie na pojedyncze wystąpienie danych.</span><span class="sxs-lookup"><span data-stu-id="64ca9-218">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span> <span data-ttu-id="64ca9-219">Dodaj to jako następny `BuildAndTrainModel()` wiersz w metodzie:</span><span class="sxs-lookup"><span data-stu-id="64ca9-219">Add this as the next line in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[CreatePredictionEngine1](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a><span data-ttu-id="64ca9-220">Przewidywanie z przeszkolony model</span><span class="sxs-lookup"><span data-stu-id="64ca9-220">Predict with the trained model</span></span>

<span data-ttu-id="64ca9-221">Dodaj problem GitHub, aby przetestować przewidywanie `Predict` uczonego modelu `GitHubIssue`w metodzie, tworząc wystąpienie:</span><span class="sxs-lookup"><span data-stu-id="64ca9-221">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[CreateTestIssue1](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreateTestIssue1)]

<span data-ttu-id="64ca9-222">Użyj [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) funkcja sprawia, że przewidywanie w jednym wierszu danych:</span><span class="sxs-lookup"><span data-stu-id="64ca9-222">Use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

[!code-csharp[Predict](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a><span data-ttu-id="64ca9-223">Korzystanie z modelu: wyniki przewidywania</span><span class="sxs-lookup"><span data-stu-id="64ca9-223">Using the model: prediction results</span></span>

<span data-ttu-id="64ca9-224">Wyświetl `GitHubIssue` i `Area` odpowiednie przewidywanie etykiet, aby udostępnić wyniki i odpowiednio je podjąć.</span><span class="sxs-lookup"><span data-stu-id="64ca9-224">Display `GitHubIssue` and corresponding `Area` label prediction in order to share the results and act on them accordingly.</span></span>  <span data-ttu-id="64ca9-225">Utwórz wyświetlanie wyników przy <xref:System.Console.WriteLine?displayProperty=nameWithType> użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="64ca9-225">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="64ca9-226">Powrót modelu przeszkolonego do wykorzystania do oceny</span><span class="sxs-lookup"><span data-stu-id="64ca9-226">Return the model trained to use for evaluation</span></span>

<span data-ttu-id="64ca9-227">Zwraca model na końcu `BuildAndTrainModel` metody.</span><span class="sxs-lookup"><span data-stu-id="64ca9-227">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a><span data-ttu-id="64ca9-228">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="64ca9-228">Evaluate the model</span></span>

<span data-ttu-id="64ca9-229">Teraz, gdy utworzono i przeszkolony model, należy ocenić go za pomocą innego zestawu danych dla zapewnienia jakości i sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="64ca9-229">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="64ca9-230">W `Evaluate` metodzie model utworzony `BuildAndTrainModel` w jest przekazywana do oceny.</span><span class="sxs-lookup"><span data-stu-id="64ca9-230">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="64ca9-231">Utwórz `Evaluate` metodę, `BuildAndTrainModel`zaraz po , jak w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="64ca9-231">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate(DataViewSchema trainingDataViewSchema)
{

}
```

<span data-ttu-id="64ca9-232">Metoda `Evaluate` wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="64ca9-232">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="64ca9-233">Ładuje testowy zestaw danych.</span><span class="sxs-lookup"><span data-stu-id="64ca9-233">Loads the test dataset.</span></span>
* <span data-ttu-id="64ca9-234">Tworzy wieloklasowego oceniającego.</span><span class="sxs-lookup"><span data-stu-id="64ca9-234">Creates the multiclass evaluator.</span></span>
* <span data-ttu-id="64ca9-235">Ocenia model i tworzenie metryk.</span><span class="sxs-lookup"><span data-stu-id="64ca9-235">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="64ca9-236">Wyświetla metryki.</span><span class="sxs-lookup"><span data-stu-id="64ca9-236">Displays the metrics.</span></span>

<span data-ttu-id="64ca9-237">Dodaj wywołanie do nowej `Main` metody z metody, bezpośrednio w wywołaniu `BuildAndTrainModel` metody, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="64ca9-237">Add a call to the new method from the `Main` method, right under the `BuildAndTrainModel` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallEvaluate)]

<span data-ttu-id="64ca9-238">Podobnie jak poprzednio w przypadku zestawu danych szkoleniowych, załaduj `Evaluate` testowy zestaw danych, dodając do metody następujący kod:</span><span class="sxs-lookup"><span data-stu-id="64ca9-238">As you did previously with the training dataset, load the test dataset by adding the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#LoadTestDataset)]

<span data-ttu-id="64ca9-239">Metoda [Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) oblicza metryki jakości dla modelu przy użyciu określonego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="64ca9-239">The [Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) method computes the quality metrics for the model using the specified dataset.</span></span> <span data-ttu-id="64ca9-240">Zwraca <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> obiekt, który zawiera ogólne metryki obliczone przez oceniających klasyfikacji wieloklasowej.</span><span class="sxs-lookup"><span data-stu-id="64ca9-240">It returns a <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> object that contains the overall metrics computed by multiclass classification evaluators.</span></span>
<span data-ttu-id="64ca9-241">Aby wyświetlić metryki, aby określić jakość modelu, należy je najpierw uzyskać.</span><span class="sxs-lookup"><span data-stu-id="64ca9-241">To display the metrics to determine the quality of the model, you need to get them first.</span></span>
<span data-ttu-id="64ca9-242">Zwróć uwagę na użycie [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) `_trainedModel` metody zmiennej globalnej uczenia maszynowego [(ITransformer)](xref:Microsoft.ML.ITransformer)do wprowadzania funkcji i prognozy zwracania.</span><span class="sxs-lookup"><span data-stu-id="64ca9-242">Notice the use of the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method of the machine learning `_trainedModel` global variable (an [ITransformer](xref:Microsoft.ML.ITransformer)) to input the features and return predictions.</span></span> <span data-ttu-id="64ca9-243">Dodaj następujący kod `Evaluate` do metody jako następny wiersz:</span><span class="sxs-lookup"><span data-stu-id="64ca9-243">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[Evaluate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Evaluate)]

<span data-ttu-id="64ca9-244">Dla klasyfikacji wieloklasowej oceniane są następujące metryki:</span><span class="sxs-lookup"><span data-stu-id="64ca9-244">The following metrics are evaluated for multiclass classification:</span></span>

* <span data-ttu-id="64ca9-245">Mikrodokładność — każda para klas próbek przyczynia się w równym stopniu do metryki dokładności.</span><span class="sxs-lookup"><span data-stu-id="64ca9-245">Micro Accuracy - Every sample-class pair contributes equally to the accuracy metric.</span></span>  <span data-ttu-id="64ca9-246">Chcesz, aby mikrodokładność była jak najbardziej zbliżony do jednej.</span><span class="sxs-lookup"><span data-stu-id="64ca9-246">You want Micro Accuracy to be as close to one as possible.</span></span>

* <span data-ttu-id="64ca9-247">Dokładność makra — każda klasa przyczynia się w równym stopniu do metryki dokładności.</span><span class="sxs-lookup"><span data-stu-id="64ca9-247">Macro Accuracy - Every class contributes equally to the accuracy metric.</span></span> <span data-ttu-id="64ca9-248">Klasy mniejszościowe mają taką samą wagę jak większe klasy.</span><span class="sxs-lookup"><span data-stu-id="64ca9-248">Minority classes are given equal weight as the larger classes.</span></span> <span data-ttu-id="64ca9-249">Dokładność makr ma być jak najbardziej zbliżony do jednego.</span><span class="sxs-lookup"><span data-stu-id="64ca9-249">You want Macro Accuracy to be as close to one as possible.</span></span>

* <span data-ttu-id="64ca9-250">Log-loss - zobacz [Utrata dziennika](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="64ca9-250">Log-loss - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="64ca9-251">Chcesz, aby strata dziennika była jak najbardziej zbliżony do zera.</span><span class="sxs-lookup"><span data-stu-id="64ca9-251">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="64ca9-252">Redukcja strat dziennika — waha się od [-inf, 1.00], gdzie 1.00 jest doskonałe prognozy i 0 wskazuje średnie prognozy.</span><span class="sxs-lookup"><span data-stu-id="64ca9-252">Log-loss reduction - Ranges from [-inf, 1.00], where 1.00 is perfect predictions and 0 indicates mean predictions.</span></span> <span data-ttu-id="64ca9-253">Chcesz, aby redukcja strat dziennika była jak najbardziej zbliżony do jednego.</span><span class="sxs-lookup"><span data-stu-id="64ca9-253">You want Log-loss reduction to be as close to one as possible.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="64ca9-254">Wyświetlanie metryk do sprawdzania poprawności modelu</span><span class="sxs-lookup"><span data-stu-id="64ca9-254">Displaying the metrics for model validation</span></span>

<span data-ttu-id="64ca9-255">Użyj następującego kodu, aby wyświetlić metryki, udostępnić wyniki, a następnie działać na nich:</span><span class="sxs-lookup"><span data-stu-id="64ca9-255">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DisplayMetrics)]

### <a name="save-the-model-to-a-file"></a><span data-ttu-id="64ca9-256">Zapisywanie modelu w pliku</span><span class="sxs-lookup"><span data-stu-id="64ca9-256">Save the model to a file</span></span>

<span data-ttu-id="64ca9-257">Po zadowoleniu z modelu, zapisz go do pliku, aby przewidywań w późniejszym czasie lub w innej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="64ca9-257">Once satisfied with your model, save it to a file to make predictions at a later time or in another application.</span></span> <span data-ttu-id="64ca9-258">Dodaj następujący kod do metody `Evaluate`:</span><span class="sxs-lookup"><span data-stu-id="64ca9-258">Add the following code to the `Evaluate` method.</span></span>

[!code-csharp[SnippetCallSaveModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetCallSaveModel)]

<span data-ttu-id="64ca9-259">Utwórz `SaveModelAsFile` metodę `Evaluate` poniżej swojej metody.</span><span class="sxs-lookup"><span data-stu-id="64ca9-259">Create the `SaveModelAsFile` method below your `Evaluate` method.</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext,DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

<span data-ttu-id="64ca9-260">Dodaj następujący kod `SaveModelAsFile` do metody.</span><span class="sxs-lookup"><span data-stu-id="64ca9-260">Add the following code to your `SaveModelAsFile` method.</span></span> <span data-ttu-id="64ca9-261">Ten kod [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) używa metody do serializacji i przechowywania uczonego modelu jako pliku zip.</span><span class="sxs-lookup"><span data-stu-id="64ca9-261">This code uses the [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) method to serialize and store the trained model as a zip file.</span></span>

[!code-csharp[SnippetSaveModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetSaveModel)]

## <a name="deploy-and-predict-with-a-model"></a><span data-ttu-id="64ca9-262">Wdrażanie i przewidywanie za pomocą modelu</span><span class="sxs-lookup"><span data-stu-id="64ca9-262">Deploy and Predict with a model</span></span>

<span data-ttu-id="64ca9-263">Dodaj wywołanie do nowej `Main` metody z metody, bezpośrednio w wywołaniu `Evaluate` metody, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="64ca9-263">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredictIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallPredictIssue)]

<span data-ttu-id="64ca9-264">Utwórz `PredictIssue` metodę tuż `Evaluate` za metodą (i `SaveModelAsFile` tuż przed metodą), używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="64ca9-264">Create the `PredictIssue` method, just after the `Evaluate` method (and just before the `SaveModelAsFile` method), using the following code:</span></span>

```csharp
private static void PredictIssue()
{

}
```

<span data-ttu-id="64ca9-265">Metoda `PredictIssue` wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="64ca9-265">The `PredictIssue` method executes the following tasks:</span></span>

* <span data-ttu-id="64ca9-266">Ładuje zapisany model</span><span class="sxs-lookup"><span data-stu-id="64ca9-266">Loads the saved model</span></span>
* <span data-ttu-id="64ca9-267">Tworzy pojedynczy problem danych testowych.</span><span class="sxs-lookup"><span data-stu-id="64ca9-267">Creates a single issue of test data.</span></span>
* <span data-ttu-id="64ca9-268">Prognozuje obszar na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="64ca9-268">Predicts Area based on test data.</span></span>
* <span data-ttu-id="64ca9-269">Łączy dane testowe i prognozy dla raportowania.</span><span class="sxs-lookup"><span data-stu-id="64ca9-269">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="64ca9-270">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="64ca9-270">Displays the predicted results.</span></span>

<span data-ttu-id="64ca9-271">Załaduj zapisany model do aplikacji, `PredictIssue` dodając następujący kod do metody:</span><span class="sxs-lookup"><span data-stu-id="64ca9-271">Load the saved model into your application by adding the following code to the `PredictIssue` method:</span></span>

[!code-csharp[SnippetLoadModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetLoadModel)]

<span data-ttu-id="64ca9-272">Dodaj problem GitHub, aby przetestować przewidywanie `Predict` uczonego modelu `GitHubIssue`w metodzie, tworząc wystąpienie:</span><span class="sxs-lookup"><span data-stu-id="64ca9-272">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[AddTestIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddTestIssue)]

<span data-ttu-id="64ca9-273">Podobnie jak poprzednio, `PredictionEngine` utwórz wystąpienie z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="64ca9-273">As you did previously, create a `PredictionEngine` instance with the following code:</span></span>

[!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreatePredictionEngine)]

<span data-ttu-id="64ca9-274">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest interfejs emanujący interfejsu API wygody, który umożliwia wykonywanie przewidywanie na pojedyncze wystąpienie danych.</span><span class="sxs-lookup"><span data-stu-id="64ca9-274">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="64ca9-275">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny dla nici.</span><span class="sxs-lookup"><span data-stu-id="64ca9-275">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="64ca9-276">Dopuszczalne jest stosowanie w środowiskach jednowątkowych lub prototypowych.</span><span class="sxs-lookup"><span data-stu-id="64ca9-276">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="64ca9-277">Aby zwiększyć wydajność i bezpieczeństwo wątków `PredictionEnginePool` w środowiskach [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) produkcyjnych, należy użyć usługi, która tworzy obiektów [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do użycia w całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="64ca9-277">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="64ca9-278">Zobacz ten przewodnik, jak [ `PredictionEnginePool` używać w ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="64ca9-278">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="64ca9-279">`PredictionEnginePool`rozszerzenie usługi jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="64ca9-279">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="64ca9-280">Użyj `PredictionEngine` do przewidywania etykiety GitHub obszaru, dodając `PredictIssue` następujący kod do metody przewidywania:</span><span class="sxs-lookup"><span data-stu-id="64ca9-280">Use the `PredictionEngine` to predict the Area GitHub label by adding the following code to the `PredictIssue` method for the prediction:</span></span>

[!code-csharp[PredictIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a><span data-ttu-id="64ca9-281">Korzystanie z załadowanego modelu do przewidywania</span><span class="sxs-lookup"><span data-stu-id="64ca9-281">Using the loaded model for prediction</span></span>

<span data-ttu-id="64ca9-282">Wyświetl, `Area` aby kategoryzować problem i odpowiednio na niego działać.</span><span class="sxs-lookup"><span data-stu-id="64ca9-282">Display `Area` in order to categorize the issue and act on it accordingly.</span></span> <span data-ttu-id="64ca9-283">Utwórz wyświetlanie wyników przy <xref:System.Console.WriteLine?displayProperty=nameWithType> użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="64ca9-283">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayResults](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DisplayResults)]

## <a name="results"></a><span data-ttu-id="64ca9-284">Wyniki</span><span class="sxs-lookup"><span data-stu-id="64ca9-284">Results</span></span>

<span data-ttu-id="64ca9-285">Wyniki powinny być podobne do poniższych.</span><span class="sxs-lookup"><span data-stu-id="64ca9-285">Your results should be similar to the following.</span></span> <span data-ttu-id="64ca9-286">W procesach potoku wyświetla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="64ca9-286">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="64ca9-287">Mogą być wyświetlane ostrzeżenia lub wiadomości przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="64ca9-287">You may see warnings, or processing messages.</span></span> <span data-ttu-id="64ca9-288">Te komunikaty zostały usunięte z następujących wyników dla jasności.</span><span class="sxs-lookup"><span data-stu-id="64ca9-288">These messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="64ca9-289">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="64ca9-289">Congratulations!</span></span> <span data-ttu-id="64ca9-290">Teraz pomyślnie skonstruowano model uczenia maszynowego do klasyfikowania i przewidywania etykiety obszaru dla problemu z githubem.</span><span class="sxs-lookup"><span data-stu-id="64ca9-290">You've now successfully built a machine learning model for classifying and predicting an Area label for a GitHub issue.</span></span> <span data-ttu-id="64ca9-291">Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification)</span><span class="sxs-lookup"><span data-stu-id="64ca9-291">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="64ca9-292">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="64ca9-292">Next steps</span></span>

<span data-ttu-id="64ca9-293">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="64ca9-293">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="64ca9-294">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="64ca9-294">Prepare your data</span></span>
> * <span data-ttu-id="64ca9-295">Przekształcanie danych</span><span class="sxs-lookup"><span data-stu-id="64ca9-295">Transform the data</span></span>
> * <span data-ttu-id="64ca9-296">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="64ca9-296">Train the model</span></span>
> * <span data-ttu-id="64ca9-297">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="64ca9-297">Evaluate the model</span></span>
> * <span data-ttu-id="64ca9-298">Przewidywanie z przeszkolony model</span><span class="sxs-lookup"><span data-stu-id="64ca9-298">Predict with the trained model</span></span>
> * <span data-ttu-id="64ca9-299">Wdrażanie i przewidywanie przy załadowanym modelu</span><span class="sxs-lookup"><span data-stu-id="64ca9-299">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="64ca9-300">Przejdź do następnego samouczka, aby dowiedzieć się więcej</span><span class="sxs-lookup"><span data-stu-id="64ca9-300">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="64ca9-301">Przewidywanie taryfy taksówkowej</span><span class="sxs-lookup"><span data-stu-id="64ca9-301">Taxi Fare Predictor</span></span>](predict-prices.md)
