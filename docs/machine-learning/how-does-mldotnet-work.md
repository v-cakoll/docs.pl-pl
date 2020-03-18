---
title: Co to jest ML.NET i jak to działa?
description: ML.NET umożliwia dodawanie uczenia maszynowego do aplikacji .NET w scenariuszach online lub offline. Dzięki tej funkcji można tworzyć automatyczne prognozy przy użyciu danych dostępnych dla aplikacji bez konieczności łączenia się z siecią w celu korzystania z ML.NET. W tym artykule wyjaśniono podstawy uczenia maszynowego w ML.NET.
ms.date: 11/5/2019
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: 169250adf81992ad0025e78eb9c8f151107bcf40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185858"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a><span data-ttu-id="1f28f-105">Co to jest ML.NET i jak to działa?</span><span class="sxs-lookup"><span data-stu-id="1f28f-105">What is ML.NET and how does it work?</span></span>

<span data-ttu-id="1f28f-106">ML.NET umożliwia dodawanie uczenia maszynowego do aplikacji .NET w scenariuszach online lub offline.</span><span class="sxs-lookup"><span data-stu-id="1f28f-106">ML.NET gives you the ability to add machine learning to .NET applications, in either online or offline scenarios.</span></span> <span data-ttu-id="1f28f-107">Dzięki tej funkcji można tworzyć automatyczne prognozy przy użyciu danych dostępnych dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1f28f-107">With this capability, you can make automatic predictions using the data available to your application.</span></span> <span data-ttu-id="1f28f-108">Aplikacje uczenia maszynowego korzystać z wzorców w danych do prognozowania, a nie muszą być jawnie zaprogramowane.</span><span class="sxs-lookup"><span data-stu-id="1f28f-108">Machine learning applications make use of patterns in the data to make predictions rather than needing to be explicitly programmed.</span></span>

<span data-ttu-id="1f28f-109">Centralnym elementem ML.NET jest **model**uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="1f28f-109">Central to ML.NET is a machine learning **model**.</span></span> <span data-ttu-id="1f28f-110">Model określa kroki potrzebne do przekształcenia danych wejściowych w przewidywanie.</span><span class="sxs-lookup"><span data-stu-id="1f28f-110">The model specifies the steps needed to transform your input data into a prediction.</span></span> <span data-ttu-id="1f28f-111">Za pomocą ML.NET można nabyć model niestandardowy, określając algorytm lub zaimportować wstępnie przeszkolonych modeli TensorFlow i ONNX.</span><span class="sxs-lookup"><span data-stu-id="1f28f-111">With ML.NET, you can train a custom model by specifying an algorithm, or you can import pre-trained TensorFlow and ONNX models.</span></span>

<span data-ttu-id="1f28f-112">Gdy masz model, można dodać go do aplikacji, aby prognozy.</span><span class="sxs-lookup"><span data-stu-id="1f28f-112">Once you have a model, you can add it to your application to make the predictions.</span></span>

<span data-ttu-id="1f28f-113">ML.NET działa w systemach Windows, Linux i macOS przy użyciu programu .NET Core lub systemu Windows przy użyciu programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1f28f-113">ML.NET runs on Windows, Linux, and macOS using .NET Core, or Windows using .NET Framework.</span></span> <span data-ttu-id="1f28f-114">64 bit jest obsługiwany na wszystkich platformach.</span><span class="sxs-lookup"><span data-stu-id="1f28f-114">64 bit is supported on all platforms.</span></span> <span data-ttu-id="1f28f-115">32-bitowy jest obsługiwany w systemie Windows, z wyjątkiem funkcji związanych z TensorFlow, LightGBM i ONNX.</span><span class="sxs-lookup"><span data-stu-id="1f28f-115">32 bit is supported on Windows, except for TensorFlow, LightGBM, and ONNX-related functionality.</span></span>

<span data-ttu-id="1f28f-116">Przykłady typów prognoz, które można wykonać za pomocą ML.NET:</span><span class="sxs-lookup"><span data-stu-id="1f28f-116">Examples of the type of predictions that you can make with ML.NET:</span></span>

