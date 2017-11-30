---
title: "&#39; Wiersz &#39; instrukcje nie są już obsługiwane (błąd kompilatora Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords: BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9d2db5dc786749360dfcf6789f12b5659d5713fc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="39line39-statements-are-no-longer-supported-visual-basic-compiler-error"></a>&#39; Wiersz &#39; instrukcje nie są już obsługiwane (błąd kompilatora Visual Basic)
Instrukcje wiersza nie są już obsługiwane. Funkcje We/Wy plików są dostępne jako `Microsoft.VisualBasic.FileSystem.LineInput` i funkcje graficzne są dostępne jako `System.Drawing.Graphics.DrawLine`.  
  
 **Identyfikator błędu:** BC30830  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Jeśli dostęp do plików, użyj `Microsoft.VisualBasic.FileSystem.LineInput`.  
  
2.  Jeśli wykonywane grafiki, użyj `System.Drawing.Graphics.Drawline`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO>  
 <xref:System.Drawing>  
 [Dostęp do plików za pomocą Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
