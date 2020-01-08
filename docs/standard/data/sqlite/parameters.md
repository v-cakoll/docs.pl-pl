---
title: Parametry
ms.date: 12/13/2019
description: Dowiedz się, jak używać parametrów SQL.
ms.openlocfilehash: 1d2f818ad392a919faedd785394de28a9c6f56c3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447189"
---
# <a name="parameters"></a><span data-ttu-id="07320-103">Parametry</span><span class="sxs-lookup"><span data-stu-id="07320-103">Parameters</span></span>

<span data-ttu-id="07320-104">Parametry są używane do ochrony przed atakami polegającymi na iniekcji SQL.</span><span class="sxs-lookup"><span data-stu-id="07320-104">Parameters are used to protect against SQL injection attacks.</span></span> <span data-ttu-id="07320-105">Zamiast łączyć dane wejściowe użytkownika z instrukcjami SQL, użyj parametrów, aby upewnić się, że dane wejściowe są kiedykolwiek traktowane jako wartość literału, a nigdy nie wykonane.</span><span class="sxs-lookup"><span data-stu-id="07320-105">Instead of concatenating user input with SQL statements, use parameters to ensure input is only ever treated as a literal value and never executed.</span></span> <span data-ttu-id="07320-106">W przypadku oprogramowania SQLite parametry są zwykle dozwolone wszędzie tam, gdzie literał jest dozwolony w instrukcjach SQL.</span><span class="sxs-lookup"><span data-stu-id="07320-106">In SQLite, parameters are typically allowed anywhere a literal is allowed in SQL statements.</span></span>

<span data-ttu-id="07320-107">Parametry mogą być poprzedzone `:`, `@`lub `$`.</span><span class="sxs-lookup"><span data-stu-id="07320-107">Parameters can be prefixed with either `:`, `@`, or `$`.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

<span data-ttu-id="07320-108">Aby uzyskać szczegółowe informacje o tym, jak wartości .NET są mapowane na wartości oprogramowania SQLite, zobacz [typy danych](types.md) .</span><span class="sxs-lookup"><span data-stu-id="07320-108">See [Data types](types.md) for details about how .NET values are mapped to SQLite values.</span></span>

## <a name="truncation"></a><span data-ttu-id="07320-109">Obcięcie</span><span class="sxs-lookup"><span data-stu-id="07320-109">Truncation</span></span>

<span data-ttu-id="07320-110">Użyj właściwości <xref:Microsoft.Data.Sqlite.SqliteParameter.Size>, aby obciąć wartości tekstowe i obiekty BLOB.</span><span class="sxs-lookup"><span data-stu-id="07320-110">Use the <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> property to truncate TEXT and BLOB values.</span></span>

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Length = 30;
```

## <a name="alternative-types"></a><span data-ttu-id="07320-111">Typy alternatywne</span><span class="sxs-lookup"><span data-stu-id="07320-111">Alternative types</span></span>

<span data-ttu-id="07320-112">Czasami warto użyć alternatywnego typu oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="07320-112">Sometimes, you may want to use an alternative SQLite type.</span></span> <span data-ttu-id="07320-113">W tym celu należy ustawić właściwość <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType>.</span><span class="sxs-lookup"><span data-stu-id="07320-113">Do this by setting the <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> property.</span></span>

<span data-ttu-id="07320-114">Można użyć następujących mapowań alternatywnego typu.</span><span class="sxs-lookup"><span data-stu-id="07320-114">The following alternative type mappings can be used.</span></span> <span data-ttu-id="07320-115">Aby uzyskać domyślne mapowania, zobacz [typy danych](types.md).</span><span class="sxs-lookup"><span data-stu-id="07320-115">For the default mappings, see [Data types](types.md).</span></span>

| <span data-ttu-id="07320-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="07320-116">Value</span></span>          | <span data-ttu-id="07320-117">Sqlitetype</span><span class="sxs-lookup"><span data-stu-id="07320-117">SqliteType</span></span> | <span data-ttu-id="07320-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="07320-118">Remarks</span></span>          |
| -------------- | ---------- | ---------------- |
| <span data-ttu-id="07320-119">Char</span><span class="sxs-lookup"><span data-stu-id="07320-119">Char</span></span>           | <span data-ttu-id="07320-120">Liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="07320-120">Integer</span></span>    | <span data-ttu-id="07320-121">UTF-16</span><span class="sxs-lookup"><span data-stu-id="07320-121">UTF-16</span></span>           |
| <span data-ttu-id="07320-122">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="07320-122">DateTime</span></span>       | <span data-ttu-id="07320-123">Rzeczywiste</span><span class="sxs-lookup"><span data-stu-id="07320-123">Real</span></span>       | <span data-ttu-id="07320-124">Wartość w postaci ciągu juliańskim</span><span class="sxs-lookup"><span data-stu-id="07320-124">Julian day value</span></span> |
| <span data-ttu-id="07320-125">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="07320-125">DateTimeOffset</span></span> | <span data-ttu-id="07320-126">Rzeczywiste</span><span class="sxs-lookup"><span data-stu-id="07320-126">Real</span></span>       | <span data-ttu-id="07320-127">Wartość w postaci ciągu juliańskim</span><span class="sxs-lookup"><span data-stu-id="07320-127">Julian day value</span></span> |
| <span data-ttu-id="07320-128">Guid</span><span class="sxs-lookup"><span data-stu-id="07320-128">Guid</span></span>           | <span data-ttu-id="07320-129">Obiekt blob</span><span class="sxs-lookup"><span data-stu-id="07320-129">Blob</span></span>       |                  |
| <span data-ttu-id="07320-130">przedział_czasu</span><span class="sxs-lookup"><span data-stu-id="07320-130">TimeSpan</span></span>       | <span data-ttu-id="07320-131">Rzeczywiste</span><span class="sxs-lookup"><span data-stu-id="07320-131">Real</span></span>       | <span data-ttu-id="07320-132">W dniach</span><span class="sxs-lookup"><span data-stu-id="07320-132">In days</span></span>          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a><span data-ttu-id="07320-133">Parametry wyjściowe</span><span class="sxs-lookup"><span data-stu-id="07320-133">Output parameters</span></span>

<span data-ttu-id="07320-134">Produkt SQLite nie obsługuje parametrów wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="07320-134">SQLite doesn't support output parameters.</span></span> <span data-ttu-id="07320-135">Zamiast tego Zwróć wartości w wynikach zapytania.</span><span class="sxs-lookup"><span data-stu-id="07320-135">Return values in the query results instead.</span></span>

## <a name="see-also"></a><span data-ttu-id="07320-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07320-136">See also</span></span>

* [<span data-ttu-id="07320-137">Typy danych</span><span class="sxs-lookup"><span data-stu-id="07320-137">Data types</span></span>](types.md)
