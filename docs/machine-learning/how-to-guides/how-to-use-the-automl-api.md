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
# <a name="how-to-use-the-mlnet-automated-machine-learning-api"></a>Jak korzystać z ML.NET automatycznego interfejsu API uczenia maszynowego

Automatyczne uczenie maszynowe (AutoML) automatyzuje proces stosowania uczenia maszynowego do danych. Biorąc pod uwagę zestaw danych, można uruchomić **eksperyment** AutoML, aby iterate nad różnymi featurizations danych, algorytmów uczenia maszynowego i hiperparametrów, aby wybrać najlepszy model.

> [!NOTE]
> Ten temat odnosi się do interfejsu API automatycznego uczenia maszynowego dla ML.NET, który jest obecnie w wersji zapoznawczej. Materiał może ulec zmianie.

## <a name="load-data"></a>Ładowanie danych

Automatyczne uczenie maszynowe obsługuje ładowanie zestawu danych do [widoku IDataView](xref:Microsoft.ML.IDataView). Dane mogą być w postaci plików wartości rozdzielonych kartami (TSV) i plików wartości oddzielonych przecinkami (CSV).

Przykład:

```csharp
using Microsoft.ML;
using Microsoft.ML.AutoML;
    // ...
    MLContext mlContext = new MLContext();
    IDataView trainDataView = mlContext.Data.LoadFromTextFile<SentimentIssue>("my-data-file.csv", hasHeader: true);
```

## <a name="select-the-machine-learning-task-type"></a>Wybierz typ zadania uczenia maszynowego

Przed utworzeniem eksperymentu należy określić rodzaj problemu z uczeniem maszynowym, który chcesz rozwiązać. Automatyczne uczenie maszynowe obsługuje następujące zadania w celu połączenia maszynowego:

* Klasyfikacja binarna
* Klasyfikacja wieloklasowa
* Regresja
* Zalecenie

## <a name="create-experiment-settings"></a>Tworzenie ustawień eksperymentu

Utwórz ustawienia eksperymentu dla określonego typu zadania ML:

* Klasyfikacja binarna

  ```csharp
  var experimentSettings = new BinaryExperimentSettings();
  ```

* Klasyfikacja wieloklasowa

  ```csharp
  var experimentSettings = new MulticlassExperimentSettings();
  ```

* Regresja

  ```csharp
  var experimentSettings = new RegressionExperimentSettings();
  ```

* Zalecenie

  ```csharp
  var experimentSettings = new RecommendationExperimentSettings();
  ```

## <a name="configure-experiment-settings"></a>Konfigurowanie ustawień eksperymentu

Eksperymenty są wysoce konfigurowalne. Zobacz [dokumenty interfejsu API AutoML,](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl?view=ml-dotnet-preview) aby uzyskać pełną listę ustawień konfiguracji.

Oto niektóre przykłady:

1. Określ maksymalny czas, przez jaki eksperyment może zostać uruchomiony.

    ```csharp
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    ```

1. Użyj tokenu anulowania, aby anulować eksperyment przed jego zakończeniem.

    ```csharp
    experimentSettings.CancellationToken = cts.Token;

    // Cancel experiment after the user presses any key
    CancelExperimentAfterAnyKeyPress(cts);
    ```

1. Określ inną metrykę optymalizującą.

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.OptimizingMetric = RegressionMetric.MeanSquaredError;
    ```

1. Ustawienie `CacheDirectory` jest wskaźnikiem do katalogu, w którym zostaną zapisane wszystkie modele przeszkolone podczas wykonywania zadania AutoML. Jeśli `CacheDirectory` jest ustawiona na null, modele będą przechowywane w pamięci, a nie zapisywane na dysku.

    ```csharp
    experimentSettings.CacheDirectory = null;
    ```

1. Poinstruować zautomatyzowane ML, aby nie używało niektórych trenerów.

    Domyślna lista trenerów do optymalizacji są eksplorowane na zadanie. Tę listę można zmodyfikować dla każdego eksperymentu. Na przykład trenerów, które działają powoli na zestaw danych można usunąć z listy. Aby zoptymalizować na `experimentSettings.Trainers.Clear()`jednym konkretnym wywołaniu trenera, a następnie dodać trenera, którego chcesz użyć.

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.Trainers.Remove(RegressionTrainer.LbfgsPoissonRegression);
    experimentSettings.Trainers.Remove(RegressionTrainer.OnlineGradientDescent);
    ```

