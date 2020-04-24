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
# <a name="blob-io"></a><span data-ttu-id="b4bc0-103">We/wy obiektu blob</span><span class="sxs-lookup"><span data-stu-id="b4bc0-103">Blob I/O</span></span>

<span data-ttu-id="b4bc0-104">Można zmniejszyć użycie pamięci podczas odczytywania i pisania dużych obiektów przez przesyłanie strumieniowe danych do i z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="b4bc0-104">You can reduce memory usage while reading and writing large objects by streaming the data into and out of the database.</span></span> <span data-ttu-id="b4bc0-105">Może to być szczególnie przydatne podczas analizowania lub przekształcania danych.</span><span class="sxs-lookup"><span data-stu-id="b4bc0-105">This can be especially useful when parsing or transforming the data.</span></span>

<span data-ttu-id="b4bc0-106">Zacznij od wstawienia wiersza jako normalny.</span><span class="sxs-lookup"><span data-stu-id="b4bc0-106">Start by inserting a row as normal.</span></span> <span data-ttu-id="b4bc0-107">Użyj funkcji `zeroblob()` SQL w celu przydzielenia miejsca w bazie danych w celu przechowywania dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="b4bc0-107">Use the `zeroblob()` SQL function to allocate space in the database to hold the large object.</span></span> <span data-ttu-id="b4bc0-108">`last_insert_rowid()` Funkcja zapewnia wygodny sposób uzyskiwania jego ROWID.</span><span class="sxs-lookup"><span data-stu-id="b4bc0-108">The `last_insert_rowid()` function provides a convenient way to get its rowid.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Insert)]

<span data-ttu-id="b4bc0-109">Po wstawieniu wiersza Otwórz strumień, aby napisać duży obiekt za pomocą <xref:Microsoft.Data.Sqlite.SqliteBlob>.</span><span class="sxs-lookup"><span data-stu-id="b4bc0-109">After inserting the row, open a stream to write the large object using <xref:Microsoft.Data.Sqlite.SqliteBlob>.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Write)]

<span data-ttu-id="b4bc0-110">Aby przesłać strumieniowo duży obiekt z bazy danych, musisz wybrać identyfikator RowId lub jeden z jego aliasów, jak pokazano tutaj, oprócz kolumny dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="b4bc0-110">To stream the large object out of the database, you must select the rowid or one of its aliases as show here in addition to the large object's column.</span></span> <span data-ttu-id="b4bc0-111">Jeśli nie wybierzesz ROWID, cały obiekt zostanie załadowany do pamięci.</span><span class="sxs-lookup"><span data-stu-id="b4bc0-111">If you don't select the rowid, the entire object will be loaded into memory.</span></span> <span data-ttu-id="b4bc0-112">Obiekt zwrócony przez `GetStream()` to `SqliteBlob` po poprawnym wykonaniu.</span><span class="sxs-lookup"><span data-stu-id="b4bc0-112">The object returned by `GetStream()` will be a `SqliteBlob` when done correctly.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Read)]
