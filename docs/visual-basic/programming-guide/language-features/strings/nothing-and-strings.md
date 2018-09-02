---
title: Nothing i ciągi w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: d03781209f0f9b021d540bd251c6c6025ad21422
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43425214"
---
# <a name="nothing-and-strings-in-visual-basic"></a>Nothing i ciągi w Visual Basic
Środowisko uruchomieniowe języka Visual Basic i [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] oceny `Nothing` inaczej kiedy chodzi o ciągów.  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a>Środowisko uruchomieniowe języka Visual Basic i .NET Framework  
 Rozważmy następujący przykład:  
  
 [!code-vb[VbVbalrStrings#47](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/nothing-and-strings_1.vb)]  
  
 Środowisko uruchomieniowe języka Visual Basic zazwyczaj ocenia `Nothing` jako ciąg pusty (""). [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Nie zawiera i zgłasza wyjątek, zawsze wtedy, gdy podejmowana jest próba wykonania operacji ciągu na `Nothing`.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do ciągów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
