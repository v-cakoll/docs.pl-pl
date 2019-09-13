---
title: Co to jest ML.NET i jak to działa?
description: ML.NET umożliwia dodawanie uczenia maszynowego do aplikacji .NET, w scenariuszach w trybie online lub offline. Dzięki tej możliwości można dokonać automatycznych prognoz przy użyciu danych dostępnych dla aplikacji bez konieczności podłączania do sieci w celu użycia ML.NET. W tym artykule objaśniono podstawowe informacje dotyczące uczenia maszynowego w programie ML.NET.
ms.date: 08/26/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
author: natke
ms.openlocfilehash: d49a4bdfec133fe805bc9d534e04edf2f9ca5726
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929412"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a><span data-ttu-id="15ab0-105">Co to jest ML.NET i jak to działa?</span><span class="sxs-lookup"><span data-stu-id="15ab0-105">What is ML.NET and how does it work?</span></span>

<span data-ttu-id="15ab0-106">ML.NET umożliwia dodawanie uczenia maszynowego do aplikacji .NET, w scenariuszach w trybie online lub offline.</span><span class="sxs-lookup"><span data-stu-id="15ab0-106">ML.NET gives you the ability to add machine learning to .NET applications, in either online or offline scenarios.</span></span> <span data-ttu-id="15ab0-107">Dzięki tej możliwości można dokonać automatycznych prognoz przy użyciu danych dostępnych dla aplikacji bez konieczności podłączania do sieci.</span><span class="sxs-lookup"><span data-stu-id="15ab0-107">With this capability, you can make automatic predictions using the data available to your application without having to be connected to a network.</span></span> <span data-ttu-id="15ab0-108">W tym artykule objaśniono podstawowe informacje dotyczące uczenia maszynowego w programie ML.NET.</span><span class="sxs-lookup"><span data-stu-id="15ab0-108">This article explains the basics of machine learning in ML.NET.</span></span> 

<span data-ttu-id="15ab0-109">Przykłady typu przewidywania, które można wprowadzić za pomocą ML.NET, to m.in.:</span><span class="sxs-lookup"><span data-stu-id="15ab0-109">Examples of the type of predictions that you can make with ML.NET include:</span></span>

|||
|-|-|
|<span data-ttu-id="15ab0-110">Klasyfikacja/Kategoryzacja</span><span class="sxs-lookup"><span data-stu-id="15ab0-110">Classification/Categorization</span></span>|<span data-ttu-id="15ab0-111">Automatycznie Podziel Opinie klientów na kategorie dodatnie i ujemne</span><span class="sxs-lookup"><span data-stu-id="15ab0-111">Automatically divide customer feedback into positive and negative categories</span></span>|
|<span data-ttu-id="15ab0-112">Wartości ciągłe regresji/przewidywania</span><span class="sxs-lookup"><span data-stu-id="15ab0-112">Regression/Predict continuous values</span></span>|<span data-ttu-id="15ab0-113">Przewidywanie ceny domów na podstawie rozmiaru i lokalizacji</span><span class="sxs-lookup"><span data-stu-id="15ab0-113">Predict the price of houses based on size and location</span></span>|
|<span data-ttu-id="15ab0-114">Wykrywanie anomalii</span><span class="sxs-lookup"><span data-stu-id="15ab0-114">Anomaly Detection</span></span>|<span data-ttu-id="15ab0-115">Wykrywanie fałszywych transakcji bankowych</span><span class="sxs-lookup"><span data-stu-id="15ab0-115">Detect fraudulent banking transactions</span></span> |
|<span data-ttu-id="15ab0-116">Zalecenia</span><span class="sxs-lookup"><span data-stu-id="15ab0-116">Recommendations</span></span>|<span data-ttu-id="15ab0-117">Sugeruj produkty, które kupujący online może chcieć kupić, w oparciu o ich poprzednie zakupy</span><span class="sxs-lookup"><span data-stu-id="15ab0-117">Suggest products that online shoppers may want to buy, based on their previous purchases</span></span>|

## <a name="hello-mlnet-world"></a><span data-ttu-id="15ab0-118">Witaj w świecie ML.NET</span><span class="sxs-lookup"><span data-stu-id="15ab0-118">Hello ML.NET World</span></span>

