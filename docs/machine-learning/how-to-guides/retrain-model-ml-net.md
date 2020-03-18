---
title: Ponowne trenowanie modelu
description: Dowiedz się, jak przekwalifikować model w ML.NET
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 735782a4a0877a917b6e1885f009aa49d834170f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73976965"
---
# <a name="re-train-a-model"></a>Ponowne trenowanie modelu

Dowiedz się, jak ponownie trenować model uczenia maszynowego w ML.NET.

Świat i dane wokół niego zmieniają się w stałym tempie. W związku z tym modele muszą również ulec zmianie i zaktualizować. ML.NET udostępnia funkcje dla modeli ponownego szkolenia przy użyciu wyuczonych parametrów modelu jako punkt wyjścia do ciągłego korzystania z poprzednich doświadczeń, a nie począwszy od zera za każdym razem.

Następujące algorytmy można ponownie nabyć w ML.NET:

- [Trener UśrednionyPerceptron](xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer)
- [FieldAwareFactorizationMachineTrainer](xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer)
- [LbfgsLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer)
- [LbfgsMaximumEntropyMultiClassTrainer](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer)
- [LbfgsPoissonTrener regresu](xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer)
- [LinearSvmTrainer (LinearSvmTrainer)](xref:Microsoft.ML.Trainers.LinearSvmTrainer)
- [OnlineGradientDescentTrainer](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer)
- [SgdCalibratedTrainer](xref:Microsoft.ML.Trainers.SgdCalibratedTrainer)
- [SgdNonCalibratedTrainer](xref:Microsoft.ML.Trainers.SgdNonCalibratedTrainer)
- [SymbolicSgdLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer)

## <a name="load-pre-trained-model"></a>Załaduj wstępnie przeszkolony model

Najpierw załaduj wstępnie przeszkolony model do aplikacji. Aby dowiedzieć się więcej na temat ładowania potoków szkoleniowych i modeli, zobacz [Zapisywanie i ładowanie uczonego modelu](save-load-machine-learning-models-ml-net.md).

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

## <a name="extract-pre-trained-model-parameters"></a>Wyodrębnianie wstępnie przeszkolonych parametrów modelu

Po załadowaniu modelu wyodrębnij parametry modelu, [`Model`](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) uzyskując dostęp do właściwości wstępnie uczonego modelu. Wstępnie przeszkolony model został przeszkolony [`OnlineGradientDescentTrainer`](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) przy użyciu[`RegressionPredictionTransformer`](xref:Microsoft.ML.Data.RegressionPredictionTransformer%601) modelu [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters)regresji liniowej, który tworzy, że wyjścia . Te parametry modelu regresji liniowej zawierają wyuczoną stronniczość i wagi lub współczynniki modelu. Wartości te będą używane jako punkt wyjścia dla nowego modelu ponownie przeszkolony.

```csharp
// Extract trained model parameters
LinearRegressionModelParameters originalModelParameters =
    ((ISingleFeaturePredictionTransformer<object>)trainedModel).Model as LinearRegressionModelParameters;
```

## <a name="re-train-model"></a>Przetrain model

Proces przekwalifikowania modelu nie różni się od szkolenia modelu. Jedyną różnicą [`Fit`](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*) jest metoda oprócz danych również przyjmuje jako dane wejściowe oryginalne parametry modelu wyuczonego i używa ich jako punkt wyjścia w procesie ponownego szkolenia.

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

## <a name="compare-model-parameters"></a>Porównanie parametrów modelu

Skąd wiesz, czy przekwalifikowanie rzeczywiście się stało? Jednym ze sposobów byłoby porównanie, czy parametry ponownie przeszkolonego modelu różnią się od parametrów oryginalnego modelu. Poniższy przykład kodu porównuje oryginał z przekwalifikowanymi wagami modelu i wyprowadza je do konsoli.

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

W poniższej tabeli pokazano, jak może wyglądać dane wyjściowe.

|Oryginał | Przekwalifikowany | Różnica |
|---|---|---|
| 33039.86 | 56293.76 | -23253.9 |
| 29099.14 | 49586.03 | -20486.89 |
| 28938.38 | 48609.23 | -19670.85 |
| 30484.02 | 53745.43 | -23261.41 |
