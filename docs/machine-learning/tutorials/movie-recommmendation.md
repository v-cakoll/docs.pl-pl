---
title: Użyj strukturze ML.NET w scenariuszu zaleceń filmu
description: Dowiedz się, jak na potrzeby strukturze ML.NET w scenariuszu rekomendacji zaleca się filmy dla użytkowników.
author: briacht
ms.author: johalex
ms.date: 03/08/2019
ms.custom: mvc
ms.topic: tutorial
ms.openlocfilehash: 9b7ef12591e0a231b633f461547ec0eeaec1a530
ms.sourcegitcommit: 77854e8704b9689b73103d691db34d71c2bf1dad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2019
ms.locfileid: "58308064"
---
# <a name="tutorial-create-a-movie-recommender-with-mlnet"></a>Samouczek: Utwórz polecania filmów za pomocą platformy ML.NET

Ten przykładowy samouczek przedstawia tworzenie polecania filmu, za pośrednictwem używany aplikację konsoli .NET Core za pomocą strukturze ML.NET C# w programie Visual Studio 2017.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Wybieranie algorytmu uczenia maszynowego
> * Przygotowanie i ładowania danych
> * Tworzenie i uczenie modelu
> * Ocena modelu
> * Wdrażanie i korzystanie z modelu

> [!NOTE]
> W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie. Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Obecnie używasz tego samouczka, a powiązane próbki **strukturze ML.NET wersji 0,11**. Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repozytorium.

## <a name="machine-learning-workflow"></a>Maszyny uczenie się przepływu pracy
Poniższe kroki użyje do wykonywania zadań, a także inne zadanie w strukturze ML.NET:

