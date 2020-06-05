---
title: Option Explicit, instrukcja
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
ms.openlocfilehash: a352df0323cfeca1ea0e206ae45c3f85a2cd7da3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404372"
---
# <a name="option-explicit-statement-visual-basic"></a>Option Explicit — Instrukcja (Visual Basic)
Wymusza jawną deklarację wszystkich zmiennych w pliku lub zezwala na niejawne deklaracje zmiennych.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a>Części  
 `On`  
 Opcjonalny. Włącza `Option Explicit` Sprawdzanie. Jeśli `On` lub `Off` nie jest określony, wartość domyślna to `On` .  
  
 `Off`  
 Opcjonalny. Wyłącza `Option Explicit` Sprawdzanie.  
  
## <a name="remarks"></a>Uwagi  
 Gdy `Option Explicit On` lub `Option Explicit` pojawia się w pliku, należy jawnie zadeklarować wszystkie zmienne przy użyciu `Dim` instrukcji or `ReDim` . Jeśli spróbujesz użyć niezadeklarowanej nazwy zmiennej, wystąpi błąd w czasie kompilacji. `Option Explicit Off`Instrukcja umożliwia niejawną deklarację zmiennych.  
  
 Jeśli jest używana, `Option Explicit` instrukcja musi pojawić się w pliku przed innymi instrukcjami kodu źródłowego.  
  
> [!NOTE]
> Ustawienie `Option Explicit` na `Off` ogół nie jest dobrym sposobem. W co najmniej jednej lokalizacji można wypróbować nazwę zmiennej, co spowodowałoby nieoczekiwane wyniki, gdy program zostanie uruchomiony.  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a>Gdy nie ma instrukcji Option Explicit  
 Jeśli kod źródłowy nie zawiera `Option Explicit` instrukcji, zostanie użyta **opcja jawne** ustawienie na [stronie kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) . Jeśli jest używany kompilator wiersza polecenia, opcja kompilatora [-optionexplicit](../../reference/command-line-compiler/optionexplicit.md) jest używana.  
  
#### <a name="to-set-option-explicit-in-the-ide"></a>Aby ustawić opcję jawną w środowisku IDE  
  
1. W **Eksplorator rozwiązań**wybierz projekt. W menu **projekt** kliknij polecenie **Właściwości**.  
  
2. Kliknij kartę **kompilacja** .  
  
3. Ustaw wartość w polu **opcja jawna** .  
  
 Podczas tworzenia nowego projektu **opcja ustawienie jawne** na karcie **kompilowania** jest ustawiona na wartość ustawienie **jawne** w oknie dialogowym **Ustawienia domyślne języka vb** . Aby uzyskać dostęp do okna dialogowego **Ustawienia domyślne VB** , w menu **Narzędzia** kliknij polecenie **Opcje**. W oknie dialogowym **Opcje** rozwiń węzeł **projekty i rozwiązania**, a następnie kliknij pozycję **Ustawienia domyślne w języku VB**. Początkowe domyślne ustawienie w **języku VB** domyślnie ma wartość `On` .  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a>Aby ustawić opcję jawną w wierszu polecenia  
  
- Dołącz opcję kompilatora [-optionexplicit](../../reference/command-line-compiler/optionexplicit.md) w poleceniu **VBC** .  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa instrukcji, `Option Explicit` Aby wymusić jawną deklarację wszystkich zmiennych. Próba użycia niezadeklarowanej zmiennej powoduje błąd w czasie kompilacji.  
  
 [!code-vb[VbVbalrStatements#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#47)]  
  
 [!code-vb[VbVbalrStatements#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#48)]  
  
## <a name="see-also"></a>Zobacz też

- [Dim, instrukcja](dim-statement.md)
- [ReDim, instrukcja](redim-statement.md)
- [Option Compare — Instrukcja](option-compare-statement.md)
- [Option Strict — Instrukcja](option-strict-statement.md)
- [-optioncompare](../../reference/command-line-compiler/optioncompare.md)
- [-optionexplicit](../../reference/command-line-compiler/optionexplicit.md)
- [-optionstrict](../../reference/command-line-compiler/optionstrict.md)
- [Domyślne ustawienia programu Visual Basic, Projekty, Opcje — okno dialogowe](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
