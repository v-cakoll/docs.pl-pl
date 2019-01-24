---
title: '&#39;Wiersz&#39; instrukcje nie są już obsługiwane (błąd kompilatora Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: 36226cc371ffb8a51cb8d0f918952f1c717aea10
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702980"
---
# <a name="39line39-statements-are-no-longer-supported-visual-basic-compiler-error"></a>&#39;Wiersz&#39; instrukcje nie są już obsługiwane (błąd kompilatora Visual Basic)
Instrukcje wiersza nie są już obsługiwane. Funkcje We/Wy pliku jest dostępna jako `Microsoft.VisualBasic.FileSystem.LineInput` i funkcje graficzne jest dostępna jako `System.Drawing.Graphics.DrawLine`.  
  
 **Identyfikator błędu:** BC30830  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Jeśli wykonanie dostęp do plików, użyj `Microsoft.VisualBasic.FileSystem.LineInput`.  
  
2.  Jeśli wykonanie grafiki, użyj `System.Drawing.Graphics.Drawline`.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.IO>
- <xref:System.Drawing>
- [Dostęp do plików za pomocą Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
