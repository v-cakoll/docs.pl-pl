---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: 405b557568a736de3ddc3b51e265261222613131
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403034"
---
# <a name="-verbose"></a>-verbose
Powoduje, że kompilator tworzy pełny stan i komunikaty o błędach.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+`&#124;`-`  
 Opcjonalny. Określanie `-verbose` jest takie samo jak określanie `-verbose+` , co powoduje, że kompilator emituje pełne komunikaty. Wartość domyślna dla tej opcji to `-verbose-` .  
  
## <a name="remarks"></a>Uwagi  
 `-verbose`Opcja wyświetla informacje o całkowitej liczbie błędów wydanych przez kompilator, raporty, które zestawy są ładowane przez moduł, i wyświetla pliki, które są obecnie kompilowane.  
  
> [!NOTE]
> `-verbose`Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `In.vb` i kieruje kompilator, aby wyświetlić pełne informacje o stanie.  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a>Zobacz też

- [Kompilator wiersza polecenia Visual Basic](index.md)
- [Przykłady kompilacji — wiersze poleceń](sample-compilation-command-lines.md)
