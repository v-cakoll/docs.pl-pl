---
title: We/wy obiektu BLOB
ms.date: 12/13/2019
description: Dowiedz się, jak używać funkcji we/wy obiektu BLOB firmy SQLite.
ms.openlocfilehash: 0c133deacdc19684eca3a6724fb398dc01fda558
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447049"
---
# <a name="blob-io"></a>We/wy obiektu BLOB

Można zmniejszyć użycie pamięci podczas odczytywania i pisania dużych obiektów przez przesyłanie strumieniowe danych do i z bazy danych. Może to być szczególnie przydatne podczas analizowania lub przekształcania danych.

Zacznij od wstawienia wiersza jako normalny. Użyj funkcji SQL `zeroblob()`, aby przydzielić miejsce w bazie danych w celu przechowywania dużego obiektu. Funkcja `last_insert_rowid()` zapewnia wygodny sposób uzyskiwania jego ROWID.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Insert)]

Po wstawieniu wiersza Otwórz strumień, aby zapisać duży obiekt przy użyciu <xref:Microsoft.Data.Sqlite.SqliteBlob>.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Write)]

Aby przesłać strumieniowo duży obiekt z bazy danych, musisz wybrać identyfikator RowId lub jeden z jego aliasów, jak pokazano tutaj, oprócz kolumny dużego obiektu. Jeśli nie wybierzesz ROWID, cały obiekt zostanie załadowany do pamięci. Obiekt zwrócony przez `GetStream()` będzie `SqliteBlob` po poprawnym wykonaniu.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Read)]
