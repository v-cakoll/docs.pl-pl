---
title: 'Samouczek: Wykrywaj anomalie w sprzedaży produktu'
description: Dowiedz się, jak utworzyć aplikację wykrywania anomalii dla danych sprzedaży produktu. W tym samouczku przedstawiono tworzenie aplikacji konsolowej C# platformy .NET Core przy użyciu programu Visual Studio 2019.
ms.date: 07/17/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: e87034733b048153202bc11ab94ed7605749f60c
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331691"
---
# <a name="tutorial-detect-anomalies-in-product-sales-with-mlnet"></a>Samouczek: Wykrywaj anomalie w sprzedaży produktów za pomocą ML.NET

Dowiedz się, jak utworzyć aplikację wykrywania anomalii dla danych sprzedaży produktu. W tym samouczku przedstawiono tworzenie aplikacji konsolowej C# platformy .NET Core przy użyciu programu Visual Studio.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Ładowanie danych
> * Uczenie modelu umożliwiającego przeprowadzenie wykrywania anomalii
> * Wykrywaj anomalie wzrostu przy użyciu przeszkolonego modelu
> * Uczenie modelu wykrywania anomalii punktu zmiany
> * Wykrywaj anomalie punktu zmiany przy użyciu przeszkolonego modelu

Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) .

## <a name="prerequisites"></a>Wymagania wstępne

* [Program Visual Studio 2017 15,6 lub nowszy](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core.

* [Zestaw danych Product-Sales. csv](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> Format danych w programie `product-sales.csv` jest oparty na zestawie danych "szampon Sales w okresie trzech lat", pierwotnie pochodzący od DataMarket i udostępnianych przez bibliotekę danych szeregów czasowych (TSDL) utworzonych przez Roba Hyndman. "Szampon Sales w okresie trzech lat", który jest licencjonowany w ramach domyślnej licencji Open w ramach programu DataMarket.

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. Utwórz **aplikację konsolową .NET Core** o nazwie "ProductSalesAnomalyDetection".

2. Utwórz katalog o nazwie *dane* w projekcie, aby zapisać pliki zestawu danych.

3. Zainstaluj **pakiet NuGet Microsoft.ml**:

    W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, Wyszukaj pozycję **Microsoft.ml**, wybierz pakiet **v 1.0.0** na liście, a następnie wybierz przycisk **Instaluj** . Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów. Powtórz te kroki dla **Microsoft. ml. szeregów czasowych v 0.12.0**.

4. Dodaj następujące `using` instrukcje w górnej części pliku *program.cs* :

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a>Pobieranie danych

1. Pobierz zestaw danych i Zapisz go w utworzonym wcześniej folderze *danych* :

   * Kliknij prawym przyciskiem myszy plik [*Product-Sales. csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) i wybierz pozycję "Zapisz link (lub cel) jako..."

     Upewnij się, że plik CSV \*został zapisany w folderze *dane* lub po jego zapisaniu w \*innym miejscu Przenieś plik CSV do folderu *dane* .

2. W Eksplorator rozwiązań kliknij prawym przyciskiem \*myszy plik CSV i wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.

Poniższa tabela zawiera podgląd danych z \*pliku CSV:

|Bieżącym  |ProductSales |
|-------|-------------|
|1 stycznia  |    271      |
|2-sty  |    150,9    |
|.....  |    .....    |
|1 — Luty  |    199,3    |
|.....  |    .....    |

### <a name="create-classes-and-define-paths"></a>Tworzenie klas i Definiowanie ścieżek

Następnie zdefiniuj swoją strukturę danych klasy wejściowej.

Dodaj nową klasę do projektu:

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz pozycję **Dodaj > nowy element**.

2. W **oknie dialogowym Dodaj nowy element**wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *ProductSalesData.cs*. Następnie wybierz przycisk **Dodaj** .

Plik *ProductSalesData.cs* zostanie otwarty w edytorze kodu. Dodaj następującą `using` instrukcję na początku *ProductSalesData.cs*:

```csharp
using Microsoft.ML.Data;
```

Usuń istniejącą definicję klasy i Dodaj następujący kod, który ma dwie klasy `ProductSalesData` i `ProductSalesPrediction`, do pliku *ProductSalesData.cs* :

[!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/ProductSalesData.cs#DeclareTypes "Declare data record types")]

`ProductSalesData`Określa klasę danych wejściowych. Atrybut [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) określa, które kolumny (według indeksu kolumn) w zestawie danych powinny zostać załadowane. 

Dodaj następujące dodatkowe `using` instrukcje na początku pliku *program.cs* :

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

Należy utworzyć dwa pola globalne do przechowywania ostatnio pobranej ścieżki pliku zestawu danych i zapisanej ścieżki pliku modelu:

* `_dataPath`ma ścieżkę do zestawu danych używanego do uczenia modelu.
* `_docsize`zawiera liczbę rekordów w pliku DataSet. Ta funkcja zostanie użyta do `pvalueHistoryLength`obliczenia.

Dodaj następujący kod do wiersza bezpośrednio powyżej metody, `Main` aby określić te ścieżki:

[!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DeclareGlobalVariables "Declare global variables")]

[Klasa MLContext](xref:Microsoft.ML.MLContext) jest punktem początkowym dla wszystkich operacji ml.NET, a inicjowanie `mlContext` tworzy nowe środowisko ml.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest to podobne, pojęciowo do `DBContext` w Entity Framework.

### <a name="initialize-variables-in-main"></a>Inicjuj zmienne w głównym

Zastąp `Main` `mlContext` wiersz w metodzie poniższym kodem, aby zadeklarować i zainicjować zmienną: `Console.WriteLine("Hello World!")`

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateMLContext "Create the ML Context")]

