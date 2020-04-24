---
title: Wstawianie zbiorcze
ms.date: 12/13/2019
description: Porady dotyczące wydajności, których można użyć podczas wprowadzania wielu zmian w bazie danych.
ms.openlocfilehash: 9d87d5c8d70f8e70479f9aa02b7802f73b88de9e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447042"
---
# <a name="bulk-insert"></a><span data-ttu-id="4bc18-103">Wstawianie zbiorcze</span><span class="sxs-lookup"><span data-stu-id="4bc18-103">Bulk insert</span></span>

<span data-ttu-id="4bc18-104">Program SQLite nie ma specjalnego sposobu na zbiorcze Wstawianie danych.</span><span class="sxs-lookup"><span data-stu-id="4bc18-104">SQLite doesn't have any special way to bulk insert data.</span></span> <span data-ttu-id="4bc18-105">Aby zapewnić optymalną wydajność podczas wstawiania lub aktualizowania danych, należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4bc18-105">To get optimal performance when inserting or updating data, ensure that you do the following:</span></span>

- <span data-ttu-id="4bc18-106">Użyj transakcji.</span><span class="sxs-lookup"><span data-stu-id="4bc18-106">Use a transaction.</span></span>
- <span data-ttu-id="4bc18-107">Ponownie Użyj tego samego sparametryzowanego polecenia.</span><span class="sxs-lookup"><span data-stu-id="4bc18-107">Reuse the same parameterized command.</span></span> <span data-ttu-id="4bc18-108">Kolejne wykonania będą ponownie używały kompilacji pierwszej.</span><span class="sxs-lookup"><span data-stu-id="4bc18-108">Subsequent executions will reuse the compilation of the first one.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BulkInsertSample/Program.cs?name=snippet_BulkInsert)]
