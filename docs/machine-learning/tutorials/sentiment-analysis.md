---
title: 'Samouczek: Analizowanie komentarzy na stronie internetowej - klasyfikacja binarna'
description: W tym samouczku pokazano, jak utworzyć aplikację konsoli .NET Core, która klasyfikuje tonacji z komentarzy do witryny sieci Web i wykonuje odpowiednie działania. Klasyfikator tonacji binarnych używa języka C# w programie Visual Studio.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 47b9a9fe37cbcacab3797ed7fb1398b0c524d746
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241133"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a>Samouczek: Analizuj nastroje komentarzy na stronie internetowej z klasyfikacją binarną w ML.NET

W tym samouczku pokazano, jak utworzyć aplikację konsoli .NET Core, która klasyfikuje tonacji z komentarzy do witryny sieci Web i wykonuje odpowiednie działania. Klasyfikator tonacji binarnych używa języka C# w programie Visual Studio 2017.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Tworzenie aplikacji konsolowej
> - Przygotowywanie danych
> - Ładowanie danych
> - Zbuduj i wytrenuj model
> - Ocena modelu
> - Użyj modelu, aby dokonać przewidywania
> - Zobacz wyniki

Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis)

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2017 w wersji 15.6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym obciążeniem ".NET Core cross-platform development"

- [Zestaw danych zdań oznaczonych etykietami UCI](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (plik ZIP)

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. Utwórz **aplikację .NET Core Console** o nazwie "SentimentAnalysis".

2. Utwórz katalog o nazwie *Dane* w projekcie, aby zapisać pliki zestawu danych.

3. Zainstaluj **pakiet Microsoft.ML NuGet:**

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **polecenie Zarządzaj pakietami NuGet**. Wybierz "nuget.org" jako źródło pakietu, a następnie wybierz kartę **Przeglądaj.** Wyszukaj **Microsoft.ML**wybierz odpowiedni pakiet, a następnie wybierz przycisk **Zainstaluj.** Kontynuuj instalację, zgadzając się na warunki licencyjne dla wybranego pakietu. Zrób to samo dla pakietu **Microsoft.ML.FastTree** NuGet.

## <a name="prepare-your-data"></a>Przygotowywanie danych

> [!NOTE]
> Zestawy danych dla tego samouczka są z "Od grupy do pojedynczych etykiet przy użyciu funkcji głębokich", Kotzias et. Al. KDD 2015 i gościł w UCI Machine Learning Repozytorium - Dua, D. i Karra Taniskidou, E. (2017). Repozytorium uczenia maszynowegohttp://archive.ics.uci.edu/mlUCI [ ]. Irvine, Kalifornia: Uniwersytet Kalifornijski, Szkoła Informacji i Informatyki.

1. Pobierz [plik ZIP zestawu danych UCI Sentiment Labeled Sentences](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)i rozpakuj.

2. Skopiuj `yelp_labelled.txt` plik do utworzonego katalogu *danych.*

3. W Eksploratorze `yelp_labeled.txt` rozwiązań kliknij prawym przyciskiem myszy plik i wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**zmień wartość **kopiuj do katalogu wyjściowego,** aby **skopiować, jeśli nowsza**.

### <a name="create-classes-and-define-paths"></a>Tworzenie klas i definiowanie ścieżek

1. Dodaj następujące `using` dodatkowe instrukcje do górnej części pliku *Program.cs:*

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddUsings "Add necessary usings")]

