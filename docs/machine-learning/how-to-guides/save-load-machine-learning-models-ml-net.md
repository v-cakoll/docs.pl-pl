---
title: Zapisywanie i ładowanie przeszkolonych modeli
description: Dowiedz się, jak zapisywać i ładować przeszkolone modele
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: e3cebe979b5c279ce8cb90db5510f8758c24c2b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73977007"
---
# <a name="save-and-load-trained-models"></a><span data-ttu-id="40bcf-103">Zapisywanie i ładowanie przeszkolonych modeli</span><span class="sxs-lookup"><span data-stu-id="40bcf-103">Save and load trained models</span></span>

<span data-ttu-id="40bcf-104">Dowiedz się, jak zapisywać i ładować przeszkolone modele w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="40bcf-104">Learn how to save and load trained models in your application.</span></span>

<span data-ttu-id="40bcf-105">W całym procesie budowania modelu model mieszka w pamięci i jest dostępny w całym cyklu życia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="40bcf-105">Throughout the model building process, a model lives in memory and is accessible throughout the application's lifecycle.</span></span> <span data-ttu-id="40bcf-106">Jednak gdy aplikacja przestanie działać, jeśli model nie jest zapisywany gdzieś lokalnie lub zdalnie, nie jest już dostępny.</span><span class="sxs-lookup"><span data-stu-id="40bcf-106">However, once the application stops running, if the model is not saved somewhere locally or remotely, it's no longer accessible.</span></span> <span data-ttu-id="40bcf-107">Zazwyczaj modele są używane w pewnym momencie po szkoleniu w innych aplikacjach albo do wnioskowania lub ponownego szkolenia.</span><span class="sxs-lookup"><span data-stu-id="40bcf-107">Typically models are used at some point after training in other applications either for inference or re-training.</span></span> <span data-ttu-id="40bcf-108">W związku z tym ważne jest, aby przechowywać model.</span><span class="sxs-lookup"><span data-stu-id="40bcf-108">Therefore, it's important to store the model.</span></span> <span data-ttu-id="40bcf-109">Zapisz i załaduj modele, wykonując kroki opisane w kolejnych sekcjach tego dokumentu podczas korzystania z potoków przygotowania i szkolenia modelu, takich jak ten opisany poniżej.</span><span class="sxs-lookup"><span data-stu-id="40bcf-109">Save and load models using the steps described in subsequent sections of this document when using data preparation and model training pipelines like the one detailed below.</span></span> <span data-ttu-id="40bcf-110">Mimo że w tym przykładzie używa modelu regresji liniowej, ten sam proces ma zastosowanie do innych algorytmów ML.NET.</span><span class="sxs-lookup"><span data-stu-id="40bcf-110">Although this sample uses a linear regression model, the same process applies to other ML.NET algorithms.</span></span>

