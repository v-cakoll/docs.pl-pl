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
# <a name="make-predictions-with-a-trained-model"></a><span data-ttu-id="f7f82-103">Wprowadzaj prognozy za pomocą przeszkolonego modelu</span><span class="sxs-lookup"><span data-stu-id="f7f82-103">Make predictions with a trained model</span></span>

<span data-ttu-id="f7f82-104">Dowiedz się, jak używać uczonego modelu do tworzenia prognoz</span><span class="sxs-lookup"><span data-stu-id="f7f82-104">Learn how to use a trained model to make predictions</span></span>

## <a name="create-data-models"></a><span data-ttu-id="f7f82-105">Tworzenie modeli danych</span><span class="sxs-lookup"><span data-stu-id="f7f82-105">Create data models</span></span>

### <a name="input-data"></a><span data-ttu-id="f7f82-106">Dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="f7f82-106">Input data</span></span>

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

### <a name="output-data"></a><span data-ttu-id="f7f82-107">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="f7f82-107">Output data</span></span>

<span data-ttu-id="f7f82-108">Podobnie `Features` jak `Label` nazwy kolumn wejściowych, ML.NET ma domyślne nazwy kolumn wartości przewidywanej produkowane przez model.</span><span class="sxs-lookup"><span data-stu-id="f7f82-108">Like the `Features` and `Label` input column names, ML.NET has default names for the predicted value columns produced by a model.</span></span> <span data-ttu-id="f7f82-109">W zależności od zadania nazwa może się różnić.</span><span class="sxs-lookup"><span data-stu-id="f7f82-109">Depending on the task the name may differ.</span></span>

<span data-ttu-id="f7f82-110">Ponieważ algorytm używany w tym przykładzie jest algorytm regresji liniowej, domyślna nazwa kolumny wyjściowej jest, `Score` który jest zdefiniowany przez [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) atrybut we `PredictedPrice` właściwości.</span><span class="sxs-lookup"><span data-stu-id="f7f82-110">Because the algorithm used in this sample is a linear regression algorithm, the default name of the output column is `Score` which is defined by the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute on the `PredictedPrice` property.</span></span>

```csharp
class HousingPrediction
{
    [ColumnName("Score")]
    public float PredictedPrice { get; set; }
}
```

## <a name="set-up-a-prediction-pipeline"></a><span data-ttu-id="f7f82-111">Konfigurowanie potoku prognozowania</span><span class="sxs-lookup"><span data-stu-id="f7f82-111">Set up a prediction pipeline</span></span>

