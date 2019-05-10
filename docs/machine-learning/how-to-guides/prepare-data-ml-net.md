---
title: Przygotowywanie danych
description: Dowiedz się, jak użyć przekształceń w strukturze ML.NET do manipulowania i przygotowuje dane do dodatkowego przetwarzania lub tworzenia modelu.
author: luisquintanilla
ms.author: luquinta
ms.date: 05/03/2019
ms.custom: mvc, how-to
ms.openlocfilehash: 461a00c6ecc1d9a8b9caaca79f9d7905d2bb7528
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063466"
---
# <a name="prepare-data"></a>Przygotowywanie danych

Dowiedz się, jak używać strukturze ML.NET do przygotowywania danych do dodatkowego przetwarzania lub budowania modelu.

Dane są często nieczyste i rozrzedzone. Ponadto algorytmów uczenia maszynowego w strukturze ML.NET oczekiwać, że dane wejściowe lub funkcje, aby być w przypadku pojedynczego wektora wartości liczbowych. Dlatego jest jednym z celów przygotowywania danych do pobrania danych do formatu oczekiwanego przez algorytmy strukturze ML.NET. 

## <a name="filter-data"></a>Filtrowanie danych

Czasami nie wszystkie dane w zestawie danych są istotne dla analizy. Filtrowanie jest sposobem usunięcia danych nie ma znaczenia. [ `DataOperationsCatalog` ](xref:Microsoft.ML.DataOperationsCatalog) Zawiera zestaw operacji filtrów, które pobierają w [ `IDataView` ](xref:Microsoft.ML.IDataView) zawierająca wszystkie dane i zwrócenia [IDataView](xref:Microsoft.ML.IDataView) zawierający tylko dane punktów orientacyjnych. Należy zauważyć, że ponieważ filtr operacje nie są [ `IEstimator` ](xref:Microsoft.ML.IEstimator%601) lub [ `ITransformer` ](xref:Microsoft.ML.ITransformer) , takich jak te w [ `TransformsCatalog` ](xref:Microsoft.ML.TransformsCatalog), nie mogą być dołączone jako część [ `EstimatorChain` ](xref:Microsoft.ML.Data.EstimatorChain%601) lub [ `TransformerChain` ](xref:Microsoft.ML.Data.TransformerChain%601) potoku przygotowywania danych. 

Przy użyciu następujących danych wejściowych, który jest ładowany do [ `IDataView` ](xref:Microsoft.ML.IDataView):

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms=1f,
        Price=100000f
    },
    new HomeData
    {
        NumberOfBedrooms=2f,
        Price=300000f
    },
    new HomeData
    {
        NumberOfBedrooms=6f,
        Price=600000f
    }
};
```

Aby filtrować dane na podstawie wartości kolumny, należy użyć [ `FilterRowsByColumn` ](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) metody.

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

Powyższe przykładowe przyjmuje wierszy w zestawie danych z ceną między 200000 do 1 000 000. Wynik zastosowania ten filtr będzie zwracać tylko ostatnie dwa wiersze danych i pominąć pierwszy wiersz, ponieważ jej miesięczna cena to 100000, a nie od określonego zakresu.

## <a name="replace-missing-values"></a>Zastąp wartości Brak

Brak wartości są wystąpieniem typowe w zestawach danych. Jedno z podejść do radzenia sobie z brakującymi wartościami ma zastąpić je wartością domyślną dla danego typu lub innej mająca znaczenie wartość, takie jak średnia wartość w danych. 

Przy użyciu następujących danych wejściowych, który jest ładowany do [ `IDataView` ](xref:Microsoft.ML.IDataView):

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms=1f,
        Price=100000f
    },
    new HomeData
    {
        NumberOfBedrooms=2f,
        Price=300000f
    },
    new HomeData
    {
        NumberOfBedrooms=6f,
        Price=float.NaN
    }
};
```

