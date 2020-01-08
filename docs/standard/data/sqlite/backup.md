---
title: Kopia zapasowa online
ms.date: 12/13/2019
description: Dowiedz się, jak używać funkcji tworzenia kopii zapasowych online oprogramowania SQLite.
ms.openlocfilehash: 885aa2c5555b58deb2551c0a4e6933742a093457
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447098"
---
# <a name="online-backup"></a>Kopia zapasowa online

Program SQLite może utworzyć kopię zapasową plików bazy danych, gdy aplikacja jest uruchomiona. Ta funkcja jest dostępna w firmie Microsoft. Data. sqlite jako metoda <xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> w `SqliteConnection`.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BackupSample/Program.cs?name=snippet_Backup)]

Obecnie `BackupDatabase` tworzy kopię zapasową bazy danych tak szybko, jak to możliwe, i blokuje inne połączenia z zapisu w bazie danych. Problem [#13834](https://github.com/aspnet/EntityFrameworkCore/issues/13834) zapewnia alternatywny interfejs API do tworzenia kopii zapasowej bazy danych w tle i zezwala na inne połączenia w celu przerwania tworzenia kopii zapasowej i zapisu w bazie danych. Jeśli jesteś zainteresowanym, Prześlij opinię na temat problemu.
