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
# <a name="in-memory-databases"></a>Bazy danych w pamięci

Bazy danych SQLite w pamięci są bazami danych przechowywanymi w całości w pamięci, a nie na dysku. Użyj specjalnej nazwy pliku `:memory:` źródła danych, aby utworzyć bazę danych w pamięci. Po zamknięciu połączenia baza danych jest usuwana. Podczas `:memory:`korzystania z tego każde połączenie tworzy własną bazę danych.

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a>Bazy danych w pamięci, które można udostępnić

Bazy danych w pamięci mogą być współużytkowane przez wiele połączeń przy użyciu `Mode=Memory` i `Cache=Shared` w ciągu połączenia. Słowo `Data Source` kluczowe jest używane do nadawanie nazwy w bazie danych w pamięci. Parametry połączenia o tej samej nazwie będą uzyskiwać dostęp do tej samej bazy danych w pamięci. Baza danych będzie się powtarzać tak długo, jak co najmniej jedno połączenie z nią pozostaje otwarte. [Przykład](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) pokazujący to jest dostępny w usłudze GitHub.

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
