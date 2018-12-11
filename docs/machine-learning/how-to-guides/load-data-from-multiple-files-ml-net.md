---
title: Ładowanie danych z wielu plików, machine learning przetwarzania - strukturze ML.NET
description: Dowiedz się, jak ładowanie danych z wielu plików do użycia w modelu uczenia maszynowego, kompilowania, szkolenia i oceniania za pomocą platformy ML.NET
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: c9b34bd6bcbac62e9f9c33226f5d0feb41168392
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150735"
---
# <a name="load-data-from-multiple-files-for-machine-learning-processing---mlnet"></a><span data-ttu-id="a6ca7-103">Ładowanie danych z wielu plików, machine learning przetwarzania - strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="a6ca7-103">Load data from multiple files for machine learning processing - ML.NET</span></span>

<span data-ttu-id="a6ca7-104">Użyj `TextLoader`i określ tablicę plików `Read` metody.</span><span class="sxs-lookup"><span data-stu-id="a6ca7-104">Use the `TextLoader`, and specify an array of files to the `Read` method.</span></span> <span data-ttu-id="a6ca7-105">Pliki muszą mieć taką samą schematu (ten sam numer i typ kolumny):</span><span class="sxs-lookup"><span data-stu-id="a6ca7-105">The files must have the same schema (same number and type of columns):</span></span>

* [<span data-ttu-id="a6ca7-106">Przykład Plik1</span><span class="sxs-lookup"><span data-stu-id="a6ca7-106">Example file1</span></span>](https://github.com/dotnet/machinelearning/blob/e3a34ae6ae1b25ac96faa0317308703ce943ff95/test/data/adult.train)
* [<span data-ttu-id="a6ca7-107">Przykład plik2</span><span class="sxs-lookup"><span data-stu-id="a6ca7-107">Example file2</span></span>](https://github.com/dotnet/machinelearning/blob/e3a34ae6ae1b25ac96faa0317308703ce943ff95/test/data/adult.test)

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Create the reader: define the data columns and where to find them in the text file.
var reader = mlContext.Data.TextReader(new TextLoader.Arguments
{
    Column = new[] {
        // A boolean column depicting the 'label'.
        new TextLoader.Column("IsOver50k", DataKind.BL, 0),
        // Three text columns.
        new TextLoader.Column("Workclass", DataKind.TX, 1),
        new TextLoader.Column("Education", DataKind.TX, 2),
        new TextLoader.Column("MaritalStatus", DataKind.TX, 3)
    },
    // First line of the file is a header, not a data row.
    HasHeader = true
});

var data = reader.Read(exampleFile1, exampleFile2);
```