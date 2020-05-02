---
title: Tworzenie puli obiektów przy użyciu obiekt ConcurrentBag
ms.date: 05/01/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object pool, in .NET Framework
ms.assetid: 0480e7ff-b6f9-480e-a889-2ed4264d8372
ms.openlocfilehash: 2c060dc901f8d06a5f9c51db1cd563cb28e4fda3
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728470"
---
# <a name="create-an-object-pool-by-using-a-concurrentbag"></a>Tworzenie puli obiektów przy użyciu obiekt ConcurrentBag

Ten przykład pokazuje, <xref:System.Collections.Concurrent.ConcurrentBag%601> jak używać do implementowania puli obiektów. Pule obiektów mogą zwiększyć wydajność aplikacji w sytuacjach, gdy wymagana jest wiele wystąpień klasy, a Klasa jest kosztowna do tworzenia lub niszczenia. Gdy program kliencki żąda nowego obiektu, Pula obiektów najpierw próbuje dostarczyć taką, która została już utworzona i zwrócona do puli. Jeśli żaden nie jest dostępny, tylko wtedy jest tworzony nowy obiekt.

<xref:System.Collections.Concurrent.ConcurrentBag%601> Służy do przechowywania obiektów, ponieważ obsługuje szybkie Wstawianie i usuwanie, szczególnie gdy ten sam wątek dodaje i usuwa elementy. Ten przykład może być dodatkowo rozszerzany tak <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, aby był zbudowany wokół, który jest implementowany przez strukturę danych zbioru <xref:System.Collections.Concurrent.ConcurrentQueue%601> , <xref:System.Collections.Concurrent.ConcurrentStack%601>jak to zrobić i.

> [!TIP]
> W tym artykule opisano sposób pisania własnej implementacji puli obiektów z podstawowym typem współbieżnym do przechowywania obiektów do ponownego użycia. Jednak ten <xref:Microsoft.Extensions.ObjectPool.ObjectPool%601?displayProperty=nameWithType> typ już istnieje w <xref:Microsoft.Extensions.ObjectPool?displayProperty=fullName> przestrzeni nazw. Rozważ użycie dostępnego typu przed utworzeniem własnej implementacji, która obejmuje wiele dodatkowych funkcji.

## <a name="example"></a>Przykład

[!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
[!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]

## <a name="see-also"></a>Zobacz także

- [Kolekcje bezpieczne dla wątków](../../../../docs/standard/collections/thread-safe/index.md)
