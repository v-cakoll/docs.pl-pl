---
title: Przygotowuje dane do budowania modelu
description: Dowiedz się, jak użyć przekształceń w strukturze ML.NET do manipulowania i przygotowuje dane do dodatkowego przetwarzania lub tworzenia modelu.
author: luisquintanilla
ms.author: luquinta
ms.date: 06/25/2019
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 4b7d5a09044e49f1b57b8276b893e0fc962a3be2
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397716"
---
# <a name="prepare-data-for-building-a-model"></a><span data-ttu-id="760c5-103">Przygotowuje dane do budowania modelu</span><span class="sxs-lookup"><span data-stu-id="760c5-103">Prepare data for building a model</span></span>

<span data-ttu-id="760c5-104">Dowiedz się, jak używać strukturze ML.NET do przygotowywania danych do dodatkowego przetwarzania lub budowania modelu.</span><span class="sxs-lookup"><span data-stu-id="760c5-104">Learn how to use ML.NET to prepare data for additional processing or building a model.</span></span>

<span data-ttu-id="760c5-105">Dane są często nieczyste i rozrzedzone.</span><span class="sxs-lookup"><span data-stu-id="760c5-105">Data is often unclean and sparse.</span></span> <span data-ttu-id="760c5-106">Ponadto algorytmów uczenia maszynowego w strukturze ML.NET oczekiwać, że dane wejściowe lub funkcje, aby być w przypadku pojedynczego wektora wartości liczbowych.</span><span class="sxs-lookup"><span data-stu-id="760c5-106">Additionally, ML.NET machine learning algorithms expect input or features to be in a single numerical vector.</span></span> <span data-ttu-id="760c5-107">Dlatego jest jednym z celów przygotowywania danych do pobrania danych do formatu oczekiwanego przez algorytmy strukturze ML.NET.</span><span class="sxs-lookup"><span data-stu-id="760c5-107">Therefore one of the goals of data preparation is to get the data into the format expected by ML.NET algorithms.</span></span> 

## <a name="filter-data"></a><span data-ttu-id="760c5-108">Filtrowanie danych</span><span class="sxs-lookup"><span data-stu-id="760c5-108">Filter data</span></span>

<span data-ttu-id="760c5-109">Czasami nie wszystkie dane w zestawie danych są istotne dla analizy.</span><span class="sxs-lookup"><span data-stu-id="760c5-109">Sometimes, not all data in a dataset is relevant for analysis.</span></span> <span data-ttu-id="760c5-110">Filtrowanie jest sposobem usunięcia danych nie ma znaczenia.</span><span class="sxs-lookup"><span data-stu-id="760c5-110">An approach to remove irrelevant data is filtering.</span></span> <span data-ttu-id="760c5-111">[ `DataOperationsCatalog` ](xref:Microsoft.ML.DataOperationsCatalog) Zawiera zestaw operacji filtrów, które pobierają w [ `IDataView` ](xref:Microsoft.ML.IDataView) zawierająca wszystkie dane i zwrócenia [IDataView](xref:Microsoft.ML.IDataView) zawierający tylko dane punktów orientacyjnych.</span><span class="sxs-lookup"><span data-stu-id="760c5-111">The [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) contains a set of filter operations that take in an [`IDataView`](xref:Microsoft.ML.IDataView) containing all of the data and return an [IDataView](xref:Microsoft.ML.IDataView) containing only the data points of interest.</span></span> <span data-ttu-id="760c5-112">Należy zauważyć, że ponieważ filtr operacje nie są [ `IEstimator` ](xref:Microsoft.ML.IEstimator%601) lub [ `ITransformer` ](xref:Microsoft.ML.ITransformer) , takich jak te w [ `TransformsCatalog` ](xref:Microsoft.ML.TransformsCatalog), nie mogą być dołączone jako część [ `EstimatorChain` ](xref:Microsoft.ML.Data.EstimatorChain%601) lub [ `TransformerChain` ](xref:Microsoft.ML.Data.TransformerChain%601) potoku przygotowywania danych.</span><span class="sxs-lookup"><span data-stu-id="760c5-112">It's important to note that because filter operations are not an [`IEstimator`](xref:Microsoft.ML.IEstimator%601) or [`ITransformer`](xref:Microsoft.ML.ITransformer) like those in the [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), they cannot be included as part of an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) or [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) data preparation pipeline.</span></span> 

