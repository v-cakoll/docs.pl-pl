---
title: Ponowne szkolenie modelu
description: Dowiedz się, jak ponowne szkolenie modelu w strukturze ML.NET
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 552698c02a7846db588822fa68d094dece160ea0
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063568"
---
# <a name="re-train-a-model"></a><span data-ttu-id="dde8d-103">Ponowne szkolenie modelu</span><span class="sxs-lookup"><span data-stu-id="dde8d-103">Re-train a model</span></span>

<span data-ttu-id="dde8d-104">Dowiedz się, jak doskonalenie model w strukturze ML.NET uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="dde8d-104">Learn how to retrain a machine learning model in ML.NET.</span></span>

<span data-ttu-id="dde8d-105">Na świecie i danych wokół niej zmienić tempie stałej.</span><span class="sxs-lookup"><span data-stu-id="dde8d-105">The world and the data around it change at a constant pace.</span></span> <span data-ttu-id="dde8d-106">Jako takie Zmień i zaktualizuj również konieczne modeli.</span><span class="sxs-lookup"><span data-stu-id="dde8d-106">As such, models need to change and update as well.</span></span> <span data-ttu-id="dde8d-107">Strukturze ML.NET udostępnia funkcje Ponowne szkolenie modeli za pomocą przedstawiono parametry modelu jako punktu wyjścia ciągle tworzyć na poprzednie środowisko, a nie od zera, każdym razem.</span><span class="sxs-lookup"><span data-stu-id="dde8d-107">ML.NET provides functionality for re-training models using learned model parameters as a starting point to continually build on previous experience rather than starting from scratch every time.</span></span>  

<span data-ttu-id="dde8d-108">Następujące algorytmy są ponownie trainable w strukturze ML.NET:</span><span class="sxs-lookup"><span data-stu-id="dde8d-108">The following algorithms are re-trainable in ML.NET:</span></span>

- [<span data-ttu-id="dde8d-109">AveragedPerceptronTrainer</span><span class="sxs-lookup"><span data-stu-id="dde8d-109">AveragedPerceptronTrainer</span></span>](xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer)
- [<span data-ttu-id="dde8d-110">FieldAwareFactorizationMachineTrainer</span><span class="sxs-lookup"><span data-stu-id="dde8d-110">FieldAwareFactorizationMachineTrainer</span></span>](xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer)
- [<span data-ttu-id="dde8d-111">LbfgsLogisticRegressionBinaryTrainer</span><span class="sxs-lookup"><span data-stu-id="dde8d-111">LbfgsLogisticRegressionBinaryTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer)
- [<span data-ttu-id="dde8d-112">LbfgsMaximumEntropyMulticlassTrainer</span><span class="sxs-lookup"><span data-stu-id="dde8d-112">LbfgsMaximumEntropyMulticlassTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer)
- [<span data-ttu-id="dde8d-113">LbfgsPoissonRegressionTrainer</span><span class="sxs-lookup"><span data-stu-id="dde8d-113">LbfgsPoissonRegressionTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer)
- [<span data-ttu-id="dde8d-114">LinearSvmTrainer</span><span class="sxs-lookup"><span data-stu-id="dde8d-114">LinearSvmTrainer</span></span>](xref:Microsoft.ML.Trainers.LinearSvmTrainer)
- [<span data-ttu-id="dde8d-115">OnlineGradientDescentTrainer</span><span class="sxs-lookup"><span data-stu-id="dde8d-115">OnlineGradientDescentTrainer</span></span>](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer)
- [<span data-ttu-id="dde8d-116">SgdCalibratedTrainer</span><span class="sxs-lookup"><span data-stu-id="dde8d-116">SgdCalibratedTrainer</span></span>](xref:Microsoft.ML.Trainers.SgdCalibratedTrainer)
- [<span data-ttu-id="dde8d-117">SgdNonCalibratedTrainer</span><span class="sxs-lookup"><span data-stu-id="dde8d-117">SgdNonCalibratedTrainer</span></span>](xref:Microsoft.ML.Trainers.SgdNonCalibratedTrainer)
- [<span data-ttu-id="dde8d-118">SymbolicSgdLogisticRegressionBinaryTrainer</span><span class="sxs-lookup"><span data-stu-id="dde8d-118">SymbolicSgdLogisticRegressionBinaryTrainer</span></span>](xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer)

