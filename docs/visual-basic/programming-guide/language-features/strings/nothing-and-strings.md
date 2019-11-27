---
title: Nothing i ciągi
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: dfc43748d0754f0a6a29763c42ab82d9937f89f8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344295"
---
# <a name="nothing-and-strings-in-visual-basic"></a>Nothing i ciągi w Visual Basic
Środowisko uruchomieniowe Visual Basic i .NET Framework oceniane `Nothing` w różny sposób, gdy przejdzie do ciągów.  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a>Visual Basic środowisko uruchomieniowe i .NET Framework  
 Rozważmy następujący przykład:  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 Środowisko uruchomieniowe Visual Basic zwykle szacuje `Nothing` jako ciąg pusty (""). .NET Framework nie jest jednak ani zgłasza wyjątek, gdy podejmowana jest próba wykonania operacji na ciągach na `Nothing`.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do ciągów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
