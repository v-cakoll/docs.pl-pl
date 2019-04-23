---
title: Wartości zwracane REF (Visual Basic)
ms.date: 04/28/2017
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
ms.openlocfilehash: d0600f7d9030324160343e800c37e0f5e68bff61
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133981"
---
# <a name="support-for-reference-return-values-visual-basic"></a>Obsługa wartości zwracane odwołanie (Visual Basic)

Począwszy od C# 7.0, C# obsługuje język *odwoływać się do wartości zwracane*. Jednym ze sposobów, aby zrozumieć wartości zwracane odwołanie jest możliwość ich przeciwieństwo argumenty, które są przekazywane przez odwołanie do metody. Po zmodyfikowaniu argument przekazywany przez odwołanie, zmiany są odzwierciedlane w wartości zmiennej na obiekcie wywołującym. Modyfikacje wprowadzone do odwołania wartość zwracana przez obiekt wywołujący metodę zawiera wartość zwracaną odwołanie do elementu wywołującego, są odzwierciedlane w danych o nazwie metody.

Visual Basic nie zezwala na umożliwia tworzenie metod z odwołaniem do wartości zwracane, ale go zezwala na używanie wartości zwracane odwołanie. Innymi słowy można wywołać metody zawierającej określenie zwracanej wartości odniesienia i modyfikować tej wartości zwracanej, a zmiany na wartość zwracaną odwołania są uwzględniane w danych o nazwie metody.

## <a name="modifying-the-ref-return-value-directly"></a>Modyfikowanie bezpośrednio zwracana wartość ref

Dla metod, które zawsze powiedzie się i nie mają `ByRef` parametry, zwracana wartość odniesienia można zmodyfikować bezpośrednio. W tym celu przypisywania nową wartość do wyrażenia, które zwraca wartość zwracaną odwołania. 

Następujące C# przykładzie zdefiniowano `NumericValue.IncrementValue` metodę, która zwiększa wartość będącą liczbą wewnętrzny i zwraca go jako odwołanie zwracają wartość. 

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

Odwołanie zwracana wartość jest następnie modyfikowana przez obiekt wywołujący w poniższym przykładzie w języku Visual Basic. Należy pamiętać, że wiersz z `NumericValue.IncrementValue` wywołanie metody nie przypisuje wartość do metody. Zamiast tego przypisuje wartość do wartości zwracane odwołanie zwracany przez metodę.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a>Za pomocą innej metody pomocnika

W innych przypadkach modyfikując wartość zwracaną odwołanie do wywołania metody bezpośrednio może nie zawsze jest pożądane. Na przykład metoda wyszukiwania, które zwraca ciąg może nie zawsze znaleźć dopasowania. W takim przypadku chcesz zmodyfikować zwracanej wartości odniesienia, tylko w przypadku, jeśli wyszukiwanie zakończy się pomyślnie.

Następujące C# przykład ilustruje ten scenariusz. Definiuje on `Sentence` klasy w C# obejmuje `FindNext` metodę, która umożliwia znalezienie następnego wyrazu w zdaniu, zaczynającą się podanym podciągiem. Ten ciąg jest zwracany jako wartość zwracana przez odwołanie, a `Boolean` zmiennej przekazywany przez odwołanie do metody wskazuje, czy wyszukiwanie zakończyło się pomyślnie. Dokumentacja zwracana wartość wskazuje, czy wywołujący można nie tylko do odczytu zwrócona wartość; on również zmodyfikować go, a tej zmiany jest widoczny w danych znajdujących się wewnętrznie w `Sentence` klasy.

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

Bezpośrednie modyfikowanie odwołanie zwracana wartość w tym przypadku nie są wiarygodne, ponieważ wywołania metody które może się nie powieść znaleźć dopasowania i powrócić pierwszy wyraz w zdaniu. W takim przypadku obiekt wywołujący przypadkowo zmodyfikuje pierwszy wyraz zdania. Można to zapobiegać przez obiekt wywołujący, zwracając `null` (lub `Nothing` w języku Visual Basic). Ale w takim przypadku próby zmodyfikowania ciągu, którego wartością jest `Nothing` zgłasza <xref:System.NullReferenceException>. Jeśli również można zapobiegać przez obiekt wywołujący, zwracając <xref:System.String.Empty?displayProperty=nameWithType>, ale wymaga to, że obiekt wywołujący definiowania zmiennej ciągu, którego wartością jest <xref:System.String.Empty?displayProperty=nameWithType>. Gdy obiekt wywołujący może zmodyfikować te parametry, modyfikacji, sama służy nie, ponieważ modyfikacji ciągu nie ma relacji wyrazy w zdaniu przechowywane przez `Sentence` klasy.

Najlepszym sposobem obsługi tego scenariusza jest przekazać odwołanie wartość zwracaną przez odwołanie do metody pomocnika. Metoda pomocnika zawiera następnie logika do określenia, czy wywołanie metody powiodło się, a jeśli go tak, aby zmodyfikować odwołania zwracają wartość. W poniższym przykładzie przedstawiono potencjalne zastosowanie.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a>Zobacz także

- [Przekazywanie argumentów według wartości i według odwołania](passing-arguments-by-value-and-by-reference.md)
- [Procedury w Visual Basic](index.md)
