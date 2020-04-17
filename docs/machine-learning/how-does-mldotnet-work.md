---
title: Co to jest ML.NET i jak to działa?
description: ML.NET umożliwia dodawanie uczenia maszynowego do aplikacji platformy .NET w scenariuszach online lub offline. Dzięki tej funkcji można dokonać automatycznych prognoz przy użyciu danych dostępnych dla aplikacji bez konieczności konieczności podłączenia do sieci do używania ML.NET. W tym artykule wyjaśniono podstawy uczenia maszynowego w ML.NET.
ms.date: 11/5/2019
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: 0929005e02ad9b43636213735f8c7232aa6d4f42
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607774"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a><span data-ttu-id="351d3-105">Co to jest ML.NET i jak to działa?</span><span class="sxs-lookup"><span data-stu-id="351d3-105">What is ML.NET and how does it work?</span></span>

<span data-ttu-id="351d3-106">ML.NET umożliwia dodawanie uczenia maszynowego do aplikacji platformy .NET w scenariuszach online lub offline.</span><span class="sxs-lookup"><span data-stu-id="351d3-106">ML.NET gives you the ability to add machine learning to .NET applications, in either online or offline scenarios.</span></span> <span data-ttu-id="351d3-107">Dzięki tej funkcji można dokonać automatycznych prognoz przy użyciu danych dostępnych dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="351d3-107">With this capability, you can make automatic predictions using the data available to your application.</span></span> <span data-ttu-id="351d3-108">Aplikacje uczenia maszynowego korzystają z wzorców w danych, aby przewidywanie, a nie muszą być jawnie zaprogramowane.</span><span class="sxs-lookup"><span data-stu-id="351d3-108">Machine learning applications make use of patterns in the data to make predictions rather than needing to be explicitly programmed.</span></span>

<span data-ttu-id="351d3-109">Centralnym ML.NET jest **model**uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="351d3-109">Central to ML.NET is a machine learning **model**.</span></span> <span data-ttu-id="351d3-110">Model określa kroki potrzebne do przekształcenia danych wejściowych w prognozę.</span><span class="sxs-lookup"><span data-stu-id="351d3-110">The model specifies the steps needed to transform your input data into a prediction.</span></span> <span data-ttu-id="351d3-111">Za pomocą ML.NET można trenować model niestandardowy, określając algorytm lub zaimportować wstępnie przeszkolone modele TensorFlow i ONNX.</span><span class="sxs-lookup"><span data-stu-id="351d3-111">With ML.NET, you can train a custom model by specifying an algorithm, or you can import pre-trained TensorFlow and ONNX models.</span></span>

<span data-ttu-id="351d3-112">Po modelu, można dodać go do aplikacji, aby prognoz.</span><span class="sxs-lookup"><span data-stu-id="351d3-112">Once you have a model, you can add it to your application to make the predictions.</span></span>

<span data-ttu-id="351d3-113">ML.NET działa w systemach Windows, Linux i macOS przy użyciu platformy .NET Core lub systemu Windows przy użyciu programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="351d3-113">ML.NET runs on Windows, Linux, and macOS using .NET Core, or Windows using .NET Framework.</span></span> <span data-ttu-id="351d3-114">64 bit jest obsługiwany na wszystkich platformach.</span><span class="sxs-lookup"><span data-stu-id="351d3-114">64 bit is supported on all platforms.</span></span> <span data-ttu-id="351d3-115">32-bitowe jest obsługiwane w systemie Windows, z wyjątkiem funkcji tensorflow, LightGBM i ONNX.</span><span class="sxs-lookup"><span data-stu-id="351d3-115">32 bit is supported on Windows, except for TensorFlow, LightGBM, and ONNX-related functionality.</span></span>

<span data-ttu-id="351d3-116">Przykłady typu prognoz, które można wykonać za pomocą ML.NET:</span><span class="sxs-lookup"><span data-stu-id="351d3-116">Examples of the type of predictions that you can make with ML.NET:</span></span>

