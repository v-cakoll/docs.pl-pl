---
title: Co to jest ML.NET i jak to działa?
description: ML.NET umożliwia dodawanie uczenia maszynowego do aplikacji platformy .NET w scenariuszach online lub offline. Dzięki tej funkcji można dokonać automatycznych prognoz przy użyciu danych dostępnych dla aplikacji bez konieczności konieczności podłączenia do sieci do używania ML.NET. W tym artykule wyjaśniono podstawy uczenia maszynowego w ML.NET.
ms.date: 11/5/2019
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: 0929005e02ad9b43636213735f8c7232aa6d4f42
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607774"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a>Co to jest ML.NET i jak to działa?

ML.NET umożliwia dodawanie uczenia maszynowego do aplikacji platformy .NET w scenariuszach online lub offline. Dzięki tej funkcji można dokonać automatycznych prognoz przy użyciu danych dostępnych dla aplikacji. Aplikacje uczenia maszynowego korzystają z wzorców w danych, aby przewidywanie, a nie muszą być jawnie zaprogramowane.

Centralnym ML.NET jest **model**uczenia maszynowego. Model określa kroki potrzebne do przekształcenia danych wejściowych w prognozę. Za pomocą ML.NET można trenować model niestandardowy, określając algorytm lub zaimportować wstępnie przeszkolone modele TensorFlow i ONNX.

Po modelu, można dodać go do aplikacji, aby prognoz.

ML.NET działa w systemach Windows, Linux i macOS przy użyciu platformy .NET Core lub systemu Windows przy użyciu programu .NET Framework. 64 bit jest obsługiwany na wszystkich platformach. 32-bitowe jest obsługiwane w systemie Windows, z wyjątkiem funkcji tensorflow, LightGBM i ONNX.

Przykłady typu prognoz, które można wykonać za pomocą ML.NET:

|||
|-|-|
|Klasyfikacja/Kategoryzacja|Automatyczne dzielenie opinii klientów na kategorie pozytywne i negatywne|
|Regresja/Przewidywanie wartości ciągłych|Przewiduj ceny domów na podstawie wielkości i lokalizacji|
|Wykrywanie anomalii|Wykrywanie nieuczciwych transakcji bankowych |
|Zalecenia|Zaproponuj produkty, które kupujący online mogą chcieć kupić, na podstawie ich poprzednich zakupów|
|Szeregi czasowe/dane sekwencyjne|Prognoza pogody/sprzedaży produktów|
|Klasyfikacja obrazów|Kategoryzowanie patologii na obrazach medycznych|

## <a name="hello-mlnet-world"></a>Witam ML.NET świecie

Kod w poniższym urywek pokazuje najprostszy ML.NET aplikacji. W tym przykładzie konstruuje model regresji liniowej do przewidywania cen domów przy użyciu wielkości domu i danych cenowych.

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

Poniższy diagram reprezentuje strukturę kodu aplikacji, a także iteracyjnego procesu tworzenia modelu:

- Zbieranie i ładowanie danych szkoleniowych do obiektu **IDataView**
- Określanie potoku operacji wyodrębniania funkcji i stosowanie algorytmu uczenia maszynowego
- Trenuj model, wywołując **Fit()** na potoku
- Oceń model i iteruj, aby poprawić
- Zapisywanie modelu w formacie binarnym do użycia w aplikacji
- Załaduj model z powrotem do obiektu **ITransformer**
- Twórz prognozy, wywołując **CreatePredictionEngine.Predict()**

![ML.NET przepływ tworzenia aplikacji, w tym składniki do generowania danych, tworzenia potoku, szkolenia modelu, oceny modelu i użycia modelu](./media/mldotnet-annotated-workflow.png)

Zagłębimy się nieco głębiej w te koncepcje.

## <a name="machine-learning-model"></a>Model uczenia maszynowego

Model ML.NET jest obiektem, który zawiera przekształcenia do wykonania na danych wejściowych, aby dotrzeć do przewidywanych danych wyjściowych.

### <a name="basic"></a>Podstawowy

Najbardziej podstawowym modelem jest dwuwymiarowa regresja liniowa, gdzie jedna ciągła ilość jest proporcjonalna do innej, jak w powyższym przykładzie ceny domu.

![Model regresji liniowej z parametrami odchylenia i masy](./media/linear-regression-model.svg)

Model jest po prostu: $Price = b + rozmiar * w$. Parametry $b$ i $w $ są szacowane przez dopasowanie linii na zestawie par (rozmiar, cena). Dane używane do znajdowania parametrów modelu nazywane są **danymi treningowymi**. Dane wejściowe modelu uczenia maszynowego są nazywane **funkcjami**. W tym przykładzie $Size$ jest jedyną funkcją. Wartości prawdy gruntu używane do uczenia modelu uczenia maszynowego są nazywane **etykietami.** W tym miejscu $Price$ wartości w zestawie danych szkolenia są etykiety.

### <a name="more-complex"></a>Bardziej złożone

