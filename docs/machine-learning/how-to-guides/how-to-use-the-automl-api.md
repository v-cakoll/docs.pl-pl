---
title: Jak używać strukturze ML.NET automatyczne interfejsu API uczenia Maszynowego
description: Strukturze ML.NET automatyczne interfejsu API uczenia Maszynowego automatyzuje modelu proces tworzenia i generuje gotowe do wdrożenia modelu. Dowiedz się, opcje, które umożliwiają skonfigurowanie automatycznych usługi machine learning zadania.
ms.date: 04/24/2019
ms.custom: mvc,how-to
ms.openlocfilehash: d624b999384dd92d41033e385d01fe556e10a065
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960417"
---
# <a name="how-to-use-the-mlnet-automated-machine-learning-api"></a>Jak używać strukturze ML.NET automatyczne interfejsu API usługi machine learning

Automatyczne usługi machine learning (AutoML) automatyzuje proces stosowania uczenia maszynowego do danych. Biorąc pod uwagę zestaw danych, możesz uruchomić AutoML **eksperymentować** Iterowanie featurizations różnych danych, maszyny algorytmów uczenia i hiperparametrów, aby wybrać najlepszy model.

> [!NOTE]
> W tym temacie odnosi się do automatycznego machine learning API dla strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej. Materiał może ulec zmianie.

## <a name="load-data"></a>Ładowanie danych

Automatyczne usługi machine learning obsługuje ładowanie zestawu danych do [IDataView](xref:Microsoft.ML.IDataView). Dane mogą być w formie plików wartości rozdzielane tabulatorami (TSV) i plików rozdzielanych przecinkami (CSV).

Przykład:

```csharp
using Microsoft.ML;
using Microsoft.ML.AutoML;
    ...
    MLContext mlContext = new MLContext();
    IDataView trainDataView = mlContext.Data.LoadFromTextFile<SentimentIssue>("my-data-file.csv", hasHeader: true);
```

## <a name="select-the-machine-learning-task-type"></a>Wybierz typ zadania uczenia maszynowego
Przed utworzeniem eksperymentu, należy określić rodzaj maszyny nauczanym problemem, który chcesz rozwiązać. Automatyczne machine learning obsługuje następujące zadania uczenia Maszynowego:
* Klasyfikacja binarna
* Wieloklasowej klasyfikacji
* Regresji

## <a name="create-experiment-settings"></a>Utwórz ustawienia eksperymentu

Tworzenie eksperymentu ustawień dla określonego typu zadania uczenia Maszynowego:

* Klasyfikacja binarna

  ```csharp
  var experimentSettings = new BinaryExperimentSettings();
  ```

* Wieloklasowej klasyfikacji

  ```csharp
  var experimentSettings = new MulticlassExperimentSettings();
  ```

* Regresji

  ```csharp
  var experimentSettings = new RegressionExperimentSettings();
  ```

## <a name="configure-experiment-settings"></a>Konfigurowanie ustawień eksperymentu

