---
title: Ograniczenia Dapper
ms.date: 12/13/2019
description: W tym artykule opisano niektóre z ograniczeń, które można napotkać podczas korzystania z programu Dapper.
ms.openlocfilehash: 90c7fb24f068d663081390bdba9b1b222b4be56e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447280"
---
# <a name="dapper-limitations"></a>Ograniczenia Dapper

Istnieje kilka ograniczeń, które należy wziąć pod uwagę podczas korzystania z programu Microsoft. Data. sqlite z [Dapper](https://stackexchange.github.io/Dapper/).

## <a name="parameters"></a>Parametry

W nazwach parametrów SQLite jest rozróżniana wielkość liter. Upewnij się, że nazwy parametrów używane w programie SQL pasują do wielkości liter we właściwościach obiektu anonimowego. Problem [#18861](https://github.com/aspnet/EntityFrameworkCore/issues/18861) poprawi to środowisko.

Dapper oczekuje również parametrów do użycia prefiksu `@`. Inne prefiksy nie będą działały.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_Parameter)]

## <a name="data-types"></a>Typy danych

Dapper odczytuje wartości za pomocą indeksatora SqliteDataReader. Zwracanym typem tego indeksatora jest Object, co oznacza, że zwróci tylko wartości Long, Double, String lub Byte []. Aby uzyskać więcej informacji, zobacz [typy danych](types.md). Dapper obsługuje większość konwersji między tymi i innymi typami pierwotnymi. Niestety, nie obsługuje `DateTimeOffset`, `Guid`lub `TimeSpan`. Utwórz programy obsługi typów, jeśli chcesz używać tych typów w wynikach.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_TypeHandlers)]

Nie zapomnij dodać programów obsługi typu przed wykonaniem zapytania.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_AddTypeHandlers)]

## <a name="see-also"></a>Zobacz także

* [Typy danych](types.md)
* [Ograniczenia asynchroniczne](async.md)
