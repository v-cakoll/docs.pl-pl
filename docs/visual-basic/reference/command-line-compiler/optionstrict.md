---
title: -optionstrict —
ms.date: 07/20/2015
f1_keywords:
- -optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
ms.openlocfilehash: 5479c312ae7eb7a166803a6e1238806aae9bd656
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835664"
---
# <a name="-optionstrict"></a>-optionstrict —
Wymusza semantykę typów ścisłych w celu ograniczenia niejawnych konwersji typów.  
  
## <a name="syntax"></a>Składnia  
  
```  
-optionstrict[+ | -]  
-optionstrict[:custom]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+` &#124; `-`  
 Opcjonalna. `-optionstrict+` Opcja ogranicza niejawna konwersja typu. Wartość domyślna tej opcji to `-optionstrict-`. `-optionstrict+` Opcja jest taka sama jak `-optionstrict`. Można użyć obu tych opcji dla semantyka typów ograniczająca.  
  
 `custom`  
 Wymagana. Ostrzegaj, gdy nie są przestrzegane ścisłą semantykę języka.  
  
## <a name="remarks"></a>Uwagi  
 Gdy `-optionstrict+` obowiązuje, tylko konwersje rozszerzające możliwe niejawnie. Niejawne zawężanie konwersji typów, takich jak przypisywanie `Decimal` typ obiektu do obiektu typu Liczba całkowita, są zgłaszane jako błędy.  
  
 Aby wygenerować ostrzeżeń dotyczących niejawnych konwersji zawężających typu, należy użyć `-optionstrict:custom`. Użyj `-nowarn:numberlist` ignorowania ostrzeżeń dotyczących określonego i `-warnaserror:numberlist` do traktowania określonego ostrzeżenia jako błędy.  
  
### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a>Aby ustawić - optionstrict — w środowisku IDE programu Visual Studio  
  
1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości.**   
  
2.  Kliknij przycisk **skompilować** kartę.  
  
3.  Zmodyfikuj wartość w **Option Strict** pole.  
  
### <a name="to-set--optionstrict-programmatically"></a>Aby programowo ustawić - optionstrict —  
  
-   Zobacz [Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `Test.vb` semantykę typów ścisłych w użyciu.  
  
```console
vbc -optionstrict+ test.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)
- [-warnaserror — (Visual Basic)](../../../visual-basic/reference/command-line-compiler/warnaserror.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Domyślne ustawienia programu Visual Basic, Projekty, Opcje — okno dialogowe](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
