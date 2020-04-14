---
title: Sortowanie
ms.date: 12/13/2019
description: Dowiedz się, jak utworzyć niestandardową sekwencję sortowania.
ms.openlocfilehash: 9879846cc191a62c4cb47a0fbaa47c59153ba61c
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242975"
---
# <a name="collation"></a><span data-ttu-id="0434a-103">Sortowanie</span><span class="sxs-lookup"><span data-stu-id="0434a-103">Collation</span></span>

<span data-ttu-id="0434a-104">Sekwencje sortowania są używane przez SQLite podczas porównywania wartości TEXT w celu określenia kolejności i równości.</span><span class="sxs-lookup"><span data-stu-id="0434a-104">Collating sequences are used by SQLite when comparing TEXT values to determine order and equality.</span></span> <span data-ttu-id="0434a-105">Można określić, które sortowanie ma być używane podczas tworzenia kolumn lub operacji na operację w kwerendach SQL.</span><span class="sxs-lookup"><span data-stu-id="0434a-105">You can specify which collation to use when creating columns or per-operation in SQL queries.</span></span> <span data-ttu-id="0434a-106">SQLite zawiera domyślnie trzy sekwencje sortowania.</span><span class="sxs-lookup"><span data-stu-id="0434a-106">SQLite includes three collating sequences by default.</span></span>

| <span data-ttu-id="0434a-107">Sortowanie</span><span class="sxs-lookup"><span data-stu-id="0434a-107">Collation</span></span> | <span data-ttu-id="0434a-108">Opis</span><span class="sxs-lookup"><span data-stu-id="0434a-108">Description</span></span>                               |
| --------- | ----------------------------------------- |
| <span data-ttu-id="0434a-109">RTRIM</span><span class="sxs-lookup"><span data-stu-id="0434a-109">RTRIM</span></span>     | <span data-ttu-id="0434a-110">Ignoruje końcowe odstępy</span><span class="sxs-lookup"><span data-stu-id="0434a-110">Ignores trailing whitespace</span></span>               |
| <span data-ttu-id="0434a-111">NOCASE (NOCASE)</span><span class="sxs-lookup"><span data-stu-id="0434a-111">NOCASE</span></span>    | <span data-ttu-id="0434a-112">Bez uwzględniania wielkości liter dla znaków ASCII A-Z</span><span class="sxs-lookup"><span data-stu-id="0434a-112">Case-insensitive for ASCII characters A-Z</span></span> |
| <span data-ttu-id="0434a-113">Binarnym</span><span class="sxs-lookup"><span data-stu-id="0434a-113">BINARY</span></span>    | <span data-ttu-id="0434a-114">Rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="0434a-114">Case-sensitive.</span></span> <span data-ttu-id="0434a-115">Bezpośrednio porównuje bajty</span><span class="sxs-lookup"><span data-stu-id="0434a-115">Compares bytes directly</span></span>   |

## <a name="custom-collation"></a><span data-ttu-id="0434a-116">Sortowanie niestandardowe</span><span class="sxs-lookup"><span data-stu-id="0434a-116">Custom collation</span></span>

<span data-ttu-id="0434a-117">Można również zdefiniować własne sekwencje sortowania lub zastąpić wbudowane za pomocą programu <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>.</span><span class="sxs-lookup"><span data-stu-id="0434a-117">You can also define your own collating sequences or override the built-in ones using <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>.</span></span> <span data-ttu-id="0434a-118">Poniższy przykład przedstawia zastępowanie sortowania NOCASE do obsługi znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="0434a-118">The following example shows overriding the NOCASE collation to support Unicode characters.</span></span> <span data-ttu-id="0434a-119">[Pełny przykładowy kod](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs) jest dostępny w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="0434a-119">The [full sample code](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs) is available on GitHub.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a><span data-ttu-id="0434a-120">Podobnie jak operator</span><span class="sxs-lookup"><span data-stu-id="0434a-120">Like operator</span></span>

<span data-ttu-id="0434a-121">Operator LIKE w SQLite nie honoruje sortowania.</span><span class="sxs-lookup"><span data-stu-id="0434a-121">The LIKE operator in SQLite doesn't honor collations.</span></span> <span data-ttu-id="0434a-122">Domyślna implementacja ma taką samą semantycę jak sortowanie NOCASE.</span><span class="sxs-lookup"><span data-stu-id="0434a-122">The default implementation has the same semantics as the NOCASE collation.</span></span> <span data-ttu-id="0434a-123">Jest to tylko niewrażliwe na litery dla znaków ASCII od A do Z.</span><span class="sxs-lookup"><span data-stu-id="0434a-123">It's only case-insensitive for the ASCII characters A through Z.</span></span>

<span data-ttu-id="0434a-124">Można łatwo sprawić, aby przypadek operatora LIKE był rozróżniany przy użyciu następującej instrukcji pragma:</span><span class="sxs-lookup"><span data-stu-id="0434a-124">You can easily make the LIKE operator case-sensitive by using the following pragma statement:</span></span>

```sql
PRAGMA case_sensitive_like = 1
```

<span data-ttu-id="0434a-125">Zobacz [funkcje zdefiniowane przez użytkownika,](user-defined-functions.md) aby uzyskać szczegółowe informacje na temat zastępowania implementacji operatora LIKE.</span><span class="sxs-lookup"><span data-stu-id="0434a-125">See [User-defined functions](user-defined-functions.md) for details on overriding the implementation of the LIKE operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="0434a-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0434a-126">See also</span></span>

* [<span data-ttu-id="0434a-127">Funkcje zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="0434a-127">User-defined functions</span></span>](user-defined-functions.md)
* [<span data-ttu-id="0434a-128">Składnia SQL</span><span class="sxs-lookup"><span data-stu-id="0434a-128">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
