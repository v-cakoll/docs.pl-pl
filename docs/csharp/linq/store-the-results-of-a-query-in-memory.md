---
title: Store wyniki zapytania w pamięci
description: Sposób przechowywania wyników.
ms.date: 11/30/2016
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 52d502a841c428bd90a26c803ba577e76c17197c
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404304"
---
# <a name="store-the-results-of-a-query-in-memory"></a>Store wyniki zapytania w pamięci

Zapytanie jest po prostu zestaw instrukcji dotyczących sposobu pobierania i organizowania danych. Zapytania są wykonywane opóźnieniem, zgodnie z żądaniem jest każdy element kolejne w wyniku. Kiedy używasz `foreach` do iteracji wyników, elementy są zwracane jako dostępne. Ocena zapytania i przechowywać wyniki bez wykonywania `foreach` pętli, po prostu wywołać jedną z następujących metod w zmiennej zapytania:

- <xref:System.Linq.Enumerable.ToList%2A>

- <xref:System.Linq.Enumerable.ToArray%2A>

- <xref:System.Linq.Enumerable.ToDictionary%2A>

- <xref:System.Linq.Enumerable.ToLookup%2A>

 Zaleca się, czy podczas można przechowywać wyników zapytania, można przypisać obiektu zwróconego kolekcji do nowej zmiennej jak pokazano w poniższym przykładzie:

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideLINQ#25](~/samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]

## <a name="see-also"></a>Zobacz także

[Language Integrated Query (LINQ)](index.md)