|||
|-|-|
|<span data-ttu-id="351d3-117">Klasyfikacja/Kategoryzacja</span><span class="sxs-lookup"><span data-stu-id="351d3-117">Classification/Categorization</span></span>|<span data-ttu-id="351d3-118">Automatyczne dzielenie opinii klientów na kategorie pozytywne i negatywne</span><span class="sxs-lookup"><span data-stu-id="351d3-118">Automatically divide customer feedback into positive and negative categories</span></span>|
|<span data-ttu-id="351d3-119">Regresja/Przewidywanie wartości ciągłych</span><span class="sxs-lookup"><span data-stu-id="351d3-119">Regression/Predict continuous values</span></span>|<span data-ttu-id="351d3-120">Przewiduj ceny domów na podstawie wielkości i lokalizacji</span><span class="sxs-lookup"><span data-stu-id="351d3-120">Predict the price of houses based on size and location</span></span>|
|<span data-ttu-id="351d3-121">Wykrywanie anomalii</span><span class="sxs-lookup"><span data-stu-id="351d3-121">Anomaly Detection</span></span>|<span data-ttu-id="351d3-122">Wykrywanie nieuczciwych transakcji bankowych</span><span class="sxs-lookup"><span data-stu-id="351d3-122">Detect fraudulent banking transactions</span></span> |
|<span data-ttu-id="351d3-123">Zalecenia</span><span class="sxs-lookup"><span data-stu-id="351d3-123">Recommendations</span></span>|<span data-ttu-id="351d3-124">Zaproponuj produkty, które kupujący online mogą chcieć kupić, na podstawie ich poprzednich zakupów</span><span class="sxs-lookup"><span data-stu-id="351d3-124">Suggest products that online shoppers may want to buy, based on their previous purchases</span></span>|
|<span data-ttu-id="351d3-125">Szeregi czasowe/dane sekwencyjne</span><span class="sxs-lookup"><span data-stu-id="351d3-125">Time series/sequential data</span></span>|<span data-ttu-id="351d3-126">Prognoza pogody/sprzedaży produktów</span><span class="sxs-lookup"><span data-stu-id="351d3-126">Forecast the weather/product sales</span></span>|
|<span data-ttu-id="351d3-127">Klasyfikacja obrazów</span><span class="sxs-lookup"><span data-stu-id="351d3-127">Image classification</span></span>|<span data-ttu-id="351d3-128">Kategoryzowanie patologii na obrazach medycznych</span><span class="sxs-lookup"><span data-stu-id="351d3-128">Categorize pathologies in medical images</span></span>|

## <a name="hello-mlnet-world"></a><span data-ttu-id="351d3-129">Witam ML.NET świecie</span><span class="sxs-lookup"><span data-stu-id="351d3-129">Hello ML.NET World</span></span>

<span data-ttu-id="351d3-130">Kod w poniższym urywek pokazuje najprostszy ML.NET aplikacji.</span><span class="sxs-lookup"><span data-stu-id="351d3-130">The code in the following snippet demonstrates the simplest ML.NET application.</span></span> <span data-ttu-id="351d3-131">W tym przykładzie konstruuje model regresji liniowej do przewidywania cen domów przy użyciu wielkości domu i danych cenowych.</span><span class="sxs-lookup"><span data-stu-id="351d3-131">This example constructs a linear regression model to predict house prices using house size and price data.</span></span>

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

## <a name="code-workflow"></a><span data-ttu-id="351d3-132">Przepływ pracy kodu</span><span class="sxs-lookup"><span data-stu-id="351d3-132">Code workflow</span></span>

<span data-ttu-id="351d3-133">Poniższy diagram reprezentuje strukturę kodu aplikacji, a także iteracyjnego procesu tworzenia modelu:</span><span class="sxs-lookup"><span data-stu-id="351d3-133">The following diagram represents the application code structure, as well as the iterative process of model development:</span></span>

- <span data-ttu-id="351d3-134">Zbieranie i ładowanie danych szkoleniowych do obiektu **IDataView**</span><span class="sxs-lookup"><span data-stu-id="351d3-134">Collect and load training data into an **IDataView** object</span></span>
- <span data-ttu-id="351d3-135">Określanie potoku operacji wyodrębniania funkcji i stosowanie algorytmu uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="351d3-135">Specify a pipeline of operations to extract features and apply a machine learning algorithm</span></span>
- <span data-ttu-id="351d3-136">Trenuj model, wywołując **Fit()** na potoku</span><span class="sxs-lookup"><span data-stu-id="351d3-136">Train a model by calling **Fit()** on the pipeline</span></span>
- <span data-ttu-id="351d3-137">Oceń model i iteruj, aby poprawić</span><span class="sxs-lookup"><span data-stu-id="351d3-137">Evaluate the model and iterate to improve</span></span>
- <span data-ttu-id="351d3-138">Zapisywanie modelu w formacie binarnym do użycia w aplikacji</span><span class="sxs-lookup"><span data-stu-id="351d3-138">Save the model into binary format, for use in an application</span></span>
- <span data-ttu-id="351d3-139">Załaduj model z powrotem do obiektu **ITransformer**</span><span class="sxs-lookup"><span data-stu-id="351d3-139">Load the model back into an **ITransformer** object</span></span>
- <span data-ttu-id="351d3-140">Twórz prognozy, wywołując **CreatePredictionEngine.Predict()**</span><span class="sxs-lookup"><span data-stu-id="351d3-140">Make predictions by calling **CreatePredictionEngine.Predict()**</span></span>

![ML.NET przepływ tworzenia aplikacji, w tym składniki do generowania danych, tworzenia potoku, szkolenia modelu, oceny modelu i użycia modelu](./media/mldotnet-annotated-workflow.png)

<span data-ttu-id="351d3-142">Zagłębimy się nieco głębiej w te koncepcje.</span><span class="sxs-lookup"><span data-stu-id="351d3-142">Let's dig a little deeper into those concepts.</span></span>

## <a name="machine-learning-model"></a><span data-ttu-id="351d3-143">Model uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="351d3-143">Machine learning model</span></span>

<span data-ttu-id="351d3-144">Model ML.NET jest obiektem, który zawiera przekształcenia do wykonania na danych wejściowych, aby dotrzeć do przewidywanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="351d3-144">An ML.NET model is an object that contains transformations to perform on your input data to arrive at the predicted output.</span></span>

