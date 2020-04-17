---
title: 'Samouczek: Zbuduj rekomendację filmu - faktoizacja macierzy'
description: W tym samouczku pokazano, jak utworzyć program polecający film z ML.NET w aplikacji konsoli .NET Core. Kroki używają języka C# i Visual Studio 2019.
author: briacht
ms.date: 09/30/2019
ms.custom: mvc, title-hack-0516
ms.topic: tutorial
ms.openlocfilehash: a1d7ef6226580fd3172b5714f9d7358298ba6668
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608000"
---
# <a name="tutorial-build-a-movie-recommender-using-matrix-factorization-with-mlnet"></a>Samouczek: Tworzenie programu rekomendacyjnego przy użyciu faktoryzacji macierzy z ML.NET

W tym samouczku pokazano, jak utworzyć program polecający film z ML.NET w aplikacji konsoli .NET Core. Kroki używają języka C# i Visual Studio 2019.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> * Wybieranie algorytmu uczenia maszynowego
> * Przygotowanie i załadowanie danych
> * Tworzenie i szkolenie modelu
> * Ocena modelu
> * Wdrażanie i korzystanie z modelu

Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation)

## <a name="machine-learning-workflow"></a>Przepływ pracy uczenia maszynowego

Aby wykonać zadanie, wykonasz następujące kroki, a także wszelkie inne ML.NET zadanie:

