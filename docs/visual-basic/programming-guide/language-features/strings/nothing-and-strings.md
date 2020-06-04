---
title: Nothing i ciągi
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: 392de45b0ee1688224f3e8170b0144f1acdb0912
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360569"
---
# <a name="nothing-and-strings-in-visual-basic"></a>Nothing i ciągi w Visual Basic
Środowisko uruchomieniowe Visual Basic i .NET Framework są oceniane w `Nothing` różny sposób, gdy przejdzie do ciągów.  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a>Visual Basic środowisko uruchomieniowe i .NET Framework  
 Rozpatrzmy następujący przykład:  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 Środowisko uruchomieniowe Visual Basic zwykle jest obliczane `Nothing` jako ciąg pusty (""). .NET Framework nie jest jednak ani zgłasza wyjątek, gdy podejmowana jest próba wykonania operacji na ciągach `Nothing` .  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do ciągów w Visual Basic](introduction-to-strings.md)
