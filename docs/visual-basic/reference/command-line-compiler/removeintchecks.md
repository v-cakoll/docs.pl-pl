---
title: -removeintchecks
ms.date: 03/13/2018
f1_keywords:
- removeintchecks
- -removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
ms.openlocfilehash: c086a031d5cef4563a6769e7683dcb1110b8fe49
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822729"
---
# <a name="-removeintchecks"></a>-removeintchecks
Włącza sprawdzanie operacji liczby całkowitej lub wyłącz błąd przepełnienia.  
  
## <a name="syntax"></a>Składnia  
  
```  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`+` &#124; `-`|Opcjonalna. `-removeintchecks-` Opcja powoduje, że kompilator będzie sprawdzać wszystkich obliczeń na liczbach całkowitych błędy przepełnienia. Wartość domyślna to `-removeintchecks-`.<br /><br /> Określanie `-removeintchecks` lub `-removeintchecks+` zapobiega, sprawdzanie błędów i może szybciej obliczeń na liczbach całkowitych. Jednak bez sprawdzania błędów, i jeśli są przepełnienie pojemności typu danych, bez zgłaszania błędu mogą być przechowywane niepoprawne wyniki.|  
  
|Aby ustawić - removeintchecks w programie Visual Studio zintegrowane środowisko projektowe|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. <br />2.  Kliknij przycisk **skompilować** kartę.<br />3.  Kliknij przycisk **zaawansowane** przycisku.<br />4.  Zmodyfikuj wartość **Usuń nadmiaru** pole.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `Test.vb` i wyłącza sprawdzanie błąd przepełnienia liczby całkowitej.  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
