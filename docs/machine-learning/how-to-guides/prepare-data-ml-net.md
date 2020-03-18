---
title: Przygotowywanie danych do tworzenia modelu
description: Dowiedz się, jak używać przekształceń w ML.NET do manipulowania i przygotowywania danych do dodatkowego przetwarzania lub tworzenia modeli.
author: luisquintanilla
ms.author: luquinta
ms.date: 01/29/2020
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 12f933253af9ea519d711c20227fe075fed003de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77452990"
---
# <a name="prepare-data-for-building-a-model"></a>Przygotowywanie danych do tworzenia modelu

Dowiedz się, jak używać ML.NET do przygotowania danych do dodatkowego przetwarzania lub tworzenia modelu.

Dane są często nieczyste i rzadkie. ML.NET algorytmy uczenia maszynowego oczekują, że dane wejściowe lub funkcje będą w jednym wektoru liczbowym. Podobnie wartość do przewidywania (etykieta), zwłaszcza gdy jest to dane kategoryczne, musi być zakodowany. Dlatego jednym z celów przygotowania danych jest uzyskanie danych do formatu oczekiwanego przez algorytmy ML.NET.

## <a name="filter-data"></a>Filtrowanie danych

Czasami nie wszystkie dane w zestawie danych są istotne do analizy. Podejście do usuwania nieistotnych danych jest filtrowanie. Zawiera [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) zestaw operacji filtrowania, które [`IDataView`](xref:Microsoft.ML.IDataView) przyjmują w zawierające wszystkie dane i zwracają [IDataView](xref:Microsoft.ML.IDataView) zawierający tylko punkty zainteresowania danych. Należy pamiętać, że ponieważ [`IEstimator`](xref:Microsoft.ML.IEstimator%601) operacje filtrowania [`ITransformer`](xref:Microsoft.ML.ITransformer) nie są [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog)lub podobne do tych [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) w [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) , nie mogą być uwzględnione jako część lub potoku przygotowania danych.

Weź następujące dane wejściowe i [`IDataView`](xref:Microsoft.ML.IDataView) załaduj je do tzw: `data`

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

Aby filtrować dane na podstawie wartości [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) kolumny, należy użyć tej metody.

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

Powyższy przykład pobiera wiersze w zestawie danych z ceną między 200000 a 1000000. Wynik stosowania tego filtru zwróci tylko dwa ostatnie wiersze w danych i wykluczyć pierwszy wiersz, ponieważ jego cena wynosi 100000, a nie między określonym zakresem.

## <a name="replace-missing-values"></a>Zamień brakujące wartości

Brakujące wartości są częstym wystąpieniem w zestawach danych. Jednym z podejść do radzenia sobie z brakujących wartości jest zastąpienie ich wartością domyślną dla danego typu, jeśli istnieje lub inna znacząca wartość, taka jak średnia wartość w danych.

Weź następujące dane wejściowe i [`IDataView`](xref:Microsoft.ML.IDataView) załaduj je do tzw: `data`

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

Należy zauważyć, że ostatni element na `Price`naszej liście ma brakującą wartość dla . Aby zastąpić brakujące wartości `Price` w kolumnie, należy użyć [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) metody, aby wypełnić tę brakującą wartość.

