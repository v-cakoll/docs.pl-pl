---
title: Użyj strukturze ML.NET w scenariuszu wieloklasowej klasyfikacji problemu usługi GitHub
description: Dowiedz się, jak używać strukturze ML.NET w scenariuszu wieloklasowej klasyfikacji można klasyfikować problemy usługi GitHub, aby przypisać je do danego obszaru.
ms.date: 01/24/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 6f01357906fd4398f68dadfb35dbce816f4302c0
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55066210"
---
# <a name="tutorial-use-mlnet-in-a-multiclass-classification-scenario-to-classify-github-issues"></a><span data-ttu-id="ca1e9-103">Samouczek: Umożliwia strukturze ML.NET w scenariuszu klasyfikacji wieloklasowej klasyfikacji problemów w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-103">Tutorial: Use ML.NET in a multiclass classification scenario to classify GitHub issues.</span></span>

<span data-ttu-id="ca1e9-104">Ten przykładowy samouczek przedstawia tworzenie klasyfikatora problem usługi GitHub za pomocą używany aplikację konsoli .NET Core przy użyciu strukturze ML.NET C# w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-104">This sample tutorial illustrates using ML.NET to create a GitHub issue classifier via a .NET Core console application using C# in Visual Studio 2017.</span></span>

<span data-ttu-id="ca1e9-105">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="ca1e9-106">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="ca1e9-106">Understand the problem</span></span>
> * <span data-ttu-id="ca1e9-107">Wybierz zadanie uczenia odpowiedniej maszyny</span><span class="sxs-lookup"><span data-stu-id="ca1e9-107">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="ca1e9-108">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="ca1e9-108">Prepare your data</span></span>
> * <span data-ttu-id="ca1e9-109">Tworzenie potoku uczenia</span><span class="sxs-lookup"><span data-stu-id="ca1e9-109">Create the learning pipeline</span></span>
> * <span data-ttu-id="ca1e9-110">Ładowanie klasyfikatora</span><span class="sxs-lookup"><span data-stu-id="ca1e9-110">Load a classifier</span></span>
> * <span data-ttu-id="ca1e9-111">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="ca1e9-111">Train the model</span></span>
> * <span data-ttu-id="ca1e9-112">Ocena modelu za pomocą innego zestawu danych</span><span class="sxs-lookup"><span data-stu-id="ca1e9-112">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="ca1e9-113">Pojedyncze wystąpienie wynik danych testu przy użyciu modelu prognozowania</span><span class="sxs-lookup"><span data-stu-id="ca1e9-113">Predict a single instance of test data outcome with the model</span></span>
> * <span data-ttu-id="ca1e9-114">Przewidywanie wyników danych testów przy użyciu załadować modelu</span><span class="sxs-lookup"><span data-stu-id="ca1e9-114">Predict the test data outcomes with a loaded model</span></span>

> [!NOTE]
> <span data-ttu-id="ca1e9-115">W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-115">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="ca1e9-116">Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="ca1e9-116">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

## <a name="github-issue-sample-overview"></a><span data-ttu-id="ca1e9-117">Omówienie przykładowych problem usługi GitHub</span><span class="sxs-lookup"><span data-stu-id="ca1e9-117">GitHub issue sample overview</span></span>

<span data-ttu-id="ca1e9-118">Próbka jest aplikacją konsoli, która używa strukturze ML.NET do nauczenia modelu, która klasyfikuje i przewiduje etykieta obszar problemu w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-118">The sample is a console app that uses ML.NET to train a model that classifies and predicts the Area label for a GitHub issue.</span></span> <span data-ttu-id="ca1e9-119">Oblicza model z drugiego zestawu danych do analizy jakości dostawców.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-119">It also evaluates the model with a second dataset for quality analysis.</span></span> <span data-ttu-id="ca1e9-120">Zestawy danych problem pochodzą z repozytorium GitHub dotnet/corefx.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-120">The issue datasets are from the dotnet/corefx GitHub repo.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ca1e9-121">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="ca1e9-121">Prerequisites</span></span>

