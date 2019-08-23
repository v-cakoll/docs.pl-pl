---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 07e1718554b158635b9d8b04958834e804e1fe9f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964378"
---
# <a name="-nologo-visual-basic"></a>-nologo (Visual Basic)
Pomija wyświetlanie transparentu praw autorskich i komunikatów informacyjnych podczas kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
-nologo  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli określisz `-nologo`, kompilator nie wyświetli transparentu praw autorskich. Domyślnie program `-nologo` nie działa.  
  
> [!NOTE]
> `-nologo` Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` i nie wyświetla transparentu praw autorskich.  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
