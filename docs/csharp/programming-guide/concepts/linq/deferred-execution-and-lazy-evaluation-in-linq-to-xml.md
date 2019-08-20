---
title: Wykonywanie odroczone i Ocena z opóźnieniem w LINQ to XMLC#()
ms.date: 07/20/2015
ms.assetid: 8683d1b4-b7ec-407b-be12-906ebe958a09
ms.openlocfilehash: 9cf28afb5b7b8b3047c8b1b21915ffe7409eb25e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594568"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-c"></a>Wykonywanie odroczone i Ocena z opóźnieniem w LINQ to XMLC#()
Operacje zapytań i osi często są implementowane w celu użycia odroczonego wykonania. W tym temacie opisano wymagania i zalety odroczonego wykonywania oraz niektóre zagadnienia dotyczące implementacji.  
  
## <a name="deferred-execution"></a>Wykonanie odroczone  
 Wykonywanie odroczone oznacza, że Obliczanie wyrażenia jest opóźnione do momentu, gdy wartość rzeczywista jest wymagana. Wykonywanie odroczone może znacznie poprawić wydajność, gdy trzeba manipulować dużymi kolekcjami danych, szczególnie w programach, które zawierają serię zapytań lub manipulacji łańcucha. W najlepszym przypadku wykonywanie odroczone włącza tylko jedną iterację za pomocą kolekcji źródłowej.  
  
 Technologie LINQ umożliwiają użycie odroczonego wykonania w obu elementach członkowskich klas podstawowych <xref:System.Linq?displayProperty=nameWithType> i w metodach rozszerzających w różnych przestrzeniach nazw LINQ, takich jak. <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>  
  
 Wykonywanie odroczone jest obsługiwane bezpośrednio w C# języku za pomocą słowa kluczowego [Yield](../../../language-reference/keywords/yield.md) (w `yield-return` formie instrukcji), gdy jest używana w bloku iteratora. Taki iterator musi zwracać kolekcję typu <xref:System.Collections.IEnumerator> lub <xref:System.Collections.Generic.IEnumerator%601> (lub typu pochodnego).  
  
## <a name="eager-vs-lazy-evaluation"></a>Eager a Ocena z opóźnieniem  
 Podczas pisania metody, która implementuje wykonywanie odroczone, należy również zdecydować, czy zaimplementować metodę przy użyciu oceny z opóźnieniem czy oceny eager.  
  
- W *ocenie*z opóźnieniem pojedynczy element kolekcji źródłowej jest przetwarzany podczas każdego wywołania iteratora. Jest to typowy sposób implementacji iteratorów.  
  
- W *ocenie eager*pierwsze wywołanie iteratora spowoduje przetworzenie całej kolekcji. Może być również wymagana tymczasowa kopia kolekcji źródłowej. Na przykład <xref:System.Linq.Enumerable.OrderBy%2A> Metoda musi sortować całą kolekcję przed zwróceniem pierwszego elementu.  
  
 Ocena z opóźnieniem zwykle zapewnia lepszą wydajność, ponieważ dystrybuuje przetwarzanie narzutowe równomiernie przez oszacowanie kolekcji i minimalizuje użycie danych tymczasowych. Oczywiście w przypadku niektórych operacji nie ma żadnej innej opcji, aby zmaterializowania wyniki pośrednie.  
  
## <a name="next-steps"></a>Następne kroki  
 Następny temat w tym samouczku ilustruje odroczone wykonywanie:  
  
- [Przykład wykonania odroczonego (C#)](./deferred-execution-example.md)  
  
## <a name="see-also"></a>Zobacz także

- [Samouczek: Łączenie łańcuchowe zapytań (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
- [Pojęcia i terminologia (przekształcenie funkcjonalne)C#()](./concepts-and-terminology-functional-transformation.md)
- [Operacje agregacjiC#()](./aggregation-operations.md)
- [yield](../../../language-reference/keywords/yield.md)
