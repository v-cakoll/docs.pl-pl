---
title: Odroczone wykonanie i ocena z opóźnieniem w LINQ do XML (C#)
ms.date: 07/20/2015
ms.assetid: 8683d1b4-b7ec-407b-be12-906ebe958a09
ms.openlocfilehash: 9cf28afb5b7b8b3047c8b1b21915ffe7409eb25e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69594568"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-c"></a>Odroczone wykonanie i ocena z opóźnieniem w LINQ do XML (C#)
Kwerendy i operacji osi są często implementowane do korzystania z odroczonego wykonania. W tym temacie wyjaśniono wymagania i zalety odroczonego wykonania i niektóre zagadnienia dotyczące implementacji.  
  
## <a name="deferred-execution"></a>Wykonanie odroczone  
 Odroczone wykonanie oznacza, że ocena wyrażenia jest opóźniona, dopóki jego *wartość jest* faktycznie wymagana. Odroczone wykonanie może znacznie zwiększyć wydajność, gdy trzeba manipulować dużych zbiorów danych, szczególnie w programach, które zawierają serię zapytań łańcuchowych lub manipulacji. W najlepszym przypadku odroczone wykonanie umożliwia tylko pojedynczą iterację za pośrednictwem kolekcji źródłowej.  
  
 Technologie LINQ szeroko wykorzystują odroczone wykonanie zarówno w <xref:System.Linq?displayProperty=nameWithType> elementach członkowskich klas podstawowych, jak i w metodach rozszerzenia w różnych przestrzeniach nazw LINQ, takich jak <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.  
  
 Odroczone wykonanie jest obsługiwane bezpośrednio w języku C# przez [yield](../../../language-reference/keywords/yield.md) `yield-return` — słowo kluczowe (w postaci instrukcji) w przypadku użycia w bloku iteratorem. Taki iterator musi zwrócić kolekcję typu <xref:System.Collections.IEnumerator> lub <xref:System.Collections.Generic.IEnumerator%601> (lub typu pochodnego).  
  
## <a name="eager-vs-lazy-evaluation"></a>Chętni kontra Leniwi ocena  
 Podczas pisania metody, która implementuje odroczone wykonanie, należy również zdecydować, czy zaimplementować metodę przy użyciu oceny z opóźnieniem lub chętnie oceny.  
  
- W *ocenie z opóźnieniem*, pojedynczy element kolekcji źródłowej jest przetwarzany podczas każdego wywołania iteratodawcy. Jest to typowy sposób implementacji iteratorów.  
  
- W *chętnej oceny*, pierwsze wywołanie iterator spowoduje całą kolekcję przetwarzane. Może być również wymagana tymczasowa kopia kolekcji źródłowej. Na przykład <xref:System.Linq.Enumerable.OrderBy%2A> metoda musi posortować całą kolekcję, zanim zwróci pierwszy element.  
  
 Ocena z opóźnieniem zwykle daje lepszą wydajność, ponieważ dystrybuuje przetwarzanie narzutów równomiernie w całej oceny kolekcji i minimalizuje użycie danych tymczasowych. Oczywiście w przypadku niektórych operacji nie ma innej możliwości niż zmaterializować wyniki pośrednie.  
  
## <a name="next-steps"></a>Następne kroki  
 Następny temat w tym samouczku ilustruje odroczone wykonanie:  
  
- [Przykład odroczonego wykonania (C#)](./deferred-execution-example.md)  
  
## <a name="see-also"></a>Zobacz też

- [Samouczek: Łączenie zapytań razem (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
- [Pojęcia i terminologia (transformacja funkcjonalna) (C#)](./concepts-and-terminology-functional-transformation.md)
- [Operacje agregacji (C#)](./aggregation-operations.md)
- [yield](../../../language-reference/keywords/yield.md)
