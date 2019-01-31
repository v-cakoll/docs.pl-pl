---
title: Ładowanie danych z pliku tekstowego, machine learning przetwarzania - strukturze ML.NET
description: Dowiedz się, jak załadować dane z pliku tekstowego do użycia w modelu uczenia maszynowego, kompilowania, szkolenia i oceniania za pomocą platformy ML.NET
ms.date: 01/29/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 6a8f74cc5324050ca94e60592f083c35afc68377
ms.sourcegitcommit: dcc8feeff4718664087747529638ec9b47e65234
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/31/2019
ms.locfileid: "55479675"
---
# <a name="load-data-from-a-text-file-for-machine-learning-processing---mlnet"></a><span data-ttu-id="59216-103">Ładowanie danych z pliku tekstowego, machine learning przetwarzania - strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="59216-103">Load data from a text file for machine learning processing - ML.NET</span></span>

<span data-ttu-id="59216-104">`TextLoader` Służy do ładowania danych z plików tekstowych.</span><span class="sxs-lookup"><span data-stu-id="59216-104">`TextLoader` is used to load data from text files.</span></span> <span data-ttu-id="59216-105">Należy określić kolumny danych, ich typy i ich lokalizacji w pliku tekstowym.</span><span class="sxs-lookup"><span data-stu-id="59216-105">You need to specify the data columns, their types, and their location in the text file.</span></span>

<span data-ttu-id="59216-106">Należy pamiętać, że doskonale dopuszczalne do odczytu niektórych kolumn w pliku lub przeczytaj tę samą kolumnę wiele razy.</span><span class="sxs-lookup"><span data-stu-id="59216-106">Note that it's perfectly acceptable to read some columns of a file, or read the same column multiple times.</span></span>

<span data-ttu-id="59216-107">[Przykładowy plik](https://github.com/dotnet/machinelearning/blob/master/test/data/adult.tiny.with-schema.txt):</span><span class="sxs-lookup"><span data-stu-id="59216-107">[Example file](https://github.com/dotnet/machinelearning/blob/master/test/data/adult.tiny.with-schema.txt):</span></span>

```console
Label   Workclass   education   marital-status
0   Private 11th    Never-married
0   Private HS-grad Married-civ-spouse
1   Local-gov   Assoc-acdm  Married-civ-spouse
1   Private Some-college    Married-civ-spouse
```

<span data-ttu-id="59216-108">Aby załadować dane z pliku tekstowego:</span><span class="sxs-lookup"><span data-stu-id="59216-108">To load the data from a text file:</span></span>

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Create the reader: define the data columns and where to find them in the text file.
var reader = mlContext.Data.CreateTextReader(
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

// Now read the file (remember though, readers are lazy, so the actual reading will happen when the data is accessed).
var data = reader.Read(dataPath);
```