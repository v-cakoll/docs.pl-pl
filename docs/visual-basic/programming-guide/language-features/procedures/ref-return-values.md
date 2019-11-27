---
title: Wartości zwracane ref
ms.date: 04/28/2017
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
ms.openlocfilehash: 2d2a302a899fbde549161469f281d3e580bcb71f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352536"
---
# <a name="support-for-reference-return-values-visual-basic"></a>Obsługa wartości zwracanych przez odwołanie (Visual Basic)

Począwszy od C# 7,0, C# język obsługuje *wartości zwracane przez odwołanie*. Jednym ze sposobów zrozumienia zwracanych wartości odwołania jest to, że są one przeciwieństwem argumentów, które są przekazane przez odwołanie do metody. Gdy argument przekazane przez odwołanie jest modyfikowany, zmiany zostaną odzwierciedlone w wartości zmiennej w obiekcie wywołującym. Gdy metoda udostępnia wartość zwracaną odwołanie do obiektu wywołującego, modyfikacje wartości zwracanej odwołania przez wywołującego są odzwierciedlone w danych wywołanej metody.

Visual Basic nie pozwala na tworzenie metod za pomocą zwracanych wartości, ale umożliwia korzystanie z wartości zwracanych przez odwołanie. Innymi słowy, można wywołać metodę z wartością zwracaną przez odwołanie i zmodyfikować tę wartość zwracaną, a zmiany wartości zwracanej odwołania są odzwierciedlone w danych wywołanej metody.

## <a name="modifying-the-ref-return-value-directly"></a>Bezpośrednie modyfikowanie ref zwracanej wartości

Dla metod, które zawsze kończą się powodzeniem i nie mają parametrów `ByRef`, można zmodyfikować wartość zwracaną bezpośrednio odwołania. Można to zrobić, przypisując nową wartość do wyrażeń, które zwracają wartość zwracaną przez odwołanie.

W poniższym C# przykładzie zdefiniowano metodę `NumericValue.IncrementValue`, która zwiększa wartość wewnętrzną i zwraca ją jako wartość zwracaną przez odwołanie.

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

Wartość zwracana odwołania jest następnie modyfikowana przez obiekt wywołujący w poniższym przykładzie Visual Basic. Należy zauważyć, że wiersz z wywołaniem metody `NumericValue.IncrementValue` nie przypisuje wartości do metody. Zamiast tego przypisuje wartość do wartości zwracanej odwołania zwracanej przez metodę.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a>Korzystanie z metody pomocnika

W innych przypadkach modyfikowanie wartości zwracanej przez wywołanie metody bezpośrednio może być niewskazane. Na przykład Metoda wyszukiwania zwracająca ciąg może nie zawsze znaleźć dopasowania. W takim przypadku należy zmodyfikować wartość zwrotną odwołania tylko wtedy, gdy wyszukiwanie zakończyło się pomyślnie.

Poniższy C# przykład ilustruje ten scenariusz. Definiuje klasę `Sentence`, która jest zapisywana w C# systemie, zawiera metodę `FindNext`, która umożliwia znalezienie następnego wyrazu w zdaniu rozpoczynającym się od określonego podciągu. Ciąg jest zwracany jako wartość zwracana przez odwołanie, a zmienna `Boolean` przekazana przez odwołanie do metody wskazuje, czy wyszukiwanie zakończyło się pomyślnie. Zwracana wartość odwołania wskazuje, że obiekt wywołujący nie może odczytać zwracanej wartości; może także ją modyfikować i modyfikacja jest odzwierciedlana w danych zawartych wewnętrznie w klasie `Sentence`.

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

Bezpośrednie modyfikowanie referencyjnej wartości zwracanej w tym przypadku nie jest niezawodne, ponieważ wywołanie metody może nie znaleźć dopasowania i zwrócić pierwsze słowo w zdaniu. W takim przypadku obiekt wywołujący będzie przypadkowo modyfikować pierwszy wyraz zdania. Może to uniemożliwić wywołującemu zwrócenie `null` (lub `Nothing` w Visual Basic). Ale w tym przypadku próbuje zmodyfikować ciąg, którego wartość jest `Nothing` zgłasza <xref:System.NullReferenceException>. Jeśli może być również uniemożliwione przez obiekt wywołujący, zwraca <xref:System.String.Empty?displayProperty=nameWithType>, ale wymaga, aby obiekt wywołujący definiował zmienną ciągu, której wartość jest <xref:System.String.Empty?displayProperty=nameWithType>. Obiekt wywołujący może zmodyfikować ten ciąg, ale modyfikacja nie będzie miało zastosowania, ponieważ zmodyfikowany ciąg nie ma relacji do wyrazów w zdaniu przechowywanym przez klasę `Sentence`.

Najlepszym sposobem obsługi tego scenariusza jest przekazanie wartości zwracanej odwołania przez odwołanie do metody pomocnika. Metoda pomocnika zawiera następnie logikę, aby określić, czy wywołanie metody powiodło się, a jeśli tak, aby zmodyfikować wartość zwracaną przez odwołanie. W poniższym przykładzie przedstawiono możliwe wdrożenie.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a>Zobacz także

- [Przekazywanie argumentów według wartości i według odwołania](passing-arguments-by-value-and-by-reference.md)
- [Procedury w Visual Basic](index.md)
