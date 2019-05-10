---
title: Tworzyć prognozy przy użyciu uczonego modelu
description: Dowiedz się, jak tworzyć prognozy przy użyciu uczonego modelu
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: dac3b3bfa68776975a2e5e762f46db16e39d61fb
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65066176"
---
# <a name="make-predictions-with-a-trained-model"></a>Tworzyć prognozy przy użyciu uczonego modelu

Dowiedz się, jak używać uczonego modelu do prognozowania

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

Podobnie jak `Features` i `Label` nazwy kolumn danych wejściowych, strukturze ML.NET ma domyślne nazwy dla kolumny przewidzianej wartości zwracane przez model. Zależności od zadania, nazwa może się różnić.

Ponieważ algorytm używany w tym przykładzie jest to algorytm regresji liniowej, domyślna nazwa kolumny wyjściowej to `Score` który jest definiowany przez [ `ColumnName` ](xref:Microsoft.ML.Data.ColumnNameAttribute) atrybutu na `PredictedPrice` właściwości.

```csharp
class HousingPrediction : HousingData
{
    [ColumnName("Score")]
    public float PredictedPrice { get; set; }
}
```

`HousingPrediction` Modelu danych, o których dziedziczy `HousingData` ułatwia wizualizowanie oryginalne dane wejściowe dane oraz dane wyjściowe generowane przez model.  

## <a name="set-up-a-prediction-pipeline"></a>Skonfiguruj potok prognoz

Czy wprowadzania pojedynczego lub prognoz usługi batch, prognozowanie potoku musi być ładowane do aplikacji. Ten potok zawiera zarówno przetwarzania wstępnego przekształcenia danych, jak i trenowanego modelu. Poniższy fragment kodu ładuje potoku prognozowania z pliku o nazwie `model.zip`.

```csharp
//Create MLContext 
MLContext mlContext = new MLContext();

// Load Trained Model
DataViewSchema predictionPipelineSchema;
ITransformer predictionPipeline = mlContext.Model.Load("model.zip", out predictionPipelineSchema);
```

## <a name="single-prediction"></a>Pojedynczy prognoz

Przewiduje jednego, Utwórz [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602) przy użyciu potoku załadować prognozy.

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

Następnie należy użyć [ `Predict` ](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) metody i przekazać w danych wejściowych jako parametr. Należy zauważyć, że używanie [ `Predict` ](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) metoda nie wymaga danych wejściowych jako [ `IDataView` ](xref:Microsoft.ML.IDataView)). Jest to spowodowane wygodnie program internalizes manipulowania typu danych wejściowych, dzięki czemu można przekazać obiekt typu danych wejściowych. Ponadto ponieważ `CurrentPrice` docelowego lub etykiety, które próbujesz przewidzieć, przy użyciu nowych danych, zakłada się, w tym momencie nie istnieje dla niego wartość.

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

Jeśli uzyskujesz dostęp do `Score` właściwość `prediction` obiektu, należy uzyskać podobny do wartości `150079`.

## <a name="batch-prediction"></a>Prognozy usługi Batch

Biorąc pod uwagę następujące dane, ładować je do [ `IDataView` ](xref:Microsoft.ML.IDataView). Ponieważ `CurrentPrice` docelowego lub etykiety, które próbujesz przewidzieć, przy użyciu nowych danych, zakłada się, w tym momencie nie istnieje dla niego wartość.

```csharp
// Actual data
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f,175000f,210000f }
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

Następnie należy użyć [ `Transform` ](xref:Microsoft.ML.ITransformer.Transform*) metodę, aby zastosować przekształceń danych oraz generować przewidywania.

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

Sprawdź przewidywane wartości za pomocą [ `GetColumn` ](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) metody.

```csharp
// Get Predictions
float[] scoreColumn = predictions.GetColumn<float>("Score").ToArray();
```

Przewidywane wartości w kolumnie wynik powinien wyglądać następująco:

| Obserwowanie | Prognozy |
|---|---|
| 1 | 144638.2 |
| 2 | 150079.4 |
| 3 | 107789.8 |
