---
title: Przygotowywanie danych do kompilowania modelu
description: Dowiedz się, jak używać transformacji w programie ML.NET, aby manipulować i przygotowywać dane do dodatkowego przetwarzania lub kompilowania modeli.
author: luisquintanilla
ms.author: luquinta
ms.date: 01/29/2020
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 12f933253af9ea519d711c20227fe075fed003de
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452990"
---
# <a name="prepare-data-for-building-a-model"></a><span data-ttu-id="342bc-103">Przygotowywanie danych do kompilowania modelu</span><span class="sxs-lookup"><span data-stu-id="342bc-103">Prepare data for building a model</span></span>

<span data-ttu-id="342bc-104">Dowiedz się, w jaki sposób używać ML.NET do przygotowywania danych do dodatkowego przetwarzania lub tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="342bc-104">Learn how to use ML.NET to prepare data for additional processing or building a model.</span></span>

<span data-ttu-id="342bc-105">Dane często są nieoczyszczone i rozrzedzone.</span><span class="sxs-lookup"><span data-stu-id="342bc-105">Data is often unclean and sparse.</span></span> <span data-ttu-id="342bc-106">Algorytmy uczenia maszynowego ML.NET oczekują wejścia lub funkcje, które mogą znajdować się w pojedynczym wektorze liczbowym.</span><span class="sxs-lookup"><span data-stu-id="342bc-106">ML.NET machine learning algorithms expect input or features to be in a single numerical vector.</span></span> <span data-ttu-id="342bc-107">Podobnie, wartość do prognozowania (etykieta), szczególnie w przypadku kategorii danych, musi być zakodowana.</span><span class="sxs-lookup"><span data-stu-id="342bc-107">Similarly, the value to predict (label), especially when it's categorical data, has to be encoded.</span></span> <span data-ttu-id="342bc-108">W związku z tym jednym z celów przygotowywania danych jest uzyskanie danych do formatu oczekiwanego przez algorytmy ML.NET.</span><span class="sxs-lookup"><span data-stu-id="342bc-108">Therefore one of the goals of data preparation is to get the data into the format expected by ML.NET algorithms.</span></span>

## <a name="filter-data"></a><span data-ttu-id="342bc-109">Filtrowanie danych</span><span class="sxs-lookup"><span data-stu-id="342bc-109">Filter data</span></span>