### <a name="basic"></a><span data-ttu-id="351d3-145">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="351d3-145">Basic</span></span>

<span data-ttu-id="351d3-146">Najbardziej podstawowym modelem jest dwuwymiarowa regresja liniowa, gdzie jedna ciągła ilość jest proporcjonalna do innej, jak w powyższym przykładzie ceny domu.</span><span class="sxs-lookup"><span data-stu-id="351d3-146">The most basic model is two-dimensional linear regression, where one continuous quantity is proportional to another, as in the house price example above.</span></span>

![Model regresji liniowej z parametrami odchylenia i masy](./media/linear-regression-model.svg)

<span data-ttu-id="351d3-148">Model jest po prostu: $Price = b + rozmiar \* w$.</span><span class="sxs-lookup"><span data-stu-id="351d3-148">The model is simply: $Price = b + Size \* w$.</span></span> <span data-ttu-id="351d3-149">Parametry $b$ i $w $ są szacowane przez dopasowanie linii na zestawie par (rozmiar, cena).</span><span class="sxs-lookup"><span data-stu-id="351d3-149">The parameters $b$ and $w$ are estimated by fitting a line on a set of (size, price) pairs.</span></span> <span data-ttu-id="351d3-150">Dane używane do znajdowania parametrów modelu nazywane są **danymi treningowymi**.</span><span class="sxs-lookup"><span data-stu-id="351d3-150">The data used to find the parameters of the model is called **training data**.</span></span> <span data-ttu-id="351d3-151">Dane wejściowe modelu uczenia maszynowego są nazywane **funkcjami**.</span><span class="sxs-lookup"><span data-stu-id="351d3-151">The inputs of a machine learning model are called **features**.</span></span> <span data-ttu-id="351d3-152">W tym przykładzie $Size$ jest jedyną funkcją.</span><span class="sxs-lookup"><span data-stu-id="351d3-152">In this example, $Size$ is the only feature.</span></span> <span data-ttu-id="351d3-153">Wartości prawdy gruntu używane do uczenia modelu uczenia maszynowego są nazywane **etykietami.**</span><span class="sxs-lookup"><span data-stu-id="351d3-153">The ground-truth values used to train a machine learning model are called **labels**.</span></span> <span data-ttu-id="351d3-154">W tym miejscu $Price$ wartości w zestawie danych szkolenia są etykiety.</span><span class="sxs-lookup"><span data-stu-id="351d3-154">Here, the $Price$ values in the training data set are the labels.</span></span>

### <a name="more-complex"></a><span data-ttu-id="351d3-155">Bardziej złożone</span><span class="sxs-lookup"><span data-stu-id="351d3-155">More complex</span></span>

<span data-ttu-id="351d3-156">Bardziej złożony model klasyfikuje transakcje finansowe na kategorie przy użyciu opisu tekstu transakcji.</span><span class="sxs-lookup"><span data-stu-id="351d3-156">A more complex model classifies financial transactions into categories using the transaction text description.</span></span>

<span data-ttu-id="351d3-157">Każdy opis transakcji jest podzielony na zestaw funkcji, usuwając zbędne wyrazy i znaki oraz licząc kombinacje słów i znaków.</span><span class="sxs-lookup"><span data-stu-id="351d3-157">Each transaction description is broken down into a set of features by removing redundant words and characters, and counting word and character combinations.</span></span> <span data-ttu-id="351d3-158">Zestaw funkcji służy do trenowania modelu liniowego na podstawie zestawu kategorii w danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="351d3-158">The feature set is used to train a linear model based on the set of categories in the training data.</span></span> <span data-ttu-id="351d3-159">Im bardziej podobny jest nowy opis do tych w zestawie treningowym, tym większe prawdopodobieństwo, że zostanie on przypisany do tej samej kategorii.</span><span class="sxs-lookup"><span data-stu-id="351d3-159">The more similar a new description is to the ones in the training set, the more likely it will be assigned to the same category.</span></span>

![Model klasyfikacji tekstu](./media/text-classification-model.svg)

<span data-ttu-id="351d3-161">Zarówno model ceny domu, jak i model klasyfikacji tekstu są modelami **liniowymi.**</span><span class="sxs-lookup"><span data-stu-id="351d3-161">Both the house price model and the text classification model are **linear** models.</span></span> <span data-ttu-id="351d3-162">W zależności od charakteru danych i rozwiązywanego problemu można również użyć modeli **drzewa decyzyjnego,** **uogólnionych** modeli dodatków i innych.</span><span class="sxs-lookup"><span data-stu-id="351d3-162">Depending on the nature of your data and the problem you are solving, you can also use **decision tree** models, **generalized additive** models, and others.</span></span> <span data-ttu-id="351d3-163">Możesz dowiedzieć się więcej o modelach w [zadaniach](./resources/tasks.md).</span><span class="sxs-lookup"><span data-stu-id="351d3-163">You can find out more about the models in [Tasks](./resources/tasks.md).</span></span>

## <a name="data-preparation"></a><span data-ttu-id="351d3-164">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="351d3-164">Data preparation</span></span>