1. [Załaduj dane](#load-your-data)
2. [Tworzenie i uczenie modelu](#build-and-train-your-model)
3. [Ocena modelu](#evaluate-your-model)
4. [Użyj modelu](#use-your-model)

## <a name="prerequisites"></a>Wymagania wstępne

* [Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".

## <a name="select-the-appropriate-machine-learning-task"></a>Wybierz zadanie uczenia odpowiedniej maszyny

Istnieje kilka sposobów podejście problemy zalecenie, takie jak polecanie listy filmów lub zalecania listę powiązanych z nimi produktów, ale w tym przypadku będzie przewidywania jakie oceny (1-5) użytkownika będą dawać do konkretnego filmu i zaleca się ten film, jeśli jest przekracza określoną wartość progową (wyższa ocenę, tym wyższe prawdopodobieństwo użytkownika liking konkretnego filmu).

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

### <a name="create-a-project"></a>Tworzenie projektu

1. Otwórz program Visual Studio 2017. Wybierz **pliku** > **New** > **projektu** z paska menu. W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła następuje **platformy .NET Core** węzła. Następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonu projektu. W **nazwa** pole tekstowe, wpisz "MovieRecommender", a następnie wybierz **OK** przycisku.

2. Utwórz katalog o nazwie *danych* w projekcie do przechowywania zestawu danych:

    W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj** > **nowy Folder**. Wpisz "Dane", a następnie naciśnij klawisz Enter.

3. Zainstaluj **Microsoft.ML** i **Microsoft.ML.Recommender** pakiety NuGet:

    W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz opcję **Przeglądaj** kartę, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku. Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych. Powtórz te kroki dla **Microsoft.ML.Recommender**.

  > [!NOTE]
  > W tym samouczku **Microsoft.ML v0.11.0** i **Microsoft.ML.Recommender v0.11.0**.
    
4. Dodaj następujący kod `using` instrukcji w górnej części Twojej *Program.cs* pliku:
    
    [!code-csharp[UsingStatements](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a>Pobieranie danych

1. Pobierz dwa zestawy danych i zapisywanie ich *danych* wcześniej utworzony folder:

*   Kliknij prawym przyciskiem myszy [ *zalecenie klasyfikacje — train.csv* ](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) i wybierz pozycję "Zapisz jako łącza (lub docelowego)..."
*   Kliknij prawym przyciskiem myszy [ *zalecenie klasyfikacje — test.csv* ](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) i wybierz pozycję "Zapisz jako łącza (lub docelowego)..."

     Upewnij się, albo zapisać \*plików CSV *danych* folderu lub po jego zapisaniu innym miejscu, Przenieś \*plików CSV *danych* folderu.

2. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy każdy z \*plików CSV, a następnie wybierz **właściwości**. W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.

   ![Kopiuj Jeśli nowszy w programie VS](./media/movie-recommendation/copytoout.gif)

## <a name="load-your-data"></a>Załaduj dane

Pierwszym krokiem w procesie strukturze ML.NET jest przygotowanie i obciążenia sieci szkolenia i modelu danych testowych.

Dane oceny zalecenie jest podzielony na `Train` i `Test` zestawów danych. `Train` Danych służy do dopasowania modelu. `Test` Dane są używane do prognozowania za pomocą uczonego modelu i ocena wydajności modelu. Jest często mają 80/20, Podziel się `Train` i `Test` danych.

Poniżej znajduje się podgląd danych z usługi \*plików CSV:

![Podgląd danych](./media/movie-recommendation/csv-dataset-preview.png)

W \*plików CSV znajdują się cztery kolumny:

* `userId`
* `movieId`
* `rating`
* `timestamp`

W usłudze machine learning, są nazywane kolumn, które są używane do prognozowania [funkcji](../resources/glossary.md#feature), i nosi nazwę kolumny z prognozowania zwracane [etykiety](../resources/glossary.md#label).

Chcesz przewidzieć klasyfikacji filmów, więc kolumny ocenę `Label`. Pozostałe trzy kolumny `userId`, `movieId`, i `timestamp` wyświetlane są wszystkie `Features` używać do prognozowania `Label`.

| Funkcje      | Etykieta         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId `      |               |
| `timestamp`     |               |

To Ty decydujesz o tym, które `Features` są używane do prognozowania `Label`. Można również użyć metod, takich jak [znaczenie permutacji funkcji](../how-to-guides/determine-global-feature-importance-in-model.md) ułatwiające wybranie najlepszych `Features`.

W takim przypadku można wyeliminować `timestamp` jako kolumny `Feature` ponieważ sygnatura czasowa naprawdę wpływa na sposób użytkownik ocenia danego filmu, a zatem nie przyczyni się do wprowadzania dokładniejszych prognoz:

| Funkcje      | Etykieta         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId `      |               |

Następnie zdefiniuj strukturę danych wejściowych klasy.

Dodaj nową klasę do projektu:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj > Nowy element**.

2. W **okno dialogowe Dodaj nowy element**, wybierz opcję **klasy** i zmień **nazwa** pole *MovieRatingData.cs*. Następnie wybierz **Dodaj** przycisku.

*MovieRatingData.cs* plik zostanie otwarty w edytorze kodu. Dodaj następujący kod `using` instrukcji na górze *MovieRatingData.cs*:

```csharp
using Microsoft.ML.Data;
```

Utwórz klasę o nazwie `MovieRating` , usuwając istniejącą definicję klasy i dodając następujący kod w *MovieRatingData.cs*:

[!code-csharp[MovieRatingClass](../../../samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

`MovieRating` Określa klasę danych wejściowych. [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) atrybut określa, które kolumny (według indeksu kolumny) w zestawie danych, które powinny być załadowane. `userId` i `movieId` kolumny są usługi `Features` (dane wejściowe zostanie nadana model do przewidywania `Label`), i kolumna Ocena jest `Label` czy będzie przewidzieć (dane wyjściowe modelu).

Tworzenie innej klasy `MovieRatingPrediction`, do reprezentowania wyników, dodając następujący kod po `MovieRating` klasy w *MovieRatingData.cs*:

[!code-csharp[PredictionClass](../../../samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

W *Program.cs*, Zastąp `Console.WriteLine("Hello World!")` następujący kod wewnątrz `Main()`:

[!code-csharp[MLContext](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MLContext "Add MLContext")]

[Klasy MLContext](xref:Microsoft.ML.MLContext) to punkt początkowy dla wszystkich operacji w strukturze ML.NET oraz inicjowanie `mlContext` tworzy nowe środowisko strukturze ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Przypomina, model `DBContext` platformy Entity Framework.

Po `Main()`, utworzyć metodę o nazwie `LoadData()`:
```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{


}
```

> [!NOTE]
> Ta metoda zapewni błąd do momentu dodania instrukcji return w poniższych krokach.

Inicjowanie zmiennych ścieżki danych, Załaduj dane z plików *.csv i zwróć `Train` i `Test` dane jako `IDataView` obiektów przez dodanie poniższego jako następnego wiersza kodu w `LoadData()`:

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadData "Load data from data paths")]

Dane w strukturze ML.NET jest reprezentowany jako [klasy IDataView](xref:Microsoft.Data.DataView.IDataView). `IDataView` jest elastyczny i wydajny sposób opisu danych tabelarycznych (liczbowe i tekstowe). Dane można załadować z pliku tekstowego lub w czasie rzeczywistym (na przykład SQL bazy danych lub dziennika plików) do `IDataView` obiektu.

[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczytuje w pliku. Pobiera zmienne ścieżek danych i zwraca `IDataView`. W tym przypadku podaj ścieżkę dla Twojego `Test` i `Train` pliki i wskazać nagłówka pliku tekstowego (tak, aby go prawidłowo używać nazwy kolumn) i przecinkami danych znak separatora (domyślnym separatorem jest karta).

Dodaj następujący kod jako następnych dwóch wierszach kodu w `Main()` metodę do wywołania usługi `LoadData()` metody i zwrócenie `Train` i `Test` danych:

[!code-csharp[LoadDataMain](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadDataMain "Add LoadData method to Main")]


## <a name="build-and-train-your-model"></a>Tworzenie i uczenie modelu

Istnieją trzy główne pojęcia w strukturze ML.NET: [Dane](../basic-concepts-model-training-in-mldotnet.md#data), [transformatory](../basic-concepts-model-training-in-mldotnet.md#transformer), i [aplikacjom](../basic-concepts-model-training-in-mldotnet.md#estimator).

Uczenie maszynowe szkolenia algorytmów wymaganych danych w określonym formacie. `Transformers` są używane do przekształcania danych tabelarycznych na format zgodny.

![Transformer obrazu](./media/movie-recommendation/transformer.png)

Możesz utworzyć `Transformers` w strukturze ML.NET, tworząc `Estimators`. `Estimators` podjęcia w obszarach danych i zwrócenia `Transformers`.

![Narzędzie do szacowania obrazu](./media/movie-recommendation/estimator.png)

Zalecenie uczenie algorytmu, będą używane na potrzeby szkolenia modelu jest przykładem `Estimator`.

Tworzenie `Estimator` następujące czynności:

Tworzenie `BuildAndTrainModel()` metody tuż za `LoadData()` metody, używając następującego kodu:
```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{


}
```
> [!NOTE]
> Ta metoda zapewni błąd do momentu dodania instrukcji return w poniższych krokach.

Zdefiniować przekształceń danych, dodając następujący kod do `BuildAndTrainModel()`:
   
[!code-csharp[DataTransformations](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#DataTransformations "Define data transformations")]

Ponieważ `userId` i `movieId` reprezentują użytkowników i tytułów filmów, nie rzeczywiste wartości, użyj [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) metoda przekształcania każdego `userId` i każdy `movieId` do klucza typu liczbowego `Feature`kolumny (formacie akceptowanym przez algorytmy zalecenie) i dodaj je jako nowe kolumny zestawu danych:

| userId | movieId | Etykieta | userIdEncoded | movieIdEncoded |
| ------------- |:-------------:| -----:|-----:|-----:|
| 1 | 1 | 4 | userKey1 | movieKey1 |
| 1 | 3 | 4 | userKey1 | movieKey2 |
| 1 | 6 | 4 | userKey1 | movieKey3 |


Wybieranie algorytmu uczenia maszynowego, a następnie dołącza je do definicji przekształcania danych, dodając następujące jako następnego wiersza kodu w `BuildAndTrainModel()`:

[!code-csharp[AddAlgorithm](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#AddAlgorithm "Add the training algorithm with options")]

[MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) jest algorytm szkolenia zalecenia.  [Macierz Factorization](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) jest typowym podejściem do zalecenia, gdy masz dane, w jaki użytkownicy, które oceniły produktów w przeszłości jest tak w przypadku zestawów danych w ramach tego samouczka. Istnieją inne algorytmy zalecenie używane w przypadku różnych dostępnych danych (zobacz [inne algorytmy zalecenie](#other-recommendation-algorithms) sekcji poniżej, aby dowiedzieć się więcej). 

W tym przypadku `Matrix Factorization` algorytm używa metodę o nazwie "współpracy filtering", która zakłada się, że jeśli 1 użytkownik ma ten sam opinia jako 2 użytkownika dotyczących niektórych problemów, a następnie 1 użytkownika jest bardziej prawdopodobne, że ten sam sposób jak 2 użytkowników o innym problemem.

Na przykład jeśli użytkownik 1 i 2 użytkownika podobnie szybkości filmy, następnie 2 użytkownika jest bardziej prawdopodobne cieszyć się filmu 1 użytkownik ma obserwowane i o wysokiej:

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| Użytkownik 1 | Monitorowane i zbędne filmu | Monitorowane i zbędne filmu | Monitorowane i zbędne filmu |
| Użytkownik 2 | Monitorowane i zbędne filmu | Monitorowane i zbędne filmu | Nie ma obserwowane--zaleca się filmu |

`Matrix Factorization` Trainer ma kilka [opcje](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), której możesz przeczytać więcej na temat w [hiperparametrów algorytm](#algorithm-hyperparameters) poniższej sekcji.

Dopasuj do modelu `Train` danych i zwracają uczonego modelu przez dodanie poniższego jako następnego wiersza kodu w `BuildAndTrainModel()` metody:

[!code-csharp[FitModel](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#FitModel "Call the Fit method and return back the trained model")]

[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.Data.DataView.IDataView,Microsoft.Data.DataView.IDataView%29) metoda szkolenie modeli modelu za pomocą podanego szkolenia zestawu danych. Technicznie rzecz biorąc, wykonuje `Estimator` definicje, przekształcanie danych i stosując, szkolenia i zwraca kopię trenowanego modelu, który jest `Transformer`.

Dodaj następujący kod jako następnego wiersza kodu w `Main()` metodę do wywołania usługi `BuildAndTrainModel()` metody i zwrócenie uczonego modelu:

[!code-csharp[BuildTrainModelMain](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a>Ocena modelu

Gdy masz uczony model, korzystanie z Twoich danych testu do oceny, jak działa model. 

Tworzenie `EvaluateModel()` metody tuż za `BuildAndTrainModel()` metody, używając następującego kodu:
```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{


}
```

Przekształcanie `Test` danych przez dodanie poniższego kodu `EvaluateModel()`: [!code-csharp[Transform](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Transform "Transform the test data")]

[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda wykonuje prognozy dla wielu podać wiersze danych wejściowych zestawu testów.

Ocena modelu przez dodanie poniższego jako następnego wiersza kodu w `EvaluateModel()` metody:

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

Po utworzeniu prognozowania ustawiona, [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) metoda ocenia modelu, który porównuje przewidywane wartości z rzeczywistych `Labels` w testowego zestawu danych i zwraca metryki dotyczące jak działa model.

Drukuj metryk oceny do konsoli, dodając następujące jako następnego wiersza kodu w `EvaluateModel()` metody:

[!code-csharp[PrintMetrics](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintMetrics "Print the evaluation metrics")]

Dodaj następujący kod jako następnego wiersza kodu w `Main()` metodę do wywołania usługi `EvaluateModel()` metody:

[!code-csharp[EvaluateModelMain](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#EvaluateModelMain "Add EvaluateModel method in Main")]

Do tej pory dane wyjściowe powinny wyglądać podobnie do następującego tekstu:

```console
=============== Training the model ===============
iter      tr_rmse          obj
   0       1.5403   3.1262e+05
   1       0.9221   1.6030e+05
   2       0.8687   1.5046e+05
   3       0.8416   1.4584e+05
   4       0.8142   1.4209e+05
   5       0.7849   1.3907e+05
   6       0.7544   1.3594e+05
   7       0.7266   1.3361e+05
   8       0.6987   1.3110e+05
   9       0.6751   1.2948e+05
  10       0.6530   1.2766e+05
  11       0.6350   1.2644e+05
  12       0.6197   1.2541e+05
  13       0.6067   1.2470e+05
  14       0.5953   1.2382e+05
  15       0.5871   1.2342e+05
  16       0.5781   1.2279e+05
  17       0.5713   1.2240e+05
  18       0.5660   1.2230e+05
  19       0.5592   1.2179e+05
=============== Evaluating the model ===============
Rms: 0.994051469730769
RSquared: 0.412556298844873
```

W poniższych danych wyjściowych istnieją 20 iteracjach. W każdej iteracji miary błąd zmniejsza i zbieżna dla wartości bliżej i bliżej 0.

`root of mean squared error` (Usługi RMS lub RMSE) jest często używane do mierzenia różnice między wartości prognozowane przez model i wartościami odczytanymi w zestawie danych testowych. Z technicznego punktu widzenia jest pierwiastek kwadratowy ze średniej kwadratów błędów. Chcesz, aby Twój wynik RMSE sposób maksymalnie zbliżony 1, jak to możliwe.

`R Squared` jest wartością procentową zmiany w przewidywane wartości wyjaśnione przy użyciu modelu. Jest wartością z zakresu od 0 do 1, a im bliżej wartość to 0, tym lepsze model jest.

## <a name="use-your-model"></a>Użyj modelu

Teraz można użyć uczonego modelu do prognozowania na nowych danych.

Tworzenie `UseModelForSinglePrediction()` metody tuż za `EvaluateModel()` metody, używając następującego kodu:
```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{


}
```

Użyj `PredictionEngine` do prognozowania tę klasyfikację, dodając następujący kod do `UseModelForSinglePrediction()`:

[!code-csharp[PredictionEngine](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PredictionEngine "Create Prediction Engine")]

[Klasy PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest wygoda interfejsu API, dzięki czemu można przekazać pojedyncze wystąpienie danych, a następnie wykonaj prognozę na to pojedyncze wystąpienie danych.

Utwórz wystąpienie obiektu `MovieRating` o nazwie `testInput` i przekaż go do aparatu prognozowania, dodając następujące jako z następującymi wierszami kodu w `UseModelForSinglePrediction()` metody:

[!code-csharp[MakeSinglePrediction](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) funkcja sprawia, że prognozę na pojedynczej kolumny danych.

Następnie można użyć `Score`, lub przewidywane oceny, ustalenie, czy polecisz film z movieId 10 użytkownika 6. Wyższe `Score`, tym większe prawdopodobieństwo użytkownika liking konkretnego filmu. W tym przypadku Załóżmy, że zalecane jest użycie filmów z oceną przewidywane > 3.5.

Aby wydrukować wyniki, należy dodać następujące porty jako dalej wiersze kodu `UseModelForSinglePrediction()` metody:

[!code-csharp[PrintResults](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintResults "Print the recommendation prediction results")]

Dodaj następujący kod jako następnego wiersza kodu w `Main()` metodę do wywołania usługi `UseModelForSinglePrediction()` metody:

[!code-csharp[UseModelMain](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UseModelMain "Add UseModelForSinglePrediction method in Main")]

Dane wyjściowe tej metody powinien wyglądać podobnie do następującego tekstu:

```console
=============== Making a prediction ===============
Movie 10 is recommended for user 6
```

### <a name="save-your-model"></a>Zapisz model
Aby użyć modelu do prognozowania w aplikacji użytkownika końcowego, należy najpierw zapisać modelu.

Tworzenie `SaveModel()` metody tuż za `UseModelForSinglePrediction()` metody, używając następującego kodu:
```csharp
public static void SaveModel(MLContext mlContext, ITransformer model)
{


}
```

Zapisania trenowanego modelu, dodając następujący kod w `SaveModel()` metody:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModel "Save the model to a zip file")]

Ta metoda zapisuje uczonego modelu do pliku zip (w folderze "Dane"), które następnie mogą być używane w innych aplikacjach platformy .NET do przewidywania przyszłych zdarzeń.

Dodaj następujący kod jako następnego wiersza kodu w `Main()` metodę do wywołania usługi `SaveModel()` metody:

[!code-csharp[SaveModelMain](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a>Użyj zapisanych modelu
Po zapisaniu uczonego modelu może zużywać model w różnych środowiskach (zobacz ["Poradnik"](../how-to-guides/consuming-model-ml-net.md) dowiesz się, jak do obsługi operacji modelu uczenia maszynowego uczonego w aplikacjach).

## <a name="results"></a>Wyniki

Po wykonaniu powyższych kroków, uruchom aplikację konsoli (Ctrl + F5). Wyniki z jednej prognozowania powyżej powinny być podobne do następujących. Może zostać wyświetlony, ostrzeżenia i przetwarzanie komunikatów, ale te komunikaty zostały usunięte z następujące wyniki dla przejrzystości.

```console
=============== Training the model ===============
iter      tr_rmse          obj
   0       1.5382   3.1213e+05
   1       0.9223   1.6051e+05
   2       0.8691   1.5050e+05
   3       0.8413   1.4576e+05
   4       0.8145   1.4208e+05
   5       0.7848   1.3895e+05
   6       0.7552   1.3613e+05
   7       0.7259   1.3357e+05
   8       0.6987   1.3121e+05
   9       0.6747   1.2949e+05
  10       0.6533   1.2766e+05
  11       0.6353   1.2636e+05
  12       0.6209   1.2561e+05
  13       0.6072   1.2462e+05
  14       0.5965   1.2394e+05
  15       0.5868   1.2352e+05
  16       0.5782   1.2279e+05
  17       0.5713   1.2227e+05
  18       0.5637   1.2190e+05
  19       0.5604   1.2178e+05
=============== Evaluating the model ===============
Rms: 0.977175077487166
RSquared: 0.43233349213192
=============== Making a prediction ===============
Movie 10 is recommended for user 6
=============== Saving the model to a file ===============
```

Gratulacje! Usługi machine learning model polecanie filmów teraz zostały pomyślnie skompilowane. Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repozytorium.

## <a name="improve-your-model"></a>Poprawa modelu

Istnieje kilka sposobów, że może poprawić wydajność modelu, dzięki czemu można uzyskać dokładniejszych prognoz.

### <a name="data"></a>Dane 

Dodawanie większej ilości danych szkoleniowych, który ma wystarczającej liczby próbek dla każdego użytkownika i identyfikator filmu może zwiększyć jakość modelu zalecenia.

[Krzyżowe sprawdzanie poprawności](../how-to-guides/train-cross-validation-ml-net.md) to technika, który losowo oceniania modeli są rozróżniane danych na podzestawy (zamiast wyodrębniania się dane testowe z zestawu danych, jak zrobiono to w ramach tego samouczka) i przyjmuje niektórych grup nauczenia danych, a niektóre z tych grup jako test dane. Tej metody przewyższa przekształcania stosowane, dzięki czemu train-test podziału pod względem jakości modelu.

### <a name="features"></a>Funkcje

W tym samouczku używasz tylko trzy `Features` (`user id`, `movie id`, i `rating`) są dostarczane przez zestaw danych. 

Gdy jest to dobry początek, w rzeczywistości możesz chcieć dodać inne atrybuty lub `Features` (na przykład, wiek, płeć, geolokalizacja itp.), jeśli są one uwzględnione w zestawie danych. Dodawanie istotniejsze `Features` może zwiększyć wydajność modelu zalecenia. 

Jeśli nie wiesz o tym, które `Features` może być najbardziej istotne dla zadania machine learning, można również skorzystać z funkcji wkład obliczeń (FCC) i [znaczenie permutacji funkcji](../how-to-guides/determine-global-feature-importance-in-model.md), który zapewnia strukturze ML.NET Odkryj najbardziej duży wpływ `Features`.

### <a name="algorithm-hyperparameters"></a>Algorytm hiperparametrów

Strukturze ML.NET zapewnia dobre domyślne szkolenia algorytmów, jednocześnie można dodatkowo dostrajania wydajności przez zmianę tego algorytmu [hiperparametrów](../resources/glossary.md#hyperparameter).

Aby uzyskać `Matrix Factorization`, można eksperymentować hiperparametrów takich jak [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) i [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) aby zobaczyć, jeśli zapewnia to lepsze wyniki.

Na przykład w tym samouczku algorytm są następujące opcje:

```csharp
var options = new MatrixFactorizationTrainer.Options
{
    MatrixColumnIndexColumnName = "userIdEncoded",
    MatrixRowIndexColumnName = "movieIdEncoded", 
    LabelColumnName = "Label",
    NumberOfIterations = 20,
    ApproximationRank = 100
};
```

### <a name="other-recommendation-algorithms"></a>Inne algorytmy zalecenia
Algorytm factorization macierzy za pomocą filtrowania z wykorzystaniem współpracy jest tylko jedno z podejść do wykonywania rekomendacji filmów. W wielu przypadkach może nie ma dostępnych danych oceny i mieć tylko historii film dostępny od użytkowników. W innych przypadkach może mieć więcej niż tylko przez użytkownika klasyfikacji danych.

| Algorytm       | Scenariusz           | Przykład  |
| ------------- |:-------------:| -----:|
| Factorization macierzy jednej klasy | Użyj tego, jeśli masz tylko identyfikator użytkownika i movieId. Ten styl zalecenie opiera się na scenariuszu wspólnej zakupu lub produktów często kupowane razem, co oznacza, że będzie zalecamy klientom zestaw produktów na podstawie własnych zakupu historii zamówień. | [> wypróbuj działanie rozwiązania](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| Pole pamiętać Factorization maszyn | Użyj tego zaleceń, gdy masz większą liczbą funkcji poza userId, identyfikator produktu i klasyfikacji (na przykład opis produktu lub cena produktu). Ta metoda używa również wspólne podejście filtrowania. | [> wypróbuj działanie rozwiązania](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a>Nowy scenariusz użytkownika
Jeden powszechny problem związany z filtrowania z wykorzystaniem współpracy jest problem zimnego, czyli w przypadku nowego użytkownika bez poprzedniego danych do rysowania wniosków z. To często problemu zadając nowych użytkowników, aby utworzyć profil i, na przykład filmy szybkość ich przejrzane w przeszłości. Gdy ta metoda powoduje niektórych obciążeń na użytkownika, zawiera dane wyjścia dla nowych użytkowników o Brak historii klasyfikacji.

## <a name="resources"></a>Zasoby
Dane używane w tym samouczku jest tworzony na podstawie [MovieLens Dataset](http://files.grouplens.org/datasets/movielens/).

## <a name="next-steps"></a>Następne kroki
W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
> * Wybieranie algorytmu uczenia maszynowego
> * Przygotowanie i ładowania danych
> * Tworzenie i uczenie modelu
> * Ocena modelu
> * Wdrażanie i korzystanie z modelu

Przejdź do następnego samouczka, aby dowiedzieć się więcej
> [!div class="nextstepaction"]
> [Analiza tonacji](sentiment-analysis.md)
