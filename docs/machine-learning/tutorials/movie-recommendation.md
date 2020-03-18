---
title: 'Samouczek: Tworzenie rekomendacji filmu - faktorinizacja matrycy'
description: W tym samouczku pokazano, jak utworzyć program polecający film z ML.NET w aplikacji konsoli .NET Core. Kroki są używane c# i Visual Studio 2019.
author: briacht
ms.date: 09/30/2019
ms.custom: mvc, title-hack-0516
ms.topic: tutorial
ms.openlocfilehash: a221289d0c232863f03a275c26dce835f2878bf7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241107"
---
# <a name="tutorial-build-a-movie-recommender-using-matrix-factorization-with-mlnet"></a>Samouczek: Tworzenie rekomendacji filmów przy użyciu faktoryzacji macierzy z ML.NET

W tym samouczku pokazano, jak utworzyć program polecający film z ML.NET w aplikacji konsoli .NET Core. Kroki są używane c# i Visual Studio 2019.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> * Wybierz algorytm uczenia maszynowego
> * Przygotowywanie i ładowanie danych
> * Budowanie i szkolenie modelu
> * Ocena modelu
> * Wdrażanie modelu i korzystanie z go

Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation)

## <a name="machine-learning-workflow"></a>Przepływ pracy uczenia maszynowego

Aby wykonać zadanie, należy wykonać następujące czynności, a także wszelkie inne zadania ML.NET:

1. [Załaduj swoje dane](#load-your-data)
2. [Buduj i trenuj swój model](#build-and-train-your-model)
3. [Ocenianie modelu](#evaluate-your-model)
4. [Korzystanie z modelu](#use-your-model)

## <a name="prerequisites"></a>Wymagania wstępne

* [Visual Studio 2017 w wersji 15.6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem ".NET Core programistorna wieloplatformowa".

## <a name="select-the-appropriate-machine-learning-task"></a>Wybierz odpowiednie zadanie uczenia maszynowego

Istnieje kilka sposobów podejścia do problemów z rekomendacjami, takich jak zalecanie listy filmów lub polecanie listy powiązanych produktów, ale w tym przypadku można przewidzieć, jaką ocenę (1-5) użytkownik da konkretnemu filmowi i zalecić ten film, jeśli jest wyższy niż określony próg (im wyższa ocena, tym większe prawdopodobieństwo, że użytkownik polubi dany film).

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

### <a name="create-a-project"></a>Tworzenie projektu

1. Otwórz program Visual Studio 2017. Wybierz **pozycję Plik** > **nowy** > **projekt** z paska menu. W oknie dialogowym **Nowy projekt** wybierz węzeł **Visual C#,** po którym następuje węzeł **.NET Core.** Następnie wybierz szablon projektu **aplikacji konsoli (.NET Core).** W polu tekstowym **Nazwa** wpisz "MovieRecommender", a następnie wybierz przycisk **OK.**

2. Utwórz katalog o nazwie *Dane* w projekcie, aby przechowywać zestaw danych:

    W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj** > **nowy folder**. Wpisz "Dane" i naciśnij klawisz Enter.

3. Zainstaluj **pakiety Microsoft.ML** i **Microsoft.ML.Recommender** NuGet:

    W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**. Wybierz "nuget.org" jako źródło pakietu, wybierz kartę **Przeglądaj,** wyszukaj **Microsoft.ML,** wybierz pakiet na liście i wybierz przycisk **Zainstaluj.** Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z warunkami licencyjnymi dla wymienionych pakietów. Powtórz te kroki dla **pliku Microsoft.ML.Recommender**.

4. Dodaj następujące `using` instrukcje u góry pliku *Program.cs:*

    [!code-csharp[UsingStatements](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a>Pobieranie danych

1. Pobierz dwa zestawy danych i zapisz je w folderze *Data,* który został wcześniej utworzony:

   * Kliknij prawym przyciskiem myszy [*rekomendację-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) i wybierz opcję "Zapisz link (lub cel) jako..."
   * Kliknij prawym przyciskiem myszy [*rekomendację-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) i wybierz opcję "Zapisz link (lub cel) jako..."

     Upewnij się, że \*pliki csv są zapisywane w folderze *Dane* lub \*po zapisaniu go w innym miejscu, przenieś pliki csv do folderu *Dane.*

2. W Eksploratorze rozwiązań \*kliknij prawym przyciskiem myszy każdy z plików csv i wybierz **polecenie Właściwości**. W obszarze **Zaawansowane**zmień wartość **kopiuj do katalogu wyjściowego,** aby **skopiować, jeśli nowsza**.

   ![GIF użytkownika wybierającego kopię, jeśli jest nowsza w wersji VS.](./media/movie-recommendation/copy-to-output-if-newer.gif)

## <a name="load-your-data"></a>Załaduj swoje dane

Pierwszym krokiem w procesie ML.NET jest przygotowanie i załadowanie modelu szkolenia i testowania danych.

Dane klasyfikacji rekomendacji są `Train` dzielone na `Test` zestawy danych. Dane `Train` są używane do dopasowania modelu. Dane `Test` są używane do prognozowania z uczonego modelu i oceny wydajności modelu. Często dzieli się z nim dane i `Train` `Test` dane o 80/20.

Poniżej znajduje się podgląd danych \*z plików csv:

![Zrzut ekranu przedstawiający podgląd zestawu danych CVS.](./media/movie-recommendation/csv-file-dataset-preview.png)

W \*plikach csv znajdują się cztery kolumny:

* `userId`
* `movieId`
* `rating`
* `timestamp`

W uczeniu maszynowym kolumny, które są używane do przewidywania są nazywane [funkcje,](../resources/glossary.md#feature)a kolumna z zwróconym przewidywanie nazywa [label](../resources/glossary.md#label).

Chcesz przewidzieć oceny filmów, więc kolumna `Label`klasyfikacji jest . Pozostałe trzy kolumny `userId` `movieId`, `timestamp` , `Features` i wszystkie `Label`są używane do przewidywania .

| Funkcje      | Label         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |
| `timestamp`     |               |

To do Ciebie, aby `Features` zdecydować, które `Label`są używane do przewidywania . Można również użyć metod, takich jak [znaczenie funkcji permutacji,](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md) aby ułatwić wybór najlepszych `Features`.

W takim przypadku należy `timestamp` wyeliminować kolumnę `Feature` jako sygnatury czasowej, ponieważ tak naprawdę nie wpływa na sposób oceniania danego filmu przez użytkownika, a tym samym nie przyczynia się do dokładniejszego przewidywania:

| Funkcje      | Label         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |

Następnie należy zdefiniować strukturę danych dla klasy wejściowej.

Dodaj nową klasę do projektu:

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj > nowy element**.

2. W **oknie dialogowym Dodawanie nowego elementu**wybierz pozycję **Klasa** i zmień pole **Nazwa** na *MovieRatingData.cs*. Następnie wybierz przycisk **Dodaj.**

Plik *MovieRatingData.cs* zostanie otwarty w edytorze kodu. Dodaj następującą `using` instrukcję na górze *MovieRatingData.cs:*

```csharp
using Microsoft.ML.Data;
```

Utwórz klasę `MovieRating` o nazwie, usuwając istniejącą definicję klasy i dodając następujący kod w *MovieRatingData.cs:*

[!code-csharp[MovieRatingClass](~/samples/snippets/machine-learning/MovieRecommendation/csharp/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

`MovieRating`określa klasę danych wejściowych. [Atrybut LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) określa, które kolumny (według indeksu kolumn) w zestawie danych powinny być ładowane. Kolumny `userId` `movieId` i kolumny `Features` są twoje (dane wejściowe, które `Label`dajesz modelowi `Label` do przewidywania), a kolumna klasyfikacji jest kolumną, którą można przewidzieć (dane wyjściowe modelu).

Utwórz inną `MovieRatingPrediction`klasę, aby przedstawić przewidywane wyniki, `MovieRating` dodając następujący kod po klasie w *MovieRatingData.cs:*

[!code-csharp[PredictionClass](~/samples/snippets/machine-learning/MovieRecommendation/csharp/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

W *Program.cs,* `Console.WriteLine("Hello World!")` zastąp `Main()`następujący kod wewnątrz:

[!code-csharp[MLContext](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#MLContext "Add MLContext")]

[Klasa MLContext](xref:Microsoft.ML.MLContext) jest punktem wyjścia dla wszystkich operacji `mlContext` ML.NET, a inicjowanie tworzy nowe środowisko ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest to podobne, koncepcyjnie, `DBContext` do w ramach jednostki.

Po `Main()`, utwórz `LoadData()`metodę o nazwie:

```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{

}
```

> [!NOTE]
> Ta metoda daje błąd, dopóki nie dodasz return instrukcji w poniższych krokach.

Inicjuj zmienne ścieżki danych, \*ładuj dane z `Train` plików `Test` csv i zwracaj dane jako `IDataView` obiekty, dodając następujący wiersz kodu w: `LoadData()`

[!code-csharp[LoadData](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#LoadData "Load data from data paths")]

Dane w ML.NET jest reprezentowana jako [klasa IDataView](xref:Microsoft.ML.IDataView). `IDataView`to elastyczny i skuteczny sposób opisywania danych tabelarycznych (numerycznych i tekstowych). Dane mogą być ładowane z pliku tekstowego lub w czasie rzeczywistym `IDataView` (na przykład bazy danych SQL lub plików dziennika) do obiektu.

[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczyty w pliku. Przyjmuje zmienne ścieżki danych i `IDataView`zwraca . W takim przypadku należy podać `Test` ścieżkę dla plików i `Train` plików i wskazać zarówno nagłówek pliku tekstowego (aby można było poprawnie używać nazw kolumn), jak i separator danych zdinnymi (domyślnym separatorem jest karta).

Dodaj następujący kod `Main()` w metodzie, aby wywołać metodę `LoadData()` i zwrócić `Train` i `Test` dane:

[!code-csharp[LoadDataMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#LoadDataMain "Add LoadData method to Main")]

## <a name="build-and-train-your-model"></a>Buduj i trenuj swój model

Istnieją trzy główne pojęcia w ML.NET: [Dane](../resources/glossary.md#data), [Transformatory](../resources/glossary.md#transformer)i [Estymatory](../resources/glossary.md#estimator).

Algorytmy szkolenia uczenia maszynowego wymagają danych w określonym formacie. `Transformers`są używane do przekształcania danych tabelarycznych do zgodnego formatu.

![Diagram przepływu danych Transformer.](./media/movie-recommendation/data-transformer-transformed.png)

Tworzenie `Transformers` w ML.NET `Estimators`przez utworzenie . `Estimators`danych i zwrotu `Transformers`.

![Diagram przepływu danych estymatora.](./media/movie-recommendation/data-estimator-transformer.png)

Algorytm szkolenia rekomendacji, który będzie używany do szkolenia `Estimator`modelu jest przykładem .

Zbuduj za `Estimator` pomocą następujących kroków:

Utwórz `BuildAndTrainModel()` metodę, tuż `LoadData()` po tej metodzie, używając następującego kodu:

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{

}
```

> [!NOTE]
> Ta metoda daje błąd, dopóki nie dodasz return instrukcji w poniższych krokach.

Zdefiniuj przekształcenia danych, `BuildAndTrainModel()`dodając następujący kod do:

[!code-csharp[DataTransformations](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#DataTransformations "Define data transformations")]

Ponieważ `userId` `movieId` i reprezentują użytkowników i tytuły filmów, a nie wartości rzeczywistych, `userId` należy `movieId` użyć [Metody MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) do przekształcania każdego z nich w kolumnę typu `Feature` klucza numerycznego (format akceptowany przez algorytmy rekomendacji) i dodawanie ich jako nowych kolumn zestawu danych:

| userId | filmId (identyfikator filmowy) | Label | userIdZakodowany | movieIdKoded |
| ------------- |:-------------:| -----:|-----:|-----:|
| 1 | 1 | 4 | userKey1 | movieKey1 |
| 1 | 3 | 4 | userKey1 | movieKey2 |
| 1 | 6 | 4 | userKey1 | movieKey3 |

Wybierz algorytm uczenia maszynowego i dołącz go do definicji transformacji danych, dodając `BuildAndTrainModel()`następujący wiersz kodu w:

[!code-csharp[AddAlgorithm](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#AddAlgorithm "Add the training algorithm with options")]

[MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) jest algorytm szkolenia rekomendacji.  [Matrix Factorization](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) jest typowym podejściem do zalecenia, gdy masz dane na temat tego, jak użytkownicy ocenili produkty w przeszłości, co ma miejsce w przypadku zestawów danych w tym samouczku. Istnieją inne algorytmy rekomendacji, gdy masz dostępne różne dane (zobacz [sekcję Inne algorytmy rekomendacji](#other-recommendation-algorithms) poniżej, aby dowiedzieć się więcej).

W takim przypadku `Matrix Factorization` algorytm używa metody zwanej "filtrowaniem współpracy", która zakłada, że jeśli Użytkownik 1 ma taką samą opinię jak Użytkownik 2 w danej sprawie, użytkownik 1 jest bardziej prawdopodobne, że będzie czuł się tak samo jak Użytkownik 2 w innym problemie.

Na przykład, jeśli użytkownik 1 i użytkownik 2 oceń filmy podobnie, a następnie Użytkownik 2 jest bardziej prawdopodobne, aby cieszyć się film, że Użytkownik 1 oglądał i oceniane wysoko:

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| Użytkownik 1 | Oglądany i lubiany film | Oglądany i lubiany film | Oglądany i lubiany film |
| Użytkownik 2 | Oglądany i lubiany film | Oglądany i lubiany film | Nie oglądałem -- POLECAM film |

Trener `Matrix Factorization` ma kilka [opcji](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), o których możesz przeczytać więcej w sekcji [Hiperparametry algorytmu](#algorithm-hyperparameters) poniżej.

Dopasuj `Train` model do danych i zwróć uczonego modelu, `BuildAndTrainModel()` dodając następujące wierszy kodu w metodzie:

[!code-csharp[FitModel](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#FitModel "Call the Fit method and return back the trained model")]

[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) Metoda szkoli model z dostarczonym zestawem danych szkolenia. Technicznie wykonuje `Estimator` definicje, przekształcając dane i stosując szkolenie i zwraca z powrotem przeszkolony model, który jest . `Transformer`

Dodaj następujące jako następny wiersz kodu `Main()` w metodzie, aby wywołać metodę `BuildAndTrainModel()` i zwrócić uczonego modelu:

[!code-csharp[BuildTrainModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a>Ocenianie modelu

Po przeszkoleniu modelu należy użyć danych testowych, aby ocenić, jak model jest wykonywane.

Utwórz `EvaluateModel()` metodę, tuż `BuildAndTrainModel()` po tej metodzie, używając następującego kodu:

```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{

}
```

Przekształć dane, `Test` dodając `EvaluateModel()`następujący kod do:

[!code-csharp[Transform](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#Transform "Transform the test data")]

Metoda [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) tworzy prognozy dla wielu podanych wierszy wejściowych zestawu danych testowych.

Oceń model, dodając następujący wiersz kodu w `EvaluateModel()` metodzie:

[!code-csharp[Evaluate](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

Po ustawieniu przewidywania metoda [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) ocenia model, który porównuje przewidywane wartości z `Labels` rzeczywistymi w zestawie danych testowych i zwraca metryki dotyczące sposobu wykonywania modelu.

Wydrukuj metryki oceny do konsoli, dodając następujące wierszy `EvaluateModel()` kodu w metodzie:

[!code-csharp[PrintMetrics](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#PrintMetrics "Print the evaluation metrics")]

Dodaj następujące jako następny wiersz kodu `Main()` w metodzie, aby wywołać metodę: `EvaluateModel()`

[!code-csharp[EvaluateModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#EvaluateModelMain "Add EvaluateModel method in Main")]

Dane wyjściowe do tej pory powinny wyglądać podobnie do następującego tekstu:

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

W tym wyjściu istnieje 20 iteracji. W każdej iteracji miara błędu zmniejsza się i zbiega coraz bliżej 0.

(RMS `root of mean squared error` lub RMSE) służy do pomiaru różnic między wartościami przewidywanymi modelu a wartościami obserwowanymi przez test. Technicznie jest to pierwiastek kwadratowy średniej kwadratów błędów. Im niższa, tym lepszy jest model.

`R Squared`wskazuje, jak dobrze dane pasują do modelu. Waha się od 0 do 1. Wartość 0 oznacza, że dane są losowe lub w inny sposób nie mogą być dostosowane do modelu. Wartość 1 oznacza, że model dokładnie pasuje do danych. Chcesz, `R Squared` aby Twój wynik był jak najbardziej zbliżony do 1.

Budowanie udanych modeli jest procesem iteracyjnym. Ten model ma początkową niższą jakość, ponieważ samouczek używa małych zestawów danych, aby zapewnić szybkie szkolenie modelu. Jeśli nie jesteś zadowolony z jakości modelu, możesz spróbować go poprawić, udostępniając większe zestawy danych szkoleniowych lub wybierając różne algorytmy szkolenia z różnymi hiperparametrami dla każdego algorytmu. Aby uzyskać więcej informacji, zapoznaj się z sekcją [Ulepszanie modelu](#improve-your-model) poniżej.

## <a name="use-your-model"></a>Korzystanie z modelu

Teraz można użyć uczonego modelu do prognozowania nowych danych.

Utwórz `UseModelForSinglePrediction()` metodę, tuż `EvaluateModel()` po tej metodzie, używając następującego kodu:

```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

Użyj `PredictionEngine` do przewidywania klasyfikacji, dodając następujący `UseModelForSinglePrediction()`kod do:

[!code-csharp[PredictionEngine](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#PredictionEngine "Create Prediction Engine")]

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest interfejs emanujący interfejsu API wygody, który umożliwia wykonywanie przewidywanie na pojedyncze wystąpienie danych. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny dla nici. Dopuszczalne jest stosowanie w środowiskach jednowątkowych lub prototypowych. Aby zwiększyć wydajność i bezpieczeństwo wątków `PredictionEnginePool` w środowiskach [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) produkcyjnych, należy użyć usługi, która tworzy obiektów [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do użycia w całej aplikacji. Zobacz ten przewodnik, jak [ `PredictionEnginePool` używać w ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

> [!NOTE]
> `PredictionEnginePool`rozszerzenie usługi jest obecnie w wersji zapoznawczej.

Utwórz wystąpienie `MovieRating` `testInput` o nazwie i przekazać go do aparatu przewidywania, dodając `UseModelForSinglePrediction()` następujące wiersze kodu w metodzie:

[!code-csharp[MakeSinglePrediction](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) Funkcja sprawia, że przewidywanie w jednej kolumnie danych.

Następnie można użyć `Score`, lub przewidywanej oceny, aby ustalić, czy chcesz polecić film z movieId 10 do użytkownika 6. Im wyższy `Score`, tym większe prawdopodobieństwo, że użytkownik polubi konkretny film. W tym przypadku załóżmy, że polecasz filmy o przewidywanej ocenie > 3,5.

Aby wydrukować wyniki, dodaj następujące wiersze kodu `UseModelForSinglePrediction()` w metodzie:

[!code-csharp[PrintResults](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#PrintResults "Print the recommendation prediction results")]

Dodaj następujące jako następny wiersz kodu `Main()` w metodzie, aby wywołać metodę: `UseModelForSinglePrediction()`

[!code-csharp[UseModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#UseModelMain "Add UseModelForSinglePrediction method in Main")]

Dane wyjściowe tej metody powinny wyglądać podobnie do następującego tekstu:

```console
=============== Making a prediction ===============
Movie 10 is recommended for user 6
```

### <a name="save-your-model"></a>Zapisywanie modelu

Aby użyć modelu do prognozowania w aplikacjach użytkowników końcowych, należy najpierw zapisać model.

Utwórz `SaveModel()` metodę, tuż `UseModelForSinglePrediction()` po tej metodzie, używając następującego kodu:

```csharp
public static void SaveModel(MLContext mlContext, DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

Zapisz uczonego modelu, dodając `SaveModel()` następujący kod w metodzie:

[!code-csharp[SaveModel](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#SaveModel "Save the model to a zip file")]

Ta metoda zapisuje uczonego modelu do pliku zip (w folderze "Dane"), który następnie może być używany w innych aplikacjach .NET do prognozowania.

Dodaj następujące jako następny wiersz kodu `Main()` w metodzie, aby wywołać metodę: `SaveModel()`

[!code-csharp[SaveModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a>Korzystanie z zapisanego modelu

Po zapisaniu uczonego modelu można użyć modelu w różnych środowiskach. Zobacz [Zapisywanie i ładowanie przeszkolonych modeli,](../how-to-guides/save-load-machine-learning-models-ml-net.md) aby dowiedzieć się, jak operacjonalizować przeszkolony model uczenia maszynowego w aplikacjach.

## <a name="results"></a>Wyniki

Po zakończeniu powyższych czynności uruchom aplikację konsoli (Ctrl + F5). Wyniki z pojedynczej prognozy powyżej powinny być podobne do następujących. Mogą zostać wyświetlone ostrzeżenia lub wiadomości przetwarzania, ale te komunikaty zostały usunięte z następujących wyników dla jasności.

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

Gratulacje! Teraz pomyślnie skonstruowano model uczenia maszynowego do polecania filmów. Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation)

## <a name="improve-your-model"></a>Ulepszanie modelu

Istnieje kilka sposobów, które można zwiększyć wydajność modelu, dzięki czemu można uzyskać bardziej dokładne prognozy.

### <a name="data"></a>Dane

Dodanie większej ilości danych szkoleniowych, które mają wystarczającą liczbę próbek dla każdego użytkownika i identyfikatora filmu może pomóc poprawić jakość modelu rekomendacji.

[Krzyżowe sprawdzanie poprawności](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md) jest techniką oceny modeli, które losowo dzieli dane na podzbiory (zamiast wyodrębniania danych testowych z zestawu danych, jak to miało miejsce w tym samouczku) i zajmuje niektóre grupy jako dane pociągu i niektóre grupy jako dane testowe. Ta metoda przewyższa dokonywanie train-test podziału pod względem jakości modelu.

### <a name="features"></a>Funkcje

W tym samouczku używasz `Features` tylko`user id` `movie id`trzech `rating`( , i ), które są dostarczane przez zestaw danych.

Chociaż jest to dobry początek, w rzeczywistości możesz chcieć dodać inne atrybuty lub `Features` (na przykład wiek, płeć, geolokalizację itp.), jeśli są one zawarte w zestawie danych. Dodanie bardziej `Features` trafne może pomóc zwiększyć wydajność modelu rekomendacji.

Jeśli nie masz pewności, które `Features` mogą być najbardziej istotne dla twojego zadania uczenia maszynowego, możesz również skorzystać z obliczenia wkładu funkcji (FCC) i znaczenia funkcji [permutacji,](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md)które ML.NET zapewnia odkrycie najbardziej wpływowych. `Features`

### <a name="algorithm-hyperparameters"></a>Hiperparametry algorytmu

Podczas gdy ML.NET zapewnia dobre domyślne algorytmy szkoleniowe, można dodatkowo dostosować wydajność, zmieniając [hiperparametry](../resources/glossary.md#hyperparameter)algorytmu .

Dla `Matrix Factorization`, można eksperymentować z hiperparametrów, takich jak [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) i [ApproximationRank,](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) aby sprawdzić, czy to daje lepsze wyniki.

Na przykład w tym samouczku opcje algorytmu są następujące:

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

### <a name="other-recommendation-algorithms"></a>Inne algorytmy rekomendacji

Algorytm faktoryzacji macierzy z filtrowaniem współpracy jest tylko jednym z podejść do wykonywania rekomendacji filmowych. W wielu przypadkach dane klasyfikacji mogą nie być dostępne i mają tylko historię filmów dostępną od użytkowników. W innych przypadkach możesz mieć więcej niż tylko dane oceny użytkownika.

| Algorytm       | Scenariusz           | Sample  |
| ------------- |:-------------:| -----:|
| Czynnikiznawanie macierzy jednej klasy | Użyj tego, gdy masz tylko userId i movieId. Ten styl rekomendacji opiera się na scenariuszu współzakupu lub produktach często kupowanych razem, co oznacza, że poleci klientom zestaw produktów na podstawie własnej historii zamówień zakupu. | [>Wypróbuj](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| Maszyny faktoryzacji field aware | Użyj tej informacji, aby tworzyć rekomendacje, gdy masz więcej funkcji poza identyfikatorem użytkownika, identyfikatorem produktu i oceną (np. opis produktu lub cena produktu). Ta metoda używa również podejścia do filtrowania współpracy. | [>Wypróbuj](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a>Nowy scenariusz użytkownika

Jednym z częstych problemów w filtrowaniu współpracy jest problem z zimnym startem, czyli wtedy, gdy masz nowego użytkownika bez wcześniejszych danych do wyciągania wniosków. Ten problem jest często rozwiązywany przez proszenie nowych użytkowników o utworzenie profilu i, na przykład, ocenianie filmów, które widzieli w przeszłości. Chociaż ta metoda nakłada pewne obciążenie na użytkownika, zapewnia pewne dane początkowe dla nowych użytkowników bez historii klasyfikacji.

## <a name="resources"></a>Zasoby

Dane użyte w tym samouczku pochodzą z [zestawu danych MovieLens](http://files.grouplens.org/datasets/movielens/).

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> * Wybierz algorytm uczenia maszynowego
> * Przygotowywanie i ładowanie danych
> * Budowanie i szkolenie modelu
> * Ocena modelu
> * Wdrażanie modelu i korzystanie z go

Przejdź do następnego samouczka, aby dowiedzieć się więcej
> [!div class="nextstepaction"]
> [Analiza tonacji](sentiment-analysis.md)