<span data-ttu-id="351d3-165">W większości przypadków dostępne dane nie są odpowiednie do bezpośredniego uczenia modelu uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="351d3-165">In most cases, the data that you have available isn't suitable to be used directly to train a machine learning model.</span></span> <span data-ttu-id="351d3-166">Nieprzetworzone dane muszą być przygotowane lub wstępnie przetworzone, zanim będzie można je użyć do znalezienia parametrów modelu.</span><span class="sxs-lookup"><span data-stu-id="351d3-166">The raw data needs to be prepared, or pre-processed, before it can be used to find the parameters of your model.</span></span> <span data-ttu-id="351d3-167">Dane mogą wymagać konwersji z wartości ciągu na reprezentację numeryczną.</span><span class="sxs-lookup"><span data-stu-id="351d3-167">Your data may need to be converted from string values to a numerical representation.</span></span> <span data-ttu-id="351d3-168">W danych wejściowych mogą znajdować się nadmiarowe informacje.</span><span class="sxs-lookup"><span data-stu-id="351d3-168">You might have redundant information in your input data.</span></span> <span data-ttu-id="351d3-169">Może być konieczne zmniejszenie lub rozszerzenie wymiarów danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="351d3-169">You may need to reduce or expand the dimensions of your input data.</span></span> <span data-ttu-id="351d3-170">Dane mogą wymagać normalizacji lub skalowania.</span><span class="sxs-lookup"><span data-stu-id="351d3-170">Your data might need to be normalized or scaled.</span></span>

<span data-ttu-id="351d3-171">Samouczki [ML.NET](./tutorials/index.md) uczą o różnych potokach przetwarzania danych dla danych tekstowych, graficznych, numerycznych i szeregów czasowych używanych do określonych zadań uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="351d3-171">The [ML.NET tutorials](./tutorials/index.md) teach you about different data processing pipelines for text, image, numerical, and time-series data used for specific machine learning tasks.</span></span>

<span data-ttu-id="351d3-172">[Sposób przygotowania danych](./how-to-guides/prepare-data-ml-net.md) pokazuje, jak zastosować przygotowanie danych bardziej ogólnie.</span><span class="sxs-lookup"><span data-stu-id="351d3-172">[How to prepare your data](./how-to-guides/prepare-data-ml-net.md) shows you how to apply data preparation more generally.</span></span>

<span data-ttu-id="351d3-173">Dodatek wszystkich [dostępnych przekształceń](./resources/transforms.md) można znaleźć w sekcji zasoby.</span><span class="sxs-lookup"><span data-stu-id="351d3-173">You can find an appendix of all of the [available transformations](./resources/transforms.md) in the resources section.</span></span>

## <a name="model-evaluation"></a><span data-ttu-id="351d3-174">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="351d3-174">Model evaluation</span></span>

<span data-ttu-id="351d3-175">Po przeszkoleniu modelu, skąd wiesz, jak dobrze będzie to w przyszłości prognozy?</span><span class="sxs-lookup"><span data-stu-id="351d3-175">Once you have trained your model, how do you know how well it will make future predictions?</span></span> <span data-ttu-id="351d3-176">Za pomocą ML.NET można ocenić model na kilka nowych danych testowych.</span><span class="sxs-lookup"><span data-stu-id="351d3-176">With ML.NET, you can evaluate your model against some new test data.</span></span>

<span data-ttu-id="351d3-177">Każdy typ zadania uczenia maszynowego ma metryki używane do oceny dokładności i precyzji modelu względem zestawu danych testowych.</span><span class="sxs-lookup"><span data-stu-id="351d3-177">Each type of machine learning task has metrics used to evaluate the accuracy and precision of the model against the test data set.</span></span>

<span data-ttu-id="351d3-178">W naszym przykładzie ceny domu użyliśmy zadania **regresji.**</span><span class="sxs-lookup"><span data-stu-id="351d3-178">For our house price example, we used the **Regression** task.</span></span> <span data-ttu-id="351d3-179">Aby ocenić model, dodaj następujący kod do oryginalnego przykładu.</span><span class="sxs-lookup"><span data-stu-id="351d3-179">To evaluate the model, add the following code to the original sample.</span></span>

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

<span data-ttu-id="351d3-180">Metryki oceny mówią, że błąd jest niski-owski i że korelacja między przewidywanych danych wyjściowych i danych wyjściowych testu jest wysoka.</span><span class="sxs-lookup"><span data-stu-id="351d3-180">The evaluation metrics tell you that the error is low-ish, and that correlation between the predicted output and the test output is high.</span></span> <span data-ttu-id="351d3-181">To było łatwe!</span><span class="sxs-lookup"><span data-stu-id="351d3-181">That was easy!</span></span> <span data-ttu-id="351d3-182">W rzeczywistych przykładach potrzeba więcej strojenia, aby osiągnąć dobre metryki modelu.</span><span class="sxs-lookup"><span data-stu-id="351d3-182">In real examples, it takes more tuning to achieve good model metrics.</span></span>

## <a name="mlnet-architecture"></a><span data-ttu-id="351d3-183">architektura ML.NET</span><span class="sxs-lookup"><span data-stu-id="351d3-183">ML.NET architecture</span></span>

