---
title: Użyj strukturze ML.NET w scenariuszu wieloklasowej klasyfikacji problemu usługi GitHub
description: Dowiedz się, jak używać strukturze ML.NET w scenariuszu wieloklasowej klasyfikacji można klasyfikować problemy usługi GitHub, aby przypisać je do danego obszaru.
ms.date: 02/14/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 80f4e322ee94e9c3a41bd1c3945383f89f4347d0
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/16/2019
ms.locfileid: "56333524"
---
# <a name="tutorial-use-mlnet-in-a-multiclass-classification-scenario-to-classify-github-issues"></a><span data-ttu-id="ea30a-103">Samouczek: Umożliwia strukturze ML.NET w scenariuszu klasyfikacji wieloklasowej klasyfikacji problemów w usłudze GitHub</span><span class="sxs-lookup"><span data-stu-id="ea30a-103">Tutorial: Use ML.NET in a multiclass classification scenario to classify GitHub issues</span></span>

<span data-ttu-id="ea30a-104">Ten przykładowy samouczek przedstawia tworzenie klasyfikatora problem usługi GitHub za pomocą używany aplikację konsoli .NET Core przy użyciu strukturze ML.NET C# w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="ea30a-104">This sample tutorial illustrates using ML.NET to create a GitHub issue classifier via a .NET Core console application using C# in Visual Studio 2017.</span></span>

<span data-ttu-id="ea30a-105">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="ea30a-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="ea30a-106">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="ea30a-106">Understand the problem</span></span>
> * <span data-ttu-id="ea30a-107">Wybieranie algorytmu uczenia maszynowego odpowiednie</span><span class="sxs-lookup"><span data-stu-id="ea30a-107">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="ea30a-108">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="ea30a-108">Prepare your data</span></span>
> * <span data-ttu-id="ea30a-109">Przekształcanie danych</span><span class="sxs-lookup"><span data-stu-id="ea30a-109">Transform the data</span></span>
> * <span data-ttu-id="ea30a-110">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="ea30a-110">Train the model</span></span>
> * <span data-ttu-id="ea30a-111">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="ea30a-111">Evaluate the model</span></span>
> * <span data-ttu-id="ea30a-112">Prognozowanie za pomocą uczonego modelu</span><span class="sxs-lookup"><span data-stu-id="ea30a-112">Predict with the trained model</span></span>
> * <span data-ttu-id="ea30a-113">Wdrażanie i przewidywanie załadować modelu</span><span class="sxs-lookup"><span data-stu-id="ea30a-113">Deploy and Predict with a loaded model</span></span>

> [!NOTE]
> <span data-ttu-id="ea30a-114">W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="ea30a-114">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="ea30a-115">Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="ea30a-115">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

## <a name="github-issue-sample-overview"></a><span data-ttu-id="ea30a-116">Omówienie przykładowych problem usługi GitHub</span><span class="sxs-lookup"><span data-stu-id="ea30a-116">GitHub issue sample overview</span></span>

<span data-ttu-id="ea30a-117">Próbka jest aplikacją konsoli, która używa strukturze ML.NET do nauczenia modelu, która klasyfikuje i przewiduje etykieta obszar problemu w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="ea30a-117">The sample is a console app that uses ML.NET to train a model that classifies and predicts the Area label for a GitHub issue.</span></span> <span data-ttu-id="ea30a-118">Oblicza model z drugiego zestawu danych do analizy jakości dostawców.</span><span class="sxs-lookup"><span data-stu-id="ea30a-118">It also evaluates the model with a second dataset for quality analysis.</span></span> <span data-ttu-id="ea30a-119">Zestawy danych problem pochodzą z repozytorium GitHub dotnet/corefx.</span><span class="sxs-lookup"><span data-stu-id="ea30a-119">The issue datasets are from the dotnet/corefx GitHub repo.</span></span>

<span data-ttu-id="ea30a-120">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="ea30a-120">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ea30a-121">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="ea30a-121">Prerequisites</span></span>

