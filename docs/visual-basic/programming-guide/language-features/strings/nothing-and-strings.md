---
title: Nothing i ciągi w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: f5c1ea8cc0728b25e8e874963967aed504e466d7
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591345"
---
# <a name="nothing-and-strings-in-visual-basic"></a>Nothing i ciągi w Visual Basic
Ocena środowiska uruchomieniowego języka Visual Basic i .NET Framework `Nothing` inaczej kiedy chodzi o ciągów.  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a>Środowisko uruchomieniowe języka Visual Basic i .NET Framework  
 Rozważmy następujący przykład:  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 Środowisko uruchomieniowe języka Visual Basic zazwyczaj ocenia `Nothing` jako ciąg pusty (""). .NET Framework nie zawiera i zgłasza wyjątek, zawsze wtedy, gdy podejmowana jest próba wykonania operacji ciągu na `Nothing`.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do ciągów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
