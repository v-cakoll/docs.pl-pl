---
title: /debug (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- debug compiler switches
- /debug compiler option [Visual Basic]
- -debug compiler option [Visual Basic]
- debug compiler option [Visual Basic]
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
ms.openlocfilehash: e32ce702847375c85a805926c56fb965a057ff03
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54605505"
---
# <a name="-debug-visual-basic"></a>-debug (Visual Basic)
Powoduje, że kompilator generuje informacje o debugowaniu i umieść go w plikach wyjściowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
-debug[+ | -]  
' -or-  
-debug:[full | pdbonly]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`+` &#124; `-`|Opcjonalna. Określanie `+` lub `/debug` powoduje, że kompilator generuje informacje o debugowaniu i umieść go w pliku .pdb. Określanie `-` ma taki sam skutek co określenie nie `/debug`.|  
|`full` &#124; `pdbonly`|Opcjonalna. Określa typ informacji o debugowaniu generowanych przez kompilator. Jeśli nie określisz `/debug:pdbonly`, wartość domyślna to `full`, co umożliwia dołączanie debugera do uruchomionego programu. `pdbonly` Argument umożliwia debugowanie kodu źródłowego, gdy program jest uruchomiony w debugerze, ale wyświetla kod języka asemblera, tylko wtedy, gdy jest uruchomiony program jest dołączony do debugera.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj tej opcji, aby utworzyć kompilacji do debugowania. Jeśli nie określisz `/debug`, `/debug+`, lub `/debug:full`, będzie mógł debugować plik wyjściowy programu.  
  
 Domyślnie, informacje o debugowaniu nie jest emitowane (`/debug-`). Emitowanie informacji o debugowaniu, należy określić `/debug` lub `/debug+`.  
  
 Aby uzyskać informacje dotyczące sposobu konfigurowania wydajność debugowania aplikacji, zobacz [ułatwianie obrazu do debugowania](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).  
  
|Aby ustawić - debugowanie w programie Visual Studio zintegrowanego środowiska programistycznego|  
|---|  
|1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**. <br />2.  Kliknij przycisk **skompilować** kartę.<br />3.  Kliknij przycisk **zaawansowane opcje kompilacji**.<br />4.  Zmodyfikuj wartość w **Generuj informacje o debugowaniu** pole.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umieszcza informacje o debugowaniu w pliku wyjściowym `App.exe`.  
  
```  
vbc -debug -out:app.exe test.vb  
```  
  
## <a name="see-also"></a>Zobacz także
- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
