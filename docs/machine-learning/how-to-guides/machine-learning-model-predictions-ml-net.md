---
title: Tworzenie prognoz przy użyciu przeszkolonego modelu
description: Dowiedz się, jak tworzyć prognozy przy użyciu przeszkolonego modelu
ms.date: 09/18/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: f764d2147ec56f8dcc38f96d566ac746cf205650
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799133"
---
# <a name="make-predictions-with-a-trained-model"></a><span data-ttu-id="87dd6-103">Tworzenie prognoz przy użyciu przeszkolonego modelu</span><span class="sxs-lookup"><span data-stu-id="87dd6-103">Make predictions with a trained model</span></span>

<span data-ttu-id="87dd6-104">Dowiedz się, jak tworzyć prognozy przy użyciu przeszkolonego modelu</span><span class="sxs-lookup"><span data-stu-id="87dd6-104">Learn how to use a trained model to make predictions</span></span>

## <a name="create-data-models"></a><span data-ttu-id="87dd6-105">Tworzenie modeli danych</span><span class="sxs-lookup"><span data-stu-id="87dd6-105">Create data models</span></span>

### <a name="input-data"></a><span data-ttu-id="87dd6-106">Dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="87dd6-106">Input data</span></span>

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

### <a name="output-data"></a><span data-ttu-id="87dd6-107">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="87dd6-107">Output data</span></span>

<span data-ttu-id="87dd6-108">Podobnie jak `Features` i `Label` nazw kolumn wejściowych, ML.NET ma domyślne nazwy dla kolumn wartości przewidywanych produkowanych przez model.</span><span class="sxs-lookup"><span data-stu-id="87dd6-108">Like the `Features` and `Label` input column names, ML.NET has default names for the predicted value columns produced by a model.</span></span> <span data-ttu-id="87dd6-109">W zależności od zadania, którego nazwa może się różnić.</span><span class="sxs-lookup"><span data-stu-id="87dd6-109">Depending on the task the name may differ.</span></span>

<span data-ttu-id="87dd6-110">Ponieważ algorytm używany w tym przykładzie jest algorytmem regresji liniowej, domyślną nazwą kolumny wyjściowej jest `Score`, która jest definiowana przez atrybut [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) właściwości `PredictedPrice`.</span><span class="sxs-lookup"><span data-stu-id="87dd6-110">Because the algorithm used in this sample is a linear regression algorithm, the default name of the output column is `Score` which is defined by the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute on the `PredictedPrice` property.</span></span>

```csharp
class HousingPrediction
{
    [ColumnName("Score")]
    public float PredictedPrice { get; set; }
}
```

## <a name="set-up-a-prediction-pipeline"></a><span data-ttu-id="87dd6-111">Konfigurowanie potoku prognozowania</span><span class="sxs-lookup"><span data-stu-id="87dd6-111">Set up a prediction pipeline</span></span>

<span data-ttu-id="87dd6-112">Niezależnie od tego, czy dokonywana jest prognoza pojedyncza, czy wsadowa, należy załadować potok przewidywania do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="87dd6-112">Whether making a single or batch prediction, the prediction pipeline needs to be loaded into the application.</span></span> <span data-ttu-id="87dd6-113">Ten potok zawiera zarówno przekształcenia wstępnego przetwarzania danych, jak i przeszkolony model.</span><span class="sxs-lookup"><span data-stu-id="87dd6-113">This pipeline contains both the data pre-processing transformations as well as the trained model.</span></span> <span data-ttu-id="87dd6-114">Poniższy fragment kodu ładuje potok przewidywania z pliku o nazwie `model.zip`.</span><span class="sxs-lookup"><span data-stu-id="87dd6-114">The code snippet below loads the prediction pipeline from a file named `model.zip`.</span></span>

```csharp
//Create MLContext 
MLContext mlContext = new MLContext();

// Load Trained Model
DataViewSchema predictionPipelineSchema;
ITransformer predictionPipeline = mlContext.Model.Load("model.zip", out predictionPipelineSchema);
```

## <a name="single-prediction"></a><span data-ttu-id="87dd6-115">Pojedyncze prognozowanie</span><span class="sxs-lookup"><span data-stu-id="87dd6-115">Single prediction</span></span>

<span data-ttu-id="87dd6-116">Aby wykonać pojedyncze prognozowanie, Utwórz [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) przy użyciu załadowanego potoku predykcyjnego.</span><span class="sxs-lookup"><span data-stu-id="87dd6-116">To make a single prediction, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) using the loaded prediction pipeline.</span></span>

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

