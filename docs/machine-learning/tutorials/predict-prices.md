---
title: 'Samouczek: Przewidywanie cen za pomocą regresji'
description: W tym samouczku pokazano, jak zbudować model regresji przy użyciu ML.NET do przewidywania cen, w szczególności, New York City taksówki.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 51cef97178c2dbc6a5b572a7045bdad4bc382ba0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78240990"
---
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a>Samouczek: Przewidywanie cen za pomocą regresji za pomocą ML.NET

W tym samouczku pokazano, jak zbudować [model regresji](../resources/glossary.md#regression) przy użyciu ML.NET do przewidywania cen, w szczególności, New York City taksówki.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> * Przygotowywanie i rozumienie danych
> * Ładowanie i przekształcanie danych
> * Wybierz algorytm uczenia się
> * Uczenie modelu
> * Ocena modelu
> * Użyj modelu dla prognoz

## <a name="prerequisites"></a>Wymagania wstępne

* [Visual Studio 2017 w wersji 15.6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem ".NET Core programistorna wieloplatformowa".

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. Utwórz **aplikację .NET Core Console o** nazwie "TaxiFarePrediction".

1. Utwórz katalog o nazwie *Dane* w projekcie, aby przechowywać pliki zestawu danych i modelu.

1. Zainstaluj **pakiet Microsoft.ML** NuGet:

    W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**. Wybierz "nuget.org" jako źródło pakietu, wybierz kartę **Przeglądaj,** wyszukaj **Microsoft.ML,** wybierz pakiet na liście i wybierz przycisk **Zainstaluj.** Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z warunkami licencyjnymi dla wymienionych pakietów. Zrób to samo dla pakietu **Microsoft.ML.FastTree** NuGet.

## <a name="prepare-and-understand-the-data"></a>Przygotowywanie i rozumienie danych

1. Pobierz [zestawy danych taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) i [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) i zapisz je w folderze *Data* utworzonym w poprzednim kroku. Używamy tych zestawów danych do uczenia modelu uczenia maszynowego, a następnie oceniamy, jak dokładny jest model. Te zestawy danych pochodzą z [zestawu danych NYC TLC Taxi Trip](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page).

1. W **Eksploratorze**rozwiązań \*kliknij prawym przyciskiem myszy każdy z plików csv i wybierz **polecenie Właściwości**. W obszarze **Zaawansowane**zmień wartość **kopiuj do katalogu wyjściowego,** aby **skopiować, jeśli nowsza**.

1. Otwórz zestaw danych **taxi-fare-train.csv** i spójrz na nagłówki kolumn w pierwszym wierszu. Spójrz na każdą z kolumn. Zrozumienie danych i zdecydować, które kolumny są **operacjami,** a które **etykietą**.

Jest `label` to kolumna, którą chcesz przewidzieć. Zidentyfikowane `Features`są dane wejściowe, które dajesz modelowi przewidzieć `Label`.

Dostarczony zestaw danych zawiera następujące kolumny:

* **vendor_id:** Identyfikator dostawcy taksówek jest funkcją.
* **rate_code:** Typ stawki podróży taksówką jest cechą.
* **passenger_count:** Liczba pasażerów w podróży jest cechą.
* **trip_time_in_secs:** Czas podróży. Chcesz przewidzieć taryfę podróży przed zakończeniem podróży. W tym momencie nie wiesz, jak długo potrwa podróż. W związku z tym czas podróży nie jest funkcją i wykluczysz tę kolumnę z modelu.
* **trip_distance:** Odległość podróży jest cechą.
* **payment_type:** Metoda płatności (gotówka lub karta kredytowa) jest funkcją.
* **fare_amount:** Całkowita opłata za przejazd taksówką jest etykietą.

## <a name="create-data-classes"></a>Tworzenie klas danych

Tworzenie klas dla danych wejściowych i prognoz:

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.
1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *TaxiTrip.cs*. Następnie wybierz przycisk **Dodaj.**
1. Dodaj następujące `using` dyrektywy do nowego pliku:

   [!code-csharp[AddUsings](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/TaxiTrip.cs#1 "Add necessary usings")]

Usuń istniejącą definicję klasy i dodaj następujący `TaxiTrip` `TaxiTripFarePrediction`kod, który ma dwie klasy i , do *pliku TaxiTrip.cs:*

[!code-csharp[DefineTaxiTrip](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip`jest klasą danych wejściowych i ma definicje dla każdej z kolumn zestawu danych. Użyj <xref:Microsoft.ML.Data.LoadColumnAttribute> atrybutu, aby określić indeksy kolumn źródłowych w zestawie danych.

Klasa `TaxiTripFarePrediction` reprezentuje przewidywane wyniki. Ma jedno pole float, `FareAmount`, `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> z zastosowanym atrybutem. W przypadku zadania regresji **Score** kolumna zawiera przewidywane wartości etykiet.

> [!NOTE]
> Typ `float` służy do reprezentowania wartości zmiennoprzecinkowych w klasach danych wejściowych i przewidywania.

### <a name="define-data-and-model-paths"></a>Definiowanie ścieżek danych i modeli

Dodaj następujące `using` dodatkowe instrukcje do górnej części pliku *Program.cs:*

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#1 "Add necessary usings")]

Aby zapisać model, należy utworzyć trzy pola, aby przytrzymać ścieżki do plików z zestawami danych i plik:

* `_trainDataPath`zawiera ścieżkę do pliku z zestawem danych używanym do nauczenia modelu.
* `_testDataPath`zawiera ścieżkę do pliku z zestawem danych używanym do oceny modelu.
* `_modelPath`zawiera ścieżkę do pliku, w którym jest przechowywany uczonego modelu.

Dodaj następujący kod tuż `Main` nad metodą, aby `_textLoader` określić te ścieżki i zmienną:

[!code-csharp[InitializePaths](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#2 "Define variables to store the data file paths")]

Wszystkie operacje ML.NET rozpoczynają się w [klasie MLContext](xref:Microsoft.ML.MLContext). Inicjowanie `mlContext` tworzy nowe środowisko ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest to podobne, koncepcyjnie, `DBContext` do w ramach jednostki.

### <a name="initialize-variables-in-main"></a>Inicjowanie zmiennych w main

Zamień `Console.WriteLine("Hello World!")` wiersz `Main` w metodzie na następujący kod, `mlContext` aby zadeklarować i zainicjować zmienną:

[!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#3 "Create the ML Context")]

Dodaj następujące jako następny wiersz kodu `Main` w metodzie, aby wywołać `Train` metodę:

[!code-csharp[Train](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#5 "Train your model")]

Metoda `Train()` wykonuje następujące zadania:

* Ładuje dane.
* Wyodrębnia i przekształca dane.
* Trenuje model.
* Zwraca model.

Metoda `Train` trenuje model. Utwórz tę `Main`metodę tuż poniżej, używając następującego kodu:

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a>Ładowanie i przekształcanie danych

ML.NET używa [klasy IDataView](xref:Microsoft.ML.IDataView) jako elastycznego i wydajnego sposobu opisywania danych liczbowych lub tekstowych. `IDataView`można ładować pliki tekstowe lub w czasie rzeczywistym (na przykład bazy danych SQL lub pliki dziennika). Dodaj następujący kod jako pierwszy `Train()` wiersz metody:

[!code-csharp[LoadTrainData](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#6 "loading training dataset")]

Jak chcesz przewidzieć taryfy przejazd `FareAmount` taksówką, `Label` kolumna jest, że można przewidzieć (wyjście modelu). Użyj `CopyColumnsEstimator` klasy transformacji, `FareAmount`aby skopiować i dodać następujący kod:

[!code-csharp[CopyColumnsEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#7 "Use the CopyColumnsEstimator")]

Algorytm, który trenuje model wymaga funkcji **numerycznych,** więc trzeba`VendorId` `RateCode`przekształcić `PaymentType`dane kategorii (, `RateCodeEncoded`i `PaymentTypeEncoded`) wartości na liczby (`VendorIdEncoded`, i ). Aby to zrobić, należy użyć [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) klasy transformacji, który przypisuje różne wartości klucza liczbowego do różnych wartości w każdej z kolumn i dodać następujący kod:

[!code-csharp[OneHotEncodingEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#8 "Use the OneHotEncodingEstimator")]

Ostatni krok w przygotowaniu danych łączy wszystkie kolumny funkcji `mlContext.Transforms.Concatenate` w **kolumnie Funkcje** przy użyciu klasy transformacji. Domyślnie algorytm uczenia się przetwarza tylko funkcje z **kolumny Funkcje.** Dodaj następujący kod:

[!code-csharp[ColumnConcatenatingEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a>Wybierz algorytm uczenia się

Ten problem polega na przewidywaniu przejazdu taksówką w Nowym Jorku. Na pierwszy rzut oka może się wydawać, że zależy to po prostu od przebytej odległości. Jednak sprzedawcy taksówek w Nowym Jorku pobierają różne kwoty za inne czynniki, takie jak dodatkowi pasażerowie lub płacąc kartą kredytową zamiast gotówką. Chcesz przewidzieć wartość ceny, która jest wartością rzeczywistą, na podstawie innych czynników w zestawie danych. Aby to zrobić, należy wybrać zadanie uczenia maszynowego [regresji.](../resources/glossary.md#regression)

Dołącz zadanie uczenia maszynowego [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) do definicji transformacji danych, dodając następujący `Train()`wiersz kodu w:

[!code-csharp[FastTreeRegressionTrainer](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a>Uczenie modelu

Dopasuj model `dataview` do szkolenia i zwróć uczonego `Train()` modelu, dodając następujący wiersz kodu w metodzie:

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#11 "Train the model")]

[Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) Metoda szkoli modelu przez przekształcenie zestawu danych i stosowania szkolenia.

Zwraca uczonego modelu z następującym `Train()` wierszem kodu w metodzie:

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a>Ocena modelu

Następnie oceń wydajność modelu za pomocą danych testowych w celu zapewnienia jakości i weryfikacji. Utwórz `Evaluate()` metodę, `Train()`zaraz po , z następującym kodem:

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

Metoda `Evaluate` wykonuje następujące zadania:

* Ładuje testowy zestaw danych.
* Tworzy oceniającego regresji.
* Ocenia model i tworzy metryki.
* Wyświetla metryki.

Dodaj wywołanie do nowej `Main` metody z metody, bezpośrednio w wywołaniu `Train` metody, przy użyciu następującego kodu:

[!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#14 "Call the Evaluate method")]

Załaduj testowy zestaw danych przy użyciu metody [LoadFromTextFile().](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) Oceń model przy użyciu tego zestawu danych jako sprawdzanie jakości, dodając następujący kod w metodzie: `Evaluate`

[!code-csharp[LoadTestDataset](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#15 "Load the test dataset")]

Następnie przekształć `Test` dane, dodając `Evaluate()`następujący kod do:

[!code-csharp[PredictWithTransformer](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#16 "Predict using the Transformer")]

Metoda [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) tworzy prognozy dla wierszy wejściowych zestawu danych testowych.

Metoda `RegressionContext.Evaluate` oblicza metryki jakości dla `PredictionModel` przy użyciu określonego zestawu danych. Zwraca <xref:Microsoft.ML.Data.RegressionMetrics> obiekt, który zawiera ogólne metryki obliczone przez oceniających regresji.

Aby wyświetlić te, aby określić jakość modelu, należy najpierw uzyskać metryki. Dodaj następujący kod jako następny `Evaluate` wiersz w metodzie:

[!code-csharp[ComputeMetrics](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#17 "Compute Metrics")]

Po ustawieniu przewidywania metoda [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) ocenia model, który porównuje przewidywane wartości z `Labels` rzeczywistymi w zestawie danych testowych i zwraca metryki dotyczące sposobu wykonywania modelu.

Dodaj następujący kod, aby ocenić model i wygenerować metryki oceny:

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

[RSquared](../resources/glossary.md#coefficient-of-determination) jest inną metryką oceny modeli regresji. RSquared przyjmuje wartości z wartości od 0 do 1. Im bliżej jego wartości jest 1, tym lepszy jest model. Dodaj następujący kod `Evaluate` do metody, aby wyświetlić wartość RSquared:

[!code-csharp[DisplayRSquared](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#18 "Display the RSquared metric.")]

[Program RMS](../resources/glossary.md#root-of-mean-squared-error-rmse) jest jedną ze metryk oceny modelu regresji. Im niższa, tym lepszy jest model. Dodaj następujący kod `Evaluate` do metody, aby wyświetlić wartość RMS:

[!code-csharp[DisplayRMS](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a>Użyj modelu dla prognoz

Utwórz `TestSinglePrediction` metodę, tuż `Evaluate` po tej metodzie, używając następującego kodu:

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

Metoda `TestSinglePrediction` wykonuje następujące zadania:

* Tworzy pojedynczy komentarz danych testowych.
* Prognozuje kwotę taryfy na podstawie danych testowych.
* Łączy dane testowe i prognozy dla raportowania.
* Wyświetla przewidywane wyniki.

Dodaj wywołanie do nowej `Main` metody z metody, bezpośrednio w wywołaniu `Evaluate` metody, przy użyciu następującego kodu:

[!code-csharp[CallTestSinglePrediction](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#20 "Call the TestSinglePrediction method")]

Użyj `PredictionEngine` do przewidywania taryfy, dodając następujący `TestSinglePrediction()`kod do:

[!code-csharp[MakePredictionEngine](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#22 "Create the PredictionFunction")]

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest interfejs emanujący interfejsu API wygody, który umożliwia wykonywanie przewidywanie na pojedyncze wystąpienie danych. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny dla nici. Dopuszczalne jest stosowanie w środowiskach jednowątkowych lub prototypowych. Aby zwiększyć wydajność i bezpieczeństwo wątków `PredictionEnginePool` w środowiskach [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) produkcyjnych, należy użyć usługi, która tworzy obiektów [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do użycia w całej aplikacji. Zobacz ten przewodnik, jak [ `PredictionEnginePool` używać w ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

> [!NOTE]
> `PredictionEnginePool`rozszerzenie usługi jest obecnie w wersji zapoznawczej.

Ten samouczek używa jednej podróży testowej w tej klasie. Później można dodać inne scenariusze do eksperymentowania z modelem. Dodaj podróż do testowania przewidywania kosztu przez `TestSinglePrediction()` uczonego modelu `TaxiTrip`w metodzie, tworząc wystąpienie:

[!code-csharp[PredictionData](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#23 "Create test data for single prediction")]

Następnie przewiduj taryfę na podstawie pojedynczego wystąpienia `PredictionEngine` danych przejazdu taksówką i przekaż `TestSinglePrediction()` ją do następującego wiersza jako następnych wierszy kodu w metodzie:

[!code-csharp[Predict](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#24 "Create a prediction of taxi fare")]

[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) Funkcja sprawia, że przewidywanie dla pojedynczego wystąpienia danych.

Aby wyświetlić przewidywaną taryfę określonej podróży, dodaj następujący `TestSinglePrediction` kod do metody:

[!code-csharp[Predict](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#25 "Display the prediction.")]

Uruchom program, aby zobaczyć przewidywaną taryfę taksówki dla twojego przypadku testowego.

Gratulacje! Teraz pomyślnie skonstruowano model uczenia maszynowego do przewidywania taryf przejazdów taksówką, oceniałeś jego dokładność i używałeś go do tworzenia prognoz. Kod źródłowy tego samouczka można znaleźć w repozytorium GitHub [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction)

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> * Przygotowywanie i rozumienie danych
> * Tworzenie potoku uczenia się
> * Ładowanie i przekształcanie danych
> * Wybierz algorytm uczenia się
> * Uczenie modelu
> * Ocena modelu
> * Użyj modelu dla prognoz

Przejdź do następnego samouczka, aby dowiedzieć się więcej.

> [!div class="nextstepaction"]
> [Klastrowanie zestawu danych Iris](iris-clustering.md)
