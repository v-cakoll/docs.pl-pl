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
# <a name="save-and-load-trained-models"></a>Zapisywanie i ładowanie przeszkolonych modeli

Dowiedz się, jak zapisywać i ładować przeszkolone modele w aplikacji.

W całym procesie budowania modelu model mieszka w pamięci i jest dostępny w całym cyklu życia aplikacji. Jednak gdy aplikacja przestanie działać, jeśli model nie jest zapisywany gdzieś lokalnie lub zdalnie, nie jest już dostępny. Zazwyczaj modele są używane w pewnym momencie po szkoleniu w innych aplikacjach albo do wnioskowania lub ponownego szkolenia. W związku z tym ważne jest, aby przechowywać model. Zapisz i załaduj modele, wykonując kroki opisane w kolejnych sekcjach tego dokumentu podczas korzystania z potoków przygotowania i szkolenia modelu, takich jak ten opisany poniżej. Mimo że w tym przykładzie używa modelu regresji liniowej, ten sam proces ma zastosowanie do innych algorytmów ML.NET.

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

Ponieważ większość modeli i potoków przygotowania danych dziedziczyć z tego samego zestawu klas, zapisz i załadować podpisy metody dla tych składników jest taka sama. W zależności od przypadku użycia można połączyć potok przygotowania [`EstimatorChain`](xref:Microsoft.ML.Data.TransformerChain%601) danych i modelu [`ITransformer`](xref:Microsoft.ML.ITransformer) w jednym, który [`ITransformer`](xref:Microsoft.ML.ITransformer) będzie wyprowadzać jeden lub oddzielić je w ten sposób tworząc oddzielne dla każdego.

## <a name="save-a-model-locally"></a>Zapisywanie modelu lokalnie

Podczas zapisywania modelu potrzebne są dwie rzeczy:

1. Modelu. [`ITransformer`](xref:Microsoft.ML.ITransformer)
2. Oczekiwane [`DataViewSchema`](xref:Microsoft.ML.DataViewSchema) go [`ITransformer`](xref:Microsoft.ML.ITransformer)wego.

Po przeszkoleniu modelu, [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) należy użyć metody, aby `model.zip` zapisać `DataViewSchema` uczonego modelu do pliku o nazwie przy użyciu danych wejściowych.

```csharp
// Save Trained Model
mlContext.Model.Save(trainedModel, data.Schema, "model.zip");
```

## <a name="load-a-model-stored-locally"></a>Załaduj model przechowywany lokalnie

Modele przechowywane lokalnie mogą być używane `ASP.NET Core` `Serverless Web Applications`w innych procesach lub aplikacjach, takich jak i . Aby dowiedzieć się więcej, [zobacz Używanie ML.NET w interfejsie API sieci Web](./serve-model-web-api-ml-net.md) i wdrażanie artykułów ML.NET aplikacji ML.NET [serverless Web App.](./serve-model-serverless-azure-functions-ml-net.md)

W oddzielnej aplikacji lub [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) procesu użyj metody wraz ze ścieżką pliku, aby uzyskać uczonego modelu do aplikacji.

```csharp
//Define DataViewSchema for data preparation pipeline and trained model
DataViewSchema modelSchema;

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```

## <a name="load-a-model-stored-remotely"></a>Załaduj model przechowywany zdalnie

Aby załadować potoki przygotowania danych i modele przechowywane [`Stream`](xref:System.IO.Stream) w lokalizacji zdalnej [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) do aplikacji, należy użyć ścieżki pliku zamiast metody.

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

## <a name="working-with-separate-data-preparation-and-model-pipelines"></a>Praca z oddzielnymi potokami przygotowania i modelowania danych

> [!NOTE]
> Praca z oddzielnymi potokami przygotowania danych i szkolenia modelu jest opcjonalna. Separacja potoków ułatwia sprawdzanie parametrów modelu wyuczonego. W przypadku prognoz łatwiej jest zapisać i załadować pojedynczy potok, który zawiera operacje przygotowania danych i szkolenia modelu.

Podczas pracy z oddzielnymi potokami i modelami przygotowania danych stosuje się ten sam proces co pojedyncze potoki; z wyjątkiem teraz oba rurociągi muszą być zapisywane i ładowane jednocześnie.

Biorąc pod uwagę oddzielne potoki przygotowania danych i model szkolenia:

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

### <a name="save-data-preparation-pipeline-and-trained-model"></a>Zapisywanie potoku przygotowania danych i przeszkolonego modelu

Aby zapisać zarówno potok przygotowania danych, jak i przeszkolony model, użyj następujących poleceń:

```csharp
// Save Data Prep transformer
mlContext.Model.Save(dataPrepTransformer, data.Schema, "data_preparation_pipeline.zip");

// Save Trained Model
mlContext.Model.Save(trainedModel, transformedData.Schema, "model.zip");
```

### <a name="load-data-preparation-pipeline-and-trained-model"></a>Potok przygotowania danych załadowania i przeszkolony model

W oddzielnym procesie lub aplikacji załaduj potok przygotowania danych i przeszkolony model jednocześnie w następujący sposób:

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define data preparation and trained model schemas
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline and trained model
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip",out dataPrepPipelineSchema);
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```
