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
# <a name="bulk-insert"></a>Wstawianie zbiorcze

Program SQLite nie ma specjalnego sposobu na zbiorcze Wstawianie danych. Aby zapewnić optymalną wydajność podczas wstawiania lub aktualizowania danych, należy wykonać następujące czynności:

- Użyj transakcji.
- Ponownie Użyj tego samego sparametryzowanego polecenia. Kolejne wykonania będą ponownie używały kompilacji pierwszej.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BulkInsertSample/Program.cs?name=snippet_BulkInsert)]
