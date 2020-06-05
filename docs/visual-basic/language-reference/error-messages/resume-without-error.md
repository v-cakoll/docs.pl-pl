---
title: Wznowienie bez błędu
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: b6b565c88acadca048ade22ab00ac68539725f78
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400373"
---
# <a name="resume-without-error"></a><span data-ttu-id="daeed-102">Wznowienie bez błędu</span><span class="sxs-lookup"><span data-stu-id="daeed-102">Resume without error</span></span>
<span data-ttu-id="daeed-103">`Resume`Instrukcja pojawiła się poza kodem obsługi błędu lub kod przeskoczy do procedury obsługi błędów, chociaż nie wystąpił błąd.</span><span class="sxs-lookup"><span data-stu-id="daeed-103">A `Resume` statement appeared outside error-handling code, or the code jumped into an error handler even though there was no error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="daeed-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="daeed-104">To correct this error</span></span>  
  
1. <span data-ttu-id="daeed-105">Przenieś `Resume` instrukcję do procedury obsługi błędów lub usuń ją.</span><span class="sxs-lookup"><span data-stu-id="daeed-105">Move the `Resume` statement into an error handler, or delete it.</span></span>  
  
2. <span data-ttu-id="daeed-106">Przeskocz do etykiet nie mogą występować w różnych procedurach, więc Wyszukaj w tej procedurze etykietę identyfikującą procedurę obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="daeed-106">Jumps to labels cannot occur across procedures, so search the procedure for the label that identifies the error handler.</span></span> <span data-ttu-id="daeed-107">Jeśli zostanie znaleziona zduplikowana etykieta określona jako obiekt docelowy `GoTo` instrukcji, która nie jest `On Error GoTo` instrukcją, Zmień etykietę wiersza, aby zgadzać się z zamierzonym celem.</span><span class="sxs-lookup"><span data-stu-id="daeed-107">If you find a duplicate label specified as the target of a `GoTo` statement that isn't an `On Error GoTo` statement, change the line label to agree with its intended target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daeed-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="daeed-108">See also</span></span>

- [<span data-ttu-id="daeed-109">Resume — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="daeed-109">Resume Statement</span></span>](../statements/resume-statement.md)
- [<span data-ttu-id="daeed-110">On Error, instrukcja</span><span class="sxs-lookup"><span data-stu-id="daeed-110">On Error Statement</span></span>](../statements/on-error-statement.md)
