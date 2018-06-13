---
title: REF zwracanych wartości (Visual Basic)
ms.date: 04/28/2017
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2979359f0ffafe46a62696485bbb87b211c1704
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651244"
---
# <a name="support-for-reference-return-values-visual-basic"></a>Obsługa odwołanie zwracane wartości (Visual Basic)

Począwszy od wersji 7.0 C#, obsługuje języka C# *odwołanie zwracane wartości*. Jednym ze sposobów zrozumieć zwracanych wartości odwołania jest są przeciwieństwem argumenty, które są przekazywane przez odwołanie do metody. Po zmodyfikowaniu argument przekazany przez odwołanie, zmiany zostaną odzwierciedlone w wartości zmiennej na wywołującego. Metoda zapewnia wartości zwracanej odwołania do wywołującego, modyfikacje odwołanie wartość zwracaną przez obiekt wywołujący są odzwierciedlane w danych wywołaną metodę.

Visual Basic nie zezwala na wartości do metod autora z odwołaniem zwracane, ale pozwala korzystać zwracanych wartości odwołania. Innymi słowy można wywołać metodę z wartością zwracaną odwołania i modyfikować tej wartości zwracanej, a zmiany zwracana wartość odwołania są odzwierciedlane w danych wywołaną metodę.

## <a name="modifying-the-ref-return-value-directly"></a>Bezpośrednie modyfikowanie zwracana wartość ref

Dla metod, które zawsze powiedzie się i nie mają `ByRef` parametry, można zmodyfikować zwracanej wartości odwołania, bezpośrednio. Można to zrobić, przypisując nową wartość do wyrażeń, które zwraca wartość zwracaną odwołania. 

W poniższym przykładzie C# definiuje `NumericValue.IncrementValue` wartość zwracana z metody, która zwiększa wewnętrzne wartości i zwraca go jako odwołanie. 

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

Odwołanie zwracać wartość następnie jest modyfikowany przez obiekt wywołujący w poniższym przykładzie w języku Visual Basic. Należy pamiętać, że wiersz z `NumericValue.IncrementValue` wywołanie metody nie przypisuje wartość do metody. Zamiast tego przypisuje wartość do wartości zwracane odwołanie zwracany przez metodę.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a>Przy użyciu metody pomocnika

W pozostałych przypadkach bezpośrednie modyfikowanie odwołanie zwracana wartość wywołania metody mogą nie być pożądane. Na przykład metoda wyszukiwania, która zwraca ciąg może nie zawsze znaleźć dopasowania. W takim przypadku chcesz zmodyfikować zwracanej wartości odwołania, tylko jeśli wyszukiwanie powiedzie się.

W poniższym przykładzie C# przedstawiono w tym scenariuszu. Definiuje `Sentence` klasa napisane w języku C# zawiera `FindNext` metodę, która znajduje następny wyraz w zdaniu zaczyna się od wskazany podciąg. Jako wartość zwracana przez odwołanie i zostanie zwrócony ciąg `Boolean` zmiennej przekazywana przez odwołanie do metody wskazuje, czy wyszukiwanie zakończyła się powodzeniem. Wartość zwracana odwołania wskazuje, że obiekt wywołujący nie może tylko odczytać zwrócona wartość; on również ją zmodyfikować, i tej zmiany jest widoczny w danych zawartych w wewnętrznie `Sentence` klasy.

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

Bezpośrednie modyfikowanie odwołanie zwracać wartość w tym przypadku nie jest niezawodne, ponieważ wywołanie metody może nie znaleziono dopasowania i zwraca pierwsze słowo w zdaniu. W takim przypadku obiekt wywołujący przypadkowo zmodyfikuje pierwsze słowo zdania. To można zapobiegać przez obiekt wywołujący zwracanie `null` (lub `Nothing` w języku Visual Basic). Jednak w takim przypadku próby zmodyfikowania ciągu, którego wartość jest `Nothing` zgłasza <xref:System.NullReferenceException>. Jeśli można również blokowane przez obiekt wywołujący zwracanie <xref:System.String.Empty?displayProperty=nameWithType>, ale wymaga to, że wywołującego Definiowanie zmiennej ciągu, którego wartość jest <xref:System.String.Empty?displayProperty=nameWithType>. Gdy obiekt wywołujący można modyfikować tego ciągu, modyfikacja sam służy bezcelowe, ponieważ zmodyfikowany ciąg nie ma relacji wyrazy w zdaniu przechowywane przez `Sentence` klasy.

Najlepszy sposób, aby obsługiwać ten scenariusz jest zwracana wartość odwołania jest przekazywany za pomocą odwołań do metody pomocnika. Metoda pomocnika zawiera następnie logika do określenia, czy wywołania metody, które zakończyło się pomyślnie, a jeśli go tak, aby zmodyfikować odwołanie zwracają wartość. W poniższym przykładzie przedstawiono możliwe implementacji.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a>Zobacz także

[Przekazywanie argumentów według wartości i według odwołania](passing-arguments-by-value-and-by-reference.md)   
[Procedury w Visual Basic](index.md)   


