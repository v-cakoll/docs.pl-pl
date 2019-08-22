---
title: 'Samouczek: Tworzenie zalecenia dotyczącego filmu — factorization macierzy'
description: W tym samouczku przedstawiono sposób tworzenia zalecenia dotyczącego filmu z ML.NET w aplikacji konsolowej .NET Core. Kroki używają C# i programu Visual Studio 2019.
author: briacht
ms.date: 07/09/2019
ms.custom: mvc, title-hack-0516
ms.topic: tutorial
ms.openlocfilehash: 82da512d437ed2c5c28601c34687494b8be4d046
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666687"
---
# <a name="tutorial-build-a-movie-recommender-using-matrix-factorizaton-with-mlnet"></a>Samouczek: Tworzenie zalecenia dotyczącego filmu przy użyciu narzędzia Matrix factorizaton z ML.NET

W tym samouczku przedstawiono sposób tworzenia zalecenia dotyczącego filmu z ML.NET w aplikacji konsolowej .NET Core. Kroki używają C# i programu Visual Studio 2019.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Wybierz algorytm uczenia maszynowego
> * Przygotowywanie i ładowanie danych
> * Kompilowanie i uczenie modelu
> * Oceń model
> * Wdrażanie i korzystanie z modelu

Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) .

## <a name="machine-learning-workflow"></a>Przepływ pracy uczenia maszynowego

Wykonaj następujące kroki, aby wykonać zadanie, a także inne zadania ML.NET:

