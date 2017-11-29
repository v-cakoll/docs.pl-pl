---
title: "Wykonanie odroczone i obliczanie leniwe w składniku LINQ to XML (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 8683d1b4-b7ec-407b-be12-906ebe958a09
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 847d8f830c26f54521664accc4bf569f822f255a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-c"></a>Wykonanie odroczone i obliczanie leniwe w składniku LINQ to XML (C#)
Operacje zapytań i osi są często stosowane do użycia odroczonego wykonania. W tym temacie opisano wymagania i zalety wykonanie odroczone oraz pewne zagadnienia implementacji.  
  
## <a name="deferred-execution"></a>Wykonanie odroczone  
 Odroczone wykonywania oznacza, że obliczania wyrażenia jest opóźnione aż do jego *zrealizowane* faktycznie wymagana jest wartość. Wykonanie odroczone może znacznie poprawić wydajność podczas modyfikowania kolekcji dużej ilości danych, szczególnie w programach, które zawierają ciąg kwerendy łańcuchowych lub manipulacji. W najlepszym przypadku wykonanie odroczone umożliwia tylko jednego iteracji za pomocą kolekcji źródłowej.  
  
 Technologie LINQ umożliwiają zwiększone użycie odroczonego wykonania w przypadku członków podstawowych <xref:System.Linq?displayProperty=nameWithType> klas i metod rozszerzenia w różnych przestrzeniach nazw LINQ, takich jak <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.  
  
 Wykonanie odroczone jest obsługiwane bezpośrednio w języku C#, przez [yield](../../../../csharp/language-reference/keywords/yield.md) — słowo kluczowe (w postaci `yield-return` instrukcji) używanego w ramach blokiem iteratora. Takie iteratora musi zwracać kolekcję typu <xref:System.Collections.IEnumerator> lub <xref:System.Collections.Generic.IEnumerator%601> (lub typu pochodnego).  
  
## <a name="eager-vs-lazy-evaluation"></a>Wczesny vs. Obliczanie leniwe  
 Podczas pisania metodę, która implementuje wykonanie odroczone należy zdecydować, czy należy zaimplementować metodę przy użyciu obliczanie leniwe lub wczesny oceny.  
  
-   W *obliczanie leniwe*, pojedynczy element kolekcji źródłowej jest przetwarzany każde wywołanie iteratora. To jest typowym sposobem, w którym Iteratory są implementowane.  
  
-   W *wczesny oceny*, pierwsze wywołanie w celu iteratora spowoduje całą kolekcję przetwarzane. Mogą być także wymagane tymczasową kopię kolekcji źródłowej. Na przykład <xref:System.Linq.Enumerable.OrderBy%2A> metoda ma sortowania całą kolekcję przed zwraca pierwszy element.  
  
 Obliczanie leniwe zazwyczaj daje lepszą wydajność, ponieważ dystrybuuje większe obciążenie przetwarzania równomiernie w całej oceny kolekcji i minimalizuje dane tymczasowe. Oczywiście dla niektórych operacji, nie ma żadnych innych opcji niż aby zmaterializowania pośrednich wyników.  
  
## <a name="next-steps"></a>Następne kroki  
 Następnego tematu w tym samouczku przedstawiono odroczonego wykonania:  
  
-   [Wykonanie odroczone przykład (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Samouczek: Tworzenie łańcuchów zapytań razem (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)  
 [Pojęcia i terminologię (funkcjonalności przekształcania) (C#)](../../../../csharp/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)  
 [Operacje agregacji (C#)](../../../../csharp/programming-guide/concepts/linq/aggregation-operations.md)  
 [YIELD](../../../../csharp/language-reference/keywords/yield.md)