<span data-ttu-id="15ab0-119">Kod w poniższym fragmencie kodu demonstruje najprostszą aplikację ML.NET.</span><span class="sxs-lookup"><span data-stu-id="15ab0-119">The code in the following snippet demonstrates the simplest ML.NET application.</span></span> <span data-ttu-id="15ab0-120">Ten przykład tworzy model regresji liniowej do przewidywania cen dla domu przy użyciu rozmiaru domu i danych cen.</span><span class="sxs-lookup"><span data-stu-id="15ab0-120">This example constructs a linear regression model to predict house prices using house size and price data.</span></span> <span data-ttu-id="15ab0-121">W aplikacjach w czasie rzeczywistym Twoje dane i model będą znacznie bardziej skomplikowane.</span><span class="sxs-lookup"><span data-stu-id="15ab0-121">In your real-life applications, your data and model will be much more complex.</span></span>

 ```csharp
    using System;
    using Microsoft.ML;
    using Microsoft.ML.Data;
    
    class Program
    {
        public class HouseData
        {
            public float Size { get; set; }
            public float Price { get; set; }
        }
    
        public class Prediction
        {
            [ColumnName("Score")]
            public float Price { get; set; }
        }
    
        static void Main(string[] args)
        {
            MLContext mlContext = new MLContext();
    
            // 1. Import or create training data
            HouseData[] houseData = {
                new HouseData() { Size = 1.1F, Price = 1.2F },
                new HouseData() { Size = 1.9F, Price = 2.3F },
                new HouseData() { Size = 2.8F, Price = 3.0F },
                new HouseData() { Size = 3.4F, Price = 3.7F } };
            IDataView trainingData = mlContext.Data.LoadFromEnumerable(houseData);

            // 2. Specify data preparation and model training pipeline
            var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
                .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
    
            // 3. Train model
            var model = pipeline.Fit(trainingData);
    
            // 4. Make a prediction
            var size = new HouseData() { Size = 2.5F };
            var price = mlContext.Model.CreatePredictionEngine<HouseData, Prediction>(model).Predict(size);

            Console.WriteLine($"Predicted price for size: {size.Size*1000} sq ft= {price.Price*100:C}k");

            // Predicted price for size: 2500 sq ft= $261.98k
        }
    } 
```

## <a name="code-workflow"></a><span data-ttu-id="15ab0-122">Przepływ pracy kodu</span><span class="sxs-lookup"><span data-stu-id="15ab0-122">Code workflow</span></span>

<span data-ttu-id="15ab0-123">Poniższy diagram przedstawia strukturę kodu aplikacji, a także proces iteracyjny projektowania modelu:</span><span class="sxs-lookup"><span data-stu-id="15ab0-123">The following diagram represents the application code structure, as well as the iterative process of model development:</span></span>

- <span data-ttu-id="15ab0-124">Zbieranie i ładowanie danych szkoleniowych do obiektu **IDataView**</span><span class="sxs-lookup"><span data-stu-id="15ab0-124">Collect and load training data into an **IDataView** object</span></span>
- <span data-ttu-id="15ab0-125">Określ potok operacji, aby wyodrębnić funkcje i zastosować algorytm uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="15ab0-125">Specify a pipeline of operations to extract features and apply a machine learning algorithm</span></span>
- <span data-ttu-id="15ab0-126">Uczenie modelu przez wywoływanie funkcji **dopasowania ()** na potoku</span><span class="sxs-lookup"><span data-stu-id="15ab0-126">Train a model by calling **Fit()** on the pipeline</span></span>
- <span data-ttu-id="15ab0-127">Oceń model i wykonaj iterację w celu usprawnienia</span><span class="sxs-lookup"><span data-stu-id="15ab0-127">Evaluate the model and iterate to improve</span></span>
- <span data-ttu-id="15ab0-128">Zapisz model w formacie binarnym, który ma być używany w aplikacji</span><span class="sxs-lookup"><span data-stu-id="15ab0-128">Save the model into binary format, for use in an application</span></span>
- <span data-ttu-id="15ab0-129">Załaduj model z powrotem do obiektu **ITransformer**</span><span class="sxs-lookup"><span data-stu-id="15ab0-129">Load the model back into an **ITransformer** object</span></span>
- <span data-ttu-id="15ab0-130">Wykonaj przewidywania, wywołując **CreatePredictionEngine. predykcyjny ()**</span><span class="sxs-lookup"><span data-stu-id="15ab0-130">Make predictions by calling **CreatePredictionEngine.Predict()**</span></span>

![Przepływ tworzenia aplikacji ML.NET, w tym składniki służące do generowania danych, tworzenia potoku, szkolenia modeli, oceny modelu i użycia modelu](./media/mldotnet-annotated-workflow.png) 

<span data-ttu-id="15ab0-132">Przyjrzyjmy się nieco bardziej szczegółowym koncepcjom.</span><span class="sxs-lookup"><span data-stu-id="15ab0-132">Let's dig a little deeper into those concepts.</span></span>

## <a name="machine-learning-model"></a><span data-ttu-id="15ab0-133">Model uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="15ab0-133">Machine learning model</span></span>

<span data-ttu-id="15ab0-134">Model ML.NET jest obiektem, który zawiera przekształcenia do wykonania na danych wejściowych w celu osiągnięcia przewidywanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="15ab0-134">An ML.NET model is an object that contains transformations to perform on your input data to arrive at the predicted output.</span></span>

### <a name="basic"></a><span data-ttu-id="15ab0-135">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="15ab0-135">Basic</span></span>

<span data-ttu-id="15ab0-136">Najpopularniejszym modelem jest dwuwymiarowa regresja liniowa, w której jedna ciągła ilość jest proporcjonalna do innej, jak w powyższym przykładzie cen domu.</span><span class="sxs-lookup"><span data-stu-id="15ab0-136">The most basic model is two-dimensional linear regression, where one continuous quantity is proportional to another, as in the house price example above.</span></span> 

![Model regresji liniowej z parametrami bias i wagi](./media/linear-regression-model.svg)

