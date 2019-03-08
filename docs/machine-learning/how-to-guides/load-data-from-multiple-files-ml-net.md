---
title: Ładowanie danych z wielu plików, machine learning przetwarzania - strukturze ML.NET
description: Dowiedz się, jak ładowanie danych z wielu plików do użycia w modelu uczenia maszynowego, kompilowania, szkolenia i oceniania za pomocą platformy ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: fbf5e4b5ab9a1a686edb933bdec818fc532bbf42
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679027"
---
# <a name="load-data-from-multiple-files-for-machine-learning-processing---mlnet"></a><span data-ttu-id="7c521-103">Ładowanie danych z wielu plików, machine learning przetwarzania - strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="7c521-103">Load data from multiple files for machine learning processing - ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="7c521-104">W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="7c521-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="7c521-105">Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="7c521-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="7c521-106">Obecnie używasz w tym przykładzie porad i pokrewnych **strukturze ML.NET wersji 0.10**.</span><span class="sxs-lookup"><span data-stu-id="7c521-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="7c521-107">Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="7c521-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="7c521-108">Użyj `TextLoader`i określ tablicę plików `Read` metody.</span><span class="sxs-lookup"><span data-stu-id="7c521-108">Use the `TextLoader`, and specify an array of files to the `Read` method.</span></span> <span data-ttu-id="7c521-109">Pliki muszą mieć taką samą schematu (ten sam numer i typ kolumny):</span><span class="sxs-lookup"><span data-stu-id="7c521-109">The files must have the same schema (same number and type of columns):</span></span>

* [<span data-ttu-id="7c521-110">Przykład Plik1</span><span class="sxs-lookup"><span data-stu-id="7c521-110">Example file1</span></span>](https://github.com/dotnet/machinelearning/blob/e3a34ae6ae1b25ac96faa0317308703ce943ff95/test/data/adult.train)
* [<span data-ttu-id="7c521-111">Przykład plik2</span><span class="sxs-lookup"><span data-stu-id="7c521-111">Example file2</span></span>](https://github.com/dotnet/machinelearning/blob/e3a34ae6ae1b25ac96faa0317308703ce943ff95/test/data/adult.test)

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Create the reader: define the data columns and where to find them in the text file.
var reader = mlContext.Data.CreateTextLoader(
    columns: new TextLoader.Column[]
    {
        // A boolean column depicting the 'target label'.
        new TextLoader.Column("IsOver50k",DataKind.BL,0),
        // Three text columns.
        new TextLoader.Column("WorkClass",DataKind.TX,1),
        new TextLoader.Column("Education",DataKind.TX,2),
        new TextLoader.Column("MaritalStatus",DataKind.TX,3)
    },
    hasHeader: true
);

// Now read the files (remember though, readers are lazy, so the actual reading will happen when the data is accessed).
var data = reader.Read(exampleFile1, exampleFile2);
```