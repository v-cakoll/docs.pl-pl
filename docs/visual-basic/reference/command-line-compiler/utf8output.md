---
title: -utf8output
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 5cdc60888cd872940afc1b03febd879bb6d87c2e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350835"
---
# <a name="-utf8output-visual-basic"></a>-utf8output — (Visual Basic)
Wyświetla dane wyjściowe kompilatora przy użyciu kodowania UTF-8.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+` &#124; `-`  
 Opcjonalna. Wartość domyślna dla tej opcji to `-utf8output-`, co oznacza, że wyjście kompilatora nie używa kodowania UTF-8. Określanie `-utf8output` jest taka sama jak określanie `-utf8output+`.  
  
## <a name="remarks"></a>Uwagi  
 W niektórych konfiguracjach międzynarodowych dane wyjściowe kompilatora nie mogą być prawidłowo wyświetlane w konsoli programu. W takich sytuacjach należy używać `-utf8output` i przekierować dane wyjściowe kompilatora do pliku.  
  
> [!NOTE]
> Opcja `-utf8output` nie jest dostępna w środowisku deweloperskim programu Visual Studio; jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `In.vb` i kieruje kompilator do wyświetlania danych wyjściowych przy użyciu kodowania UTF-8.  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