<span data-ttu-id="15ab0-138">Model jest po prostu: $Price = b + rozmiar \* w $.</span><span class="sxs-lookup"><span data-stu-id="15ab0-138">The model is simply: $Price = b + Size \* w$.</span></span> <span data-ttu-id="15ab0-139">Parametry $b $ i $w $ są szacowane przez dopasowanie wiersza do pary par (size, Price).</span><span class="sxs-lookup"><span data-stu-id="15ab0-139">The parameters $b$ and $w$ are estimated by fitting a line on a set of (size, price) pairs.</span></span> <span data-ttu-id="15ab0-140">Dane używane do znajdowania parametrów modelu są nazywane **danymi szkoleniowymi**.</span><span class="sxs-lookup"><span data-stu-id="15ab0-140">The data used to find the parameters of the model is called **training data**.</span></span> <span data-ttu-id="15ab0-141">Dane wejściowe modelu uczenia maszynowego są nazywane **funkcjami**.</span><span class="sxs-lookup"><span data-stu-id="15ab0-141">The inputs of a machine learning model are called **features**.</span></span> <span data-ttu-id="15ab0-142">W tym przykładzie $Size $ jest jedyną funkcją.</span><span class="sxs-lookup"><span data-stu-id="15ab0-142">In this example, $Size$ is the only feature.</span></span> <span data-ttu-id="15ab0-143">Wartości typu podstawa — prawdziwie używane do uczenia modelu uczenia maszynowego są nazywane **etykietami**.</span><span class="sxs-lookup"><span data-stu-id="15ab0-143">The ground-truth values used to train a machine learning model are called **labels**.</span></span> <span data-ttu-id="15ab0-144">W tym miejscu $Price $ wartości w zestawie danych szkoleniowych są etykietami.</span><span class="sxs-lookup"><span data-stu-id="15ab0-144">Here, the $Price$ values in the training data set are the labels.</span></span>

### <a name="more-complex"></a><span data-ttu-id="15ab0-145">Bardziej skomplikowane</span><span class="sxs-lookup"><span data-stu-id="15ab0-145">More complex</span></span>

<span data-ttu-id="15ab0-146">Bardziej skomplikowany model klasyfikuje transakcje finansowe do kategorii przy użyciu opisu tekstu transakcji.</span><span class="sxs-lookup"><span data-stu-id="15ab0-146">A more complex model classifies financial transactions into categories using the transaction text description.</span></span>

<span data-ttu-id="15ab0-147">Każdy opis transakcji jest podzielony na zestaw funkcji przez usunięcie zbędnych słów i znaków oraz liczenie kombinacji wyrazów i znaków.</span><span class="sxs-lookup"><span data-stu-id="15ab0-147">Each transaction description is broken down into a set of features by removing redundant words and characters, and counting word and character combinations.</span></span> <span data-ttu-id="15ab0-148">Zestaw funkcji służy do uczenia modelu liniowego na podstawie zestawu kategorii w danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="15ab0-148">The feature set is used to train a linear model based on the set of categories in the training data.</span></span> <span data-ttu-id="15ab0-149">Im bardziej podobne są nowe opisy w zestawie szkoleniowym, tym bardziej prawdopodobnie zostanie przypisany do tej samej kategorii.</span><span class="sxs-lookup"><span data-stu-id="15ab0-149">The more similar a new description is to the ones in the training set, the more likely it will be assigned to the same category.</span></span> 

![Model klasyfikacji tekstu](./media/text-classification-model.svg)

<span data-ttu-id="15ab0-151">Model cen domu i model klasyfikacji tekstu to modele liniowe .</span><span class="sxs-lookup"><span data-stu-id="15ab0-151">Both the house price model and the text classification model are **linear** models.</span></span> <span data-ttu-id="15ab0-152">W zależności od charakteru danych i rozwiązywanego problemu można także używać modeli **drzewa decyzyjnego** , **ogólnych modeli dodatków** i innych.</span><span class="sxs-lookup"><span data-stu-id="15ab0-152">Depending on the nature of your data and the problem you are solving, you can also use **decision tree** models, **generalized additive** models, and others.</span></span> <span data-ttu-id="15ab0-153">Więcej informacji o modelach można znaleźć w części [zadania](./resources/tasks.md).</span><span class="sxs-lookup"><span data-stu-id="15ab0-153">You can find out more about the models in [Tasks](./resources/tasks.md).</span></span>

## <a name="data-preparation"></a><span data-ttu-id="15ab0-154">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="15ab0-154">Data preparation</span></span>

<span data-ttu-id="15ab0-155">W większości przypadków dostępne dane nie są odpowiednie do użycia bezpośrednio do uczenia modelu uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="15ab0-155">In most cases, the data that you have available isn't suitable to be used directly to train a machine learning model.</span></span> <span data-ttu-id="15ab0-156">Dane pierwotne muszą zostać przygotowane lub wstępnie przetworzone, aby można było ich użyć w celu znalezienia parametrów modelu.</span><span class="sxs-lookup"><span data-stu-id="15ab0-156">The raw data needs to be prepared, or pre-processed before it can be used to find the parameters of your model.</span></span> <span data-ttu-id="15ab0-157">Może być konieczne przekonwertowanie danych z wartości ciągu na reprezentację liczbową.</span><span class="sxs-lookup"><span data-stu-id="15ab0-157">Your data may need to be converted from string values to a numerical representation.</span></span> <span data-ttu-id="15ab0-158">Dane wejściowe mogą zawierać nadmiarowe informacje.</span><span class="sxs-lookup"><span data-stu-id="15ab0-158">You might have redundant information in your input data.</span></span> <span data-ttu-id="15ab0-159">Może być konieczne zmniejszenie lub powiększenie wymiarów danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="15ab0-159">You may need to reduce or expand the dimensions of your input data.</span></span> <span data-ttu-id="15ab0-160">Może być konieczne znormalizowanie lub skalowanie danych.</span><span class="sxs-lookup"><span data-stu-id="15ab0-160">Your data might need to be normalized or scaled.</span></span>