Bardziej złożony model klasyfikuje transakcje finansowe na kategorie przy użyciu opisu tekstu transakcji.

Każdy opis transakcji jest podzielony na zestaw funkcji, usuwając zbędne wyrazy i znaki oraz licząc kombinacje słów i znaków. Zestaw funkcji służy do trenowania modelu liniowego na podstawie zestawu kategorii w danych szkoleniowych. Im bardziej podobny jest nowy opis do tych w zestawie treningowym, tym większe prawdopodobieństwo, że zostanie on przypisany do tej samej kategorii.

![Model klasyfikacji tekstu](./media/text-classification-model.svg)

Zarówno model ceny domu, jak i model klasyfikacji tekstu są modelami **liniowymi.** W zależności od charakteru danych i rozwiązywanego problemu można również użyć modeli **drzewa decyzyjnego,** **uogólnionych** modeli dodatków i innych. Możesz dowiedzieć się więcej o modelach w [zadaniach](./resources/tasks.md).

## <a name="data-preparation"></a>Przygotowywanie danych

W większości przypadków dostępne dane nie są odpowiednie do bezpośredniego uczenia modelu uczenia maszynowego. Nieprzetworzone dane muszą być przygotowane lub wstępnie przetworzone, zanim będzie można je użyć do znalezienia parametrów modelu. Dane mogą wymagać konwersji z wartości ciągu na reprezentację numeryczną. W danych wejściowych mogą znajdować się nadmiarowe informacje. Może być konieczne zmniejszenie lub rozszerzenie wymiarów danych wejściowych. Dane mogą wymagać normalizacji lub skalowania.

Samouczki [ML.NET](./tutorials/index.md) uczą o różnych potokach przetwarzania danych dla danych tekstowych, graficznych, numerycznych i szeregów czasowych używanych do określonych zadań uczenia maszynowego.

[Sposób przygotowania danych](./how-to-guides/prepare-data-ml-net.md) pokazuje, jak zastosować przygotowanie danych bardziej ogólnie.

Dodatek wszystkich [dostępnych przekształceń](./resources/transforms.md) można znaleźć w sekcji zasoby.

## <a name="model-evaluation"></a>Ocena modelu

Po przeszkoleniu modelu, skąd wiesz, jak dobrze będzie to w przyszłości prognozy? Za pomocą ML.NET można ocenić model na kilka nowych danych testowych.

Każdy typ zadania uczenia maszynowego ma metryki używane do oceny dokładności i precyzji modelu względem zestawu danych testowych.

W naszym przykładzie ceny domu użyliśmy zadania **regresji.** Aby ocenić model, dodaj następujący kod do oryginalnego przykładu.

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

Metryki oceny mówią, że błąd jest niski-owski i że korelacja między przewidywanych danych wyjściowych i danych wyjściowych testu jest wysoka. To było łatwe! W rzeczywistych przykładach potrzeba więcej strojenia, aby osiągnąć dobre metryki modelu.

## <a name="mlnet-architecture"></a>architektura ML.NET

W tej sekcji przechodzimy przez wzory architektoniczne ML.NET. Jeśli jesteś doświadczonym deweloperem platformy .NET, niektóre z tych wzorców będą ci znane, a niektóre będą mniej znane. Trzymaj się mocno, a my zanurzamy się!

Aplikacja ML.NET rozpoczyna się od <xref:Microsoft.ML.MLContext> obiektu. Ten obiekt singleton zawiera **katalogi**. Katalog jest fabryką ładowania i zapisywania danych, przekształcania, trenerów i składników operacji modelu. Każdy obiekt katalogu ma metody tworzenia różnych typów składników:

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
||CzasSeries|<xref:Microsoft.ML.TimeSeriesCatalog>|dodawanie `Microsoft.ML.TimeSeries` pakietu NuGet|
|Użycie modelu ||<xref:Microsoft.ML.ModelOperationsCatalog>||