|||
|-|-|
|<span data-ttu-id="1f28f-117">Klasyfikacja/kategoryzacja</span><span class="sxs-lookup"><span data-stu-id="1f28f-117">Classification/Categorization</span></span>|<span data-ttu-id="1f28f-118">Automatyczne dzielenie opinii klientów na kategorie pozytywne i negatywne</span><span class="sxs-lookup"><span data-stu-id="1f28f-118">Automatically divide customer feedback into positive and negative categories</span></span>|
|<span data-ttu-id="1f28f-119">Regresja/Przewidywanie wartości ciągłych</span><span class="sxs-lookup"><span data-stu-id="1f28f-119">Regression/Predict continuous values</span></span>|<span data-ttu-id="1f28f-120">Przewidywanie cen domów na podstawie wielkości i lokalizacji</span><span class="sxs-lookup"><span data-stu-id="1f28f-120">Predict the price of houses based on size and location</span></span>|
|<span data-ttu-id="1f28f-121">Wykrywanie anomalii</span><span class="sxs-lookup"><span data-stu-id="1f28f-121">Anomaly Detection</span></span>|<span data-ttu-id="1f28f-122">Wykrywanie nieuczciwych transakcji bankowych</span><span class="sxs-lookup"><span data-stu-id="1f28f-122">Detect fraudulent banking transactions</span></span> |
|<span data-ttu-id="1f28f-123">Zalecenia</span><span class="sxs-lookup"><span data-stu-id="1f28f-123">Recommendations</span></span>|<span data-ttu-id="1f28f-124">Zaproponuj produkty, które kupujący online mogą chcieć kupić na podstawie wcześniejszych zakupów</span><span class="sxs-lookup"><span data-stu-id="1f28f-124">Suggest products that online shoppers may want to buy, based on their previous purchases</span></span>|
|<span data-ttu-id="1f28f-125">Dane szeregowe/sekwencyjne</span><span class="sxs-lookup"><span data-stu-id="1f28f-125">Time series/sequential data</span></span>|<span data-ttu-id="1f28f-126">Prognoza pogody/sprzedaży produktów</span><span class="sxs-lookup"><span data-stu-id="1f28f-126">Forecast the weather/product sales</span></span>|
|<span data-ttu-id="1f28f-127">Klasyfikacja obrazów</span><span class="sxs-lookup"><span data-stu-id="1f28f-127">Image classification</span></span>|<span data-ttu-id="1f28f-128">Kategoryzuj patologie na obrazach medycznych</span><span class="sxs-lookup"><span data-stu-id="1f28f-128">Categorize pathologies in medical images</span></span>|

## <a name="hello-mlnet-world"></a><span data-ttu-id="1f28f-129">Witaj ML.NET Świecie</span><span class="sxs-lookup"><span data-stu-id="1f28f-129">Hello ML.NET World</span></span>

<span data-ttu-id="1f28f-130">Kod w poniższym fragmencie kodu pokazuje najprostszą aplikację ML.NET.</span><span class="sxs-lookup"><span data-stu-id="1f28f-130">The code in the following snippet demonstrates the simplest ML.NET application.</span></span> <span data-ttu-id="1f28f-131">W tym przykładzie konstruuje model regresji liniowej do przewidywania cen domów przy użyciu danych rozmiaru domu i ceny.</span><span class="sxs-lookup"><span data-stu-id="1f28f-131">This example constructs a linear regression model to predict house prices using house size and price data.</span></span>

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

## <a name="code-workflow"></a><span data-ttu-id="1f28f-132">Przepływ pracy kodu</span><span class="sxs-lookup"><span data-stu-id="1f28f-132">Code workflow</span></span>

<span data-ttu-id="1f28f-133">Poniższy diagram przedstawia strukturę kodu aplikacji, a także iteracyjny proces tworzenia modelu:</span><span class="sxs-lookup"><span data-stu-id="1f28f-133">The following diagram represents the application code structure, as well as the iterative process of model development:</span></span>

- <span data-ttu-id="1f28f-134">Zbieranie i ładowanie danych szkoleniowych do obiektu **IDataView**</span><span class="sxs-lookup"><span data-stu-id="1f28f-134">Collect and load training data into an **IDataView** object</span></span>
- <span data-ttu-id="1f28f-135">Określ potok operacji w celu wyodrębnienia funkcji i zastosowania algorytmu uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="1f28f-135">Specify a pipeline of operations to extract features and apply a machine learning algorithm</span></span>
- <span data-ttu-id="1f28f-136">Trenuj model, wywołując **fit()** w potoku</span><span class="sxs-lookup"><span data-stu-id="1f28f-136">Train a model by calling **Fit()** on the pipeline</span></span>
- <span data-ttu-id="1f28f-137">Oceń model i iterate, aby poprawić</span><span class="sxs-lookup"><span data-stu-id="1f28f-137">Evaluate the model and iterate to improve</span></span>
- <span data-ttu-id="1f28f-138">Zapisz model w formacie binarnym, do użycia w aplikacji</span><span class="sxs-lookup"><span data-stu-id="1f28f-138">Save the model into binary format, for use in an application</span></span>
- <span data-ttu-id="1f28f-139">Załaduj model z powrotem do obiektu **ITransformer**</span><span class="sxs-lookup"><span data-stu-id="1f28f-139">Load the model back into an **ITransformer** object</span></span>
- <span data-ttu-id="1f28f-140">Dokonaj prognoz, wywołując **CreatePredictionEngine.Predict()**</span><span class="sxs-lookup"><span data-stu-id="1f28f-140">Make predictions by calling **CreatePredictionEngine.Predict()**</span></span>

![ML.NET przepływ rozwoju aplikacji, w tym składniki do generowania danych, opracowywania potoku, szkolenia modelu, oceny modelu i użycia modelu](./media/mldotnet-annotated-workflow.png)

<span data-ttu-id="1f28f-142">Zagłębijmy się nieco głębiej w te koncepcje.</span><span class="sxs-lookup"><span data-stu-id="1f28f-142">Let's dig a little deeper into those concepts.</span></span>

## <a name="machine-learning-model"></a><span data-ttu-id="1f28f-143">Model uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="1f28f-143">Machine learning model</span></span>

<span data-ttu-id="1f28f-144">Model ML.NET jest obiektem, który zawiera przekształcenia do wykonania na danych wejściowych, aby dotrzeć do przewidywanego danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="1f28f-144">An ML.NET model is an object that contains transformations to perform on your input data to arrive at the predicted output.</span></span>

