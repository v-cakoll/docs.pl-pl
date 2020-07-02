---
title: 'Samouczek: prognozowanie cen przy użyciu regresji'
description: W tym samouczku przedstawiono sposób tworzenia modelu regresji przy użyciu ML.NET do przewidywania cen, w oddziałach, w oddziałach, w oddziałach
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 0a8ab9ca07d2d83f41b40a3f5782e8e7e201976f
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803238"
---
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a>Samouczek: prognozowanie cen przy użyciu regresji z ML.NET

W tym samouczku przedstawiono sposób tworzenia [modelu regresji](../resources/glossary.md#regression) przy użyciu ml.NET do przewidywania cen, w oddziałach, w oddziałach, w oddziałach

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> * Przygotuj i poznanie danych
> * Załaduj i Przekształć dane
> * Wybierz algorytm uczenia
> * Uczenie modelu
> * Ocena modelu
> * Używanie modelu dla prognoz

## <a name="prerequisites"></a>Wymagania wstępne

* [Program Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowszy albo program visual Studio 2017 w wersji 15,6 lub nowszej z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core.

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. Utwórz **aplikację konsolową .NET Core** o nazwie "TaxiFarePrediction".

1. Utwórz katalog o nazwie *dane* w projekcie do przechowywania zestawu danych i plików modeli.

1. Zainstaluj pakiet NuGet **Microsoft.ml** :

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę **Przeglądaj** , wyszukaj pozycję **Microsoft.ml**, wybierz pakiet z listy, a następnie wybierz przycisk **Instaluj** . Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów. Wykonaj te same czynności dla pakietu NuGet **Microsoft. ml. FastTree** .

## <a name="prepare-and-understand-the-data"></a>Przygotuj i poznanie danych

1. Pobierz [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) i [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) zestawy danych i Zapisz je w folderze *danych* utworzonym w poprzednim kroku. Te zestawy danych są używane do uczenia modelu uczenia maszynowego, a następnie szacowania dokładnego modelu. Te zestawy danych pierwotnie pochodzą z [zestawu danych o podróży NYC TLC](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page).

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy każdy z \* plików CSV i wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.

1. Otwórz zestaw danych **taxi-fare-train.csv** i sprawdź nagłówki kolumn w pierwszym wierszu. Zapoznaj się z każdą kolumną. Zrozumienie danych i decydowanie o tym, które kolumny są **funkcjami** , a które są takie same jak **etykieta**.

`label`Jest to kolumna, która ma zostać przewidywalna. Identyfikowane `Features` są dane wejściowe, które dają model do przewidywania `Label` .

Podany zestaw danych zawiera następujące kolumny:

* **vendor_id:** Identyfikator dostawcy taksówki jest funkcją.
* **rate_code:** Typ szybkości podróży z taksówką jest funkcją.
* **passenger_count:** Liczba pasażerów w podróży to funkcja.
* **trip_time_in_secs:** Czas trwania podróży. Chcesz przewidzieć przejazd podróży przed ukończeniem podróży. W tej chwili nie wiesz, jak długo trwa podróż. W ten sposób czas podróży nie jest funkcją, a ta kolumna zostanie wykluczona z modelu.
* **trip_distance:** Odległość podróży to funkcja.
* **payment_type:** Forma płatności (karta kasowa lub kredytowa) to funkcja.
* **fare_amount:** Łączna liczba płatnych opłat za taksówkę to etykieta.

## <a name="create-data-classes"></a>Tworzenie klas danych

Utwórz klasy dla danych wejściowych i prognoz:

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj**  >  **nowy element**.
1. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *TaxiTrip.cs*. Następnie wybierz przycisk **Dodaj** .
1. Dodaj następujące `using` dyrektywy do nowego pliku:

   [!code-csharp[AddUsings](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/TaxiTrip.cs#1 "Add necessary usings")]

Usuń istniejącą definicję klasy i Dodaj następujący kod, który ma dwie klasy `TaxiTrip` i `TaxiTripFarePrediction` , do pliku *TaxiTrip.cs* :

[!code-csharp[DefineTaxiTrip](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip`jest klasą danych wejściowych i zawiera definicje dla każdej z kolumn zestawu danych. Użyj <xref:Microsoft.ML.Data.LoadColumnAttribute> atrybutu, aby określić indeksy kolumn źródłowych w zestawie danych.

`TaxiTripFarePrediction`Klasa reprezentuje przewidywane wyniki. Ma pojedyncze pole zmiennoprzecinkowe, `FareAmount` z `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> zastosowanym atrybutem. W przypadku zadania regresji kolumna **Score** zawiera wartości przewidywanych etykiet.

> [!NOTE]
> Użyj `float` typu, aby reprezentować wartości zmiennoprzecinkowe w klasach danych wejściowych i prognoz.

### <a name="define-data-and-model-paths"></a>Definiowanie ścieżek danych i modeli

Dodaj następujące dodatkowe `using` instrukcje na początku pliku *program.cs* :

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#1 "Add necessary usings")]

Należy utworzyć trzy pola do przechowywania ścieżek do plików z zestawami danych i plik, aby zapisać model:

* `_trainDataPath`zawiera ścieżkę do pliku z zestawem danych używanym do uczenia modelu.
* `_testDataPath`zawiera ścieżkę do pliku z zestawem danych używanym do szacowania modelu.
* `_modelPath`zawiera ścieżkę do pliku, w którym jest przechowywany przeszkolony model.

Dodaj następujący kod bezpośrednio powyżej metody, `Main` Aby określić te ścieżki i dla `_textLoader` zmiennej:

[!code-csharp[InitializePaths](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#2 "Define variables to store the data file paths")]

Wszystkie operacje ML.NET są uruchamiane w [klasie MLContext](xref:Microsoft.ML.MLContext). Inicjowanie `mlContext` tworzy nowe środowisko ml.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest to podobne, pojęciowo do `DBContext` w Entity Framework.

### <a name="initialize-variables-in-main"></a>Inicjuj zmienne w głównym

Zastąp `Console.WriteLine("Hello World!")` wiersz w `Main` metodzie poniższym kodem, aby zadeklarować i zainicjować `mlContext` zmienną:

[!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#3 "Create the ML Context")]

Dodaj następujący kod jako następny wiersz kodu w `Main` metodzie, aby wywołać `Train` metodę:

[!code-csharp[Train](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#5 "Train your model")]

`Train()`Metoda wykonuje następujące zadania:

* Ładuje dane.
* Wyodrębnia i przekształca dane.
* Pociąga za siebie model.
* Zwraca model.

`Train`Metoda pociąga za niego model. Utwórz tę metodę tuż poniżej `Main` , używając następującego kodu:

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a>Ładowanie i Przekształcanie danych

ML.NET używa [klasy IDataView](xref:Microsoft.ML.IDataView) jako elastycznej, wydajnej metody opisywania danych tabelarycznych lub tekstowych. `IDataView`może ładować pliki tekstowe lub w czasie rzeczywistym (na przykład bazy danych SQL lub pliki dzienników). Dodaj następujący kod jako pierwszy wiersz `Train()` metody:

[!code-csharp[LoadTrainData](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#6 "loading training dataset")]

W miarę jak ma być przewidywana taryfa za podróż, `FareAmount` kolumna jest `Label` przewidywalna (dane wyjściowe modelu). Użyj `CopyColumnsEstimator` klasy transformacji, aby skopiować `FareAmount` i dodać następujący kod:

[!code-csharp[CopyColumnsEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#7 "Use the CopyColumnsEstimator")]

Algorytm, który pociąga za ten model, wymaga funkcji **liczbowych** , dlatego należy przekształcić wartości danych kategorii (, `VendorId` `RateCode` i `PaymentType` ) na liczby ( `VendorIdEncoded` , `RateCodeEncoded` i `PaymentTypeEncoded` ). W tym celu należy użyć klasy transformacji [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) , która przypisuje różne wartości klucza liczbowego do różnych wartości w każdej z kolumn, a następnie Dodaj następujący kod:

[!code-csharp[OneHotEncodingEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#8 "Use the OneHotEncodingEstimator")]

Ostatnim krokiem w przygotowaniu danych jest połączenie wszystkich kolumn funkcji w kolumnie **funkcje** przy użyciu `mlContext.Transforms.Concatenate` klasy transformacji. Domyślnie algorytm uczenia przetwarza tylko funkcje z kolumny **Features** . Dodaj następujący kod:

[!code-csharp[ColumnConcatenatingEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a>Wybierz algorytm uczenia

Ten problem polega na przewidywaniu opłaty za podróż z taksówką w Nowym Jorku. Na pierwszy rzut oka może wydawać się, że zależy tylko od podróży. Jednak dostawcy taksówki w Nowym Jorku naliczane są różne kwoty dla innych czynników, takich jak dodatkowe pasażerowie lub płacisz kartą kredytową zamiast gotówki. Chcesz przewidzieć wartość ceny, która jest wartością rzeczywistą, opartą na innych czynnikach w zestawie danych. W tym celu należy wybrać zadanie uczenia [maszynowego](../resources/glossary.md#regression) .

Dołącz zadanie uczenia maszynowego [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) do definicji transformacji danych, dodając następujący kod jako następny wiersz kodu w `Train()` :

[!code-csharp[FastTreeRegressionTrainer](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a>Uczenie modelu

Dopasuj model do szkolenia `dataview` i zwróć przeszkolony model, dodając następujący wiersz kodu do `Train()` metody:

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#11 "Train the model")]

Metoda [dopasowywania ()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) pociąga za siebie model poprzez transformowanie zestawu danych i zastosowanie szkolenia.

Zwróć przeszkolony model z następującym wierszem kodu w `Train()` metodzie:

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a>Ocena modelu

Następnie Oceń wydajność modelu z danymi testowymi w celu zapewnienia jakości i weryfikacji. Utwórz `Evaluate()` metodę, tuż po `Train()` , przy użyciu następującego kodu:

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

`Evaluate`Metoda wykonuje następujące zadania:

* Ładuje zestaw danych testowych.
* Tworzy ewaluatora regresji.
* Oblicza model i tworzy metryki.
* Wyświetla metryki.

Dodaj wywołanie do nowej metody z `Main` metody, bezpośrednio pod `Train` wywołaniem metody, przy użyciu następującego kodu:

[!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#14 "Call the Evaluate method")]

Załaduj zestaw danych testowych przy użyciu metody [LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) . Oceń model przy użyciu tego zestawu danych jako sprawdzenie jakości, dodając następujący kod w `Evaluate` metodzie:

[!code-csharp[LoadTestDataset](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#15 "Load the test dataset")]

Następnie Przekształć `Test` dane, dodając następujący kod do `Evaluate()` :

[!code-csharp[PredictWithTransformer](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#16 "Predict using the Transformer")]

Metoda [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) umożliwia prognozowanie wierszy wejściowych zestawu danych testowych.

`RegressionContext.Evaluate`Metoda oblicza metryki jakości dla `PredictionModel` użycia określonego zestawu danych. Zwraca <xref:Microsoft.ML.Data.RegressionMetrics> obiekt, który zawiera ogólne metryki obliczone przez oszacowania regresji.

Aby wyświetlić je w celu określenia jakości modelu, należy najpierw uzyskać metryki. Dodaj następujący kod w następnym wierszu `Evaluate` metody:

[!code-csharp[ComputeMetrics](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#17 "Compute Metrics")]

Po zestawie prognoz Metoda [oceny ()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) ocenia model, który porównuje wartości przewidywane z wartością rzeczywistą `Labels` w testowanym zestawie danych i zwraca metryki dotyczące sposobu działania modelu.

Dodaj następujący kod, aby ocenić model i utworzyć metryki oceny:

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

[RSquared](../resources/glossary.md#coefficient-of-determination) jest kolejną metryką oceny dla modeli regresji. RSquared przyjmuje wartości z zakresu od 0 do 1. Im bliżej wartości jest 1, tym lepszy jest model. Dodaj następujący kod do metody, `Evaluate` Aby wyświetlić wartość RSquared:

[!code-csharp[DisplayRSquared](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#18 "Display the RSquared metric.")]

[RMS](../resources/glossary.md#root-of-mean-squared-error-rmse) jest jedną z metryk oceny modelu regresji. Im niższa wartość, tym lepszy jest model. Dodaj następujący kod do metody, `Evaluate` Aby wyświetlić wartość RMS:

[!code-csharp[DisplayRMS](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a>Używanie modelu dla prognoz

Utwórz `TestSinglePrediction` metodę, tuż po `Evaluate` metodzie, przy użyciu następującego kodu:

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

`TestSinglePrediction`Metoda wykonuje następujące zadania:

* Tworzy pojedynczy komentarz dotyczący danych testowych.
* Przewiduje wartość opłaty za przejazd na podstawie danych testowych.
* Łączy dane testowe i prognozy na potrzeby raportowania.
* Wyświetla przewidywane wyniki.

Dodaj wywołanie do nowej metody z `Main` metody, bezpośrednio pod `Evaluate` wywołaniem metody, przy użyciu następującego kodu:

[!code-csharp[CallTestSinglePrediction](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#20 "Call the TestSinglePrediction method")]

Użyj `PredictionEngine` do przewidywania taryfy, dodając następujący kod do `TestSinglePrediction()` :

[!code-csharp[MakePredictionEngine](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#22 "Create the PredictionFunction")]

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest WYGODNYm interfejsem API, który umożliwia prognozowanie jednego wystąpienia danych. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny wątkowo. Jest to możliwe do użycia w środowiskach wielowątkowych lub prototypowych. Aby zwiększyć wydajność i bezpieczeństwo wątków w środowiskach produkcyjnych, należy użyć `PredictionEnginePool` usługi, która tworzy [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) obiekty do użycia w całej aplikacji. Zapoznaj się z tym przewodnikiem dotyczącym [korzystania `PredictionEnginePool` z programu w ASP.NET Core INTERNETowym interfejsie API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

> [!NOTE]
> `PredictionEnginePool`rozszerzenie usługi jest obecnie w wersji zapoznawczej.

Ten samouczek używa jednej podróży testowej w tej klasie. Później możesz dodać inne scenariusze, aby eksperymentować z modelem. Dodaj podróż, aby przetestować przeszkolony model kosztów w `TestSinglePrediction()` metodzie, tworząc wystąpienie `TaxiTrip` :

[!code-csharp[PredictionData](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#23 "Create test data for single prediction")]

Następnie należy przewidzieć opłaty za pośrednictwem jednego wystąpienia danych podróży z taksówką i przekazać je do programu, `PredictionEngine` dodając następujące elementy jako kolejne wiersze kodu w `TestSinglePrediction()` metodzie:

[!code-csharp[Predict](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#24 "Create a prediction of taxi fare")]

Funkcja [przewidywania ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) dokonuje prognozowania dla pojedynczego wystąpienia danych.

Aby wyświetlić przewidywaną opłatę za określoną podróż, Dodaj następujący kod do `TestSinglePrediction` metody:

[!code-csharp[Predict](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#25 "Display the prediction.")]

Uruchom program, aby zobaczyć przewidywalną opłatę za taksówkę w przypadku testowym.

Gratulacje! Pomyślnie skompilowano model uczenia maszynowego na potrzeby przewidywania opłat za podróż z użyciem taksówki, oceny jego dokładności i używania go do prognozowania. Kod źródłowy dla tego samouczka można znaleźć w repozytorium GitHub [/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) .

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> * Przygotuj i poznanie danych
> * Tworzenie potoku uczenia
> * Załaduj i Przekształć dane
> * Wybierz algorytm uczenia
> * Uczenie modelu
> * Ocena modelu
> * Używanie modelu dla prognoz

Przejdź do następnego samouczka, aby dowiedzieć się więcej.

> [!div class="nextstepaction"]
> [Klastrowanie zestawu danych Iris](iris-clustering.md)
