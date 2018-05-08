---
title: -highentropyva (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fef3f922d3089eaca1762ffe35fa38cfe94baf22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-highentropyva-visual-basic"></a>-highentropyva (Visual Basic)
Wskazuje, czy 64-bitowy wykonywalny lub plik wykonywalny, który został oznaczony przez [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) — opcja kompilatora obsługuje wysokiej entropii losowe generowanie układu przestrzeni adresów (ASLR).  
  
## <a name="syntax"></a>Składnia  
  
```  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+` &#124; `-`  
 Opcjonalna. Opcja jest domyślnie wyłączona lub jeśli określisz `-highentropyva-`. Opcja jest włączona, jeśli można określić `-highentropyva` lub `-highentropyva+`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli określisz tej opcji, zgodne wersje jądra systemu Windows można użyć wyższy stopień entropii podczas jądra wybrać losowo układ przestrzeni adresów procesu jako część ASLR. Jeśli jądra używa wyższy stopień entropii, większa liczba adresów mogą przydzielone do regiony pamięci, takich jak stosy i stosów. W związku z tym jest trudniej odgadnąć lokalizacji obszaru pamięci.  
  
 Gdy opcja znajduje się w docelowym pliku wykonywalnego i wszelkich modułów na jego zależności musi mieć możliwość obsługi wartości wskaźnika, które są większe niż 4 gigabajty (GB), gdy te moduły są uruchomione jako procesów 64-bitowych.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
