---
title: 'Porady: dopasowywanie ciągu do wzorca'
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
ms.openlocfilehash: 49328a72c2cff78b8fe13ca73209d224495ad7a1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343641"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a>Porady: dopasowywanie ciągu do wzorca (Visual Basic)

Jeśli chcesz dowiedzieć się, czy wyrażenie [typu danych ciąg](../../../../visual-basic/language-reference/data-types/string-data-type.md) spełnia warunki wzorca, możesz użyć [operatora like](../../../../visual-basic/language-reference/operators/like-operator.md).

`Like` pobiera dwa operandy. Lewy operand jest wyrażeniem ciągu, a prawy operand jest ciągiem zawierającym wzorzec, który ma być używany do dopasowywania. `Like` zwraca `Boolean` wartość wskazującą, czy wyrażenie ciągu spełnia warunki wzorca.

Można dopasować każdy znak w wyrażeniu ciągu do określonego znaku, symbolu wieloznacznego, listy znaków lub zakresu znaków. Pozycje specyfikacji w ciągu wzorca odpowiadają pozycjom znaków, które mają być dopasowane w wyrażeniu ciągu.

## <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a>Aby dopasować znak w wyrażeniu ciągu do określonego znaku

Umieść określony znak bezpośrednio w ciągu wzorca. Niektóre znaki specjalne muszą być ujęte w nawiasy kwadratowe (`[ ]`). Aby uzyskać więcej informacji, zobacz [operator like](../../../../visual-basic/language-reference/operators/like-operator.md).

Poniższy przykład sprawdza, czy `myString` składa się dokładnie z pojedynczego znaku `H`.

[!code-vb[VbVbalrOperators#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#70)]

## <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a>Aby dopasować znak w wyrażeniu ciągu do symbolu wieloznacznego

Wstaw znak zapytania (`?`) w ciągu wzorca. Każdy prawidłowy znak w tym miejscu powoduje pomyślne dopasowanie.

Poniższy przykład sprawdza, czy `myString` składa się z pojedynczego znaku `W` po którym następuje dokładnie dwa znaki wszelkich wartości.

[!code-vb[VbVbalrOperators#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#71)]

## <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a>Aby dopasować znak w wyrażeniu ciągu do listy znaków

Umieść nawiasy (`[ ]`) w ciągu wzorca i wewnątrz nawiasów, umieszczając listę znaków. Nie oddzielaj znaków przecinkami ani innymi separatorami. Każdy pojedynczy znak na liście powoduje pomyślne dopasowanie.

Poniższy przykład sprawdza, czy `myString` składa się z dowolnego prawidłowego znaku, po którym następuje dokładnie jeden ze znaków `A`, `C`lub `E`.

[!code-vb[VbVbalrOperators#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#72)]

Należy pamiętać, że ten odpowiednik uwzględnia wielkość liter.

## <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a>Aby dopasować znak w wyrażeniu ciągu do zakresu znaków

Umieść nawiasy (`[ ]`) w ciągu wzorca i wewnątrz nawiasów Umieść najniższy i najwyższe znaki z zakresu, oddzielone łącznikiem (`–`). Każdy pojedynczy znak w zakresie powoduje pomyślne dopasowanie.

Poniższy przykład sprawdza, czy `myString` składa się ze znaków `num`, po których następuje dokładnie jeden ze znaków, `i`, `j`, `k`, `l`, `m`lub `n`.

[!code-vb[VbVbalrOperators#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#73)]

Należy pamiętać, że ten odpowiednik uwzględnia wielkość liter.

## <a name="matching-empty-strings"></a>Dopasowywanie pustych ciągów

`Like` traktuje `[]` sekwencji jako ciąg o zerowej długości (`""`). Za pomocą `[]` można sprawdzić, czy całe wyrażenie ciągu jest puste, ale nie można go użyć do przetestowania, jeśli określona pozycja w wyrażeniu ciągu jest pusta. Jeśli puste położenie jest jedną z opcji, które należy wykonać w celu przetestowania, można użyć `Like` więcej niż jeden raz.

### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a>Aby dopasować znak w wyrażeniu ciągu do listy znaków lub bez znaku

1. Wywołaj operator `Like` dwa razy w tym samym wyrażeniu ciągu i połącz dwa wywołania z [operatorem OR](../../../../visual-basic/language-reference/operators/or-operator.md) lub [operatorem OrElse](../../../../visual-basic/language-reference/operators/orelse-operator.md).

2. W ciągu wzorca dla pierwszej klauzuli `Like` Dołącz listę znaków ujętą w nawiasy kwadratowe (`[ ]`).

3. W ciągu wzorca dla drugiej klauzuli `Like` nie umieszczaj żadnego znaku w podanym położeniu.

    Poniższy przykład sprawdza numer telefonu siedmiu cyfr `phoneNum` dla dokładnie trzech cyfr, po którym następuje spacja, łącznik (`–`), kropka (`.`) lub bez znaku, a następnie dokładnie cztery cyfry.

    [!code-vb[VbVbalrOperators#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#74)]

## <a name="see-also"></a>Zobacz także

- [Operatory porównania](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Operatory i wyrażenia](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Like, operator](../../../../visual-basic/language-reference/operators/like-operator.md)
- [String, typ danych](../../../../visual-basic/language-reference/data-types/string-data-type.md)
