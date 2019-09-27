---
title: Jak korzystać z interfejsu API zautomatyzowanej ML.NET ML
description: Interfejs API zautomatyzowanej sieci ML.NET automatyzuje proces tworzenia modelu i generuje model gotowy do wdrożenia. Informacje na temat opcji, których można użyć do konfigurowania automatycznych zadań uczenia maszynowego.
ms.date: 04/24/2019
ms.custom: mvc,how-to
ms.openlocfilehash: a7057337fb6ff19a1e402d7bf74a766b246ea3c1
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332718"
---
# <a name="how-to-use-the-mlnet-automated-machine-learning-api"></a><span data-ttu-id="f3a3b-104">Jak korzystać z interfejsu API automatycznego uczenia maszynowego ML.NET</span><span class="sxs-lookup"><span data-stu-id="f3a3b-104">How to use the ML.NET automated machine learning API</span></span>

<span data-ttu-id="f3a3b-105">Automatyczne Uczenie maszynowe (AutoML) automatyzuje proces stosowania uczenia maszynowego do danych.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-105">Automated machine learning (AutoML) automates the process of applying machine learning to data.</span></span> <span data-ttu-id="f3a3b-106">Mając zestaw danych, można uruchomić **eksperyment** AutoML, aby wykonać iterację różnych danych featurizations, algorytmów uczenia maszynowego i parametrów do wybierania najlepszego modelu.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-106">Given a dataset, you can run an AutoML **experiment** to iterate over different data featurizations, machine learning algorithms, and hyperparameters to select the best model.</span></span>

> [!NOTE]
> <span data-ttu-id="f3a3b-107">Ten temat odnosi się do zautomatyzowanego interfejsu API uczenia maszynowego dla usługi ML.NET, który jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-107">This topic refers to the automated machine learning API for ML.NET, which is currently in preview.</span></span> <span data-ttu-id="f3a3b-108">Materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-108">Material may be subject to change.</span></span>

## <a name="load-data"></a><span data-ttu-id="f3a3b-109">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="f3a3b-109">Load data</span></span>

