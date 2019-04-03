---
title: Wykonanie odroczone i obliczanie z opóźnieniem w LINQ to XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 31998eed-b95e-47fb-a865-9de1f337d1fb
ms.openlocfilehash: b5c3e2a484aa16df22742ddf77d6438ec2a699bb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839041"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-visual-basic"></a>Wykonanie odroczone i obliczanie z opóźnieniem w LINQ to XML (Visual Basic)
Operacje zapytań i osi są często stosowane do użycia odroczonego wykonania. W tym temacie opisano wymagania i zalety wykonanie odroczone i kilka kwestii dotyczących wdrażania.  
  
## <a name="deferred-execution"></a>Wykonanie odroczone  
 Odroczone wykonania oznacza wyniku obliczenia wyrażenia jest opóźnione aż do jego *zrealizowany* faktycznie wymagana jest wartość. Wykonanie odroczone może znacznie zwiększyć wydajność, gdy masz do manipulowania kolekcji dużych ilości danych, szczególnie w programach, które zawierają szereg zapytań łańcuchowych lub manipulacje. W przypadku najlepszych odroczonego wykonania umożliwia jednej iteracji za pomocą kolekcji źródłowej.  
  
 Technologii LINQ wykorzystać rozbudowane odroczonego wykonania w przypadku członków podstawowych <xref:System.Linq?displayProperty=nameWithType> klas i metod rozszerzenia w różnych obszarach nazw LINQ, takich jak <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.  
  
## <a name="eager-vs-lazy-evaluation"></a>Zapoznamy programu vs. Obliczanie z opóźnieniem  
 Podczas pisania metody, która implementuje odroczonym należy zdecydować, czy zaimplementować metodę, przy użyciu opóźnieniem lub eager oceny.  
  
-   W *opóźnieniem*, jeden element z kolekcji źródłowej jest przetwarzany w każdym wywołaniu iteratora. Jest to typowy sposób, w którym są implementowane Iteratory.  
  
-   W *eager oceny*, pierwsze wywołanie funkcji iteratora spowoduje całą kolekcję przetwarzany. Tymczasową kopię kolekcji źródłowej, mogą być także wymagane. Na przykład <xref:System.Linq.Enumerable.OrderBy%2A> metoda ma sortowania całą kolekcję przed zwróceniem pierwszego elementu.  
  
 Obliczanie leniwe zwykle daje lepszą wydajność, ponieważ dystrybuuje obciążenie przetwarzania równomiernie w całej oceny kolekcji, a minimalizuje wykorzystanie danych tymczasowych. Oczywiście w przypadku niektórych operacji nie ma innych opcji niż celu zmaterializowania wyników pośrednich.  
  
## <a name="next-steps"></a>Następne kroki  
 Następny temat w tym samouczku przedstawiono odroczonego wykonania:  
  
-   [Przykład wykonania odroczonego (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a>Zobacz także

- [Samouczek: Wykonanie odroczone (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
- [Pojęcia i terminologia (Przekształcanie funkcjonalne) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)
- [Operacje agregacji (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)
