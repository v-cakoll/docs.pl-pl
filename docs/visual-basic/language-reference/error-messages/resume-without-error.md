---
title: Wznowienie bez błędu
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: 5e45f713a433365b4bbc8286154a3b877b08ec59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="resume-without-error"></a><span data-ttu-id="37fa9-102">Wznowienie bez błędu</span><span class="sxs-lookup"><span data-stu-id="37fa9-102">Resume without error</span></span>
<span data-ttu-id="37fa9-103">A `Resume` instrukcji znajdowały się poza kodu obsługi błędu lub kod przeskoki do obsługi błędów, nawet jeśli nie było żadnych błędów.</span><span class="sxs-lookup"><span data-stu-id="37fa9-103">A `Resume` statement appeared outside error-handling code, or the code jumped into an error handler even though there was no error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="37fa9-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="37fa9-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="37fa9-105">Przenieś `Resume` instrukcji do obsługi błędów lub usuń go.</span><span class="sxs-lookup"><span data-stu-id="37fa9-105">Move the `Resume` statement into an error handler, or delete it.</span></span>  
  
2.  <span data-ttu-id="37fa9-106">Dlatego przeskoki do etykiet nie może wystąpić między procedurami, wyszukaj procedury dla etykiety, który identyfikuje program obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="37fa9-106">Jumps to labels cannot occur across procedures, so search the procedure for the label that identifies the error handler.</span></span> <span data-ttu-id="37fa9-107">Jeśli okaże się zduplikowane etykiety określony jako element docelowy `GoTo` instrukcji, która nie jest `On Error GoTo` instrukcji, zmienić etykietę wiersza, aby uzgodnić z jej celem.</span><span class="sxs-lookup"><span data-stu-id="37fa9-107">If you find a duplicate label specified as the target of a `GoTo` statement that isn't an `On Error GoTo` statement, change the line label to agree with its intended target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37fa9-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="37fa9-108">See Also</span></span>  
 [<span data-ttu-id="37fa9-109">Resume, instrukcja</span><span class="sxs-lookup"><span data-stu-id="37fa9-109">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [<span data-ttu-id="37fa9-110">On Error, instrukcja</span><span class="sxs-lookup"><span data-stu-id="37fa9-110">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
