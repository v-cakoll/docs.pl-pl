---
title: Wznowienie bez błędu
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: 55295997e5e534b091063815d5ad1a37b81638ff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686624"
---
# <a name="resume-without-error"></a><span data-ttu-id="ff510-102">Wznowienie bez błędu</span><span class="sxs-lookup"><span data-stu-id="ff510-102">Resume without error</span></span>
<span data-ttu-id="ff510-103">A `Resume` instrukcji znajdowały się poza kodu obsługi błędu lub kod wyniósł do procedury obsługi błędów, nawet jeśli wystąpił błąd braku.</span><span class="sxs-lookup"><span data-stu-id="ff510-103">A `Resume` statement appeared outside error-handling code, or the code jumped into an error handler even though there was no error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ff510-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="ff510-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="ff510-105">Przenieś `Resume` instrukcji do obsługi błędów lub usuń go.</span><span class="sxs-lookup"><span data-stu-id="ff510-105">Move the `Resume` statement into an error handler, or delete it.</span></span>  
  
2.  <span data-ttu-id="ff510-106">Dlatego przechodzi do etykiety nie może występować między procedurami, wyszukaj procedury dla etykiety, która identyfikuje procedurę obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="ff510-106">Jumps to labels cannot occur across procedures, so search the procedure for the label that identifies the error handler.</span></span> <span data-ttu-id="ff510-107">Jeśli okaże się zduplikowane etykiety, określona jako obiekt docelowy `GoTo` instrukcję, która nie jest `On Error GoTo` instrukcji, zmień wiersz etykiety zgadza się z jego zamierzonym obiektem docelowym.</span><span class="sxs-lookup"><span data-stu-id="ff510-107">If you find a duplicate label specified as the target of a `GoTo` statement that isn't an `On Error GoTo` statement, change the line label to agree with its intended target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff510-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff510-108">See also</span></span>
- [<span data-ttu-id="ff510-109">Resume, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ff510-109">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)
- [<span data-ttu-id="ff510-110">On Error, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ff510-110">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
