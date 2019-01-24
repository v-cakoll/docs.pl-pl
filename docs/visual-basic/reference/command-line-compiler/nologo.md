---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 1b9cedc3e45795a66c203d4c86bb071045a1d3f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550477"
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
  
## <a name="see-also"></a>Zobacz także
- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
