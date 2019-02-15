---
title: Podstawowe pojęcia do trenowania modelu w strukturze ML.NET
description: W tym artykule opisano podstawowe pojęcia dotyczące *modelu szkolenia* scenariuszy w strukturze ML.NET. Nie wszystkie pojęcia są istotne dla bardziej prostego scenariusza *prognozowania z istniejącego modelu*.
ms.date: 02/13/2019
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: c47d5832527dca1416abfc55756dca48f1daf493
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56303663"
---
# <a name="basic-concepts-for-model-training-in-mlnet"></a><span data-ttu-id="2578d-104">Podstawowe pojęcia do trenowania modelu w strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="2578d-104">Basic concepts for model training in ML.NET</span></span>

<span data-ttu-id="2578d-105">W tym artykule opisano podstawowe pojęcia dotyczące *modelu szkolenia* scenariuszy w strukturze ML.NET.</span><span class="sxs-lookup"><span data-stu-id="2578d-105">This article explains the basic concepts covering *model training* scenarios in ML.NET.</span></span> <span data-ttu-id="2578d-106">Nie wszystkie pojęcia są istotne dla bardziej prostego scenariusza *prognozowania z istniejącego modelu*.</span><span class="sxs-lookup"><span data-stu-id="2578d-106">Not all concepts are relevant to the more simple scenario of *prediction with an existing model*.</span></span>

## <a name="model-training-concepts"></a><span data-ttu-id="2578d-107">Pojęcia dotyczące szkolenia modelu</span><span class="sxs-lookup"><span data-stu-id="2578d-107">Model training concepts</span></span>

<span data-ttu-id="2578d-108">W tym dokumencie opisano następujące pojęcia związane z szkolenia modelu w strukturze ML.NET:</span><span class="sxs-lookup"><span data-stu-id="2578d-108">This document covers the following concepts related to model training in ML.NET:</span></span>