<span data-ttu-id="351d3-184">W tej sekcji przechodzimy przez wzory architektoniczne ML.NET.</span><span class="sxs-lookup"><span data-stu-id="351d3-184">In this section, we go through the architectural patterns of ML.NET.</span></span> <span data-ttu-id="351d3-185">Jeśli jesteś doświadczonym deweloperem platformy .NET, niektóre z tych wzorców będą ci znane, a niektóre będą mniej znane.</span><span class="sxs-lookup"><span data-stu-id="351d3-185">If you are an experienced .NET developer, some of these patterns will be familiar to you, and some will be less familiar.</span></span> <span data-ttu-id="351d3-186">Trzymaj się mocno, a my zanurzamy się!</span><span class="sxs-lookup"><span data-stu-id="351d3-186">Hold tight, while we dive in!</span></span>

<span data-ttu-id="351d3-187">Aplikacja ML.NET rozpoczyna się od <xref:Microsoft.ML.MLContext> obiektu.</span><span class="sxs-lookup"><span data-stu-id="351d3-187">An ML.NET application starts with an <xref:Microsoft.ML.MLContext> object.</span></span> <span data-ttu-id="351d3-188">Ten obiekt singleton zawiera **katalogi**.</span><span class="sxs-lookup"><span data-stu-id="351d3-188">This singleton object contains **catalogs**.</span></span> <span data-ttu-id="351d3-189">Katalog jest fabryką ładowania i zapisywania danych, przekształcania, trenerów i składników operacji modelu.</span><span class="sxs-lookup"><span data-stu-id="351d3-189">A catalog is a factory for data loading and saving, transforms, trainers, and model operation components.</span></span> <span data-ttu-id="351d3-190">Każdy obiekt katalogu ma metody tworzenia różnych typów składników:</span><span class="sxs-lookup"><span data-stu-id="351d3-190">Each catalog object has methods to create the different types of components:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="351d3-191">Ładowanie i zapisywanie danych</span><span class="sxs-lookup"><span data-stu-id="351d3-191">Data loading and saving</span></span>||<xref:Microsoft.ML.DataOperationsCatalog>||
|<span data-ttu-id="351d3-192">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="351d3-192">Data preparation</span></span>||<xref:Microsoft.ML.TransformsCatalog>||
|<span data-ttu-id="351d3-193">Algorytmy szkoleniowe</span><span class="sxs-lookup"><span data-stu-id="351d3-193">Training algorithms</span></span>|<span data-ttu-id="351d3-194">Klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="351d3-194">Binary classification</span></span>|<xref:Microsoft.ML.BinaryClassificationCatalog>||
||<span data-ttu-id="351d3-195">Klasyfikacja wieloklasowa</span><span class="sxs-lookup"><span data-stu-id="351d3-195">Multiclass classification</span></span>|<xref:Microsoft.ML.MulticlassClassificationCatalog>||
||<span data-ttu-id="351d3-196">Wykrywanie anomalii</span><span class="sxs-lookup"><span data-stu-id="351d3-196">Anomaly detection</span></span>|<xref:Microsoft.ML.AnomalyDetectionCatalog>||
||<span data-ttu-id="351d3-197">Klastrowanie</span><span class="sxs-lookup"><span data-stu-id="351d3-197">Clustering</span></span>|<xref:Microsoft.ML.ClusteringCatalog>||
||<span data-ttu-id="351d3-198">Prognozowanie</span><span class="sxs-lookup"><span data-stu-id="351d3-198">Forecasting</span></span>|<xref:Microsoft.ML.ForecastingCatalog>||
||<span data-ttu-id="351d3-199">Ranking</span><span class="sxs-lookup"><span data-stu-id="351d3-199">Ranking</span></span>|<xref:Microsoft.ML.RankingCatalog>||
||<span data-ttu-id="351d3-200">Regresja</span><span class="sxs-lookup"><span data-stu-id="351d3-200">Regression</span></span>|<xref:Microsoft.ML.RegressionCatalog>||
||<span data-ttu-id="351d3-201">Zalecenie</span><span class="sxs-lookup"><span data-stu-id="351d3-201">Recommendation</span></span>|<xref:Microsoft.ML.RecommendationCatalog>|<span data-ttu-id="351d3-202">dodawanie `Microsoft.ML.Recommender` pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="351d3-202">add the `Microsoft.ML.Recommender` NuGet package</span></span>|
||<span data-ttu-id="351d3-203">CzasSeries</span><span class="sxs-lookup"><span data-stu-id="351d3-203">TimeSeries</span></span>|<xref:Microsoft.ML.TimeSeriesCatalog>|<span data-ttu-id="351d3-204">dodawanie `Microsoft.ML.TimeSeries` pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="351d3-204">add the `Microsoft.ML.TimeSeries` NuGet package</span></span>|
|<span data-ttu-id="351d3-205">Użycie modelu</span><span class="sxs-lookup"><span data-stu-id="351d3-205">Model usage</span></span> ||<xref:Microsoft.ML.ModelOperationsCatalog>||

