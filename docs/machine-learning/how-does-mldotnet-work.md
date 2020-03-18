---
title: Co to jest ML.NET i jak to działa?
description: ML.NET umożliwia dodawanie uczenia maszynowego do aplikacji .NET w scenariuszach online lub offline. Dzięki tej funkcji można tworzyć automatyczne prognozy przy użyciu danych dostępnych dla aplikacji bez konieczności łączenia się z siecią w celu korzystania z ML.NET. W tym artykule wyjaśniono podstawy uczenia maszynowego w ML.NET.
ms.date: 11/5/2019
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: 169250adf81992ad0025e78eb9c8f151107bcf40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185858"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a>Co to jest ML.NET i jak to działa?

ML.NET umożliwia dodawanie uczenia maszynowego do aplikacji .NET w scenariuszach online lub offline. Dzięki tej funkcji można tworzyć automatyczne prognozy przy użyciu danych dostępnych dla aplikacji. Aplikacje uczenia maszynowego korzystać z wzorców w danych do prognozowania, a nie muszą być jawnie zaprogramowane.

Centralnym elementem ML.NET jest **model**uczenia maszynowego. Model określa kroki potrzebne do przekształcenia danych wejściowych w przewidywanie. Za pomocą ML.NET można nabyć model niestandardowy, określając algorytm lub zaimportować wstępnie przeszkolonych modeli TensorFlow i ONNX.

Gdy masz model, można dodać go do aplikacji, aby prognozy.

ML.NET działa w systemach Windows, Linux i macOS przy użyciu programu .NET Core lub systemu Windows przy użyciu programu .NET Framework. 64 bit jest obsługiwany na wszystkich platformach. 32-bitowy jest obsługiwany w systemie Windows, z wyjątkiem funkcji związanych z TensorFlow, LightGBM i ONNX.

Przykłady typów prognoz, które można wykonać za pomocą ML.NET:

|||
|-|-|
|Klasyfikacja/kategoryzacja|Automatyczne dzielenie opinii klientów na kategorie pozytywne i negatywne|
|Regresja/Przewidywanie wartości ciągłych|Przewidywanie cen domów na podstawie wielkości i lokalizacji|
|Wykrywanie anomalii|Wykrywanie nieuczciwych transakcji bankowych |
|Zalecenia|Zaproponuj produkty, które kupujący online mogą chcieć kupić na podstawie wcześniejszych zakupów|
|Dane szeregowe/sekwencyjne|Prognoza pogody/sprzedaży produktów|
|Klasyfikacja obrazów|Kategoryzuj patologie na obrazach medycznych|

## <a name="hello-mlnet-world"></a>Witaj ML.NET Świecie

Kod w poniższym fragmencie kodu pokazuje najprostszą aplikację ML.NET. W tym przykładzie konstruuje model regresji liniowej do przewidywania cen domów przy użyciu danych rozmiaru domu i ceny.

 ```csharp
    using System;
    using Microsoft.ML;
    using Microsoft.ML.Data;

    class Program
    {
        public class HouseData
        {
            public float Size { get; set; }
            public float Price { get; set; }
        }

        public class Prediction
        {
            [ColumnName("Score")]
            public float Price { get; set; }
        }

        static void Main(string[] args)
        {
            MLContext mlContext = new MLContext();

            // 1. Import or create training data
            HouseData[] houseData = {
                new HouseData() { Size = 1.1F, Price = 1.2F },
                new HouseData() { Size = 1.9F, Price = 2.3F },
                new HouseData() { Size = 2.8F, Price = 3.0F },
                new HouseData() { Size = 3.4F, Price = 3.7F } };
            IDataView trainingData = mlContext.Data.LoadFromEnumerable(houseData);

            // 2. Specify data preparation and model training pipeline
            var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
                .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));

            // 3. Train model
            var model = pipeline.Fit(trainingData);

            // 4. Make a prediction
            var size = new HouseData() { Size = 2.5F };
            var price = mlContext.Model.CreatePredictionEngine<HouseData, Prediction>(model).Predict(size);

            Console.WriteLine($"Predicted price for size: {size.Size*1000} sq ft= {price.Price*100:C}k");

            // Predicted price for size: 2500 sq ft= $261.98k
        }
    }
```

## <a name="code-workflow"></a>Przepływ pracy kodu

Poniższy diagram przedstawia strukturę kodu aplikacji, a także iteracyjny proces tworzenia modelu:

