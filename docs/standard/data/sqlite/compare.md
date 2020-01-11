---
title: Porównanie z System. Data. SQLite
ms.date: 12/13/2019
description: W tym artykule opisano niektóre różnice między bibliotekami Microsoft. Data. sqlite i system. Data. SQLite.
ms.openlocfilehash: 076bbc6f746cf9296c96ec73047397a21a3b2558
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900713"
---
# <a name="comparison-to-systemdatasqlite"></a>Porównanie z System. Data. SQLite

W 2005, Robert Simpson utworzył system. Data. SQLite, dostawcę oprogramowania SQLite dla ADO.NET 2,0. W 2010 zespół ds. oprogramowania SQLite przejął konserwację i opracowywanie projektu. Warto również zauważyć, że zespół mono rozwidlenie kodu w 2007 jako mono. Data. sqlite. System. Data. SQLite ma długą historię i został rozdzielony na stabilny i w pełni funkcjonalny dostawca usług ADO.NET z narzędziami programu Visual Studio. Nowe wersje nadal będą dostarczać zestawy zgodne z każdą wersją .NET Framework z powrotem do wersji 2,0, a nawet .NET Compact Framework 3,5.

Pierwsza wersja programu .NET Core (wydana w 2016) to jedna, lekka, nowoczesne i wieloplatformowa implementacja platformy .NET. Przestarzałe interfejsy API i interfejsy API z bardziej nowoczesnymi alternatywami zostały celowo usunięte. ADO.NET nie zawierał żadnego z interfejsów API zestawu danych (w tym DataTable i DataAdapter).

Zespół Entity Framework był nieco zaznajomiony z bazą kodu system. Data. SQLite. Brice Lambson, członek zespołu EF wcześniej pobrał pomoc techniczną do dodania do Entity Framework wersji 5 i 6. Brice również eksperymentować z własną implementacją dostawcy oprogramowania SQLite ADO.NET w tym samym czasie, w którym zaplanowano platformę .NET Core. Po długiej dyskusji zespół Entity Framework zdecydował się utworzyć Microsoft. Data. sqlite na podstawie prototypu Brice. Pozwoli to na utworzenie nowej uproszczonej i nowoczesnej implementacji, która będzie wyrównana do celów platformy .NET Core.

Przykładem tego, co robimy przez bardziej nowoczesny kod, można utworzyć [zdefiniowaną przez użytkownika funkcję](user-defined-functions.md) w obu polach system. Data. sqlite i Microsoft. Data. sqlite.

```csharp
// System.Data.SQLite
connection.BindFunction(
    new SQLiteFunctionAttribute("ceiling", 1, FunctionType.Scalar),
    (Func<object[], object>)((object[] args) => Math.Ceiling((double)((object[])args[1])[0])),
    null);

// Microsoft.Data.Sqlite
connection.CreateFunction(
    "ceiling",
    (double arg) => Math.Ceiling(arg));
```

W 2017 na platformie .NET Core 2,0 Wystąpił Zmiana strategii. Ustalono, że zgodność z .NET Framework była istotna dla sukcesu platformy .NET Core. Wiele z usuniętych interfejsów API, w tym interfejsów API zestawu danych, zostało dodanych z powrotem. Podobnie jak w przypadku wielu innych, ten odblokowany system. Data. SQLite umożliwia również przenoszenie go do programu .NET Core. Oryginalny cel firmy Microsoft. Data. sqlite jako uproszczony i nowoczesny, jednak nadal pozostaje. Zobacz [ADO.NET ograniczenia](adonet-limitations.md) , aby uzyskać szczegółowe informacje o interfejsach API ADO.NET, które nie zostały zaimplementowane przez firmę Microsoft. Data. sqlite.

Po dodaniu nowych funkcji do programu Microsoft. Data. SQLite jest uwzględniany projekt system. Data. SQLite. Staramy się, jeśli to możliwe, aby zminimalizować zmiany między tymi dwoma, aby ułatwić przejście między nimi.

## <a name="data-types"></a>Typy danych

Największą różnicą między elementami Microsoft. Data. sqlite i system. Data. SQLite jest sposób obsługi typów danych. Jak opisano w [typach danych](types.md), Microsoft. Data. sqlite nie próbuje ukryć bazowego quirkiness oprogramowania SQLite, co umożliwia określenie dowolnego ciągu jako typu kolumny i zawiera tylko cztery typy pierwotne: Integer, Real, text i BLOB.

System. Data. SQLite stosuje dodatkową semantykę do typów kolumn, mapując je bezpośrednio do typów .NET. Dzięki temu dostawca ma bardziej silnie wpisaną, ale ma pewne przybliżone krawędzie. Na przykład musiały wprowadzić nową instrukcję SQL (typy), aby określić typy kolumn wyrażeń w instrukcji SELECT.

## <a name="connection-strings"></a>Parametry połączeń

Microsoft. Data. sqlite zawiera wiele słów kluczowych [parametrów połączenia](connection-strings.md) . W poniższej tabeli przedstawiono alternatywy, których można użyć zamiast tego.

| Słowo kluczowe          | Różne                                         |
| ---------------- | --------------------------------------------------- |
| Rozmiar pamięci podręcznej       | Wyślij `PRAGMA cache_size = <pages>`                  |
| Domyślny limit czasu  | Używanie właściwości DefaultTimeout w SqliteConnection |
| FailIfMissing    | Użyj `Mode=ReadWrite`                                |
| FullUri          | Użyj słowa kluczowego źródła danych                         |
| Tryb dziennika     | Wyślij `PRAGMA journal_mode = <mode>`                 |
| Starszy format    | Wyślij `PRAGMA legacy_file_format = 1`                |
| Maksymalna liczba stron   | Wyślij `PRAGMA max_page_count = <pages>`              |
| Rozmiar strony        | Wyślij `PRAGMA page_size = <bytes>`                   |
| Tylko do odczytu        | Użyj `Mode=ReadOnly`                                 |
| Synchroniczny      | Wyślij `PRAGMA synchronous = <mode>`                  |
| URI              | Użyj słowa kluczowego źródła danych                         |
| UseUTF16Encoding | Wyślij `PRAGMA encoding = 'UTF-16'`                   |

## <a name="authorization"></a>Autoryzacja

Microsoft. Data. sqlite nie ma interfejsu API uwidaczniania wywołania zwrotnego autoryzacji oprogramowania SQLite. Użyj [#13835](https://github.com/dotnet/efcore/issues/13835) problemu, aby przekazać opinię na temat tej funkcji.

## <a name="data-change-notifications"></a>Powiadomienia o zmianach danych

Microsoft. Data. sqlite nie ma interfejsu API uwidaczniania powiadomień o zmianach danych oprogramowania SQLite. Użyj [#13827](https://github.com/dotnet/efcore/issues/13827) problemu, aby przekazać opinię na temat tej funkcji.

## <a name="virtual-table-modules"></a>Moduły tabeli wirtualnej

Microsoft. Data. sqlite nie ma żadnego interfejsu API do tworzenia modułów tabeli wirtualnej. Użyj [#13823](https://github.com/dotnet/efcore/issues/13823) problemu, aby przekazać opinię na temat tej funkcji.

## <a name="see-also"></a>Zobacz także

* [Typy danych](types.md)
* [Parametry połączenia](connection-strings.md)
* [Szyfrowanie](encryption.md)
* [Ograniczenia ADO.NET](adonet-limitations.md)
* [Ograniczenia Dapper](dapper-limitations.md)
