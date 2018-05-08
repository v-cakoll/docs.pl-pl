---
title: Zwracanie kwerendy z metody
description: Sposób zwracania zapytania.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: 6a1d581c46c7b0b2062859fd60701dd25ea54eea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a>Porady: zwracanie zapytania z metody (Przewodnik programowania w języku C#)
W tym przykładzie pokazano, jak zwracanie kwerendy z metody jako wartość zwracaną, a `out` parametru.  
  
 Obiekty zapytania są zezwala na składanie, co oznacza, że można zwracanie kwerendy z metody. Obiekty, które reprezentują zapytania nie należy przechowywać wynikowy kolekcji, ale raczej kroki w celu uzyskania wyników w razie potrzeby. Zaletą zwracać obiekty zapytania z metody jest że mogą zostać dalsze składane albo zmodyfikować. W związku z tym wszelkie zwracać wartość lub `out` parametru metody, która zwraca zapytania musi mieć również tego typu. Jeśli metoda zostaje kwerendy do konkretnych <xref:System.Collections.Generic.List%601> lub <xref:System.Array> typu, jest on uznawany za zwracać wyniki zapytania, zamiast samą kwerendę. Można nadal składa się zmienną zapytania, która jest zwracana z metody lub zmodyfikowany.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pierwsza metoda zwraca zapytanie jako wartości zwracane, a druga metoda zwraca zapytanie jako `out` parametru. Należy pamiętać, że w obu przypadkach kwerendę, która jest zwracana nie wyników zapytania.  
  
 [!code-csharp[csProgGuideLINQ#80](../../../samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a>Zobacz też  
 [Wyrażenia zapytań LINQ](index.md)
