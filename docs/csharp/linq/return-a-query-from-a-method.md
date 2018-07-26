---
title: Zwracanie zapytania z metody
description: Jak zwracanie zapytania.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: 13f0839f712cb76b34c98157a30315787d300109
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404161"
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a>Porady: zwracanie zapytania z metody (Przewodnik programowania w języku C#)
W tym przykładzie pokazano, jak zwracanie zapytania z metody jako wartość zwracaną i `out` parametru.  
  
 Obiekty zapytania są konfigurowalna, co oznacza, że można zwracanie zapytania z metody. Nie należy przechowywać obiekty reprezentujące zapytań, wynikowy kolekcji, ale raczej kroki w celu uzyskania wyników, w razie. Zaletą zwracać obiekty zapytania z metody jest, można je dodatkowo składa się lub zmodyfikowany. W związku z tym powrotnych wartość lub `out` parametru metody, która zwraca kwerendy musi również mieć tego typu. Jeśli metoda materializuje zapytania na konkretny <xref:System.Collections.Generic.List%601> lub <xref:System.Array> typu, jest on uznawany za zwracać wyniki kwerendy zamiast samo zapytanie. Zmienna zapytania, który jest zwracany z metody można nadal składa się lub zmodyfikowany.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pierwsza metoda zwraca zapytanie jako wartości zwracanej, a druga metoda zwraca zapytanie jako `out` parametru. Należy pamiętać, że w obu przypadkach zapytanie, które ma zostać zwrócona, nie wyników zapytania.  
  
 [!code-csharp[csProgGuideLINQ#80](~/samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a>Zobacz też  
 [Language Integrated Query (LINQ)](index.md)
