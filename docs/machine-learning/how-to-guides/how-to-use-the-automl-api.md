---
title: Jak używać strukturze ML.NET automatyczne interfejsu API uczenia Maszynowego
description: Strukturze ML.NET automatyczne interfejsu API uczenia Maszynowego automatyzuje modelu proces tworzenia i generuje gotowe do wdrożenia modelu. Dowiedz się, opcje, które umożliwiają skonfigurowanie automatycznych usługi machine learning zadania.
ms.date: 04/24/2019
ms.custom: mvc,how-to
ms.openlocfilehash: b05b6ed7c66062b28aaf634913a9598602b62498
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557878"
---
# <a name="how-to-use-the-mlnet-automated-machine-learning-api"></a><span data-ttu-id="f3a8a-104">Jak używać strukturze ML.NET automatyczne interfejsu API usługi machine learning</span><span class="sxs-lookup"><span data-stu-id="f3a8a-104">How to use the ML.NET automated machine learning API</span></span>

<span data-ttu-id="f3a8a-105">Automatyczne usługi machine learning (AutoML) automatyzuje proces stosowania uczenia maszynowego do danych.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-105">Automated machine learning (AutoML) automates the process of applying machine learning to data.</span></span> <span data-ttu-id="f3a8a-106">Biorąc pod uwagę zestaw danych, możesz uruchomić AutoML **eksperymentować** Iterowanie featurizations różnych danych, maszyny algorytmów uczenia i hiperparametrów, aby wybrać najlepszy model.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-106">Given a dataset, you can run an AutoML **experiment** to iterate over different data featurizations, machine learning algorithms, and hyperparameters to select the best model.</span></span>

> [!NOTE]
> <span data-ttu-id="f3a8a-107">W tym temacie odnosi się do automatycznego machine learning API dla strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-107">This topic refers to the automated machine learning API for ML.NET, which is currently in preview.</span></span> <span data-ttu-id="f3a8a-108">Materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-108">Material may be subject to change.</span></span>

## <a name="load-data"></a><span data-ttu-id="f3a8a-109">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="f3a8a-109">Load data</span></span>

