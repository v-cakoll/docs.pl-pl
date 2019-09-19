---
title: Tworzenie prognoz przy użyciu przeszkolonego modelu
description: Dowiedz się, jak tworzyć prognozy przy użyciu przeszkolonego modelu
ms.date: 09/18/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 33e0cb74342ca3e82ff5f108453d63e022d63d20
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118020"
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

Podobnie jak nazwy `Label` kolumn wejściowych i,ml.netmanazwydomyślnedlakolumnwartościprzewidywanychprodukowanychprzezmodel.`Features` W zależności od zadania, którego nazwa może się różnić.

Ponieważ algorytm używany w tym przykładzie jest algorytmem regresji liniowej, domyślna nazwa kolumny wyjściowej jest `Score` definiowana [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) przez atrybut `PredictedPrice` właściwości.

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

Aby wykonać pojedyncze prognozowanie, Utwórz [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) za pomocą załadowanego potoku predykcyjnego.

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

Następnie użyj [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) metody i Przekaż dane wejściowe jako parametr. Należy zauważyć, że [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) użycie metody nie wymaga, aby dane wejściowe [`IDataView`](xref:Microsoft.ML.IDataView)były. Jest to spowodowane tym, że wygodnie internalizes manipulowanie danymi typu danych wejściowych, aby można było przekazać obiekt typu danych wejściowych. Ponadto, ponieważ `CurrentPrice` jest obiektem docelowym lub etykietą, którą próbujesz przewidzieć przy użyciu nowych danych, zakłada się, że nie ma w tej chwili żadnej wartości.

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

Jeśli uzyskujesz dostęp `Score` do właściwości `prediction` obiektu, należy uzyskać wartość podobną do `150079`.

## <a name="multiple-predictions"></a>Wiele prognoz

Uwzględniając poniższe dane, załaduj je do [`IDataView`](xref:Microsoft.ML.IDataView). W tym przypadku nazwa [`IDataView`](xref:Microsoft.ML.IDataView) jest. `inputData` Ponieważ `CurrentPrice` jest obiektem docelowym lub etykietą, którą próbujesz przewidzieć przy użyciu nowych danych, zakłada się, że nie ma w tej chwili żadnej wartości.

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

Następnie użyj [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) metody, aby zastosować przekształcenia danych i wygenerować przewidywania.

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

Sprawdź przewidywane wartości przy użyciu [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) metody.

```csharp
// Get Predictions
float[] scoreColumn = predictions.GetColumn<float>("Score").ToArray();
```

Wartości przewidywane w kolumnie Score powinny wyglądać następująco:

| Uchwyceni | Prognozy |
|---|---|
| 1 | 144638,2 |
| 2 | 150079,4 |
| 3 | 107789,8 |
