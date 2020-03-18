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
# <a name="prepare-data-for-building-a-model"></a><span data-ttu-id="f3310-103">Przygotowywanie danych do tworzenia modelu</span><span class="sxs-lookup"><span data-stu-id="f3310-103">Prepare data for building a model</span></span>

<span data-ttu-id="f3310-104">Dowiedz się, jak używać ML.NET do przygotowania danych do dodatkowego przetwarzania lub tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="f3310-104">Learn how to use ML.NET to prepare data for additional processing or building a model.</span></span>

<span data-ttu-id="f3310-105">Dane są często nieczyste i rzadkie.</span><span class="sxs-lookup"><span data-stu-id="f3310-105">Data is often unclean and sparse.</span></span> <span data-ttu-id="f3310-106">ML.NET algorytmy uczenia maszynowego oczekują, że dane wejściowe lub funkcje będą w jednym wektoru liczbowym.</span><span class="sxs-lookup"><span data-stu-id="f3310-106">ML.NET machine learning algorithms expect input or features to be in a single numerical vector.</span></span> <span data-ttu-id="f3310-107">Podobnie wartość do przewidywania (etykieta), zwłaszcza gdy jest to dane kategoryczne, musi być zakodowany.</span><span class="sxs-lookup"><span data-stu-id="f3310-107">Similarly, the value to predict (label), especially when it's categorical data, has to be encoded.</span></span> <span data-ttu-id="f3310-108">Dlatego jednym z celów przygotowania danych jest uzyskanie danych do formatu oczekiwanego przez algorytmy ML.NET.</span><span class="sxs-lookup"><span data-stu-id="f3310-108">Therefore one of the goals of data preparation is to get the data into the format expected by ML.NET algorithms.</span></span>

## <a name="filter-data"></a><span data-ttu-id="f3310-109">Filtrowanie danych</span><span class="sxs-lookup"><span data-stu-id="f3310-109">Filter data</span></span>

<span data-ttu-id="f3310-110">Czasami nie wszystkie dane w zestawie danych są istotne do analizy.</span><span class="sxs-lookup"><span data-stu-id="f3310-110">Sometimes, not all data in a dataset is relevant for analysis.</span></span> <span data-ttu-id="f3310-111">Podejście do usuwania nieistotnych danych jest filtrowanie.</span><span class="sxs-lookup"><span data-stu-id="f3310-111">An approach to remove irrelevant data is filtering.</span></span> <span data-ttu-id="f3310-112">Zawiera [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) zestaw operacji filtrowania, które [`IDataView`](xref:Microsoft.ML.IDataView) przyjmują w zawierające wszystkie dane i zwracają [IDataView](xref:Microsoft.ML.IDataView) zawierający tylko punkty zainteresowania danych.</span><span class="sxs-lookup"><span data-stu-id="f3310-112">The [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) contains a set of filter operations that take in an [`IDataView`](xref:Microsoft.ML.IDataView) containing all of the data and return an [IDataView](xref:Microsoft.ML.IDataView) containing only the data points of interest.</span></span> <span data-ttu-id="f3310-113">Należy pamiętać, że ponieważ [`IEstimator`](xref:Microsoft.ML.IEstimator%601) operacje filtrowania [`ITransformer`](xref:Microsoft.ML.ITransformer) nie są [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog)lub podobne do tych [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) w [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) , nie mogą być uwzględnione jako część lub potoku przygotowania danych.</span><span class="sxs-lookup"><span data-stu-id="f3310-113">It's important to note that because filter operations are not an [`IEstimator`](xref:Microsoft.ML.IEstimator%601) or [`ITransformer`](xref:Microsoft.ML.ITransformer) like those in the [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), they cannot be included as part of an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) or [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) data preparation pipeline.</span></span>

<span data-ttu-id="f3310-114">Weź następujące dane wejściowe i [`IDataView`](xref:Microsoft.ML.IDataView) załaduj je do tzw: `data`</span><span class="sxs-lookup"><span data-stu-id="f3310-114">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="f3310-115">Aby filtrować dane na podstawie wartości [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) kolumny, należy użyć tej metody.</span><span class="sxs-lookup"><span data-stu-id="f3310-115">To filter data based on the value of a column, use the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) method.</span></span>

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

