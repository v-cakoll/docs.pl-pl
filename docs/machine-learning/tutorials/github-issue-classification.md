---
title: Użyj strukturze ML.NET w scenariuszu wieloklasowej klasyfikacji problemu usługi GitHub
description: Dowiedz się, jak używać strukturze ML.NET w scenariuszu wieloklasowej klasyfikacji można klasyfikować problemy usługi GitHub, aby przypisać je do danego obszaru.
ms.date: 03/12/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e25f044247064db26e4e1e74590d6f4970fe4477
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019129"
---
# <a name="tutorial-use-mlnet-in-a-multiclass-classification-scenario-to-classify-github-issues"></a><span data-ttu-id="5a510-103">Samouczek: Umożliwia strukturze ML.NET w scenariuszu klasyfikacji wieloklasowej klasyfikacji problemów w usłudze GitHub</span><span class="sxs-lookup"><span data-stu-id="5a510-103">Tutorial: Use ML.NET in a multiclass classification scenario to classify GitHub issues</span></span>

<span data-ttu-id="5a510-104">Ten przykładowy samouczek przedstawia tworzenie klasyfikatora problem usługi GitHub za pomocą używany aplikację konsoli .NET Core przy użyciu strukturze ML.NET C# w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="5a510-104">This sample tutorial illustrates using ML.NET to create a GitHub issue classifier via a .NET Core console application using C# in Visual Studio 2017.</span></span>

<span data-ttu-id="5a510-105">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="5a510-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="5a510-106">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="5a510-106">Understand the problem</span></span>
> * <span data-ttu-id="5a510-107">Wybieranie algorytmu uczenia maszynowego odpowiednie</span><span class="sxs-lookup"><span data-stu-id="5a510-107">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="5a510-108">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="5a510-108">Prepare your data</span></span>
> * <span data-ttu-id="5a510-109">Przekształcanie danych</span><span class="sxs-lookup"><span data-stu-id="5a510-109">Transform the data</span></span>
> * <span data-ttu-id="5a510-110">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="5a510-110">Train the model</span></span>
> * <span data-ttu-id="5a510-111">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="5a510-111">Evaluate the model</span></span>
> * <span data-ttu-id="5a510-112">Prognozowanie za pomocą uczonego modelu</span><span class="sxs-lookup"><span data-stu-id="5a510-112">Predict with the trained model</span></span>
> * <span data-ttu-id="5a510-113">Wdrażanie i przewidywanie załadować modelu</span><span class="sxs-lookup"><span data-stu-id="5a510-113">Deploy and Predict with a loaded model</span></span>

