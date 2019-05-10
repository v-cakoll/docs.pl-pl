---
title: Zapisywanie i ładowanie przeszkolone modele
description: Dowiedz się, jak zapisać i załadować przeszkolone modele
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: e3d4a51ceaf707d30c5072b91d7baf7fe02ef433
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65066170"
---
# <a name="save-and-load-trained-models"></a><span data-ttu-id="4b334-103">Zapisywanie i ładowanie przeszkolone modele</span><span class="sxs-lookup"><span data-stu-id="4b334-103">Save and load trained models</span></span>

<span data-ttu-id="4b334-104">Dowiedz się, jak zapisać i załadować przeszkolone modele w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4b334-104">Learn how to save and load trained models in your application.</span></span> 

<span data-ttu-id="4b334-105">Przez cały proces tworzenia modelu modelu są przechowywane w pamięci i jest dostępny przez cały cykl życia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4b334-105">Throughout the model building process, a model lives in memory and is accessible throughout the application's lifecycle.</span></span> <span data-ttu-id="4b334-106">Jednak po przerwanie działania aplikacji, jeśli model nie jest zapisana gdzieś lokalnie lub zdalnie, nie jest już dostępny.</span><span class="sxs-lookup"><span data-stu-id="4b334-106">However, once the application stops running, if the model is not saved somewhere locally or remotely, it's no longer accessible.</span></span> <span data-ttu-id="4b334-107">Modele są zazwyczaj używane w pewnym momencie po szkolenia w innych aplikacjach, zarówno dla wnioskowania lub ponownego szkolenia.</span><span class="sxs-lookup"><span data-stu-id="4b334-107">Typically models are used at some point after training in other applications either for inference or re-training.</span></span> <span data-ttu-id="4b334-108">Dlatego ważne jest do przechowywania modelu.</span><span class="sxs-lookup"><span data-stu-id="4b334-108">Therefore, it's important to store the model.</span></span> <span data-ttu-id="4b334-109">Zapisz i załadować modeli, wykonując kroki opisane w kolejnych sekcjach tego dokumentu, korzystając z operacji przygotowania danych i potokami szkolenia modelu podobne do pokazanego poniżej.</span><span class="sxs-lookup"><span data-stu-id="4b334-109">Save and load models using the steps described in subsequent sections of this document when using data preparation and model training pipelines like the one detailed below.</span></span> <span data-ttu-id="4b334-110">Chociaż ten przykład używa modelu regresji liniowej, ten sam proces dotyczy inne algorytmy strukturze ML.NET.</span><span class="sxs-lookup"><span data-stu-id="4b334-110">Although this sample uses a linear regression model, the same process applies to other ML.NET algorithms.</span></span>

```csharp
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 600f,
        HistoricalPrices = new float[] { 100000f ,125000f ,122000f },
        CurrentPrice = 170000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 200000f, 250000f, 230000f },
        CurrentPrice = 225000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 126000f, 130000f, 200000f },
        CurrentPrice = 195000f
    }
};

// Create MLContext
MLContext mlContext = new MLContext();

// Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(housingData);

// Define data preparation estimator
EstimatorChain<RegressionPredictionTransformer<LinearRegressionModelParameters>> pipelineEstimator =
    mlContext.Transforms.Concatenate("Features", new string[] { "Size", "HistoricalPrices" })
        .Append(mlContext.Transforms.NormalizeMinMax("Features"))
        .Append(mlContext.Regression.Trainers.Sdca());

// Train model
ITransformer trainedModel = pipelineEstimator.Fit(data);

// Save model
mlContext.Model.Save(trainedModel, data.Schema, "model.zip");
```

<span data-ttu-id="4b334-111">Ponieważ dziedziczy większość potoki przygotowania danych i modeli taki sam zestaw klas, Zapisz, a następnie załadować podpisy metod dla tych składników, jest taka sama.</span><span class="sxs-lookup"><span data-stu-id="4b334-111">Because most models and data preparation pipelines inherit from the same set of classes, the save and load method signatures for these components is the same.</span></span> <span data-ttu-id="4b334-112">W zależności od danego przypadku użycia można albo połączyć potoku przygotowania danych i modelu w pojedynczej [ `EstimatorChain` ](xref:Microsoft.ML.Data.TransformerChain%601) będzie wyjściowy, który pojedynczej [ `ITransformer` ](xref:Microsoft.ML.ITransformer) lub oddzielić je w ten sposób tworzenia oddzielne [ `ITransformer` ](xref:Microsoft.ML.ITransformer) dla każdego.</span><span class="sxs-lookup"><span data-stu-id="4b334-112">Depending on your use case, you can either combine the data preparation pipeline and model into a single [`EstimatorChain`](xref:Microsoft.ML.Data.TransformerChain%601) which would output a single [`ITransformer`](xref:Microsoft.ML.ITransformer) or separate them thus creating a separate [`ITransformer`](xref:Microsoft.ML.ITransformer) for each.</span></span> 

