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
ms.openlocfilehash: b33b8b2d17c240e380377528d4f5d2f511381a7d
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37959955"
---
# <a name="local-type-inference-visual-basic"></a>Wnioskowanie o typie lokalnym (Visual Basic)
Kompilator języka Visual Basic używa *wnioskowanie o typie* Aby określić typy danych zmiennych lokalnych zadeklarowana bez `As` klauzuli. Kompilator wnioskuje typ zmiennej z typu wyrażenia inicjowania. Dzięki temu można deklarować zmienne bez jawne określenie typu, jak pokazano w poniższym przykładzie. W wyniku deklaracji zarówno `num1` i `num2` są silnie typizowane jako liczby całkowite.  
  
 [!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_1.vb)]  
 
> [!NOTE]
>  Jeśli nie chcesz `num2` w poprzednim przykładzie, aby wpisać jako `Integer`, można określić inny typ za pomocą deklaracji, takich jak `Dim num3 As Object = 3` lub `Dim num4 As Double = 3`.  

> [!NOTE]
>  Wnioskowanie o typie mogą służyć tylko dla zmiennych lokalnych niestatycznych; Nie można określić typu klasy, pola, właściwości lub funkcji.
 
 Wnioskowanie o typie lokalnym ma zastosowanie na poziomie procedury. Nie można zadeklarować zmienne na poziomie modułu (w obrębie klasy, struktury, modułu lub interfejsu ale nie w obrębie procedurę lub blok). Jeśli `num2` w poprzednim przykładzie był to pole klasy zamiast zmiennej lokalnej w procedurze, deklaracja spowodowałoby błąd `Option Strict` i czy sklasyfikować `num2` jako `Object` z `Option Strict` wyłączone. Podobnie, wnioskowanie o typie lokalnym nie ma zastosowania do procedury zmienne poziomu zadeklarowane jako `Static`.  
  
## <a name="type-inference-vs-late-binding"></a>Wpisz vs wnioskowania. Późne powiązania  
 Kod używa wnioskowanie o typie jest podobny do kodu, która korzysta z późnym wiązaniem. Jednak wnioskowanie o typie silnie typy zmiennych, zamiast zostawiać je jako `Object`. Kompilator używa inicjator zmiennej do określenia typu w czasie kompilacji, aby wygenerować kod z wczesnym wiązaniem. W poprzednim przykładzie `num2`, takiej jak `num1`, jest `Integer`.  
  
 Zachowanie zmiennych wczesnym wiązaniem różni się od zmiennych z późnym wiązaniem, dla których typ jest znana dopiero w czasie wykonywania. Wcześnie, wiedząc typu umożliwia kompilatorowi zidentyfikować problemy przed wykonaniem, dokładnie przydzielić pamięci i wykonywać inne optymalizacje. Wczesne powiązania umożliwia także języka Visual Basic zintegrowanego środowiska programistycznego (IDE), aby zapewnić pomoc IntelliSense dotyczących elementów członkowskich obiektu. Wczesne powiązania jest również preferowana dla wydajności. Jest to spowodowane wszystkie dane przechowywane w zmiennej z późnym wiązaniem muszą być zapakowane jako typ `Object`, i uzyskiwanie dostępu do elementów członkowskich typu w czasie wykonywania sprawia, że program wolniej.  
  
## <a name="examples"></a>Przykłady  
 Wnioskowanie o typie występuje, gdy zmienna lokalna jest zadeklarowana bez `As` klauzuli i zainicjowane. Kompilator używa typ przypisaną wartością początkową jako typ zmiennej. Na przykład, każda następujące wiersze kodu deklaruje zmienną typu `String`.  
  
 [!code-vb[VbVbalrTypeInference#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_2.vb)]  
  
 Poniższy kod przedstawia dwa sposoby równoważne do utworzenia tablicy liczb całkowitych.  
  
 [!code-vb[VbVbalrTypeInference#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_3.vb)]  
  
 Jest łatwa w użyciu wnioskowanie o typie, aby określić typ zmienna sterująca pętli. W poniższym kodzie, kompilator wnioskuje, że `number` jest `Integer` ponieważ `someNumbers2` z poprzedniego przykładu jest tablicy liczb całkowitych.  
  
 [!code-vb[VbVbalrTypeInference#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_4.vb)]  
  
 Wnioskowanie o typie lokalnym mogą być używane w `Using` instrukcje, aby ustanowić wpisz nazwę zasobu, tak jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrTypeInference#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_5.vb)]  
  
 Również można wywnioskować typu zmiennej na podstawie wartości zwracane funkcji, tak jak pokazano w poniższym przykładzie. Zarówno `pList1` i `pList2` są tablicami procesów, ponieważ `Process.GetProcesses` zwraca tablicę procesów.  
  
 [!code-vb[VbVbalrTypeInference#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_6.vb)]  
  
## <a name="option-infer"></a>Option Infer  
 `Option Infer` Umożliwia określenie, czy wnioskowanie o typie lokalnym jest dozwolone w określonym pliku. Aby włączyć lub Blokuj opcję, należy wpisać jedną z następujących instrukcji na początku pliku.  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 Jeśli nie określisz wartości `Option Infer` w kodzie jest domyślna wartość kompilatora `Option Infer On`. Dla projektów uaktualniony z [!INCLUDE[vb_orcas_long](~/includes/vb-orcas-long-md.md)] lub wcześniej, domyślna wartość kompilatora `Option Infer Off`.  
  
 Jeśli ustawiono wartość `Option Infer` w pliku powoduje konflikt z wartości ustawionej w IDE lub w wierszu polecenia, wartość w pliku ma pierwszeństwo.  
  
 Aby uzyskać więcej informacji, zobacz [Option Infer — instrukcja](../../../../visual-basic/language-reference/statements/option-infer-statement.md) i [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
## <a name="see-also"></a>Zobacz też  
 [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Wczesne i późne powiązania](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [For Each...Next, instrukcja](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [For...Next, instrukcja](../../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Option Infer, instrukcja](../../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [/optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