- <span data-ttu-id="2578d-109">[*Dane* ](#data) reprezentowane jako `IDataView` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2578d-109">[*Data*](#data) represented as an `IDataView` interface.</span></span>
  - <span data-ttu-id="2578d-110">W strukturze ML.NET dane są podobne do widoku SQL: Jest cursorable opóźnieniem ocenianą, niemodyfikowalny, zestaw danych heterogenicznych, informatycznych.</span><span class="sxs-lookup"><span data-stu-id="2578d-110">In ML.NET, data is similar to a SQL view: It's a lazily evaluated, immutable, cursorable, heterogenous, schematized dataset.</span></span> 
  - <span data-ttu-id="2578d-111">Dokument doskonałą temat interfejs danych to [zasady projektowania IDataView](https://github.com/dotnet/machinelearning/blob/master/docs/code/IDataViewDesignPrinciples.md).</span><span class="sxs-lookup"><span data-stu-id="2578d-111">An excellent document about the data interface is [IDataView Design Principles](https://github.com/dotnet/machinelearning/blob/master/docs/code/IDataViewDesignPrinciples.md).</span></span>
- <span data-ttu-id="2578d-112">[*Transformer* ](#transformer) reprezentowane jako `ITransformer` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2578d-112">[*Transformer*](#transformer) represented as `ITransformer` interface.</span></span>
  - <span data-ttu-id="2578d-113">Transformer jest składnikiem, który pobiera dane, niektóre działa na nim i zwraca nowy przekształconych danych.</span><span class="sxs-lookup"><span data-stu-id="2578d-113">A transformer is a component that takes data, does some work on it, and returns new transformed data.</span></span>
  - <span data-ttu-id="2578d-114">Na przykład można traktować modelu uczenia maszynowego jako transformer, przyjmuje funkcji, która zwraca prognozy.</span><span class="sxs-lookup"><span data-stu-id="2578d-114">For example, you can think of a machine learning model as a transformer that takes features and returns predictions.</span></span>
  - <span data-ttu-id="2578d-115">Inny przykład tokenizatora tekst przyjmuje pojedynczej kolumny tekstowej i danych wyjściowych kolumny wektora z poszczególnych wyrazów wyodrębnione poza teksty.</span><span class="sxs-lookup"><span data-stu-id="2578d-115">Another example, text tokenizer takes a single text column and outputs a vector column with individual words extracted out of the texts.</span></span>
- <span data-ttu-id="2578d-116">[*Czytnik danych* ](#data-reader) reprezentowane jako `IDataReader<T>` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2578d-116">[*Data reader*](#data-reader) represented as an `IDataReader<T>` interface.</span></span>
  - <span data-ttu-id="2578d-117">Czytnik danych jest strukturze ML.NET składnika do utworzenia danych.</span><span class="sxs-lookup"><span data-stu-id="2578d-117">The data reader is ML.NET component to create data.</span></span> <span data-ttu-id="2578d-118">Trwa wystąpienie `T` i zwraca dane z niej.</span><span class="sxs-lookup"><span data-stu-id="2578d-118">It takes an instance of `T` and returns data out of it.</span></span> 
  - <span data-ttu-id="2578d-119">Na przykład *TextLoader* jest `IDataReader<IMultiStreamSource>`.</span><span class="sxs-lookup"><span data-stu-id="2578d-119">For example, a *TextLoader* is an `IDataReader<IMultiStreamSource>`.</span></span> <span data-ttu-id="2578d-120">Jego trwa źródłowego i generuje dane.</span><span class="sxs-lookup"><span data-stu-id="2578d-120">It takes the source and produces data.</span></span> 
- <span data-ttu-id="2578d-121">[*Narzędzie do szacowania* ](#estimator) reprezentowane jako `IEstimator<T>` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2578d-121">[*Estimator*](#estimator) represented as an `IEstimator<T>` interface.</span></span>
  - <span data-ttu-id="2578d-122">Jest to obiekt, który uzyskuje informacje o dane.</span><span class="sxs-lookup"><span data-stu-id="2578d-122">This is an object that learns from data.</span></span> <span data-ttu-id="2578d-123">Jest wynikiem szkoleniowe *transformatora*.</span><span class="sxs-lookup"><span data-stu-id="2578d-123">The result of the learning is a *transformer*.</span></span>
  - <span data-ttu-id="2578d-124">Można potraktować uczenia maszynowego *algorytm* jako narzędzie do szacowania, która uczy się na danych i uczenia maszynowego tworzy *modelu*.</span><span class="sxs-lookup"><span data-stu-id="2578d-124">You can think of a machine learning *algorithm* as an estimator that learns on data and produces a machine learning *model*.</span></span>
- <span data-ttu-id="2578d-125">[*Funkcja prognozowania* ](#prediction-function) reprezentowane jako `PredictionEngine<TSrc, TDst>` klasy.</span><span class="sxs-lookup"><span data-stu-id="2578d-125">[*Prediction function*](#prediction-function) represented as a `PredictionEngine<TSrc, TDst>` class.</span></span>
  - <span data-ttu-id="2578d-126">Funkcja prognozowania może być traktowany jako maszynie, która dotyczy transformatora jeden wiersz, takie jak w momencie prognozy.</span><span class="sxs-lookup"><span data-stu-id="2578d-126">The prediction function can be seen as a machine that applies a transformer to one row, such as at prediction time.</span></span>

## <a name="data"></a><span data-ttu-id="2578d-127">Dane</span><span class="sxs-lookup"><span data-stu-id="2578d-127">Data</span></span>

<span data-ttu-id="2578d-128">W strukturze ML.NET dane są podobne do widoku SQL: Jest opóźnieniem ocenianą, informatycznych cursorable heterogenicznych, zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="2578d-128">In ML.NET, data is similar to a SQL view: It's a lazily evaluated, cursorable, heterogenous, schematized dataset.</span></span>

- <span data-ttu-id="2578d-129">Ma ona *schematu* (wystąpienie `ISchema` interfejsu) zawierający informacje dotyczące kolumny widoku danych.</span><span class="sxs-lookup"><span data-stu-id="2578d-129">It has *Schema* (an instance of an `ISchema` interface) that contains the information about the data view's columns.</span></span>
  - <span data-ttu-id="2578d-130">Każda kolumna ma *nazwa*, *typu*i dowolnego zestawu *metadanych* skojarzonych z nim.</span><span class="sxs-lookup"><span data-stu-id="2578d-130">Each column has a *Name*, a *Type*, and an arbitrary set of *metadata* associated with it.</span></span>
  - <span data-ttu-id="2578d-131">W kolumnie *metadanych* zawiera informacje, takie jak miejsce nazwy kolumny wektora i podobne.</span><span class="sxs-lookup"><span data-stu-id="2578d-131">The column's *metadata* contains information like slot names of a vector column and the like.</span></span> <span data-ttu-id="2578d-132">Metadane, sama jest reprezentowany jako innego jednowierszowym *danych* unikatowy dla każdej kolumny.</span><span class="sxs-lookup"><span data-stu-id="2578d-132">The metadata itself is represented as another one-row *data* that is unique to each column.</span></span>
  - <span data-ttu-id="2578d-133">Widok danych to źródło *kursory*.</span><span class="sxs-lookup"><span data-stu-id="2578d-133">The data view is a source of *cursors*.</span></span> <span data-ttu-id="2578d-134">Reakcji kursorów SQL: Kursor jest obiekt, który iteruje po danych jeden wiersz w czasie i przedstawia dostępne dane.</span><span class="sxs-lookup"><span data-stu-id="2578d-134">Think SQL cursors: A cursor is an object that iterates through the data, one row at a time, and presents the available data.</span></span>
  - <span data-ttu-id="2578d-135">Oczywiście dane mogą mieć dowolną liczbę aktywnych kursorów nad nią zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="2578d-135">Naturally, data can have as many active cursors over it as needed.</span></span> <span data-ttu-id="2578d-136">Ponieważ dane są niezmienne, kursory są naprawdę niezależne.</span><span class="sxs-lookup"><span data-stu-id="2578d-136">Since data itself is immutable, cursors are truly independent.</span></span>
  - <span data-ttu-id="2578d-137">Kursory zwykle dostęp tylko podzbiór kolumn: W celu zwiększenia wydajności w strukturze ML.NET oblicza tylko wartości kolumn, które są wymagane przez kursor.</span><span class="sxs-lookup"><span data-stu-id="2578d-137">Cursors typically access only a subset of columns: For efficiency, ML.NET computes only the values of columns that are needed by the cursor.</span></span>

## <a name="transformer"></a><span data-ttu-id="2578d-138">Transformer</span><span class="sxs-lookup"><span data-stu-id="2578d-138">Transformer</span></span>

<span data-ttu-id="2578d-139">Transformer jest składnikiem, który pobiera dane, niektóre działa na nim i zwraca nowy przekształconych danych.</span><span class="sxs-lookup"><span data-stu-id="2578d-139">A transformer is a component that takes data, does some work on it, and returns new transformed data.</span></span>

<span data-ttu-id="2578d-140">Większość transformatory w strukturze ML.NET mają tendencję do działania na jednym *kolumny wejściowej* w czasie i wygenerować *kolumnę wyjściową*.</span><span class="sxs-lookup"><span data-stu-id="2578d-140">Most transformers in ML.NET tend to operate on one *input column* at a time, and produce the *output column*.</span></span> <span data-ttu-id="2578d-141">Na przykład `new HashTransformer("bar", "foo")` pobiera wartości z kolumny "foo", skróty je i umieszcza je w kolumnie "bar".</span><span class="sxs-lookup"><span data-stu-id="2578d-141">For example, a `new HashTransformer("bar", "foo")` takes the values from column "foo", hashes them, and puts them into column "bar".</span></span> 

<span data-ttu-id="2578d-142">Jest również typowe, że nazwy kolumn wejściowych i wyjściowych są takie same.</span><span class="sxs-lookup"><span data-stu-id="2578d-142">It's also common that the input and output column names are the same.</span></span> <span data-ttu-id="2578d-143">W tym przypadku starego kolumny jest zastępowany nowym.</span><span class="sxs-lookup"><span data-stu-id="2578d-143">In this case, the old column is replaced with the new one.</span></span> <span data-ttu-id="2578d-144">Na przykład `new HashTransformer("foo")` pobiera wartości z kolumny "foo", skróty je i umieszcza je z powrotem do "foo".</span><span class="sxs-lookup"><span data-stu-id="2578d-144">For example, a `new HashTransformer("foo")` takes the values from column "foo", hashes them, and puts them back into "foo".</span></span> 

<span data-ttu-id="2578d-145">Wszelkie transformer, tworzy nowe dane widoku, kiedy `Transform` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="2578d-145">Any transformer, produces a new data view when `Transform` is called.</span></span> <span data-ttu-id="2578d-146">Należy pamiętać, że widoki danych są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="2578d-146">Remember, data views are immutable.</span></span>

<span data-ttu-id="2578d-147">Innym ważnym zagadnieniem jest fakt, że ponieważ opóźnieniem szacowania danych *transformatory są powolne zbyt*.</span><span class="sxs-lookup"><span data-stu-id="2578d-147">Another important consideration is that, because data is lazily evaluated, *transformers are lazy too*.</span></span> <span data-ttu-id="2578d-148">Zasadniczo po wywołaniu</span><span class="sxs-lookup"><span data-stu-id="2578d-148">Essentially, after you call</span></span>

```csharp
var newData = transformer.Transform(oldData)
```

<span data-ttu-id="2578d-149">nie rzeczywiste obliczenia się nie dzieje.</span><span class="sxs-lookup"><span data-stu-id="2578d-149">no actual computation happens.</span></span> <span data-ttu-id="2578d-150">Tylko wtedy, gdy otrzymasz kursora z `newData` i rozpoczęcie używania wartość `newData` wywołania `transformer` logiki przekształcania (a nawet wówczas go tylko się dzieje w przypadku `transformer` jest zagrożona niezbędnych do wyprodukowania żądanej kolumny).</span><span class="sxs-lookup"><span data-stu-id="2578d-150">Only after you get a cursor from `newData` and start consuming the value does `newData` invoke the `transformer` transformation logic (and even then, it only happens if the `transformer` in question is needed to produce the requested columns).</span></span>

### <a name="transformer-chains"></a><span data-ttu-id="2578d-151">Łańcuchy transformatora</span><span class="sxs-lookup"><span data-stu-id="2578d-151">Transformer chains</span></span>

<span data-ttu-id="2578d-152">Jest przydatne właściwość transformatora *kolejność stosowania transformatorów tworzyć jako kolejny transformatora*:</span><span class="sxs-lookup"><span data-stu-id="2578d-152">A useful property of a transformer is that *you can build a sequential application of transformers as yet another transformer*:</span></span>

```csharp
var fullTransformer = transformer1.Append(transformer2).Append(transformer3);
```

<span data-ttu-id="2578d-153">Ta właściwość jest często używana w strukturze ML.NET: zazwyczaj uczonego modelu w strukturze ML.NET jest łańcuch transformatory, który jest na wszystkich intents i purposes, *transformatora*.</span><span class="sxs-lookup"><span data-stu-id="2578d-153">This property is commonly used in ML.NET: typically, the trained ML.NET model is a chain of transformers, which is, for all intents and purposes, a *transformer*.</span></span>

## <a name="data-reader"></a><span data-ttu-id="2578d-154">Czytnik danych</span><span class="sxs-lookup"><span data-stu-id="2578d-154">Data reader</span></span>

<span data-ttu-id="2578d-155">Czytnik danych jest składnikiem strukturze ML.NET, aby utworzyć dane: Trwa wystąpienie `T` i zwraca dane z niej.</span><span class="sxs-lookup"><span data-stu-id="2578d-155">The data reader is an ML.NET component to 'create' data: it takes an instance of `T` and returns data out of it.</span></span>

<span data-ttu-id="2578d-156">Interesujące właściwości, należy pamiętać, jest, czy można utworzyć czytnika danych, dołączając transformatora do istniejących czytnik danych.</span><span class="sxs-lookup"><span data-stu-id="2578d-156">An interesting property to note is that you can create a data reader by attaching a transformer to an existing data reader.</span></span> <span data-ttu-id="2578d-157">W ten sposób może mieć czytnik z działaniem przekształcania wbudowanymi:</span><span class="sxs-lookup"><span data-stu-id="2578d-157">This way you can have a reader with transformation behavior baked in:</span></span>

```csharp
var newReader = reader.Append(transformer1).Append(transformer2)
```

<span data-ttu-id="2578d-158">Inny podobieństwa do transformatory jest fakt, że ponieważ opóźnieniem szacowania danych *czytniki są powolne*: nie (lub minimalny) rzeczywiste odczytu się dzieje, gdy wywołujesz `reader.Read()`: tylko gdy kursor jest wymagane w danych wynikowych jest Czytnik rozpocząć pracę.</span><span class="sxs-lookup"><span data-stu-id="2578d-158">Another similarity to transformers is that, since data is lazily evaluated, *readers are lazy*: no (or minimal) actual 'reading' happens when you call `reader.Read()`: only when a cursor is requested on the resulting data does the reader begin to work.</span></span>

## <a name="estimator"></a><span data-ttu-id="2578d-159">Estimator</span><span class="sxs-lookup"><span data-stu-id="2578d-159">Estimator</span></span>

<span data-ttu-id="2578d-160">*Narzędzie do szacowania* jest obiektem, który uzyskuje informacje o dane.</span><span class="sxs-lookup"><span data-stu-id="2578d-160">The *estimator* is an object that learns from data.</span></span> <span data-ttu-id="2578d-161">Jest wynikiem szkoleniowe *transformatora*.</span><span class="sxs-lookup"><span data-stu-id="2578d-161">The result of the learning is a *transformer*.</span></span>

<span data-ttu-id="2578d-162">W strukturze ML.NET, ta właściwość umożliwia tworzenie potoków uczenia, połączonych ze sobą różnych aplikacjom:</span><span class="sxs-lookup"><span data-stu-id="2578d-162">In ML.NET, use this property to create learning pipelines that chain together different estimators:</span></span>

```csharp
MLContext mlContext = new MLContext(seed: 0);

var pipeline = mlContext.Transforms.CopyColumns("Label","FareAmount")
    .Append(mlContext.Transforms.Categorical.OneHotEncoding("VendorId"))
    .Append(mlContext.Transforms.Categorical.OneHotEncoding("RateCode"))
    .Append(mlContext.Transforms.Categorical.OneHotEncoding("PaymentType"))
    .Append(mlContext.Transforms.Concatenate("Features","VendorId","RateCode","PassengerCount","TripTime","TripDistance","PaymentType"))
    .Append(mlContext.Regression.Trainers.FastTree("Label","Features"));

var model = pipeline.Fit(dataView);
```

<span data-ttu-id="2578d-163">Co ważne właściwości aplikacjom jest fakt, że *aplikacjom to eager, nie z opóźnieniem*: każde wywołanie `Fit` powoduje uczenia się i tak się stanie, co jest potencjalnie czasochłonna operacja.</span><span class="sxs-lookup"><span data-stu-id="2578d-163">One important property of estimators is that *estimators are eager, not lazy*: every call to `Fit` is causing learning to happen, which is potentially a time-consuming operation.</span></span>

## <a name="prediction-function"></a><span data-ttu-id="2578d-164">Funkcja prognozowania</span><span class="sxs-lookup"><span data-stu-id="2578d-164">Prediction function</span></span>

<span data-ttu-id="2578d-165">Funkcja prognozowania może być traktowany jako składnik, który dotyczy transformatora jeden wiersz.</span><span class="sxs-lookup"><span data-stu-id="2578d-165">The prediction function can be seen as a component that applies a transformer to one row.</span></span>

<span data-ttu-id="2578d-166">Po pobraniu modelu ( *transformatora* uczony albo za pośrednictwem `Fit()`, lub załadowany z innej lokalizacji), służy do tworzyć prognozy przy użyciu normalnych wywołania `model.Transform(data)`.</span><span class="sxs-lookup"><span data-stu-id="2578d-166">Once you get the model (a *transformer* either trained via `Fit()`, or loaded from somewhere), you can use it to make predictions using the normal calls to `model.Transform(data)`.</span></span> <span data-ttu-id="2578d-167">Jednak jeśli używasz tego modelu w scenariuszu rzeczywistych często nie masz wiele przykładów do prognozowania na.</span><span class="sxs-lookup"><span data-stu-id="2578d-167">However, when you use this model in a real-life scenario, you often don't have many examples to predict on.</span></span> <span data-ttu-id="2578d-168">Zamiast tego ma przykładem w czasie i musisz prognozowania aktualnych na nich od razu.</span><span class="sxs-lookup"><span data-stu-id="2578d-168">Instead, you have one example at a time, and you need to make timely predictions on them immediately.</span></span>

<span data-ttu-id="2578d-169">Oczywiście może to zmniejszyć do prognozowania usługi batch:</span><span class="sxs-lookup"><span data-stu-id="2578d-169">Of course, you can reduce this to the batch prediction:</span></span>

- <span data-ttu-id="2578d-170">Utwórz widok danych przy użyciu dokładnie jeden wiersz.</span><span class="sxs-lookup"><span data-stu-id="2578d-170">Create a data view with exactly one row.</span></span>
- <span data-ttu-id="2578d-171">Wywołaj `model.Transform(data)` do wyświetlania warunków prognozowanych danych.</span><span class="sxs-lookup"><span data-stu-id="2578d-171">Call `model.Transform(data)` to get the predicted data view.</span></span>
- <span data-ttu-id="2578d-172">Pobieranie kursora nad dane wynikowe.</span><span class="sxs-lookup"><span data-stu-id="2578d-172">Get a cursor over the resulting data.</span></span>
- <span data-ttu-id="2578d-173">Przejdź jeden krok kursora, aby przejść do wiersza pierwszą (i jedyną).</span><span class="sxs-lookup"><span data-stu-id="2578d-173">Advance the cursor one step to get to the first (and only) row.</span></span>
- <span data-ttu-id="2578d-174">Wyodrębnij przewidywane wartości z niej.</span><span class="sxs-lookup"><span data-stu-id="2578d-174">Extract the predicted values out of it.</span></span>

<span data-ttu-id="2578d-175">Poprzedni algorytm można zaimplementować przy użyciu [zrozumienie schematu](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md), za pomocą dwóch obiektów zdefiniowanych przez użytkownika `InputExample` i `OutputPrediction` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="2578d-175">The preceding algorithm can be implemented using the [schema comprehension](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md), with two user-defined objects `InputExample` and `OutputPrediction` as follows:</span></span>

```csharp
var inputData = mlContext.Data.ReadFromEnumerable(new InputExample[] { example });
var outputData = model.Transform(inputData);
var output = mlContext.CreateEnumerable<OutputPrediction>(outputData,reuseRowObject:false).First();
```

<span data-ttu-id="2578d-176">Ale to jest skomplikowana względem i ponosi koszty wydajności.</span><span class="sxs-lookup"><span data-stu-id="2578d-176">But this is cumbersome and incurs performance costs.</span></span> <span data-ttu-id="2578d-177">Zamiast tego obiektu funkcji prognozowania wykonuje takie same pracy, ale szybciej i łatwiej za pomocą metody rozszerzenia `CreatePredictionEngine`:</span><span class="sxs-lookup"><span data-stu-id="2578d-177">Instead, a prediction function object performs the same work, but faster and more convenient, via an extension method `CreatePredictionEngine`:</span></span>

```csharp
var predictionEngine = model.CreatePredictionEngine<InputExample,OutputPrediction>(mlContext);
var prediction = predictionEngine.Predict(example);
```

<span data-ttu-id="2578d-178">Funkcja prognozowania *nie wielobieżnej / wątkowo*.</span><span class="sxs-lookup"><span data-stu-id="2578d-178">The prediction function is *not re-entrant / thread-safe*.</span></span> <span data-ttu-id="2578d-179">Jeśli chcesz przeprowadzić prognoz jednocześnie z wielu wątków, musisz mieć funkcji prognozowania na wątek.</span><span class="sxs-lookup"><span data-stu-id="2578d-179">If you want to conduct predictions simultaneously with multiple threads, you need to have a prediction function per thread.</span></span>