### <a name="basic"></a><span data-ttu-id="1f28f-145">Podstawowa (Basic)</span><span class="sxs-lookup"><span data-stu-id="1f28f-145">Basic</span></span>

<span data-ttu-id="1f28f-146">Najbardziej podstawowym modelem jest dwuwymiarowa regresja liniowa, gdzie jedna ciągła ilość jest proporcjonalna do drugiej, jak w powyższym przykładzie ceny domu.</span><span class="sxs-lookup"><span data-stu-id="1f28f-146">The most basic model is two-dimensional linear regression, where one continuous quantity is proportional to another, as in the house price example above.</span></span>

![Model regresji liniowej z parametrami odchylenia i wagi](./media/linear-regression-model.svg)

<span data-ttu-id="1f28f-148">Model jest po prostu: $Price = b + Rozmiar \* w$.</span><span class="sxs-lookup"><span data-stu-id="1f28f-148">The model is simply: $Price = b + Size \* w$.</span></span> <span data-ttu-id="1f28f-149">Parametry $b$ i $w $ są szacowane przez zamontowanie linii na zestawie par (rozmiar, cena).</span><span class="sxs-lookup"><span data-stu-id="1f28f-149">The parameters $b$ and $w$ are estimated by fitting a line on a set of (size, price) pairs.</span></span> <span data-ttu-id="1f28f-150">Dane używane do znajdowania parametrów modelu są nazywane **danymi treningowymi.**</span><span class="sxs-lookup"><span data-stu-id="1f28f-150">The data used to find the parameters of the model is called **training data**.</span></span> <span data-ttu-id="1f28f-151">Dane wejściowe modelu uczenia maszynowego są nazywane **funkcjami**.</span><span class="sxs-lookup"><span data-stu-id="1f28f-151">The inputs of a machine learning model are called **features**.</span></span> <span data-ttu-id="1f28f-152">W tym przykładzie $Size$ jest jedyną funkcją.</span><span class="sxs-lookup"><span data-stu-id="1f28f-152">In this example, $Size$ is the only feature.</span></span> <span data-ttu-id="1f28f-153">Wartości prawdy gruntu używane do szkolenia modelu uczenia maszynowego są nazywane **etykietami.**</span><span class="sxs-lookup"><span data-stu-id="1f28f-153">The ground-truth values used to train a machine learning model are called **labels**.</span></span> <span data-ttu-id="1f28f-154">W tym miejscu wartości $Price$ w zestawie danych szkoleniowych są etykietami.</span><span class="sxs-lookup"><span data-stu-id="1f28f-154">Here, the $Price$ values in the training data set are the labels.</span></span>

### <a name="more-complex"></a><span data-ttu-id="1f28f-155">Bardziej złożone</span><span class="sxs-lookup"><span data-stu-id="1f28f-155">More complex</span></span>

<span data-ttu-id="1f28f-156">Bardziej złożony model klasyfikuje transakcje finansowe na kategorie przy użyciu opisu tekstu transakcji.</span><span class="sxs-lookup"><span data-stu-id="1f28f-156">A more complex model classifies financial transactions into categories using the transaction text description.</span></span>

<span data-ttu-id="1f28f-157">Każdy opis transakcji jest podzielony na zestaw funkcji przez usunięcie zbędnych wyrazów i znaków oraz zliczanie kombinacji wyrazów i znaków.</span><span class="sxs-lookup"><span data-stu-id="1f28f-157">Each transaction description is broken down into a set of features by removing redundant words and characters, and counting word and character combinations.</span></span> <span data-ttu-id="1f28f-158">Zestaw funkcji służy do uczenia modelu liniowego na podstawie zestawu kategorii w danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="1f28f-158">The feature set is used to train a linear model based on the set of categories in the training data.</span></span> <span data-ttu-id="1f28f-159">Im bardziej podobny jest nowy opis do opisu w zestawie szkoleniowym, tym bardziej prawdopodobne jest, że zostanie przypisany do tej samej kategorii.</span><span class="sxs-lookup"><span data-stu-id="1f28f-159">The more similar a new description is to the ones in the training set, the more likely it will be assigned to the same category.</span></span>

![Model klasyfikacji tekstu](./media/text-classification-model.svg)

<span data-ttu-id="1f28f-161">Zarówno model ceny domu, jak i model klasyfikacji tekstu są modelami **liniowymi.**</span><span class="sxs-lookup"><span data-stu-id="1f28f-161">Both the house price model and the text classification model are **linear** models.</span></span> <span data-ttu-id="1f28f-162">W zależności od charakteru danych i rozwiązywania problemu można również użyć modeli **drzewa decyzyjnego,** **uogólnionych** modeli dodatków i innych.</span><span class="sxs-lookup"><span data-stu-id="1f28f-162">Depending on the nature of your data and the problem you are solving, you can also use **decision tree** models, **generalized additive** models, and others.</span></span> <span data-ttu-id="1f28f-163">Więcej informacji na temat modeli można znaleźć w [obszarze Zadania](./resources/tasks.md).</span><span class="sxs-lookup"><span data-stu-id="1f28f-163">You can find out more about the models in [Tasks](./resources/tasks.md).</span></span>

## <a name="data-preparation"></a><span data-ttu-id="1f28f-164">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="1f28f-164">Data preparation</span></span>

