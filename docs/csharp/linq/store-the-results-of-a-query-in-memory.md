---
title: "Przechowywanie wyników kwerendy w pamięci"
description: "Sposób przechowywania wyników."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 86a9c2d464eac83cabb5faa68987ad580fc31248
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
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
