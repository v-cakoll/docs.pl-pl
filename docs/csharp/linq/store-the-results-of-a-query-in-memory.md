---
title: Przechowywanie wyników zapytania w pamięci
description: Jak przechowywać wyniki.
ms.date: 11/30/2016
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 66a7a95c74db4062e76c54d4339ccb7343f44067
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "65633567"
---
# <a name="store-the-results-of-a-query-in-memory"></a>Przechowywanie wyników zapytania w pamięci

Kwerenda jest w zasadzie zestaw instrukcji dotyczących pobierania i organizowania danych. Zapytania są wykonywane leniwie, jak każdy kolejny element w wyniku jest wymagane. Gdy używasz `foreach` do iterate wyników, elementy są zwracane jako dostęp. Aby ocenić kwerendę i przechowywać `foreach` jej wyniki bez wykonywania pętli, wystarczy wywołać jedną z następujących metod na zmiennej kwerendy:

- <xref:System.Linq.Enumerable.ToList%2A>

- <xref:System.Linq.Enumerable.ToArray%2A>

- <xref:System.Linq.Enumerable.ToDictionary%2A>

- <xref:System.Linq.Enumerable.ToLookup%2A>

 Zaleca się, aby podczas przechowywania wyników kwerendy przypisano zwrócony obiekt kolekcji do nowej zmiennej, jak pokazano w poniższym przykładzie:

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideLINQ#25](~/samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]

## <a name="see-also"></a>Zobacz też

- [Language Integrated Query (LINQ)](index.md)
