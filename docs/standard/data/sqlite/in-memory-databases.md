---
title: Bazy danych w pamięci
ms.date: 12/13/2019
description: Dowiedz się, jak używać baz danych programu SQLite w pamięci.
ms.openlocfilehash: 16a9b6536fbfede203c24b757e96e28e7c49dc05
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777414"
---
# <a name="in-memory-databases"></a>Bazy danych w pamięci

Bazy danych w pamięci programu SQLite są bazami danych przechowywanymi w całości w pamięci, a nie na dysku. Użyj specjalnej nazwy pliku źródła danych `:memory:`, aby utworzyć bazę danych w pamięci. Po zamknięciu połączenia baza danych zostanie usunięta. W przypadku korzystania z `:memory:`każde połączenie tworzy własną bazę danych.

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a>Współużytkowane bazy danych w pamięci

Bazy danych znajdujące się w pamięci mogą być współużytkowane przez wiele połączeń przy użyciu `Mode=Memory` i `Cache=Shared` w parametrach połączenia. Słowo kluczowe `Data Source` służy do nadania nazwy bazy danych znajdującej się w pamięci. Parametry połączenia używające tej samej nazwy będą miały dostęp do tej samej bazy danych w pamięci. Baza danych utrzymuje się, dopóki nie zostanie otwarte co najmniej jedno połączenie. [Przykład](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/InMemorySample/Program.cs) pokazujący, że jest dostępny w serwisie GitHub.

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
