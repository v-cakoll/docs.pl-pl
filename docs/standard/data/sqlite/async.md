---
title: Ograniczenia asynchroniczne
ms.date: 12/13/2019
description: Wyjaśnia ograniczenia dotyczące asynchronicznych interfejsów API i niektórych alternatyw, których można użyć zamiast tego.
ms.openlocfilehash: 350237dc5c03023f60e9680e8b9c94aabb62606f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447084"
---
# <a name="async-limitations"></a><span data-ttu-id="0b672-103">Ograniczenia asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="0b672-103">Async limitations</span></span>

<span data-ttu-id="0b672-104">SQLite nie obsługuje asynchronicznych operacji we/wy.</span><span class="sxs-lookup"><span data-stu-id="0b672-104">SQLite doesn't support asynchronous I/O.</span></span> <span data-ttu-id="0b672-105">Asynchroniczne metody ADO.NET będą wykonywane synchronicznie w programie Microsoft. Data. sqlite.</span><span class="sxs-lookup"><span data-stu-id="0b672-105">Async ADO.NET methods will execute synchronously in Microsoft.Data.Sqlite.</span></span> <span data-ttu-id="0b672-106">Należy unikać wywoływania tych funkcji.</span><span class="sxs-lookup"><span data-stu-id="0b672-106">Avoid calling them.</span></span>

<span data-ttu-id="0b672-107">Zamiast tego należy użyć [zapisu z wyprzedzeniem](https://www.sqlite.org/wal.html) , aby zwiększyć wydajność i współbieżność.</span><span class="sxs-lookup"><span data-stu-id="0b672-107">Instead, use [write-ahead logging](https://www.sqlite.org/wal.html) to improve performance and concurrency.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AsyncSample/Program.cs?name=snippet_WAL)]

> [!TIP]
> <span data-ttu-id="0b672-108">Rejestrowanie z wyprzedzeniem jest domyślnie włączone w bazach danych utworzonych przy użyciu [Entity Framework Core](/ef/core/).</span><span class="sxs-lookup"><span data-stu-id="0b672-108">Write-ahead logging is enabled by default on databases created using [Entity Framework Core](/ef/core/).</span></span>
