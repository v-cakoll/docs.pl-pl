---
title: -quiet
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- -quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a0ed08e013f088f512ae915daa9aeb2fa6b249b0
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="-quiet"></a>-quiet
Uniemożliwia wyświetlanie kodu dotyczące składni błędów i ostrzeżeń kompilatora.  
  
## <a name="syntax"></a>Składnia  
  
```  
-quiet  
```  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie `-quiet` nie jest włączone. Kiedy kompilator zgłasza błąd związany z składni lub ostrzeżenie, generuje także wiersza z kodu źródłowego. Dla aplikacji, które przeanalizować dane wyjściowe kompilatora może być wygodniejsze kompilator, aby uzyskać tylko tekst diagnostyki.  
  
 W poniższym przykładzie `Module1` generuje błąd, który zawiera kod źródłowy, gdy kompilowany bez `-quiet`.  
  
```vb  
Module Module1  
    Sub Main()  
        x()  
    End Sub  
End Module  
```  
  
 Dane wyjściowe:  
 
```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
``` 
 Skompilowane z `-quiet`, kompilator generuje jedynie następujące elementy:  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
> [!NOTE]
>  `-quiet` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` i nie zawiera kodu dla diagnostyki kompilatora dotyczące składni:  
  
```  
vbc -quiet t2.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
