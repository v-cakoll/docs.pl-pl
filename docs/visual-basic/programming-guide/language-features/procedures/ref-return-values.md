---
title: Wartości zwrotu ref
ms.date: 04/28/2017
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
ms.openlocfilehash: f2a92c584dbb12a322e28435d797fa4d7c2f6dbb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186935"
---
# <a name="support-for-reference-return-values-visual-basic"></a>Obsługa referencyjnych wartości zwracania (Visual Basic)

Począwszy od języka C# 7.0, język C# obsługuje *odwołania zwracane wartości*. Jednym ze sposobów zrozumienia wartości zwracanych odwołania jest to, że są one przeciwieństwem argumentów, które są przekazywane przez odwołanie do metody. Gdy argument przekazywany przez odwołanie jest modyfikowany, zmiany są odzwierciedlane w wartości zmiennej na wywołującym. Gdy metoda zapewnia wartość zwracaną odwołania do wywołującego, modyfikacje wprowadzone do odwołania wartości zwracanej przez wywołującego są odzwierciedlane w danych metody wywoływanej.

Visual Basic nie pozwala na tworzenie metod z odwołania zwracane wartości, ale pozwala na korzystanie z wartości zwracane odwołania. Innymi słowy można wywołać metodę z referencyjną wartością zwracaną i zmodyfikować tę wartość zwracaną, a zmiany wartości zwracanej odwołania są odzwierciedlane w danych wywoływanej metody.

## <a name="modifying-the-ref-return-value-directly"></a>Bezpośrednie modyfikowanie wartości zwracanej ref

Dla metod, które zawsze `ByRef` powiedzie się i nie mają parametrów, można bezpośrednio zmodyfikować wartość zwracaną odwołania. Można to zrobić, przypisując nową wartość do wyrażeń zwracających referencyjną wartość zwracaną.

Poniższy przykład języka C# definiuje `NumericValue.IncrementValue` metodę, która zwiększa wartość wewnętrzną i zwraca ją jako wartość zwracaną odwołania.

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

Odwołanie wartość zwracana jest następnie modyfikowany przez obiekt wywołujący w poniższym przykładzie języka Visual Basic. Należy zauważyć, że `NumericValue.IncrementValue` wiersz z wywołaniem metody nie przypisuje wartość do metody. Zamiast tego przypisuje wartość do referencyjnej wartości zwracanej przez metodę.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a>Korzystanie z metody pomocnika

W innych przypadkach modyfikowanie referencyjnej wartości zwracanej wywołania metody bezpośrednio może nie zawsze być pożądane. Na przykład metoda wyszukiwania, która zwraca ciąg nie zawsze może znaleźć dopasowanie. W takim przypadku chcesz zmodyfikować wartość zwracaną odwołania tylko wtedy, gdy wyszukiwanie zakończy się pomyślnie.

Poniższy przykład języka C# ilustruje ten scenariusz. Definiuje klasę `Sentence` napisaną w języku `FindNext` C# zawiera metodę, która znajduje następny wyraz w zdaniu, który zaczyna się od określonego podciągu. Ciąg jest zwracany jako odwołanie wartości `Boolean` zwracanej, a zmienna przekazywana przez odwołanie do metody wskazuje, czy wyszukiwanie zakończyło się pomyślnie. Odwołanie wartość zwracana wskazuje, że oprócz odczytu zwracanej wartości, wywołujący można również zmodyfikować go i tej `Sentence` modyfikacji jest odzwierciedlone w danych zawartych wewnętrznie w klasie.

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

Bezpośrednie modyfikowanie odwołania wartości zwracanej w tym przypadku nie jest wiarygodne, ponieważ wywołanie metody może nie znaleźć dopasowania i zwrócić pierwszy wyraz w zdaniu. W takim przypadku obiekt wywołujący przypadkowo zmodyfikuje pierwsze słowo zdania. Może to być zapobieżenie `null` przez `Nothing` wywołującego zwraca (lub w języku Visual Basic). Ale w takim przypadku próba zmodyfikowania ciągu, którego wartością jest `Nothing` throws a <xref:System.NullReferenceException>. Jeśli można również zapobiec przez wywołującego <xref:System.String.Empty?displayProperty=nameWithType>zwraca, ale wymaga to, aby wywołujący <xref:System.String.Empty?displayProperty=nameWithType>zdefiniować zmienną ciągu, której wartość jest . Podczas gdy wywołujący można zmodyfikować tego ciągu, sama modyfikacja służy bezcelu, ponieważ zmodyfikowany `Sentence` ciąg nie ma związku ze słowami w zdaniu przechowywanych przez klasę.

Najlepszym sposobem obsługi tego scenariusza jest przekazanie odwołania wartości zwracanej przez odwołanie do metody pomocnika. Metoda pomocnika następnie zawiera logikę, aby ustalić, czy wywołanie metody powiodło się, a jeśli tak, aby zmodyfikować wartość zwracaną odwołania. Poniższy przykład zawiera możliwe implementacji.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a>Zobacz też

- [Przekazywanie argumentów według wartości i odwołań](passing-arguments-by-value-and-by-reference.md)
- [Procedury w Visual Basic](index.md)