<span data-ttu-id="351d3-206">Można przejść do metod tworzenia w każdej z powyższych kategorii.</span><span class="sxs-lookup"><span data-stu-id="351d3-206">You can navigate to the creation methods in each of the above categories.</span></span> <span data-ttu-id="351d3-207">Za pomocą programu Visual Studio katalogi są wyświetlane za pośrednictwem programu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="351d3-207">Using Visual Studio, the catalogs show up via IntelliSense.</span></span>

   ![Intellisense dla trenerów regresji](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a><span data-ttu-id="351d3-209">Zbuduj potok</span><span class="sxs-lookup"><span data-stu-id="351d3-209">Build the pipeline</span></span>

<span data-ttu-id="351d3-210">Wewnątrz każdego katalogu znajduje się zestaw metod rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="351d3-210">Inside each catalog is a set of extension methods.</span></span> <span data-ttu-id="351d3-211">Przyjrzyjmy się, jak metody rozszerzenia są używane do tworzenia potoku szkolenia.</span><span class="sxs-lookup"><span data-stu-id="351d3-211">Let's look at how extension methods are used to create a training pipeline.</span></span>

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
```

<span data-ttu-id="351d3-212">We urywek `Concatenate` i `Sdca` są obie metody w katalogu.</span><span class="sxs-lookup"><span data-stu-id="351d3-212">In the snippet, `Concatenate` and `Sdca` are both methods in the catalog.</span></span> <span data-ttu-id="351d3-213">Każdy z nich tworzy obiekt [IEstimator,](xref:Microsoft.ML.IEstimator%601) który jest dołączany do potoku.</span><span class="sxs-lookup"><span data-stu-id="351d3-213">They each create an [IEstimator](xref:Microsoft.ML.IEstimator%601) object that is appended to the pipeline.</span></span>

<span data-ttu-id="351d3-214">W tym momencie obiekty są tworzone tylko.</span><span class="sxs-lookup"><span data-stu-id="351d3-214">At this point, the objects are created only.</span></span> <span data-ttu-id="351d3-215">Nie doszło do egzekucji.</span><span class="sxs-lookup"><span data-stu-id="351d3-215">No execution has happened.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="351d3-216">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="351d3-216">Train the model</span></span>

<span data-ttu-id="351d3-217">Po utworzeniu obiektów w potoku, dane mogą służyć do szkolenia modelu.</span><span class="sxs-lookup"><span data-stu-id="351d3-217">Once the objects in the pipeline have been created, data can be used to train the model.</span></span>

```csharp
    var model = pipeline.Fit(trainingData);
```

<span data-ttu-id="351d3-218">Wywołanie `Fit()` używa danych szkoleniowych wejściowych do oszacowania parametrów modelu.</span><span class="sxs-lookup"><span data-stu-id="351d3-218">Calling `Fit()` uses the input training data to estimate the parameters of the model.</span></span> <span data-ttu-id="351d3-219">Jest to znane jako szkolenie modelu.</span><span class="sxs-lookup"><span data-stu-id="351d3-219">This is known as training the model.</span></span> <span data-ttu-id="351d3-220">Pamiętaj, że model regresji liniowej powyżej miał dwa parametry modelu: **odchylenie** i **wagę**.</span><span class="sxs-lookup"><span data-stu-id="351d3-220">Remember, the linear regression model above had two model parameters: **bias** and **weight**.</span></span> <span data-ttu-id="351d3-221">Po `Fit()` wywołaniu znane są wartości parametrów.</span><span class="sxs-lookup"><span data-stu-id="351d3-221">After the `Fit()` call, the values of the parameters are known.</span></span> <span data-ttu-id="351d3-222">Większość modeli będzie miała o wiele więcej parametrów niż to.</span><span class="sxs-lookup"><span data-stu-id="351d3-222">Most models will have many more parameters than this.</span></span>

<span data-ttu-id="351d3-223">Możesz dowiedzieć się więcej o szkoleniu modelu w [jak trenować model](./how-to-guides/train-machine-learning-model-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="351d3-223">You can learn more about model training in [How to train your model](./how-to-guides/train-machine-learning-model-ml-net.md).</span></span>

<span data-ttu-id="351d3-224">Wynikowy obiekt modelu implementuje <xref:Microsoft.ML.ITransformer> interfejs.</span><span class="sxs-lookup"><span data-stu-id="351d3-224">The resulting model object implements the <xref:Microsoft.ML.ITransformer> interface.</span></span> <span data-ttu-id="351d3-225">Oznacza to, że model przekształca dane wejściowe w prognozy.</span><span class="sxs-lookup"><span data-stu-id="351d3-225">That is, the model transforms input data into predictions.</span></span>

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a><span data-ttu-id="351d3-226">Użyj modelu</span><span class="sxs-lookup"><span data-stu-id="351d3-226">Use the model</span></span>

<span data-ttu-id="351d3-227">Dane wejściowe można przekształcić w prognozowania zbiorczo lub jedno dane wejściowe naraz.</span><span class="sxs-lookup"><span data-stu-id="351d3-227">You can transform input data into predictions in bulk, or one input at a time.</span></span> <span data-ttu-id="351d3-228">W przykładzie ceny domu zrobiliśmy zarówno: luzem w celu oceny modelu, jak i jeden po drugim, aby dokonać nowej prognozy.</span><span class="sxs-lookup"><span data-stu-id="351d3-228">In the house price example, we did both: in bulk for the purpose of evaluating the model, and one at a time to make a new prediction.</span></span> <span data-ttu-id="351d3-229">Przyjrzyjmy się pojedynczym prognozom.</span><span class="sxs-lookup"><span data-stu-id="351d3-229">Let's look at making single predictions.</span></span>

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = mlContext.CreatePredictionEngine<HouseData, Prediction>(model);
    var price = predEngine.Predict(size);
```

<span data-ttu-id="351d3-230">Metoda `CreatePredictionEngine()` przyjmuje klasę danych wejściowych i klasę danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="351d3-230">The `CreatePredictionEngine()` method takes an input class and an output class.</span></span> <span data-ttu-id="351d3-231">Nazwy pól i/lub atrybuty kodu określają nazwy kolumn danych używanych podczas szkolenia i przewidywania modelu.</span><span class="sxs-lookup"><span data-stu-id="351d3-231">The field names and/or code attributes determine the names of the data columns used during model training and prediction.</span></span> <span data-ttu-id="351d3-232">Aby uzyskać więcej informacji, zobacz [Owydowienie prognoz z przeszkolonym modelem](how-to-guides/machine-learning-model-predictions-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="351d3-232">For more information, see [Make predictions with a trained model](how-to-guides/machine-learning-model-predictions-ml-net.md).</span></span>

### <a name="data-models-and-schema"></a><span data-ttu-id="351d3-233">Modele danych i schemat</span><span class="sxs-lookup"><span data-stu-id="351d3-233">Data models and schema</span></span>

<span data-ttu-id="351d3-234">Sednem ML.NET potoku uczenia maszynowego są obiekty [DataView.](xref:Microsoft.ML.IDataView)</span><span class="sxs-lookup"><span data-stu-id="351d3-234">At the core of an ML.NET machine learning pipeline are [DataView](xref:Microsoft.ML.IDataView) objects.</span></span>

<span data-ttu-id="351d3-235">Każda transformacja w potoku ma schemat wejściowy (nazwy danych, typy i rozmiary, które transformacja oczekuje, aby zobaczyć na jego danych wejściowych); oraz schemat danych wyjściowych (nazwy danych, typy i rozmiary, które transformacja tworzy po transformacji).</span><span class="sxs-lookup"><span data-stu-id="351d3-235">Each transformation in the pipeline has an input schema (data names, types, and sizes that the transform expects to see on its input); and an output schema (data names, types, and sizes that the transform produces after the transformation).</span></span> <span data-ttu-id="351d3-236">Poniższy dokument zawiera szczegółowe wyjaśnienie [interfejsu IDataView i jego systemu typów.](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html)</span><span class="sxs-lookup"><span data-stu-id="351d3-236">The following document provides an in-depth explanation of the [IDataView interface and its type system](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html).</span></span>

<span data-ttu-id="351d3-237">Jeśli schemat danych wyjściowych z jednego przekształcenia w potoku nie pasuje do schematu wejściowego następnego przekształcenia, ML.NET zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="351d3-237">If the output schema from one transform in the pipeline doesn't match the input schema of the next transform, ML.NET will throw an exception.</span></span>

<span data-ttu-id="351d3-238">Obiekt widoku danych zawiera kolumny i wiersze.</span><span class="sxs-lookup"><span data-stu-id="351d3-238">A data view object has columns and rows.</span></span> <span data-ttu-id="351d3-239">Każda kolumna ma nazwę, typ i długość.</span><span class="sxs-lookup"><span data-stu-id="351d3-239">Each column has a name and a type and a length.</span></span> <span data-ttu-id="351d3-240">Na przykład kolumny wejściowe w przykładzie ceny domu to **Rozmiar** i **Cena**.</span><span class="sxs-lookup"><span data-stu-id="351d3-240">For example, the input columns in the house price example are **Size** and **Price**.</span></span> <span data-ttu-id="351d3-241">Są one zarówno typu i są one skalarne ilości, a nie wektora.</span><span class="sxs-lookup"><span data-stu-id="351d3-241">They are both type and they are scalar quantities rather than vector ones.</span></span>

   ![przykład ML.NET Data View z danymi prognozowania cen nieruchomości](./media/ml-net-dataview.png)

<span data-ttu-id="351d3-243">Wszystkie algorytmy ML.NET wyszukują kolumnę wejściową, która jest wektorem.</span><span class="sxs-lookup"><span data-stu-id="351d3-243">All ML.NET algorithms look for an input column that is a vector.</span></span> <span data-ttu-id="351d3-244">Domyślnie ta kolumna wektorowa nosi nazwę **Funkcje**.</span><span class="sxs-lookup"><span data-stu-id="351d3-244">By default this vector column is called **Features**.</span></span> <span data-ttu-id="351d3-245">Dlatego połączyliśmy kolumnę **Rozmiar** z nową kolumną o nazwie **Funkcje** w naszym przykładzie ceny domu.</span><span class="sxs-lookup"><span data-stu-id="351d3-245">This is why we concatenated the **Size** column into a new column called **Features** in our house price example.</span></span>

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

<span data-ttu-id="351d3-246">Wszystkie algorytmy również utworzyć nowe kolumny po wykonaniu prognozowania.</span><span class="sxs-lookup"><span data-stu-id="351d3-246">All algorithms also create new columns after they have performed a prediction.</span></span> <span data-ttu-id="351d3-247">Stałe nazwy tych nowych kolumn zależą od typu algorytmu uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="351d3-247">The fixed names of these new columns depend on the type of machine learning algorithm.</span></span> <span data-ttu-id="351d3-248">W przypadku zadania regresji jedna z nowych kolumn nosi nazwę **Wynik**.</span><span class="sxs-lookup"><span data-stu-id="351d3-248">For the regression task, one of the new columns is called **Score**.</span></span> <span data-ttu-id="351d3-249">Dlatego przypisaliśmy nasze dane cenowe tą nazwą.</span><span class="sxs-lookup"><span data-stu-id="351d3-249">This is why we attributed our price data with this name.</span></span>

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```

<span data-ttu-id="351d3-250">Więcej informacji na temat kolumn wyjściowych różnych zadań uczenia maszynowego można znaleźć w przewodniku [Zadania uczenia maszynowego.](resources/tasks.md)</span><span class="sxs-lookup"><span data-stu-id="351d3-250">You can find out more about output columns of different machine learning tasks in the [Machine Learning Tasks](resources/tasks.md) guide.</span></span>

<span data-ttu-id="351d3-251">Ważną właściwością obiektów DataView jest to, że są one oceniane **leniwie.**</span><span class="sxs-lookup"><span data-stu-id="351d3-251">An important property of DataView objects is that they are evaluated **lazily**.</span></span> <span data-ttu-id="351d3-252">Widoki danych są ładowane i obsługiwane tylko podczas szkolenia i oceny modelu oraz przewidywania danych.</span><span class="sxs-lookup"><span data-stu-id="351d3-252">Data views are only loaded and operated on during model training and evaluation, and data prediction.</span></span> <span data-ttu-id="351d3-253">Podczas pisania i testowania aplikacji ML.NET, można użyć debugera programu Visual Studio, aby zajrzeć do dowolnego obiektu widoku danych, wywołując [metodę podglądu.](xref:Microsoft.ML.DebuggerExtensions.Preview*)</span><span class="sxs-lookup"><span data-stu-id="351d3-253">While you are writing and testing your ML.NET application, you can use the Visual Studio debugger to take a peek at any data view object by calling the [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview*) method.</span></span>

```csharp
    var debug = testPriceDataView.Preview();
```

<span data-ttu-id="351d3-254">Można obejrzeć `debug` zmienną w debugerze i zbadać jej zawartość.</span><span class="sxs-lookup"><span data-stu-id="351d3-254">You can watch the `debug` variable in the debugger and examine its contents.</span></span> <span data-ttu-id="351d3-255">Nie należy używać podglądu metody w kodzie produkcyjnym, ponieważ znacznie obniża wydajność.</span><span class="sxs-lookup"><span data-stu-id="351d3-255">Do not use the Preview method in production code, as it significantly degrades performance.</span></span>

### <a name="model-deployment"></a><span data-ttu-id="351d3-256">Wdrażanie modelu</span><span class="sxs-lookup"><span data-stu-id="351d3-256">Model Deployment</span></span>

<span data-ttu-id="351d3-257">W rzeczywistych aplikacjach kod szkolenia i oceny modelu będzie oddzielony od prognozowania.</span><span class="sxs-lookup"><span data-stu-id="351d3-257">In real-life applications, your model training and evaluation code will be separate from your prediction.</span></span> <span data-ttu-id="351d3-258">W rzeczywistości te dwie czynności są często wykonywane przez oddzielne zespoły.</span><span class="sxs-lookup"><span data-stu-id="351d3-258">In fact, these two activities are often performed by separate teams.</span></span> <span data-ttu-id="351d3-259">Zespół deweloperów modelu można zapisać modelu do użycia w aplikacji przewidywania.</span><span class="sxs-lookup"><span data-stu-id="351d3-259">Your model development team can save the model for use in the prediction application.</span></span>

```csharp
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="next-steps"></a><span data-ttu-id="351d3-260">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="351d3-260">Next steps</span></span>

* <span data-ttu-id="351d3-261">Dowiedz się, jak tworzyć aplikacje przy użyciu różnych zadań uczenia maszynowego z bardziej realistycznymi zestawami danych w [samouczkach](./tutorials/index.md).</span><span class="sxs-lookup"><span data-stu-id="351d3-261">Learn how to build applications using different machine learning tasks with more realistic data sets in the [tutorials](./tutorials/index.md).</span></span>

* <span data-ttu-id="351d3-262">Dowiedz się więcej o konkretnych tematach w [przewodnikach](./how-to-guides/index.md).</span><span class="sxs-lookup"><span data-stu-id="351d3-262">Learn about specific topics in more depth in the [How To Guides](./how-to-guides/index.md).</span></span>

* <span data-ttu-id="351d3-263">Jeśli jesteś bardzo chętny, możesz zanurzyć się bezpośrednio w [dokumentacji api reference.](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet)</span><span class="sxs-lookup"><span data-stu-id="351d3-263">If you're super keen, you can dive straight into the [API Reference documentation](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet).</span></span>
