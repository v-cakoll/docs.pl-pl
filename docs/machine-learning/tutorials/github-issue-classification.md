---
title: 'Samouczek: kategoryzowanie problemów z pomocą techniczną — Klasyfikacja wieloklasowa'
description: Dowiedz się, jak używać ML.NET w scenariuszu klasyfikacji wieloklasowej do klasyfikowania problemów z usługi GitHub w celu przypisywania ich do danego obszaru.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: d4ab7f0fcc6b582e74f54d3f0e60032696277249
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051548"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-mlnet"></a><span data-ttu-id="ebc55-103">Samouczek: kategoryzowanie problemów pomocy technicznej przy użyciu klasyfikacji wieloklasowej z ML.NET</span><span class="sxs-lookup"><span data-stu-id="ebc55-103">Tutorial: Categorize support issues using multiclass classification with ML.NET</span></span>

<span data-ttu-id="ebc55-104">Ten przykładowy samouczek ilustruje użycie ML.NET do utworzenia klasyfikatora problemu w usłudze GitHub w celu uczenia modelu, który klasyfikuje i przewidywalnuje etykietę obszaru dla problemu usługi GitHub za pośrednictwem aplikacji konsolowej .NET Core przy użyciu języka C# w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ebc55-104">This sample tutorial illustrates using ML.NET to create a GitHub issue classifier to train a model that classifies and predicts the Area label for a GitHub issue via a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="ebc55-105">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="ebc55-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="ebc55-106">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="ebc55-106">Prepare your data</span></span>
> * <span data-ttu-id="ebc55-107">Przekształcanie danych</span><span class="sxs-lookup"><span data-stu-id="ebc55-107">Transform the data</span></span>
> * <span data-ttu-id="ebc55-108">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="ebc55-108">Train the model</span></span>
> * <span data-ttu-id="ebc55-109">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="ebc55-109">Evaluate the model</span></span>
> * <span data-ttu-id="ebc55-110">Przewidywanie przy użyciu przeszkolonego modelu</span><span class="sxs-lookup"><span data-stu-id="ebc55-110">Predict with the trained model</span></span>
> * <span data-ttu-id="ebc55-111">Wdrażanie i przewidywanie z załadowanym modelem</span><span class="sxs-lookup"><span data-stu-id="ebc55-111">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="ebc55-112">Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) .</span><span class="sxs-lookup"><span data-stu-id="ebc55-112">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ebc55-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="ebc55-113">Prerequisites</span></span>

