---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: 8c5bc1d2ce331b8fe9461f91d64fbeab5a070b59
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004971"
---
# <a name="-verbose"></a>-verbose
Powoduje, że kompilator tworzy pełny stan i komunikaty o błędach.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+`&#124;`-`  
 Element opcjonalny. Określanie `-verbose` jest takie samo jak określanie `-verbose+`, co powoduje, że kompilator emituje pełne komunikaty. Wartość domyślna dla tej opcji to `-verbose-`.  
  
## <a name="remarks"></a>Uwagi  
 `-verbose` Opcja wyświetla informacje o całkowitej liczbie błędów wydanych przez kompilator, raporty, które zestawy są ładowane przez moduł, i wyświetla pliki, które są obecnie kompilowane.  
  
> [!NOTE]
> `-verbose` Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio; jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `In.vb` i kieruje kompilator, aby wyświetlić pełne informacje o stanie.  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a>Zobacz też

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
