---
title: Funkcje zdefiniowane przez użytkownika
ms.date: 12/13/2019
description: Dowiedz się, jak tworzyć zdefiniowane przez użytkownika funkcje skalarne i agregujące.
ms.openlocfilehash: 9ee3fbac73215353c8dc82199203b0d25e580cdb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447175"
---
# <a name="user-defined-functions"></a>Funkcje zdefiniowane przez użytkownika

Większość baz danych ma dialekt proceduralny dotyczący języka SQL, którego można użyć do zdefiniowania własnych funkcji. Jednak program SQLite działa w procesie z aplikacją. Zamiast uczyć się nowego dialektu SQL, można po prostu użyć języka programowania aplikacji.

## <a name="scalar-functions"></a>Funkcje skalarne

Funkcje skalarne zwracają pojedynczą wartość skalarną dla każdego wiersza w zapytaniu. Zdefiniuj nowe funkcje skalarne i zastąp wbudowane przy użyciu polecenia <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateFunction%2A>.

Zobacz [typy danych](types.md) , aby uzyskać listę obsługiwanych parametrów i zwracanych typów dla `func` tego argumentu.

Określenie `state` argumentu spowoduje przekazanie tej wartości do każdego wywołania funkcji. Użyj tego, aby uniknąć zamykania.

Określ `isDeterministic` , czy funkcja jest deterministyczna, aby umożliwić firmie SQLite Używanie dodatkowych optymalizacji podczas kompilowania zapytań.

Poniższy przykład pokazuje, jak dodać funkcję skalarną, aby obliczyć promień cylindra.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ScalarFunctionSample/Program.cs?name=snippet_CreateFunction)]

## <a name="operators"></a>Operatory

Następujące operatory programu SQLite są implementowane przez odpowiednie funkcje skalarne. Zdefiniowanie tych funkcji skalarnych w aplikacji spowoduje przesłonięcie zachowania tych operatorów.

| Operator          | Funkcja      |
| ----------------- | ------------- |
| X GLOBALIZOWANIA Y          | globalizowania (Y, X)    |
| X PODOBNE DO Y          | like (Y, X)    |
| X LIKE Y UCIECZKI Z | like (Y, X, Z) |
| X DOPASOWANIA Y         | dopasowanie (Y, X)   |
| X REGEXP Y        | RegExp (Y, X)  |

Poniższy przykład pokazuje, jak zdefiniować funkcję RegExp w celu włączenia odpowiadającego jej operatora. Technologia SQLite nie zawiera domyślnej implementacji funkcji RegExp.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/RegularExpressionSample/Program.cs?name=snippet_Regex)]

## <a name="aggregate-functions"></a>Funkcje agregujące

Funkcje agregujące zwracają pojedynczą, zagregowaną wartość dla wszystkich wierszy w zapytaniu. Zdefiniuj i Przesłoń funkcje agregujące przy użyciu <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateAggregate%2A>.

`seed` Argument określa początkowy stan kontekstu. Użyj tego, aby uniknąć również zamknięć.

`func` Argument jest wywoływany raz w każdym wierszu. Użyj kontekstu, aby zbierać wynik końcowy. Zwróć kontekst. Ten wzorzec zezwala na kontekst jako typ wartości lub niezmienny.

Jeśli nie `resultSelector` jest określony, ostatni stan kontekstu jest używany jako wynik. Może to uprościć definicje funkcji, takich jak sum i Count, które wymagają zwiększenia liczby tylko każdego wiersza i zwrócenia go.

Określ `resultSelector` , aby obliczyć końcowy wynik z kontekstu po przeprowadzeniu iteracji we wszystkich wierszach.

Zobacz [typy danych](types.md) , aby uzyskać listę obsługiwanych typów parametrów dla `func` argumentu i typów zwracanych dla `resultSelector`.

Jeśli funkcja jest deterministyczna, określ `isDeterministic` , czy program SQLite ma używać dodatkowych optymalizacji podczas kompilowania zapytań.

W poniższym przykładzie zdefiniowano funkcję agregującą, aby obliczyć odchylenie standardowe kolumny.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AggregateFunctionSample/Program.cs?name=snippet_CreateAggregate)]

## <a name="errors"></a>Errors

Jeśli funkcja zdefiniowana przez użytkownika zgłosi wyjątek, komunikat jest zwracany do oprogramowania SQLite. Oprogramowanie SQLite zgłosi błąd, a firma Microsoft. Data. sqlite zgłosi wyjątek Sqliteexception. Aby uzyskać więcej informacji, zobacz [Błędy bazy danych](database-errors.md).

Domyślnie kod błędu programu SQLite zostanie zwrócony SQLITE_ERROR (lub 1). Można jednak go zmienić, przerzucając <xref:Microsoft.Data.Sqlite.SqliteException> w funkcji funkcję z żądanym <xref:Microsoft.Data.Sqlite.SqliteException.SqliteErrorCode> określonym.

## <a name="debugging"></a>Debugowanie

Technologia SQLite bezpośrednio wywołuje Twoją implementację. Dzięki temu można dodawać punkty przerwania wyzwalane podczas oceniania przez program SQLite zapytań. Dostępne jest pełne środowisko debugowania .NET, które ułatwia tworzenie funkcji zdefiniowanych przez użytkownika.

## <a name="see-also"></a>Zobacz też

* [Typy danych](types.md)
* [Podstawowe funkcje oprogramowania SQLite](https://www.sqlite.org/lang_corefunc.html)
* [Funkcje agregujące oprogramowania SQLite](https://www.sqlite.org/lang_aggfunc.html)