<span data-ttu-id="f3a8a-110">Automatyczne usługi machine learning obsługuje ładowanie zestawu danych do [IDataView](https://docs.microsoft.com/dotnet/api/microsoft.ml.idataview?view=ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="f3a8a-110">Automated machine learning supports loading a dataset into an [IDataView](https://docs.microsoft.com/dotnet/api/microsoft.ml.idataview?view=ml-dotnet).</span></span> <span data-ttu-id="f3a8a-111">Dane mogą być w formie plików wartości rozdzielane tabulatorami (TSV) i plików rozdzielanych przecinkami (CSV).</span><span class="sxs-lookup"><span data-stu-id="f3a8a-111">Data can be in the form of tab-separated value (TSV) files and comma separated value (CSV) files.</span></span>

<span data-ttu-id="f3a8a-112">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f3a8a-112">Example:</span></span>

```csharp
using Microsoft.ML;
using Microsoft.ML.AutoML;
    ...
    MLContext mlContext = new MLContext();
    IDataView trainDataView = mlContext.Data.LoadFromTextFile<SentimentIssue>("my-data-file.csv", hasHeader: true);
```

## <a name="select-the-machine-learning-task-type"></a><span data-ttu-id="f3a8a-113">Wybierz typ zadania uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="f3a8a-113">Select the machine learning task type</span></span>
<span data-ttu-id="f3a8a-114">Przed utworzeniem eksperymentu, należy określić rodzaj maszyny nauczanym problemem, który chcesz rozwiązać.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-114">Before creating an experiment, determine the kind of machine learning problem you want to solve.</span></span> <span data-ttu-id="f3a8a-115">Automatyczne machine learning obsługuje następujące zadania uczenia Maszynowego:</span><span class="sxs-lookup"><span data-stu-id="f3a8a-115">Automated machine learning supports the following ML tasks:</span></span>
* <span data-ttu-id="f3a8a-116">Klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="f3a8a-116">Binary Classification</span></span>
* <span data-ttu-id="f3a8a-117">Wieloklasowej klasyfikacji</span><span class="sxs-lookup"><span data-stu-id="f3a8a-117">Multiclass Classification</span></span>
* <span data-ttu-id="f3a8a-118">Regresji</span><span class="sxs-lookup"><span data-stu-id="f3a8a-118">Regression</span></span>

## <a name="create-experiment-settings"></a><span data-ttu-id="f3a8a-119">Utwórz ustawienia eksperymentu</span><span class="sxs-lookup"><span data-stu-id="f3a8a-119">Create experiment settings</span></span>

<span data-ttu-id="f3a8a-120">Tworzenie eksperymentu ustawień dla określonego typu zadania uczenia Maszynowego:</span><span class="sxs-lookup"><span data-stu-id="f3a8a-120">Create experiment settings for the determined ML task type:</span></span>

* <span data-ttu-id="f3a8a-121">Klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="f3a8a-121">Binary Classification</span></span>

  ```csharp
  var experimentSettings = new BinaryExperimentSettings();
  ```

* <span data-ttu-id="f3a8a-122">Wieloklasowej klasyfikacji</span><span class="sxs-lookup"><span data-stu-id="f3a8a-122">Multiclass Classification</span></span>

  ```csharp
  var experimentSettings = new MulticlassExperimentSettings();
  ```

* <span data-ttu-id="f3a8a-123">Regresji</span><span class="sxs-lookup"><span data-stu-id="f3a8a-123">Regression</span></span>

  ```csharp
  var experimentSettings = new RegressionExperimentSettings();
  ```

## <a name="configure-experiment-settings"></a><span data-ttu-id="f3a8a-124">Konfigurowanie ustawień eksperymentu</span><span class="sxs-lookup"><span data-stu-id="f3a8a-124">Configure experiment settings</span></span>

<span data-ttu-id="f3a8a-125">Eksperymenty są wysoce konfigurowalne.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-125">Experiments are highly configurable.</span></span> <span data-ttu-id="f3a8a-126">Zobacz [dokumentacji interfejsu API AutoML](https://docs.microsoft.com/dotnet/api/microsoft.ml.auto?view=ml-dotnet) poznania pełnej listy ustawień konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-126">See the [AutoML API docs](https://docs.microsoft.com/dotnet/api/microsoft.ml.auto?view=ml-dotnet) for a full list of configuration settings.</span></span>

<span data-ttu-id="f3a8a-127">Oto niektóre przykłady:</span><span class="sxs-lookup"><span data-stu-id="f3a8a-127">Some examples include:</span></span>

1. <span data-ttu-id="f3a8a-128">Określ maksymalny czas, w którym można uruchamiać eksperymentu.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-128">Specify the maximum time that the experiment is allowed to run.</span></span>

    ```csharp
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    ```

1. <span data-ttu-id="f3a8a-129">Użyj token anulowania do anulowania doświadczenia, zanim jest zaplanowane na zakończenie.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-129">Use a cancellation token to cancel the experiment before it is scheduled to finish.</span></span>

    ```csharp
    experimentSettings.CancellationToken = cts.Token;

    // Cancel experiment after the user presses any key
    CancelExperimentAfterAnyKeyPress(cts);
    ```

1. <span data-ttu-id="f3a8a-130">Określ inną metrykę optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-130">Specify a different optimizing metric.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.OptimizingMetric = RegressionMetric.MeanSquaredError;
    ```

1. <span data-ttu-id="f3a8a-131">`CacheDirectory` Ustawienie jest wskaźnikiem do katalogu, w którym zostaną zapisane wszystkie modele skonfigurowanych pod kątem podczas wykonywania zadania AutoML.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-131">The `CacheDirectory` setting is a pointer to a directory where all models trained during the AutoML task will be saved.</span></span> <span data-ttu-id="f3a8a-132">Jeśli `CacheDirectory` jest ustawiona na wartość null, modele będą przechowywane w pamięci, a nie zapisane na dysku.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-132">If `CacheDirectory` is set to null, models will be kept in memory instead of written to disk.</span></span>
 
    ```csharp
    experimentSettings.CacheDirectory = null;
    ```

1. <span data-ttu-id="f3a8a-133">Poinstruuj ML automatycznego nie należy używać niektórych instruktorów.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-133">Instruct automated ML not to use certain trainers.</span></span>

    <span data-ttu-id="f3a8a-134">Domyślną listę instruktorów, aby zoptymalizować zbadano poszczególnych zadań.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-134">A default list of trainers to optimize are explored per task.</span></span> <span data-ttu-id="f3a8a-135">Dla każdego doświadczenia można zmodyfikować tej listy.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-135">This list can be modified for each experiment.</span></span> <span data-ttu-id="f3a8a-136">Na przykład można usunąć z listy instruktorów, które spowolnienie działania na twoim zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-136">For instance, trainers that run slowly on your dataset can be removed from the list.</span></span> <span data-ttu-id="f3a8a-137">Do optymalizacji na jedno wywołanie dla określonych trenerów `experimentSettings.Trainers.Clear()`, następnie dodać instruktora, którego chcesz używać.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-137">To optimize on one specific trainer call `experimentSettings.Trainers.Clear()`, then add the trainer that you want to use.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.Trainers.Remove(RegressionTrainer.LbfgsPoissonRegression);
    experimentSettings.Trainers.Remove(RegressionTrainer.OnlineGradientDescent);
    ```

<span data-ttu-id="f3a8a-138">Lista obsługiwanych Instruktorzy każdego zadania uczenia Maszynowego znajduje się w temacie odpowiednie łącze poniżej:</span><span class="sxs-lookup"><span data-stu-id="f3a8a-138">The list of supported trainers per ML task can be found at the corresponding link below:</span></span>
* [<span data-ttu-id="f3a8a-139">Obsługiwane algorytmy Klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="f3a8a-139">Supported Binary Classification Algorithms</span></span>](https://docs.microsoft.com/en-us/dotnet/api/microsoft.ml.automl.binaryclassificationtrainer?view=automl-dotnet)
* [<span data-ttu-id="f3a8a-140">Obsługiwane algorytmy Wieloklasowej klasyfikacji</span><span class="sxs-lookup"><span data-stu-id="f3a8a-140">Supported Multiclass Classification Algorithms</span></span>](https://docs.microsoft.com/en-us/dotnet/api/microsoft.ml.automl.multiclassclassificationtrainer?view=automl-dotnet)
* [<span data-ttu-id="f3a8a-141">Regresja obsługiwane algorytmy</span><span class="sxs-lookup"><span data-stu-id="f3a8a-141">Supported Regression Algorithms</span></span>](https://docs.microsoft.com/en-us/dotnet/api/microsoft.ml.automl.regressiontrainer?view=automl-dotnet)

## <a name="optimizing-metric"></a><span data-ttu-id="f3a8a-142">Optymalizacja metryki</span><span class="sxs-lookup"><span data-stu-id="f3a8a-142">Optimizing metric</span></span>

<span data-ttu-id="f3a8a-143">Optymalizacja metryki, jak pokazano w przykładzie powyżej, określa metryki można optymalizować podczas uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-143">The optimizing metric, as shown in the example above, determines the metric to be optimized during model training.</span></span> <span data-ttu-id="f3a8a-144">Optymalizacja metryki, które można wybrać, jest określana przez typ zadania, które wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-144">The optimizing metric you can select is determined by the task type you choose.</span></span> <span data-ttu-id="f3a8a-145">Poniżej znajduje się lista dostępnych metryk.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-145">Below is a list of available metrics.</span></span>

|[<span data-ttu-id="f3a8a-146">Klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="f3a8a-146">Binary Classification</span></span>](https://docs.microsoft.com/en-us/dotnet/api/microsoft.ml.automl.binaryclassificationmetric?view=automl-dotnet) | [<span data-ttu-id="f3a8a-147">Wieloklasowej klasyfikacji</span><span class="sxs-lookup"><span data-stu-id="f3a8a-147">Multiclass Classification</span></span>](https://docs.microsoft.com/en-us/dotnet/api/microsoft.ml.automl.multiclassclassificationmetric?view=automl-dotnet) | [<span data-ttu-id="f3a8a-148">Regression</span><span class="sxs-lookup"><span data-stu-id="f3a8a-148">Regression</span></span>](https://docs.microsoft.com/en-us/dotnet/api/microsoft.ml.automl.regressionmetric?view=automl-dotnet)
|-- |-- |--
|<span data-ttu-id="f3a8a-149">dokładność</span><span class="sxs-lookup"><span data-stu-id="f3a8a-149">Accuracy</span></span>| <span data-ttu-id="f3a8a-150">LogLoss</span><span class="sxs-lookup"><span data-stu-id="f3a8a-150">LogLoss</span></span> | <span data-ttu-id="f3a8a-151">RSquared</span><span class="sxs-lookup"><span data-stu-id="f3a8a-151">RSquared</span></span>
|<span data-ttu-id="f3a8a-152">AreaUnderPrecisionRecallCurve</span><span class="sxs-lookup"><span data-stu-id="f3a8a-152">AreaUnderPrecisionRecallCurve</span></span> | <span data-ttu-id="f3a8a-153">LogLossReduction</span><span class="sxs-lookup"><span data-stu-id="f3a8a-153">LogLossReduction</span></span> | <span data-ttu-id="f3a8a-154">MeanAbsoluteError</span><span class="sxs-lookup"><span data-stu-id="f3a8a-154">MeanAbsoluteError</span></span>
|<span data-ttu-id="f3a8a-155">AreaUnderRocCurve</span><span class="sxs-lookup"><span data-stu-id="f3a8a-155">AreaUnderRocCurve</span></span> | <span data-ttu-id="f3a8a-156">MacroAccuracy</span><span class="sxs-lookup"><span data-stu-id="f3a8a-156">MacroAccuracy</span></span> | <span data-ttu-id="f3a8a-157">MeanSquaredError</span><span class="sxs-lookup"><span data-stu-id="f3a8a-157">MeanSquaredError</span></span>
|<span data-ttu-id="f3a8a-158">F1Score</span><span class="sxs-lookup"><span data-stu-id="f3a8a-158">F1Score</span></span> | <span data-ttu-id="f3a8a-159">MicroAccuracy</span><span class="sxs-lookup"><span data-stu-id="f3a8a-159">MicroAccuracy</span></span> | <span data-ttu-id="f3a8a-160">RootMeanSquaredError</span><span class="sxs-lookup"><span data-stu-id="f3a8a-160">RootMeanSquaredError</span></span>
|<span data-ttu-id="f3a8a-161">NegativePrecision</span><span class="sxs-lookup"><span data-stu-id="f3a8a-161">NegativePrecision</span></span> | <span data-ttu-id="f3a8a-162">TopKAccuracy</span><span class="sxs-lookup"><span data-stu-id="f3a8a-162">TopKAccuracy</span></span>
|<span data-ttu-id="f3a8a-163">NegativeRecall</span><span class="sxs-lookup"><span data-stu-id="f3a8a-163">NegativeRecall</span></span> |
|<span data-ttu-id="f3a8a-164">PositivePrecision</span><span class="sxs-lookup"><span data-stu-id="f3a8a-164">PositivePrecision</span></span>
|<span data-ttu-id="f3a8a-165">PositiveRecall</span><span class="sxs-lookup"><span data-stu-id="f3a8a-165">PositiveRecall</span></span>

## <a name="data-pre-processing-and-featurization"></a><span data-ttu-id="f3a8a-166">Wstępne przetwarzanie danych i cechowania</span><span class="sxs-lookup"><span data-stu-id="f3a8a-166">Data pre-processing and featurization</span></span>

<span data-ttu-id="f3a8a-167">Przetwarzanie wstępne danych miały domyślnie, a poniższe kroki są wykonywane automatycznie dla Ciebie:</span><span class="sxs-lookup"><span data-stu-id="f3a8a-167">Data pre-processing happens by default and the following steps are performed automatically for you:</span></span>

1. <span data-ttu-id="f3a8a-168">Upuszczanie funkcji żadnych użytecznych informacji</span><span class="sxs-lookup"><span data-stu-id="f3a8a-168">Drop features with no useful information</span></span>

    <span data-ttu-id="f3a8a-169">Usuwanie funkcji żadnych użytecznych informacji z zestawów szkolenia i sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-169">Drop features with no useful information from training and validation sets.</span></span> <span data-ttu-id="f3a8a-170">Obejmują one funkcje wszystkich wartości Brak, tę samą wartość we wszystkich wierszach lub bardzo dużej kardynalności (np. skróty, lub identyfikatory GUID).</span><span class="sxs-lookup"><span data-stu-id="f3a8a-170">These include features with all values missing, same value across all rows or with extremely high cardinality (e.g., hashes, IDs or GUIDs).</span></span>

1. <span data-ttu-id="f3a8a-171">Brak wskazania wartość i przypisywania</span><span class="sxs-lookup"><span data-stu-id="f3a8a-171">Missing value indication and imputation</span></span>

    <span data-ttu-id="f3a8a-172">Wypełnienie brakujących wartości komórek z wartością domyślną dla typu danych.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-172">Fill missing value cells with the default value for the datatype.</span></span> <span data-ttu-id="f3a8a-173">Dołącz wskaźnik funkcji, korzystając z taką samą liczbę miejsc, jako kolumna danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-173">Append indicator features with the same number of slots as the input column.</span></span> <span data-ttu-id="f3a8a-174">Wartość w funkcji dołączonych wskaźnik jest `1` Jeśli brakuje wartości w kolumnie wejściowej i `0` inaczej.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-174">The value in the appended indicator features is `1` if the value in the input column is missing and `0` otherwise.</span></span>

1. <span data-ttu-id="f3a8a-175">Generuj dodatkowe funkcje</span><span class="sxs-lookup"><span data-stu-id="f3a8a-175">Generate additional features</span></span>
    
    <span data-ttu-id="f3a8a-176">Funkcje tekstowe: Funkcje zbioru programu word za pomocą unigrams i tri znak g.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-176">For text features: Bag-of-word features using unigrams and tri-character-grams.</span></span>
    
    <span data-ttu-id="f3a8a-177">Podzielone na kategorie funkcji: Jeden hot-hash kodowanie funkcji podzielonych na kategorie wysoka Kardynalność klauzuli i hot jeden kodowania dla funkcji Kardynalność niski.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-177">For categorical features: One-hot encoding for low cardinality features, and one-hot-hash encoding for high cardinality categorical features.</span></span>

1. <span data-ttu-id="f3a8a-178">Przekształcenia i kodowania</span><span class="sxs-lookup"><span data-stu-id="f3a8a-178">Transformations and encodings</span></span>

    <span data-ttu-id="f3a8a-179">Funkcje tekstowe z bardzo niewielkiej liczbie unikatowych wartości przekształcone w kategorii funkcji.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-179">Text features with very few unique values transformed into categorical features.</span></span> <span data-ttu-id="f3a8a-180">W zależności od kardynalności kategorii funkcji należy wykonać hot jeden kodowania lub hot jeden skrót kodowania.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-180">Depending on cardinality of categorical features, perform one-hot encoding or one-hot hash encoding.</span></span>

## <a name="exit-criteria"></a><span data-ttu-id="f3a8a-181">Kryteria wyjścia</span><span class="sxs-lookup"><span data-stu-id="f3a8a-181">Exit criteria</span></span>

<span data-ttu-id="f3a8a-182">Określ kryteria do ukończenia zadania:</span><span class="sxs-lookup"><span data-stu-id="f3a8a-182">Define the criteria to complete your task:</span></span>

1. <span data-ttu-id="f3a8a-183">Zakończ po przez długi czas — przy użyciu `MaxExperimentTimeInSeconds` w ustawieniach eksperymentu można zdefiniować, jak długo w ciągu kilku sekund, które zadania powinny nadal działać.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-183">Exit after a length of time - Using `MaxExperimentTimeInSeconds` in your experiment settings you can define how long in seconds that an task should continue to run.</span></span>

1. <span data-ttu-id="f3a8a-184">Zakończ token anulowania — mogą używać token anulowania, który pozwala anulować zadania, zanim jest zaplanowane na zakończenie.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-184">Exit on a cancellation token -  You can use a cancellation token that lets you cancel the task before it is scheduled to finish.</span></span>

    ```csharp
    var cts = new CancellationTokenSource();
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    experimentSettings.CancellationToken = cts.Token;
    ```

## <a name="create-an-experiment"></a><span data-ttu-id="f3a8a-185">Tworzenie eksperymentu</span><span class="sxs-lookup"><span data-stu-id="f3a8a-185">Create an experiment</span></span>

<span data-ttu-id="f3a8a-186">Po skonfigurowaniu ustawień eksperymentu, możesz przystąpić do tworzenia eksperymentu.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-186">Once you have configured the experiment settings, you are ready to create the experiment.</span></span>

```csharp
RegressionExperiment experiment = mlContext.Auto().CreateRegressionExperiment(experimentSettings);
```

## <a name="run-the-experiment"></a><span data-ttu-id="f3a8a-187">Uruchamianie eksperymentu</span><span class="sxs-lookup"><span data-stu-id="f3a8a-187">Run the experiment</span></span>

<span data-ttu-id="f3a8a-188">Uruchamianie eksperymentu danych wyzwalaczy przetwarzania wstępnego, algorytm wybór i strojenia hiperparametrycznego uczenia.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-188">Running the experiment triggers data pre-processing, learning algorithm selection, and hyperparameter tuning.</span></span> <span data-ttu-id="f3a8a-189">AutoML będą w dalszym ciągu kombinacji cechowania, algorytmów uczenia i hiperparametrów aż do wygenerowania `MaxExperimentTimeInSeconds` osiągnięciu lub eksperymentu zostanie zakończony.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-189">AutoML will continue to generate combinations of featurization, learning algorithms, and hyperparameters until the `MaxExperimentTimeInSeconds` is reached or the experiment is terminated.</span></span>

```csharp
ExperimentResult<RegressionMetrics> experimentResult = experiment
    .Execute(trainingDataView, LabelColumnName, progressHandler: progressHandler);
```

<span data-ttu-id="f3a8a-190">Poznaj inne przeciążenia `Execute()` jeśli mają być przekazywane sprawdzania poprawności danych, wskazując przeznaczenie kolumny lub prefeaturizers informacji o kolumnie.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-190">Explore other overloads for `Execute()` if you want to pass in validation data, column information indicating the column purpose, or prefeaturizers.</span></span>

## <a name="training-modes"></a><span data-ttu-id="f3a8a-191">Tryby szkolenia</span><span class="sxs-lookup"><span data-stu-id="f3a8a-191">Training modes</span></span>

### <a name="training-dataset"></a><span data-ttu-id="f3a8a-192">Zestaw danych szkoleniowych</span><span class="sxs-lookup"><span data-stu-id="f3a8a-192">Training dataset</span></span>

<span data-ttu-id="f3a8a-193">AutoML zapewnia przeciążone eksperymentu Wykonaj metodę, która umożliwia przekazanie danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-193">AutoML provides an overloaded experiment execute method which allows you to provide training data.</span></span> <span data-ttu-id="f3a8a-194">Wewnętrznie zautomatyzowane ML dzieli dane na train-validate dzieli dane.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-194">Internally, automated ML divides the data into train-validate splits.</span></span>

```csharp
experiment.Execute(trainDataView);   
```

### <a name="custom-validation-dataset"></a><span data-ttu-id="f3a8a-195">Zestaw niestandardowego sprawdzania poprawności danych</span><span class="sxs-lookup"><span data-stu-id="f3a8a-195">Custom validation dataset</span></span>

<span data-ttu-id="f3a8a-196">Użyj zestawu niestandardowego sprawdzania poprawności danych, jeśli losowe podziału nie jest dopuszczalne, tak jak zwykle w przypadku przy użyciu danych szeregów czasowych.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-196">Use custom validation dataset if random split is not acceptable, as is usually the case with time series data.</span></span> <span data-ttu-id="f3a8a-197">Można określić własnego zestawu danych walidacji.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-197">You can specify your own validation dataset.</span></span> <span data-ttu-id="f3a8a-198">Model zostaną ocenione względem zestawu danych walidacji, zamiast jednego lub więcej losowych zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-198">The model will be evaluated against the validation dataset specified instead of one or more random datasets.</span></span>

```csharp
experiment.Execute(trainDataView, validationDataView);   
```

## <a name="explore-model-metrics"></a><span data-ttu-id="f3a8a-199">Eksplorowanie metryk modelu</span><span class="sxs-lookup"><span data-stu-id="f3a8a-199">Explore model metrics</span></span>

<span data-ttu-id="f3a8a-200">Po każdej iteracji eksperymentu uczenia Maszynowego metryki odnoszące się do tego zadania są przechowywane.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-200">After each iteration of an ML experiment, metrics relating to that task are stored.</span></span>

<span data-ttu-id="f3a8a-201">Na przykład firma Microsoft jest dostępna metryki weryfikacji najlepszy przebieg:</span><span class="sxs-lookup"><span data-stu-id="f3a8a-201">For example, we can access validation metrics from the best run:</span></span>

```csharp
RegressionMetrics metrics = experimentResult.BestRun.ValidationMetrics;
Console.WriteLine($"R-Squared: {metrics.RSquared:0.##}");
Console.WriteLine($"Root Mean Squared Error: {metrics.RootMeanSquaredError:0.##}");
```

<span data-ttu-id="f3a8a-202">Poniżej wymieniono wszystkie dostępne metryki dla zadania uczenia Maszynowego:</span><span class="sxs-lookup"><span data-stu-id="f3a8a-202">The following are all the available metrics per ML task:</span></span>
* [<span data-ttu-id="f3a8a-203">Klasyfikacja binarna metryki</span><span class="sxs-lookup"><span data-stu-id="f3a8a-203">Binary classification metrics</span></span>](https://docs.microsoft.com/en-us/dotnet/api/microsoft.ml.automl.binaryclassificationmetric?view=automl-dotnet
)
* [<span data-ttu-id="f3a8a-204">Metryki klasyfikacji wieloklasowej</span><span class="sxs-lookup"><span data-stu-id="f3a8a-204">Multiclass classification metrics</span></span>](https://docs.microsoft.com/en-us/dotnet/api/microsoft.ml.automl.multiclassclassificationmetric?view=automl-dotnet
)
* [<span data-ttu-id="f3a8a-205">Metryki regresji</span><span class="sxs-lookup"><span data-stu-id="f3a8a-205">Regression metrics</span></span>](https://docs.microsoft.com/en-us/dotnet/api/microsoft.ml.automl.regressionmetric?view=automl-dotnet
)

## <a name="see-also"></a><span data-ttu-id="f3a8a-206">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3a8a-206">See also</span></span>

<span data-ttu-id="f3a8a-207">Przykłady pełnego kodu i nie tylko można znaleźć [machinelearning-dotnet-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="f3a8a-207">For full code samples and more visit the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) GitHub repository.</span></span>