<span data-ttu-id="f3a3b-110">Automatyczne Uczenie maszynowe obsługuje ładowanie zestawu danych do [IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="f3a3b-110">Automated machine learning supports loading a dataset into an [IDataView](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="f3a3b-111">Dane mogą mieć postać plików z wartościami rozdzielanymi tabulatorami (TSV) i plików z wartościami rozdzielanymi przecinkami (CSV).</span><span class="sxs-lookup"><span data-stu-id="f3a3b-111">Data can be in the form of tab-separated value (TSV) files and comma separated value (CSV) files.</span></span>

<span data-ttu-id="f3a3b-112">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f3a3b-112">Example:</span></span>

```csharp
using Microsoft.ML;
using Microsoft.ML.AutoML;
    // ...
    MLContext mlContext = new MLContext();
    IDataView trainDataView = mlContext.Data.LoadFromTextFile<SentimentIssue>("my-data-file.csv", hasHeader: true);
```

## <a name="select-the-machine-learning-task-type"></a><span data-ttu-id="f3a3b-113">Wybierz typ zadania uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="f3a3b-113">Select the machine learning task type</span></span>
<span data-ttu-id="f3a3b-114">Przed utworzeniem eksperymentu należy określić rodzaj problemu z uczeniem maszynowym, który ma zostać rozwiązany.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-114">Before creating an experiment, determine the kind of machine learning problem you want to solve.</span></span> <span data-ttu-id="f3a3b-115">Automatyczne Uczenie maszynowe obsługuje następujące zadania w ML:</span><span class="sxs-lookup"><span data-stu-id="f3a3b-115">Automated machine learning supports the following ML tasks:</span></span>

* <span data-ttu-id="f3a3b-116">Klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="f3a3b-116">Binary Classification</span></span>
* <span data-ttu-id="f3a3b-117">Klasyfikacja wieloklasowa</span><span class="sxs-lookup"><span data-stu-id="f3a3b-117">Multiclass Classification</span></span>
* <span data-ttu-id="f3a3b-118">Regresji</span><span class="sxs-lookup"><span data-stu-id="f3a3b-118">Regression</span></span>

## <a name="create-experiment-settings"></a><span data-ttu-id="f3a3b-119">Utwórz ustawienia eksperymentu</span><span class="sxs-lookup"><span data-stu-id="f3a3b-119">Create experiment settings</span></span>

<span data-ttu-id="f3a3b-120">Utwórz ustawienia eksperymentu dla typu zadania o określonej ML:</span><span class="sxs-lookup"><span data-stu-id="f3a3b-120">Create experiment settings for the determined ML task type:</span></span>

* <span data-ttu-id="f3a3b-121">Klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="f3a3b-121">Binary Classification</span></span>

  ```csharp
  var experimentSettings = new BinaryExperimentSettings();
  ```

* <span data-ttu-id="f3a3b-122">Klasyfikacja wieloklasowa</span><span class="sxs-lookup"><span data-stu-id="f3a3b-122">Multiclass Classification</span></span>

  ```csharp
  var experimentSettings = new MulticlassExperimentSettings();
  ```

* <span data-ttu-id="f3a3b-123">Regresji</span><span class="sxs-lookup"><span data-stu-id="f3a3b-123">Regression</span></span>

  ```csharp
  var experimentSettings = new RegressionExperimentSettings();
  ```

## <a name="configure-experiment-settings"></a><span data-ttu-id="f3a3b-124">Konfigurowanie ustawień eksperymentu</span><span class="sxs-lookup"><span data-stu-id="f3a3b-124">Configure experiment settings</span></span>

<span data-ttu-id="f3a3b-125">Eksperymenty są wysoce konfigurowalne.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-125">Experiments are highly configurable.</span></span> <span data-ttu-id="f3a3b-126">Zobacz dokumentację [interfejsu API AutoML](https://docs.microsoft.com/dotnet/api/?view=automl-dotnet) , aby uzyskać pełną listę ustawień konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-126">See the [AutoML API docs](https://docs.microsoft.com/dotnet/api/?view=automl-dotnet) for a full list of configuration settings.</span></span>

<span data-ttu-id="f3a3b-127">Oto niektóre przykłady:</span><span class="sxs-lookup"><span data-stu-id="f3a3b-127">Some examples include:</span></span>

1. <span data-ttu-id="f3a3b-128">Określ maksymalny czas działania eksperymentu.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-128">Specify the maximum time that the experiment is allowed to run.</span></span>

    ```csharp
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    ```

1. <span data-ttu-id="f3a3b-129">Użyj tokenu anulowania, aby anulować eksperyment przed zaplanowaniem jego zakończenia.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-129">Use a cancellation token to cancel the experiment before it is scheduled to finish.</span></span>

    ```csharp
    experimentSettings.CancellationToken = cts.Token;

    // Cancel experiment after the user presses any key
    CancelExperimentAfterAnyKeyPress(cts);
    ```

1. <span data-ttu-id="f3a3b-130">Określ inną metrykę optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-130">Specify a different optimizing metric.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.OptimizingMetric = RegressionMetric.MeanSquaredError;
    ```

1. <span data-ttu-id="f3a3b-131">`CacheDirectory` Ustawienie to wskaźnik do katalogu, w którym wszystkie modele przeszkolone podczas zadania AutoML zostaną zapisane.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-131">The `CacheDirectory` setting is a pointer to a directory where all models trained during the AutoML task will be saved.</span></span> <span data-ttu-id="f3a3b-132">Jeśli `CacheDirectory` jest ustawiona na wartość null, modele będą przechowywane w pamięci zamiast zapisywać na dysku.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-132">If `CacheDirectory` is set to null, models will be kept in memory instead of written to disk.</span></span>
 
    ```csharp
    experimentSettings.CacheDirectory = null;
    ```

1. <span data-ttu-id="f3a3b-133">Poinstruuj zautomatyzowany ML, aby nie używać niektórych instruktorów.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-133">Instruct automated ML not to use certain trainers.</span></span>

    <span data-ttu-id="f3a3b-134">Domyślna lista instruktorów do optymalizacji są zbadane według poszczególnych zadań.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-134">A default list of trainers to optimize are explored per task.</span></span> <span data-ttu-id="f3a3b-135">Tę listę można modyfikować dla każdego eksperymentu.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-135">This list can be modified for each experiment.</span></span> <span data-ttu-id="f3a3b-136">Na przykład, instruktorzy, którzy działają wolno w zestawie danych, można usunąć z listy.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-136">For instance, trainers that run slowly on your dataset can be removed from the list.</span></span> <span data-ttu-id="f3a3b-137">Aby zoptymalizować na jednym konkretnym wywołaniu `experimentSettings.Trainers.Clear()`Trainer, Dodaj Trainer, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-137">To optimize on one specific trainer call `experimentSettings.Trainers.Clear()`, then add the trainer that you want to use.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.Trainers.Remove(RegressionTrainer.LbfgsPoissonRegression);
    experimentSettings.Trainers.Remove(RegressionTrainer.OnlineGradientDescent);
    ```

<span data-ttu-id="f3a3b-138">Listę obsługiwanych zadań instruktorów na ML można znaleźć w odpowiadającym jej poniższym łączu:</span><span class="sxs-lookup"><span data-stu-id="f3a3b-138">The list of supported trainers per ML task can be found at the corresponding link below:</span></span>

* [<span data-ttu-id="f3a3b-139">Obsługiwane algorytmy klasyfikacji binarnej</span><span class="sxs-lookup"><span data-stu-id="f3a3b-139">Supported Binary Classification Algorithms</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationTrainer)
* [<span data-ttu-id="f3a3b-140">Obsługiwane algorytmy klasyfikacji wieloklasowej</span><span class="sxs-lookup"><span data-stu-id="f3a3b-140">Supported Multiclass Classification Algorithms</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationTrainer)
* [<span data-ttu-id="f3a3b-141">Obsługiwane algorytmy regresji</span><span class="sxs-lookup"><span data-stu-id="f3a3b-141">Supported Regression Algorithms</span></span>](xref:Microsoft.ML.AutoML.RegressionTrainer)

## <a name="optimizing-metric"></a><span data-ttu-id="f3a3b-142">Optymalizowanie metryki</span><span class="sxs-lookup"><span data-stu-id="f3a3b-142">Optimizing metric</span></span>

<span data-ttu-id="f3a3b-143">Metryka optymalizacji, jak pokazano w powyższym przykładzie, określa metrykę do zoptymalizowania podczas uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-143">The optimizing metric, as shown in the example above, determines the metric to be optimized during model training.</span></span> <span data-ttu-id="f3a3b-144">Metryka optymalizacji, którą można wybrać, zależy od wybranego typu zadania.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-144">The optimizing metric you can select is determined by the task type you choose.</span></span> <span data-ttu-id="f3a3b-145">Poniżej znajduje się lista dostępnych metryk.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-145">Below is a list of available metrics.</span></span>

|[<span data-ttu-id="f3a3b-146">Klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="f3a3b-146">Binary Classification</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationMetric) | [<span data-ttu-id="f3a3b-147">Klasyfikacja wieloklasowa</span><span class="sxs-lookup"><span data-stu-id="f3a3b-147">Multiclass Classification</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric) |[<span data-ttu-id="f3a3b-148">Regression</span><span class="sxs-lookup"><span data-stu-id="f3a3b-148">Regression</span></span>](xref:Microsoft.ML.AutoML.RegressionMetric)
|-- |-- |--
|<span data-ttu-id="f3a3b-149">odpowiedni</span><span class="sxs-lookup"><span data-stu-id="f3a3b-149">Accuracy</span></span>| <span data-ttu-id="f3a3b-150">LogLoss</span><span class="sxs-lookup"><span data-stu-id="f3a3b-150">LogLoss</span></span> | <span data-ttu-id="f3a3b-151">RSquared</span><span class="sxs-lookup"><span data-stu-id="f3a3b-151">RSquared</span></span>
|<span data-ttu-id="f3a3b-152">AreaUnderPrecisionRecallCurve</span><span class="sxs-lookup"><span data-stu-id="f3a3b-152">AreaUnderPrecisionRecallCurve</span></span> | <span data-ttu-id="f3a3b-153">LogLossReduction</span><span class="sxs-lookup"><span data-stu-id="f3a3b-153">LogLossReduction</span></span> | <span data-ttu-id="f3a3b-154">MeanAbsoluteError</span><span class="sxs-lookup"><span data-stu-id="f3a3b-154">MeanAbsoluteError</span></span>
|<span data-ttu-id="f3a3b-155">AreaUnderRocCurve</span><span class="sxs-lookup"><span data-stu-id="f3a3b-155">AreaUnderRocCurve</span></span> | <span data-ttu-id="f3a3b-156">MacroAccuracy</span><span class="sxs-lookup"><span data-stu-id="f3a3b-156">MacroAccuracy</span></span> | <span data-ttu-id="f3a3b-157">MeanSquaredError</span><span class="sxs-lookup"><span data-stu-id="f3a3b-157">MeanSquaredError</span></span>
|<span data-ttu-id="f3a3b-158">F1Score</span><span class="sxs-lookup"><span data-stu-id="f3a3b-158">F1Score</span></span> | <span data-ttu-id="f3a3b-159">Mikrodokładność</span><span class="sxs-lookup"><span data-stu-id="f3a3b-159">MicroAccuracy</span></span> | <span data-ttu-id="f3a3b-160">RootMeanSquaredError</span><span class="sxs-lookup"><span data-stu-id="f3a3b-160">RootMeanSquaredError</span></span>
|<span data-ttu-id="f3a3b-161">NegativePrecision</span><span class="sxs-lookup"><span data-stu-id="f3a3b-161">NegativePrecision</span></span> | <span data-ttu-id="f3a3b-162">TopKAccuracy</span><span class="sxs-lookup"><span data-stu-id="f3a3b-162">TopKAccuracy</span></span>
|<span data-ttu-id="f3a3b-163">NegativeRecall</span><span class="sxs-lookup"><span data-stu-id="f3a3b-163">NegativeRecall</span></span> |
|<span data-ttu-id="f3a3b-164">PositivePrecision</span><span class="sxs-lookup"><span data-stu-id="f3a3b-164">PositivePrecision</span></span>
|<span data-ttu-id="f3a3b-165">PositiveRecall</span><span class="sxs-lookup"><span data-stu-id="f3a3b-165">PositiveRecall</span></span>

## <a name="data-pre-processing-and-featurization"></a><span data-ttu-id="f3a3b-166">Wstępne przetwarzanie danych i cechowania</span><span class="sxs-lookup"><span data-stu-id="f3a3b-166">Data pre-processing and featurization</span></span>

> [!NOTE]
> <span data-ttu-id="f3a3b-167">W kolumnie funkcji obsługiwane są tylko typy [`Boolean`](https://docs.microsoft.com/en-us/dotnet/api/system.boolean), [`Single`](https://docs.microsoft.com/en-us/dotnet/api/system.single)i [`String`](https://docs.microsoft.com/en-us/dotnet/api/system.string).</span><span class="sxs-lookup"><span data-stu-id="f3a3b-167">The feature column only supported types of [`Boolean`](https://docs.microsoft.com/en-us/dotnet/api/system.boolean), [`Single`](https://docs.microsoft.com/en-us/dotnet/api/system.single), and [`String`](https://docs.microsoft.com/en-us/dotnet/api/system.string).</span></span>

<span data-ttu-id="f3a3b-168">Przetwarzanie wstępne danych odbywa się domyślnie, a następujące kroki są wykonywane automatycznie:</span><span class="sxs-lookup"><span data-stu-id="f3a3b-168">Data pre-processing happens by default and the following steps are performed automatically for you:</span></span>

1. <span data-ttu-id="f3a3b-169">Funkcje upuszczania bez użytecznych informacji</span><span class="sxs-lookup"><span data-stu-id="f3a3b-169">Drop features with no useful information</span></span>

    <span data-ttu-id="f3a3b-170">Usuwanie funkcji żadnych użytecznych informacji z zestawów szkolenia i sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-170">Drop features with no useful information from training and validation sets.</span></span> <span data-ttu-id="f3a3b-171">Obejmują one funkcje wszystkich wartości Brak, tę samą wartość we wszystkich wierszach lub bardzo dużej kardynalności (np. skróty, lub identyfikatory GUID).</span><span class="sxs-lookup"><span data-stu-id="f3a3b-171">These include features with all values missing, same value across all rows or with extremely high cardinality (e.g., hashes, IDs or GUIDs).</span></span>

1. <span data-ttu-id="f3a3b-172">Brak wskazania wartości i nie należy ich przypisywaniu</span><span class="sxs-lookup"><span data-stu-id="f3a3b-172">Missing value indication and imputation</span></span>

    <span data-ttu-id="f3a3b-173">Wypełnij brakujące komórki wartości wartością domyślną dla typu danych.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-173">Fill missing value cells with the default value for the datatype.</span></span> <span data-ttu-id="f3a3b-174">Dołącz funkcje wskaźnika z taką samą liczbą gniazd jak w przypadku kolumny wejściowej.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-174">Append indicator features with the same number of slots as the input column.</span></span> <span data-ttu-id="f3a3b-175">Wartość w funkcjach dołączanych wskaźników jest `1` w przypadku braku wartości w kolumnie wejściowej i `0` w przeciwnym razie.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-175">The value in the appended indicator features is `1` if the value in the input column is missing and `0` otherwise.</span></span>

1. <span data-ttu-id="f3a3b-176">Generuj dodatkowe funkcje</span><span class="sxs-lookup"><span data-stu-id="f3a3b-176">Generate additional features</span></span>
    
    <span data-ttu-id="f3a3b-177">Dla funkcji tekstowych: Funkcje zbioru słów korzystające z unigrams i Tri-Character-Grams.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-177">For text features: Bag-of-word features using unigrams and tri-character-grams.</span></span>
    
    <span data-ttu-id="f3a3b-178">Dla funkcji kategorii: Jednostronicowe kodowanie dla funkcji niskiej kardynalności i jednostronicowe kodowanie dla funkcji kategorii wysoka Kardynalność.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-178">For categorical features: One-hot encoding for low cardinality features, and one-hot-hash encoding for high cardinality categorical features.</span></span>

1. <span data-ttu-id="f3a3b-179">Przekształcenia i kodowania</span><span class="sxs-lookup"><span data-stu-id="f3a3b-179">Transformations and encodings</span></span>

    <span data-ttu-id="f3a3b-180">Funkcje tekstowe z bardzo kilkoma unikatowymi wartościami przekształconymi na funkcje kategorii.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-180">Text features with very few unique values transformed into categorical features.</span></span> <span data-ttu-id="f3a3b-181">W zależności od kardynalności funkcji kategorii należy wykonać jedno-gorąca lub jednostronicowe kodowanie skrótu.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-181">Depending on cardinality of categorical features, perform one-hot encoding or one-hot hash encoding.</span></span>

## <a name="exit-criteria"></a><span data-ttu-id="f3a3b-182">Kryteria wyjścia</span><span class="sxs-lookup"><span data-stu-id="f3a3b-182">Exit criteria</span></span>

<span data-ttu-id="f3a3b-183">Zdefiniuj kryteria, aby ukończyć zadanie:</span><span class="sxs-lookup"><span data-stu-id="f3a3b-183">Define the criteria to complete your task:</span></span>

1. <span data-ttu-id="f3a3b-184">Zakończ po upływie długiego czasu `MaxExperimentTimeInSeconds` w ustawieniach eksperymentu możesz określić, jak długo w sekundach ma być nadal wykonywane zadanie.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-184">Exit after a length of time - Using `MaxExperimentTimeInSeconds` in your experiment settings you can define how long in seconds that an task should continue to run.</span></span>

1. <span data-ttu-id="f3a3b-185">Wyjście z tokenu anulowania — można użyć tokenu anulowania, który umożliwia anulowanie zadania przed jego zaplanowaniem.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-185">Exit on a cancellation token -  You can use a cancellation token that lets you cancel the task before it is scheduled to finish.</span></span>

    ```csharp
    var cts = new CancellationTokenSource();
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    experimentSettings.CancellationToken = cts.Token;
    ```

## <a name="create-an-experiment"></a><span data-ttu-id="f3a3b-186">Tworzenie eksperymentu</span><span class="sxs-lookup"><span data-stu-id="f3a3b-186">Create an experiment</span></span>

<span data-ttu-id="f3a3b-187">Po skonfigurowaniu ustawień eksperymentu możesz przystąpić do tworzenia eksperymentu.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-187">Once you have configured the experiment settings, you are ready to create the experiment.</span></span>

```csharp
RegressionExperiment experiment = mlContext.Auto().CreateRegressionExperiment(experimentSettings);
```

## <a name="run-the-experiment"></a><span data-ttu-id="f3a3b-188">Uruchamianie eksperymentu</span><span class="sxs-lookup"><span data-stu-id="f3a3b-188">Run the experiment</span></span>

<span data-ttu-id="f3a3b-189">Uruchamianie eksperymentu wyzwala wstępne przetwarzanie danych, wybór algorytmu uczenia i dostrajanie parametrów.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-189">Running the experiment triggers data pre-processing, learning algorithm selection, and hyperparameter tuning.</span></span> <span data-ttu-id="f3a3b-190">AutoML będzie nadal generować kombinacje algorytmów cechowania, uczenia i parametrów do momentu `MaxExperimentTimeInSeconds` osiągnięcia lub eksperymentu.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-190">AutoML will continue to generate combinations of featurization, learning algorithms, and hyperparameters until the `MaxExperimentTimeInSeconds` is reached or the experiment is terminated.</span></span>

```csharp
ExperimentResult<RegressionMetrics> experimentResult = experiment
    .Execute(trainingDataView, LabelColumnName, progressHandler: progressHandler);
```

<span data-ttu-id="f3a3b-191">Zapoznaj się z `Execute()` innymi przeciążeniami, jeśli chcesz przekazać dane sprawdzania poprawności, informacje o kolumnie wskazujące cel kolumny lub prefeaturizers.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-191">Explore other overloads for `Execute()` if you want to pass in validation data, column information indicating the column purpose, or prefeaturizers.</span></span>

## <a name="training-modes"></a><span data-ttu-id="f3a3b-192">Tryby szkoleniowe</span><span class="sxs-lookup"><span data-stu-id="f3a3b-192">Training modes</span></span>

### <a name="training-dataset"></a><span data-ttu-id="f3a3b-193">Zestaw danych szkoleniowych</span><span class="sxs-lookup"><span data-stu-id="f3a3b-193">Training dataset</span></span>

<span data-ttu-id="f3a3b-194">AutoML zapewnia przeciążoną metodę wykonywania eksperymentu, która umożliwia dostarczanie danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-194">AutoML provides an overloaded experiment execute method which allows you to provide training data.</span></span> <span data-ttu-id="f3a3b-195">Wewnętrznie, zautomatyzowanej ML dzieli dane na pociąg-Validate Splits.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-195">Internally, automated ML divides the data into train-validate splits.</span></span>

```csharp
experiment.Execute(trainDataView);   
```

### <a name="custom-validation-dataset"></a><span data-ttu-id="f3a3b-196">Zestaw niestandardowego sprawdzania poprawności danych</span><span class="sxs-lookup"><span data-stu-id="f3a3b-196">Custom validation dataset</span></span>

<span data-ttu-id="f3a3b-197">Użyj niestandardowego zestawu danych walidacji, jeśli podział losowy nie jest akceptowalny, jak zwykle jest to przypadek z danymi szeregów czasowych.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-197">Use custom validation dataset if random split is not acceptable, as is usually the case with time series data.</span></span> <span data-ttu-id="f3a3b-198">Można określić własnego zestawu danych walidacji.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-198">You can specify your own validation dataset.</span></span> <span data-ttu-id="f3a3b-199">Model zostanie oceniony względem określonego zestawu danych walidacji, a nie do co najmniej jednego losowo ustawionego typu danych.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-199">The model will be evaluated against the validation dataset specified instead of one or more random datasets.</span></span>

```csharp
experiment.Execute(trainDataView, validationDataView);   
```

## <a name="explore-model-metrics"></a><span data-ttu-id="f3a3b-200">Eksplorowanie metryk modelu</span><span class="sxs-lookup"><span data-stu-id="f3a3b-200">Explore model metrics</span></span>

<span data-ttu-id="f3a3b-201">Po każdej iteracji eksperymentu ML są przechowywane metryki dotyczące tego zadania.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-201">After each iteration of an ML experiment, metrics relating to that task are stored.</span></span>

<span data-ttu-id="f3a3b-202">Można na przykład uzyskać dostęp do metryk walidacji z najlepszego przebiegu:</span><span class="sxs-lookup"><span data-stu-id="f3a3b-202">For example, we can access validation metrics from the best run:</span></span>

```csharp
RegressionMetrics metrics = experimentResult.BestRun.ValidationMetrics;
Console.WriteLine($"R-Squared: {metrics.RSquared:0.##}");
Console.WriteLine($"Root Mean Squared Error: {metrics.RootMeanSquaredError:0.##}");
```

<span data-ttu-id="f3a3b-203">Poniżej znajdują się wszystkie dostępne metryki na ML zadania:</span><span class="sxs-lookup"><span data-stu-id="f3a3b-203">The following are all the available metrics per ML task:</span></span>

* [<span data-ttu-id="f3a3b-204">Metryki klasyfikacji binarnej</span><span class="sxs-lookup"><span data-stu-id="f3a3b-204">Binary classification metrics</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationMetric)
* [<span data-ttu-id="f3a3b-205">Metryki klasyfikacji wieloklasowej</span><span class="sxs-lookup"><span data-stu-id="f3a3b-205">Multiclass classification metrics</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric)
* [<span data-ttu-id="f3a3b-206">Metryki regresji</span><span class="sxs-lookup"><span data-stu-id="f3a3b-206">Regression metrics</span></span>](xref:Microsoft.ML.AutoML.RegressionMetric)

## <a name="see-also"></a><span data-ttu-id="f3a3b-207">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3a3b-207">See also</span></span>

<span data-ttu-id="f3a3b-208">Aby uzyskać pełne przykłady kodu i więcej informacji, odwiedź repozytorium [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="f3a3b-208">For full code samples and more visit the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) GitHub repository.</span></span>
