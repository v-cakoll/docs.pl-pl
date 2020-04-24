---
title: Bazy danych w pamięci
ms.date: 12/13/2019
description: Dowiedz się, jak używać baz danych programu SQLite w pamięci.
ms.openlocfilehash: 408c81f538e27dcfffad20db74b7809912b7905f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391211"
---
# <a name="in-memory-databases"></a>Bazy danych w pamięci

Bazy danych w pamięci programu SQLite są bazami danych przechowywanymi w całości w pamięci, a nie na dysku. Użyj nazwy pliku `:memory:` specjalnej źródła danych, aby utworzyć bazę danych w pamięci. Po zamknięciu połączenia baza danych zostanie usunięta. W przypadku `:memory:`korzystania z programu każde połączenie tworzy własną bazę danych.

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a>Współużytkowane bazy danych w pamięci

Bazy danych w pamięci mogą być współużytkowane przez wiele połączeń `Mode=Memory` przy `Cache=Shared` użyciu i w parametrach połączenia. `Data Source` Słowo kluczowe jest używane do nadania nazwy bazy danych znajdującej się w pamięci. Parametry połączenia używające tej samej nazwy będą miały dostęp do tej samej bazy danych w pamięci. Baza danych utrzymuje się, dopóki nie zostanie otwarte co najmniej jedno połączenie. [Przykład](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) pokazujący, że jest dostępny w serwisie GitHub.

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
