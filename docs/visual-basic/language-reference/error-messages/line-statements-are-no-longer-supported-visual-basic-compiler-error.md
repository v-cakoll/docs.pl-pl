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
# <a name="39line39-statements-are-no-longer-supported-visual-basic-compiler-error"></a><span data-ttu-id="b74fb-102">&#39;Wiersz&#39; instrukcje nie są już obsługiwane (błąd kompilatora Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b74fb-102">&#39;Line&#39; statements are no longer supported (Visual Basic Compiler Error)</span></span>
<span data-ttu-id="b74fb-103">Instrukcje wiersza nie są już obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="b74fb-103">Line statements are no longer supported.</span></span> <span data-ttu-id="b74fb-104">Funkcje We/Wy pliku jest dostępna jako `Microsoft.VisualBasic.FileSystem.LineInput` i funkcje graficzne jest dostępna jako `System.Drawing.Graphics.DrawLine`.</span><span class="sxs-lookup"><span data-stu-id="b74fb-104">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>  
  
 <span data-ttu-id="b74fb-105">**Identyfikator błędu:** BC30830</span><span class="sxs-lookup"><span data-stu-id="b74fb-105">**Error ID:** BC30830</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b74fb-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="b74fb-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="b74fb-107">Jeśli wykonanie dostęp do plików, użyj `Microsoft.VisualBasic.FileSystem.LineInput`.</span><span class="sxs-lookup"><span data-stu-id="b74fb-107">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>  
  
2.  <span data-ttu-id="b74fb-108">Jeśli wykonanie grafiki, użyj `System.Drawing.Graphics.Drawline`.</span><span class="sxs-lookup"><span data-stu-id="b74fb-108">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b74fb-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b74fb-109">See also</span></span>
- <xref:System.IO>
- <xref:System.Drawing>
- [<span data-ttu-id="b74fb-110">Dostęp do plików za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b74fb-110">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