> [!IMPORTANT]
> [`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A)działa tylko z danymi liczbowymi.

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

ML.NET obsługuje różne [tryby wymiany](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode). Powyższy przykład `Mean` używa trybu wymiany, który wypełnia brakującą wartość średnią wartością tej kolumny. Wynik wymiany wypełnia `Price` właściwość dla ostatniego elementu w naszych danych z 200.000, ponieważ jest to średnia 100.000 i 300.000.

## <a name="use-normalizers"></a>Użyj normalizatorów

[Normalizacja](https://en.wikipedia.org/wiki/Feature_scaling) jest techniką wstępnego przetwarzania danych używaną do skalowania funkcji w tym samym zakresie, zwykle między 0 a 1, dzięki czemu mogą być dokładniej przetwarzane przez algorytm uczenia maszynowego. Na przykład zakresy wiekowe i dochody różnią się znacznie w zależności od wieku, który zazwyczaj mieści się w przedziale od 0 do 100, a dochód jest zazwyczaj w zakresie od zera do tysięcy. Odwiedź [stronę przekształceń,](../resources/transforms.md) aby uzyskać bardziej szczegółową listę i opis przekształceń normalizacyjnych.

### <a name="min-max-normalization"></a>Normalizacja Min-Max

Weź następujące dane wejściowe i [`IDataView`](xref:Microsoft.ML.IDataView) załaduj je do tzw: `data`

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

Normalizację można zastosować do kolumn z pojedynczymi wartościami liczbowymi, a także wektorów. Normalizuj dane `Price` w kolumnie za pomocą [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) normalizacji min-max za pomocą metody.

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

Oryginalne wartości `[200000,100000]` cen są `[ 1, 0.5 ]` konwertowane `MinMax` na przy użyciu formuły normalizacji, która generuje wartości wyjściowe w zakresie 0-1.

### <a name="binning"></a>Binning

[Binning](https://en.wikipedia.org/wiki/Data_binning) konwertuje wartości ciągłe na dyskretną reprezentację danych wejściowych. Załóżmy na przykład, że jedną z funkcji jest wiek. Zamiast używać rzeczywistej wartości wieku, binning tworzy zakresy dla tej wartości. 0-18 może być jeden pojemnik, inny może być 19-35 i tak dalej.

Weź następujące dane wejściowe i [`IDataView`](xref:Microsoft.ML.IDataView) załaduj je do tzw: `data`

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

Normalizuj dane do [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A) pojemników przy użyciu metody. Parametr `maximumBinCount` umożliwia określenie liczby pojemników potrzebnych do sklasyfikowania danych. W tym przykładzie dane zostaną wprowadzone do dwóch pojemników.

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

Wynik binningu tworzy granice `[0,200000,Infinity]`pojemnika . Dlatego powstałe pojemniki `[0,1,1]` są, ponieważ pierwsza obserwacja jest między 0-200000, a pozostałe są większe niż 200000, ale mniej niż nieskończoność.

## <a name="work-with-categorical-data"></a>Praca z danymi kategorycznymi

Jednym z najczęstszych typów danych są dane podzielone na kategorie. Dane kategoryczne mają skończoną liczbę kategorii. Na przykład stany USA lub lista typów zwierząt znalezionych w zestawie zdjęć. Niezależnie od tego, czy dane kategorii są operacjami, czy etykietami, muszą być mapowane na wartość liczbową, aby można je było użyć do wygenerowania modelu uczenia maszynowego. Istnieje wiele sposobów pracy z danymi kategorii w ML.NET, w zależności od problemu, który rozwiązujesz.

### <a name="key-value-mapping"></a>Mapowanie wartości klucza

W ML.NET klucz jest wartością całkowitą reprezentującą kategorię. Mapowanie wartości klucza jest najczęściej używane do mapowania etykiet ciągów do unikatowych wartości całkowitych dla szkolenia, a następnie z powrotem do ich wartości ciągów, gdy model jest używany do przewidywania.

Przekształcenia używane do wykonywania mapowania wartości klucza są [MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) i [MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A).

`MapValueToKey`dodaje słownik mapowania w modelu, dzięki `MapKeyToValue` czemu można wykonać odwrotną transformację podczas przewidywania.

### <a name="one-hot-encoding"></a>Jedno gorące kodowanie

Jedno kodowanie gorące przyjmuje skończony zestaw wartości i mapuje je na liczby `1` całkowite, których reprezentacja binarna ma jedną wartość w unikatowych pozycjach w ciągu. Jedno gorące kodowanie może być najlepszym wyborem, jeśli nie ma niejawnej kolejności danych kategorii. W poniższej tabeli przedstawiono przykład z kodami pocztowymi jako wartościami surowymi.

|Wartość pierwotna|Jedna zakodowana wartość zakodowana na gorąco|
|---------|---------------------|
|98052|00...01|
|98100|00...10|
|...|...|
|98109|10...00|

Transformacja do konwersji danych kategorycznych na jednogorące numery zakodowane jest [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A).

### <a name="hashing"></a>Mieszania

Haszowanie to kolejny sposób konwertowania danych kategorycznie na liczby. Funkcja mieszania mapuje dane o dowolnym rozmiarze (na przykład ciąg tekstu) na liczbę o stałym zakresie. Haszowanie może być szybkim i efektywnym w przestrzeni sposobem wektorowania obiektów. Godnym uwagi przykładem mieszania w uczeniu maszynowym jest filtrowanie spamu e-mail, w którym zamiast utrzymywać słownik znanych słów, każde słowo w wiadomości e-mail jest haszowane i dodawane do dużego wektora funkcji. Używanie mieszania w ten sposób pozwala uniknąć problemu złośliwego filtrowania spamu przez używanie słów, które nie znajdują się w słowniku.

ML.NET umożliwia transformację [mieszania](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) w celu wykonania mieszania tekstu, dat i danych liczbowych. Podobnie jak mapowanie klucza wartości, wyjścia transformacji mieszania są typami kluczy.

## <a name="work-with-text-data"></a>Praca z danymi tekstowymi

Podobnie jak dane kategoryczne, dane tekstowe muszą zostać przekształcone w funkcje liczbowe przed użyciem go do utworzenia modelu uczenia maszynowego. Odwiedź [stronę przekształceń,](../resources/transforms.md) aby uzyskać bardziej szczegółową listę i opis przekształceń tekstu.

Korzystanie z danych, takich jak dane [`IDataView`](xref:Microsoft.ML.IDataView)poniżej, który został załadowany do :

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

ML.NET zapewnia [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) transformację, która przyjmuje wartość ciągu tekstu i tworzy zestaw funkcji z tekstu, stosując serię pojedynczych przekształceń.

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

Wynikowa transformacja konwertuje `Description` wartości tekstowe w kolumnie na wektor numeryczny, który wygląda podobnie do danych wyjściowych poniżej:

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

Przekształcenia, które tworzą `FeaturizeText` mogą być również stosowane indywidualnie dla ściślejszej kontroli ziarna nad generowaniem funkcji.

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

`textEstimator`zawiera podzbiór operacji wykonywanych [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) przez metodę. Zaletą bardziej złożonego potoku jest kontrola i widoczność przekształceń stosowanych do danych.

Na przykładzie pierwszego wpisu przedstawiono szczegółowy opis wyników opracowanych przez kroki `textEstimator`transformacji zdefiniowane przez:

**Oryginalny tekst: Jest to dobry produkt**

|Przekształcanie | Opis | Wynik
|--|--|--|
|1. NormalizujTekst | Domyślnie konwertuje wszystkie litery na małe litery | jest to dobry produkt
|2. TokenizeWords | Dzieli ciąg na poszczególne wyrazy | ["to","jest","a",,"dobry",produkt"]
|3. UsuńDefaultStopWords | Usuwa stopwords jak *jest* *i*. | ["dobry","produkt"]
|4. MapValueToKey | Mapuje wartości na klucze (kategorie) na podstawie danych wejściowych |  [1,2]
|5. ProduceNGrams | Przekształca tekst w sekwencję kolejnych słów | [1,1,1,0,0]
|6. Normalizuj Normę Lp | Skaluj dane wejściowe według ich lp-norm | [ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]