> [!NOTE]
> <span data-ttu-id="5a510-114">W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="5a510-114">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="5a510-115">Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="5a510-115">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="5a510-116">Obecnie używasz tego samouczka, a powiązane próbki **strukturze ML.NET wersji 0,11**.</span><span class="sxs-lookup"><span data-stu-id="5a510-116">This tutorial and related sample are currently using **ML.NET version 0.11**.</span></span> <span data-ttu-id="5a510-117">Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium dotnet/machinelearning github](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="5a510-117">For more information, see the release notes at the [dotnet/machinelearning github repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

## <a name="github-issue-sample-overview"></a><span data-ttu-id="5a510-118">Omówienie przykładowych problem usługi GitHub</span><span class="sxs-lookup"><span data-stu-id="5a510-118">GitHub issue sample overview</span></span>

<span data-ttu-id="5a510-119">Próbka jest aplikacją konsoli, która używa strukturze ML.NET do nauczenia modelu, która klasyfikuje i przewiduje etykieta obszar problemu w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="5a510-119">The sample is a console app that uses ML.NET to train a model that classifies and predicts the Area label for a GitHub issue.</span></span> <span data-ttu-id="5a510-120">Oblicza model z drugiego zestawu danych do analizy jakości dostawców.</span><span class="sxs-lookup"><span data-stu-id="5a510-120">It also evaluates the model with a second dataset for quality analysis.</span></span> <span data-ttu-id="5a510-121">Zestawy danych problem pochodzą z repozytorium GitHub dotnet/corefx.</span><span class="sxs-lookup"><span data-stu-id="5a510-121">The issue datasets are from the dotnet/corefx GitHub repo.</span></span>

<span data-ttu-id="5a510-122">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="5a510-122">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5a510-123">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="5a510-123">Prerequisites</span></span>

* <span data-ttu-id="5a510-124">[Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".</span><span class="sxs-lookup"><span data-stu-id="5a510-124">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="5a510-125">[Github generuje plik z wartościami oddzielonymi tabulatorami (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span><span class="sxs-lookup"><span data-stu-id="5a510-125">The [Github issues tab separated file (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span></span>
* <span data-ttu-id="5a510-126">[Problemy usługi Github test pliku z wartościami oddzielonymi tabulatorami (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span><span class="sxs-lookup"><span data-stu-id="5a510-126">The [Github issues test tab separated file (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="5a510-127">Maszyny uczenie się przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="5a510-127">Machine learning workflow</span></span>

<span data-ttu-id="5a510-128">W tym samouczku poniżej przepływu pracy, który umożliwia proces przenoszenia w sposób uporządkowany uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="5a510-128">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="5a510-129">Fazy przepływu pracy są następujące:</span><span class="sxs-lookup"><span data-stu-id="5a510-129">The workflow phases are as follows:</span></span>

1. <span data-ttu-id="5a510-130">**Omówienie problemu**</span><span class="sxs-lookup"><span data-stu-id="5a510-130">**Understand the problem**</span></span>
2. <span data-ttu-id="5a510-131">**Przygotowywanie danych**</span><span class="sxs-lookup"><span data-stu-id="5a510-131">**Prepare your data**</span></span>
   * <span data-ttu-id="5a510-132">**Ładowanie danych**</span><span class="sxs-lookup"><span data-stu-id="5a510-132">**Load the data**</span></span>
   * <span data-ttu-id="5a510-133">**Wyodrębnianie funkcji (przekształcania danych)**</span><span class="sxs-lookup"><span data-stu-id="5a510-133">**Extract features (Transform your data)**</span></span>
3. <span data-ttu-id="5a510-134">**Kompilowanie i szkolenie**</span><span class="sxs-lookup"><span data-stu-id="5a510-134">**Build and train**</span></span> 
   * <span data-ttu-id="5a510-135">**Uczenie modelu**</span><span class="sxs-lookup"><span data-stu-id="5a510-135">**Train the model**</span></span>
   * <span data-ttu-id="5a510-136">**Ocena modelu**</span><span class="sxs-lookup"><span data-stu-id="5a510-136">**Evaluate the model**</span></span>
4. <span data-ttu-id="5a510-137">**Wdrażanie modelu**</span><span class="sxs-lookup"><span data-stu-id="5a510-137">**Deploy Model**</span></span>
   * <span data-ttu-id="5a510-138">**Użyj modelu do prognozowania**</span><span class="sxs-lookup"><span data-stu-id="5a510-138">**Use the Model to predict**</span></span>

### <a name="understand-the-problem"></a><span data-ttu-id="5a510-139">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="5a510-139">Understand the problem</span></span>

<span data-ttu-id="5a510-140">Należy najpierw zrozumieć, dzięki czemu można podzielić je w dół do części obsługujące kompilowanie i uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="5a510-140">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="5a510-141">Potężne problem umożliwia prognozowanie i ocena wyników.</span><span class="sxs-lookup"><span data-stu-id="5a510-141">Breaking  down the problem allows you to predict and evaluate the results.</span></span>

<span data-ttu-id="5a510-142">Ten problem, w tym samouczku jest zrozumienie przychodzące problemy usługi GitHub powierzchni należą do, aby można było oznaczyć je poprawnie priorytetyzacja i planowanie.</span><span class="sxs-lookup"><span data-stu-id="5a510-142">The problem for this tutorial is to understand what area incoming GitHub issues belong to in order to label them correctly for prioritization and scheduling.</span></span>

<span data-ttu-id="5a510-143">Ten problem można podzielić na następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="5a510-143">You can break down the problem to the following parts:</span></span>

* <span data-ttu-id="5a510-144">tekst tytułu problem</span><span class="sxs-lookup"><span data-stu-id="5a510-144">the issue title text</span></span>
* <span data-ttu-id="5a510-145">tekst opisu problemu</span><span class="sxs-lookup"><span data-stu-id="5a510-145">the issue description text</span></span>
* <span data-ttu-id="5a510-146">wartość obszaru danych szkoleniowych modelu</span><span class="sxs-lookup"><span data-stu-id="5a510-146">an area value for the model training data</span></span>
* <span data-ttu-id="5a510-147">wartość obszaru przewidywane, można obliczyć, a następnie za pomocą pod względem</span><span class="sxs-lookup"><span data-stu-id="5a510-147">a predicted area value that you can evaluate and then use operationally</span></span>

<span data-ttu-id="5a510-148">Następnie należy **określić** obszar, który ułatwia wybór zadań uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="5a510-148">You then need to **determine** the area, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-algorithm"></a><span data-ttu-id="5a510-149">Wybieranie algorytmu uczenia maszynowego odpowiednie</span><span class="sxs-lookup"><span data-stu-id="5a510-149">Select the appropriate machine learning algorithm</span></span>

<span data-ttu-id="5a510-150">W rozwiązaniu tego problemu znasz następujące fakty:</span><span class="sxs-lookup"><span data-stu-id="5a510-150">With this problem, you know the following facts:</span></span>

<span data-ttu-id="5a510-151">Dane szkoleniowe:</span><span class="sxs-lookup"><span data-stu-id="5a510-151">Training data:</span></span>

<span data-ttu-id="5a510-152">Problemy usługi GitHub może być oznaczony jako w kilku obszarach (**obszaru**) jak w następujących przykładach:</span><span class="sxs-lookup"><span data-stu-id="5a510-152">GitHub issues can be labeled in several areas (**Area**) as in the following examples:</span></span>

* <span data-ttu-id="5a510-153">area-System.Numerics</span><span class="sxs-lookup"><span data-stu-id="5a510-153">area-System.Numerics</span></span>
* <span data-ttu-id="5a510-154">area-System.Xml</span><span class="sxs-lookup"><span data-stu-id="5a510-154">area-System.Xml</span></span>
* <span data-ttu-id="5a510-155">obszar infrastruktura</span><span class="sxs-lookup"><span data-stu-id="5a510-155">area-Infrastructure</span></span>
* <span data-ttu-id="5a510-156">area-System.Linq</span><span class="sxs-lookup"><span data-stu-id="5a510-156">area-System.Linq</span></span>
* <span data-ttu-id="5a510-157">area-System.IO</span><span class="sxs-lookup"><span data-stu-id="5a510-157">area-System.IO</span></span>

<span data-ttu-id="5a510-158">Przewidywanie **obszaru** z nowego problemu w usłudze GitHub takich jak w następujących przykładach:</span><span class="sxs-lookup"><span data-stu-id="5a510-158">Predict the **Area** of a new GitHub Issue such as in the following examples:</span></span>

* <span data-ttu-id="5a510-159">Contract.Assert vs Debug.Assert</span><span class="sxs-lookup"><span data-stu-id="5a510-159">Contract.Assert vs Debug.Assert</span></span>
* <span data-ttu-id="5a510-160">Tworzenie pola tylko do odczytu w System.Xml</span><span class="sxs-lookup"><span data-stu-id="5a510-160">Make fields readonly in System.Xml</span></span>

<span data-ttu-id="5a510-161">Algorytmu uczenia maszynowego klasyfikacji najlepiej nadaje się dla tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="5a510-161">The classification machine learning algorithm is best suited for this scenario.</span></span>

### <a name="about-the-classification-learning-algorithm"></a><span data-ttu-id="5a510-162">Temat algorytmu uczenia klasyfikacji</span><span class="sxs-lookup"><span data-stu-id="5a510-162">About the classification learning algorithm</span></span>

<span data-ttu-id="5a510-163">Klasyfikacja jest algorytm uczenia maszynowego, która korzysta z danych do **określić** kategorii, typ lub klasa elementu lub wiersza danych.</span><span class="sxs-lookup"><span data-stu-id="5a510-163">Classification is a machine learning algorithm that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="5a510-164">Na przykład można użyć klasyfikacji:</span><span class="sxs-lookup"><span data-stu-id="5a510-164">For example, you can use classification to:</span></span>

* <span data-ttu-id="5a510-165">Zidentyfikuj tonacji jako dodatnia lub ujemna.</span><span class="sxs-lookup"><span data-stu-id="5a510-165">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="5a510-166">Klasyfikowanie wiadomości e-mail jako spam, wiadomości-śmieci lub właściwej.</span><span class="sxs-lookup"><span data-stu-id="5a510-166">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="5a510-167">Ustal, czy pacjent laboratorium przykładowe dane stanowią cancerous.</span><span class="sxs-lookup"><span data-stu-id="5a510-167">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="5a510-168">Klienci na kategorie według ich tendencje do odpowiedzi na kampanię sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="5a510-168">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="5a510-169">Klasyfikacja, Użyj algorytmu uczenia przypadki są często jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="5a510-169">Classification learning algorithm use cases are frequently one of the following types:</span></span>

* <span data-ttu-id="5a510-170">Plik binarny: A i B.</span><span class="sxs-lookup"><span data-stu-id="5a510-170">Binary: either A or B.</span></span>
* <span data-ttu-id="5a510-171">Kontra: wielu kategorii, które można przewidzieć przy użyciu pojedynczego modelu.</span><span class="sxs-lookup"><span data-stu-id="5a510-171">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="5a510-172">Tego rodzaju problem korzystanie z klasyfikacji kontra, uczenie algorytmu, ponieważ do prognozowania kategorii problemu może być jednym z wielu kategorii (kontra), a nie tylko dwóch (binarnych).</span><span class="sxs-lookup"><span data-stu-id="5a510-172">For this type of problem, use a Multiclass classification learning algorithm, since your issue category prediction can be one of multiple categories (multiclass) rather than just two (binary).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="5a510-173">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="5a510-173">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="5a510-174">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="5a510-174">Create a project</span></span>

1. <span data-ttu-id="5a510-175">Otwórz program Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="5a510-175">Open Visual Studio 2017.</span></span> <span data-ttu-id="5a510-176">Wybierz **pliku** > **New** > **projektu** z paska menu.</span><span class="sxs-lookup"><span data-stu-id="5a510-176">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="5a510-177">W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła następuje **platformy .NET Core** węzła.</span><span class="sxs-lookup"><span data-stu-id="5a510-177">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="5a510-178">Następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="5a510-178">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="5a510-179">W **nazwa** pole tekstowe, wpisz "GitHubIssueClassification", a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="5a510-179">In the **Name** text box, type "GitHubIssueClassification" and then select the **OK** button.</span></span>

2. <span data-ttu-id="5a510-180">Utwórz katalog o nazwie *danych* w projekcie, aby zapisać pliki zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="5a510-180">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="5a510-181">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nad projektem i wybierz **Dodaj** > **nowy Folder**.</span><span class="sxs-lookup"><span data-stu-id="5a510-181">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="5a510-182">Wpisz "Dane", a następnie naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="5a510-182">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="5a510-183">Utwórz katalog o nazwie *modeli* w projekcie, aby zapisać modelu:</span><span class="sxs-lookup"><span data-stu-id="5a510-183">Create a directory named *Models* in your project to save your model:</span></span>

    <span data-ttu-id="5a510-184">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nad projektem i wybierz **Dodaj** > **nowy Folder**.</span><span class="sxs-lookup"><span data-stu-id="5a510-184">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="5a510-185">Wpisz "Modele", a następnie naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="5a510-185">Type "Models" and hit Enter.</span></span>

4. <span data-ttu-id="5a510-186">Zainstaluj **pakietu NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="5a510-186">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="5a510-187">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="5a510-187">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="5a510-188">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="5a510-188">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="5a510-189">Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.</span><span class="sxs-lookup"><span data-stu-id="5a510-189">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="5a510-190">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="5a510-190">Prepare your data</span></span>

1. <span data-ttu-id="5a510-191">Pobierz [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) i [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) danych ustawia i zapisywanie ich *danych* wcześniej utworzony folder.</span><span class="sxs-lookup"><span data-stu-id="5a510-191">Download the [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) and the [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="5a510-192">Szkolenie modeli modelu uczenia maszynowego na pierwszego zestawu danych, a drugi może służyć do oceny, jak dokładna jest model.</span><span class="sxs-lookup"><span data-stu-id="5a510-192">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="5a510-193">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy każdy z \*pliki tsv i wybierz pozycję **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="5a510-193">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="5a510-194">W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="5a510-194">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="5a510-195">Tworzenie klas i definiowania ścieżek</span><span class="sxs-lookup"><span data-stu-id="5a510-195">Create classes and define paths</span></span>

<span data-ttu-id="5a510-196">Dodaj następujące dodatkowe `using` instrukcji na górze *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="5a510-196">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

<span data-ttu-id="5a510-197">Utwórz trzy pola globalnego na potrzeby przechowywania ścieżek do ostatnio pobrane pliki i zmiennych globalnych `MLContext`,`DataView`, `PredictionEngine`, i `TextLoader`:</span><span class="sxs-lookup"><span data-stu-id="5a510-197">Create three global fields to hold the paths to the recently downloaded files, and global variables for the `MLContext`,`DataView`, `PredictionEngine`, and `TextLoader`:</span></span>

* <span data-ttu-id="5a510-198">`_trainDataPath` zawiera ścieżkę do zestawu danych, używane do trenowania modelu.</span><span class="sxs-lookup"><span data-stu-id="5a510-198">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="5a510-199">`_testDataPath` zawiera ścieżkę do zestawu danych, używane do oceny modelu.</span><span class="sxs-lookup"><span data-stu-id="5a510-199">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="5a510-200">`_modelPath` ma ścieżkę, w którym jest zapisany trenowanego modelu.</span><span class="sxs-lookup"><span data-stu-id="5a510-200">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="5a510-201">`_mlContext` jest <xref:Microsoft.ML.MLContext> zapewniający przetwarzania kontekstu.</span><span class="sxs-lookup"><span data-stu-id="5a510-201">`_mlContext` is the <xref:Microsoft.ML.MLContext> that provides processing context.</span></span>
* <span data-ttu-id="5a510-202">`_trainingDataView` jest <xref:Microsoft.Data.DataView.IDataView> używani do przetwarzania zestaw danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="5a510-202">`_trainingDataView` is the <xref:Microsoft.Data.DataView.IDataView> used to process the training dataset.</span></span>
* <span data-ttu-id="5a510-203">`_predEngine` jest <xref:Microsoft.ML.PredictionEngine%602> używany dla pojedynczego prognozy.</span><span class="sxs-lookup"><span data-stu-id="5a510-203">`_predEngine` is the <xref:Microsoft.ML.PredictionEngine%602> used for single predictions.</span></span>
* <span data-ttu-id="5a510-204">`_reader` jest <xref:Microsoft.ML.Data.TextLoader> używany do ładowania i przekształcić zestawy danych.</span><span class="sxs-lookup"><span data-stu-id="5a510-204">`_reader` is the <xref:Microsoft.ML.Data.TextLoader> used to load and transform the datasets.</span></span>

<span data-ttu-id="5a510-205">Dodaj następujący kod po prawej stronie wiersza powyżej `Main` metodę, aby określić ścieżki te i inne zmienne:</span><span class="sxs-lookup"><span data-stu-id="5a510-205">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="5a510-206">Utwórz niektóre klasy dla danych wejściowych i prognozy.</span><span class="sxs-lookup"><span data-stu-id="5a510-206">Create some classes for your input data and predictions.</span></span> <span data-ttu-id="5a510-207">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="5a510-207">Add a new class to your project:</span></span>

1. <span data-ttu-id="5a510-208">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="5a510-208">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="5a510-209">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *GitHubIssueData.cs*.</span><span class="sxs-lookup"><span data-stu-id="5a510-209">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *GitHubIssueData.cs*.</span></span> <span data-ttu-id="5a510-210">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="5a510-210">Then, select the **Add** button.</span></span>

    <span data-ttu-id="5a510-211">*GitHubIssueData.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="5a510-211">The *GitHubIssueData.cs* file opens in the code editor.</span></span> <span data-ttu-id="5a510-212">Dodaj następujący kod `using` instrukcji na górze *GitHubIssueData.cs*:</span><span class="sxs-lookup"><span data-stu-id="5a510-212">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

<span data-ttu-id="5a510-213">Usuń istniejącą definicję klasy i Dodaj następujący kod, który zawiera dwie klasy `GitHubIssue` i `IssuePrediction`, *GitHubIssueData.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="5a510-213">Remove the existing class definition and add the following code, which has two classes `GitHubIssue` and `IssuePrediction`, to the *GitHubIssueData.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

<span data-ttu-id="5a510-214">`GitHubIssue` jest to klasa wejściowy zestaw danych i ma następujące <xref:System.String> pola:</span><span class="sxs-lookup"><span data-stu-id="5a510-214">`GitHubIssue` is the input dataset class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="5a510-215">`ID` zawiera wartość dla Identyfikatora problemu usługi GitHub</span><span class="sxs-lookup"><span data-stu-id="5a510-215">`ID` contains a value for the GitHub issue ID</span></span>
* <span data-ttu-id="5a510-216">`Area` zawiera wartość dla `Area` etykiety</span><span class="sxs-lookup"><span data-stu-id="5a510-216">`Area` contains a value for the `Area` label</span></span>
* <span data-ttu-id="5a510-217">`Title` zawiera tytuł problemu usługi GitHub</span><span class="sxs-lookup"><span data-stu-id="5a510-217">`Title` contains the GitHub issue title</span></span>
* <span data-ttu-id="5a510-218">`Description` Zawiera opis problemu usługi GitHub</span><span class="sxs-lookup"><span data-stu-id="5a510-218">`Description` contains the GitHub issue description</span></span>

<span data-ttu-id="5a510-219">`IssuePrediction` Klasa służy do prognozowania po wyszkoliła modelu.</span><span class="sxs-lookup"><span data-stu-id="5a510-219">`IssuePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="5a510-220">Ma on jeden `string` (`Area`) i `PredictedLabel` `ColumnName` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="5a510-220">It has a single `string` (`Area`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="5a510-221">`Label` Umożliwia tworzenie i uczenie modelu, a także drugiego zestawu danych do ewaluacji modelu.</span><span class="sxs-lookup"><span data-stu-id="5a510-221">The `Label` is used to create and train the model, and it's also used with a second dataset to evaluate the model.</span></span> <span data-ttu-id="5a510-222">`PredictedLabel` Używany podczas prognoz i oceny.</span><span class="sxs-lookup"><span data-stu-id="5a510-222">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="5a510-223">W wersji ewaluacyjnej używane są dane szkoleniowe, przewidywane wartości i model danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="5a510-223">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="5a510-224">Podczas tworzenia modelu za pomocą platformy ML.NET, rozpoczyna się od utworzenia <xref:Microsoft.ML.MLContext>.</span><span class="sxs-lookup"><span data-stu-id="5a510-224">When building a model with ML.NET, you start by creating an <xref:Microsoft.ML.MLContext>.</span></span> <span data-ttu-id="5a510-225">`MLContext` można porównywać pod względem koncepcyjnym do korzystania z `DbContext` platformy Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="5a510-225">`MLContext` is comparable conceptually to using `DbContext` in Entity Framework.</span></span> <span data-ttu-id="5a510-226">Środowisko dostarcza kontekst dla zadania uczenia Maszynowego, który może służyć do wyjątku, śledzenie i rejestrowanie.</span><span class="sxs-lookup"><span data-stu-id="5a510-226">The environment provides a context for your ML job that can be used for exception tracking and logging.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="5a510-227">Inicjowanie zmiennych w głównym oknie</span><span class="sxs-lookup"><span data-stu-id="5a510-227">Initialize variables in Main</span></span>

<span data-ttu-id="5a510-228">Inicjowanie `_mlContext` zmienna globalna o nowe wystąpienie klasy `MLContext` z Inicjator losowy (`seed: 0`) dla powtarzalnych/deterministyczne wyników w szkoleniach wielu.</span><span class="sxs-lookup"><span data-stu-id="5a510-228">Initialize the `_mlContext` global variable  with a new instance of `MLContext` with a random seed (`seed: 0`) for repeatable/deterministic results across multiple trainings.</span></span>  <span data-ttu-id="5a510-229">Zastąp `Console.WriteLine("Hello World!")` wiersz poniższym kodem w `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="5a510-229">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a><span data-ttu-id="5a510-230">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="5a510-230">Load the data</span></span>

<span data-ttu-id="5a510-231">Następnie zainicjuj `_trainingDataView` <xref:Microsoft.Data.DataView.IDataView> zmiennej globalnej i ładowanie danych za pomocą `_trainDataPath` parametru.</span><span class="sxs-lookup"><span data-stu-id="5a510-231">Next, initialize the `_trainingDataView` <xref:Microsoft.Data.DataView.IDataView> global variable and load the data with the `_trainDataPath` parameter.</span></span>

 <span data-ttu-id="5a510-232">Jako dane wejściowe i wyjściowe [ `Transforms` ](../basic-concepts-model-training-in-mldotnet.md#transformer), `DataView` jest typem potoku danych podstawowych porównywalne do `IEnumerable` dla `LINQ`.</span><span class="sxs-lookup"><span data-stu-id="5a510-232">As the input and output of [`Transforms`](../basic-concepts-model-training-in-mldotnet.md#transformer), a `DataView` is the fundamental data pipeline type, comparable to `IEnumerable` for `LINQ`.</span></span>

<span data-ttu-id="5a510-233">W strukturze ML.NET, dane są podobne do `SQL view`.</span><span class="sxs-lookup"><span data-stu-id="5a510-233">In ML.NET, data is similar to a `SQL view`.</span></span> <span data-ttu-id="5a510-234">Jest opóźnieniem ocenianą informatycznych i heterogenicznych.</span><span class="sxs-lookup"><span data-stu-id="5a510-234">It is lazily evaluated, schematized, and heterogenous.</span></span> <span data-ttu-id="5a510-235">Obiekt jest pierwszą częścią potoku i służy do ładowania danych.</span><span class="sxs-lookup"><span data-stu-id="5a510-235">The object is the first part of the pipeline, and loads the data.</span></span> <span data-ttu-id="5a510-236">W tym samouczku ładuje zestaw danych o problem tytułów, opisów i odpowiednie etykiety GitHub powierzchni.</span><span class="sxs-lookup"><span data-stu-id="5a510-236">For this tutorial, it loads a dataset with issue titles, descriptions, and corresponding area GitHub label.</span></span> <span data-ttu-id="5a510-237">`DataView` Umożliwia tworzenie i trenowanie modelu.</span><span class="sxs-lookup"><span data-stu-id="5a510-237">The `DataView` is used to create and train the model.</span></span>

<span data-ttu-id="5a510-238">Ponieważ utworzone wcześniej `GitHubIssue` typ modelu danych jest zgodny schemat zestawu danych, można połączyć inicjowania, mapowanie i zestaw danych ładowania do jednego wiersza kodu.</span><span class="sxs-lookup"><span data-stu-id="5a510-238">Since your previously created `GitHubIssue` data model type matches the dataset schema, you can combine the initialization, mapping, and dataset loading into one line of code.</span></span>

<span data-ttu-id="5a510-239">Ładowanie danych za pomocą `MLContext.Data.LoadFromTextFile` otoki dla [metoda LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29).</span><span class="sxs-lookup"><span data-stu-id="5a510-239">Load the data using the `MLContext.Data.LoadFromTextFile` wrapper for the [LoadFromTextFile method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29).</span></span> <span data-ttu-id="5a510-240">Zwraca <xref:Microsoft.Data.DataView.IDataView> którego wnioskuje schemat zestawu danych z `GitHubIssue` typ modelu danych i używa nagłówka zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="5a510-240">It returns a <xref:Microsoft.Data.DataView.IDataView> which infers the dataset schema from the `GitHubIssue` data model type and uses the dataset header.</span></span> 

<span data-ttu-id="5a510-241">Wcześniej zdefiniowany schemat danych podczas tworzenia `GitHubIssue` klasy.</span><span class="sxs-lookup"><span data-stu-id="5a510-241">You defined the data schema previously when you created the `GitHubIssue` class.</span></span> <span data-ttu-id="5a510-242">Dla schematu:</span><span class="sxs-lookup"><span data-stu-id="5a510-242">For your schema:</span></span>

* <span data-ttu-id="5a510-243">Pierwsza kolumna `ID` (identyfikator problemu usługi GitHub)</span><span class="sxs-lookup"><span data-stu-id="5a510-243">the first column `ID` (GitHub Issue ID)</span></span>
* <span data-ttu-id="5a510-244">druga kolumna `Area` (prognozowane potrzeby szkolenia)</span><span class="sxs-lookup"><span data-stu-id="5a510-244">the second column `Area` (the prediction for training)</span></span>
* <span data-ttu-id="5a510-245">trzecia kolumna `Title` (tytuł problemu usługi GitHub) jest to pierwszy [funkcji](../resources/glossary.md##feature) używane do prognozowania `Area`</span><span class="sxs-lookup"><span data-stu-id="5a510-245">the third column `Title` (GitHub issue title) is the first [feature](../resources/glossary.md##feature)  used for predicting the `Area`</span></span>
* <span data-ttu-id="5a510-246">Czwarta kolumna `Description` jest druga funkcja używana do prognozowania `Area`</span><span class="sxs-lookup"><span data-stu-id="5a510-246">the fourth column  `Description` is the second feature used for predicting the `Area`</span></span>

<span data-ttu-id="5a510-247">Aby zainicjować i załadować `_trainingDataView` zmienna globalna, aby mógł zostać użyty dla potoku, Dodaj następujący kod po `mlContext` inicjowania:</span><span class="sxs-lookup"><span data-stu-id="5a510-247">To initialize and load the `_trainingDataView` global variable in order to use it for the pipeline, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]

<span data-ttu-id="5a510-248">Dodaj następujący kod jako następnego wiersza kodu w `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="5a510-248">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallProcessData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

<span data-ttu-id="5a510-249">`ProcessData` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="5a510-249">The `ProcessData` method executes the following tasks:</span></span>

* <span data-ttu-id="5a510-250">Wyodrębnia i przekształca dane.</span><span class="sxs-lookup"><span data-stu-id="5a510-250">Extracts and transforms the data.</span></span>
* <span data-ttu-id="5a510-251">Zwraca potoku przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="5a510-251">Returns the processing pipeline.</span></span>

<span data-ttu-id="5a510-252">Tworzenie `ProcessData` metody tuż za `Main` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="5a510-252">Create the `ProcessData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="5a510-253">Wyodrębnianie funkcji i przekształcania danych</span><span class="sxs-lookup"><span data-stu-id="5a510-253">Extract Features and transform the data</span></span>

<span data-ttu-id="5a510-254">Wstępne przetwarzanie i czyszczenie danych są ważne zadania, które występują przed zestaw danych jest efektywnie używać uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="5a510-254">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="5a510-255">Nieprzetworzone dane są często hałas i zawodnych i może brakować wartości.</span><span class="sxs-lookup"><span data-stu-id="5a510-255">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="5a510-256">Korzystanie z danych bez tych zadań modelowania może spowodować wyświetlenie nieprawdziwych wyników.</span><span class="sxs-lookup"><span data-stu-id="5a510-256">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="5a510-257">UCZENIE MASZYNOWE. Potoki przekształcenie firmy NET tworzą niestandardową `transforms`zestaw, który jest stosowany do dane przed szkolenie i testowanie.</span><span class="sxs-lookup"><span data-stu-id="5a510-257">ML.NET's transform pipelines compose a custom `transforms`set that is applied to your data before training or testing.</span></span> <span data-ttu-id="5a510-258">Przekształcenia głównym celem jest danych [cechowania](../resources/glossary.md#feature-engineering).</span><span class="sxs-lookup"><span data-stu-id="5a510-258">The transforms' primary purpose is data [featurization](../resources/glossary.md#feature-engineering).</span></span> <span data-ttu-id="5a510-259">Omówienie algorytmów uczenia maszynowego [neural](../resources/glossary.md#feature) dane, dzięki czemu następnym krokiem jest do przekształcania danych tekstowych do formatu, który rozpoznaje nasze algorytmy uczenia Maszynowego.</span><span class="sxs-lookup"><span data-stu-id="5a510-259">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, so the next step is to transform our textual data into a format that our ML algorithms recognize.</span></span> <span data-ttu-id="5a510-260">Ten format jest [liczbowych wektor](../resources/glossary.md#numerical-feature-vector).</span><span class="sxs-lookup"><span data-stu-id="5a510-260">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="5a510-261">W następnych krokach nazywamy kolumny według nazw zdefiniowana w `GitHubIssue` klasy.</span><span class="sxs-lookup"><span data-stu-id="5a510-261">In the next steps, we refer to the columns by the names defined in the `GitHubIssue` class.</span></span>

<span data-ttu-id="5a510-262">Gdy wiedzę i oceniane, domyślne wartości w modelu **etykiety** kolumny będą traktowane jako prawidłowe wartości do można przewidzieć.</span><span class="sxs-lookup"><span data-stu-id="5a510-262">When the model is trained and evaluated, by default, the values in the **Label** column are considered as correct values to be predicted.</span></span> <span data-ttu-id="5a510-263">Ponieważ chcemy przewidzieć etykieta GitHub powierzchni `GitHubIssue`, kopia `Area` kolumny na **etykiety** kolumny.</span><span class="sxs-lookup"><span data-stu-id="5a510-263">As we want to predict the Area GitHub label for a `GitHubIssue`, copy the `Area` column into the **Label** column.</span></span> <span data-ttu-id="5a510-264">Aby to zrobić, należy użyć `MLContext.Transforms.Conversion.MapValueToKey`, który jest otoką <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A> klasy przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="5a510-264">To do that, use the `MLContext.Transforms.Conversion.MapValueToKey`, which is a wrapper for the <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A> transformation class.</span></span>  <span data-ttu-id="5a510-265">`MapValueToKey` Zwraca <xref:Microsoft.ML.Data.EstimatorChain%601> skutecznie się potoku.</span><span class="sxs-lookup"><span data-stu-id="5a510-265">The `MapValueToKey` returns an <xref:Microsoft.ML.Data.EstimatorChain%601> that will effectively be a pipeline.</span></span> <span data-ttu-id="5a510-266">Nazwij to `pipeline` jako następnie dołączy trainer do `EstimatorChain`.</span><span class="sxs-lookup"><span data-stu-id="5a510-266">Name this `pipeline` as you will then append the trainer to the `EstimatorChain`.</span></span> <span data-ttu-id="5a510-267">Dodaj kolejny wiersz kodu:</span><span class="sxs-lookup"><span data-stu-id="5a510-267">Add the next line of code:</span></span>

[!code-csharp[MapValueToKey](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

 <span data-ttu-id="5a510-268">Featurizing różnych wartości kluczowych numeryczne są przypisane różne wartości w każdej z kolumn i jest używany przez algorytmu uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="5a510-268">Featurizing assigns different numeric key values to the different values in each of the columns and is used by the machine learning algorithm.</span></span> <span data-ttu-id="5a510-269">Następnie wywołaj `mlContext.Transforms.Text.FeaturizeText` które featurizes tekst (`Title` i `Description`) kolumny liczbowe wektor dla każdego o nazwie `TitleFeaturized` i `DescriptionFeaturized`.</span><span class="sxs-lookup"><span data-stu-id="5a510-269">Next, call `mlContext.Transforms.Text.FeaturizeText` which featurizes the text (`Title` and `Description`) columns into a numeric vector for each called `TitleFeaturized` and `DescriptionFeaturized`.</span></span> <span data-ttu-id="5a510-270">Dołącz cechowania dla obu kolumn do potoku z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="5a510-270">Append the featurization for both columns to the pipeline with the following code:</span></span>

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

>[!WARNING]
> <span data-ttu-id="5a510-271">Wersja strukturze ML.NET 0.10 została zmieniona kolejność parametrów transformacji.</span><span class="sxs-lookup"><span data-stu-id="5a510-271">ML.NET Version 0.10 has changed the order of the Transform parameters.</span></span> <span data-ttu-id="5a510-272">To spowoduje nie Błąd limitu do czasu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5a510-272">This will not error out until you build.</span></span> <span data-ttu-id="5a510-273">Użyj nazwy parametrów transformacji, jak pokazano w poprzednim fragmencie kodu.</span><span class="sxs-lookup"><span data-stu-id="5a510-273">Use the parameter names for Transforms as illustrated in the previous code snippet.</span></span>

<span data-ttu-id="5a510-274">Ostatnim krokiem w przygotowaniu danych łączy wszystkie kolumny funkcji do **funkcji** przy użyciu kolumny `Concatenate` klasy przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="5a510-274">The last step in data preparation combines all of the feature columns into the **Features** column using the `Concatenate` transformation class.</span></span> <span data-ttu-id="5a510-275">Domyślnie algorytmu uczenia przetwarza tylko funkcje z **funkcji** kolumny.</span><span class="sxs-lookup"><span data-stu-id="5a510-275">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="5a510-276">Dołącz to przekształcenie do potoku z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="5a510-276">Append this transformation to the pipeline with the following code:</span></span>

[!code-csharp[Concatenate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 <span data-ttu-id="5a510-277">Następnie dołącz <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> w pamięci podręcznej widoku danych, dzięki czemu podczas iteracji przez dane wielokrotnie przy użyciu pamięci podręcznej mogą uzyskać lepszą wydajność, zgodnie z poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="5a510-277">Next, append a <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> to cache the DataView so when you iterate over the data multiple times using the cache might get better performance, as with the following code:</span></span>

[!code-csharp[AppendCache](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

> [!WARNING]
> <span data-ttu-id="5a510-278">Użyj AppendCacheCheckpoint dla zestawów danych małe i średnie, aby zmniejszyć czas szkolenia.</span><span class="sxs-lookup"><span data-stu-id="5a510-278">Use AppendCacheCheckpoint for small/medium datasets to lower training time.</span></span> <span data-ttu-id="5a510-279">Nie używaj go (Usuń. AppendCacheCheckpoint()) podczas obsługi bardzo dużych zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="5a510-279">Do NOT use it (remove .AppendCacheCheckpoint()) when handling very large datasets.</span></span>

<span data-ttu-id="5a510-280">Zwróć potoku na końcu `ProcessData` metody.</span><span class="sxs-lookup"><span data-stu-id="5a510-280">Return the pipeline at the end of the `ProcessData` method.</span></span>

[!code-csharp[ReturnPipeline](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

<span data-ttu-id="5a510-281">W tym kroku obsługuje przetwarzania wstępnego cechowania.</span><span class="sxs-lookup"><span data-stu-id="5a510-281">This step handles preprocessing/featurization.</span></span> <span data-ttu-id="5a510-282">Za pomocą dodatkowych składników dostępnych w strukturze ML.NET umożliwiają lepsze wyniki za pomocą modelu.</span><span class="sxs-lookup"><span data-stu-id="5a510-282">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="build-and-train-the-model"></a><span data-ttu-id="5a510-283">Tworzenie i trenowanie modelu</span><span class="sxs-lookup"><span data-stu-id="5a510-283">Build and train the model</span></span>

<span data-ttu-id="5a510-284">Dodaj następujące wywołanie do `BuildAndTrainModel`metodę jako następnego wiersza kodu w `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="5a510-284">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="5a510-285">`BuildAndTrainModel` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="5a510-285">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="5a510-286">Tworzy klasę algorytm szkolenia.</span><span class="sxs-lookup"><span data-stu-id="5a510-286">Creates the training algorithm class.</span></span>
* <span data-ttu-id="5a510-287">Szkolenie modeli modelu.</span><span class="sxs-lookup"><span data-stu-id="5a510-287">Trains the model.</span></span>
* <span data-ttu-id="5a510-288">Prognozuje obszaru, w oparciu o dane szkoleniowe.</span><span class="sxs-lookup"><span data-stu-id="5a510-288">Predicts area based on training data.</span></span>
* <span data-ttu-id="5a510-289">Zapisuje modelu, który ma `.zip` pliku.</span><span class="sxs-lookup"><span data-stu-id="5a510-289">Saves the model to a `.zip` file.</span></span>
* <span data-ttu-id="5a510-290">Zwraca wartość modelu.</span><span class="sxs-lookup"><span data-stu-id="5a510-290">Returns the model.</span></span>

<span data-ttu-id="5a510-291">Tworzenie `BuildAndTrainModel` metody tuż za `Main` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="5a510-291">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

<span data-ttu-id="5a510-292">Należy zauważyć, że dwa parametry są przekazywane do metody BuildAndTrainModel; `IDataView` dla zestawu danych szkoleniowych (`trainingDataView`), a <xref:Microsoft.ML.Data.EstimatorChain%601> dla potoku przetwarzania utworzonych w ProcessData (`pipeline`).</span><span class="sxs-lookup"><span data-stu-id="5a510-292">Notice that two parameters are passed into the BuildAndTrainModel method; an `IDataView` for the training dataset (`trainingDataView`), and a <xref:Microsoft.ML.Data.EstimatorChain%601> for the processing pipeline created in ProcessData (`pipeline`).</span></span>

 <span data-ttu-id="5a510-293">Dodaj następujący kod jako pierwsza linia `BuildAndTrainModel` metody:</span><span class="sxs-lookup"><span data-stu-id="5a510-293">Add the following code as the first line of the `BuildAndTrainModel` method:</span></span>

### <a name="choose-a-learning-algorithm"></a><span data-ttu-id="5a510-294">Wybieranie algorytmu uczenia</span><span class="sxs-lookup"><span data-stu-id="5a510-294">Choose a learning algorithm</span></span>

<span data-ttu-id="5a510-295">Aby dodać Algorytm uczenia, należy wywołać `mlContext.MulticlassClassification.Trainers.StochasticDualCoordinateAscent` metody otoki, która zwraca <xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer> obiektu.</span><span class="sxs-lookup"><span data-stu-id="5a510-295">To add the learning algorithm, call the `mlContext.MulticlassClassification.Trainers.StochasticDualCoordinateAscent` wrapper method which returns a <xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer> object.</span></span>  <span data-ttu-id="5a510-296">`SdcaMultiClassTrainer` Jest dołączany do `pipeline` i akceptuje neural `Title` i `Description` (`Features`) i `Label` parametrów, aby dowiedzieć się więcej na podstawie historycznych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="5a510-296">The `SdcaMultiClassTrainer` is appended to the `pipeline` and accepts the featurized `Title` and `Description` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span> <span data-ttu-id="5a510-297">Należy również mapować etykiety na wartość, aby powrócić do stanu pierwotnego do odczytu.</span><span class="sxs-lookup"><span data-stu-id="5a510-297">You also need to map the label to the value to return to its original readable state.</span></span> <span data-ttu-id="5a510-298">Czy obu tych akcji, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="5a510-298">Do both of those actions with the following code:</span></span>

[!code-csharp[AddTrainer](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

### <a name="train-the-model"></a><span data-ttu-id="5a510-299">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="5a510-299">Train the model</span></span>

<span data-ttu-id="5a510-300">Uczenie modelu, <xref:Microsoft.ML.Data.TransformerChain%601>zgodnie z zestawu danych, który został załadowany i przekształcone.</span><span class="sxs-lookup"><span data-stu-id="5a510-300">You train the model, <xref:Microsoft.ML.Data.TransformerChain%601>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="5a510-301">Po zdefiniowaniu estymatora uczenie modelu przy użyciu <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> przy jednoczesnym zapewnieniu dane szkoleniowe już załadowana.</span><span class="sxs-lookup"><span data-stu-id="5a510-301">Once the estimator has been defined, you train your model using the <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> while providing the already loaded training data.</span></span> <span data-ttu-id="5a510-302">Ta metoda zwraca modelu na potrzeby prognozy.</span><span class="sxs-lookup"><span data-stu-id="5a510-302">This  method returns a model to use for predictions.</span></span> <span data-ttu-id="5a510-303">`trainingPipeline.Fit()` szkolenie modeli potoku i zwraca `Transformer` na podstawie `DataView` przekazany.</span><span class="sxs-lookup"><span data-stu-id="5a510-303">`trainingPipeline.Fit()` trains the pipeline and returns a `Transformer` based on the `DataView` passed in.</span></span> <span data-ttu-id="5a510-304">Eksperyment nie jest wykonywane, dopóki `.Fit()` metoda przebiegów.</span><span class="sxs-lookup"><span data-stu-id="5a510-304">The experiment is not executed until the `.Fit()` method runs.</span></span>

<span data-ttu-id="5a510-305">Dodaj następujący kod do `BuildAndTrainModel` metody:</span><span class="sxs-lookup"><span data-stu-id="5a510-305">Add the following code to the `BuildAndTrainModel` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

<span data-ttu-id="5a510-306">Gdy `model` jest `transformer` który operuje na wiele wierszy danych, na potrzeby prognoz na poszczególne przykłady to typowy scenariusz w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="5a510-306">While the `model` is a `transformer` that operates on many rows of data, a need for predictions on individual examples is a common production scenario.</span></span> <span data-ttu-id="5a510-307"><xref:Microsoft.ML.PredictionEngine%602> Jest otoką, który jest zwracany z `CreatePredictionEngine` metody.</span><span class="sxs-lookup"><span data-stu-id="5a510-307">The <xref:Microsoft.ML.PredictionEngine%602> is a wrapper that is returned from the `CreatePredictionEngine` method.</span></span> <span data-ttu-id="5a510-308">Możemy dodać następujący kod, aby utworzyć `PredictionEngine` w następnym wierszu `BuildAndTrainModel` metody:</span><span class="sxs-lookup"><span data-stu-id="5a510-308">Let's add the following code to create the `PredictionEngine` as the next line in the `BuildAndTrainModel` Method:</span></span>

[!code-csharp[CreatePredictionEngine1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a><span data-ttu-id="5a510-309">Prognozowanie za pomocą uczonego modelu</span><span class="sxs-lookup"><span data-stu-id="5a510-309">Predict with the trained model</span></span>

<span data-ttu-id="5a510-310">Dodaj problem w usłudze GitHub do testowania uczonego modelu prognozowania w `Predict` metody przez utworzenie wystąpienia `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="5a510-310">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[CreateTestIssue1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

<span data-ttu-id="5a510-311">Można go używać, aby przewidzieć `Area` etykiety pojedyncze wystąpienie danych problem.</span><span class="sxs-lookup"><span data-stu-id="5a510-311">You can use that to predict the `Area` label of a single instance of the issue data.</span></span> <span data-ttu-id="5a510-312">Aby uzyskać prognozę, użyj <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> na danych.</span><span class="sxs-lookup"><span data-stu-id="5a510-312">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="5a510-313">Dane wejściowe to ciąg, a model zawiera cechowania.</span><span class="sxs-lookup"><span data-stu-id="5a510-313">The input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="5a510-314">Potok jest zsynchronizowany podczas uczenia i przewidywania.</span><span class="sxs-lookup"><span data-stu-id="5a510-314">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="5a510-315">Nie trzeba napisać kod przetwarzania wstępnego cechowania specjalnie dla prognoz i zajmuje się tego samego interfejsu API i usługi batch jednorazowe prognozy.</span><span class="sxs-lookup"><span data-stu-id="5a510-315">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a><span data-ttu-id="5a510-316">Przy użyciu modelu: przewidywanie wyników</span><span class="sxs-lookup"><span data-stu-id="5a510-316">Using the model: prediction results</span></span>

<span data-ttu-id="5a510-317">Wyświetlanie `GitHubIssue` i odpowiadających im `Area` etykiety prognozowania, aby można było udostępnić wyniki i podejmowanie odpowiednich działań na nich.</span><span class="sxs-lookup"><span data-stu-id="5a510-317">Display `GitHubIssue` and corresponding `Area` label prediction in order to share the results and act on them accordingly.</span></span>  <span data-ttu-id="5a510-318">Tworzenie ekranu wyników za pomocą następujących <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:</span><span class="sxs-lookup"><span data-stu-id="5a510-318">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="5a510-319">Zwraca czy model jest uczony na potrzeby oceny</span><span class="sxs-lookup"><span data-stu-id="5a510-319">Return the model trained to use for evaluation</span></span>

<span data-ttu-id="5a510-320">Zwraca model na końcu `BuildAndTrainModel` metody.</span><span class="sxs-lookup"><span data-stu-id="5a510-320">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a><span data-ttu-id="5a510-321">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="5a510-321">Evaluate the model</span></span>

<span data-ttu-id="5a510-322">Teraz, po utworzeniu i uczony model, należy ocenić ją z innego zestawu danych do zapewniania jakości i sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="5a510-322">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="5a510-323">W `Evaluate` metody, model utworzony w `BuildAndTrainModel` jest przekazywany do obliczenia.</span><span class="sxs-lookup"><span data-stu-id="5a510-323">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="5a510-324">Tworzenie `Evaluate` metody tuż za `BuildAndTrainModel`, jak w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="5a510-324">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate()
{

}
```

<span data-ttu-id="5a510-325">`Evaluate` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="5a510-325">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="5a510-326">Ładuje zestawy danych testowych.</span><span class="sxs-lookup"><span data-stu-id="5a510-326">Loads the test dataset.</span></span>
* <span data-ttu-id="5a510-327">Tworzy ewaluatora wieloklasowej.</span><span class="sxs-lookup"><span data-stu-id="5a510-327">Creates the multiclass evaluator.</span></span>
* <span data-ttu-id="5a510-328">Oblicza model oraz tworzenie metryk.</span><span class="sxs-lookup"><span data-stu-id="5a510-328">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="5a510-329">Przedstawia metryki.</span><span class="sxs-lookup"><span data-stu-id="5a510-329">Displays the metrics.</span></span>

<span data-ttu-id="5a510-330">Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `BuildAndTrainModel` wywołania metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="5a510-330">Add a call to the new method from the `Main` method, right under the `BuildAndTrainModel` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

<span data-ttu-id="5a510-331">Tak jak poprzednio w przypadku zestawu danych szkoleniowych, można łączyć inicjowania, mapowanie i testów ładowania w jednym wierszu kodu zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="5a510-331">As you did previously with the training dataset, you can combine the initialization, mapping, and test dataset loading into one line of code.</span></span> <span data-ttu-id="5a510-332">Możesz ocenić modelu przy użyciu tego zestawu danych w celu sprawdzenia jakości.</span><span class="sxs-lookup"><span data-stu-id="5a510-332">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="5a510-333">Dodaj następujący kod do `Evaluate` metody:</span><span class="sxs-lookup"><span data-stu-id="5a510-333">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

<span data-ttu-id="5a510-334">`MulticlassClassificationContext.Evaluate` Jest otoką <xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A> metody, które oblicza metryk jakości dla modelu przy użyciu określonego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="5a510-334">The `MulticlassClassificationContext.Evaluate` is a wrapper for the <xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A> method that computes the quality metrics for the model using the specified dataset.</span></span> <span data-ttu-id="5a510-335">Zwraca <xref:Microsoft.ML.Data.MultiClassClassifierMetrics> obiekt, który zawiera metryki ogólną obliczone przez ewaluatory klasyfikacji wieloklasowej.</span><span class="sxs-lookup"><span data-stu-id="5a510-335">It returns a <xref:Microsoft.ML.Data.MultiClassClassifierMetrics> object that contains the overall metrics computed by multiclass classification evaluators.</span></span>
<span data-ttu-id="5a510-336">Aby wyświetlić metryki, aby określić jakość modelu, należy je uzyskać pierwszy.</span><span class="sxs-lookup"><span data-stu-id="5a510-336">To display the metrics to determine the quality of the model, you need to get them first.</span></span>
<span data-ttu-id="5a510-337">Zwróć uwagę na `Transform` metoda uczenia maszynowego `_trainedModel` zmiennej globalnej (transformatora) do wprowadzania funkcji i zwracają prognozy.</span><span class="sxs-lookup"><span data-stu-id="5a510-337">Notice the use of the `Transform` method of the machine learning `_trainedModel` global variable (a transformer) to input the features and return predictions.</span></span> <span data-ttu-id="5a510-338">Dodaj następujący kod do `Evaluate` metodę jako następny wiersz:</span><span class="sxs-lookup"><span data-stu-id="5a510-338">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

<span data-ttu-id="5a510-339">Następujące metryki są oceniane pod kątem wieloklasowej klasyfikacji:</span><span class="sxs-lookup"><span data-stu-id="5a510-339">The following metrics are evaluated for multiclass classification:</span></span>

* <span data-ttu-id="5a510-340">Dokładność Micro - każdej pary przykładową klasę przyczynia się jednakowo do metryki dokładności.</span><span class="sxs-lookup"><span data-stu-id="5a510-340">Micro Accuracy - Every sample-class pair contributes equally to the accuracy metric.</span></span>  <span data-ttu-id="5a510-341">Chcesz, aby dokładność Micro być jak zbliżone do wartości 1, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="5a510-341">You want Micro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="5a510-342">Dokładność — makro — każda klasa przyczynia się jednakowo do metryki dokładności.</span><span class="sxs-lookup"><span data-stu-id="5a510-342">Macro Accuracy - Every class contributes equally to the accuracy metric.</span></span> <span data-ttu-id="5a510-343">Moduł klasy są podane weight równe jako większych klas.</span><span class="sxs-lookup"><span data-stu-id="5a510-343">Minority classes are given equal weight as the larger classes.</span></span> <span data-ttu-id="5a510-344">Chcesz, aby dokładność — makro sposób maksymalnie zbliżony 1, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="5a510-344">You want Macro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="5a510-345">Dziennik utraty — zobacz [utraty dziennika](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="5a510-345">Log-loss - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="5a510-346">Ma dziennik utraty sposób maksymalnie zbliżony zero, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="5a510-346">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="5a510-347">Zmniejszenie dziennika utraty — zakresy z [-inf, 100], gdzie 100 to doskonałe prognoz i 0 wskazuje średnią prognozy.</span><span class="sxs-lookup"><span data-stu-id="5a510-347">Log-loss reduction - Ranges from [-inf, 100], where 100 is perfect predictions and 0 indicates mean predictions.</span></span> <span data-ttu-id="5a510-348">Chcesz, aby zmniejszenie dziennika utraty sposób maksymalnie zbliżony zero, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="5a510-348">You want Log-loss reduction to be as close to zero as possible.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="5a510-349">Wyświetlanie metryki dotyczące weryfikacji modelu</span><span class="sxs-lookup"><span data-stu-id="5a510-349">Displaying the metrics for model validation</span></span>

<span data-ttu-id="5a510-350">Użyj poniższego kodu, aby wyświetlić metryki, udostępnianie wyników, a następnie działanie na nich:</span><span class="sxs-lookup"><span data-stu-id="5a510-350">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

### <a name="save-the-trained-and-evaluated-model"></a><span data-ttu-id="5a510-351">Zapisywanie modelu uczonego i ocenione</span><span class="sxs-lookup"><span data-stu-id="5a510-351">Save the trained and evaluated model</span></span>

<span data-ttu-id="5a510-352">W tym momencie masz model typu <xref:Microsoft.ML.Data.TransformerChain%601> , można zintegrować wszystkich istniejących i nowych aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="5a510-352">At this point, you have a model of type <xref:Microsoft.ML.Data.TransformerChain%601> that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="5a510-353">Aby zapisać uczonego modelu w pliku .zip, Dodaj następujący kod do wywoływania `SaveModelAsFile` metody w następnym wierszu `BuildAndTrainModel`:</span><span class="sxs-lookup"><span data-stu-id="5a510-353">To save your trained model to a .zip file, add the following code to call the `SaveModelAsFile` method as the next line in `BuildAndTrainModel`:</span></span>

[!code-csharp[CallSaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallSaveModel)]

## <a name="save-the-model-as-a-zip-file"></a><span data-ttu-id="5a510-354">Zapisz model jako plik .zip</span><span class="sxs-lookup"><span data-stu-id="5a510-354">Save the model as a .zip file</span></span>

<span data-ttu-id="5a510-355">Tworzenie `SaveModelAsFile` metody tuż za `Evaluate` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="5a510-355">Create the `SaveModelAsFile` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="5a510-356">`SaveModelAsFile` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="5a510-356">The `SaveModelAsFile` method executes the following tasks:</span></span>

* <span data-ttu-id="5a510-357">Zapisuje modelu w postaci pliku zip.</span><span class="sxs-lookup"><span data-stu-id="5a510-357">Saves the model as a .zip file.</span></span>

<span data-ttu-id="5a510-358">Następnie utwórz metodę, aby zapisać modelu mogą być używane ponownie i używane w innych aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="5a510-358">Next, create a method to save the model so that it can be reused and consumed in other applications.</span></span> <span data-ttu-id="5a510-359">`ITransformer` Ma <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> metodę, która przyjmuje `_modelPath` globalne pola i <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="5a510-359">The `ITransformer` has a <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> method that takes in the `_modelPath` global field, and a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="5a510-360">Aby zapisać model jako plik zip, należy utworzyć `FileStream` bezpośrednio przed wywołaniem `SaveTo` metody.</span><span class="sxs-lookup"><span data-stu-id="5a510-360">To save the model as a zip file, you'll create the `FileStream` immediately before calling the `SaveTo` method.</span></span> <span data-ttu-id="5a510-361">Dodaj następujący kod do `SaveModelAsFile` metodę jako następny wiersz:</span><span class="sxs-lookup"><span data-stu-id="5a510-361">Add the following code to the `SaveModelAsFile` method as the next line:</span></span>

[!code-csharp[SaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SaveModel)]

<span data-ttu-id="5a510-362">Można również wyświetlić, którym został zapisany plik przy pisaniu komunikatu konsoli, za pomocą `_modelPath`, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="5a510-362">You could also display where the file was written by writing a console message with the `_modelPath`, using the following code:</span></span>

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="deploy-and-predict-with-a-loaded-model"></a><span data-ttu-id="5a510-363">Wdrażanie i przewidywanie załadować modelu</span><span class="sxs-lookup"><span data-stu-id="5a510-363">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="5a510-364">Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `Evaluate` wywołania metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="5a510-364">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

<span data-ttu-id="5a510-365">Tworzenie `PredictIssue` metody tuż za `Evaluate` — metoda (i tuż przed `SaveModelAsFile` metoda), używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="5a510-365">Create the `PredictIssue` method, just after the `Evaluate` method (and just before the `SaveModelAsFile` method), using the following code:</span></span>

```csharp
private static void PredictIssue()
{

}
```

<span data-ttu-id="5a510-366">`PredictIssue` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="5a510-366">The `PredictIssue` method executes the following tasks:</span></span>

* <span data-ttu-id="5a510-367">Tworzy jeden problem danych testowych.</span><span class="sxs-lookup"><span data-stu-id="5a510-367">Creates a single issue of test data.</span></span>
* <span data-ttu-id="5a510-368">Prognozuje obszaru na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="5a510-368">Predicts Area based on test data.</span></span>
* <span data-ttu-id="5a510-369">Łączy w sobie testowanie, danych i prognoz dla raportowania.</span><span class="sxs-lookup"><span data-stu-id="5a510-369">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="5a510-370">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="5a510-370">Displays the predicted results.</span></span>

<span data-ttu-id="5a510-371">Najpierw załadować modelu, które zostały zapisane wcześniej z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="5a510-371">First, load the model that you saved previously with the following code:</span></span>

[!code-csharp[LoadModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadModel)]

<span data-ttu-id="5a510-372">Dodaj problem w usłudze GitHub do testowania uczonego modelu prognozowania w `Predict` metody przez utworzenie wystąpienia `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="5a510-372">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[AddTestIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]
  
<span data-ttu-id="5a510-373">Teraz, gdy model, możesz go używać, aby przewidzieć etykieta GitHub powierzchni pojedyncze wystąpienie danych problem usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="5a510-373">Now that you have a model, you can use that to predict the Area GitHub label of a single instance of the GitHub issue data.</span></span> <span data-ttu-id="5a510-374">Aby uzyskać prognozę, użyj <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> na danych.</span><span class="sxs-lookup"><span data-stu-id="5a510-374">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="5a510-375">Dane wejściowe to ciąg, a model zawiera cechowania.</span><span class="sxs-lookup"><span data-stu-id="5a510-375">The input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="5a510-376">Potok jest zsynchronizowany podczas uczenia i przewidywania.</span><span class="sxs-lookup"><span data-stu-id="5a510-376">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="5a510-377">Nie trzeba napisać kod przetwarzania wstępnego cechowania specjalnie dla prognoz i zajmuje się tego samego interfejsu API i usługi batch jednorazowe prognozy.</span><span class="sxs-lookup"><span data-stu-id="5a510-377">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span> <span data-ttu-id="5a510-378">Dodaj następujący kod do `PredictIssue` metodę dla prognoz:</span><span class="sxs-lookup"><span data-stu-id="5a510-378">Add the following code to the `PredictIssue` method for the predictions:</span></span>

[!code-csharp[PredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a><span data-ttu-id="5a510-379">Przy użyciu załadować modelu do prognozowania</span><span class="sxs-lookup"><span data-stu-id="5a510-379">Using the loaded model for prediction</span></span>

<span data-ttu-id="5a510-380">Wyświetlanie `Area` celu kategoryzowania problem i odpowiednie do nich działanie na nim.</span><span class="sxs-lookup"><span data-stu-id="5a510-380">Display `Area` in order to categorize the issue and act on it accordingly.</span></span> <span data-ttu-id="5a510-381">Tworzenie ekranu wyników za pomocą następujących <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:</span><span class="sxs-lookup"><span data-stu-id="5a510-381">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayResults](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a><span data-ttu-id="5a510-382">Wyniki</span><span class="sxs-lookup"><span data-stu-id="5a510-382">Results</span></span>

<span data-ttu-id="5a510-383">Wyniki powinny być podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="5a510-383">Your results should be similar to the following.</span></span> <span data-ttu-id="5a510-384">Ponieważ przetwarza potoku, wyświetla komunikaty.</span><span class="sxs-lookup"><span data-stu-id="5a510-384">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="5a510-385">Może zostać wyświetlony ostrzeżenia lub komunikaty przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="5a510-385">You may see warnings, or processing messages.</span></span> <span data-ttu-id="5a510-386">Te komunikaty zostały usunięte z następujących wyników dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="5a510-386">These messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="5a510-387">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="5a510-387">Congratulations!</span></span> <span data-ttu-id="5a510-388">Teraz został pomyślnie skompilowany usługi machine learning model do klasyfikowania i prognozowanie etykieta obszar problemu w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="5a510-388">You've now successfully built a machine learning model for classifying and predicting an Area label for a GitHub issue.</span></span> <span data-ttu-id="5a510-389">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="5a510-389">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5a510-390">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="5a510-390">Next steps</span></span>

<span data-ttu-id="5a510-391">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="5a510-391">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="5a510-392">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="5a510-392">Understand the problem</span></span>
> * <span data-ttu-id="5a510-393">Wybieranie algorytmu uczenia maszynowego odpowiednie</span><span class="sxs-lookup"><span data-stu-id="5a510-393">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="5a510-394">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="5a510-394">Prepare your data</span></span>
> * <span data-ttu-id="5a510-395">Przekształcanie danych</span><span class="sxs-lookup"><span data-stu-id="5a510-395">Transform the data</span></span>
> * <span data-ttu-id="5a510-396">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="5a510-396">Train the model</span></span>
> * <span data-ttu-id="5a510-397">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="5a510-397">Evaluate the model</span></span>
> * <span data-ttu-id="5a510-398">Prognozowanie za pomocą uczonego modelu</span><span class="sxs-lookup"><span data-stu-id="5a510-398">Predict with the trained model</span></span>
> * <span data-ttu-id="5a510-399">Wdrażanie i przewidywanie załadować modelu</span><span class="sxs-lookup"><span data-stu-id="5a510-399">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="5a510-400">Przejdź do następnego samouczka, aby dowiedzieć się więcej</span><span class="sxs-lookup"><span data-stu-id="5a510-400">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="5a510-401">Taxi Fare Predictor</span><span class="sxs-lookup"><span data-stu-id="5a510-401">Taxi Fare Predictor</span></span>](taxi-fare.md)
