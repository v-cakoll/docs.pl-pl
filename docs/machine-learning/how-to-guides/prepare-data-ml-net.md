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
# <a name="prepare-data-for-building-a-model"></a><span data-ttu-id="98792-103">Przygotowywanie danych do kompilowania modelu</span><span class="sxs-lookup"><span data-stu-id="98792-103">Prepare data for building a model</span></span>

<span data-ttu-id="98792-104">Dowiedz się, w jaki sposób używać ML.NET do przygotowywania danych do dodatkowego przetwarzania lub tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="98792-104">Learn how to use ML.NET to prepare data for additional processing or building a model.</span></span>

<span data-ttu-id="98792-105">Dane często są nieoczyszczone i rozrzedzone.</span><span class="sxs-lookup"><span data-stu-id="98792-105">Data is often unclean and sparse.</span></span> <span data-ttu-id="98792-106">Algorytmy uczenia maszynowego ML.NET oczekują wejścia lub funkcje, które mogą znajdować się w pojedynczym wektorze liczbowym.</span><span class="sxs-lookup"><span data-stu-id="98792-106">ML.NET machine learning algorithms expect input or features to be in a single numerical vector.</span></span> <span data-ttu-id="98792-107">Podobnie, wartość do prognozowania (etykieta), szczególnie w przypadku kategorii danych, musi być zakodowana.</span><span class="sxs-lookup"><span data-stu-id="98792-107">Similarly, the value to predict (label), especially when it's categorical data, has to be encoded.</span></span> <span data-ttu-id="98792-108">W związku z tym jednym z celów przygotowywania danych jest uzyskanie danych do formatu oczekiwanego przez algorytmy ML.NET.</span><span class="sxs-lookup"><span data-stu-id="98792-108">Therefore one of the goals of data preparation is to get the data into the format expected by ML.NET algorithms.</span></span> 

## <a name="filter-data"></a><span data-ttu-id="98792-109">Filtrowanie danych</span><span class="sxs-lookup"><span data-stu-id="98792-109">Filter data</span></span>

<span data-ttu-id="98792-110">Czasami nie wszystkie dane w zestawie danych są związane z analizą.</span><span class="sxs-lookup"><span data-stu-id="98792-110">Sometimes, not all data in a dataset is relevant for analysis.</span></span> <span data-ttu-id="98792-111">Podejście do usuwania nieistotnych danych jest filtrowanie.</span><span class="sxs-lookup"><span data-stu-id="98792-111">An approach to remove irrelevant data is filtering.</span></span> <span data-ttu-id="98792-112">Zawiera zestaw operacji filtrowania, które przyjmują [`IDataView`](xref:Microsoft.ML.IDataView) wszystkie dane i zwracają [IDataView](xref:Microsoft.ML.IDataView) zawierające tylko interesujące punkty danych. [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog)</span><span class="sxs-lookup"><span data-stu-id="98792-112">The [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) contains a set of filter operations that take in an [`IDataView`](xref:Microsoft.ML.IDataView) containing all of the data and return an [IDataView](xref:Microsoft.ML.IDataView) containing only the data points of interest.</span></span> <span data-ttu-id="98792-113">Należy pamiętać, że [`IEstimator`](xref:Microsoft.ML.IEstimator%601) ponieważ operacje filtrowania nie są ani [`ITransformer`](xref:Microsoft.ML.ITransformer) takie jak te w programie [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), nie można [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) ich uwzględnić jako części potoku przygotowywania lub [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) przygotowania danych.</span><span class="sxs-lookup"><span data-stu-id="98792-113">It's important to note that because filter operations are not an [`IEstimator`](xref:Microsoft.ML.IEstimator%601) or [`ITransformer`](xref:Microsoft.ML.ITransformer) like those in the [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), they cannot be included as part of an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) or [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) data preparation pipeline.</span></span> 

<span data-ttu-id="98792-114">Użycie następujących danych wejściowych, które są ładowane do [`IDataView`](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="98792-114">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="98792-115">Aby filtrować dane na podstawie wartości kolumny, użyj [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) metody.</span><span class="sxs-lookup"><span data-stu-id="98792-115">To filter data based on the value of a column, use the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) method.</span></span>

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

