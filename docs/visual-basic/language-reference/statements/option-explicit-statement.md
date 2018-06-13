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
ms.openlocfilehash: 3a2d81b1441052c132e4739dfe6045f8c3a026d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604604"
---
# <a name="option-explicit-statement-visual-basic"></a>Option Explicit — Instrukcja (Visual Basic)
Wymusza jawnej deklaracji wszystkich zmiennych w pliku lub zezwala na niejawne deklaracji zmiennych.  
  
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
 Gdy `Option Explicit On` lub `Option Explicit` pojawia się w pliku, musisz jawnie zadeklarować wszystkie zmienne przy użyciu `Dim` lub `ReDim` instrukcje. Jeśli spróbujesz użyć niezadeklarowanego nazwę zmiennej, wystąpi błąd w czasie kompilacji. `Option Explicit Off` Instrukcji zezwala na niejawne deklaracji zmiennych.  
  
 Jeśli używana, `Option Explicit` instrukcji musi występować w pliku przed wszystkimi innymi instrukcjami kodu źródłowego.  
  
> [!NOTE]
>  Ustawienie `Option Explicit` do `Off` zwykle nie jest dobrym rozwiązaniem. Można wpiszesz nazwę zmiennej w przynajmniej jednej lokalizacji, co może spowodować nieoczekiwane wyniki, gdy program jest uruchamiany.  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a>Jeśli nie jest obecny Option Explicit — instrukcja  
 Jeśli kod źródłowy nie zawiera `Option Explicit` instrukcji, **Option Explicit** ustawienie [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) jest używany. Jeśli używana jest kompilatora wiersza polecenia, [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) — opcja kompilatora jest używany.  
  
#### <a name="to-set-option-explicit-in-the-ide"></a>Aby ustawić Option Explicit w środowisku IDE  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt. Na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **skompilować** kartę.  
  
3.  Ustaw wartość **Option Explicit** pole.  
  
 Podczas tworzenia nowego projektu **Option Explicit** ustawienie **skompilować** ustawiono kartę **Option Explicit** ustawienie **VB domyślne**okno dialogowe. Aby uzyskać dostęp do **domyślne VB** okna dialogowego, na **narzędzia** menu, kliknij przycisk **opcje**. W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, a następnie kliknij przycisk **domyślne VB**. Ustawieniem domyślnym początkowej w **domyślne VB** jest `On`.  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a>Aby ustawić Option Explicit w wierszu polecenia  
  
-   Obejmują [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) w — opcja kompilatora **vbc** polecenia.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Option Explicit` instrukcji, aby wymusić jawnej deklaracji wszystkich zmiennych. Podjęto próbę użycia niezadeklarowanej zmiennej powoduje błąd w czasie kompilacji.  
  
 [!code-vb[VbVbalrStatements#47](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_1.vb)]  
  
 [!code-vb[VbVbalrStatements#48](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [ReDim, instrukcja](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [Option Compare, instrukcja](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [Okno dialogowe Opcje domyślne, projektów, Visual Basic](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
