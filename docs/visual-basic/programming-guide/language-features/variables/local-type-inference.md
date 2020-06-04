---
title: Wnioskowanie o typie lokalnym
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
ms.openlocfilehash: 3979396d32aa5d3b853aa087d43f70d5987e510b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410402"
---
# <a name="local-type-inference-visual-basic"></a>Wnioskowanie o typie lokalnym (Visual Basic)

Kompilator Visual Basic używa *wnioskowania o typie* , aby określić typy danych zmiennych lokalnych zadeklarowanych bez `As` klauzuli. Kompilator wnioskuje typ zmiennej z typu wyrażenia inicjowania. Dzięki temu można zadeklarować zmienne bez jawnego stwierdzenia typu, jak pokazano w poniższym przykładzie. W wyniku deklaracji zarówno `num1` i `num2` są jednoznacznie wpisane jako liczby całkowite.

[!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]

> [!NOTE]
> Jeśli nie chcesz `num2` , aby w poprzednim przykładzie był wpisywany jako `Integer` , możesz określić inny typ przy użyciu deklaracji takiej jak `Dim num3 As Object = 3` lub `Dim num4 As Double = 3` .

> [!NOTE]
> Wnioskowanie o typie może być używane tylko w przypadku niestatycznych zmiennych lokalnych; nie można jej użyć do określenia typu pól klasy, właściwości lub funkcji.

Wnioskowanie o typie lokalnym jest stosowane na poziomie procedury. Nie można jej użyć do deklarowania zmiennych na poziomie modułu (w obrębie klasy, struktury, modułu lub interfejsu, ale nie wewnątrz procedury lub bloku). Jeśli `num2` w poprzednim przykładzie było to pole klasy, a nie zmienna lokalna w procedurze, deklaracja spowodowałaby wystąpienie błędu z `Option Strict` włączonym i zostałaby sklasyfikowana `num2` jako `Object` with `Option Strict` off. Podobnie wnioskowanie o typie lokalnym nie ma zastosowania do zmiennych poziomu procedury zadeklarowanych jako `Static` .

## <a name="type-inference-vs-late-binding"></a>Wnioskowanie o typie a późne wiązanie

Kod używający wnioskowania o typie przypomina kod, który opiera się na późnym powiązaniu. Jednak typ wnioskowania o silnej liczbie typów zmienna zamiast opuszczania go jako `Object` . Kompilator używa inicjatora zmiennej do określenia typu zmiennej w czasie kompilacji w celu utworzenia kodu z wczesnym wiązaniem. W poprzednim przykładzie, na przykład `num2` `num1` , jest wpisana jako `Integer` .

Zachowanie zmiennych wczesnych powiązań różni się od wartości zmiennych z późnym wiązaniem, dla których typ jest znany tylko w czasie wykonywania. Poznanie typu wczesnego pozwala kompilatorowi identyfikować problemy przed wykonaniem, przydzielać pamięć dokładnie i wykonywać inne optymalizacje. Wczesne wiązanie umożliwia również Visual Basic zintegrowanego środowiska programistycznego (IDE), aby zapewnić pomoc IntelliSense na temat elementów członkowskich obiektu. Wczesne wiązanie jest również preferowane dla wydajności. Wynika to z faktu, że wszystkie dane przechowywane w zmiennej z późnym wiązaniem muszą być opakowane jako typ `Object` , a dostęp do elementów członkowskich typu w czasie wykonywania sprawia, że program jest wolniejszy.

## <a name="examples"></a>Przykłady

Wnioskowanie o typie występuje, gdy zmienna lokalna jest zadeklarowana bez `As` klauzuli i zainicjowana. Kompilator używa typu przypisanej wartości początkowej jako typu zmiennej. Na przykład każdy z poniższych wierszy kodu deklaruje zmienną typu `String` .

[!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]

Poniższy kod ilustruje dwa równoważne sposoby tworzenia tablicy liczb całkowitych.

[!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]

Użycie wnioskowania typu w celu określenia typu zmiennej kontrolnej pętli. W poniższym kodzie kompilator wnioskuje, że w `number` `Integer` `someNumbers2` poprzednim przykładzie jest tablicą liczb całkowitych.

[!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]

Wnioskowanie o typie lokalnym może być używane w `Using` instrukcjach w celu ustalenia typu nazwy zasobu, jak pokazano w poniższym przykładzie.

[!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]

Typ zmiennej może być również wywnioskowany na podstawie zwracanych wartości funkcji, jak pokazano w poniższym przykładzie. Oba `pList1` i `pList2` są tablicami procesów, ponieważ `Process.GetProcesses` zwraca tablicę procesów.

[!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]

## <a name="option-infer"></a>Wnioskowanie dotyczące opcji

`Option Infer`umożliwia określenie, czy wnioskowanie typu lokalnego jest dozwolone w określonym pliku. Aby włączyć lub zablokować opcję, wpisz jedną z poniższych instrukcji na początku pliku.

`Option Infer On`

`Option Infer Off`

Jeśli nie określisz wartości dla `Option Infer` w kodzie, kompilator domyślnie ma wartość `Option Infer On` .

Jeśli wartość ustawiona dla `Option Infer` w pliku powoduje konflikt z wartością ustawioną w środowisku IDE lub w wierszu polecenia, wartość w pliku ma pierwszeństwo.

Aby uzyskać więcej informacji, zobacz temat [opcja wnioskowanie](../../../language-reference/statements/option-infer-statement.md) i [Strona kompilacja, projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).

## <a name="see-also"></a>Zobacz też

- [Typy anonimowe](../objects-and-classes/anonymous-types.md)
- [Wczesne i późne powiązania](../early-late-binding/index.md)
- [For Each...Next, instrukcja](../../../language-reference/statements/for-each-next-statement.md)
- [For...Next, instrukcja](../../../language-reference/statements/for-next-statement.md)
- [Option Infer — Instrukcja](../../../language-reference/statements/option-infer-statement.md)
- [-optioninfer](../../../reference/command-line-compiler/optioninfer.md)
- [Wprowadzenie do LINQ w Visual Basic](../linq/introduction-to-linq.md)
