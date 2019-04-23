---
title: Podstawowe pojęcia do trenowania modelu w strukturze ML.NET
description: W tym artykule opisano podstawowe pojęcia dotyczące *modelu szkolenia* scenariuszy w strukturze ML.NET. Nie wszystkie pojęcia są istotne dla bardziej prostego scenariusza *prognozowania z istniejącego modelu*.
ms.date: 03/05/2019
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: d29f6b901b0296f4d9a75b470a84dc087fb50e5d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973840"
---
# <a name="basic-concepts-for-model-training-in-mlnet"></a><span data-ttu-id="cc48c-104">Podstawowe pojęcia do trenowania modelu w strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="cc48c-104">Basic concepts for model training in ML.NET</span></span>

<span data-ttu-id="cc48c-105">W tym artykule opisano podstawowe pojęcia dotyczące *modelu szkolenia* scenariuszy w strukturze ML.NET.</span><span class="sxs-lookup"><span data-stu-id="cc48c-105">This article explains the basic concepts covering *model training* scenarios in ML.NET.</span></span> <span data-ttu-id="cc48c-106">Nie wszystkie pojęcia są istotne dla bardziej prostego scenariusza *prognozowania z istniejącego modelu*.</span><span class="sxs-lookup"><span data-stu-id="cc48c-106">Not all concepts are relevant to the more simple scenario of *prediction with an existing model*.</span></span>

<span data-ttu-id="cc48c-107">Obecnie używasz niniejszego artykułu i powiązane próbki **strukturze ML.NET wersji 0.10**.</span><span class="sxs-lookup"><span data-stu-id="cc48c-107">This article and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="cc48c-108">Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="cc48c-108">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

## <a name="model-training-concepts"></a><span data-ttu-id="cc48c-109">Pojęcia dotyczące szkolenia modelu</span><span class="sxs-lookup"><span data-stu-id="cc48c-109">Model training concepts</span></span>

<span data-ttu-id="cc48c-110">W tym dokumencie opisano następujące pojęcia związane z szkolenia modelu w strukturze ML.NET:</span><span class="sxs-lookup"><span data-stu-id="cc48c-110">This document covers the following concepts related to model training in ML.NET:</span></span>

