---
title: Przetwarzanie wsadowe
ms.date: 12/13/2019
description: Dowiedz się, jak wykonać partię instrukcji SQL w pojedynczym poleceniu.
ms.openlocfilehash: 0799784471520bb279db6a4b5879ad30945bdebb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447056"
---
# <a name="batching"></a>Przetwarzanie wsadowe

Oprogramowanie SQLite nie obsługuje natywnie wsadowych instrukcji SQL wraz z pojedynczym poleceniem. Jednak ze względu na to, że nie ma żadnych sieci, usługa nie może jeszcze pomóc w działaniu. Firma Microsoft. Data. sqlite wykonuje jednak implementację wsadową tworzenia instrukcji jako wygodę, aby była zachowywać się bardziej jak w przypadku innych dostawców ADO.NET.

Podczas wywoływania <xref:System.Data.Common.DbCommand.ExecuteReader%2A?displayProperty=nameWithType>instrukcje są wykonywane do pierwszego z nich, który zwraca wyniki. Wywołanie <xref:System.Data.Common.DbDataReader.NextResult%2A?displayProperty=nameWithType> kontynuuje wykonywanie instrukcji do kolejnej, która zwraca wyniki lub do momentu osiągnięcia końca zadania wsadowego. Wywołanie <xref:System.Data.Common.DbDataReader.Dispose%2A?displayProperty=nameWithType> lub <xref:System.Data.Common.DbDataReader.Close%2A> wykonanie wszelkich pozostałych instrukcji, które nie zostały zużyte przez `NextResult()`program. Jeśli czytnik danych nie zostanie rozdysponowany, finalizator próbuje wykonać pozostałe instrukcje, ale wszelkie napotkane błędy zostaną zignorowane. W związku z tym ważne jest, aby usunąć `DbDataReader` obiekty przy użyciu partii.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BatchingSample/Program.cs?name=snippet_Batching)]

## <a name="see-also"></a>Zobacz też

* [Wstawianie zbiorcze](bulk-insert.md)