* <span data-ttu-id="ebc55-114">[Program Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowszy albo program visual Studio 2017 w wersji 15,6 lub nowszej z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ebc55-114">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>
* <span data-ttu-id="ebc55-115">[Plik rozdzielony tabulatorami problemów usługi GitHub (issues_train. tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span><span class="sxs-lookup"><span data-stu-id="ebc55-115">The [GitHub issues tab separated file (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span></span>
* <span data-ttu-id="ebc55-116">[Plik rozdzielony kart testów problemów GitHub (issues_test. tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span><span class="sxs-lookup"><span data-stu-id="ebc55-116">The [GitHub issues test tab separated file (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="ebc55-117">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="ebc55-117">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="ebc55-118">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="ebc55-118">Create a project</span></span>

1. <span data-ttu-id="ebc55-119">Otwórz program Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="ebc55-119">Open Visual Studio 2017.</span></span> <span data-ttu-id="ebc55-120">Na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt** .</span><span class="sxs-lookup"><span data-stu-id="ebc55-120">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="ebc55-121">W oknie dialogowym **Nowy projekt** wybierz węzeł **Visual C#** , a następnie węzeł **.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="ebc55-121">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="ebc55-122">Następnie wybierz szablon projektu **aplikacja konsoli (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="ebc55-122">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="ebc55-123">W polu tekstowym **Nazwa** wpisz "GitHubIssueClassification", a następnie wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="ebc55-123">In the **Name** text box, type "GitHubIssueClassification" and then select the **OK** button.</span></span>

2. <span data-ttu-id="ebc55-124">Utwórz katalog o nazwie *dane* w projekcie, aby zapisać pliki zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="ebc55-124">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="ebc55-125">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj**  >  **Nowy folder**.</span><span class="sxs-lookup"><span data-stu-id="ebc55-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="ebc55-126">Wpisz "Data" i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="ebc55-126">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="ebc55-127">Utwórz katalog o nazwie *models* w projekcie, aby zapisać model:</span><span class="sxs-lookup"><span data-stu-id="ebc55-127">Create a directory named *Models* in your project to save your model:</span></span>

    <span data-ttu-id="ebc55-128">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj**  >  **Nowy folder**.</span><span class="sxs-lookup"><span data-stu-id="ebc55-128">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="ebc55-129">Wpisz "models" i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="ebc55-129">Type "Models" and hit Enter.</span></span>

4. <span data-ttu-id="ebc55-130">Zainstaluj **pakiet NuGet Microsoft.ml**:</span><span class="sxs-lookup"><span data-stu-id="ebc55-130">Install the **Microsoft.ML NuGet Package**:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    <span data-ttu-id="ebc55-131">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="ebc55-131">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="ebc55-132">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, Wyszukaj pozycję **Microsoft.ml** i wybierz przycisk **Instaluj** .</span><span class="sxs-lookup"><span data-stu-id="ebc55-132">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="ebc55-133">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="ebc55-133">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="ebc55-134">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="ebc55-134">Prepare your data</span></span>

1. <span data-ttu-id="ebc55-135">Pobierz zestawy danych [issues_train. tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) i [issues_test. tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) i Zapisz je w utworzonym wcześniej folderze *danych* .</span><span class="sxs-lookup"><span data-stu-id="ebc55-135">Download the [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) and the [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="ebc55-136">Pierwszy zestaw danych pociąga za niego model uczenia maszynowego, a drugi może służyć do oszacowania, jak dokładny jest model.</span><span class="sxs-lookup"><span data-stu-id="ebc55-136">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="ebc55-137">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy każdy z \* plików. tsv i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="ebc55-137">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="ebc55-138">W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="ebc55-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="ebc55-139">Tworzenie klas i Definiowanie ścieżek</span><span class="sxs-lookup"><span data-stu-id="ebc55-139">Create classes and define paths</span></span>

<span data-ttu-id="ebc55-140">Dodaj następujące dodatkowe `using` instrukcje na początku pliku *program.cs* :</span><span class="sxs-lookup"><span data-stu-id="ebc55-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddUsings)]

<span data-ttu-id="ebc55-141">Utwórz trzy pola globalne do przechowywania ścieżek do ostatnio pobranych plików, a następnie zmienne globalne dla `MLContext` , `DataView` i `PredictionEngine` :</span><span class="sxs-lookup"><span data-stu-id="ebc55-141">Create three global fields to hold the paths to the recently downloaded files, and global variables for the `MLContext`,`DataView`, and `PredictionEngine`:</span></span>

* <span data-ttu-id="ebc55-142">`_trainDataPath`ma ścieżkę do zestawu danych używanego do uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="ebc55-142">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="ebc55-143">`_testDataPath`ma ścieżkę do zestawu danych używanego do szacowania modelu.</span><span class="sxs-lookup"><span data-stu-id="ebc55-143">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="ebc55-144">`_modelPath`ma ścieżkę, w której jest zapisywany model szkolony.</span><span class="sxs-lookup"><span data-stu-id="ebc55-144">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="ebc55-145">`_mlContext`jest to element <xref:Microsoft.ML.MLContext> , który zawiera kontekst przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="ebc55-145">`_mlContext` is the <xref:Microsoft.ML.MLContext> that provides processing context.</span></span>
* <span data-ttu-id="ebc55-146">`_trainingDataView`jest <xref:Microsoft.ML.IDataView> używany do przetwarzania zestawu danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="ebc55-146">`_trainingDataView` is the <xref:Microsoft.ML.IDataView> used to process the training dataset.</span></span>
* <span data-ttu-id="ebc55-147">`_predEngine`jest <xref:Microsoft.ML.PredictionEngine%602> używany dla pojedynczych prognoz.</span><span class="sxs-lookup"><span data-stu-id="ebc55-147">`_predEngine` is the <xref:Microsoft.ML.PredictionEngine%602> used for single predictions.</span></span>

<span data-ttu-id="ebc55-148">Dodaj następujący kod do wiersza bezpośrednio powyżej `Main` metody, aby określić te ścieżki i inne zmienne:</span><span class="sxs-lookup"><span data-stu-id="ebc55-148">Add the following code to the line directly above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="ebc55-149">Utwórz klasy dla danych wejściowych i prognoz.</span><span class="sxs-lookup"><span data-stu-id="ebc55-149">Create some classes for your input data and predictions.</span></span> <span data-ttu-id="ebc55-150">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="ebc55-150">Add a new class to your project:</span></span>

1. <span data-ttu-id="ebc55-151">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj**  >  **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="ebc55-151">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="ebc55-152">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *GitHubIssueData.cs*.</span><span class="sxs-lookup"><span data-stu-id="ebc55-152">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *GitHubIssueData.cs*.</span></span> <span data-ttu-id="ebc55-153">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="ebc55-153">Then, select the **Add** button.</span></span>

    <span data-ttu-id="ebc55-154">Plik *GitHubIssueData.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="ebc55-154">The *GitHubIssueData.cs* file opens in the code editor.</span></span> <span data-ttu-id="ebc55-155">Dodaj następującą `using` instrukcję na początku *GitHubIssueData.cs*:</span><span class="sxs-lookup"><span data-stu-id="ebc55-155">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/GitHubIssueData.cs#AddUsings)]

<span data-ttu-id="ebc55-156">Usuń istniejącą definicję klasy i Dodaj następujący kod, który ma dwie klasy `GitHubIssue` i `IssuePrediction` , do pliku *GitHubIssueData.cs* :</span><span class="sxs-lookup"><span data-stu-id="ebc55-156">Remove the existing class definition and add the following code, which has two classes `GitHubIssue` and `IssuePrediction`, to the *GitHubIssueData.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/GitHubIssueData.cs#DeclareTypes)]

<span data-ttu-id="ebc55-157">`label`Jest to kolumna, która ma zostać przewidywalna.</span><span class="sxs-lookup"><span data-stu-id="ebc55-157">The `label` is the column you want to predict.</span></span> <span data-ttu-id="ebc55-158">Identyfikowane `Features` są dane wejściowe, które umożliwiają modelowi przewidywalność etykiety.</span><span class="sxs-lookup"><span data-stu-id="ebc55-158">The identified `Features` are the inputs you give the model to predict the Label.</span></span>

<span data-ttu-id="ebc55-159">Użyj [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) , aby określić indeksy kolumn źródłowych w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="ebc55-159">Use the [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="ebc55-160">`GitHubIssue`jest klasą wejściowego zestawu danych i zawiera następujące <xref:System.String> pola:</span><span class="sxs-lookup"><span data-stu-id="ebc55-160">`GitHubIssue` is the input dataset class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="ebc55-161">Pierwsza kolumna `ID` (identyfikator problemu usługi GitHub)</span><span class="sxs-lookup"><span data-stu-id="ebc55-161">the first column `ID` (GitHub Issue ID)</span></span>
* <span data-ttu-id="ebc55-162">Druga kolumna `Area` (Prognoza dla szkolenia)</span><span class="sxs-lookup"><span data-stu-id="ebc55-162">the second column `Area` (the prediction for training)</span></span>
* <span data-ttu-id="ebc55-163">Trzecia kolumna `Title` (tytuł problemu GitHub) jest pierwszym `feature` używanym do przewidywania`Area`</span><span class="sxs-lookup"><span data-stu-id="ebc55-163">the third column `Title` (GitHub issue title) is the first `feature` used for predicting the `Area`</span></span>
* <span data-ttu-id="ebc55-164">czwarta kolumna `Description` jest sekundą `feature` używaną do przewidywania`Area`</span><span class="sxs-lookup"><span data-stu-id="ebc55-164">the fourth column  `Description` is the second `feature` used for predicting the `Area`</span></span>

<span data-ttu-id="ebc55-165">`IssuePrediction`jest klasą używaną do przewidywania po przeszkoleniu modelu.</span><span class="sxs-lookup"><span data-stu-id="ebc55-165">`IssuePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="ebc55-166">Ma pojedynczy `string` ( `Area` ) i `PredictedLabel` `ColumnName` atrybut.</span><span class="sxs-lookup"><span data-stu-id="ebc55-166">It has a single `string` (`Area`) and a `PredictedLabel` `ColumnName` attribute.</span></span>  <span data-ttu-id="ebc55-167">`PredictedLabel`Jest używany podczas przewidywania i oceny.</span><span class="sxs-lookup"><span data-stu-id="ebc55-167">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="ebc55-168">W celu dokonania oceny dane wejściowe z danymi szkoleniowymi, przewidywane wartości i model są używane.</span><span class="sxs-lookup"><span data-stu-id="ebc55-168">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="ebc55-169">Wszystkie operacje ML.NET są uruchamiane w klasie [MLContext](xref:Microsoft.ML.MLContext) .</span><span class="sxs-lookup"><span data-stu-id="ebc55-169">All ML.NET operations start in the [MLContext](xref:Microsoft.ML.MLContext) class.</span></span> <span data-ttu-id="ebc55-170">Inicjowanie `mlContext` tworzy nowe środowisko ml.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="ebc55-170">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="ebc55-171">Jest to podobne, pojęciowo do `DBContext` w `Entity Framework` .</span><span class="sxs-lookup"><span data-stu-id="ebc55-171">It's similar, conceptually, to `DBContext` in `Entity Framework`.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="ebc55-172">Inicjuj zmienne w głównym</span><span class="sxs-lookup"><span data-stu-id="ebc55-172">Initialize variables in Main</span></span>

<span data-ttu-id="ebc55-173">Zainicjuj `_mlContext` zmienną globalną z nowym wystąpieniem `MLContext` z losowym inicjatorem ( `seed: 0` ) dla powtarzalnych/deterministycznych wyników w wielu szkoleniach.</span><span class="sxs-lookup"><span data-stu-id="ebc55-173">Initialize the `_mlContext` global variable  with a new instance of `MLContext` with a random seed (`seed: 0`) for repeatable/deterministic results across multiple trainings.</span></span>  <span data-ttu-id="ebc55-174">Zamień `Console.WriteLine("Hello World!")` wiersz na następujący kod w `Main` metodzie:</span><span class="sxs-lookup"><span data-stu-id="ebc55-174">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a><span data-ttu-id="ebc55-175">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="ebc55-175">Load the data</span></span>

<span data-ttu-id="ebc55-176">ML.NET używa [klasy IDataView](xref:Microsoft.ML.IDataView) jako elastycznej, wydajnej metody opisywania danych tabelarycznych lub tekstowych.</span><span class="sxs-lookup"><span data-stu-id="ebc55-176">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="ebc55-177">`IDataView`może ładować pliki tekstowe lub w czasie rzeczywistym (na przykład bazy danych SQL lub pliki dzienników).</span><span class="sxs-lookup"><span data-stu-id="ebc55-177">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span>

<span data-ttu-id="ebc55-178">Aby zainicjować i załadować `_trainingDataView` zmienną globalną w celu użycia jej dla potoku, należy dodać następujący kod po `mlContext` zainicjowaniu:</span><span class="sxs-lookup"><span data-stu-id="ebc55-178">To initialize and load the `_trainingDataView` global variable in order to use it for the pipeline, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[LoadTrainData](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#LoadTrainData)]

<span data-ttu-id="ebc55-179">[LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczytuje w pliku.</span><span class="sxs-lookup"><span data-stu-id="ebc55-179">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="ebc55-180">Przyjmuje zmienne ścieżki danych i zwraca `IDataView` .</span><span class="sxs-lookup"><span data-stu-id="ebc55-180">It takes in the data path variables and returns an `IDataView`.</span></span>

<span data-ttu-id="ebc55-181">Dodaj następujący kod jako następny wiersz kodu w `Main` metodzie:</span><span class="sxs-lookup"><span data-stu-id="ebc55-181">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallProcessData](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallProcessData)]

<span data-ttu-id="ebc55-182">`ProcessData`Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="ebc55-182">The `ProcessData` method executes the following tasks:</span></span>

* <span data-ttu-id="ebc55-183">Wyodrębnia i przekształca dane.</span><span class="sxs-lookup"><span data-stu-id="ebc55-183">Extracts and transforms the data.</span></span>
* <span data-ttu-id="ebc55-184">Zwraca potok przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="ebc55-184">Returns the processing pipeline.</span></span>

<span data-ttu-id="ebc55-185">Utwórz `ProcessData` metodę, tuż po `Main` metodzie, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ebc55-185">Create the `ProcessData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="ebc55-186">Wyodrębnij funkcje i Przekształć dane</span><span class="sxs-lookup"><span data-stu-id="ebc55-186">Extract Features and transform the data</span></span>

<span data-ttu-id="ebc55-187">Aby przewidzieć etykietę obszaru usługi GitHub dla elementu, należy `GitHubIssue` użyć metody [MapValueToKey ()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) do przekształcenia `Area` kolumny w kolumnę typu klucza numerycznego `Label` (format akceptowany przez algorytmy klasyfikacji) i dodać ją jako nową kolumnę zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="ebc55-187">As you want to predict the Area GitHub label for a `GitHubIssue`, use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform the `Area` column into a numeric key type `Label` column (a format accepted by classification algorithms) and add it as a new dataset column:</span></span>

[!code-csharp[MapValueToKey](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#MapValueToKey)]

<span data-ttu-id="ebc55-188">Następnie należy wywołać metodę `mlContext.Transforms.Text.FeaturizeText` , która przekształca kolumny tekstu ( `Title` i `Description` ) do wektora liczbowego dla każdego wywoływanego `TitleFeaturized` i `DescriptionFeaturized` .</span><span class="sxs-lookup"><span data-stu-id="ebc55-188">Next, call `mlContext.Transforms.Text.FeaturizeText`, which transforms the text (`Title` and `Description`) columns into a numeric vector for each called `TitleFeaturized` and `DescriptionFeaturized`.</span></span> <span data-ttu-id="ebc55-189">Dołącz cechowania dla obu kolumn do potoku przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ebc55-189">Append the featurization for both columns to the pipeline with the following code:</span></span>

[!code-csharp[FeaturizeText](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#FeaturizeText)]

<span data-ttu-id="ebc55-190">Ostatnim krokiem w przygotowaniu danych jest połączenie wszystkich kolumn funkcji w kolumnie **funkcje** przy użyciu metody [złączing ()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) .</span><span class="sxs-lookup"><span data-stu-id="ebc55-190">The last step in data preparation combines all of the feature columns into the **Features** column using the [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) method.</span></span> <span data-ttu-id="ebc55-191">Domyślnie algorytm uczenia przetwarza tylko funkcje z kolumny **Features** .</span><span class="sxs-lookup"><span data-stu-id="ebc55-191">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="ebc55-192">Dołącz tę transformację do potoku przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ebc55-192">Append this transformation to the pipeline with the following code:</span></span>

[!code-csharp[Concatenate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Concatenate)]

 <span data-ttu-id="ebc55-193">Następnie Dołącz <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> do pamięci podręcznej, aby w przypadku wielokrotnego powtarzania danych za pomocą pamięci podręcznej można było uzyskać lepszą wydajność, podobnie jak w przypadku następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ebc55-193">Next, append a <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> to cache the DataView so when you iterate over the data multiple times using the cache might get better performance, as with the following code:</span></span>

[!code-csharp[AppendCache](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AppendCache)]

> [!WARNING]
> <span data-ttu-id="ebc55-194">Aby zmniejszyć czas uczenia, użyj AppendCacheCheckpoint dla małych i średnich zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="ebc55-194">Use AppendCacheCheckpoint for small/medium datasets to lower training time.</span></span> <span data-ttu-id="ebc55-195">Nie należy używać go (Usuń. AppendCacheCheckpoint ()) podczas obsługi bardzo dużych zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="ebc55-195">Do NOT use it (remove .AppendCacheCheckpoint()) when handling very large datasets.</span></span>

<span data-ttu-id="ebc55-196">Zwróć potok na końcu `ProcessData` metody.</span><span class="sxs-lookup"><span data-stu-id="ebc55-196">Return the pipeline at the end of the `ProcessData` method.</span></span>

[!code-csharp[ReturnPipeline](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#ReturnPipeline)]

<span data-ttu-id="ebc55-197">Ten krok obsługuje przetwarzanie wstępne/cechowania.</span><span class="sxs-lookup"><span data-stu-id="ebc55-197">This step handles preprocessing/featurization.</span></span> <span data-ttu-id="ebc55-198">Korzystanie z dodatkowych składników dostępnych w programie ML.NET może umożliwić lepsze wyniki w modelu.</span><span class="sxs-lookup"><span data-stu-id="ebc55-198">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="build-and-train-the-model"></a><span data-ttu-id="ebc55-199">Kompilowanie i uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="ebc55-199">Build and train the model</span></span>

<span data-ttu-id="ebc55-200">Dodaj następujące wywołanie do `BuildAndTrainModel` metody jako następny wiersz kodu w `Main` metodzie:</span><span class="sxs-lookup"><span data-stu-id="ebc55-200">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="ebc55-201">`BuildAndTrainModel`Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="ebc55-201">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="ebc55-202">Tworzy klasę algorytmu szkoleniowego.</span><span class="sxs-lookup"><span data-stu-id="ebc55-202">Creates the training algorithm class.</span></span>
* <span data-ttu-id="ebc55-203">Pociąga za siebie model.</span><span class="sxs-lookup"><span data-stu-id="ebc55-203">Trains the model.</span></span>
* <span data-ttu-id="ebc55-204">Obszar przewidywania na podstawie danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="ebc55-204">Predicts area based on training data.</span></span>
* <span data-ttu-id="ebc55-205">Zwraca model.</span><span class="sxs-lookup"><span data-stu-id="ebc55-205">Returns the model.</span></span>

<span data-ttu-id="ebc55-206">Utwórz `BuildAndTrainModel` metodę, tuż po `Main` metodzie, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ebc55-206">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a><span data-ttu-id="ebc55-207">Informacje o zadaniu klasyfikacji</span><span class="sxs-lookup"><span data-stu-id="ebc55-207">About the classification task</span></span>

<span data-ttu-id="ebc55-208">Klasyfikacja to zadanie uczenia maszynowego, które używa danych do **określania** kategorii, typu lub klasy elementu lub wiersza danych. jest to często jeden z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="ebc55-208">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data and is frequently one of the following types:</span></span>

* <span data-ttu-id="ebc55-209">Plik binarny: A lub B.</span><span class="sxs-lookup"><span data-stu-id="ebc55-209">Binary: either A or B.</span></span>
* <span data-ttu-id="ebc55-210">Wieloklasowe: wiele kategorii, które mogą być przewidywane przy użyciu jednego modelu.</span><span class="sxs-lookup"><span data-stu-id="ebc55-210">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="ebc55-211">W przypadku tego typu problemu należy użyć wieloklasowego algorytmu uczenia klasyfikacji, ponieważ przewidywanie kategorii problemu może być jedną z wielu kategorii (wiele klas), a nie tylko dwóch (binarnych).</span><span class="sxs-lookup"><span data-stu-id="ebc55-211">For this type of problem, use a Multiclass classification learning algorithm, since your issue category prediction can be one of multiple categories (multiclass) rather than just two (binary).</span></span>

<span data-ttu-id="ebc55-212">Dołącz algorytm uczenia maszynowego do definicji transformacji danych, dodając następujący kod jako pierwszy wiersz kodu w `BuildAndTrainModel()` :</span><span class="sxs-lookup"><span data-stu-id="ebc55-212">Append the machine learning algorithm to the data transformation definitions by adding the following as the first line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddTrainer](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddTrainer)]

<span data-ttu-id="ebc55-213">[SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) to algorytm szkoleniowy klasyfikacji wieloklasowej.</span><span class="sxs-lookup"><span data-stu-id="ebc55-213">The [SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) is your multiclass classification training algorithm.</span></span> <span data-ttu-id="ebc55-214">Jest on dołączany do `pipeline` i akceptuje featurized `Title` i `Description` ( `Features` ) oraz `Label` Parametry wejściowe, aby poznać dane historyczne.</span><span class="sxs-lookup"><span data-stu-id="ebc55-214">This is appended to the `pipeline` and accepts the featurized `Title` and `Description` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="ebc55-215">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="ebc55-215">Train the model</span></span>

<span data-ttu-id="ebc55-216">Dopasuj model do `splitTrainSet` danych i zwróć przeszkolony model, dodając następujący kod jako następny wiersz kodu w `BuildAndTrainModel()` metodzie:</span><span class="sxs-lookup"><span data-stu-id="ebc55-216">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#TrainModel)]

<span data-ttu-id="ebc55-217">`Fit()`Metoda pociąga za siebie model poprzez transformowanie zestawu danych i zastosowanie szkolenia.</span><span class="sxs-lookup"><span data-stu-id="ebc55-217">The `Fit()`method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="ebc55-218">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest WYGODNYm interfejsem API, który pozwala na przekazywanie danych, a następnie wykonywanie prognozowania na jednym wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="ebc55-218">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span> <span data-ttu-id="ebc55-219">Dodaj tę wartość jako następny wiersz w `BuildAndTrainModel()` metodzie:</span><span class="sxs-lookup"><span data-stu-id="ebc55-219">Add this as the next line in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[CreatePredictionEngine1](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a><span data-ttu-id="ebc55-220">Przewidywanie przy użyciu przeszkolonego modelu</span><span class="sxs-lookup"><span data-stu-id="ebc55-220">Predict with the trained model</span></span>

<span data-ttu-id="ebc55-221">Dodaj problem w usłudze GitHub, aby przetestować prognozę przeszkolonego modelu w `Predict` metodzie, tworząc wystąpienie `GitHubIssue` :</span><span class="sxs-lookup"><span data-stu-id="ebc55-221">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[CreateTestIssue1](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreateTestIssue1)]

<span data-ttu-id="ebc55-222">Funkcja [przewidywania ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) służy do prognozowania pojedynczego wiersza danych:</span><span class="sxs-lookup"><span data-stu-id="ebc55-222">Use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

[!code-csharp[Predict](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a><span data-ttu-id="ebc55-223">Korzystanie z modelu: wyniki przewidywania</span><span class="sxs-lookup"><span data-stu-id="ebc55-223">Using the model: prediction results</span></span>

<span data-ttu-id="ebc55-224">Wyświetlaj `GitHubIssue` i odpowiadaj `Area` prognozie etykiet, aby udostępnić wyniki i wykonać odpowiednie działania.</span><span class="sxs-lookup"><span data-stu-id="ebc55-224">Display `GitHubIssue` and corresponding `Area` label prediction in order to share the results and act on them accordingly.</span></span>  <span data-ttu-id="ebc55-225">Utwórz ekran dla wyników przy użyciu następującego <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:</span><span class="sxs-lookup"><span data-stu-id="ebc55-225">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="ebc55-226">Zwróć model przeszkolony do użycia na potrzeby oceny</span><span class="sxs-lookup"><span data-stu-id="ebc55-226">Return the model trained to use for evaluation</span></span>

<span data-ttu-id="ebc55-227">Zwróć model na końcu `BuildAndTrainModel` metody.</span><span class="sxs-lookup"><span data-stu-id="ebc55-227">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a><span data-ttu-id="ebc55-228">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="ebc55-228">Evaluate the model</span></span>

<span data-ttu-id="ebc55-229">Teraz, gdy tworzysz i przeszkolony model, musisz go oszacować z innym zestawem danych w celu zapewnienia jakości i weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="ebc55-229">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="ebc55-230">W `Evaluate` metodzie model utworzony w `BuildAndTrainModel` jest przeszedł do oceny.</span><span class="sxs-lookup"><span data-stu-id="ebc55-230">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="ebc55-231">Utwórz `Evaluate` metodę, tuż po `BuildAndTrainModel` , jak w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="ebc55-231">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate(DataViewSchema trainingDataViewSchema)
{

}
```

<span data-ttu-id="ebc55-232">`Evaluate`Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="ebc55-232">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="ebc55-233">Ładuje zestaw danych testowych.</span><span class="sxs-lookup"><span data-stu-id="ebc55-233">Loads the test dataset.</span></span>
* <span data-ttu-id="ebc55-234">Tworzy ewaluatora wieloklasowe.</span><span class="sxs-lookup"><span data-stu-id="ebc55-234">Creates the multiclass evaluator.</span></span>
* <span data-ttu-id="ebc55-235">Oblicza model i tworzy metryki.</span><span class="sxs-lookup"><span data-stu-id="ebc55-235">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="ebc55-236">Wyświetla metryki.</span><span class="sxs-lookup"><span data-stu-id="ebc55-236">Displays the metrics.</span></span>

<span data-ttu-id="ebc55-237">Dodaj wywołanie do nowej metody z `Main` metody, bezpośrednio pod `BuildAndTrainModel` wywołaniem metody, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ebc55-237">Add a call to the new method from the `Main` method, right under the `BuildAndTrainModel` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallEvaluate)]

<span data-ttu-id="ebc55-238">Tak jak wcześniej z zestawem danych szkoleniowych, Załaduj zestaw danych testowych, dodając następujący kod do `Evaluate` metody:</span><span class="sxs-lookup"><span data-stu-id="ebc55-238">As you did previously with the training dataset, load the test dataset by adding the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#LoadTestDataset)]

<span data-ttu-id="ebc55-239">Metoda COMPUTE [()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) oblicza metryki jakości dla modelu przy użyciu określonego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="ebc55-239">The [Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) method computes the quality metrics for the model using the specified dataset.</span></span> <span data-ttu-id="ebc55-240">Zwraca <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> obiekt, który zawiera metryki ogólne obliczone przez konstruktory klasyfikacji wieloklasowej.</span><span class="sxs-lookup"><span data-stu-id="ebc55-240">It returns a <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> object that contains the overall metrics computed by multiclass classification evaluators.</span></span>
<span data-ttu-id="ebc55-241">Aby wyświetlić metryki w celu określenia jakości modelu, należy je najpierw pobrać.</span><span class="sxs-lookup"><span data-stu-id="ebc55-241">To display the metrics to determine the quality of the model, you need to get them first.</span></span>
<span data-ttu-id="ebc55-242">Zwróć uwagę na użycie metody [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) zmiennej globalnej uczenia maszynowego `_trainedModel` ( [ITransformer](xref:Microsoft.ML.ITransformer)) w celu wejścia do funkcji i zwracania prognoz.</span><span class="sxs-lookup"><span data-stu-id="ebc55-242">Notice the use of the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method of the machine learning `_trainedModel` global variable (an [ITransformer](xref:Microsoft.ML.ITransformer)) to input the features and return predictions.</span></span> <span data-ttu-id="ebc55-243">Dodaj następujący kod do `Evaluate` metody w następnym wierszu:</span><span class="sxs-lookup"><span data-stu-id="ebc55-243">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[Evaluate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Evaluate)]

<span data-ttu-id="ebc55-244">Następujące metryki są oceniane dla klasyfikacji wieloklasowej:</span><span class="sxs-lookup"><span data-stu-id="ebc55-244">The following metrics are evaluated for multiclass classification:</span></span>

* <span data-ttu-id="ebc55-245">Mikro-dokładność — każda para klasy próbek bezproblemowo przyczynia się do metryki dokładności.</span><span class="sxs-lookup"><span data-stu-id="ebc55-245">Micro Accuracy - Every sample-class pair contributes equally to the accuracy metric.</span></span>  <span data-ttu-id="ebc55-246">Chcesz, aby program Micro dokładności był możliwie blisko jednej, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="ebc55-246">You want Micro Accuracy to be as close to one as possible.</span></span>

* <span data-ttu-id="ebc55-247">Dokładność makra — każda klasa przyczynia się równo do metryki dokładności.</span><span class="sxs-lookup"><span data-stu-id="ebc55-247">Macro Accuracy - Every class contributes equally to the accuracy metric.</span></span> <span data-ttu-id="ebc55-248">Klasy mniejszości są traktowane jako takie same wagi jak większe klasy.</span><span class="sxs-lookup"><span data-stu-id="ebc55-248">Minority classes are given equal weight as the larger classes.</span></span> <span data-ttu-id="ebc55-249">Dokładność makra powinna być jak najbliżej jednego z nich.</span><span class="sxs-lookup"><span data-stu-id="ebc55-249">You want Macro Accuracy to be as close to one as possible.</span></span>

* <span data-ttu-id="ebc55-250">Dziennik — utrata — zobacz [Dziennik strat](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="ebc55-250">Log-loss - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="ebc55-251">Utrata dziennika powinna być jak najbliżej zera.</span><span class="sxs-lookup"><span data-stu-id="ebc55-251">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="ebc55-252">Redukcja utraconych plików dziennika — zakresy z [-inf, 1,00], gdzie 1,00 są idealnym przewidywaniam, a wartość 0 oznacza przewidywania.</span><span class="sxs-lookup"><span data-stu-id="ebc55-252">Log-loss reduction - Ranges from [-inf, 1.00], where 1.00 is perfect predictions and 0 indicates mean predictions.</span></span> <span data-ttu-id="ebc55-253">Zmniejszenie liczby utraconych dzienników jest możliwie najbliżej jednego z nich.</span><span class="sxs-lookup"><span data-stu-id="ebc55-253">You want Log-loss reduction to be as close to one as possible.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="ebc55-254">Wyświetlanie metryk na potrzeby walidacji modelu</span><span class="sxs-lookup"><span data-stu-id="ebc55-254">Displaying the metrics for model validation</span></span>

<span data-ttu-id="ebc55-255">Użyj poniższego kodu, aby wyświetlić metryki, Udostępnij wyniki, a następnie wykonaj na nich czynności:</span><span class="sxs-lookup"><span data-stu-id="ebc55-255">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DisplayMetrics)]

### <a name="save-the-model-to-a-file"></a><span data-ttu-id="ebc55-256">Zapisz model w pliku</span><span class="sxs-lookup"><span data-stu-id="ebc55-256">Save the model to a file</span></span>

<span data-ttu-id="ebc55-257">Po spełnieniu modelu należy zapisać go w pliku, aby dokonać prognoz w późniejszym czasie lub w innej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ebc55-257">Once satisfied with your model, save it to a file to make predictions at a later time or in another application.</span></span> <span data-ttu-id="ebc55-258">Dodaj następujący kod do metody `Evaluate`:</span><span class="sxs-lookup"><span data-stu-id="ebc55-258">Add the following code to the `Evaluate` method.</span></span>

[!code-csharp[SnippetCallSaveModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetCallSaveModel)]

<span data-ttu-id="ebc55-259">Utwórz `SaveModelAsFile` metodę poniżej `Evaluate` metody.</span><span class="sxs-lookup"><span data-stu-id="ebc55-259">Create the `SaveModelAsFile` method below your `Evaluate` method.</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext,DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

<span data-ttu-id="ebc55-260">Dodaj następujący kod do `SaveModelAsFile` metody.</span><span class="sxs-lookup"><span data-stu-id="ebc55-260">Add the following code to your `SaveModelAsFile` method.</span></span> <span data-ttu-id="ebc55-261">Ten kod używa [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) metody do serializacji i przechowywania przeszkolonego modelu jako pliku zip.</span><span class="sxs-lookup"><span data-stu-id="ebc55-261">This code uses the [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) method to serialize and store the trained model as a zip file.</span></span>

[!code-csharp[SnippetSaveModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetSaveModel)]

## <a name="deploy-and-predict-with-a-model"></a><span data-ttu-id="ebc55-262">Wdrażanie i prognozowanie przy użyciu modelu</span><span class="sxs-lookup"><span data-stu-id="ebc55-262">Deploy and Predict with a model</span></span>

<span data-ttu-id="ebc55-263">Dodaj wywołanie do nowej metody z `Main` metody, bezpośrednio pod `Evaluate` wywołaniem metody, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ebc55-263">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredictIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallPredictIssue)]

<span data-ttu-id="ebc55-264">Utwórz `PredictIssue` metodę, tuż po `Evaluate` metodzie (i tuż przed metodą `SaveModelAsFile` ), używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ebc55-264">Create the `PredictIssue` method, just after the `Evaluate` method (and just before the `SaveModelAsFile` method), using the following code:</span></span>

```csharp
private static void PredictIssue()
{

}
```

<span data-ttu-id="ebc55-265">`PredictIssue`Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="ebc55-265">The `PredictIssue` method executes the following tasks:</span></span>

* <span data-ttu-id="ebc55-266">Ładuje zapisany model</span><span class="sxs-lookup"><span data-stu-id="ebc55-266">Loads the saved model</span></span>
* <span data-ttu-id="ebc55-267">Tworzy pojedynczy problem dotyczący danych testowych.</span><span class="sxs-lookup"><span data-stu-id="ebc55-267">Creates a single issue of test data.</span></span>
* <span data-ttu-id="ebc55-268">Obszar przewidywania na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="ebc55-268">Predicts Area based on test data.</span></span>
* <span data-ttu-id="ebc55-269">Łączy dane testowe i prognozy na potrzeby raportowania.</span><span class="sxs-lookup"><span data-stu-id="ebc55-269">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="ebc55-270">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="ebc55-270">Displays the predicted results.</span></span>

<span data-ttu-id="ebc55-271">Załaduj zapisany model do aplikacji, dodając następujący kod do `PredictIssue` metody:</span><span class="sxs-lookup"><span data-stu-id="ebc55-271">Load the saved model into your application by adding the following code to the `PredictIssue` method:</span></span>

[!code-csharp[SnippetLoadModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetLoadModel)]

<span data-ttu-id="ebc55-272">Dodaj problem w usłudze GitHub, aby przetestować prognozę przeszkolonego modelu w `Predict` metodzie, tworząc wystąpienie `GitHubIssue` :</span><span class="sxs-lookup"><span data-stu-id="ebc55-272">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[AddTestIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddTestIssue)]

<span data-ttu-id="ebc55-273">Tak jak wcześniej, Utwórz `PredictionEngine` wystąpienie o następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="ebc55-273">As you did previously, create a `PredictionEngine` instance with the following code:</span></span>

[!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreatePredictionEngine)]

<span data-ttu-id="ebc55-274">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest WYGODNYm interfejsem API, który umożliwia prognozowanie jednego wystąpienia danych.</span><span class="sxs-lookup"><span data-stu-id="ebc55-274">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="ebc55-275">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny wątkowo.</span><span class="sxs-lookup"><span data-stu-id="ebc55-275">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="ebc55-276">Jest to możliwe do użycia w środowiskach wielowątkowych lub prototypowych.</span><span class="sxs-lookup"><span data-stu-id="ebc55-276">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="ebc55-277">Aby zwiększyć wydajność i bezpieczeństwo wątków w środowiskach produkcyjnych, należy użyć `PredictionEnginePool` usługi, która tworzy [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) obiekty do użycia w całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ebc55-277">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="ebc55-278">Zapoznaj się z tym przewodnikiem dotyczącym [korzystania `PredictionEnginePool` z programu w ASP.NET Core INTERNETowym interfejsie API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="ebc55-278">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="ebc55-279">`PredictionEnginePool`rozszerzenie usługi jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="ebc55-279">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="ebc55-280">Użyj, `PredictionEngine` aby przewidzieć etykietę obszaru GitHub, dodając następujący kod do `PredictIssue` metody przewidywania:</span><span class="sxs-lookup"><span data-stu-id="ebc55-280">Use the `PredictionEngine` to predict the Area GitHub label by adding the following code to the `PredictIssue` method for the prediction:</span></span>

[!code-csharp[PredictIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a><span data-ttu-id="ebc55-281">Używanie załadowanego modelu do prognozowania</span><span class="sxs-lookup"><span data-stu-id="ebc55-281">Using the loaded model for prediction</span></span>

<span data-ttu-id="ebc55-282">Wyświetlaj `Area` w celu skategoryzowania problemu i działania na nim odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="ebc55-282">Display `Area` in order to categorize the issue and act on it accordingly.</span></span> <span data-ttu-id="ebc55-283">Utwórz ekran dla wyników przy użyciu następującego <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:</span><span class="sxs-lookup"><span data-stu-id="ebc55-283">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayResults](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DisplayResults)]

## <a name="results"></a><span data-ttu-id="ebc55-284">Wyniki</span><span class="sxs-lookup"><span data-stu-id="ebc55-284">Results</span></span>

<span data-ttu-id="ebc55-285">Wyniki powinny wyglądać podobnie do poniższego.</span><span class="sxs-lookup"><span data-stu-id="ebc55-285">Your results should be similar to the following.</span></span> <span data-ttu-id="ebc55-286">Proces potokowy wyświetla komunikaty.</span><span class="sxs-lookup"><span data-stu-id="ebc55-286">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="ebc55-287">Mogą pojawić się ostrzeżenia lub przetwarzanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="ebc55-287">You may see warnings, or processing messages.</span></span> <span data-ttu-id="ebc55-288">Te komunikaty zostały usunięte z następujących wyników dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="ebc55-288">These messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="ebc55-289">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="ebc55-289">Congratulations!</span></span> <span data-ttu-id="ebc55-290">Pomyślnie skompilowano model uczenia maszynowego służący do klasyfikowania i przewidywania etykiet obszaru dla problemu usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="ebc55-290">You've now successfully built a machine learning model for classifying and predicting an Area label for a GitHub issue.</span></span> <span data-ttu-id="ebc55-291">Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) .</span><span class="sxs-lookup"><span data-stu-id="ebc55-291">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ebc55-292">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="ebc55-292">Next steps</span></span>

<span data-ttu-id="ebc55-293">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="ebc55-293">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="ebc55-294">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="ebc55-294">Prepare your data</span></span>
> * <span data-ttu-id="ebc55-295">Przekształcanie danych</span><span class="sxs-lookup"><span data-stu-id="ebc55-295">Transform the data</span></span>
> * <span data-ttu-id="ebc55-296">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="ebc55-296">Train the model</span></span>
> * <span data-ttu-id="ebc55-297">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="ebc55-297">Evaluate the model</span></span>
> * <span data-ttu-id="ebc55-298">Przewidywanie przy użyciu przeszkolonego modelu</span><span class="sxs-lookup"><span data-stu-id="ebc55-298">Predict with the trained model</span></span>
> * <span data-ttu-id="ebc55-299">Wdrażanie i przewidywanie z załadowanym modelem</span><span class="sxs-lookup"><span data-stu-id="ebc55-299">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="ebc55-300">Przejdź do następnego samouczka, aby dowiedzieć się więcej</span><span class="sxs-lookup"><span data-stu-id="ebc55-300">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="ebc55-301">Predykcyjny opłat za taksówkę</span><span class="sxs-lookup"><span data-stu-id="ebc55-301">Taxi Fare Predictor</span></span>](predict-prices.md)
