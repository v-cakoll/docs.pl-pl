---
title: -optioncompare
ms.date: 07/20/2015
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
ms.openlocfilehash: ee130073b95dfbab5616a54c188b09fa92ccc930
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005364"
---
# <a name="-optioncompare"></a>-optioncompare
Określa sposób, w jaki są wykonywane porównania ciągów.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a>Uwagi  
 Można określić `-optioncompare` w jednej z dwóch form: `-optioncompare:binary`, aby użyć porównań ciągów binarnych i `-optioncompare:text` do użycia porównania ciągów tekstowych. Domyślnie kompilator używa `-optioncompare:binary`.  
  
 W systemie Microsoft Windows bieżąca strona kodowa Określa binarny porządek sortowania. Typowa binarna kolejność sortowania jest następująca:  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 Porównania ciągów tekstowych są oparte na kolejności sortowania tekstu bez uwzględniania wielkości liter, która zależy od ustawień regionalnych systemu. Typowy porządek sortowania tekstu jest następujący:  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a>Aby ustawić-optioncompare w środowisku IDE programu Visual Studio  
  
1. Zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** kliknij polecenie **Właściwości**.   
  
2. Kliknij kartę **kompilacja** .  
  
3. Zmodyfikuj wartość w polu **PORÓWNAJ opcję** .  
  
### <a name="to-set--optioncompare-programmatically"></a>Aby programowo ustawić — optioncompare  
  
- Zobacz [Option Compare instrukcji](../../../visual-basic/language-reference/statements/option-compare-statement.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `ProjFile.vb` i używa porównywania ciągów binarnych.  
  
```console
vbc -optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Compare, instrukcja](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Domyślne ustawienia programu Visual Basic, Projekty, Opcje — okno dialogowe](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
