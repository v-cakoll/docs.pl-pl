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
# <a name="online-backup"></a><span data-ttu-id="79348-103">Kopia zapasowa online</span><span class="sxs-lookup"><span data-stu-id="79348-103">Online backup</span></span>

<span data-ttu-id="79348-104">Program SQLite może utworzyć kopię zapasową plików bazy danych, gdy aplikacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="79348-104">SQLite can back up database files while the app is running.</span></span> <span data-ttu-id="79348-105">Ta funkcja jest dostępna w firmie Microsoft. Data. sqlite jako metoda <xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> w `SqliteConnection`.</span><span class="sxs-lookup"><span data-stu-id="79348-105">This functionality is available in Microsoft.Data.Sqlite as the <xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> method on `SqliteConnection`.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BackupSample/Program.cs?name=snippet_Backup)]

<span data-ttu-id="79348-106">Obecnie `BackupDatabase` tworzy kopię zapasową bazy danych tak szybko, jak to możliwe, i blokuje inne połączenia z zapisu w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="79348-106">Currently, `BackupDatabase` will back up the database as quickly as possible and blocks other connections from writing to the database.</span></span> <span data-ttu-id="79348-107">Problem [#13834](https://github.com/dotnet/efcore/issues/13834) zapewnia alternatywny interfejs API do tworzenia kopii zapasowej bazy danych w tle i zezwala na inne połączenia w celu przerwania tworzenia kopii zapasowej i zapisu w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="79348-107">Issue [#13834](https://github.com/dotnet/efcore/issues/13834) would provide an alternative API to back up the database in the background and allow other connections to interrupt the backup and write to the database.</span></span> <span data-ttu-id="79348-108">Jeśli jesteś zainteresowanym, Prześlij opinię na temat problemu.</span><span class="sxs-lookup"><span data-stu-id="79348-108">If you're interested, provide feedback on the issue.</span></span>
