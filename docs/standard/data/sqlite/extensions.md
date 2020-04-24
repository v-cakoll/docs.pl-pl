---
title: Rozszerzenia
ms.date: 12/13/2019
description: Dowiedz się, jak ładować rozszerzenia oprogramowania SQLite.
ms.openlocfilehash: 51c705349c25240fe42e0edda8004a3e3b013ca3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242962"
---
# <a name="extensions"></a>Rozszerzenia

Program SQLite obsługuje ładowanie rozszerzeń w czasie wykonywania. Rozszerzenia obejmują elementy, takie jak dodatkowe funkcje SQL, sortowania, tabele wirtualne i nie tylko.

Platforma .NET Core zawiera dodatkową logikę do lokalizowania bibliotek natywnych w dodatkowych miejscach, takich jak pakiety NuGet, do których istnieją odwołania. Niestety, program SQLite nie może wykorzystać tej logiki; Interfejs API platformy jest wywoływany bezpośrednio w celu załadowania bibliotek. W związku z tym może być konieczne zmodyfikowanie ścieżki, LD_LIBRARY_PATH lub DYLD_LIBRARY_PATH zmiennych środowiskowych przed załadowaniem rozszerzeń programu SQLite. Istnieje [przykład](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) w witrynie GitHub, który pokazuje wyszukiwanie plików binarnych dla bieżącego środowiska uruchomieniowego w pakiecie NuGet, do którego istnieje odwołanie.

Aby załadować rozszerzenie, wywołaj <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A> metodę. Firma Microsoft. Data. sqlite zapewni załadowanie rozszerzenia, nawet jeśli połączenie zostanie zamknięte i ponownie otwarte.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs?name=snippet_LoadExtension)]

## <a name="see-also"></a>Zobacz też

* [Rozszerzenia do załadowania w czasie wykonywania](https://www.sqlite.org/loadext.html)
