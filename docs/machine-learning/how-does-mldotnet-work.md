---
title: Co to jest strukturze ML.NET i jak to działa?
description: Strukturze ML.NET daje możliwość dodawania usługi machine learning do aplikacji platformy .NET. Dzięki tej możliwości, istnieje możliwość automatycznego prognozy przy użyciu danych, które są dostępne dla aplikacji. W tym artykule opisano podstawy uczenia maszynowego w strukturze ML.NET.
ms.date: 04/10/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
author: natke
ms.openlocfilehash: 58e79cf0b017d65644f25250d05d252b5635c21e
ms.sourcegitcommit: 5e05f983e63d5bbd8c0b246d02c6e4f23d2fc1db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2019
ms.locfileid: "67152003"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a><span data-ttu-id="88bae-105">Co to jest strukturze ML.NET i jak to działa?</span><span class="sxs-lookup"><span data-stu-id="88bae-105">What is ML.NET and how does it work?</span></span>

<span data-ttu-id="88bae-106">Strukturze ML.NET daje możliwość dodawania usługi machine learning do aplikacji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="88bae-106">ML.NET gives you the ability to add machine learning to .NET applications.</span></span> <span data-ttu-id="88bae-107">Dzięki tej możliwości, istnieje możliwość automatycznego prognozy przy użyciu danych, które są dostępne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="88bae-107">With this capability, you can make automatic predictions using the data available to your application.</span></span> <span data-ttu-id="88bae-108">W tym artykule opisano podstawy uczenia maszynowego w strukturze ML.NET.</span><span class="sxs-lookup"><span data-stu-id="88bae-108">This article explains the basics of machine learning in ML.NET.</span></span> 

<span data-ttu-id="88bae-109">Typ prognoz, które można wprowadzić za pomocą platformy ML.NET należą:</span><span class="sxs-lookup"><span data-stu-id="88bae-109">Examples of the type of predictions that you can make with ML.NET include:</span></span>

|||
|-|-|
|<span data-ttu-id="88bae-110">Klasyfikacja/kategoryzacji</span><span class="sxs-lookup"><span data-stu-id="88bae-110">Classification/Categorization</span></span>|<span data-ttu-id="88bae-111">Automatycznie podzielić opinie na kategorie dodatnie i ujemne</span><span class="sxs-lookup"><span data-stu-id="88bae-111">Automatically divide customer feedback into positive and negative categories</span></span>|
|<span data-ttu-id="88bae-112">Regresja/Predict ciągłe wartości</span><span class="sxs-lookup"><span data-stu-id="88bae-112">Regression/Predict continuous values</span></span>|<span data-ttu-id="88bae-113">Przewidzieć cenę infrastrukturę, w oparciu o rozmiar i położenie</span><span class="sxs-lookup"><span data-stu-id="88bae-113">Predict the price of houses based on size and location</span></span>|
|<span data-ttu-id="88bae-114">Wykrywanie anomalii</span><span class="sxs-lookup"><span data-stu-id="88bae-114">Anomaly Detection</span></span>|<span data-ttu-id="88bae-115">Wykrywanie transakcji bankowych oszustwa</span><span class="sxs-lookup"><span data-stu-id="88bae-115">Detect fraudulent banking transactions</span></span> |
|<span data-ttu-id="88bae-116">Zalecenia</span><span class="sxs-lookup"><span data-stu-id="88bae-116">Recommendations</span></span>|<span data-ttu-id="88bae-117">Zaproponuj produktów, które online kupujący mogą chcieć to kupić, oparte na poprzednim zakupów</span><span class="sxs-lookup"><span data-stu-id="88bae-117">Suggest products that online shoppers may want to buy, based on their previous purchases</span></span>|

## <a name="hello-mlnet-world"></a><span data-ttu-id="88bae-118">Witaj, świecie strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="88bae-118">Hello ML.NET World</span></span>

<span data-ttu-id="88bae-119">W poniższym fragmencie kodu demonstruje najprostszej aplikacji strukturze ML.NET.</span><span class="sxs-lookup"><span data-stu-id="88bae-119">The code in the following snippet demonstrates the simplest ML.NET application.</span></span> <span data-ttu-id="88bae-120">Ten przykład tworzy model regresji liniowej do prognozowania cen DOM przy użyciu danych o wielkości i ceny domu.</span><span class="sxs-lookup"><span data-stu-id="88bae-120">This example constructs a linear regression model to predict house prices using house size and price data.</span></span> <span data-ttu-id="88bae-121">W aplikacjach rzeczywistych danych i modelu będzie znacznie bardziej złożone.</span><span class="sxs-lookup"><span data-stu-id="88bae-121">In your real-life applications, your data and model will be much more complex.</span></span>

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