<span data-ttu-id="87dd6-117">Następnie użyj metody [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) i Przekaż dane wejściowe jako parametr.</span><span class="sxs-lookup"><span data-stu-id="87dd6-117">Then, use the [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) method and pass in your input data as a parameter.</span></span> <span data-ttu-id="87dd6-118">Należy zauważyć, że użycie metody [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) nie wymaga, aby dane wejściowe były [`IDataView`](xref:Microsoft.ML.IDataView)).</span><span class="sxs-lookup"><span data-stu-id="87dd6-118">Notice that using the [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) method does not require the input to be an [`IDataView`](xref:Microsoft.ML.IDataView)).</span></span> <span data-ttu-id="87dd6-119">Jest to spowodowane tym, że wygodnie internalizes manipulowanie danymi typu danych wejściowych, aby można było przekazać obiekt typu danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="87dd6-119">This is because it conveniently internalizes the input data type manipulation so you can pass in an object of the input data type.</span></span> <span data-ttu-id="87dd6-120">Ponadto, ponieważ `CurrentPrice` jest obiektem docelowym lub etykietą, którą próbujesz przewidzieć przy użyciu nowych danych, zakłada się, że nie ma w tej chwili żadnej wartości.</span><span class="sxs-lookup"><span data-stu-id="87dd6-120">Additionally, since `CurrentPrice` is the target or label you're trying to predict using new data, it's assumed there is no value for it at the moment.</span></span>

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

<span data-ttu-id="87dd6-121">W przypadku uzyskania dostępu do właściwości `Score` obiektu `prediction` należy uzyskać wartość podobną do `150079`.</span><span class="sxs-lookup"><span data-stu-id="87dd6-121">If you access the `Score` property of the `prediction` object, you should get a value similar to `150079`.</span></span>

## <a name="multiple-predictions"></a><span data-ttu-id="87dd6-122">Wiele prognoz</span><span class="sxs-lookup"><span data-stu-id="87dd6-122">Multiple predictions</span></span>

<span data-ttu-id="87dd6-123">Uwzględniając poniższe dane, załaduj je do [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="87dd6-123">Given the following data, load it into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="87dd6-124">W takim przypadku nazwa [`IDataView`](xref:Microsoft.ML.IDataView) jest `inputData`.</span><span class="sxs-lookup"><span data-stu-id="87dd6-124">In this case, the name of the [`IDataView`](xref:Microsoft.ML.IDataView) is `inputData`.</span></span> <span data-ttu-id="87dd6-125">Ponieważ `CurrentPrice` jest obiektem docelowym lub etykietą, którą próbujesz przewidzieć przy użyciu nowych danych, zakłada się, że nie ma w tej chwili żadnej wartości.</span><span class="sxs-lookup"><span data-stu-id="87dd6-125">Because `CurrentPrice` is the target or label you're trying to predict using new data, it's assumed there is no value for it at the moment.</span></span>

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

<span data-ttu-id="87dd6-126">Następnie użyj metody [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) , aby zastosować przekształcenia danych i wygenerować przewidywania.</span><span class="sxs-lookup"><span data-stu-id="87dd6-126">Then, use the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method to apply the data transformations and generate predictions.</span></span>

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

<span data-ttu-id="87dd6-127">Sprawdź przewidywane wartości przy użyciu metody [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) .</span><span class="sxs-lookup"><span data-stu-id="87dd6-127">Inspect the predicted values by using the [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method.</span></span>

```csharp
// Get Predictions
float[] scoreColumn = predictions.GetColumn<float>("Score").ToArray();
```

<span data-ttu-id="87dd6-128">Wartości przewidywane w kolumnie Score powinny wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="87dd6-128">The predicted values in the score column should look like the following:</span></span>

| <span data-ttu-id="87dd6-129">Uchwyceni</span><span class="sxs-lookup"><span data-stu-id="87dd6-129">Observation</span></span> | <span data-ttu-id="87dd6-130">Przewidując</span><span class="sxs-lookup"><span data-stu-id="87dd6-130">Prediction</span></span> |
|---|---|
| <span data-ttu-id="87dd6-131">1</span><span class="sxs-lookup"><span data-stu-id="87dd6-131">1</span></span> | <span data-ttu-id="87dd6-132">144638,2</span><span class="sxs-lookup"><span data-stu-id="87dd6-132">144638.2</span></span> |
| <span data-ttu-id="87dd6-133">2</span><span class="sxs-lookup"><span data-stu-id="87dd6-133">2</span></span> | <span data-ttu-id="87dd6-134">150079,4</span><span class="sxs-lookup"><span data-stu-id="87dd6-134">150079.4</span></span> |
| <span data-ttu-id="87dd6-135">3</span><span class="sxs-lookup"><span data-stu-id="87dd6-135">3</span></span> | <span data-ttu-id="87dd6-136">107789,8</span><span class="sxs-lookup"><span data-stu-id="87dd6-136">107789.8</span></span> |
