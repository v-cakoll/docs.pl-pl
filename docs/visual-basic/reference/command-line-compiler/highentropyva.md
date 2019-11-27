---
title: -highentropyva
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
ms.openlocfilehash: 7934dcaada4675bf687624bef5ed1ea25e842832
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344252"
---
# <a name="-highentropyva-visual-basic"></a>-HIGHENTROPYVA (Visual Basic)
Wskazuje, czy 64-bitowy plik wykonywalny lub plik wykonywalny, który jest oznaczony przez [-platformą: anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) , opcja kompilatora o wysokiej entropii (ASLR).  
  
## <a name="syntax"></a>Składnia  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+` &#124; `-`  
 Opcjonalna. Opcja jest domyślnie wyłączona lub jeśli określono `-highentropyva-`. Opcja jest włączona, jeśli określono `-highentropyva` lub `-highentropyva+`.  
  
## <a name="remarks"></a>Uwagi  
 W przypadku wybrania tej opcji zgodne wersje jądra systemu Windows mogą używać wyższych stopni entropii, gdy jądro losowo rozmieszczenie przestrzeni adresowej procesu w ramach ASLR. Jeśli jądro używa wyższych stopni entropii, można przydzielać większą liczbę adresów do regionów pamięci, takich jak stosy i sterty. W związku z tym trudniejsze jest odpuszczenie lokalizacji określonego obszaru pamięci.  
  
 Gdy opcja jest włączona, docelowy plik wykonywalny i wszystkie moduły, od których zależy, muszą być w stanie obsłużyć wartości wskaźników, które są większe niż 4 gigabajty (GB), gdy te moduły działają jako procesy 64-bitowe.  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
