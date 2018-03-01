---
title: "&#39; Wiersz &#39; instrukcje nie są już obsługiwane (błąd kompilatora Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9d2db5dc786749360dfcf6789f12b5659d5713fc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="39line39-statements-are-no-longer-supported-visual-basic-compiler-error"></a><span data-ttu-id="5d7ba-102">&#39; Wiersz &#39; instrukcje nie są już obsługiwane (błąd kompilatora Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d7ba-102">&#39;Line&#39; statements are no longer supported (Visual Basic Compiler Error)</span></span>
<span data-ttu-id="5d7ba-103">Instrukcje wiersza nie są już obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5d7ba-103">Line statements are no longer supported.</span></span> <span data-ttu-id="5d7ba-104">Funkcje We/Wy plików są dostępne jako `Microsoft.VisualBasic.FileSystem.LineInput` i funkcje graficzne są dostępne jako `System.Drawing.Graphics.DrawLine`.</span><span class="sxs-lookup"><span data-stu-id="5d7ba-104">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>  
  
 <span data-ttu-id="5d7ba-105">**Identyfikator błędu:** BC30830</span><span class="sxs-lookup"><span data-stu-id="5d7ba-105">**Error ID:** BC30830</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5d7ba-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="5d7ba-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="5d7ba-107">Jeśli dostęp do plików, użyj `Microsoft.VisualBasic.FileSystem.LineInput`.</span><span class="sxs-lookup"><span data-stu-id="5d7ba-107">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>  
  
2.  <span data-ttu-id="5d7ba-108">Jeśli wykonywane grafiki, użyj `System.Drawing.Graphics.Drawline`.</span><span class="sxs-lookup"><span data-stu-id="5d7ba-108">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d7ba-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5d7ba-109">See Also</span></span>  
 <xref:System.IO>  
 <xref:System.Drawing>  
 [<span data-ttu-id="5d7ba-110">Dostęp do plików za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5d7ba-110">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
