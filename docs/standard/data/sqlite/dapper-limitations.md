---
title: Ograniczenia Dapper
ms.date: 12/13/2019
description: W tym artykule opisano niektóre z ograniczeń, które można napotkać podczas korzystania z programu Dapper.
ms.openlocfilehash: 396507f25f591a9ab5c3bb07c0af6fd8d175e4ea
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901210"
---
# <a name="dapper-limitations"></a><span data-ttu-id="437a0-103">Ograniczenia Dapper</span><span class="sxs-lookup"><span data-stu-id="437a0-103">Dapper limitations</span></span>

<span data-ttu-id="437a0-104">Istnieje kilka ograniczeń, które należy wziąć pod uwagę podczas korzystania z programu Microsoft. Data. sqlite z [Dapper](https://stackexchange.github.io/Dapper/).</span><span class="sxs-lookup"><span data-stu-id="437a0-104">There are a few limitations you should be aware of when using Microsoft.Data.Sqlite with [Dapper](https://stackexchange.github.io/Dapper/).</span></span>

## <a name="parameters"></a><span data-ttu-id="437a0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="437a0-105">Parameters</span></span>

<span data-ttu-id="437a0-106">W nazwach parametrów SQLite jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="437a0-106">SQLite parameter names are case-sensitive.</span></span> <span data-ttu-id="437a0-107">Upewnij się, że nazwy parametrów używane w programie SQL pasują do wielkości liter we właściwościach obiektu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="437a0-107">Ensure that the parameter names used in SQL match the case of the anonymous object's properties.</span></span> <span data-ttu-id="437a0-108">Problem [#18861](https://github.com/dotnet/efcore/issues/18861) poprawi to środowisko.</span><span class="sxs-lookup"><span data-stu-id="437a0-108">Issue [#18861](https://github.com/dotnet/efcore/issues/18861) would improve this experience.</span></span>

<span data-ttu-id="437a0-109">Dapper oczekuje również parametrów do użycia `@` prefiksu.</span><span class="sxs-lookup"><span data-stu-id="437a0-109">Dapper also expects parameters to use the `@` prefix.</span></span> <span data-ttu-id="437a0-110">Inne prefiksy nie będą działały.</span><span class="sxs-lookup"><span data-stu-id="437a0-110">Other prefixes won't work.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_Parameter)]

## <a name="data-types"></a><span data-ttu-id="437a0-111">Typy danych</span><span class="sxs-lookup"><span data-stu-id="437a0-111">Data types</span></span>

<span data-ttu-id="437a0-112">Dapper odczytuje wartości za pomocą indeksatora SqliteDataReader.</span><span class="sxs-lookup"><span data-stu-id="437a0-112">Dapper reads values using the SqliteDataReader indexer.</span></span> <span data-ttu-id="437a0-113">Zwracanym typem tego indeksatora jest Object, co oznacza, że zwróci tylko wartości Long, Double, String lub Byte [].</span><span class="sxs-lookup"><span data-stu-id="437a0-113">The return type of this indexer is object, which means it will only ever return long, double, string, or byte[] values.</span></span> <span data-ttu-id="437a0-114">Aby uzyskać więcej informacji, zobacz [typy danych](types.md).</span><span class="sxs-lookup"><span data-stu-id="437a0-114">For more information, see [Data types](types.md).</span></span> <span data-ttu-id="437a0-115">Dapper obsługuje większość konwersji między tymi i innymi typami pierwotnymi.</span><span class="sxs-lookup"><span data-stu-id="437a0-115">Dapper handles most conversions between these and other primitive types.</span></span> <span data-ttu-id="437a0-116">Niestety, nie obsługuje `DateTimeOffset`, `Guid`, ani. `TimeSpan`</span><span class="sxs-lookup"><span data-stu-id="437a0-116">Unfortunately, it doesn't handle `DateTimeOffset`, `Guid`, or `TimeSpan`.</span></span> <span data-ttu-id="437a0-117">Utwórz programy obsługi typów, jeśli chcesz używać tych typów w wynikach.</span><span class="sxs-lookup"><span data-stu-id="437a0-117">Create type handlers if you want to use these types in your results.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_TypeHandlers)]

<span data-ttu-id="437a0-118">Nie zapomnij dodać programów obsługi typu przed wykonaniem zapytania.</span><span class="sxs-lookup"><span data-stu-id="437a0-118">Don't forget to add the type handlers before querying.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_AddTypeHandlers)]

## <a name="see-also"></a><span data-ttu-id="437a0-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="437a0-119">See also</span></span>

* [<span data-ttu-id="437a0-120">Typy danych</span><span class="sxs-lookup"><span data-stu-id="437a0-120">Data types</span></span>](types.md)
* [<span data-ttu-id="437a0-121">Ograniczenia asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="437a0-121">Async limitations</span></span>](async.md)