<span data-ttu-id="342bc-110">Czasami nie wszystkie dane w zestawie danych są związane z analizą.</span><span class="sxs-lookup"><span data-stu-id="342bc-110">Sometimes, not all data in a dataset is relevant for analysis.</span></span> <span data-ttu-id="342bc-111">Podejście do usuwania nieistotnych danych jest filtrowanie.</span><span class="sxs-lookup"><span data-stu-id="342bc-111">An approach to remove irrelevant data is filtering.</span></span> <span data-ttu-id="342bc-112">[`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) zawiera zestaw operacji filtrowania, które przyjmują [`IDataView`](xref:Microsoft.ML.IDataView) zawierające wszystkie dane i zwracają [IDataView](xref:Microsoft.ML.IDataView) zawierające tylko interesujące punkty danych.</span><span class="sxs-lookup"><span data-stu-id="342bc-112">The [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) contains a set of filter operations that take in an [`IDataView`](xref:Microsoft.ML.IDataView) containing all of the data and return an [IDataView](xref:Microsoft.ML.IDataView) containing only the data points of interest.</span></span> <span data-ttu-id="342bc-113">Należy pamiętać, że ponieważ operacje filtrowania nie są [`IEstimator`](xref:Microsoft.ML.IEstimator%601) lub [`ITransformer`](xref:Microsoft.ML.ITransformer) takie jak te w [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), nie można ich uwzględnić w ramach potoku przygotowywania danych [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) lub [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) .</span><span class="sxs-lookup"><span data-stu-id="342bc-113">It's important to note that because filter operations are not an [`IEstimator`](xref:Microsoft.ML.IEstimator%601) or [`ITransformer`](xref:Microsoft.ML.ITransformer) like those in the [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), they cannot be included as part of an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) or [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) data preparation pipeline.</span></span>

<span data-ttu-id="342bc-114">Wykonaj następujące dane wejściowe i załaduj je do [`IDataView`](xref:Microsoft.ML.IDataView) o nazwie `data`:</span><span class="sxs-lookup"><span data-stu-id="342bc-114">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="342bc-115">Aby filtrować dane na podstawie wartości kolumny, użyj metody [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) .</span><span class="sxs-lookup"><span data-stu-id="342bc-115">To filter data based on the value of a column, use the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) method.</span></span>

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

<span data-ttu-id="342bc-116">Powyższy przykład pobiera wiersze w zestawie danych z ceną z zakresu od 200000 do 1000000.</span><span class="sxs-lookup"><span data-stu-id="342bc-116">The sample above takes rows in the dataset with a price between 200000 and 1000000.</span></span> <span data-ttu-id="342bc-117">Wynikiem zastosowania tego filtru będzie zwrócenie tylko ostatnich dwóch wierszy danych i wykluczenie pierwszego wiersza, ponieważ jego cena jest 100000, a nie pomiędzy określonym zakresem.</span><span class="sxs-lookup"><span data-stu-id="342bc-117">The result of applying this filter would return only the last two rows in the data and exclude the first row because its price is 100000 and not between the specified range.</span></span>

## <a name="replace-missing-values"></a><span data-ttu-id="342bc-118">Zamień brakujące wartości</span><span class="sxs-lookup"><span data-stu-id="342bc-118">Replace missing values</span></span>

<span data-ttu-id="342bc-119">Brakujące wartości są typowym wystąpieniem w zestawach danych.</span><span class="sxs-lookup"><span data-stu-id="342bc-119">Missing values are a common occurrence in datasets.</span></span> <span data-ttu-id="342bc-120">Jednym z metod postępowania z brakującymi wartościami jest zastąpienie ich wartością domyślną dla danego typu, jeśli jakakolwiek lub inna wartość istotna, taka jak wartość średnia w danych.</span><span class="sxs-lookup"><span data-stu-id="342bc-120">One approach to dealing with missing values is to replace them with the default value for the given type if any or another meaningful value such as the mean value in the data.</span></span>

<span data-ttu-id="342bc-121">Wykonaj następujące dane wejściowe i załaduj je do [`IDataView`](xref:Microsoft.ML.IDataView) o nazwie `data`:</span><span class="sxs-lookup"><span data-stu-id="342bc-121">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="342bc-122">Zwróć uwagę, że ostatni element na naszej liście ma brakującą wartość dla `Price`.</span><span class="sxs-lookup"><span data-stu-id="342bc-122">Notice that the last element in our list has a missing value for `Price`.</span></span> <span data-ttu-id="342bc-123">Aby zastąpić brakujące wartości w kolumnie `Price`, użyj metody [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) , aby wypełnić tę brakującą wartość.</span><span class="sxs-lookup"><span data-stu-id="342bc-123">To replace the missing values in the `Price` column, use the [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) method to fill in that missing value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="342bc-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) działa tylko z danymi liczbowymi.</span><span class="sxs-lookup"><span data-stu-id="342bc-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) only works with numerical data.</span></span>

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

<span data-ttu-id="342bc-125">ML.NET obsługuje różne [tryby wymiany](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span><span class="sxs-lookup"><span data-stu-id="342bc-125">ML.NET supports various [replacement modes](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span></span> <span data-ttu-id="342bc-126">Powyższy przykład używa trybu wymiany `Mean`, który wypełnia brakującą wartość wartością średnią tej kolumny.</span><span class="sxs-lookup"><span data-stu-id="342bc-126">The sample above uses the `Mean` replacement mode, which fills in the missing value with that column's average value.</span></span> <span data-ttu-id="342bc-127">Wynikiem zamiany jest wypełnienie właściwości `Price` ostatniego elementu w danych o 200 000, ponieważ jest to średnia z 100 000 i 300 000.</span><span class="sxs-lookup"><span data-stu-id="342bc-127">The replacement 's result fills in the `Price` property for the last element in our data with 200,000 since it's the average of 100,000 and 300,000.</span></span>

## <a name="use-normalizers"></a><span data-ttu-id="342bc-128">Korzystanie z normalizacji</span><span class="sxs-lookup"><span data-stu-id="342bc-128">Use normalizers</span></span>

<span data-ttu-id="342bc-129">[Normalizacja](https://en.wikipedia.org/wiki/Feature_scaling) to technika przetwarzania wstępnego danych służąca do skalowania funkcji, które mają być w tym samym zakresie, zwykle między 0 i 1, dzięki czemu mogą być bardziej precyzyjnie przetwarzane przez algorytm uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="342bc-129">[Normalization](https://en.wikipedia.org/wiki/Feature_scaling) is a data pre-processing technique used to scale features to be in the same range, usually between 0 and 1, so that they can be more accurately processed by a machine learning algorithm.</span></span> <span data-ttu-id="342bc-130">Na przykład zakresy dla wieku i przychodu różnią się znacznie od wieku w zakresie 0-100 i przychodów ogólnie w zakresie od zera do tysięcy.</span><span class="sxs-lookup"><span data-stu-id="342bc-130">For example, the ranges for age and income vary significantly with age generally being in the range of 0-100 and income generally being in the range of zero to thousands.</span></span> <span data-ttu-id="342bc-131">Odwiedź [stronę przekształcenia](../resources/transforms.md) , aby uzyskać bardziej szczegółową listę i opis transformacji normalizacji.</span><span class="sxs-lookup"><span data-stu-id="342bc-131">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of normalization transforms.</span></span>

### <a name="min-max-normalization"></a><span data-ttu-id="342bc-132">Minimalna-Maksymalna normalizacja</span><span class="sxs-lookup"><span data-stu-id="342bc-132">Min-Max normalization</span></span>

<span data-ttu-id="342bc-133">Wykonaj następujące dane wejściowe i załaduj je do [`IDataView`](xref:Microsoft.ML.IDataView) o nazwie `data`:</span><span class="sxs-lookup"><span data-stu-id="342bc-133">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="342bc-134">Normalizację można zastosować do kolumn z pojedynczą wartością liczbową, a także wektorami.</span><span class="sxs-lookup"><span data-stu-id="342bc-134">Normalization can be applied to columns with single numerical values as well as vectors.</span></span> <span data-ttu-id="342bc-135">Normalizowanie danych w kolumnie `Price` przy użyciu metody [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) z zastosowaniem minimalnej maksymalnej normalizacji.</span><span class="sxs-lookup"><span data-stu-id="342bc-135">Normalize the data in the `Price` column using min-max normalization with the [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) method.</span></span>

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

<span data-ttu-id="342bc-136">Pierwotne wartości cen `[200000,100000]` są konwertowane na `[ 1, 0.5 ]` przy użyciu formuły normalizacji `MinMax`, która generuje wartości wyjściowe z zakresu 0-1.</span><span class="sxs-lookup"><span data-stu-id="342bc-136">The original price values `[200000,100000]` are converted to `[ 1, 0.5 ]` using the `MinMax` normalization formula that generates output values in the range of 0-1.</span></span>

### <a name="binning"></a><span data-ttu-id="342bc-137">Pakowania</span><span class="sxs-lookup"><span data-stu-id="342bc-137">Binning</span></span>

<span data-ttu-id="342bc-138">[Pakowania](https://en.wikipedia.org/wiki/Data_binning) konwertuje ciągłe wartości na dyskretną reprezentację danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="342bc-138">[Binning](https://en.wikipedia.org/wiki/Data_binning) converts continuous values into a discrete representation of the input.</span></span> <span data-ttu-id="342bc-139">Załóżmy na przykład, że jedna z Twoich funkcji jest w wieku.</span><span class="sxs-lookup"><span data-stu-id="342bc-139">For example, suppose one of your features is age.</span></span> <span data-ttu-id="342bc-140">Zamiast korzystać z rzeczywistej wartości wieku, pakowania tworzy zakresy dla tej wartości.</span><span class="sxs-lookup"><span data-stu-id="342bc-140">Instead of using the actual age value,  binning creates ranges for that value.</span></span> <span data-ttu-id="342bc-141">0-18 może być jednym pojemnikem, innym może być 19-35 i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="342bc-141">0-18 could be one bin, another could be 19-35 and so on.</span></span>

<span data-ttu-id="342bc-142">Wykonaj następujące dane wejściowe i załaduj je do [`IDataView`](xref:Microsoft.ML.IDataView) o nazwie `data`:</span><span class="sxs-lookup"><span data-stu-id="342bc-142">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="342bc-143">Normalizowanie danych do pojemników przy użyciu metody [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A) .</span><span class="sxs-lookup"><span data-stu-id="342bc-143">Normalize the data into bins using the [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A) method.</span></span> <span data-ttu-id="342bc-144">`maximumBinCount` parametr umożliwia określenie liczby pojemników potrzebnych do klasyfikowania danych.</span><span class="sxs-lookup"><span data-stu-id="342bc-144">The `maximumBinCount` parameter enables you to specify the number of bins needed to classify your data.</span></span> <span data-ttu-id="342bc-145">W tym przykładzie dane będą umieszczane w dwóch pojemnikach.</span><span class="sxs-lookup"><span data-stu-id="342bc-145">In this example, data will be put into two bins.</span></span>

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

<span data-ttu-id="342bc-146">Wynik pakowania tworzy granice bin `[0,200000,Infinity]`.</span><span class="sxs-lookup"><span data-stu-id="342bc-146">The result of binning creates bin bounds of `[0,200000,Infinity]`.</span></span> <span data-ttu-id="342bc-147">W związku z tym te pojemniki są `[0,1,1]`, ponieważ pierwsza obserwacja wynosi od 0-200000, a pozostałe są większe niż 200000, ale mniejsze niż nieskończoność.</span><span class="sxs-lookup"><span data-stu-id="342bc-147">Therefore the resulting bins are `[0,1,1]` because the first observation is between 0-200000 and the others are greater than 200000 but less than infinity.</span></span>

## <a name="work-with-categorical-data"></a><span data-ttu-id="342bc-148">Pracuj z danymi kategorii</span><span class="sxs-lookup"><span data-stu-id="342bc-148">Work with categorical data</span></span>

<span data-ttu-id="342bc-149">Jednym z najpopularniejszych typów danych jest kategorii danych.</span><span class="sxs-lookup"><span data-stu-id="342bc-149">One of the most common types of data is categorical data.</span></span> <span data-ttu-id="342bc-150">Dane kategorii mają skończoną liczbę kategorii.</span><span class="sxs-lookup"><span data-stu-id="342bc-150">Categorical data has a finite number of categories.</span></span> <span data-ttu-id="342bc-151">Na przykład stany USA lub lista typów zwierząt znalezionych w zestawie obrazów.</span><span class="sxs-lookup"><span data-stu-id="342bc-151">For example, the states of the USA, or a list of the types of animals found in a set of pictures.</span></span> <span data-ttu-id="342bc-152">Niezależnie od tego, czy dane kategorii są funkcjami lub etykietami, muszą być mapowane na wartość liczbową, aby można było ich użyć do wygenerowania modelu uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="342bc-152">Whether the categorical data are features or labels, they must be mapped onto a numerical value so they can be used to generate a machine learning model.</span></span> <span data-ttu-id="342bc-153">Istnieje kilka sposobów pracy z danymi kategorii w ML.NET, w zależności od rozwiązywanego problemu.</span><span class="sxs-lookup"><span data-stu-id="342bc-153">There are a number of ways of working with categorical data in ML.NET, depending on the problem you are solving.</span></span>

### <a name="key-value-mapping"></a><span data-ttu-id="342bc-154">Mapowanie wartości klucza</span><span class="sxs-lookup"><span data-stu-id="342bc-154">Key value mapping</span></span>

<span data-ttu-id="342bc-155">W ML.NET klucz jest wartością całkowitą reprezentującą kategorię.</span><span class="sxs-lookup"><span data-stu-id="342bc-155">In ML.NET, a key is an integer value that represents a category.</span></span> <span data-ttu-id="342bc-156">Mapowanie wartości klucza jest najczęściej używane do mapowania etykiet ciągów na unikatowe wartości całkowite dla szkolenia, a następnie z powrotem do ich wartości ciągów, gdy model jest używany do prognozowania.</span><span class="sxs-lookup"><span data-stu-id="342bc-156">Key value mapping is most often used to map string labels into unique integer values for training, then back to their string values when the model is used to make a prediction.</span></span>

<span data-ttu-id="342bc-157">Transformacje używane do przeprowadzenia mapowania wartości klucza to [MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) i [MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A).</span><span class="sxs-lookup"><span data-stu-id="342bc-157">The transforms used to perform key value mapping are [MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) and [MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A).</span></span>

<span data-ttu-id="342bc-158">`MapValueToKey` dodaje słownik mapowań w modelu, dzięki czemu `MapKeyToValue` mogą wykonywać przekształcenia odwrotne podczas tworzenia prognoz.</span><span class="sxs-lookup"><span data-stu-id="342bc-158">`MapValueToKey` adds a dictionary of mappings in the model, so that `MapKeyToValue` can perform the reverse transform when making a prediction.</span></span>

### <a name="one-hot-encoding"></a><span data-ttu-id="342bc-159">Jedno kodowanie gorąca</span><span class="sxs-lookup"><span data-stu-id="342bc-159">One hot encoding</span></span>

<span data-ttu-id="342bc-160">Jedno kodowanie gorąca przyjmuje skończoną zbiór wartości i mapuje je na liczby całkowite, których reprezentacja binarna ma jedną `1` wartość w unikatowych pozycjach w ciągu.</span><span class="sxs-lookup"><span data-stu-id="342bc-160">One hot encoding takes a finite set of values and maps them onto integers whose binary representation has a single `1` value in unique positions in the string.</span></span> <span data-ttu-id="342bc-161">Jedno kodowanie gorąca może być najlepszym wyborem, jeśli nie istnieje niejawna kolejność danych kategorii.</span><span class="sxs-lookup"><span data-stu-id="342bc-161">One hot encoding can be the best choice if there is no implicit ordering of the categorical data.</span></span> <span data-ttu-id="342bc-162">W poniższej tabeli przedstawiono przykład z kodami zip jako pierwotne wartości.</span><span class="sxs-lookup"><span data-stu-id="342bc-162">The following table shows an example with zip codes as raw values.</span></span>

|<span data-ttu-id="342bc-163">Wartość pierwotna</span><span class="sxs-lookup"><span data-stu-id="342bc-163">Raw value</span></span>|<span data-ttu-id="342bc-164">Jedna zakodowana wartość</span><span class="sxs-lookup"><span data-stu-id="342bc-164">One hot encoded value</span></span>|
|---------|---------------------|
|<span data-ttu-id="342bc-165">98052</span><span class="sxs-lookup"><span data-stu-id="342bc-165">98052</span></span>|<span data-ttu-id="342bc-166">00... 01</span><span class="sxs-lookup"><span data-stu-id="342bc-166">00...01</span></span>|
|<span data-ttu-id="342bc-167">98100</span><span class="sxs-lookup"><span data-stu-id="342bc-167">98100</span></span>|<span data-ttu-id="342bc-168">00... 10</span><span class="sxs-lookup"><span data-stu-id="342bc-168">00...10</span></span>|
|<span data-ttu-id="342bc-169">Przyciski ...</span><span class="sxs-lookup"><span data-stu-id="342bc-169">...</span></span>|<span data-ttu-id="342bc-170">Przyciski ...</span><span class="sxs-lookup"><span data-stu-id="342bc-170">...</span></span>|
|<span data-ttu-id="342bc-171">98109</span><span class="sxs-lookup"><span data-stu-id="342bc-171">98109</span></span>|<span data-ttu-id="342bc-172">10... 00</span><span class="sxs-lookup"><span data-stu-id="342bc-172">10...00</span></span>|

<span data-ttu-id="342bc-173">Przekształcenie do konwersji danych kategorii na jednokodowane zakodowane liczby jest [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A).</span><span class="sxs-lookup"><span data-stu-id="342bc-173">The transform to convert categorical data to one-hot encoded numbers is [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A).</span></span>

### <a name="hashing"></a><span data-ttu-id="342bc-174">Tworzenia skrótów</span><span class="sxs-lookup"><span data-stu-id="342bc-174">Hashing</span></span>

<span data-ttu-id="342bc-175">Mieszanie jest innym sposobem konwersji kategorii danych na liczby.</span><span class="sxs-lookup"><span data-stu-id="342bc-175">Hashing is another way to convert categorical data to numbers.</span></span> <span data-ttu-id="342bc-176">Funkcja skrótu mapuje dane dowolnego rozmiaru (na przykład ciąg tekstowy) na liczbę z ustalonym zakresem.</span><span class="sxs-lookup"><span data-stu-id="342bc-176">A hash function maps data of an arbitrary size (a string of text for example) onto a number with a fixed range.</span></span> <span data-ttu-id="342bc-177">Mieszanie może być szybkim i wydajnym miejscem funkcji zrównoleglonej biblioteki pełniejszą.</span><span class="sxs-lookup"><span data-stu-id="342bc-177">Hashing can be a fast and space-efficient way of vectorizing features.</span></span> <span data-ttu-id="342bc-178">Jednym z przykładów tworzenia skrótów w usłudze Machine Learning jest filtrowanie spamu poczty e-mail, gdzie zamiast obsługi słownika znanych wyrazów każdy wyraz w wiadomości e-mail zostaje zmieszany i dodany do dużego wektora funkcji.</span><span class="sxs-lookup"><span data-stu-id="342bc-178">One notable example of hashing in machine learning is email spam filtering where, instead of maintaining a dictionary of known words, every word in the email is hashed and added to a large feature vector.</span></span> <span data-ttu-id="342bc-179">Użycie mieszania w ten sposób pozwala uniknąć problemu złośliwego filtrowania spamu przez użycie wyrazów, które nie znajdują się w słowniku.</span><span class="sxs-lookup"><span data-stu-id="342bc-179">Using hashing in this way avoids the problem of malicious spam filtering circumvention by the use of words that are not in the dictionary.</span></span>

<span data-ttu-id="342bc-180">ML.NET zapewnia transformacja [skrótu](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) do wykonywania skrótów dla danych tekstowych, dat i liczbowych.</span><span class="sxs-lookup"><span data-stu-id="342bc-180">ML.NET provides [Hash](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) transform to perform hashing on text, dates, and numerical data.</span></span> <span data-ttu-id="342bc-181">Podobnie jak mapowanie klucza wartości, dane wyjściowe przekształcenia mieszania są typami kluczy.</span><span class="sxs-lookup"><span data-stu-id="342bc-181">Like value key mapping, the outputs of the hash transform are key types.</span></span>

## <a name="work-with-text-data"></a><span data-ttu-id="342bc-182">Pracuj z danymi tekstowymi</span><span class="sxs-lookup"><span data-stu-id="342bc-182">Work with text data</span></span>

<span data-ttu-id="342bc-183">Podobnie jak dane kategorii, dane tekstowe muszą zostać przekształcone w funkcje liczbowe przed użyciem go do kompilowania modelu uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="342bc-183">Like categorical data, text data needs to be transformed into numerical features before using it to build a machine learning model.</span></span> <span data-ttu-id="342bc-184">Odwiedź [stronę przekształcenia](../resources/transforms.md) , aby uzyskać bardziej szczegółową listę i opis przekształceń tekstu.</span><span class="sxs-lookup"><span data-stu-id="342bc-184">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of text transforms.</span></span>

<span data-ttu-id="342bc-185">Używając danych, takich jak poniższe dane, które zostały załadowane do [`IDataView`](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="342bc-185">Using data like the data below that has been loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="342bc-186">ML.NET zapewnia transformację [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) , która pobiera wartość ciągu tekstu i tworzy zestaw funkcji z tekstu, stosując serię poszczególnych transformacji.</span><span class="sxs-lookup"><span data-stu-id="342bc-186">ML.NET provides the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) transform that takes a text's string value and creates a set of features from the text, by applying a series of individual transforms.</span></span>

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

<span data-ttu-id="342bc-187">Wynikowe przekształcanie konwertuje wartości tekstowe w kolumnie `Description` na wektor liczbowy, który wygląda podobnie do danych wyjściowych poniżej:</span><span class="sxs-lookup"><span data-stu-id="342bc-187">The resulting transform converts the text values in the `Description` column to a numerical vector that looks similar to the output below:</span></span>

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

<span data-ttu-id="342bc-188">Transformacje, które składają się `FeaturizeText` można również zastosować osobno w celu dokładniejszej kontroli nad generowaniem funkcji.</span><span class="sxs-lookup"><span data-stu-id="342bc-188">The transforms that make up `FeaturizeText` can also be applied individually for finer grain control over feature generation.</span></span>

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

<span data-ttu-id="342bc-189">`textEstimator` zawiera podzestaw operacji wykonywanych przez metodę [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) .</span><span class="sxs-lookup"><span data-stu-id="342bc-189">`textEstimator` contains a subset of operations performed by the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) method.</span></span> <span data-ttu-id="342bc-190">Zaletą bardziej złożonej potoku jest kontrola i widoczność przekształceń zastosowanych do danych.</span><span class="sxs-lookup"><span data-stu-id="342bc-190">The benefit of a more complex pipeline is control and visibility over the transformations applied to the data.</span></span>

<span data-ttu-id="342bc-191">Przy użyciu pierwszego wpisu na przykład, poniżej przedstawiono szczegółowy opis wyników przedstawionych przez kroki transformacji zdefiniowane przez `textEstimator`:</span><span class="sxs-lookup"><span data-stu-id="342bc-191">Using the first entry as an example, the following is a detailed description of the results produced by the transformation steps defined by `textEstimator`:</span></span>

<span data-ttu-id="342bc-192">**Oryginalny tekst: jest to dobry produkt**</span><span class="sxs-lookup"><span data-stu-id="342bc-192">**Original Text: This is a good product**</span></span>

|<span data-ttu-id="342bc-193">Przekształcanie</span><span class="sxs-lookup"><span data-stu-id="342bc-193">Transform</span></span> | <span data-ttu-id="342bc-194">Opis</span><span class="sxs-lookup"><span data-stu-id="342bc-194">Description</span></span> | <span data-ttu-id="342bc-195">Wynik</span><span class="sxs-lookup"><span data-stu-id="342bc-195">Result</span></span>
|--|--|--|
|<span data-ttu-id="342bc-196">1. NormalizeText</span><span class="sxs-lookup"><span data-stu-id="342bc-196">1. NormalizeText</span></span> | <span data-ttu-id="342bc-197">Konwertuje domyślnie wszystkie litery na małe</span><span class="sxs-lookup"><span data-stu-id="342bc-197">Converts all letters to lowercase by default</span></span> | <span data-ttu-id="342bc-198">jest to dobry produkt</span><span class="sxs-lookup"><span data-stu-id="342bc-198">this is a good product</span></span>
|<span data-ttu-id="342bc-199">2. TokenizeWords</span><span class="sxs-lookup"><span data-stu-id="342bc-199">2. TokenizeWords</span></span> | <span data-ttu-id="342bc-200">Dzieli ciąg na pojedyncze wyrazy</span><span class="sxs-lookup"><span data-stu-id="342bc-200">Splits string into individual words</span></span> | <span data-ttu-id="342bc-201">["This", "is", "a", "dobry", "Product"]</span><span class="sxs-lookup"><span data-stu-id="342bc-201">["this","is","a","good","product"]</span></span>
|<span data-ttu-id="342bc-202">3. RemoveDefaultStopWords</span><span class="sxs-lookup"><span data-stu-id="342bc-202">3. RemoveDefaultStopWords</span></span> | <span data-ttu-id="342bc-203">Usuwa Stop-słowa, *takie* jak *i.*</span><span class="sxs-lookup"><span data-stu-id="342bc-203">Removes stopwords like *is* and *a*.</span></span> | <span data-ttu-id="342bc-204">["dobry", "produkt"]</span><span class="sxs-lookup"><span data-stu-id="342bc-204">["good","product"]</span></span>
|<span data-ttu-id="342bc-205">4. MapValueToKey</span><span class="sxs-lookup"><span data-stu-id="342bc-205">4. MapValueToKey</span></span> | <span data-ttu-id="342bc-206">Mapuje wartości na klucze (kategorie) w oparciu o dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="342bc-206">Maps the values to keys (categories) based on the input data</span></span> |  <span data-ttu-id="342bc-207">[1,2]</span><span class="sxs-lookup"><span data-stu-id="342bc-207">[1,2]</span></span>
|<span data-ttu-id="342bc-208">5. ProduceNGrams</span><span class="sxs-lookup"><span data-stu-id="342bc-208">5. ProduceNGrams</span></span> | <span data-ttu-id="342bc-209">Przekształca tekst w sekwencję kolejnych wyrazów</span><span class="sxs-lookup"><span data-stu-id="342bc-209">Transforms text into sequence of consecutive words</span></span> | <span data-ttu-id="342bc-210">[1,1,1,0,0]</span><span class="sxs-lookup"><span data-stu-id="342bc-210">[1,1,1,0,0]</span></span>
|<span data-ttu-id="342bc-211">6. NormalizeLpNorm</span><span class="sxs-lookup"><span data-stu-id="342bc-211">6. NormalizeLpNorm</span></span> | <span data-ttu-id="342bc-212">Skalowanie danych wejściowych według ich standardu LP</span><span class="sxs-lookup"><span data-stu-id="342bc-212">Scale inputs by their lp-norm</span></span> | <span data-ttu-id="342bc-213">[0,577350529, 0,577350529, 0,577350529, 0, 0]</span><span class="sxs-lookup"><span data-stu-id="342bc-213">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span></span>
