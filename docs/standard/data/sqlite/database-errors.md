---
title: Błędy bazy danych
ms.date: 12/13/2019
description: Opisuje sposób obsługi błędów bazy danych i ich wykonywania przez bibliotekę.
ms.openlocfilehash: 9a613b6f94a89dc40e627c14f46836be77080035
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447273"
---
# <a name="database-errors"></a>Błędy bazy danych

<xref:Microsoft.Data.Sqlite.SqliteException>jest generowany w przypadku napotkania błędu oprogramowania SQLite. Komunikat jest dostarczany przez program SQLite. Właściwości `SqliteErrorCode` i `SqliteExtendedErrorCode` zawierają [kod wyniku](https://www.sqlite.org/rescode.html) programu SQLite błędu.

Błędy mogą wystąpić w dowolnym momencie, gdy firma Microsoft. Data. sqlite współdziała z natywną biblioteką oprogramowania SQLite. Na poniższej liście przedstawiono typowe scenariusze, w których mogą wystąpić błędy:

* Otwieranie połączenia.
* Rozpoczęcie transakcji.
* Wykonywanie polecenia.
* Wywoływanie <xref:Microsoft.Data.Sqlite.SqliteDataReader.NextResult%2A>.

Rozważ uważnie, jak aplikacja będzie obsługiwać te błędy.

## <a name="locking-retries-and-timeouts"></a>Blokowanie, ponawianie próby i limity czasu

W przypadku zablokowania tabel i plików bazy danych w programie SQLite jest agresywne. Jeśli aplikacja umożliwia równoczesny dostęp do bazy danych, prawdopodobnie wystąpią błędy zajęte i zablokowane. Możesz złagodzić wiele błędów, używając [udostępnionej pamięci podręcznej](connection-strings.md#cache) i [rejestrowania z wyprzedzeniem](async.md).

Za każdym razem, gdy Microsoft. Data. sqlite napotka błąd zajęty lub zablokowany, nastąpi automatyczne ponowienie próby do momentu pomyślnego lub przekroczenie limitu czasu polecenia.

Można zwiększyć limit czasu polecenia według ustawienia <xref:Microsoft.Data.Sqlite.SqliteCommand.CommandTimeout%2A>. Domyślny limit czasu wynosi 30 sekund. Wartość `0` oznacza brak limitu czasu.

```csharp
// Retry for 60 seconds while locked
command.CommandTimeout = 60;
```

Microsoft. Data. sqlite czasami musi utworzyć obiekt polecenia niejawnego. Na przykład podczas BeginTransaction. Aby ustawić limit czasu dla tych poleceń, użyj <xref:Microsoft.Data.Sqlite.SqliteConnection.DefaultTimeout%2A>polecenia.

```csharp
// Set the default timeout of all commands on this connection
connection.DefaultTimeout = 60;
```

## <a name="see-also"></a>Zobacz też

* [Kody błędów oprogramowania SQLite](https://www.sqlite.org/rescode.html)
* [Blokowanie plików w programie SQLite](https://www.sqlite.org/lockingv3.html)
* [Tryb udostępnionej pamięci podręcznej](https://www.sqlite.org/sharedcache.html)
* [Rejestrowanie przed zapisem](https://www.sqlite.org/wal.html)