<span data-ttu-id="760c5-113">Przy użyciu następujących danych wejściowych, który jest ładowany do [ `IDataView` ](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="760c5-113">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="760c5-114">Aby filtrować dane na podstawie wartości kolumny, należy użyć [ `FilterRowsByColumn` ](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) metody.</span><span class="sxs-lookup"><span data-stu-id="760c5-114">To filter data based on the value of a column, use the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) method.</span></span>

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

<span data-ttu-id="760c5-115">Powyższe przykładowe przyjmuje wierszy w zestawie danych z ceną między 200000 do 1 000 000.</span><span class="sxs-lookup"><span data-stu-id="760c5-115">The sample above takes rows in the dataset with a price between 200000 and 1000000.</span></span> <span data-ttu-id="760c5-116">Wynik zastosowania ten filtr będzie zwracać tylko ostatnie dwa wiersze danych i pominąć pierwszy wiersz, ponieważ jej miesięczna cena to 100000, a nie od określonego zakresu.</span><span class="sxs-lookup"><span data-stu-id="760c5-116">The result of applying this filter would return only the last two rows in the data and exclude the first row because its price is 100000 and not between the specified range.</span></span>

## <a name="replace-missing-values"></a><span data-ttu-id="760c5-117">Zastąp wartości Brak</span><span class="sxs-lookup"><span data-stu-id="760c5-117">Replace missing values</span></span>

<span data-ttu-id="760c5-118">Brak wartości są wystąpieniem typowe w zestawach danych.</span><span class="sxs-lookup"><span data-stu-id="760c5-118">Missing values are a common occurrence in datasets.</span></span> <span data-ttu-id="760c5-119">Jedno z podejść do radzenia sobie z brakującymi wartościami ma zastąpić je wartością domyślną dla danego typu lub innej mająca znaczenie wartość, takie jak średnia wartość w danych.</span><span class="sxs-lookup"><span data-stu-id="760c5-119">One approach to dealing with missing values is to replace them with the default value for the given type if any or another meaningful value such as the mean value in the data.</span></span> 

<span data-ttu-id="760c5-120">Przy użyciu następujących danych wejściowych, który jest ładowany do [ `IDataView` ](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="760c5-120">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="760c5-121">Należy zauważyć, że po ostatnim elemencie w naszej listy ma Brak wartości dla `Price`.</span><span class="sxs-lookup"><span data-stu-id="760c5-121">Notice that the last element in our list has a missing value for `Price`.</span></span> <span data-ttu-id="760c5-122">Aby zastąpić brakujących wartości w `Price` kolumny, użyj [ `ReplaceMissingValues` ](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) metodę, aby wypełnić tę wartość Brak.</span><span class="sxs-lookup"><span data-stu-id="760c5-122">To replace the missing values in the `Price` column, use the [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) method to fill in that missing value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="760c5-123">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) działa tylko z danymi liczbowymi.</span><span class="sxs-lookup"><span data-stu-id="760c5-123">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) only works with numerical data.</span></span>

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

