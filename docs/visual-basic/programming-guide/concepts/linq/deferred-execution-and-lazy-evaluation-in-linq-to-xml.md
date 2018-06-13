---
title: Wykonanie odroczone i obliczanie leniwe w składniku LINQ to XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 31998eed-b95e-47fb-a865-9de1f337d1fb
ms.openlocfilehash: eade2fe987ecbc399c2e2a8a65e74e3beab5e123
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643127"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-visual-basic"></a>Wykonanie odroczone i obliczanie leniwe w składniku LINQ to XML (Visual Basic)
Operacje zapytań i osi są często stosowane do użycia odroczonego wykonania. W tym temacie opisano wymagania i zalety wykonanie odroczone oraz pewne zagadnienia implementacji.  
  
## <a name="deferred-execution"></a>Wykonanie odroczone  
 Odroczone wykonywania oznacza, że obliczania wyrażenia jest opóźnione aż do jego *zrealizowane* faktycznie wymagana jest wartość. Wykonanie odroczone może znacznie poprawić wydajność podczas modyfikowania kolekcji dużej ilości danych, szczególnie w programach, które zawierają ciąg kwerendy łańcuchowych lub manipulacji. W najlepszym przypadku wykonanie odroczone umożliwia tylko jednego iteracji za pomocą kolekcji źródłowej.  
  
 Technologie LINQ umożliwiają zwiększone użycie odroczonego wykonania w przypadku członków podstawowych <xref:System.Linq?displayProperty=nameWithType> klas i metod rozszerzenia w różnych przestrzeniach nazw LINQ, takich jak <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.  
  
## <a name="eager-vs-lazy-evaluation"></a>Wczesny vs. Obliczanie leniwe  
 Podczas pisania metodę, która implementuje wykonanie odroczone należy zdecydować, czy należy zaimplementować metodę przy użyciu obliczanie leniwe lub wczesny oceny.  
  
-   W *obliczanie leniwe*, pojedynczy element kolekcji źródłowej jest przetwarzany każde wywołanie iteratora. To jest typowym sposobem, w którym Iteratory są implementowane.  
  
-   W *wczesny oceny*, pierwsze wywołanie w celu iteratora spowoduje całą kolekcję przetwarzane. Mogą być także wymagane tymczasową kopię kolekcji źródłowej. Na przykład <xref:System.Linq.Enumerable.OrderBy%2A> metoda ma sortowania całą kolekcję przed zwraca pierwszy element.  
  
 Obliczanie leniwe zazwyczaj daje lepszą wydajność, ponieważ dystrybuuje większe obciążenie przetwarzania równomiernie w całej oceny kolekcji i minimalizuje dane tymczasowe. Oczywiście dla niektórych operacji, nie ma żadnych innych opcji niż aby zmaterializowania pośrednich wyników.  
  
## <a name="next-steps"></a>Następne kroki  
 Następnego tematu w tym samouczku przedstawiono odroczonego wykonania:  
  
-   [Wykonanie odroczone — przykład (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Samouczek: Odroczonego wykonania (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)  
 [Pojęcia i terminologię (funkcjonalności przekształcania) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)  
 [Operacje agregacji (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)
