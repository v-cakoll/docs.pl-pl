---
title: Przechowywanie wyników zapytania w pamięci
description: Sposób przechowywania wyników.
ms.date: 11/30/2016
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 66a7a95c74db4062e76c54d4339ccb7343f44067
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633567"
---
# <a name="store-the-results-of-a-query-in-memory"></a>Przechowywanie wyników zapytania w pamięci

Zapytanie jest po prostu zestaw instrukcji dotyczących sposobu pobierania i organizowania danych. Zapytania są wykonywane opóźnieniem, zgodnie z żądaniem jest każdy element kolejne w wyniku. Kiedy używasz `foreach` do iteracji wyników, elementy są zwracane jako dostępne. Ocena zapytania i przechowywać wyniki bez wykonywania `foreach` pętli, po prostu wywołać jedną z następujących metod w zmiennej zapytania:

- <xref:System.Linq.Enumerable.ToList%2A>

- <xref:System.Linq.Enumerable.ToArray%2A>

- <xref:System.Linq.Enumerable.ToDictionary%2A>

- <xref:System.Linq.Enumerable.ToLookup%2A>

 Zaleca się, czy podczas można przechowywać wyników zapytania, można przypisać obiektu zwróconego kolekcji do nowej zmiennej jak pokazano w poniższym przykładzie:

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideLINQ#25](~/samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]

## <a name="see-also"></a>Zobacz także

- [Language Integrated Query (LINQ)](index.md)