Należy zauważyć, że po ostatnim elemencie w naszej listy ma Brak wartości dla `Price`. Aby zastąpić brakujących wartości w `Price` kolumny, użyj [ `ReplaceMissingValues` ](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) metodę, aby wypełnić tę wartość Brak.

> [!IMPORTANT]
> [`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) działa tylko z danymi liczbowymi.

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

Strukturze ML.NET obsługuje różne [tryby zastąpienie](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode). Przykład powyżej używa `Mean` trybu zastępczy, który wypełni brakujące wartością średniej wartości tej kolumny. Wypełnia wyniku zastąpienia `Price` właściwość po ostatnim elemencie w naszych danych za pomocą 200 000, ponieważ jest średnią 100 000 i 300 000. 

## <a name="use-normalizers"></a>Użyj normalizers

[Normalizacja](https://en.wikipedia.org/wiki/Feature_scaling) danych, przetwarzanie wstępne technika używana do standaryzacji funkcje, które nie znajdują się na tę samą skalę, która pomaga algorytmy zbiegają się szybciej. Na przykład zakresy dla wartości, takich jak wiek i przychody się istotnie różnić o wieku ogólnie jest z zakresu od 0 do 100 i przychody ogólnie znajdujące się w zakresie od zera do tysięcy. Odwiedź stronę [stronę przekształcenia](../resources/transforms.md) bardziej szczegółowe listę i opis przekształcenia normalizacji. 

### <a name="min-max-normalization"></a>Normalizacji minimum-maksimum

Przy użyciu następujących danych wejściowych, który jest ładowany do [ `IDataView` ](xref:Microsoft.ML.IDataView):

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms = 2f,
        Price = 200000f
    },
    new HomeData
    {
        NumberOfBedrooms = 1f,
        Price = 100000f
    }
};
```

Normalizacji danych przy użyciu normalizacji minimum maksimum [ `NormalizeMinMax` ](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) metody.

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

Oryginalne wartości cen `[200000,100000]` są konwertowane na `[ 1, 0.5 ]` przy użyciu `MinMax` Formuła normalizacji, które generuje wartości wyjściowe w zakresie 0 – 1.

### <a name="binning"></a>Kwantowanie

[Kwantowanie](https://en.wikipedia.org/wiki/Data_binning) konwertuje ciągłe wartości dyskretnych reprezentacja danych wejściowych. Na przykład załóżmy, że jedna z funkcji jest okres ważności. Zamiast używania wartości rzeczywistej wiek, pakowania tworzy zakresy dla tej wartości. 0 – 18 może być jednego pojemnika, inny może być 19 – 35 i tak dalej. 

Przy użyciu następujących danych wejściowych, który jest ładowany do [ `IDataView` ](xref:Microsoft.ML.IDataView):

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms=1f,
        Price=100000f
    },
    new HomeData
    {
        NumberOfBedrooms=2f,
        Price=300000f
    },
    new HomeData
    {
        NumberOfBedrooms=6f,
        Price=600000f
    }
};
```

Normalizacji danych do pojemniki przy użyciu [ `NormalizeBinning` ](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning*) metody. `maximumBinCount` Parametr umożliwia określenie liczba pojemników potrzebne do klasyfikowania danych. W tym przykładzie dane będą umieszczone dwa pojemniki.  

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

Wynik pakowania tworzy granice bin `[0,200000,Infinity]`. W związku z tym pojemniki wynikowe są `[0,1,1]` ponieważ pierwszy obserwacji jest z zakresu od 0 200000 i inne są większe niż 200000, ale mniejszą niż nieskończoność.

## <a name="work-with-categorical-data"></a>Praca z danymi podzielonych na kategorie

Dane podzielone na kategorie nieliczbowe musi być konwertowany na liczbę przed ich użyciem do tworzenia modelu uczenia maszynowego. 

Przy użyciu następujących danych wejściowych, który jest ładowany do [ `IDataView` ](xref:Microsoft.ML.IDataView):

```csharp
CarData[] cars = new CarData[] 
{
    new CarData
    {
        Color="Red",
        VehicleType="SUV"
    },
    new CarData
    {
        Color="Blue",
        VehicleType="Sedan"
    },
    new CarData
    {
        Color="Black",
        VehicleType="SUV"
    }
};
```

Podzielone na kategorie `VehicleType` właściwości mogą być konwertowane na numer przy użyciu [ `OneHotEncoding` ](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*) metody. 

```csharp
// Define categorical transform estimator
var categoricalEstimator = mlContext.Transforms.Categorical.OneHotEncoding("VehicleType");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer categoricalTransformer = categoricalEstimator.Fit(data);

