---
title: Użyj strukturze ML.NET w scenariuszu klasyfikacji binarnej analizy tonacji
description: Dowiedz się, jak używać strukturze ML.NET w scenariuszu klasyfikacji binarnej zrozumienie, jak na potrzeby prognozowania tonacji podjąć odpowiednie działania.
ms.date: 04/18/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 45e94e325fc4fbfaf1e71f7839d5083e44d5863e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973703"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a>Samouczek: Użyj strukturze ML.NET w scenariuszu klasyfikacji binarnej analizy tonacji

Ten przykładowy samouczek przedstawia tworzenie klasyfikatora tonacji uzyskiwania opinii przychodzących komentarze witryny sieci Web, aby podjąć odpowiednie działania, za pośrednictwem używany aplikację konsoli .NET Core przy użyciu strukturze ML.NET C# w programie Visual Studio 2017. W środowisku usługi machine learning tego rodzaju prognozowania nosi nazwę klasyfikacji binarnej.

> [!NOTE]
> W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie. Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Obecnie używasz tego samouczka, a powiązane próbki **(wersja zapoznawcza) w strukturze ML.NET wersji 1.0.0**. Aby uzyskać więcej informacji, zobacz informacje o wersji w [dotnet/machinelearning repozytorium GitHub](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Omówienie problemu
> * Wybieranie algorytmu uczenia maszynowego odpowiednie
> * Przygotowywanie danych
> * Przekształcanie danych
> * Uczenie modelu
> * Ocena modelu
> * Prognozowanie za pomocą uczonego modelu
> * Wdrażanie i przewidywanie załadować modelu

Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repozytorium.

## <a name="prerequisites"></a>Wymagania wstępne

* [Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".

* [Plik zip zdania etykietą tonacji na zestaw danych](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. Tworzenie **aplikacji konsoli .NET Core** o nazwie "SentimentAnalysis".

2. Utwórz katalog o nazwie *danych* w projekcie, aby zapisać pliki zestawu danych.

3. Zainstaluj **pakietu NuGet Microsoft.ML**:

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku. Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.

### <a name="prepare-your-data"></a>Przygotowywanie danych

1. Pobierz [pliku zip zestawu danych na wskaźniki nastrojów klientów etykietą zdań (patrz cytaty poniżej)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)i Rozpakuj go.

2. Kopiuj `yelp_labelled.txt` mezzanine do *danych* katalog został utworzony.

    > [!NOTE]
    > Zestawy danych, w tym samouczku są z "From grupy do poszczególnych etykiet korzystanie z funkcji głębokiego" Kotzias et. Al. KDD 2015 i hostowanej na Machine Learning repozytorium — Dua, D. i Karra Taniskidou, E. (2017). UCI usługi Machine Learning repozytorium [http://archive.ics.uci.edu/ml]. Irvine, CA: Uniwersytet kalifornijski School informacji i informatyki.

3. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy `yelp_labeled.txt` plik i wybierz **właściwości**. W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.

### <a name="create-classes-and-define-paths"></a>Tworzenie klas i definiowania ścieżek

Dodaj następujące dodatkowe `using` instrukcji na górze *Program.cs* pliku:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

Należy utworzyć dwa pola globalnego na potrzeby przechowywania ostatnio pobrane dataset ścieżkę pliku i ścieżka pliku zapisanego modelu:

* `_dataPath` zawiera ścieżkę do zestawu danych, używane do trenowania modelu.
* `_modelPath` ma ścieżkę, w którym jest zapisany trenowanego modelu.

Dodaj następujący kod po prawej stronie wiersza powyżej `Main` metodę, aby określić tych ścieżek:

[!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

Musisz utworzyć niektóre klasy dla danych wejściowych i prognozy. Dodaj nową klasę do projektu:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.

1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *SentimentData.cs*. Następnie wybierz **Dodaj** przycisku.

    *SentimentData.cs* plik zostanie otwarty w edytorze kodu. Dodaj następujący kod `using` instrukcji na górze *SentimentData.cs*:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

Usuń istniejącą definicję klasy i Dodaj następujący kod, który zawiera dwie klasy `SentimentData` i `SentimentPrediction`, *SentimentData.cs* pliku:

[!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

Klasa wejściowy zestaw danych `SentimentData`, ma `string` dla komentarza (`SentimentText`) i `bool` (`Sentiment`) z wartością dla tonacji dodatnie (1) lub fałszywie ujemny (0). Oba pola mają [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) atrybuty do nich dołączone, która opisuje kolejność plików danych każdego pola.  Ponadto `Sentiment` właściwość ma [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) atrybutu, aby uczynić go `Label` pola. Następujący przykład pliku nie ma wiersz nagłówka i wygląda następująco:

|SentimentText                         |Wskaźniki nastrojów klientów (etykieta) |
|--------------------------------------|----------|
|Waitress była nieco wolno w usłudze.|    0     |
|Skórki nie jest dobra.                    |    0     |
|WOW... Pracowałem z tego miejsca.              |    1     |
|Usługa była bardzo szybkie.              |    1     |

`SentimentPrediction` Klasa prognozowania służy po szkoleń modelowych. Ma ona pojedynczy atrybut typu wartość logiczna (`Sentiment`) i `PredictedLabel` `ColumnName` atrybutu. `Label` Umożliwia tworzenie i uczenie modelu, a także używane z Podziel się z zestawu danych testowych do ewaluacji modelu. `PredictedLabel` Używany podczas prognoz i oceny. W wersji ewaluacyjnej są używane dane szkoleniowe, przewidywane wartości i modelu.

[Klasy MLContext](xref:Microsoft.ML.MLContext) to punkt początkowy dla wszystkich operacji w strukturze ML.NET oraz inicjowanie `mlContext` tworzy nowe środowisko strukturze ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Przypomina, model `DBContext` platformy Entity Framework.

### <a name="initialize-variables-in-main"></a>Inicjowanie zmiennych w głównym oknie

Zastąp `Console.WriteLine("Hello World!")` linię `Main` metody za pomocą następującego kodu, aby zadeklarować i zainicjować zmienną mlContext:

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

Dodaj następujący kod jako następnego wiersza kodu w `Main()` metody:

[!code-csharp[CallLoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

`LoadData()` Metoda wykonuje następujące zadania:

* Służy do ładowania danych.
* Dzieli załadowanego zestawu danych na szkolenie i testowanie zestawów danych.
* Zwraca podziału nauczenia i przetestowania zestawów danych.

Tworzenie `LoadData()` metody tuż za `Main()` metody, używając następującego kodu:

```csharp
public static TrainTestData LoadData(MLContext mlContext)
{

}
```

## <a name="load-the-data"></a>Ładowanie danych

Dane w strukturze ML.NET jest reprezentowany jako [klasy IDataView](xref:Microsoft.ML.IDataView). `IDataView` jest elastyczny i wydajny sposób opisu danych tabelarycznych (liczbowe i tekstowe). Dane można załadować z pliku tekstowego lub w czasie rzeczywistym (na przykład SQL bazy danych lub dziennika plików) do `IDataView` obiektu.
Dodaj następujący kod jako pierwsza linia `LoadData()` metody:

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczytuje w pliku. Pobiera zmienne ścieżek danych i zwraca `IDataView`.

### <a name="split-the-dataset-for-model-training-and-testing"></a>Podziel zestaw danych dla modelu, szkolenia i testowania

Następnie należy zarówno zestaw danych szkoleniowych do nauczenia modelu, jak i zestawy danych testowych do ewaluacji modelu.

Aby podzielić dane załadowane do wymaganych zestawów danych, Dodaj następujący kod w następnym wierszu `LoadData()` metody:

[!code-csharp[SplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

W poprzednim kodzie użyto [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) metodę, aby podzielić załadowanego zestawu danych na szkolenie i testowanie zestawy danych i zwraca je w [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) klasy. Ustawienia testu procent danych za pomocą `testFraction`parametru. Wartość domyślna wynosi 10%, ale w tym przypadku użyj 20% do oceny większej ilości danych.  

Zwróć `splitDataView` na końcu `LoadData()` metody:

[!code-csharp[ReturnSplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a>Tworzenie i trenowanie modelu

Dodaj następujące wywołanie do `BuildAndTrainModel`metodę jako następnego wiersza kodu w `Main()` metody:

[!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

`BuildAndTrainModel()` Metoda wykonuje następujące zadania:

* Wyodrębnia i przekształca dane.
* Szkolenie modeli modelu.
* Prognozuje tonacji na podstawie danych testowych.
* Zwraca wartość modelu.

Tworzenie `BuildAndTrainModel()` metody tuż za `Main()` metody, używając następującego kodu:

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
{

}
```

## <a name="extract-and-transform-the-data"></a>Wyodrębnianie i przekształcania danych

Wywołaj `FeaturizeText` jako następnego wiersza kodu:

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

`FeaturizeText()` Metoda w poprzednim kodzie Konwertuje kolumny tekstowej (`SentimentText`) na typ liczbowy klucza `Features` kolumny używane przez algorytmu uczenia maszynowego i dodaje go jako nowe kolumny zestawu danych:

|SentimentText                         |wskaźniki nastrojów klientów |Funkcje              |
|--------------------------------------|----------|----------------------|
|Waitress była nieco wolno w usłudze.|    0     |[0.76, 0.65, 0.44, …] |
|Skórki nie jest dobra.                    |    0     |[0.98, 0.43, 0.54, …] |
|WOW... Pracowałem z tego miejsca.              |    1     |[0.35, 0.73, 0.46, …] |
|Usługa była bardzo szybkie.              |    1     |[0.39, 0, 0.75, …]    |

## <a name="add-a-learning-algorithm"></a>Dodaj algorytmu uczenia

### <a name="about-the-classification-task"></a>O zadaniu klasyfikacji

"Chodzi A lub B?"

![algorytmu uczenia maszynowego klasyfikacji](./media/sentiment-analysis/classification.png)

Klasyfikacja jest algorytm uczenia maszynowego, która korzysta z danych do **określić** kategorii, typ lub klasa elementu lub wiersz danych i jest często jednym z następujących typów:

* Plik binarny: A i B.
* Kontra: wielu kategorii, które można przewidzieć przy użyciu pojedynczego modelu.

Ponieważ komentarze witryny sieci Web muszą być klasyfikowane jako dodatnie lub ujemne, możesz użyć zadania klasyfikacji binarnej.

Dołącz zadanie uczenia maszynowego z definicjami przekształcania danych, dodając następujące jako następnego wiersza kodu w `BuildAndTrainModel()`:

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) to algorytm klasyfikacji szkolenia. To jest dołączany do `estimator` i akceptuje neural `SentimentText` (`Features`) i `Label` parametrów, aby dowiedzieć się więcej na podstawie historycznych danych wejściowych.

## <a name="train-the-model"></a>Uczenie modelu

Dopasuj do modelu `splitTrainSet` danych i zwracają uczonego modelu przez dodanie poniższego jako następnego wiersza kodu w `BuildAndTrainModel()` metody:

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) metoda szkolenie modeli modelu przekształcania zestawu danych i stosując szkolenia.

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Zwraca czy model jest uczony na potrzeby oceny

 Zwraca model na końcu `BuildAndTrainModel()` metody:

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a>Ocena modelu

Po model jest uczony, należy użyć danych testowych do oceny, jak działa model kontroli jakości i sprawdzania poprawności. Tworzenie `Evaluate()` metody tuż za `BuildAndTrainModel()`, używając następującego kodu:

```csharp
public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
{

}
```

`Evaluate()` Metoda wykonuje następujące zadania:

* Ładuje zestawy danych testowych.
* Tworzy ewaluatora BinaryClassification.
* Oblicza model i tworzy metryki.
* Przedstawia metryki.

Dodaj wywołanie do nowej metody z `Main()` metody, po prawej stronie w obszarze `BuildAndTrainModel()` wywołania metody, używając następującego kodu:

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

Przekształcanie `splitTestSet` danych przez dodanie poniższego kodu `Evaluate()`:

[!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

W poprzednim kodzie użyto [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metodę, aby tworzyć prognozy dla wielu podać wiersze danych wejściowych zestawu testów.

Ocena modelu przez dodanie poniższego jako następnego wiersza kodu w `Evaluate()` metody:

[!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

Po utworzeniu prognozowania, ustaw (`predictions`), [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) metoda ocenia modelu, który porównuje przewidywane wartości z rzeczywistych `Labels` zestawu danych testowych i zwraca [ CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) obiekt jak działa model.

### <a name="displaying-the-metrics-for-model-validation"></a>Wyświetlanie metryki dotyczące weryfikacji modelu

Użyj poniższego kodu, aby wyświetlić metryki:

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

* `Accuracy` Metryki pobiera dokładności modelu, część poprawne prognozy w zestawie testów.

* `AreaUnderRocCurve` Metryka wskazuje, jak pewność modelu jest poprawnie klasyfikowania klasy dodatnie i ujemne. Chcesz `AreaUnderRocCurve` sposób maksymalnie zbliżony jeden, jak to możliwe.

* `F1Score` Metryki pobiera wynik F1 modelu, który jest miarą równowagi między [dokładności](../resources/glossary.md#precision) i [odwołania](../resources/glossary.md#recall).  Chcesz `F1Score` sposób maksymalnie zbliżony jeden, jak to możliwe.

## <a name="predict-the-test-data-outcome"></a>Przewidywanie wyników danych testowych

Tworzenie `UseModelWithSingleItem()` metody tuż za `Evaluate()` metody, używając następującego kodu:

```csharp
private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
{

}
```

`UseModelWithSingleItem()` Metoda wykonuje następujące zadania:

* Tworzy pojedynczy komentarz danych testowych.
* Prognozuje tonacji na podstawie danych testowych.
* Łączy w sobie testowanie, danych i prognoz dla raportowania.
* Wyświetla przewidywane wyniki.

Dodaj wywołanie do nowej metody z `Main()` metody, po prawej stronie w obszarze `Evaluate()` wywołania metody, używając następującego kodu:

[!code-csharp[CallUseModelWithSingleItem](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest wygoda interfejsu API, dzięki czemu można przekazać, a następnie wykonaj prognozowania w pojedynczym wystąpieniu danych. Dodaj następujący kod do utworzenia jako pierwszy wiersz w `Predict()` metody:

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]
  
Dodaj komentarz do testowania uczonego modelu prognozowania w `Predict()` metody przez utworzenie wystąpienia `SentimentData`:

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

Przekaż dane komentarz testu do `Prediction Engine` przez dodanie poniższego jako z następującymi wierszami kodu w `UseModelWithSingleItem()` metody:

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) funkcja sprawia, że prognoz na pojedynczy wiersz danych.

### <a name="use-the-model-prediction"></a>Użyj modelu: prognoz

Wyświetlanie `SentimentText` i odpowiednie wskaźniki nastrojów klientów przewidywania, używając następującego kodu:

[!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="deploy-and-predict-batch-items"></a>Wdrażanie i przewidywanie elementów usługi batch

Tworzenie `UseModelWithBatchItems()` metody tuż za `UseModelWithSingleItem()` metody, używając następującego kodu:

```csharp
public static void UseModelWithBatchItems(MLContext mlContext)
{

}
```

`UseModelWithBatchItems()` Metoda wykonuje następujące zadania:

* Tworzy dane testowe usługi batch.
* Prognozuje tonacji na podstawie danych testowych.
* Łączy w sobie testowanie, danych i prognoz dla raportowania.
* Wyświetla przewidywane wyniki.

Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `UseModelWithSingleItem()` wywołania metody, używając następującego kodu:

[!code-csharp[CallPredictModelBatchItems](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

Dodaj niektóre komentarze, aby przetestować prognozy uczonego modelu w `UseModelWithBatchItems()` metody:

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="use-the-model-for-prediction"></a>Użyj modelu do prognozowania

Zastosowanie modelu do prognozowania, komentarz dane opinii za pomocą [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metody:

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a>Łączenie i wyświetlanie prognozy

Utwórz nagłówek dla prognoz, używając następującego kodu:

[!code-csharp[OutputHeaders](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

Przed wyświetleniem wyników, należy połączyć oryginalnym komentarzem z jego przewidywane tonacji za pomocą [Zip()](xref:System.Linq.Enumerable.Zip%2A) metody:

[!code-csharp[BuildTuples](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#BuildSentimentPredictionPairs "Build the pairs of sentiment data and predictions")]

Teraz, gdy `SentimentText` i `Sentiment` są łączone w klasie, wyświetlić wyniki:

[!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a>Wyniki

Wyniki powinny być podobne do następujących. Podczas przetwarzania, komunikaty są wyświetlane. Może zostać wyświetlony ostrzeżenia lub komunikaty przetwarzania. Te zostały usunięte z następujących wyników dla przejrzystości.

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

Gratulacje! Model uczenia maszynowego dla klasyfikacji i prognozowanie tonacji wiadomości teraz zostały pomyślnie skompilowane.

Tworzenie modeli pomyślne jest procesem iteracyjnym. Ten model jest początkowa niższa jakość samouczek używa małych zestawów danych na przeszkolenie szybkiego modelu. Jeśli nie jesteś zadowolony z jakość modelu, możesz spróbować ją ulepszyć, dostarczając większych zestawów danych szkoleniowych lub wybierając inną szkolenia algorytmów z różnymi [hiper parametrami](../resources/glossary.md##hyperparameter) dla każdego algorytmu.

Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repozytorium.

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Omówienie problemu
> * Wybieranie algorytmu uczenia maszynowego odpowiednie
> * Przygotowywanie danych
> * Przekształcanie danych
> * Uczenie modelu
> * Ocena modelu
> * Prognozowanie za pomocą uczonego modelu
> * Wdrażanie i przewidywanie załadować modelu

Przejdź do następnego samouczka, aby dowiedzieć się więcej
> [!div class="nextstepaction"]
> [Klasyfikacja problemu](github-issue-classification.md)
