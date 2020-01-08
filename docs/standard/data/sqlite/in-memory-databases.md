---
title: Bazy danych w pamięci
ms.date: 12/13/2019
description: Dowiedz się, jak używać baz danych programu SQLite w pamięci.
ms.openlocfilehash: b125ff5aa4128bd4c3ff558c5573b7d11802090a
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447245"
---
# <a name="in-memory-databases"></a><span data-ttu-id="91565-103">Bazy danych w pamięci</span><span class="sxs-lookup"><span data-stu-id="91565-103">In-memory databases</span></span>

<span data-ttu-id="91565-104">Bazy danych w pamięci programu SQLite są bazami danych przechowywanymi w całości w pamięci, a nie na dysku.</span><span class="sxs-lookup"><span data-stu-id="91565-104">SQLite in-memory databases are databases stored entirely in memory, not on disk.</span></span> <span data-ttu-id="91565-105">Użyj specjalnej nazwy pliku źródła danych `:memory:`, aby utworzyć bazę danych w pamięci.</span><span class="sxs-lookup"><span data-stu-id="91565-105">Use the special data source filename `:memory:` to create an in-memory database.</span></span> <span data-ttu-id="91565-106">Po zamknięciu połączenia baza danych zostanie usunięta.</span><span class="sxs-lookup"><span data-stu-id="91565-106">When the connection is closed, the database is deleted.</span></span> <span data-ttu-id="91565-107">W przypadku korzystania z `:memory:`każde połączenie tworzy własną bazę danych.</span><span class="sxs-lookup"><span data-stu-id="91565-107">When using `:memory:`, each connection creates its own database.</span></span>

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a><span data-ttu-id="91565-108">Współużytkowane bazy danych w pamięci</span><span class="sxs-lookup"><span data-stu-id="91565-108">Shareable in-memory databases</span></span>

<span data-ttu-id="91565-109">Bazy danych znajdujące się w pamięci mogą być współużytkowane przez wiele połączeń przy użyciu `Mode=Memory` i `Cache=Shared` w parametrach połączenia.</span><span class="sxs-lookup"><span data-stu-id="91565-109">In-memory databases can be shared between multiple connections by using `Mode=Memory` and `Cache=Shared` in the connection string.</span></span> <span data-ttu-id="91565-110">Słowo kluczowe `Data Source` służy do nadania nazwy bazy danych znajdującej się w pamięci.</span><span class="sxs-lookup"><span data-stu-id="91565-110">The `Data Source` keyword is used to give the in-memory database a name.</span></span> <span data-ttu-id="91565-111">Parametry połączenia używające tej samej nazwy będą miały dostęp do tej samej bazy danych w pamięci.</span><span class="sxs-lookup"><span data-stu-id="91565-111">Connection strings using the same name will access the same in-memory database.</span></span> <span data-ttu-id="91565-112">Baza danych utrzymuje się, dopóki nie zostanie otwarte co najmniej jedno połączenie.</span><span class="sxs-lookup"><span data-stu-id="91565-112">The database persists as long as at least one connection to it remains open.</span></span> <span data-ttu-id="91565-113">[Przykład](https://github.com/dotnet/samples/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) pokazujący, że jest dostępny w serwisie GitHub.</span><span class="sxs-lookup"><span data-stu-id="91565-113">A [sample](https://github.com/dotnet/samples/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) demonstrating this is available on GitHub.</span></span>

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
