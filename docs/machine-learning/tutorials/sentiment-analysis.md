---
title: 'Samouczek: Analizowanie komentarzy na stronie internetowej - klasyfikacja binarna'
description: W tym samouczku pokazano, jak utworzyć aplikację konsoli .NET Core, która klasyfikuje tonację z komentarzy w witrynie sieci Web i podejmuje odpowiednie działania. Klasyfikator tonacji binarnych używa języka C# w programie Visual Studio.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c6e13cfca93c54648b1a0423c5983013d3e2a1a0
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243300"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a>Samouczek: Analizowanie nastrojów komentarzy na stronie internetowej z klasyfikacją binarną w ML.NET

W tym samouczku pokazano, jak utworzyć aplikację konsoli .NET Core, która klasyfikuje tonację z komentarzy w witrynie sieci Web i podejmuje odpowiednie działania. Klasyfikator tonacji binarnych używa języka C# w programie Visual Studio 2017.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Tworzenie aplikacji konsolowej
> - Przygotowywanie danych
> - Ładowanie danych
> - Zbuduj i trenuj model
> - Ocena modelu
> - Użyj modelu, aby dokonać prognozowania
> - Zobacz wyniki

Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis)

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2017 w wersji 15.6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym obciążeniem ".NET Core rozwoju między platformami"

- [Zestaw danych Zdania z etykietami uci sentiment](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (plik ZIP)

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. Utwórz **aplikację konsoli .NET** Core o nazwie "SentimentAnalysis".

2. Utwórz katalog o nazwie *Dane* w projekcie, aby zapisać pliki zestawu danych.

3. Zainstaluj **pakiet nuget Microsoft.ML:**

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Zarządzaj pakietami NuGet**. Wybierz "nuget.org" jako źródło pakietu, a następnie wybierz kartę **Przeglądaj.** Wyszukaj **Microsoft.ML**, wybierz odpowiedni pakiet, a następnie wybierz przycisk **Zainstaluj.** Kontynuuj instalację, zgadzając się na warunki licencji dla wybranego pakietu. Zrób to samo dla pakietu **Microsoft.ML.FastTree** NuGet.

## <a name="prepare-your-data"></a>Przygotowywanie danych

> [!NOTE]
> Zestawy danych dla tego samouczka pochodzą z "Od grupy do poszczególnych etykiet przy użyciu funkcji głębokich", Kotzias et. Al. KDD 2015 i gościł w repozytorium uczenia maszynowego UCI - Dua, D. i Karra Taniskidou, E. (2017). Repozytorium uczenia maszynowego UCI [ ].http://archive.ics.uci.edu/ml Irvine, CA: Uniwersytet Kalifornijski, Szkoła Informatyki i Informatyki.

1. Pobierz [plik ZIP zestawu danych UCI Sentiment Labeled Sentences](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)i rozpaj.

2. Skopiuj `yelp_labelled.txt` plik do utworzonego katalogu *Danych.*

3. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy `yelp_labeled.txt` plik i wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**zmień wartość **kopiuj na Katalog wyjściowy** na **Kopiuj, jeśli jest nowszy**.

### <a name="create-classes-and-define-paths"></a>Tworzenie klas i definiowanie ścieżek

1. Dodaj następujące `using` dodatkowe instrukcje w górnej części pliku *Program.cs:*

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddUsings "Add necessary usings")]

