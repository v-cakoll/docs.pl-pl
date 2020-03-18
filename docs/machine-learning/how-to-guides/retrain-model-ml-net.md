---
title: Ponowne trenowanie modelu
description: Dowiedz się, jak przekwalifikować model w ML.NET
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 735782a4a0877a917b6e1885f009aa49d834170f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73976965"
---
# <a name="re-train-a-model"></a><span data-ttu-id="5e10c-103">Ponowne trenowanie modelu</span><span class="sxs-lookup"><span data-stu-id="5e10c-103">Re-train a model</span></span>

<span data-ttu-id="5e10c-104">Dowiedz się, jak ponownie trenować model uczenia maszynowego w ML.NET.</span><span class="sxs-lookup"><span data-stu-id="5e10c-104">Learn how to retrain a machine learning model in ML.NET.</span></span>

<span data-ttu-id="5e10c-105">Świat i dane wokół niego zmieniają się w stałym tempie.</span><span class="sxs-lookup"><span data-stu-id="5e10c-105">The world and the data around it change at a constant pace.</span></span> <span data-ttu-id="5e10c-106">W związku z tym modele muszą również ulec zmianie i zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="5e10c-106">As such, models need to change and update as well.</span></span> <span data-ttu-id="5e10c-107">ML.NET udostępnia funkcje dla modeli ponownego szkolenia przy użyciu wyuczonych parametrów modelu jako punkt wyjścia do ciągłego korzystania z poprzednich doświadczeń, a nie począwszy od zera za każdym razem.</span><span class="sxs-lookup"><span data-stu-id="5e10c-107">ML.NET provides functionality for re-training models using learned model parameters as a starting point to continually build on previous experience rather than starting from scratch every time.</span></span>

<span data-ttu-id="5e10c-108">Następujące algorytmy można ponownie nabyć w ML.NET:</span><span class="sxs-lookup"><span data-stu-id="5e10c-108">The following algorithms are re-trainable in ML.NET:</span></span>

- [<span data-ttu-id="5e10c-109">Trener UśrednionyPerceptron</span><span class="sxs-lookup"><span data-stu-id="5e10c-109">AveragedPerceptronTrainer</span></span>](xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer)
- [<span data-ttu-id="5e10c-110">FieldAwareFactorizationMachineTrainer</span><span class="sxs-lookup"><span data-stu-id="5e10c-110">FieldAwareFactorizationMachineTrainer</span></span>](xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer)
- [<span data-ttu-id="5e10c-111">LbfgsLogisticRegressionBinaryTrainer</span><span class="sxs-lookup"><span data-stu-id="5e10c-111">LbfgsLogisticRegressionBinaryTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer)
- [<span data-ttu-id="5e10c-112">LbfgsMaximumEntropyMultiClassTrainer</span><span class="sxs-lookup"><span data-stu-id="5e10c-112">LbfgsMaximumEntropyMulticlassTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer)
- [<span data-ttu-id="5e10c-113">LbfgsPoissonTrener regresu</span><span class="sxs-lookup"><span data-stu-id="5e10c-113">LbfgsPoissonRegressionTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer)
- [<span data-ttu-id="5e10c-114">LinearSvmTrainer (LinearSvmTrainer)</span><span class="sxs-lookup"><span data-stu-id="5e10c-114">LinearSvmTrainer</span></span>](xref:Microsoft.ML.Trainers.LinearSvmTrainer)
- [<span data-ttu-id="5e10c-115">OnlineGradientDescentTrainer</span><span class="sxs-lookup"><span data-stu-id="5e10c-115">OnlineGradientDescentTrainer</span></span>](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer)
- [<span data-ttu-id="5e10c-116">SgdCalibratedTrainer</span><span class="sxs-lookup"><span data-stu-id="5e10c-116">SgdCalibratedTrainer</span></span>](xref:Microsoft.ML.Trainers.SgdCalibratedTrainer)
- [<span data-ttu-id="5e10c-117">SgdNonCalibratedTrainer</span><span class="sxs-lookup"><span data-stu-id="5e10c-117">SgdNonCalibratedTrainer</span></span>](xref:Microsoft.ML.Trainers.SgdNonCalibratedTrainer)
- [<span data-ttu-id="5e10c-118">SymbolicSgdLogisticRegressionBinaryTrainer</span><span class="sxs-lookup"><span data-stu-id="5e10c-118">SymbolicSgdLogisticRegressionBinaryTrainer</span></span>](xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer)