## <a name="load-pre-trained-model"></a><span data-ttu-id="dde8d-119">Załaduj wstępnie przeszkolonych model</span><span class="sxs-lookup"><span data-stu-id="dde8d-119">Load pre-trained model</span></span>

<span data-ttu-id="dde8d-120">Najpierw Załaduj wstępnie uczonego modelu w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dde8d-120">First, load the pre-trained model into your application.</span></span> <span data-ttu-id="dde8d-121">Aby dowiedzieć się więcej na temat ładowania potokami szkolenia i modeli, zobacz powiązane [instrukcje](./consuming-model-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="dde8d-121">To learn more about loading training pipelines and models, see the related [how-to article](./consuming-model-ml-net.md).</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define DataViewSchema of data prep pipeline and trained model
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data prepration pipeline
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip", out dataPrepPipelineSchema);

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("ogd_model.zip", out modelSchema);
```

## <a name="extract-pre-trained-model-parameters"></a><span data-ttu-id="dde8d-122">Wyodrębnianie parametrów wstępnie uczonego modelu</span><span class="sxs-lookup"><span data-stu-id="dde8d-122">Extract pre-trained model parameters</span></span>

<span data-ttu-id="dde8d-123">Po załadowaniu modelu wyodrębnić parametry nauczony model, uzyskując dostęp do [ `Model` ](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) właściwość wstępnie trenowanego modelu.</span><span class="sxs-lookup"><span data-stu-id="dde8d-123">Once the model is loaded, extract the learned model parameters by accessing the [`Model`](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) property of the pre-trained model.</span></span> <span data-ttu-id="dde8d-124">Wstępnie przeszkolonych model został uczony przy użyciu modelu regresji liniowej [ `OnlineGradientDescentTrainer` ](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) tworzy[ `RegressionPredictionTransformer` ](xref:Microsoft.ML.Data.RegressionPredictionTransformer`1) , generuje [ `LinearRegressionModelParameters` ](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters).</span><span class="sxs-lookup"><span data-stu-id="dde8d-124">The pre-trained model was trained using the linear regression model [`OnlineGradientDescentTrainer`](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) which creates a[`RegressionPredictionTransformer`](xref:Microsoft.ML.Data.RegressionPredictionTransformer`1) that outputs [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters).</span></span> <span data-ttu-id="dde8d-125">Te parametry modelu regresji liniowej zawierają nauczony odchylenie i wagi lub współczynników w modelu.</span><span class="sxs-lookup"><span data-stu-id="dde8d-125">These linear regression model parameters contain the learned bias and weights or coefficients of the model.</span></span> <span data-ttu-id="dde8d-126">Te wartości będzie służyć jako punkt początkowy dla nowych ponownie trenowanego modelu.</span><span class="sxs-lookup"><span data-stu-id="dde8d-126">These values will be used as a starting point for the new re-trained model.</span></span>

```csharp
// Extract trained model parameters
LinearRegressionModelParameters originalModelParameters = 
    ((ISingleFeaturePredictionTransformer<object>)trainedModel).Model as LinearRegressionModelParameters;
```

## <a name="re-train-model"></a><span data-ttu-id="dde8d-127">Ponowne szkolenie modelu</span><span class="sxs-lookup"><span data-stu-id="dde8d-127">Re-train model</span></span>

<span data-ttu-id="dde8d-128">Proces ponownego szkolenia modelu nie różni się niż uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="dde8d-128">The process for retraining a model is no different than that of training a model.</span></span> <span data-ttu-id="dde8d-129">Jedyna różnica polega na, [ `Fit` ](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*) metoda oprócz danych również przyjmuje jako dane wejściowe, oryginalnym przedstawiono parametry modelu i wykorzystuje je jako początkowy punkt w procesie ponownego szkolenia.</span><span class="sxs-lookup"><span data-stu-id="dde8d-129">The only difference is, the [`Fit`](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*) method in addition to the data also takes as input the original learned model parameters and uses them as a starting point in the re-training process.</span></span>  

```csharp
// New Data
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f,175000f,210000f },
        CurrentPrice = 205000f
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f },
        CurrentPrice = 210000f
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f },
        CurrentPrice = 180000f
    }
};

//Load New Data
IDataView newData = mlContext.Data.LoadFromEnumerable<HousingData>(housingData);

// Preprocess Data
IDataView transformedNewData = dataPrepPipeline.Transform(newData);