<span data-ttu-id="15ab0-161">W [samouczkach ml.NET](./tutorials/index.md) przedstawiono różne potoki przetwarzania danych dotyczące tekstu, obrazów, liczb i danych szeregów czasowych używanych do określonych zadań uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="15ab0-161">The [ML.NET tutorials](./tutorials/index.md) teach you about different data processing pipelines for text, image, numerical, and time-series data used for specific machine learning tasks.</span></span>

<span data-ttu-id="15ab0-162">[Sposób przygotowania danych](./how-to-guides/prepare-data-ml-net.md) pokazuje, jak zwykle zastosować Przygotowywanie danych.</span><span class="sxs-lookup"><span data-stu-id="15ab0-162">[How to prepare your data](./how-to-guides/prepare-data-ml-net.md) shows you how to applied data preparation more generally.</span></span>

<span data-ttu-id="15ab0-163">Dodatek wszystkich [dostępnych transformacji](./resources/transforms.md) można znaleźć w sekcji Resources (zasoby).</span><span class="sxs-lookup"><span data-stu-id="15ab0-163">You can find an appendix of all of the [available transformations](./resources/transforms.md) in the resources section.</span></span>

## <a name="model-evaluation"></a><span data-ttu-id="15ab0-164">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="15ab0-164">Model evaluation</span></span>

<span data-ttu-id="15ab0-165">Po przeprowadzeniu szkolenia modelu wiesz, jak dobrze będzie w przyszłości prognozować?</span><span class="sxs-lookup"><span data-stu-id="15ab0-165">Once you have trained your model, how do you know how well it will make future predictions?</span></span> <span data-ttu-id="15ab0-166">Dzięki ML.NET można oszacować model na podstawie nowych danych testowych.</span><span class="sxs-lookup"><span data-stu-id="15ab0-166">With ML.NET, you can evaluate your model against some new test data.</span></span> 

<span data-ttu-id="15ab0-167">Każdy typ zadania uczenia maszynowego ma metryki używane do oszacowania dokładności i dokładności modelu względem zestawu danych testowych.</span><span class="sxs-lookup"><span data-stu-id="15ab0-167">Each type of machine learning task has metrics used to evaluate the accuracy and precision of the model against the test data set.</span></span>

<span data-ttu-id="15ab0-168">W naszym przykładzie cen domu użyto zadania regresji .</span><span class="sxs-lookup"><span data-stu-id="15ab0-168">For our house price example, we used the **Regression** task.</span></span> <span data-ttu-id="15ab0-169">Aby oszacować model, Dodaj następujący kod do oryginalnego przykładu.</span><span class="sxs-lookup"><span data-stu-id="15ab0-169">To evaluate the model, add the following code to the original sample.</span></span>

```csharp
        HouseData[] testHouseData =
        {
            new HouseData() { Size = 1.1F, Price = 0.98F },
            new HouseData() { Size = 1.9F, Price = 2.1F },
            new HouseData() { Size = 2.8F, Price = 2.9F },
            new HouseData() { Size = 3.4F, Price = 3.6F }
        };

        var testHouseDataView = mlContext.Data.LoadFromEnumerable(testHouseData);
        var testPriceDataView = model.Transform(testHouseDataView);
                
        var metrics = mlContext.Regression.Evaluate(testPriceDataView, labelColumnName: "Price");

        Console.WriteLine($"R^2: {metrics.RSquared:0.##}");
        Console.WriteLine($"RMS error: {metrics.RootMeanSquaredError:0.##}");

        // R^2: 0.96
        // RMS error: 0.19
```

<span data-ttu-id="15ab0-170">Metryki oceny informują o tym, że błąd ma niską ish i że korelacja między przewidywanym wyjściem i wyjściem testu jest wysoka.</span><span class="sxs-lookup"><span data-stu-id="15ab0-170">The evaluation metrics tell you that the error is low-ish, and that correlation between the predicted output and the test output is high.</span></span> <span data-ttu-id="15ab0-171">To było łatwe!</span><span class="sxs-lookup"><span data-stu-id="15ab0-171">That was easy!</span></span> <span data-ttu-id="15ab0-172">W rzeczywistych przykładach zwiększa się to w celu osiągnięcia dobrych metryk modelu.</span><span class="sxs-lookup"><span data-stu-id="15ab0-172">In real examples, it takes more tuning to achieve good model metrics.</span></span>

## <a name="mlnet-architecture"></a><span data-ttu-id="15ab0-173">Architektura ML.NET</span><span class="sxs-lookup"><span data-stu-id="15ab0-173">ML.NET architecture</span></span>

