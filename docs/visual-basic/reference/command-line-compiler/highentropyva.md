---
title: -highentropyva (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
ms.openlocfilehash: 5d948817d4bc71aa31c5890f6740248f4c309588
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181504"
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
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