Eksperymenty są wysoce konfigurowalne. Zobacz [dokumentacji interfejsu API AutoML](https://docs.microsoft.com/dotnet/api/?view=automl-dotnet) poznania pełnej listy ustawień konfiguracji.

Oto niektóre przykłady:

1. Określ maksymalny czas, w którym można uruchamiać eksperymentu.

    ```csharp
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    ```

1. Użyj token anulowania do anulowania doświadczenia, zanim jest zaplanowane na zakończenie.

    ```csharp
    experimentSettings.CancellationToken = cts.Token;

    // Cancel experiment after the user presses any key
    CancelExperimentAfterAnyKeyPress(cts);
    ```

1. Określ inną metrykę optymalizacji.

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.OptimizingMetric = RegressionMetric.MeanSquaredError;
    ```

1. `CacheDirectory` Ustawienie jest wskaźnikiem do katalogu, w którym zostaną zapisane wszystkie modele skonfigurowanych pod kątem podczas wykonywania zadania AutoML. Jeśli `CacheDirectory` jest ustawiona na wartość null, modele będą przechowywane w pamięci, a nie zapisane na dysku.
 
    ```csharp
    experimentSettings.CacheDirectory = null;
    ```

1. Poinstruuj ML automatycznego nie należy używać niektórych instruktorów.

    Domyślną listę instruktorów, aby zoptymalizować zbadano poszczególnych zadań. Dla każdego doświadczenia można zmodyfikować tej listy. Na przykład można usunąć z listy instruktorów, które spowolnienie działania na twoim zestawie danych. Do optymalizacji na jedno wywołanie dla określonych trenerów `experimentSettings.Trainers.Clear()`, następnie dodać instruktora, którego chcesz używać.

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.Trainers.Remove(RegressionTrainer.LbfgsPoissonRegression);
    experimentSettings.Trainers.Remove(RegressionTrainer.OnlineGradientDescent);
    ```

Lista obsługiwanych Instruktorzy każdego zadania uczenia Maszynowego znajduje się w temacie odpowiednie łącze poniżej:
* [Obsługiwane algorytmy Klasyfikacja binarna](xref:Microsoft.ML.AutoML.BinaryClassificationTrainer)
* [Obsługiwane algorytmy Wieloklasowej klasyfikacji](xref:Microsoft.ML.AutoML.MulticlassClassificationTrainer)
* [Regresja obsługiwane algorytmy](xref:Microsoft.ML.AutoML.RegressionTrainer)

## <a name="optimizing-metric"></a>Optymalizacja metryki

Optymalizacja metryki, jak pokazano w przykładzie powyżej, określa metryki można optymalizować podczas uczenia modelu. Optymalizacja metryki, które można wybrać, jest określana przez typ zadania, które wybierzesz. Poniżej znajduje się lista dostępnych metryk.

|[Klasyfikacja binarna](xref:Microsoft.ML.AutoML.BinaryClassificationMetric) | [Wieloklasowej klasyfikacji](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric) |[Regression](xref:Microsoft.ML.AutoML.RegressionMetric)
|-- |-- |--
|dokładność| LogLoss | RSquared
|AreaUnderPrecisionRecallCurve | LogLossReduction | MeanAbsoluteError
|AreaUnderRocCurve | MacroAccuracy | MeanSquaredError
|F1Score | MicroAccuracy | RootMeanSquaredError
|NegativePrecision | TopKAccuracy
|NegativeRecall |
|PositivePrecision
|PositiveRecall

## <a name="data-pre-processing-and-featurization"></a>Wstępne przetwarzanie danych i cechowania

Przetwarzanie wstępne danych miały domyślnie, a poniższe kroki są wykonywane automatycznie dla Ciebie:

1. Upuszczanie funkcji żadnych użytecznych informacji

    Usuwanie funkcji żadnych użytecznych informacji z zestawów szkolenia i sprawdzania poprawności. Obejmują one funkcje wszystkich wartości Brak, tę samą wartość we wszystkich wierszach lub bardzo dużej kardynalności (np. skróty, lub identyfikatory GUID).

1. Brak wskazania wartość i przypisywania

    Wypełnienie brakujących wartości komórek z wartością domyślną dla typu danych. Dołącz wskaźnik funkcji, korzystając z taką samą liczbę miejsc, jako kolumna danych wejściowych. Wartość w funkcji dołączonych wskaźnik jest `1` Jeśli brakuje wartości w kolumnie wejściowej i `0` inaczej.

1. Generuj dodatkowe funkcje
    
    Funkcje tekstowe: Funkcje zbioru programu word za pomocą unigrams i tri znak g.
    
    Podzielone na kategorie funkcji: Jeden hot-hash kodowanie funkcji podzielonych na kategorie wysoka Kardynalność klauzuli i hot jeden kodowania dla funkcji Kardynalność niski.

1. Przekształcenia i kodowania

    Funkcje tekstowe z bardzo niewielkiej liczbie unikatowych wartości przekształcone w kategorii funkcji. W zależności od kardynalności kategorii funkcji należy wykonać hot jeden kodowania lub hot jeden skrót kodowania.

## <a name="exit-criteria"></a>Kryteria wyjścia

Określ kryteria do ukończenia zadania:

1. Zakończ po przez długi czas — przy użyciu `MaxExperimentTimeInSeconds` w ustawieniach eksperymentu można zdefiniować, jak długo w ciągu kilku sekund, które zadania powinny nadal działać.

1. Zakończ token anulowania — mogą używać token anulowania, który pozwala anulować zadania, zanim jest zaplanowane na zakończenie.

    ```csharp
    var cts = new CancellationTokenSource();
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    experimentSettings.CancellationToken = cts.Token;
    ```

## <a name="create-an-experiment"></a>Tworzenie eksperymentu

Po skonfigurowaniu ustawień eksperymentu, możesz przystąpić do tworzenia eksperymentu.

```csharp
RegressionExperiment experiment = mlContext.Auto().CreateRegressionExperiment(experimentSettings);
```

## <a name="run-the-experiment"></a>Uruchamianie eksperymentu

Uruchamianie eksperymentu danych wyzwalaczy przetwarzania wstępnego, algorytm wybór i strojenia hiperparametrycznego uczenia. AutoML będą w dalszym ciągu kombinacji cechowania, algorytmów uczenia i hiperparametrów aż do wygenerowania `MaxExperimentTimeInSeconds` osiągnięciu lub eksperymentu zostanie zakończony.

```csharp
ExperimentResult<RegressionMetrics> experimentResult = experiment
    .Execute(trainingDataView, LabelColumnName, progressHandler: progressHandler);
```

Poznaj inne przeciążenia `Execute()` jeśli mają być przekazywane sprawdzania poprawności danych, wskazując przeznaczenie kolumny lub prefeaturizers informacji o kolumnie.

## <a name="training-modes"></a>Tryby szkolenia

### <a name="training-dataset"></a>Zestaw danych szkoleniowych

AutoML zapewnia przeciążone eksperymentu Wykonaj metodę, która umożliwia przekazanie danych szkoleniowych. Wewnętrznie zautomatyzowane ML dzieli dane na train-validate dzieli dane.

```csharp
experiment.Execute(trainDataView);   
```

### <a name="custom-validation-dataset"></a>Zestaw niestandardowego sprawdzania poprawności danych

Użyj zestawu niestandardowego sprawdzania poprawności danych, jeśli losowe podziału nie jest dopuszczalne, tak jak zwykle w przypadku przy użyciu danych szeregów czasowych. Można określić własnego zestawu danych walidacji. Model zostaną ocenione względem zestawu danych walidacji, zamiast jednego lub więcej losowych zestawów danych.

```csharp
experiment.Execute(trainDataView, validationDataView);   
```

## <a name="explore-model-metrics"></a>Eksplorowanie metryk modelu

Po każdej iteracji eksperymentu uczenia Maszynowego metryki odnoszące się do tego zadania są przechowywane.

Na przykład firma Microsoft jest dostępna metryki weryfikacji najlepszy przebieg:

```csharp
RegressionMetrics metrics = experimentResult.BestRun.ValidationMetrics;
Console.WriteLine($"R-Squared: {metrics.RSquared:0.##}");
Console.WriteLine($"Root Mean Squared Error: {metrics.RootMeanSquaredError:0.##}");
```

Poniżej wymieniono wszystkie dostępne metryki dla zadania uczenia Maszynowego:
* [Klasyfikacja binarna metryki](xref:Microsoft.ML.AutoML.BinaryClassificationMetric)
* [Metryki klasyfikacji wieloklasowej](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric)
* [Metryki regresji](xref:Microsoft.ML.AutoML.RegressionMetric)

## <a name="see-also"></a>Zobacz także

Przykłady pełnego kodu i nie tylko można znaleźć [machinelearning-dotnet-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) repozytorium GitHub.