## <a name="code-workflow"></a><span data-ttu-id="88bae-122">Kod przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="88bae-122">Code workflow</span></span>

<span data-ttu-id="88bae-123">Poniższy diagram przedstawia strukturę kodu aplikacji, jak również proces iteracyjny modelu programowania:</span><span class="sxs-lookup"><span data-stu-id="88bae-123">The following diagram represents the application code structure, as well as the iterative process of model development:</span></span>
- <span data-ttu-id="88bae-124">Zbieranie i załadować dane szkoleniowe **IDataView** obiektu</span><span class="sxs-lookup"><span data-stu-id="88bae-124">Collect and load training data into an **IDataView** object</span></span>
- <span data-ttu-id="88bae-125">Określ potoku operacji wyodrębnianie funkcji i stosowanie algorytmu uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="88bae-125">Specify a pipeline of operations to extract features and apply a machine learning algorithm</span></span>
- <span data-ttu-id="88bae-126">Uczenie modelu przez wywołanie metody **Fit()** do potoku</span><span class="sxs-lookup"><span data-stu-id="88bae-126">Train a model by calling **Fit()** on the pipeline</span></span>
- <span data-ttu-id="88bae-127">Ocena modelu i modyfikować w celu</span><span class="sxs-lookup"><span data-stu-id="88bae-127">Evaluate the model and iterate to improve</span></span>
- <span data-ttu-id="88bae-128">Zapisz model do formatu binarnego, do użycia w aplikacji</span><span class="sxs-lookup"><span data-stu-id="88bae-128">Save the model into binary format, for use in an application</span></span>
- <span data-ttu-id="88bae-129">Ładowanie modelu do **ITransformer** obiektu</span><span class="sxs-lookup"><span data-stu-id="88bae-129">Load the model back into an **ITransformer** object</span></span>
- <span data-ttu-id="88bae-130">Prognozowania, wywołując **CreatePredictionEngine.Predict()**</span><span class="sxs-lookup"><span data-stu-id="88bae-130">Make predictions by calling **CreatePredictionEngine.Predict()**</span></span>

![Przepływ rozwoju aplikacji strukturze ML.NET tym składników Generowanie danych, opracowywanie potoku, szkoleń modelowych, oceny modelu i użycia modelu](./media/mldotnet-annotated-workflow.png) 

<span data-ttu-id="88bae-132">Przyjrzyjmy się nieco bardziej szczegółowe informacje te pojęcia.</span><span class="sxs-lookup"><span data-stu-id="88bae-132">Let's dig a little deeper into those concepts.</span></span>

## <a name="machine-learning-model"></a><span data-ttu-id="88bae-133">Model uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="88bae-133">Machine learning model</span></span>

<span data-ttu-id="88bae-134">Na model w strukturze ML.NET jest obiektem, który zawiera przekształceń w celu wykonania na danych wejściowych na dostęp do przewidywanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="88bae-134">An ML.NET model is an object that contains transformations to perform on your input data to arrive at the predicted output.</span></span>

### <a name="basic"></a><span data-ttu-id="88bae-135">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="88bae-135">Basic</span></span>

<span data-ttu-id="88bae-136">To najbardziej podstawowy model jest dwuwymiarowy regresji liniowej, gdzie jeden ilość ciągłego jest proporcjonalna do innego, tak jak w powyższym przykładzie cena dom.</span><span class="sxs-lookup"><span data-stu-id="88bae-136">The most basic model is two-dimensional linear regression, where one continuous quantity is proportional to another, as in the house price example above.</span></span> 

![Liniowy modelu regresji przy użyciu parametrów odchylenie i wagę rekordu](./media/linear-regression-model.svg)

<span data-ttu-id="88bae-138">Model, który jest po prostu: $Price = b + rozmiar \* w$.</span><span class="sxs-lookup"><span data-stu-id="88bae-138">The model is simply: $Price = b + Size \* w$.</span></span> <span data-ttu-id="88bae-139">$ Parametry $b i $w$ są szacowane przez dopasowanie wiersza w zestawie (rozmiar, cena) pary.</span><span class="sxs-lookup"><span data-stu-id="88bae-139">The parameters $b$ and $w$ are estimated by fitting a line on a set of (size, price) pairs.</span></span> <span data-ttu-id="88bae-140">Dane, używana do znajdowania parametrów modelu są nazywane **dane szkoleniowe**.</span><span class="sxs-lookup"><span data-stu-id="88bae-140">The data used to find the parameters of the model is called **training data**.</span></span> <span data-ttu-id="88bae-141">Dane wejściowe modelu uczenia maszynowego są nazywane **funkcji**.</span><span class="sxs-lookup"><span data-stu-id="88bae-141">The inputs of a machine learning model are called **features**.</span></span> <span data-ttu-id="88bae-142">W tym przykładzie $Size$ jest jedyną funkcją.</span><span class="sxs-lookup"><span data-stu-id="88bae-142">In this example, $Size$ is the only feature.</span></span> <span data-ttu-id="88bae-143">Wartości PRAWDA podstaw używane do trenowania modelu usługi machine learning są nazywane **etykiety**.</span><span class="sxs-lookup"><span data-stu-id="88bae-143">The ground-truth values used to train a machine learning model are called **labels**.</span></span> <span data-ttu-id="88bae-144">W tym miejscu $Price$ szkoleniowy zestaw danych mają etykiety.</span><span class="sxs-lookup"><span data-stu-id="88bae-144">Here, the $Price$ values in the training data set are the labels.</span></span>

