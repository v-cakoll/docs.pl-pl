---
title: W przypadku wykrycia anomalii sprzedaży, użyj strukturze ML.NET
description: Dowiedz się, jak używać strukturze ML.NET w scenariuszu wykrywania anomalii sprzedaży produktu zrozumienie, jak analizować dane pod kątem klamry anomalii i zmiany punktów podejmowanie odpowiednich działań.
ms.date: 05/06/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: b0dbd8793e2be3973c37f0f78bc0ddd61b6bfea7
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65066191"
---
# <a name="tutorial-use-mlnet-for-product-sales-anomaly-detection"></a>Samouczek: Na użytek strukturze ML.NET wykrywania anomalii sprzedaży produktu 

Ten przykładowy samouczek przedstawia wykrycia anomalii w danych sprzedaży produktu podejmowanie odpowiednich działań za pośrednictwem używany aplikację konsoli .NET Core przy użyciu strukturze ML.NET C# w programie Visual Studio 2019 r. 

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Ładowanie danych
> * Uczenie modelu do kolekcji wykrywania anomalii
> * Wykrywaj anomalie kolekcji za pomocą uczonego modelu
> * Uczenie modelu dla zmiany punktu anomalii
> * Wykrywaj anomalie punktu zmiany za pomocą uczonego modelu

Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repozytorium.

## <a name="prerequisites"></a>Wymagania wstępne

* [Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".

* [Zestaw danych sales.csv produktu](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> Dane formatu w `product-sales.csv` opiera się na zestawie danych "Szamponu sprzedaż za pośrednictwem trzech lat" pierwotnie skąd pochodzi z usługi DataMarket i udostępniane przez czas serii danych biblioteki (TSDL), utworzone przez Rob Hyndman. Zestaw danych "Szamponu sprzedaży przez trzy lata" uzyskał licencje w ramach licencji Open DataMarket domyślne.

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. Tworzenie **aplikacji konsoli .NET Core** o nazwie "ProductSalesAnomalyDetection".

2. Utwórz katalog o nazwie *danych* w projekcie, aby zapisać pliki zestawu danych.

3. Zainstaluj **pakietu NuGet Microsoft.ML**:

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.ML**, wybierz opcję **1.0.0** pakietu na liście, a następnie wybierz pozycję **zainstalować** przycisku. Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych. Powtórz te kroki dla **Microsoft.ML.TimeSeries v0.12.0**.

4. Dodaj następujący kod `using` instrukcji w górnej części Twojej *Program.cs* pliku:

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a>Pobieranie danych

1. Pobierz zestaw danych i zapisać go w celu *danych* wcześniej utworzony folder:

   * Kliknij prawym przyciskiem myszy [ *sales.csv produktu* ](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) i wybierz pozycję "Zapisz jako łącza (lub docelowego)..."

     Upewnij się, albo zapisać \*pliku CSV *danych* folderu lub po jego zapisaniu innym miejscu, Przenieś \*pliku CSV *danych* folderu.

2. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy \*pliku CSV, a następnie wybierz **właściwości**. W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.

Poniższa tabela jest podgląd danych z usługi \*pliku CSV:

|Miesiąc  |ProductSales |
|-------|-------------|
|1 stycznia  |    271      |
|2 stycznia  |    150.9    |
|.....  |    .....    |
|1-Feb  |    199.3    |
|.....  |    .....    |

### <a name="create-classes-and-define-paths"></a>Tworzenie klas i definiowania ścieżek

Następnie zdefiniuj strukturę danych wejściowych klasy.

Dodaj nową klasę do projektu:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj > Nowy element**.

2. W **okno dialogowe Dodaj nowy element**, wybierz opcję **klasy** i zmień **nazwa** pole *ProductSalesData.cs*. Następnie wybierz **Dodaj** przycisku.

*ProductSalesData.cs* plik zostanie otwarty w edytorze kodu. Dodaj następujący kod `using` instrukcji na górze *ProductSalesData.cs*:

```csharp
using Microsoft.ML.Data;
```

Usuń istniejącą definicję klasy i Dodaj następujący kod, który zawiera dwie klasy `ProductSalesData` i `ProductSalesPrediction`, *ProductSalesData.cs* pliku:

[!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/ProductSalesData.cs#DeclareTypes "Declare data record types")]

`ProductSalesData` Określa klasę danych wejściowych. [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) atrybut określa, które kolumny (według indeksu kolumny) w zestawie danych, które powinny być załadowane. 

Dodaj następujące dodatkowe `using` instrukcji na górze *Program.cs* pliku:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

Należy utworzyć dwa pola globalnego na potrzeby przechowywania ostatnio pobrane dataset ścieżkę pliku i ścieżka pliku zapisanego modelu:

* `_dataPath` zawiera ścieżkę do zestawu danych, używane do trenowania modelu.
* `_docsize` ma to liczba rekordów w pliku zestawu danych. Można będzie użyć do obliczenia `pvalueHistoryLength`.

Dodaj następujący kod po prawej stronie wiersza powyżej `Main` metodę, aby określić tych ścieżek:

[!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DeclareGlobalVariables "Declare global variables")]

[Klasy MLContext](xref:Microsoft.ML.MLContext) to punkt początkowy dla wszystkich operacji w strukturze ML.NET oraz inicjowanie `mlContext` tworzy nowe środowisko strukturze ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Przypomina, model `DBContext` platformy Entity Framework.

### <a name="initialize-variables-in-main"></a>Inicjowanie zmiennych w głównym oknie

Zastąp `Console.WriteLine("Hello World!")` linię `Main` metody za pomocą następującego kodu, aby zadeklarować i zainicjować `mlContext` zmiennej:

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateMLContext "Create the ML Context")]

