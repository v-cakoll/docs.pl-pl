---
title: 'Samouczek: analizowanie komentarzy witryny sieci Web — klasyfikacja binarna'
description: W tym samouczku przedstawiono sposób tworzenia aplikacji konsolowej .NET Core, która klasyfikuje tonacji z komentarzy w witrynie sieci Web i podejmuje odpowiednie działania. Użycie C# binarnego klasyfikatora tonacji w programie Visual Studio.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 47b9a9fe37cbcacab3797ed7fb1398b0c524d746
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78241133"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a>Samouczek: analizowanie tonacji komentarzy w witrynie sieci Web za pomocą klasyfikacji binarnej w ML.NET

W tym samouczku przedstawiono sposób tworzenia aplikacji konsolowej .NET Core, która klasyfikuje tonacji z komentarzy w witrynie sieci Web i podejmuje odpowiednie działania. Użycie C# binarnego klasyfikatora tonacji w programie Visual Studio 2017.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Tworzenie aplikacji konsolowej
> - Przygotowywanie danych
> - Ładowanie danych
> - Kompilowanie i uczenie modelu
> - Oceń model
> - Tworzenie prognoz przy użyciu modelu
> - Zobacz wyniki

Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) .

## <a name="prerequisites"></a>Wymagania wstępne

- [Program Visual Studio 2017 w wersji 15,6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core

- [UCI tonacji z etykietą zestawu danych](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (plik zip)

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. Utwórz **aplikację konsolową .NET Core** o nazwie "SentimentAnalysis".

2. Utwórz katalog o nazwie *dane* w projekcie, aby zapisać pliki zestawu danych.

3. Zainstaluj **pakiet NuGet Microsoft.ml**:

    W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, a następnie wybierz kartę **Przeglądaj** . wyszukaj pozycję **Microsoft.ml**, wybierz pakiet, a następnie wybierz przycisk **Instaluj** . Kontynuuj instalację, zgadzając się z postanowieniami licencyjnymi dotyczącymi wybranego pakietu. Wykonaj te same czynności dla pakietu NuGet **Microsoft. ml. FastTree** .

## <a name="prepare-your-data"></a>Przygotowywanie danych

> [!NOTE]
> Zestawy danych dla tego samouczka pochodzą z grupy "from do poszczególnych etykiet przy użyciu funkcji głębokiej", Kotzias et. Al,. KDD 2015 i hostowana w repozytorium Machine Learning/Dua, D. i Karra Taniskidou, E. (2017). /Na Machine Learning repozytorium [http://archive.ics.uci.edu/ml]. Irvine, CA: University of Kalifornii, szkolna informacja i nauka komputera.

1. Pobierz [UCI tonacji oznaczone zdaniami w pliku zip](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)i rozpakuj.

2. Skopiuj plik `yelp_labelled.txt` do utworzonego katalogu *danych* .

3. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy plik `yelp_labeled.txt` i wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.

### <a name="create-classes-and-define-paths"></a>Tworzenie klas i Definiowanie ścieżek

1. Dodaj następujące dodatkowe instrukcje `using` na początku pliku *program.cs* :

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddUsings "Add necessary usings")]

1. Dodaj następujący kod do wiersza bezpośrednio powyżej metody `Main`, aby utworzyć pole do przechowywania niedawno pobranej ścieżki pliku zestawu danych:

    [!code-csharp[Declare global variables](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

1. Następnie utwórz klasy dla danych wejściowych i prognoz. Dodaj nową klasę do projektu:

    - W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz pozycję **Dodaj** > **nowy element**.

    - W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *SentimentData.cs*. Następnie wybierz przycisk **Dodaj** .

1. Plik *SentimentData.cs* zostanie otwarty w edytorze kodu. Dodaj następującą instrukcję `using` na początku *SentimentData.cs*:

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#AddUsings "Add necessary usings")]

1. Usuń istniejącą definicję klasy i Dodaj następujący kod, który ma dwie klasy `SentimentData` i `SentimentPrediction`, do pliku *SentimentData.cs* :

    [!code-csharp[DeclareTypes](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a>Jak dane zostały przygotowane

Wejściowa Klasa zestawu danych, `SentimentData`, ma `string` dla komentarzy użytkownika (`SentimentText`) i wartość `bool` (`Sentiment`) równa 1 (dodatnia) lub 0 (ujemna) dla tonacji. Oba pola mają dołączone atrybuty [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) , które opisują kolejność plików danych każdego pola.  Ponadto Właściwość `Sentiment` ma atrybut [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) służący do wyznaczania go jako pola `Label`. Następujący przykładowy plik nie ma wiersza nagłówka i wygląda następująco:

|SentimentText                         |Tonacji (etykieta) |
|--------------------------------------|----------|
|Waitress był nieco wolny w usłudze.|    0     |
|Crust nie jest dobry.                    |    0     |
|Wow... Uwielbiane to miejsce.              |    1     |
|Usługa była bardzo monitem.              |    1     |

`SentimentPrediction` jest klasą przewidywania używaną po przekształceniu modelu. Dziedziczy po `SentimentData`, aby można było wyświetlić `SentimentText` wejściowe wraz z prognozą wyjściową. Wartość logiczna `Prediction` jest wartością przewidywalną przez model, gdy jest dostarczany z nowym `SentimentText`wejściowym.

Klasa wyjściowa `SentimentPrediction` zawiera dwie inne właściwości obliczone przez model: `Score` — nieprzetworzony wynik obliczony przez model i `Probability` — wynik uzyskany do prawdopodobieństwa, że tekst ma pozytywny tonacji.

W tym samouczku najważniejszym właściwością jest `Prediction`.

## <a name="load-the-data"></a>Ładowanie danych

Dane w ML.NET są reprezentowane jako [Klasa IDataView](xref:Microsoft.ML.IDataView). `IDataView` to elastyczny i wydajny sposób opisywania danych tabelarycznych (liczbowych i tekstowych). Dane można ładować z pliku tekstowego lub w czasie rzeczywistym (na przykład bazy danych SQL lub plików dziennika) do obiektu `IDataView`.

[Klasa MLContext](xref:Microsoft.ML.MLContext) jest punktem początkowym dla wszystkich operacji ml.NET. Inicjowanie `mlContext` tworzy nowe środowisko ML.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest to podobne, pojęciowo, aby `DBContext` w Entity Framework.

Przygotujesz aplikację, a następnie załadujesz dane:

1. Zastąp wiersz `Console.WriteLine("Hello World!")` w metodzie `Main` następującym kodem, aby zadeklarować i zainicjować zmienną mlContext:

    [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateMLContext "Create the ML Context")]

2. Dodaj następujący kod jako następny wiersz kodu w metodzie `Main()`:

    [!code-csharp[CallLoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallLoadData)]

3. Utwórz metodę `LoadData()` po prostu po metodzie `Main()`, używając następującego kodu:

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    Metoda `LoadData()` wykonuje następujące zadania:

    - Ładuje dane.
    - Dzieli załadowany zestaw danych na pociąg i testowe zestawy danych.
    - Zwraca zestawienie pociągów i testów zestawu danych.

4. Dodaj następujący kod jako pierwszy wiersz metody `LoadData()`:

    [!code-csharp[LoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#LoadData "loading dataset")]

    [LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczytuje w pliku. Przyjmuje zmienne ścieżki danych i zwraca `IDataView`.

### <a name="split-the-dataset-for-model-training-and-testing"></a>Podziel zestaw danych na potrzeby szkolenia i testowania modelu

Podczas przygotowywania modelu należy użyć części zestawu danych, aby szkolić i części zestawu danych w celu przetestowania dokładności modelu.

1. Aby podzielić dane załadowane do wymaganych zestawów danych, Dodaj następujący kod jako następny wiersz w `LoadData()` metodzie:

    [!code-csharp[SplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#SplitData "Split the Data")]

    Poprzedni kod używa metody [TrainTestSplit ()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) , aby podzielić załadowany zestaw danych na pociąg i test zestawy danych i zwrócić je w klasie [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) . Określ wartość procentową zestawu testów z parametrem `testFraction`. Wartość domyślna to 10%, w tym przypadku do obliczenia większej ilości danych służy 20%.

2. Zwróć `splitDataView` na końcu metody `LoadData()`:

    [!code-csharp[ReturnSplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a>Kompilowanie i uczenie modelu

1. Dodaj następujące wywołanie do metody `BuildAndTrainModel`jako następny wiersz kodu w metodzie `Main()`:

    [!code-csharp[CallBuildAndTrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallBuildAndTrainModel)]

    Metoda `BuildAndTrainModel()` wykonuje następujące zadania:

    - Wyodrębnia i przekształca dane.
    - Pociąga za siebie model.
    - Przewidywania tonacji na podstawie danych testowych.
    - Zwraca model.

2. Utwórz metodę `BuildAndTrainModel()` po prostu po metodzie `Main()`, używając następującego kodu:

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a>Wyodrębnij i Przekształć dane

1. Wywołaj `FeaturizeText` jako następny wiersz kodu:

    [!code-csharp[FeaturizeText](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#FeaturizeText "Featurize the text")]

    Metoda `FeaturizeText()` w poprzednim kodzie konwertuje kolumnę tekstową (`SentimentText`) na typ klucza numerycznego `Features` kolumny używanej przez algorytm uczenia maszynowego i dodaje ją jako nową kolumnę zestawu danych:

    |SentimentText                         |Opinia |Funkcje              |
    |--------------------------------------|----------|----------------------|
    |Waitress był nieco wolny w usłudze.|    0     |[0,76, 0,65, 0,44,...] |
    |Crust nie jest dobry.                    |    0     |[0,98, 0,43, 0,54,...] |
    |Wow... Uwielbiane to miejsce.              |    1     |[0,35, 0,73, 0,46,...] |
    |Usługa była bardzo monitem.              |    1     |[0,39, 0, 0,75,...]    |

### <a name="add-a-learning-algorithm"></a>Dodawanie algorytmu uczenia

Ta aplikacja używa algorytmu klasyfikacji, który klasyfikuje elementy lub wiersze danych. Aplikacja klasyfikuje Komentarze witryny sieci Web jako wartość dodatnią lub ujemną, więc Użyj zadania klasyfikacji binarnej.

Dołącz zadanie uczenia maszynowego do definicji transformacji danych, dodając następujący kod jako następny wiersz kodu w `BuildAndTrainModel()`:

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) jest algorytmem szkoleniowym klasyfikacji. Ta wartość jest dołączana do `estimator` i akceptuje featurized `SentimentText` (`Features`) i `Label` parametrów wejściowych, aby poznać dane historyczne.

### <a name="train-the-model"></a>Uczenie modelu

Dopasuj model do danych `splitTrainSet` i zwróć przeszkolony model, dodając następujący kod jako następny wiersz kodu w metodzie `BuildAndTrainModel()`:

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TrainModel "Train the model")]

Metoda [dopasowywania ()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) pociąga za siebie model poprzez transformowanie zestawu danych i zastosowanie szkolenia.

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Zwróć model przeszkolony do użycia na potrzeby oceny

 Zwróć model na końcu metody `BuildAndTrainModel()`:

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a>Oceń model

Po przeszkoleniu modelu Użyj danych testowych, aby sprawdzić wydajność modelu.

1. Utwórz metodę `Evaluate()`, zaraz po `BuildAndTrainModel()`, przy użyciu następującego kodu:

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    Metoda `Evaluate()` wykonuje następujące zadania:

    - Ładuje zestaw danych testowych.
    - Tworzy ewaluatora BinaryClassification.
    - Oblicza model i tworzy metryki.
    - Wyświetla metryki.

2. Dodaj wywołanie do nowej metody z metody `Main()`, bezpośrednio pod wywołaniem metody `BuildAndTrainModel()`, przy użyciu następującego kodu:

    [!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallEvaluate "Call the Evaluate method")]

3. Przekształć `splitTestSet` dane, dodając następujący kod do `Evaluate()`:

    [!code-csharp[PredictWithTransformer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TransformData "Predict using the Transformer")]

    Poprzedni kod używa metody [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) do przeprowadzania prognoz dla wielu podanych danych wejściowych dla testu zestawu danych.

4. Oceń model, dodając następujący kod jako następny wiersz kodu w metodzie `Evaluate()`:

    [!code-csharp[ComputeMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Evaluate "Compute Metrics")]

Po zastosowaniu zestawu prognozowania (`predictions`) Metoda [oceny ()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) ocenia model, który porównuje wartości przewidywane z rzeczywistym `Labels` w zestawie danych testów i zwraca obiekt [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) , w jaki działa model.

### <a name="displaying-the-metrics-for-model-validation"></a>Wyświetlanie metryk na potrzeby walidacji modelu

Użyj następującego kodu, aby wyświetlić metryki:

[!code-csharp[DisplayMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayMetrics "Display selected metrics")]

- Metryka `Accuracy` pobiera dokładność modelu, który jest proporcją prawidłowych prognoz w zestawie testów.

- Metryka `AreaUnderRocCurve` wskazuje, jak pewność, że model prawidłowo klasyfikuje klasy dodatnie i ujemne. Chcesz, aby `AreaUnderRocCurve` się jak najbliżej jednego z nich.

- Metryka `F1Score` pobiera wynik F1 modelu, który jest miarą równowagi między [dokładnością](../resources/glossary.md#precision) i [odwołaniem](../resources/glossary.md#recall).  Chcesz, aby `F1Score` się jak najbliżej jednego z nich.

### <a name="predict-the-test-data-outcome"></a>Przewidywanie wyniku danych testowych

1. Utwórz metodę `UseModelWithSingleItem()` po prostu po metodzie `Evaluate()`, używając następującego kodu:

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    Metoda `UseModelWithSingleItem()` wykonuje następujące zadania:

    - Tworzy pojedynczy komentarz dotyczący danych testowych.
    - Przewidywania tonacji na podstawie danych testowych.
    - Łączy dane testowe i prognozy na potrzeby raportowania.
    - Wyświetla przewidywane wyniki.

2. Dodaj wywołanie do nowej metody z metody `Main()`, bezpośrednio pod wywołaniem metody `Evaluate()`, przy użyciu następującego kodu:

    [!code-csharp[CallUseModelWithSingleItem](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. Dodaj następujący kod, aby utworzyć jako pierwszy wiersz w metodzie `UseModelWithSingleItem()`:

    [!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest WYGODNYm interfejsem API, który umożliwia prognozowanie jednego wystąpienia danych. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nie jest bezpieczna wątkowo. Jest to możliwe do użycia w środowiskach wielowątkowych lub prototypowych. Aby zwiększyć wydajność i bezpieczeństwo wątków w środowiskach produkcyjnych, Użyj usługi `PredictionEnginePool`, która tworzy [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) obiektów do użycia w całej aplikacji. Zapoznaj się z tym przewodnikiem dotyczącym [korzystania z `PredictionEnginePool` w ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

    > [!NOTE]
    > rozszerzenie usługi `PredictionEnginePool` jest obecnie w wersji zapoznawczej.

4. Dodaj komentarz, aby przetestować prognozę przeszkolonego modelu w metodzie `UseModelWithSingleItem()`, tworząc wystąpienie `SentimentData`:

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. Przekaż dane komentarzy testowych do [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) przez dodanie następujących elementów jako następnych wierszy kodu w metodzie `UseModelWithSingleItem()`:

    [!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Predict "Create a prediction of sentiment")]

    Funkcja [przewidywania ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) dokonuje prognozowania dla pojedynczego wiersza danych.

6. Wyświetl `SentimentText` i odpowiadające przewidywania tonacji przy użyciu następującego kodu:

    [!code-csharp[OutputPrediction](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a>Używanie modelu do przewidywania

### <a name="deploy-and-predict-batch-items"></a>Wdrażanie i prognozowanie elementów wsadowych

1. Utwórz metodę `UseModelWithBatchItems()` po prostu po metodzie `UseModelWithSingleItem()`, używając następującego kodu:

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    Metoda `UseModelWithBatchItems()` wykonuje następujące zadania:

    - Tworzy dane testów wsadowych.
    - Przewidywania tonacji na podstawie danych testowych.
    - Łączy dane testowe i prognozy na potrzeby raportowania.
    - Wyświetla przewidywane wyniki.

2. Dodaj wywołanie do nowej metody z metody `Main`, bezpośrednio pod wywołaniem metody `UseModelWithSingleItem()`, przy użyciu następującego kodu:

    [!code-csharp[CallPredictModelBatchItems](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. Dodaj komentarze, aby przetestować przewidywania modeli przeszkolonych w `UseModelWithBatchItems()` metodzie:

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a>Tonacji komentarz przewidywania

Użyj modelu, aby przewidzieć tonacji danych komentarzy przy użyciu metody [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) :

[!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a>Łączenie i wyświetlanie prognoz

Utwórz nagłówek dla prognoz przy użyciu następującego kodu:

[!code-csharp[OutputHeaders](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddInfoMessage "Display prediction outputs")]

Ponieważ `SentimentPrediction` jest dziedziczona po `SentimentData`, Metoda `Transform()` zapełniona `SentimentText` z przewidywanymi polami. Gdy proces ML.NET przetwarza, każdy składnik dodaje kolumny, co ułatwia wyświetlanie wyników:

[!code-csharp[DisplayPredictions](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a>Wyniki

Wyniki powinny wyglądać podobnie do poniższego. Podczas przetwarzania wyświetlane są komunikaty. Mogą pojawić się ostrzeżenia lub przetwarzanie komunikatów. Zostały one usunięte z następujących wyników dla przejrzystości.

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 83.96%
Auc: 90.51%
F1Score: 84.04%

=============== End of model evaluation ===============

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This was a very bad steak | Prediction: Negative | Probability: 0.1027377
=============== End of Predictions ===============

=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This was a horrible meal | Prediction: Negative | Probability: 0.1369192
Sentiment: I love this spaghetti. | Prediction: Positive | Probability: 0.9960636
=============== End of predictions ===============

=============== End of process ===============
Press any key to continue . . .

```

Gratulacje! Pomyślnie skompilowano model uczenia maszynowego do klasyfikowania i przewidywania komunikatów tonacji.

Kompilowanie udanych modeli jest procesem iteracyjnym. Ten model ma wstępną niższą jakość, ponieważ samouczek używa małych zestawów danych w celu zapewnienia szybkiego szkolenia modeli. Jeśli jakość modelu jest niezadowalająca, możesz spróbować go ulepszyć, dostarczając większe zestawy danych szkoleniowych lub wybierając różne algorytmy szkoleniowe z różnymi [parametrami funkcji Hyper-Parameters](../resources/glossary.md#hyperparameter) dla każdego algorytmu.

Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) .

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Tworzenie aplikacji konsolowej
> - Przygotowywanie danych
> - Ładowanie danych
> - Kompilowanie i uczenie modelu
> - Oceń model
> - Tworzenie prognoz przy użyciu modelu
> - Zobacz wyniki

Przejdź do następnego samouczka, aby dowiedzieć się więcej
> [!div class="nextstepaction"]
> [Klasyfikacja problemu](github-issue-classification.md)