### <a name="more-complex"></a><span data-ttu-id="88bae-145">Bardziej złożone</span><span class="sxs-lookup"><span data-stu-id="88bae-145">More complex</span></span>

<span data-ttu-id="88bae-146">Bardziej złożonych model klasyfikuje transakcji finansowych na kategorie za pomocą transakcji tekst opisu.</span><span class="sxs-lookup"><span data-stu-id="88bae-146">A more complex model classifies financial transactions into categories using the transaction text description.</span></span>

<span data-ttu-id="88bae-147">Opis każdej transakcji został podzielony na zestaw funkcji przez usunięcie nadmiarowych wyrazów i znaków, a wciąż dochodzą nowe kombinacje znaków i word.</span><span class="sxs-lookup"><span data-stu-id="88bae-147">Each transaction description is broken down into a set of features by removing redundant words and characters, and counting word and character combinations.</span></span> <span data-ttu-id="88bae-148">Zestaw funkcji jest używany do nauczenia modelu liniowego, na podstawie zestawu kategorii w danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="88bae-148">The feature set is used to train a linear model based on the set of categories in the training data.</span></span> <span data-ttu-id="88bae-149">Im więcej podobne nowy opis w zestaw szkoleniowy, tym większe prawdopodobieństwo zostanie do niej przypisany do tej samej kategorii.</span><span class="sxs-lookup"><span data-stu-id="88bae-149">The more similar a new description is to the ones in the training set, the more likely it will be assigned to the same category.</span></span> 

![Model klasyfikacji tekstu](./media/text-classification-model.svg)

<span data-ttu-id="88bae-151">Zarówno w modelu DOM ceny, jak i model klasyfikacji tekstu **liniowej** modeli.</span><span class="sxs-lookup"><span data-stu-id="88bae-151">Both the house price model and the text classification model are **linear** models.</span></span> <span data-ttu-id="88bae-152">W zależności od charakteru danych i są rozwiązywania problemów można również użyć **drzewa decyzyjnego** modeli, **uogólniony dodatku** modeli i inne.</span><span class="sxs-lookup"><span data-stu-id="88bae-152">Depending on the nature of your data and the problem you are solving, you can also use **decision tree** models, **generalized additive** models, and others.</span></span> <span data-ttu-id="88bae-153">Możesz dowiedzieć się więcej na temat modeli w [zadania](./resources/tasks.md).</span><span class="sxs-lookup"><span data-stu-id="88bae-153">You can find out more about the models in [Tasks](./resources/tasks.md).</span></span>

## <a name="data-preparation"></a><span data-ttu-id="88bae-154">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="88bae-154">Data preparation</span></span>

<span data-ttu-id="88bae-155">W większości przypadków dane dostępne nie są odpowiednie do użycia bezpośrednio do nauczenia modelu uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="88bae-155">In most cases, the data that you have available isn't suitable to be used directly to train a machine learning model.</span></span> <span data-ttu-id="88bae-156">Nieprzetworzone dane należy do przygotowania i wstępnie przetworzone przed można odnaleźć parametrów modelu.</span><span class="sxs-lookup"><span data-stu-id="88bae-156">The raw data needs to be prepared, or pre-processed before it can be used to find the parameters of your model.</span></span> <span data-ttu-id="88bae-157">Dane, może być konieczne przekonwertowana z wartościami ciągów w reprezentacji liczbowych.</span><span class="sxs-lookup"><span data-stu-id="88bae-157">Your data may need to be converted from string values to a numerical representation.</span></span> <span data-ttu-id="88bae-158">Możesz mieć nadmiarowe informacje w danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="88bae-158">You might have redundant information in your input data.</span></span> <span data-ttu-id="88bae-159">Może być konieczne zmniejszenie lub rozszerzeniu wymiary swoich danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="88bae-159">You may need to reduce or expand the dimensions of your input data.</span></span> <span data-ttu-id="88bae-160">Danych może być konieczne może być znormalizowane lub skalowania.</span><span class="sxs-lookup"><span data-stu-id="88bae-160">Your data might need to be normalized or scaled.</span></span>

