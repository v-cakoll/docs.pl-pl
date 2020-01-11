---
title: Kopia zapasowa online
ms.date: 12/13/2019
description: Dowiedz się, jak używać funkcji tworzenia kopii zapasowych online oprogramowania SQLite.
ms.openlocfilehash: d857dcb69f2b2d10b034a0abf222b30c2e20bb41
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901284"
---
# <a name="online-backup"></a>Kopia zapasowa online

Program SQLite może utworzyć kopię zapasową plików bazy danych, gdy aplikacja jest uruchomiona. Ta funkcja jest dostępna w firmie Microsoft. Data. sqlite jako metoda <xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> w `SqliteConnection`.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BackupSample/Program.cs?name=snippet_Backup)]

Obecnie `BackupDatabase` tworzy kopię zapasową bazy danych tak szybko, jak to możliwe, i blokuje inne połączenia z zapisu w bazie danych. Problem [#13834](https://github.com/dotnet/efcore/issues/13834) zapewnia alternatywny interfejs API do tworzenia kopii zapasowej bazy danych w tle i zezwala na inne połączenia w celu przerwania tworzenia kopii zapasowej i zapisu w bazie danych. Jeśli jesteś zainteresowanym, Prześlij opinię na temat problemu.