Listę obsługiwanych trenerów na zadanie ML można znaleźć pod odpowiednim linkiem poniżej:

* [Obsługiwane algorytmy klasyfikacji binarnej](xref:Microsoft.ML.AutoML.BinaryClassificationTrainer)
* [Obsługiwane algorytmy klasyfikacji wieloklasowej](xref:Microsoft.ML.AutoML.MulticlassClassificationTrainer)
* [Obsługiwane algorytmy regresji](xref:Microsoft.ML.AutoML.RegressionTrainer)
* [Obsługiwane algorytmy rekomendacji](xref:Microsoft.ML.AutoML.RecommendationTrainer)

## <a name="optimizing-metric"></a>Optymalizacja metryki

Metryka optymalizacji, jak pokazano w powyższym przykładzie, określa metrykę, która ma być zoptymalizowana podczas szkolenia modelu. Metryka optymalizująca, którą można wybrać, zależy od wybranego typu zadania. Poniżej znajduje się lista dostępnych danych.

|[Klasyfikacja binarna](xref:Microsoft.ML.AutoML.BinaryClassificationMetric) | [Klasyfikacja wieloklasowa](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric) |[Zalecenie & regresji](xref:Microsoft.ML.AutoML.RegressionMetric)
|-- |-- |--
|Dokładność| LogLoss (Strata logów) | RSquared (kwadrat)
|AreaUnderPrecisionRecallCurve (Krzywa niedostatecznie przypomnę) | LogLossReduction (Redukcja loglossów) | MeanAbsoluteError (MeanAbsoluteError)
|AreaUnderRocCurve (ObszarUnderrocCurve) | Dokładność makra | Błąd MeanSquaredError
|Wynik F1 | Mikrodokładność | Błąd RootMeanSquaredError
|Ujemna precyzja | Dokładność Topk
|NegatywnePrzywołanie |
|Dodatnia dokładność
|PozytywnePrzywołanie

## <a name="data-pre-processing-and-featurization"></a>Wstępne przetwarzanie danych i featurization

> [!NOTE]
> Kolumna funkcji obsługiwane tylko <xref:System.Boolean> <xref:System.Single>typy <xref:System.String>, i .

Przetwarzanie wstępne danych odbywa się domyślnie, a następujące kroki są wykonywane automatycznie dla Ciebie:

1. Funkcje upuszczenia bez przydatnych informacji

    Funkcje upuść bez przydatnych informacji z zestawów szkoleniowych i sprawdzania poprawności. Należą do nich funkcje ze wszystkimi brakującymi wartościami, tą samą wartością we wszystkich wierszach lub o bardzo wysokiej kardynalności (np. haszysze, identyfikatory lub identyfikatory GUID).

1. Brakujące wskazanie wartości i przypisania

    Wypełnij brakujące komórki wartości wartości wartości wartością domyślną dla typu danych. Dołącz funkcje wskaźnika z taką samą liczbą gniazd jak kolumna wprowadzania. Wartość w dołączonych funkcji `1` wskaźnika jest, jeśli brakuje `0` wartości w kolumnie wejściowej i w przeciwnym razie.

1. Generowanie dodatkowych funkcji

    Funkcje tekstowe: Funkcje worka z wyrazami przy użyciu unigramów i trzech znaków-gramów.

    W przypadku funkcji kategorii: kodowanie na gorąco dla funkcji o niskiej kardynalności i kodowanie skrótu jeden-hot-hash dla funkcji kategorii wysokiej kardynalności.

1. Przekształcenia i kodowanie

    Funkcje tekstowe z bardzo nielicznymi unikatowymi wartościami przekształcone w funkcje kategoryczne. W zależności od kardynalności funkcji kategorycznych wykonaj kodowanie jedno-gorące lub kodowanie skrótu jeden-hot.

