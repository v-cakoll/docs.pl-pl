---
title: Co to jest strukturze ML.NET i jak to działa?
description: Strukturze ML.NET daje możliwość dodawania usługi machine learning do aplikacji platformy .NET. Dzięki tej możliwości, istnieje możliwość automatycznego prognozy przy użyciu danych, które są dostępne dla aplikacji. W tym artykule opisano podstawy uczenia maszynowego w strukturze ML.NET.
ms.date: 04/10/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
author: natke
ms.openlocfilehash: 054fa0e1d9d8cc0d7c32efd4a9e8c81b91cb1335
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960426"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a>Co to jest strukturze ML.NET i jak to działa?

Strukturze ML.NET daje możliwość dodawania usługi machine learning do aplikacji platformy .NET. Dzięki tej możliwości, istnieje możliwość automatycznego prognozy przy użyciu danych, które są dostępne dla aplikacji. W tym artykule opisano podstawy uczenia maszynowego w strukturze ML.NET. 

Typ prognoz, które można wprowadzić za pomocą platformy ML.NET należą:

|||
|-|-|
|Klasyfikacja/kategoryzacji|Automatycznie podzielić opinie na kategorie dodatnie i ujemne|
|Regresja/Predict ciągłe wartości|Przewidzieć cenę infrastrukturę, w oparciu o rozmiar i położenie|
|Wykrywanie anomalii|Wykrywanie transakcji bankowych oszustwa |
|Zalecenia|Zaproponuj produktów, które online kupujący mogą chcieć to kupić, oparte na poprzednim zakupów|

## <a name="hello-mlnet-world"></a>Witaj, świecie strukturze ML.NET

