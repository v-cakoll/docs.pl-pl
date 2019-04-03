---
title: Option Compare — instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Compare
- vb.OptionCompare
helpviewer_keywords:
- case sensitivity, Option Compare statement
- Compare keyword [Visual Basic]
- binary comparison [Visual Basic]
- strings [Visual Basic], returning from functions
- binary comparison [Visual Basic], Option Compare statement
- strings [Visual Basic], comparing
- string comparison [Visual Basic], Option Compare statement
- Text keyword [Visual Basic], Option Compare statement
- Binary keyword [Visual Basic], Option Compare statement
- string comparison [Visual Basic], sorting data
- Option Compare statement [Visual Basic]
- text [Visual Basic], comparing
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
ms.openlocfilehash: b092d54e6cf4d8a96a35e6b1cc818fad8f26e3ae
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834078"
---
# <a name="option-compare-statement"></a>Option Compare — Instrukcja
Deklaruje domyślną metodę porównywania do użycia podczas porównywania danych ciągu.  
  
## <a name="syntax"></a>Składnia  
  
```  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`Binary`|Opcjonalna. Wynikiem porównania ciągów, w oparciu o kolejność sortowania jest pochodną wewnętrzne binarne reprezentacje znaków.<br /><br /> Ten typ porównania przydaje się zwłaszcza, jeśli ciągi mogą zawierać znaków, które nie mają być interpretowane jako tekst. W takim przypadku możesz zrezygnować z obciążenia porównania z wartością alfabetycznej równoważności, takie jak ignorowanie wielkości liter.|  
|`Text`|Opcjonalna. Wyniki w porównań ciągów, w oparciu o kolejność sortowania bez uwzględniania wielkości liter tekstu, określane przez ustawienia regionalne Twojego systemu.<br /><br /> Ten typ porównania jest przydatne, jeśli Twoimi ciągami, zawierać wszystkie znaki, tekst, a chcesz porównać ich równoważniki alfabetyczne konta, takie jak ignorowanie wielkości liter i cyfr ściśle powiązanych z uwzględnieniem. Na przykład możesz chcieć należy wziąć pod uwagę `A` i `a` równe, i `Ä` i `ä` przed `B` i `b`.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli używane, `Option Compare` instrukcja musi znajdować się w pliku przed wszystkimi innymi instrukcjami kodu źródłowego.  
  
 `Option Compare` Instrukcja określa metodę porównywania ciągów (`Binary` lub `Text`).  Domyślna metoda porównania tekstu jest `Binary`.  
  
 A `Binary` porównania porównuje wartość liczbową Unicode każdego znaku w każdym ciągu. A `Text` porównania porównuje każdego znaku Unicode, oparte na ich leksykalne znaczenia w bieżącej kultury.  
  
 W Microsoft Windows kolejność sortowania jest określana przez stronę kodową. Aby uzyskać więcej informacji, zobacz [stron kodowych](/cpp/c-runtime-library/code-pages).  
  
 W poniższym przykładzie znaków na stronie kodowej angielski/Europejskiego (ANSI 1252) są sortowane za pomocą `Option Compare Binary`, która generuje typowych binarny porządek sortowania.  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 Kiedy te same znaki w tej samej stronie kodowej są sortowane za pomocą `Option Compare Text`, generowany jest tekstowy porządek sortowania.  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a>W przypadku opcji Option Compare instrukcja nie jest obecny  
 Jeśli kod źródłowy nie zawiera `Option Compare` instrukcji **Option Compare** ustawienie [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) jest używany. Jeśli używasz kompilatora wiersza polecenia, ustawienia określone przez [/optioncompare —](../../../visual-basic/reference/command-line-compiler/optioncompare.md) — opcja kompilatora jest używany.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a>Można ustawić opcji Option Compare w środowisku IDE  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt. Na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **skompilować** kartę.  
  
3.  Ustaw wartość w **Option Compare** pole.  
  
 Podczas tworzenia projektu, **Option Compare** ustawienie **skompilować** karta jest ustawiona na **Option Compare** w **opcje** okno dialogowe. Aby zmienić to ustawienie, na **narzędzia** menu, kliknij przycisk **opcje**. W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, a następnie kliknij przycisk **ustawienia domyślne VB**. Ustawieniem domyślnym początkowej w **ustawienia domyślne VB** jest **binarne**.  
  
#### <a name="to-set-option-compare-on-the-command-line"></a>Można ustawić opcji Option Compare, w wierszu polecenia  
  
-   Obejmują [/optioncompare —](../../../visual-basic/reference/command-line-compiler/optioncompare.md) w — opcja kompilatora **vbc** polecenia.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Option Compare` instrukcję, aby ustawić porównanie binarne jako domyślną metodę porównywania ciągów. Aby użyć tego kodu, usuń znaczniki komentarza `Option Compare Binary` instrukcji i umieścić go w górnej części pliku źródłowego.  
  
 [!code-vb[VbVbalrStatements#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#45)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Option Compare` instrukcję, aby ustawić kolejność sortowania bez uwzględniania wielkości liter tekstu jako domyślną metodę porównywania ciągów. Aby użyć tego kodu, usuń znaczniki komentarza `Option Compare Text` instrukcji i umieścić go w górnej części pliku źródłowego.  
  
 [!code-vb[VbVbalrStatements#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#46)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>
- <xref:Microsoft.VisualBasic.Strings.Replace%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [Operatory porównania](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Operatory porównania w języku Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Like, operator](../../../visual-basic/language-reference/operators/like-operator.md)
- [Funkcje ciągów](../../../visual-basic/language-reference/functions/string-functions.md)
- [Option Explicit, instrukcja](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