* <span data-ttu-id="ea30a-122">[Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".</span><span class="sxs-lookup"><span data-stu-id="ea30a-122">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="ea30a-123">[Github generuje plik z wartościami oddzielonymi tabulatorami (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span><span class="sxs-lookup"><span data-stu-id="ea30a-123">The [Github issues tab separated file (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span></span>
* <span data-ttu-id="ea30a-124">[Problemy usługi Github test pliku z wartościami oddzielonymi tabulatorami (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span><span class="sxs-lookup"><span data-stu-id="ea30a-124">The [Github issues test tab separated file (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="ea30a-125">Maszyny uczenie się przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ea30a-125">Machine learning workflow</span></span>

<span data-ttu-id="ea30a-126">W tym samouczku poniżej przepływu pracy, który umożliwia proces przenoszenia w sposób uporządkowany uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="ea30a-126">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="ea30a-127">Fazy przepływu pracy są następujące:</span><span class="sxs-lookup"><span data-stu-id="ea30a-127">The workflow phases are as follows:</span></span>

1. <span data-ttu-id="ea30a-128">**Omówienie problemu**</span><span class="sxs-lookup"><span data-stu-id="ea30a-128">**Understand the problem**</span></span>
2. <span data-ttu-id="ea30a-129">**Przygotowywanie danych**</span><span class="sxs-lookup"><span data-stu-id="ea30a-129">**Prepare your data**</span></span>
   * <span data-ttu-id="ea30a-130">**Ładowanie danych**</span><span class="sxs-lookup"><span data-stu-id="ea30a-130">**Load the data**</span></span>
   * <span data-ttu-id="ea30a-131">**Wyodrębnianie funkcji (przekształcania danych)**</span><span class="sxs-lookup"><span data-stu-id="ea30a-131">**Extract features (Transform your data)**</span></span>
3. <span data-ttu-id="ea30a-132">**Kompilowanie i szkolenie**</span><span class="sxs-lookup"><span data-stu-id="ea30a-132">**Build and train**</span></span> 
   * <span data-ttu-id="ea30a-133">**Uczenie modelu**</span><span class="sxs-lookup"><span data-stu-id="ea30a-133">**Train the model**</span></span>
   * <span data-ttu-id="ea30a-134">**Ocena modelu**</span><span class="sxs-lookup"><span data-stu-id="ea30a-134">**Evaluate the model**</span></span>
4. <span data-ttu-id="ea30a-135">**Wdrażanie modelu**</span><span class="sxs-lookup"><span data-stu-id="ea30a-135">**Deploy Model**</span></span>
   * <span data-ttu-id="ea30a-136">**Użyj modelu do prognozowania**</span><span class="sxs-lookup"><span data-stu-id="ea30a-136">**Use the Model to predict**</span></span>

### <a name="understand-the-problem"></a><span data-ttu-id="ea30a-137">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="ea30a-137">Understand the problem</span></span>

<span data-ttu-id="ea30a-138">Należy najpierw zrozumieć, dzięki czemu można podzielić je w dół do części obsługujące kompilowanie i uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="ea30a-138">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="ea30a-139">Potężne problem umożliwia prognozowanie i ocena wyników.</span><span class="sxs-lookup"><span data-stu-id="ea30a-139">Breaking  down the problem allows you to predict and evaluate the results.</span></span>

<span data-ttu-id="ea30a-140">Ten problem, w tym samouczku jest zrozumienie przychodzące problemy usługi GitHub powierzchni należą do, aby można było oznaczyć je poprawnie priorytetyzacja i planowanie.</span><span class="sxs-lookup"><span data-stu-id="ea30a-140">The problem for this tutorial is to understand what area incoming GitHub issues belong to in order to label them correctly for prioritization and scheduling.</span></span>

<span data-ttu-id="ea30a-141">Ten problem można podzielić na następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="ea30a-141">You can break down the problem to the following parts:</span></span>

* <span data-ttu-id="ea30a-142">tekst tytułu problem</span><span class="sxs-lookup"><span data-stu-id="ea30a-142">the issue title text</span></span>
* <span data-ttu-id="ea30a-143">tekst opisu problemu</span><span class="sxs-lookup"><span data-stu-id="ea30a-143">the issue description text</span></span>
* <span data-ttu-id="ea30a-144">wartość obszaru danych szkoleniowych modelu</span><span class="sxs-lookup"><span data-stu-id="ea30a-144">an area value for the model training data</span></span>
* <span data-ttu-id="ea30a-145">wartość obszaru przewidywane, można obliczyć, a następnie za pomocą pod względem</span><span class="sxs-lookup"><span data-stu-id="ea30a-145">a predicted area value that you can evaluate and then use operationally</span></span>

<span data-ttu-id="ea30a-146">Następnie należy **określić** obszar, który ułatwia wybór zadań uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="ea30a-146">You then need to **determine** the area, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-algorithm"></a><span data-ttu-id="ea30a-147">Wybieranie algorytmu uczenia maszynowego odpowiednie</span><span class="sxs-lookup"><span data-stu-id="ea30a-147">Select the appropriate machine learning algorithm</span></span>

<span data-ttu-id="ea30a-148">W rozwiązaniu tego problemu znasz następujące fakty:</span><span class="sxs-lookup"><span data-stu-id="ea30a-148">With this problem, you know the following facts:</span></span>

<span data-ttu-id="ea30a-149">Dane szkoleniowe:</span><span class="sxs-lookup"><span data-stu-id="ea30a-149">Training data:</span></span>

<span data-ttu-id="ea30a-150">Problemy usługi GitHub może być oznaczony jako w kilku obszarach (**obszaru**) jak w następujących przykładach:</span><span class="sxs-lookup"><span data-stu-id="ea30a-150">GitHub issues can be labeled in several areas (**Area**) as in the following examples:</span></span>

* <span data-ttu-id="ea30a-151">area-System.Numerics</span><span class="sxs-lookup"><span data-stu-id="ea30a-151">area-System.Numerics</span></span>
* <span data-ttu-id="ea30a-152">area-System.Xml</span><span class="sxs-lookup"><span data-stu-id="ea30a-152">area-System.Xml</span></span>
* <span data-ttu-id="ea30a-153">obszar infrastruktura</span><span class="sxs-lookup"><span data-stu-id="ea30a-153">area-Infrastructure</span></span>
* <span data-ttu-id="ea30a-154">area-System.Linq</span><span class="sxs-lookup"><span data-stu-id="ea30a-154">area-System.Linq</span></span>
* <span data-ttu-id="ea30a-155">area-System.IO</span><span class="sxs-lookup"><span data-stu-id="ea30a-155">area-System.IO</span></span>

<span data-ttu-id="ea30a-156">Przewidywanie **obszaru** z nowego problemu w usłudze GitHub takich jak w następujących przykładach:</span><span class="sxs-lookup"><span data-stu-id="ea30a-156">Predict the **Area** of a new GitHub Issue such as in the following examples:</span></span>

* <span data-ttu-id="ea30a-157">Contract.Assert vs Debug.Assert</span><span class="sxs-lookup"><span data-stu-id="ea30a-157">Contract.Assert vs Debug.Assert</span></span>
* <span data-ttu-id="ea30a-158">Tworzenie pola tylko do odczytu w System.Xml</span><span class="sxs-lookup"><span data-stu-id="ea30a-158">Make fields readonly in System.Xml</span></span>

<span data-ttu-id="ea30a-159">Algorytmu uczenia maszynowego klasyfikacji najlepiej nadaje się dla tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="ea30a-159">The classification machine learning algorithm is best suited for this scenario.</span></span>

### <a name="about-the-classification-learning-algorithm"></a><span data-ttu-id="ea30a-160">Temat algorytmu uczenia klasyfikacji</span><span class="sxs-lookup"><span data-stu-id="ea30a-160">About the classification learning algorithm</span></span>

<span data-ttu-id="ea30a-161">Klasyfikacja jest algorytm uczenia maszynowego, która korzysta z danych do **określić** kategorii, typ lub klasa elementu lub wiersza danych.</span><span class="sxs-lookup"><span data-stu-id="ea30a-161">Classification is a machine learning algorithm that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="ea30a-162">Na przykład można użyć klasyfikacji:</span><span class="sxs-lookup"><span data-stu-id="ea30a-162">For example, you can use classification to:</span></span>

* <span data-ttu-id="ea30a-163">Zidentyfikuj tonacji jako dodatnia lub ujemna.</span><span class="sxs-lookup"><span data-stu-id="ea30a-163">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="ea30a-164">Klasyfikowanie wiadomości e-mail jako spam, wiadomości-śmieci lub właściwej.</span><span class="sxs-lookup"><span data-stu-id="ea30a-164">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="ea30a-165">Ustal, czy pacjent laboratorium przykładowe dane stanowią cancerous.</span><span class="sxs-lookup"><span data-stu-id="ea30a-165">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="ea30a-166">Klienci na kategorie według ich tendencje do odpowiedzi na kampanię sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="ea30a-166">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="ea30a-167">Klasyfikacja, Użyj algorytmu uczenia przypadki są często jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="ea30a-167">Classification learning algorithm use cases are frequently one of the following types:</span></span>

* <span data-ttu-id="ea30a-168">Plik binarny: A i B.</span><span class="sxs-lookup"><span data-stu-id="ea30a-168">Binary: either A or B.</span></span>
* <span data-ttu-id="ea30a-169">Kontra: wielu kategorii, które można przewidzieć przy użyciu pojedynczego modelu.</span><span class="sxs-lookup"><span data-stu-id="ea30a-169">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="ea30a-170">Tego rodzaju problem korzystanie z klasyfikacji kontra, uczenie algorytmu, ponieważ do prognozowania kategorii problemu może być jednym z wielu kategorii (kontra), a nie tylko dwóch (binarnych).</span><span class="sxs-lookup"><span data-stu-id="ea30a-170">For this type of problem, use a Multiclass classification learning algorithm, since your issue category prediction can be one of multiple categories (multiclass) rather than just two (binary).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="ea30a-171">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="ea30a-171">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="ea30a-172">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="ea30a-172">Create a project</span></span>

1. <span data-ttu-id="ea30a-173">Otwórz program Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="ea30a-173">Open Visual Studio 2017.</span></span> <span data-ttu-id="ea30a-174">Wybierz **pliku** > **New** > **projektu** z paska menu.</span><span class="sxs-lookup"><span data-stu-id="ea30a-174">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="ea30a-175">W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła następuje **platformy .NET Core** węzła.</span><span class="sxs-lookup"><span data-stu-id="ea30a-175">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="ea30a-176">Następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="ea30a-176">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="ea30a-177">W **nazwa** pole tekstowe, wpisz "SentimentAnalysis", a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="ea30a-177">In the **Name** text box, type "SentimentAnalysis" and then select the **OK** button.</span></span>

2. <span data-ttu-id="ea30a-178">Utwórz katalog o nazwie *danych* w projekcie, aby zapisać pliki zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="ea30a-178">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="ea30a-179">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nad projektem i wybierz **Dodaj** > **nowy Folder**.</span><span class="sxs-lookup"><span data-stu-id="ea30a-179">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="ea30a-180">Wpisz "Dane", a następnie naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="ea30a-180">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="ea30a-181">Utwórz katalog o nazwie *modeli* w projekcie, aby zapisać modelu:</span><span class="sxs-lookup"><span data-stu-id="ea30a-181">Create a directory named *Models* in your project to save your model:</span></span>

    <span data-ttu-id="ea30a-182">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nad projektem i wybierz **Dodaj** > **nowy Folder**.</span><span class="sxs-lookup"><span data-stu-id="ea30a-182">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="ea30a-183">Wpisz "Modele", a następnie naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="ea30a-183">Type "Models" and hit Enter.</span></span>

4. <span data-ttu-id="ea30a-184">Zainstaluj **pakietu NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="ea30a-184">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="ea30a-185">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="ea30a-185">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="ea30a-186">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="ea30a-186">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="ea30a-187">Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.</span><span class="sxs-lookup"><span data-stu-id="ea30a-187">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="ea30a-188">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="ea30a-188">Prepare your data</span></span>

1. <span data-ttu-id="ea30a-189">Pobierz [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) i [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) danych ustawia i zapisywanie ich *danych* wcześniej utworzony folder.</span><span class="sxs-lookup"><span data-stu-id="ea30a-189">Download the [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) and the [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="ea30a-190">Szkolenie modeli modelu uczenia maszynowego na pierwszego zestawu danych, a drugi może służyć do oceny, jak dokładna jest model.</span><span class="sxs-lookup"><span data-stu-id="ea30a-190">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="ea30a-191">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy każdy z \*pliki tsv i wybierz pozycję **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="ea30a-191">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="ea30a-192">W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="ea30a-192">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="ea30a-193">Tworzenie klas i definiowania ścieżek</span><span class="sxs-lookup"><span data-stu-id="ea30a-193">Create classes and define paths</span></span>

<span data-ttu-id="ea30a-194">Dodaj następujące dodatkowe `using` instrukcji na górze *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="ea30a-194">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

<span data-ttu-id="ea30a-195">Utwórz trzy pola globalnego na potrzeby przechowywania ścieżek do ostatnio pobrane pliki i zmiennych globalnych `MLContext`,`DataView`, `PredictionEngine`, i `TextLoader`:</span><span class="sxs-lookup"><span data-stu-id="ea30a-195">Create three global fields to hold the paths to the recently downloaded files, and global variables for the `MLContext`,`DataView`, `PredictionEngine`, and `TextLoader`:</span></span>

* <span data-ttu-id="ea30a-196">`_trainDataPath` zawiera ścieżkę do zestawu danych, używane do trenowania modelu.</span><span class="sxs-lookup"><span data-stu-id="ea30a-196">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="ea30a-197">`_testDataPath` zawiera ścieżkę do zestawu danych, używane do oceny modelu.</span><span class="sxs-lookup"><span data-stu-id="ea30a-197">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="ea30a-198">`_modelPath` ma ścieżkę, w którym jest zapisany trenowanego modelu.</span><span class="sxs-lookup"><span data-stu-id="ea30a-198">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="ea30a-199">`_mlContext` jest <xref:Microsoft.ML.MLContext> zapewniający przetwarzania kontekstu.</span><span class="sxs-lookup"><span data-stu-id="ea30a-199">`_mlContext` is the <xref:Microsoft.ML.MLContext> that provides processing context.</span></span>
* <span data-ttu-id="ea30a-200">`_trainingDataView` jest <xref:Microsoft.Data.DataView.IDataView> używani do przetwarzania zestaw danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="ea30a-200">`_trainingDataView` is the <xref:Microsoft.Data.DataView.IDataView> used to process the training dataset.</span></span>
* <span data-ttu-id="ea30a-201">`_predEngine` jest <xref:Microsoft.ML.PredictionEngine%602> używany dla pojedynczego prognozy.</span><span class="sxs-lookup"><span data-stu-id="ea30a-201">`_predEngine` is the <xref:Microsoft.ML.PredictionEngine%602> used for single predictions.</span></span>
* <span data-ttu-id="ea30a-202">`_reader` jest <xref:Microsoft.ML.Data.TextLoader> używany do ładowania i przekształcić zestawy danych.</span><span class="sxs-lookup"><span data-stu-id="ea30a-202">`_reader` is the <xref:Microsoft.ML.Data.TextLoader> used to load and transform the datasets.</span></span>

<span data-ttu-id="ea30a-203">Dodaj następujący kod po prawej stronie wiersza powyżej `Main` metodę, aby określić ścieżki te i inne zmienne:</span><span class="sxs-lookup"><span data-stu-id="ea30a-203">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="ea30a-204">Utwórz niektóre klasy dla danych wejściowych i prognozy.</span><span class="sxs-lookup"><span data-stu-id="ea30a-204">Create some classes for your input data and predictions.</span></span> <span data-ttu-id="ea30a-205">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="ea30a-205">Add a new class to your project:</span></span>

1. <span data-ttu-id="ea30a-206">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="ea30a-206">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="ea30a-207">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *GitHubIssueData.cs*.</span><span class="sxs-lookup"><span data-stu-id="ea30a-207">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *GitHubIssueData.cs*.</span></span> <span data-ttu-id="ea30a-208">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="ea30a-208">Then, select the **Add** button.</span></span>

    <span data-ttu-id="ea30a-209">*GitHubIssueData.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="ea30a-209">The *GitHubIssueData.cs* file opens in the code editor.</span></span> <span data-ttu-id="ea30a-210">Dodaj następujący kod `using` instrukcji na górze *GitHubIssueData.cs*:</span><span class="sxs-lookup"><span data-stu-id="ea30a-210">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

<span data-ttu-id="ea30a-211">Usuń istniejącą definicję klasy i Dodaj następujący kod, który zawiera dwie klasy `GitHubIssue` i `IssuePrediction`, *GitHubIssueData.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="ea30a-211">Remove the existing class definition and add the following code, which has two classes `GitHubIssue` and `IssuePrediction`, to the *GitHubIssueData.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

<span data-ttu-id="ea30a-212">`GitHubIssue` jest to klasa wejściowy zestaw danych i ma następujące <xref:System.String> pola:</span><span class="sxs-lookup"><span data-stu-id="ea30a-212">`GitHubIssue` is the input dataset class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="ea30a-213">`ID` zawiera wartość dla Identyfikatora problemu usługi GitHub</span><span class="sxs-lookup"><span data-stu-id="ea30a-213">`ID` contains a value for the GitHub issue ID</span></span>
* <span data-ttu-id="ea30a-214">`Area` zawiera wartość dla `Area` etykiety</span><span class="sxs-lookup"><span data-stu-id="ea30a-214">`Area` contains a value for the `Area` label</span></span>
* <span data-ttu-id="ea30a-215">`Title` zawiera tytuł problemu usługi GitHub</span><span class="sxs-lookup"><span data-stu-id="ea30a-215">`Title` contains the GitHub issue title</span></span>
* <span data-ttu-id="ea30a-216">`Description` Zawiera opis problemu usługi GitHub</span><span class="sxs-lookup"><span data-stu-id="ea30a-216">`Description` contains the GitHub issue description</span></span>

<span data-ttu-id="ea30a-217">`IssuePrediction` Klasa służy do prognozowania po wyszkoliła modelu.</span><span class="sxs-lookup"><span data-stu-id="ea30a-217">`IssuePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="ea30a-218">Ma on jeden `string` (`Area`) i `PredictedLabel` `ColumnName` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ea30a-218">It has a single `string` (`Area`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="ea30a-219">`Label` Umożliwia tworzenie i uczenie modelu, a także drugiego zestawu danych do ewaluacji modelu.</span><span class="sxs-lookup"><span data-stu-id="ea30a-219">The `Label` is used to create and train the model, and it's also used with a second dataset to evaluate the model.</span></span> <span data-ttu-id="ea30a-220">`PredictedLabel` Używany podczas prognoz i oceny.</span><span class="sxs-lookup"><span data-stu-id="ea30a-220">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="ea30a-221">W wersji ewaluacyjnej używane są dane szkoleniowe, przewidywane wartości i model danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="ea30a-221">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="ea30a-222">Podczas tworzenia modelu za pomocą platformy ML.NET, rozpoczyna się od utworzenia <xref:Microsoft.ML.MLContext>.</span><span class="sxs-lookup"><span data-stu-id="ea30a-222">When building a model with ML.NET, you start by creating an <xref:Microsoft.ML.MLContext>.</span></span> <span data-ttu-id="ea30a-223">`MLContext` można porównywać pod względem koncepcyjnym do korzystania z `DbContext` platformy Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="ea30a-223">`MLContext` is comparable conceptually to using `DbContext` in Entity Framework.</span></span> <span data-ttu-id="ea30a-224">Środowisko dostarcza kontekst dla zadania uczenia Maszynowego, który może służyć do wyjątku, śledzenie i rejestrowanie.</span><span class="sxs-lookup"><span data-stu-id="ea30a-224">The environment provides a context for your ML job that can be used for exception tracking and logging.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="ea30a-225">Inicjowanie zmiennych w głównym oknie</span><span class="sxs-lookup"><span data-stu-id="ea30a-225">Initialize variables in Main</span></span>

<span data-ttu-id="ea30a-226">Inicjowanie `_mlContext` zmienna globalna o nowe wystąpienie klasy `MLContext` z Inicjator losowy (`seed: 0`) dla powtarzalnych/deterministyczne wyników w szkoleniach wielu.</span><span class="sxs-lookup"><span data-stu-id="ea30a-226">Initialize the `_mlContext` global variable  with a new instance of `MLContext` with a random seed (`seed: 0`) for repeatable/deterministic results across multiple trainings.</span></span>  <span data-ttu-id="ea30a-227">Zastąp `Console.WriteLine("Hello World!")` wiersz poniższym kodem w `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="ea30a-227">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a><span data-ttu-id="ea30a-228">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="ea30a-228">Load the data</span></span>

<span data-ttu-id="ea30a-229">Następnie zainicjuj `_trainingDataView` <xref:Microsoft.Data.DataView.IDataView> zmiennej globalnej i ładowanie danych za pomocą `_trainDataPath` parametru.</span><span class="sxs-lookup"><span data-stu-id="ea30a-229">Next, initialize the `_trainingDataView` <xref:Microsoft.Data.DataView.IDataView> global variable and load the data with the `_trainDataPath` parameter.</span></span>

 <span data-ttu-id="ea30a-230">Jako dane wejściowe i wyjściowe [ `Transforms` ](../basic-concepts-model-training-in-mldotnet.md#transformer), `DataView` jest typem potoku danych podstawowych porównywalne do `IEnumerable` dla `LINQ`.</span><span class="sxs-lookup"><span data-stu-id="ea30a-230">As the input and output of [`Transforms`](../basic-concepts-model-training-in-mldotnet.md#transformer), a `DataView` is the fundamental data pipeline type, comparable to `IEnumerable` for `LINQ`.</span></span>

<span data-ttu-id="ea30a-231">W strukturze ML.NET, dane są podobne do `SQL view`.</span><span class="sxs-lookup"><span data-stu-id="ea30a-231">In ML.NET, data is similar to a `SQL view`.</span></span> <span data-ttu-id="ea30a-232">Jest opóźnieniem ocenianą informatycznych i heterogenicznych.</span><span class="sxs-lookup"><span data-stu-id="ea30a-232">It is lazily evaluated, schematized, and heterogenous.</span></span> <span data-ttu-id="ea30a-233">Obiekt jest pierwszą częścią potoku i służy do ładowania danych.</span><span class="sxs-lookup"><span data-stu-id="ea30a-233">The object is the first part of the pipeline, and loads the data.</span></span> <span data-ttu-id="ea30a-234">W tym samouczku ładuje zestaw danych o problem tytułów, opisów i odpowiednie etykiety GitHub powierzchni.</span><span class="sxs-lookup"><span data-stu-id="ea30a-234">For this tutorial, it loads a dataset with issue titles, descriptions, and corresponding area GitHub label.</span></span> <span data-ttu-id="ea30a-235">`DataView` Umożliwia tworzenie i trenowanie modelu.</span><span class="sxs-lookup"><span data-stu-id="ea30a-235">The `DataView` is used to create and train the model.</span></span>

<span data-ttu-id="ea30a-236">Ponieważ utworzone wcześniej `GitHubIssue` typ modelu danych jest zgodny schemat zestawu danych, można połączyć inicjowania, mapowanie i zestaw danych ładowania do jednego wiersza kodu.</span><span class="sxs-lookup"><span data-stu-id="ea30a-236">Since your previously created `GitHubIssue` data model type matches the dataset schema, you can combine the initialization, mapping, and dataset loading into one line of code.</span></span>

<span data-ttu-id="ea30a-237">Pierwsza część wiersza (`CreateTextLoader<GitHubIssue>(hasHeader: true)`) tworzy <xref:Microsoft.ML.Data.TextLoader> przez wnioskowanie schematu zestawu danych z `GitHubIssue` modelu danych, typ i przy użyciu nagłówka zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="ea30a-237">The first part of the line (`CreateTextLoader<GitHubIssue>(hasHeader: true)`) creates a <xref:Microsoft.ML.Data.TextLoader> by inferring the dataset schema from the `GitHubIssue` data model type and using the dataset header.</span></span>

<span data-ttu-id="ea30a-238">Wcześniej zdefiniowany schemat danych podczas tworzenia `GitHubIssue` klasy.</span><span class="sxs-lookup"><span data-stu-id="ea30a-238">You defined the data schema previously when you created the `GitHubIssue` class.</span></span> <span data-ttu-id="ea30a-239">Dla schematu:</span><span class="sxs-lookup"><span data-stu-id="ea30a-239">For your schema:</span></span>

* <span data-ttu-id="ea30a-240">Pierwsza kolumna `ID` (identyfikator problemu usługi GitHub)</span><span class="sxs-lookup"><span data-stu-id="ea30a-240">the first column `ID` (GitHub Issue ID)</span></span>
* <span data-ttu-id="ea30a-241">druga kolumna `Area` (prognozowane potrzeby szkolenia)</span><span class="sxs-lookup"><span data-stu-id="ea30a-241">the second column `Area` (the prediction for training)</span></span>
* <span data-ttu-id="ea30a-242">trzecia kolumna `Title` (tytuł problemu usługi GitHub) jest to pierwszy [funkcji](../resources/glossary.md##feature) używane do prognozowania `Area`</span><span class="sxs-lookup"><span data-stu-id="ea30a-242">the third column `Title` (GitHub issue title) is the first [feature](../resources/glossary.md##feature)  used for predicting the `Area`</span></span>
* <span data-ttu-id="ea30a-243">Czwarta kolumna `Description` jest druga funkcja używana do prognozowania `Area`</span><span class="sxs-lookup"><span data-stu-id="ea30a-243">the fourth column  `Description` is the second feature used for predicting the `Area`</span></span>

<span data-ttu-id="ea30a-244">Druga część wiersza (`.Read(_trainDataPath)`) używa <xref:Microsoft.ML.Data.TextLoader.Read%2A> metodę, aby załadować tekstu szkolenia plików przy użyciu `_trainDataPath` do `IDataView` (`_trainingDataView`) zmiennej globalnej.</span><span class="sxs-lookup"><span data-stu-id="ea30a-244">The second part of the line  (`.Read(_trainDataPath)`) uses <xref:Microsoft.ML.Data.TextLoader.Read%2A> method to load the training text file using `_trainDataPath` into the `IDataView` (`_trainingDataView`) global variable.</span></span>  

<span data-ttu-id="ea30a-245">Aby zainicjować i załadować `_trainingDataView` zmienna globalna, aby mógł zostać użyty dla potoku, Dodaj następujący kod po `mlContext` inicjowania:</span><span class="sxs-lookup"><span data-stu-id="ea30a-245">To initialize and load the `_trainingDataView` global variable in order to use it for the pipeline, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]


<span data-ttu-id="ea30a-246">Dodaj następujący kod jako następnego wiersza kodu w `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="ea30a-246">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallProcessData](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

<span data-ttu-id="ea30a-247">`ProcessData` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="ea30a-247">The `ProcessData` method executes the following tasks:</span></span>

* <span data-ttu-id="ea30a-248">Wyodrębnia i przekształca dane.</span><span class="sxs-lookup"><span data-stu-id="ea30a-248">Extracts and transforms the data.</span></span>
* <span data-ttu-id="ea30a-249">Zwraca potoku przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="ea30a-249">Returns the processing pipeline.</span></span>

<span data-ttu-id="ea30a-250">Tworzenie `ProcessData` metody tuż za `Main` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ea30a-250">Create the `ProcessData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static EstimatorChain<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="ea30a-251">Wyodrębnianie funkcji i przekształcania danych</span><span class="sxs-lookup"><span data-stu-id="ea30a-251">Extract Features and transform the data</span></span>

<span data-ttu-id="ea30a-252">Wstępne przetwarzanie i czyszczenie danych są ważne zadania, które występują przed zestaw danych jest efektywnie używać uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="ea30a-252">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="ea30a-253">Nieprzetworzone dane są często hałas i zawodnych i może brakować wartości.</span><span class="sxs-lookup"><span data-stu-id="ea30a-253">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="ea30a-254">Korzystanie z danych bez tych zadań modelowania może spowodować wyświetlenie nieprawdziwych wyników.</span><span class="sxs-lookup"><span data-stu-id="ea30a-254">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="ea30a-255">UCZENIE MASZYNOWE. Potoki przekształcenie firmy NET tworzą niestandardową `transforms`zestaw, który jest stosowany do dane przed szkolenie i testowanie.</span><span class="sxs-lookup"><span data-stu-id="ea30a-255">ML.NET's transform pipelines compose a custom `transforms`set that is applied to your data before training or testing.</span></span> <span data-ttu-id="ea30a-256">Przekształcenia głównym celem jest danych [cechowania](../resources/glossary.md#feature-engineering).</span><span class="sxs-lookup"><span data-stu-id="ea30a-256">The transforms' primary purpose is data [featurization](../resources/glossary.md#feature-engineering).</span></span> <span data-ttu-id="ea30a-257">Omówienie algorytmów uczenia maszynowego [neural](../resources/glossary.md#feature) dane, dzięki czemu następnym krokiem jest do przekształcania danych tekstowych do formatu, który rozpoznaje nasze algorytmy uczenia Maszynowego.</span><span class="sxs-lookup"><span data-stu-id="ea30a-257">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, so the next step is to transform our textual data into a format that our ML algorithms recognize.</span></span> <span data-ttu-id="ea30a-258">Ten format jest [liczbowych wektor](../resources/glossary.md#numerical-feature-vector).</span><span class="sxs-lookup"><span data-stu-id="ea30a-258">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="ea30a-259">W następnych krokach nazywamy kolumny według nazw zdefiniowana w `GitHubIssue` klasy.</span><span class="sxs-lookup"><span data-stu-id="ea30a-259">In the next steps, we refer to the columns by the names defined in the `GitHubIssue` class.</span></span>

<span data-ttu-id="ea30a-260">Gdy wiedzę i oceniane, domyślne wartości w modelu **etykiety** kolumny będą traktowane jako prawidłowe wartości do można przewidzieć.</span><span class="sxs-lookup"><span data-stu-id="ea30a-260">When the model is trained and evaluated, by default, the values in the **Label** column are considered as correct values to be predicted.</span></span> <span data-ttu-id="ea30a-261">Ponieważ chcemy przewidzieć etykieta GitHub powierzchni `GitHubIssue`, kopia `Area` kolumny na **etykiety** kolumny.</span><span class="sxs-lookup"><span data-stu-id="ea30a-261">As we want to predict the Area GitHub label for a `GitHubIssue`, copy the `Area` column into the **Label** column.</span></span> <span data-ttu-id="ea30a-262">Aby to zrobić, należy użyć `MLContext.Transforms.Conversion.MapValueToKey`, który jest otoką <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A> klasy przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="ea30a-262">To do that, use the `MLContext.Transforms.Conversion.MapValueToKey`, which is a wrapper for the <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A> transformation class.</span></span>  <span data-ttu-id="ea30a-263">`MapValueToKey` Zwraca <xref:Microsoft.ML.Data.EstimatorChain%601> skutecznie się potoku.</span><span class="sxs-lookup"><span data-stu-id="ea30a-263">The `MapValueToKey` returns an <xref:Microsoft.ML.Data.EstimatorChain%601> that will effectively be a pipeline.</span></span> <span data-ttu-id="ea30a-264">Nazwij to `pipeline` jako następnie dołączy trainer do `EstimatorChain`.</span><span class="sxs-lookup"><span data-stu-id="ea30a-264">Name this `pipeline` as you will then append the trainer to the `EstimatorChain`.</span></span> <span data-ttu-id="ea30a-265">Dodaj kolejny wiersz kodu:</span><span class="sxs-lookup"><span data-stu-id="ea30a-265">Add the next line of code:</span></span>

[!code-csharp[MapValueToKey](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

 <span data-ttu-id="ea30a-266">Featurizing różnych wartości kluczowych numeryczne są przypisane różne wartości w każdej z kolumn i jest używany przez algorytmu uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="ea30a-266">Featurizing assigns different numeric key values to the different values in each of the columns and is used by the machine learning algorithm.</span></span> <span data-ttu-id="ea30a-267">Następnie wywołaj `mlContext.Transforms.Text.FeaturizeText` które featurizes tekst (`Title` i `Description`) kolumny liczbowe wektor dla każdego o nazwie `TitleFeaturized` i `DescriptionFeaturized`.</span><span class="sxs-lookup"><span data-stu-id="ea30a-267">Next, call `mlContext.Transforms.Text.FeaturizeText` which featurizes the text (`Title` and `Description`) columns into a numeric vector for each called `TitleFeaturized` and `DescriptionFeaturized`.</span></span> <span data-ttu-id="ea30a-268">Dołącz cechowania dla obu kolumn do potoku z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="ea30a-268">Append the featurization for both columns to the pipeline with the following code:</span></span>

[!code-csharp[FeaturizeText](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

>[!WARNING]
> <span data-ttu-id="ea30a-269">Wersja strukturze ML.NET 0.10 została zmieniona kolejność parametrów transformacji.</span><span class="sxs-lookup"><span data-stu-id="ea30a-269">ML.NET Version 0.10 has changed the order of the Transform parameters.</span></span> <span data-ttu-id="ea30a-270">To spowoduje nie Błąd limitu do czasu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ea30a-270">This will not error out until you build.</span></span> <span data-ttu-id="ea30a-271">Użyj nazwy parametrów transformacji, jak pokazano w poprzednim fragmencie kodu.</span><span class="sxs-lookup"><span data-stu-id="ea30a-271">Use the parameter names for Transforms as illustrated in the previous code snippet.</span></span>

<span data-ttu-id="ea30a-272">Ostatnim krokiem w przygotowaniu danych łączy wszystkie kolumny funkcji do **funkcji** przy użyciu kolumny `Concatenate` klasy przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="ea30a-272">The last step in data preparation combines all of the feature columns into the **Features** column using the `Concatenate` transformation class.</span></span> <span data-ttu-id="ea30a-273">Domyślnie algorytmu uczenia przetwarza tylko funkcje z **funkcji** kolumny.</span><span class="sxs-lookup"><span data-stu-id="ea30a-273">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="ea30a-274">Dołącz to przekształcenie do potoku z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="ea30a-274">Append this transformation to the pipeline with the following code:</span></span>

[!code-csharp[Concatenate](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 <span data-ttu-id="ea30a-275">Następnie dołącz <xref:Microsoft.ML.Data.EstimatorChain`1.AppendCacheCheckpoint%2A> w pamięci podręcznej widoku danych, dzięki czemu podczas iteracji przez dane wielokrotnie przy użyciu pamięci podręcznej mogą uzyskać lepszą wydajność, zgodnie z poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="ea30a-275">Next, append a <xref:Microsoft.ML.Data.EstimatorChain`1.AppendCacheCheckpoint%2A> to cache the DataView so when you iterate over the data multiple times using the cache might get better performance, as with the following code:</span></span>

[!code-csharp[AppendCache](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

<span data-ttu-id="ea30a-276">Zwróć potoku na końcu `ProcessData` metody.</span><span class="sxs-lookup"><span data-stu-id="ea30a-276">Return the pipeline at the end of the `ProcessData` method.</span></span>

[!code-csharp[ReturnPipeline](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

<span data-ttu-id="ea30a-277">W tym kroku obsługuje przetwarzania wstępnego cechowania.</span><span class="sxs-lookup"><span data-stu-id="ea30a-277">This step handles preprocessing/featurization.</span></span> <span data-ttu-id="ea30a-278">Za pomocą dodatkowych składników dostępnych w strukturze ML.NET umożliwiają lepsze wyniki za pomocą modelu.</span><span class="sxs-lookup"><span data-stu-id="ea30a-278">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="build-and-train-the-model"></a><span data-ttu-id="ea30a-279">Tworzenie i trenowanie modelu</span><span class="sxs-lookup"><span data-stu-id="ea30a-279">Build and train the model</span></span>

<span data-ttu-id="ea30a-280">Dodaj następujące wywołanie do `BuildAndTrainModel`metodę jako następnego wiersza kodu w `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="ea30a-280">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="ea30a-281">`BuildAndTrainModel` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="ea30a-281">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="ea30a-282">Tworzy klasę algorytm szkolenia.</span><span class="sxs-lookup"><span data-stu-id="ea30a-282">Creates the training algorithm class.</span></span>
* <span data-ttu-id="ea30a-283">Szkolenie modeli modelu.</span><span class="sxs-lookup"><span data-stu-id="ea30a-283">Trains the model.</span></span>
* <span data-ttu-id="ea30a-284">Prognozuje obszaru, w oparciu o dane szkoleniowe.</span><span class="sxs-lookup"><span data-stu-id="ea30a-284">Predicts area based on training data.</span></span>
* <span data-ttu-id="ea30a-285">Zapisuje modelu, który ma `.zip` pliku.</span><span class="sxs-lookup"><span data-stu-id="ea30a-285">Saves the model to a `.zip` file.</span></span>
* <span data-ttu-id="ea30a-286">Zwraca wartość modelu.</span><span class="sxs-lookup"><span data-stu-id="ea30a-286">Returns the model.</span></span>

<span data-ttu-id="ea30a-287">Tworzenie `BuildAndTrainModel` metody tuż za `Main` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ea30a-287">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static EstimatorChain<KeyToValueMappingTransformer> BuildAndTrainModel(IDataView trainingDataView, EstimatorChain<ITransformer> pipeline)
{

}
```

<span data-ttu-id="ea30a-288">Należy zauważyć, że dwa parametry są przekazywane do metody BuildAndTrainModel; `IDataView` dla zestawu danych szkoleniowych (`trainingDataView`), a <xref:Microsoft.ML.Data.EstimatorChain%601> dla potoku przetwarzania utworzonych w ProcessData (`pipeline`).</span><span class="sxs-lookup"><span data-stu-id="ea30a-288">Notice that two parameters are passed into the BuildAndTrainModel method; an `IDataView` for the training dataset (`trainingDataView`), and a <xref:Microsoft.ML.Data.EstimatorChain%601> for the processing pipeline created in ProcessData (`pipeline`).</span></span>

 <span data-ttu-id="ea30a-289">Dodaj następujący kod jako pierwsza linia `BuildAndTrainModel` metody:</span><span class="sxs-lookup"><span data-stu-id="ea30a-289">Add the following code as the first line of the `BuildAndTrainModel` method:</span></span>

### <a name="choose-a-learning-algorithm"></a><span data-ttu-id="ea30a-290">Wybieranie algorytmu uczenia</span><span class="sxs-lookup"><span data-stu-id="ea30a-290">Choose a learning algorithm</span></span>

<span data-ttu-id="ea30a-291">Aby dodać Algorytm uczenia, należy wywołać `mlContext.MulticlassClassification.Trainers.StochasticDualCoordinateAscent` metody otoki, która zwraca <xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer> obiektu.</span><span class="sxs-lookup"><span data-stu-id="ea30a-291">To add the learning algorithm, call the `mlContext.MulticlassClassification.Trainers.StochasticDualCoordinateAscent` wrapper method which returns a <xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer> object.</span></span>  <span data-ttu-id="ea30a-292">`SdcaMultiClassTrainer` Jest dołączany do `pipeline` i akceptuje neural `Title` i `Description` (`Features`) i `Label` parametrów, aby dowiedzieć się więcej na podstawie historycznych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="ea30a-292">The `SdcaMultiClassTrainer` is appended to the `pipeline` and accepts the featurized `Title` and `Description` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span> <span data-ttu-id="ea30a-293">Należy również mapować etykiety na wartość, aby powrócić do stanu pierwotnego do odczytu.</span><span class="sxs-lookup"><span data-stu-id="ea30a-293">You also need to map the label to the value to return to its original readable state.</span></span> <span data-ttu-id="ea30a-294">Czy obu tych akcji, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ea30a-294">Do both of those actions with the following code:</span></span>

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

### <a name="train-the-model"></a><span data-ttu-id="ea30a-295">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="ea30a-295">Train the model</span></span>

<span data-ttu-id="ea30a-296">Uczenie modelu, <xref:Microsoft.ML.Data.TransformerChain%601>zgodnie z zestawu danych, który został załadowany i przekształcone.</span><span class="sxs-lookup"><span data-stu-id="ea30a-296">You train the model, <xref:Microsoft.ML.Data.TransformerChain%601>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="ea30a-297">Po zdefiniowaniu estymatora uczenie modelu przy użyciu <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> przy jednoczesnym zapewnieniu dane szkoleniowe już załadowana.</span><span class="sxs-lookup"><span data-stu-id="ea30a-297">Once the estimator has been defined, you train your model using the <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> while providing the already loaded training data.</span></span> <span data-ttu-id="ea30a-298">Ta metoda zwraca modelu na potrzeby prognozy.</span><span class="sxs-lookup"><span data-stu-id="ea30a-298">This  method returns a model to use for predictions.</span></span> <span data-ttu-id="ea30a-299">`trainingPipeline.Fit()` szkolenie modeli potoku i zwraca `Transformer` na podstawie `DataView` przekazany.</span><span class="sxs-lookup"><span data-stu-id="ea30a-299">`trainingPipeline.Fit()` trains the pipeline and returns a `Transformer` based on the `DataView` passed in.</span></span> <span data-ttu-id="ea30a-300">Eksperyment nie jest wykonywane, dopóki `.Fit()` metoda przebiegów.</span><span class="sxs-lookup"><span data-stu-id="ea30a-300">The experiment is not executed until the `.Fit()` method runs.</span></span>

<span data-ttu-id="ea30a-301">Dodaj następujący kod do `BuildAndTrainModel` metody:</span><span class="sxs-lookup"><span data-stu-id="ea30a-301">Add the following code to the `BuildAndTrainModel` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

<span data-ttu-id="ea30a-302">Gdy `model` jest `transformer` który operuje na wiele wierszy danych, na potrzeby prognoz na poszczególne przykłady to typowy scenariusz w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="ea30a-302">While the `model` is a `transformer` that operates on many rows of data, a need for predictions on individual examples is a common production scenario.</span></span> <span data-ttu-id="ea30a-303"><xref:Microsoft.ML.PredictionEngine%602> Jest otoką, który jest zwracany z `CreatePredictionEngine` metody.</span><span class="sxs-lookup"><span data-stu-id="ea30a-303">The <xref:Microsoft.ML.PredictionEngine%602> is a wrapper that is returned from the `CreatePredictionEngine` method.</span></span> <span data-ttu-id="ea30a-304">Możemy dodać następujący kod, aby utworzyć `PredictionEngine` w następnym wierszu `BuildAndTrainModel` metody:</span><span class="sxs-lookup"><span data-stu-id="ea30a-304">Let's add the following code to create the `PredictionEngine` as the next line in the `BuildAndTrainModel` Method:</span></span>

[!code-csharp[CreatePredictionEngine1](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a><span data-ttu-id="ea30a-305">Prognozowanie za pomocą uczonego modelu</span><span class="sxs-lookup"><span data-stu-id="ea30a-305">Predict with the trained model</span></span>

<span data-ttu-id="ea30a-306">Dodaj problem w usłudze GitHub do testowania uczonego modelu prognozowania w `Predict` metody przez utworzenie wystąpienia `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="ea30a-306">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[CreateTestIssue1](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

<span data-ttu-id="ea30a-307">Można go używać, aby przewidzieć `Area` etykiety pojedyncze wystąpienie danych problem.</span><span class="sxs-lookup"><span data-stu-id="ea30a-307">You can use that to predict the `Area` label of a single instance of the issue data.</span></span> <span data-ttu-id="ea30a-308">Aby uzyskać prognozę, użyj <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> na danych.</span><span class="sxs-lookup"><span data-stu-id="ea30a-308">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="ea30a-309">Dane wejściowe to ciąg, a model zawiera cechowania.</span><span class="sxs-lookup"><span data-stu-id="ea30a-309">The input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="ea30a-310">Potok jest zsynchronizowany podczas uczenia i przewidywania.</span><span class="sxs-lookup"><span data-stu-id="ea30a-310">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="ea30a-311">Nie trzeba napisać kod przetwarzania wstępnego cechowania specjalnie dla prognoz i zajmuje się tego samego interfejsu API i usługi batch jednorazowe prognozy.</span><span class="sxs-lookup"><span data-stu-id="ea30a-311">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a><span data-ttu-id="ea30a-312">Przy użyciu modelu: przewidywanie wyników</span><span class="sxs-lookup"><span data-stu-id="ea30a-312">Using the model: prediction results</span></span>

<span data-ttu-id="ea30a-313">Wyświetlanie `GitHubIssue` i odpowiadających im `Area` etykiety prognozowania, aby można było udostępnić wyniki i podejmowanie odpowiednich działań na nich.</span><span class="sxs-lookup"><span data-stu-id="ea30a-313">Display `GitHubIssue` and corresponding `Area` label prediction in order to share the results and act on them accordingly.</span></span>  <span data-ttu-id="ea30a-314">Tworzenie ekranu wyników za pomocą następujących <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:</span><span class="sxs-lookup"><span data-stu-id="ea30a-314">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="ea30a-315">Zwraca czy model jest uczony na potrzeby oceny</span><span class="sxs-lookup"><span data-stu-id="ea30a-315">Return the model trained to use for evaluation</span></span>

<span data-ttu-id="ea30a-316">Zwraca model na końcu `BuildAndTrainModel` metody.</span><span class="sxs-lookup"><span data-stu-id="ea30a-316">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a><span data-ttu-id="ea30a-317">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="ea30a-317">Evaluate the model</span></span>

<span data-ttu-id="ea30a-318">Teraz, po utworzeniu i uczony model, należy ocenić ją z innego zestawu danych do zapewniania jakości i sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="ea30a-318">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="ea30a-319">W `Evaluate` metody, model utworzony w `BuildAndTrainModel` jest przekazywany do obliczenia.</span><span class="sxs-lookup"><span data-stu-id="ea30a-319">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="ea30a-320">Tworzenie `Evaluate` metody tuż za `BuildAndTrainModel`, jak w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="ea30a-320">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate()
{

}
```

<span data-ttu-id="ea30a-321">`Evaluate` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="ea30a-321">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="ea30a-322">Ładuje zestawy danych testowych.</span><span class="sxs-lookup"><span data-stu-id="ea30a-322">Loads the test dataset.</span></span>
* <span data-ttu-id="ea30a-323">Tworzy ewaluatora wieloklasowej.</span><span class="sxs-lookup"><span data-stu-id="ea30a-323">Creates the multiclass evaluator.</span></span>
* <span data-ttu-id="ea30a-324">Oblicza model oraz tworzenie metryk.</span><span class="sxs-lookup"><span data-stu-id="ea30a-324">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="ea30a-325">Przedstawia metryki.</span><span class="sxs-lookup"><span data-stu-id="ea30a-325">Displays the metrics.</span></span>

<span data-ttu-id="ea30a-326">Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `BuildAndTrainModel` wywołania metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ea30a-326">Add a call to the new method from the `Main` method, right under the `BuildAndTrainModel` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

<span data-ttu-id="ea30a-327">Tak jak poprzednio w przypadku zestawu danych szkoleniowych, można łączyć inicjowania, mapowanie i testów ładowania w jednym wierszu kodu zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="ea30a-327">As you did previously with the training dataset, you can combine the initialization, mapping, and test dataset loading into one line of code.</span></span> <span data-ttu-id="ea30a-328">Możesz ocenić modelu przy użyciu tego zestawu danych w celu sprawdzenia jakości.</span><span class="sxs-lookup"><span data-stu-id="ea30a-328">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="ea30a-329">Dodaj następujący kod do `Evaluate` metody:</span><span class="sxs-lookup"><span data-stu-id="ea30a-329">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

<span data-ttu-id="ea30a-330">`MulticlassClassificationContext.Evaluate` Jest otoką <xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A> metody, które oblicza metryk jakości dla modelu przy użyciu określonego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="ea30a-330">The `MulticlassClassificationContext.Evaluate` is a wrapper for the <xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A> method that computes the quality metrics for the model using the specified dataset.</span></span> <span data-ttu-id="ea30a-331">Zwraca <xref:Microsoft.ML.Data.MultiClassClassifierMetrics> obiekt, który zawiera metryki ogólną obliczone przez ewaluatory klasyfikacji wieloklasowej.</span><span class="sxs-lookup"><span data-stu-id="ea30a-331">It returns a <xref:Microsoft.ML.Data.MultiClassClassifierMetrics> object that contains the overall metrics computed by multiclass classification evaluators.</span></span>
<span data-ttu-id="ea30a-332">Aby wyświetlić metryki, aby określić jakość modelu, należy je uzyskać pierwszy.</span><span class="sxs-lookup"><span data-stu-id="ea30a-332">To display the metrics to determine the quality of the model, you need to get them first.</span></span>
<span data-ttu-id="ea30a-333">Zwróć uwagę na `Transform` metoda uczenia maszynowego `_trainedModel` zmiennej globalnej (transformatora) do wprowadzania funkcji i zwracają prognozy.</span><span class="sxs-lookup"><span data-stu-id="ea30a-333">Notice the use of the `Transform` method of the machine learning `_trainedModel` global variable (a transformer) to input the features and return predictions.</span></span> <span data-ttu-id="ea30a-334">Dodaj następujący kod do `Evaluate` metodę jako następny wiersz:</span><span class="sxs-lookup"><span data-stu-id="ea30a-334">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

<span data-ttu-id="ea30a-335">Następujące metryki są oceniane pod kątem wieloklasowej klasyfikacji:</span><span class="sxs-lookup"><span data-stu-id="ea30a-335">The following metrics are evaluated for multiclass classification:</span></span>

* <span data-ttu-id="ea30a-336">Dokładność Micro - każdej pary przykładową klasę przyczynia się jednakowo do metryki dokładności.</span><span class="sxs-lookup"><span data-stu-id="ea30a-336">Micro Accuracy - Every sample-class pair contributes equally to the accuracy metric.</span></span>  <span data-ttu-id="ea30a-337">Chcesz, aby dokładność Micro być jak zbliżone do wartości 1, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="ea30a-337">You want Micro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="ea30a-338">Dokładność — makro — każda klasa przyczynia się jednakowo do metryki dokładności.</span><span class="sxs-lookup"><span data-stu-id="ea30a-338">Macro Accuracy - Every class contributes equally to the accuracy metric.</span></span> <span data-ttu-id="ea30a-339">Moduł klasy są podane weight równe jako większych klas.</span><span class="sxs-lookup"><span data-stu-id="ea30a-339">Minority classes are given equal weight as the larger classes.</span></span> <span data-ttu-id="ea30a-340">Chcesz, aby dokładność — makro sposób maksymalnie zbliżony 1, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="ea30a-340">You want Macro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="ea30a-341">Dziennik utraty — zobacz [utraty dziennika](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="ea30a-341">Log-loss - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="ea30a-342">Ma dziennik utraty sposób maksymalnie zbliżony zero, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="ea30a-342">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="ea30a-343">Zmniejszenie dziennika utraty — zakresy z [-inf, 100], gdzie 100 to doskonałe prognoz i 0 wskazuje średnią prognozy.</span><span class="sxs-lookup"><span data-stu-id="ea30a-343">Log-loss reduction - Ranges from [-inf, 100], where 100 is perfect predictions and 0 indicates mean predictions.</span></span> <span data-ttu-id="ea30a-344">Chcesz, aby zmniejszenie dziennika utraty sposób maksymalnie zbliżony zero, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="ea30a-344">You want Log-loss reduction to be as close to zero as possible.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="ea30a-345">Wyświetlanie metryki dotyczące weryfikacji modelu</span><span class="sxs-lookup"><span data-stu-id="ea30a-345">Displaying the metrics for model validation</span></span>

<span data-ttu-id="ea30a-346">Użyj poniższego kodu, aby wyświetlić metryki, udostępnianie wyników, a następnie działanie na nich:</span><span class="sxs-lookup"><span data-stu-id="ea30a-346">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

### <a name="save-the-trained-and-evaluated-model"></a><span data-ttu-id="ea30a-347">Zapisywanie modelu uczonego i ocenione</span><span class="sxs-lookup"><span data-stu-id="ea30a-347">Save the trained and evaluated model</span></span>

<span data-ttu-id="ea30a-348">W tym momencie masz model typu <xref:Microsoft.ML.Data.TransformerChain%601> , można zintegrować wszystkich istniejących i nowych aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="ea30a-348">At this point, you have a model of type <xref:Microsoft.ML.Data.TransformerChain%601> that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="ea30a-349">Aby zapisać uczonego modelu w pliku .zip, Dodaj następujący kod do wywoływania `SaveModelAsFile` metody w następnym wierszu `BuildAndTrainModel`:</span><span class="sxs-lookup"><span data-stu-id="ea30a-349">To save your trained model to a .zip file, add the following code to call the `SaveModelAsFile` method as the next line in `BuildAndTrainModel`:</span></span>

[!code-csharp[CallSaveModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallSaveModel)]

## <a name="save-the-model-as-a-zip-file"></a><span data-ttu-id="ea30a-350">Zapisz model jako plik .zip</span><span class="sxs-lookup"><span data-stu-id="ea30a-350">Save the model as a .zip file</span></span>

<span data-ttu-id="ea30a-351">Tworzenie `SaveModelAsFile` metody tuż za `Evaluate` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ea30a-351">Create the `SaveModelAsFile` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="ea30a-352">`SaveModelAsFile` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="ea30a-352">The `SaveModelAsFile` method executes the following tasks:</span></span>

* <span data-ttu-id="ea30a-353">Zapisuje modelu w postaci pliku zip.</span><span class="sxs-lookup"><span data-stu-id="ea30a-353">Saves the model as a .zip file.</span></span>

<span data-ttu-id="ea30a-354">Następnie utwórz metodę, aby zapisać modelu mogą być używane ponownie i używane w innych aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="ea30a-354">Next, create a method to save the model so that it can be reused and consumed in other applications.</span></span> <span data-ttu-id="ea30a-355">`ITransformer` Ma <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> metodę, która przyjmuje `_modelPath` globalne pola i <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="ea30a-355">The `ITransformer` has a <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> method that takes in the `_modelPath` global field, and a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="ea30a-356">Aby zapisać model jako plik zip, należy utworzyć `FileStream` bezpośrednio przed wywołaniem `SaveTo` metody.</span><span class="sxs-lookup"><span data-stu-id="ea30a-356">To save the model as a zip file, you'll create the `FileStream` immediately before calling the `SaveTo` method.</span></span> <span data-ttu-id="ea30a-357">Dodaj następujący kod do `SaveModelAsFile` metodę jako następny wiersz:</span><span class="sxs-lookup"><span data-stu-id="ea30a-357">Add the following code to the `SaveModelAsFile` method as the next line:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SaveModel)]

<span data-ttu-id="ea30a-358">Można również wyświetlić, którym został zapisany plik przy pisaniu komunikatu konsoli, za pomocą `_modelPath`, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ea30a-358">You could also display where the file was written by writing a console message with the `_modelPath`, using the following code:</span></span>

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="deploy-and-predict-with-a-loaded-model"></a><span data-ttu-id="ea30a-359">Wdrażanie i przewidywanie załadować modelu</span><span class="sxs-lookup"><span data-stu-id="ea30a-359">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="ea30a-360">Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `Evaluate` wywołania metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ea30a-360">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredictIssue](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

<span data-ttu-id="ea30a-361">Tworzenie `PredictIssue` metody tuż za `Evaluate` — metoda (i tuż przed `SaveModelAsFile` metoda), używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ea30a-361">Create the `PredictIssue` method, just after the `Evaluate` method (and just before the `SaveModelAsFile` method), using the following code:</span></span>

```csharp
private static void PredictIssue()
{

}
```

<span data-ttu-id="ea30a-362">`PredictIssue` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="ea30a-362">The `PredictIssue` method executes the following tasks:</span></span>

* <span data-ttu-id="ea30a-363">Tworzy jeden problem danych testowych.</span><span class="sxs-lookup"><span data-stu-id="ea30a-363">Creates a single issue of test data.</span></span>
* <span data-ttu-id="ea30a-364">Prognozuje obszaru na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="ea30a-364">Predicts Area based on test data.</span></span>
* <span data-ttu-id="ea30a-365">Łączy w sobie testowanie, danych i prognoz dla raportowania.</span><span class="sxs-lookup"><span data-stu-id="ea30a-365">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="ea30a-366">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="ea30a-366">Displays the predicted results.</span></span>

<span data-ttu-id="ea30a-367">Najpierw załadować modelu, które zostały zapisane wcześniej z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="ea30a-367">First, load the model that you saved previously with the following code:</span></span>

[!code-csharp[LoadModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadModel)]

<span data-ttu-id="ea30a-368">Dodaj problem w usłudze GitHub do testowania uczonego modelu prognozowania w `Predict` metody przez utworzenie wystąpienia `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="ea30a-368">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[AddTestIssue](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]
  
<span data-ttu-id="ea30a-369">Teraz, gdy model, możesz go używać, aby przewidzieć etykieta GitHub powierzchni pojedyncze wystąpienie danych problem usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="ea30a-369">Now that you have a model, you can use that to predict the Area GitHub label of a single instance of the GitHub issue data.</span></span> <span data-ttu-id="ea30a-370">Aby uzyskać prognozę, użyj <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> na danych.</span><span class="sxs-lookup"><span data-stu-id="ea30a-370">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="ea30a-371">Dane wejściowe to ciąg, a model zawiera cechowania.</span><span class="sxs-lookup"><span data-stu-id="ea30a-371">The input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="ea30a-372">Potok jest zsynchronizowany podczas uczenia i przewidywania.</span><span class="sxs-lookup"><span data-stu-id="ea30a-372">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="ea30a-373">Nie trzeba napisać kod przetwarzania wstępnego cechowania specjalnie dla prognoz i zajmuje się tego samego interfejsu API i usługi batch jednorazowe prognozy.</span><span class="sxs-lookup"><span data-stu-id="ea30a-373">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span> <span data-ttu-id="ea30a-374">Dodaj następujący kod do `PredictIssue` metodę dla prognoz:</span><span class="sxs-lookup"><span data-stu-id="ea30a-374">Add the following code to the `PredictIssue` method for the predictions:</span></span>

[!code-csharp[PredictIssue](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a><span data-ttu-id="ea30a-375">Przy użyciu załadować modelu do prognozowania</span><span class="sxs-lookup"><span data-stu-id="ea30a-375">Using the loaded model for prediction</span></span>

<span data-ttu-id="ea30a-376">Wyświetlanie `Area` celu kategoryzowania problem i odpowiednie do nich działanie na nim.</span><span class="sxs-lookup"><span data-stu-id="ea30a-376">Display `Area` in order to categorize the issue and act on it accordingly.</span></span> <span data-ttu-id="ea30a-377">Tworzenie ekranu wyników za pomocą następujących <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:</span><span class="sxs-lookup"><span data-stu-id="ea30a-377">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayResults](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a><span data-ttu-id="ea30a-378">Wyniki</span><span class="sxs-lookup"><span data-stu-id="ea30a-378">Results</span></span>

<span data-ttu-id="ea30a-379">Wyniki powinny być podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="ea30a-379">Your results should be similar to the following.</span></span> <span data-ttu-id="ea30a-380">Ponieważ przetwarza potoku, wyświetla komunikaty.</span><span class="sxs-lookup"><span data-stu-id="ea30a-380">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="ea30a-381">Może zostać wyświetlony ostrzeżenia lub komunikaty przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="ea30a-381">You may see warnings, or processing messages.</span></span> <span data-ttu-id="ea30a-382">Te komunikaty zostały usunięte z następujących wyników dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="ea30a-382">These messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="ea30a-383">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="ea30a-383">Congratulations!</span></span> <span data-ttu-id="ea30a-384">Teraz został pomyślnie skompilowany usługi machine learning model do klasyfikowania i prognozowanie etykieta obszar problemu w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="ea30a-384">You've now successfully built a machine learning model for classifying and predicting an Area label for a GitHub issue.</span></span> <span data-ttu-id="ea30a-385">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="ea30a-385">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ea30a-386">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="ea30a-386">Next steps</span></span>

<span data-ttu-id="ea30a-387">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="ea30a-387">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="ea30a-388">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="ea30a-388">Understand the problem</span></span>
> * <span data-ttu-id="ea30a-389">Wybieranie algorytmu uczenia maszynowego odpowiednie</span><span class="sxs-lookup"><span data-stu-id="ea30a-389">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="ea30a-390">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="ea30a-390">Prepare your data</span></span>
> * <span data-ttu-id="ea30a-391">Przekształcanie danych</span><span class="sxs-lookup"><span data-stu-id="ea30a-391">Transform the data</span></span>
> * <span data-ttu-id="ea30a-392">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="ea30a-392">Train the model</span></span>
> * <span data-ttu-id="ea30a-393">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="ea30a-393">Evaluate the model</span></span>
> * <span data-ttu-id="ea30a-394">Prognozowanie za pomocą uczonego modelu</span><span class="sxs-lookup"><span data-stu-id="ea30a-394">Predict with the trained model</span></span>
> * <span data-ttu-id="ea30a-395">Wdrażanie i przewidywanie załadować modelu</span><span class="sxs-lookup"><span data-stu-id="ea30a-395">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="ea30a-396">Przejdź do następnego samouczka, aby dowiedzieć się więcej</span><span class="sxs-lookup"><span data-stu-id="ea30a-396">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="ea30a-397">Taxi Fare Predictor</span><span class="sxs-lookup"><span data-stu-id="ea30a-397">Taxi Fare Predictor</span></span>](taxi-fare.md)
