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
ms.openlocfilehash: 64d91162b27eba80fba63761d0a926e441b63440
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287864"
---
# <a name="create-an-object-pool-by-using-a-concurrentbag"></a>Tworzenie puli obiektów przy użyciu obiekt ConcurrentBag

Ten przykład pokazuje, jak używać <xref:System.Collections.Concurrent.ConcurrentBag%601> do implementowania puli obiektów. Pule obiektów mogą zwiększyć wydajność aplikacji w sytuacjach, gdy wymagana jest wiele wystąpień klasy, a Klasa jest kosztowna do tworzenia lub niszczenia. Gdy program kliencki żąda nowego obiektu, Pula obiektów najpierw próbuje dostarczyć taką, która została już utworzona i zwrócona do puli. Jeśli żaden nie jest dostępny, tylko wtedy jest tworzony nowy obiekt.

Służy <xref:System.Collections.Concurrent.ConcurrentBag%601> do przechowywania obiektów, ponieważ obsługuje szybkie Wstawianie i usuwanie, szczególnie gdy ten sam wątek dodaje i usuwa elementy. Ten przykład może być dodatkowo rozszerzany tak, aby był zbudowany wokół <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> , który jest implementowany przez strukturę danych zbioru, jak to zrobić <xref:System.Collections.Concurrent.ConcurrentQueue%601> i <xref:System.Collections.Concurrent.ConcurrentStack%601> .

> [!TIP]
> W tym artykule opisano sposób pisania własnej implementacji puli obiektów z podstawowym typem współbieżnym do przechowywania obiektów do ponownego użycia. Jednak ten <xref:Microsoft.Extensions.ObjectPool.ObjectPool%601?displayProperty=nameWithType> Typ już istnieje w <xref:Microsoft.Extensions.ObjectPool?displayProperty=fullName> przestrzeni nazw. Rozważ użycie dostępnego typu przed utworzeniem własnej implementacji, która obejmuje wiele dodatkowych funkcji.

## <a name="example"></a>Przykład

[!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
[!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]

## <a name="see-also"></a>Zobacz także

- [Kolekcje bezpieczne dla wątków](index.md)
