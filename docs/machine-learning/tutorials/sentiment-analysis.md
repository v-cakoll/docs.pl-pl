---
title: 'Samouczek: Analizowanie komentarzy witryny sieci Web — klasyfikacja binarna'
description: W tym samouczku przedstawiono sposób tworzenia aplikacji konsolowej .NET Core, która klasyfikuje tonacji z komentarzy w witrynie sieci Web i podejmuje odpowiednie działania. Użycie C# binarnego klasyfikatora tonacji w programie Visual Studio.
ms.date: 05/13/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: f89174204c13b907db5a41ed374e1a31c61dcf11
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929027"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a>Samouczek: Analizuj tonacji komentarzy witryny internetowej za pomocą klasyfikacji binarnej w ML.NET

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

- [Program Visual Studio 2017 15,6 lub nowszy](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core

- [UCI tonacji — zestaw danych zdań z etykietą](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (Plik ZIP)

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. Utwórz **aplikację konsolową .NET Core** o nazwie "SentimentAnalysis".

2. Utwórz katalog o nazwie *dane* w projekcie, aby zapisać pliki zestawu danych.

3. Zainstaluj **pakiet NuGet Microsoft.ml**:

    W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, a następnie wybierz kartę **przeglądanie** . Wyszukaj pozycję **Microsoft.ml**, wybierz żądany pakiet, a następnie wybierz przycisk **Instaluj** . Kontynuuj instalację, zgadzając się z postanowieniami licencyjnymi dotyczącymi wybranego pakietu. Wykonaj te same czynności dla pakietu NuGet **Microsoft. ml. FastTree** .

## <a name="prepare-your-data"></a>Przygotowywanie danych

> [!NOTE]
> Zestawy danych dla tego samouczka pochodzą z grupy "from do poszczególnych etykiet przy użyciu funkcji głębokiej", Kotzias et. Al,. KDD 2015 i hostowana w repozytorium Machine Learning/Dua, D. i Karra Taniskidou, E. (2017). /Na Machine Learning repozytorium http://archive.ics.uci.edu/ml []. Irvine, CA: University of Kalifornii, szkolna informacja i nauka komputerowe.

1. Pobierz [UCI tonacji oznaczone zdaniami w pliku zip](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)i rozpakuj.

2. Skopiuj plik do utworzonego katalogu *danych.* `yelp_labelled.txt`

3. W Eksplorator rozwiązań kliknij prawym przyciskiem `yelp_labeled.txt` myszy plik i wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.

### <a name="create-classes-and-define-paths"></a>Tworzenie klas i Definiowanie ścieżek

1. Dodaj następujące dodatkowe `using` instrukcje na początku pliku *program.cs* :

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

2. Utwórz dwa pola globalne do przechowywania ostatnio pobranej ścieżki pliku zestawu danych i zapisanej ścieżki pliku modelu:

    - `_dataPath`ma ścieżkę do zestawu danych używanego do uczenia modelu.
    - `_modelPath`ma ścieżkę, w której jest zapisywany model szkolony.

3. Dodaj następujący kod do wiersza bezpośrednio powyżej `Main` metody, aby określić ścieżki:

    [!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

4. Następnie utwórz klasy dla danych wejściowych i prognoz. Dodaj nową klasę do projektu:

    - W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.

    - W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *SentimentData.cs*. Następnie wybierz przycisk **Dodaj** .

5. Plik *SentimentData.cs* zostanie otwarty w edytorze kodu. Dodaj następującą `using` instrukcję na początku *SentimentData.cs*:

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

6. Usuń istniejącą definicję klasy i Dodaj następujący kod, który ma dwie klasy `SentimentData` i `SentimentPrediction`, do pliku *SentimentData.cs* :

    [!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a>Jak dane zostały przygotowane
Wejściowa Klasa DataSet, `SentimentData`, `string` ma dla `bool` komentarzy użytkownika (`SentimentText`) i (`Sentiment`) wartość 1 (pozytywna) lub 0 (ujemna) dla tonacji. Oba pola mają dołączone atrybuty [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) , które opisują kolejność plików danych każdego pola.  Ponadto `Sentiment` właściwość ma atrybut [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) , aby `Label` wyznaczyć go jako pole. Następujący przykładowy plik nie ma wiersza nagłówka i wygląda następująco:

|SentimentText                         |Tonacji (etykieta) |
|--------------------------------------|----------|
|Waitress był nieco wolny w usłudze.|    0     |
|Crust nie jest dobry.                    |    0     |
|Wow... Uwielbiane to miejsce.              |    1     |
|Usługa była bardzo monitem.              |    1     |

`SentimentPrediction`jest klasą przewidywania używaną po przekształceniu modelu. Dziedziczy po `SentimentData` , tak aby dane wejściowe `SentimentText` mogły być wyświetlane wraz z przewidywaniam danych wyjściowych. Wartość logiczna jest wartością przewidywalną przez model, gdy jest dostarczany z nowymi danymi wejściowymi `SentimentText`. `Prediction`

Klasa `SentimentPrediction` Output zawiera dwie inne właściwości obliczone przez model: `Score` — nieprzetworzony wynik obliczony przez model i `Probability` -wynik uzyskany do prawdopodobieństwa, że tekst ma dodatnie tonacji.

W tym samouczku najważniejszym właściwość jest `Prediction`.

## <a name="load-the-data"></a>Ładowanie danych
Dane w ML.NET są reprezentowane jako [Klasa IDataView](xref:Microsoft.ML.IDataView). `IDataView`to elastyczny i wydajny sposób opisywania danych tabelarycznych (liczbowych i tekstowych). Dane można ładować z pliku tekstowego lub w czasie rzeczywistym (na przykład bazy danych SQL lub plików dziennika) do `IDataView` obiektu.

[Klasa MLContext](xref:Microsoft.ML.MLContext) jest punktem początkowym dla wszystkich operacji ml.NET. Inicjowanie `mlContext` tworzy nowe środowisko ml.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest to podobne, pojęciowo do `DBContext` w Entity Framework.

Przygotujesz aplikację, a następnie załadujesz dane:

1. Zastąp `Main` wiersz w metodzie poniższym kodem, aby zadeklarować i zainicjować zmienną mlContext: `Console.WriteLine("Hello World!")`

    [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

2. Dodaj następujący kod jako następny wiersz kodu w `Main()` metodzie:

    [!code-csharp[CallLoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

3. Utwórz metodę, tuż po metodzie, przy użyciu następującego kodu: `Main()` `LoadData()`

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    `LoadData()` Metoda wykonuje następujące zadania:

    - Ładuje dane.
    - Dzieli załadowany zestaw danych na pociąg i testowe zestawy danych.
    - Zwraca zestawienie pociągów i testów zestawu danych.

4. Dodaj następujący kod jako pierwszy wiersz `LoadData()` metody:

    [!code-csharp[LoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

    [LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczytuje w pliku. Przyjmuje zmienne ścieżki danych i zwraca `IDataView`.

### <a name="split-the-dataset-for-model-training-and-testing"></a>Podziel zestaw danych na potrzeby szkolenia i testowania modelu

Podczas przygotowywania modelu należy użyć części zestawu danych, aby szkolić i części zestawu danych w celu przetestowania dokładności modelu.

1. Aby podzielić dane załadowane do wymaganych zestawów danych, Dodaj następujący kod jako następny wiersz w `LoadData()` metodzie:

    [!code-csharp[SplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

    Poprzedni kod używa metody [TrainTestSplit ()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) , aby podzielić załadowany zestaw danych na pociąg i test zestawy danych i zwrócić je w klasie [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) . Określ wartość procentową zestawu testów dla danych z `testFraction`parametrem. Wartość domyślna to 10%, w tym przypadku do obliczenia większej ilości danych służy 20%.

2. Zwróć na końcu `LoadData()`metody: `splitDataView`

    [!code-csharp[ReturnSplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a>Kompilowanie i uczenie modelu

1. Dodaj następujące wywołanie do `BuildAndTrainModel`metody jako następny wiersz kodu `Main()` w metodzie:

    [!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

    `BuildAndTrainModel()` Metoda wykonuje następujące zadania:

    - Wyodrębnia i przekształca dane.
    - Pociąga za siebie model.
    - Przewidywania tonacji na podstawie danych testowych.
    - Zwraca model.

2. Utwórz metodę, tuż po metodzie, przy użyciu następującego kodu: `Main()` `BuildAndTrainModel()`

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a>Wyodrębnij i Przekształć dane

1. Wywołaj `FeaturizeText` jako następny wiersz kodu:

    [!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

    Metoda w poprzednim kodzie konwertuje kolumnę tekstową (`SentimentText`) na kolumnę typu `Features` wartości liczbowej używanej przez algorytm uczenia maszynowego i dodaje ją jako nową kolumnę zestawu danych: `FeaturizeText()`

    |SentimentText                         |Tonacji |Funkcje              |
    |--------------------------------------|----------|----------------------|
    |Waitress był nieco wolny w usłudze.|    0     |[0,76, 0,65, 0,44,...] |
    |Crust nie jest dobry.                    |    0     |[0,98, 0,43, 0,54,...] |
    |Wow... Uwielbiane to miejsce.              |    1     |[0,35, 0,73, 0,46,...] |
    |Usługa była bardzo monitem.              |    1     |[0,39, 0, 0,75,...]    |

### <a name="add-a-learning-algorithm"></a>Dodawanie algorytmu uczenia

Ta aplikacja używa algorytmu klasyfikacji, który klasyfikuje elementy lub wiersze danych. Aplikacja klasyfikuje Komentarze witryny sieci Web jako wartość dodatnią lub ujemną, więc Użyj zadania klasyfikacji binarnej.

Dołącz zadanie uczenia maszynowego do definicji transformacji danych, dodając następujący kod jako następny wiersz kodu w `BuildAndTrainModel()`:

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) jest algorytmem szkoleniowym klasyfikacji. Ta wartość jest dołączana `estimator` do i akceptuje featurized `SentimentText` (`Features`) i `Label` parametry wejściowe, aby poznać dane historyczne.

### <a name="train-the-model"></a>Uczenie modelu

Dopasuj model do `splitTrainSet` danych i zwróć przeszkolony model, dodając następujący kod jako następny wiersz kodu `BuildAndTrainModel()` w metodzie:

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

Metoda [dopasowywania ()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) pociąga za siebie model poprzez transformowanie zestawu danych i zastosowanie szkolenia.

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Zwróć model przeszkolony do użycia na potrzeby oceny

 Zwróć model na końcu `BuildAndTrainModel()` metody:

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a>Oceń model

Po przeszkoleniu modelu Użyj danych testowych, aby sprawdzić wydajność modelu.

1. Utwórz metodę, tuż po `BuildAndTrainModel()`, przy użyciu następującego kodu: `Evaluate()`

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    `Evaluate()` Metoda wykonuje następujące zadania:

    - Ładuje zestaw danych testowych.
    - Tworzy ewaluatora BinaryClassification.
    - Oblicza model i tworzy metryki.
    - Wyświetla metryki.

2. Dodaj wywołanie do nowej metody z `Main()` metody, bezpośrednio `BuildAndTrainModel()` pod wywołaniem metody, przy użyciu następującego kodu:

    [!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

3. Przekształć `Evaluate()`dane, dodając następujący kod do: `splitTestSet`

    [!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

    Poprzedni kod używa metody [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) do przeprowadzania prognoz dla wielu podanych danych wejściowych dla testu zestawu danych.

4. Oceń model poprzez dodanie następujących elementów jako następny wiersz kodu w `Evaluate()` metodzie:

    [!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

Gdy posiadasz zestaw predykcyjny (`predictions`), Metoda [oceny ()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) ocenia model, który porównuje wartości przewidywane z wartością rzeczywistą `Labels` w testowym zestawie danych i zwraca [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) Obiekt, na którym działa model.

### <a name="displaying-the-metrics-for-model-validation"></a>Wyświetlanie metryk na potrzeby walidacji modelu

Użyj następującego kodu, aby wyświetlić metryki:

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

- `Accuracy` Metryka pobiera dokładność modelu, który jest proporcją prawidłowych prognoz w zestawie testów.

- `AreaUnderRocCurve` Metryka wskazuje, jak pewność, że model prawidłowo klasyfikuje klasy dodatnie i ujemne. Ma `AreaUnderRocCurve` być tak blisko jednego, jak to możliwe.

- Metryka pobiera wynik F1 modelu, który jest miarą równowagi między [dokładnością](../resources/glossary.md#precision) i [odwołaniem.](../resources/glossary.md#recall) `F1Score`  Ma `F1Score` być tak blisko jednego, jak to możliwe.

### <a name="predict-the-test-data-outcome"></a>Przewidywanie wyniku danych testowych

1. Utwórz metodę, tuż po metodzie, przy użyciu następującego kodu: `Evaluate()` `UseModelWithSingleItem()`

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    `UseModelWithSingleItem()` Metoda wykonuje następujące zadania:

    - Tworzy pojedynczy komentarz dotyczący danych testowych.
    - Przewidywania tonacji na podstawie danych testowych.
    - Łączy dane testowe i prognozy na potrzeby raportowania.
    - Wyświetla przewidywane wyniki.

2. Dodaj wywołanie do nowej metody z `Main()` metody, bezpośrednio `Evaluate()` pod wywołaniem metody, przy użyciu następującego kodu:

    [!code-csharp[CallUseModelWithSingleItem](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. Dodaj następujący kod, aby utworzyć jako pierwszy wiersz w `UseModelWithSingleItem()` metodzie:

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest WYGODNYm interfejsem API, który pozwala na przekazywanie danych, a następnie wykonywanie prognozowania na jednym wystąpieniu.

4. Dodaj komentarz, aby przetestować prognozę przeszkolonego modelu w `UseModelWithSingleItem()` metodzie, tworząc `SentimentData`wystąpienie:

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. Przekaż dane komentarza testowego do `Prediction Engine` elementu przez dodanie następujących elementów jako następnych wierszy kodu `UseModelWithSingleItem()` w metodzie:

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

    Funkcja [przewidywania ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) dokonuje prognozowania dla pojedynczego wiersza danych.

6. Wyświetlaj `SentimentText` i odpowiadaj prognozie tonacji przy użyciu następującego kodu:

    [!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a>Używanie modelu do przewidywania

### <a name="deploy-and-predict-batch-items"></a>Wdrażanie i prognozowanie elementów wsadowych

1. Utwórz metodę, tuż po metodzie, przy użyciu następującego kodu: `UseModelWithSingleItem()` `UseModelWithBatchItems()`

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    `UseModelWithBatchItems()` Metoda wykonuje następujące zadania:

    - Tworzy dane testów wsadowych.
    - Przewidywania tonacji na podstawie danych testowych.
    - Łączy dane testowe i prognozy na potrzeby raportowania.
    - Wyświetla przewidywane wyniki.

2. Dodaj wywołanie do nowej metody z `Main` metody, bezpośrednio `UseModelWithSingleItem()` pod wywołaniem metody, przy użyciu następującego kodu:

    [!code-csharp[CallPredictModelBatchItems](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. Dodaj komentarze, aby przetestować przewidywania modeli przeszkolonych w `UseModelWithBatchItems()` metodzie:

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a>Tonacji komentarz przewidywania

Użyj modelu, aby przewidzieć tonacji danych komentarzy przy użyciu metody [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) :

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a>Łączenie i wyświetlanie prognoz

Utwórz nagłówek dla prognoz przy użyciu następującego kodu:

[!code-csharp[OutputHeaders](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

Ponieważ `SentimentPrediction` jest dziedziczona z `SentimentData`, `Transform()` Metoda jest wypełniana `SentimentText` polami przewidywanymi. Gdy proces ML.NET przetwarza, każdy składnik dodaje kolumny, co ułatwia wyświetlanie wyników:

[!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

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

Kompilowanie udanych modeli jest procesem iteracyjnym. Ten model ma wstępną niższą jakość, ponieważ samouczek używa małych zestawów danych w celu zapewnienia szybkiego szkolenia modeli. Jeśli jakość modelu jest niezadowalająca, możesz spróbować go ulepszyć, dostarczając większe zestawy danych szkoleniowych lub wybierając różne algorytmy szkoleniowe z różnymi [parametrami funkcji Hyper-Parameters](../resources/glossary.md##hyperparameter) dla każdego algorytmu.

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