Można przejść do metod tworzenia w każdej z powyższych kategorii. Za pomocą programu Visual Studio katalogi są wyświetlane za pośrednictwem programu IntelliSense.

   ![Intellisense dla trenerów regresji](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a>Zbuduj potok

Wewnątrz każdego katalogu znajduje się zestaw metod rozszerzenia. Przyjrzyjmy się, jak metody rozszerzenia są używane do tworzenia potoku szkolenia.

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
```

We urywek `Concatenate` i `Sdca` są obie metody w katalogu. Każdy z nich tworzy obiekt [IEstimator,](xref:Microsoft.ML.IEstimator%601) który jest dołączany do potoku.

W tym momencie obiekty są tworzone tylko. Nie doszło do egzekucji.

### <a name="train-the-model"></a>Uczenie modelu

Po utworzeniu obiektów w potoku, dane mogą służyć do szkolenia modelu.

```csharp
    var model = pipeline.Fit(trainingData);
```

Wywołanie `Fit()` używa danych szkoleniowych wejściowych do oszacowania parametrów modelu. Jest to znane jako szkolenie modelu. Pamiętaj, że model regresji liniowej powyżej miał dwa parametry modelu: **odchylenie** i **wagę**. Po `Fit()` wywołaniu znane są wartości parametrów. Większość modeli będzie miała o wiele więcej parametrów niż to.

Możesz dowiedzieć się więcej o szkoleniu modelu w [jak trenować model](./how-to-guides/train-machine-learning-model-ml-net.md).

Wynikowy obiekt modelu implementuje <xref:Microsoft.ML.ITransformer> interfejs. Oznacza to, że model przekształca dane wejściowe w prognozy.

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a>Użyj modelu

Dane wejściowe można przekształcić w prognozowania zbiorczo lub jedno dane wejściowe naraz. W przykładzie ceny domu zrobiliśmy zarówno: luzem w celu oceny modelu, jak i jeden po drugim, aby dokonać nowej prognozy. Przyjrzyjmy się pojedynczym prognozom.

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = mlContext.CreatePredictionEngine<HouseData, Prediction>(model);
    var price = predEngine.Predict(size);
```

Metoda `CreatePredictionEngine()` przyjmuje klasę danych wejściowych i klasę danych wyjściowych. Nazwy pól i/lub atrybuty kodu określają nazwy kolumn danych używanych podczas szkolenia i przewidywania modelu. Aby uzyskać więcej informacji, zobacz [Owydowienie prognoz z przeszkolonym modelem](how-to-guides/machine-learning-model-predictions-ml-net.md).

### <a name="data-models-and-schema"></a>Modele danych i schemat

Sednem ML.NET potoku uczenia maszynowego są obiekty [DataView.](xref:Microsoft.ML.IDataView)

Każda transformacja w potoku ma schemat wejściowy (nazwy danych, typy i rozmiary, które transformacja oczekuje, aby zobaczyć na jego danych wejściowych); oraz schemat danych wyjściowych (nazwy danych, typy i rozmiary, które transformacja tworzy po transformacji). Poniższy dokument zawiera szczegółowe wyjaśnienie [interfejsu IDataView i jego systemu typów.](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html)

Jeśli schemat danych wyjściowych z jednego przekształcenia w potoku nie pasuje do schematu wejściowego następnego przekształcenia, ML.NET zgłosić wyjątek.

Obiekt widoku danych zawiera kolumny i wiersze. Każda kolumna ma nazwę, typ i długość. Na przykład kolumny wejściowe w przykładzie ceny domu to **Rozmiar** i **Cena**. Są one zarówno typu i są one skalarne ilości, a nie wektora.

   ![przykład ML.NET Data View z danymi prognozowania cen nieruchomości](./media/ml-net-dataview.png)

Wszystkie algorytmy ML.NET wyszukują kolumnę wejściową, która jest wektorem. Domyślnie ta kolumna wektorowa nosi nazwę **Funkcje**. Dlatego połączyliśmy kolumnę **Rozmiar** z nową kolumną o nazwie **Funkcje** w naszym przykładzie ceny domu.

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

Wszystkie algorytmy również utworzyć nowe kolumny po wykonaniu prognozowania. Stałe nazwy tych nowych kolumn zależą od typu algorytmu uczenia maszynowego. W przypadku zadania regresji jedna z nowych kolumn nosi nazwę **Wynik**. Dlatego przypisaliśmy nasze dane cenowe tą nazwą.

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```

Więcej informacji na temat kolumn wyjściowych różnych zadań uczenia maszynowego można znaleźć w przewodniku [Zadania uczenia maszynowego.](resources/tasks.md)

Ważną właściwością obiektów DataView jest to, że są one oceniane **leniwie.** Widoki danych są ładowane i obsługiwane tylko podczas szkolenia i oceny modelu oraz przewidywania danych. Podczas pisania i testowania aplikacji ML.NET, można użyć debugera programu Visual Studio, aby zajrzeć do dowolnego obiektu widoku danych, wywołując [metodę podglądu.](xref:Microsoft.ML.DebuggerExtensions.Preview*)

```csharp
    var debug = testPriceDataView.Preview();
```

Można obejrzeć `debug` zmienną w debugerze i zbadać jej zawartość. Nie należy używać podglądu metody w kodzie produkcyjnym, ponieważ znacznie obniża wydajność.

### <a name="model-deployment"></a>Wdrażanie modelu

W rzeczywistych aplikacjach kod szkolenia i oceny modelu będzie oddzielony od prognozowania. W rzeczywistości te dwie czynności są często wykonywane przez oddzielne zespoły. Zespół deweloperów modelu można zapisać modelu do użycia w aplikacji przewidywania.

```csharp
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="next-steps"></a>Następne kroki

* Dowiedz się, jak tworzyć aplikacje przy użyciu różnych zadań uczenia maszynowego z bardziej realistycznymi zestawami danych w [samouczkach](./tutorials/index.md).

* Dowiedz się więcej o konkretnych tematach w [przewodnikach](./how-to-guides/index.md).

* Jeśli jesteś bardzo chętny, możesz zanurzyć się bezpośrednio w [dokumentacji api reference.](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet)
