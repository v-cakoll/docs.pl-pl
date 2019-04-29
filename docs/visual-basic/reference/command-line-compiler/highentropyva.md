---
title: -highentropyva (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
ms.openlocfilehash: 16bfea37a5742ac5aaaabfacdcf03a2b5bedb6db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663274"
---
# <a name="-highentropyva-visual-basic"></a>-highentropyva (Visual Basic)
Wskazuje, czy 64-bitowy plik wykonywalny lub plik wykonywalny, który jest oznaczony za [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) — opcja kompilatora obsługuje o wysokiej entropii adres miejsca układ losowe (ASLR).  
  
## <a name="syntax"></a>Składnia  
  
```  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+` &#124; `-`  
 Opcjonalna. Opcja jest domyślnie wyłączona, lub jeśli określisz `-highentropyva-`. Opcja jest włączona, jeśli określisz `-highentropyva` lub `-highentropyva+`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli ta opcja jest określona, zgodne wersje jądra Windows użyć wyższy stopień entropii jądra wybiera losowo układ przestrzeni adresów procesu jako część ASLR. Jeśli jądro używa wyższy stopień entropii, większej liczby adresów można przydzielić do regionów pamięci, takich jak stosy i stosów. W rezultacie jego trudniej jest intruzowi zgadnąć lokalizację konkretnego regionu pamięci.  
  
 Gdy opcja jest na docelowego pliku wykonywalnego i moduły, w której jest to uzależnione należy obsługi wartości wskaźnika, które są większe niż 4 gigabajty (GB), gdy te moduły są uruchomione jako procesy 64-bitowe.  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
