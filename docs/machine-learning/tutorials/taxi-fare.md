---
title: Przewidywanie ceny za pomocą uczeń regresji za pomocą platformy ML.NET
description: Przewidywanie ceny za pomocą platformy ML.NET przy użyciu uczeń regresji.
author: aditidugar
ms.author: johalex
ms.date: 03/05/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 543411f58f2d7c5c4e8658bd90cf52c7a3291ec3
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57678409"
---
# <a name="tutorial-predict-prices-using-a-regression-learner-with-mlnet"></a>Samouczek: Przewidywanie ceny za pomocą uczeń regresji za pomocą platformy ML.NET

W tym samouczku pokazano, jak za pomocą strukturze ML.NET tworzyć [modelu regresji](../resources/glossary.md#regression) do prognozowania cen, w szczególności, taksówek w Nowym Jorku cen w klasie ekonomicznej.

> [!NOTE]
> W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do struktury ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Obecnie używasz tego samouczka, a powiązane próbki **strukturze ML.NET wersji 0.10**. Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Omówienie problemu
> * Wybierz zadanie uczenia odpowiedniej maszyny
> * Przygotuj i zrozumieć dane
> * Tworzenie potoku uczenia
> * Ładowania i przekształcania danych
> * Wybieranie algorytmu uczenia
> * Uczenie modelu
> * Ocena modelu
> * Na użytek modelu prognozy

## <a name="prerequisites"></a>Wymagania wstępne

* [Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".

## <a name="understand-the-problem"></a>Omówienie problemu

Ten problem dotyczy Prognozowanie opłacie podróż taksówek w Nowym Jorku. Na pierwszy rzut oka może wydawać się po prostu zależą dystans. Jednak dostawców taksówek w Nowym Jorku jest opłata w wysokości zmiennych ilości dla innych czynników, takich jak dodatkowe osób lub płacenia kartą kredytową zamiast środków pieniężnych.

## <a name="select-the-appropriate-machine-learning-task"></a>Wybierz zadanie uczenia odpowiedniej maszyny

Chcesz przewidzieć wartość ceny, który jest wartością rzeczywistego na podstawie innych czynników, w zestawie danych. Aby zrobić, możesz wybrać [regresji](../resources/glossary.md#regression) machine learning zadania.

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. Otwórz program Visual Studio 2017. Wybierz **pliku** > **New** > **projektu** z paska menu. W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła następuje **platformy .NET Core** węzła. Następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonu projektu. W **nazwa** pole tekstowe, wpisz "TaxiFarePrediction", a następnie wybierz **OK** przycisku.

1. Utwórz katalog o nazwie *danych* w projekcie do przechowywania plików modelu i zestaw danych:

    W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj** > **nowy Folder**. Wpisz "Dane", a następnie naciśnij klawisz Enter.

1. Zainstaluj **Microsoft.ML** pakietu NuGet:

    W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz opcję **Przeglądaj** kartę, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku. Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.

## <a name="prepare-and-understand-the-data"></a>Przygotuj i zrozumieć dane

1. Pobierz [taksówek taryfy train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) i [taksówek taryfy test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) danych ustawia i zapisywanie ich *danych* folderu utworzonego w poprzednim kroku. Używamy tych zestawów danych do nauczenia modelu uczenia maszynowego, a następnie ocenę, jak dokładna jest model. Te zestawy danych są pierwotnie z [zestawu danych podróży taksówek TLC NYC](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy każdy z \*plików CSV, a następnie wybierz **właściwości**. W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.

1. Otwórz **taksówek taryfy train.csv** dane ustawić i spójrz na nagłówki kolumn w pierwszym wierszu. Przyjrzyj się każdej z kolumn. Zrozumieć dane i zdecydować, które kolumny są **funkcji** i który z nich jest **etykiety**.

**Etykiety** to identyfikator kolumny, aby przewidzieć. Wskazywanego przez nią **funkcji** są używane do prognozowania etykiety.

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

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

Usuń istniejącą definicję klasy i Dodaj następujący kod, który zawiera dwie klasy `TaxiTrip` i `TaxiTripFarePrediction`, *TaxiTrip.cs* pliku:

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip` jest klasą danych wejściowych i ma definicje dla każdej z kolumn w zestawie danych. Użyj <xref:Microsoft.ML.Data.ColumnAttribute> atrybutu, aby określić indeksów kolumny źródłowe w zestawie danych.

`TaxiTripFarePrediction` Klasa reprezentuje wyników. Ma pola pojedynczego `FareAmount`, za pomocą `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> zastosowany. W przypadku zadań regresji **wynik** kolumna zawiera wartości prognozowanej etykiet.

> [!NOTE]
> Użyj `float` typu do reprezentowania wartości zmiennoprzecinkowych w klasach danych wejściowych i prognozowania.

## <a name="define-data-and-model-paths"></a>Zdefiniować dane oraz model ścieżki

Dodaj następujące dodatkowe `using` instrukcji na górze *Program.cs* pliku:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

Musisz utworzyć trzy pola do przechowywania ścieżek do plików z zestawami danych i plik Aby zapisać model i zmienną globalną, uzyskać `TextLoader`:

* `_trainDataPath` zawiera ścieżkę do pliku z zestawem danych, używane do trenowania modelu.
* `_testDataPath` zawiera ścieżkę do pliku z zestawem danych, używane do oceny modelu.
* `_modelPath` zawiera ścieżkę do pliku, w którym przechowywany jest trenowanego modelu.
* `_textLoader` jest <xref:Microsoft.ML.Data.TextLoader> używany do ładowania i przekształcić zestawy danych.

Dodaj następujący kod nad `Main` metodę, aby określić tych ścieżek i `_textLoader` zmiennej:

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

Podczas tworzenia modelu za pomocą platformy ML.NET rozpoczyna się od utworzenia kontekście uczenia Maszynowego. To jest porównywalna koncepcyjnie za pomocą `DbContext` platformy Entity Framework. Środowisko dostarcza kontekst dla zadania uczenia maszyny używanej dla wyjątku, śledzenia i rejestrowania.

### <a name="initialize-variables-in-main"></a>Inicjowanie zmiennych w głównym oknie

Utwórz zmienną o nazwie `mlContext` i zainicjuj ją o nowe wystąpienie klasy `MLContext`.  Zastąp `Console.WriteLine("Hello World!")` wiersz poniższym kodem w `Main` metody:

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

Następnie do Instalatora w celu załadowania zainicjować danych `_textLoader` zmienna globalna, aby można było użyć go ponownie. Po utworzeniu `TextLoader`, są przekazywane w kontekście potrzebne i <xref:Microsoft.ML.Data.TextLoader.Arguments> klasy, która umożliwia dostosowanie. Określ schemat danych, przekazując tablicę <xref:Microsoft.ML.Data.TextLoader.Column> obiekty do `TextLoader` zawierająca wszystkie nazwy kolumn i ich typy. Zdefiniowany schemat danych wcześniej podczas tworzenia naszej `TaxiTrip` klasy.

`TextLoader` Klasa zwraca w pełni zainicjowane <xref:Microsoft.ML.Data.TextLoader>  

Aby zainicjować `_textLoader` zmienna globalna, aby można było użyć go ponownie w przypadku wymaganych zestawów danych, Dodaj następujący kod po `mlContext` inicjowania:

[!code-csharp[initTextLoader](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Initialize the TextLoader")]

Dodaj następujący kod jako następnego wiersza kodu w `Main` metodę do wywołania `Train` metody:

[!code-csharp[Train](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

`Train` Metoda wykonuje następujące zadania:

* Służy do ładowania danych.
* Wyodrębnia i przekształca dane.
* Szkolenie modeli modelu.
* Zapisuje modelu w postaci pliku zip.
* Zwraca wartość modelu.

`Train` Metoda szkolenie modeli modelu. Tej metody Create, tuż poniżej `Main`, używając następującego kodu:

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

Firma Microsoft kończy się sukcesem dwa parametry do `Train` metoda; `MLContext` kontekstu (`mlContext`) i ciągu dla ścieżki zestawu danych (`dataPath`). Zamierzamy ponownie użyć tej metody do ładowania zestawów danych.

## <a name="load-and-transform-data"></a>Obciążenia i przekształcania danych

Firma Microsoft będzie załadować dane przy użyciu `_textLoader` zmienna globalna z `dataPath` parametru. Zwraca <xref:Microsoft.Data.DataView.IDataView>. Jako dane wejściowe i wyjściowe transformacji `IDataView` jest typem potoku danych podstawowych porównywalne do `IEnumerable` dla `LINQ`.

W strukturze ML.NET dane są podobne do widoku SQL. Jest opóźnieniem ocenianą informatycznych i heterogenicznych. Obiekt jest pierwszą częścią potoku i służy do ładowania danych. W tym samouczku ładuje zestaw danych taksówek podróży informacje przydatne do prognozowania cen biletów. Służy do tworzenia modelu i szkoleń.

 Dodaj następujący kod jako pierwsza linia `Train` metody:

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

W następnych krokach nazywamy kolumny według nazw zdefiniowana w `TaxiTrip` klasy.

Gdy wiedzę i oceniane, domyślne wartości w modelu **etykiety** kolumny będą traktowane jako prawidłowe wartości do można przewidzieć. Ponieważ chcemy przewidzieć taryfy taksówek w podróży, skopiuj `FareAmount` kolumny na **etykiety** kolumny. Aby to zrobić, należy użyć `CopyColumnsEstimator` przekształcania klasy, a następnie dodaj następujący kod:

[!code-csharp[CopyColumnsEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

Algorytm, który przygotowuje model wymaga **liczbowych** funkcji, więc do przekształcania danych podzielonych na kategorie (`VendorId`, `RateCode`, i `PaymentType`) wartości jako liczby. Aby to zrobić, należy użyć `OneHotEncodingEstimator` klasy transformacji, która przypisuje różnych liczbowe wartości różne wartości w każdej z kolumn klucza i Dodaj następujący kod:

[!code-csharp[OneHotEncodingEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

Ostatnim krokiem w przygotowaniu danych łączy wszystkie kolumny funkcji do **funkcji** przy użyciu kolumny `ColumnConcatenatingEstimator` klasy przekształcenia. Domyślnie algorytmu uczenia przetwarza tylko funkcje z **funkcji** kolumny. Dodaj następujący kod:

[!code-csharp[ColumnConcatenatingEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a>Wybieranie algorytmu uczenia

Po dodaniu danych z potokiem i przekształcane na poprawny format danych wejściowych, możemy wybrać algorytm uczenia (**learner**). Uczeń przygotowuje modelu. Wybraliśmy **regresji** zadań dla tego problemu, więc używana `FastTreeRegressionTrainer` uczeń, który jest jednym z uczących regresji, dostarczone przez strukturze ML.NET.

`FastTreeRegressionTrainer` Uczeń korzysta, wzrostu gradientu. Ulepszanie gradientu jest techniką problemów regresji uczenia maszynowego. Zbudował każdego drzewa regresji, w sposób stopniowy. Aby zmierzyć błędów w każdym kroku i popraw go w ciągu następnych widoku jest używana funkcja utraty wstępnie zdefiniowane. Wynik jest model predykcyjny, który jest faktycznie zespołu słabszy modele predykcyjne. Aby uzyskać więcej informacji na temat zwiększania wyniku gradientu zobacz [wzmocnione regresji drzewa decyzyjnego](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).

Dodaj następujący kod do `Train` metody w celu dodania `FastTreeRegressionTrainer` kodowi przetwarzania danych dodane w poprzednim kroku:

[!code-csharp[FastTreeRegressionTrainer](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a>Uczenie modelu

Ostatnim krokiem jest do nauczenia modelu. Uczenie modelu, <xref:Microsoft.ML.Data.TransformerChain>zgodnie z zestawu danych, który został załadowany i przekształcone. Po zdefiniowaniu estymatora uczenie modelu przy użyciu <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> przy jednoczesnym zapewnieniu dane szkoleniowe już załadowana. Spowoduje to zwrócenie modelu na potrzeby prognozy. `pipeline.Fit()` szkolenie modeli potoku i zwraca `Transformer` na podstawie `DataView` przekazany. Eksperyment nie jest wykonywane, dopóki nie dzieje.

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

I to wszystko! Zostały pomyślnie uczony model, który potrafi prognozować taryf taksówek w NYC uczenia maszynowego. Teraz sklonujemy zapoznaj się z zrozumieć, jak dokładna jest model i Dowiedz się, jak go używać do prognozowania wartości taryfy taksówek.

### <a name="save-the-model"></a>Zapisz model

W tym momencie masz model typu <xref:Microsoft.ML.Data.TransformerChain> , można zintegrować wszystkich istniejących i nowych aplikacji .NET. Aby zapisać model do pliku zip, Dodaj następujący kod na końcu `Train` metody:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Save the model as a .zip file and return the model")]

## <a name="save-the-model-as-a-zip-file"></a>Zapisz model jako plik .zip

Tworzenie `SaveModelAsFile` metody tuż za `Train` metody, używając następującego kodu:

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

`SaveModelAsFile` Metoda wykonuje następujące zadania:

* Zapisuje modelu w postaci pliku zip.

Musimy utworzyć metodę, aby zapisać modelu mogą być używane ponownie i używane w innych aplikacjach. `ITransformer` Ma <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> metodę, która przyjmuje `_modelPath` globalne pola i <xref:System.IO.Stream>. Ponieważ chcemy zapisać ten element jako plik zip, utworzymy `FileStream` bezpośrednio przed wywołaniem `SaveTo` metody. Dodaj następujący kod do `SaveModelAsFile` metodę jako następny wiersz:

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Add the SaveTo Method")]

Firma Microsoft może także wyświetlać, której plik został zapisany przy pisaniu komunikatu konsoli, za pomocą `_modelPath`, używając następującego kodu:

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="evaluate-the-model"></a>Ocena modelu

Ocena jest procesem sprawdzania, jak model przewiduje wartości etykiet. Należy pamiętać, że model sprawia, że dobry prognozy na danych, który nie był używany do nauczenia modelu. Jednym ze sposobów, w tym celu jest podzielenie danych na zestaw szkoleniowy i zestawami danych testowych, co jest wykonywane w ramach tego samouczka. Skoro już uczony model na dane szkoleniowe, możesz zobaczyć, jak sprawdzi się na danych testowych.

`Evaluate` Metoda ocenia modelu. Aby utworzyć tę metodę, Dodaj następujący kod poniżej `Train` metody:

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

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Call the Evaluate method")]

Załadujemy zestawu danych testowych za pomocą wcześniej zainicjowane `_textLoader` zmienna globalna z `_testDataPath` globalne pole. Możesz ocenić modelu przy użyciu tego zestawu danych w celu sprawdzenia jakości. Dodaj następujący kod do `Evaluate` metody:

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

Następnie użyjemy usługi machine learning `model` parametru (transformatora), aby dane wejściowe funkcji i zwracają prognozy. Dodaj następujący kod do `Evaluate` metodę jako następny wiersz:

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

`RegressionContext.Evaluate` Metoda oblicza metryk jakości `PredictionModel` przy użyciu określonego zestawu danych. Zwraca <xref:Microsoft.ML.Data.RegressionMetrics> obiekt, który zawiera metryki ogólną obliczone przez ewaluatory regresji. Aby je wyświetlić, aby określić jakość modelu, należy pobrać pierwszy metryki. Dodaj następujący kod w następnym wierszu `Evaluate` metody:

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

Dodaj następujący kod do ewaluacji modelu i generować metryk oceny:

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

[RSquared](../resources/glossary.md#coefficient-of-determination) jest kolejną metrykę oceny, modele regresji. RSquared przyjmuje wartości od 0 do 1. Im bliżej jego wartość jest bliższa 1, tym lepiej jest model. Dodaj następujący kod do `Evaluate` metodę, aby wyświetlić wartość RSquared:

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#18 "Display the RSquared metric.")]

[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) jest jedną z metryk oceny modelu regresji. Im niższa, w tym lepsze model jest. Dodaj następujący kod do `Evaluate` metodę, aby wyświetlić wartość RMS:

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a>Na użytek modelu prognozy


## <a name="predict-the-test-data-outcome-with-the-model-and-a-single-comment"></a>Przewidywanie wyników danych testu za pomocą modelu i pojedynczego komentarza

Tworzenie `TestSinglePrediction` metody tuż za `Evaluate` metody, używając następującego kodu:

```csharp
private static void TestSinglePrediction(MLContext mlContext)
{

}
```

`TestSinglePrediction` Metoda wykonuje następujące zadania:

* Tworzy pojedynczy komentarz danych testowych.
* Prognozuje kwota taryfy oparte na danych testowych.
* Łączy w sobie testowanie, danych i prognoz dla raportowania.
* Wyświetla przewidywane wyniki.

Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `Evaluate` wywołania metody, używając następującego kodu:

[!code-csharp[CallTestSinglePrediction](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#20 "Call the TestSinglePrediction method")]

Ponieważ chcemy, aby załadować modelu z pliku zip wcześniej zapisany, utworzymy `FileStream` bezpośrednio przed wywołaniem `Load` metody. Dodaj następujący kod do `TestSinglePrediction` metodę jako następny wiersz:

[!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#21 "Load the model")]

Gdy `model` jest `transformer` który operuje na wiele wierszy danych, to bardzo typowy scenariusz w środowisku produkcyjnym jest na potrzeby prognoz na poszczególne przykłady. <xref:Microsoft.ML.PredictionEngine%602> Jest otoką, który jest zwracany z `CreatePredictionEngine` metody. Możemy dodać następujący kod, aby utworzyć `PredictionEngine` w następnym wierszu `TestSinglePrediction` metody:

[!code-csharp[MakePredictionEngine](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]
  
Ten samouczek używa test dwustronnej tej klasy. Później możesz dodać inne scenariusze, aby eksperymentować z modelu. Dodaj podróży do testowania uczonego modelu prognozowania kosztu `TestSinglePrediction` metody przez utworzenie wystąpienia `TaxiTrip`:

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

 Firma Microsoft może używać, aby przewidzieć opłatę, w oparciu o jedno wystąpienie danych taksówek w podróży. Aby uzyskać prognozę, użyj <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> na danych. Należy pamiętać, że dane wejściowe to ciąg, a model zawiera cechowania. Potok jest zsynchronizowany podczas uczenia i przewidywania. Nie trzeba napisać kod przetwarzania wstępnego cechowania specjalnie dla prognoz i zajmuje się tego samego interfejsu API i usługi batch jednorazowe prognozy.

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

Aby wyświetlić przewidywane opłacie określonego podróży, Dodaj następujący kod do `TestSinglePrediction` metody:

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

Uruchom program, aby zobaczyć taryfy przewidywane taksówek dla przypadków testowych.

Gratulacje! Już teraz pomyślnie wbudowany model uczenia maszynowego do przewidywania taksówek podróży opłaty, ocenić jego dokładności i używana do tworzenia prognoz. Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) repozytorium GitHub.

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Omówienie problemu
> * Wybierz zadanie uczenia odpowiedniej maszyny
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
