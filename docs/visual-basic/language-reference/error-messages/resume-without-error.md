---
title: "Wznowienie bez błędu"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f86361b1e5310359288a97c5f41f017a344c30b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="resume-without-error"></a><span data-ttu-id="10d33-102">Wznowienie bez błędu</span><span class="sxs-lookup"><span data-stu-id="10d33-102">Resume without error</span></span>
<span data-ttu-id="10d33-103">A `Resume` instrukcji znajdowały się poza kodu obsługi błędu lub kod przeskoki do obsługi błędów, nawet jeśli nie było żadnych błędów.</span><span class="sxs-lookup"><span data-stu-id="10d33-103">A `Resume` statement appeared outside error-handling code, or the code jumped into an error handler even though there was no error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="10d33-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="10d33-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="10d33-105">Przenieś `Resume` instrukcji do obsługi błędów lub usuń go.</span><span class="sxs-lookup"><span data-stu-id="10d33-105">Move the `Resume` statement into an error handler, or delete it.</span></span>  
  
2.  <span data-ttu-id="10d33-106">Dlatego przeskoki do etykiet nie może wystąpić między procedurami, wyszukaj procedury dla etykiety, który identyfikuje program obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="10d33-106">Jumps to labels cannot occur across procedures, so search the procedure for the label that identifies the error handler.</span></span> <span data-ttu-id="10d33-107">Jeśli okaże się zduplikowane etykiety określony jako element docelowy `GoTo` instrukcji, która nie jest `On Error GoTo` instrukcji, zmienić etykietę wiersza, aby uzgodnić z jej celem.</span><span class="sxs-lookup"><span data-stu-id="10d33-107">If you find a duplicate label specified as the target of a `GoTo` statement that isn't an `On Error GoTo` statement, change the line label to agree with its intended target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10d33-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="10d33-108">See Also</span></span>  
 [<span data-ttu-id="10d33-109">Resume — instrukcja</span><span class="sxs-lookup"><span data-stu-id="10d33-109">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [<span data-ttu-id="10d33-110">On Error — instrukcja</span><span class="sxs-lookup"><span data-stu-id="10d33-110">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