<span data-ttu-id="1f28f-165">W większości przypadków dostępne dane nie są odpowiednie do bezpośredniego uczenia modelu uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="1f28f-165">In most cases, the data that you have available isn't suitable to be used directly to train a machine learning model.</span></span> <span data-ttu-id="1f28f-166">Nieprzetworzone dane muszą być przygotowane lub wstępnie przetworzone, zanim będzie można go użyć do znalezienia parametrów modelu.</span><span class="sxs-lookup"><span data-stu-id="1f28f-166">The raw data needs to be prepared, or pre-processed, before it can be used to find the parameters of your model.</span></span> <span data-ttu-id="1f28f-167">Dane mogą wymagać konwersji z wartości ciągu do reprezentacji liczbowej.</span><span class="sxs-lookup"><span data-stu-id="1f28f-167">Your data may need to be converted from string values to a numerical representation.</span></span> <span data-ttu-id="1f28f-168">Być może w danych wejściowych mogą być dostępne nadmiarowe informacje.</span><span class="sxs-lookup"><span data-stu-id="1f28f-168">You might have redundant information in your input data.</span></span> <span data-ttu-id="1f28f-169">Może być konieczne zmniejszenie lub rozszerzenie wymiarów danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="1f28f-169">You may need to reduce or expand the dimensions of your input data.</span></span> <span data-ttu-id="1f28f-170">Dane mogą wymagać znormalizowania lub skalowania.</span><span class="sxs-lookup"><span data-stu-id="1f28f-170">Your data might need to be normalized or scaled.</span></span>

<span data-ttu-id="1f28f-171">[Samouczki ML.NET](./tutorials/index.md) uczą o różnych potokach przetwarzania danych dla tekstu, obrazu, numerycznych i szeregów czasowych danych używanych do określonych zadań uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="1f28f-171">The [ML.NET tutorials](./tutorials/index.md) teach you about different data processing pipelines for text, image, numerical, and time-series data used for specific machine learning tasks.</span></span>

<span data-ttu-id="1f28f-172">[Jak przygotować dane](./how-to-guides/prepare-data-ml-net.md) pokazuje, jak zastosować przygotowanie danych bardziej ogólnie.</span><span class="sxs-lookup"><span data-stu-id="1f28f-172">[How to prepare your data](./how-to-guides/prepare-data-ml-net.md) shows you how to apply data preparation more generally.</span></span>

<span data-ttu-id="1f28f-173">W sekcji zasobów można znaleźć dodatek wszystkich [dostępnych przekształceń.](./resources/transforms.md)</span><span class="sxs-lookup"><span data-stu-id="1f28f-173">You can find an appendix of all of the [available transformations](./resources/transforms.md) in the resources section.</span></span>

## <a name="model-evaluation"></a><span data-ttu-id="1f28f-174">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="1f28f-174">Model evaluation</span></span>

<span data-ttu-id="1f28f-175">Po przeszkoleniu modelu, skąd wiesz, jak dobrze będzie to w przyszłości prognozy?</span><span class="sxs-lookup"><span data-stu-id="1f28f-175">Once you have trained your model, how do you know how well it will make future predictions?</span></span> <span data-ttu-id="1f28f-176">Za pomocą ML.NET można ocenić model na niektóre nowe dane testowe.</span><span class="sxs-lookup"><span data-stu-id="1f28f-176">With ML.NET, you can evaluate your model against some new test data.</span></span>

<span data-ttu-id="1f28f-177">Każdy typ zadania uczenia maszynowego ma metryki używane do oceny dokładności i dokładności modelu w stosunku do zestawu danych testowych.</span><span class="sxs-lookup"><span data-stu-id="1f28f-177">Each type of machine learning task has metrics used to evaluate the accuracy and precision of the model against the test data set.</span></span>

<span data-ttu-id="1f28f-178">W naszym przykładzie ceny domu użyliśmy zadania **Regresja.**</span><span class="sxs-lookup"><span data-stu-id="1f28f-178">For our house price example, we used the **Regression** task.</span></span> <span data-ttu-id="1f28f-179">Aby ocenić model, dodaj następujący kod do oryginalnego przykładu.</span><span class="sxs-lookup"><span data-stu-id="1f28f-179">To evaluate the model, add the following code to the original sample.</span></span>

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

<span data-ttu-id="1f28f-180">Metryki oceny powiedzieć, że błąd jest low-owski i że korelacja między przewidywane dane wyjściowe i dane wyjściowe testu jest wysoka.</span><span class="sxs-lookup"><span data-stu-id="1f28f-180">The evaluation metrics tell you that the error is low-ish, and that correlation between the predicted output and the test output is high.</span></span> <span data-ttu-id="1f28f-181">To było łatwe!</span><span class="sxs-lookup"><span data-stu-id="1f28f-181">That was easy!</span></span> <span data-ttu-id="1f28f-182">W rzeczywistych przykładach trwa więcej strojenia, aby osiągnąć dobre metryki modelu.</span><span class="sxs-lookup"><span data-stu-id="1f28f-182">In real examples, it takes more tuning to achieve good model metrics.</span></span>

## <a name="mlnet-architecture"></a><span data-ttu-id="1f28f-183">architektura ML.NET</span><span class="sxs-lookup"><span data-stu-id="1f28f-183">ML.NET architecture</span></span>