### <a name="load-the-data"></a>Ładowanie danych

Dane w ML.NET są reprezentowane jako [Klasa IDataView](xref:Microsoft.ML.IDataView). `IDataView`to elastyczny i wydajny sposób opisywania danych tabelarycznych (liczbowych i tekstowych). Dane można ładować z pliku tekstowego lub w czasie rzeczywistym (na przykład bazy danych SQL lub plików dziennika) do `IDataView` obiektu. Dodaj następujący kod w następnym wierszu `Main()` metody:

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#LoadData "loading dataset")]

[LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczytuje w pliku. Przyjmuje zmienne ścieżki danych i zwraca `IDataView`.

## <a name="ml-task---time-series-anomaly-detection"></a>"ML" — wykrywanie anomalii szeregów czasowych 

Wykrywanie anomalii flagi nieoczekiwane lub nietypowe zdarzenia lub zachowania. Zawiera wskazówki, gdzie szukać problemów i pomaga odpowiedzieć na pytanie "czy to brzmienia?".

![Czy ten brzmienia](./media/sales-anomaly-detection/anomalydetection.png)

Wykrywanie anomalii to proces wykrywania wartości odstających danych szeregów czasowych; wskazuje na dane wejściowe serie czasowe, w których zachowanie nie jest oczekiwane, lub "brzmienia".

Może to być przydatne na wiele sposobów. Przykład:

Jeśli masz samochód, warto wiedzieć: Czy ten miernik oleju jest odczytywany w normalnym lub czy mam wyciek?
Jeśli monitorujesz zużycie mocy, warto wiedzieć: Czy wystąpił przestój?

Istnieją dwa typy anomalii szeregów czasowych, które mogą zostać wykryte: 

* **Skoki** wskazują tymczasowe rozerwania nietypowego zachowania w systemie. 

* **Punkty zmian** wskazują początek trwałych zmian w czasie w systemie. 

W programie ML.NET algorytmy wykrywania i wykrywania punktu zmiany identyfikatora IID są odpowiednie dla niezależnych [i identycznie rozproszonych zestawów danych](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables). 

Przeanalizujesz te same dane sprzedaży produktu w celu wykrywania skoków i punktów zmian. Proces kompilowania i uczenia jest taki sam, jak w celu uzyskania wykrywalności i wykrywania punktów zmiany; Główną różnicą jest używany algorytm wykrywania.

## <a name="spike-detection"></a>Wykrywanie 

Celem w zakresie wykrywania jest zidentyfikowanie nagłych obciążeń tymczasowych, które znacząco różnią się od większości wartości danych szeregów czasowych. Ważne jest, aby wykrywać te podejrzane rzadkie elementy, zdarzenia lub obserwacje w odpowiednim czasie, aby być zminimalizowane. Poniższe podejście może służyć do wykrywania różnych anomalii, takich jak: awaria, ataki cybernetycznymi lub wirusowej zawartości sieci Web. Na poniższej ilustracji przedstawiono przykład skoków w zestawie danych szeregów czasowych:

![SpikeDetection](./media/sales-anomaly-detection/SpikeDetection.png)

### <a name="create-the-detectspike-method"></a>Tworzenie metody DetectSpike ()

Dodaj następujące wywołanie do `DetectSpike()`metody jako następny wiersz kodu `Main()` w metodzie:

[!code-csharp[CallDetectSpike](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectSpike)]

`DetectSpike()` Metoda wykonuje następujące zadania:

* Pociąga za siebie model.
* Wykrywa skoki na podstawie historycznych danych sprzedaży.
* Wyświetla wyniki.

Utwórz metodę, tuż po metodzie, przy użyciu następującego kodu: `Main()` `DetectSpike()`

```csharp
static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

Użyj [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) , aby nauczyć model na potrzeby wykrywania. Dodaj go do `DetectSpike()` metody przy użyciu następującego kodu:

[!code-csharp[AddSpikeTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddSpikeTrainer)]

Dopasuj model do `productSales` danych, dodając następujący kod jako następny wiersz kodu `DetectSpike()` w metodzie:

[!code-csharp[TrainModel1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel1)]

Metoda [dopasowywania ()](xref:Microsoft.ML.Data.TrivialEstimator%601.Fit%2A) pociąga za siebie model poprzez transformowanie zestawu danych i zastosowanie szkolenia.

Dodaj następujący wiersz kodu, aby przekształcić `productSales` dane jako następny wiersz `DetectSpike()` w metodzie:

[!code-csharp[TransformData1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData1)]

Poprzedni kod używa metody [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) do przeprowadzania prognoz dla wielu podanych danych wejściowych dla testu zestawu danych.

Konwertuj na silnie wpisaną `IEnumerable` wartość, aby ułatwić wyświetlanie przy użyciu metody "xmlliczaln [()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) " z następującym kodem: `transformedData`

[!code-csharp[CreateEnumerable1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable1)]

Utwórz wiersz nagłówka wyświetlanego przy użyciu następującego <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:

[!code-csharp[DisplayHeader1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader1)]

Następujące informacje zostaną wyświetlone w wynikach wykrywania:

* `Alert`wskazuje alert dla danego punktu danych.

* `Score``ProductSales` jest wartością dla danego punktu danych w zestawie danych.

* `P-Value`"P" oznacza prawdopodobieństwo. Wskazuje to, jak najprawdopodobniej ten punkt danych jest anomalią. 

Użyj poniższego kodu, aby wykonać iterację `predictions` `IEnumerable` i wyświetlić wyniki:

[!code-csharp[DisplayResults1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults1)]

## <a name="spike-detection-results"></a>Skoki wyników wykrywania

Wyniki powinny wyglądać podobnie do poniższego. Podczas przetwarzania wyświetlane są komunikaty. Mogą pojawić się ostrzeżenia lub przetwarzanie komunikatów. Zostały one usunięte z następujących wyników dla przejrzystości.

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

## <a name="change-point-detection"></a>Wykrywanie punktu zmiany

`Change points`są trwałymi zmianami w czasie dystrybucji strumienia zdarzeń szeregów czasowych, takich jak zmiany poziomów i trendy. Te trwałe zmiany są ostatnie znacznie dłużej `spikes` niż i mogą wskazywać na katastrofalne zdarzenia. `Change points`nie są zwykle widoczne dla gołym okiem, ale mogą być wykrywane w danych przy użyciu podejścia, takiego jak w poniższej metodzie.  Na poniższej ilustracji przedstawiono przykład wykrywania punktu zmiany:

![ChangePointDetection](./media/sales-anomaly-detection/ChangePointDetection.png)

### <a name="create-the-detectchangepoint-method"></a>Tworzenie metody DetectChangepoint ()

Dodaj następujące wywołanie do `DetectChangepoint()`metody jako następny wiersz kodu `Main()` w metodzie:

[!code-csharp[CallDetectChangepoint](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectChangepoint)]

`DetectChangepoint()` Metoda wykonuje następujące zadania:

* Pociąga za siebie model.
* Wykrywa punkty zmian w oparciu o dane dotyczące sprzedaży historycznej.
* Wyświetla wyniki.

Utwórz metodę, tuż po metodzie, przy użyciu następującego kodu: `Main()` `DetectChangepoint()`

```csharp
static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

[IidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) jest używany do uczenia modelu wykrywania punktu zmiany. Dodaj go do `DetectChangepoint()` metody przy użyciu następującego kodu:

[!code-csharp[AddChangepointTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddChangepointTrainer)]

Tak jak wcześniej, Dopasuj model do `productSales` danych, dodając następujący kod jako następny wiersz kodu `DetectChangePoint()` w metodzie:

[!code-csharp[TrainModel2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel2)]

Użyj metody do `Training` przekształcenia danych, dodając następujący kod do `DetectChangePoint()`: `Transform()`

[!code-csharp[TransformData2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData2)]

Tak jak wcześniej, przekonwertuj `transformedData` na silnie wpisaną `IEnumerable` wartość, `CreateEnumerable()`aby ułatwić wyświetlanie przy użyciu metody z następującym kodem:

[!code-csharp[CreateEnumerable2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable2)]

Utwórz nagłówek wyświetlania z następującym kodem jako następnym wierszem w `DetectChangePoint()` metodzie:

[!code-csharp[DisplayHeader2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader2)]

W wynikach wykrywania punktu zmiany zostaną wyświetlone następujące informacje:

* `Alert`wskazuje alert punktu zmiany dla danego punktu danych.
* `Score``ProductSales` jest wartością dla danego punktu danych w zestawie danych.
* `P-Value`"P" oznacza prawdopodobieństwo. Wskazuje to, jak najprawdopodobniej ten punkt danych jest anomalią. 
* `Martingale value`służy do identyfikowania, jak "brzmienia" punkt danych jest oparty na sekwencji wartości P.  

Wykonaj iterację i Wyświetl wyniki przy użyciu następującego kodu: `IEnumerable` `predictions`

[!code-csharp[DisplayResults2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults2)]

## <a name="change-point-detection-results"></a>Wyniki wykrywania punktu zmiany

Wyniki powinny wyglądać podobnie do poniższego. Podczas przetwarzania wyświetlane są komunikaty. Mogą pojawić się ostrzeżenia lub przetwarzanie komunikatów. Zostały one usunięte z następujących wyników dla przejrzystości.

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

Gratulacje! Pomyślnie skompilowano modele uczenia maszynowego na potrzeby wykrywania skoków i różnic punktów zmian w danych sprzedaży.

Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) .

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Ładowanie danych
> * Uczenie modelu umożliwiającego przeprowadzenie wykrywania anomalii
> * Wykrywaj anomalie wzrostu przy użyciu przeszkolonego modelu
> * Uczenie modelu wykrywania anomalii punktu zmiany
> * Wykryj anomalie punktu zmiany w trybie przeszkolonym

## <a name="next-steps"></a>Następne kroki

Zapoznaj się z repozytorium Machine Learning przykłady w witrynie GitHub, aby poznać przykład wykrywania anomalii dotyczącego zużycia mocy.
> [!div class="nextstepaction"]
> [dotnet/machinelearning — przykłady repozytorium GitHub](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)
