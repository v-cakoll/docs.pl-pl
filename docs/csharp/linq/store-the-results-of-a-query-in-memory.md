---
title: Przechowywanie wyników zapytania w pamięci
description: Sposób przechowywania wyników.
ms.date: 11/30/2016
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 98a300b2c11eb037ed4ce34caea2673a4e0f8e6b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61688439"
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