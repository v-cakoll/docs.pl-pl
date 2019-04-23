---
title: Instrukcje „Line” nie są już obsługiwane (Błąd kompilatora Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: c7a3e6bcd0db268a0e0acfc74c570e26f89cff6a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59339076"
---
# <a name="line-statements-are-no-longer-supported-visual-basic-compiler-error"></a>Instrukcje „Line” nie są już obsługiwane (Błąd kompilatora Visual Basic)
Instrukcje wiersza nie są już obsługiwane. Funkcje We/Wy pliku jest dostępna jako `Microsoft.VisualBasic.FileSystem.LineInput` i funkcje graficzne jest dostępna jako `System.Drawing.Graphics.DrawLine`.  
  
 **Identyfikator błędu:** BC30830  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Jeśli wykonanie dostęp do plików, użyj `Microsoft.VisualBasic.FileSystem.LineInput`.  
  
2. Jeśli wykonanie grafiki, użyj `System.Drawing.Graphics.Drawline`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO>
- <xref:System.Drawing>
- [Dostęp do plików za pomocą Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