## <a name="load-pre-trained-model"></a><span data-ttu-id="5e10c-119">Załaduj wstępnie przeszkolony model</span><span class="sxs-lookup"><span data-stu-id="5e10c-119">Load pre-trained model</span></span>

<span data-ttu-id="5e10c-120">Najpierw załaduj wstępnie przeszkolony model do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5e10c-120">First, load the pre-trained model into your application.</span></span> <span data-ttu-id="5e10c-121">Aby dowiedzieć się więcej na temat ładowania potoków szkoleniowych i modeli, zobacz [Zapisywanie i ładowanie uczonego modelu](save-load-machine-learning-models-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="5e10c-121">To learn more about loading training pipelines and models, see [Save and load a trained model](save-load-machine-learning-models-ml-net.md).</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define DataViewSchema of data prep pipeline and trained model
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip", out dataPrepPipelineSchema);

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("ogd_model.zip", out modelSchema);
```

## <a name="extract-pre-trained-model-parameters"></a><span data-ttu-id="5e10c-122">Wyodrębnianie wstępnie przeszkolonych parametrów modelu</span><span class="sxs-lookup"><span data-stu-id="5e10c-122">Extract pre-trained model parameters</span></span>

<span data-ttu-id="5e10c-123">Po załadowaniu modelu wyodrębnij parametry modelu, [`Model`](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) uzyskując dostęp do właściwości wstępnie uczonego modelu.</span><span class="sxs-lookup"><span data-stu-id="5e10c-123">Once the model is loaded, extract the learned model parameters by accessing the [`Model`](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) property of the pre-trained model.</span></span> <span data-ttu-id="5e10c-124">Wstępnie przeszkolony model został przeszkolony [`OnlineGradientDescentTrainer`](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) przy użyciu[`RegressionPredictionTransformer`](xref:Microsoft.ML.Data.RegressionPredictionTransformer%601) modelu [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters)regresji liniowej, który tworzy, że wyjścia .</span><span class="sxs-lookup"><span data-stu-id="5e10c-124">The pre-trained model was trained using the linear regression model [`OnlineGradientDescentTrainer`](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) which creates a[`RegressionPredictionTransformer`](xref:Microsoft.ML.Data.RegressionPredictionTransformer%601) that outputs [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters).</span></span> <span data-ttu-id="5e10c-125">Te parametry modelu regresji liniowej zawierają wyuczoną stronniczość i wagi lub współczynniki modelu.</span><span class="sxs-lookup"><span data-stu-id="5e10c-125">These linear regression model parameters contain the learned bias and weights or coefficients of the model.</span></span> <span data-ttu-id="5e10c-126">Wartości te będą używane jako punkt wyjścia dla nowego modelu ponownie przeszkolony.</span><span class="sxs-lookup"><span data-stu-id="5e10c-126">These values will be used as a starting point for the new re-trained model.</span></span>

```csharp
// Extract trained model parameters
LinearRegressionModelParameters originalModelParameters =
    ((ISingleFeaturePredictionTransformer<object>)trainedModel).Model as LinearRegressionModelParameters;
