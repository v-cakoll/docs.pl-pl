---
title: Przeciążone właściwości i metody (Visual Basic)
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
ms.openlocfilehash: 8d7341370d9770d2e57f786ac7c68277e66a9bbd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864874"
---
# <a name="overloaded-properties-and-methods-visual-basic"></a>Przeciążone właściwości i metody (Visual Basic)

Przeciążenie jest tworzenie więcej niż jednej procedury, Konstruktor wystąpienia lub właściwości w klasie o takiej samej nazwie, ale argument różnych typów.

## <a name="overloading-usage"></a>Przeciążanie użycia

Przeciążenie jest szczególnie przydatne w przypadku, gdy model obiektu mówią, że zostanie zastosowana identyczne nazwy dla procedur, które działają na różnych typach danych. Na przykład klasa, która może wyświetlać wiele różnych typów danych może mieć `Display` procedur, które wyglądają następująco:

[!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]

Bez przeciążenia, będziesz potrzebować do tworzenia unikatowych nazw dla każdej procedury, mimo że tak samo, jak pokazano dalej:

[!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]

Przeciążanie sprawia, że łatwiej używać właściwości lub metody, ponieważ zapewnia szeroki wybór typów danych, które mogą być używane. Na przykład zastąpionej `Display` omówionych wcześniej można wywołać metody z dowolnym następujące wiersze kodu:

[!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]

W czasie wykonywania Visual Basic wywołuje procedury poprawny, na podstawie typów danych parametrów, które określisz.

## <a name="overloading-rules"></a>Przeciążanie reguły

 Możesz utworzyć członka przeciążonego, dla klasy, dodając dwa lub więcej właściwości lub metody o tej samej nazwie. Z wyjątkiem przeciążone elementy członkowskie pochodnej każdego członka przeciążonego musi mieć listy różnych parametrów, a następujące elementy nie może pełnić funkcję różnicujący przeciążania właściwość lub procedura:

- Modyfikatory, takich jak `ByVal` lub `ByRef`, które są stosowane do członka lub parametrów elementu członkowskiego.

- Nazwy parametrów

- Zwracane typy procedur

`Overloads` — Słowo kluczowe jest opcjonalny w przypadku przeciążania, ale jeśli przeciążone używa elementu członkowskiego `Overloads` — słowo kluczowe, a następnie wszystkie inne przeciążone elementy członkowskie o takiej samej nazwie należy także określić to słowo kluczowe.

Klasy pochodne może doprowadzić do przeciążenia dziedziczone elementy członkowskie z elementami członkowskimi, które mają identyczne parametry i typy parametrów, proces ten jest znany jako *przesłanianie przez nazwę i podpis*. Jeśli `Overloads` — słowo kluczowe jest używana podczas przesłanianie przez nazwę i podpis, implementacja klasy pochodnej elementu członkowskiego, będą używane zamiast implementacji w klasie bazowej i inne przeciążenia dla tego elementu członkowskiego będą dostępne dla wystąpienia elementu klasy pochodnej.

Jeśli `Overloads` — słowo kluczowe zostanie pominięty w przypadku przeciążania dziedziczonej składowej ze składową, który ma identyczne parametry i typy parametrów, a następnie przeciążenie jest wywoływane *przesłanianie według nazwy*. Przesłanianie według nazwy zastępuje dziedziczona implementacja elementu członkowskiego, a także udostępnia inne przeciążenia niedostępny dla wystąpień klasy pochodnej i jego decedents.

`Overloads` i `Shadows` modyfikatorów nie można używać z tej samej właściwości lub metody.

### <a name="example"></a>Przykład

Poniższy przykład tworzy przeciążone metody, które akceptują albo `String` lub `Decimal` reprezentacja kwoty i zwracany ciąg zawierający podatku od sprzedaży.

#### <a name="to-use-this-example-to-create-an-overloaded-method"></a>Aby wykorzystać ten przykład, aby utworzyć przeciążonej metody

1. Otwórz nowy projekt i Dodaj klasę o nazwie `TaxClass`.

2. Dodaj następujący kod do `TaxClass` klasy.

    [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]

3. Poniższej procedury można dodać do formularza.

    [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]

4. Dodawanie przycisku do formularza i wywołania `ShowTax` procedury z `Button1_Click` zdarzenia przycisku.

5. Uruchom projekt, a następnie kliknij przycisk na formularzu, aby przetestować przeciążone `ShowTax` procedury.

W czasie wykonywania kompilator wybiera odpowiednie przeciążonej funkcji zgodny z parametrami, które są używane. Po kliknięciu przycisku, przeciążona metoda jest wywoływana najpierw z `Price` parametr, który jest ciągiem i komunikat, "cena jest ciąg. Podatek jest $5,12" jest wyświetlana. `TaxAmount` jest wywoływana z `Decimal` wartość po raz drugi i komunikat, "cena to wartości dziesiętnej. Podatek jest $5,12" jest wyświetlana.

## <a name="see-also"></a>Zobacz także

- [Obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Przesłanianie w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Sub, instrukcja](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Podstawowe informacje o dziedziczeniu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)
- [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
