---
title: Ponowne trenowanie modelu
description: Dowiedz się, jak ponownie nauczyć model w ML.NET
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 735782a4a0877a917b6e1885f009aa49d834170f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976965"
---
# <a name="re-train-a-model"></a>Ponowne trenowanie modelu

Dowiedz się, jak ponownie przeprowadzić uczenie modelu uczenia maszynowego w programie ML.NET.

Na całym świecie dane zmieniają się w stałym tempie. W związku z tym modele muszą ulec zmianie i zaktualizować. ML.NET oferuje funkcje dla modeli do ponownego uczenia przy użyciu parametrów modelu, które są punktem wyjścia do ciągłego kompilowania na podstawie poprzedniego środowiska, zamiast rozpoczynać się za każdym razem.

Następujące algorytmy są ponownie pouczeni w ML.NET:

- [AveragedPerceptronTrainer](xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer)
- [FieldAwareFactorizationMachineTrainer](xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer)
- [LbfgsLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer)
- [LbfgsMaximumEntropyMulticlassTrainer](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer)
- [LbfgsPoissonRegressionTrainer](xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer)
- [LinearSvmTrainer](xref:Microsoft.ML.Trainers.LinearSvmTrainer)
- [OnlineGradientDescentTrainer](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer)
- [SgdCalibratedTrainer](xref:Microsoft.ML.Trainers.SgdCalibratedTrainer)
- [SgdNonCalibratedTrainer](xref:Microsoft.ML.Trainers.SgdNonCalibratedTrainer)
- [SymbolicSgdLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer)

## <a name="load-pre-trained-model"></a>Załaduj wstępnie szkolony model

Najpierw Załaduj wstępnie szkolony model do aplikacji. Aby dowiedzieć się więcej na temat ładowania potoków szkoleń i modeli, zobacz [Zapisywanie i ładowanie nauczonego modelu](save-load-machine-learning-models-ml-net.md).

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define DataViewSchema of data prep pipeline and trained model
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip", out dataPrepPipelineSchema);

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("ogd_model.zip", out modelSchema);
```

## <a name="extract-pre-trained-model-parameters"></a>Wyodrębnij wstępnie przeszkolone parametry modelu

Po załadowaniu modelu Wyodrębnij uzyskane parametry modelu, uzyskując dostęp do właściwości [`Model`](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) wstępnie nauczonego modelu. Model z góry szkolony został przeszkolony przy użyciu modelu regresji liniowej [`OnlineGradientDescentTrainer`](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) , który tworzy[`RegressionPredictionTransformer`](xref:Microsoft.ML.Data.RegressionPredictionTransformer%601) , który wyprowadza [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters). Te parametry modelu regresji liniowej zawierają rozmieszczoną wagę i wagi lub współczynniki modelu. Te wartości będą używane jako punkt wyjścia dla nowego modelu ponownie szkolony.

```csharp
// Extract trained model parameters
LinearRegressionModelParameters originalModelParameters =
    ((ISingleFeaturePredictionTransformer<object>)trainedModel).Model as LinearRegressionModelParameters;
```

## <a name="re-train-model"></a>Model ponownego uczenia

Proces ponownego szkolenia modelu nie różni się od poziomu szkolenia modelu. Jedyną różnicą jest to, że metoda [`Fit`](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*) oprócz danych również przyjmuje jako dane wejściowe parametry oryginalnych informacji o modelu i używa ich jako punktu wyjścia w procesie ponownego uczenia.

```csharp
// New Data
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f,175000f,210000f },
        CurrentPrice = 205000f
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f },
        CurrentPrice = 210000f
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f },
        CurrentPrice = 180000f
    }
};

//Load New Data
IDataView newData = mlContext.Data.LoadFromEnumerable<HousingData>(housingData);

// Preprocess Data
IDataView transformedNewData = dataPrepPipeline.Transform(newData);

// Retrain model
RegressionPredictionTransformer<LinearRegressionModelParameters> retrainedModel =
    mlContext.Regression.Trainers.OnlineGradientDescent()
        .Fit(transformedNewData, originalModelParameters);
```

## <a name="compare-model-parameters"></a>Porównaj parametry modelu

Jak można sprawdzić, czy ponowne szkolenie rzeczywiście się zaszło? Jednym ze sposobów jest porównanie, czy parametry modelu, który został przeszkolony, różnią się od modelu oryginalnego. Poniższy przykład kodu porównuje oryginalny z odszkolonymi wagami modelu i wyprowadza je do konsoli.

```csharp
// Extract Model Parameters of re-trained model
LinearRegressionModelParameters retrainedModelParameters = retrainedModel.Model as LinearRegressionModelParameters;

// Inspect Change in Weights
var weightDiffs =
    originalModelParameters.Weights.Zip(
        retrainedModelParameters.Weights, (original, retrained) => original - retrained).ToArray();

Console.WriteLine("Original | Retrained | Difference");
for(int i=0;i < weightDiffs.Count();i++)
{
    Console.WriteLine($"{originalModelParameters.Weights[i]} | {retrainedModelParameters.Weights[i]} | {weightDiffs[i]}");
}
```

W poniższej tabeli pokazano, jak dane wyjściowe mogą wyglądać podobnie.

|Oryginał | Przeszkol ponownie | Występują |
|---|---|---|
| 33039,86 | 56293,76 | -23253,9 |
| 29099,14 | 49586,03 | -20486,89 |
| 28938,38 | 48609,23 | -19670,85 |
| 30484,02 | 53745,43 | -23261,41 |