<span data-ttu-id="760c5-124">Strukturze ML.NET obsługuje różne [tryby zastąpienie](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span><span class="sxs-lookup"><span data-stu-id="760c5-124">ML.NET supports various [replacement modes](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span></span> <span data-ttu-id="760c5-125">Przykład powyżej używa `Mean` trybu zastępczy, który wypełni brakujące wartością średniej wartości tej kolumny.</span><span class="sxs-lookup"><span data-stu-id="760c5-125">The sample above uses the `Mean` replacement mode which will fill in the missing value with that column's average value.</span></span> <span data-ttu-id="760c5-126">Wypełnia wyniku zastąpienia `Price` właściwość po ostatnim elemencie w naszych danych za pomocą 200 000, ponieważ jest średnią 100 000 i 300 000.</span><span class="sxs-lookup"><span data-stu-id="760c5-126">The replacement 's result fills in the `Price` property for the last element in our data with 200,000 since it's the average of 100,000 and 300,000.</span></span> 

## <a name="use-normalizers"></a><span data-ttu-id="760c5-127">Użyj normalizers</span><span class="sxs-lookup"><span data-stu-id="760c5-127">Use normalizers</span></span>

<span data-ttu-id="760c5-128">[Normalizacja](https://en.wikipedia.org/wiki/Feature_scaling) danych, przetwarzanie wstępne technika używana do standaryzacji funkcje, które nie znajdują się na tę samą skalę, która pomaga algorytmy zbiegają się szybciej.</span><span class="sxs-lookup"><span data-stu-id="760c5-128">[Normalization](https://en.wikipedia.org/wiki/Feature_scaling) is a data pre-processing technique used to standardize features that are not on the same scale which helps algorithms converge faster.</span></span> <span data-ttu-id="760c5-129">Na przykład zakresy dla wartości, takich jak wiek i przychody się istotnie różnić o wieku ogólnie jest z zakresu od 0 do 100 i przychody ogólnie znajdujące się w zakresie od zera do tysięcy.</span><span class="sxs-lookup"><span data-stu-id="760c5-129">For example, the ranges for values like age and income vary significantly with age generally being in the range of 0-100 and income generally being in the range of zero to thousands.</span></span> <span data-ttu-id="760c5-130">Odwiedź stronę [stronę przekształcenia](../resources/transforms.md) bardziej szczegółowe listę i opis przekształcenia normalizacji.</span><span class="sxs-lookup"><span data-stu-id="760c5-130">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of normalization transforms.</span></span> 

### <a name="min-max-normalization"></a><span data-ttu-id="760c5-131">Normalizacji minimum-maksimum</span><span class="sxs-lookup"><span data-stu-id="760c5-131">Min-Max normalization</span></span>

<span data-ttu-id="760c5-132">Przy użyciu następujących danych wejściowych, który jest ładowany do [ `IDataView` ](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="760c5-132">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="760c5-133">Normalizacja można zastosować do kolumn z jednej wartości liczbowe, a także wektorów.</span><span class="sxs-lookup"><span data-stu-id="760c5-133">Normalization can be applied to columns with single numerical values as well as vectors.</span></span> <span data-ttu-id="760c5-134">Normalizować dane w `Price` kolumny przy użyciu normalizacji minimum maksimum z [ `NormalizeMinMax` ](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) metody.</span><span class="sxs-lookup"><span data-stu-id="760c5-134">Normalize the data in the `Price` column using min-max normalization with the [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) method.</span></span>

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

<span data-ttu-id="760c5-135">Oryginalne wartości cen `[200000,100000]` są konwertowane na `[ 1, 0.5 ]` przy użyciu `MinMax` Formuła normalizacji, które generuje wartości wyjściowe w zakresie 0 – 1.</span><span class="sxs-lookup"><span data-stu-id="760c5-135">The original price values `[200000,100000]` are converted to `[ 1, 0.5 ]` using the `MinMax` normalization formula which generates output values in the range of 0-1.</span></span>

### <a name="binning"></a><span data-ttu-id="760c5-136">Kwantowanie</span><span class="sxs-lookup"><span data-stu-id="760c5-136">Binning</span></span>

<span data-ttu-id="760c5-137">[Kwantowanie](https://en.wikipedia.org/wiki/Data_binning) konwertuje ciągłe wartości dyskretnych reprezentacja danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="760c5-137">[Binning](https://en.wikipedia.org/wiki/Data_binning) converts continuous values into a discrete representation of the input.</span></span> <span data-ttu-id="760c5-138">Na przykład załóżmy, że jedna z funkcji jest okres ważności.</span><span class="sxs-lookup"><span data-stu-id="760c5-138">For example, suppose one of your features is age.</span></span> <span data-ttu-id="760c5-139">Zamiast używania wartości rzeczywistej wiek, pakowania tworzy zakresy dla tej wartości.</span><span class="sxs-lookup"><span data-stu-id="760c5-139">Instead of using the actual age value,  binning creates ranges for that value.</span></span> <span data-ttu-id="760c5-140">0 – 18 może być jednego pojemnika, inny może być 19 – 35 i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="760c5-140">0-18 could be one bin, another could be 19-35 and so on.</span></span> 

<span data-ttu-id="760c5-141">Przy użyciu następujących danych wejściowych, który jest ładowany do [ `IDataView` ](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="760c5-141">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="760c5-142">Normalizacji danych do pojemniki przy użyciu [ `NormalizeBinning` ](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning*) metody.</span><span class="sxs-lookup"><span data-stu-id="760c5-142">Normalize the data into bins using the [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning*) method.</span></span> <span data-ttu-id="760c5-143">`maximumBinCount` Parametr umożliwia określenie liczba pojemników potrzebne do klasyfikowania danych.</span><span class="sxs-lookup"><span data-stu-id="760c5-143">The `maximumBinCount` parameter enables you to specify the number of bins needed to classify your data.</span></span> <span data-ttu-id="760c5-144">W tym przykładzie dane będą umieszczone dwa pojemniki.</span><span class="sxs-lookup"><span data-stu-id="760c5-144">In this example, data will be put into two bins.</span></span>  

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

<span data-ttu-id="760c5-145">Wynik pakowania tworzy granice bin `[0,200000,Infinity]`.</span><span class="sxs-lookup"><span data-stu-id="760c5-145">The result of binning creates bin bounds of `[0,200000,Infinity]`.</span></span> <span data-ttu-id="760c5-146">W związku z tym pojemniki wynikowe są `[0,1,1]` ponieważ pierwszy obserwacji jest z zakresu od 0 200000 i inne są większe niż 200000, ale mniejszą niż nieskończoność.</span><span class="sxs-lookup"><span data-stu-id="760c5-146">Therefore the resulting bins are `[0,1,1]` because the first observation is between 0-200000 and the others are greater than 200000 but less than infinity.</span></span>

## <a name="work-with-categorical-data"></a><span data-ttu-id="760c5-147">Praca z danymi podzielonych na kategorie</span><span class="sxs-lookup"><span data-stu-id="760c5-147">Work with categorical data</span></span>

<span data-ttu-id="760c5-148">Dane podzielone na kategorie nieliczbowe musi być konwertowany na liczbę przed ich użyciem do tworzenia modelu uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="760c5-148">Non-numeric categorical data needs to be converted to a number before being used to build a machine learning model.</span></span> 

<span data-ttu-id="760c5-149">Przy użyciu następujących danych wejściowych, który jest ładowany do [ `IDataView` ](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="760c5-149">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="760c5-150">Podzielone na kategorie `VehicleType` właściwości mogą być konwertowane na numer przy użyciu [ `OneHotEncoding` ](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*) metody.</span><span class="sxs-lookup"><span data-stu-id="760c5-150">The categorical `VehicleType` property can be converted into a number using the [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*) method.</span></span> 

```csharp
// Define categorical transform estimator
var categoricalEstimator = mlContext.Transforms.Categorical.OneHotEncoding("VehicleType");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer categoricalTransformer = categoricalEstimator.Fit(data);

// Transform Data
IDataView transformedData = categoricalTransformer.Transform(data);
```

<span data-ttu-id="760c5-151">Wynikowy przekształcenie konwertuje wartość tekstu `VehicleType` na liczbę.</span><span class="sxs-lookup"><span data-stu-id="760c5-151">The resulting transform converts the text value of `VehicleType` to a number.</span></span> <span data-ttu-id="760c5-152">Wpisy w `VehicleType` kolumny stają się następujące po zastosowaniu przekształcenia:</span><span class="sxs-lookup"><span data-stu-id="760c5-152">The entries in the `VehicleType` column become the following when the transform is applied:</span></span> 

```text
[
    1, // SUV
    2, // Sedan
    1 // SUV
]
```

## <a name="work-with-text-data"></a><span data-ttu-id="760c5-153">Praca z danymi tekstu</span><span class="sxs-lookup"><span data-stu-id="760c5-153">Work with text data</span></span>

<span data-ttu-id="760c5-154">Dane tekstowe muszą zostać przekształcone na liczby, przed jego użyciem, aby zbudować model uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="760c5-154">Text data needs to be transformed into numbers before using it to build a machine learning model.</span></span> <span data-ttu-id="760c5-155">Odwiedź stronę [stronę przekształcenia](../resources/transforms.md) bardziej szczegółową listę i opis przekształcenia tekstu.</span><span class="sxs-lookup"><span data-stu-id="760c5-155">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of text transforms.</span></span>

<span data-ttu-id="760c5-156">Korzystanie z danych, takich jak dane poniżej, który został załadowany do [ `IDataView` ](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="760c5-156">Using data like the data below that has been loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="760c5-157">Minimalna krokiem do konwertowania tekstu do reprezentacji liczbowych wektora jest używanie [ `FeaturizeText` ](xref:Microsoft.ML.TextCatalog.FeaturizeText*) metody.</span><span class="sxs-lookup"><span data-stu-id="760c5-157">The minimum step to convert text to a numerical vector representation is to use the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) method.</span></span> <span data-ttu-id="760c5-158">Za pomocą [ `FeaturizeText` ](xref:Microsoft.ML.TextCatalog.FeaturizeText*) przekształcenie, które szereg przekształcenia jest stosowany do kolumny wprowadzania tekstu, co w przypadku wektora wartości liczbowych, reprezentujący znormalizowane lp word i ngrams znak.</span><span class="sxs-lookup"><span data-stu-id="760c5-158">By using the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) transform, a series of transformations is applied to the input text column resulting in a numerical vector representing the lp-normalized word and character ngrams.</span></span> 

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

<span data-ttu-id="760c5-159">Przekształcanie wynikowy będzie konwersji wartości tekstowe w `Description` kolumny liczbowe wektor, który wygląda podobnie do danych wyjściowych poniżej:</span><span class="sxs-lookup"><span data-stu-id="760c5-159">The resulting transform would convert the text values in the `Description` column to a numerical vector that looks similar to the output below:</span></span>

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

<span data-ttu-id="760c5-160">Przetwarzanie złożonych tekstu łączenia wchodzi do [ `EstimatorChain` ](xref:Microsoft.ML.Data.EstimatorChain%601) usunąć hałasu i zmniejszenie ilości zasobów do przetwarzania wymagane zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="760c5-160">Combine complex text processing steps into an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) to remove noise and potentially reduce the amount of required processing resources as needed.</span></span>

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

<span data-ttu-id="760c5-161">`textEstimator` zawiera podzestaw operacji wykonywanych przez [ `FeaturizeText` ](xref:Microsoft.ML.TextCatalog.FeaturizeText*) metody.</span><span class="sxs-lookup"><span data-stu-id="760c5-161">`textEstimator` contains a subset of operations performed by the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) method.</span></span> <span data-ttu-id="760c5-162">Korzyści wynikające z bardziej złożonych potoku kontroli i widoczności umieszczeniu transformacji zastosowanych względem danych.</span><span class="sxs-lookup"><span data-stu-id="760c5-162">The benefit of a more complex pipeline is control and visibility over the transformations applied to the data.</span></span> 

<span data-ttu-id="760c5-163">Przy użyciu pierwszej pozycji, na przykład, poniżej przedstawiono szczegółowy opis efektów kroki przekształcania definicją `textEstimator`:</span><span class="sxs-lookup"><span data-stu-id="760c5-163">Using the first entry as an example, the following is a detailed description of the results produced by the transformation steps defined by `textEstimator`:</span></span>

<span data-ttu-id="760c5-164">**Oryginalny tekst: Jest to dobry produktu**</span><span class="sxs-lookup"><span data-stu-id="760c5-164">**Original Text: This is a good product**</span></span>

|<span data-ttu-id="760c5-165">Transformacja</span><span class="sxs-lookup"><span data-stu-id="760c5-165">Transform</span></span> | <span data-ttu-id="760c5-166">Opis</span><span class="sxs-lookup"><span data-stu-id="760c5-166">Description</span></span> | <span data-ttu-id="760c5-167">Wynik</span><span class="sxs-lookup"><span data-stu-id="760c5-167">Result</span></span>
|--|--|--|
|<span data-ttu-id="760c5-168">1. NormalizeText</span><span class="sxs-lookup"><span data-stu-id="760c5-168">1. NormalizeText</span></span> | <span data-ttu-id="760c5-169">Konwertuje wszystkie litery na małe litery, domyślnie</span><span class="sxs-lookup"><span data-stu-id="760c5-169">Converts all letters to lowercase by default</span></span> | <span data-ttu-id="760c5-170">Jest to dobry produktu</span><span class="sxs-lookup"><span data-stu-id="760c5-170">this is a good product</span></span>
|<span data-ttu-id="760c5-171">2. TokenizeWords</span><span class="sxs-lookup"><span data-stu-id="760c5-171">2. TokenizeWords</span></span> | <span data-ttu-id="760c5-172">Dzieli dane ciągu do poszczególnych wyrazów</span><span class="sxs-lookup"><span data-stu-id="760c5-172">Splits string into individual words</span></span> | <span data-ttu-id="760c5-173">["to", "is", "","dobre","produkt"]</span><span class="sxs-lookup"><span data-stu-id="760c5-173">["this","is","a","good","product"]</span></span>
|<span data-ttu-id="760c5-174">3. RemoveDefaultStopWords</span><span class="sxs-lookup"><span data-stu-id="760c5-174">3. RemoveDefaultStopWords</span></span> | <span data-ttu-id="760c5-175">Usuwa Stop-słowa, takie jak *jest* *i*.</span><span class="sxs-lookup"><span data-stu-id="760c5-175">Removes stopwords like *is* and *a*.</span></span> | <span data-ttu-id="760c5-176">["dobre", "produkt"]</span><span class="sxs-lookup"><span data-stu-id="760c5-176">["good","product"]</span></span>
|<span data-ttu-id="760c5-177">4. MapValueToKey</span><span class="sxs-lookup"><span data-stu-id="760c5-177">4. MapValueToKey</span></span> | <span data-ttu-id="760c5-178">Mapuje wartości kluczy (kategorie), na podstawie danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="760c5-178">Maps the values to keys (categories) based on the input data</span></span> |  <span data-ttu-id="760c5-179">[1,2]</span><span class="sxs-lookup"><span data-stu-id="760c5-179">[1,2]</span></span>
|<span data-ttu-id="760c5-180">5. ProduceNGrams</span><span class="sxs-lookup"><span data-stu-id="760c5-180">5. ProduceNGrams</span></span> | <span data-ttu-id="760c5-181">Przekształca tekst w sekwencji kolejnych wyrazów</span><span class="sxs-lookup"><span data-stu-id="760c5-181">Transforms text into sequence of consecutive words</span></span> | <span data-ttu-id="760c5-182">[1,1,1,0,0]</span><span class="sxs-lookup"><span data-stu-id="760c5-182">[1,1,1,0,0]</span></span>
|<span data-ttu-id="760c5-183">6. NormalizeLpNorm</span><span class="sxs-lookup"><span data-stu-id="760c5-183">6. NormalizeLpNorm</span></span> | <span data-ttu-id="760c5-184">Skala wejść przez ich lp typ norm</span><span class="sxs-lookup"><span data-stu-id="760c5-184">Scale inputs by their lp-norm</span></span> | <span data-ttu-id="760c5-185">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span><span class="sxs-lookup"><span data-stu-id="760c5-185">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span></span>
