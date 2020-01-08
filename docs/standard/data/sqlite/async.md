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
# <a name="async-limitations"></a>Ograniczenia asynchroniczne

SQLite nie obsługuje asynchronicznych operacji we/wy. Asynchroniczne metody ADO.NET będą wykonywane synchronicznie w programie Microsoft. Data. sqlite. Należy unikać wywoływania tych funkcji.

Zamiast tego należy użyć [zapisu z wyprzedzeniem](https://www.sqlite.org/wal.html) , aby zwiększyć wydajność i współbieżność.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AsyncSample/Program.cs?name=snippet_WAL)]

> [!TIP]
> Rejestrowanie z wyprzedzeniem jest domyślnie włączone w bazach danych utworzonych przy użyciu [Entity Framework Core](/ef/core/).
