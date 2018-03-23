---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e5eb9db7af861a8439b47adb8f5e515331fae6e
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="-nologo-visual-basic"></a>-nologo (Visual Basic)
Pomija wyświetlanie banera praw autorskich i komunikaty informacyjne podczas kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
-nologo  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli określisz `-nologo`, kompilator nie wyświetla transparentu o prawach autorskich. Domyślnie `-nologo` nie jest włączone.  
  
> [!NOTE]
>  `-nologo` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` i nie wyświetla transparentu o prawach autorskich.  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