## <a name="save-a-model-locally"></a><span data-ttu-id="4b334-113">Zapisywanie modelu lokalnie</span><span class="sxs-lookup"><span data-stu-id="4b334-113">Save a model locally</span></span>

<span data-ttu-id="4b334-114">Podczas zapisywania modelu należy się dwie rzeczy:</span><span class="sxs-lookup"><span data-stu-id="4b334-114">When saving a model you need two things:</span></span>

1. <span data-ttu-id="4b334-115">[ `ITransformer` ](xref:Microsoft.ML.ITransformer) Modelu.</span><span class="sxs-lookup"><span data-stu-id="4b334-115">The [`ITransformer`](xref:Microsoft.ML.ITransformer) of the model.</span></span>
2. <span data-ttu-id="4b334-116">[ `DataViewSchema` ](xref:Microsoft.ML.DataViewSchema) z [ `ITransformer` ](xref:Microsoft.ML.ITransformer)użytkownika oczekuje danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="4b334-116">The [`DataViewSchema`](xref:Microsoft.ML.DataViewSchema) of the [`ITransformer`](xref:Microsoft.ML.ITransformer)'s expected input.</span></span>

<span data-ttu-id="4b334-117">Po uczenia modelu [ `Save` ](xref:Microsoft.ML.ModelOperationsCatalog.Save*) metodę, aby zapisać uczonego modelu w pliku o nazwie `model.zip` przy użyciu `DataViewSchema` danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="4b334-117">After training the model, use the [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) method to save the trained model to a file called `model.zip` using the `DataViewSchema` of the input data.</span></span> 

```csharp
// Save Trained Model
mlContext.Model.Save(trainedModel, data.Schema, "model.zip");
```

## <a name="load-a-model-stored-locally"></a><span data-ttu-id="4b334-118">Ładowanie modelu przechowywane lokalnie</span><span class="sxs-lookup"><span data-stu-id="4b334-118">Load a model stored locally</span></span>

<span data-ttu-id="4b334-119">Modele przechowywane lokalnie, mogą być używane w innych procesów lub aplikacje, takie jak `ASP.NET Core` i `Serverless Web Applications`.</span><span class="sxs-lookup"><span data-stu-id="4b334-119">Models stored locally can be used in other processes or applications like `ASP.NET Core` and `Serverless Web Applications`.</span></span> <span data-ttu-id="4b334-120">Zobacz [strukturze ML.NET użycia, w interfejsie API sieci Web](./serve-model-web-api-ml-net.md) i [wdrażanie strukturze ML.NET aplikacji bez użycia serwera sieci Web](./serve-model-serverless-azure-functions-ml-net.md) artykuły, aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="4b334-120">See [Use ML.NET in Web API](./serve-model-web-api-ml-net.md) and [Deploy ML.NET Serverless Web App](./serve-model-serverless-azure-functions-ml-net.md) how-to articles to learn more.</span></span> 

<span data-ttu-id="4b334-121">W innej aplikacji lub proces, za pomocą [ `Load` ](xref:Microsoft.ML.ModelOperationsCatalog.Load*) metody oraz ścieżkę pliku, aby uzyskać uczonego modelu w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4b334-121">In a separate application or process, use the [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) method along with the file path to get the trained model into your application.</span></span>

```csharp
//Define DataViewSchema for data preparation pipeline and trained model
DataViewSchema modelSchema;

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```

## <a name="load-a-model-stored-remotely"></a><span data-ttu-id="4b334-122">Ładowanie modelu przechowywanych zdalnie</span><span class="sxs-lookup"><span data-stu-id="4b334-122">Load a model stored remotely</span></span>

