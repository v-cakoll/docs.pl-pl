---
title: Instrukcje „Line” nie są już obsługiwane (Błąd kompilatora Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: 7616bcdc39ab479049586534fac22f1e2d96a700
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831842"
---
# <a name="line-statements-are-no-longer-supported-visual-basic-compiler-error"></a>Instrukcje „Line” nie są już obsługiwane (Błąd kompilatora Visual Basic)
Instrukcje wiersza nie są już obsługiwane. Funkcje We/Wy pliku jest dostępna jako `Microsoft.VisualBasic.FileSystem.LineInput` i funkcje graficzne jest dostępna jako `System.Drawing.Graphics.DrawLine`.  
  
 **Identyfikator błędu:** BC30830  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Jeśli wykonanie dostęp do plików, użyj `Microsoft.VisualBasic.FileSystem.LineInput`.  
  
2.  Jeśli wykonanie grafiki, użyj `System.Drawing.Graphics.Drawline`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO>
- <xref:System.Drawing>
- [Dostęp do plików za pomocą Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
