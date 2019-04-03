---
title: Option Infer — instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.OptionInfer
- vb.Infer
helpviewer_keywords:
- variables [Visual Basic], declaring
- Option Infer statement [Visual Basic]
- Infer keyword [Visual Basic]
- declaring variables [Visual Basic], inferred
- inferred variable declaration
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
ms.openlocfilehash: a3846c952969a4814151757c5210d9df6f3c97b4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823496"
---
# <a name="option-infer-statement"></a>Option Infer — Instrukcja
Umożliwia użycie wnioskowania o typie lokalnym w zadeklarowania zmiennych.  
  
## <a name="syntax"></a>Składnia  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`On`|Opcjonalna. Umożliwia wnioskowanie o typie lokalnym.|  
|`Off`|Opcjonalna. Wyłącza wnioskowanie o typie lokalnym.|  
  
## <a name="remarks"></a>Uwagi  
 Aby ustawić `Option Infer` w pliku, wpisz `Option Infer On` lub `Option Infer Off` w górnej części pliku, przed uruchomieniem jakiegokolwiek kodu źródłowego. Jeśli ustawiono wartość `Option Infer` w pliku powoduje konflikt z wartości ustawionej w IDE lub w wierszu polecenia, wartość w pliku ma pierwszeństwo.  
  
 Po ustawieniu `Option Infer` do `On`, zmienne lokalne można deklarować bez jawne określenie typu danych. Kompilator wnioskuje typ danych zmiennej z typu jej wyrażenia inicjowania.  
  
 Na poniższej ilustracji `Option Infer` jest włączona. Zmienna w deklaracji `Dim someVar = 2` jest zadeklarowany jako liczba całkowita, wnioskowanie o typie.

 Poniższy zrzut ekranu przedstawia IntelliSense, gdy Option Infer znajduje się na: 
  
 ![Zrzut ekranu przedstawiający widok IntelliSense, gdy Option Infer znajduje się na.](./media/option-infer-statement/option-infer-as-integer-on.png)  
  
 Na poniższej ilustracji `Option Infer` jest wyłączona. Zmienna w deklaracji `Dim someVar = 2` jest zadeklarowany jako `Object` przez wnioskowanie o typie. W tym przykładzie **Option Strict** jest ustawiana **poza** na [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
 Poniższy zrzut ekranu przedstawia IntelliSense, gdy Option Infer jest wyłączony:
 
 ![Zrzut ekranu przedstawiający widok IntelliSense, gdy Option Infer jest wyłączony.](./media/option-infer-statement/option-infer-as-object-off.png)  
  
> [!NOTE]
>  Gdy zmienna jest zadeklarowana jako `Object`, można zmienić typu run-time, gdy program jest uruchomiony. Visual Basic wykonuje operacje o nazwie *pakowania* i *Rozpakowywanie* do konwersji między `Object` i typie wartości, co sprawia, że wykonanie wolniej. Uzyskać informacji o konwersji boxing i konwersja unboxing, zobacz [specyfikacja języka Visual Basic](~/_vblang/spec/conversions.md#value-type-conversions).
  
 Wnioskowanie o typie ma zastosowanie na poziomie procedury i nie ma zastosowania poza procedury w klasie, strukturze, modułu lub interfejs.  
  
 Aby uzyskać więcej informacji, zobacz [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
## <a name="when-an-option-infer-statement-is-not-present"></a>Podczas Option Infer — instrukcja nie jest obecny  
 Jeśli kod źródłowy nie zawiera `Option Infer` instrukcji **Option Infer** ustawienie [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) jest używany. Jeśli jest używany kompilator w wierszu polecenia, [/optioninfer —](../../../visual-basic/reference/command-line-compiler/optioninfer.md) — opcja kompilatora jest używany.  
  
#### <a name="to-set-option-infer-in-the-ide"></a>Aby ustawić Option Infer w środowisku IDE  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt. Na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **skompilować** kartę.  
  
3.  Ustaw wartość w **Option infer** pole.  
  
 Podczas tworzenia nowego projektu **Option Infer** ustawienie **skompilować** karta jest ustawiona na **Option Infer** w **ustawienia domyślne VB** okno dialogowe. Aby uzyskać dostęp do **ustawienia domyślne VB** dialogowym **narzędzia** menu, kliknij przycisk **opcje**. W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, a następnie kliknij przycisk **ustawienia domyślne VB**. Ustawieniem domyślnym początkowej w **ustawienia domyślne VB** jest `On`.  
  
#### <a name="to-set-option-infer-on-the-command-line"></a>Aby ustawić Option Infer w wierszu polecenia  
  
-   Obejmują [/optioninfer —](../../../visual-basic/reference/command-line-compiler/optioninfer.md) w — opcja kompilatora **vbc** polecenia.  
  
## <a name="default-data-types-and-values"></a>Dane domyślne typy i wartości  
 W poniższej tabeli opisano wyniki różnych kombinacji określania typu danych i inicjatora w `Dim` instrukcji.  
  
|Określony typ danych?|Inicjatora określona?|Przykład|Wynik|  
|---|---|---|---|  
|Nie|Nie|`Dim qty`|Jeśli `Option Strict` jest wyłączone (domyślnie), zmienna jest ustawiana `Nothing`.<br /><br /> Jeśli `Option Strict` jest włączona, wystąpi błąd kompilacji.|  
|Nie|Tak|`Dim qty = 5`|Jeśli `Option Infer` znajduje się na (ustawienie domyślne), zmienna przyjmuje dane typu inicjatora. Zobacz [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Jeśli `Option Infer` jest wyłączona i `Option Strict` jest wyłączone, zmienna ma typ danych `Object`.<br /><br /> Jeśli `Option Infer` jest wyłączona i `Option Strict` jest włączona, wystąpi błąd kompilacji.|  
|Tak|Nie|`Dim qty As Integer`|Zmienna jest ustawiana na wartość domyślną dla typu danych. Aby uzyskać więcej informacji, zobacz [instrukcji Dim](../../../visual-basic/language-reference/statements/dim-statement.md).|  
|Tak|Tak|`Dim qty  As Integer = 5`|Jeśli typ danych Inicjator nie jest konwertowany na określony typ danych, wystąpi błąd kompilacji.|  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano sposób, w jaki `Option Infer` instrukcji umożliwia wnioskowanie o typie lokalnym.  
  
 [!code-vb[VbVbalrTypeInference#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#6)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, że typu run-time może się różnić, gdy zmienna jest identyfikowany jako `Object`.  
  
 [!code-vb[VbVbalrTypeInference#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>Zobacz także

- [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Compare, instrukcja](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Option Explicit, instrukcja](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Domyślne ustawienia programu Visual Basic, Projekty, Opcje — okno dialogowe](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Konwersja boxing i konwersja unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
