---
title: Przeciążone właściwości i metody
ms.date: 07/20/2015
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], multiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
ms.openlocfilehash: a5017d371f8a01436020443b2e3466c78fc35d21
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346086"
---
# <a name="overloaded-properties-and-methods-visual-basic"></a>Przeciążone właściwości i metody (Visual Basic)

Przeciążenie jest tworzeniem więcej niż jednej procedury, konstruktora wystąpienia lub właściwości w klasie o tej samej nazwie, ale różnych typach argumentów.

## <a name="overloading-usage"></a>Przeciążenie użycia

Przeciążenie jest szczególnie przydatne, gdy model obiektów wskazuje, że są stosowane identyczne nazwy dla procedur, które działają na różnych typach danych. Na przykład Klasa, która może wyświetlać kilka różnych typów danych, może mieć `Display` procedury, które wyglądają następująco:

[!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]

Bez przeciążania należy utworzyć odrębne nazwy dla każdej procedury, nawet jeśli są one takie same, jak pokazano poniżej:

[!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]

Przeciążanie ułatwia korzystanie z właściwości lub metod, ponieważ umożliwia wybór typów danych, które mogą być używane. Na przykład przeciążona metoda `Display` opisana wcześniej może być wywoływana z dowolnym z następujących wierszy kodu:

[!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]

W czasie wykonywania Visual Basic wywołuje poprawną procedurę na podstawie typów danych parametrów, które określisz.

## <a name="overloading-rules"></a>Reguły przeciążania

 Tworzysz przeciążoną składową klasy przez dodanie dwóch lub więcej właściwości lub metod o tej samej nazwie. Z wyjątkiem przeciążonych członków pochodnych każdy przeciążony element członkowski musi mieć różne listy parametrów, a następujące elementy nie mogą być używane jako funkcja odróżniająca podczas przeciążania właściwości lub procedury:

- Modyfikatory, takie jak `ByVal` lub `ByRef`, które mają zastosowanie do elementu członkowskiego lub parametrów elementu członkowskiego.

- Nazwy parametrów

- Zwracane typy procedur

Słowo kluczowe `Overloads` jest opcjonalne podczas przeciążania, ale jeśli jakikolwiek przeciążony element członkowski używa słowa kluczowego `Overloads`, wówczas wszystkie inne przeciążone elementy członkowskie o tej samej nazwie muszą również określać to słowo kluczowe.

Klasy pochodne mogą przeciążać dziedziczone elementy członkowskie z elementami członkowskimi, które mają identyczne parametry i typy parametrów, proces znany jako *przesłanianie przez nazwę i podpis*. Jeśli `Overloads` słowo kluczowe jest używane podczas przesłaniania według nazwy i podpisu, implementacja klasy pochodnej elementu członkowskiego zostanie użyta zamiast implementacji w klasie bazowej, a wszystkie pozostałe przeciążenia dla tego elementu członkowskiego będą dostępne dla wystąpień klasy pochodnej.

Jeśli słowo kluczowe `Overloads` zostanie pominięte podczas przeciążenia dziedziczonego elementu członkowskiego, który ma identyczne parametry i typy parametrów, Przeciążenie jest nazywane *przesłanianiem o nazwie*. Przesłanianie według nazwy zastępuje dziedziczone implementacje elementu członkowskiego i powoduje, że wszystkie pozostałe przeciążenia są niedostępne dla wystąpień klasy pochodnej i jej decedents.

Modyfikatory `Overloads` i `Shadows` nie mogą być używane z tą samą właściwością lub metodą.

### <a name="example"></a>Przykład

Poniższy przykład tworzy przeciążone metody, które akceptują `String` lub `Decimal` reprezentację kwoty dolara i zwracają ciąg zawierający podatek sprzedaży.

#### <a name="to-use-this-example-to-create-an-overloaded-method"></a>Aby użyć tego przykładu do utworzenia przeciążonej metody

1. Otwórz nowy projekt i Dodaj klasę o nazwie `TaxClass`.

2. Dodaj następujący kod do klasy `TaxClass`.

    [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]

3. Dodaj następującą procedurę do formularza.

    [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]

4. Dodaj przycisk do formularza i Wywołaj procedurę `ShowTax` ze zdarzenia `Button1_Click` przycisku.

5. Uruchom projekt i kliknij przycisk w formularzu, aby przetestować przeciążoną procedurę `ShowTax`.

W czasie wykonywania kompilator wybiera odpowiednią przeciążoną funkcję zgodną z używanymi parametrami. Po kliknięciu przycisku przeciążona metoda jest wywoływana jako pierwsza z parametrem `Price`, który jest ciągiem i komunikatem "Price jest ciągiem. Zostanie wyświetlony podatek $5,12. `TaxAmount` jest wywoływana z wartością `Decimal` po raz drugi i komunikatem "cena jest liczbą dziesiętną. Zostanie wyświetlony podatek $5,12.

## <a name="see-also"></a>Zobacz także

- [Obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Obserwowanie w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Sub, instrukcja](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Podstawowe informacje o dziedziczeniu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)
- [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
