---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: 5b3899462af7c4aa8e0f77377a8d7485975f9867
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937259"
---
# <a name="-verbose"></a>-verbose
Powoduje, że kompilator tworzy pełny stan i komunikaty o błędach.  
  
## <a name="syntax"></a>Składnia  
  
```  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+` &#124; `-`  
 Opcjonalny. Określanie `-verbose` jest takie samo jak określanie `-verbose+`, co powoduje, że kompilator emituje pełne komunikaty. Wartość domyślna dla tej opcji to `-verbose-`.  
  
## <a name="remarks"></a>Uwagi  
 `-verbose` Opcja wyświetla informacje o całkowitej liczbie błędów wydanych przez kompilator, raporty, które zestawy są ładowane przez moduł, i wyświetla pliki, które są obecnie kompilowane.  
  
> [!NOTE]
> `-verbose` Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `In.vb` i kieruje kompilator, aby wyświetlić pełne informacje o stanie.  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
