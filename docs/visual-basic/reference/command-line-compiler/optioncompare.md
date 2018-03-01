---
title: /optioncompare
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 62a9a4bf3428f3ee731e7ecc63be51dbf3076ee4
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="optioncompare"></a>/optioncompare
Określa, jak zostały wprowadzone porównywania ciągów.  
  
## <a name="syntax"></a>Składnia  
  
```  
/optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a>Uwagi  
 Można określić `/optioncompare` w jednym z dwóch formach: `/optioncompare:binary` do używania porównania ciągu binarnego i `/optioncompare:text` do używania porównania ciągów tekstu. Domyślnie używa kompilator `/optioncompare:binary`.  
  
 W systemie Microsoft Windows strona kodowa używana Określa binarny porządek sortowania. Typowy binarny porządek sortowania jest następujący:  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 Porównywanie ciągów tekstowych są oparte na porządek sortowania bez uwzględniania wielkości liter tekstu ustaleniami ustawień regionalnych systemu. Typowy tekstowy porządek sortowania jest następujący:  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set-optioncompare-in-the-visual-studio-ide"></a>Aby ustawić/optioncompare w środowisku IDE programu Visual Studio  
  
1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**.   
  
2.  Kliknij przycisk **skompilować** kartę.  
  
3.  Zmodyfikuj wartość w **Option Compare** pole.  
  
### <a name="to-set-optioncompare-programmatically"></a>Aby ustawić/optioncompare programowo  
  
-   Zobacz [Option Compare — instrukcja](../../../visual-basic/language-reference/statements/option-compare-statement.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `ProjFile.vb` i używa porównania ciągu binarnego.  
  
```  
vbc /optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Option Compare, instrukcja](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [Okno dialogowe Opcje domyślne, projektów, Visual Basic](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
