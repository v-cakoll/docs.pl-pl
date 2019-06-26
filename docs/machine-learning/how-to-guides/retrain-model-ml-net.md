---
title: Ponowne trenowanie modelu
description: Dowiedz się, jak ponowne szkolenie modelu w strukturze ML.NET
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 1628d0669d8a9e677ff39b5869d3802d89d96410
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397702"
---
# <a name="re-train-a-model"></a>Ponowne trenowanie modelu

Dowiedz się, jak doskonalenie model w strukturze ML.NET uczenia maszynowego.

Na świecie i danych wokół niej zmienić tempie stałej. Jako takie Zmień i zaktualizuj również konieczne modeli. Strukturze ML.NET udostępnia funkcje Ponowne szkolenie modeli za pomocą przedstawiono parametry modelu jako punktu wyjścia ciągle tworzyć na poprzednie środowisko, a nie od zera, każdym razem.  

Następujące algorytmy są ponownie trainable w strukturze ML.NET:

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

## <a name="load-pre-trained-model"></a>Załaduj wstępnie przeszkolonych model

Najpierw Załaduj wstępnie uczonego modelu w aplikacji. Aby dowiedzieć się więcej na temat ładowania potokami szkolenia i modeli, zobacz powiązane [instrukcje](./consuming-model-ml-net.md).

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

## <a name="extract-pre-trained-model-parameters"></a>Wyodrębnianie parametrów wstępnie uczonego modelu

Po załadowaniu modelu wyodrębnić parametry nauczony model, uzyskując dostęp do [ `Model` ](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) właściwość wstępnie trenowanego modelu. Wstępnie przeszkolonych model został uczony przy użyciu modelu regresji liniowej [ `OnlineGradientDescentTrainer` ](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) tworzy[ `RegressionPredictionTransformer` ](xref:Microsoft.ML.Data.RegressionPredictionTransformer%601) , generuje [ `LinearRegressionModelParameters` ](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters). Te parametry modelu regresji liniowej zawierają nauczony odchylenie i wagi lub współczynników w modelu. Te wartości będzie służyć jako punkt początkowy dla nowych ponownie trenowanego modelu.

```csharp
// Extract trained model parameters
LinearRegressionModelParameters originalModelParameters = 
    ((ISingleFeaturePredictionTransformer<object>)trainedModel).Model as LinearRegressionModelParameters;
```

## <a name="re-train-model"></a>Ponowne szkolenie modelu

Proces ponownego szkolenia modelu nie różni się niż uczenia modelu. Jedyna różnica polega na, [ `Fit` ](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*) metoda oprócz danych również przyjmuje jako dane wejściowe, oryginalnym przedstawiono parametry modelu i wykorzystuje je jako początkowy punkt w procesie ponownego szkolenia.  

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

Jak można sprawdzić, czy ponowne szkolenie się faktycznie stało? Jednym ze sposobów byłoby porównać czy ponownie uczonego modelu parametry są inne niż te, oryginalnym modelu. Poniższy przykład kodu porównuje oryginalny względem wagi ponownie uczonego modelu i wysyła je do konsoli.

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

W poniższej tabeli przedstawiono, jak może wyglądać dane wyjściowe. 

|Oryginał | Retrained | Różnica |
|---|---|---|
| 33039.86 | 56293.76 | -23253.9 |
| 29099.14 | 49586.03 | -20486.89 |
| 28938.38 | 48609.23 | -19670.85 |
| 30484.02 | 53745.43 | -23261.41 |
