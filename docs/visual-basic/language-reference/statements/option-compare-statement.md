---
title: "Option Compare — Instrukcja"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "37"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 00753eddb641c07ef9c6e6282fe00c5e8d00547a
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="option-compare-statement"></a>Option Compare — Instrukcja
Deklaruje domyślną metodę porównywania do używania przy porównywaniu danych ciągów.  
  
## <a name="syntax"></a>Składnia  
  
```  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`Binary`|Opcjonalny. Wynikiem porównania ciągu oparte na kolejność sortowania, pochodzi z wewnętrznego reprezentacje binarne znaków.<br /><br /> Ten typ porównania jest szczególnie przydatny w przypadku ciągi mogą zawierać znaki, które nie mają być interpretowane jako tekst. W takim przypadku nie chcesz odchylenia porównania z alfabetyczną ekwiwalenty, takich jak ignorowanie wielkości liter.|  
|`Text`|Opcjonalny. Wynikiem porównania ciągu oparte na porządek sortowania bez uwzględniania wielkości liter tekstu ustaleniami ustawień regionalnych systemu.<br /><br /> Jeśli Twoje ciągi zawiera wszystkie znaki tekstu i chcesz porównać je z uwzględnieniem konta ekwiwalenty alfabetyczne, takich jak liter i cyfr blisko związane przydaje porównania tego typu. Na przykład, warto rozważyć `A` i `a` równe, i `Ä` i `ä` przed `B` i `b`.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli używana, `Option Compare` instrukcji musi występować w pliku przed wszystkimi innymi instrukcjami kodu źródłowego.  
  
 `Option Compare` Instrukcji określa metodę porównywania ciągów (`Binary` lub `Text`).  Domyślną metodę porównywania tekst jest `Binary`.  
  
 A `Binary` wartość liczbową Unicode każdego znaku w ciągu każdej porównuje porównania. A `Text` porównania porównuje każdego znaku Unicode oparte na jego leksykalne znaczenie w bieżącej kultury.  
  
 W systemie Microsoft Windows kolejność sortowania jest określany za pomocą stron kodowych. Aby uzyskać więcej informacji, zobacz [stron kodowych](/cpp/c-runtime-library/code-pages).  
  
 W poniższym przykładzie znaków w stronie kodowej angielski/Europejskiej (ANSI 1252) są sortowane przy użyciu `Option Compare Binary`, która tworzy typowe binarny porządek sortowania.  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 Gdy te same znaki w tej samej strony kodowej są sortowane przy użyciu `Option Compare Text`, jest generowany tekstowy porządek sortowania.  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a>Po opcji Option Compare — instrukcja nie jest obecny  
 Jeśli kod źródłowy nie zawiera `Option Compare` instrukcji, **Option Compare** ustawienie [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) jest używany. Jeśli używasz kompilatora wiersza polecenia, ustawienia określone przez [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) — opcja kompilatora jest używany.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a>Aby ustawić Option Compare w środowisku IDE  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt. Na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **skompilować** kartę.  
  
3.  Ustaw wartość **Option Compare** pole.  
  
 Podczas tworzenia projektu, **Option Compare** ustawienie **skompilować** ustawiono kartę **Option Compare** w **opcje** okno dialogowe. Aby zmienić to ustawienie, na **narzędzia** menu, kliknij przycisk **opcje**. W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, a następnie kliknij przycisk **domyślne VB**. Ustawieniem domyślnym początkowej w **domyślne VB** jest **binarne**.  
  
#### <a name="to-set-option-compare-on-the-command-line"></a>Aby ustawić Option Compare w wierszu polecenia  
  
-   Obejmują [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) w — opcja kompilatora **vbc** polecenia.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Option Compare` instrukcji, aby ustawić porównanie binarne jako domyślną metodę porównywania ciągów. Aby użyć tego kodu, usuń znaczniki komentarza `Option Compare Binary` instrukcji i umieszcza je w górnej części pliku źródłowego.  
  
 [!code-vb[VbVbalrStatements#45](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_1.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Option Compare` instrukcji, aby ustawić kolejność sortowania bez uwzględniania wielkości liter tekstu jako domyślną metodę porównywania ciągów. Aby użyć tego kodu, usuń znaczniki komentarza `Option Compare Text` instrukcji i umieszcza je w górnej części pliku źródłowego.  
  
 [!code-vb[VbVbalrStatements#46](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A>  
 <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>  
 <xref:Microsoft.VisualBasic.Strings.Replace%2A>  
 <xref:Microsoft.VisualBasic.Strings.Split%2A>  
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A>  
 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [Operatory porównania](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [Operatory porównania w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Like, operator](../../../visual-basic/language-reference/operators/like-operator.md)  
 [Funkcje ciągów](../../../visual-basic/language-reference/functions/string-functions.md)  
 [Option Explicit, instrukcja](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
