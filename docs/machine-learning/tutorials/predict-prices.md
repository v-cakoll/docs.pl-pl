---
title: 'Samouczek: Przewidywanie cen przy użyciu regresji'
description: W tym samouczku pokazano, jak utworzyć model regresji przy użyciu ML.NET do przewidywania cen, w szczególności, New York City opłat za taksówki.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 91429383341cf718d38e636bd1d71dc25d30d20d
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607974"
---
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a>Samouczek: Przewiduj ceny za pomocą regresji z ML.NET

W tym samouczku pokazano, jak utworzyć [model regresji](../resources/glossary.md#regression) przy użyciu ML.NET do przewidywania cen, w szczególności, New York City opłat za taksówki.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> * Przygotowanie i zrozumienie danych
> * Ładowanie i przekształcanie danych
> * Wybieranie algorytmu uczenia się
> * Uczenie modelu
> * Ocena modelu
> * Użyj modelu do prognoz

## <a name="prerequisites"></a>Wymagania wstępne

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowsze lub Visual Studio 2017 w wersji 15.6 lub nowszej z zainstalowanym obciążeniem ".NET Core rozwoju między platformami".

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. Utwórz **aplikację konsoli .NET** Core o nazwie "TaxiFarePrediction".

1. Utwórz katalog o nazwie *Dane* w projekcie, aby przechowywać zestaw danych i pliki modelu.

1. Zainstaluj **pakiet nuget Microsoft.ML:**

    W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**. Wybierz "nuget.org" jako źródło pakietu, wybierz kartę **Przeglądaj,** wyszukaj **Microsoft.ML**, wybierz pakiet na liście i wybierz przycisk **Zainstaluj.** Wybierz przycisk **OK** w oknie **dialogowym Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów. Zrób to samo dla pakietu **Microsoft.ML.FastTree** NuGet.

## <a name="prepare-and-understand-the-data"></a>Przygotowanie i zrozumienie danych

1. Pobierz zestawy danych [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) i [taxi-fare-teste.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) i zapisz je w folderze *Dane* utworzonym w poprzednim kroku. Używamy tych zestawów danych do uczenia modelu uczenia maszynowego, a następnie oceny dokładności modelu. Te zestawy danych pochodzą z [zestawu danych NYC TLC Taxi Trip](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page).

1. W **Eksploratorze rozwiązań** \*kliknij prawym przyciskiem myszy każdy z plików csv i wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**zmień wartość **kopiuj na Katalog wyjściowy** na **Kopiuj, jeśli jest nowszy**.

1. Otwórz zestaw danych **taxi-fare-train.csv** i spójrz na nagłówki kolumn w pierwszym wierszu. Spójrz na każdą z kolumn. Zrozumieć dane i zdecydować, które kolumny są **funkcje,** a które jest **etykieta**.

Jest `label` to kolumna, którą chcesz przewidzieć. Zidentyfikowane `Features`są dane wejściowe, które można `Label`podać model do przewidzenia .

Podany zestaw danych zawiera następujące kolumny:

* **vendor_id:** Identyfikator dostawcy taksówki jest funkcją.
* **rate_code:** Rodzaj stawki podróży taksówką jest cechą.
* **passenger_count:** Liczba pasażerów w podróży jest cechą.
* **trip_time_in_secs:** Czas podróży trwał. Chcesz przewidzieć taryfę podróży przed zakończeniem podróży. W tym momencie nie wiesz, jak długo potrwa podróż. W związku z tym czas podróży nie jest funkcją i wykluczysz tę kolumnę z modelu.
* **trip_distance:** Odległość podróży jest cechą.
* **payment_type:** Metoda płatności (gotówka lub karta kredytowa) jest funkcją.
* **fare_amount:** Całkowita opłata za przejazd taksówką jest etykietą.

## <a name="create-data-classes"></a>Tworzenie klas danych

Tworzenie klas dla danych wejściowych i prognoz:

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.
1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *TaxiTrip.cs*. Następnie wybierz przycisk **Dodaj.**
1. Dodaj następujące `using` dyrektywy do nowego pliku:

   [!code-csharp[AddUsings](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/TaxiTrip.cs#1 "Add necessary usings")]

Usuń istniejącą definicję klasy i dodaj następujący `TaxiTrip` `TaxiTripFarePrediction`kod, który ma dwie klasy i , do pliku *TaxiTrip.cs:*

[!code-csharp[DefineTaxiTrip](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip`jest klasą danych wejściowych i zawiera definicje dla każdej kolumny zestawu danych. Użyj <xref:Microsoft.ML.Data.LoadColumnAttribute> atrybutu, aby określić indeksy kolumn źródłowych w zestawie danych.

Klasa `TaxiTripFarePrediction` reprezentuje przewidywane wyniki. Ma jedno pole float, `FareAmount`z `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> zastosowanym atrybutem. W przypadku zadania regresji **wynik** kolumna zawiera przewidywane wartości etykiet.

> [!NOTE]
> Użyj `float` typu do reprezentowania wartości zmiennoprzecinkowych w klasach danych wejściowych i przewidywanie.

### <a name="define-data-and-model-paths"></a>Definiowanie danych i ścieżek modelu

Dodaj następujące `using` dodatkowe instrukcje w górnej części pliku *Program.cs:*

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#1 "Add necessary usings")]

Aby zapisać model, należy utworzyć trzy pola, aby przytrzymać ścieżki do plików z zestawami danych i plikiem:

* `_trainDataPath`zawiera ścieżkę do pliku z zestawem danych używanym do trenowania modelu.
* `_testDataPath`zawiera ścieżkę do pliku z zestawem danych używanym do oceny modelu.
* `_modelPath`zawiera ścieżkę do pliku, w którym jest przechowywany przeszkolony model.

Dodaj następujący kod tuż `Main` nad metodą, aby `_textLoader` określić te ścieżki i dla zmiennej:

[!code-csharp[InitializePaths](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#2 "Define variables to store the data file paths")]

Wszystkie operacje ML.NET rozpoczynają się w [klasie MLContext](xref:Microsoft.ML.MLContext). Inicjowanie `mlContext` tworzy nowe środowisko ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest podobny, koncepcyjnie, do `DBContext` w entity framework.

### <a name="initialize-variables-in-main"></a>Inicjowanie zmiennych w trybie Głównym

Zastąp `Console.WriteLine("Hello World!")` `Main` wiersz w metodzie następującym kodem, aby zadeklarować i zainicjować zmienną: `mlContext`

[!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#3 "Create the ML Context")]

Dodaj następujące jako następny wiersz kodu `Main` w metodzie, aby wywołać `Train` metodę:

[!code-csharp[Train](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#5 "Train your model")]

Metoda `Train()` wykonuje następujące zadania:

* Ładuje dane.
* Wyodrębnia i przekształca dane.
* Trenuje model.
* Zwraca model.

Metoda `Train` trenuje model. Utwórz tę `Main`metodę tuż poniżej , używając następującego kodu:

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a>Ładowanie i przekształcanie danych

ML.NET używa [IDataView klasy](xref:Microsoft.ML.IDataView) jako elastyczny, skuteczny sposób opisywania danych liczbowych lub tekstowych tabelaryczne. `IDataView`można załadować pliki tekstowe lub w czasie rzeczywistym (na przykład bazy danych SQL lub plików dziennika). Dodaj następujący kod jako pierwszy `Train()` wiersz metody:

[!code-csharp[LoadTrainData](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#6 "loading training dataset")]

Jak chcesz przewidzieć taryfę podróży taksówką, `FareAmount` `Label` kolumna jest, że można przewidzieć (dane wyjściowe modelu). Użyj `CopyColumnsEstimator` klasy transformacji, `FareAmount`aby skopiować i dodać następujący kod:

[!code-csharp[CopyColumnsEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#7 "Use the CopyColumnsEstimator")]

Algorytm, który trenuje model wymaga funkcji **liczbowych,** więc trzeba przekształcić`VendorId` `RateCode`wartości `PaymentType`danych kategorii (`VendorIdEncoded`, `RateCodeEncoded`, `PaymentTypeEncoded`i ) na liczby ( , , i ). Aby to zrobić, należy użyć [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) transformation class, która przypisuje różne wartości klucza liczbowego do różnych wartości w każdej z kolumn i dodaj następujący kod:

[!code-csharp[OneHotEncodingEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#8 "Use the OneHotEncodingEstimator")]

Ostatni krok w przygotowaniu danych łączy wszystkie kolumny **Features** funkcji w `mlContext.Transforms.Concatenate` features kolumny przy użyciu klasy transformacji. Domyślnie algorytm uczenia się przetwarza tylko funkcje z **funkcji kolumny.** Dodaj następujący kod:

[!code-csharp[ColumnConcatenatingEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a>Wybieranie algorytmu uczenia się

Ten problem polega na przewidywaniu taryfy taksówką w Nowym Jorku. Na pierwszy rzut oka może się wydawać, że zależy to po prostu od przebytej odległości. Jednak sprzedawcy taksówek w Nowym Jorku pobierają różne kwoty za inne czynniki, takie jak dodatkowi pasażerowie lub płacąc kartą kredytową zamiast gotówką. Chcesz przewidzieć wartość ceny, która jest wartością rzeczywistą, na podstawie innych czynników w zestawie danych. Aby to zrobić, należy wybrać zadanie uczenia maszynowego [regresji.](../resources/glossary.md#regression)

Dołącz zadanie uczenia maszynowego [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) do definicji transformacji danych, dodając następujące `Train()`elementy jako następny wiersz kodu w:

[!code-csharp[FastTreeRegressionTrainer](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a>Uczenie modelu

Dopasuj model `dataview` do szkolenia i zwróć przeszkolony model, `Train()` dodając następujący wiersz kodu w metodzie:

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#11 "Train the model")]

[Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) Metoda trenuje modelu przez przekształcenie zestawu danych i stosowania szkolenia.

Zwracacie przeszkolony model z następującym `Train()` wierszem kodu w metodzie:

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a>Ocena modelu

Następnie oceń wydajność modelu za pomocą danych testowych pod kątem zapewnienia jakości i sprawdzania poprawności. Utwórz `Evaluate()` metodę, `Train()`zaraz po , z następującym kodem:

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

Metoda `Evaluate` wykonuje następujące zadania:

* Ładuje testowy zestaw danych.
* Tworzy oceniającego regresję.
* Ocenia model i tworzy metryki.
* Wyświetla dane.

Dodaj wywołanie do nowej `Main` metody z metody, bezpośrednio pod wywołaniem `Train` metody, przy użyciu następującego kodu:

[!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#14 "Call the Evaluate method")]

Załaduj testowy zestaw danych przy użyciu metody [LoadFromTextFile().](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) Oceń model przy użyciu tego zestawu danych jako sprawdzanie `Evaluate` jakości, dodając następujący kod w metodzie:

[!code-csharp[LoadTestDataset](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#15 "Load the test dataset")]

Następnie przekształć `Test` dane, `Evaluate()`dodając następujący kod do:

[!code-csharp[PredictWithTransformer](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#16 "Predict using the Transformer")]

Metoda [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) tworzy prognoz dla wierszy wejściowych zestawu danych testowych.

Metoda `RegressionContext.Evaluate` oblicza metryki jakości `PredictionModel` przy użyciu określonego zestawu danych. Zwraca <xref:Microsoft.ML.Data.RegressionMetrics> obiekt, który zawiera ogólne metryki obliczone przez oceniających regresję.

Aby wyświetlić je w celu określenia jakości modelu, należy najpierw uzyskać metryki. Dodaj następujący kod jako następny `Evaluate` wiersz w metodzie:

[!code-csharp[ComputeMetrics](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#17 "Compute Metrics")]

Po ustawieniu prognozowania metoda [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) ocenia model, który porównuje przewidywane wartości `Labels` z rzeczywistym w zestawie danych testowych i zwraca metryki dotyczące wykonywania modelu.

Dodaj następujący kod, aby ocenić model i utworzyć metryki oceny:

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

[RSquared](../resources/glossary.md#coefficient-of-determination) jest inny metryka oceny modeli regresji. RSquared przyjmuje wartości od 0 do 1. Im bliżej jego wartości jest 1, tym lepszy jest model. Dodaj następujący kod `Evaluate` do metody, aby wyświetlić wartość RSquared:

[!code-csharp[DisplayRSquared](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#18 "Display the RSquared metric.")]

[RMS](../resources/glossary.md#root-of-mean-squared-error-rmse) jest jednym z metryk oceny modelu regresji. Im niższy, tym lepszy jest model. Dodaj następujący kod `Evaluate` do metody, aby wyświetlić wartość RMS:

[!code-csharp[DisplayRMS](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a>Użyj modelu do prognoz

Utwórz `TestSinglePrediction` metodę, zaraz `Evaluate` po metodzie, używając następującego kodu:

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

Metoda `TestSinglePrediction` wykonuje następujące zadania:

* Tworzy pojedynczy komentarz danych testowych.
* Prognozuje kwotę taryfy na podstawie danych testowych.
* Łączy dane testowe i prognozy do raportowania.
* Wyświetla przewidywane wyniki.

Dodaj wywołanie do nowej `Main` metody z metody, bezpośrednio pod wywołaniem `Evaluate` metody, przy użyciu następującego kodu:

[!code-csharp[CallTestSinglePrediction](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#20 "Call the TestSinglePrediction method")]

Użyj, `PredictionEngine` aby przewidzieć taryfę, dodając `TestSinglePrediction()`następujący kod do:

[!code-csharp[MakePredictionEngine](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#22 "Create the PredictionFunction")]

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest interfejsem API wygody, który umożliwia wykonywanie prognozowania na jednym wystąpieniu danych. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny dla wątków. Jest dopuszczalne do użycia w środowiskach jednowątkowych lub prototypowych. Aby zwiększyć wydajność i bezpieczeństwo wątków `PredictionEnginePool` w środowiskach [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) produkcyjnych, należy użyć usługi, która tworzy obiekty [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do użycia w całej aplikacji. Zobacz ten przewodnik dotyczący [używania `PredictionEnginePool` w ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

> [!NOTE]
> `PredictionEnginePool`rozszerzenie usługi jest obecnie w wersji zapoznawczej.

W tym samouczku używa jednej podróży testowej w tej klasie. Później można dodać inne scenariusze do eksperymentowania z modelem. Dodaj podróż, aby przetestować przewidywanie kosztów `TestSinglePrediction()` w metodzie przez `TaxiTrip`przeszkolony model, tworząc wystąpienie:

[!code-csharp[PredictionData](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#23 "Create test data for single prediction")]

Następnie należy przewidzieć taryfę na podstawie pojedynczego wystąpienia danych podróży `PredictionEngine` taksówką i przekazać ją do, `TestSinglePrediction()` dodając następujące jako następne wiersze kodu w metodzie:

[!code-csharp[Predict](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#24 "Create a prediction of taxi fare")]

[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) Funkcja sprawia, że przewidywanie na jednym wystąpieniu danych.

Aby wyświetlić przewidywaną taryfę określonej podróży, dodaj `TestSinglePrediction` do metody następujący kod:

[!code-csharp[Predict](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#25 "Display the prediction.")]

Uruchom program, aby zobaczyć przewidywaną taryfę taksówek dla twojego przypadku testowego.

Gratulacje! Teraz udało ci się stworzyć model uczenia maszynowego do przewidywania taryf za przejazd taksówką, ocenić jego dokładność i wykorzystać go do przewidywania. Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub.

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> * Przygotowanie i zrozumienie danych
> * Tworzenie potoku nauki
> * Ładowanie i przekształcanie danych
> * Wybieranie algorytmu uczenia się
> * Uczenie modelu
> * Ocena modelu
> * Użyj modelu do prognoz

Przejdź do następnego samouczka, aby dowiedzieć się więcej.

> [!div class="nextstepaction"]
> [Klastrowanie zestawu danych Iris](iris-clustering.md)