<span data-ttu-id="98792-116">Powyższy przykład pobiera wiersze w zestawie danych z ceną z zakresu od 200000 do 1000000.</span><span class="sxs-lookup"><span data-stu-id="98792-116">The sample above takes rows in the dataset with a price between 200000 and 1000000.</span></span> <span data-ttu-id="98792-117">Wynikiem zastosowania tego filtru będzie zwrócenie tylko ostatnich dwóch wierszy danych i wykluczenie pierwszego wiersza, ponieważ jego cena jest 100000, a nie pomiędzy określonym zakresem.</span><span class="sxs-lookup"><span data-stu-id="98792-117">The result of applying this filter would return only the last two rows in the data and exclude the first row because its price is 100000 and not between the specified range.</span></span>

## <a name="replace-missing-values"></a><span data-ttu-id="98792-118">Zamień brakujące wartości</span><span class="sxs-lookup"><span data-stu-id="98792-118">Replace missing values</span></span>

<span data-ttu-id="98792-119">Brakujące wartości są typowym wystąpieniem w zestawach danych.</span><span class="sxs-lookup"><span data-stu-id="98792-119">Missing values are a common occurrence in datasets.</span></span> <span data-ttu-id="98792-120">Jednym z metod postępowania z brakującymi wartościami jest zastąpienie ich wartością domyślną dla danego typu, jeśli jakakolwiek lub inna wartość istotna, taka jak wartość średnia w danych.</span><span class="sxs-lookup"><span data-stu-id="98792-120">One approach to dealing with missing values is to replace them with the default value for the given type if any or another meaningful value such as the mean value in the data.</span></span> 

<span data-ttu-id="98792-121">Użycie następujących danych wejściowych, które są ładowane do [`IDataView`](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="98792-121">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="98792-122">Zwróć uwagę, że ostatni element na naszej liście ma brakującą wartość `Price`dla.</span><span class="sxs-lookup"><span data-stu-id="98792-122">Notice that the last element in our list has a missing value for `Price`.</span></span> <span data-ttu-id="98792-123">Aby zastąpić brakujące wartości w `Price` kolumnie, [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) Użyj metody, aby wypełnić tę brakującą wartość.</span><span class="sxs-lookup"><span data-stu-id="98792-123">To replace the missing values in the `Price` column, use the [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) method to fill in that missing value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="98792-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*)działa tylko z danymi liczbowymi.</span><span class="sxs-lookup"><span data-stu-id="98792-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) only works with numerical data.</span></span>

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

