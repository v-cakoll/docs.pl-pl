---
title: 'Instrukcje: Dopasowuje ciąg do wzorca (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- pattern matching
- strings [Visual Basic], comparing
- string comparison [Visual Basic], operators
- Visual Basic code, operators
- pattern matching [Visual Basic], string comparison
- string comparison [Visual Basic]
- Like operator [Visual Basic], pattern matching
- pattern matching, empty strings
- operators [Visual Basic], comparison
ms.assetid: 19a83804-b5af-4739-928b-ac93e64e457f
ms.openlocfilehash: 0bac0869d9e319071abb31dd0576edf0450aa198
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054153"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a>Instrukcje: Dopasowuje ciąg do wzorca (Visual Basic)

Jeśli chcesz dowiedzieć się, czy wyrażenie [typu danych ciąg](../../../../visual-basic/language-reference/data-types/string-data-type.md) spełnia warunki wzorca, możesz użyć [operatora like](../../../../visual-basic/language-reference/operators/like-operator.md).

`Like`przyjmuje dwa operandy. Lewy operand jest wyrażeniem ciągu, a prawy operand jest ciągiem zawierającym wzorzec, który ma być używany do dopasowywania. `Like``Boolean` zwraca wartość wskazującą czy wyrażenie ciągu spełnia warunki wzorca.

Można dopasować każdy znak w wyrażeniu ciągu do określonego znaku, symbolu wieloznacznego, listy znaków lub zakresu znaków. Pozycje specyfikacji w ciągu wzorca odpowiadają pozycjom znaków, które mają być dopasowane w wyrażeniu ciągu.

## <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a>Aby dopasować znak w wyrażeniu ciągu do określonego znaku

Umieść określony znak bezpośrednio w ciągu wzorca. Niektóre znaki specjalne muszą być ujęte w nawiasy kwadratowe (`[ ]`). Aby uzyskać więcej informacji, zobacz [operator like](../../../../visual-basic/language-reference/operators/like-operator.md).

Poniższy przykład sprawdza, czy `myString` zawiera dokładnie jeden znak. `H`

[!code-vb[VbVbalrOperators#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#70)]

## <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a>Aby dopasować znak w wyrażeniu ciągu do symbolu wieloznacznego

Umieść znak zapytania (`?`) w ciągu wzorca. Każdy prawidłowy znak w tym miejscu powoduje pomyślne dopasowanie.

Poniższy przykład sprawdza, czy `myString` składa się z pojedynczego `W` znaku, po którym następuje dokładnie dwa znaki każdej wartości.

[!code-vb[VbVbalrOperators#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#71)]

## <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a>Aby dopasować znak w wyrażeniu ciągu do listy znaków

Umieść nawiasy`[ ]`() w ciągu wzorca i wewnątrz nawiasów, umieszczając listę znaków. Nie oddzielaj znaków przecinkami ani innymi separatorami. Każdy pojedynczy znak na liście powoduje pomyślne dopasowanie.

Poniższy przykład sprawdza, czy `myString` składa się z dowolnego prawidłowego znaku, po którym występuje dokładnie `A`jeden `C`z znaków `E`, lub.

[!code-vb[VbVbalrOperators#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#72)]

Należy pamiętać, że ten odpowiednik uwzględnia wielkość liter.

## <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a>Aby dopasować znak w wyrażeniu ciągu do zakresu znaków

Umieść nawiasy`[ ]`() w ciągu wzorca, a wewnątrz nawiasów Umieść najniższy i najwyższe znaki z zakresu, oddzielone łącznikiem (`–`). Każdy pojedynczy znak w zakresie powoduje pomyślne dopasowanie.

Poniższy przykład sprawdza, czy `myString` zawiera znaki `num` , po których następuje dokładnie jeden `k`z `m`znaków `i`, `j`,, `l`, lub `n`.

[!code-vb[VbVbalrOperators#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#73)]

Należy pamiętać, że ten odpowiednik uwzględnia wielkość liter.

## <a name="matching-empty-strings"></a>Dopasowywanie pustych ciągów

`Like`traktuje sekwencję `[]` jako ciąg o zerowej długości`""`(). Można użyć `[]` do sprawdzenia, czy całe wyrażenie ciągu jest puste, ale nie można go użyć do przetestowania, jeśli określone położenie w wyrażeniu ciągu jest puste. Jeśli puste położenie jest jedną z opcji, które należy wykonać w celu przetestowania, można `Like` użyć więcej niż raz.

### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a>Aby dopasować znak w wyrażeniu ciągu do listy znaków lub bez znaku

1. Wywołaj [](../../../../visual-basic/language-reference/operators/or-operator.md) operatora dwa razy w tym samym wyrażeniu ciągu i połącz dwa wywołania z operatorem OR lub [operatorem OrElse.](../../../../visual-basic/language-reference/operators/orelse-operator.md) `Like`

2. W ciągu wzorca dla pierwszej `Like` klauzuli należy uwzględnić listę znaków ujętą w nawiasy kwadratowe (`[ ]`).

3. W ciągu wzorca dla drugiej `Like` klauzuli nie umieszczaj żadnego znaku w podanym położeniu.

    Poniższy przykład sprawdza numer `phoneNum` telefonu siedmiu cyfr dla dokładnie trzech cyfr, po którym następuje spacja, łącznik (`–`), kropka (`.`) lub bez znaku, a następnie dokładnie cztery cyfry.

    [!code-vb[VbVbalrOperators#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#74)]

## <a name="see-also"></a>Zobacz także

- [Operatory porównania](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Operatory i wyrażenia](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Like, operator](../../../../visual-basic/language-reference/operators/like-operator.md)
- [String, typ danych](../../../../visual-basic/language-reference/data-types/string-data-type.md)