- <span data-ttu-id="cc48c-111">[*Dane* ](#data) reprezentowane jako `IDataView` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="cc48c-111">[*Data*](#data) represented as an `IDataView` interface.</span></span>
  - <span data-ttu-id="cc48c-112">W strukturze ML.NET dane są podobne do widoku SQL: Jest cursorable opóźnieniem ocenianą, niemodyfikowalny, zestaw danych heterogenicznych, informatycznych.</span><span class="sxs-lookup"><span data-stu-id="cc48c-112">In ML.NET, data is similar to a SQL view: It's a lazily evaluated, immutable, cursorable, heterogenous, schematized dataset.</span></span> 
  - <span data-ttu-id="cc48c-113">Dokument doskonałą temat interfejs danych to [zasady projektowania IDataView](https://github.com/dotnet/machinelearning/blob/master/docs/code/IDataViewDesignPrinciples.md).</span><span class="sxs-lookup"><span data-stu-id="cc48c-113">An excellent document about the data interface is [IDataView Design Principles](https://github.com/dotnet/machinelearning/blob/master/docs/code/IDataViewDesignPrinciples.md).</span></span>
- <span data-ttu-id="cc48c-114">[*Transformer* ](#transformer) reprezentowane jako `ITransformer` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="cc48c-114">[*Transformer*](#transformer) represented as `ITransformer` interface.</span></span>
  - <span data-ttu-id="cc48c-115">Transformer jest składnikiem, który pobiera dane, niektóre działa na nim i zwraca nowy przekształconych danych.</span><span class="sxs-lookup"><span data-stu-id="cc48c-115">A transformer is a component that takes data, does some work on it, and returns new transformed data.</span></span>
  - <span data-ttu-id="cc48c-116">Na przykład można traktować modelu uczenia maszynowego jako transformer, przyjmuje funkcji, która zwraca prognozy.</span><span class="sxs-lookup"><span data-stu-id="cc48c-116">For example, you can think of a machine learning model as a transformer that takes features and returns predictions.</span></span>
  - <span data-ttu-id="cc48c-117">Inny przykład tokenizatora tekst przyjmuje pojedynczej kolumny tekstowej i danych wyjściowych kolumny wektora z poszczególnych wyrazów wyodrębnione poza teksty.</span><span class="sxs-lookup"><span data-stu-id="cc48c-117">Another example, text tokenizer takes a single text column and outputs a vector column with individual words extracted out of the texts.</span></span>
- <span data-ttu-id="cc48c-118">[*Czytnik danych* ](#data-reader) reprezentowane jako `IDataReader<T>` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="cc48c-118">[*Data reader*](#data-reader) represented as an `IDataReader<T>` interface.</span></span>
  - <span data-ttu-id="cc48c-119">Czytnik danych jest strukturze ML.NET składnika do utworzenia danych.</span><span class="sxs-lookup"><span data-stu-id="cc48c-119">The data reader is ML.NET component to create data.</span></span> <span data-ttu-id="cc48c-120">Trwa wystąpienie `T` i zwraca dane z niej.</span><span class="sxs-lookup"><span data-stu-id="cc48c-120">It takes an instance of `T` and returns data out of it.</span></span> 
  - <span data-ttu-id="cc48c-121">Na przykład *TextLoader* jest `IDataReader<IMultiStreamSource>`.</span><span class="sxs-lookup"><span data-stu-id="cc48c-121">For example, a *TextLoader* is an `IDataReader<IMultiStreamSource>`.</span></span> <span data-ttu-id="cc48c-122">Jego trwa źródłowego i generuje dane.</span><span class="sxs-lookup"><span data-stu-id="cc48c-122">It takes the source and produces data.</span></span> 
- <span data-ttu-id="cc48c-123">[*Narzędzie do szacowania* ](#estimator) reprezentowane jako `IEstimator<T>` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="cc48c-123">[*Estimator*](#estimator) represented as an `IEstimator<T>` interface.</span></span>
  - <span data-ttu-id="cc48c-124">Jest to obiekt, który uzyskuje informacje o dane.</span><span class="sxs-lookup"><span data-stu-id="cc48c-124">This is an object that learns from data.</span></span> <span data-ttu-id="cc48c-125">Jest wynikiem szkoleniowe *transformatora*.</span><span class="sxs-lookup"><span data-stu-id="cc48c-125">The result of the learning is a *transformer*.</span></span>
  - <span data-ttu-id="cc48c-126">Można potraktować uczenia maszynowego *algorytm* jako narzędzie do szacowania, która uczy się na danych i uczenia maszynowego tworzy *modelu*.</span><span class="sxs-lookup"><span data-stu-id="cc48c-126">You can think of a machine learning *algorithm* as an estimator that learns on data and produces a machine learning *model*.</span></span>
- <span data-ttu-id="cc48c-127">[*Funkcja prognozowania* ](#prediction-function) reprezentowane jako `PredictionEngine<TSrc, TDst>` klasy.</span><span class="sxs-lookup"><span data-stu-id="cc48c-127">[*Prediction function*](#prediction-function) represented as a `PredictionEngine<TSrc, TDst>` class.</span></span>
  - <span data-ttu-id="cc48c-128">Funkcja prognozowania może być traktowany jako maszynie, która dotyczy transformatora jeden wiersz, takie jak w momencie prognozy.</span><span class="sxs-lookup"><span data-stu-id="cc48c-128">The prediction function can be seen as a machine that applies a transformer to one row, such as at prediction time.</span></span>

## <a name="data"></a><span data-ttu-id="cc48c-129">Dane</span><span class="sxs-lookup"><span data-stu-id="cc48c-129">Data</span></span> 

<span data-ttu-id="cc48c-130">W strukturze ML.NET dane są podobne do widoku SQL: Jest opóźnieniem ocenianą, informatycznych cursorable heterogenicznych, zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="cc48c-130">In ML.NET, data is similar to a SQL view: It's a lazily evaluated, cursorable, heterogenous, schematized dataset.</span></span>

- <span data-ttu-id="cc48c-131">Ma ona *schematu* (wystąpienie `ISchema` interfejsu) zawierający informacje dotyczące kolumny widoku danych.</span><span class="sxs-lookup"><span data-stu-id="cc48c-131">It has *Schema* (an instance of an `ISchema` interface) that contains the information about the data view's columns.</span></span>
  - <span data-ttu-id="cc48c-132">Każda kolumna ma *nazwa*, *typu*i dowolnego zestawu *metadanych* skojarzonych z nim.</span><span class="sxs-lookup"><span data-stu-id="cc48c-132">Each column has a *Name*, a *Type*, and an arbitrary set of *metadata* associated with it.</span></span>
  - <span data-ttu-id="cc48c-133">W kolumnie *metadanych* zawiera informacje, takie jak miejsce nazwy kolumny wektora i podobne.</span><span class="sxs-lookup"><span data-stu-id="cc48c-133">The column's *metadata* contains information like slot names of a vector column and the like.</span></span> <span data-ttu-id="cc48c-134">Metadane, sama jest reprezentowany jako innego jednowierszowym *danych* unikatowy dla każdej kolumny.</span><span class="sxs-lookup"><span data-stu-id="cc48c-134">The metadata itself is represented as another one-row *data* that is unique to each column.</span></span>
  - <span data-ttu-id="cc48c-135">Widok danych to źródło *kursory*.</span><span class="sxs-lookup"><span data-stu-id="cc48c-135">The data view is a source of *cursors*.</span></span> <span data-ttu-id="cc48c-136">Reakcji kursorów SQL: Kursor jest obiekt, który iteruje po danych jeden wiersz w czasie i przedstawia dostępne dane.</span><span class="sxs-lookup"><span data-stu-id="cc48c-136">Think SQL cursors: A cursor is an object that iterates through the data, one row at a time, and presents the available data.</span></span>
  - <span data-ttu-id="cc48c-137">Oczywiście dane mogą mieć dowolną liczbę aktywnych kursorów nad nią zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="cc48c-137">Naturally, data can have as many active cursors over it as needed.</span></span> <span data-ttu-id="cc48c-138">Ponieważ dane są niezmienne, kursory są naprawdę niezależne.</span><span class="sxs-lookup"><span data-stu-id="cc48c-138">Since data itself is immutable, cursors are truly independent.</span></span>
  - <span data-ttu-id="cc48c-139">Kursory zwykle dostęp tylko podzbiór kolumn: W celu zwiększenia wydajności w strukturze ML.NET oblicza tylko wartości kolumn, które są wymagane przez kursor.</span><span class="sxs-lookup"><span data-stu-id="cc48c-139">Cursors typically access only a subset of columns: For efficiency, ML.NET computes only the values of columns that are needed by the cursor.</span></span>

## <a name="transformer"></a><span data-ttu-id="cc48c-140">Transformer</span><span class="sxs-lookup"><span data-stu-id="cc48c-140">Transformer</span></span>

<span data-ttu-id="cc48c-141">Transformer jest składnikiem, który pobiera dane, niektóre działa na nim i zwraca nowy przekształconych danych.</span><span class="sxs-lookup"><span data-stu-id="cc48c-141">A transformer is a component that takes data, does some work on it, and returns new transformed data.</span></span>

<span data-ttu-id="cc48c-142">Większość transformatory w strukturze ML.NET mają tendencję do działania na jednym *kolumny wejściowej* w czasie i wygenerować *kolumnę wyjściową*.</span><span class="sxs-lookup"><span data-stu-id="cc48c-142">Most transformers in ML.NET tend to operate on one *input column* at a time, and produce the *output column*.</span></span> <span data-ttu-id="cc48c-143">Na przykład `new HashTransformer("bar", "foo")` pobiera wartości z kolumny "foo", skróty je i umieszcza je w kolumnie "bar".</span><span class="sxs-lookup"><span data-stu-id="cc48c-143">For example, a `new HashTransformer("bar", "foo")` takes the values from column "foo", hashes them, and puts them into column "bar".</span></span> 

<span data-ttu-id="cc48c-144">Jest również typowe, że nazwy kolumn wejściowych i wyjściowych są takie same.</span><span class="sxs-lookup"><span data-stu-id="cc48c-144">It's also common that the input and output column names are the same.</span></span> <span data-ttu-id="cc48c-145">W tym przypadku starego kolumny jest zastępowany nowym.</span><span class="sxs-lookup"><span data-stu-id="cc48c-145">In this case, the old column is replaced with the new one.</span></span> <span data-ttu-id="cc48c-146">Na przykład `new HashTransformer("foo")` pobiera wartości z kolumny "foo", skróty je i umieszcza je z powrotem do "foo".</span><span class="sxs-lookup"><span data-stu-id="cc48c-146">For example, a `new HashTransformer("foo")` takes the values from column "foo", hashes them, and puts them back into "foo".</span></span> 

<span data-ttu-id="cc48c-147">Wszelkie transformer, tworzy nowe dane widoku, kiedy `Transform` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="cc48c-147">Any transformer, produces a new data view when `Transform` is called.</span></span> <span data-ttu-id="cc48c-148">Należy pamiętać, że widoki danych są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="cc48c-148">Remember, data views are immutable.</span></span>

<span data-ttu-id="cc48c-149">Innym ważnym zagadnieniem jest fakt, że ponieważ opóźnieniem szacowania danych *transformatory są powolne zbyt*.</span><span class="sxs-lookup"><span data-stu-id="cc48c-149">Another important consideration is that, because data is lazily evaluated, *transformers are lazy too*.</span></span> <span data-ttu-id="cc48c-150">Zasadniczo po wywołaniu</span><span class="sxs-lookup"><span data-stu-id="cc48c-150">Essentially, after you call</span></span>

```csharp
var newData = transformer.Transform(oldData)
```

<span data-ttu-id="cc48c-151">nie rzeczywiste obliczenia się nie dzieje.</span><span class="sxs-lookup"><span data-stu-id="cc48c-151">no actual computation happens.</span></span> <span data-ttu-id="cc48c-152">Tylko wtedy, gdy otrzymasz kursora z `newData` i rozpoczęcie używania wartość `newData` wywołania `transformer` logiki przekształcania (a nawet wówczas go tylko się dzieje w przypadku `transformer` jest zagrożona niezbędnych do wyprodukowania żądanej kolumny).</span><span class="sxs-lookup"><span data-stu-id="cc48c-152">Only after you get a cursor from `newData` and start consuming the value does `newData` invoke the `transformer` transformation logic (and even then, it only happens if the `transformer` in question is needed to produce the requested columns).</span></span>

### <a name="transformer-chains"></a><span data-ttu-id="cc48c-153">Łańcuchy transformatora</span><span class="sxs-lookup"><span data-stu-id="cc48c-153">Transformer chains</span></span>

<span data-ttu-id="cc48c-154">Jest przydatne właściwość transformatora *kolejność stosowania transformatorów tworzyć jako kolejny transformatora*:</span><span class="sxs-lookup"><span data-stu-id="cc48c-154">A useful property of a transformer is that *you can build a sequential application of transformers as yet another transformer*:</span></span>

```csharp
var fullTransformer = transformer1.Append(transformer2).Append(transformer3);
```

<span data-ttu-id="cc48c-155">Ta właściwość jest często używana w strukturze ML.NET: zazwyczaj uczonego modelu w strukturze ML.NET jest łańcuch transformatory, który jest na wszystkich intents i purposes, *transformatora*.</span><span class="sxs-lookup"><span data-stu-id="cc48c-155">This property is commonly used in ML.NET: typically, the trained ML.NET model is a chain of transformers, which is, for all intents and purposes, a *transformer*.</span></span>

## <a name="data-reader"></a><span data-ttu-id="cc48c-156">Czytnik danych</span><span class="sxs-lookup"><span data-stu-id="cc48c-156">Data reader</span></span>

<span data-ttu-id="cc48c-157">Czytnik danych jest składnikiem strukturze ML.NET, aby utworzyć dane: Trwa wystąpienie `T` i zwraca dane z niej.</span><span class="sxs-lookup"><span data-stu-id="cc48c-157">The data reader is an ML.NET component to 'create' data: it takes an instance of `T` and returns data out of it.</span></span>

<span data-ttu-id="cc48c-158">Interesujące właściwości, należy pamiętać, jest, czy można utworzyć czytnika danych, dołączając transformatora do istniejących czytnik danych.</span><span class="sxs-lookup"><span data-stu-id="cc48c-158">An interesting property to note is that you can create a data reader by attaching a transformer to an existing data reader.</span></span> <span data-ttu-id="cc48c-159">W ten sposób może mieć czytnik z działaniem przekształcania wbudowanymi:</span><span class="sxs-lookup"><span data-stu-id="cc48c-159">This way you can have a reader with transformation behavior baked in:</span></span>

```csharp
var newReader = reader.Append(transformer1).Append(transformer2)
```

<span data-ttu-id="cc48c-160">Inny podobieństwa do transformatory jest fakt, że ponieważ opóźnieniem szacowania danych *czytniki są powolne*: nie (lub minimalny) rzeczywiste odczytu się dzieje, gdy wywołujesz `reader.Read()`: tylko gdy kursor jest wymagane w danych wynikowych jest Czytnik rozpocząć pracę.</span><span class="sxs-lookup"><span data-stu-id="cc48c-160">Another similarity to transformers is that, since data is lazily evaluated, *readers are lazy*: no (or minimal) actual 'reading' happens when you call `reader.Read()`: only when a cursor is requested on the resulting data does the reader begin to work.</span></span>

## <a name="estimator"></a><span data-ttu-id="cc48c-161">Estimator</span><span class="sxs-lookup"><span data-stu-id="cc48c-161">Estimator</span></span>

<span data-ttu-id="cc48c-162">*Narzędzie do szacowania* jest obiektem, który uzyskuje informacje o dane.</span><span class="sxs-lookup"><span data-stu-id="cc48c-162">The *estimator* is an object that learns from data.</span></span> <span data-ttu-id="cc48c-163">Jest wynikiem szkoleniowe *transformatora*.</span><span class="sxs-lookup"><span data-stu-id="cc48c-163">The result of the learning is a *transformer*.</span></span>

<span data-ttu-id="cc48c-164">W strukturze ML.NET, ta właściwość umożliwia tworzenie potoków uczenia, połączonych ze sobą różnych aplikacjom:</span><span class="sxs-lookup"><span data-stu-id="cc48c-164">In ML.NET, use this property to create learning pipelines that chain together different estimators:</span></span>

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

<span data-ttu-id="cc48c-165">Co ważne właściwości aplikacjom jest fakt, że *aplikacjom to eager, nie z opóźnieniem*: każde wywołanie `Fit` powoduje uczenia się i tak się stanie, co jest potencjalnie czasochłonna operacja.</span><span class="sxs-lookup"><span data-stu-id="cc48c-165">One important property of estimators is that *estimators are eager, not lazy*: every call to `Fit` is causing learning to happen, which is potentially a time-consuming operation.</span></span>

## <a name="prediction-function"></a><span data-ttu-id="cc48c-166">Funkcja prognozowania</span><span class="sxs-lookup"><span data-stu-id="cc48c-166">Prediction function</span></span>

<span data-ttu-id="cc48c-167">Funkcja prognozowania może być traktowany jako składnik, który dotyczy transformatora jeden wiersz.</span><span class="sxs-lookup"><span data-stu-id="cc48c-167">The prediction function can be seen as a component that applies a transformer to one row.</span></span>

<span data-ttu-id="cc48c-168">Po pobraniu modelu ( *transformatora* uczony albo za pośrednictwem `Fit()`, lub załadowany z innej lokalizacji), służy do tworzyć prognozy przy użyciu normalnych wywołania `model.Transform(data)`.</span><span class="sxs-lookup"><span data-stu-id="cc48c-168">Once you get the model (a *transformer* either trained via `Fit()`, or loaded from somewhere), you can use it to make predictions using the normal calls to `model.Transform(data)`.</span></span> <span data-ttu-id="cc48c-169">Jednak jeśli używasz tego modelu w scenariuszu rzeczywistych często nie masz wiele przykładów do prognozowania na.</span><span class="sxs-lookup"><span data-stu-id="cc48c-169">However, when you use this model in a real-life scenario, you often don't have many examples to predict on.</span></span> <span data-ttu-id="cc48c-170">Zamiast tego ma przykładem w czasie i musisz prognozowania aktualnych na nich od razu.</span><span class="sxs-lookup"><span data-stu-id="cc48c-170">Instead, you have one example at a time, and you need to make timely predictions on them immediately.</span></span>

<span data-ttu-id="cc48c-171">Oczywiście może to zmniejszyć do prognozowania usługi batch:</span><span class="sxs-lookup"><span data-stu-id="cc48c-171">Of course, you can reduce this to the batch prediction:</span></span>

- <span data-ttu-id="cc48c-172">Utwórz widok danych przy użyciu dokładnie jeden wiersz.</span><span class="sxs-lookup"><span data-stu-id="cc48c-172">Create a data view with exactly one row.</span></span>
- <span data-ttu-id="cc48c-173">Wywołaj `model.Transform(data)` do wyświetlania warunków prognozowanych danych.</span><span class="sxs-lookup"><span data-stu-id="cc48c-173">Call `model.Transform(data)` to get the predicted data view.</span></span>
- <span data-ttu-id="cc48c-174">Pobieranie kursora nad dane wynikowe.</span><span class="sxs-lookup"><span data-stu-id="cc48c-174">Get a cursor over the resulting data.</span></span>
- <span data-ttu-id="cc48c-175">Przejdź jeden krok kursora, aby przejść do wiersza pierwszą (i jedyną).</span><span class="sxs-lookup"><span data-stu-id="cc48c-175">Advance the cursor one step to get to the first (and only) row.</span></span>
- <span data-ttu-id="cc48c-176">Wyodrębnij przewidywane wartości z niej.</span><span class="sxs-lookup"><span data-stu-id="cc48c-176">Extract the predicted values out of it.</span></span>

<span data-ttu-id="cc48c-177">Poprzedni algorytm można zaimplementować przy użyciu [zrozumienie schematu](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md), za pomocą dwóch obiektów zdefiniowanych przez użytkownika `InputExample` i `OutputPrediction` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="cc48c-177">The preceding algorithm can be implemented using the [schema comprehension](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md), with two user-defined objects `InputExample` and `OutputPrediction` as follows:</span></span>

```csharp
var inputData = mlContext.Data.ReadFromEnumerable(new InputExample[] { example });
var outputData = model.Transform(inputData);
var output = mlContext.CreateEnumerable<OutputPrediction>(outputData,reuseRowObject:false).First();
```

<span data-ttu-id="cc48c-178">Ale to jest skomplikowana względem i ponosi koszty wydajności.</span><span class="sxs-lookup"><span data-stu-id="cc48c-178">But this is cumbersome and incurs performance costs.</span></span> <span data-ttu-id="cc48c-179">Zamiast tego obiektu funkcji prognozowania wykonuje takie same pracy, ale szybciej i łatwiej za pomocą metody rozszerzenia `CreatePredictionEngine`:</span><span class="sxs-lookup"><span data-stu-id="cc48c-179">Instead, a prediction function object performs the same work, but faster and more convenient, via an extension method `CreatePredictionEngine`:</span></span>

```csharp
var predictionEngine = model.CreatePredictionEngine<InputExample,OutputPrediction>(mlContext);
var prediction = predictionEngine.Predict(example);
```

<span data-ttu-id="cc48c-180">Funkcja prognozowania *nie wielobieżnej / wątkowo*.</span><span class="sxs-lookup"><span data-stu-id="cc48c-180">The prediction function is *not re-entrant / thread-safe*.</span></span> <span data-ttu-id="cc48c-181">Jeśli chcesz przeprowadzić prognoz jednocześnie z wielu wątków, musisz mieć funkcji prognozowania na wątek.</span><span class="sxs-lookup"><span data-stu-id="cc48c-181">If you want to conduct predictions simultaneously with multiple threads, you need to have a prediction function per thread.</span></span>
