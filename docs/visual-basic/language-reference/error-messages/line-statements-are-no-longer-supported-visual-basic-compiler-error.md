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
ms.locfileid: "33587882"
---
# <a name="39line39-statements-are-no-longer-supported-visual-basic-compiler-error"></a><span data-ttu-id="18a48-102">&#39;Wiersz&#39; instrukcji nie są już obsługiwane (błąd kompilatora Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18a48-102">&#39;Line&#39; statements are no longer supported (Visual Basic Compiler Error)</span></span>
<span data-ttu-id="18a48-103">Instrukcje wiersza nie są już obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="18a48-103">Line statements are no longer supported.</span></span> <span data-ttu-id="18a48-104">Funkcje We/Wy plików są dostępne jako `Microsoft.VisualBasic.FileSystem.LineInput` i funkcje graficzne są dostępne jako `System.Drawing.Graphics.DrawLine`.</span><span class="sxs-lookup"><span data-stu-id="18a48-104">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>  
  
 <span data-ttu-id="18a48-105">**Identyfikator błędu:** BC30830</span><span class="sxs-lookup"><span data-stu-id="18a48-105">**Error ID:** BC30830</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="18a48-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="18a48-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="18a48-107">Jeśli dostęp do plików, użyj `Microsoft.VisualBasic.FileSystem.LineInput`.</span><span class="sxs-lookup"><span data-stu-id="18a48-107">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>  
  
2.  <span data-ttu-id="18a48-108">Jeśli wykonywane grafiki, użyj `System.Drawing.Graphics.Drawline`.</span><span class="sxs-lookup"><span data-stu-id="18a48-108">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18a48-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="18a48-109">See Also</span></span>  
 <xref:System.IO>  
 <xref:System.Drawing>  
 [<span data-ttu-id="18a48-110">Dostęp do plików za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="18a48-110">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