<span data-ttu-id="15ab0-174">W tej sekcji przejdziemy do wzorca architektury ML.NET.</span><span class="sxs-lookup"><span data-stu-id="15ab0-174">In this section, we go through the architectural patterns of ML.NET.</span></span> <span data-ttu-id="15ab0-175">Jeśli jesteś doświadczonym deweloperem platformy .NET, niektóre z tych wzorców będą znane użytkownikowi, a niektóre z nich będą mniej znane.</span><span class="sxs-lookup"><span data-stu-id="15ab0-175">If you are an experienced .NET developer, some of these patterns will be familiar to you, and some will be less familiar.</span></span> <span data-ttu-id="15ab0-176">Zaczekaj, aż szczegółowemy!</span><span class="sxs-lookup"><span data-stu-id="15ab0-176">Hold tight, while we dive in!</span></span>

<span data-ttu-id="15ab0-177">Aplikacja ml.NET rozpoczyna się od <xref:Microsoft.ML.MLContext> obiektu.</span><span class="sxs-lookup"><span data-stu-id="15ab0-177">An ML.NET application starts with an <xref:Microsoft.ML.MLContext> object.</span></span> <span data-ttu-id="15ab0-178">Ten obiekt singleton zawiera **wykazy**.</span><span class="sxs-lookup"><span data-stu-id="15ab0-178">This singleton object contains **catalogs**.</span></span> <span data-ttu-id="15ab0-179">Katalog jest fabryką służącą do ładowania i zapisywania danych, przekształcania, instruktorów i składników operacji modelu.</span><span class="sxs-lookup"><span data-stu-id="15ab0-179">A catalog is a factory for data loading and saving, transforms, trainers, and model operation components.</span></span> <span data-ttu-id="15ab0-180">Każdy obiekt wykazu ma metody do tworzenia różnych typów składników:</span><span class="sxs-lookup"><span data-stu-id="15ab0-180">Each catalog object has methods to create the different types of components:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="15ab0-181">Ładowanie i zapisywanie danych</span><span class="sxs-lookup"><span data-stu-id="15ab0-181">Data loading and saving</span></span>||<xref:Microsoft.ML.DataOperationsCatalog>||
|<span data-ttu-id="15ab0-182">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="15ab0-182">Data preparation</span></span>||<xref:Microsoft.ML.TransformsCatalog>||
|<span data-ttu-id="15ab0-183">Algorytmy szkoleniowe</span><span class="sxs-lookup"><span data-stu-id="15ab0-183">Training algorithms</span></span>|<span data-ttu-id="15ab0-184">Klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="15ab0-184">Binary classification</span></span>|<xref:Microsoft.ML.BinaryClassificationCatalog>||
||<span data-ttu-id="15ab0-185">Klasyfikacja wieloklasowa</span><span class="sxs-lookup"><span data-stu-id="15ab0-185">Multiclass classification</span></span>|<xref:Microsoft.ML.MulticlassClassificationCatalog>||
||<span data-ttu-id="15ab0-186">Wykrywanie anomalii</span><span class="sxs-lookup"><span data-stu-id="15ab0-186">Anomaly detection</span></span>|<xref:Microsoft.ML.AnomalyDetectionCatalog>||
||<span data-ttu-id="15ab0-187">Usługę</span><span class="sxs-lookup"><span data-stu-id="15ab0-187">Clustering</span></span>|<xref:Microsoft.ML.ClusteringCatalog>||
||<span data-ttu-id="15ab0-188">Prognozowanie</span><span class="sxs-lookup"><span data-stu-id="15ab0-188">Forecasting</span></span>|<xref:Microsoft.ML.ForecastingCatalog>||
||<span data-ttu-id="15ab0-189">Określania</span><span class="sxs-lookup"><span data-stu-id="15ab0-189">Ranking</span></span>|<xref:Microsoft.ML.RankingCatalog>||
||<span data-ttu-id="15ab0-190">Regresji</span><span class="sxs-lookup"><span data-stu-id="15ab0-190">Regression</span></span>|<xref:Microsoft.ML.RegressionCatalog>||
||<span data-ttu-id="15ab0-191">Zalecenie</span><span class="sxs-lookup"><span data-stu-id="15ab0-191">Recommendation</span></span>|<xref:Microsoft.ML.RecommendationCatalog>|<span data-ttu-id="15ab0-192">Dodawanie pakietu `Microsoft.ML.Recommender` NuGet</span><span class="sxs-lookup"><span data-stu-id="15ab0-192">add the `Microsoft.ML.Recommender` NuGet package</span></span>|
||<span data-ttu-id="15ab0-193">Szeregów czasowych</span><span class="sxs-lookup"><span data-stu-id="15ab0-193">TimeSeries</span></span>|<xref:Microsoft.ML.TimeSeriesCatalog>|<span data-ttu-id="15ab0-194">Dodawanie pakietu `Microsoft.ML.TimeSeries` NuGet</span><span class="sxs-lookup"><span data-stu-id="15ab0-194">add the `Microsoft.ML.TimeSeries` NuGet package</span></span>|
|<span data-ttu-id="15ab0-195">Użycie modelu</span><span class="sxs-lookup"><span data-stu-id="15ab0-195">Model usage</span></span> ||<xref:Microsoft.ML.ModelOperationsCatalog>||

