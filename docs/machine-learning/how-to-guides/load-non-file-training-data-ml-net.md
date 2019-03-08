---
title: Szkolenie modelu uczenia maszynowego z danymi, które nie znajduje się w pliku tekstowym - strukturze ML.NET
description: Dowiedz się, jak używać strukturze ML.NET do ładowania danych innego niż plik szkolenia szkoleń modelowych jako część potoku prognoz uczenia maszynowego.
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 27b327a63cb55b7fce0f4ff7facd3ee7c4a1c85c
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57678629"
---
# <a name="train-a-machine-learning-model-with-data-thats-not-in-a-text-file---mlnet"></a><span data-ttu-id="16f77-103">Szkolenie modelu uczenia maszynowego z danymi, które nie znajduje się w pliku tekstowym - strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="16f77-103">Train a machine learning model with data that's not in a text file - ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="16f77-104">W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="16f77-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="16f77-105">Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="16f77-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="16f77-106">Obecnie używasz w tym przykładzie porad i pokrewnych **strukturze ML.NET wersji 0.10**.</span><span class="sxs-lookup"><span data-stu-id="16f77-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="16f77-107">Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="16f77-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="16f77-108">W przypadku użycia często wykazały strukturze ML.NET jest używany `TextLoader` można odczytać danych szkoleniowych z pliku.</span><span class="sxs-lookup"><span data-stu-id="16f77-108">The commonly demonstrated use case for ML.NET is use the `TextLoader` to read the training data from a file.</span></span>
<span data-ttu-id="16f77-109">Jednak w przypadku scenariuszy szkoleniowych w czasie rzeczywistym dane mogą być w innych miejscach, takich jak:</span><span class="sxs-lookup"><span data-stu-id="16f77-109">However, in real-time training scenarios the data can be elsewhere, such as:</span></span>

* <span data-ttu-id="16f77-110">w tabelach SQL</span><span class="sxs-lookup"><span data-stu-id="16f77-110">in SQL tables</span></span>
* <span data-ttu-id="16f77-111">wyodrębniony z plików dziennika</span><span class="sxs-lookup"><span data-stu-id="16f77-111">extracted from log files</span></span>
* <span data-ttu-id="16f77-112">wygenerowany na bieżąco</span><span class="sxs-lookup"><span data-stu-id="16f77-112">generated on the fly</span></span>

<span data-ttu-id="16f77-113">Użyj [zrozumienie schematu](https://github.com/dotnet/machinelearning/tree/master/docs/code/SchemaComprehension.md) Aby wyświetlić istniejące C# `IEnumerable` w strukturze ML.NET jako `DataView`.</span><span class="sxs-lookup"><span data-stu-id="16f77-113">Use [schema comprehension](https://github.com/dotnet/machinelearning/tree/master/docs/code/SchemaComprehension.md) to bring an existing C# `IEnumerable` into ML.NET as a `DataView`.</span></span>

<span data-ttu-id="16f77-114">W tym przykładzie utworzysz klienta model predykcyjny współczynnika zmian i wyodrębniania następujące funkcje z Twoim systemem produkcyjnym:</span><span class="sxs-lookup"><span data-stu-id="16f77-114">For this example, you'll build the customer churn prediction model, and extract the following features from your production system:</span></span>

* <span data-ttu-id="16f77-115">Identyfikator klienta (ignorowane przez model)</span><span class="sxs-lookup"><span data-stu-id="16f77-115">Customer ID (ignored by the model)</span></span>
* <span data-ttu-id="16f77-116">Czy klient ma modyfikowane (cel "etykieta")</span><span class="sxs-lookup"><span data-stu-id="16f77-116">Whether the customer has churned (the target 'label')</span></span>
* <span data-ttu-id="16f77-117">Kategoria demograficznych (jednego ciągu, takich jak "młodych zawartość dla dorosłych" itp.)</span><span class="sxs-lookup"><span data-stu-id="16f77-117">The 'demographic category' (one string, like 'young adult' etc.)</span></span>
* <span data-ttu-id="16f77-118">Liczba wizyt w ciągu ostatnich 5 dni.</span><span class="sxs-lookup"><span data-stu-id="16f77-118">The number of visits from the last 5 days.</span></span>

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

<span data-ttu-id="16f77-119">Załadować te dane do `DataView` i trenowanie modelu, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="16f77-119">Load this data into the `DataView` and train the model, using the following code:</span></span>

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
var trainData = mlContext.Data.ReadFromEnumerable(churnData);

// Build the learning pipeline.
// In our case, we will one-hot encode the demographic category, and concatenate that with the number of visits.
// We apply our FastTree binary classifier to predict the 'HasChurned' label.

var pipeline = mlContext.Transforms.Categorical.OneHotEncoding("DemographicCategory")
    .Append(mlContext.Transforms.Concatenate("Features", "DemographicCategory", "LastVisits"))
    .Append(mlContext.BinaryClassification.Trainers.FastTree("HasChurned", "Features", numTrees: 20));

var model = pipeline.Fit(trainData);
```