<span data-ttu-id="88bae-161">[Samouczki strukturze ML.NET](./tutorials/index.md) nauczą Cię o potoki różnych przetwarzania danych dla tekstu, obrazów danych liczbowych i szeregów czasowych, używane do uczenia maszynowego określonych zadań.</span><span class="sxs-lookup"><span data-stu-id="88bae-161">The [ML.NET tutorials](./tutorials/index.md) teach you about different data processing pipelines for text, image, numerical, and time-series data used for specific machine learning tasks.</span></span>

<span data-ttu-id="88bae-162">[Jak przygotować dane](./how-to-guides/prepare-data-ml-net.md) dowiesz się, jak można zastosować przygotowywania danych bardziej ogólnie.</span><span class="sxs-lookup"><span data-stu-id="88bae-162">[How to prepare your data](./how-to-guides/prepare-data-ml-net.md) shows you how to applied data preparation more generally.</span></span>

<span data-ttu-id="88bae-163">Możesz znaleźć dodatku wszystkich [dostępnych transformacji](./resources/transforms.md) w sekcji zasobów.</span><span class="sxs-lookup"><span data-stu-id="88bae-163">You can find an appendix of all of the [available transformations](./resources/transforms.md) in the resources section.</span></span>

## <a name="model-evaluation"></a><span data-ttu-id="88bae-164">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="88bae-164">Model evaluation</span></span>

<span data-ttu-id="88bae-165">Gdy masz uczony model, skąd wiadomo, jak wprowadzić przewidywania przyszłych?</span><span class="sxs-lookup"><span data-stu-id="88bae-165">Once you have trained your model, how do you know how well it will make future predictions?</span></span> <span data-ttu-id="88bae-166">Za pomocą platformy ML.NET będziesz w stanie ocenić modelu w odniesieniu do niektórych nowych danych testowych.</span><span class="sxs-lookup"><span data-stu-id="88bae-166">With ML.NET, you can evaluate your model against some new test data.</span></span> 

<span data-ttu-id="88bae-167">Każdy typ machine learning zadania ma metryki używane do oceny dokładności i dokładności modelu przed testowego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="88bae-167">Each type of machine learning task has metrics used to evaluate the accuracy and precision of the model against the test data set.</span></span>

<span data-ttu-id="88bae-168">W naszym przykładzie cena DOM użyliśmy **regresji** zadania.</span><span class="sxs-lookup"><span data-stu-id="88bae-168">For our house price example, we used the **Regression** task.</span></span> <span data-ttu-id="88bae-169">Aby ocenić modelu, Dodaj następujący kod do oryginalnego przykładu.</span><span class="sxs-lookup"><span data-stu-id="88bae-169">To evaluate the model, add the following code to the original sample.</span></span>

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

<span data-ttu-id="88bae-170">Metryki oceny informujące o tym, że błąd jest low-ish i tej korelacji między przewidywane wyniki i dane wyjściowe testu jest wysoka.</span><span class="sxs-lookup"><span data-stu-id="88bae-170">The evaluation metrics tell you that the error is low-ish, and that correlation between the predicted output and the test output is high.</span></span> <span data-ttu-id="88bae-171">To było łatwe!</span><span class="sxs-lookup"><span data-stu-id="88bae-171">That was easy!</span></span> <span data-ttu-id="88bae-172">W przykładach rzeczywistych zajmuje więcej dostrajania do osiągnięcia dobry model metryk.</span><span class="sxs-lookup"><span data-stu-id="88bae-172">In real examples, it takes more tuning to achieve good model metrics.</span></span>

## <a name="mlnet-architecture"></a><span data-ttu-id="88bae-173">Architektura strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="88bae-173">ML.NET architecture</span></span>

<span data-ttu-id="88bae-174">W tej sekcji kursu wzorców architektury strukturze ML.NET.</span><span class="sxs-lookup"><span data-stu-id="88bae-174">In this section, we go through the architectural patterns of ML.NET.</span></span> <span data-ttu-id="88bae-175">Jeśli jesteś doświadczonym deweloperom platformy .NET, niektóre z tych wzorców jest znana użytkownikom, a niektóre są mniej znanych.</span><span class="sxs-lookup"><span data-stu-id="88bae-175">If you are an experienced .NET developer, some of these patterns will be familiar to you, and some will be less familiar.</span></span> <span data-ttu-id="88bae-176">Przytrzymując ścisłej, możemy zacząć korzystać!</span><span class="sxs-lookup"><span data-stu-id="88bae-176">Hold tight, while we dive in!</span></span>

