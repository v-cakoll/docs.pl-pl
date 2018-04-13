---
title: -verbose
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0523409e53a8c7ea34de7dcc24b1bce2885a183
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="-verbose"></a>-verbose
Powoduje, że kompilator, aby utworzyć pełne komunikaty o stanie i błędach.  
  
## <a name="syntax"></a>Składnia  
  
```  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+` &#124; `-`  
 Opcjonalny. Określanie `-verbose` jest taka sama jak określanie `-verbose+`, co powoduje, że kompilator, aby wysyłać komunikaty pełne. Wartość domyślna dla tej opcji to `-verbose-`.  
  
## <a name="remarks"></a>Uwagi  
 `-verbose` Opcja wyświetla informacje o całkowita liczba błędów wystawiony przez kompilator, raporty, zestawy, które są ładowane przez moduł oraz pliki, które są aktualnie kompilowana.  
  
> [!NOTE]
>  `-verbose` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `In.vb` i kieruje kompilatora, aby wyświetlić informacje o stanie pełne.  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
