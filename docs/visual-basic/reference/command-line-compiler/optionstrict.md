---
title: /optionstrict
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 692681b21c243432ec8e7160bcc1eaa4e718d64d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="optionstrict"></a>/optionstrict
Wymusza ścisłe zasady semantyki ograniczyć niejawne konwersje typów.  
  
## <a name="syntax"></a>Składnia  
  
```  
/optionstrict[+ | -]  
/optionstrict[:custom]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+` &#124; `-`  
 Opcjonalny. `/optionstrict+` Opcja ogranicza niejawna konwersja typu. Wartość domyślna dla tej opcji to `/optionstrict-`. `/optionstrict+` Opcji jest taka sama jak `/optionstrict`. Można użyć zarówno dla typu ograniczająca semantyki.  
  
 `custom`  
 Wymagany. Ostrzegaj, gdy ścisła semantyka języka nie są przestrzegane.  
  
## <a name="remarks"></a>Uwagi  
 Gdy `/optionstrict+` w efekcie jest niejawnie może być utworzona tylko rozszerzającą konwersje typów. Zawężanie konwersji typu, takich jak przypisywanie niejawne `Decimal` typ obiektu do obiektu typu Liczba całkowita, są raportowane klientowi jako błędy.  
  
 Aby wygenerować ostrzeżenia dla niejawnej konwersji zawężającej typu, należy użyć `/optionstrict:custom`. Użyj `/nowarn:numberlist` ignorowania ostrzeżeń dotyczących określonego i `/warnaserror:numberlist` traktować określonego ostrzeżenia jako błędy.  
  
### <a name="to-set-optionstrict-in-the-visual-studio-ide"></a>Aby ustawić/optionstrict — w programie Visual Studio IDE  
  
1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości.**   
  
2.  Kliknij przycisk **skompilować** kartę.  
  
3.  Zmodyfikuj wartość w **Option Strict** pole.  
  
### <a name="to-set-optionstrict-programmatically"></a>Aby ustawić/optionstrict — programowo  
  
-   Zobacz [Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `Test.vb` za pomocą semantyki typu strict.  
  
```  
vbc /optionstrict+ test.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)  
 [/ warnaserror (Visual Basic)](../../../visual-basic/reference/command-line-compiler/warnaserror.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Okno dialogowe Opcje domyślne, projektów, Visual Basic](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
