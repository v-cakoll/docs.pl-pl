---
title: Option Explicit — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Explicit
- vb.OptionExplicit
helpviewer_keywords:
- declaring variables [Visual Basic], explicit
- forced variable declaration in Option Explicit statement [Visual Basic]
- Explicit keyword
- explicit variable declaration
- Option Explicit statement [Visual Basic]
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
ms.openlocfilehash: 0a319ba4259e66ed9a37aa2de9e97d2335b78663
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59308617"
---
# <a name="option-explicit-statement-visual-basic"></a>Option Explicit — Instrukcja (Visual Basic)
Wymusza jawnej deklaracji wszystkich zmiennych w pliku lub zezwala na niejawne deklaracje zmiennych.  
  
## <a name="syntax"></a>Składnia  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a>Części  
 `On`  
 Opcjonalna. Włącza `Option Explicit` sprawdzania. Jeśli `On` lub `Off` nie zostanie określony, wartością domyślną jest `On`.  
  
 `Off`  
 Opcjonalna. Wyłącza `Option Explicit` sprawdzania.  
  
## <a name="remarks"></a>Uwagi  
 Gdy `Option Explicit On` lub `Option Explicit` pojawia się w pliku, należy jawnie deklarować wszystkie zmienne, za pomocą `Dim` lub `ReDim` instrukcji. Jeśli zostanie podjęta próba użycia nazwy zmiennej niezadeklarowany, wystąpi błąd w czasie kompilacji. `Option Explicit Off` Instrukcji umożliwia niejawne deklaracji zmiennych.  
  
 Jeśli używane, `Option Explicit` instrukcja musi znajdować się w pliku przed wszystkimi innymi instrukcjami kodu źródłowego.  
  
> [!NOTE]
>  Ustawienie `Option Explicit` do `Off` zwykle nie jest dobrym rozwiązaniem. Można błędnego wpisania nazwy zmiennej w przynajmniej jednej lokalizacji, co mogłoby spowodować nieoczekiwane wyniki, gdy program jest uruchamiany.  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a>Jeśli nie jest obecny Option Explicit — instrukcja  
 Jeśli kod źródłowy nie zawiera `Option Explicit` instrukcji **Option Explicit** ustawienie [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) jest używany. Jeśli jest używany kompilator w wierszu polecenia, [/optionexplicit —](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) — opcja kompilatora jest używany.  
  
#### <a name="to-set-option-explicit-in-the-ide"></a>Aby ustawić Option Explicit w środowisku IDE  
  
1. W **Eksploratora rozwiązań**, wybierz projekt. Na **projektu** menu, kliknij przycisk **właściwości**.  
  
2. Kliknij przycisk **skompilować** kartę.  
  
3. Ustaw wartość w **Option Explicit** pole.  
  
 Podczas tworzenia nowego projektu **Option Explicit** ustawienie **skompilować** karta jest ustawiona na **Option Explicit** ustawienie w **VB domyślnie**okno dialogowe. Aby uzyskać dostęp do **ustawienia domyślne VB** dialogowym **narzędzia** menu, kliknij przycisk **opcje**. W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, a następnie kliknij przycisk **ustawienia domyślne VB**. Ustawieniem domyślnym początkowej w **ustawienia domyślne VB** jest `On`.  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a>Aby ustawić Option Explicit, w wierszu polecenia  
  
-   Obejmują [/optionexplicit —](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) w — opcja kompilatora **vbc** polecenia.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Option Explicit` instrukcję, aby wymusić jawnej deklaracji wszystkich zmiennych. Podjęto próbę użycia niezadeklarowana zmienna powoduje błąd w czasie kompilacji.  
  
 [!code-vb[VbVbalrStatements#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#47)]  
  
 [!code-vb[VbVbalrStatements#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#48)]  
  
## <a name="see-also"></a>Zobacz także

- [Dim — instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)
- [ReDim — Instrukcja](../../../visual-basic/language-reference/statements/redim-statement.md)
- [Option Compare — Instrukcja](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Option Strict — Instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [Domyślne ustawienia programu Visual Basic, Projekty, okno dialogowe Opcje](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