<span data-ttu-id="15ab0-196">Możesz przejść do metod tworzenia w każdej z powyższych kategorii.</span><span class="sxs-lookup"><span data-stu-id="15ab0-196">You can navigate to the creation methods in each of the above categories.</span></span> <span data-ttu-id="15ab0-197">W przypadku korzystania z programu Visual Studio wykazy są wyświetlane za pośrednictwem technologii IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="15ab0-197">Using Visual Studio, the catalogs show up via IntelliSense.</span></span>

   ![Technologia IntelliSense dla instruktorów regresji](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a><span data-ttu-id="15ab0-199">Kompilowanie potoku</span><span class="sxs-lookup"><span data-stu-id="15ab0-199">Build the pipeline</span></span>

<span data-ttu-id="15ab0-200">W każdym katalogu jest zestaw metod rozszerzających.</span><span class="sxs-lookup"><span data-stu-id="15ab0-200">Inside each catalog is a set of extension methods.</span></span> <span data-ttu-id="15ab0-201">Przyjrzyjmy się sposobom, w jaki metody rozszerzające są używane do tworzenia potoku szkoleniowego.</span><span class="sxs-lookup"><span data-stu-id="15ab0-201">Let's look at how extension methods are used to create a training pipeline.</span></span>

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
```

<span data-ttu-id="15ab0-202">W tym fragmencie kodu `Concatenate` i `Sdca` są obie metody w wykazie.</span><span class="sxs-lookup"><span data-stu-id="15ab0-202">In the snippet, `Concatenate` and `Sdca` are both methods in the catalog.</span></span> <span data-ttu-id="15ab0-203">Każdy z nich tworzy obiekt [IEstimator](xref:Microsoft.ML.IEstimator%601) , który jest dołączany do potoku.</span><span class="sxs-lookup"><span data-stu-id="15ab0-203">They each create an [IEstimator](xref:Microsoft.ML.IEstimator%601) object that is appended to the pipeline.</span></span>

<span data-ttu-id="15ab0-204">W tym momencie obiekty są tworzone tylko.</span><span class="sxs-lookup"><span data-stu-id="15ab0-204">At this point, the objects are created only.</span></span> <span data-ttu-id="15ab0-205">Nie wykonano żadnego wykonania.</span><span class="sxs-lookup"><span data-stu-id="15ab0-205">No execution has happened.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="15ab0-206">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="15ab0-206">Train the model</span></span>

<span data-ttu-id="15ab0-207">Po utworzeniu obiektów w potoku, dane mogą być używane do uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="15ab0-207">Once the objects in the pipeline have been created, data can be used to train the model.</span></span>

```csharp
    var model = pipeline.Fit(trainingData);
```

<span data-ttu-id="15ab0-208">Wywołanie `Fit()` używa danych szkolenia wejściowego do oszacowania parametrów modelu.</span><span class="sxs-lookup"><span data-stu-id="15ab0-208">Calling `Fit()` uses the input training data to estimate the parameters of the model.</span></span> <span data-ttu-id="15ab0-209">Jest to nazywane uczeniem modelu.</span><span class="sxs-lookup"><span data-stu-id="15ab0-209">This is known as training the model.</span></span> <span data-ttu-id="15ab0-210">Należy pamiętać, że model regresji liniowej powyżej ma dwa parametry modelu: **bias** i **waga**.</span><span class="sxs-lookup"><span data-stu-id="15ab0-210">Remember, the linear regression model above had two model parameters: **bias** and **weight**.</span></span> <span data-ttu-id="15ab0-211">`Fit()` Po wywołaniu wartości parametrów są znane.</span><span class="sxs-lookup"><span data-stu-id="15ab0-211">After the `Fit()` call, the values of the parameters are known.</span></span> <span data-ttu-id="15ab0-212">Większość modeli będzie zawierać wiele innych parametrów niż to.</span><span class="sxs-lookup"><span data-stu-id="15ab0-212">Most models will have many more parameters than this.</span></span>

<span data-ttu-id="15ab0-213">Możesz dowiedzieć się więcej na temat szkolenia modeli w temacie [Jak szkolić model](./how-to-guides/train-machine-learning-model-ml-net.md)</span><span class="sxs-lookup"><span data-stu-id="15ab0-213">You can learn more about model training in [How to train your model](./how-to-guides/train-machine-learning-model-ml-net.md)</span></span>

<span data-ttu-id="15ab0-214">Obiekt modelu z wynikiem jest zaimplementowany <xref:Microsoft.ML.ITransformer> przez interfejs.</span><span class="sxs-lookup"><span data-stu-id="15ab0-214">The resulting model object implements the <xref:Microsoft.ML.ITransformer> interface.</span></span> <span data-ttu-id="15ab0-215">Oznacza to, że model przekształca dane wejściowe w przewidywania.</span><span class="sxs-lookup"><span data-stu-id="15ab0-215">That is, the model transforms input data into predictions.</span></span>

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a><span data-ttu-id="15ab0-216">Korzystanie z modelu</span><span class="sxs-lookup"><span data-stu-id="15ab0-216">Use the model</span></span>

<span data-ttu-id="15ab0-217">Można przekształcać dane wejściowe w prognozy zbiorcze lub pojedyncze dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="15ab0-217">You can transform input data into predictions in bulk, or one input at a time.</span></span> <span data-ttu-id="15ab0-218">W przykładzie cen domu firma Microsoft: w sposób zbiorczy na potrzeby oceny modelu i po jednym naraz, aby utworzyć nowe prognozowanie.</span><span class="sxs-lookup"><span data-stu-id="15ab0-218">In the house price example, we did both: in bulk for the purpose of evaluating the model, and one at a time to make a new prediction.</span></span> <span data-ttu-id="15ab0-219">Przyjrzyjmy się tworzeniu pojedynczych prognoz.</span><span class="sxs-lookup"><span data-stu-id="15ab0-219">Let's look at making single predictions.</span></span>

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = mlContext.CreatePredictionEngine<HouseData, Prediction>(model);
    var price = predEngine.Predict(size);
```
 
<span data-ttu-id="15ab0-220">`CreatePredictionEngine()` Metoda przyjmuje klasę wejściową i klasę wyjściową.</span><span class="sxs-lookup"><span data-stu-id="15ab0-220">The `CreatePredictionEngine()` method takes an input class and an output class.</span></span> <span data-ttu-id="15ab0-221">Nazwy pól i/lub atrybuty kodu określają nazwy kolumn danych używanych podczas szkoleń i prognozowania modeli.</span><span class="sxs-lookup"><span data-stu-id="15ab0-221">The field names and/or code attributes determine the names of the data columns used during model training and prediction.</span></span> <span data-ttu-id="15ab0-222">Informacje na temat [sposobu tworzenia pojedynczego przewidywania](./how-to-guides/single-predict-model-ml-net.md) można znaleźć w sekcji How to.</span><span class="sxs-lookup"><span data-stu-id="15ab0-222">You can read about  [How to make a single prediction](./how-to-guides/single-predict-model-ml-net.md) in the How-to section.</span></span>

### <a name="data-models-and-schema"></a><span data-ttu-id="15ab0-223">Modele danych i schemat</span><span class="sxs-lookup"><span data-stu-id="15ab0-223">Data models and schema</span></span>

<span data-ttu-id="15ab0-224">Na początku potoku uczenia maszynowego ML.NET są obiekty [DataView](xref:Microsoft.ML.IDataView) .</span><span class="sxs-lookup"><span data-stu-id="15ab0-224">At the core of an ML.NET machine learning pipeline are [DataView](xref:Microsoft.ML.IDataView) objects.</span></span>

<span data-ttu-id="15ab0-225">Każda transformacja w potoku ma schemat wejściowy (nazwy danych, typy i rozmiary, których transformacja oczekuje na dane wejściowe); oraz schemat danych wyjściowych (nazwy danych, typy i rozmiary generowane przez transformację po przekształceniu).</span><span class="sxs-lookup"><span data-stu-id="15ab0-225">Each transformation in the pipeline has an input schema (data names, types, and sizes that the transform expects to see on its input); and an output schema (data names, types, and sizes that the transform produces after the transformation).</span></span> <span data-ttu-id="15ab0-226">Poniższy dokument zawiera szczegółowy opis [interfejsu IDataView oraz jego systemu typów](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html).</span><span class="sxs-lookup"><span data-stu-id="15ab0-226">The following document provides an in-depth explanation of the [IDataView interface and its type system](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html).</span></span>

<span data-ttu-id="15ab0-227">Jeśli schemat danych wyjściowych z jednego przekształcenia w potoku nie jest zgodny ze schematem wejściowym kolejnej transformacji, ML.NET zgłosi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="15ab0-227">If the output schema from one transform in the pipeline doesn't match the input schema of the next transform, ML.NET will throw an exception.</span></span>

<span data-ttu-id="15ab0-228">Obiekt widoku danych ma kolumny i wiersze.</span><span class="sxs-lookup"><span data-stu-id="15ab0-228">A data view object has columns and rows.</span></span> <span data-ttu-id="15ab0-229">Każda kolumna ma nazwę i typ i długość.</span><span class="sxs-lookup"><span data-stu-id="15ab0-229">Each column has a name and a type and a length.</span></span> <span data-ttu-id="15ab0-230">Na przykład: kolumny wejściowe w podanej cenie domu mają **rozmiar** i **cenę**.</span><span class="sxs-lookup"><span data-stu-id="15ab0-230">For example: the input columns in the house price example are **Size** and **Price**.</span></span> <span data-ttu-id="15ab0-231">Są one zarówno typu, jak i są liczbami skalarnymi, a nie wektorami.</span><span class="sxs-lookup"><span data-stu-id="15ab0-231">They are both type  and they are scalar quantities rather than vector ones.</span></span>

   ![Przykład widoku danych ML.NET z danymi prognozowania cen domu](./media/ml-net-dataview.png)

<span data-ttu-id="15ab0-233">Wszystkie algorytmy ML.NET szukają kolumny wejściowej, która jest wektorem.</span><span class="sxs-lookup"><span data-stu-id="15ab0-233">All ML.NET algorithms look for an input column that is a vector.</span></span> <span data-ttu-id="15ab0-234">Domyślnie ta kolumna wektora jest nazywana **funkcjami**.</span><span class="sxs-lookup"><span data-stu-id="15ab0-234">By default this vector column is called **Features**.</span></span> <span data-ttu-id="15ab0-235">To dlatego, że połączymy kolumnę **size** z nową kolumną o nazwie **Features** w naszym przykładzie cen domu.</span><span class="sxs-lookup"><span data-stu-id="15ab0-235">This is why we concatenated the **Size** column into a new column called **Features** in our house price example.</span></span>

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

<span data-ttu-id="15ab0-236">Wszystkie algorytmy również tworzą nowe kolumny po przeprowadzeniu przewidywania.</span><span class="sxs-lookup"><span data-stu-id="15ab0-236">All algorithms also create new columns after they have performed a prediction.</span></span> <span data-ttu-id="15ab0-237">Stałe nazwy tych nowych kolumn zależą od typu algorytmu uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="15ab0-237">The fixed names of these new columns depend on the type of machine learning algorithm.</span></span> <span data-ttu-id="15ab0-238">W przypadku zadania regresji jedna z nowych kolumn jest nazywana **wynikiem**.</span><span class="sxs-lookup"><span data-stu-id="15ab0-238">For the regression task, one of the new columns is called **Score**.</span></span> <span data-ttu-id="15ab0-239">To dlatego, że nasze dane cen są przypisane do tej nazwy.</span><span class="sxs-lookup"><span data-stu-id="15ab0-239">This is why we attributed our price data with this name.</span></span>

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```    

<span data-ttu-id="15ab0-240">Więcej informacji na temat kolumn wyjściowych różnych zadań uczenia maszynowego można znaleźć w przewodniku [zadania Machine Learning](resources/tasks.md) .</span><span class="sxs-lookup"><span data-stu-id="15ab0-240">You can find out more about output columns of different machine learning tasks in the [Machine Learning Tasks](resources/tasks.md) guide.</span></span>

<span data-ttu-id="15ab0-241">Ważną właściwością obiektów DataView jest to, że są one oceniane **opóźnieniem**.</span><span class="sxs-lookup"><span data-stu-id="15ab0-241">An important property of DataView objects is that they are evaluated **lazily**.</span></span> <span data-ttu-id="15ab0-242">Widoki danych są ładowane i obsługiwane tylko podczas szkoleń i oceny modelu oraz do przewidywania danych.</span><span class="sxs-lookup"><span data-stu-id="15ab0-242">Data views are only loaded and operated on during model training and evaluation, and data prediction.</span></span> <span data-ttu-id="15ab0-243">Podczas pisania i testowania aplikacji ML.NET można użyć debugera programu Visual Studio, aby uzyskać wgląd w dowolny obiekt widoku danych przez wywołanie metody [podglądu](xref:Microsoft.ML.DebuggerExtensions.Preview*) .</span><span class="sxs-lookup"><span data-stu-id="15ab0-243">While you are writing and testing your ML.NET application, you can use the Visual Studio debugger to take a peek at any data view object by calling the [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview*) method.</span></span>

```csharp
    var debug = testPriceDataView.Preview();
```

<span data-ttu-id="15ab0-244">Możesz obejrzeć `debug` zmienną w debugerze i przeanalizować jej zawartość.</span><span class="sxs-lookup"><span data-stu-id="15ab0-244">You can watch the `debug` variable in the debugger and examine its contents.</span></span> <span data-ttu-id="15ab0-245">Nie używaj metody Preview w kodzie produkcyjnym, ponieważ znacząco obniża ona wydajność.</span><span class="sxs-lookup"><span data-stu-id="15ab0-245">Do not use the Preview method in production code, as it significantly degrades performance.</span></span>

### <a name="model-deployment"></a><span data-ttu-id="15ab0-246">Wdrożenie modelu</span><span class="sxs-lookup"><span data-stu-id="15ab0-246">Model Deployment</span></span>

<span data-ttu-id="15ab0-247">W aplikacjach w czasie rzeczywistym model szkoleń i oceny kodu zostanie oddzielony od prognoz.</span><span class="sxs-lookup"><span data-stu-id="15ab0-247">In real-life applications, your model training and evaluation code will be separate from your prediction.</span></span> <span data-ttu-id="15ab0-248">W rzeczywistości te dwa działania są często wykonywane przez oddzielne zespoły.</span><span class="sxs-lookup"><span data-stu-id="15ab0-248">In fact, these two activities are often performed by separate teams.</span></span> <span data-ttu-id="15ab0-249">Zespół projektowy modelu może zapisać model do użycia w aplikacji predykcyjnej.</span><span class="sxs-lookup"><span data-stu-id="15ab0-249">Your model development team can save the model for use in the prediction application.</span></span>

```csharp   
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="where-to-now"></a><span data-ttu-id="15ab0-250">Gdzie teraz?</span><span class="sxs-lookup"><span data-stu-id="15ab0-250">Where to now?</span></span>

<span data-ttu-id="15ab0-251">Możesz dowiedzieć się, jak tworzyć aplikacje przy użyciu różnych zadań uczenia maszynowego z bardziej realistycznymi zestawami danych w [samouczkach](./tutorials/index.md).</span><span class="sxs-lookup"><span data-stu-id="15ab0-251">You can learn how to build applications using different machine learning tasks with more realistic data sets in the [tutorials](./tutorials/index.md).</span></span>

<span data-ttu-id="15ab0-252">Możesz też zapoznać się z bardziej szczegółowymi tematami w temacie [jak przewodniki](./how-to-guides/index.md).</span><span class="sxs-lookup"><span data-stu-id="15ab0-252">Or you can learn about specific topics in more depth in the [How To Guides](./how-to-guides/index.md).</span></span>

<span data-ttu-id="15ab0-253">A jeśli jesteś super Keen, możesz szczegółowe bezpośrednio do [dokumentacji dotyczącej interfejsu API](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="15ab0-253">And if you're super keen, you can dive straight into the [API Reference documentation](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet)!</span></span>
