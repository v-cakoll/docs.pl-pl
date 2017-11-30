---
title: /removeintchecks
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- removeintchecks
- /removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e765f0007eea8e196b1a1b3b55b969c5b074b52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="removeintchecks"></a>/removeintchecks
Włącza sprawdzanie operacji liczby całkowitej lub wyłącz błąd przepełnienia.  
  
## <a name="syntax"></a>Składnia  
  
```  
/removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`+` &#124; `-`|Opcjonalny. `/removeintchecks-` Opcja powoduje, że kompilator, aby sprawdzić wszystkie obliczenia całkowitą błędy przepełnienia. Wartość domyślna to `/removeintchecks-`.<br /><br /> Określanie `/removeintchecks` lub `/removeintchecks+` uniemożliwia sprawdzanie błędów i może wykonywać szybsze obliczenia liczby całkowitej. Jednak bez sprawdzania błędów, i jeśli są przepełnienie danych typu pojemności, niepoprawne wyniki mogą być przechowywane bez zgłaszania błędu.|  
  
|Aby ustawić/removeintchecks w programie Visual Studio zintegrowane środowisko deweloperskie|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. Aby uzyskać więcej informacji, zobacz [wprowadzenie do projektanta projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Kliknij przycisk **skompilować** kartę.<br />3.  Kliknij przycisk **zaawansowane** przycisku.<br />4.  Zmodyfikuj wartość **Wyłącz sprawdzanie przepełnienia całkowitych** pole.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `Test.vb` i wyłącza sprawdzanie błąd przepełnienia liczby całkowitej.  
  
```  
vbc /removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Kompilacja przykładów — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
