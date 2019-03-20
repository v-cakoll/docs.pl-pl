---
title: Szkolenie modelu uczenia maszynowego z danymi, które nie znajduje się w pliku tekstowym - strukturze ML.NET
description: Dowiedz się, jak używać strukturze ML.NET do ładowania danych innego niż plik szkolenia szkoleń modelowych jako część potoku prognoz uczenia maszynowego.
ms.date: 03/18/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 32de37e45b9e19669ea06d74c7f252ec885fe004
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2019
ms.locfileid: "58186094"
---
# <a name="train-a-machine-learning-model-with-data-thats-not-in-a-text-file---mlnet"></a><span data-ttu-id="19e4a-103">Szkolenie modelu uczenia maszynowego z danymi, które nie znajduje się w pliku tekstowym - strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="19e4a-103">Train a machine learning model with data that's not in a text file - ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="19e4a-104">W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="19e4a-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="19e4a-105">Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="19e4a-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="19e4a-106">Obecnie używasz w tym przykładzie porad i pokrewnych **strukturze ML.NET wersji 0,11**.</span><span class="sxs-lookup"><span data-stu-id="19e4a-106">This how-to and related sample are currently using **ML.NET version 0.11**.</span></span> <span data-ttu-id="19e4a-107">Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="19e4a-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="19e4a-108">W przypadku użycia często wykazały strukturze ML.NET jest używany `TextLoader` można odczytać danych szkoleniowych z pliku.</span><span class="sxs-lookup"><span data-stu-id="19e4a-108">The commonly demonstrated use case for ML.NET is use the `TextLoader` to read the training data from a file.</span></span>
<span data-ttu-id="19e4a-109">Jednak w przypadku scenariuszy szkoleniowych w czasie rzeczywistym dane mogą być w innych miejscach, takich jak:</span><span class="sxs-lookup"><span data-stu-id="19e4a-109">However, in real-time training scenarios the data can be elsewhere, such as:</span></span>

* <span data-ttu-id="19e4a-110">w tabelach SQL</span><span class="sxs-lookup"><span data-stu-id="19e4a-110">in SQL tables</span></span>
* <span data-ttu-id="19e4a-111">JSON/XML</span><span class="sxs-lookup"><span data-stu-id="19e4a-111">JSON/XML</span></span>
* <span data-ttu-id="19e4a-112">wyodrębniony z plików dziennika</span><span class="sxs-lookup"><span data-stu-id="19e4a-112">extracted from log files</span></span>
* <span data-ttu-id="19e4a-113">wygenerowany na bieżąco</span><span class="sxs-lookup"><span data-stu-id="19e4a-113">generated on the fly</span></span>

<span data-ttu-id="19e4a-114">Użyj [zrozumienie schematu](https://github.com/dotnet/machinelearning/tree/master/docs/code/SchemaComprehension.md) Aby wyświetlić istniejące C# `IEnumerable` w strukturze ML.NET jako `DataView`.</span><span class="sxs-lookup"><span data-stu-id="19e4a-114">Use [schema comprehension](https://github.com/dotnet/machinelearning/tree/master/docs/code/SchemaComprehension.md) to bring an existing C# `IEnumerable` into ML.NET as a `DataView`.</span></span>

<span data-ttu-id="19e4a-115">W tym przykładzie utworzysz klienta model predykcyjny współczynnika zmian i wyodrębniania następujące funkcje z Twoim systemem produkcyjnym:</span><span class="sxs-lookup"><span data-stu-id="19e4a-115">For this example, you'll build the customer churn prediction model, and extract the following features from your production system:</span></span>

* <span data-ttu-id="19e4a-116">Identyfikator klienta (ignorowane przez model)</span><span class="sxs-lookup"><span data-stu-id="19e4a-116">Customer ID (ignored by the model)</span></span>
* <span data-ttu-id="19e4a-117">Czy klient ma modyfikowane (cel "etykieta")</span><span class="sxs-lookup"><span data-stu-id="19e4a-117">Whether the customer has churned (the target 'label')</span></span>
* <span data-ttu-id="19e4a-118">Kategoria demograficznych (jednego ciągu, takich jak "młodych zawartość dla dorosłych" itp.)</span><span class="sxs-lookup"><span data-stu-id="19e4a-118">The 'demographic category' (one string, like 'young adult' etc.)</span></span>
* <span data-ttu-id="19e4a-119">Liczba wizyt w ciągu ostatnich 5 dni.</span><span class="sxs-lookup"><span data-stu-id="19e4a-119">The number of visits from the last 5 days.</span></span>

```csharp
private class CustomerChurnInfo
{
    public string CustomerID { get; set; }
    public bool HasChurned { get; set; }
    public string DemographicCategory { get; set; }
    // Visits during last 5 days, latest to newest.
    [VectorType(5)]
    public float[] LastVisits { get; set; }
}
```

<span data-ttu-id="19e4a-120">Załadować te dane do `DataView` i trenowanie modelu, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="19e4a-120">Load this data into the `DataView` and train the model, using the following code:</span></span>

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging,
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Step one: read the data as an IDataView.
// Let's assume that 'GetChurnData()' fetches and returns the training data from somewhere.
IEnumerable<CustomerChurnInfo> churnData = GetChurnInfo();

// Turn the data into the ML.NET data view.
// We can use CreateDataView or CreateStreamingDataView, depending on whether 'churnData' is an IList,
// or merely an IEnumerable.
var trainData = mlContext.Data.LoadFromEnumerable(churnData);

// Build the learning pipeline.
// In our case, we will one-hot encode the demographic category, and concatenate that with the number of visits.
// We apply our FastTree binary classifier to predict the 'HasChurned' label.

var pipeline = mlContext.Transforms.Categorical.OneHotEncoding("DemographicCategory")
    .Append(mlContext.Transforms.Concatenate("Features", "DemographicCategory", "LastVisits"))
    .Append(mlContext.BinaryClassification.Trainers.FastTree("HasChurned", "Features", numTrees: 20));

var model = pipeline.Fit(trainData);
```
