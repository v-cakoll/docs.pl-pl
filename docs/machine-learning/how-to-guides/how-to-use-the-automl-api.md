---
title: Jak korzystać z ML.NET zautomatyzowanego interfejsu API ML
description: ML.NET zautomatyzowany interfejs API ml automatyzuje proces tworzenia modelu i generuje model gotowy do wdrożenia. Poznaj opcje, których można użyć do konfigurowania zadań automatycznego uczenia maszynowego.
ms.date: 12/18/2019
ms.custom: mvc,how-to
ms.openlocfilehash: b322c484282d025033d747d2093f7b5b4d216fde
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75636565"
---
# <a name="how-to-use-the-mlnet-automated-machine-learning-api"></a><span data-ttu-id="80d00-104">Jak korzystać z ML.NET automatycznego interfejsu API uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="80d00-104">How to use the ML.NET automated machine learning API</span></span>

<span data-ttu-id="80d00-105">Automatyczne uczenie maszynowe (AutoML) automatyzuje proces stosowania uczenia maszynowego do danych.</span><span class="sxs-lookup"><span data-stu-id="80d00-105">Automated machine learning (AutoML) automates the process of applying machine learning to data.</span></span> <span data-ttu-id="80d00-106">Biorąc pod uwagę zestaw danych, można uruchomić **eksperyment** AutoML, aby iterate nad różnymi featurizations danych, algorytmów uczenia maszynowego i hiperparametrów, aby wybrać najlepszy model.</span><span class="sxs-lookup"><span data-stu-id="80d00-106">Given a dataset, you can run an AutoML **experiment** to iterate over different data featurizations, machine learning algorithms, and hyperparameters to select the best model.</span></span>

> [!NOTE]
> <span data-ttu-id="80d00-107">Ten temat odnosi się do interfejsu API automatycznego uczenia maszynowego dla ML.NET, który jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="80d00-107">This topic refers to the automated machine learning API for ML.NET, which is currently in preview.</span></span> <span data-ttu-id="80d00-108">Materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="80d00-108">Material may be subject to change.</span></span>

## <a name="load-data"></a><span data-ttu-id="80d00-109">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="80d00-109">Load data</span></span>

