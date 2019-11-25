---
title: Tworzenie prognoz przy użyciu przeszkolonego modelu
description: Dowiedz się, jak tworzyć prognozy przy użyciu przeszkolonego modelu
ms.date: 09/18/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 182350cc5143155133385c6fd77986b271f6db91
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977048"
---
# <a name="make-predictions-with-a-trained-model"></a>Tworzenie prognoz przy użyciu przeszkolonego modelu

Dowiedz się, jak tworzyć prognozy przy użyciu przeszkolonego modelu

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

Podobnie jak `Features` i `Label` nazw kolumn wejściowych, ML.NET ma domyślne nazwy dla kolumn wartości przewidywanych produkowanych przez model. W zależności od zadania, którego nazwa może się różnić.

Ponieważ algorytm używany w tym przykładzie jest algorytmem regresji liniowej, domyślną nazwą kolumny wyjściowej jest `Score`, która jest definiowana przez atrybut [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) właściwości `PredictedPrice`.

```csharp
class HousingPrediction
{
    [ColumnName("Score")]
    public float PredictedPrice { get; set; }
}
```

## <a name="set-up-a-prediction-pipeline"></a>Konfigurowanie potoku prognozowania

Niezależnie od tego, czy dokonywana jest prognoza pojedyncza, czy wsadowa, należy załadować potok przewidywania do aplikacji. Ten potok zawiera zarówno przekształcenia wstępnego przetwarzania danych, jak i przeszkolony model. Poniższy fragment kodu ładuje potok przewidywania z pliku o nazwie `model.zip`.

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Load Trained Model
DataViewSchema predictionPipelineSchema;
ITransformer predictionPipeline = mlContext.Model.Load("model.zip", out predictionPipelineSchema);
```

## <a name="single-prediction"></a>Pojedyncze prognozowanie

Aby wykonać pojedyncze prognozowanie, Utwórz [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) przy użyciu załadowanego potoku predykcyjnego.

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

Następnie użyj metody [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) i Przekaż dane wejściowe jako parametr. Należy zauważyć, że użycie metody [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) nie wymaga, aby dane wejściowe były [`IDataView`](xref:Microsoft.ML.IDataView)). Jest to spowodowane tym, że wygodnie internalizes manipulowanie danymi typu danych wejściowych, aby można było przekazać obiekt typu danych wejściowych. Ponadto, ponieważ `CurrentPrice` jest obiektem docelowym lub etykietą, którą próbujesz przewidzieć przy użyciu nowych danych, zakłada się, że nie ma w tej chwili żadnej wartości.

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

W przypadku uzyskania dostępu do właściwości `Score` obiektu `prediction` należy uzyskać wartość podobną do `150079`.

## <a name="multiple-predictions"></a>Wiele prognoz

Uwzględniając poniższe dane, załaduj je do [`IDataView`](xref:Microsoft.ML.IDataView). W takim przypadku nazwa [`IDataView`](xref:Microsoft.ML.IDataView) jest `inputData`. Ponieważ `CurrentPrice` jest obiektem docelowym lub etykietą, którą próbujesz przewidzieć przy użyciu nowych danych, zakłada się, że nie ma w tej chwili żadnej wartości.

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

Następnie użyj metody [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) , aby zastosować przekształcenia danych i wygenerować przewidywania.

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

Sprawdź przewidywane wartości przy użyciu metody [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) .

```csharp
// Get Predictions
float[] scoreColumn = predictions.GetColumn<float>("Score").ToArray();
```

Wartości przewidywane w kolumnie Score powinny wyglądać następująco:

| Uchwyceni | Przewidując |
|---|---|
| 1 | 144638,2 |
| 2 | 150079,4 |
| 3 | 107789,8 |
