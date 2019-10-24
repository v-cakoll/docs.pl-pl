---
title: Wnioskowanie o typie lokalnym (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- local type inference
- vb.TypeInfer
helpviewer_keywords:
- Option Infer statement [Visual Basic]
- local type inference [Visual Basic]
- implicitly-typed local variables [Visual Basic]
- variables [Visual Basic], type inference
- inference [Visual Basic]
- type inference [Visual Basic]
ms.assetid: b8307f18-2e56-4ab3-a45a-826873f400f6
ms.openlocfilehash: 2b239e17ba7fa0b6a6b08d52f4394541eaa08b28
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775724"
---
# <a name="local-type-inference-visual-basic"></a>Wnioskowanie o typie lokalnym (Visual Basic)

Kompilator Visual Basic używa *wnioskowania typu* w celu określenia typów danych zmiennych lokalnych zadeklarowanych bez klauzuli `As`. Kompilator wnioskuje typ zmiennej z typu wyrażenia inicjowania. Dzięki temu można zadeklarować zmienne bez jawnego stwierdzenia typu, jak pokazano w poniższym przykładzie. W wyniku deklaracji zarówno `num1`, jak i `num2` są silnie wpisane jako liczby całkowite.

[!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]

> [!NOTE]
> Jeśli nie chcesz, aby `num2` w poprzednim przykładzie zostały wpisane jako `Integer`, możesz określić inny typ za pomocą deklaracji, takiej jak `Dim num3 As Object = 3` lub `Dim num4 As Double = 3`.

> [!NOTE]
> Wnioskowanie o typie może być używane tylko w przypadku niestatycznych zmiennych lokalnych; nie można jej użyć do określenia typu pól klasy, właściwości lub funkcji.

Wnioskowanie o typie lokalnym jest stosowane na poziomie procedury. Nie można jej użyć do deklarowania zmiennych na poziomie modułu (w obrębie klasy, struktury, modułu lub interfejsu, ale nie wewnątrz procedury lub bloku). Jeśli `num2` w poprzednim przykładzie było polem klasy, a nie zmienną lokalną w procedurze, deklaracja spowodowałaby błąd z `Option Strict` on i klasyfikuje `num2` jako `Object` z `Option Strict` off. Podobnie wnioskowanie o typie lokalnym nie ma zastosowania do zmiennych poziomu procedury zadeklarowanych jako `Static`.

## <a name="type-inference-vs-late-binding"></a>Wnioskowanie o typie a późne wiązanie

Kod używający wnioskowania o typie przypomina kod, który opiera się na późnym powiązaniu. Jednak typ wnioskowania o silnej liczbie typów zmiennej zamiast opuszczania jej jako `Object`. Kompilator używa inicjatora zmiennej do określenia typu zmiennej w czasie kompilacji w celu utworzenia kodu z wczesnym wiązaniem. W poprzednim przykładzie `num2`, jak `num1`, jest wpisana jako `Integer`.

Zachowanie zmiennych wczesnych powiązań różni się od wartości zmiennych z późnym wiązaniem, dla których typ jest znany tylko w czasie wykonywania. Poznanie typu wczesnego pozwala kompilatorowi identyfikować problemy przed wykonaniem, przydzielać pamięć dokładnie i wykonywać inne optymalizacje. Wczesne wiązanie umożliwia również Visual Basic zintegrowanego środowiska programistycznego (IDE), aby zapewnić pomoc IntelliSense na temat elementów członkowskich obiektu. Wczesne wiązanie jest również preferowane dla wydajności. Wynika to z faktu, że wszystkie dane przechowywane w zmiennej późnej powiązania muszą być opakowane jako typ `Object` i dostęp do elementów członkowskich typu w czasie wykonywania sprawia, że program jest wolniejszy.

## <a name="examples"></a>Przykłady

Wnioskowanie o typie występuje, gdy zmienna lokalna jest zadeklarowana bez klauzuli `As` i została zainicjowana. Kompilator używa typu przypisanej wartości początkowej jako typu zmiennej. Na przykład każdy z poniższych wierszy kodu deklaruje zmienną typu `String`.

[!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]

Poniższy kod ilustruje dwa równoważne sposoby tworzenia tablicy liczb całkowitych.

[!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]

Użycie wnioskowania typu w celu określenia typu zmiennej kontrolnej pętli. W poniższym kodzie kompilator wnioskuje, że `number` jest `Integer`, ponieważ `someNumbers2` z poprzedniego przykładu jest tablicą liczb całkowitych.

[!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]

Wnioskowanie o typie lokalnym może być używane w instrukcjach `Using` do ustalenia typu nazwy zasobu, jak pokazano w poniższym przykładzie.

[!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]

Typ zmiennej może być również wywnioskowany na podstawie zwracanych wartości funkcji, jak pokazano w poniższym przykładzie. Zarówno `pList1`, jak i `pList2` są tablicami procesów, ponieważ `Process.GetProcesses` zwraca tablicę procesów.

[!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]

## <a name="option-infer"></a>Wnioskowanie dotyczące opcji

`Option Infer` umożliwia określenie, czy w określonym pliku jest dozwolone wnioskowanie o typie lokalnym. Aby włączyć lub zablokować opcję, wpisz jedną z poniższych instrukcji na początku pliku.

`Option Infer On`

`Option Infer Off`

Jeśli nie określisz wartości dla `Option Infer` w kodzie, domyślnym kompilatorem jest `Option Infer On`.

Jeśli wartość ustawiona dla `Option Infer` w pliku powoduje konflikt z wartością ustawioną w środowisku IDE lub w wierszu polecenia, wartość w pliku ma pierwszeństwo.

Aby uzyskać więcej informacji, zobacz temat [opcja wnioskowanie](../../../../visual-basic/language-reference/statements/option-infer-statement.md) i [Strona kompilacja, projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).

## <a name="see-also"></a>Zobacz także

- [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Wczesne i późne powiązania](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [For Each...Next, instrukcja](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [For...Next, instrukcja](../../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Option Infer, instrukcja](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [-optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