1. Dodaj następujący kod do wiersza `Main` tuż nad metodą, aby utworzyć pole do przechowywania ostatnio pobranej ścieżki pliku zestawu danych:

    [!code-csharp[Declare global variables](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

1. Następnie utwórz klasy dla danych wejściowych i prognoz. Dodaj nową klasę do projektu:

    - W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.

    - W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *SentimentData.cs*. Następnie wybierz przycisk **Dodaj.**

1. Plik *SentimentData.cs* zostanie otwarty w edytorze kodu. Dodaj następującą `using` instrukcję do górnej części *SentimentData.cs:*

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#AddUsings "Add necessary usings")]

1. Usuń istniejącą definicję klasy i dodaj następujący `SentimentData` `SentimentPrediction`kod, który ma dwie klasy i , do pliku *SentimentData.cs:*

    [!code-csharp[DeclareTypes](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a>Sposób przygotowania danych

Klasa wejściowego zestawu `SentimentData`danych, `string` ma dla`SentimentText`komentarzy `bool` użytkownika`Sentiment`( ) i ( ) wartość 1 (dodatnia) lub 0 (ujemna) dla tonacji. Oba pola mają atrybuty [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) dołączone do nich, który opisuje kolejność plików danych każdego pola.  Ponadto `Sentiment` właściwość ma atrybut [ColumnName,](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) aby wyznaczyć `Label` go jako pole. Poniższy przykładowy plik nie ma wiersza nagłówka i wygląda następująco:

|SentimentText (Tekst sentymentu)                         |Tonację (etykieta) |
|--------------------------------------|----------|
|Kelnerka była trochę powolna w służbie.|    0     |
|Skorupa nie jest dobra.                    |    0     |
|Wow... Bardzo dobre miejsce na życie.              |    1     |
|Obsługa była bardzo szybka.              |    1     |

`SentimentPrediction`jest klasą przewidywania używane po szkoleniu modelu. Dziedziczy z `SentimentData` tak, `SentimentText` aby dane wejściowe mogą być wyświetlane wraz z przewidywanie danych wyjściowych. Wartość `Prediction` logiczna jest wartością, którą model przewiduje `SentimentText`po podaniu nowego wejścia .

Klasa `SentimentPrediction` danych wyjściowych zawiera dwie inne `Score` właściwości obliczone przez model: `Probability` - wynik pierwotny obliczony przez model i - wynik skalibrowany do prawdopodobieństwa, że tekst ma pozytywny sentyment.

W tym samouczku najważniejszą `Prediction`właściwością jest .

## <a name="load-the-data"></a>Ładowanie danych

Dane w ML.NET są reprezentowane jako [klasa IDataView](xref:Microsoft.ML.IDataView). `IDataView`jest elastycznym, skutecznym sposobem opisywania danych tabelaryjskich (liczbowych i tekstowych). Dane można ładować z pliku tekstowego lub w czasie rzeczywistym (na przykład bazy danych SQL lub plików dziennika) do obiektu. `IDataView`

[Klasa MLContext](xref:Microsoft.ML.MLContext) jest punktem wyjścia dla wszystkich operacji ML.NET. Inicjowanie `mlContext` tworzy nowe środowisko ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest podobny, koncepcyjnie, do `DBContext` w entity framework.

Przygotuj aplikację, a następnie ładuj dane:

1. Zastąp `Console.WriteLine("Hello World!")` `Main` wiersz w metodzie następującym kodem, aby zadeklarować i zainicjować zmienną mlContext:

    [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateMLContext "Create the ML Context")]

2. Dodaj następujące jako następny wiersz kodu `Main()` w metodzie:

    [!code-csharp[CallLoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallLoadData)]

3. Utwórz `LoadData()` metodę, zaraz `Main()` po metodzie, używając następującego kodu:

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    Metoda `LoadData()` wykonuje następujące zadania:

    - Ładuje dane.
    - Dzieli załadowany zestaw danych do zestawów danych pociągu i testu.
    - Zwraca zestaw danych pociągu podzielonego i testu.

4. Dodaj następujący kod jako pierwszy `LoadData()` wiersz metody:

    [!code-csharp[LoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#LoadData "loading dataset")]

    Metoda [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczytuje w pliku. Przyjmuje zmienne ścieżki danych i `IDataView`zwraca plik .

### <a name="split-the-dataset-for-model-training-and-testing"></a>Dzielenie zestawu danych do szkolenia i testowania modelu

Podczas przygotowywania modelu, należy użyć części zestawu danych, aby go wyszkolić i część zestawu danych, aby przetestować dokładność modelu.

1. Aby podzielić załadowane dane na potrzebne zestawy danych, dodaj następujący `LoadData()` kod jako następny wiersz metody:

    [!code-csharp[SplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#SplitData "Split the Data")]

    Poprzedni kod używa [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) metoda podzielić załadowany zestaw danych do zestawu danych pociągu <xref:Microsoft.ML.DataOperationsCatalog.TrainTestData> i testowania i zwrócić je w klasie. Określ procent testu zestawu `testFraction`danych z parametrem. Wartość domyślna to 10%, w tym przypadku używasz 20% do oceny większej ilości danych.

2. Zwraca `splitDataView` na końcu `LoadData()` metody:

    [!code-csharp[ReturnSplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a>Zbuduj i trenuj model

1. Dodaj następujące wywołanie `BuildAndTrainModel`metody jako następny wiersz `Main()` kodu w metodzie:

    [!code-csharp[CallBuildAndTrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallBuildAndTrainModel)]

    Metoda `BuildAndTrainModel()` wykonuje następujące zadania:

    - Wyodrębnia i przekształca dane.
    - Trenuje model.
    - Prognozuje tonację na podstawie danych testowych.
    - Zwraca model.

2. Utwórz `BuildAndTrainModel()` metodę, zaraz `Main()` po metodzie, używając następującego kodu:

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a>Wyodrębnianie i przekształcanie danych

1. Zadzwoń `FeaturizeText` jako następny wiersz kodu:

    [!code-csharp[FeaturizeText](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#FeaturizeText "Featurize the text")]

    Metoda `FeaturizeText()` w poprzednim kodzie konwertuje`SentimentText`kolumnę tekstową `Features` ( ) na kolumnę typu klucza numerycznego używaną przez algorytm uczenia maszynowego i dodaje ją jako nową kolumnę zestawu danych:

    |SentimentText (Tekst sentymentu)                         |Opinia |Funkcje              |
    |--------------------------------------|----------|----------------------|
    |Kelnerka była trochę powolna w służbie.|    0     |[0.76, 0.65, 0.44, ...] |
    |Skorupa nie jest dobra.                    |    0     |[0.98, 0.43, 0.54, ...] |
    |Wow... Bardzo dobre miejsce na życie.              |    1     |[0.35, 0.73, 0.46, ...] |
    |Obsługa była bardzo szybka.              |    1     |[0.39, 0, 0.75, ...]    |

### <a name="add-a-learning-algorithm"></a>Dodawanie algorytmu uczenia się

Ta aplikacja używa algorytmu klasyfikacji, który kategoryzuje elementy lub wiersze danych. Aplikacja kategoryzuje komentarze witryny sieci Web jako pozytywne lub negatywne, więc użyj zadania klasyfikacji binarnej.

Dołącz zadanie uczenia maszynowego do definicji transformacji danych, dodając następujące `BuildAndTrainModel()`elementy jako następny wiersz kodu w:

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) jest algorytm szkolenia klasyfikacji. Jest to dołączone do `estimator` i akceptuje `SentimentText` featurized`Features`( `Label` ) i parametry wejściowe, aby dowiedzieć się z danych historycznych.

### <a name="train-the-model"></a>Uczenie modelu

Dopasuj `splitTrainSet` model do danych i zwróć przeszkolony model, dodając następujący `BuildAndTrainModel()` wiersz kodu w metodzie:

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TrainModel "Train the model")]

[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) Metoda trenuje modelu przez przekształcenie zestawu danych i stosowania szkolenia.

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Zwraca model przeszkolony do wykorzystania do oceny

 Zwraca model na końcu `BuildAndTrainModel()` metody:

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a>Ocena modelu

Po przeszkoleniu modelu należy użyć danych testowych sprawdź poprawność wydajności modelu.

1. Utwórz `Evaluate()` metodę, `BuildAndTrainModel()`zaraz po , z następującym kodem:

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    Metoda `Evaluate()` wykonuje następujące zadania:

    - Ładuje testowy zestaw danych.
    - Tworzy binaryclassification oceniającego.
    - Ocenia model i tworzy metryki.
    - Wyświetla dane.

2. Dodaj wywołanie do nowej `Main()` metody z metody, bezpośrednio pod wywołaniem `BuildAndTrainModel()` metody, przy użyciu następującego kodu:

    [!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallEvaluate "Call the Evaluate method")]

3. Przekształć `splitTestSet` dane, `Evaluate()`dodając następujący kod do:

    [!code-csharp[PredictWithTransformer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TransformData "Predict using the Transformer")]

    Poprzedni kod używa [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda do przewidywania dla wielu wierszy wejściowych dostarczonych zestawu danych testowych.

4. Oceń model, dodając następujące jako następny wiersz `Evaluate()` kodu w metodzie:

    [!code-csharp[ComputeMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Evaluate "Compute Metrics")]

Po ustawieniu prognozowania`predictions`( ), [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) metoda ocenia model, który porównuje przewidywane wartości z rzeczywistym `Labels` w zestawie danych testu i zwraca [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) obiektu na jak model wykonuje.

### <a name="displaying-the-metrics-for-model-validation"></a>Wyświetlanie metryk sprawdzania poprawności modelu

Użyj następującego kodu, aby wyświetlić dane:

[!code-csharp[DisplayMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayMetrics "Display selected metrics")]

- Metryka `Accuracy` pobiera dokładność modelu, który jest proporcją poprawnych prognoz w zestawie testów.

- `AreaUnderRocCurve` Metryka wskazuje, jak pewny siebie model jest poprawnie klasyfikowanie dodatnich i ujemnych klas. Chcesz być `AreaUnderRocCurve` jak najbliżej jednego, jak to możliwe.

- Metryka `F1Score` pobiera wynik F1 modelu, który jest miarą równowagi między [precyzją](../resources/glossary.md#precision) a [przywoływaniem.](../resources/glossary.md#recall)  Chcesz być `F1Score` jak najbliżej jednego, jak to możliwe.

### <a name="predict-the-test-data-outcome"></a>Przewidywanie wyników danych testowych

1. Utwórz `UseModelWithSingleItem()` metodę, zaraz `Evaluate()` po metodzie, używając następującego kodu:

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    Metoda `UseModelWithSingleItem()` wykonuje następujące zadania:

    - Tworzy pojedynczy komentarz danych testowych.
    - Prognozuje tonację na podstawie danych testowych.
    - Łączy dane testowe i prognozy do raportowania.
    - Wyświetla przewidywane wyniki.

2. Dodaj wywołanie do nowej `Main()` metody z metody, bezpośrednio pod wywołaniem `Evaluate()` metody, przy użyciu następującego kodu:

    [!code-csharp[CallUseModelWithSingleItem](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. Dodaj następujący kod, aby utworzyć jako `UseModelWithSingleItem()` pierwszy wiersz w Method:

    [!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest interfejsem API wygody, który umożliwia wykonywanie prognozowania na jednym wystąpieniu danych. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny dla wątków. Jest dopuszczalne do użycia w środowiskach jednowątkowych lub prototypowych. Aby zwiększyć wydajność i bezpieczeństwo wątków `PredictionEnginePool` w środowiskach [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) produkcyjnych, należy użyć usługi, która tworzy obiekty [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do użycia w całej aplikacji. Zobacz ten przewodnik dotyczący [używania `PredictionEnginePool` w ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

    > [!NOTE]
    > `PredictionEnginePool`rozszerzenie usługi jest obecnie w wersji zapoznawczej.

4. Dodaj komentarz, aby przetestować przewidywanie uczonego modelu w `UseModelWithSingleItem()` `SentimentData`metodzie, tworząc wystąpienie:

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. Przekaż dane komentarza testu [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do, dodając następujące jako następne `UseModelWithSingleItem()` wiersze kodu w metodzie:

    [!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Predict "Create a prediction of sentiment")]

    [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) Funkcja sprawia, że przewidywanie w jednym wierszu danych.

6. Wyświetlanie `SentimentText` i odpowiednie przewidywanie tonacji przy użyciu następującego kodu:

    [!code-csharp[OutputPrediction](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a>Użyj modelu do przewidywania

### <a name="deploy-and-predict-batch-items"></a>Wdrażanie i przewidywanie elementów wsadowych

1. Utwórz `UseModelWithBatchItems()` metodę, zaraz `UseModelWithSingleItem()` po metodzie, używając następującego kodu:

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    Metoda `UseModelWithBatchItems()` wykonuje następujące zadania:

    - Tworzy dane testu wsadowego.
    - Prognozuje tonację na podstawie danych testowych.
    - Łączy dane testowe i prognozy do raportowania.
    - Wyświetla przewidywane wyniki.

2. Dodaj wywołanie do nowej `Main` metody z metody, bezpośrednio pod wywołaniem `UseModelWithSingleItem()` metody, przy użyciu następującego kodu:

    [!code-csharp[CallPredictModelBatchItems](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. Dodaj kilka komentarzy, aby przetestować przewidywania modelu `UseModelWithBatchItems()` uczonego w metodzie:

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a>Przewidywanie tonacji komentarzy

Model służy do przewidywania tonacji danych komentarzy przy użyciu metody [Transform():](xref:Microsoft.ML.ITransformer.Transform%2A)

[!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a>Łączenie i wyświetlanie prognoz

Utwórz nagłówek dla prognoz przy użyciu następującego kodu:

[!code-csharp[OutputHeaders](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddInfoMessage "Display prediction outputs")]

Ponieważ `SentimentPrediction` jest dziedziczona `SentimentData` `Transform()` z `SentimentText` metody wypełnionej przewidywanymi polami. W miarę procesów ML.NET procesów każdy składnik dodaje kolumny, co ułatwia wyświetlanie wyników:

[!code-csharp[DisplayPredictions](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a>Wyniki

Wyniki powinny być podobne do następujących. Podczas przetwarzania są wyświetlane komunikaty. Mogą być widoczne ostrzeżenia lub przetwarzania komunikatów. Zostały one usunięte z następujących wyników dla jasności.

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

Gratulacje! Pomyślnie zbudowano model uczenia maszynowego do klasyfikowania i przewidywania tonacji wiadomości.

Tworzenie udanych modeli jest procesem iteracyjnym. Ten model ma początkową niższą jakość, ponieważ samouczek używa małych zestawów danych, aby zapewnić szybkie szkolenie modelu. Jeśli nie jesteś zadowolony z jakości modelu, można spróbować go poprawić, zapewniając większe zestawy danych szkoleniowych lub wybierając różne algorytmy szkoleniowe z różnymi [hiper-parametrów](../resources/glossary.md#hyperparameter) dla każdego algorytmu.

Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis)

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Tworzenie aplikacji konsolowej
> - Przygotowywanie danych
> - Ładowanie danych
> - Zbuduj i trenuj model
> - Ocena modelu
> - Użyj modelu, aby dokonać prognozowania
> - Zobacz wyniki

Przejdź do następnego samouczka, aby dowiedzieć się więcej
> [!div class="nextstepaction"]
> [Klasyfikacja problemów](github-issue-classification.md)