<span data-ttu-id="1f28f-184">W tej sekcji przechodzimy przez wzorce architektoniczne ML.NET.</span><span class="sxs-lookup"><span data-stu-id="1f28f-184">In this section, we go through the architectural patterns of ML.NET.</span></span> <span data-ttu-id="1f28f-185">Jeśli jesteś doświadczonym deweloperem .NET, niektóre z tych wzorców będą znane, a niektóre będą mniej znane.</span><span class="sxs-lookup"><span data-stu-id="1f28f-185">If you are an experienced .NET developer, some of these patterns will be familiar to you, and some will be less familiar.</span></span> <span data-ttu-id="1f28f-186">Trzymaj się mocno, podczas gdy my nurkujemy!</span><span class="sxs-lookup"><span data-stu-id="1f28f-186">Hold tight, while we dive in!</span></span>

<span data-ttu-id="1f28f-187">Aplikacja ML.NET rozpoczyna <xref:Microsoft.ML.MLContext> się od obiektu.</span><span class="sxs-lookup"><span data-stu-id="1f28f-187">An ML.NET application starts with an <xref:Microsoft.ML.MLContext> object.</span></span> <span data-ttu-id="1f28f-188">Ten pojedynczy obiekt zawiera **katalogi**.</span><span class="sxs-lookup"><span data-stu-id="1f28f-188">This singleton object contains **catalogs**.</span></span> <span data-ttu-id="1f28f-189">Katalog jest fabryką do ładowania i zapisywania danych, przekształca, trenerów i składników operacji modelu.</span><span class="sxs-lookup"><span data-stu-id="1f28f-189">A catalog is a factory for data loading and saving, transforms, trainers, and model operation components.</span></span> <span data-ttu-id="1f28f-190">Każdy obiekt katalogu ma metody tworzenia różnych typów składników:</span><span class="sxs-lookup"><span data-stu-id="1f28f-190">Each catalog object has methods to create the different types of components:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="1f28f-191">Ładowanie i zapisywanie danych</span><span class="sxs-lookup"><span data-stu-id="1f28f-191">Data loading and saving</span></span>||<xref:Microsoft.ML.DataOperationsCatalog>||
|<span data-ttu-id="1f28f-192">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="1f28f-192">Data preparation</span></span>||<xref:Microsoft.ML.TransformsCatalog>||
|<span data-ttu-id="1f28f-193">Algorytmy szkoleniowe</span><span class="sxs-lookup"><span data-stu-id="1f28f-193">Training algorithms</span></span>|<span data-ttu-id="1f28f-194">Klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="1f28f-194">Binary classification</span></span>|<xref:Microsoft.ML.BinaryClassificationCatalog>||
||<span data-ttu-id="1f28f-195">Klasyfikacja wieloklasowa</span><span class="sxs-lookup"><span data-stu-id="1f28f-195">Multiclass classification</span></span>|<xref:Microsoft.ML.MulticlassClassificationCatalog>||
||<span data-ttu-id="1f28f-196">Wykrywanie anomalii</span><span class="sxs-lookup"><span data-stu-id="1f28f-196">Anomaly detection</span></span>|<xref:Microsoft.ML.AnomalyDetectionCatalog>||
||<span data-ttu-id="1f28f-197">Klastrowanie</span><span class="sxs-lookup"><span data-stu-id="1f28f-197">Clustering</span></span>|<xref:Microsoft.ML.ClusteringCatalog>||
||<span data-ttu-id="1f28f-198">Prognozowanie</span><span class="sxs-lookup"><span data-stu-id="1f28f-198">Forecasting</span></span>|<xref:Microsoft.ML.ForecastingCatalog>||
||<span data-ttu-id="1f28f-199">Ranking</span><span class="sxs-lookup"><span data-stu-id="1f28f-199">Ranking</span></span>|<xref:Microsoft.ML.RankingCatalog>||
||<span data-ttu-id="1f28f-200">Regresja</span><span class="sxs-lookup"><span data-stu-id="1f28f-200">Regression</span></span>|<xref:Microsoft.ML.RegressionCatalog>||
||<span data-ttu-id="1f28f-201">Zalecenie</span><span class="sxs-lookup"><span data-stu-id="1f28f-201">Recommendation</span></span>|<xref:Microsoft.ML.RecommendationCatalog>|<span data-ttu-id="1f28f-202">dodawanie `Microsoft.ML.Recommender` pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="1f28f-202">add the `Microsoft.ML.Recommender` NuGet package</span></span>|
||<span data-ttu-id="1f28f-203">Seria czasu</span><span class="sxs-lookup"><span data-stu-id="1f28f-203">TimeSeries</span></span>|<xref:Microsoft.ML.TimeSeriesCatalog>|<span data-ttu-id="1f28f-204">dodawanie `Microsoft.ML.TimeSeries` pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="1f28f-204">add the `Microsoft.ML.TimeSeries` NuGet package</span></span>|
|<span data-ttu-id="1f28f-205">Użycie modelu</span><span class="sxs-lookup"><span data-stu-id="1f28f-205">Model usage</span></span> ||<xref:Microsoft.ML.ModelOperationsCatalog>||

