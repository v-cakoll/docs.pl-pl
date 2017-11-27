---
title: /highentropyva (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 55568808bb94f98ce7a20016fc5a2a0a2ef23a38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="highentropyva-visual-basic"></a>/highentropyva (Visual Basic)
Wskazuje, czy 64-bitowy wykonywalny lub plik wykonywalny, który został oznaczony przez [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) — opcja kompilatora obsługuje wysokiej entropii losowe generowanie układu przestrzeni adresów (ASLR).  
  
## <a name="syntax"></a>Składnia  
  
```  
/highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+` &#124; `-`  
 Opcjonalny. Opcja jest domyślnie wyłączona lub jeśli określisz `/highentropyva-`. Opcja jest włączona, jeśli można określić `/highentropyva` lub `/highentropyva+`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli określisz tej opcji, zgodne wersje jądra systemu Windows można użyć wyższy stopień entropii podczas jądra wybrać losowo układ przestrzeni adresów procesu jako część ASLR. Jeśli jądra używa wyższy stopień entropii, większa liczba adresów mogą przydzielone do regiony pamięci, takich jak stosy i stosów. W związku z tym jest trudniej odgadnąć lokalizacji obszaru pamięci.  
  
 Gdy opcja znajduje się w docelowym pliku wykonywalnego i wszelkich modułów na jego zależności musi mieć możliwość obsługi wartości wskaźnika, które są większe niż 4 gigabajty (GB), gdy te moduły są uruchomione jako procesów 64-bitowych.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Kompilacja przykładów — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