<span data-ttu-id="88bae-177">Aplikację strukturze ML.NET rozpoczyna się od <xref:Microsoft.ML.MLContext> obiektu.</span><span class="sxs-lookup"><span data-stu-id="88bae-177">An ML.NET application starts with an <xref:Microsoft.ML.MLContext> object.</span></span> <span data-ttu-id="88bae-178">Ten obiekt pojedyncze zawiera **katalogi**.</span><span class="sxs-lookup"><span data-stu-id="88bae-178">This singleton object contains **catalogs**.</span></span> <span data-ttu-id="88bae-179">Wykaz jest fabryki danych, ładowania i zapisywania przekształceń, instruktorów i składników operacji modelu.</span><span class="sxs-lookup"><span data-stu-id="88bae-179">A catalog is a factory for data loading and saving, transforms, trainers, and model operation components.</span></span> <span data-ttu-id="88bae-180">Każdy obiekt wykazu zawiera metody służące do tworzenia różnych typów składników:</span><span class="sxs-lookup"><span data-stu-id="88bae-180">Each catalog object has methods to create the different types of components:</span></span>

||||
|-|-|-|
|<span data-ttu-id="88bae-181">Ładowanie danych i zapisywanie</span><span class="sxs-lookup"><span data-stu-id="88bae-181">Data loading and saving</span></span>||<xref:Microsoft.ML.DataOperationsCatalog>|
|<span data-ttu-id="88bae-182">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="88bae-182">Data preparation</span></span>||<xref:Microsoft.ML.TransformsCatalog>|
|<span data-ttu-id="88bae-183">Szkolenie algorytmów</span><span class="sxs-lookup"><span data-stu-id="88bae-183">Training algorithms</span></span>|<span data-ttu-id="88bae-184">Klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="88bae-184">Binary classification</span></span>|<xref:Microsoft.ML.BinaryClassificationCatalog>|
||<span data-ttu-id="88bae-185">Wieloklasowej klasyfikacji</span><span class="sxs-lookup"><span data-stu-id="88bae-185">Multiclass classification</span></span>|<xref:Microsoft.ML.MulticlassClassificationCatalog>|
||<span data-ttu-id="88bae-186">Wykrywanie anomalii</span><span class="sxs-lookup"><span data-stu-id="88bae-186">Anomaly detection</span></span>|<xref:Microsoft.ML.AnomalyDetectionCatalog>|
||<span data-ttu-id="88bae-187">Klasyfikacja</span><span class="sxs-lookup"><span data-stu-id="88bae-187">Ranking</span></span>|<xref:Microsoft.ML.RankingCatalog>|
||<span data-ttu-id="88bae-188">Regresji</span><span class="sxs-lookup"><span data-stu-id="88bae-188">Regression</span></span>|<xref:Microsoft.ML.RegressionCatalog>|
||<span data-ttu-id="88bae-189">Zalecenie</span><span class="sxs-lookup"><span data-stu-id="88bae-189">Recommendation</span></span>|<xref:Microsoft.ML.RecommendationCatalog>|
|<span data-ttu-id="88bae-190">Sposób użycia modelu</span><span class="sxs-lookup"><span data-stu-id="88bae-190">Model usage</span></span> ||<xref:Microsoft.ML.ModelOperationsCatalog>|

