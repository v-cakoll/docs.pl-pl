---
title: Nothing i ciągi w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: 873c4e40a0b12dd657d3294785e04dd9efc23956
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967990"
---
# <a name="nothing-and-strings-in-visual-basic"></a>Nothing i ciągi w Visual Basic
Środowisko uruchomieniowe języka Visual Basic i [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] oceny `Nothing` inaczej kiedy chodzi o ciągów.  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a>Środowisko uruchomieniowe języka Visual Basic i .NET Framework  
 Rozważmy następujący przykład:  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 Środowisko uruchomieniowe języka Visual Basic zazwyczaj ocenia `Nothing` jako ciąg pusty (""). [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Nie zawiera i zgłasza wyjątek, zawsze wtedy, gdy podejmowana jest próba wykonania operacji ciągu na `Nothing`.  
  
## <a name="see-also"></a>Zobacz także
- [Wprowadzenie do ciągów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
