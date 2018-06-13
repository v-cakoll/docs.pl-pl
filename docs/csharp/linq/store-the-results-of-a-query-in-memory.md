---
title: Przechowywanie wyników kwerendy w pamięci
description: Sposób przechowywania wyników.
ms.date: 11/30/2016
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: c125d134d7c1db98363844c12fc8abd3faa9c868
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279636"
---
# <a name="store-the-results-of-a-query-in-memory"></a>Przechowywanie wyników kwerendy w pamięci

Zapytanie jest zasadniczo zestaw instrukcji dotyczących sposobu pobierania i organizowania danych. Zapytania są wykonywane w trybie opóźnienia, żądaną każdego elementu kolejnych w wyniku. Jeśli używasz `foreach` iteracyjne wyniki, elementy są zwracane jako dostępne. Ocena zapytania i przechowywać wyniki bez wykonywania `foreach` pętli, po prostu wywołaj jedną z następujących metod na zmienną zapytania:  
  
-   <xref:System.Linq.Enumerable.ToList%2A>  
  
-   <xref:System.Linq.Enumerable.ToArray%2A>  
  
-   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
-   <xref:System.Linq.Enumerable.ToLookup%2A>  
  
 Zaleca się, czy podczas przechowywania wyników zapytania, można przypisać obiektu zwracana kolekcja do nowej zmiennej jak pokazano w poniższym przykładzie:  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideLINQ#25](../../../samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]  
  

## <a name="see-also"></a>Zobacz też  
 [Wyrażenia zapytań LINQ](index.md)