```csharp
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 600f,
        HistoricalPrices = new float[] { 100000f, 125000f, 122000f },
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

<span data-ttu-id="40bcf-111">Ponieważ większość modeli i potoków przygotowania danych dziedziczyć z tego samego zestawu klas, zapisz i załadować podpisy metody dla tych składników jest taka sama.</span><span class="sxs-lookup"><span data-stu-id="40bcf-111">Because most models and data preparation pipelines inherit from the same set of classes, the save and load method signatures for these components is the same.</span></span> <span data-ttu-id="40bcf-112">W zależności od przypadku użycia można połączyć potok przygotowania [`EstimatorChain`](xref:Microsoft.ML.Data.TransformerChain%601) danych i modelu [`ITransformer`](xref:Microsoft.ML.ITransformer) w jednym, który [`ITransformer`](xref:Microsoft.ML.ITransformer) będzie wyprowadzać jeden lub oddzielić je w ten sposób tworząc oddzielne dla każdego.</span><span class="sxs-lookup"><span data-stu-id="40bcf-112">Depending on your use case, you can either combine the data preparation pipeline and model into a single [`EstimatorChain`](xref:Microsoft.ML.Data.TransformerChain%601) which would output a single [`ITransformer`](xref:Microsoft.ML.ITransformer) or separate them thus creating a separate [`ITransformer`](xref:Microsoft.ML.ITransformer) for each.</span></span>

## <a name="save-a-model-locally"></a><span data-ttu-id="40bcf-113">Zapisywanie modelu lokalnie</span><span class="sxs-lookup"><span data-stu-id="40bcf-113">Save a model locally</span></span>

<span data-ttu-id="40bcf-114">Podczas zapisywania modelu potrzebne są dwie rzeczy:</span><span class="sxs-lookup"><span data-stu-id="40bcf-114">When saving a model you need two things:</span></span>

1. <span data-ttu-id="40bcf-115">Modelu. [`ITransformer`](xref:Microsoft.ML.ITransformer)</span><span class="sxs-lookup"><span data-stu-id="40bcf-115">The [`ITransformer`](xref:Microsoft.ML.ITransformer) of the model.</span></span>
2. <span data-ttu-id="40bcf-116">Oczekiwane [`DataViewSchema`](xref:Microsoft.ML.DataViewSchema) go [`ITransformer`](xref:Microsoft.ML.ITransformer)wego.</span><span class="sxs-lookup"><span data-stu-id="40bcf-116">The [`DataViewSchema`](xref:Microsoft.ML.DataViewSchema) of the [`ITransformer`](xref:Microsoft.ML.ITransformer)'s expected input.</span></span>

<span data-ttu-id="40bcf-117">Po przeszkoleniu modelu, [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) należy użyć metody, aby `model.zip` zapisać `DataViewSchema` uczonego modelu do pliku o nazwie przy użyciu danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="40bcf-117">After training the model, use the [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) method to save the trained model to a file called `model.zip` using the `DataViewSchema` of the input data.</span></span>

```csharp
// Save Trained Model
mlContext.Model.Save(trainedModel, data.Schema, "model.zip");
```

## <a name="load-a-model-stored-locally"></a><span data-ttu-id="40bcf-118">Załaduj model przechowywany lokalnie</span><span class="sxs-lookup"><span data-stu-id="40bcf-118">Load a model stored locally</span></span>

<span data-ttu-id="40bcf-119">Modele przechowywane lokalnie mogą być używane `ASP.NET Core` `Serverless Web Applications`w innych procesach lub aplikacjach, takich jak i .</span><span class="sxs-lookup"><span data-stu-id="40bcf-119">Models stored locally can be used in other processes or applications like `ASP.NET Core` and `Serverless Web Applications`.</span></span> <span data-ttu-id="40bcf-120">Aby dowiedzieć się więcej, [zobacz Używanie ML.NET w interfejsie API sieci Web](./serve-model-web-api-ml-net.md) i wdrażanie artykułów ML.NET aplikacji ML.NET [serverless Web App.](./serve-model-serverless-azure-functions-ml-net.md)</span><span class="sxs-lookup"><span data-stu-id="40bcf-120">See [Use ML.NET in Web API](./serve-model-web-api-ml-net.md) and [Deploy ML.NET Serverless Web App](./serve-model-serverless-azure-functions-ml-net.md) how-to articles to learn more.</span></span>

<span data-ttu-id="40bcf-121">W oddzielnej aplikacji lub [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) procesu użyj metody wraz ze ścieżką pliku, aby uzyskać uczonego modelu do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="40bcf-121">In a separate application or process, use the [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) method along with the file path to get the trained model into your application.</span></span>

```csharp
//Define DataViewSchema for data preparation pipeline and trained model
DataViewSchema modelSchema;

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```

## <a name="load-a-model-stored-remotely"></a><span data-ttu-id="40bcf-122">Załaduj model przechowywany zdalnie</span><span class="sxs-lookup"><span data-stu-id="40bcf-122">Load a model stored remotely</span></span>

<span data-ttu-id="40bcf-123">Aby załadować potoki przygotowania danych i modele przechowywane [`Stream`](xref:System.IO.Stream) w lokalizacji zdalnej [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) do aplikacji, należy użyć ścieżki pliku zamiast metody.</span><span class="sxs-lookup"><span data-stu-id="40bcf-123">To load data preparation pipelines and models stored in a remote location into your application, use a [`Stream`](xref:System.IO.Stream) instead of a file path in the [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) method.</span></span>

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

## <a name="working-with-separate-data-preparation-and-model-pipelines"></a><span data-ttu-id="40bcf-124">Praca z oddzielnymi potokami przygotowania i modelowania danych</span><span class="sxs-lookup"><span data-stu-id="40bcf-124">Working with separate data preparation and model pipelines</span></span>

> [!NOTE]
> <span data-ttu-id="40bcf-125">Praca z oddzielnymi potokami przygotowania danych i szkolenia modelu jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="40bcf-125">Working with separate data preparation and model training pipelines is optional.</span></span> <span data-ttu-id="40bcf-126">Separacja potoków ułatwia sprawdzanie parametrów modelu wyuczonego.</span><span class="sxs-lookup"><span data-stu-id="40bcf-126">Separation of pipelines makes it easier to inspect the learned model parameters.</span></span> <span data-ttu-id="40bcf-127">W przypadku prognoz łatwiej jest zapisać i załadować pojedynczy potok, który zawiera operacje przygotowania danych i szkolenia modelu.</span><span class="sxs-lookup"><span data-stu-id="40bcf-127">For predictions, it's easier to save and load a single pipeline that includes the data preparation and model training operations.</span></span>

<span data-ttu-id="40bcf-128">Podczas pracy z oddzielnymi potokami i modelami przygotowania danych stosuje się ten sam proces co pojedyncze potoki; z wyjątkiem teraz oba rurociągi muszą być zapisywane i ładowane jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="40bcf-128">When working with separate data preparation pipelines and models, the same process as single pipelines applies; except now both pipelines need to be saved and loaded simultaneously.</span></span>

<span data-ttu-id="40bcf-129">Biorąc pod uwagę oddzielne potoki przygotowania danych i model szkolenia:</span><span class="sxs-lookup"><span data-stu-id="40bcf-129">Given separate data preparation and model training pipelines:</span></span>

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

### <a name="save-data-preparation-pipeline-and-trained-model"></a><span data-ttu-id="40bcf-130">Zapisywanie potoku przygotowania danych i przeszkolonego modelu</span><span class="sxs-lookup"><span data-stu-id="40bcf-130">Save data preparation pipeline and trained model</span></span>

<span data-ttu-id="40bcf-131">Aby zapisać zarówno potok przygotowania danych, jak i przeszkolony model, użyj następujących poleceń:</span><span class="sxs-lookup"><span data-stu-id="40bcf-131">To save both the data preparation pipeline and trained model, use the following commands:</span></span>

```csharp
// Save Data Prep transformer
mlContext.Model.Save(dataPrepTransformer, data.Schema, "data_preparation_pipeline.zip");

// Save Trained Model
mlContext.Model.Save(trainedModel, transformedData.Schema, "model.zip");
```

### <a name="load-data-preparation-pipeline-and-trained-model"></a><span data-ttu-id="40bcf-132">Potok przygotowania danych załadowania i przeszkolony model</span><span class="sxs-lookup"><span data-stu-id="40bcf-132">Load data preparation pipeline and trained model</span></span>

<span data-ttu-id="40bcf-133">W oddzielnym procesie lub aplikacji załaduj potok przygotowania danych i przeszkolony model jednocześnie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="40bcf-133">In a separate process or application, load the data preparation pipeline and trained model simultaneously as follows:</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define data preparation and trained model schemas
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline and trained model
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip",out dataPrepPipelineSchema);
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```