1. Dodaj następujący kod do wiersza `Main` tuż nad metodą, aby utworzyć pole do przechowywania ostatnio pobranej ścieżki pliku zestawu danych:

    [!code-csharp[Declare global variables](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

1. Następnie utwórz klasy dla danych wejściowych i prognoz. Dodaj nową klasę do projektu:

    - W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.

    - W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *SentimentData.cs*. Następnie wybierz przycisk **Dodaj.**

1. Plik *SentimentData.cs* zostanie otwarty w edytorze kodu. Dodaj następującą `using` instrukcję na górze *SentimentData.cs:*

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#AddUsings "Add necessary usings")]

1. Usuń istniejącą definicję klasy i dodaj następujący `SentimentData` `SentimentPrediction`kod, który ma dwie klasy i , do *pliku SentimentData.cs:*

    [!code-csharp[DeclareTypes](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a>Jak przygotowano dane

Klasa zestawu danych `SentimentData`wejściowych `string` , ma`SentimentText`wartość dla `bool` `Sentiment`komentarzy użytkownika ( ) i ( ) wartość 1 (dodatni) lub 0 (ujemna) dla tonacji. Oba pola mają dołączonych atrybutów [LoadColumn,](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) które opisują kolejność plików danych każdego pola.  Ponadto `Sentiment` właściwość ma [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) atrybut, aby wyznaczyć go jako `Label` pole. Poniższy przykładowy plik nie ma wiersza nagłówka i wygląda następująco:

|SentymentTekst                         |Sentyment (etykieta) |
|--------------------------------------|----------|
|Kelnerka była trochę powolna w służbie.|    0     |
|Skorupa nie jest dobra.                    |    0     |
|Wow... Uwielbiałem to miejsce.              |    1     |
|Obsługa była bardzo szybka.              |    1     |

`SentimentPrediction`jest klasy przewidywania używane po treningu modelu. Dziedziczy `SentimentData` z tak, `SentimentText` że dane wejściowe mogą być wyświetlane wraz z prognozą danych wyjściowych. Wartość `Prediction` logiczna jest wartością, którą model przewiduje `SentimentText`po dostarczeniu z nowym wejściem.

Klasa `SentimentPrediction` danych wyjściowych zawiera dwie inne właściwości `Score` obliczone przez model: - `Probability` wynik raw obliczony przez model oraz - wynik skalibrowany do prawdopodobieństwa, że tekst ma pozytywne nastawienie.

W tym samouczku najważniejszą `Prediction`właściwością jest .

## <a name="load-the-data"></a>Ładowanie danych

Dane w ML.NET jest reprezentowana jako [klasa IDataView](xref:Microsoft.ML.IDataView). `IDataView`to elastyczny i skuteczny sposób opisywania danych tabelarycznych (numerycznych i tekstowych). Dane mogą być ładowane z pliku tekstowego lub w czasie rzeczywistym `IDataView` (na przykład bazy danych SQL lub plików dziennika) do obiektu.

[Klasa MLContext](xref:Microsoft.ML.MLContext) jest punktem wyjścia dla wszystkich operacji ML.NET. Inicjowanie `mlContext` tworzy nowe środowisko ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest to podobne, koncepcyjnie, `DBContext` do w ramach jednostki.

Przygotuj aplikację, a następnie załaduj dane:

1. Zamień `Console.WriteLine("Hello World!")` wiersz `Main` w metodzie na następujący kod, aby zadeklarować i zainicjować zmienną mlContext:

    [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateMLContext "Create the ML Context")]

2. Dodaj następujące jako następny wiersz kodu `Main()` w metodzie:

    [!code-csharp[CallLoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallLoadData)]

3. Utwórz `LoadData()` metodę, tuż `Main()` po tej metodzie, używając następującego kodu:

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    Metoda `LoadData()` wykonuje następujące zadania:

    - Ładuje dane.
    - Dzieli załadowany zestaw danych na zestawy danych pociągu i testów.
    - Zwraca zestawy danych podzielonego pociągu i testu.

4. Dodaj następujący kod jako pierwszy `LoadData()` wiersz metody:

    [!code-csharp[LoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#LoadData "loading dataset")]

    [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczyty w pliku. Przyjmuje zmienne ścieżki danych i `IDataView`zwraca .

### <a name="split-the-dataset-for-model-training-and-testing"></a>Dzielenie zestawu danych do szkolenia i testowania modelu

Podczas przygotowywania modelu, należy użyć części zestawu danych do nauczenia go i część zestawu danych, aby przetestować dokładność modelu.

1. Aby podzielić załadowane dane na potrzebne zestawy danych, dodaj `LoadData()` następujący kod jako następny wiersz w metodzie:

    [!code-csharp[SplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#SplitData "Split the Data")]

    Poprzedni kod używa [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) metoda podzielić załadowany zestaw danych do pociągu i testów zestawów danych i zwrócić je w [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) klasy. Określ procent zestawu testów `testFraction`danych z parametrem. Wartość domyślna to 10%, w tym przypadku do oceny większej liczby danych jest używany chorować na 20%.

2. Zwraca `splitDataView` na końcu `LoadData()` metody:

    [!code-csharp[ReturnSplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a>Zbuduj i wytrenuj model

1. Dodaj następujące wywołanie `BuildAndTrainModel`do metody jako następny `Main()` wiersz kodu w metodzie:

    [!code-csharp[CallBuildAndTrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallBuildAndTrainModel)]

    Metoda `BuildAndTrainModel()` wykonuje następujące zadania:

    - Wyodrębnia i przekształca dane.
    - Trenuje model.
    - Prognozuje tonacji na podstawie danych testowych.
    - Zwraca model.

2. Utwórz `BuildAndTrainModel()` metodę, tuż `Main()` po tej metodzie, używając następującego kodu:

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a>Wyodrębnianie i przekształcanie danych

1. Wywołaj `FeaturizeText` jako następny wiersz kodu:

    [!code-csharp[FeaturizeText](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#FeaturizeText "Featurize the text")]

    Metoda `FeaturizeText()` w poprzednim kodzie konwertuje kolumnę tekstową (`SentimentText`) na kolumnę typu `Features` klucza numerycznego używaną przez algorytm uczenia maszynowego i dodaje ją jako nową kolumnę zestawu danych:

    |SentymentTekst                         |Opinia |Funkcje              |
    |--------------------------------------|----------|----------------------|
    |Kelnerka była trochę powolna w służbie.|    0     |[0.76, 0.65, 0.44, ...] |
    |Skorupa nie jest dobra.                    |    0     |[0.98, 0.43, 0.54, ...] |
    |Wow... Uwielbiałem to miejsce.              |    1     |[0.35, 0.73, 0.46, ...] |
    |Obsługa była bardzo szybka.              |    1     |[0.39, 0, 0.75, ...]    |

### <a name="add-a-learning-algorithm"></a>Dodawanie algorytmu uczenia się

Ta aplikacja używa algorytmu klasyfikacji, który kategoryzuje elementy lub wiersze danych. Aplikacja kategoryzuje komentarze witryny jako pozytywne lub negatywne, więc użyj zadania klasyfikacji binarnej.

Dołącz zadanie uczenia maszynowego do definicji przekształcania danych, dodając następujące `BuildAndTrainModel()`wierszy kodu w:

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) jest algorytm szkolenia klasyfikacji. Jest to dołączone `estimator` do i akceptuje featurized `SentimentText` ( `Label` `Features`) i parametry wejściowe, aby dowiedzieć się z danych historycznych.

### <a name="train-the-model"></a>Uczenie modelu

Dopasuj `splitTrainSet` model do danych i zwróć uczonego modelu, `BuildAndTrainModel()` dodając następujące wierszy kodu w metodzie:

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TrainModel "Train the model")]

[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) Metoda szkoli modelu przez przekształcenie zestawu danych i stosowania szkolenia.

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Powrót modelu przeszkolonego do wykorzystania do oceny

 Zwraca model na końcu `BuildAndTrainModel()` metody:

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a>Ocena modelu

Po uczonego modelu należy użyć danych testowych sprawdź poprawność wydajności modelu.

1. Utwórz `Evaluate()` metodę, `BuildAndTrainModel()`zaraz po , z następującym kodem:

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    Metoda `Evaluate()` wykonuje następujące zadania:

    - Ładuje testowy zestaw danych.
    - Tworzy oceniającego BinaryClassification.
    - Ocenia model i tworzy metryki.
    - Wyświetla metryki.

2. Dodaj wywołanie do nowej `Main()` metody z metody, bezpośrednio w wywołaniu `BuildAndTrainModel()` metody, przy użyciu następującego kodu:

    [!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallEvaluate "Call the Evaluate method")]

3. Przekształć dane, `splitTestSet` dodając `Evaluate()`następujący kod do:

    [!code-csharp[PredictWithTransformer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TransformData "Predict using the Transformer")]

    Poprzedni kod używa [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda do prognozowania dla wielu dostarczonych wierszy wejściowych zestawu danych testowych.

4. Oceń model, dodając następujący wiersz kodu w `Evaluate()` metodzie:

    [!code-csharp[ComputeMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Evaluate "Compute Metrics")]

Po ustawie przewidywanie`predictions`( ), [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) metoda ocenia model, który porównuje przewidywane `Labels` wartości z rzeczywistym w zestawie danych testowych i zwraca [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) obiektu, w jaki sposób model działa.

### <a name="displaying-the-metrics-for-model-validation"></a>Wyświetlanie metryk do sprawdzania poprawności modelu

Użyj następującego kodu, aby wyświetlić metryki:

[!code-csharp[DisplayMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayMetrics "Display selected metrics")]

- Metryka `Accuracy` pobiera dokładność modelu, który jest proporcją poprawnych prognoz w zestawie testów.

- Metryka `AreaUnderRocCurve` wskazuje, jak pewny siebie model poprawnie klasyfikuje klasy dodatnie i ujemne. Chcesz, `AreaUnderRocCurve` aby być jak najbliżej jednego, jak to możliwe.

- Metryka `F1Score` pobiera wynik F1 modelu, który jest miarą równowagi między [precyzją](../resources/glossary.md#precision) a [wycofaniem.](../resources/glossary.md#recall)  Chcesz, `F1Score` aby być jak najbliżej jednego, jak to możliwe.

### <a name="predict-the-test-data-outcome"></a>Przewidywanie wyników danych testowych

1. Utwórz `UseModelWithSingleItem()` metodę, tuż `Evaluate()` po tej metodzie, używając następującego kodu:

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    Metoda `UseModelWithSingleItem()` wykonuje następujące zadania:

    - Tworzy pojedynczy komentarz danych testowych.
    - Prognozuje tonacji na podstawie danych testowych.
    - Łączy dane testowe i prognozy dla raportowania.
    - Wyświetla przewidywane wyniki.

2. Dodaj wywołanie do nowej `Main()` metody z metody, bezpośrednio w wywołaniu `Evaluate()` metody, przy użyciu następującego kodu:

    [!code-csharp[CallUseModelWithSingleItem](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. Dodaj następujący kod do utworzenia jako `UseModelWithSingleItem()` pierwszy wiersz w metodzie:

    [!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest interfejs emanujący interfejsu API wygody, który umożliwia wykonywanie przewidywanie na pojedyncze wystąpienie danych. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny dla nici. Dopuszczalne jest stosowanie w środowiskach jednowątkowych lub prototypowych. Aby zwiększyć wydajność i bezpieczeństwo wątków `PredictionEnginePool` w środowiskach [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) produkcyjnych, należy użyć usługi, która tworzy obiektów [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do użycia w całej aplikacji. Zobacz ten przewodnik, jak [ `PredictionEnginePool` używać w ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

    > [!NOTE]
    > `PredictionEnginePool`rozszerzenie usługi jest obecnie w wersji zapoznawczej.

4. Dodaj komentarz, aby przetestować przewidywanie `UseModelWithSingleItem()` uczonego modelu `SentimentData`w metodzie, tworząc wystąpienie:

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. Przekaż dane komentarza testowego [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do, dodając następujące wiersze `UseModelWithSingleItem()` kodu w metodzie:

    [!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Predict "Create a prediction of sentiment")]

    [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) Funkcja sprawia, że przewidywanie dla pojedynczego wiersza danych.

6. Wyświetlanie `SentimentText` i odpowiednie przewidywanie tonacji przy użyciu następującego kodu:

    [!code-csharp[OutputPrediction](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a>Użyj modelu do przewidywania

### <a name="deploy-and-predict-batch-items"></a>Wdrażanie i przewidywanie elementów wsadowych

1. Utwórz `UseModelWithBatchItems()` metodę, tuż `UseModelWithSingleItem()` po tej metodzie, używając następującego kodu:

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    Metoda `UseModelWithBatchItems()` wykonuje następujące zadania:

    - Tworzy dane testowe partii.
    - Prognozuje tonacji na podstawie danych testowych.
    - Łączy dane testowe i prognozy dla raportowania.
    - Wyświetla przewidywane wyniki.

2. Dodaj wywołanie do nowej `Main` metody z metody, bezpośrednio w wywołaniu `UseModelWithSingleItem()` metody, przy użyciu następującego kodu:

    [!code-csharp[CallPredictModelBatchItems](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. Dodaj kilka komentarzy, aby przetestować prognozy `UseModelWithBatchItems()` uczonego modelu w metodzie:

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a>Przewiduj nastroje komentarzy

Użyj modelu do przewidywania tonacji danych komentarza przy użyciu metody [Transform():](xref:Microsoft.ML.ITransformer.Transform%2A)

[!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a>Łączenie i wyświetlanie prognoz

Utwórz nagłówek dla prognoz przy użyciu następującego kodu:

[!code-csharp[OutputHeaders](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddInfoMessage "Display prediction outputs")]

Ponieważ `SentimentPrediction` jest dziedziczona z `SentimentData`, `Transform()` metoda wypełniona `SentimentText` przewidywanych pól. W miarę ML.NET procesów każdy składnik dodaje kolumny, co ułatwia wyświetlanie wyników:

[!code-csharp[DisplayPredictions](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a>Wyniki

Wyniki powinny być podobne do poniższych. Podczas przetwarzania są wyświetlane komunikaty. Mogą być wyświetlane ostrzeżenia lub wiadomości przetwarzania. Zostały one usunięte z następujących wyników dla jasności.

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

Gratulacje! Teraz pomyślnie skonstruowano model uczenia maszynowego do klasyfikowania i przewidywania tonacji wiadomości.

Budowanie udanych modeli jest procesem iteracyjnym. Ten model ma początkową niższą jakość, ponieważ samouczek używa małych zestawów danych, aby zapewnić szybkie szkolenie modelu. Jeśli nie jesteś zadowolony z jakości modelu, możesz spróbować go poprawić, udostępniając większe zestawy danych szkoleniowych lub wybierając różne algorytmy szkolenia z [różnymi hiperparametrami](../resources/glossary.md#hyperparameter) dla każdego algorytmu.

Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis)

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Tworzenie aplikacji konsolowej
> - Przygotowywanie danych
> - Ładowanie danych
> - Zbuduj i wytrenuj model
> - Ocena modelu
> - Użyj modelu, aby dokonać przewidywania
> - Zobacz wyniki

Przejdź do następnego samouczka, aby dowiedzieć się więcej
> [!div class="nextstepaction"]
> [Klasyfikacja wydania](github-issue-classification.md)
