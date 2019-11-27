---
title: Wykonanie odroczone i obliczanie z opóźnieniem w LINQ to XML
ms.date: 07/20/2015
ms.assetid: 31998eed-b95e-47fb-a865-9de1f337d1fb
ms.openlocfilehash: 8e94b9133a2d2dd287fba91600c94460a5204b2c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346405"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-visual-basic"></a>Wykonywanie odroczone i Ocena z opóźnieniem w LINQ to XML (Visual Basic)
Operacje zapytań i osi często są implementowane w celu użycia odroczonego wykonania. W tym temacie opisano wymagania i zalety odroczonego wykonywania oraz niektóre zagadnienia dotyczące implementacji.  
  
## <a name="deferred-execution"></a>Wykonanie odroczone  
 Wykonywanie odroczone oznacza, że Obliczanie wyrażenia jest opóźnione do momentu, gdy wartość *rzeczywista* jest wymagana. Wykonywanie odroczone może znacznie poprawić wydajność, gdy trzeba manipulować dużymi kolekcjami danych, szczególnie w programach, które zawierają serię zapytań lub manipulacji łańcucha. W najlepszym przypadku wykonywanie odroczone włącza tylko jedną iterację za pomocą kolekcji źródłowej.  
  
 Technologie LINQ wykorzystują szerokie użycie odroczonego wykonania w obu elementach członkowskich klas podstawowych <xref:System.Linq?displayProperty=nameWithType> i w metodach rozszerzających w różnych przestrzeniach nazw LINQ, takich jak <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.  
  
## <a name="eager-vs-lazy-evaluation"></a>Ocena eager a z opóźnieniem  
 Podczas pisania metody, która implementuje wykonywanie odroczone, należy również zdecydować, czy zaimplementować metodę przy użyciu oceny z opóźnieniem czy oceny eager.  
  
- W *ocenie z opóźnieniem*pojedynczy element kolekcji źródłowej jest przetwarzany podczas każdego wywołania iteratora. Jest to typowy sposób implementacji iteratorów.  
  
- W *ocenie eager*pierwsze wywołanie iteratora spowoduje przetworzenie całej kolekcji. Może być również wymagana tymczasowa kopia kolekcji źródłowej. Na przykład Metoda <xref:System.Linq.Enumerable.OrderBy%2A> musi sortować całą kolekcję przed zwróceniem pierwszego elementu.  
  
 Ocena z opóźnieniem zwykle zapewnia lepszą wydajność, ponieważ dystrybuuje przetwarzanie narzutowe równomiernie przez oszacowanie kolekcji i minimalizuje użycie danych tymczasowych. Oczywiście w przypadku niektórych operacji nie ma żadnej innej opcji, aby zmaterializowania wyniki pośrednie.  
  
## <a name="next-steps"></a>Następne kroki  
 Następny temat w tym samouczku ilustruje odroczone wykonywanie:  
  
- [Przykład wykonania odroczonego (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a>Zobacz także

- [Samouczek: wykonywanie odroczone (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
- [Pojęcia i terminologia (przekształcenie funkcjonalne) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)
- [Operacje agregacji (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)
