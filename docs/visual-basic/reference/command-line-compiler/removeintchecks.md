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
ms.openlocfilehash: 917977d8e5e12c231370ab3c956aca9d96e8a8a8
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. <br />2.  Kliknij przycisk **skompilować** kartę.<br />3.  Kliknij przycisk **zaawansowane** przycisku.<br />4.  Zmodyfikuj wartość **Wyłącz sprawdzanie przepełnienia całkowitych** pole.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `Test.vb` i wyłącza sprawdzanie błąd przepełnienia liczby całkowitej.  
  
```  
vbc /removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