<span data-ttu-id="f3310-116">Powyższy przykład pobiera wiersze w zestawie danych z ceną między 200000 a 1000000.</span><span class="sxs-lookup"><span data-stu-id="f3310-116">The sample above takes rows in the dataset with a price between 200000 and 1000000.</span></span> <span data-ttu-id="f3310-117">Wynik stosowania tego filtru zwróci tylko dwa ostatnie wiersze w danych i wykluczyć pierwszy wiersz, ponieważ jego cena wynosi 100000, a nie między określonym zakresem.</span><span class="sxs-lookup"><span data-stu-id="f3310-117">The result of applying this filter would return only the last two rows in the data and exclude the first row because its price is 100000 and not between the specified range.</span></span>

## <a name="replace-missing-values"></a><span data-ttu-id="f3310-118">Zamień brakujące wartości</span><span class="sxs-lookup"><span data-stu-id="f3310-118">Replace missing values</span></span>

<span data-ttu-id="f3310-119">Brakujące wartości są częstym wystąpieniem w zestawach danych.</span><span class="sxs-lookup"><span data-stu-id="f3310-119">Missing values are a common occurrence in datasets.</span></span> <span data-ttu-id="f3310-120">Jednym z podejść do radzenia sobie z brakujących wartości jest zastąpienie ich wartością domyślną dla danego typu, jeśli istnieje lub inna znacząca wartość, taka jak średnia wartość w danych.</span><span class="sxs-lookup"><span data-stu-id="f3310-120">One approach to dealing with missing values is to replace them with the default value for the given type if any or another meaningful value such as the mean value in the data.</span></span>

<span data-ttu-id="f3310-121">Weź następujące dane wejściowe i [`IDataView`](xref:Microsoft.ML.IDataView) załaduj je do tzw: `data`</span><span class="sxs-lookup"><span data-stu-id="f3310-121">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="f3310-122">Należy zauważyć, że ostatni element na `Price`naszej liście ma brakującą wartość dla .</span><span class="sxs-lookup"><span data-stu-id="f3310-122">Notice that the last element in our list has a missing value for `Price`.</span></span> <span data-ttu-id="f3310-123">Aby zastąpić brakujące wartości `Price` w kolumnie, należy użyć [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) metody, aby wypełnić tę brakującą wartość.</span><span class="sxs-lookup"><span data-stu-id="f3310-123">To replace the missing values in the `Price` column, use the [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) method to fill in that missing value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f3310-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A)działa tylko z danymi liczbowymi.</span><span class="sxs-lookup"><span data-stu-id="f3310-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) only works with numerical data.</span></span>

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