W poniższym fragmencie kodu demonstruje najprostszej aplikacji strukturze ML.NET. Ten przykład tworzy model regresji liniowej do prognozowania cen DOM przy użyciu danych o wielkości i ceny domu. W aplikacjach rzeczywistych danych i modelu będzie znacznie bardziej złożone.

 ```csharp
    using System;
    using System.IO;
    using Microsoft.Data.DataView;
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

## <a name="code-workflow"></a>Kod przepływu pracy

Poniższy diagram przedstawia strukturę kodu aplikacji, jak również proces iteracyjny modelu programowania:
- Zbieranie i załadować dane szkoleniowe **IDataView** obiektu
- Określ potoku operacji wyodrębnianie funkcji i stosowanie algorytmu uczenia maszynowego
- Uczenie modelu przez wywołanie metody **Fit()** do potoku
- Ocena modelu i modyfikować w celu
- Zapisz model do formatu binarnego, do użycia w aplikacji
- Ładowanie modelu do **ITransformer** obiektu
- Prognozowania, wywołując **CreatePredictionEngine.Predict()**

![Przepływ rozwoju aplikacji strukturze ML.NET tym składników Generowanie danych, opracowywanie potoku, szkoleń modelowych, oceny modelu i użycia modelu](./media/mldotnet-annotated-workflow.png) 

Przyjrzyjmy się nieco bardziej szczegółowe informacje te pojęcia.

## <a name="machine-learning-model"></a>Model uczenia maszynowego

Na model w strukturze ML.NET jest obiektem, który zawiera przekształceń w celu wykonania na danych wejściowych na dostęp do przewidywanych danych wyjściowych.

### <a name="basic"></a>Podstawowy

To najbardziej podstawowy model jest dwuwymiarowy regresji liniowej, gdzie jeden ilość ciągłego jest proporcjonalna do innego, tak jak w powyższym przykładzie cena dom. 

![Liniowy modelu regresji przy użyciu parametrów odchylenie i wagę rekordu](./media/linear-regression-model.svg)

Model, który jest po prostu: $Price = b + rozmiar * w$. $ Parametry $b i $w$ są szacowane przez dopasowanie wiersza w zestawie (rozmiar, cena) pary. Dane, używana do znajdowania parametrów modelu są nazywane **dane szkoleniowe**. Dane wejściowe modelu uczenia maszynowego są nazywane **funkcji**. W tym przykładzie $Size$ jest jedyną funkcją. Wartości PRAWDA podstaw używane do trenowania modelu usługi machine learning są nazywane **etykiety**. W tym miejscu $Price$ szkoleniowy zestaw danych mają etykiety.

### <a name="more-complex"></a>Bardziej złożone

Bardziej złożonych model klasyfikuje transakcji finansowych na kategorie za pomocą transakcji tekst opisu.

Opis każdej transakcji został podzielony na zestaw funkcji przez usunięcie nadmiarowych wyrazów i znaków, a wciąż dochodzą nowe kombinacje znaków i word. Zestaw funkcji jest używany do nauczenia modelu liniowego, na podstawie zestawu kategorii w danych szkoleniowych. Im więcej podobne nowy opis w zestaw szkoleniowy, tym większe prawdopodobieństwo zostanie do niej przypisany do tej samej kategorii. 

![Model klasyfikacji tekstu](./media/text-classification-model.svg)

Zarówno w modelu DOM ceny, jak i model klasyfikacji tekstu **liniowej** modeli. W zależności od charakteru danych i są rozwiązywania problemów można również użyć **drzewa decyzyjnego** modeli, **uogólniony dodatku** modeli i inne. Możesz dowiedzieć się więcej na temat modeli w [zadania](./resources/tasks.md).

## <a name="data-preparation"></a>Przygotowywanie danych

W większości przypadków dane dostępne nie są odpowiednie do użycia bezpośrednio do nauczenia modelu uczenia maszynowego. Nieprzetworzone dane należy do przygotowania i wstępnie przetworzone przed można odnaleźć parametrów modelu. Dane, może być konieczne przekonwertowana z wartościami ciągów w reprezentacji liczbowych. Możesz mieć nadmiarowe informacje w danych wejściowych. Może być konieczne zmniejszenie lub rozszerzeniu wymiary swoich danych wejściowych. Danych może być konieczne może być znormalizowane lub skalowania.

[Samouczki strukturze ML.NET](./tutorials/index.md) nauczą Cię o potoki różnych przetwarzania danych dla tekstu, obrazów danych liczbowych i szeregów czasowych, używane do uczenia maszynowego określonych zadań.

[Jak przygotować dane](./how-to-guides/prepare-data-ml-net.md) dowiesz się, jak można zastosować przygotowywania danych bardziej ogólnie.

Możesz znaleźć dodatku wszystkich [dostępnych transformacji](./resources/transforms.md) w sekcji zasobów.

## <a name="model-evaluation"></a>Ocena modelu

Gdy masz uczony model, skąd wiadomo, jak wprowadzić przewidywania przyszłych? Za pomocą platformy ML.NET będziesz w stanie ocenić modelu w odniesieniu do niektórych nowych danych testowych. 

Każdy typ machine learning zadania ma metryki używane do oceny dokładności i dokładności modelu przed testowego zestawu danych.

W naszym przykładzie cena DOM użyliśmy **regresji** zadania. Aby ocenić modelu, Dodaj następujący kod do oryginalnego przykładu.

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

Metryki oceny informujące o tym, że błąd jest low-ish i tej korelacji między przewidywane wyniki i dane wyjściowe testu jest wysoka. To było łatwe! W przykładach rzeczywistych zajmuje więcej dostrajania do osiągnięcia dobry model metryk.

## <a name="mlnet-architecture"></a>Architektura strukturze ML.NET

W tej sekcji kursu wzorców architektury strukturze ML.NET. Jeśli jesteś doświadczonym deweloperom platformy .NET, niektóre z tych wzorców jest znana użytkownikom, a niektóre są mniej znanych. Przytrzymując ścisłej, możemy zacząć korzystać!

Aplikację strukturze ML.NET rozpoczyna się od <xref:Microsoft.ML.MLContext> obiektu. Ten obiekt pojedyncze zawiera **katalogi**. Wykaz jest fabryki danych, ładowania i zapisywania przekształceń, instruktorów i składników operacji modelu. Każdy obiekt wykazu zawiera metody służące do tworzenia różnych typów składników:

||||
|-|-|-|
|Ładowanie danych i zapisywanie||<xref:Microsoft.ML.DataOperationsCatalog>|
|Przygotowywanie danych||<xref:Microsoft.ML.TransformsCatalog>|
|Szkolenie algorytmów|Klasyfikacja binarna|<xref:Microsoft.ML.BinaryClassificationCatalog>|
||Wieloklasowej klasyfikacji|<xref:Microsoft.ML.MulticlassClassificationCatalog>|
||Wykrywanie anomalii|<xref:Microsoft.ML.AnomalyDetectionCatalog>|
||Klasyfikacja|<xref:Microsoft.ML.RankingCatalog>|
||Regresji|<xref:Microsoft.ML.RegressionCatalog>|
||Zalecenie|<xref:Microsoft.ML.RecommendationCatalog>|
|Sposób użycia modelu ||<xref:Microsoft.ML.ModelOperationsCatalog>|

Możesz przejść do metod tworzenia w każdej z powyższych kategorii. W programie Visual Studio wykazów są wyświetlane za pomocą funkcji IntelliSense.

   ![Funkcja IntelliSense dla Instruktorzy regresji](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a>Tworzenie potoku

W każdym katalogu to zestaw metod rozszerzenia. Przyjrzyjmy się jak metody rozszerzenia są używane do tworzenia potoku szkolenia.

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
```

Ten fragment kodu `Concatenate` i `Sdca` są obie metody w wykazie. Każdy tworzą [IEstimator](xref:Microsoft.ML.IEstimator%601) obiekt, który jest dołączany do potoku.

W tym momencie obiekty są tworzone tylko. Stało się nie wykonania.

### <a name="train-the-model"></a>Uczenie modelu

Po utworzeniu obiektów w potoku danych może służyć do nauczenia modelu.

```csharp
    var model = pipeline.Fit(trainingData);
```

