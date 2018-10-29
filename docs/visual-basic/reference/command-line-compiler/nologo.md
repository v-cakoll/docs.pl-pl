---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 21c708ef632cc0ed923713cd49e22d44848b4db3
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199912"
---
# <a name="-nologo-visual-basic"></a>-nologo (Visual Basic)
Pomija wyświetlanie transparentu praw autorskich i komunikaty informacyjne, podczas kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
-nologo  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli określisz `-nologo`, kompilator nie wyświetla transparentu praw autorskich. Domyślnie `-nologo` nie jest włączone.  
  
> [!NOTE]
>  `-nologo` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` i nie wyświetla transparentu praw autorskich.  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