<span data-ttu-id="98792-125">ML.NET obsługuje różne [tryby wymiany](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span><span class="sxs-lookup"><span data-stu-id="98792-125">ML.NET supports various [replacement modes](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span></span> <span data-ttu-id="98792-126">Powyższy przykład używa `Mean` trybu zamiany, który spowoduje wypełnienie brakującej wartości wartością średnią tej kolumny.</span><span class="sxs-lookup"><span data-stu-id="98792-126">The sample above uses the `Mean` replacement mode which will fill in the missing value with that column's average value.</span></span> <span data-ttu-id="98792-127">Wynikiem zamiany jest wypełnienie `Price` właściwości ostatniego elementu w danych z 200 000, ponieważ jest to średnia z 100 000 i 300 000.</span><span class="sxs-lookup"><span data-stu-id="98792-127">The replacement 's result fills in the `Price` property for the last element in our data with 200,000 since it's the average of 100,000 and 300,000.</span></span> 

## <a name="use-normalizers"></a><span data-ttu-id="98792-128">Korzystanie z normalizacji</span><span class="sxs-lookup"><span data-stu-id="98792-128">Use normalizers</span></span>

<span data-ttu-id="98792-129">[Normalizacja](https://en.wikipedia.org/wiki/Feature_scaling) to technika przetwarzania wstępnego danych używana do standaryzacji funkcji, które nie znajdują się na tej samej skali, co ułatwia algorytmom szybsze wywoływanie zbieżności.</span><span class="sxs-lookup"><span data-stu-id="98792-129">[Normalization](https://en.wikipedia.org/wiki/Feature_scaling) is a data pre-processing technique used to standardize features that are not on the same scale which helps algorithms converge faster.</span></span> <span data-ttu-id="98792-130">Na przykład zakresy wartości, takie jak wiek i dochód, różnią się znacznie w stosunku do wieku w zakresie 0-100 i przychodów ogólnie w zakresie od zera do tysięcy.</span><span class="sxs-lookup"><span data-stu-id="98792-130">For example, the ranges for values like age and income vary significantly with age generally being in the range of 0-100 and income generally being in the range of zero to thousands.</span></span> <span data-ttu-id="98792-131">Odwiedź [stronę przekształcenia](../resources/transforms.md) , aby uzyskać bardziej szczegółową listę i opis transformacji normalizacji.</span><span class="sxs-lookup"><span data-stu-id="98792-131">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of normalization transforms.</span></span> 

### <a name="min-max-normalization"></a><span data-ttu-id="98792-132">Minimalna-Maksymalna normalizacja</span><span class="sxs-lookup"><span data-stu-id="98792-132">Min-Max normalization</span></span>

<span data-ttu-id="98792-133">Użycie następujących danych wejściowych, które są ładowane do [`IDataView`](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="98792-133">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="98792-134">Normalizację można zastosować do kolumn z pojedynczą wartością liczbową, a także wektorami.</span><span class="sxs-lookup"><span data-stu-id="98792-134">Normalization can be applied to columns with single numerical values as well as vectors.</span></span> <span data-ttu-id="98792-135">Normalizuje dane w `Price` kolumnie, używając minimalnej normalizacji [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) z metodą.</span><span class="sxs-lookup"><span data-stu-id="98792-135">Normalize the data in the `Price` column using min-max normalization with the [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) method.</span></span>

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

<span data-ttu-id="98792-136">Pierwotne wartości `[200000,100000]` cen są konwertowane na `[ 1, 0.5 ]` użycie `MinMax` formuły normalizacji, która generuje wartości wyjściowe z zakresu 0-1.</span><span class="sxs-lookup"><span data-stu-id="98792-136">The original price values `[200000,100000]` are converted to `[ 1, 0.5 ]` using the `MinMax` normalization formula which generates output values in the range of 0-1.</span></span>

### <a name="binning"></a><span data-ttu-id="98792-137">Pakowania</span><span class="sxs-lookup"><span data-stu-id="98792-137">Binning</span></span>

<span data-ttu-id="98792-138">[Pakowania](https://en.wikipedia.org/wiki/Data_binning) konwertuje ciągłe wartości na dyskretną reprezentację danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="98792-138">[Binning](https://en.wikipedia.org/wiki/Data_binning) converts continuous values into a discrete representation of the input.</span></span> <span data-ttu-id="98792-139">Załóżmy na przykład, że jedna z Twoich funkcji jest w wieku.</span><span class="sxs-lookup"><span data-stu-id="98792-139">For example, suppose one of your features is age.</span></span> <span data-ttu-id="98792-140">Zamiast korzystać z rzeczywistej wartości wieku, pakowania tworzy zakresy dla tej wartości.</span><span class="sxs-lookup"><span data-stu-id="98792-140">Instead of using the actual age value,  binning creates ranges for that value.</span></span> <span data-ttu-id="98792-141">0-18 może być jednym pojemnikem, innym może być 19-35 i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="98792-141">0-18 could be one bin, another could be 19-35 and so on.</span></span> 

<span data-ttu-id="98792-142">Użycie następujących danych wejściowych, które są ładowane do [`IDataView`](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="98792-142">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="98792-143">Normalizowanie danych do pojemników przy użyciu [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning*) metody.</span><span class="sxs-lookup"><span data-stu-id="98792-143">Normalize the data into bins using the [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning*) method.</span></span> <span data-ttu-id="98792-144">`maximumBinCount` Parametr umożliwia określenie liczby pojemników potrzebnych do klasyfikowania danych.</span><span class="sxs-lookup"><span data-stu-id="98792-144">The `maximumBinCount` parameter enables you to specify the number of bins needed to classify your data.</span></span> <span data-ttu-id="98792-145">W tym przykładzie dane będą umieszczane w dwóch pojemnikach.</span><span class="sxs-lookup"><span data-stu-id="98792-145">In this example, data will be put into two bins.</span></span>  

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

<span data-ttu-id="98792-146">Wynik pakowania tworzy granice `[0,200000,Infinity]`bin.</span><span class="sxs-lookup"><span data-stu-id="98792-146">The result of binning creates bin bounds of `[0,200000,Infinity]`.</span></span> <span data-ttu-id="98792-147">W związku z tym te `[0,1,1]` pojemniki są spowodowane tym, że Pierwsza obserwacja jest między 0-200000 a pozostałe są większe niż 200000, ale mniejsze niż nieskończoność.</span><span class="sxs-lookup"><span data-stu-id="98792-147">Therefore the resulting bins are `[0,1,1]` because the first observation is between 0-200000 and the others are greater than 200000 but less than infinity.</span></span>

## <a name="work-with-categorical-data"></a><span data-ttu-id="98792-148">Pracuj z danymi kategorii</span><span class="sxs-lookup"><span data-stu-id="98792-148">Work with categorical data</span></span>

<span data-ttu-id="98792-149">Dane nieliczbowe kategorii muszą zostać przekonwertowane na liczbę przed użyciem do kompilowania modelu uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="98792-149">Non-numeric categorical data needs to be converted to a number before being used to build a machine learning model.</span></span> 

<span data-ttu-id="98792-150">Użycie następujących danych wejściowych, które są ładowane do [`IDataView`](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="98792-150">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="98792-151">Właściwość kategorii `VehicleType` można przekonwertować na liczbę [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*) przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="98792-151">The categorical `VehicleType` property can be converted into a number using the [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*) method.</span></span> 

```csharp
// Define categorical transform estimator
var categoricalEstimator = mlContext.Transforms.Categorical.OneHotEncoding("VehicleType");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer categoricalTransformer = categoricalEstimator.Fit(data);

// Transform Data
IDataView transformedData = categoricalTransformer.Transform(data);
```

<span data-ttu-id="98792-152">Wynikiem przekształcenia jest konwertowanie wartości `VehicleType` tekstowej na liczbę.</span><span class="sxs-lookup"><span data-stu-id="98792-152">The resulting transform converts the text value of `VehicleType` to a number.</span></span> <span data-ttu-id="98792-153">Po zastosowaniu przekształcenia `VehicleType` wpisy w kolumnie stają się następujące:</span><span class="sxs-lookup"><span data-stu-id="98792-153">The entries in the `VehicleType` column become the following when the transform is applied:</span></span> 

```text
[
    1, // SUV
    2, // Sedan
    1 // SUV
]
```

## <a name="work-with-text-data"></a><span data-ttu-id="98792-154">Pracuj z danymi tekstowymi</span><span class="sxs-lookup"><span data-stu-id="98792-154">Work with text data</span></span>

<span data-ttu-id="98792-155">Aby można było utworzyć model uczenia maszynowego, dane tekstowe muszą zostać przekształcone w liczby.</span><span class="sxs-lookup"><span data-stu-id="98792-155">Text data needs to be transformed into numbers before using it to build a machine learning model.</span></span> <span data-ttu-id="98792-156">Odwiedź [stronę przekształcenia](../resources/transforms.md) , aby uzyskać bardziej szczegółową listę i opis przekształceń tekstu.</span><span class="sxs-lookup"><span data-stu-id="98792-156">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of text transforms.</span></span>

<span data-ttu-id="98792-157">Używając danych, takich jak poniższe dane, które zostały załadowane [`IDataView`](xref:Microsoft.ML.IDataView)do:</span><span class="sxs-lookup"><span data-stu-id="98792-157">Using data like the data below that has been loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="98792-158">Minimalny krok konwersji tekstu na cyfrową reprezentację wektorową polega na użyciu [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) metody.</span><span class="sxs-lookup"><span data-stu-id="98792-158">The minimum step to convert text to a numerical vector representation is to use the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) method.</span></span> <span data-ttu-id="98792-159">Przy użyciu [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) transformacji serie przekształceń są stosowane do kolumny tekstu wejściowego, co jest wektorem liczbowym reprezentującym słowo LP-znormalizowane i znaki ngrams.</span><span class="sxs-lookup"><span data-stu-id="98792-159">By using the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) transform, a series of transformations is applied to the input text column resulting in a numerical vector representing the lp-normalized word and character ngrams.</span></span> 

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

<span data-ttu-id="98792-160">Wynikowa transformacja spowoduje przekonwertowanie wartości tekstowych w `Description` kolumnie na wektor liczbowy, który wygląda podobnie do danych wyjściowych poniżej:</span><span class="sxs-lookup"><span data-stu-id="98792-160">The resulting transform would convert the text values in the `Description` column to a numerical vector that looks similar to the output below:</span></span>

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

<span data-ttu-id="98792-161">Połącz złożone kroki przetwarzania tekstu w [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) celu usunięcia szumu i potencjalnie Zmniejsz ilość wymaganych zasobów przetwarzania zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="98792-161">Combine complex text processing steps into an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) to remove noise and potentially reduce the amount of required processing resources as needed.</span></span>

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

<span data-ttu-id="98792-162">`textEstimator`zawiera podzestaw operacji wykonywanych przez [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) metodę.</span><span class="sxs-lookup"><span data-stu-id="98792-162">`textEstimator` contains a subset of operations performed by the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) method.</span></span> <span data-ttu-id="98792-163">Zaletą bardziej złożonej potoku jest kontrola i widoczność przekształceń zastosowanych do danych.</span><span class="sxs-lookup"><span data-stu-id="98792-163">The benefit of a more complex pipeline is control and visibility over the transformations applied to the data.</span></span> 

<span data-ttu-id="98792-164">Przy użyciu pierwszego wpisu na przykład, poniżej przedstawiono szczegółowy opis wyników przedstawionych przez kroki transformacji zdefiniowane przez `textEstimator`:</span><span class="sxs-lookup"><span data-stu-id="98792-164">Using the first entry as an example, the following is a detailed description of the results produced by the transformation steps defined by `textEstimator`:</span></span>

<span data-ttu-id="98792-165">**Oryginalny tekst: Jest to dobry produkt**</span><span class="sxs-lookup"><span data-stu-id="98792-165">**Original Text: This is a good product**</span></span>

|<span data-ttu-id="98792-166">Transformacja</span><span class="sxs-lookup"><span data-stu-id="98792-166">Transform</span></span> | <span data-ttu-id="98792-167">Opis</span><span class="sxs-lookup"><span data-stu-id="98792-167">Description</span></span> | <span data-ttu-id="98792-168">Wynik</span><span class="sxs-lookup"><span data-stu-id="98792-168">Result</span></span>
|--|--|--|
|<span data-ttu-id="98792-169">1. NormalizeText</span><span class="sxs-lookup"><span data-stu-id="98792-169">1. NormalizeText</span></span> | <span data-ttu-id="98792-170">Konwertuje domyślnie wszystkie litery na małe</span><span class="sxs-lookup"><span data-stu-id="98792-170">Converts all letters to lowercase by default</span></span> | <span data-ttu-id="98792-171">jest to dobry produkt</span><span class="sxs-lookup"><span data-stu-id="98792-171">this is a good product</span></span>
|<span data-ttu-id="98792-172">2. TokenizeWords</span><span class="sxs-lookup"><span data-stu-id="98792-172">2. TokenizeWords</span></span> | <span data-ttu-id="98792-173">Dzieli ciąg na pojedyncze wyrazy</span><span class="sxs-lookup"><span data-stu-id="98792-173">Splits string into individual words</span></span> | <span data-ttu-id="98792-174">["This", "is", "a", "dobry", "Product"]</span><span class="sxs-lookup"><span data-stu-id="98792-174">["this","is","a","good","product"]</span></span>
|<span data-ttu-id="98792-175">3. RemoveDefaultStopWords</span><span class="sxs-lookup"><span data-stu-id="98792-175">3. RemoveDefaultStopWords</span></span> | <span data-ttu-id="98792-176">Usuwa Stop-słowa, *takie* jak *i.*</span><span class="sxs-lookup"><span data-stu-id="98792-176">Removes stopwords like *is* and *a*.</span></span> | <span data-ttu-id="98792-177">["dobry", "produkt"]</span><span class="sxs-lookup"><span data-stu-id="98792-177">["good","product"]</span></span>
|<span data-ttu-id="98792-178">4. MapValueToKey</span><span class="sxs-lookup"><span data-stu-id="98792-178">4. MapValueToKey</span></span> | <span data-ttu-id="98792-179">Mapuje wartości na klucze (kategorie) w oparciu o dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="98792-179">Maps the values to keys (categories) based on the input data</span></span> |  <span data-ttu-id="98792-180">[1,2]</span><span class="sxs-lookup"><span data-stu-id="98792-180">[1,2]</span></span>
|<span data-ttu-id="98792-181">5. ProduceNGrams</span><span class="sxs-lookup"><span data-stu-id="98792-181">5. ProduceNGrams</span></span> | <span data-ttu-id="98792-182">Przekształca tekst w sekwencję kolejnych wyrazów</span><span class="sxs-lookup"><span data-stu-id="98792-182">Transforms text into sequence of consecutive words</span></span> | <span data-ttu-id="98792-183">[1,1,1,0,0]</span><span class="sxs-lookup"><span data-stu-id="98792-183">[1,1,1,0,0]</span></span>
|<span data-ttu-id="98792-184">6. NormalizeLpNorm</span><span class="sxs-lookup"><span data-stu-id="98792-184">6. NormalizeLpNorm</span></span> | <span data-ttu-id="98792-185">Skalowanie danych wejściowych według ich standardu LP</span><span class="sxs-lookup"><span data-stu-id="98792-185">Scale inputs by their lp-norm</span></span> | <span data-ttu-id="98792-186">[0,577350529, 0,577350529, 0,577350529, 0, 0]</span><span class="sxs-lookup"><span data-stu-id="98792-186">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span></span>
