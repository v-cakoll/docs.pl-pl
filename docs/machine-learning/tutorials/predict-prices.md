---
title: 'Samouczek: Przewidywanie ceny za pomocą regresji'
description: W tym samouczku pokazano, jak do zbudowania modelu regresji przy użyciu strukturze ML.NET do prognozowania cen, w szczególności taryf taksówek w Nowym Jorku.
author: jralexander
ms.author: johalex
ms.date: 05/09/2019
ms.topic: tutorial
ms.custom: mvc, seodec18, title-hack-0516
ms.openlocfilehash: 40f70b6d89bf19ae0b20cb00d56e9f7dceb48f61
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2019
ms.locfileid: "66377794"
---
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a>Samouczek: Przewidywanie ceny za pomocą regresji za pomocą platformy ML.NET

W tym samouczku przedstawiono sposób tworzenia [modelu regresji](../resources/glossary.md#regression) przy użyciu strukturze ML.NET do prognozowania cen, w szczególności taryf taksówek w Nowym Jorku.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Przygotuj i zrozumieć dane
> * Ładowania i przekształcania danych
> * Wybieranie algorytmu uczenia
> * Uczenie modelu
> * Ocena modelu
> * Na użytek modelu prognozy

## <a name="prerequisites"></a>Wymagania wstępne

* [Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. Tworzenie **aplikacji konsoli .NET Core** o nazwie "TaxiFarePrediction".

1. Utwórz katalog o nazwie *danych* w projekcie do przechowywania plików modelu i zestawu danych.

1. Zainstaluj **Microsoft.ML** pakietu NuGet:

    W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz opcję **Przeglądaj** kartę, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku. Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych. Tym samym **Microsoft.ML.FastTree** pakietu Nuget.

## <a name="prepare-and-understand-the-data"></a>Przygotuj i zrozumieć dane

1. Pobierz [taksówek taryfy train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) i [taksówek taryfy test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) danych ustawia i zapisywanie ich *danych* folderu utworzonego w poprzednim kroku. Używamy tych zestawów danych do nauczenia modelu uczenia maszynowego, a następnie ocenę, jak dokładna jest model. Te zestawy danych są pierwotnie z [zestawu danych podróży taksówek TLC NYC](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy każdy z \*plików CSV, a następnie wybierz **właściwości**. W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.

1. Otwórz **taksówek taryfy train.csv** dane ustawić i spójrz na nagłówki kolumn w pierwszym wierszu. Przyjrzyj się każdej z kolumn. Zrozumieć dane i zdecydować, które kolumny są **funkcji** i który z nich jest **etykiety**.

`label` Kolumna, która chcesz przewidzieć. Wskazywanego przez nią `Features`to dane wejściowe, nadaj model do przewidywania `Label`.

Podany zestaw danych zawiera następujące kolumny:

* **vendor_id:** Identyfikator dostawcy taksówek jest funkcją.
* **rate_code:** Typ stawki podróży taksówek jest funkcją.
* **passenger_count:** Liczba osób w ramach wyzwolenie jest funkcją.
* **trip_time_in_secs:** Ilość czasu trwania podróży. Chcesz przewidzieć opłacie wyzwolenie przed zakończeniem podróż. W tym momencie nie wiesz, jak długo podróży zajęłoby. Dlatego czas podróży nie jest funkcją i będzie Wyklucz tę kolumnę z modelu.
* **trip_distance:** Odległość wyzwolenie jest funkcją.
* **payment_type:** Sposób zapłaty (pieniężnych lub karta kredytowa) jest funkcją.
* **fare_amount:** Taryfy taksówek łączna liczba płatnych jest etykieta.

## <a name="create-data-classes"></a>Tworzenie klas danych

Tworzenie klasy dla danych wejściowych i prognozy są tym:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.
1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *TaxiTrip.cs*. Następnie wybierz **Dodaj** przycisku.
1. Dodaj następujący kod `using` dyrektywy do nowego pliku:

   [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

Usuń istniejącą definicję klasy i Dodaj następujący kod, który zawiera dwie klasy `TaxiTrip` i `TaxiTripFarePrediction`, *TaxiTrip.cs* pliku:

[!code-csharp[DefineTaxiTrip](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip` jest klasą danych wejściowych i ma definicje dla każdej z kolumn w zestawie danych. Użyj <xref:Microsoft.ML.Data.LoadColumnAttribute> atrybutu, aby określić indeksów kolumny źródłowe w zestawie danych.

`TaxiTripFarePrediction` Klasa reprezentuje wyników. Ma pola pojedynczego `FareAmount`, za pomocą `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> zastosowany. W przypadku zadań regresji **wynik** kolumna zawiera wartości prognozowanej etykiet.

> [!NOTE]
> Użyj `float` typu do reprezentowania wartości zmiennoprzecinkowych w klasach danych wejściowych i prognozowania.

### <a name="define-data-and-model-paths"></a>Zdefiniować dane oraz model ścieżki

Dodaj następujące dodatkowe `using` instrukcji na górze *Program.cs* pliku:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

Musisz utworzyć trzy pola do przechowywania ścieżek do plików z zestawami danych i plik, aby zapisać modelu:

* `_trainDataPath` zawiera ścieżkę do pliku z zestawem danych, używane do trenowania modelu.
* `_testDataPath` zawiera ścieżkę do pliku z zestawem danych, używane do oceny modelu.
* `_modelPath` zawiera ścieżkę do pliku, w którym przechowywany jest trenowanego modelu.

Dodaj następujący kod nad `Main` metodę, aby określić tych ścieżek i `_textLoader` zmiennej:

[!code-csharp[InitializePaths](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

Wszystkie operacje strukturze ML.NET uruchomić w [klasy MLContext](xref:Microsoft.ML.MLContext). Inicjowanie `mlContext` tworzy nowe środowisko strukturze ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Przypomina, model `DBContext` platformy Entity Framework.

### <a name="initialize-variables-in-main"></a>Inicjowanie zmiennych w głównym oknie

Zastąp `Console.WriteLine("Hello World!")` linię `Main` metody za pomocą następującego kodu, aby zadeklarować i zainicjować `mlContext` zmiennej:

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

Dodaj następujący kod jako następnego wiersza kodu w `Main` metodę do wywołania `Train` metody:

[!code-csharp[Train](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

`Train()` Metoda wykonuje następujące zadania:

* Służy do ładowania danych.
* Wyodrębnia i przekształca dane.
* Szkolenie modeli modelu.
* Zwraca wartość modelu.

`Train` Metoda szkolenie modeli modelu. Tej metody Create, tuż poniżej `Main`, używając następującego kodu:

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a>Obciążenia i przekształcania danych

Używa strukturze ML.NET [klasy IDataView](xref:Microsoft.ML.IDataView) jako dane tabelaryczne numeryczny lub tekst opisujący sposób elastyczne i wydajne. `IDataView` można załadować albo pliki tekstowe lub w czasie rzeczywistym (na przykład SQL bazy danych lub pliki dziennika). Dodaj następujący kod jako pierwsza linia `Train()` metody:

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

Do przewidywania taksówek taryfy podróży, możesz dodać dowolną `FareAmount` kolumna jest `Label` czy będzie przewidzieć (dane wyjściowe modelu) użyj `CopyColumnsEstimator` klasy przekształcenia do skopiowania `FareAmount`i Dodaj następujący kod: 

[!code-csharp[CopyColumnsEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

Algorytm, który przygotowuje model wymaga **liczbowych** funkcji, więc do przekształcania danych podzielonych na kategorie (`VendorId`, `RateCode`, i `PaymentType`) wartości liczb (`VendorIdEncoded`, `RateCodeEncoded`, i `PaymentTypeEncoded`). Aby to zrobić, należy użyć [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) klasy transformacji, która przypisuje różnych liczbowe wartości różne wartości w każdej z kolumn klucza i Dodaj następujący kod:

[!code-csharp[OneHotEncodingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

Ostatnim krokiem w przygotowaniu danych łączy wszystkie kolumny funkcji do **funkcji** przy użyciu kolumny `mlContext.Transforms.Concatenate` klasy przekształcenia. Domyślnie algorytmu uczenia przetwarza tylko funkcje z **funkcji** kolumny. Dodaj następujący kod:

[!code-csharp[ColumnConcatenatingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a>Wybieranie algorytmu uczenia

Ten problem dotyczy Prognozowanie taryfy podróży taksówek w Nowym Jorku. Na pierwszy rzut oka może wydawać się po prostu zależą dystans. Jednak dostawców taksówek w Nowym Jorku jest opłata w wysokości zmiennych ilości dla innych czynników, takich jak dodatkowe osób lub płacenia kartą kredytową zamiast środków pieniężnych. Chcesz przewidzieć wartość ceny, który jest wartością rzeczywistego na podstawie innych czynników, w zestawie danych. Aby to zrobić, możesz wybrać [regresji](../resources/glossary.md#regression) machine learning zadania.

Dołącz [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) zadania uczenia maszyny z definicjami przekształcania danych, dodając następujące jako następnego wiersza kodu w `Train()`:

[!code-csharp[FastTreeRegressionTrainer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a>Uczenie modelu

Dopasuj do szkolenia modelu `dataview` i zwracają trenowanego modelu, dodając następujący wiersz kodu w `Train()` metody:

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

[Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) metoda szkolenie modeli modelu przekształcania zestawu danych i stosując szkolenia.

Zwróć uczonego modelu o następujący wiersz kodu w `Train()` metody:

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a>Ocena modelu

Następnie ocenić wydajność modelu przy użyciu danych testowych do zapewniania jakości i sprawdzania poprawności. Tworzenie `Evaluate()` metody tuż za `Train()`, używając następującego kodu:

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

`Evaluate` Metoda wykonuje następujące zadania:

* Ładuje zestawy danych testowych.
* Tworzy ewaluatora regresji.
* Oblicza model i tworzy metryki.
* Przedstawia metryki.

Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `Train` wywołania metody, używając następującego kodu:

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Call the Evaluate method")]

Obciążenia za pomocą zestawu danych testowych [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) metody. Ocena modelu za pomocą tego zestawu danych w celu sprawdzenia jakości, dodając następujący kod w `Evaluate` metody:

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

Następnie przekształcić `Test` danych przez dodanie poniższego kodu `EvaluateModel()`:

[!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metody sprawia, że prognoz dotyczących testu wiersze danych wejściowych zestawu danych.

`RegressionContext.Evaluate` Metoda oblicza metryk jakości `PredictionModel` przy użyciu określonego zestawu danych. Zwraca <xref:Microsoft.ML.Data.RegressionMetrics> obiekt, który zawiera metryki ogólną obliczone przez ewaluatory regresji. 

Aby je wyświetlić, aby określić jakość modelu, należy pobrać pierwszy metryki. Dodaj następujący kod w następnym wierszu `Evaluate` metody:

[!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

Po utworzeniu prognozowania ustawiona, [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) metoda ocenia modelu, który porównuje przewidywane wartości z rzeczywistych `Labels` w testowego zestawu danych i zwraca metryki dotyczące jak działa model.

Dodaj następujący kod do ewaluacji modelu i generować metryk oceny:

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

[RSquared](../resources/glossary.md#coefficient-of-determination) jest kolejną metrykę oceny, modele regresji. RSquared przyjmuje wartości od 0 do 1. Im bliżej jego wartość jest bliższa 1, tym lepiej jest model. Dodaj następujący kod do `Evaluate` metodę, aby wyświetlić wartość RSquared:

[!code-csharp[DisplayRSquared](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#18 "Display the RSquared metric.")]

[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) jest jedną z metryk oceny modelu regresji. Im niższa, w tym lepsze model jest. Dodaj następujący kod do `Evaluate` metodę, aby wyświetlić wartość RMS:

[!code-csharp[DisplayRMS](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a>Na użytek modelu prognozy

Tworzenie `TestSinglePrediction` metody tuż za `Evaluate` metody, używając następującego kodu:

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

`TestSinglePrediction` Metoda wykonuje następujące zadania:

* Tworzy pojedynczy komentarz danych testowych.
* Prognozuje kwota taryfy oparte na danych testowych.
* Łączy w sobie testowanie, danych i prognoz dla raportowania.
* Wyświetla przewidywane wyniki.

Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `Evaluate` wywołania metody, używając następującego kodu:

[!code-csharp[CallTestSinglePrediction](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#20 "Call the TestSinglePrediction method")]

Użyj `PredictionEngine` do prognozowania opłatę, dodając następujący kod do `TestSinglePrediction()`:

[!code-csharp[MakePredictionEngine](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]

[Klasy PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest wygoda interfejsu API, dzięki czemu można przekazać pojedyncze wystąpienie danych, a następnie wykonaj prognozę na nim.

Ten samouczek używa test dwustronnej tej klasy. Później możesz dodać inne scenariusze, aby eksperymentować z modelu. Dodaj podróży do testowania uczonego modelu prognozowania kosztu `TestSinglePrediction()` metody przez utworzenie wystąpienia `TaxiTrip`:

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

Następnie przewidzieć opłatę, w oparciu o jedno wystąpienie danych taksówek w podróży i przekazać go do `PredictionEngine` przez dodanie poniższego jako z następującymi wierszami kodu w `TestSinglePrediction()` metody:

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) funkcja sprawia, że prognozowania w pojedynczym wystąpieniu danych.

Aby wyświetlić przewidywane opłacie określonego podróży, Dodaj następujący kod do `TestSinglePrediction` metody:

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

Uruchom program, aby zobaczyć taryfy przewidywane taksówek dla przypadków testowych.

Gratulacje! Już teraz pomyślnie wbudowany model uczenia maszynowego do przewidywania taksówek podróży opłaty, ocenić jego dokładności i używana do tworzenia prognoz. Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) repozytorium GitHub.

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
> * Przygotuj i zrozumieć dane
> * Tworzenie potoku uczenia
> * Ładowania i przekształcania danych
> * Wybieranie algorytmu uczenia
> * Uczenie modelu
> * Ocena modelu
> * Na użytek modelu prognozy

Przejdź do następnego samouczka, aby dowiedzieć się więcej.

> [!div class="nextstepaction"]
> [Klastrowanie zestawu danych Iris](iris-clustering.md)
