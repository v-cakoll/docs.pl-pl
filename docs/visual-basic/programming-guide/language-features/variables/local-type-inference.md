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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="local-type-inference-visual-basic"></a>Wnioskowanie o typie lokalnym (Visual Basic)
Kompilator Visual Basic używa *wnioskowanie* do określania typów danych zmienna lokalna zadeklarowana bez `As` klauzuli. Kompilator wnioskuje typ zmiennej typu wyrażenia inicjowania. Dzięki temu można zadeklarować zmienne bez jawne określenie typu, jak pokazano w poniższym przykładzie. W wyniku deklaracjami zarówno `num1` i `num2` są silnie typizowane liczbami całkowitymi.  
  
 [!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_1.vb)]  
 
> [!NOTE]
>  Jeśli nie chcesz `num2` w poprzednim przykładzie, aby wpisać jako `Integer`, można określić innego typu za pomocą deklaracji, takich jak `Dim num3 As Object = 3` lub `Dim num4 As Double = 3`.  

> [!NOTE]
>  Wnioskowanie o typie mogą służyć tylko dla zmiennych lokalnych niestatyczna; Nie można określić typu pola klasy, właściwości lub funkcji.
 
 Wnioskowanie o typie lokalnym stosowana na poziomie procedury. Nie można zadeklarować zmienne na poziomie modułu (w ramach klasy, struktury, modułu lub interfejs jednak nie wcześniej niż procedurę lub blok). Jeśli `num2` w poprzednim przykładzie zostały pola klasy zamiast zmiennej lokalnej w procedurze, deklaracji mogłoby spowodować błąd `Option Strict` i czy sklasyfikować `num2` jako `Object` z `Option Strict` off. Podobnie, wnioskowanie o typie lokalnym nie ma zastosowania do zmiennych poziomu procedury zadeklarowany jako `Static`.  
  
## <a name="type-inference-vs-late-binding"></a>Wpisz wnioskowania vs. Późne wiązanie  
 Kod używa wnioskowanie typu podobny kod, który korzysta z późnym wiązaniem. Jednak wnioskowanie o typie silnie typy zmiennej zamiast zostawiać je jako `Object`. Kompilator używa inicjator zmiennej można określić typu zmienną w czasie kompilacji, aby wygenerować kod z wczesnym wiązaniem. W poprzednim przykładzie `num2`, takiej jak `num1`, jest typu `Integer`.  
  
 Zachowanie zmiennych z wczesnym wiązaniem różni się od zmiennych z późnym wiązaniem, dla których typ jest znany tylko w czasie wykonywania. Znajomość typu wczesne włącza kompilator, aby zidentyfikować problemy przed realizacją, dokładnie przydzielić pamięci i wykonywać inne optymalizacje. Wczesne powiązania umożliwia również Visual Basic zintegrowane środowisko programistyczne (IDE), aby zapewnić pomoc IntelliSense dotyczących elementów członkowskich obiektu. Wczesne powiązania jest również preferowane wydajności. Jest to spowodowane wszystkie dane przechowywane w zmiennej późnym wiązaniem musi być zawijany jako typ `Object`, i uzyskiwanie dostępu do elementów członkowskich tego typu w czasie wykonywania sprawia, że program wolniej.  
  
## <a name="examples"></a>Przykłady  
 Wnioskowanie o typie występuje, gdy zmienna lokalna jest zadeklarowana bez `As` klauzuli i zainicjować. Kompilator używa typu przypisanej wartości początkowej typu zmienną. Na przykład, każdy z poniższych wierszy kodu deklaruje zmienną typu `String`.  
  
 [!code-vb[VbVbalrTypeInference#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_2.vb)]  
  
 Poniższy kod przedstawia dwa sposoby równoważne do utworzenia tablicy liczb całkowitych.  
  
 [!code-vb[VbVbalrTypeInference#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_3.vb)]  
  
 Jest to łatwe w użyciu wnioskowanie o typie można określić typu zmienna sterująca pętli for. W poniższym kodzie kompilator wnioskuje który `number` jest `Integer` ponieważ `someNumbers2` z poprzedniego przykładu jest tablica liczb całkowitych.  
  
 [!code-vb[VbVbalrTypeInference#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_4.vb)]  
  
 Wnioskowanie o typie lokalnym mogą być używane w `Using` instrukcje w celu ustalenia typu nazwa zasobu, jak w poniższym przykładzie pokazano.  
  
 [!code-vb[VbVbalrTypeInference#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_5.vb)]  
  
 Typ zmiennej również można wywnioskować na podstawie wartości zwracanych z funkcji, jak w poniższym przykładzie pokazano. Zarówno `pList1` i `pList2` są tablice procesy, ponieważ `Process.GetProcesses` zwraca tablicę procesów.  
  
 [!code-vb[VbVbalrTypeInference#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_6.vb)]  
  
## <a name="option-infer"></a>Option Infer  
 `Option Infer` Ta funkcja umożliwia określenie, czy wnioskowanie o typie lokalnym jest dozwolone w pliku. Aby włączyć lub opcji, wpisz jedno z następujących instrukcji na początku pliku.  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 Jeśli nie określisz wartości `Option Infer` w kodzie domyślnym kompilatora jest `Option Infer On`. Dla projektów uaktualnione z [!INCLUDE[vb_orcas_long](~/includes/vb-orcas-long-md.md)] lub starszym, jest domyślną kompilatora `Option Infer Off`.  
  
 Jeśli ustawiona wartość `Option Infer` w pliku powoduje konflikt z wartością ustawioną w IDE lub w wierszu polecenia, wartość w pliku ma pierwszeństwo.  
  
 Aby uzyskać więcej informacji, zobacz [Option Infer — instrukcja](../../../../visual-basic/language-reference/statements/option-infer-statement.md) i [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
## <a name="see-also"></a>Zobacz też  
 [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Wczesne i późne powiązania](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [For Each...Next, instrukcja](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [For...Next, instrukcja](../../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Option Infer, instrukcja](../../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [/optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