## <a name="exit-criteria"></a>Kryteria wyjścia

Zdefiniuj kryteria, aby wykonać zadanie:

1. Zakończ po upływie `MaxExperimentTimeInSeconds` czasu — za pomocą w ustawieniach eksperymentu można zdefiniować, jak długo w sekundach, że zadanie powinno być kontynuowane.

1. Zakończ na tokenanulowania — można użyć tokenu anulowania, który pozwala anulować zadanie, zanim zostanie zaplanowane do zakończenia.

    ```csharp
    var cts = new CancellationTokenSource();
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    experimentSettings.CancellationToken = cts.Token;
    ```

## <a name="create-an-experiment"></a>Tworzenie eksperymentu

Po skonfigurowaniu ustawień eksperymentu można przystąpić do tworzenia eksperymentu.

```csharp
RegressionExperiment experiment = mlContext.Auto().CreateRegressionExperiment(experimentSettings);
```

## <a name="run-the-experiment"></a>Uruchamianie eksperymentu

Uruchomienie eksperymentu wyzwala przetwarzanie wstępne danych, wybór algorytmu uczenia i dostrajanie hiperparametrów. AutoML będzie nadal generować kombinacje featurization, algorytmy uczenia `MaxExperimentTimeInSeconds` się i hiperparametrów, dopóki nie zostanie osiągnięty lub eksperyment zostanie zakończony.

```csharp
ExperimentResult<RegressionMetrics> experimentResult = experiment
    .Execute(trainingDataView, LabelColumnName, progressHandler: progressHandler);
```

Eksploruj inne przeciążenia, `Execute()` jeśli chcesz przekazać dane sprawdzania poprawności, informacje o kolumnie wskazujące cel kolumny lub prefeaturizers.

## <a name="training-modes"></a>Tryby treningowe

### <a name="training-dataset"></a>Zestaw danych szkoleniowych

Automl udostępnia przeciążoną metodę wykonywania eksperymentu, która umożliwia dostarczanie danych szkoleniowych. Wewnętrznie zautomatyzowany ml dzieli dane na podziały sprawdzania poprawności pociągu.

```csharp
experiment.Execute(trainDataView);
```

### <a name="custom-validation-dataset"></a>Niestandardowy zestaw danych sprawdzania poprawności

Użyj niestandardowego zestawu danych sprawdzania poprawności, jeśli losowy podział nie jest dopuszczalny, jak to zwykle bywa w przypadku danych szeregów czasowych. Można określić własny zestaw danych sprawdzania poprawności. Model zostanie oceniony względem zestawu danych sprawdzania poprawności określonego zamiast jednego lub więcej losowych zestawów danych.

```csharp
experiment.Execute(trainDataView, validationDataView);
```

## <a name="explore-model-metrics"></a>Eksplorowanie danych modelu

Po każdej iteracji eksperymentu ML są przechowywane metryki odnoszące się do tego zadania.

Na przykład możemy uzyskać dostęp do metryk sprawdzania poprawności z najlepszego przebiegu:

```csharp
RegressionMetrics metrics = experimentResult.BestRun.ValidationMetrics;
Console.WriteLine($"R-Squared: {metrics.RSquared:0.##}");
Console.WriteLine($"Root Mean Squared Error: {metrics.RootMeanSquaredError:0.##}");
```

Poniżej przedstawiono wszystkie dostępne metryki dla zadania ml:

* [Metryki klasyfikacji binarnej](xref:Microsoft.ML.AutoML.BinaryClassificationMetric)
* [Wieloklasowe metryki klasyfikacji](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric)
* [Wskaźniki rekomendacji & regresji](xref:Microsoft.ML.AutoML.RegressionMetric)

## <a name="see-also"></a>Zobacz też

Aby uzyskać pełne próbki kodu i więcej odwiedź repozytorium GitHub dotnet/machinelearning.For full code samples and more visit the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) GitHub repository.