```

## <a name="re-train-model"></a><span data-ttu-id="5e10c-127">Przetrain model</span><span class="sxs-lookup"><span data-stu-id="5e10c-127">Re-train model</span></span>

<span data-ttu-id="5e10c-128">Proces przekwalifikowania modelu nie różni się od szkolenia modelu.</span><span class="sxs-lookup"><span data-stu-id="5e10c-128">The process for retraining a model is no different than that of training a model.</span></span> <span data-ttu-id="5e10c-129">Jedyną różnicą [`Fit`](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*) jest metoda oprócz danych również przyjmuje jako dane wejściowe oryginalne parametry modelu wyuczonego i używa ich jako punkt wyjścia w procesie ponownego szkolenia.</span><span class="sxs-lookup"><span data-stu-id="5e10c-129">The only difference is, the [`Fit`](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*) method in addition to the data also takes as input the original learned model parameters and uses them as a starting point in the re-training process.</span></span>

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

## <a name="compare-model-parameters"></a><span data-ttu-id="5e10c-130">Porównanie parametrów modelu</span><span class="sxs-lookup"><span data-stu-id="5e10c-130">Compare model parameters</span></span>

<span data-ttu-id="5e10c-131">Skąd wiesz, czy przekwalifikowanie rzeczywiście się stało?</span><span class="sxs-lookup"><span data-stu-id="5e10c-131">How do you know if re-training actually happened?</span></span> <span data-ttu-id="5e10c-132">Jednym ze sposobów byłoby porównanie, czy parametry ponownie przeszkolonego modelu różnią się od parametrów oryginalnego modelu.</span><span class="sxs-lookup"><span data-stu-id="5e10c-132">One way would be to compare whether the re-trained model's parameters are different than those of the original model.</span></span> <span data-ttu-id="5e10c-133">Poniższy przykład kodu porównuje oryginał z przekwalifikowanymi wagami modelu i wyprowadza je do konsoli.</span><span class="sxs-lookup"><span data-stu-id="5e10c-133">The code sample below compares the original against the re-trained model weights and outputs them to the console.</span></span>

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

<span data-ttu-id="5e10c-134">W poniższej tabeli pokazano, jak może wyglądać dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="5e10c-134">The table below shows what the output might look like.</span></span>

|<span data-ttu-id="5e10c-135">Oryginał</span><span class="sxs-lookup"><span data-stu-id="5e10c-135">Original</span></span> | <span data-ttu-id="5e10c-136">Przekwalifikowany</span><span class="sxs-lookup"><span data-stu-id="5e10c-136">Retrained</span></span> | <span data-ttu-id="5e10c-137">Różnica</span><span class="sxs-lookup"><span data-stu-id="5e10c-137">Difference</span></span> |
|---|---|---|
| <span data-ttu-id="5e10c-138">33039.86</span><span class="sxs-lookup"><span data-stu-id="5e10c-138">33039.86</span></span> | <span data-ttu-id="5e10c-139">56293.76</span><span class="sxs-lookup"><span data-stu-id="5e10c-139">56293.76</span></span> | <span data-ttu-id="5e10c-140">-23253.9</span><span class="sxs-lookup"><span data-stu-id="5e10c-140">-23253.9</span></span> |
| <span data-ttu-id="5e10c-141">29099.14</span><span class="sxs-lookup"><span data-stu-id="5e10c-141">29099.14</span></span> | <span data-ttu-id="5e10c-142">49586.03</span><span class="sxs-lookup"><span data-stu-id="5e10c-142">49586.03</span></span> | <span data-ttu-id="5e10c-143">-20486.89</span><span class="sxs-lookup"><span data-stu-id="5e10c-143">-20486.89</span></span> |
| <span data-ttu-id="5e10c-144">28938.38</span><span class="sxs-lookup"><span data-stu-id="5e10c-144">28938.38</span></span> | <span data-ttu-id="5e10c-145">48609.23</span><span class="sxs-lookup"><span data-stu-id="5e10c-145">48609.23</span></span> | <span data-ttu-id="5e10c-146">-19670.85</span><span class="sxs-lookup"><span data-stu-id="5e10c-146">-19670.85</span></span> |
| <span data-ttu-id="5e10c-147">30484.02</span><span class="sxs-lookup"><span data-stu-id="5e10c-147">30484.02</span></span> | <span data-ttu-id="5e10c-148">53745.43</span><span class="sxs-lookup"><span data-stu-id="5e10c-148">53745.43</span></span> | <span data-ttu-id="5e10c-149">-23261.41</span><span class="sxs-lookup"><span data-stu-id="5e10c-149">-23261.41</span></span> |