* <span data-ttu-id="ca1e9-122">[Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".</span><span class="sxs-lookup"><span data-stu-id="ca1e9-122">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="ca1e9-123">[Github generuje plik z wartościami oddzielonymi tabulatorami (issues_train.tsv)](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span><span class="sxs-lookup"><span data-stu-id="ca1e9-123">The [Github issues tab separated file (issues_train.tsv)](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span></span>
* <span data-ttu-id="ca1e9-124">[Problemy usługi Github test pliku z wartościami oddzielonymi tabulatorami (issues_test.tsv)](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span><span class="sxs-lookup"><span data-stu-id="ca1e9-124">The [Github issues test tab separated file (issues_test.tsv)](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="ca1e9-125">Maszyny uczenie się przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ca1e9-125">Machine learning workflow</span></span>

<span data-ttu-id="ca1e9-126">W tym samouczku poniżej przepływu pracy, który umożliwia proces przenoszenia w sposób uporządkowany uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-126">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="ca1e9-127">Fazy przepływu pracy są następujące:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-127">The workflow phases are as follows:</span></span>

1. <span data-ttu-id="ca1e9-128">**Omówienie problemu**</span><span class="sxs-lookup"><span data-stu-id="ca1e9-128">**Understand the problem**</span></span>
2. <span data-ttu-id="ca1e9-129">**Przygotowywanie danych**</span><span class="sxs-lookup"><span data-stu-id="ca1e9-129">**Prepare your data**</span></span>
   * <span data-ttu-id="ca1e9-130">**Ładowanie danych**</span><span class="sxs-lookup"><span data-stu-id="ca1e9-130">**Load the data**</span></span>
   * <span data-ttu-id="ca1e9-131">**Wyodrębnianie funkcji (przekształcania danych)**</span><span class="sxs-lookup"><span data-stu-id="ca1e9-131">**Extract features (Transform your data)**</span></span>
3. <span data-ttu-id="ca1e9-132">**Kompilowanie i szkolenie**</span><span class="sxs-lookup"><span data-stu-id="ca1e9-132">**Build and train**</span></span> 
   * <span data-ttu-id="ca1e9-133">**Uczenie modelu**</span><span class="sxs-lookup"><span data-stu-id="ca1e9-133">**Train the model**</span></span>
   * <span data-ttu-id="ca1e9-134">**Ocena modelu**</span><span class="sxs-lookup"><span data-stu-id="ca1e9-134">**Evaluate the model**</span></span>
4. <span data-ttu-id="ca1e9-135">**Uruchom**</span><span class="sxs-lookup"><span data-stu-id="ca1e9-135">**Run**</span></span>
   * <span data-ttu-id="ca1e9-136">**Model użycia**</span><span class="sxs-lookup"><span data-stu-id="ca1e9-136">**Model consumption**</span></span>

### <a name="understand-the-problem"></a><span data-ttu-id="ca1e9-137">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="ca1e9-137">Understand the problem</span></span>

<span data-ttu-id="ca1e9-138">Należy najpierw zrozumieć, dzięki czemu można podzielić je w dół do części obsługujące kompilowanie i uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-138">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="ca1e9-139">Potężne problem umożliwia prognozowanie i ocena wyników.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-139">Breaking  down the problem allows you to predict and evaluate the results.</span></span>

<span data-ttu-id="ca1e9-140">Ten problem, w tym samouczku jest zrozumienie przychodzące problemy usługi GitHub powierzchni należą do, aby można było oznaczyć je poprawnie priorytetyzacja i planowanie.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-140">The problem for this tutorial is to understand what area incoming GitHub issues belong to in order to label them correctly for prioritization and scheduling.</span></span>

<span data-ttu-id="ca1e9-141">Problem można podzielić na następujące:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-141">You can break down the problem to the following:</span></span>

* <span data-ttu-id="ca1e9-142">tekst tytułu problem</span><span class="sxs-lookup"><span data-stu-id="ca1e9-142">the issue title text</span></span>
* <span data-ttu-id="ca1e9-143">tekst opisu problemu</span><span class="sxs-lookup"><span data-stu-id="ca1e9-143">the issue description text</span></span>
* <span data-ttu-id="ca1e9-144">wartość obszaru danych szkoleniowych modelu</span><span class="sxs-lookup"><span data-stu-id="ca1e9-144">an area value for the model training data</span></span>
* <span data-ttu-id="ca1e9-145">wartość obszaru przewidywane, można obliczyć, a następnie za pomocą pod względem</span><span class="sxs-lookup"><span data-stu-id="ca1e9-145">a predicted area value that you can evaluate and then use operationally</span></span>

<span data-ttu-id="ca1e9-146">Następnie należy **określić** obszar, który ułatwia wybór zadań uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-146">You then need to **determine** the area, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="ca1e9-147">Wybierz zadanie uczenia odpowiedniej maszyny</span><span class="sxs-lookup"><span data-stu-id="ca1e9-147">Select the appropriate machine learning task</span></span>

<span data-ttu-id="ca1e9-148">W rozwiązaniu tego problemu znasz następujące fakty:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-148">With this problem, you know the following facts:</span></span>

<span data-ttu-id="ca1e9-149">Dane szkoleniowe:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-149">Training data:</span></span>

<span data-ttu-id="ca1e9-150">Problemy usługi GitHub może być oznaczony jako w kilku obszarach (**obszaru**) jak w następujących przykładach:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-150">GitHub issues can be labeled in several areas (**Area**) as in the following examples:</span></span>

* <span data-ttu-id="ca1e9-151">area-System.Numerics</span><span class="sxs-lookup"><span data-stu-id="ca1e9-151">area-System.Numerics</span></span>
* <span data-ttu-id="ca1e9-152">area-System.Xml</span><span class="sxs-lookup"><span data-stu-id="ca1e9-152">area-System.Xml</span></span>
* <span data-ttu-id="ca1e9-153">obszar infrastruktura</span><span class="sxs-lookup"><span data-stu-id="ca1e9-153">area-Infrastructure</span></span>
* <span data-ttu-id="ca1e9-154">area-System.Linq</span><span class="sxs-lookup"><span data-stu-id="ca1e9-154">area-System.Linq</span></span>
* <span data-ttu-id="ca1e9-155">area-System.IO</span><span class="sxs-lookup"><span data-stu-id="ca1e9-155">area-System.IO</span></span>

<span data-ttu-id="ca1e9-156">Przewidywanie **obszaru** z nowego problemu w usłudze GitHub takich jak w następujących przykładach:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-156">Predict the **Area** of a new GitHub Issue such as in the following examples:</span></span>

* <span data-ttu-id="ca1e9-157">Contract.Assert vs Debug.Assert</span><span class="sxs-lookup"><span data-stu-id="ca1e9-157">Contract.Assert vs Debug.Assert</span></span>
* <span data-ttu-id="ca1e9-158">Tworzenie pola tylko do odczytu w System.Xml</span><span class="sxs-lookup"><span data-stu-id="ca1e9-158">Make fields readonly in System.Xml</span></span>

<span data-ttu-id="ca1e9-159">Zadania uczenia maszyny klasyfikacji najlepiej nadaje się dla tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-159">The classification machine learning task is best suited for this scenario.</span></span>

### <a name="about-the-classification-task"></a><span data-ttu-id="ca1e9-160">O zadaniu klasyfikacji</span><span class="sxs-lookup"><span data-stu-id="ca1e9-160">About the classification task</span></span>

<span data-ttu-id="ca1e9-161">Klasyfikacja jest zadanie uczenia maszynowego, które są używane dane do **określić** kategorii, typ lub klasa elementu lub wiersza danych.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-161">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="ca1e9-162">Na przykład można użyć klasyfikacji:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-162">For example, you can use classification to:</span></span>

* <span data-ttu-id="ca1e9-163">Zidentyfikuj tonacji jako dodatnia lub ujemna.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-163">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="ca1e9-164">Klasyfikowanie wiadomości e-mail jako spam, wiadomości-śmieci lub właściwej.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-164">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="ca1e9-165">Ustal, czy pacjent laboratorium przykładowe dane stanowią cancerous.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-165">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="ca1e9-166">Klienci na kategorie według ich tendencje do odpowiedzi na kampanię sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-166">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="ca1e9-167">Klasyfikacja zadań są często jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-167">Classification tasks are frequently one of the following types:</span></span>

* <span data-ttu-id="ca1e9-168">Plik binarny: A i B.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-168">Binary: either A or B.</span></span>
* <span data-ttu-id="ca1e9-169">Kontra: wielu kategorii, które można przewidzieć przy użyciu pojedynczego modelu.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-169">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="ca1e9-170">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="ca1e9-170">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="ca1e9-171">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="ca1e9-171">Create a project</span></span>

1. <span data-ttu-id="ca1e9-172">Otwórz program Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-172">Open Visual Studio 2017.</span></span> <span data-ttu-id="ca1e9-173">Wybierz **pliku** > **New** > **projektu** z paska menu.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-173">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="ca1e9-174">W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła następuje **platformy .NET Core** węzła.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-174">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="ca1e9-175">Następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-175">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="ca1e9-176">W **nazwa** pole tekstowe, wpisz "SentimentAnalysis", a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-176">In the **Name** text box, type "SentimentAnalysis" and then select the **OK** button.</span></span>

2. <span data-ttu-id="ca1e9-177">Utwórz katalog o nazwie *danych* w projekcie, aby zapisać pliki zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-177">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="ca1e9-178">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nad projektem i wybierz **Dodaj** > **nowy Folder**.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-178">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="ca1e9-179">Wpisz "Dane", a następnie naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-179">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="ca1e9-180">Zainstaluj **pakietu NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-180">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="ca1e9-181">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-181">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="ca1e9-182">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-182">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="ca1e9-183">Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-183">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="ca1e9-184">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="ca1e9-184">Prepare your data</span></span>

1. <span data-ttu-id="ca1e9-185">Pobierz [issues_train.tsv](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) i [issues_test.tsv](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) danych ustawia i zapisywanie ich *danych* wcześniej utworzony folder.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-185">Download the [issues_train.tsv](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) and the [issues_test.tsv](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="ca1e9-186">Szkolenie modeli modelu uczenia maszynowego na pierwszego zestawu danych, a drugi może służyć do oceny, jak dokładna jest model.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-186">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="ca1e9-187">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy każdy z \*pliki tsv i wybierz pozycję **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-187">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="ca1e9-188">W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-188">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="ca1e9-189">Tworzenie klas i definiowania ścieżek</span><span class="sxs-lookup"><span data-stu-id="ca1e9-189">Create classes and define paths</span></span>

<span data-ttu-id="ca1e9-190">Dodaj następujące dodatkowe `using` instrukcji na górze *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-190">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

<span data-ttu-id="ca1e9-191">Musisz utworzyć trzy pola globalnego na potrzeby przechowywania ścieżek do ostatnio pobrane pliki, a dla zmiennej globalnej `TextLoader`:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-191">You need to create three global fields to hold the paths to the recently downloaded files, and a global variable for the `TextLoader`:</span></span>

* <span data-ttu-id="ca1e9-192">`_trainDataPath` zawiera ścieżkę do zestawu danych, używane do trenowania modelu.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-192">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="ca1e9-193">`_testDataPath` zawiera ścieżkę do zestawu danych, używane do oceny modelu.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-193">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="ca1e9-194">`_modelPath` ma ścieżkę, w którym jest zapisany trenowanego modelu.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-194">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="ca1e9-195">`_mlContext` jest <xref:Microsoft.ML.MLContext> zapewniający przetwarzania kontekstu.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-195">`_mlContext` is the <xref:Microsoft.ML.MLContext> that provides processing context.</span></span>
* <span data-ttu-id="ca1e9-196">`_trainingDataView` jest <xref:Microsoft.ML.Data.IDataView> używani do przetwarzania zestaw danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-196">`_trainingDataView` is the <xref:Microsoft.ML.Data.IDataView> used to process the training dataset.</span></span>
* <span data-ttu-id="ca1e9-197">`_predEngine` jest <xref:Microsoft.ML.PredictionEngine%602> używany dla pojedynczego prognozy.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-197">`_predEngine` is the <xref:Microsoft.ML.PredictionEngine%602> used for single predictions.</span></span>
* <span data-ttu-id="ca1e9-198">`_reader` jest <xref:Microsoft.ML.Data.TextLoader> używany do ładowania i przekształcić zestawy danych.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-198">`_reader` is the <xref:Microsoft.ML.Data.TextLoader> used to load and transform the datasets.</span></span>

<span data-ttu-id="ca1e9-199">Dodaj następujący kod po prawej stronie wiersza powyżej `Main` metodę, aby określić ścieżki te i inne zmienne:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-199">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="ca1e9-200">Musisz utworzyć niektóre klasy dla danych wejściowych i prognozy.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-200">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="ca1e9-201">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-201">Add a new class to your project:</span></span>

1. <span data-ttu-id="ca1e9-202">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-202">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="ca1e9-203">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *GitHubIssueData.cs*.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-203">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *GitHubIssueData.cs*.</span></span> <span data-ttu-id="ca1e9-204">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-204">Then, select the **Add** button.</span></span>

    <span data-ttu-id="ca1e9-205">*GitHubIssueData.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-205">The *GitHubIssueData.cs* file opens in the code editor.</span></span> <span data-ttu-id="ca1e9-206">Dodaj następujący kod `using` instrukcji na górze *GitHubIssueData.cs*:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-206">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

<span data-ttu-id="ca1e9-207">Usuń istniejącą definicję klasy i Dodaj następujący kod, który zawiera dwie klasy `GitHubIssue` i `IssuePrediction`, *GitHubIssueData.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-207">Remove the existing class definition and add the following code, which has two classes `GitHubIssue` and `IssuePrediction`, to the *GitHubIssueData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

<span data-ttu-id="ca1e9-208">`GitHubIssue` jest to klasa wejściowy zestaw danych i ma następujące <xref:System.String> pola:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-208">`GitHubIssue` is the input dataset class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="ca1e9-209">`ID` zawiera wartość dla Identyfikatora problemu usługi GitHub</span><span class="sxs-lookup"><span data-stu-id="ca1e9-209">`ID` contains a value for the GitHub issue ID</span></span>
* <span data-ttu-id="ca1e9-210">`Area` zawiera wartość dla `Area` etykiety</span><span class="sxs-lookup"><span data-stu-id="ca1e9-210">`Area` contains a value for the `Area` label</span></span>
* <span data-ttu-id="ca1e9-211">`Title` zawiera tytuł problemu usługi GitHub</span><span class="sxs-lookup"><span data-stu-id="ca1e9-211">`Title` contains the GitHub issue title</span></span>
* <span data-ttu-id="ca1e9-212">`Description` Zawiera opis problemu usługi GitHub</span><span class="sxs-lookup"><span data-stu-id="ca1e9-212">`Description` contains the GitHub issue description</span></span>

<span data-ttu-id="ca1e9-213">`IssuePrediction` Klasa służy do prognozowania po wyszkoliła modelu.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-213">`IssuePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="ca1e9-214">Ma on jeden `string` (`Area`) i `PredictedLabel` `ColumnName` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-214">It has a single `string` (`Area`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="ca1e9-215">`Label` Umożliwia tworzenie i uczenie modelu, a także drugiego zestawu danych do ewaluacji modelu.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-215">The `Label` is used to create and train the model, and it's also used with a second dataset to evaluate the model.</span></span> <span data-ttu-id="ca1e9-216">`PredictedLabel` Używany podczas prognoz i oceny.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-216">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="ca1e9-217">W wersji ewaluacyjnej używane są dane szkoleniowe, przewidywane wartości i model danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-217">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="ca1e9-218">Podczas tworzenia modelu za pomocą platformy ML.NET, rozpoczyna się od utworzenia <xref:Microsoft.ML.MLContext>.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-218">When building a model with ML.NET, you start by creating an <xref:Microsoft.ML.MLContext>.</span></span> <span data-ttu-id="ca1e9-219">To jest porównywalna koncepcyjnie za pomocą `DbContext` platformy Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-219">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span> <span data-ttu-id="ca1e9-220">Środowisko dostarcza kontekst dla zadania uczenia Maszynowego, który może służyć do wyjątku, śledzenie i rejestrowanie.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-220">The environment provides a context for your ML job that can be used for exception tracking and logging.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="ca1e9-221">Inicjowanie zmiennych w głównym oknie</span><span class="sxs-lookup"><span data-stu-id="ca1e9-221">Initialize variables in Main</span></span>

<span data-ttu-id="ca1e9-222">Inicjowanie `_mlContext` zmienna globalna o nowe wystąpienie klasy `MLContext` z Inicjator losowy (`seed: 0`) dla powtarzalnych/deterministyczne wyników w szkoleniach wielu.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-222">Initialize the `_mlContext` global variable  with a new instance of `MLContext` with a random seed (`seed: 0`) for repeatable/deterministic results across multiple trainings.</span></span>  <span data-ttu-id="ca1e9-223">Zastąp `Console.WriteLine("Hello World!")` wiersz poniższym kodem w `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-223">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a><span data-ttu-id="ca1e9-224">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="ca1e9-224">Load the data</span></span>

<span data-ttu-id="ca1e9-225">Następnie zainicjuj `_trainingDataView` <xref:Microsoft.ML.Data.IDataView> zmiennej globalnej i ładowanie danych za pomocą `_trainDataPath` parametru.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-225">Next, initialize the `_trainingDataView` <xref:Microsoft.ML.Data.IDataView> global variable and load the data with the `_trainDataPath` parameter.</span></span>

 <span data-ttu-id="ca1e9-226">Jako dane wejściowe i wyjściowe `Transforms`, `DataView` jest typem potoku danych podstawowych porównywalne do `IEnumerable` dla `LINQ`.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-226">As the input and output of `Transforms`, a `DataView` is the fundamental data pipeline type, comparable to `IEnumerable` for `LINQ`.</span></span>

<span data-ttu-id="ca1e9-227">W strukturze ML.NET, dane są podobne do `SQL view`.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-227">In ML.NET, data is similar to a `SQL view`.</span></span> <span data-ttu-id="ca1e9-228">Jest opóźnieniem ocenianą informatycznych i heterogenicznych.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-228">It is lazily evaluated, schematized, and heterogenous.</span></span> <span data-ttu-id="ca1e9-229">Obiekt jest pierwszą częścią potoku i służy do ładowania danych.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-229">The object is the first part of the pipeline, and loads the data.</span></span> <span data-ttu-id="ca1e9-230">W tym samouczku ładuje zestaw danych o problem tytułów, opisów i odpowiednie etykiety GitHub powierzchni.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-230">For this tutorial, it loads a dataset with issue titles, descriptions, and corresponding area GitHub label.</span></span> <span data-ttu-id="ca1e9-231">`DataView` Umożliwia tworzenie i trenowanie modelu.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-231">The `DataView` is used to create and train the model.</span></span>

<span data-ttu-id="ca1e9-232">Ponieważ utworzone wcześniej `GitHubIssue` typ modelu danych jest zgodny schemat zestawu danych, można połączyć inicjowania, mapowanie i zestaw danych ładowania do jednego wiersza kodu.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-232">Since your previously created `GitHubIssue` data model type matches the dataset schema, you can combine the initialization, mapping, and dataset loading into one line of code.</span></span>

<span data-ttu-id="ca1e9-233">Pierwsza część wiersza (`CreateTextReader<GitHubIssue>(hasHeader: true)`) tworzy <xref:Microsoft.ML.Data.TextLoader> przez wnioskowania schematu zestawu danych z `GitHubIssue` modelu danych, typ i przy użyciu nagłówka zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-233">The first part of the line (`CreateTextReader<GitHubIssue>(hasHeader: true)`) creates a <xref:Microsoft.ML.Data.TextLoader> by inferencing the dataset schema from the `GitHubIssue` data model type and using the dataset header.</span></span>

<span data-ttu-id="ca1e9-234">Wcześniej zdefiniowany schemat danych podczas tworzenia `GitHubIssue` klasy.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-234">You defined the data schema previously when you created the `GitHubIssue` class.</span></span> <span data-ttu-id="ca1e9-235">Dla schematu:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-235">For your schema:</span></span>

* <span data-ttu-id="ca1e9-236">Pierwsza kolumna `ID` (identyfikator problemu usługi GitHub)</span><span class="sxs-lookup"><span data-stu-id="ca1e9-236">the first column `ID` (GitHub Issue ID)</span></span>
* <span data-ttu-id="ca1e9-237">druga kolumna `Area` (prognozowane potrzeby szkolenia)</span><span class="sxs-lookup"><span data-stu-id="ca1e9-237">the second column `Area` (the prediction for training)</span></span>
* <span data-ttu-id="ca1e9-238">trzecia kolumna `Title` (tytuł problemu usługi GitHub) jest to pierwszy [funkcji](../resources/glossary.md##feature) używane do prognozowania `Area`</span><span class="sxs-lookup"><span data-stu-id="ca1e9-238">the third column `Title` (GitHub issue title) is the first [feature](../resources/glossary.md##feature)  used for predicting the `Area`</span></span>
* <span data-ttu-id="ca1e9-239">Czwarta kolumna `Description` jest druga funkcja używana do prognozowania `Area`</span><span class="sxs-lookup"><span data-stu-id="ca1e9-239">the fourth column  `Description` is the second feature used for predicting the `Area`</span></span>

<span data-ttu-id="ca1e9-240">Druga część wiersza (`.Read(_trainDataPath)`) używa <xref:Microsoft.ML.Data.TextLoader.Read%2A> metodę, aby załadować tekstu szkolenia plików przy użyciu `_trainDataPath` do `IDataView` (`_trainingDataView`) zmiennej globalnej.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-240">The second part of the line  (`.Read(_trainDataPath)`) uses <xref:Microsoft.ML.Data.TextLoader.Read%2A> method to load the training text file using `_trainDataPath` into the `IDataView` (`_trainingDataView`) global variable.</span></span>  

<span data-ttu-id="ca1e9-241">Aby zainicjować i załadować `_trainingDataView` zmienna globalna, aby mógł zostać użyty dla potoku, Dodaj następujący kod po `mlContext` inicjowania:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-241">To initialize and load the `_trainingDataView` global variable in order to use it for the pipeline, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]


<span data-ttu-id="ca1e9-242">Dodaj następujący kod jako następnego wiersza kodu w `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-242">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallProcessData](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

<span data-ttu-id="ca1e9-243">`ProcessData` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-243">The `ProcessData` method executes the following tasks:</span></span>

* <span data-ttu-id="ca1e9-244">Wyodrębnia i przekształca dane.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-244">Extracts and transforms the data.</span></span>
* <span data-ttu-id="ca1e9-245">Zwraca potoku przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-245">Returns the processing pipeline.</span></span>

<span data-ttu-id="ca1e9-246">Tworzenie `ProcessData` metody tuż za `Main` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-246">Create the `ProcessData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static EstimatorChain<ITransformer> ProcessData()
{

}
```

## <a name="extract-and-transform-the-data"></a><span data-ttu-id="ca1e9-247">Wyodrębnianie i przekształcania danych</span><span class="sxs-lookup"><span data-stu-id="ca1e9-247">Extract and transform the data</span></span>

<span data-ttu-id="ca1e9-248">Wstępne przetwarzanie i czyszczenie danych są ważne zadania, które występują przed zestaw danych jest efektywnie używać uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-248">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="ca1e9-249">Nieprzetworzone dane są często hałas i zawodnych i może brakować wartości.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-249">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="ca1e9-250">Korzystanie z danych bez tych zadań modelowania może spowodować wyświetlenie nieprawdziwych wyników.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-250">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="ca1e9-251">UCZENIE MASZYNOWE. Potoki przekształcenie firmy NET tworzą zbiór niestandardowych przekształceń, które są stosowane do danych przed szkolenie i testowanie.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-251">ML.NET's transform pipelines compose a custom set of transforms that are applied to your data before training or testing.</span></span> <span data-ttu-id="ca1e9-252">Przekształcenia głównym celem jest danych [cechowania](../resources/glossary.md#feature-engineering).</span><span class="sxs-lookup"><span data-stu-id="ca1e9-252">The transforms' primary purpose is data [featurization](../resources/glossary.md#feature-engineering).</span></span> <span data-ttu-id="ca1e9-253">Omówienie algorytmów uczenia maszynowego [neural](../resources/glossary.md#feature) dane, dzięki czemu następnym krokiem jest do przekształcania danych tekstowych do formatu, który rozpoznaje nasze algorytmy uczenia Maszynowego.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-253">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, so the next step is to transform our textual data into a format that our ML algorithms recognize.</span></span> <span data-ttu-id="ca1e9-254">Ten format jest [liczbowych wektor](../resources/glossary.md#numerical-feature-vector).</span><span class="sxs-lookup"><span data-stu-id="ca1e9-254">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="ca1e9-255">W następnych krokach nazywamy kolumny według nazw zdefiniowana w `GitHubIssue` klasy.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-255">In the next steps, we refer to the columns by the names defined in the `GitHubIssue` class.</span></span>

<span data-ttu-id="ca1e9-256">Gdy wiedzę i oceniane, domyślne wartości w modelu **etykiety** kolumny będą traktowane jako prawidłowe wartości do można przewidzieć.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-256">When the model is trained and evaluated, by default, the values in the **Label** column are considered as correct values to be predicted.</span></span> <span data-ttu-id="ca1e9-257">Ponieważ chcemy przewidzieć etykieta GitHub powierzchni `GitHubIssue`, kopia `Area` kolumny na **etykiety** kolumny.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-257">As we want to predict the Area GitHub label for a `GitHubIssue`, copy the `Area` column into the **Label** column.</span></span> <span data-ttu-id="ca1e9-258">Aby to zrobić, należy użyć `MLContext.Transforms.Conversion.MapValueToKey`, który jest otoką <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A> klasy przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-258">To do that, use the `MLContext.Transforms.Conversion.MapValueToKey`, which is a wrapper for the <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A> transformation class.</span></span>  <span data-ttu-id="ca1e9-259">`MapValueToKey` Zwraca <xref:Microsoft.ML.Data.EstimatorChain%601> skutecznie się potoku.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-259">The `MapValueToKey` returns an <xref:Microsoft.ML.Data.EstimatorChain%601> that will effectively be a pipeline.</span></span> <span data-ttu-id="ca1e9-260">Nazwij to `pipeline` jako następnie dołączy trainer do `EstimatorChain`.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-260">Name this `pipeline` as you will then append the trainer to the `EstimatorChain`.</span></span> <span data-ttu-id="ca1e9-261">Dodaj jako następnego wiersza kodu:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-261">Add this as the next line of code:</span></span>

[!code-csharp[MapValueToKey](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

<span data-ttu-id="ca1e9-262">Algorytm, który przygotowuje model wymaga **liczbowych** wywołania funkcji, więc trzeba następnie `mlContext.Transforms.Text.FeaturizeText` które featurizes tekst (`Title` i `Description`) kolumny liczbowe wektor dla każdego o nazwie `TitleFeaturized` i `DescriptionFeaturized`.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-262">The algorithm that trains the model requires **numeric** features, so you have Next, call `mlContext.Transforms.Text.FeaturizeText` which featurizes the text (`Title` and `Description`) columns into a numeric vector for each called `TitleFeaturized` and `DescriptionFeaturized`.</span></span> <span data-ttu-id="ca1e9-263">Featurizing różnych wartości kluczowych numeryczne są przypisane różne wartości w każdej z kolumn i jest używany przez algorytmu uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-263">Featurizing assigns different numeric key values to the different values in each of the columns and is used by the machine learning algorithm.</span></span>
<span data-ttu-id="ca1e9-264">Dołącz cechowania dla obu kolumn do potoku z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-264">Append the featurization for both columns to the pipeline with the following code:</span></span>

[!code-csharp[FeaturizeText](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

<span data-ttu-id="ca1e9-265">Ostatnim krokiem w przygotowaniu danych łączy wszystkie kolumny funkcji do **funkcji** przy użyciu kolumny `Concatenate` klasy przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-265">The last step in data preparation combines all of the feature columns into the **Features** column using the `Concatenate` transformation class.</span></span> <span data-ttu-id="ca1e9-266">Domyślnie algorytmu uczenia przetwarza tylko funkcje z **funkcji** kolumny.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-266">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="ca1e9-267">Dołącz to przekształcenie do potoku z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-267">Append this transformation to the pipeline with the following code:</span></span>

[!code-csharp[Concatenate](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 <span data-ttu-id="ca1e9-268">Następnie dołącz <xref:Microsoft.ML.Data.EstimatorChain`1.AppendCacheCheckpoint%2A> w pamięci podręcznej widoku danych, dzięki czemu podczas iteracji przez dane wielokrotnie przy użyciu pamięci podręcznej mogą uzyskać lepszą wydajność, zgodnie z poniższym kodem</span><span class="sxs-lookup"><span data-stu-id="ca1e9-268">Next, append a <xref:Microsoft.ML.Data.EstimatorChain`1.AppendCacheCheckpoint%2A> to cache the DataView so when you iterate over the data multiple times using the cache might get better performance, as with the following code</span></span>

[!code-csharp[AppendCache](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

<span data-ttu-id="ca1e9-269">Zwróć potoku na końcu `ProcessData` metody.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-269">Return the pipeline at the end of the `ProcessData` method.</span></span>

[!code-csharp[ReturnPipeline](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

<span data-ttu-id="ca1e9-270">W tym kroku obsługuje przetwarzania wstępnego cechowania.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-270">This step handles preprocessing/featurization.</span></span> <span data-ttu-id="ca1e9-271">Za pomocą dodatkowych składników dostępnych w strukturze ML.NET umożliwiają lepsze wyniki za pomocą modelu.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-271">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="build-and-train-the-model"></a><span data-ttu-id="ca1e9-272">Tworzenie i trenowanie modelu</span><span class="sxs-lookup"><span data-stu-id="ca1e9-272">Build and train the model</span></span>

<span data-ttu-id="ca1e9-273">Dodaj następujące wywołanie do `BuildAndTrainModel`metodę jako następnego wiersza kodu w `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-273">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="ca1e9-274">`BuildAndTrainModel` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-274">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="ca1e9-275">Tworzy klasę algorytm szkolenia.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-275">Creates the training algorithm class.</span></span>
* <span data-ttu-id="ca1e9-276">Szkolenie modeli modelu.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-276">Trains the model.</span></span>
* <span data-ttu-id="ca1e9-277">Prognozuje obszaru, w oparciu o dane szkoleniowe.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-277">Predicts area based on training data.</span></span>
* <span data-ttu-id="ca1e9-278">Zapisuje modelu, który ma `.zip` pliku.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-278">Saves the model to a `.zip` file.</span></span>
* <span data-ttu-id="ca1e9-279">Zwraca wartość modelu.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-279">Returns the model.</span></span>

<span data-ttu-id="ca1e9-280">Tworzenie `BuildAndTrainModel` metody tuż za `Main` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-280">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static void BuildAndTrainModel()
{

}
```

<span data-ttu-id="ca1e9-281">Należy zauważyć, że dwa parametry są przekazywane do metody BuildAndTrainModel; `IDataView` dla zestawu danych szkoleniowych (`trainingDataView`), a <xref:Microsoft.ML.Data.EstimatorChain%601> dla potoku przetwarzania utworzonych w ProcessData (`pipeline`).</span><span class="sxs-lookup"><span data-stu-id="ca1e9-281">Notice that two parameters are passed into the BuildAndTrainModel method; an `IDataView` for the training dataset (`trainingDataView`), and a <xref:Microsoft.ML.Data.EstimatorChain%601> for the processing pipeline created in ProcessData (`pipeline`).</span></span>

 <span data-ttu-id="ca1e9-282">Dodaj następujący kod jako pierwsza linia `BuildAndTrainModel` metody:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-282">Add the following code as the first line of the `BuildAndTrainModel` method:</span></span>

### <a name="choose-a-trainer-algorithm"></a><span data-ttu-id="ca1e9-283">Wybieranie algorytmu instruktora</span><span class="sxs-lookup"><span data-stu-id="ca1e9-283">Choose a trainer algorithm</span></span>

<span data-ttu-id="ca1e9-284">Aby dodać algorytm trainer, należy wywołać `mlContext.Transforms.Text.FeaturizeText` metody otoki, która zwraca <xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer> obiektu.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-284">To add the trainer algorithm, call the `mlContext.Transforms.Text.FeaturizeText` wrapper method which returns a <xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer> object.</span></span> <span data-ttu-id="ca1e9-285">Jest to uczeń drzewa decyzyjne, które będą używane w tym potoku.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-285">This is a decision tree learner you'll use in this pipeline.</span></span> <span data-ttu-id="ca1e9-286">`SdcaMultiClassTrainer` Jest dołączany do `pipeline` i akceptuje neural `Title` i `Description` (`Features`) i `Label` parametrów, aby dowiedzieć się więcej na podstawie historycznych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-286">The `SdcaMultiClassTrainer` is appended to the `pipeline` and accepts the featurized `Title` and `Description` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

<span data-ttu-id="ca1e9-287">Dodaj następujący kod do `BuildAndTrainModel` metody:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-287">Add the following code to the `BuildAndTrainModel` method:</span></span>

[!code-csharp[SdcaMultiClassTrainer](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SdcaMultiClassTrainer)]

<span data-ttu-id="ca1e9-288">Teraz, po utworzeniu algorytm trainer, dołącz go do `pipeline`.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-288">Now that you've created a trainer algorithm, append it to the `pipeline`.</span></span> <span data-ttu-id="ca1e9-289">Należy również mapować etykiety na wartość, aby powrócić do stanu pierwotnego do odczytu.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-289">You also need to map the label to the value to return to its original readable state.</span></span> <span data-ttu-id="ca1e9-290">Czy obu tych akcji, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-290">Do both of those actions with the following code:</span></span>

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

### <a name="train-the-model"></a><span data-ttu-id="ca1e9-291">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="ca1e9-291">Train the model</span></span>

<span data-ttu-id="ca1e9-292">Uczenie modelu, <xref:Microsoft.ML.Data.TransformerChain%601>zgodnie z zestawu danych, który został załadowany i przekształcone.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-292">You train the model, <xref:Microsoft.ML.Data.TransformerChain%601>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="ca1e9-293">Po zdefiniowaniu estymatora uczenie modelu przy użyciu <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> przy jednoczesnym zapewnieniu dane szkoleniowe już załadowana.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-293">Once the estimator has been defined, you train your model using the <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> while providing the already loaded training data.</span></span> <span data-ttu-id="ca1e9-294">Spowoduje to zwrócenie modelu na potrzeby prognozy.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-294">This returns a model to use for predictions.</span></span> <span data-ttu-id="ca1e9-295">`trainingPipeline.Fit()` szkolenie modeli potoku i zwraca `Transformer` na podstawie `DataView` przekazany.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-295">`trainingPipeline.Fit()` trains the pipeline and returns a `Transformer` based on the `DataView` passed in.</span></span> <span data-ttu-id="ca1e9-296">Eksperyment nie jest wykonywane, dopóki nie dzieje.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-296">The experiment is not executed until this happens.</span></span>

<span data-ttu-id="ca1e9-297">Dodaj następujący kod do `BuildAndTrainModel` metody:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-297">Add the following code to the `BuildAndTrainModel` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

<span data-ttu-id="ca1e9-298">Gdy `model` jest `transformer` który operuje na wiele wierszy danych, to bardzo typowy scenariusz w środowisku produkcyjnym jest na potrzeby prognoz na poszczególne przykłady.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-298">While the `model` is a `transformer` that operates on many rows of data, a very common production scenario is a need for predictions on individual examples.</span></span> <span data-ttu-id="ca1e9-299"><xref:Microsoft.ML.PredictionEngine%602> Jest otoką, który jest zwracany z `CreatePredictionEngine` metody.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-299">The <xref:Microsoft.ML.PredictionEngine%602> is a wrapper that is returned from the `CreatePredictionEngine` method.</span></span> <span data-ttu-id="ca1e9-300">Możemy dodać następujący kod, aby utworzyć `PredictionEngine` w następnym wierszu `BuildAndTrainModel` metody:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-300">Let's add the following code to create the `PredictionEngine` as the next line in the `BuildAndTrainModel` Method:</span></span>

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]

<span data-ttu-id="ca1e9-301">Dodaj problem w usłudze GitHub do testowania uczonego modelu prognozowania w `Predict` metody przez utworzenie wystąpienia `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-301">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[CreateTestIssue1](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

<span data-ttu-id="ca1e9-302">Można go używać, aby przewidzieć `Area` etykiety pojedyncze wystąpienie danych problem.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-302">You can use that to predict the `Area` label of a single instance of the issue data.</span></span> <span data-ttu-id="ca1e9-303">Aby uzyskać prognozę, użyj <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> na danych.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-303">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="ca1e9-304">Należy pamiętać, że dane wejściowe to ciąg, a model zawiera cechowania.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-304">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="ca1e9-305">Potok jest zsynchronizowany podczas uczenia i przewidywania.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-305">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="ca1e9-306">Nie trzeba napisać kod przetwarzania wstępnego cechowania specjalnie dla prognoz i zajmuje się tego samego interfejsu API i usługi batch jednorazowe prognozy.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-306">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="model-operationalization-prediction"></a><span data-ttu-id="ca1e9-307">Model operacjonalizacji: prognoz</span><span class="sxs-lookup"><span data-stu-id="ca1e9-307">Model operationalization: prediction</span></span>

<span data-ttu-id="ca1e9-308">Wyświetlanie `GitHubIssue` i odpowiadających im `Area` etykiety prognozowania, aby można było udostępnić wyniki i podejmowanie odpowiednich działań na nich.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-308">Display `GitHubIssue` and corresponding `Area` label prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="ca1e9-309">Jest to nazywane operacjonalizacji, jako część zasad operacyjnych przy użyciu zwracanych danych.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-309">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="ca1e9-310">Tworzenie ekranu wyników za pomocą następujących <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-310">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="ca1e9-311">Zapisz i wróć, czy model jest uczony na potrzeby oceny</span><span class="sxs-lookup"><span data-stu-id="ca1e9-311">Save and return the model trained to use for evaluation</span></span>

<span data-ttu-id="ca1e9-312">W tym momencie masz model typu <xref:Microsoft.ML.Data.TransformerChain%601> , można zintegrować wszystkich istniejących i nowych aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-312">At this point, you have a model of type <xref:Microsoft.ML.Data.TransformerChain%601> that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="ca1e9-313">Aby zapisać uczonego modelu w pliku .zip, Dodaj następujący kod do wywoływania `SaveModelAsFile` metody w następnym wierszu `BuildAndTrainModel`:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-313">To save your trained model to a .zip file, add the following code to call the `SaveModelAsFile` method as the next line in `BuildAndTrainModel`:</span></span>

[!code-csharp[CallSaveModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallSaveModel)]

<span data-ttu-id="ca1e9-314">Zwraca model na końcu `BuildAndTrainModel` metody.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-314">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="save-the-model-as-azip-file"></a><span data-ttu-id="ca1e9-315">Zapisz model jako plik a.zip</span><span class="sxs-lookup"><span data-stu-id="ca1e9-315">Save the model as a.zip file</span></span>

<span data-ttu-id="ca1e9-316">Tworzenie `SaveModelAsFile` metody tuż za `BuildAndTrainModel` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-316">Create the `SaveModelAsFile` method, just after the `BuildAndTrainModel` method, using the following code:</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="ca1e9-317">`SaveModelAsFile` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-317">The `SaveModelAsFile` method executes the following tasks:</span></span>

* <span data-ttu-id="ca1e9-318">Zapisuje modelu w postaci pliku zip.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-318">Saves the model as a .zip file.</span></span>

<span data-ttu-id="ca1e9-319">Następnie utwórz metodę, aby zapisać modelu mogą być używane ponownie i używane w innych aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-319">Next, create a method to save the model so that it can be reused and consumed in other applications.</span></span> <span data-ttu-id="ca1e9-320">`ITransformer` Ma <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> metodę, która przyjmuje `_modelPath` globalne pola i <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-320">The `ITransformer` has a <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> method that takes in the `_modelPath` global field, and a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="ca1e9-321">Aby zapisać ten element jako plik zip, należy utworzyć `FileStream` bezpośrednio przed wywołaniem `SaveTo` metody.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-321">To save this as a zip file, you'll create the `FileStream` immediately before calling the `SaveTo` method.</span></span> <span data-ttu-id="ca1e9-322">Dodaj następujący kod do `SaveModelAsFile` metodę jako następny wiersz:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-322">Add the following code to the `SaveModelAsFile` method as the next line:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SaveModel)]

<span data-ttu-id="ca1e9-323">Można również wyświetlić, którym został zapisany plik przy pisaniu komunikatu konsoli, za pomocą `_modelPath`, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-323">You could also display where the file was written by writing a console message with the `_modelPath`, using the following code:</span></span>

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="evaluate-the-model"></a><span data-ttu-id="ca1e9-324">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="ca1e9-324">Evaluate the model</span></span>

<span data-ttu-id="ca1e9-325">Teraz, po utworzeniu i uczony model, należy ocenić ją z innego zestawu danych do zapewniania jakości i sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-325">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="ca1e9-326">W `Evaluate` metody, model utworzony w `BuildAndTrainModel` jest przekazywany do obliczenia.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-326">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="ca1e9-327">Tworzenie `Evaluate` metody tuż za `BuildAndTrainModel`, jak w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-327">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate()
{

}
```

<span data-ttu-id="ca1e9-328">`Evaluate` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-328">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="ca1e9-329">Ładuje zestawy danych testowych.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-329">Loads the test dataset.</span></span>
* <span data-ttu-id="ca1e9-330">Tworzy ewaluatora wieloklasowej.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-330">Creates the multiclass evaluator.</span></span>
* <span data-ttu-id="ca1e9-331">Oblicza model oraz tworzenie metryk.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-331">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="ca1e9-332">Przedstawia metryki.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-332">Displays the metrics.</span></span>

<span data-ttu-id="ca1e9-333">Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `BuildAndTrainModel` wywołania metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-333">Add a call to the new method from the `Main` method, right under the `BuildAndTrainModel` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

<span data-ttu-id="ca1e9-334">Tak jak poprzednio w przypadku zestawu danych szkoleniowych, można łączyć inicjowania, mapowanie i testów ładowania w jednym wierszu kodu zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-334">As you did previously with the training dataset, you can combine the initialization, mapping, and test dataset loading into one line of code.</span></span> <span data-ttu-id="ca1e9-335">Możesz ocenić modelu przy użyciu tego zestawu danych w celu sprawdzenia jakości.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-335">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="ca1e9-336">Dodaj następujący kod do `Evaluate` metody:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-336">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

<span data-ttu-id="ca1e9-337">`MulticlassClassificationContext.Evaluate` Jest otoką <xref:Microsoft.ML.MulticlassClassificationContext.Evaluate%2A> metody, które oblicza metryk jakości dla modelu przy użyciu określonego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-337">The `MulticlassClassificationContext.Evaluate` is a wrapper for the <xref:Microsoft.ML.MulticlassClassificationContext.Evaluate%2A> method that computes the quality metrics for the model using the specified dataset.</span></span> <span data-ttu-id="ca1e9-338">Zwraca <xref:Microsoft.ML.Data.MultiClassClassifierMetrics> obiekt, który zawiera metryki ogólną obliczone przez ewaluatory klasyfikacji wieloklasowej.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-338">It returns a <xref:Microsoft.ML.Data.MultiClassClassifierMetrics> object that contains the overall metrics computed by multiclass classification evaluators.</span></span>
<span data-ttu-id="ca1e9-339">Aby je wyświetlić, aby określić jakość modelu, należy pobrać pierwszy metryki.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-339">To display these to determine the quality of the model, you need to get the metrics first.</span></span>
<span data-ttu-id="ca1e9-340">Zwróć uwagę na `Transform` metoda uczenia maszynowego `_trainedModel` zmiennej globalnej (transformatora) do wprowadzania funkcji i zwracają prognozy.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-340">Notice the use of the `Transform` method of the machine learning `_trainedModel` global variable (a transformer) to input the features and return predictions.</span></span> <span data-ttu-id="ca1e9-341">Dodaj następujący kod do `Evaluate` metodę jako następny wiersz:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-341">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

<span data-ttu-id="ca1e9-342">Następujące metryki są oceniane pod kątem wieloklasowej klasyfikacji:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-342">The following metrics are evaluated for multiclass classification:</span></span>

* <span data-ttu-id="ca1e9-343">Dokładność Micro - każdej pary przykładową klasę przyczynia się jednakowo do metryki dokładności.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-343">Micro Accuracy - Every sample-class pair contributes equally to the accuracy metric.</span></span>  <span data-ttu-id="ca1e9-344">Chcesz, aby dokładność Micro być jak zbliżone do wartości 1, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-344">You want Micro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="ca1e9-345">Dokładność — makro — każda klasa przyczynia się jednakowo do metryki dokładności.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-345">Macro Accuracy - Every class contributes equally to the accuracy metric.</span></span> <span data-ttu-id="ca1e9-346">Moduł klasy są podane weight równe jako większych klas.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-346">Minority classes are given equal weight as the larger classes.</span></span> <span data-ttu-id="ca1e9-347">Chcesz, aby dokładność — makro sposób maksymalnie zbliżony 1, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-347">You want Macro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="ca1e9-348">Dziennik utraty — zobacz [utraty dziennika](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="ca1e9-348">Log-loss - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="ca1e9-349">Ma dziennik utraty sposób maksymalnie zbliżony zero, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-349">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="ca1e9-350">Zmniejszenie dziennika utraty — zakresy z [-inf, 100], gdzie 100 to doskonałe prognoz i 0 wskazuje średnią prognozy.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-350">Log-loss reduction - Ranges from [-inf, 100], where 100 is perfect predictions and 0 indicates mean predictions.</span></span> <span data-ttu-id="ca1e9-351">Chcesz, aby zmniejszenie dziennika utraty sposób maksymalnie zbliżony zero, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-351">You want Log-loss reduction to be as close to zero as possible.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="ca1e9-352">Wyświetlanie metryki dotyczące weryfikacji modelu</span><span class="sxs-lookup"><span data-stu-id="ca1e9-352">Displaying the metrics for model validation</span></span>

<span data-ttu-id="ca1e9-353">Użyj poniższego kodu, aby wyświetlić metryki, udostępnianie wyników, a następnie działanie na nich:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-353">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

## <a name="predict-the-test-data-outcome-with-the-saved-model"></a><span data-ttu-id="ca1e9-354">Wynik testu danych przy użyciu zapisanych modelu prognozowania</span><span class="sxs-lookup"><span data-stu-id="ca1e9-354">Predict the test data outcome with the saved model</span></span>

<span data-ttu-id="ca1e9-355">Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `Evaluate` wywołania metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-355">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredictIssue](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

<span data-ttu-id="ca1e9-356">Tworzenie `PredictIssue` metody tuż za `Evaluate` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-356">Create the `PredictIssue` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void PredictIssue()
{

}
```

<span data-ttu-id="ca1e9-357">`PredictIssue` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-357">The `PredictIssue` method executes the following tasks:</span></span>

* <span data-ttu-id="ca1e9-358">Tworzy jeden problem danych testowych.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-358">Creates a single issue of test data.</span></span>
* <span data-ttu-id="ca1e9-359">Prognozuje obszaru na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-359">Predicts Area based on test data.</span></span>
* <span data-ttu-id="ca1e9-360">Łączy w sobie testowanie, danych i prognoz dla raportowania.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-360">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="ca1e9-361">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-361">Displays the predicted results.</span></span>

<span data-ttu-id="ca1e9-362">Najpierw załadować modelu, które zostały zapisane wcześniej z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-362">First, load the model that you saved previously with the following code:</span></span>

[!code-csharp[LoadModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadModel)]

<span data-ttu-id="ca1e9-363">Dodaj problem w usłudze GitHub do testowania uczonego modelu prognozowania w `Predict` metody przez utworzenie wystąpienia `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-363">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[AddTestIssue](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]
  
<span data-ttu-id="ca1e9-364">Teraz, gdy model, możesz go używać, aby przewidzieć etykieta GitHub powierzchni pojedyncze wystąpienie danych problem usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-364">Now that you have a model, you can use that to predict the Area GitHub label of a single instance of the GitHub issue data.</span></span> <span data-ttu-id="ca1e9-365">Aby uzyskać prognozę, użyj <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> na danych.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-365">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="ca1e9-366">Należy pamiętać, że dane wejściowe to ciąg, a model zawiera cechowania.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-366">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="ca1e9-367">Potok jest zsynchronizowany podczas uczenia i przewidywania.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-367">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="ca1e9-368">Nie trzeba napisać kod przetwarzania wstępnego cechowania specjalnie dla prognoz i zajmuje się tego samego interfejsu API i usługi batch jednorazowe prognozy.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-368">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span> <span data-ttu-id="ca1e9-369">Dodaj następujący kod do `PredictIssue` metodę dla prognoz:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-369">Add the following code to the `PredictIssue` method for the predictions:</span></span>

[!code-csharp[PredictIssue](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]

### <a name="model-operationalization-prediction"></a><span data-ttu-id="ca1e9-370">Model operacjonalizacji: prognoz</span><span class="sxs-lookup"><span data-stu-id="ca1e9-370">Model operationalization: prediction</span></span>

<span data-ttu-id="ca1e9-371">Wyświetlanie `Area` celu kategoryzowania problem i odpowiednie do nich działanie na nim.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-371">Display `Area` in order to categorize the issue and act on it accordingly.</span></span> <span data-ttu-id="ca1e9-372">Jest to nazywane operacjonalizacji, jako część zasad operacyjnych przy użyciu zwracanych danych.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-372">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="ca1e9-373">Tworzenie ekranu wyników za pomocą następujących <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-373">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayResults](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a><span data-ttu-id="ca1e9-374">Wyniki</span><span class="sxs-lookup"><span data-stu-id="ca1e9-374">Results</span></span>

<span data-ttu-id="ca1e9-375">Wyniki powinny być podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-375">Your results should be similar to the following.</span></span> <span data-ttu-id="ca1e9-376">Ponieważ przetwarza potoku, wyświetla komunikaty.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-376">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="ca1e9-377">Może zostać wyświetlony ostrzeżenia lub komunikaty przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-377">You may see warnings, or processing messages.</span></span> <span data-ttu-id="ca1e9-378">Te zostały usunięte z następujących wyników dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-378">These have been removed from the following results for clarity.</span></span>

```console
=============== Single Prediction just-trained-model - Result: area-System.Net ===============
The model is saved to C:\Users\johalex\dotnet-samples\samples\machine-learning\tutorials\GitHubIssueClassification\bin\Debug\netcoreapp2.0\..\..\..\Models\model.zip
*************************************************************************************************************
*       Metrics for Multi-class Classification model - Test Data
*------------------------------------------------------------------------------------------------------------
*       MicroAccuracy:    0.74
*       MacroAccuracy:    0.687
*       LogLoss:          .932
*       LogLossReduction: 63.852
*************************************************************************************************************
=============== Single Prediction - Result: area-System.Data ===============
```

<span data-ttu-id="ca1e9-379">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="ca1e9-379">Congratulations!</span></span> <span data-ttu-id="ca1e9-380">Teraz został pomyślnie skompilowany usługi machine learning model do klasyfikowania i prognozowanie etykieta obszar problemu w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-380">You've now successfully built a machine learning model for classifying and predicting an Area label for a GitHub issue.</span></span> <span data-ttu-id="ca1e9-381">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="ca1e9-381">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ca1e9-382">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="ca1e9-382">Next steps</span></span>

<span data-ttu-id="ca1e9-383">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="ca1e9-383">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="ca1e9-384">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="ca1e9-384">Understand the problem</span></span>
> * <span data-ttu-id="ca1e9-385">Wybierz zadanie uczenia odpowiedniej maszyny</span><span class="sxs-lookup"><span data-stu-id="ca1e9-385">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="ca1e9-386">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="ca1e9-386">Prepare your data</span></span>
> * <span data-ttu-id="ca1e9-387">Tworzenie potoku uczenia</span><span class="sxs-lookup"><span data-stu-id="ca1e9-387">Create the learning pipeline</span></span>
> * <span data-ttu-id="ca1e9-388">Ładowanie klasyfikatora</span><span class="sxs-lookup"><span data-stu-id="ca1e9-388">Load a classifier</span></span>
> * <span data-ttu-id="ca1e9-389">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="ca1e9-389">Train the model</span></span>
> * <span data-ttu-id="ca1e9-390">Ocena modelu za pomocą innego zestawu danych</span><span class="sxs-lookup"><span data-stu-id="ca1e9-390">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="ca1e9-391">Przewidywanie wyników danych testów przy użyciu modelu</span><span class="sxs-lookup"><span data-stu-id="ca1e9-391">Predict the test data outcomes with the model</span></span>

<span data-ttu-id="ca1e9-392">Przejdź do następnego samouczka, aby dowiedzieć się więcej</span><span class="sxs-lookup"><span data-stu-id="ca1e9-392">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="ca1e9-393">Taxi Fare Predictor</span><span class="sxs-lookup"><span data-stu-id="ca1e9-393">Taxi Fare Predictor</span></span>](taxi-fare.md)