<span data-ttu-id="f3310-125">ML.NET obsługuje różne [tryby wymiany](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span><span class="sxs-lookup"><span data-stu-id="f3310-125">ML.NET supports various [replacement modes](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span></span> <span data-ttu-id="f3310-126">Powyższy przykład `Mean` używa trybu wymiany, który wypełnia brakującą wartość średnią wartością tej kolumny.</span><span class="sxs-lookup"><span data-stu-id="f3310-126">The sample above uses the `Mean` replacement mode, which fills in the missing value with that column's average value.</span></span> <span data-ttu-id="f3310-127">Wynik wymiany wypełnia `Price` właściwość dla ostatniego elementu w naszych danych z 200.000, ponieważ jest to średnia 100.000 i 300.000.</span><span class="sxs-lookup"><span data-stu-id="f3310-127">The replacement 's result fills in the `Price` property for the last element in our data with 200,000 since it's the average of 100,000 and 300,000.</span></span>

## <a name="use-normalizers"></a><span data-ttu-id="f3310-128">Użyj normalizatorów</span><span class="sxs-lookup"><span data-stu-id="f3310-128">Use normalizers</span></span>

<span data-ttu-id="f3310-129">[Normalizacja](https://en.wikipedia.org/wiki/Feature_scaling) jest techniką wstępnego przetwarzania danych używaną do skalowania funkcji w tym samym zakresie, zwykle między 0 a 1, dzięki czemu mogą być dokładniej przetwarzane przez algorytm uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="f3310-129">[Normalization](https://en.wikipedia.org/wiki/Feature_scaling) is a data pre-processing technique used to scale features to be in the same range, usually between 0 and 1, so that they can be more accurately processed by a machine learning algorithm.</span></span> <span data-ttu-id="f3310-130">Na przykład zakresy wiekowe i dochody różnią się znacznie w zależności od wieku, który zazwyczaj mieści się w przedziale od 0 do 100, a dochód jest zazwyczaj w zakresie od zera do tysięcy.</span><span class="sxs-lookup"><span data-stu-id="f3310-130">For example, the ranges for age and income vary significantly with age generally being in the range of 0-100 and income generally being in the range of zero to thousands.</span></span> <span data-ttu-id="f3310-131">Odwiedź [stronę przekształceń,](../resources/transforms.md) aby uzyskać bardziej szczegółową listę i opis przekształceń normalizacyjnych.</span><span class="sxs-lookup"><span data-stu-id="f3310-131">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of normalization transforms.</span></span>

### <a name="min-max-normalization"></a><span data-ttu-id="f3310-132">Normalizacja Min-Max</span><span class="sxs-lookup"><span data-stu-id="f3310-132">Min-Max normalization</span></span>

<span data-ttu-id="f3310-133">Weź następujące dane wejściowe i [`IDataView`](xref:Microsoft.ML.IDataView) załaduj je do tzw: `data`</span><span class="sxs-lookup"><span data-stu-id="f3310-133">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="f3310-134">Normalizację można zastosować do kolumn z pojedynczymi wartościami liczbowymi, a także wektorów.</span><span class="sxs-lookup"><span data-stu-id="f3310-134">Normalization can be applied to columns with single numerical values as well as vectors.</span></span> <span data-ttu-id="f3310-135">Normalizuj dane `Price` w kolumnie za pomocą [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) normalizacji min-max za pomocą metody.</span><span class="sxs-lookup"><span data-stu-id="f3310-135">Normalize the data in the `Price` column using min-max normalization with the [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) method.</span></span>

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

<span data-ttu-id="f3310-136">Oryginalne wartości `[200000,100000]` cen są `[ 1, 0.5 ]` konwertowane `MinMax` na przy użyciu formuły normalizacji, która generuje wartości wyjściowe w zakresie 0-1.</span><span class="sxs-lookup"><span data-stu-id="f3310-136">The original price values `[200000,100000]` are converted to `[ 1, 0.5 ]` using the `MinMax` normalization formula that generates output values in the range of 0-1.</span></span>

### <a name="binning"></a><span data-ttu-id="f3310-137">Binning</span><span class="sxs-lookup"><span data-stu-id="f3310-137">Binning</span></span>

<span data-ttu-id="f3310-138">[Binning](https://en.wikipedia.org/wiki/Data_binning) konwertuje wartości ciągłe na dyskretną reprezentację danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="f3310-138">[Binning](https://en.wikipedia.org/wiki/Data_binning) converts continuous values into a discrete representation of the input.</span></span> <span data-ttu-id="f3310-139">Załóżmy na przykład, że jedną z funkcji jest wiek.</span><span class="sxs-lookup"><span data-stu-id="f3310-139">For example, suppose one of your features is age.</span></span> <span data-ttu-id="f3310-140">Zamiast używać rzeczywistej wartości wieku, binning tworzy zakresy dla tej wartości.</span><span class="sxs-lookup"><span data-stu-id="f3310-140">Instead of using the actual age value,  binning creates ranges for that value.</span></span> <span data-ttu-id="f3310-141">0-18 może być jeden pojemnik, inny może być 19-35 i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="f3310-141">0-18 could be one bin, another could be 19-35 and so on.</span></span>

<span data-ttu-id="f3310-142">Weź następujące dane wejściowe i [`IDataView`](xref:Microsoft.ML.IDataView) załaduj je do tzw: `data`</span><span class="sxs-lookup"><span data-stu-id="f3310-142">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="f3310-143">Normalizuj dane do [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A) pojemników przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="f3310-143">Normalize the data into bins using the [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A) method.</span></span> <span data-ttu-id="f3310-144">Parametr `maximumBinCount` umożliwia określenie liczby pojemników potrzebnych do sklasyfikowania danych.</span><span class="sxs-lookup"><span data-stu-id="f3310-144">The `maximumBinCount` parameter enables you to specify the number of bins needed to classify your data.</span></span> <span data-ttu-id="f3310-145">W tym przykładzie dane zostaną wprowadzone do dwóch pojemników.</span><span class="sxs-lookup"><span data-stu-id="f3310-145">In this example, data will be put into two bins.</span></span>

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

<span data-ttu-id="f3310-146">Wynik binningu tworzy granice `[0,200000,Infinity]`pojemnika .</span><span class="sxs-lookup"><span data-stu-id="f3310-146">The result of binning creates bin bounds of `[0,200000,Infinity]`.</span></span> <span data-ttu-id="f3310-147">Dlatego powstałe pojemniki `[0,1,1]` są, ponieważ pierwsza obserwacja jest między 0-200000, a pozostałe są większe niż 200000, ale mniej niż nieskończoność.</span><span class="sxs-lookup"><span data-stu-id="f3310-147">Therefore the resulting bins are `[0,1,1]` because the first observation is between 0-200000 and the others are greater than 200000 but less than infinity.</span></span>

## <a name="work-with-categorical-data"></a><span data-ttu-id="f3310-148">Praca z danymi kategorycznymi</span><span class="sxs-lookup"><span data-stu-id="f3310-148">Work with categorical data</span></span>

<span data-ttu-id="f3310-149">Jednym z najczęstszych typów danych są dane podzielone na kategorie.</span><span class="sxs-lookup"><span data-stu-id="f3310-149">One of the most common types of data is categorical data.</span></span> <span data-ttu-id="f3310-150">Dane kategoryczne mają skończoną liczbę kategorii.</span><span class="sxs-lookup"><span data-stu-id="f3310-150">Categorical data has a finite number of categories.</span></span> <span data-ttu-id="f3310-151">Na przykład stany USA lub lista typów zwierząt znalezionych w zestawie zdjęć.</span><span class="sxs-lookup"><span data-stu-id="f3310-151">For example, the states of the USA, or a list of the types of animals found in a set of pictures.</span></span> <span data-ttu-id="f3310-152">Niezależnie od tego, czy dane kategorii są operacjami, czy etykietami, muszą być mapowane na wartość liczbową, aby można je było użyć do wygenerowania modelu uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="f3310-152">Whether the categorical data are features or labels, they must be mapped onto a numerical value so they can be used to generate a machine learning model.</span></span> <span data-ttu-id="f3310-153">Istnieje wiele sposobów pracy z danymi kategorii w ML.NET, w zależności od problemu, który rozwiązujesz.</span><span class="sxs-lookup"><span data-stu-id="f3310-153">There are a number of ways of working with categorical data in ML.NET, depending on the problem you are solving.</span></span>

### <a name="key-value-mapping"></a><span data-ttu-id="f3310-154">Mapowanie wartości klucza</span><span class="sxs-lookup"><span data-stu-id="f3310-154">Key value mapping</span></span>

<span data-ttu-id="f3310-155">W ML.NET klucz jest wartością całkowitą reprezentującą kategorię.</span><span class="sxs-lookup"><span data-stu-id="f3310-155">In ML.NET, a key is an integer value that represents a category.</span></span> <span data-ttu-id="f3310-156">Mapowanie wartości klucza jest najczęściej używane do mapowania etykiet ciągów do unikatowych wartości całkowitych dla szkolenia, a następnie z powrotem do ich wartości ciągów, gdy model jest używany do przewidywania.</span><span class="sxs-lookup"><span data-stu-id="f3310-156">Key value mapping is most often used to map string labels into unique integer values for training, then back to their string values when the model is used to make a prediction.</span></span>

<span data-ttu-id="f3310-157">Przekształcenia używane do wykonywania mapowania wartości klucza są [MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) i [MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A).</span><span class="sxs-lookup"><span data-stu-id="f3310-157">The transforms used to perform key value mapping are [MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) and [MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A).</span></span>

<span data-ttu-id="f3310-158">`MapValueToKey`dodaje słownik mapowania w modelu, dzięki `MapKeyToValue` czemu można wykonać odwrotną transformację podczas przewidywania.</span><span class="sxs-lookup"><span data-stu-id="f3310-158">`MapValueToKey` adds a dictionary of mappings in the model, so that `MapKeyToValue` can perform the reverse transform when making a prediction.</span></span>

### <a name="one-hot-encoding"></a><span data-ttu-id="f3310-159">Jedno gorące kodowanie</span><span class="sxs-lookup"><span data-stu-id="f3310-159">One hot encoding</span></span>

<span data-ttu-id="f3310-160">Jedno kodowanie gorące przyjmuje skończony zestaw wartości i mapuje je na liczby `1` całkowite, których reprezentacja binarna ma jedną wartość w unikatowych pozycjach w ciągu.</span><span class="sxs-lookup"><span data-stu-id="f3310-160">One hot encoding takes a finite set of values and maps them onto integers whose binary representation has a single `1` value in unique positions in the string.</span></span> <span data-ttu-id="f3310-161">Jedno gorące kodowanie może być najlepszym wyborem, jeśli nie ma niejawnej kolejności danych kategorii.</span><span class="sxs-lookup"><span data-stu-id="f3310-161">One hot encoding can be the best choice if there is no implicit ordering of the categorical data.</span></span> <span data-ttu-id="f3310-162">W poniższej tabeli przedstawiono przykład z kodami pocztowymi jako wartościami surowymi.</span><span class="sxs-lookup"><span data-stu-id="f3310-162">The following table shows an example with zip codes as raw values.</span></span>

|<span data-ttu-id="f3310-163">Wartość pierwotna</span><span class="sxs-lookup"><span data-stu-id="f3310-163">Raw value</span></span>|<span data-ttu-id="f3310-164">Jedna zakodowana wartość zakodowana na gorąco</span><span class="sxs-lookup"><span data-stu-id="f3310-164">One hot encoded value</span></span>|
|---------|---------------------|
|<span data-ttu-id="f3310-165">98052</span><span class="sxs-lookup"><span data-stu-id="f3310-165">98052</span></span>|<span data-ttu-id="f3310-166">00...01</span><span class="sxs-lookup"><span data-stu-id="f3310-166">00...01</span></span>|
|<span data-ttu-id="f3310-167">98100</span><span class="sxs-lookup"><span data-stu-id="f3310-167">98100</span></span>|<span data-ttu-id="f3310-168">00...10</span><span class="sxs-lookup"><span data-stu-id="f3310-168">00...10</span></span>|
|<span data-ttu-id="f3310-169">...</span><span class="sxs-lookup"><span data-stu-id="f3310-169">...</span></span>|<span data-ttu-id="f3310-170">...</span><span class="sxs-lookup"><span data-stu-id="f3310-170">...</span></span>|
|<span data-ttu-id="f3310-171">98109</span><span class="sxs-lookup"><span data-stu-id="f3310-171">98109</span></span>|<span data-ttu-id="f3310-172">10...00</span><span class="sxs-lookup"><span data-stu-id="f3310-172">10...00</span></span>|

<span data-ttu-id="f3310-173">Transformacja do konwersji danych kategorycznych na jednogorące numery zakodowane jest [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A).</span><span class="sxs-lookup"><span data-stu-id="f3310-173">The transform to convert categorical data to one-hot encoded numbers is [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A).</span></span>

### <a name="hashing"></a><span data-ttu-id="f3310-174">Mieszania</span><span class="sxs-lookup"><span data-stu-id="f3310-174">Hashing</span></span>

<span data-ttu-id="f3310-175">Haszowanie to kolejny sposób konwertowania danych kategorycznie na liczby.</span><span class="sxs-lookup"><span data-stu-id="f3310-175">Hashing is another way to convert categorical data to numbers.</span></span> <span data-ttu-id="f3310-176">Funkcja mieszania mapuje dane o dowolnym rozmiarze (na przykład ciąg tekstu) na liczbę o stałym zakresie.</span><span class="sxs-lookup"><span data-stu-id="f3310-176">A hash function maps data of an arbitrary size (a string of text for example) onto a number with a fixed range.</span></span> <span data-ttu-id="f3310-177">Haszowanie może być szybkim i efektywnym w przestrzeni sposobem wektorowania obiektów.</span><span class="sxs-lookup"><span data-stu-id="f3310-177">Hashing can be a fast and space-efficient way of vectorizing features.</span></span> <span data-ttu-id="f3310-178">Godnym uwagi przykładem mieszania w uczeniu maszynowym jest filtrowanie spamu e-mail, w którym zamiast utrzymywać słownik znanych słów, każde słowo w wiadomości e-mail jest haszowane i dodawane do dużego wektora funkcji.</span><span class="sxs-lookup"><span data-stu-id="f3310-178">One notable example of hashing in machine learning is email spam filtering where, instead of maintaining a dictionary of known words, every word in the email is hashed and added to a large feature vector.</span></span> <span data-ttu-id="f3310-179">Używanie mieszania w ten sposób pozwala uniknąć problemu złośliwego filtrowania spamu przez używanie słów, które nie znajdują się w słowniku.</span><span class="sxs-lookup"><span data-stu-id="f3310-179">Using hashing in this way avoids the problem of malicious spam filtering circumvention by the use of words that are not in the dictionary.</span></span>

<span data-ttu-id="f3310-180">ML.NET umożliwia transformację [mieszania](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) w celu wykonania mieszania tekstu, dat i danych liczbowych.</span><span class="sxs-lookup"><span data-stu-id="f3310-180">ML.NET provides [Hash](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) transform to perform hashing on text, dates, and numerical data.</span></span> <span data-ttu-id="f3310-181">Podobnie jak mapowanie klucza wartości, wyjścia transformacji mieszania są typami kluczy.</span><span class="sxs-lookup"><span data-stu-id="f3310-181">Like value key mapping, the outputs of the hash transform are key types.</span></span>

## <a name="work-with-text-data"></a><span data-ttu-id="f3310-182">Praca z danymi tekstowymi</span><span class="sxs-lookup"><span data-stu-id="f3310-182">Work with text data</span></span>

<span data-ttu-id="f3310-183">Podobnie jak dane kategoryczne, dane tekstowe muszą zostać przekształcone w funkcje liczbowe przed użyciem go do utworzenia modelu uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="f3310-183">Like categorical data, text data needs to be transformed into numerical features before using it to build a machine learning model.</span></span> <span data-ttu-id="f3310-184">Odwiedź [stronę przekształceń,](../resources/transforms.md) aby uzyskać bardziej szczegółową listę i opis przekształceń tekstu.</span><span class="sxs-lookup"><span data-stu-id="f3310-184">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of text transforms.</span></span>

<span data-ttu-id="f3310-185">Korzystanie z danych, takich jak dane [`IDataView`](xref:Microsoft.ML.IDataView)poniżej, który został załadowany do :</span><span class="sxs-lookup"><span data-stu-id="f3310-185">Using data like the data below that has been loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="f3310-186">ML.NET zapewnia [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) transformację, która przyjmuje wartość ciągu tekstu i tworzy zestaw funkcji z tekstu, stosując serię pojedynczych przekształceń.</span><span class="sxs-lookup"><span data-stu-id="f3310-186">ML.NET provides the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) transform that takes a text's string value and creates a set of features from the text, by applying a series of individual transforms.</span></span>

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

<span data-ttu-id="f3310-187">Wynikowa transformacja konwertuje `Description` wartości tekstowe w kolumnie na wektor numeryczny, który wygląda podobnie do danych wyjściowych poniżej:</span><span class="sxs-lookup"><span data-stu-id="f3310-187">The resulting transform converts the text values in the `Description` column to a numerical vector that looks similar to the output below:</span></span>

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

<span data-ttu-id="f3310-188">Przekształcenia, które tworzą `FeaturizeText` mogą być również stosowane indywidualnie dla ściślejszej kontroli ziarna nad generowaniem funkcji.</span><span class="sxs-lookup"><span data-stu-id="f3310-188">The transforms that make up `FeaturizeText` can also be applied individually for finer grain control over feature generation.</span></span>

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

<span data-ttu-id="f3310-189">`textEstimator`zawiera podzbiór operacji wykonywanych [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) przez metodę.</span><span class="sxs-lookup"><span data-stu-id="f3310-189">`textEstimator` contains a subset of operations performed by the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) method.</span></span> <span data-ttu-id="f3310-190">Zaletą bardziej złożonego potoku jest kontrola i widoczność przekształceń stosowanych do danych.</span><span class="sxs-lookup"><span data-stu-id="f3310-190">The benefit of a more complex pipeline is control and visibility over the transformations applied to the data.</span></span>

<span data-ttu-id="f3310-191">Na przykładzie pierwszego wpisu przedstawiono szczegółowy opis wyników opracowanych przez kroki `textEstimator`transformacji zdefiniowane przez:</span><span class="sxs-lookup"><span data-stu-id="f3310-191">Using the first entry as an example, the following is a detailed description of the results produced by the transformation steps defined by `textEstimator`:</span></span>

<span data-ttu-id="f3310-192">**Oryginalny tekst: Jest to dobry produkt**</span><span class="sxs-lookup"><span data-stu-id="f3310-192">**Original Text: This is a good product**</span></span>

|<span data-ttu-id="f3310-193">Przekształcanie</span><span class="sxs-lookup"><span data-stu-id="f3310-193">Transform</span></span> | <span data-ttu-id="f3310-194">Opis</span><span class="sxs-lookup"><span data-stu-id="f3310-194">Description</span></span> | <span data-ttu-id="f3310-195">Wynik</span><span class="sxs-lookup"><span data-stu-id="f3310-195">Result</span></span>
|--|--|--|
|<span data-ttu-id="f3310-196">1. NormalizujTekst</span><span class="sxs-lookup"><span data-stu-id="f3310-196">1. NormalizeText</span></span> | <span data-ttu-id="f3310-197">Domyślnie konwertuje wszystkie litery na małe litery</span><span class="sxs-lookup"><span data-stu-id="f3310-197">Converts all letters to lowercase by default</span></span> | <span data-ttu-id="f3310-198">jest to dobry produkt</span><span class="sxs-lookup"><span data-stu-id="f3310-198">this is a good product</span></span>
|<span data-ttu-id="f3310-199">2. TokenizeWords</span><span class="sxs-lookup"><span data-stu-id="f3310-199">2. TokenizeWords</span></span> | <span data-ttu-id="f3310-200">Dzieli ciąg na poszczególne wyrazy</span><span class="sxs-lookup"><span data-stu-id="f3310-200">Splits string into individual words</span></span> | <span data-ttu-id="f3310-201">["to","jest","a",,"dobry",produkt"]</span><span class="sxs-lookup"><span data-stu-id="f3310-201">["this","is","a","good","product"]</span></span>
|<span data-ttu-id="f3310-202">3. UsuńDefaultStopWords</span><span class="sxs-lookup"><span data-stu-id="f3310-202">3. RemoveDefaultStopWords</span></span> | <span data-ttu-id="f3310-203">Usuwa stopwords jak *jest* *i*.</span><span class="sxs-lookup"><span data-stu-id="f3310-203">Removes stopwords like *is* and *a*.</span></span> | <span data-ttu-id="f3310-204">["dobry","produkt"]</span><span class="sxs-lookup"><span data-stu-id="f3310-204">["good","product"]</span></span>
|<span data-ttu-id="f3310-205">4. MapValueToKey</span><span class="sxs-lookup"><span data-stu-id="f3310-205">4. MapValueToKey</span></span> | <span data-ttu-id="f3310-206">Mapuje wartości na klucze (kategorie) na podstawie danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="f3310-206">Maps the values to keys (categories) based on the input data</span></span> |  <span data-ttu-id="f3310-207">[1,2]</span><span class="sxs-lookup"><span data-stu-id="f3310-207">[1,2]</span></span>
|<span data-ttu-id="f3310-208">5. ProduceNGrams</span><span class="sxs-lookup"><span data-stu-id="f3310-208">5. ProduceNGrams</span></span> | <span data-ttu-id="f3310-209">Przekształca tekst w sekwencję kolejnych słów</span><span class="sxs-lookup"><span data-stu-id="f3310-209">Transforms text into sequence of consecutive words</span></span> | <span data-ttu-id="f3310-210">[1,1,1,0,0]</span><span class="sxs-lookup"><span data-stu-id="f3310-210">[1,1,1,0,0]</span></span>
|<span data-ttu-id="f3310-211">6. Normalizuj Normę Lp</span><span class="sxs-lookup"><span data-stu-id="f3310-211">6. NormalizeLpNorm</span></span> | <span data-ttu-id="f3310-212">Skaluj dane wejściowe według ich lp-norm</span><span class="sxs-lookup"><span data-stu-id="f3310-212">Scale inputs by their lp-norm</span></span> | <span data-ttu-id="f3310-213">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span><span class="sxs-lookup"><span data-stu-id="f3310-213">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span></span>