<span data-ttu-id="f7f82-112">Niezależnie od tego, czy dokonywanie pojedynczej lub wsadowe przewidywanie, potoku przewidywania musi zostać załadowany do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f7f82-112">Whether making a single or batch prediction, the prediction pipeline needs to be loaded into the application.</span></span> <span data-ttu-id="f7f82-113">Ten potok zawiera zarówno przekształcenia przetwarzania wstępnego danych, jak również uczonego modelu.</span><span class="sxs-lookup"><span data-stu-id="f7f82-113">This pipeline contains both the data pre-processing transformations as well as the trained model.</span></span> <span data-ttu-id="f7f82-114">Poniższy fragment kodu ładuje potok przewidywania `model.zip`z pliku o nazwie .</span><span class="sxs-lookup"><span data-stu-id="f7f82-114">The code snippet below loads the prediction pipeline from a file named `model.zip`.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Load Trained Model
DataViewSchema predictionPipelineSchema;
ITransformer predictionPipeline = mlContext.Model.Load("model.zip", out predictionPipelineSchema);
```

## <a name="single-prediction"></a><span data-ttu-id="f7f82-115">Pojedyncza prognoza</span><span class="sxs-lookup"><span data-stu-id="f7f82-115">Single prediction</span></span>

<span data-ttu-id="f7f82-116">Aby utworzyć pojedyncze przewidywanie, utwórz [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) przy użyciu załadowanego potoku prognozowania.</span><span class="sxs-lookup"><span data-stu-id="f7f82-116">To make a single prediction, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) using the loaded prediction pipeline.</span></span>

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

<span data-ttu-id="f7f82-117">Następnie należy [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) użyć metody i przekazać dane wejściowe jako parametr.</span><span class="sxs-lookup"><span data-stu-id="f7f82-117">Then, use the [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) method and pass in your input data as a parameter.</span></span> <span data-ttu-id="f7f82-118">Należy zauważyć, [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) że przy użyciu metody [`IDataView`](xref:Microsoft.ML.IDataView)nie wymaga danych wejściowych, aby być ).</span><span class="sxs-lookup"><span data-stu-id="f7f82-118">Notice that using the [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) method does not require the input to be an [`IDataView`](xref:Microsoft.ML.IDataView)).</span></span> <span data-ttu-id="f7f82-119">Dzieje się tak, ponieważ wygodnie internalizuje manipulacji typu danych wejściowych, dzięki czemu można przekazać w obiekcie typu danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="f7f82-119">This is because it conveniently internalizes the input data type manipulation so you can pass in an object of the input data type.</span></span> <span data-ttu-id="f7f82-120">Ponadto ponieważ `CurrentPrice` jest obiektem docelowym lub etykietą, którą próbujesz przewidzieć przy użyciu nowych danych, zakłada się, że w tej chwili nie ma dla niego żadnej wartości.</span><span class="sxs-lookup"><span data-stu-id="f7f82-120">Additionally, since `CurrentPrice` is the target or label you're trying to predict using new data, it's assumed there is no value for it at the moment.</span></span>

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

<span data-ttu-id="f7f82-121">Jeśli uzyskujesz dostęp do `Score` właściwości `prediction` obiektu, `150079`powinna zostać uzyskana wartość podobna do .</span><span class="sxs-lookup"><span data-stu-id="f7f82-121">If you access the `Score` property of the `prediction` object, you should get a value similar to `150079`.</span></span>

## <a name="multiple-predictions"></a><span data-ttu-id="f7f82-122">Wiele prognoz</span><span class="sxs-lookup"><span data-stu-id="f7f82-122">Multiple predictions</span></span>

<span data-ttu-id="f7f82-123">Biorąc pod uwagę następujące dane, załaduj je do pliku [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="f7f82-123">Given the following data, load it into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="f7f82-124">W takim przypadku nazwa [`IDataView`](xref:Microsoft.ML.IDataView) jest `inputData`.</span><span class="sxs-lookup"><span data-stu-id="f7f82-124">In this case, the name of the [`IDataView`](xref:Microsoft.ML.IDataView) is `inputData`.</span></span> <span data-ttu-id="f7f82-125">Ponieważ `CurrentPrice` jest to cel lub etykieta, którą próbujesz przewidzieć przy użyciu nowych danych, zakłada się, że w tej chwili nie ma dla niego żadnej wartości.</span><span class="sxs-lookup"><span data-stu-id="f7f82-125">Because `CurrentPrice` is the target or label you're trying to predict using new data, it's assumed there is no value for it at the moment.</span></span>

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

<span data-ttu-id="f7f82-126">Następnie użyj [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) metody, aby zastosować przekształcenia danych i wygenerować prognozy.</span><span class="sxs-lookup"><span data-stu-id="f7f82-126">Then, use the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method to apply the data transformations and generate predictions.</span></span>

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

<span data-ttu-id="f7f82-127">Sprawdź przewidywane wartości przy [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="f7f82-127">Inspect the predicted values by using the [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method.</span></span>

```csharp
// Get Predictions
float[] scoreColumn = predictions.GetColumn<float>("Score").ToArray();
```

<span data-ttu-id="f7f82-128">Przewidywane wartości w kolumnie wyników powinny wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="f7f82-128">The predicted values in the score column should look like the following:</span></span>

| <span data-ttu-id="f7f82-129">Obserwacji</span><span class="sxs-lookup"><span data-stu-id="f7f82-129">Observation</span></span> | <span data-ttu-id="f7f82-130">Prediction (Prognoza)</span><span class="sxs-lookup"><span data-stu-id="f7f82-130">Prediction</span></span> |
|---|---|
| <span data-ttu-id="f7f82-131">1</span><span class="sxs-lookup"><span data-stu-id="f7f82-131">1</span></span> | <span data-ttu-id="f7f82-132">144638.2</span><span class="sxs-lookup"><span data-stu-id="f7f82-132">144638.2</span></span> |
| <span data-ttu-id="f7f82-133">2</span><span class="sxs-lookup"><span data-stu-id="f7f82-133">2</span></span> | <span data-ttu-id="f7f82-134">150079.4</span><span class="sxs-lookup"><span data-stu-id="f7f82-134">150079.4</span></span> |
| <span data-ttu-id="f7f82-135">3</span><span class="sxs-lookup"><span data-stu-id="f7f82-135">3</span></span> | <span data-ttu-id="f7f82-136">107789.8</span><span class="sxs-lookup"><span data-stu-id="f7f82-136">107789.8</span></span> |