<span data-ttu-id="88bae-191">Możesz przejść do metod tworzenia w każdej z powyższych kategorii.</span><span class="sxs-lookup"><span data-stu-id="88bae-191">You can navigate to the creation methods in each of the above categories.</span></span> <span data-ttu-id="88bae-192">W programie Visual Studio wykazów są wyświetlane za pomocą funkcji IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="88bae-192">Using Visual Studio, the catalogs show up via IntelliSense.</span></span>

   ![Funkcja IntelliSense dla Instruktorzy regresji](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a><span data-ttu-id="88bae-194">Tworzenie potoku</span><span class="sxs-lookup"><span data-stu-id="88bae-194">Build the pipeline</span></span>

<span data-ttu-id="88bae-195">W każdym katalogu to zestaw metod rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="88bae-195">Inside each catalog is a set of extension methods.</span></span> <span data-ttu-id="88bae-196">Przyjrzyjmy się jak metody rozszerzenia są używane do tworzenia potoku szkolenia.</span><span class="sxs-lookup"><span data-stu-id="88bae-196">Let's look at how extension methods are used to create a training pipeline.</span></span>

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
```

<span data-ttu-id="88bae-197">Ten fragment kodu `Concatenate` i `Sdca` są obie metody w wykazie.</span><span class="sxs-lookup"><span data-stu-id="88bae-197">In the snippet, `Concatenate` and `Sdca` are both methods in the catalog.</span></span> <span data-ttu-id="88bae-198">Każdy tworzą [IEstimator](xref:Microsoft.ML.IEstimator%601) obiekt, który jest dołączany do potoku.</span><span class="sxs-lookup"><span data-stu-id="88bae-198">They each create an [IEstimator](xref:Microsoft.ML.IEstimator%601) object that is appended to the pipeline.</span></span>

<span data-ttu-id="88bae-199">W tym momencie obiekty są tworzone tylko.</span><span class="sxs-lookup"><span data-stu-id="88bae-199">At this point, the objects are created only.</span></span> <span data-ttu-id="88bae-200">Stało się nie wykonania.</span><span class="sxs-lookup"><span data-stu-id="88bae-200">No execution has happened.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="88bae-201">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="88bae-201">Train the model</span></span>

<span data-ttu-id="88bae-202">Po utworzeniu obiektów w potoku danych może służyć do nauczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="88bae-202">Once the objects in the pipeline have been created, data can be used to train the model.</span></span>

```csharp
    var model = pipeline.Fit(trainingData);
```

<span data-ttu-id="88bae-203">Wywoływanie `Fit()` korzysta z danych wejściowych szkolenia można oszacować parametrów modelu.</span><span class="sxs-lookup"><span data-stu-id="88bae-203">Calling `Fit()` uses the input training data to estimate the parameters of the model.</span></span> <span data-ttu-id="88bae-204">Jest to nazywane uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="88bae-204">This is known as training the model.</span></span> <span data-ttu-id="88bae-205">Należy pamiętać, że powyższego modelu regresji liniowej ma dwa parametry modelu: **odchylenie** i **wagi**.</span><span class="sxs-lookup"><span data-stu-id="88bae-205">Remember, the linear regression model above had two model parameters: **bias** and **weight**.</span></span> <span data-ttu-id="88bae-206">Po `Fit()` wywołanie, są znane wartości parametrów.</span><span class="sxs-lookup"><span data-stu-id="88bae-206">After the `Fit()` call, the values of the parameters are known.</span></span> <span data-ttu-id="88bae-207">Większość modeli mają dużo więcej parametrów niż to.</span><span class="sxs-lookup"><span data-stu-id="88bae-207">Most models will have many more parameters than this.</span></span>

<span data-ttu-id="88bae-208">Dowiedz się więcej na temat szkoleń modelowych w [jak uczenie modelu](./how-to-guides/train-machine-learning-model-ml-net.md)</span><span class="sxs-lookup"><span data-stu-id="88bae-208">You can learn more about model training in [How to train your model](./how-to-guides/train-machine-learning-model-ml-net.md)</span></span>

<span data-ttu-id="88bae-209">Wynikowy obiekt modelu implementuje <xref:Microsoft.ML.ITransformer> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="88bae-209">The resulting model object implements the <xref:Microsoft.ML.ITransformer> interface.</span></span> <span data-ttu-id="88bae-210">Oznacza to, że model przekształca dane wejściowe w prognozy.</span><span class="sxs-lookup"><span data-stu-id="88bae-210">That is, the model transforms input data into predictions.</span></span>

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a><span data-ttu-id="88bae-211">Użyj modelu</span><span class="sxs-lookup"><span data-stu-id="88bae-211">Use the model</span></span>

<span data-ttu-id="88bae-212">W danym momencie można przekształcić dane wejściowe do przewidywania luzem lub jedne dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="88bae-212">You can transform input data into predictions in bulk, or one input at a time.</span></span> <span data-ttu-id="88bae-213">W tym przykładzie cena DOM były wykonywane zarówno: w trybie zbiorczym na potrzeby oceny modelu i pojedynczo do nowych prognozowania.</span><span class="sxs-lookup"><span data-stu-id="88bae-213">In the house price example, we did both: in bulk for the purpose of evaluating the model, and one at a time to make a new prediction.</span></span> <span data-ttu-id="88bae-214">Przyjrzyjmy się wprowadzania pojedynczego prognozy.</span><span class="sxs-lookup"><span data-stu-id="88bae-214">Let's look at making single predictions.</span></span>

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = mlContext.CreatePredictionEngine<HouseData, Prediction>(model);
    var price = predEngine.Predict(size);
```
 
<span data-ttu-id="88bae-215">`CreatePredictionEngine()` Metoda przyjmuje wejściowe klasy a dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="88bae-215">The `CreatePredictionEngine()` method takes an input class and an output class.</span></span> <span data-ttu-id="88bae-216">Nazwy pól i/lub kod atrybuty określają nazwy kolumn danych, używane podczas uczenia modelu i przewidywania.</span><span class="sxs-lookup"><span data-stu-id="88bae-216">The field names and/or code attributes determine the names of the data columns used during model training and prediction.</span></span> <span data-ttu-id="88bae-217">Informacje o [jak pojedynczy przewiduje](./how-to-guides/single-predict-model-ml-net.md) w sekcji porad.</span><span class="sxs-lookup"><span data-stu-id="88bae-217">You can read about  [How to make a single prediction](./how-to-guides/single-predict-model-ml-net.md) in the How-to section.</span></span>

### <a name="data-models-and-schema"></a><span data-ttu-id="88bae-218">Modele danych i schematu</span><span class="sxs-lookup"><span data-stu-id="88bae-218">Data models and schema</span></span>

<span data-ttu-id="88bae-219">W samym sercu potoku uczenia maszynowego w strukturze ML.NET są [DataView](xref:Microsoft.ML.IDataView) obiektów.</span><span class="sxs-lookup"><span data-stu-id="88bae-219">At the core of an ML.NET machine learning pipeline are [DataView](xref:Microsoft.ML.IDataView) objects.</span></span>

<span data-ttu-id="88bae-220">Każde przekształcenie w potoku ma schemat danych wejściowych (danych nazw, typów i rozmiarów, które przekształcenia oczekuje na dane wejściowe); i schemat danych wyjściowych (nazwy danych, typy i rozmiary, których przekształcenie daje po przekształceniu).</span><span class="sxs-lookup"><span data-stu-id="88bae-220">Each transformation in the pipeline has an input schema (data names, types, and sizes that the transform expects to see on its input); and an output schema (data names, types, and sizes that the transform produces after the transformation).</span></span> 

<span data-ttu-id="88bae-221">Jeśli schemat danych wyjściowych z jednym przekształcenia w potoku nie jest zgodny schemat danych wejściowych dalej transformacji, strukturze ML.NET spowoduje zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="88bae-221">If the output schema from one transform in the pipeline doesn't match the input schema of the next transform, ML.NET will throw an exception.</span></span>

<span data-ttu-id="88bae-222">Obiekt widoku danych ma kolumn i wierszy.</span><span class="sxs-lookup"><span data-stu-id="88bae-222">A data view object has columns and rows.</span></span> <span data-ttu-id="88bae-223">Każda kolumna ma nazwę i typ i długość.</span><span class="sxs-lookup"><span data-stu-id="88bae-223">Each column has a name and a type and a length.</span></span> <span data-ttu-id="88bae-224">Na przykład: wejściowy kolumn w domu przykład ceny są **rozmiar** i **cena**.</span><span class="sxs-lookup"><span data-stu-id="88bae-224">For example: the input columns in the house price example are **Size** and **Price**.</span></span> <span data-ttu-id="88bae-225">Są zarówno typ i ich są skalarnymi, a nie te wektor.</span><span class="sxs-lookup"><span data-stu-id="88bae-225">They are both type  and they are scalar quantities rather than vector ones.</span></span>

   ![Przykładowy widok danych strukturze ML.NET z danymi przewidywań cena DOM](./media/ml-net-dataview.png)

<span data-ttu-id="88bae-227">Wszystkie algorytmy strukturze ML.NET poszukaj kolumny wejściowej, które jest wektorem.</span><span class="sxs-lookup"><span data-stu-id="88bae-227">All ML.NET algorithms look for an input column that is a vector.</span></span> <span data-ttu-id="88bae-228">Domyślnie ta kolumna wektora jest nazywany **funkcji**.</span><span class="sxs-lookup"><span data-stu-id="88bae-228">By default this vector column is called **Features**.</span></span> <span data-ttu-id="88bae-229">Dlatego firma Microsoft połączonych **rozmiar** kolumny w nową kolumnę o nazwie **funkcji** w naszym przykładzie cena domu.</span><span class="sxs-lookup"><span data-stu-id="88bae-229">This is why we concatenated the **Size** column into a new column called **Features** in our house price example.</span></span>

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

<span data-ttu-id="88bae-230">Wszystkie algorytmy także tworzenie nowych kolumn po wykonywanej prognozę.</span><span class="sxs-lookup"><span data-stu-id="88bae-230">All algorithms also create new columns after they have performed a prediction.</span></span> <span data-ttu-id="88bae-231">Stałe nazwy tych nowych kolumn zależą od rodzaju algorytmu uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="88bae-231">The fixed names of these new columns depend on the type of machine learning algorithm.</span></span> <span data-ttu-id="88bae-232">W zadaniu regresji, jeden z nowymi kolumnami nosi nazwę **wynik**.</span><span class="sxs-lookup"><span data-stu-id="88bae-232">For the regression task, one of the new columns is called **Score**.</span></span> <span data-ttu-id="88bae-233">Jest to, dlaczego firma Microsoft opartego na atrybutach danych ceny o tej nazwie.</span><span class="sxs-lookup"><span data-stu-id="88bae-233">This is why we attributed our price data with this name.</span></span>

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```    

<span data-ttu-id="88bae-234">Możesz dowiedzieć się więcej na temat kolumn wyjściowych uczenia maszynowego różnych zadań w [zadania uczenia maszynowego](resources/tasks.md) przewodnik.</span><span class="sxs-lookup"><span data-stu-id="88bae-234">You can find out more about output columns of different machine learning tasks in the [Machine Learning Tasks](resources/tasks.md) guide.</span></span>

<span data-ttu-id="88bae-235">Ważne właściwość DataView obiektów, są one oceniane **opóźnieniem**.</span><span class="sxs-lookup"><span data-stu-id="88bae-235">An important property of DataView objects is that they are evaluated **lazily**.</span></span> <span data-ttu-id="88bae-236">Widoki danych są ładowane i tylko zasilaniu podczas uczenia modelu i oceny i przewidywania danych.</span><span class="sxs-lookup"><span data-stu-id="88bae-236">Data views are only loaded and operated on during model training and evaluation, and data prediction.</span></span> <span data-ttu-id="88bae-237">Podczas pisania i testowania aplikacji strukturze ML.NET, można użyć debugera programu Visual Studio do etapów przy dowolnego obiektu widoku danych, wywołując [Podgląd](xref:Microsoft.ML.DebuggerExtensions.Preview*) metody.</span><span class="sxs-lookup"><span data-stu-id="88bae-237">While you are writing and testing your ML.NET application, you can use the Visual Studio debugger to take a peek at any data view object by calling the [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview*) method.</span></span>

```csharp
    var debug = testPriceDataView.Preview();
```

<span data-ttu-id="88bae-238">Możesz obejrzeć `debug` zmiennych debugera i sprawdź jego zawartość.</span><span class="sxs-lookup"><span data-stu-id="88bae-238">You can watch the `debug` variable in the debugger and examine its contents.</span></span> <span data-ttu-id="88bae-239">Nie używaj metody (wersja zapoznawcza) w kodzie produkcyjnym, ponieważ znacznie obniża wydajność.</span><span class="sxs-lookup"><span data-stu-id="88bae-239">Do not use the Preview method in production code, as it significantly degrades performance.</span></span>

### <a name="model-deployment"></a><span data-ttu-id="88bae-240">Wdrażanie modelu</span><span class="sxs-lookup"><span data-stu-id="88bae-240">Model Deployment</span></span>

<span data-ttu-id="88bae-241">W rzeczywistych aplikacjach kod uczenie i Ewaluacja modelu będzie nienależący do prognozowania.</span><span class="sxs-lookup"><span data-stu-id="88bae-241">In real-life applications, your model training and evaluation code will be separate from your prediction.</span></span> <span data-ttu-id="88bae-242">W rzeczywistości te dwa działania często są wykonywane przez oddzielne zespoły.</span><span class="sxs-lookup"><span data-stu-id="88bae-242">In fact, these two activities are often performed by separate teams.</span></span> <span data-ttu-id="88bae-243">Twój zespół deweloperów modelu można zapisać modelu do użycia w aplikacji prognozy.</span><span class="sxs-lookup"><span data-stu-id="88bae-243">Your model development team can save the model for use in the prediction application.</span></span>

```csharp   
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="where-to-now"></a><span data-ttu-id="88bae-244">Gdzie teraz?</span><span class="sxs-lookup"><span data-stu-id="88bae-244">Where to now?</span></span>

<span data-ttu-id="88bae-245">Możesz dowiedzieć się, jak tworzyć aplikacje przy użyciu zadania uczenia maszynowego różnych z bardziej realistycznymi zestawami danych w [samouczki](./tutorials/index.md).</span><span class="sxs-lookup"><span data-stu-id="88bae-245">You can learn how to build applications using different machine learning tasks with more realistic data sets in the [tutorials](./tutorials/index.md).</span></span>

<span data-ttu-id="88bae-246">Lub możesz dowiedzieć się o określonych tematów, które bardziej szczegółowo w sekcji [jak do prowadnic](./how-to-guides/index.md).</span><span class="sxs-lookup"><span data-stu-id="88bae-246">Or you can learn about specific topics in more depth in the [How To Guides](./how-to-guides/index.md).</span></span>

<span data-ttu-id="88bae-247">A jeśli masz bardzo atrakcyjne, możesz od razu bezpośrednio do [dokumentację referencyjną interfejsu API](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet)!</span><span class="sxs-lookup"><span data-stu-id="88bae-247">And if you're super keen, you can dive straight into the [API Reference documentation](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet)!</span></span>
