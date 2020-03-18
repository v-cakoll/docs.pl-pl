---
title: Wprowadzaj prognozy za pomocą przeszkolonego modelu
description: Naucz się przewidywać przy użyciu uczonego modelu
ms.date: 09/18/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 182350cc5143155133385c6fd77986b271f6db91
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73977048"
---
# <a name="make-predictions-with-a-trained-model"></a>Wprowadzaj prognozy za pomocą przeszkolonego modelu

Dowiedz się, jak używać uczonego modelu do tworzenia prognoz

## <a name="create-data-models"></a>Tworzenie modeli danych

### <a name="input-data"></a>Dane wejściowe

```csharp
public class HousingData
{
    [LoadColumn(0)]
    public float Size { get; set; }

    [LoadColumn(1, 3)]
    [VectorType(3)]
    public float[] HistoricalPrices { get; set; }

    [LoadColumn(4)]
    [ColumnName("Label")]
    public float CurrentPrice { get; set; }
}
```

### <a name="output-data"></a>Dane wyjściowe

Podobnie `Features` jak `Label` nazwy kolumn wejściowych, ML.NET ma domyślne nazwy kolumn wartości przewidywanej produkowane przez model. W zależności od zadania nazwa może się różnić.

Ponieważ algorytm używany w tym przykładzie jest algorytm regresji liniowej, domyślna nazwa kolumny wyjściowej jest, `Score` który jest zdefiniowany przez [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) atrybut we `PredictedPrice` właściwości.

```csharp
class HousingPrediction
{
    [ColumnName("Score")]
    public float PredictedPrice { get; set; }
}
```

## <a name="set-up-a-prediction-pipeline"></a>Konfigurowanie potoku prognozowania

Niezależnie od tego, czy dokonywanie pojedynczej lub wsadowe przewidywanie, potoku przewidywania musi zostać załadowany do aplikacji. Ten potok zawiera zarówno przekształcenia przetwarzania wstępnego danych, jak również uczonego modelu. Poniższy fragment kodu ładuje potok przewidywania `model.zip`z pliku o nazwie .

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Load Trained Model
DataViewSchema predictionPipelineSchema;
ITransformer predictionPipeline = mlContext.Model.Load("model.zip", out predictionPipelineSchema);
```

## <a name="single-prediction"></a>Pojedyncza prognoza

Aby utworzyć pojedyncze przewidywanie, utwórz [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) przy użyciu załadowanego potoku prognozowania.

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

Następnie należy [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) użyć metody i przekazać dane wejściowe jako parametr. Należy zauważyć, [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) że przy użyciu metody [`IDataView`](xref:Microsoft.ML.IDataView)nie wymaga danych wejściowych, aby być ). Dzieje się tak, ponieważ wygodnie internalizuje manipulacji typu danych wejściowych, dzięki czemu można przekazać w obiekcie typu danych wejściowych. Ponadto ponieważ `CurrentPrice` jest obiektem docelowym lub etykietą, którą próbujesz przewidzieć przy użyciu nowych danych, zakłada się, że w tej chwili nie ma dla niego żadnej wartości.

```csharp
// Input Data
HousingData inputData = new HousingData
{
    Size = 900f,
    HistoricalPrices = new float[] { 155000f, 190000f, 220000f }
};

// Get Prediction
HousingPrediction prediction = predictionEngine.Predict(inputData);
```

Jeśli uzyskujesz dostęp do `Score` właściwości `prediction` obiektu, `150079`powinna zostać uzyskana wartość podobna do .

## <a name="multiple-predictions"></a>Wiele prognoz

Biorąc pod uwagę następujące dane, załaduj je do pliku [`IDataView`](xref:Microsoft.ML.IDataView). W takim przypadku nazwa [`IDataView`](xref:Microsoft.ML.IDataView) jest `inputData`. Ponieważ `CurrentPrice` jest to cel lub etykieta, którą próbujesz przewidzieć przy użyciu nowych danych, zakłada się, że w tej chwili nie ma dla niego żadnej wartości.

```csharp
// Actual data
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f, 175000f, 210000f }
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f }
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f }
    }
};
```

Następnie użyj [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) metody, aby zastosować przekształcenia danych i wygenerować prognozy.

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

Sprawdź przewidywane wartości przy [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) użyciu metody.

```csharp
// Get Predictions
float[] scoreColumn = predictions.GetColumn<float>("Score").ToArray();
```

Przewidywane wartości w kolumnie wyników powinny wyglądać następująco:

| Obserwacji | Prediction (Prognoza) |
|---|---|
| 1 | 144638.2 |
| 2 | 150079.4 |
| 3 | 107789.8 |