- Zbieranie i ładowanie danych szkoleniowych do obiektu **IDataView**
- Określ potok operacji w celu wyodrębnienia funkcji i zastosowania algorytmu uczenia maszynowego
- Trenuj model, wywołując **fit()** w potoku
- Oceń model i iterate, aby poprawić
- Zapisz model w formacie binarnym, do użycia w aplikacji
- Załaduj model z powrotem do obiektu **ITransformer**
- Dokonaj prognoz, wywołując **CreatePredictionEngine.Predict()**

![ML.NET przepływ rozwoju aplikacji, w tym składniki do generowania danych, opracowywania potoku, szkolenia modelu, oceny modelu i użycia modelu](./media/mldotnet-annotated-workflow.png)

Zagłębijmy się nieco głębiej w te koncepcje.

## <a name="machine-learning-model"></a>Model uczenia maszynowego

Model ML.NET jest obiektem, który zawiera przekształcenia do wykonania na danych wejściowych, aby dotrzeć do przewidywanego danych wyjściowych.

### <a name="basic"></a>Podstawowa (Basic)

Najbardziej podstawowym modelem jest dwuwymiarowa regresja liniowa, gdzie jedna ciągła ilość jest proporcjonalna do drugiej, jak w powyższym przykładzie ceny domu.

![Model regresji liniowej z parametrami odchylenia i wagi](./media/linear-regression-model.svg)

Model jest po prostu: $Price = b + Rozmiar * w$. Parametry $b$ i $w $ są szacowane przez zamontowanie linii na zestawie par (rozmiar, cena). Dane używane do znajdowania parametrów modelu są nazywane **danymi treningowymi.** Dane wejściowe modelu uczenia maszynowego są nazywane **funkcjami**. W tym przykładzie $Size$ jest jedyną funkcją. Wartości prawdy gruntu używane do szkolenia modelu uczenia maszynowego są nazywane **etykietami.** W tym miejscu wartości $Price$ w zestawie danych szkoleniowych są etykietami.

### <a name="more-complex"></a>Bardziej złożone

Bardziej złożony model klasyfikuje transakcje finansowe na kategorie przy użyciu opisu tekstu transakcji.

Każdy opis transakcji jest podzielony na zestaw funkcji przez usunięcie zbędnych wyrazów i znaków oraz zliczanie kombinacji wyrazów i znaków. Zestaw funkcji służy do uczenia modelu liniowego na podstawie zestawu kategorii w danych szkoleniowych. Im bardziej podobny jest nowy opis do opisu w zestawie szkoleniowym, tym bardziej prawdopodobne jest, że zostanie przypisany do tej samej kategorii.

![Model klasyfikacji tekstu](./media/text-classification-model.svg)

Zarówno model ceny domu, jak i model klasyfikacji tekstu są modelami **liniowymi.** W zależności od charakteru danych i rozwiązywania problemu można również użyć modeli **drzewa decyzyjnego,** **uogólnionych** modeli dodatków i innych. Więcej informacji na temat modeli można znaleźć w [obszarze Zadania](./resources/tasks.md).

## <a name="data-preparation"></a>Przygotowywanie danych

W większości przypadków dostępne dane nie są odpowiednie do bezpośredniego uczenia modelu uczenia maszynowego. Nieprzetworzone dane muszą być przygotowane lub wstępnie przetworzone, zanim będzie można go użyć do znalezienia parametrów modelu. Dane mogą wymagać konwersji z wartości ciągu do reprezentacji liczbowej. Być może w danych wejściowych mogą być dostępne nadmiarowe informacje. Może być konieczne zmniejszenie lub rozszerzenie wymiarów danych wejściowych. Dane mogą wymagać znormalizowania lub skalowania.

[Samouczki ML.NET](./tutorials/index.md) uczą o różnych potokach przetwarzania danych dla tekstu, obrazu, numerycznych i szeregów czasowych danych używanych do określonych zadań uczenia maszynowego.

[Jak przygotować dane](./how-to-guides/prepare-data-ml-net.md) pokazuje, jak zastosować przygotowanie danych bardziej ogólnie.

W sekcji zasobów można znaleźć dodatek wszystkich [dostępnych przekształceń.](./resources/transforms.md)

## <a name="model-evaluation"></a>Ocena modelu

Po przeszkoleniu modelu, skąd wiesz, jak dobrze będzie to w przyszłości prognozy? Za pomocą ML.NET można ocenić model na niektóre nowe dane testowe.

Każdy typ zadania uczenia maszynowego ma metryki używane do oceny dokładności i dokładności modelu w stosunku do zestawu danych testowych.

W naszym przykładzie ceny domu użyliśmy zadania **Regresja.** Aby ocenić model, dodaj następujący kod do oryginalnego przykładu.

