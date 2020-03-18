---
title: 'Samouczek: Wykrywanie anomalii w sprzedaży produktów'
description: Dowiedz się, jak utworzyć aplikację do wykrywania anomalii dla danych sprzedaży produktów. W tym samouczku utworzy aplikację konsoli .NET Core przy użyciu języka C# w programie Visual Studio 2019.
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: c3fd4aa715a64a20f1eff9b789f6a87eaa749163
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78239992"
---
# <a name="tutorial-detect-anomalies-in-product-sales-with-mlnet"></a>Samouczek: Wykrywanie anomalii w sprzedaży produktów za pomocą ML.NET

Dowiedz się, jak utworzyć aplikację do wykrywania anomalii dla danych sprzedaży produktów. Ten samouczek tworzy aplikację konsoli .NET Core przy użyciu języka C# w programie Visual Studio.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> * Ładowanie danych
> * Tworzenie transformacji w celu wykrywania anomalii kolec
> * Wykrywanie anomalii skokowych przy transformacji
> * Tworzenie transformacji w celu wykrywania anomalii punktu zmian
> * Wykrywanie anomalii punktu zmiany przy transformacji

Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection)

## <a name="prerequisites"></a>Wymagania wstępne

* [Visual Studio 2017 w wersji 15.6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym obciążeniem ".NET Core programistorna wieloplatformowa".

* [Zestaw danych product-sales.csv](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> Format danych `product-sales.csv` w opiera się na zbiorze danych "Szampon sprzedaży w okresie trzech lat" pierwotnie pochodzą z DataMarket i dostarczone przez Time Series Data Library (TSDL), stworzony przez Rob Hyndman.
> "Szampon sprzedaży w okresie trzech lat" Dataset licencjonowane w ramach DataMarket Domyślna Otwarta Licencja.

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. Utwórz **aplikację .NET Core Console o** nazwie "ProductSalesAnomalyDetection".

2. Utwórz katalog o nazwie *Dane* w projekcie, aby zapisać pliki zestawu danych.

3. Zainstaluj **pakiet Microsoft.ML NuGet:**

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **polecenie Zarządzaj pakietami NuGet**. Wybierz "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj **Microsoft.ML** i wybierz przycisk **Zainstaluj.** Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z warunkami licencyjnymi dla wymienionych pakietów. Powtórz te kroki dla **programu Microsoft.ML.TimeSeries**.

4. Dodaj następujące `using` instrukcje u góry pliku *Program.cs:*

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a>Pobieranie danych

1. Pobierz zestaw danych i zapisz go w folderze *Data,* który został wcześniej utworzony:

   * Kliknij prawym przyciskiem myszy [*na product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) i wybierz "Zapisz link (lub target) Jako ..."

     Upewnij się, że \*plik csv jest zapisywany w folderze \* *Dane* lub po zapisaniu go w innym miejscu, przenieś plik csv do folderu *Dane.*

2. W Eksploratorze \*rozwiązań kliknij prawym przyciskiem myszy plik csv i wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**zmień wartość **kopiuj do katalogu wyjściowego,** aby **skopiować, jeśli nowsza**.

Poniższa tabela jest podglądem \*danych z pliku csv:

|Month  |Sprzedaż produktu |
|-------|-------------|
|1-sty  |    271      |
|2 stycznia  |    150.9    |
|.....  |    .....    |
|1-lut  |    199.3    |
|.....  |    .....    |

### <a name="create-classes-and-define-paths"></a>Tworzenie klas i definiowanie ścieżek

Następnie zdefiniuj struktury danych klas wejściowych i przewidywania.

Dodaj nową klasę do projektu:

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj > nowy element**.

2. W **oknie dialogowym Dodawanie nowego elementu**wybierz pozycję **Klasa** i zmień pole **Nazwa** na *ProductSalesData.cs*. Następnie wybierz przycisk **Dodaj.**

   Plik *ProductSalesData.cs* zostanie otwarty w edytorze kodu.

3. Dodaj następującą `using` instrukcję do górnej części *ProductSalesData.cs:*

   ```csharp
   using Microsoft.ML.Data;
   ```

4. Usuń istniejącą definicję klasy i dodaj następujący `ProductSalesData` `ProductSalesPrediction`kod, który ma dwie klasy i , do *pliku ProductSalesData.cs:*

    [!code-csharp[DeclareTypes](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/ProductSalesData.cs#DeclareTypes "Declare data record types")]

    `ProductSalesData`określa klasę danych wejściowych. [Atrybut LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) określa, które kolumny (według indeksu kolumn) w zestawie danych powinny być ładowane.

    `ProductSalesPrediction`określa klasę danych przewidywania. W przypadku wykrywania anomalii przewidywanie składa się z alertu, aby wskazać, czy istnieje anomalia, wynik surowy i p-wartość. Im bliżej wartość p jest 0, tym bardziej prawdopodobne anomalii wystąpił.

5. Utwórz dwa pola globalne, aby pomieścić ostatnio pobraną ścieżkę pliku zestawu danych i zapisaną ścieżkę pliku modelu:

    * `_dataPath`ma ścieżkę do zestawu danych używanego do nauczenia modelu.
    * `_docsize`ma liczbę rekordów w pliku zestawu danych. Użyjesz `_docSize` do `pvalueHistoryLength`obliczenia .

6. Dodaj następujący kod do wiersza `Main` tuż nad metodą, aby określić te ścieżki:

    [!code-csharp[Declare global variables](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

### <a name="initialize-variables-in-main"></a>Inicjowanie zmiennych w main

1. Zamień `Console.WriteLine("Hello World!")` wiersz `Main` w metodzie na następujący kod, `mlContext` aby zadeklarować i zainicjować zmienną:

    [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CreateMLContext "Create the ML Context")]

    [Klasa MLContext](xref:Microsoft.ML.MLContext) jest punktem wyjścia dla wszystkich operacji `mlContext` ML.NET, a inicjowanie tworzy nowe środowisko ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest to podobne, koncepcyjnie, `DBContext` do w ramach jednostki.

### <a name="load-the-data"></a>Ładowanie danych

Dane w ML.NET jest reprezentowana jako [klasa IDataView](xref:Microsoft.ML.IDataView). `IDataView`to elastyczny i skuteczny sposób opisywania danych tabelarycznych (numerycznych i tekstowych). Dane mogą być ładowane z pliku tekstowego lub z innych źródeł `IDataView` (na przykład bazy danych SQL lub plików dziennika) do obiektu.

1. Dodaj następujący kod jako następny `Main()` wiersz metody:

    [!code-csharp[LoadData](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#LoadData "loading dataset")]

    [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczyty w pliku. Przyjmuje zmienne ścieżki danych i `IDataView`zwraca .

## <a name="time-series-anomaly-detection"></a>Wykrywanie anomalii szeregów czasowych

Wykrywanie anomalii flagi nieoczekiwane lub nietypowe zdarzenia lub zachowania. Daje wskazówki, gdzie szukać problemów i pomaga odpowiedzieć na pytanie "Czy to dziwne?".

![Przykład wykrywania anomalii "Czy to dziwne".](./media/sales-anomaly-detection/time-series-anomaly-detection.png)

Wykrywanie anomalii to proces wykrywania wartości odstających danych szeregów czasowych; punktów w danej serii czasu wprowadzania, gdzie zachowanie nie jest to, czego oczekiwano, lub "dziwne".

Wykrywanie anomalii może być przydatne na wiele sposobów. Przykład:

Jeśli masz samochód, możesz wiedzieć: Czy ten wskaźnik oleju jest normalny, czy też mam wyciek?
Jeśli monitorujesz zużycie energii, chcesz wiedzieć: Czy jest awaria?

Istnieją dwa typy anomalii szeregów czasowych, które można wykryć:

* **Kolce** wskazują tymczasowe wybuchy nietypowezachowanie w systemie.

* **Punkty zmian** wskazują początek trwałych zmian w czasie w systemie.

W ML.NET algorytmy wykrywania iid spike detection lub IID Change point detections nadają się do [niezależnych i identycznie rozproszonych zestawów danych.](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables)

W przeciwieństwie do modeli w innych samouczkach, detektor anomalii szeregów czasowych przekształca się bezpośrednio na danych wejściowych. Metoda `IEstimator.Fit()` nie wymaga danych szkoleniowych do produkcji transformacji. Jednak musi schemat danych, który jest dostarczany przez widok danych wygenerowany `ProductSalesData`z pustej listy .

Będziesz analizować te same dane dotyczące sprzedaży produktów, aby wykryć skoki i punkty zmian. Proces budowania i modelu szkolenia jest taki sam dla wykrywania kolców i wykrywania punktów zmiany; główną różnicą jest stosowany specyficzny algorytm wykrywania.

## <a name="spike-detection"></a>Wykrywanie kolec

Celem wykrywania skoków jest zidentyfikowanie nagłych, ale tymczasowych serii, które znacznie różnią się od większości wartości danych szeregów czasowych. Ważne jest, aby wykryć te podejrzane rzadkie elementy, zdarzenia lub obserwacje w odpowiednim czasie, aby zminimalizować. Następujące podejście może służyć do wykrywania różnych anomalii, takich jak: awarie, cyberataki lub wirusowe treści internetowe. Poniższy obraz jest przykładem skoków w zestawie danych szeregów czasowych:

![Zrzut ekranu przedstawiający dwa wykryć kolce.](./media/sales-anomaly-detection/two-spike-detections.png)

### <a name="add-the-createemptydataview-method"></a>Dodawanie metody CreateEmptyDataView()

Dodaj następującą `Program.cs`metodę do:

[!code-csharp[CreateEmptyDataView](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CreateEmptyDataView)]

Tworzy `CreateEmptyDataView()` obiekt pustego widoku danych z poprawnym schematem, `IEstimator.Fit()` który ma być używany jako dane wejściowe do metody.

### <a name="create-the-detectspike-method"></a>Tworzenie metody DetectSpike()

Metoda: `DetectSpike()`

* Tworzy transformację z estymatora.
* Wykrywa skoki na podstawie historycznych danych sprzedaży.
* Wyświetla wyniki.

1. Utwórz `DetectSpike()` metodę, tuż `Main()` po tej metodzie, używając następującego kodu:

    ```csharp
    static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. Użyj [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) do szkolenia modelu do wykrywania kolców. Dodaj go `DetectSpike()` do metody z następującym kodem:

    [!code-csharp[AddSpikeTrainer](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#AddSpikeTrainer)]

1. Utwórz transformację wykrywania skoku, dodając następujący `DetectSpike()` wiersz kodu w metodzie:

    [!code-csharp[TrainModel1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#TrainModel1)]

1. Dodaj następujący wiersz kodu, `productSales` aby przekształcić dane jako `DetectSpike()` następny wiersz w metodzie:

    [!code-csharp[TransformData1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#TransformData1)]

    Poprzedni kod używa [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda do prognozowania dla wielu wierszy wejściowych zestawu danych.

1. Konwertuj swoje `transformedData` `IEnumerable` na silnie typizowany dla łatwiejszego wyświetlania przy użyciu [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) metody z następującym kodem:

    [!code-csharp[CreateEnumerable1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CreateEnumerable1)]

1. Utwórz wyświetloną linię <xref:System.Console.WriteLine?displayProperty=nameWithType> nagłówka przy użyciu następującego kodu:

    [!code-csharp[DisplayHeader1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DisplayHeader1)]

    Wyniki wykrywania skoków zostaną wyświetlone następujące informacje:

    * `Alert`wskazuje alert skokowy dla danego punktu danych.
    * `Score`jest `ProductSales` wartością dla danego punktu danych w zestawie danych.
    * `P-Value`"P" oznacza prawdopodobieństwo. Im bliżej wartość p jest 0, tym bardziej prawdopodobne, punkt danych jest anomalia.

1. Użyj następującego kodu, aby `predictions` `IEnumerable` iterować i wyświetlać wyniki:

    [!code-csharp[DisplayResults1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DisplayResults1)]

1. Dodaj wywołanie `DetectSpike()`do metody `Main()` w metodzie:

    [!code-csharp[CallDetectSpike](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CallDetectSpike)]

## <a name="spike-detection-results"></a>Wyniki wykrywania kolców

Wyniki powinny być podobne do poniższych. Podczas przetwarzania są wyświetlane komunikaty. Mogą być wyświetlane ostrzeżenia lub wiadomości przetwarzania. Niektóre komunikaty zostały usunięte z następujących wyników dla jasności.

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

`Change points`są trwałe zmiany w strumieniu zdarzeń szeregów czasowych dystrybucji wartości, takich jak zmiany poziomu i trendy. Te trwałe zmiany trwają `spikes` znacznie dłużej niż i mogą wskazywać na katastrofalne zdarzenia. `Change points`zazwyczaj nie są widoczne gołym okiem, ale mogą być wykryte w danych za pomocą metod, takich jak w poniższej metodzie.  Poniższy obraz jest przykładem wykrywania punktu zmiany:

![Zrzut ekranu przedstawiający wykrywanie punktu zmiany.](./media/sales-anomaly-detection/change-point-detection.png)

### <a name="create-the-detectchangepoint-method"></a>Tworzenie metody DetectChangepoint()

Metoda `DetectChangepoint()` wykonuje następujące zadania:

* Tworzy transformację z estymatora.
* Wykrywa punkty zmian na podstawie historycznych danych sprzedaży.
* Wyświetla wyniki.

1. Utwórz `DetectChangepoint()` metodę, tuż `Main()` po tej metodzie, używając następującego kodu:

    ```csharp
    static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. Utwórz [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) `DetectChangepoint()` w metodzie z następującym kodem:

    [!code-csharp[AddChangepointTrainer](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#AddChangepointTrainer)]

1. Podobnie jak poprzednio, utwórz transformację z estymatora, dodając następujący wiersz kodu w metodzie: `DetectChangePoint()`

    [!code-csharp[TrainModel2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#TrainModel2)]

1. Użyj `Transform()` metody, aby przekształcić dane, dodając `DetectChangePoint()`następujący kod do:

    [!code-csharp[TransformData2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#TransformData2)]

1. Podobnie jak poprzednio, `transformedData` przekonwertuj swoje na silnie typizowany `IEnumerable` dla łatwiejszego `CreateEnumerable()`wyświetlania przy użyciu metody z następującym kodem:

    [!code-csharp[CreateEnumerable2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CreateEnumerable2)]

1. Utwórz nagłówek wyświetlania z następującym kodem jako następny wiersz w metodzie: `DetectChangePoint()`

    [!code-csharp[DisplayHeader2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DisplayHeader2)]

    W wynikach wykrywania punktów zmian zostaną wyświetlone następujące informacje:

    * `Alert`wskazuje alert punktu zmiany dla danego punktu danych.
    * `Score`jest `ProductSales` wartością dla danego punktu danych w zestawie danych.
    * `P-Value`"P" oznacza prawdopodobieństwo. Im bliżej Wartość P jest do 0, tym bardziej prawdopodobne, punkt danych jest anomalia.
    * `Martingale value`służy do identyfikowania, jak "dziwny" jest punkt danych, na podstawie sekwencji wartości P.

1. Iteruj `predictions` `IEnumerable` i wyświetlaj wyniki za pomocą następującego kodu:

    [!code-csharp[DisplayResults2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DisplayResults2)]

1. Dodaj następujące wywołanie `DetectChangepoint()`do `Main()` metody w metodzie:

    [!code-csharp[CallDetectChangepoint](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CallDetectChangepoint)]

## <a name="change-point-detection-results"></a>Zmiana wyników wykrywania punktów

Wyniki powinny być podobne do poniższych. Podczas przetwarzania są wyświetlane komunikaty. Mogą być wyświetlane ostrzeżenia lub wiadomości przetwarzania. Niektóre wiadomości zostały usunięte z następujących wyników dla jasności.

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

Gratulacje! Teraz pomyślnie skonstruowano modele uczenia maszynowego do wykrywania skoków i anomalii punktowych zmian w danych sprzedaży.

Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection)

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> * Ładowanie danych
> * Szkolenie modelu wykrywania anomalii kolec
> * Wykrywanie anomalii kolec z uczonego modelu
> * Szkolenie modelu wykrywania anomalii punktu zmiany
> * Wykrywanie anomalii punktu zmiany w trybie szkoleniowym

## <a name="next-steps"></a>Następne kroki

Zapoznaj się z przykładów uczenia maszynowego repozytorium GitHub do eksplorowania powody wykrywania anomalii zużycia energii.
> [!div class="nextstepaction"]
> [dotnet/machinelearning-samples Repozytorium GitHub](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)
