---
title: /nologo (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3c2c7e7a111a3763d7463f67c2d984955da33bbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="nologo-visual-basic"></a>/nologo (Visual Basic)
Pomija wyświetlanie banera praw autorskich i komunikaty informacyjne podczas kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
/nologo  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli określisz `/nologo`, kompilator nie wyświetla transparentu o prawach autorskich. Domyślnie `/nologo` nie jest włączone.  
  
> [!NOTE]
>  `/nologo` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` i nie wyświetla transparentu o prawach autorskich.  
  
```  
vbc /nologo t2.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Kompilacja przykładów — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