```csharp
        HouseData[] testHouseData =
        {
            new HouseData() { Size = 1.1F, Price = 0.98F },
            new HouseData() { Size = 1.9F, Price = 2.1F },
            new HouseData() { Size = 2.8F, Price = 2.9F },
            new HouseData() { Size = 3.4F, Price = 3.6F }
        };

        var testHouseDataView = mlContext.Data.LoadFromEnumerable(testHouseData);
        var testPriceDataView = model.Transform(testHouseDataView);

        var metrics = mlContext.Regression.Evaluate(testPriceDataView, labelColumnName: "Price");

        Console.WriteLine($"R^2: {metrics.RSquared:0.##}");
        Console.WriteLine($"RMS error: {metrics.RootMeanSquaredError:0.##}");

        // R^2: 0.96
        // RMS error: 0.19
```

Metryki oceny powiedzieć, że błąd jest low-owski i że korelacja między przewidywane dane wyjściowe i dane wyjściowe testu jest wysoka. To było łatwe! W rzeczywistych przykładach trwa więcej strojenia, aby osiągnąć dobre metryki modelu.

## <a name="mlnet-architecture"></a>architektura ML.NET

W tej sekcji przechodzimy przez wzorce architektoniczne ML.NET. Jeśli jesteś doświadczonym deweloperem .NET, niektóre z tych wzorców będą znane, a niektóre będą mniej znane. Trzymaj się mocno, podczas gdy my nurkujemy!

Aplikacja ML.NET rozpoczyna <xref:Microsoft.ML.MLContext> się od obiektu. Ten pojedynczy obiekt zawiera **katalogi**. Katalog jest fabryką do ładowania i zapisywania danych, przekształca, trenerów i składników operacji modelu. Każdy obiekt katalogu ma metody tworzenia różnych typów składników:

|||||
|-|-|-|-|
|Ładowanie i zapisywanie danych||<xref:Microsoft.ML.DataOperationsCatalog>||
|Przygotowywanie danych||<xref:Microsoft.ML.TransformsCatalog>||
|Algorytmy szkoleniowe|Klasyfikacja binarna|<xref:Microsoft.ML.BinaryClassificationCatalog>||
||Klasyfikacja wieloklasowa|<xref:Microsoft.ML.MulticlassClassificationCatalog>||
||Wykrywanie anomalii|<xref:Microsoft.ML.AnomalyDetectionCatalog>||
||Klastrowanie|<xref:Microsoft.ML.ClusteringCatalog>||
||Prognozowanie|<xref:Microsoft.ML.ForecastingCatalog>||
||Ranking|<xref:Microsoft.ML.RankingCatalog>||
||Regresja|<xref:Microsoft.ML.RegressionCatalog>||
||Zalecenie|<xref:Microsoft.ML.RecommendationCatalog>|dodawanie `Microsoft.ML.Recommender` pakietu NuGet|
||Seria czasu|<xref:Microsoft.ML.TimeSeriesCatalog>|dodawanie `Microsoft.ML.TimeSeries` pakietu NuGet|
|Użycie modelu ||<xref:Microsoft.ML.ModelOperationsCatalog>||

