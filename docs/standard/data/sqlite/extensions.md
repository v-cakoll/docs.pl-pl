---
title: Rozszerzenia
ms.date: 12/13/2019
description: Dowiedz się, jak ładować rozszerzenia oprogramowania SQLite.
ms.openlocfilehash: 74b207205492bac48c89cb756470326f8e4a13c4
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777369"
---
# <a name="extensions"></a>Rozszerzenia

Program SQLite obsługuje ładowanie rozszerzeń w czasie wykonywania. Rozszerzenia obejmują elementy, takie jak dodatkowe funkcje SQL, sortowania, tabele wirtualne i nie tylko.

Platforma .NET Core zawiera dodatkową logikę do lokalizowania bibliotek natywnych w dodatkowych miejscach, takich jak pakiety NuGet, do których istnieją odwołania. Niestety, program SQLite nie może wykorzystać tej logiki; Interfejs API platformy jest wywoływany bezpośrednio w celu załadowania bibliotek. W związku z tym aplikacja może wymagać modyfikacji ścieżki, LD_LIBRARY_PATH lub DYLD_LIBRARY_PATH zmiennych środowiskowych przed załadowaniem rozszerzeń programu SQLite. Istnieje [przykład](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) w witrynie GitHub, który pokazuje wyszukiwanie plików binarnych dla bieżącego środowiska uruchomieniowego w pakiecie NuGet, do którego istnieje odwołanie.

Aby załadować rozszerzenie, wywołaj metodę <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A>. Firma Microsoft. Data. sqlite zapewni załadowanie rozszerzenia, nawet jeśli połączenie zostanie zamknięte i ponownie otwarte.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs?name=snippet_LoadExtension)]

## <a name="see-also"></a>Zobacz także

* [Rozszerzenia do załadowania w czasie wykonywania](https://www.sqlite.org/loadext.html)
