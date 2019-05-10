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
# <a name="save-and-load-trained-models"></a>Zapisywanie i ładowanie przeszkolone modele

Dowiedz się, jak zapisać i załadować przeszkolone modele w aplikacji. 

Przez cały proces tworzenia modelu modelu są przechowywane w pamięci i jest dostępny przez cały cykl życia aplikacji. Jednak po przerwanie działania aplikacji, jeśli model nie jest zapisana gdzieś lokalnie lub zdalnie, nie jest już dostępny. Modele są zazwyczaj używane w pewnym momencie po szkolenia w innych aplikacjach, zarówno dla wnioskowania lub ponownego szkolenia. Dlatego ważne jest do przechowywania modelu. Zapisz i załadować modeli, wykonując kroki opisane w kolejnych sekcjach tego dokumentu, korzystając z operacji przygotowania danych i potokami szkolenia modelu podobne do pokazanego poniżej. Chociaż ten przykład używa modelu regresji liniowej, ten sam proces dotyczy inne algorytmy strukturze ML.NET.

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

Ponieważ dziedziczy większość potoki przygotowania danych i modeli taki sam zestaw klas, Zapisz, a następnie załadować podpisy metod dla tych składników, jest taka sama. W zależności od danego przypadku użycia można albo połączyć potoku przygotowania danych i modelu w pojedynczej [ `EstimatorChain` ](xref:Microsoft.ML.Data.TransformerChain%601) będzie wyjściowy, który pojedynczej [ `ITransformer` ](xref:Microsoft.ML.ITransformer) lub oddzielić je w ten sposób tworzenia oddzielne [ `ITransformer` ](xref:Microsoft.ML.ITransformer) dla każdego. 

## <a name="save-a-model-locally"></a>Zapisywanie modelu lokalnie

Podczas zapisywania modelu należy się dwie rzeczy:

1. [ `ITransformer` ](xref:Microsoft.ML.ITransformer) Modelu.
2. [ `DataViewSchema` ](xref:Microsoft.ML.DataViewSchema) z [ `ITransformer` ](xref:Microsoft.ML.ITransformer)użytkownika oczekuje danych wejściowych.

Po uczenia modelu [ `Save` ](xref:Microsoft.ML.ModelOperationsCatalog.Save*) metodę, aby zapisać uczonego modelu w pliku o nazwie `model.zip` przy użyciu `DataViewSchema` danych wejściowych. 

```csharp
// Save Trained Model
mlContext.Model.Save(trainedModel, data.Schema, "model.zip");
```

## <a name="load-a-model-stored-locally"></a>Ładowanie modelu przechowywane lokalnie

Modele przechowywane lokalnie, mogą być używane w innych procesów lub aplikacje, takie jak `ASP.NET Core` i `Serverless Web Applications`. Zobacz [strukturze ML.NET użycia, w interfejsie API sieci Web](./serve-model-web-api-ml-net.md) i [wdrażanie strukturze ML.NET aplikacji bez użycia serwera sieci Web](./serve-model-serverless-azure-functions-ml-net.md) artykuły, aby dowiedzieć się więcej. 

W innej aplikacji lub proces, za pomocą [ `Load` ](xref:Microsoft.ML.ModelOperationsCatalog.Load*) metody oraz ścieżkę pliku, aby uzyskać uczonego modelu w aplikacji.

```csharp
//Define DataViewSchema for data preparation pipeline and trained model
DataViewSchema modelSchema;

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```

## <a name="load-a-model-stored-remotely"></a>Ładowanie modelu przechowywanych zdalnie

Aby załadować przygotowania potoków danych i modeli, przechowywane w lokalizacji zdalnej w swojej aplikacji, użyj [ `Stream` ](xref:System.IO.Stream) zamiast ścieżki pliku w [ `Load` ](xref:Microsoft.ML.ModelOperationsCatalog.Load*) metody.

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

## <a name="working-with-separate-data-preparation-and-model-pipelines"></a>Praca z przygotowania danych i potoki modelu

> [!NOTE]
> Praca z przygotowania osobne dane i potokami szkolenia modelu jest opcjonalne. Rozdzielenie potoki ułatwia Sprawdzanie parametrów nauczony model. Dla prognoz łatwiej jest zapisać i załadować pojedynczy potok, który obejmuje przygotowanie danych i operacji uczenia modelu.

Podczas pracy z oddzielnych przygotowania potoków danych i modeli, stosuje się ten sam proces jako pojedynczy potoki; z wyjątkiem teraz zarówno potoki muszą być zapisane i załadować jednocześnie.

Przygotowanie danego osobne dane i potokami szkolenia modelu:

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

### <a name="save-data-preparation-pipeline-and-trained-model"></a>Zapisz potoku przygotowania danych i uczonego modelu

Aby zapisać zarówno potoku przygotowywania danych, jak i trenowanego modelu, użyj następujących poleceń:

```csharp
// Save Data Prep transformer
mlContext.Model.Save(dataPrepTransformer, data.Schema, "data_preparation_pipeline.zip");

// Save Trained Model
mlContext.Model.Save(trainedModel, transformedData.Schema, "model.zip");
```

### <a name="load-data-preparation-pipeline-and-trained-model"></a>Załaduj potoku przygotowania danych i uczonego modelu 

W oddzielnym procesie lub aplikacji obciążenia potoku przygotowania danych i uczonego modelu jednocześnie, w następujący sposób:

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define data preparation and trained model schemas
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline and trained model
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip",out dataPrepPipelineSchema);
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```
