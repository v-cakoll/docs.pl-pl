---
title: Zwracanie zapytania z metody
description: Jak zwracanie zapytania.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: fe2192a3edb683d7284ffae3b66cb9f70e8854b1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61659829"
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a>Instrukcje: Zwracanie zapytania z metody (C# Programming Guide)
W tym przykładzie pokazano, jak zwracanie zapytania z metody jako wartość zwracaną i `out` parametru.  
  
 Obiekty zapytania są konfigurowalna, co oznacza, że można zwracanie zapytania z metody. Nie należy przechowywać obiekty reprezentujące zapytań, wynikowy kolekcji, ale raczej kroki w celu uzyskania wyników, w razie. Zaletą zwracać obiekty zapytania z metody jest, można je dodatkowo składa się lub zmodyfikowany. W związku z tym powrotnych wartość lub `out` parametru metody, która zwraca kwerendy musi również mieć tego typu. Jeśli metoda materializuje zapytania na konkretny <xref:System.Collections.Generic.List%601> lub <xref:System.Array> typu, jest on uznawany za zwracać wyniki kwerendy zamiast samo zapytanie. Zmienna zapytania, który jest zwracany z metody można nadal składa się lub zmodyfikowany.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pierwsza metoda zwraca zapytanie jako wartości zwracanej, a druga metoda zwraca zapytanie jako `out` parametru. Należy pamiętać, że w obu przypadkach zapytanie, które ma zostać zwrócona, nie wyników zapytania.  
  
 [!code-csharp[csProgGuideLINQ#80](~/samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a>Zobacz także

- [Language Integrated Query (LINQ)](index.md)
