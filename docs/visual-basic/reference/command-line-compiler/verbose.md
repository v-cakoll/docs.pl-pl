---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: 7a5dd305d1cc40e57d0f07f383151dc1a965bdda
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54513922"
---
# <a name="-verbose"></a>-verbose
Powoduje, że kompilator generuje pełny stan i komunikaty o błędach.  
  
## <a name="syntax"></a>Składnia  
  
```  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+` &#124; `-`  
 Opcjonalna. Określanie `-verbose` jest taka sama jak określanie `-verbose+`, co powoduje, że kompilator będzie pełne komunikaty wyjściowe. Wartość domyślna tej opcji to `-verbose-`.  
  
## <a name="remarks"></a>Uwagi  
 `-verbose` Opcji wyświetla informacje o całkowitą liczbę wszystkich błędów, które wystawiony przez kompilator, raporty, zestawy, które są ładowane przez moduł i wyświetla pliki, które są aktualnie kompilowana.  
  
> [!NOTE]
>  `-verbose` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `In.vb` i instruuje kompilator, aby wyświetlić informacje o stanie pełne.  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a>Zobacz także
- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
