---
title: /utf8output (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 23c7c308865a6b6afb07443a42090fff3d9e2efb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="utf8output-visual-basic"></a>/utf8output (Visual Basic)
Wyświetla kompilatora, dane wyjściowe przy użyciu kodowania UTF-8.  
  
## <a name="syntax"></a>Składnia  
  
```  
/utf8output[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+` &#124; `-`  
 Opcjonalny. Wartość domyślna dla tej opcji to `/utf8output-`, co oznacza, że dane wyjściowe kompilatora nie używa kodowania UTF-8. Określanie `/utf8output` jest taka sama jak określanie `/utf8output+`.  
  
## <a name="remarks"></a>Uwagi  
 W niektórych konfiguracjach międzynarodowe dane wyjściowe kompilatora nie można wyświetlić poprawnie w konsoli. W takiej sytuacji należy używać `/utf8output` i Przekieruj dane wyjściowe kompilatora do pliku.  
  
> [!NOTE]
>  `/utf8output` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `In.vb` i kieruje kompilatora, aby wyświetlić dane wyjściowe przy użyciu kodowania UTF-8.  
  
```  
vbc /utf8output in.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Kompilacja przykładów — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
