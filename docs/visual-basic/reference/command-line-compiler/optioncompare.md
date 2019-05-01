---
title: -optioncompare —
ms.date: 07/20/2015
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
ms.openlocfilehash: b88cba4d16c5a770a72b47868d11b16cbba6cae8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788963"
---
# <a name="-optioncompare"></a>-optioncompare —
Określa, jak są wykonywane porównywania ciągów.  
  
## <a name="syntax"></a>Składnia  
  
```  
-optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a>Uwagi  
 Można określić `-optioncompare` w jednej z dwóch formach: `-optioncompare:binary` używać ciąg binarny porównań, i `-optioncompare:text` używać porównania ciągów tekstu. Domyślnie kompilator używa `-optioncompare:binary`.  
  
 W Windows firmy Microsoft w bieżącej stronie kodowej Określa binarny porządek sortowania. Typowe binarny porządek sortowania jest następująca:  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 Porównywanie ciągów tekstowych opierają się na kolejność sortowania bez uwzględniania wielkości liter tekstu, określane przez ustawienia regionalne Twojego systemu. Typowe tekstowy porządek sortowania jest następująca:  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a>Aby ustawić - optioncompare — w środowisku IDE programu Visual Studio  
  
1. Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**.   
  
2. Kliknij przycisk **skompilować** kartę.  
  
3. Zmodyfikuj wartość w **Option Compare** pole.  
  
### <a name="to-set--optioncompare-programmatically"></a>Aby programowo ustawić - optioncompare —  
  
- Zobacz [Option Compare — instrukcja](../../../visual-basic/language-reference/statements/option-compare-statement.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `ProjFile.vb` i używa porównania ciągów binarnych.  
  
```console
vbc -optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Compare, instrukcja](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Domyślne ustawienia programu Visual Basic, Projekty, Opcje — okno dialogowe](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