1. [Załaduj swoje dane](#load-your-data)
2. [Zbuduj i trenuj swój model](#build-and-train-your-model)
3. [Ocenianie modelu](#evaluate-your-model)
4. [Korzystanie z modelu](#use-your-model)

## <a name="prerequisites"></a>Wymagania wstępne

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowsze lub Visual Studio 2017 w wersji 15.6 lub nowszej z zainstalowanym obciążeniem ".NET Core rozwoju między platformami".

## <a name="select-the-appropriate-machine-learning-task"></a>Wybierz odpowiednie zadanie uczenia maszynowego

Istnieje kilka sposobów podejścia do problemów z rekomendacjami, takich jak zalecanie listy filmów lub polecanie listy powiązanych produktów, ale w tym przypadku można przewidzieć, jaką ocenę (1-5) użytkownik da konkretnemu filmowi i zalecić ten film, jeśli jest wyższy niż zdefiniowany próg (im wyższa ocena, tym większe prawdopodobieństwo polubienia konkretnego filmu przez użytkownika).

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

### <a name="create-a-project"></a>Tworzenie projektu

1. Otwórz program Visual Studio 2017. Z paska menu **wybierz pozycję Plik** > **nowy** > **projekt.** W oknie dialogowym **Nowy projekt** wybierz węzeł **Visual C#,** po którym następuje węzeł **.NET Core.** Następnie wybierz szablon projektu **aplikacji konsoli (net core).** W polu **tekstowym Nazwa** wpisz "MovieRecommender", a następnie wybierz przycisk **OK.**

2. Utwórz katalog o nazwie *Dane* w projekcie, aby zapisać zestaw danych:

    W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj** > **nowy folder**. Wpisz "Dane" i naciśnij enter.

3. Zainstaluj **pakiety NuGet Microsoft.ML** i **Microsoft.ML.Recommender:**

    W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**. Wybierz "nuget.org" jako źródło pakietu, wybierz kartę **Przeglądaj,** wyszukaj **Microsoft.ML**, wybierz pakiet na liście i wybierz przycisk **Zainstaluj.** Wybierz przycisk **OK** w oknie **dialogowym Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów. Powtórz te kroki dla **programu Microsoft.ML.Recommender**.

4. Dodaj następujące `using` instrukcje w górnej części pliku *Program.cs:*

    [!code-csharp[UsingStatements](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a>Pobieranie danych

1. Pobierz dwa zestawy danych i zapisz je w folderze *Dane,* który został wcześniej utworzony:

   * Kliknij prawym przyciskiem myszy [*rekomendację-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) i wybierz "Zapisz link (lub cel) jako..."
   * Kliknij prawym przyciskiem myszy [*rekomendację-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) i wybierz "Zapisz link (lub cel) jako..."

     Upewnij się, że \*pliki csv są zapisywane w folderze *Dane* lub \*po zapisaniu ich w innym miejscu, przenieś pliki csv do folderu *Dane.*

2. W Eksploratorze rozwiązań \*kliknij prawym przyciskiem myszy każdy z plików csv i wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**zmień wartość **kopiuj na Katalog wyjściowy** na **Kopiuj, jeśli jest nowszy**.

   ![GIF użytkownika wybierającego kopię, jeśli nowsza w programie VS.](./media/movie-recommendation/copy-to-output-if-newer.gif)

## <a name="load-your-data"></a>Załaduj swoje dane

Pierwszym krokiem w procesie ML.NET jest przygotowanie i załadowanie danych szkoleniowych i testowych modelu.

Dane klasyfikacji rekomendacji są `Train` `Test` dzielone na zestawy danych i. Dane `Train` są używane do dopasowania modelu. Dane `Test` są używane do tworzenia prognoz z przeszkolonym modelem i oceny wydajności modelu. Często ma podział 80/20 z `Train` danymi `Test` i danymi.

Poniżej znajduje się podgląd \*danych z plików csv:

![Zrzut ekranu przedstawiający podgląd zestawu danych CVS.](./media/movie-recommendation/csv-file-dataset-preview.png)

W \*plikach csv znajdują się cztery kolumny:

* `userId`
* `movieId`
* `rating`
* `timestamp`

W uczeniu maszynowym kolumny, które są używane do przewidywania są nazywane [Funkcje](../resources/glossary.md#feature), a kolumna z zwróconą przewidywaniem nosi nazwę [Label](../resources/glossary.md#label).

Chcesz przewidzieć oceny filmów, więc kolumna `Label`klasyfikacji to . Pozostałe trzy kolumny, `userId` `movieId`, `timestamp` i `Features` są używane `Label`do przewidywania .

| Funkcje      | Label         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |
| `timestamp`     |               |

To do Ciebie, aby `Features` zdecydować, które `Label`są używane do przewidywania . Można również użyć metod, takich jak [znaczenie funkcji permutacji,](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md) aby pomóc w wyborze najlepszego `Features`.

W takim przypadku należy `timestamp` wyeliminować kolumnę jako, ponieważ sygnatura czasowa `Feature` nie ma wpływu na sposób, w jaki użytkownik ocenia dany film, a tym samym nie przyczyni się do dokładniejszej prognozowania:

| Funkcje      | Label         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |

Następnie należy zdefiniować strukturę danych dla klasy wejściowej.

Dodaj nową klasę do projektu:

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj > Nowy element**.

2. W **oknie dialogowym Dodawanie nowego elementu**wybierz pozycję **Klasa** i zmień pole **Nazwa** na *MovieRatingData.cs*. Następnie wybierz przycisk **Dodaj.**

Plik *MovieRatingData.cs* zostanie otwarty w edytorze kodu. Dodaj następującą `using` instrukcję do górnej części *MovieRatingData.cs:*

```csharp
using Microsoft.ML.Data;
```

Utwórz klasę `MovieRating` wywoływaną przez usunięcie istniejącej definicji klasy i dodanie następującego kodu w *MovieRatingData.cs:*

[!code-csharp[MovieRatingClass](~/samples/snippets/machine-learning/MovieRecommendation/csharp/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

`MovieRating`określa klasę danych wejściowych. [Atrybut LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) określa, które kolumny (według indeksu kolumn) w zestawie danych powinny zostać załadowane. I `userId` `movieId` kolumny są `Features` twoje (dane wejściowe, które podasz modelowi do przewidzenia `Label`), a kolumna klasyfikacji jest `Label` tym, który będzie przewidywany (dane wyjściowe modelu).

Utwórz inną `MovieRatingPrediction`klasę , aby reprezentować przewidywane `MovieRating` wyniki, dodając następujący kod po klasie w *MovieRatingData.cs:*

[!code-csharp[PredictionClass](~/samples/snippets/machine-learning/MovieRecommendation/csharp/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

W *Program.cs*, wymienić `Console.WriteLine("Hello World!")` na następujący `Main()`kod wewnątrz:

[!code-csharp[MLContext](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#MLContext "Add MLContext")]

Klasa [MLContext](xref:Microsoft.ML.MLContext) jest punktem wyjścia dla wszystkich operacji ML.NET, a inicjowanie `mlContext` tworzy nowe środowisko ML.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest podobny, koncepcyjnie, do `DBContext` w entity framework.

Po `Main()`, utwórz `LoadData()`metodę o nazwie :

```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{

}
```

> [!NOTE]
> Ta metoda daje błąd, dopóki nie dodasz return instrukcji w poniższych krokach.

Inicjuj zmienne ścieżki danych, \*ładuj dane z `Train` plików `Test` csv i zwracaj dane jako `IDataView` obiekty, dodając następujące elementy jako następny wiersz kodu w `LoadData()`:

[!code-csharp[LoadData](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#LoadData "Load data from data paths")]

Dane w ML.NET są reprezentowane jako [klasa IDataView](xref:Microsoft.ML.IDataView). `IDataView`jest elastycznym, skutecznym sposobem opisywania danych tabelaryjskich (liczbowych i tekstowych). Dane można ładować z pliku tekstowego lub w czasie rzeczywistym (na przykład bazy danych SQL lub plików dziennika) do obiektu. `IDataView`

[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczytuje w pliku. Przyjmuje zmienne ścieżki danych i `IDataView`zwraca plik . W takim przypadku należy podać `Test` ścieżkę dla i `Train` plików i wskazać zarówno nagłówek pliku tekstowego (dzięki czemu można użyć nazwy kolumny poprawnie) i separator danych znaków przecinka (domyślny separator jest kartę).

Dodaj następujący kod `Main()` w metodzie, aby wywołać metodę `LoadData()` i zwrócić `Train` dane i: `Test`

[!code-csharp[LoadDataMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#LoadDataMain "Add LoadData method to Main")]

## <a name="build-and-train-your-model"></a>Zbuduj i trenuj swój model

Istnieją trzy główne pojęcia w ML.NET: [Dane,](../resources/glossary.md#data) [Transformatory](../resources/glossary.md#transformer)i [Estymatory.](../resources/glossary.md#estimator)

Algorytmy szkoleniowe uczenia maszynowego wymagają danych w określonym formacie. `Transformers`są używane do przekształcania danych tabelaryczne do zgodnego formatu.

![Diagram przepływu danych transformatora.](./media/movie-recommendation/data-transformer-transformed.png)

Tworzenie `Transformers` w ML.NET przez utworzenie `Estimators`. `Estimators`danych i zwrócić `Transformers`.

![Diagram przepływu danych estymatora.](./media/movie-recommendation/data-estimator-transformer.png)

Algorytm szkolenia rekomendacji, który będzie używany do `Estimator`szkolenia modelu jest przykładem .

Stwórz z `Estimator` następujących kroków:

Utwórz `BuildAndTrainModel()` metodę, zaraz `LoadData()` po metodzie, używając następującego kodu:

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{

}
```

> [!NOTE]
> Ta metoda daje błąd, dopóki nie dodasz return instrukcji w poniższych krokach.

Zdefiniuj przekształcenia danych, dodając następujący kod do: `BuildAndTrainModel()`

[!code-csharp[DataTransformations](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#DataTransformations "Define data transformations")]

Ponieważ `userId` `movieId` i reprezentują użytkowników i tytuły filmów, a nie wartości rzeczywiste, używasz `userId` Metody `movieId` [MapValueToKey(),](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) aby przekształcić każdą i każdą kolumnę o typie `Feature` klucza numerycznego (format akceptowany przez algorytmy rekomendacji) i dodać je jako nowe kolumny zestawu danych:

| userId | movieId (ida) | Label | userIdEncoded | movieIdEncoded |
| ------------- |:-------------:| -----:|-----:|-----:|
| 1 | 1 | 4 | userKey1 | filmKey1 |
| 1 | 3 | 4 | userKey1 | filmKey2 |
| 1 | 6 | 4 | userKey1 | filmKey3 |

Wybierz algorytm uczenia maszynowego i dołącz go do definicji transformacji danych, dodając `BuildAndTrainModel()`następujące elementy jako następny wiersz kodu w:

[!code-csharp[AddAlgorithm](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#AddAlgorithm "Add the training algorithm with options")]

[MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) jest algorytm szkolenia rekomendacji.  [Macierz Factorization](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) jest wspólne podejście do zalecenia, gdy masz dane na temat sposobu, w jaki użytkownicy ocenili produkty w przeszłości, co ma miejsce w przypadku zestawów danych w tym samouczku. Istnieją inne algorytmy rekomendacji, gdy masz różne dane dostępne (zobacz [inne algorytmy rekomendacji](#other-recommendation-algorithms) poniżej, aby dowiedzieć się więcej).

W takim przypadku `Matrix Factorization` algorytm używa metody o nazwie "filtrowanie współpracy", która zakłada, że jeśli użytkownik 1 ma taką samą opinię jak Użytkownik 2 w pewnym problemie, użytkownik 1 jest bardziej prawdopodobne, aby czuć się tak samo jak Użytkownik 2 o innym problemie.

Na przykład, jeśli użytkownik 1 i Użytkownik 2 oceniają filmy w podobny sposób, użytkownik 2 jest bardziej skłonny do korzystania z filmu, który użytkownik 1 oglądał i wysoko ocenił:

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| Użytkownik 1 | Oglądany i lubiany film | Oglądany i lubiany film | Oglądany i lubiany film |
| Użytkownik 2 | Oglądany i lubiany film | Oglądany i lubiany film | Nie oglądałem -- POLECAM film |

Trener `Matrix Factorization` ma kilka [opcji](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), o których można przeczytać więcej w [hiperparametrach algorytm](#algorithm-hyperparameters) poniżej.

Dopasuj `Train` model do danych i zwróć przeszkolony model, dodając następujący `BuildAndTrainModel()` wiersz kodu w metodzie:

[!code-csharp[FitModel](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#FitModel "Call the Fit method and return back the trained model")]

[Metoda Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) trenuje model z dostarczonym zestawem danych szkoleniowych. Technicznie wykonuje `Estimator` definicje, przekształcając dane i stosując szkolenie, i zwraca z powrotem przeszkolony `Transformer`model, który jest .

Dodaj następujące jako następny wiersz kodu `Main()` w metodzie, aby wywołać metodę `BuildAndTrainModel()` i zwrócić przeszkolony model:

[!code-csharp[BuildTrainModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a>Ocenianie modelu

Po przeszkoleniu modelu użyj danych testowych, aby ocenić, jak model działa.

Utwórz `EvaluateModel()` metodę, zaraz `BuildAndTrainModel()` po metodzie, używając następującego kodu:

```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{

}
```

Przekształć `Test` dane, `EvaluateModel()`dodając następujący kod do:

[!code-csharp[Transform](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#Transform "Transform the test data")]

Metoda [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) sprawia, że prognoz dla wielu wierszy wejściowych dostarczonych zestawu danych testowych.

Oceń model, dodając następujące jako następny wiersz `EvaluateModel()` kodu w metodzie:

[!code-csharp[Evaluate](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

Po ustawieniu prognozowania metoda [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) ocenia model, który porównuje przewidywane wartości `Labels` z rzeczywistym w zestawie danych testowych i zwraca metryki dotyczące wykonywania modelu.

Wydrukuj metryki oceny w konsoli, dodając następujące elementy `EvaluateModel()` jako następny wiersz kodu w metodzie:

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

W tym wyjściu istnieje 20 iteracji. W każdej iteracji miara błędu zmniejsza się i zbiega się coraz bliżej 0.

(RMS `root of mean squared error` lub RMSE) służy do pomiaru różnic między wartościami przewidywanymi modelami a obserwowanymi wartościami testowego zestawu danych. Technicznie jest to pierwiastek kwadratowy średniej kwadratów błędów. Im niższy, tym lepszy jest model.

`R Squared`wskazuje, jak dobrze dane pasują do modelu. Waha się od 0 do 1. Wartość 0 oznacza, że dane są losowe lub w inny sposób nie mogą być dostosowane do modelu. Wartość 1 oznacza, że model dokładnie pasuje do danych. Chcesz, `R Squared` aby twój wynik był jak najbliżej 1, jak to możliwe.

Tworzenie udanych modeli jest procesem iteracyjnym. Ten model ma początkową niższą jakość, ponieważ samouczek używa małych zestawów danych, aby zapewnić szybkie szkolenie modelu. Jeśli nie jesteś zadowolony z jakości modelu, można spróbować go poprawić, zapewniając większe zestawy danych szkoleniowych lub wybierając różne algorytmy szkoleniowe z różnymi hiper-parametrów dla każdego algorytmu. Aby uzyskać więcej informacji, zapoznaj się z sekcją [Ulepszanie modelu](#improve-your-model) poniżej.

## <a name="use-your-model"></a>Korzystanie z modelu

Teraz można użyć przeszkolonego modelu do przewidywania na nowe dane.

Utwórz `UseModelForSinglePrediction()` metodę, zaraz `EvaluateModel()` po metodzie, używając następującego kodu:

```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

Służy `PredictionEngine` do przewidywania klasyfikacji przez dodanie `UseModelForSinglePrediction()`następującego kodu do:

[!code-csharp[PredictionEngine](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#PredictionEngine "Create Prediction Engine")]

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest interfejsem API wygody, który umożliwia wykonywanie prognozowania na jednym wystąpieniu danych. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny dla wątków. Jest dopuszczalne do użycia w środowiskach jednowątkowych lub prototypowych. Aby zwiększyć wydajność i bezpieczeństwo wątków `PredictionEnginePool` w środowiskach [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) produkcyjnych, należy użyć usługi, która tworzy obiekty [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do użycia w całej aplikacji. Zobacz ten przewodnik dotyczący [używania `PredictionEnginePool` w ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

> [!NOTE]
> `PredictionEnginePool`rozszerzenie usługi jest obecnie w wersji zapoznawczej.

Utwórz wystąpienie wywoływane `MovieRating` `testInput` i przekazać go do aparatu przewidywania, dodając `UseModelForSinglePrediction()` następujące jako następne wiersze kodu w metodzie:

[!code-csharp[MakeSinglePrediction](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) Funkcja sprawia, że przewidywanie na jednej kolumnie danych.

Następnie można użyć `Score`, lub przewidywanej klasyfikacji, aby określić, czy chcesz polecić film z movieId 10 do użytkownika 6. Im `Score`wyższe, tym większe prawdopodobieństwo polubienia konkretnego filmu przez użytkownika. W takim przypadku załóżmy, że polecasz filmy o przewidywanej ocenie > 3,5.

Aby wydrukować wyniki, dodaj następujące wiersze jako `UseModelForSinglePrediction()` następne wiersze kodu w metodzie:

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

Utwórz `SaveModel()` metodę, zaraz `UseModelForSinglePrediction()` po metodzie, używając następującego kodu:

```csharp
public static void SaveModel(MLContext mlContext, DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

Zapisz przeszkolony model, dodając następujący `SaveModel()` kod w metodzie:

[!code-csharp[SaveModel](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#SaveModel "Save the model to a zip file")]

Ta metoda zapisuje przeszkolony model do pliku zip (w folderze "Dane"), który może być następnie używany w innych aplikacjach .NET do tworzenia prognoz.

Dodaj następujące jako następny wiersz kodu `Main()` w metodzie, aby wywołać metodę: `SaveModel()`

[!code-csharp[SaveModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a>Korzystanie z zapisanego modelu

Po zapisaniu przeszkolonego modelu można korzystać z modelu w różnych środowiskach. Zobacz [Zapisywanie i ładowanie wyszkolonych modeli,](../how-to-guides/save-load-machine-learning-models-ml-net.md) aby dowiedzieć się, jak operacjonalizacji wyszkolonego modelu uczenia maszynowego w aplikacjach.

## <a name="results"></a>Wyniki

Po wykonać powyższe czynności uruchom aplikację konsoli (Ctrl + F5). Wyniki z pojedynczej prognozy powyżej powinny być podobne do następujących. Możesz zobaczyć ostrzeżenia lub przetwarzania wiadomości, ale te komunikaty zostały usunięte z następujących wyników dla jasności.

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

Gratulacje! Pomyślnie skompilowano model uczenia maszynowego do polecania filmów. Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation)

## <a name="improve-your-model"></a>Ulepszanie modelu

Istnieje kilka sposobów, które można poprawić wydajność modelu, dzięki czemu można uzyskać dokładniejsze prognoz.

### <a name="data"></a>Dane

Dodanie większej liczby danych szkoleniowych, które mają wystarczającą liczbę próbek dla każdego użytkownika i identyfikator filmu, może poprawić jakość modelu rekomendacji.

[Sprawdzanie poprawności krzyżowej](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md) jest techniką oceny modeli, która losowo dzieli dane na podzbiory (zamiast wyodrębniania danych testowych z zestawu danych, tak jak to miało miejsce w tym samouczku) i przyjmuje niektóre grupy jako dane pociągu, a niektóre grupy jako dane testowe. Ta metoda przewyższa dokonywanie podziału testu pociągu pod względem jakości modelu.

### <a name="features"></a>Funkcje

W tym samouczku używasz `Features` `user id`tylko `movie id`trzech `rating`( , i ), które są dostarczane przez zestaw danych.

Chociaż jest to dobry początek, w rzeczywistości można `Features` dodać inne atrybuty lub (na przykład wiek, płeć, geolokalię itp.), jeśli są one zawarte w zestawie danych. Dodanie bardziej `Features` istotne może pomóc poprawić wydajność modelu rekomendacji.

Jeśli nie masz `Features` pewności, które z nich może być najbardziej istotne dla twojego zadania uczenia maszynowego, możesz również skorzystać z obliczania `Features`wkładu funkcji (FCC) i znaczenia funkcji [permutacji,](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md)które ML.NET zapewnia, aby odkryć najbardziej wpływowe.

### <a name="algorithm-hyperparameters"></a>Algorytm hiperparametry

Chociaż ML.NET zapewnia dobre domyślne algorytmy szkoleniowe, można dodatkowo dostosować wydajność, zmieniając [hiperparametry algorytmu.](../resources/glossary.md#hyperparameter)

For `Matrix Factorization`, można eksperymentować z hiperparametrów, takich jak [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) i [ApproximationRank,](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) aby sprawdzić, czy to daje lepsze wyniki.

Na przykład w tym samouczku opcje algorytmu są:

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

Algorytm faktoryzacji macierzy z filtrowania współpracy jest tylko jedno podejście do wykonywania zaleceń filmowych. W wielu przypadkach dane ocen mogą nie być dostępne i mieć dostępną tylko historię filmów od użytkowników. W innych przypadkach możesz mieć więcej niż tylko dane ratingowe użytkownika.

| Algorytm       | Scenariusz           | Przykład  |
| ------------- |:-------------:| -----:|
| Faktoryzacja macierzy jednej klasy | Użyj tego, gdy masz tylko identyfikator użytkownika i identyfikator movieId. Ten styl rekomendacji opiera się na scenariuszu współskupu lub produktach często kupowanych razem, co oznacza, że poleci klientom zestaw produktów opartych na ich własnej historii zamówień zakupu. | [>Wypróbuj](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| Maszyny faktoryzacji z uwzględnieniem pola | Użyj tego, aby sformułować zalecenia, gdy masz więcej funkcji poza identyfikatorem użytkownika, identyfikatorem produktu i oceną (na przykład opis produktu lub cenę produktu). Ta metoda używa również podejścia do filtrowania współpracy. | [>Wypróbuj](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a>Nowy scenariusz użytkownika

Jednym z typowych problemów w filtrowaniu współpracy jest problem zimnego rozruchu, który jest, gdy masz nowego użytkownika bez poprzednich danych do wyciągnięcia wniosków z. Ten problem jest często rozwiązywany przez prośbę nowych użytkowników o utworzenie profilu i, na przykład, ocenę filmów, które widzieli w przeszłości. Chociaż ta metoda nakłada pewne obciążenie na użytkownika, zapewnia pewne dane początkowe dla nowych użytkowników bez historii klasyfikacji.

## <a name="resources"></a>Zasoby

Dane użyte w tym samouczku pochodzą z [movielens dataset](http://files.grouplens.org/datasets/movielens/).

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> * Wybieranie algorytmu uczenia maszynowego
> * Przygotowanie i załadowanie danych
> * Tworzenie i szkolenie modelu
> * Ocena modelu
> * Wdrażanie i korzystanie z modelu

Przejdź do następnego samouczka, aby dowiedzieć się więcej
> [!div class="nextstepaction"]
> [Analiza tonacji](sentiment-analysis.md)
