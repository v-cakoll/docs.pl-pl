---
title: Parametry
ms.date: 12/13/2019
description: Dowiedz się, jak używać parametrów SQL.
ms.openlocfilehash: 1d2f818ad392a919faedd785394de28a9c6f56c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400457"
---
# <a name="parameters"></a><span data-ttu-id="cc3a6-103">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc3a6-103">Parameters</span></span>

<span data-ttu-id="cc3a6-104">Parametry są używane do ochrony przed atakami iniekcji SQL.</span><span class="sxs-lookup"><span data-stu-id="cc3a6-104">Parameters are used to protect against SQL injection attacks.</span></span> <span data-ttu-id="cc3a6-105">Zamiast konkretyzować dane wejściowe użytkownika z instrukcjami SQL, należy użyć parametrów, aby upewnić się, że dane wejściowe są zawsze traktowane jako wartość literału i nigdy nie są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="cc3a6-105">Instead of concatenating user input with SQL statements, use parameters to ensure input is only ever treated as a literal value and never executed.</span></span> <span data-ttu-id="cc3a6-106">W SQLite parametry są zazwyczaj dozwolone w dowolnym miejscu literału jest dozwolone w instrukcjach SQL.</span><span class="sxs-lookup"><span data-stu-id="cc3a6-106">In SQLite, parameters are typically allowed anywhere a literal is allowed in SQL statements.</span></span>

<span data-ttu-id="cc3a6-107">Parametry można poprzedzać `:` `@`jednymi `$`, lub .</span><span class="sxs-lookup"><span data-stu-id="cc3a6-107">Parameters can be prefixed with either `:`, `@`, or `$`.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

<span data-ttu-id="cc3a6-108">Zobacz [Typy danych,](types.md) aby uzyskać szczegółowe informacje o sposobie zamapowania wartości .NET na wartości SQLite.</span><span class="sxs-lookup"><span data-stu-id="cc3a6-108">See [Data types](types.md) for details about how .NET values are mapped to SQLite values.</span></span>

## <a name="truncation"></a><span data-ttu-id="cc3a6-109">Obcinania</span><span class="sxs-lookup"><span data-stu-id="cc3a6-109">Truncation</span></span>

<span data-ttu-id="cc3a6-110">Właściwość <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> służy do obcinania wartości TEXT i BLOB.</span><span class="sxs-lookup"><span data-stu-id="cc3a6-110">Use the <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> property to truncate TEXT and BLOB values.</span></span>

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Length = 30;
```

## <a name="alternative-types"></a><span data-ttu-id="cc3a6-111">Typy alternatywne</span><span class="sxs-lookup"><span data-stu-id="cc3a6-111">Alternative types</span></span>

<span data-ttu-id="cc3a6-112">Czasami możesz chcieć użyć alternatywnego typu SQLite.</span><span class="sxs-lookup"><span data-stu-id="cc3a6-112">Sometimes, you may want to use an alternative SQLite type.</span></span> <span data-ttu-id="cc3a6-113">Należy to zrobić, ustawiając <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> właściwość.</span><span class="sxs-lookup"><span data-stu-id="cc3a6-113">Do this by setting the <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> property.</span></span>

<span data-ttu-id="cc3a6-114">Można użyć następujących mapowania typu alternatywnego.</span><span class="sxs-lookup"><span data-stu-id="cc3a6-114">The following alternative type mappings can be used.</span></span> <span data-ttu-id="cc3a6-115">Aby uzyskać domyślne mapowania, zobacz [Typy danych](types.md).</span><span class="sxs-lookup"><span data-stu-id="cc3a6-115">For the default mappings, see [Data types](types.md).</span></span>

| <span data-ttu-id="cc3a6-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="cc3a6-116">Value</span></span>          | <span data-ttu-id="cc3a6-117">Typ sqlite</span><span class="sxs-lookup"><span data-stu-id="cc3a6-117">SqliteType</span></span> | <span data-ttu-id="cc3a6-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cc3a6-118">Remarks</span></span>          |
| -------------- | ---------- | ---------------- |
| <span data-ttu-id="cc3a6-119">Char</span><span class="sxs-lookup"><span data-stu-id="cc3a6-119">Char</span></span>           | <span data-ttu-id="cc3a6-120">Liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="cc3a6-120">Integer</span></span>    | <span data-ttu-id="cc3a6-121">UTF-16</span><span class="sxs-lookup"><span data-stu-id="cc3a6-121">UTF-16</span></span>           |
| <span data-ttu-id="cc3a6-122">DateTime</span><span class="sxs-lookup"><span data-stu-id="cc3a6-122">DateTime</span></span>       | <span data-ttu-id="cc3a6-123">Rzeczywiste</span><span class="sxs-lookup"><span data-stu-id="cc3a6-123">Real</span></span>       | <span data-ttu-id="cc3a6-124">Wartość dnia juliańska</span><span class="sxs-lookup"><span data-stu-id="cc3a6-124">Julian day value</span></span> |
| <span data-ttu-id="cc3a6-125">Datetimeoffset</span><span class="sxs-lookup"><span data-stu-id="cc3a6-125">DateTimeOffset</span></span> | <span data-ttu-id="cc3a6-126">Rzeczywiste</span><span class="sxs-lookup"><span data-stu-id="cc3a6-126">Real</span></span>       | <span data-ttu-id="cc3a6-127">Wartość dnia juliańska</span><span class="sxs-lookup"><span data-stu-id="cc3a6-127">Julian day value</span></span> |
| <span data-ttu-id="cc3a6-128">Guid (identyfikator GUID)</span><span class="sxs-lookup"><span data-stu-id="cc3a6-128">Guid</span></span>           | <span data-ttu-id="cc3a6-129">Obiekt blob</span><span class="sxs-lookup"><span data-stu-id="cc3a6-129">Blob</span></span>       |                  |
| <span data-ttu-id="cc3a6-130">przedział_czasu</span><span class="sxs-lookup"><span data-stu-id="cc3a6-130">TimeSpan</span></span>       | <span data-ttu-id="cc3a6-131">Rzeczywiste</span><span class="sxs-lookup"><span data-stu-id="cc3a6-131">Real</span></span>       | <span data-ttu-id="cc3a6-132">W dniach</span><span class="sxs-lookup"><span data-stu-id="cc3a6-132">In days</span></span>          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a><span data-ttu-id="cc3a6-133">Parametry wyjściowe</span><span class="sxs-lookup"><span data-stu-id="cc3a6-133">Output parameters</span></span>

<span data-ttu-id="cc3a6-134">SQLite nie obsługuje parametrów wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="cc3a6-134">SQLite doesn't support output parameters.</span></span> <span data-ttu-id="cc3a6-135">Zamiast tego zwraca wartości w wynikach kwerendy.</span><span class="sxs-lookup"><span data-stu-id="cc3a6-135">Return values in the query results instead.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc3a6-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc3a6-136">See also</span></span>

* [<span data-ttu-id="cc3a6-137">Typy danych</span><span class="sxs-lookup"><span data-stu-id="cc3a6-137">Data types</span></span>](types.md)