<span data-ttu-id="1f28f-206">Można przejść do metod tworzenia w każdej z powyższych kategorii.</span><span class="sxs-lookup"><span data-stu-id="1f28f-206">You can navigate to the creation methods in each of the above categories.</span></span> <span data-ttu-id="1f28f-207">Za pomocą programu Visual Studio katalogi są wyświetlane za pośrednictwem programu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="1f28f-207">Using Visual Studio, the catalogs show up via IntelliSense.</span></span>

   ![Intellisense dla trenerów regresji](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a><span data-ttu-id="1f28f-209">Tworzenie potoku</span><span class="sxs-lookup"><span data-stu-id="1f28f-209">Build the pipeline</span></span>

<span data-ttu-id="1f28f-210">Wewnątrz każdego katalogu jest zestaw metod rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="1f28f-210">Inside each catalog is a set of extension methods.</span></span> <span data-ttu-id="1f28f-211">Przyjrzyjmy się, jak metody rozszerzenia są używane do tworzenia potoku szkolenia.</span><span class="sxs-lookup"><span data-stu-id="1f28f-211">Let's look at how extension methods are used to create a training pipeline.</span></span>

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
```

<span data-ttu-id="1f28f-212">We fragmencie `Concatenate` `Sdca` kodu i obie metody w katalogu.</span><span class="sxs-lookup"><span data-stu-id="1f28f-212">In the snippet, `Concatenate` and `Sdca` are both methods in the catalog.</span></span> <span data-ttu-id="1f28f-213">Każdy z nich tworzy obiekt [IEstimator,](xref:Microsoft.ML.IEstimator%601) który jest dołączany do potoku.</span><span class="sxs-lookup"><span data-stu-id="1f28f-213">They each create an [IEstimator](xref:Microsoft.ML.IEstimator%601) object that is appended to the pipeline.</span></span>

<span data-ttu-id="1f28f-214">W tym momencie obiekty są tworzone tylko.</span><span class="sxs-lookup"><span data-stu-id="1f28f-214">At this point, the objects are created only.</span></span> <span data-ttu-id="1f28f-215">Nie doszło do wykonania.</span><span class="sxs-lookup"><span data-stu-id="1f28f-215">No execution has happened.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="1f28f-216">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="1f28f-216">Train the model</span></span>

<span data-ttu-id="1f28f-217">Po utworzeniu obiektów w potoku dane mogą służyć do nauczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="1f28f-217">Once the objects in the pipeline have been created, data can be used to train the model.</span></span>

```csharp
    var model = pipeline.Fit(trainingData);
```

<span data-ttu-id="1f28f-218">Wywołanie `Fit()` używa danych wejściowych szkolenia do oszacowania parametrów modelu.</span><span class="sxs-lookup"><span data-stu-id="1f28f-218">Calling `Fit()` uses the input training data to estimate the parameters of the model.</span></span> <span data-ttu-id="1f28f-219">Jest to nazywane szkoleniem modelu.</span><span class="sxs-lookup"><span data-stu-id="1f28f-219">This is known as training the model.</span></span> <span data-ttu-id="1f28f-220">Należy pamiętać, że powyższy model regresji liniowej miał dwa parametry modelu: **stronniczość** i **wagę.**</span><span class="sxs-lookup"><span data-stu-id="1f28f-220">Remember, the linear regression model above had two model parameters: **bias** and **weight**.</span></span> <span data-ttu-id="1f28f-221">Po `Fit()` wywołaniu wartości parametrów są znane.</span><span class="sxs-lookup"><span data-stu-id="1f28f-221">After the `Fit()` call, the values of the parameters are known.</span></span> <span data-ttu-id="1f28f-222">Większość modeli będzie miała o wiele więcej parametrów niż ten.</span><span class="sxs-lookup"><span data-stu-id="1f28f-222">Most models will have many more parameters than this.</span></span>

<span data-ttu-id="1f28f-223">Możesz dowiedzieć się więcej o szkoleniu modelu w [Jak trenować swój model](./how-to-guides/train-machine-learning-model-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="1f28f-223">You can learn more about model training in [How to train your model](./how-to-guides/train-machine-learning-model-ml-net.md).</span></span>

<span data-ttu-id="1f28f-224">Wynikowy obiekt modelu implementuje <xref:Microsoft.ML.ITransformer> interfejs.</span><span class="sxs-lookup"><span data-stu-id="1f28f-224">The resulting model object implements the <xref:Microsoft.ML.ITransformer> interface.</span></span> <span data-ttu-id="1f28f-225">Oznacza to, że model przekształca dane wejściowe w prognozy.</span><span class="sxs-lookup"><span data-stu-id="1f28f-225">That is, the model transforms input data into predictions.</span></span>

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a><span data-ttu-id="1f28f-226">Korzystanie z modelu</span><span class="sxs-lookup"><span data-stu-id="1f28f-226">Use the model</span></span>

<span data-ttu-id="1f28f-227">Dane wejściowe można przekształcać w prognozy zbiorczo lub jedno dane wejściowe naraz.</span><span class="sxs-lookup"><span data-stu-id="1f28f-227">You can transform input data into predictions in bulk, or one input at a time.</span></span> <span data-ttu-id="1f28f-228">W przykładzie ceny domu zrobiliśmy oba: zbiorczo w celu oceny modelu, a po jednym na raz, aby dokonać nowej prognozy.</span><span class="sxs-lookup"><span data-stu-id="1f28f-228">In the house price example, we did both: in bulk for the purpose of evaluating the model, and one at a time to make a new prediction.</span></span> <span data-ttu-id="1f28f-229">Przyjrzyjmy się tworzeniu pojedynczych prognoz.</span><span class="sxs-lookup"><span data-stu-id="1f28f-229">Let's look at making single predictions.</span></span>

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = mlContext.CreatePredictionEngine<HouseData, Prediction>(model);
    var price = predEngine.Predict(size);
```

<span data-ttu-id="1f28f-230">Metoda `CreatePredictionEngine()` przyjmuje klasy wejściowej i klasy wyjściowej.</span><span class="sxs-lookup"><span data-stu-id="1f28f-230">The `CreatePredictionEngine()` method takes an input class and an output class.</span></span> <span data-ttu-id="1f28f-231">Nazwy pól i/lub atrybuty kodu określają nazwy kolumn danych używanych podczas szkolenia i przewidywania modelu.</span><span class="sxs-lookup"><span data-stu-id="1f28f-231">The field names and/or code attributes determine the names of the data columns used during model training and prediction.</span></span> <span data-ttu-id="1f28f-232">Możesz przeczytać o [Jak zrobić pojedyncze przewidywanie](./how-to-guides/single-predict-model-ml-net.md) w sekcji Instrukcje.</span><span class="sxs-lookup"><span data-stu-id="1f28f-232">You can read about  [How to make a single prediction](./how-to-guides/single-predict-model-ml-net.md) in the How-to section.</span></span>

### <a name="data-models-and-schema"></a><span data-ttu-id="1f28f-233">Modele danych i schemat</span><span class="sxs-lookup"><span data-stu-id="1f28f-233">Data models and schema</span></span>

<span data-ttu-id="1f28f-234">W centrum ML.NET potoku uczenia maszynowego są [DataView](xref:Microsoft.ML.IDataView) obiektów.</span><span class="sxs-lookup"><span data-stu-id="1f28f-234">At the core of an ML.NET machine learning pipeline are [DataView](xref:Microsoft.ML.IDataView) objects.</span></span>

<span data-ttu-id="1f28f-235">Każda transformacja w potoku ma schemat wejściowy (nazwy danych, typy i rozmiary, które transformacja oczekuje, aby zobaczyć na jego danych wejściowych); i schemat wyjściowy (nazwy danych, typy i rozmiary, które transformacja tworzy po transformacji).</span><span class="sxs-lookup"><span data-stu-id="1f28f-235">Each transformation in the pipeline has an input schema (data names, types, and sizes that the transform expects to see on its input); and an output schema (data names, types, and sizes that the transform produces after the transformation).</span></span> <span data-ttu-id="1f28f-236">Poniższy dokument zawiera szczegółowe wyjaśnienie [interfejsu IDataView i jego systemu typów](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html).</span><span class="sxs-lookup"><span data-stu-id="1f28f-236">The following document provides an in-depth explanation of the [IDataView interface and its type system](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html).</span></span>

<span data-ttu-id="1f28f-237">Jeśli schemat wyjściowy z jednej transformacji w potoku nie pasuje do schematu wejściowego następnego przekształcenia, ML.NET zwyżenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="1f28f-237">If the output schema from one transform in the pipeline doesn't match the input schema of the next transform, ML.NET will throw an exception.</span></span>

<span data-ttu-id="1f28f-238">Obiekt widoku danych ma kolumny i wiersze.</span><span class="sxs-lookup"><span data-stu-id="1f28f-238">A data view object has columns and rows.</span></span> <span data-ttu-id="1f28f-239">Każda kolumna ma nazwę, typ i długość.</span><span class="sxs-lookup"><span data-stu-id="1f28f-239">Each column has a name and a type and a length.</span></span> <span data-ttu-id="1f28f-240">Na przykład kolumny wejściowe w przykładzie ceny domu to **Rozmiar** i **Cena**.</span><span class="sxs-lookup"><span data-stu-id="1f28f-240">For example, the input columns in the house price example are **Size** and **Price**.</span></span> <span data-ttu-id="1f28f-241">Są one zarówno typu i są ilości skalarne, a nie te wektorowe.</span><span class="sxs-lookup"><span data-stu-id="1f28f-241">They are both type and they are scalar quantities rather than vector ones.</span></span>

   ![przykład ML.NET widoku danych z danymi dotyczącymi prognozowania cen nieruchomości](./media/ml-net-dataview.png)

<span data-ttu-id="1f28f-243">Wszystkie ML.NET algorytmy poszukują kolumny wejściowej, która jest wektorem.</span><span class="sxs-lookup"><span data-stu-id="1f28f-243">All ML.NET algorithms look for an input column that is a vector.</span></span> <span data-ttu-id="1f28f-244">Domyślnie ta kolumna wektorowa nosi nazwę **Funkcje**.</span><span class="sxs-lookup"><span data-stu-id="1f28f-244">By default this vector column is called **Features**.</span></span> <span data-ttu-id="1f28f-245">Dlatego połączyliśmy kolumnę **Size** w nową kolumnę o nazwie **Funkcje** w naszym przykładzie ceny domu.</span><span class="sxs-lookup"><span data-stu-id="1f28f-245">This is why we concatenated the **Size** column into a new column called **Features** in our house price example.</span></span>

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

<span data-ttu-id="1f28f-246">Wszystkie algorytmy również utworzyć nowe kolumny po wykonaniu prognozowania.</span><span class="sxs-lookup"><span data-stu-id="1f28f-246">All algorithms also create new columns after they have performed a prediction.</span></span> <span data-ttu-id="1f28f-247">Stałe nazwy tych nowych kolumn zależą od typu algorytmu uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="1f28f-247">The fixed names of these new columns depend on the type of machine learning algorithm.</span></span> <span data-ttu-id="1f28f-248">W przypadku zadania regresji jedna z nowych kolumn nosi nazwę **Score**.</span><span class="sxs-lookup"><span data-stu-id="1f28f-248">For the regression task, one of the new columns is called **Score**.</span></span> <span data-ttu-id="1f28f-249">Dlatego przypisaliśmy nasze dane cenowe o tej nazwie.</span><span class="sxs-lookup"><span data-stu-id="1f28f-249">This is why we attributed our price data with this name.</span></span>

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```

<span data-ttu-id="1f28f-250">Więcej informacji na temat kolumn wyjściowych różnych zadań uczenia maszynowego można znaleźć w przewodniku [zadania uczenia maszynowego.](resources/tasks.md)</span><span class="sxs-lookup"><span data-stu-id="1f28f-250">You can find out more about output columns of different machine learning tasks in the [Machine Learning Tasks](resources/tasks.md) guide.</span></span>

<span data-ttu-id="1f28f-251">Ważną właściwością DataView obiektów jest, że są one oceniane **leniwie**.</span><span class="sxs-lookup"><span data-stu-id="1f28f-251">An important property of DataView objects is that they are evaluated **lazily**.</span></span> <span data-ttu-id="1f28f-252">Widoki danych są ładowane i obsługiwane tylko podczas szkolenia i oceny modelu oraz prognozowania danych.</span><span class="sxs-lookup"><span data-stu-id="1f28f-252">Data views are only loaded and operated on during model training and evaluation, and data prediction.</span></span> <span data-ttu-id="1f28f-253">Podczas pisania i testowania aplikacji ML.NET, można użyć debugera Programu Visual Studio, aby zerknąć na dowolny obiekt widoku danych, wywołując [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview*) metody.</span><span class="sxs-lookup"><span data-stu-id="1f28f-253">While you are writing and testing your ML.NET application, you can use the Visual Studio debugger to take a peek at any data view object by calling the [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview*) method.</span></span>

```csharp
    var debug = testPriceDataView.Preview();
```

<span data-ttu-id="1f28f-254">Można obejrzeć `debug` zmienną w debugerze i sprawdzić jej zawartość.</span><span class="sxs-lookup"><span data-stu-id="1f28f-254">You can watch the `debug` variable in the debugger and examine its contents.</span></span> <span data-ttu-id="1f28f-255">Nie należy używać podglądu metody w kodzie produkcyjnym, ponieważ znacznie obniża wydajność.</span><span class="sxs-lookup"><span data-stu-id="1f28f-255">Do not use the Preview method in production code, as it significantly degrades performance.</span></span>

### <a name="model-deployment"></a><span data-ttu-id="1f28f-256">Wdrażanie modelu</span><span class="sxs-lookup"><span data-stu-id="1f28f-256">Model Deployment</span></span>

<span data-ttu-id="1f28f-257">W rzeczywistych aplikacjach kodu szkolenia i oceny modelu będzie oddzielony od prognozowania.</span><span class="sxs-lookup"><span data-stu-id="1f28f-257">In real-life applications, your model training and evaluation code will be separate from your prediction.</span></span> <span data-ttu-id="1f28f-258">W rzeczywistości te dwa działania są często wykonywane przez oddzielne zespoły.</span><span class="sxs-lookup"><span data-stu-id="1f28f-258">In fact, these two activities are often performed by separate teams.</span></span> <span data-ttu-id="1f28f-259">Zespół programistycznych modelu można zapisać model do użycia w aplikacji przewidywania.</span><span class="sxs-lookup"><span data-stu-id="1f28f-259">Your model development team can save the model for use in the prediction application.</span></span>

```csharp
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="next-steps"></a><span data-ttu-id="1f28f-260">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="1f28f-260">Next steps</span></span>

* <span data-ttu-id="1f28f-261">Dowiedz się, jak tworzyć aplikacje przy użyciu różnych zadań uczenia maszynowego z bardziej realistycznymi zestawami danych w [samouczkach](./tutorials/index.md).</span><span class="sxs-lookup"><span data-stu-id="1f28f-261">Learn how to build applications using different machine learning tasks with more realistic data sets in the [tutorials](./tutorials/index.md).</span></span>

* <span data-ttu-id="1f28f-262">Więcej informacji na temat konkretnych tematów można uzyskać w [podręcznikach Jak to zrobić.](./how-to-guides/index.md)</span><span class="sxs-lookup"><span data-stu-id="1f28f-262">Learn about specific topics in more depth in the [How To Guides](./how-to-guides/index.md).</span></span>

* <span data-ttu-id="1f28f-263">Jeśli jesteś bardzo zainteresowany, możesz zanurzyć się bezpośrednio w [dokumentacji referencyjnej API.](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet)</span><span class="sxs-lookup"><span data-stu-id="1f28f-263">If you're super keen, you can dive straight into the [API Reference documentation](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet).</span></span>
