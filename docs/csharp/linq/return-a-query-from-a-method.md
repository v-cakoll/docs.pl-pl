---
title: Zwracanie zapytania z metody
description: Jak zwrócić zapytanie.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: 1df533770f76301432b104d6f8398f1687750cce
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73972523"
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a>Jak zwrócić zapytanie z metody (C# Przewodnik programowania)
Ten przykład przedstawia sposób zwrócenia zapytania z metody jako wartości zwracanej i jako parametru `out`.  
  
 Obiekty zapytań są możliwe do redagowania, co oznacza, że można zwrócić zapytanie z metody. Obiekty reprezentujące zapytania nie przechowują wynikowej kolekcji, ale zamiast kroków w celu wygenerowania wyników w razie potrzeby. Zaletą zwracania obiektów zapytań z metod jest, że mogą one być bardziej złożone lub zmodyfikowane. W związku z tym każda wartość zwracana lub `out` parametr metody, która zwraca zapytanie, musi również mieć ten typ. Jeśli metoda materializuje zapytanie w konkretną <xref:System.Collections.Generic.List%601> lub <xref:System.Array>, jest uznawane za zwracające wyniki zapytania zamiast samego zapytania. Zmienna zapytania, która jest zwracana z metody, może być w dalszym ciągu złożona lub zmodyfikowana.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pierwsza metoda zwraca zapytanie jako wartość zwracaną, a druga metoda zwraca zapytanie jako parametr `out`. Należy zauważyć, że w obu przypadkach jest to zapytanie, które jest zwracane, a nie wyniki zapytania.  
  
 [!code-csharp[csProgGuideLINQ#80](~/samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a>Zobacz także

- [Language Integrated Query (LINQ)](index.md)
