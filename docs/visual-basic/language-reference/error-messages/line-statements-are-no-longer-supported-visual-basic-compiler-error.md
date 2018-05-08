---
title: '&#39;Wiersz&#39; instrukcji nie są już obsługiwane (błąd kompilatora Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: 06bba0ebfc2faec24f4720c45de3bdcfec993499
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="39line39-statements-are-no-longer-supported-visual-basic-compiler-error"></a>&#39;Wiersz&#39; instrukcji nie są już obsługiwane (błąd kompilatora Visual Basic)
Instrukcje wiersza nie są już obsługiwane. Funkcje We/Wy plików są dostępne jako `Microsoft.VisualBasic.FileSystem.LineInput` i funkcje graficzne są dostępne jako `System.Drawing.Graphics.DrawLine`.  
  
 **Identyfikator błędu:** BC30830  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Jeśli dostęp do plików, użyj `Microsoft.VisualBasic.FileSystem.LineInput`.  
  
2.  Jeśli wykonywane grafiki, użyj `System.Drawing.Graphics.Drawline`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO>  
 <xref:System.Drawing>  
 [Dostęp do plików za pomocą Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
