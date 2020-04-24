---
title: -nologo
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 03dc98c45a894304a67765c3e49cd19bbb089c8c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335434"
---
# <a name="-nologo-visual-basic"></a>-nologo (Visual Basic)
Pomija wyświetlanie transparentu praw autorskich i komunikatów informacyjnych podczas kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-nologo  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli określisz `-nologo`, kompilator nie wyświetli transparentu praw autorskich. Domyślnie program `-nologo` nie działa.  
  
> [!NOTE]
> `-nologo` Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio; jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` i nie wyświetla transparentu praw autorskich.  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a>Zobacz też

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