### <a name="load-the-data"></a>Ładowanie danych

Dane w strukturze ML.NET jest reprezentowany jako [klasy IDataView](xref:Microsoft.ML.IDataView). `IDataView` jest elastyczny i wydajny sposób opisu danych tabelarycznych (liczbowe i tekstowe). Dane można załadować z pliku tekstowego lub w czasie rzeczywistym (na przykład SQL bazy danych lub dziennika plików) do `IDataView` obiektu. Dodaj następujący kod jako następnego wiersza `Main()` metody:

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#LoadData "loading dataset")]

[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczytuje w pliku. Pobiera zmienne ścieżek danych i zwraca `IDataView`.

## <a name="ml-task---time-series-anomaly-detection"></a>Zadanie ML — wykrywanie anomalii w czasie serii 

Wykrywanie anomalii flagi nieoczekiwane lub nietypowe zdarzenia lub zachowania. Ta funkcja zapewnia wskazówki gdzie szukać problemów i pomaga w odpowiedzi na pytanie "Jest to brzmienia?".

![Jest to nieco dziwne](./media/sales-anomaly-detection/anomalydetection.png)

Wykrywanie anomalii to proces wykrywania dane szeregów czasowych; punktów danego wejściowego szereg czasowy których zachowanie nie jest oczekiwanym lub "nieco dziwne".

Może to być przydatne na wiele różnych sposobów. Przykład:

Jeśli masz samochód, warto wiedzieć: Jest to przemysł miernika odczytu normalne lub masz przeciek?
Jeśli monitorujesz zużycie energii, czy chcesz wiedzieć: Występuje po awarii?

Istnieją dwa rodzaje czas serii anomalie, które mogą zostać wykryte: 

* **Wartości graniczne** wskazuje nietypowe zachowanie tymczasowe wzrosty w systemie. 

* **Punkty zmian** określenia początku trwałych zmian wraz z upływem czasu w systemie. 

W strukturze ML.NET, algorytmy wykrywania kolekcji IID lub wykrywanie punktów zmiany identyfikatora IID są przystosowane do potrzeb [niezależne i identycznie rozproszonych zestawów danych](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables). 

Będzie analizować te same dane sprzedaży produktu do wykrywania wzrostów i zmiany punktów. Proces kompilowania i szkolenie modelu jest taki sam dla kolekcji wykrywania i zmiany punktu wykrywania; Główna różnica polega na algorytm wykrywania określonych.

## <a name="spike-detection"></a>Wykrywanie kolekcji 

Jest celem wykrywania kolekcji do identyfikowania nagłe jeszcze tymczasowe wzrosty, różniące się znacznie od większość wartości danych serii czasu. Jest ważne wykryć te podejrzane elementów rzadkie, zdarzeń lub obserwacji w sposób terminowy minimalizowanie. Następujące podejście może służyć do wykrywania szereg anomalie, takich jak: awarii, ataków cybernetycznych lub zawartości WWW wirusowej. Poniższy rysunek jest przykładem skoki w zestawie danych serii czasu:

![SpikeDetection](./media/sales-anomaly-detection/SpikeDetection.png)

### <a name="create-the-detectspike-method"></a>Utwórz metodę DetectSpike()

Dodaj następujące wywołanie do `DetectSpike()`metodę jako następnego wiersza kodu w `Main()` metody:

[!code-csharp[CallDetectSpike](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectSpike)]

`DetectSpike()` Metoda wykonuje następujące zadania:

* Szkolenie modeli modelu.
* Wykrywa skoki, na podstawie historycznych danych sprzedaży.
* Wyświetla wyniki.

Tworzenie `DetectSpike()` metody tuż za `Main()` metody, używając następującego kodu:

```csharp
static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

Użyj [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) do nauczenia modelu do kolekcji wykrywania. Dodaj go do `DetectChangepoint()` metoda następującym kodem:

[!code-csharp[AddSpikeTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddSpikeTrainer)]

Dopasuj do modelu `productSales` danych i zwracają uczonego modelu przez dodanie poniższego jako następnego wiersza kodu w `DetectSpike()` metody:

[!code-csharp[TrainModel1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel1)]

[Fit()](xref:Microsoft.ML.Data.TrivialEstimator%601.Fit%2A) metoda szkolenie modeli modelu przekształcania zestawu danych i stosując szkolenia.

Dodaj następujący wiersz kodu do przekształcania `productSales` danych w następnym wierszu `DetectSpike()` metody:

[!code-csharp[TransformData1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData1)]

W poprzednim kodzie użyto [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metodę, aby tworzyć prognozy dla wielu podać wiersze danych wejściowych zestawu testów.

Konwertuj swoje `transformedData` do silnie typizowanego `IEnumerable` dla łatwiejsze wyświetlania przy użyciu [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) metoda następującym kodem:

[!code-csharp[CreateEnumerable1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable1)]

Tworzenie za pomocą następujących wiersz nagłówka wyświetlana <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:

[!code-csharp[DisplayHeader1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader1)]

Poniższe informacje będą wyświetlane w wynikach wykrywania kolekcji:

* `Alert` Wskazuje alert dotyczący punktu danych w ramach kolekcji.

* `Score` jest `ProductSales` wartość punktu danych w zestawie danych.

* `P-Value` "P" oznacza prawdopodobieństwo. Oznacza to, jakie jest prawdopodobieństwo, ten punkt danych anomalii. 

Użyj poniższego kodu, aby wykonać iterację `predictions` `IEnumerable` i wyświetlić wyniki:

[!code-csharp[DisplayResults1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults1)]

## <a name="spike-detection-results"></a>Wyniki wykrywania kolekcji

Wyniki powinny być podobne do następujących. Podczas przetwarzania, komunikaty są wyświetlane. Może zostać wyświetlony ostrzeżenia lub komunikaty przetwarzania. Te zostały usunięte z następujących wyników dla przejrzystości.

```console
Detect temporary changes in pattern
=============== Training the model ===============
=============== End of training process ===============
Alert   Score   P-Value
0       271.00  0.50
0       150.90  0.00
0       188.10  0.41
0       124.30  0.13
0       185.30  0.47
0       173.50  0.47
0       236.80  0.19
0       229.50  0.27
0       197.80  0.48
0       127.90  0.13
1       341.50  0.00 <-- Spike detected
0       190.90  0.48
0       199.30  0.48
0       154.50  0.24
0       215.10  0.42
0       278.30  0.19
0       196.40  0.43
0       292.00  0.17
0       231.00  0.45
0       308.60  0.18
0       294.90  0.19
1       426.60  0.00 <-- Spike detected
0       269.50  0.47
0       347.30  0.21
0       344.70  0.27
0       445.40  0.06
0       320.90  0.49
0       444.30  0.12
0       406.30  0.29
0       442.40  0.21
1       580.50  0.00 <-- Spike detected
0       412.60  0.45
1       687.00  0.01 <-- Spike detected
0       480.30  0.40
0       586.30  0.20
0       651.90  0.14
```

## <a name="change-point-detection"></a>Zmiana punktu wykrywania

`Change points` trwałych zmian w czas serii zdarzeń strumienia rozłożenia wartości, takich jak zmiany poziomu i trendów. Te zmiany trwały ostatnie znacznie dłużej niż `spikes` i wskazywać, że zdarzenia krytycznego. `Change points` nie są zwykle widoczne gołym okiem, ale może zostać wykryte w Twoich danych przy użyciu metod, takich jak następującą metodę.  Poniższa ilustracja jest przykładem wykrywania punktu zmian:

![ChangePointDetection](./media/sales-anomaly-detection/ChangePointDetection.png)

### <a name="create-the-detectchangepoint-method"></a>Utwórz metodę DetectChangepoint()

Dodaj następujące wywołanie do `DetectChangepoint()`metodę jako następnego wiersza kodu w `Main()` metody:

[!code-csharp[CallDetectChangepoint](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectChangepoint)]

`DetectChangepoint()` Metoda wykonuje następujące zadania:

* Szkolenie modeli modelu.
* Wykrywa, punktów zmiany na podstawie historycznych danych sprzedaży.
* Wyświetla wyniki.

Tworzenie `DetectChangepoint()` metody tuż za `Main()` metody, używając następującego kodu:

```csharp
static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

[IidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) służy do nauczenia modelu dla zmiany punktu wykrywania. Dodaj go do `DetectChangepoint()` metoda następującym kodem:

[!code-csharp[AddChangepointTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddChangepointTrainer)]

Jak poprzednio, dopasowania modelu do `productSales` danych i zwracają uczonego modelu przez dodanie poniższego jako następnego wiersza kodu w `DetectChangePoint()` metody:

[!code-csharp[TrainModel2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel2)]

Użyj `Transform()` metodę, aby przekształcić `Training` danych przez dodanie poniższego kodu `DetectChangePoint()`:

[!code-csharp[TransformData2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData2)]

Tak jak wcześniej, należy przekonwertować swoje `transformedData` do silnie typizowanego `IEnumerable` dla łatwiejsze wyświetlania przy użyciu `CreateEnumerable()`metoda następującym kodem:

[!code-csharp[CreateEnumerable2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable2)]

Utwórz nagłówek wyświetlania następującym kodem w następnym wierszu `DetectChangePoint()` metody:

[!code-csharp[DisplayHeader2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader2)]

Poniższe informacje będą wyświetlane w wynikach wykrywania punktu zmiany:

* `Alert` Wskazuje alert punktu zmiany punktu danych.
* `Score` jest `ProductSales` wartość punktu danych w zestawie danych.
* `P-Value` "P" oznacza prawdopodobieństwo. Oznacza to, jakie jest prawdopodobieństwo, ten punkt danych anomalii. 
* `Martingale value` jest używany do identyfikowania, jak jest "brzmienia" punkt danych, na podstawie sekwencji wartości P.  

Iteracyjne przeglądanie `predictions` `IEnumerable` i wyświetlić wyniki w następującym kodem:

[!code-csharp[DisplayResults2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults2)]

## <a name="change-point-detection-results"></a>Zmiana punktu wykrywania wyników

Wyniki powinny być podobne do następujących. Podczas przetwarzania, komunikaty są wyświetlane. Może zostać wyświetlony ostrzeżenia lub komunikaty przetwarzania. Te zostały usunięte z następujących wyników dla przejrzystości.

```console
Detect Persistent changes in pattern
=============== Training the model Using Change Point Detection Algorithm===============
=============== End of training process ===============
Alert   Score   P-Value Martingale value
0       271.00  0.50    0.00
0       150.90  0.00    2.33
0       188.10  0.41    2.80
0       124.30  0.13    9.16
0       185.30  0.47    9.77
0       173.50  0.47    10.41
0       236.80  0.19    24.46
0       229.50  0.27    42.38
1       197.80  0.48    44.23 <-- alert is on, predicted changepoint
0       127.90  0.13    145.25
0       341.50  0.00    0.01
0       190.90  0.48    0.01
0       199.30  0.48    0.00
0       154.50  0.24    0.00
0       215.10  0.42    0.00
0       278.30  0.19    0.00
0       196.40  0.43    0.00
0       292.00  0.17    0.01
0       231.00  0.45    0.00
0       308.60  0.18    0.00
0       294.90  0.19    0.00
0       426.60  0.00    0.00
0       269.50  0.47    0.00
0       347.30  0.21    0.00
0       344.70  0.27    0.00
0       445.40  0.06    0.02
0       320.90  0.49    0.01
0       444.30  0.12    0.02
0       406.30  0.29    0.01
0       442.40  0.21    0.01
0       580.50  0.00    0.01
0       412.60  0.45    0.01
0       687.00  0.01    0.12
0       480.30  0.40    0.08
0       586.30  0.20    0.03
0       651.90  0.14    0.09
```

Gratulacje! Teraz zostały pomyślnie skompilowane modeli uczenia maszynowego do wykrywania wzrostów i zmienić punkt anomalii w danych sprzedaży.

Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repozytorium.

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Ładowanie danych
> * Uczenie modelu do kolekcji wykrywania anomalii
> * Wykrywaj anomalie kolekcji za pomocą uczonego modelu
> * Uczenie modelu dla zmiany punktu anomalii
> * Wykrywaj anomalie punktu zmiany w trybie uczonego

## <a name="next-steps"></a>Następne kroki

Zapoznaj się z repozytorium GitHub samples usługi Machine Learning można eksplorować przykładową wykrywania anomalii zużycia energii.
> [!div class="nextstepaction"]
> [repozytorium GitHub machinelearning-DotNet-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/TimeSeries_PowerAnomalyDetection)