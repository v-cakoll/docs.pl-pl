---
title: Bazy danych w pamięci
ms.date: 12/13/2019
description: Dowiedz się, jak korzystać z baz danych SQLite w pamięci.
ms.openlocfilehash: 408c81f538e27dcfffad20db74b7809912b7905f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391211"
---
# <a name="in-memory-databases"></a><span data-ttu-id="9e219-103">Bazy danych w pamięci</span><span class="sxs-lookup"><span data-stu-id="9e219-103">In-memory databases</span></span>

<span data-ttu-id="9e219-104">Bazy danych SQLite w pamięci są bazami danych przechowywanymi w całości w pamięci, a nie na dysku.</span><span class="sxs-lookup"><span data-stu-id="9e219-104">SQLite in-memory databases are databases stored entirely in memory, not on disk.</span></span> <span data-ttu-id="9e219-105">Użyj specjalnej nazwy pliku `:memory:` źródła danych, aby utworzyć bazę danych w pamięci.</span><span class="sxs-lookup"><span data-stu-id="9e219-105">Use the special data source filename `:memory:` to create an in-memory database.</span></span> <span data-ttu-id="9e219-106">Po zamknięciu połączenia baza danych jest usuwana.</span><span class="sxs-lookup"><span data-stu-id="9e219-106">When the connection is closed, the database is deleted.</span></span> <span data-ttu-id="9e219-107">Podczas `:memory:`korzystania z tego każde połączenie tworzy własną bazę danych.</span><span class="sxs-lookup"><span data-stu-id="9e219-107">When using `:memory:`, each connection creates its own database.</span></span>

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a><span data-ttu-id="9e219-108">Bazy danych w pamięci, które można udostępnić</span><span class="sxs-lookup"><span data-stu-id="9e219-108">Shareable in-memory databases</span></span>

<span data-ttu-id="9e219-109">Bazy danych w pamięci mogą być współużytkowane przez wiele połączeń przy użyciu `Mode=Memory` i `Cache=Shared` w ciągu połączenia.</span><span class="sxs-lookup"><span data-stu-id="9e219-109">In-memory databases can be shared between multiple connections by using `Mode=Memory` and `Cache=Shared` in the connection string.</span></span> <span data-ttu-id="9e219-110">Słowo `Data Source` kluczowe jest używane do nadawanie nazwy w bazie danych w pamięci.</span><span class="sxs-lookup"><span data-stu-id="9e219-110">The `Data Source` keyword is used to give the in-memory database a name.</span></span> <span data-ttu-id="9e219-111">Parametry połączenia o tej samej nazwie będą uzyskiwać dostęp do tej samej bazy danych w pamięci.</span><span class="sxs-lookup"><span data-stu-id="9e219-111">Connection strings using the same name will access the same in-memory database.</span></span> <span data-ttu-id="9e219-112">Baza danych będzie się powtarzać tak długo, jak co najmniej jedno połączenie z nią pozostaje otwarte.</span><span class="sxs-lookup"><span data-stu-id="9e219-112">The database persists as long as at least one connection to it remains open.</span></span> <span data-ttu-id="9e219-113">[Przykład](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) pokazujący to jest dostępny w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="9e219-113">A [sample](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) demonstrating this is available on GitHub.</span></span>

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
