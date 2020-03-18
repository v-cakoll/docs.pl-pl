---
title: Zwracanie zapytania z metody
description: Jak zwrócić zapytanie.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: 1df533770f76301432b104d6f8398f1687750cce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73972523"
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a>Jak zwrócić zapytanie z metody (Przewodnik programowania C#)
W tym przykładzie pokazano, jak zwrócić kwerendę z `out` metody jako wartość zwracaną i jako parametr.  
  
 Obiekty kwerendy można składać, co oznacza, że można zwrócić kwerendę z metody. Obiekty reprezentujące kwerendy nie przechowują wynikowej kolekcji, ale raczej kroki, aby uzyskać wyniki w razie potrzeby. Zaletą zwracania obiektów kwerendy z metod jest to, że mogą być dalej składa się lub modyfikowane. W związku z `out` tym każda wartość zwracana lub parametr metody, która zwraca kwerendę musi mieć również tego typu. Jeśli metoda materializuje kwerendy do <xref:System.Collections.Generic.List%601> konkretnego <xref:System.Array> lub typu, jest uważany za zwracanie wyników kwerendy zamiast samej kwerendy. Zmienna kwerendy, która jest zwracana z metody nadal mogą być składane lub modyfikowane.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pierwsza metoda zwraca kwerendę jako wartość zwracaną, a `out` druga metoda zwraca kwerendę jako parametr. Należy zauważyć, że w obu przypadkach jest to kwerenda, która jest zwracana, a nie wyniki kwerendy.  
  
 [!code-csharp[csProgGuideLINQ#80](~/samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a>Zobacz też

- [Language Integrated Query (LINQ)](index.md)
