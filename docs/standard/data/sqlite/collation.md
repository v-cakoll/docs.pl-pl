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
# <a name="collation"></a><span data-ttu-id="98e8a-103">Sortowanie</span><span class="sxs-lookup"><span data-stu-id="98e8a-103">Collation</span></span>

<span data-ttu-id="98e8a-104">Kolejność sortowania jest używana przez program SQLite podczas porównywania wartości tekstowych, aby określić kolejność i równość.</span><span class="sxs-lookup"><span data-stu-id="98e8a-104">Collating sequences are used by SQLite when comparing TEXT values to determine order and equality.</span></span> <span data-ttu-id="98e8a-105">Można określić, które sortowanie ma być używane podczas tworzenia kolumn lub dla operacji na zapytania SQL.</span><span class="sxs-lookup"><span data-stu-id="98e8a-105">You can specify which collation to use when creating columns or per-operation in SQL queries.</span></span> <span data-ttu-id="98e8a-106">Program SQLite domyślnie zawiera trzy sekwencje sortowania.</span><span class="sxs-lookup"><span data-stu-id="98e8a-106">SQLite includes three collating sequences by default.</span></span>

| <span data-ttu-id="98e8a-107">Sortowanie</span><span class="sxs-lookup"><span data-stu-id="98e8a-107">Collation</span></span> | <span data-ttu-id="98e8a-108">Opis</span><span class="sxs-lookup"><span data-stu-id="98e8a-108">Description</span></span>                               |
| --------- | ----------------------------------------- |
| <span data-ttu-id="98e8a-109">RTRIM</span><span class="sxs-lookup"><span data-stu-id="98e8a-109">RTRIM</span></span>     | <span data-ttu-id="98e8a-110">Ignoruje końcowe odstępy</span><span class="sxs-lookup"><span data-stu-id="98e8a-110">Ignores trailing whitespace</span></span>               |
| <span data-ttu-id="98e8a-111">Nocase</span><span class="sxs-lookup"><span data-stu-id="98e8a-111">NOCASE</span></span>    | <span data-ttu-id="98e8a-112">Bez uwzględniania wielkości liter dla znaków ASCII A-Z</span><span class="sxs-lookup"><span data-stu-id="98e8a-112">Case-insensitive for ASCII characters A-Z</span></span> |
| <span data-ttu-id="98e8a-113">BINARNY</span><span class="sxs-lookup"><span data-stu-id="98e8a-113">BINARY</span></span>    | <span data-ttu-id="98e8a-114">Wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="98e8a-114">Case-sensitive.</span></span> <span data-ttu-id="98e8a-115">Porównuje bajty bezpośrednio</span><span class="sxs-lookup"><span data-stu-id="98e8a-115">Compares bytes directly</span></span>   |

## <a name="custom-collation"></a><span data-ttu-id="98e8a-116">Sortowanie niestandardowe</span><span class="sxs-lookup"><span data-stu-id="98e8a-116">Custom collation</span></span>

<span data-ttu-id="98e8a-117">Można również zdefiniować własne sekwencje sortowania lub zastąpić wbudowane przy użyciu polecenia <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>.</span><span class="sxs-lookup"><span data-stu-id="98e8a-117">You can also define your own collating sequences or override the built-in ones using <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>.</span></span> <span data-ttu-id="98e8a-118">W poniższym przykładzie przedstawiono przesłanianie sortowania nocase do obsługi znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="98e8a-118">The following example shows overriding the NOCASE collation to support Unicode characters.</span></span> <span data-ttu-id="98e8a-119">[Pełny przykładowy kod](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs) jest dostępny w serwisie GitHub.</span><span class="sxs-lookup"><span data-stu-id="98e8a-119">The [full sample code](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs) is available on GitHub.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a><span data-ttu-id="98e8a-120">Like — Operator</span><span class="sxs-lookup"><span data-stu-id="98e8a-120">Like operator</span></span>

<span data-ttu-id="98e8a-121">Operator LIKE w programie SQLite nie honoruje sortowania.</span><span class="sxs-lookup"><span data-stu-id="98e8a-121">The LIKE operator in SQLite doesn't honor collations.</span></span> <span data-ttu-id="98e8a-122">Domyślna implementacja ma tę samą semantykę co sortowanie nocase.</span><span class="sxs-lookup"><span data-stu-id="98e8a-122">The default implementation has the same semantics as the NOCASE collation.</span></span> <span data-ttu-id="98e8a-123">W przypadku znaków ASCII od A do Z jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="98e8a-123">It's only case-insensitive for the ASCII characters A through Z.</span></span>

<span data-ttu-id="98e8a-124">Można łatwo wprowadzić wielkość liter operatora LIKE, używając następującej instrukcji pragma:</span><span class="sxs-lookup"><span data-stu-id="98e8a-124">You can easily make the LIKE operator case-sensitive by using the following pragma statement:</span></span>

```sql
PRAGMA case_sensitive_like = 1
```

<span data-ttu-id="98e8a-125">Zobacz [funkcje zdefiniowane przez użytkownika](user-defined-functions.md) , aby uzyskać szczegółowe informacje na temat zastępowania implementacji operatora like.</span><span class="sxs-lookup"><span data-stu-id="98e8a-125">See [User-defined functions](user-defined-functions.md) for details on overriding the implementation of the LIKE operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="98e8a-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="98e8a-126">See also</span></span>

* [<span data-ttu-id="98e8a-127">Funkcje zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="98e8a-127">User-defined functions</span></span>](user-defined-functions.md)
* [<span data-ttu-id="98e8a-128">Składnia SQL</span><span class="sxs-lookup"><span data-stu-id="98e8a-128">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
