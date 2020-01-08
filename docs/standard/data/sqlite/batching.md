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
# <a name="batching"></a><span data-ttu-id="01336-103">Przetwarzanie wsadowe</span><span class="sxs-lookup"><span data-stu-id="01336-103">Batching</span></span>

<span data-ttu-id="01336-104">Oprogramowanie SQLite nie obsługuje natywnie wsadowych instrukcji SQL wraz z pojedynczym poleceniem.</span><span class="sxs-lookup"><span data-stu-id="01336-104">SQLite doesn't natively support batching SQL statements together into a single command.</span></span> <span data-ttu-id="01336-105">Jednak ze względu na to, że nie ma żadnych sieci, usługa nie może jeszcze pomóc w działaniu.</span><span class="sxs-lookup"><span data-stu-id="01336-105">But because there's no network involved, it wouldn't really help performance anyway.</span></span> <span data-ttu-id="01336-106">Firma Microsoft. Data. sqlite wykonuje jednak implementację wsadową tworzenia instrukcji jako wygodę, aby była zachowywać się bardziej jak w przypadku innych dostawców ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="01336-106">Microsoft.Data.Sqlite does, however, implement statement batching as a convenience to make it behave more like other ADO.NET providers.</span></span>

<span data-ttu-id="01336-107">Podczas wywoływania <xref:System.Data.Common.DbCommand.ExecuteReader%2A?displayProperty=nameWithType>instrukcje są wykonywane do pierwszego, który zwraca wyniki.</span><span class="sxs-lookup"><span data-stu-id="01336-107">When calling <xref:System.Data.Common.DbCommand.ExecuteReader%2A?displayProperty=nameWithType>, statements are executed up to the first one that returns results.</span></span> <span data-ttu-id="01336-108">Wywoływanie <xref:System.Data.Common.DbDataReader.NextResult%2A?displayProperty=nameWithType> kontynuuje wykonywanie instrukcji aż do następnej, która zwraca wyniki lub dopóki nie osiągnie końca zadania wsadowego.</span><span class="sxs-lookup"><span data-stu-id="01336-108">Calling <xref:System.Data.Common.DbDataReader.NextResult%2A?displayProperty=nameWithType> continues executing statements until the next one that returns results or until it reaches the end of the batch.</span></span> <span data-ttu-id="01336-109">Wywołanie <xref:System.Data.Common.DbDataReader.Dispose%2A?displayProperty=nameWithType> lub <xref:System.Data.Common.DbDataReader.Close%2A> wykonuje wszystkie pozostałe instrukcje, które nie zostały zużyte przez `NextResult()`.</span><span class="sxs-lookup"><span data-stu-id="01336-109">Calling <xref:System.Data.Common.DbDataReader.Dispose%2A?displayProperty=nameWithType> or <xref:System.Data.Common.DbDataReader.Close%2A> executes any remaining statements that haven't been consumed by `NextResult()`.</span></span> <span data-ttu-id="01336-110">Jeśli czytnik danych nie zostanie rozdysponowany, finalizator próbuje wykonać pozostałe instrukcje, ale wszelkie napotkane błędy zostaną zignorowane.</span><span class="sxs-lookup"><span data-stu-id="01336-110">If you don't dispose a data reader, the finalizer tries to execute the remaining statements, but any errors it encounters are ignored.</span></span> <span data-ttu-id="01336-111">W związku z tym ważne jest, aby zlikwidować `DbDataReader` obiektów podczas korzystania z partii.</span><span class="sxs-lookup"><span data-stu-id="01336-111">Because of this, it's important to dispose `DbDataReader` objects when using batches.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BatchingSample/Program.cs?name=snippet_Batching)]

## <a name="see-also"></a><span data-ttu-id="01336-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01336-112">See also</span></span>

* [<span data-ttu-id="01336-113">Wstawianie zbiorcze</span><span class="sxs-lookup"><span data-stu-id="01336-113">Bulk Insert</span></span>](bulk-insert.md)