Wywoływanie `Fit()` korzysta z danych wejściowych szkolenia można oszacować parametrów modelu. Jest to nazywane uczenia modelu. Należy pamiętać, że powyższego modelu regresji liniowej ma dwa parametry modelu: **odchylenie** i **wagi**. Po `Fit()` wywołanie, są znane wartości parametrów. Większość modeli mają dużo więcej parametrów niż to.

Dowiedz się więcej na temat szkoleń modelowych w [jak uczenie modelu](./how-to-guides/train-machine-learning-model-ml-net.md)

Wynikowy obiekt modelu implementuje <xref:Microsoft.ML.ITransformer> interfejsu. Oznacza to, że model przekształca dane wejściowe w prognozy.

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a>Użyj modelu

W danym momencie można przekształcić dane wejściowe do przewidywania luzem lub jedne dane wejściowe. W tym przykładzie cena DOM były wykonywane zarówno: w trybie zbiorczym na potrzeby oceny modelu i pojedynczo do nowych prognozowania. Przyjrzyjmy się wprowadzania pojedynczego prognozy.

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = model.CreatePredictionEngine<HouseData, Prediction>(mlContext);
    var price = predEngine.Predict(size);
```
 
`CreatePredictionEngine()` Metoda przyjmuje wejściowe klasy a dane wyjściowe. Nazwy pól i/lub kod atrybuty określają nazwy kolumn danych, używane podczas uczenia modelu i przewidywania. Informacje o [jak pojedynczy przewiduje](./how-to-guides/single-predict-model-ml-net.md) w sekcji porad.

### <a name="data-models-and-schema"></a>Modele danych i schematu

W samym sercu potoku uczenia maszynowego w strukturze ML.NET są [DataView](xref:Microsoft.ML.IDataView) obiektów.

Każde przekształcenie w potoku ma schemat danych wejściowych (danych nazw, typów i rozmiarów, które przekształcenia oczekuje na dane wejściowe); i schemat danych wyjściowych (nazwy danych, typy i rozmiary, których przekształcenie daje po przekształceniu). 

Jeśli schemat danych wyjściowych z jednym przekształcenia w potoku nie jest zgodny schemat danych wejściowych dalej transformacji, strukturze ML.NET spowoduje zgłoszenie wyjątku.

Obiekt widoku danych ma kolumn i wierszy. Każda kolumna ma nazwę i typ i długość. Na przykład: wejściowy kolumn w domu przykład ceny są **rozmiar** i **cena**. Są zarówno typ i ich są skalarnymi, a nie te wektor.

   ![Przykładowy widok danych strukturze ML.NET z danymi przewidywań cena DOM](./media/ml-net-dataview.png)

Wszystkie algorytmy strukturze ML.NET poszukaj kolumny wejściowej, które jest wektorem. Domyślnie ta kolumna wektora jest nazywany **funkcji**. Dlatego firma Microsoft połączonych **rozmiar** kolumny w nową kolumnę o nazwie **funkcji** w naszym przykładzie cena domu.

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

Wszystkie algorytmy także tworzenie nowych kolumn po wykonywanej prognozę. Stałe nazwy tych nowych kolumn zależą od rodzaju algorytmu uczenia maszynowego. W zadaniu regresji, jeden z nowymi kolumnami nosi nazwę **wynik**. Jest to, dlaczego firma Microsoft opartego na atrybutach danych ceny o tej nazwie.

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```    

Możesz dowiedzieć się więcej na temat kolumn wyjściowych uczenia maszynowego różnych zadań w [zadania uczenia maszynowego](resources/tasks.md) przewodnik.

Ważne właściwość DataView obiektów, są one oceniane **opóźnieniem**. Widoki danych są ładowane i tylko zasilaniu podczas uczenia modelu i oceny i przewidywania danych. Podczas pisania i testowania aplikacji strukturze ML.NET, można użyć debugera programu Visual Studio do etapów przy dowolnego obiektu widoku danych, wywołując [Podgląd](xref:Microsoft.ML.DebuggerExtensions.Preview*) metody.

```csharp
    var debug = testPriceDataView.Preview();
```

Możesz obejrzeć `debug` zmiennych debugera i sprawdź jego zawartość. Nie używaj metody (wersja zapoznawcza) w kodzie produkcyjnym, ponieważ znacznie obniża wydajność.

### <a name="model-deployment"></a>Wdrażanie modelu

W rzeczywistych aplikacjach kod uczenie i Ewaluacja modelu będzie nienależący do prognozowania. W rzeczywistości te dwa działania często są wykonywane przez oddzielne zespoły. Twój zespół deweloperów modelu można zapisać modelu do użycia w aplikacji prognozy.

```csharp   
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="where-to-now"></a>Gdzie teraz?

Możesz dowiedzieć się, jak tworzyć aplikacje przy użyciu zadania uczenia maszynowego różnych z bardziej realistycznymi zestawami danych w [samouczki](./tutorials/index.md).

Lub możesz dowiedzieć się o określonych tematów, które bardziej szczegółowo w sekcji [jak do prowadnic](./how-to-guides/index.md).

A jeśli masz bardzo atrakcyjne, możesz od razu bezpośrednio do [dokumentację referencyjną interfejsu API](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet)!