1. [Ładowanie danych](#load-your-data)
2. [Kompilowanie i uczenie modelu](#build-and-train-your-model)
3. [Oceń model](#evaluate-your-model)
4. [Korzystanie z modelu](#use-your-model)

## <a name="prerequisites"></a>Wymagania wstępne

* [Program Visual Studio 2017 15,6 lub nowszy](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core.

## <a name="select-the-appropriate-machine-learning-task"></a>Wybierz odpowiednie zadanie uczenia maszynowego

Istnieje kilka sposobów podejścia do problemów z zaleceniami, takich jak zalecanie listy filmów lub zalecaną listę produktów pokrewnych, ale w tym przypadku można przewidzieć klasyfikację (1-5) użytkownika w określonym filmie i zalecać film, jeśli jest wyższy niż określony próg (im wyższa ocena, tym większe prawdopodobieństwo poniesienia określonego filmu przez użytkownika).

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

### <a name="create-a-project"></a>Tworzenie projektu

1. Otwórz program Visual Studio 2017. Na pasku menu wybierz pozycję **plik** > **Nowy** > **projekt** . W oknie dialogowym **Nowy projekt** wybierz węzeł **wizualizacji C#**  , a następnie węzeł **.NET Core** . Następnie wybierz szablon projektu **aplikacja konsoli (.NET Core)** . W polu tekstowym **Nazwa** wpisz "MovieRecommender", a następnie wybierz przycisk **OK** .

2. Utwórz katalog o nazwie *dane* w projekcie w celu zapisania zestawu danych:

    W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj** > **Nowy folder**. Wpisz "Data" i naciśnij klawisz ENTER.

3. Zainstaluj pakiety NuGet **Microsoft.ml** i **Microsoft. ml. zalecenia** :

    W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę **Przeglądaj** , wyszukaj pozycję **Microsoft.ml**, wybierz pakiet z listy, a następnie wybierz przycisk **Instaluj** . Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie wybierz przycisk Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów. Powtórz te kroki dla **Microsoft. ml. zalecamy**.

4. Dodaj następujące `using` instrukcje w górnej części pliku *program.cs* :

    [!code-csharp[UsingStatements](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a>Pobieranie danych

1. Pobierz dwa zestawy danych i Zapisz je w utworzonym wcześniej folderze *danych* :

   * Kliknij prawym przyciskiem myszy plik [*Recommendation-ratings-Train. csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) i wybierz pozycję "Zapisz link (lub cel) jako..."
   * Kliknij prawym przyciskiem myszy plik [*Recommendation-ratings-test. csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) i wybierz pozycję "Zapisz link (lub cel) jako..."

     Upewnij \*się, że zapisano pliki CSV do folderu *danych* lub po jego zapisaniu w \*innym miejscu Przenieś pliki CSV do folderu *dane* .

2. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy każdy z \*plików CSV i wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.

   ![Kopiuj, jeśli nowszy w programie VS](./media/movie-recommendation/copytoout.gif)

## <a name="load-your-data"></a>Ładowanie danych

Pierwszym krokiem w procesie ML.NET jest przygotowanie i załadowanie modelu szkolenia i testowanie danych.

Dane klasyfikacji rekomendacji są podzielone na `Train` i `Test` zestawy danych. `Train` Dane są używane do dopasowania do modelu. `Test` Dane służą do przeprowadzania prognoz z przeszkolonym modelem i oceny wydajności modelu. Często istnieje 80/20 podział z `Train` i `Test` danych.

Poniżej znajduje się podgląd danych z \*plików CSV:

![Podgląd danych](./media/movie-recommendation/csv-dataset-preview.png)

\*W plikach CSV znajdują się cztery kolumny:

* `userId`
* `movieId`
* `rating`
* `timestamp`

W obszarze Uczenie maszynowe kolumny, które są używane do prognozowania, są nazywane [funkcjami](../resources/glossary.md#feature), a kolumna z zwróconym przewidywaniam nazywa się [etykietą](../resources/glossary.md#label).

Chcesz przewidzieć klasyfikację filmów, aby kolumna Rating była `Label`kolumną. Pozostałe trzy `userId`kolumny, `movieId`, i `timestamp` są `Features` używane do przewidywania `Label`.

| Funkcje      | Etykieta         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |
| `timestamp`     |               |

Jest to konieczne, aby określić, które `Features` są używane do `Label`przewidywania. Możesz również użyć metod, takich jak [Funkcja Permutacja](../how-to-guides/determine-global-feature-importance-in-model.md) , aby ułatwić wybór najlepszych `Features`.

W takim przypadku należy wyeliminować `timestamp` kolumnę `Feature` jako, ponieważ sygnatura czasowa nie wpływa na to, jak użytkownik ocenia dany film i w związku z tym nie przyczynia się do dokładniejszego przewidywania:

| Funkcje      | Etykieta         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |

Następnie należy zdefiniować strukturę danych dla klasy wejściowej.

Dodaj nową klasę do projektu:

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz pozycję **Dodaj > nowy element**.

2. W **oknie dialogowym Dodaj nowy element**wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *MovieRatingData.cs*. Następnie wybierz przycisk **Dodaj** .

Plik *MovieRatingData.cs* zostanie otwarty w edytorze kodu. Dodaj następującą `using` instrukcję na początku *MovieRatingData.cs*:

```csharp
using Microsoft.ML.Data;
```

Utwórz klasę o nazwie `MovieRating` , usuwając istniejącą definicję klasy i dodając następujący kod w *MovieRatingData.cs*:

[!code-csharp[MovieRatingClass](~/samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

`MovieRating`Określa klasę danych wejściowych. Atrybut [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) określa, które kolumny (według indeksu kolumn) w zestawie danych powinny zostać załadowane. `Label` `Label`Kolumny `userId` i`movieId` są`Features` kolumnami (dane wejściowe będą nadawać modelowi przewidywanie), a kolumna oceny jest przewidywalna (dane wyjściowe modelu).

Utwórz kolejną klasę, `MovieRatingPrediction`aby reprezentować przewidywane wyniki, dodając następujący kod `MovieRating` po klasie w *MovieRatingData.cs*:

[!code-csharp[PredictionClass](~/samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

W *program.cs*, Zamień na `Console.WriteLine("Hello World!")` następujący kod `Main()`w:

[!code-csharp[MLContext](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MLContext "Add MLContext")]

[Klasa MLContext](xref:Microsoft.ML.MLContext) jest punktem początkowym dla wszystkich operacji ml.NET, a inicjowanie `mlContext` tworzy nowe środowisko ml.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest to podobne, pojęciowo do `DBContext` w Entity Framework.

Po `Main()`utworzeniu należy utworzyć metodę o `LoadData()`nazwie:

```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{

}
```

> [!NOTE]
> Ta metoda daje błąd do momentu dodania instrukcji return w poniższych krokach.

Zainicjuj zmienne ścieżki \*danych, Załaduj dane z plików CSV i `Train` Zwróć dane oraz `Test` jako `IDataView` obiekty, dodając następujący kod jako następny wiersz kodu w `LoadData()`:

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadData "Load data from data paths")]

Dane w ML.NET są reprezentowane jako [Klasa IDataView](xref:Microsoft.ML.IDataView). `IDataView`to elastyczny i wydajny sposób opisywania danych tabelarycznych (liczbowych i tekstowych). Dane można ładować z pliku tekstowego lub w czasie rzeczywistym (na przykład bazy danych SQL lub plików dziennika) do `IDataView` obiektu.

[LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczytuje w pliku. Przyjmuje zmienne ścieżki danych i zwraca `IDataView`. W takim przypadku należy podać ścieżkę do `Test` plików i `Train` wskazać zarówno nagłówek pliku tekstowego (tak, aby można było poprawnie używać nazw kolumn), jak i separator danych znak przecinka (domyślny separator jest tabulatorem).

Dodaj następujące `Main()` dwa wiersze kodu w metodzie, aby `LoadData()` wywołać metodę i zwrócić `Train` dane i `Test` :

[!code-csharp[LoadDataMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadDataMain "Add LoadData method to Main")]

## <a name="build-and-train-your-model"></a>Kompilowanie i uczenie modelu

Istnieją trzy podstawowe koncepcje w ML.NET: [Dane](../resources/glossary.md#data), [Transformatory](../resources/glossary.md#transformer)i [szacowania](../resources/glossary.md#estimator).

Algorytmy szkoleniowe dotyczące uczenia maszynowego wymagają danych w określonym formacie. `Transformers`służy do przekształcania danych tabelarycznych w zgodny format.

![obraz transformatora](./media/movie-recommendation/transformer.png)

Tworzysz w ml.NET, tworząc `Estimators`. `Transformers` `Estimators`Zapoznaj się z danymi `Transformers`i wróć.

![obraz szacowania](./media/movie-recommendation/estimator.png)

Algorytm szkolenia rekomendacji, który będzie używany do uczenia modelu, jest przykładem `Estimator`.

`Estimator` Wykonaj następujące czynności:

Utwórz metodę, tuż po metodzie, przy użyciu następującego kodu: `LoadData()` `BuildAndTrainModel()`

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{

}
```

> [!NOTE]
> Ta metoda daje błąd do momentu dodania instrukcji return w poniższych krokach.

Zdefiniuj przekształcenia danych, dodając następujący kod do `BuildAndTrainModel()`:

[!code-csharp[DataTransformations](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#DataTransformations "Define data transformations")]

Ponieważ `userId` i `Feature` `movieId` [](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) `userId` reprezentują użytkowników i tytuły filmów, a nie wartości rzeczywiste, należy użyć metody MapValueToKey () do przekształcania każdego i każdego z nich w kolumnę typu klucza numerycznego (zaakceptowano format `movieId` według algorytmów rekomendacji) i Dodaj je jako nowe kolumny zestawu danych:

| userId | movieId | Etykieta | userIdEncoded | movieIdEncoded |
| ------------- |:-------------:| -----:|-----:|-----:|
| 1 | 1 | 4 | userKey1 | movieKey1 |
| 1 | 3 | 4 | userKey1 | movieKey2 |
| 1 | 6 | 4 | userKey1 | movieKey3 |

Wybierz algorytm uczenia maszynowego i dołącz go do definicji transformacji danych, dodając następujący element jako następny wiersz kodu w `BuildAndTrainModel()`:

[!code-csharp[AddAlgorithm](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#AddAlgorithm "Add the training algorithm with options")]

[MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) jest algorytmem szkoleniowym rekomendacji.  [Factorization macierzy](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) jest powszechnym podejściem do rekomendacji, gdy masz dane dotyczące sposobu, w jaki użytkownicy mają sklasyfikowane produkty w przeszłości, czyli w przypadku zestawów danych w tym samouczku. Istnieją inne algorytmy rekomendacji, w których dostępne są różne dane (zobacz [inne algorytmy rekomendacji](#other-recommendation-algorithms) poniżej, aby dowiedzieć się więcej).

W tym przypadku `Matrix Factorization` algorytm używa metody zwanej "filtrowaniem do współpracy", która zakłada, że jeśli użytkownik 1 ma taką samą opinię co użytkownik 2 w przypadku pewnego problemu, wówczas użytkownik 1 będzie prawdopodobnie taki sam jak użytkownik 2, który ma inny problem.

Na przykład jeśli użytkownik 1 i użytkownik 2 oceniają szybkość filmów w podobny sposób, wówczas użytkownik 2 może korzystać z filmu, który użytkownik 1 zaobserwuje i ocenił:

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| Użytkownik 1 | Film obserwowany i Niemnie | Film obserwowany i Niemnie | Film obserwowany i Niemnie |
| Użytkownik 2 | Film obserwowany i Niemnie | Film obserwowany i Niemnie | Nie został obserwowany — ZALECAnym filmem |

Trainer ma kilka [opcji](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), które można dowiedzieć się więcej o w poniższej sekcji [preparameters Algorithm](#algorithm-hyperparameters). `Matrix Factorization`

Dopasuj model do `Train` danych i zwróć przeszkolony model, dodając następujący kod jako następny wiersz kodu `BuildAndTrainModel()` w metodzie:

[!code-csharp[FitModel](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#FitModel "Call the Fit method and return back the trained model")]

Metoda [dopasowywania ()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) pociąga za siebie model z udostępnionym zestawem danych szkoleniowych. Technicznie wykonuje `Estimator` definicje przez Przekształcanie danych i stosowanie szkoleń i zwraca z powrotem model szkolony, który `Transformer`jest.

Dodaj następujący kod jako następny wiersz kodu w `Main()` metodzie, aby `BuildAndTrainModel()` wywołać metodę i zwrócić szkolony model:

[!code-csharp[BuildTrainModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a>Oceń model

Po przeprowadzeniu szkolenia modelu Użyj danych testowych, aby oszacować, jak działa model.

Utwórz metodę, tuż po metodzie, przy użyciu następującego kodu: `BuildAndTrainModel()` `EvaluateModel()`

```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{

}
```

Przekształć `EvaluateModel()`dane, dodając następujący kod do: `Test`

[!code-csharp[Transform](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Transform "Transform the test data")]

Metoda [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) udostępnia prognozy dla wielu podanych danych wejściowych dla testu zestawu danych.

Oceń model poprzez dodanie następujących elementów jako następny wiersz kodu w `EvaluateModel()` metodzie:

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

Po zestawie prognoz Metoda [oceny ()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) ocenia model, który porównuje wartości przewidywane z wartością rzeczywistą `Labels` w testowanym zestawie danych i zwraca metryki dotyczące sposobu działania modelu.

Wydrukuj metryki oceny do konsoli, dodając następujący kod jako następny wiersz kodu w `EvaluateModel()` metodzie:

[!code-csharp[PrintMetrics](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintMetrics "Print the evaluation metrics")]

Dodaj następujący kod jako następny wiersz kodu w `Main()` metodzie, aby `EvaluateModel()` wywołać metodę:

[!code-csharp[EvaluateModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#EvaluateModelMain "Add EvaluateModel method in Main")]

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

W tych danych wyjściowych występuje 20 iteracji. W każdej iteracji miara błędów jest zmniejszana i zbieżna bliżej i bliższa 0.

`root of mean squared error` (RMS lub RMSE) służy do mierzenia różnic między wartościami przewidywanymi przez model i wartościami obserwowanymi testów zestawu danych. Jest to technicznie pierwiastek kwadratowy średniej kwadratów błędów. Im niższa wartość, tym lepszy jest model.

`R Squared`wskazuje, jak dobre dane pasują do modelu. Zakresy z zakresu od 0 do 1. Wartość 0 oznacza, że dane są losowo lub w przeciwnym razie nie można dopasować do modelu. Wartość 1 oznacza, że model dokładnie pasuje do danych. Chcesz, aby `R Squared` wynik był możliwie blisko 1, jak to możliwe.

Kompilowanie udanych modeli jest procesem iteracyjnym. Ten model ma wstępną niższą jakość, ponieważ samouczek używa małych zestawów danych w celu zapewnienia szybkiego szkolenia modeli. Jeśli jakość modelu jest niezadowalająca, możesz spróbować go ulepszyć, dostarczając większe zestawy danych szkoleniowych lub wybierając różne algorytmy szkoleniowe z różnymi parametrami funkcji Hyper-Parameters dla każdego algorytmu. Aby uzyskać więcej informacji, zapoznaj się z sekcją [Popraw model](#improve-your-model) poniżej.

## <a name="use-your-model"></a>Korzystanie z modelu

Teraz można użyć Twojego przeszkolonego modelu do prognozowania nowych danych.

Utwórz metodę, tuż po metodzie, przy użyciu następującego kodu: `EvaluateModel()` `UseModelForSinglePrediction()`

```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

Użyj do przewidywania klasyfikacji, dodając następujący kod do `UseModelForSinglePrediction()`: `PredictionEngine`

[!code-csharp[PredictionEngine](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PredictionEngine "Create Prediction Engine")]

[Klasa PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest WYGODNYm interfejsem API, który umożliwia przekazywanie pojedynczej instancji danych, a następnie przeprowadza prognozowanie na tym pojedynczym wystąpieniu danych.

Utwórz wystąpienie o `MovieRating` nazwie `testInput` i przekaż je do aparatu przewidywania, dodając następujący element jako następny `UseModelForSinglePrediction()` wiersz kodu w metodzie:

[!code-csharp[MakeSinglePrediction](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

Funkcja [przewidywania ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) dokonuje prognozowania dla pojedynczej kolumny danych.

Następnie można użyć `Score`lub klasyfikacji przewidywanej, aby określić, czy chcesz zalecić film z movieId 10 do użytkownika 6. Im wyższy poziom `Score`, tym większe prawdopodobieństwo, że użytkownik przydzieli określony film. W tym przypadku Załóżmy, że zaleca się używanie filmów z przewidywaną klasyfikacją > 3,5.

Aby wydrukować wyniki, Dodaj następujący kod jako następny wiersz kodu w `UseModelForSinglePrediction()` metodzie:

[!code-csharp[PrintResults](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintResults "Print the recommendation prediction results")]

Dodaj następujący kod jako następny wiersz kodu w `Main()` metodzie, aby `UseModelForSinglePrediction()` wywołać metodę:

[!code-csharp[UseModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UseModelMain "Add UseModelForSinglePrediction method in Main")]

Dane wyjściowe tej metody powinny wyglądać podobnie do następującego tekstu:

```console
=============== Making a prediction ===============
Movie 10 is recommended for user 6
```

### <a name="save-your-model"></a>Zapisz model

Aby używać modelu do prognozowania aplikacji użytkowników końcowych, należy najpierw zapisać model.

Utwórz metodę, tuż po metodzie, przy użyciu następującego kodu: `UseModelForSinglePrediction()` `SaveModel()`

```csharp
public static void SaveModel(MLContext mlContext, DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

Zapisz swój przeszkolony model, dodając następujący kod w `SaveModel()` metodzie:

[!code-csharp[SaveModel](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModel "Save the model to a zip file")]

Ta metoda zapisuje swój przeszkolony model do pliku zip (w folderze "dane"), który można następnie użyć w innych aplikacjach .NET do prognozowania.

Dodaj następujący kod jako następny wiersz kodu w `Main()` metodzie, aby `SaveModel()` wywołać metodę:

[!code-csharp[SaveModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a>Użyj zapisanego modelu

Po zapisaniu przeszkolonego modelu można korzystać z modelu w różnych środowiskach (zobacz [Przewodnik po poradniku](../how-to-guides/consuming-model-ml-net.md) ), aby dowiedzieć się, jak operacjonalizować model uczenia maszynowego w aplikacjach.

## <a name="results"></a>Wyniki

Po wykonaniu powyższych kroków uruchom aplikację konsolową (Ctrl + F5). Wyniki z pojedynczej przewidywania powyżej powinny być podobne do następujących. Mogą pojawić się ostrzeżenia lub komunikaty o przetwarzaniu, ale te komunikaty zostały usunięte z następujących wyników dla przejrzystości.

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

Gratulacje! Pomyślnie skompilowano model uczenia maszynowego na potrzeby zalecanych filmów. Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) .

## <a name="improve-your-model"></a>Ulepszanie modelu

Istnieje kilka sposobów na zwiększenie wydajności modelu, dzięki czemu można uzyskać dokładniejsze przewidywania.

### <a name="data"></a>Dane

Dodanie więcej danych szkoleniowych, które mają wystarczającą ilość próbek dla każdego użytkownika i identyfikatora filmu, może pomóc w ulepszeniu jakości modelu rekomendacji.

[Krzyżowe sprawdzanie poprawności](../how-to-guides/train-cross-validation-ml-net.md) to technika służąca do oceniania modeli, które losowo dzielą dane na podzestawy (zamiast wyodrębniania danych testowych z zestawu danych, takiego jak w tym samouczku), a także niektóre grupy jako dane dotyczące uczenia i niektóre z tych grup. Ta metoda prowadzi do podzielenia testu pociągowego pod względem jakości modelu.

### <a name="features"></a>Funkcje

W tym samouczku używane są tylko `Features` trzy (`user id`, `movie id`i `rating`), które są udostępniane przez zestaw danych.

Chociaż jest to dobry początek, w rzeczywistości warto dodać inne atrybuty lub `Features` (na przykład wiek, płeć, lokalizację geograficzną itp.), jeśli są one zawarte w zestawie danych. Dodanie bardziej istotnych `Features` informacji może pomóc w zwiększeniu wydajności modelu rekomendacji.

Jeśli nie masz pewności, co `Features` może być najbardziej odpowiednie dla zadania uczenia maszynowego, możesz również skorzystać z funkcji obliczania udziałów funkcji (FCC) i znaczenia wartości [permutacji](../how-to-guides/determine-global-feature-importance-in-model.md), która ml.NET umożliwia odnajdywanie najbardziej wpływ `Features`.

### <a name="algorithm-hyperparameters"></a>Moje parametry algorytmu

Chociaż ML.NET zapewnia dobre domyślne algorytmy szkoleniowe, można dokładniej dostosować wydajność przez zmianę [parametrów](../resources/glossary.md#hyperparameter)algorytmu.

W `Matrix Factorization`przypadku programu można eksperymentować z parametrami, takimi jak [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) i [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) , aby sprawdzić, czy daje on lepsze wyniki.

Na przykład w tym samouczku są dostępne następujące opcje algorytmu:

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

Algorytm factorization Matrix z filtrowaniem do współpracy jest tylko jednym podejściem do wykonywania zaleceń dotyczących filmów. W wielu przypadkach możesz nie mieć dostępnych danych klasyfikacji i mieć tylko historię filmów dostępną dla użytkowników. W innych przypadkach może być więcej niż tylko dane oceny użytkownika.

| Algorytm       | Scenariusz           | Przykład  |
| ------------- |:-------------:| -----:|
| Factorization macierzy klasy 1 | Użyj tego, jeśli masz tylko userId i movieId. Ten styl rekomendacji jest oparty na scenariuszu współsprzedaży lub produktów często kupowanych, co oznacza, że klient będzie polecał klientom zestaw produktów oparty na ich historii zakupów. | [> Wypróbuj](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| Maszyny factorization z obsługą pól | Użyj tego do zaleceń, gdy masz więcej funkcji poza userId, productId i klasyfikacją (na przykład Opis produktu lub cena produktu). Ta metoda używa również podejścia do filtrowania wspólnie. | [> Wypróbuj](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a>Nowy scenariusz użytkownika

Jednym z typowych problemów w filtrowaniu do współpracy jest problem z zimnym rozpoczęciem, który jest przeznaczony dla nowego użytkownika, który nie ma żadnych poprzednich danych do rysowania wniosków z. Ten problem jest często rozwiązywany przez zaproszenie nowych użytkowników o utworzenie profilu, a na przykład ocenianie filmów, które pojawiły się w przeszłości. Chociaż ta metoda nakłada pewne obciążenie dla użytkownika, zapewnia pewne dane wyjściowe dla nowych użytkowników bez historii klasyfikacji.

## <a name="resources"></a>Zasoby

Dane używane w tym samouczku pochodzą z [zestawu danych MovieLens](http://files.grouplens.org/datasets/movielens/).

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
> * Wybierz algorytm uczenia maszynowego
> * Przygotowywanie i ładowanie danych
> * Kompilowanie i uczenie modelu
> * Oceń model
> * Wdrażanie i korzystanie z modelu

Przejdź do następnego samouczka, aby dowiedzieć się więcej
> [!div class="nextstepaction"]
> [Analiza tonacji](sentiment-analysis.md)