Można przejść do metod tworzenia w każdej z powyższych kategorii. Za pomocą programu Visual Studio katalogi są wyświetlane za pośrednictwem programu IntelliSense.

   ![Intellisense dla trenerów regresji](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a>Tworzenie potoku

Wewnątrz każdego katalogu jest zestaw metod rozszerzenia. Przyjrzyjmy się, jak metody rozszerzenia są używane do tworzenia potoku szkolenia.

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
```

We fragmencie `Concatenate` `Sdca` kodu i obie metody w katalogu. Każdy z nich tworzy obiekt [IEstimator,](xref:Microsoft.ML.IEstimator%601) który jest dołączany do potoku.

W tym momencie obiekty są tworzone tylko. Nie doszło do wykonania.

### <a name="train-the-model"></a>Uczenie modelu

Po utworzeniu obiektów w potoku dane mogą służyć do nauczenia modelu.

```csharp
    var model = pipeline.Fit(trainingData);
```

Wywołanie `Fit()` używa danych wejściowych szkolenia do oszacowania parametrów modelu. Jest to nazywane szkoleniem modelu. Należy pamiętać, że powyższy model regresji liniowej miał dwa parametry modelu: **stronniczość** i **wagę.** Po `Fit()` wywołaniu wartości parametrów są znane. Większość modeli będzie miała o wiele więcej parametrów niż ten.

Możesz dowiedzieć się więcej o szkoleniu modelu w [Jak trenować swój model](./how-to-guides/train-machine-learning-model-ml-net.md).

Wynikowy obiekt modelu implementuje <xref:Microsoft.ML.ITransformer> interfejs. Oznacza to, że model przekształca dane wejściowe w prognozy.

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a>Korzystanie z modelu

Dane wejściowe można przekształcać w prognozy zbiorczo lub jedno dane wejściowe naraz. W przykładzie ceny domu zrobiliśmy oba: zbiorczo w celu oceny modelu, a po jednym na raz, aby dokonać nowej prognozy. Przyjrzyjmy się tworzeniu pojedynczych prognoz.

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = mlContext.CreatePredictionEngine<HouseData, Prediction>(model);
    var price = predEngine.Predict(size);
```

Metoda `CreatePredictionEngine()` przyjmuje klasy wejściowej i klasy wyjściowej. Nazwy pól i/lub atrybuty kodu określają nazwy kolumn danych używanych podczas szkolenia i przewidywania modelu. Możesz przeczytać o [Jak zrobić pojedyncze przewidywanie](./how-to-guides/single-predict-model-ml-net.md) w sekcji Instrukcje.

### <a name="data-models-and-schema"></a>Modele danych i schemat

W centrum ML.NET potoku uczenia maszynowego są [DataView](xref:Microsoft.ML.IDataView) obiektów.

Każda transformacja w potoku ma schemat wejściowy (nazwy danych, typy i rozmiary, które transformacja oczekuje, aby zobaczyć na jego danych wejściowych); i schemat wyjściowy (nazwy danych, typy i rozmiary, które transformacja tworzy po transformacji). Poniższy dokument zawiera szczegółowe wyjaśnienie [interfejsu IDataView i jego systemu typów](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html).

Jeśli schemat wyjściowy z jednej transformacji w potoku nie pasuje do schematu wejściowego następnego przekształcenia, ML.NET zwyżenie wyjątku.

Obiekt widoku danych ma kolumny i wiersze. Każda kolumna ma nazwę, typ i długość. Na przykład kolumny wejściowe w przykładzie ceny domu to **Rozmiar** i **Cena**. Są one zarówno typu i są ilości skalarne, a nie te wektorowe.

   ![przykład ML.NET widoku danych z danymi dotyczącymi prognozowania cen nieruchomości](./media/ml-net-dataview.png)

Wszystkie ML.NET algorytmy poszukują kolumny wejściowej, która jest wektorem. Domyślnie ta kolumna wektorowa nosi nazwę **Funkcje**. Dlatego połączyliśmy kolumnę **Size** w nową kolumnę o nazwie **Funkcje** w naszym przykładzie ceny domu.

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

Wszystkie algorytmy również utworzyć nowe kolumny po wykonaniu prognozowania. Stałe nazwy tych nowych kolumn zależą od typu algorytmu uczenia maszynowego. W przypadku zadania regresji jedna z nowych kolumn nosi nazwę **Score**. Dlatego przypisaliśmy nasze dane cenowe o tej nazwie.

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```

Więcej informacji na temat kolumn wyjściowych różnych zadań uczenia maszynowego można znaleźć w przewodniku [zadania uczenia maszynowego.](resources/tasks.md)

Ważną właściwością DataView obiektów jest, że są one oceniane **leniwie**. Widoki danych są ładowane i obsługiwane tylko podczas szkolenia i oceny modelu oraz prognozowania danych. Podczas pisania i testowania aplikacji ML.NET, można użyć debugera Programu Visual Studio, aby zerknąć na dowolny obiekt widoku danych, wywołując [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview*) metody.

```csharp
    var debug = testPriceDataView.Preview();
```

Można obejrzeć `debug` zmienną w debugerze i sprawdzić jej zawartość. Nie należy używać podglądu metody w kodzie produkcyjnym, ponieważ znacznie obniża wydajność.

### <a name="model-deployment"></a>Wdrażanie modelu

W rzeczywistych aplikacjach kodu szkolenia i oceny modelu będzie oddzielony od prognozowania. W rzeczywistości te dwa działania są często wykonywane przez oddzielne zespoły. Zespół programistycznych modelu można zapisać model do użycia w aplikacji przewidywania.

```csharp
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="next-steps"></a>Następne kroki

* Dowiedz się, jak tworzyć aplikacje przy użyciu różnych zadań uczenia maszynowego z bardziej realistycznymi zestawami danych w [samouczkach](./tutorials/index.md).

* Więcej informacji na temat konkretnych tematów można uzyskać w [podręcznikach Jak to zrobić.](./how-to-guides/index.md)

* Jeśli jesteś bardzo zainteresowany, możesz zanurzyć się bezpośrednio w [dokumentacji referencyjnej API.](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet)
