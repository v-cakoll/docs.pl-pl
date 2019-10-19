---
title: Option Compare — Instrukcja (Visual Basic)
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
ms.openlocfilehash: 43d3faf3a6630cd308913ce2325a5f7fe96e474c
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581584"
---
# <a name="option-compare-statement"></a>Option Compare — Instrukcja
Deklaruje domyślną metodę porównania do użycia podczas porównywania danych ciągu.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`Binary`|Opcjonalny. Wyniki porównywania ciągów na podstawie kolejności sortowania pochodzącej z wewnętrznych reprezentacji binarnych znaków.<br /><br /> Ten typ porównania jest przydatny zwłaszcza wtedy, gdy ciągi mogą zawierać znaki, które nie są interpretowane jako tekst. W tym przypadku nie chcesz porównań z odpowiednikami alfabetycznymi, na przykład bez uwzględniania wielkości liter.|  
|`Text`|Opcjonalny. Wyniki porównywania ciągów na podstawie kolejności sortowania tekstu niezależnego od wielkości liter, ustalonej przez ustawienia regionalne systemu.<br /><br /> Ten typ porównania jest przydatny, jeśli ciągi zawierają wszystkie znaki tekstowe i chcesz je porównać przy uwzględnieniu równoważności alfabetycznej, takich jak nieuwzględnianie wielkości liter i ściśle powiązane litery. Przykładowo warto rozważyć, `A` i `a` być równe, a `Ä` i `ä` przed `B` i `b`.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli jest używana, instrukcja `Option Compare` musi znajdować się w pliku przed wszelkimi innymi instrukcjami kodu źródłowego.  
  
 Instrukcja `Option Compare` określa metodę porównania ciągów (`Binary` lub `Text`).  Domyślna metoda porównywania tekstu to `Binary`.  
  
 Porównanie `Binary` porównuje wartość liczbową Unicode każdego znaku w każdym ciągu. Porównanie `Text` porównuje każdy znak Unicode w oparciu o jego leksykalne znaczenie w bieżącej kulturze.  
  
 W systemie Microsoft Windows kolejność sortowania jest określana przez stronę kodową. Aby uzyskać więcej informacji, zobacz [stronę kodową](/cpp/c-runtime-library/code-pages).  
  
 W poniższym przykładzie znaki na stronie kodowej angielski/Europa (ANSI 1252) są sortowane przy użyciu `Option Compare Binary`, co daje typowy binarny porządek sortowania.  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 Gdy te same znaki na tej samej stronie kodowej są sortowane przy użyciu `Option Compare Text`, generowany jest następujący porządek sortowania tekstu.  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a>Gdy nie ma instrukcji Compare  
 Jeśli kod źródłowy nie zawiera instrukcji `Option Compare`, zostanie użyta **opcja porównanie** ustawienia na [stronie kompilowania, projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) . Jeśli używasz kompilatora wiersza polecenia, ustawienie określone przez opcję kompilatora [/optioncompare —](../../../visual-basic/reference/command-line-compiler/optioncompare.md) jest używane.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a>Aby ustawić opcję Porównaj w środowisku IDE  
  
1. W **Eksplorator rozwiązań**wybierz projekt. W menu **projekt** kliknij polecenie **Właściwości**.  
  
2. Kliknij kartę **kompilacja** .  
  
3. Ustaw wartość w polu **Compare (porównanie opcji** ).  
  
 Podczas tworzenia projektu **opcja Porównaj** ustawienie na karcie **kompilowania** jest ustawiona na **opcję Porównaj** ustawienia w oknie dialogowym **Opcje** . Aby zmienić to ustawienie, w menu **Narzędzia** kliknij polecenie **Opcje**. W oknie dialogowym **Opcje** rozwiń węzeł **projekty i rozwiązania**, a następnie kliknij pozycję **Ustawienia domyślne w języku VB**. Początkowe domyślne ustawienie w **języku VB** jest wartością **binarną**.  
  
#### <a name="to-set-option-compare-on-the-command-line"></a>Aby ustawić opcję Compare w wierszu polecenia  
  
- Dołącz opcję kompilatora [/optioncompare —](../../../visual-basic/reference/command-line-compiler/optioncompare.md) do polecenia **VBC** .  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa instrukcji `Option Compare`, aby ustawić porównanie binarne jako domyślną metodę porównywania ciągów. Aby użyć tego kodu, Usuń komentarz instrukcji `Option Compare Binary` i umieść go w górnej części pliku źródłowego.  
  
 [!code-vb[VbVbalrStatements#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#45)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa instrukcji `Option Compare`, aby ustawić kolejność sortowania tekstu bez uwzględniania wielkości liter jako domyślną metodę porównywania ciągów. Aby użyć tego kodu, Usuń komentarz instrukcji `Option Compare Text` i umieść go w górnej części pliku źródłowego.  
  
 [!code-vb[VbVbalrStatements#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#46)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>
- <xref:Microsoft.VisualBasic.Strings.Replace%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [Operatory porównania](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Operatory porównania w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Like, operator](../../../visual-basic/language-reference/operators/like-operator.md)
- [Funkcje ciągów](../../../visual-basic/language-reference/functions/string-functions.md)
- [Option Explicit, instrukcja](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
