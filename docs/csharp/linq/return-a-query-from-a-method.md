---
title: Zwracanie kwerendy z metody
description: "Sposób zwracania zapytania."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: c1b69e3f5f0cd2c50ae80d2454e6b7f13dc30344
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a>Porady: zwracanie zapytania z metody (Przewodnik programowania w języku C#)
W tym przykładzie pokazano, jak zwracanie kwerendy z metody jako wartość zwracaną, a `out` parametru.  
  
 Obiekty zapytania są zezwala na składanie, co oznacza, że można zwracanie kwerendy z metody. Obiekty, które reprezentują zapytania nie należy przechowywać wynikowy kolekcji, ale raczej kroki w celu uzyskania wyników w razie potrzeby. Zaletą zwracać obiekty zapytania z metody jest że mogą zostać dalsze składane albo zmodyfikować. W związku z tym wszelkie zwracać wartość lub `out` parametru metody, która zwraca zapytania musi mieć również tego typu. Jeśli metoda zostaje kwerendy do konkretnych <xref:System.Collections.Generic.List%601> lub <xref:System.Array> typu, jest on uznawany za zwracać wyniki zapytania, zamiast samą kwerendę. Można nadal składa się zmienną zapytania, która jest zwracana z metody lub zmodyfikowany.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pierwsza metoda zwraca zapytanie jako wartości zwracane, a druga metoda zwraca zapytanie jako `out` parametru. Należy pamiętać, że w obu przypadkach kwerendę, która jest zwracana nie wyników zapytania.  
  
 [!code-csharp[csProgGuideLINQ#80](../../../samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a>Zobacz też  
 [Wyrażenia zapytań LINQ](index.md)
