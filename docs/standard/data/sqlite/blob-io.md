---
title: We/wy obiektu blob
ms.date: 12/13/2019
description: Dowiedz się, jak używać funkcji we/wy obiektu BLOB firmy SQLite.
ms.openlocfilehash: 0c133deacdc19684eca3a6724fb398dc01fda558
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447049"
---
# <a name="blob-io"></a>We/wy obiektu blob

Można zmniejszyć użycie pamięci podczas odczytywania i pisania dużych obiektów przez przesyłanie strumieniowe danych do i z bazy danych. Może to być szczególnie przydatne podczas analizowania lub przekształcania danych.

Zacznij od wstawienia wiersza jako normalny. Użyj funkcji `zeroblob()` SQL w celu przydzielenia miejsca w bazie danych w celu przechowywania dużego obiektu. `last_insert_rowid()` Funkcja zapewnia wygodny sposób uzyskiwania jego ROWID.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Insert)]

Po wstawieniu wiersza Otwórz strumień, aby napisać duży obiekt za pomocą <xref:Microsoft.Data.Sqlite.SqliteBlob>.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Write)]

Aby przesłać strumieniowo duży obiekt z bazy danych, musisz wybrać identyfikator RowId lub jeden z jego aliasów, jak pokazano tutaj, oprócz kolumny dużego obiektu. Jeśli nie wybierzesz ROWID, cały obiekt zostanie załadowany do pamięci. Obiekt zwrócony przez `GetStream()` to `SqliteBlob` po poprawnym wykonaniu.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Read)]