<span data-ttu-id="4b334-123">Aby załadować przygotowania potoków danych i modeli, przechowywane w lokalizacji zdalnej w swojej aplikacji, użyj [ `Stream` ](xref:System.IO.Stream) zamiast ścieżki pliku w [ `Load` ](xref:Microsoft.ML.ModelOperationsCatalog.Load*) metody.</span><span class="sxs-lookup"><span data-stu-id="4b334-123">To load data preparation pipelines and models stored in a remote location into your application, use a [`Stream`](xref:System.IO.Stream) instead of a file path in the [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) method.</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define DataViewSchema and ITransformers
DataViewSchema modelSchema;
ITransformer trainedModel;

// Load data prep pipeline and trained model 
using (HttpClient client = new HttpClient())
{
    Stream modelFile = await client.GetStreamAsync("<YOUR-REMOTE-FILE-LOCATION>");

    trainedModel = mlContext.Model.Load(modelFile, out modelSchema);
}
```

## <a name="working-with-separate-data-preparation-and-model-pipelines"></a><span data-ttu-id="4b334-124">Praca z przygotowania danych i potoki modelu</span><span class="sxs-lookup"><span data-stu-id="4b334-124">Working with separate data preparation and model pipelines</span></span>

> [!NOTE]
> <span data-ttu-id="4b334-125">Praca z przygotowania osobne dane i potokami szkolenia modelu jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="4b334-125">Working with separate data preparation and model training pipelines is optional.</span></span> <span data-ttu-id="4b334-126">Rozdzielenie potoki ułatwia Sprawdzanie parametrów nauczony model.</span><span class="sxs-lookup"><span data-stu-id="4b334-126">Separation of pipelines makes it easier to inspect the learned model parameters.</span></span> <span data-ttu-id="4b334-127">Dla prognoz łatwiej jest zapisać i załadować pojedynczy potok, który obejmuje przygotowanie danych i operacji uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="4b334-127">For predictions, it's easier to save and load a single pipeline that includes the data preparation and model training operations.</span></span>

<span data-ttu-id="4b334-128">Podczas pracy z oddzielnych przygotowania potoków danych i modeli, stosuje się ten sam proces jako pojedynczy potoki; z wyjątkiem teraz zarówno potoki muszą być zapisane i załadować jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="4b334-128">When working with separate data preparation pipelines and models, the same process as single pipelines applies; except now both pipelines need to be saved and loaded simultaneously.</span></span>

<span data-ttu-id="4b334-129">Przygotowanie danego osobne dane i potokami szkolenia modelu:</span><span class="sxs-lookup"><span data-stu-id="4b334-129">Given separate data preparation and model training pipelines:</span></span>

```csharp
// Define data preparation estimator
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", new string[] { "Size", "HistoricalPrices" })
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// Create data preparation transformer
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(data);

// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Pre-process data using data prep operations
IDataView transformedData = dataPrepTransformer.Transform(data);

// Train regression model
RegressionPredictionTransformer<LinearRegressionModelParameters> trainedModel = sdcaEstimator.Fit(transformedData);
```

### <a name="save-data-preparation-pipeline-and-trained-model"></a><span data-ttu-id="4b334-130">Zapisz potoku przygotowania danych i uczonego modelu</span><span class="sxs-lookup"><span data-stu-id="4b334-130">Save data preparation pipeline and trained model</span></span>

<span data-ttu-id="4b334-131">Aby zapisać zarówno potoku przygotowywania danych, jak i trenowanego modelu, użyj następujących poleceń:</span><span class="sxs-lookup"><span data-stu-id="4b334-131">To save both the data preparation pipeline and trained model, use the following commands:</span></span>

```csharp
// Save Data Prep transformer
mlContext.Model.Save(dataPrepTransformer, data.Schema, "data_preparation_pipeline.zip");

// Save Trained Model
mlContext.Model.Save(trainedModel, transformedData.Schema, "model.zip");
```

### <a name="load-data-preparation-pipeline-and-trained-model"></a><span data-ttu-id="4b334-132">Załaduj potoku przygotowania danych i uczonego modelu</span><span class="sxs-lookup"><span data-stu-id="4b334-132">Load data preparation pipeline and trained model</span></span> 

<span data-ttu-id="4b334-133">W oddzielnym procesie lub aplikacji obciążenia potoku przygotowania danych i uczonego modelu jednocześnie, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="4b334-133">In a separate process or application, load the data preparation pipeline and trained model simultaneously as follows:</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define data preparation and trained model schemas
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline and trained model
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip",out dataPrepPipelineSchema);
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```
