---
title: Wykonanie odroczone i obliczanie z opóźnieniem w LINQ to XML (C#)
ms.date: 07/20/2015
ms.assetid: 8683d1b4-b7ec-407b-be12-906ebe958a09
ms.openlocfilehash: 83fdc73b583a2c8aba5383f4a5b3af11a1f6f9c4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709692"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-c"></a>Wykonanie odroczone i obliczanie z opóźnieniem w LINQ to XML (C#)
Operacje zapytań i osi są często stosowane do użycia odroczonego wykonania. W tym temacie opisano wymagania i zalety wykonanie odroczone i kilka kwestii dotyczących wdrażania.  
  
## <a name="deferred-execution"></a>Wykonanie odroczone  
 Odroczone wykonania oznacza wyniku obliczenia wyrażenia jest opóźnione aż do jego *zrealizowany* faktycznie wymagana jest wartość. Wykonanie odroczone może znacznie zwiększyć wydajność, gdy masz do manipulowania kolekcji dużych ilości danych, szczególnie w programach, które zawierają szereg zapytań łańcuchowych lub manipulacje. W przypadku najlepszych odroczonego wykonania umożliwia jednej iteracji za pomocą kolekcji źródłowej.  
  
 Technologii LINQ wykorzystać rozbudowane odroczonego wykonania w przypadku członków podstawowych <xref:System.Linq?displayProperty=nameWithType> klas i metod rozszerzenia w różnych obszarach nazw LINQ, takich jak <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.  
  
 Wykonanie odroczone jest obsługiwane bezpośrednio w języku C#, [uzyskanie](../../../../csharp/language-reference/keywords/yield.md) — słowo kluczowe (w postaci `yield-return` instrukcji) używanego w ramach blokiem iteratora. Takie iteratora musi zwracać kolekcję typu <xref:System.Collections.IEnumerator> lub <xref:System.Collections.Generic.IEnumerator%601> (lub typem pochodnym).  
  
## <a name="eager-vs-lazy-evaluation"></a>Zapoznamy programu vs. Obliczanie z opóźnieniem  
 Podczas pisania metody, która implementuje odroczonym należy zdecydować, czy zaimplementować metodę, przy użyciu opóźnieniem lub eager oceny.  
  
-   W *opóźnieniem*, jeden element z kolekcji źródłowej jest przetwarzany w każdym wywołaniu iteratora. Jest to typowy sposób, w którym są implementowane Iteratory.  
  
-   W *eager oceny*, pierwsze wywołanie funkcji iteratora spowoduje całą kolekcję przetwarzany. Tymczasową kopię kolekcji źródłowej, mogą być także wymagane. Na przykład <xref:System.Linq.Enumerable.OrderBy%2A> metoda ma sortowania całą kolekcję przed zwróceniem pierwszego elementu.  
  
 Obliczanie leniwe zwykle daje lepszą wydajność, ponieważ dystrybuuje obciążenie przetwarzania równomiernie w całej oceny kolekcji, a minimalizuje wykorzystanie danych tymczasowych. Oczywiście w przypadku niektórych operacji nie ma innych opcji niż celu zmaterializowania wyników pośrednich.  
  
## <a name="next-steps"></a>Następne kroki  
 Następny temat w tym samouczku przedstawiono odroczonego wykonania:  
  
-   [Przykład wykonania odroczonego (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a>Zobacz także

- [Samouczek: Łączenie łańcuchowe zapytań (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
- [Pojęcia i terminologia (Przekształcanie funkcjonalne) (C#)](../../../../csharp/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)
- [Operacje agregacji (C#)](../../../../csharp/programming-guide/concepts/linq/aggregation-operations.md)
- [yield](../../../../csharp/language-reference/keywords/yield.md)