// Retrain model
RegressionPredictionTransformer<LinearRegressionModelParameters> retrainedModel = 
    mlContext.Regression.Trainers.OnlineGradientDescent()
        .Fit(transformedNewData, originalModelParameters);
```

## <a name="compare-model-parameters"></a><span data-ttu-id="dde8d-130">Porównaj parametry modelu</span><span class="sxs-lookup"><span data-stu-id="dde8d-130">Compare model parameters</span></span>

<span data-ttu-id="dde8d-131">Jak można sprawdzić, czy ponowne szkolenie się faktycznie stało?</span><span class="sxs-lookup"><span data-stu-id="dde8d-131">How do you know if re-training actually happened?</span></span> <span data-ttu-id="dde8d-132">Jednym ze sposobów byłoby porównać czy ponownie uczonego modelu parametry są inne niż te, oryginalnym modelu.</span><span class="sxs-lookup"><span data-stu-id="dde8d-132">One way would be to compare whether the re-trained model's parameters are different than those of the original model.</span></span> <span data-ttu-id="dde8d-133">Poniższy przykład kodu porównuje oryginalny względem wagi ponownie uczonego modelu i wysyła je do konsoli.</span><span class="sxs-lookup"><span data-stu-id="dde8d-133">The code sample below compares the original against the re-trained model weights and outputs them to the console.</span></span>

```csharp
// Extract Model Parameters of re-trained model
LinearRegressionModelParameters retrainedModelParameters = retrainedModel.Model as LinearRegressionModelParameters;

// Inspect Change in Weights
var weightDiffs = 
    originalModelParameters.Weights.Zip(
        retrainedModelParameters.Weights, (original, retrained) => original - retrained).ToArray();

Console.WriteLine("Original | Retrained | Difference");
for(int i=0;i < weightDiffs.Count();i++)
{
    Console.WriteLine($"{originalModelParameters.Weights[i]} | {retrainedModelParameters.Weights[i]} | {weightDiffs[i]}");
}
```

<span data-ttu-id="dde8d-134">W poniższej tabeli przedstawiono, jak może wyglądać dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="dde8d-134">The table below shows what the output might look like.</span></span> 

|<span data-ttu-id="dde8d-135">Oryginał</span><span class="sxs-lookup"><span data-stu-id="dde8d-135">Original</span></span> | <span data-ttu-id="dde8d-136">Retrained</span><span class="sxs-lookup"><span data-stu-id="dde8d-136">Retrained</span></span> | <span data-ttu-id="dde8d-137">Różnica</span><span class="sxs-lookup"><span data-stu-id="dde8d-137">Difference</span></span> |
|---|---|---|
| <span data-ttu-id="dde8d-138">33039.86</span><span class="sxs-lookup"><span data-stu-id="dde8d-138">33039.86</span></span> | <span data-ttu-id="dde8d-139">56293.76</span><span class="sxs-lookup"><span data-stu-id="dde8d-139">56293.76</span></span> | <span data-ttu-id="dde8d-140">-23253.9</span><span class="sxs-lookup"><span data-stu-id="dde8d-140">-23253.9</span></span> |
| <span data-ttu-id="dde8d-141">29099.14</span><span class="sxs-lookup"><span data-stu-id="dde8d-141">29099.14</span></span> | <span data-ttu-id="dde8d-142">49586.03</span><span class="sxs-lookup"><span data-stu-id="dde8d-142">49586.03</span></span> | <span data-ttu-id="dde8d-143">-20486.89</span><span class="sxs-lookup"><span data-stu-id="dde8d-143">-20486.89</span></span> |
| <span data-ttu-id="dde8d-144">28938.38</span><span class="sxs-lookup"><span data-stu-id="dde8d-144">28938.38</span></span> | <span data-ttu-id="dde8d-145">48609.23</span><span class="sxs-lookup"><span data-stu-id="dde8d-145">48609.23</span></span> | <span data-ttu-id="dde8d-146">-19670.85</span><span class="sxs-lookup"><span data-stu-id="dde8d-146">-19670.85</span></span> |
| <span data-ttu-id="dde8d-147">30484.02</span><span class="sxs-lookup"><span data-stu-id="dde8d-147">30484.02</span></span> | <span data-ttu-id="dde8d-148">53745.43</span><span class="sxs-lookup"><span data-stu-id="dde8d-148">53745.43</span></span> | <span data-ttu-id="dde8d-149">-23261.41</span><span class="sxs-lookup"><span data-stu-id="dde8d-149">-23261.41</span></span> |
