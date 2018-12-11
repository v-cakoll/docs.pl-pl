---
title: Szkolenie modelu uczenia maszynowego z danymi, które nie znajduje się w pliku tekstowym - strukturze ML.NET
description: Dowiedz się, jak używać strukturze ML.NET do ładowania danych innego niż plik szkolenia szkoleń modelowych jako część potoku prognoz uczenia maszynowego.
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: 971c5c62acc9dd7bf29aa11ce898c2b76822c3d7
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53125405"
---
# <a name="train-a-machine-learning-model-with-data-thats-not-in-a-text-file---mlnet"></a>Szkolenie modelu uczenia maszynowego z danymi, które nie znajduje się w pliku tekstowym - strukturze ML.NET

W przypadku użycia często wykazały strukturze ML.NET jest używany `TextLoader` można odczytać danych szkoleniowych z pliku.
Jednak w przypadku scenariuszy szkoleniowych w czasie rzeczywistym dane mogą być w innych miejscach, takich jak:

* w tabelach SQL
* wyodrębniony z plików dziennika
* wygenerowany na bieżąco

Użyj [zrozumienie schematu](https://github.com/dotnet/machinelearning/tree/master/docs/code/SchemaComprehension.md) Aby wyświetlić istniejące C# `IEnumerable` w strukturze ML.NET jako `DataView`.

W tym przykładzie utworzysz klienta model predykcyjny współczynnika zmian i wyodrębniania następujące funkcje z Twoim systemem produkcyjnym:

* Identyfikator klienta (ignorowane przez model)
* Czy klient ma modyfikowane (cel "etykieta")
* Kategoria demograficznych (jednego ciągu, takich jak "młodych zawartość dla dorosłych" itp.)
* Liczba wizyt w ciągu ostatnich 5 dni.

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

Załadować te dane do `DataView` i trenowanie modelu, używając następującego kodu:

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
var trainData = mlContext.CreateStreamingDataView(churnData);

// Build the learning pipeline.
// In our case, we will one-hot encode the demographic category, and concatenate that with the number of visits.
// We apply our FastTree binary classifier to predict the 'HasChurned' label.

var pipeline = mlContext.Transforms.Categorical.OneHotEncoding("DemographicCategory")
    .Append(mlContext.Transforms.Concatenate("Features", "DemographicCategory", "LastVisits"))
    .Append(mlContext.BinaryClassification.Trainers.FastTree("HasChurned", "Features", numTrees: 20));

var model = pipeline.Fit(trainData);
```
