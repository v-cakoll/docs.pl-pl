---
title: Przygotowywanie danych do kompilowania modelu
description: Dowiedz się, jak używać transformacji w programie ML.NET, aby manipulować i przygotowywać dane do dodatkowego przetwarzania lub kompilowania modeli.
author: luisquintanilla
ms.author: luquinta
ms.date: 09/11/2019
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 4452aef351f33df532f3c673307dedbbf71631b8
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929374"
---
# <a name="prepare-data-for-building-a-model"></a>Przygotowywanie danych do kompilowania modelu

Dowiedz się, w jaki sposób używać ML.NET do przygotowywania danych do dodatkowego przetwarzania lub tworzenia modelu.

Dane często są nieoczyszczone i rozrzedzone. Algorytmy uczenia maszynowego ML.NET oczekują wejścia lub funkcje, które mogą znajdować się w pojedynczym wektorze liczbowym. Podobnie, wartość do prognozowania (etykieta), szczególnie w przypadku kategorii danych, musi być zakodowana. W związku z tym jednym z celów przygotowywania danych jest uzyskanie danych do formatu oczekiwanego przez algorytmy ML.NET. 

## <a name="filter-data"></a>Filtrowanie danych

Czasami nie wszystkie dane w zestawie danych są związane z analizą. Podejście do usuwania nieistotnych danych jest filtrowanie. Zawiera zestaw operacji filtrowania, które przyjmują [`IDataView`](xref:Microsoft.ML.IDataView) wszystkie dane i zwracają [IDataView](xref:Microsoft.ML.IDataView) zawierające tylko interesujące punkty danych. [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) Należy pamiętać, że [`IEstimator`](xref:Microsoft.ML.IEstimator%601) ponieważ operacje filtrowania nie są ani [`ITransformer`](xref:Microsoft.ML.ITransformer) takie jak te w programie [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), nie można [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) ich uwzględnić jako części potoku przygotowywania lub [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) przygotowania danych. 

Użycie następujących danych wejściowych, które są ładowane do [`IDataView`](xref:Microsoft.ML.IDataView):

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

Aby filtrować dane na podstawie wartości kolumny, użyj [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) metody.

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

Powyższy przykład pobiera wiersze w zestawie danych z ceną z zakresu od 200000 do 1000000. Wynikiem zastosowania tego filtru będzie zwrócenie tylko ostatnich dwóch wierszy danych i wykluczenie pierwszego wiersza, ponieważ jego cena jest 100000, a nie pomiędzy określonym zakresem.

## <a name="replace-missing-values"></a>Zamień brakujące wartości

Brakujące wartości są typowym wystąpieniem w zestawach danych. Jednym z metod postępowania z brakującymi wartościami jest zastąpienie ich wartością domyślną dla danego typu, jeśli jakakolwiek lub inna wartość istotna, taka jak wartość średnia w danych. 

Użycie następujących danych wejściowych, które są ładowane do [`IDataView`](xref:Microsoft.ML.IDataView):

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

Zwróć uwagę, że ostatni element na naszej liście ma brakującą wartość `Price`dla. Aby zastąpić brakujące wartości w `Price` kolumnie, [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) Użyj metody, aby wypełnić tę brakującą wartość.

