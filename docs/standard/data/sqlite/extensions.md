---
title: Rozszerzenia
ms.date: 12/13/2019
description: Dowiedz się, jak załadować rozszerzenia SQLite.
ms.openlocfilehash: 51c705349c25240fe42e0edda8004a3e3b013ca3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242962"
---
# <a name="extensions"></a>Rozszerzenia

SQLite obsługuje rozszerzenia ładowania w czasie wykonywania. Rozszerzenia obejmują takie rzeczy jak dodatkowe funkcje SQL, sortowania, tabele wirtualne i inne.

Program .NET Core zawiera dodatkową logikę lokalizowania bibliotek natywnych w dodatkowych miejscach, takich jak pakiety NuGet, do których istnieje odwołanie. Niestety, SQLite nie może wykorzystać tej logiki; wywołuje interfejs API platformy bezpośrednio do ładowania bibliotek. Z tego powodu może być konieczne zmodyfikowanie path, LD_LIBRARY_PATH lub DYLD_LIBRARY_PATH zmiennych środowiskowych przed załadowaniem rozszerzeń SQLite. Istnieje [przykład](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) na GitHub, który demonstruje znajdowanie plików binarnych dla bieżącego środowiska wykonawczego wewnątrz pakietu NuGet, do którego istnieje odwołanie.

Aby załadować rozszerzenie, <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A> należy wywołać metodę. Microsoft.Data.Sqlite zapewni, że rozszerzenie pozostaje załadowany, nawet jeśli połączenie jest zamknięte i ponownie otwarte.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs?name=snippet_LoadExtension)]

## <a name="see-also"></a>Zobacz też

* [Rozszerzenia wczytywalne w czasie wykonywania](https://www.sqlite.org/loadext.html)
