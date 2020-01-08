---
title: Sortowanie
ms.date: 12/13/2019
description: Dowiedz się, jak utworzyć niestandardową sekwencję sortowania.
ms.openlocfilehash: 0942ad4523a149ad74321cbe0f63021f53303579
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447028"
---
# <a name="collation"></a><span data-ttu-id="9d0ad-103">Sortowanie</span><span class="sxs-lookup"><span data-stu-id="9d0ad-103">Collation</span></span>

<span data-ttu-id="9d0ad-104">Kolejność sortowania jest używana przez program SQLite podczas porównywania wartości tekstowych, aby określić kolejność i równość.</span><span class="sxs-lookup"><span data-stu-id="9d0ad-104">Collating sequences are used by SQLite when comparing TEXT values to determine order and equality.</span></span> <span data-ttu-id="9d0ad-105">Można określić, które sortowanie ma być używane podczas tworzenia kolumn lub dla operacji na zapytania SQL.</span><span class="sxs-lookup"><span data-stu-id="9d0ad-105">You can specify which collation to use when creating columns or per-operation in SQL queries.</span></span> <span data-ttu-id="9d0ad-106">Program SQLite domyślnie zawiera trzy sekwencje sortowania.</span><span class="sxs-lookup"><span data-stu-id="9d0ad-106">SQLite includes three collating sequences by default.</span></span>

| <span data-ttu-id="9d0ad-107">Sortowanie</span><span class="sxs-lookup"><span data-stu-id="9d0ad-107">Collation</span></span> | <span data-ttu-id="9d0ad-108">Opis</span><span class="sxs-lookup"><span data-stu-id="9d0ad-108">Description</span></span>                               |
| --------- | ----------------------------------------- |
| <span data-ttu-id="9d0ad-109">RTRIM</span><span class="sxs-lookup"><span data-stu-id="9d0ad-109">RTRIM</span></span>     | <span data-ttu-id="9d0ad-110">Ignoruje końcowe odstępy</span><span class="sxs-lookup"><span data-stu-id="9d0ad-110">Ignores trailing whitespace</span></span>               |
| <span data-ttu-id="9d0ad-111">Nocase</span><span class="sxs-lookup"><span data-stu-id="9d0ad-111">NOCASE</span></span>    | <span data-ttu-id="9d0ad-112">Bez uwzględniania wielkości liter dla znaków ASCII A-Z</span><span class="sxs-lookup"><span data-stu-id="9d0ad-112">Case-insensitive for ASCII characters A-Z</span></span> |
| <span data-ttu-id="9d0ad-113">BINARY</span><span class="sxs-lookup"><span data-stu-id="9d0ad-113">BINARY</span></span>    | <span data-ttu-id="9d0ad-114">Wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="9d0ad-114">Case-sensitive.</span></span> <span data-ttu-id="9d0ad-115">Porównuje bajty bezpośrednio</span><span class="sxs-lookup"><span data-stu-id="9d0ad-115">Compares bytes directly</span></span>   |

## <a name="custom-collation"></a><span data-ttu-id="9d0ad-116">Sortowanie niestandardowe</span><span class="sxs-lookup"><span data-stu-id="9d0ad-116">Custom collation</span></span>

<span data-ttu-id="9d0ad-117">Można także definiować własne sekwencje sortowania lub przesłonić wbudowane przy użyciu <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>.</span><span class="sxs-lookup"><span data-stu-id="9d0ad-117">You can also define your own collating sequences or override the built-in ones using <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>.</span></span> <span data-ttu-id="9d0ad-118">W poniższym przykładzie przedstawiono przesłanianie sortowania nocase do obsługi znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="9d0ad-118">The following example shows overriding the NOCASE collation to support Unicode characters.</span></span> <span data-ttu-id="9d0ad-119">[Pełny przykładowy kod](https://github.com/dotnet/samples/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs) jest dostępny w serwisie GitHub.</span><span class="sxs-lookup"><span data-stu-id="9d0ad-119">The [full sample code](https://github.com/dotnet/samples/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs) is available on GitHub.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a><span data-ttu-id="9d0ad-120">Like — Operator</span><span class="sxs-lookup"><span data-stu-id="9d0ad-120">Like operator</span></span>

<span data-ttu-id="9d0ad-121">Operator LIKE w programie SQLite nie honoruje sortowania.</span><span class="sxs-lookup"><span data-stu-id="9d0ad-121">The LIKE operator in SQLite doesn't honor collations.</span></span> <span data-ttu-id="9d0ad-122">Domyślna implementacja ma tę samą semantykę co sortowanie nocase.</span><span class="sxs-lookup"><span data-stu-id="9d0ad-122">The default implementation has the same semantics as the NOCASE collation.</span></span> <span data-ttu-id="9d0ad-123">W przypadku znaków ASCII od A do Z jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="9d0ad-123">It's only case-insensitive for the ASCII characters A through Z.</span></span>

<span data-ttu-id="9d0ad-124">Można łatwo wprowadzić wielkość liter operatora LIKE, używając następującej instrukcji pragma:</span><span class="sxs-lookup"><span data-stu-id="9d0ad-124">You can easily make the LIKE operator case-sensitive by using the following pragma statement:</span></span>

```sql
PRAGMA case_sensitive_like = 0
```

<span data-ttu-id="9d0ad-125">Zobacz [funkcje zdefiniowane przez użytkownika](user-defined-functions.md) , aby uzyskać szczegółowe informacje na temat zastępowania implementacji operatora like.</span><span class="sxs-lookup"><span data-stu-id="9d0ad-125">See [User-defined functions](user-defined-functions.md) for details on overriding the implementation of the LIKE operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d0ad-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d0ad-126">See also</span></span>

* [<span data-ttu-id="9d0ad-127">Funkcje zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="9d0ad-127">User-defined functions</span></span>](user-defined-functions.md)
* [<span data-ttu-id="9d0ad-128">Składnia języka SQL</span><span class="sxs-lookup"><span data-stu-id="9d0ad-128">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
