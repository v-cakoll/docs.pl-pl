---
title: -utf8output — (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: adcb518cbe8397549c3ae3b3a8ca9f0ecf9dc38e
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004665"
---
# <a name="-utf8output-visual-basic"></a>-utf8output — (Visual Basic)
Wyświetla dane wyjściowe kompilatora przy użyciu kodowania UTF-8.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+` &#124; `-`  
 Opcjonalny. Wartość domyślna dla tej opcji to `-utf8output-`, co oznacza, że wyjście kompilatora nie używa kodowania UTF-8. Określanie `-utf8output` jest taka sama jak w przypadku określenia `-utf8output+`.  
  
## <a name="remarks"></a>Uwagi  
 W niektórych konfiguracjach międzynarodowych dane wyjściowe kompilatora nie mogą być prawidłowo wyświetlane w konsoli programu. W takich sytuacjach należy używać `-utf8output` i przekierować dane wyjściowe kompilatora do pliku.  
  
> [!NOTE]
> Opcja `-utf8output` nie jest dostępna w środowisku deweloperskim programu Visual Studio. jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `In.vb` i kieruje kompilator do wyświetlenia danych wyjściowych przy użyciu kodowania UTF-8.  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