> [!IMPORTANT]
> [`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*)działa tylko z danymi liczbowymi.

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

ML.NET obsługuje różne [tryby wymiany](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode). Powyższy przykład używa `Mean` trybu zamiany, który spowoduje wypełnienie brakującej wartości wartością średnią tej kolumny. Wynikiem zamiany jest wypełnienie `Price` właściwości ostatniego elementu w danych z 200 000, ponieważ jest to średnia z 100 000 i 300 000. 

## <a name="use-normalizers"></a>Korzystanie z normalizacji

[Normalizacja](https://en.wikipedia.org/wiki/Feature_scaling) to technika przetwarzania wstępnego danych używana do standaryzacji funkcji, które nie znajdują się na tej samej skali, co ułatwia algorytmom szybsze wywoływanie zbieżności. Na przykład zakresy wartości, takie jak wiek i dochód, różnią się znacznie w stosunku do wieku w zakresie 0-100 i przychodów ogólnie w zakresie od zera do tysięcy. Odwiedź [stronę przekształcenia](../resources/transforms.md) , aby uzyskać bardziej szczegółową listę i opis transformacji normalizacji. 

### <a name="min-max-normalization"></a>Minimalna-Maksymalna normalizacja

Użycie następujących danych wejściowych, które są ładowane do [`IDataView`](xref:Microsoft.ML.IDataView):

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

Normalizację można zastosować do kolumn z pojedynczą wartością liczbową, a także wektorami. Normalizuje dane w `Price` kolumnie, używając minimalnej normalizacji [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) z metodą.

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

Pierwotne wartości `[200000,100000]` cen są konwertowane na `[ 1, 0.5 ]` użycie `MinMax` formuły normalizacji, która generuje wartości wyjściowe z zakresu 0-1.

### <a name="binning"></a>Pakowania

[Pakowania](https://en.wikipedia.org/wiki/Data_binning) konwertuje ciągłe wartości na dyskretną reprezentację danych wejściowych. Załóżmy na przykład, że jedna z Twoich funkcji jest w wieku. Zamiast korzystać z rzeczywistej wartości wieku, pakowania tworzy zakresy dla tej wartości. 0-18 może być jednym pojemnikem, innym może być 19-35 i tak dalej. 

Użycie następujących danych wejściowych, które są ładowane do [`IDataView`](xref:Microsoft.ML.IDataView):

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

Normalizowanie danych do pojemników przy użyciu [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning*) metody. `maximumBinCount` Parametr umożliwia określenie liczby pojemników potrzebnych do klasyfikowania danych. W tym przykładzie dane będą umieszczane w dwóch pojemnikach.  

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

Wynik pakowania tworzy granice `[0,200000,Infinity]`bin. W związku z tym te `[0,1,1]` pojemniki są spowodowane tym, że Pierwsza obserwacja jest między 0-200000 a pozostałe są większe niż 200000, ale mniejsze niż nieskończoność.

## <a name="work-with-categorical-data"></a>Pracuj z danymi kategorii

Dane nieliczbowe kategorii muszą zostać przekonwertowane na liczbę przed użyciem do kompilowania modelu uczenia maszynowego. 

Użycie następujących danych wejściowych, które są ładowane do [`IDataView`](xref:Microsoft.ML.IDataView):

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

Właściwość kategorii `VehicleType` można przekonwertować na liczbę [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*) przy użyciu metody. 

```csharp
// Define categorical transform estimator
var categoricalEstimator = mlContext.Transforms.Categorical.OneHotEncoding("VehicleType");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer categoricalTransformer = categoricalEstimator.Fit(data);

// Transform Data
IDataView transformedData = categoricalTransformer.Transform(data);
```

Wynikiem przekształcenia jest konwertowanie wartości `VehicleType` tekstowej na liczbę. Po zastosowaniu przekształcenia `VehicleType` wpisy w kolumnie stają się następujące: 

```text
[
    1, // SUV
    2, // Sedan
    1 // SUV
]
```

## <a name="work-with-text-data"></a>Pracuj z danymi tekstowymi

Aby można było utworzyć model uczenia maszynowego, dane tekstowe muszą zostać przekształcone w liczby. Odwiedź [stronę przekształcenia](../resources/transforms.md) , aby uzyskać bardziej szczegółową listę i opis przekształceń tekstu.

Używając danych, takich jak poniższe dane, które zostały załadowane [`IDataView`](xref:Microsoft.ML.IDataView)do:

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

Minimalny krok konwersji tekstu na cyfrową reprezentację wektorową polega na użyciu [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) metody. Przy użyciu [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) transformacji serie przekształceń są stosowane do kolumny tekstu wejściowego, co jest wektorem liczbowym reprezentującym słowo LP-znormalizowane i znaki ngrams. 

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

Wynikowa transformacja spowoduje przekonwertowanie wartości tekstowych w `Description` kolumnie na wektor liczbowy, który wygląda podobnie do danych wyjściowych poniżej:

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

Połącz złożone kroki przetwarzania tekstu w [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) celu usunięcia szumu i potencjalnie Zmniejsz ilość wymaganych zasobów przetwarzania zgodnie z potrzebami.

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

`textEstimator`zawiera podzestaw operacji wykonywanych przez [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) metodę. Zaletą bardziej złożonej potoku jest kontrola i widoczność przekształceń zastosowanych do danych. 

Przy użyciu pierwszego wpisu na przykład, poniżej przedstawiono szczegółowy opis wyników przedstawionych przez kroki transformacji zdefiniowane przez `textEstimator`:

**Oryginalny tekst: Jest to dobry produkt**

|Transformacja | Opis | Wynik
|--|--|--|
|1. NormalizeText | Konwertuje domyślnie wszystkie litery na małe | jest to dobry produkt
|2. TokenizeWords | Dzieli ciąg na pojedyncze wyrazy | ["This", "is", "a", "dobry", "Product"]
|3. RemoveDefaultStopWords | Usuwa Stop-słowa, *takie* jak *i.* | ["dobry", "produkt"]
|4. MapValueToKey | Mapuje wartości na klucze (kategorie) w oparciu o dane wejściowe |  [1,2]
|5. ProduceNGrams | Przekształca tekst w sekwencję kolejnych wyrazów | [1,1,1,0,0]
|6. NormalizeLpNorm | Skalowanie danych wejściowych według ich standardu LP | [0,577350529, 0,577350529, 0,577350529, 0, 0]