// Transform Data
IDataView transformedData = categoricalTransformer.Transform(data);
```

Wynikowy przekształcenie konwertuje wartość tekstu `VehicleType` na liczbę. Wpisy w `VehicleType` kolumny stają się następujące po zastosowaniu przekształcenia: 

```text
[
    1, // SUV
    2, // Sedan
    1 // SUV
]
```

## <a name="work-with-text-data"></a>Praca z danymi tekstu

Dane tekstowe muszą zostać przekształcone na liczby, przed jego użyciem, aby zbudować model uczenia maszynowego. Odwiedź stronę [stronę przekształcenia](../resources/transforms.md) bardziej szczegółową listę i opis przekształcenia tekstu.

Korzystanie z danych, takich jak dane poniżej, który został załadowany do [ `IDataView` ](xref:Microsoft.ML.IDataView):

```csharp
ReviewData[] reviews = new ReviewData[]
{
    new ReviewData
    {
        Description="This is a good product",
        Rating=4.7f
    },
    new ReviewData
    {
        Description="This is a bad product",
        Rating=2.3f
    }
};
```

Minimalna krokiem do konwertowania tekstu do reprezentacji liczbowych wektora jest używanie [ `FeaturizeText` ](xref:Microsoft.ML.TextCatalog.FeaturizeText*) metody. Za pomocą [ `FeaturizeText` ](xref:Microsoft.ML.TextCatalog.FeaturizeText*) przekształcenie, które szereg przekształcenia jest stosowany do kolumny wprowadzania tekstu, co w przypadku wektora wartości liczbowych, reprezentujący znormalizowane lp word i ngrams znak. 

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

Przekształcanie wynikowy będzie konwersji wartości tekstowe w `Description` kolumny liczbowe wektor, który wygląda podobnie do danych wyjściowych poniżej:

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

Przetwarzanie złożonych tekstu łączenia wchodzi do [ `EstimatorChain` ](xref:Microsoft.ML.Data.EstimatorChain%601) usunąć hałasu i zmniejszenie ilości zasobów do przetwarzania wymagane zgodnie z potrzebami.

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

`textEstimator` zawiera podzestaw operacji wykonywanych przez [ `FeaturizeText` ](xref:Microsoft.ML.TextCatalog.FeaturizeText*) metody. Korzyści wynikające z bardziej złożonych potoku kontroli i widoczności umieszczeniu transformacji zastosowanych względem danych. 

Przy użyciu pierwszej pozycji, na przykład, poniżej przedstawiono szczegółowy opis efektów kroki przekształcania definicją `textEstimator`:

**Oryginalny tekst: Jest to dobry produktu**

|Transformacja | Opis | Wynik
|--|--|--|
|1. NormalizeText | Konwertuje wszystkie litery na małe litery, domyślnie | jest to dobry produktu
|2. TokenizeWords | Dzieli dane ciągu do poszczególnych wyrazów | ["to", "is", "","dobre","produkt"]
|3. RemoveDefaultStopWords | Usuwa Stop-słowa, takie jak *jest* i *a*. | ["dobre", "produkt"]
|4. MapValueToKey | Mapuje wartości kluczy (kategorie), na podstawie danych wejściowych |  [1,2]
|5. ProduceNGrams | Przekształca tekst w sekwencji kolejnych wyrazów | [1,1,1,0,0]
|6. NormalizeLpNorm | Skala wejść przez ich lp typ norm | [ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]