<span data-ttu-id="80d00-110">Automatyczne uczenie maszynowe obsługuje ładowanie zestawu danych do [widoku IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="80d00-110">Automated machine learning supports loading a dataset into an [IDataView](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="80d00-111">Dane mogą być w postaci plików wartości rozdzielonych kartami (TSV) i plików wartości oddzielonych przecinkami (CSV).</span><span class="sxs-lookup"><span data-stu-id="80d00-111">Data can be in the form of tab-separated value (TSV) files and comma separated value (CSV) files.</span></span>

<span data-ttu-id="80d00-112">Przykład:</span><span class="sxs-lookup"><span data-stu-id="80d00-112">Example:</span></span>

```csharp
using Microsoft.ML;
using Microsoft.ML.AutoML;
    // ...
    MLContext mlContext = new MLContext();
    IDataView trainDataView = mlContext.Data.LoadFromTextFile<SentimentIssue>("my-data-file.csv", hasHeader: true);
```

## <a name="select-the-machine-learning-task-type"></a><span data-ttu-id="80d00-113">Wybierz typ zadania uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="80d00-113">Select the machine learning task type</span></span>

<span data-ttu-id="80d00-114">Przed utworzeniem eksperymentu należy określić rodzaj problemu z uczeniem maszynowym, który chcesz rozwiązać.</span><span class="sxs-lookup"><span data-stu-id="80d00-114">Before creating an experiment, determine the kind of machine learning problem you want to solve.</span></span> <span data-ttu-id="80d00-115">Automatyczne uczenie maszynowe obsługuje następujące zadania w celu połączenia maszynowego:</span><span class="sxs-lookup"><span data-stu-id="80d00-115">Automated machine learning supports the following ML tasks:</span></span>

* <span data-ttu-id="80d00-116">Klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="80d00-116">Binary Classification</span></span>
* <span data-ttu-id="80d00-117">Klasyfikacja wieloklasowa</span><span class="sxs-lookup"><span data-stu-id="80d00-117">Multiclass Classification</span></span>
* <span data-ttu-id="80d00-118">Regresja</span><span class="sxs-lookup"><span data-stu-id="80d00-118">Regression</span></span>
* <span data-ttu-id="80d00-119">Zalecenie</span><span class="sxs-lookup"><span data-stu-id="80d00-119">Recommendation</span></span>

## <a name="create-experiment-settings"></a><span data-ttu-id="80d00-120">Tworzenie ustawień eksperymentu</span><span class="sxs-lookup"><span data-stu-id="80d00-120">Create experiment settings</span></span>

<span data-ttu-id="80d00-121">Utwórz ustawienia eksperymentu dla określonego typu zadania ML:</span><span class="sxs-lookup"><span data-stu-id="80d00-121">Create experiment settings for the determined ML task type:</span></span>

* <span data-ttu-id="80d00-122">Klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="80d00-122">Binary Classification</span></span>

  ```csharp
  var experimentSettings = new BinaryExperimentSettings();
  ```

* <span data-ttu-id="80d00-123">Klasyfikacja wieloklasowa</span><span class="sxs-lookup"><span data-stu-id="80d00-123">Multiclass Classification</span></span>

  ```csharp
  var experimentSettings = new MulticlassExperimentSettings();
  ```

* <span data-ttu-id="80d00-124">Regresja</span><span class="sxs-lookup"><span data-stu-id="80d00-124">Regression</span></span>

  ```csharp
  var experimentSettings = new RegressionExperimentSettings();
  ```

* <span data-ttu-id="80d00-125">Zalecenie</span><span class="sxs-lookup"><span data-stu-id="80d00-125">Recommendation</span></span>

  ```csharp
  var experimentSettings = new RecommendationExperimentSettings();
  ```

## <a name="configure-experiment-settings"></a><span data-ttu-id="80d00-126">Konfigurowanie ustawień eksperymentu</span><span class="sxs-lookup"><span data-stu-id="80d00-126">Configure experiment settings</span></span>

<span data-ttu-id="80d00-127">Eksperymenty są wysoce konfigurowalne.</span><span class="sxs-lookup"><span data-stu-id="80d00-127">Experiments are highly configurable.</span></span> <span data-ttu-id="80d00-128">Zobacz [dokumenty interfejsu API AutoML,](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl?view=ml-dotnet-preview) aby uzyskać pełną listę ustawień konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="80d00-128">See the [AutoML API docs](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl?view=ml-dotnet-preview) for a full list of configuration settings.</span></span>

<span data-ttu-id="80d00-129">Oto niektóre przykłady:</span><span class="sxs-lookup"><span data-stu-id="80d00-129">Some examples include:</span></span>

1. <span data-ttu-id="80d00-130">Określ maksymalny czas, przez jaki eksperyment może zostać uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="80d00-130">Specify the maximum time that the experiment is allowed to run.</span></span>

    ```csharp
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    ```

1. <span data-ttu-id="80d00-131">Użyj tokenu anulowania, aby anulować eksperyment przed jego zakończeniem.</span><span class="sxs-lookup"><span data-stu-id="80d00-131">Use a cancellation token to cancel the experiment before it is scheduled to finish.</span></span>

    ```csharp
    experimentSettings.CancellationToken = cts.Token;

    // Cancel experiment after the user presses any key
    CancelExperimentAfterAnyKeyPress(cts);
    ```

1. <span data-ttu-id="80d00-132">Określ inną metrykę optymalizującą.</span><span class="sxs-lookup"><span data-stu-id="80d00-132">Specify a different optimizing metric.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.OptimizingMetric = RegressionMetric.MeanSquaredError;
    ```

1. <span data-ttu-id="80d00-133">Ustawienie `CacheDirectory` jest wskaźnikiem do katalogu, w którym zostaną zapisane wszystkie modele przeszkolone podczas wykonywania zadania AutoML.</span><span class="sxs-lookup"><span data-stu-id="80d00-133">The `CacheDirectory` setting is a pointer to a directory where all models trained during the AutoML task will be saved.</span></span> <span data-ttu-id="80d00-134">Jeśli `CacheDirectory` jest ustawiona na null, modele będą przechowywane w pamięci, a nie zapisywane na dysku.</span><span class="sxs-lookup"><span data-stu-id="80d00-134">If `CacheDirectory` is set to null, models will be kept in memory instead of written to disk.</span></span>

    ```csharp
    experimentSettings.CacheDirectory = null;
    ```

1. <span data-ttu-id="80d00-135">Poinstruować zautomatyzowane ML, aby nie używało niektórych trenerów.</span><span class="sxs-lookup"><span data-stu-id="80d00-135">Instruct automated ML not to use certain trainers.</span></span>

    <span data-ttu-id="80d00-136">Domyślna lista trenerów do optymalizacji są eksplorowane na zadanie.</span><span class="sxs-lookup"><span data-stu-id="80d00-136">A default list of trainers to optimize are explored per task.</span></span> <span data-ttu-id="80d00-137">Tę listę można zmodyfikować dla każdego eksperymentu.</span><span class="sxs-lookup"><span data-stu-id="80d00-137">This list can be modified for each experiment.</span></span> <span data-ttu-id="80d00-138">Na przykład trenerów, które działają powoli na zestaw danych można usunąć z listy.</span><span class="sxs-lookup"><span data-stu-id="80d00-138">For instance, trainers that run slowly on your dataset can be removed from the list.</span></span> <span data-ttu-id="80d00-139">Aby zoptymalizować na `experimentSettings.Trainers.Clear()`jednym konkretnym wywołaniu trenera, a następnie dodać trenera, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="80d00-139">To optimize on one specific trainer call `experimentSettings.Trainers.Clear()`, then add the trainer that you want to use.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.Trainers.Remove(RegressionTrainer.LbfgsPoissonRegression);
    experimentSettings.Trainers.Remove(RegressionTrainer.OnlineGradientDescent);
    ```

<span data-ttu-id="80d00-140">Listę obsługiwanych trenerów na zadanie ML można znaleźć pod odpowiednim linkiem poniżej:</span><span class="sxs-lookup"><span data-stu-id="80d00-140">The list of supported trainers per ML task can be found at the corresponding link below:</span></span>

* [<span data-ttu-id="80d00-141">Obsługiwane algorytmy klasyfikacji binarnej</span><span class="sxs-lookup"><span data-stu-id="80d00-141">Supported Binary Classification Algorithms</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationTrainer)
* [<span data-ttu-id="80d00-142">Obsługiwane algorytmy klasyfikacji wieloklasowej</span><span class="sxs-lookup"><span data-stu-id="80d00-142">Supported Multiclass Classification Algorithms</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationTrainer)
* [<span data-ttu-id="80d00-143">Obsługiwane algorytmy regresji</span><span class="sxs-lookup"><span data-stu-id="80d00-143">Supported Regression Algorithms</span></span>](xref:Microsoft.ML.AutoML.RegressionTrainer)
* [<span data-ttu-id="80d00-144">Obsługiwane algorytmy rekomendacji</span><span class="sxs-lookup"><span data-stu-id="80d00-144">Supported Recommendation Algorithms</span></span>](xref:Microsoft.ML.AutoML.RecommendationTrainer)

## <a name="optimizing-metric"></a><span data-ttu-id="80d00-145">Optymalizacja metryki</span><span class="sxs-lookup"><span data-stu-id="80d00-145">Optimizing metric</span></span>

<span data-ttu-id="80d00-146">Metryka optymalizacji, jak pokazano w powyższym przykładzie, określa metrykę, która ma być zoptymalizowana podczas szkolenia modelu.</span><span class="sxs-lookup"><span data-stu-id="80d00-146">The optimizing metric, as shown in the example above, determines the metric to be optimized during model training.</span></span> <span data-ttu-id="80d00-147">Metryka optymalizująca, którą można wybrać, zależy od wybranego typu zadania.</span><span class="sxs-lookup"><span data-stu-id="80d00-147">The optimizing metric you can select is determined by the task type you choose.</span></span> <span data-ttu-id="80d00-148">Poniżej znajduje się lista dostępnych danych.</span><span class="sxs-lookup"><span data-stu-id="80d00-148">Below is a list of available metrics.</span></span>

|[<span data-ttu-id="80d00-149">Klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="80d00-149">Binary Classification</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationMetric) | [<span data-ttu-id="80d00-150">Klasyfikacja wieloklasowa</span><span class="sxs-lookup"><span data-stu-id="80d00-150">Multiclass Classification</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric) |[<span data-ttu-id="80d00-151">Zalecenie & regresji</span><span class="sxs-lookup"><span data-stu-id="80d00-151">Regression & Recommendation</span></span>](xref:Microsoft.ML.AutoML.RegressionMetric)
|-- |-- |--
|<span data-ttu-id="80d00-152">Dokładność</span><span class="sxs-lookup"><span data-stu-id="80d00-152">Accuracy</span></span>| <span data-ttu-id="80d00-153">LogLoss (Strata logów)</span><span class="sxs-lookup"><span data-stu-id="80d00-153">LogLoss</span></span> | <span data-ttu-id="80d00-154">RSquared (kwadrat)</span><span class="sxs-lookup"><span data-stu-id="80d00-154">RSquared</span></span>
|<span data-ttu-id="80d00-155">AreaUnderPrecisionRecallCurve (Krzywa niedostatecznie przypomnę)</span><span class="sxs-lookup"><span data-stu-id="80d00-155">AreaUnderPrecisionRecallCurve</span></span> | <span data-ttu-id="80d00-156">LogLossReduction (Redukcja loglossów)</span><span class="sxs-lookup"><span data-stu-id="80d00-156">LogLossReduction</span></span> | <span data-ttu-id="80d00-157">MeanAbsoluteError (MeanAbsoluteError)</span><span class="sxs-lookup"><span data-stu-id="80d00-157">MeanAbsoluteError</span></span>
|<span data-ttu-id="80d00-158">AreaUnderRocCurve (ObszarUnderrocCurve)</span><span class="sxs-lookup"><span data-stu-id="80d00-158">AreaUnderRocCurve</span></span> | <span data-ttu-id="80d00-159">Dokładność makra</span><span class="sxs-lookup"><span data-stu-id="80d00-159">MacroAccuracy</span></span> | <span data-ttu-id="80d00-160">Błąd MeanSquaredError</span><span class="sxs-lookup"><span data-stu-id="80d00-160">MeanSquaredError</span></span>
|<span data-ttu-id="80d00-161">Wynik F1</span><span class="sxs-lookup"><span data-stu-id="80d00-161">F1Score</span></span> | <span data-ttu-id="80d00-162">Mikrodokładność</span><span class="sxs-lookup"><span data-stu-id="80d00-162">MicroAccuracy</span></span> | <span data-ttu-id="80d00-163">Błąd RootMeanSquaredError</span><span class="sxs-lookup"><span data-stu-id="80d00-163">RootMeanSquaredError</span></span>
|<span data-ttu-id="80d00-164">Ujemna precyzja</span><span class="sxs-lookup"><span data-stu-id="80d00-164">NegativePrecision</span></span> | <span data-ttu-id="80d00-165">Dokładność Topk</span><span class="sxs-lookup"><span data-stu-id="80d00-165">TopKAccuracy</span></span>
|<span data-ttu-id="80d00-166">NegatywnePrzywołanie</span><span class="sxs-lookup"><span data-stu-id="80d00-166">NegativeRecall</span></span> |
|<span data-ttu-id="80d00-167">Dodatnia dokładność</span><span class="sxs-lookup"><span data-stu-id="80d00-167">PositivePrecision</span></span>
|<span data-ttu-id="80d00-168">PozytywnePrzywołanie</span><span class="sxs-lookup"><span data-stu-id="80d00-168">PositiveRecall</span></span>

## <a name="data-pre-processing-and-featurization"></a><span data-ttu-id="80d00-169">Wstępne przetwarzanie danych i featurization</span><span class="sxs-lookup"><span data-stu-id="80d00-169">Data pre-processing and featurization</span></span>

> [!NOTE]
> <span data-ttu-id="80d00-170">Kolumna funkcji obsługiwane tylko <xref:System.Boolean> <xref:System.Single>typy <xref:System.String>, i .</span><span class="sxs-lookup"><span data-stu-id="80d00-170">The feature column only supported types of <xref:System.Boolean>, <xref:System.Single>, and <xref:System.String>.</span></span>

<span data-ttu-id="80d00-171">Przetwarzanie wstępne danych odbywa się domyślnie, a następujące kroki są wykonywane automatycznie dla Ciebie:</span><span class="sxs-lookup"><span data-stu-id="80d00-171">Data pre-processing happens by default and the following steps are performed automatically for you:</span></span>

1. <span data-ttu-id="80d00-172">Funkcje upuszczenia bez przydatnych informacji</span><span class="sxs-lookup"><span data-stu-id="80d00-172">Drop features with no useful information</span></span>

    <span data-ttu-id="80d00-173">Funkcje upuść bez przydatnych informacji z zestawów szkoleniowych i sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="80d00-173">Drop features with no useful information from training and validation sets.</span></span> <span data-ttu-id="80d00-174">Należą do nich funkcje ze wszystkimi brakującymi wartościami, tą samą wartością we wszystkich wierszach lub o bardzo wysokiej kardynalności (np. haszysze, identyfikatory lub identyfikatory GUID).</span><span class="sxs-lookup"><span data-stu-id="80d00-174">These include features with all values missing, same value across all rows or with extremely high cardinality (e.g., hashes, IDs or GUIDs).</span></span>

1. <span data-ttu-id="80d00-175">Brakujące wskazanie wartości i przypisania</span><span class="sxs-lookup"><span data-stu-id="80d00-175">Missing value indication and imputation</span></span>

    <span data-ttu-id="80d00-176">Wypełnij brakujące komórki wartości wartości wartości wartością domyślną dla typu danych.</span><span class="sxs-lookup"><span data-stu-id="80d00-176">Fill missing value cells with the default value for the datatype.</span></span> <span data-ttu-id="80d00-177">Dołącz funkcje wskaźnika z taką samą liczbą gniazd jak kolumna wprowadzania.</span><span class="sxs-lookup"><span data-stu-id="80d00-177">Append indicator features with the same number of slots as the input column.</span></span> <span data-ttu-id="80d00-178">Wartość w dołączonych funkcji `1` wskaźnika jest, jeśli brakuje `0` wartości w kolumnie wejściowej i w przeciwnym razie.</span><span class="sxs-lookup"><span data-stu-id="80d00-178">The value in the appended indicator features is `1` if the value in the input column is missing and `0` otherwise.</span></span>

1. <span data-ttu-id="80d00-179">Generowanie dodatkowych funkcji</span><span class="sxs-lookup"><span data-stu-id="80d00-179">Generate additional features</span></span>

    <span data-ttu-id="80d00-180">Funkcje tekstowe: Funkcje worka z wyrazami przy użyciu unigramów i trzech znaków-gramów.</span><span class="sxs-lookup"><span data-stu-id="80d00-180">For text features: Bag-of-word features using unigrams and tri-character-grams.</span></span>

    <span data-ttu-id="80d00-181">W przypadku funkcji kategorii: kodowanie na gorąco dla funkcji o niskiej kardynalności i kodowanie skrótu jeden-hot-hash dla funkcji kategorii wysokiej kardynalności.</span><span class="sxs-lookup"><span data-stu-id="80d00-181">For categorical features: One-hot encoding for low cardinality features, and one-hot-hash encoding for high cardinality categorical features.</span></span>

1. <span data-ttu-id="80d00-182">Przekształcenia i kodowanie</span><span class="sxs-lookup"><span data-stu-id="80d00-182">Transformations and encodings</span></span>

    <span data-ttu-id="80d00-183">Funkcje tekstowe z bardzo nielicznymi unikatowymi wartościami przekształcone w funkcje kategoryczne.</span><span class="sxs-lookup"><span data-stu-id="80d00-183">Text features with very few unique values transformed into categorical features.</span></span> <span data-ttu-id="80d00-184">W zależności od kardynalności funkcji kategorycznych wykonaj kodowanie jedno-gorące lub kodowanie skrótu jeden-hot.</span><span class="sxs-lookup"><span data-stu-id="80d00-184">Depending on cardinality of categorical features, perform one-hot encoding or one-hot hash encoding.</span></span>

## <a name="exit-criteria"></a><span data-ttu-id="80d00-185">Kryteria wyjścia</span><span class="sxs-lookup"><span data-stu-id="80d00-185">Exit criteria</span></span>

<span data-ttu-id="80d00-186">Zdefiniuj kryteria, aby wykonać zadanie:</span><span class="sxs-lookup"><span data-stu-id="80d00-186">Define the criteria to complete your task:</span></span>

1. <span data-ttu-id="80d00-187">Zakończ po upływie `MaxExperimentTimeInSeconds` czasu — za pomocą w ustawieniach eksperymentu można zdefiniować, jak długo w sekundach, że zadanie powinno być kontynuowane.</span><span class="sxs-lookup"><span data-stu-id="80d00-187">Exit after a length of time - Using `MaxExperimentTimeInSeconds` in your experiment settings you can define how long in seconds that an task should continue to run.</span></span>

1. <span data-ttu-id="80d00-188">Zakończ na tokenanulowania — można użyć tokenu anulowania, który pozwala anulować zadanie, zanim zostanie zaplanowane do zakończenia.</span><span class="sxs-lookup"><span data-stu-id="80d00-188">Exit on a cancellation token -  You can use a cancellation token that lets you cancel the task before it is scheduled to finish.</span></span>

    ```csharp
    var cts = new CancellationTokenSource();
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    experimentSettings.CancellationToken = cts.Token;
    ```

## <a name="create-an-experiment"></a><span data-ttu-id="80d00-189">Tworzenie eksperymentu</span><span class="sxs-lookup"><span data-stu-id="80d00-189">Create an experiment</span></span>

<span data-ttu-id="80d00-190">Po skonfigurowaniu ustawień eksperymentu można przystąpić do tworzenia eksperymentu.</span><span class="sxs-lookup"><span data-stu-id="80d00-190">Once you have configured the experiment settings, you are ready to create the experiment.</span></span>

```csharp
RegressionExperiment experiment = mlContext.Auto().CreateRegressionExperiment(experimentSettings);
```

## <a name="run-the-experiment"></a><span data-ttu-id="80d00-191">Uruchamianie eksperymentu</span><span class="sxs-lookup"><span data-stu-id="80d00-191">Run the experiment</span></span>

<span data-ttu-id="80d00-192">Uruchomienie eksperymentu wyzwala przetwarzanie wstępne danych, wybór algorytmu uczenia i dostrajanie hiperparametrów.</span><span class="sxs-lookup"><span data-stu-id="80d00-192">Running the experiment triggers data pre-processing, learning algorithm selection, and hyperparameter tuning.</span></span> <span data-ttu-id="80d00-193">AutoML będzie nadal generować kombinacje featurization, algorytmy uczenia `MaxExperimentTimeInSeconds` się i hiperparametrów, dopóki nie zostanie osiągnięty lub eksperyment zostanie zakończony.</span><span class="sxs-lookup"><span data-stu-id="80d00-193">AutoML will continue to generate combinations of featurization, learning algorithms, and hyperparameters until the `MaxExperimentTimeInSeconds` is reached or the experiment is terminated.</span></span>

```csharp
ExperimentResult<RegressionMetrics> experimentResult = experiment
    .Execute(trainingDataView, LabelColumnName, progressHandler: progressHandler);
```

<span data-ttu-id="80d00-194">Eksploruj inne przeciążenia, `Execute()` jeśli chcesz przekazać dane sprawdzania poprawności, informacje o kolumnie wskazujące cel kolumny lub prefeaturizers.</span><span class="sxs-lookup"><span data-stu-id="80d00-194">Explore other overloads for `Execute()` if you want to pass in validation data, column information indicating the column purpose, or prefeaturizers.</span></span>

## <a name="training-modes"></a><span data-ttu-id="80d00-195">Tryby treningowe</span><span class="sxs-lookup"><span data-stu-id="80d00-195">Training modes</span></span>

### <a name="training-dataset"></a><span data-ttu-id="80d00-196">Zestaw danych szkoleniowych</span><span class="sxs-lookup"><span data-stu-id="80d00-196">Training dataset</span></span>

<span data-ttu-id="80d00-197">Automl udostępnia przeciążoną metodę wykonywania eksperymentu, która umożliwia dostarczanie danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="80d00-197">AutoML provides an overloaded experiment execute method which allows you to provide training data.</span></span> <span data-ttu-id="80d00-198">Wewnętrznie zautomatyzowany ml dzieli dane na podziały sprawdzania poprawności pociągu.</span><span class="sxs-lookup"><span data-stu-id="80d00-198">Internally, automated ML divides the data into train-validate splits.</span></span>

```csharp
experiment.Execute(trainDataView);
```

### <a name="custom-validation-dataset"></a><span data-ttu-id="80d00-199">Niestandardowy zestaw danych sprawdzania poprawności</span><span class="sxs-lookup"><span data-stu-id="80d00-199">Custom validation dataset</span></span>

<span data-ttu-id="80d00-200">Użyj niestandardowego zestawu danych sprawdzania poprawności, jeśli losowy podział nie jest dopuszczalny, jak to zwykle bywa w przypadku danych szeregów czasowych.</span><span class="sxs-lookup"><span data-stu-id="80d00-200">Use custom validation dataset if random split is not acceptable, as is usually the case with time series data.</span></span> <span data-ttu-id="80d00-201">Można określić własny zestaw danych sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="80d00-201">You can specify your own validation dataset.</span></span> <span data-ttu-id="80d00-202">Model zostanie oceniony względem zestawu danych sprawdzania poprawności określonego zamiast jednego lub więcej losowych zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="80d00-202">The model will be evaluated against the validation dataset specified instead of one or more random datasets.</span></span>

```csharp
experiment.Execute(trainDataView, validationDataView);
```

## <a name="explore-model-metrics"></a><span data-ttu-id="80d00-203">Eksplorowanie danych modelu</span><span class="sxs-lookup"><span data-stu-id="80d00-203">Explore model metrics</span></span>

<span data-ttu-id="80d00-204">Po każdej iteracji eksperymentu ML są przechowywane metryki odnoszące się do tego zadania.</span><span class="sxs-lookup"><span data-stu-id="80d00-204">After each iteration of an ML experiment, metrics relating to that task are stored.</span></span>

<span data-ttu-id="80d00-205">Na przykład możemy uzyskać dostęp do metryk sprawdzania poprawności z najlepszego przebiegu:</span><span class="sxs-lookup"><span data-stu-id="80d00-205">For example, we can access validation metrics from the best run:</span></span>

```csharp
RegressionMetrics metrics = experimentResult.BestRun.ValidationMetrics;
Console.WriteLine($"R-Squared: {metrics.RSquared:0.##}");
Console.WriteLine($"Root Mean Squared Error: {metrics.RootMeanSquaredError:0.##}");
```

<span data-ttu-id="80d00-206">Poniżej przedstawiono wszystkie dostępne metryki dla zadania ml:</span><span class="sxs-lookup"><span data-stu-id="80d00-206">The following are all the available metrics per ML task:</span></span>

* [<span data-ttu-id="80d00-207">Metryki klasyfikacji binarnej</span><span class="sxs-lookup"><span data-stu-id="80d00-207">Binary classification metrics</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationMetric)
* [<span data-ttu-id="80d00-208">Wieloklasowe metryki klasyfikacji</span><span class="sxs-lookup"><span data-stu-id="80d00-208">Multiclass classification metrics</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric)
* [<span data-ttu-id="80d00-209">Wskaźniki rekomendacji & regresji</span><span class="sxs-lookup"><span data-stu-id="80d00-209">Regression & recommendation metrics</span></span>](xref:Microsoft.ML.AutoML.RegressionMetric)

## <a name="see-also"></a><span data-ttu-id="80d00-210">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80d00-210">See also</span></span>

<span data-ttu-id="80d00-211">Aby uzyskać pełne próbki kodu i więcej odwiedź repozytorium GitHub dotnet/machinelearning.For full code samples and more visit the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) GitHub repository.</span><span class="sxs-lookup"><span data-stu-id="80d00-211">For full code samples and more visit the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) GitHub repository.</span></span>
