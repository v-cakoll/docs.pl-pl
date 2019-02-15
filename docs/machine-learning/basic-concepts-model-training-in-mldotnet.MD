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
# <a name="basic-concepts-for-model-training-in-mlnet"></a>Podstawowe pojęcia do trenowania modelu w strukturze ML.NET

W tym artykule opisano podstawowe pojęcia dotyczące *modelu szkolenia* scenariuszy w strukturze ML.NET. Nie wszystkie pojęcia są istotne dla bardziej prostego scenariusza *prognozowania z istniejącego modelu*.

## <a name="model-training-concepts"></a>Pojęcia dotyczące szkolenia modelu

W tym dokumencie opisano następujące pojęcia związane z szkolenia modelu w strukturze ML.NET:

- [*Dane* ](#data) reprezentowane jako `IDataView` interfejsu.
  - W strukturze ML.NET dane są podobne do widoku SQL: Jest cursorable opóźnieniem ocenianą, niemodyfikowalny, zestaw danych heterogenicznych, informatycznych. 
  - Dokument doskonałą temat interfejs danych to [zasady projektowania IDataView](https://github.com/dotnet/machinelearning/blob/master/docs/code/IDataViewDesignPrinciples.md).
- [*Transformer* ](#transformer) reprezentowane jako `ITransformer` interfejsu.
  - Transformer jest składnikiem, który pobiera dane, niektóre działa na nim i zwraca nowy przekształconych danych.
  - Na przykład można traktować modelu uczenia maszynowego jako transformer, przyjmuje funkcji, która zwraca prognozy.
  - Inny przykład tokenizatora tekst przyjmuje pojedynczej kolumny tekstowej i danych wyjściowych kolumny wektora z poszczególnych wyrazów wyodrębnione poza teksty.
- [*Czytnik danych* ](#data-reader) reprezentowane jako `IDataReader<T>` interfejsu.
  - Czytnik danych jest strukturze ML.NET składnika do utworzenia danych. Trwa wystąpienie `T` i zwraca dane z niej. 
  - Na przykład *TextLoader* jest `IDataReader<IMultiStreamSource>`. Jego trwa źródłowego i generuje dane. 
- [*Narzędzie do szacowania* ](#estimator) reprezentowane jako `IEstimator<T>` interfejsu.
  - Jest to obiekt, który uzyskuje informacje o dane. Jest wynikiem szkoleniowe *transformatora*.
  - Można potraktować uczenia maszynowego *algorytm* jako narzędzie do szacowania, która uczy się na danych i uczenia maszynowego tworzy *modelu*.
- [*Funkcja prognozowania* ](#prediction-function) reprezentowane jako `PredictionEngine<TSrc, TDst>` klasy.
  - Funkcja prognozowania może być traktowany jako maszynie, która dotyczy transformatora jeden wiersz, takie jak w momencie prognozy.

## <a name="data"></a>Dane

W strukturze ML.NET dane są podobne do widoku SQL: Jest opóźnieniem ocenianą, informatycznych cursorable heterogenicznych, zestawu danych.

- Ma ona *schematu* (wystąpienie `ISchema` interfejsu) zawierający informacje dotyczące kolumny widoku danych.
  - Każda kolumna ma *nazwa*, *typu*i dowolnego zestawu *metadanych* skojarzonych z nim.
  - W kolumnie *metadanych* zawiera informacje, takie jak miejsce nazwy kolumny wektora i podobne. Metadane, sama jest reprezentowany jako innego jednowierszowym *danych* unikatowy dla każdej kolumny.
  - Widok danych to źródło *kursory*. Reakcji kursorów SQL: Kursor jest obiekt, który iteruje po danych jeden wiersz w czasie i przedstawia dostępne dane.
  - Oczywiście dane mogą mieć dowolną liczbę aktywnych kursorów nad nią zgodnie z potrzebami. Ponieważ dane są niezmienne, kursory są naprawdę niezależne.
  - Kursory zwykle dostęp tylko podzbiór kolumn: W celu zwiększenia wydajności w strukturze ML.NET oblicza tylko wartości kolumn, które są wymagane przez kursor.

## <a name="transformer"></a>Transformer

Transformer jest składnikiem, który pobiera dane, niektóre działa na nim i zwraca nowy przekształconych danych.

Większość transformatory w strukturze ML.NET mają tendencję do działania na jednym *kolumny wejściowej* w czasie i wygenerować *kolumnę wyjściową*. Na przykład `new HashTransformer("bar", "foo")` pobiera wartości z kolumny "foo", skróty je i umieszcza je w kolumnie "bar". 

Jest również typowe, że nazwy kolumn wejściowych i wyjściowych są takie same. W tym przypadku starego kolumny jest zastępowany nowym. Na przykład `new HashTransformer("foo")` pobiera wartości z kolumny "foo", skróty je i umieszcza je z powrotem do "foo". 

Wszelkie transformer, tworzy nowe dane widoku, kiedy `Transform` jest wywoływana. Należy pamiętać, że widoki danych są niezmienne.

Innym ważnym zagadnieniem jest fakt, że ponieważ opóźnieniem szacowania danych *transformatory są powolne zbyt*. Zasadniczo po wywołaniu

```csharp
var newData = transformer.Transform(oldData)
```

nie rzeczywiste obliczenia się nie dzieje. Tylko wtedy, gdy otrzymasz kursora z `newData` i rozpoczęcie używania wartość `newData` wywołania `transformer` logiki przekształcania (a nawet wówczas go tylko się dzieje w przypadku `transformer` jest zagrożona niezbędnych do wyprodukowania żądanej kolumny).

### <a name="transformer-chains"></a>Łańcuchy transformatora

Jest przydatne właściwość transformatora *kolejność stosowania transformatorów tworzyć jako kolejny transformatora*:

```csharp
var fullTransformer = transformer1.Append(transformer2).Append(transformer3);
```

Ta właściwość jest często używana w strukturze ML.NET: zazwyczaj uczonego modelu w strukturze ML.NET jest łańcuch transformatory, który jest na wszystkich intents i purposes, *transformatora*.

## <a name="data-reader"></a>Czytnik danych

Czytnik danych jest składnikiem strukturze ML.NET, aby utworzyć dane: Trwa wystąpienie `T` i zwraca dane z niej.

Interesujące właściwości, należy pamiętać, jest, czy można utworzyć czytnika danych, dołączając transformatora do istniejących czytnik danych. W ten sposób może mieć czytnik z działaniem przekształcania wbudowanymi:

```csharp
var newReader = reader.Append(transformer1).Append(transformer2)
```

Inny podobieństwa do transformatory jest fakt, że ponieważ opóźnieniem szacowania danych *czytniki są powolne*: nie (lub minimalny) rzeczywiste odczytu się dzieje, gdy wywołujesz `reader.Read()`: tylko gdy kursor jest wymagane w danych wynikowych jest Czytnik rozpocząć pracę.

## <a name="estimator"></a>Estimator

*Narzędzie do szacowania* jest obiektem, który uzyskuje informacje o dane. Jest wynikiem szkoleniowe *transformatora*.

W strukturze ML.NET, ta właściwość umożliwia tworzenie potoków uczenia, połączonych ze sobą różnych aplikacjom:

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

Co ważne właściwości aplikacjom jest fakt, że *aplikacjom to eager, nie z opóźnieniem*: każde wywołanie `Fit` powoduje uczenia się i tak się stanie, co jest potencjalnie czasochłonna operacja.

## <a name="prediction-function"></a>Funkcja prognozowania

Funkcja prognozowania może być traktowany jako składnik, który dotyczy transformatora jeden wiersz.

Po pobraniu modelu ( *transformatora* uczony albo za pośrednictwem `Fit()`, lub załadowany z innej lokalizacji), służy do tworzyć prognozy przy użyciu normalnych wywołania `model.Transform(data)`. Jednak jeśli używasz tego modelu w scenariuszu rzeczywistych często nie masz wiele przykładów do prognozowania na. Zamiast tego ma przykładem w czasie i musisz prognozowania aktualnych na nich od razu.

Oczywiście może to zmniejszyć do prognozowania usługi batch:

- Utwórz widok danych przy użyciu dokładnie jeden wiersz.
- Wywołaj `model.Transform(data)` do wyświetlania warunków prognozowanych danych.
- Pobieranie kursora nad dane wynikowe.
- Przejdź jeden krok kursora, aby przejść do wiersza pierwszą (i jedyną).
- Wyodrębnij przewidywane wartości z niej.

Poprzedni algorytm można zaimplementować przy użyciu [zrozumienie schematu](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md), za pomocą dwóch obiektów zdefiniowanych przez użytkownika `InputExample` i `OutputPrediction` w następujący sposób:

```csharp
var inputData = mlContext.Data.ReadFromEnumerable(new InputExample[] { example });
var outputData = model.Transform(inputData);
var output = mlContext.CreateEnumerable<OutputPrediction>(outputData,reuseRowObject:false).First();
```

Ale to jest skomplikowana względem i ponosi koszty wydajności. Zamiast tego obiektu funkcji prognozowania wykonuje takie same pracy, ale szybciej i łatwiej za pomocą metody rozszerzenia `CreatePredictionEngine`:

```csharp
var predictionEngine = model.CreatePredictionEngine<InputExample,OutputPrediction>(mlContext);
var prediction = predictionEngine.Predict(example);
```

Funkcja prognozowania *nie wielobieżnej / wątkowo*. Jeśli chcesz przeprowadzić prognoz jednocześnie z wielu wątków, musisz mieć funkcji prognozowania na wątek.
