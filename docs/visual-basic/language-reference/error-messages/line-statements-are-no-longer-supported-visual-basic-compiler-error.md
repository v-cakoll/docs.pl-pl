---
title: Instrukcje „Line” nie są już obsługiwane (Błąd kompilatora Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: a3d243f39f3fc45ca6b1ba0d26892d4c3db56f59
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397301"
---
# <a name="line-statements-are-no-longer-supported-visual-basic-compiler-error"></a>Instrukcje „Line” nie są już obsługiwane (Błąd kompilatora Visual Basic)
Instrukcje liniowe nie są już obsługiwane. Funkcja we/wy plików jest dostępna, ponieważ `Microsoft.VisualBasic.FileSystem.LineInput` Funkcja graficzna jest dostępna jako `System.Drawing.Graphics.DrawLine` .  
  
 **Identyfikator błędu:** BC30830  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. W przypadku uzyskiwania dostępu do plików użyj `Microsoft.VisualBasic.FileSystem.LineInput` .  
  
2. Jeśli wykonujesz grafikę, użyj `System.Drawing.Graphics.Drawline` .  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO>
- <xref:System.Drawing>
- [Dostęp do plików za pomocą Visual Basic](../../developing-apps/programming/drives-directories-files/file-access.md)
